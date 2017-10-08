---
author: makumbe
comments: true
date: 2010-12-20 11:30:49+00:00
layout: post
link: http://blog.daanalytics.nl/2010/12/20/oracle-bi-applications-security/
slug: oracle-bi-applications-security
title: Oracle BI Applications - Security
wordpress_id: 641
categories:
- Oracle BI Applications
tags:
- 10g
- Oracle E-Business Suite
- R12
- Security
---

[](http://obibb.files.wordpress.com/2010/12/security-requirement1.jpg)[](http://obibb.files.wordpress.com/2010/12/cp-ebs-oltp.jpg)[](http://obibb.files.wordpress.com/2010/12/variable-manager.jpg)[](http://obibb.files.wordpress.com/2010/12/group.jpg)[](http://obibb.files.wordpress.com/2010/12/user-group-permissions.jpg)[](http://obibb.files.wordpress.com/2010/12/expression-builder.jpg)[](http://obibb.files.wordpress.com/2010/12/user-group-permissions.jpg)[](http://obibb.files.wordpress.com/2010/12/expression-builder.jpg)I recently had to digg into the standard Oracle BI Applications Security Oracle delivers out of the box. The clients had two security requirements.

The first one was a Data Security requirement. When a user logs in he is presented with his / her organization's data only. So a user from organization '001'  only sees data from organization '001' . Organization user '002' only sees organization '002' and so on.

The second requirement was Object Security. Each function has access to a group of objects, regardless of their organization. So all 'General Ledger Super Users' have access to the same objects whether they are in organization '001' or '002'

 [![](http://obibb.files.wordpress.com/2010/12/security-requirement1.jpg?w=300)](http://obibb.files.wordpress.com/2010/12/security-requirement1.jpg)

The client has the following installation:



	
  * Oracle eBS R12 (12.1.1)

	
  * Oracle BI Apps  (7.9.6)

	
  * Oracle BI EE (10.1.3.4.1)


In general the standard Oracle BI Applications security solution is built around;

	
  * Groups (Repository, Web Catalog)

	
  * Session Variables

	
  * Business Model Filters

	
  * Permissions

	
  * Priviliges


In more detail the following steps have to be performed:

**Set the application context**

The Oracle BI Applications session should get the same security context as Oracle eBS, where you navigate from.

[![](http://obibb.files.wordpress.com/2010/12/cp-ebs-oltp.jpg?w=300)](http://obibb.files.wordpress.com/2010/12/cp-ebs-oltp.jpg)

 During logon the ‘EBS Security Context’-Initialization Block is called and executed. The Oracle eBS session cookie is used to set the context. The Initialization block 'fills' the variables with information about which user / responsibility combination is logged on. These variable will be used in other Initialiation Blocks along the road.

[sourcecode language="sql"]
call APP_SESSION.validate_icx_session('valueof(NQ_SESSION.ICX_SESSION_COOKIE)')
[/sourcecode]

 If all goes well, the Oracle BI Apps session will get the same context as Oracle eBS. Otherwisse there are 3 options :



	
  * SESSION_DOES_NOT_EXIST,

	
  * SESSION_NOT_VALID,

	
  * SESSION_EXPIRED.


**Repository Groups[![](http://obibb.files.wordpress.com/2010/12/security-manager1.jpg?w=300)](http://obibb.files.wordpress.com/2010/12/security-manager1.jpg)**

There are two important Groups;



	
  * Responsibility Groups (Should the Responsibilities in Oracle eBS)

	
  * Security Groups (These will be used for the Data Security)  

	
    * --> Examples:

	
    * Ledger-based Security

	
    * Inventory Org-based Security

	
    * Operating Unit Org-based Security





** Variables**

The security group someone belongs to is detemined by session variables, which are set during logon.

[![](http://obibb.files.wordpress.com/2010/12/variable-manager.jpg?w=300)](http://obibb.files.wordpress.com/2010/12/variable-manager.jpg)

Initialization Blocks and Variables are the necessary objects to examine. If we relate to the example in the previous section, we could state that the following three Initialization Blocks are most important;
	
* Ledgers

	
* Inventory Organizations

	
* Operating Unit Organizations

 

**Data Security**

Data Security is being set up via, Security Groups and Business Model Filters.

 [![](http://obibb.files.wordpress.com/2010/12/group.jpg?w=224)](http://obibb.files.wordpress.com/2010/12/group.jpg)[![](http://obibb.files.wordpress.com/2010/12/user-group-permissions.jpg?w=300)](http://obibb.files.wordpress.com/2010/12/user-group-permissions.jpg)[![](http://obibb.files.wordpress.com/2010/12/expression-builder.jpg?w=300)](http://obibb.files.wordpress.com/2010/12/expression-builder.jpg)[](http://obibb.files.wordpress.com/2010/12/expression-builder.jpg)

As from now on, each query which is composited with a table linked to a Security Group a "Where-clause" is added.

**Presentation Catalog Groups**

The groups as they are created in the repository should also be created in the Web Catalog.

 [![](http://obibb.files.wordpress.com/2010/12/wc-manage-groups.jpg?w=300)](http://obibb.files.wordpress.com/2010/12/wc-manage-groups.jpg)

** Object Security**

You can use the Catalog Groups to grant or revoke acces to certain objects (Folders, Answers, Dashboards, etc) in the Web Catalog. The same groups an be used to mange the privilliges within the Web Catalog. Use the Security Groups in the Repository to control the Access to the Subject Area's in the Presentation Layer.

Check my previous [post](http://obibb.wordpress.com/2010/10/13/navigating-back-to-oracle-ebs-from-oracle-bi-ee/) about navigating from Oracle eBS to Oracle BI EE.
