---
author: makumbe
comments: true
date: 2014-05-08 12:38:43+00:00
layout: post
link: http://blog.daanalytics.nl/2014/05/08/rm-bi-forum-2014-notes-cloudera-hadoop-masterclass/
slug: rm-bi-forum-2014-notes-cloudera-hadoop-masterclass
title: RM BI Forum 2014 Notes – Cloudera Hadoop Masterclass
wordpress_id: 1669
categories:
- RittmanMead BI Forum
tags:
- biforum2014
- Cloudera
- Hadoop
---

[![Cloudera](http://obibb.files.wordpress.com/2014/05/cloudera.jpg?w=300)](http://www.cloudera.com)

The Rittman Mead BI Forum started off with a one-day Hadoop Masterclass, provided by [Lars George](https://twitter.com/larsgeorge).  As he messaged us the day before we have learned what Hadoop is all about, what its major components are, how to acquire, processes and provide data as part of a production data processing pipeline. To that effect, Lars advised that it would be useful to follow along the examples in the course and have an environment handy. That would allow us to experiment at our convenience during and after the class. He directed us to the following [link;](http://www.cloudera.com/content/support/en/downloads/download-components/download-products.html?productID=F6mO278Rvo) the Cloudera Quickstart VM.


Lars recommends the following: "Select the CDH5 version of the VM. Please select a virtual machines image matching your VM platform of choice. If you do not have a VM host application installed yet, you can choose from a few available ones. VirtualBox is provided by Oracle and a great choice to use. It can be downloaded [here](https://www.virtualbox.org/). Set up the VM application, then download and start the Cloudera Quickstart VM to run on top of it. It is as easy as that."







Find below a few notes I took during the Masterclass.







Lars devided the Masterclass into four parts.









### I - Introduction into Hadoop








	
  * What is Big Data? -  It's not necessarily volume but also format and speed. Three V's - Volume, Variety and Velocity

	
  * Introduction to Hadoop

	
  * HDFS

	
  * [MapReduce](http://research.google.com/archive/mapreduce.html)

	
  * [YARN](http://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html)

	
  * Cluster Planning















Hadoop is Open Source and Apache licensed — [http://hadoop.apache.org](http://hadoop.apache.org/)




Many developers Cloudera, Apple




Contributers




Many related projects, applications, tools







Hadoop is not a system but a set of tools, projects which work together. You should decide, for each part of the architecture, which tool you should use and how you would use it.







[Hadoop Ecosystem](http://www.cloudera.com/content/cloudera/en/training/library/apache-hadoop-ecosystem.html)













[![HadoopEcosystem](http://obibb.files.wordpress.com/2014/05/hadoopecosystem.jpg?w=300)](http://www.cloudera.com/content/cloudera/en/training/library/apache-hadoop-ecosystem.html)












**Hadoop where to get it?**








	
  * Apache Hadoop

	
  * Open Source Distribution ( Cloudera CDH -[ Cloudera Enterprise Data Hub](http://www.cloudera.com/content/cloudera/en/products-and-services/cdh.html))

	
  * Commercial (IBM) --> Company specific standards







**Load, Process and Analyze data**







Hadoop Concept - distribute data in the system.




Process the data where it resides




No network processing




High level code (java)




No communication between nodes




Data stored on different machines in advance





**Map Reduce Data Flow**








	
  * Map

	
  * Sort en Shuffle

	
  * Reduce





### II - Ingress and Egress




Ingress - moving data into Hadoop (HDFS)







[Flume](http://flume.apache.org)  (Near Real-Time Pipeline)








	
  * Source

	
  * (File) Channel

	
  * Sink —> poll, collect and write to eg. HDFS










![Apache_Flume](http://obibb.files.wordpress.com/2014/05/apache_flume.png?w=300)







[Sqoop](http://sqoop.apache.org)







Transfer data between Relational Database (Oracle, Terradata, Sql Server, etc.) and HDFS




Oracle Database Driver for Sqoop - [OraOop by Quest ](https://github.com/QuestSoftwareTCD/OracleSQOOPconnector)







FIle Formats important to keep in mind when you want to get the data out again.







Simple File versus Container (Structured) File







[Parquet](http://blog.cloudera.com/blog/2013/03/introducing-parquet-columnar-storage-for-apache-hadoop/) vs Google [Dremel](https://code.google.com/p/dremel/) —>







**BI Integration**








	
  * Sqoop

	
  * HDFS Connector

	
  * ODBC/JDBC


















### III - NoSQL and Hadoop




[NoSQL](http://nosql-database.org)







[HBase](http://hbase.apache.org)







ACID (atomicity, consistency, isolation, durability) 




### IV Analyzing Big Data








	
  * [Pig](http://pig.apache.org)

	
  * [Hive](//hive.apache.org)  ([HiveServer2](http://blog.cloudera.com/blog/2013/07/how-hiveserver2-brings-security-and-concurrency-to-apache-hive/) instead of HiveServer1)

	
  * [Impala](http://blog.cloudera.com/blog/2012/10/cloudera-impala-real-time-queries-in-apache-hadoop-for-real/)

	
  * Search - [Lucien](http://lucene.apache.org/core/)

	
  * [Data Pipelines](http://hortonworks.com/hadoop-tutorial/defining-processing-data-end-end-data-pipeline-apache-falcon/) (micro -  macro)

	
  * [Oozie](http://oozie.apache.org) (Workflow Server)

	
  * Information Architecture - Where / How to store data and how to secure this structure

	
  * [Spark](http://spark.apache.org) (Java, Python, Scala compile into code)







I think Lars could have talked about Hadoop two more days (with or without sheets). Hadoop is all about making choices. There are similar tools, projects, concepts, etc. All depends on what you want to achieve.







Although this Masterclass was very informative, I still struggle to see the use case at this moment. A lot of my customers are still struggling with their ’normal’ data…...



