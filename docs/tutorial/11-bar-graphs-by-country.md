---
title: Create side-by-side bar graphs for cases by country
parent: Tableau Tutorial
layout: default
created_date: 2020-04-07
staff:
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 11
grand_parent: Creating a Tableau Dashboard using COVID-19 data (Intermediate)
---
### Create side-by-side bar graphs for cases by country

{:style="counter-reset:step-counter 55"}

56. For the third section of the dashboard, create a **new worksheet**, and name it “**CasesbyCountry**”.

57. From the Measures section, drag **Metric Switcher** next to **columns**.

58. From the Dimensions section, drag **Country_Region** next to **rows**.

59. From Dimensions, drag **Case_Type** next to **columns**, to the **left** of **Metric Switcher**.

60. Also, from Dimensions, drag **Case_Type** to **Color** on the Marks card.

61. **Right click** on the **Country Region** pill next to rows and select **Sort**.  
![CasesbyCountry worksheet with the "Country_Region" dropdown menu. The menu item "Sort" is highlighted.]({{ '/assets/images/tableau_intermediate_064a.png' | relative_url }})

    Change Sort by to **Field**, under Field Name pick **Metric Switcher**, sort **Descending**, and then close the sort window.  
        ![The "Sort [Country_Region]" pop up window with the settings customized as described]({{ '/assets/images/tableau_intermediate_065a.png' | relative_url }})

62. From the **Analysis** menu, select **Totals**, and then select **Show Columns Grand Totals**.  
![The Analysis drop down menu with the menu item “Totals” and the sub-menu item "Show Column Grand Totals" highlighted]({{ '/assets/images/tableau_intermediate_066.png' | relative_url }})

63. Go back to the **Analysis** menu again, select **Totals**, and then select **Column Totals to Top**.  
![The Analysis drop down menu with the menu item “Totals” and the sub-menu item "Column Totals to Top" highlighted]({{ '/assets/images/tableau_intermediate_067a.png' | relative_url }})

    You will see the grand total appear as the first bar in the graph.  
        !["CasebyCountry" horizontal bar graphs with grand totals displayed at the top]({{ '/assets/images/tableau_intermediate_068.png' | relative_url }})

64. From Dimensions, drag **Date is Max** to the **Filters** shelf, select **True**, and click on OK. This will ensure that the graph is only displaying data for the most recent date.

65. Click on **Tooltip** on the Marks card. Deselect **Show tooltips** to remove tooltips for this graph.  
![The "Edit Tooltip" pop up window with the item "Show tooltips" unchecked]({{ '/assets/images/tableau_intermediate_069.png' | relative_url }})

66. Let’s clean up this bar graph so it will be ready to use in our dashboard. **Right click** on the **x axis** and **uncheck Show Header.** **Right click** on the **Case Type header**, and select **Hide Field Labels for Columns**. **Right click** on the **Confirmed header** and **uncheck Show Header**. **Right click** on **Country_Region header** and **click Hide Field Labels for Rows**. After clean up, your graph should look like this:  
!["CasebyCountry" horizontal bar graphs with all headers and axis labels removed]({{ '/assets/images/tableau_intermediate_070.png' | relative_url }})

67. Click on **Label** on the Marks card and select **Show Mark Labels**. Also check off **Allow labels to overlap other marks**.  
    ![Label menu with the items "Show mark labels” and "Allow labels to overlap other marks" highlighted]({{ '/assets/images/tableau_intermediate_071.png' | relative_url }})

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)