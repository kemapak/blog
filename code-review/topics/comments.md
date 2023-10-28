# Comments

> "Don’t comment bad code, rewrite it." — Brian W. Kernighan and P. J. Plaugher [1](#cite01)

Comments are great! When well written they help the developer to explain his code, tell his/her story clearly. Sometimes a programming language is not enough to explain the complexity of the logic, exception, code. In these cases comments do come to rescue. In reality if you name your classes, methods, functions, variables well and write small functions, comments mostly become unnecessary. A good code should be self documented and comments should only be used sparely only when absolutely necessary.

**There are 3 types of comments**

1. Line comments.
2. Block comments.
3. Documentation comments.

> Comments must be written as a regular sentence. Start with an uppercase letter and end with a period.

_For example:_

`This is a well written comment.`

`this is a badly written comment`

> Do not decorate your comments.

## Line comments
As the name indicates they are added to the top of the code (or sometimes to the end of the statement). These usually short and able to supplement the code (or exceptions) for more clear explanation in English or any language you use. Do not use multiple lines comments use block level comments.

_For example:_

JavaScript or TypeScript
```
// This is a line comment.
code
```

## Block comments
These comments are used if there a complex logic, exceptions. If you need more space than a line comment to explain your intend, you need to use block level comments.

_For example:_
### JavaScript or TypeScript
```
/* 
   This is a block comment.
   Another line.
   Yet another line.
*/
code   
```

### HTML
```
<!-- This a comment. -->

<!-- 
	This is another comment.
	Which has multiple lines. 
-->
```

### CSS
```
/* This is a comment. */

/* 
	This is another comment.
	Which has multiple lines. 
*/
```

## Documentation comments

Documentation comments are extremely valuable and necessary for explaining your methods, classes to other developers and are used to generate your systems technical documentation, interface. JSDocs, JavaDocs are good examples of these.

Please check [JS Doc Reference](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html) for more information.

## [CMT1] Don't use comments

> "The proper use of comments is to compensate for our failure to express ourself in code." — Robert C. Martin  [1](#cite01)

- Check your code if the comment is necessary! Are you stating the obvious? Are you repeating what your code says?

_Antipattern_

```
  // This is user object.
  let user = {
	  firstName: '',
	  lastName: ''
  }
```

- Can you rename a variable, method, function? Can you extract a block of code into a function and name it accordingly to avoid using a comment?

_Antipattern_

```
// Check if employee is eligible for full benefits.
if((true === employee.fullTime) && (67 < employee.age)) then {
	...
} 
```

Should be written as below. The whole number check is extracted into its own method.

_Good names and methods instead of comments._

```
if (employee.isEligableForFullBenefits()) {
	...
}
```

- Is your code too long you use comments as markers to indicate start end finish? Divide your code into modules, functions. In the case below we create a web component that encapsulates the left navigation to simplify our code without need of using comments.

_Antipattern_

```
<!-- Start of left navigation -->
<nav>
	<ul>
		<li><a href="index.html">home</li>
		...
	</ul>
</nav>
<!-- End of left navigation -->

```

_Modularized HTML instead of comments._

```
	<left-nav></left-nav>
```

- Are you afraid that you need to revert some complex code so you commented it out and live it in? Do you possibly need bring it back and old code if the requirements changes so you commented the code and checked in? This completely unnecessary unless you are currently working on it. When you check in your code it must be in pristine condition and you can always revert back using SCM (source control management). That is the reason we use SCMs, awesome applications like git! Below code is not OK!

_Antipattern_

```
 // Change for user story 12345
 // function someVeryComplexWeirdCrazyCode() {
 //  ...
 //}
```

## [CMT2] Use comments

> “Truth can only be found in one place: the code.” Robert C. Martin  [1](#cite01)

The above statement is absolutely true but in certain cases our code needs additional support to explain the engineer's intend by adding some necessary information. Below are main use cases.

- Sometimes our company do requires legal comments, licenses, etc.

- Sometimes explaining a very complex logic, a warning about a side effect in English is necessary.

- We might need to add TODO comments if there is additional work has to be done.  It is OK as long as we take care of them in a short period of time. It is not OK to leave TODOs for months or even years. Add a TODO always with a date.

	`// TODO @Kem Apak 2023-10-28 Move the whole number logic into it's own method.`

- Using documentation comments like JSDocs or JavaDocs for our methods, functions, classes are required. This is necessary to help our fellow engineers who will use our code. [2](#cite02)

- Finally, if you need and only must to write a comment it must be clearly explain the indent!

## References
1. <a id="cite01"></a>Clean Code by Robert C. Martin, Comments
2. <a id="cite02"></a>[JS Doc Reference](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html)
---

[Back to Code Review](../code-review.md)