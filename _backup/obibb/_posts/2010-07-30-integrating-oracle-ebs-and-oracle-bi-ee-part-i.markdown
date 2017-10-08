---
author: makumbe
comments: true
date: 2010-07-30 12:00:30+00:00
layout: post
link: http://blog.daanalytics.nl/2010/07/30/integrating-oracle-ebs-and-oracle-bi-ee-part-i/
slug: integrating-oracle-ebs-and-oracle-bi-ee-part-i
title: Integrating Oracle eBS and Oracle BI EE - Getting started
wordpress_id: 307
categories:
- Oracle eBS
tags:
- Oracle BI EE
- R12
---

I have been playing around with Oracle eBS Release 12 and Oracle BI EE 10g. 

In Release 12 the integration is very straight forward. If you would like to achieve the same functionality in Release 11, you need to do some patching first.

Lucky enough for me I am able to use an Release 12 environment.

[sourcecode language="sql"]
select release_name
from   applsys.fnd_product_groups
[/sourcecode]

All I had to do was set the 'FND: Oracle Business Intelligence Suite EE base URL'-profile in Oracle eBS.

[![](http://obibb.files.wordpress.com/2010/07/fnd-oracle-business-intelligence-suite-ee-base-url.png?w=300)](http://obibb.files.wordpress.com/2010/07/fnd-oracle-business-intelligence-suite-ee-base-url.png)

[![](http://obibb.files.wordpress.com/2010/07/fnd-oracle-business-intelligence-suite-ee-base-url-value.png?w=300)](http://obibb.files.wordpress.com/2010/07/fnd-oracle-business-intelligence-suite-ee-base-url-value.png)

This would be something like; **[http://[hostname.domain_name]:[port_number](http://[hostname.domain_name]:[port_number)]**

statement:

[sourcecode language="sql"]
select fnd_profile.value('FND_OBIEE_URL') oracle_bi_url
from   dual
[/sourcecode]

Now Oracle eBS nows where to find Oracle BI.

Secondly I had to change the way Oracle BI authenticates in the instanceconfig.xml file. This way you can login to Oracle BI via Oracle eBS. You use your Oracle eBS credentials to login to Oracle BI directly.

[sourcecode language="xml"]
   <Auth>
   <ExternalLogon enabled="true">
      <ParamList>
      <Param name="NQ_SESSION.ICX_SESSION_COOKIE"
         source="cookie"
         nameInSource="VIS"/>
      <Param name="NQ_SESSION.ACF"
         source="url"
         nameInSource="acf"/>
      </ParamList>
   </ExternalLogon>
   </Auth>  
[/sourcecode]

Last but not least, you change your connection settings in the Repository of Oracle BI and you are good to go.

If you would like to see how the integration between Oracle eBS and Oracle BI works, I can recommend a blogpost of [Gerard Braat](http://www.beyeblogs.com/eyeonbi/archive/2007/06/oracle_bi_fusion_intelligence.php).

[Robin Moffat](http://rnm1978.wordpress.com/2010/05/17/validating-ebs-bi-authentication-without-bi/) has written a good explanation about how to validate EBS-BI authentication, without BI.
