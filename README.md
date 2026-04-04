# miniGPT 🧠✨

### The world's smallest GPT — train on emoji, English, or Chinese stories, all in your browser.

~4,000 parameters. Trains in 30 seconds. Runs entirely in your browser. No server, no dependencies, no install.

## What is this?

A complete, from-scratch GPT implementation running entirely in the browser:

- **Autograd engine** — full backpropagation, built from scalar `Value` nodes
- **Transformer architecture** — multi-head self-attention, RMSNorm, MLP, positional embeddings
- **Adam optimizer** — with bias correction and learning rate decay
- **KV-cache inference** — token-by-token generation with probability visualization

Three built-in datasets, switchable with one click:

| Dataset | Tokenizer | Example |
|---------|-----------|---------|
| 🌈 Emoji | space-split | `🌅 🐓 🎵 ☕ 🍳 😋` |
| 🔤 English | word-split | `the sun rose over the mountains` |
| 🀄 Chinese | char-split | `太阳升起来了，鸟儿开始歌唱` |
| 📂 Custom | auto-detect | upload any `.txt` file |

## Quick Start

1. Download `index.html` and open it in your browser — that's it, just one file
2. Pick a dataset tab: **Emoji**, **English**, **中文**, or upload your own
3. Click **▶ Train** (takes ~30 seconds with default settings)
4. Scroll down to the Inference Playground
5. Enter a prompt and press **Continue ▶** to watch token-by-token generation

> Works offline. No server needed. `file://` protocol and GitHub Pages both supported.

## Architecture

```
Token Embedding + Positional Embedding
          ↓
       RMSNorm
          ↓
  ┌─── Transformer Block (×N) ───┐
  │  RMSNorm → Multi-Head Attn   │
  │  + Residual                   │
  │  RMSNorm → MLP (ReLU)        │
  │  + Residual                   │
  └───────────────────────────────┘
          ↓
     Linear → Softmax → Loss
```

Default config: 16-dim embeddings, 4 attention heads, 1 layer, ~4K parameters.

## Features

- **3 built-in datasets** — Emoji / English / Chinese, switch instantly
- **Custom dataset** — drag & drop any `.txt` file (one story per line)
- **Auto tokenizer** — space-split for emoji/English, char-split for Chinese, auto-detect for custom
- **Fully configurable** — embedding dim, heads, layers, block size, learning rate, temperature
- **Live training visualization** — loss curve, stats, auto-generated sample stories
- **Interactive inference** — enter a prompt, watch token-by-token generation with probability bars
- **Zero dependencies** — one self-contained HTML file, works offline

## Use Cases

- **AI Education** — The most intuitive way to teach how GPT works. See the full pipeline live: data → training → loss curve → inference → generation. Switch between emoji, English, and Chinese to show how the same architecture handles different languages and tokenizers.
- **Cross-language Comparison** — Train on emoji, then English, then Chinese with identical hyperparameters. Watch how vocab size, loss curves, and generation quality change across tokenization strategies.
- **Narrative Prototyping** — Validate story structures at near-zero cost before scaling up to larger models.
- **Creative & Social** — Use generated emoji stories as prompts for improv writing, party games, or social media content.

## Why does it work?

How can a ~4K-parameter model generate coherent stories? The answer is dimensionality reduction.

**Emoji** collapse meaning aggressively — a single 🏥 carries what an English sentence takes twenty words to say. **Chinese characters** pack dense semantics into single tokens. **English words** sit in between. All three expose the same underlying principle: the transformer learns transition probabilities between tokens, and your brain fills in the rest.

Same architecture. Different token spaces. Same magic.

## Acknowledgements

Built on [**@karpathy**](https://gist.github.com/karpathy/8627fe009c40f57531cb18360106ce95)'s microGPT and [**@xenova**](https://github.com/xenova/microgpt.js)'s microgpt.js browser port. miniGPT extends their work with multi-language dataset switching, an embedded dataset system (no fetch needed), a custom file upload mode, and a redesigned UI.

## ⭐ Like it? Star it!

If you find this project useful, give it a **star** — it helps others discover it too.

## Follow Me

I write about AI, startups, and psychology.

- **WeChat public account:** MindCode
- **X:** [@moneygalaxy](https://x.com/moneygalaxy)
- **Substack:** [mindcodeplus](https://substack.com/@mindcodeplus)

## License

MIT
