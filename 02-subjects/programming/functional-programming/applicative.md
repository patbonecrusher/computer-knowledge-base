---
creation date: 03/27/2025
tags:
  - dev/functional-programming
---
---
## Definition

Applicative is a sub-type of [functor](02-subjects/programming/functional-programming/functor.md) with additional available functions: `pure` and `ap`.

```javascript
function pure<A>(A) : Foo<A>  
function ap<A, B>(Foo<A => B>, Foo<A>) : Foo<B>
```

`pure` should take a value of any type and return an applicative functor with that value inside it. When we say inside it, we're using the box analogy again, even though we've seen that it doesn't always stand up to scrutiny. But the a -> f a type declaration is still pretty descriptive. We take a value, and we wrap it in an applicative functor that has that value as the result inside it.  A better way of thinking about pure would be to say that it takes a value and puts it in some default (or pure) context—a minimal context that still yields that value.

The `<*>` function is really interesting. It has a type declaration of `f (a -> b) -> f a -> f b`. Does this remind you of anything? Of course, `fmap : : (a -> b) -> f a -> f b`. It's a sort of a beefed-up fmap. Whereas fmap takes a function and a functor and applies the function inside the functor, `<*>` takes a functor that has a function in it and another functor and sort of extracts that function from the first functor and then maps it over the second one. When I say extract, I actually sort of mean run and then extract, maybe even sequence. We'll see why soon.

`pure` places a value into a minimal context, and `ap` serves the purpose of function application within a context. `map` lets you apply a normal function to a value inside a functor, getting a functor that holds a new value in an unchanged functor context. `ap` goes further; given a function and a value that are both already inside functor contexts, it combines these contexts and puts the result of the function application into the new context.

So another way to look at `ap` is that it lets us turn a function _within a context into a function that operates _on contexts_. Effectively `ap` can let us lift a function through a functor.

The most important takeaway while learning to use applicatives is that `ap` behaves like normal function application, just inside of a functor, and that `pure` produces contexts that can be combined with other contexts without modifying the other context.


---
