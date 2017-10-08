---
author: makumbe
comments: true
date: 2012-08-20 10:38:56+00:00
layout: post
link: http://blog.daanalytics.nl/2012/08/20/logout-link-disappearing-in-oracle-bi-11g-oracle-ebs-r12-integration/
slug: logout-link-disappearing-in-oracle-bi-11g-oracle-ebs-r12-integration
title: 'Logout Link disappearing in Oracle BI 11g / Oracle eBS R12 integration '
wordpress_id: 1209
categories:
- Oracle eBS
tags:
- 11g
- Oracle Business Analytics
- R12
---

We have successfully [integrated ](http://obibb.wordpress.com/2012/08/16/integrating-oracle-ebs-r12-and-oracle-bi-11g/)Oracle BI 11g with Oracle eBS R12. We log into Oracle BI 11g via Oracle eBS R12. One of the additional requirements is to have a Log out Link in Oracle BI 11g which takes us back to Oracle eBS R12. Therefor we have added the following to our instanceconfig.xml

[sourcecode language="xml"]
<!--Adding Logout Link-->
<SchemaExtensions>
<Schema name="EBS-ICX" logonURL="http://<Oracle eBS R12 Server:port>/OA_HTML/OA.jsp?OAFunc=OAHOMEPAGE" logoffURL="http://<Oracle eBS R12 Server:port>/OA_HTML/OA.jsp?OAFunc=OAHOMEPAGE"/>
</SchemaExtensions>
<!--Adding Logout Link-->
[/sourcecode]

This works like expected, but every time we do a restart of the BI service, the instanceconfig.xml get's backed up and replaced a 'new' instanceconfig.xml, without the Log out Link.

This 'problem' is related to the following BUG; [14249563](https://support.oracle.com/epmos/faces/Dashboard?_adf.ctrl-state=kpsrf8w3_157) on My Oracle Support. The good news is that it will be fixed in 11.1.1.7. The bad news is that at present the only workaround is to manually re-set the link.
