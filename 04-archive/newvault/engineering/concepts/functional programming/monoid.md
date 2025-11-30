---
creation date: 03/27/2025
tags:
  - dev/functional-programming
url: https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html
---
---
What is the similarity between number addition, string concatenation, array concatenation, and function composition?

They are all **monoids**. And monoids are super useful.

The term Monoid comes from category theory. It describes a set of elements which has 3 special properties when combined with a particular operation, often named `concat`:

- The operation must combine two values of the set into a third value of the same set. If `a`and `b` are part of the set, then `concat(a, b)` must also be part of the set. In category theory, this is called a _magma_.
- The operation must be _associative_: `concat(x, concat(y, z))` must be the same as `concat(concat(x, y), z)` where `x`, `y`, and `z` are any value in the set. No matter how you group the operation, the result should be the same, as long as the order is respected.
- The set must possess a _neutral element_ in regard to the operation. If that neutral element is combined with any other value, it should not change it. `concat(element, neutral) == concat(neutral, element) == element`

Now that you know what a monoid is, what if I told you that you use it all the time?

**Tip**: This article is the second one in a series about [functional programming in JavaScript](https://marmelab.com/blog/2018/03/14/functional-programming-1-unit-of-code.html). You can read this one first, or start with the previous one, describing the _unit_.

## [](https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html#number-addition-is-a-monoid)Number Addition Is A Monoid

![lego concat](https://marmelab.com/images/blog/monoid-lego-concat.jpg)

When you add two numbers, you manipulate a set of JavaScript `Number` instances. The addition operation takes two numbers, and always return a number. Therefore, it is a _magma_.

The addition is _associative_:

```text
(1 + 2) + 3 == 1 + (2 + 3); // true
```

Finally, the number 0 is the neutral element for the addition operation:

```js
x + 0; // x
```

So according to the definition, numbers form a monoid under the addition operation.

**Tip**: You see that the concat function doesn't have to be named `concat` for a monoid to exist. Here, it's just `+`.

Let's see another example.

## [](https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html#string-concatenation-is-a-monoid)String Concatenation Is a Monoid

In JavaScript, `concat` is a method of `String` instances. But it's easy to extract it as a pure function:

```js
const concat = (a, b) => a.concat(b);
```

This function operates on two strings and returns a string. So it's a _magma_.

It's also _associative_:

```js
concat("hello", concat(" ", "world")); // "hello world"
concat(concat("hello", " "), "world"); // "hello world"
```

And it has a neutral element, the empty string (`''`):

```js
concat("hello", ""); // 'hello'
concat("", "hello"); // 'hello'
```

So according to the definition, strings form a monoid under the concatenation operation. Do you want another example?

## [](https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html#function-composition-is-a-monoid)Function Composition Is A Monoid

You probably know the `compose` function:

```js
const compose = (func1, func2) => arg => func1(func2(arg));
```

Compose takes two functions as arguments, and returns a function. So it's a _magma_.

Now let's see associativity and neutrality:

```js
const compose = (f1, f2) => arg => f1(f2(arg));

const add5 = a => a + 5;
const double = a => a * 2;
const resultIs = a => `result: ${a}`;

const doubleThenAdd5 = compose(
  add5,
  double
);

doubleThenAdd5(3); // 11

// The composition is associative.
// The grouping does not matter as long as the order is preserved.
compose(
  compose(
    resultIs,
    add5
  ),
  double
)(3); // 'result: 11'
compose(
  resultIs,
  compose(
    add5,
    double
  )
)(3); // 'result: 11'

// And the neutral element is the identity function v => v.
const neutral = v => v;

compose(
  add5,
  neutral
)(3); // 8
compose(
  neutral,
  add5
)(3); // 8
```

So according to the definition, functions form a monoid under the composition operation.

But what are monoids good for?

## [](https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html#reducing-function-arguments)Reducing Function Arguments

[In the previous post of this series](https://marmelab.com/blog/2018/03/14/functional-programming-1-unit-of-code.html#next-step), I explained that when we manipulate functions, we need a way to turn a function that takes two arguments into a function that takes any number of arguments.

Monoids are the solution to that problem when used in combination with `Array.reduce`.

Let's start with number addition. The addition operation takes two arguments. How can I apply it on an array of arbitrary size? Using `Array.reduce`:

```js
const add = (a, b) => a + b;
const addArray = arr => arr.reduce(add, 0);
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
addArray(numbers); // 55
```

This works with other monoids, too:

```js
const concat = (a, b) => a.concat(b);
const concatArray = arr => arr.reduce(concat, "");
const strings = ["hello", " ", "world"];
concatArray(strings); // 'hello world';

const compose = (f1, f2) => arg => f1(f2(arg));
const composeArray = arr => arr.reduce(compose, x => x);
const resultIs = a => `result: ${a}`;
const add5 = a => a + 5;
const double = a => a * 2;
const functions = [resultIs, add5, double];
const myOperation = composeArray(functions);
myOperation(2); // result: 9
```

Let's generalize: when you have a monoid, you can transform a function taking two arguments to a function taking an array of arguments by calling:

```js
[value1, value2, value3, ...].reduce(concat, neutral);
```

![Reduce](https://marmelab.com/images/blog/monoid-reduce.jpg)

## [](https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html#splitting-computation-in-chunks)Splitting Computation In Chunks

As the operation of a monoid is associative, you can cut an array of values into smaller chunks, apply the `concat` operation on each array, then recombine the results using the `concat`operation:

```js
const concat = (a, b) => a + b;
const bigArray = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
bigArray.reduce(concat, 0); // 55
const result1 = bigArray.slice(0, 5).reduce(concat, 0); // 15
const result2 = bigArray.slice(5).reduce(concat, 0); // 40
concat(result1, result2); // 55
```

The interest is to distribute large computation across many computation units (cores). This is possible with any monoid, so that explains why parallel programming is made easier by functional paradigms.

## [](https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html#async-composition)Async Composition

Using the same logic, I can create a function that composes any number of asynchronous functions (or any function that returns a promise). I just need to form a monoid.

```js
const fetchJoke = async number => fetch(`http://api.icndb.com/jokes/${number}`);
const toJson = async response => response.json();
const parseJoke = json => json.value.joke;

const getJoke = async number => parseJoke(await toJson(await fetchJoke(number))
getJoke(23).then(console.log); // "Time waits for no man. Unless that man is Chuck Norris."

// the getJoke() function is a pain to write. Let's use composition to make it easier
const asyncCompose = (func1, func2) => async x => func1(await func2(x));

// asyncCompose() is associative
asyncCompose(parseJoke, asyncCompose(toJson, fetchJoke))(23).then(console.log);
// "Time waits for no man. Unless that man is Chuck Norris."

asyncCompose(asyncCompose(parseJoke, toJson), fetchJoke)(23).then(console.log);
// "Time waits for no man. Unless that man is Chuck Norris."

// asyncCompose() has a neutral element - the identity function
const neutralAsyncFunc = x => x;
asyncCompose(a => Promise.resolve(a + 1), neutralAsyncFunc)(5) // Promise(6)
asyncCompose(neutralAsyncFunc, a => Promise.resolve(a + 1))(5) // Promise(6)

// so async functions form a monoid under the asyncCompose operation
// hurray, we can use Array.reduce!
const asyncComposeArray = functions => functions.reduce(asyncCompose, x => x);
// let's make it a function that takes an arbitrary number of arguments instead
const asyncComposeArgs = (...args) => args.reduce(asyncCompose, x => x);

// now, writing getJoke() becomes much easier
const getJoke2 = asyncComposeArgs(parseJoke, toJson, fetchJoke);
getJoke2(23).then(console.log); // "Time waits for no man. Unless that man is Chuck Norris."
```

Thanks to monoids, I managed to write an asynchronous version of `compose()` working with an arbitrary number of arguments in no time. This is not magic, this is math.

As a side note, `asyncCompose` will work with normal functions, too. And that's because `await`works with any value - not only Promises.

## [](https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html#async-flow)Async Flow

There is just one problem: this reads backward.

`const getJoke2 = asyncComposeArgs(parseJoke, toJson, fetchJoke);`

So instead of using `compose()`, let's use `flow()`, which does exactly the same thing, but the other way around:

```js
const fetchJoke = async number => fetch(`http://api.icndb.com/jokes/${number}`);
const toJson = async response => response.json();
const parseJoke = json => json.value.joke;

const flow = (func1, func2) => async x => func2(await func1(x));
// func1 is executed before func2
const flowArray = functions => functions.reduce(flow, x => x);
// let's make it a function that takes an arbitrary number of arguments instead
const flowArgs = (...args) => args.reduce(flow, x => x);

// now, writing getJoke() becomes much easier
const getJoke2 = flowArgs(fetchJoke, toJson, parseJoke);
getJoke2(23).then(console.log); // "Time waits for no man. Unless that man is Chuck Norris."
```

That's much more readable: I can use a sequential execution model of the functions passed as arguments to `flowArgs()`.

I love this `flowArgs()` pattern, it has many advantages in terms of testability, encapsulation, and delayed execution.

## [](https://marmelab.com/blog/2018/04/18/functional-programming-2-monoid.html#conclusion)Conclusion

So monoids are pretty common, and their link with `Array.reduce` makes them super useful. Don't be frightened by the [academic articles on monoids](https://en.wikipedia.org/wiki/Monoid), which make them look harder than they actually are!

Any time you need to compose an arbitrary number of items (e.g. when flattening a hierarchy of objects, or when implementing a workflow of async operations), look for a monoid! That's another great learning from functional programming.

In the next post in this series, I'll talk about the superpowers hidden in `Array.map`. It will be the time for the `Functor`, and no this is not the name of a villain in Power Rangers.