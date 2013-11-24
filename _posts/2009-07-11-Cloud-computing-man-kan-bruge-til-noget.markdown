---
layout: post
title: "Cloud computing man kan bruge til noget"
date: 2009-07-11 12:07
comments: true 
categories: 
---
Jeg har tidligere kigget på brugen af <a href="http://vmware.com">vmware</a> ifm test og udvikling. Jeg har fundet ud af det det kan være fordelagtigt at opbevare udviklingsmiljøer og databaseopsætninger på virtuelle maskiner - det hjælper typisk med at min hoved-udviklingsmaskine ikke bliver 'møget' til af diverse projekter jeg kigger på i løbet af ugen.  Jeg har også kigget på <a href="http://code.google.com/intl/da/appengine/docs/java/overview.htmlhttp://">Google App Engine for java </a>- det er godt med nogle fasttømrede api'er der er klargjort til af fungere på en større gruppe af maskiner på en gang - så performance og skalerbarhed har været der fra starten ( Jeg hører også gode ting om Amazon EC2)

Det har dog bæret sådan at det bliver lidt bøvlet at vedligeholde diverse images rundt omkring - og Google App Engine for java stiller væsentlige begrænsninger på hvordan man kan skrive SQL - og det kan blive vanskeligt at få benyttet GIS operatorer på GAE (Bemærk at jeg slet ikke har prøvet microsofts <a href="http://www.microsoft.com/azure/default.mspx">nye Azure platform</a>)

<a href="http://oddthesis.org">Bob McWhirter </a>kører iøjeblikket et projekt for jboss , hvor han iøjeblikket eksperimenterer med <a href="http://reductivelabs.com/trac/puppet">puppet </a> til at administrere virtuelle maskiner. Jboss håndterer udviklingen under projektet <a href="http://github.com/bobmcwhirter/jboss-cloud/tree/master">jboss cloud</a> . Ideen er at man kan benytte "metaappliance" til at generere de øvrige "appliances".  <a href="http://github.com/bobmcwhirter/jboss-cloud/tree/master">Jboss understøttede clustering allerede fra version 4</a> - det nye i eksperimentet er nu maskin-håndteringen, hvor deployment-platformene inkluderer <a href="http://aws.amazon.com/ec2/"> ec2</a>, <a href="http://www.vmware.com/products/server/">vmware</a>, <a href="http://www.linux-kvm.org/page/Main_Page">kvm</a> .

Jeg håber at kunne bruge jboss-cloud projektet til at håndtere mine udviklingsservere på en mere fornuftig vis :)