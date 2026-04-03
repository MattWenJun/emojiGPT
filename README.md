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

This project is inspired by and built upon the ideas from:

- [**microGPT**](https://gist.github.com/karpathy/8627fe009c40f57531cb18360106ce95) by **Andrej Karpathy** — the most atomic way to train and run a GPT, in pure dependency-free Python. The autograd engine and GPT architecture in emojiGPT directly follow this beautifully minimal design.

- [**microgpt.js**](https://github.com/xenova/microgpt.js) by **Xenova** — porting the microGPT concept to JavaScript for the browser. This project demonstrated that a full transformer training loop can run client-side, which directly inspired emojiGPT's browser-first approach.

## License

MIT
