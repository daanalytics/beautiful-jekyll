---
author: makumbe
comments: true
date: 2010-10-18 10:20:22+00:00
layout: post
link: http://blog.daanalytics.nl/2010/10/18/extend-dashboard-funtionality-by-using-presentation-variables/
slug: extend-dashboard-funtionality-by-using-presentation-variables
title: 'Extend Dashboard funtionality by using Presentation Variables '
wordpress_id: 490
categories:
- Oracle BI Dashboards
tags:
- Oracle BI EE
- presentation variables
- variables
---

[](http://obibb.files.wordpress.com/2010/10/section-1.png)[](http://obibb.files.wordpress.com/2010/10/section-1-rename.png)[](http://obibb.files.wordpress.com/2010/10/section-1-pv-rename.png)[](http://obibb.files.wordpress.com/2010/10/rename.png)[](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-output.png)[](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-pv-s-output.png)[](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-pv-o-output.png)[](http://obibb.files.wordpress.com/2010/10/set-pv.png)[](http://obibb.files.wordpress.com/2010/10/dashboard-non-oracle1.png)It's possible to extend the functionality of your Oracle BI Dashboard by using Presentation Variables. Nothing new here. For some more details about variables in Oracle BI EE and how to use the please have a look [here](http://siebel-essentials.blogspot.com/2008/09/oracle-bi-ee-variables.html).

A colleague of mine pointed me to two examples of how to use these variables in your Oracle BI Dashboard. Maybe nothing new as well, but nice to mention anyway.

**Add a Presentation Variable to a section heading**

If you want, you can add an heading to your section. This is pretty straight forward**.**

Default, when you add a section to your dashboard, the section is named; 'Section 1'.

 [![](http://obibb.files.wordpress.com/2010/10/section-1.png?w=300)](http://obibb.files.wordpress.com/2010/10/section-1.png)

 If you want to give this section a maeningful name and add it to your dashboard page, you can rename and display the section.

[![](http://obibb.files.wordpress.com/2010/10/section-1-rename.png?w=300)](http://obibb.files.wordpress.com/2010/10/section-1-rename.png)[![](http://obibb.files.wordpress.com/2010/10/rename.png)](http://obibb.files.wordpress.com/2010/10/rename.png)

The dashboard page will show the text acccordingly.[](http://obibb.files.wordpress.com/2010/10/section-1-pv-rename.png)

[![](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-output.png?w=300)](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-output.png)

If you like you can make this heading dynamic by using a Presentation Variable. First you will have to make a dashboard prompt to set the Presentation Variable.

[![](http://obibb.files.wordpress.com/2010/10/set-pv.png?w=300)](http://obibb.files.wordpress.com/2010/10/set-pv.png) 

Secondly you can reference the Presentation Variable. In this case, add; @{PV_SUPPLIER} to the section heading.

[![](http://obibb.files.wordpress.com/2010/10/section-1-pv-rename.png)](http://obibb.files.wordpress.com/2010/10/section-1-pv-rename.png)

Now the dashboard page will show the heading, including the Presentation Variable.

[![](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-pv-s-output.png?w=300)](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-pv-s-output.png)

When you change the selection in the dashboard prompt the text will also change.

[![](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-pv-o-output.png?w=300)](http://obibb.files.wordpress.com/2010/10/oracle-bi-dashboards-pv-o-output.png)

**Using an iFrame to show different views of the same Answer based on Guided Navigation and a Presentation Variable**

Picture the following simple requirement:

I have a set of Suppliers. Each Supplier has a Supplier Type.

[![](http://obibb.files.wordpress.com/2010/10/supplier-table.png?w=300)](http://obibb.files.wordpress.com/2010/10/supplier-table.png)

On my dashboard, there is a prompt on Supplier Type.

[![](http://obibb.files.wordpress.com/2010/10/prompt-supplier-type1.png)](http://obibb.files.wordpress.com/2010/10/prompt-supplier-type1.png)[](http://obibb.files.wordpress.com/2010/10/prompt-supplier-type.png)

When I select 'Oracle'; show a Pivot table. If 'Non-Oracle' is chosen, then there should be a 'Line Chart' for 'Scamander Solutions'. 'Oracle BI By Bakboord' will show a 'Bar Graph'.

You could achieve this by making multiple Answers, Guided Navigation and some hard-coding. Another way of achieving this requirement, is using Guided Navigation, iFrames and a Presentation Variable in combination with an GO Url. iFrames require the use of Presentation Variables, because they cannot capture the values you select in a prompt directly.

Edit a dashboard page and add two sections with Guided Navigation to switch between the views for the Supplier Type. In the section for Supplier Type = 'Non-Oracle' add two Text Objects for the iFrames.

[![](http://obibb.files.wordpress.com/2010/10/edit-dashboard.png?w=300)](http://obibb.files.wordpress.com/2010/10/edit-dashboard.png)

Add the folowing code to the Text Object for the iFrame:

    
    <iframe src=
    <a href="http://10.0.0.24:9704/analytics/saw.dll?Go&Path=/shared/OBIBB/Presentation%20Variable%20iFrame&Action=Navigate&P0=2&P1=eq&P2="Dim%20Supplier"."Supplier%20Type"&P3=@{PV_SUPPLIER_TYPE}&P4=eq&P5="Dim%20Supplier"."Supplier%20Name"&P6=Oracle%20BI%20By%20Bakboord&Options=rmf&ViewName=staticchart!1">http://localhost:9704/analytics/saw.dll?Go&Path=/shared/OBIBB/Presentation%20Variable%20iFrame&Action=Navigate&P0=2&P1=eq&P2="Dim%20Supplier"."Supplier%20Type"&P3=@{PV_SUPPLIER_TYPE}&P4=eq&P5="Dim%20Supplier"."Supplier%20Name"&P6=Oracle%20BI%20By%20Bakboord&Options=rmf&ViewName=staticchart!1</a> width=100% height=375 frameborder=none>
    </iframe>


 Now I am able to switch between different views, without having to create different Answers

[![](http://obibb.files.wordpress.com/2010/10/dashboard-oracle.png?w=300)](http://obibb.files.wordpress.com/2010/10/dashboard-oracle.png)

** [![](http://obibb.files.wordpress.com/2010/10/dashboard-non-oracle1.png?w=300)](http://obibb.files.wordpress.com/2010/10/dashboard-non-oracle1.png)**
