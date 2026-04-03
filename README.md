# emojiGPT 🧠✨

Train a tiny GPT on emoji stories — and watch it generate new ones token by token — **all in your browser**.

No server, no dependencies, no install. Just open `index.html`.

## What is this?

A complete, from-scratch GPT implementation running entirely in the browser:

- **Autograd engine** — full backpropagation, built from scalar `Value` nodes
- **Transformer architecture** — multi-head self-attention, RMSNorm, MLP, positional embeddings
- **Adam optimizer** — with bias correction and learning rate decay
- **KV-cache inference** — token-by-token generation with probability visualization

The model trains on ~170 emoji stories (editable!), learning patterns like "🌅 → ☕ → 🍳 → 😋" or "🤕 → 🏥 → 💉 → 🙏". After training, you can type any emoji prompt and watch the model continue the story, showing real-time probability distributions for each predicted token.

## Quick Start

1. Open `index.html` in your browser
2. Click **▶ Train** (takes ~30 seconds with default settings)
3. Scroll down to the inference playground
4. Type a few emoji (e.g. `🌅 🐓 🎵`) and press **Continue ▶**
5. Watch the model predict the story, one emoji at a time

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

- **Fully configurable** — embedding dim, heads, layers, block size, learning rate, temperature
- **Editable training data** — write your own emoji stories or paste AI-generated ones
- **Live training visualization** — loss curve, stats, auto-generated sample stories
- **Interactive inference** — type emoji prompts, see token-by-token generation with probability bars
- **Zero dependencies** — one self-contained HTML file

## Acknowledgements

This project is a derivative work built on top of an incredible chain of open-source contributions:

1. [**microGPT**](https://gist.github.com/karpathy/8627fe009c40f57531cb18360106ce95) by **Andrej Karpathy** — the original minimal GPT implementation in pure, dependency-free Python. It demonstrated that you can train and run a complete GPT from scratch in a single file, with a working autograd engine and transformer architecture. The original model generates English names.

2. [**microgpt.js**](https://github.com/xenova/microgpt.js) by **Xenova** — a JavaScript port of Karpathy's microGPT that brought the entire training and inference pipeline into the browser. This is the direct codebase that emojiGPT is built upon.

**What emojiGPT adds:** Starting from Xenova's microgpt.js, we redesigned the application from name generation to **emoji story generation** — a new training dataset of ~170 emoji narratives, a token-by-token inference playground with real-time probability visualization, and a fully reworked UI. The core autograd engine and transformer architecture come from the upstream projects above.

## License

MIT
