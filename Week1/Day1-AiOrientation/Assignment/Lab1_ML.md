# Lab Assignment: Supervised vs. Unsupervised Learning

## Objective

Given a one-line description of a real-world problem, decide:

1. **Learning paradigm** – Supervised or Unsupervised
2. **Problem type** – one of the following
   - Supervised: *Classification* (binary or multiclass) or *Regression*
   - Unsupervised: *Clustering*, *Dimensionality Reduction*, *Association Rule Mining*, or *Anomaly Detection*
3. **Reason** – one sentence justifying your choice

## Quick Reference

| Paradigm | What the data looks like | Problem types |
|----------|--------------------------|---------------|
| **Supervised** | Every training example has a known answer (a label or a number) | Classification (discrete class), Regression (continuous number) |
| **Unsupervised** | No answers are provided; the algorithm finds structure on its own | Clustering, Dimensionality Reduction, Association Rules, Anomaly Detection |

**Hints**
- Ask: *"Do I have historical examples with the correct answer attached?"* If yes, it is supervised.
- If the answer is a **number** (price, count, temperature), it is regression.
- If the answer is a **category** (yes/no, cat/dog/bird), it is classification.
- Words like *group, discover, find patterns, no labels* point to unsupervised.
- *"Detect"* is a trap word. Check whether labeled examples exist before deciding.

## Instructions

- Work through all 50 cases.
- Fill in the three blank columns for each case.
- Keep your reason to a single sentence.
- Time allotted: **45 minutes**.

## Cases

| # | Case | Learning (S / U) | Type | Reason |
|---|------|------------------|------|--------|
| 1 | Predict a house's sale price from size, location, and bedrooms | | | |
| 2 | Flag incoming email as spam or not spam | | | |
| 3 | Group shoppers by buying habits with no predefined segments | | | |
| 4 | Forecast tomorrow's high temperature | | | |
| 5 | Recognize handwritten digits 0 to 9 | | | |
| 6 | Find items frequently bought together in a supermarket | | | |
| 7 | Detect credit card fraud using a history of confirmed fraud cases | | | |
| 8 | Spot unusual network traffic with no labeled attacks | | | |
| 9 | Squash 1,000 gene-expression features into 2 axes for a plot | | | |
| 10 | Predict a student's exam score from hours studied | | | |
| 11 | Decide if a tumor is benign or malignant from biopsy features | | | |
| 12 | Organize an untagged news archive into topics | | | |
| 13 | Predict whether a subscriber will cancel next month | | | |
| 14 | Estimate hourly bike rentals at a station | | | |
| 15 | Segment satellite pixels into land types with no ground truth | | | |
| 16 | Predict a car's fuel economy from engine specs | | | |
| 17 | Label movie reviews positive, negative, or neutral from a tagged corpus | | | |
| 18 | Compress photos by keeping only the main visual components | | | |
| 19 | Build a "people also bought" list from transaction logs | | | |
| 20 | Predict loan default from applicant history | | | |
| 21 | Catch defective parts when only normal sensor readings are available | | | |
| 22 | Predict a stock's closing price | | | |
| 23 | Identify iris species from petal measurements | | | |
| 24 | Group songs into playlists by audio features without genre tags | | | |
| 25 | Predict food delivery time in minutes | | | |
| 26 | Detect the language of a text using labeled documents | | | |
| 27 | Find hidden themes in a pile of support tickets | | | |
| 28 | Estimate a person's age from a photo | | | |
| 29 | Predict whether a patient has diabetes from lab values | | | |
| 30 | Plot word embeddings on a 2-D map | | | |
| 31 | Predict salary from years of experience | | | |
| 32 | Detect a failing server from logs with no labeled failures | | | |
| 33 | Recognize which employee is at the door for access control | | | |
| 34 | Group near-duplicate documents for deduplication | | | |
| 35 | Forecast a building's energy use next month | | | |
| 36 | Find web pages usually visited in the same session | | | |
| 37 | Sort photos into cat, dog, or bird using tagged images | | | |
| 38 | Predict whether it will rain tomorrow | | | |
| 39 | Flag an unusual spending pattern on one bank account | | | |
| 40 | Predict units of a product sold next week | | | |
| 41 | Diagnose which of 5 diseases a patient has | | | |
| 42 | Find communities in a social network graph | | | |
| 43 | Predict crop yield in tons from rainfall and soil data | | | |
| 44 | Classify tweets as hate speech or not from a labeled set | | | |
| 45 | Reduce an 80-question survey to a few underlying factors | | | |
| 46 | Predict a person's annual medical insurance cost | | | |
| 47 | Discover which genes tend to be expressed together | | | |
| 48 | Assign a bank transaction to one of 12 expense categories | | | |
| 49 | Compress 200 sensor channels into 10 summary signals | | | |
| 50 | Predict a movie rating from 1 to 5 stars from user history | | | |

## Reflection Questions

Answer briefly after completing the table.

1. Pick two cases that both use the word *detect* but landed in different paradigms. What made the difference?
2. Case 38 asks for a probability. Why is it still classification and not regression?
3. Case 50 could be argued either way. State both arguments and say which you would choose and why.
4. Give one new example of your own for each of the six problem types.

## Submission

Submit this file with the table and reflection questions completed. Name it `<your_name>_ml_lab.md`.
