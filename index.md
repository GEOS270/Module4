---
layout: default
title: Spatial Data Models
has_children: True
nav_order: 1
---

# Spatial Data Models

Spatial Data has some unique properties which mean we need to implement specific strategies to work with it.  There are two key formats we work with in GIS for spatial data: **Raster** and **Vector**.  Both models can be used to represent most spatial phenomena; but they are not equally suited for all applications.

<img src="docs/content/images/03-vector-v-raster.jpg" width="900">


## Learning Outcomes

### Lecture

- Overview of different types of phenomena
- Overview of different types of data
- Differentiate between raster and vector data models.
- Learn how each model represents space and stores attributes.
- Learn which types of models are best suited for different applications.
- Overview of data resolution and how it relates to scale.

# How do we represent Geographic Information digitally?  


Now that we've covered how we project spatial data, we can learn how we actually represent that spatial data in a computer.  But first, lets take a step back and talk more broadly about data.

<details>
<summary>What are data?</summary>

<i>A collection of information (qualitative or quantiative) that describe a phenomena.</i>

</details>
<br>

<details>
<summary>What makes spatial data different from other types of data?</summary>

<i>The spatial coordinates must be treated differently (projected).  Further, spatial relationshps like proximity must be accounted for.</i>

</details>
<br>

<details>
<summary>Do similar issues arise with temporal data?</summary>

<i>Yes!  Time units must be treated differently and temporal relationshps like proximity are generally important.</i>

</details>
<br>




### Lab

* Experience a Typical GIS Workflow
* Explore Canadian Census Data
* Download Data from Google Earth Engine
* Work with Raster and Vector Data Layers
* Conduct Spatial Analysis
* Normalize and Classify Data
* Create Charts
