---
layout: post
title: "Hardcore forking action (git for begyndere)"
date: 2009-01-02 08:01
comments: true 
categories: 
---
Efter at have været belemret med <a href="http://git.or.cz/">git</a> i et stykke tid nu (ifbm at have kigget på <a title="prototype js" href="http://github.com/sstephenson/prototype/tree/master">prototype js</a> ) så har jeg bandet og svovlet over at skulle lære endnu et kildekode-håndteringssystem. Vi har jo allerede <a title="cvs" href="http://www.nongnu.org/cvs/">cvs </a>, <a title="svn" href="http://subversion.tigris.org/">svn</a> , <a title="darcs" href="http://darcs.net/">darcs</a> , <a title="perforce" href="http://www.perforce.com/">perforce</a> ( eller den gode gamle kending - et zipdrev  og et værktøj til at sammenligne biblioteker!)  - så hvorfor skulle man bruge git? Egentligt ved jeg det jo godt - hvis jeg skulle drive et opensource projekt, så ville jeg helst undgå at spilde tid på at diskutere hvem der skulle have "commit" access eller ej  - og hvem der er med i "kerne"-gruppen . Det kan man undgå med et distribueret system til håndtering af kildekode såsom Git.  Git har iflg Linus Torvalds  flg. fordele
<ul>
	<li> Det er distribueret</li>
	<li>Det har en god ydeevne (det skalerer godt)</li>
	<li>Indhold kommer ud på præcis samme facon som det kom ind</li>
</ul>
Torvarlds gav flg præsentation hos google for et par år siden:

<object width="425" height="350" data="http://www.youtube.com/v/4XpnKHJAok8" type="application/x-shockwave-flash"><param name="src" value="http://www.youtube.com/v/4XpnKHJAok8" /></object>

Indrømmet  - jeg har da også kigget på git i 2007 - men der jeg fandt det unødigt svært at overskue.  I 2008 ændrede situationen sig idet  <a href="http://github.com">http://github.com</a> kom på banen. Github er et websted der kan benyttes til håndtere git repositories vha en grafisk grænseflade . Jeg er specielt imponeret over hvor nemt det er at lave "fork" af et repository og dernæst overskue dets "fork queue" ( det er virkeligt en lækker oplevelse - sammenlignet med de ubehageligheder jeg har haft igennem årene med cvs og branches).

På linux er installationen af git ekstremt simpel (sudo apt-get install git)  - mens du på windows har muligheden for at installere git vha brug af "cygwin" og "msys"    - der er en udførlig beskrivelse af hvordan du benytter git og github her : <a href="http://kylecordes.com/2008/04/30/git-windows-go/">http://kylecordes.com/2008/04/30/git-windows-go/</a> . Du kan også vælge en noget kortere udgave her :<a href="http://github.com/guides/using-git-and-github-for-the-windows-for-newbies"> http://github.com/guides/using-git-and-github-for-the-windows-for-newbies</a> .

Jeg har lige pushet <a title="yas" href="http://github.com/jacobandresen/yase/tree/master"> Yase (Yet another Search Engine)</a> til github.com  -  alle skulle nu kunne lave et fork og sende et pull request til mig  ;)