---
layout: post
title: "klargøring af tekst fra dokumentfiler vha ifilters"
date: 2007-11-11 04:11
comments: true 
categories: 
---
En stor del af infrastrukturen for at opstille en søgemaskine er at kunne hente tekst fra de dokumenter man ønsker at kunne søge i.

Microsoft stiller flere værktøjer til rådighed ifbm søgning - heraf kan flg. nævnes:
<ul>
	<li>Windows Desktop Search</li>
	<li>Indexing Server</li>
	<li>Sharepoint Portal</li>
</ul>
Disse værktøjer benytter alle teknologien "ifilter" (<a href="http://www.ifilter.org/Links.htm" title="ifilter"> http://www.ifilter.org</a> ) der opstiller et centralt interface der benyttes til udtrække tekst og information fra forskellige dokumenttyper ,  der implementerer dette interface. Hvis du kigger på <a href="http://www.ifilter.org/Links.htm" title="ifilter"> http://www.ifilter.org</a>  så kan du finde en liste af understøttede dokumenttyper.

Ifilter teknologien er central for at kunne klargøre tekst fra dokumentfiler på windows-platformen og er tilgængelig fra Windows  sdk'et ( se mere her :<a href="http://en.wikipedia.org/wiki/Microsoft_Windows_SDK" title="windows sdk" target="_blank"> http://en.wikipedia.org/wiki/Microsoft_Windows_SDK</a>  )

SDK'et stiller   applikationerne \bin\filtdump.exe og \bin\filtreg.exe til rådighed.

filreg.exe giver dig en oversigt over hvilke ifilters der er registreret på dit  system.  Hvis du kører denne applikation fra kommandolinjen , kan du få en oversigt over registrerede filtre. På mit system er .pdf filer understøttet vha "Adobe Acrobat Reader 8.0" .

filtdump.exe kan udtrække tekst fra et dokument  der har et registreret ifilter. Jeg kan eksempelvis køre

filtdump.exe -b blei03a.pdf

og få teksten fra pdf-filen

Der er et eksempel på hvordan du kan kode dit eget ifilter i \Samples\WinBase\Indexing\IFilter .