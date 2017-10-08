---
author: makumbe
comments: true
date: 2012-10-29 10:25:46+00:00
layout: post
link: http://blog.daanalytics.nl/2012/10/29/solving-ora-01722-invalid-number-while-navigating-from-oracle-bi-11g-to-oracle-ebs-r12/
slug: solving-ora-01722-invalid-number-while-navigating-from-oracle-bi-11g-to-oracle-ebs-r12
title: Solving ORA-01722 - Invalid Number while navigating from Oracle BI 11g to Oracle
  eBS R12
wordpress_id: 1277
categories:
- Oracle BI 11g
tags:
- 11g
- Action Framework
- Connection Pool
- Oracle Business Analytics
---

[
](http://obibb.files.wordpress.com/2012/10/servererror-navigation.png)In a previous [blog post](http://wp.me/pVzHx-k2), I covered how to navigate from Oracle BI 11g to Oracle eBS R12. While setting this up, I had some challenges to overcome. One of them was the following. When I clicked the column with the Action Link, the following error showed up;

[![](http://obibb.files.wordpress.com/2012/10/servererror-navigation.png?w=300)](http://obibb.files.wordpress.com/2012/10/servererror-navigation.png)

The Oracle eBS Server was available, so that couldn't be the problem. Checking the logfile(s) showed that there was a ORA-01722 error involved.

The question at this point is; Which query is throwing a 'Invalid Number'-error. Thanks to [Robin ](http://rnm1978.wordpress.com/2011/02/02/instrumenting-obiee-for-tracing-oracle-db-calls/)I got the idea to Sql Trace the Connection Pool which is being used for the Action Link.

[![](http://obibb.files.wordpress.com/2012/10/oracle-ebs-oltp-connection-pool-action-framework.png?w=300)](http://obibb.files.wordpress.com/2012/10/oracle-ebs-oltp-connection-pool-action-framework.png)

Via the generated Trace Files I was able to identify the problem - query. It turned out to be the query which constructs the Url to navigate to Oracle eBS.

[sourcecode language="sql"]
select fnd_run_function.get_run_function_url
 ( cast
 ( fnd_function.get_function_id ( 'AP_APXINWKB_SUMMARY_VIEW' ) as number )
 , cast ( '200.00' as number )
 , cast ( '*****' as number )
 , cast ( '0.00' as number )
 , 'INVOICE_ID=*****'
 , null ) as action_link
 from DUAL
[/sourcecode]

A quick check in SQL*Plus gave the same error. The problem is in the Cast functions and the NLS_NUMERIC_CHARACTERS-settings.

An easy;

[sourcecode language="sql"]
ALTER SESSION SET NLS_NUMERIC_CHARACTERS = '.,' ;
[/sourcecode]

..... solved the problem in SQL*Plus.

In Oracle BI, I added the 'Alter Session'-Statement in the Connection Pool which is being used for the Action Link.

[![](http://obibb.files.wordpress.com/2012/10/oracle-ebs-oltp-connection-pool-action-framework-alter-session-statement.png?w=300)](http://obibb.files.wordpress.com/2012/10/oracle-ebs-oltp-connection-pool-action-framework-alter-session-statement.png)

Problem Solved.

- Daan
