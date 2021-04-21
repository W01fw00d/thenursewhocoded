## How to transform your blog into a podcast for free

* [Audio version of this post](https://anchor.fm/gabriel-romaymachado/episodes/How-to-transform-your-blog-into-a-podcast-for-free-evavgb)

### Some Context

I recently developed [a solution to turn old books into a podcast](https://thenursewhocoded.hashnode.dev/turning-text-into-voice-freedom-for-your-content) 📚. I had the idea of adapting this for transforming my text blog into an audioblog 🦻. Because I don’t have a decent microphone in order to use my own voice 🙊. And because we live in the future 🌟.

Anyway, it seems that Hashnode, the blogging platform I’m currently using, [is already offering a similar feature](https://townhall.hashnode.com/introducing-audio-blogs-on-hashnode-now-listen-to-articles-automatically). I listened to some examples and it sounds great 👍🏽, I wanted to try it on my own blog!

%[https://media.giphy.com/media/3oEduOnl5IHM5NRodO/giphy.gif]

But it’s still experimental and you can only use it if you’re an Ambassador 🤷🏼‍♀️. In addition to that, I wanted to be able to fully customize the audio output and play with it a bit, so the way to go was clear: Hacking Time 👩🏻‍💻!

### [What I needed](https://github.com/W01fw00d/hashnode-to-anchorfm/projects/1)

- A way of getting all my articles from Hasnode into my task 📃
- An adaptation of my [text-to-voice task](https://github.com/W01fw00d/text-to-voice) ⚙
- A way of getting the voice file into [anchor.fm](https://anchor.fm/), my podcast platform of choice 🎧

%[https://media.giphy.com/media/eK1sbbshY1fMYGLhH5/giphy.gif]

### How it went

- I believe [Hasnode already offers an API](https://engineering.hashnode.com/introducing-hashnode-graphql-api-public-beta-cjydzvp59001q2gs1b5zxaeaf?guid=ff63291a-7d1c-4ea7-a1f0-d4b731ef9bd1&deviceId=42236bef-9b56-47cd-911f-2e25d457d263) that lets you get your posts quite conveniently, but I was more interested in its backup feature. You see, if you create a [github repository](https://github.com/W01fw00d/thenursewhocoded) and give permissions to Hashnode, it will download your posts in .md format after every new creation or edition. It's quite easy to configure ☺! You only need to go to your blog dashboard and select “backup”.

- I decided to create my new tasks in an [independent repository](https://github.com/W01fw00d/hashnode-to-anchorfm) for security reasons ㊙

- I found [a github repository](https://github.com/Schrodinger-Hat/youtube-to-anchorfm), made by an Italian [organization named Schrodinger-Hat](https://www.schrodinger-hat.it/) 🐱‍💻, for converting a youtube video into an audio file and uploading it to anchor.fm. The upload task used [puppeteer](https://developers.google.com/web/tools/puppeteer) for that and I thought it was quite cool and simple, so I just forked it 😏. They are great, check them out!

%[https://media.giphy.com/media/3oKIPvAgCSqbwEgIU0/giphy.gif]


### Lessons learned or pending to learn

This project wouldn't be possible without three wonderful open-source projects: [the node-gtts library](https://www.npmjs.com/package/node-gtts), [the fluent-ffmpeg library](https://github.com/fluent-ffmpeg/node-fluent-ffmpeg) and the [youtube-to-anchorfm repository](https://github.com/Schrodinger-Hat/youtube-to-anchorfm). I have known for years how wonderful our software development global community is, so I’m impressed, but not surprised 🥰.

### The fruits of hard work

As I said at the beginning, you can already check [the audio version of this post in anchor.fm](https://anchor.fm/gabriel-romaymachado). And one great feature of anchor.fm is that it distributes it to other platforms too: Spotify (which makes sense, as the same company owns both), Google Podcasts, Pocket Casts… so convenient 👏🏻.

And of course, [this repository is available on github](https://github.com/W01fw00d/hashnode-to-anchorfm).

%[https://media.giphy.com/media/cnhpl4IeYgU7MCBdV2/giphy.gif]

### Is there a future for this project?

[I’m still developing some features](https://github.com/W01fw00d/hashnode-to-anchorfm/projects/1) related to the voice file generation: using sounds as substitutes for emojis 😶, adding all the links inside the blog post text into the audio post description 📋...

[The original repository I forked](https://github.com/Schrodinger-Hat/youtube-to-anchorfm) contains code for creating a Github action to execute the download and upload task. When I finish adding the rest of the features I mentioned, it would be nice to have it all automated and just need to access github to publish a new audio post ⚙.

And the best thing is that this project can be easily adapted to work with different blogging and podcast platforms 😏!

So yeah, its future looks just bright ✨ (at least till the incredible Hasnode developers rollout the audiblog feature to all users… or till I become Ambassador and get one of those cool t-shirts 👕).
