---
author: makumbe
comments: true
date: 2011-12-07 11:02:29+00:00
layout: post
link: http://blog.daanalytics.nl/2011/12/07/solving-the-informatica-tm_6795-error/
slug: solving-the-informatica-tm_6795-error
title: Solving the Informatica TM_6795 ERROR
wordpress_id: 1030
categories:
- Oracle BI Applications
tags:
- DAC
- Informatica
---

When running an Execution Plan in the DAC, I ran into an error. Investigating this error led to the Informatica Workflow Monitor. The logfile returned the following error;

_"TM_6795 ERROR: Session or its instance is invalidated and the Integration Service is configured not to run impacted sessions."_

The Informatica Message Reference leads to the following;

***

_**TM_6795** The Repository Service marked the session as impacted, and the Integration Service is not configured to run impacted sessions._
_**User Response:** Validate the session or configure the Integration Service to run impacted sessions._

***

If this is the case check whether all the related Informatica Mappings, Mapplets and Workflows, etc. are  validated and checked in. The latter did it for me. Not all objects where properly checked in.
