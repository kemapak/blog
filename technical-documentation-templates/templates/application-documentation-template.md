# Application documentation template
(Replace the title with yours)

## Feature 
Description of the feature, links to product documentation (Should be under the same documentation directory).

| Name         | Link(s)        | Date   | Status  | 
|:-------------|:---------------|:-------|:--------|
| Feature name | [F123456]('#') | Value  | Value   |

> Note: Feature link will have all the user stories, tickets for this feature.

> Note: Status could be: planning, in progress, cancelled, blocked, complete. 

## Table of Contents
* [Team](#team)
* [Description](#description)
* [Testing](#testing)
* [Application Links](#application-links)
* [Test credentials](#test-credentials)
* [Design links](#design-links)
* [Repo links](#repo-links)
* [CI/CD pipeline links](#cicd-pipeline-links)
* [Application local setup](#application-local-setup)
* [Technical design](#technical-design)
* [Architectural design](#architectural-design)
* [Middle tier](#middle-tier)
* [APIs](#apis)
* [Backend Services](#backend-services)
* [Accessibility (A11y)](#accessibility-a11y)
* [Cookies, session and local storage](#cookies-session-and-local-storage)
* [Feature flags](#feature-flags)
* [Knowledge transfer](#knowledge-transfer)
* [Open items](#open-items)
* [Related content](#related-content)

## Team
| Members             | Name(s)      |
|:--------------------|:-------------|
| Engineering Manager | John Doe     | 
| Product             | Jane Doe     |       
| Design              | John Smith   | 
| A11y                | Jane Smith   | 
| QA                  | John Abc     | 
| Engineering         | Jane Abc     | 
| Architecture        | John Xyz     |

## Description
What does the application do, what is the specific functionality, describe it here. This could be a child to the main 
application, a micro frontend or a smart component.

## Testing
Document all the automated (and God forbid manual) tests. Unit, e2e, performance, a11y, security, integration.

## Application Links
- QA [full url]('#')
- Staging [full url]('#')
- Prod [full url]('#')

## Test credentials
Usernames, password and comments that explain the user type, or the environment, settings.

| Username | Password           | Environment | Comments                         |
|:---------|:-------------------|:------------|:---------------------------------|
| abcd     | verySecret@123     | QA          | for specific functionality users |
| admin    | topSecret@456      | QA          | for admin type users             |
| prodTest | ultimateSecret@789 | Prod        | for prod test user               |

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

## Architectural design
Add the links to architectural design if exits.

## Middle tier
If we have any middle tier, like backend for frontend (BFF) we add the information or links here.

## APIs
Name and URI of the APIs, and any comments related. Add the payloads.

| Name        | Uri              | Comments        |
|:------------|:-----------------|:----------------|
| doSomething | /api/dosomething | Does something. |


## Backend Services
Name and URI of the services, and any comments related. Add the payloads.

| Name        | Uri                  | Comments                 |
|:------------|:---------------------|:-------------------------|
| userProfile | /service/userProfile | User profile management. |

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

| Name                 | Purpose                                  | LifeSpan   | Link               | Comments      |
|:---------------------|:-----------------------------------------|:-----------|:-------------------|:--------------|
| ffShowSpecialFeature | Show new feature to potential customers. | 01/01/2025 | [featureFlag]('#') | Some details. | 

## Knowledge transfer
If you are inheriting an application this could be links to other documentation, or your notes, video/audio recordings, 
contact information. Please note since you now own the application you need to move all the other documentation under 
the same document directory, and format it if necessary.

## Open items
| Issue | Description               | Owner               | Status                  | Comments |
|:------|:--------------------------|:--------------------|:------------------------|:---------|
| Name  | Details, description.     | Team and/or name(s) | Open-Assigned-Resolved  | Comments |

## Related content
Add the links to the related documents. Coding standards, NFR requirements, etc.
- [Coding standards](#)
- [Ally standards](#)
- [Frameworks, libraries used](#)
- [Other related content](#)

---
Return to [Technical documentation templates](../technical-documentation-templates.md)