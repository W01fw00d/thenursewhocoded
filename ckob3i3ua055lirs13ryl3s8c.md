## How to publish an HTML game in itch.io

%[https://github.com/W01fw00d/barbarians]

* Cover image art by <kbd>[@gelabert.art](https://www.instagram.com/gelabert.art/)</kbd>

* <kbd>[Play the game now!](https://w01fw00d.itch.io/barbarians)</kbd>


### Some context

This project started in 2017 as a birthday gift for a friend who studied the History Degree ⏳ and loves strategy historical games, especially the Roman era.

Being a big fan 💓 of games like Risk, Age of Empires, or Advance Wars; I decided to create something similar using <kbd>[some tiles and sprites](https://github.com/W01fw00d/barbarians/tree/master/src/images/board)</kbd> my good friend <kbd>[@gelabert.art](https://www.instagram.com/gelabert.art/)</kbd> painted.

%[https://media.giphy.com/media/QqR82WpBPFeeJmIVfR/giphy.gif]

The first version that I gifted my friend was buggy but playable 😅. Over the years I have been refactoring, <kbd>[adding tests](https://github.com/W01fw00d/barbarians/tree/master/src/scripts/game/tests)</kbd>, and <kbd>[removing jquery](https://github.blog/2018-09-06-removing-jquery-from-github-frontend/)</kbd> and other unnecessary and old libraries to have a <kbd>[true minimalist pure JS game](https://github.com/W01fw00d/barbarians/tree/master/src/scripts/game)</kbd> 💖.

<kbd>[In my first post](https://thenursewhocoded.hashnode.dev/how-i-learned-to-code)</kbd> 📃 I confessed that I have never published a game before so… this week I decided to change that. So, shall we 👐🏼?


### What you’ll need

- An account in <kbd>[itch.io](https://itch.io/register)</kbd>. It's free 💸!
- A zip file or an HTML file that contains all your game logic… in my case I created the zip using the free 💸 <kbd>[7-Zip](https://www.7-zip.org/)</kbd> with my repository as the index.html file present on it will work as an entry point on the itch.io server. Note: There’s a limit of 1000 files 🚯 inside that zip… so make sure to remove testing libraries 📚 and that kind of thing not necessary for production release ⭐.
- The process of publishing a game in HTML format is quite simple and <kbd>[it’s well explained by itch.io itself](https://itch.io/docs/creators/html5)</kbd>. Just pick “HTML Game” from the “Kind Of Game” list when in the New Game form 👍🏿.

%[https://media.giphy.com/media/hqsrF8y3F8LYBkWWsU/giphy.gif]


### And now what?

I like that itch.io lets you choose a state for the game. I decided to publish it as “In active development”. The UI is terrible and the mechanics could be improved 🤔. But, who knows, maybe in 4 years more I’ll change to “Released” 🦾.

I started this project when I was a junior developer 👶🏽 and with the pass of time, I have been refactoring it and adding a lot of improvements since I gained expertise using javascript (ES6, functional programming…): it’s like a diary 🗒 of my JS adventure until today!

I’m even using <kbd>[Cypress](https://www.cypress.io/)</kbd> 🌳 to test it and did you know that this project participated in a <kbd>[Hacktoberfest](https://hacktoberfest.digitalocean.com/)</kbd> 🍻? But that’s a story for another day 😏.

%[https://media.giphy.com/media/oelBzAtCnCShpPNMRx/giphy.gif]


### Is there a future for this project?

I have a lot, like, A LOT of ideas 💡, improvements, refactors, and bugfixes 🚒 <kbd>[registered on this project](https://github.com/W01fw00d/barbarians/issues)</kbd>. The most interesting new features would be a multiplayer mode 👫, a custom map editor 🗺, a procedural map generator ⚙, a “going back in time” mechanic 🕰, creating a gif with all the turns screenshots at the end of a map 🎞...
