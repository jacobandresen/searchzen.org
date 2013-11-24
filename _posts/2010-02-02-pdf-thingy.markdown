---
layout: post
title: "pdf thingy"
date: 2010-02-02 08:02
comments: true 
categories: 
---
<strong>Update 2010-10-16:</strong>

<strong>I took pdf-thingy offline from github.</strong>

<strong>Update 2010-05-08:</strong>

<strong>Google has decided to discontinue Google wave, so  I  will stop updating pdf-thingy.</strong>

I've spent a couple of hours tinkering with pdf export from wave. I put the result here :
pdf-thingy@appspot.com . You can invite the bot to your wave, when you do it will present a link to a pdf version of the root blip. No fancy colors yet ;)

Somebody pointed me to <a href="http://googlewavebots.info/wiki/index.php?title=PDF_Wave_Exporter">PDF Wave Exporter</a>, but I could not find the source code for it to tinker with. (I admit that I did not look that hard).

I implemented pdf thingy to learn more about python,wave and google appengine.

I based pdf-thingy on exporty by Pamela Fox , available from <a href="http://code.google.com/p/google-wave-resources/">google code</a> .  <a href="http://konryd.blogspot.com/2008/04/outputting-pdfs-with-google-app-engine.html">This tutorial</a> helped me learn about reportlab on google app engine.

You can find the code here: <a href="http://github.com/jacobandresen/pdf-thingy">http://github.com/jacobandresen/pdf-thingy</a>

There are some obvious points of improvement:
- handle text overflow
- supporting annotations
- fancy color templating