# Foundation Models HW1 - LLM Forensics

**Home Assignment 1 (M.Sc. Data Science, HIT). Three sizes of Qwen2.5-Instruct (0.5B, 1.5B, 3B) investigated as a black box through controlled experiments — tokenization, decoding, long-context retrieval, scaling, inference efficiency and failure analysis. What can be learned about a foundation model from its behaviour, measurements and limits alone?**

## Headline Results
- **Position beats length:** a fact at the end of the document was retrieved in **24 of 24** conditions, while the middle broke at **8K** tokens for 0.5B and at **30K** for 3B. Scaling delayed the threshold, not removed it.
- **Uneven scaling:** overall score **0.333 / 0.583 / 0.750** from 0.5B to 3B, yet no task type improves at both steps.
- **Cache over weights:** 6.25× weights buy **2.25×** the score; KV cache buys up to **7.8×** speed, parameters unchanged.
- **Smaller and better:** 3B in 4-bit uses **1.914 GiB** and scores **0.708**, against 1.5B in bf16 at 2.875 GiB and 0.583.

## Key Features
- **Tokenizer Fingerprint:** Hebrew, English, numbers, dates, URLs, emoji and code compared by characters per token.
- **Decoding Strategies:** greedy, low and high temperature, top-k and top-p, five seeded runs each.
- **Context & Position:** a planted fact at start, middle and end, up to 30K tokens, plus a distractor test.
- **Inference Efficiency:** 27.5 vs. 42.4 ms per token, and speculative decoding 30–40% slower on this model pair.
- **Failure Forensics:** 275 failures collected automatically into a taxonomy, plus a minimal-pair experiment.
- **Bonus - Quantization Sweep:** bf16, 8-bit and 4-bit NF4 on the same benchmark.

## Repository Structure
- `Foundation Models HW1.ipynb`: Full solution notebook — all six experiments, the bonus and the forensic profile.
- `Assignment1.pdf`: Original assignment instructions.
