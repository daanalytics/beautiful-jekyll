---
author: makumbe
comments: true
date: 2010-12-23 11:22:32+00:00
layout: post
link: http://blog.daanalytics.nl/2010/12/23/connect-to-the-database-from-oracle-bi-11g/
slug: connect-to-the-database-from-oracle-bi-11g
title: Connect to the Database from Oracle BI 11g
wordpress_id: 696
categories:
- Setup
tags:
- 10g
- 11g
- Oracle Forum
- OTN
- TNS_ADMIN
- tns_names.ora
---

I ran into the following issue when I upgraded from Oracle BI 10g to Oracle BI 11g. Although the upgrade went smoothly, all of a sudden I was not able to reach the database anymore. After doing some research on the internet I stumbled upon the following [thread](http://forums.oracle.com/forums/thread.jspa?threadID=1118668&tstart=0) on OTN.

The main difference between Oracle BI 10g and Oracle BI 11g is the fact that Oracle BI 11g has it's own Oracle_Home.

Thanks to Dirk and Venkat for the possible solutions:

1.

navigate to; {ORACLE_INSTANCE}\bifoundation\OracleBIApplication\coreapplication\setup,

alter user.cmd or user.sh depending on your OS,

set your TNS_ADMIN location to point to; {MIDDLEWARE_HOME}\Oracle_BI1\network\admin

2.

Copy your tnsnames.ora to {MIDDLEWARE_HOME}\Oracle_BI1\network\admin directory

3.

Use the full  expanded tnsnames as shown below and use this one as the datasource name in your Connection Pool:

(DESCRIPTION =(ADDRESS = (PROTOCOL =  TCP)(HOST = host_name/ip_address)(PORT = port_number))(CONNECT_DATA =(SERVER =  DEDICATED)(SERVICE_NAME = service_name)))
