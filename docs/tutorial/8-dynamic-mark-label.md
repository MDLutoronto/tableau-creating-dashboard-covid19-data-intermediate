---
title: Create a dynamic mark label
parent: Tableau Tutorial
layout: default
created_date: 2020-04-07
staff:
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 8
grand_parent: Creating a Tableau Dashboard using COVID-19 data (Intermediate)
---
### Create a dynamic mark label

{:style="counter-reset:step-counter 19"}

20. Let’s add a dynamic mark label to highlight today’s data in the graph. From Measures, drag **Metric Switcher** to **Label** on the Marks card. From Dimensions, drag **Date** to **Label** too.  
![Label mark on the marks card is highlighted. ]({{ '/assets/images/tableau_intermediate_029.png' | relative_url }})

21. **Right click** on the **YEAR(Date)** pill listed on the Marks card, and select **Exact Date**.  
    ![The menu from the "YEAR(Date)" pill, with the menu item "Exact Date" highlighted]({{ '/assets/images/tableau_intermediate_030.png' | relative_url }})

22. Click on **Label** on the Marks card. Under the **Marks to Label** section, select **Most Recent**. Under the **Label Appearance** section, click on the gray button with ellipses next to Text.  
    ![Label card window with the ellipses button and the "Most Recent" button highlighted.]({{ '/assets/images/tableau_intermediate_031.png' | relative_url }})

    Center both lines (if not centered already) and bold them. Change <SUM(Metric Switcher)> to **size 12**, and <**Date**> to **size 10**. Then click on OK. 
    
    ![The "Edit Label" pop up window displaying the bolded and resized text.]({{ '/assets/images/tableau_intermediate_032.png' | relative_url }})

23. While still on the Label popup, under the **Label Appearance** section, click the **Alignment** dropdown menu. Set Horizontal alignment to right justified, Direction (of text) to a right-side up A, Vertical alignment to top, and Wrap to off.  
![Label Alignment sub-menu with the alignment settings customized as described.]({{ '/assets/images/tableau_intermediate_033.png' | relative_url }})

    *Note: Sometimes you need to select a sideways A first and then the right-side up A in order to make the change stay – just a bug. Now you should see a dynamic label for our latest data point.*

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)