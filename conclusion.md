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

```python

# Code for concatenating the dataframes for each group of 50 reviews

df_complete = pd.concat([df, df2, df3, df4, df5], axis=0)

```
</div>

Another challenge we faced was finding the right HTML source code for our variables to prevent our data table skewing from different starting points when being called with the soup.find_all() function. For example, the reviewer name data variable included the top reviews section, which was a repeat of reviews that Amazon wanted to highlight. Review dates, however, started with the most recent review, which was the point at which we wanted our data table to start. After some trial and error, we were able to identify HTML source code for each data variable which had the same starting point to avoid the skewing issue.

Data cleaning was not a one size fits all solution for our data variables. For some data variables we were able to rely uniquely on the string slicing function in Python to clean it up, but for others like review dates we had to get more creative. 

# **Data Analysis Challenges:**
{: .fs-7 }

ABHI TEXT HERE

# **NLP Analysis Challenges:**
{: .fs-7 }

VANESSA TEXT HERE

# **Programming and Data Wrangling Challenges:**
{: .fs-7 }



