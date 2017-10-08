---
author: makumbe
comments: true
date: 2015-07-09 09:21:34+00:00
layout: post
link: http://blog.daanalytics.nl/2015/07/09/extracting-data-from-bics-apex-via-restful-webservice/
slug: extracting-data-from-bics-apex-via-restful-webservice
title: Extracting Data from BICS / Apex via RESTful Webservice
wordpress_id: 1912
categories:
- Oracle BI Cloud Service
tags:
- BICS
- REST
---

A few days ago, I read the following post; [Extracting Data from BICS / Apex via RESTful Webservice](http://www.ateam-oracle.com/extracting-data-from-bics-apex-via-restful-webservice/) on the Oracle A-Team Chronicles website. I tried the example to see how things work.


#### Cocoa Rest Client


In the blogpost is referred to [cURL](http://curl.haxx.se) to test the REST-endpoints. I have been testing this out on a Mac and used; [Cocoa Rest Client](https://code.google.com/p/cocoa-rest-client/).

If you test the created RESTful Service Handler, you get a window with a JSON formatted result set. You can copy the url.

![Test_SQLWorkshop](https://obibb.files.wordpress.com/2015/07/test_sqlworkshop.png?w=680)

Enter the copied url in the Cocoa Client.

[![Test_Cocoa](https://obibb.files.wordpress.com/2015/07/test_cocoa.png?w=680)](https://obibb.files.wordpress.com/2015/07/test_cocoa.png)

You will find the result in the Response Body of the CocoaClient. Don't forget to enter your credentials to your BICS environment.
