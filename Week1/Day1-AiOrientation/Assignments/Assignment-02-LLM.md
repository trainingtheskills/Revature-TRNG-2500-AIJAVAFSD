# Assignment 02: Large Language Models (LLMs)

**Format:** Hands-on, prompt-based
**Suggested time:** 4–5 hours
**Prerequisite:** Access to at least **two** different LLMs. Suitable free or trial options include Claude (claude.ai), ChatGPT (chatgpt.com), Gemini (gemini.google.com), Microsoft Copilot, and an open-weight model such as Llama or Mistral through a free playground (for example Hugging Face, Groq, or a local Ollama install). Any two will do.
**Submission:** One Markdown or Word document. **Every prompt you ran and every raw, unedited model response must be included**, either inline or in an appendix. Screenshots are acceptable in addition to text, not instead of it.

---

## Learning objectives

By the end of this assignment you should be able to:

1. Match common business scenarios to the LLM capability that solves them.
2. Describe the main families of language models (GPT, BERT, Claude, Llama and others) and explain when each is appropriate.
3. Build a prompt from four components: **role, task, context, constraints**, and show how each one changes the output.
4. Run the same business prompt on two or more models and compare the results objectively.
5. Evaluate an LLM response for **accuracy, relevance and hallucination** using a scoring rubric.

---

## Background scenario: Meridian Mutual Insurance

Meridian Mutual is a regional insurer offering home, motor and small-business policies. It has 1,200 staff, a contact centre of 180 agents, and a claims department that handles about 7,000 new claims a month. The Chief Operating Officer has asked an innovation team to find out where LLMs could help, and to produce evidence rather than opinions.

Five departments have each put forward a scenario.

| ID | Department | Scenario |
|----|------------|----------|
| B1 | Contact centre | Agents answer the same policy questions all day ("Is accidental damage covered on the standard home policy?"). Meridian wants a draft-answer assistant that reads the relevant policy wording and proposes a reply the agent can edit. |
| B2 | Claims | Each claim arrives with a free-text description from the customer, sometimes several paragraphs. Claims handlers want a two-line summary, the claim type, and a list of missing information to request from the customer. |
| B3 | Legal & Compliance | The team reviews supplier contracts. They want to paste a contract clause and get a plain-English explanation plus a flag if the clause contains an unlimited liability, auto-renewal or exclusivity term. |
| B4 | Marketing | Writing product descriptions and email campaigns for three audiences (young renters, families, small-business owners) takes weeks. They want first drafts that match Meridian's tone: "clear, warm, no jargon". |
| B5 | IT | Developers maintain a 15-year-old claims system. They want help explaining legacy code, writing unit tests and converting stored procedures to documented Python functions. |

Reference material you will use in Part 3 is in **Appendix A** (a policy wording extract) and **Appendix B** (a sample claim description).

---

## Part 1: LLM applications in business scenarios (15 marks)

For each scenario B1–B5:

1. Name the primary LLM capability being used. Choose from: **question answering over documents (retrieval-augmented), summarisation, information extraction, classification, text generation, code generation / explanation, translation, conversational agent**. A scenario may use more than one.
2. State the **main business risk** if the LLM makes a mistake in that scenario, and rate it Low / Medium / High.
3. Suggest **one safeguard** (human review, retrieval from approved documents, output validation, restricted scope, and so on) that would reduce that risk.

Then answer: which **one** of the five scenarios would you pilot first, and why? Limit: 150 words.

---

## Part 2: Exploring the model landscape (15 marks)

Research and complete the following table. Use official documentation or reputable sources, and cite the source for each row. Keep each cell short.

| Model family | Developer | Architecture type (encoder-only, decoder-only, encoder-decoder) | Open-weight or proprietary? | Typical strengths | Best-fit Meridian scenario(s) | Source |
|--------------|-----------|--------------------------------------------------------|----------------------------|-------------------|-------------------------------|--------|
| GPT (GPT-4 family and later) | | | | | | |
| BERT (and variants such as RoBERTa, DistilBERT) | | | | | | |
| Claude | | | | | | |
| Llama | | | | | | |
| Gemini | | | | | | |
| Mistral / Mixtral | | | | | | |
| T5 / FLAN-T5 | | | | | | |

Then answer the following in 2–4 sentences each:

1. Why is BERT generally **not** used to generate the marketing copy in B4, even though it is a well-known language model?
2. Meridian's Legal team says contract text must never leave company infrastructure. Which models in the table could still be used, and what would the trade-off be?
3. What is the difference between a model's **context window** and its **training data cutoff**, and why does each matter for scenario B1?

---

## Part 3: Prompt engineering exercises (30 marks)

You will work on scenario **B2 (claims summary)** using the sample claim in Appendix B. Use **one** model throughout Part 3 and name it.

### Exercise 3.1: The naive prompt

Run this exact prompt and record the response:

```text
Summarise this claim.

<paste Appendix B>
```

Write two sentences on what is missing or unhelpful about the output for a claims handler.

### Exercise 3.2: Add a role

Add a **role** line at the top (for example, "You are an experienced motor claims handler at a UK insurer") and keep everything else the same. Run it. Note what changed.

### Exercise 3.3: Add a task specification

Keep the role. Replace "Summarise this claim" with a precise **task**: a two-line summary, the claim type (choose from: motor accident, motor theft, home contents, home buildings, business interruption, liability), and a bulleted list of information that is missing and should be requested from the customer. Run it. Note what changed.

### Exercise 3.4: Add context

Keep the role and task. Add **context** that the model did not have: for example, that Meridian requires a police reference number for all theft claims, that photographs are required for damage over £500, and that the customer's policy excess is £250. Run it. Note what changed, especially in the "missing information" list.

### Exercise 3.5: Add constraints

Keep everything. Add **constraints**: maximum 120 words, output as JSON with keys `summary`, `claim_type`, `missing_information`, and an instruction to use only facts stated in the claim and to write `"not stated"` rather than guessing. Run it. Note what changed.

### Exercise 3.6: Reflection

In a table, list the five versions of the prompt and, for each, one concrete thing that improved and one thing (if any) that got worse. Then answer: which single component (role, task, context or constraints) made the biggest difference for this scenario, and why do you think that is?

**Marking:** each of 3.1–3.5 is worth 5 marks (prompt + raw response + observation); 3.6 is worth 5 marks.

---

## Part 4: Comparing LLM responses to the same business problem (20 marks)

Take your **final prompt from Exercise 3.5** and run it, unchanged, on a **second, different model** (ideally from a different developer, for example Claude and GPT, or Gemini and Llama).

Then run the **same final prompt a second time** on your original model, to see whether its output changes between runs.

Record all three outputs. Complete this comparison table:

| Dimension | Model A, run 1 | Model A, run 2 | Model B |
|-----------|----------------|----------------|---------|
| Followed JSON format exactly? | | | |
| Stayed within 120 words? | | | |
| Claim type chosen | | | |
| Number of missing-information items | | | |
| Any facts not in the claim? (list them) | | | |
| Used "not stated" where appropriate? | | | |
| Tone appropriate for internal use? | | | |

Answer in no more than 200 words:

1. Which model's response would you hand to a claims handler, and why?
2. How different were Model A's two runs? What does this tell you about using LLM output in a production process?
3. Did either model interpret an ambiguous part of the claim differently? Which interpretation was more defensible?

---

## Part 5: Evaluating accuracy, relevance and hallucination (20 marks)

### Exercise 5.1: Hallucination probe

Run each of the following prompts on **both** models and record the responses.

**Probe 1 (fictional entity):**
```text
Summarise the key coverage limits of the Meridian Mutual "HomeShield Plus" policy and tell me the year it was launched.
```
There is no such product. Note whether each model invents coverage limits or a launch year, asks for the document, or says it does not know.

**Probe 2 (grounded question with a trap):**
```text
Using only the policy wording below, answer: Is damage caused by a burst pipe covered, and is there an excess? If the wording does not say, reply "The wording does not say."

<paste Appendix A>
```
Appendix A covers escape of water but does **not** state the excess amount. Note whether each model invents an excess figure.

**Probe 3 (verifiable fact):**
```text
What is the difference between an insurance excess and a premium? Answer in two sentences.
```
Both terms have standard definitions. Check both answers against a reputable source and note any errors.

### Exercise 5.2: Score the responses

Score every response from Probes 1–3 on this rubric. Give evidence for each score.

| Criterion | 1 | 3 | 5 |
|-----------|---|---|---|
| **Accuracy** | Contains clear factual errors | Mostly correct, minor errors | Fully correct and verifiable |
| **Relevance** | Off-topic or ignores the question | Addresses the question with padding | Directly and completely answers the question |
| **Hallucination** | Invents specific facts, figures or sources | Hedges but still speculates | Says it does not know, or uses only given material |

### Exercise 5.3: Short answer (max 250 words)

1. Which probe was most effective at exposing hallucination, and why?
2. Based on your results, write a one-paragraph recommendation to Meridian's COO on when LLM output can be used **without** human review, and when it cannot.

---

## Expected output

- [ ] Part 1: table for B1–B5 with capability, risk rating, safeguard; pilot recommendation.
- [ ] Part 2: completed model landscape table with sources; three short answers.
- [ ] Part 3: five prompts, five raw responses, observations, and the reflection table.
- [ ] Part 4: three raw responses, completed comparison table, three short answers.
- [ ] Part 5: six probe responses (three probes × two models), scored rubric with evidence, short answers.

## Evaluation criteria

| Part | Marks | Assessed on |
|------|-------|-------------|
| 1 | 15 | Correct capability mapping; realistic risk assessment; practical safeguards; justified pilot choice |
| 2 | 15 | Factual accuracy with sources; correct architecture types; clear reasoning on BERT, on-premise deployment, and context window vs cutoff |
| 3 | 30 | All five iterations run and documented; observations are specific and tied to the change made; reflection identifies cause and effect |
| 4 | 20 | Comparison is objective and evidence-based; recognises run-to-run variability; defensible recommendation |
| 5 | 20 | Probes run on both models; rubric scored honestly with evidence; recommendation is proportionate to the evidence |
| **Total** | **100** | |

**Pass mark:** 60. Submissions missing raw model outputs for any part will be capped at 70. Fabricated model outputs are academic misconduct.

---

## Appendix A: Policy wording extract (for Parts 3 and 5)

> **Meridian Mutual Standard Home Policy – Section 2: Buildings**
>
> **2.4 Escape of water.** We will pay for loss or damage to the buildings caused by water escaping from any fixed domestic water or heating installation, washing machine, dishwasher, refrigerator or freezer. We will not pay for: (a) damage caused by subsidence, heave or landslip resulting from escape of water; (b) the cost of repairing the installation from which the water escaped; (c) loss or damage occurring while the home is unoccupied for more than 60 consecutive days.
>
> **2.5 Accidental damage (optional extension).** Where shown on your schedule, we will pay for accidental damage to the buildings. We will not pay for damage caused by wear and tear, gradual deterioration, or by any process of cleaning, repair or alteration.
>
> **2.9 Excess.** The excess applicable to each claim under this section is shown on your schedule.

## Appendix B: Sample claim description (for Parts 3 and 4)

> Hi, I'm writing about my car. Last Thursday evening I parked on Elm Street outside my friend's house around 7pm, and when I came back about 10:30 it wasn't there. I thought maybe it had been towed but the council said no. I've looked around the area. It's a 2019 blue Ford Focus. There were a few things in it, my laptop bag was in the boot and I think my sunglasses. I haven't been able to find the spare key either, I think it might have been in the glovebox, not sure. I did report it the next morning. I need a car for work so I'd like to know about a hire car. My policy number is MM-4471902. Thanks, Priya.
