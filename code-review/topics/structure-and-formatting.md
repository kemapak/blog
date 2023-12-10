# Structure and Formatting

As software engineers, we claim to be a professional craftsman. How we write, how we organize and structure our code indeed proves if we are professionals or not.

Bob Martin in his Clean Code book indicates that we should keep our code nicely formatted, have simple set of rules agreed within our teams and use a tool do to this.

Formatting, organizing and structuring your code is fundamental to properly communicate with other software engineers.

## [SF1] File size (Class or module size)

The smaller the file size the better to read and understand. This follows the same principle of size of unit of code. 
Unlike unit of code for 14 lines, file size there is no exact guidance, but if it is too larger just divide it.

## [SF2] Group related files together
For example utility classes should be grouped under a "utility" folder. Similarly, _for example:_ a web component should have
all the HTML, CSS, JavaScript, Unit Tests and assets (images, videos, etc) in the same folder

```shell
  \components
  
      \componentExample
        \assets
            open.jpeg
            close.jpeg
            intro.mpg
        component-example.html
        component-example.css
        component-example.js
        component-example.test.js
        readme.md
        
      \anotherComponentExample
        ...
```

## [SF3] Class fields/members

Class fields needs to be declared at the top. If private, their getter and setter should follow the declaration.

_For example:_

```javascript
class Person {
	
  #name;
	
  get name() {
    return this.#name;
  }

  constructor(nameParam) {
    this.#name = nameParam;
  }
}
```

## [SF4] Methods, functions

They need to be declared from general at the top to the details in the bottom. In other words main functions, methods 
should be declared at the top and methods, functions they call should be declared afterward.

This is like giving the summary first and details later.

_For example:_

```javascript
class Person {
    
    // Summary - Generic
    contructor() {
        
        this.methodOne();
        this.methodTwo();
    }
    
    // Detailed - Specific
    methodOne() {
        
        this.methodThree();
    }

    // Detailed - Specific
    methodTwo() {
        
    }

    // Detailed - Specific
    methodThree() {
        
    }
}

```

## [SF5] Variable declarations
Variables should be declared closest where they are used.

Loop variables should be declared within the loop.

## [SF6] Paragraph

Just like a paragraph related code that describes a concept should be grouped together seperated by spaces at the top and
bottom, just like a paragraph.

Even better they should be moved to its own function.

_For example:_

```javascript
function example() {
    
    ...
    ...
    
    ...
    ...
    
    ...
    
}
```

## [SF7] Line width
Just like file sizes shorter lines are easier to read. You should never scroll horizontally to read a line of code.
Have standard in your team but usually it is either 80 or 120 characters, since the new monitors do have way more 
horizontal space.

## [SF8] Horizontal spacing
"We use horizontal white space to associate things that are strongly related and disassociate things that are more 
weakly related." - [1](#cite01)

_For example:_

```javascript
 index++;
 let a = b;
 function x(paramOne, paramTwo) {...}
 let y = x(5, 6);
```

## [SF9] Indentation

Indentation shows hierarchy and scope of your code. Indentation shows the position in the hierarchy of the line. 
"Without indentation, programs would be virtually unreadable by humans." - [1](#cite01)

Use spaces or tabs that is agreed within your team. I use spaces (2 for HTML, CSS and 4 for JavaScript, JSON).


## References

1. <a id="cite01"></a>Clean Code by Robert C. Martin, Formatting

---

[Back to Code Review](../code-review.md)
