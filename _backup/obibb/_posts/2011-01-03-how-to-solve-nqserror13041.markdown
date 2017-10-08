---
author: makumbe
comments: true
date: 2011-01-03 14:27:05+00:00
layout: post
link: http://blog.daanalytics.nl/2011/01/03/how-to-solve-nqserror13041/
slug: how-to-solve-nqserror13041
title: 'How to solve - nqsError:13041 '
wordpress_id: 714
categories:
- OBIBB - General
tags:
- 11g
- My Oracle Support
- nQsError
- Oracle BI EE
- Security
---

When I was working on multiple catalogs, trying to merge them into one, I was presented with the following error:

"[nQsError 13041] The GUID of user 'Administrator' does not match user reference GUID at the repository. Please ask the administrator to delete the old user reference at the repository and login again"

My Oracle Support has an Doc Id; [1265802.1](https://support.oracle.com:443/CSP/ui/flash.html#tab=KBHome(page=KBHome&id=()),(page=KBNavigator&id=(bmDocTitle=GUID%20of%20user%20'Administrator'%20does%20not%20match%20user%20reference%20GUID%20at%20the%20repository&from=BOOKMARK&bmDocType=HOWTO&bmDocID=1265802.1&bmDocDsrc=KB&viewingMode=1143))) on this error. The solution to this problem is in the [documentation](http://download.oracle.com/docs/cd/E14571_01/core.1111/e10105/testprod.htm#CHDDJHHJ). There is one minor error in the documentation. You have to add the following line into the instanceconfig.xml-file;

[sourcecode language="xml"]
<ps:UpdateAccountGUIDs>UpdateAndExit<ps:UpdateAccountGUIDs>
[/sourcecode]

This should be;

[sourcecode language="xml"]
<ps:UpdateAccountGUIDs>UpdateAndExit</ps:UpdateAccountGUIDs>
[/sourcecode]


Check the '/' in the closing 'ps:UpdateAccountGUIDs'-tag.

The rest of the chapter works as documented.
