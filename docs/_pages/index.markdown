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

![steam 1](assets/images/steamdb_game_releases_per_year.png)

![steam 2](assets/images/steamdb_game_releases_per_month.png)


<div style="height: 400px">
<vegachart schema-url="/g1-2025-website/assets/charts/metacritic.json" style="width: 100%; height: 100%"></vegachart>
</div>


