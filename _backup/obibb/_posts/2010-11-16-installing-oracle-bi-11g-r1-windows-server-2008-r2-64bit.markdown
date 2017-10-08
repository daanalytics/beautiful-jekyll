---
author: makumbe
comments: true
date: 2010-11-16 10:03:54+00:00
layout: post
link: http://blog.daanalytics.nl/2010/11/16/installing-oracle-bi-11g-r1-windows-server-2008-r2-64bit/
slug: installing-oracle-bi-11g-r1-windows-server-2008-r2-64bit
title: Installing Oracle BI 11g R1 - Windows Server 2008 R2 64bit
wordpress_id: 561
categories:
- Setup
tags:
- 11g
- obi11g
- obiee11g
- Oracle Business Analytics
- RCU
- Weblogic
- Windows R2008 64bit
---

Recently I did an installation on a Windows Server 2008 R2 64bit. Reading through the documentation made me realize that it's not possible to do a 'Enterprise Install'. Check the following part in the manual:

"**1.4.3 Software Only Install**

The Software Only Install type installs the Oracle Business Intelligence software binary files in an Oracle home for later configuration as part of a Fusion Middleware deployment. This install type is required to install Oracle Business Intelligence on an AIX operating system or with a 64-bit JVM, such as on a supported 64-bit operating system."

Th following could be a guideline to install Oracle BI 11g on Windows Server 2008 R2 64bit:

Install RCU --> rcuHome\BIN\rcu.bat
Install [JDK 64bit](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
Install [Weblogic generic](http://download.oracle.com/otn/nt/middleware/11g/wls1033_generic.jar) --> via the Command Line java -jar wls1033_generic.jar
Install Oracle BI11g --> 'Software Only'
Run config.bat to configure Oracle BI11g -->C:\Oracle\Middleware\Oracle_BI1\bin\config.bat

Of course you need to check the manual for additional info. Next to that you have to perform a 'Software Only' install on 32bit machine to be able to use your client tools.

Check [My Oracle Support](https://supporthtml.oracle.com/ep/faces/secure/km/DocumentDisplay.jspx?id=1220564.1) for more details.
