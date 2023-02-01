---
title: 2. Programming Process
layout: home
---

# **Framework**
{: .fs-7 }

1.	Create a for loop to paginate through the pages of URLs with Amazon reviews
2.	Establish a connection by running a request via Scraper API
3.	Source relevant HTML code for each data feature
4.	Store into a Python Pandas data frame

# **Collection**
{: .fs-7 }

Amazon reviews come in sets of ten per page in order of date. At the time of our data retrieval, the Logitech mouse had 15,203 ratings and 2,606 reviews, which meant that we had 261 pages worth of reviews to paginate through. Every page’s URL is the same apart from the page number, so we labeled the page number as “i” and ran a for loop in the range of the page count. To ease the performance load on the program, we ran multiple loops in groups of 50 pages rather than keeping everything in one large loop. We kept the groups separate through the entire program until the very end where we concatenated our extracted data. While this makes our code less clean, it significantly lowers the minimum processing power to run the code, improving our program’s accessibility. 

Visual: pagination code

<div class="code-example" markdown="1">
```Python

#Code for generating first 50 Amazon URLs (500 reviews)

for i in range(1, 50): # Generate URLs
   url = "https://www.amazon.com/Logitech-MX-Master-3S-Pale/product-reviews/B09HMKFDXC/ref=cm_cr_arp_d_viewopt_srt?ie=UTF8&reviewerType=all_reviews&sortBy=recent&pageNumber=" 
   + str(i) # Construct URL with page number
   list_of_urls.append(url) # Add URL to list of URLs
```
<div class="code-example" markdown="1">

Once we created a list of URLs, we needed to establish a connection between our program and each URL via an import from the Python Requests library. Because our program is extracting data from over 2,000 reviews, we risk having our IP address blocked from making such a high quantity of requests. This is especially true for a website like Amazon which is not web-scraper friendly. To avoid issues with IP blocks, captchas, and proxies, we requested data via a third-party API called ScraperAPI which rotates through IP addresses while iterating through each URL within our list of URLs. This became the outer loop within our nested for loop. 

Visual: Request being made with our API - API key blocked out

With an established connection, we were able to start pulling our relevant data. From each review, we wanted to pull the reviewer name, the star rating, review body, and review date, which we would eventually store into a pandas data frame. After manually identifying the relevant HTML for each data variable, we created an inner loop that used beautiful soup to extract the data for each review, running ten at a time for each URL and then moving on to the next page. 

Visual: show inner for loop 

Each group of data variables per review was appended into its own dictionary. These dictionaries were then combined and converted into a pandas data frame, making it easy to conduct further cleaning. The dictionaries were structured so the data would fit naturally into a two-dimensional matrix with each column representing a new data variable once converted into a pandas data frame. 

# **Cleaning**
{: .fs-7 }

While we were able to pull the relevant data with Beautiful Soup, much of the data came with additional HTML syntax that we did not need. Because of this, we had to come up with unique cleaning solutions for each data variable. This table showcases the before and after cleaning for each variable:

Visual: Table

**Reviewer Name:** For this variable, the only issue was the additional HTML code captured in the first 29 and last 7 characters of each data point. These characters were eliminated using string slicing with Python Pandas. 

Visual: code for reviewer name cleaning

**Star Rating:** Like reviewer name, the issue we faced here was the additional HTML code captured in the first 25 and last 24 characters, which were eliminated using string slicing. We also converted the rating into an integer so it can be used for data analysis in the future. This was the variable for which we had to manipulate the type as the rest were already strings.

Visual: code for star rating cleaning

**Reviews:** We eliminated the first 89 and last 15 characters using string slicing. We also replaced the HTML code that represented breaks in the text with an empty string (“”) so the text would not be interrupted by HTML. This way the text can be used without interruption for NLP. 

Visual: code for reviews cleaning

**Review Dates:** For this variable, the HTML strings in the front of the actual date were of different lengths, and the months of the dates are different lengths (march has 5 characters while December has 8, for example). To work around these challenges, we used Python Pandas to only keep the last 7 characters of each string using a stop argument. Then, we applied a lambda function to each element of the column. The lambda function first split the string on spaces, then used list slicing to grab the last three items of the list, and then joined those three items back into a single string by adding a space between each word. 

Visual: code for review dates cleaning

We also used a function to drop the whole row in case there were any data points that were blank. Because our data was extracted accurately, this only affected rows that had unusual review texts, as this was the only element that was unique in its structure (i.e., how many characters, page breaks, unique symbols, etc.). We felt it was important to delete the entire row so each entry can be complete for any kind of data analysis or visualization. 

----

- [For more information on ScraperAPI and their services, please visit their website by clicking here](https://www.scraperapi.com).
