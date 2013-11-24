---
layout: post
title: "openlayers 2.8 supports WFS-T"
date: 2009-09-02 07:09
comments: true 
categories: 
---
if you are in a organisation where you store data with geographical information associated with it , then you have the option of sharing your data using the following standards specified by<a href="http://www.opengeospatial.org/"> OGC</a>:
<ul>
	<li><a href="http://www.opengeospatial.org/standards/wms">WMS (Web map service)</a></li>
	<li><a href="http://www.opengeospatial.org/standards/wfs">WFS (Web feature service)</a></li>
</ul>
One way to leverage these standards is to use the <a title="geoserver" href="http://geoserver.org">geoserver project </a>for data storage and the <a href="http://openlayers.org/">openlayers project</a> web for showing and editing maps.<strong>update 2009-09-03</strong>: When integrating with the extjs framework , then it is worth using  the <a href="http://geoext.org">geoext project</a>.

An example snippet from geoserver shows the use of WFS-T for inserting geometric data with associated metadata for an alley in Tasmania. I'll just bring it here:

<code lang="xml">

xmlns:wfs="http://www.opengis.net/wfs"
xmlns:topp="http://www.openplans.org/topp"
xmlns:gml="http://www.opengis.net/gml"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.opengis.net/wfs http://schemas.opengis.net/wfs/1.0.0/WFS-transaction.xsd http://www.openplans.org/topp http://localhost:8080/geoserver/wfs/DescribeFeatureType?typename=topp:tasmania_roads"&gt;







494475.71056415,5433016.8189323 494982.70115662,5435041.95096618





alley



</code>

Note that oracle has a well supported ways of extracting GML from spatial datatypes if you need to construct the wfs transactions yourself ( <a href="http://www.oracle.com/technology/sample_code/products/spatial/index.html">oracle locator</a> )

At the first glance wfs can seem a bit complicated. Luckily openlayers has nice wrappings for it that is easily accessed from code  as shown in one of their examples running <a href="http://openlayers.org/dev/examples/wfs-t.html">here</a> :

<script src="https://gist.github.com/1046699.js"> </script>