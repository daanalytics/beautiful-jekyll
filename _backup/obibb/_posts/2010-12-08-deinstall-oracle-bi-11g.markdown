---
author: makumbe
comments: true
date: 2010-12-08 12:33:44+00:00
layout: post
link: http://blog.daanalytics.nl/2010/12/08/deinstall-oracle-bi-11g/
slug: deinstall-oracle-bi-11g
title: Deinstall Oracle BI 11g
wordpress_id: 628
categories:
- Oracle BI 11g
tags:
- 11g
- Installation
- Oracle Business Analytics
---

Sometimes you might run into the situation that you have to deinstal, Oracle BI 11g. If you read the [manual](http://download.oracle.com/docs/cd/E14571_01/bi.1111/e10539/c5_deinstall.htm#CIHIIGAD), you will be presented with a sequence of events. Deinstalling an Oracle Business Intelligence installation on a single Windows computer involves the following tasks:

**--> Run the deinstall script and select the Deinstall instances managed by a WebLogic domain option.**

Make sure the weblogicserver is running.

Open a command prompt,

Cd <MIDDLEWARE_HOME>\Oracle_BI1\oui\bin

Run setup.exe -deinstall

option: Deinstall ASInstances managed by WebLogic Domain

**--> Stop all Oracle Business Intelligence processes and servers, including all OPMN-controlled components and JEE components.**

**--> Drop the Metadata Services (MDS) and Business Intelligence Platform (BIPLATFORM) schemas using RCU.**

Cd <RCU_HOME>\bin

Run rcu.bat

**--> Run the deinstall script and select the Deinstall the Oracle home option.**

Cd <MIDDLEWARE_HOME>\Oracle_BI1\oui\bin

Run setup.exe -deinstall

option: Deinstall Oracle home

**--> Deinstall the Oracle Common home manually or by running the deinstall script that it contains.**

oracle_common\oui\bin\

Run setup.exe -deinstall -jreLoc full_path_of_jre_or_jdk

**--> Use the Oracle WebLogic Server uninstaller to uninstall WebLogic Server.**

Cd <MIDDLEWARE_HOME>\utils\uninstall

uninstall -mode=console

**--> Remove the Oracle home (if necessary).**

Cd <MIDDLEWARE_HOME>/user_projects/domains

delete folder; bifoundation_domain

**--> Remove the Middleware home and any other homes (Domain home, Applications home, and Instance home) that might have been installed outside of the Middleware home.**

navigate to <MIDDLEWARE_HOME>- parent_dirictory

delete folder; <MIDDLEWARE_HOME>

Now you are good to go and try again.

Good Luck!
