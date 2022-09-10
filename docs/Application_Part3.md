---
layout: default
title: Data Exploration
parent: Lab Assignment
nav_order: 3
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

# Visualizing Vector Data & Plotting Relationships
These Census data are in **Vector** format.  A key advantage of Vector Data is that we can have multiple attributes associated with each entity (point/line/polygon).  Here, we are interested in three variables: Population (total residents), Housing (monthly rent), and Income (annual total).  

**1**{: .label .label-red } Symbolize your census data by population.
* Set the Field to Population
* Change the symbology for Van_DA_2016 to Graduated Colors
* Explore how the different classification schemes influence the way the classified layer looks on the map

**2**{: .label .label-red } Make a Histogram of Population.
* Set the number to population
* Make sure the mean, median, and standard deviations are all shown on the Histogram.

**3**{: .label .label-red } Create a chart income vs. housing.
* Right click Van_DA_2016 and click Create Chart > Scatter Plot.
* In the chart properties tab set:
  * **X-axis**: Income
  * **Y-axis**: Housing
* Make sure "Show linear trend" is checked to display a regression line on your chart.


**4**{: .label .label-red } Note the zero values on the X & Y Axes.  Stats Canada "suppresses" data when they don't get enough responses to a census question.  No house in Vancouver is worth $0.  We need to exclude the zeros so they don't skew our results
* In the Map tab, click **Select by Attribute**, select for "Housing" greater than 0 **And** "Income" greater than 0.
  * Select by Attribute allows us to select rows/objects with a certain attribute.
  * It relies on something called a Structured Query Language (SQL).
  * We are selecting all rows "Where" our conditions are met.
    * You can use the **And**/**Or** commands to combine querries.
    * **And**: Selects whre **All** statements are true
    * **Or**: Selects whre **Any** statements are true

<iframe width="560" height="315" src="https://www.youtube.com/embed/cWr6B9Pp4Dc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## A Note on Linear Regression.
A regression line is also know as a "line of best fit".  [Linear regression](https://en.wikipedia.org/wiki/Linear_regression#Introduction) assumes the relationship between an X variable (eg. Income) and a Y variable (eg. Housing) follows a linear relationship (eg. Y=MX + B) where M is the slope and B is the intercept. 
* Any deviations from this linear relationship are "errors".  That is, all the other variability that cannot be explained by the model.  Rental cost is impacted by many factors (eg. scarcity) that aren't as easy to capture with census data alone.
* In the example below for Van_DA_2016 (before excluding zeros), M = 0.0123 and b = 660.1, which means at $0 income, rent is $660.1.  And for every $100 increase in income, rent goes up $1.23.

<img src="content/images/Statistics.png" alt="hi" class="inline"/>


The <b>R<sup>2</sup></b> score, is known as the [coefficient of determination](https://en.wikipedia.org/wiki/Coefficient_of_determination).  It is a measure of how well a model fits the data.  It ranges from 0 to 1, with 0 representing "no fit" and 1 representing a "perfect fit".

* This table shows how we assess the strength of a relationships indicated by the R<sup>2</sup> statistics.  In the example above, there is no strong relationship.

|R<sup>2</sup>| Relationship|
|-------------|-------------|
|<0.3         | Very Weak   |
|0.3 - 0.5    | Weak        |
|0.5 - 0.7    | Moderate    |
|>0.7         | Strong      |

## Comparing CTs to DAs

Repeat the steps above for the VanCMA_CT_2016 layer.  **Don't forget** to exclude the zeros on your scatter plot. Note there are fewer zeros overall. Think about why that might be.  **Hint** look at the population of CTs compared to DAs

# Visualizing and Classifying Raster Data
These NDVI data are in **Raster** format. An important caveat of raster data layers is they can only have **one** value per cell.  However, they are useful because they allow us to represent continuous phenomena (i.e. vegetation health) as a simple image.

## Create a Histogram
To get a feel for the distribution of NDVI values in the dataset, we're going to plot them in a histogram to aid our visual inspection of the NDVI data.

**1**{: .label .label-blue } Create a chart showing the count of cells by NDVI values.
* A histogram represents a distribution by grouping the data into bins (ranges), and plotting the count of values (eg. raster cells) for by bin.
  * Change the bin number to see how changing the size of the bins, impacts how you perceive the data.  Try 10, then try 50.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9bjZrh6tQFk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Use The Natural Breaks Classification

**2**{: .label .label-blue } Search for the Reclassify tool in the geoprocessing pane.  Use the projected NDVI layer as the input.  
  
* Click classify to set the classification scheme.  Set the method to **Natural Breaks** and the number of classes to 3.
  * We talked about the Natural Breaks Classification in [Module 3](https://geos270.github.io/Module3/docs/Content_Part2.html).
  * It is designed to automatically find an "optimal" fit to a dataset. 
* We can use it to group the NDVI values into three classes:
  * 1: Water/Urban (lowest values)
  * 2: Medium Density Residential (middle values)
  * 3: Green Vegetation (highest values)

# Change the Base Map 

To help inspect the NDVI classification, we can change the base map and look at a satellite image layer.

* On the Map tab click "Basemap" and choose Imagery
* Toggle the NDVI Layer and classified image on and off to see how the NDVI values correspond to green vegetation on the visible imagery base map layer. 

<div style="overflow: hidden;
  padding-top: 56.25%;
  position: relative">
  <iframe src="content/videos/BaseMap.mp4" title="Processes" scrolling="no" frameborder="0"
    style="border: 0;
   height: 100%;
   left: 0;
   position: absolute;
   top: 0;
   width: 100%;">
   <p>Your browser does not support iframes.</p>
 </iframe>
</div>
<a href="content/videos/BaseMap.mp4" target="_blank">View Image in New Tab</a>
