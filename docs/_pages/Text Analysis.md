---
layout: default
title: "Text Analysis"
subtitle: ""
---

<h1 class = "full-width-wrapper superH1"> Text Analysis </h1>

## Goal and data

For each of the games in our dataset, we scraped reviews from both critics and users from the relative Metacritic page. From each review we collected not only the text, but also the score, the platform and the date of posting. Our goal was to identify patterns derived from the review which could be tied to our custom variables of popularity and appreciation.

### Selection of datasets

Due to time constraints we limited our analysis to a small number of interesting subsets of games. In particular, we looked at:

<ul class = "in_text_list">
  <li> Top 15 Most Appreciated Indie Games </li>
  <li> Top 15 Most Popular Indie Games </li>
  <li> Top 15 Most Appreciated Non Indie Games </li>
  <li> Top 15 Most Popular Non Indie Games </li>
  <li> Top 15 Critic Score > User Score </li>
  <li> Top 15 User Score > Critic Score </li>
  <li> Top 15 High Popularity, Low Appreciation </li>
  <li> Top 15 High Appreciation, Low Popularity </li>
</ul>



### Preprocessing

Reviews on Metacritic are written in a variety of different languages, so prior to text analysis we translated to English all the reviews using the ***Google Translate API***.

To prepare reviews for analysis we applied some very basic text cleaning, using regular expressions to remove excessive punctuation and/or white spaces, as well as URLS (if present).

The number of reviews left, particularly by users, for certain games was extremely high (several thousands). The analysis of the whole review set would have been very expensive in terms of time and the number of calls to the ***Hugging Face's*** API. To remedy this issue we decided to cap the number of reviews per game to 500. For any game with more than 500 reviews, we have extracted a random sample of 500 out of the total.


## Hugging Face Models

With our text analysis we were looking for two things:

<ul class = "in_text_list">
  <li> Topic discussed by the reviewer </li>
  <li> Sentiment associated to each topic discussed </li>
</ul>

In order to achieve this we have used two different Hugging Face models


### BART - large

***Bidirectional Autoregressive Transformer (BART)*** is a transformer encoder-decoder trained on English language which can be effectively used for topic extractions task. Rather than any topic we asked the model to look for 7 specific topics of interest in the realm of video games:

<ul class = "in_text_list">
  <li> Gameplay </li>
  <li> Story and narrative </li>
  <li> Characters and dialogue </li>
  <li> Graphics and visuals </li>
  <li> Sound and music </li>
  <li> Technical Issues </li>
  <li> Price and value for money </li>
</ul>

The model returned then a list of topics found in each review and a confidence score associated to each topic. To establish an appropriate confidence score we inspected a number of reviews and their extracted topics and found that a threshold of 0.6 was the best compromise between recognising significant topics and discarding potentially misclassified (misrecognised?) ones.

### twitter-XLM-roBERTa-base
This is a ***BERT***-based model fine-tuned for sentiment analysis. We chose this particular model because it was trained on Twitter data, making it more suitable to the kind of informal language often found in video game reviews.
All reviews with identified topics (with a confidence level > 0.6) were passed to the ***twitter-roBERTa*** model using this focussed prompt: 

<p style = "text-align: center; padding: 10px; font-size: 1.2rem;"> 
    <code> In this review, the sentiment about {topic} is: {topic_review}. </code>
</p> 

So we were able to obtain a sentiment (**positive**, **neutral**, **negative**) for each topic in the review.

To check the performance of this model for sentiment analysis and to improve the explainability of our results we also extracted supporting sentences for each identified topic. For each extracted topic, the supporting sentences in each review were found with a keyword search. This was implemented using a dictionary containing a list keywords associated to each topic.

<figure>
  <img src='assets/images/final output of the text analysis on one review.png' width = 500>
  <figcaption class = "figcaption_class"> Fig.1 - Final output of the text analysis on one review. </figcaption>
</figure>


## Results

Aggregating the results from all the analysed reviews for each game, we were able to extract the number of mentions of each topic and their associated sentiments. The graph below shows a visualisation of the total mentions per topic, per game, which can be filtered to show the total mentions per topic and game by sentiment.

<figure>
  <img src='assets/images/final output of the text analysis on one review.png' width = 500>
  <figcaption class = "figcaption_class"> Fig.2 - Total mentions per topic, per game. </figcaption>
</figure>


