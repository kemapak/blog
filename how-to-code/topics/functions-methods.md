# Functions and Methods

“Functions are the first line of organization in any program.” [1](#cite01)

## [FM1] Functions and methods must be small.

“The first rule of functions is that they should be small. The second rule of functions is that 
they should be smaller than that.” [1](#cite01)

Functions and methods should not exceed 44 lines of code, excluding comments, white spaces. If it 
is large, break it up. [2](#cite02)

If your methods, functions are small and named properly your code is already in good shape.

Small functions are methods are also easier to test.

## [FM2] Functions and methods must be cohesive.

The functions and methods should to one and only one thing. If it is does more than one thing 
break it up.

If you have multiple conditionals, loops you most probably are not cohesive. Move them to new
functions and give them logical names.

Avoid side effects, functions must either do something or answer a question not both.

## [FM3] Manage dependencies, loose coupling

Any code that has dependencies are more complex, harder to maintain. Reduce dependencies as much as 
you can. Said that it is impossible to completely and always decoupled. The question becomes how you 
manage it.

Pass instantiated classes, callback functions as parameters. Avoid to instantiating classes inside your 
methods, functions as much as you can. Move dependencies to the class level or module level

Use modules, packages and import external packages, classes, functions to use them.

## [FM4] Passing parameters.

Name your parameters well. See [naming](./naming.md) guidelines.

If you have more than 3 parameters create an object and pass them as part of an object.

_For example:_ 

```
function(name, lastName, street, city, zip, phone, email) {
}
```

into

```javascript
function person( 
    {
        name: 'John', 
        lastName: 'Doe', 
        street: 'Abc Drive', 
        city: 'San Diego', 
        zip: 12345, 
        phone: '(111) 222-3333', 
        email: 'john.doe@example.com'
    }) {
}
```

## [FM5] Order of the methods and functions should be top down.

Your order should be from general to specific. In other words, summary to details.

_For example:_

If method main() is calling subOne() and subOne is calling  subTwo() the order should be as follows

```
class Example {

    constructor() {
       
    }
    
    main() {
    
        subOne();
    }
    
    subOne() {
    
        subTwo();
    }
    
    subTwo() {
    
    }
}
```

## Refactoring Pattern, Extract to Method/Function
Refactoring is not random. We use patterns to refactor our code. This is an important pattern to 
learn, and it is very easy.

If you see a function, method is doing multiple things. You can cut that code and move it to a 
new function, method. And call it from your current function.

Most IDEs do already have tooling to support this. So you do not need to almost anything.

_For example:_

```
function factorial(parameter) {
    if ('number' !== typeof parameter) {
        throw new Error(parameter + ' is not a number.');
    }
    
    if (parameter < 0) {
        throw new Error(parameter + ' is a negative number.');
    }
    
    if (parameter !== Math.trunc(parameter)) {
        throw new Error(parameter + ' is a decimal number.');
    }
    
    if (0 === parameter) {
        return 1;
    }
    
    if (1 === parameter) {
        return 1;
    }
    
    if (parameter > 1) {
        return parameter * factorial(parameter - 1);
    }
}
```

into this below. The whole number check is extracted into its own method.

```
function factorial(parameter) {
	if (false === isWholeNumber(parameter)) {
		throw new Error(parameter + ' is not a whole number.');
	}

	if (0 === parameter || 1 === parameter) {
		return 1;
	}

	if (parameter > 1) {
		return parameter * factorial(parameter - 1);
	}
}
```

## References
1. <a id="cite01"></a>Clean Code by Robert C. Martin, Functions
2. <a id="cite02"></a>Code Simplicity by Max Kanat-Alexander
3. <a id="cite03"></a>Refactoring by Martin Fowler
---

[Back to Code Review](../code-review.md)