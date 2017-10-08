---
author: makumbe
comments: true
date: 2010-11-05 12:02:50+00:00
layout: post
link: http://blog.daanalytics.nl/2010/11/05/oracle-ebs-release-12-1-1-and-internet-explorer-8/
slug: oracle-ebs-release-12-1-1-and-internet-explorer-8
title: Oracle eBS Release 12.1.1 and Internet Explorer 8
wordpress_id: 537
categories:
- Oracle eBS
tags:
- Internet Explorer
- R12
---

Oracle eBS Release 12.1.1 and Internet Explorer 8; it's not always a happy marriage. Although Internet Explorer 8 is [certified](http://blogs.oracle.com/stevenChan/2009/09/internet_explorer_8_certified_ebs12.html) with E-Business Suite Release 12, you could experiencing problems. If this is the case, the following could be a solution.

- Add URL to Local Intranet Trusted Sites

Internet Explorer Menu => Tools => Internet Options => (Tab)Security => Local Intranet => (Button) Sites => (Button) Advanced

** Add the URL

- Internet Explorer Menu => Tools => Internet Options => (Tab)Security => (Button) Custom Level => (Option) Scripting =>

   ** Enable XXS Filter => Disable

- Disable Google Toolbar

Good Luck.
