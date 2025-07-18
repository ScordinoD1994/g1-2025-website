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


# GAMEBRAKING - Unlocking the data behind a videogame's success

**Table of content**

<nav aria-label = "primary-navigation">
    <ol>
        <li> <a href="#A crowded market"> A crowded market </a> </li>
        <li> <a href="#Popularity & Appreciation Scores"> Popularity & Appreciation Scores </a> </li>
        <li> <a href="#Tag Analysis"> Tag Analysis </a> </li>
        <li> <a href="#Conclusions & Next Steps"> Conclusions & Next Steps </a> </li>
    </ol>
</nav>


---


Steam, the world’s largest PC gaming platform, has transformed how games are made, discovered, and consumed. With thousands of titles launching every year, players and developers alike face a daunting question: **what makes a game successful**?
Success in gaming is no longer just about quality or even popularity alone. Some games attract massive player bases but struggle to earn positive reception. Others fly under the radar despite glowing reviews. Navigating this landscape requires moving beyond simple metrics like playtime or critic scores to understand the multidimensional dynamics of game performance.
In this article, we explore this question by analyzing a [curated dataset of Steam games](https://www.kaggle.com/datasets/fronkongames/steam-games-dataset) — specifically those that have a Metacritic page from 1997 to 2023. This criterion sets a minimum threshold of visibility, ensuring that we study games that have at least broken through the initial barrier of recognition and discourse.

# A crowded market

Steam’s growth over the past decade has been staggering. In 2023 alone, over 11,000 games were released on the platform — that’s **more than 30 games per day**. 

<figure style = "float:left; margin - right:1em;">
  <img src='assets/images/steamdb_game_releases_per_year.png' width = 500>
  <figcaption class = "figcaption_class">Fig.1 - Game releases per year. Image from <a href="https://steamdb.info/stats/releases/">SteamDB</a>.</figcaption>
</figure>
<figure style = "float:left; margin - right:1em;">
  <img src='assets/images/steamdb_game_releases_per_month.png' width = 500>
  <figcaption class = "figcaption_class">Fig.2 - Game releases per month. Image from <a href="https://steamdb.info/stats/releases/">SteamDB</a>.</figcaption>
</figure>

This deluge of content has created fierce competition for attention. For many games, even getting noticed is a monumental challenge.
To focus on titles that have reached some degree of exposure, we narrowed our dataset to the subset of Steam games with a Metacritic page. These are titles that have drawn at least some degree of critic and user attention — a crucial step toward both commercial and critical success.
But even within this more visible subset, the numbers tell a revealing story. While the absolute number of games with Metacritic pages has been steadily rising — nearly tripling since 2015 — their proportion relative to the total number of Steam releases has been declining. 

<figure>
  <vegachart schema-url="/g1-2025-website/assets/charts/metacritic_games_per_year.json" style="width: 100%; height: 100%"></vegachart>
  <figcaption class = "figcaption_class">Fig.3 - Metacritic games per year.</figcaption>
</figure>

In other words, as the flood of new releases grows, fewer of them are breaking through to earn critical attention.


## How players engage

Once a game is released on Steam, how do players actually engage with it? We examined three key signals: **estimated ownership**, **average playtime**, **review counts**, each revealing a different aspect of how attention and interest unfold. First, the total estimated number of owners has increased steadily over the years, showing that even as the platform grows more crowded, many games are still managing to reach players — often helped by bundles, deep discounts, or seasonal promotions. However, the gains are far from evenly distributed.

When we look at average playtime over time, a subtle but important shift emerges: newer games tend to see shorter engagement windows compared to older titles. Whether due to time constraints, the abundance of available alternatives, or changing player habits, it's clear that player attention is fragmenting.

<figure>
  <vegachart schema-url="/g1-2025-website/assets/charts/total_average_estimated_owners_per_year_plus_average_playtime_per_year.json" style="width: 100%; height: 100%; align-items: center;"></vegachart>
  <figcaption class = "figcaption_class">Fig.4 - Total average estimated owners (left plot) and average playtime per year (right plot).</figcaption>
</figure>

Some noticeable spikes in the data trace back to landmark releases. The peaks in average playtime seen in years like 1998, 2000, 2001, 2003, and 2004 align with the launches of enduring classics like *Half-Life*, *Counter-Strike* *Half-Life: Blue Shift*, *Day of Defeat*, and *Counter-Strike: Source*. These titles have maintained active player bases over decades, skewing the average upward. Similarly, the sharp rise in estimated ownership in 2013 is largely attributable to *Dota 2*, a free-to-play phenomenon that brought millions of players onto Steam and became a pillar of its ecosystem.

<figure>
  <vegachart schema-url="/g1-2025-website/assets/charts/explain_spikes.json" style="width: 100%; height: 100%" ></vegachart>
  <figcaption class = "figcaption_class">Fig.5 - Spikes breakdown.</figcaption>
</figure>

Finally, we explored review activity by looking at the distribution of the number of user reviews per game. The pattern here is starkly unequal: most games receive very few reviews, while a select few attract thousands. This distribution — like ownership and playtime — reflects a highly competitive ecosystem, where visibility and player feedback are dominated by a small percentage of releases.
Together, these trends reveal how player engagement is both growing and concentrating, offering opportunities for breakout hits, but also highlighting the steep climb most games face after launch.

<figure>
  <vegachart schema-url="/g1-2025-website/assets/charts/reviews_distribution_plus_reviews_bucket_per_released_games.json" style="width: 100%; height: 100%"></vegachart>
  <figcaption class = "figcaption_class">Fig.6 - Review distribution.</figcaption>
</figure>

Understanding how much a game is liked is not as straightforward as it might seem. Appreciation can’t be distilled into a single number, but the industry has long leaned on a few core metrics. On Metacritic, two scores are typically available: the critic score, based on professional reviews, and the user score, submitted by players. On Steam, the main visible indicator of satisfaction is the positive review ratio—the share of user reviews marked as “positive”. 
Each of these metrics, however, tells a slightly different story. Critic scores tend to cluster around the higher end of the scale. Reviewers often avoid the harshest ratings, leading to a compressed distribution with fewer low scores and a bias toward the 70–90 range. User scores, on the other hand, are more variable. Players are not shy about expressing dissatisfaction, resulting in a broader spread that includes more low-rated games. The contrast becomes clear when the two are plotted together—players are often harsher, and sometimes more polarized.

<figure>
  <vegachart schema-url="/g1-2025-website/assets/charts/critic_plus_user_score.json" style="width: 100%; height: 100%"></vegachart>
  <figcaption class = "figcaption_class">Fig.7 - Metacritic critic score (left plot) and user score (right plot) distributions.</figcaption>
</figure>

Then there’s the Steam positive ratio, which differs not just in scale but in nature. Steam reviews operate on a binary system —“thumbs up” or “thumbs down”— which strips away nuance and skews the distribution dramatically. Most games that gather reviews at all tend to be favored, so the ratio is heavily biased toward high values. In many cases, even moderately liked games can end up with “Very Positive” labels, suggesting that this metric alone might not capture the full spectrum of appreciation.

<figure>
  <vegachart schema-url="/g1-2025-website/assets/charts/steam_positive_review_ratio.json" style="width: 100%; height: 100%"></vegachart>
  <figcaption class = "figcaption_class">Fig.8 - Steam positive review ration distribution with review segmentation.</figcaption>
</figure>

These differences highlight the challenge of evaluating player sentiment in a consistent way. Each metric provides a piece of the puzzle, but none offers the full picture. This tension points to the need for more robust, composite measurements—an effort we take up in the next section, where we move toward defining appreciation and popularity as integrated, quantifiable outcomes.

<figure style = "float:left; margin - right:1em;">
  <vegachart schema-url="/g1-2025-website/assets/charts/metacritic_score_difference.json" style="width: 100%; height: 100%"></vegachart>
  <figcaption class = "figcaption_class">Fig.9 - Difference between critic and user metacritic scores.</figcaption>
</figure>

Beyond the general trends, some games exhibit striking discrepancies between critic and user evaluations. In our dataset, we found a substantial number of titles where the difference between the two scores exceeds 20 points on a 100-point scale—sometimes even more than 30. These outliers can reflect cases where critics and players approached the game from entirely different perspectives: technical polish vs. emotional resonance, innovation vs. nostalgia, or even divergent expectations shaped by marketing.
Analyzing these outliers in more detail could offer valuable insights into the dynamics of reception—what drives such a divide, and what it reveals about the varying standards of professional reviewers and general audiences.

<figure>
  <vegachart schema-url="/g1-2025-website/assets/charts/user_vs_critic_score_by_difference.json" style="width: 100%; height: 100%"></vegachart>
  <figcaption class = "figcaption_class">Fig.10 - Users vs critic score on Metacritic.</figcaption>
</figure>





## Measuring Popularity & Apprection





# Tag Analysis

Lorem ipsum...


# Popularity & Appreciation Scores

Lorem ipsum...


# Conclusions & Next Steps

Lorem ipsum...



