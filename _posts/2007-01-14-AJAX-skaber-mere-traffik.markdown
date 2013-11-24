---
layout: post
title: "AJAX skaber mere traffik"
date: 2007-01-14 03:01
comments: true 
categories: 
---
<span class="small"></span>
<strong>Problemet med at lave en asynkron http flerbruger chat på en standard host </strong>

Nå. Det ser ud til at b-one ikke kan lide den ekstra traffik , som brugen af min AJAX chat har genereret på citypolarna.se . Det får mig til at tænke på hvordan man egentligt kan lave ajax løsninger , der skalerer fornuftigt på normale http servere. Det kan jo være både godt at dårligt at der er kommet mere traffik på serveren (men det skulle helst ikke være min implementation, der er skyld i det).

<strong>Lidt piveri over manglende sessionshåndtering i http protokollen</strong>

Som vi alle ved, så er http protokollen tilstandsløs. Dette vanskeliggør at lave 'push update' til en specifik web klient , der kører for en specifik bruger. Det er også vanskeligt at 'skubbe' alle nye beskeder ud til alle browsere - uden at lave en speciel løsning på en anden måde.

<strong>En dyr måde at kode en  flerbruger chat</strong>

vi kunne kigge på at sammenkoble sessions-information håndteret eksempelvis af php eller asp sammen med en speciel server proces, der fastholder kontakten til klienterne. Klienten kunne så komunikere med denne serverproces vha. sockets. (Dette ville så inkludere at bruge java eller flash på klientsiden)

<strong>En billigere måde at lave den på</strong>

Man kunne også på serversiden holde styr hvad der blev sendt til den pågældende klient sidste gang, for derefter kun at sende de seneste opdateringer. Problemet med denne tilgang er at dette ville kræve en fornuftige måde at opdatere tabeller i alle browsere på. Det ved jeg ikke lige hvordan man gør endu.

<strong>opdatering 2007-11-20: Jeg er nu blevet gjort opmærksom på webstedet <a href="http://cometdaily.com/">http://www.cometdaily.com</a> , hvor man kan læse mere om problemstillingen. </strong>