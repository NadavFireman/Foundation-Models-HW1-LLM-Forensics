# Foundation Models - LLM Forensics (HW1)

**Home Assignment 1 (M.Sc. Data Science, HIT). Controlled black-box experiments on Qwen2.5-Instruct (0.5B / 1.5B / 3B) covering tokenization, decoding, long-context retrieval, scaling behaviour, inference efficiency and failure analysis.**

## Headline Results

- **Position > length:** end-of-context facts retrieved in 24/24 conditions; middle-context retrieval failed at 8K (0.5B) and 30K (3B).
- **Uneven scaling:** overall score 0.333 → 0.583 → 0.750; code saturates early while reasoning lags.
- **Cache over weights:** KV cache delivers up to 7.8× speedup; 4-bit 3B (0.708) outperforms bf16 1.5B (0.583) at lower memory.

## Key Features

- Tokenizer fingerprint across Hebrew, English, numbers, code and emoji
- Decoding strategies (greedy, temperature, top-k, top-p)
- Needle-in-a-haystack position & length tests up to 30K tokens
- Inference timing + speculative decoding experiment
- Automated failure taxonomy (275 cases)
- Quantization sweep (bonus)

## Repository Structure

- `Foundation Models HW1.ipynb` — full solution notebook (explanations in Hebrew)
- `Assignment1.pdf` — original assignment instructions
