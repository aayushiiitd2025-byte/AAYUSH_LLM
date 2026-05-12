````markdown
Beyond the Answer: Probing Numerical Reasoning in Financial LLMs

> Investigating why small language models fail on financial reasoning tasks — and how symbolic verification can improve reliability.



Author

Aayush Choudhary 
B.Tech, IIIT Delhi

🔗 GitHub Repository:  
https://github.com/aayushiiitd2025-byte/AAYUSH_LLM

---

Project Overview

Financial question answering is not just about producing the correct number.  
In real-world finance, the reasoning process matters just as much as the final answer.

This project explores how a lightweight LLM (**Qwen2.5-0.5B-Instruct**) performs on **FinQA**, a benchmark built around financial reports, tables, and multi-step numerical reasoning.

Instead of trying to maximize benchmark accuracy, this work focuses on understanding:

- Why the model fails
- Which failure modes are most common
- Whether the model is actually reasoning or simply pattern matching
- How symbolic verification can improve reliability without additional training

The project was completed as part of a research-style assignment focused on financial reasoning reliability in LLMs.

---

Problem Statement

FinQA questions require models to:

1. Retrieve relevant values from financial tables and text
2. Perform multi-step arithmetic reasoning
3. Maintain intermediate computations using symbolic references (`#0`, `#1`, etc.)
4. Produce both:
   - a reasoning program
   - and a final numerical answer

Example:

```text
subtract(153.7, 139.9)
divide(#0, 139.9)
````

Even when the retrieved numbers are correct, applying operations in the wrong order can silently produce financially dangerous answers.

---

Dataset

FinQA

* 8,281 financial QA pairs
* Derived from S&P 500 earnings reports
* Mixed table + textual evidence
* Symbolic executable reasoning programs

The dataset is specifically designed to evaluate:

* numerical reasoning,
* financial understanding,
* and interpretable reasoning chains.

---

Model & Environment

| Component       | Details                  |
| --------------- | ------------------------ |
| Model           | Qwen2.5-0.5B-Instruct    |
| Environment     | Google Colab (T4 GPU)    |
| Evaluation Size | 100 FinQA Test Examples  |
| Framework       | HuggingFace Transformers |

---

Repository Structure

```bash
├── FinQA_Complete_Submission_Aayush.ipynb
├── NUMERICAL_REASONING_IN_FINANCIAL_LLMS_Aayush.pdf
├── AAYUSH_Q_AND_A.pdf
├── README.md
└── assets/
```

---

 Layer 1 — Dataset Analysis

The first part of the project focused on understanding the structure of FinQA before any modelling.

### Areas Explored

* Meaning of symbolic references (`#0`, `#1`)
* Program complexity distribution
* Evidence source distribution
* Percentage reasoning patterns
* Execution Accuracy vs Program Accuracy

### Key Findings

* Most questions depend heavily on table retrieval.
* 1-step and 2-step programs dominate the dataset.
* Tables appear in the majority of questions.
* A model can generate the correct answer while using the wrong reasoning chain.

That final observation is especially important in finance because incorrect reasoning may still produce plausible outputs.

---

# Layer 2 — Error Taxonomy & Evaluation

A lightweight reasoning pipeline was built using Qwen2.5-0.5B-Instruct and evaluated on 100 test examples.

The goal was not only to measure accuracy, but to understand *how* the model fails.

---

## Error Categories

Wrong answers were manually classified into:

* Retrieval Errors
* Operation Errors
* Order Errors
* Hallucinations
* Parsing Failures
* Program Mismatch

---

## Major Observation

The dominant failure mode was **retrieval failure**.

The model often selected incorrect values from the financial context even when the required arithmetic operation was correct.

### Main Insight

> Retrieval, not arithmetic, was the biggest bottleneck for a 0.5B financial reasoning model.

---

# Context Sensitivity Experiment

The same questions were evaluated under three different context settings:

1. Full Context (Table + Text)
2. Table Only
3. Text Only

### Observation

Removing tables hurt performance far more than removing textual context.

This reinforces the idea that:

* table understanding,
* value selection,
* and structured retrieval

are critical for financial QA systems.

---

# Layer 3 — Proposed Improvement

Instead of using larger models or fine-tuning, this project explored a lightweight reasoning improvement strategy:

## Complexity Routing + Symbolic Verification

### Pipeline

1. Classify questions by complexity
2. Route simple and complex questions differently
3. Symbolically verify generated reasoning programs

---

## Why This Matters

Financial models can confidently produce:

* plausible percentages,
* believable growth numbers,
* or realistic returns

while still using incorrect reasoning internally.

That kind of silent failure is dangerous in financial decision-making systems.

Symbolic verification helps detect inconsistencies between:

* the generated reasoning program,
* and the final numerical answer.

Importantly, this was achieved:

* without fine-tuning,
* without additional GPUs,
* and without extra inference calls.

---

# Key Takeaways

### 1. Retrieval is the real bottleneck

Most failures were caused by selecting incorrect numbers from context.

---

### 2. Right answer ≠ Right reasoning

Execution accuracy alone is not sufficient in regulated financial settings.

---

### 3. Tables matter more than text

Structured financial tables contain the majority of critical evidence.

---

### 4. Verification layers are valuable

Even lightweight symbolic checking can improve reliability.

---

# Running the Project

## Install Dependencies

```bash
pip install transformers accelerate torch pandas matplotlib
```

---

## Run Notebook

Open:

```bash
FinQA_Complete_Submission_Aayush.ipynb
```

Run all cells sequentially in Google Colab.

Recommended:

* T4 GPU (Free Colab tier)

---

# Files Included

| File                                               | Description                     |
| -------------------------------------------------- | ------------------------------- |
| `FinQA_Complete_Submission_Aayush.ipynb`           | Complete implementation         |
| `NUMERICAL_REASONING_IN_FINANCIAL_LLMS_Aayush.pdf` | Final presentation              |
| `AAYUSH_Q_AND_A.pdf`                               | Written answers for Layer 1 & 2 |
| `README.md`                                        | Project documentation           |

---

# Future Improvements

With more compute resources, the next steps would include:

* Retrieval augmentation
* Table-aware embeddings
* Verifier-specific fine-tuning
* Better structured prompting
* Program repair mechanisms

---

# Final Reflection

This project reinforced an important idea:

> Financial reasoning systems should not only be evaluated on whether the answer is correct, but also on whether the reasoning process is trustworthy.

Improving reliability, interpretability, and verification may ultimately matter more than improving raw benchmark accuracy.

---

# Acknowledgements

### Dataset

FinQA — Numerical Reasoning over Financial Data

### Model

Qwen2.5-0.5B-Instruct

```
```
