## Using npm link with React packages

### 😖 It all started with a cruel realization...

I think one of the worst experiences a Developer can have is to find out that some piece of code that used to work just fine for them for months or even years suddenly "stops working". This strange bug usually has obscure and random causes: maybe you updated some dependency that the code uses, maybe you updated the system that actually runs the code; maybe the Running Environment configuration changed...

In my case, it was a bash script that executed `npm link` for me on my <kbd>[Chemistry-UI](https://github.com/W01fw00d/chemistry-ui)</kbd> component library and my main app, <kbd>[Cooking With Amateurs](https://github.com/W01fw00d/cooking-with-amateurs)</kbd>.

I suspect the script stopped working after updating node and npm on my local system and deciding to set the last versions in <kbd>[package.json -> engines](https://github.com/W01fw00d/cooking-with-amateurs/blob/52514b47de52a72c1478154083f3767b271389ce/package.json#L30)</kbd>. Maybe the inner workings of 'npm link' changed with the last versions? I don't know, it was difficult to track down because I was many versions behind before updating.

%[https://media.giphy.com/media/7E8UUn3jg36aDEWdBO/giphy.gif]


### 📖 About `npm link` and `React`

Usually, using `npm link` is quite straightforward: you create a <kbd>[symbolic link](https://en.wikipedia.org/wiki/Symbolic_link)</kbd> (symlink from now on) to your local library so you don't have to get that library from `npm` or your `node_modules` folder. That helps to quickly do changes in your local library and test it in your app.

But it gets a bit more complicated when both your library and app are using `react`, `react-dom` or `react-router`. Long story short: `React` freaks out when there are 2 different versions of `React` (or just two 'different' `Reacts` that come from different places, for example, one from your local library and another from your app). To solve this, you need to use some additional `npm link` to make sure only one `React` is being used in your local dependency configuration.


### 🕑 1st approach: just go back in time!

I first thought about downgrading to a previous npm or node version to check if my script still worked. That could work if you are in a hurry, but I'm actually "ok" investing time on these side projects and I was happy learning more about `npm link` and the more correct and updated way of using it in `npm 8.1.1`.

%[https://media.giphy.com/media/gguFCTia9eznw48z2D/giphy.gif]


### 🔍 2nd approach: look for a quick solution on the Internet

Tools like `npm` are supposed to release the Developer from a lot of avoidable burdens when developing, so the Developer can focus on the actual product code they are developing.

So, you don't really want to expend too much time configuring and learning about a tool. But at the same time, we all know cases in which issues arise from using a tool "wrong" because the developer didn't really learn how to use it properly.

I looked for a solution for a while, but nothing worked for my particular case. I even found contradictory approaches, which didn't help.


### 👪 3rd approach: find the people that might know

My particular issue was related to both `npm link` and the way React dependencies work when used as a symlink. So I decided to trust those sources.

When looking into <kbd>[React documentation](https://reactjs.org/warnings/invalid-hook-call-warning.html#duplicate-react)</kbd>, I found out that the cause of this issue is actually having a duplicate React. As explained there:

> 
This problem can also come up when you use npm link or an equivalent. In that case, your bundler might “see” two Reacts — one in application folder and one in your library folder. Assuming `myapp` and `mylib` are sibling folders, one possible fix is to run `npm link ../myapp/node_modules/react` from `mylib`. This should make the library use the application’s React copy.

I already knew the cause of the issue, way back years ago when I wrote my bash script; but for some reason, my script was actually doing the opposite: it was running `npm link ../mylib/node_modules/react` from `myapp`. I'm not sure why did it work for me on previous versions of npm, but investigating it seemed to expensive in time, so I decided to just move forward.

This second approach that doesn't work in my particular case is actually recommended in this <kbd>[Stack Overflow answer](https://stackoverflow.com/questions/57871715/duplicate-reactjs-import-issue-when-using-npm-link-to-test-component-before-publ/64650373#64650373)</kbd> as well and other sources. I guess it might work depending on your project.

%[https://media.giphy.com/media/Ll2fajzk9DgaY/giphy.gif]


### 🌟 Definitive approach: use what you learned and fix it properly

I realized that my app was a node app so it would be cool to have a node task that did all the `npm link` stuff instead of a bash script. Easier to maintain as the language would be the same.

I was able to write a quite clear node.js script that might be easier to understand, modify and fix in the future if another catastrophe like this one happens again (turns out: that might happen and might be more and more possible as years go by if this project gets stuck again in an old node / npm version).

I was able to use `npm link` more effectively and reduce the number of steps, thanks to all I learned on this "adventure".

I even used terminal colors as it's well explained in this <kbd>[Stack Overflow answer](https://stackoverflow.com/questions/9781218/how-to-change-node-jss-console-font-color)</kbd>. This helps give clearer feedback to the script user about what each step is actually doing.

%[https://media.giphy.com/media/l0MYxqKEmJoL150TC/giphy.gif]

And I added some `npm ls react` to give the user some feedback in the terminal about what React dependencies are actually being used. Transparency is key in a script tool that is going to be used by developers.

By the way, another useful command is `npm ls -g --depth=0 --link=true`, which will return all your symbolic links in your local machine, useful for debugging.

Here is <kbd>[my full commit](https://github.com/W01fw00d/cooking-with-amateurs/pull/100/commits/6b9356b29c56a1a39db873f7d8388f914d95bf7e#diff-9772691f1743d336e32071447e668e3e45d15eb2a47787d379e5cccc6ae093d9R1)</kbd> solving this issue.

Also, check out <kbd>[this nice article](https://benjaminwfox.com/blog/tech/why-isnt-npm-link-working)</kbd> I found explaining how npm link works if you want to know more!