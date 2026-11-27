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
| **[arabic-retrieval-finetune](https://github.com/alialrikabi313/arabic-retrieval-finetune)** | Fine-tunes a small multilingual embedder for Arabic retrieval; evaluated on the **full** MIRACL-ar corpus (2.06M passages), with ablations; [model on Hugging Face](https://huggingface.co/Alialrikabi313/multilingual-minilm-arabic-retrieval) | nDCG@10 **0.145 → 0.394 ± 0.009** (3 seeds, ~30 s of training); with extra Mr.TyDi data (deduplicated against dev) 0.508; still below e5/bge-m3, reported as is |
| **[arabic-embed-throughput](https://github.com/alialrikabi313/arabic-embed-throughput)** | GPU sweep for Arabic embedders — precision, attention, `torch.compile`, ONNX Runtime, TensorRT, FP8/INT8 — with ranking parity and nDCG measured against fp32 | fp16 + SDPA is **3.0–3.7×** faster than fp32; TensorRT fp16 reaches **3.7–5.1×** with nDCG@10 within 0.0006 of fp32; dynamic INT8 was *slower* than fp32; bf16 reorders the top-10 more than fp16 but leaves nDCG unchanged |
| **[arabic-rag-bench](https://github.com/alialrikabi313/arabic-rag-bench)** | Reproducible benchmark of chunking strategies for Arabic RAG, with bootstrap CIs and size-matched baselines | Semantic chunking adds no gain at equal size and paragraphs match the best fixed size — across **two** question generators; the chunk-size trend is generator-dependent (paired bootstrap) |
| **[arabic-embed-bench](https://github.com/alialrikabi313/arabic-embed-bench)** | CLI to compare embedding models on *your* documents, with the prompt-prefix pitfalls handled — `pip install arabic-embed-bench` | `e5-small` matches `bge-m3` within error at ~**9×** less encode time |
| **[grounded-qa-eval](https://github.com/alialrikabi313/grounded-qa-eval)** | Scores whether an LLM answers only when the passage supports it and quotes its evidence verbatim, using hard negatives and no LLM judge | On two independently generated question sets (80 + 100 questions), a local 27B model abstained on 96–99% of hard negatives with 1 fabricated quote in 174 answers; false refusals ranged 2–11% depending on the question set |
| **[arabic-rag-app](https://github.com/alialrikabi313/arabic-rag-app)** | Flutter RTL chat + FastAPI/bge-m3 backend; answers with numbered, tappable sources | Refusal threshold calibrated on 442 valid vs. 20 off-topic questions — trade-off table published |
| **[arabic-text-mcp](https://github.com/alialrikabi313/arabic-text-mcp)** | MCP server of deterministic Arabic text tools — `pip install arabic-text-mcp` | Verified end-to-end over a real stdio MCP session |

All seven have tests and CI workflows. The tests come from real failures I hit; the key chunking test is verified to fail when its bug is reintroduced.

## Shipped apps

Production Flutter apps (Arabic, RTL), published under my own developer accounts:

- **20 apps live on [Google Play](https://play.google.com/store/apps/developer?id=Ali+Al-rikabi313)** — **~228,000 downloads in total** (from my Play Console, summed across the 20 apps; counts installs, not unique users), **4.9★ average** (4.93 over 931 ratings on the public store pages; 7 apps are at the 10K+ tier).
- **9 apps on the [App Store](https://apps.apple.com/us/developer/id1829770951)** — smaller footprint (e.g. the hadith library has 5 ratings).
- **[darb-maps](https://github.com/alialrikabi313/darb-maps)** — offline-capable navigation for Iraq on OpenStreetMap, with Iraqi-dialect voice guidance and driver-reported traffic.

*Download total: Play Console, as of 2026-11-26. Ratings and tiers: public store pages (Google shows install tiers there, not exact numbers).*

## How I work

- **Evaluation first:** golden questions with verbatim-quote evidence, confidence intervals, and the baseline that could embarrass my idea.
- **Honest limits:** every README lists what the numbers do *not* show.
- **Production habits:** config-driven, resumable pipelines, explicit failure modes, tests drawn from real cases.

## Stack

**AI:** Python · sentence-transformers · Ollama / local LLMs · RAG evaluation · MCP  ·  **Backend:** FastAPI · NestJS · PostgreSQL · Docker  ·  **Mobile:** Flutter · Dart · Firebase
