# Cost of Software Defects

## What is quality software?
- From the business and customer perspective a system that runs, executes as expected. Enables the user to
finish a task successfully.

## What is needed to have quality software?
- First, consistency of the user interface, ease of use, performant, defect free, predictable, reliable.
  - A consistent user interface consists of common components instead of custom
  - A good and simple information architecture, how easy to navigate, how many pages, click does it take a user to land on page they want.
- Second, easy to maintain, modular, loosely coupled and cohesive
  - Have the necessary tools to measure the health of the system, unit of code, cyclomatic complexity (loops, conditionals), modularization.
- Third, to have the testing/validation pyramid executed with automated tests. 
  - TDD, unit tests, e2e tests, layout tests, security tests, accessibility tests, performance tests, acceptance tests.
- Fourth, education, knowledge and experience of the engineering and architecture team.
- Finally, a well focused organization, with a leadership team that does not allow politics but has a common goal.
  - Allow team to make mistakes, and correct them
  - Constant improvement, learning.
  - Instead of top to bottom decision-making mechanism, it has a system of meritocracy to make technical, product and business decisions.
  - Everyone has a say in the decision, depending on their knowledge and experience.
  - Award employees by recognizing their work and achievements.
  - Have small, cohesive teams that can work independently!

## What is the cost of lack of quality software?
In software engineering books we learn fixing defects in software development life cycles is the cheapest during the development,
and tenfold expensive after it is released. 

Also lost of opportunity the time wasted to fix the defects. Lost of customers confidence. Even these are not easy measure
they are facts.

According to Nasa it costs 10-11 times more to fix a defect in production compare to development.
(Error Cost Escalation Through the Project Life Cycle)[https://ntrs.nasa.gov/api/citations/20100036670/downloads/20100036670.pdf]

According to (Forbes/CISQ)[https://www.forbes.com/sites/forbestechcouncil/2023/12/26/costly-code-the-price-of-software-errors/?sh=43805ea43242]
software defects cost $2.08 trillion dollar to US economy.

## How to calculate cost of fixing bugs?

Every company is different, depending on, how agile, how lean, how their test automation, CI/CD and code quality is they will 
spend less or more to fix bugs. According to Adam Tornhill, CTO of CodeScene it is twice as fast and easier to fix defects
in code bases that are healthy.

Basic calculation, ignoring the customer impact, and lost of opportunity to use the developer to write functional software improve 
the product. It is for each defect, how many people worked (QA, engineer, customer service, product, management, dev ops, etc), how many hours
times the cost of their hourly rate to the company.

Cost of fixing a defect = (personA hours spend * hourly cost A) + (personB hours spend * hourly cost B) + .....

If you are working in an archaic technology company the cost will be even, way more. For example if you do not have unit tests, 
automated e2e tests, functional tests, you might introduce new bugs fixing the current one.

