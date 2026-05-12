````markdown
# Beyond the Answer — Probing Numerical Reasoning in Financial LLMs

## Author
**Aayush Choudhary**  
IIIT Delhi

---

## GitHub Repository

🔗 Repository Link:  
https://github.com/aayushiiitd2025-byte/AAYUSH_LLM

---

# Overview

This project investigates numerical reasoning failures in Financial Large Language Models (LLMs) using the **FinQA** dataset.

Rather than focusing only on final answer accuracy, this project analyzes:

- Retrieval failures
- Program reasoning correctness
- Context sensitivity
- Silent numerical reasoning failures
- Symbolic verification for reliability improvement

---

# Configuration Used

| Component | Details |
|---|---|
| Model | Qwen2.5-0.5B-Instruct |
| Environment | Google Colab (T4 GPU) |
| Dataset | FinQA |
| Evaluation | 100 Test Examples |

---

# Repository Structure

```bash
├── FinQA_Complete_Submission_Aayush.ipynb
├── NUMERICAL_REASONING_IN_FINANCIAL_LLMS_Aayush.pdf
├── AAYUSH_Q_AND_A.pdf
├── README.md
└── assets/
````

---

# Layer 1 — Dataset Understanding

Performed detailed analysis of:

* FinQA symbolic program structure
* `#N` intermediate references
* Evidence source distribution
* Percentage reasoning patterns
* Execution vs Program accuracy

## Key Findings

* Most questions depend heavily on table retrieval.
* Execution accuracy alone is insufficient for financial reliability.
* Program correctness is critical in regulated financial systems.

---

# Layer 2 — Error Taxonomy & Evaluation

Built a reasoning pipeline using **Qwen2.5-0.5B-Instruct**.

## Evaluation Setup

* 100 FinQA test examples
* Few-shot prompting
* Execution accuracy evaluation
* Program accuracy comparison

## Error Categories Analyzed

* Retrieval errors
* Operation/order errors
* Hallucinations
* Parsing failures
* Program mismatch

## Major Findings

* Retrieval errors dominated (~93% of failures)
* Few-shot prompting improved parse consistency
* Execution accuracy and program accuracy frequently diverged

---

# Layer 2B — Context Sensitivity

Compared three context formats:

1. Full Context (Table + Text)
2. Table Only
3. Text Only

## Observation

* Tables are the most critical information source for FinQA reasoning.
* Removing tables significantly impacts numerical retrieval quality.

---

# Layer 3 — Proposed Improvement

Implemented:

* Complexity-based routing
* Symbolic verification layer

## Pipeline

1. Classify question complexity
2. Route questions using different prompting strategies
3. Verify generated reasoning programs symbolically

## Motivation

Financial systems require **reasoning reliability**, not merely plausible numerical outputs.

## Result

Symbolic verification helped detect answer-program inconsistencies at zero additional inference cost.

---

# Key Insight

A financial model can produce:

* a numerically plausible answer,
* with incorrect reasoning,
* without any visible indication of failure.

This creates a serious reliability issue in real-world financial decision-making systems.

The goal of this project is therefore to improve:

* interpretability,
* reasoning reliability,
* verification transparency.

---

# Requirements

Install dependencies:

```bash
pip install transformers accelerate torch pandas matplotlib
```

---

# Running the Notebook

Open:

```bash
FinQA_Complete_Submission_Aayush.ipynb
```

Run all cells sequentially in Google Colab.

## Recommended Hardware

* Google Colab T4 GPU

---

# Files Included

* Complete implementation notebook
* Layer 1 & Layer 2 written answers
* Final presentation slides
* Evaluation and analysis outputs

---

# Future Work

If additional compute resources were available:

* Fine-tune a domain-specific reasoning model
* Add retrieval augmentation
* Improve table structure encoding
* Train a dedicated verifier model

---

# Acknowledgements

## Dataset

FinQA — Numerical Reasoning over Financial Data

## Model

Qwen2.5-0.5B-Instruct

```
```
