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

`research-repro-flow` 是一个面向 Codex 的交互式技能，用来把机器学习研究目标推进到可执行的复现实验路径。它会先调研近期方法并让你选择要复现的工作，然后再检查开源代码、配置环境、获取数据，并产出可运行的训练和测试脚本。

### 为什么使用

很多复现工作并不是卡在论文阅读，而是卡在从“这个方法看起来不错”到“这条命令真的能跑”之间的细节。这个技能会把这些细节显式化：

- 按代码和数据集覆盖情况筛选近期基线
- 优先选择官方实现或 benchmark 维护的实现
- 分别推荐最受欢迎、精度最高和速度最快的候选工作
- 对“情绪分类”这类多义任务，先确认是文本、语音、表情、多模态还是对话情绪识别
- 等待你输入方法编号后再进入代码检查和复现阶段
- 如果第一阶段方向不对，你可以直接纠正范围，它会重新调研
- 区分“调研已完成”和“执行被数据或代码阻塞”
- 当数据需要登录、付费或人工审批时明确停止并说明步骤
- 产出复现交接所需的训练脚本、测试脚本、命令、产物和指标

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
$research-repro-flow 我要做目标检测任务，请调研近两年的方法，列一个表格，推荐最受欢迎、精度最高、速度最快的三个工作，然后让我选择一个复现。
```

```text
$research-repro-flow 我要做多模态情绪识别任务，请调研近两年的方法，推荐最受欢迎、精度最高、速度最快的三个工作，然后让我选择一个复现。
```

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

1. 明确任务类型、模态、benchmark 和用户约束；任务多义时先提问澄清。
2. 默认调研近两年方法，除非你指定其他时间范围。
3. 搜索论文、leaderboard、官方仓库、benchmark 仓库和实现索引。
4. 构建带编号的方法表，包含方法、年份、会议、论文、指标、速度、热度、代码和数据集。
5. 推荐三个候选：最受欢迎、精度最高、速度最快。
6. 暂停并等待你输入方法编号。
7. 根据你选择的方法检查是否有官方或可靠开源实现。
8. 如果有代码，优先适配开源实现；如果没有代码，则根据论文复现。
9. 下载可公开获取的数据，配置最小环境，并提供完整训练和测试脚本。
10. 在条件允许时运行最短可信的训练或评估冒烟命令。

### 输出形式

调研阶段会先输出可选择的方法表和三类推荐：

| ID | 方法 | 年份 | 会议 | 论文 | Benchmark/指标 | 速度 | 热度信号 | 代码 | 数据集 | 备注 |
|---:|---|---:|---|---|---|---|---|---|---|---|
| 1 | ExampleDet | 2026 | Example | Link | COCO AP | 120 FPS | 高 stars/引用 | 官方实现 | COCO | 速度强 |

| 推荐类型 | ID | 方法 | 理由 |
|---|---:|---|---|
| 最受欢迎 |  |  |  |
| 精度最高 |  |  |  |
| 速度最快 |  |  |  |

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

`research-repro-flow` is an interactive Codex skill for turning an ML research goal into a practical reproduction path. It first surveys recent methods and asks you to choose one, then checks code availability, sets up the environment, obtains data, and produces runnable train/test scripts.

### Why Use It

Research reproduction usually fails in the gaps between "this paper looks good" and "this command runs." This skill makes those gaps explicit:

- shortlist recent baselines with repo and dataset coverage
- prefer official or benchmark-maintained implementations
- recommend the most popular, highest-accuracy, and fastest candidates
- clarify ambiguous tasks, such as text/speech/facial/multimodal emotion recognition
- wait for your numeric method selection before moving into reproduction
- restart the research phase if you correct the scope after the first table
- separate research completion from execution blockers
- stop cleanly when data requires login, payment, or manual approval
- produce the scripts, commands, artifacts, and metrics needed for a reproducible handoff

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
$research-repro-flow I want to work on object detection. Survey methods from the last two years, list them in a table, recommend the most popular, highest-accuracy, and fastest works, then let me choose one to reproduce.
```

```text
$research-repro-flow I want to work on multimodal emotion recognition. Survey methods from the last two years, recommend the most popular, highest-accuracy, and fastest works, then let me choose one to reproduce.
```

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

1. Identify the task family, modality, benchmark, and user constraints; ask a clarification question when the task is ambiguous.
2. Default to methods from the last two years unless you specify another time window.
3. Search papers, leaderboards, official repositories, benchmark repositories, and implementation indexes.
4. Build a numbered method table with method, year, venue, paper, metric, speed, popularity, code, and datasets.
5. Recommend three candidates: most popular, highest accuracy, and fastest.
6. Pause and wait for your method ID.
7. Check whether the selected method has official or reliable open-source code.
8. If code exists, adapt it; if not, reproduce the method from the paper.
9. Download public data, configure a minimal environment, and provide complete train/test scripts.
10. Run the shortest credible smoke train/eval command when compute and data allow.

### Output Shape

The research phase first produces a selectable method table and three recommendations:

| ID | Method | Year | Venue | Paper | Benchmark/metric | Speed | Popularity signal | Code | Datasets | Note |
|---:|---|---:|---|---|---|---|---|---|---|---|
| 1 | ExampleDet | 2026 | Example | Link | COCO AP | 120 FPS | High stars/citations | Official | COCO | Strong speed |

| Choice | ID | Method | Why |
|---|---:|---|---|
| Most popular |  |  |  |
| Highest accuracy |  |  |  |
| Fastest |  |  |  |

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
