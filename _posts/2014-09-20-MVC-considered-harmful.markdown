---
layout: post
title: "MVC considered harmful"
date: 2014-09-20 07:56
comments: false
categories:
---
Having spent considerable amounts of time looking at large javascript and HTML related codebases I have come to one conclusion:
most attempts at structuring frontend code or anything UI related in a team setting will fail if the attempts does not consider the long traditions
for software development - and understand the mental models that have been formed so far.
Or as [George Santayana](http://www.wikiwand.com/en/George_Santayana) put it "Those who cannot remember the past are condemned to repeat it".

To better understand the historical context I think all web developers should be at least familiar with a basic description of
the MVC pattern and familiar with the existing frameworks that are allready available.

## A detour around Xerox PARC
Prior to the internet - programming mostly involved a workstation and in some cases a central server with a central datastore .
Programming was mainly about data entry and computation and how share the results of that in a meaningfull manner.
Great care and effort was put into meeting the immediate expectations of the users and programming was typically done using a structured plan - something that we know today as the [waterfall model](https://www.wikiwand.com/en/Waterfall_model) .
Software modelling was (and still is) done by using metaphors to map user needs into software and carefully designing the sofware using object 
oriented constructs.
One prevalent approach was to apply the MVC pattern invented by [Trygve Reenskaug](https://www.wikiwand.com/en/Trygve_Reenskaug)
in 1978 while visiting Xerox PARC.

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

It should be noted that most of the listed frameworks now have implemented MVVM as an adaption of MVC.
Microsoft introduced [MVVM](http://addyosmani.com/blog/understanding-mvvm-a-guide-for-javascript-developers/) as an adaption of MVC to
with considerations about the costs of exposing the entire model to the view. This was originally available via Silverlight and WPF and to some
extent Adobe Flex -  but has now been widely implemented by other frameworks.

## Using MV* javascript frameworks is not a quick fix
With the advent of javascript  MV* frameworks we now should have a shared vocabulary for programming , but for many practical use cases regarding
web applications it is typically disregarded. Why is that?

One might argue that the average bravado of your average-day web hacker resembles that of a hired gun in the wild west. It is very easy to reach small
implementation goals fast using HTML, css and javascript.  Javascript was introduced during the early days of the web to introduce more advanced ways 
of interaction in a web application - not as a  means of structuring applications per se. The early version of javascript was implemented by Brendan 
Eich in [10 days](https://www.w3.org/community/webed/wiki/A_Short_History_of_JavaScript) and contains shortcomings that has lead to use of linters 
like [jslint](https://jslint.com).  Popular javascript libraries like [prototypejs](https://prototypejs.org) (that was popular during the rise of 
[ruby on rails](https://rubyonrails.org) ) and  [jquery](https://jquery.com) tried to address some of the shortcomings and disparaties in  
[DOM](https://wwww.w3.org/DOM) manipulation the various browsers. Somewhat deservingly javascript gained the notion of a toy language by professional
programmers in its early days - this situation has changed with the introduction of tools like jslint and the ability to focus on
[the good parts](http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742) of javascript. And with the advent of  javascript on the
serverside it is possible to end-to-end solutions for clean room MVC  - but in most practical scenarios where the server implementation will be in 
something other than javascript, then there will be some kind of duplication of logic on the server and the client. Or as zxibit could have said:

*Yo Dawg I hurd you like MVC so I put a MVC in your MVC*

Jokes aside ... It is important to understand that taking the MVC paradigm and applying it on web application programming in the same manner as you 
would have applied it to application programming in the PC era could be considered harmful. The web has a entirely different delivery mechanism 
than your local PC had.

##  Understanding the web as a delivery platform 

The main difference between  a local pc application and a web application today is typically that the web application involves data available from 
another machine. This should not pose a noticeable problem when rendering logic is expressed on the server - e.g when all the view is rendered via one call to the 
server. But if the view is constructed on the client side and requires several calls to fetch data e.g for a compound view then this could pose a problem
performancewise. It should be immediately obvious that a solution where all data comes prerendered will be faster than a solution that requires data to 
be assembled via several calls. When you also consider the added complexity of tackling layout changes as a result of unpredictable results then you 
could start considering looking for ways to improve performance. So - one obvious choice would be to minimize the amount of needed calls to the server.



## Where to go from here?
First of all - You should think very hard about what you are doing if you are planning to roll your own MVC framework. If you are going to do it anyway
I hope you at least browse through the [allready available frameworks](https://todomvc.com) and familiarize yourself
with the basics of [MV*](http://addyosmani.com/blog/understanding-mvvm-a-guide-for-javascript-developers/) and understand the performance penalties of cleanroom MVC.

One  way to minimize the number of calls to server would be to setup a fullstack solution - where javascript is used both on the server and on the client
side. This could be done e.g with [react.js](https://facebook.github.io/react/) that has introduced the use of a virtual dom so that you can reason about
the entire page before starting rendering on the client side (here is an example to get started: [react server example](https://github.com/mhart/react-server-example) ).
  react.js could be used for the V in MV* . For the M you could use [Backbone.js](https://backbonejs.org) or vanilla javascript constructs.


If you are thinking about refactoring an existing codebase to support better separation of concerns then I suggest that you consider a temporary goal before
switching your entire codebase to e.g angular og ember.js . If you are in a situation where view rendering are constructed  via javascript or some custom constructs 
on the serverside the you could consider if you could express the sample logic via an existing templating engine. E.g if you are considering a switch to
ember.js then it could be worthwhile to try to port some of your viewlogic to [handlebars](http://handlebarsjs.com/) first. If your existing codebase was constructed
sometime after 2000 then chances are that data retrieval/manipulation parts allready are expressed in manner that are without rendering logic - if  not - then you could
refactor them to be so.

