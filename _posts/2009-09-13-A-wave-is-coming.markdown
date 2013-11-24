---
layout: post
title: "A wave is coming"
date: 2009-09-13 09:09
comments: true 
categories: 
---
Last week I attended a  day of <a title="outstanding geek fun" href="http://www.masteringwave.com/2009/09/wave-hackathon-in-copenhagen/">outstanding geek fun</a> . At the Google wave hackathon I had the chance to sink my teeth into the Google wave API after seeing presentations on gwt and google wave  by <a href="http://twitter.com/tpedersen">Tommy Pedersen</a> and a presentation on wave gadgets by  Joakim Recht.

After a couple of hours of presentations and brainstorming  we started hacking.  I teamed up with <a title="skakanka" href="http://twitter.com/skakanka"> skakanka</a> to experiment with sending the contents of a wave to a Proof of concept Document storage system . But we ended up doing a simple Echo Bot (but hey! we illustrated how to extract content from a wavelet and send it somewhere).

I brought a mac and used the <a title="google eclipse plugin" href="http://code.google.com/eclipse/">Google eclipse plugin</a> for galileo for coding. It helped that I allready had a Google app engine account from some earlier experiments - but I spent some time learning the different key combinations on the mac - it was great fun though (and now I know how to use eclipse on  a mac!). Deploying on google app engine is as simple as pressing a button in eclipse (I also tried using som ant tasks in my earlier experiments).

We managed to have a google wave running sometime before lunch - so it is very easy to get a basic understanding what a wave bot is all about. (You could think of it as an <a href="https://sourceforge.net/projects/pluggableircbot/">ircbot</a> on steroids ! )

The overall idea of building a google wave bot is to listen to incoming events defined in the protocol. Let's say we want to perform something when somebody enters the wave or write something - then we can define the capabilities like this:

<code lang="xml">
<?xml version="1.0"?>
<w:robot xmlns:w="http://wave.google.com/extensions/robots/1.0">
  <w:version>0.0.4</w:version>
  <w:capabilities>
     <w:capability name="blip_submitted"></w:capability>
    <w:capability name="wavelet_participants_changed"/>
  </w:capabilities>
</w:robot>
</code>

Then the robot should act on the defined events in a manner similar to this :

<code lang="java">
@Override
public void processEvents(RobotMessageBundle robotMessageBundle) {
  Wavelet wavelet = robotMessageBundle.getWavelet();
  String rootText = wavelet.getRootBlip().getDocument().getText();
  for ( Event e: robotMessageBundle.getEvents()){
    Blip b= e.getBlip();
    String text= e.getBlip().getDocument().getText();
    if (e.getType().equals(EventType.BLIP_SUBMITTED)){
      e.getBlip().getDocument().append( makeEcho(text));
    }
  }
}
</code>

The Wave client api  offers something like the DOM api for the xml being sent back and forth. During the hackathon I learnt that there is no way to ask for the contents of the entire wave from a single blip - so it will require some thinking to save the entire contents of the wave - but it should be doable.

Sometime during the afternoon things started to slow down on the wave test server. I noticed that some of the other guys doing a multiuser  interactive drawing gadget for wave. It looked like they recorded a delta to send every time the mouse moved! This made me want to look a bit under "the hood":

<object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" width="425" height="350" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,40,0"><param name="src" value="http://www.youtube.com/v/uOFzWZrsPV0" /><embed type="application/x-shockwave-flash" width="425" height="350" src="http://www.youtube.com/v/uOFzWZrsPV0"></embed></object>

Sounds like the team are handling the multiuser issues using "operational transforms" . Maybe they could somehow 'batch' deltas from interactive gadgets ? I have yet to fully understand how "operational transforms" work  - but it sounds like an exciting challenge to make this work on a large scale!