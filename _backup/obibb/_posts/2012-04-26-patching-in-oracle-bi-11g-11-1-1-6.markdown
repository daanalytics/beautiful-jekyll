---
author: makumbe
comments: true
date: 2012-04-26 10:48:31+00:00
layout: post
link: http://blog.daanalytics.nl/2012/04/26/patching-in-oracle-bi-11g-11-1-1-6/
slug: patching-in-oracle-bi-11g-11-1-1-6
title: Patching in Oracle BI 11g 11.1.1.6
wordpress_id: 1121
categories:
- Oracle BI 11g
tags:
- 11.1.1.6.0
- 11g
- Opatch
- Oracle BI EE
- Patch
---

Last week the [announcement](https://blogs.oracle.com/proactivesupportEPM/entry/obiee_11_1_1_62) came that there has been a Patch (13742915) released for Oracle BI EE 11.1.1.6.1. This Patch can be dowloaded via [Oracle Support](https://supporthtml.oracle.com/) (Login required).

If you want to apply the Patch, you have to perform a few steps. These steps can differ, depending on which steps you may or may not already have executed.

Start by downloading the Patch first.

**Download Patch 13742915**
--------------------------------

1. Navigate to 'Patches & Updates'
2. Search for Patch 13742915
3. Select the required OS (I installed on Windows 64-bit)
4. Dowload the Patch

When the Patch has been dowloaded, go to your Oracle BI environment for the installation of the Patch. The following steps have to be performed.

**Patch Installation for server**
--------------------------------
1. Stop all BI Services, including BI Server, BI Administration Tool, BI Javahost, BI Scheduler (Start->Programs->Oracle BI->Stop BI Services)
2. Backup ORACLE_HOME\bifoundation\server
3. Backup ORACLE_INSTANCE\bifoundation\OracleBIServerComponent\coreapplication_obis1\repository
4. Apply Patch using Opatch (See below)
5. Start all BI Services
6. Test the Patch
7. If needed, rollback the Patch (See below)

**Apply Patch using Opatch**
--------------------------------

**Note:** Make sure all BI Services have stopped

Check Oracle Support; 'OBIEE 11g: How to Apply Patches Using Opatch' (Id - 1220799.1)

1. Verify whether you have (the latest) version of [Opatch](http://www.orafaq.com/wiki/Opatch) installed

a) If needed install a new version of the Opatch utility (See below)
Make sure ....

... the ORACLE_HOME variable exists --> set ORACLE_HOME=MIDDLEWARE_HOME\Oracle_BI1

----
-- **Side-note from Oracle:** "You are setting ORACLE_HOME for this command-prompt session only.
-- This is set to only facilitate patch application/rollback/inventory, etc.
-- Do not make this a permanent environment variable as it will affect other Oracle Products running
-- on your system which may need a permanent ORACLE_HOME environment variable."
----

... the OPATCH-directory is in your PATH --> set PATH=%PATH%;ORACLE_HOME\OPatch

2. Read through the README.txt
3. Download the Patch to the PATCH_TOP directory (in my case; Z:\Oracle\FMW\OracleBIAdmin\PATCH_TOP)
4. CD to Patch directory (in my case; Z:\Oracle\FMW\OracleBIAdmin\PATCH_TOP\13742915)
5. Apply Patch
a) run "opatch apply" (without quotes)
-- If you are running a 64-bit OS: Windows64bit / Linux 64bit / AIX 64bit
b) run "patch apply -jre %ORACLE_HOME%/jdk/jre" (without quotes)
6. OPatch succeeded
7. Verify the succesful installation
a) run "opatch lsinventory" (without quotes)
-- If you are running a 64-bit OS: Windows64bit / Linux 64bit / AIX 64bit
b) run "opatch lsinventory -jre %ORACLE_HOME%/jdk/jre" (without quotes)
8. OPatch succeeded

**Note:** All BI Services can be started

**Rollback the Patch using Opatch**
--------------------------------
1. CD to Patch directory (in my case; Z:\Oracle\FMW\OracleBIAdmin\PATCH_TOP\13742915)
2 Rollback Patch
a) run "opatch rollback -id 13742915" (without quotes)
-- If you are running a 64-bit OS: Windows64bit / Linux 64bit / AIX 64bit
b) run "opatch rollback -id 13742915 -jre %ORACLE_HOME%/jdk/jre" (without quotes)

**How to install the Opatch utility**
---------------------------------------

1. Navigate to 'Patches & Updates'
2. Search for Patch 6880880
3. Select the required OS (I installed on Windows 64-bit)
4. Dowload the Patch
5. Extract the zip file directly under the ORACLE_HOME (MIDDLEWARE_HOME\Oracle_BI1).
6. Backup ORACLE_HOME\OPatch
7. Make sure no directory ORACLE_HOME\OPatch exist
8. Unzip the OPatch downloaded zip into the ORACLE_HOME directory
9. check the version of the OPatch utility
a) ORACLE_HOME\OPatch
b) run "opatch version" (without quotes)

Good Luck!
