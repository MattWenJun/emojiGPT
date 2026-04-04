# emojiGPT 🧠✨

### The world's smallest GPT that covers the full pipeline — dataset curation, training, inference, and story generation — in one file.

~4,000 parameters. Trains in 30 seconds. Runs entirely in your browser. No server, no dependencies, no install.

## What is this?

A complete, from-scratch GPT implementation running entirely in the browser:

- **Autograd engine** — full backpropagation, built from scalar `Value` nodes
- **Transformer architecture** — multi-head self-attention, RMSNorm, MLP, positional embeddings
- **Adam optimizer** — with bias correction and learning rate decay
- **KV-cache inference** — token-by-token generation with probability visualization

The model trains on ~170 emoji stories (editable!), learning patterns like "🌅 → ☕ → 🍳 → 😋" or "🤕 → 🏥 → 💉 → 🙏". After training, you can type any emoji prompt and watch the model continue the story, showing real-time probability distributions for each predicted token.

## Quick Start

1. Download `index.html` and open it in your browser — that's it, just one file
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

## Why does it work?

How can a ~4K-parameter model generate coherent stories? The answer is a blend of AI and cognitive psychology.

**Emoji are a natural dimensionality reduction.** A single 🏥 carries the meaning that would take an entire sentence in English. By training on emoji sequences instead of text, we collapse the problem space by orders of magnitude.

**The other half of the magic is you.** Your brain automatically unpacks each emoji into a rich scene — the hospital visit, the injection, the prayer, the relief. The model writes a compressed story; your mind decompresses it into a full one.

Emoji as dimensionality reduction + the human brain as the decompressor — that's how a tiny transformer learns to tell stories.

## Acknowledgements

Built on [**@karpathy**](https://gist.github.com/karpathy/8627fe009c40f57531cb18360106ce95)'s microGPT and [**@xenova**](https://github.com/xenova/microgpt.js)'s microgpt.js browser port — beautiful, minimal implementations that made this possible. emojiGPT extends their work from name generation to emoji story generation, with a new training dataset, inference playground, and UI.

## ⭐ Like it? Star it!

If you find this project interesting, give it a **star** — it helps others discover it too.

## Follow Me

I write about AI, startups, and psychology.

- **WeChat public account:** MindCode
- **X:** [@moneygalaxy](https://x.com/moneygalaxy)
- **Substack:** [mindcodeplus](https://substack.com/@mindcodeplus)

## License

MIT
