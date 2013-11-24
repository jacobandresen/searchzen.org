---
layout: post
title: "gemcutter: the missing manual"
date: 2009-10-21 07:10
comments: true 
categories: 
---
Thanks to <a href="http://www.kruse-net.dk">Jakob Kruse </a> I now know how to operate RubyGems and gemcutter on windows. Here's what I did:

1:I downloaded the 1.8.6 ruby installer <a href="http://www.ruby-lang.org/en/downloads/">here</a>

2: I installed gemcutter like this:

[bash]
gem update --system
gem install gemcutter
gem tumble
gem install jspec
[/bash]

this let me use gemcutter on windows using the current one-click installer ;)