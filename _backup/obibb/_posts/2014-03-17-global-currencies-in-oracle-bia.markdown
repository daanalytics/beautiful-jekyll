---
author: makumbe
comments: true
date: 2014-03-17 11:23:23+00:00
layout: post
link: http://blog.daanalytics.nl/2014/03/17/global-currencies-in-oracle-bia/
slug: global-currencies-in-oracle-bia
title: Global Currencies in Oracle BIA
wordpress_id: 1542
categories:
- Oracle BI Applications
tags:
- Currency
- DAC
- Informatica
- OBIA
- Oracle eBS
---

If you read the [Oracle Documentation](http://docs.oracle.com/cd/E20490_01/bia.7963/e19039/anyimp_oracle_apps.htm#BABJJJHF) for Oracle BIA (7.6.9.3), you could find the following; "Currency conversions are required because your business might have transactions involving multiple currencies. To create a meaningful report, you have to use a common currency."

Oracle BIA stores amounts in the following currencies;

- Document Currency --> Currency of the actual Transaction (Can vary in a multinational organization)
- Local Currency --> Currency defined in the Ledger
- Global Currency --> Defined in the DAC

You can use a Global Currency if you want to report all the different Currencies in one Global Currency (eg. 'EUR', or 'USD'). Oracle BIA for Oracle eBS is able to report in 3 different Global Currencies. If you use Oracle BIA for CRM, you are able to store an additional two Global Currencies. You define the Global Currencies in the DAC.

- $$GLOBAL1_CURR_CODE
- $$GLOBAL2_CURR_CODE
- $$GLOBAL3_CURR_CODE

You will have to define a Global Rate Type for each Global Currency as well.

- $$GLOBAL1_RATE_TYPE (for the first global currency)
- $$GLOBAL2_RATE_TYPE (for the second global currency)
- $$GLOBAL3_RATE_TYPE (for the third global currency)

[![DAC - Currency - Rate - Parameters](http://obibb.files.wordpress.com/2014/03/dac-currency-rate-parameters.png?w=300)](http://obibb.files.wordpress.com/2014/03/dac-currency-rate-parameters.png)

You would use the above DAC Parameters for a Document Currency to Global Currency Conversion ($$GLOBALn_CURR_CODE & $$GLOBALn_RATE_TYPE). The $$DEFAULT_LOC_RATE_TYPE-Parameter is used for the Document Currency to Local Currency Conversion.

To get a better understanding about how these Conversions work, you should try to understand the; 'MPLT_CURCY_CONVERSION_RATES'-Mapplet. The purpose of this Mapplet is to; "Find the Conversion Rate for a given Currency Code, Rate Type and Exchange date. You should find this mapping in the Out-of-the-Box SILOS-Folder.

[![Informatica - Mapplet - MPLT_CURCY_CONVERSION_RATES - Diagram](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates-lkp_w_exch_rate-diagram.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates-lkp_w_exch_rate-diagram.png)

In the 'MPLT_CURCY_CONVERSION_RATES'-Mapplet you will find an Expression; 'EXPT_CALC_EXCH_RATES.' This 'EXPT_CALC_EXCH_RATES'-Expression is responsible for the actual Conversion (Calculation).

[![Informatica - Mapplet - MPLT_CURCY_CONVERSION_RATES - EXPT_CALC_EXCH_RATES](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates-expt_calc_exch_rates.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates-expt_calc_exch_rates.png)

There are a few other Mapplets with similar name and functionality compared to the 'MPLT_CURCY_CONVERSION_RATES'-Mapplet.

The Conversion for eg. the GLOBAL1_EXCHANGE_RATE basically consists of three components:

- Input from a Mapping (eg. SIL_APInvoiceDistributionFact - W_AP_INV_DIST_F)
- Lookup to the W_GLOBAL_CURR_G-Table
- Lookup to the W_EXCH_RATE_G-Table

[![Informatica - Mapplet - MPLT_CURCY_CONVERSION_RATES - EXPT_CALC_EXCH_RATES - Calculate Rate](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates-expt_calc_exch_rates-calculate-rate.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates-expt_calc_exch_rates-calculate-rate.png)

_Input from a Mapping_

The 'MPLT_CURCY_CONVERSION_RATES'-Mapplet is part of a Mapping. Let's take the 'SIL_APInvoiceDistributionFact'-Mapping which populates the 'W_AP_INV_DIST_F'-Table as an example.

[![Informatica Mapping - SIL_APInvoiceDistributionFact](http://obibb.files.wordpress.com/2014/03/informatica-mapping-sil_apinvoicedistributionfact.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-mapping-sil_apinvoicedistributionfact.png)

_Lookup to the W_GLOBAL_CURR_G-Table_

The 'SILGlobalCurrencyGeneral_Update'-Mapping in the 'SILOS'-folder stores the values of the  to the $$GLOBALn_CURR_CODE-, and $$GLOBALn_RATE_TYPE-DAC-Parameters in the W_GLOBAL_CURR_G-Table.

[![W_GLOBAL_CURR_G - Currency - Rate](http://obibb.files.wordpress.com/2014/03/w_global_curr_g-currency-rate.png?w=300)](http://obibb.files.wordpress.com/2014/03/w_global_curr_g-currency-rate.png)

As you can see the values in the W_GLOBAL_CURR_G-Table, match with the values in the DAC-Parameters. Of course you can setup these Parameters anyway you like.

_Lookup to the W_EXCH_RATE_G-Table_

The W_EXCH_RATE_G is a Table which resembles the GL_DAILY_RATE-Table in Oracle eBS. If the contents of this Table are incomplete or incorrect, the whole setup of the different Currencies is useless. The 'LKP_W_EXCH_RATE'-Lookup is used to find the Conversion Rate for a given Currency Code ('From' and 'To') and Exchange Date .

[![Informatica - Mapplet - MPLT_CURCY_CONVERSION_RATES - LKP_W_EXCH_RATE - Complete](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates-lkp_w_exch_rate-complete.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-mapplet-mplt_curcy_conversion_rates-lkp_w_exch_rate-complete.png)



If you query the  'W_AP_INV_DIST_F'-Table an you find the 'GLOBAL1_EXCHANGE_RATE'-Column empty for a certain Transaction, the above should help you find out the reason.

Good Luck.
