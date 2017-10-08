---
author: makumbe
comments: true
date: 2010-08-17 06:15:09+00:00
layout: post
link: http://blog.daanalytics.nl/2010/08/17/installing-oracle-bi-11g-r1/
slug: installing-oracle-bi-11g-r1
title: Installing Oracle BI 11g R1
wordpress_id: 360
categories:
- General (Oracle BI EE)
tags:
- 11g
- Installation
- Oracle Business Analytics
---

[](http://obibb.files.wordpress.com/2010/08/prereq-processes-failure.png)Today I started with the installation of the new Oracle BI 11g R1 release. This time I did something a man normally doesn’t do. I started by [RTFM](http://en.wikipedia.org/wiki/RTFM). The documentation could be found [here](http://download.oracle.com/docs/cd/E14571_01/bi.htm). Lucky for me, John did a four part [series](http://obiee101.blogspot.com/2010/08/obiee11g-installation-on-32-bits-xp-pro.html) about installing the Oracle BI Oracle BI 11g R1 release on a on a windows 32 bit XP-pro box. 

I only want to add some additional info about some issues I had while installing. 

The first error or warning I received was about the character set of my 11g database.

 [![](http://obibb.files.wordpress.com/2010/08/characterset.png?w=300)](http://obibb.files.wordpress.com/2010/08/characterset.png)[](http://obibb.files.wordpress.com/2010/08/characterset.png)

For some more details about the 11g database character set, please check [OTN](http://forums.oracle.com/forums/thread.jspa?threadID=924403&tstart=-2).

You can change the character set by issuing the following commands; 

To check the character set

[sourcecode language="sql"]SELECT *
  FROM nls_database_parameters;[/sourcecode]

To change the character set

[sourcecode language="sql"]alter system enable restricted session;
alter system set job_queue_processes=0;
alter database open;
ALTER DATABASE CHARACTER SET INTERNAL_USE UTF8;
ALTER DATABASE CHARACTER SET INTERNAL_USE AL32UTF8;
Shutdown immediate;
startup mount;[/sourcecode]

Next I received a few ‘RCU-6107: DB Init Param’ errors.

[![](http://obibb.files.wordpress.com/2010/08/prereq-processes-failure.png)](http://obibb.files.wordpress.com/2010/08/prereq-processes-failure.png)

[![](http://obibb.files.wordpress.com/2010/08/prereq-open_cursors-failure.png)](http://obibb.files.wordpress.com/2010/08/prereq-open_cursors-failure.png)

Thanks to [Muhammad Habib](http://mhabib.wordpress.com/2010/07/20/rcu6107-db-init-param-error/), I was able to solve these issues.

Let’s see what  Oracle BI 11g R1 has to offer us.
