---
author: makumbe
comments: true
date: 2010-10-12 12:35:30+00:00
layout: post
link: http://blog.daanalytics.nl/2010/10/12/deploy-custom-content-folder-location-in-wls/
slug: deploy-custom-content-folder-location-in-wls
title: Deploy Custom content folder location in WLS
wordpress_id: 422
categories:
- Setup
tags:
- 10g
- 11g
- Custom
- Folder
- obi11g
- Weblogic
---

[](http://obibb.files.wordpress.com/2010/09/no-custom-content-sv-dashboard.png)[](http://obibb.files.wordpress.com/2010/09/deployment.png)[](http://obibb.files.wordpress.com/2010/09/deployment-install.png)[](http://obibb.files.wordpress.com/2010/09/install-analyticsres.png)[](http://obibb.files.wordpress.com/2010/09/install-this-deployment-as-an-application.png)[](http://obibb.files.wordpress.com/2010/09/select-deployment-targets.png)[](http://obibb.files.wordpress.com/2010/09/operational-settings-source-accessibility.png)[](http://obibb.files.wordpress.com/2010/09/activate-changes.png)[](http://obibb.files.wordpress.com/2010/09/start-deployment.png)[](http://obibb.files.wordpress.com/2010/10/11g-custom-content-sv-dashboard.png)In an earlier [post](http://obibb.wordpress.com/2010/10/07/upgrading-from…ory-and-webcat/) I ended up with problems with custom folders in Oracle BI 11g R1. It turned out that I had to make some additional steps to deploy a custom folder in the Weblogic Server. Thanks to the documentation of the [SampleApp](http://www.oracle.com/technetwork/middleware/bi-foundation/obiee-samples-167534.html) I was able to make this work.

I have been working on a demo. Therefore I have created an index site with links to custom images and custom documentation. When I migrated this demo from 10g to 11g, I had to copy the images and documents manually. This seemed not to be enough. I ended up with some red crosses.

[![](http://obibb.files.wordpress.com/2010/09/no-custom-content-sv-dashboard.png?w=300)](http://obibb.files.wordpress.com/2010/09/no-custom-content-sv-dashboard.png)

You have to take the following steps to deploy custom folders to the Weblogic Server.

Login to the Weblogic Server
Navigate to te Deployments
Click on 'Lock & Edit' in the left pane to enable the 'Install'-button

 [![](http://obibb.files.wordpress.com/2010/09/deployment.png?w=187)](http://obibb.files.wordpress.com/2010/09/deployment.png)

click 'Install'

[![](http://obibb.files.wordpress.com/2010/09/deployment-install.png)](http://obibb.files.wordpress.com/2010/09/deployment-install.png)

Navigate to '<MIDDLEWARE_HOME>\instances\instance1\bifoundation\OracleBIPresentationServicesComponent\coreapplication_obips1'

select 'analyticsRes'
click 'Next'

[![](http://obibb.files.wordpress.com/2010/09/install-analyticsres.png?w=300)](http://obibb.files.wordpress.com/2010/09/install-analyticsres.png)

select 'Install this deployment as an application' (default)
click 'Next'

[![](http://obibb.files.wordpress.com/2010/09/install-this-deployment-as-an-application.png?w=300)](http://obibb.files.wordpress.com/2010/09/install-this-deployment-as-an-application.png)
Select 'Deployment targets'
Choose 'bi_server1'
click 'Next'

[![](http://obibb.files.wordpress.com/2010/09/select-deployment-targets.png?w=300)](http://obibb.files.wordpress.com/2010/09/select-deployment-targets.png)

Under 'Source accessibility'

Choose 'I will make the deployment accessible from the following location'
'<MIDDLEWARE_HOME>\instances\instance1\bifoundation\OracleBIPresentationServicesComponent\coreapplication_obips1\analyticsRes'
click 'Finish'

[![](http://obibb.files.wordpress.com/2010/09/operational-settings-source-accessibility.png?w=300)](http://obibb.files.wordpress.com/2010/09/operational-settings-source-accessibility.png)

Check the 'Deployments' to see whether the 'analyticsRes' is available.

click on 'Activate Changes'

[![](http://obibb.files.wordpress.com/2010/09/activate-changes.png)](http://obibb.files.wordpress.com/2010/09/activate-changes.png)

start the deployment; 'analyticsRes'

[![](http://obibb.files.wordpress.com/2010/09/start-deployment.png?w=300)](http://obibb.files.wordpress.com/2010/09/start-deployment.png)

Now I am able to add the required images and documents in custom folders just by referencing to the  'analyticsRes'- folder, eg.; '/analyticsRes/Documents/'

[![](http://obibb.files.wordpress.com/2010/10/11g-custom-content-sv-dashboard.png?w=300)](http://obibb.files.wordpress.com/2010/10/11g-custom-content-sv-dashboard.png)
