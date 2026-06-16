<div align="center">

# Research Repro Flow

Research, shortlist, and reproduce machine learning baselines with Codex.

[![Codex Skill](https://img.shields.io/badge/Codex-skill-111827)](research-repro-flow/SKILL.md)
[![Workflow](https://img.shields.io/badge/workflow-research%20to%20repro-2563eb)](research-repro-flow/references/workflow.md)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

**README 语言 / README Language**

[中文](#中文) | [English](#english)

点击上方链接切换 README 语言。Click the links above to switch README language.

</div>

## 中文

`research-repro-flow` 是一个面向 Codex 的技能，用来把机器学习研究目标推进到可执行的复现实验路径。它会帮助代理搜索近期方法、筛选可信基线、检查开源代码、配置环境、获取数据，并在条件允许时运行最小训练或评估冒烟实验。

### 为什么使用

很多复现工作并不是卡在论文阅读，而是卡在从“这个方法看起来不错”到“这条命令真的能跑”之间的细节。这个技能会把这些细节显式化：

- 按代码和数据集覆盖情况筛选近期基线
- 优先选择官方实现或 benchmark 维护的实现
- 推荐一个默认基线，并给出少量备选方案
- 区分“调研已完成”和“执行被数据或代码阻塞”
- 当数据需要登录、付费或人工审批时明确停止并说明步骤
- 记录复现交接所需的命令、产物和指标

### 快速开始

从本仓库的 `research-repro-flow/` 子目录安装技能：

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo shaopengDaJiDaLi/research-repro-flow \
  --path research-repro-flow
```

也可以从 GitHub URL 安装：

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --url https://github.com/shaopengDaJiDaLi/research-repro-flow/tree/main/research-repro-flow
```

安装后重启 Codex，让新技能生效。

### 使用方式

在 Codex 中直接触发：

```text
$research-repro-flow
```

示例提示词：

```text
$research-repro-flow 找出步态识别任务中最适合复现的强基线，然后帮我复现其中一个。
```

```text
$research-repro-flow 对比遥感变化检测方向近期可开源复现的基线，并推荐一个优先运行。
```

```text
$research-repro-flow 如果代码和数据公开可用，帮我复现当前数据集上最实用的强基线。
```

### 工作流

1. 明确任务类型、benchmark 和用户约束。
2. 搜索近期论文、官方仓库和 benchmark 仓库。
3. 构建紧凑候选表，包含方法、年份、会议、代码状态、数据集和复现备注。
4. 推荐一个默认基线；必要时给出一到两个备选。
5. 根据选中仓库的说明配置最小 conda 环境。
6. 在许可范围内自动下载公开数据。
7. 运行最短但可信的训练或评估冒烟命令。
8. 汇报命令、产物、指标、阻塞点和下一步。

### 输出形式

这个技能倾向于输出小而可执行的决策结果，而不是泛泛的文献综述：

| 排名 | 方法 | 年份 | 会议 | 开源状态 | 仓库 | 数据集 | 推荐理由 |
|---|---|---:|---|---|---|---|---|
| 1 | 默认基线 | 2026 | Example | 官方实现 | Link | 目标 benchmark | 强且适合作为第一选择 |
| 2 | 备选方法 | 2025 | Example | 社区实现 | Link | 相关 benchmark | 适合作为备用或对比 |

### 仓库结构

```text
.
├── README.md
├── RELEASE.md
├── LICENSE
└── research-repro-flow/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── workflow.md
```

### 项目状态

这是一个轻量级 Codex skill，不是 Python 包。核心行为位于 [`research-repro-flow/SKILL.md`](research-repro-flow/SKILL.md)，操作清单位于 [`research-repro-flow/references/workflow.md`](research-repro-flow/references/workflow.md)。

### 许可证

本项目使用 [MIT License](LICENSE)。

## English

`research-repro-flow` is a Codex skill for turning an ML research goal into a practical reproduction path. It helps an agent search recent methods, shortlist credible baselines, inspect open-source code, set up the environment, obtain data, and run a smoke train/eval when possible.

### Why Use It

Research reproduction usually fails in the gaps between "this paper looks good" and "this command runs." This skill makes those gaps explicit:

- shortlist recent baselines with repo and dataset coverage
- prefer official or benchmark-maintained implementations
- choose one default baseline plus a small number of alternates
- separate research completion from execution blockers
- stop cleanly when data requires login, payment, or manual approval
- record the commands, artifacts, and metrics needed for a reproducible handoff

### Quick Start

Install the skill from this repository's `research-repro-flow/` directory:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo shaopengDaJiDaLi/research-repro-flow \
  --path research-repro-flow
```

Or install from a GitHub URL:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --url https://github.com/shaopengDaJiDaLi/research-repro-flow/tree/main/research-repro-flow
```

Restart Codex after installing so the new skill is visible.

### Usage

Trigger the skill directly in Codex:

```text
$research-repro-flow
```

Example prompts:

```text
$research-repro-flow Find the best reproducible baselines for gait recognition, then help me reproduce one of them.
```

```text
$research-repro-flow Compare recent open-source baselines for remote sensing change detection and recommend one to run first.
```

```text
$research-repro-flow Reproduce the strongest practical baseline for my dataset if public code and data are available.
```

### Workflow

1. Identify the task family, benchmark, and user constraints.
2. Search recent papers, official repositories, and benchmark repositories.
3. Build a compact shortlist with method, year, venue, code status, datasets, and reproducibility notes.
4. Recommend one default baseline and, when useful, one or two alternates.
5. Set up a minimal conda environment from the selected repository's instructions.
6. Download public data automatically when allowed.
7. Run the shortest credible smoke train/eval command.
8. Report commands, artifacts, metrics, blockers, and the next action.

### Output Shape

The skill is designed to produce small, decision-ready outputs instead of broad literature surveys:

| Rank | Method | Year | Venue | Open source | Repo | Datasets | Why it matters |
|---|---|---:|---|---|---|---|---|
| 1 | Default baseline | 2026 | Example | Official | Link | Target benchmark | Strong, runnable first choice |
| 2 | Alternate | 2025 | Example | Community | Link | Related benchmark | Useful fallback or comparison |

### Repository Layout

```text
.
├── README.md
├── RELEASE.md
├── LICENSE
└── research-repro-flow/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── workflow.md
```

### Project Status

This is a lightweight Codex skill rather than a Python package. The core behavior lives in [`research-repro-flow/SKILL.md`](research-repro-flow/SKILL.md), with the operational checklist in [`research-repro-flow/references/workflow.md`](research-repro-flow/references/workflow.md).

### License

Released under the [MIT License](LICENSE).
