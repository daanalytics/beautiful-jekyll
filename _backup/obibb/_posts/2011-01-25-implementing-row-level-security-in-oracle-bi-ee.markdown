---
author: makumbe
comments: true
date: 2011-01-25 12:00:36+00:00
layout: post
link: http://blog.daanalytics.nl/2011/01/25/implementing-row-level-security-in-oracle-bi-ee/
slug: implementing-row-level-security-in-oracle-bi-ee
title: Implementing Row-Level-Security in Oracle BI EE
wordpress_id: 746
categories:
- Setup
tags:
- Oracle BI EE
- Repository
- Row-Level-Security
- Security
---

Sometimes there is a need to restrict data access to certain groups of users. Oracle provides a mechanism called [Row-Level-Security](http://www.dba-oracle.com/concepts/restricting_access.htm). You could achieve similar functionality from within Oracle BI EE.

Picture this; You have a table of Sales Managers which are responsible for a certain region. Each Sales Manger may only see the data for his / her region.

First you have to know which user has logged on and to which region this user belongs. Therefore you should use Session variables. To set this up properly you could refer to the [documentation](http://download.oracle.com/docs/cd/E12096_01/books/admintool/admintool_Variables4.html). You validate the logged on user to a table of Sales Managers. This way you could also select the region a Sales Manager is responsible for. The principle of this solution is that you have the Sales Manager and their regions in a table which you can select from. Let's say we now have a 'REGION' session variable.

We can go on to the Security Groups. Create a new Security Group called; 'Sales Managers'. Assign all the Sales Managers (Repository Users) to this newly created group.

The final step is to set Business Model Filters on this group. The concept of these filters is thatb you add all Logical Tables to this group, which you want to restrict on a Sales Managers' region. You could achieve this by following the next steps;



	
  1. Open the 'Sales Manager'-Security Group,

	
  2. Click on; 'Permissions',

	
  3. Click on the Tab; 'Filters',

	
  4. Click; 'Add',

	
  5. Select the table you want to restrict, eg.; "Sales"."Dim Region"."Region Name",

	
  6. Use the Expression Builder to create the actual filter; "Sales"."Dim Region"."Region Name" = VALUEOF(NQ_SESSION."REGION").


Now when you use the "Sales"."Dim Region"-table in an Oracle BI Answers query, the Business Model Filter will be applied. This filter only applies to this Security Group. User which do not belong to this group will see all the regions.

Similar functionality is used when implementing [Oracle BI Apps Security](http://obibb.wordpress.com/2010/12/20/oracle-bi-applications-security/).
