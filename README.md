<h1 align="center">Ali Hashim Al-Rikabi</h1>

<p align="center">
  <strong>AI engineer building evaluation-driven RAG and agent tooling — with a focus on Arabic and multilingual systems.</strong><br>
  I measure before I claim, and I publish the results that contradict my own hypotheses.<br>
  <strong>Open to remote work.</strong>
</p>

<p align="center">
  <a href="mailto:alialrikabi313a@gmail.com"><img src="https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
  <a href="https://play.google.com/store/apps/developer?id=Ali+Al-rikabi313"><img src="https://img.shields.io/badge/Google_Play-Live_Apps-34A853?style=for-the-badge&logo=google-play&logoColor=white" alt="Google Play"></a>
</p>

---

## A finding worth your two minutes

I expected semantic chunking to beat fixed windows for Arabic RAG. It didn't: **semantic chunks perform like fixed windows of the same size, and cheap paragraph chunks match the best fixed size** — and this held when I re-ran the benchmark with a second, different question generator. (The "bigger chunks are better" trend did *not* survive that check, and the repo says so.)

<p align="center">
  <a href="https://github.com/alialrikabi313/arabic-rag-bench">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://github.com/alialrikabi313/arabic-rag-bench/raw/main/docs/size-vs-hit1-dark.png">
      <img src="https://github.com/alialrikabi313/arabic-rag-bench/raw/main/docs/size-vs-hit1-light.png" alt="Hit@1 versus median chunk size" width="640">
    </picture>
  </a>
</p>

## Open-source work

| Project | What it does | Result |
|---|---|---|
| **[arabic-retrieval-finetune](https://github.com/alialrikabi313/arabic-retrieval-finetune)** | Fine-tunes a small multilingual embedder for Arabic retrieval; evaluated on the **full** MIRACL-ar corpus (2.06M passages), with ablations; [model on Hugging Face](https://huggingface.co/Alialrikabi313/multilingual-minilm-arabic-retrieval) | nDCG@10 **0.145 → 0.402** from 30 s of training (still below e5/bge-m3, reported as is); hard negatives gave no gain over random |
| **[arabic-embed-throughput](https://github.com/alialrikabi313/arabic-embed-throughput)** | GPU sweep of precision × attention × batch size for Arabic embedders, with a ranking-parity check against fp32 | fp16 + SDPA is **3.0–3.7×** faster than fp32/eager at ≥0.985 top-10 overlap; bf16 is as fast but diverged more (0.916 for e5-small) |
| **[arabic-rag-bench](https://github.com/alialrikabi313/arabic-rag-bench)** | Reproducible benchmark of chunking strategies for Arabic RAG, with bootstrap CIs and size-matched baselines | Semantic chunking adds no gain at equal size and paragraphs match the best fixed size — across **two** question generators; the chunk-size trend is generator-dependent (paired bootstrap) |
| **[arabic-embed-bench](https://github.com/alialrikabi313/arabic-embed-bench)** | CLI to compare embedding models on *your* documents, with the prompt-prefix pitfalls handled — `pip install arabic-embed-bench` | `e5-small` matches `bge-m3` within error at ~**9×** less encode time |
| **[grounded-qa-eval](https://github.com/alialrikabi313/grounded-qa-eval)** | Scores whether an LLM answers only when the passage supports it and quotes its evidence verbatim, using hard negatives and no LLM judge | A local 27B model abstained on 98.8% of hard negatives with 0 fabricated quotes — but wrongly refused 11% of answerable questions |
| **[arabic-rag-app](https://github.com/alialrikabi313/arabic-rag-app)** | Flutter RTL chat + FastAPI/bge-m3 backend; answers with numbered, tappable sources | Refusal threshold calibrated on 442 valid vs. 20 off-topic questions — trade-off table published |
| **[arabic-text-mcp](https://github.com/alialrikabi313/arabic-text-mcp)** | MCP server of deterministic Arabic text tools — `pip install arabic-text-mcp` | Verified end-to-end over a real stdio MCP session |

All seven have tests and CI workflows. The tests come from real failures I hit; the key chunking test is verified to fail when its bug is reintroduced.

## Shipped apps

Production Flutter apps (Arabic, RTL), published under my own developer accounts:

- **20 apps live on [Google Play](https://play.google.com/store/apps/developer?id=Ali+Al-rikabi313)** — **97,000+ installs combined** (sum of each app's public install tier; 7 apps are at 10K+), **4.93★ average over 931 ratings** (13 apps have enough ratings to show one).
- **9 apps on the [App Store](https://apps.apple.com/us/developer/id1829770951)** — smaller footprint (e.g. the hadith library has 5 ratings).
- **[darb-maps](https://github.com/alialrikabi313/darb-maps)** — offline-capable navigation for Iraq on OpenStreetMap, with Iraqi-dialect voice guidance and driver-reported traffic.

*Figures are from the public store pages, 2026-11-26. Install counts are lower bounds (Google shows tiers, not exact numbers).*

## How I work

- **Evaluation first:** golden questions with verbatim-quote evidence, confidence intervals, and the baseline that could embarrass my idea.
- **Honest limits:** every README lists what the numbers do *not* show.
- **Production habits:** config-driven, resumable pipelines, explicit failure modes, tests drawn from real cases.

## Stack

**AI:** Python · sentence-transformers · Ollama / local LLMs · RAG evaluation · MCP  ·  **Backend:** FastAPI · NestJS · PostgreSQL · Docker  ·  **Mobile:** Flutter · Dart · Firebase
