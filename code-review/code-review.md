# Code Review
## Software development is a team sport.
I cannot say how many times I heard this, and I do know this is completely true. Software development is hard and one of the most important aspect a team of engineers is helping one another, helping each other. Collectively improve their technical knowledge, capability, expertise as well as domain knowledge they are building applications. One way to do this is code reviews.

> A team is strong as their weakest engineer. Build a team of star engineers by promoting continues learning, continues feedback, and most importantly trust.

## Sharing is caring
A senior engineer's most important job is to help and mentor junior engineers. One way to do this is code reviews.

## Blame game
When there is production issues, when there is a major flaw in an application blaming a junior engineer is the worst thing a person can do. It is the fault of the entire team, from the most senior to most junior engineer, from QA to engineering manager, to the architect. Everyone is to blame, the team is to blame. One way to reduce this is to do code reviews.

Code reviews are not personal, and should not be taken personally. The most important point is the reviewers should not blame and name a person when they see an issue. They must use the words like, "we can improve our code by doing this...", "if we do this there could be problem", "if we use this design pattern we can improve our code", and most importantly "what do you think? Can we do something different to improve our code and make it better?". Also never forget to complement. Positive motivation, can go a long way and make reviews something that every engineer look forward to. Complements could have names, and should have names. "Jim you wrote this perfectly.", "Jane you convert this complex algorithm to something so simple and beautiful"

> Make sure that everyone speaks up! With out worrying about any consequences.

## Automate basic review process
There is nothing equal a team review their own code together. Said that time will be never enough to go over everything. Even this is never talked it is true. Automate some of basic items. There are tools that can check the size of unit of code, cyclomatic complexity and most importantly unit tests, and code coverage. If these are in place you can improve complex, hard identify items instead of spending your time on basic stuff. 

> Note: we will go over unit of code, cyclomatic complexity in detail and a bit of unit test later.

## Code review process
TODO

## Code review items
- [Naming](./topics/naming.md). Naming is everything
- Unit of code. Small is always better
- Cyclomatic complexity. Simple is always better
- Unit Tests. Test first, code later (TDD, test driven development)
- Comments. What to say and when to say it? Is silence golden?
- `Readme.md` What and how to document!
- [Function, Methods](./topics/functions-methods.md). Are you cohesive enough.
- Dependency handling. Let's decouple!
- [Exception and Error handling](./topics/exception-and-error-handling.md). How to handle punches!
- Defensive coding. Let's do some aikido!
- Classes. Who are you, what can you do? 
- Interfaces. Let's add some behavior to make you a superman!
- Constants, variables and class properties. What are you, who are you?
- Public, Private or Static. Now you see me or may be not!
- Inheritance. Not all inheritance make you rich!
- Design Patterns. Software is life!
- Data, Model. Garbage in garbage out!
- Code Structure. What is where?
- Small changes. Can you release it now?

