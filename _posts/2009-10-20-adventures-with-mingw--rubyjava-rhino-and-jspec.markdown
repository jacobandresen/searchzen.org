---
layout: post
title: "adventures with mingw , ruby,java, rhino and jspec"
date: 2009-10-20 11:10
comments: true 
categories: 
---
<strong>update 2010-10-05: jspec has been deprecated in favour of <a title="jasmine" href="http://pivotal.github.com/jasmine/">jasmine</a></strong>

<strong>update 2009-10-21: This post is a writeup of my early experiences with gemcutter and rubygems. The strange runtime error I did not understand was probably related to that I needed to update rubygems to 1.3.5.  <a href="http://www.pedant.dk/2009/10/21/gemcutter-the-missing-manual/">I now know how to use gemcutter from ruby1.8.6 using the oneclick installer</a> .</strong>

I have been using <a href="http://github.com/visionmedia/jspec/tree/3.x">jspec</a> on macosx for a while  and decided to give it a try on windows vista today. Installing jspec on macosx and linux can be done using the instructions <a href="http://github.com/visionmedia/jspec/blob/3.x/README.md">here</a> .

I want to run the automated jspec tests available via rhino at a client site. Sadly , I am forced to use windows there, so I have given some thought on how to make jspec run on windows.

First of all you need to install ruby.  I used the automated 1.8.6 One-Click Installer available <a href="http://www.ruby-lang.org/en/downloads/">here</a> . After installing i ran

<code lang="bash">
gem update
</code>

the instructions in the README file for jspec currently states that I should install gemcutter and install jspec via that . I was not able to do that on windows  ( my system decided to report an obscure runtime error that I did not understand). So i decided to do this instead:

<code lang="bash">
gem sources -a http://gems.github.com
gem install visionmedia-jspec
</code>

I let gem install the required dependencies visionmedia-commander and visionmedia-bind. After this I had the jspec script available. Sadly this gave me version 2.7.2 (I noticed \ruby\lib\ruby\gems\1.8\gems\visionmedia-jspec-2.7.2 ) <a href="http://gemcutter.org/gems/jspec">The listing on gemcutter</a> told me that a version 2.11.10 is a avaiable , so I decided to dig deeper. Maybe I could make gemcutter work anyway?

After a little browsing on github.com I found the <a href="http://github.com/oneclick/rubyinstaller/">oneclick installer</a>

I cloned this repo using git

using the following command:
<code lang="bash">
git clone git://github.com/oneclick/rubyinstaller.git
</code>

and pressed

<code lang="bash">
rake ruby19
</code>

This project creates a sandbox that compiles a working ruby environment using <a href="http://mingw.org/">mingw</a>.

After contemplating the insanity of what I was doing for a couple of minutes (remember : installing a working ruby on linux is a single shell command) I grabbed some coca cola and started browsing through the source code for ruby distro while the rubyinstall was compiling. I looked a bit at ruby.c and  vm_exec.c  and had grim flashbacks to my c days. Luckily the compile finished and I copied ruby19_mingw to my c:\ drive and set it up on my PATH variable. Then I could check which version I was using:

<code lang="bash">
C:\&gt;ruby -v
ruby 1.9.1p243 (2009-07-16 revision 24175) [i386-mingw32]
</code>

Now I was able to do:
<code lang="bash">
gem install gemcutter
gem tumble
gem install jspec
</code>

(Note that there is  information sent to the terminal during these steps)

Now for the interesting part(!) jspec was working , so I could do this:

<code lang="bash">
jspec init SolitaireCipher --freeze
</code>

This created a directory where I can train doing the <a href="http://www.rubyquiz.com/quiz1.html">SolitaireCipher</a> using javascript. I renamed lib/yourlib.core.js to lib/SolitaireCipher.js  and spec/spec.core.js to spec/spec.SolitaireCipher.js and spec/spec.dom.html accordingly.

After 20 mins of fiddling I managed to get some running tests in a browser by opening spec.dom.html. Then I decided I want to automate the tests using <a href="http://www.mozilla.org/rhino/download.html">mozilla rhino</a>. After installing rhino , I could run automated tests like this

<code lang="bash">
cd c:\projects\SolitaireCipher
jspec --rhino
</code>

This opens up a proces that listens to file changes in the lib and spec folders. All very well - untill I discovered that jspec currently uses ANSI codes to render colors to the terminal screens. ANSI codes are not supported on windows vista (something with ANSI.SYS being obsoleted), so if I want the nice colors then I need an alternative terminal than my command prompt in vista.

I found rxvt available from <a href="http://code.google.com/p/msysgit/downloads/list">PortableGit</a> on google code. This renders the colors just nicely - but has some other drawbacks. If I just use rxvt for rendering feedback from the jspec tests, then it seems to work though.

One thing to note is that rhino needs the java sdk to be installed and js.jar needs to be on your CLASSPATH. when starting jspec from rxvt on the msys from PortableGit, then CLASSPATH could be set like this (assuming rhino is installed in c:\tools ):

<code lang="bash">
export CLASSPATH=/c/tools/rhino1_7R2/js.jar
</code>

I probably want to avoid using rxvt on PortableGit too much . There are some major flaws listed <a href="http://code.google.com/p/msysgit/wiki/WhyIsRxvtNotTheDefault">here</a> .

Maybe I should look into doing a adobe air frontend for jspec?