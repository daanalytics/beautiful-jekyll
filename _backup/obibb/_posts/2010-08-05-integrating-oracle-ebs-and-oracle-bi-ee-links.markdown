---
author: makumbe
comments: true
date: 2010-08-05 09:14:16+00:00
layout: post
link: http://blog.daanalytics.nl/2010/08/05/integrating-oracle-ebs-and-oracle-bi-ee-links/
slug: integrating-oracle-ebs-and-oracle-bi-ee-links
title: Integrating Oracle eBS and Oracle BI EE - Links
wordpress_id: 315
categories:
- Oracle eBS
tags:
- Navigation
- Oracle BI EE
- R12
---

The setup for Integrating Oracle eBS and Oracle BI EE is complete. Now we can create links between the two. These links should make it possible to navigate from Oracle eBS to Oracle BI EE and vice versa. Both in context.

For additional details I would refer to the following document on [My Oracle Support](https://supporthtml.oracle.com/ep/faces/secure/km/DocumentDisplay.jspx?id=552735.1) about Integrating Oracle Business Intelligence Applications with Oracle E-Business Suite.

First thing I want to look at is how to setup the navigation from Oracle eBS to Oracle BI EE. A standard Oracle eBS installation already contains some initial setup. How this is organized could be retrieved using the following query;

[sourcecode language="sql"]
SELECT   fa.application_short_name
, fa.application_name
, fda.application_short_name data_application_short_name
, fda.application_name data_application_name
, fdg.data_group_name
, frt.responsibility_key
, frt.responsibility_name
, frt.description responsibility_description
, fff.function_name
, fff.description function_description
, fff.user_function_name
, fm.menu_name
, fm.user_menu_name
, fm.description menu_description
FROM apps.fnd_menus_vl fm
, apps.fnd_form_functions_vl fff
, apps.fnd_menu_entries_vl fme
, apps.fnd_responsibility_vl frt
, apps.fnd_application_vl fa
, apps.fnd_application_vl fda
, applsys.fnd_data_groups fdg
WHERE fm.menu_id = fme.menu_id
AND frt.menu_id(+) = fm.menu_id
AND frt.responsibility_key LIKE '%OBIEE%'
AND fme.function_id(+) = fff.function_id
AND fa.application_id = frt.application_id
AND fda.application_id = frt.data_group_application_id
AND fdg.data_group_id = frt.data_group_id
ORDER BY frt.responsibility_key
[/sourcecode]

There are a few different ways to navigate to Oracle BI EE. As you could have seen in the pervious query, navigation to Oracle BI EE is controlled via functions in menus. The most easy way to navigate is to go directly to your default Oracle BI Dashboard or to the homepage for Oracle BI Answers.

The following query shows an example of the settings for this default navigation;

[sourcecode language="sql"]
SELECT fff.function_name
, fff.user_function_name
, fff.description
, fff.type function_type_code
, fft.meaning function_type
, fff.web_host_name
, fff.web_html_call
FROM apps.fnd_form_functions_vl fff
, fnd_lookups fft
WHERE fft.lookup_code = fff.type
AND fff.function_name like '%OBIEE%F'
AND fft.lookup_type = 'FORM_FUNCTION_TYPE'
[/sourcecode]

The 'web_html_call' can be adjusted according to your own specific needs. It's good to have a good understanding of URL Parameters in Oracle BI EE. [Venkat](http://oraclebizint.wordpress.com/2007/12/04/oracle-bi-ee-101332-url-parameters/) has written about this subject a while back. Check his [spreadsheet](http://spreadsheets.google.com/pub?key=pKiykjBtiWVA_qqLY8nbGCg) on Google for more details.

Navigating to the default is controlled by the following entries:



	
  * OracleOasis.jsp?mode=OBIEE&function=Dashboard

	
  * OracleOasis.jsp?mode=OBIEE&function=Answers


If you want to navigate to a specific Dashboard(-Page) or a specific Answers Subject Area or report, you should extend the default navigation links to look something like the following:

** Dashboard

	
  * OracleOasis.jsp?mode=OBIEE&function=Dashboard&parameters=PortalPath~/shared/[Folder_Name]/_portal/[Dashboard_Name] --> This will navigate to a specific Oracle BI Dashboard

	
  * OracleOasis.jsp?mode=OBIEE&function=Dashboard&parameters=PortalPath~/shared/[Folder_Name]/_portal/[Dashboard_Name]%26Page=[Page Name] --> This will navigate to a specific Oracle BI Dashboard Page


The '%26' is used instead of the '&'-sign. Make sure you replace all the spaces with '%20'. It's even better trying to avoid using spaces.

I used a site created by Brian Wilson for the [Url-encoding](http://www.blooberry.com/indexdot/html/topics/urlencoding.htm). W3Schools.com could also be used as an [HTML URL Encoding Reference](http://www.w3schools.com/TAGS/ref_urlencode.asp).

** Answers



	
  * OracleOasis.jsp?mode=OBIEE&function=Answers&parameters=SubjectArea~[Subject Area Name] --> This will navigate to the Subject Area of your choice

	
  * OracleOasis.jsp?mode=OBIEE&function=Go&parameters=Path~/shared/[Folder_Name]/[Report_Name] --> This will directly navigate to the Answer of choice (Make sure you replace all the spaces with '%20')


If you go back to the previously mentioned spreadsheet it's good to take the following into account;

	
  * 'function=' --> is followed by one of the entries in the 'Command'-column

	
  * 'parameters='--> contains the full url, including 'Parameters' if needed

	
  * after the '~'-sign comes the full url to the location of choice


Next in line could be investigating the possibilities of navigating from a Oracle eBS Form directly to an Oracle BI Dashboard including prompts. This way we could navigate 'in context'.
