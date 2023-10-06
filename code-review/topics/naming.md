# Naming

“You should name a variable using the same care with which you name a firstborn child.” - James O. Coplien [1](#cite01)

## [N1] Use good understandable names

“Don’t be afraid to make a name long. A long descriptive name is better 
than a short enigmatic name.” [2](#cite02)

Human beings identify everything by their names. Naming is the most important aspect of coding. Most important aspect of code documentation is good, simple, understandable names.

So our classes, methods, members, functions, modules, variables, constants, properties names must be named clearly, understandably.

## [N2] Do not use abbreviations unless agreed by the entire team and documented as a list.

_For example:_

`db` is this a date of birth, or a database?

**Abbreviations in names must follow the language specified naming conventions.**

`mainPageUrl` in JavaScript. `.main-page-url` in CSS.

The team needs to create and maintain a list of abbreviations which is allowed to be used.

| Abbreviation | Name | Comments |
|:--|:--|:--|
| Usr | User | User prefix. |
| Num | Number | - |
| Url | Uniform Resource Locator | Address, location of assets and services |

## [N3] Never use single letters for indexes or variables. Give meaningful names.

_For example:_

`for (let i=0; i < collection; i++) {...}` **this is really bad! What is index, what is collection?**

`for (let userIndex=0, numberOfUsers = users.length; userIndex < numberOfUsers; userIndex++) {...}` **this is good and clear!**

## [N4] Do not use similar variable names.

_For example:_

`user`, `userObject`, `userInformation` it will be hard to understand the differences for other developers as well as yourself.

## [N5] Use proper language to name variables, do not add types, objects type indicators.

_For example:_

`intAccount`, this should be `accountNumber`.

`strUserNo`, this should be `userId`.

`userArray`, this should be `users` or `userCollection`.

`userObject`, this should be `user`.

## [N6] Avoid using language related reversed words.

## [N7] Git branch names must be lower case, words spared by '-' dashes.

## [N8] Folders names must be lower case, words separated by '-' dashes.

## [N-HTML] HTML
	- File names must be lower case, words separated by '-' dashes.
	- All tags must be lower case, words separated by '-' dashes. (Web components)
	- All properties must be lower case, words separated by '-' dashes.

## [N-CSS] CSS
	- File names must be lower case, words separated by '-' dashes.
	- Selector (Class) names must be lower case, words separated by '-' dashes.

## [N-JavaScript] JavaScript (Applicable to TypeScript)
	- File names must be camel case. 
	- Class file names must start with uppercase.
	- Method, function, variable names must camel case, first letter must be lower case.
	- Constants names must be all upper case, words separated by '-' dashes. (except imports)

## References

1. <a id="cite01"></a>Clean Code by Robert C. Martin, Introduction
2. <a id="cite02"></a>Clean Code by Robert C. Martin, Naming

---

[Back to Code Review](../code-review.md)
