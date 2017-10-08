---
author: makumbe
comments: true
date: 2011-05-13 10:28:12+00:00
layout: post
link: http://blog.daanalytics.nl/2011/05/13/installing-oracle-bi-apps-7-9-6-3-2/
slug: installing-oracle-bi-apps-7-9-6-3-2
title: Installing Oracle BI Apps 7.9.6.3
wordpress_id: 902
categories:
- Oracle BI Applications
tags:
- 7.9.6.3
- Installation
---

The following is a short description of what steps have to be taken to install Oracle BI Applications (OBIA) version 7.9.6.3. This version of OBIA is the first version which runs on the new Oracle BI 11g 11.1.1.5.0 platform

This document assumes, that Oracle BI 11g has been installed already. Make sure the Weblogic Administration Server is running before the installation starts.



	
  * Unpack the installation software

	
  * Navigate to the folder; 'Oracle_BI_Applications'

	
  * Start Setup.exe

	
  * A wizard will start


![](http://obibb.files.wordpress.com/2011/05/051111_1327_installingo2.png)



	
  * Click Next

	
  * 


Enter the installation directories -- {MIDDLEWARE_HOME}



	
    * 


There are three important locations;



	
      * Oracle BI Home Locatie  --> {MIDDLEWARE_HOME}\Oracle_BI1

	
      * Oracle Instance Locatie  --> {MIDDLEWARE_HOME}\instances\instance1

	
      * Oracle Domain Location --> {MIDDLEWARE_HOME}\user_projects\domains\bifoundation_domain








![](http://obibb.files.wordpress.com/2011/05/051111_1327_installingo3.png)



	
  * Click Next

	
  * Enter the Weblogic Administrator Details


![](http://obibb.files.wordpress.com/2011/05/051111_1327_installingo4.png)



	
  * Click Next

	
  * In the background, some examinations are performed. This could take a while

	
  * Select the applications (default = everything), which should be installed


![](http://obibb.files.wordpress.com/2011/05/051111_1327_installingo5.png)



	
  * Click Next

	
  * A summary appears with the e=information about what will be installed


![](http://obibb.files.wordpress.com/2011/05/051111_1327_installingo6.png)



	
  * 


Click Next




	
  * Wait for the installer to finish



	
  * Click Finish


After the installation has finished, one can check what has been installed. In the 'Oracle BI Home' there has been an additional folder (biapps) added.

![](http://obibb.files.wordpress.com/2011/05/051111_1327_installingo8.png)

You will find the new Repository RPD-file in; {MIDDLEWARE_HOME}\Oracle_BI1\biapps\repository

The Repository can be opened offline. The Repository password (Admin123) is the default.

De new Catalog resides in the; {MIDDLEWARE_HOME}\Oracle_BI1\biapps\catalog-folder.

More to come.
