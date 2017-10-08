---
author: makumbe
comments: true
date: 2010-10-07 08:15:21+00:00
layout: post
link: http://blog.daanalytics.nl/2010/10/07/upgrading-from-10g-to-11g-repository-and-webcat/
slug: upgrading-from-10g-to-11g-repository-and-webcat
title: Upgrading from 10g to 11g (Repository and Webcat)
wordpress_id: 453
categories:
- Setup
tags:
- 10g
- 11g
- migrate
- obi11g
---

[](http://obibb.files.wordpress.com/2010/10/rpd-catalog.png)[](http://obibb.files.wordpress.com/2010/10/source.png)[](http://obibb.files.wordpress.com/2010/10/source.png)[](http://obibb.files.wordpress.com/2010/10/weblogic-server.png)[](http://obibb.files.wordpress.com/2010/10/examine.png)[](http://obibb.files.wordpress.com/2010/10/upgrade-summary.png)[](http://obibb.files.wordpress.com/2010/10/upgrade-process.png)[](http://obibb.files.wordpress.com/2010/10/upgrade-complete.png)When I had installed the Oracle BI 11g R1 version, I thought it would be nice to see what happened when I migrate a simple 10g Repository and Catalog to 11g.

Migrating from 10g to 11g seems very straight forward.

Navigate to <MIDDLEWARE_HOME>\Oracle_BI1\bin\ and start 'ua.bat'

You are presented with the following screens fill in the required values according to your site's needs;

[![](http://obibb.files.wordpress.com/2010/10/welcome.png?w=300)](http://obibb.files.wordpress.com/2010/10/welcome.png)

click 'Next'

[![](http://obibb.files.wordpress.com/2010/10/rpd-catalog.png?w=300)](http://obibb.files.wordpress.com/2010/10/rpd-catalog.png)

Choose to upgrade the RPD and the Presentation Catalog.

click 'Next'

[![](http://obibb.files.wordpress.com/2010/10/source.png?w=300)](http://obibb.files.wordpress.com/2010/10/source.png)

Choose the location of  the RPD file you want to migrate.
Fill in the credentials

In 11g you have to provide an additional password for your RPD.
Fill in the credentials

Choose the location of your catalog
Choose the Deliveries directory

click 'Next'

[![](http://obibb.files.wordpress.com/2010/10/weblogic-server.png?w=300)](http://obibb.files.wordpress.com/2010/10/weblogic-server.png)

Provide the details (port and credentials) of your Weblogic server

click 'Next'

[![](http://obibb.files.wordpress.com/2010/10/examine.png?w=300)](http://obibb.files.wordpress.com/2010/10/examine.png)

If everything has been provided well so far the status will be 'succeeded' 

 click 'Next'

[![](http://obibb.files.wordpress.com/2010/10/upgrade-summary.png?w=300)](http://obibb.files.wordpress.com/2010/10/upgrade-summary.png)

The summary shows the details. Now you are ready to upgrade.

click 'Upgrade'

[![](http://obibb.files.wordpress.com/2010/10/upgrade-process.png?w=300)](http://obibb.files.wordpress.com/2010/10/upgrade-process.png)

If everything runs like expected, the status will be 'succeeded' 

 click 'Next'

[![](http://obibb.files.wordpress.com/2010/10/upgrade-complete.png?w=300)](http://obibb.files.wordpress.com/2010/10/upgrade-complete.png)

You are finished.

click 'Closed'

For some more/other details, please refer to [Venkat's](http://www.rittmanmead.com/2010/08/23/oracle-bi-ee-11g-upgrading-from-bi-ee-10g-repository-web-catalog/) post.

You can now check the 'Enterprise Manager'. There you will see that the newly created Repository and Catalog are 'active'.

In the end it seems that most of the functionality has been migrated succesfully to 11g. Two 'major' problems I experienced immediately;



	
  1. I used some custom folders in 10g. In 11g you have to take some additional steps to make custom  folders available. I will cover this topic in a next post.

	
  2. I used a 'Narrative View' with; ' Contains HTML Markup'. This doesn't work for all HTML Markup. It does work in the 'Static View'. I do not have a solution for that yet.


