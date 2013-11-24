---
layout: post
title: "brug af datastores og data-views i extjs"
date: 2008-04-01 09:04
comments: true 
categories: 
---
Jeg har kigget lidt på <a title="extjs" href="http://extjs.com">extjs</a> javascript bibliotekerne og kan lide hvad jeg har set indtil videre. En af de gode ting ved extjs er konceptet med datastores  som kan benyttes som datagrundlag for et<a title="grid" href="http://extjs.com/deploy/dev/examples/grid/array-grid.html"> grid</a>

Designet tillader at man benytte forskellig datastores afhængigt af hvilken  underliggende transportform man bruger fra serveren. En default <a title="Ext datastore" href="http://extjs.com/deploy/ext/docs/output/Ext.data.Store.html">Ext.data.Store</a> bruger xml til at udveksle data, mens en <a title="JsonStore" href="http://extjs.com/deploy/ext-1.1.1/docs/output/Ext.data.JsonStore.html">Ext.data.JsonStore</a> bruger json til at udveksle data . Dette design muliggør at man kan benytte f.eks grids eller dataviews uafhængigt af transportformatet. Meninen er så at man skifter datastore hvis man skifter dataformat - og bibeholder den kode man har skrivet til sit grid.

Jeg har pillet lidt ved et af eksemplerne fra ext-js distroen her:
<iframe src="http://pedant.dk/hacks/20080401/data-view.html"></iframe>

Eksemplet er oprindeligt fra her : <a href="http://extjs.com/deploy/dev/examples/view/data-view.html">http://extjs.com/deploy/dev/examples/view/data-view.html</a>

Det ser iøvrigt ud til at der iøjeblikket ( 2008-04-01) er noget specielt med lokale links i mit nye extjs tema på min blog. Det må jeg lige kigge lidt nærmere på (det ser ud til at lokale links ikke åbner fra sider inde wordpress med det nye extjs tema).

<strong>opdatering 2008-04-13</strong>: Jeg har nu valgt at disable det extjs tema, der skabte problemerne. Det burde nu være muligt at kunne klikke på interne links igen