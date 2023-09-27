# Naming

“You should name a variable using the same care with which you name a firstborn child.” - James O. Coplien [1](#cite01)

Human being identify everything by names. Naming is the most important aspect of coding.

So our classes, methods, members, functions, modules, variables, constants, properties names must be named clearly, understandably.

## [N1] Never use abbreviations unless agreed by the entire team and documented in as a list.

_For example:_ 

`db` is this a date of birth, or a database?

**Abbreviations in names must follow the language specified naming conventions.**

_For example:_ `mainPageUrl` in JavaScript. `.main-url` in CSS.

## [N2] Never use single letters for indexes or variables. Give meaningful names.

_For example:_

`for (let i=0; I < collection; I++) {...}` **this is bad!**

`for (let userIndex=0, numberOfUsers = users.length; userIndex < numberOfUsers; userIndex++) {...}` **this is good!**

## [N3] Do not use similar variable names.

_For example:_

`user`, `userObject`, `userInformation` it will be hard to understand the differences for other developers as well as yourself.

## [N4] Use English or any other language that you are using to name variables, do not add types, objects type indicators.

_For example:_ 

`intAccount`, this should be `accountNumber`.

`strUserNo`, this should be `userId`.

`userArray`, this should be `users` or `userCollection`.

`userObject`, this should be `user`.

## [N5] Avoid using language related reversed words.

## [N6] Git branch names must be lower case, words spared by '-' dashes.

## [N7] Folders names must be lower case, words separated by '-' dashes.

- [N-HTML]
	- File names must be lower case, words separated by '-' dashes.
	- All tags must be lower case, words separated by '-' dashes. (Web components)
	- All properties must be lower case, words separated by '-' dashes.
- [N-CSS]
	- File names must be lower case, words separated by '-' dashes.
	- Selector (Class) names must be lower case, words separated by '-' dashes.
- [N-JavaScript/TypeScript]
	- File names must be camel case. Class file names must start with uppercase.
	- Class names must be camel case, first letter must be uppercase.
	- Method, function, variable names must camel case, first letter must be lower case.
	- Constants names must be all upper case, words separated by '-' dashes.

## References

1. <a id="cite01"></a>Clean Code by Robert C. Martin, Introduction

