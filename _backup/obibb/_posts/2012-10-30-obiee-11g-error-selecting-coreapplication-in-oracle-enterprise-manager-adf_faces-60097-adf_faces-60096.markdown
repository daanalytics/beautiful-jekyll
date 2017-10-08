---
author: makumbe
comments: true
date: 2012-10-30 10:11:56+00:00
layout: post
link: http://blog.daanalytics.nl/2012/10/30/obiee-11g-error-selecting-coreapplication-in-oracle-enterprise-manager-adf_faces-60097-adf_faces-60096/
slug: obiee-11g-error-selecting-coreapplication-in-oracle-enterprise-manager-adf_faces-60097-adf_faces-60096
title: OBIEE 11g - Error selecting ''Coreapplication'' in Oracle Enterprise Manager
  (ADF_FACES-60097, ADF_FACES-60096)
wordpress_id: 1287
categories:
- Oracle BI 11g
tags:
- 11g
- ADF_FACES-60096
- ADF_FACES-60097
- Error
- Oracle Business Analytics
- Oracle Enterprise Manager
---

When we logged into Oracle Enterprise Manager (EM) and select 'Coreapplication' in the left pane , we encouter the error; "ADF_FACES-60097 : For more information, please see the server's error log for an entry beginning with: ADF_FACES-60096: Server Exception during PPR, #1"

This seems like a known bug so we followed the steps in Doc Id [1363602.1](https://support.oracle.com/epmos/faces/ui/km/SearchDocDisplay.jspx?_afrLoop=383309722234089&recommended=true&type=DOCUMENT&id=1363602.1&_afrWindowMode=0&_adf.ctrl-state=1bqm1xse8i_109). Unfortunately that didn't solve the problem.

Oracle Support advised us to increase the logging for the EM as shown in Doc ID [1464333.1](https://support.oracle.com/epmos/faces/ui/km/SearchDocDisplay.jspx?_afrLoop=383440459530683&recommended=true&type=DOCUMENT&id=1464333.1&_afrWindowMode=0&_adf.ctrl-state=1bqm1xse8i_130). This resulted in Error Logging in one of the AdminServer-diagnostic Log Files. A Fatal Error occurred reading this file: 'FMWhome/user_projects/domains/lnbisfoundation_domain/sysman/mds/partition1/ai/bi/fragments/mdssys/cust/user/weblogic/deployment.jspx.xml'

Investigating the structure of this file turned out that for some reason this file was empty (zero bytes). Removing the file and restarting the environment did the trick for us. The file got recreated and 'Coreapplication'  could be selected again.

[Update 09/14/2015 - FMWhome/user_projects/domains//sysman/mds/partition1/ai/bi/mdssys/cust/user//instance.jspx.xml
can also be zero bytes. A delete and a restart can fix the EM.]

- Daan
