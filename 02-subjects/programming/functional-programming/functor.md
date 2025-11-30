---
creation date: 03/27/2025
tags:
  - dev/functional-programming
---
---
## Definition
A functor is a data structure that acts like a container holding a generic type.  A more correct term for what a functor is would be computational context.

If we want to make a type constructor an instance of Functor, it has to have a kind of \* ->\*, which means that it has to take exactly one concrete type as a type parameter.  For example, Maybe can be made an instance because it takes one type parameter to produce a concrete type, like Maybe Int or Maybe String.   *If a type constructor takes two parameters, like Either, we have to partially apply the type constructor until it only takes one type parameter.*

Functor works on a type parameter that takes only one parameters.

There must be a `map` function defined for that data structure, which applies a function to the contents of that functor.  


```python
class Functor f where
    fmap :: (a -> b) -> f a -> f b
```

It is an abstraction that wraps a value into a context and allows mapping over it. Mapping means applying a function to a value to get another value.   

It's a form of morphism that enables different types to be mappable.   In python, `list`, `set`, `tuple`, and `array` can be used with the `map` function to iterate over elements.  However, this is not the case for other types.  

## Example
Let's say we wanted to make a panda series mappable; we could do the following:

```python
import abc
import pandas as pd

from typing import Generic, TypeVar, Callable, Union

A = TypeVar('A')
B = TypeVar('B')

class Functor(Generic[A], metaclass=abc.ABCMeta):
	@abc.abstractmethod
	def fmap(self, f: Callable[[A], B]) -> 'Functor[B]':
		raise NotImplemented

class FSeries(pd.Series, Functor):
	def fmap(self, f):
		return self.apply(f).astype(self.dtype)

series = FSeries([1, 2, 3], index=['one', 'two', 'three'])
print(series.fmap(lambda x: x*3))

# would output
one 3
two 6
three 9
```

Functors are the base of other functional concepts, such as [functor-applicative-monad in pictures](02-subjects/programming/functional-programming/functor-applicative-monad%20in%20pictures.md) like the `Maybe`, `IO`, or `Either` monad and such as [applicative](02-subjects/programming/functional-programming/applicative.md).

## Laws
For something to be a functor, its `map` function has to obey two laws.

1.  `map` must preserve identity. That is, for any functor `f`, `map(x => x, f)` has to be equal to `f`. This is called “identity” because the function which returns whatever value it was called without changing it is often referred to as “the identity function” or `id`. This function is implemented as `x => x`.
2.  `map` must preserve function composition. For any functor `f` and any functions `foo` and `bar`, `map(foo, map(bar, f))` must be equal to `map(contents => foo(bar(contents)), f)`.

## Properties
An important property of functors is that the composition of two functors is also a functor. That is, given a functor `Foo<A>` and a functor `Bar<A>`, we can define the type `type FooBar<A> = Foo<Bar<A>>`, and define the `mapFooBar`function as so:

```python
mapFooBar<A, B>(fn: A => B, a: FooBar<A>) : FooBar<B> {  
  return mapFoo(x => mapBar(fn, x), a);  
}
```

As long as `mapFoo` and `mapBar` follow the functor laws, `mapFooBar` will also.

---
