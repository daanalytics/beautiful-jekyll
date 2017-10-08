---
author: makumbe
comments: true
date: 2013-09-11 10:55:51+00:00
layout: post
link: http://blog.daanalytics.nl/2013/09/11/the-fit-of-oracle-analytical-applications/
slug: the-fit-of-oracle-analytical-applications
title: The Fit of Oracle Analytical Applications
wordpress_id: 1460
categories:
- Oracle BI Applications
tags:
- OAA
- OBIA
---

My colleague Ronald Kok wrote a [blogpost](http://dataliberator.wordpress.com/2013/08/31/prefab-datawarenhuizen-everybody-happy/) yesterday. Next to Oracle BI Applications for ERP / CRM (OBIA), Oracle offers BI Applications for the [industry](http://www.oracle.com/us/solutions/business-analytics/analytic-applications/industry/overview/index.html) as well. I agree with Ronald, that there is nothing wrong with the technology. Still there are (a lot of) Oracle Analytical Applications (OAA) projects which struggle to succeed.

In my experience one of the major reasons of these struggles is the fact that a lot of Implementation Partners refuse to implement OAA like it is meant to be. They just start customizing and before you know it, you are no longer looking at OBIA, but you have built your own custom solution. I don't have anything against custom solutions, but if you have spent a large amount of money on buying OBIA,  then it's sin if you do not use it.

I do not have any experience with the Industry BI Applications. From my on-hands OBIA implementations, I know for a fact that you should always start with a Vanilla Implementation. Take your time to follow the Configuration Guide. Include Functional expertise in the process of configuring OBIA. If you do the configuration properly and run your first load, you will see the out-of-the-box dashboards and they will show data. Not just data, but the data of the source system OBIA extracts it's data from.

From this point on, you will be able to assess what OBIA can do for your organization. Perform a Fit/Gap analyses, but focus on the Fit and not solely on the Gap. ![Oracle BIA - Iceberg](http://obibb.files.wordpress.com/2013/09/oracle-bia-iceberg.png?w=293)In a lot of Oracle BIA presentations you will see the picture on the left side. What you see is definitely not only what  you get. The top of the iceberg could be compared with the dashboards and reports of OBIA. The OBIEE metadata and the ETL (DAC & Informatica or ODI and the Web Configuration Tools) represent the remainder of the iceberg.

A Gap does not necessarily mean that you have to build a whole new customization or dig your way through the existing ETL. It's quite possible that just changing an out-of-the-box analysis would be sufficient. I have mentioned it [earlier](http://obibb.wordpress.com/2013/07/18/validating-the-group-account-mapping-in-oracle-bia-7963/), the out-of-the-box Balance Sheet, can easily be customized by using GL Segments instead of the Group Accounts. The GL Segments are out-of-the-box functionality (just some configuration) as well. It's 'just' a matter of replacing fields.

Therefore I recommend everybody to take the time to investigate what's actually in OBIA. Fit/Gap analyses will take time, but building a customized solution will take time too.
