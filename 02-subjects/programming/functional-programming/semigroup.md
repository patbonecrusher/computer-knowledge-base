---
creation date: 03/27/2025
tags:
  - dev/functional-programming
---
---
## definition
"In mathematics, a **semigroup** is an [algebraic structure](https://en.wikipedia.org/wiki/Algebraic_structure "Algebraic structure") consisting of a [set](https://en.wikipedia.org/wiki/Set_(mathematics) "Set (mathematics)")together with an [associative](https://en.wikipedia.org/wiki/Associative "Associative") internal [binary operation](https://en.wikipedia.org/wiki/Binary_operation "Binary operation") on it." **Wikipedia**

The idea is semigroups come from abstract algebra. We are encoding this in our code to keep the name the same and understand the laws and properties of this mathematical structure rather than just making something up on our own.

The following Sum class is a semigroup because it has a concat operation available.  It is associative because we can Sum (1+3) or Sum (3+1)

```python
class Sum():
	def __init__(self, x: Any):
		super(Sum, self).__init__()
		self.x = x

	def concat(self, o: Sum):
		return Sum(self.x + o.x)

	def __str__(self) -> str:
		return f"Sum({self.x})"
```

We can turn it into a [monoid](02-subjects/programming/functional-programming/monoid.md) by adding an identity function (empty)

```python
class Sum():
	def __init__(self, x: Any):
		super(Sum, self).__init__()
		self.x = x

	def concat(self, o: Sum):
		return Sum(self.x + o.x)

	def __str__(self) -> str:
		return f"Sum({self.x})"

	@staticmethod
	def empty():
		return Sum(0)
```

Positive [integers](https://en.wikipedia.org/wiki/Integer "Integer") with addition form a commutative semigroup that is not a monoid, whereas the non-negative [integers](https://en.wikipedia.org/wiki/Integer "Integer") do form a monoid. A semigroup without an identity element can be easily turned into a monoid by just adding an identity element.
