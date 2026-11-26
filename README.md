<h1 align="center">Ali Hashim Al-Rikabi</h1>

<p align="center">
  <strong>AI engineer building evaluation-driven RAG and agent tooling — with a focus on Arabic and multilingual systems.</strong><br>
  I measure before I claim, and I publish the results that contradict my own hypotheses.
</p>

<p align="center">
  <a href="mailto:alialrikabi313a@gmail.com"><img src="https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
  <a href="https://play.google.com/store/apps/developer?id=Ali+Al-rikabi313"><img src="https://img.shields.io/badge/Google_Play-Live_Apps-34A853?style=for-the-badge&logo=google-play&logoColor=white" alt="Google Play"></a>
</p>

---

## A finding worth your two minutes

I expected semantic chunking to beat fixed windows for Arabic RAG. On 442 questions it didn't: **chunk size, not chunking strategy, drives retrieval quality** — semantic chunks land exactly on the fixed-window trend, and the cheapest method (paragraphs) was best.

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
| **[arabic-rag-bench](https://github.com/alialrikabi313/arabic-rag-bench)** | Reproducible benchmark of chunking strategies for Arabic RAG, with bootstrap CIs and size-matched baselines | Paragraph chunks: Hit@1 **0.792**, MRR **0.863**; semantic chunking adds no gain at equal size |
| **[arabic-embed-bench](https://github.com/alialrikabi313/arabic-embed-bench)** | CLI to compare embedding models on *your* documents, with the prompt-prefix pitfalls handled | `e5-small` matches `bge-m3` within error at ~**9×** less encode time |
| **[arabic-rag-app](https://github.com/alialrikabi313/arabic-rag-app)** | Flutter RTL chat + FastAPI/bge-m3 backend; answers with numbered, tappable sources | Refusal threshold calibrated on 442 valid vs. 20 off-topic questions — trade-off table published |
| **[arabic-text-mcp](https://github.com/alialrikabi313/arabic-text-mcp)** | MCP server of deterministic Arabic text tools | Verified end-to-end over a real stdio MCP session |

All four have tests and CI workflows. The tests come from real failures I hit; the key chunking test is verified to fail when its bug is reintroduced.

## Shipped apps

- **[darb-maps](https://github.com/alialrikabi313/darb-maps)** — offline-capable navigation for Iraq on OpenStreetMap, with Iraqi-dialect voice guidance and driver-reported traffic
- **[anwarsajadia](https://github.com/alialrikabi313/anwarsajadia)** — Flutter app for the Sahifa Sajjadiyya and the Treatise on Rights, plus the Quran with tafsir, supplications and a compass
- More on [Google Play](https://play.google.com/store/apps/developer?id=Ali+Al-rikabi313)

## How I work

- **Evaluation first:** golden questions with verbatim-quote evidence, confidence intervals, and the baseline that could embarrass my idea.
- **Honest limits:** every README lists what the numbers do *not* show.
- **Production habits:** config-driven, resumable pipelines, explicit failure modes, tests drawn from real cases.

## Stack

**AI:** Python · sentence-transformers · Ollama / local LLMs · RAG evaluation · MCP  ·  **Backend:** FastAPI · NestJS · PostgreSQL · Docker  ·  **Mobile:** Flutter · Dart · Firebase
