---
author: makumbe
comments: true
date: 2014-03-10 12:53:32+00:00
layout: post
link: http://blog.daanalytics.nl/2014/03/10/oracle-bia-making-the-full-incremental-load-work/
slug: oracle-bia-making-the-full-incremental-load-work
title: Oracle BIA - Making the Full / Incremental Load work
wordpress_id: 1495
categories:
- Oracle BI Applications
tags:
- DAC
- ETL
- Full Load
- Incremental Load
- Informatica
---

It's possible to configure either a Full- or an Incremental Load in Oracle BIA. If you look at the Informatica version of Oracle BIA, there are a few areas you will have to configure.

First you start with the Informatica Mapping. This will be one Mapping. It does not matter whether you run this Mapping Full or Incremental.

Lets take the 'SDE_ORA_GLJournals'-Mapping as an example. In the Source Qualifier of the Mapping (or Mapplet), you will see a reference to to the $$LAST_EXTRACT_DATE. If you would run the Mapping with these settings, you will run an Incremental Mapping. This means that you only select the data which is created / updated since the last ETL-run.

[![Informatica - Source Qualifier - $$LAST_EXTRACT_DATE](http://obibb.files.wordpress.com/2014/03/informatica-source-qualifier-last_extract_date.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-source-qualifier-last_extract_date.png)

The $$LAST_EXTRACT_DATE is a Parameter which you configure in the Datawarehouse Administration Console (DAC) and reference in Informatica.

[![DAC - Configure $$LAST_EXTRACT_DATE](http://obibb.files.wordpress.com/2014/03/dac-configure-last_extract_date.png?w=300)](http://obibb.files.wordpress.com/2014/03/dac-configure-last_extract_date.png)

According to the Oracle documentation, the "@DAC_SOURCE_PRUNED_REFRESH_TIMESTAMP. Returns the minimum of the task's primary or auxiliary source tables last refresh timestamp, minus the prune minutes."

Make sure this Parameter is available in both the DAC (see above) as well as in the Mapping (or Mapplet).

[![Informatica - Variables and Parameters - $$LAST_EXTRACT_DATE](http://obibb.files.wordpress.com/2014/03/informatica-variables-and-parameters-last_extract_date.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-variables-and-parameters-last_extract_date.png)

This way the Parameter can be used in the Extraction Mapping. If you reference a Parameter in the Extraction Mapping Query which isn't declared, the Workflow will return an error and won't complete.

So the steps are easy;

1. Declare the $$LAST_EXTRACT_DATE-Parameter in the DAC
2. Declare the $$LAST_EXTRACT_DATE-Parameter in Informatica
3. Reference the $$LAST_EXTRACT_DATE-Parameter in the Source Qualifier

As I said before, the same Mapping is used for the the Incremental- as well as the Full-Load. If you want to run the two different loads, make sure there ar two different Workflows which run the same mapping. The difference is in the mapping of the Workflow. The Full-Workflow uses the $$INITIAL_EXTRACT_DATE whereas the Incremental-Workflow uses the $$LAST_EXTRACT_DATE.

[![Informatica - Workflow - SDE_ORA_GLJournals](http://obibb.files.wordpress.com/2014/03/informatica-workflow-sde_ora_gljournals.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-workflow-sde_ora_gljournals.png)

If you edit the task which belongs to the Incremental-Workflow ('SDE_ORA_GLJournals'), you will find the Source Qualifier with the extraction query and a reference to the $$LAST_EXTRACT_DATE-Parameter.

As you can see, the LAST_UPDATE_DATE is compared to the $$LAST_EXTRACT_DATE-Parameter.

After each ETL-run, the LAST_EXTRACT_DATES (Refresh Date) per table are stored. You can check, update or delete these values as per requirement (see picture below). If you decide to delete the Refresh Date, a Full Load ill be performed the next time.

[![DAC - Refresh Dates](http://obibb.files.wordpress.com/2014/03/dac-refresh-dates.png?w=300)](http://obibb.files.wordpress.com/2014/03/dac-refresh-dates.png)

As stated earlier, the Full-Workflow is almost identical. The only thing is that there is a reference to the $$INITIAL_EXTRACT_DATE. The $$INITIAL_EXTRACT_DATE-Parameter is defined in the DAC. You define a date in the past. Just make sure that this date captures all the data you need.

[![DAC - Configure $$INITIAL_EXTRACT_DATE](http://obibb.files.wordpress.com/2014/03/dac-configure-initial_extract_date.png?w=300)](http://obibb.files.wordpress.com/2014/03/dac-configure-initial_extract_date.png)

Make sure this Parameter is available in both the DAC (see above) as well as in the Mapping (or Mapplet).

[![Informatica - Variables and Parameters - $$INITIAL_EXTRACT_DATE](http://obibb.files.wordpress.com/2014/03/informatica-variables-and-parameters-initial_extract_date.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-variables-and-parameters-initial_extract_date.png)

This way the Parameter can be used in the Extraction Mapping. If you reference a parameter in the Extraction Mapping Query which isn't declared, the Workflow will return an error and won't complete.

How do you make sure that the $$INITIAL_EXTRACT_DATE-Parameter will be used when running a Full-Load?

[![Informatica - Workflow - SDE_ORA_GLJournals_Full](http://obibb.files.wordpress.com/2014/03/informatica-workflow-sde_ora_gljournals_full.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-workflow-sde_ora_gljournals_full.png)

If you edit the task which belongs to the Incremental-Workflow ('SDE_ORA_GLJournals_Full'), you will find the Source Qualifier with the extraction query and a reference to the $$INITIAL_EXTRACT_DATE-Parameter.

As you can see, the LAST_UPDATE_DATE is compared to the $$INITIAL_EXTRACT_DATE-Parameter.

At this point everything is in place to either run a Full-, or an Incremental Load.

[![Informatica - Workflows](http://obibb.files.wordpress.com/2014/03/informatica-workflows.png?w=300)](http://obibb.files.wordpress.com/2014/03/informatica-workflows.png)

You just have to tell the DAC to either run the 'SDE_ORA_GLJournals_Full'-Workflow or the 'SDE_ORA_GLJournals'-Workflow (incremental)

[![DAC - Task - SDE_ORA_GL_Journals](http://obibb.files.wordpress.com/2014/03/dac-task-sde_ora_gl_journals.png?w=300)](http://obibb.files.wordpress.com/2014/03/dac-task-sde_ora_gl_journals.png)

Check the Informatica Session Log when the ETL has a another result than expected. It could be that the Workflows are incorrectly defined. You will see in the Session Log which Parameter is used and what the value of that Parameter is.

Good Luck.
