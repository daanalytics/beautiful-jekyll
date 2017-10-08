---
author: makumbe
comments: true
date: 2014-05-09 13:30:07+00:00
layout: post
link: http://blog.daanalytics.nl/2014/05/09/rm-bi-forum-2014-notes-day-i/
slug: rm-bi-forum-2014-notes-day-i
title: RM BI Forum 2014 Notes - Day I
wordpress_id: 1685
categories:
- RittmanMead BI Forum
tags:
- biforum2014
- Rittman Mead BI Forum
---

## RM BI Forum 2014 Notes - Day I


Find below some notes, links, etc regarding day I of the RittmanMead BI Forum 2014. These are just some notes and it's by no means a re-cap of the complete presentations. Check the RittmanMead [blog](http://www.rittmanmead.com/blog/) after the Atlanta edition of the RittmanMead BI Forum 2014. They will post all the presentations (both Brighton as well as Atlanta).


### **Extreme Intelligence by**** [Emiel van Bockel](https://twitter.com/bifacts)**


Emiel started the day where he took us on a journey with regards to the [Exalytics](http://www.oracle.com/us/solutions/ent-performance-bi/business-intelligence/exalytics-bi-machine/overview/index.html) implementation @ [CB Logistics](http://www.cb-logistics.nl/eng/home/). Exalytics is one of the [Engineered Systems](http://www.oracle.com/us/products/engineered-systems/index.html) Oracle has.

An Engineered System is not a Plug ’n Play Environment. It needs to be Engineered. Only start engineering when you are sure system works.

Know your system (understand your data)

Do not use the wizards, but use your head/experience. Do it yourself.

If done right you own your own Extreme Intelligence System. The best in the world!


### **Times Ten Best Practice and Optimization by**** [Chris Jenkins](http://uk.linkedin.com/in/chrisdjenkins)**


Chris who is Senior Director, In-Memory Technology, TimesTen Development at Oracle gave us some very detailed insight into Oracle Times Ten.

OS Configuration

Shared Memory Segment

Huge Page considerations

Semaphores

Save storage (inline - out of line) by comparing Data Types between an Oracle Database and the Times Ten Database

Compression

Loading Times Ten via.....



	
  * [Oracle DAC](http://docs.oracle.com/cd/E36909_01/fusionapps.1111/e14849/timesten.htm)

	
  * ODI


[Incremental refresh](http://www.rittmanmead.com/2013/01/incremental-refresh-exalytics-aggregates-using-timesten/)

Parallelism

Performance Optimisation



	
  * BI optimiser hints

	
  * statistics

	
  * indexes ([Index Advisor](http://download.oracle.com/otn_hosted_doc/timesten/1122/quickstart/html/admin/index_advisor.html))




### ** ****OBIEE Performance in the Real World by [Robin Moffat](https://twitter.com/rmoff)**


Evidence based Design and Diagnostics

Create Time Profile - "Nose to Tail” —> Which component (OBIEE, Weblogic, Network, Database, etc.) is causing trouble.

Dive into the NQQuery Log - Query Logging is not evil! Check for more details [here](http://www.rittmanmead.com/2012/05/obiee-performance-tuning-myth-bi-server-logging/).

DMS metrics ([obi-metrics-agent](http://www.rittmanmead.com/2014/03/introducing-obi-metrics-agent-an-open-source-obiee-metrics-collector/))

Grafana - Public live demo [online](http://play.grafana.org/)

Must Read - "[Thinking Clearly about Performance](http://carymillsap.blogspot.co.uk/2010/02/thinking-clearly-about-performance.html)"


### **Oracle BI Cloud by [Adam Bloom](http://obibb.wordpress.com/wp-admin/uk.linkedin.com/pub/adam-bloom/1/55/696)**


Sort of NDA, but it will be there……the [Oracle BI Cloud](https://cloud.oracle.com/business_intelligence)

Oracle invests heavily in the Cloud. As a part of that a lot of new interesting Oracle BI functionality will become available in the Cloud first. Hopefully these functionalities will arrive on Premise shortly after.


### **Extreme Data Warehousing by [Paul Oprea](https://twitter.com/paul_oprea)**


A lot of discussion about [Agile](http://agilemanifesto.org/) and Waterfall.One ting is important; Keep the user engaged and involved!


### **A Picture Can Replace A Thousand Words by [Michael Rainey](https://twitter.com/mRainey)**


Using pictures to vizualize the process will help in getting the requirements clear.

[BPMN](http://www.bpmn.org)


### **About the Oracle DW Global Leaders Program by [Reiner Zimmerman](https://www.linkedin.com/pub/reiner-zimmermann/2/33b/32a)**


**[http://www.oracle.com/technetwork/database/bi-datawarehousing/oracle-dw-global-leaders-brochure-345526.pdf](http://www.oracle.com/technetwork/database/bi-datawarehousing/oracle-dw-global-leaders-brochure-345526.pdf)**


###  **Enterprise Big Data Architecture by [Andrew Bond](https://www.linkedin.com/pub/andrew-bond/3/693/4a2) & [Stewart Bryson](http://www.rittmanmead.com/author/stewart-bryson/)**


Oracle Information Management Reference [Architecture](http://www.oracle.com/technetwork/topics/entarch/articles/info-mgmt-big-data-ref-arch-1902853.pdf)

Discovery Lab

Foundation Layer - (Raw) Data Reservoir - Golden Gate  -> Mapping Physical to Logical (OBIEE) - No ETL, yet

Data Factory (ETL)

Enterprise Information Store

Event Engine

Data Ingestion

Information Interpretation

Agile Manifesto

Model Driven Development - Sandbox

Generate Logical Model Documentation (OBIEE)

Access and Performance Layer

Refactoring - Solve challenges in the Front-End. Working report -> Then move down to RPD or ETL

[TDWI Chicago 2013 Keynote: Big Data, Bigger Impact](https://www.youtube.com/watch?v=xKrw2TKfj4w)

