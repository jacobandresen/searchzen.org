---
layout: post
title: "icanhas javascript OOP?"
date: 2009-12-12 05:12
comments: true 
categories: 
---
In javascript we can express objects using the prototype notation:

[javascript]
  var Cat = function () {
     this.furry = true;
  }
 Cat.prototype.greet = function () {
   return &quot;meeow&quot;;
 }
[/javascript]

using class mimicking from <a href="http://prototypejs.org/">prototype-js</a> it would be :

[javascript]
 var Cat = new Class({
  initialize: function (){
    this.furry = true;
    },
  ask: function (item) {
   return &quot;icanhas &quot;+item+&quot; ?&quot;;
 });
[/javascript]

This example should be pretty clear. But when we get into real-life application scenarios we need to interact with users and databases.

Let's say we had a panel and a button for interacting with <a href="http://icanhascheezburger.com/2008/08/12/funny-pictures-i-fightz-dem/">lolcats</a>:

[javascript]
var CatInformationPanel = Class.create({
   initialize: function (container) {
     $(container.id+'_furry').checked = true;
     $('petButton').observe('click',  this.ask.bindAsEventListener(this));
  },
  ask:  function (item) {
    $(container.id+'_text').value =&quot;icanhas &quot;+item+&quot; ?&quot;;
  }
});
[/javascript]

Note that we need to bind "this" to the the function scope for "ask". this is one of the intricacies of object oriented javascript. Here are <a href="http://alternateidea.com/blog/articles/2007/7/18/javascript-scope-and-binding">some badass ninja examples</a> to explain why.

Now, after interacting with user , you probably want to save the result to a database. let's assume that you have a resource /lol/cat/questions you can issue a HTTP post to (you can create this using <a href="http://rubyonrails.org/">rubyonrails</a> or  something similar).

[javascript]
var CatInformationPanel = Class.create({
   initialize: function (container,name) {
     this.name = name;
     $(container.id+'_furry').checked = true;
     $('petButton').observe('click',  this.ask.bindAsEventListener(this));
  },
  ask:  function (item) {
    var question = &quot;icanhas &quot;+item+&quot; ?&quot;
    $(container.id+'_text').value =question;
   var request = new Ajax.Request ({
      &quot;/lol/cat/question&quot;, {
        method:'post',
        params:{ name:name, question:question },
        onSuccess: function (json) {
           alert(&quot;saved question&quot;);
           }
     }
    });
  }
});
[/javascript] 