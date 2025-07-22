---
layout: default
title: "Data Gathering"
subtitle: ""
vega: true
---

<h1 class = "full-width-wrapper superH1"> Data Gathering </h1>

Our modeling dataset was built from the <a href="https://www.kaggle.com/datasets/fronkongames/steam-games-dataset?select=games.csv">Steam Kaggle dataset</a>, enhanced with external sources including <a href="https://steamspy.com">SteamSpy</a>, <a href="https://steamcharts.com">SteamCharts</a>, <a href="https://backloggd.com">Backloggd</a>, and <a href="https://www.metacritic.com/game/">Metacritic</a>. 

In particular, using SteamSpy API we updated the following attributes:

<ul class = "in_text_list">
    <li> <var> positive </var>: number of postive reviews from Steam </li>
    <li> <var> negative </var>: number of negative reviews from Steam  </li>
    <li> <var> owners </var>: number of estimated owners for each Steam game </li>
    <li> <var> average_forever </var>: average playtime in minutes per game </li>
    <li> <var> median_forever </var>: median playtime in minutes per game </li>
    <li> <var> price </var>: Steam current price </li>
    <li> <var> initialprice </var>: Steam launch price </li>
    <li> <var> discount </var>: discount percentage on Steam </li>
    <li> <var> ccu </var>: maximum number of concurrent player in the last 24 hours </li>
    <li> <var> languages </var>: list of languages in which each game has been translated </li>
    <li> <var> genre </var>: Steam genres associated to each game </li>
    <li> <var> tags </var>: Steam tags assigned to each game </li>
</ul>

From SteamChart, using <a href="https://www.crummy.com/software/BeautifulSoup/bs4/doc/">Beautiful Soup</a>, we scraped <var> all-time peak </var> which represents the maximum number of concurrent players for a game starting from the release date. 

Finally, from Backloggd we scraped the following data:

<ul class = "in_text_list">
    <li> <var> Played </var>: number of times a game has been played </li>
    <li> <var> Playing </var>: number of current players </li>
    <li> <var> Backlogs </var>: number of times in which a game has been bought but not played even once </li>
    <li> <var> Wishlist </var>: number of times in which a game has been put in a wishlist </li>
    <li> <var> Lists </var>: number of times in which a game appears in user-made list </li>
    <li> <var> Reviews </var>: number of reviews for each game on Backloggd </li>
    <li> <var> Likes </var>: likes number </li>
    <li> <var> Platforms </var>: list of platforms on which a game has been released </li>
</ul>

From Metacritic, using <a href="https://selenium-python.readthedocs.io/">Selenium</a>, we scraped for each game 

<ul class = "in_text_list">
    <li> <var> Metascore </var>: average critics rating </li>
    <li> <var> User Score </var>: average users rating </li>
    <li> <var> Total number of reviews for critics and users </var> </li>
    <li> <var> Reviews from critic and users (with their score, date and platform) </var> </li>
</ul>

The final dataset contained more than <b>90,000 games</b>, but we filtered it by considering only games with a Metacritic page reducing its size to around <b>5,000</b> games. This allowed us to consider only games with a certain market visibility, also taking care of a large amount of missing values present in the Kaggle dataset for less renowned games. Finally, considering we only had partial data available for 2024, we removed all games released in 2024 from the dataset. We also removed from the dataset games not having user reviews on Metacritic (this reduced the datased to <b>4878</b> games). 



