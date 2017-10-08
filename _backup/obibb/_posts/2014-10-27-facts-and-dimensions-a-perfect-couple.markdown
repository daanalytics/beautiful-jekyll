---
author: makumbe
comments: true
date: 2014-10-27 10:30:17+00:00
layout: post
link: http://blog.daanalytics.nl/2014/10/27/facts-and-dimensions-a-perfect-couple/
slug: facts-and-dimensions-a-perfect-couple
title: Facts and Dimensions - a Perfect Couple
wordpress_id: 1821
categories:
- Oracle BI EE
tags:
- Dimensions
- Facts
- Oracle BI Answers
---

With Oracle BI EE (OBIEE) you are able to report against various different data models. There are several different interesting blogposts to prove that. Let me Google that for you; [Transactional Schemas](http://bit.ly/1semeIY), [Data Vault](http://bit.ly/1vUURK5). In the end the Business Model and Mapping Layer (Logical Layer) 'needs' a [Star Schema](http://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/star-schema-olap-cube/) to construct the model we can report upon.

To simplify things, the Star Schema is one Fact-Table with one or more Dimension-Tables. So when you start creating your reports in eg. Oracle BI Answers, it's just a matter of combining the Fact-Table with the Dimension-Table(s). Last week I was at a client who had a problem with one of the reports; Unexpected Results.

The issue was the following; 3 Dimension-Tables joined together. Dimension-Tables in a Star Schema do not have a direct relationship with each other. The 3 Dimension-Tables together only get a meaning when there is a Fact-Table included. Let me clarify that.

Let's say we have 3 Dimension-Tables (Date - 27/10/2014, Product - iPhone, Region - Europe). If we put these 3 Dimension-Tables in a report, what does that tell us? Nothing! We can guess. There are iPhones sold in Europe on 27/10/2014? That might be. How much? We don't know. There are iPhones stolen in Europe on 27/10/2014? That might be correct as well.

If we add a Fact-Table (Quantity Sold - 20,000) to the above, the whole query makes more sense. There are 20,000 iPhones sold in Europe on 27/10/2014.

When you construct a query in OBIEE with only Dimension-Tables OBIEE includes a Fact-Table in it's query. Unless you have defined an [Implicit Fact Column](http://docs.oracle.com/cd/E28280_01/bi.1111/e10540/presentationlayer.htm#BIEMG1413), you don't necessarily know for sure which Fact-Table/Column is included in the Dimension-Only Query.

Facts and Dimensions are a Perfect Couple, please include both of them in your query.
