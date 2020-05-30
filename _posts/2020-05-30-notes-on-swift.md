# What Swift has borrowed from other languages

Notes on reading about Swift, and what it makes me think of from other languages

## C#

* Nullability is part of type system
* `nil`-safe accessors
* property willSet/didSet
  
## Scala
* Algebraic data types (sort of, with enums)
* Deconstruction with switch statements
* Expressive type system
* Autoclosures (nee call-by-name parameters)

## Go
* defer
* if-let

## Unique
* Subscripts

## Misc. Notes

### Danger!
* exception-ignoring try?
* Covariance?
* Escaping closures must be declared explicitly? Why not just GC closures?
* Argument label vs. parameter name

## Comparison of Swift/Objective-C terminology with "standard" terminology

Objective-C (other languages):

* interface (header)
* implementation (implementation)
* protocol (interface)
* category (extension)
