# Amgen Center for Observational Research — Senior RWD Analyst/Programmer
## SimulStat RWE Assessment 准备攻略（整合版）

---

## 一、岗位背景

**职位**：Senior RWD Analyst/Programmer（Remote）
**部门**：Amgen Center for Observational Research
**招聘方**：SimulStat Incorporated（Recruiter: Ben Jones）

**核心职责**：
将大规模 claims 和 EHR 原始数据，
转化为可供 epidemiologists / statisticians / analysts 
使用的 patient cohorts、
longitudinal event histories 和 
analysis-ready datasets，
支撑 safety、
effectiveness、
patient outcomes 相关的 
RWE / HEOR 研究。

**Basic Qualifications**：
- SAS 编程经验 6 年以上（analytical/statistical role）
- SQL database programming 实操经验
- Survival analysis、regression modeling 等统计方法应用经验
- 使用过 MarketScan、Optum、Medicare 等 claims/EHR 数据库

**Preferred Qualifications**：
- OMOP CDM 经验
- Python / R / Databricks 或其他云端分析平台
- Pharma/biotech 行业 observational/RWE 研究支持经验
- 流行病学方法训练（cohort/case-control 设计、confounding control、sensitivity analysis）

**岗位定位判断**：这是一个偏 **编程/数据交付** 的岗位，不是纯流行病学/生物统计理论岗。
测评重点大概率落在"能不能把原始 claims/EHR 数据变成干净、可复现的分析数据集"，而不是抽象统计推导。

---

## 二、你的核心人设定位

> 我有临床医学 + 肿瘤统计编程 + 真实世界证据分析的复合背景。我既懂肿瘤临床终点和研究问题，
也具备 SDTM/ADaM、TLF、SAS 编程和 QC validation 的交付经验。
在 RWE 项目中，我的核心优势是能够将临床研究问题转化为清晰的 
cohort definition、
index date、
exposure、
outcome、
covariates 
和 analysis-ready dataset，
并确保整个过程可追溯、可复现、可验证。

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

- Persistence/adherence 指标：
**PDC (Proportion of Days Covered)**、
**MPR (Medication Possession Ratio)**

- Switching / discontinuation / augmentation 判断逻辑

### 4. 统计方法 ★★★★（JD 明确要求 survival + regression）
- Kaplan-Meier、Cox proportional hazards——适用场景与假设
- Logistic / Poisson / 线性回归的区分使用
- Censoring 处理（尤其 claims 数据中常见的 disenrollment censoring）

### 5. 加分项（若涉及）
- OMOP CDM 基本表：`person`、`condition_occurrence`、`drug_exposure`、
                  `visit_occurrence`、`observation_period`

- Python / R / Databricks 基础操作

---

## 四、常见问题回答模板

### Q1. Why SimulStat / Why this role?
> 我对这个机会感兴趣，是因为它结合了 real-world data programming、epidemiology 方法学
以及 pharma 客户交付，这与我的背景高度契合。我希望能把自己的
肿瘤临床背景、
SAS/SQL 编程经验以
及 RWE 方法学结合在一起，
为 Amgen 这样的项目提供高质量、
可复现的 evidence generation 支持。

### Q2. RWE 项目的一般工作流程
> 一个典型的 RWE 项目从明确 research question 和 study objective 开始，接着评估数据源是否 fit-for-purpose，
然后定义 study population、cohort entry criteria、index date、exposure、outcome、covariates 
和 follow-up window。之后构建 analysis-ready dataset，进行描述性分析、survival analysis、
regression modeling 或 propensity score methods（如 IPTW）。
最后通过 independent QC、record count check、date logic check、missingness review 和 
sensitivity analysis 确保结果可靠。

### Q3. Claims、EHR、Registry 的区别
> Claims data 的优势是 longitudinal utilization、诊断、手术和用药信息较完整，适合治疗模式和医疗资源使用分析，
但临床细节不足。
> EHR data 包含 labs、vitals、临床笔记等更丰富的临床信息，但 missingness 和 unstructured data 问题较多。
> Registry data 通常 disease-specific，outcome 质量较高，但存在 selection bias 和 generalizability 限制。
> 实际项目中，我会先评估数据完整性、关键变量的可靠性，以及 exposure 和 outcome 能否被准确捕捉。

### Q4. 如何处理 Confounding 和 Bias
> 因为 RWE 是 observational study，confounding 是核心挑战。我会基于临床知识和 causal pathway 
先识别真正的 confounders，然后根据研究设计选择 restriction、stratification、multivariable regression、
PSM、IPTW 或 sensitivity analysis。同时避免调整 mediator 或 collider，并在结果解释时明确说明 
residual confounding 的可能性。

### Q5. Oncology RWE 的特殊性（重点发挥优势）
> 肿瘤 RWE 的难点在于 line of therapy、treatment episode、biomarker subgroup、real-world progression 
和 response 的定义。Claims 数据对治疗、诊断和利用情况捕捉较好，但 progression 较难直接定义；
EHR 或 registry 能提供更多临床细节，但需要严格验证。我之前的肿瘤临床试验编程经验，
让我更理解这些 endpoint 的临床含义，也能把它们转化为清晰、可执行、可验证的分析规格。

### Q6. SAS / SQL / Programming 能力
> 我主要使用 SAS，同时具备 SQL、R 和 Python 经验。在 RWE 项目中，我会用 SAS 或 SQL 处理大型 
healthcare database，完成 cohort extraction、table joins、exposure episode derivation、
outcome identification、covariate creation 以及 analysis-ready dataset 的构建。
我的临床试验编程背景也让我非常注重 traceability、reproducibility 和 QC validation，这对 RWE 交付同样重要。

### 万能结尾句
> Overall, I believe this role is a strong match because it requires a combination of 
**RWE methodology**, **healthcare data understanding**, **SAS/SQL programming**, 
**oncology knowledge**, and **high-quality client delivery**. 
This combination is exactly where my background fits best.

---

## 五、考前自查清单

- [ ] 能写出 `PROC SQL` 的 inner/left join 语法
- [ ] 能解释 `retain` + `first.`/`last.` 在 longitudinal 数据里的作用
- [ ] 能说清 index date / washout period / look-back period 的定义与编程判断逻辑
- [ ] 能说出 PDC 和 MPR 的计算公式与区别
- [ ] 能解释 Cox regression 的比例风险假设，以及何时用 Kaplan-Meier
- [ ] 能对比 claims vs. EHR vs. registry 的优缺点
- [ ] 能讲清楚一个完整 RWE 项目从 research question 到最终 QC 的全流程
- [ ] 准备好 1-2 个具体项目案例，能讲清楚你在其中做了什么、怎么做 QC

---

*本文件基于职位描述（Amgen Center for Observational Research, Senior RWD Analyst/Programmer）
及前期讨论整理，供考前复习使用。*
