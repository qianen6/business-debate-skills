# Business Debate Skills for Cursor

Three AI skills for Cursor IDE that help you **build, challenge, and stress-test business models** using adversarial debate between AI agents.

## What's Inside

### 1. `business-canvas` — Build the Business Model

Interactive Business Model Canvas (BMC) & Value Proposition Canvas (VPC) generator based on [Strategyzer](https://www.strategyzer.com/) methodology.

**Produces:**
- Value Proposition Canvas (Jobs / Pains / Gains + Pain Relievers / Gain Creators)
- Business Model Canvas (9 blocks + competitive analysis + unit economics)
- Test Cards & Learning Cards for hypothesis validation
- Executive Summary

**Methodology:** Alexander Osterwalder's BMC/VPC framework from *Business Model Generation* (2010), *Value Proposition Design* (2014), and *Testing Business Ideas* (2019).

### 2. `office-hours` — Challenge the Assumptions

YC Office Hours diagnostic adapted from [Garry Tan's gstack](https://github.com/garrytan/gstack). Six forcing questions that expose whether your startup idea has real demand or just wishful thinking.

**The Six Questions:**

| # | Question | What It Tests |
|---|----------|---------------|
| Q1 | Demand Reality | Is there REAL evidence someone wants this? |
| Q2 | Status Quo | What are users doing today — even badly? |
| Q3 | Desperate Specificity | Can you name the ACTUAL person who needs this? |
| Q4 | Narrowest Wedge | What's the smallest version someone would pay for? |
| Q5 | Observation | Have you watched someone use this? |
| Q6 | Future-Fit | Does the future make this more essential? |

**Produces:** A diagnostic report with Demand Strength Score (1-10) and one concrete action item.

### 3. `canvas-debate` — Stress-Test via Adversarial Debate

Two AI agents debate your business model: a **YC Partner** (challenger) attacks, a **Business Strategist** (defender) improves. A referee orchestrates the exchange.

```
R0: Strategist reads codebase → generates initial canvas
     ↓
R1: YC Partner sees ONLY canvas → raises 5-7 challenges
     ↓
    Strategist responds + updates canvas
     ↓
R2: YC Partner reviews changes → new challenges
     ↓
    ...continues until no new CRITICAL/SERIOUS challenges...
     ↓
Final: YC Partner gives Robustness Score (1-10)
       Referee generates debate-report.md
```

**Key design:** Each agent only sees the other's *output*, not their *reasoning*. This creates information asymmetry that produces genuinely tough challenges.

**Produces:** Battle-tested canvas files + `debate-report.md` with full debate transcript, convergence analysis, and emergent insights.

## Installation

Copy the skill folders to your Cursor skills directory:

```bash
# macOS / Linux
cp -r business-canvas office-hours canvas-debate ~/.cursor/skills/

# Windows (PowerShell)
Copy-Item -Recurse business-canvas, office-hours, canvas-debate "$env:USERPROFILE\.cursor\skills\"
```

## Usage

In Cursor, the skills activate based on trigger phrases:

| Skill | Trigger Phrases |
|-------|----------------|
| `business-canvas` | "商业模式画布", "business model canvas", "商业建模", "分析商业逻辑" |
| `office-hours` | "office hours", "is this worth building", "创业诊断", "诊断我的项目" |
| `canvas-debate` | "博弈分析", "red team my canvas", "对抗分析", "挑战我的商业模式" |

**Recommended order:**

1. Run `office-hours` first — diagnose demand reality
2. Run `business-canvas` — build structured business model
3. Run `canvas-debate` — stress-test via adversarial debate

## Output Files

All skills output to `docs/business/` in your project:

| File | Source |
|------|--------|
| `office-hours-report.md` | Diagnostic report from office-hours |
| `value-proposition-canvas.md` | VPC from business-canvas |
| `business-model-canvas.md` | BMC from business-canvas |
| `test-cards.md` | Test Cards + Learning Cards |
| `canvas-summary.md` | Executive summary |
| `debate-report.md` | Full debate transcript from canvas-debate |

## Features

- **Bilingual support** — Works in both Chinese and English, matches user's language
- **Codebase-aware** — Reads your actual code to pre-fill canvas blocks
- **Hypothesis validation** — Strategyzer Test Cards with 3-stage testing funnel
- **Fit scoring** — Calibrated 1-10 scoring with clear definitions for each range
- **Environment Map** — Market forces, industry forces, key trends, macro forces
- **Porter's Five Forces** — Quick-check competitive analysis
- **Chinese-English glossary** — 35 business terms with explanations
- **Convergence-based debate** — Debate continues until challenger can't find new critical issues (max 10 rounds)

## Credits

- **Strategyzer methodology**: Alexander Osterwalder, Yves Pigneur, David Bland
- **YC Office Hours framework**: Adapted from [Garry Tan's gstack](https://github.com/garrytan/gstack) `office-hours` skill
- **Paul Graham's essays**: Startup idea validation philosophy

## License

MIT
