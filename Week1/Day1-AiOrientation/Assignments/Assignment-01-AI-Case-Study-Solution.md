# Assignment 01: AI Case Study – Supervised & Unsupervised Learning
## Solution Guide

>
> This guide gives model answers, marking notes and common mistakes. Participants' answers will vary in wording. Award marks for correct reasoning, not for matching this text word for word.

---

## Part 1: Identify business problems suitable for AI/ML (20 marks)

### Model answer

Participants should find most of the following. Six well-reasoned items earn full marks; award partial marks for fewer or weaker justifications.

| # | Business problem | Business outcome | Why ML rather than rules |
|---|------------------|------------------|--------------------------|
| P1 | **Demand forecasting**: predict daily/weekly units per SKU per store | Fewer stock-outs, less perishable waste, lower inventory cost | Demand depends on the interaction of seasonality, weather, promotions and local events across 140 stores and thousands of SKUs. No human can maintain rules at that scale; the relationships change over time. |
| P2 | **Customer segmentation** for marketing | Higher open and conversion rates, less email fatigue | The segments are unknown. ML can discover natural groupings in behaviour that marketers can then interpret. |
| P3 | **Support ticket classification and routing** | Faster first response, agent time saved (two minutes × 9,000 tickets per week ≈ 300 agent-hours per week) | Free-text is messy; keyword rules break on synonyms, typos and mixed-topic tickets. A trained text classifier generalises. |
| P4 | **Payment fraud detection** | Lower fraud losses (1.2% of e-commerce revenue), fewer false declines | Fraud patterns are subtle and adversarial; fraudsters adapt to fixed thresholds. A model can weigh many signals jointly and be retrained. |
| P5 | **Anomaly detection** on refrigeration sensors (predictive maintenance) and on store return patterns | Avoided equipment failure and spoilage; early detection of return abuse or product issues | "Normal" is multi-dimensional and differs per unit; an unsupervised model can learn the baseline and flag deviations without pre-defined thresholds. |
| P6 | **Product de-duplication / similarity clustering** across 60,000 SKUs | Cleaner catalogue, better search, consolidated purchasing | Names vary in wording and spelling; exact-match rules fail. Embedding-based similarity handles fuzzy matches. |
| P7 | **Employee attrition prediction** | Lower turnover cost, targeted retention actions | Many weak signals (absences, shift pattern, pay band, tenure) combine non-linearly. Historical outcomes exist to learn from. |
| P8 | **Product recommendation** from clickstream | Higher basket size and conversion | Preferences are individual and emergent from millions of interactions; collaborative filtering scales where hand-curated lists cannot. |
| P9 | **Review sentiment analysis** | Full coverage of reviews instead of a sampled subset; faster detection of product problems | Language is varied; sentiment depends on context, sarcasm and negation. A trained classifier handles this better than word lists. |

### Non-ML or simple-analytics concern

Accept any well-argued example. Good answers include:

- **"Nobody looks at the data warehouse."** The first, cheapest win for supply chain is a dashboard of last year's sales by store and SKU with promotion overlays. That is reporting, not ML, and should happen before a forecasting model.
- **"Agents spend two minutes routing tickets."** Part of this is a process problem. A structured intake form with a mandatory "topic" drop-down would remove much of the routing work with zero ML.
- **Exit interview analysis.** Simple tabulation of stated reasons by store and manager is analytics, not ML, and may be more actionable than a prediction model.

### Marking notes

- 2 marks per problem (up to 12) for problem statement + outcome; up to 6 marks for the quality of "why ML" reasoning across the set; 2 marks for a sensible non-ML concern.
- Deduct if the participant lists the same problem twice under different names (for example "forecasting" and "inventory optimisation" with no distinction).
- Do not penalise participants who list problems not shown here, provided the reasoning is sound.

---

## Part 2: Classify scenarios as supervised or unsupervised learning (25 marks)

### Model answer

| # | Supervised / Unsupervised | Task type | Target variable | Justification |
|---|---------------------------|-----------|-----------------|---------------|
| S1 | Supervised | Regression (time-series forecasting) | units_sold (next week) | Historical units_sold is a known numeric outcome for every past date; the model learns to predict a continuous value. |
| S2 | Unsupervised | Clustering | None | No segment labels exist. The algorithm (for example k-means) groups members by similarity in behaviour and demographics. |
| S3 | Supervised | Multi-class classification (text) | agent_assigned_category | Three years of tickets already carry a human-assigned category, which is exactly the label needed. |
| S4 | Supervised | Binary classification | chargeback_flag | Eighteen months of transactions carry a yes/no fraud outcome. Note: a strong answer mentions class imbalance (fraud is rare). |
| S5 | Unsupervised | Anomaly / outlier detection | None | The case says there is no history of labelled failures. The model learns the normal operating envelope and flags deviations. |
| S6 | Unsupervised | Clustering (often on text embeddings) | None | No "belongs together" tags exist. Group by similarity of titles, descriptions and attributes. |
| S7 | Supervised | Binary classification | left_company (within six-month window) | HR records include whether each past employee left, so the outcome is known for training. |
| S8 | Unsupervised (accept "either" with justification) | Association rules / collaborative filtering | None | Market-basket and co-occurrence methods find items frequently bought together without a label. Accept supervised framing if the participant proposes predicting purchase_flag from clickstream features. |
| S9 | Supervised | Multi-class classification (sentiment) | star_rating (mapped to positive / neutral / negative) | The star rating is a ready-made proxy label for sentiment. A strong answer notes that it is a proxy and may be imperfect. |
| S10 | Unsupervised | Dimensionality reduction (for example PCA) | None | The goal is to compress features, not predict an outcome. No label is involved. |

### Marking notes

- 2.5 marks per scenario: 1 for supervised/unsupervised, 0.5 for task type, 0.5 for target variable (or correctly stating "none"), 0.5 for justification.
- S8 is deliberately open. Either answer earns full marks **if the participant explains the framing**. "Unsupervised because recommendation" with no reasoning earns half.
- Common error: calling S5 supervised because "we know what failures look like". The case explicitly states there is no labelled failure history. Award 0 for supervised/unsupervised on S5 but give the task-type mark if they say "anomaly detection".
- Common error: calling S9 unsupervised because "the text is unstructured". Unstructured input does not make the task unsupervised; the presence or absence of a label does.

---

## Part 3: Labelled vs. unlabelled datasets (20 marks)

### 3.1 Model answer

| Dataset | Labelled? | Label column | Business question the label answers |
|---------|-----------|--------------|-------------------------------------|
| D1 Daily sales | **Labelled** (for forecasting) | units_sold | "How many will we sell?" Each past row's units_sold is the ground truth for a forecasting model. Note: this is a case where the "label" is just a historical measurement. |
| D2 Loyalty profiles | **Unlabelled** (for segmentation) | None | There is no segment column. Could become labelled for other tasks (for example, churn, if "lapsed" were defined). |
| D3 Support tickets | **Labelled** | agent_assigned_category | "Which category does this ticket belong to?" Also resolution_time could serve as a regression label. |
| D4 E-commerce transactions | **Labelled** (last 18 months only) | chargeback_flag | "Was this transaction fraudulent?" Note the limited window. |
| D5 Refrigeration sensors | **Unlabelled** | None | No failure or fault column. Suitable for anomaly detection. |
| D6 Product catalogue | **Unlabelled** | None | No grouping or duplicate-of column. |
| D7 HR records | **Labelled** | left_company (and exit_date for timing) | "Did this employee leave?" |
| D8 Clickstream | **Partially / depends** | purchase_flag could act as a label | Unlabelled for discovering co-view patterns; labelled if the task is "predict whether this session converts". |
| D9 Product reviews | **Labelled** (proxy) | star_rating | "Is this review positive or negative?" The star rating is a proxy label, not a direct sentiment label. |

Award 1 mark per dataset for the correct classification and label identification (9 marks). Accept "depends on use case" for D1, D2 and D8 if explained.

### 3.2 Labelling plan for an unlabelled dataset (6 marks)

Example for **D5 Refrigeration sensors**:

> BrightCart could create failure labels by joining the sensor logs to maintenance work orders. Each unit that had a compressor replacement or emergency callout gets a "failure" event at the timestamp of the ticket, and all readings in the 72 hours before it are labelled "pre-failure". Everything else is "normal". The facilities team and a data engineer would do this; it is a one-off join plus some manual checking of perhaps 200 incidents over two years, so a few days of work. The main risk is that work orders are logged late or imprecisely, so the "pre-failure" window is wrong and the model learns from mislabelled readings.

Example for **D6 Product catalogue**:

> Merchandising assistants could review candidate pairs proposed by a simple string-similarity script and mark each pair as "same product" or "different". Reviewing 10,000 pairs at 20 seconds each is about 55 hours. The risk is inconsistent judgement between reviewers (for example whether pack sizes count as the same product), which would teach the model an inconsistent rule.

Award full marks for: a realistic source of labels, who does it, an effort estimate, and one quality risk.

### 3.3 Label noise and bias (5 marks)

**agent_assigned_category (D3):**
- Agents may pick the first plausible category to move quickly, or may be inconsistent with each other on borderline tickets (a damaged item that needs a refund could be "refund" or "product defect").
- Category definitions may have changed over three years, so old tickets carry outdated labels.
- Effect: the model learns the agents' inconsistencies and reproduces them; its measured accuracy is capped by the agreement rate between agents.

**star_rating (D9):**
- Reviewers use the scale differently; some give 3 stars for "fine", others for "disappointing".
- Ratings may reflect delivery experience rather than the product, so the text and the label disagree.
- Extreme ratings are over-represented (people review when very happy or very angry), so the "neutral" class is small and the model will be poor at it.
- Effect: a model trained on these labels inherits the bias; evaluating against the same noisy labels overstates its real quality.

---

## Part 4: Prompt engineering activity (25 marks)

### Example of a strong prompt

```text
ROLE
You are a senior machine learning consultant with experience in retail.

TASK
Analyse the BrightCart Retail case below. Produce:
1. A list of every business problem that is a good candidate for machine learning.
2. For each one, state whether it is supervised or unsupervised learning, the task type
   (classification, regression, clustering, anomaly detection, recommendation,
   dimensionality reduction), and which dataset (D1–D9) it would use.
3. For supervised tasks, name the exact column that would serve as the label.

CONTEXT
<paste the eight interview excerpts>
<paste the D1–D9 data assets table>

CONSTRAINTS
- Output as a single Markdown table with columns: Problem | Department | Supervised/Unsupervised | Task type | Dataset | Label column | One-line rationale.
- Maximum 12 rows.
- Use only the datasets and columns listed. If a label column does not exist in the
  data provided, write "none in data" rather than inventing one.
- Do not estimate financial benefits unless a figure is given in the case.
- After the table, list in 3 bullet points any problems from the case that are NOT
  well suited to ML and why.
```

### What a good LLM response looks like

A capable model will typically produce a table close to the Part 1 and Part 2 model answers. Typical observed behaviours worth discussing in class:

- **Coverage** is usually high (8–9 problems).
- **Classification** is usually correct, with S8 (recommendation) the most variable.
- **Label identification** is usually correct where the column is obvious, but models sometimes invent a column such as "is_duplicate" for D6 or "failure_flag" for D5 if the constraint against invention is missing. This is the point of the grounding criterion.
- **Grounding failures** to watch for: invented ROI percentages, claims that BrightCart "already has a data science team", or references to data (such as competitor prices) not in the case.
- **Format compliance** is usually good when the format is spelled out, and poor when it is vague ("give me a summary").

### Marking the evaluation (Step 3)

Award marks for honesty and evidence, not for the LLM's score. A participant who gives the model 2/5 on grounding and quotes the invented fact earns more than one who gives 5/5 with no evidence.

| Element | Marks |
|---------|-------|
| Prompt contains all four labelled components | 6 |
| Prompt is specific and includes an anti-invention constraint | 4 |
| Exact prompt and complete raw response submitted, with model named | 4 |
| Rubric scored with specific evidence for each criterion | 7 |
| Improvement step: a single clear change, with an honest description of its effect | 4 |

### Common good improvements for Step 4

- Adding one worked example row (few-shot) usually tightens the format and classification.
- Adding "If unsure, say so" reduces invented labels.
- Changing the role to "a sceptical data engineer" often surfaces data-quality concerns (such as the 18-month limit on chargeback_flag).
- Removing the row limit usually increases coverage but adds duplicates.

Participants should notice that a change can make one criterion better and another worse. Reward that observation.

---

## Part 5: Reflection (10 marks)

### 5.1 Which problem first?

There is no single right answer. Strong candidates and their reasoning:

- **Support ticket classification (P3).** Labels already exist in volume, the task is well understood, the benefit is immediate and measurable (agent-minutes saved), and a wrong prediction has low cost because an agent can re-route. **This is the recommended "first" answer.**
- **Demand forecasting (P1).** High value, data is ready, but the model is harder to build well, and a bad forecast has real cost (waste or stock-outs).
- **Fraud detection (P4).** High value, labelled data exists, but only 18 months, the class is heavily imbalanced, and false positives annoy good customers. Higher risk.

Award 4 marks for a justified choice that weighs **data readiness**, **value** and **risk**. Award 2 marks for a choice with only one of those considered.

### 5.2 and 5.3

Award 3 marks each for thoughtful, specific answers. Expected points for 5.3:

- Verify every factual claim against the source material.
- Check whether the model used only the data provided.
- Run the same prompt more than once; LLM output is not deterministic.
- Have a domain expert review the recommendations.
- Remember that fluent, confident text is not evidence of correctness.

---

## Quick marking summary

| Part | Marks | Key discriminators |
|------|-------|--------------------|
| 1 | 20 | Six distinct, correctly justified ML problems; a sensible non-ML concern |
| 2 | 25 | S5 unsupervised; S9 supervised; S8 justified either way; target variables correctly named |
| 3 | 20 | D5 and D6 unlabelled; D3, D4, D7 labelled with correct columns; realistic labelling plan; label-noise discussion |
| 4 | 25 | All four prompt components; raw output submitted; evidence-based rubric; meaningful single-change improvement |
| 5 | 10 | Prioritisation balances readiness, value and risk; critical view of LLM output |

**Typical score distribution:** well-prepared participants land in the 70–85 range. Scores above 90 should show original problem identification and a sharp critique of the LLM's grounding.
