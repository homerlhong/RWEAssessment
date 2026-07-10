# Amgen Center for Observational Research — Senior RWD Analyst/Programmer
## SimulStat RWE Assessment 准备攻略（整合版）

---

## 一、岗位背景

**职位**：Senior RWD Analyst/Programmer（Remote）
**部门**：Amgen Center for Observational Research
**招聘方**：SimulStat Incorporated（Recruiter: Ben Jones）

**核心职责**：
将大规模 claims 和 EHR 原始数据，转化为可供 epidemiologists / statisticians / analysts 

使用的 patient cohorts、
longitudinal event histories 
和 analysis-ready datasets，
支撑 safety、
effectiveness、
patient outcomes 相关的 RWE / HEOR 研究。

**Basic Qualifications**：
- SAS 编程经验 4 年以上（analytical/statistical role）
- SQL database programming 实操经验
- Survival analysis、regression modeling 等统计方法应用经验
- 使用过 MarketScan、Optum、Medicare 等 claims/EHR 数据库

**Preferred Qualifications**：
- OMOP CDM 经验
- Python / R / Databricks 或其他云端分析平台
- Pharma/biotech 行业 observational/RWE 研究支持经验
- 流行病学方法训练（cohort/case-control 设计、confounding control、sensitivity analysis）

**岗位定位判断**：这是一个偏 **编程/数据交付** 的岗位，不是纯流行病学/生物统计理论岗。测评重点大概率落在"能不能把原始 claims/EHR 数据变成干净、可复现的分析数据集"，而不是抽象统计推导。

---

## 二、你的核心人设定位

> 我有临床医学 + 肿瘤统计编程 + 真实世界证据分析的复合背景。我既懂肿瘤临床终点和研究问题，也具备 SDTM/ADaM、TLF、SAS 编程和 QC validation 的交付经验。在 RWE 项目中，我的核心优势是能够将临床研究问题转化为清晰的 cohort definition、index date、exposure、outcome、covariates 和 analysis-ready dataset，并确保整个过程可追溯、可复现、可验证。

**贯穿始终的 5 个关键词**：
1. RWE 方法学
2. SAS/SQL 编程
3. Oncology 经验
4. Pharma 交付能力
5. QC / Validation / Reproducibility

**答题核心原则**：不要讲得太学术。少讲纯理论，多讲"我怎么做""我做过什么""我怎么保证质量"。

---

## 三、预计考察重点（按优先级排序）

### 1. SAS / SQL 核心编程 ★★★★★（JD 硬性要求，最高优先级）
- `PROC SQL` joins（inner/left/right）、子查询
- Data step：`merge`、`retain`、`first.`/`last.` 逻辑（处理 longitudinal 数据的核心手法）
- `PROC TRANSPOSE`（wide ↔ long 转换）
- Macro 变量基础
- 去重逻辑（如同一天多条 claim 记录的处理）

### 2. Claims / EHR 数据结构 ★★★★★（MarketScan / Optum / Medicare）
- 典型表结构：enrollment（连续参保记录）、medical claims（inpatient/outpatient）、pharmacy claims
- **Index date、baseline/look-back period、washout period、follow-up period** 的编程逻辑
- 用 ICD-10-CM / CPT / HCPCS / NDC 编码定义 exposure 与 outcome
- Continuous enrollment 判断逻辑（常见坑：enrollment gap 如何处理）

### 3. Cohort Building & Treatment Patterns ★★★★
- "First exposure"/drug initiation 逻辑（排除 prevalent users，只保留 new users）
- Persistence/adherence 指标：**PDC (Proportion of Days Covered)**、**MPR (Medication Possession Ratio)**
- Switching / discontinuation / augmentation 判断逻辑

### 4. 统计方法 ★★★★（JD 明确要求 survival + regression）
- Kaplan-Meier、Cox proportional hazards——适用场景与假设
- Logistic / Poisson / 线性回归的区分使用
- Censoring 处理（尤其 claims 数据中常见的 disenrollment censoring）

### 5. 加分项（若涉及）
- OMOP CDM 基本表：
`person`、
`condition_occurrence`、
`drug_exposure`、
`visit_occurrence`、
`observation_period`
- Python / R / Databricks 基础操作

---

## 四、常见问题回答模板

### Q1. Why SimulStat / Why this role?
> 我对这个机会感兴趣，是因为它结合了
real-world data programming、
epidemiology 方法学以及 
pharma 客户交付，这与我的背景高度契合。
我希望能把自己的肿瘤临床背景、SAS/SQL 编程经验以及 RWE 方法学结合在一起，为 Amgen 这样的项目提供高质量、可复现的 evidence generation 支持。

### Q2. RWE 项目的一般工作流程
> 一个典型的 RWE 项目从明确 research question 和 study objective 开始，
接着评估数据源是否 fit-for-purpose，
然后定义 study population、
cohort entry criteria、
index date、
exposure、
outcome、
covariates 
和 follow-up window。
之后构建 analysis-ready dataset，
进行描述性分析、
survival analysis、
regression modeling 
或 propensity score methods（如 IPTW）。
最后通过 independent QC、
record count check、
date logic check、
missingness review 
和 sensitivity analysis 确保结果可靠。

### Q3. Claims、EHR、Registry 的区别
> Claims data 的优势是 
longitudinal utilization、
诊断、
手术
和用药信息较完整，
适合治疗模式和医疗资源使用分析，但临床细节不足。

> EHR data 包含
labs、
vitals、
临床笔记等更丰富的临床信息，
但 missingness 和 unstructured data 问题较多。

> Registry data 通常 
disease-specific，
outcome 质量较高，
但存在 selection bias 和 generalizability 限制。

> 实际项目中，我会先评估数据完整性、关键变量的可靠性，以及 exposure 和 outcome 能否被准确捕捉。

### Q4. 如何处理 Confounding 和 Bias
> 因为 RWE 是 observational study，confounding 是核心挑战。
我会基于临床知识和 causal pathway 先识别真正的 confounders，然后根据
研究设计
选择 restriction、
stratification、
multivariable regression、
PSM、
IPTW 
或 sensitivity analysis。
同时避免调整 mediator 或 collider，
并在结果解释时明确说明 residual confounding 的可能性。

### Q5. Oncology RWE 的特殊性（重点发挥优势）
> 肿瘤 RWE 的难点在于 
line of therapy、
treatment episode、
biomarker subgroup、
real-world progression 
和 response 的定义。
Claims 数据对治疗、诊断和利用情况捕捉较好，
但 progression 较难直接定义；
EHR 或 registry 能提供更多临床细节，但需要严格验证。
我之前的肿瘤临床试验编程经验，让我更理解这些 endpoint 的临床含义，也能把它们转化为清晰、可执行、可验证的分析规格。

### Q6. SAS / SQL / Programming 能力
> 我主要使用 SAS，同时具备 SQL、R 和 Python 经验。在 RWE 项目中，我会用 SAS 或 SQL 处理大型 
healthcare database，
完成 cohort extraction、
table joins、
exposure episode derivation、
outcome identification、
covariate creation 以及 
analysis-ready dataset 的构建。

我的临床试验编程背景也让我非常注重 
traceability、
reproducibility 和 
QC validation，这对 RWE 交付同样重要。

### 万能结尾句
> Overall, I believe this role is a strong match because it requires a combination of 
**RWE methodology**, **healthcare data understanding**, **SAS/SQL programming**, 
**oncology knowledge**, and **high-quality client delivery**.
This combination is exactly where my background fits best.

---

## 五、OMOP CDM / ATLAS 补充章节（Preferred Qualification 加分项）

JD 里明确把 **OMOP CDM 经验** 列为 preferred qualification。
行业趋势上，越来越多大型药企（如 AbbVie）正在把多个外部数据供应商的 RWD 统一转换成 OMOP CDM 格式，
并部署 **OHDSI ATLAS** 这类可视化工具，
让不写代码的流行病学家/医学事务团队也能自主定义 cohort、跑分析。理解这个趋势并能讲清楚，是一个明显的加分项。

### 核心知识点

**OMOP CDM 是什么**：一种标准化的数据模型，
把不同来源（claims、EHR、registry）的数据统一映射成一致的表结构和标准词汇（vocabulary），
从而支持跨数据源、可复现的分析。

**ATLAS 是什么**：
OHDSI 社区开发的开源 Web 工具，基于 OMOP CDM 之上构建，核心功能包括：

- 定义 **Concept Set**（概念集，标准化的诊断/药品/操作编码集合）
- 设计复杂 **Cohort**（队列定义）
- **Cohort Characterization**（队列特征描述）
- **Incidence Rate** 计算（发病率）
- **Population Level Effect Estimation**（人群层面效应估计，如比较有效性研究）
- **Patient Level Prediction**（患者层面预测模型）
- 查看 **Patient Profile**（患者画像）
**典型技术架构**（了解即可，无需死记）：

ATLAS（前端）+ WebAPI（Java 后端）+ ATLAS Database
（存储配置与用户生成数据，支持 Oracle/PostgreSQL/MS SQL）
+ ACHILLES（数据库层面统计报告）
+ 可选的 R Execution Engine。
通常用 Docker 部署，分 Test 和 Production 两套环境，认证多用 MS Active Directory + RBAC。

### 面试回答思路

**如果被问到"你对 OMOP CDM / ATLAS 的理解"**：
> OMOP CDM 是目前 RWE 行业里推动标准化和可重复性的重要方向，
它能把 claims、EHR 等不同来源的数据统一映射到同一套表结构和标准词汇下，方便跨数据源分析。
ATLAS 则是构建在 OMOP CDM 之上的可视化工具，
能让团队成员——即使不写代码——也能
自主定义 concept set、cohort，并跑 incidence rate、population-level effect estimation 这类分析。
即使我没有直接使用过 ATLAS，我理解它的价值在于标准化和协作效率的提升；
而且在企业实际落地时，
后台仍然需要大量的数据准备、自定义 cohort logic 和结果验证工作，这正是我 SAS/SQL 编程背景能持续发挥价值的地方。

**关键定位**：不要把 ATLAS 讲成"取代编程"的工具，
而要强调"底层数据准备和验证仍然离不开扎实的编程能力"——这正好呼应你的核心人设（SAS/SQL + QC/Validation）。

---

## 六、MarketScan → OMOP ETL 核心技术考点（实战细节，含加分回答）

这一部分对应更深入的技术追问——如果面试官/测评往 "ETL 实操细节" 方向深挖，用这三个考点应对。

### 考点一：模糊 Domain 怎么分表？（Domain Priority 规则）

**规则**：当一个 source code 属于双重 domain（比如同时像 Condition 又像 Procedure），
且没有明确映射到标准 concept 时，ETL 按固定优先级分表：

> **Condition > Procedure > Measurement > Observation > Device > Drug**

**每个 domain 的判断要点**：
| Domain | 目标表 | 典型例子 | 排序逻辑 |
|---|---|---|---|
| Condition | `condition_occurrence` | 疾病诊断（如肺恶性肿瘤） | 疾病定义是 disease cohort 的核心入口，优先级最高 |
| Procedure | `procedure_occurrence` | 结肠镜检查等操作 | 若同一代码可能是诊断，先保证 Condition 优先 |
| Measurement | `measurement` | 血红蛋白、HbA1c 等数值化验 | 有明确 test name/value/unit，结构化程度高于 Observation |
| Observation | `observation` | 吸烟状态、家族史 | 兜底类别，不符合前三类才归入这里 |
| Device | `device_exposure` | 起搏器、支架、胰岛素泵 | 器械代码常和 procedure 绑定，需先排除 procedure 归属 |
| Drug | `drug_exposure` | NDC/RxNorm 药物代码 | 排最后不是因为不重要，而是药物通常已能通过
NDC/RxNorm 明确映射，此优先级只处理"模糊代码" |

**核心价值**：保证规则可复现、避免同一条 source record 被重复映射进多张事件表，维护数据唯一性。

**英文作答示范**：
> When a source code has an ambiguous domain — for example it could be either 
Condition or Procedure — and it doesn't map cleanly to a standard concept,
the ETL follows a fixed domain priority: Condition,
then Procedure, Measurement, Observation, Device, and finally Drug. 
This prevents the same source record from being duplicated across multiple event tables 
and keeps the mapping reproducible and auditable. That said, I wouldn't apply this
mechanically for codes that are critical to a disease cohort or outcome definition — 
I'd review the clinical meaning with the epidemiology or clinical lead, 
and consider a custom mapping or sensitivity analysis if needed.

### 考点二：急诊 + 住院同一天发生，怎么合并？（Visit 聚合逻辑）

**背景**：真实 claims 数据里，病人常常先看急诊（ER）后直接转住院（Inpatient），原始表里会是两条独立记录。

**处理逻辑**：如果同一病人同一天既有 ER visit（concept 9203）又有 Inpatient visit（concept 9201），ETL 会用聚合规则把两者合并成一个新概念：**Concept 262（Emergency Room and Inpatient Visit）**，避免后续计算住院率/住院成本时把这次事件割裂成两段。

**英文作答示范**：
> In real claims data, a patient often goes through the ER and is then admitted 
as inpatient on the same day, which shows up as two separate raw records. 
During ETL, when an ER visit and an inpatient visit occur on the same day for the same patient, 
they get consolidated into a single visit concept — Emergency Room and Inpatient Visit — 
so downstream calculations like admission rate or inpatient cost don't miss the ER portion 
or double-count the encounter.

### 考点三：一对多药物映射的"费用乘数陷阱"（COST 表风险）

**技术陷阱**：某些原始药物代码（NDC）或手术码在映射到标准词汇时，可能同时对应**多个**标准 concept
（比如一个复方药映射出两种活性成分），导致 `DRUG_EXPOSURE` 里生成多条记录。如果原始账单费用被机械地按记录数复制，
总费用会被不合理地放大（乘数陷阱）。

**处理方式**：对于会产生一对多映射的药物代码，在 COST 表里不为这些重复记录都创建费用条目，
或者将费用统一归集到主 Procedure 上，避免总金额被成倍放大。

**英文作答示范**：
> A common trap in claims-to-OMOP conversion is one-to-many drug mappings —
a single NDC code, like one for a combination product, can map to multiple standard concepts, 
generating multiple DRUG_EXPOSURE records. If the original claim cost gets copied onto 
every one of those records, total cost ends up inflated. 
The standard fix is to avoid creating duplicate cost records for these one-to-many mappings, 
or consolidate the cost onto the primary procedure instead — 
and I'd flag this specifically during QC.

---

## 七、考前自查清单

- [ ] 能写出 `PROC SQL` 的 inner/left join 语法
- [ ] 能解释 `retain` + `first.`/`last.` 在 longitudinal 数据里的作用
- [ ] 能说清 index date / washout period / look-back period 的定义与编程判断逻辑
- [ ] 能说出 PDC 和 MPR 的计算公式与区别
- [ ] 能解释 Cox regression 的比例风险假设，以及何时用 Kaplan-Meier
- [ ] 能对比 claims vs. EHR vs. registry 的优缺点
- [ ] 能讲清楚一个完整 RWE 项目从 research question 到最终 QC 的全流程
- [ ] 能讲清楚 OMOP CDM 和 ATLAS 的核心价值与功能
- [ ] 能背出 Domain Priority 顺序（Condition > Procedure > Measurement > Observation > Device > Drug）并说明原因
- [ ] 能解释 ER + Inpatient 同日合并为 Concept 262 的逻辑
- [ ] 能解释一对多药物映射导致的费用乘数陷阱及应对方式
- [ ] 准备好 1-2 个具体项目案例，能讲清楚你在其中做了什么、怎么做 QC

---

*本文件基于职位描述（Amgen Center for Observational Research, Senior RWD Analyst/Programmer）
及前期讨论整理，供考前复习使用。*

这个优先级：

Condition > Procedure > Measurement > Observation > Device > Drug

意思是：当一个原始代码在 OMOP 里身份不清楚、可能属于多个 domain 时，
ETL 要按照固定顺序决定它最终进入哪一类事件表，避免同一个代码被随意放置或重复放进多张表。
文档里明确提到，如果 source code 有双重 domain，比如 Condition/Procedure，
而且没有明确映射到标准 concept，就按这个优先级处理。 

⸻

1. Condition：疾病/诊断优先

Condition 指疾病、诊断、临床状态，进入：

condition_occurrence

例子：

一个代码既可能表示“肺癌诊断”，又可能和某个诊疗过程相关。如果系统判断它是 Condition/Procedure，
但没有更明确的标准映射，ETL 会优先把它放到 Condition。

比如：

“Malignant neoplasm of lung”
肺恶性肿瘤

它更像一个疾病状态，所以优先进入 condition_occurrence。

面试解释：

因为 RWE 研究中 disease cohort 通常依赖 diagnosis，疾病定义是最核心的入口，所以 Condition 优先级最高。

⸻

2. Procedure：手术/操作第二

Procedure 指医疗操作、手术、检查过程，进入：

procedure_occurrence

例子：

colonoscopy
结肠镜检查

它不是疾病，而是医生做了一个操作，所以放入 Procedure。

但如果某个代码既像诊断又像操作，Condition 优先于 Procedure。只有当它不符合 Condition，
或者明确是操作时，才进 Procedure。

面试解释：

Procedure 代表医疗行为，比如手术、检查、治疗操作；但如果同一个代码可能代表疾病诊断，
OMOP 规则会先保护疾病定义的准确性。

⸻

3. Measurement：可测量结果第三

Measurement 指实验室检查、数值型检测、生命体征等，进入：

measurement

例子：

Hemoglobin = 12.5 g/dL
HbA1c = 7.2%
LDL cholesterol = 130 mg/dL

这些有数值、有单位，适合进入 Measurement。

为什么 Measurement 在 Observation 前面？

因为 Measurement 更结构化，有明确 test name、value、unit，对分析更有价值。
如果一个信息能作为测量结果，就不要泛泛地放进 Observation。

⸻

4. Observation：一般临床观察第四

Observation 是比较“兜底”的临床信息，进入：

observation

例子：

smoking status
family history
pregnancy status
social history

这些不是疾病，也不是手术，也不是标准化化验数值，但仍然是有意义的临床信息。

面试解释：

Observation 更像临床背景信息或补充信息。只有当它不适合 Condition、Procedure、Measurement 时，
才考虑放入 Observation。

⸻

5. Device：医疗器械第五

Device 指植入或使用的医疗器械，进入：

device_exposure

例子：

pacemaker
stent
insulin pump
catheter

这些是“患者接触或使用过某个器械”。

为什么 Device 排在后面？

因为 claims 数据中很多器械代码可能和 procedure 绑定在一起，比如支架植入既涉及 device，也涉及 procedure。
若代码更像操作，可能优先进入 Procedure；只有明确是器械暴露时，才进入 Device。

⸻

6. Drug：药物最后

Drug 指药物暴露，进入：

drug_exposure

例子：

NDC code for adalimumab
NDC code for venetoclax
prescription claim for atorvastatin

为什么 Drug 排最后？

不是说药物不重要，而是因为真正的药物通常会通过 NDC、RxNorm、pharmacy claims 很清楚地映射到 Drug domain。
这个优先级主要处理“模糊代码”。如果一个代码已经明确是 NDC 或 RxNorm，它当然会进入 drug_exposure。

⸻

简单比喻

就像老师整理学生交上来的纸条：

如果纸条写得很模糊，老师要决定它放进哪个文件夹：

1. 先看是不是疾病诊断
2. 不是疾病，再看是不是手术操作
3. 不是操作，再看是不是化验测量
4. 不是化验，再看是不是一般观察
5. 不是观察，再看是不是医疗器械
6. 最后才看是不是药物

⸻

面试可直接说的版本

可以这样回答：

当一个 source code 在 OMOP vocabulary 里出现 ambiguous domain，比如同时可能属于 Condition 和 Procedure，
但又没有明确映射到标准 concept 时，ETL 会按照预设的 
domain priority 处理：Condition > Procedure > Measurement > Observation > Device > Drug。

例如，如果一个代码被识别为 Condition/Procedure，系统会优先把它放入 condition_occurrence，
而不是 procedure_occurrence。这样做的目的是避免同一条 source record 被重复映射到多个 event tables，
同时保证规则可重复、可解释、可 QC。

但如果这个代码对 disease cohort、outcome definition 或 exposure definition 很关键，
我会进一步 review source code、standard concept、clinical meaning，
并和 epidemiologist 或 clinical lead 确认，必要时做 custom mapping 或 sensitivity analysis。

中文压缩版：

模糊代码默认按优先级分表；Condition 最高，因为疾病队列最核心；Drug 最低不是因为不重要
，而是药物通常有 NDC/RxNorm 可以明确映射。关键代码不能机械处理，要做 clinical review 和 QC。
