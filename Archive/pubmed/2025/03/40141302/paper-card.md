## 01 基本信息

- **标题**：Noradrenaline Synergistically Enhances Porphyromonas gingivalis LPS and OMV-Induced Interleukin-1beta Production in BV-2 Microglia Through Differential Mechanisms
- **作者**：Muramoto, Sakura; Shimizu, Sachi; Shirakawa, Sumika; Ikeda, Honoka; Miyamoto, Sayaka; Jo, Misato; Takemori, Uzuki; Morimoto, Chiharu; Wu, Zhou; Tozaki-Saitoh, Hidetoshi; Oda, Kosuke; Inoue, Erika; Nonaka, Saori; Nakanishi, Hiroshi
- **单位**：未提供（推测为日本安田女子大学药学部等，但原文未明确列出全部单位）
- **期刊/平台**：International Journal of Molecular Sciences
- **年份**：2025
- **论文类型**：实验研究（in vitro）
- **领域**：神经免疫学、微生物致病机制、炎症信号转导
- **关键词**：noradrenaline；Porphyromonas gingivalis；IL-1β；microglia；NF-κB；AP-1；TLR9；OMV
- **DOI/arXiv 号**：10.3390/ijms26062660
- **代码**：未提供
- **数据**：未提供（原始数据未公开）
- **阅读日期**：2026-05-13（系统日期）
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：本文并非直接研究TF-DNA结合机制，但涉及转录因子NF-κB p65与AP-1 c-Fos的协同DNA结合调控IL-1β表达，并使用AlphaFold2预测p65:p50:c-Fos三元复合物结构。对本课题的可迁移点在于：(1) 转录因子间的物理互作（c-Fos与p65）如何增强DNA结合亲和力；(2) AlphaFold2用于预测TF-TF互作复合物的方法学；(3) 不同病原刺激（LPS vs OMV）激活不同TF通路的差异化机制。

---

## 02 一句话总结

本文发现去甲肾上腺素（NA）通过β2肾上腺素受体（Aβ2R）通路，分别与牙龈卟啉单胞菌（Pg）的LPS和OMV协同作用，经不同机制（LPS依赖NF-κB p65与AP-1 c-Fos的物理互作；OMV依赖TLR9/p52/RelB通路）将BV-2小胶质细胞IL-1β的产生量提升至单独刺激的10–20倍。

---

## 03 研究问题

- **具体问题**：NA（应激相关神经递质）是否能增强Pg毒力因子（LPS和OMV）诱导的小胶质细胞IL-1β产生？其分子机制是什么？
- **为什么重要**：Pg感染与多种慢性炎症性疾病（包括阿尔茨海默病）相关，而抑郁/应激与炎症水平升高相关。理解NA如何调节Pg诱导的神经炎症，可为应激加剧牙周炎相关全身疾病的机制提供线索。
- **现有方法为何不足**：此前研究多关注Pg LPS或OMV单独激活小胶质细胞的机制，未考虑应激状态下NA的调节作用；且LPS与OMV的TLR激活谱不同（TLR2 vs TLR9），其与NA的协同机制可能不同。
- **精确的"Can..."问题**：Can noradrenaline synergistically enhance Pg LPS- and OMV-induced IL-1β production in BV-2 microglia through distinct signaling mechanisms?

---

## 04 背景与发展脉络

*注：以下脉络基于本文引言及讨论，属「仅本文框架」，未经外部系统核验。*

1. **阶段一：Pg作为牙周病原体与全身疾病关联**（~2000s-2010s）
   - 代表方法：流行病学关联研究
   - 发现：Pg感染与糖尿病、类风湿关节炎、AD相关
   - 局限：机制不清

2. **阶段二：Pg毒力因子激活先天免疫**（~2010s-2020s）
   - 代表方法：细胞培养+TLR激动剂/抑制剂
   - 发现：Pg LPS是弱TLR2/4激动剂；OMV含LPS、菌毛、DNA/RNA，可被吞噬后激活胞内TLR
   - 局限：未考虑宿主神经内分泌调节

3. **阶段三：应激-神经炎症轴**（~2015s-至今）
   - 代表方法：肾上腺素受体激动剂/拮抗剂+炎症因子检测
   - 发现：NA通过Aβ2R/Epac激活AP-1，诱导IL-1β
   - 局限：未与病原体刺激联合研究

4. **本文位置**：首次将NA与Pg毒力因子联合研究，揭示协同机制，并引入AlphaFold2预测TF复合物结构。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Pg LPS单独刺激IL-1β能力弱 | Pg LPS是弱TLR2/4激动剂，诱导IL-1β水平低 | Pg LPS脂质A酰基链和磷酸基团少于E. coli LPS，TLR激活效力低 | 引言第1段 |
| NA单独刺激IL-1β能力有限 | NA单独处理诱导的IL-1β水平远低于联合处理 | NA主要通过Aβ2R/Epac激活AP-1，单独激活不足以高效驱动IL-1β转录 | Results 图1D |
| 协同机制不明确 | LPS与OMV的协同机制不同，但此前未区分 | LPS经TLR2→NF-κB p65；OMV经吞噬→TLR9→p52/RelB，两条通路与NA的交叉点不同 | Results 图4-6 |
| 转录因子协同的分子基础不清 | NF-κB与AP-1如何物理协同增强DNA结合 | c-Fos与p65直接互作，增强p65与κB位点的结合 | Results 图7-8；Discussion |
| 传统结构方法难以捕捉TF-TF-DNA三元复合物 | 缺乏高分辨率结构数据 | AlphaFold2可预测p65:p50:c-Fos复合物结构 | Results 图8；Methods 4.9 |

---

## 06 核心思想

### 1) 表面方法
- 使用BV-2小胶质细胞系，以NA（30–1000 nM）与Pg LPS（10 μg/mL）或OMV（150 μg蛋白/mL）单独或联合处理
- 检测IL-1β mRNA（qPCR）、启动子活性（NanoLuc报告基因）、蛋白水平（Western blot）
- 使用药理学抑制剂：ICI-118551（Aβ2R拮抗剂）、wedelolactone（IKK抑制剂）、NAI（NF-κB抑制剂）、U0126（MEK抑制剂）、SR11302（AP-1抑制剂）、E6446（TLR9抑制剂）、SN52（p52抑制剂）
- 用AlphaFold2预测p65:p50:c-Fos三元复合物结构

### 2) 核心洞察
- **NA与Pg毒力因子通过不同机制协同**：LPS通路依赖NF-κB p65与AP-1 c-Fos的物理互作（c-Fos直接结合p65，增强p65与DNA的结合）；OMV通路依赖TLR9/p52/RelB，NA通过Aβ2R/Epac促进吞噬体成熟，增强OMV的胞内TLR9信号
- **转录因子间的物理互作可替代DNA结合位点的协同**：c-Fos不直接结合IL-1β启动子的κB位点，而是通过蛋白-蛋白互作增强p65的DNA结合能力

### 3) 可能的普适教训 [Analysis]
- 转录因子协同不一定需要两个TF都直接结合DNA——一个TF通过蛋白-蛋白互作"招募"或"稳定"另一个TF的DNA结合，是增强转录输出的有效策略
- 同一配体（NA）可通过不同节点（转录因子互作 vs 吞噬体成熟）增强不同病原刺激的炎症反应，提示"协同"的机制高度依赖刺激物的细胞进入途径
- AlphaFold2可用于快速生成TF-TF互作复合物的结构假设，为设计突变实验（验证互作界面）提供起点

---

## 07 方法总览

- **输入**：BV-2小胶质细胞；刺激物：NA（30–1000 nM）、Pg LPS（10 μg/mL）、Pg OMV（150 μg蛋白/mL）；抑制剂（浓度见各图）
- **输出**：IL-1β mRNA水平（qPCR）、IL-1β启动子活性（NanoLuc RLU）、IL-1β蛋白（Western blot）、p65-c-Fos互作（Co-IP）、p65:p50:c-Fos复合物结构（AlphaFold2）
- **模块**：
  1. 细胞培养与刺激
  2. qPCR检测mRNA
  3. NanoLuc报告基因检测启动子活性
  4. Western blot检测IL-1β蛋白
  5. Co-IP检测p65-c-Fos互作
  6. AlphaFold2结构预测
- **训练**：不适用（无机器学习训练）
- **工具**：GraphPad Prism 8（统计）、AlphaFold2/ColabFold（结构预测）
- **反馈回路**：无（单轮实验设计）
- **文字流程**：BV-2细胞培养 → 药物处理（NA±LPS/OMV±抑制剂）→ 收获细胞 → 分别进行qPCR/NanoLuc/Western/Co-IP → 统计分析 → AlphaFold2预测复合物结构 → 整合机制模型

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| qPCR检测IL-1β mRNA | 定量转录水平变化 | 确认协同效应发生在转录层面 | 输入：cDNA；输出：相对mRNA量 | Results 图1A-C | 无法区分转录vs转录后调控 |
| NanoLuc报告基因 | 检测IL-1β启动子活性 | 确认协同效应在启动子水平 | 输入：Nluc报告细胞；输出：RLU | Results 图1D-F, 图2 | 无法反映内源染色质环境 |
| 药理学抑制剂组合 | 解析信号通路 | 区分NF-κB、AP-1、TLR9、Aβ2R的贡献 | 输入：抑制剂+刺激；输出：RLU变化 | Results 图4-6 | 抑制剂特异性有限，可能有脱靶效应 |
| Co-IP + Western | 检测p65-c-Fos物理互作 | 验证转录因子直接结合 | 输入：细胞裂解液；输出：互作条带 | Results 图7B,C | 无法区分直接/间接互作 |
| AlphaFold2结构预测 | 生成p65:p50:c-Fos复合物模型 | 提供结构假设，解释互作如何增强DNA结合 | 输入：氨基酸序列；输出：PDB结构 | Results 图8 | 预测模型未经实验验证（如突变体） |
| 免疫测定（Lumit） | 定量IL-1β蛋白 | 确认蛋白水平协同 | 输入：细胞裂解液；输出：IL-1β浓度 | Results 图3A,B | 仅检测总IL-1β，未区分pro/成熟形式 |

**消融效应区分**：药理学抑制剂实验为「实测消融效应」；AlphaFold2模型移除后的影响为「预期效应」（无法直接实验验证）。

---

## 09 关键公式符号

本文为实验生物学论文，无数学公式。唯一涉及的计算为：

- **相对mRNA表达量**：`2^(-ΔΔCt)`（qPCR相对定量，Methods 4.5提及校准曲线法，未给出具体公式）
- **统计检验**：one-way ANOVA with Tukey's post hoc test（Methods 4.10）

**不适用**——本文无需要列出的关键公式。

---

## 10 实验设计与证据链

### 数据集/群体/规模
- 细胞系：BV-2小鼠小胶质细胞系（永生化）
- 刺激物浓度：NA 30–1000 nM；Pg LPS 10 μg/mL（部分实验30 μg/mL）；OMV 150 μg蛋白/mL
- 抑制剂：ICI-118551（0.1 μM）、wedelolactone（30 μM）、NAI（100 nM）、U0126（15 μM）、SR11302（10 μM）、E6446（浓度未明确）、SN52（浓度未明确）
- 指标：IL-1β mRNA（qPCR）、NanoLuc RLU、IL-1β蛋白（Western/Lumit）
- 时间点：mRNA峰值1h，6h内回落（图2）
- 重复次数：未明确（图注未提供n值）
- 统计：one-way ANOVA + Tukey's post hoc，p<0.05

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| 剂量-反应（图1A-C） | NA增强Pg LPS/OMV诱导的IL-1β mRNA | NA 30-1000 nM ± LPS/OMV vs 单独处理 | 联合处理mRNA达单独处理的9-12.8倍 | NA与Pg毒力因子协同增强IL-1β转录 | 未检测蛋白水平是否同步 | Results 2.1 |
| 报告基因实验（图1D-F） | 协同效应在启动子水平 | NA±LPS/OMV vs 单独 | 联合处理RLU达单独处理的22.3倍（LPS）和29.7倍（OMV） | 协同效应至少部分在转录水平 | 未排除mRNA稳定性贡献 | Results 2.2 |
| 时间过程（图2） | 协同效应的时间特征 | 0.5-6h时间点 | 峰值1h，6h回落 | 协同不改变动力学特征 | 未检测更长时间点 | Results 2.2 |
| 蛋白水平（图3A,B） | 协同效应在蛋白水平 | NA+LPS/OMV vs 单独 | IL-1β蛋白增加10倍（LPS）和20倍（OMV） | 转录协同转化为蛋白产出 | 未检测分泌vs胞内 | Results 2.3 |
| Western blot（图3C,D） | pro-IL-1β和成熟IL-1β的变化 | 联合vs单独 | 33kDa pro-IL-1β和17kDa成熟IL-1β均增加；OMV组出现20kDa形式 | LPS和OMV通路产生不同IL-1β加工形式 | 20kDa形式功能未验证 | Results 2.3 |
| 抑制剂实验（图4） | NF-κB通路参与 | wedelolactone/NAI ± 刺激 | wedelolactone完全抑制LPS+NA；NAI抑制80%；两者对OMV+NA无效 | LPS+NA依赖NF-κB；OMV+NA不依赖 | 抑制剂可能有脱靶效应 | Results 2.4 |
| 抑制剂实验（图5） | AP-1通路参与 | U0126/SR11302 ± 刺激 | U0126和SR11302抑制LPS+NA约20%；对OMV+NA无效 | AP-1部分参与LPS+NA；不参与OMV+NA | 抑制程度低，可能非主要机制 | Results 2.4 |
| 抑制剂实验（图6A-D） | Aβ2R参与 | ICI-118551 ± 刺激 | 高浓度NA（3μM）时ICI-118551抑制NA单独效应；对联合效应抑制不显著 | Aβ2R部分介导NA效应 | 低浓度NA时Aβ2R作用不明确 | Results 2.5 |
| 抑制剂实验（图6E,F） | TLR9/p52参与OMV通路 | E6446/SN52 ± OMV | 两者均显著抑制OMV和OMV+NA诱导的IL-1β | OMV经TLR9/p52/RelB通路 | 未检测吞噬体成熟直接证据 | Results 2.5 |
| Co-IP（图7B,C） | p65与c-Fos物理互作 | 抗p65 IP后检测c-Fos | 联合处理后c-Fos与p65共沉淀 | NA+LPS诱导p65-c-Fos复合物形成 | 未做定量比较 | Results 2.6 |
| AlphaFold2（图8） | p65:p50:c-Fos复合物结构 | 预测模型 vs 已知p65:p50-DNA结构（PDB 2I9T） | c-Fos亮氨酸拉链插入DNA大沟 | 结构上支持c-Fos增强p65-DNA结合 | 预测未经突变验证 | Results 2.7 |

---

## 11 结论正确解读

- **任务范围**：仅限BV-2小胶质细胞系in vitro实验；未涉及原代小胶质细胞、动物模型或人体样本
- **oracle/真值输入**：无（非计算/预测类研究）
- **端到端状态**：非端到端；为机制解析型研究，各实验独立验证特定环节
- **算力成本**：仅AlphaFold2预测（Colab免费服务器），成本极低
- **历史数据依赖**：依赖既往文献中关于NA/Aβ2R/Epac/AP-1通路（参考文献16）和Pg LPS/TLR2（参考文献20）的结论
- **模型依赖**：AlphaFold2预测的p65:p50:c-Fos复合物未经实验验证（如突变体破坏互作界面后功能丧失实验）
- **最难情形**：OMV+NA的协同机制未完全阐明——作者提出Aβ2R/Epac促进吞噬体成熟的假说，但未提供直接证据（如吞噬体示踪实验）
- **群体/领域边界**：结果可能不适用于其他细胞类型（如原代小胶质细胞、巨噬细胞）或其他细菌毒力因子
- **不确定性**：抑制剂实验存在特异性局限；Co-IP未定量；20kDa IL-1β形式的病理意义未探讨
- **有边界的复述**：在BV-2小胶质细胞中，NA（30–1000 nM）通过Aβ2R通路，与Pg LPS（经NF-κB p65-AP-1 c-Fos互作）和Pg OMV（经TLR9/p52/RelB通路）分别协同，将IL-1β产生量提升至单独刺激的10–20倍；该结论仅适用于该细胞系和刺激条件，机制细节（特别是OMV通路的吞噬体成熟假说）需进一步验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 仅in vitro研究 | 所有实验在BV-2细胞系进行 | 需使用应激动物模型验证 | Discussion 末段 |
| Pg LPS制备方法限制 | 使用商品化Pg LPS（热酚法提取），可能含脂蛋白等杂质 | 使用更纯化的LPS或合成脂质A | Discussion 末段 |
| 未使用原代细胞 | BV-2是永生化细胞系 | 需在原代小胶质细胞中验证 | Discussion 末段 |
| OMV协同机制未完全阐明 | Aβ2R/Epac促进吞噬体成熟为推测 | 需直接检测吞噬体成熟和TLR9信号 | Discussion 末段 |
| 未检测其他炎症因子 | 仅关注IL-1β | 需检测其他细胞因子 | Discussion 末段 |

**作者提及的相关约束**（非正式局限）：使用单一Pg菌株（ATCC 33277），该菌株为低毒力株；不同菌株的OMV成分可能不同，影响结论普适性。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 协同效应倍数（10-20倍）基于报告基因和mRNA，蛋白水平仅验证了LPS组 | 转录协同可能不完整转化为蛋白水平差异；mRNA稳定性可能受影响 | 若蛋白水平协同弱于mRNA水平，则生物学意义有限 | 在多个时间点定量分泌IL-1β蛋白（ELISA） | Results 图1-3 |
| 抑制剂实验使用单一浓度 | 剂量-反应关系未建立，部分抑制可能因浓度不足 | 无法确定通路贡献的真实比例 | 做抑制剂剂量梯度实验 | Results 图4-6 |
| Co-IP未做定量，且未做反向IP（抗c-Fos IP后检测p65） | 互作可能非特异性或方向性不明 | 无法判断互作强度是否随刺激增强 | 定量Co-IP + 反向IP + 竞争实验 | Results 图7 |
| AlphaFold2预测的复合物未与DNA共折叠 | 模型仅预测蛋白-蛋白互作，未包含DNA；"插入DNA大沟"的结论来自叠加而非共折叠 | 结构假设可能不准确 | 用AlphaFold3或MD模拟包含DNA的三元复合物 | Results 图8 |
| 未检测NA受体的下游信号（如cAMP/PKA） | 作者假设Aβ2R/Epac通路，但未直接检测cAMP水平或Epac活性 | 机制链条不完整 | 检测cAMP、Epac活性、PKA活性 | Discussion |
| 未检测IL-1β的加工和分泌机制 | 20kDa形式的出现提示非经典加工，但未探讨 | 可能涉及不同的炎症机制 | 检测caspase-1、cathepsin D活性 | Results 图3D |
| 未做siRNA/敲除验证 | 药理学抑制剂特异性有限 | 基因水平验证可增强结论可靠性 | siRNA敲低Aβ2R、p65、c-Fos、TLR9 | 未提供 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **TF-TF物理互作增强DNA结合的机制**：本文证明c-Fos通过蛋白-蛋白互作与p65结合，增强p65与κB位点的结合，而非c-Fos直接结合DNA。这提示在研究TF-DNA结合时，需考虑TF-TF互作对DNA结合亲和力的间接贡献。**可迁移方法**：用Co-IP验证TF互作，用AlphaFold2预测互作界面，用EMSA或报告基因验证DNA结合增强。

2. **AlphaFold2用于TF复合物结构预测**：本文用AlphaFold2预测p65:p50:c-Fos三元复合物，并将模型与已知DNA结合结构叠加，提出c-Fos插入DNA大沟的假说。**可迁移方法**：对TF-TF-DNA三元复合物，可先用AlphaFold2预测TF-TF互作，再与已知TF-DNA结构（如PDB 2I9T）叠加，生成结构假设，指导突变实验设计。

3. **不同刺激物激活不同TF通路的差异化设计**：LPS经TLR2→NF-κB，OMV经吞噬→TLR9→p52/RelB，NA通过同一受体（Aβ2R）但不同下游节点（转录因子互作 vs 吞噬体成熟）增强两条通路。**可迁移启示**：在研究TF-DNA结合时，需考虑刺激物的细胞进入途径和胞内定位，同一调控因子可能通过不同机制增强不同刺激的转录输出。

4. **报告基因系统用于TF活性检测**：NanoLuc报告基因系统可实时、定量检测IL-1β启动子活性，且与mRNA和蛋白水平检测互补。**可迁移方法**：构建含κB位点或AP-1位点的报告基因，用于快速筛选TF活性调节剂。

5. **"协同"的实验设计框架**：本文采用"单独刺激 vs 联合刺激"的对比设计，配合通路特异性抑制剂，可系统解析协同机制。**可迁移方法**：在研究TF-DNA结合时，可用"TF-A + TF-B vs 单独"的设计，配合DNA结合抑制剂或TF特异性抑制剂，解析协同结合机制。

---

## 15 与已有知识连接

- **NF-κB与AP-1的协同**：已有文献广泛报道NF-κB和AP-1在炎症基因启动子上的协同作用（如IL-6、IL-8等），但多数研究聚焦于两个TF结合相邻DNA位点的"增强体"模型。本文提出c-Fos直接结合p65、不依赖DNA位点邻近的替代机制，与Stein et al. (1993) 关于c-Fos-p65互作的早期报道一致，但提供了更详细的结构模型。
- **AlphaFold2在TF复合物预测中的应用**：AlphaFold2已被用于预测多种蛋白复合物（如Jumper et al., 2021; Evans et al., 2022），但用于TF-TF-DNA三元复合物的预测仍较少。本文的方法（预测TF-TF互作+与已知TF-DNA结构叠加）可作为该方向的参考。
- **β2肾上腺素受体与神经炎症**：已有研究表明β2-AR激动剂可调节小胶质细胞炎症反应（如Färber et al., 2008），但多为抗炎效应。本文发现的促炎协同效应提示β2-AR的作用具有刺激特异性。
- **Pg OMV的胞内TLR9激活**：与本文一致，已有研究报道细菌OMV可被吞噬后激活胞内TLR9（如Kappelmann et al., 2021），本文进一步揭示NA可增强该通路。
- **IL-1β的20kDa形式**：已有文献报道cathepsin D可切割pro-IL-1β产生20kDa形式（如Hazuda et al., 1991），本文在OMV+NA条件下观察到该形式增加，提示非经典加工途径参与。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选1：基于AlphaFold2+MD模拟的TF-TF-DNA三元复合物结合自由能预测
- **名称**：AF2-MD pipeline for TF-TF-DNA ternary complex binding affinity prediction
- **来源局限/观察**：本文用AlphaFold2预测p65:p50:c-Fos复合物，但未包含DNA，也未计算结合自由能；"c-Fos插入DNA大沟"的结论来自与已知结构的叠加，缺乏动态验证
- **核心假设**：将AlphaFold2预测的TF-TF复合物与DNA对接后，用MD模拟（如μs级）可准确预测TF-TF互作对DNA结合亲和力的增强效应
- **初步方法**：(1) 用AlphaFold2预测p65:p50:c-Fos复合物；(2) 与PDB 2I9T中的DNA对接；(3) 用GROMACS/AMBER做MD模拟；(4) 用MM-PBSA/MM-GBSA计算结合自由能；(5) 与EMSA实验数据对比
- **验证方式**：对p65-c-Fos互作界面做突变（如亮氨酸拉链关键残基），预测并实验验证结合亲和力变化
- **创新状态**：unverified（方法组合有先例，但用于TF-TF-DNA三元体系并结合实验验证的完整pipeline未见报道）

### 候选2：TF-TF互作增强DNA结合的通用机制研究——以NF-κB家族成员为例
- **名称**：Systematic mapping of NF-κB family TF-TF interactions and their effect on DNA binding specificity
- **来源局限/观察**：本文仅研究p65与c-Fos一对互作；NF-κB家族有5个成员（p50, p52, p65, c-Rel, RelB），其与AP-1家族（c-Fos, c-Jun, JunB等）的互作网络未被系统研究
- **核心假设**：不同NF-κB成员与AP-1成员的互作对DNA结合的影响具有成员特异性，可预测
- **初步方法**：(1) 用AlphaFold2批量预测NF-κB×AP-1互作矩阵；(2) 用表面等离子共振（SPR）或微量热泳动（MST）验证结合亲和力；(3) 用报告基因系统检测功能输出；(4) 建立序列-结构-功能预测模型
- **验证方式**：对预测的强互作对做突变验证，对弱互作对做功能验证
- **创新状态**：partially checked（NF-κB与AP-1互作有零散报道，但系统性矩阵研究未见）

### 候选3：应激-病原体协同炎症的细胞类型特异性——小胶质细胞vs巨噬细胞
- **名称**：Cell-type-specific synergy between noradrenergic signaling and bacterial virulence factors in innate immune cells
- **来源局限/观察**：本文仅用BV-2小胶质细胞；NA的促炎协同效应是否存在于其他免疫细胞（如骨髓来源巨噬细胞、外周血单核细胞）未知
- **核心假设**：NA与Pg毒力因子的协同效应具有细胞类型特异性，取决于β2-AR表达水平和TLR表达谱
- **初步方法**：(1) 比较BV-2、RAW264.7、BMDM、THP-1等细胞中NA+LPS/OMV的IL-1β产生；(2) 检测β2-AR、TLR2、TLR9表达水平；(3) 用siRNA或CRISPR敲除β2-AR验证必要性
- **验证方式**：若发现细胞类型差异，进一步用转录组学（RNA-seq）解析差异机制
- **创新状态**：unverified（本文未涉及多细胞类型比较）

### 候选4：TF-DNA结合预测模型纳入TF-TF互作特征
- **名称**：Incorporating TF-TF interaction features into deep learning models for TF-DNA binding prediction
- **来源局限/观察**：现有深度学习TF-DNA结合预测模型（如DeepBind, DeepSEA, BPNet）多基于单TF的序列特征，未考虑TF-TF互作对结合的影响；本文证明TF-TF互作可显著增强DNA结合
- **核心假设**：在深度学习模型中引入TF-TF互作特征（如共表达、蛋白-蛋白互作、结构域兼容性），可提高TF-DNA结合预测的准确性
- **初步方法**：(1) 收集TF-TF互作数据（如BioGRID, STRING）；(2) 在现有模型架构中加入互作特征编码层；(3) 在ENCODE/DREAM数据集上评估性能提升
- **验证方式**：对预测改善的TF对做实验验证（如ChIP-seq共结合分析）
- **创新状态**：partially checked（已有研究探索TF协同结合预测，但基于物理互作特征的方法未见）

### 候选5：AlphaFold2预测的TF复合物结构用于指导DNA结合位点预测
- **名称**：Structure-guided DNA binding site prediction using AlphaFold2-predicted TF-TF complexes
- **来源局限/观察**：本文的AlphaFold2模型提示c-Fos可能通过改变p65构象增强DNA结合；这种结构信息可用于预测TF复合物的DNA结合位点偏好
- **核心假设**：基于AlphaFold2预测的TF-TF复合物结构，用分子对接或几何匹配方法预测复合物的DNA结合位点，比基于单体TF的预测更准确
- **初步方法**：(1) 对已知TF-TF-DNA复合物（如PDB中的NF-κB-AP-1-DNA结构）做AlphaFold2预测；(2) 比较预测结构与实验结构的DNA结合域构象差异；(3) 开发基于结构的DNA结合位点预测算法
- **验证方式**：在独立测试集上比较与现有方法（如DeepSEA, FactorNet）的准确性
- **创新状态**：unverified（结构预测用于DNA结合位点预测有初步探索，但针对TF-TF复合物未见）