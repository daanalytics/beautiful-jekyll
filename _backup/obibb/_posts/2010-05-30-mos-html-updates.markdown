---
author: makumbe
comments: true
date: 2010-05-30 18:21:08+00:00
layout: post
link: http://blog.daanalytics.nl/2010/05/30/mos-html-updates/
slug: mos-html-updates
title: MOS HTML updates
wordpress_id: 96
categories:
- My Oracle Support
tags:
- MOS
- Oracle
---

Thanks to [Timur Akhmadeev's blog](http://timurakhmadeev.wordpress.com/2010/04/28/mos-html-updates/) I found the solution for the broken links in the MOS HTML updates mail from Oracle Support.

Links in an email are like this:

    
    https://supporthtml.oracle.com/ep/faces/secure/kmDocumentDisplay.jspx?id=1062675.1


but should be like this:

    
    https://supporthtml.oracle.com/ep/faces/secure/km<strong>/</strong>DocumentDisplay.jspx?id=1062675.1


- note the extra slash between km and DocumentDisplay.

For more details, check Timur's blog.
