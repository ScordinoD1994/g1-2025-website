---
layout: default
title: "Data Gathering"
subtitle: ""
vega: true
---

<h1 class = "full-width-wrapper superH1"> Data Gathering </h1>

In this project we have used two types of data: tabular data, obtained merging data from a variety of sources and textual data, scraped from Metacritic.

For tabular data, we started from a dataset publicly available on Kaggle (<a href="">Steam Games Dataset</a>), containing aggregated information on the whole Steam catalogue as of April 2024. This data was supplemented with:

<ul class = "in_text_list">
    <li> *data* collected from <b>SteamSpy</b> using its API; </li>
    <li> *data* collected from <b>steam_trends_2023</b>; </li>
    <li> wish lists scraped from <b>Backloggd</b> using <b>Beautiful Soup</b>; </li>
    <li> users and critics scores scraped from Metacritic. </li>
</ul>

This data, gathered from different sources, was then merged into a single dataset using the game's Steam ID as unique identifier.

The original dataset contained more than *90,000 games*, but we filtered it by considering only games with a Metacritic page. This allowed us to consider only games with a certain market visibility, also taking care of a large amount of missing values present in the Kaggle dataset for less renowned games. Finally, considering we only had partial data available for 2024, we removed all games released in 2024 from the dataset.

All the data used for review and text analysis was scraped from Metacritic using **Selenium**.

*If games were removed from the dataset due to a lack of user reviews on Metacritic, please add a line to say this*


