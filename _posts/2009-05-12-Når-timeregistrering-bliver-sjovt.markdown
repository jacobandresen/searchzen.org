---
layout: post
title: "Når timeregistrering bliver sjovt"
date: 2009-05-12 07:05
comments: true 
categories: 
---
Alle der har været i nærheden af et timeregistreringsystem ved hvor kedeligt det kan være. Nåja - det kan være effektivt ifbm. at forbedre ens udviklingsteknik - men det er stadigvæk <strong>KEEDELIGT</strong> .

Det har jeg heldigvis nu mulighed for at lave om på vha <a href="http://www.fogcreek.com/FogBugz/">fogbugz</a> ! Fogbugz tilbyder et <a href="http://www.fogcreek.com/FogBugz/docs/60/topics/advanced/API.html">REST api</a> så det er fleksibelt i den forstand at jeg kan benytte et selvvalgt sprog til at kode en applikation op imod det på en enkelt facon.

For <a href="http://rubyforge.org/projects/rubyinstaller/">ruby</a> kan man f.eks gøre således vha <a href="http://rubygems.org/">rubygems</a>:
<code lang="bash">
gem sources -a http://gems.github.com
gem install austinmoody-fogbugz-api
</code>

for derefter at skrive flg vha ruby:

<code lang="ruby">
require 'rubygems'
require 'fogbugz-api'
fb = FogBugz.new("stureaps.fogbugz.com", true)
fb.logon("jacob@stureaps.dk", "mitkodeord")
mycases = fb.search("AssignedTo:\"Jacob Andresen\"")
mycases.each {|c| print c.to_s + "\n" }
fb.logoff
</code>

Derfra er det jo så meget sjovt at kigge på resultatet på kommandolinjen!  Et lidt mere seriøst brug kunne være at udtrække rapporter over tidsforbrug.