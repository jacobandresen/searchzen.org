---
layout: post
title: "Farvel til Windows Vista i 2008"
date: 2008-01-01 12:01
comments: true 
categories: 
---
Jeg har benyttet indgangen til 2008 til at deinstallere windows Vista som primært operativsystem på min hjemmepc . Planen er nu at jeg vil køre ubuntu linux som level 2 hypervisor (  se evt <a href="http://en.wikipedia.org/wiki/Hypervisor">http://en.wikipedia.org/wiki/Hypervisor</a> )

Mit første skridt var at hente vmware converter her

<a href="http://www.vmware.com/products/converter/">http://www.vmware.com/products/converter/</a>

for dernæst at lave en virtuel maskine ud af min eksisterende windows vista maskine. Det var en lidt sær fornemmelse at lave en virtuel maskine på en kørende maskine (vmware converter brokkede sig også lidt)  - men det virkede. Jeg huskede her at opsplitte disk images i filer af 2gb så de kunne være på min eksterne harddisk , der var formatteret i FAT32 . Bemærk her at jeg ikke kunne opsplitte til 2gb filer når jeg skrev direkte til den eksterne harddisk vha gratisudgaven af vmware converter, men jeg godt kunne når jeg skrev til disken inde i maskinen . Det må være en af salgsargumenterne for købeudgaven - da det tog en del ekstra tid først at skrive den nye virtuelle maskine til den interne disk på den maskine jeg klonede - for derefter at kopiere den ud til den eksterne harddisk.

Mit næste skridt var at hente ubuntu linux herfra : <a href="http://www.ubuntu.com/getubuntu/download">http://www.ubuntu.com/getubuntu/download</a>

installeringsmetoden for ubuntu er simpelthen genial! Jeg stak cd'en ind - og straks var der et kørende live system. Alle mine drivere virkede out-of-the-box . Installationsskridtene tog mig mindre end 10 minutter.

Min plan er nu at køre følgende i 2008:
<ul>
	<li>ubuntu server - hypervisor, apache , oracle 10ias (512 mb)</li>
	<li>ubuntu klient - udviklingsboks til J2EE (1024 mb)</li>
	<li>Windows Vista - Demomaskine (1024)</li>
	<li>Windows XP - Visual dataFlex (1024)</li>
	<li>Windows XP - gaming box (1024 mb)</li>
</ul>
Og ja! jeg har faktisk så mange windows licenser liggende rundt omkring.
Fordelen ved denne tilgang er at de udviklingsting jeg kører nu kan adskilles fra serverprocesserne og de spil jeg har installeret. Jeg ser meget frem til at skulle undgå at ominstallere programmer i 2008!

<strong>Opdatering 2008-01-21:</strong>

Jeg har nu været igennem et par uger med dette setup. Det har vist sig at det ikke er praktisk at køre med mere end 2 virtuelle maskiner ad gangen med min maskine (2 cpu'er med 2 gigabyte ram) - Heldigvis har det så vist sig at der er et fungerende udviklingsmiljø for java i ubuntu at jeg har vurderet at default opsætning af eclipse og tomcat5.5  fungerer for mine behov.  Dvs at jeg nu kører følgende:
<ul>
	<li> ubuntu 7.10 ( J2EE udvikling - oracle 10 , tomcat5.5 , eclipse, vmware klient)</li>
	<li> Windows XP Home edition (Visual DataFlex  512 mb)</li>
	<li>Windows Vista Business Edition (Demo maskine 1024 mb)</li>
</ul>
Det har ikke fungeret med at spille spil på vmware - så nu har jeg en gammel pc der kører windows XP tilkoblet ved siden af min arbejdsstation.