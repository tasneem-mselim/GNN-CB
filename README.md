# GNN-CB: A Graph Neural Network Competition Benchmark

<p align="center">
  <img src="assets/logos/gnncb_logo.svg" alt="GNN-CB Logo" width="180"/>
</p>

<p align="center">
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-green.svg?logo=github" alt="MIT License"/></a>
  <a href="https://creativecommons.org/licenses/by-sa/4.0/"><img src="https://img.shields.io/badge/License-CC--BY--SA--4.0-green.svg?logo=github" alt="CC-BY-SA-4.0"/></a>
  <a href="https://arxiv.org/abs/XXXX.XXXXX"><img src="https://img.shields.io/badge/arXiv-XXXX.XXXXX-B31B1B.svg?logo=arxiv" alt="arXiv"/></a>
  <a href="https://basira-lab.github.io/gnncb/"><img src="https://img.shields.io/badge/Website-GNN--CB-2176BC?logo=GoogleChrome" alt="Website"/></a>
  <a href="https://basira-lab.github.io/gnncb/#leaderboard"><img src="https://img.shields.io/badge/Leaderboard-GNN--CB-FFD21E?logo=Hoopscotch" alt="Leaderboard"/></a>
</p>

Welcome to the official repository for the paper **"GNN-CB: A Graph Neural Network Competition Benchmark for Human and LLM Evaluation"**. GNN-CB is the **first competition-based benchmark** designed to evaluate both humans and large language models (LLMs) on executable graph neural network (GNN) coding tasks under controlled, reproducible competition settings.

---

## 📑 Table of Contents

- [💥 News](#-news)
- [📖 Introduction](#-introduction)
- [🏗️ Benchmark Overview](#-benchmark-overview)
- [🏆 Leaderboard](#-leaderboard)
- [⚙️ LLM Evaluation](#-llm-evaluation)
  - [Environment Setup](#environment-setup)
  - [Non-Agent Evaluation](#non-agent-evaluation)
  - [Agent-Based Evaluation](#agent-based-evaluation)
  - [Submission Format](#submission-format)
- [👥 Human Evaluation Protocol](#-human-evaluation-protocol)
- [📂 Repository Structure](#-repository-structure)
- [📊 Results Summary](#-results-summary)
- [🤖 Supported Models](#-supported-models)
- [📜 License](#-license)
- [📚 Citation](#-citation)

---

## 💥 News

- **[2026.05.23]** 🎉 **GNN-CB** paper submitted to EMNLP 2026! Benchmark and evaluation infrastructure publicly released.
- **[2026.05.20]** 🚀 Live leaderboards are now available at [basira-lab.github.io/gnncb](https://basira-lab.github.io/gnncb/#leaderboard).
- **[2026.05.15]** 📦 All 18 competition repositories with automated GitHub Actions pipelines are now live.

---

## 📖 Introduction

Graph Neural Networks (GNNs) are central to modern graph machine learning, yet no benchmark has systematically evaluated whether LLMs can autonomously solve realistic **end-to-end GNN coding tasks**. GNN-CB bridges this gap.

**Key features:**

- **18 curated competitions** spanning node-, edge-, and graph-level prediction across 7 graph categories and 4 difficulty tiers.
- **Unified hidden-test evaluation pipeline** via automated GitHub Actions — identical conditions for all human and LLM submissions.
- **Three complementary protocols:** competition design, controlled human evaluation, and frozen-prompt LLM evaluation with bounded execute-and-repair loops.
- **Two LLM evaluation modes:** API-only non-agent and autonomous agent-based, supporting both proprietary and open-source models.
- **Living benchmark:** dynamic leaderboards, reproducible pipelines, and an open submission infrastructure.

**Key findings:**

- Frontier proprietary reasoning LLMs (Claude Opus 4.7, GPT-5.4 Codex, Gemini 2.5 Pro) approach human performance on **Easy** tasks but lag substantially on **Medium** and **Hard** competitions.
- The dominant LLM failure mode is **consistency** across heterogeneous tasks, not peak capability — every model achieves at least one near-human score, yet none sustains that level on average.
- Competition-style, repository-grounded evaluation provides a more discriminating signal of GNN coding ability than isolated-function benchmarks.

---

## 🏗️ Benchmark Overview

GNN-CB contains **18 independent competitions** organized along two axes:

| Axis | Values |
|------|--------|
| **Graph Category** | Homogeneous, Heterogeneous, Temporal, Spatial, Hierarchical, Molecular, Generalization |
| **Difficulty** | Easy, Medium, Hard, Expert |
| **Task Type** | Node Classification, Edge Classification, Graph Classification, Graph Regression |
| **Domains** | Biomedical, Finance, Social, Cybersecurity, Neuroimaging, Academic, Urban, Bioprinting |

### Competition Summary Table

| ID | Competition | Category | Difficulty | Task | Domain | Metric | Dataset |
|-----|-------------|----------|-----------|------|--------|--------|---------|
| C01 | PROVEN-GNN | Hetero | Med | Graph Classification | Cybersecurity | Macro-F1 | DiverseVul |
| C02 | CGCC | Homo | Hard | Graph Classification | Urban | Macro-F1 | OpenStreetMap |
| C03 | Real Or Fake! | Hier | Easy | Graph Classification | Social | Binary F1 | GossipCop |
| C04 | GLIMPS-GNN | Gen | Hard | Node Classification | Biomedical | F1 | GEO |
| C05 | GNN_BACE | Mol | Med | Graph Classification | Medical | Macro-F1 | BACE |
| C06 | DiaGraph | Homo | Hard | Node Classification | Medical | Macro-F1 | Kaggle Diabetes |
| C07 | GRAPE | Spatial | Med | Graph Classification | Medical | Macro-F1 | DRIVE/STARE/HRF |
| C08 | Liar Nodes | Homo | Easy | Node Classification | Biomedical | Accuracy | CancerSCEM |
| C09 | GraphFMD | Temp | Med | Node Classification | Finance | Macro-F1 | Elliptic |
| C10 | NetLinkArena | Homo | Med | Link Prediction | Academic | AUC-ROC | CiteSeer |
| C11 | PARK-GNN | Homo | Hard | Node Classification | Medical | Macro-F1 | UCI Parkinson's |
| C12 | GNN-CoRA | Homo | Med | Node Classification | Academic | Accuracy | Cora |
| C13 | GTA | Gen | Hard | Graph Classification | Bioinformatics | Macro-F1 | MUTAG |
| C14 | BrainAge | Homo | Easy | Graph Regression | Neuroimaging | MAE | OASIS-3 |
| C15 | OctoNode Cup | Homo | Med | Node Classification | Social | Macro-F1 | GitHub Social |
| C16 | Graph4ASD | Homo | Med | Graph Classification | Neuroimaging | Macro-F1 | ABIDE |
| C17 | Mix2Print | Homo | Hard | Graph Regression | Bioprinting | NMAE | CECT |
| C18 | THInC | Spatial | Hard | Node Classification | Biomedical | Macro-F1 | NuCLS |

Each competition repository includes: task README, dataset files, submission specification, evaluation metric, hidden test set, and automated GitHub Actions scoring pipeline.

---

## 🏆 Leaderboard

The interactive leaderboard is available at **[basira-lab.github.io/gnncb/#leaderboard](https://basira-lab.github.io/gnncb/#leaderboard)**.

Below is a summary of LLM performance vs. human top across all 18 competitions:

| Model | Family | Mode | Easy (avg) | Med (avg) | Hard (avg) | Mean Gap ↓ |
|-------|--------|------|-----------|----------|-----------|------------|
| **Claude Opus 4.7** | Proprietary Reasoning | Agent | 0.987 | 0.728 | 0.543 | ↓ 0.148 |
| **Gemini 2.5 Pro** | Proprietary Reasoning | Non-Agent | 0.931 | 0.696 | 0.398 | ↓ 0.179 |
| **GPT-5.4 Codex** | Proprietary Reasoning | Agent | 0.865 | 0.714 | 0.531 | ↓ 0.182 |
| **Gemini-3 Flash** | Proprietary Chat | Non-Agent | 0.982 | 0.693 | 0.453 | ↓ 0.174 |
| **Claude Opus 4.6** | Proprietary Chat | Non-Agent | 0.968 | 0.721 | 0.487 | ↓ 0.163 |
| **DeepSeek-v4 Pro** | Open-source Reasoning | Non-Agent | 0.841 | 0.654 | 0.372 | ↓ 0.221 |
| **Kimi k2.6** | Open-source Chat | Non-Agent | 0.786 | 0.720 | 0.508 | ↓ 0.198 |
| **Qwen2.5-Coder 32B** | Open-source Chat | Non-Agent | 0.816 | 0.602 | 0.337 | ↓ 0.265 |
| **Llama-3.3 70B** | Open-source Chat | Non-Agent | 0.728 | 0.543 | 0.389 | ↓ 0.299 |
| **Human Top** | — | — | 0.987 | 0.854 | 0.756 | — |

Blue subscripts ↓ indicate performance drop below the human top. See the [website leaderboard](https://basira-lab.github.io/gnncb/#leaderboard) for full per-competition scores.

---

## ⚙️ LLM Evaluation

### Environment Setup

```bash
conda create --name gnncb python=3.10
conda activate gnncb
pip install -r requirements.txt
touch .env
```

Set your API keys in `.env`:

```
OPENAI_API_KEY=your-OpenAI-api-key
ANTHROPIC_API_KEY=your-Anthropic-api-key
GOOGLE_API_KEY=your-Google-api-key
DEEPSEEK_API_KEY=your-DeepSeek-api-key
TOGETHER_API_KEY=your-Together-api-key
```

### Non-Agent Evaluation

The non-agent mode uses a frozen prompt template with slot filling (README, repository tree, dataset summary, submission spec, requirements) and a bounded execute-and-repair loop (k ≤ 5):

```bash
cd evaluation/non_agent

# Run a single competition
python run_evaluation.py \
    --model claude-opus-4-6 \
    --competition C03 \
    --repair_limit 5 \
    --output_dir results/

# Run all competitions for a model
./run_all_competitions.sh --model gemini-2.5-pro
```

The instantiated prompt follows a `<plan>` → `<code>` paradigm, producing a structured reasoning plan and a standalone `solution.py` executed under CPU-only constraints.

### Agent-Based Evaluation

The agent-based mode allows autonomous repository exploration, code generation, execution, and iterative repair without human intervention:

```bash
cd evaluation/agent

# Run agent-based evaluation (Claude Code / GPT-5.4 Codex)
python run_agent_evaluation.py \
    --model claude-opus-4-7 \
    --competition C03 \
    --repair_limit 5 \
    --output_dir results/agent/
```

Both modes enforce identical evaluation conditions: same repository information, same CPU-only execution constraints, and the same automated hidden-test scoring pipeline.

### Submission Format

All models submit a `predictions.csv` file through the automated hidden-test pipeline. The file must contain exactly two columns:

```csv
id,y_pred
0,1
1,0
2,1
...
```

For regression tasks (C14, C17), `y_pred` should be a floating-point value. For link prediction (C10), submit a probability score. See each competition's `submit_spec.md` for task-specific details.

**Per-competition submission portals** are listed in [`competition_links.md`](competition_links.md).

### Evaluation Output

After evaluation, results are stored in `results/MODEL-LABEL/`:

```
results/
  claude-opus-4-6/
    C03_Real_Or_Fake/
      plan.txt          # generated reasoning plan
      solution.py       # generated executable code
      predictions.csv   # submitted predictions
      score.json        # hidden-test score
      repair_log.txt    # traceback + repair history
```

---

## 👥 Human Evaluation Protocol

Human participants solve each competition under the following standardized constraints:

| Constraint | Value |
|-----------|-------|
| **Architecture** | GNN only (no CNN, RNN, or Transformers) |
| **Compute budget** | 3 CPU hours per task |
| **Random seed** | Fixed at `seed=25` |
| **Submissions** | 1 final submission per competition |
| **HP tuning runs** | ≤ 5 |
| **LLM assistance** | Low-level utility only; no task-specific context |

Each participant maintains a documentation log recording: hyperparameter search strategy, all configurations attempted, training time, hardware specs, and any LLM-assisted snippets. Prediction files are encrypted locally before upload via pull-request to prevent information leakage.

Human performance statistics (mean, standard deviation, best, worst) across all 18 competitions are available in Table 2 of the paper and on the [leaderboard page](https://basira-lab.github.io/gnncb/#leaderboard).

---

## 📂 Repository Structure

```
gnncb/
├── README.md
├── requirements.txt
├── competition_links.md          # per-competition submission portal links
├── evaluation/
│   ├── non_agent/
│   │   ├── run_evaluation.py     # non-agent orchestration pipeline
│   │   ├── run_all_competitions.sh
│   │   └── prompt_template.txt   # frozen prompt shared across all 18 tasks
│   └── agent/
│       └── run_agent_evaluation.py
├── competitions/
│   ├── C01_PROVEN_GNN/           # competition-specific README, data, spec
│   ├── C02_CGCC/
│   ├── ...
│   └── C18_THInC/
├── results/                      # per-model, per-competition outputs
├── assets/
│   ├── logos/
│   ├── figures/
│   └── examples/
└── docs/                         # GitHub Pages source (index.html)
```

---

## 📊 Results Summary

**Human performance** exhibits substantial variability across tasks:
- Easy tasks (C03, C08, C14): high scores with low variance — participants reliably implement standard GNN pipelines.
- Hard tasks (C02, C04, C11, C18): lower averages and larger best–worst gaps — sensitive to architectural choices and optimization quality.

**LLM performance** stratifies clearly by difficulty:
- On Easy competitions, frontier models approach or match human top (e.g., Claude Opus 4.7 reaches 0.998 on C08).
- On Medium and Hard tasks, sizeable gaps persist (0.05–0.40 below human top).
- The **Best–Mean gap** (26–44 pp) indicates that no model reliably sustains its peak performance across diverse tasks.
- Two LLMs exceed human top on specific tasks: Kimi k2.6 on C09 GraphFMD (+0.153) and GPT-5.4 Codex on C13 GTA (+0.036).

---

## 🤖 Supported Models

| Model | Provider | Mode | API |
|-------|----------|------|-----|
| Claude Opus 4.7 | Anthropic | Agent | `claude-opus-4-7` |
| Claude Opus 4.6 | Anthropic | Non-Agent | `claude-opus-4-6` |
| GPT-5.4 Codex | OpenAI | Agent | `gpt-5.4-codex` |
| Gemini 2.5 Pro | Google DeepMind | Non-Agent | `gemini-2.5-pro` |
| Gemini-3 Flash | Google DeepMind | Non-Agent | `gemini-3-flash` |
| DeepSeek-v4 Pro | DeepSeek-AI | Non-Agent | `deepseek-v4-pro` |
| Llama-3.3 70B | Meta AI | Non-Agent | `meta-llama/Llama-3.3-70B-Instruct` |
| Qwen2.5-Coder 32B | Alibaba Cloud | Non-Agent | `Qwen/Qwen2.5-Coder-32B-Instruct` |
| Kimi k2.6 | Moonshot AI | Non-Agent | `kimi-k2.6` |

To add support for additional models, implement the model interface in `evaluation/engines/factory.py` and add the API key to your `.env` file. Pull requests are welcome.

---

## 📜 License

- **Code**: Released under the [MIT License](LICENSE).
- **Benchmark data and competition repositories**: Released under [CC BY-SA 4.0](LICENSE-DATA).
- All datasets are used under their original public licenses (MoleculeNet, Cora, OGB, OASIS-3 data-use agreement, Elliptic, GossipCop, GitHub Social Network, etc.). LLMs are accessed under providers' API terms of service.

**Ethics note:** LLM-generated GNN code, if deployed in safety-critical domains (medical diagnosis, financial fraud detection, neuroimaging) without expert verification, could amplify model failures or propagate dataset biases. GNN-CB is released for controlled research and educational use.

---

## 📚 Citation

If you use **GNN-CB** in your work, please cite:

```bibtex
@inproceedings{gnncb2026,
  title     = {GNN-CB: A Graph Neural Network Competition Benchmark for Human and LLM Evaluation},
  author    = {Anonymous},
  booktitle = {Proceedings of the 2026 Conference on Empirical Methods in Natural Language Processing (EMNLP)},
  year      = {2026}
}
```

---

<p align="center">Basira Lab · GNN-CB 2026</p>
