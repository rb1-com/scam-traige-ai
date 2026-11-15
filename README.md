# 🚨 Scam Triage AI

**Finance Track — Veritas AI International High School Hackathon**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rb1-com/scam-traige-ai/blob/main/ScamTriage_AI.ipynb)

Paste in any text message, email, or DM. In under a second, Scam Triage AI returns a **Scam Risk Score (0–100)**, lists the *specific red flags* it found, and tells you exactly what to do next — not just a yes/no verdict.

## Why it matters

Americans lost a record $15.9 billion to scams in 2025, and text messages were the single most common way scammers made first contact that year (FTC). Text-scam losses specifically hit $470 million in 2024 — five times 2020 levels — and young adults (18–29) saw the sharpest rise in scam-text attempts of any age group, roughly tripling (Consumer Reports, 2025).

## How it works

Two signals, combined:

1. **A classifier trained from scratch** (TF-IDF + Logistic Regression, scikit-learn) on the **SMS Spam Collection** — 5,574 real, hand-labeled text messages. Evaluated against a baseline and tested on held-out data it never saw during training.
2. **An explainable rule engine** we wrote ourselves, scanning for real documented scam patterns: urgency language, gift-card/crypto payment requests, fake delivery fees, impersonation of a bank or agency, suspicious links, and more.

Every rule that fires is named in the output, so the result is always explainable, never a black box.

## Results (held-out test set, 1,115 messages never seen in training)

| Metric | Baseline ("always guess not-spam") | Our trained model |
|---|---|---|
| Accuracy | 86.6% | **97.7%** |
| Recall on spam | 0.0% (catches nothing) | **91.3%** |
| Precision on spam | n/a | **91.3%** |

We also stress-tested the model on 5 modern (2020s-style) scam messages we wrote ourselves, since the training data is from the early 2010s — it correctly caught 3/5, missing newer, low-keyword scam openers like "wrong number" pivot-texts. That gap is exactly what the rule engine is there to help cover, and it's discussed in the notebook and write-up.

## Run it

Click the **Open in Colab** badge above — it opens this exact notebook in a live, runnable environment. Then Runtime → Run all, and try the built-in examples in the demo at the bottom.

## Tech stack

- Python, pandas, scikit-learn (TF-IDF + Logistic Regression)
- Gradio (demo UI)

## Credits

- Dataset: SMS Spam Collection (5,574 labeled messages)
- Model: TF-IDF + Logistic Regression, trained from scratch with scikit-learn
- Demo UI: [Gradio](https://www.gradio.app/)
- Rule engine: written by our team, based on patterns documented in FTC text-scam spotlight reports
- AI coding assistance: Claude (Anthropic) helped write, debug, and structure this notebook and the evaluation pipeline
- Stats: FTC 2025 Consumer Sentinel data; FTC text-scam spotlight reports; Consumer Reports 2025 Cyber Readiness survey

This project is a prototype and is not financial advice.

No paid APIs, no account sign-ups required. One public dataset, trained from scratch, fully reproducible in the notebook.
