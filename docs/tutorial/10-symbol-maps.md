---
title: Create side-by-side proportional symbol maps of cases with dynamic tooltips
parent: Tableau Tutorial
layout: default
created_date: 2020-04-07
staff:
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
maintainer: 
    - name: Kelly Schultz
      link: https://library.utoronto.ca/staff/kelly-schultz
nav_order: 10
---
### Create side-by-side proportional symbol maps of cases with dynamic tooltips

{:style="counter-reset:step-counter 33"}

34. For the next section of the dashboard, we need to create some maps. First, create a third **worksheet** and name it **Map**. For best practices on mapping COVID data, including an explanation of the choice of why one might use a logarithmic scale to size the proportional symbols (which we will do in this case), see this [blog post from Esri on Mapping Coronavirus, responsibly](https://www.esri.com/arcgis-blog/products/product/mapping/mapping-coronavirus-responsibly/).

35. From the **Analysis** menu, select **Create Calculated Field...**, and name it **Log of Metric Switcher**. Paste in the following formula:  
```
LOG(SUM([Metric Switcher]))
//Used for the map mark size scaling
```
Then click on OK.  
*Note: The double forward slashes are used to denote comments. They are notes to help you and anyone else looking at your code to understand what it is doing, but it has no effect.*  
!["Create Calculated Field" pop up window with the described formula added]({{ '/assets/images/tableau_intermediate_043.png' | relative_url }})

36. Holding the **CTRL key** (or the Command key on a Mac), click on **Lat**, **Log of Metric Switcher**, and **Long** to select all of them from the Measures section. Release the CTRL key and click on the **Show Me** tab (top right). Click on the recommended graph type, which is a **proportional symbol map**. Then, click on the Show Me tab afterwards to close it.  
![The three variables selected in the side bar and the proportional symbol map highlighted under the “Show Me” drop down menu]({{ '/assets/images/Tableau_Covid19_011.jpg' | relative_url }})

37. In the columns section, **right click** on the **Long** pill and select **Dimension**. Do the same thing for the **Lat** pill.  
![Dropdown menu for the pill "AVG(Long)", with the menu item "Dimension" highlighted]({{ '/assets/images/tableau_intermediate_045a.png' | relative_url }})

38. From Dimensions, drag **Case_Type** next to **columns**, to the **left** of Long to create side-by-side maps.

39. From Dimensions, drag **Case_Type** to **Color** on the Marks card to apply the same colour scheme as the previous visualization.  
![Two maps, with the colour-coding and pill placement as described. "Colour" and "Case_Type", both in the Marks card, are highlighted ]({{ '/assets/images/tableau_intermediate_046a.png' | relative_url }})

40. From the **Analysis** menu, select **Create Calculated Field...**, and name it **Max Date**. Paste in the following formula:  
    ```
    {MAX([Date])}
    //A Level of Detail calculation, using curly brackets to calculate at the level of whole table, to find the most recent date
    ```  
    !["Create Calculated Field" pop up window with the described formula added for "Max Date"]({{ '/assets/images/tableau_intermediate_047.png' | relative_url }})

41. Create another calculated field: from the **Analysis** menu, select **Create Calculated Field...**, and name it **Date is Max**, Paste in the following formula:    
```
[Max Date] = [Date]
//Boolean logic used to display the most current date’s information
``` 
!["Create Calculated Field" pop up window with the described formula added for "Date is Max"]({{ '/assets/images/tableau_intermediate_048.png' | relative_url }})

42. From Dimensions, drag **Date is Max** to the **Filters** shelf, select **True**, and click on OK. This will ensure that the map is only displaying data for the most recent date.  
!["Filter [Date is Max]" pop up window, with the item "True" checked]({{ '/assets/images/tableau_intermediate_049a.png' | relative_url }})

43. From Measures, drag **Metric Switcher** to the **Filters** shelf. Select **Sum** and click Next.  
![The "Filter Field [Metric Switcher]" pop up window with the item "Sum" highlighted.]({{ '/assets/images/tableau_intermediate_050.png' | relative_url }})

    Click on the **At least** tab, set the **minimum value** to **1**, and then click OK. This ensures the map will only show data where there is at least 1 case.  
        ![The "Filter [Metric Switcher]" pop up window with the item “At least” and the minimum value of "1" highlighted.]({{ '/assets/images/tableau_intermediate_051.png' | relative_url }})

44. Click on **Color** on the Marks card, and in the window that pops up, make the following changes: under the **Effects** section, set Border and Halo to white, and set the **Opacity** to 50%. Click away from the popup to close it.  
!["Color" drop down menu with 50% opacity and the border and halo set to white]({{ '/assets/images/tableau_intermediate_052.png' | relative_url }})

45. From the **Analysis** menu, select **Create Calculated Field…**, and name it **Location Detail**. Paste in the following formula:

    ```
    IF [Country_Region] = "US" THEN [Admin2]
    ELSEIF [Province_State] != "N/A" THEN [Province_State]
    ELSE [Country_Region]  
    END   
    //Used to determine the smallest level of detail for which there is information   
    //Note that Admin2 stores information on US counties
    ```

    !["Create Calculated Field" pop up window with the described formula added for "Location Detail"]({{ '/assets/images/tableau_intermediate_053.png' | relative_url }})
46. From Dimensions, drag **Location Detail** to **Detail** on the Marks card, so that data displayed on the map is shown at the smallest level of geography available (i.e., country, province/state or county).  
![Overview of Map worksheet with Location Detail added to the Detail marks card]({{ '/assets/images/tableau_intermediate_054a.png' | relative_url }})
47. Next, we will need to create a few calculated fields to use in our tooltip. From the **Analysis** menu, select **Create Calculated Field…**, and name it **Province State Label**. Paste in the following formula:  
    ```
    IF [Province_State] != "N/A" THEN [Province_State] 
    ELSE ""
    END  
    //Used in map tooltip to display a province/state name, if present
    ```
    !["Create Calculated Field" pop up window with the described formula added for "Province State Label"]({{ '/assets/images/tableau_intermediate_055.png' | relative_url }})

48. From the **Analysis** menu, select**Create Calculated Field…**, and name it **Admin2 Label (US)**. Paste the following formula:  
    ```
    IF [Country_Region] = "US"
    THEN " | County: " + [Admin2] 
    ELSE ""
    END
    //Used in the map tooltip to display a county name as well, if in the US
    ```  
!["Create Calculated Field" pop up window with the described formula added for "Admin2 Label (US)"]({{ '/assets/images/tableau_intermediate_056.png' | relative_url }})

49. From Dimensions, drag **Max Date**, **Country_Region**, **Admin 2 Label (US)**, and **Province State Label** on to **Tooltip** on the Marks card.  
![Marks card highlighting the added four variables to "Tooltip"]({{ '/assets/images/tableau_intermediate_057.png' | relative_url }})

50. Go to the Tooltip worksheet we created for the first visualization. **Right click** on the **Tooltip worksheet**’s tab at the bottom and select **Duplicate**. **Rename** the duplicate (called Tooltip (2) by default) **MapTooltip**.  
![Tooltip worksheet menu with the menu item "Duplicate" highlighted]({{ '/assets/images/tableau_intermediate_058a.png' | relative_url }})

51. In the **MapTooltip** worksheet, **right click** on **Tooltip (DAY(Date))** in the Filters shelf and select **Remove**.

52. From **Dimensions**, drag **Date is Max** on to the **Filters** shelf, select **True**, and click on OK.

53. Return to the **Map worksheet** and click on **Tooltip** on the Marks card. Delete all the text and insert the following attributes in order (on separate lines where noted):  

    ```
    <ATTR(Max Date)>  
    <ATTR(Country_Region)>  
    <ATTR(Province State Label)><ATTR(Admin2 Label (US))>
    ```

    Then, insert the **MapTooltip sheet** by clicking on **Insert**, then **Sheets**, then **MapTooltip**.  
    Within the new line for the MapTooltip sheet, **highlight** <**All fields**>(leaving the quotation marks unselected) and then insert **Location Detail**.

    The final text should look like this:

    ```
    <ATTR(Max Date)>  
    <ATTR(Country_Region)>  
    <ATTR(Province State Label)><ATTR(Admin2 Label (US))>  
    <Sheet name="MapTooltip" maxwidth="300" maxheight="300" filter="<Location Detail>">
    ```

    !["Edit Tooltip" pop up window with the described text inserted]({{ '/assets/images/tableau_intermediate_059.png' | relative_url }})

    Once you are done, click on OK. Hover over symbols on the map to see this tooltip in action.

    ![Hovering over Anoka County, Minnesota in the map worksheet, with the related tooltip displayed ]({{ '/assets/images/tableau_intermediate_060.png' | relative_url }})

54. Finally, let’s clean up the map. In the lower right corner, there is a gray warning listing the number of null values. Click on this box.  
![Map with the gray button "2 nulls" at the bottom highlighted]({{ '/assets/images/tableau_intermediate_061.png' | relative_url }})

    When it asks you what to do, click on **Filter data**.  
        ![Null value warning popup, with the item "Filter data" highlighted]({{ '/assets/images/tableau_intermediate_062.png' | relative_url }})
55. Also, let’s remove a few headers as we did with the first visualization. **Right click** on the **Case_Type header** at the top of the map, and select **Hide Field Labels for Columns**. **Right click** the **Confirmed header** on the top left of the map, and uncheck **Show Header**.  
![Final map displayed]({{ '/assets/images/tableau_intermediate_063.png' | relative_url }})

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization) \| **Tools:** [Tableau](https://mdlutoronto.github.io/tutorials-search/?tool=Tableau)