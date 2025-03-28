---
creation date: 03/27/2025
tags:
  - dev/functional-programming
url: https://www.adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html
---
---

Here's a simple value:

![](https://www.adit.io/imgs/functors/value.png)

And we know how to apply a function to this value:  
![](https://www.adit.io/imgs/functors/value_apply.png)

Simple enough. Lets extend this by saying that any value can be in a context. For now you can think of a context as a box that you can put a value in:

![[Pasted image 20250327230517.png]]

Now when you apply a function to this value, you'll get different results **depending on the context**. This is the idea that Functors, Applicatives, Monads, Arrows etc are all based on. The `Maybe` data type defines two related contexts:

![[Pasted image 20250327230532.png]]

```
data Maybe a = Nothing | Just a
```

In a second we'll see how function application is different when something is a `Just a` versus a `Nothing`. First let's talk about Functors!

---
## Functors

When a value is wrapped in a context, you can't apply a normal function to it:

![[Pasted image 20250327230545.png]]

This is where `fmap` comes in. `fmap` is from the street, `fmap` is hip to contexts. `fmap` knows how to apply functions to values that are wrapped in a context. For example, suppose you want to apply `(+3)` to `Just 2`. Use `fmap`:

```
> fmap (+3) (Just 2)
Just 5
```

![](https://www.adit.io/imgs/functors/fmap_apply.png)

**Bam!** `fmap` shows us how it's done! But how does `fmap` know how to apply the function?

## Just what is a Functor, really?

`Functor` is a [typeclass](http://learnyouahaskell.com/types-and-typeclasses#typeclasses-101). Here's the definition:

![[Pasted image 20250327230618.png]]

A `Functor` is any data type that defines how `fmap` applies to it. Here's how `fmap` works:

![[Pasted image 20250327230628.png]]

So we can do this:

```
> fmap (+3) (Just 2)
Just 5
```

And `fmap` magically applies this function, because `Maybe` is a Functor. It specifies how `fmap`applies to `Just`s and `Nothing`s:

```
instance Functor Maybe where
    fmap func (Just val) = Just (func val)
    fmap func Nothing = Nothing
```

Here's what is happening behind the scenes when we write `fmap (+3) (Just 2)`:

![[Pasted image 20250327230638.png]]

So then you're like, alright `fmap`, please apply `(+3)` to a `Nothing`?

![[Pasted image 20250327230647.png]]
```
> fmap (+3) Nothing
Nothing
```

![[Pasted image 20250327230659.png]]

Like Morpheus in the Matrix, `fmap` knows just what to do; you start with `Nothing`, and you end up with `Nothing`! `fmap` is zen. Now it makes sense why the `Maybe` data type exists. For example, here's how you work with a database record in a language without `Maybe`:

```
post = Post.find_by_id(1)
if post
  return post.title
else
  return nil
end
```

But in Haskell:

```
fmap (getPostTitle) (findPost 1)
```

If `findPost` returns a post, we will get the title with `getPostTitle`. If it returns `Nothing`, we will return `Nothing`! Pretty neat, huh? `<$>` is the infix version of `fmap`, so you will often see this instead:

```
getPostTitle <$> (findPost 1)
```

Here's another example: what happens when you apply a function to a list?

![[Pasted image 20250327230711.png]]

Lists are functors too! Here's the definition:

```
instance Functor [] where
    fmap = map
```

Okay, okay, one last example: what happens when you apply a function to another function?

```
fmap (+3) (+1)
```

Here's a function:

![[Pasted image 20250327230725.png]]
Here's a function applied to another function:

![[Pasted image 20250327230738.png]]

The result is just another function!

```
> import Control.Applicative
> let foo = fmap (+3) (+2)
> foo 10
15
```

So functions are Functors too!

```
instance Functor ((->) r) where
    fmap f g = f . g
```

When you use fmap on a function, you're just doing function composition!

---
## Applicatives
Applicatives take it to the next level. With an applicative, our values are wrapped in a context, just like Functors:

![[Pasted image 20250327230017.png]]

But our functions are wrapped in a context too!

![[Pasted image 20250327230027.png]]

Yeah. Let that sink in. Applicatives don’t kid around. Applicative defines `*` (`<*>` in Haskell), which knows how to apply a function wrapped in a context to a value wrapped in a context:

![[Pasted image 20250327230036.png]]

i.e.:

```python
>>> Just(lambda x: x+3) * Just(2) == Just(5)
True
```

Using `*` can lead to some interesting situations. For example:

```python
>>> List([lambda x: x*2, lambda y: y+3]) * List([1, 2, 3])
[2, 4, 6, 4, 5, 6]
```

![[Pasted image 20250327230050.png]]

**Here’s something you can do with Applicatives that you can’t do with Functors.** How do you apply a function that takes two arguments to two wrapped values?

```python
>>> (lambda x,y: x+y) % Just(5)
Just functools.partial(<function <lambda> at 0x1003c1bf8>, 5)

>>> Just(lambda x: x+5) % Just(5)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for <<: 'Just' and 'Just'

```

Applicatives:

```python
>>> (lambda x,y: x+y) % Just(5)
Just functools.partial(<function <lambda> at 0x1003c1bf8>, 5)

>>> Just(lambda x: x+5) * Just(5)
Just 10
```

`Applicative` pushes `Functor` aside. “Big boys can use functions with any number of arguments,” it says. “Armed with `%`and `*`, I can take any function that expects any number of unwrapped values. Then I pass it all wrapped values and get a wrapped value out! AHAHAHAHAH!”

```python
>>> (lambda x,y: x*y) % Just(5) * Just(3)
Just 15
```

And hey! There’s a method called `lift_a2` that does the same thing:

```python
>>> Just(5).lift_a2(lambda x,y: x*y, Just(3))
Just 15
```

---
## Monads

How to learn about Monads:

1. Get a PhD in computer science.
2. Throw it away because you don't need it for this section!

Monads add a new twist.

Functors apply a function to a wrapped value:
![[Pasted image 20250327225249.png]]

Applicatives apply a wrapped function to a wrapped value:
![[Pasted image 20250327225308.png]]

Monads apply a function **that returns a wrapped value** to a wrapped value. Monads have a function `>>=` (pronounced "bind") to do this.

Let's see an example. Good ol' `Maybe` is a monad:
![[Pasted image 20250327225331.png]]

Suppose `half` is a function that only works on even numbers:

```
half x = if even x
           then Just (x `div` 2)
           else Nothing
```

![[Pasted image 20250327225352.png]]

What if we feed it a wrapped value?

![[Pasted image 20250327225410.png]]

We need to use `>>=` to shove our wrapped value into the function. Here's a photo of `>>=`:

![[Pasted image 20250327225421.png]]

Here's how it works:

```
> Just 3 >>= half
Nothing
> Just 4 >>= half
Just 2
> Nothing >>= half
Nothing
```

What's happening inside? `Monad` is another typeclass. Here's a partial definition:

```
class Monad m where
    (>>=) :: m a -> (a -> m b) -> m b
```

Where `>>=` is:

![[Pasted image 20250327225437.png]]

```
instance Monad Maybe where
    Nothing >>= func = Nothing
    Just val >>= func  = func val
```

Here it is in action with a `Just 3`!

![[Pasted image 20250327225450.png]]

And if you pass in a `Nothing` it's even simpler:

![[Pasted image 20250327225510.png]]

You can also chain these calls:

```
> Just 20 >>= half >>= half >>= half
Nothing
```

![[Pasted image 20250327225520.png]]

![[Pasted image 20250327225530.png]]

Cool stuff! So now we know that `Maybe` is a `Functor`, an `Applicative`, and a `Monad`.

Now let's mosey on over to another example: the `IO` monad:

![[Pasted image 20250327225543.png]]

Specifically three functions. `getLine` takes no arguments and gets user input:

![[Pasted image 20250327225554.png]]

```
getLine :: IO String
```

`readFile` takes a string (a filename) and returns that file's contents:

![[Pasted image 20250327225604.png]]

```
readFile :: FilePath -> IO String
```

`putStrLn` takes a string and prints it:

![[Pasted image 20250327225616.png]]

```
putStrLn :: String -> IO ()
```

All three functions take a regular value (or no value) and return a wrapped value. We can chain all of these using `>>=`!

![[Pasted image 20250327225627.png]]

```
getLine >>= readFile >>= putStrLn
```

Aw yeah! Front row seats to the monad show!

Haskell also provides us with some syntactical sugar for monads, called `do` notation:

```
foo = do
    filename <- getLine
    contents <- readFile filename
    putStrLn contents
```
## what is a maybe (a monad)

1.  A functor is a data type that implements the `Functor` abstract base class.
2.  An applicative is a data type that implements the `Applicative` abstract base class.
3.  A monad is a data type that implements the `Monad` abstract base class.
4.  A `Maybe` implements all three, so it is a functor, an applicative, and a monad.

What is the difference between the three?
![[Pasted image 20250327225118.png]]
-   **functors**: you apply a function to a wrapped value using `map` or `%`
-   **applicatives**: you apply a wrapped function to a wrapped value using `*` or `lift`
-   **monads**: you apply a function that returns a wrapped value, to a wrapped value using ´|´ or `bind`

So, dear friend (I think we are friends by this point), I think we both agree that monads are easy and a SMART IDEA(tm). Now that you've wet your whistle on this guide, why not pull a Mel Gibson and grab the whole bottle. Check out LYAH's [section on Monads](http://learnyouahaskell.com/a-fistful-of-monads). There's a lot of things I've glossed over because Miran does a great job going in-depth with this stuff.