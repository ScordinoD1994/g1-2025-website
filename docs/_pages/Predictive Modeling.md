---
layout: default
title: "Predictive Model"
subtitle: ""
vega: true
---

<div class="full-width-wrapper">
    <img src="{{ site.baseurl }}/assets/images/header.svg" alt="sbd-pattern" class="full-width-image filter-green">
</div>

<h1 class = "full-width-wrapper superH1"> Predictive Model </h1>

<figure style = "padding: 40px;">
  <img src='assets/images/pacman_separator.png' style = "width: 100%">
</figure>


## Overview
 
To understand what makes a game successful, we trained a set of machine learning models to predict **popularity**, **player appreciation**, and their combined expression as a **quadrant** (e.g. high-popularity/low-appreciation). The goal was not only to classify games into outcome categories, but also to uncover which features influence those outcomes most — using interpretable techniques like SHAP to peer inside the "black box" of the model.
 
## Problem Setup
 
We framed the task as a **classification problem** across three fronts:

<ul class = "in_text_list">
    <li> <b> Popularity Score </b>: Binary classification — high vs low based on the median score in the dataset. </li>
    <li> <b> Appreciation Score </b>: Binary classification — high vs low (also median split). </li>
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
    <li> <b>Numerical</b>: <var>required_age</var>, <var>dlc_count</var>, <var>year</var>, <var>is_indie</var>, <var>wishlist_backloggd</var>, <var>num_supported_languages</var>, <var>num_audio_languages</var>, <var>num_platforms</var> </li>
    <li> <b>Categorical</b> (one-hot encoded):  Tags/attributes across 9 game design categories: <var>Themes & Moods</var>, <var>Top-Level Genres</var>, <var>Visuals & Viewpoint</var>, <var>Sub-Genres</var>, <var>Players</var>, <var>Story</var>, <var>Level Design</var>, <var>Sports</var>, and <var>initial/current_price_range</var>. </li>
</ul>

 
## Modeling Approach
 
We used the <b><a href="https://xgboost.ai/">XGBoost</a> classifier</b>, a high-performance gradient boosting algorithm well-suited for tabular data. Each model was tuned using a **grid search** over key hyperparameters to balance learning ability and generalization. Key tuning strategies included:

<ul class = "in_text_list">
    <li> Keeping <var>max_depth</var> and <var>n_estimators</var> low (1–2 and 15–25 respectively), </li>
    <li> Monitoring <b>early stopping</b> to prevent overfitting, </li>
    <li> Using <var>logloss</var> and <var>mlogloss</var> as evaluation metrics. </li>
</ul>

<figure>
  <div class = "general_chartClass">
    <img src='assets/images/overfitting_pop.png' width = 500 height = 500 style = 'padding: 15px;'>
    <img src='assets/images/overfitting_appr.png' width = 500 height = 500 style = 'padding: 15px;'>
    <img src='assets/images/overfitting_quad.png' width = 500 height = 500 style = 'padding: 15px;'>
  </div>
  <figcaption class = "figcaption_class"> 
    Fig.1 - Training and validation loss vs number of estimators for popularity-only (left plot), appreciation-only (middle plot) and quadrant (right plot) models with <code><var>max_depth</var> = 2</code>. In each case, to prevent overfitting the number of estimators must be kept low.
  </figcaption>
</figure>

In order to find the best parameters configuration we used <code>Gridsearch</code>. In Fig.2 we display the best configurations with magenta dots.

<figure>
  <div class = "general_chartClass">
    <img src='assets/images/overfitting_pop_2.png' width = 500 height = 500 style = 'padding: 15px;'>
    <img src='assets/images/overfitting_appr_2.png' width = 500 height = 500 style = 'padding: 15px;'>
    <img src='assets/images/overfitting_quad_2.png' width = 500 height = 500 style = 'padding: 15px;'>
  </div>
  <figcaption class = "figcaption_class"> 
    Fig.2 - Best parameters selection for popularity-only (left plot), appreciation-only (middle plot) and quadrant (right plot) models. The red dot represents our best model on the mean validation accurary -  mean train accuracy plane. Models close to the diagonal line do not suffer from overfitting or underfitting.
  </figcaption>
</figure>



## Model Performance

Tab.1 repots parameters and performance for the best models.

<table class = "custom_table">
    <tr>
        <td>Model</td>
        <td>Mean Train Accuracy (CV)</td>
        <td>Mean Validation Accuracy (CV)</td>
        <td>Test Accuracy</td>
        <td>Parameters</td>
        <td>Notes</td>
    </tr>
    <tr>
        <td>Popularity Model</td>
        <td>0.879</td>
        <td>0.865</td>
        <td>0.838</td>
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
        <td>0.746</td>
        <td>0.725</td>
        <td>0.729</td>
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
        <td>0.657</td>
        <td>0.616</td>
        <td>0.611</td>
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
    <caption class = "figcaption_class">
        Tab.1 - Train accuracy (second column), validation accuracy (third column), test accuracy (fourth column) and best parameters (fifth column) for each predictive model considered.
    </caption>
</table>

Tab.2, Tab.3 and Tab.4 show the classification report for each model while Fig.3 displays the corresponding confusion matrices.

<div class="full-width-wrapper general_chartClass">
    <table class = "custom_table">
        <thead>
            <td>  </td>
            <td> precision </td>
            <td> recall </td>
            <td> f1-score </td>
            <td> support </td>
        </thead>
        <tr>
            <td> 0 </td>
            <td> 0.816 </td>
            <td> 0.875</td>
            <td> 0.844</td>
            <td> 471</td>
        </tr>
        <tr>
            <td> 1 </td>
            <td> 0.865</td>
            <td> 0.802</td>
            <td> 0.832</td>
            <td> 470 </td>
        </tr>
        <tr>
            <td> accuracy </td>
            <td>  </td>
            <td>  </td>
            <td> 0.838 </td>
            <td> 941 </td>
        </tr>
        <tr>
            <td> macro avg </td>
            <td> 0.840 </td>
            <td> 0.838 </td>
            <td> 0.838 </td>
            <td> 941 </td>
        </tr>
        <tr>
            <td> weighted avg </td>
            <td> 0.840 </td>
            <td> 0.838</td>
            <td> 0.838</td>
            <td> 941</td>
        </tr>
        <caption class = "figcaption_class">
            Tab.2 - Popularity classification report. Class 0 corresponds to Low Popularity while class 1 corresponds to High Popularity.
        </caption>
    </table>
    <table class = "custom_table">
        <thead>
            <td>  </td>
            <td> precision </td>
            <td> recall </td>
            <td> f1-score </td>
            <td> support </td>
        </thead>
        <tr>
            <td> 0 </td>
            <td> 0.708 </td>
            <td> 0.781</td>
            <td> 0.743</td>
            <td> 471</td>
        </tr>
        <tr>
            <td> 1 </td>
            <td> 0.755</td>
            <td> 0.677</td>
            <td> 0.714</td>
            <td> 470 </td>
        </tr>
        <tr>
            <td> accuracy </td>
            <td>  </td>
            <td>  </td>
            <td> 0.729 </td>
            <td> 941 </td>
        </tr>
        <tr>
            <td> macro avg </td>
            <td> 0.732 </td>
            <td> 0.729 </td>
            <td> 0.728 </td>
            <td> 941 </td>
        </tr>
        <tr>
            <td> weighted avg </td>
            <td> 0.732 </td>
            <td> 0.729</td>
            <td> 0.728</td>
            <td> 941</td>
        </tr>
        <caption class = "figcaption_class">
            Tab.3 - Appreciation classification report. Class 0 corresponds to Low Appreciation while class 1 corresponds to High Appreciation.
        </caption>
    </table>
    <table class = "custom_table">
        <thead>
            <td>  </td>
            <td> precision </td>
            <td> recall </td>
            <td> f1-score </td>
            <td> support </td>
        </thead>
        <tr>
            <td> 0 </td>
            <td> 0.709 </td>
            <td> 0.659</td>
            <td> 0.683</td>
            <td> 311</td>
        </tr>
        <tr>
            <td> 1 </td>
            <td> 0.483</td>
            <td> 0.631</td>
            <td> 0.547</td>
            <td> 160</td>
        </tr>
        <tr>
            <td> 2 </td>
            <td> 0.410</td>
            <td> 0.544</td>
            <td> 0.468</td>
            <td> 160</td>
        </tr>
        <tr>
            <td> 3 </td>
            <td> 0.788 </td>
            <td> 0.587 </td>
            <td> 0.673 </td>
            <td> 310 </td>
        </tr>
        <tr>
            <td> accuracy </td>
            <td>  </td>
            <td>  </td>
            <td> 0.611 </td>
            <td> 941 </td>
        </tr>
        <tr>
            <td> macro avg </td>
            <td> 0.598 </td>
            <td> 0.605 </td>
            <td> 0.593 </td>
            <td> 941 </td>
        </tr>
        <tr>
            <td> weighted avg </td>
            <td> 0.646 </td>
            <td> 0.611</td>
            <td> 0.620</td>
            <td> 941</td>
        </tr>
        <caption class = "figcaption_class">
            Tab.4 - Quadrant classification report. Class 0 corresponds to Low Popularity / Low Appreciation, class 1 corresponds to High Popularity / Low Appreciation, class 2 corresponds to Low Popularity / High Appreciation while class 3 corresponds to High Popularity / High Appreciation.
        </caption>
    </table>
</div>

<figure>
  <div class = "general_chartClass">
    <img src='assets/images/confusion_matrix_pop.png' width = 500 height = 500 style = 'padding: 15px;'>
    <img src='assets/images/confusion_matrix_appr.png' width = 500 height = 500 style = 'padding: 15px;'>
    <img src='assets/images/confusion_matrix_quad.png' width = 500 height = 500 style = 'padding: 15px;'>
  </div>
  <figcaption class = "figcaption_class"> 
    Fig.3 - Confusion matrices for popularity-only (left plot), appreciation-only (middle plot) and quadrant (right plot) best models.
  </figcaption>
</figure>


In order to have some insight on the model performances in the various cases, we tried to run a clustering algorithm (<b>Kmeans</b>) using as features the ones defining Popularity and Appreciation scores. This approach results in two macro-clusters. Fig.4 shows distributions for popularity and appreciation for each cluster. As we can see, only popularity can be considered well separated into two classes (High Popularity and Low Popularity), while it is not possible to obtain analogous informations for appreciation. This can justify the worse performance of our model in predicting appreciation or in the multi-class classification task. Tab.5 reports mean and standard deviation for popularity and appreciation for the whole dataset and two clusters.

<div class="full-width-wrapper general_chartClass">
    <figure>
    <img src='assets/images/kmeans_clustering_distributions.png' width = 600 style = 'padding: 15px;'>
    <figcaption class = "figcaption_class"> Fig.4 - Popularity and appreciation distribution on the whole dataset (white histogram) and for the two clustes. </figcaption>
    </figure>
    <table class = "custom_table">
        <thead>
            <td>  </td>
            <td> Mean </td>
            <td> Std  </td>
        </thead>
        <tr>
            <td> Dataset Popularity </td>
            <td> 0.403 </td>
            <td> 0.185 </td>
        </tr>
        <tr>
            <td> Cluster 0 Popularity </td>
            <td> 0.488 </td>
            <td> 0.155 </td>
        </tr>
        <tr>
            <td> Cluster 1 Popularity </td>
            <td> 0.228 </td>
            <td> 0.097 </td>
        </tr>
        <tr>
            <td> Dataset Appreciation </td>
            <td> 0.687 </td>
            <td> 0.148 </td>
        </tr>
        <tr>
            <td> Cluster 0 Appreciation </td>
            <td> 0.719 </td>
            <td> 0.135 </td>
        </tr>
        <tr>
            <td> Cluster 1 Appreciation </td>
            <td> 0.623 </td>
            <td> 0.153 </td>
        </tr>
        <caption class = "figcaption_class">
            Tab.5 - Mean and standard deviation for popularity and appreciation for the whole dataset and two clusters.
        </caption>
    </table>
</div>

 
## Explainability: Using SHAP
 
To move beyond raw accuracy and into **insight**, we used <b><a href="https://shap.readthedocs.io/en/latest/">SHAP</a> (SHapley Additive exPlanations)</b> to interpret the models. SHAP provides per-feature attribution scores that show not only what features matter, but **how** they influence predictions — whether positively or negatively.

The SHAP summary plot shows the impact of each feature on the model's predictions across all samples. Each dot represents a game, positioned horizontally by how much that feature pushed the prediction higher or lower (the SHAP value). The color of the dot indicates the actual value of the feature for that game — with red meaning a high value and blue a low one. Features are sorted top to bottom by their overall importance (mean absolute SHAP value), so those at the top had the greatest influence on the model’s output. This plot helps you see not just which features matter most, but also how different values of those features affect predictions.

<figure>
  <img src='assets/images/shap_summary_plot_pop.png' style = "width: 100%">
  <figcaption class = "figcaption_class"> Fig.5 - SHAP summary plot for popularity score-only prediction. </figcaption>
</figure>

<figure>
  <img src='assets/images/shap_summary_plot_appr.png' style = "width: 100%">
  <figcaption class = "figcaption_class"> Fig.6 - SHAP summary plot for appreciation score-only prediction. </figcaption>
</figure>

<figure>
  <img src='assets/images/shap_summary_plot_High App-High Pop.png' style = "width: 100%">
  <figcaption class = "figcaption_class"> Fig.7 - SHAP summary plot for HP-HA quadrant prediction. </figcaption>
</figure>


<figure>
  <img src='assets/images/shap_summary_plot_Low App-High Pop.png' style = "width: 100%">
  <figcaption class = "figcaption_class"> Fig.8 - SHAP summary plot for HP-LA quadrant prediction. </figcaption>
</figure>


<figure>
  <img src='assets/images/shap_summary_plot_High App-Low Pop.png' style = "width: 100%">
  <figcaption class = "figcaption_class"> Fig.9 - SHAP summary plot for LP-HA quadrant prediction. </figcaption>
</figure>


<figure>
  <img src='assets/images/shap_summary_plot_Low App-Low Pop.png' style = "width: 100%">
  <figcaption class = "figcaption_class"> Fig.10 - SHAP summary plot for LP-LA quadrant prediction. </figcaption>
</figure>


SHAP helped reveal:

<ul class = "in_text_list">
    <li> The dominant influence of <var>wishlist_backloggd</var> across all models  </li>
    <li> The asymmetric importance of features like <var>Multiplayer</var>, <var>Strategy</var>, <var>is_indie</var>, and <var>Open World</var> </li>
    <li> That high appreciation often hinges on tags like <var>Puzzle</var>, <var>Cute</var>, or <var>Funny</var>, while popularity leans on broader features like multiplayer or platform support </li>
    <li> The complexity of quadrant dynamics — e.g., how some features protect against a "low/low" outcome, while others increase the risk of being overhyped but underwhelming </li>
</ul>



## Limitations

<ul class = "in_text_list">
    <li> <b>Data size</b> (~5,000 games) is relatively modest, especially for deep modeling of subjective traits like appreciation </li>
    <li> <b>Tag quality</b> depends on how consistently games are labeled, which may introduce noise. </li>
    <li> <b>Temporal generalization</b> is not tested — models were trained on a snapshot and may not fully predict future hits. </li>
    <li> <b>Additional features</b> related to marketing or reviews content could add deeper context to future models. </li>
</ul>






