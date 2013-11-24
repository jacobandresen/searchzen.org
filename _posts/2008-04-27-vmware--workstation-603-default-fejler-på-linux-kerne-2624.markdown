---
layout: post
title: "vmware  workstation 6.0.3 default fejler på linux kerne 2.6.24"
date: 2008-04-27 04:04
comments: true 
categories: 
---
Jeg har for nyligt opgraderet til <a href="https://wiki.ubuntu.com/HardyHeron/RC">Ubuntu 8.04 . </a>

Efter at have opgraderet ubuntu, så oplevede jeg at vmware-config.pl ikke opgraderede min kernemoduler for vmware som vanligt. Dette skyldes øjensynligt at der er blevet flyttet rundt på nogle headere i kerne 2.6.24 som ubuntu 8.04 kører med.

Efter at have kigge lidt rundt på nettet fandt jeg <a href="http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel">følgende løsning  </a>, der involverer brugen af "any-any" patchet for vmware . Jeg har selv valgt denne løsning selvom at den ikke er officielt supporteret af vmware ( jeg har kun gjort dette ifbm med min hjemmeserver, der ikke kører kritiske ting).