# RCT 临床试验统计编程面试准备

Last updated: 2026-11-09

## 定位与电梯陈述

目标岗位是 **Statistical Programmer / Senior Statistical Programmer**，方向为 RCT，肿瘤优先。差异化有三点：三个淋巴瘤研究的端到端编程经验，数据库锁定时顶住压力交付的经历，以及医学背景（能读懂方案里的临床逻辑）。

| 版本 | 内容 |
| --- | --- |
| 30 秒 | 见下方英文 |
| 2 分钟 | 30 秒版本 + 一个 STAR 故事（下文的「385 个输出」）+ 为什么换到这个岗位 |

> "I'm a statistical programmer with an MD-PhD and a clinical background in neurosurgery. At Tigermed I owned end-to-end programming and QC for three lymphoma studies: SDTM, ADaM, and CSR-ready TLFs, including PFS and OS event and censoring derivations, ORR, DOR, Kaplan–Meier and Cox outputs. On one lymphoma study, a specification discrepancy potentially affected 385 outputs close to a reporting milestone. I helped assess the impact, aligned the correction with the statistician, and ran a controlled rerun with independent QC in parallel; remediation was completed in about three days and the CSR remained on schedule. I also programmed CRS safety tables for an integrated safety summary of a bispecific antibody. My clinical training helps me read a protocol the way the clinical team does, so I catch derivation issues before they reach the tables."

注意：对外只说「a bispecific T-cell engager」，不说化合物名和研究编号。

## 端到端流程

面试官最常问的一句是「walk me through a study」。答案就是下面这条线，每一步都要能说出你的产出和你检查什么。

1. **Protocol 和 SAP**：确认主要及次要终点、分析人群（ITT、mITT、PP、Safety）、分层因素、删失规则。
2. **TLF shell 和编程规格**：和统计师对齐每张表的分母、排序、脚注。
3. **SDTM**：原始 EDC → 标准 domain（DM、AE、EX、LB、RS、TU/TR、DS），受控术语，SUPP--。
4. **ADaM**：ADSL（一人一行，人群标志）、BDS（ADLB、ADVS、ADTTE、ADRS）、OCCDS（ADAE、ADCM）。核心原则：可追溯，一个 PROC 就能出表。
5. **TLF**：人口学、处置、暴露、疗效、安全性。
6. **提交包**：define.xml、cSDRG / ADRG、Pinnacle 21 报告（解释或修复每个 issue）。

| 常问 | 中文要点 | 英文回答 |
| --- | --- | --- |
| SDTM 和 ADaM 的区别？ | SDTM 是收集到什么；ADaM 是分析需要什么 | "SDTM represents what was collected; ADaM is analysis-ready and traceable back to SDTM, so one procedure produces one result." |
| BDS 里 PARAMCD / AVAL / BASE / CHG / ABLFL 怎么用？ | 参数长格式；基线标志驱动 BASE，再算 CHG | "Each row is one parameter at one timepoint. ABLFL flags the baseline record, BASE carries it to every row, and CHG equals AVAL minus BASE." |
| Pinnacle 21 报错怎么处理？ | 先分类：真错误修复，数据本身如此就写进 reviewer's guide | "I triage each issue: fix true errors, and document data-driven exceptions in the reviewer's guide with a justification." |

## 肿瘤疗效终点

这是你最强的部分，面试里要主动引到这里。核心是 ADTTE 里的事件与删失逻辑。

| 终点 | 事件 | 常见删失规则 | 分析 |
| --- | --- | --- | --- |
| PFS | 疾病进展（PD）或任何原因死亡 | 无事件删失于最后一次充分评估；新抗肿瘤治疗前删失；连续 ≥2 次缺失评估后的事件删失于缺失前最后一次评估 | KM 中位数 + 95% CI；分层 log-rank；分层 Cox HR |
| OS | 任何原因死亡 | 删失于最后已知存活日期 | 同上 |
| ORR | CR 或 PR（通常需确认） | 不适用；无评估者算非应答 | 比例 + Clopper–Pearson CI |
| DOR | 仅应答者：首次应答到 PD 或死亡 | 同 PFS | KM（仅应答者人群） |

类比：ADTTE 就像一张跑步计时表。起点是随机化日期，终点要么是摔倒（事件），要么是没跑完但离开了赛道（删失）。`CNSR=0` 是事件，`CNSR=1` 是删失，`EVNTDESC` / `CNSDTDSC` 说明原因。

面试题：

- **PD 前开始了新的抗肿瘤治疗，怎么处理？**
  - "Per most SAPs, PFS is censored at the last adequate assessment before the new therapy, because the later progression no longer reflects the study treatment. I'd confirm the exact rule in the SAP and add a sensitivity analysis that counts it as an event."
- **为什么用分层 Cox？**
  - "Randomization was stratified, so the analysis should respect the same strata. Stratifying lets each stratum keep its own baseline hazard while estimating one common treatment effect."
- **如何 QC 一张 KM 表？**
  - "Independently derive ADTTE from SDTM, compare event and censoring counts by arm first, then reproduce the median, CI and HR. Most mismatches come from censoring dates, so I check a sample of censored patients by hand."
- **比例风险假设不成立怎么办？**
  - "Check with Schoenfeld residuals or log(-log) plots. If violated, I'd report it and support the statistician with RMST or piecewise HRs as prespecified sensitivity analyses."

## 安全性分析

安全性表数量最多，考的是细节：TEAE 的定义、按人还是按事件计数、最高等级怎么取。

| 表 | 关键点 |
| --- | --- |
| TEAE 概览 | TRTEMFL：首剂当天或之后发生，或基线已有但加重；截止到末次给药后 N 天（看 SAP） |
| SOC / PT 表 | 按人计数，同一人同一 PT 只算一次；按第一列频数降序；MedDRA 版本写进脚注 |
| 按最高等级 | 每人每 PT 取最高 CTCAE / ASTCT 等级；缺失等级的处理规则要先确认 |
| AESI（如 CRS） | 按给药阶段；发作时间和持续时间；症状谱；处理（tocilizumab、激素） |
| 实验室 shift | 基线等级 × 基线后最差等级（ATOXGR）；BNRIND / ANRIND |
| 暴露量 | 治疗持续时间、剂量强度、剂量中断 / 减量 |

面试题：

- **AE 开始日期部分缺失，怎么判断是否 TEAE？**
  - "I impute per the SAP, typically conservatively: if the month and year match first dose, use the first-dose date, so a possibly treatment-emergent event isn't missed. The imputed date and its flag go in ADAE (ASTDTF) for traceability."
- **各列 n 加起来不等于总数，是 bug 吗？**
  - "Not necessarily. Subjects are counted once per row, but one subject can have several PTs under one SOC, and pooled columns can overlap. I check that no subject is double-counted within a single cell."
- **双抗的 CRS 你怎么汇总？**
  - "By incidence and maximum ASTCT grade, by dosing step, since step-up dosing is designed to reduce early CRS, plus time to onset, duration, signs and symptoms, and management."

## SAS / R 技术题与 QC

技术面通常一半口述、一半现场写代码。下面这些要能不查资料答出来。

| 主题 | 要能说清楚的 |
| --- | --- |
| MERGE vs SQL JOIN | MERGE 需先排序，多对多会出错；SQL 做笛卡尔积。合并后检查 log 里的 "repeats of BY values" |
| RETAIN / FIRST. / LAST. | 累计、取每组首末记录、基线携带 |
| 宏 | %macro / %let / call symput；参数化 TLF；调试用 MPRINT / SYMBOLGEN |
| 统计过程 | PROC FREQ（卡方、CMH、exact CI）、LIFETEST、PHREG、MIXED（MMRM）、LOGISTIC |
| 输出 | PROC REPORT + ODS RTF；dummy shell 保证空组也有行 |
| R | tidyverse 做数据处理；survival / survminer；pharmaverse（admiral 生成 ADaM、Tplyr / rtables 出表） |
| Log 审查 | 0 ERROR、0 WARNING；还要查 "uninitialized"、"converted"、"repeats of BY values" |

Double programming 的标准做法：

1. QC 程序员只看 SAP、规格和 shell，不看主程序，独立写。
2. `PROC COMPARE` 比对 ADaM 和表格数据集，要求 0 差异。
3. 有差异时先定位到格子和受试者，再分类：规格理解不同（交统计师裁定），还是代码错误。
4. 所有问题进 issue log，重跑后关闭。

> "For QC I program independently from the spec, never from the production code. PROC COMPARE must show zero differences. When there is a mismatch, I trace it to the cell and the subjects, then decide whether it's a spec interpretation, which goes to the statistician, or a coding error. Everything is logged in the issue tracker."

加分题（AI）：不要夸大。"I use AI as an assistant for drafting code from specs and cross-checking logic, but every number and every QC comparison stays deterministic in SAS or R, so results are reproducible and auditable."

## 行为面试 STAR 故事与反问

准备 3 个故事，覆盖大多数行为题。每个控制在 90 秒内。

| 故事 | 能回答的题 | Situation / Task | Action | Result |
| --- | --- | --- | --- | --- |
| 1. 规格不一致的补救 | 压力、截止日期、优先级 | 临近报告节点，发现规格不一致，可能影响 385 个输出 | 评估影响范围 → 和统计师对齐修正方案 → 受控重跑与独立 QC 并行 | 约 3 天完成补救，CSR 按时交付 |
| 2. 发现规格不一致 | 注重细节、主动沟通 | 姊妹表的过滤条件不一致 | 对比代码、定位差异、和统计师确认规则 | 两张表统一规则，写进 issue log |
| 3. 从临床到编程 | 为什么转行、你的独特优势 | 神经外科背景转向统计编程 | 系统学习 CDISC / SAS / R，在 CRO 实战 | 能从临床角度发现派生问题 |

关于故事 2：只讲你当时真实做过的部分。如果是在回顾代码时才发现的，就说「when reviewing sister programs」，不要说成当时 QC 抓到的。

> Why this role: "Oncology RCTs are where my experience is deepest, and where clinical judgement helps programming most: endpoints like PFS depend on censoring rules that only make sense if you understand how patients are actually followed."

反问问题（选 2–3 个）：

- "What therapeutic areas and study phases would I support first?"
- "Is the model FSP or full-service, and how are programmers paired with statisticians?"
- "How is QC organized: independent double programming for all outputs, or risk-based?"
- "Is the team using SAS only, or moving toward R and pharmaverse?"
- "What does success look like in the first 90 days?"
