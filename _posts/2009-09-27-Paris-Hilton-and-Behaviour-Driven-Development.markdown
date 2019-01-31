---
layout: post
title: "Paris Hilton and Behaviour Driven Development"
date: 2009-09-27 06:09
comments: true 
categories: 
---
Recently, I have been giving Behaviour Driven Development some thought.

Let's take a an example of how to develop and test a  music video search and storage  system. A traditional way of developing this would require formulating a object oriented system architecture, thinking about streaming and metadata enabled search. The system architecture could consist  of a well chosen database server, a streaming server and a metadata enabled search engine - combining these technologies with a modern UI  and encapsulating theme in carefully designed object oriented structures. During all these important choices , and all during development we would make sure to write tests before we write a single line of code.

All these things put together would lead to a well thought out system architecture , but all the effort put into the system architecture can be in vain - if we don't have a solid business understanding of what a video storage system should do. What will the users expect?

While browsing on <a href="http://www.facebook.com">facebook</a> this other day I found the <a href="http://www.facebook.com/group.php?gid=5299495387">"The Paris Hilton &amp; Jacques Derrida Appreciation Society" </a> - this group explores the connections between the works of Paris Hilton and Jacques Derrida. When we deconstruct the "pretty blonde" facade of Paris Hilton, then you can actually find some deep insights. Take "Nothing in this world" for instance:

<object width="560" height="340"><param name="movie" value="http://www.youtube.com/v/32DwYTRmmto&amp;hl=en&amp;fs=1&amp;" /><param name="allowFullScreen" value="true" /><param name="allowscriptaccess" value="always" /><embed type="application/x-shockwave-flash" width="560" height="340" src="http://www.youtube.com/v/32DwYTRmmto&amp;hl=en&amp;fs=1&amp;" allowfullscreen="true" allowscriptaccess="always"></object>

Take the phrase "when you are with somebody else, that's me in your eye".  There is the obvious interpretation of the sentence .  But thinking about that sentence also let's you reflect on the <em>real meaning</em> . When you look at Paris Hilton in this video, what do you see? Do you see the pretty blonde or the millionaire , hard working young girl . In this video I am seeing the image of the pretty blonde - but I am also thinking about the millions of dollars she is earning portraying herself in this way.  So in a sense - I am reading the original message out of context. I am admiring what Paris Hilton in some other way than she intended - the original meaning of the words seem to have disappeared - but my understanding of the sentence is more useful to me.  I wish I could do what Paris Hilton does - but in a way that would make sense in my world .

The producers of the "Nothing in this world" video are not likely to convey information about the business empire of Paris Hilton in the metadata supplied for the video. So a system formulated as a "video storage system" would not let me exploit the information I found in the facebook group.

BDD introduces the use of a Domain Specific language to express the users expectations in a manner more directly focused on the behavioural aspects of the system. This lifts the clouds from the system aspects and focuses on <em>intent</em>.

A better way to formulate my expectations for the system would be:
<pre>Describe the music video storage system:
  I should be able to search for videos using metadata
  it should play videos  in my browser
  I should be able to query facebook for information about it</pre>
If I had those expectations formulated to me , then I would choose to implement this system as a mashup between youtube and facebook as a facebook application. This would be a radically different system architecture than the one describe above.

Furthermore , by leveraging one of the several BDD test frameworks available, then the expectations could be formulated in way that can be used as tests.
