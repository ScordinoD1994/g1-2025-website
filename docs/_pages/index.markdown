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
The video game industry is a multi-billion dollar global market, characterized by an ever-growing number of games and platforms. Despite the enormous interest, understanding which games will become successful and why remains a complex and multifaceted challenge. This project seeks to apply data science techniques to identify the key factors that contribute to the popularity and commercial success of video games. Through data-driven analysis, we aim to uncover hidden patterns and provide insights into the mechanics behind successful games.

## A crowded market
 For those unfamiliar with it, Steam is a digital distribution platform for PC games, created by Valve—the studio behind the iconic Half-Life, released in 1998. Steam itself launched in 2003 as a way to distribute updates and patches for Valve’s games. But in 2005, everything changed: Valve opened Steam to third-party developers, laying the groundwork for what would become the largest game storefront on the planet.
 
Steam’s early years were relatively modest. But in 2012, Valve introduced Steam Greenlight, a system that allowed indie developers to submit games for user voting. It dramatically lowered the barriers to entry and engaged the community in deciding what got published. Greenlight is often credited as the catalyst for the surge in game releases that followed.
 
Then came 2017, the year Steam removed almost all gatekeeping. With Steam Direct, any developer who submitted the required information and a small fee could publish a game without needing approval. The floodgates opened—and the platform was never the same. Since then, the number of games released each year has skyrocketed, peaking at over 18,000 new titles in 2024.
 
In just a decade, Steam transitioned from a curated digital store to an open bazaar—one where creativity thrives but discoverability becomes a brutal contest.

<img src='assets/images/steamdb_game_releases_per_year.png' width = 400>

![steam 2](assets/images/steamdb_game_releases_per_month.png)

<div class = "didascalia"> Didascalia </div>

Ciao
{ : .didascalia }


To ensure the relevance and interpretability of the results, this study focuses on Steam games that have a corresponding Metacritic page. This constraint helps isolate games that have surpassed a threshold of public and critical visibility, allowing the analysis to focus on factors associated with appreciation among both critics and players. While this approach may exclude certain under-the-radar indie successes, it enables a more consistent and interpretable comparison set. Future work may expand this scope to include the long tail of the Steam catalogue.

Of the games that reached Metacritic, not all of them managed to spark conversation. Many were released, reviewed by critics, and then seemingly disappeared into the digital void. To focus our analysis on games that actually reached players and provoked reactions, we removed any title that received zero user reviews.
 
This step helped us narrow the dataset down to games that were not just visible—but engaged with. After all, it’s hard to measure appreciation or popularity without a single player speaking up. Whether it’s praise, critique, or outright fury, we wanted games that left a footprint in the form of player feedback.
 



