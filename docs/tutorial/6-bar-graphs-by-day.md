---
title: Create side-by-side bar graphs with filters for cases by day
parent: Tableau Tutorial
layout: default
created_date: 2020-04-07
staff:
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 6
---
### Create side-by-side bar graphs with filters for cases by day

{:style="counter-reset:step-counter 4"}

5. First, we will create the side by side bar graphs of confirmed cases and deaths over time. **Right click** on the Sheet 1 tab at the bottom, select **Rename**, and give it the name “CasesbyDay”.  
![Renaming the new sheet to “CasesbyDay”.]({{ '/assets/images/tableau_intermediate_005a.png' | relative_url }})

6. From the Dimensions section, drag **Date** next to **columns**. Note that it defaults to YEAR (Date). To format how the date is displayed, **right click** on YEAR (Date) and select **Day**, specifically the option that has the example "8th May, 2015".  
![Drop down menu for YEAR(Date) with the menu item 'Day' highlighted]({{ '/assets/images/Tableau_Covid19_001.jpg' | relative_url }})

7. **Right click** again on **DAY (Date)** and this time select **Discrete** - as the data updates daily, it is not a continuous flow.  
![Drop down menu with the menu item "Discrete" highlighted]({{ '/assets/images/Tableau_Covid19_002.jpg' | relative_url }})

8. From the Measures section, drag **Cases** next to **rows**.  
![Column and row section is displayed with the respective pills.]({{ '/assets/images/tableau_intermediate_008.png' | relative_url }})

9. On the Marks card, from its drop down that says Automatic, change the selection to **Bar**.  
![The menu item 'Bar' highlighted in the Marks dropdown menu]({{ '/assets/images/Tableau_Covid19_003.jpg' | relative_url }})

10. From Dimensions, drag **Case_Type** next to **columns**, to the **left** of DAY (Date). This creates two side-by-side bar graphs showing cases by day. By sharing the y-axis, you can more accurately compare the data. To see them both without scrolling, drop down on Standard at the top and change the view to Entire View.  
    ![Two bar charts are displayed. Above them, the view option 'Entire View' and the pill 'Case_Type' highlighted]({{ '/assets/images/tableau_intermediate_010.png' | relative_url }})

11. Let’s use colours to differentiate the two categories. Drag **Case_Type** to **Color** on the Marks card. Click on Color and then select "Edit Colors...".  
    !["Edit Colours" button highlighted.]({{ '/assets/images/tableau_intermediate_011.png' | relative_url }})

    Leave Confirmed cases at the default blue, but select **Deaths** then the **purple** available in the default palette to change it. Then click on OK.  
        ![The "Edit colours" menu, with "Deaths" assigned colour changed to purple.]({{ '/assets/images/tableau_intermediate_012.png' | relative_url }})

12. Let’s clean up the axes so that when the graphs are displayed in the dashboard, they don’t take up so much room. Right click on the **x-axis** listing the dates, and **uncheck Show Header**. Since one day will be highlighted, click in the white space of the graph to unselect that day.  
    ![X-axis menu with the menu item "Show Header" highlighted.]({{ '/assets/images/tableau_intermediate_013.png' | relative_url }})

13. **Right click** on the **Case Type header** in the graph, and select **Hide Field Label for Columns**.  
    ![Dropdown menu for the Case_Type column. The menu item option "Hide Field Labels for Columns" is highlighted.]({{ '/assets/images/tableau_intermediate_014a.png' | relative_url }})

14. We can also add some filters to these graphs, so that a user could filter to see a certain country or date range. From Dimensions, drag **Country_Region** to the **Filters** shelf. Click on **All** and then OK.  
    ![“Country_Region” in the Dimensions section is highlighted, as well as the Filters Shelf. The resulting pop-up window is also shown. ]({{ '/assets/images/Tableau_Covid19_004.JPG' | relative_url }})

    Then **right click** on the **Country_Region** pill on the Filters shelf and select **Show Filter**.  
        ![Dropdown menu for the "Country_Region" pill, with the menu item "Show Filter" highlighted.]({{ '/assets/images/tableau_intermediate_016.png' | relative_url }})

    You will see a list of countries on the right. If you hover over the title of the list, you should see a small arrow on the right that you can use to access a drop-down menu.  
        ![Dropdown button on the "Country_Region" card highlighted. ]({{ '/assets/images/tableau_intermediate_017.png' | relative_url }})

    Click on it and select **Single Value (dropdown)**.  
        ![Dropdown menu for the “Country_Region” card, with the menu item “Single Value (dropdown)” selected.]({{ '/assets/images/tableau_intermediate_018.png' | relative_url }})

    This makes the filter take up a much smaller amount of space on the screen, and eventually the dashboard. Make the country filter include All countries for now.

15. From Dimensions, drag **Date** to the **Filters** shelf. Select **Relative Date** and click Next.  
    !["Filter Field [Date]" pop up menu with the menu item "Relative Date" highlighted.]({{ '/assets/images/tableau_intermediate_019.png' | relative_url }})

    Go to the **Starting date** tab, check **Include Null Values**, and then click OK.  
     ![The "Filter [Date]" pop up window the items “Starting date” and "Include Null Values" highlighted. ]({{ '/assets/images/tableau_intermediate_020.png' | relative_url }})

    Then **right click** on the **Date** pill on the Filters shelf and select **Show Filter**. You will see a slider Date filter on the right.  
        ![“Date”, “Country_Region”, and “Case_Type” filter and legend cards displayed.]({{ '/assets/images/tableau_intermediate_021.png' | relative_url }})

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)