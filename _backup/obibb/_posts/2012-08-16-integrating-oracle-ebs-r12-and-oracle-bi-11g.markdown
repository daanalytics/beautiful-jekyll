---
author: makumbe
comments: true
date: 2012-08-16 07:22:02+00:00
layout: post
link: http://blog.daanalytics.nl/2012/08/16/integrating-oracle-ebs-r12-and-oracle-bi-11g/
slug: integrating-oracle-ebs-r12-and-oracle-bi-11g
title: Integrating Oracle eBS R12 and Oracle BI 11g
wordpress_id: 1176
categories:
- Oracle eBS
tags:
- 11g
- Oracle BI EE
- Oracle E-Business Suite
- R12
---

I have made a [blogpost](http://obibb.wordpress.com/2010/07/30/integrating-oracle-ebs-and-oracle-bi-ee-part-i/) in the past about integrating Oracle eBS R12 and Oracle BI 10g. In the course of an upgrade of Oracle BI Applications (OBIA) to OBIA 7.9.6.3, I came to the subject of integrating  Oracle eBS R12 and Oracle BI 11g. Of course you should start with the [documentation](http://docs.oracle.com/cd/E23943_01/bi.1111/e16364/ebs_actions.htm#CJADIFBA). Next to that, Oracle provides a note on [Oracle Support](https://support.oracle.com/epmos/faces/ui/km/DocumentDisplay.jspx?_afrLoop=554928375146425&id=1343143.1&_afrWindowMode=0&_adf.ctrl-state=103mymztio_97) (**ID 1343143.1**). A lot of integration steps are equal to the 10g version.

**In short:**

There are two sides (Oracle eBS & Oracle BI) where you need to make some preparations.

**Oracle eBS:**

You need to define the link from to Oracle eBS to Oracle BI. This functionality hasn't changed and I have described that process [here](http://obibb.wordpress.com/2010/08/05/integrating-oracle-ebs-and-oracle-bi-ee-links/). Combined with the ‘FND: Oracle Business Intelligence Suite EE base URL’-profile option in Oracle eBS, you now are ready to navigate from Oracle eBS to Oracle BI.

**Oracle BI:**

Now the Oracle eBS side is ready, you'll have to prepare Oracle BI for accepting login requests from Oracle eBS. This parts differs a little from 10g. The changes in the Repository are still the same and consist of validation of the ICX-cookie in the Oracle eBS Connection Pool and the Authentication via Session variables. You can choose to either authenticate via the GROUP- system variable or directly via the new 11g ROLES-system variable.

After that you need to change the Oracle BI configuration;



	
  * authenticationschemas.xml (ORACLE_HOME/bifoundation/web/display)




[![authenticationschemas.xml (SchemaKeyVariable)](http://obibb.files.wordpress.com/2012/08/authenticationschemas_xml_schemakeyvariable1.jpg)](http://obibb.files.wordpress.com/2012/08/authenticationschemas_xml_schemakeyvariable1.jpg)[
](http://obibb.files.wordpress.com/2012/08/authenticationschemas_xml_schemakeyvariable1.jpg)




[![authenticationschemas.xml](http://obibb.files.wordpress.com/2012/07/authenticationschemas_xml.jpg)](http://obibb.files.wordpress.com/2012/07/authenticationschemas_xml.jpg)






	
  * instanceconfig.xml (ORACLE_INSTANCE/config/OracleBIPresentationServicesComponent/coreapplication_obips1)




[![instanceconfig.xml](http://obibb.files.wordpress.com/2012/07/instanceconfig_xml.jpg)](http://obibb.files.wordpress.com/2012/07/instanceconfig_xml.jpg)[
](http://obibb.files.wordpress.com/2012/07/instanceconfig_xml.jpg)




**Note:** Don't get mislead by the following sentence; '<!--This Configuration setting is managed by Oracle Enterprise Manager Fusion Middleware Control-->'. You must adjust these settings directly in the instanceconfig.xml itself.


This should (all) be sufficient to log into Oracle BI via a selected responsibility in Oracle.

In a following post I will cover the subject of applying Data Security in Oracle BI, based on the Oracle eBS Responsibility.
