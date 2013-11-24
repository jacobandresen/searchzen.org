---
layout: post
title: "behandling af ekstreme datasæt vha shellscripting og fuse-zip"
date: 2008-10-06 09:10
comments: true 
categories: 
---
Hvis du er stødt på et datasæt, der er større end du er vant til  så kan det være vanskeligt umiddelbart at importere data ind i excel så du bare kan kigge på dem.

I denne situation kan det være brugbart at manipulere lidt med dem først  enten i form at spillet datasættene op i mindre bidder så det kan lade sig gøre , eller også at opstille et komprimeret filsystem, som gør at afviklingen af dine shellscripts kan foretages mens data er på komprimeret form.

Lad os betragte et tilfælde hvor  vi skal foretage  et crawl af internettet , der skal benyttes til beregning af linkmatricer.

Hvis vi eksempelvis  igangsætter flg. kommando:

<code lang="bash">
wget --random-wait --no-dns-cache --recursive --level=20 http://slashdot.org
</code>

Så  vil vi henover tid producere så meget data at det vil en optage en stor del af disken.

I en linkanalyse kan det være unødigvendigt at betragte hele datasættet ( i vores tilfælde skal vi kun kigge inærheden af hvor der står HREF eller MAILTO ). Derfor vil der være spildtid i at holde hele datasættet i lageret i ukomprimeret form.

Her er fuse-zip brugbart. fuse-zip kan benyttes til at gennemse dele af en zipfil monteret som et drev .

fuse-zip kræver at man installerer lib-fuse først. Dette gøres således  (eksemplet er her for ubuntu):

<code lang="bash">
sudo apt-get install  libfuse-dev
mkdir -p ~/tmp
cd ~/tmp
wget fuse-zip.googlecode.com/files/fuse-zip-0.2.6.tar.gz
tar zxvf fuse-zip-0.2.6.tar.gz
cd fuse-zip-0.2.6/
sudo make install
</code>

Du får nu kommandoen "fuse-zip" tilrådighed.

Nu kan du eksempelvis vælge at gøre flg:

<code lang="bash">
cd ~/tmp
mkdir a
zip -r a.zip a
mkdir afuse
</code>

og så montere a.zip som et nyt filsystem på flg. facon:

<code lang="bash">
fuse-zip  a.zip afuse
</code>

Du kan nu gentage crawl kommandoen og se at den ikke får den samme pladsbelastning på din disk.
Bemærk at du skal afmontere dit nye fuse-zip drev før at du kan overføre zip filen til et andets ted. Dette kan du gøre på flg. facon:

<code lang="bash">
cd ~/tmp/
sudo umount afuse
</code>

Du kan jo også vælge at montere en zip-fil som du har modtaget fra et datasæt. Husk at navngive monteringspunkterne så du kan holde styr på hvilket monteringspunkt der hører til hvilken zip-fil.

Når du nu har monteret dit crawl som en zip-fil, så behøver du ikke have den i ukomprimeret form længere for at kunne benytte de shell kommandoer du kender i forvejen.

For vores linkanalyse kunne det være relevant at starte med at kigge på hvor mange gange der står HREF  på slashdot.org siderne:

<code lang="bash">
grep --recursive -c href *
</code>

Ved at forbedre lidt på de regulære udtryk kunne man optælle links i de forskellige filer . Dernæst kunne man analysere links imellem filer. Altsammen vha shellscripting i en zip-komprimeret fil(!)