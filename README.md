# **Recipe Analysis** 🍽️🧂
## Authors: Megan Bowen & Jade VanHaitsma
Contact: jadev@umich.edu & 
---
# Introduction

Online recipe websites have now replaced recipe books as the mainstream (and free!) way to find cooking inpsiration for one's next meal. The data set we will be working with is a compiliation of recipies and reviews from a popular website, Food.com. This website provides recipies for a variety of cuisines, and recipies dating back 15 years (2008), and stopping in 2018. 


The central question we would like to investigate is **What do recipies tend to be healthier?** We would like to use data analysis techniques to predict the 


## Introduction to the dataset

The original data set consisted of two data sets which we had merged by their `id` column. This data set has 234,429 rows and 17 columns. We have chosen the following 16 columns to be included in our DataFrame for analysis. 10 of such columns were not in the original data set, but a subset of the original data cleaned and created from  separated. 

### Name and Descriptions of the Columns used: 

- `id`: The id column uniquely identifies the recipes on Food.com. 
- `submitted` : The submitted column contains the date that the recipe was published by the creator. 
- `minutes` : The minutes column 
- `n_steps`
- `n_ingredients`
- `n_rating`
- `avg_rating`
- `n_tags`
- `calories`
- `total fat`
- `sugar`
- `sodium`
- `saturated fat`
- `carbohydrates`
- `year`
- `healthy_tag`

---
# Data Cleaning and Exploratory Data Analysis

---
## Bivariate Plots

<iframe
  src="assets/bivar_box.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
This is a plot that describles the distrivbutions of Calories in recipies that are tagged "Unhealthly" (red) vs "Healthy" (green). 
---

# Framing a Prediction Problem


---
# Baseline Model



---
# Final Model




---
### December 5, 2024
