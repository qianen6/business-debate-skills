# 商业博弈 Skills for Cursor

[English](#english) | 中文

三个 Cursor IDE 的 AI 技能，帮助你**构建、挑战、压力测试商业模式**。

## 核心理念

> 画布不是一次性文档，是需要被攻击才能变强的活体。

传统做法：一个 AI 帮你填画布 → 看起来很完美 → 实际全是未验证的假设。

本工具做法：**一个 AI 构建，另一个 AI 攻击，直到攻击者提不出新问题为止。**

## 包含三个 Skill

### 1. `business-canvas` — 构建商业画布

基于 [Strategyzer](https://www.strategyzer.com/) 方法论的交互式商业画布生成器。

**产出：**
- 价值主张画布（VPC）：客户任务/痛点/收益 + 方案匹配
- 商业模式画布（BMC）：9 个模块 + 竞品分析 + 单位经济
- 验证卡片 & 学习卡片
- 执行摘要

**v1.1 新增：**
- 双分评估（乐观分 vs 现实分）— 区分"假设都成立"和"只看硬证据"
- 单一证伪假设 — 找出最可能推翻整个模型的那一个假设

### 2. `yc-office-hours` — YC 创业诊断

改编自 [Garry Tan 的 gstack](https://github.com/garrytan/gstack)，六个强制性问题戳破需求幻觉。

| # | 问题 | 检验什么 |
|---|------|---------|
| Q1 | 需求真实性 | 有没有人真的想要这个？ |
| Q2 | 现状竞争 | 用户现在用什么凑合？ |
| Q3 | 精确到人 | 你能说出最需要这个的那个人的名字吗？ |
| Q4 | 最小切入点 | 最小的付费版本是什么？ |
| Q5 | 观察与意外 | 你看过真人使用吗？ |
| Q6 | 未来适配 | 3 年后这个东西更重要还是更不重要？ |

**v1.1 新增：**
- Kill Gate（5 分钟快速筛选）— 搜索同赛道死亡公司，避免在死路上浪费博弈
- 死亡公司搜索 — 写入报告
- 双分需求评估（乐观分 vs 现实分）

### 3. `canvas-debate` — 对抗博弈压力测试

两个 AI 智能体对你的商业模式进行对抗博弈：**YC 合伙人（挑战者）** 攻击，**商业建模师（防守者）** 改进。仲裁者编排交换。

```
R0: 建模师读代码库 → 生成初始画布
     ↓
R1: YC 合伙人只看画布 → 提出 5-7 个挑战
     ↓
    建模师回应 + 更新画布
     ↓
R2: YC 合伙人审查修改 → 新挑战
     ↓
    ...持续到提不出新的 CRITICAL/SERIOUS 挑战...
     ↓
最终: YC 合伙人给出稳健性评分 (1-10)
      仲裁者生成 debate-report.md
```

**关键设计：** 每个智能体只能看到对方的*输出*，看不到*推理过程*。信息不对称产生真正尖锐的挑战。

**v1.1 新增：**
- 深度切换（Fast / Thorough / Red Team）
- 张力表 — 显示双方在哪些维度上有分歧
- 少数派报告 — 保留反对方的最强论点
- 归档 INDEX — 多次博弈的纵向追踪

## 安装

### 方式一：ClawHub（推荐）

```bash
clawhub install business-canvas
clawhub install yc-office-hours
clawhub install canvas-debate
```

### 方式二：手动复制

```bash
# macOS / Linux
cp -r business-canvas office-hours canvas-debate ~/.cursor/skills/

# Windows (PowerShell)
Copy-Item -Recurse business-canvas, office-hours, canvas-debate "$env:USERPROFILE\.cursor\skills\"
```

## 使用方法

在 Cursor 中，通过触发词激活：

| Skill | 触发词 |
|-------|-------|
| `business-canvas` | "商业模式画布"、"business model canvas"、"商业建模"、"分析商业逻辑" |
| `yc-office-hours` | "office hours"、"创业诊断"、"诊断我的项目"、"is this worth building" |
| `canvas-debate` | "博弈分析"、"对抗分析"、"挑战我的商业模式"、"red team my canvas" |

**推荐顺序：**

```
1. office-hours → 先诊断需求真伪
2. business-canvas → 再构建结构化画布
3. canvas-debate → 最后压力测试
```

## 输出文件

所有输出到项目的 `docs/business/` 目录：

| 文件 | 来源 |
|------|------|
| `office-hours-report.md` | Kill Gate + 需求诊断报告 |
| `value-proposition-canvas.md` | 价值主张画布 |
| `business-model-canvas.md` | 商业模式画布 |
| `test-cards.md` | 验证卡片 + 学习卡片 |
| `canvas-summary.md` | 执行摘要 |
| `debate-report.md` | 博弈全程记录 + 收敛分析 |
| `debate-index.md` | 多次博弈的纵向追踪 |

## 特性

- **中英双语** — 自动匹配用户语言，框架术语中英对照
- **代码库感知** — 读取实际代码预填画布
- **假设验证** — Strategyzer 验证卡片 + 3 阶段测试漏斗
- **双分评估** — 乐观分/现实分并行，暴露认知差距
- **Kill Gate** — 5 分钟快速筛选，搜索同赛道死亡公司
- **环境地图** — 市场力量、行业力量、关键趋势、宏观力量
- **Porter 五力** — 快速竞争分析
- **中英术语表** — 35 个商业术语解释
- **收敛式博弈** — 持续到挑战者提不出新的 CRITICAL/SERIOUS（最多 10 轮）
- **张力表** — 显示双方的分歧点
- **少数派报告** — 保留反对方最强论点
- **归档追踪** — 多次博弈的纵向对比

## 致谢

- **Strategyzer 方法论**: Alexander Osterwalder, Yves Pigneur, David Bland
- **YC Office Hours**: 改编自 [Garry Tan 的 gstack](https://github.com/garrytan/gstack)
- **竞品借鉴**: [solo-validate](https://clawhub.ai/skills/solo-validate)（Kill Gate、双分评估）、[multi-viewpoint-debates](https://clawhub.ai/skills/multi-viewpoint-debates)（张力表、归档）、[agent-debate](https://clawhub.ai/skills/agent-debate)（少数派报告）

## 许可

MIT

---

<a name="english"></a>

## English

Three AI skills for Cursor IDE: **build, challenge, and stress-test business models** via adversarial debate.

| Skill | What it does |
|-------|-------------|
| `business-canvas` | Strategyzer BMC/VPC generator with dual scoring and falsifying assumptions |
| `yc-office-hours` | YC diagnostic with Kill Gate, dead company search, 6 forcing questions |
| `canvas-debate` | Adversarial debate between AI agents with tension table, minority report, archive |

**Install via ClawHub:**

```bash
clawhub install business-canvas
clawhub install yc-office-hours
clawhub install canvas-debate
```

See Chinese section above for full documentation.
