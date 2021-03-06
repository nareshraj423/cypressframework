# cypressframework (Cucumber + Cypress + GitHub Actions + Docker)
This cypress framework automatically attaches screenshots to failed cucumber steps so that they will appear on Cucumber reports.
## Installation :

1. Download this project and type below commands in the terminal: 
	```bash
	npm install
	```
2. How to run the bundled tests from CLI:
	```bash
	npm run cy:scripts
	```
3. How to run the bundled tests from Cypress Test Runner:
	```bash
	npm run cy:open
	```
	
# In a nutshell
Cypress is a next generation front end testing tool built for the modern web. It addresses the key pain points that the developers and QA engineers face when testing modern applications.
Cypress is most often compared to Selenium; however Cypress is both fundamentally and architecturally different. Cypress is not constrained by the same restrictions as Selenium.
This enables you to write faster, easier and more reliable tests.

## Cypress ecosystem
Cypress consists of a free, open source, locally installed Test Runner and a Dashboard Service for recording your tests. It also provides 3rd party integrations to various plugins and tools.
Cypress helps you set up and start writing tests every day while you build your application locally. Both BDD(Behavioral Driven Developement) and TDD(Test Driven Development) can be accomplished.
After building up a suite of tests and integrating Cypress with CI Provider which in our case is GitHub Actions, but Cypress Dashboard Service can even then record our test runs.

## Steps to contribute to this framework:
1. Clone this repository from GitHub into your local desktop.
2. Create a branch:
	```bash
	git checkout -b <branch_name>.
	```
3. 	Make your changes and commit them:
	```
	git commit -m '<commit_message>'
	```
4. Push to the original branch: 
	```
	git push
	```
5. Create a pull request and assign to your reviewer.

## Cucumber/gherkin-syntax
The cypress-cucumber-preprocessor adds support for using feature files when testing with Cypress.

You can follow the documentation below, or if you prefer to hack on a working example, take a look at https://github.com/TheBrainFamily/cypress-cucumber-example

## How to write tests and How to organize the tests.
You choose to have only one in the root of the directory cypress/integrations or per directory.
Easier to show than to explain, so, assuming the feature file is in cypress/integration/FunctionalTestSuite/LoginPage.feature , as proposed above, the preprocessor will read all the files inside cypress/integration/FunctionalTestSuite/LoginPage.js (or any other .js file in the same path)
## Feature file
1. Example: cypress/integration/FunctionalTestSuite/LoginPage.feature

```
Feature: Login Page

  I want to open a Login Page
  
  @focus
  Scenario: Opening a Login page
    Given I open Login page
    Then I see XXXX in the title
```

The @focus tag is not necessary, but we want to you to notice it so you look it up below. It will speed up your workflow significantly!

## Step definitions
This is the RECOMMENDED way of Step definitions creation. The .feature file will use steps definitions from a directory with the same name as your .feature file. The javascript files containing the step definitions can have other names if you want to break them into different concerns.

## Reusable step definitions
We also have a way to create reusable step definitions. Put them in cypress/integration/common/
This is a good place to put global before/beforeEach/after/afterEach hooks.

## Visual Studio Code
To get vscode to resolve your steps, install the Cucumber (Gherkin) Full Support extension from the marketplace.

## Oldschool/Legacy Cucumber style
Not recommended. Please let us know if you decide to use it! The problem with the legacy structure is that everything is global. This is problematic for multiple reasons.

## Final Words
It makes it harder to create .feature files that read nicely - you have to make sure you are not stepping on toes of already existing step definitions. You should be able to write your tests without worrying about reusability, complex regexp matches, or anything like that. Just write a story. Explain what you want to see without getting into the details. Reuse in the .js files, not in something you should consider an always up-to-date, human-readable documentation.
The startup times get much worse - because we have to analyze all the different step definitions so we can match the .feature files to the test.
Hooks are problematic. If you put before() in a step definition file, you might think that it will run only for the .feature file related to that step definition. You try the feature you work on, everything seems fine and you push the code. Here comes a surprise - it will run for ALL .feature files in your whole project. Very unintuitive. And good luck debugging problems caused by that! This problem was not unique to this plugin, but to the way cucumberjs operates.

Suggestions are welcome !!.