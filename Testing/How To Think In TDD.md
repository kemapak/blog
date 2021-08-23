# How To Think In TDD and Write Quality Code

**What is quality?**
>"The standard of something as measured against other things of a similar kind; the degree of excellence of something" --Apple Dictionary

**What is quality code?**
>A well tested, well written, and well documented code (self documented). That behaves and runs as expected, with minimal dependencies and strong cohesion. Code that is easy to understand and easy to maintain.

## Introduction
_Test Driven Development_ TDD for short advocates one simple but fundamental rule. Write your tests first, then your code.

TDD will make your code better, easier to understand. It will make you a better software engineer, a true craftsman.

By the way, when I say code, I meant the implementation, both tests and implementation are code and every software engineering principle does apply to both. It is not a surprise to see more lines of code in unit and automation tests than the implementation code.

Writing unit tests were not initially intuitive for me. Especially for web development. I wrote my entire code first and afterward tried to write the tests. If I ever had time to bother writing tests in the first place. It was very hard and unpleasant. My tests were not helpful except that I can brag about code coverage and I have tests.

After I started to write my test first and then implement the code things changed. It did change so dramatically I could not believe how it affected my thinking and coding. My code was way more robust, way easier to understand, and cover all the cases not only the happy path!

Just like riding a bicycle for the first time, it was really hard and awkward, but in a very short time frame writing tests first become easy and a habit, so addictive, that I cannot live without. I was happy and proud of my code and tests.

## How to Think in TDD
What I have here is a sample approach that will make you think about how to first write a test and then your code. Hopefully, will it demystify the TDD mythology and show how fun and simple it is.

### I want you to keep 4 rules in mind.
1. **Write A Test**: Think about one atomic functionality, the happy path first. Write the test for it. Yes, you do not write the implementation so your test will fail, which may not sound OK but this is the way TDD works.
1. **Write An Implementation**: Write the code just to make the test pass. Do not optimize, do not refactor your code, we will do next.
1. **Refactor And Optimize Your Code** Since the test are passing you can confidently improve and refactor your code if needed. Make sure you follow the refactoring patterns.
1. **Repeat Steps 1, 2 and 3**: Until you cover all happy paths and exceptions.
1. **Refactor, Optimize and Organize**: After you are finished a major functionality, make your code better while running your tests.

I will share several examples of how to write unit tests. The way I wrote and organize my code or the tools that I use. This is my preferred way does not mean it the best way or the only right way to write code. It is up to you to find what best fits your needs, your coding style, your tools. However, you need to write the same code with your coding style and tools to understand the mechanism and how to think in TDD.

The small code samples below illustrate the workings. It is meant to be a hands-on exercises. In each example please do read the README.md first. It has the details of the problem in the example and the steps on how to write the tests, the code, and finally how to refactor. Factorial is step by step, Histogram shows the tests, and it is a good review after you are done with Factorial.

(Factorial Example)[https://github.com/kemapak/factorial-tdd]
(Histogram Example)[https://github.com/kemapak/histogram-tdd]

Happy coding

Kem


