---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: "Home"
vega: true
---

<div class="full-width-wrapper">
    <img src="{{ site.baseurl }}/assets/images/header.svg" alt="sbd-pattern" class="full-width-image">
</div>


# GAMEBRAKING
## Unlocking the data behind a videogame's success

**Navigation**

1. [Introduction](#1-Introduction)
2. [Popularity & Appreciation Scores](#2-Popularity-&-Appreciation-Scores)
3. [Indie vs Non-Indie](#3-Indie-vs-Non-Indie)
4. [Tag Analysis](#4-Tag-Analysis)
5. [Conclusions & Next Steps](#5-Conclusions-&-Next-Steps)
 
---

# Introduction
Steam, the world’s largest PC gaming platform, has transformed how games are made, discovered, and consumed. With thousands of titles launching every year, players and developers alike face a daunting question: **what makes a game successful**?
Success in gaming is no longer just about quality or even popularity alone. Some games attract massive player bases but struggle to earn positive reception. Others fly under the radar despite glowing reviews. Navigating this landscape requires moving beyond simple metrics like playtime or critic scores to understand the multidimensional dynamics of game performance.
In this article, we explore this question by analyzing a [curated dataset of Steam games](https://www.kaggle.com/datasets/fronkongames/steam-games-dataset) — specifically those that have a Metacritic page from 1997 to 2023. This criterion sets a minimum threshold of visibility, ensuring that we study games that have at least broken through the initial barrier of recognition and discourse.

## A crowded market

Steam’s growth over the past decade has been staggering. In 2023 alone, over 11,000 games were released on the platform — that’s **more than 30 games per day**. 

<figure style = "float:left; margin - right:1em;">
  <img src='assets/images/steamdb_game_releases_per_year.png' width = 500>
  <figcaption>Fig.1 - Game releases per year. Image from [SteamDB](https://steamdb.info/stats/releases/).</figcaption>
</figure>
<figure style = "float:right; margin - left:1em;">
  <img src='assets/images/steamdb_game_releases_per_month.png' width = 500>
  <figcaption>Fig.2 - Game releases per month. Image from [SteamDB](https://steamdb.info/stats/releases/).</figcaption>
</figure>


This deluge of content has created fierce competition for attention. For many games, even getting noticed is a monumental challenge.
To focus on titles that have reached some degree of exposure, we narrowed our dataset to the subset of Steam games with a Metacritic page. These are titles that have drawn at least some degree of critic and user attention — a crucial step toward both commercial and critical success.
But even within this more visible subset, the numbers tell a revealing story. While the absolute number of games with Metacritic pages has been steadily rising — nearly tripling since 2015 — their proportion relative to the total number of Steam releases has been declining. 

<figure>
  <img src='assets/images/metacritic_games_per_year.png' width = 500>
  <figcaption>Fig.3 - Metacritic games per year.</figcaption>
</figure>

In other words, as the flood of new releases grows, fewer of them are breaking through to earn critical attention.


## How players engage

Visibility is just the beginning. Among the games that are noticed, how do players actually engage with them?
We look at several metrics — like ownership counts, average playtime, and review volume — to measure different layers of engagement. While some games manage to draw large audiences and sustain long-term interest, many others are briefly sampled or abandoned altogether.

For example, a large share of games show very short average playtimes, with only a small fraction achieving sustained user engagement over time.

**NOTA**: qui mettiamo un plot a griglia che contiene total_avg_estimated_owners_per_year, tempo_medio_di_gioco_per_anno

Similarly, review activity tends to be highly concentrated: most games receive only a handful of reviews, while a few outliers collect thousands.

<figure style = "float:left; margin - right:1em;">
  <img src='assets/images/total_average_estimated_owners_per_year_plus_average_playtime_per_year.png' width = 500>
  <figcaption>Fig.4 - SteamDB game releases per month.</figcaption>
</figure>


