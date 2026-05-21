---
title: Create a dashboard to pull these three visualizations together
parent: Tableau Tutorial
layout: default
created_date: 2020-04-07
staff:
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 12
grand_parent: Creating a Tableau Dashboard using COVID-19 data (Intermediate)
---
### Create a dashboard to pull these three visualizations together

{:style="counter-reset:step-counter 67"}

68. Finally, let’s create a dashboard to pull all of these visualizations together. Click on the **new dashboard** icon at the bottom to create a new dashboard.  
!["New Dashboard" button highlighted]({{ '/assets/images/tableau_intermediate_072.png' | relative_url }})

69. **Under Size** on the left, use the dropdown menu to change Fixed Size to **Automatic**.  
![Dashboard side bar with the Size dropdown menu, the menu item "Automatic" is highlighted]({{ '/assets/images/Tableau_Covid19_012.jpg' | relative_url }})

70. Drag **CasesbyDay**, from the sheet list on the left, on to the dashboard.  
![Dragging the "CasesbyDay" sheet onto the dashboard]({{ '/assets/images/tableau_intermediate_074.png' | relative_url }})

    Then, drag **Map**, from the sheet list, to take up the **bottom half** of the dashboard.  
        ![Dragging the "Map" sheet to the bottom half of the dashboard]({{ '/assets/images/tableau_intermediate_075.png' | relative_url }})

    Finally, drag **CasesbyCountry**, from the sheet list, to take up the **bottom quarter** of the dashboard.  
        ![Dashboard with "CasesbyCountry" sheet dragged to the bottom quarter]({{ '/assets/images/tableau_intermediate_076.png' | relative_url }})

71. From under Objects (bottom left), drag **Text** to the **top** of the dashboard. This will be your title.  
![Dragging "Text" to the top of the dashboard]({{ '/assets/images/tableau_intermediate_077.png' | relative_url }})

    Call your dashboard **COVID-19 Cases**. Change the text size to 20 points, bold it, and click on OK.  
        !["Edit Text" pop up window with the text inserted and customized as described]({{ '/assets/images/tableau_intermediate_078.png' | relative_url }})

    Resize the bottom of this new text box to minimize white space.  
        ![The dashboard after resizing the title bar]({{ '/assets/images/tableau_intermediate_079.png' | relative_url }})

72. Drag the **date filter** (using the dark gray handle that appears when you click on the title of the Date filter box) to right underneath the title, such that it extends across the top of the dashboard.  
![The "Date" filter item with the dark gray handle at the top highlighted]({{ '/assets/images/tableau_intermediate_080.png' | relative_url }})

    You might need to resize its height.  
        ![Dashboard with "Date" filter item moved and resized]({{ '/assets/images/tableau_intermediate_081.png' | relative_url }})

73. Similarly, drag the **Selected Metric** parameter and position it so that it occupies half of the row that Date currently occupies.  
![Dashboard with the "Select Metric" item moved]({{ '/assets/images/tableau_intermediate_082.png' | relative_url }})

74. Finally, drag the **Country_Region** filter into the same row and resize the widths of all three boxes so that they have equal space. There should be three filters all at the top of the dashboard under the title. You might need to resize the visualizations after doing this, as the filters might squish the first bar graph a bit.  
![Dashboard with the "Country_Region" filter item moved]({{ '/assets/images/tableau_intermediate_083.png' | relative_url }})

75. **Remove** the Case_Type and Log of Metric Switch boxes on the right by clicking on them and then clicking on the X that appears in the top left corner of the box.  
![Removing the "Case_Type" and "Log of Metric Switcher" items from the dashboard]({{ '/assets/images/tableau_intermediate_084.png' | relative_url }})

76. Click on the **CasesbyDay** container, and then click on the **More Options arrow** from the dark gray menu on the left. Uncheck **Title**.  
!["CasesbyDay" with the "More Options" button highlighted]({{ '/assets/images/tableau_intermediate_085.png' | relative_url }})  
!["CasesbyDay" "More Options" drop down menu with the item "Title" selected]({{ '/assets/images/tableau_intermediate_086.png' | relative_url }})

    Repeat this step for the **Map** and **CasesbyCountry** containers.

77. From the Objects pane on the left, drag **Blank** space to the **left** side of the row with the first bar graph. Repeat with the row immediately under: the map. Adjust the blank spaces so that they are aligned – they should snap into alignment - and take up approximately the left 15% of the dashboard. Use these blank spaces to try to align the centre line of all 3 visualizations. Consider switching into Presentation Mode (by pressing F7 and using the ESC key to exit) to better assess the overall look.  
![Dashboard with the "Blank" object being dragged to two locations]({{ '/assets/images/tableau_intermediate_087.png' | relative_url }})

78. Finally, let’s apply the Country_Region filter to the first two visualizations. Click on the **Country Region** **filter**, and then click on the **More Options arrow** from the dark gray menu on the left. Under **Apply to Worksheets**, select **Selected Worksheets...** 
!["Country_Region " "More Options" drop down menu with the item "Apply to Worksheets" and the sub menu item "Selected Worksheets" highlighted]({{ '/assets/images/tableau_intermediate_088.png' | relative_url }})

    Select everything except CasesByCountry.  
        !["Apply Filter to Worksheets" pop up window with the items "CasesbyDay" and "Map" checked off]({{ '/assets/images/tableau_intermediate_089.png' | relative_url }})

79. It’s time to test your dashboard. Change between a few different countries. Hover over the proportional symbols in the map to see the count of cases. Under Switch Metric, switch between Total Cases and New Cases. Ensure that everything is working as expected; if not, consider retracing your steps with the problematic worksheet.  
![Testing dashboard by changing Switch Metric, New Cases, and the map tooltip]({{ '/assets/images/tableau_intermediate_090.png' | relative_url }})

80. Change Country_Region back to (All) and under Select Metric, return it to Total Cases.

81. **Right click** on the **Dashboard1** tab at the bottom of the screen, and select **Hide All Sheets**.  
![Dashboard menu with the menu item "Hide All Sheets" highlighted]({{ '/assets/images/tableau_intermediate_091.png' | relative_url }})

    This will hide all sheets other than **Tooltip** and **MapTooltip**. **Right click** on each of them and select **Hide**.  
        ![Tooltip worksheet menu with the item "Hide" highlighted]({{ '/assets/images/tableau_intermediate_092.png' | relative_url }})

    This ensures that your viewer will only see the main dashboard, and they will not be distracted by seeing the other sheets listed as tabs at the bottom. You might at this point also want to adjust the sizes of your visualizations to even out the display.  
        ![The finished dashboard]({{ '/assets/images/tableau_intermediate_997a.png' | relative_url }})

That’s it! Your dashboard is now complete. If you downloaded Tableau’s dashboard workbook file from Tableau Public, you will notice that not everything in that file is covered in this tutorial. Feel free to explore further and try to understand and recreate all aspects of the dashboard for your own learning.

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)