# Grand Finale 答辩稿 · Model Risk Factory（Challenge 04）

> 用途：2026-11-23 Grand Finale 现场答辩。**6 分钟 presentation + demo，4 分钟 Jury Q&A，到点即停，不加时。**
> 数字口径：一律以 **seed 47 formal run**（`v2-20261112T150753Z-7b6cc549`，冻结提交 `21c3235`）为准，来源是 README 和 `Doc/Overview.pdf`。
> 写法：正文中文；模型、指标、专业术语保留英文；每段的 **English key lines** 可以直接照着讲。

---

## ⚠️ 赛前待办（11/23 之前先处理）

- [ ] **1. 回邮件确认参赛**
  - 发给 monika.rawal@exlservice.com，附上 team leader 的手机号。

- [ ] **2. 决赛用新版 PPT，不要用提交过的旧 PPT（`Doc/solution_deck.pdf`）**
  - 旧 PPT 和其他材料对不上：
    - 第 1、9 页写着 "No formal v3 run exists"，但 seed 47 formal run 已经跑完了。
    - 第 5、6 页用的是旧的 seed 46 数字（6,000 行，AUC 0.7529，TP 621 …），而 `Doc/Overview.pdf` 和 README 用的是 seed 47（1,199 行，AUC 0.699）。
    - 第 8 页写着 `uci_competition_use_approved=false`，但现在的 config 是 `true`。
    - 页脚引用了没有公开的内部文件（`docs/01_比赛背景与官方要求.md`、`docs/v3/...`）。
  - 新版已经做好：[Model_Risk_Factory_Grand_Finale.pptx](Model_Risk_Factory_Grand_Finale.pptx)（和本文件在同一个 `Doc/` 目录）。英文，统一用 seed 47 的数字，9 页正讲 + 4 页附录。每页的备注（speaker notes）里写了讲者、时间和 English key lines，用 PowerPoint 的 Presenter View 就能看到。

    | 页 | 内容 | 讲者 · 时间 |
    | --- | --- | --- |
    | 1 | Title：Model Risk Factory + one-liner + Gate A/B/C | A · 0:00–0:10 |
    | 2 | Problem：~250 models、8–12 weeks、SS1/23，三个痛点 | A · 0:10–0:40 |
    | 3 | How it works：五个阶段 + 三个 gates + 三种角色 + hard boundary | B · 0:40–1:30 |
    | 4 | Demo：4 个页面看什么（然后切到 Streamlit） | B · 1:30–3:20 |
    | 5 | Evidence：parity 截图 + 2.22e-16 / +0.001 / 0.699 | B · 3:20–3:30 |
    | 6 | Responsible AI：Privacy、Security、Fairness、Transparency + Limits | B · 3:30–4:15 |
    | 7 | Why different：对比表 + 四个创新点 | A · 4:15–5:00 |
    | 8 | Feasible & scalable：laptop、340 tests、3.5 min、250 个模型的路径、KPI | A · 5:00–5:35 |
    | 9 | 13/14 PASS + RELEASE: BLOCKED + 结束语 | A · 5:35–6:00 |
    | 10–13 | 附录（只在 Q&A 用）：完整架构图、demo 备用截图、seed 47 数字表 + AUC 图、PRA SS1/23 对照 | Q&A |

  - 还要做：封面加上队名；两人各自用 Presenter View 过一遍备注，把措辞改成自己顺口的说法。

- [ ] **3. 补上占位符**
  - `Doc/Overview.pdf` 里还有 `[Enter Team Name]`、`[Enter Team Leader Email]`，demo video 写着 "Link pending"。
  - 决赛 PPT 封面要写上队名。

- [ ] **4. 确认 demo 电脑上有 seed 47 run 目录**
  - 目录是 `runs/v2-20261112T150753Z-7b6cc549`。kaiwenyao 这台电脑的 `runs/` 里没有，应该在 fangxunwu 的电脑上，demo 就用那台。
  - 用第 4 节的 4 个链接逐页打开测试一遍，再断网测一次。

- [ ] **5. 填上队名和场次**
  - Challenge 04 有两支队：Hivemind 11:05（全场第 1 个）、Big Thigh 11:25（第 3 个）。
  - 填到第 0 节，按场次选对应的讲法。

- [ ] **6. 讲 AUC 置信区间时说明是估算**
  - 0.66–0.74 是 Hanley–McNeil 粗算出来的，仓库里没有这个数。讲的时候说 "roughly" 或 "approximately"。

- [ ] **7. 彩排**
  - 至少完整计时彩排 3 次。超时就先删第 5 段的对比表，只保留四个创新点的一句话版本。
  - 两人互相抽问第 6 节的问题，重点练 Q1、Q2、Q5、Q11、Q21。

---

## 0. 现场信息

| 项 | 内容 |
| --- | --- |
| 日期 / 地点 | 2026-11-23（周一），O'Connor Centre for Learning，**Room L0.17** |
| 到场 | 11:00 开始，**10:45 前到场入座**；到场后联系 EXL 的 Bharti Pareek |
| 我们的场次 | Challenge 04 有两支队：**Hivemind 11:05–11:15（全场第 1 个）**、**Big Thigh 11:25–11:35（第 3 个）**。我们是：`__________` |
| 场次策略 | 如果第 1 个上：评委没有对照，开场 40 秒必须把问题讲清楚。如果第 3 个上：评委刚听完另一支 04 队，要多讲 **differentiation**（第 5 段） |
| 时间 | 6 min 讲 + demo，4 min Q&A。英语语速约 130–140 wpm，6 分钟大约 800 词，含 demo 解说 |
| 着装 / 人员 | 正装；**所有队员必须到场**；每人有明确角色（见第 3 节） |

---

## 1. 核心信息（先背下来）

**One-liner（开场和结尾都用）：**

> "Model Risk Factory lets an AI Agent do the drafting, deterministic code do the checking, and a human sign off at three hash-bound gates — so every claim in a model-risk file can be traced and re-checked."

**三个 headline numbers：**

| 数字 | 含义 |
| --- | --- |
| **2.22e-16** | R vs Python 最大概率差 max \|Δp\|，**1,199 行 formal Holdout**，0 classification mismatches，0 behaviour mismatches |
| **3.5 min** | 合成数据上的完整 Agent pipeline（3 份 inventory + migration + validation + report + export）：29 条 CLI 命令，3.49 min wall clock，0 failed steps |
| **13 / 14** | acceptance checks PASS；release **BLOCKED**，因为系统不会替自己放行（见第 3 节第 7 段） |

**口径红线（台上和 Q&A 都不能越过）：**

- "~250 models / 8–12 weeks / PRA SS1/23" 是 challenge brief 里的 **client context**，不是我们测出来的结果。
- **不说节省了百分之多少时间**。我们只测了 automation time，manual baseline 的配对实测还没做（PENDING）。
- 不说 "fair"、"compliant"、"production-ready"、"validated"。可以说 audit signal、prototype、evidence chain。
- seed 46（6,000 行 Holdout，AUC 0.753）只是 historical run，评委问到才提。
- 数据是 2005 年台湾的 UCI 公开数据，不是 UK portfolio。

---

## 2. 评分维度对照

官方 rubric（pre-screening 和 finale 用同一套），**平分时看 Business Impact**：

| 维度 | 权重 | 评委要看到什么 | 我们的证据 | 讲稿位置 |
| --- | --- | --- | --- | --- |
| **Business Impact** | 30% | 解决 client 的问题，用户受益明确，**有可信的成功衡量方式** | PRA SS1/23 痛点；validator 从"拼证据"变成"判断证据"；pilot KPI 和配对实测方案 | 第 1、6 段 |
| **Technical Approach** | 25% | 数据和 AI 方法合理，用验证或 prototype 证明可行 | Agent + trusted validator + 3 gates；record-by-record parity；mutation test；340 个自动化测试 | 第 2、3 段 |
| **Innovation** | 20% | 方法原创，说清楚比现有方案好在哪 | Unknown 是合法答案；parity proof 不靠 retraining；hash-bound gates；one-time Holdout；release-check 会 BLOCK 自己 | 第 5 段 |
| **Responsible AI** | 15% | privacy、security、bias；局限和 safeguards 讲清楚 | LLM 边界；Docker sandbox；fairness audit + LOW_SAMPLE；局限直接写在报告里 | 第 4 段 |
| **Presentation & Q&A** | 10% | 讲得清楚，主张有证据，答得上问题 | 每个数字能落到 JSON path；Q&A 预案 | 全程 + 第 6 节 |

邮件里列的 7 个关注点（Business Impact / Feasibility / Technical / Responsible AI / Innovation / Presentation & Demo / Jury Q&A）都对应到上表和下面的讲稿。

---

## 3. 6 分钟讲稿

**角色分配（建议，可对调）：**

- **讲者 A = fangxunwu（team leader）**：开场、innovation、scale、诚实状态、结尾。formal run 是 A 操作的，Gate A/B/C 也是 A 审批的，所以 release 状态由 A 讲最有说服力。
- **讲者 B = kaiwenyao**：architecture、demo 操作和解说、Responsible AI。
- 只交接两次（0:40 A→B，4:15 B→A），减少换人耗时。

| # | 时间 | 讲者 | 内容 | 对应维度 | PPT 页 |
| --- | --- | --- | --- | --- | --- |
| 1 | 0:00–0:40 | A | Hook + 问题 | Business Impact | 1–2 |
| 2 | 0:40–1:30 | B | 方案 + 架构 | Technical | 3 |
| 3 | 1:30–3:30 | B | Demo（4 个页面） | Presentation & Demo | 4 → 切到 Streamlit → 5 |
| 4 | 3:30–4:15 | B | Responsible AI | Responsible AI | 6 |
| 5 | 4:15–5:00 | A | 差异化 / Innovation | Innovation | 7 |
| 6 | 5:00–5:35 | A | 可行性、规模、怎么衡量成功 | Business + Feasibility | 8 |
| 7 | 5:35–6:00 | A | 诚实状态 + 结尾 | 为 Q&A 铺垫 | 9 |

### 第 1 段 · Hook + 问题（A，0:00–0:40）

要点：

- 客户：**Tier-1 UK retail bank**，约 250 个 production models（credit、fraud、pricing），用 SAS、R、Python 写成。
- 监管：**PRA SS1/23** 要求每个模型有最新的 documentation 和 independent validation。
- 痛点：文档和代码对不上；一次 validation 要 8–12 周；re-implementation 靠肉眼或"AUC 看起来差不多"来检查；每次 review 都要重新拼证据。
- 用户：model owners、independent validators（second line）、sign-off reviewers。

English key lines：

> "A Tier-1 UK bank runs about 250 production models. Under PRA SS1/23, every one of them needs current documentation and independent validation. Today a single validation takes 8 to 12 weeks — and the documents no longer match the code."
>
> "The hard part is not writing the document. It is proving the document is true."

### 第 2 段 · 方案 + 架构（B，0:40–1:30）

要点（对着 PPT 第 3 页讲；完整架构图在附录第 10 页，留给 Q&A）：

- 五个阶段对应 brief 的建议流程：**Discover → Document → Redevelop → Validate → Monitor**。
- **三种角色严格分开**：
  - **Agent**（LLM，经 OpenAI-compatible gateway，默认 `deepseek-v4.1-flash`，tool-calling，每轮最多 8 次请求）只做三件事：抽取 model inventory、写 Python migration candidate（首次生成 + 最多 2 次 repair）、解释报告。
  - **Deterministic code**：human-written trusted validator、metrics 计算、report 渲染。Agent 写的代码它一行都不 import。
  - **Human**：三个 hash-bound gates。**Gate A** 批 inventory 的 SHA-256；**Gate B** 在 candidate 运行**之前**批它源码的 SHA-256；**Gate C** 批 report manifest 的 SHA-256。src、config 或 candidate 任何一处改动都会让已批准的 gate 失效。
- **Hard boundary**：Holdout 的输入和答案永远不进 Agent context，Agent 只能看到 aggregate metrics。

English key lines：

> "Three roles, strictly separated: the Agent drafts, deterministic code checks, and a human approves. The Agent never computes a metric, and it never sees the Holdout."
>
> "A human approves the exact SHA-256 of each artifact. Change one byte, and the approval is void."

### 第 3 段 · Demo（B，1:30–3:30，共 2 分钟）

开场先说一句 badge：页面左上角是 `UCI · REPLAY`，意思是这是存下来的 formal seed 47 run，不是现场跑的。主动说清楚，比评委自己发现好。

| 页面 | 时长 | 展示什么 | 讲什么 |
| --- | --- | --- | --- |
| **1 · Inventory** | 20 s | 3 个模型：`MDL_CREDIT_V1`（migrate to Python）、`MDL_CREDIT_V2`、`MDL_CREDIT_TREE`（document only），Gate A 都是 APPROVED，sources / conflicts / unknowns 计数 | 三个 legacy R 模型（logistic regression ×2 + `rpart` decision tree），配上故意过时的旧文档 |
| **2 · Model detail** | 30 s | **threshold 冲突**：代码是 0.35，文档写 0.50；每条事实带 file path、line range、excerpt、SHA-256；Owner、Training date = `Unknown` | Agent 可以说 Unknown，但不能悄悄替人选一个答案。冲突保留下来，交给 model owner 判断 |
| **3 · Migration** | 35 s | candidate 源码 + 64-hex hash；Gate B；parity scatter plot：**1,199 行，max \|Δp\| 2.22e-16，0 class mismatches，0 behaviour mismatches** | 不 retrain，直接复用 R 导出的 coefficients、medians、feature order 和 0.35 threshold。candidate 在 Docker 里运行：no network、read-only、non-root、30 s 上限。missing values、imputation flags、rejection codes 也逐行比对。**Mutation test**：把一个系数改 +0.001，validator 能抓到 |
| **4 · Validation report** | 25 s | ROC-AUC 卡片（dev 0.746 / holdout 0.699 / shifted 0.763）、calibration deciles、confusion matrix @0.35、PSI 柱状图、fairness TPR/FPR 点图、Gate C | 数字全部由 Python 计算，每个都能落到 `validation_metrics.json` 的一个 path。Gate C 重新渲染报告，逐格核对表格 |

Demo 结束后切回 PPT 第 5 页，用 10 秒收尾：parity 完全一致、validator 能抓到 0.001 的改动、AUC 如实报告，然后进入第 4 段。

English key lines：

> "2.2e-16 is float64 machine precision. R and Python agree to the last bit, on every one of 1,199 unseen records."
>
> "To prove the checker is not a rubber stamp, we shift one coefficient by 0.001. The validator catches it."
>
> "Every number in this report is computed by Python and resolves to a JSON path. The Agent explains. It never writes a number."

### 第 4 段 · Responsible AI（B，3:30–4:15）

要点：

- **Privacy**：只有 R code、模拟的旧文档、JSON schemas 和 aggregate diagnostics 会发给 LLM。原始行、client ID、labels、Holdout 都留在本机。API key 只放在本地环境变量里。导出的 evidence ZIP 走白名单，不含任何数据行。
- **Security**：LLM 生成的代码按 untrusted 处理。先过 Gate B 的 hash 审批，再在 Docker 里跑：`--network none`、non-root（UID 65532）、read-only root 和 inputs、512 MB、1 CPU、64 PIDs、30 s timeout。candidate 看不到 tests，也看不到 baseline answers。
- **Fairness**：age、sex 不进模型输入，只用于审计。按 age band 和 sex 报告 TPR/FPR，和 reference group 比较。少于 30 行的组标 `LOW_SAMPLE`，相关类别少于 5 条记录的 rate 标为不可评估。这些是 **audit signals**，不是 fairness verdict。
- **Transparency & accountability**：每条事实都有 citation；每个数字都能落到 JSON path；有 agent audit log、request log；记录真实 reviewer 身份，agent-delegated review 单独标注。
- **Limitations**：报告里直接写明：2005 年台湾公开数据，不是 UK portfolio；Holdout 和训练数据同期，不是 back-test；没有 out-of-time 数据；这是 prototype，没有独立验证，也不是监管认证。

English key lines：

> "We treat the LLM's code as untrusted. It runs only after a human approves its exact hash, inside a container with no network."
>
> "Age and sex never enter the model. We use them only to audit outcomes — and we report them as signals, not verdicts."

### 第 5 段 · Innovation / 差异化（A，4:15–5:00）

| 现有做法 | 问题 | 我们 |
| --- | --- | --- |
| Manual validation | 8–12 周，文档和代码脱节 | Agent 起草，validator 拿到的是现成证据 |
| 直接让 GenAI copilot "把 R 转成 Python" | 写得流畅，但没法验证，也没有 audit trail | 逐行 parity proof + behaviour fixtures + mutation test |
| MLOps 平台（MLflow / Azure ML） | 擅长跟踪新模型，不会 reverse-engineer legacy 资产，也不证明 parity | 补上这一层；MLflow / Azure ML 可以作为 evidence sink |

四个创新点：

1. **"Unknown" 是合法答案**：没有来源的字段保持 Unknown；代码和文档的冲突（0.35 vs 0.50）保留下来，不自动"修正"。
2. **Parity proof，不 retrain**：behavioural equivalence 逐行证明，mutation test 证明 validator 真的敏感。
3. **Hash-bound human gates**：审批绑定确切 artifact，任何改动都要重新审批。
4. **One-time Holdout + release-check**：Holdout 只能消费一次，记入 consumption ledger；release-check 会拒绝和发布提交不匹配的证据，也会 BLOCK 我们自己。

English key lines：

> "Other tools give you code. We give you evidence."
>
> "Our Agent is allowed to say 'I don't know'. In model risk, an honest Unknown is worth more than a confident guess."

### 第 6 段 · 可行性、规模、怎么衡量成功（A，5:00–5:35）

要点：

- **今天就能跑**：一台 laptop，Python + R（`rocker/r-ver:4.4.2` 容器）+ Docker + Streamlit；成本基本只有 LLM tokens；单一 CLI 入口，UI 的每个按钮也调同一个 CLI，绕不过 gate；340 个自动化测试。
- **速度**：合成 run 端到端 3.5 min；Agent 阶段 inventory 每个模型 13–40 s，candidate 66 s，report summary 10 s。
- **扩到 250 个模型**：同样的 gates、同样的 validator、每个模型一份 context、每个 campaign 一个 Holdout。这是排队问题，不需要重新设计。瓶颈是人工 review 时间，这是有意设计的（SS1/23 要求 independent review），但 reviewer 的时间从"拼证据"变成了"判断证据"。
- **Model-agnostic gateway**：换成银行批准的 endpoint（比如银行 tenant 里的 Azure OpenAI）只要改 config。
- **怎么衡量成功**（Business Impact 要求 "a credible way to measure success"）：我们没有宣称节省了多少百分比。pilot 的 KPI：每次 validation 的 elapsed time（对照 8–12 周）、每个 gate 的 reviewer hours、带 citation 的字段比例、first-pass parity rate、发现的 doc-code conflicts 数量。配对实测方案已经设计好（manual vs Agent + human）。

English key lines：

> "Scaling to 250 models is a queue problem, not a redesign."
>
> "We did not claim a percentage saving we have not measured. Our pilot measures elapsed time per validation against today's 8 to 12 weeks."

### 第 7 段 · 诚实状态 + 结尾（A，5:35–6:00）

要点：

- 14 项 acceptance checks 中 13 项 PASS。
- V1-07 FAIL 的原因：Docker 中途崩溃后，我们按 SOP 走了一次经批准的 repair，但我们自己的 command-chain checker 把这次合法 repair 误判成违规（defect D-01）。
- 修复已经做了，也加了 regression tests，但**只对之后的 run 生效**。看到结果再改规则，正是 model risk management 禁止的事。
- UCI 数据已经没有没用过的行来做第二次诚实的 Holdout，所以 release 是 **BLOCKED**，没有打 `v3` tag。

English key lines：

> "Thirteen of fourteen checks passed. The fourteenth failed because of a bug in our own checker. We fixed it for future runs — but we did not re-grade our own exam. So our release is BLOCKED, and we think that is exactly what a model-risk system should do."
>
> "Agent drafts. Code checks. Humans decide. Thank you."

---

## 4. Demo 方案

**主方案：Streamlit REPLAY formal run（不现场跑 LLM 或 Docker）**

- 理由：现场 Wi-Fi、LLM gateway、Docker 任何一个出问题，6 分钟就没了；而且 formal Holdout 已经用过，不能再消费一次。
- 用 **有 seed 47 run 目录的那台电脑**（`runs/v2-20261112T150753Z-7b6cc549`，不进 Git；**本机 `runs/` 里没有这个目录**，应该在 fangxunwu 的电脑上）。
- 进场前启动：

```bash
streamlit run app.py
```

- 提前开好 4 个 tab，demo 时只切 tab，不在侧栏里点来点去：

```text
http://localhost:8501/?root=runs&run=v2-20261112T150753Z-7b6cc549&page=1
http://localhost:8501/?root=runs&run=v2-20261112T150753Z-7b6cc549&page=2
http://localhost:8501/?root=runs&run=v2-20261112T150753Z-7b6cc549&page=3
http://localhost:8501/?root=runs&run=v2-20261112T150753Z-7b6cc549&page=4
```

- 投影前把浏览器放大到 125–150%，关闭通知，提前测试 HDMI / USB-C 转接和镜像显示。

**备用方案：**

1. `Doc/demo_video.mp4`（1:51，英文旁白 + 字幕，synthetic replay）放在本地，不依赖网络。
2. PPT 附录第 11 页（Inventory、Model detail 摘要、Validation report 截图）加第 5 页（Migration 的 parity 截图）。放映时输入页码再按 Enter 就能直接跳过去。

**失败处理：** Streamlit 10 秒没反应就直接切到 PPT 第 11 页或视频，台上不 debug。可以说："In the interest of time, here are the same screens from the recorded run."

**如果评委问 "Can it run live?"：** "Yes. The deterministic pipeline runs with no API key in about 5 minutes — README Demo A. We replay the formal run here because its Holdout can only be used once."

---

## 5. 关键数字速查表（seed 47 formal run）

| 类别 | 指标 | 数值 |
| --- | --- | --- |
| 数据 | Dataset | UCI Default of Credit Card Clients（ID 350），CC BY 4.0，2005 Taiwan，30,000 行 |
| 数据 | Split | train 15,000 / dev 6,000 / **holdout 1,199** / shift_pool 3,000；另有 4,801 行不使用 |
| 数据 | Holdout default rate | 264 / 1,199 = 22% |
| 模型 | `MDL_CREDIT_V1` | logistic regression，4 个 features：`delay_1`、`log_limit`、`util_1`、`log_pay_1`；threshold **0.35**（文档写 0.50） |
| 模型 | `MDL_CREDIT_V2` | logistic regression，7 个 features，threshold 0.30，document only |
| 模型 | `MDL_CREDIT_TREE` | `rpart` decision tree，maxdepth 3，threshold 0.50，document only |
| Parity | dev（6,000 行） | max \|Δp\| 2.78e-16 |
| Parity | **holdout（1,199 行）** | **max \|Δp\| 2.22e-16**；classification / behaviour mismatches = 0 |
| Parity | Tolerance | max 1e-8，mean 1e-10 |
| Parity | Mutation test | `delay_1` 系数 +0.001 → 被检测出来（status PASS 的意思是"错误被抓到了"） |
| Performance | ROC-AUC / Brier | dev 0.7461 / 0.1405；**holdout 0.6988 / 0.1506**；shifted 0.7634 / 0.1432 |
| Performance | Confusion matrix（holdout @0.35） | TP 95、FN 169、FP 95、TN 840 → recall 0.36、precision 0.50、accuracy 0.78、FPR 0.10 |
| Performance | Holdout AUC 95% CI（自己估算，仓库里没有） | Hanley–McNeil 约 **0.66–0.74**（SE ≈ 0.02） |
| Stability | PSI（dev vs shifted scenario A） | 6 项全部 OK；最大 `util_1` 0.0611；prediction 0.0187；阈值 attention 0.10 / review 0.25（项目 demo 规则，不是监管标准） |
| Stability | Shift scenario | weighted resample，2,000 行，`util_weight` 2.0，`limit_weight` 1.5 |
| Fairness | Reference groups | age 26–35，sex=2 |
| Fairness | age 21–25 TPR | 0.474 vs reference 0.340（age 51+ 只有 83 行） |
| Fairness | sex=1 TPR | 0.340 vs reference 0.372 |
| Fairness | Small-sample rules | < 30 labelled rows → `LOW_SAMPLE`；相关类别 < 5 条 → rate 不可评估 |
| Agent | Gateway / model | OpenAI-compatible，默认 `deepseek-v4.1-flash:1017`（v1 candidate 用的是 `kimi-k2.7-code`） |
| Agent | Tools | `read_asset`、`validate_inventory`、`submit_candidate`、`run_dev_tests`、`read_dev_diagnostics` |
| Agent | 限制 | 每轮最多 8 次请求；candidate 首次生成 + 最多 2 次 repair；看不到 Holdout、tests、数据行 |
| Sandbox | Docker runner | `--network none`、non-root 65532、read-only、512 MB、1 CPU、64 PIDs、30 s |
| Speed | 合成 run 端到端 | 29 条命令，200.5 s command time，3.49 min wall clock，0 failed |
| Speed | Agent 阶段 | inventory 12.7 / 31.6 / 40.3 s，candidate 66.1 s，report summary 9.8 s |
| Quality | Tests | 340 passed，0 skipped（最终提交 `469c94c`；没有 UCI ZIP 时会跳过 8 个） |
| Quality | Report 追溯 | 合成 run 196 个 report values，0 unresolved |
| Release | Acceptance | 13 / 14 PASS；V1-07 FAIL（D-01）；release-check BLOCKED；没有 `v3` tag |
| Release | 历史 | v1 released（7/7 PASS）；v2 BLOCKED（证据在 dirty worktree 上生成，release-check 列出 17 条 gaps） |

---

## 6. Q&A 预案（4 分钟）

**规则：**

- 4 分钟大约 4–6 个问题，每个回答 **≤ 30 秒**：先给结论，再给一个证据，然后停。
- 分工：技术类（Agent、parity、sandbox、metrics）→ **B**；业务、Responsible AI、状态、roadmap → **A**。另一个人不插话，除非对方卡住。
- 不会的问题："That's a fair point. We haven't tested that — here is how we would." 不要编数字。
- 需要时翻 PPT 附录：第 10 页架构图（Q11–Q17）、第 12 页数字表和 AUC 图（Q2、Q6、Q18）、第 13 页 SS1/23 对照（Q23）。

### A. 状态与局限（最可能被追问）

**Q1. "Your release is BLOCKED. So does it actually work?"**
- 要点：pipeline 端到端在真实 UCI 数据上跑完了；13/14 PASS；唯一的 FAIL 来自 checker 自己的 bug，不是模型或迁移的问题；事后改判就等于自己给自己的考试重新打分。
- English：*"Yes, it works end to end on real data — 13 of 14 checks passed and parity is exact. The one failure is a bug in our own checker. We could have re-graded the run after fixing it. We chose not to, because that is exactly what a model-risk process must never allow."*

**Q2. "Holdout AUC is 0.699 — isn't that weak?"**
- 要点：这是 **legacy model** 本身的表现（4 个 features 的 logistic regression），我们的任务是忠实迁移和如实验证，不是提升模型；Holdout 只有 1,199 行（264 个违约），95% CI 大约 0.66–0.74；之前 6,000 行的 run 是 0.753；报告如实给出数字，不美化。
- English：*"That is the legacy model's performance, not our migration's — we reproduce it exactly, and our job is to report it honestly. The Holdout is small, so the interval is roughly ±0.04; an earlier 6,000-row run gave 0.75. A real validator would flag this for monitoring, and our report surfaces it rather than hiding it."*

**Q3. "Why only 1,199 Holdout rows?"**
- 要点：规则是任何被之前 formal Holdout 用过的行都不再用；之前每次 formal run 各用掉一次 Holdout；30,000 行排除之后只剩 1,199 行干净的；代价是 CI 变宽，但换来不泄漏。
- English：*"Each formal Holdout can be used once, and we never reuse a row a previous Holdout saw. That left 1,199 clean rows. We traded a wider interval for zero leakage."*

**Q4. "No back-testing? The brief asked for it."**
- 要点：UCI 是单一时间点的快照（2005 年 4–9 月的还款记录，10 月是否违约），没有 out-of-time 数据；报告里列为 missing evidence；drift 用 weighted resample 做 sensitivity analysis；拿到银行的 vintage 数据就能做 back-test，validator 不用改。
- English：*"This dataset is a single 2005 snapshot, so a genuine out-of-time back-test is impossible. We list it as missing evidence instead of faking it, and we run drift as a sensitivity analysis. With bank vintage data, the same validator back-tests without changes."*

**Q5. "Who was the independent reviewer? The same person ran and approved it?"**
- 要点：如实说，competition run 是单人操作，由 fangxunwu 执行并审批，仓库里有披露；系统记录 reviewer 身份，并单独标注 agent-delegated review；生产环境必须做 separation of duties（RBAC：operator ≠ approver，four-eyes），这在 roadmap 里。
- English：*"In the competition run, one team member operated and approved, and we disclosed that. The system records who approved each hash. In production we would enforce separation of duties — the operator can never be the approver."*

### B. 模型与指标

**Q6. "What does 2.2e-16 actually mean?"**
- 要点：2.22e-16 = 2⁻⁵²，float64 的 machine epsilon，等于两边只差浮点舍入；tolerance 是 1e-8；只比概率不够，所以 classification、missing value 处理、imputation flags、rejection codes 也逐行比。
- English：*"It's float64 machine epsilon — the two implementations differ only by rounding. And we compare behaviour too: missing values, imputation flags and rejection codes, record by record."*

**Q7. "How do you know the validator isn't just passing everything?"**
- 要点：mutation test，把 `delay_1` 系数改 +0.001 会被抓到；validator 是人写的，从不 import 生成的代码，只比较容器的输出；还有 row-order、column-order 和结构性拒绝的 fixtures。
- English：*"We attack it. We shift one coefficient by 0.001 and the validator fails it. The validator is human-written and never imports the Agent's code — it only compares outputs."*

**Q8. "Why not retrain the model in Python?"**
- 要点：retrain 得到的是另一个模型，需要从头做完整 validation，迁移就失去意义；migration 的目标是 behavioural equivalence，所以复用 R 导出的 coefficients、medians、feature order 和 threshold。
- English：*"Retraining creates a new model that needs a full re-validation. Migration should change the language, not the model — so we prove equivalence instead."*

**Q9. "Why PSI thresholds 0.10 / 0.25?"**
- 要点：业界常用的经验阈值；我们明确标为项目 demo 规则，不是监管标准；可以配置；达到 review 状态应该触发 re-validation。
- English：*"They're common industry rules of thumb, and we label them as project rules, not regulation. They're configurable, and a 'review' state is the trigger for re-validation."*

**Q10. "Does it work for more complex models — GBMs, neural nets?"**
- 要点：tree model 已经做了 documentation，还没有迁移；确定性模型（tree、GBM 的 scoring）可以用同样的 parity 方法；不能逐位复现的模型改用统计等价检验加 behaviour tests；gate 和证据链不用变。
- English：*"For any deterministic scorer, the same record-by-record parity applies. Where bit-exact reproduction isn't possible, we'd switch to statistical equivalence tests — the gates and the evidence chain stay the same."*

### C. Agent 与技术

**Q11. "If the coefficients are exported, why do you even need an LLM?"**
- 要点：对一个模型来说确实不难，所以我们选它作为第一个**可证明**的案例；价值在于 factory pattern，250 个模型里大部分时间花在理解代码、写文档、翻译 behaviour 上；Agent 做的是规模化起草，validator 负责证明；迁移通常坏在 edge cases（缺失值、校验、列顺序），我们的 fixtures 专门测这些。
- English：*"For one model, it's easy — that's why we chose it as the first provable case. The value is the factory: across 250 models the Agent does the drafting, and the same fixed validator does the proving. Migrations usually break on edge cases, and that's exactly what our fixtures test."*

**Q12. "How do you stop the Agent from hallucinating the inventory?"**
- 要点：每条事实必须带 file path、line range、excerpt、SHA-256，并且做机械检查：文件 hash 要对得上，excerpt 必须真的出现在那几行里；做 schema validation；允许的 finding 按模型分别设定；没有来源的字段就是 `Unknown`；最后还有 Gate A 人工审批。
- English：*"Every fact must cite a file, a line range, an excerpt and a SHA-256, and we check mechanically that the excerpt really is on those lines. No source, no fact — it stays Unknown."*

**Q13. "Can the Agent write wrong numbers into the report?"**
- 要点：不能；数字和表格全部由 trusted code 渲染；Agent 只选 review focus，返回结构化事实，这些事实必须和 metrics 一致；Gate C 重新渲染报告并逐格核对（合成 run：196 个 values，0 unresolved）。
- English：*"No. Trusted code renders every number and table. The Agent only chooses what to emphasise, and its structured facts must match the metrics. Gate C re-renders and checks every cell."*

**Q14. "Why DeepSeek? Would a bank send code to that model?"**
- 要点：gateway 是 OpenAI-compatible、model-agnostic，换模型只改 config；我们发出去的只有代码、模拟文档和 aggregates，没有客户数据；在银行里会指向银行批准的 endpoint（自有 tenant 里的 Azure OpenAI 或自托管模型）；选它是为了比赛期间的成本和速度。
- English：*"The gateway is model-agnostic — switching is a config change. Even today only code, notes and aggregates leave the host. In a bank we'd point it at a bank-approved endpoint, such as Azure OpenAI in the bank's own tenant."*

**Q15. "What about prompt injection in the legacy code or notes?"**
- 要点：Agent 只有白名单工具，没有 shell 和网络；`read_asset` 拒绝读数据和 test 源码；legacy 资产 read-only；输出经过 schema 和 validator 检查；生成的代码在 sandbox 里跑并经过 Gate B；有专门的 tests（`tests/test_agent_security.py`）。
- English：*"The Agent has an allow-listed toolset — no shell, no network, no access to data or tests. Whatever it outputs is validated, and any code runs only in the sandbox after Gate B."*

**Q16. "Why not Azure ML / MLflow, which the brief prefers?"**
- 要点：15 天里我们优先做可验证的 evidence chain，这正是现有平台缺的部分；MLflow / Azure ML 适合作为 registry 和 evidence sink，在 roadmap 里，用来接住我们的产出，不替代 gates。
- English：*"We prioritised the part existing platforms don't do — proving legacy parity with an audit trail. MLflow or Azure ML would be our evidence sink and registry, not a replacement for the gates."*

**Q17. "What happens when the Agent fails?"**
- 要点：首次生成 + 最多 2 次 repair，repair 只能用 dev 阶段的 FAIL diagnostics；每次 repair 都要重新过 Gate B；还不行就交给人；所有尝试都留在 `command_log.jsonl`，不删除也不改写。
- English：*"It gets an initial attempt plus at most two repairs, using development diagnostics only, and each attempt needs a fresh Gate B approval. After that, a human takes over. Every attempt stays in the log."*

### D. Responsible AI

**Q18. "You removed age and sex — doesn't that make it fair?"**
- 要点：不能，其他变量可能是 proxy（比如 credit limit 和年龄相关），所以要按组审计结果；age 21–25 的 TPR 是 0.474，reference 是 0.340，我们把它作为 signal 提给 model owner 和 compliance 复核，不下结论。
- English：*"No — other variables can act as proxies, which is why we audit outcomes by group. We flag differences like the 21-to-25 age band as signals for the model owner and compliance, not as a verdict."*

**Q19. "Is the UCI data allowed / is it personal data?"**
- 要点：规则允许 "public or synthetic data"，并点名 public credit-risk datasets；UCI 是 CC BY 4.0；没有直接 identifiers，但有 demographic 字段，只用于审计；原始文件不进 Git，下载时校验 SHA-256。
- English：*"The rules allow public credit-risk data. UCI is CC BY 4.0 with no direct identifiers; demographics are used only for auditing, and the raw file never enters the repository."*

**Q20. "How do you prevent rubber-stamping at the gates?"**
- 要点：审批必须针对确切 hash，并写 reviewer 和 comment；UI 会展示要审的内容（source、diff、conflicts）；后续加入 checklist、review 时长统计和 four-eyes。
- English：*"Approval is bound to an exact hash with a named reviewer and comment. Next we'd add review checklists and four-eyes approval for high-materiality models."*

### E. Business & scale

**Q21. "How much time does it save?"**
- 要点：不编数字；已经测到的是 automation 端到端 3.5 min；人工基线还没测，所以不宣称百分比；pilot 用配对实测（同一个任务分别 manual 和 Agent + human），KPI 是 elapsed time per validation 和 reviewer hours per gate。
- English：*"We measured the automation — about 3.5 minutes end to end — but we haven't measured the manual baseline, so we don't claim a percentage. A pilot would pair the same task done manually and with the Agent, and measure elapsed time against today's 8 to 12 weeks."*

**Q22. "How would you roll this out at the bank?"**
- 要点：先选 10 个低复杂度的 R scorecard 做 pilot → 接入 SAS → 用 batch queue 覆盖 250 个模型；按 model materiality 分级 review 强度；换成银行批准的 LLM endpoint；接 MLflow / Azure ML。
- English：*"Start with a pilot of about ten simple R scorecards, measure, then add SAS and a batch queue. Review depth would follow model materiality tier."*

**Q23. "How does this map to PRA SS1/23?"**
- 要点：SS1/23 的 5 个 principles：
  - P1 model identification & risk classification → model inventory
  - P2 governance → 三个 gates + review log
  - P3 development, implementation & use → migration + tests
  - P4 independent validation → validator + report
  - P5 model risk mitigants → drift monitoring + release-check
- English：*"Inventory covers model identification, the gates cover governance, migration and tests cover implementation, the report covers validation, and drift monitoring plus release-check act as mitigants."*

**Q24. "What does it cost to run?"**
- 要点：一台 laptop 加 LLM tokens；每个模型的 Agent 时间大约 1–2 分钟；token 成本没有精确统计，不要报具体金额。
- English：*"A laptop and LLM tokens. Agent time is about one to two minutes per model; most of the cost is human review time, by design."*

### F. Innovation & future

**Q25. "What's different from just asking ChatGPT to convert R to Python?"**
- English：*"ChatGPT gives you code. We give you evidence: cited facts, a record-by-record parity proof, hash-bound approvals, an audit log and a release decision."*

**Q26. "What would you do with three more months?"**
- 要点：(1) 用新数据和 separation of duties 做一次授权的 formal run；(2) SAS ingestion；(3) 250 个模型的 batch queue；(4) MLflow / Azure ML evidence sink；(5) out-of-time back-test；(6) 配对时间实测 pilot。
- English：*"An authorised formal run on fresh data with separate approvers, SAS ingestion, a batch queue for the estate, MLflow as the evidence sink, and a paired time study to prove the business case."*

**Q27. "Which parts were written by AI?"**
- 要点：开发时用了 Claude Code 和 Kimi Code CLI 辅助写代码、测试和文档；产品里的 Agent 写 migration candidate、inventories 和报告叙述；**trusted Python reference predictor 和 fixed tests 由人写**；三个 legacy R 模型和旧文档是我们自己做的测试材料。
- English：*"AI helped us build it, and that's declared. But the trusted reference and the fixed tests — the things that decide pass or fail — are human-written."*

---

## 7. 决赛当天 Checklist

- [ ] 已回邮件确认参赛，并附 team leader 手机号
- [ ] 笔记本充满电，带充电器、HDMI / USB-C 转接头
- [ ] 正装
- [ ] 决赛版 PPT `Doc/Model_Risk_Factory_Grand_Finale.pptx`（本地 + U 盘 + 云端各一份，封面已加队名）
- [ ] GitHub repo 可以打开：github.com/wufangxun106334-pixel/Project_model-risk-factory
- [ ] `Doc/demo_video.mp4` 本地可以播放（备用）
- [ ] Streamlit 已提前启动，4 个 tab 已打开，浏览器已放大
- [ ] Demo 完整测过（断网也能跑 REPLAY）
- [ ] 角色分工明确：A 开场 / innovation / scale / 状态 / 结尾；B 架构 / demo / RAI
- [ ] 所有队员到场（强制）
- [ ] 10:45 前到 O'Connor Centre for Learning L0.17，找 Bharti Pareek（EXL）
