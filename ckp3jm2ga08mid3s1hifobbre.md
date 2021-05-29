## Using Cypress to test a Web App

%[https://github.com/W01fw00d/cooking-with-amateurs]

🖼 Cover image by <kbd>[Marta XimenisCampins](https://www.domestika.org/es/projects/692722-cocina-con-amateurs)</kbd>

🖥 <kbd>[Check a demo of the App](https://cooking-with-amateurs.herokuapp.com/#/list)</kbd>


### Some context

During the beginning of <kbd>[the pandemic](https://en.wikipedia.org/wiki/COVID-19_pandemic)</kbd> 🦠, a friend who works as a cook 👨🏼‍🍳 started to teach us some new recipes during weekly video calls 📲. I started this project to manage those cooking recipes and the photos of the resulting dishes 🍽.

I named it "Cooking with Amateurs" ("Cocinando con Amateurs" in Spanish). At the time I was already developing a Components Library 📚 named <kbd>[Chemistry-UI](https://github.com/W01fw00d/chemistry-ui)</kbd> (I even wrote a <kbd>[previous post](https://thenursewhocoded.hashnode.dev/your-own-components-library-with-storybook)</kbd>‌ about it!).

I wanted this project to be scalable 💗, and a good showcase of best practices as I'm bored 🥱 of doing code tests for potential future employers and I wanted to have <kbd>[a decent portfolio](https://github.com/W01fw00d)</kbd> 🖼.

So, I needed to develop a good test suite ✅ for this project (I even added <kbd>[a coverage script](https://github.com/W01fw00d/cooking-with-amateurs/blob/master/package.json#L10)</kbd>). For unit tests, it was clear to me that I wanted to use <kbd>[Jest](https://jestjs.io/)</kbd> and that I was going to focus on the <kbd>["model" modules](https://github.com/W01fw00d/cooking-with-amateurs/blob/master/src/pages/recipeDetail/model.ts)</kbd>, where my main business logic ⚙ was gathered. But for <kbd>[Functional Tests](https://en.wikipedia.org/wiki/Functional_testing)</kbd>, I needed something else 🤔.

%[https://media.giphy.com/media/l4MJnT4YXg3xt81tKn/giphy.gif]


### About Functional Tests Tools

There are a lot of different tools 🛠. In addition to <kbd>[Cypress](https://www.cypress.io/)</kbd>, I have worked in the past with <kbd>[Selenium](https://www.selenium.dev/)</kbd> too. 

When choosing the right testing library for you ⚖, it's important to look for one that somehow "enforces" a good testing paradigm. I have been using Cypress 🌳 in many projects, professional and <kbd>[side projects](https://github.com/W01fw00d?tab=repositories&q=cypress&type=&language=&sort=)</kbd>. It always adapts wonderfully: its API is clear and there are some interesting community-developed plugins´💖.

Can't say I find Selenium so easy to use: in many projects I worked on in the past, app developers had to develop libraries 📚 on top of selenium in order to get a consistent platform that every user in the team could use without much effort 😅.

%[https://media.giphy.com/media/icJA0VF7ntoEL18Jez/giphy.gif]


### Who should develop these tests?

In big companies, there's usually an independent role 👩🏿‍💼 (QA Engineer, or Testing Engineer) in charge of developing this type of testing. I believe this is not the more optimal management: there're many benefits that you gain when App Developers 👩🏼‍💻 create functional tests too:

* Functional tests, as unit tests in <kbd>[TDD](https://en.wikipedia.org/wiki/Test-driven_development)</kbd>, forces you to uncouple 🪓 your code to test it properly. For example, defining an API allows you to mock that API and show any data you want on the UI 🖥. Another case: calling an external module 📞 from inside the module you want to test. You'll find that you need to inject that dependency in a way you can mock it 🤥. This will also result in better quality app code 🌟.

* If you write descriptively named tests 📄, you can mimic the actual requirements for that development! At some point, I worked on a project that used Selenium + <kbd>[Cucumber](https://cucumber.io/)</kbd> 🥒 + an abstraction layer that allowed anybody without technical knowledge to write tests as requirements ✍🏼 (for example: "User enters the page and completes the login").

* You can <kbd>[randomize the characters](https://github.com/W01fw00d/cooking-with-amateurs/blob/master/cypress/integration/list.spec.ts#L84-L93)</kbd> and the lengths of the strings that your UI displays 💻. This is useful to check the responsiveness of that UI and allows frontend developers to be more aware of possible visual bugs 🐛.

%[https://media.giphy.com/media/Zp3dDTwtkKKU8/giphy.gif]


### Some last comments

Functional Tests have a lot of benefits, but you have to develop them in good measure ⚖. They are usually expensive to run 💰, so you don't really need to cover all your features. It's better to just cover the core features (for example, the login or the buying process) ✅.

If you want to test complex logic ⚙ or achieve a code coverage close to the 100%, you need to invest in unit tests, not functional ones.

So, what do you think? Have you tried Cypress already, do you love it 🤗?


