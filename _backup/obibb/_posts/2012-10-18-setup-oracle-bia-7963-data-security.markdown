---
author: makumbe
comments: true
date: 2012-10-18 10:30:23+00:00
layout: post
link: http://blog.daanalytics.nl/2012/10/18/setup-oracle-bia-7963-data-security/
slug: setup-oracle-bia-7963-data-security
title: Setup Oracle BIA 7963 - Data Security
wordpress_id: 1229
categories:
- Oracle eBS
tags:
- 11g
- Data Security
- Oracle BI EE
- R12
- Security
---

Customer wants to secure their data based on things like Ledger, Company, Operating Unit, etc. All users who login via Oracle eBS should inherit (based on the current responsibility) the same security settings in Oracle BI. The following is a possible solution.




**Environment**






	
  * Oracle eBS R12.1.1

	
  * Oracle BI EE 11.1.1.6.0

	
  * Oracle BIA 7.9.6.3




**Setup**


The setup consists of a few different parts



	
  * [Integration Oracle eBS and Oracle BI](http://obibb.wordpress.com/2012/08/16/integrating-oracle-ebs-r12-and-oracle-bi-11g/)

	
  * Data Security


**Data Security**

The Data Security is based on different Roles and a Profile Option assigned to the responsibilities in Oracle eBS

**Oracle eBS**



	
  * Create 'BI Type User'-profile option**
**

	
  * Assign 'BI Type User'-profile option to Responsibility**
**

	
  * Assign Responsibility to User**
**


Each Responsibility has either a specific 'BI Type User'-profile option or a 'BI Type User'-profile option on Site level. A view (xx_obia_user_groups_v) in Oracle eBS 'holds' the profile option information.

[sourcecode language="sql"]
select fpov.level_value responsibility_id
 , fpov.level_value_application_id application_id
 , 'OBIA '
 || fpov.profile_option_value autorisatierol_code
 , fl.meaning autorisatierol
 from applsys.fnd_profile_option_values fpov
 , apps.fnd_profile_options_vl fpo
 , apps.fnd_lookups fl
 where fpo.profile_option_id = fpov.profile_option_id
 and fpo.application_id = fpov.application_id
 and fpov.profile_option_value = fl.lookup_code
 and fl.lookup_type = 'BI_TYPE_GEBRUIKER'
 and fpo.profile_option_name = 'XXBI_TYPE_GEBRUIKER'
 and fpov.level_id = 10003
[/sourcecode]

**Oracle BI**

In Oracle BI, there is a Initialization Block which populates the; ROLES Session Variable

[sourcecode language="sql"]
select ( select sector
 from apps.xx_obia_user_groups_v
 where responsibility_key = 'VALUEOF(NQ_SESSION.OLTP_EBS_RESP_KEY)'
 and responsibility_id = valueof ( nq_session.oltp_ebs_resp_id ) )
 || ';'
 || ( select autorisatierol_code &quot;ROLES&quot;
 from apps.xx_obia_user_groups_v
 where responsibility_key = 'VALUEOF(NQ_SESSION.OLTP_EBS_RESP_KEY)'
 and responsibility_id = valueof ( nq_session.oltp_ebs_resp_id ) )
 || ';'
 || ( select responsibility_key &quot;ROLES&quot;
 from apps.xx_obia_user_groups_v
 where responsibility_key = 'VALUEOF(NQ_SESSION.OLTP_EBS_RESP_KEY)'
 and responsibility_id = valueof ( nq_session.oltp_ebs_resp_id ) )
 &quot;ROLES&quot;
 from DUAL
[/sourcecode]

![](http://obibb.files.wordpress.com/2012/10/100212_1017_setuporacle7.png)

![](http://obibb.files.wordpress.com/2012/10/100212_1017_setuporacle8.png)

**Oracle Enterprise Manager (EM)**

In the EM 'all' the different Application Roles, related to the Data Security are created.

There are a few different Application Roles;



	
  * Out-of the box

	
  * ********Data Security

	
  * eBS Profile


**Out-of-the-Box**



	
  * BIAdministrators

	
    * Administration privileges.




	
  * BIAuthors

	
    * Create, use or consume content.




	
  * BIConsumers

	
    * Use / consume content,

	
    * Every authenticated user.




	
  * BISystem

	
    * Component connections between products.





![](http://obibb.files.wordpress.com/2012/10/100212_1017_setuporacle9.png)

**Data Security & eBS Profile**

![](http://obibb.files.wordpress.com/2012/10/100212_1017_setuporacle10.png)

**Oracle BI Administrator (Identity Manager)**

In the Identity Manager, the Business Model Filters are applied to the Data Security Application Roles

![](http://obibb.files.wordpress.com/2012/10/100212_1017_setuporacle11.png)

![](http://obibb.files.wordpress.com/2012/10/100212_1017_setuporacle12.png)

![](http://obibb.files.wordpress.com/2012/10/100212_1017_setuporacle13.png)

The Business Model Filters are based on the Initialization Blocks. Some out-of-the-box, others custom.

This setup should be sufficient to apply Data Security to all queries, which query the Logical Tables with the Business Model Filters applied to it.

**Note: **Application roles data filters won't apply for users with BI Administrator role.

By definition the BIAdministrator application role is granted the "oracle.bi.server.manageRepositories" permission, which is equivalent to the 10g "Administrator" user who also had unrestricted access. Hence, data filters won't affect users with BIAdministrator Role. (source: Oracle Support)


###### Related articles





	
  * [Integrating Oracle eBS R12 and Oracle BI 11g](http://obibb.wordpress.com/2012/08/16/integrating-oracle-ebs-r12-and-oracle-bi-11g/) (obibb.wordpress.com)


