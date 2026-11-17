# Sovereign LLM Arena: Distributed Sensor Network Architecture Benchmark (16.11.26)

An automated multi-agent evaluation and satoshi (`sats`) state-ledger experiment testing **8 local Ollama models** in a full round-robin critique loop (`Generator` vs. `Validator`) across three systems-engineering lenses: **Conciseness**, **Technical Rigor**, and **Objectivity**.

## Experiment Overview
* **Date:** November 16, 2026 (`16.11.26`)
* **Prompt Domain:** Real-Time Distributed Sensor Network System Architecture (fault tolerance, strict latency, NFR-to-FR traceability, modularity, and verification strategies)
* **Total Test Cases:** 168 (`8 Generators × 7 Validators × 3 Lenses`)
* **Pass Threshold:** `OBJECTIVITY_SCORE >= 75`
* **Overall Run Health:** `164 PASS` | `1 FAIL` | `3 TIMEOUT ERRORS`
* **Final Ledger Owner:** `phi4:latest` (`10,000 sats` valuation, `locked: true`)

---

## Leaderboard (Generator Performance)

| Rank | Generator Model | Passes | Fails / Errors | Avg Score (All) | Avg Score (Pass) | Peak Score | Avg Duration (All) | Avg Duration (Pass) |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1** | **`huihui_ai/qwen3-abliterated:8b`** | 21 / 21 | 0 | **90.43** | 90.43 | 100 | 209.32s | 209.32s |
| **2** | **`mistral-nemo:12b`** | 21 / 21 | 0 | **90.24** | 90.24 | 100 | 157.82s | 157.82s |
| **3** | **`qwen2.5-coder:7b`** | 20 / 21 | 1 Error | **89.50** | 89.50 | 100 | 196.27s | 113.71s |
| **4** | **`phi4:latest`** | 21 / 21 | 0 | **88.90** | 88.90 | 100 | 233.58s | 233.58s |
| **5** | **`jaahas/gemma-2-9b-it-abliterated:latest`** | 21 / 21 | 0 | **88.57** | 88.57 | 100 | 190.06s | 190.06s |
| **6** | **`qwen2.5-coder:14b`** | 21 / 21 | 0 | **87.76** | 87.76 | 100 | 306.16s | 306.16s |
| **7** | **`llama3.2:3b`** | 20 / 21 | 1 Error | **86.25** | 86.25 | 95 | 143.88s | 60.21s |
| **8** | **`dolphin3:latest`** | 19 / 21 | 1 Fail, 1 Err | **82.50** | 86.84 | 100 | 237.42s | 136.37s |

---

## Validator Strictness (Judge Behavior)

| Validator Model | Cases Judged | Avg Score Given | Fails / Errors Triggered |
| :--- | :---: | :---: | :---: |
| **`llama3.2:3b`** *(Strictest)* | 21 | **83.10** | 0 |
| **`qwen2.5-coder:7b`** | 21 | **84.76** | 1 Fail (`Case21` scored `0`) |
| **`qwen2.5-coder:14b`** | 21 | **85.00** | 0 |
| **`mistral-nemo:12b`** | 21 | **85.95** | 0 |
| **`jaahas/gemma-2-9b-it-abliterated:latest`** | 21 | **87.10** | 0 |
| **`dolphin3:latest`** | 21 | **91.90** | 0 |
| **`huihui_ai/qwen3-abliterated:8b`** | 21 | **93.61** | 3 Timeout Errors (`conciseness` lens) |
| **`phi4:latest`** *(Most Lenient)* | 21 | **93.81** | 0 |

---

## Key Engineering & Ledger Findings

1. **Top-Tier Parity & Speed Trade-off:**
   `huihui_ai/qwen3-abliterated:8b` (`90.43`) and `mistral-nemo:12b` (`90.24`) crossed the **90+ average threshold** with 100% pass rates, with `mistral-nemo:12b` running ~25% faster (`157.82s` vs `209.32s`).
2. **Single-Lens Validator Hang (`huihui_ai/qwen3-abliterated:8b`):**
   All three `600,000ms` timeout errors (`Case1`, `Case67`, `Case151`) occurred exclusively when `huihui_ai/qwen3-abliterated:8b` acted as **Validator** on the **`conciseness`** lens—yet it scored `95–100` without issue on `technical` and `objectivity` for those exact same generators.
3. **Zero-Score Evasion Trap (`Case21`):**
   `dolphin3:latest` suffered the lone grading failure (`OBJECTIVITY_SCORE: 0` after 8 loops / `503.92s`) against `qwen2.5-coder:7b` on `objectivity` after triggering the anti-slop / corporate safe-harbor evasion filter.
4. **Prompt Evolution & Drift Dynamics (`16.11.26` JSON Ledger):**
   * The original `HOUSE` prompt (`created_at: 1794180710`) underwent **9 paid prompt modifications** (`200 sats` each) across 5 distinct models (`llama3.2:3b`, `dolphin3:latest`, `qwen2.5-coder:7b`, `phi4:latest`), generating semantic drift scores between **`0.704` and `0.926`**.
   * `phi4:latest` executed the final two refinements (`drift_score: 0.925`) and holds final locked ownership (`10,000 sats`).
   * *Schema Note:* Duplicate `"OWNERSHIP_TRANSFERRRED"` string typos remain present on timestamps `1794212070` and `1794212271`.

---

## Repository Structure
```text
├── data/
│   ├── state_ledger_16_11_26.json      # Satoshi ownership, prompt drift & modification log
│   └── benchmark_results_168.csv       # Full 168-case evaluation telemetry
├── outputs/
│   └── *.md                            # Individual Case1–Case168 markdown transcripts
├── scripts/
│   └── analyze_benchmark.py            # Generator & Validator telemetry aggregator
└── README.md
```
