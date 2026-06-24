---
title: "Insurance Claim Prediction: My First End-to-End ML Project"
date: 2026-04-11
categories: [Blogs, ML_blog]
tags: [Journey, UET Faisalabad, Computer Engineering, Machine Learning, Python, Learning]
---

# Insurance Claim Prediction: My First End-to-End ML Project

Most of the small exercises I had done before this project gave me a clean dataset and a clear question to answer. The insurance claim prediction project was the first time I had to build something closer to a real workflow — start with raw, slightly messy data, figure out what question was even worth asking, and only then start training anything. It ended up being one of the most useful projects of the semester precisely because so much of the difficulty had nothing to do with the model itself.

The goal was to predict whether a policyholder was likely to file an insurance claim, based on attributes like age, policy details, and a handful of risk-related features in the dataset. Before touching any model, I spent a noticeable chunk of time just looking at the data — checking which columns had missing values, which ones were categorical and needed encoding, and which numeric columns had ranges so different from each other that they would need scaling before being fed into most algorithms. This part felt unglamorous compared to the idea of "training a machine learning model," but it quickly became obvious that skipping it would have produced a model that learned the wrong patterns, or no useful pattern at all.

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report

data = pd.read_csv("insurance_claims.csv")
data = data.dropna()

X = data.drop("claim_filed", axis=1)
y = data["claim_filed"]

X = pd.get_dummies(X, drop_first=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train_scaled, y_train)

predictions = model.predict(X_test_scaled)
print(classification_report(y_test, predictions))
```

One thing that surprised me was how much the class balance in the data mattered. Far fewer policyholders actually filed claims than did not, which meant a model could get a deceptively high accuracy simply by predicting "no claim" almost every time. That realization forced me to look beyond a single accuracy number and pay closer attention to precision and recall instead, since the cost of missing an actual claim is very different from the cost of a false alarm. This was the first time a metric other than plain accuracy actually mattered to me, rather than being a definition I had memorized for an exam.

I compared a logistic regression model against a random forest model on the same data, mostly out of curiosity about how different algorithms would handle the same imbalance. Logistic regression gave a simpler, more interpretable result, while the random forest handled the non-linear relationships between features noticeably better, at the cost of being harder to explain in plain terms. Choosing between an interpretable model and a more accurate but opaque one was a trade-off I had read about before but never actually had to weigh myself until this project forced the decision.

The dataset itself is the kind of real, fairly precise data that Dr. Bilal Ahmad consistently pushed us toward working with rather than synthetic toy examples, and it was easy to see why once I started working with it. The messiness, the class imbalance, the mix of categorical and numeric features — all of it forced decisions that a clean, artificially balanced dataset would never have required. Working through those decisions, even imperfectly, taught me far more than a tidier dataset would have.

By the time I had a working model with a reasonable classification report, the project had stopped feeling like a single technical task and started feeling like a small pipeline: clean the data, understand its imbalance, choose features carefully, pick a model suited to the problem, and only then evaluate it with metrics that actually reflect what matters. That pipeline mindset, more than the specific random forest model I ended up with, is the part of this project I expect to reuse in every machine learning task that comes after it.
