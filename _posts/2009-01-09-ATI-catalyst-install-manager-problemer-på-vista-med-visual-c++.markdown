---
layout: post
title: "ATI catalyst install manager problemer på vista med visual c++"
date: 2009-01-09 10:01
comments: true 
categories: 
---
Jeg kører nu windows vista på min stationære computer derhjemme igen . Performance på vista er blevet lidt bedre i løbet af 2008 - og det er lykkedes mig at finde veje veje uden om de fleste codec problemer jeg har oplevede i 2007.  Mit windows xp arbejdsimage kører iøjeblikket på min ubuntu-labtop og vil blive flyttet over til min stationære maskine.

Ifbm med at køre vista igen så har jeg oplevet problemer med at skulle installere ATI catalyst driverne  - her nægtede ATI catalyst install manager konsekvent at starte.

Efter at kigget lidt i ATI installer folderen bemærkede jeg flg. filer :
<ul>
	<li>msvp80.dll</li>
	<li>msvcr80.dll</li>
</ul>
Dernæst kiggede jeg på stien for ATI's CCC :  c:\Program Files\ATI Technologies\ATI.ACE\Core.Static

Dette kunne tyde på uklarheder om hvordan lækningen til c++ runtimen er foretaget. Her indså jeg så at jeg havde "Microsoft Visual C++ 2008 express edition" og "Visual c++ 2005" runtimen installeret og tilgængelig vha kommandolinjen. Da jeg ikke har brug for en microsoft specifik kompiler længere ( der er andre c++ kompilere til rådighed , eks.  g++ vha <a href="http://www.mingw.org/">http://www.mingw.org/ </a>) så valgte jeg at deinstallere Visual C++ 2008 og visual c++ 2005 runtimen på vista. Et mindre drastisk valg kunne selfølgeligt være at sørge for at der ikke er overlap mellem de forskellige dll'er  - men det mener jeg nu er ATI's problem. Mit valg virker for mig iøjeblikket da jeg ikke har brug for Visual c++  lige nu.

Hvis du kender til en bedre løsning , så skriv evt en kommentar her. Jeg kan forestille mig at der kan være lignende issues med lænkning, hvis visual c++ runtimen er tilgængelig fra andre programmer end Visual Studio, men jeg har ikke lige gennemsøgt ATI's forum for fejlbeskrivelser .

Efter at have fået mit ATI Radeon 2400 xt kort til at køre grafikken pænt over mine 2 skærme, så gik jeg videre til få lyden til at få  HD Audio til at fungere sammen med kortet. Først eksperimenterede jeg med at slå onboard audio fra i bios  (jeg har et integreret lydkort i bundkortet på min stationære maskine). Dette virkede ikke umiddelbart  (det ser ud som at listning af devices ikke umiddelbart blev opdateret ved genstart af vista) så jeg valgte at slå onboard audio til igen. Derefter gættede jeg og prøvede at fjerne HD audio driveren - her "opdagede" vista så at driveren var der og tilkoblede den. Så virkede min lyd igen.

Det virker iøvrigt som at det ikke længere er helt umuligt at lave fejlsøgning på Vista  og performance virker nu kun lidt ringere end på xp. Mit bud er at Microsoft har foretaget en del performanceforbedringer i Vista servicepack 1.

<strong>Opdatering 2009-01-11</strong>: Jeg har nu geninstalleret Visual C++ 2008 igen (ifbm med at kompilere<a href="http://code.google.com/p/tortoisegit/"> tortoise-git</a> ). Både ATI catalyst install manager og visual c++ 2008 express edition kører.  Mon det var visual c++ 2005 runtimen der skabte fejlen?