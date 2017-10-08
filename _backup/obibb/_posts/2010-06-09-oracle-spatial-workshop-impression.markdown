---
author: makumbe
comments: true
date: 2010-06-09 10:11:12+00:00
layout: post
link: http://blog.daanalytics.nl/2010/06/09/oracle-spatial-workshop-impression/
slug: oracle-spatial-workshop-impression
title: Oracle Spatial Workshop - Impression
wordpress_id: 169
categories:
- OBIBB - General
---

Last week we had an Oracle Spatial Workshop at Scamander. The goal of the evening was to highlight a fundamental different technique in the Oracle database.
Instead of the usual WHERE-clause and JOIN syntaxis the database provides a set of similar tools but based on the spacial technique.

For the attendants it proved to be very descriptive to be able to execute an insert-statement and to display the result with the push of a button.

The relative simple techniques addressed was enough to show that this is a very different technique and requires a different point of view on data. Just as the “regular” SQL-toolset in the Oracle database, this is a complex and broad topic.

We used [Oracle Spatial tools](http://www.oracle.com/technology/products/database/sql_developer/index.html). Mapviewer serves for the display of maps with navigation and other functionality, but we need something to compile the maps, layers, styles, etc.  For that purpose Oracle provides for a tool called Mapbuilder (source: [Oracle Wiki](http://wiki.oracle.com/page/Spatial+Tools)[](http://obibb.files.wordpress.com/2010/06/circle1.png)[](http://obibb.files.wordpress.com/2010/06/vierkant-union-circle.png)[](http://obibb.files.wordpress.com/2010/06/buffer1.png)[](http://obibb.files.wordpress.com/2010/06/adressen.png)[](http://obibb.files.wordpress.com/2010/06/select-adressen.png))

To give an example:

** INSERT Vierkant (square)


 [![](http://obibb.files.wordpress.com/2010/06/vierkant.png?w=300)](http://obibb.files.wordpress.com/2010/06/vierkant.png)




[![](http://obibb.files.wordpress.com/2010/06/insert-vierkant.png?w=300)](http://obibb.files.wordpress.com/2010/06/insert-vierkant.png)




** INSERT Circel (circle)


 [![](http://obibb.files.wordpress.com/2010/06/circle1.png?w=300)](http://obibb.files.wordpress.com/2010/06/circle1.png)

[![](http://obibb.files.wordpress.com/2010/06/insert-circle.png?w=300)](http://obibb.files.wordpress.com/2010/06/insert-circle.png)

** INSERT  the Union of the two inserted objects (square, circle)** **

[![](http://obibb.files.wordpress.com/2010/06/vierkant-union-circle.png?w=300)](http://obibb.files.wordpress.com/2010/06/vierkant-union-circle.png)

[![](http://obibb.files.wordpress.com/2010/06/insert-vierkant-union-circle.png?w=300)](http://obibb.files.wordpress.com/2010/06/insert-vierkant-union-circle.png)

** ** **CREATE a buffer around the UNION:

[![](http://obibb.files.wordpress.com/2010/06/buffer1.png?w=300)](http://obibb.files.wordpress.com/2010/06/buffer1.png)

[![](http://obibb.files.wordpress.com/2010/06/create-buffer.png?w=300)](http://obibb.files.wordpress.com/2010/06/create-buffer.png)

** SELECT addresses within the square:

** [![](http://obibb.files.wordpress.com/2010/06/adressen.png?w=300)](http://obibb.files.wordpress.com/2010/06/adressen.png)**

[![](http://obibb.files.wordpress.com/2010/06/select-adressen.png?w=300)](http://obibb.files.wordpress.com/2010/06/select-adressen.png)

It was nice to have a visual representation of the subject; Oracle Spatial. We are certainly no experts at this time like Maarten Jan, but we have a good impression of what the capabilities of Oracle Spatial are.

Next time we will make a link between Oracle Spatial and Oracle BI EE. Hopefully we can use Oracle BI 11g for that.

**Useful Links**



	
  * [Index](http://download.oracle.com/docs/cd/B14117_01/appdev.101/b10826/index.htm)

	
  * [Toc](http://download.oracle.com/docs/cd/B14117_01/appdev.101/b10826/toc.htm)

	
  * [Spatial operators](http://download.oracle.com/docs/cd/B13789_01/appdev.101/b10826/sdo_operat.htm#BGEDACIF)

	
  * [Spatial aggregate functions](http://download.oracle.com/docs/cd/B14117_01/appdev.101/b10826/sdo_aggr.htm)

	
  * [Spatial Data Types and Metadata](http://www.filibeto.org/sun/lib/nonsun/oracle/10.1.0.2/B14117_01/appdev.101/b10826/sdo_objrelschema.htm)

	
  * [SDO_GEOM Package (Geometry)](http://web.deu.edu.tr/doc/oracle/B19306_01/appdev.102/b14255/sdo_objgeom.htm#i856140)


[](http://web.deu.edu.tr/doc/oracle/B19306_01/appdev.102/b14255/sdo_objgeom.htm#i856140)
