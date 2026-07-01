# Beyond the Answer: Probing Numerical Reasoning in Financial LLMs

**Author:** Aayush Choudhary, IIIT Delhi
**Repo:** [github.com/aayushiiitd2025-byte/AAYUSH_LLM](https://github.com/aayushiiitd2025-byte/AAYUSH_LLM)

## Overview
This project investigates *why* financial LLMs get numerical reasoning wrong, not just how often — using the FinQA dataset (8,281 QA pairs over S&P 500 earnings reports). It goes beyond final-answer accuracy to study retrieval failures, reasoning-program correctness, context sensitivity, and silent failures where a plausible-looking answer hides an incorrect reasoning chain.

## Setup
- **Model:** Qwen2.5-0.5B-Instruct
- **Environment:** Google Colab (T4 GPU)
- **Dataset:** FinQA (8,281 QA pairs; 1,147 in the test set)

```bash
pip install transformers accelerate torch pandas matplotlib
```
Run all cells sequentially in `FinQA_Complete_Submission_Aayush.ipynb` on Colab.

## Approach

**Layer 1 — Dataset Analysis**
Studied FinQA's symbolic program structure, #N reference chaining, and evidence sources. Table evidence appears in ~75% of questions; 1-step programs dominate (54.2%) but a single wrong step propagates through the full chain.

**Layer 2 — Error Taxonomy**
Ran a 100-example few-shot evaluation. Retrieval errors dominated (~93% of failures — correct operations, wrong numbers pulled from context), while parsing and hallucination errors were minor. Execution accuracy (2%) and program accuracy (3%) frequently diverged, showing that getting the right answer doesn't mean reasoning correctly.

**Layer 2B — Context Sensitivity**
Compared Full Context, Table-Only, and Text-Only inputs. All three scored identically (2%) — traced to a prompt-contamination artifact (answers were embedded in the few-shot examples, not retrieved from context). This flagged an experimental design fix: future context-sensitivity tests need held-out few-shot examples.

**Layer 3 — Complexity Routing + Symbolic Verification**
Built a lightweight pipeline: classify question complexity → route to a shorter or fuller prompt → symbolically execute the model's own program and flag mismatches against its stated answer. This caught answer-program inconsistencies at zero extra inference cost, improving results from 2% (few-shot baseline) to 4%.

## Key Findings
- **Retrieval, not parsing, is the bottleneck** — 93% of errors were wrong-number retrieval, not malformed output (100% parse success with few-shot prompting).
- **A correct answer can mask incorrect reasoning** — the exec/program accuracy gap is the real reliability signal in regulated financial settings.
- **Tables matter most** — 75%+ of questions require table values.
- **Verification is essentially free** — symbolic checking triggered 22 times and corrected 2 cases, with no added inference cost.

## Why It Matters
A model that states one number while its reasoning chain computes another is a silent, high-confidence failure — dangerous in financial decision-making where the reasoning trail matters as much as the final figure. Symbolic verification catches this mismatch before it reaches a decision-maker.

## Repository Structure
```
FinQA_Complete_Submission_Aayush.ipynb   # Full implementation
NUMERICAL_REASONING_IN_FINANCIAL_LLMS_Aayush.pdf  # Written report
PPT_Aayush.pdf                            # Presentation slides
README.md
assets/
```

## Future Work
- Fine-tune a domain-specific reasoning model
- Add retrieval augmentation
- Improve table structure encoding
- Train a dedicated verifier model

## Acknowledgements
Dataset: FinQA — Numerical Reasoning over Financial Data
Model: Qwen2.5-0.5B-Instruct
