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

A class should have one responsibility. This rule should never be violated! It is called **Single Responsibility 
Principle, SRP**

## [C3] Classes must be cohesive.

Make sure your instance fields and methods bind together as a whole logically. Follow the single responsibility 
principle. Cohesive classes are usually small classes. When a class loses cohesion, split it.

Do not modify your classes to add functionality but extend them with subclasses. This is called **Open Close Principle, 
OCP**. A class is open for extension, but is closed for modification.

## [C3] Classes must be independent (loosely coupled)

Freedom, independence is good for human beings as well as classes. Try to decouple your classes from other classes, modules, 
packages as much as possible. This makes it easy to test, easy to modify without impacting other parts of your software. 
If you need to add a dependency, which happens quite often, pass other classes (instantiated) and methods as a parameter. 
This is called ** Dependency Injection, DI **. Also, you can use interfaces, abstract classes, decorator pattern, template 
method pattern to manage the dependencies, this is called **Dependency Inversion Principle, DIP**. Move the implementation
details to the sub, concrete classes. Our classes should depend on abstractions not concrete details.

## [S2] Keep inheritance to a minimum use interfaces instead

Even one of the core mechanism of OO is inheritance, try to keep your system flat as much as possible. Do not inherit 
more than 3 levels. Instead, use interfaces and decorator pattern as much as possible.

## References

1. <a id="cite01"></a>Clean Code, Robert Martin, Classes

---

[Back to Code Review](../code-review.md)
