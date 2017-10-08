---
author: makumbe
comments: true
date: 2014-03-27 11:30:07+00:00
layout: post
link: http://blog.daanalytics.nl/2014/03/27/global-currencies-in-oracle-bia-the-sequel/
slug: global-currencies-in-oracle-bia-the-sequel
title: Global Currencies in Oracle BIA - The Sequel
wordpress_id: 1571
categories:
- Oracle BI Applications
tags:
- Currency
- DAC
- Oracle BIA
---

I have [blogged](http://obibb.wordpress.com/2014/03/17/global-currencies-in-oracle-bia/) about Global Currencies in Oracle BIA recently. Global Currencies are used to report in different Currencies like USD, GBP, EUR. If you use the Global Currencies to report the same Currencies (eg. EUR) against different Exchange Rate (Types) you might end up with a challenge, because the Out-of-the-Box Oracle BIA ETL expects different Currency Codes.

If you take eg. the; 'MPLT_CURCY_CONVERSION_RATES_ToGlobalCurrenciesOnly'-Mapplet, you will notice the;  'DOC_TO_GLOBAL2_EXCH_RATE_OUT'-Port. This Port is based on the; 'DOC_TO_GLOBAL2_EXCH_RATE_VAR'-Port.

![Informatica - Mapplet - MPLT_CURCY_CONVERSION_RATES_ToGlobalCurrenciesOnly - DOC_TO_GLOBAL2_EXCH_RATE_VAR](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates_toglobalcurrenciesonly-doc_to_global2_exch_rate_var.png?w=630)

If you further analyze the expression in the; 'DOC_TO_GLOBAL2_EXCH_RATE_VAR'-Port, you can see that it's made up of a few different checks.

[![DOC_TO_GLOBAL2_EXCH_RATE_VAR](http://obibb.files.wordpress.com/2014/03/doc_to_global2_exch_rate_var-e1395826685426.png)](http://obibb.files.wordpress.com/2014/03/doc_to_global2_exch_rate_var-e1395826685426.png)

1. If GLOBAL2_CURR_CODE = NULL then populate GLOBAL2_EXCH_RATE = NULL

2. If previous condition(s) not satisfied, then; If GLOBAL2_CURR_CODE = GLOBAL1_CURR_CODE then populate GLOBAL2_EXCH_RATE = GLOBAL1_EXCH_RATE

3. If previous condition(s) not satisfied, then; If GLOBAL2_CURR_CODE = DOC_CURR_CODE, then populate GLOBAL2_EXCH_RATE = 1.0

4. If previous condition(s) not satisfied, then; If DOC_CURR_CODE = ‘STAT’, then populate GLOBAL2_EXCH_RATE = 1.0

5. If previous condition(s) not satisfied, then; If GLOBAL2_CURR_CODE = LOC_CURR_CODE, then populate GLOBAL2_EXCH_RATE = DOC_TO_LOC_EXCHANGE_RATE_VAR else lookup on W_EXCH_RATE_G on the condition (DOC_CURR_CODE, GLOBAL2_CURR_CODE, EXCH_DT, GLOBAL2_RATE_TYPE_VAR, DATASOURCE_NUM_ID). The output of this Lookup is used to populate the; GLOBAL2_EXCH_RATE.

In the case of the same Global Currencies (eg. EUR) the execution of the above expression will stop at condition 2 and populate the GLOBAL2_EXCH_RATE-column with the value of GLOBAL1_EXCH_RATE. Although this behavior seems logical from an Oracle BIA perspective, it might not be satisfying as you cannot compare GLOBAL1_EXCH_RATE with GLOBAL2_EXCH_RATE.

In this case you will end up with a customization on the; the; 'MPLT_CURCY_CONVERSION_RATES_ToGlobalCurrenciesOnly'-Mapplet. The easiest way is to copy the logic in the; DOC_TO_GLOBAL1_EXCH_RATE_VAR'-Port and apply it to the DOC_TO_GLOBAL2_EXCH_RATE_VAR'-Port. Of course you have to replace the references to; 'GLOBAL1' with; 'GLOBAL2'.

[![DOC_TO_GLOBAL1_EXCH_RATE_VAR](http://obibb.files.wordpress.com/2014/03/doc_to_global1_exch_rate_var.png)](http://obibb.files.wordpress.com/2014/03/doc_to_global1_exch_rate_var.png)


