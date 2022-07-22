# DATA-ANALYSIS-AND-VISUALIZATION-OF-A-TWITTER-ACCOUNT-WeRateDogs-dog_rates-
Python Libraries was used

The essence of data analysis and visualization is to uncover insightful details from a data. A critical step in data analytics, data visualization gives firms crucial insights into untapped data and messages that would otherwise be lost. We now have a visual summary of the data, so we don't need to trawl through millions of rows to uncover trends and patterns. Python’s libraries were used to carry out the analysis and visualization, the codes are included in this report.

The dataset that you will be wrangling (and analyzing and visualizing) is the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because "they're good dogs Brent." WeRateDogs has over 9 million followers and has received international media coverage.

WeRateDogs downloaded their Twitter archive and sent it to Udacity via email exclusively. This archive contains basic tweet data (tweet ID, timestamp, text, etc.) for all 5000+ of their tweets as they stood on August 1, 2017. More on this soon.

In this project, I will work on the following three datasets.

**1. Enhanced Twitter Archive**

The WeRateDogs Twitter archive contains basic tweet data for all 5000+ of their tweets, but not everything. One column the archive does contain though: each tweet's text, which was used to extract rating, dog name, and dog "stage" (i.e. doggo, floofer, pupper, and puppo) to make this Twitter archive "enhanced." Of the 5000+ tweets, the tweets have filtered  with ratings only (there are 2356).

Extracted data from tweet text
The extracted data from each tweet's text This data has been extracted data programmatically, but didn't do a very good job. The ratings probably aren't all correct. Same goes for the dog names and probably dog stages (see below for more information on these) too. There is need to assess and clean these columns in order to use them for analysis and visualization.


**2. Additional Data via the Twitter API**

Back to the basic-ness of Twitter archives: retweet count and favorite count are two of the notable column omissions. Fortunately, this additional data can be gathered by anyone from Twitter's API. Well, "anyone" who has access to data for the 3000 most recent tweets, at least. But I, because I have the WeRateDogs Twitter archive and specifically the tweet IDs within it, can gather this data for all 5000+. And guess what? You're going to query Twitter's API to gather this valuable data.

**3. Image Predictions File**

One more cool thing: every image in the WeRateDogs Twitter  archive have been ran through a neural network that can classify breeds of dogs*. The results: a table full of image predictions (the top three only) alongside each tweet ID, image URL, and the image number that corresponded to the most confident prediction (numbered 1 to 4 since tweets can have up to four images).

Image predictions
Tweet image prediction data

So for the last row in that table:

tweet_id is the last part of the tweet URL after "status/" → https://twitter.com/dog_rates/status/889531135344209921
p1 is the algorithm's #1 prediction for the image in the tweet → golden retriever
p1_conf is how confident the algorithm is in its #1 prediction → 95%
p1_dog is whether or not the #1 prediction is a breed of dog → TRUE
p2 is the algorithm's second most likely prediction → Labrador retriever
p2_conf is how confident the algorithm is in its #2 prediction → 1%
p2_dog is whether or not the #2 prediction is a breed of dog → TRUE
etc.

The following are what I did:
- ## Data Gathering
>1. Imported **Enhanced Twitter Archive** using Pandas
>2. Used Request to import **Image Prediction File** through its URL
>3. Twitter API was used to query WeRateDogs handle using Tweepy to gathher the **Additional Data via the Twitter API**
- ## Data Assesing
> This was done virtually and programmatically to assess what has to be cleaned in the data.
- ## Data Cleaning
The following are issues encountered and cleaned for proper analysis and visualization:
#### Quality Issues
- Twitter Archive Data
>1. Retweets columns are present.
>2. `tweet_id` is an integer.
>3. Dog stages columns doggo, floofer, pupper,and puppo contains None, instead of NaNs.
>4. Dog name also containes None instead of NaNs.
>5. `timestamp` is object datatype.
>6. Extract the text from source column
- Image Predictions Data
>7. `p1`, `p2` and `p3` contains some entries that are lower cased and some contains underscore.
- Twitter API Data
>8. `tweet_id` is an integer instead of string.
#### Tidiness Issues
>1. 4 different dog stages (doggo, floofer, pupper, puppo) that can just be in a column.
>2. The 3 dataframes sould be merged into one.
- ## Data Analysis
The insights gotten are
>1. The most used kind of device for tweeting
>2. Which dog stage is tweeted the most 
>3. The most liked dog stage
>4. Dog stages that are retweeted the most
>5. The most common dog name
>6. The most common dog type
>7. Correlation between favorite count and retweet count
>8. An heatmap to see the relationship of all the features
