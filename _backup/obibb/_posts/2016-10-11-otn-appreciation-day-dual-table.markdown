---
author: makumbe
comments: true
date: 2016-10-11 08:00:54+00:00
layout: post
link: http://blog.daanalytics.nl/2016/10/11/otn-appreciation-day-dual-table/
slug: otn-appreciation-day-dual-table
title: 'OTN Appreciation Day : Dual Table'
wordpress_id: 1976
categories:
- OBIBB - General
tags:
- '#ThanksOTN'
---

[![otn-appreciation-day](https://obibb.files.wordpress.com/2016/10/otn-appreciation-day.jpg?w=300)](https://twitter.com/search?f=tweets&vertical=default&q=%23ThanksOTN&src=tyah)I have been working with Oracle products for about 20 years now. One of the great things about Oracle is the Oracle Community. Central platform within this community is the Oracle Technology Network (OTN). I have been frequenting OTN loads of times (downloading software, exchanging knowledge on the forums, etc. ). A lot of people I know in the Oracle Community, I have met via OTN.

Today I read the OTN Appreciation Day announcement on Tim Hall's [blog](https://oracle-base.com/blog/2016/09/28/otn-appreciation-day/).

"considering OTN is all about community, I figured it would be fun if we got as many people as possible to write a small blog post about their favourite Oracle feature and we all post them on the same day"

I immediately thought about the Dual Table in the Oracle database.

**Dual Table**

What I like about the [Dual Table](http://www.orafaq.com/wiki/Dual), is that something which looks so simple can be so powerful. You can select the date, the length of a string, the result of calculation and so on. One simple table, with just one varchar dummy column is able to tell you almost everything you want.

I can illustrate how powerful the Dual Table is by a short anekdote. The story could be a little bit different but it's all about the scope. One of my former colleagues (I won't tell his name) wanted to test part of his code. Therefore he decided to insert a record in the Dual Table. I think it was in the Oracle database version 7 / 8 timeframe. It might have been a smart move in his mind, but it was disastrous for the application running. Very slowly the application collapsed. The application code expected one row when selecting from the Dual Table. It took some time to realise that the Dual Table contained an extra record. As far as I know the functionality of the Dual Table has changed since then, but I guess there is no need at all to mess with the Dual Table.

Curious what other people have to share on OTN Appreciation Day, check [here](https://twitter.com/search?f=tweets&vertical=default&q=%23ThanksOTN&src=tyah).

Cheers,

Daan
