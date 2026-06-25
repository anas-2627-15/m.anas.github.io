---
title: "My Machine Learning Experience"
date: 2026-04-12
images:
  path: /assets/img/posts/8.jpg
categories:
  - Course Learning
tags: [Journey, UET Faisalabad, Computer Engineering, Machine Learning, Python, Learning]
---

# My Machine Learning Experience

Machine Learning was not a formal course on my timetable this semester, but it ended up taking up a surprising amount of my time anyway, mostly because of how it was introduced to us alongside Database Systems. Dr. Bilal Ahmad, whose actual courses with us were Programming Fundamentals and Database Systems, has a background in training AI and ML models, and he often used examples from that world usually built on real, carefully collected datasets like medical or operational data to explain why structured, trustworthy data matters so much. That framing made me curious enough to actually sit down and work through a small ML project of my own rather than just hearing about the field secondhand.

I chose a Walmart weekly sales dataset for my first real attempt, mostly because it was large enough to feel realistic but still manageable for someone trying machine learning for the first time. The project started, predictably, with cleaning the data. There were missing values in some columns, dates that needed to be converted into a usable format, and outliers in the sales figures that looked like they could either be genuine spikes from holiday weeks or errors in the data itself. Deciding how to handle each of these cases taught me that a huge portion of machine learning work happens before any model is involved at all.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error

data = pd.read_csv("walmart_sales.csv")
data = data.dropna()

X = data.drop("Weekly_Sales", axis=1)
y = data["Weekly_Sales"]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

predictions = model.predict(X_test)
print("RMSE:", mean_squared_error(y_test, predictions, squared=False))
```

Visualization turned out to matter just as much as the modeling step. Plotting sales over time using matplotlib and seaborn made patterns visible that I would never have noticed by scrolling through raw numbers seasonal spikes around certain holidays, noticeably different behavior across different store locations, and a few weeks that stood out as clear anomalies. Those visual patterns directly shaped which features I decided to include in the model, since a feature that looked meaningless in a table of numbers sometimes turned out to be very informative once plotted against sales over time.

I trained two different models on the same processed data a decision tree and a random forest mainly to compare how they handled the same patterns. The decision tree was easy to interpret and fast to train, but it tended to overfit, performing well on the training data while struggling on data it had not seen before. The random forest, built from many decision trees combined together, handled this much better, smoothing out the overfitting problem at the cost of being harder to explain in simple terms. Watching this trade-off play out directly, rather than just reading about overfitting in a definition, made the concept stick in a way no lecture slide had managed before.

Saving the trained model using joblib was a small step that taught me something about how machine learning fits into a larger system. A model is not very useful sitting only inside a Jupyter notebook; being able to save it and reload it meant I could imagine, even if I never built it, a small application that loads this trained model and produces predictions on new data without retraining from scratch every time. That shift in thinking from "I trained a model" to "this model could be a component in something larger" felt like an important step in understanding what machine learning actually looks like outside of an academic exercise.

What stayed with me most from this experience is something Dr. Bilal Ahmad emphasized repeatedly: a model is only as good as the data underneath it. No amount of algorithm tuning could have fixed a dataset full of unreliable, poorly collected values, and no clever model architecture replaces the unglamorous work of cleaning and understanding data before training anything on it. That single idea connected this entire machine learning experience back to everything I had already learned in Database Systems about structure, integrity, and trustworthy data two subjects that, on the surface, looked unrelated, but turned out to depend on each other completely.

Tuning the random forest's hyperparameters was a small but genuinely educational detour within this project. Increasing the number of trees improved performance up to a point, after which the gains became negligible while training time kept increasing, which gave me a concrete feel for diminishing returns rather than just a definition of the term. Adjusting the maximum depth of each tree showed the opposite kind of trade-off: too shallow, and the model could not capture the more subtle patterns in the data; too deep, and it started memorizing quirks specific to the training set rather than learning anything that generalized. Watching the RMSE shift in response to each of these changes turned hyperparameter tuning from an abstract checklist into something closer to a hands-on experiment with immediate feedback.

Cross-validation was another piece I added after my first attempt at evaluation felt slightly too convenient a single train-test split can sometimes flatter a model simply through luck in how the data happened to be divided. Running the same model across several different splits and averaging the results gave me a more honest sense of how it would likely perform on data it had never seen, and it also taught me to be a little more skeptical of any single strong result before treating it as proof that a model is actually good.

I also spent some time simply sitting with the visualizations longer than the project strictly required, mostly out of curiosity about what other patterns the data might be hiding. Plotting sales against store size, for instance, revealed a relationship I had not specifically gone looking for, and noticing it changed how I thought about which features might matter before I even started formal feature selection. That habit of exploring a dataset a little further than necessary, just to see what shows up, is something I want to keep doing in future projects rather than treating visualization as a box to check before getting to the "real" modeling work.

By the end of this project, the gap between reading about machine learning concepts in a tutorial and actually sitting with a messy, real dataset and making my own judgment calls had narrowed considerably. The concepts themselves were not new by the time I finished overfitting, feature importance, evaluation metrics but having lived through each of them on data I had cleaned and understood myself made them feel earned in a way that reading about them never quite managed.

I also learned, somewhat by accident, how much patience model training itself requires compared to the rest of the pipeline. The data cleaning and exploration took hours spread across several sessions, while actually fitting the random forest model on the prepared data took only a few seconds once everything was ready. That imbalance surprised me at first, since I had assumed training would be the slow, computationally heavy part of the whole process. It reinforced something I had already started suspecting from the insurance claim project: the genuinely hard, time-consuming work in machine learning is almost always upstream of the model itself, in decisions about data quality and feature selection, not in the training step that gets most of the attention in casual conversations about the field.

Comparing the predicted sales values against the actual figures in the test set, week by week, also gave me a more honest picture of how a model performs than the single RMSE number alone. Some weeks the prediction was extremely close; others, usually around unusual holiday spikes, were noticeably off. Seeing exactly where the model struggled, rather than only seeing one aggregate error metric, made it clear that "the model works" is rarely a complete sentence — a more honest version is usually closer to "the model works well in these conditions and less well in these other ones," and learning to think in those more specific terms felt like a genuine step toward thinking like someone who actually understands the data, rather than someone who just ran a script that produced a number.
