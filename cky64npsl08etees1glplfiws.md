## More accessibility learnings

### 🖼 Some context

I have been using <kbd>[This Frontend Checklist](https://frontendchecklist.io/)</kbd> to check my personal project webpage <kbd>[Cooking With Amateurs](https://cooking-with-amateurs.herokuapp.com/#/list)</kbd>. I find out that this checklist gives a lot of useful recommendations about accessibility, and I wanted to share the ones that helped me the most.


### 📄 More about 'alt-texts' in imgs

I have learn more about this thanks to <kbd>[this great article](https://axesslab.com/alt-texts)</kbd>.

For example, the article recommends you to add . in your `img`s `alt`s to allow for a pleasant pause when the screen reader reads the text out loud.


### 🔎 Screen magnifiers

As <kbd>[this article](https://dev.to/_bigblind/how-to-make-your-website-accessible-to-people-who-use-a-screen-magnifier)</kbd> points out; when enhancing accessibility in a webpage we usually only think about screen readers, but we ignore that most users with visual impairments actually use screen magnifiers to navigate.

This article offers quite useful tips. I couldn't apply any to my current project, but they are applicable to many web pages out there.

%[https://media.giphy.com/media/l378rhA6c1QhJDgbu/giphy.gif]


### 🌟 Optimizing images

I used <kbd>[this free tool](https://imageoptim.com/online)</kbd> to reduce my images byte size. Time to lose some weight!



### 🦥 Lazy Loading images in a list

There are many React libraries that offer components with that in-build feature, but I wanted to use HTML5 atributes to implement it myself.

<kbd>[Here](https://carlosazaustre.es/lazy-loading-image)</kbd> you will find a quite simple article about how to do it.

I was able to implement it using `loading="lazy"` and setting the `width` and `height` of the image in the ´img´ attributes. The browser needs to know these values while loading the page for the lazy load to work.

%[https://media.giphy.com/media/a5MFvAwc6GPf2/giphy.gif]

I'm styling the size of my images dynamically, luckily doing that on CSS doesn't break the lazy loading.

Then I managed to set a "test" story on my storybook using the same img url for all my recipes. Normally, the server only downloads the same image once, but you can 'trick' it using different url params.

The results are wonderful, you can see how the images are being requested in the Chrome Inspector/Network tab while scrolling down the page:

![lazy_loading.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1641663713732/APfNhem5I.gif)


Be aware that not all Modern Browsers <kbd>[are compatible](https://carlosazaustre.es/lazy-loading-image)</kbd> with this solution right now.

![caniuse_lazy-loading-html.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1634109054494/mCc8NJ_Rp.png)

I even added a <kbd>[Cypress test](https://github.com/W01fw00d/cooking-with-amateurs/pull/97/commits/16ecaa2b69debaa0de65bcdee6e111d5ad7cf836)</kbd> to check that it's really lazy loading! 

### 👩‍💻 The code

Chemistry-UI PR: https://github.com/W01fw00d/chemistry-ui/pull/49

Cooking With Amateurs PR: https://github.com/W01fw00d/cooking-with-amateurs/pull/83