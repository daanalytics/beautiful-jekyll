---
author: makumbe
comments: true
date: 2012-10-25 10:30:02+00:00
layout: post
link: http://blog.daanalytics.nl/2012/10/25/navigating-from-oracle-bi-11g-to-oracle-ebs-r12/
slug: navigating-from-oracle-bi-11g-to-oracle-ebs-r12
title: Navigating from Oracle BI 11g to Oracle eBS R12
wordpress_id: 1242
categories:
- Oracle BI 11g
tags:
- 11g
- Action Framework
- Navigation
- Oracle Business Analytics
- Oracle eBS
- R12
---

One of the interesting features of Oracle BI 11g is the [Action Framework](http://www.peakindicators.com/blog/obiee-11g-overview-of-action-framework_2). This feature makes it possible to e.g. navigate from Oracle BI 11g to Oracle eBS R12. When you have a look at the different Oracle BI(A) presentations from Oracle you will see a slide regarding Action Links 'Insight to Action'.

[![](http://obibb.files.wordpress.com/2012/10/oracle-bia-action-links-insight-to-action.png?w=300)](http://obibb.files.wordpress.com/2012/10/oracle-bia-action-links-insight-to-action.png)

It looks like this is standard Out-of-the-Box functionality. This is partly true. You should have at least the Oracle BI 11g & Oracle eBS R12 [integration](http://obibb.wordpress.com/2012/08/16/integrating-oracle-ebs-r12-and-oracle-bi-11g/) in place. Next to that there is some additional configuration / implementation required.

**Oracle BI configuration**



	
  * _Enable Action Link to Oracle eBS (ActionFrameworkConfig.xml)_


Navigate to the following location

ORACLE_MIDDLEWARE_HOME/user_projects/domains/bifoundation_domain/config/fmwconfig/biinstances/coreapplication

Edit the ActionFrameworkConfig.xml

[![](http://obibb.files.wordpress.com/2012/10/oracle-bi-action-framework-ebusinessuiteconfig1.png)](http://obibb.files.wordpress.com/2012/10/oracle-bi-action-framework-ebusinessuiteconfig1.png)

After you have modified the ActionframeworkConfig.xml file, you have to restart the Managed Server in Weblogic that is hosting your Oracle BI EE environment.



	
  * _Oracle BI Connection Pool_


Edit / Add a Connection Pool entry in the Oracle BI Administration Pool. This Connection Pool will be used to connect to Oracle BI Applications

**Note  **

I - the Application Role must have privileges to execute direct database requests against the Oracle eBS Connection Pool.

II -  for the Application Role (responsibility) to successfully invoke a Navigate to E-Business Suite action, the target Oracle eBS function must be accessible from the user's current Oracle eBS Context.

**Identify Oracle eBS Form Parameter**

If you want to navigate to a query the form you are navigating to, you should identify the Oracle eBS Form Parameter. This can be achieved by the following steps.

1. Log into Oracle eBS and select the Form you want to navigate to

2. Identify the name of the Form and the Function which calls this Form

Navigate to the Forms Personalization Screen via Help, Diagnostics, Custom Code, Personalize

[![](http://obibb.files.wordpress.com/2012/10/forms-parameter-apxinwkb-personalize.png?w=300)](http://obibb.files.wordpress.com/2012/10/forms-parameter-apxinwkb-personalize.png)



	
  * Forms

	
  * Function


[![](http://obibb.files.wordpress.com/2012/10/oracle-ebs-forms-personalization1.png?w=300)](http://obibb.files.wordpress.com/2012/10/oracle-ebs-forms-personalization1.png)

We will use the name of the Form to identify the possible parameters of this Form. In this case; [ ](http://obibb.files.wordpress.com/2012/10/oracle-ebs-forms-personalization1.png)APXINWKB. The Function Code will be used later on when creating the actual Action Link.

You can download the related .fmb-file from the Oracle eBS Application Server in the following location; $AU_TOP/forms/NL. The 'NL'-part refers to the language.

When you open the .fmb-file in Oracle Forms, you should be able to locate the parameters

**[![](http://obibb.files.wordpress.com/2012/10/forms-parameter-apxinwkb-invoice-id.png?w=300)](http://obibb.files.wordpress.com/2012/10/forms-parameter-apxinwkb-invoice-id.png)
**

**Action Link**

Now everything is in place to create the actual Action Link.



	
  * _Create Action Link_


Create the Action Link via New, Action, Navigate to E-Business Suite** **

**[![](http://obibb.files.wordpress.com/2012/10/oracle-bi-answers-new-action-navigate-to-oracle-ebs.png?w=300)](http://obibb.files.wordpress.com/2012/10/oracle-bi-answers-new-action-navigate-to-oracle-ebs.png)**



	
  * _Edit Action Link_


Now we must edit the specific Action Link details

[![](http://obibb.files.wordpress.com/2012/10/oracle-bi-answers-edit-action-navigate-to-oracle-ebs.png?w=300)](http://obibb.files.wordpress.com/2012/10/oracle-bi-answers-edit-action-navigate-to-oracle-ebs.png)

This consists of;



	
  * The Function Code (AP_APXINWKB_SUMMARY_VIEW)

	
  * The Oracle BI Connection Pool (Oracle EBS OLTP Connection Pool - Action Framework)

	
  * Parameter(s) --> INVOICE_ID


With this Action Link it is possible to call this link directly end fill in the Invoice Id yourself.

Another option is to make the Action Link part of an Oracle BI Answers Request.

	
  * _Edit Oracle BI Answers Request_


Select and edit a column in an Oracle BI Answers Request. Navigate to the Interaction Tab. Here we can add / edit an (existing) Action Link.

[![](http://obibb.files.wordpress.com/2012/10/oracle-bi-answers-action-link-example-navigation-to-oracle-ebs1.png?w=300)](http://obibb.files.wordpress.com/2012/10/oracle-bi-answers-action-link-example-navigation-to-oracle-ebs1.png)

I have chosen to use a Invoice Number with an Action Link which uses a hidden (Invoice Id) column to navigate to Oracle eBS. This way I do not have to show the Invoice Id in the Oracle BI Answers Request. Still I can use the Invoice Id as a parameter in the Oracle eBS Form.

It's a little bit of work, but still it's a nice feature.

- Daan
