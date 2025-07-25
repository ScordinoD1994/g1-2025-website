---
layout: default
title: "Text Analysis"
subtitle: ""
vega: true
---

<div class="full-width-wrapper">
    <img src="{{ site.baseurl }}/assets/images/header.svg" alt="sbd-pattern" class="full-width-image filter-green">
</div>

<h1 class = "full-width-wrapper superH1"> Text Analysis </h1>

<figure style = "padding: 40px;">
  <img src='assets/images/pacman_separator.png' style = "width: 100%">
</figure>

## Goal and data

For each of the games in our dataset, we scraped reviews from both critics and users from the relative Metacritic page. From each review we collected not only the text, but also the score, the platform and the date of posting. Our goal was to identify patterns, derived from the reviews, which could be tied to our custom variables of popularity and appreciation.

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

Reviews on Metacritic are written in a variety of different languages, so prior to text analysis we translated to English all the reviews using the Goole Translate API. In addition, to prepare reviews for analysis with Hugging Face models, we applied some very basic text cleaning, using regular expressions to remove excessive punctuation and/or white spaces, as well as URLS (if present).

We also had to cap the number of reviews analysed per game. The number of reviews left, particularly by users, for particularly popular games was extremely high (several thousands). The analysis of the whole review set would have been very expensive, both in terms of time and the number of calls to the Hugging Face's API. To remedy this issue we decided to limit the number of analysed reviews per game to 500. For any game with more than 500 reviews, we have extracted a random sample of 500 out of the total to use for analysis.


## Hugging Face Models

Our analysis of game reviews aimed to extract the following information:

<ul class = "in_text_list">
  <li> Topic discussed by the reviewer </li>
  <li> Sentiment associated to each topic discussed </li>
</ul>

In order to achieve this we have used two different Hugging Face models


### BART - large

***Bidirectional Autoregressive Transformer (BART)*** is a transformer encoder-decoder trained on English language which can be successfully used for topic extractions task. Rather than letting the model extract any topic we specifically prompted it to look for 7 topics of interest in the realm of video games:

<ul class = "in_text_list">
  <li> Gameplay </li>
  <li> Story and narrative </li>
  <li> Characters and dialogue </li>
  <li> Graphics and visuals </li>
  <li> Sound and music </li>
  <li> Technical Issues </li>
  <li> Price and value for money </li>
</ul>

The model returned a list of topics found in each review and a confidence score associated to each topic. To establish an appropriate confidence score, we inspected a number of reviews and their extracted topics and found that a threshold of 0.6 was the best compromise between recognising significant topics and discarding potential red herrings. 

### twitter-XLM-roBERTa-base
This is a ***BERT***-based model fine-tuned for sentiment analysis. We chose this particular model because it was trained on Twitter data, making it more suitable to the kind of informal language often found in video game reviews.
All reviews with identified topics (with a confidence level > 0.6) were passed to the twitter-roBERTa model using this focussed prompt 

<p style = "text-align: center; padding: 10px; font-size: 1.2rem;"> 
    <code> In this review, the sentiment about {topic} is: {topic_review}. </code>
</p> 

The model returned then a sentiment (**positive**, **neutral**, **negative**) for each topic in the review, together with a confidence score. We observed that confidence scores for the returned sentiments were mostly greater than 0.9; lower confidence scores were mostly observed for neutral sentiments in general and for positive and neutral sentiments in the *technical issues* topic.

<figure>
  <div class = "general_chartClass">
    <img src='assets/images/neutral_sentiment.png' width = 500>
  </div>
  <figcaption class = "figcaption_class"> Fig.1 - An example of sentiment confidence scores on neutral sentiment. </figcaption>
</figure>

To check the performance of this model for sentiment analysis and to improve the explainability of our results we also extracted supporting sentences for each identified topic. For each extracted topic, the supporting sentences in each review were found with a keyword search. This was implemented using a dictionary containing a list keywords associated to each topic.

<figure>
  <div class = "general_chartClass">
    <img src='assets/images/final output of the text analysis on one review.png' width = 500>
  </div>
  <figcaption class = "figcaption_class"> Fig.2 - Final output of the text analysis on one review. </figcaption>
</figure>


## Results

Aggregating the results from all the analysed reviews for each game, we were able to extract the number of mentions of each topic and their associated sentiments. The graph below shows a visualisation of the sentiments associated to both users and critics comments. Critics comments tend to be more positive overall in the dataset we have analysed.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/totalSentimentCounts.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.3 - Left: Number of comments per sentiment and reviewer type. Right: percentage of comments by sentiment and reviewer type. </figcaption>
</figure>

The graph below shows a visualisation of the total mentions per topic, per game, based on the sentiment of the comment (positive, negative or neutral). Both comments from critic and user reviews were included.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/AllReviews_countsAndSentiment.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.4 - Total mentions per topic, per game. The dropdown menu can be used to change the sentiment. </figcaption>
</figure>

The most common topic of discussion, both in positive and negative is, probably unsurprisingly, the gameplay. We can also see that the most negative comments are found in technical issues and price and value for money. Excluding the gameplay, it seems that, out of the topics we have analysed, both users and critics are mostly concerned with story and narrative and graphics and visuals, while characters and dialogue and music and sound are of secondary importance.

A more detailed summary view of all the reviews we have analysed can be had by exploiting the chart below. The dropdown menu will change between user and critic reviews, while clicking on the topic columns will show the sentiment breakdown of the comments.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/emojiChart_wholeDataset.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.5 - Left: Total mention by topic. Right: Sentiment breakdown by topic. The dropdown menu can be used to switch between users and critics. </figcaption>
</figure>




