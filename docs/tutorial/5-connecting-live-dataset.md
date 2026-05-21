---
title: Connecting to a live dataset that has multiple sheets
parent: Tableau Tutorial
layout: default
created_date: 2020-04-07
staff:
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 5
grand_parent: Creating a Tableau Dashboard using COVID-19 data (Intermediate)
---
### Connecting to a live dataset that has multiple sheets
{: #connecting-to-a-live-dataset-that-has-multiple-sheets}

1. First start up Tableau Desktop and connect it to a Google Sheet of the COVID\-19 data. In Tableau’s Connect screen, under **To a Server**, select **Google Sheets**.  
![Tableau's connect menu. The option 'Google Sheets' is highlighted.]({{ '/assets/images/tableau_intermediate_001_0.png' | relative_url }})

    Follow the prompts to allow Tableau to access your Google account. Go back to Tableau. From a list of sheets, you should see COVID-19 Cases, **highlight it**, and then click on **Connect**. If you don’t see that sheet, then, in the URL bar, paste this link: [https://docs.google.com/spreadsheets/d/14quQPFErG-hlpsrNgYcX85vW7JMMK5X2vNZrafRcH8c/edit#gid=1154316396](https://docs.google.com/spreadsheets/d/14quQPFErG-hlpsrNgYcX85vW7JMMK5X2vNZrafRcH8c/edit#gid=1154316396) and click on Search. Then highlight the sheet COVID-19 cases, and click on Connect.  
        ![Window for selecting the Google sheet to connect to]({{ '/assets/images/tableau_intermediate_002.png' | relative_url }})

    Since this is a popular dataset, it might take some time to first connect to it, and then to load the data.

2. Drag **New Union**, listed on the left, to the orange box in the centre of the screen that says “Drag sheets here”.  
    ![Tableau's database join page. 'New Union' is highlighted.]({{ '/assets/images/tableau_intermediate_003.png' | relative_url }})

3. Next drag in the sheets called **COVID-19 Confirmed** and **COVID-19 Deaths** into the Union box, and click on OK. This will create a dataset combining all the rows in both of these sheets (they share the same columns).  
    ![Union popup confirming the sheets to be joined.]({{ '/assets/images/tableau_intermediate_004.png' | relative_url }})

4. Click on Sheet 1 (in orange at the bottom) to create a new worksheet.

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)