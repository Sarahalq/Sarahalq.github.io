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

### Project objective
Maximize the WomenTechWomenYes annual gala attendance and contribution.

### Problem statement
* Deploying street teams effectively
* Targeting the right people


### Project Design

In order to create a strategy for the street team, we needed to use the MTA turnstile data to find the top stations with the highest traffic record, the dates with the most number of riders for each station and locating stations that are near tech companies.


### Data Acquisition

The data we used for this project is the MTA turnstile data which can be downloaded freely from their website [Here]({{http://web.mta.info/developers/turnstile.html}}).
We wanted our data to be relevant to the date of the event. Thus, we chose to explore the data from the month of May 2019, as the gala is planned to take place in the beginning of summer.

### Data cleaning
In order to get a more accurate results we had to clean and preprocess the dataset.

We began by looking at our dataset and **dropping out unnecessary column** that will not add value to our analysis as well as **filtering dates that are not in our month scope**. In order to get the total number of traffic per station we had to **Create a unique identifier for each turnstiles, by combining the UNIT + SCP columns**. After that, we **Sorted the Dataset by the dates**, the reason for this is that the data is appended to the file randomly meaning you may find the same date but with a different turnstile and that will affect your total traffic accuracy, since the turnstile data is cumulative. To meet our 1st project objective *we created a new column for total traffic* (notice that entries and exists are cumulative measures and are measured every 4 hours) that subtract each row of the entries\exists from its previous (putting in mind larger values to avoid negative values). Some of the turnstile had malware issues entering extreme values. We had to check for them in our data, *using the IQR method to find outliers in each station and replacing them with the median of the station*.

### Data Visualization
After cleaning our data, we visualized the results using matplotlib and seaborn.
To analyze the data and conclude recommendation for WomenTechWomenYes we used the below bar graphs.

![Image test]({{ site.url }}/images/Unknown.png)

The above graph shows the top 20 stations in NYC for the month of May 2019.

![Image test]({{ site.url }}/images/Unknown-1.png)

The above graph shows the traffic per day for the month of May 2019 in our top station "34 ST-PEEN STA".

The results above help us to know what are the stations we should send our street team too and in what days. In order to get the most signatures, we believe that we should target the most crowded stations and to make sure that we are talking to the right people we should target the top stations that are near tech companies to meet our target audience.


### Recommendations
For WomenTechWomenYes annual gala, we would recommend distributing their street team on **34 ST-PEEN STA, GRD CNTRL-42 ST, 23 ST and TIMES SQ-42 ST** during workdays.


### Future Work

* Automate the process of locating the nearest stations to tech companies.
* Explore a larger scope from our data
* Determine the exact hours of the day where station are crowded the most.  



### Tools used for this project

#### Python
we used python packages to clean and analyze the data specifically pandas to clean and preprocess, matplotlib and seaborn to visualize it.

#### Git and Github
we used Git for coordinating work among us.
