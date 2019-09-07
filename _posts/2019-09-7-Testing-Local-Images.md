---
layout: post
title: Data Analysis of MTA Turnstile Data
---

Finding the top 10 stations in NYC with the highest traffic record.

![Image test]({{ site.url }}/images/pic.jpg)


```
---
layout: post
title: Data Analysis of MTA Turnstile Data
---
```

###Project objective:
Maximize the WomenTechWomenYes annual gala attendance and contribution.

###Problem statement:
* Deploying street teams effectively
* Targeting the right people


###Project Design

In order to create a strategy for the street team, we needed to use the MTA turnstile data to find the top stations with the highest traffic record, the dates with the most number of riders for each station and locating stations that are near tech companies.


### Data Acquisition

The data we used for this project is the MTA turnstile data which can be downloaded freely from their website [Here]({{http://web.mta.info/developers/turnstile.html}}).
We wanted our data to be relevant to the date of the event. Thus, we chose to explore the data from the month of May 2019, as the gala is planned to take place in the beginning of summer.

### Data cleaning
In order to get a more accurate results we had to clean and preprocess the dataset.

We began by looking at our dataset and **dropping out unnecessary column** that will not add to our analysis as well as filtering dates that are not in our month scope.
In order to get the total number of traffic per station we had to Create a unique identifier for each turnstiles, by combining the UNIT + SCP columns. After that, we Sorted the Dataset by the dates, the reason for this is that the data is appended to the file randomly meaning you may find the same date but with a different turnstile and that will affect your total traffic accuracy since the turnstile data is cumulative. To meet our 1st project objective we created a new column for total traffic (notice that entries and exists are cumulative measures and are measured every 4 hours) that subtract each row of the entries\exists from its previous (putting in mind larger values to avoid negative values). Some of the turnstile had malware issues entering extreme values. We had to check for them in our data, using the IQR method to find outliers in each station and replacing them with the median of the station.

### Other things
* Like
* lists
* and
* stuff
