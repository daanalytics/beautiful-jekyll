---
author: makumbe
comments: true
date: 2011-01-13 11:28:09+00:00
layout: post
link: http://blog.daanalytics.nl/2011/01/13/security-issues-when-upgrading-a-web-catalog-from-10g-to-11g/
slug: security-issues-when-upgrading-a-web-catalog-from-10g-to-11g
title: Security issues when upgrading a Web Catalog from 10g to 11g
wordpress_id: 728
categories:
- Setup
tags:
- 11g
- obi11g
- OBIEE
- obiee11g
- Oracle WebLogic Server
- Security
- Web Catalog
---

I blogged about upgrading from Oracle BI EE 10g to Oracle BI EE 11g R1 [earlier](http://obibb.wordpress.com/2010/10/07/upgrading-from-10g-to-11g-repository-and-webcat/). Although this is a very straight forward process, you could end up with some security issues.

Picture the following. You are an administrator user with the appropriate security roles to act as an (Presentation Server) Administrator. You are able to login and manage the Weblogic Console and the Enterprise Manager. When you log into the upgraded Web Catalog you are not able to see the Administration-link.

There already a lot of good blogpost about the new Oracle BI 11g security setup. Just to name a few;



	
  * [RittmanMead](http://www.rittmanmead.com/2010/08/oracle-bi-ee-11g-authentication-authorization-weblogic-security/)

	
  * [Rob Reynolds Part1](https://blogs.oracle.com/robreynolds/entry/security_in_obiee_11g_part_1)

	
  * [Rob Reynolds Part2](https://blogs.oracle.com/robreynolds/entry/security_in_obiee_11g_part_2)


When upgradin a WebCatlog you could be forced to do a work-around  for the security, thanks to [René Kuipers](http://nl.linkedin.com/in/rjlkuipers). The workaround is as follows;



	
  * Do the upgrade according to the documentation

	
  * Make a backup via the Catalog Manager or upgrade a second time so you have a copy of the Web Catalog

	
  * Throw away the user folders via the Catalog Manager

	
  * Login again into the Web Catalog via; [http://localhost:9704/analytics](http://localhost:9704/analytics) (a new user folder should be created)

	
  * If necessary you could move the reports from the backup to the online Web Catalog


It's a workaround and could be very time-consuming when you have to upgrade a Catalog with a lot of users. Hopefully this issue will be solved in a future release.
