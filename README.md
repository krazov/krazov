# Welcome to my GitHub profile!

I decided to create a short guide through my repositories to bring some order to those otherwise unrelated projects. There is one take-home assignment, a couple of todo lists that I made to fiddle with various frameworks, three Games of Life, and a bunch of one-time projects.


<details>
<summary>Click here to read about the projects</summary>

## Todo lists

There is a special place for todo lists among my projects. Initially, I was going for Game of Life, but as my colleague Miguel once said, “Todo list has everything to test a framework: it has a list with sorting and filtering, it has a form to add and edit, and it has a remove functionality.” Ever since, and it was in 2018, I go for a todo when I want to see a new toy in action.

Projects in this section are ordered from the oldest to the newest to show the progress.

### Todo with Vue

* **Link:** [github.com/krazov/todo-vue](https://github.com/krazov/todo-vue)
* **Technologies explored:** Vue (along with Vuex), Pug, Stylus
* **Context:** This pretty straightforward implementation was research before an actual project. Plain and simple, it helped us decide to go with Vue, which turned out to be a very good decision. Vue was fast to work with and offered a lot of functionalities out of the box.
* **Takeaways:** What’s worth pointing out is that I decided to go with a container layer between the store and components. This way the component (understood as a more complex section of the app) would work with data passed as a prop and would be unaware of what happens with the data above. I still like this approach, however, back in 2018 I copied the React approach and was passing handlers top-down. These days, I would use events bubbling, and let decide the container (or anyone on the way for that matter) what to do with this

### Todo with Svelte

* **Link:** [github.com/krazov/todo-svelte](https://github.com/krazov/todo-svelte)
* **Technology explored:** Svelte
* **Context:** A colleague sent me a link to the project and after going through their official tutorial, I decided to give it a shot.
* **Takeaways:** While I was thinking that working with Vue was fast because building the previous app took 3 days, Svelte turned out to be even faster, and I was able to wrap up in around 3 hours. I liked their approach to the store: it’s not a centralised unit but each “module” operates on its own. I also fell in love with how little code needs to be written and that the resulting bundle is stripped of the framework itself. Any commercial project in it still remains to be done.

### Todos with Hooks

* **Link:** [github.com/krazov/todos-with-hooks](https://github.com/krazov/todos-with-hooks)
* **Technology explored:** React (but Hooks, specifically)
* **Context:** I felt out of touch with the latest React (I was working with the Hooks spiritual predecessor, Recompose; _created by the same person_), so I decided to give it a shot. A dev case of FOMO.
* **Takeaways:** This would be a relatively bland project to share, but I wanted to recreate with a Hook a concept of the store like I saw in [Reagent](https://reagent-project.github.io/) (a bridge between React and ClojureScript) and later in Svelte (the previous project). This culminated in this file: [useGlobalAtom.js](https://github.com/krazov/todos-with-hooks/blob/master/src/hooks/useGlobalAtom.js) – a Hook that can be used to create an atom (naming taken from Reagent) that will share a single data container between all the components that use it.

### Todo List Water Closet Star Wars

* **Link:** [github.com/krazov/todo-wc-sw](https://github.com/krazov/todo-wc-sw)
* **Technologies explored:** WebComponents, Composable Stylesheets, ServiceWorker, IndexedDB
* **Context:** I started working with a project that heavily relied on WebComponents but was also mixed with Vue (class-based and TypeScripted), which was confusing as to what came from where. To remove complexity, I decided to make a project in pure vanilla JS to see just WebComponents in action. Other technologies were thrown in as I went. _Once you start, it’s hard to stop._
* **Takeaways:** WebComponent turned out to be a quite different beast from what I knew at the time, but also very good in scoping chunks of the app. And, thanks to Composable Stylesheets, it did not lead to bloating of the code (something you will get with `<style>` tags). Then, having momentum, I threw in ServiceWorker with IndexedDB to leave the main thread for UI only. With the last sparks of my enthusiasm, I managed to implement routing system. The most beautiful thing is that all that was done not only with pure vanilla but also without any bundler. All running in the browser with native modules. The technology is ready. _More notes in the project’s README file._

## Game of Life

It was 2016 when I stumbled upon Conway’s Game of Life (quite possibly, it was an article about the `reduce` or `map` function; but we know that `map` is a special case of `reduce`, anyway). In a heartbeat, I decided that it is my imperative to implement it. And to those implementations, I would like to dedicate this section of the guide to my repositories.

### Game of Life

* **Link:** [github.com/krazov/game-of-life](https://github.com/krazov/game-of-life)
* **Technology:** almost entirely pure vanilla JS _(save for RequireJS because in 2016 native modules didn’t work in browsers yet)_
* **Context:** I was working in a company producing online roulette games, and I wanted to try to do a different type of game, and Game of Life, with its one-player mode (or even no-player), appealed to me.
* **Takeaways:** This was the first time I experimented with a flat array to store two-dimensional data (grid in this case). Unlike C/C++, JavaScript doesn’t have multidimensional arrays. Albeit the syntax looks the same, those are merely nested arrays, and while it works as a mental model, I thought that a single array where I would calculate the real position of the virtual one would be faster. It’s probably true for really large sets of data. The other thing was the graphic interface. I settled for an HTML table with animation handled with CSS transitions. It looked fine. I know because I had it deployed on a website, and I played a bit with it.

### Game of Life with Denizens

* **Link:** [github.com/krazov/game-of-life-with-denizens](https://github.com/krazov/game-of-life-with-denizens)
* **Technology:** again pure vanilla JS with RequireJS
* **Context:** It was 2017, and I got interested in `class`-based objects. Half of the code was written on the plane until the battery died.
* **Takeaways:** Now, JS doesn’t have classes, it’s still just an object with an attached prototype, but I was curious if writing the code like that has any upsides. I split each entity into a separate class: the game, the board, and cells. The cells were the titular denizens (citizens), each storing its information. This allowed me to experiment with accumulated scores (instead of usual alive/dead), but this didn’t lead to any interesting results. What I learned is if I want to have data married with its methods, `class` gives much more concise notation. (And since then, private properties were added, so it’s becoming more than just syntax sugar.)

### Game of Life with React

* **Link:** [github.com/krazov/game-of-life-react](https://github.com/krazov/game-of-life-react)
* **Technology:** React
* **Context:** In early 2018, I was tasked with rewriting our game. At the same time, I read that jQuery was finally dethroned in favour of React, and so I decided to give it a shot. The whole journey has been covered [in my Twitter thread](https://twitter.com/Krazov/status/948639475374190592) if you’re interested (I even got some hints from Dan Abramov himself in the process).
* **Takeaways:** First quirks aside, I found working with React pretty fast. The main thing that I liked was templating. While it felt a bit off to put HTML inside JS, it was much faster to work with and, as Douglas Crockford said, you should optimise developers time in the first place, not the code. He also said that DOM API is the thing that most people don’t like when they blame JavaScript. We decided to do our project in React (coupling it with Redux, RxJS, and Styletron).

## Take-home assignments

### Address book

* **Link:** [github.com/krazov/address-book](https://github.com/krazov/address-book)
* **Technologies:** vanilla JS (plus Grunt, incidentally)
* **Context:** In mid-2018 I applied for a tech lead position in a company and I got this assignment to solve. It was meant to mimic a large application, despite not being one, so it was supposed to be extendable. (I got the job, BTW.)
* **Takeaways:** Having a week deadline and assuming that if I start setting a React project, which I didn’t know enough, I would get stuck and produced nothing, I started with a single JS file for everything, and as the idea grew organically, I started splitting it into files and modules, coming up eventually with my templating engine and a message bus. I felt that with a couple of days more, I would start pursuing Virtual DOM. The question I got later on the interview was, “Have you thought about routing?” What I discovered was that vanilla JS is ready to be used to build apps. _Though, at the time, ES modules didn’t work in Firefox (d’oh), so I had to transpile it somehow, and I used Grunt, which we were using at my then-current job._

## GitHub archive

At some point in my life, I had to download a history of GitHub issues in one of our projects. I was not able to find any out-of-the-box tool, so I decided to write it myself. _Perhaps, I was not looking hard enough on purpose._

### Github tools

* **Link:** [github.com/krazov/github-tools](https://github.com/krazov/github-tools)
* **Technology:** Node.js, GitHub API
* **Context:** _(above)_
* **Takeaways:** Figuring things out with GitHub API was a nice thing, as well as creating all the communication between my tool and the API. Also, I had to think of a command-line presentation form.

### Github archive visualisation

* **Link:** [github.com/krazov/github-archive-visualisation](https://github.com/krazov/github-archive-visualisation)
* **Technology:** Vue, Nuxt.js
* **Context:** Having done the tools to download all the issues, I had to present them in a form readable to a non-technical person.
* **Takeaways:** It was my first and only approach to server-side rendering in the JavaScript world (I still remember PHP days, so it’s not as novel to me). The app was created pretty fast. Then, I generated the website to have a bunch of HTML files that can be open as, well, files. This, however, required some hardcoding of the links. In the end, the solution served its purpose very well and was even used later by a colleague of mine.

## Other

### Microservice

* **Link:** [github.com/krazov/microservice](https://github.com/krazov/microservice)
* **Technologies:** NodeJS, Mongoose, MongoDB, Express
* **Context:** Preparing for a conversation/interview for a back-end tech lead, I decided to implement a microservice. The idea of content handled was a simplified todo list (generic “notes”).
* **Takeaways:** This was a nice break from my day-job front-end activities. In two days, I managed to implement registration, logging in, logging out, as well as operations on notes: adding, editing, and deleting them. It was a weekend play, and it was abandoned shortly after (so, for instance, any logged-in user can mess up notes of anyone), however, I used detailed commits here, so more information can be read there.

### Cron tools

* **Link:** [github.com/krazov/cron-tools](https://github.com/krazov/cron-tools)
* **Technology:** JS
* **Context:** We ran into a situation at work where we had to calculate a difference between two crons. I said then, “It’s not a ticket, it’s a mini-project.” The ticket got cancelled (not a crucial thing) while I started working on this one.
* **Takeaways:** It was meant to be a fun project planned to end as an NPM package. Due to February 29th and months having a different number of days, it does only check within “safe ranges” (if the day was 31st, but it wasn’t specified which month, it would throw an error; the plan was to pass also a year, so this can be all calculated). It also uses detailed commits and was built in a TDD manner (every scenario starts as a test). At a bottom of my heart, I still believe I will return to it one day to cover all the corner cases.

### Multidimensional array

* **Link:** [github.com/krazov/multidimensional-array](https://github.com/krazov/multidimensional-array)
* **Technology:** JS (+ Jest)
* **Context:** An idea that was born while I was working on my first Game of Life. An optimal container for an array with a flat array underneath.
* **Takeaways:** Test-driven and based on a growing number of cases, failed due to my inability of creating sufficiently complex use-cases for 3D array (and here I was hoping to have 4D, 5D, and more). However, it was a fun thing to do as it appealed to my fondness of working with data structures.

### Escalator

* **Link:** [github.com/krazov/escalator](https://github.com/krazov/escalator)
* **Technology:** JS (+ Jest)
* **Context:** Made on a spark, it creates an object that allows storing consecutive sections of number that can _escalate_ the value to the next section if the range in the current one is full.
* **Takeaways:** I took a lot of fun with this one. It was also a good exercise in writing in a test-driven mode. Because it was a short project and my family was away, I managed to finish it. Not a small feat.

## Research

### Sorting business

* **Link:** [github.com/krazov/sorting-business](https://github.com/krazov/sorting-business)
* **Concept:** Sorting algorithms.
* **Context:** I was at a company event, getting slightly bored and overloaded with loud music when I realised that I am curious about the performance of various sorting algorithms. I left the party immediately and went back to a hotel room where I started coding.
* **Takeaways:** Sorting was never my strong side, so I had to refresh implementations myself and then come up with various test cases. As a cunning eye will notice, all the data is numeric. While at some point I was considering preparing also a variant with sorting strings or even objects, my interest ran its course before I got there. This repo also marks the tipping point of my fascination with functional programming. Everything is point-free and split into the smallest functions. While this seemed like a good idea, upon revisiting it, I realised it was a mistake because I have produced utterly illegible code. I have avoided this approach ever since, even making amends with loops. And that’s probably the main takeaway for me (the other one was exploring how algorithms worked differently for different sets of data).

### Fantasyland implementation

* **Link:** [github.com/krazov/fantasyland-implementation](https://github.com/krazov/fantasyland-implementation)
* **Concept:** Algebraic JavaScript Specification
* **Context:** A colleague sent me the link as something fancy, and I fell in love with it immediately. This was still in my FP phase, but I didn’t get to it until much later. This was partially documented, again, [on my Twitter](https://twitter.com/Krazov/status/1226080188217294849).
* **Takeaways:** I abandoned it quite early (my internal goal was to reach the monad milestone), so it turned out to be a TDD exercise above anything else.

### Linked list, class-based

* **Link:** [gist.github.com/krazov/00755de9645fb9a9c239ae635436390d](https://gist.github.com/krazov/00755de9645fb9a9c239ae635436390d)
* **Concept:** A linked list.
* **Context:** I got interested in linked lists when I was reading “Purely Functional Data Structures” by Chris Okasaki. Now, JavaScript has arrays dynamic enough to not need linked lists, so I had to implement them in my spare time.
* **Takeaways:** To be faster, I decided to work with a class-based component, which was fine, but in a way, it felt like a futile attempt because due to public properties, all linked-list functionality could have been bypassed. (There were still no private properties when I was writing it.) I also used chaining, which is the pattern I like, but rarely has a chance to use. There were some additional methods implemented, like map or filter. There is also an iterator that, among other things, allows to quickly convert the list into an array.

### Linked list, purely functional

* **Link:** [gist.github.com/krazov/77fd7a98bb1230accd3662db5d92d966](https://gist.github.com/krazov/77fd7a98bb1230accd3662db5d92d966)
* **Concept:** A linked list.
* **Context:** After not being fully happy with a class-based linked list, I decided to give it a fully functional treatment.
* **Takeaways:** This time the list itself is guarded very well, giving access to a snapshot of a single link in the chain. The only operations on the chain are possible through methods exposed with each snapshot. I also made a list two-sided, so it’s possible to go back and forth. Additionally, I experimented with non-enumerable properties for methods (with `Object.defineProperty`), so when shallow-cloning the snapshot, only the data will be copied.

### Assembler parser

* **Link:** [github.com/krazov/interpreter](https://github.com/krazov/interpreter)
* **Concept:** Various languages parsers written in JS.
* **Context:** Files in this repo started as solutions to katas from Code Wars. I thought I could rework them at some point into an in-browser parser/REPL, so I started collecting them for the future. This time still didn’t come. I have also an unfinished MySQL parser.
* **Takeaways:** When working on [an assembler parser](https://github.com/krazov/interpreter/blob/master/simple-assembler-interpreter-2.js), I learn that the `for` loop can be treated as a tape from which I can read. When putting lines of code into an array I can jump through it with a head. _This came in handy a year later or so when I figured out that instead of recursion, I could work on an array whose length is changing its size. It’s probably a thing not the most legible for others, but might be a useful hack in some cases._

## Other languages

As Douglas Crockford said once, you should learn new languages so you can see different ways of doing things. A couple of times, I got into a completely new language to acquire new perspectives and return with them to JavaScript.

### Trolley game

* **Link:** [github.com/krazov/trolley-game](https://github.com/krazov/trolley-game)
* **Technologies explored:** ClojureScript + Reagent
* **Context:** In January 2018, while looking for technology we could use in our new project, I stumbled upon ClojureScript, and I fell in love with its syntax and the way of expressing myself in it. It was not doable to use it for the actual project, but I wanted to give it a shot. At the same time, I was following a Facebook page for trolley dilemma memes, and someone posted a text-based game where you’d have to make choices about saving people or not and scoring in utilitarian and Kant points for each choice. I wrote to the author if they would be fine with me rewriting it from Python to ClojureScript and I got permission.
* **Takeaways:** ClojureScript was a different beast but at the same time, it felt familiar. For rendering purposes, I decided to use React, through Reagent bridge. What I liked about ClojureScript the most was its debugging: I could call any function from the project in the terminal to see how it behaves. The project was never finished and I have forgotten the language, and there are rather no jobs in it in Europe, so, likely, it will stay like that.

### Practical CommonLisp

* **Link:** [github.com/krazov/practical-common-lisp](https://github.com/krazov/practical-common-lisp)
* **Technology explored:** CommonLisp
* **Context:** A couple of years after my ClojureScript adventure, I was reading “Master of Doom” about id Software, and inspired by stories there, I realised I would like to dive more into some LISP dialect just for the fun of it. And so I decided to give it a shot. I found a book on CommonLisp and started going a chapter after chapter, pausing to do the exercises from the book, as well as doing my own.
* **Takeaways:** The largest thing I built with CommonLisp was, well, [a todo list](https://github.com/krazov/practical-common-lisp/blob/master/004_own-todo.lisp), my old flame, that could be run in a command line. It had all the functionalities needed and it was storing the results in the file, so it could be closed and opened later without losing the list. Working with Lisp was interesting because JavaScript is sometimes called a bastard dialect of Lisp, so while syntax is completely different, the underlying logic feels very familiar. Sadly, there is not much development in Lisp these days, and especially not in Europe, so the passion wore out.

## Writings

The Internet is full of various articles about technology. When I see that someone wrote about something, I have no interest in doing so as well, even if it’s an easy way to gather some sort of reputation. However, very rarely do I find a topic that hasn’t been covered. Then I step in and write about it. So far, it happened three times.

* [Non-`new` constructors](https://github.com/krazov/writings/blob/master/posts/non-new-constructors.md) – following Eric Elliott’s advice not to expose bare classes and inspired by Python’s approach, which my dear colleague Miguel showed me at work, I played a little with it. It didn’t catch on so far.
* [`instanceof` in depth](https://github.com/krazov/writings/blob/master/posts/instanceof-in-depth.md) – again inspired by Eric Elliott’s quote that _`instanceof` lies_, I explored the reasons why could that be so.
* [Cloning an object](https://github.com/krazov/writings/blob/master/posts/cloning-an-object.md) – after reading a couple of times about using `JSON.parse` and `JSON.stringify` to clone an object, I decided to throw in my three eurocents.

</details>