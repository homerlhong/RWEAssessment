# Amgen Senior RWD Analyst/Programmer — 49个面试问题清单

按考察重点分为 7 大类，共 49 题。

---

## 一、SAS / SQL 编程（10题）

1. How would you join two SAS datasets when the key fields have inconsistent formats (e.g., different date formats)?
2. Explain the difference between `MERGE` in a data step vs. `PROC SQL JOIN`. When would you choose one over the other?
3. How do you identify and remove duplicate records in a claims dataset using SAS?
4. Walk me through the logic to derive a patient's first exposure date to a drug using NDC codes.
5. What is the purpose of `RETAIN`, `FIRST.`, and `LAST.` when processing longitudinal claims data?
6. How would you transpose a long dataset of monthly claims into a wide format for reporting?
7. How do you handle missing values in a large claims table without introducing bias into the analysis?
8. What performance considerations do you keep in mind when running SAS programs against millions of claims records?
9. Describe how you would validate/QC a SAS-derived analysis dataset against the source data.
10. When working with very large tables, would you use `PROC SQL` or `PROC SORT` + data step merge — and why?

---

## 二、Claims / EHR 数据结构（8题）

11. What is a "continuous enrollment" requirement, and why does it matter in claims-based studies?
12. How do you define an index date in a new-user cohort study?
13. Explain the difference between a look-back period and a washout period.
14. What are the key structural differences between MarketScan, Optum, and Medicare claims data?
15. How would you distinguish inpatient vs. outpatient claims within a claims database?
16. What challenges typically arise when linking claims data to EHR data?
17. How do you handle enrollment gaps when calculating a patient's follow-up time?
18. What are common data quality issues in EHR data compared to claims data?

---

## 三、Cohort Building & Treatment Patterns（7题）

19. How do you define a "new user" (incident user) cohort, and why is this distinction important?
20. What is PDC (Proportion of Days Covered) and how is it calculated?
21. How does MPR (Medication Possession Ratio) differ from PDC?
22. How would you programmatically distinguish a treatment switch from a treatment augmentation?
23. How do you define treatment discontinuation using claims data (e.g., what gap threshold would you use, and why)?
24. Walk me through how you would build an analysis-ready dataset starting from raw claims tables.
25. How do you handle patients who have multiple qualifying index events during the study period?

---

## 四、统计方法（7题）

26. When would you use Cox proportional hazards regression vs. Kaplan-Meier estimation?
27. What is the proportional hazards assumption, and how would you test it?
28. When would logistic regression be preferred over Poisson regression?
29. How do you handle censoring in a claims-based survival analysis (e.g., disenrollment)?
30. What is propensity score matching, and when would you use IPTW instead?
31. How do you assess covariate balance after propensity score matching?
32. What's the difference between how you interpret a hazard ratio vs. an odds ratio?

---

## 五、RWE 方法学 / 研究设计（7题）

33. Walk me through the end-to-end workflow of a typical RWE study, from research question to final deliverable.
34. How do you determine whether a data source is "fit-for-purpose" for a given research question?
35. What is immortal time bias, and how would you design a study to avoid it?
36. What's the difference between confounding and effect modification?
37. How do you approach designing a sensitivity analysis for an observational study?
38. What is the OMOP Common Data Model, and what problem does it solve?
39. How would you design a study to compare treatment effectiveness using claims data alone?

---

## 六、Oncology RWE 专项（5题）

40. How do you define "line of therapy" using oncology claims data?
41. What challenges exist in capturing disease progression using real-world data?
42. How would you approximate biomarker status when working with a claims-only dataset?
43. What's your approach to defining a treatment episode in oncology RWE research?
44. How do real-world outcome/response definitions differ from clinical trial endpoints?

---

## 七、行为面试 / 项目经验（5题）

45. Tell me about a time you discovered a data quality issue that changed your study's conclusions.
46. Describe a project where you had to explain technical programming decisions to non-technical stakeholders (e.g., epidemiologists or clinicians).
47. How do you ensure reproducibility and traceability in your programming work?
48. Tell me about a time you had to work from an ambiguous or incomplete study protocol. How did you proceed?
49. How do you manage tight timelines when working on multiple RWE deliverables at once?

---

*建议：优先熟练回答第一、二、三类（JD 硬性要求的编程与数据结构部分），这些大概率是评分重点。第六类可结合你的肿瘤背景重点发挥，作为差异化优势。*

下面是 Amgen Senior RWD Analyst/Programmer — 49 个面试问题 + 英文答案 + 中文理解版。
我按面试最常问的逻辑分成 7 组：Background、RWD/RWE、Data、Programming、Statistics、Oncology、Behavioral。

Amgen Senior RWD Analyst/Programmer — 49 Interview Questions with English & Chinese Answers

⸻

A. Background / Fit

1. Tell me about yourself.

English Answer:
I have a hybrid background in clinical medicine, oncology statistical programming, and real-world data analytics.
I was trained as a physician and previously worked in neurosurgery, which gives me strong clinical understanding. 
In Canada, I have worked in clinical trial programming, RWE analytics, and regulatory data projects. 
My core strengths are SAS programming, SQL-based data handling, cohort definition, endpoint derivation, QC validation, 
and translating clinical research questions into analysis-ready datasets. For this Amgen role, I believe 
my oncology programming experience and RWD exposure make me a strong fit.

中文理解：
我有临床医学、肿瘤统计编程和真实世界数据分析的复合背景。
以前做过神经外科医生，所以有临床理解力。
在加拿大，
我做过临床试验编程、RWE 分析和监管数据项目。
我的核心优势是 SAS、SQL、cohort 定义、endpoint derivation、QC validation，
以及把临床研究问题转化成可分析的数据集。
这个 Amgen 岗位非常匹配我的背景。

⸻

2. Why are you interested in Amgen?

English Answer:
I am interested in Amgen because it is a global biotechnology company with a strong focus on oncology, inflammation,
cardiovascular disease, and other serious illnesses. The Senior RWD Analyst/Programmer role is especially attractive
to me because it combines healthcare data, statistical programming, real-world evidence generation, and cross-functional 
collaboration. I would like to contribute my SAS/RWD programming skills and oncology experience to support evidence 
generation that can inform clinical, regulatory, and business decisions.

中文理解：
我对 Amgen 感兴趣，是因为它是全球领先的生物技术公司，
重点领域包括肿瘤、炎症、心血管等重大疾病。
这个岗位吸引我，
是因为它结合了 
healthcare data、统计编程、RWE 证据生成和跨部门合作。
我希望用自己的 SAS/RWD 编程和肿瘤经验支持证据生成。

⸻

3. Why this Senior RWD Analyst/Programmer role?

English Answer:
This role matches the intersection of my experience. I have hands-on experience building analysis datasets, 
deriving endpoints, creating TLFs, performing QC, and working with healthcare data. I also understand how important
traceability, reproducibility, and quality control are in both clinical trials and RWE projects.
The role requires someone who can translate scientific questions into executable programming specifications,
and that is exactly where my background fits best.

中文理解：
这个岗位正好在我的经验交叉点上。
我做过分析数据集、endpoint derivation、TLF、QC，也接触过 healthcare data。
我理解临床试验和 RWE 项目都非常重视可追溯、可复现和质量控制。
这个岗位需要能把科学问题变成可执行编程规格的人，这正是我的优势。

⸻

4. How does your clinical background help you in RWD programming?

English Answer:
My clinical background helps me understand disease progression, treatment pathways, clinical endpoints, 
and the limitations of real-world data. For example, in oncology RWD, defining line of therapy, treatment episodes,
progression, response, and biomarker subgroups requires clinical judgment, not only programming skills. 
My medical training allows me to communicate more effectively with epidemiologists, clinicians, and statisticians,
and to identify potential clinical inconsistencies during data review.

中文理解：
我的临床背景帮助我
理解疾病进展、治疗路径、临床终点和真实世界数据的局限。
比如肿瘤 RWD 中，
line of therapy、
treatment episode、
progression、
response 
和 biomarker subgroup 的定义，
不只是编程问题，也需要临床判断。
医学背景让我能更好地和流行病学家、医生、统计师沟通，
也能在数据审查中发现临床不合理的地方。

⸻

5. What is your biggest strength for this role?

English Answer:
My biggest strength is the ability to connect clinical understanding with technical implementation. I can understand
the clinical research question, translate it into cohort definitions and variable specifications, program the 
datasets using SAS or SQL, and validate the results through systematic QC. This combination of clinical insight, 
programming ability, and delivery mindset is highly relevant to RWD evidence generation.

中文理解：
我最大的优势是能连接临床理解和技术实现。
我能理解临床研究问题，
把它转化成 cohort definition 和变量规格，
用 SAS 或 SQL 编程实现，
并通过系统性 QC 验证结果。
这种临床、编程和交付能力的组合，非常适合 RWD 证据生成。

⸻

B. RWD / RWE Core Concepts

6. What is real-world data?

English Answer:
Real-world data refers to data collected outside traditional randomized clinical trials. Common sources include 
claims databases, electronic health records, registries, pharmacy data, laboratory data, and patient-generated data. 
RWD can be used to understand treatment patterns, patient characteristics, safety outcomes, healthcare resource 
utilization, effectiveness, and unmet medical needs in routine clinical practice.

中文理解：
真实世界数据是指传统随机临床试验之外收集的数据。
常见来源包括 
claims、
EHR、
registry、
药房数据、
实验室数据
和患者生成数据。
RWD 可用于研究治疗模式、患者特征、安全性、医疗资源使用、真实世界疗效和未满足临床需求。

⸻

7. What is real-world evidence?

English Answer:
Real-world evidence is clinical evidence generated from the analysis of real-world data. While RWD is the raw 
or processed data source, RWE is the interpretation and evidence produced through appropriate study design, 
data curation, statistical analysis, and quality control. RWE can support regulatory, medical, HEOR, market access, 
and clinical development decisions.

中文理解：
真实世界证据是基于真实世界数据分析后产生的临床证据。
RWD 是数据来源，RWE 是通过研究设计、数据整理、统计分析和 QC 后得到的证据。
RWE 可以支持监管、医学、HEOR、市场准入和临床开发决策。

⸻

8. Describe a typical RWD study workflow.

English Answer:
A typical RWD study starts with defining the research question and study objectives. Then we assess whether the 
data source is fit-for-purpose. After that, we define the study population, inclusion and exclusion criteria, 
index date, exposure, outcomes, covariates, and follow-up period. Then we build the analysis-ready dataset, 
perform descriptive and statistical analyses, generate tables and figures, and conduct QC checks. Finally,
results are interpreted with attention to bias, confounding, missing data, and data limitations.

中文理解：
一个典型 RWD 项目从研究问题和研究目标开始。
然后评估数据源是否 fit-for-purpose。
接着定义研究人群、
入排标准、
index date、
exposure、
outcomes、
covariates 
和 follow-up period。
之后构建 analysis-ready dataset，做描述性和统计分析，生成表格和图形，并进行 QC。
最后解释结果时要考虑 bias、confounding、missing data 和数据局限。

⸻

9. What does fit-for-purpose mean in RWD?

English Answer:
Fit-for-purpose means that the data source is appropriate for answering the specific research question. 
I would evaluate whether the database contains the target population, exposure, outcome, covariates, 
sufficient follow-up, sample size, and data completeness. For example, claims data may be fit for treatment 
pattern and healthcare utilization studies, but may not be sufficient for detailed clinical response unless 
linked to EHR or registry data.

中文理解：
Fit-for-purpose 指数据源是否适合回答特定研究问题。
我会评估数据中是否包含目标人群、暴露、结局、协变量、足够 follow-up、样本量和完整性。
比如 claims 数据适合治疗模式和医疗资源使用研究，
但如果要分析详细临床 response，可能需要 EHR 或 registry 数据。

⸻

10. What are common RWD study designs?

English Answer:
Common RWD study designs include retrospective cohort studies, prospective observational studies, case-control studies, 
cross-sectional studies, treatment pattern studies, external control arm studies, comparative effectiveness studies, 
and safety studies. The choice depends on the research question, outcome frequency, exposure definition, 
available follow-up, and the quality of the data source.

中文理解：
常见 RWD 研究设计
包括回顾性队列、前瞻性观察性研究、病例对照、横断面研究、治疗模式研究、外部对照研究、比较有效性研究和安全性研究。
选择哪种设计取决于研究问题、结局频率、暴露定义、follow-up 和数据质量。

⸻

11. What is an index date?

English Answer:
The index date is the starting point for follow-up in an observational study. It is usually defined based on 
a clinically meaningful event, such as treatment initiation, diagnosis date, procedure date, or cohort entry date. 
Correct index date definition is important because it determines baseline covariate assessment, exposure classification,
follow-up time, and outcome attribution.

中文理解：
Index date 是观察性研究中 follow-up 的起点，
通常基于有临床意义的事件定义，
例如治疗开始、诊断日期、手术日期或入组日期。

Index date 非常关键，

因为它决定 
baseline covariates、
exposure classification、
follow-up 时间
和 outcome attribution。

⸻

12. What is a baseline period?

English Answer:
The baseline period is the time window before the index date used to assess patient characteristics, comorbidities, 
prior treatment, prior healthcare utilization, and baseline clinical status. In claims studies, a common baseline 
period may be 6 or 12 months of continuous enrollment before the index date. The baseline period helps define 
covariates and ensure comparability across study groups.

中文理解：
Baseline period 是 index date 之前的一段时间，
用于评估患者特征、合并症、既往治疗、医疗资源使用和基线临床状态。
在 claims 研究中，
常用 6 或 12 个月连续参保作为 baseline period。
它帮助定义 covariates，也帮助比较不同组的可比性。

⸻

13. What is follow-up time in RWD?

English Answer:
Follow-up time is the period after the index date during which outcomes, treatment changes, discontinuation, 
death, or healthcare utilization are assessed. It may end at outcome occurrence, treatment discontinuation,
disenrollment, death, data cutoff, or end of study period. Clear follow-up rules are important to avoid 
immortal time bias and inconsistent outcome measurement.

中文理解：
Follow-up time 是 index date 之后
观察结局、治疗变化、停药、死亡或医疗资源使用的时间。
它可能结束于结局发生、停药、退出保险、
死亡、data cutoff 或研究结束。
清晰的 follow-up 规则可以避免 immortal time bias 和结局测量不一致。

⸻

14. What is immortal time bias?

English Answer:
Immortal time bias occurs when a period of follow-up during which the outcome could not occur is incorrectly 
classified or assigned to an exposure group. This can make a treatment appear more beneficial than it truly is.
To avoid it, exposure, index date, and follow-up should be aligned carefully, and time-dependent exposure methods 
may be considered when appropriate.

中文理解：
Immortal time bias 是指某段患者“不可能发生结局”的时间被错误归入某个暴露组，
导致治疗效果看起来比真实情况更好。
避免方法是
合理定义 exposure、index date 和 follow-up，
必要时使用 time-dependent exposure 方法。

⸻

C. RWD Data Sources

15. What are the differences between claims, EHR, and registry data?

English Answer:
Claims data captures billing information such as diagnoses, procedures, medications, and healthcare utilization. 
It is longitudinal and useful for treatment patterns and cost studies, but lacks detailed clinical information. 
EHR data contains richer clinical details such as labs, vitals, physician notes, and test results,
but may have missingness and unstructured data challenges. Registry data is often disease-specific and 
may have higher-quality outcome information, but may have selection bias and limited generalizability.

中文理解：
Claims 数据主要是医保或账单数据，
包括诊断、手术、用药和医疗资源使用。
它有纵向优势，
适合治疗模式和费用研究，但临床细节不足。
EHR 有 labs、vitals、医生记录和检查结果，临床信息更丰富，
但 missingness 和非结构化数据问题较多。
Registry 通常是疾病特异性数据库，结局质量较高，
但可能有 selection bias 和外推性限制。

⸻

16. What are common limitations of claims data?

English Answer:
Common limitations include lack of detailed clinical information, limited laboratory results, limited disease 
severity measures, potential coding errors, diagnosis codes used for billing rather than clinical confirmation, 
and incomplete capture of services outside the insurance system. Claims data is strong for utilization and 
medication dispensing, but outcome definitions often need careful validation.

中文理解：
Claims 数据常见局限包括
缺少详细临床信息、
实验室结果有限、
疾病严重程度有限、
编码错误、
诊断代码可能是为了报销而不是临床确认，
以及无法捕捉保险系统外的服务。
Claims 对医疗使用和处方领取很强，但 outcome definition 需要严格验证。

⸻

17. What are common limitations of EHR data?

English Answer:
EHR data can have missing values, inconsistent documentation, unstructured clinical notes, variation across sites, 
and incomplete capture of care received outside the health system. However, EHR data provides rich clinical details 
such as laboratory results, tumor characteristics, biomarkers, performance status, and physician assessments,
which are often not available in claims data.

中文理解：
EHR 的问题包括 
missing values、
记录不一致、
非结构化临床笔记、
不同机构差异，
以及无法完整捕捉系统外就医。
但 EHR 的优势是有丰富临床信息，
比如 labs、肿瘤特征、biomarker、performance status 和医生评估，这些通常是 claims 没有的。

⸻

18. How do you assess data quality in RWD?

English Answer:
I assess data quality by checking completeness, consistency, plausibility, duplicate records, date logic,
missingness, coding validity, continuous enrollment, and availability of key variables. I also compare patient 
counts across derivation steps, review extreme values, and validate important clinical concepts such as exposure
and outcomes. For high-impact variables, I would document assumptions and conduct sensitivity analyses when needed.

中文理解：
我会
从完整性、一致性、合理性、重复记录、日期逻辑、缺失情况、编码有效性、连续参保和关键变量可用性几个方面评估数据质量。
我也会检查每一步 patient counts、异常值，
并验证 exposure 和 outcomes 等重要临床概念。
对于关键变量，我会记录假设，
并在必要时做敏感性分析。

⸻

19. How do you handle missing data in RWD?

English Answer:
First, I try to understand why the data are missing and whether missingness is related to the outcome or exposure. 
Then I summarize missingness patterns by treatment group and key subgroups. Depending on the variable and analysis 
objective, options may include complete-case analysis, missing indicator, multiple imputation, or sensitivity analysis.
I would avoid blindly imputing clinically meaningful variables without understanding the data generation process.

中文理解：
我首先会理解
为什么缺失，
以及缺失是否和 outcome 
或 exposure 有关。
然后按治疗组和关键亚组总结 missingness pattern。
根据变量和分析目标，
可以考虑 complete-case analysis、missing indicator、multiple imputation 或 sensitivity analysis。
我不会在不了解数据产生机制的情况下盲目插补临床关键变量。

⸻

20. What is continuous enrollment in claims data?

English Answer:
Continuous enrollment means that a patient has uninterrupted insurance coverage during a specified period, 
often before and after the index date. It is important because claims data can only capture healthcare services
while the patient is enrolled. Requiring continuous enrollment helps ensure that baseline characteristics, 
prior treatments, and outcomes are more completely observed.

中文理解：
Continuous enrollment 指患者在某段时间内持续参保，通常包括 index date 前后。它很重要，因为 claims 数据只能捕捉患者参保期间
发生的医疗服务。要求 continuous enrollment 可以提高 baseline characteristics、既往治疗和 outcomes 的完整性。

⸻

21. How would you identify a disease cohort in claims data?

English Answer:
I would define the disease cohort using diagnosis codes, procedure codes, medication codes, and sometimes
repeated diagnosis requirements. For example, I may require at least two diagnosis codes on separate dates 
or one inpatient diagnosis code to improve specificity. I would also apply age, enrollment, index date, 
and exclusion criteria. The exact algorithm should be based on literature, clinical input, and study objectives.

中文理解：
我会用诊断代码、手术代码、药物代码，
有时还会要求重复诊断来定义疾病 cohort。
比如要求两个不同日期的诊断代码，或一次住院诊断，
以提高特异性。
还要加年龄、连续参保、index date 和排除标准。
具体算法应基于文献、临床输入和研究目标。

⸻

22. How would you define treatment exposure in RWD?

English Answer:
Treatment exposure can be defined using pharmacy claims, administration codes, procedure codes, or medication records. 
I would identify treatment initiation, treatment episodes, gaps, discontinuation, switching, and combination therapy
based on prespecified rules. For oral drugs, days supply is important. For infused drugs, administration dates
and procedure codes may be used. Clear exposure definitions are essential for reproducibility.

中文理解：
Treatment exposure 可以
用药房 claims、给药代码、手术/操作代码或 medication records 定义。
我会根据预先规则定义 
treatment initiation、treatment episodes、gap、discontinuation、switching 和 combination therapy。
口服药要看 days supply；
输注药要看 administration dates 和 procedure codes。
清晰定义 exposure 对可复现非常重要。

⸻

D. SAS / SQL / Programming

23. What SAS experience do you have?

English Answer:
I have extensive SAS experience in clinical trial and RWD-related programming. I have used SAS for 
data cleaning, derivations, SDTM/ADaM datasets, TLF generation, QC validation, macro development, 
and analysis dataset creation. In RWD projects, I can use SAS to process large healthcare datasets, 
perform joins, derive cohorts, create exposure and outcome variables, and generate analysis-ready datasets 
with traceable programming logic.

中文理解：
我有较丰富的 SAS 经验，既做过临床试验，也做过 RWD 相关编程。
我用 
SAS 做数据清洗、
变量派生、
SDTM/ADaM、
TLF、
QC validation、
macro 和分析数据集。
在 RWD 项目中，我能用 SAS 处理大型 healthcare datasets，做 joins、cohort derivation、
exposure/outcome 变量和 analysis-ready datasets。

⸻

24. What SQL experience do you have?

English Answer:
I have used SQL for querying and joining relational healthcare data, extracting cohorts, filtering patient records, 
summarizing events, and creating intermediate analysis tables. SQL is especially useful in RWD because claims 
and EHR databases are often stored in relational structures. I am comfortable using joins, subqueries, aggregation, 
date filters, and case logic to derive patient-level variables.

中文理解：
我
用 SQL 查询和合并关系型healthcare data，
抽取 cohorts，
筛选患者记录，总结事件，并创建中间分析表。
SQL 在 RWD 中特别重要，
因为 claims 和 EHR 数据通常是关系型结构。
我熟悉
joins、
subqueries、
aggregation、
date filters 
和 case logic 来生成 
patient-level 变量。

⸻

25. How do you ensure programming quality?

English Answer:
I ensure programming quality through clear specifications, modular code, version control, independent QC, log review, 
record count comparison, source-to-output traceability, and validation against table shells or expected results. 
I also check date logic, duplicates, missing values, treatment group assignments, and denominator definitions. 
For important outputs, I prefer independent programming validation rather than only code review.

中文理解：
我通过清晰规格、
模块化代码、
版本控制、
独立 QC、
log review、
record count comparison、
从源数据到输出的可追溯性，
以及和 table shells 或 expected results 对比来保证质量。
我也会检查日期逻辑、重复值、缺失值、治疗组分配和 denominator。
关键输出最好做 independent programming validation。

⸻

26. How do you debug SAS code?

English Answer:
I usually start by reviewing the SAS log for errors, warnings, uninitialized variables, missing formats, 
merge issues, and unexpected notes. Then I isolate the problematic step, check input and output record counts, 
inspect key variables, and run smaller test datasets when needed. If the issue is related to derivation logic, 
I trace it back to the specification and source data.

中文理解：
我通常
先看 SAS log，
检查 errors、
warnings、
未初始化变量、
format 问题、
merge 问题和
异常 notes。
然后定位出问题的步骤，
检查输入输出记录数、关键变量，必要时用小数据集测试。
如果问题和 derivation logic 有关，我会回到 specification 和 source data 追踪。

⸻

27. How do you validate an analysis-ready dataset?

English Answer:
I validate an analysis-ready dataset by checking cohort counts, key inclusion and exclusion criteria, 
index date derivation, baseline covariates, exposure episodes, outcome flags, follow-up time, and 
censoring variables. I also compare derived variables against specifications, review missingness and distributions, 
and perform independent QC for key derivations. Documentation is important so that the dataset can be reproduced 
and audited.

中文理解：
我会检查 
cohort counts、
入排标准、
index date、
baseline covariates、
exposure episodes、
outcome flags、
follow-up time 和 
censoring variables。
还会把派生变量和 specifications 对比，检查 missingness 和分布，
对关键派生做 independent QC。
文档也很重要，这样数据集可以复现和审计。

⸻

28. How do you work with large datasets?

English Answer:
For large datasets, I focus on efficient data handling. I select only necessary variables, filter early, 
use appropriate indexing when available, avoid unnecessary sorts, summarize at the right level, 
and use SQL joins carefully. I also check intermediate record counts to avoid accidental many-to-many joins.
In SAS, I pay attention to memory, sorting, formats, and log messages.

中文理解：
处理大数据时，我会
注重效率。
只选择必要变量，尽早过滤，必要时
使用 indexing，避免不必要排序，
在合适层级汇总，
并谨慎使用 SQL joins。
我也会检查中间记录数，
避免意外 many-to-many joins。
在 SAS 里，我会注意内存、排序、formats 和 log messages。

⸻

29. What is your approach to creating tables and figures?

English Answer:
I start by reviewing the table shell, denominator definition, population flag, treatment group, 
analysis variable, statistical method, and display format. Then I create a programming plan, 
derive the necessary dataset, generate the output, and validate it independently. For RWD outputs,
I pay special attention to cohort attrition, baseline characteristics, treatment patterns, outcome rates, 
and follow-up time.

中文理解：
我会先看
table shell、
denominator、
population flag、
treatment group、
analysis variable、
统计方法
和显示格式。

然后制定编程计划，生成所需数据集，输出表格，并做独立验证。
RWD 输出中特别关注 
cohort attrition、
baseline characteristics、
treatment patterns、
outcome rates 
和 follow-up time。

⸻

30. How do you document programming work?

English Answer:
I document programming work through clear code comments, derivation notes, specifications, QC documentation, 
issue logs, and version history. For complex derivations, I describe the data source, assumptions, logic, 
input variables, output variables, and validation approach. Good documentation supports reproducibility, 
audit readiness, and smooth handover to other team members.

中文理解：
我会用代码注释、
derivation notes、
specifications、
QC 文档、
issue log 
和版本记录来记录编程工作。
复杂派生要说明数据源、假设、逻辑、输入变量、输出变量和验证方法。
好的文档有助于可复现、审计准备和团队交接。

⸻

E. Statistical / Epidemiology Concepts

31. How do you handle confounding in RWD studies?

English Answer:
I handle confounding by first using clinical knowledge and causal thinking to identify true confounders. 
Then, depending on the study design, I may use restriction, stratification, multivariable regression, 
propensity score matching, weighting such as IPTW, or sensitivity analyses. I also avoid adjusting for 
mediators or colliders. Even after adjustment, I would clearly acknowledge the possibility of residual confounding.

中文理解：
我会
先用临床知识和因果思维识别真正的 confounders。
然后根据研究设计
选择 restriction、
stratification、
多变量回归、
PSM、
IPTW 
或 sensitivity analysis。
我也会避免调整 mediator 或 collider。
即使调整后，也要承认 residual confounding 可能存在。

⸻

32. What is propensity score matching?

English Answer:
Propensity score matching is a method used to balance observed baseline characteristics between treatment groups 
in observational studies. The propensity score is the probability of receiving a treatment given observed covariates.
Patients from different groups are matched based on similar propensity scores. 
The goal is to reduce confounding by measured variables, although it cannot address unmeasured confounding.

中文理解：
PSM 是观察性研究中
平衡不同治疗组 baseline characteristics 的方法。
Propensity score 是患者在给定协变量情况下接受某治疗的概率。
不同组患者根据相似的 propensity score 匹配。
目的是减少已测量变量造成的 confounding，但不能解决未测量混杂。

⸻

33. What is IPTW?

English Answer:
IPTW stands for inverse probability of treatment weighting. It uses propensity scores to create a weighted 
pseudo-population in which measured baseline covariates are balanced across treatment groups. 
Each patient receives a weight based on the inverse probability of receiving the treatment they actually received. 
After weighting, treatment effects can be estimated with better covariate balance.

中文理解：
IPTW 是 inverse probability of treatment weighting。
它利用 propensity score 构建一个加权后的 pseudo-population，
使不同治疗组的 baseline covariates 更平衡。
每个患者根据其实际接受治疗的概率倒数赋权。
加权后可以更合理估计 treatment effect。

⸻

34. How do you assess covariate balance?

English Answer:
I usually assess covariate balance using standardized mean differences, or SMDs, 
before and after matching or weighting. An SMD below 0.1 is often considered acceptable, 
although this depends on context. I would also review distributions of key clinical variables and 
not rely only on p-values, because p-values are sensitive to sample size.

中文理解：
我通常用 standardized mean differences，也就是 SMD，
评估匹配或加权前后的 covariate balance。
一般 SMD 小于 0.1 被认为可接受，
但也要看具体情况。
我也会查看关键临床变量分布，
而不只依赖 p-value，
因为 p-value 对样本量很敏感。

⸻

35. What is censoring in survival analysis?

English Answer:
Censoring occurs when the event of interest has not been observed for a patient by the end of 
follow-up or when the patient is lost to follow-up. In RWD, censoring may occur due to disenrollment, 
end of data availability, death for non-death endpoints, treatment discontinuation, or study end. 
Correct censoring rules are important for unbiased time-to-event analysis.

中文理解：
Censoring 指患者
在 follow-up 结束前没有观察到目标事件，或者失访。
在 RWD 中，
censoring 可能因为退出保险、数据结束、非死亡终点中的死亡、停药或研究结束。
正确的 censoring 规则对 time-to-event 分析很重要。

⸻

36. Explain Kaplan-Meier analysis.

English Answer:
Kaplan-Meier analysis is used to estimate the survival function or time-to-event probability over time.
It accounts for censored observations and provides estimates such as median survival time and survival 
probability at specific time points. In RWD studies, KM analysis can be used for outcomes such as overall survival, 
time to treatment discontinuation, or time to next treatment.

中文理解：
Kaplan-Meier 分析用于
估计 survival function 或 time-to-event 概率。
它可以处理 censored observations，
并提供 median survival time 和特定时间点生存率。
在 RWD 中，
KM 可用于 OS、time to treatment discontinuation
或 time to next treatment。

⸻

37. Explain Cox proportional hazards model.

English Answer:
The Cox proportional hazards model is used to estimate the association between covariates and time-to-event outcomes. 
It produces hazard ratios comparing the hazard of an event between groups, adjusting for covariates if needed. 
A key assumption is proportional hazards, meaning the hazard ratio is relatively constant over time. 
In RWD, the model is often used for comparative effectiveness or safety outcomes.

中文理解：
Cox 比例风险模型
用于估计协变量和 time-to-event 结局之间的关系。
它
产生 hazard ratio，可以比较不同组事件风险，并可调整协变量。
关键假设是 proportional hazards，也就是 HR 随时间相对稳定。
在 RWD 中常用于比较有效性或安全性结局。

⸻

38. How do you interpret a hazard ratio?

English Answer:
A hazard ratio compares the event hazard between two groups over time. A hazard ratio below 1 suggests
a lower event hazard in the treatment group compared with the reference group, 
while a hazard ratio 
above 1 suggests a higher hazard. Interpretation should consider the confidence interval, p-value, event definition,
censoring rules, follow-up time, and potential confounding.

中文理解：
Hazard ratio 比较两个组随时间发生事件的风险。
HR 小于 1 表示治疗组相对参考组事件风险更低；
HR 大于 1 表示风险更高。
解释时要看 
confidence interval、
p-value、
事件定义、
censoring 规则、
follow-up 时间
和 potential confounding。

⸻

F. Oncology RWD

39. What are special challenges in oncology RWD?

English Answer:
Oncology RWD has several challenges, including defining line of therapy, treatment episodes, combination regimens, 
biomarker subgroups, disease progression, response, and recurrence. Claims data may capture diagnosis and treatment 
but often lacks tumor response or progression details. EHR and registry data may provide richer clinical information 
but require careful abstraction and validation. My oncology clinical trial experience helps me understand these 
endpoints and implement them more carefully in RWD.

中文理解：
肿瘤 RWD 的难点包括 
line of therapy、
treatment episodes、
联合方案、
biomarker subgroup、
疾病进展、
response 
和复发。
Claims 能捕捉诊断和治疗，但通常缺少 response/progression 细节。
EHR 和 registry 临床信息更丰富，但需要仔细提取和验证。
我的肿瘤临床试验经验能帮助我更好理解和实现这些 endpoint。

⸻

40. How would you define line of therapy in oncology RWD?

English Answer:
Line of therapy is usually defined based on treatment initiation, combination rules, gaps, additions, 
discontinuations, and switches. A new line may begin when a new systemic therapy is added
after a predefined window, when all agents in a regimen are discontinued and a new regimen starts, 
or when there is a clinically meaningful treatment switch. The exact algorithm should be prespecified and aligned with clinical input.

中文理解：
Line of therapy 通常根据治疗开始、联合用药规则、gap、加药、停药和换药定义。
新 line 可能开始于预设窗口后加入新系统治疗，
原方案全部停止后开始新方案，
或发生有临床意义的换药。
具体算法必须预先定义，
并和临床专家意见一致。

⸻

41. How would you define treatment discontinuation?

English Answer:
Treatment discontinuation can be defined as the absence of treatment after a prespecified gap period. 
For oral therapies, days supply can be used to estimate coverage and gaps. For infused therapies, 
administration dates are used. The gap length should be clinically meaningful and prespecified, 
such as 30, 60, or 90 days, depending on the treatment schedule and study context.

中文理解：
Treatment discontinuation 可以定义为超过预设 gap 后没有继续治疗。口服药可用 days supply 估计覆盖期和 gap；
输注药用 administration dates。Gap 长度要有临床意义并预先规定，比如 30、60 或 90 天，取决于治疗周期和研究背景。

⸻

42. What is real-world overall survival?

English Answer:
Real-world overall survival is the time from a defined index date, such as treatment initiation, 
to death from any cause using real-world data sources. The major challenge is accurate death capture. 
Death information may come from EHR, claims, registry, Social Security Death Index, obituary data,
or linked mortality databases. The reliability of the mortality source should be evaluated.

中文理解：
Real-world OS 是从某个 index date，比如治疗开始，到任何原因死亡的时间。主要挑战是死亡信息是否准确。
死亡数据可能来自 EHR、claims、registry、死亡数据库或其他链接来源。必须评估 mortality source 的可靠性。

⸻

43. What is real-world progression-free survival?

English Answer:
Real-world progression-free survival is more difficult to define than trial-based PFS 
because progression is not always systematically captured in routine care. It may be derived 
from clinician-documented progression, radiology reports, treatment changes, or abstraction from EHR. 
The definition should be transparent and validated when possible. Claims-only data is usually limited 
for directly identifying progression.

中文理解：
Real-world PFS 比临床试验 PFS 难定义，因为日常诊疗中 progression 不一定被系统记录。
它可能来自医生记录的 progression、影像报告、治疗改变或 EHR 抽取。定义必须透明，并尽量验证。
单独 claims 数据通常很难直接识别 progression。

⸻

44. How does your oncology trial programming experience help in oncology RWD?

English Answer:
My oncology trial programming experience helps me understand endpoint definitions, response criteria, 
safety outputs, censoring rules, treatment exposure, and analysis populations.
Although RWD is different from clinical trial data, the discipline of clear specifications, traceability, 
QC, and endpoint understanding is highly transferable. This allows me to implement oncology RWD algorithms 
with more clinical awareness.

中文理解：
我的肿瘤临床试验编程经验帮助我理解 endpoint definitions、response criteria、安全性输出、censoring rules、
treatment exposure 和 analysis populations。虽然 RWD 和临床试验数据不同，但清晰规格、可追溯、QC 和 endpoint 
理解是高度可迁移的。这让我能更有临床意识地实现肿瘤 RWD 算法。

⸻

G. Behavioral / Delivery / Communication

45. Tell me about a time you found a discrepancy during QC.

English Answer:
In a previous project, my validation result did not match the production output for a table. 
I first identified exactly where the discrepancy occurred, such as denominator, treatment group, 
or derived endpoint. Then I compared the specification, source data, derivation logic, and SAS log.
After tracing the issue, I found that the discrepancy came from a difference in population flag application. 
I documented the issue, discussed it with the team, corrected the logic, and reran both production and 
validation outputs. This experience reinforced the importance of systematic QC and clear specifications.

中文理解：
以前项目中，我的 validation 结果和 production output 不一致。我先定位差异在 denominator、treatment group 还是 
endpoint。然后比较 specification、source data、derivation logic 和 SAS log。
最后发现是 population flag 应用不同导致的。我记录问题，和团队沟通，修正逻辑，并重新跑 production 和 validation。
这说明系统性 QC 和清晰规格非常重要。

⸻

46. How do you handle unclear specifications?

English Answer:
When specifications are unclear, I first review the protocol, SAP, data dictionary, prior outputs, 
and related documentation. I then identify the exact ambiguity and propose possible interpretations
with pros and cons. Instead of making assumptions silently, I discuss the issue with the statistician, 
epidemiologist, or clinical lead. Once the decision is made, I document the clarification and apply it 
consistently in programming and QC.

中文理解：
如果规格不清楚，我会先看 protocol、SAP、data dictionary、历史输出和相关文档。然后明确哪里模糊，并提出可能解释及利弊。
我不会私自假设，而是和统计师、流行病学家或临床负责人讨论。决定后，我会记录 clarification，并在编程和 QC 中一致应用。

⸻

47. How do you manage tight timelines?

English Answer:
Under tight timelines, I prioritize tasks based on deliverable importance, risk, and dependencies.
I clarify requirements early, break the work into smaller milestones, and communicate progress and risks proactively.
I also focus QC on high-risk areas such as cohort definition, index date, treatment group, denominator,
and key endpoints. If timeline risks arise, I escalate early with proposed solutions rather than waiting 
until the deadline.

中文理解：
时间紧时，我会根据交付重要性、风险和依赖关系排序。尽早澄清需求，把工作拆成小节点，并主动沟通进展和风险。
QC 会重点放在高风险部分，比如 cohort definition、index date、treatment group、denominator 和 key endpoints。
如果有延期风险，我会提前升级并给出解决方案，而不是等到 deadline。

⸻

48. How do you communicate with non-programmers?

English Answer:
When communicating with non-programmers, I avoid technical jargon and focus on the business 
or scientific meaning of the issue. For example, instead of only saying there is a merge issue, 
I would explain how it affects patient counts, cohort eligibility, or outcome classification. 
I try to present options, implications, and recommended next steps clearly so that statisticians, clinicians, 
and project leads can make informed decisions.

中文理解：
和非程序员沟通时，我会避免过多技术术语，重点解释问题的业务或科学含义。比如我不会只说有 merge issue，
而会解释它如何影响 patient counts、cohort eligibility 或 outcome classification。我会清楚展示选项、影响和建议，
帮助统计师、临床专家和项目负责人做决定。

⸻

49. Why should we hire you?

English Answer:
You should hire me because I bring a rare combination of clinical background, oncology programming experience, 
RWD understanding, SAS/SQL skills, and strong QC discipline. I can understand the clinical question, 
translate it into data and programming specifications, build analysis-ready datasets, validate results,
and communicate findings clearly to cross-functional teams. For a Senior RWD Analyst/Programmer role at Amgen, 
I believe this combination would allow me to contribute quickly and reliably.

中文理解：
你们应该录用我，因为我有少见的组合：临床背景、肿瘤编程经验、RWD 理解、SAS/SQL 技能和强 QC 意识。我能理解临床问题，
把它转化为数据和编程规格，构建 analysis-ready datasets，验证结果，并清楚地和跨部门团队沟通。
对于 Amgen 这个 Senior RWD Analyst/Programmer 岗位，我相信这个组合能让我快速、可靠地贡献价值。

⸻

Final Memory Sentence

English:
My value is that I can understand the clinical question, translate it into RWD specifications, 
implement it with SAS/SQL, validate the results, and deliver high-quality evidence for pharma decision-making.

中文：
我的价值在于：我能理解临床问题，把它转化成 RWD 规格，用 SAS/SQL 实现，验证结果，并为药企决策交付高质量证据。

你考试或面试时不用逐字背，核心就抓住一句话：
clinical question 
→ RWD specification 
→ SAS/SQL implementation 
→ QC validation 
→ pharma delivery。
