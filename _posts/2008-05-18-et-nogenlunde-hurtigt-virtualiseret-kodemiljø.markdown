---
layout: post
title: "et nogenlunde hurtigt virtualiseret kodemiljø"
date: 2008-05-18 10:05
comments: true 
categories: 
---
Jeg har <a href="http://www.pedant.dk/2008/01/31/et-pragmatisk-milj%c3%b8-til-at-kode-j2ee-i/">tidligere</a> skrevet om min oplevelser med at kode J2EE på linux. Siden da har jeg fået lidt flere erfaringer med brugen af vmware og har gjort mig flg. observationer:
<ul>
	<li>Det er skidt at flytte datasæt "ind" i et vmware image. Så er det nemmere at lave filshares samt databaser på hostmaskinen .</li>
	<li>Kontorprogrammer samt gængse applikationer er bedre placeret på hostmaskinen end i det vmware image der programmeres i.</li>
	<li>wmare kræver ikke så meget RAM for at køre. Jo mindre RAM der tildeles det enkelte image - jo hurtigere går det med at åbne og lukke det.</li>
	<li>Kode er  placeret bedst i versionskontrol på en anden server. Ideelt set så kan det brugte image rulles tilbage til start efter endt brug.</li>
</ul>
Jeg kører nu med 256 mb tildelt mit windows image og har flyttet kontorprogrammer ud fra windows. Dvs at jeg nu kører alle andre programmer end de windows-specikke fra linux.
En af de umiddelbare fordele der er kommet ud af at samle min arbejdsfiler på et enkelt share er at mine backupfiler er faldet drastisk i størrelse.