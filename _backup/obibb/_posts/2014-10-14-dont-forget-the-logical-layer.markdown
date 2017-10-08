---
author: makumbe
comments: true
date: 2014-10-14 10:30:34+00:00
layout: post
link: http://blog.daanalytics.nl/2014/10/14/dont-forget-the-logical-layer/
slug: dont-forget-the-logical-layer
title: Don't forget the Logical Layer
wordpress_id: 1773
categories:
- Logical Layer
tags:
- 11g
- OBIEE
- Repository
---

I often see OBIEE RPD's which are developed via "Drag 'n Drop". If you know what you are doing this hasn't necessarily have to be a problem. It becomes a problem if you do not know what you are doing. Especially dragging and dropping multiple tables together can give you additional 'functionality', which you do not need. Sometimes you are not even aware that you added additional links and keys, you don't need. It becomes even worse when it's 'functionality' you don't want. I know from experience that it can cause incorrect results, depending on the columns you select in your analysis.

Normally I build my Logical Models manually from scratch instead of via "Drag 'n Drop". This way I know exactly what I am doing and I don't get surprised by unintended functionality. This is by no means a 'Best Practice', but it works for me. Let's consider it to be a '[Right Practice](http://www.scaleabilities.co.uk/2011/09/16/right-practice/)'.

There is another reason for avoiding a "Drag 'n Drop and leave the Logical Layer like that"-Construction of the Logical Layer. The Logical Layer is an important part in the construction of the actual Physical Query(s). The Oracle BI Server does not have to be a Black Box. You just need to give the Oracle BI Server as much information as possible so you know / understand, what query(s) the Oracle BI Server will fire to the underlying database(s). Pay attention to the following recommendations:



	
  * Dimension Logical Tables must have a Logical Key assigned, if possible a business related key (order number, purchase number, employee number). Fact Logical Table do not have a Logical Key assigned

	
  * Fact Logical Tables contain Measure Columns with an Aggregation Rule (SUM, COUNT, MIN, MAX, etc.) applied to it.

	
  * Define a Dimension Hierarchy for every Dimension Logical Table

	
    * Each Level is unique

	
    * The Primary Key of the lowest Level matches the Primary Key of the Logical Table

	
    * Specify the number of element per Level




	
  * Specify the Content Level for each Logical Table (Column)

	
    * Each Content Level 'belongs' to a Level in the Dimension Hierarchie




	
  * Construction of the Logical Table

	
    * (Re-) Naming Conventions

	
    * Only those columns you really need





The above listing is by no means exhaustive. There are few interesting links you can check out, when it comes to modeling the Logical Layer;

	
  * Using OBIEE and Data Vault to Virtualize Your BI Environment: An Agile Approach

	
  * [Using OBIEE against Transactional Schemas](http://www.rittmanmead.com/2013/03/obiee-transactional5/)

	
  * [Advanced MetaData Topics](https://obibb.files.wordpress.com/2017/06/mcquigg_metadata.pdf)

	
  * [Oracle BI Server – the ultimate choice for BICC’s – Decoupling](https://obibb.files.wordpress.com/2017/06/wilcke_bicc.pdf)

	
  * [OBIEE 11.1.1 - BI Design Best Practices Whitepaper V1.5](https://blogs.oracle.com/pa/entry/obiee_11_1_1_bi3)


One important [note](http://hekatonkheires.blogspot.nl/2014/07/think-and-understand-before-you-give.html) has been made by Christian Berg; "**Think** and **Understand** before you give **'Advice'**". The same goes when you are trying to apply things yourself. Don't just do it, because you can. Do it because you understand why you have to do it that way.

Feel free to comment.
