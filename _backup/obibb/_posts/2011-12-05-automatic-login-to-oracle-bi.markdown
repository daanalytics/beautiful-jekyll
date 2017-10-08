---
author: makumbe
comments: true
date: 2011-12-05 10:14:19+00:00
layout: post
link: http://blog.daanalytics.nl/2011/12/05/automatic-login-to-oracle-bi/
slug: automatic-login-to-oracle-bi
title: Automatic login to Oracle BI via Oracle eBS
wordpress_id: 1017
categories:
- Oracle eBS
tags:
- 10g
- Oracle BI Applications
- Oracle Business Analytics
- R12
---

I have been blogging about the integration between Oracle eBS and Oracle BI. It's possible to login to Oracle BI via Oracle eBS. In these situations it's necessarily to have an account and a responsibility in Oracle eBS.

Some people make use of Oracle BI and not Oracle eBS. Normally the wouldn't need an Oracle eBS account.

In cases of an integration between the two systems you have to login to Oracle eBS, select a responsibility and select a link to Oracle BI.

[![](http://obibb.files.wordpress.com/2011/12/oracle-ebs-hompage-navigator.png?w=300)](http://obibb.files.wordpress.com/2011/12/oracle-ebs-hompage-navigator.png)

For some people these are to many steps to get to Oracle BI.

It's possible to set a default start page when you login to Oracle eBS. You could eg. choose 'Oracle BI Answers' as your default start page.

This could be set per user via the Preferences of the user who has logged in.

[![](http://obibb.files.wordpress.com/2011/12/oracle-ebs-hompage-navigator-preferences.png?w=300)](http://obibb.files.wordpress.com/2011/12/oracle-ebs-hompage-navigator-preferences.png)

Here you could set the start page

[![](http://obibb.files.wordpress.com/2011/12/oracle-ebs-preferences-startpage.png?w=300)](http://obibb.files.wordpress.com/2011/12/oracle-ebs-preferences-startpage.png)

Be careful setting this option, because once you set it, you wont be able to return to Oracle eBS. In such a case when a user wants to get rid of this startpage use the Oracle eBS Profile Option; 'Applications Start page'. This option could be set for a specific user or a responsibility via the 'System Administrator'-responsibility.

Via 'Profile', 'System', you can find the specific 'System Profile Value'

[![](http://obibb.files.wordpress.com/2011/12/oracle-ebs-system-profile.png?w=300)](http://obibb.files.wordpress.com/2011/12/oracle-ebs-system-profile.png)

For the user; 'DBAKBOORD' the value of this profile is;

[![](http://obibb.files.wordpress.com/2011/12/oracle-ebs-system-profile-value.png?w=300)](http://obibb.files.wordpress.com/2011/12/oracle-ebs-system-profile-value.png)

This value can be retrieved from the database via the following query;

[sourcecode language="sql"]

select fpov.level_value user_id

, fu.user_name

, fpov.profile_option_value

from applsys.fnd_profile_option_values fpov

, apps.fnd_profile_options_vl fpo

, applsys.fnd_user fu

where fpo.profile_option_id = fpov.profile_option_id

and fpo.application_id = fpov.application_id

and fu.user_id = fpov.level_value

and fpo.profile_option_name = 'APPLICATIONS_START_PAGE'

and fpov.level_id = 10004

[/sourcecode]

The output of this query is the following;

[![](http://obibb.files.wordpress.com/2011/12/toad-query-output.png?w=300)](http://obibb.files.wordpress.com/2011/12/toad-query-output.png)

Using the Oracle eBS Profile Option; 'Applications Start page' could also be an easy solution to set a startpage for a whole group of user. After setting this option they all will login to Oracle BI Answers directly without selecting the menuoption in Oracle eBS first.
[
](http://obibb.files.wordpress.com/2011/12/toad-query-output.png)
