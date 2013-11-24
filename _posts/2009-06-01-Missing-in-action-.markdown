---
layout: post
title: "Missing in action !"
date: 2009-06-01 08:06
comments: true 
categories: 
---
Jeg har igennem årene set forskellige måder hvordan man kan få data ind og ud af en database i forskellige sprog.   problemet beskrives som ORB  - Object Relational Mapping  - hvordan man kan få data i relationelle databaser til at fungere nemmest sammen med et objektorienteret sprog.

her i midten af 2009 er der følgende state of the art løsninger:
<ul>
	<li><a href="http://msdn.microsoft.com/en-us/netframework/aa904594.aspx ">http://msdn.microsoft.com/en-us/netframework/aa904594.aspx </a>(funktionsprogrammering  og sql-lignende udvidelser til C#)</li>
	<li><a href="http://www.grails.org/GORM ">http://www.grails.org/GORM </a>(rails inspireret groovy løsning)</li>
	<li><a href="http://ar.rubyonrails.org/">http://ar.rubyonrails.org/</a> (kernen af Ruby on rails )</li>
	<li><a href="http://www.datanucleus.org/">http://www.datanucleus.org/</a> (opensource jpa implementation brugt i google app engine)</li>
	<li><a href="http://www.doctrine-project.org/">http://www.doctrine-project.org/</a> (for php )</li>
	<li><a href="http://www.visualdataflex.com">http://www.visualdataflex.com</a> (DataFlex løste problemet i midt-firserne!)</li>
</ul>
Den løsning der er blevet valgt i de projekter jeg har været i nærheden af har typisk været afhængig af hvilke erfaringer medlemmerne nu har haft.

Her forleden sad jeg og så  <a href="http://www.imdb.com/title/tt0087727/">Missing in action</a> og kom til at tænke på at starten af relationelle databaser var omkring Vietnam krigen  ( <a href="http://en.wikipedia.org/wiki/IBM_System_R"> IBM lavede System R i 70'erne </a> ).    Når vi tænker på at objekterede sprog også har eksisteret siden 70'erne , så er det  lidt underligt at det ikke er helt oplagt hvordan man løser ORM problemet endnu.

Ted Neward  har beskrevet ORM problemet som  <a href="http://www.odbms.org/download/031.01%20Neward%20The%20Vietnam%20of%20Computer%20Science%20June%202006.PDF"> The Vietnam of Computer science </a> . Vietnamkrigen  er ofte blevet beskrevet som en krig som USA aldrig kunne have vundet.

Jeg har kendskab til flere projekter der stadigvæk kæmper med at løse ORM problemet - de må betragtes som værende "Missing in Action". Kan vi ikke sende Chuck Norris ind for at redde dem ? :P