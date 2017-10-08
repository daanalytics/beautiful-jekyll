---
author: makumbe
comments: true
date: 2011-05-19 13:04:56+00:00
layout: post
link: http://blog.daanalytics.nl/2011/05/19/rittmanmead-bi-forum-2011-masterclass-part-ii/
slug: rittmanmead-bi-forum-2011-masterclass-part-ii
title: RittmanMead BI Forum 2011 - Masterclass (Part II)
wordpress_id: 913
categories:
- RittmanMead BI Forum
tags:
- 11g
- Action Framework
- obiee11g
- Oracle BI Server
- RPD
- SOA
---

After the lunch, which was excellent by the way, Mark continued the Masterclass. Next on is the OBIEE11g - Server & RPD New Features. There are new features in the RPD which you should try yourself (including me), before you really can understand what is happening. The guys over at RittmanMead are decompiling .jar-files to make anything more clear! I guess I will start with the Admin-tool. A few highlights;



	
  * Column Descriptors --> Use the description to show, while in the background you use an Id (indexed) to 'fire' a query (Oracle Discoverer functionality)

	
  * [Lookups Tables & Functions](http://www.rittmanmead.com/2010/08/oracle-bi-ee-11g-lookup-tables-sparse-and-dense-lookups/) --> Interesting functionality Venkat already blogged about

	
  * Hierarchies (Ragged & Skip Level) --> Only use Ragged and Skip Level when you really need it, because it will generate complex queries to identify and it will be giving problems with generating MDX for Essbase.

	
  * Parent Child Hierarchies --> PC Aggregation is only aggregating for the member by default. You should do some extra modeling to bring the closure table into the model.

	
  * Oracle OLAP Option --> The BI Server now can manage navitve Oracle OLAP. As Mark mentioned; "A cautious welcome"


Tony closes the Masterclass whit the OBIEE11g - SOA Integration. New in Oracle BI 11g is the [Action Framework.](http://www.oracle.com/pls/ebn/swf_viewer.load?p_shows_id=8910843&p_referred=FlashISeminar) The Action Framework makes it possible to integrate your Business Intelligence System with your business process. Either by navigating through an url or by integrating with Web Services. Calling Web Services opens a whole new world for me. Now you see a further integration of Oracle BI 11g and Oracle Fusion Middleware. On the one end this Action Framework gives us a lot of new possibilities. On the other end it gets more and more complex. You should get to know a few of the following and more:



	
  * SOA Concepts

	
  * JDeveloper

	
  * BPEL Workflows

	
  * Oracle SOA


This way you should be able to integrate with external applications by building and deploying web services and invoke them from Oracle BI EE.

Thanks to Mark and Tony, they did a great job with this Masterclass. Although it seems like an information overload, both guys have presented a lot of information in such a way we do not have to be bored in the coming months.


###### Related articles





	
  * [RittmanMead BI Forum 2011 - Masterclass (Part I)](http://obibb.wordpress.com/2011/05/18/rittmanmead-bi-forum-2011-masterclass-part-i/) (obibb.wordpress.com)


