---
author: makumbe
comments: true
date: 2011-05-20 12:28:50+00:00
layout: post
link: http://blog.daanalytics.nl/2011/05/20/rittmanmead-bi-forum-2011-day-i/
slug: rittmanmead-bi-forum-2011-day-i
title: RittmanMead BI Forum 2011 - Day I
wordpress_id: 920
categories:
- RittmanMead BI Forum
tags:
- 11g
- Mobile device
- obi11g
- obiee11g
- Oracle BI Server
- Oracle WebLogic Server
- WLST
---

[John Minkjan](http://obiee101.blogspot.com/) kicks of Day I of the RittmanMead BI Forum. He's subject is Oracle BI EE on mobile devices. Very appropriate to the discussion last night during Oracle's Keynote. Mobile is hot and the audience is very eager to see Oracle BI EE in action on Mobile Devices (Ipad / Galaxy Tab). Before going to the demonstration, John shows us a lot of things you should bare in mind when developing mobile applications. I will not go into the XXX-details or better DDDD.

Oracle BI EE on mobile is not only about nice and fancy dashboards but also about:



	
  * Equipment

	
  * Antenna's

	
  * Environment

	
  * Security

	
  * Usage

	
  * Cost

	
  * Health

	
  * Type (Wifi, Bluetooth, Cellular)

	
  * Content Control

	
  * Operating System

	
  * Device

	
  * Patching


You have to think about dashboards which are firstly built for a laptop/desktop. Now you should redesign to fit the dashboard into the device. You could use some kind of landing page to navigate to the different dashboards, depending on where you are coming from.

Next up is [Adam Bloom](http://uk.linkedin.com/pub/adam-bloom/1/55/696). Adam is opening the lid on Oracle BI 11g security. He has a lot to open!! First he shows us the architecture of a Weblogic deployment. The best thing is try to use the Fusion Middleware (FMW) Security. Although 10g  Security via Init Blocks is supported you should make a choice between the two. Another thing is you should stick to whatever is certified, because of the limitations of the Oracle Platform Security Services [(OPSS)](http://www.oracle.com/technetwork/testcontent/opss-faq-131489.pdf).

Adam also demystified some of the GUID issues. There are some issues when you login with the weblogic-user in different RPD's. When you set the following parameter; FMW_UPDATE_ROLE_AND_USER_REF_GUIDS in the NQSConfig-file to 'YES', the problem is solved. You refresh the GUID's only when you are moving the indentity stores to a new server. Also when a RPD hasn't been used on a server yet.

Unfortunately this topic is so new and so complex, some other subjects could not be covered. We shortly addressed configuration and logging but according to Adam; "There are no bugs, only bad configuration".

On to [Andreas Nobbmann](http://blog.trivadis.com/blogs/andreasnobbmann/default.aspx), who is going to; "Script for a Jester's tear" referring to a song of [Marillion](http://en.wikipedia.org/wiki/Script_for_a_Jester%27s_Tear). Andreas is scripting fanatic and he warns us not to exaggerate the scripting. Scripting could make your life easier and can be used for;



	
  * repeating tasks

	
  * deployment

	
  * configuration

	
  * backups

	
  * starting / stopping / status


Downside of scripting is the lack of logging.

Andreas cover various elements of scripting:

	
  * [XUDML](http://download.oracle.com/docs/cd/E21764_01/bi.1111/e16364/xml_about.htm)

	
  * [WLST](http://download.oracle.com/docs/cd/E13222_01/wls/docs90/config_scripting/using_WLST.html)

	
  * [Phython](http://www.python.org/)

	
  * [Saxon](http://saxon.sourceforge.net/)


If it comes to migrating security check [here](http://obibb.wordpress.com/2011/05/12/obibb-update/http://download.oracle.com/docs/cd/E13222_01/wls/docs81/secmanage/security_data_migration.html).

After lunch, [Mike Brooks](http://uk.linkedin.com/pub/mike-brookes/1b/37b/81b) did his 'Warts and All'-presentation about his real-life experiences when implementing Oracle BI 11g. It turns out that a major release like Oracle 11g is, is not that easy. Not even for experienced people like Mike, supported by the RittmanMead guys. Over at Play.com, they tried to do a one week POC. Based on advice and documentation plans could be made, but due to later experiences the had to switch plans every once and a while.

Implementing the BI part of Oracle BI 11g is no rocket science, but the Weblogic Server is a whole new ballgame. That needs additional skills and training.

Now follows a panel discussion about the following subject; "Was it worth the wait", My personal opinion is; Yes!! Of course we have been waiting very long and of coures not everything is running as smoothly as we would like it to. On the other hand, the product looks fantastic and it gives us a lot of new opportunities, both technically as well as functionally. I guess we should focus on the good things and let Oracle work on the rest to improve the product.

A few highlights of the discussion;



	
  * focus on security issues instead of improved BI capabilities

	
  * sexy Front-end

	
  * early access, release dates

	
  * data lineage

	
  * versioning

	
  * MUD

	
  * charting like BI Publisher

	
  * Oracle OLAP vs Essbase

	
  * Essbase (Front-end Yes!!, Back-end No!!)

	
  * Stability

	
  * Integrated


Was it worth the wait or was worth the technical change? In the end, I guess it was a cautious yes.

[Michael Wilcke](http://ch.linkedin.com/in/michaelwilcke) finished the day with a presentation about why the Oracle BI Server is the ultimate choice for a BICC. BI is a circular process which never stops. When BI stops it is finished. Michael features on two subjects;



	
  * Business versus IT

	
  * Process and Organization


There is 'always' tension between business and IT. The Oracle BI Server offers the ability to separate these two (logical sql versus physical sql). This way you can de-couple the Front-end from the Back-end.

Requirement engineering can be done via prototyping in Excel and de-coupling. The requirement process is all about understanding the user instead of believing you know what he/she wants. You should define, establish and review. Top-down DWH vs. Bottom-up DWH.

In the end it turned out that Michael did a great job. He was elected by the audience as the Best Speaker. Therefor Mr. Wilcke went home with the most prestigious Brighton #biforum Best Speaker Award. Congratulations Michael.

It was a very interesting day. I think the speakers of this day have taken this event to a higher level (again!)


###### Related articles





	
  * [RittmanMead BI Forum 2011 - Masterclass (Part I)](http://obibb.wordpress.com/2011/05/18/rittmanmead-bi-forum-2011-masterclass-part-i/) (obibb.wordpress.com)

	
  * [RittmanMead BI Forum 2011 - Masterclass (Part II)](http://obibb.wordpress.com/2011/05/19/rittmanmead-bi-forum-2011-masterclass-part-ii/) (obibb.wordpress.com)


