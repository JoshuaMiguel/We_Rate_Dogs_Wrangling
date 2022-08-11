wrangle_report
July 11, 2022
0.1 Reporting: wragle_report
I firstly imported several libraries such as pandas, numpy and others needed for data wrangling.
The twitter archive dataset provided was read it as a csv_file. I used the request method to download the image prediction flat file and subsequently read it as a tab seperated value file. I applied
to twitter for upgrade to my twitter account to a developers account for the purpose of gaining
the credentials needed to assess the twitter Api using Tweepy. It was granted and then I wrote
a json file of missing datas such as tweet count and favorites count on the twitter archive table. After gathering the data, I began assessing it. Firstly, I assessed the data visually and found
some errors such as several missing values, inconsistent name in name column and None value in
doggo, floofer, pupper and puppo columns , all in the twitter_archive dataset. I also found visually inconsistent naming in p1,p2 and p3 columns such as mixture of small letter and Initial letter
capitalisation, use of ’_’ and white space character, and use of ’-’ in names such as German_shorthaired_pointer, all in the image prediction dataset
I then proceeded to assess the 3 datasets programmatically using methods such as .info(), .describe(), .sample(), .unique(), .value_counts(), .nunique(), .datatype, .isnull() and a few other methods. I found the following errors on: Quality issues Twitter_Archive Table 1.Erroneous datatypes
(timestamp, retweeted_status_timestamp and tweet_id) 2.Nulls represented as None in name,
doggo, floofer, pupper and puppo columns 3.A number of ratings in the rating_numerator are
inaccurate compared with the text value 4.All of the a tag in source column should be replaced
with its corresponding value or content 5.urls included in text column 6.Some names in the name
column are in lowercase and appears not to be actual names such as (’not’, ’an’,’this’, ’this’, ’all’)
Image_Prediction Table 1.Consistency in breed names of dogs 2.tweet_id datatype should be a
string and not interger ?3. Only one prediction data with a value of True and with the highest confidence level will be included in the dataframe Retweets Table 1.tweet_id should be a
string Tidiness issues 1.name, doggo, floofer, pupper and puppo columns in Twitter_Archive Table should be merged and called dog_stages 2.merge p1, p2, p3 related columns for confidence
level and extract to new columns highest confidence level and dog breed 3.rating_numerator and
rating_denominator columns should be merged and named ratings 4.Since only original ratings
are required and no retweet, the following columns with values in their rows will be removed particularly ( retweeted_status and in_reply_to_status_id) 5.All columns not useful for this analysis
will be removed 6.All dataframe will be merged into one master dataframe
I then proceeded to made a copy of all 3 datasets and proceeded to clean the data frame using
several methods such as .loc(), .drop(), for loops, if statements, .merge(), .replace(), regex and
several other methods


0.1 Report: act_report
After cleaning the dataset I then merged all 3 dataset into 1 master dataframe as per course requirements. I then began analysing the dataset for insights. I began by importing several libraries
also, particularly needed for visualization, they include seasborn, matplotlib,.pyplot, matplotlib
inline and plotly.express. I didn’t use all of the libraries imported due to the lateness already
in submission of this report. I used the groupby method to assess one variable against another.
Alongside the groupby method, I used functions like .count(), .sort_values(). I discovered an insight on the master dataset which is that the top dog_breeds based on the highest number of
tweets are Golden Retriever, Pembroke, Labrador Retriever, Chihuahua, Pug, Pomeranian and so
on as in the dataframe above. Then I also checked for number of tweets made using the dog stages
terminologies and I found that 202 tweets were made having a value for dog stages.
Then I checked for any correlation between the favorites count and the retweet count using
the pandas .corr() method and I found that the favorites count and retweet count have a strong
correlation. I proceeded to run a visualization of this finding using a scatter plot and it confirmed
the insight to be correct. Although there is a strong correlation between the two variables there is
no explanation on causation which will require further analysis