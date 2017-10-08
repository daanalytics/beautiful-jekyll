---
author: makumbe
comments: true
date: 2015-04-28 08:36:18+00:00
layout: post
link: http://blog.daanalytics.nl/2015/04/28/oracle-business-intelligence-cloud-service-data-sync-is-out-on-otn/
slug: oracle-business-intelligence-cloud-service-data-sync-is-out-on-otn
title: Oracle Business Intelligence Cloud Service Data Sync is out on OTN
wordpress_id: 1901
categories:
- Oracle BI Cloud Service
tags:
- A-Team
- BICS
- Data Load
- OTN
---

A typical Oracle BI Cloud Service (BICS) flow looks like the following:



	
  * Load your data to the Cloud

	
  * Model and Secure your data

	
  * Author Analyzes,Visualizations and Interactive Dashboards

	
  * Use and Share BICS content


In the current version of BICS you have to upload your data into the Cloud. There are several ways to load the data:

	
  * [BICS Data Loader](http://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/bics/DataLoader/dataloader.html)

	
  * REST API

	
  * [SQL Developer](http://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/bics/MigratingData/migrate_data.html)

	
  * PL/SQL Data Import

	
  * BICS Data Sync




The BICS Data Sync is a client utility to schedule and load data into the Cloud. If you are familiar with the Informatica version of Oracle BI Applications, you will see the similarities between BICS Data Sync and the DAC. BICS Data Sync has become GA on [OTN](http://www.oracle.com/technetwork/middleware/bicloud/downloads/index.html) recently.




For more details about BICS Data Sync check the following:






	
  * [BICS Data Sync getting started guide](http://www.oracle.com/technetwork/topics/virtualization/whatsnew/bicsdatasync-gs-v1-2525282.pdf)

	
  * [BICS Data Sync documentation](http://www.oracle.com/technetwork/topics/virtualization/whatsnew/bicsdatasync-doc-v1-2525284.pdf)

	
  * [Configuring the Data Sync Tool for BI Cloud Service (BICS)](http://www.ateam-oracle.com/configuring-the-data-sync-tool-for-bi-cloud-service-bics/)


In the first BICS version the only database option for BICS was the Oracle Schema-as-a-Service. This had its limitations. Oracle recently release the option to run BICS on a Oracle Database-as-a-Service. Check [here](https://cloud.oracle.com/database) for the differences between the two. One of the benefits of the Database-as-a-Service option that you can use any ETL tool to load data into the Cloud. Consider the BICS Data Sync option as a light option for ETL to the Cloud.
