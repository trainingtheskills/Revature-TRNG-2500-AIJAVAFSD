# AI Orientation: Popular Interview Questions with Answers

## 1. AI Introduction

**Q1. What is Artificial Intelligence?**
AI is the field of building systems that perform tasks normally needing human intelligence, such as reasoning, learning, perception, language understanding and decision-making. Examples include recommendation engines, chatbots and self-driving systems.

**Q2. What is the difference between AI, ML and Deep Learning?**
- **AI** is the broadest term: any technique that makes machines act intelligently, including rule-based systems.
- **ML** is a subset of AI in which systems learn patterns from data instead of being explicitly programmed.
- **Deep Learning** is a subset of ML that uses multi-layer neural networks. It works well on images, audio and text.
- **Generative AI** is a subset of deep learning that creates new content, such as text, images and code.

**Q3. What is the difference between Narrow AI, General AI and Super AI?**
- **Narrow AI (ANI):** does one task well, like spam filtering or ChatGPT. Everything that exists today is narrow AI.
- **AGI:** human-level ability across any task. It is theoretical.
- **ASI:** surpasses human intelligence. It is hypothetical.

**Q4. Is AI the same as automation?**
No. Automation follows fixed rules ("if X then Y"). AI handles ambiguity and adapts from data. An automated script always behaves the same; an AI model's output depends on what it learned.

---

## 2. ML Introduction

**Q5. What is Machine Learning?**
Tom Mitchell's definition: a program learns from experience *E* with respect to task *T* and performance measure *P* if its performance on *T*, measured by *P*, improves with *E*. In practice, you give it data and it finds the patterns.

**Q6. Explain the typical ML workflow.**
1. Define the problem and success metric
2. Collect data
3. Clean and preprocess it (missing values, encoding, scaling)
4. Split into train, validation and test sets
5. Select and train a model
6. Evaluate it (accuracy, precision, recall, F1, RMSE)
7. Tune hyperparameters
8. Deploy
9. Monitor for data drift and retrain

**Q7. What is overfitting and underfitting? How do you fix them?**
- **Overfitting:** the model memorizes the training data and performs poorly on new data (low training error, high test error).
  - Fixes: more data, regularization (L1/L2), dropout, early stopping, a simpler model, cross-validation.
- **Underfitting:** the model is too simple to capture the pattern (high error on both sets).
  - Fixes: a more complex model, better features, longer training.

**Q8. What is the bias–variance tradeoff?**
- **Bias** is error from overly simple assumptions (underfitting).
- **Variance** is error from sensitivity to the training data (overfitting).
- Reducing one usually raises the other. The goal is the sweet spot with the lowest total error.

---

## 3. Supervised vs. Unsupervised Learning

**Q9. What is the difference between supervised and unsupervised learning?**

| | Supervised | Unsupervised |
|---|---|---|
| Data | Labeled (input + correct output) | Unlabeled |
| Goal | Predict a known target | Discover hidden structure |
| Tasks | Classification, regression | Clustering, dimensionality reduction, anomaly detection |
| Examples | Spam detection, house price prediction | Customer segmentation, topic discovery |
| Algorithms | Linear/logistic regression, decision trees, SVM, random forest | K-Means, hierarchical clustering, PCA, DBSCAN |
| Evaluation | Straightforward (compare with labels) | Harder (no ground truth) |

**Q10. Classification vs. regression?**
Classification predicts a **category** (spam / not spam). Regression predicts a **continuous number** (price, temperature).

**Q11. Give a real example where you'd use each.**
- Supervised: predicting loan default from historical labeled loans.
- Unsupervised: grouping customers by purchase behavior when you don't know the groups in advance.

---

## 4. LLMs (GPT, BERT, Claude, Llama, Copilot, Codeium)

**Q12. What is an LLM?**
A Large Language Model is a neural network, almost always a Transformer, trained on massive text corpora to predict the next token. At scale this produces abilities like summarizing, translating, reasoning and coding.

**Q13. Explain the Transformer architecture and self-attention.**
Transformers (from "Attention Is All You Need", 2017) process all tokens in parallel instead of one at a time as RNNs do. **Self-attention** lets every token weigh how relevant every other token is, using Query, Key and Value vectors. This captures long-range context, and parallelism makes it practical to train at huge scale. Positional encodings supply word order.

**Q14. GPT vs. BERT. What's the difference?**

| | GPT | BERT |
|---|---|---|
| Architecture | Decoder-only | Encoder-only |
| Direction | Left-to-right (autoregressive) | Bidirectional |
| Pre-training | Predict the next token | Masked language modeling plus next-sentence prediction |
| Best at | Text **generation**, chat | **Understanding**: classification, NER, search, embeddings |

**Q15. Name popular LLMs and tools.**
- **GPT** (OpenAI), **Claude** (Anthropic) and **Gemini** (Google) are proprietary, API-based models.
- **Llama** (Meta) and **Mistral** are open-weight models you can self-host.
- **GitHub Copilot** and **Codeium** are AI coding assistants built on LLMs. They provide autocomplete, chat and code explanation inside the IDE.

**Q16. Open-source (open-weight) vs. proprietary LLMs?**
- **Open-weight (Llama):** full control, data stays in-house, can be fine-tuned, no per-token fees, but you own the infrastructure and operations.
- **Proprietary (GPT, Claude):** top-tier quality, no infrastructure to manage, but you pay per token and send data to a vendor, and you have less control.

**Q17. How is an LLM trained?**
1. **Pre-training:** self-supervised next-token prediction on huge text datasets.
2. **Supervised fine-tuning (SFT):** train on curated instruction and response pairs.
3. **Alignment (RLHF or similar):** use human preference feedback to make outputs helpful and safe.

**Q18. What are hallucinations and how do you reduce them?**
A hallucination is a fluent, confident answer that is factually wrong. The model predicts plausible text, not verified truth.
Mitigations:
- **RAG** (ground answers in retrieved documents)
- Lower temperature
- Ask for citations and verify them
- Tell the model to say "I don't know"
- Add human review for critical output

**Q19. What is a context window?**
The maximum number of tokens (input plus output) the model can consider in a single request. Content beyond it is ignored or must be truncated or summarized.

**Q20. What are temperature and top-p?**
They control randomness when sampling the next token. A low temperature (0–0.3) is more deterministic, which suits extraction and code. A high temperature (0.7–1.0) is more creative, which suits brainstorming. Top-p limits sampling to the smallest set of tokens whose cumulative probability is at least p.

---

## 5. Use Cases for LLMs

**Q21. What are the common enterprise use cases?**
- **Code:** generation, review, debugging, test writing, documentation (Copilot, Codeium)
- **Customer support:** chatbots and agent-assist
- **Content:** drafting, summarizing, translation, rewriting
- **Knowledge search:** Q&A over internal documents (RAG)
- **Data tasks:** information extraction, classification, sentiment analysis, SQL generation
- **Agents:** multi-step workflows that call tools and APIs

**Q22. What is RAG and why is it used?**
Retrieval-Augmented Generation:
1. Split documents into chunks and embed them into vectors.
2. Store them in a vector database.
3. At query time, retrieve the most similar chunks.
4. Put them in the prompt so the LLM answers from that context.

It gives access to private or up-to-date data, reduces hallucinations, and is cheaper and faster to update than fine-tuning.

**Q23. RAG vs. fine-tuning: when do you use which?**
- **RAG:** when knowledge changes often, you need citations, or the data is large or private.
- **Fine-tuning:** when you need a specific style, format or behavior, or domain-specific skill, rather than new facts.
- Often the best systems combine both.

**Q24. What are embeddings?**
Numeric vectors that represent text so that semantically similar text sits close together. They power semantic search, clustering, recommendations and RAG.

**Q25. When would you *not* use an LLM?**
- Deterministic tasks where rules or code are enough (tax calculation, simple validation)
- Tasks requiring guaranteed 100% accuracy
- Strict low-latency or very-low-cost, high-volume jobs where a small classical ML model works
- Highly sensitive data, if no compliant deployment option exists

---

## 6. LLM Best Practices

**Q26. What makes a good prompt?**
Be clear and specific, and give:
1. **Role/context** ("You are a senior Java reviewer")
2. **Task**
3. **Constraints and format** ("Return JSON with keys…")
4. **Examples** (few-shot)
5. **Input data**, clearly delimited

**Q27. How do you evaluate LLM output quality?**
- Build a test set of representative inputs with expected outputs
- Automated metrics where possible (exact match, BLEU/ROUGE, schema validity)
- LLM-as-judge for subjective quality, spot-checked by humans
- Track regressions whenever you change the prompt or model

**Q28. How do you secure an LLM application?**
- **Prompt injection:** treat all external content (web pages, emails, documents) as untrusted data, not instructions.
- Never put secrets in prompts.
- Apply least privilege to tools and agents, and require human approval for destructive actions.
- Redact PII before sending it to external APIs.
- Validate and sanitize outputs before executing them (SQL, shell, HTML).

**Q29. What are ethical concerns with LLMs?**
Bias, privacy and data leakage, copyright, misinformation, over-reliance, and transparency. Mitigate with human oversight, bias testing, clear disclosure of AI use and data-governance policies.

**Q30. Best practices for using AI coding assistants?**
Review every suggestion, since generated code can contain bugs and vulnerabilities. Write tests, don't paste proprietary code into unapproved tools, give the assistant enough context (files, constraints), and use it to accelerate work, not to replace understanding.

---

## 7. Cost and Token Considerations

**Q31. What is a token?**
The unit of text an LLM processes. It's a word fragment, roughly **4 characters or about ¾ of an English word**, so 100 tokens is about 75 words. Code and non-English text usually use more tokens per word.

**Q32. How is LLM pricing calculated?**
Per token, usually priced per million tokens, with **input and output tokens priced separately**. Output tokens typically cost several times more than input tokens.

`Cost = (input_tokens × input_price) + (output_tokens × output_price)`

**Q33. Worked example: estimate monthly cost.**
Say a chatbot handles 10,000 requests a day with 1,000 input and 300 output tokens each, at $3 per 1M input and $15 per 1M output.
- Input: 10,000 × 1,000 = 10M tokens/day → **$30/day**
- Output: 10,000 × 300 = 3M tokens/day → **$45/day**
- **Total: $75/day, about $2,250/month**

(Prices are illustrative. Always check current vendor pricing.)

**Q34. How do you reduce LLM costs?**
- **Pick the right-sized model.** Use a small, cheap model for easy tasks and a large one only for hard ones (model routing).
- **Shorten prompts.** Remove redundant instructions and trim retrieved context.
- **Cap output** with `max_tokens` and ask for concise formats.
- **Prompt caching.** Reuse the static prefix (system prompt, documents) at a discounted rate.
- **Response caching** for repeated or identical queries.
- **Batch APIs** for non-urgent work, usually at a discount.
- **RAG with tight top-k** instead of stuffing whole documents in.
- **Summarize conversation history** instead of resending it all.
- **Set usage monitoring, budgets and alerts.**

**Q35. Why does a long conversation get more expensive over time?**
Chat APIs are stateless, so the full history is resent as input on every turn. Cost per turn grows with conversation length. The fix is to summarize or truncate older turns.

**Q36. What are the trade-offs between model size, cost, latency and quality?**
Larger models give better reasoning and quality but cost more and respond more slowly. Smaller models are faster and cheaper but weaker on complex tasks. Choose the **smallest model that meets your quality bar**, and validate that with your own evaluation set.

---
