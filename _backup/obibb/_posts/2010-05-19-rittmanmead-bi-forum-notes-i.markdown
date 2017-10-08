---
author: makumbe
comments: true
date: 2010-05-19 16:30:11+00:00
layout: post
link: http://blog.daanalytics.nl/2010/05/19/rittmanmead-bi-forum-notes-i/
slug: rittmanmead-bi-forum-notes-i
title: RittmanMead BI Forum 2010 - Notes I
wordpress_id: 15
categories:
- RittmanMead BI Forum
---

Today we had a kick-off of the [RittmanMead BI Forum](http://www.rittmanmead.com/biforum2010/) with a Masterclass of [Kurt Wolff](http://kpipartners.blogspot.com). Kurt is one of the founders of Oracle BI EE as we know the product today. He was there when the product was developed by NQuire in the late nineties.

It was nice to get a whole new perspective on Oracle BI EE. Because he was there from the beginning Kurt is able to clearify some design issues.

Kurt does not preach a best practice, but a possible practice (Kurt's practice). Some of his statements lead to new insights and several discussions. Maybe some open doors, but absolutely valuable.

Check back to the [RittmanMead BI Forum](http://www.rittmanmead.com/biforum2010/) to find the handouts.

A few short notes:

MUD (Multi User Development) --> Kurt has his own ideas of working with repositories. If you start from scratch, you will do it in offline mode. From the moment the RPD is promoted to production, you can manage it in online mode. 

Make sure you have a local copy so you can always go back. Working in online mode shouldn't be  a problem if the number of developers is limited. Working in timeshifts and in different area’s of the RPD makes this approach even more worth a try.

LTS - Logical Table Sources --> There is a lot to say and to learn about LTS. Kurt goes for one logical fact table with multiple LTS's (one for each source physical table). Exception for the compound fact column with multiple physical source tables.

I was in the assumption that the BI Server randomly chose a possible LTS. It turns out that picks the LTS based on the smallest Logical Level defined in the Dimension Hierarchy. Each LTS is candidate.

Server Complex Aggregate --> Sometimes, when you defined a calculation in your answer, totals are wrongly calculated. You can put the aggregation rule to; Server Complex Aggregate. It tells the BI Server to go back to the RPD and do calculation by itself as is the column defined in the Logical Layer.

Some nice to know notes:

When you fire a query, it shows 'Searching'. 'Querying' makes more sense. Oracle BI EE was originally meant as some kind of search-engine for structured data.

Answers comes from a 'Ask Jeeves' like functionality. Pick up the phone, ask de desired output and the computer provides the output without human interference.

Kurt provided a lot of other handy stuff, which I have to work out for myself. All in all a very nice way to start this forum.

Check [Alex'](http://siebel-essentials.blogspot.com/2010/05/bi-forum-brighton-2010-day-1.html) blog for his notes about this Masterclass.

Looking forward to the rest.

Keep you posted.
