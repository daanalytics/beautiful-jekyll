---
author: makumbe
comments: true
date: 2011-02-21 11:37:42+00:00
layout: post
link: http://blog.daanalytics.nl/2011/02/21/udml-scripting/
slug: udml-scripting
title: UDML - Scripting
wordpress_id: 772
categories:
- Scripting
tags:
- Security
- Security Groups
- UDML
---

One of my clients wants to add loads of Security Groups into the repoitory. Of course this can be done manually, but in this case it would be better to script these groups into the database. I knew that UDML is an undocumneted feature in Oracle BI 10g. If you perform a search on [Google](http://lmgtfy.com/?q=%22Oracle+BI%22+UDML+security+groups), you could find enough information. I used the information provided by [Venkat](http://oraclebizint.wordpress.com/2008/04/08/oracle-bi-ee-101332-automating-import-of-usersgroups-into-repository-using-udml/) and [Andreas](http://www.trivadis.com/uploads/tx_cabagdownloadarea/andreas_nobbmann_udml_xml_02.pdf).

There was one thing I couldn't find out directly. I was looking for a possibility to nest Security Groups. It was not clear to me what the syntax should be. Again UDML to the rescue. You can use to script something into the repository. The other way around works as well. What I did was, I created a nested Security Group manually.

[![](http://obibb.files.wordpress.com/2011/02/manual-security-group.png?w=227)](http://obibb.files.wordpress.com/2011/02/manual-security-group.png)

No I was able to extract the UDML-syntax from the repository;

[sourcecode language="text"]
G:\Oracle\10g\OracleBI\server\Bin\nQUDMLGen.exe -U Administrator -P Administrator -R "Y:\webLog\OBIBB\OBIBB - UDML\groupImport.rpd" -O "Y:\webLog\OBIBB\OBIBB - UDML\securityUDML.txt"  -S
[/sourcecode]

 The '-S'  is for generating script for only security objects.

Output for 'securityUDML.txt' is as follows;

[sourcecode language="text"]
DECLARE REPOSITORY PROPERTIES (
 'CustomPresentationLayer' = '01',
 'PersistedNextUpgradeID' = '0A000000');
VERSION 1.1.184;
DECLARE SECURITY ROLE "Administrators" AS "Administrators" UPGRADE ID 2
 HAS USERS (
    "Administrator" )
 PRIVILEGES ( READ);
DECLARE SECURITY ROLE "Group01a" AS "Group01a" UPGRADE ID 4
 INHERITS FROM (
    "ManualGroup" )
 PRIVILEGES ( READ);
DECLARE SECURITY ROLE "Group01b" AS "Group01b" UPGRADE ID 6
 INHERITS FROM (
    "ManualGroup" )
 PRIVILEGES ( READ);
DECLARE SECURITY ROLE "ManualGroup" AS "ManualGroup" UPGRADE ID 9
 PROPAGATES TO (
    "Group01a",
    "Group01b" )
 PRIVILEGES ( READ);
DECLARE USER "Administrator" AS "Administrator" UPGRADE ID 3 FULL NAME {} PASSWORD 'D7EDED84BC624A917F5B462A4DCA05CDCE256EEEEEDC97D5213DF9555A8D6E566A4A72028AAD1FC28AA7433B66F722D0CEE88C996D2D894F' NEVER EXPIRES
 HAS ROLES (
    "Administrators" )
 PRIVILEGES ( READ);
[/sourcecode]

Looking add this output, you see that the subgroup 'INHERITS FROM' the parentgroup. The parentgroup 'PROPAGATES TO' the subgroup.

Now using the following script I should be able to import subgroups and parentgroups into the repository:

[sourcecode language="text"]
DECLARE SECURITY ROLE "Group01a" AS "Group01a"
 PRIVILEGES ( READ);
DECLARE SECURITY ROLE "Group01b" AS "Group01b"
 PRIVILEGES ( READ); 
DECLARE SECURITY ROLE "Group02a" AS "Group02a"
 PRIVILEGES ( READ);
DECLARE SECURITY ROLE "Group02b" AS "Group02b"
 PRIVILEGES ( READ);
DECLARE SECURITY ROLE "Group01" AS "Group01"
PROPAGATES TO ("Group01a", "Group01b")
PRIVILEGES ( READ);
DECLARE SECURITY ROLE "Group02" AS "Group02"
PROPAGATES TO ("Group02a", "Group02b")
PRIVILEGES ( READ)
;
[/sourcecode]

By using the [nqudmlexec](http://gerardnico.com/wiki/dat/obiee/executable_files/nqudmlexec)-executable, you should be able to import the parentgroups ("Group01" , "Group02") and subgroups("Group01a", "Group01b", "Group02a", "Group02b") into the repository.

[![](http://obibb.files.wordpress.com/2011/02/scripted-security-group.png?w=227)](http://obibb.files.wordpress.com/2011/02/scripted-security-group.png)

I hope the same is possible for Catalog Groups. More to come. [](http://obibb.files.wordpress.com/2011/02/scripted-security-group.png)
