---
author: makumbe
comments: true
date: 2015-04-23 08:00:27+00:00
layout: post
link: http://blog.daanalytics.nl/2015/04/23/introducing-oracle-analytics-cloud/
slug: introducing-oracle-analytics-cloud
title: Introducing Oracle Analytics Cloud
wordpress_id: 1893
categories:
- Oracle BI Cloud Service
tags:
- BICS
- Cloud
---

I recently joined Quistor as a Senior Oracle BI Consultant working from the Netherlands. Quistor already has an Oracle BI Practice working from Spain. As a well-respected Oracle BI Partner in Spain it only seemed logical to start expanding the Practice from the Netherlands. The place where it al has began for Quistor.

Why Quistor? I did not know Quistor as an Oracle BI Partner. It is a real challenge to help position Quistor as an important Oracle BI Partner, not only in Spain but also in the rest of Europe. Next to that Quistor has a real team of Oracle BI focused consultants, not bounded by any country borders.

One of the great things of working at Quistor is that we are willing to invest in new things. As an Oracle BI Partner it cannot have slipped your mind that Oracle is heavily investing in the Cloud. Oracle BI Cloud Services (BICS) is one of Oracle's focus areas. At Quistor we decided to buy our own BICS environment. At this moment we are in the course of developing and demonstrating our first Proof-of-Concepts (POC), both in Spain as well as in the Netherlands.

Next to these POCs it is great to mention that we are also working on a [Fixed Scope Offering](http://www.oracle.com/partners/en/partner-with-oracle/develop-solutions/fixed-scope-offering/index.html) (FSO) as well. It will only be a matter of time before we are added to the [Oracle Partner Network Solution Catalog](https://solutions.oracle.com/) with a FSO for BICS on JD Edwards as well. 



#### What is the Oracle Cloud?


There are three different consumption models when it comes to the Cloud;



	
  * 


Private




	
    * Customer buys / builds, hosts and manages





	
  * 


Managed




	
    * Customer buys / builds


	
    * Oracle manages against a monthly fee


	
    * Hosting depends - Can be the Customer as well as Oracle





	
  * 


Public




	
    * Oracle buys / builds, hosts and manages


	
    * Customer subscribes





![](http://obibb.files.wordpress.com/2015/04/042215_1159_introducing1.jpg)

As you can see the difference is who (customer or Oracle) is responsible for buying / building, hosting and managing the Cloud solution. It seems like Oracle has moved the complete Red-Stack to the Public Cloud. There are other Cloud competitors and there shall be better ones at this moment. Oracle is the only one who has an offering for the complete stack.









**Figure 1: Source Oracle**



At this moment Oracle offers the following 'as-a-Service'-solutions:



	
  * Data-as-a-Service


	
  * Infrastructure-as-a-Service


	
  * 


Platform-as-a-Service (Middleware)




	
    * Business Intelligence (and therefor BICS) is a Middleware Product


	
    * Also products like Oracle Database, Cloud Marketplace and Java





	
  * 


Application as a Service




	
    * Modules like Financials, HCM, CRM, etc.


	
    * Brand new but based on the existing Applications (Oracle eBS, JD Edwards, Peoplesoft and Siebel)








![](http://obibb.files.wordpress.com/2015/04/042215_1159_introducing3.png)

**Figure 2: Source Oracle
**

One of the reasons not to go for the Oracle Cloud (or any other Cloud solution) is the location of the data. Oracle has several Global Data Centers. The only Data Center with coverage for BICS is currently based in Chicago only. (US Commercial 2 - us2). Probably in June 2015 Amsterdam will be the proud owner of a Data Center with coverage for BICS as well.




#### What's driving the Cloud?




There are few factors, which make that we want to move to the Cloud:



	
  * Data Explosion (Datafication)


	
  * Mobility


	
  * Globalization


	
  * Social


	
  * Innovation (Modernization)





I have written a blog post about the Oracle (Business Analytics) Strategy earlier. One of the key focus points next to e.g. Mobile and Big Data is; Cloud. If you ask your customers, one of the main driver to evaluate a move to the Cloud is; Cost Reduction. You don't have to worry about your infrastructure, the maintenance of your environment nor the upgrade or customization of this environment. It's all taken care of by Oracle.

Next to the Cost Reduction, things like Performance, Innovation (It's not easy to keep up with the OBIEE On-Premise release schedule) and Risk are important topics where a move to the Cloud is considered. Oracle's current strategy regarding the Oracle BI Cloud is that all development is for the Cloud first. All major ne feature development goes to BICS first and than Oracle BI EE (OBIEE) On-Premise (+/- 6 months).

The current version of BICS is basically a light version of OBIEE in the Cloud. There is no support for things like Delivers (Agents), Scorecarding or BI Publisher yet. The Action Framework is limited in its options.

BICS will catch up very soon. The developments are going very fast (in a monthly cycle). Oracle divides its Roadmap in a few timeframes:

	
  * ![](http://obibb.files.wordpress.com/2015/04/042215_1159_introducing4.png)Today (current state)


	
  * 1-2 months (soon to be released)


	
  * 3-6 months,


	
  * 6 months







Check for more details on [http://oracle.cloud.com](http://oracle.cloud.com).



Patching will happen overnight during specific announced Maintenance Windows. You cannot stay more than one or two versions behind without a specific reason.




#### Introducing Oracle Analytics Cloud





During last years Open World, Oracle has introduced a whole set of new Cloud Services. Check the [Official Press Release](http://www.oracle.com/us/corporate/press/2313778?rssid=rss_ocom_pr) for more details. The Oracle Analytics Cloud delivers Business Intelligence & Analytics for Traditional Data and Big Data.







	
  * 


Oracle Business Intelligence Cloud Service (BICS)



	
  * 


Embedded Transactional Analytics for LoB SaaS users (OTBI)



	
    * 


[HCM Analytics](https://cloud.oracle.com/otbie_for_hcm)



	
    * 


[ERP Analytics](https://cloud.oracle.com/erp-analytics)



	
    * 


[SCM Analytics](https://cloud.oracle.com/scm-analytics)



	
    * 


[CRM Analytics](https://cloud.oracle.com/otbie_for_crm)






	
  * Deep, cross-source analytics for LoB users (OTBI-E)

	
  * [Oracle Big Data Discovery](https://cloud.oracle.com/bigdatadiscovery)

	
  * 


[Oracle Big Data in the Cloud](https://cloud.oracle.com/bigdata_saas)



As far as the OTBI (based on the Cloud Transactional Fusion Database) is concerned, you cannot modify anything. You are not abele to include external data. And then there is the issue of performance OTBI is based on a Transactional Database and not a DWH. As an alternative one can consider; BICS. Move a snapshot of the Fusion Database into the BICS Database.

OTBI Enterprise is a Pre-built Oracle BI Applications (OBIA) in the Cloud. Also in the cloud it's the same [Buy versus Build](http://www.oracle.com/us/solutions/business-intelligence/064094.pdf); 'Buy versus Build' as On-Premise (OBIEE / BICS vs. OBIA / OTBI-E).

In later posts I will deeper dive into what the Oracle Analytics Cloud has to offer. Believe me, it's interesting. Oracle is not there yet, but it really looks promising.

This post is available on the Quistor [Blog](http://www.quistor.com/nl/blog/entry/introducing-oracle-analytics-cloud-1) as well
