---
layout: post
title: "Code all the things"
date: 2020-07-26 21:07
comments: false
categories:
---
Much to my delight - it seems that dramatic increase of new  JavaScript MVC frameworks have stopped. Efforts like ["TodoMVC"](https://github.com/tastejs/todomvc) and ["Realworld"](https://github.com/gothinkster/realworld) have served to highlight the practical problems of using the web as a delivery platform while also highlighting the allready and wellcrafted solutions to the known problems. It also seems that people have started ["second guessing the modern web"](https://macwright.com/2020/05/10/spa-fatigue.html) - wondering if there is more to it than just optimizing using serverside rendering and data fetching.

Some time ago, I received a good advice: "Do not think too much about the frontend, it will be redone in 5 years". My experience so far has shown , that this advice has been a solid one - most of the choices having been made 5 years ago about encapsulating the variances in internet browsers are largely irrelevant today.  I think it is safe to say, that my earlier JavaScript framework favourites ["Prototype"](https://prototypejs.org/), ["jQuery"](https://jquery.com/) and ["ExtJS"](https://www.extjs.com/) have come and gone. Having acknowledged that I need to move on I also realized that most of my architectural decisions have been formed by what I learned during these times - and to what extent my thinking have been formed what the words I have learned to use in this period.


## "There is more to life than Java applets"

Now that the years have passed, I also understand that my eagerness and preference for modelling everything using object constructs during my web programming days in the 00's and the early 10's have been founded in what I have read in books, and used in my early Java applet programming days. My intuitive fondness of what I saw in my ["ExtJS"](https://www.extjs.com/") was based in that I could easily related to have I programmed solutions using Java and ["AWT"](https://docs.oracle.com/javase/7/docs/api/java/awt/package-summary.html)  - while paying little or no attention to the web as a delivery platform.

Modern web development, while still being centered around ["SPA's"](https://en.wikipedia.org/wiki/Single-page_application) is now progressing more in the lines of reactive programming than the traditional MVC/MVVM approach  - so in that sense web programming is evolving away from the traditional desktop/server metaphor and is is now embracing concepts like reactive programming and immutable datastores. By employing immutable data stores, we now have a way for easy reasoning about what parts of the user interface should be updated, even allowing it to be done stepwise - in a coordinated manner. The concepts from ["Reframe"](http://day8.github.io/re-frame/) now have widespread applications in the industry  - eg ["Redux"](https://redux.js.org/) and ["NGRX"](https://ngrx.io/) . In addition, we now have the support of "map" and "reduce" constructs from ["ES6"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) and more declarative style of programming via ["rxjs"](https://www.learnrxjs.io/) .

  But before progressing more in the lines of reactive programming and leaving traditional MVC style programming behind completely I thought it would be worthwhile to stop and pause for a while to reflect on my route ahead. 

## "Hic Sunt Dracones"

In my daily practice  I have seen good software development as something being rooted in usecases - and I have made most of my practical implementation choices from the the availability of supporting tools.  It is hard to start to use a tool that you do not have - but when you get the new tools, they usually build upon learnings that were required to build the new tool. My learnings so far have been rooted in experiences gained by trying to improve my existing practice using existing tools or processing, not contemplating how to improve my practise with no reference to tools at all. 

So how do we form a good practice for software development that is not rooted in tooling or use case analysis, but more in the line of captured experiences and less friction when developing?  Thinking in these lines , I came to remember one afternoon where I visited ["The Royal Geographic Society"](https://www.rgs.org/) where I saw a ["sextant"](https://en.wikipedia.org/wiki/Sextant) for the first time in my life. A sextant has come to me as a symbol of a tool , that is now outdated , but has formed a line of new and updated tools , that serve the same purpose. Tools can be refined , but the original intent of them  and the continued mindset will endure.  Similar tools exist in the software world , e.g ["LISP"](https://en.wikipedia.org/wiki/Lisp_(programming_language)) and ["Haskell"](https://www.haskell.org/) - these language have defined whole families of ideas , and served as a hallmark for industrial strength programming. But in themselves, these tools cannot carry the definitions of systems - they need earlier experiences to be captured in writing. For the example of using a sextant , a nautical charts and maps are required. For software development we have developed the tradition of ["design patterns"](https://en.wikipedia.org/wiki/Software_design_pattern) that can be used to navigate and discuss software architectures . But still - as for the early days of exploration - effective use of a sextant and maps was not allways enough, there still had to be an idea for the journey, as welll as the passing along of experiences from earlier explorer In the early days of exploration ,there was a tradition of marking "Dangerous" or "unexplored" waters with ["Hic Sunt dracones"](https://en.wikipedia.org/wiki/Here_be_dragons). This sentence could serve both as a warning and a invitation to later explorers. 

In my experience - the dangerous waters in software development tend to be related to discrepancies between formal methods and the actual lived experiences of human beings. Formal methods being based on logic or mathematical descriptions will at some point fail to capture the essense of problem at hand, when the system being developed is suposed to assist human beings.  Or put it in antother way - a strictly systematic approach such as traditional  ["Software engineering"](https://en.wikipedia.org/wiki/Software_engineering) will fail to capture the elusive nature of human life. We need a fresh way to capture the ever changing conditions of human life in code in a rapid manner. In essence - we need to consider web development as a craft, not a formal discipline. 


## "Code all the things"

So how do we escape the formalism of Software engineering and focus more on the lived experiences of actual human beings?  The answer to that question might seem a bit counter-intuitive. I think we need to code all the things!

![Code All the tings](/public/code_all_teh_things.jpg)

I think that decisions or design considerations relevant to features should be taken the teams implementing them whenever possible. In my experience - code that captures or tries to mimic human experience wille be more successfully implemented , when the teams implementing it have a better understanding of the context (I tried to capture my thoughts on this as ["Mindful software"](/2011/04/19/Mindful-software/) ).  Given that features will be implemented using  code, it would beneficial that the features are described in manner that uses code whenever possible. Concretely, to me "code all the things"  would the mean the following to me in the context of implementing features for an organisation in 2020:


* evolve feature descriptions using automated test specifications (e.g using ["cypress"](https://cypress.io)
* maintain and use a common design system using modern styling mechanisms (e.g ["SASS"](https://sass-lang.com/)
* maintain and use a common component library (e.g using ["TypeScript"](https://www.typescriptlang.org/)  and ["StoryBook"](https://storybook.js.org/) ) 
* implement features using microservices for easier scalability  (e.g using ["Docker"](https://www.docker.com/) and ["Kubernetes"](https://kubernetes.io/) and ["OpenAPI"](https://swagger.io/specification/) )
* guide system coherency using reactive programming (E.g using ["Reactive extensions"](http://reactivex.io/) )
 
What it specifically does NOT mean is:
- Encapsulate and code everything in your MVC framework frontend framework. Some things are better done on the serverside.
- refer to general descriptions on post-its captured during "wave planning" . Agility is not being vague.
- continously referring to "what we agreed upon at standup". Consensus is not allways optimal.

My point here is that the more technical context a description can be provide , the better. If the description is in a allready running form , then this should be optimal. Maybe we can find a way to perform system development where we code all the things and embrace change faster in this way?









