---
layout: post
title: "om autoriteter i brugerskabt indhold"
date: 2009-02-14 04:02
comments: true 
categories: 
---
Den bedste internet søgemaskine på markedet idag er baseret på begreberne 'hubs' og 'authorities'. En 'authority' opfattes som en side der er central i et netværk for et givent emne og opfattes af netværket som centralt for emnet. En 'hub' er et knudepunkt i netværket der indeholder mange henvisninger til øvrige steder.

Efterhånden som flere og flere steder på internettet tillader brugerskabt indhold så mener jeg at vi må ændre på beregning af autoritet vha af henvisninger i et netværk. F.eks på 'blogs' så indeholder kommentarer typisk en henvisning tilbage til hjemmesiden til ham eller hende der har skrevet kommentaren, derved vender vi op og ned på hvad en 'hub' og en 'authority' er - idet linket nu går den anden vej i kommentaren.

<strong>Den traditionelle 'hubs' and 'authorities' model
</strong>
Hvis vi i den traditionelle situation betragter et endeligt antal websider uden brugerskabt indhold i et sæt {1,2, ... ,n} så kan vi opstille en matrice <strong>B</strong> med links i mellem de forskellige websider hvor 1 markerer at der link mens 0 markerer intet link - indgang (i,j) i B markerer så at der er et link fra i til j.

Hvis vi så yderligere betragter 'hubs'  som <img title="inline h=&lt;h_1,h_2, .., h_n&gt;" src="http://latex.codecogs.com/gif.latex? h=&lt;h_1,h_2, .., h_n&gt;" alt="" /> og authorities <img src="http://latex.codecogs.com/gif.latex?%5Cinline%20a=%3Ca_1,a_2,..,a_n%3E" alt="" />

Så kan vi beregnene vægtene i netværket således :

<img title="inline h=Bcdot a" src="http://latex.codecogs.com/gif.latex? h=Bcdot a" alt="" /> og      <img title="inline a=B^{T}cdot h" src="http://latex.codecogs.com/gif.latex?a=B^{T}cdot h" alt="" />

Hvis vi itererer en gang så når vi

<img title=" h = left( BB^{T} righ) a" src="http://latex.codecogs.com/gif.latex? h = left( BB^{T} right) a" alt="" /> og   <img title="a=left( B^{T}Bh right)h" src="http://latex.codecogs.com/gif.latex? a=left( B^{T}Bh right)h" alt="" />

næste iteration giver

<img title="inline h = left( B B^{T} right)^2a" src="http://latex.codecogs.com/gif.latex?h = left( B B^{T} right)^2a" alt="" /> og <img title="inline a = left ( B^{T} B right)^2 a" src="http://latex.codecogs.com/gif.latex? a = left ( B^{T} B right)^2 a" alt="" />

Den matematisk kyndige læser vil her indse at at resultaterne vil konvergere imod de principielle egenvektorer for <a href="http://www.codecogs.com/eqnedit.php?latex=inline left( B B^{T} right)" target="_blank"><img title=" left( B B^{T} right)" src="http://latex.codecogs.com/gif.latex? left( B B^{T} right)" alt="" /></a> og <a href="http://www.codecogs.com/eqnedit.php?latex=inline B^{T}B" target="_blank"><img title="B^{T}B" src="http://latex.codecogs.com/gif.latex?B^{T}B" alt="" /></a>

Rent intuitivt ses det at samlingen af autoritetsvægte for siderne i netværket udtrykker at en gennemsøgning i netværket vil have større sandsynlighed for at ende på en side hvor vægten er større end på en side hvor vægten er lille.

Google har benyttet princippet til at opstille deres <a href="http://infolab.stanford.edu/~backrub/google.html">PageRank </a>

<a href="http://www.codecogs.com/eqnedit.php?latex=inline PR(A)=(1-d) @plus; d(PR(T_1)/C/T_1) @plus; ... @plus; PR(T_n)/C(T_n))" target="_blank"><img title="inline PR(A)=(1-d) + d(PR(T_1)/C(T_1)) + ... + PR(T_n)/C(T_n))" src="http://latex.codecogs.com/gif.latex?PR(A)=(1-d) + d(PR(T_1)/C(T_1)) + ... + PR(T_n)/C(T_n))" alt="" /></a>

Hvor <a href="http://www.codecogs.com/eqnedit.php?latex= C(T_i)" target="_blank"><img title=" C(T_i)" src="http://latex.codecogs.com/gif.latex? C(T_i)" alt="" /></a> er antallet af links ud fra side <a href="http://www.codecogs.com/eqnedit.php?latex=inline T_i" target="_blank"><img title="inline T_i" src="http://latex.codecogs.com/gif.latex? T_i" alt="" /></a> og d er valgt til 0.85.

<strong>Min mulige ændring af beregning af autoriteter </strong>

Når vi betragter modeller hvor "autoritet" tages som et udtryk for at en læser vil have høj sandsynlighed for at opleve en henvisning fra side A til side B som autoritet, så vil et brugerskabt links fra A til B have mulighed for at vende situationen om. Et kendt eksempel er ved brugen af blogs, hvor en hyppig bruger af mange blogs vil opnå mange indgående links (Man kunne kalde det en 'invers hub'). Brugen af henvisninger i brugerskabt indhold går nu fra at være en måde at udtrykke mening om relevans inden for et emne til at udtrykke interesse for et emne.

Det er så her at jeg tænker på om man kan finde de typiske steder hvor brugeren af blogs skriver på og foretage tilpasninger af link-beregningen der. Lad os antage at vi kunne finde en passende måde at beregne om der er tale om lille koncentreret klynge af websteder der henviser til hinanden . Efter at have opnået listen af sider kunne vi ændre på den vægt der tilføjes pr iteration ved betragtninger over linkafstanden til klyngecenteret. Altså at hvis vi betrager et websted , der er inde i den lille klynge, så har et link ikke så stor betydning som hvis det optrådte udenfor.