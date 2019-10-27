---
layout: post
title: News Clustering
---

Can we predict the category of a news article by its headline?
![Image test]({{ site.url }}/images/breaking_news1.png)


### Dataset

This dataset contains headlines, URLs, and categories for 422,937 news stories collected by a web aggregator between March 10th, 2014 and August 10th, 2014.


Downloaded from: [Here]({{https://www.kaggle.com/uciml/news-aggregator-dataset}}).


##### Dataset Attribute Information:
* ID : the numeric ID of the article
* TITLE : the headline of the article
* URL : the URL of the article
* PUBLISHER : the publisher of the article
* CATEGORY : the category of the news item; one of: -- b : business -- t : science and technology -- e : entertainment -- m : health
* STORY : alphanumeric ID of the news story that the article discusses
* HOSTNAME : hostname where the article was posted
* TIMESTAMP : approximate timestamp of the article's publication, given in Unix time (seconds since midnight on Jan 1, 1970)


### Data cleaning

1. In order to preform unsupervised learning (Clustering) on the data I dropped all
columns except the TITLE.

2. In order to clean the headlines column I used nltk, space and regex libraries.
  * Make all words lowercase
  * Removing punctuation
  * Removing numbers
  * Removing stop words
  * Removing non-English words
  * Performing lemmatization

  This is an example of how the cleaning process was applied to the headlines:
  ![Image test]({{ site.url }}/images/cleaning1.png)


### Vectorizing

After cleaning the headlines, we have to convert all documents into vectors of
numbers so we can run statistical models on them.
The method I chose was CountVectorizer: Bag of words (BoW).  
In BoW, every sentence is represented as the bag of its words where the
occurrence of each word is used as a feature.



### Topic Modeling & Clustering


In order to find the best number of cluster for my data I used one of
the popular measures the Elbow method:
![Image test]({{ site.url }}/images/elbow.png)

Here are the top 10 most important words for each of the 4 topics:
![Image test]({{ site.url }}/images/topics.png)
as you can see some of these words in each topic made sense.
For example, topic 1 had words such as global, warming, climate and panel which
usually come together.


### Tools used for this project

#### Python
Pandas and numpy to clean and preprocess, matplotlib and seaborn to visualize it, and sklearn for modeling
