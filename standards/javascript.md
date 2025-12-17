# JavaScript Coding Standards
This document defines JavaScript coding standards to ensure **readability**, **consistency**, **maintainability**, and 
**long-term scalability** across the codebase. These rules are written to be enforceable via tooling (ESLint, Prettier) 
and easy to follow during day-to-day development.

## Table of Contents
* [Files & Directory:](#files--directory)
  * [DF-01 - JavaScript File Naming Convention](#df-01---javascript-file-naming-convention)
* [Style & Syntax](#style--syntax)
  * [JS-02 – Avoid JavaScript When Possible](#js-02--avoid-javascript-when-possible)
  * [JS-03 – Cohesion & Coupling](#js-03--cohesion--coupling)
  * [JS-04 – Units of Code](#js-04--units-of-code)
  * [JS-05 – Naming Conventions](#js-05--naming-conventions)
  * [JS-06 – Semicolons](#js-06--semicolons)
  * [JS-07 - Commas](#js-07---commas)
  * [JS-08 – Whitespace & Formatting](#js-08--whitespace--formatting)
  * [JS-09 – Strings](#js-09--strings)
  * [JS-10 – Curly Braces](#js-10--curly-braces)
  * [JS-11 – Comments](#js-11--comments)
  * [JS-12 – Derivable Properties](#js-12--derivable-properties)
  * [JS-13 – Conditionals & Equality](#js-13--conditionals--equality)
  * [JS-14 – Loops](#js-14--loops)
  * [JS-15 – Variables & Scope](#js-15--variables--scope)
  * [JS-16 – Strict Mode](#js-16--strict-mode)
  * [JS-17 – Anonymous Functions](#js-17--anonymous-functions)
  * [JS-18 – Inner Functions & Closures](#js-18--inner-functions--closures)
  * [JS-19 – this Keyword](#js-19--this-keyword)
  * [JS-20 – Exception Handling](#js-20--exception-handling)
  * [JS-21 – DOM Manipulation](#js-21--dom-manipulation)
  * [JS-22 - Private Methods and Fields](#js-22---private-methods-and-fields)
  * [JS-23 - Static Methods and Fields](#js-23---static-methods-and-fields)
  * [JS-24 - Use getters and setters for private fields](#js-24---use-getters-and-setters-for-private-fields)
  * [JS-25 – Inline JavaScript](#js-25--inline-javascript)
  * [JS-26 – External JavaScript](#js-26--external-javascript)
  * [JS-99 – Always Refactor](#js-99--always-refactor)



## Files & Directory:

### DF-01 - JavaScript File Naming Convention
File names should clearly describe **what the file is** and **how it is used**.
- Classes start with uppercase.
- Utilities start with lowercase.
- Use **camelCase** for multi-word names.
- No abbreviations unless formally agreed upon.
- **Unit tests** use `test` postfix.
- **Models** use `model` postfix.
- **Configurations** use `config` postfix.
- **Utilities** use 'util' postfix.
- JavaScript files end with `.js`.
- JSON files end with `.json`.

**Format**:
```text
class
[Name]*Name.js
[Name]*Name.type.js

or

other
[name]*Name.js
[name]*Name.json
[name]*Name.type.js
[name]*Name.type.json
```

**Examples**:
- `Card.js`
- `Card.test.js`
- `AdminUser.js`
- `AdminUser.model.js`
- `PhoneCatalog.js`
- `PhoneCatalog.test.js`
- `util.js`
- `util.test.js`
- `dataVisualization.util.js`
- `dataVisualization.util.test.js`
- `config.json`
- `userData.json`
- `index.js`

## Style & Syntax

### JS-02 – Avoid JavaScript When Possible
If a requirement can be fulfilled using **HTML or CSS alone**, do not use JavaScript.

### JS-03 – Cohesion & Coupling
- Methods must do **one thing only**.
- Prefer **high cohesion** and **low coupling**.
- Document unavoidable coupling.
- Prefer **Observer**, **Dependency Injection**, or **Event-based** patterns.

### JS-04 – Units of Code
- Each method/function must be **≤ 33 lines** and/or **≤ 15 statements** (excluding comments, blank lines and braces).
- Large methods must be refactored into smaller units.
- USE ESLint rules to enforce maximum complexity and size.

### JS-05 – Naming Conventions
**General Principles**
- **Naming is the most important aspect of self-documenting code**.
- Use **clear, full English words**.
- **Avoid abbreviations** unless formally agreed upon.

**Case Rules**
- Variables, functions, methods, fields: `camelCase`
- Classes: `PascalCase`
- Constants: `UPPER_SNAKE_CASE`

**Examples**:
```javascript
let userName = 'JohnDoe';

function disableUser() {}

class Person {}

const MAX_RETRY_COUNT = 3;
```

**Additional Rules**
- Avoid single-letter variables (e.g. `i`, `j`, `k`).
- Avoid numeric suffixes (e.g. `element2`, `index3`).
- Use domain terminology consistently.
- Acronyms follow normal casing: `homePageUrl`, `UriParser`.
- Boolean variables must use `is` / `has` prefixes.
- Use **nouns** for classes and variables.
- Use **verbs** for functions and methods.

### JS-06 – Semicolons
- Every statement must end with a semicolon.

### JS-07 - Commas
- Last collection member or an object property should not have a comma.

Example:
```javascript
// Not OK
let collection = [
    'a',
    'b',
    'c',
];

// OK
let collection = [
    'a',
    'b',
    'c'
];

// Not OK
let person = {
    name: 'John',
    lastName: 'Doe',
    age: 27,
    id: 'DFR123',
};

// Not OK
let person = {
    name: 'John',
    lastName: 'Doe',
    age: 27,
    id: 'DFR123'
};
```

### JS-08 – Whitespace & Formatting
- Use **4 spaces** for indentation.
- Maximum **120 characters per line**.
- One space around operators. (e.g. `user = 'adam';`,  `a >= b`, `function (a, b, c) {}`)
- No spaces for `++` / `--`.
- Logical blocks separated by blank lines.

### JS-09 – Strings
- Use **single quotes** (`'`) for JavaScript strings.
- **Never use double quotes** (`"`) in JS. 
  - It is OK if using **double quotes** in HTML strings (e.g. `let container = '<div class="container">...</div>'`).
  - It is OK using **double quotes** inside **single quotes**.
- Use **backtick** template literals/string (`\``) for templates and multiline strings.
- JSON **must use double quotes** for keys and string values.

### JS-10 – Curly Braces
- Always use braces, even for single-line blocks (including single line arrow functions).
- Opening brace on the same line.
- Closing brace on its own line.
- Closing brace on the same line if single statement.

**Examples**:
```javascript
// Not OK.
if (condition) {
    doSomething(); } 
else 
{
    doSomethingElse();
}

// OK
if (condition) {
    doSomething();
} else {
    doSomethingElse();
}

// Not OK
let greet = name => console.log(`Hello, ${name}!`);

// OK
let greet = (name) => { console.log(`Hello, ${name}!`); };
```

### JS-11 – Comments
**Comment only exceptions and things you cannot explain with code.**
- **Instead of adding a comment try to have better variable, method, function or class name.**
- **Do not comment unused code**, just remove it! Never commit commented-out code.
- For **temporary or exception** cases, add a TODO, the current date, and your name.
    - ` TODO <Date> <Developer Name>: Explanation.`
- Start with a space, uppercase letter, end with a period. Just like a regular sentence.
- Explain exceptions or overrides clearly

**Line Comments**
- Single-line only
- Must be on their own line.

**Example**:
```javascript
// This explains intent.

// TODO 12-12-20205 @Kem: Need to update some setting.
```

**Block Comments**
- For explaining complex logic only.

**Example**:
```javascript
/* 
There is some very complex multiline logic.
Which does require a lot of explanation. 
Which is not possible to convey just with code.
 */
```

**Documentation Comments (JSDoc)**
- Required for all classes, public methods and functions.
- Explains what it does.
- Shows the signature input parameters and returned values.
- Shows the exceptions thrown.

**Example**:
```javascript
/**
* Calculates if the application limit passed. 
* @param {number} count The count of calls.
* @returns {boolean} The application is passed or not.
* @throws {error} Not a number. 
*/
```

[JS Doc Reference](https://jsdoc.app)

### JS-12 – Derivable Properties
- Never recompute static values unnecessarily.
- Cache derived values and DOM references.

**Example**:
```javascript
// Not OK
let minutesInADay = 24 * 60;

// OK
// 24 * 60
let minutesInADay = 1440; 
```

- Cache DOM references using variables.
**Example**:
```javascript
let shopingListContainer = document.getElementById('shoppingListContainer');

shopingListContainer.className = 'container-empty'
```

### JS-13 – Conditionals & Equality
- Always use `===`, `!==` instead of `==`, `!=`.
- Place constants on the left side of comparisons.

**Example**:
```javascript
if ('admin' === userType) {
    ...
}
```

### JS-14 – Loops
- Avoid deep nesting.
- Avoid `continue`.
- Prefer `break` for early exits.
- Calculate the size of static collections in the initialization section of the loop. 
  - For dynamic collection this is OK.

**Examples**:
```javascript
// Not OK
for (let index = 0; index < collection.length; index++) {
...
}

// OK
for (let index = 0, maxIndex = collection.length; index < maxIndex; index++) {
    ...
}
```

### JS-15 – Variables & Scope
- Avoid global scope.
- **Do not use** `var`.
- Use `const` **only for constants**.
- Use `let` **for variables**.

**Examples**:
```javascript
// Not OK
var userName = 'JohnDoe';

// Not OK
for (var userIndex = 0, numberUsers = 10; userIndex <= numberOfUsers; userIndex++) {
    // Some loop logic.
}

// OK
let userName = 'JohnDoe';

// OK
for (let userIndex = 0, numberUsers = 10; userIndex <= numberOfUsers; userIndex++) {
    // Some loop logic.
}

// OK
const USER_CONFIG = {
    ...
};

// OK
const MAX_USERS = 10;
```

### JS-16 – Strict Mode
- Use only Classes and Modules.
- Explicit `use strict` is unnecessary.

### JS-17 – Anonymous Functions
- Use arrow functions for anonymous functions.

### JS-18 – Inner Functions & Closures
- Prefer external functions and private class methods. 
  - In rare occasion you can use inner functions to improve readability.
- Avoid using closures prefer classes and private methods and fields.

### JS-19 – this Keyword
- Use `this` keyword in classes, arrow functions and interface functions.
- Avoid using alias variables like `self`, `_this`, `that` to `this`.

**Example**:
```javascript
// Not OK
let self = this;
```

### JS-20 – Exception Handling
- Throw meaningful errors at low level functions and methods.
- High level methods shold only catch (handle) exceptions.
- Document exceptions using JSDoc.

> Read [how to code - exception and error hanlding](../how-to-code/topics/exception-and-error-handling.md) to learn more.

### JS-21 – DOM Manipulation
- Use `DocumentFragment` when creating dom structures. Add the fragments to DOM after it is complete.
- Prefer template literals strings `\``.
- Modify DOM via CSS classes and avoid updating inline styles.
- Avoid embedding CSS and HTML in JavaScript.

### JS-22 - Private Methods and Fields
- Use (`#`) to indicate private methods and fields in your classes.
- Avoid using (`_`) prefix to indicate private methods and fields.

### JS-23 - Static Methods and Fields
- Use `static` keyword to indicate class methods and fields.

### JS-24 - Use getters and setters for private fields
- Provide controlled access to class private fields.
- Provides encapsulation, logic execution, data validation setting private fields.

### JS-25 – Inline JavaScript
- Inline JavaScript must be avoided.

**Allowed exception**:
- Minimal bootstrapping or configuration initialization inside HTML (e.g., setting a root config object or feature flag).
- During developing and testing code.

**Not allowed**:
- Business logic
- DOM manipulation
- Event handling (unless required by framework)

**Examples**:
```html
// NOT OK
<script>

    function calculateDiscount(percent) {
        ...
    }
</script>
    
// NOT OK    
<button onclick="calculateDiscount(document.getElementById('discount').value)">Calculate Discount</button>

// OK
<script>
    let cart = {
      name: 'abc',
      items: [
          {...},
          {...}
      ]   
    } 
</script>

// OK with Angular
<button [disabled]="isDisabled">Click Me</button>
<input type="text" [value]="name" />
```

### JS-26 – External JavaScript
- All JavaScript logic must reside in external files.
- Each file must have a single, clear responsibility.
- One class per file.
- One utility module per file.
- One configuration per file.

### JS-99 – Always Refactor
- Clean code is a continuous process. 
- Refactor mercilessly. 
- Keep your kitchen clean.
- Learn Refactoring Patterns.
