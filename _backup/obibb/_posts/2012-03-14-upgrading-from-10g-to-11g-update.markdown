---
author: makumbe
comments: true
date: 2012-03-14 11:30:05+00:00
layout: post
link: http://blog.daanalytics.nl/2012/03/14/upgrading-from-10g-to-11g-update/
slug: upgrading-from-10g-to-11g-update
title: Upgrading from 10g to 11g (Update)
wordpress_id: 1095
categories:
- Oracle BI 11g
tags:
- 11g
- Oracle BI EE
- Security
- Upgrade Assistant
---

In preparation of an Oracle BI Applications (OBIA) upgrade to OBIA 7.9.6.3, I have been running the Oracle BI 11.1.1.6 [Upgrade Assistant](http://docs.oracle.com/cd/E23943_01/bi.1111/e16452/apndx_screens.htm#FUGBI274). Just to see whether we could expect (serious) issues. On the other hand I was curious how the Oracle BI 10g Security Groups would upgrade to the Oracle BI 11g Application Roles. Application Roles are managed via the the Enterprise Manager (Policy Store - [system-jazn-data.xml](http://docs.oracle.com/cd/E23943_01/bi.1111/b32121/pbr_conf012.htm#RSPUB75339)). Actually [Rittman Mead](http://www.rittmanmead.com/2012/03/an-obiee-11g-security-primer-introduction/) are running a 5-part series on Oracle BI 11g Security at the moment.

The Oracle BI Application Security is configured as [follows](http://obibb.wordpress.com/2010/12/20/oracle-bi-applications-security/) in Oracle BI 10g. The responsibilities in Oracle eBS are created as groups in Oracle BI. After upgrading to 11g these groups are created as Applications Roles. If you check the in the Oracle BI 11g Weblogic Console, you would see that the responsibilities are also created as groups. These groups are created for Authentication (confirming the identity of a user) purposes. The Application roles are created for the Authorization (specifying access rights).

I have been blogging about the [upgrade](http://obibb.wordpress.com/2010/10/07/upgrading-from-10g-to-11g-repository-and-webcat/) from 10g to 11g earlier. There doesn't seem to be any major difference in the Upgrade Assistant in 11.1.1.6. You basically have to follow the same steps as in the previous versions.

After the upgrade I ran the Consistency Checker. A few 'Warnings' caught my eye. I haven't seen those before so I guess they are introduced in Oracle BI 11g.

--> NQSError 39051 (Warnings) - Application Role "*****" is not defined in the Enterprise Manager.

There are 2 options to solve these errors:

Remove the Application Role from ....



	
  * .... the Policy Store via the Enterprise Manager

	
  * .... the Reporsitory (RPD) via the Identy Manager in the Oracle BI Administration Tool.


--> NQSError 39062 (Warnings) Initialization Block '*****' uses Connection Pool '"*****"."*****"' which is used for report queries. This may impact query performance.

It's common practice to create an additional Initialization Block for Session variables. Check [Nicolas'](http://gerardnico.com/wiki/dat/obiee/connection_pool) blog for more details on the Oracle BI Connection Pools.

Cheers.
