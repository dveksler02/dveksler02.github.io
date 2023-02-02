---
title: 4. Challenges & Conclusion
layout: home
---

# **Scraping Access Challenges:**
{: .fs-7 }

The first challenge we ran into was gaining access to the site without interference. It is in Amazon’s best interest to prevent web scraping capabilities so they can keep users on their site, so the company uses a variety of anti-scraping measures, including varying web structures and blocking unusual requests such as those with abnormal quantities or coming from bots. Thankfully, the web structure of the customer reviews section is mostly similar on every Amazon product, so we were able to work around that first hurdle. As for avoiding our IP address being blocked, we worked around this challenge by running requests through ScraperAPI which rotated IP addresses with each request. Using an API, however, increased the processing power to run our code significantly which led to us having to employ additional work arounds so our program could run seamlessly.

# **Programming and Data Wrangling Challenges:**
{: .fs-7 }

At first, the processing power required to run our program was simply too high, especially for a browser-based Python IDE like Google Colab. On top of requesting via an API, the program would have to pull four data elements for ten reviews for each URL at a time, repeat this process for 261 unique URLs, and then store all the information into separate dictionaries. To alleviate the pressure, we separated the links into smaller groups of URLs and had the program iterate through 50 URLs at a time instead of 261 and concatenate the extracted dictionaries into a data frame at the very end. Finding the optimal group size for the groups of URLs took some trial and error, but we find that groups of 50 took the computer anywhere from 3 to 5 minutes to process and export an uncleaned CSV.

<div class="code-example" markdown="1">
```python
# Code for creating lists of URLs, each storing 50 with the exception of the last which stores 61 (for 261 reviews overall)

list_of_urls = []
list_of_urls2 = []
list_of_urls3 = []
list_of_urls4 = []
list_of_urls5 = []
```
</div>

<div class="code-example" markdown="1">
```python
# Code for concatenating the dataframes for each group of 50 reviews

df_complete = pd.concat([df, df2, df3, df4, df5], axis=0)
```
</div>

Another challenge we faced was finding the right HTML source code for our variables to prevent our data table skewing from different starting points when being called with the soup.find_all() function. For example, the reviewer name data variable included the top reviews section, which was a repeat of reviews that Amazon wanted to highlight. Review dates, however, started with the most recent review, which was the point at which we wanted our data table to start. After some trial and error, we were able to identify HTML source code for each data variable which had the same starting point to avoid the skewing issue.

Data cleaning was not a one size fits all solution for our data variables. For some data variables we were able to rely uniquely on the string slicing function in Python to clean it up, but for others like review dates we had to get more creative. 

# **Data Analysis Challenges:**
{: .fs-7 }

The main issues and challenges faced within the data analysis process stemmed from creating multiple boxplots to show the Star-rating of reviews in instances where a specific keyword was mentioned. The challenge within this data-analysis was twofold, firstly many cases of debugging was required when using the several nested loops and string manipulations to rectify any inconsistent data types. Secondly, it was essential to be able to understand which loops to utilize to iterate through each row of the dataframe. This meant using unfamiliar panda functions namely '.iterrows()' and it took time to find solutions on forums like StackOverflow. However, after creating the first python program for boxplots, using the plotnine library with lists became relatively easy with similar syntax and processes being used to create the histogram and bar charts.

# **NLP Analysis Challenges:**
{: .fs-7 }
 
The main challenge we faced is the selection bias of the data we are using for NLP analysis: the most reviews are all 5 stars because those who usually rate and leave comment are satisfied with the product. This skewed distribution of amazon product reviews affects the accuracy of our analysis as we are more biased towards positive aspects of the mouse than the negatives. Furthermore, the customers’ ratings were subjective as they tend to give a higher rating than what they actually think of the product, hence we used sentiment intensity analyzer to score the review texts to get a more accurate sentiment score and compared the two distributions of star ratings and sentiment scores.   

# **Conclusion:**
{: .fs-7 }

Within our project scope, we had two goals we wanted to accomplish when working on this project. The first and primary goal was to create a plug-in program that seamlessly and efficiently extracts Amazon customer reviews and exports them into a CSV. The second goal was to illustrate a use case of how our program can be used for further purposes, and we wanted to accomplish this by creating summary statistics and data analysis on reviews of the Logitech MX Master 3.

We can confidently say that we accomplished our first goal in its entirety. With our plug-in program, anybody can input a link to an Amazon Customer Reviews page, configure the number of groups to the review count, and seamlessly output a cleaned CSV file with all the review data. This program runs best on Google Colab as we developed our code on it. This factor further accomplishes our goal because of the accessible nature of a Google IDE; to use our program, you do not even need to have Python installed on your computer.

While we were able to create descriptive statistics and run some analysis on the Logitech MX Master 3, many of our findings were inconclusive. While there were many factors that limited our capabilities as analysts, the biggest was the J-shaped distribution. With a lack of variables in each category but 5 stars, it is difficult for us to gauge the accuracy of any model we attempt to create. 

For anybody interested in extracting customer reviews from Amazon for whatever purpose, we highly recommend you try our plug-in model! It is highly versatile and easy to use! Thank you for browsing our website.



