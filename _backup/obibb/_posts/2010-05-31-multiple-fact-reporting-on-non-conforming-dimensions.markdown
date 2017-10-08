---
author: makumbe
comments: true
date: 2010-05-31 16:05:08+00:00
layout: post
link: http://blog.daanalytics.nl/2010/05/31/multiple-fact-reporting-on-non-conforming-dimensions/
slug: multiple-fact-reporting-on-non-conforming-dimensions
title: Multiple Fact Reporting on (Non-)Conforming dimensions
wordpress_id: 80
categories:
- Logical Layer
tags:
- Conformed
- Dimension
- Facts
- Hierarchy
- OBIEE
---

****

**Update 31 August 2017**

Although published about 7 years ago, this subject still seems a source of questions. To understand the concepts of Oracle BI (OBIEE) better, it is good to check out the following blogposts as well. They will link to other blogs ["Don’t forget the Logical Layer"](http://blog.daanalytics.nl/2014/10/14/dont-forget-the-logical-layer/) & ["Going to the core of Oracle Analytics"](http://blog.daanalytics.nl/2017/06/22/going-to-the-core-of-oracle-analytics/) and will help you better understand the basis of OBIEE. This basis is an absolute must to get the most out of OBIEE.

****

There are some questions, which are popping up at the Oracle BI EE Forums regularly. One of those questions is;

**_*** How to model multiple facts against (non-) conforming dimensions? _**

I will try to work things out. Click on the images to see more detail.

Note: I am aware of the extra white space between the images. That's not intended functionality, but lack of knowledge of  Wordpress.

Picture the following:

There are two fact tables and three dimension tables. FACT_TABLE_1 has two conformed dimension tables; DIM_TABLE_CONF_1 and DIM_TABLE_CONF_2 and one non-conformed dimension table DIM_TABLE_NON_CONF_1.

FACT_TABLE_2 has two conformed dimension tables; DIM_TABLE_CONF_1 and DIM_TABLE_CONF_2.

The Physical Model would have the following structure:

[caption id="attachment_105" align="alignnone" width="300"][![](http://obibb.files.wordpress.com/2010/05/physical-diagram.png?w=300)](http://obibb.files.wordpress.com/2010/05/physical-diagram.png) Physical Diagram[/caption]

Based on the Physical Model we could construct the following Logical Model:

[caption id="attachment_107" align="alignnone" width="300"][![](http://obibb.files.wordpress.com/2010/05/logical-diagram.png?w=300)](http://obibb.files.wordpress.com/2010/05/logical-diagram.png) Logical Diagram[/caption]

I have created one fact table which contains Logical Table Sources (LTS) for FACT_TABLE_1 and FACT_TABLE_2

[caption id="attachment_108" align="alignnone" width="300"][![](http://obibb.files.wordpress.com/2010/05/logical-model.png?w=300)](http://obibb.files.wordpress.com/2010/05/logical-model.png) Logical Model[/caption]

As you can see I have created Dimensions (Hierarchy’s) for each Dimension Table.

FACT_TABLE_2 has no physical relationship with DIM_TABLE_NON_CONF_1. Therefore you should set the logical levels for FACT_TABLE_2 to the ‘Grand Total’-level of DIM_TABLE_NON_CONF_1. This way the Oracle BI Server won’t look for a join between DIM_TABLE_NON_CONF_1 and FACT_TABLE_2.

If you want to avoid nulls, set the detail levels for the facts. Set the ‘Grand Total’-levels for the metrics as well.

[caption id="attachment_109" align="alignnone" width="300"][![](http://obibb.files.wordpress.com/2010/05/logical-table-source-fact-i.png?w=300)](http://obibb.files.wordpress.com/2010/05/logical-table-source-fact-i.png) Logical Table Source - Fact I[/caption]

[caption id="attachment_111" align="alignnone" width="300"][![](http://obibb.files.wordpress.com/2010/05/logical-table-source-fact-ii.png?w=300)](http://obibb.files.wordpress.com/2010/05/logical-table-source-fact-ii.png) Logical Table Source - Fact II[/caption]

[caption id="attachment_106" align="alignnone" width="300"][![](http://obibb.files.wordpress.com/2010/05/logical-column-fact-ii.png?w=300)](http://obibb.files.wordpress.com/2010/05/logical-column-fact-ii.png) Logical Column - Fact II[/caption]

If we take a look at Oracle BI Answers, we can create a report which contains data from the following tables;



	
  * DIM_TABLE_CONF_1

	
  * DIM_TABLE_CONF_2

	
  * FACT_TABLE_1

	
  * FACT_TABLE_2


[caption id="attachment_113" align="alignnone" width="300"][![](http://obibb.files.wordpress.com/2010/05/oracle-bi-answers-conformed-dimension.png?w=300)](http://obibb.files.wordpress.com/2010/05/oracle-bi-answers-conformed-dimension.png) Oracle BI Answers - Conformed Dimension[/caption]

Now we can bring data from DIM_TABLE_NON_CONF_1 into this report. It is impossible to devide data from FACT_TABLE_2 over this dimension. Therefore the data will be the same for every value of this dimension.

[caption id="attachment_112" align="alignnone" width="300"][![](http://obibb.files.wordpress.com/2010/05/oracle-bi-answers-non-conformed-dimension.png?w=300)](http://obibb.files.wordpress.com/2010/05/oracle-bi-answers-non-conformed-dimension.png) Oracle BI Answers - (Non-) Conformed Dimension[/caption]

**_*** Summary:_**

**_ _**It's possible to report on facts and dimensions which not have a physical relationship to each other. Just make sure you create dimensions (hierarchy’s) for every dimension table. Next to that you should set the logical levels for your logical tables.
