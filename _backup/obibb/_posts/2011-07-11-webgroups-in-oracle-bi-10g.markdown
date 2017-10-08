---
author: makumbe
comments: true
date: 2011-07-11 10:30:54+00:00
layout: post
link: http://blog.daanalytics.nl/2011/07/11/webgroups-in-oracle-bi-10g/
slug: webgroups-in-oracle-bi-10g
title: WEBGROUPS in Oracle BI 10g
wordpress_id: 966
categories:
- Presentation Catalog
tags:
- 10g
- Oracle Business Analytics
- presentation catalog
- session variable
- webgroups
---

While a lot of us are already focusing on Oracle BI 11g, I still also have to service some 10g clients. This one is a Oracle BIA 7.9.6 client with hundreds of responsibilities in Oracle eBS with access to Oracle BI. I used [UDML](http://obibb.wordpress.com/2011/02/21/udml-scripting/) to script the responsibilities into the repository. Via de weblog of [KPI Partners](http://kpipartners.blogspot.com/2009/12/defining-and-assigning-web-group.html) I found the solution to assign the responsibilities to a Web Group.

Oracle eBS will be used to store the membership information. A group (responsibility) in the Oracle BI Repository belongs to a organization and a role.  This information can be retrieved from the responsibility in Oracle eBS. The organization is stored via a profile option ('PER_SECURITY_PROFILE_ID'). In this case we specified an additional custom profile option to store the role (User, Superuser, Reportbuilder, etc.).  Via an Initialization Block the WEBGROUP-variable can be initialized.

[![](http://obibb.files.wordpress.com/2011/07/init-block-webgroups.png?w=300)](http://obibb.files.wordpress.com/2011/07/init-block-webgroups.png)

**Note:** Do not forget to uncheck the 'Use caching' checkbox, to make sure that you retrieve the current values.

[![](http://obibb.files.wordpress.com/2011/07/session-variable-webgroups.png?w=300)](http://obibb.files.wordpress.com/2011/07/session-variable-webgroups.png)

****The only thing what's left to do mis to create the roles and organizations as Webgroups in the Presentation Catalog.

Instead of making all the Oracle eBS responsibilities separately available in the Presentation Catalog, you'll only have to define the Webgroups. In this case it was a difference of hundreds compared to about 10 to 15.

This could make your life a little bit easier.
