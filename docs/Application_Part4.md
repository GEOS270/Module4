---
layout: default
title: Spatial Analysis
parent: Lab Assignment
nav_order: 4
---


<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>
---


# Spatial Analysis
{: .no_toc }

A key aspect of GIS is overlaying multiple data layers to generate new information.  There are typically multiple solutions to a given problem in GIS.  Here, we are going to look at two methods for combining a raster layer and a vector layer:

1) **Zonal Statistics**:  This method is faster, but can be applied in a more limited number of circumstances.  

2) **Raster to Polygon Conversion**: This method involves converting between data types and requires more a few steps, but it is more flexible.


# Clean Up Your Workspace Selection

From here on out, we are only goin to be working with the VanCMA_CT_2016 so you can remove the Van_DA_2016 layer.

# Method 1

## Zonal Statistics as Table

We are going to overlay the vector data on the raster data to measure the mean NDVI value for each census tract using the **Zonal Statistics as Table** tool.  Then we will **Join** the resulting output table to add the NDVI values by CT to the layer.  A **join** is a way to add tables to a layer based on a specific column.  You can reference the video below for guidance.

**1**{: .label .label-red } Find the Zonal Statistics as Table tool in the Geoprocessing pane, choose **VanCMA_CT_2016** as the feature zone data, and **Van_Greenest_ProjectRaster** as the Input value raster. 
* Set CTUID as the Zone Field
* Select All statistics types

**2**{: .label .label-red } Right click on VanCMA_CT_2016 and choose Joins and Relates > Add Join.  
* Set CTUID as the Input Join Field
* Choose the Zonal Statistics table as your input. *(the name should look something like ZonalST_VanCMA_1)*
* Make sure CTUID is selected as the Join Table Field as well

**3**{: .label .label-red } Inspect the Join
* Open the attribute table and note the new columns at the end

<iframe width="560" height="315" src="https://www.youtube.com/embed/DBFmPbMekHE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Method 2

## Raster to Polygon Conversion and Intersection

We are going to convert the classified raster layer to a vector layer.  Then we can overlay the resulting vector layer with the VanCMA_CT_2016 layer using an intersect which will let us calculate the total green vegetation area per CT in the next step.  You can reference the video below for guidance.

**1**{: .label .label-green } Find the **Raster to Polygon** tool in the geoprocessing pane.
* Set the Classified NDVI image as the Input raster
* Choose Value as the Field

**2**{: .label .label-green } Find the [Intersect tool](https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/intersect.htm) in the geoprocessing pane.  It will combine the feature classes where they overlap and exclude all other areas.  We'll talk a lot more about this tool.

* Set Van_DA_2016 and the output from the raster to polygon conversion as the inputs.  Then click run.
* Change the symbology and open the attribute table to confirm the results look like what we'd expect.

<iframe width="560" height="315" src="https://www.youtube.com/embed/nFynnK6SEnI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Calculate the Green Vegetation Area and Dissolve by CT

Now we are going to calculate the total green vegetation area by CT, and toss out a bunch of the unnecessary data.  You can reference the video below for guidance.

**1**{: .label .label-blue } Add a new field to the VanCMA_CT_2016_Intersect layer called "Green_Veg_Area" so we
* Name the field Green_Veg_Area
* Make sure the data type is **Double**.

**2**{: .label .label-blue } Choose Select by Attribute and set your query to: Where gridcode is equal to 3.

**3**{: .label .label-blue } Right click on Green Veg Area and choose **Calculate Field**.  This allows us to define a function and apply it to the table.
* Set the expression to: Green_Veg_Area = Shape_Area 
  * *Note* you only need to complete the right side of the equation 
  * This will simply copy the shape area for the green vegetation areas, we will work with a more complex expression on the next page.

**4**{: .label .label-blue } We want to assign all other rows a 0.  We can quickly invert our selection with the **Switch** button.
* Calculate the field again, but with Green_Veg_Area = 0
  * We have selected gridcode 1 & 2 (Not vegetation) so they all get zeros.

<iframe width="560" height="315" src="https://www.youtube.com/embed/dUd8UbF2dQI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Data Normalization

One last thing step!  We need to account for a confounding factor.  The CTs are different sizes.  To better compare the CTs (which are vastly different sizes), lets Normalize our results by the total area of each CT!  **Normalizing**, sometimes also referred to as standardizing, is the process of dividing one variable by another variable to account for their relationship.  It can help us identify patterns that might be masked by a confounding variable.

**1**{: .label .label-yellow } Add a new field called "PCT_Green_Space".  
* Make sure you set the data type to **Double**

**2**{: .label .label-yellow } Calculate the field using the following equation:
* PCT_Green_Space = SUM_Green_Veg_Area/Shape_Area
  * *Note* you only need to complete the right side of the equation 

**3**{: .label .label-yellow } Right click on PCT_Green_Space and select "Statistics"
* This will bring up some descriptive statistics for this field.



# Inspect and Compare the Outputs

Lets see how the two methods compare?

**1**{: .label .label-green } Open the Attribute Table of VanCMA_CT_NDVI_Veg.  Double click on **Mean_NDVI** to sort by that column in ascending/descending order.  Take note of the CTUIDs for of the CTs with the highest values.  Now look at  **SUM_Green_Veg_Area** and **PCT_Green_Space**.  Do they all match up, or are there some differences?

**2**{: .label .label-green } Create a new Scatter plot. Set the X-axis to **Mean_NDVI** and the Y-axis to **SUM_Green_Veg_Area**.  Look at the R2 score and think about the relationship between these variables.  Now change the Y-axis to **PCT_Green_Space** and not how the relationship changes.


**3**{: .label .label-green } Change X-axis to **Mean_NDVI** the Y-axis to **Housing**.  Make sure to **Exclude the zeros** using the same procedure as earlier then look at the resulting relationship.  Is the **Mean_NDVI** a good predictor of housing cost?  Try changing the X-axis to **PCT_Green_Space** to see if it gives a better result?







