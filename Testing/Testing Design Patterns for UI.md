# UI Unit Testing Design Patterns

> "It is better not to have any tests than having unreliable tests."

So here I am trying to advocate writing good tests and asking you not to write tests just for the sake writing tests. The question is does tests improves quality of our code? The answer in my opinion is only good tests result in good code. Bad tests will only give you a false and very dangerous confidence with nice code coverage report.

This document try's to explain automated unit testing design patterns and concepts. The expectation with these patterns is to make test more robust, simple, and do depict the functionality, state, and behavior of our code.

> Remember: **Unit test are written to prevent bugs, not to catch them.**

## Benefits and Characteristics

1. Verify correct behavior and state; in other words both positive and negative. 
1. Be predictable and stable: always return what is expected.
1. Be resilient: always return what is expected in single or multiple runs.
1. Allow refactoring safely and with confidence.
1. Force good code design.
1. Document the system and the code, and its contract.

## Terms

### Unit of Code
A cohesive chunk of code.

The recommended size is 33 lines of statements. (Excluding, comments, declarations, imports, and exports)

### Cohesion
Measurement of the atomic functionality of a code group. (Function, method). 

A method, the function should do one and only one thing. Strong cohesion indicates robust and maintainable code.

### Coupling
Measurement of the dependency of a code group to another. Most of the time dependencies in code cannot be avoided but there are several design patterns that help to manage de as dependency injection, avoiding internal instantiation of dependent classes, etc.

In testing Mocks and Spies patterns are used to have dependencies.

Loose coupling indicates robust maintainable code.

### Patterns
A general repeatable solution to a commonly occurring coding design and implementation problem.
		
### Anti- Patterns
A solution that is usually counterproductive or ineffective in a code design and implementation.

### SUT
System Under Test - Primary Object
				
System, Component, Class Under Test. In other words Primary Object of the test.

### Collaborator	
Secondary Objects
			
Secondary component, class, method that helps to the test the SUT. In other words Secondary Object(s) of the test.

Usually mocked, stubbed, or spied.
		
### Test Case
Testing a certain behavior or state of class, part of a class, a method or part of a method.

### Test Suite
Group of related test cases. A test suite is usually for a Class, Module, or Component. Test suites can include other test suites.
	
### Fixture
A test fixture is the code setup designated to verify SUT.
				
A fix state of the environment is used for software testing, so the results are predictable and repeatable.
				
Certain markup, browser, or run environment are good examples. 

Fixtures only apply to unit tests.
		
_For example_:
```html
<tablist id="tabContainer">
	<tab>One</tab>
	<tab>Two</tab>
	<tab-panel>Content One</tab-panel>
	<tab-panel>Content Two</tab-panel>
</tablist>
```

### Stub
Mimics actual objects and their data. Generally used to verify state.

If you want to have a database on memory (using JS Maps, with save, get, delete methods). This is also called a Fake. 

If you want to replace real rest calls with stubs mimicking a server.

### Spies
It verifies a method that is called or how many times it is called without calling the real method. 

The return value of the spied method is not irrelevant.

If the return value is important than you need to use a mock.

### Mocks
They are used to test behavior as well. They are similar to stubs but the called methods are pre-programmed with expectations, which form a specification of the calls they receive. In other words, mock objects and their methods are pre-programmed for specific calls to verify the behavior.

### Test Driven Development
Writing tests first with respect to the functionality desired, then writing enough code to pass the test before writing the next test/functionality.

_For example_: `test sum 2 + 2 is 4`

### Behavior Driven Development
Very similar to TDD but when writing test we indicate the expected behavior.

_For example_: `it should return the sum of 4 when 2 + 2 is passed as a parameter`

It is the wording but enables to read your test like regular sentences.

### Code Coverage
The measurement of the code tested in a code group. Including if each function/method is called, if each statement is executed, if each conditional (and therefore branch) statement executed.

## Patterns

### Pauses or Delay (anti-pattern)
Do not use artificial pauses, explicit waits, sleeps. This will make your test more fragile. Use framework given smart waits, implicit waits, async/wait. If the code for some reason does not execute the system wide timeout will kick in.

_For example_: `sleep(300);`

### Fixture Management 
#### Setup 
##### Inline Setup
If the fixture is simple, it does not need to be used in multiple test cases. The fixture is created inside a test case. 
TODO: Add example;

##### Implicit Setup (Test Suite)
This is usually called before each.
In setup creates fixture for each test. The fixture is not shared by each test cases and a fresh copy is used.
TODO: Add example;

##### Delegated Setup
Call utility methods to create a test fixture. If a fixture is repeated in multiple test cases, instead of copying and initializing the fixture in each test, a utility method can be used to create the fixture. The fixture should not be shared directly and a fresh copy is used each time.
TODO: Add example;

##### Chained Setup (Anti Pattern)
Use the leftover, updated fixture from a previous tests. This makes tests dependent, coupled to each other thus makes fragile. In other words issues with tests become hard to find and isolate. The fixture is initialized in the test suite and each test case updates the fixture. Therefore creates test dependencies and unexpected failures.
TODO: Add example;

#### Teardown
##### Inline Teardown
If the fixture is simple, it does not need to be used in multiple test cases. The fixture is destroyed after verification inside a test case.

##### Implicit Teardown (Test Suite)
This is usually called after each.
This is the most common pattern for teardown. In a teardown of the test suite, it destroys fixture for each test.

##### Automated teardown / Garbage collected teardown (anti-pattern).
If no explicit teardown is necessary the garbage collector destroys the fixture. This pattern is OK if the fixture is created inside a test case.

**For fixtures created in test suites setup it is not recommended.**

#### Test Value Management
This pattern is used for managing values that in tests; for fixtures, and in exercising and verification stages. Sometimes using helper methods could make the code simpler and more descriptive.

##### Literal
When you use literal constants in the tests to set up, exercise, and verify your code, you can use value literals. Literal values are clear to humans about the intention.
On the other hand, hardcoded literals usually make it harder to understand the intent of test sometimes. But if the data value does not impact the flow or validation of the text, then generated values are better to use. See the Generated section below.

_For example_:

```javascript
this.itemTitle = 'Meeting with Steve'; 
this.expanded = false;
```

##### Derived
Use this if the values in your test can be derived deterministically. Either via a utility method or an explicit statement.

_For example_:

```javascript
// In the case we just need a display name is the combination of a user first name and last name.
this.displayName = testUtil.getDisplayName(this.firstName, this.lastName);
```

##### Generated
Most of the tests do not need data legible by humans. For example, a name could be any string value. For these types of values, you can use creative methods in utility files. Generate a unique string, number, date, etc., literals or even certain objects would work for any field, variable.
Make the test more descriptive, and decouple from hard coded data.

_For example_:

```javascript
// In the case we just need a string value for the user name field. It does not be a specific value like Joe or Jane.
this.userName = testUtil.generateString();
```

#### Verification (Assertions)
##### State Assertion
This is the assertion of the expected state of SUT after the setup and exercise stages. This is the most common pattern used in verification. See the example below:

_For example_:

```javascript
// Checks the subtitle is no longer in the DOM.
let tab = document.querySelector('tab.tab-active'); 
expect(tab).to.equal(null);
```

##### Delta Assertion
This is the assertion of the difference or delta of the pre and post-state of the test. See the example below:

_For example_:

```javascript
// Setup
beforeEach(function() {
 warehouse = new Warehouse({"Fanta":10,"Cola":10,"Sprite":10});
});

// In the test case exercise stage.
warehouse.addProduct('Drink', 'Pepsi', 2);
warehouse.orderProducts('Drink');

// Verifies the difference or the delta remaining items.
expect.equal(8, warehouse.getInventory("Pepsi");
```

##### Behavior Assertion
This is the assertion for indirect outputs. For example, dispatching an event, calling a method, messages sent, etc. This pattern uses spies in general.

_For example_:

```javascript
// Example from sinonjs.org
require("@fatso83/mini-mocha").install(); const sinon = require("sinon");
const PubSub = require("pubsub-js");
const referee = require("@sinonjs/referee"); describe("PubSub", function() {
it("should call subscribers on publish", function() { const callback = sinon.spy();
          PubSub.subscribe("message", callback);
          PubSub.publishSync("message");
expect(callback.called).to.be.true; });
});
```

##### Custom Assertion
This assertion is not common, but it is one of the most useful testing patterns. A custom assertion makes the code more readable. This pattern encapsulates all the duplicate and conditional logic of verification logic into a single utility assertion method.

_For example_:(anti-pattern)

```javascript
// Antipattern. DO NOT WRITE YOUR TESTS LIKE THIS.
// Address set using inline pattern.
it ("Address should have type home", function(){

 let address = new Address({...});

 // Check if address if not null.
if (null !== address || "undefined" !== typeof address || null !== address.type || "undefined" !== typeof address.type || "string") {
 expect.fail("Not a valid Address.");
}

 expect(typeof address.type).to.be.equal("string");
 expect(address.type).to.be.equal("home");
}
```

_For example_: (with custom assertion)

```javascript
it ("Address should have type home", function(){
 // Address set using inline pattern.
 let address = new Address({...});
 
 expect(address).to.be.a.validAddress();
 expect(typeof address.type).to.be.equal("string");
 expect(address.type).to.be.equal("home");
}
```

Each testing framework should have the capability of writing custom assertions. For example here is some information in [Chai assertion library](https://www.chaijs.com/guide/helpers/)

##### Guarded Assertion
This assertion is not common, but it is very important for creating pure tests. In other words, it encapsulates exceptions and conditionals. When a test has an unexpected condition, it could show up as a test error instead of a test failure. It is better to check the condition explicitly, instead of using try/catch or conditionals.
Similar to the code example for the Custom Assertion pattern examples, the following code is written with try/catch:

_For example_: (anti-pattern)

```javascript
// Anti-pattern. DO NOT WRITE YOUR TESTS LIKE THIS.
it ("Address should have type home", function(){
// Address set using inline pattern.
let address = new Address({...});

try {
 expect(typeof address.type).to.be.equal("string"); expect(address.type).to.be.equal("home");
} catch (e) {
 expect.fail("Not a valid address!");
}
});
```

A better way to write the same code and also test if the address is valid instead of causing a test code error is below.

_For example_: (with guarded assertion)

```javascript
it ("Address should have type home", function(){ 

// Address set using inline pattern.
let address = new Address({...});

expect(address).to.be.a.validAddress();
expect(typeof address.type).to.be.equal("string"); expect(address.type).to.be.equal("home");
}
```

##### Unfinished Test Assertion
While you are writing your tests and they are incomplete this pattern puts and explicit TODO. The incomplete tests fail as a reminder.

_For example_:

```javascript
it ("Should fail since the test code is not written or complete.", function() {

// TODO implement the test code.
expect.fail("Unfinished Test!");
});
```


## Testing Trouble Shooting

### When the code is hard to test

|Probem|Solution|
|:--|:--|
|The development code is very large and complex. The unit code is too large, methods perform multiple tasks and are not cohesive. Dependencies are not easy to mock | Development needs to refactor the actual code.|
|Testing asynchronous non-blocking UI functionality| Use async/await, callback in your tests.|
|||

### When the Test is hard to understand

|Problem|Solution|
|:--|:--|
|The test code is not easy to read, test cases do not describe clearly what is tested.| The unit of code is too large. There are conditionals and try/catches. There are too many internal helper functionality that could be externalized into helper methods.|

### When there are too many bugs in production or other Testing Layers

|Casues|
|:---|
|Not testing the right code. Not enough test coverage.|

### When the Tests are fragile

|Problem|Solution|
|:--|:--|
|The test fails when SUT changes | If the actual component changes, your tests might fail, update your tests.|
|The test fails when dependencies are changed.|In unit test dependencies needs to mocked.|
|The test fails when run out of order|The test needs to be isolated and able to run independently|
|The test fails erratically.
Sometimes it passes sometimes and other fails.|Fixtures are not fresh. New tests are needed to check the state of SUT.
Collaborators / Secondary Objects needs to be stable and predictable. Tests use explicit waits, pauses; convert them to async / await or smart waits.|

### When there are Code and Configuration Leaks

|Problem|Solution|
|:--|:--|
|Test configuration or test code is published to production.
|Test code and configuration should not be leaked to production. Change your code.|

### When there are too many Assertions

|Problem|Solution|
|:--|:--|
|Test cases have too many assertions, it is not clear what is tested or if the test fails what is failed.|Refactor the test into multiple test cases which will have fewer and more cohesive assertions|

### When there are Conditional Test Logic

|Problem|Solution|
|:--|:--|
|Unit tests are strictly controlled. If you have conditional logic in a test it may or may not be executed.| **Do not use conditional logic.** Use Custom and Guarded Assertion patterns|

### When there are errors handling in Tests

|Problem|Solution|
|:--|:--|
|Your test code must be deterministic. It is OK to test if a method throws an exception but it is not OK to use try and catch in your test code.
Solution| **Do not use try and catch.** Use Custom and Guarded Assertion patterns|

### When the tests are slow.

|Problem|Solution|
|:--|:--|
|Test takes too long to run and slows the development as well as the build/verification process.|There should be no explicit pauses in your test. Check your collaborators/secondary object are mocked correctly or performing as expected. If by nature the test will be a slow one move it to a different test bucket, via tags or different test suite.|

## Reference

- [XUnit Test Patterns](http://xunitpatterns.com)
- [What's the difference between a mock & stub?](https://stackoverflow.com/questions/3459287/whats-the-difference-between-a-mock-stub/17810004%2317810004)
- [Mocks Aren't Stubs](https://martinfowler.com/articles/mocksArentStubs.html)
- [Automated Testing Patterns and Smells](https://www.youtube.com/watch?v=Pq6LHFM4JvE) (**Video**)

## Dilema

Who will test the test code?

- Make sure you follow the coding standards.
- Lint your code.
- Do not write large bulky code.
- Keep cohesion and coupling always in mind.
- Avoid dependencies and mock them.
- Write small tests
- Write and use utility methods.
- Write and use custom assertions.