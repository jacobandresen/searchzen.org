---
layout: post
title: "ding på github - mine første 20 minutter"
date: 2009-06-27 09:06
comments: true 
categories: 
---
Jeg fald lige over <a title="ding" href="http://github.com/kdb/ding/tree/master">http://github.com/kdb/ding/tree/master</a> på github, hvor Københavns biblioteker er igang med at kode en <a title="drupal" href="http://drupal.org/">drupal </a>baseret frontend til <a href="http://gnit.dk">ting</a> projektet. Nu er jeg jo ikke lige en haj til drupal og php , så jeg startede med at nøjes med at kigge på en klient <a title="klienten til php5" href="http://github.com/kdb/ting-dbc-php5-client/tree/master">til php5</a>. Den var også enormt kompliceret , så jeg skøjtede videre til <a href="http://didicas.dbc.dk/opensearch/opensearch.wsdl">http://didicas.dbc.dk/opensearch/opensearch.wsdl</a> og prøvede at lave en php5 webservice klient vha <a href="http://sourceforge.net/projects/nusoap/">nusoap. </a>

Den virkede ikke lige, så prøvede jeg istedet at skrive "wsdl http://didicas.dbc.dk/opensearch/opensearch.wsdl" på kommandolinjen (her var det heldigt at jeg havde installeret <a title="windows sdk'et" href="http://msdn.microsoft.com/en-us/windows/bb980924.aspx">Windows SDK'et</a> ) . Den kommando lavede filen tingService.cs til mig .

Jeg så straks at designeren af skemaet kan lide <a href="http://en.wikipedia.org/wiki/CamelCase">lower camelcase </a>- det undrede mig dog at typerne resulterer i små begyndelsesbogstaver for mine klasser.

Ved at kigge lidt i tingService.cs så jeg hvilke parametre man skulle bruge . Jeg ved ikke lige hvad formatType og sortType skal bruges til ,så jeg lavede bare en default constructor på den. Det førte til flg kode:

<code lang="c#">
using System;

public class test {
 public static void Main(){

 tingService t=new tingService();
 searchResult sr = t.search("test", "", null, new formatType(), true, 1, true, 5, true, new sortType(), true);
 Console.Write(sr.hitCount);
 //Console.Write(sr.records[0].relations[0]);
 }
}
</code>


jeg kompilerede koden med "csc test.cs tingService.cs" og fik umiddelbart en køretidsfejl. .NET frameworket rapporterede om en Ikke-afviklet undtagelse ifm en HTTP fejl 301  hvor det blev meddelt at endepunktet var flyttet til http://didicas.dbc.dk/opensearch/

Efter at have tilføjet et "/" til endepunktet for servicen i tingService.cs , så kunne jeg se at der er "1320" svar på søgningen "test" .

Jeg kan se at resultaterne bliver afleveret i en struktur kaldet "tingRecord" i det returnerede searchResult, men jeg kan ikke umiddelbart overskue hvordan man hiver resultaterne ud derfra.  Jeg vil prøve at følge lidt med i projektet og kigge lidt nærmere på wsdl filen ved lejlighed :)