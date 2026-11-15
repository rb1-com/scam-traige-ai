# 🚨 Scam Triage AI

**Finance Track — Veritas AI International High School Hackathon**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rb1-com/scam-traige-ai/blob/main/ScamTriage_AI.ipynb)

Paste in any text message, email, or DM. In under a second, Scam Triage AI returns a **Scam Risk Score (0–100)**, lists the *specific red flags* it found, and tells you exactly what to do next — not just a yes/no verdict.

## Why it matters

Americans lost a record $15.9 billion to scams in 2025, and text messages were the single most common way scammers made first contact that year (FTC). Text-scam losses specifically hit $470 million in 2024 — five times 2020 levels — and young adults (18–29) saw the sharpest rise in scam-text attempts of any age group, roughly tripling (Consumer Reports, 2025).

## How it works

Two signals, combined, both running for free with no API key:

1. **A zero-shot AI model** (`facebook/bart-large-mnli`, via Hugging Face `transformers`) scores the message against "this is a scam" vs. "this is legitimate" — no training data required.
2. **An explainable rule engine** we wrote ourselves, scanning for real documented scam patterns: urgency language, gift-card/crypto payment requests, fake delivery fees, impersonation of a bank or agency, suspicious links, and more.

Every rule that fires is named in the output, so the result is always explainable, never a black box.

## Run it

Click the **Open in Colab** badge above — it opens this exact notebook in a live, runnable environment. Then Runtime → Run all, and try the built-in examples in the demo at the bottom.

## Tech stack

- Python
- Hugging Face `transformers` (`facebook/bart-large-mnli`)
- Gradio (demo UI)

## Credits

- Model: [`facebook/bart-large-mnli`](https://huggingface.co/facebook/bart-large-mnli)
- Demo UI: [Gradio](https://www.gradio.app/)
- Rule engine: written by our team, based on patterns documented in FTC text-scam spotlight reports
- AI coding assistance: Claude (Anthropic) helped write, debug, and structure this notebook
- Stats: FTC 2025 Consumer Sentinel data; FTC text-scam spotlight reports; Consumer Reports 2025 Cyber Readiness survey

No paid APIs, no labeled training dataset, no account sign-ups required.
