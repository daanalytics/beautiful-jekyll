---
author: makumbe
comments: true
date: 2011-03-31 09:07:45+00:00
layout: post
link: http://blog.daanalytics.nl/2011/03/31/logical-sql-in-a-go-url/
slug: logical-sql-in-a-go-url
title: Logical Sql in a GO Url
wordpress_id: 839
categories:
- Oracle BI Dashboards
tags:
- 10g
- GO Url
- Logical SQL
---

There are a lot of good posts on how to us the GO Url functionlity in Oracle BI EE. One thing which isn't covered very often is the use of 'OR' in a prompted-GO Url.

If you want to filter sales <= 5000 or sales >= 15000 it seems not possible via the 'standard' GO Url structure. An alternative is using Logical Sql in the GO Url;

[sourcecode language="text"]
saw.dll?Go&SQL=select+Region,Dollars+from+SupplierSales
[/sourcecode]

In this case 'SupplierSales' is the Subject Area.

It is possible to add a where-clause to the select statement. I created the following example:

[![](http://obibb.files.wordpress.com/2011/03/logical-sql-dashboard.png)](http://obibb.files.wordpress.com/2011/03/logical-sql-dashboard.png)

[![](http://obibb.files.wordpress.com/2011/03/logical-sql-edit-dashboard.png)](http://obibb.files.wordpress.com/2011/03/logical-sql-edit-dashboard.png)

The first link contains a Go URL with Logical Sql.

[![](http://obibb.files.wordpress.com/2011/03/link-properties.png?w=300)](http://obibb.files.wordpress.com/2011/03/link-properties.png)

[sourcecode language="text"]
saw.dll?Go&SQL=SELECT+"Dim Time"."Calendar Month", "Fact Sales Amounts"."Sales Amount"+FROM+Sales
[/sourcecode]

The result of this link;

[![](http://obibb.files.wordpress.com/2011/03/output-logical-sql.png?w=186)](http://obibb.files.wordpress.com/2011/03/output-logical-sql.png)

The second link has a Go URL also, but this one includes Logical Sql with a where-clause.

[sourcecode language="text"]
saw.dll?Go&SQL=SELECT+"Dim Time"."Calendar Month", "Fact Sales Amounts"."Sales Amount"+FROM+Sales+WHERE+"Fact Sales Amounts"."Sales Amount"+<=+5000+OR+"Fact Sales Amounts"."Sales Amount"+>=+15000
[/sourcecode]

The result of this second link;

[![](http://obibb.files.wordpress.com/2011/03/output-logical-sql-incl-where-clause.png)](http://obibb.files.wordpress.com/2011/03/output-logical-sql-incl-where-clause.png)

Unfortunately these forms of the Go URL return tabular results only.
