# Unit Tests

"Having dirty tests is equivalent to, if not worse than, having no tests." - Robert Martin [1](#cite01)

Actually in my opinion it is better to have no tests than bad tests. What a way to start promoting tests by saying
do not write tests if you are not going to really do it properly. May be shocking but this is the truth.

Wrong tests will give you false confidence or false concern. You will never know if your code is running as expected or 
not.

> Test code is real code, it must be clean and simple!

If you do not write your test properly, maintaining them could become a huge task by itself. The test code should be 
treated the same as production code. If you do not maintain your tests like your production code, it will become rotten. 
Instead, unit tests helping to maintain your code, they will be hassle, pain have around. Eventually you will stop 
running your unit tests, and even remove them completely, as a result your production code will decay and will be 
impossible to maintain.

"It is unit tests that keep our code flexible, maintainable, and reusable. The reason is simple. If you have tests, 
you do not fear making changes to the code! Without tests every change is a possible bug." - Robert Martin [1](#cite01)

> Unit tests are not written to catch bugs but prevent them. It is very different from end to end, 
> functional tests which are written to catch bugs and verify expectations.

## Test code structure and flow
**Setup -> Execution -> Verification -> Teardown**

## [UT1] Unit tests live together in same source directory with actual code
Unit tests and code are tightly coupled, they are meant to be together.

## [UT2] Test must be independent and repeatable.

A test should be able to run without any dependency to another test, and always produce the same result, regardless how 
many times you run it. They should not share same test data unless to you have a clean, virgin (initialized) set for 
each test.

## [UT3] Single concept per test (no conditionals and no try catch)
Each test should test one simple concept. They should not be dozens of asserts, there should not be conditionals, there
should not be try catch blocks. If you see a need for this split the tests.

In other words unit tests should not have any logic just test a single concept.

"So it’s not the multiple asserts in each section of Listing 9-8 that causes the problem. Rather it is the fact that
there is more than one concept being tested. So probably the best rule is that you should minimize the number of
asserts per concept and test just one concept per test function." - Robert Martin [1](#cite01)

## [UT4] Write your tests in GWT (BDD) format.
Write your tests in **Given**, **When**, **Then** format to be more readable and understandable. Remember unit test are 
the contract and documentation of your system. This format does not only apply to acceptance test only but to any type.

## What is TDD?
"Drive development with automated tests, a style of development called Test-Driven Development (TDD)." - Kent Beck [2](cite#2)

Unit test existed for a long time, but it was Kent Beck who brought TDD or Test Driven Development into the software engineering
scene by his classic and legendary book Test Driven Development by Example. He is also the inventor of XP eXtreme Programming.

If you want your development have a clean design, simple, testable code you use TDD. The goal TDD is clean code, 
clean design. It removes the stress out of the development process and give engineers the confidence one test at a time
with building each functionality one at a time.

The pattern of TDD is simple RED/GREEN/REFACTOR. You write the test first, run it, it fails (RED) obviously, then you 
right just enough code to pass the test (GREEN), then you make it better and improve (REFACTOR).

If you are going to write unit tests, it is way better to be written before you write your code. I will be very honest 
here. You cannot write good code or testable code if you do not write your unit tests first! Don't bother to write tests 
to look good!

But why you may ask!

TDD forces to you think about requirements, write the test first. Therefore, forces you to write testable cohesive code.
It blocks you to over-engineer any code! It blocks you to write monolithic code with 100 or even 1000 lines of methods,
functions. It forces you to follow unit of code guidelines (15 lines of code) [3](#cite03).

Personally it teaches how to write code, when to refactor, how to refactor. Makes coding a pleasure instead of a chore!

To learn more about TDD read the book [Test Driven Development by Example](https://www.informit.com/store/test-driven-development-by-example-9780321146533) by Kent Beck,
or go over the hand on exercises created by me [Learning TDD by factorial example](https://github.com/kemapak/factorial-tdd).

## Testing design patterns.
Test do not have tests! How can you maintain them the best possible way? If you do not refactor and keep your test code 
in clean and in good condition they will become rotten and your production code will share the same fate.
The best way to learn xUnit patterns is to read the awesome book by Gerard Meszaros [XUnit Test Patterns](http://xunitpatterns.com)
and check my blog [Unit test desing patterns](https://github.com/kemapak/blog/blob/master/testing/Testing%20Design%20Patterns%20for%20UI.md) for a summarized version.

## References

1. <a id="cite01"></a>Clean code, Robert Martin, Unit Tests
2. <a id="cite02"></a>Test-Driven Development: By Example, Kent Back, Preface
3. <a id="cite03"></a>Building Maintainable Software, Joost Visser, Write Short Units of Code
4. [XUnit Test Patterns](http://xunitpatterns.com), Gerard Meszaros
5. [Learning TDD by factorial example](https://github.com/kemapak/factorial-tdd), Kem Apak
6. [Unit test desing patterns](https://github.com/kemapak/blog/blob/master/testing/Testing%20Design%20Patterns%20for%20UI.md), Kem Apak

---

[Back to Code Review](../code-review.md)
