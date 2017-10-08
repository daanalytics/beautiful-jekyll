---
author: makumbe
comments: true
date: 2014-05-12 10:54:29+00:00
layout: post
link: http://blog.daanalytics.nl/2014/05/12/rm-bi-forum-2014-notes-day-ii/
slug: rm-bi-forum-2014-notes-day-ii
title: RM BI Forum 2014 Notes - Day II
wordpress_id: 1716
categories:
- RittmanMead BI Forum
tags:
- biforum2014
- Rittman Mead BI Forum
---

## RM BI Forum 2014 Notes - Day II


Find below some notes, links, etc regarding day I of the RittmanMead BI Forum 2014. These are just some notes and it's by no means a re-cap of the complete presentations. Check the RittmanMead [blog](http://www.rittmanmead.com/blog/) after the Atlanta edition of the RittmanMead BI Forum 2014. They will post all the presentations (both Brighton as well as Atlanta)


### Drawing in a New Rock on the Map – How will Endeca Fit in to Your Oracle BI Topography by [Truls Bergersen](https://twitter.com/trulsbergersen)


Data Discovery
- Unknown Answers to Unknown Questions
- New Datasources

Hybrid search/analytical database
Key Value Pairs
In-Memory Analytics

[Self-Service Provisioning](https://www.youtube.com/watch?v=2MGqOFyJ3bo) - (Excel, [JSON](http://www.json.org)-Files, OBIEE Data Source)

[Web Acquisition Toolkit](https://www.youtube.com/watch?v=rXXWHCXqHG4)

ODI KM - Integration Knowledge Module

Sentiment Analysis (only via Integrator tier) - Lexical (Dictionary)

Oracle eBS [extensions](https://www.youtube.com/watch?v=B_WJzR46ek0&list=PLEOdbv_Kaxnuz04M7neeMnNc9nseQioKS) for Endeca (light-weight Oracle BI Apps)


### Real-time Data Warehouse Upgrade – Success Stories by [Nicholas Hurt](https://twitter.com/Nicholas_Hurt) & [Michael Rainey](https://twitter.com/mRainey)


Events —> ETL --> Cleanse --> De-dupe --> Summarize --> Dashboard
Streams & Oracle CDC —> Oracle [GoldenGate](http://www.oracle.com/technetwork/middleware/goldengate/overview/index.html?ssSourceSiteId=otncn) (Journalizing - ODI)
OWB —> ODI 11g - 3R’s- Re-Asses, Replicate, Refine existing mappings

JMK Oracle to Oracle Consistent (OGG) Knowledge Module

Oracle Information Management Reference [Architecture](http://www.oracle.com/technetwork/topics/entarch/articles/info-mgmt-big-data-ref-arch-1902853.pdf)

Staging Layer -
Performance Layer (Dimensional Model - Star Schema)
Hybrid Layer

[Real-time BI: An Introduction](http://www.rittmanmead.com/2011/05/real-time-bi-an-introduction/)

[GoldenGate and ODI – A Perfect Match for Real-Time Data Warehousing](http://www.rittmanmead.com/2013/02/goldengate-and-oracle-data-integrator-a-perfect-match-part-1/)


### **Oracle BI Cloud by [Matt Bedin](https://www.linkedin.com/pub/matt-bedin/0/a42/a31)**


Sort of NDA, but it will be there……the [Oracle BI Cloud](https://cloud.oracle.com/business_intelligence)

Oracle invests heavily in the Cloud. As a part of that a lot of new interesting Oracle BI functionality will become available in the Cloud first. Hopefully these functionalities will arrive on Premise shortly after.


### Essbase within/without OBIEE – not just an aggregation engine by [Gianni Ceresa](https://twitter.com/G_Ceresa)


Essbase and OBIEE Aggregate Pesistance [wizard](http://www.rittmanmead.com/2012/09/improvements-to-essbase-integration-in-obiee-11-1-1-6-2-bp1-aso-aggregate-persistence-combined-install-systems-management/)

Essbase Studio

[ASO](http://www.oracle.com/technetwork/issue-archive/2010/10-sep/o50bi-165473.html) (Aggregate Storage Option)
BSO (Block Storage Option)

CalcScripts

[UDF](http://docs.oracle.com/cd/E12825_01/epm.111/esb_dbag/frameset.htm?dcaudfs.htm) - User Defined Functions
Essbase Writeback


### Speed up RPD Development by [Marco Klaassens](http://nl.linkedin.com/pub/marco-klaassens/0/453/672)


Speedup Delivering = Knowledge * Focus * Offering


### Neo’s Voyage in OBIEE by [Christian Berg](https://twitter.com/Nephentur)


Blue Pill - It’s Known
Red Pill - It’s Undocumented (Use at own risk)

NQS Procedures as Physical Tables (ODBC) in the Physical Layer

Contact Christian directly, he might want to share.


<blockquote>Anybody who wants my [#biforum2014](https://twitter.com/search?q=%23biforum2014&src=hash) slides, RPD etc contact me directly

— Christian Berg (@Nephentur) [May 9, 2014](https://twitter.com/Nephentur/statuses/464775168892866560)</blockquote>







### Tuning TimesTen with Aggregate Persistence by [Alistair Burgess ](https://twitter.com/alastairburgess)




[Aggregates Persistance Wizard](http://www.oracle.com/webfolder/technetwork/tutorials/obe/fmw/bi/bi11117/agp/agr.html)







Tuning TimesTen








	
  * RangeIndexType=0

	
  * TimesTen Data Types (TT_INTEGER, TT_SMALLINT)

	
  * RAM Policy

	
  * Compression

	
  * [Index Advisor](http://www.rittmanmead.com/2013/08/optimizing-timesten-for-exalytics-queries-using-the-timestens-index-advisor/)

	
  * Execute on Connect

	
  * Parallel Query







Licence costs (compared to the Oracle Database) could be interesting
