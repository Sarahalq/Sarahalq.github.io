---
layout: post
title: Predicting book prices
---

Predicting book prices using linear regression model.

![Image test]({{ site.url }}/images/book.JPG)


### Dataset
Data was scrapped from the Book Depository website using Beautiful Soup. Which is a python package that is used for scrapping html and xml files. [Book Depository] ({{https://www.bookdepository.com/bestsellers}}) is an online book store with over 20 million books. My data set contained 1020 book from the bestseller page with 13 different attributes. These attributes are the book author name, genre, publisher name, cover (paperback or hardback), date of publication, number of pages, average rating, number of reviews, rank on the bestseller list and price.


### Data cleaning
After obtaining the data and organize it into a data-frame cleaning was performed using Pandas.
![Image test]({{ site.url }}/images/df.png)
*  Converting all non-numeric columns to numeric type by removing regular expressions first and then using pandas function as type.
![Image test]({{ site.url }}/images/cleaning.png)
* Removing null values, duplicates, and unnecessary columns.
* Removing outliers using IQR.
* Dealing with the genre column, each book in the dataset contained multiple genres I ended up with over 600 different genres for the whole dataset. In order to minimize this number I created 6 categories containing the sum of the top categories and any book that is not on those categories will be in the others genre.
![Image test]({{ site.url }}/images/genre.png)


### Data Analysis
![Image test]({{ site.url }}/images/kids.png)
The graph above is a scatter plot showing the price and pages of all books (blue dots) and books in the kid’s genre (orange dots). As you can see some of the kid’s books are clustered in the lower area where pages are under a 100. However, the price is distributed between 5 dollars and 35 dollars. The rest of the data is randomly scattered which shows that there is no specific pattern associated with the price variable.

In the graph below you can see that the price variable was not normally distributed.
![Image test]({{ site.url }}/images/price.png)

I preformed log transformation on the variable and the new price distribution is shown below.
![Image test]({{ site.url }}/images/price_log.png)

Before preforming the linear regression, I had to create dummy variables for my categorical data by assigning each categories as a combination of 1 and 0.
![Image test]({{ site.url }}/images/dummy.png)

Now we can check the correlation matrix to find what variables have the highest correlation with the target (price).
![Image test]({{ site.url }}/images/heatmap.png)

The heat map above shows there is no correlation between the target and the features.

When the linear regression model was performed on the trained dataset:
![Image test]({{ site.url }}/images/train.png)

When the linear regression model was performed on the test dataset:
![Image test]({{ site.url }}/images/test.png)

### Conclusion
In conclusion, my data don't fit a linear regression model as the r^2 indicated above.
There were no correlation between the target and the features. However, trying another model or increase the
dataset to include more books not just the bestsellers.
