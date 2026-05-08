---
title: The Dashboard
parent: Creating a Tableau Dashboard using COVID-19 data (Intermediate)
layout: default
created_date: 2020-04-07
staff:
    - name: Nick Field
      link: https://library.utoronto.ca/staff/nick-field
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 2
---

# The Dashboard

This tutorial will be focused on learning how to recreate aspects of [this old dashboard](https://www.tableau.com/about/blog/2020/3/covid-19-data-resources-to-understand-virus-impact) (seen as a screenshot) and [this new dashboard](https://public.tableau.com/profile/covid.19.data.resource.hub#!/vizhome/COVID-19Cases_15840488375320/COVID-19GlobalView) using Tableau Desktop. *Note: This dashboard used to have information on recoveries as well, which is best practice for COVID-19 visualizations, but unfortunately the dataset it was based on removed recovery information, as they concluded the data was too unreliable. Also, this dashboard (and so the tutorial) was designed using straight case counts, but for comparison purposes, it would make more sense to compare based on cases per # of people (e.g., cases per 100,000 people).*

When working to emulate a Tableau dashboard found on the Tableau Public website, you can often click on the download icon (hover over the icons at the bottom right of the dashboard to find it) and download the underlying workbook (if the owner gave permission).  
![Tableau Public workbook with download button highlighted]({{ '/assets/images/tableau_intermediate_000b.png' | relative_url }})

![Download menu with Tableau Workbook option highlighted]({{ '/assets/images/tableau_intermediate_000c.png' | relative_url }})

This is a great way to learn how to create dashboards in Tableau. However, in some situations, a workbook can be so complicated that it might take a while to unpick and understand what is going on. That is the situation here, and why this tutorial was created.

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)