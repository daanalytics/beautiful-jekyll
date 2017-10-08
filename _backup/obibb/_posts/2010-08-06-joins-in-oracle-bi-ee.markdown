---
author: makumbe
comments: true
date: 2010-08-06 13:37:38+00:00
layout: post
link: http://blog.daanalytics.nl/2010/08/06/joins-in-oracle-bi-ee/
slug: joins-in-oracle-bi-ee
title: Joins in Oracle BI EE
wordpress_id: 340
categories:
- Modelling
tags:
- Join
- Logical Layer
- Oracle BI EE
- Physical Layer
---

There a lot of questions on the [Oracle Forums](http://forums.oracle.com/forums/forum.jspa?forumID=378&start=0), recently also, about join in Oracle BI EE. It seems like there are a lot of misconceptions about the use of joins in Oracle BI EE. 

There are two types of joins;



	
  * Foreign Key Join

	
  * Complex Join


[![](http://obibb.files.wordpress.com/2010/08/menu-bar.png?w=300)](http://obibb.files.wordpress.com/2010/08/menu-bar.png)

These joins could be applied to two different in layers;



	
  * Physical Layer

	
  * Logical Layer (Business Model)


 --> _When would you use which join?_

You can use both joins in both layers. There are some basic rules when it comes to using joins in Oracle BI EE.

In the Physical Layer, you should use Foreign Key joins, while in the Logical layer it’s common to use Complex Joins.

_--> __Why should you use these joins ?_

Physical Layer - Foreign Key Join

The Oracle BI Server uses the Foreign Key Joins to construct the where clause when selecting form multiple tables.

There are two types of keys in the Physical Layer:



	
  * Primary Key – Unique identifier of a single record in a table

	
  * Foreign Key – Reference to the Primary Key of another table


So basically the Foreign Key Join is a ‘Primary Key / Foreign Key’- relationship between two tables.

 There are situations where you could use Complex Joins in the Physical Layer.[ Jeff McQuigg ](http://greatobi.wordpress.com/2009/12/02/physical-layer-tips-and-gotcha%E2%80%99s/) has written a good blogpost about this subject.

Basically it comes down to the following three situations:



	
  * Range Joins

	
  * Data Type Conversion Joins

	
  * Cartesian Joins


Logical Layer – Complex Join

You use Complex Joins in the Logical Layer only to tell the Oracle BI Server that there is a link between the two tables. The Oracle BI Server should go to the Physical layer to see the actual link between the two tables.

A logical tabel consists of one or more Logical Table Sources. Multiple Logical Table Sources  lead to multiple join paths. Using a Foreign Key join in a situation where multiple join paths exists, restricts the Oracle BI Server only to use the specified join. Therefore it is common practice to use a Complex Join in the Logical Layer.

I hear you think; Why is the Foreign Key Join supported in the first place? It seems to only be there for backwards compatibility

In the Logical Layer you define Primary Keys as well. The purpose of a Primary Key in the Logical Layer is….



	
  * …to identify the Unique identifier of a single record in a Logical Table

	
  * … to identify the lowes level of detail of a Logical Table


