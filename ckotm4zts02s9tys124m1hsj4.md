## How to parse .csv with Python

%[https://github.com/W01fw00d/bondy]

### Python in Science

<kbd>[Python](https://www.python.org/)</kbd> 🐍 is a great language for beginners 👶 <kbd>[(I myself started coding with it)](https://thenursewhocoded.hashnode.dev/how-i-learned-to-code)</kbd>. It's especially useful for creating small tasks ⚙ on your computer, automating file management 📂, calculations 🧮, document formatting 📄...

So you won't be surprised to know that it's <kbd>[the preferred language](https://www.techrepublic.com/article/top-5-programming-languages-for-data-scientists-to-learn/)</kbd> among scientists 👩🏻‍🔬. A lot of <kbd>[artificial intelligence libraries](https://www.tensorflow.org/)</kbd> are written in Python, but other science fields like Chemistry 🧪 use Python in their calculus programs, like the <kbd>[R project](https://www.r-project.org/)</kbd>.


### Solving a problem

Let me share a little example with you. One day, a chemist (who happens to be also my wife 😇) asked me how to transform a concrete <kbd>[.csv](https://en.wikipedia.org/wiki/Comma-separated_values)</kbd> 📃 columns and rows structure into a different structure automatically.

The <kbd>[UV-vis spectrophotometer](https://www.labx.com/product/varian-cary-300#:~:text=The%20Varian%20Cary%20300%20Bio,for%20routine%20analysis%20and%20research.&text=The%20Varian%20Cary%20300%20UV%2FVis%20Spectrophotometer%20with%20Cary%20Dual,the%20new%20Cary%20WinUV%20software.)</kbd> machine ⚙ my wife was using at the university laboratory was outputting a format "A", and she needed a format "B" as input for the analysis software 👨🏼‍💻<kbd>[(ReactLab JPlus Consulting)](https://jplusconsulting.com/)</kbd> that was processing the scientific data.

%[https://media.giphy.com/media/l0HlQCEq4A9H2evVC/giphy.gif]


### How to decide when to automate a task

She has been doing that task manually for a week 📅, realizing that all that time was being wasted on something that should be trivial. Time ⏳ that she could have been investing in doing actual scientific work.

In addition to that, she wasn't the only one who had to suffer this manual process: the machine was used by other colleagues 🥼 in the present, and potentially, in the future.

This kind of situation is ideal for creating a task and make somebody more productive and probably happier 🙂. To be sure about it, just sum the hours 🕗 each person is wasting on a task daily, and multiply it by all the persons 👨‍👨‍👧‍👧 in that situation (and consider persons outside the organization that could benefit from it too! 🌐). If the resulting number is bigger than the hours of effort 💦 you will need to invest, it's generally a good idea to develop that task ✅.

So I asked my wife 💁🏽‍♀️ <kbd>[an example](https://github.com/W01fw00d/bondy/tree/master/example)</kbd> for the `input.csv` and the `output.csv` and started working!

%[https://media.giphy.com/media/pM0cqxUmZqkow/giphy.gif]


### Some details


Python includes by default:

1- A <kbd>[csv module](https://docs.python.org/3/library/csv.html)</kbd> 🧩 that gave me the feature I needed to write the `output.csv`.

2- A <kbd>[glob module](https://docs.python.org/3/library/glob.html)</kbd> 🧩 that allowed me to read the `input.csv`

So, I just needed to develop <kbd>[the logic](https://github.com/W01fw00d/bondy/blob/master/bondy_writer.py)</kbd> 🦾 for rearranging and restructuring the columns and row!

Finally, I just wrote a small <kbd>[batch file](https://github.com/W01fw00d/bondy/blob/master/click_me_to_execute.bat)</kbd> that could be clicked 🖱 by the user so they didn't need to use their OS terminal.


### Closing time

I named the <kbd>[task "Bondy"](https://github.com/W01fw00d/bondy)</kbd> as a reference to the concept of <kbd>[covalent bonds](https://en.wikipedia.org/wiki/Covalent_bond#:~:text=A%20covalent%20bond%20is%20a,is%20known%20as%20covalent%20bonding.)</kbd> ⛓ in chemistry.

I tried to keep the <kbd>[README](https://github.com/W01fw00d/bondy/blob/master/README.md)</kbd> very simple so people with no programming experience could use the ask without issues 😊. The harder part of the setup was installing Python, luckily MacOS includes it by default and Windows users can just download and install it without needing more than user-level computer knowledge 😎...

%[https://media.giphy.com/media/OeyAkKTKYSvmw/giphy.gif]

This task helped to publish this <kbd>[research paper](https://pubs.rsc.org/en/Content/ArticleLanding/2021/CC/D0CC07683J#!divAbstract)</kbd> 📃, which makes me quite happy as an old hard-core Science supporter 💓

If you are a scientist 👨🏿‍🔬, I think you could benefit a lot from learning a bit of Python to create your own small tasks. If you combine that skill with some spreadsheets 📄 skills, you will be able to work faster and be more independent. Free your mind from repetitive work, learn to code today!

Did you solve any similar problems with some lines of code? Did it blow your mind 🤯? Let me know in the comments 😉.
