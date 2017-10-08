---
author: makumbe
comments: true
date: 2011-05-18 17:24:39+00:00
layout: post
link: http://blog.daanalytics.nl/2011/05/18/rittmanmead-bi-forum-2011-masterclass-part-i/
slug: rittmanmead-bi-forum-2011-masterclass-part-i
title: RittmanMead BI Forum 2011 - Masterclass (Part I)
wordpress_id: 911
categories:
- RittmanMead BI Forum
tags:
- 11g
- Architecture
- obiee11g
- Oracle BI EE
- Spatial
- Weblogic
- WLST
---

Arrived this morning in Brighton for my second [RittmanMead BI Forum 2011](http://www.rittmanmead.com/biforum2011/). The forum started of with a Masterclass. Because of the flight-schedule between Amsterdam and London - Gatwick, I wasn't able to make it on time. In the end I received sufficient information to call it a valuable Masterclass. The hosts of this Masterclass were the master himself; [Mark Rittman](http://www.rittmanmead.com/author/mark-rittman/) and [Tony Heljula](http://www.linkedin.com/in/antonyheljula). These guys had the privilege to 'compete' with last years Masterclass by [Kurt Wolff](http://kpipartners.blogspot.com/). I must say; They did a pretty good job. The Masterclass consist of 4 different subjects, equally (although Mark tried to claim Tony's time) divided by the two hosts:



	
  * OBIEE11g - Architecture, Components & Internals

	
  * OBIEE11g - Spatial Integration

	
  * OBIEE11g - Server & RPD New Features

	
  * OBIEE11g - SOA Integration


Mark started off with the OBIEE11g - Architecture, Components & Internals. Unfortunately I had to miss the first part. Still I have been able to take some notes. With the new Oracle BI 11g release, starting form 11.1.1.3 we are presented with an whole new architecture. The best way to  make sense of Oracle BI 11g is to get comfortable with;

	
  * Instances

	
  * Domains

	
  * Using the WebLogic Scripting Tool ([WLST](http://download.oracle.com/docs/cd/E12840_01/wls/docs103/config_scripting/using_WLST.html))


I joined the Masterclass when Mark arrived at the WLST part. Thes WLST-scripts are calling [MBeans.](http://download.oracle.com/javase/tutorial/jmx/mbeans/standard.html) There seem to be more of these MBeans in the background than presented via the GUI. By using scripting ([Jython](http://en.wikipedia.org/wiki/Jython)) you are able to manipulate meta-data in the repository and objects in the catalog. [Andreas Nobbmann](http://blog.trivadis.com/blogs/andreasnobbmann/default.aspx) will cover part of this subject in his presentation on Thursday.

Anthony continued with his presentation about the improvements of the Spatial Integration in OBIEE11g. One of my ex-colleagues (Maarten Jan Kampen)  did a presentation of  [Spatial Intelligence](http://www.rittmanmead.com/files/maarten_jan_kampen_obiee_mapviewer.pdf) in OBIEE10g. The integration in OBIEE10g was full of additional Javascripting. In OBIEE11g this has significantly improved. For the sake of his marriage, Tony didn't gave his holiday a different purpose, so he left his presentation based on 11.1.1.3. So maybe there are some more improvements in 11.1.1.5.

If you have your spatial metadata in order, the user should be capable to make his own spatial reports. Just by using the Map as an additional representation of the data, next to eg. the Pivot View. In OBI11g the spatial architecture is as follows;



	
  * Database (Locator could be enough, for extra manipulations on the data you will need an additional Spatial-license)

	
  * Oracle Mapviewer

	
  * Oracle Mapbuilder (or better Map Configurator)


Tony showed us several possibilities of building basemaps using the sample files from [Navteq](http://download.oracle.com/technology/products/bi/files/SampleApp_Navteq_dmp.zip) on OTN. You could also use Google Maps or Bing Maps. Using the Navtew files you could also create your own custom basemaps. Next to that Tony showed us a lot of possibilities of Spatial Integration in OBIEE11g, like



	
  * Locator Functions

	
  * Spatial Functions

	
  * Drilling (Master-Detail)

	
  * Navigating

	
  * Evaluate --> Spatial Functions


Already a lot to talk about and we were only half way!!
