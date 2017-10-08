---
author: makumbe
comments: true
date: 2011-01-20 11:50:04+00:00
layout: post
link: http://blog.daanalytics.nl/2011/01/20/passing-special-characters-in-oracle-bi-ee/
slug: passing-special-characters-in-oracle-bi-ee
title: Passing special characters in Oracle BI EE
wordpress_id: 739
categories:
- Styling
tags:
- HTML
- Url Encoding
---

I saw a question on [Oracle IT Toolbox](http://oracle.ittoolbox.com/groups/technical-functional/oracle-bi-l/go-url-unable-to-pass-special-characters-in-obiee-10314-3984848) the other day. A subject which ﻿I mentioned this [earlier](http://obibb.wordpress.com/2010/08/05/integrating-oracle-ebs-and-oracle-bi-ee-links/).

Passing special characters in Oracle BI EE is something you should avoid as much as possible. If you have to cope with these special characters, eg. in a GO-url, please refer to a site which handles HTML URL Encoding; [http://www.w3schools.com/TAGS/ref_urlencode.asp](http://www.w3schools.com/TAGS/ref_urlencode.asp)

If  you have a string with spaces, you could use the 'REPLACE'-function to substitute the space with; '%20'. If necessary you could nest the 'REPLACE'-function to also substitute '&' with '%26'.

Something like; REPLACE(REPLACE(string, ' ', '%20'), '&', '%26')

Good Luck
