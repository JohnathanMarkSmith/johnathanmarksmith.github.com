---
layout: post
title: "Basic install of JBoss for developers on linux"
description: "Basic install of JBoss for developers on linux"
categories: [ Linux, Java, JBoss, AS7 ]
tags: [ Linux, Java, JBoss, AS7 ]
comments: false
---

Below is a quick and easy way to install JBoss on linux for a developer to test and learn how to use it.  

Please don't use this setup for production.

### Download JBoss EAP6 (AS7.1.1.Final) and untar 

To download and untar jboss you need to enter the following commands:
{% highlight bash %}
[jsmith@regan ~] wget http://download.jboss.org/jbossas/7.1/jboss-as-7.1.1.Final/jboss-as-7.1.1.Final.tar.gz
[jsmith@regan ~] tar -zxvf jboss-as-7.1.1.Final.tar.gz 
{% endhighlight %}

### Start Up JBoss in standalone mode

Now that you have jboss untar on your linux box its time to start it in standalone mode. Just enter the following commands:


{% highlight bash %}
[jsmith@regan ~] cd jboss-as-7.1.1.Final/bin
[jsmith@regan ~] ./standalone.sh
{% endhighlight %}

The output should look something like the one below:

{% highlight bash %}
=========================================================================

  JBoss Bootstrap Environment

  JBOSS_HOME: /home/jsmith/tmp/jboss-as-7.1.1.Final

  JAVA: java

  JAVA_OPTS:  -server -XX:+UseCompressedOops -XX:+TieredCompilation -Xms64m -Xmx512m -XX:MaxPermSize=256m -Djava.net.preferIPv4Stack=true -Dorg.jboss.resolver.warning=true -Dsun.rmi.dgc.client.gcInterval=3600000 -Dsun.rmi.dgc.server.gcInterval=3600000 -Djboss.modules.system.pkgs=org.jboss.byteman -Djava.awt.headless=true -Djboss.server.default.config=standalone.xml

=========================================================================

14:10:26,029 INFO  [org.jboss.modules] JBoss Modules version 1.1.1.GA
14:10:26,250 INFO  [org.jboss.msc] JBoss MSC version 1.0.2.GA
14:10:26,312 INFO  [org.jboss.as] JBAS015899: JBoss AS 7.1.1.Final "Brontes" starting
14:10:27,440 INFO  [org.xnio] XNIO Version 3.0.3.GA
14:10:27,457 INFO  [org.jboss.as.server] JBAS015888: Creating http management service using socket-binding (management-http)
14:10:27,465 INFO  [org.xnio.nio] XNIO NIO Implementation Version 3.0.3.GA
14:10:27,485 INFO  [org.jboss.remoting] JBoss Remoting version 3.2.3.GA
14:10:27,548 INFO  [org.jboss.as.logging] JBAS011502: Removing bootstrap log handlers
14:10:27,557 INFO  [org.jboss.as.configadmin] (ServerService Thread Pool -- 26) JBAS016200: Activating ConfigAdmin Subsystem
14:10:27,587 INFO  [org.jboss.as.clustering.infinispan] (ServerService Thread Pool -- 31) JBAS010280: Activating Infinispan subsystem.
14:10:27,682 INFO  [org.jboss.as.connector] (MSC service thread 1-3) JBAS010408: Starting JCA Subsystem (JBoss IronJacamar 1.0.9.Final)
14:10:27,689 INFO  [org.jboss.as.naming] (ServerService Thread Pool -- 38) JBAS011800: Activating Naming Subsystem
14:10:27,720 INFO  [org.jboss.as.osgi] (ServerService Thread Pool -- 39) JBAS011940: Activating OSGi Subsystem
14:10:27,735 INFO  [org.jboss.as.security] (ServerService Thread Pool -- 44) JBAS013101: Activating Security Subsystem
14:10:27,750 INFO  [org.jboss.as.connector.subsystems.datasources] (ServerService Thread Pool -- 27) JBAS010403: Deploying JDBC-compliant driver class org.h2.Driver (version 1.3)
14:10:27,776 INFO  [org.jboss.as.security] (MSC service thread 1-2) JBAS013100: Current PicketBox version=4.0.7.Final
14:10:27,840 INFO  [org.jboss.as.webservices] (ServerService Thread Pool -- 48) JBAS015537: Activating WebServices Extension
14:10:27,871 INFO  [org.jboss.as.naming] (MSC service thread 1-4) JBAS011802: Starting Naming Service
14:10:27,924 INFO  [org.jboss.as.mail.extension] (MSC service thread 1-1) JBAS015400: Bound mail session [java:jboss/mail/Default]
14:10:28,183 INFO  [org.jboss.ws.common.management.AbstractServerConfig] (MSC service thread 1-1) JBoss Web Services - Stack CXF Server 4.0.2.GA
14:10:28,272 INFO  [org.apache.coyote.http11.Http11Protocol] (MSC service thread 1-3) Starting Coyote HTTP/1.1 on http--127.0.0.1-8080
14:10:28,746 INFO  [org.jboss.as.remoting] (MSC service thread 1-1) JBAS017100: Listening on /127.0.0.1:4447
14:10:28,749 INFO  [org.jboss.as.remoting] (MSC service thread 1-3) JBAS017100: Listening on /127.0.0.1:9999
14:10:28,754 INFO  [org.jboss.as.server.deployment.scanner] (MSC service thread 1-2) JBAS015012: Started FileSystemDeploymentService for directory /home/jsmith/tmp/jboss-as-7.1.1.Final/standalone/deployments
14:10:28,896 INFO  [org.jboss.as.connector.subsystems.datasources] (MSC service thread 1-1) JBAS010400: Bound data source [java:jboss/datasources/ExampleDS]
14:10:29,026 INFO  [org.jboss.as] (Controller Boot Thread) JBAS015951: Admin console listening on http://127.0.0.1:9990
14:10:29,027 INFO  [org.jboss.as] (Controller Boot Thread) JBAS015874: JBoss AS 7.1.1.Final "Brontes" started in 3281ms - Started 133 of 208 services (74 services are passive or on-demand)
{% endhighlight %}

### Add the admin

Now it's time to setup the admin account for jboss. Open a new console and follow the following steps. I am going to make the username "admin" and the password "jboss" but you can use any username and password you would like, follow the commands below

{% highlight bash %}
cd jboss-as-7.1.1.Final/bin
./add-user.sh
{% endhighlight %}

Your output should look like this:

{% highlight bash %}
What type of user do you wish to add? 
 a) Management User (mgmt-users.properties) 
 b) Application User (application-users.properties)
(a): 

Enter the details of the new user to add.
Realm (ManagementRealm) : 
Username : admin
Password : 
Re-enter Password : 
The username 'admin' is easy to guess
Are you sure you want to add user 'admin' yes/no? yes
About to add user 'admin' for realm 'ManagementRealm'
Is this correct yes/no? yes
{% endhighlight %}

### JBoss is up and running.

Ok that is the basic install of jboss as a standalone for a developer to use.  Now launch your browser to http://127.0.0.1:8080 or http://localhost:8080 and if anything was done righ your output should look like the one below:

<div style="text-align: center">
<img src="/images/jboss.jpg" alt="Installing Jboss on Linux with Johnathan Mark Smith">
</div>


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
