---
layout: post
title: News Clustering
---

Can we predict the category of a news article by its headline?

![Image test]({{ site.url }}/images/breaking_news1.png)



### Project objective
There is no simple rule for determining the edibility of a mushroom.
The objective of this project is to build a classification model to predict
whether a mushroom is edible or poisonous.



### Dataset

This dataset includes descriptions of hypothetical samples corresponding to 23 species of gilled mushrooms in the Agaricus and Lepiota Family Mushroom drawn from The Audubon Society Field Guide to North American Mushrooms (1981). Each species is identified as edible or poisonous.

Downloaded from: [Here]({{https://www.kaggle.com/uciml/mushroom-classification}}).

Time period: Donated to UCI ML 27 April 1987

Donated by: Jeff Schlimmer

License: CC0: Public Domain

##### Dataset Attribute Information:
* cap-shape: bell, conical, convex, flat, knobbed, sunken.
* cap-surface: fibrous, grooves, scaly, smooth.
* cap-color: brown, buff, cinnamon, gray, green, pink, purple, red, white, yellow.
* bruises: bruises, no bruises.
* odor: almond, anise, creosote, fishy, foul, musty, none, pungent, spicy.
* gill-attachment: attached, descending, free, notched.
* gill-spacing: close, crowded, distant.
* gill-size: broad, narrow.
* gill-color: black, brown, buff, chocolate, gray, green, orange, pink, purple, red, white, yellow.
* stalk-shape: enlarging, tapering.
* stalk-root: bulbous, club, cup, equal, rhizomorphs, rooted, missing
* stalk-surface-above-ring: fibrous, scaly, silky, smooth
* stalk-surface-below-ring: fibrous, scaly, silky, smooth
* stalk-color-above-ring: brown, buff, cinnamon, gray, orange, pink, red, white, yellow.
* stalk-color-below-ring: brown, buff, cinnamon, gray, orange, pink, red, white, yellow.
* veil-type: partial,universal.
* veil-color: brown, orange, white, yellow.
* ring-number: none, one, two.
* ring-type: cobwebby, evanescent, flaring, large, none, pendant, sheathing, zone.
* spore-print-color: black, brown, buff, chocolate, green, orange, purple, white, yellow.
* population: abundant ,clustered ,numerous, scattered, several, solitary.
* habitat: grasses, leaves ,meadows, paths, urban, waste, woods.

**Example of different mushroom cap-shape**

![Image test]({{ site.url }}/images/cap_shape.jpeg)



### Data cleaning
The dataset was mostly clean with no null-values. However, after exploring the dataset I decided to:

1. Drop the veil-type column as all of the rows in that column had only one value and that will not add to the model learning process.
2. Plot the stalk-root column distribution with each feature once with the missing value and once without.
![Image test]({{ site.url }}/images/stalk.png)

as shown above, the missing value in stalk-root column represent a lot of the datapoint thus, I will keep it in the dataset as removing them may effect the learning of the model.



### Exploratory Data Analysis
After cleaning the data, I visualized the distribution of different features using matplotlib and seaborn.

The graph below, shows the class distribution.

![Image test]({{ site.url }}/images/mushroom_class.png)

The graph below, shows the mushroom odor distribution.

![Image test]({{ site.url }}/images/odor_dist.png)


The graph below, shows the mushroom odor distribution compared to the class.

![Image test]({{ site.url }}/images/odor_to_class_dist.png)


The graph below, shows the gill-size categories percentage.

![Image test]({{ site.url }}/images/gill_size.png)




### Model testing
I choose to go with logistic regression which is a popular classification technique
to predict binomial outcomes (y = 0 or 1). Logistic regression predicts categorical outcomes.

1. I started with splitting my data and pre-processing my train set.  

* Reseting the data index
* Checking for any collinearity between the features.
![Image test]({{ site.url }}/images/mushroom_heatmap.png)
as you can see from the heatmap there is a high correlation between the veil-color and gill-attachment.


2. Transformed my feature through one-hot-encoding and then transformed it again with dummy variables.

3. Cross-validation to have an idea about the test data score.

4. I created a baseline model. I fitted all my independent variables into the model, these the results I got.

![Image test]({{ site.url }}/images/log.png)

as you can see the model accuracy was very high. In order to make sure my model was not overfitting I decided to perform regularization.

5. Regularized the model with a 0.9 lasso ratio. The regularized model preformed better than the baseline model.


6. Simplifying the model, since my model was preforming well I decided to simplify it by reducing the number of features.

I went through the model's coefficient and kept only the the top 5 features. These were the features that influenced the model the most.

![Image test]({{ site.url }}/images/coef.png)

as you can see most of the feature were from the odor category.

7. Final model

![Image test]({{ site.url }}/images/final_score.png)




### Model Evaluation


#### Confusion Metric


![Image test]({{ site.url }}/images/confusion_matrix.png)

from the classification above we can see that the model was performing well. I was mostly concerned about the false negative section.
This model have a lower number of false negative than false positive which is what I were hoping for.


#### ROC

![Image test]({{ site.url }}/images/roc.png)

The graph above shows how good the model is preforming regarding the true and false positive.
Area under the curve =  0.9854579048208978
Model Performance: Excellent model


### Tools used for this project

#### Python
Pandas and numpy to clean and preprocess, matplotlib and seaborn to visualize it, and sklearn for modeling
