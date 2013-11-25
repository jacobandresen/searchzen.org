---
layout: post
title: "Learning some Sencha touch MVC code fu at sourcedevcon 2011"
date: 2011-05-08 03:05
comments: true 
categories: 
---
This week I had pleasure to attend sourcedevcon 2011at the awesome resort  <a title="Le meridien split" href="http://www.starwoodhotels.com/lemeridien/property/overview/index.html?propertyID=1956">Le meridien Split</a> together with  <a title="Virdun" href="http://twitter.com/#!/Virdun">@virdun </a> ,<a title="JakobKruse" href="http://twitter.com/#!/search/jakobkruse">@jakobkruse </a>and <a title="@StureAndersen" href="http://twitter.com/#!/StureAndersen">@stureandersen</a> . I have been lurking for a couple of years in the ExtJS community  since attending  the extjs conference in Orlando back in 2009, keeping up to date on things at our local <a title="Öresund ExtJS meetup" href="http://www.meetup.com/The-Oresund-ExtJS-Meetup/">Öresund ExtJS meetup</a> , so it was nice to get in touch with some of the regular faces in the ExtJS community.

<p style="text-align: left;">Flying into Split I had some doubts on how many ExtJS devs would take their time to fly to split, this being the first community-driven sencha conference in Europe. After arriving I quickly put all my doubts aside - since the venue and conference organization was carefully laid  out.  Split itself is a very charming city, and we had an easy time arriving (leaving was another problem though). I was impressed by the fact that 200+ attendees had chosen to show up (that figure somewhat resembles the first Orlando conference in the US).</p>
At the venue , the first thing we noticed was the outstanding bar with an overview of the local marina and the ExtJS swedes <a title="FredricBerling" href="http://twitter.com/#!/FredricBerling">@FredricBerling</a> , <a title="EmilPennlov" href="http://twitter.com/#!/EmilPennlov">@EmilPenlov</a> (and @<a title="Mats Bryntse" href="http://twitter.com/#!/Bryntum">bryntum</a> when he was not to busy hanging out in some other bars).
<h2>Learning some  Sencha touch MVC  Code fu.</h2>
At some point Johan (@virdun)  decided that he wanted  to get a Sencha Touch application up and running  . So we kind of lost him for a moment there in the bar.  I don't remember if it started before <a href="http://twitter.com/#!/jamespearce">@jamespearce</a> introducing sencha touch  - but Johan started hacking furiously on this app for his site <a title="Citypolarna" href="http://citypolarna.se">http://citypolarna.se </a> somewhat right about  that session.

Being Johan, he just wouldn't let go, so I had to answer a lot of questions  about how sencha touch applications worked.

When I discovered that Johan was not being satisfied by the answer "but hey, I haven't coded a line of sencha touch yet" we walked through the basic shopping list example for sencha touch and Johan modified it a bit, so it could serve as as base for implementing an event viewer for citypolarna. Combining the info found on <a title="sencha" href="http://sencha.com">http://sencha.com</a> and info from the sessions by <a title="_jdg" href="http://twitter.com/#!/_jdg">@_jdg </a>and <a title="@edspencer" href="http://twitter.com/#!/edspencer">@edspencer </a>this was an easy task, so modifying the shopping list example to a working application could be done during the conference. Oh yes, it also helped that we remember  to use extraParams instead of baseParams .


<h2>Learning to migrate to ExtJS 4</h2>
Besides learning more about sencha touch I learned a lot from <a title="@bmoeskau" href="http://twitter.com/#!/bmoeskau">@bmoskeau</a>'s session on migrating from to ExtJS 4.

Here I especially noted that using the MVC pattern can be postponed to a last optional step and that during migration to ExtJS 4, the old "new" constructor syntax should be able to work (but that the new Ext.define and Ext.create constructs is the preferred way to go).  Brian laid out a migration strategy using the   4 R's  "Rendering , Running, Ready, Refactor" describing the 4 stages the migration should go through.

<h2>ExtJS Scheduler and Calendar</h2>
The session by <a title="@bmoeskau" href="http://twitter.com/#!/bmoeskau">@bmoskeau</a> and <a title="Mats Bryntse" href="http://twitter.com/#!/Bryntum">bryntum</a> on Ext Calendar and Ext Scheduler  was supposed to be a showcase of the two products, but to me the main value of the session was seing how easy it was to integrate such complex ExtJS  components. My jaw dropped when I saw Brian demonstrate him using his component updating the data model simultaneously in ExtJS scheduler. This is a testament to two very well designed components .
<h2>Wrapup</h2>
All in all sourcedevcon 2011 left me with the impression of a very vibrant ExtJS community  - I also got the impression of the strong commercial focus Sencha has. Sencha presented   Sencha.IO as a product - I look forward to exploring that  more indepth in the future. I chose to focus more on learning about Sencha touch and the MVC parts of ExtJS 4 during the conference..

"The Irish guys" has posted some writeups of their experiences at sourcedevcon . Well worth a read:

<a title="The lowdown of sourcedevcon" href="http://www.darraghduffy.ie/?p=294">The lowdown of sourcdevcon</a>

<a title="sourcedevcon day1" href="http://www.joelennon.ie/2011/05/05/source-dev-con-day-1/">http://www.joelennon.ie/2011/05/05/source-dev-con-day-1/</a>

<a title="@nilsdehl" href="http://twitter.com/#!/nilsdehl">@nielsdehl</a> has posted pictures from the conference at flickr here :

<a title="sourcedevcon day1" href="http://www.flickr.com/photos/nils-dehl/sets/72157626648487744/">http://www.flickr.com/photos/nils-dehl/sets/72157626648487744/</a> (sourcedevcon day1)

<a title="sourcedevcon day2" href="http://www.flickr.com/photos/nils-dehl/sets/72157626533490549/">http://www.flickr.com/photos/nils-dehl/sets/72157626533490549/</a> (sourcedevcon day2)

<a title="sourcedevcon day3" href="http://www.flickr.com/photos/nils-dehl/sets/72157626544637927/">http://www.flickr.com/photos/nils-dehl/sets/72157626544637927/</a> (sourcedevcon day3)

<a title="sourcedevcon day4" href="http://www.flickr.com/photos/nils-dehl/sets/72157626672433598/">http://www.flickr.com/photos/nils-dehl/sets/72157626672433598/</a> (sourcedevcon day4)
<div id="_mcePaste" class="mcePaste" style="overflow: hidden; position: absolute; left: -10000px; top: 238px; width: 1px; height: 1px;">http://www.joelennon.ie/2011/05/05/source-dev-con-day-1/</div>
