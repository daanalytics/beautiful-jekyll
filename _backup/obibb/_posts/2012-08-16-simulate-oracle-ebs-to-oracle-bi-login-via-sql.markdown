---
author: makumbe
comments: true
date: 2012-08-16 08:26:25+00:00
layout: post
link: http://blog.daanalytics.nl/2012/08/16/simulate-oracle-ebs-to-oracle-bi-login-via-sql/
slug: simulate-oracle-ebs-to-oracle-bi-login-via-sql
title: Simulate Oracle eBS to Oracle BI login via SQL
wordpress_id: 1194
categories:
- Oracle eBS
tags:
- 11g
- Oracle Business Analytics
- R12
- Security
---

There is an interesting (for me at least) topic on [OTN](https://forums.oracle.com/forums/thread.jspa?threadID=2416106&start=0&tstart=0) about integrating Oracle eBS security into Oracle BI. It is a topic about getting Oracle eBS HR-Security to work in Oracle BI. Robin Moffat has a [blogpost](https://rnm1978.wordpress.com/2010/05/17/validating-ebs-bi-authentication-without-bi/) about;  'Validating EBS-BI authentication, without BI'. He refers to an My Oracle Support article ([758392.1](https://supporthtml.oracle.com/ep/faces/secure/km/DocumentDisplay.jspx?id=758392.1&h=Y)), which provides some (additional) troubleshooting details.

When I want to simulate Oracle eBS to Oracle BI login via SQL, I use some SQL-statements / scripts, to see what happens or at least should happen. If I need to know which HR-Orgs I could expect based on the Oracle eBS HR-Security I use the following scripts;

**Query User - Responsibility -- Rol**

Check which responsibilities a user has within Oracle eBS.
[sourcecode language="sql"]
select fu.user_id
 , frv.responsibility_id
 , fa.application_id
 , frv.responsibility_key
 , frv.responsibility_name
 from apps.fnd_responsibility_vl frv
 , applsys.fnd_application fa
 , applsys.fnd_request_groups frg
 , apps.fnd_user_resp_groups_all furga
 , applsys.fnd_user fu
 where fa.application_id = frv.application_id
 and TRUNC ( SYSDATE ) between fu.start_date
 and NVL ( fu.end_date
 , to_date ( '31-DEC-4712'
 , 'DD-MON-YYYY' ) )
 and fu.user_id = furga.user_id
 and TRUNC ( SYSDATE ) between furga.start_date
 and NVL ( furga.end_date
 , to_date ( '31-DEC-4712'
 , 'DD-MON-YYYY' ) )
 and furga.responsibility_id = frv.responsibility_id
 and frv.request_group_id = frg.request_group_id(+)
 and fu.user_name like :p_user_name
 and frv.responsibility_name like :p_responsibility_name
order by frv.responsibility_name
[/sourcecode]


**Excecute Apps Initialize**

Run the Apps Initialize script to get the session in context of the user / responsibility combination of your choice, based on the previous query.
[sourcecode language="sql"]
BEGIN
apps.fnd_global.apps_initialize(user_id, resposnsibility_id, resposnsibility_application_id, security_group_id);
END;
[/sourcecode]


**Validate the Context**

Check the output of the previous step
[sourcecode language="sql"]
select fnd_global.resp_id
 , fnd_global.resp_appl_id
 , fnd_global.security_group_id
 , fnd_global.resp_name
 , fnd_global.user_id
 , fnd_global.employee_id
 , fnd_global.user_name
 , ( select distinct responsibility_key
 from fnd_responsibility
 where responsibility_id = fnd_global.resp_id )
 responsibility_key
 from DUAL
[/sourcecode]


**Validate HR-Security**

If all the above steps have completed like expected, you are able to check the query within the Oracle BI Initialization Block (IB) related to HR-Security. In my case it's IB; 'HR Organization'. This IB has the following query;
[sourcecode language="sql"]
SELECT
 DISTINCT 'HR_ORG'
,TO_CHAR(SEC_DET.ORGANIZATION_ID)
FROM
(
SELECT
 'HR_ORG',
 ASG.ORGANIZATION_ID
FROM
 FND_USER_RESP_GROUPS URP
,FND_USER USR
,PER_SECURITY_PROFILES PSEC
,PER_PERSON_LIST PER
,PER_ALL_ASSIGNMENTS_F ASG
WHERE
 URP.START_DATE < TRUNC(SYSDATE)
AND (CASE WHEN URP.END_DATE IS NULL THEN TRUNC(SYSDATE) ELSE TO_DATE(URP.END_DATE) END) >= TRUNC(SYSDATE)
AND USR.USER_NAME = 'VALUEOF(NQ_SESSION.USER)'
AND USR.USER_ID = URP.USER_ID
AND TRUNC(SYSDATE)
 BETWEEN URP.START_DATE AND NVL(URP.END_DATE, HR_GENERAL.END_OF_TIME)
AND PSEC.SECURITY_PROFILE_ID = FND_PROFILE.VALUE_SPECIFIC('PER_SECURITY_PROFILE_ID', URP.USER_ID, URP.RESPONSIBILITY_ID, URP.RESPONSIBILITY_APPLICATION_ID)
AND PER.SECURITY_PROFILE_ID = PSEC.SECURITY_PROFILE_ID
AND PER.PERSON_ID = ASG.PERSON_ID
AND ASG.PERSON_ID = USR.EMPLOYEE_ID
AND TRUNC(SYSDATE) BETWEEN ASG.EFFECTIVE_START_DATE AND ASG.EFFECTIVE_END_DATE
AND URP.RESPONSIBILITY_ID = DECODE(FND_GLOBAL.RESP_ID,
 -1, URP.RESPONSIBILITY_ID,
 NULL, URP.RESPONSIBILITY_ID,
 FND_GLOBAL.RESP_ID)
UNION
SELECT DISTINCT 'HR_ORG',
 ORGANIZATION_ID
FROM PER_ALL_ASSIGNMENTS_F ASG,
 FND_USER USR
WHERE ASG.PERSON_ID = USR.EMPLOYEE_ID
AND USR.USER_NAME = 'VALUEOF(NQ_SESSION.USER)'
AND TRUNC(SYSDATE) BETWEEN ASG.EFFECTIVE_START_DATE AND ASG.EFFECTIVE_END_DATE
AND ASG.PRIMARY_FLAG = 'Y'
) SEC_DET
[/sourcecode]


You should replace the 'VALUEOF(NQ_SESSION.USER)' part with either the user or fnd_global.user_name.

Now you are able to see whether the Initialization Block is working like expected and retrieves the same values as it does in Oracle eBS. If you can conform these steps and the the Security isn't working, it's probably because one of the related IB's doesn't retrieve (all) the necessary values.

This whole post assumes that the [integration ](http://obibb.wordpress.com/2012/08/16/integrating-oracle-ebs-r12-and-oracle-bi-11g/)is setup correctly.

Good Luck.
