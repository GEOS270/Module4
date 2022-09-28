---
layout: default
title: Module Quiz
nav_order: 3
---

# Module 4 Quiz

You can submit your answers to these questions via the Module 4 Quiz on Canvas.  Questions are listed here with hyperlinks to the relevant section of the lab if you need help finding answers.

## Rubric

Written answers and maps will be evaluated using the rubric below and your TA will provide brief comments where applicable.

* If you need more feedback you can follow up with your TA via email or in lab.
* Categories are just general guides
    * Your TA may assign scores between these levels


|      Category      |                   Written Answers                |                 Map/Chart Submissions                             |Score|
|--------------------|--------------------------------------------------|-------------------------------------------------------------------|-----|
|Missing             |N/A                                               |N/A                                                                |0%   |
|Insufficient        |Missing major key points or serious logical flaws |Serious errors in analysis, missing data, or major stylistic issues|25%  |
|Below Expectations  |Missing a few key points or minor logical flaws   |Minor errors in analysis or multiple stylistic issues              |50%  |
|Meets Expectations  |Hits key points and mostly well constructed       |Error free analysis, minor stylistic issue                         |75%  |
|Exceeds Expectations|Clearly thought out, concise, and astute          |Error free analysis and clean, aesthetically pleasing map          |100% |

### Written Answers 

Written answers can be brief but they should adequately answer the question.

* Bullet point format is okay **unless otherwise specified**

### File Submissions

Map/charts/figures will be evaluated for completeness and aesthetics.

* Files should be saved as using the file type specified (.pdf, .png, etc.)
    * Make sure to double check the file before uploading!

---

# Quiz Questions

Unless otherwise specified, numeric answers have a margin of error of 0.01, so give all responses to at least the hundredths place.

[**1**](Application_Part2.md#monitoring-vegetation-with-satelites)
What is NDVI and what is it used for and how is it calculated? What do high and low NDVI values represent respectively? What patterns do you see in the NDVI data for the metro Vancouver area?


[**2**](Application_Part3.md#a-note-on-linear-regression)
Looking at the **VanDA_2016** layer, for every $100 increase in income at the DA level, how much does rental price increase?

[**3**](Application_Part3.md#a-note-on-linear-regression)
Looking at the **VanDA_2016** layer, what is the R2 score for this model?

[**4**](Application_Part3.md#comparing-cts-to-das)
What is the median population of a Census Tract (VanCMA_CT_2016) in Metro Vancouver?

[**5**](Application_Part3.md#comparing-cts-to-das)
Which Census Unit displays a more direct relationship between Income and Housing?  What evidence supports this conclusion? 

[**6**](Application_Part3.md#use-the-natural-breaks-classification)
What value does the Natural Breaks method determine should denotes the lower bound of the "Green Vegetation" class? **Hint**:  Look at the Start/End values when applying the natural breaks classification.

[**7**](Application_Part3.md#change-the-base-map)
Looking at the satellite image, how well do you think the natural breaks classification method did at distinguishing areas of green vegetation from residential areas and urban/water areas?

[**8**](Application_Part4.md#zonal-statistics-as-table)
What is the highest MEAN NDVI value for any CT in the Metro Vancouver CMA? *Hint* Double clicking on MEAN NDVI  in the attribute table allows you to sort in ascending/descending order.  (Round your answer to the nearest  hundredths place)

[**9**](Application_Part4.md#raster-to-polygon-conversion-and-intersection)
There are 478 polygons (Census Tracts) in the VanCMA_CT_2016 layer.  After intersecting VanCMA_CT_2016 with the output for the raster to polygon conversion step, many more polygons are created within the area covered by teh VanCMA_CT_2016.  How many polygons are the output from the intersect (VanCMA_CT_2016_Intersect in the video, your specific name may be different)?

[**10**](Application_Part4.md#data-normalization)
What is the mean PCT_Green_Space value per Census Tract?  (Round your answer to the nearest  hundredths place)

[**11**](Application_Part4.md#data-normalization)
Why did we calculate the PCT_Green_Space field?


[**12**](Application_Part4.md#inspect-and-compare-the-outputs)
Describe the relationship between the **Mean_NDVI** value per CT and and the **PCT_Green_Space** per CT.  Are they telling us the same thing?  How Strongly are they related?

[**13**](Application_Part4.md#inspect-and-compare-the-outputs)
Are either **Mean_NDVI** or **PCT_Green_Space** strongly linked to housing cost? What evidence supports this conclusion? How might we refine our analysis using Ordinary Least Squares Regression? Suggest a two other factors you think we should include in our analysis besides **Mean_NDVI** or **PCT_Green_Space**? Are there any other more general improvements you think we could make to this analysis beyond just adding more variables to our model?

[**14**](Application_Part5.md)
Export your Layout as a .pdf and upload it to Canvas.


