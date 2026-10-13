<p align="center">
  <img src="docs/assets/img/banner.png" alt="OmniStepBench: a lobster evaluator checking the evidence" width="820">
</p>

<h1 align="center">OmniStepBench: Deployment-Aware Agent Evaluation across Modalities and Task Complexity</h1>

<p align="center">
  <a href="https://arxiv.org/abs/2609.06059"><img src="https://img.shields.io/badge/arXiv-2609.06059-b31b1b?style=flat-square&amp;logo=arxiv&amp;logoColor=white" alt="arXiv paper"></a>
  <a href="https://seerray-lab.github.io/OmniStepBench/"><img src="https://img.shields.io/badge/Page-1b3a5c?style=flat-square&amp;logo=githubpages&amp;logoColor=white" alt="Project page"></a>
  <a href="https://seerray-lab.github.io/OmniStepBench/#leaderboard"><img src="https://img.shields.io/badge/Leaderboard-e8604c?style=flat-square" alt="Interactive leaderboard"></a>
  <a href="https://github.com/SeerRay-Lab/OmniStepBench"><img src="https://img.shields.io/badge/Code-29233f?style=flat-square&amp;logo=github&amp;logoColor=white" alt="GitHub code"></a>
  <a href="https://huggingface.co/datasets/SeerRay-Lab/OmniStepBench"><img src="https://img.shields.io/badge/Dataset-e3ad25?style=flat-square&amp;logo=huggingface&amp;logoColor=white" alt="Hugging Face dataset"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-Apache_2.0-blue?style=flat-square" alt="License: Apache-2.0"></a>
  <a href="#citation"><img src="https://img.shields.io/badge/BibTeX-d6336c?style=flat-square" alt="Citation"></a>
</p>

<p align="center"><b>One shared OpenClaw runtime. A 2&times;3 workload matrix. Evidence-based score auditing.</b></p>

<p align="center"><a href="#overview">Overview</a> &middot; <a href="#leaderboard">Leaderboard</a> &middot; <a href="#quick-start">Quick Start</a> &middot; <a href="#citation">Citation</a></p>

## News

- **Oct 2026** &mdash; The leaderboard covers 42 models (30 API + 12 local), including GPT-6-Astra, GPT-6.1-Sol, Claude-Opus-5.5, Kimi-K3, Qwen3.8-Max and MiMo-V2.6.
- **5 Sep 2026** &mdash; The paper is on [arXiv](https://arxiv.org/abs/2609.06059).
- The [project page](https://seerray-lab.github.io/OmniStepBench/) has the interactive leaderboard, the accuracy&ndash;cost frontiers and the evidence-based audit.

## Overview

OmniStepBench is a benchmark for deployment-aware agent evaluation across modalities and task complexity.
Built on a shared OpenClaw execution environment, it organizes **233 tasks** selected and adapted from
**22 source benchmarks** into a **2&times;3 workload matrix** defined by input modality and execution form, and
evaluates them under a unified contract-based protocol with evidence-based score auditing. The paper evaluates
30 commercial API models and 12 locally deployed open-weight models (42 models in total) over
9,218 model&ndash;task runs, reporting accuracy and token consumption alongside reference costs for API models.

<p align="center">
  <a href="docs/assets/img/overview.png"><img src="docs/assets/img/overview.png" alt="Overview of OmniStepBench: task construction, shared agent execution, scoring with evidence-based audit, and metrics" width="100%"></a>
</p>

*Overview of OmniStepBench (paper Fig. 2): (1) constructing 233 tasks from 22 source benchmarks and organizing
them by modality and execution form; (2) executing all models in a shared agent environment; (3) applying automated,
LLM-based, or hybrid scoring with evidence-based auditing; and (4) reporting overall and workload-level accuracy,
token usage, reference cost, and accuracy&ndash;cost frontiers.*

### Workload matrix

| | Single-step | Multi-step | Multi-step + tools |
| --- | --- | --- | --- |
| **Text** | **20 tasks**<br>LogiQA · GPQA | **87 tasks**<br>AdvancedIF · Bamboogle · SimpleQA · LongBench · LexEval · TableBench · FinQA | **55 tasks**<br>DeepSearchQA · WideSearch · Seal0 · TerminalBench2 · OpenAgentSafety · OSWorld |
| **Multimodal** | **20 tasks**<br>SimpleVQA · HLE | **26 tasks**<br>CharXiv · MedXpertQA | **25 tasks**<br>AgentVista · MMSearch · MMSearchPlus |

Scoring: 125 automated, 73 LLM-judged and 35 hybrid tasks.

## Leaderboard

Audited accuracy (%) from paper Table 1 (first 10 API models in the paper's order, plus the strongest local model).
The [interactive leaderboard](https://seerray-lab.github.io/OmniStepBench/#leaderboard) covers all 42 models, with API/local filters and sorting.

| Model | Text-SS | Text-MS | Text-MT | Text Avg | MM-SS | MM-MS | MM-MT | MM Avg |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| GPT-6-Astra | 96.0 | 82.8 | 70.6 | 80.3 | 70.0 | 94.2 | 67.6 | 78.0 |
| GPT-6.1-Sol | 96.1 | 84.0 | 71.3 | 81.2 | 70.0 | 92.3 | 62.9 | 75.7 |
| Claude-Opus-5.5 | 99.2 | 84.4 | 65.0 | 79.6 | 75.0 | 92.3 | 53.2 | 73.7 |
| Claude-Opus-4.8 | 98.8 | 78.1 | 65.3 | 76.3 | 85.0 | 69.2 | 61.8 | 71.1 |
| Kimi-K3 | 95.3 | 82.9 | 64.0 | 78.0 | 80.0 | 69.2 | 54.1 | 66.9 |
| MiMo-V2.6-Pro | 91.5 | 82.9 | 63.6 | 77.4 | 85.0 | 69.2 | 50.4 | 67.0 |
| GPT-5.5 | 94.1 | 83.6 | 59.8 | 76.8 | 90.0 | 75.0 | 42.4 | 67.7 |
| Claude-Opus-4.6 | 91.5 | 83.4 | 58.3 | 75.9 | 75.0 | 76.2 | 48.1 | 65.9 |
| Qwen3.8-Max | 89.7 | 82.6 | 65.0 | 77.5 | 80.0 | 61.5 | 48.4 | 62.1 |
| Gemini-3.1-Pro | 96.4 | 80.7 | 56.1 | 74.3 | 85.0 | 88.5 | 32.7 | 67.9 |
| Qwen3.6-27B *(best local)* | 84.9 | 72.1 | 37.2 | 61.8 | 75.0 | 55.8 | 38.5 | 55.1 |

**No model dominates all six workload groups:** Claude-Opus-5.5 leads Text-SS (99.2) and Text-MS (84.4); GPT-6.1-Sol leads Text-MT (71.3); GPT-5.5 leads MM-SS (90.0); GPT-6-Astra leads MM-MS (94.2) and MM-MT (67.6).

### Evidence-based audit

LLM judges can award credit that the execution evidence does not support. OmniStepBench applies deterministic post-hoc
rules to every score that involves the primary judge (Qwen3.5-VL-Plus) and routes flagged cases to a meta-judge from a
different model family (Claude-Opus-4.6). Of 9,218 model&ndash;task runs, 4,096 are judge/hybrid calls; 182 were flagged and
**143 unsupported positive scores were removed**. Against human experts (100 stratified
trajectories from a 3,340-call validation pool), the mean absolute error drops from 0.098 (primary judge) to 0.049 (after the meta-judge).

| Pattern | Local | API | Total |
| --- | ---: | ---: | ---: |
| Deadlock loop | 86 | 0 | 86 |
| Rubric leakage | 12 | 14 | 26 |
| Pseudo-tool-call credulity | 20 | 0 | 20 |
| Output instability | 5 | 2 | 7 |
| Timeout-with-credit | 1 | 3 | 4 |
| **Total** | **124** | **19** | **143** |

## Code

```text
tasks/      233 task files: YAML frontmatter, prompt, automated checks, LLM-judge rubric
assets/     Workspace fixtures copied into the agent workspace for each task
scripts/    Benchmark runner, OpenClaw and basemodel executors, grading, result aggregation
logs/       Run logs and result files
docs/       Project page (served by GitHub Pages)
```

## Quick Start

> **Step-by-step guide:** [RUN_BENCHMARK.md](RUN_BENCHMARK.md) has the up-to-date setup (pinned OpenClaw version, ClawHub skill owners, judge, smoke test, paper-style report). The steps below are the original quick start.

### Step 1: Install OpenClaw and required skills

```bash
# Install OpenClaw
curl -fsSL https://openclaw.ai/install.sh | bash

# Install skills from Clawhub
clawhub install self-improving-agent
clawhub install summarize
clawhub install gog
clawhub install proactive-agent
clawhub install skill-vetter
clawhub install humanizer
clawhub install github
clawhub install multi-search-engine
clawhub install ontology
clawhub install agent-browser-clawdbot
clawhub install desktop-control

# Configure your models (providers, API keys, etc.)
openclaw onboard
```

### Step 2: Run the benchmark

**Requirements**

- Python 3.10+
- [uv](https://docs.astral.sh/uv/) package manager
- A running OpenClaw instance (when using the `openclaw` executor)

**2.1 Clone this repository**

```bash
git clone https://github.com/SeerRay-Lab/OmniStepBench.git
cd OmniStepBench
```

**2.2 Configure the judge model**

LLM-judged tasks use a separate model. Edit `scripts/lib_grading.py` and set `DEFAULT_JUDGE_MODEL` to a provider/model your OpenClaw setup can run, for example:

```python
DEFAULT_JUDGE_MODEL = "PROVIDER_NAME/MODEL_NAME"
```

**2.3 Launch runs**

- **Parallel (multiple models)** — edit the `MODELS=( ... )` array in `scripts/run_parallel.sh`, then:

  ```bash
  ./scripts/run_parallel.sh
  ```

  Keep concurrent models modest (about **5 or fewer**) to reduce flaky failures from rate limits or resource contention. Extra `benchmark.py` flags can be appended; they are forwarded to every worker.


- **Serial (multiple models, one after another)** — same `MODELS=( ... )` idea in `scripts/run_serial.sh`:

  ```bash
  ./scripts/run_serial.sh
  ```

- **Single model (direct)** — no need to edit the parallel scripts:

  ```bash
  ./scripts/run.sh --model PROVIDER_NAME/MODEL_NAME
  ```

## Command reference
| Flag | Description |
|------|-------------|
| `--model MODEL` | Model under test (e.g. `openrouter/anthropic/claude-sonnet-4.6`). Required for `./scripts/run.sh`; parallel/serial scripts set this per entry in `MODELS`. |
| `--suite SUITE` | `all` (default), `automated-only`, or comma-separated task IDs |
| `--runs N` | Number of runs per task for averaging (default: `1`) |
| `--timeout-multiplier N` | Multiplier for all task timeouts (default: `1.0`) |
| `--output-dir DIR` | Where to write results (default: `results`) |
| `--session-backup-dir DIR` | Directory for session transcript backups (parallel scripts set this under each run’s log folder) |
| `--executor EXEC` | `openclaw` or `basemodel` (default: `openclaw`) |
| `--verbose`, `-v` | Verbose logging (transcripts, workspace detail, etc.) |

## Citation

```bibtex
@article{liu2026omnistepbench,
  title   = {OmniStepBench: Deployment-Aware Agent Evaluation across Modalities and Task Complexity},
  author  = {Liu, Yu and Liu, Zhilin and Yang, Zhiwei and Zhang, Shaojie and Deng, Zheyuan and Huang, Tingwei and Luo, Zhenbo and Jiang, Lei and Liu, Yanbing and Fu, Pei},
  journal = {arXiv preprint arXiv:2609.06059},
  year    = {2026}
}
```

## License

- **Code and OmniStepBench's own additions** (benchmark runner, task wrappers, grading code, rubrics, project page): [Apache License 2.0](LICENSE). The benchmark runner is derived from [PinchBench](https://github.com/pinchbench/skill) (MIT License); see [NOTICE](NOTICE).
- **Tasks and workspace files keep the licence of their source benchmark** (`tasks/`, `assets/`), including attribution, non-commercial and share-alike terms:

| Source benchmark | Tasks | Licence | Terms to note |
| --- | ---: | --- | --- |
| [LogiQA](https://github.com/lgw863/LogiQA-dataset) | 10 | Not specified (none declared) | No licence declared by the authors |
| [GPQA](https://huggingface.co/datasets/Idavidrein/gpqa) | 10 | CC-BY-4.0 | Gated upstream; asks not to reveal examples online; canary |
| [AdvancedIF](https://huggingface.co/datasets/facebook/AdvancedIF) | 10 | CC-BY-NC-4.0 | **Non-commercial** (NC) |
| [Bamboogle](https://github.com/ofirpress/self-ask) | 10 | MIT | — |
| [SimpleQA](https://github.com/openai/simple-evals) | 10 | MIT | Licence of the simple-evals repository |
| [LongBench](https://huggingface.co/datasets/zai-org/LongBench-v2) | 10 | Apache-2.0 | — |
| [LexEval](https://github.com/CSHaitao/LexEval) | 20 | MIT | — |
| [TableBench](https://huggingface.co/datasets/Multilingual-Multimodal-NLP/TableBench) | 17 | Apache-2.0 | — |
| [FinQA](https://github.com/czyssrs/FinQA) | 10 | MIT | Repo MIT; IBM's Hub copy is CC BY 4.0 |
| [DeepSearchQA](https://huggingface.co/datasets/google/deepsearchqa) | 10 | Apache-2.0 | — |
| [WideSearch](https://huggingface.co/datasets/ByteDance-Seed/WideSearch) | 10 | CC0-1.0 | CC0 per the dataset's LICENSE file (card says 'other') |
| [Seal0](https://huggingface.co/datasets/vtllms/sealqa) | 10 | Apache-2.0 | Canary |
| [TerminalBench2](https://github.com/harbor-framework/terminal-bench-2) | 10 | Apache-2.0 | Canary; fixtures may embed third-party files |
| [OpenAgentSafety](https://github.com/Open-Agent-Safety/OpenAgentSafety) | 6 | MIT | Licence of the repository |
| [OSWorld](https://github.com/xlang-ai/OSWorld) | 9 | Apache-2.0 | Some fixtures are third-party photos |
| [SimpleVQA](https://huggingface.co/datasets/m-a-p/SimpleVQA) | 10 | Apache-2.0 | — |
| [HLE](https://huggingface.co/datasets/cais/hle) | 10 | MIT | Gated upstream; canary |
| [CharXiv](https://huggingface.co/datasets/princeton-nlp/CharXiv) | 10 | CC-BY-SA-4.0 | **Share-alike** (SA); chart images © original arXiv authors |
| [MedXpertQA](https://huggingface.co/datasets/TsinghuaC3I/MedXpertQA) | 16 | MIT | — |
| [AgentVista](https://huggingface.co/datasets/Warrieryes/AgentVista) | 10 | CC-BY-4.0 | — |
| [MMSearch](https://huggingface.co/datasets/CaraJ/MMSearch) | 10 | MIT | — |
| [MMSearchPlus](https://huggingface.co/datasets/Cie1/MMSearch-Plus) | 5 | CC-BY-4.0 | Encrypted upstream to prevent contamination |

- **Non-commercial:** AdvancedIF is CC BY-NC 4.0 — its tasks may not be used commercially.
- **Share-alike:** CharXiv questions are CC BY-SA 4.0; the chart images remain with the original arXiv authors.
- **No licence declared:** LogiQA — included for non-commercial research evaluation only; rights holders can request removal via an issue.
- **Evaluation only:** do not train on these tasks. GPQA and HLE are gated upstream and carry canaries, SealQA and Terminal-Bench publish canaries, and MMSearch-Plus is distributed encrypted upstream.

Full details and the evidence for every licence: [DATA_LICENSES.md](DATA_LICENSES.md) (also on the Hub as [LICENSE.md](https://huggingface.co/datasets/SeerRay-Lab/OmniStepBench/blob/main/LICENSE.md)).

## Acknowledgements

OmniStepBench runs on [OpenClaw](https://openclaw.ai) and adapts tasks from 22 public benchmarks (paper Table 9);
we thank their authors. The benchmark runner builds on [PinchBench](https://github.com/pinchbench/skill).
