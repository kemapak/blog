# Unit Tests

"Having dirty tests is equivalent to, if not worse than, having no tests." - Robert Martin [1](#cite01)

Actually in my opinion it is better to have no tests then bad tests. What a way to start promoting tests by saying
do not write tests if you are not going to really do it properly. May be shocking but this is the truth.

Wrong tests will give you false confidence or false concern. You will never know if your code is running as expected or 
not.

> Test code is real code, it must be clean and simple!

If you do not write your test properly, maintaining them could become a huge task by itself.

> Unit tests are not written to catch bugs but prevent them. It is very different from end to end, 
> functional tests which are written to catch bugs.

> Unit Test Flow: **Setup -> Execution -> Verification -> Teardown**

## What is TDD?
If you are going to write unit tests, it is a must be written first, before you write your code. I will be very honest here.
You cannot write good code or testable code if you do not write your unit tests first! 

But why you may ask!

Unit test existed for a long time, but it was Kent Beck who brought TDD or Test Driven Development into the software engineering
scene, by eXtreme Programming and by his classic and legendary book Test Driven Development by Example. 

TDD forces to you think about requirements, write the test first. Therefore, forces you to write testable cohesive code.
It blocks you to over-engineer any code! It blocks you to write monolithic code with 100 or even 1000 lines of methods, 
functions. It forces you to follow unit of code guidelines (15 lines of code) [2](#cite02).

Personally it teaches how to code, when to refactor, how to refactor.

To learn more about TDD read the book [Test Driven Development by Example](https://www.informit.com/store/test-driven-development-by-example-9780321146533) by Kent Beck, 
or go over the hand on exercises created by me [Learning TDD by factorial example](https://github.com/kemapak/factorial-tdd).

## Testing design patterns.
If you do not refactor and keep your test code in good condition your production code will same the same fate.
The best way to learn xUnit patterns is to read the awesome book by Gerard Meszaros [XUnit Test Patterns](http://xunitpatterns.com)
and check my blog [Unit test desing patterns](https://github.com/kemapak/blog/blob/master/testing/Testing%20Design%20Patterns%20for%20UI.md) 
for a summarized version.

## [UT1] Single concept per test
Each test should test one simple concept. They should not be dozens of asserts, there should not be conditionals, there 
should not be try catch blocks. If you see a need for this split the tests.

"So it’s not the multiple asserts in each section of Listing 9-8 that causes the problem. Rather it is the fact that 
there is more than one concept being tested. So probably the best rule is that you should minimize the number of 
asserts per concept and test just one concept per test function." - Robert Martin [1](#cite01)

## [S2] Test must be independent and repeatable.

A test should be able to run without any dependency to another test, and always produce the same result, regardless how 
many times you run it.

## [S3] Write your tests in BDD format.
Write your tests in **Given**, **When**, **Then** format to be more readable and understandable. Remember unit test are the contract
and documentation of your system.

## References

1. <a id="cite01"></a>Clean code, Robert Martin, Unit Tests
2. <a id="cite02"></a>Building Maintainable Software, Joost Visser, Write Short Units of Code
3. xUnit Patterns, Gerard Meszaros
4. Learning TDD with Factorial, Kem Apak
5. xUnit Design Patterns, Kem Apak

---

[Back to Code Review](../code-review.md)
