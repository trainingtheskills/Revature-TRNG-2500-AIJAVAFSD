# Assignment 01: AI Case Study – Supervised & Unsupervised Learning

**Format:** Practical, scenario-based
**Suggested time:** 3–4 hours
**Submission:** One Markdown or Word document containing your answers to all five parts, plus the prompt(s) you wrote and the raw LLM output you obtained in Part 4.

---

## Learning objectives

By the end of this assignment you should be able to:

1. Read a real-world business situation and pick out the problems that AI/ML can realistically solve.
2. Decide whether a given problem is a **supervised** or **unsupervised** learning task, and explain why.
3. Tell the difference between **labelled** and **unlabelled** datasets, and identify what the label is.
4. Write a structured prompt that asks a Large Language Model (LLM) to analyze a business case, then critically evaluate its answer.

---

## The case study: BrightCart Retail

BrightCart Retail is a mid-sized omnichannel retailer. It operates 140 physical stores across four regions, an e-commerce website, and a mobile app. It sells groceries, household goods, electronics and apparel. BrightCart has about 2.8 million registered loyalty members and processes roughly 450,000 transactions per day across all channels.

The leadership team has asked the newly formed Data & AI group to identify where AI and machine learning could deliver value in the next 12 months. During discovery interviews, the group captured the following concerns from department heads.

### Operations (Head of Supply Chain)

> "We either run out of popular items on weekends or we over-order perishables that end up in the bin. Our buyers use last year's numbers and gut feel. We have five years of daily sales per store per product, weather, local events and promotion calendars sitting in a warehouse nobody looks at."

### Marketing (VP of Marketing)

> "We send the same promotional email to all 2.8 million members. Open rates are falling. I'd love to group our customers into meaningful segments, but nobody has told us what the segments should be. We don't have a 'segment' column anywhere."

### Customer Service (Director of Customer Experience)

> "We receive around 9,000 support tickets a week through email, chat and the app. Agents spend the first two minutes of every ticket just working out whether it's about a delivery, a refund, a product defect, or an account problem, and then routing it. We've got three years of tickets, and every closed ticket already has the category the agent picked."

### Finance (Risk & Fraud Manager)

> "Online payment fraud cost us about 1.2% of e-commerce revenue last year. Our rules engine flags anything over a certain amount or from a new device, which annoys genuine customers and still misses the clever cases. We have the transaction history and, for the last 18 months, a chargeback flag telling us which transactions turned out to be fraudulent."

### Store Operations (Regional Manager)

> "Some of our stores have strange patterns, like a sudden spike in returns of a specific product or sensor readings from refrigeration units that drift before they fail. We don't know what 'normal' looks like, so we can't spot 'abnormal' until it's too late."

### Merchandising (Category Manager)

> "Our product catalogue has 60,000 SKUs, and the descriptions and attributes were entered by different suppliers over the years. Many products are near-duplicates with slightly different names. We want to find groups of similar products, but we've never tagged which ones belong together."

### Human Resources (HR Business Partner)

> "Store staff turnover is 38% a year. Exit interviews tell us why people left, after the fact. We have HR records for everyone who joined in the last six years, including whether they are still with us, and we'd like to know who is likely to leave in the next six months so managers can intervene."

### Website (Head of Digital)

> "Our 'you may also like' section shows the same bestsellers to everyone. We log every click, search, add-to-cart and purchase, but we don't do anything with it. Also, we'd like to automatically read the thousands of free-text product reviews customers leave and know whether they are positive or negative. Right now, a team of interns reads a sample each month."

### Available data assets

| # | Dataset | Description | Columns of note |
|---|---------|-------------|-----------------|
| D1 | Daily sales history | 5 years, per store, per SKU | date, store_id, sku, units_sold, price, promo_flag, weather, local_event |
| D2 | Loyalty member profiles | 2.8M members | member_id, age_band, region, join_date, total_spend_12m, visit_frequency, categories_purchased, channel_preference |
| D3 | Support tickets | 3 years, ~1.4M tickets | ticket_id, channel, free_text_message, agent_assigned_category, resolution_time |
| D4 | E-commerce transactions | 18 months | txn_id, member_id, amount, device_id, ip_country, time_of_day, items, chargeback_flag (yes/no) |
| D5 | Refrigeration sensor logs | 2 years, 140 stores | timestamp, unit_id, temperature, compressor_cycles, power_draw |
| D6 | Product catalogue | 60,000 SKUs | sku, supplier_name, product_title, free_text_description, attributes_json |
| D7 | HR records | 6 years | employee_id, role, store_id, hire_date, pay_band, shift_pattern, absences, performance_rating, left_company (yes/no), exit_date |
| D8 | Clickstream logs | 2 years | session_id, member_id, page_viewed, search_term, add_to_cart, purchase_flag |
| D9 | Product reviews | 2 years, ~900,000 reviews | review_id, sku, free_text_review, star_rating (1–5) |

---

## Part 1: Identify business problems suitable for AI/ML (20 marks)

Read the interview notes carefully.

1. List **at least six** distinct business problems from the interviews that are good candidates for an AI/ML solution. For each one, write:
   - A one-sentence problem statement in your own words.
   - The business outcome if it were solved (for example, "fewer stock-outs", "lower fraud losses").
   - Why ML is a better fit than a fixed set of hand-written rules.
2. Identify **at least one** concern from the interviews that is **not** really an ML problem, or that could be solved with simple analytics, reporting or process change. Explain your reasoning.

> **Hint:** A good test is to ask, "Is there a pattern in historical data that is too complex, too large or too changeable for a human to write down as rules?"

---

## Part 2: Classify scenarios as supervised or unsupervised learning (25 marks)

For each scenario below, state whether it is best framed as **supervised** or **unsupervised** learning. Then give:

- The type of task (for example: classification, regression, clustering, anomaly detection, dimensionality reduction, association/recommendation).
- A one-line justification.
- If supervised, name the **target variable** the model would predict.

| # | Scenario |
|---|----------|
| S1 | Predict how many units of each SKU each store will sell next week. |
| S2 | Group loyalty members into segments for targeted marketing when no segment definitions exist. |
| S3 | Automatically assign an incoming support ticket to one of the categories "delivery", "refund", "product defect", "account". |
| S4 | Flag an online transaction as likely fraudulent at checkout. |
| S5 | Detect unusual refrigeration sensor patterns that may indicate an impending failure, with no history of labelled failures. |
| S6 | Find clusters of near-duplicate products in the catalogue. |
| S7 | Predict whether a store employee will leave in the next six months. |
| S8 | Recommend products on the website based on items that customers frequently view or buy together. |
| S9 | Determine whether a product review is positive, neutral or negative. |
| S10 | Reduce the 40 attribute columns in the loyalty profile to a handful of underlying factors for visualisation. |

Present your answer as a table with columns: **Scenario | Supervised / Unsupervised | Task type | Target variable (if any) | Justification**.

---

## Part 3: Labelled vs. unlabelled datasets (20 marks)

Look at the nine datasets (D1–D9) in the "Available data assets" table.

1. For each dataset, state whether it is **labelled**, **unlabelled**, or **partially labelled / depends on the use case**. Where it is labelled, name the column that acts as the label and the business question that label answers.
2. Choose **one** dataset that you classified as unlabelled. Describe, in 4–6 sentences, how BrightCart could create labels for it if it wanted to use supervised learning. Mention who would do the labelling, roughly how much effort it would take, and one risk of poor-quality labels.
3. The star_rating column in D9 and the agent_assigned_category column in D3 were both created by humans. Explain one way each of these labels could be **noisy or biased**, and how that would affect a model trained on them.

---

## Part 4: Prompt engineering activity (25 marks)

In this part you will ask an LLM (for example Claude, ChatGPT, Gemini, or an open model such as Llama) to analyze the BrightCart case for you, then judge how well it did.

### Step 1: Write a structured prompt

Write a single prompt that includes all four of the following components. Label each component clearly in your submission.

- **Role:** who the model should act as (for example, "a senior machine learning consultant").
- **Task:** exactly what you want it to produce (for example, identify the ML opportunities, classify each as supervised or unsupervised, state the label).
- **Context:** paste the interview notes and the data assets table from this document.
- **Constraints:** output format (a table), length limits, a requirement to say "unknown" if the information is not in the case, and an instruction not to invent data that is not provided.

### Step 2: Run it

Submit the **exact prompt** you used and the **complete, unedited response** from the LLM. State which model you used.

### Step 3: Evaluate the response

Score the LLM's answer on the rubric below (1 = poor, 5 = excellent) and give a one- or two-sentence reason for each score.

| Criterion | What to look for |
|-----------|------------------|
| Coverage | Did it find most of the problems you found in Part 1? |
| Correct classification | Does its supervised/unsupervised labelling agree with yours in Part 2? Where it differs, who is right? |
| Label identification | Did it correctly name the label column where one exists? |
| Grounding | Did it stick to the data described, or did it invent datasets, numbers or capabilities BrightCart does not have? |
| Format compliance | Did it follow your output format and length constraints? |

### Step 4: Improve the prompt

Change **one** thing in your prompt (for example, add a constraint, change the role, or add an example row) and run it again. Describe what changed in the output and whether it improved. Submit the second prompt and response too.

---

## Part 5: Reflection (10 marks)

Answer in no more than 300 words in total:

1. Which problem from the case would you recommend BrightCart tackle **first**, and why? Consider data readiness, business value and risk.
2. What is one thing the LLM did better than you expected, and one thing it did worse?
3. What would you need to check before trusting an LLM's analysis in a real client engagement?

---

## Expected output

Your submission should contain:

- [ ] Part 1: list of six or more ML-suitable problems with outcomes and justification, plus one non-ML concern.
- [ ] Part 2: completed classification table for S1–S10.
- [ ] Part 3: labelled/unlabelled table for D1–D9, a labelling plan for one unlabelled dataset, and the label-quality discussion.
- [ ] Part 4: two prompts, two raw LLM responses, model name, and a scored rubric for the first response.
- [ ] Part 5: reflection answers.

## Evaluation criteria

| Part | Marks | Assessed on |
|------|-------|-------------|
| 1 | 20 | Correct identification of ML-suitable problems; clear business outcomes; sound reasoning about why ML beats rules; correct identification of a non-ML concern |
| 2 | 25 | Correct supervised/unsupervised classification; correct task type; correct target variable; quality of justification |
| 3 | 20 | Correct labelled/unlabelled identification; realistic labelling plan; thoughtful discussion of label noise and bias |
| 4 | 25 | Prompt contains all four components; prompt is clear and specific; evaluation is honest and evidence-based; the improvement step shows understanding of how prompt changes affect output |
| 5 | 10 | Clear reasoning; prioritisation considers data readiness, value and risk; critical view of LLM output |
| **Total** | **100** | |

**Pass mark:** 60. Submissions that do not include the raw LLM output for Part 4 will be capped at 75.
