---
layout: post
title: "afprøvning af groovy på tomcat5.5 på ubuntu vha mysql"
date: 2009-03-03 10:03
comments: true 
categories: 
---
Jeg har iøjeblikket brug for at kunne afprøve flere forskellige måder at implementere ting i java ifbm prototypning.  Under prototypning kan det være forbundet med ulemper at benytte hele J2EE stakken under udvikling da det kan tage unødigt lang tid at kompilere og deploye  Derfor  har jeg valgt at kigge  på <a title="groovy" href="http://groovy.codehaus.org/">groovy</a> .

Da det iøjeblikket er for webapplikationer jeg undersøger , så har jeg valgt at køre under tomcat5.5 på min testmaskine.
tomcat5.5 og groovy kan nemt installeres sammen  på ubuntu. Det gøres sådan her  (jeg antager at du allerede har installeret mysql og den virker)

{%highlight bash%}
sudo apt-get install tomcat5.5 tomcat5.5-admin groovy
{%endhighlight%}

For at få tomcat5.5 til at køre groovy til demonstrationsformål har jeg sat "TOMCAT5_SECURITY=no" i filen "/etc/init.d/tomcat5.5". I et produktionsmiljø bør man gøre sig overvejelser om brugen af classloaders.

 Jeg har  til demonstrationsformål valgt at rette filen /etc/tomcat5.5/tomcat-users.xml til således at bruger "tomcat" har roles="tomcat,admin,manager" - derved kan jeg logge ind i  /manager/ vha 'tomcat' og 'tomcat' .Bemærk at der nederst på manager-siden står "WAR file to deploy". Her kan du uploade flg. fil : <a title="groovytest.war" href="http://pedant.dk/hacks/20090303/groovytest.war">groovytest.war</a>

Herefter kan der ses et resultat i  /groovytest/ på testmaskinen. groovy testkoden ser således ud:

{%highlight Java%}
Sql.loadDriver("com.mysql.jdbc.Driver");
sql = Sql.newInstance("jdbc:mysql://localhost:3306/test", "web","sockmonkey");

sql.eachRow("select * from test") {
println it.id + " " + it.name
}
print "mere test"
{%endhighlight%}

"test.groovy"  henviser til en database "test" med tabellen "test". Disse kan skabes vha filen "test.sql" der er vedlagt i <a title="groovytest.war" href="http://pedant.dk/hacks/20090303/groovytest.war">groovytest.war</a>

war-filen indeholder mysql-driveren , så forbindelsen mellem mysql og groovy skulle fungere der. Men hvis du vil forsøge dig med at køre test.groovy fra kommandolinjen , så kan du også det , hvis du kopierer mysql-connector-java-3.1.14-bin.jar over i din  ~/.groovy/lib/ .  På den facon kan du afvikle testen på serveren uden om tomcat.
