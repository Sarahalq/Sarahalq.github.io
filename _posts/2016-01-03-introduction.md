
---

###Project Design

In order to create a strategy for the street team, we needed to use the MTA turnstile data to find the top stations with the highest traffic record, the dates with the most number of riders for each station and locating stations that are near tech companies.

-----

### Data Acquisition

The data we used for this project is the MTA turnstile data which can be downloaded freely from their website [Here]({{http://web.mta.info/developers/turnstile.html}}).
We wanted our data to be relevant to the date of the event. Thus, we chose to explore the data from the month of May 2019, as the gala is planned to take place in the beginning of summer

### Data cleaning
In order to get a more accurate results we had to clean and preprocess the dataset.

We began by looking at our dataset and **dropping out unnecessary column** that will not add to our analysis as well as filtering dates that are not in our month scope.
In order to get the total number of traffic per station we had to Create a unique identifier for each turnstiles, by combining the UNIT + SCP columns. After that, we Sorted the Dataset by the dates, the reason for this is that the data is appended to the file randomly meaning you may find the same date but with a different turnstile and that will affect your total traffic accuracy since the turnstile data is cumulative. To meet our 1st project objective we created a new column for total traffic (notice that entries and exists are cumulative measures and are measured every 4 hours) that subtract each row of the entries\exists from its previous (putting in mind larger values to avoid negative values). Some of the turnstile had malware issues entering extreme values. We had to check for them in our data, using the IQR method to find outliers in each station and replacing them with the median of the station.

There are currently three themes built on Poole:

* [Hyde](http://hyde.getpoole.com)
* [Lanyon](http://lanyon.getpoole.com)
* [Enfield](http://enfield.getpoole.com)

Learn more and contribute on [GitHub]({{ site.github.repo }}).

### What's included

Poole is a streamlined Jekyll site designed and built as a foundation for building more meaningful themes. Poole, and every theme built on it like this one, includes the following:

* Complete Jekyll setup included (layouts, config, [404]({{ site.baseurl }}/404.html), [RSS feed]({{ site.baseurl }}/atom.xml), posts, and [example page]({{ site.baseurl }}/about))
* Mobile friendly design and development
* Easily scalable text and component sizing with `rem` units in the CSS
* Support for a wide gamut of HTML elements
* Related posts (time-based, because Jekyll) below each post
* Syntax highlighting, courtesy Jekyll's built-in support for Rouge

Additional features are available in individual themes.

### Browser support

Poole and its themes are by preference a forward-thinking project. In addition to the latest versions of Chrome, Safari (mobile and desktop), and Firefox, it is only compatible with Internet Explorer 9 and above.

### Download

These themes are developed on and hosted with GitHub. Head to the [GitHub repository]({{ site.github.repo }}) for downloads, bug reports, and features requests.

Thanks!
