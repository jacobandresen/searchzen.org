---
layout: post
title: "MVC considered harmful"
date: 2014-09-20 07:56
comments: false
categories:
---
Having spent considerable amounts of time looking at large javascript and HTML related codebases I have come to one conclusion: most attempts at structuring frontend code or anything UI related in a team setting will fail if the attempts does not consider the long traditions for software development - and understand the mental models that have been formed so far. Or as [George Santayana](http://www.wikiwand.com/en/George_Santayana) put it "Those who cannot remember the past are condemned to repeat it".

To better understand the historical context I think all web developers should be at least familiar with a basic description of the MVC pattern and familiar with the existing frameworks that are allready available and understand their benefits and shortcomings before setting out to implement new ones.

# A detour around Xerox PARC
Prior to the internet - programming mostly involved a workstation and in some cases a central server with a central datastore . Programming was mainly about data entry and computation and how share the results of that in a meaningfull manner. Great care and effort was put into meeting the immediate expectations of the users and programming was typically done using a structured plan - something that we know today as the [waterfall model](https://www.wikiwand.com/en/Waterfall_model) . Software modelling was (and still is) done by using metaphors to map user needs into software and carefully designing the sofware using object oriented constructs.  One prevalent way of approach was to apply MVC patterne invented by [Trygve Reenskaug](https://www.wikiwand.com/en/Trygve_Reenskaug) in 1978 while visiting Xerox PARC.  

At the core of the MVC paradigm is :

* Model -  Encapsulating the data and the domain logic
* View -   Presenting data to the user
* Controller - Responsible for controlling the flow in the application and sending data back and forth between the model and the view.

The MVC pattern has been been the foundation for many of the modern user interfaces and frameworks we know today. Examples include [Java Swing](http://www.oracle.com/technetwork/java/architecture-142923.html), [Ruby on Rails](http://guides.rubyonrails.org/getting_started.html)  and [asp.net MVC](http://www.asp.net/mvc) .  
 
Several implementations of javascript MVC frameworks allready exist. You can compare the different implementations via the [TodoMVC](http://todomvc.com) . As you might have noticed there are allready a lot of implementations readily available so there is [no need to go about implementing your own](http://blog.tastejs.com/yet-another-framework-syndrome-yafs).

Some of the most currently publicly visible projects are:

* [angular](https://angularjs.org)
* [ember](https://emberjs.com)
* [Knockout](https://knockoutjs.com)
* [Backbone](https://backbonejs.org)
* [ExtJS](http://dev.sencha.com/ext/5.0.0/)

It should be noted that most of the listed frameworks now have implemented MVVM as an adaption of MVC. Microsoft introduced [MVVM](http://addyosmani.com/blog/understanding-mvvm-a-guide-for-javascript-developers/) as an adaption of MVC to with considerations about the costs of exposing the entire model to the view. This was originally available via Silverlight and WPF and to some extent Adobe Flex -  but has now been widely implemented by other frameworks.

## Using MV* javascript frameworks is not a quick fix
With the advent of javascript  MV* frameworks we now should have a shared vocabulary for programming , but for many practical use cases regarding web applications it is typically disregarded. Why is that?

One might argue that the average bravado of your average-day web hacker resembles that of a hired gun in the wild west. It is very easy to reach small implementation goals fast using HTML, css and javascript.  Javascript was introduced during the early days of the web to introduce more advanced ways of interaction in a web application - not as a  means of structuring applications per se. The early version of javascript was implemented by Brendan Eich in [10 days](https://www.w3.org/community/webed/wiki/A_Short_History_of_JavaScript) and contains shortcomings that has lead to use of linters like [jslint](https://jslint.com).  Popular javascript libraries like [prototypejs](https://prototypejs.org) (that was popular during the rise of [ruby on rails](https://rubyonrails.org) ) and  [jquery](https://jquery.com) tried to address some of the shortcomings and disparaties in  [DOM](https://wwww.w3.org/DOM) manipulation the various browsers. Somewhat deservingly javascript gained the notion of a toy language by professional programmers in its early days - this situation has changed with the introduction of tools like jslint and the ability to focus on [the good parts](http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742) of javascript. And with the advent of  javascript on the serverside it is possible to end-to-end solutions for clean room MVC  - but in most practical scenarios where the server implementation will be in something other than javascript, then there will be some kind of duplication of logic on the server and the client. Or as zxibit could have said:

![Yo Dawg I hurd you like MVC so I put a MVC in your MVC](http://cdn.meme.am/instances/500x/50530257.jpg)


Jokes aside ... It is important to understand that taking the MVC paradigm and applying it on web application programming in the same manner as you would have applied it to application programming in the PC era could be considered harmful. The web has a entirely different delivery mechanism than your local PC had.

## Latency is the bottleneck
Speed is the ultimate feature




Speed: 14.k initial payload

## Package managment

We also have to consider the problem of having a highly competitive javascript ecosystem. We have several competing javascript frameworks - and reusing code between them can be a challenge. Some solutions are bettter than other solutions.
sconf eu 2013 - introducing react.js . Throwing out well established perceptions about MVC
Clarity and readabilityy

#Where to go from here?
react.js
pjax
Webcomponents!
