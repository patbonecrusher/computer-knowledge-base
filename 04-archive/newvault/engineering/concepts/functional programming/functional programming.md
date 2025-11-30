---
creation date: 03/27/2025
tags:
  - dev/functional-programming
---

---

![[04-archive/newvault/engineering/concepts/functional programming/attachments/Screenshot 2025-03-27 at 22.37.14.png]]

[functor](04-archive/newvault/engineering/concepts/functional%20programming/functor.md)
[applicative](04-archive/newvault/engineering/concepts/functional%20programming/applicative.md)
[semigroup](04-archive/newvault/engineering/concepts/functional%20programming/semigroup.md)
[monoid](04-archive/newvault/engineering/concepts/functional%20programming/monoid.md)


---
## Glossary

## First-class function
If you can treat a function as a value, it is a first-class Function.
* You can assign it to a variable.
* You can pass it in as an argument to another function.
* You can return it from a function.

## High-order function
Functions that operate on other functions, either by taking them as arguments or by returning them.

## Pure function
A Pure Function is **a function (a block of code) that always returns the same result if the same arguments are passed**. It does not depend on any state or data change during a program's execution. Rather, it only depends on its input arguments.

## Do
**The do notation is just syntactic sugar for monadic composition**. On the surface, it looks a lot like imperative code, but it translates directly to a sequence of binds and lambda expressions.

Example for the IO Functor
*The result of mapping something over an I/O action will be an I/O action, so right off the bat, we use **do** syntax to glue two actions and make a new one.*
