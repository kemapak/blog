# Classes

A class defines the structure and behavior of an object. This is the foundation of computer programming both in Object
Oriented Programming (OOP) and Prototype Based Programming (PBP). Depending on the language we have different flavors
or classes. Abstract, static, concrete and so forth. The most important point of designing and building classes is the
cohesion and coupling. These are the two main pillars of software engineering and architecture.

## [C1] Use good understandable names

"The name of a class should describe what responsibilities it fulfills" - Robert Martin [1](#cite01)

Naming is everything! See [naming](./naming.md) topic for details.

## [C2] Classes must be small, and have a single responsibility

"The first rule of classes is that they should be small. The second rule of classes is that they should be smaller than 
that."  - Robert Martin [1](#cite01)

Just like functions which we discussed, the classes should be small. There is one important difference though: 
Functions must have few statements, classes on the other hand must have few instance fields (properties) and methods 
(behavior). Excluding accessors, and common methods like toString, toValue, an instance class 
should have maximum of **12 public methods** and should have a maximum of **21 fields**. Utility and _static classes_ on 
the other hand, can have way more methods and fields as long as they are static. 

If an instance class has too many methods and too many fields, it is most likely to have multiple responsibilities. It 
must be refactored and divided into smaller classes.

A class should have one responsibility (**Single Responsibility Principle**). This rule should never be violated!

## [C3] Classes must be cohesive.

“Reference.” - Author Name Lastname [1](#cite01)

Text

_For example:_

```javascript
Code
```

## [S2] Classes must be independent (loosely coupled)

“Reference.” - Author Name Lastname [1](#cite01)

Text

_For example:_

```javascript
Code
```

## [S2] Keep inheritance to a minimum use interfaces instead

“Reference.” - Author Name Lastname [1](#cite01)

Text

_For example:_

```javascript
Code
```

## References

1. <a id="cite01"></a>Clean Code, Robert Martin, Classes
2. <a id="cite02"></a>Book Name, Author Name Last Name, Chapter

---

[Back to Code Review](../code-review.md)
