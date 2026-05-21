---
title: Create a dynamic bar graph embedded in a tooltip
parent: Tableau Tutorial
layout: default
created_date: 2020-04-07
staff:
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 9
grand_parent: Creating a Tableau Dashboard using COVID-19 data (Intermediate)
---
### Create a dynamic bar graph embedded in a tooltip

{:style="counter-reset:step-counter 23"}

24. Let’s create a small bar graph that will show up as part of a tooltip when you hover over a bar in the graph. First, create a second worksheet, naming it **Tooltip**.  
![Location of the Create Worksheet button, with the button highlighted.]({{ '/assets/images/tableau_intermediate_000.png' | relative_url }})  
![Naming the new worksheet "Tooltip"]({{ '/assets/images/tableau_intermediate_000a.png' | relative_url }})

25. From Measures, drag **Metric Switcher** next to **columns**.

26. From Dimensions, drag **Case_Type** next to **rows**.

27. Also, from Dimensions, drag **Case_Type** to **Color** on the Marks card.

28. **Right click** on the **x-axis** and **uncheck Show Header**.  
![Tooltip sheet with the X-axis menu, the menu item "Show Header" is highlighted.]({{ '/assets/images/tableau_intermediate_034.png' | relative_url }})

29. Within the bar graph, **right click** on the **Case_Type header** listed above Confirmed and Deaths on the y-axis. Click **Hide Field Labels for Rows**.  
![Header menu with menu item "Hide Field Labels for Rows" selected]({{ '/assets/images/tableau_intermediate_035.png' | relative_url }})

    *Note: Do not right click on the Case_Type pill next to Rows. This specifically refers to an option only present when clicking on the tab within the graph.*

30. Click on **Label** on the Marks card and **check Show Mark Labels**. Then click away.  
![Final Tooltip horizontal bar graph, with labels and headers removed, and labels displayed]({{ '/assets/images/tableau_intermediate_036.png' | relative_url }})

31. Go back to the CasesbyDay worksheet and click on **Tooltip** on the Marks card.  
![The CasesbyDay sheet with "Tooltip" on the marks card highlighted]({{ '/assets/images/Tableau_Covid19_008.JPG' | relative_url }})

    Delete all text except for <DAY(Date)>. Then, underneath <DAY(Date)>, click on **Insert**, **Sheets**, **Tooltip**.  
        ![The "Edit Tooltip" pop up window with the “Insert” dropdown menu. The menu item “Sheets” and its sub-menu item “Tooltip” are also displayed.]({{ '/assets/images/tableau_intermediate_038.png' | relative_url }})

32. In the ensuing block of text, **highlight** <**All Fields**> (but leave the surrounding quotation marks), click on **Insert**, and then click **DAY(Date)**.  

    ![The "Edit Tooltip" window with Tooltip text inserted. In the text, the section 'All Fields' is highlighted.]({{ '/assets/images/tableau_intermediate_039a.png' | relative_url }})  

    ![The "Edit Tooltip" window with the Insert dropdown menu selected. The menu item "DAY(Date)" is highlighted.]({{ '/assets/images/Tableau_Covid19_009.jpg' | relative_url }})  

    ![The "Edit Tooltip" window with the final text.]({{ '/assets/images/tableau_intermediate_040.png' | relative_url }})

    Then click OK. As you hover over the various bars, you will now see the Tooltip worksheet in miniature, filtered by the date, showing the day’s data.  
        ![The CasesbyDay worksheet with the tooltip appearing when hovering over a specific bar.]({{ '/assets/images/tableau_intermediate_041.png' | relative_url }})

33. To finish up, let’s clean up the axes a bit more. Now that we have added a label and a tooltip, **right click** on the **y axis** and **uncheck Show Header** to remove that extra information and make the graph more compact for our dashboard.  
![Y axis menu with the menu item "Show Header" highlighted]({{ '/assets/images/Tableau_Covid19_010.jpg' | relative_url }})  
![Final graph, with the y axis label removed]({{ '/assets/images/tableau_intermediate_042.png' | relative_url }})

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)