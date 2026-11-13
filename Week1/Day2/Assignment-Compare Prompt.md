# Lab Exercise: Same Task, Nine Prompt Formats

**Based on:** *Types of Prompts: A Practical Guide* (Day 2, LLM Platform)
**Goal:** Take **5 everyday tasks** and write each one in **9 different prompt formats**, so you can compare how the *format alone* changes the AI's output.
**Domains:** HR, Sales, Banking, Healthcare, Everyday Life (no technical background needed)
**Total prompts:** 5 tasks x 9 formats = **45 prompts**
**Duration:** about 3 hours (or 2 sessions of 90 minutes)
**Level:** Beginner

---

## 1. Why This Lab?

In the first lab, each prompt type used a different task. That makes it hard to tell whether the output changed because of the *format* or because of the *task*.

Here, the **task and facts stay the same**. Only the prompt format changes. That lets you isolate what each format really does: adds examples, a viewpoint, steps, reasoning, background, structure, stages or limits.

## 2. Lab Objectives

By the end of this lab you will be able to:

1. Rewrite one task in nine prompt formats without changing the underlying facts.
2. Score and compare outputs on a consistent rubric.
3. Explain *why* a format produced a better or worse result.
4. Choose the best format, or combination, for a given real-world task.

## 3. The Nine Formats

| # | Format | What it adds |
|---|---|---|
| 1 | Zero-shot | Nothing extra; just the task |
| 2 | Few-shot | Examples to copy |
| 3 | Role | A viewpoint or expertise |
| 4 | Instruction | Numbered, explicit steps |
| 5 | Chain-of-thought | Step-by-step reasoning before the answer |
| 6 | Contextual | Situation, audience and goal |
| 7 | Structured output | An exact output shape |
| 8 | Prompt chaining | A sequence of smaller prompts |
| 9 | Constraint / negative | Limits and "do not" rules |

## 4. Lab Rules (the experiment must be fair)

1. **Same facts in every version.** The facts of a task (names, numbers, dates) never change. Only the format does.
2. **Same model and settings** for all 45 prompts.
3. **New chat for every prompt**, so earlier answers don't leak into later ones. The only exception is Format 8 (chaining), where you continue within one chat.
4. **Paste the prompt exactly.** Don't improve it while running.
5. **Run each prompt once.** If time allows, run Task A twice (see Part 7) to measure natural variation.
6. **Save every output** (copy into a document) before scoring.
7. **Use fictional data only.** Healthcare prompts are for general information and clinic administration, not medical advice.

---

## 5. The Five Tasks

Each task lists its **fixed facts** (identical in all nine versions) and then the nine prompts.

---

### Task A: HR. Feedback on Lateness

**Fixed facts:** Jordan works in customer service. Jordan arrived 15 to 30 minutes late six times last month. Jordan is very strong with customers. The goal is to improve punctuality.

**A1. Zero-shot**
`Write feedback for Jordan, a customer service employee who arrived 15 to 30 minutes late six times last month but is very strong with customers. The goal is to improve punctuality.`

**A2. Few-shot**
`Situation: An employee missed three deadlines but produces excellent quality. Feedback: "Your quality is excellent and I value it. Missing three deadlines this month affected the team. Let's agree on realistic dates and check in weekly." Situation: An employee talks over colleagues in meetings but has great ideas. Feedback: "Your ideas are valuable. In meetings, you sometimes speak before others finish. Try noting your point and waiting for a pause so everyone is heard." Situation: Jordan, a customer service employee, arrived 15 to 30 minutes late six times last month but is very strong with customers. The goal is to improve punctuality. Feedback:`

**A3. Role**
`You are an experienced, fair HR manager. Write feedback for Jordan, a customer service employee who arrived 15 to 30 minutes late six times last month but is very strong with customers. The goal is to improve punctuality.`

**A4. Instruction**
`Write feedback for Jordan, a customer service employee. 1) Start with a genuine strength: Jordan is very strong with customers. 2) State the facts: Jordan arrived 15 to 30 minutes late six times last month. 3) Explain the impact on the team. 4) Agree on one improvement action to improve punctuality. 5) Offer support. 6) Keep it under 120 words.`

**A5. Chain-of-thought**
`Jordan is a customer service employee who arrived 15 to 30 minutes late six times last month but is very strong with customers. The goal is to improve punctuality. Think step by step: first identify Jordan's strength, then the key facts about lateness, then the impact on the team, then the most helpful action. Show your reasoning briefly, then write the final feedback.`

**A6. Contextual**
`Situation: Jordan works in customer service and arrived 15 to 30 minutes late six times last month. Jordan is very strong with customers. Audience: Jordan will hear this feedback in a one-to-one meeting with their manager. Goal: improve punctuality while keeping Jordan motivated. Using this background, write what the manager should say.`

**A7. Structured output**
`Write feedback for Jordan, a customer service employee who arrived 15 to 30 minutes late six times last month but is very strong with customers. The goal is to improve punctuality. Use exactly these headings: What is going well, The concern, Agreed action, Support offered. Maximum 120 words.`

**A8. Prompt chaining** *(send as four separate messages in one chat)*
Step 1: `Jordan is a customer service employee who arrived 15 to 30 minutes late six times last month but is very strong with customers. List Jordan's strength and the key facts.`
Step 2: `Now suggest two actions that could improve Jordan's punctuality, and explain the impact lateness has on a customer service team.`
Step 3: `Using the strength, facts and best action above, draft the feedback for Jordan.`
Step 4: `Check the draft for a respectful tone and shorten it to under 120 words.`

**A9. Constraint / negative**
`Write feedback for Jordan, a customer service employee who arrived 15 to 30 minutes late six times last month but is very strong with customers. The goal is to improve punctuality. Do not use accusatory language, do not guess at reasons, and do not mention discipline. Do include one specific improvement action. Maximum 100 words.`

---

### Task B: Sales. Handling a Price Objection

**Fixed facts:** Maria owns a small florist shop. Our online-ordering software costs $1,200 per year. Maria said "the price is too high." Benefits: customers can order 24/7, fewer phone orders, free setup. We offer a 30-day money-back guarantee. The goal is to keep the conversation going and invite Maria to a 15-minute call.

**B1. Zero-shot**
`Write a reply email to Maria, a florist shop owner who said "the price is too high" about our $1,200-a-year online-ordering software. Mention that customers can order 24/7, there are fewer phone orders, setup is free, and there is a 30-day money-back guarantee. Invite her to a 15-minute call to keep the conversation going.`

**B2. Few-shot**
`Situation: A customer says delivery takes too long. Reply: "I understand speed matters. Most orders arrive in 5 days, and express delivery is available for a small extra cost. Would a quick call help us find the right option for you?" Situation: A customer says a gym membership contract is too long. Reply: "That is a fair concern. We offer a 14-day trial so you can try it with no commitment. Can I call you tomorrow to talk it through?" Situation: Maria, a florist shop owner, said "the price is too high" about our $1,200-a-year online-ordering software. Benefits: customers can order 24/7, fewer phone orders, free setup, and a 30-day money-back guarantee. Invite her to a 15-minute call. Reply:`

**B3. Role**
`You are an experienced, friendly sales consultant. Write a reply email to Maria, a florist shop owner who said "the price is too high" about our $1,200-a-year online-ordering software. Mention that customers can order 24/7, there are fewer phone orders, setup is free, and there is a 30-day money-back guarantee. Invite her to a 15-minute call to keep the conversation going.`

**B4. Instruction**
`Write a reply email to Maria. 1) Acknowledge her concern that the $1,200-a-year price is too high. 2) Mention three benefits: customers can order 24/7, fewer phone orders, free setup. 3) Mention the 30-day money-back guarantee. 4) Invite her to a 15-minute call. 5) Keep it under 120 words.`

**B5. Chain-of-thought**
`Maria, a florist shop owner, said "the price is too high" about our $1,200-a-year online-ordering software. Benefits: customers can order 24/7, fewer phone orders, free setup, and a 30-day money-back guarantee. The goal is to invite her to a 15-minute call. Think step by step: what is her real concern, which benefits answer it, and how can the guarantee reduce her risk? Then write the reply email.`

**B6. Contextual**
`Situation: Maria owns a small florist shop. She received a quote of $1,200 per year for our online-ordering software and said "the price is too high." Our software lets customers order 24/7, reduces phone orders and includes free setup, with a 30-day money-back guarantee. Audience: Maria, a busy small-business owner. Goal: keep the conversation going and invite her to a 15-minute call. Using this background, write the reply email.`

**B7. Structured output**
`Write a reply to Maria, a florist shop owner who said "the price is too high" about our $1,200-a-year online-ordering software. Use exactly this structure: Subject line; Greeting; Acknowledgement of her concern (1 sentence); Value points (3 bullets: customers can order 24/7, fewer phone orders, free setup); Risk reducer (30-day money-back guarantee); Next step (invite her to a 15-minute call). Maximum 120 words.`

**B8. Prompt chaining** *(four separate messages in one chat)*
Step 1: `Maria, a florist shop owner, said "the price is too high" about our $1,200-a-year online-ordering software. What might her real concerns be?`
Step 2: `Our software lets customers order 24/7, reduces phone orders, includes free setup and has a 30-day money-back guarantee. Match each benefit to her likely concerns.`
Step 3: `Write a reply email to Maria using those points and inviting her to a 15-minute call.`
Step 4: `Check the email sounds helpful, not pushy, and shorten it to under 120 words.`

**B9. Constraint / negative**
`Write a reply email to Maria, a florist shop owner who said "the price is too high" about our $1,200-a-year online-ordering software. Mention 24/7 ordering, fewer phone orders, free setup and the 30-day money-back guarantee, and invite her to a 15-minute call. Do not offer a discount, do not pressure her, and do not use jargon. Maximum 100 words.`

---

### Task C: Banking. Explaining a Car Loan

**Fixed facts:** Alex is a first-time borrower. The loan is $20,000 at 6% annual interest over 5 years, paid monthly. The goal is to explain the monthly payment and the total interest.

*Facilitator check: the monthly payment is about $386.66, total repaid about $23,199 and total interest about $3,199.*

**C1. Zero-shot**
`Explain to Alex, a first-time borrower, what the monthly payment and total interest would be on a $20,000 car loan at 6% annual interest over 5 years, paid monthly.`

**C2. Few-shot**
`Loan: $10,000 at 5% annual interest for 2 years, paid monthly. Explanation: "Your payment would be about $438.71 a month. Over 2 years you would pay about $529 in interest, so the car would cost about $10,529 in total." Loan: $5,000 at 4% annual interest for 1 year, paid monthly. Explanation: "Your payment would be about $425.75 a month. Over 1 year you would pay about $109 in interest, so you would repay about $5,109 in total." Loan: $20,000 at 6% annual interest for 5 years, paid monthly, for Alex, a first-time borrower. Explanation:`

**C3. Role**
`You are a friendly bank loan officer. Explain to Alex, a first-time borrower, what the monthly payment and total interest would be on a $20,000 car loan at 6% annual interest over 5 years, paid monthly.`

**C4. Instruction**
`Explain a car loan to Alex, a first-time borrower. The loan is $20,000 at 6% annual interest over 5 years, paid monthly. 1) State the monthly payment. 2) State the total interest. 3) State the total repaid. 4) Add one sentence explaining how interest works. 5) Use simple language and keep it under 100 words.`

**C5. Chain-of-thought**
`Alex, a first-time borrower, has a $20,000 car loan at 6% annual interest over 5 years, paid monthly. Work out the monthly payment and total interest step by step: convert the annual rate to a monthly rate, find the number of payments, apply the loan payment formula, then calculate total repaid and total interest. Show each step, then explain the result to Alex in simple words.`

**C6. Contextual**
`Situation: Alex is taking out a first loan, a $20,000 car loan at 6% annual interest over 5 years, with monthly payments. Audience: Alex has never borrowed before and wants to understand the real cost. Goal: explain the monthly payment and the total interest so Alex can decide with confidence. Using this background, write the explanation.`

**C7. Structured output**
`Explain a $20,000 car loan at 6% annual interest over 5 years, paid monthly, to Alex, a first-time borrower. Present it as a table with these rows: Loan amount, Interest rate, Term, Monthly payment, Total repaid, Total interest. Then add a one-sentence plain-language summary.`

**C8. Prompt chaining** *(four separate messages in one chat)*
Step 1: `A $20,000 loan has 6% annual interest and runs 5 years with monthly payments. Convert the annual rate to a monthly rate and find the number of payments.`
Step 2: `Using those values, calculate the monthly payment.`
Step 3: `Now calculate the total repaid and the total interest.`
Step 4: `Explain the results to Alex, a first-time borrower, in simple language under 100 words.`

**C9. Constraint / negative**
`Explain to Alex, a first-time borrower, the monthly payment and total interest on a $20,000 car loan at 6% annual interest over 5 years, paid monthly. Do not use jargon such as "amortization", do not recommend whether Alex should take the loan, and do not give investment advice. Round to the nearest dollar. Maximum 100 words.`

---

### Task D: Healthcare. Appointment Reminder

**Fixed facts:** Mr. Lee has an appointment tomorrow at 10:30am with Dr. Patel at Maple Family Clinic. He should bring his health card and a list of his medications and arrive 10 minutes early. To cancel or reschedule he should call 555-0100.

**D1. Zero-shot**
`Write a reminder message for Mr. Lee about his appointment tomorrow at 10:30am with Dr. Patel at Maple Family Clinic. Ask him to bring his health card and a list of his medications, arrive 10 minutes early, and call 555-0100 to cancel or reschedule.`

**D2. Few-shot**
`Details: Ms. Brown, dental cleaning on Tuesday at 2pm with Dr. Singh, bring insurance card, call 555-0111 to change. Message: "Hi Ms. Brown, a reminder of your dental cleaning on Tuesday at 2pm with Dr. Singh. Please bring your insurance card. Call us at 555-0111 to change it. See you soon!" Details: Mr. Ortiz, eye test on Friday at 9am with Dr. Hall, bring current glasses, call 555-0122 to change. Message: "Hello Mr. Ortiz, your eye test is on Friday at 9am with Dr. Hall. Please bring your current glasses. To change the time, call 555-0122. Thank you!" Details: Mr. Lee, appointment tomorrow at 10:30am with Dr. Patel at Maple Family Clinic, bring health card and a list of medications, arrive 10 minutes early, call 555-0100 to cancel or reschedule. Message:`

**D3. Role**
`You are a warm, professional front-desk coordinator at a family clinic. Write a reminder message for Mr. Lee about his appointment tomorrow at 10:30am with Dr. Patel at Maple Family Clinic. Ask him to bring his health card and a list of his medications, arrive 10 minutes early, and call 555-0100 to cancel or reschedule.`

**D4. Instruction**
`Write an appointment reminder for Mr. Lee. 1) Greet him by name. 2) State the appointment: tomorrow at 10:30am with Dr. Patel at Maple Family Clinic. 3) Ask him to bring his health card and a list of his medications. 4) Ask him to arrive 10 minutes early. 5) Tell him to call 555-0100 to cancel or reschedule. 6) Keep it under 60 words.`

**D5. Chain-of-thought**
`Mr. Lee has an appointment tomorrow at 10:30am with Dr. Patel at Maple Family Clinic. He must bring his health card and a list of his medications, arrive 10 minutes early, and call 555-0100 to cancel or reschedule. Think step by step about what he needs to know first, what he needs to do, and the clearest order to say it in. Then write the reminder message.`

**D6. Contextual**
`Situation: Maple Family Clinic is reminding patients the day before appointments to reduce no-shows. Mr. Lee's appointment is tomorrow at 10:30am with Dr. Patel. He should bring his health card and a list of his medications, arrive 10 minutes early, and call 555-0100 to cancel or reschedule. Audience: Mr. Lee, who prefers short, clear messages. Goal: make sure he knows what to bring and how to change the appointment. Using this background, write the reminder.`

**D7. Structured output**
`Write a reminder for Mr. Lee using exactly this layout. Line 1: Greeting. Line 2: Appointment (date, time, doctor, place). Line 3: Bring (health card, list of medications; arrive 10 minutes early). Line 4: To cancel or reschedule (call 555-0100). Details: tomorrow at 10:30am with Dr. Patel at Maple Family Clinic. Maximum 50 words.`

**D8. Prompt chaining** *(four separate messages in one chat)*
Step 1: `Mr. Lee has an appointment tomorrow at 10:30am with Dr. Patel at Maple Family Clinic. List the key facts a patient needs in a reminder.`
Step 2: `He should bring his health card and a list of his medications, arrive 10 minutes early, and call 555-0100 to cancel or reschedule. Put all facts in the best order.`
Step 3: `Write the reminder message for Mr. Lee.`
Step 4: `Make the message friendlier and shorter, under 60 words.`

**D9. Constraint / negative**
`Write a reminder message for Mr. Lee about his appointment tomorrow at 10:30am with Dr. Patel at Maple Family Clinic. Ask him to bring his health card and a list of his medications, arrive 10 minutes early, and call 555-0100 to cancel or reschedule. Do not include any medical advice or health details, do not use abbreviations, and do keep a friendly tone. Maximum 50 words.`

---

### Task E: Everyday Life. Weekend Trip Plan

**Fixed facts:** Two friends are travelling from Toronto to Montreal by bus. They leave Friday evening and return Sunday night. Each has a $400 budget. They enjoy food and museums.

**E1. Zero-shot**
`Plan a weekend trip from Toronto to Montreal for two friends. They travel by bus, leave Friday evening, return Sunday night, have a $400 budget each, and enjoy food and museums.`

**E2. Few-shot**
`Trip: Vancouver to Seattle for one friend, Saturday and Sunday, loves hiking. Plan: Sat: morning bus to Seattle, hike at Discovery Park, dinner at Pike Place Market. Sun: visit a museum, return by evening bus. Trip: Calgary to Banff for a couple, Saturday and Sunday, loves scenery. Plan: Sat: shuttle to Banff, walk by the Bow River, dinner downtown. Sun: ride the gondola, return by evening shuttle. Trip: Toronto to Montreal for two friends who travel by bus, leave Friday evening, return Sunday night, have $400 each, and enjoy food and museums. Plan:`

**E3. Role**
`You are a travel agent who specialises in budget trips. Plan a weekend trip from Toronto to Montreal for two friends. They travel by bus, leave Friday evening, return Sunday night, have a $400 budget each, and enjoy food and museums.`

**E4. Instruction**
`Plan a weekend trip from Toronto to Montreal for two friends who travel by bus and enjoy food and museums. 1) Plan Friday evening (arrival). 2) Plan Saturday with one museum and one food stop. 3) Plan Sunday before the Sunday-night return. 4) Estimate costs per person for transport, lodging, food and activities. 5) Keep the total within $400 per person.`

**E5. Chain-of-thought**
`Two friends are travelling from Toronto to Montreal by bus, leaving Friday evening and returning Sunday night, with $400 each. They enjoy food and museums. Think step by step: first estimate the fixed costs (bus and lodging), then work out what is left for food and activities, then choose activities that fit. Show your reasoning, then give the final plan.`

**E6. Contextual**
`Situation: Two friends want a weekend away. They will take the bus from Toronto to Montreal, leaving Friday evening and returning Sunday night. Each has a $400 budget. They both enjoy food and museums. Goal: have a memorable, well-paced weekend without overspending. Using this background, plan their trip.`

**E7. Structured output**
`Plan a weekend trip from Toronto to Montreal for two friends who travel by bus (Friday evening to Sunday night, $400 each, they enjoy food and museums). Present it as a table with columns: Day, Time, Activity, Estimated cost per person. End with one line showing the total cost per person.`

**E8. Prompt chaining** *(four separate messages in one chat)*
Step 1: `Two friends are taking a bus from Toronto to Montreal for a weekend, leaving Friday evening and returning Sunday night, with a $400 budget each. Estimate the cost of bus tickets and two nights of budget lodging per person.`
Step 2: `With the remaining budget, suggest food stops and museums that suit friends who enjoy food and museums.`
Step 3: `Build a day-by-day itinerary from Friday evening to Sunday night.`
Step 4: `Check the total cost per person is within $400 and adjust if needed.`

**E9. Constraint / negative**
`Plan a weekend trip from Toronto to Montreal for two friends who travel by bus, leave Friday evening, return Sunday night, have a $400 budget each, and enjoy food and museums. Do not exceed $400 per person, do not suggest car rentals, and do not suggest luxury restaurants. Do include one free activity each day. No more than 3 activities per day. Maximum 250 words.`

---

## 6. Scoring and Recording

### 6.1 Scoring rubric

Score each output from **1 (poor) to 5 (excellent)** on each criterion.

| Criterion | What to check |
|---|---|
| **Relevance** | Does it answer exactly what the task asked? |
| **Accuracy** | Are the facts and numbers correct and unchanged from the task? |
| **Completeness** | Are all the fixed facts included? |
| **Format adherence** | Does it follow the structure, length and rules the prompt set? |
| **Tone and audience fit** | Does it suit the reader (employee, customer, patient, friends)? |
| **Usability** | Could you send or use it as-is with no edits? |

Also record **word count** (objective) and **edits needed** (None / Minor / Major).

### 6.2 Scoring sheet (copy one per task)

**Task: ______**

| Format | Words | Relevance | Accuracy | Completeness | Format adherence | Tone fit | Usability | **Total /30** | Edits needed | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| 1. Zero-shot | | | | | | | | | | |
| 2. Few-shot | | | | | | | | | | |
| 3. Role | | | | | | | | | | |
| 4. Instruction | | | | | | | | | | |
| 5. Chain-of-thought | | | | | | | | | | |
| 6. Contextual | | | | | | | | | | |
| 7. Structured output | | | | | | | | | | |
| 8. Prompt chaining | | | | | | | | | | |
| 9. Constraint / negative | | | | | | | | | | |

### 6.3 Summary matrix (total scores out of 30)

| Format | Task A | Task B | Task C | Task D | Task E | **Average** | **Rank** |
|---|---|---|---|---|---|---|---|
| 1. Zero-shot | | | | | | | |
| 2. Few-shot | | | | | | | |
| 3. Role | | | | | | | |
| 4. Instruction | | | | | | | |
| 5. Chain-of-thought | | | | | | | |
| 6. Contextual | | | | | | | |
| 7. Structured output | | | | | | | |
| 8. Prompt chaining | | | | | | | |
| 9. Constraint / negative | | | | | | | |

---

## 7. Extension Experiment: How Much Does the Output Vary?

Before judging formats, check the natural variation of the model.

1. Run prompts **A1 (zero-shot)** and **A7 (structured)** **three times each** in fresh chats.
2. Compare the three outputs for each prompt: word count, wording, structure.
3. Answer: *Which format gave more consistent outputs? Is the difference between formats bigger than the difference between repeat runs?*

This tells you whether a difference you saw in Section 6 is real or just random variation.

---

## 8. Analysis Questions (answer in your report)

**Compare and contrast**

1. Which format gave the **highest average score**? Which gave the lowest?
2. Which format produced the **longest** outputs? Which the **shortest**? Was longer better?
3. For which task did the formats differ **most**? For which did they differ **least**? Why?
4. Compare **Zero-shot vs. Few-shot**: what did the examples change (tone, length, structure)?
5. Compare **Role vs. Zero-shot**: did the role change the facts, or only the style?
6. Compare **Instruction vs. Structured output**: both give structure. What is the difference in the results?
7. Compare **Chain-of-thought vs. Prompt chaining**: both break the work into steps. Which was easier to check and correct?
8. Compare **Contextual vs. Zero-shot**: did the output become more specific to the situation, or just longer?
9. Which **constraints** in Format 9 held? Which did the model break?

**Judgement**

10. In **Task C (the loan)**, which formats got the numbers right? Did showing the working help or not?
11. In **Task D (the reminder)**, which format would you actually send to a patient, and why?
12. Which format gave the best result for the **least effort** to write?
13. Which two formats would you **combine** for each task to get an even better result? Write the combined prompt for one task and test it.

## 9. Deliverable

A **1-2 page report** with:

1. The completed summary matrix (Section 6.3).
2. A short answer (3-5 sentences) to each analysis question you choose (minimum 8).
3. **Your recommendation:** a table with the task type (for example "customer email", "numerical explanation") and the best format or combination for it.
4. One combined prompt you wrote and tested, with its score.

## 10. Assessment Rubric (25 points)

| Criteria | Points |
|---|---|
| All 45 prompts run with outputs saved | 5 |
| Scoring sheets completed with consistent, justified scores | 5 |
| Summary matrix and ranking completed | 5 |
| Analysis answers explain *why*, not just *what* | 5 |
| Combined prompt tested and compared to the single formats | 5 |

---

## 11. Facilitator Notes

**Typical patterns to expect** (outputs vary, so treat these as hypotheses for learners to confirm or challenge, not guarantees):

| Format | What you will often see |
|---|---|
| Zero-shot | Reasonable but generic; length and structure vary from run to run |
| Few-shot | Copies the example's length, tone and structure closely; may over-copy phrases |
| Role | Changes tone and vocabulary more than the facts; sounds more "professional" |
| Instruction | Covers every numbered point; most reliable for completeness |
| Chain-of-thought | Longer; shows working; most useful on the loan (Task C) and the budget (Task E) |
| Contextual | More tailored to the audience and goal; slightly longer |
| Structured output | Easiest to scan and reuse; strict on layout, sometimes thinner in content |
| Prompt chaining | Highest quality control; many messages, so slower; good for checking numbers |
| Constraint / negative | Tighter and safer; check whether "do not" rules and word limits were really respected |

**Running the session**

- **Answer key for Task C:** about $386.66 per month, about $23,199 total, about $3,199 interest. Use any numerical error as a teaching moment.
- **Check word limits by actually counting.** Models often exceed them.
- **Pair work works well:** one person writes and runs the prompts, the other scores blind (without knowing which format produced which output).
- **Blind scoring (optional):** have a partner remove the format labels from the outputs before scoring, to avoid bias toward fancier prompts.
- **Time-box:** if time is short, assign Tasks A, C and E only (27 prompts) and skip Section 7.
- **Keep data fictional,** and remind learners that healthcare prompts here are administrative, not medical advice.
- **Debrief message:** no single format wins everywhere. The best format depends on what the model is missing, so the best prompts usually combine two or three formats.
