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

Feature engineering turned out to be a more interesting part of this project than I expected going in. A few of the raw columns in the dataset were not very predictive on their own, but combining them into new derived features made a noticeable difference once I started experimenting. For example, looking at the ratio between a policyholder's age and how long they had held their policy revealed a pattern that neither column showed clearly by itself. Building that kind of derived feature required actually understanding what the underlying numbers represented in the real world, not just treating them as abstract inputs to a model, which connected back to lessons from Database Systems about understanding the meaning behind raw data rather than just its structure.

Interpreting the random forest's feature importances after training was another step that added real value beyond just getting predictions. Seeing which features the model relied on most heavily gave me a way to sanity-check whether it had learned something reasonable or something accidental. When one of the top features turned out to be a policy type that genuinely does carry different risk profiles in the real world, it gave me more confidence that the model had picked up on a real pattern rather than a coincidence in the training data. If an irrelevant column like a record ID had shown up as highly important instead, that would have been a clear signal that something in the pipeline was leaking information it should not have access to.

I also spent time experimenting with different decision thresholds for converting the model's predicted probabilities into a final yes-or-no claim prediction. The default threshold of fifty percent is not always the right choice, especially with imbalanced classes like this one, where missing an actual claim can be far more costly than incorrectly flagging a policyholder who never ends up filing one. Adjusting that threshold and watching precision and recall shift in opposite directions gave me a concrete, hands-on understanding of a trade-off that had only ever been a paragraph in a textbook before this project.

Looking back at this project alongside the smaller exercises earlier in the semester, the difference in scope is what stands out most. This was the first time I had to make a real decision at almost every stage — how to handle missing data, which features to engineer, which model to trust, where to set a threshold — rather than following a fixed set of instructions toward a single correct answer. That difference, more than any specific technique, is what made this project feel like a genuine step toward doing machine learning rather than just practicing it.

Feature selection turned out to be one of the most underrated parts of the entire process. Early on, I simply fed every available column into the model, assuming more information could only help. The result was a model that took noticeably longer to train and did not perform any better than a version trained on a carefully chosen subset of features. Going back and removing columns that were clearly irrelevant to whether someone files a claim, or that overlapped heavily with another feature already in the dataset, actually improved performance slightly while making the whole pipeline faster and easier to reason about. That experience taught me that more data fed into a model is not automatically better data, and that understanding what each feature actually represents matters as much as how many features you include.

I also spent time experimenting with different probability thresholds for classifying a claim as likely versus unlikely, instead of accepting the default fifty percent cutoff scikit-learn uses automatically. Lowering that threshold caught more genuine claims at the cost of more false alarms, while raising it did the opposite. Seeing those trade-offs change in real time as I adjusted a single number made the abstract idea of a precision-recall trade-off feel concrete in a way that reading about it in a textbook never quite managed, and it left me with a much stronger appreciation for why choosing the right threshold for a real business problem is itself a meaningful design decision, not just a technical afterthought.
