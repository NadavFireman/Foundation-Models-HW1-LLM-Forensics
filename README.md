# Foundation Models - LLM Forensics (HW1)

**Home Assignment 1 (M.Sc. Data Science, HIT). Three sizes of Qwen2.5-Instruct (0.5B, 1.5B, 3B) reverse-engineered as a black box through controlled experiments — tokenization, decoding, long-context retrieval, scaling, inference efficiency and failure analysis — ending in an evidence-based forensic profile of the model.**

## Headline Results
- **Position beats length:** a fact planted at the end of the document was retrieved in 24 of 24 conditions across both tested sizes, while the middle broke at 8K tokens for 0.5B and at 30K for 3B — scaling delayed the threshold rather than removing it.
- **Uneven scaling:** overall benchmark score rises 0.333 / 0.583 / 0.750 from 0.5B to 3B, yet no task type improves at both steps — code hits the ceiling at 1.5B while reasoning stays among the lowest at 3B.
- **Cache over weights:** 6.25× more weights buys 2.25× the score, while the KV cache buys up to 7.8× speed without changing a single parameter.

## Key Features
- **Tokenizer Fingerprint:** Hebrew, English, numbers, dates, URLs, emoji and code compared by token count and characters-per-token efficiency.
- **Decoding Strategies:** greedy, low and high temperature, top-k and top-p, five seeded runs each, on a factual and an open-ended task.
- **Context & Position:** a synthetic needle at the start, middle and end across context lengths up to 30K tokens, plus a multi-fact distractor test.
- **Inference Efficiency:** decode cost measured at 27.5 vs. 42.4 ms per token (0.5B vs. 3B), and a speculative decoding run (0.5B drafting for 3B) that came out 30–40% slower, explained by the measured 1.54× draft/target speed gap.
- **Failure Forensics:** 275 failures collected automatically against pre-defined criteria into a taxonomy, with a minimal-pair experiment on a reasoning failure.
- **Bonus — Quantization Sweep:** 3B in 4-bit uses 1.914 GiB and scores 0.708, versus 1.5B in bf16 at 2.875 GiB and 0.583 — smaller and better.
- **Reproducibility:** one factor changed per experiment, greedy or seeded runs (seed 51095), single NVIDIA L4 in bf16.

## Repository Structure
- `Foundation Models HW1.ipynb`: Full solution notebook — all six experiments, the bonus and the forensic profile (explanations in Hebrew).
- `Assignment1.pdf`: Original assignment instructions.
