# Assignment 02: Large Language Models (LLMs)
##  Solution Guide

>
> LLM outputs vary between models, versions and runs. This guide describes what good answers and good model behaviour look like, and flags the patterns you should expect to see. Mark on the quality of the participant's observation and reasoning, not on whether their model produced the same text as the examples here.

---

## Part 1: LLM applications in business scenarios (15 marks)

### Model answer

| ID | Primary capability | Main risk if wrong | Rating | Safeguard |
|----|--------------------|--------------------|--------|-----------|
| B1 | Question answering over documents (retrieval-augmented generation), conversational agent | Agent tells a customer something is covered when it is not; regulatory and financial exposure | **High** | Retrieve only from approved policy wording; show the source clause alongside the answer; agent must confirm before sending |
| B2 | Summarisation + information extraction + classification | A missed detail delays or wrongly rejects a claim; a hallucinated detail could lead to a wrong payout | **Medium** | Handler reviews the summary next to the original text; extracted fields validated against a fixed list; "not stated" required for unknowns |
| B3 | Information extraction + classification + summarisation (plain-English explanation) | A missed unlimited-liability or auto-renewal clause has legal and financial consequences | **High** | Treat as a first-pass screen only; lawyer reviews every flagged and unflagged clause; log the model's reasoning for audit |
| B4 | Text generation | Off-brand or misleading copy; compliance issues if it over-promises coverage | **Medium** (Low for drafts, High if published unreviewed) | Marketing and compliance sign-off before publication; style guide in the prompt; never let the model state coverage terms |
| B5 | Code generation / explanation | Incorrect test or conversion introduces bugs in a production claims system | **Medium** | Code review; tests run in CI; generated code never deployed without a developer reading it; conversions verified against original outputs on sample data |

### Pilot recommendation

The best-supported answer is **B2 (claims summary)** or **B5 (developer assistance)**:

- B2: high volume (7,000 claims a month), clear measurable benefit (handler time), output is internal, every summary is checked by a human who also has the original text. Low blast radius.
- B5: developers are skilled reviewers of the output, errors are caught by tests and review, and no customer is affected directly.

Accept B1 only if the participant explicitly describes retrieval from approved documents and agent approval before sending. Accept B4 if the participant restricts it to first drafts. B3 is a weak first pilot because the cost of a miss is high and hard to detect.

**Marking:** 2 marks per scenario (capability, risk, safeguard), 5 marks for a justified pilot choice.

---

## Part 2: Exploring the model landscape (15 marks)

### Model answer

Versions change frequently. Accept any current, correctly sourced version information. The essentials that should be correct are below.

| Model family | Developer | Architecture | Open or proprietary | Typical strengths | Best-fit scenarios |
|--------------|-----------|--------------|---------------------|-------------------|--------------------|
| GPT | OpenAI | Decoder-only transformer | Proprietary (API) | General-purpose generation, reasoning, code, broad tooling ecosystem | B1, B2, B4, B5 |
| BERT (RoBERTa, DistilBERT) | Google (BERT, 2018); Meta (RoBERTa); Hugging Face (DistilBERT) | **Encoder-only** transformer | Open-weight | Classification, named-entity recognition, semantic search / embeddings, sentence similarity; small and cheap to run | Classification part of B2; clause-flagging part of B3; retrieval step of B1 |
| Claude | Anthropic | Decoder-only transformer | Proprietary (API, also via AWS Bedrock and Google Cloud Vertex AI) | Long context windows, careful instruction following, document analysis, coding, strong refusal of unsafe requests | B1, B2, B3, B5 |
| Llama | Meta | Decoder-only transformer | Open-weight (licensed, with usage conditions) | Can be self-hosted and fine-tuned; wide range of sizes; strong community tooling | B3 (on-premise), B2, B5 |
| Gemini | Google DeepMind | Decoder-only, natively multimodal | Proprietary (API, also in Google Workspace) | Very long context, multimodal input, Google ecosystem integration | B1, B2, B4 |
| Mistral / Mixtral | Mistral AI | Decoder-only; Mixtral uses mixture-of-experts | Mostly open-weight, some proprietary | Efficient inference, good quality for size, self-hostable, European provider | B3 (on-premise), B2 |
| T5 / FLAN-T5 | Google | **Encoder-decoder** transformer | Open-weight | Text-to-text tasks such as summarisation, translation, classification; small variants run cheaply | B2 summarisation, translation if needed |

**Marking:** 1 mark per row for a substantially correct, sourced entry (7 marks). Deduct 0.5 if architecture is wrong for BERT (encoder-only) or T5 (encoder-decoder), since these are the key conceptual distinctions. 8 marks for the three short answers.

### Short answers

**1. Why not BERT for marketing copy?**
BERT is an encoder-only model. It is trained to produce a rich representation of input text (via masked-token prediction), not to generate text token by token. It is excellent at understanding and classifying text, but it has no decoder and cannot write a paragraph. Generative tasks need a decoder-only (GPT, Claude, Llama) or encoder-decoder (T5) model.

**2. Contract text must not leave company infrastructure.**
Open-weight models such as Llama, Mistral/Mixtral, FLAN-T5, and BERT variants can be downloaded and run on Meridian's own servers or private cloud, so no data leaves. Trade-offs: Meridian must provision and maintain GPU infrastructure, handle updates and security itself, and the largest open models may still lag the best proprietary models on nuanced legal reasoning. A middle option is a proprietary model deployed in a private cloud tenancy (for example Claude on AWS Bedrock within Meridian's own account) with contractual data-handling guarantees, which the participant may or may not count as "company infrastructure"; accept either position if argued.

**3. Context window vs. training cutoff.**
The **context window** is how much text the model can take in at once (prompt plus response), measured in tokens. The **training cutoff** is the date after which the model has seen no data. For B1, the context window matters because the policy wording must fit alongside the question; a long policy may need retrieval of the relevant section rather than the whole document. The training cutoff matters because the model knows nothing about Meridian's specific policies regardless of the date, and may have outdated general knowledge about regulation; this is why the answer must be grounded in retrieved documents rather than the model's memory.

---

## Part 3: Prompt engineering exercises (30 marks)

### Expected progression

The sample claim is deliberately messy: it is a motor theft, the customer did not report it until the next morning, the spare key may have been in the car (an insurer would care about this a great deal), contents (laptop, sunglasses) were in the car, and the customer asks about a hire car. Several facts are missing: exact date, police reference, vehicle registration, the value of contents, whether the car was locked, and what the policy covers for hire cars.

| Exercise | What the model typically produces | What participants should notice |
|----------|-----------------------------------|----------------------------------|
| **3.1 Naive** | A fluent paragraph restating the story: car parked, gone by 10:30, laptop in boot, reported next morning, wants hire car. | Reads well but gives the handler nothing actionable: no claim type, no list of what is missing, often buries the key detail about the spare key, and may be as long as the original. |
| **3.2 + Role** | Tone becomes more professional. Often starts using insurance vocabulary ("insured", "vehicle", "theft claim"). May spontaneously note the spare key issue. | The role changes **voice and emphasis** more than structure. Output is still a prose summary. Some models add unrequested advice. |
| **3.3 + Task** | Produces the three requested parts: two-line summary, "motor theft", and a bulleted missing-information list (date, registration, police reference, contents values, lock status). | The task specification is usually the biggest structural jump. The missing-information list is driven by the model's general knowledge of insurance, which may or may not match Meridian's rules. |
| **3.4 + Context** | The missing-information list now specifically includes the police reference number (because the context said theft claims require it) and photographs if damage is claimed (may be noted as not applicable). May mention the £250 excess in the summary. | Context makes the output **company-specific** rather than generic. A good observation: the model sometimes mentions the excess even though it was not asked to, which is a hint that constraints are needed. |
| **3.5 + Constraints** | Valid JSON, under 120 words, `claim_type: "motor theft"`, `missing_information` as an array, with "not stated" used for registration, exact date, and value of contents. | Output becomes **machine-readable and predictable**. Some models wrap the JSON in Markdown fences or add a sentence before it; that is a format compliance issue worth noting. Word limits may force the model to drop useful items from the list. |

### 3.6 Reflection: expected conclusion

Most participants will conclude that **task** made the biggest difference, because it changed the output from a narrative into the three artefacts the handler needs. A strong answer will argue that **context** made the biggest difference *to usefulness* because it is the only component that injected knowledge the model could not have had (Meridian's rules), while **constraints** made the biggest difference *to reliability* because they made the output parseable and stopped guessing. Accept any of these if well argued. "Role" as the biggest difference is a weak answer for this scenario and should earn fewer marks unless the participant presents clear evidence.

### Marking (30 marks)

- 5 marks per exercise 3.1–3.5: 1 for the correct prompt, 2 for the raw response, 2 for a specific observation that ties the change to the output.
- 5 marks for 3.6: 3 for the table, 2 for a justified choice of most impactful component.
- Deduct if observations are generic ("the output got better") with no specifics.

---

## Part 4: Comparing LLM responses (20 marks)

### What to expect

- **Format compliance.** Most current models produce valid JSON when asked. Common deviations: Markdown code fences around the JSON, a preamble sentence ("Here is the summary:"), or keys in a different order. A strict comparison should count the fences as a format deviation if the constraint said "output as JSON".
- **Claim type.** Almost always "motor theft". If a model chooses "motor accident", that is a clear error.
- **Missing-information count.** Typically 4–7 items. Differences arise from the word limit and from how granular the model is.
- **Invented facts.** Watch for: a specific date (the claim only says "last Thursday"), a registration number, a stated value for the laptop, an assertion that the car was locked or unlocked, or a claim that the police were contacted "the same evening". The claim says the next morning. Any of these is a hallucination.
- **Run-to-run variability.** Two runs of the same prompt on the same model will usually agree on structure and claim type but differ in wording and sometimes in which items make the missing-information list. Participants should observe this and conclude that production use needs either deterministic settings (low temperature), validation of the output schema, or human review, or all three.

### Marking

| Element | Marks |
|---------|-------|
| Three raw outputs submitted, correctly labelled | 4 |
| Comparison table completed with evidence (quotes or specifics) | 8 |
| Q1: defensible choice with reasons | 3 |
| Q2: observes variability and draws a sensible production conclusion | 3 |
| Q3: identifies an ambiguity (spare key, report timing, hire car entitlement) and judges interpretations | 2 |

A participant who states that the two runs were "identical" should be able to show it; byte-identical output is unusual unless the model was run at temperature 0. Do not penalise if the evidence supports it.

---

## Part 5: Evaluating accuracy, relevance and hallucination (20 marks)

### Probe 1: fictional "HomeShield Plus" product

**Desired behaviour:** the model says it has no information about a Meridian Mutual product by that name, notes that Meridian Mutual as described may be fictional or private, and asks for the policy document.

**Hallucination patterns to watch for:**
- Inventing coverage limits ("buildings cover up to £500,000, contents up to £75,000").
- Inventing a launch year.
- Producing a confident, well-structured summary of a product that does not exist.
- A middle case: the model hedges ("I don't have specific details, but a typical policy of this kind might include...") and then lists plausible generic figures. This still scores low on hallucination (around 2–3) because a reader could take the figures as fact.

Most current frontier models from major providers will decline or ask for the document. Smaller or older open models are more likely to invent. This difference is a useful class discussion point.

### Probe 2: burst pipe and excess from Appendix A

**Correct answer:**
- Damage from a burst pipe is covered under clause 2.4 (escape of water from a fixed domestic water or heating installation), subject to the three exclusions.
- The excess: **"The wording does not say."** Clause 2.9 says the excess is shown on the schedule, which is not provided.

**Hallucination patterns:**
- Stating a specific excess (for example "£250" or "£100"). Some models will reuse the £250 figure if the participant ran Part 3 in the same conversation; this is a good illustration of context leakage and is worth discussing.
- Saying "there is no excess". That is wrong; the wording says there is one but does not state the amount.
- Ignoring the instruction to reply "The wording does not say."

A strong participant answer distinguishes "covered, with exclusions" from "covered" and notes the unoccupied-60-days exclusion.

### Probe 3: excess vs. premium

**Correct answer:** A premium is the amount the policyholder pays the insurer, usually monthly or annually, for the cover. An excess is the fixed amount the policyholder pays towards each claim before the insurer pays the rest.

Almost every model gets this right. Minor errors to watch for: describing the excess as a percentage only, or confusing "excess" with "deductible" terminology without noting that they are equivalent terms in different markets (which is acceptable if explained). This probe mainly serves as a control: it shows the rubric should give high scores when they are deserved.

### 5.2 Marking the rubric (10 marks)

Award marks for **evidence-based scoring**. A participant who writes "Accuracy 5/5" with no justification earns less than one who writes "Accuracy 2/5: the model stated the excess was £100, which appears nowhere in the wording." Expect roughly:

| Probe | Well-behaved model | Poorly-behaved model |
|-------|--------------------|----------------------|
| 1 | Accuracy n/a or 5 (correctly says unknown), Relevance 4–5, Hallucination 5 | Accuracy 1, Relevance 3 (answers the question, wrongly), Hallucination 1 |
| 2 | 5 / 5 / 5 | 2–3 / 4 / 1–2 |
| 3 | 5 / 5 / 5 | 4 / 5 / 5 |

### 5.3 Short answers (6 marks)

**Which probe exposed hallucination best?** Usually Probe 1, because it gives the model nothing to ground on and tests whether it will admit ignorance. Probe 2 is the more realistic business test because it mimics a real document-grounded workflow where the trap is subtle. Accept either with reasoning.

**Recommendation to the COO.** A strong answer resembles:

> LLM output can be used without human review only where the task is low-stakes, the output is checked automatically (for example a JSON schema validation and a fixed list of allowed claim types), and errors are cheap and reversible, such as internal first drafts or developer suggestions that go through code review anyway. Anything that reaches a customer, states what a policy covers, quantifies money, or flags legal risk must be grounded in approved documents and reviewed by a qualified person before use. Our probes showed that models will confidently state figures that do not exist unless explicitly told not to, and that two runs of the same prompt can differ, so any production use must include validation and audit logging.

Award full marks for a recommendation that is **proportionate** to what the participant actually observed. A participant whose models behaved well may reasonably be more permissive; one whose models invented an excess figure should be more cautious. Penalise recommendations that ignore the participant's own evidence.

---

## Quick marking summary

| Part | Marks | Key discriminators |
|------|-------|--------------------|
| 1 | 15 | B1 and B3 rated High risk; safeguards are concrete; pilot choice weighs blast radius |
| 2 | 15 | BERT encoder-only, T5 encoder-decoder; open vs proprietary correct; context window vs cutoff clearly distinguished |
| 3 | 30 | All five iterations with raw output; observations tied to the specific change; reflection reasoned |
| 4 | 20 | Evidence-based comparison; variability noticed; production implications drawn |
| 5 | 20 | Probe 2 excess answered "the wording does not say"; rubric scored with evidence; recommendation matches evidence |

**Common issues across submissions:**

- Paraphrased or "cleaned up" model outputs instead of raw text. Apply the 70-mark cap stated in the assignment.
- Running all of Part 3 and Part 5 in a single chat session, so earlier context (the £250 excess) contaminates Probe 2. This is not a mistake to penalise, but ask the participant whether they noticed, and use it as a teaching point about conversation state.
- Treating a model's confident tone as evidence of accuracy. The rubric is designed to separate the two; reward participants who catch it.
