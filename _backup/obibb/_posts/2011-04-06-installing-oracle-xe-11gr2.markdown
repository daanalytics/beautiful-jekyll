---
author: makumbe
comments: true
date: 2011-04-06 11:14:12+00:00
layout: post
link: http://blog.daanalytics.nl/2011/04/06/installing-oracle-xe-11gr2/
slug: installing-oracle-xe-11gr2
title: Installing Oracle XE 11gR2
wordpress_id: 860
categories:
- Setup
tags:
- 11g
- Oracle
- Oracle Database
- Oracle Technology Network
- R2
- XE
---

Last week Oracle XE 11gR2 has become available for [download](http://www.oracle.com/technetwork/database/express-edition/11gxe-beta-download-302519.html).[Lucas Jellema](http://technology.amis.nl/blog/11785/oracle-xe-11gr2-the-free-express-edition-for-oracle-database-11gr2) must be among the first ones to write about the installation. This installation seems to be very straight forward. Unfortunately I was presented with an error message about my Physical Memory. A search on Google showed that I was not the only one. On [OTN](http://forums.oracle.com/forums/thread.jspa?messageID=9493493) there were a few people with similar 'problems'.

After going through the [documentation](http://download.oracle.com/docs/cd/E17781_01/install.112/e18803/toc.htm#CIHFEBGE) I found out that the installations requires a free Disk Space of 1.5 GB minimum. When I freed up to 1,5 GB of Disk Space (it was less than 750 MB) on my C-drive (Windows), I was able to continue the installation. If necessary you can even install the software on another drive if you want to.
