# **Recipe Analysis** 🍽️🧂
## Authors: Megan Bowen & Jade VanHaitsma
Contact: jadev@umich.edu & 
---
# Introduction

Online recipe websites have now replaced recipe books as the mainstream (and free!) way to find cooking inpsiration for one's next meal. The data set we will be working with is a compiliation of recipies and reviews from a popular website, Food.com. This website provides recipies for a variety of cuisines, and recipies dating back 15 years (2008), and stopping in 2018. 


The central question we would like to investigate is **What do recipies tend to be healthier?** We would like to use data analysis techniques to predict the 


## Introduction to the dataset

The original data set consisted of two data sets which we have merged by the recipe `id` column. This data set has 234,429 rows and 17 columns. We have chosen the following 16 columns to be included in our DataFrame for analysis. 10 of such columns were not in the original data set, but a subset of the original data cleaned and created from  separated. 
### Column Name and Descriptions: 

- `id`: The 'id' column uniquely identifies the recipes on Food.com, used as the index column for our purposes. 
- `submitted` : The 'submitted' column contains the date that the recipe was published by the creator. 
- `minutes` : The 'minutes' column represents the number of minutes that it takes for a recipe to be made from start to end.
- `n_steps` : The 'n_steps' column is a record of the number of steps each recipes has, created by the author.
- `n_ingredients`: The 'n_steps' column is a record of the number of ingredients each recipes has.
- `n_rating` : The 'n_rating' column gives a 1-5 rating from users who have attempted to create a particular recipe. Recipes with a rating of '0' were not given a rating by the user who reviewed them.
- `avg_rating` : The 'avg_rating' column contains the mean rating for each particular recipe based on the reviews and ratings per recipe id.  
- `n_tags` : The 'n_tags' column is a record of the number of tags each recipes has that was put on the recipe by the author. 
- `calories`: Subset of the original 'nutrition' column, the 'calories' column records the self repoted number of calories for the recipe.
- `total fat`: Subset of the original 'nutrition' column, the 'total fat' column records the PDV of total fat for the recipe.
- `sugar`: Subset of the original 'nutrition' column, the 'sugar' column records the PDV of sugar for the recipe.
- `sodium`: Subset of the original 'nutrition' column, the 'sodium' column records the PDV of sodium for the recipe.
- `saturated fat`: Subset of the original 'nutrition' column, the 'saturated fat' column records the **author-inputed** PDV of saturated fat for the recipe.
- `carbohydrates`: Subset of the original 'nutrition' column, the 'carbohydrates' column records the PDV of carbohydrates for the recipe. 
- `year` : The 'year' column is a subset of the 'submitted'column. We extracted the year in order to get data about recipes on a per year basis. 
- `healthy_tag` : The 'healthy_tag' column indicates '1' if there was a tag of "healthy" on the recipe or '0' for no tag. 

---
# Data Cleaning and Exploratory Data Analysis

--- 
- cutting off the number due to physical or real work significance -- we will put both of them

- show remove at 0 and show nan for ratings

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
