---
author: makumbe
comments: true
date: 2013-05-09 07:00:25+00:00
layout: post
link: http://blog.daanalytics.nl/2013/05/09/rm-bi-forum-2013-notes-oracle-data-integrator-master-class/
slug: rm-bi-forum-2013-notes-oracle-data-integrator-master-class
title: RM BI Forum 2013 Notes - Oracle Data Integrator Master Class
wordpress_id: 1337
categories:
- RittmanMead BI Forum
tags:
- ODI
- Oracle Data Integrator
- Rittman Mead BI Forum
---

Today the RittmanMead BI Forum 2013 started with an Oracle Data Integrator Master Class provided by (in alphabetical order)  [Mark Rittman](http://www.rittmanmead.com/author/mark-rittman/), [Michael Rainey](http://www.rittmanmead.com/author/michael-rainey/) and [Stewart Bryson](http://www.rittmanmead.com/author/stewart-bryson/).


I made some notes, so I'll try to highlight some points from the Master Class. It won't be complete, but it gives an indication. I didn't know much about ODI, so the start of the Master Class was very welcome to me.








  



**Overview by Stewart Bryson**








  



Just in time for [Oracle BIA 11.1.1.7](http://obibb.wordpress.com/2013/05/07/oracle-business-intelligence-applications-11-1-1-7-ga-on-otn/) - everything [ODI](http://www.rittmanmead.com/2012/12/odi11g-in-the-enterprise-part-2-data-integration-using-essbase-messaging-and-big-data-sources-and-targets/), bye, bye Informatica and DAC (DAC translated into configuration and packaging and load plans).





  

Further integration with Oracle Weblogic and the Fusion Middleware





  



ODI & OBI Jive really good together. Abstraction of physical Sources logic built into the model not the process. Same like OBI. Develop the model, not the query. Metadata. See the the similarity between ODI and OBI.





  



Scripting becomes Groovy with ODI  (see later on).





  



Everything you do in ODI goes via Agents







OCI versus JDBC --> ETL versus E-LT (insert into select)





  



Develop once in the Model instead of in the interface / mapping. Interface inherits from the model, override if needed. Interconnect interfaces via yellow temporary interfaces





  



Knowledge Modules (KM) -  the physical implementation of the logic




How to load is determined by the KM, E-LT or ETL





  



Packaging (sequencing) versus [Load Plans](http://www.oracle.com/technetwork/issue-archive/2012/12-sep/o52bi-1735905.html)


  









**Goldengate and ODI by Michael Rainey**


  









Oracle Reference Architecture for Information Management and Big Data - [2013 Whitepaper](http://www.oracle.com/technetwork/topics/entarch/articles/info-mgmt-big-data-ref-arch-1902853.pdf)





  



Oracle Goldengate - Data Replication





  



CDC Journalizing in ODI - Journalizing Knowledge Module ([JKM](http://docs.oracle.com/cd/E15586_01/integrate.1111/e12645/intro.htm#CEGGBHEH))


  






Goldengate uses the JKM....generated metadata and a readme how to apply. No full integration





  



RMAN redo log, archive log , cleaning the logs





  



Parent Child Journalizing two different tables via two interfaces into the same target table





  



Subscription Views a RM feature to provide a choice for the ETL developer to choose which object to use





  



Oracle Goldengate and ODI are a [Perfect Match](http://www.rittmanmead.com/2013/02/goldengate-and-oracle-data-integrator-a-perfect-match-part-1/)





  






**ODI and Big Data by Mark Rittman**










If you do not care about a single row you refer to Big Data




Decisions based on your own data vs decisions based on all data relevant to you





  



Oracle [Big Data](http://www.oracle.com/uk/technologies/big-data/index.html)





  



Terminology





  



- [Hadoop](http://hadoop.apache.org) -- [http://wiki.apache.org/hadoop/PoweredBy](http://wiki.apache.org/hadoop/PoweredBy)




- [MapReduce](http://hadoop.apache.org/docs/r1.0.4/mapred_tutorial.html)




- [HDFS](http://hadoop.apache.org/docs/r1.0.4/hdfs_design.html)




- [Hive](http://hive.apache.org)





  



ODI (or OBIEE) to connect the Hadoop world to the traditional DWH world via the Hive.





  



[HiveODBC](https://support.oracle.com/epmos/faces/ui/km/SearchDocDisplay.jspx?returnToSrId=&_afrLoop=384756135479859&srnum=&type=DOCUMENT&id=1520733.1&displayIndex=6&_afrWindowMode=0&_adf.ctrl-state=9vf6net92_81) (DocId 1520733.1) and [HiveJDBC](http://docs.oracle.com/cd/E27101_01/doc.10/e27365/odi.htm#sthref98)





  



ODI and OBIEE als enabelers to use the result out of the Hadoop world







Check Mark's [presentation](http://www.slideshare.net/rittmanmead/rm-bi-forum-2013-odi-hadoop-big-data)





  



**The three R's of ODI - Resuming, Restarting, Restoring by Stewart Bryson**





  



Using database features in ODI to eliminate the "Aftermath scenarios".





  



Resuming





  



Enable resumability in ODI to prevent a load to fail and just suspend




Monitor the resumable view - dba_resumable view





  



Load Plans





  



Restarting





  



[Oracle Flashback Technology](http://www.oracle.com/technetwork/database/features/availability/flashback-overview-082751.html)





  



Flashback Table




Flashback Database





  



Record the SCN (be careful with row level and block level)





  



Restoring





  



archivelog mode




Block change tracking file




Insert /*APPEND*/




Nologging




Backup








  



Check the origin of the "Three R's of Data Warehouse Fault Tolerance" [here](https://s3.amazonaws.com/rmc_docs/dw_fault_tolerance_oow2010_bryson.pdf).








  



**Automating & Scripting Oracle Data Integrator by Michael Rainey**








  



Some great examples of how to make life a little bit easier. Could Oracle have used this to migrate Oracle BIA from Informatica to Oracle Data Integrator earlier?





  



[ODI SDK Public API](http://docs.oracle.com/cd/E28280_01/apirefs.1111/e17060/index.html)




[Groovy](http://groovy.codehaus.org)




[Swing Builder](http://groovy.codehaus.org/Swing+Builder)





  



ODI - 11g Expert Accelerator for Model Creation - [David Allen ](https://blogs.oracle.com/dataintegration/entry/odi_11g_expert_accelerator_for)





  



All in all it was a very valuable Master Class. I learned a lot and there is lot more to investigate and explore. Hopefully this is the standard for the rest of the BI Forum.
