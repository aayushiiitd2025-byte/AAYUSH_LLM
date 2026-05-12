````markdown id="fixedgithubreadme"
# Beyond the Answer: Probing Numerical Reasoning in Financial LLMs

This project explores how small language models perform on financial numerical reasoning tasks using the **FinQA** dataset.

The work focuses not only on answer accuracy, but also on:

- reasoning correctness
- retrieval failures
- context sensitivity
- symbolic verification for improving reliability

The project was implemented using **Qwen2.5-0.5B-Instruct** on **Google Colab (T4 GPU)** and evaluated on 100 FinQA test examples.

---

## Key Findings

- Retrieval errors were the most common failure mode.
- Tables were more important than text for solving FinQA questions.
- Models could produce correct answers using incorrect reasoning.
- Symbolic verification helped detect answer-program inconsistencies.

---

## Proposed Improvement

Implemented:

- Complexity-based routing
- Symbolic verification layer

The goal was to improve reasoning reliability without fine-tuning or larger models.

---

## Repository Structure

```bash
├── FinQA_Complete_Submission_Aayush.ipynb
├── NUMERICAL_REASONING_IN_FINANCIAL_LLMS_Aayush.pdf
├── AAYUSH_Q_AND_A.pdf
└── README.md
````

---

## Setup

Install dependencies:

```bash
pip install transformers accelerate torch pandas matplotlib
```

Run the notebook in Google Colab:

```bash
FinQA_Complete_Submission_Aayush.ipynb
```

---

## GitHub Repository

🔗 [https://github.com/aayushiiitd2025-byte/AAYUSH_LLM](https://github.com/aayushiiitd2025-byte/AAYUSH_LLM)

---

## Author

**Aayush Choudhary**
IIIT Delhi

```
```
