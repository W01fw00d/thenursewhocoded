## How to use Cypress in a JS Game

### Why functional testing was useful for my Game

Recently I published a very <kbd>[minimalist javascript game](https://github.com/W01fw00d/barbarians)</kbd> ð® in <kbd>[itch.io](https://itch.io/)</kbd>, as I explained in a <kbd>[previous post](https://thenursewhocoded.hashnode.dev/how-to-publish-an-html-game-in-itchio)</kbd>.

I have worked on this project during intermittent periods. At some point, I needed to do a huge refactor, because I started this project 4 years ago ð <kbd>[before ES6 was approved](https://www.infoworld.com/article/2937716/its-official-ecmascript-6-is-approved.html
)</kbd> so I wasnât really using any of the new ð useful features as <kbd>[modules](https://hacks.mozilla.org/2015/08/es6-in-depth-modules/)</kbd> or <kbd>[Functional Programming syntax](https://blog.cloudboost.io/es6-function-programming-cheatsheet-update-spread-note-example-tutorial-26f265b0ddf1)</kbd>...

%[https://media.giphy.com/media/l0HlGmv4WqldO9c5y/giphy.gif]

For example, I needed to change a lot of code in order to be able to add transition animations for the AI turn ð¤. That meant changing a sequential code into a `wait and callbacks` type of code. I needed to update the unit tests, which were designed to test the old code ðµð½. While those tests were broken â, I wouldnât have a way to be sure that the game's main features still worked ðð¿ââï¸.

But with functional tests, I could cover my main features (gaining gold, combat, winning, losing...), treating the production code as a âblack boxâ â¬ and therefore having tests that are completely independent of any big refactors ðª. If you want to know more about functional tests, you can check <kbd>[my previous post](https://thenursewhocoded.hashnode.dev/using-cypress-to-test-a-web-app)</kbd> about applying them in a Web App ð.


### General Tips

1- â Divide your specs into two groups/folders: <kbd>["Core" and "Not Core"](https://github.com/W01fw00d/barbarians/tree/master/cypress/integration)</kbd>. That way you can check that the main App features are still working when using Cypress UI ð³; which is faster than launching the whole test suite:

![cypress_barbarians.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1621242699089/XB_bpK75eZ.gif)


2- ð¡ While you develop new tests, use  <kbd>[.only() and .skip()](https://docs.cypress.io/guides/core-concepts/writing-and-organizing-tests#Excluding-and-Including-Tests)</kbd>; they are quite useful and allow you to test a single test individually without having to comment out code or similar workarounds. By the way, <kbd>[Cypress documentation](https://docs.cypress.io/guides/overview/why-cypress)</kbd> is quite easy to follow and the community is great too ð.

3- ð³ Cypress allows you to easily set the state of the game to a point that you want to test, avoiding repetitive actions ð¥± such as playing through all the level 1 to make sure that you can win and get to level 2. <kbd>[In my case](https://github.com/W01fw00d/barbarians/blob/master/src/scripts/main.js)</kbd>, I achieve that using URL parameters to select a level, disable animations, sound...

4- â You can add your Jasmine.js unit tests into a Cypress spec too. Of course, you should run your unit tests more frequently and independently of the functional ones. But it's cool to <kbd>[visit your jasmine tests HTML page](https://github.com/W01fw00d/barbarians/blob/master/cypress/integration/core/jasmine.spec.js)</kbd> with Cypress before the "real" functional tests just to check that everything is green â and good to go!

![cypress_barbarians2.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1621243382696/I7T4JAOzS.gif)


### Issues I found

- ð¤ My game had some luck and randomness involved in the AI movements and the combat resolution. You cannot test a feature that you donât know exactly what will output, but luckily cypress API offers some functions that give the flexibility to test results. That's not a proper solution; it feels like a workaround: tests should be strict, so Iâm planning to <kbd>[add a flag to disable randomness](https://github.com/W01fw00d/barbarians/issues/105)</kbd>.

- â The game used window alerts for showing some messages instead of a custom modal. I ended up using my own modal always, but meanwhile, I was able to test that using this code:

```
cy.on('window:alert', stub);
click('#button').then(() => {
  expect(stub.getCall(0)).to.be.calledWith("Hello World!");
}

```

And by the way, you can do <kbd>[something similar](https://github.com/W01fw00d/barbarians/blob/master/cypress/integration/core/map_over.spec.js#L44-L54)</kbd> for `window:confirm`!

- â Do you need to check that a console.log was printed? I was able to test that using this simple utils functions:

```
const CONSOLE_LOG = "consoleLog";

export const havePrinted = (text) =>
  cy.get(`@${CONSOLE_LOG}`).should("be.calledWith", text);

export const mockedConsole = {
  onBeforeLoad(win) {
    cy.stub(win.console, "log").as(CONSOLE_LOG);
  },
};
```

Then, I used it on my tests like this:

```

import { mockedConsole, havePrinted } from "./utils/console";

// You need to mock the console before the first load
cy.visit("my.fake.url", mockedConsole);

// This will return true if there's a console.log printing 'Hello world!'
havePrinted("Hello world!);

```


### Closing time

It's funny to use tools out of the context they were designed for. I'm not sure Cypress can be applied in a canvas JS game for example. For simple HTML tags ð· games, it works perfectly as it's not so different from your usual Web App ð¥.