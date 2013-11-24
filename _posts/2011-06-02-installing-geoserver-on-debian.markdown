---
layout: post
title: "installing geoserver on debian"
date: 2011-06-02 03:06
comments: true 
categories: 
---
I just installed geoserver on debian using apache 2.2 . Here's what I did:

First of all I installed jetty using "sudo aptitude install jetty" , then I grabbed the geoserver source from <a href="http://svn.codehaus.org/geoserver/trunk/">http://svn.codehaus.org/geoserver/trunk/</a> and compiled it using openjdk-6 and maven 2.2  (looks like the build fails using the standard maven in debian, so I grabbed a version of maven from<a title="ftp://mirors.sunsite.dk" href="ftp://mirrors.sunsite.dk"> ftp://mirrors.sunsite.dk</a> ) . 

After compiling, I copied geoserver/src/web/app/target/geoserver.war to /usr/share/jetty/webapps/ and restarted jetty using /etc/init.d/jetty restart .

I can only access port 80 on my webhost, and I need apache 2 for other purposes , so I had to configure mod_proxy. I setup a virtual host in /etc/apache2/sites-available/geo.searchzen.org and symlinked it to /etc/apache2/sites-enabled/geo.searchzen.org . To enable mod_proxy , I created  symlinks  for  /etc/apache2/mods-available/proxy.load and /etc/apache2/mods-available/proxy_http.load to /etc/apache2/mods-enabled. (mod_proxy fails without the symlink to proxy_http.load)

Here's the relevant parts of my mod_proxy configuration in /etc/apache2/sites-enabled/geo.searchzen.org :

<script src="https://gist.github.com/1004676.js"> </script>
