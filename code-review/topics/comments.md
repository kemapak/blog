# Comments

> "Don’t comment bad code, rewrite it." —Brian W. Kernighan and P. J. Plaugher [1](#cite01)

Comments are great! When well written they help the developer to explain his code, tell his/her story clearly. Sometimes a programming language is not enough to explain the complexity of the logic, exception, code. In these cases comments do come to rescue. In reality if you name your classes, methods, functions, variables well and write small functions, comments mostly become unnecessary. A good code should be self documented and comments should only be used sparely only when absolutely necessary.

**There are 3 types of comments**

1. Line comments.
2. Block comments.
3. Documentation comments.

> Comments must be written as a regular sentence. Start with an uppercase letter and ends with a period.

_For example:_

`This is a well written comment.`

`this is a badly written comment`

## Line comments
As the name indicates they are added to the top of the code (or sometimes to the end of the statement). These usually short and able to supplement the code (or exceptions) for more clear explanation in English or any language you use. Do not use multiple lines comments use block level comments.

_For example:_

JavaScript or TypeScript
```
// This is a line comment.
code
```

## Block comments
These comments are used if there a complex logic, exceptions. If you need more space than a line comment you need to use block level comments.

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


## [CMT1] Don't use comments


## References
1. <a id="cite01"></a>Clean Code by Robert C. Martin, Functions, Comments

---

[Back to Code Review](../code-review.md)