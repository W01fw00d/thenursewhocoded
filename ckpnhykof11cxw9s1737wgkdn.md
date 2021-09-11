## How to use HTML5 draggable in your game

### Some context

I recently published <kbd>[Barbarians!](https://github.com/W01fw00d/barbarians)</kbd> in <kbd>[itch.io](https://w01fw00d.itch.io/barbarians)</kbd>, as I explained on <kbd>[a previous post](https://thenursewhocoded.hashnode.dev/how-to-publish-an-html-game-in-itchio)</kbd> ✍. It was clear to me that the Game UI 🖥 needed a lot of work (I created that interface 4 years ago and I haven’t really updated it since then).

“Improving UI” is quite a broad concept that includes a lot of small tasks that I have been recording for quite a long time 📋, so I decided to organize this “sub-project” using a <kbd>[GitHub project board](https://github.com/W01fw00d/barbarians/projects/3)</kbd>. That way I could stay focused on my main goal and don’t get distracted fixing game logic bugs 🐛 for example.

I was reading an article about draggable and I realized that it wasn’t really difficult to implement nowadays <kbd>[with vanilla js](https://www.w3schools.com/tags/tryit.asp?filename=tryhtml5_global_draggable)</kbd> 👍🏼. So I created <kbd>[a specific issue](https://github.com/W01fw00d/barbarians/issues/102)</kbd> for applying this to adding a new feature that would allow users to move their soldiers by dragging them 👆🏾, in addition to the previous moving option of clicking the soldiers and after that clicking the destination 🥱.

![barbarians_drag1.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1621843747024/WFYO2Rz99.gif)


### What do you need to use draggable

1 - 👆 The <kbd>[HTML draggable attribute](https://github.com/W01fw00d/barbarians/pull/103/files?file-filters%5B%5D=.js#diff-084b74600de3ecc1e3249a315ce89fc798ef2b12a95088004432c06265b2fdb9R9)</kbd>

1 - 📨 The <kbd>[`dragstart` event](https://github.com/W01fw00d/barbarians/pull/103/files?file-filters%5B%5D=.js#diff-0294806d5f7755f2157de75bad0538836429a1aed7badb04552ff38513bb80aeR251)</kbd>. Save the id of the node that you are "dragging" in the <kbd>[event data](https://github.com/W01fw00d/barbarians/pull/103/files?file-filters%5B%5D=.js#diff-0294806d5f7755f2157de75bad0538836429a1aed7badb04552ff38513bb80aeR248)</kbd> for future use.

2- 📩´The <kbd>[`drop` and `dragover` events](https://github.com/W01fw00d/barbarians/pull/103/files?file-filters%5B%5D=.js#diff-0294806d5f7755f2157de75bad0538836429a1aed7badb04552ff38513bb80aeR220-R229)</kbd>. On the drop event handler, get the node using the id that you previously saved on the event and then <kbd>[append that node](https://github.com/W01fw00d/barbarians/pull/103/files?file-filters%5B%5D=.js#diff-0294806d5f7755f2157de75bad0538836429a1aed7badb04552ff38513bb80aeR186)</kbd> as a child from the event target node (the final node where you dragged the original node), On the `dragover` event handler, we will just <kbd>[disable the default behavior](https://github.com/W01fw00d/barbarians/pull/103/files?file-filters%5B%5D=.js#diff-0294806d5f7755f2157de75bad0538836429a1aed7badb04552ff38513bb80aeR225)</kbd>, as only want to "move" the node when the user releases the click, not only when entering a dragging area.

3 - ❕ Be aware that <kbd>[html attributes and js listener API are different](https://stackoverflow.com/a/67453844/5235624)</kbd>. Do not get confused with the different named events!

%[https://media.giphy.com/media/igPKsfNkb9kXsRWSfF/giphy.gif]


### How to test it using Cypress

As I explained in a <kbd>[previous post](https://thenursewhocoded.hashnode.dev/)</kbd>, I use <kbd>[Cypress](https://www.cypress.io/)</kbd> 🌳 for functionally testing this game. Having to play manually through the same levels over and over is horrible; better to have all the game main features automatically testable ⚙.

After trying simulating mouse 🖱 events by myself using X and Y coordinates with no luck 😢, I found <kbd>[a small library](https://github.com/4teamwork/cypress-drag-drop)</kbd> that implements an easy drag feature in cypress. It worked perfectly for my needs because I only needed to use selectors instead of mouse positions 📊. Big thanks and shout-out to the creators, <kbd>[4teamwork](https://github.com/4teamwork)</kbd>!


### Closing words

You can check the full <kbd>[Pull Request](https://github.com/W01fw00d/barbarians/pull/103
)</kbd> if you want more details 😉.

And that's all for today. Personally, I like how easy is to implement a draggable feature without using any framework or libraries; but what do you think 🤗?
