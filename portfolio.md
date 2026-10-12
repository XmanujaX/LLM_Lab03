# Portfolio – Lab 3 Transformer

## Step 1: Getting the Data
I loaded the `roneneldan/TinyStories` dataset from Hugging Face. It has ~2.1M training rows and 21,990 validation rows.

**Struggle:** At first, I accidentally loaded the `TinyStoriesInstruct` version. When I printed it, it just gave me weird labels like "Features: Dialogue" instead of actual stories. I had to switch to the original `TinyStories` dataset to get real text.

## Step 2 & 3: Preprocessing and Batching
I used 5,000 stories and built a character-level tokenizer. Vocab size was 65. I split it 90/10 for training and validation, with `block_size=128` and `batch_size=32`.

**Reflection:** Character-level is easy to set up, but the sequences are really long. A subword tokenizer like BPE would probably be more efficient next time.

## Step 4 & 5: Building and Initializing the Model
I implemented the Transformer from scratch. It has token/positional embeddings, masked multi-head attention, feed-forward layers, residual connections, and layer normalization. The model came out to **0.82 million parameters**. I used AdamW and cross-entropy loss.

## Step 6 & 7: Training and Monitoring
I trained for 5,000 iterations. Loss dropped from 4.37 to 1.13 (train) and 1.22 (val). 

**Reflection:** The loss curves are smooth and validation tracked training closely, so it wasn't overfitting. 
*(Evidence: `outputs/loss_curve.png`, `screenshots/training_logs.png`)*

## Step 8: Evaluation
Final validation loss: **1.2144**. Perplexity: **3.37**. Lower perplexity means the model is more confident about predicting the next character.

## Step 9: Generating Stories
Prompt: "Once upon a time"

**Result:** 
> "Once upon a time stick to find the bell. She had laughed it another. He bad on a give. She smole were was pretends!"

**Reflection:** It's word-shaped and uses real words, but it doesn't really make sense yet. Needs more data and training.
*(Evidence: `outputs/generated_stories.txt`)*

## Step 10: Experimenting with Settings
I noted that increasing to `n_layer=6`, `n_head=8`, `n_embd=256`, and `max_iters=10000` would likely improve output. I didn't have enough Colab GPU time to run this fully, but it's what I'd do next.

## Step 11: Saving the Model
Saved the weights and config (including vocab mappings) so I can load it later.

## Optional: Gradio Interface
Built a quick Gradio app so a user can type a prompt and get a story back. Cool to see it working in a web UI, even if the stories are a bit nonsensical right now.
*(Evidence: `screenshots/gradio_chat.png`)*

## Final Thoughts
Building attention from scratch was tough, but seeing the loss go down and watching the model learn to spell was pretty rewarding. I now actually understand how Transformers work under the hood.
