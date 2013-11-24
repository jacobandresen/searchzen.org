---
layout: post
title: "Et pragmatisk miljø til at kode J2EE i"
date: 2008-01-30 10:01
comments: true 
categories: 
---
Efter at have kigget lidt på linux igen her i 2008, så har jeg fundet opdaget at det er forholdsvist nemt at  begå sig med javaudvikling på serversiden i linux. Tilbage dengang da J2EE startede med at gribe om sig omkring år 1998- 2001 , så kan dem der var med den gang nok huske hvilket helvede det var at vedligeholde et udviklingsmiljø for java.  Tingene har sandeligt ændret sig siden <a href="http://www.sun.com/software/opensource/java/index.jsp" title="Sun frigav java som Open source!">Sun frigav java som Open source</a>!

I dag har jeg installeret  et udviklingsmiljø på linux med:
<ul>
	<li>suns java sdk</li>
	<li> eclipse</li>
	<li>tomcat 5.5</li>
	<li> ant og junit</li>
	<li>php</li>
</ul>
Det kunne jeg gøre forholdsvist nemt således:

<strong>sudo apt-get install sun-java6-jdk eclipse tomcat5.5 ant junit</strong>

jeg havde allerede installeret <a href="http://www.oracle.com/technology/products/database/xe/index.html" title="Oracle Express Edition">Oracle Express edition</a> og havde bemærket at jdbc driverne lå i

<em>/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/jdbc/lib</em>/

Hvis  jeg havde databasen på en anden maskine, så ville jeg have hentet jdbc driverne  <a href="http://www.oracle.com/technology/software/tech/java/sqlj_jdbc/index.html" title="her">her</a>

Da  dette er min hjemme maskine , så vil jeg også gerne kunne køre php ifbm andre ting --  så jeg vil gerne stadigvæk køre apache. Derfor ville jeg gerne have en måde at integrere php på apache2 og tomcat5.5. Jeg har tidligere gjort dette med mod-jk connectoren til projekter - og fandt heldigvis mod-jk og php5 hos ubuntu:

<strong>sudo apt-get install libapache2-mod-jk php5
</strong>

Det viste sig at jeg skulle pille lidt ved jk.load opsætningen for mod-jk modulet for apache:

indhold af /etc/apache2/mods-enabled/jk.load:

<em>LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so
JkWorkersFile /etc/apache2/workers.properties
JkLogFile /var/log/apache2/mod_jk.log
JkLogLevel debug
JkLogStampFormat "[%a %b %d %H:%M:%S %Y]"
JkMount /java/* worker1</em>

<em>
</em> derefter skulle /etc/apache2/workers.properties indstilles:

<em>workers.tomcat_home=/usr/share/tomcat5.5
workers.java_home=/usr/lib/jvm/java-1.6.0-sun
ps=/
worker.list=worker1
worker.worker1.port=8009
worker.worker1.host=localhost
worker.worker1.type=ajp13
worker.worker1.lbfactor=1</em>

Dernæst skulle apache2 og tomcat5.5 genstartes:

<strong>sudo /etc/init.d/apache2 restart</strong>

<strong>sudo /etc/init.d/tomcat5.5 restart</strong>

Nu kan urls med /java/* i køre på tomcat og resten på apache. Voila .

Bemærk iøvrigt at du nok gerne vil omdøbe /java/ til dit helt eget seje applikationsnavn i /usr/share/tomcat5.5/webapps/ . Du kan læse mere om hvordan du bruger servlets og jsp her : <a href="http://www.coreservlets.com/Apache-Tomcat-Tutorial/tomcat-5.5.html" title="coreservlets tomcat tutorial">http://www.coreservlets.com/Apache-Tomcat-Tutorial/</a>