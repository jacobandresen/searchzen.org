---
layout: post
title: "udskriving af oracle.xml.parser.v2.XMLDocument"
date: 2007-10-16 12:10
comments: true 
categories: 
---
I kampens hede, når man er igang med at kode mod oracle 10ias og ved at hive information ud af et xml dokument, så kan man jo blive paranoid og begynde ikke at stole på sin debugger. Så kunne man jo få lyst til at udskrive indholdet af den indkommende strøm for at kigge på den i sin log.

Sådan gør man det:

InputStream in = request.getInputStream();
DOMParser xmlParser = new DOMParser();
XMLDocument req = null;
xmlParser.parse(in);
req = xmlParser.getDocument();

req.print(System.out);

Bemærk det sidste "req.print(System.out)"  - den glemmer jeg selv altid. Tricket er at man kan skrive dokumentet ud til en printstream.