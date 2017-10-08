---
author: makumbe
comments: true
date: 2010-10-11 08:45:20+00:00
layout: post
link: http://blog.daanalytics.nl/2010/10/11/solving-exp-00056-oracle-error-932-encountered/
slug: solving-exp-00056-oracle-error-932-encountered
title: 'Solving "EXP-00056: ORACLE error 932 encountered"'
wordpress_id: 477
categories:
- Oracle Errors
tags:
- 10g
- EXP-00056
- ORA-00932
- Oracle
---

When I was trying to export a schema out of an Oracle Database; 10g Release 10.2.0.1.0.

After a while I was faced with the following error; "EXP-00056: ORACLE error 932 encountered"

After a little bit of Googlin' I found a solution on the [Oracle OTN Forum](http://forums.oracle.com/forums/thread.jspa?threadID=572154). Thanks to 'slappyjam' I was able to solve my problem.

** Solution  **

Run following scripts while connected as SYS user:

[sourcecode language="sql"]
sqlplus /nolog
[/sourcecode]

[sourcecode language="sql"]
SQL> connect / as sysdba
SQL> @?/rdbms/admin/catmetx.sql
SQL> @?/rdbms/admin/utlrp.sql

SQL> exit
[/sourcecode]

The export ended succesfully; "Export terminated successfully without warnings"
