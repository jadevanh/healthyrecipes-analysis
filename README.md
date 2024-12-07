# **Recipe Analysis** 🍽️🧂
## Authors: Megan Bowen & Jade VanHaitsma
Contact: jadev@umich.edu & megbowen@umich.edu
----
# Introduction


Online recipe websites have now replaced recipe books as the mainstream (and free!) way to find cooking inspiration for one's next meal. The data set we will be working with is a compilation of recipes and reviews from a popular website, Food.com. This website provides recipes for a variety of cuisines, dating back 15 years (2008), and stopping in 2018. The data sets had 10 years worth of recipe ideas where we would like to investigate what authors should be considered 'healthy' in their recipe.




The central question we would like to investigate is, **What recipes tend to be healthier?** We would like to use data analysis techniques to classify whether or not a recipe would be tagged as 'healthy' based on the information in the data.




## Introduction to the dataset


The original data set consisted of two data sets which we have merged by the recipe `id` column. This data set has 234,429 rows and 17 columns. We have chosen the following 16 columns to be included in our DataFrame for analysis. 10 of such columns were not in the original data set, but a subset of the original data cleaned and created from extracting data. 
### Column Name and Descriptions:


- `id`: The 'id' column uniquely identifies the recipes on Food.com, used as the index column for our purposes.
- `submitted` : The 'submitted' column contains the date that the recipe was published by the creator.
- `minutes` : The 'minutes' column represents the number of minutes that it takes for a recipe to be made from start to end.
- `n_steps` : The 'n_steps' column is a record of the number of steps each recipe has, created by the author.
- `n_ingredients`: The 'n_steps' column is a record of the number of ingredients each recipe has.
- `n_rating` : The 'n_rating' column gives a 1-5 rating from users who have attempted to create a particular recipe. Recipes with a rating of '0' were not given a rating by the user who reviewed them.
- `avg_rating` : The 'avg_rating' column contains the mean rating for each particular recipe based on the reviews and ratings per recipe id. 
- `n_tags` : The 'n_tags' column is a record of the number of tags each recipe has that was put on the recipe by the author.
- `calories`: Subset of the original 'nutrition' column, the 'calories' column records the self-reported number of calories for the recipe.
- `total fat`: Subset of the original 'nutrition' column, the 'total fat' column records the PDV of total fat for the recipe.
- `sugar`: Subset of the original 'nutrition' column, the 'sugar' column records the PDV of sugar for the recipe.
- `sodium`: Subset of the original 'nutrition' column, the 'sodium' column records the PDV of sodium for the recipe.
- `saturated fat`: Subset of the original 'nutrition' column, the 'saturated fat' column records the PDV of saturated fat for the recipe.
- `carbohydrates`: Subset of the original 'nutrition' column, the 'carbohydrates' column records the PDV of carbohydrates for the recipe.
- `year` : The 'year' column is a subset of the 'submitted’ column. We extracted the year in order to get data about recipes on a per year basis.
- `healthy_tag` : The 'healthy_tag' column indicates '1' if there was a tag of "healthy" on the recipe or '0' for no tag.


### Below are the first 5 rows of our cleaned DataFrame:




| name                                  | submitted   |   minutes |   n_steps | ingredients                                                                                                                            |   n_ingredients |   n_rating |   avg_rating |   calories |   total fat |   sugar |   sodium |   protein |   saturated fat |   carbohydrates |   year |   healthy_tag |
|:--------------------------------------|:------------|----------:|----------:|:---------------------------------------------------------------------------------------------------------------------------------------|----------------:|-----------:|-------------:|-----------:|------------:|--------:|---------:|----------:|----------------:|----------------:|-------:|--------------:|
| impossible macaroni and cheese pie    | 2008-01-01  |        50 |        11 | ['cheddar cheese', 'macaroni', 'milk', 'eggs', 'bisquick', 'salt', 'red pepper sauce']                                                 |               7 |        nan |            3 |      386.1 |          34 |       7 |       24 |        41 |              62 |               8 |   2008 |             0 |
| impossible rhubarb pie                | 2008-01-01  |        55 |         6 | ['rhubarb', 'eggs', 'bisquick', 'butter', 'salt', 'sugar', 'vanilla', 'milk']                                                          |               8 |        nan |            3 |      377.1 |          18 |     208 |       13 |        13 |              30 |              20 |   2008 |             1 |
| impossible seafood pie                | 2008-01-01  |        45 |         7 | ['frozen crabmeat', 'sharp cheddar cheese', 'cream cheese', 'onion', 'milk', 'bisquick', 'eggs', 'salt', 'nutmeg']                     |               9 |        nan |            3 |      326.6 |          30 |      12 |       27 |        37 |              51 |               5 |   2008 |             0 |
| paula deen s caramel apple cheesecake | 2008-01-01  |        45 |        11 | ['apple pie filling', 'graham cracker crust', 'cream cheese', 'sugar', 'vanilla', 'eggs', 'caramel topping', 'pecan halves', 'pecans'] |               9 |        nan |            5 |      577.7 |          53 |     149 |       19 |        14 |              67 |              21 |   2008 |             0 |
| midori poached pears                  | 2008-01-01  |        25 |         8 | ['midori melon liqueur', 'water', 'caster sugar', 'cinnamon stick', 'vanilla pod', 'lemon rind', 'orange rind', 'pear', 'mint']        |               9 |        nan |            5 |      386.9 |           0 |     347 |        0 |         1 |               0 |              33 |   2008 |             0 |


---
# Data Cleaning and Exploratory Data Analysis




### Data Cleaning




---
To start the cleaning process, we merged the two data sets, 'interactions' and 'recipes' on the `id` column which links the reviews and ratings of recipes with the information about the recipe from the recipe dataset.


To follow, we have taken all recipes with rating '0', denoting that there was no rating for that particular interaction, and replaced them with nAn values.
Below are the distribution of recipes before and after the drop.


<iframe
 src="assets/ratingRaw.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>


<iframe
 src="assets/ratingClean.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>


After this, we chose to create the column 'avg_rating` which creates a column for the mean rating of each recipe of all the ratings the recipe has received.
This allows us to do calculations on the recipes using one metric as the rating. 


Then, we have decided to take the relevant columns from the dataset, dropping the following columns: `contributor_id`, `steps`, `description`, `user_id`, and `recipe_id`. We chose to save the irrelevant columns and kept the columns, `name`,`id`,`minutes`,`submitted`,`tags`,`nutrition`,`n_steps`,`n_ingredients`,`user_id`,`rating`, and `avg_rating`. These columns will aid in the data analysis.






--
## Univariate Analysis
For our univariate analysis, we explored the distributions of nutritional information that is often related to the health of a recipe.
Here we have histograms describing the distribution of total fats and sugars for all recipes.
For many of our variables there are outliers, skewing the dating to be a wide range. We have chosen to crop these graphs in order to get a closer image of the distribution of the graph.
We wanted the distribution of total fats, capping the x-axis at 200 (PDV) because this would mean the recipe has 200% more total than the typical daily intake. Values greater than this seemed not to make sense for the variable. We have attached both graphs for reference.


<iframe
 src="assets/total_fatAll.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>


<iframe
 src="assets/total_fatCrop.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>
We also wanted to look at the distribution of sugars. For the same reason as total fats, we have attached the full distribution and a cut-off range of [0,200] for the sugar distribution.
<iframe
 src="assets/sugarDist.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>
<iframe
 src="assets/sugarCropped.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>


Both plots are heavily right-skewed. We also see the medians of these distributions, as indicated by the red dotted line, and middle of the boxplot. The median for saturated fats is 21.0 PDV, and for sugars it is 23.0. This indicates that many of the listed recipes fall within typical daily value ranges for sugar and saturated fat composition.






---
## Bivariate Analysis
This is a plot that describes the distributions of Calories in recipes that are tagged "Unhealthy" (red) vs "Healthy" (green).
From this plot, we see the trend that the distribution of unhealthy recipes have a higher number of calories, while the healthy recipes tend to have fewer calories.


<iframe
 src="assets/colorCalorieCrop.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>


Note that due to a high number of outliers, we have cropped the range of the plot to be between 0 and 2000 calories, as that is typical daily intake.
<iframe
 src="assets/colorCalorieFull.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>


We were also interested in the scatter plot between calories and carbohydrates. This gives us insight into how the two nutrients are related, and if there is any pattern when looking at the dots between healthy and unhealthy recipes based on these variables.
Looking at the plot, we noticed that there is a slight upward trend between the two variables, and many of the recipes with lower calories are seen as healthy, over the recipes that have high calories.
<iframe
 src="assets/colorCalorieScatterp.html"
 width="800"
 height="600"
 frameborder="0"
></iframe>




---
## Interesting Aggregates
Here we've aggregated recipes based on if they've been tagged 'healthy' or not, and are looking at the median nutritional information for each tag category.
We can see that recipes tagged 'healthy' have lower median calories, fats, sodium, and protein than those tagged 'unhealthy'.


|   `year` |   `healthy_tag` |
|-------:|--------------:|
|   2008 |      0.190893 |
|   2009 |      0.188007 |
|   2010 |      0.19753  |
|   2011 |      0.212201 |
|   2012 |      0.18315  |
|   2013 |      0.183017 |
|   2014 |      0.180172 |
|   2015 |      0.124183 |
|   2016 |      0.132353 |
|   2017 |      0.128472 |
|   2018 |      0.121693 |


---
# Framing a Prediction Problem
Our prediction problem is a binary classification problem. We are hoping to classify recipes as either 'healthy' or 'not healthy' based on their nutritional content and ingredients -- the response variable is `healthy_tag`. 
We chose this response variable because given the detailed information on the nutrients and ingredients of these recipes, we felt we could make insightful predictions about general recipe health based on that. 
When putting together a recipe, the user will have full information about the ingredients and thus nutritional content of the recipe, so it is fair game using predictors from these categories as a basis for whether it would be considered a healthy recipe.


We have decided to use accuracy as our performance metric because we consider true positives and true negatives equally for our predictions, and do not require the more in-depth analysis offered by F1. While we recognize that F1 often provides a more comprehensive performance metric, especially for imbalanced data, we ultimately decided accuracy was the metric we were able to improve our model upon the most and proceeded with that.




---
# Baseline Model
For our baseline model, we used Logistic Regression. Our features include `calories` and `protein`, both of which are quantitative.


Our baseline model's accuracy is: 0.8065


We do not believe our current model is the best it can be, considering there is room to improve on our performance metric, and we are only using two features (both of which are from nutritional content) as our predictors. Because of this, we also do not think our model would be super generalizable to unseen data.


Our aim is to incorporate more features that could be indicative of the health of a recipe, such as specific ingredients, as well as other nutritional information so that our model can make more informed classifications.


---
# Final Model
In our final model, we included the following nutritional features: `calories`, `total fat`, `sugar`, `sodium`, `protein`, `saturated fat`, `carbohydrates`. We wanted to use all nutritional information available to inform our model, seeing as just calories and protein do not give the full picture.


Lastly, we engineered 4 one-hot-encoded categorical features derived from `ingredients` into this model:
- `low_ingredients`
- `skim_ingredients`
- `reduced_ingredients`
- `organic_ingredients`
These features have a value of 1 if a recipe contains any ingredient that is considered to be low/reduced content, skim, or organic. We added this because aside from strictly numerical nutrition information, one can also determine how healthy a recipe is based on the type of ingredients used.


After exploring different versions of logistic regression models and decision trees, we ultimately used a Decision Tree for our final model as it performed better than our regression models.


We tuned the hyperparameters using `GridSearchCV` and got the following optimal values:
- `max_depth` = 6
- `min_samples_split` = 7


Our final model yielded a test accuracy of: 0.8135, which is a slight improvement from our baseline model. We believe incorporating additional nutritional content information as well as factoring in specific ingredient characteristics boosted out model performance by providing more specific insight to each recipe.


We have included visualization of our confusion matrix describing this model’s performance:


It should be noted that our model’s key flaw is that due to the skewness of the classes, we predict many False Negatives. That is, we predict recipes to be ‘unhealthy’ when they are in fact tagged ‘healthy’. This is also a likely cause for why our accuracy did not seem to improve by much even after running hyper parameters and adding relevant features.


One challenge we’ve come to realize is that a recipe being tagged as ‘healthy’ is completely up to the user who submits the recipe. A recipe could be nutritionally healthy, but if a user doesn’t ultimately tag it as ‘healthy,’ our model will fall short. The same goes for recipes that may be nutritionally unhealthy where the user tagged it as ‘healthy.’ Should we continue this analysis further, we would definitely want to refine our model to account for this subjectivity.


---
