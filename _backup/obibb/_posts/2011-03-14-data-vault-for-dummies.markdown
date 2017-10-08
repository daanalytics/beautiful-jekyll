---
author: makumbe
comments: true
date: 2011-03-14 13:06:31+00:00
layout: post
link: http://blog.daanalytics.nl/2011/03/14/data-vault-for-dummies/
slug: data-vault-for-dummies
title: Data Vault for Dummies
wordpress_id: 822
categories:
- OBIBB - General
tags:
- Data Vault
---

One of the pillars on which the company I work for ([Scamander Solutions](www.scamander.com/)) is based on is (sharing) knowledge.

Last week I attended a session at the office about [Data Vault](http://danlinstedt.com/about/data-vault-basics/). This is a subject which isn't discussed very often within the Oracle BI community. Nevertheless it is an interesting subject. During the meeting we discussed the possibilities of designing a Data Vault for one of our clients. For me it has been few years ago that I first got into contact with this subject. Our Certified Data Vault Data Modeler ([CDVDM](http://www.geneseeacademy.com/certification)) : [Denny de Jonge](nl.linkedin.com/in/dennydejonge), was kind enough to refresh my memory.

**Data Vault for Dummies:**

The Data Vault is based on the following Object Types:

[![](http://obibb.files.wordpress.com/2011/03/datavault.jpg)](http://obibb.files.wordpress.com/2011/03/datavault.jpg)

[http://gerardnico.com/wiki/data_modeling/data_vault](http://gerardnico.com/wiki/data_modeling/data_vault)



	
  1. Hubs

	
    * Identification of an entity

	
      * Customer

	
      * Invoice

	
      * Order







	
  2. Links

	
    * Link between two hubs

	
      * a Customer places an Order







	
  3. Satellites

	
    * Details  / Description of a Hub

	
      * Context






	
    * Specification of a Link

	
      * Alternative payment








**How to Build the Data Vault?**

You build a Data Vault by defining the Hubs first. When the Hubs ar there, it's time to build the Links between the Hubs. Last but not least you can build the Satelites to describe the Hubs. 

[![](http://obibb.files.wordpress.com/2011/03/complete-northwind-data-vault-model.gif?w=300)](http://obibb.files.wordpress.com/2011/03/complete-northwind-data-vault-model.gif)

 [http://danlinstedt.com/about/data-vault-basics/](http://danlinstedt.com/about/data-vault-basics/)

Ad 1. **Hub**

A Hub consists of the following columns:



	
  * Unique Identification - CustomerId, OrderId (Sequence)

	
  * Identification - eg. CustomerNumber, OrderNumber

	
  * RecordSource -Which source does this record come from

	
  * LoadDate - Date the record has been loaded


Ad 2. **Link**

A Link consists of the following columns:



	
  * Unique Identification of the Hub - Customer (CustomerId)

	
  * Unique Identification of the linking Hub - Order (OrderId)

	
  * RecordSource -Which source does this record come from

	
  * LoadDate - Date the record has been loaded


Ad 3. ** Satellites**

A Satellite could consist of the following columns:



	
  * CustomerName

	
  * Address

	
  * Fax

	
  * Email

	
  * RecordSource -Which source does this record come from

	
  * LoadDate - Date the record has been loaded

	
  * Unique Identification of the Hub - Customer (CustomerId)

	
  * EndDate


The first columns are describing the concerning Hub. The LoadDate and the CustomerId uniquely identify a Satellite-record.

**Additional Comments**



	
  * Unit of Work




In Data Warehouse terms a Unit of Work is the definition of a load operation. Is eg. in the case of a mistake the whole batch rejected or is only the erroneous record disapproved? In a Data Vault a Unit of Work is a combination of a Hub and a Link






	
  * Everything fits




Whatever you load or wherever you load from, it is always possible to load the data. Everything that has been loaded can be monitored via eg. Errormarts, 'corrected' afterwards via updates and managed via Version Control.  






	
  * Data Integration vs. Data Interpretation




Data is integrated close at the source via the Data Vault. The meaning / interpretation of the data is situated in the Datamart.


Of course there is a lot that could be added to the subject of Data Vault, but for me it's enough for now.
