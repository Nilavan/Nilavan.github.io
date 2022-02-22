---
name: Tredence - Ode To Code
tools: [Machinehack, Optuna, featured]
image: ../assets/img/Tredence.jpg
description: Predicting Weather Using Alien Fruit Properties.
---

> [Competition](https://machinehack.com/hackathon/odetocode_predicting_weather_using_alien_fruit_properties/overview) by [Analytics India Magazine](https://analyticsindiamag.com/) and [Tredence](https://www.tredence.com/) on MachineHack.

## Contents:

1. [Introduction](#introduction)
2. [Problem statement](#problem)
3. [About the dataset](#data)
4. [Approach](#approach)
   1. [Data cleaning](#clean)
   2. [Models](#model)
   3. [CV and hyperparameters](#cv)
5. [Results](#result)

<div class="m-3" id="introduction">
    <br />
    <h2>👋 Introduction:</h2>
</div>

Competitions with tabular datasets are always fun. I've been focusing on Computer Vision with [RespAI](/projects/4-respai) and the [Petfinder competition](https://www.kaggle.com/nilavanakilan/petfinder-swin-svr-fastai-w-yolo) and this competition came as a pleasant surprise. I entered it as an escape/distraction from computer vision but that soon changed as I found myself working on it for hours together. The data presented here isn't real world and clearly human-made, with clean rows and a seemingly careful input of NaNs into specific columns. I spent most of my time figuring out methods to fill these NaNs with model predictions being the solution I went with finally. As beginner-friendly as it was, it did help me learn a great deal. This was the first time I explored hyperparameter tuning libraries (apart from sklearn's random search and grid search) and stuck with Optuna. Classical Machine Learning models aside, I took a Neural Network approach as well. Of course, my final submission was an ensemble of pretty much all the models I successfully evaluated. Below, I note down the info and details about the competition and my approach towards it.

<div class="m-3" id="problem">
    <br />
    <h2>🎯 Problem statement:</h2>
</div>

The year is 2050 and a team of astronauts from all over the world went on a mission to an Exoplanet and discovered a vast amount of life and awesome weather. The scientists began collecting data samples of fruits found in their landing site and were curious by their shape and size. They collected data for more than a solar year of the planet to understand the fruit growing conditions in different weathers.

To analyze data and grow fruits similar to earth, they began transmitting data back to the Earth, however, due to solar radiation, some data got corrupted and got lost in transmission. Back on Earth, the scientists figured they need to identify the type of climate the exoplanet has based on the properties of the fruit with the existing challenge of missing data. Help the scientists identify the earth-like season in which the fruit must have grown using the data collected.

<div class="m-3" id="data">
    <br />
    <h2>📚 About the dataset:</h2>
</div>

- Train: 42,748 rows x 14 columns
- Test: 18,321 rows x 14 columns

Find out more about the columns in the dataset [here.](https://machinehack.com/hackathon/odetocode_predicting_weather_using_alien_fruit_properties/data)

<div class="m-3" id="approach">
    <br />
    <h2>✅ Approach:</h2>
</div>

<div class="m-3" id="clean">
    <br />
    <h4>🧹 Data cleaning:</h4>
</div>

- NaNs were found in columns ring-type and gill-attachment
- Filled NaNs in gill-attachment using predictions from CatBoost [Tuned with Optuna]
- Separate NaNs in ring-type into a new column
- LabelEncode and OneHotEncode

<div class="m-3" id="model">
    <br />
    <h4>🧠 Models:</h4>
</div>

Ensemble of the following models:

- XGBClassifier
- CatBoostClassifier
- SVC
- RandomForestClassifier
- Neural network (Architecture below)

<div class="mermaid" align='center'>
flowchart LR

subgraph layer1
direction TB
B[Dense 128] --> C[Relu]
C --> D[Dropout 0.3]
end

subgraph layer2
direction TB
E[Dense 64] --> F[Relu]
F --> G[Dropout 0.2]
end

subgraph layer3
direction TB
H[Dense 16] --> I[Relu]
end

subgraph layer4
direction TB
J[Dense 4] --> K[Softmax]
end

A[Input] --> layer1
layer1 --> layer2
layer2 --> layer3
layer3 --> layer4
layer4 --> L[Output]

</div>

<div class="m-3" id="cv">
    <br />
    <h4>🚀 CV and hyperparameter tuning:</h4>
</div>

- Stratified 5 fold cross validation
- Binning using Rice rule
- Hyperparameter tuning ML models using Optuna:
  - RandomForest: {'n_estimators': 597, 'criterion': 'gini'}
  - CatBoost: {'n_estimators': 1170, 'learning_rate': 0.0631377357362828, 'max_depth': 14, task_type:’GPU’}

<br />

- Best CV scores:
  - XGBClassifier - 0.51658
  - CatBoostClassifier - 0.51611
  - SVC - 0.51925
  - RandomForestClassifier - 0.51838
  - Neural network - 0.52039

<div class="m-3" id="result">
    <br />
    <h2>🎯 Results:</h2>
</div>

- Final score: 0.51913
- Rank: 25
