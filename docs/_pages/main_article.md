---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: "Main Article"
vega: true
---

<div class="full-width-wrapper">
    <img src="{{ site.baseurl }}/assets/images/header.svg" alt="sbd-pattern" class="full-width-image filter-green">
</div>


<h1 class = "full-width-wrapper superH1"> GAMEBREAKING </h1>
<h4 class = "full-width-wrapper superSubTitle"> Unlocking the data behind a videogame's success </h4>


<div class = "full-width-wrapper toc_container">
  <nav class = "toc">
  <h5>Table of contents</h5>
      <ol>
          <li> <a href="#A crowded market">A crowded market</a> </li>
          <ul>
            <li> <a href="#How players engage">How players engage</a> </li>
          </ul>
          <li> <a href="#Measuring Success">Measuring Success</a> </li>
          <ul>
            <li> <a href="#Popularity Score">Popularity Score</a> </li>
            <li> <a href="#Appreciation Score">Appreciation Score</a> </li>
            <li> <a href="#Appreciation-Popularity Plane">Appreciation-Popularity Plane</a> </li>
          </ul>
          <li> <a href="#Indie vs Non-Indie">Indie vs Non-Indie</a> </li>
          <li> <a href="#Steam tags analysis">Steam tags analysis</a> </li>
          <li> <a href="#Predicting Success?">Predicting Success?</a> </li>
          <ul>
            <li> <a href="#Predicting popularity">Predicting popularity</a> </li>
            <li> <a href="#Predicting appreciation">Predicting appreciation</a> </li>
            <li> <a href="#Predicting success">Predicting both popularity and appreciation</a> </li>
          </ul>
          <li> <a href="#Conclusions">Conclusions</a> </li>
      </ol>
  </nav>
</div>

<!-- 
<div class = "container_abstract">
  <div style = "padding: 15px;">
    <p>
      Steam, the world’s largest PC gaming platform, has transformed how games are made, discovered, and consumed. With thousands of titles launching every year, players and developers alike face a daunting question:
    </p> 
    <p style = "text-align: center; padding: 10px; font-size: 1.6rem; font-style: italic; font-weight: bold;"> 
      <q> What makes a game successful? </q>
    </p>
    <p>
      Success in gaming is no longer just about quality or even popularity alone. Some games attract massive player bases but struggle to earn positive reception. Others fly under the radar despite glowing reviews. Navigating this landscape requires moving beyond simple metrics like playtime or critic scores to understand the multidimensional dynamics of game performance.
      In this article, we explore this question by analyzing a <a href = "https://www.kaggle.com/datasets/fronkongames/steam-games-dataset">curated dataset of Steam games</a> and specifically those that have a <a href = "https://www.metacritic.com/game/">Metacritic</a> page from 1997 to 2023. This criterion sets a minimum threshold of visibility, ensuring that we study games that have at least broken through the initial barrier of recognition and discourse.
    </p>
  </div>
</div>
-->



<h1 id = "A crowded market"> A crowded market </h1>

Steam’s growth over the past decade has been staggering. In 2023 alone, over 11,000 games were released on the platform — that’s **more than 30 games per day**. 

<figure>
  <img src='assets/images/steamdb_game_releases_per_year.png' style = "width: 100%">
  <figcaption class = "figcaption_class"> Fig.1 - Game releases per year. Image from <a href="https://steamdb.info/stats/releases/">SteamDB</a>. </figcaption>
</figure>
<figure>
  <img src='assets/images/steamdb_game_releases_per_month.png' style = "width: 100%">
  <figcaption class = "figcaption_class"> Fig.2 - Game releases per month. Image from <a href="https://steamdb.info/stats/releases/">SteamDB</a>. </figcaption>
</figure>

This deluge of content has created fierce competition for attention. For many games, even getting noticed is a monumental challenge.
To focus on titles that have reached some degree of exposure, we narrowed our dataset to the subset of Steam games with a Metacritic page. These are titles that have drawn at least some degree of critic and user attention — a crucial step toward both commercial and critical success.
But even within this more visible subset, the numbers tell a revealing story. While the absolute number of games with Metacritic pages has been steadily rising — nearly tripling since 2015 — their proportion relative to the total number of Steam releases has been declining. 


***title*** The number of Metacritic pages for games has been increasing over the years

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/metacritic_games_per_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.3 - Games with a Metacritic page per year. </figcaption>
</figure>

In other words, as the flood of new releases grows, fewer of them are breaking through to earn critical attention.


<h2 id="How players engage"> How players engage </h2>

Once a game is released on Steam, how do players actually engage with it? We examined three key signals: **estimated ownership**, **average playtime**, **review counts**, each revealing a different aspect of how attention and interest unfold. First, the total estimated number of owners has increased steadily over the years, showing that even as the platform grows more crowded, many games are still managing to reach players — often helped by bundles, deep discounts, or seasonal promotions. However, the gains are far from evenly distributed.

When we look at average playtime over time, a subtle but important shift emerges: newer games tend to see shorter engagement windows compared to older titles. Whether due to time constraints, the abundance of available alternatives, or changing player habits, it's clear that player attention is fragmenting.

***Title*** As the number of owned games increases, average playtime decreases

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/total_average_estimated_owners_per_year_plus_average_playtime_per_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.4 - Top: Total average estimated owners; Bottom: Average playtime per year. </figcaption>
</figure>

Some noticeable spikes in the data trace back to landmark releases. The peaks in average playtime seen in years like 1998, 2000, 2001, 2003, and 2004 align with the launches of well-loved classics like ***Half-Life***, ***Counter-Strike***, ***Half-Life: Blue Shift***, ***Day of Defeat***, and ***Counter-Strike: Source***. These titles have maintained active player bases over decades, skewing the average upward. Similarly, the sharp rise in estimated ownership in 2013 is largely attributable to *Dota 2*, a free-to-play phenomenon that brought millions of players onto Steam and became a pillar of its ecosystem.


<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/explain_spikes.json"></vegachart>
  </div>  
  <figcaption class = "figcaption_class"> Fig.5 - Spikes breakdown. </figcaption>
</figure>

Finally, we explored review postings by looking at the distribution of the number of user reviews per game. The pattern here shows clear inequalities: most games receive very few reviews, while a select few attract thousands. This distribution — like ownership and playtime — reflects a highly competitive ecosystem, where visibility and player feedback are dominated by a small percentage of releases.
Together, these trends reveal how player engagement is both growing and concentrating **better explanation needed**, offering opportunities for breakout hits, but also highlighting the steep climb most games face after launch.

***Title*** The majority of games only receives a small number of reviews

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/reviews_distribution_plus_reviews_bucket_per_released_games.json"></vegachart>
  </div>  
  <figcaption class = "figcaption_class"> Fig.6 - Top: Total distribution of games based on their number of reviews. Bottom: Distribution of games based on their number of reviews per year </figcaption>
</figure>

Understanding how much a game is liked by players is not as straightforward as it might seem. As Fortuna Imperatore underscores,

<blockquote class = "expert_quote">
  "The recipe is very difficult to find, considering that a developer's impossible task is to respond to the needs of society at that historical moment."
</blockquote>

Enjoyment and recognition cannot be condensed in a single number, but scores meant to summarise the quality of a game are readily available. On Metacritic, two scores are typically available: the critic score, based on professional reviews, and the user score, submitted by players. On Steam, the main visible indicator of satisfaction is the positive review ratio — the share of user reviews marked as “positive”. 
Caution must be exercised, however, when taking these numbers at face value. Critic scores tend to cluster around the higher end of a scale that ranges from 0 to 100. Reviewers often avoid the harshest ratings, leading to a compressed distribution with fewer low scores and a bias toward the 70–90 range. As Andrea Porta explains,

<blockquote class = "expert_quote">
  "This is usually the case because journalists can sometimes feel a significant responsibility when assigning a very low score to highly anticipated titles. Such a dynamic is very real and has deep roots within the video game critics landscape, which currently grapples with substantial financial challenges."
</blockquote>

User scores, on the other hand, are more varied. Players are not shy about expressing dissatisfaction, resulting in a broader spread that includes more low-rated games. The contrast becomes clear when the two are plotted together; players are often harsher, and sometimes more polarised.


***Title*** Users tend to give lower scores compared to critics

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/critic_plus_user_score.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.7 - Left: Metacritic critic score distribution. Right: Metacritic user score distribution. </figcaption>
</figure>

Then there’s the Steam positive ratio, which is quite different in nature. Steam reviews operate on a binary system —“thumbs up” or “thumbs down” — which strips away nuance and skews the distribution dramatically. Most games that gather reviews at all tend to be favored, so the ratio is heavily biased toward high values. In many cases, even moderately liked games can end up with “Very Positive” labels, suggesting that this metric alone might not capture the full spectrum of appreciation.

***Title*** The positive ratio is not heavily influenced by the number of reviews left on Steam

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/steam_positive_review_ratio.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.8 - Steam positive review ratio distribution with review segmentation. </figcaption>
</figure>

These differences highlight the challenge of evaluating player sentiment in a consistent way. Each metric provides a piece of the puzzle, but none offers the full picture. This tension points to the need for more robust, composite measurements—an effort we take up in the next section, where we move toward defining appreciation and popularity as integrated, quantifiable outcomes.


Beyond the general trends, some games exhibit striking discrepancies between critic and user evaluations. In our dataset, we found a substantial number of titles where the difference between the two scores exceeds 20 points on a 100-point scale—sometimes even more than 30. 


<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/metacritic_score_difference.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.9 - Difference between critic and user metacritic scores. </figcaption>
</figure>

These outliers can reflect cases where critics and players approached the game from entirely different perspectives: technical polish vs. emotional resonance, innovation vs. nostalgia, or even divergent expectations shaped by marketing.
Analyzing these outliers in more detail could offer valuable insights into the dynamics of reception—what drives such a divide, and what it reveals about the varying standards of professional reviewers and general audiences. 

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/user_vs_critic_score_by_difference.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.10 - Users vs critic score on Metacritic. </figcaption>
</figure>

We have dived a little more deeply into this topic, by analysing game reviews for the top 15 games where critics' and users' scores differred the most.

In the case of games that have received more critic's praise than user's love, the most talked about category, gameplay, has received mostly negative mentions from users, even for games with plenty of positive critics mentions. Price and value for money is also a point of contention; looking at critics reviews, all games received mostly positive mentions with respect to this topic. For users this is the second most talked about topic, but in a decidedly negative perspective. It is also interesting to note that both critics and users had plenty of comments to make about technical issues, which are mostly negative; however, it seems that critics did not find these issues to be relevant enough to impact the game, while users might have had a different view.

In the case of games that have received more love from the users than from the critics, it is not surprising to see that most user comments are positive across all categories, however, it is more difficult to spot any obvious trend. For some games, like Cortex Command or Disney Pixar WALL-E, users and critics focussed their reviews on different aspects of the games altogether, demonstrating a differing interests in the game features. For other games, like 7 Days to Die or Knock-knock, it seems that users were far less harsh in their judgements compared to critics.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/CriticScore_diff_UserScore.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.11 - Heatmaps showing density of mentions per topic, per game, plus histograms showing each topic sentiment breakdown. The dropdown menu can be used to change the dataset. </figcaption>
</figure>



<h1 id = "Measuring Success"> Measuring Success </h1>

With thousands of games released each year and player attention more fragmented than ever, relying on a single dimension to evaluate a game’s success is limiting. A high number of owners does not necessarily mean players enjoyed the experience; a strong review ratio might come from a niche but passionate fanbase. Conversely, a critically acclaimed title might fail to attract a meaningful audience. In such a complex ecosystem, success is multidimensional and it becomes crucial to disentangle its components.

To this end, we introduce two composite indicators: ***Popularity*** and ***Appreciation***. These scores aim to summarise multiple attributes into meaningful, interpretable indicators. Popularity combines a game’s visibility, reach, and commercial uptake (through ownership, wishlisting, and review counts), while appreciation reflects how well a game is received once it's played (via various types of ratings).

This dual-axis approach allows for a more nuanced understanding of a game's position in the market: whether it is loved but overlooked, widely played but polarising, or among that group that is both popular and appreciated. In the sections that follow, we explore how these indicators behave, what patterns emerge, and what features seem to shape a game's trajectory across these axes.

<h2 id="Popularity Score"> Popularity Score </h2>

Popularity in the gaming world is more than just raw sales. It’s a combination of visibility, engagement, and community presence. To capture this complex reality, we created a composite ***Popularity Score*** using data from both Steam and gaming databases like Metacritic and Backloggd.
We identified ten core indicators of attention, ranging from how many people bought or played a game, to how often it was reviewed or recommended. These included:

<ul class = "in_text_list">
  <li> Player activity metrics like peak concurrent users (24h and all-time) </li>
  <li> Estimated number of owners </li>
  <li> Steam review counts (total and recommendations) </li>
  <li> Engagement on Backloggd (plays, backlogs, reviews) </li>
  <li> Number of critic and user reviews on Metacritic </li>
</ul>

Because these numbers can vary wildly between indie successes and AAA blockbusters, we applied a logarithmic transformation to scale them more evenly. Then, we used ***Principal Component Analysis (PCA)*** to synthesize these features into a single, unified score (which is then normalized between 0 and 1). This score doesn’t just tell us how many people bought a game. It reflects how visible, discussed, and socially present a game is in the gaming ecosystem.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_15_popularity.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.12 - Top 15 games with respect to our <i>Popularity Score</i>. </figcaption>
</figure>

The top 15 games according to our popularity score feature a mix of blockbuster titles and enduring multiplayer hits. ***GTA V*** leads the pack, followed closely by ***ELDEN RING*** and ***Cyberpunk 2077***. Multiplayer staples like ***CS:GO***, ***Left 4 Dead 2***, and ***PAYDAY 2*** show strong staying power, while narrative-rich games (***Red Dead Redemption 2***, ***The Witcher 3***, ***Baldur’s Gate 3***) and indie successes (***Stardew Valley***, ***Terraria***) demonstrate the wide range of what "popular" can mean on Steam.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/popularity_distribution.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.13 - Popularity score distribution and Kernel Density Estimation. </figcaption>
</figure>

The median popularity of games by release year reveals how audience focus has evolved. In the late ’90s and early 2000s, median scores often exceeded 0.6, driven by landmark titles like ***Half-Life*** and ***Counter-Strike***. But from 2006 onward, scores declined to around 0.35–0.45, reflecting the rise of digital platforms, indie games, and a fragmented attention economy. A slight uptick in recent years hints at pandemic-era engagement and viral hits, though overall visibility per title has diminished as the market expands.

***Title*** Popularity of games is on average declining

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/median_popularity_and_max_popularity_by_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.14 - Median and maximum popularity by year. </figcaption>
</figure>

Tracking each year's most popular game outlines a parallel history of standout releases. Valve dominated early on, followed by a mix of cult hits (***Psychonauts***, ***Stardew Valley***) and AAA blockbusters (***GTA V***, ***ELDEN RING***). These games not only captured attention at launch but they remained culturally and playably relevant, setting them apart in an increasingly saturated landscape.


<h2 id="Appreciation Score"> Appreciation Score </h2>

While popularity tells us which games are getting the most attention, appreciation is about how deeply players value their time spent. To distill that sentiment into a measurable score, we combined three distinct signals of game quality:

<ul class = "in_text_list">
  <li> Steam review ratio: a basic signal of user satisfaction </li>
  <li> Metacritic critic score: a curated, professional assessment </li>
  <li> Metacritic user score: broader public sentiment outside Steam’s ecosystem </li>
</ul>


We used ***Principal Component Analysis (PCA)*** to synthesize these variables into a single score (which is then normalized between 0 and 1), one that cuts through isolated metrics and offers a more holistic picture of how a game is received across communities. This approach lets us identify not just the most played games, but the most loved.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_15_appreciation.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.15 - Top 15 games with respect to our <i>Appreciation Score</i>. </figcaption>
</figure>

The top 15 most appreciated games highlight story-driven, critically acclaimed titles. ***Baldur’s Gate 3*** leads, with classics like ***Half-Life 2***, ***Portal 2***, and ***BioShock*** close behind. Several entries from long-running franchises (***Final Fantasy***, ***Persona***, ***The Elder Scrolls***) appear alongside modern hits like ***Red Dead Redemption 2*** and ***God of War***. This ranking underscores how narrative quality, innovation, and lasting impact drive appreciation, regardless of release date.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/appreciation_distribution.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.16 - Appreciation score distribution and Kernel Density Estimation. </figcaption>
</figure>

Tracking the evolution of appreciation scores reveals how perceptions of quality have shifted in tandem with Steam’s growth. From the late '90s through the 2000s, median scores remained high, reflecting a more selective release environment — where titles like ***Half-Life*** and ***Half-Life 2*** weren’t just popular but deeply respected. The post-2010 period, however, saw a dip, particularly around 2014–2016, as the platform opened to a flood of indie games — some exceptional, many less polished. Yet from 2020 onward, appreciation begins a modest recovery, suggesting developers have adapted to a crowded market, and players to better filtering tools. Our two domain experts have different points of view on this matter:

<blockquote class = "expert_quote">
  <p>"As the pool increases, the quality inevitably decreases on average. Then on Steam, all this is amplified because more and more unknown games are released, and this can lead to an average decrease in appreciation." - <cite> Andrea Porta </cite> </p>

  <p>"For years, video game creators have responded to player's calls for elements like 'cutting-edge graphics' and other initially gratifying features. However, prioritizing these aspects has, at times, come at the cost of content depth and innovation." - <cite> Fortuna Imperatore </cite> </p>
</blockquote>

***Title*** Appreciation of games is on average declining

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/median_appreciation_and_max_appreciation_by_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.17 - Median and maximum appreciation by year. </figcaption>
</figure>

Overlaying top appreciated games by year reinforces this: alongside AAA milestones like ***The Witcher 3*** and ***Baldur’s Gate 3***, we find greatly appreciated indies like ***Celeste***, ***Hollow Knight***, and ***Pizza Tower***. These titles show that lasting impact isn’t tied to budget, but to originality, depth, and connection.



<h2 id="Appreciation-Popularity Plane"> Appreciation-Popularity Plane </h2>

The scatter plot below positions games according to their appreciation (horizontal axis) and popularity (vertical axis) scores. With median lines dividing the space, four distinct profiles emerge. Games in the top-right quadrant — such as ***Red Dead Redemption 2*** or ***The Witcher 3*** — combine strong admiration with widespread reach. The top-left captures popular games with more mixed reception, while the bottom-right shows beloved titles with narrower appeal. The bottom-left hosts games that struggled to resonate broadly on either front. This quadrant framework helps decode the landscape of critical and commercial impact at a single glance.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/popularity_vs_appreciation.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.18 - Games distribution on the Appreciation and Popularity score plane. Most "extreme" games in each quadrant are marked with yellow circles. </figcaption>
</figure>

The top 15 titles that excel in both popularity and appreciation reflect a compelling mix of blockbuster hits and standout indie successes. Games like ***Baldur’s Gate 3***, ***GTA V***, and ***Elden Ring*** dominate thanks to massive reach and critical acclaim. But beloved indies such as ***Stardew Valley***, ***Hollow Knight***, ***Terraria***, and ***Undertale*** hold their ground, proving that emotional impact and craftsmanship can rival even the biggest AAA productions.

High popularity & low appercation games managed to draw substantial attention but not much love. Big budget titles like ***Battlefield 2042***, ***Fallout 76***, and ***NBA 2K21*** rank high in visibility yet falter in player satisfaction, as reflected by significantly lower appreciation scores. The list is almost entirely dominated by large publishers, hinting at a recurring pattern: strong marketing and brand recognition can drive popularity even when the final product disappoints. It's a stark reminder that **hype alone does not guarantee lasting success**.

High appreciation & low popularity games represent the hidden gems of the Steam catalog—titles that flew under the radar but struck a chord with those who played them. Mostly indie and niche productions, like ***Worm Jazz***, ***Depixtion***, and ***DERU - The Art of Cooperation***, these games boast remarkably high appreciation scores despite modest popularity. Their presence suggests that while marketing power can drive visibility, creative vision and satisfying gameplay can build strong player loyalty, even without mainstream attention. 

The bottom end of the popularity–appreciation spectrum paints a picture of titles that struggled to gain traction both commercially and critically. Games like ***Wild West Online*** and ***Shadow Harvest: Phantom Ops*** saw limited player interest and failed to win over those who did engage. Interestingly, many of these are smaller indie efforts or low-profile AA titles, suggesting either **underdeveloped experiences** or **misaligned expectations**.


<h1 id = "Indie vs Non-Indie"> Indie vs Non-Indie </h1>

While independent developers were virtually absent from the early 2000s Steam landscape, things began to shift dramatically in the 2010s. In 2010, only a quarter of the games with a Metacritic page were indie titles. By 2015, that share had soared past 66%, reflecting the growing accessibility of game development tools and digital distribution platforms.


***Indie games on the market have been steadily increasing

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/indie_vs_not_indie_by_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.19 - Number of indie and non-indie game released. </figcaption>
</figure>

At its peak in the mid-2010s, indie representation regularly accounted for over half of all notable Steam releases, a cultural and creative boom that brought forth titles now considered classics like ***Stardew Valley***, ***Hollow Knight***, and ***Celeste***. Though recent years have seen a slight decline in their relative share (down to around 44% in 2023), indie games remain a driving force in shaping what we play and how we engage with games.

The data tells a clear story: indie games, once rare outliers, take a now an important share of the PC gaming market. But how do they stack up in terms of visibility and critical acclaim? We break it down next.

When comparing appreciation scores, our measure of how well-received a game is, indie titles have often outperformed their big-budget counterparts, especially in more recent years.

***Indie games score better than non indie in terms of appreciation

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/indie_vs_not_indie_median_appreciation.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.20 - Median appreciation by year for indie and non-indie games. </figcaption>
</figure>

Since 2010, median appreciation scores for indie games have remained steady, hovering around 0.70–0.76. In contrast, non-indie (or AAA) games have seen greater fluctuation and, in some years, lagged behind. By 2023, indie games achieved a median appreciation of 0.75, compared to 0.69 for non-indie releases. This suggests that while indie games might not always match AAA production values, they end up being more appreciated through different means.

While indie titles have increasingly gained critical acclaim they still lag behind in terms of popularity. Median popularity scores for indie games consistently trail those of non-indie releases across most years.

***Non-Indie games score better than indie in terms of popularity

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/indie_vs_not_indie_median_popularity.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.21 - Median pupularity by year for indie and non-indie games. </figcaption>
</figure>

In the early 2000s blockbuster titles dominated the market. But even in more recent years (e.g., 2020–2023), the most popular titles remain overwhelmingly non-indie. Notably, however, some indie games have broken through this ceiling. Titles like ***Terraria***, ***Hollow Knight***, and ***Stardew Valley*** have not only achieved critical success but also popularity levels comparable to large-scale productions.

The notable spike in indie game popularity in 2008 can be attributed to a handful of highly successful titles released that year. Games like ***World of Goo***, ***AudioSurf***, ***Mount & Blade***, and ***Defense Grid: The Awakening*** gained significant traction on Steam, reflecting both their innovation and increasing visibility for indie titles. With only nine indie games in the dataset for that year, these standout hits heavily influenced the median popularity score, pushing it above 0.5 (the highest for indie titles until 2022). This moment marks one of the early breakthroughs of indie games into broader public awareness during the digital distribution era.

***Title***Some indie games have achieved AAA-levels of popularity

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_pop_top_appr_indie.json"></vegachart>
  </div>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_pop_top_appr_not_indie.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.22 - Left: Popularity score for the top 15 indie games. Right: appreciation score for the top 15 indie games. </figcaption>
</figure>


The data gathered from our review analysis shines some light on the characteristics that set apart indie and non-indie games. An analysis of the number of mentions per topic shows that both users and critics look for slightly different things in indie games compared to non indie games. For example, story and narrative do not gather as many mentions in reviews of indie games, both of users and critics, as they do for non-indie games. Users in particular tend to comment more on the sound and music in indie games, generally with a positive connotation. Interestingly, although gameplay is always the most discussed topic in games reviews, the gameplay for the most popular indie games received more attention by users than the gameplay for the most popular non indie games.

Both in terms of gameplay and price and value for money users tend to share more positive comments for popular indie games than for popular non-indie games. Considering the higher price-point of non-indie games, it may be that users are more inclined to be pleasantly surprised by games that were less expensive; it could also mean that expectations for games coming from non-indie developers are generally higher and thus more difficult to meet or exceed.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/emojiChart_indieVSnonIndie.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.23 - Left: Total mention by topic. Right: Sentiment breakdown by topic. The dropdown menu can be used to switch between users and critics. </figcaption>
</figure>

Our data highlights a clear strategic advantage for indie games in terms of initial pricing. With an average launch price of $16.85, significantly lower than non-indie titles averaging $25.60 (and a median of $14.99 compared to $19.99 for non-indies), independent developers consistently offer a more accessible entry point for players. This lower barrier to entry is crucial in a competitive market, yet affordability alone does not guarantee market dominance; our figures show that non-indie games generally achieve higher popularity scores (averaging 0.448 versus 0.363 for indies) despite their higher price point. 

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/pop_appr_byprice_scatter.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.24 - Scatter plot of popularity vs appreciation for indie and non-indie games by current prices. </figcaption>
</figure>


This gap underscores the critical role of pre-launch marketing and has been confirmed by Andrea Porta:

<blockquote class = "expert_quote">
  "The communication window between a game's announcement and its release is pivotal for building hype and shaping initial reception, with larger studios expertly orchestrating content drops—from gameplay reveals to launch trailers—to capture and sustain consumer attention. Intriguingly, many independent studios are now adopting the same strategy, leveraging similar strategic trailer releases to amplify their reach."
</blockquote>

This evolving marketing sophistication, coupled with their inherently competitive pricing, may well be key to how certain indie games carve out significant success within the overwhelmingly vast gaming landscape.




<h1 id = "Steam tags analysis"> Steam tags analysis </h1>

Steam tags serve as the primary vocabulary of the platform's discovery system. Whether applied by developers or players, tags capture everything from genre and theme to tone and mechanics. Analyzing these tags offers insight into what types of games capture attention — and which appeal most to players or critics.

A first look at Steam’s tagging ecosystem reveals the most common features and genres that define the platform’s catalog. The most frequent tags (**Singleplayer**, **Action**, **Adventure**, and **Indie**) reflect the foundational role of narrative-driven and independently developed games in Steam’s library. Tags like **Atmospheric**, **Story Rich**, and **Great Soundtrack** point to an emphasis on immersive experiences, while **Multiplayer** and **Co-op** signal the continued relevance of shared play. Meanwhile, **2D**, **Strategy**, and **Puzzle** showcase the variety in form and mechanics that appeal to different gaming audiences.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_15_tags.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.25 - Top-15 tags overall. </figcaption>
</figure>

The data reveals clear trends shaping today’s gaming landscape: immersive atmospheres and nostalgia-driven themes lead player interest, while adventure and indie genres dominate overall volume, highlighting both broad appeal and creative diversity. Visual styles range widely, with 2D aesthetics and varied perspectives thriving alongside niche approaches. Classic genres like puzzle and platformers maintain strong presence, complemented by popular sub-genres emphasizing skill and replayability. Singleplayer remains the dominant mode, though multiplayer and co-op offer rich social experiences. Narrative depth is highly valued, with players seeking agency and meaningful storytelling. Together, these insights show a balanced ecosystem where innovation, tradition, and player choice coexist to define successful game design.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/tags_frequency_by_category.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.25 - Top-10 tags by category. </figcaption>
</figure>

A closer look to the genre and subgenres tags gives some preliminary insight on how they tend to change within quadrants. Particularly significant is the difference in the top subgenres switching between the quadrants HP-LA and LP-HA. Popular tags found in the HP-LA quadrant, such as **FPS**, **Hack and Slash** and **Third-Person Shooter** are not as common in games belonging to the LP-HA quadrant; here more niche tags such as  **Puzzle-Platformers** and **Shoot ’Em Ups** take the lead in terms of frequency.

***Title*** Use the tag explorer to find out the most relevant genres and subgenres in each quadrant

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_genres_subgenres_by_quadrant.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.26 - Top genres and sub-genres by quadrant. </figcaption>
</figure>

Although some patterns are emerging from the analysis of game tags, they are not enough to paint a comprehensive picture of what characteristics make a game popular or appreciated. To shed some more light on this fundamental question, we trained a predictive model.


<h1 id = "Predicting Success?"> Predicting Success? </h1>

<blockquote class = "expert_quote" style = "color: #00ff00; text-align: justify;">
  Is it possible to predict the success of a game? More precisely, is it possible to predict it by using only pre-release features such as the number of wishlists, Steam tags or the price?
</blockquote>

We tried to answer this question by using a machine learning ensemble model called <a href="https://xgboost.ai/">XGBoost</a>. In particular, we modeled both popularity and appreciation predictions as a binary classification task with thresholds given by the medians of the two distributions. In order to interpret our results we leveraged <a href="https://shap.readthedocs.io/en/latest/">SHAP</a>, a python library. For more details we refer to the technical discussions. 

First, we tried to predict popularity and appreciation separately. 

<h2 id="Predicting popularity"> Predicting popularity </h2>

Digging deeper into what fuels a game’s popularity, a closer analysis reveals some trends. The clearest predictor? Wishlist activity. When a game racks up high interest on platforms like Backloggd before launch, it’s far more likely to become a hit — making early buzz one of the strongest signals of future popularity. This result confirm what Fortuna Imperatore told us in our interview. (*Possibile citazione*)

Social and broad-appeal features also stand out. Games tagged with Multiplayer tend to perform significantly better, while those without it often suffer in visibility — suggesting that while not essential, social functionality is becoming a powerful norm.
 
The Strategy tag offers another interesting twist. Although it’s not especially common, when present, it often signals a bump in popularity — highlighting strategic depth as a niche but respected trait among players. Curiously, Singleplayer works in the opposite direction. It doesn’t guarantee popularity, but its absence almost always drags a game down. That suggests solo play isn’t a bonus — it’s a baseline expectation for many players.

Other features like Open World, Sandbox, and Online Co-Op all contribute positively, while broader language support also nudges popularity upward, reflecting the benefits of global accessibility.
 
Some tags are more situational. Games labeled Cute or Simulation tend to have unpredictable effects — sometimes helping, sometimes hurting — likely depending on execution or market trends.

Overall, the analysis shows that popularity isn’t just about having the right tags — it’s about how and when they show up. Certain features give games a clear edge, while others only work in the right context.


<h2 id="Predicting appreciation"> Predicting appreciation </h2>

When it comes to what players really value, the data tells a fascinating story. Games with a high number of wishlist entries on platforms like Backloggd aren’t just popular — they’re also more likely to be deeply appreciated. Anticipation and lasting satisfaction often go hand-in-hand, validating pre-release buzz as a surprisingly reliable compass for acclaim.

Another standout signal is indie status. While the “indie” tag doesn’t always have a massive global effect, it tends to quietly boost a game’s appreciation score when present. Players seem to reward originality, personality, and risk-taking — qualities more commonly found in the indie space.
 
Certain genres punch well above their weight. Strategy and Puzzle games, for example, consistently drive up appreciation, pointing to a player base that values depth and thoughtful mechanics. The same goes for more playful tags like Cute and Funny, suggesting emotional tone can matter just as much as gameplay.
 
Accessibility also plays a subtle but important role. Games that support more audio and subtitle languages tend to be rated more favorably — a nod to the growing expectation for inclusivity and polish.
 
Not all tags land well, though. The Walking Simulator label, despite including some standout titles, drags down appreciation predictions on average. It’s a divisive term, and the model reflects that ambivalence. Similarly, the broad Adventure tag shows only a slight negative effect — perhaps because it’s used so loosely that it dilutes player expectations.
 
On the brighter side, 2D and Fantasy genres quietly contribute to higher satisfaction, hinting at an enduring love for stylized, imaginative worlds.
 
Interestingly, Multiplayer — a strong driver of popularity — plays only a modest role here. Players might enjoy social play, but appreciation seems to hinge more on creativity, clarity of vision, and emotional resonance.
 
In the end, it’s not just what a game does — it’s how thoughtfully it does it. Clever mechanics, polish, and personality go a long way in winning players’ hearts.


<h2 id="Predicting success"> Predicting success </h2>

Then we tried to predict success by considering popularity and appreciation at the same time. We have four different possible outcomes.


<p class = "custom_p"> Cold Reception: When Games Miss on Both Fronts (Low Popularity and Low Appreciation) </p>

Some games fall flat on both popularity and appreciation. The clearest indicator is a lack of wishlist interest. Games with low wishlist counts on Backloggd are strongly nudged into this underperforming category, highlighting the predictive power of early audience engagement (or lack thereof).

Multiplayer and singleplayer modes act as safeguards: their presence reduces the likelihood of a game landing in this low/low quadrant. Similarly, genre tags like Strategy, Open World, and Sandbox modestly buffer against total obscurity — suggesting that even niche or systems-rich games find appreciative corners of the market.

In contrast, Walking Simulator emerges as a risk factor. When present, it increases the likelihood of poor performance on both axes, possibly due to polarized expectations or unmet ambitions. Tags like Funny, Puzzle, and Colorful offer more subtle support — while their individual impact is small, their absence can signal trouble.

Ultimately, games in this group tend to lack standout qualities or defined audiences, often slipping through the cracks in both reach and reception.


<p class = "custom_p"> The Hype That Didn’t Land: Popular but Poorly Received (High Popularity and Low Appreciation) </p>

These are the games that make noise — but fail to live up to it. While not universally true, the SHAP values suggest a pattern: Multiplayer, Open World, and Simulation tags all raise the chance of a game being classified as high in popularity but low in appreciation. These features may drive interest or sales, but don’t always translate into satisfying experiences.

Surprisingly, fewer supported languages also correlate with this quadrant — possibly pointing to rushed or under-localized releases. On the pricing side, expensive games (in the $50–$100 range) show a sharp uptick in SHAP value, implying that high cost might raise expectations — and disappointment when those aren’t met.

Games with 2D, Indie, or Fantasy tags, however, are less likely to fall here. These often cater to more focused audiences, where hype is better aligned with delivery.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/HighPop_LowAppr.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.26 - Top genres and sub-genres by quadrant. </figcaption>
</figure>

In essence, big games with bold features can still miss the mark. Popularity alone isn’t enough to secure lasting appreciation.


<p class = "custom_p"> Hidden gems: Loved, but Overlooked (Low Popularity and High Appreciation) </p>
 
This quadrant houses the hidden gems — games that win hearts, even if they don’t win headlines.

Wishlist counts are typically low here, reinforcing their under-the-radar status. Yet genre and style play a key role in boosting their acclaim. Tags like 2D, Puzzle, Cute, and especially Indie are strongly associated with this quadrant. These are often smaller, more personal games that resonate with players despite lacking mass exposure.
 
Conversely, tags tied to scale — like Open World, Survival, or Online Co-Op — make games less likely to land in this category, as they typically appeal to wider audiences.

Localization plays a minor role, with fewer supported languages modestly increasing a game’s chance of being classified here. Likewise, mid-priced titles ($20–$50) are less common — perhaps suggesting that budget-friendly or unconventional pricing helps niche games reach the right players.

<figure>
  <div class = "general_chartClass">
    <vegachart schema-url="/g1-2025-website/assets/charts/HighAppr_LowPop.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.26 - Top genres and sub-genres by quadrant. </figcaption>
</figure>

These are the slow burns and cult classics — proof that critical appreciation doesn’t always follow the crowd.


<p class = "custom_p"> The Holy Grail: a developer's dream (High Popularity and High Appreciation) </p>

So what makes a game both loved and widely played? The SHAP data points to a few key ingredients.
 
First, wishlist_backloggd shows its strength: games with high wishlist counts are pushed firmly into this top-right quadrant. Broader platform availability also plays a major role: the more systems a game launches on, the more likely it is to find both popularity and appreciation.
 
Genre-wise, tags like Strategy, Multiplayer, Singleplayer, and even lighter features like Funny, Rogue-like, and Puzzle contribute positively. These games combine reach with substance — offering both accessible hooks and rewarding mechanics.
 
Surprisingly, pricing in the $50–$70 range doesn’t have a clear effect, suggesting that value perception is more nuanced at the top end.
 
In short, the most successful games blend genre depth, broad availability, and strong anticipation. They win attention and reward it — earning both widespread appeal and lasting respect.



<h1 id = "Conclusions"> Conclusions </h1>

If there's one takeaway from our analysis, it's this: <i>there is no universal recipe for making a successful game</i>. While our predictive models uncovered consistent patterns — like the strong influence of wishlist interest, the positive role of localization and accessibility, or the impact of some tags — they are not crystal balls. The models can detect statistical associations, not causal relationships. They help us understand what tends to matter, but not why or how it leads to success in every case.
 
Crucially, our findings show that success — whether measured as popularity or appreciation — can take many forms. AAA games, with their broad platform releases and marketing power, often dominate in popularity. But they are not always the most appreciated.
In contrast, some indie games quietly achieve high appreciation with far fewer resources. Titles like **[...]**, for example, are testament to how originality, thoughtful design, and strong narrative identity can create deeply resonant experiences.
 
Success in games, as in art, is multifaceted. <b><i>And perhaps that’s exactly what makes this medium so exciting</i></b>.







