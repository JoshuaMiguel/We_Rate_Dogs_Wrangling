# Data Wrangling and Analysis Report

## Overview
This project involves wrangling, cleaning, and analyzing a Twitter archive dataset, an image prediction dataset, and a retweets dataset. The goal was to process the data, identify key issues, and derive insights from the cleaned dataset using various methods and visualizations.

## Data Wrangling Process

### Step 1: Data Import & Preparation
**Libraries Used**: I imported essential libraries like `pandas`, `numpy`, and others for data wrangling and cleaning.
  **Datasets**: 
  The **Twitter archive dataset** was read from a CSV file.
    The **image prediction dataset** was downloaded using the `requests` method and saved as a tab-separated value (TSV) file.
    I applied for and received access to the Twitter API using Tweepy to gather additional data, such as tweet counts and favorite counts, and then stored this information in a JSON file.

### Step 2: Initial Data Assessment
I assessed the datasets both visually and programmatically using methods like `.info()`, `.describe()`, `.sample()`, `.unique()`, `.value_counts()`, `.isnull()`, and others.
  
#### Issues Identified:
**Twitter Archive Dataset**:
  1. Erroneous datatypes (e.g., `timestamp`, `retweeted_status_timestamp`, `tweet_id`).
  2. Missing values in `name`, `doggo`, `floofer`, `pupper`, and `puppo` columns.
  3. Inaccurate ratings in the `rating_numerator` column compared with the text.
  4. The `source` column contains HTML tags that need to be replaced with their content.
  5. URLs present in the `text` column.
  6. Inconsistent names in the `name` column, including words like 'not', 'an', 'this', which are not valid names.
  
  **Image Prediction Dataset**:
  1. Inconsistent dog breed names (capitalization and formatting issues).
  2. The `tweet_id` should be a string instead of an integer.
  3. Only one prediction (with the highest confidence level) should be included for each tweet.

  **Retweets Dataset**:
  1. The `tweet_id` should be a string, not an integer.

#### Tidiness Issues:
1. Merge `name`, `doggo`, `floofer`, `pupper`, and `puppo` columns into one column called `dog_stages`.
2. Merge the `p1`, `p2`, and `p3` related columns for breed predictions and extract the highest confidence level and breed into new columns.
3. Combine `rating_numerator` and `rating_denominator` into a single `ratings` column.
4. Remove unnecessary columns such as `retweeted_status` and `in_reply_to_status_id`.
5. Drop all other irrelevant columns for this analysis.
6. Merge all three datasets into one master dataframe for analysis.

### Step 3: Data Cleaning
I made copies of the three datasets and applied various cleaning methods including `.loc()`, `.drop()`, `.merge()`, `.replace()`, regex, and conditional statements (e.g., `if` statements) to fix the identified issues.

## Analysis and Insights

### Step 1: Data Merging
After cleaning the datasets, I merged all three into one master dataframe as required.

### Step 2: Data Visualization & Analysis
**Libraries Used**: I imported visualization libraries such as `seaborn`, `matplotlib`, and `plotly.express`.
  **Analysis**: 
  I used the `groupby` method to analyze variables against one another, and used functions like `.count()`, `.sort_values()`, and others to gather insights.
    I found that the top dog breeds based on the highest number of tweets were **Golden Retriever**, **Pembroke**, **Labrador Retriever**, **Chihuahua**, **Pug**, and **Pomeranian**.
    Additionally, I analyzed the number of tweets containing various dog stage terms (e.g., "doggo", "pupper"), and found that there were **202 tweets** featuring these terms.

### Step 3: Correlation Analysis
I performed a correlation analysis between **favorites count** and **retweet count** using the `.corr()` method in pandas.
  **Finding**: There is a **strong correlation** between the favorites count and retweet count. 
    **Visualization**: I used a scatter plot to confirm this relationship, which further verified the correlation. However, while the correlation is strong, causality cannot be determined, and further analysis would be required.

## Conclusion
The data wrangling and cleaning process allowed me to address various issues in the datasets, including missing values, inconsistent formatting, and erroneous datatypes.
The merged and cleaned dataset provided valuable insights, including trends in popular dog breeds and correlations between key variables (favorites count and retweet count).
Visualizations confirmed some of these insights and highlighted areas that could be further explored for deeper analysis.

