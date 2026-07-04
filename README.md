![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Lab | Decision Tree

## Goal

Develop a classification model using the Decision Tree algorithm: build a tree from historical patient data and their response to different medications, then use it to predict which drug suits a new patient.

## Dataset

`drug200.csv` contains 200 patient records with `Age`, `Sex`, `BP` (blood pressure), `Cholesterol`, and `Na_to_K` (sodium-to-potassium ratio) as features, and `Drug` (drugA, drugB, drugC, drugX, drugY) as the target — a multiclass classification problem.

## What Was Done

1. **Loaded and inspected the data** — read `drug200.csv` with pandas and checked its shape (200 rows, 6 columns).
2. **Pre-processed the features** — built the feature matrix `X` from `Age`, `Sex`, `BP`, `Cholesterol`, `Na_to_K`, then encoded the categorical columns (`Sex`, `BP`, `Cholesterol`) into numeric values with `sklearn.preprocessing.LabelEncoder`, since scikit-learn's decision trees require numeric input. The target vector `y` was set to the `Drug` column.
3. **Split the data** — used `train_test_split` with `test_size=0.3` and `random_state=3` to get 140 training rows and 60 test rows, then verified `X`/`y` shapes matched on both sides.
4. **Built the model** — created a `DecisionTreeClassifier` with `criterion="entropy"` and `max_depth=4`, and fit it on the training set.
5. **Predicted** — used the trained tree to predict drugs for the test set and spot-checked predictions against the true labels.
6. **Evaluated** — computed accuracy with `sklearn.metrics.accuracy_score`.
7. **Visualized** — plotted the fitted tree with `sklearn.tree.plot_tree` to inspect the splits and decision path.

## Results

- Train/test split: 140 / 60 samples (70/30 split).
- **Accuracy: 0.983** (drugTree correctly predicted the drug for 59 of 60 test patients).

## Key Learnings

- Decision trees in scikit-learn only accept numeric features, so categorical variables (`Sex`, `BP`, `Cholesterol`) must be encoded (e.g. with `LabelEncoder`) before fitting.
- Using `criterion="entropy"` lets the tree split on information gain, which is easy to interpret when visualizing the resulting splits.
- Limiting `max_depth` (here, 4) helps control model complexity and reduces the risk of overfitting on a small dataset like this one (200 rows).
- A fixed `random_state` in `train_test_split` makes the train/test split reproducible, which matters when comparing model changes across runs.
- Visualizing the tree (`plot_tree`) makes it possible to trace exactly which feature thresholds drive each prediction — useful for explaining the model's decisions, not just measuring its accuracy.
- High accuracy (98.3%) on a small, well-separated dataset like this is achievable with a shallow tree, but it's worth remembering that such results may not generalize to larger or noisier real-world data.

## Deliverables

- Completed `lab-decision-tree.ipynb` notebook with all exercise cells filled in and executed.

## Submission

- Upon completion, add your deliverables to git.
- Then commit git and push your branch to the remote.
- Make a pull request and paste the PR link in the submission field in the Student Portal.

<br>

**Good luck!**
