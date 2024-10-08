# Twitter Sentiment and Topic Categorization Project

This project involves processing a dataset of raw tweets, performing sentiment analysis, applying topic modeling, and finally categorizing harmful activities into predefined categories. Below are the detailed steps involved.

## Step 1: Dataset Preparation
We start with a dataset containing only the `Raw_Tweet` column. In this step:
- The raw tweet data is cleaned to remove unwanted URLs, tags, and special characters.
- We then apply the **VADER** sentiment analyzer to categorize each tweet into **positive**, **neutral**, or **negative** sentiments.
- After this step, the dataset has two columns: `Raw_Tweet` and `Sentiment`.

## Step 2: Text Cleaning and Preprocessing
Next, we further clean and preprocess the text data:
- After this cleaning step, the dataset now contains three columns: `Raw_Tweet`, `Cleaned_Tweet`, and `Sentiment`.

## Step 3: Dataframe Division by Sentiment
We split the original dataset into three separate dataframes based on sentiment:
- **Positive** dataframe
- **Negative** dataframe
- **Neutral** dataframe

Each of these dataframes contains the same columns: `Raw_Tweet`, `Cleaned_Tweet`, and `Sentiment`.

## Step 4: Topic Modeling
For each sentiment-based dataframe (positive, negative, and neutral), we apply **topic modeling**:
- Topic modeling is performed separately on each sentiment category to extract the most relevant topics for each group of tweets.
- For each document, we extract the top 5 words associated with the most relevant topic. These words represent the core of that topic.
- After merging the columns, each dataframe now contains the following: `Tweet`, `Cleaned_Tweet`, `Sentiment`, and `Topic_Words`.

## Step 5: Focus on Negative Sentiment
As per the objective of our project, we focus on the **negative sentiment** dataframe since it has the highest chance of revealing topics related to harmful activities.

## Step 6: Categorization by Harmful Activity
We created a custom Python script to analyze the `Topic_Words` column for each document in the negative sentiment dataframe. Based on predefined keywords, we categorize each tweet into one of the following categories:
1. **Violence**
2. **Drug-related**
3. **Crime**
4. **Abusive Language**

After this step, the dataframe now contains the following columns: `Tweet`, `Cleaned_Tweet`, `Sentiment`, `Topic_Words`, and `Category`.

## Step 7: Machine Learning Model
To predict the category of future tweets, we train a machine learning model using the current dataset:
- We use the `Cleaned_Tweet` column as the independent variable (IV) and the `Category` column as the dependent variable (DV).
- The `Cleaned_Tweet` is converted into a **TF-IDF matrix** before training the model.
- The goal is to train the model to recognize patterns in the cleaned tweet data so that, in the future, when a new tweet is processed, the model can automatically classify it into one of the four categories
