---
author: makumbe
comments: true
date: 2010-12-09 08:41:51+00:00
layout: post
link: http://blog.daanalytics.nl/2010/12/09/oracle-bi-11g-startup-sequence/
slug: oracle-bi-11g-startup-sequence
title: Oracle BI 11g - Startup Sequence
wordpress_id: 631
categories:
- Oracle BI 11g
tags:
- 11g
- Oracle Business Analytics
- Oracle WebLogic Server
---

Reading through the [Oracle Forum](http://forums.oracle.com/forums/thread.jspa?messageID=6357027) I stumbled upon a possible startup sequence for Oracle BI 11g.

Before you complete the steps below the following Windows Services should **not** be running.

a. Oracle Process Manager (instance1)
b. Oracle Weblogic NodeManager

After that follow the next steps;

**--> Start NodeManager from the Command Prompt**

Cd <MIDDLEWARE_HOME>\wlserver_10.3\server\bin

startNodeManager.cmd

Wait untill you see message "Secure socket listener start at port......"

**--> Start Admin server from command prompt**

Cd <MIDDLEWARE_HOME>\user_projects\domains\bifoundation_domain\bin

startWebLogic.cmd

It will ask for user name / password. Specify the user details that you used at the time of the Oracle BI 11g install. You could also use a 'Boot Identity File' -(boot.properties). Check the [documentation](http://download.oracle.com/docs/cd/E12839_01/web.1111/e13708/overview.htm#i1068946) for more details.

Wait untill you see message Admin server is in 'RUNNING MODE'.

**--> Now start Managed server from GUI**

Access WebLogic console from a webbrowser

[http://<machinename>:7001/console](http://%3cmachinename%3e:7001/console)

Login, Environment > servers > Control > select bi_server1 > click on start

It would take some time for the Managed server to start. Wait untill you see the 'Running' status.

**--> Now start the OBIEE components from command prompt**

Cd <MIDDLEWARE_HOME>\instances\instance1\bin

opmnctl startall

Note that it's a possible startup sequence. There are multiple ways to statup.
