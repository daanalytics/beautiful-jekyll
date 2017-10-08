---
author: makumbe
comments: true
date: 2010-07-01 15:45:23+00:00
layout: post
link: http://blog.daanalytics.nl/2010/07/01/change-a-physical-table-to-an-alias-of-a-different-physical-table/
slug: change-a-physical-table-to-an-alias-of-a-different-physical-table
title: Change a Physical table to an Alias of a different Physical table
wordpress_id: 250
tags:
- Alias
- Physical Layer
- Physical Table
- UDML
---

[](http://obibb.files.wordpress.com/2010/07/udml-physical-table.png)[](http://obibb.files.wordpress.com/2010/07/udml-command.png)[](http://obibb.files.wordpress.com/2010/07/udml-physical-table-update.png)[](http://obibb.files.wordpress.com/2010/07/udml-command-update.png)[](http://obibb.files.wordpress.com/2010/07/physical-table-update.png)Sometimes you have to make some changes in your physical model, because of changes in the underlying datamodel. This could be a lot of work. In this case UDML could come in handy. I am sure [Andreas Nobbmann](http://blog.trivadis.com/blogs/andreasnobbmann/archive/2008/04/11/good-news-you-really-need-no-mouse-for-oracle-bi-ee-administrator.aspx) will agree.

**Picture the following;**

You have created a physical table with relationships.
[![](http://obibb.files.wordpress.com/2010/07/physical-table.png?w=278)](http://obibb.files.wordpress.com/2010/07/physical-table.png)

When you want to change the actual source of your  physical table you realize that you should have used an alias instead of the actual physical table.

What to do?

With the following scripting you can change the physical table to an alias of a different physical table. This could also be used to change the source of an already existing alias or multiple aliases, or add columns etc.

For an example and reference of how to use udml to change a repository variable script-wise, please check [Venkat’s ‘old’ blog](http://oraclebizint.wordpress.com/2008/04/04/oracle-bi-ee-101332-udml-to-automate-repository-updates-migration-of-repositories-from-development-to-testproduction-environment/).
****

**Step 1.**

Produce a UDML script of your source repository:

C:\oracle\bise1\bi\server\Bin>nqudmlgen -U Administrator -P Administrator -R C:\oracle\bise1\bi\server\Repository\OBIBB.rpd -O C:\temp\udml\source.udml
[![](http://obibb.files.wordpress.com/2010/07/udml-command.png?w=300)](http://obibb.files.wordpress.com/2010/07/udml-command.png)

Look for the definition of your physical table in source.udml. The definition runs from “DECLARE TABLE” until “PRIVILEGE ( READ);”

[![](http://obibb.files.wordpress.com/2010/07/udml-physical-table.png?w=300)](http://obibb.files.wordpress.com/2010/07/udml-physical-table.png)

**Step 2. **

Copy the statement to a seperate text-file:

**Step 3.**

Modify the statement and add new source to physical table:

[![](http://obibb.files.wordpress.com/2010/07/udml-physical-table-update.png?w=300)](http://obibb.files.wordpress.com/2010/07/udml-physical-table-update.png) 

In essence the physical table “DIM_TABLE_CONF_1” will become an alias which references a different physical table “DIM_TABLE_CONF_3”.

Save as update.udml

**Step 4.**

Execute update:

nqudmlexec -U Administrator -P Administrator -I C:\temp\udml\update_source.udml -B C:\oracle\bise1\bi\server\Repository\OBIBB.rpd -O C:\oracle\bise1\bi\server\Repository\updated_OBIBB.rpd

**[![](http://obibb.files.wordpress.com/2010/07/udml-command-update.png?w=300)](http://obibb.files.wordpress.com/2010/07/udml-command-update.png)**

**Step 5**.

Check the result in the updated repository, in this case; updated_OBIBB.rpd

[![](http://obibb.files.wordpress.com/2010/07/physical-table-update.png?w=278)](http://obibb.files.wordpress.com/2010/07/physical-table-update.png)


[![Bookmark and Share](http://s7.addthis.com/static/btn/v2/lg-share-en.gif)](http://www.addthis.com/bookmark.php?v=250&username=makumbe)

