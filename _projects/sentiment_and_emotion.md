---
layout: default
title: "Sentiment Analysis and Emotion Classification of FIFA Award related Tweets"
date:    2023-09-15 14:00:00
selected: true
---


# Project Overview
[GitHub](https://github.com/SuloveBhattarai/Sentiment-Analysis-of-FIFABest-Football-Award)

This project is all about sentiment analysis and emotion classification of the FIFA Award related tweets. Data is scraped from Twitter, and let's discuss the other topics below.

&nbsp; 
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/sentiment_results1.png" alt="Sentiment Results 1" width="30%">
        <p>Sentiment Analysis</p>
    </div>
</div>

# Data Preprocessing for ISEAR Dataset

Here, I have loaded the dataset called **ISEAR(International Survey on Emotion Antecedents and Reactions)**. The first dataset is loaded and data preprocessing is done. 

The preprocessing steps include:

1. **Uppercase to Lowercase:** 
2. **Removing Whitespace Characters:** Eliminating unnecessary spaces and tabs from the text.
3. **Removing Stop Words:** Filtering out common words that do not contribute much meaning to the data.
4. **Spelling Correction Using TextBlob:** 
5. **Stemming Using PorterStemmer():** Reducing words to their base or root form.

### Encoding of Emotion to Numerical Values Using LabelEncoder

The table below shows the encoding of different emotions to numerical values using `LabelEncoder()`:

| Emotion    ||||   Count   ||||  Encoding  |
|------------||||-----------||||------------|
| Joy        ||||   1091    ||||      5     |
| Sadness    ||||   1082    ||||      6     |
| Anger      ||||   1079    ||||      0     |
| Fear       ||||   1076    ||||      2     |
| Shame      ||||   1071    ||||      7     |
| Disgust    ||||   1066    ||||      1     |
| Guilt      ||||   1049    ||||      3     |


## Train-Testing Split 75% - 25%

#### Conversion of Text to Features (Feature Engineering)

After that, **CountVectorizer** converts the text data into a matrix of token counts, and **TfidfVectorizer** is another method for converting text data into numerical features. TfidfVectorizer gives importance to the words that are meaningful across datasets.
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/sentiment_summary.png" alt="Summary" width="30%">
        <p>Summary</p>
    </div>
</div>

From above, it is clear that Logistic Regression with TFIDF has the highest accuracy, so let's select this for further classification

Then the tweet is trained using a Logistic Regression model using TF-IDF features, and emotion is predicted on the test data, and evaluated the model's performance by comparing the predicted labels to the actual labels.

#### Scrapping of Data from Twitter

Scrapping of Twitter data using Nitter library. About 1000 of tweets were scrapped for the two days after the Fifa Award was awarded. 

### Prediction of each tweet on Sentiment Analysis and Emotion classfication
After that, preprocessed tweets were taken and converted into TF-IDF features, and a trained machine learning model was used to predict the emotion of each tweet.

TextBlob's sentiment analysis was applied to each tweet.

A graph of the data was plotted by Sentiment Analysis and Emotion.
<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/sentiment_results1.png" alt="Sentiment Results 1" width="100%">
        <p>Sentiment Analysis</p>
    </div>
    <div style="flex: 1; text-align: center;">
        <img src="../images/sentiment_results2.png" alt="Sentiment Results 1" width="100%">
        <p>Emotional Classification</p>
    </div>
</div>
</div>
