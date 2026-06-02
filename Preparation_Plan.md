# Automation Testing Interview Preparation Roadmap (Target: 1 Year Experience)

## Study Weightage

| Topic | Weightage |
|---------|---------|
| Playwright | 45% |
| TypeScript | 25% |
| Framework Design (POM) | 15% |
| Manual Testing | 10% |
| Git + SQL + Jenkins | 5% |

---

# Phase 1: TypeScript

## Basics

- Variables (`let`, `const`)
- Data Types
  - string
  - number
  - boolean
  - any
  - void
- Type Inference
- Type Annotation

## Operators

- Arithmetic Operators
- Comparison Operators
- Logical Operators
- Ternary Operator

## Control Statements

- if
- if-else
- else-if
- switch

## Loops

- for
- while
- do-while
- for-of
- for-in

## Functions

- Function Declaration
- Function Expression
- Arrow Function
- Parameters
- Optional Parameters
- Default Parameters
- Return Types

## Arrays

- Array Creation
- Accessing Elements

### Array Methods

- push()
- pop()
- shift()
- unshift()
- concat()
- slice()
- splice()
- indexOf()
- includes()
- toString()

## Objects

- Object Creation
- Add Properties
- Update Properties
- Delete Properties

## OOP Concepts

### Classes

- Class Creation
- Object Creation
- Constructor
- this Keyword

### Access Modifiers

- public
- private
- protected

### Inheritance

- extends
- super()

### Polymorphism

- Method Overriding

### Interface

- Interface Creation
- implements
- Interface vs Class

### Modules

- export
- import
- export default

## Exception Handling

- try
- catch
- finally
- throw

## Async Programming

### Promises

- Promise
- resolve
- reject

### Async/Await

- async
- await

---

# Phase 2: Playwright

## Introduction

- What is Playwright?
- Advantages of Playwright
- Playwright Architecture

## Browser Management

- Browser
- BrowserContext
- Page

## Locators

### CSS Selectors

- id
- class
- attribute
- parent-child

### XPath

- Absolute XPath
- Relative XPath
- contains()
- text()

### Playwright Locators

- getByRole()
- getByText()
- getByLabel()
- getByPlaceholder()
- locator()

## Actions

- click()
- fill()
- type()
- check()
- uncheck()
- selectOption()
- hover()
- dblclick()

## Assertions

- toHaveText()
- toContainText()
- toBeVisible()
- toBeHidden()
- toHaveTitle()
- toHaveURL()
- toBeChecked()

## Waits

- Auto Waiting
- waitFor()
- waitForURL()
- waitForLoadState()

## Web Elements

- Textbox
- Checkbox
- Radio Button
- Dropdown

## Alerts

- Alert
- Confirm
- Prompt

## Frames

- iframe
- frameLocator()

## Multiple Tabs / Windows

- Popup Handling
- Promise.all()

## File Handling

### Upload

- setInputFiles()

### Download

- Download Event

## Mouse Actions

- Hover
- Right Click
- Double Click
- Drag and Drop

## Keyboard Actions

- press()
- keyboard.type()

## Screenshots & Videos

- page.screenshot()
- Screenshot Configuration
- Video Recording

## Hooks

- beforeAll
- beforeEach
- afterEach
- afterAll

## Fixtures

- Built-in Fixtures
- Custom Fixtures

## Test Execution Controls

- test.describe()
- test.only()
- test.skip()

## Retry Mechanism

- retries

## Parallel Execution

- fullyParallel
- workers

## Configuration

### playwright.config.ts

- baseURL
- timeout
- retries
- reporter
- projects

## Environment Variables

- .env
- process.env

## API Testing

### HTTP Methods

- GET
- POST
- PUT
- DELETE

### Playwright API Methods

- request.get()
- request.post()
- request.put()
- request.delete()

## Network Handling

- Route Interception
- Mock API Response

## Reporting

- HTML Report
- Playwright Report

---

# Phase 3: Framework Design

## Page Object Model (POM)

- What is POM?
- Why POM?
- Advantages of POM

## Folder Structure

```text
tests/
pages/
utils/
fixtures/
test-data/
playwright.config.ts
```

## Page Classes

- Locators
- Methods

## Utility Classes

Examples:

- Screenshot Utility
- Date Utility
- Wait Utility

## Test Data Management

- JSON Files
- Separate Data Files

## Base Page

Reusable Methods:

- click()
- fill()
- waitForElement()

---

# Phase 4: Git

## Git Basics

```bash
git clone
git status
git add .
git commit -m "message"
git push
git pull
```

## Branching

```bash
git branch
git checkout
git merge
```

## Git Concepts

- Repository
- Branch
- Merge
- Merge Conflict

---

# Phase 5: CI/CD

## CI/CD Concepts

- What is CI?
- What is CD?
- Why CI/CD?

## Jenkins Basics

- Jenkins Overview
- Job
- Build
- Trigger Build

## Pipeline Understanding

Flow:

Developer Pushes Code

↓

Git Repository

↓

Jenkins Build Triggered

↓

Automation Tests Executed

↓

Report Generated

↓

Pass / Fail Result

---

# Phase 6: SQL

## Basic Queries

```sql
SELECT
WHERE
ORDER BY
DISTINCT
```

## Aggregate Functions

```sql
COUNT()
SUM()
AVG()
MIN()
MAX()
```

## Grouping

```sql
GROUP BY
HAVING
```

## Joins

```sql
INNER JOIN
LEFT JOIN
RIGHT JOIN
```

---

# Phase 7: Manual Testing

## SDLC

- Requirement Gathering
- Design
- Development
- Testing
- Deployment
- Maintenance

## STLC

- Requirement Analysis
- Test Planning
- Test Design
- Environment Setup
- Test Execution
- Test Closure

## Testing Types

- Smoke Testing
- Sanity Testing
- Regression Testing
- Retesting
- Functional Testing
- Integration Testing
- System Testing
- UAT (User Acceptance Testing)

## Defect Management

- Defect Life Cycle
- Severity
- Priority

## Documentation

- Test Case
- Test Scenario
- Bug Report

---

# Last 15 Days Revision Plan

## TypeScript

- OOP
- Async/Await
- Promises
- Interfaces
- Modules

## Playwright

- Locators
- Assertions
- Waits
- Hooks
- Fixtures
- POM

## Manual Testing

- STLC
- SDLC
- Severity vs Priority
- Testing Types

## SQL

- SELECT
- JOINS
- GROUP BY

## Git

- pull
- push
- branch
- merge

## Jenkins

- CI/CD Flow

---

# Final Priority Order

## Tier 1 (Must Learn)

1. Manual Testing
2. Playwright
3. TypeScript Basics
4. POM Framework
5. Git

## Tier 2 (Good to Have)

6. SQL
7. API Testing
8. Jenkins CI/CD

## Tier 3 (Optional)

9. Docker
10. Advanced TypeScript
11. Advanced Jenkins

---

# Goal

By the end of preparation, you should be able to:

- Build a Playwright Framework from scratch
- Create Page Object Model Framework
- Write API Tests
- Handle Git Operations
- Explain CI/CD Flow
- Write Basic SQL Queries
- Answer Manual Testing Questions
- Answer TypeScript OOP Questions
- Crack 1-Year Experience Automation Testing Interviews
