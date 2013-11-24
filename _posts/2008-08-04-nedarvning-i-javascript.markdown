---
layout: post
title: "nedarvning i javascript"
date: 2008-08-04 09:08
comments: true 
categories: 
---
Jeg har fornyligt genopfrisket hvordan man laver nedarvning i javascript .  Det centrale i forståelsen af nedarvning i javascript er forståelsen at javascript er et <a href="http://www.javascriptkit.com/javatutors/proto.shtml">prototype</a> -baseret sprog og ikke et klassebaseret sprog.  Her er et eksempel , der gerne skulle lave en alert-box med "I am a pig":

<code lang="javascript">
function animal ()  {
  this.name = "nothing yet";
  this.legs=4;
};
tiger = new animal;
tiger.name="tiger";
pig = new animal;
pig.name="pig";

animal.prototype.classify = function (){
  alert( ' I am a ' + this.name );
};
pig.classify();
</code>

Bemærk brugen af prototype her, der tilføjer en ny funktion classify, der benytter den allerede eksisterende værdi "name".

Du kan også bruge klasser vha <a href="http://prototypejs.org" title="prototypejs">prototypejs</a> som  beskrevet <a href="http://www.hinnerup.net/2008/04/11/javascript_classes/" title="javascript klasser">her</a> (Så skal du dog benytte prototype js biblioteket)