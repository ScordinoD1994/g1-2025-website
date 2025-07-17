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

<img src='assets/images/steamdb_game_releases_per_year.png' width = 600>

Then came 2017, the year Steam removed almost all gatekeeping. With Steam Direct, any developer who submitted the required information and a small fee could publish a game without needing approval. The floodgates opened—and the platform was never the same. Since then, the number of games released each year has skyrocketed, peaking at over 18,000 new titles in 2024.

<img src='assets/images/steamdb_game_releases_per_month.png' width = 600>

In just a decade, Steam transitioned from a curated digital store to an open bazaar—one where creativity thrives but discoverability becomes a brutal contest.

To ensure the relevance and interpretability of the results, this study focuses on Steam games that have a corresponding Metacritic page. This constraint helps isolate games that have surpassed a threshold of public and critical visibility, allowing the analysis to focus on factors associated with appreciation among both critics and players. While this approach may exclude certain under-the-radar indie successes, it enables a more consistent and interpretable comparison set. Future work may expand this scope to include the long tail of the Steam catalogue.

Of the games that reached Metacritic, not all of them managed to spark conversation. Many were released, reviewed by critics, and then seemingly disappeared into the digital void. To focus our analysis on games that actually reached players and provoked reactions, we removed any title that received zero user reviews.
 
This step helped us narrow the dataset down to games that were not just visible—but engaged with. After all, it’s hard to measure appreciation or popularity without a single player speaking up. Whether it’s praise, critique, or outright fury, we wanted games that left a footprint in the form of player feedback.
 

## How players engage

The growth of the player base in the past decade is undoubtedly impressive. With more casual gamers joining the hardcore gamers, as well as more options of games, there’s no doubt that the expectations will make it harder for game developers to keep up.
 
The year 2013 seemed to be a turning point because both player base and their average playtime per game showed a clear decline afterward. From our previous discussion, we know that this is also where the Steam game library started to explode. So it seems that the ballooned game library failed to attract more players or playtime from them. It clearly says something about the game quality in general.
 
What catches the attention here is the unreal spike of playtime in 2000. Similar but much smaller spikes also happened in 1998, 2004, and 2013. Let’s zoom in and see what happened in those years.
 
The y-axis shows the average playtime per game, and the size of the dots shows the size of the player base for that particular game.
 
Now the answer is clear. Those spikes in playtime were results of the greatest hits in game history.
 
“Half-Life” was the cornerstone that brought fame and wealth to Valve in the first place. “Counter-Strike” was the legendary first-person shooter (FPS) game that took the world by storm. That explains the unreal spike of playtime in 2000, and no wonder why its sequel caused another spike in 2004. 2013 was backed up by “Dota 2” with one of the largest player base on Steam.
 
 
While sales and reviews reflect a game’s immediate success, the number of users who log a play on platforms like Backloggd offers a window into long-term engagement. When we look at the average number of plays per game by release year, the data tells a familiar story: standout years in video game history continue to echo through the habits of modern players.
 
Notably, 1998—the year of genre-defining titles like Half-Life—shows the highest average play counts, underscoring its enduring cultural legacy. Similar spikes appear in 2004, 2007, and the early 2010s, reflecting the lasting impact of titles such as Half-Life 2 and Portal. Even as the number of annual releases exploded in the late 2010s, the average plays per game saw a decline, suggesting a saturation point: more games are being released, but fewer stand out as lasting experiences.
 
In essence, the Backloggd play data reinforces a key idea already hinted at by ownership metrics—many of the most played games today were not released recently, but have proven their relevance across decades.
 
One of the clearest signs of a game's cultural impact is the moment it draws the most people in at once. The maximum number of concurrent players on Steam provides a powerful snapshot of that peak — capturing the precise moment when excitement, community buzz, and player interest all converged.
 
This metric reveals fascinating patterns over time. In 2012, Counter-Strike: Global Offensive exploded with over 1.8 million simultaneous players, while Dota 2 followed closely in 2013 with over 1.2 million. More recently, Lost Ark (2022) and New World (2021) reached similarly massive peaks, reflecting the growing scale of online communities. Earlier titles, like POSTAL (1997) or Legacy of Kain: Soul Reaver (1999), show much smaller numbers — a reflection not of their relevance, but of the era's limited infrastructure and reach.
 
While these values don't tell the full story of a game's lifespan or quality, they offer a compelling glimpse into moments when a title truly dominated players’ attention.
 
In addition to playtime and estimated ownership, user reviews are one of the clearest indicators of how much attention a game has received. Steam reviews are both a signal of reach and community engagement. However, as the following plots show, this engagement is heavily skewed: while a small number of games accumulate tens of thousands of reviews, the vast majority receive very few — or none at all.
 
While thousands of games are released on Steam each year, only a small fraction capture the majority of user engagement. Based on user review counts, just 170 games have earned over 100,000 reviews, while nearly 1,600 titles sit in the modest 100–999 review range. The most common group — around 1,800 games — falls between 1,000 and 9,999 reviews. Meanwhile, 345 games remain virtually unseen, with fewer than 100 reviews to their name.
 
This stark imbalance in attention underscores the platform’s highly competitive landscape, where visibility and engagement are far from evenly distributed. The vast majority of games struggle for recognition, while a few dominate the discourse and player feedback.

As the number of games released each year on Steam surged throughout the 2010s, so did the spread of user reviews — but not evenly. Early years like 1997 to 2004 saw only a handful of games reach higher review brackets. From 2010 onward, however, the landscape shifted: each year brought dozens of new titles amassing between 10,000 and 99,999 reviews, while a select few — often high-profile releases — crossed the 100,000 mark.
 
Still, most games remained in lower tiers. In 2020 alone, while 24 games surpassed 100,000 reviews, over 180 were in the 1,000–9,999 range, and 35 had fewer than 100 reviews. The disparity between visibility and obscurity has widened alongside the volume of releases, underscoring a platform defined by both runaway hits and forgotten titles.




