---
layout: default
title: "Predictive Model"
subtitle: ""
vega: true
---

<h1 class = "full-width-wrapper superH1"> Predictive Model </h1>

## Overview
 
To understand what makes a game successful, we trained a set of machine learning models to predict **popularity**, **player appreciation**, and their combined expression as a **quadrant** (e.g. high-popularity/low-appreciation). The goal was not only to classify games into outcome categories, but also to uncover which features influence those outcomes most — using interpretable techniques like SHAP to peer inside the "black box" of the model.
 
## Problem Setup
 
We framed the task as a **classification problem** across three fronts:

<ul class = "in_text_list">
    <li> <b> Popularity Score </b>: Binary classification — _high_ vs _low_ based on the median score in the dataset. </li>
    <li> <b> Appreciation Score </b>: Binary classification — _high_ vs _low_ (also median split). </li>
    <li> <b> Quadrant Prediction </b>: Multiclass classification into four groups. </li>
    <ul class = "in_text_list">
        <li> High Popularity - High Appreciation </li>
        <li> High Popularity - Low Appreciation </li>
        <li> Low Popularity - High Appreciation </li>
        <li> Low Popularity - Low Appreciation </li>
    </ul>
</ul>

These categories help us understand how well a game resonates commercially and critically.


 
## Data and Feature Engineering
 
After filtering for games with a valid Metacritic page, we worked with a refined dataset of around **5,000 games**.
 
We used a combination of **numeric**, **categorical**, and **one-hot encoded tag features**:

<ul class = "in_text_list">
    <li> <b>Numerical</b>: `required_age`, `dlc_count`, `year`, `is_indie`, `wishlist_backloggd`, `num_supported_languages`, `num_audio_languages`, `num_platforms` </li>
    <li> <b>Categorical</b> (one-hot encoded):  Tags/attributes across 9 game design categories:`Themes & Moods`, `Top-Level Genres`, `Visuals & Viewpoint`, `Sub-Genres`, `Players`, `Story`, `Level Design`, `Sports`, and `initial/current_price_range`. </li>
</ul>

 
## Modeling Approach
 
We used the <b><a href="https://xgboost.ai/">XGBoost</a> classifier<b>, a high-performance gradient boosting algorithm well-suited for tabular data. Each model was tuned using a **grid search** over key hyperparameters to balance learning ability and generalization. Key tuning strategies included:

<ul class = "in_text_list">
    <li> Keeping `max_depth` and `n_estimators` low (1–2 and 15–25 respectively), </li>
    <li> Monitoring <b>early stopping</b> to prevent overfitting, </li>
    <li> Using `logloss` and `mlogloss` as evaluation metrics. </li>
</ul>

<figure>
  <div class = "genral_chartClass">
    <img src='assets/images/overfitting_pop.png' width = 500>
  </div>
  <figcaption class = "figcaption_class"> 
    Fig.1 - Training and validation loss vs number of estimators for popularity-only model with <code><var>max_depth</var> = 2</code>. To prevent overfitting the number of estimators must be kept low.
  </figcaption>
</figure>



 
## Model Performance

<table class = "custom_table">
    <tr>
        <td>Model</td>
        <td>Best Accuracy (CV)</td>
        <td>Train (CV)</td>
        <td>Best Parameters</td>
        <td>Notes</td>
    </tr>
    <tr>
        <td>Popularity Model</td>
        <td>0.865</td>
        <td>0.879</td>
        <td>
            <code>
                <var>max_depth</var>: 2, 
                <var>n_estimators</var>: 25, 
                <var>learning_rate: 0.5</var>, 
                <var>colsample_bytree</var>: 0.8, 
                <var>subsample</var>: 0.8, 
                <var>reg_alpha</var>: 0.5, 
                <var>reg_lambda</var>: 0.8,
                </code>
        </td>
        <td>Strong performance with minimal overfitting</td>
    </tr>
    <tr>
        <td>Appreciation Model</td>
        <td>0.725</td>
        <td>0.746</td>
        <td>
            <code>
                <var>max_depth</var>: 2, 
                <var>n_estimators</var>: 20, 
                <var>learning_rate</var>: 0.5, 
                <var>colsample_bytree</var>: 0.8, 
                <var>subsample</var>: 0.5, 
                <var>reg_alpha</var>: 0.5, 
                <var>reg_lambda</var>: 1,
            </code>
        </td>
        <td>Predictive accuracy is solid, especially given that appreciation is inherently more subjective.</td>
    </tr>
    <tr>
        <td>Quadrant Classifier</td>
        <td>0.616</td>
        <td>0.657</td>
        <td>
            <code>
                <var>max_depth</var>: 2, 
                <var>n_estimators</var>: 20, 
                <var>learning_rate</var>: 0.5, 
                <var>colsample_bytree</var>: 0.8, 
                <var>subsample</var>: 0.8, 
                <var>reg_alpha</var>: 0, 
                <var>reg_lambda</var>: 0.5,
            </code>
        </td>
        <td>Multi-class prediction is understandably more difficult, but the model performs well enough to support deeper SHAP-based analysis of what drives game outcomes.</td>
    </tr>
</table>


<figure>
  <div class = "genral_chartClass">
    <img src='assets/images/confusion_matrix_pop.png' width = 400>
    <img src='assets/images/confusion_matrix_appr.png' width = 400>
    <img src='assets/images/confusion_matrix_quad.png' width = 400>
  </div>
  <figcaption class = "figcaption_class"> 
    Fig.2 - Confusion matrices for each classification model.
  </figcaption>
</figure>















 
## Explainability: Using SHAP
 
To move beyond raw accuracy and into **insight**, we used <b><a href="https://shap.readthedocs.io/en/latest/">SHAP</a> (SHapley Additive exPlanations)<b> to interpret the models. SHAP provides per-feature attribution scores that show not only what features matter, but **how** they influence predictions — whether positively or negatively.
 
The SHAP summary plot shows the impact of each feature on the model's predictions across all samples. Each dot represents a game, positioned horizontally by how much that feature pushed the prediction higher or lower (the SHAP value). The color of the dot indicates the actual value of the feature for that game — with red meaning a high value and blue a low one. Features are sorted top to bottom by their overall importance (mean absolute SHAP value), so those at the top had the greatest influence on the model’s output. This plot helps you see not just which features matter most, but also how different values of those features affect predictions.
 
SHAP helped reveal:

<ul class = "in_text_list">
    <li> The dominant influence of `wishlist_backloggd` across all models  </li>
    <li> The asymmetric importance of features like `Multiplayer`, `Strategy`, `is_indie`, and `Open World` </li>
    <li> That high appreciation often hinges on tags like `Puzzle`, `Cute`, or `Funny`, while popularity leans on broader features like multiplayer or platform support </li>
    <li> The complexity of quadrant dynamics — e.g., how some features protect against a "low/low" outcome, while others increase the risk of being overhyped but underwhelming </li>
</ul>




 
## Limitations and Future Work

<ul class = "in_text_list">
    <li> <b>Data size</b> (~5,000 games) is relatively modest, especially for deep modeling of subjective traits like appreciation </li>
    <li> <b>Tag quality</b> depends on how consistently games are labeled, which may introduce noise. </li>
    <li> <b>Temporal generalization</b> is not tested — models were trained on a snapshot and may not fully predict future hits. </li>
    <li> <b>Additional features</b> related to marketing or reviews content could add deeper context to future models. </li>
</ul>



## Final Thoughts
 
These models aren’t crystal balls — but they offer a structured, data-driven look at what makes a game click. With accuracy above <b>85%</b> for popularity and compelling SHAP insights for all outcomes, the models help us surface the **signals behind success** — and maybe even spot the next sleeper hit.



