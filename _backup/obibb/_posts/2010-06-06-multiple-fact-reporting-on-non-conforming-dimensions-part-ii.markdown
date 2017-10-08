---
author: makumbe
comments: true
date: 2010-06-06 13:43:38+00:00
layout: post
link: http://blog.daanalytics.nl/2010/06/06/multiple-fact-reporting-on-non-conforming-dimensions-part-ii/
slug: multiple-fact-reporting-on-non-conforming-dimensions-part-ii
title: Multiple Fact Reporting on (Non-)Conforming dimensions - Part II
wordpress_id: 146
categories:
- Logical Layer
tags:
- Conformed
- Dimension
- Facts
- Hierarchy
- Oracle BI EE
---

[](http://obibb.files.wordpress.com/2010/06/oracle-bi-answers-non-conformed-dimension-filtered1.png)[](http://obibb.files.wordpress.com/2010/06/oracle-bi-answers-non-conformed-dimension-filtered2.png)Last week I have been blogging about [Multiple Fact Reporting on (Non-)Conforming dimensions](http://obibb.wordpress.com/2010/05/31/multiple-fact-reporting-on-non-conforming-dimensions/)[](http://obibb.files.wordpress.com/2010/06/query-ii.png)[](http://obibb.files.wordpress.com/2010/06/excel-query-resultset.png). Thanks to [Nicolae](http://nicolaeancutabi.blogspot.com) I was triggered to do some further investigation on this topic. He had a [question](http://obibb.wordpress.com/2010/05/31/multiple-fact-reporting-on-non-conforming-dimensions/#comment-5); What happens when you want to filter on a non-conforming dimension?

When you filter an a non-conforming dimension, you could get a null value for the fact which has all the dimensions as conforming.


 [![](http://obibb.files.wordpress.com/2010/06/oracle-bi-answers-non-conformed-dimension-filtered2.png?w=300)](http://obibb.files.wordpress.com/2010/06/oracle-bi-answers-non-conformed-dimension-filtered2.png)




 


[](http://obibb.files.wordpress.com/2010/06/oracle-bi-answers-non-conformed-dimension-filtered1.png)

Is this not exactly how the Oracle BI-server works? We have created one logical fact table and two different logical table sources (LTS). The Oracle BI-server creates seperate queries for each LTS in a Oracle BI Answers query.

Query I:

[![](http://obibb.files.wordpress.com/2010/06/query-i.png?w=300)](http://obibb.files.wordpress.com/2010/06/query-i.png)

Query I connects fact table 1 to all the dimensions, including a filter on the non-conforming dimension.

Query II:

[![](http://obibb.files.wordpress.com/2010/06/query-ii.png?w=300)](http://obibb.files.wordpress.com/2010/06/query-ii.png)

Query II connects fact table 2 one to the conforming dimensions only. Because there is no physical relationship between fact table 2 and the non-conforming dimension, it is not possible to filter query II on  dtnc1.value3 = '3CCC3' as well.

The results of both queries:

[![](http://obibb.files.wordpress.com/2010/06/excel-query-resultset.png?w=300)](http://obibb.files.wordpress.com/2010/06/excel-query-resultset.png)

Lucky enough for me Nicolas did some investigating himself to:



	
  * Oracle BI EE Forum

	
    * [Filter on a dimension with a fact that don't depend on that dimension ](http://forums.oracle.com/forums/thread.jspa?messageID=3609020&#3609020)

	
    * [filter and non-conforming dimensions](http://forums.oracle.com/forums/thread.jspa?threadID=1075609&tstart=0)




	
  * Siebel IT Toolbox

	
    * [Two fact tables and non-conforming dimensions
](http://siebel.ittoolbox.com/groups/technical-functional/siebel-analytics-l/two-fact-tables-and-nonconforming-dimensions-3298529)





It looks like the most easy solution is to filter on the fact table which has all the dimensions as conforming. In this case, that would be; Fct1 Value1.

[![](http://obibb.files.wordpress.com/2010/06/oracle-bi-answers-non-conformed-dimension-filtered-is-null1.png?w=300)](http://obibb.files.wordpress.com/2010/06/oracle-bi-answers-non-conformed-dimension-filtered-is-null1.png)

I will try to ask some other sources what their solution is to this 'problem'.

More to come.
