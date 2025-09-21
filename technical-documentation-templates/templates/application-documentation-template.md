# Application documentation template

## Feature 
Description of the feature, links to product documentation (Should be under the same documentation directory).

| Name            | Link(s)        | Comment                                                  |
|:----------------|:---------------|:---------------------------------------------------------|
| Awesome feature | [F123456]('#') | This have all the user stories, tickets for this feature |

## Table of Contents
{{TOC}}

## Team
| Members             | Name(s)    | Comment                                                  |
|:--------------------|:-----------|:---------------------------------------------------------|
| Engineering Manager | John Doe   | a@z.com                                                  |
| Product             | Jane Doe   | b@z.com                                                  |      
| Design              | John Smith | c@z.com                                                  |
| A11y                | Jane Smith | d@z.com                                                  |
| QA                  | John Abc   | e@z.com                                                  |
| Engineering         | Jane Abc   | f@z.com                                                  |
| Architecture        | John Xyz   | g@z.com                                                  |

## Description
What does the application do, what is the specific functionality. This could be a child to the main application. 
A micro frontend, a smart component.

## Application Links
- QA [full url]('#')
- Staging [full url]('#')
- Prod [full url]('#')

## Test credentials
Usernames, password and comments that explain the user type, or the environment, settings.

| Username | Password           | Environment | Comments             |
|:---------|:-------------------|:------------|:---------------------|
| abcd     | verySecret@123     | QA          | for type X users     |
| admin    | topSecret@456      | QA          | for admin type users |
| prodTest | ultimateSecret@789 | Prod        | for prod test user   |

## Design links
This could be Figma or any other URL that point to low and/or high fidelity designs. _For example:_

- [Phase one, desktop]('#')
- [Phase one, mobile]('#')
- [Admin users, desktop]('#')
- [Admin users, mobile]('#')
- [Accessibility annotations]('#')

## Repo links
GitHub or GitLab repo, any additional component or utility library URLs.

## CI/CD pipeline links
Jenkins, Harness links

## Application local setup
This should be a link to the `README.md` file in your repo. If there are additional notes you can describe here.

## Technical design
If the application has an architecture or technical pages we need to add the links here (hopefully together with code in
the repo). If we do not have them in repo we can add our technical design directly here.

## Middle tier
If we have any middle tier, like backend for frontend (BFF) we add the information or links here.

## APIs
Name and URI of the APIs, and any comments related.

| Name        | Link             | Comments        |
|:------------|:-----------------|:----------------|
| doSomething | /api/dosomething | Does something. |


## Backend Services
Names and comments. 

| Name        | Comments                 |
|:------------|:-------------------------|
| userProfile | User profile management. |

## Accessibility (A11y)
If we have any exceptions, or important information we document here. _For example_, external PDF files are 
not accessible, or 3rd party software we are using is not accessible, or a11y design annotation comments for 
custom components or our special code, approach to address a11y needs.

## Cookies, session and local storage
List of cookies, web storage that are used, their purpose, type and life span.

| Name | Type        | Purpose       | LifeSpan | Comments               |
|:-----|:------------|:--------------|:---------|:-----------------------|
| a    | http cookie | get something | Session  | JavaScript cannot read | 

**Types:**
- cookie http
- cookie session
- cookie persistent
- local storage
- session storage

## Feature flags
List of feature flags,  their purpose, links and life spans. 

_Important note:_ Make sure you follow your companies feature flag naming conventions, development, and maintenance 
practices. 

| Name              | Purpose                                  | LifeSpan   | Link                | Comments      |
|:------------------|:-----------------------------------------|:-----------|:--------------------|:--------------|
| ffForYourEyesOnly | Show new feature to potential customers. | 01/01/2025 | [featureFlag]('#')  | Some details. | 

## Knowledge transfer
If you are inheriting an application this could be links to other documentation, or your notes, video/audio recordings, 
contact information. Please note since you now own the application you need to move all the other documentation under 
the same document directory, and format it if necessary.

---
Return to [Technical documentation templates](../technical-documentation-templates.md)