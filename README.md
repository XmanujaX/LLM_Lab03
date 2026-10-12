# Lab 3 – TinyStories Transformer Portfolio

**Student:** [Hingurala Perera - 10965291]
**Module:** [PUSL3205]
**Date:** 10 October 2026

## What is this?
I built a character-level Transformer from scratch in PyTorch for Lab 3. I trained it on the `roneneldan/TinyStories` dataset to see if a small model could generate short stories.

## Repo Structure
- `notebooks/LLM.ipynb` – My working Colab notebook.
- `outputs/` – Loss curve, training logs, generated stories.
- `screenshots/` – Evidence of dataset, training, and Gradio UI.
- `portfolio.md` – My step-by-step notes and reflections.

## How to Run
1. Open `notebooks/LLM.ipynb` in Colab.
2. Set the runtime to GPU (T4).
3. Run all cells. The last cell launches a Gradio chat window.

## Model Summary
| Item | Value |
|---|---|
| Dataset | TinyStories (2.1M rows) |
| Subset | 5,000 stories |
| Tokenizer | Character-level |
| Vocab Size | 65 |
| Params | 0.82 M |
| Iterations | 5,000 |
| Train Loss | 1.13 |
| Val Loss | 1.22 |
| Perplexity | 3.37 |

## Sample Output
**Prompt:** "Once upon a time"
**Generated:** "Once upon a time stick to find the bell. She had laughed it another..."

## Takeaways
- A 0.82M parameter model can learn basic grammar in 5,000 steps.
- Character-level tokenization is easy but limits long-range coherence.
- The text is word-shaped but loses the plot after a few words.
