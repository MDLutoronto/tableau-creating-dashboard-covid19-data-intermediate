---
title: "Creating a Tableau Dashboard using COVID-19 data (Intermediate)"
layout: "home"
description: ""
permalink: "/"  #! Remove this if not the homepage
---

# Creating a Tableau Dashboard using COVID-19 data (Intermediate)

This tutorial provides an opportunity to learn data visualization skills using a common data visualization tool, Tableau Desktop. People often say that they learn better when using data that resonates with them, so we are using COVID\-19 data in this tutorial, as this topic is touching many people’s lives right now.

 

Table of Contents
=================

[Introduction](#Intro)  
[The Dashboard](#Dashboard)  
[Starting a Visualization Project](#StartingVisualizationProject)  
[Tableau Tutorial](#TableauTutorial)

* [Connecting to a live dataset that has multiple sheets](#ConnectingLiveDataset)
* [Create side\-by\-side bar graphs with filters for cases by day](#SideBarGraphs)
* [Create a parameter so that the graphs change based on whether the user wants to see total cases or new cases](#Parameter)
* [Create a dynamic mark label](#DynamicMarkLabel)
* [Create a dynamic bar graph embedded in a tooltip](#Tooltip)
* [Create side\-by\-side proportional symbol maps of cases with dynamic tooltips](#Map)
* [Create side\-by\-side bar graphs for cases by country](#CasesbyCountry)
* [Create a dashboard to pull these three visualizations together](#FinalDashboard)

 

Introduction
============

 

DISCLAIMER: This is a very complex topic and situation right now. If you are new to data visualization, this tutorial will help you build your skills, but that does not mean you should then be sharing all the COVID\-19 visualizations you create. Leave that to experts, many of whom have already done[this](https://mdl.library.utoronto.ca/covid-19/data-visualizations). COVID\-19 data is not a “cool new dataset” to play with and data visualizations in this context MUST NOT be misleading, inaccurate, or incite panic. Each data point represents a person. Responsible and sensitive visualizations are essential. Epidemiology is also a complex area; fully understanding the data, statistics and visualizations is critical to producing and sharing useful and effective visualizations on this topic. So we recommend that for beginners you create visualizations, such as the one created in this tutorial, for just yourself, for your own learning.

Before embarking on this tutorial, do the following:

1. Get more familiar with the topic and data, and the concerns and precautions around visualizing it:

    1. [10 considerations before you create another chart about COVID\-19](https://www.tableau.com/about/blog/2020/3/ten-considerations-you-create-another-chart-about-covid-19)(Tableau)
        2. [A complete guide to coronavirus charts: Be informed, not terrified](https://www.fastcompany.com/90477393/a-complete-guide-to-coronavirus-charts-be-informed-not-terrified)(Amanda Makulec, Excella, FastCompany)
        3. [17 (or so) responsible live visualizations about the coronavirus, for you to use](https://blog.datawrapper.de/coronaviruscharts/)(Datawrapper)
        4. [What the BBC got wrong in their COVID\-19 visualization](https://www.tableau.com/about/blog/2020/3/covid-19-resources-data-viz-best-practices)(Tableau)
2. [Install Tableau Desktop](https://mdl.library.utoronto.ca/technology/tutorials/installing-tableau-desktop)(This tutorial was created using Tableau Desktop version 2020\.2\)

3. Get more familiar with the tool we’re going to be using by trying some of our other Tableau tutorials first:

    1. [Creating Data Visualizations Using Tableau Desktop](https://mdl.library.utoronto.ca/technology/tutorials/creating-data-vizualizations-using-tableau-desktop)(Beginner)
        2. [Getting Started with Tableau Desktop](https://mdl.library.utoronto.ca/technology/tutorials/getting-started-tableau-desktop-beginner-intermediate)(Beginner to Intermediate)

 

The Dashboard
=============

This tutorial will be focused on learning how to recreate aspects of [this old dashboard](https://www.tableau.com/about/blog/2020/3/covid-19-data-resources-to-understand-virus-impact)(seen as a screenshot) and[this new dashboard](https://public.tableau.com/profile/covid.19.data.resource.hub#!/vizhome/COVID-19Cases_15840488375320/COVID-19GlobalView)using Tableau Desktop.*Note: This dashboard used to have information on recoveries as well, which is best practice for COVID\-19 visualizations, but unfortunately the dataset it was based on removed recovery information, as they concluded the data was too unreliable. Also, this dashboard (and so the tutorial) was designed using straight case counts, but for comparison purposes, it would make more sense to compare based on cases per \# of people (e.g., cases per 100,000 people).*

When working to emulate a Tableau dashboard found on the Tableau Public website, you can often click on the download icon (hover over the icons at the bottom right of the dashboard to find it) and download the underlying workbook (if the owner gave permission).  
![Tableau Public workbook with download button highlighted]({{ '/assets/images/tableau_intermediate_000b.png' | relative_url }})

![Download menu with Tableau Workbook option highlighted]({{ '/assets/images/tableau_intermediate_000c.png' | relative_url }})

This is a great way to learn how to create dashboards in Tableau. However, in some situations, a workbook can be so complicated that it might take a while to unpick and understand what is going on. That is the situation here, and why this tutorial was created.

 

Starting a Visualization Project
================================

Before embarking on any visualization project, you should always consider your audience and purpose for your visualization ([Stage 1](https://mdl.library.utoronto.ca/dataviz/workflow#audience)) (see our Data Visualization Guide[Design Workflow section](https://mdl.library.utoronto.ca/dataviz/workflow)for more details). For the purposes of this tutorial, the audience is for your eyes only and the purpose is to learn how to visualize data in Tableau Desktop.

Next, you need to select your data and gain an understanding of it ([Stage 2](https://mdl.library.utoronto.ca/dataviz/workflow#data)). For this tutorial, we started by using a[Google Sheet document](https://docs.google.com/spreadsheets/d/14quQPFErG-hlpsrNgYcX85vW7JMMK5X2vNZrafRcH8c/htmlview#gid=1939846621)that was being continuously cleaned and updated by Tableau daily ([see this page for details](https://www.tableau.com/about/blog/2020/3/covid-19-data-resources-to-understand-virus-impact)). This was not necessarily the most authoritative or up\-to\-date data source to use for this topic; see our[resources pages](https://mdl.library.utoronto.ca/covid-19/resources)for other sources out there. It was selected as a good source to demonstrate linking to real time data in Tableau.

*Note: The dashboard and dataset are constantly changing. Unfortunately, these instructions no longer work with the current google sheet, so instead download [this snapshot of the data](http://maps.library.utoronto.ca/workshops/TableauTutorial/COVID19Cases.xlsx)(from April 7, 2020\) to use with the tutorial instead. In Tableau’s Connect screen, connect to an Excel file instead and browse to this snapshot file, then skip to step 2 to continue the tutorial. We leave the old instructions up for your reference on how you would connect to a google sheet datasource. More details about this dataset and how it has changed since this tutorial was created can be found[on this Tableau page](https://www.tableau.com/about/blog/2020/5/8-changes-to-covid-19-data-set).*

 

Tableau Tutorial
================

 

Connecting to a live dataset that has multiple sheets
-----------------------------------------------------

1. First start up Tableau Desktop and connect it to a Google Sheet of the COVID\-19 data. In Tableau’s Connect screen, under **To a Server**, select **Google Sheets**.  
![Tableau's connect menu. The option 'Google Sheets' is highlighted.]({{ '/assets/images/tableau_intermediate_001_0.png' | relative_url }})

    Follow the prompts to allow Tableau to access your Google account. Go back to Tableau. From a list of sheets, you should see COVID\-19 Cases, **highlight it**, and then click on **Connect**. If you don’t see that sheet, then, in the URL bar, paste this link:[https://docs.google.com/spreadsheets/d/14quQPFErG\-hlpsrNgYcX85vW7JMMK5X2vNZrafRcH8c/edit\#gid\=1154316396](https://docs.google.com/spreadsheets/d/14quQPFErG-hlpsrNgYcX85vW7JMMK5X2vNZrafRcH8c/edit#gid=1154316396)and click on Search. Then highlight the sheet COVID\-19 cases, and click on Connect.  
        ![Window for selecting the Google sheet to connect to]({{ '/assets/images/tableau_intermediate_002.png' | relative_url }})

    Since this is a popular dataset, it might take some time to first connect to it, and then to load the data.

2. Drag **New Union**, listed on the left, to the orange box in the centre of the screen that says “Drag sheets here”.  
![Tableau's database join page. 'New Union' is highlighted.]({{ '/assets/images/tableau_intermediate_003.png' | relative_url }})

3. Next drag in the sheets called **COVID\-19 Confirmed** and **COVID\-19 Deaths** into the Union box, and click on OK. This will create a dataset combining all the rows in both of these sheets (they share the same columns).  
![Union popup confirming the sheets to be joined.]({{ '/assets/images/tableau_intermediate_004.png' | relative_url }})

4. Click on Sheet 1 (in orange at the bottom) to create a new worksheet.

 

Create side\-by\-side bar graphs with filters for cases by day
--------------------------------------------------------------

5. First, we will create the side by side bar graphs of confirmed cases and deaths over time.**Right click** on the Sheet 1 tab at the bottom, select **Rename**, and give it the name “CasesbyDay”.  
![Renaming the new sheet to “CasesbyDay”]({{ '/assets/images/tableau_intermediate_005a.png' | relative_url }})

6. From the Dimensions section, drag **Date**next to **columns**. Note that it defaults to YEAR(Date). To format how the date is displayed, **right click** on YEAR(Date) and select **Day**, specifically the option that has the example "8th May, 2015".  
![Drop down menu for YEAR(Date) with the menu item 'Day' highlighted]({{ '/assets/images/Tableau_Covid19_001.jpg' | relative_url }})

7. **Right click** again on**DAY(Date)** and this time select **Discrete** \- as the data updates daily, it is not a continuous flow.  
![Drop down menu with the menu item "Discrete" highlighted]({{ '/assets/images/Tableau_Covid19_002.jpg' | relative_url }})

8. From the Measures section, drag **Cases**next to **rows**.  
![Column and row section is displayed with the respective pills.]({{ '/assets/images/tableau_intermediate_008.png' | relative_url }})

9. On the Marks card, from its drop down that says Automatic, change the selection to **Bar**.  
![The menu item 'Bar' highlighted in the Marks dropdown menu]({{ '/assets/images/Tableau_Covid19_003.jpg' | relative_url }})

10. From Dimensions, drag**Case\_Type**next to **columns**, to the **left** of DAY(Date). This creates two side\-by\-side bar graphs showing cases by day. By sharing the y\-axis, you can more accurately compare the data. To see them both without scrolling, drop down on Standard at the top and change the view to Entire View.  
![Two bar charts are displayed. Above them, the view option 'Entire View' and the pill 'Case_Type' highlighted]({{ '/assets/images/tableau_intermediate_010.png' | relative_url }})

11. Let’s use colours to differentiate the two categories. Drag**Case\_Type**to **Color**on the Marks card. Click on Color and then select "Edit Colors...".  
!["Edit Colours" button highlighted.]({{ '/assets/images/tableau_intermediate_011.png' | relative_url }})

    Leave Confirmed cases at the default blue, but select**Deaths**then the **purple** available in the default palette to change it. Then click on OK.  
        ![The "Edit colours" menu, with "Deaths" assigned colour changed to purple.]({{ '/assets/images/tableau_intermediate_012.png' | relative_url }})

12. Let’s clean up the axes so that when the graphs are displayed in the dashboard, they don’t take up so much room. Right click on the **x\-axis** listing the dates, and **uncheck Show Header**. Since one day will be highlighted, click in the white space of the graph to unselect that day.  
![X-axis menu with the menu item "Show Header" highlighted.]({{ '/assets/images/tableau_intermediate_013.png' | relative_url }})

13. **Right click** on the **Case Type header** in the graph, and select **Hide Field Label for Columns**.  
![Dropdown menu for the Case_Type column. The menu item option "Hide Field Labels for Columns" is highlighted.]({{ '/assets/images/tableau_intermediate_014a.png' | relative_url }})

14. We can also add some filters to these graphs, so that a user could filter to see a certain country or date range. From Dimensions, drag**Country\_Region**to the**Filters**shelf. Click on**All** and then OK.  
![“Country_Region” in the Dimensions section is highlighted, as well as the Filters Shelf. The resulting pop-up window is also shown. ]({{ '/assets/images/Tableau_Covid19_004.JPG' | relative_url }})

    Then**right click**on the**Country\_Region**pill on the Filters shelf and select**Show Filter**.  
        ![Dropdown menu for the "Country_Region" pill, with the menu item "Show Filter" highlighted.]({{ '/assets/images/tableau_intermediate_016.png' | relative_url }})

    You will see a list of countries on the right. If you hover over the title of the list, you should see a small arrow on the right that you can use to access a drop\-down menu.  
        ![Dropdown button on the "Country_Region" card highlighted. ]({{ '/assets/images/tableau_intermediate_017.png' | relative_url }})

    Click on it and select **Single Value (dropdown)**.  
        ![Dropdown menu for the “Country_Region” card, with the menu item “Single Value (dropdown)” selected.]({{ '/assets/images/tableau_intermediate_018.png' | relative_url }})

    This makes the filter take up a much smaller amount of space on the screen, and eventually the dashboard. Make the country filter include All countries for now.

15. From Dimensions, drag **Date** to the **Filters** shelf. Select **Relative Date** and click Next.  
!["Filter Field [Date]" pop up menu with the menu item "Relative Date" highlighted.]({{ '/assets/images/tableau_intermediate_019.png' | relative_url }})

    Go to the **Starting date** tab, check **Include Null Values**, and then click OK.  
        ![The "Filter [Date]" pop up window the items “Starting date” and "Include Null Values" highlighted. ]({{ '/assets/images/tableau_intermediate_020.png' | relative_url }})

    Then**right click**on the **Date** pill on the Filters shelf and select**Show Filter**. You will see a slider Date filter on the right.  
        ![“Date”, “Country_Region”, and “Case_Type” filter and legend cards displayed.]({{ '/assets/images/tableau_intermediate_021.png' | relative_url }})

 

Create a parameter so that the graphs change based on whether the user wants to see total cases or new cases
------------------------------------------------------------------------------------------------------------

16. **Right click** in the blank space under the Measures section, and select **Create Parameter…** 
![The Field menu displayed with the menu item “Create Parameter” highlighted.]({{ '/assets/images/Tableau_Covid19_005.jpg' | relative_url }})

    Name it **Select Metric**. Change data type to **Integer**. Under Allowable values, click **List**. In the **List of values** below, click on the first row under Value and type **0**. Next to it, in the same row under Display As, type **Total Cases**. On the next row, under Value type **1** and under Display As type **New Cases**. Click elsewhere in the list to stop editing New Cases. Then click OK.  
        ![The "Create Parameter" pop up window with details filled in as described.]({{ '/assets/images/tableau_intermediate_023.png' | relative_url }})

    You will see a new section appear under the Measures section, called **Parameter**, listing the new parameter we just created. This parameter will allow the user to specify if they want to review data for total cases or new cases.  
        ![Image of the Side Bar with the new Parameters section highlighted.]({{ '/assets/images/Tableau_Covid19_006.JPG' | relative_url }})
17. Currently, the parameter just collects input from the user, but doesn't act on it. To apply the choice to the graph, we need to create a field that acts on that choice and displays what data was requested. From the **Analysis** menu, select**Create Calculated Field...**,  
![Analysis drop down menu with the menu item "Create Calculated Field" highlighted.]({{ '/assets/images/tableau_intermediate_024.png' | relative_url }})

    and name it **Metric Switcher**. Paste in the following formula:  
        `IF [Select Metric]=0 THEN [Cases] ELSE [Difference] END`  
        ![Create Calculated Field pop up window with formula copied in]({{ '/assets/images/tableau_intermediate_025.png' | relative_url }})

    Then click on OK. You should see this new field in the Measures section.  
        *Note: Whenever a variable is mentioned (e.g. \[Cases]), you can either type the variable name exactly as it is shown or drag the variable’s pill into the calculation field.*
18. In the rows section,**right click**on**SUM(Cases)**, and select **Remove**.  
![Dropdown menu for the pill "SUM(Cases)". The menu item "Remove" is highlighted.]({{ '/assets/images/tableau_intermediate_026.png' | relative_url }})

    Then, from Measures, drag **Metric Switcher**next to **Rows**.  
        ![The pills in the Columns and Rows sections are displayed.]({{ '/assets/images/tableau_intermediate_027.png' | relative_url }})

19. From the Parameters section, **right click** on **Select Metric**, and select **Show Parameter**.  
![Menu that appears after clicking on Select Metric. The menu item "Show Parameter" is also highlighted.]({{ '/assets/images/Tableau_Covid19_007.jpg' | relative_url }})

    Now you can adjust whether Total Cases or New Cases are displayed in the bar graphs using this menu. It will sum either the field Cases or Difference depending on what was selected.

 

Create a dynamic mark label
---------------------------

20. Let’s add a dynamic mark label to highlight today’s data in the graph. From Measures, drag **Metric Switcher** to **Label** on the Marks card. From Dimensions, drag **Date** to **Label**too.  
![Label mark on the marks card is highlighted. ]({{ '/assets/images/tableau_intermediate_029.png' | relative_url }})

21. **Right click** on the**YEAR(Date)** pill listed on the Marks card, and select **Exact Date**.  
![The menu from the "YEAR(Date)" pill, with the menu item "Exact Date" highlighted]({{ '/assets/images/tableau_intermediate_030.png' | relative_url }})

22. Click on **Label**on the Marks card. Under the**Marks to Label**section, select**Most Recent**. Under the**Label Appearance**section, click on the gray button with ellipses next to Text.  
![Label card window with the ellipses button and the "Most Recent" button highlighted.]({{ '/assets/images/tableau_intermediate_031.png' | relative_url }})

    Center both lines (if not centered already) and bold them. Change \<SUM(Metric Switcher)\> to **size 12**, and \<Date\> to **size 10**. Then click on OK.  
        ![The "Edit Label" pop up window displaying the bolded and resized text.]({{ '/assets/images/tableau_intermediate_032.png' | relative_url }})

23. While still on the Label popup, under the**Label Appearance**section, click the**Alignment**dropdown menu. Set Horizontal alignment to right justified, Direction (of text) to a right\-side up A, Vertical alignment to top, and Wrap to off.  
![Label Alignment sub-menu with the alignment settings customized as described.]({{ '/assets/images/tableau_intermediate_033.png' | relative_url }})

    *Note: Sometimes you need to select a sideways A first and then the right\-side up A in order to make the change stay – just a bug. Now you should see a dynamic label for our latest data point.*

 

Create a dynamic bar graph embedded in a tooltip
------------------------------------------------

24. Let’s create a small bar graph that will show up as part of a tooltip when you hover over a bar in the graph. First, create a second worksheet, naming it **Tooltip**.  
![Location of the Create Worksheet button, with the button highlighted.]({{ '/assets/images/tableau_intermediate_000.png' | relative_url }})  
![Naming the new worksheet "Tooltip"]({{ '/assets/images/tableau_intermediate_000a.png' | relative_url }})

25. From Measures, drag **Metric Switcher** next to **columns**.

26. From Dimensions, drag**Case\_Type**next to **rows**.

27. Also, from Dimensions, drag**Case\_Type**to **Color** on the Marks card.

28. **Right click** on the **x\-axis** and **uncheck Show Header**.  
![Tooltip sheet with the X-axis menu, the menu item "Show Header" is highlighted.]({{ '/assets/images/tableau_intermediate_034.png' | relative_url }})

29. Within the bar graph, **right click** on the**Case\_Type header** listed above Confirmed and Deaths on the y\-axis. Click **Hide Field Labels for Rows**.  
![Header menu with menu item "Hide Field Labels for Rows" selected]({{ '/assets/images/tableau_intermediate_035.png' | relative_url }})

    *Note: Do not right click on the Case\_Type pill next to Rows. This specifically refers to an option only present when clicking on the tab within the graph.*

30. Click on **Labe**l on the Marks card and**check Show Mark Labels**. Then click away.  
![Final Tooltip horizontal bar graph, with labels and headers removed, and labels displayed]({{ '/assets/images/tableau_intermediate_036.png' | relative_url }})

31. Go back to the CasesbyDay worksheet and click on **Tooltip**on the Marks card.  
![The CasesbyDay sheet with "Tooltip" on the marks card highlighted]({{ '/assets/images/Tableau_Covid19_008.JPG' | relative_url }})

    Delete all text except for \<DAY(Date)\>. Then, underneath \<DAY(Date)\>, click on **Insert**, **Sheets**, **Tooltip**.  
        ![The "Edit Tooltip" pop up window with the “Insert” dropdown menu. The menu item “Sheets” and its sub-menu item “Tooltip” are also displayed.]({{ '/assets/images/tableau_intermediate_038.png' | relative_url }})

32. In the ensuing block of text, **highlight \<All Fields\>** (but leave the surrounding quotation marks), click on **Insert**, and then click**DAY(Date)**.  
![The "Edit Tooltip" window with Tooltip text inserted. In the text, the section <All Fields> is highlighted.]({{ '/assets/images/tableau_intermediate_039a.png' | relative_url }})  
![The "Edit Tooltip" window with the Insert dropdown menu selected. The menu item "DAY(Date)" is highlighted.]({{ '/assets/images/Tableau_Covid19_009.jpg' | relative_url }})  
![The "Edit Tooltip" window with the final text.]({{ '/assets/images/tableau_intermediate_040.png' | relative_url }})

    Then click OK. As you hover over the various bars, you will now see the Tooltip worksheet in miniature, filtered by the date, showing the day’s data.  
        ![The CasesbyDay worksheet with the tooltip appearing when hovering over a specific bar.]({{ '/assets/images/tableau_intermediate_041.png' | relative_url }})

33. To finish up, let’s clean up the axes a bit more. Now that we have added a label and a tooltip, **right click** on the **y axis** and **uncheck Show Header** to remove that extra information and make the graph more compact for our dashboard.  
![Y axis menu with the menu item "Show Header" highlighted]({{ '/assets/images/Tableau_Covid19_010.jpg' | relative_url }})  
![Final graph, with the y axis label removed]({{ '/assets/images/tableau_intermediate_042.png' | relative_url }})

 

Create side\-by\-side proportional symbol maps of cases with dynamic tooltips
-----------------------------------------------------------------------------

34. For the next section of the dashboard, we need to create some maps. First, create a third**worksheet** and name it **Map**. For best practices on mapping COVID data, including an explanation of the choice of why one might use a logarithmic scale to size the proportional symbols (which we will do in this case), see this[blog post from Esri on Mapping Coronavirus, responsibly](https://www.esri.com/arcgis-blog/products/product/mapping/mapping-coronavirus-responsibly/).

35. From the **Analysis** menu, select **Create Calculated Field...**, and name it **Log of Metric Switcher**. Paste in the following formula:  
`LOG(SUM([Metric Switcher]))  
//Used for the map mark size scaling`  
Then click on OK.  
*Note: The double forward slashes are used to denote comments. They are notes to help you and anyone else looking at your code to understand what it is doing, but it has no effect.*  
!["Create Calculated Field" pop up window with the described formula added]({{ '/assets/images/tableau_intermediate_043.png' | relative_url }})

36. Holding the **CTRL key** (or the Command key on a Mac), click on**Lat**, **Log of Metric Switcher**, and**Long**to select all of them from the Measures section. Release the CTRL key and click on the **Show Me**tab (top right). Click on the recommended graph type, which is a**proportional symbol map**. Then, click on the Show Me tab afterwards to close it.  
![The three variables selected in the side bar and the proportional symbol map highlighted under the “Show Me” drop down menu]({{ '/assets/images/Tableau_Covid19_011.jpg' | relative_url }})

37. In the columns section,**right click**on the **Long**pill and select**Dimension**. Do the same thing for the**Lat**pill.  
![Dropdown menu for the pill "AVG(Long)", with the menu item "Dimension" highlighted]({{ '/assets/images/tableau_intermediate_045a.png' | relative_url }})

38. From Dimensions, drag**Case\_Type**next to **columns**, to the **left** of Long to create side\-by\-side maps.

39. From Dimensions, drag**Case\_Type**to **Color**on the Marks card to apply the same colour scheme as the previous visualization.  
![Two maps, with the colour-coding and pill placement as described. "Colour" and "Case_Type", both in the Marks card, are highlighted ]({{ '/assets/images/tableau_intermediate_046a.png' | relative_url }})

40. From the **Analysis** menu, select**Create Calculated Field...**, and name it **Max Date**. Paste in the following formula:  
`{MAX([Date])}  
//A Level of Detail calculation, using curly brackets to calculate at the level of whole table, to find the most recent date`  
!["Create Calculated Field" pop up window with the described formula added for "Max Date"]({{ '/assets/images/tableau_intermediate_047.png' | relative_url }})

41. Create another calculated field: from the**Analysis**menu, select**Create Calculated Field...**, and name it **Date is Max**, Paste in the following formula:  
`[Max Date] = [Date]  
//Boolean logic used to display the most current date’s information`  
!["Create Calculated Field" pop up window with the described formula added for "Date is Max"]({{ '/assets/images/tableau_intermediate_048.png' | relative_url }})

42. From Dimensions, drag **Date is Max** to the **Filters** shelf, select**True**, and click on OK. This will ensure that the map is only displaying data for the most recent date.  
!["Filter [Date is Max]" pop up window, with the item "True" checked]({{ '/assets/images/tableau_intermediate_049a.png' | relative_url }})

43. From Measures, drag **Metric Switcher** to the**Filters**shelf. Select **Sum** and click Next.  
![The "Filter Field [Metric Switcher]" pop up window with the item "Sum" highlighted.]({{ '/assets/images/tableau_intermediate_050.png' | relative_url }})

    Click on the **At least** tab, set the **minimum value** to **1**, and then click OK. This ensures the map will only show data where there is at least 1 case.  
        ![The "Filter [Metric Switcher]" pop up window with the item “At least” and the minimum value of "1" highlighted.]({{ '/assets/images/tableau_intermediate_051.png' | relative_url }})

44. Click on **Color**on the Marks card, and in the window that pops up, make the following changes: under the **Effects** section, set Border and Halo to white, and set the**Opacity** to 50%. Click away from the popup to close it.  
!["Color" drop down menu with 50% opacity and the border and halo set to white]({{ '/assets/images/tableau_intermediate_052.png' | relative_url }})

45. From the**Analysis**menu, select**Create Calculated Field…**, and name it **Location Detail**. Paste in the following formula:  
`IF [Country_Region] = "US" THEN [Admin2]  
ELSEIF [Province_State] != "N/A" THEN [Province_State]  
ELSE [Country_Region]  
END  
//Used to determine the smallest level of detail for which there is information  
//Note that Admin2 stores information on US counties`  
!["Create Calculated Field" pop up window with the described formula added for "Location Detail"]({{ '/assets/images/tableau_intermediate_053.png' | relative_url }})
46. From Dimensions, drag **Location Detail** to **Detail**on the Marks card, so that data displayed on the map is shown at the smallest level of geography available (i.e., country, province/state or county).  
![Overview of Map worksheet with Location Detail added to the Detail marks card]({{ '/assets/images/tableau_intermediate_054a.png' | relative_url }})
47. Next, we will need to create a few calculated fields to use in our tooltip. From the**Analysis**menu, select**Create Calculated Field…**, and name it **Province State Label**. Paste in the following formula:  
`IF [Province_State] != "N/A" THEN [Province_State]  
ELSE ""  
END  
//Used in map tooltip to display a province/state name, if present`  
!["Create Calculated Field" pop up window with the described formula added for "Province State Label"]({{ '/assets/images/tableau_intermediate_055.png' | relative_url }})

48. From the**Analysis**menu, select**Create Calculated Field…**, and name it **Admin2 Label (US)**. Paste the following formula:  
`IF [Country_Region] = "US"  
THEN " | County: " + [Admin2]  
ELSE ""  
END  
//Used in the map tooltip to display a county name as well, if in the US`  
!["Create Calculated Field" pop up window with the described formula added for "Admin2 Label (US)"]({{ '/assets/images/tableau_intermediate_056.png' | relative_url }})

49. From Dimensions, drag **Max Date**,**Country\_Region**, **Admin 2 Label (US)**, and **Province State Label** on to **Tooltip**on the Marks card.  
![Marks card highlighting the added four variables to "Tooltip"]({{ '/assets/images/tableau_intermediate_057.png' | relative_url }})

50. Go to the Tooltip worksheet we created for the first visualization. **Right click** on the **Tooltip worksheet**’s tab at the bottom and select **Duplicate**. **Rename** the duplicate (called Tooltip (2\) by default)**MapTooltip**.  
![Tooltip worksheet menu with the menu item "Duplicate" highlighted]({{ '/assets/images/tableau_intermediate_058a.png' | relative_url }})

51. In the**MapTooltip**worksheet,**right click**on**Tooltip(DAY(Date))**in the Filters shelf and select **Remove**.

52. From **Dimensions**, drag **Date is Max** on to the**Filters**shelf, select**True**, and click on OK.

53. Return to the **Map worksheet** and click on **Tooltip**on the Marks card. Delete all the text and insert the following attributes in order (on separate lines where noted):  
`<ATTR(Max Date)>  
<ATTR(Country_Region)>  
<ATTR(Province State Label)><ATTR(Admin2 Label (US))>`  
Then, insert the**MapTooltip sheet** by clicking on **Insert**, then **Sheets**, then**MapTooltip**.  
Within the new line for the MapTooltip sheet, **highlight \<All fields\>** (leaving the quotation marks unselected) and then insert **Location Detail**.  
The final text should look like this:  
`<ATTR(Max Date)>  
<ATTR(Country_Region)>  
<ATTR(Province State Label)><ATTR(Admin2 Label (US))>  
<Sheet name="MapTooltip" maxwidth="300" maxheight="300" filter="<Location Detail>">`  
!["Edit Tooltip" pop up window with the described text inserted]({{ '/assets/images/tableau_intermediate_059.png' | relative_url }})

    Once you are done, click on OK. Hover over symbols on the map to see this tooltip in action.  
        ![Hovering over Anoka County, Minnesota in the map worksheet, with the related tooltip displayed ]({{ '/assets/images/tableau_intermediate_060.png' | relative_url }})
54. Finally, let’s clean up the map. In the lower right corner, there is a gray warning listing the number of null values. Click on this box.  
![Map with the gray button "2 nulls" at the bottom highlighted]({{ '/assets/images/tableau_intermediate_061.png' | relative_url }})

    When it asks you what to do, click on **Filter data**.  
        ![Null value warning popup, with the item "Filter data" highlighted]({{ '/assets/images/tableau_intermediate_062.png' | relative_url }})
55. Also, let’s remove a few headers as we did with the first visualization. **Right click** on the**Case\_Type header** at the top of the map, and select **Hide Field Labels for Columns**. **Right click** the **Confirmed header** on the top left of the map, and uncheck **Show Header**.  
![Final map displayed]({{ '/assets/images/tableau_intermediate_063.png' | relative_url }})

 

Create side\-by\-side bar graphs for cases by country
-----------------------------------------------------

56. For the third section of the dashboard, create a **new worksheet**, and name it “**CasesbyCountry**”.

57. From the Measures section, drag**Metric Switcher**next to **columns**.

58. From the Dimensions section, drag**Country\_Region**next to**rows**.

59. From Dimensions, drag**Case\_Type**next to **columns**, to the **left** of **Metric Switcher**.

60. Also, from Dimensions, drag**Case\_Type**to **Color** on the Marks card.

61. **Right click** on the **Country Region** pill next to rows and select**Sort**.  
![CasesbyCountry worksheet with the "Country_Region" dropdown menu. The menu item "Sort" is highlighted.]({{ '/assets/images/tableau_intermediate_064a.png' | relative_url }})

    Change Sort by to **Field**, under Field Name pick**Metric Switcher**, sort **Descending**, and then close the sort window.  
        ![The "Sort [Country_Region]" pop up window with the settings customized as described]({{ '/assets/images/tableau_intermediate_065a.png' | relative_url }})

62. From the **Analysis** menu, select**Totals**, and then select**Show Columns Grand Totals**.  
![The Analysis drop down menu with the menu item “Totals” and the sub-menu item "Show Column Grand Totals" highlighted]({{ '/assets/images/tableau_intermediate_066.png' | relative_url }})

63. Go back to the**Analysis**menu again, select**Totals**, and then select**Column Totals to Top**.  
![The Analysis drop down menu with the menu item “Totals” and the sub-menu item "Column Totals to Top" highlighted]({{ '/assets/images/tableau_intermediate_067a.png' | relative_url }})

    You will see the grand total appear as the first bar in the graph.  
        !["CasebyCountry" horizontal bar graphs with grand totals displayed at the top]({{ '/assets/images/tableau_intermediate_068.png' | relative_url }})

64. From Dimensions, drag **Date is Max** to the **Filters** shelf, select**True**, and click on OK. This will ensure that the graph is only displaying data for the most recent date.

65. Click on **Tooltip** on the Marks card. Deselect **Show tooltips** to remove tooltips for this graph.  
![The "Edit Tooltip" pop up window with the item "Show tooltips" unchecked]({{ '/assets/images/tableau_intermediate_069.png' | relative_url }})

66. Let’s clean up this bar graph so it will be ready to use in our dashboard. **Right click** on the **x axis** and **uncheck Show Header.** **Right click** on the **Case Type header**, and select **Hide Field Labels for Columns**. **Right click** on the **Confirmed header** and **uncheck Show Header**. **Right click** on**Country\_Region header** and **click Hide Field Labels for Rows**. After clean up, your graph should look like this:  
!["CasebyCountry" horizontal bar graphs with all headers and axis labels removed]({{ '/assets/images/tableau_intermediate_070.png' | relative_url }})

67. Click on **Label** on the Marks card and select **Show Mark Labels**. Also check off **Allow labels to overlap other marks**.  
![Label menu with the items "Show mark labels” and "Allow labels to overlap other marks" highlighted]({{ '/assets/images/tableau_intermediate_071.png' | relative_url }})

 

Create a dashboard to pull these three visualizations together
--------------------------------------------------------------

68. Finally, let’s create a dashboard to pull all of these visualizations together. Click on the **new dashboard** icon at the bottom to create a new dashboard.  
!["New Dashboard" button highlighted]({{ '/assets/images/tableau_intermediate_072.png' | relative_url }})

69. **Under Size**on the left, use the dropdown menu to change Fixed Size to **Automatic**.  
![Dashboard side bar with the Size dropdown menu, the menu item "Automatic" is highlighted]({{ '/assets/images/Tableau_Covid19_012.jpg' | relative_url }})

70. Drag**CasesbyDay**, from the sheet list on the left, on to the dashboard.  
![Dragging the "CasesbyDay" sheet onto the dashboard]({{ '/assets/images/tableau_intermediate_074.png' | relative_url }})

    Then, drag **Map**, from the sheet list, to take up the **bottom half** of the dashboard.  
        ![Dragging the "Map" sheet to the bottom half of the dashboard]({{ '/assets/images/tableau_intermediate_075.png' | relative_url }})

    Finally, drag**CasesbyCountry**, from the sheet list, to take up the **bottom quarter** of the dashboard.  
        ![Dashboard with "CasesbyCountry" sheet dragged to the bottom quarter]({{ '/assets/images/tableau_intermediate_076.png' | relative_url }})

71. From under Objects (bottom left), drag **Text** to the **top** of the dashboard. This will be your title.  
![Dragging "Text" to the top of the dashboard]({{ '/assets/images/tableau_intermediate_077.png' | relative_url }})

    Call your dashboard **COVID\-19 Cases**. Change the text size to 20 points, bold it, and click on OK.  
        !["Edit Text" pop up window with the text inserted and customized as described]({{ '/assets/images/tableau_intermediate_078.png' | relative_url }})

    Resize the bottom of this new text box to minimize white space.  
        ![The dashboard after resizing the title bar]({{ '/assets/images/tableau_intermediate_079.png' | relative_url }})

72. Drag the **date filter**(using the dark gray handle that appears when you click on the title of the Date filter box) to right underneath the title, such that it extends across the top of the dashboard.  
![The "Date" filter item with the dark gray handle at the top highlighted]({{ '/assets/images/tableau_intermediate_080.png' | relative_url }})

    You might need to resize its height.  
        ![Dashboard with "Date" filter item moved and resized]({{ '/assets/images/tableau_intermediate_081.png' | relative_url }})

73. Similarly, drag the**Selected Metric**parameter and position it so that it occupies half of the row that Date currently occupies.  
![Dashboard with the "Select Metric" item moved]({{ '/assets/images/tableau_intermediate_082.png' | relative_url }})

74. Finally, drag the**Country\_Region**filter into the same row and resize the widths of all three boxes so that they have equal space. There should be three filters all at the top of the dashboard under the title. You might need to resize the visualizations after doing this, as the filters might squish the first bar graph a bit.  
![Dashboard with the "Country_Region" filter item moved]({{ '/assets/images/tableau_intermediate_083.png' | relative_url }})

75. **Remove** theCase\_Type and Log of Metric Switch boxes on the right by clicking on them and then clicking on the X that appears in the top left corner of the box.  
![Removing the "Case_Type" and "Log of Metric Switcher" items from the dashboard]({{ '/assets/images/tableau_intermediate_084.png' | relative_url }})

76. Click on the**CasesbyDay**container, and then click on the **More Options arrow**from the dark gray menu on the left. Uncheck **Title**.  
!["CasesbyDay" with the "More Options" button highlighted]({{ '/assets/images/tableau_intermediate_085.png' | relative_url }})  
!["CasesbyDay" "More Options" drop down menu with the item "Title" selected]({{ '/assets/images/tableau_intermediate_086.png' | relative_url }})

    Repeat this step for the **Map** and**CasesbyCountry**containers.

77. From the Objects pane on the left, drag **Blank** space to the **left** side of the row with the first bar graph. Repeat with the row immediately under: the map. Adjust the blank spaces so that they are aligned – they should snap into alignment \- and take up approximately the left 15% of the dashboard. Use these blank spaces to try to align the centre line of all 3 visualizations. Consider switching into Presentation Mode (by pressing F7 and using the ESC key to exit) to better assess the overall look.  
![Dashboard with the "Blank" object being dragged to two locations]({{ '/assets/images/tableau_intermediate_087.png' | relative_url }})

78. Finally, let’s apply the Country\_Region filter to the first two visualizations. Click on the **Country Region** **filter**, and then click on the **More Options arrow** from the dark gray menu on the left. Under **Apply to Worksheets**, select**Selected Worksheets...** 
!["Country_Region " "More Options" drop down menu with the item "Apply to Worksheets" and the sub menu item "Selected Worksheets" highlighted]({{ '/assets/images/tableau_intermediate_088.png' | relative_url }})

    Select everything except CasesByCountry.  
        !["Apply Filter to Worksheets" pop up window with the items "CasesbyDay" and "Map" checked off]({{ '/assets/images/tableau_intermediate_089.png' | relative_url }})

79. It’s time to test your dashboard. Change between a few different countries. Hover over the proportional symbols in the map to see the count of cases. Under Switch Metric, switch between Total Cases and New Cases. Ensure that everything is working as expected; if not, consider retracing your steps with the problematic worksheet.  
![Testing dashboard by changing Switch Metric, New Cases, and the map tooltip]({{ '/assets/images/tableau_intermediate_090.png' | relative_url }})

80. Change Country\_Region back to (All) and under Select Metric, return it to Total Cases.

81. **Right click** on the **Dashboard1** tab at the bottom of the screen, and select**Hide All Sheets**.  
![Dashboard menu with the menu item "Hide All Sheets" highlighted]({{ '/assets/images/tableau_intermediate_091.png' | relative_url }})

    This will hide all sheets other than **Tooltip** and**MapTooltip**. **Right click** on each of them and select**Hide**.  
        ![Tooltip worksheet menu with the item "Hide" highlighted]({{ '/assets/images/tableau_intermediate_092.png' | relative_url }})

    This ensures that your viewer will only see the main dashboard, and they will not be distracted by seeing the other sheets listed as tabs at the bottom. You might at this point also want to adjust the sizes of your visualizations to even out the display.  
        ![The finished dashboard]({{ '/assets/images/tableau_intermediate_997a.png' | relative_url }})

That’s it! Your dashboard is now complete. If you downloaded Tableau’s dashboard workbook file from Tableau Public, you will notice that not everything in that file is covered in this tutorial. Feel free to explore further and try to understand and recreate all aspects of the dashboard for your own learning.

Technique: [Data Visualization](/technique/data-visualization) \| Tools: [Tableau](/tools/tableau)**Date Created:** 2020\-04\-07**Updated:** 2022\-12\-15
