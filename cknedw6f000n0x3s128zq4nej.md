## Turning text into voice: Freedom for your content!

%[https://anchor.fm/gabriel-romaymachado/episodes/Turning-text-into-voice-Freedom-for-your-content-euupq2]

%[https://github.com/W01fw00d/text-to-voice]

* Post header illustration by [@gelabert.art](https://www.instagram.com/gelabert.art) ðð»ââï¸

### Some context

I used to manage and write in a collaborative narrative writing group â (mostly in Spanish): I even did a [5 min talk about it](https://www.ivoox.com/broken-telephone-applied-to-writing-talk-english-audios-mp3_rf_67513289_1.html)! At some point, we started recording in audio ð whenever we met to read together a finalized book. Then, I decided to do some editing and create a [podcast using those audios](https://www.ivoox.com/podcast-nova-linia-cadaver-exquisito_sq_f1667423_1.html).

That was cool enough ð butâ¦ what about the first books we wrote, before having a good mic to record them? Did I really want to use my eyes to be able to enjoy them again...? *After an 8-hour session of computer work* ð¥?

%[https://giphy.com/gifs/cxg-ceg-cxg403-1WbJnEhCpZTThmzFTz]


### [What I needed](https://github.com/W01fw00d/text-to-voice/issues?q=)

- A task that could read through every chapter of a story and generate an audio file with a voice narrating it ð
- Dynamically add the chapter number at the beginning ð¢
- Dynamically change the narrator voice when reading the chapter title, on dialogues (I wanted to have at least two voices for dialogues in order to indicate two different speakers ð©ð»âð¤âð©ð¼)

%[https://giphy.com/gifs/viralhog-dog-machine-petting-3q2zs3ycokGzMv7efJ]

- Dynamically add the opening and ending songs ð¼ assigned to that book in every one of its chapters
- Support both Spanish and English ð¤ð»
- Output in .mp3 so I just have to upload it to my podcast platform of choice: ivoox (free ð¸)




### How it went

- Issue ð²: The library [node-gtts](https://www.npmjs.com/package/node-gtts) is cool and useful, but it didnât allow me to change voices using markdown or anything fancy like that ð, and it didnât offer more than 2 different Spanish voices
- Solution ðð½: I developed my own [custom loop logic](https://github.com/W01fw00d/text-to-voice/blob/master/src/scripts/chapterAssembler.js#L41-L85) and called the library for each paragraph, indicating which voice to use in each one. I had to use Portuguese and Italian, which are phonetically quite similar to Spanish, in order to have more available voices ð©âð©âð§âð¦


- Issue â: When I merged the voice file with the songs files, the output file was corrupted ð§ââï¸ (probably missing `headers`)
%[https://giphy.com/gifs/bunny-plushie-plush-toy-3o7qDGfZwtetmmai0E]
- Solution ðð¿: I was using a quite naive and old approach for combining files, based on an [archived repo](https://github.com/qawemlilo/node-streams). I had the same issue with [the audioconcat library](https://github.com/h2non/audioconcat) ð£. Finally, directly using [the fluent-ffmpeg library](https://github.com/fluent-ffmpeg/node-fluent-ffmpeg) worked perfectly, and [I didnât have to expend so much effort as I imagined](https://github.com/W01fw00d/text-to-voice/blob/master/src/scripts/audioFilesCombinator.js)



### Lessons learned

- Parsing narrative text can be expensive to develop ð: every writer uses different conventions for identifying the dialogues, scene changesâ¦ you need to design a system quite flexible and "open" because youâll need to change it whenever you find an unexpected chapter format! I even ended up using [some regex](https://github.com/W01fw00d/text-to-voice/blob/master/src/scripts/textManipulator.js) ðµ...

- Itâs a good idea to invest some time investigating a library before developing your solution. And sometimes, even if a library seems to be the perfect fit for your need, itâs better to use a library with more powerful features or just write the needed code yourself ð¨ð¿âð»

%[https://giphy.com/gifs/IntoAction-fXnx6vSSrzY92rTONJ]

- Audio edition is effort-expensive for someone like me who doesnât really know about `sampleRates` and similar audio file attributes ð§. For this kind of feature, it's better to delegate to some program or library




### The fruits of hard work

You can access [the code in my github](https://github.com/W01fw00d/text-to-voice) and check the current status of the project [in the issues section](https://github.com/W01fw00d/text-to-voice/issues) ð¤!

You can even check an [example of the final output](https://www.ivoox.com/cadaver-2-capitulo-11-english-audios-mp3_rf_68280247_1.html)! Itâs an specific chapter that I wrote in English ð¤ 


### Is there a future for this project?

While I finish transforming all the old books ð, Iâll extract some features (dialogue interpretation, adding opening and closure songs...) for more general use (something like a podcast-chapter-generator).

I would like to fix the burden of having to upload manually every chapter to ivoox (they don't offer an API, so I'm thinking of using Cypress or other similar automated tools ð¤ in order to, as always, make my life a bit easier...)

%[https://giphy.com/gifs/english-language-62CDX43Hr8WlO]