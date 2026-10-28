## 01 基本信息

- **标题**：A Novel NR3C1 Frameshift Variant Associated With Familial Glucocorticoid Resistance Syndrome: An Integrated Analysis of Steroid Profiling and Structural Modeling
- **作者**：Yun, Sufang; Zhu, Zhifeng; Zhou, Fengye; Liu, Ying; Liang, Chunfang; Ju, Haitao; Lu, Lin; Yan, Zhaoli
- **单位**：未提供（PubMed 记录未列出单位信息）
- **期刊/平台**：American Journal of Medical Genetics. Part A
- **年份**：2026（在线日期 2026-07-24）
- **论文类型**：病例报告 + 家族遗传分析 + 整合生物信息学分析
- **领域**：罕见遗传病（糖皮质激素抵抗综合征，GRS）；NR3C1 基因变异；结构预测与功能推断
- **关键词**：glucocorticoid resistance syndrome; NR3C1; frameshift variant; steroid profiling; AlphaFold3; structural modeling
- **DOI/arXiv**：10.1002/ajmg.a.70230
- **代码**：未提供
- **数据**：未提供（变异数据未提交至公共数据库的明确信息未提供）
- **阅读日期**：2026-07-24（以 PubMed 收录日期为准）
- **在「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」方向中的位置**：本文以 NR3C1（编码糖皮质激素受体 GRα，一个配体依赖型转录因子）的致病性移码变异为对象，使用 AlphaFold3 预测野生型与突变型 GRα 蛋白结构，推断 N 端截短导致 DNA-binding domain（DBD）和 ligand-binding domain（LBD）缺失。该文属于「TF 结构变异 → 功能丧失 → 疾病表型」的临床-结构整合分析，其 AI 结构预测用于支持变异致病性解释，而非开发新方法。对本课题的可迁移点在于：AlphaFold3 用于 TF 结构域完整性评估的流程、以及「结构预测 + 表达分析 + 虚拟扰动」的整合分析框架。

---

## 02 一句话总结

本文报道一个 NR3C1 外显子 2 新移码变异 c.923dupG (p.Ala309Serfs*6)，通过类固醇代谢谱、ACMG/AMP 致病性评估、AlphaFold3 结构预测和 in silico 虚拟扰动分析，证明该变异导致 GRα 在 N 端反式激活域提前终止、丧失下游 DBD 和 LBD，与家族性糖皮质激素抵抗综合征（GRS）的激素表型共分离，并将该变异分类为致病性。

---

## 03 研究问题

- **具体问题**：一个表现为难治性高血压、无 Cushing 样体征、激素谱提示 ACTH 驱动的盐皮质激素前体累积的家系，其遗传病因是否为 NR3C1 新变异？该变异如何从结构层面导致 GRα 功能丧失？
- **为什么重要**：GRS 表型异质性大，常被误诊为原发性醛固酮增多症或亚临床 Cushing 综合征。识别新变异并建立基因型-表型关联，有助于改善诊断和心血管并发症风险评估。
- **现有方法为何不足**：单纯 Sanger 测序可鉴定变异，但难以解释 N 端截短变异的致病机制；常规 ACMG 评估缺乏结构层面的功能证据；既往 GRS 病例报告分散，缺乏系统性汇总。
- **精确研究问题（Can...?）**：Can AlphaFold3 结构预测结合类固醇谱和 ACMG 标准，为 NR3C1 外显子 2 移码变异提供足够的致病性证据，并解释其导致 GRS 的分子机制？

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论的叙述，标注为「仅本文框架」，未经外部系统核验。

1. **GRS 的临床认识阶段**：GRS 由 NR3C1 致病性变异引起，表现为糖皮质激素抵抗，ACTH 代偿性升高，导致盐皮质激素和雄激素前体累积。表型高度异质，从无症状到严重高血压、低钾血症。代表方法：临床激素测定、ACTH 兴奋试验。局限：表型谱宽，诊断延迟。
2. **NR3C1 变异谱系阶段**：既往报道的 GRS 变异分布于 GRα 各功能域（NTD、DBD、LBD），以错义变异为主，少数为截短变异。代表方法：Sanger 测序、功能报告基因实验。局限：功能实验耗时，部分变异未做功能验证。
3. **结构预测辅助变异解读阶段**：AlphaFold2/3 等 AI 结构预测工具被用于评估变异对蛋白结构的影响。代表方法：AlphaFold3 预测、pLDDT 评分、结构比对。优点：快速、无需纯化蛋白；局限：对 intrinsically disordered region（如 GRα NTD）的预测可信度有限，不能替代功能实验。
4. **本文主张的位置**：将 AlphaFold3 结构预测与类固醇代谢组学、单细胞/组织表达分析、in silico 虚拟基因扰动、系统文献综述整合，形成「临床-生化-遗传-结构-通路」多层级证据链，为 N 端截短变异提供综合致病性评估框架。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| GRS 表型异质性导致误诊 | 患者被误诊为原发性醛固酮增多症或亚临床 Cushing 综合征 | 激素谱重叠，临床医生对 GRS 认识不足 | 摘要「frequent misdiagnosis as primary aldosteronism or subclinical Cushing's syndrome」 |
| N 端截短变异的致病机制不明确 | 移码变异导致 NTD 提前终止，难以用常规功能实验解释 | 截短蛋白可能不稳定或无法表达，传统实验难以捕获 | 摘要「premature termination within the N-terminal transactivation domain, supporting loss of the downstream DNA-binding and ligand-binding domains」 |
| 变异致病性评估缺乏结构证据 | ACMG 标准中结构预测证据权重有限 | 结构预测工具（如 AlphaFold3）在临床变异解读中的应用尚未标准化 | 摘要「Variant pathogenicity was assessed following ACMG/AMP criteria」；结构预测作为支持证据 |
| 心血管并发症与基因型关系不明 | 部分 N 端或截短变异携带者出现心血管事件 | 样本量小，机制假说未验证 | 摘要「cardiovascular events documented in some carriers of N-terminal or truncating variants... remains hypothesis-generating」 |

---

## 06 核心思想

### 1) 表面方法
对一个 GRS 家系进行临床表型刻画、类固醇代谢谱分析、肾上腺 CT、Sanger 测序验证 NR3C1 变异、家系共分离分析；用 AlphaFold3 预测野生型与突变型 GRα 结构；用 GTEx 等数据库分析 NR3C1 组织表达和单细胞表达；用 in silico 虚拟基因敲除（virtual knockout）分析推测受影响通路；系统文献综述汇总既往 GRS 病例。

### 2) 核心洞察
- **结构域完整性是 GRα 功能的前提**：NTD 内的移码变异导致提前终止，使下游 DBD 和 LBD 完全缺失，从结构上解释了配体结合和 DNA 结合能力的丧失，而非仅仅影响单个功能残基。
- **激素谱是 GRS 的「生化指纹」**：ACTH 升高 + 盐皮质激素前体（11-deoxycorticosterone、11-deoxycortisol）累积 + 肾素抑制，构成区别于原发性醛固酮增多症的特征性模式。
- **多层级证据整合优于单一证据**：结构预测、表达分析、虚拟扰动和文献汇总各自有局限，但整合后可形成更强的致病性论证。

### 3) 可能的普适教训 [Analysis]
- 对 TF 编码基因的截短变异，结构预测应关注「结构域是否完整保留」而非仅看局部残基扰动；AlphaFold3 对多结构域蛋白的预测可快速判断截短是否破坏关键功能域。
- 对转录因子相关疾病，激素/代谢物谱可作为「功能读出」（functional readout），弥补结构预测和遗传证据的不足。
- in silico 虚拟基因扰动（如基于表达数据的敲除模拟）可用于生成通路层面的假说，但需明确其 exploratory 性质。

---

## 07 方法总览

- **输入**：
  - 临床数据：先证者及其父亲的表型、激素测定、肾上腺 CT
  - 遗传数据：Sanger 测序获得的 NR3C1 变异
  - 序列数据：NR3C1 野生型与突变型蛋白序列
  - 表达数据：GTEx 等组织的 NR3C1 表达数据、单细胞表达数据
  - 文献数据：既往 GRS 病例报告
- **输出**：
  - 变异致病性分类（ACMG/AMP：pathogenic）
  - 野生型与突变型 GRα 的预测结构
  - NR3C1 组织/细胞类型表达图谱
  - 虚拟敲除影响的通路列表
  - 66 例既往 GRS 病例汇总表
- **模块**：
  1. 临床与生化表型刻画
  2. 遗传学分析与共分离
  3. AlphaFold3 结构预测
  4. 组织/单细胞表达分析
  5. in silico 虚拟基因敲除
  6. 系统文献综述
- **训练**：不适用（无模型训练；AlphaFold3 为预训练模型，直接推理）
- **工具**：AlphaFold3（结构预测）；GTEx 或类似数据库（表达分析）；虚拟敲除工具（具体工具名未提供）；ACMG/AMP 指南（变异分类）
- **反馈回路**：无显式反馈回路；各模块结果在讨论中整合
- **文字流程**：先证者因难治性高血压就诊 → 激素谱提示 ACTH 升高、盐皮质激素前体累积 → 肾上腺 CT 排除肿瘤 → Sanger 测序发现 NR3C1 c.923dupG → 家系共分离验证 → AlphaFold3 预测野生型/突变型 GRα 结构 → 分析 NR3C1 组织与单细胞表达 → 虚拟敲除推测受影响通路 → 系统文献综述对比既往病例 → 综合评估变异致病性并分类。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 临床与生化表型刻画 | 明确 GRS 的激素特征 | 区分 GRS 与原发性醛固酮增多症、Cushing 综合征 | 输入：临床检查、激素测定；输出：表型谱 | 摘要「steroid profiling demonstrated mild hypercortisolemia with elevated ACTH, marked increases in 11-deoxycorticosterone and 11-deoxycortisol, suppressed renin, and low-to-normal aldosterone」 | 移除后无法建立表型-基因型关联，诊断依据不足 |
| 遗传学分析与共分离 | 鉴定并验证 NR3C1 变异 | 确认变异的致病性遗传学证据 | 输入：家系 DNA；输出：变异位点、共分离结果 | 摘要「co-segregating with the familial phenotype」 | 移除后变异与疾病的因果关系无法确立 |
| AlphaFold3 结构预测 | 预测野生型与突变型 GRα 结构 | 从结构层面解释截短变异的功能后果 | 输入：蛋白序列；输出：预测结构 | 摘要「AlphaFold3 was used to predict the structures of wild-type and mutant GRalpha proteins」 | 移除后缺乏结构层面的致病性支持证据 [预期效应，未做消融] |
| 组织/单细胞表达分析 | 明确 NR3C1 的表达分布 | 评估变异影响的组织特异性 | 输入：表达数据库；输出：表达图谱 | 摘要「tissue- and single-cell-level expression analyses」 | 移除后无法讨论组织特异性效应 [预期效应，未做消融] |
| in silico 虚拟基因敲除 | 推测 NR3C1 功能丧失影响的通路 | 生成通路层面的探索性假说 | 输入：表达数据；输出：受影响通路列表 | 摘要「in silico virtual knockout analysis was performed to generate exploratory hypotheses」 | 移除后失去通路层面的假说，但该模块本身为 exploratory，影响有限 [作者明确标注 exploratory] |
| 系统文献综述 | 汇总既往 GRS 病例 | 对比新变异与已知变异谱 | 输入：文献数据库；输出：66 例病例汇总 | 摘要「systematic review was conducted to summarize previously reported GRS cases」 | 移除后无法评估新变异的表型谱位置 |

---

## 09 关键公式符号

不适用。本文为临床病例报告与结构预测分析，未涉及定量模型或数学公式。ACMG/AMP 评分标准为规则性框架而非公式，未在摘要中给出具体评分细则。

---

## 10 实验设计与证据链

- **数据集/群体**：一个 GRS 家系，两代两名受累男性（先证者及其父亲）
- **规模**：家系 n=2 受累个体；文献综述 n=66 例既往 GRS 病例
- **指标**：激素水平（皮质醇、ACTH、11-deoxycorticosterone、11-deoxycortisol、肾素、醛固酮）、肾上腺 CT 影像、Sanger 测序结果、AlphaFold3 结构预测、表达数据、虚拟敲除通路
- **基线**：无明确基线；文献综述提供既往病例表型谱作为参照
- **预算**：未提供
- **骨干/仪器**：未提供（临床检测平台未说明）
- **oracle 输入**：不适用（无监督学习或预测任务）
- **评测协议**：ACMG/AMP 变异致病性分类标准；共分离分析；结构预测结果与已知 GRα 结构域边界比对

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 激素谱分析 | 先证者存在 GRS 特征性激素异常 | 与典型 GRS 激素谱对比 | 轻度皮质醇升高、ACTH 升高、11-deoxycorticosterone 和 11-deoxycortisol 显著升高、肾素抑制、醛固酮低-正常 | 符合 ACTH 驱动的盐皮质激素前体累积模式 | 不能区分 GR 部分抵抗与完全抵抗的程度 | 摘要「Steroid profiling demonstrated...」 |
| Sanger 测序与共分离 | c.923dupG 与 GRS 表型共分离 | 家系内受累/未受累成员 | 两代受累男性均携带该变异 | 变异与疾病共分离 | 未提供未受累成员携带情况，无法排除不完全外显 | 摘要「co-segregating with the familial phenotype」 |
| AlphaFold3 结构预测 | 截短变异导致 GRα 功能域缺失 | 野生型 vs 突变型 GRα 结构 | 突变型在 NTD 内提前终止，DBD 和 LBD 缺失 | 结构层面支持功能丧失 | 结构预测不能替代功能实验；NTD 为无序区域，预测可信度有限 | 摘要「premature termination within the N-terminal transactivation domain」 |
| 虚拟基因敲除 | NR3C1 功能丧失影响特定通路 | 敲除 vs 未敲除表达谱 | 提示神经内分泌通讯、细胞外基质调控、蛋白翻译、发育通路受影响 | 生成探索性假说 | 虚拟敲除为 in silico 推断，未经实验验证 | 摘要「in silico virtual knockout analysis... exploratory hypotheses」 |
| 系统文献综述 | 新变异扩展 GRS 基因型-表型谱 | 与 66 例既往病例对比 | 新变异为 novel frameshift，表型与既往 N 端/截短变异部分重叠 | 扩展已知变异谱 | 样本量小，无法做统计关联分析 | 摘要「systematic review... 66 reported GRS cases」 |

---

## 11 结论正确解读

- **任务范围**：本文是单家系病例报告 + 生物信息学整合分析，非前瞻性队列研究或功能实验研究。结论的适用范围限于该家系及类似表型患者。
- **oracle/真值输入**：无监督学习任务；结构预测以 AlphaFold3 输出为「预测结构」，非实验解析结构（如 X-ray、Cryo-EM）。
- **端到端状态**：非端到端。变异致病性结论依赖多模块整合，各模块独立完成，无统一 pipeline 或自动化流程。
- **算力成本**：未提供。AlphaFold3 推理成本未说明。
- **历史数据依赖**：文献综述依赖既往发表的 GRS 病例，可能存在发表偏倚；表达分析依赖公共数据库（如 GTEx），其覆盖组织/细胞类型有限。
- **模型依赖**：结构预测结论依赖 AlphaFold3 的准确性；对 GRα NTD（intrinsically disordered）的预测可信度需谨慎。
- **最难情形**：无功能实验验证（如报告基因、western blot 检测蛋白表达），无法确认截短蛋白是否表达、是否具有显性负效应或单倍剂量不足。
- **群体/领域边界**：结论限于 NR3C1 相关 GRS；不能推广至其他 TF 相关疾病。
- **不确定性**：心血管并发症与 N 端截短变异的关联为假说生成性质，作者明确标注需更大样本和功能研究验证。

**有边界的复述**：在一个两代受累家系中，NR3C1 c.923dupG (p.Ala309Serfs*6) 与 GRS 激素表型共分离，AlphaFold3 预测该变异导致 GRα 在 NTD 内提前终止、丧失 DBD 和 LBD，ACMG/AMP 分类为 pathogenic；该变异与心血管并发症的关联为探索性假说，需功能实验和大样本验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 心血管并发症关联为假说 | N 端/截短变异与心血管事件的关系「remains hypothesis-generating」 | 需更大样本队列和功能研究验证 | 摘要「The potential relationship between N-terminal truncating variants and cardiovascular complications remains hypothesis-generating and requires validation in larger cohorts and functional studies」 |
| 虚拟敲除为探索性 | in silico 虚拟基因敲除用于生成假设，非验证性 | 需实验验证受影响通路 | 摘要「in silico virtual knockout analysis was performed to generate exploratory hypotheses」 |
| 结构预测替代功能实验 | AlphaFold3 预测支持致病性，但未做体外功能实验 | 未明确提及，但隐含需功能验证 | 摘要整体框架暗示结构预测为支持性证据 |

> 注：以上为摘要中明确或隐含的作者自认局限。全文可能包含更多局限说明，但摘要未提供。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| AlphaFold3 对 NTD 无序区域的预测可信度有限 | GRα NTD 为 intrinsically disordered region，AlphaFold3 对无序区域的预测可能不可靠；截短蛋白可能根本不表达（nonsense-mediated decay） | 结构预测结论可能高估了「结构域缺失」的解释力 | 用 western blot 检测患者细胞中 GRα 蛋白表达；用报告基因实验验证转录激活功能 | 摘要未提供蛋白表达或功能实验数据 |
| 共分离证据仅基于两名受累个体 | 家系规模小，未提供未受累成员基因型信息，无法排除不完全外显或修饰基因影响 | 共分离是致病性论证的关键遗传学证据，样本量小削弱证据强度 | 扩大家系或收集更多独立家系验证 | 摘要「Two affected males across successive generations」 |
| 虚拟敲除的生物学解释力未验证 | 基于表达数据的虚拟敲除可能反映间接效应或组织混杂，而非 NR3C1 直接调控 | 通路假说可能误导后续研究方向 | 用 ChIP-seq 或 CUT&Tag 验证 NR3C1 直接结合靶基因；用 siRNA/CRISPR 敲低实验验证通路变化 | 摘要明确标注为 exploratory |
| 激素谱与原发性醛固酮增多症的区分度未量化 | 摘要描述激素特征，但未给出区分 GRS 与原发性醛固酮增多症的敏感性/特异性指标 | 临床鉴别诊断价值需量化 | 收集 GRS 与原发性醛固酮增多症队列，比较激素谱的判别效能 | 摘要未提供统计比较数据 |
| 文献综述的纳入标准未说明 | 66 例病例的检索策略、纳入排除标准、质量评估未在摘要中呈现 | 综述结论的可重复性和偏倚风险无法评估 | 查阅全文 Methods 部分 | 摘要未提供综述方法细节 |

---

## 14 学到什么

> Agent 提炼的知识候选

1. **AlphaFold3 用于 TF 截短变异的结构域完整性评估**：对转录因子编码基因的移码/无义变异，可用 AlphaFold3 预测突变型蛋白结构，快速判断是否导致关键功能域（DBD、LBD）缺失。**可迁移到本课题**：对 TF–DNA 结合机制研究，当遇到新发截短变异时，可先用 AlphaFold3 做结构域完整性筛查，再决定是否进行深度功能实验。

2. **激素/代谢物谱作为 TF 功能丧失的「生化读出」**：GRS 的激素谱（ACTH 升高 + 盐皮质激素前体累积 + 肾素抑制）提供了 GRα 功能丧失的体内证据。**可迁移到本课题**：在研究 TF–DNA 结合变异的功能后果时，可寻找对应的下游生化标志物（如靶基因表达产物、代谢物），作为变异功能影响的体内读出。

3. **多层级证据整合框架**：临床表型 + 遗传共分离 + 结构预测 + 表达分析 + 虚拟扰动 + 文献综述的整合模式，可增强单一家系变异致病性论证的强度。**可迁移到本课题**：对 TF 变异的功能评估，可建立类似的「序列-结构-表达-通路-表型」多层级证据链。

4. **in silico 虚拟基因敲除作为假设生成工具**：基于表达数据的虚拟敲除可快速生成 TF 功能丧失影响的通路假说。**可迁移到本课题**：在研究 TF–DNA 结合机制时，可用虚拟敲除预测 TF 下游调控网络，再用 ChIP-seq 或报告基因验证。

5. **TF 无序区域（NTD）变异的解读需谨慎**：GRα NTD 为 intrinsically disordered region，结构预测对其可信度有限。**可迁移到本课题**：对 TF 无序区域的变异，应优先考虑功能实验而非仅依赖结构预测。

6. **ACMG/AMP 框架中结构预测证据的定位**：结构预测在 ACMG/AMP 中作为支持性证据（PP3/BP4），不能单独决定致病性分类。**可迁移到本课题**：在 TF 变异致病性评估中，结构预测应与其他证据（共分离、功能实验、人群频率）整合。

---

## 15 与已有知识连接

- **NR3C1/GR 结构与功能**：GRα 包含 NTD（含 AF-1 反式激活域）、DBD（含两个锌指结构）、铰链区和 LBD（含 AF-2）。本文移码变异位于 NTD，导致 DBD 和 LBD 缺失，与已知 GR 结构域功能模型一致（可参考 Hollenberg et al., 1987; Giguère et al., 1986 关于 GR 结构域功能的经典研究）。
- **GRS 基因型-表型关联**：既往 GRS 变异以错义变异为主（如 DBD 的 R477H、LBD 的 V729I 等），截短变异相对少见。本文补充了 NTD 截短变异的新案例（可参考 Charmandari et al., 2008 的 GRS 综述；Nicolaides et al., 2015 的 NR3C1 变异数据库）。
- **AlphaFold 在变异解读中的应用**：AlphaFold2/3 已被用于错义变异的结构影响预测（如 Jumper et al., 2021; Abramson et al., 2024）。本文将其扩展到截短变异的结构域完整性评估，与 ClinGen 序列变异解读中结构预测证据的使用方向一致。
- **糖皮质激素抵抗与盐皮质激素前体累积**：ACTH 升高导致肾上腺皮质增生和盐皮质激素前体（11-deoxycorticosterone、11-deoxycortisol）累积，是 GRS 区别于原发性醛固酮增多症的关键机制（可参考 Chrousos et al., 1983 的经典描述）。
- **TF 相关疾病的结构-功能整合分析**：本文的「临床-遗传-结构-通路」整合框架，与肿瘤中 TF 融合蛋白或截短变异的功能评估思路相似（如 p53 截短变异的功能评估，可参考 Olivier et al., 2010）。

---

## 16 研究想法

> Agent 生成的研究候选

### 候选 1：TF 截短变异的结构域完整性自动评估流程
- **名称**：TF-Truncation-Domain-Integrity (TF-TDI) Pipeline
- **来源局限/观察**：本文用 AlphaFold3 手动评估 GRα 截短变异，但缺乏自动化、可扩展的流程；对无序区域（NTD）的预测可信度未量化。
- **核心假设**：对任意 TF 编码基因的移码/无义变异，可通过 AlphaFold3 预测 + 结构域边界比对 + pLDDT 置信度加权，自动判断是否导致关键功能域（DBD、LBD、其他已知功能域）缺失，并输出致病性支持证据。
- **相对本文的增量**：将手动分析流程化为可复现的 pipeline；加入无序区域置信度校正；可批量处理多个变异。
- **初步方法**：收集 ClinVar 中 TF 基因截短变异 → 提取蛋白序列 → AlphaFold3 预测突变型结构 → 与 Pfam/UniProt 结构域边界比对 → 计算功能域保留比例 → 与已知致病性标注做 ROC 分析。
- **验证方式**：在已知致病/良性 TF 截短变异数据集上评估分类性能；与功能实验数据（如报告基因）对比。
- **可能的失败模式**：AlphaFold3 对无序区域预测不可靠导致误判；截短蛋白可能被 NMD 降解，结构预测失去意义。
- **创新状态**：unverified

### 候选 2：GRS 激素谱的判别诊断模型
- **名称**：GRS-Steroid-Fingerprint Classifier
- **来源局限/观察**：本文指出 GRS 常被误诊为原发性醛固酮增多症或亚临床 Cushing 综合征，但未量化激素谱的判别能力。
- **核心假设**：GRS 患者的类固醇代谢组学谱（ACTH、皮质醇、11-deoxycorticosterone、11-deoxycortisol、醛固酮、肾素等）构成区别于原发性醛固酮增多症和 Cushing 综合征的特征性指纹，可用于机器学习分类。
- **相对本文的增量**：将定性描述转化为定量诊断模型。
- **初步方法**：收集 GRS、原发性醛固酮增多症、亚临床 Cushing 综合征患者的类固醇谱数据 → 特征工程 → 训练随机森林/XGBoost 分类器 → 交叉验证评估 AUC。
- **验证方式**：独立验证队列；与临床诊断标准对比。
- **可能的失败模式**：样本量小（GRS 极罕见）；不同实验室检测平台差异导致特征不可比。
- **创新状态**：unverified

### 候选 3：TF 截短变异的显性负效应 vs 单倍剂量不足判别
- **名称**：TF-Dominant-Negative-Predictor
- **来源局限/观察**：本文 GRα 截短变异可能产生截短蛋白，但未讨论其是否具有显性负效应（干扰野生型等位基因功能）或仅为单倍剂量不足。
- **核心假设**：TF 截短变异的作用模式（显性负效应 vs 单倍剂量不足）可通过截短位置、保留的结构域、蛋白-蛋白相互作用界面等信息预测。
- **相对本文的增量**：为 TF 截短变异的功能后果提供机制层面的区分。
- **初步方法**：收集已知作用模式的 TF 截短变异 → 提取截短位置、保留结构域、相互作用界面特征 → 训练分类器 → 与功能实验数据对比。
- **验证方式**：在 GR 及其他核受体家族（如 AR、ER）中验证。
- **可能的失败模式**：作用模式可能依赖细胞类型和配体环境，单一模型难以泛化。
- **创新状态**：unverified

### 候选 4：AlphaFold3 预测 TF–DNA 结合界面破坏的评估框架
- **名称**：TF-DNA-Interface-Integrity-Score
- **来源局限/观察**：本文仅用 AlphaFold3 预测蛋白单体结构，未评估变异对 TF–DNA 结合界面的直接影响；对 DBD 内错义变异，界面破坏是关键机制。
- **核心假设**：AlphaFold3 可预测 TF–DNA 复合物结构，通过比较野生型与突变型复合物的界面接触变化，量化变异对 DNA 结合的影响。
- **相对本文的增量**：将结构预测从「结构域完整性」扩展到「DNA 结合界面完整性」。
- **初步方法**：选取已知 DBD 错义变异的 TF（如 GR、p53、GATA3）→ AlphaFold3 预测 TF–DNA 复合物 → 计算界面接触残基变化 → 与实验结合亲和力数据对比。
- **验证方式**：在已知结合亲和力变化的变异数据集上评估预测准确性。
- **可能的失败模式**：AlphaFold3 对 TF–DNA 复合物预测精度有限；DNA 序列依赖性结合难以建模。
- **创新状态**：unverified