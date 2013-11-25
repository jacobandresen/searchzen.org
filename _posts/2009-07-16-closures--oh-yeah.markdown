---
layout: post
title: "closures -oh yeah?"
date: 2009-07-16 09:07
comments: true 
categories: 
---
Hvad mon der sker her :

{% highlight JavaScript %}
  var a=1;
  function foo() {
    var a;
   function bar() {
     a=2;
     return a;
   }
  return bar;
  }

  a=3;
  var b=foo();
  var c=b();
  alert(c);
  alert(a);
{% endhighlight %}
