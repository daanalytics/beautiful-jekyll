---
author: makumbe
comments: true
date: 2013-05-22 11:29:56+00:00
layout: post
link: http://blog.daanalytics.nl/2013/05/22/integrating-oracle-ebs-and-oracle-bi-11g-application-roles/
slug: integrating-oracle-ebs-and-oracle-bi-11g-application-roles
title: Integrating Oracle eBS Responsibility Profiles and Oracle BI 11g Application
  Roles
wordpress_id: 1373
categories:
- Oracle eBS
tags:
- 11g
- Oracle Business Analytics
---

I have been blogging earlier about the [integration](http://obibb.wordpress.com/2012/08/16/integrating-oracle-ebs-r12-and-oracle-bi-11g/) between Oracle eBS R12 and Oracle BI 11g as well as [inheriting](http://obibb.wordpress.com/2012/10/18/setup-oracle-bia-7963-data-security/) the Oracle eBS Security in Oracle BI. Instead of making a Oracle BI Application Role for each Oracle eBS Responsibility you would like to use in Oracle BI, make use of an Oracle eBS Profile Option. You could define an Oracle eBS Profile Option (e.g. XXBI_SECURITY_PROFILE - Oracle BI Security Profile) and apply this to an Oracle eBS Responsibility. This makes it easier to maintain the Security Inheritance. When you add a new Responsibility to Oracle eBS, you do not have add this Responsibility to Oracle BI. Just make sure the Oracle eBS Responsibility gets the Oracle eBS Profile Option applied or define the Oracle BI Security Profile on Site Level as a default.

The Oracle BI Security Configuration for Oracle BI basically looks like this;

[](http://obibb.files.wordpress.com/2013/05/oracle-ebs-oracle-bi-11g-security-configuration.png)[![Oracle eBS - Oracle BI 11g Security Configuration](http://obibb.files.wordpress.com/2013/05/oracle-ebs-oracle-bi-11g-security-configuration.png?w=300)](http://obibb.files.wordpress.com/2013/05/oracle-ebs-oracle-bi-11g-security-configuration.png)



So instead of matching the Oracle eBS Responsibility to a Oracle BI Application Role, match an Oracle eBS Profile Option (assigned to an Oracle eBS Responsibility or on Site Level) to a Oracle BI Application Role.

You have to follow a few steps in Oracle eBS.

**Lookup Type**

Navigate to Application Developer – Application, Lookups, Common to add a lookup type with the different values for the Oracle BI Security Profile.

You can check the values via the following query:

[sourcecode language="sql"]
select t.lookup_type
 , t.meaning
 , a.application_name
 , t.description
 from applsys.fnd_lookup_types_tl t
 , applsys.fnd_lookup_types b
 , applsys.fnd_application_tl a
 where b.lookup_type = t.lookup_type
 and b.security_group_id = t.security_group_id
 and b.view_application_id = t.view_application_id
 and a.application_id = b.application_id
 and b.lookup_type = '&XXBI_SECURITY_PROFILE'
 and t.language = '&LANGUAGE'
 and a.language = '&LANGUAGE'
;
[/sourcecode]

[sourcecode language="sql"]
select flv.lookup_code
, flv.meaning
, flv.description
from applsys.fnd_lookup_values flv
where lookup_type = '&XXBI_SECURITY_PROFILE'
and flv.language = '&LANGUAGE'
and trunc(sysdate) >= trunc(flv.start_date_active)
and trunc(sysdate) < nvl(trunc(flv.end_date_active), trunc(sysdate) +1)
;
[/sourcecode]

**Oracle BI Security Profile**

Navigate to Application Developer – Profile to add a Oracle BI Security Profile

You can check the values via the following query:

[sourcecode language="sql"]
select fpo.profile_option_name
, a.application_name
, fpotl.user_profile_option_name
, fpotl.description
from applsys.fnd_profile_options fpo
 , applsys.fnd_profile_options_tl fpotl
 , applsys.fnd_application_tl a
where fpotl.profile_option_name = fpo.profile_option_name
 and a.application_id = fpo.application_id
 and a.language = fpotl.language
 and fpo.profile_option_name = '&XXBI_SECURITY_PROFILE'
 and fpotl.language = '&LANGUAGE'
;
[/sourcecode]

Add the following code as SQL Validation

******

SQL="SELECT MEANING \"BI Security Profile\", LOOKUP_CODE
into :visible_option_value,
:profile_option_value
from applsys.fnd_lookup_values fl
where fl.lookup_type = 'Enter Lookup Type here'
and fl.language = 'Enter Language here'
and trunc(sysdate) >= trunc(fl.start_date_active)
and trunc(sysdate) <nvl(trunc(fl.end_date_active), trunc(sysdate) + 1)"
COLUMN="\"BI Security Profile\"(10)"

******

**Assign Oracle BI Security Profile to Oracle eBS Responsibility**

Navigate to System Administrator – Profile, System to assign the Oracle BI Security Profile to the Oracle eBS Responsibility

You can check the values via the following query:

Site Level (Default)

[sourcecode language="sql"]
select fpov.profile_option_value bi_type_gebruiker_site_level
 from apps.fnd_profile_options_vl fpovl
 , applsys.fnd_profile_option_values fpov
 , applsys.fnd_profile_options fpo
 , applsys.fnd_profile_options_tl fpotl
 where fpov.profile_option_id = fpovl.profile_option_id
 and fpo.profile_option_id = fpov.profile_option_id
 and fpotl.profile_option_name = fpo.profile_option_name
 and fpov.level_id = 10001 -- Site
 and fpotl.user_profile_option_name = '&XXBI_SECURITY_PROFILE'
 and fpotl.language = '&LANGUAGE'
;
[/sourcecode]



Responsibility Level (Specific)

[sourcecode language="sql"]
select fr.responsibility_id
 , fr.responsibility_name
 , fpov.profile_option_value bi_type_gebruiker_resp_level
 from apps.fnd_responsibility_vl fr
 , applsys.fnd_profile_option_values fpov
 , applsys.fnd_profile_options fpo
 , applsys.fnd_profile_options_tl fpotl
 where fpov.level_value = fr.responsibility_id
 and fpo.profile_option_id = fpov.profile_option_id
 and fpotl.profile_option_name = fpo.profile_option_name
 and fpov.level_id = 10003 -- Responsibility
 and fpotl.user_profile_option_name = '&XXBI_SECURITY_PROFILE'
 and fpotl.language = '&LANGUAGE'
[/sourcecode]

The remainder of the setup in the Oracle Enterprise Manager and the actual match via an Initialization Block is described [here](http://obibb.wordpress.com/2012/10/18/setup-oracle-bia-7963-data-security/). The following query could be used to retrieve the Oracle eBS Profile Option and assign it to the ROLES-session variable

**Oracle BI Initialization Block: GetApplicationRoles**

[sourcecode language="sql"]
select NVL ( rl.bi_security_profile_resp_level
 , sl.bi_security_profile_site_level ) bi_type_gebruiker
 from ( select fpov.profile_option_id
 , fpotl.language
 , fpov.profile_option_value
 bi_type_gebruiker_resp_level
 from applsys.fnd_responsibility fr
 , applsys.fnd_profile_option_values fpov
 , applsys.fnd_profile_options fpo
 , applsys.fnd_profile_options_tl fpotl
 where fpov.level_value = fr.responsibility_id
 and fpo.profile_option_id = fpov.profile_option_id
 and fpotl.profile_option_name = fpo.profile_option_name
 and fpov.level_id = 10003
 and fpo.profile_option_name = '&XXBI_SECURITY_PROFILE'
 and fpotl.language = '&LANGUAGE'
 and fr.responsibility_id = fnd_global.resp_id
 and fr.application_id = fnd_global.resp_appl_id
 ) rl
 , ( select fpov.profile_option_id
 , fpotl.language
 , fpov.profile_option_value
 bi_type_gebruiker_site_level
 from applsys.fnd_profile_option_values fpov
 , applsys.fnd_profile_options fpo
 , applsys.fnd_profile_options_tl fpotl
 where fpo.profile_option_id = fpov.profile_option_id
 and fpotl.profile_option_name = fpo.profile_option_name
 and fpov.level_id = 10001
 and fpo.profile_option_name = '&XXBI_SECURITY_PROFILE'
 and fpotl.language = '&LANGUAGE' ) sl
 where sl.language = rl.language(+)
 and sl.profile_option_id = rl.profile_option_id(+)
[/sourcecode]

Feel free to comment.
