---
layout: post
title: "hvordan man omgår 'this' scope problemer for closures"
date: 2008-08-07 02:08
comments: true 
categories: 
---
<p>Man kan ikke uden videre bruge 'this'  i en indre anonym funktion der bruger information fra en ydre. (se en god beskrivelse ifbm closures i  kapitel 4 i <a href="http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742">"Javascript: the good parts"</a> ).</p>
<p>Problemet kan omgåes ved at benytte <a href="http://prototypejs.org/api/function/bind">"bind" fra prototypejs</a> på flg. facon:</p>
<p>

{%highlight JavaScript%}
ComboBox.prototype.loader= function (){
  if(this.dataStore[this.paramName]===undefined){
    new Ajax.Request (
    this.url,{
      method: 'post',
      asynchronous: true,
      parameters: this.parameters,
      onSuccess: function (transport){
                                  var response=transport.responseText;
                                  this.dataStore.data[this.paramName]=response.evalJSON();
                                  this.render();
                                  }.bind(this),
      onFailure: function (transport){
                                  alert('failed to retrieve '+this.paramName+' data');
                                  }.bind(this)
     }
}
