---
author: makumbe
comments: true
date: 2013-07-18 10:55:00+00:00
layout: post
link: http://blog.daanalytics.nl/2013/07/18/validating-the-group-account-mapping-in-oracle-bia-7963/
slug: validating-the-group-account-mapping-in-oracle-bia-7963
title: Validating the Group Account Mapping in Oracle BIA 7963
wordpress_id: 1407
categories:
- Oracle BI Applications
tags:
- 7.9.6.3
- Financial Analytics
- General Ledger
- Oracle BIA
---

Configuring Oracle BIA is one of the crucial steps when implementing Oracle BIA. If you omit this step or you perform this step incorrectly, you won't see the correct figures in your Oracle BIA Dashboards. One of the major steps is the [Group Account Mapping](http://docs.oracle.com/cd/E20490_01/bia.7963/e19039/anyimp_oracle_apps.htm#CHDFGCFA).

For Oracle eBS installations, you probably won't (at least not here in the Netherlands) use the Group Accounts in e.g. the Balance Sheet. It's more likely that custom GL hierarchies are used. Nevertheless it is essential/crucial that the Group Account Mapping is performed correctly. Oracle BIA will use this Group Account Mapping to decide e.g. whether a record should go an AR-Fact table or to AP.

As a Technical OBIA Implementation Consultant I would advice you to consult a Functional eBS Implementation Consultant to perform the Group Account Mapping. If you still want to have a look at it yourself, you could have a look at the Account Segment Hierarchy in Oracle BIA, to see whether you can map Parents of the Accounts to Group Accounts. This might give you some more insight in the ranges you will need.

In the end, if you want to check whether the Group Account Mapping is correctly executed, you can use the Oracle BIA out-of-the-Box Financial Dashboard. Navigate to the 'Financials - General Ledger'-Dashboard. Select either the 'GL Balance'- or the 'Trial Balance'-page. Filter on Group Account Number; values 'NULL' & 'OTHERS'. If an Account isn't mapped to a Group Account, the Oracle BIA ETL automatically maps the Account to 'OTHERS'. Check whether the analysis returns Accounts and still map these Accounts.
