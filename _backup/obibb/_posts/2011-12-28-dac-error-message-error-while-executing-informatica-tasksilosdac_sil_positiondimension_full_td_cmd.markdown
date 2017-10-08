---
author: makumbe
comments: true
date: 2011-12-28 11:49:14+00:00
layout: post
link: http://blog.daanalytics.nl/2011/12/28/dac-error-message-error-while-executing-informatica-tasksilosdac_sil_positiondimension_full_td_cmd/
slug: dac-error-message-error-while-executing-informatica-tasksilosdac_sil_positiondimension_full_td_cmd
title: 'DAC Error Message - Error while executing : INFORMATICA TASK:SILOS:@DAC_SIL_PositionDimension_FULL_TD_CMD'
wordpress_id: 1059
categories:
- Oracle BI Applications
tags:
- 10g
- DAC
---

Thanks to [Frank Davis](http://obieeone.com/2011/05/12/dac-error-message-the-specified-task-name-workflow-name-or-folder-name-does-not-exist-dac_xxx/), I was able to solve the following error; 'Error while executing : INFORMATICA TASK:SILOS:@DAC_SIL_PositionDimension_FULL_TD_CMD'

A patch (Patch 12968641: DAC 10.1.3.4.1 CUMULATIVE PATCH FOR BI APPS - SEP 2011) for this error can be downloaded [here](https://support.oracle.com/CSP/ui/flash.html#tab=PatchHomePage(page=PatchHomePage&id=gwq5r3o7()),(page=PatchSearchResultsHome&id=gwq5rch3(incFamilyProds=false&search=%3CSearch%3E%0A%20%20%3CFilter%20name=%22patch_number%22%20op=%22IS%22%20value=%2210052370%22%20type=%22patch_number%22/%3E%0A%20%20%3CFilter%20name=%22platform%22%20op=%22IS%22%20value=%22233,46,912,226%22%20type=%22platform%22/%3E%0A%3C/Search%3E&flag=search)),(page=PatchDetailPage&id=gwq5s8om(platformId=2000&releaseId=922101341&description=DAC%2010.1.3.4.1%20CUMULATIVE%20PATCH%20FOR%20BI%20APPS%20-%20SEP%202011&patchName=12968641&patchId=12968641&))).
