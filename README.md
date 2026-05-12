```markdown
Beyond the Answer: Probing Numerical Reasoning in Financial LLMs

This project explores how small language models perform on financial numerical reasoning tasks using the FinQA dataset.

Instead of focusing only on answer accuracy, this work investigates:
- retrieval failures
- reasoning correctness
- context sensitivity
- symbolic verification for improving reliability

The project was implemented using Qwen2.5-0.5B-Instruct on Google Colab (T4 GPU) and evaluated on 100 FinQA test examples.

------------------------------------------------------------

Key Findings

- Retrieval errors were the dominant failure mode
- Tables were more important than text for solving FinQA questions
- Models sometimes produced correct answers using incorrect reasoning
- Symbolic verification helped detect answer-program inconsistencies

------------------------------------------------------------

Proposed Improvement

Implemented:
- Complexity-based routing
- Symbolic verification layer

The goal was to improve reasoning reliability without using larger models or fine-tuning.

------------------------------------------------------------

Repository Structure

FinQA_Complete_Submission_Aayush.ipynb
PPT_Aayush.pdf
AAYUSH_Q_AND_A.pdf
README.md

------------------------------------------------------------

Setup

Install dependencies:

pip install transformers accelerate torch pandas matplotlib

Run the notebook:

FinQA_Complete_Submission_Aayush.ipynb

Recommended environment:
Google Colab T4 GPU

------------------------------------------------------------

GitHub Repository

https://github.com/aayushiiitd2025-byte/AAYUSH_LLM

------------------------------------------------------------

Author

Aayush Choudhary  
IIIT Delhi
```
