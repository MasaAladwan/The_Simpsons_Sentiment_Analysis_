# Simpsons Show Script Analysis


Analyzing Simpsons Show Scripts: Character Insights and Viewer Engagement

 Made by [Masa Aladwan](https://github.com/MasaAladwan) and [O'taymh Abu Taha](https://github.com/Otaymh)

## Project Overview

This project analyzes the script data from The Simpsons show to gain insights into the characters' dialogues, their sentiment, and viewer engagement metrics such as ratings and votes.We focused on the main characters of the show 


## Table of Contents  

[Objectives
](#headers)  

[Data Description
](#headers)  

[Data Preprocessing
](#headers)  


[Feature Engineering
](#headers)  

[Results
](#headers) 

[Sentiment Analysis
](#headers) 

[Models
](#headers) 


[WordCloud
](#headers)

[PowerBi
](#headers)

[Requirements
](#headers)

[Resources
](#headers)

[Results
](#headers)


## Objectives
* Extract and preprocess dialogue data for key characters.
* Analyze the most spoken words by each character.
* Perform sentiment analysis on the dialogues.
* Analyze viewer engagement metrics like average season rating and IMDb votes.
* Visualize the results in an informative and user-friendly manner using PowerBi.

## Data Description 

* " episode_id " : the number of episode
* " raw_character_text ": The name of the character.
* " raw_text " : the script spoken by the character 
* " spoken_words " : The dialogue spoken by the character.
* " timestamp_ms " : The timestamp of the dialogue in milliseconds.
* " season_rating " : The rating of the season.
* " IMDB_votes ": The number of votes the season received on IMDb.
* " speaking_line " : describe if character said this line or not


## Data Preprocessing 

* Identified and handled miss input in the "raw_character_text" column by comparing it with the "character_id" column"
* Null values in 'character_id' column represent scenes (scenes don't have IDs)
* Converted the character_id from object to int, as the column contains both int and float values.
* Timestamp Conversion: Convert the timestamp_ms column from milliseconds to minutes to see if they speak more at the beginning, middle, or end of the episode
* Removed stop words from the spoken_words column to clean the text data.


## Feature Engineering
* Assign Seasons: Assign seasons based on episode numbers.
* Character Script Lists: Create lists to hold dialogues for key characters.
* Interval : This column denotes three distinct values  "first," "mid," and "final," indicating the timing within the episode when the character spoke.
* word counts : the number of spoken words for each script, this helps in understanding the level of activity for each character

## Sentiment Analysis 
* Implemented TF-IDF vectorization using a custom `TFIDFVectorizer` class to analyze text data.
* The `fit_transform()` method tokenizes each document into words, calculates the term frequency (TF) for each term, and computes the inverse document frequency (IDF).
* TF-IDF scores are calculated for each document based on the TF and IDF values.
* Sentiment analysis is performed by summing up the TF-IDF scores for each document.
* Calculated mean and standard deviation of sentiment scores to determine neutral, positive, and negative thresholds.
* Assigned sentiment labels (Neutral, Positive, Negative) to documents based on their overall sentiment scores.
* Implemented a sentiment classification process to categorize documents into sentiment categories.
* Applied sentiment labels to the dataset for further analysis and interpretation.

## Models 

* Random Forest (RF): For classification and regression tasks.
* Logistic Regression: For binary and multi-class classification tasks.
* Support Vector Classifier (SVC): For classification tasks.
* XGBoost: For gradient boosting classification and regression tasks.
* TextBlob: For sentiment analysis and text processing.


## WordCloud

![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/e0e98812-be33-45ac-a774-25a51d4f5df9)

![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/2267bf40-67f4-4eee-bfdb-d9a757422287)

![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/355a3360-50d1-4812-b1e7-3b56e655e6e6)

![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/6fc3c1ab-02ca-4690-9b6f-ca95b7b06eed)


## PowerBi
![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/368d413a-b6dc-4731-a37b-929d625ee11d)
![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/c0c250f0-dd1b-4161-bd5e-046368e8714b)
![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/f9515edd-9e46-4e62-be38-7b321d317df0)


## Requirements:
Install dependencies:

```bash
pip install -r requirements.txt
```
## Resources :
* Data : https://www.kaggle.com/datasets/prashant111/the-simpsons-dataset



## Results :
* Characters Activity :

#### - Homer Simpson 
      . First : 10241
      . Mid : 9745
      .Final : 8115
#### - Marge Simpson 
      . First : 5018
      . Mid :  4589
      .Final : 3658
#### - Bart Simpson 
      . First : 4858
      . Mid : 4519
      .Final : 3808
#### - Lisa Simpson 
      . First : 3788
      . Mid : 3836
      .Final : 3253 

* Accuracy for models :
  - TF-IDF
 
  
  ![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/45856fe9-ae52-437d-bc6d-87fe28c26b7c)
  - Textblob
 
  
  ![image](https://github.com/MasaAladwan/The_Simpsons_Sentiment_Analysis_/assets/142498123/fce3e35f-3d43-443b-ae1e-ee5b0e2d3c30)


Sentiment Distribution Summary
* TextBlob Sentiment Distribution
  * Neutral: 42,588 instances
  * Positive: 14,010 instances
  * Negative: 8,830 instances

* TF-IDF Sentiment Distribution
  * Neutral: 54,641 instances
  * Positive: 6,566 instances
  * Negative: 4,221 instances

* The sentiment distribution results from TextBlob and the custom TF-IDF approach reveal the following trends:
   * Neutral Sentiment: Both methods predominantly classified the dialogues as neutral, with TF-IDF identifying a higher number of neutral instances (54,641) compared to TextBlob (42,588).
    * Positive Sentiment: TextBlob identified a significantly higher number of positive instances (14,010) compared to TF-IDF (6,566).
   * Negative Sentiment: TextBlob also identified more negative instances (8,830) than TF-IDF (4,221).

* these results suggest that TextBlob tends to classify more dialogues as positive or negative compared to the custom TF-IDF method, which leans more towards neutral classifications
