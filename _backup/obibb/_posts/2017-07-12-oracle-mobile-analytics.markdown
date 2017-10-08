---
author: makumbe
comments: true
date: 2017-07-12 08:30:13+00:00
layout: post
link: http://blog.daanalytics.nl/2017/07/12/oracle-mobile-analytics/
slug: oracle-mobile-analytics
title: Oracle Mobile Analytics
wordpress_id: 2169
categories:
- Oracle Business Analytics
tags:
- Day By Day
- Oracle BI HD
- Oracle Mobile Analytics
- Synopsis
---

Imagine yourself without a mobile device. There was a time we used our mobile phone to make calls only. Ok, we did some text sending via sms. But that was it. Nowadays (if I look at myself) I do not use my phone to make phone calls. Yes, when I am in the car the phone comes in handy to speak to others and to kill time. The main reason I use my phone is to lookup information or to interact with other people. This is not by speech but by sending messages.

In lot's of situations the smartphone or the tablet have taken over the role of the desktop computer. The same goes for Analytical Applications. People use their mobile devices to run analytics where the used to do that via their pc connected to the local network.

Also Oracle has a [strategy](https://www.oracle.com/solutions/business-analytics/business-intelligence/mobile/index.html) for mobile analytics. Oracle currently offers three different mobile apps for analytics:

![](https://obibb.files.wordpress.com/2017/07/oracle-mobile-analytics.png?w=300)



 	
  * Oracle BI HD

 	
  * Synopsis

 	
  * Day By Day




Although it looks a little bit confusing, there just is a separate app for a different purpose.

[Oracle BI HD](https://www.oracle.com/solutions/business-analytics/business-intelligence/mobile/bi-mobile/index.html) is Oracle's first mobile application for analytics. It's basically another platform to run your desktop reports. Oracle BI HD can be licensed on top of on-premise OBIEE and is integrated with the Cloud license.

![](https://obibb.files.wordpress.com/2017/07/oraclebihdserversettings.png)If you download the application from the app-store ([Apple](https://itunes.apple.com/us/app/oracle-business-intelligence-mobile-hd/id534035015?mt=8) in my case) you can just connect to any Oracle BI Server you have available. I chose to connect to our Quistor BI Cloud environment. Of course you can add any other Oracle BI Server URL you want to connect to.









You have to enter a host. In the case of the Quistor BI Cloud environment you will enter the Service Instance URL which you can find in the BICS Service Details.![](https://obibb.files.wordpress.com/2017/07/bics-service-instance-url1.png)

![](https://obibb.files.wordpress.com/2017/07/oraclebihdlogin2.png)

After the server is added and you connect to it, you have to enter the login details. This is similar to logging into the BICS environment.









Now you enter into the Analytics Environment where you have access to the same dashboards as you have available in the Cloud. Check here the General Ledger Dashboard of our Quistor BINGO environment.

![](https://obibb.files.wordpress.com/2017/07/bicsgldashboard.png) ![](https://obibb.files.wordpress.com/2017/07/oraclebihdgldashboard.png?w=169)The same dashboard on the left as it shows on my smartphone. Of course you do not have the same experience as on the desktop or even the tablet. But it is nice that you can bring your dashboards with you and analyse data while being on the road.







[Synopsis](https://www.oracle.com/solutions/business-analytics/synopsis.html) allows a user to analyse files (received on) a mobile device without the need to access a Oracle BI Server.

![](https://obibb.files.wordpress.com/2017/07/sunopsisexcelsheet.png?w=169)

Imagine you have an Excel spreadsheet available in a Box Cloud environment. In this case it is the Pipeline.xlsx.

![](https://obibb.files.wordpress.com/2017/07/synopsisimport.png?w=169)

After you download the application from the app-store ([Apple](https://itunes.apple.com/us/app/oracle-synopsis/id1191620183?mt=8) in my case) you can import this spreadsheet directly into the Oracle Synopsis mobile application.

![](https://obibb.files.wordpress.com/2017/07/synopsisimportingdata.png?w=169)



![](https://obibb.files.wordpress.com/2017/07/synopsisprojects.png?w=169)



After the data is imported into the application, you have a project with the imported spreadsheet.





You can immediately analyse the Pipeline data. The application already prepared some analysis for you based on the data it finds.

![](https://obibb.files.wordpress.com/2017/07/synopsisanalysis.png?w=169) ![](https://obibb.files.wordpress.com/2017/07/synopsisgraph.png?w=169)

Check out [Youtube](https://youtu.be/7c9LH6yEGGI) to see Oracle Synopsis in Action.









[Day By Day](https://www.oracle.com/solutions/business-analytics/day-by-day.html) is Oracle's latest addition to the Oracle Mobile Application offering. This application is different from the Oracle BI HD application. You will use search technology, either by voice or by typing, to create your analysis.

You can download the application from the app-store ([Apple](https://itunes.apple.com/us/app/oracle-day-by-day/id1236214430?mt=8) in my case).

![](https://obibb.files.wordpress.com/2017/07/daybydayselectserver.png?w=169)

Starting up the application allows you to enter. One of the prerequisites of this application is an [Oracle Analytics Cloud](https://www.oracle.com/solutions/business-analytics/analytics-cloud.html) (OAC) environment with BI Author and DV Consumer roles. At this moment I do not have an OAC environment at my disposal. There is a demo included in the app. Select 'Try a Demo' and after you are welcomed to the application you can start analysing data.![](https://obibb.files.wordpress.com/2017/07/daybydaywelcome.png?w=169)





Via a typed or spoken search string (in this case; 'revenue per customer segment' you can create an analysis.



![](https://obibb.files.wordpress.com/2017/07/daybydaysearch.png?w=169)

![](https://obibb.files.wordpress.com/2017/07/daybydayfetchingdata.png?w=169)













![](https://obibb.files.wordpress.com/2017/07/daybydaygraph.png?w=169)

This search leads to the graph on the right. Of course this is only an easy example. For more details and examples, please have a look [here](https://youtu.be/8q4foZyYQJc).









Interesting applications to check out. They might not all be evenly useful, but it's good to have a choice of functionality to satisfy your mobile analytical needs. What I don't get is that all the applications start with a blue screen. Not the [bsod](https://en.wikipedia.org/wiki/Blue_Screen_of_Death), but why Oracle did not choose an Oracle Red startup screen is a mystery for me.

This post is written as part of my [Exploring Oracle Business Analytics](http://blog.daanalytics.nl/2017/07/10/exploring-oracle-business-analytics/) series.

Thanks for reading.
