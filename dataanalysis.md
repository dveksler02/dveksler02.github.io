---
title: 3. Data Exploration & Analysis
layout: home
---

# **Data Dimensions**
{: .fs-7 }

The dataset summarizing Logitech MX Master 3 Amazon reviews is a two-dimensional matrix with 4 data elements representing each column, and 2,560 unique reviews representing each row. 

| Rows - Data Elements       | Columns - Review Count          |
|:---------------------------|:--------------------------------|
|  4                         |  2,549                          |

# **Descriptive Data Analytics**
{: .fs-7 }

The quickest identifiable feature of every review is its star rating which is on a higher-is-better 5-point scale. The distribution for this product listing, and nearly every reputable listing on Amazon for that matter, is J-shaped, with an overwhelming majority of ratings falling in the 5- and 4-star category ranges. 

# **Boxplots**
{: .fs-7 }

![Boxplot](./img/Boxplot_DS105.png)  

While investigating our dataset we realized that the data we were looking at was one dimensional in nature, so this meant that exploring correlation between a feature and star-rating was practically impossible as we did not have two independent variables to utilize. With these limitations, we found methods of analysis and visualization for data with just one dimension. This led us to creating code to visualize our data in the form of boxplots which look at the star rating of reviews under instances in which a specific keyword is mentioned and above each respective boxplot we can see the number of reviews in which the keyword was mentioned. We picked these words as our key words because they were identified as the main features on the Amazon product listing of the mouse.  
Further looking into the visualization of our data it is evident to see by the central tendency or distribution of median rating (specified by the bold horizontal line) that our data has a J-shaped distribution with a majority of 4- or 5- star reviews. This reality is further strengthened both by the spread within our boxplots which can be seen through the interquartile ranges in most cases being around 4-5 rating and that in some cases outliers exist in where the rating is 1 or 2 indicating that instances of users rating the Logitech mouse low are in fact quite rare when certain keywords are mentioned in the review.  

# **Histogram**
{: .fs-7 }

![Histogram](./img/Histogram_DS105.png)

As seen in the histogram above the distribution of the word lengths has a positive skew with the average number of words being near the 0-to-20-word count. While there is the argument this may not be useful for figuring out customer preferences as we have less data to work with, there is the caveat that the shorter comments will only contain the most important criticisms or compliments about the Logitech mouse. Below is an example of where a shorter review gives us a clearer indication of comments on the mouse which we can analyze as opposed to a longer comment: 
| Nick G      |  love all the features. Especially the thumb scroll. Great product.          |
|:---------------------------|:--------------------------------|
|  JK                        |          Summary: Mouse is twitchy, mis-clicks and has the worst software I've used it regularly causes me to click-drag-copy files in Windows and lowering its sensitivity means I have to swipe too much, to get the mouse across my two screens.  No, I'm not new to using mice and I own a 10k dpi gaming mouse that I have no problems with.  And before you suggest I adjust the dpi, I should point out that "Options", the Logitech software for Windows (which has almost no options, ironically) doesn't allow the user to change the dpi or mouse polling rate.  There's only a sensitivity setting, like Windows 10 already has. But that's just a minor complaint.  The main problems are the mouse-wheel, which is touted as an improvement over normal wheels, but feels more like a really bad automatic transmission; always scrolling WAY to far, or not far enough.  And since they replaced the normal mechanism, you can't turn it off, but without the feature enabled, the wheel response is terribly sluggish. The biggest trigger for me, however, has to be the button design for the two main buttons...                  |
