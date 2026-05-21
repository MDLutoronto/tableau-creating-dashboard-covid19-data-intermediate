---
title: Create a parameter so that the graphs change based on whether the user wants to see total cases or new cases
parent: Tableau Tutorial
layout: default
created_date: 2020-04-07
staff:
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 7
grand_parent: Creating a Tableau Dashboard using COVID-19 data (Intermediate)
---
### Create a parameter so that the graphs change based on whether the user wants to see total cases or new cases

{:style="counter-reset:step-counter 15"}

16. **Right click** in the blank space under the Measures section, and select **Create Parameter…** 
![The Field menu displayed with the menu item “Create Parameter” highlighted.]({{ '/assets/images/Tableau_Covid19_005.jpg' | relative_url }})

    Name it **Select Metric**. Change data type to **Integer**. Under Allowable values, click **List**. In the **List of values** below, click on the first row under Value and type **0**. Next to it, in the same row under Display As, type **Total Cases**. On the next row, under Value type **1** and under Display As type **New Cases**. Click elsewhere in the list to stop editing New Cases. Then click OK.  
        ![The "Create Parameter" pop up window with details filled in as described.]({{ '/assets/images/tableau_intermediate_023.png' | relative_url }})

    You will see a new section appear under the Measures section, called **Parameter**, listing the new parameter we just created. This parameter will allow the user to specify if they want to review data for total cases or new cases.  
        ![Image of the Side Bar with the new Parameters section highlighted.]({{ '/assets/images/Tableau_Covid19_006.JPG' | relative_url }})
17. Currently, the parameter just collects input from the user, but doesn't act on it. To apply the choice to the graph, we need to create a field that acts on that choice and displays what data was requested. From the **Analysis** menu, select **Create Calculated Field...**,  
![Analysis drop down menu with the menu item "Create Calculated Field" highlighted.]({{ '/assets/images/tableau_intermediate_024.png' | relative_url }})

    and name it **Metric Switcher**. Paste in the following formula:  
        ```
        IF [Select Metric]=0 THEN [Cases] ELSE [Difference] END
        ```
        ![Create Calculated Field pop up window with formula copied in]({{ '/assets/images/tableau_intermediate_025.png' | relative_url }})

    Then click on OK. You should see this new field in the Measures section.  
        *Note: Whenever a variable is mentioned (e.g. [Cases]), you can either type the variable name exactly as it is shown or drag the variable’s pill into the calculation field.*
18. In the rows section, **right click** on **SUM(Cases)**, and select **Remove**.  
![Dropdown menu for the pill "SUM(Cases)". The menu item "Remove" is highlighted.]({{ '/assets/images/tableau_intermediate_026.png' | relative_url }})

    Then, from Measures, drag **Metric Switcher** next to **Rows**.  
        ![The pills in the Columns and Rows sections are displayed.]({{ '/assets/images/tableau_intermediate_027.png' | relative_url }})

19. From the Parameters section, **right click** on **Select Metric**, and select **Show Parameter**.  
![Menu that appears after clicking on Select Metric. The menu item "Show Parameter" is also highlighted.]({{ '/assets/images/Tableau_Covid19_007.jpg' | relative_url }})

    Now you can adjust whether Total Cases or New Cases are displayed in the bar graphs using this menu. It will sum either the field Cases or Difference depending on what was selected.



**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)