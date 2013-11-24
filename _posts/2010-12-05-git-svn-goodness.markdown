---
layout: post
title: "git svn goodness"
date: 2010-12-05 03:12
comments: true 
categories: 
---
Some time ago I put a experimental websocket gameserver using node js and socket-io into a branch on 1942js on google code.

These days I prefer git over svn ,so I created 1942jsmulti on github.com and tried this :
<pre>git svn clone https://1942js.googlecode.com/svn/branches/multiplayer/ 1942jsmulti
git remote add origin git@github.com:jacobandresen/1942jsmulti.git
git push origin master</pre>
Now I can mirror changes from the svn repo and still use git . sweet!