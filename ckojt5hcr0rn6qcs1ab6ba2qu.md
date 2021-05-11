## Your own components library with Storybook

🖼 Cover image by <kbd>[Marta XimenisCampins](https://www.domestika.org/es/projects/686589-chemistry-ui)</kbd>

⌨️ <kbd>[Check the code in GitHub](https://github.com/W01fw00d/chemistry-ui)</kbd>

🖥 <kbd>[Check a demo of the catalogue](https://chemistry-ui.netlify.app/)</kbd>


### Some context

Some years ago I was working on a new cool project with React and Node.js. The architect 👨🏽‍💻who was leading the project had the great idea to create a React Components Library 📚 that could be reused in different projects. Our client wanted to do a series of new front end implementations of some web apps 💻, so that solution would probably save a lot of time and help maintain coherence in all its apps design 🖍.

I decided that I wanted to do a side project with a similar approach, as I truly believe that this paradigm is very useful in modern web development and it has a lot of potential to lift a lot of burdens from Designers 📐, Front-End Developers 🖱, Product Managers 📈 and Users 🙋🏻‍♀️.

My library would be shared <kbd>[by web apps with different needs and styles](https://github.com/W01fw00d/cooking-with-amateurs)</kbd> and would let me share common components 🧩 as per example submit buttons. I decided to name it Chemistry-UI because it’s based on <kbd>[Material-UI Library by Google](https://material-ui.com)</kbd>, it follows the Atomic Design principles (more about that some lines below) and because my wife is a chemist 🧪 and designed a beautiful logo for this project 🥰.

%[https://media.giphy.com/media/128MHrlrHNwwU0/giphy.gif]


### To achieve my objective I chose Storybook

<kbd>[Storybook is a tool](https://storybook.js.org/)</kbd> that “forces” you to develop components that are correctly rendered in a “blank” <kbd>[UI](https://en.m.wikipedia.org/wiki/User_interface)</kbd> context 📂 and that can be reused in different contexts of your apps or even in different apps 🔗! It also allows you to define “visual test cases”, called “stories” 📝, for your components, defining clearly the different states 🗂 a component can have (for example, a list with items, the same list with no items...).

This way of working made me develop complete demos for my components from the beginning while developing the Front-End, so I had to create a <kbd>[JSON with a fake example of expected data](https://github.com/W01fw00d/chemistry-ui/blob/master/.storybook/fake_data/recipes.json)</kbd> 📑 from the Back-End. That freed me from being blocked by dependencies with that part of the App. In other words, with Storybook, Front-End developers can just develop the visual UI without running the Back-End server 💽 at all until they need to test the whole app at the end of the feature development: <kbd>[Agile](https://en.m.wikipedia.org/wiki/Agile_software_development)</kbd>! 🤘🏿.

And, of course, the best effect Storybook has on your team is that it improves communication between different roles greatly 🤝. Designers 📐 can check the Storybook demo to look for already existing components that can be reused in a new template, Developers ⌨️ don't need to build the code or access production in order to see how the UI looks, Product Manager 📈 and <kbd>[QA](https://www.careerexplorer.com/careers/software-quality-assurance-engineer/)</kbd> 🕵🏼‍♀️ can see a component before it’s included in an already working template… and, of course, all of this translates in more quality 🌟 for your web app and your users 👩‍👩‍👦‍👦.

%[https://media.giphy.com/media/l3c5VMRRKfcat0WBi/giphy.gif]


### Some tips about Storybook

- You’ll probably have a lot of different components in your library 📔, so it’s quite important to decide a good hierarchy from the beginning. An interesting paradigm is the one described in <kbd>[Atomic Design](https://bradfrost.com/blog/post/atomic-web-design/)</kbd>. <kbd>[Mine is based on that](https://github.com/W01fw00d/chemistry-ui/tree/master/src/components)</kbd> but I made some changes to make my life easier 😉: for example, if a component is only used once in a very concrete context like for example inside another component, I prefer to define it as a <kbd>[child of the container component tree node](https://github.com/W01fw00d/chemistry-ui/tree/master/src/components/organisms/list/item)</kbd>. And, of course, the “Pages” 📄 components are not defined in Chemistry-UI, but in the apps that use my library, as a “Page” is a <kbd>[“hydrated template”](https://stackoverflow.com/questions/6991135/what-does-it-mean-to-hydrate-an-object#:~:text=Hydration%20refers%20to%20the%20process,is%20done%20for%20performance%20reasons.)</kbd>, or in other words, a template completed with the required backend data 💽.

- It will make it easier to maintain the library if you have the same tree hierarchy in your project “src” folder 🗂 and in your Storybook stories.


![storybook_tree_combined.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619516631151/Zw8QSDXPW.png)


- If you have <kbd>[some component with RouterLink](https://github.com/W01fw00d/chemistry-ui/blob/master/src/components/atoms/links/internal.jsx)</kbd> from <kbd>[“react-router-dom”](https://www.npmjs.com/package/react-router-dom)</kbd>; you’ll need to “trick” 🪄 React into thinking that you have a Router surrounding that component when you display it in Storybook to avoid issues. <kbd>[I use storybook-react-router](https://github.com/W01fw00d/chemistry-ui/blob/master/src/components/atoms/links/internal.stories.jsx)</kbd> in my stories for that 👍🏾.

- You can customize a lot of things, <kbd>[like for example the order of your components list](https://github.com/W01fw00d/chemistry-ui/blob/master/.storybook/preview.js#L4)</kbd> or you can choose to only display specific stories ✅.

- Storybook has a lot of useful addons that you can install. For example, <kbd>[“actions” lets you easily mock a button handler](https://github.com/W01fw00d/chemistry-ui/blob/master/src/components/atoms/buttons/icon.stories.jsx#L16)</kbd> and log a message 📬 in a built-in console every time the button is pressed.


![storybook_actions.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1619516671348/W9bPy8Ki6.gif)


### Some closing words

If you want to read some more technical argumentation 📋 about this project, you can check <kbd>[the project GitHub README](https://github.com/W01fw00d/chemistry-ui/blob/master/README.md)</kbd>!

Let me know in the comments if you want to learn more about Storybook, Material-UI or Components Libraries!
