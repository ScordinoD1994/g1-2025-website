---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: "Main Article"
vega: true
---

<div class="full-width-wrapper">
    <img src="{{ site.baseurl }}/assets/images/header.svg" alt="sbd-pattern" class="full-width-image">
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
          <li> <a href="#Conclusions">Conclusions</a> </li>
          <ul>
            <li> <a href="#Next steps">Next steps</a> </li>
          </ul>
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

<figure style = "float:left;">
  <img src='assets/images/steamdb_game_releases_per_year.png' width = 500>
  <figcaption class = "figcaption_class"> Fig.1 - Game releases per year. Image from <a href="https://steamdb.info/stats/releases/">SteamDB</a>. </figcaption>
</figure>
<figure style = "float:left;">
  <img src='assets/images/steamdb_game_releases_per_month.png' width = 500>
  <figcaption class = "figcaption_class"> Fig.2 - Game releases per month. Image from <a href="https://steamdb.info/stats/releases/">SteamDB</a>. </figcaption>
</figure>

This deluge of content has created fierce competition for attention. For many games, even getting noticed is a monumental challenge.
To focus on titles that have reached some degree of exposure, we narrowed our dataset to the subset of Steam games with a Metacritic page. These are titles that have drawn at least some degree of critic and user attention — a crucial step toward both commercial and critical success.
But even within this more visible subset, the numbers tell a revealing story. While the absolute number of games with Metacritic pages has been steadily rising — nearly tripling since 2015 — their proportion relative to the total number of Steam releases has been declining. 

<figure>
  <vegachart schema-url="/g1-2025-website/assets/charts/metacritic_games_per_year.json" style="width: 100%; height: 100%"></vegachart>
  <figcaption class = "figcaption_class"> Fig.3 - Metacritic games per year. </figcaption>
</figure>

In other words, as the flood of new releases grows, fewer of them are breaking through to earn critical attention.


<h2 id="How players engage"> How players engage </h2>

Once a game is released on Steam, how do players actually engage with it? We examined three key signals: **estimated ownership**, **average playtime**, **review counts**, each revealing a different aspect of how attention and interest unfold. First, the total estimated number of owners has increased steadily over the years, showing that even as the platform grows more crowded, many games are still managing to reach players — often helped by bundles, deep discounts, or seasonal promotions. However, the gains are far from evenly distributed.

When we look at average playtime over time, a subtle but important shift emerges: newer games tend to see shorter engagement windows compared to older titles. Whether due to time constraints, the abundance of available alternatives, or changing player habits, it's clear that player attention is fragmenting.

<figure>
  <div class = "doubleGraph" style = "width: 500px; height: 500px;">
    <vegachart schema-url="/g1-2025-website/assets/charts/total_average_estimated_owners_per_year_plus_average_playtime_per_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.4 - Total average estimated owners (left plot) and average playtime per year (right plot). </figcaption>
</figure>

Some noticeable spikes in the data trace back to landmark releases. The peaks in average playtime seen in years like 1998, 2000, 2001, 2003, and 2004 align with the launches of enduring classics like ***Half-Life***, ***Counter-Strike***, ***Half-Life: Blue Shift***, ***Day of Defeat***, and ***Counter-Strike: Source***. These titles have maintained active player bases over decades, skewing the average upward. Similarly, the sharp rise in estimated ownership in 2013 is largely attributable to *Dota 2*, a free-to-play phenomenon that brought millions of players onto Steam and became a pillar of its ecosystem.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/explain_spikes.json"></vegachart>
  </div>  
  <figcaption class = "figcaption_class"> Fig.5 - Spikes breakdown. </figcaption>
</figure>

Finally, we explored review activity by looking at the distribution of the number of user reviews per game. The pattern here is starkly unequal: most games receive very few reviews, while a select few attract thousands. This distribution — like ownership and playtime — reflects a highly competitive ecosystem, where visibility and player feedback are dominated by a small percentage of releases.
Together, these trends reveal how player engagement is both growing and concentrating, offering opportunities for breakout hits, but also highlighting the steep climb most games face after launch.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/reviews_distribution_plus_reviews_bucket_per_released_games.json"></vegachart>
  </div>  
  <figcaption class = "figcaption_class"> Fig.6 - Review distribution. </figcaption>
</figure>

Understanding how much a game is liked is not as straightforward as it might seem. As Fortuna Imperatore underscores,

<blockquote class = "expert_quote">
  "The recipe is very difficult to find, given that our impossible task is to respond to the needs of society at that historical moment."
</blockquote>

Appreciation can’t be distilled into a single number, but the industry has long leaned on a few core metrics. On Metacritic, two scores are typically available: the critic score, based on professional reviews, and the user score, submitted by players. On Steam, the main visible indicator of satisfaction is the positive review ratio — the share of user reviews marked as “positive”. 
Each of these metrics, however, tells a slightly different story. Critic scores tend to cluster around the higher end of the scale. Reviewers often avoid the harshest ratings, leading to a compressed distribution with fewer low scores and a bias toward the 70–90 range. As Andrea Porta explains,

<blockquote class = "expert_quote">
  "This is usually the case because journalists can sometimes feel a significant responsibility when assigning a very low score to highly anticipated titles. Such a dynamic is very real and has deep roots within the video game critics landscape, which currently grapples with substantial financial challenges."
</blockquote>

User scores, on the other hand, are more variable. Players are not shy about expressing dissatisfaction, resulting in a broader spread that includes more low-rated games. The contrast becomes clear when the two are plotted together—players are often harsher, and sometimes more polarized.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/critic_plus_user_score.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.7 - Metacritic critic score (left plot) and user score (right plot) distributions. </figcaption>
</figure>

Then there’s the Steam positive ratio, which differs not just in scale but in nature. Steam reviews operate on a binary system —“thumbs up” or “thumbs down” — which strips away nuance and skews the distribution dramatically. Most games that gather reviews at all tend to be favored, so the ratio is heavily biased toward high values. In many cases, even moderately liked games can end up with “Very Positive” labels, suggesting that this metric alone might not capture the full spectrum of appreciation.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/steam_positive_review_ratio.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.8 - Steam positive review ration distribution with review segmentation. </figcaption>
</figure>

These differences highlight the challenge of evaluating player sentiment in a consistent way. Each metric provides a piece of the puzzle, but none offers the full picture. This tension points to the need for more robust, composite measurements—an effort we take up in the next section, where we move toward defining appreciation and popularity as integrated, quantifiable outcomes.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/metacritic_score_difference.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.9 - Difference between critic and user metacritic scores. </figcaption>
</figure>

Beyond the general trends, some games exhibit striking discrepancies between critic and user evaluations. In our dataset, we found a substantial number of titles where the difference between the two scores exceeds 20 points on a 100-point scale—sometimes even more than 30. These outliers can reflect cases where critics and players approached the game from entirely different perspectives: technical polish vs. emotional resonance, innovation vs. nostalgia, or even divergent expectations shaped by marketing.
Analyzing these outliers in more detail could offer valuable insights into the dynamics of reception—what drives such a divide, and what it reveals about the varying standards of professional reviewers and general audiences.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/user_vs_critic_score_by_difference.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.10 - Users vs critic score on Metacritic. </figcaption>
</figure>


<h1 id = "Measuring Success"> Measuring Success </h1>

With thousands of games released each year and player attention more fragmented than ever, relying on a single metric to evaluate a game’s success is increasingly limiting. A high number of owners doesn’t necessarily mean players liked the experience; a strong review ratio might come from a niche but passionate fanbase. Conversely, a critically acclaimed title might fail to attract a meaningful audience. In such a complex ecosystem, success is multidimensional and it becomes crucial to disentangle its components.

To this end, we introduce two composite indicators: ***Popularity*** and ***Appreciation***. These scores aim to synthesize multiple signals into meaningful, interpretable dimensions. Popularity combines a game’s visibility, reach, and commercial uptake (through ownership, wishlisting, and review counts), while appreciation reflects how well a game is received once it's played (via various types of ratings).

This dual-axis approach allows for a more nuanced understanding of a game's position in the market: whether it's beloved but overlooked, widely played but polarizing, or among that group that is both popular and appreciated. In the sections that follow, we explore how these metrics behave, what patterns emerge, and what features seem to shape a game's trajectory across these axes.

<h2 id="Popularity Score"> Popularity Score </h2>

Popularity in the gaming world is more than just raw sales. It’s a combination of visibility, engagement, and community presence. To capture this complex reality, we created a composite ***Popularity Score*** using data from both Steam and gaming databases like Metacritic and Backloggd.
We began with ten core indicators of attention, ranging from how many people bought or played a game, to how often it was reviewed or recommended. These included:

<ul class = "in_text_list">
  <li> Player activity metrics like peak concurrent users (24h and all-time) </li>
  <li> Estimated number of owners </li>
  <li> Steam review counts (total and recommendations) </li>
  <li> Engagement on Backloggd (plays, backlogs, reviews) </li>
  <li> Number of critic and user reviews on Metacritic </li>
</ul>

Because these numbers can vary wildly between indie darlings and AAA blockbusters, we applied a logarithmic transformation to scale them more evenly. Then, we used ***Principal Component Analysis (PCA)*** to synthesize these features into a single, unified score (which is then normalized between 0 and 1). This score doesn’t just tell us how many people bought a game. It reflects how visible, discussed, and socially present a game is in the gaming ecosystem.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_15_popularity.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.11 - Top 15 games with respect to our <i>Popularity Score</i>. </figcaption>
</figure>

The top 15 games by our popularity score feature a mix of blockbuster titles and enduring multiplayer hits. ***GTA V*** leads the pack, followed closely by ***ELDEN RING*** and ***Cyberpunk 2077***. Multiplayer staples like ***CS:GO***, ***Left 4 Dead 2***, and ***PAYDAY 2*** show strong staying power, while narrative-rich games (***Red Dead Redemption 2***, ***The Witcher 3***, ***Baldur’s Gate 3***) and indie successes (***Stardew Valley***, ***Terraria***) demonstrate the wide range of what "popular" can mean on Steam.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/popularity_distribution.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.12 - Popularity score distribution and Kernel Density Estimation. </figcaption>
</figure>

The median popularity of games by release year reveals how audience focus has evolved. In the late ’90s and early 2000s, median scores often exceeded 0.6, driven by landmark titles like ***Half-Life*** and ***Counter-Strike***. But from 2006 onward, scores declined to around 0.35–0.45, reflecting the rise of digital platforms, indie games, and a fragmented attention economy. A slight uptick in recent years hints at pandemic-era engagement and viral hits, though overall visibility per title has diminished as the market swells.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/median_popularity_and_max_popularity_by_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.13 - Median and maximum popularity by year. </figcaption>
</figure>

Tracking each year's most popular game outlines a parallel history of standout releases. Valve dominated early on, followed by a mix of cult hits (***Psychonauts***, ***Stardew Valley***) and AAA blockbusters (***GTA V***, ***ELDEN RING***). These games not only captured attention at launch but they’ve remained culturally and playably relevant, setting them apart in an increasingly saturated landscape.


<h2 id="Appreciation Score"> Appreciation Score </h2>

While popularity tells us which games are getting the most attention, appreciation is about how deeply players value their time spent. To distill that sentiment into a measurable score, we combined three distinct signals of game quality:

<ul class = "in_text_list">
  <li> Steam review ratio: a grassroots signal of user satisfaction </li>
  <li> Metacritic critic score: a curated, professional assessment </li>
  <li> Metacritic user score: broader public sentiment outside Steam’s ecosystem </li>
</ul>


We used ***Principal Component Analysis (PCA)*** to synthesize these variables into a single score (which is then normalized between 0 and 1), one that cuts through isolated metrics and offers a more holistic picture of how a game is received across communities. This approach lets us identify not just the most played games, but the most loved.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_15_appreciation.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.14 - Top 15 games with respect to our <i>Appreciation Score</i>. </figcaption>
</figure>

The top 15 most appreciated games highlight story-driven, critically acclaimed titles. ***Baldur’s Gate 3*** leads, with classics like ***Half-Life 2***, ***Portal 2***, and ***BioShock*** close behind. Several entries from long-running franchises (***Final Fantasy***, ***Persona***, ***The Elder Scrolls***) appear alongside modern hits like ***Red Dead Redemption 2*** and ***God of War***. This ranking underscores how narrative quality, innovation, and lasting impact drive appreciation, regardless of release date.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/appreciation_distribution.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.15 - Appreciation score distribution and Kernel Density Estimation. </figcaption>
</figure>

Tracking the evolution of appreciation scores reveals how perceptions of quality have shifted in tandem with Steam’s growth. From the late '90s through the 2000s, median scores remained high, reflecting a more selective release environment — where titles like ***Half-Life*** and ***Half-Life 2*** weren’t just popular but deeply respected. The post-2010 period, however, saw a dip, particularly around 2014–2016, as the platform opened to a flood of indie games — some exceptional, many less polished. Yet from 2020 onward, appreciation begins a modest recovery, suggesting developers have adapted to a crowded market, and players to better filtering tools. Our two domain experts have different points of view:

<blockquote class = "expert_quote">
  <p>"As the pool increases, the quality inevitably decreases on average. Then on Steam, all this is amplified because more and more unknown games are released, and this can lead to an average decrease in appreciation." <cite> Andrea Porta </cite> </p>

  <p>"For years, video game creators have responded to player calls for elements like 'cutting-edge graphics' and other initially gratifying features. However, prioritizing these aspects has, at times, come at the cost of content depth and innovation." <cite> Fortuna Imperatore </cite> </p>
</blockquote>

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/median_appreciation_and_max_appreciation_by_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.16 - Median and maximum appreciation by year. </figcaption>
</figure>

Overlaying top appreciated games by year reinforces this: alongside AAA milestones like ***The Witcher 3*** and ***Baldur’s Gate 3***, we find emotionally resonant indies like ***Celeste***, ***Hollow Knight***, and ***Pizza Tower***. These titles show that lasting impact isn’t tied to budget, but to originality, depth, and connection.



<h2 id="Appreciation-Popularity Plane"> Appreciation-Popularity Plane </h2>

The scatter plot below positions games according to their appreciation (horizontal axis) and popularity (vertical axis) scores. With median lines dividing the space, four distinct profiles emerge. Games in the top-right quadrant — such as ***Red Dead Redemption 2*** or ***The Witcher 3*** — combine strong admiration with widespread reach. The top-left captures popular games with more mixed reception, while the bottom-right shows beloved titles with narrower appeal. The bottom-left hosts games that struggled to resonate broadly on either front. This quadrant framework helps decode the landscape of critical and commercial impact in a single glance.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/popularity_vs_appreciation.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.17 - Games distribution on the Appreciation and Popularity score plane. Most "extreme" games in each quadrant are marked with yellow circles. </figcaption>
</figure>

The top 15 titles that excel in both popularity and appreciation reflect a compelling mix of blockbuster hits and standout indie successes. Games like ***Baldur’s Gate 3***, ***GTA V***, and ***Elden Ring*** dominate thanks to massive reach and critical acclaim. But beloved indies such as ***Stardew Valley***, ***Hollow Knight***, ***Terraria***, and ***Undertale*** hold their ground, proving that emotional impact and craftsmanship can rival even the biggest AAA productions.

High popularity & low appercation games managed to draw substantial attention but not much love. Big budget titles like ***Battlefield 2042***, ***Fallout 76***, and ***NBA 2K21*** rank high in visibility yet falter in player satisfaction, as reflected by significantly lower appreciation scores. The list is almost entirely dominated by large publishers, hinting at a recurring pattern: strong marketing and brand recognition can drive popularity even when the final product disappoints. It's a stark reminder that **hype alone doesn't guarantee lasting success**.

High appreciation & low popularity games represent the hidden gems of the Steam catalog—titles that flew under the radar but resonated deeply with those who played them. Mostly indie and niche productions, like ***Worm Jazz***, ***Depixtion***, and ***DERU - The Art of Cooperation***, these games boast remarkably high appreciation scores despite modest popularity. Their presence suggests that while marketing power can drive visibility, creative vision and satisfying gameplay can quietly build strong player loyalty, even without mainstream attention. 

The bottom end of the popularity–appreciation spectrum paints a picture of titles that struggled to gain traction both commercially and critically. Games like ***Wild West Online*** and ***Shadow Harvest: Phantom Ops*** saw limited player interest and failed to win over those who did engage. Interestingly, many of these are smaller indie efforts or low-profile AA titles, suggesting either **underdeveloped experiences** or **misaligned expectations**. The mix of obscure failures and forgotten experiments underlines how crowded and unforgiving the Steam market can be.


<h1 id = "Indie vs Non-Indie"> Indie vs Non-Indie </h1>

While independent developers were virtually absent from the early 2000s Steam landscape, things began to shift dramatically in the 2010s. In 2010, only a quarter of the games with a Metacritic page were indie titles. By 2015, that share had soared past 66%, reflecting the growing accessibility of game development tools and digital distribution platforms.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/indie_vs_not_indie_by_year.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.18 - Number of indie and non-indie game released. </figcaption>
</figure>

At its peak in the mid-2010s, indie representation regularly accounted for over half of all notable Steam releases, a cultural and creative boom that brought forth now-classic titles like ***Stardew Valley***, ***Hollow Knight***, and ***Celeste***. Though recent years have seen a slight decline in their relative share (down to around 44% in 2023), indie games remain a driving force in shaping what we play and how we engage with games.

The data tells a clear story: indie games, once rare outliers, are now integral to the fabric of PC gaming. But how do they stack up in terms of visibility and critical acclaim? We break it down next.

When comparing appreciation scores, our measure of how well-received a game is, indie titles have often outperformed their big-budget counterparts, especially in more recent years.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/indie_vs_not_indie_median_appreciation.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.19 - Median appreciation by year for indie (left plot) and non-indie (right plot) games. </figcaption>
</figure>

Since 2010, median appreciation scores for indie games have remained impressively steady, hovering around 0.70–0.76. In contrast, non-indie (or AAA) games have seen greater fluctuation and, in some years, lagged behind. By 2023, indie games posted a median appreciation of 0.75, compared to 0.69 for non-indie releases. This growing parity, and often superiority, suggests that while indie games might not always match AAA production values, they frequently resonate more deeply with players, offering originality, emotional depth, or innovative mechanics that large studios may overlook.

While indie titles have increasingly gained critical acclaim they still lag behind in terms of popularity. Median popularity scores for indie games consistently trail those of non-indie releases across most years.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/indie_vs_not_indie_median_popularity.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.20 - Median pupularity by year for indie (left plot) and non-indie (right plot) games. </figcaption>
</figure>

This gap is particularly stark in the early 2000s, where blockbuster titles dominated. But even in more recent years (e.g., 2020–2023), the most popular titles remain overwhelmingly non-indie. Notably, however, some indie games have broken through this ceiling. Titles like ***Terraria***, ***Hollow Knight***, and ***Stardew Valley*** have not only achieved critical success but also popularity levels comparable to large-scale productions.

The notable spike in indie game popularity in 2008 can be attributed to a handful of highly successful titles released that year. Games like ***World of Goo***, ***AudioSurf***, ***Mount & Blade***, and ***Defense Grid: The Awakening*** gained significant traction on Steam, reflecting both their innovation and increasing visibility for indie titles. With only nine indie games in the dataset for that year, these standout hits heavily influenced the median popularity score, pushing it above 0.5 (the highest for indie titles until 2022). This moment marks one of the early breakthroughs of indie games into broader public awareness during the digital distribution era.

Indie games have carved out a remarkable space in both popularity and appreciation. Titles like ***Terraria***, ***Stardew Valley***, and ***Hollow Knight*** rival mainstream hits in reach, while critically adored gems such as ***Hades***, ***Celeste***, and ***Undertale*** exemplify the genre’s emotional depth and design excellence. Whether through vibrant communities, unique aesthetics, or tight gameplay, these games prove that creativity and passion can achieve lasting impact, often without blockbuster budgets.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_pop_top_appr_indie.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.21 - Popularity (left plot) and appreciation (right plot) score for top 15 indie games. </figcaption>
</figure>

Mainstream titles dominate popularity through sheer scale, marketing, and cultural footprint — with giants like ***GTA V***, ***ELDEN RING***, and ***Cyberpunk 2077*** leading the charge. Meanwhile, enduring live-service games and cinematic epics maintain engagement across years. In appreciation, it's timeless design and narrative excellence that shine: ***Baldur’s Gate 3***, ***Half-Life 2***, and ***Portal 2*** stand out for innovation and emotional impact.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_pop_top_appr_not_indie.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.22 - Popularity (left plot) and appreciation (right plot) score for top 15 non-indie games. </figcaption>
</figure>

Our data highlights a clear strategic advantage for indie games in terms of initial pricing. With an average launch price of $16.85, significantly lower than non-indie titles averaging $25.60 (and a median of $14.99 compared to $19.99 for non-indies), independent developers consistently offer a more accessible entry point for players. This lower barrier to entry is crucial in a competitive market, yet pure affordability doesn't guarantee market dominance; our figures show non-indie games generally achieve higher popularity scores (averaging 0.448 versus 0.363 for indies). 

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/pop_appr_byprice_scatter.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.23 - Scatter plot of popularity vs appreciation for indie and non-indie games by current prices. </figcaption>
</figure>

This gap underscores the critical role of pre-launch marketing. This is confirmed by Andrea Porta:

<blockquote class = "expert_quote">
  "The communication window between a game's announcement and its release is pivotal for building hype and shaping initial reception, with larger studios expertly orchestrating content drops—from gameplay reveals to launch trailers—to capture and sustain consumer attention. Intriguingly, many independent studios are now adopting this publisher playbook, leveraging similar strategic trailer releases to amplify their reach."
</blockquote>

This evolving marketing sophistication, coupled with their inherently competitive pricing, may well be key to how certain indie games carve out significant success within the overwhelmingly vast gaming landscape.




<h1 id = "Steam tags analysis"> Steam tags analysis </h1>

Steam tags serve as the primary vocabulary of the platform's discovery system. Whether applied by developers or players, tags capture everything from genre and theme to tone and mechanics. Analyzing these tags offers insight into what types of games capture attention — and which resonate most with players or critics.

A first look at Steam’s tagging ecosystem reveals the most common features and genres that define the platform’s catalog. The most frequent tags (**Singleplayer**, **Action**, **Adventure**, and **Indie**) reflect the foundational role of narrative-driven and independently developed games in Steam’s library. Tags like **Atmospheric**, **Story Rich**, and **Great Soundtrack** point to an emphasis on immersive experiences, while **Multiplayer** and **Co-op** signal the continued relevance of shared play. Meanwhile, **2D**, **Strategy**, and **Puzzle** showcase the variety in form and mechanics that appeal to different gaming audiences.

The data reveals clear trends shaping today’s gaming landscape: immersive atmospheres and nostalgia-driven themes lead player interest, while adventure and indie genres dominate overall volume, highlighting both broad appeal and creative diversity. Visual styles range widely, with 2D aesthetics and varied perspectives thriving alongside niche approaches. Classic genres like puzzle and platformers maintain strong presence, complemented by popular sub-genres emphasizing skill and replayability. Singleplayer remains the dominant mode, though multiplayer and co-op offer rich social experiences. Narrative depth is highly valued, with players seeking agency and meaningful storytelling. Level design favors freedom and exploration, yet curated, structured experiences still hold importance. Together, these insights show a balanced ecosystem where innovation, tradition, and player choice coexist to define successful game design.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/tags_frequency_by_category.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.24 - Top-10 tags by category. </figcaption>
</figure>

Across the genre landscape, four key patterns emerge. High Popularity–High Appreciation (HP–HA) genres like **Puzzle**, **Platformer**, and **Turn-Based Strategy** prove that tight mechanics and thoughtful design consistently earn both attention and praise. In contrast, High Popularity–Low Appreciation (HP–LA) genres — though widely played, such as **Arcade** and **RTS** — may suffer from oversaturation or dated design, signaling a gap between player expectations and delivery.
Meanwhile, Low Popularity–High Appreciation (LP–HA) genres like **Rhythm**, **Tower Defense**, and **Point & Click** showcase strong niche appeal, loved deeply by smaller audiences thanks to focused, polished gameplay. Finally, Low Popularity–Low Appreciation (LP–LA) entries reveal genres that may be stuck in creative stagnation, where legacy formats no longer resonate.

<figure>
  <div class = "doubleGraph">
    <vegachart schema-url="/g1-2025-website/assets/charts/top_genres_subgenres_by_quadrant.json"></vegachart>
  </div>
  <figcaption class = "figcaption_class"> Fig.25 - Top genres and sub-genres by quadrant. </figcaption>
</figure>

The sub-genre data reveals a nuanced landscape: High Popularity–High Appreciation (HP-HA) tags like **FPS**, **Hack** and **Slash**, **Metroidvania**, and **Souls-like** blend broad appeal with strong design, balancing challenge and accessibility. Meanwhile, High Popularity–Low Appreciation (HP-LA) genres — including **FPS** and **Rogue-lite** — draw many players but often suffer from repetition or lack of polish, highlighting room for innovation. Low Popularity–High Appreciation (LP-HA) sub-genres, such as **Puzzle-Platformers** and **Shoot ’Em Ups**, may fly under the radar but enjoy devoted fans thanks to tight mechanics and rewarding gameplay. Lastly, Low Popularity–Low Appreciation (LP-LA) categories show signs of oversaturation and uneven quality, signaling a need for creative reinvention and improved execution to regain player trust and relevance.


<h1 id = "Predicting Success?"> Predicting Success? </h1>






<h1 id = "Conclusions"> Conclusions </h1>

Lorem ipsum...






<h2 id = "Next steps"> Next steps </h2>
Lorem ipsum...




