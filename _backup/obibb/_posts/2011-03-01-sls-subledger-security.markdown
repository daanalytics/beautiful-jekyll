---
author: makumbe
comments: true
date: 2011-03-01 11:24:25+00:00
layout: post
link: http://blog.daanalytics.nl/2011/03/01/sls-subledger-security/
slug: sls-subledger-security
title: 'SLS: Subledger Security'
wordpress_id: 767
categories:
- Oracle eBS
tags:
- R12
- RLS
- Security
- SLS
- Subledger Security
- VPD
---

I am in the proces of implementing [security](http://obibb.wordpress.com/2010/12/20/oracle-bi-applications-security/) for Oracle BI Apps 7.9.6 in a Oracle eBS R12 environment. One of the requirements is Subledger Security ([User Guide](http://download.oracle.com/docs/cd/B40089_10/current/acrobat/120igiug.pdf), [My Oracle Support](https://support.oracle.com/CSP/ui/flash.html#tab=KBHome(page=KBHome&id=()),(page=KBNavigator&id=(bmDocID=463082.1&bmDocTitle=Oracle%20Public%20Sector%20Financials%20(International)%20Documentation%20Resources,%20Release%2012&viewingMode=1143&from=BOOKMARK&bmDocType=REFERENCE&bmDocDsrc=KB)))).

As per the documentation; **Subledger Security** is an extension to Oracle Financials that enables the user to selectively partition data within a single install of Oracle Financials. Subledger Security provides a system where all business units can access their own financial information only.

In my clients case it makes it possible to secure parties, customers and suppliers. Certain customers are only visible for selected responsibilities within the same operating unit.

For implementing the security I am interested in the database-implementation of SLS. Check the following diagram:

[![](http://obibb.files.wordpress.com/2011/02/erd-sls-security.png?w=300)](http://obibb.files.wordpress.com/2011/02/erd-sls-security.png)

For all the Subledger Security tables you have to refer to the IGI-scheme in Oracle eBS:



	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_ALLOCATIONS](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_ALLOCATIONS&c_owner=IGI&c_type=TABLE)

	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_ALLOCATIONS_AUDIT](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_ALLOCATIONS_AUDIT&c_owner=IGI&c_type=TABLE)

	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_CONSOLIDATE_GROUPS](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_CONSOLIDATE_GROUPS&c_owner=IGI&c_type=TABLE)

	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_GROUPS](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_GROUPS&c_owner=IGI&c_type=TABLE)

	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_GROUPS_AUDIT](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_GROUPS_AUDIT&c_owner=IGI&c_type=TABLE)

	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_SECURE_TABLES](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_SECURE_TABLES&c_owner=IGI&c_type=TABLE)

	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_SECURE_TABLES_AUDIT](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_SECURE_TABLES_AUDIT&c_owner=IGI&c_type=TABLE)

	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_SECURITY_GROUP_ALLOC](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_SECURITY_GROUP_ALLOC&c_owner=IGI&c_type=TABLE)

	
  * ![Table](http://etrm.oracle.com/images/table_defn.gif)[IGI_SLS_UPG_ITF](http://etrm.oracle.com/pls/et1211d9/etrm_pnav.show_object?c_name=IGI_SLS_UPG_ITF&c_owner=IGI&c_type=TABLE)


Whether Subledger Security is applied depends on two profiles;

	
  * 'Subledger Security : Security Group'

	
  * 'Subledger Security : SLS Responsibility'


A query to retrieve the values of these profiles could be;

[sourcecode language="sql"]

SELECT r.responsibility_id ,
  r.responsibility_key ,
  r.responsibility_name ,
  nvl(sr.profile_option_value, 'N') sls_responsibility ,
  nvl(sg.profile_option_value, 'No SLS Responsibility') sls_security_group ,
  nvl(i.sls_group, 'No SLS Responsibility') sls_group
FROM
  (SELECT t.profile_option_name ,
    t.user_profile_option_name ,
    v.level_id ,
    v.profile_option_value ,
    r.responsibility_id ,
    r.responsibility_key ,
    r.responsibility_name
  FROM fnd_profile_options_tl t ,
    fnd_profile_options p ,
    fnd_profile_option_values v ,
    fnd_responsibility_vl r
  WHERE t.profile_option_name    = p.profile_option_name
  AND p.application_id           = v.application_id
  AND p.profile_option_id        = v.profile_option_id
  AND r.responsibility_id        = v.level_value
  AND v.level_id                 = 10003 -- Responsibility
  AND t.user_profile_option_name = 'Subledger Security : Security Group'
  AND t.language                 = 'US'
  ) sg ,
  (SELECT t.profile_option_name ,
    t.user_profile_option_name ,
    v.level_id ,
    v.profile_option_value ,
    r.responsibility_id ,
    r.responsibility_key ,
    r.responsibility_name
  FROM fnd_profile_options_tl t ,
    fnd_profile_options p ,
    fnd_profile_option_values v ,
    fnd_responsibility_vl r
  WHERE t.profile_option_name    = p.profile_option_name
  AND p.application_id           = v.application_id
  AND p.profile_option_id        = v.profile_option_id
  AND r.responsibility_id        = v.level_value
  AND v.level_id                 = 10003 -- Responsibility
  AND t.user_profile_option_name = 'Subledger Security : SLS Responsibility'
  AND t.language                 = 'US'
  ) sr ,
  igi_sls_groups i,
  fnd_responsibility_vl r
WHERE sr.responsibility_id = sg.responsibility_id (+)
AND sr.responsibility_id (+)  = r.responsibility_id
AND i.sls_group (+)        = sg.profile_option_value ;

[/sourcecode]

Other queries to find out which data a responsibility is allowed to view:

The query below gives insight in the available SLS Security Groups, eg".: 'AR Security for Dept A'

[sourcecode language="sql"]
SELECT sls_groups --'AR Security for Dept A' 
FROM   igi_sls_groups
WHERE  sls_group_type = 'S';
[/sourcecode]

The query below gives insight in which tables are 'SLS Security'-enabled within a certain SLS Security Group.

[sourcecode language="sql"]
SELECT sls_group --'AR Security for Dept A'
,      table_name -- HZ_PARTIES 
FROM   igi_sls_enabled_alloc_v;
[/sourcecode]

The query below gives insight in which 'IG_SLS_#'-table the 'SLS-Security'-details are stored. Depending on the configuration, multiple 'IG_SLS_#'-tables  (IG_SLS_1, IG_SLS_2, IG_SLS_3, IG_SLS_4, IG_SLS_5, etc.) can exist.

[sourcecode language="sql"]
SELECT owner -- AR
,      table_name -- HZ_PARTIES
,      sls_table_name -- IG_SLS_1 
FROM igi_sls_secure_tables;
[/sourcecode]

The query below gives insight in the actual id's which are secured by the 'SLS-Security'-settings. The rowid of the source table is stored in the 'IG_SLS_#'-table.

[sourcecode language="sql"]
SELECT sls1.sls_rowid    
,      sls1.sls_sec_grp    
,      p1.party_id    
,      p1.party_number    
,      p1.party_name 
FROM   igi_sls_1 sls1 -- HZ_PARTIES    
,      hz_parties p1
WHERE  p1.ROWID = sls1.sls_rowid;
[/sourcecode]

Using these queries, you should be able to select which id's are available to a selected responsibility. Within the Oracle eBS R12 application, this is managed by [policies](http://apps2fusion.com/apps/21-technical/129-moglobal-dive-into-r12-multi-org-design) (VPD - Virtual Private Database, RLS - Row Level Security)

Check the following query, to see how it's setup;

[sourcecode language="sql"]
select object_owner --'AR'
,      object_name  -- 'HZ_PARTIES'
,      policy_name  -- 'IGI_SLS_3_POL'
,      pf_owner     -- 'APPS'
,      function     --'IGI_SLS_1_FUN'
from   dba_policies
where  policy_name like 'IGI%'
[/sourcecode]
With this information I am able to built 'SLS Security' into Oracle BI Applications.
