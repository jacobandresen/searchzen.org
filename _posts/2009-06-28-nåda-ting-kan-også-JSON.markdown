---
layout: post
title: "nåda. "ting" kan også JSON!"
date: 2009-06-28 03:06
comments: true 
categories: 
---
Her i eftermiddags kiggede jeg lidt videre på <a href="http://gnit.dk/">ting</a> projektet. Det viser sig at andre end mig har haft problemer med at bruge webservicen : <a href="http://krakoa.dk/wordpress/2009/05/31/refindting/">http://krakoa.dk/wordpress/2009/05/31/refindting/</a> . Her bemærkede jeg en kommentar der nævnte ting også kunne json , så jeg kastede mig ud i flg php  kode :

<code lang="php">
class Ting_Client {
   var $opensearch = "http://didicas.dbc.dk/opensearch/";

   public function search($query){
     $hc=new HTTPClient();
     $url = $this->opensearch."?action=searchRequest&query=$query&facets.number=10&outputType=json";
     $host = $hc->extractHost($url);
     $hc->connect($host);
     return( $hc->Get($url) );
   }
 }
</code>

Her antager jeg at din php klient også kan hente HTML sider ligesom <a href="http://github.com/jacobandresen/yase/blob/155ea553a3dd72ca4df07950c236a594fb1872ba/classes/HTTPClient.php">min</a> kan . På den facon kunne man tænke sig noget i denne her stil:

<code lang="php">
<?php
 $t=new Ting_Client();
 $searchResponse = json_decode($t->search($query));
 if($searchResponse->searchResult->hitCount>0) {
 print "<ul>\r\n";
 foreach( $searchResponse->searchResult->records->tingRecord
           as $rec){
    $isbn=$rec->dc->identifier[0];
    $isbn=preg_replace("/ISBN\:/","",$isbn);
    print "<li><a href=\"http://slashdemocracy.org/isbn/".$isbn."\">".$rec->dc->title[0]."</a></li>";
  }
 }
</code>

hvor beskrivelsen på de enkelte poster kan benyttes til at lave et mashup. Jeg har her prøvet med <a href="http://slashdemocracy.org/">slashdemocracy</a>, men det virker vist ikke helt for andet end ISBN.

Da jeg kiggede på outputtet fra ting , så undrede jeg mig lidt over hvorfor at man ikke havde valgt at bruge <a href="http://www.loc.gov/z3950/agency/Z39-50-2003.pdf">Z39.50</a> , men det er så også ok.  Når man har kigget på outputtet fra ting i et stykke tid, så giver det nogenlunde mening.