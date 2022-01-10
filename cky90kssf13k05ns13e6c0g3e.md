## Cucumber + Cypress

### 🖼 Some context

I have known Cucumber for a long time, and I used to work with it combined with Selenium. I really love Cucumber's philosophy of having tests that can be read and understood by any role related to Web Development, even non-tech ones (UX, Product Managers, QA specialists, etc). That's really powerful: when tests become a "common ground" for all the team members, they can be used as the actual specifications for the product; so they are a great way of communicating between different team members.

When I worked with Cucumber in a previous company, we used to follow this procedure: a QA specialist (who didn't have tech knowledge) wrote the Cucumber feature using the steps/phrases that we have already implemented. If a new step was needed, a developer would implement it and make sure that the test works, also implementing the real feature needed to fulfill the test requirements.

%[https://media.giphy.com/media/QWwEdgDbYjFbfOMJ3z/giphy.gif]

Working with the Cucumber tests as a guide makes Web Development so much easy for all the parts involved, and the chances of human error go down. That's why I consider it a perfect tool to enforce a good development praxis, and I wanted to include it on my personal portfolio project <kbd>[Cooking With Amateurs](https://github.com/W01fw00d/cooking-with-amateurs)</kbd>. Luckily for me, there's a nice <kbd>[npm package](https://www.npmjs.com/package/cypress-cucumber-preprocessor)</kbd> that works as a preprocessor between Cucumber and Cypress, my Functional Testing Library of choice! 

They even support <kbd>[typescript](https://www.npmjs.com/package/cypress-cucumber-preprocessor#typeScript-support)</kbd>, wow!


### 🥒 About Cucumber

<kbd>[Here's](https://github.com/TheBrainFamily/cypress-cucumber-example)</kbd> a nice example of how a Cucumber test looks.

And <kbd>[here](https://github.com/cucumber/cucumber-expressions#readme)</kbd>you will find a list of all Cucumber expressions.

But let me try to explain how Cucumber works with this example taken from <kbd>[my own tests](https://github.com/W01fw00d/cooking-with-amateurs/blob/master/cypress/integration/list/main.feature)</kbd>:


```
Feature: On List Page

@core
  Scenario: Write on search text input
    Given System will load random Recipes
    And I visit "list" Page
    When I write "text" on the "search" Input
    Then I see "text" on the "search" Input
``` 

Each Cucumber file is a Feature, and as its name implies, it can contain many scenarios but all related to the same feature or functionality. You can add @tags to the scenarios to help you group them: in my case, I mark the scenarios I want to run more often with a @core tag.

In each scenario, which are independent functional tests, you write a phrase for each step of the test. Depending on the type of step, you can use a different keyword:

- `Given` is used for steps that establish a specific state for your App, needed for the test to work properly. In my Scenario, I mock the server data of my app in my `Given` step, to be sure of the kind of recipes that will appear on the List Page when the test runs. I use a random words generator in this case because I don't need to test specific data.

- `And` is just a syntax-sugar detail, it basically means that the step will be of the same type as the previous one. In my `And` step, I navigate to the List page so the test will start already there.

- `When` defines a step that represents an action from the user, in this case, the user writing on the search input.

- `Then` steps represent the consequences of the `Given` defined state for the app or the actions performed by the user in a `When`. They are always "Assertions".


%[https://media.giphy.com/media/ZFHRyz6bsnDCVOR3nf/giphy.gif]

### 🌲 Cucumber + Cypress

When the developer actually writes the tests, they will mostly focus on developing "steps" as the ones explained above. Cucumber is quite powerful and flexible, so you don't need to define specifically the step "And I visit "list" Page", but instead <kbd>[you can do](https://github.com/W01fw00d/cooking-with-amateurs/blob/master/cypress/integration/common/navigation.ts)</kbd>:


```
Given('I visit {string} Page', page => {
  cy.visit(page.toLowerCase());
});
``` 

That way, you can develop dynamic steps that can be reused in different features! You can even include optional words using regex like this:

```
/^Recipes will( not)? show their name$/
``` 

%[https://media.giphy.com/media/aLyitXm0xd52iYuLvA/giphy.gif]


### 🌟 Extra tips


* Checking that no error is logged on the js console. You can find how to do this <kbd>[on the docs](https://docs.cypress.io/faq/questions/using-cypress-faq#How-do-I-spy-on-console-log)</kbd>


* Simulating a Mobile Device Screen

<kbd>[It's quite easy](https://github.com/W01fw00d/cooking-with-amateurs/pull/100/commits/d06596eddb4c5fb1021664daba9db43517ed2cbb)</kbd> to do with Cypress, you can just set `viewportWidth` and `viewportHeight` in `cypress.json`.

