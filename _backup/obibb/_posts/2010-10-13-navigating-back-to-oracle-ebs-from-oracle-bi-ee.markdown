---
author: makumbe
comments: true
date: 2010-10-13 11:40:21+00:00
layout: post
link: http://blog.daanalytics.nl/2010/10/13/navigating-back-to-oracle-ebs-from-oracle-bi-ee/
slug: navigating-back-to-oracle-ebs-from-oracle-bi-ee
title: Navigating Back to Oracle eBS from Oracle BI EE
wordpress_id: 505
categories:
- Oracle eBS
tags:
- Navigation
- Oracle BI EE
- R12
---

In one of the my earlier [posts](http://wp.me/pVzHx-4X) I was able to navigate from Oracle eBS directly into Oracle BI EE. By default I was not able to navigate back to the Oracle eBS homepage. After a little research on Google and My Oracle Support I found a [link](https://support.oracle.com/CSP/ui/flash.html#tab=KBHome(page=KBHome&id=()),(page=KBNavigator&id=(bmDocID=872092.1&viewingMode=1143&bmDocDsrc=KB&bmDocTitle=Navigating%20Back%20to%20EBS%20from%20OBIEE&from=BOOKMARK&bmDocType=HOWTO))) with a; 'How To : Navigating Back to EBS from OBIEE' (Id: 872092.1).

Check the following in your Oracle BI Dashboard Menu.

[![](http://obibb.files.wordpress.com/2010/10/no-navigate-back-to-ebs.png?w=300)](http://obibb.files.wordpress.com/2010/10/no-navigate-back-to-ebs.png)

Add the LogoffUrl-tag to your instanceconfig.xml and restart the Presentation Server

[sourcecode language="xml"]
<LogoffUrl> <a href="http://localhost:8000/OA_HTML/OA.jsp?OAFunc=OAHOMEPAGE">http://serverUrl:8000/OA_HTML/OA.jsp?OAFunc=OAHOMEPAGE</a>         
</LogoffUrl>
[/sourcecode]

 Your instanceconfig.xml-file will look something like this:

[sourcecode language="xml"]
<ExternalLogon enabled="true">
<LogoffUrl> <a href="http://localhost:8000/OA_HTML/OA.jsp?OAFunc=OAHOMEPAGE">http://serverUrl:8000/OA_HTML/OA.jsp?OAFunc=OAHOMEPAGE</a>         
</LogoffUrl>
  <ParamList>
  <Param name="NQ_SESSION.ICX_SESSION_COOKIE"
  source="cookie"
  nameInSource="VIS"/>
  <Param name="NQ_SESSION.ACF"
  source="url"
  nameInSource="acf"/>
  </ParamList>
</ExternalLogon>
</Auth>  
[/sourcecode]
Replace the LogoffUrl according to your specifications
Check the your Oracle BI Dashboard Menu again and verify that a 'Log Out'-link is in place. Via this link you can navigate back to the Oracle  eBS Homepage.

[![](http://obibb.files.wordpress.com/2010/10/navigate-back-to-ebs.png?w=300)](http://obibb.files.wordpress.com/2010/10/navigate-back-to-ebs.png)

[](http://obibb.files.wordpress.com/2010/10/no-navigate-back-to-ebs.png)
