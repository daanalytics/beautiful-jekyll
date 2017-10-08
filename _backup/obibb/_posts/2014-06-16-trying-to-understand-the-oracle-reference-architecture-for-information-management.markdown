---
author: makumbe
comments: true
date: 2014-06-16 07:49:07+00:00
layout: post
link: http://blog.daanalytics.nl/2014/06/16/trying-to-understand-the-oracle-reference-architecture-for-information-management/
slug: trying-to-understand-the-oracle-reference-architecture-for-information-management
title: Trying to understand the Oracle Reference Architecture for Information Management
wordpress_id: 1736
categories:
- Oracle Business Analytics
tags:
- Big Data
- Information Management
- Oracle Business Analytics
- Reference Architecture
---

Last month I have been attending the RittmanMead BI Forum 2014. In the [wrap-up](http://obibb.wordpress.com/2014/05/13/rittmanmead-bi-forum-2014-wrap-up/) I mentioned a presentation by [Andrew Bond](https://www.linkedin.com/pub/andrew-bond/3/693/4a2) & [Stewart Bryson](http://www.rittmanmead.com/author/stewart-bryson/). They had a very nice presentation about the [Oracle Information Management Reference Architecture.](http://www.rittmanmead.com/files/bryson_bond_ref_arch.pdf) This needed some further investigation from my part.

This blogpost is a first summary of the information I found online so far.

There is a complete reference library of [**IT Strategies from Oracle**](www.oracle.com/goto/itstrategies). Pay extra attention to the following docs:



	
  * Oracle Reference Architecture Information Management

	
  * Oracle Reference Architecture Business Analytics Foundation

	
  * Oracle Reference Architecture Business Analytics Infrastructure

	
  * Oracle Reference Architecture Service Orientation

	
  * Oracle Reference Architecture Security

	
  * Oracle Reference Architecture Engineered Systems


[![IT Strategies from Oracle](http://obibb.files.wordpress.com/2014/06/it-strategies-from-oracle.png?w=300)](https://obibb.files.wordpress.com/2014/06/it-strategies-from-oracle.png)

Next to that, Oracle has a few White Papers focussing on Information Management (Big Data & Analytics):



	
  * [Enabling Pervasive BI through a Practical Data Warehouse Reference Architecture](http://www.oracle.com/technetwork/database/bi-datawarehousing/twp-bidw-enabling-pervasive-bi-thro-132094.pdf) - Feb 2010

	
  * [Information Management and Big Data A Reference Architecture](http://www.oracle.com/technetwork/topics/entarch/articles/info-mgmt-big-data-ref-arch-1902853.pdf) - Feb 2013

	
  * [Big Data & Analytics Reference Architecture](http://www.oracle.com/technetwork/topics/entarch/oracle-wp-big-data-refarch-2019930.pdf) - Sep 2013




### Oracle Information Management – Logical View


Let's take a closer look, see the picture below. This picture has been copied from; the [Oracle Information Management Reference Architecture.](http://www.rittmanmead.com/files/bryson_bond_ref_arch.pdf) presentation I mentioned above. There are a few major components in the Reference Architecture



	
  * Data Sources

	
  * Information Provisioning

	
    * Data Ingestion

	
    * Logical Data Warehouse




	
  * Information Delivery


While putting together this blog post, Mark Rittman posted the following article(s); "Introducing the Updated Oracle / Rittman Mead Information Management Reference Architecture - Pt1. Information Architecture and the "Data Factory" & Pt2. – Delivering the Data Factory” on the [RM Blog](http://www.rittmanmead.com/2014/06/introducing-the-updated-oracle-rittman-mead-information-management-reference-architecture-pt1-information-architecture-and-the-data-factory/).

[![Oracle Information Management – Logical View](http://obibb.files.wordpress.com/2014/06/oracle-information-management-e28093-logical-view1-e1401893213260.png?w=630)](https://obibb.files.wordpress.com/2014/06/oracle-information-management-e28093-logical-view1.png)


#### Data Sources


Within this Reference Architecture Oracle should be able to handle all sorts of data:



	
  * Traditional Enterprise Data (ERP, CRM, etc.)

	
  * Machine-generated /Sensor Data (Smart Meters, Equipment Logs, etc.)

	
  * Social Data (Twitter, Facebook, etc.)


[![Any Data - Any Source - Any Format - Different Data](http://obibb.files.wordpress.com/2014/06/any-data-any-source-any-format-different-data.png?w=300)](https://obibb.files.wordpress.com/2014/06/any-data-any-source-any-format-different-data.png)

The last couple of years / decades, Data has changed. We (as BI/DW-Consultants) have always looked at data in a Traditional (Structured) way. Now Oracle provides an Architecture to combine the old Data with the new (Big) Data. Whether there are 3, 4, 5, or whatever number of V's, the most important thing is that you [get value from your Data](https://www.linkedin.com/today/post/article/20140306073407-64875646-big-data-the-5-vs-everyone-must-know)!


#### Data Ingestion (Loading)


Oracle provides / supports tools to perform Batch or (Near) Real-Time Data Ingestion.

_**Oracle GoldenGate & Oracle Data Integrator**_

Michael Rainey is writing an excellent series on how to load the Raw Data Reservoir (Staging Layer) and the Foundation Layer; [Oracle GoldenGate and Oracle Data Integrator – A Perfect Match in 12c](http://www.rittmanmead.com/2014/05/goldengate-odi-perfect-match-12c-1/).

_**Cloudera Distribution including Apache Hadoop (CDH)**_

Hadoop is Open Source and [Apache](http://hadoop.apache.org) licensed. Cloudera provides an Open Source Distribution ( Cloudera CDH -[ Cloudera Enterprise Data Hub](http://www.cloudera.com/content/cloudera/en/products-and-services/cdh.html)).

_**Oracle Event Processing (OEP)**_

OEP is a complete solution for building applications to filter, correlate and process events in real-time. Check the Data Sheet [here](http://www.oracle.com/us/products/middleware/soa/overview/complex-event-processing-ds-066411.pdf).


#### Logical Data Warehouse


There are a few different Layers:



	
  * Raw Data Reservoir (Staging Layer)

	
  * Foundation Layer

	
  * Access and Perfomance Layer


Depending on the requirements and the tooling one can decide to skip or combine the different Layers. Oracle has the tooling to load the various Layers directly ([GoldenGate](http://www.oracle.com/us/products/middleware/data-integration/goldengate/overview/index.html)).

The data is no longer only stored in the Oracle Database. The 'new' types of data require 'new' types of storage. There are different Data Stores for different purposes.



	
  * Historical (Historical Integrity)

	
    * [Oracle Database](http://www.oracle.com/us/products/database/overview/index.html)

	
    * [HBase](http://hbase.apache.org)

	
    * [HDFS](http://wiki.apache.org/hadoop/HDFS)

	
    * [Oracle NoSql Database](http://www.oracle.com/technetwork/database/database-technologies/nosqldb/overview/index.html)






	
  * Analytical (Ease of Acces & Query Performance)

	
    * Oracle Database

	
      * [OLAP](http://www.oracle.com/technetwork/database/options/olap/index.html)

	
      * [Spatial & Graph](http://www.oracle.com/technetwork/database/options/spatialandgraph/overview/index.html)




	
    * Oracle Essbase

	
    * [Oracle NoSql Database](http://www.oracle.com/technetwork/database/database-technologies/nosqldb/overview/index.html)

	
    * [Cloudera Hadoop](http://www.cloudera.com/content/cloudera/en/products-and-services/cloudera-enterprise.html)

	
    * [Oracle Endeca Information Discovery](http://www.oracle.com/technetwork/middleware/endeca/overview/index.html?ssSourceSiteId=otnpt)





The [Oracle Big Data Connectors](http://www.oracle.com/technetwork/database/database-technologies/bdc/big-data-connectors/overview/index.html) can be used to integrate Apache Hadoop with Oracle Database Software.



	
  * Oracle Loader for Hadoop

	
  * [Oracle Data Integrator Application Adapter for Hadoop](http://www.oracle.com/us/products/middleware/data-integration/hadoop/overview/index.html?ssSourceSiteId=ocomcaen)

	
  * Oracle R Advanced Analytics for Hadoop

	
  * Oracle SQL Connector for HDFS

	
  * Oracle XQuery for Hadoop


Processing the data could be either In-Database ([Oracle Database Options](http://www.oracle.com/technetwork/database/options/index.html?ssSourceSiteId=null) -  Advanced Analytics, OLAP) or In-Memory ([Oracle TimesTen](http://www.oracle.com/technetwork/database/database-technologies/timesten/overview/index.html)).


#### Information Delivery


Oracle is able to support proven answers to known questions via [Oracle BI](http://www.oracle.com/us/solutions/business-analytics/business-intelligence/overview/index.html). Fast answers to new questions are provided by [Oracle Endeca Information Discovery](http://www.oracle.com/technetwork/middleware/endeca/overview/index.html?ssSourceSiteId=otnpt).

"The Oracle BI Foundation Suite provides comprehensive capabilities for business intelligence, including enterprise reporting, dashboards, ad-hoc analysis, multi-dimensional OLAP, scorecards, and predictive analytics on an integrated platform"

[![Oracle BI Foundation - Front-End](http://obibb.files.wordpress.com/2014/06/oracle-bi-foundation-front-end1.png?w=300)](https://obibb.files.wordpress.com/2014/06/oracle-bi-foundation-front-end1.png)

OBIEE makes it possible (Logical Layer) to skip the 'Access and Perfomance Layer' and source directly form the 'Foundation Layer'. There are some very interesting presentations online around this subject.



	
  * [Using OBIEE and Data Vault to Virtualize Your BI Environment: An Agile Approach](https://s3.amazonaws.com/rmc_docs/odtug2013_datavault.pdf)

	
  * [Using OBIEE against Transactional Schemas](http://www.rittmanmead.com/2013/03/obiee-transactional5/)

	
  * [Advanced MetaData Topics](https://s3.amazonaws.com/rmc_docs/biforum2011/Mcquigg_Metadata.pdf)

	
  * [Oracle BI Server - the ultimate choice for BICC's - Decoupling](https://s3.amazonaws.com/rmc_docs/biforum2011/Wilcke_BICC.pdf)


"Oracle Endeca Information Discovery is a complete enterprise data discovery platform that combines information of any type, from any source, empowering business user independence in balance with IT governance. Now organizations can access the information they need, when they need it, to make business decisions they can trust."

There is still a lot more to investigate, but for me this gives a little bit more guidance.
