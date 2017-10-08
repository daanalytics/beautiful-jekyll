---
author: harzing
comments: true
date: 2014-04-07 12:44:25+00:00
layout: post
link: http://blog.daanalytics.nl/2014/04/07/weblogic_obiee_ssl/
slug: weblogic_obiee_ssl
title: Set up https (SSL) for Weblogic and OBIEE
wordpress_id: 1588
categories:
- OBIBB - General
- Oracle BI EE
- Setup
tags:
- OBIEE
- Oracle WebLogic Server
- Security
- SSL
---

I have been blogging about the [integration](http://obibb.wordpress.com/2012/08/16/integrating-oracle-ebs-r12-and-oracle-bi-11g/) between Oracle eBS and Oracle BI EE. Apart from the integration, there are are few assumptions:



	
  * Oracle eBS is installed

	
  * Oracle BI is installed

	
  * Oracle eBS and Oracle BI are compatible with each other (http vs. https)

	
  * All necessary Oracle eBS patches are installed

	
    * R11 check

	
    * R12 included




	
  * The Web Browser should be able to accept cookies

	
  * The ICX session cookie name is case-sensitive

	
  * Oracle eBS and Oracle BI should be installed into the same domain (machine1.domain.ext = machine2.domain.ext)


At one of our clients we were confronted with the fact that in a new environment, Oracle eBS runs on https while our Oracle BI environment was still http. This conflicts with one of the assumptions above.

This blog entry is inspired by: [Debashis Paul](http://debaatobiee.wordpress.com/2011/10/28/obiee-11g-ldap-with-https-ssl-setup/) by guest authors [Menno Harzing](http://harzing.net/) and [Rob Chou](http://www.linkedin.com/pub/roberto-chou/4/487/851). We have added cluster-configuration and changed the numbering.

These steps are followed to protect your data-transport from/to OBIEE via the internet.
There are two parts described below to accomplish this:

**Part One - Configuration under Weblogic Console**
**Part Two – Configuration under OFMW Enterprise Manager**


### Part One – Configuration under Weblogic Console





	
  1. Login to Weblogic Administration Console.

	
  2. Click on Environments -) Servers -) AdminServer (admin) -) General tab

	
  3. Click Lock and Edit from the left pane.

	
  4. Check the ‘SSL Listen Port Enabled’ as 7022
(this is not the default SSL port, so please check yours and modify based on that)
This will ensure that you will be able to access the URL using 7022 port using https://

	
  5. Check also ‘Listen Port Enabled’ if you also want to access BI URL using http://
[![Image](http://obibb.files.wordpress.com/2014/04/screen-shot-2014-04-01-at-11-54-43.png?w=650)](http://obibb.files.wordpress.com/2014/04/screen-shot-2014-04-01-at-11-54-43.png)

	
  6. Save the configuration
the location of the resulting file is found at /u01/app/oracle/product/fmw/user_projects/domains/<DOMAIN_NAME>/config/config.xml

	
  7. Activate the changes from left pane

	
  8. Change BIEE_MANAGER_URL in start_stop_obiee.sh
and ADMIN_URL in startManagedWeblogic.sh
from t3://…PORT (e.g. 7001) to https://….:SSL-PORT (e.g. 7002)

	
  9. Restart the Weblogic Servers(Admin/Managed) and BI Servers components

	
  10. Accept the exception in browser when it prompts for it and continue accessing BI URL in secure HTTPS protocol(Note that once this has been made as https:// you have to access OFWM EM Control page and Weblogic Console page also in https:// going forward)


### Part Two – Configuration under OFMW Enterprise Manager




	
  11. Navigate to “<OFMW Home>\user_projects\domains\bifoundation_domain\bin” and take backup of startManagedWebLogic.cmd

	
  12. Edit and locate section with below content (**on 1 line**):JAVA_OPTIONS="-Dweblogic.security.SSL.trustedCAKeyStore="/u01/app/oracle/product/fmw/wlserver_10.3/server/lib/cacerts" ${JAVA_OPTIONS}"

	
  13. Replace the above with below: (Kindly note that you have to change the OFMW Home path as applicable to your environment)JAVA_OPTIONS="-Djavax.net.ssl.trustStore="/u01/app/oracle/product/fmw/wlserver_10.3/server/lib/DemoTrust.jks" -Djavax.net.ssl.trustStorePassword="

	
  14. Restart all the services of Weblogic (Admin/Managed/opmnctl/Node Manager/Process Manager)

	
  15. Log in to OFMW Enterprise managerIn the next steps via the System MBean browser SSL across all BI components will be configured

	
  16. Open System MBean Browser
[![Image](http://obibb.files.wordpress.com/2014/04/systemmbeanbrowser.png?w=598)](http://obibb.files.wordpress.com/2014/04/systemmbeanbrowser.png)

	
  17. Invoke the Lock of BIDomain.
[![Image](http://obibb.files.wordpress.com/2014/04/lockbidomain.png?w=650)](http://obibb.files.wordpress.com/2014/04/lockbidomain.png)

	
  18. Now we have to generate the certificates required as a prerequisite for enabling SSL,
using the specified passphrase to protect both certificate stores and private keys.
This enables internal https calls to the web server.
The certificate type (pem or der) must be explicitly stated.Navigate to oracle.biee.admin –> bifoundation_domain –> BIDomain.BIInstance.SecurityConfiguration
click on the BIDomain.BIInstance.SecurityConfiguration MBean.
Click on the operation tab click on “generateSSLCertificates”.
[![Image](http://obibb.files.wordpress.com/2014/04/generatesslcertificates.png?w=650)](http://obibb.files.wordpress.com/2014/04/generatesslcertificates.png)

	
  19. Enter the details asked for: For my case I have included below:
Passphrase : ><change_password><
webServerCACertificatePath : /wlserver_10.3/server/lib/CertGenCA.der
certificateEncoding is: der

	
  20. Now click on Invoke

	
  21. Return to the path specified in step 17

	
  22. Click on simpleCommit (two items below lock).

	
  23. Repeat step 17 to lock

	
  24. Enable SSL for BI_SERVER1 on Weblogic Console (the same way as part 1, step 5)
[![Image](http://obibb.files.wordpress.com/2014/04/enablesslbiserverconsole.png?w=650)](http://obibb.files.wordpress.com/2014/04/enablesslbiserverconsole.png)

	
  25. perform step 22 for simpleCommit.

	
  26. Restart all the services of Weblogic (Admin/Managed/opmnctl/Node Manager/Process Manager)

	
  27. Go to Domain Structure – Environment – Clusters

	
  28. Click on Lock & Edit in top left pane

	
  29. Enable “Secured replication Enabled” for the cluster
[![Image](http://obibb.files.wordpress.com/2014/04/screen-shot-2014-04-04-at-15-39-45.png?w=547)](http://obibb.files.wordpress.com/2014/04/screen-shot-2014-04-04-at-15-39-45.png)

	
  30. Click on Save at top or bottom

	
  31. Click on Activate Changes in top left pane

	
  32. Repeat step 17 to lock

	
  33. Click on attributes tab of the step 8
(at BIDOMAIN.BIINSTANCE.SECURITYCONFIGURATION)
Click on ‘SSLEnabled’ .
Change the value to True
Click on Apply

	
  34. perform step 22 for simpleCommit.

	
  35. Restart all the services of Weblogic (Admin/Managed/opmnctl/Node Manager/Process Manager)

	
  36. Return to Step 8 and click on “runSSLReport” ,
Invoke it and find the output as below to ensure correct SSL communication across all BI components:
[![Image](http://obibb.files.wordpress.com/2014/04/runsslreport.png?w=650)](http://obibb.files.wordpress.com/2014/04/runsslreport.png)


Thanks [Menno Harzing](http://harzing.net/) and [Rob Chou](http://www.linkedin.com/pub/roberto-chou/4/487/851) for this blogpost.
