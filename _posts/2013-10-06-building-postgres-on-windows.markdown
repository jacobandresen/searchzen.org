---
layout: post
title: "Building postgres on windows"
date: 2013-10-06 16:51
comments: true
categories: Databases
---

So. Lately I have been advocating a switch to [postgres](http://www.postgresql.org/) from various BigCo databases. I have been inferring that "postgres" is "just better". But basically I don't have a clue. I am not a database expert  - and I did not take the advanced database classes in school. So - why I am I doing this?

## Beating myself on the head with a wooden stick

I believe in having the source available for all my tools.This is just a personal preference of mine ... I like to poke around to learn new stuff .. discover new ways  and combine projects in new ways .. but mostly I like to learn from the insights of others. See implementation tidbits buried deep down. My list of  projects to poke around in is long. Postgres is just one of the projects I'd like to poke around in. So - now I am going to poke around in postgres.  Let's see if we can compile it on window 7.  I'll just write down notes as I go along. Are you ready?   Bring forward your wooden stick!


<iframe width="420" height="315" src="http://www.youtube.com/embed/YgYEuJ5u1K0" frameborder="0" allowfullscreen></iframe>


## Checking out postgres on windows ##

So - the plan is to compile C/C++ code on windows. To do this you need a C/C++ compiler. I'll just take the easy route here on windows and download [Express 2012 for Windows Desktop](http://www.microsoft.com/visualstudio/eng/products/visual-studio-express-products) . Note that you need to register to do this. Downloading and installing Visual Studio Express can take a while.

Then you need [git](http://git-scm.com/ "Git") . If you have been living under a rock for the last decade, then git is a distributed version control system - popularized by the linux kernel and [github.com](http://github.com) . You can grab a windows installer on [git-scm.com](http://git-scm.com/download/win) . Go ahead and install it if you do not have it yet. You'll be glad you did.

After installing git you can clone the postgres code base like this:

{% highlight bash %}
mkdir build
cd build
git clone git://git.postgresl.org/git/postgresql.git
{% endhighlight %}


After a while then you should have the source code available . If you are like me ,then you'll probably hurry into \build\postgresql\src and notice win32.make. Maybe this will work?

{% highlight bash %}
nmake /f win32.mak
{% endhighlight %}

No luck! It fails with:
{% highlight bash %}
        link.exe -lib @C:\Users\Jacob\AppData\Local\Temp\nm3F8F.tmp
NMAKE : fatal error U1073: don't know how to make 'libpq-dist.rc'
Stop.
NMAKE : fatal error U1077: '"C:\Program Files (x86)\Microsoft Visual Studio 11.0\VC\BIN\nmake.EXE"' : return code '0x2'
Stop.
D:\Build\postgresql\src>
{% endhighlight  %}

Luckily there is \build\postgresql\src\tools\msvc\build.pl . 

Huh ?  What's *.pl files ? That's perl.  If you don't know what perl is , then you are in for a treat. Grab [active state perl](http://www.activestate.com/activeperl/downloads) and install it if you don't have it yet, so you will be able to process the file. 

Now. After installing perl, let's cross our fingers and type

{% highlight bash %}
perl build.pl
{% endhighlight %} 

No?? msbuild throws up with:

{% highlight bash %}

D:\Build\postgresql\src\tools\msvc>perl build.pl
Detected hardware platform: Win32
Microsoft (R) Build Engine version 4.0.30319.17929
[Microsoft .NET Framework, version 4.0.30319.18052]
Copyright (C) Microsoft Corporation. All rights reserved.

Building the projects in this solution one at a time. To enable parallel build,
please add the "/m" switch.
Build started 06-10-2013 17:58:55.
Project "D:\Build\postgresql\pgsql.sln" on node 1 (default targets).
Building with tools version "2.0".
Target "ValidateSolutionConfiguration" in file "D:\Build\postgresql\pgsql.sln.m
etaproj" from project "D:\Build\postgresql\pgsql.sln" (entry point):
Using "Error" task from assembly "Microsoft.Build.Tasks.v4.0, Version=4.0.0.0,
Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a".
Task "Error"
D:\Build\postgresql\pgsql.sln.metaproj : error MSB4126: The specified solution
configuration "Release|MCD" is invalid. Please specify a valid solution configu
ration using the Configuration and Platform properties (e.g. MSBuild.exe Soluti
on.sln /p:Configuration=Debug /p:Platform="Any CPU") or leave those properties
blank to use the default solution configuration. [D:\Build\postgresql\pgsql.sln
]
Done executing task "Error" -- FAILED.
Done building target "ValidateSolutionConfiguration" in project "pgsql.sln" --
FAILED.
Done Building Project "D:\Build\postgresql\pgsql.sln" (default targets) -- FAIL
ED.

Build FAILED.

{% endhighlight %}

Oh.you  probably spotted it also. "Detected hardware platform: win32". I ran this using the "Developer Command Prompt for VS2012" - maybe this targets win32 pr default? If I select "Microsoft Visual Studio 2012" > "Visual Studio Tools" > "VS2012 x64 Cross Tools Command Prompt" and execute "build" again - then it works!

After the compilation finished I typed:
{% highlight bash %}
mkdir c:\postgres
install c:\postgres
{% endhighlight %}

Now I can use postgres from c:\postgres ! 


# And now for something completely different

After finishing what I did above I throw out my custom compile and starting using the [postgres zip archive](http://www.postgresql.org/download/windows/)  again. I kept the code locally though. Right now I am poking around in the source code using "Run Source code analysis on solution". This gives me the lowdown on what Microsoft thinks could be improved in the code. Let's see an example:


{% highlight bash %}

C6001	Using uninitialized memory	Using uninitialized memory 'replace_val'.	libpgtypes	timestamp.c	845
'replace_val' is not initialized			388
Enter this loop, (assume '*p')			394
Enter this branch, (assume '*p==37')			396
Assume switch ( '*p' ) resolves to case 99: 			401
'replace_val' is an In/Out argument to 'pgtypes_fmt_replace' (declared at d:\build\postgresql\src\interfaces\ecpg\pgtypeslib\extern.h:37)			845
	'replace_val' is used, but may not have been initialized			845


{% endhighlight %}

Note that this is a random example. Right now I have a limited understanding of the postgresql codebase, so following the [hardening guidelines from OWASP](https://www.owasp.org/index.php/OWASP_Backend_Security_Project_PostgreSQL_Hardening) seems like a good idea. 



# But wait! There's more
I like what I see. Looks like there is an active community  [for developers here]( http://wiki.postgresql.org/wiki/Developer_and_Contributor_Resources) . And . oh. Here is the official ["Installation From Source on Windows"](http://www.postgresql.org/docs/9.0/static/install-windows.html) in the documentation. It looks solid. I'll go check that out now :P




 
