## 01 基本信息

- **标题**：Genetic elements promote retention of extrachromosomal DNA in cancer cells
- **作者与单位**：Sankar V; Hung KL; Gnanasekar A; Wong IT; Shi Q; Kraft K; Jones MG; He BJ; Yan X; Belk JA; Liu KJ; Agarwal S; Wang SK; Henssen AG; Mischel PS; Chang HY（Chang 和 Mischel 实验室，斯坦福大学）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025
- **论文类型**：预印本（研究论文）
- **领域**：癌症基因组学；染色体外DNA（ecDNA）；表观遗传学；功能基因组筛选
- **关键词**：ecDNA、retention elements、Retain-seq、有丝分裂染色体 hitchhiking、CpG 甲基化、mitotic bookmarking
- **DOI/arXiv 号**：10.1101/2025.10.10.681495
- **代码**：Cassiopeia（https://github.com/YosefLab/Cassiopeia）
- **数据**：NCBI SRA BioProject PRJNA1333946；figshare（retention element 坐标）
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：本文不直接涉及 AI 或物理模拟方法，但揭示了 ecDNA 上特定 DNA 序列元件（retention elements）与有丝分裂染色体上 bookmarking 蛋白之间的物理互作机制，为 TF–DNA 结合、mitotic bookmarking 与 DNA 序列特征关联提供了高通量功能数据，可作为 AI 模型（如预测 retention 活性序列、TF 结合与 ecDNA 保留的关联）的训练数据来源。

## 02 一句话总结

本文通过开发 Retain-seq 高通量功能筛选，鉴定出人类基因组中一类 CpG 富集的启动子/增强子样「retention elements」，它们通过在有丝分裂期间与染色体上被转录因子 bookmarking 的区域发生物理互作，将 ecDNA 拴系到染色体上，从而提高 ecDNA 在子代细胞中的保留率；该活性可被 CpG 甲基化所抑制。

## 03 研究问题

- **具体问题**：无着丝粒的 ecDNA 在有丝分裂中随机分配，为何仍能在癌细胞中跨多代稳定维持？哪些内源 DNA 序列元件介导 ecDNA 与染色体的 hitchhiking？
- **为什么重要**：ecDNA 是癌症中癌基因扩增的主要形式，驱动肿瘤异质性和治疗耐药。理解 ecDNA 保留的分子机制，对靶向 ecDNA 维持的癌症治疗策略至关重要。
- **现有方法不足**：已知病毒附加体（如 EBV、HPV）通过病毒蛋白（EBNA1、E2）拴系到染色体，但人类内源 DNA 元件是否及如何介导 ecDNA 保留完全未知；缺乏系统性的功能筛选方法。
- **精确研究问题**：Can human genomic DNA sequences, when placed on acentric episomes, promote their retention in dividing cells, and what are the sequence and epigenetic features of such "retention elements"?

## 04 背景与发展脉络

（标注：以下脉络为「经外部核验」+「仅本文框架」混合，具体标注于各阶段）

1. **ecDNA 发现与重要性**（外部核验）：ecDNA 是癌症中常见的癌基因扩增形式，无着丝粒、随机分离，但可稳定维持（参考文献 1-6）。
2. **病毒附加体 hitchhiking 机制**（外部核验）：EBV 的 EBNA1 蛋白结合 oriP 序列并拴系到染色体；HPV 的 E2 蛋白介导类似机制（参考文献 13-19）。这些是外源病毒系统，人类内源元件未知。
3. **ecDNA 与染色体共定位观察**（外部核验）：ecDNA 在有丝分裂中与染色体共定位，但机制不明（参考文献 3, 20-23）。
4. **本文主张的位置**（仅本文框架）：首次提出人类基因组中存在内源「retention elements」，通过 mitotic bookmarking 机制介导 ecDNA 的染色体 hitchhiking，并开发 Retain-seq 进行系统鉴定。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| ecDNA 无着丝粒却稳定维持 | ecDNA 缺乏着丝粒，有丝分裂中随机分配，但可在癌细胞中维持多代 | 存在内源 DNA 元件介导 ecDNA 与染色体的 hitchhiking | Results 图 1c-d：活细胞成像显示 ecDNA 与染色体同步分离 |
| 人类内源 retention 元件未知 | 病毒附加体 hitchhiking 机制已知，但人类基因组中无对应元件被鉴定 | 缺乏系统性功能筛选方法 | Introduction：指出病毒系统已知，人类内源元件未知 |
| 现有筛选方法无法直接检测 retention 活性 | 传统筛选无法区分 retention 与复制、整合等机制 | 需要一种不依赖复制、直接检测有丝分裂保留的功能筛选 | Results 图 1e：Retain-seq 设计为无复制源、直接检测保留 |
| 甲基化对 retention 的影响未知 | ecDNA 上 CpG 甲基化状态与 retention 活性的关系不清楚 | 假设 CpG 甲基化可能通过影响蛋白结合来调控 retention | Results 图 4i-n：甲基化实验显示 retention 活性被甲基化抑制 |

## 06 核心思想

**1) 表面方法**：
- 开发 Retain-seq：将人类基因组随机片段克隆到无复制源的质粒载体中，转染细胞后连续传代，通过测序富集分析鉴定能提高质粒保留的基因组序列。
- 结合活细胞成像、Hi-C、ChIP-seq 数据整合、CRISPRoff 靶向甲基化、进化模拟等手段验证机制。

**2) 核心洞察**：
- 人类基因组中存在大量内源「retention elements」，它们本质上是 CpG 富集的启动子和增强子样序列。
- Retention elements 通过与有丝分裂染色体上被 bookmarking 的调控区域发生物理互作（类似增强子-启动子互作但发生在 trans 的 DNA 分子间），将 ecDNA 拴系到染色体上。
- 该互作依赖 CpG 位点的去甲基化状态，甲基化可关闭 retention 活性。

**3) 可能的普适教训** [Analysis]：
- 基因组中「调控元件」的功能可能不限于 cis 调控基因表达，还可作为 trans 的物理锚点介导 DNA 分子的有丝分裂遗传。
- 高通量功能筛选（如 Retain-seq）可系统揭示 DNA 序列的「非经典」功能，这类数据对训练 AI 模型预测 DNA 元件的多维度功能具有价值。

## 07 方法总览

- **输入**：人类基因组随机 DNA 片段（600-1300 bp）；多种细胞系（COLO320DM、GBM39、K562、GM12878）
- **输出**：retention elements 列表（14,353 个）、其序列特征、功能验证数据
- **模块**：
  1. Retain-seq 筛选（质粒构建、转染、传代、测序富集分析）
  2. 序列特征分析（CpG 密度、启动子/增强子注释、TF 基序）
  3. 活细胞成像（ecDNA-染色体共定位、hitchhiking 概率）
  4. Hi-C（ecDNA-染色体互作）
  5. CRISPRoff 靶向甲基化
  6. 进化模拟（retention 与选择对 ecDNA 拷贝数的影响）
- **训练**：不适用（非机器学习方法）
- **工具**：Cassiopeia（进化模拟）、Fiji/ImageJ（图像分析）、CellProfiler（图像分割）、deepTools（ChIP-seq 分析）
- **反馈回路**：Retain-seq 鉴定 → 单体验证 → 机制实验 → 模拟预测 → 患者数据验证
- **假设**：ecDNA 保留主要通过有丝分裂 hitchhiking 实现；质粒载体可模拟 ecDNA 的保留行为；retention 活性不依赖 DNA 复制

**文字流程**：
1. 将 GM12878 基因组 DNA 片段化并克隆到无复制源质粒载体
2. 将质粒库转染入多种细胞系，连续传代
3. 提取保留的质粒 DNA，测序并与输入库比较，计算富集分数
4. 鉴定高置信 retention elements，进行序列特征分析
5. 单体验证（qPCR、活细胞成像）
6. Hi-C 分析 ecDNA-染色体互作
7. CRISPRoff 靶向甲基化验证表观调控
8. 患者肿瘤 WGS 数据分析 retention element 共扩增
9. 进化模拟验证 retention 对 ecDNA 维持的必要性

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Retain-seq 筛选 | 系统鉴定人类基因组中能提高质粒保留的序列 | 无先验知识，需要 unbiased 的功能筛选 | 输入：基因组片段质粒库；输出：富集序列列表 | Results 图 1e-i：多个细胞系中鉴定出数千个 retention elements | 预期影响：无法发现新元件（实测消融不可行，因为这是核心发现手段） |
| 序列特征分析 | 揭示 retention elements 的序列和染色质特征 | 理解 retention 的分子基础 | 输入：retention element 坐标；输出：CpG 密度、注释、TF 基序 | Results 图 2a-h：富集于启动子/增强子、CpG 高密度 | 预期影响：无法建立序列-功能关联 |
| 活细胞成像 | 直接观察质粒/ecDNA 与染色体的 hitchhiking | 验证 retention 的物理机制 | 输入：标记的质粒/ecDNA 和染色体；输出：共定位率、hitchhiking 概率 | Results 图 3a-d：retention element 降低 hitchhiking 失败率 | 预期影响：无法区分 retention 与其他机制（如核保留） |
| Hi-C | 检测 ecDNA 与染色体的物理互作 | 验证 retention elements 与 bookmarking 区域的互作 | 输入：有丝分裂细胞 Hi-C 数据；输出：互作矩阵 | Results 图 3e-h：retention elements 与 bookmarking 区域富集互作 | 预期影响：无法确认互作的序列特异性 |
| CRISPRoff 靶向甲基化 | 验证 CpG 甲基化对 retention 活性的调控 | 建立表观遗传调控机制 | 输入：靶向 retention element 的 dCas9-DNMT；输出：甲基化水平、质粒保留变化 | Results 图 4l-n：甲基化降低 retention 活性 | 预期影响：无法建立因果关系 |
| 进化模拟 | 预测 retention 和选择对 ecDNA 拷贝数的贡献 | 将分子机制与进化后果联系 | 输入：retention 率、选择系数；输出：拷贝数动态 | Results 图 4a-b：retention 率 <0.9 时 ecDNA 快速丢失 | 预期影响：无法量化 retention 的进化必要性 |

## 09 关键公式符号

本文无显式数学公式。核心定量关系为：

- **Retention 率 (v)**：每次有丝分裂中 ecDNA 被正确分配到子细胞核的概率，v ∈ [0, 1]。实验测得单 retention element 的 hitchhiking 失败率从 25% 降至 10.4%（即 v 从 0.75 提升至 0.896）。
- **ecDNA 拷贝数分配模型**：子细胞 i 获得的 ecDNA 拷贝数 n_i 服从二项分布：n_i ~ Binomial(N, v/2)，其中 N 为母细胞拷贝数（Methods 节）。
- **富集分数**：Retain-seq 中，每个基因组片段的富集 = log2(输出 CPM / 输入 CPM)，经邻近窗口中位数归一化后计算 Z-score，FDR < 0.1 为显著 retention element（Methods 节）。

## 10 实验设计与证据链

**数据集/群体**：
- 细胞系：COLO320DM（结直肠癌，ecMYC）、GBM39（胶质母细胞瘤，ecEGFR）、K562（慢性粒细胞白血病，无 ecDNA）、GM12878（淋巴母细胞，EBV+）
- 患者数据：TCGA 和 PCAWG 队列的 WGS 数据（AmpliconRepository）
- Retain-seq 筛选规模：人类基因组随机片段库，多个时间点（6-30 天），2 个生物学重复

**指标**：质粒保留率（qPCR）、富集 Z-score、hitchhiking 失败率（活细胞成像）、Hi-C 互作强度（APA）、甲基化水平（纳米孔测序）

**基线/对照**：空载体（pUC19）、随机基因组序列、EBV oriP 序列（阳性对照）

**评测协议**：Retain-seq 富集分析（FDR < 0.1，两个重复）；单体验证（qPCR 时间序列）；活细胞成像（有丝分裂事件 ≥5 个 foci/细胞）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| Retain-seq 筛选（3 细胞系） | 人类基因组存在功能性 retention elements | 输出 vs 输入库；多时间点 | 14,353 个 retention elements，多数 <1 kb | 存在广泛分布的 retention elements | 未证明所有元件在天然 ecDNA 上有功能 | Results 图 1g-i |
| 单体验证（6 个元件） | 单个 retention element 足以提高质粒保留 | 含元件质粒 vs 空载体 vs 随机序列 | 5/6 元件显著提高保留 | retention 活性可被单个元件赋予 | 样本量小，未覆盖所有元件类型 | Results 图 1i |
| 活细胞成像 | retention element 促进染色体 hitchhiking | 含元件质粒 vs 对照 | 失败率 25%→10.4% | 机制为有丝分裂 hitchhiking | 未排除其他共存机制 | Results 图 3c-d |
| Hi-C（有丝分裂） | retention elements 与 bookmarking 区域互作 | 有丝分裂 vs 间期；元件 vs 对照 | 元件与 bookmarking 区域富集互作 | 互作发生在有丝分裂 | 未鉴定具体蛋白中介 | Results 图 3e-h |
| CRISPRoff 甲基化 | CpG 甲基化抑制 retention 活性 | 靶向甲基化 vs 非靶向对照 | 甲基化降低保留和 hitchhiking | 甲基化是 retention 的开关 | 未测试去甲基化是否能恢复 | Results 图 4l-n |
| 患者 WGS 分析 | retention elements 在 ecDNA 上共扩增 | ecDNA vs 线性扩增子 | 98% ecDNA 含 retention elements | retention 是 ecDNA 的普遍特征 | 相关性非因果 | Results 图 4c-d |
| 进化模拟 | retention 是 ecDNA 维持的必要条件 | 不同 retention 率 vs 选择系数 | v<0.9 时 ecDNA 快速丢失 | 高 retention 率是 ecDNA 扩增前提 | 模拟参数可能简化真实情况 | Results 图 4a-b |

## 11 结论正确解读

- **任务范围**：本文鉴定的是「能提高附加体质粒在有丝分裂中保留」的人类基因组 DNA 序列元件，并验证其在 ecDNA 上的存在和功能。未直接研究 ecDNA 的复制、转录或整合。
- **oracle/真值输入**：Retain-seq 的阳性对照为 EBV oriP（已知能介导 EBV 附加体保留）；阴性对照为空载体和随机序列。真值基于功能实验而非计算预测。
- **端到端状态**：从筛选到机制验证（成像、Hi-C、甲基化）到患者数据关联，证据链完整，但未纯化鉴定具体的蛋白中介因子。
- **算力成本**：不适用（无大规模计算）。
- **历史数据依赖**：依赖已发表的 ChIP-seq（ENCODE）、Hi-C、纳米孔甲基化数据。
- **模型依赖**：不适用（无预测模型）。
- **最难情形**：单 retention element 的效应量较小（失败率 25%→10.4%），需要高灵敏度检测；不同细胞系间 retention elements 重叠度低，提示细胞类型特异性。
- **群体/领域边界**：结论基于癌细胞系和患者肿瘤数据，未在正常组织或非癌背景下验证；retention 机制可能与其他附加体维持机制（如 tethering 到核基质）共存。
- **不确定性**：未鉴定 retention elements 上具体的蛋白结合位点；甲基化实验仅测试了 5 个元件；Hi-C 分析受限于有丝分裂细胞数量。

**有边界的复述**：在测试的癌细胞系中，人类基因组中存在一类 CpG 富集的启动子/增强子样序列元件，它们能通过有丝分裂染色体 hitchhiking 提高附加体 DNA 的跨代保留，该活性依赖 CpG 去甲基化状态，且这些元件在患者肿瘤 ecDNA 上普遍共扩增。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 未鉴定具体蛋白中介 | 已知 retention 依赖 bookmarking 因子，但未纯化鉴定 | 未来系统功能研究可能鉴定必要因子 | Discussion 节 |
| 细胞类型特异性 | 不同细胞系间 retention elements 重叠度低 | 未明确提及 | Results 图 1h 讨论 |
| 单元件效应量小 | 单个 retention element 仅将失败率从 25% 降至 10.4% | 未明确提及 | Results 图 3c |
| 甲基化实验范围有限 | 仅测试了 5 个元件 | 未明确提及 | Results 图 4l-n |
| 未排除其他维持机制 | 不排除核基质 tethering 等其他机制共存 | 未明确提及 | Discussion 节 |
| 患者数据为相关性 | 98% ecDNA 含 retention elements 为相关性观察 | 未明确提及 | Results 图 4c-d |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| Retain-seq 使用质粒载体，可能不完全模拟天然 ecDNA 的染色质状态 | 质粒缺乏 ecDNA 的巨大多拷贝结构和高开放染色质状态，可能高估或低估 retention 活性 | 影响结论向天然 ecDNA 的推广 | 在天然 ecDNA 上直接编辑/删除 retention elements 并检测保留 | Methods：质粒为 2.7 kb 无复制源载体 |
| 活细胞成像中质粒 foci 可能包含整合或串联重复的质粒 | 未充分排除整合事件对「保留」信号的贡献 | 若存在整合，则 retention 活性可能被高估 | 对成像细胞进行单细胞全基因组测序或 FISH 验证 | Results 图 3a-d 方法描述 |
| Hi-C 分析中「bookmarking 区域」的定义依赖已发表数据，可能遗漏细胞类型特异性 bookmarking | 不同细胞类型 bookmarking 因子不同，COLO320DM 的 bookmarking 图谱可能不完整 | 影响互作分析的完整性 | 在 COLO320DM 中直接进行有丝分裂 ChIP-seq 或 CUT&Tag | Results 图 3e-h |
| CRISPRoff 靶向甲基化可能脱靶或影响邻近基因表达 | 甲基化可能改变局部染色质状态而非直接干扰 retention 蛋白结合 | 影响因果推断 | 使用不依赖甲基化的蛋白结合干扰（如 dCas9 竞争性结合） | Results 图 4l-n |
| 进化模拟假设 retention 率恒定，未考虑 ecDNA 拷贝数对 retention 的非线性效应 | 高拷贝数可能通过「群体效应」降低单分子丢失风险 | 影响对 retention 必要性的定量结论 | 在模拟中引入拷贝数依赖的 retention 率 | Methods：模拟参数设置 |
| 患者数据中 98% ecDNA 含 retention elements 可能反映扩增区域本身的基因密度而非 retention 选择 | 高基因密度区域天然富含启动子/增强子，可能混淆 retention 与基因密度的关联 | 影响 retention 在 ecDNA 进化中因果作用的结论 | 控制基因密度后重新分析 retention element 富集 | Results 图 4c-d |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **概念：DNA 元件的 trans 功能**。Retention elements 表明，启动子/增强子样序列不仅 cis 调控基因表达，还能作为 trans 的物理锚点介导 DNA 分子间互作。对本课题（TF–DNA 结合）的迁移：TF 在 mitotic bookmarking 中的结合位点可能同时赋予 DNA 分子「被拴系」的能力，TF 结合谱数据可用于预测 DNA 元件的 retention 活性。

2. **方法：功能筛选与序列特征关联**。Retain-seq 的「随机片段→功能筛选→序列特征分析」流程可直接迁移到 TF–DNA 结合研究：用随机 DNA 文库筛选 TF 结合介导的 retention 活性，结合机器学习识别关键序列基序。

3. **数据：retention elements 作为训练集**。14,353 个人类 retention elements 的坐标和序列可作为训练/验证集，用于开发预测 DNA 元件 retention 活性的深度学习模型（如基于 DNA 序列 + 染色质特征的 CNN/Transformer）。

4. **机制：mitotic bookmarking 与 TF 结合**。本文显示 retention elements 与 bookmarking 区域互作，提示 TF 在有丝分裂中的持续结合是 DNA 拴系的基础。对本课题的迁移：可系统研究哪些 TF 在有丝分裂中保留结合并介导 ecDNA 拴系，结合 ChIP-seq 和 Hi-C 数据构建 TF–DNA 互作网络。

5. **表观调控：CpG 甲基化作为开关**。甲基化抑制 retention 活性，提示 DNA 序列的「功能状态」由表观修饰决定。对本课题的迁移：TF–DNA 结合预测模型需整合甲基化特征，而非仅依赖序列。

6. **实验设计：多模态验证**。从功能筛选→单体验证→活细胞成像→Hi-C→患者数据→进化模拟的验证链条，为 TF–DNA 互作研究提供了「从序列到功能到进化意义」的完整范式。

## 15 与已有知识连接

- **病毒附加体 hitchhiking**（外部核验）：EBV EBNA1/oriP 和 HPV E2 的拴系机制是本文的类比基础（参考文献 13-19）。本文首次将这一概念推广到人类内源元件。
- **Mitotic bookmarking**（外部核验）：已知转录因子（如 FOXA1、GATA1）在有丝分裂中保留在染色体上（参考文献 38-44）。本文的 retention elements 与 bookmarking 区域的互作与此直接相关。
- **ecDNA 结构与功能**（外部核验）：ecDNA 的开放染色质状态和高表达活性已有报道（参考文献 56）。本文补充了 ecDNA 维持的序列基础。
- **CpG 岛与启动子功能**（外部核验）：CpG 富集启动子的转录调控功能已知。本文发现其额外的「retention」功能，扩展了 CpG 岛的功能谱系。
- **候选方向** [Analysis]：本文的 retention elements 列表可与 ENCODE 的 TF ChIP-seq 数据结合，构建「TF 结合 → retention 活性」的预测模型；也可与 AlphaFold 等结构预测工具结合，研究 retention element 上 DNA 构象与 TF 结合的关联。

## 16 研究想法

**Agent 生成的研究候选**：

1. **名称**：TF–DNA 结合预测 retention 活性的深度学习模型
   - **来源局限/观察**：本文鉴定 14,353 个 retention elements，但未系统解析其序列基序与 TF 结合的关系
   - **核心假设**：retention 活性由特定 TF 组合的结合位点决定，可通过 DNA 序列预测
   - **增量**：将 retention elements 作为标注数据，训练 CNN/Transformer 模型预测任意 DNA 序列的 retention 活性
   - **初步方法**：以 retention elements 为正样本、随机基因组片段为负样本，输入 DNA 序列 + 染色质特征（DNase、H3K27ac），输出 retention 概率；用 SHAP 识别关键基序
   - **验证方式**：留出法测试 + 湿实验验证（合成序列 + 质粒保留实验）
   - **创新状态**：unverified

2. **名称**：Mitotic bookmarking TF 与 ecDNA retention 的互作图谱
   - **来源局限/观察**：本文显示 retention elements 与 bookmarking 区域互作，但未鉴定具体 TF
   - **核心假设**：特定 bookmarking TF（如 FOXA1、GATA1）在 retention elements 上的结合是 ecDNA 拴系的必要条件
   - **增量**：整合本文 retention elements 与有丝分裂 ChIP-seq 数据，构建 TF–retention 互作网络
   - **初步方法**：对 retention elements 进行有丝分裂 CUT&Tag，鉴定结合 TF；用 CRISPR 敲除候选 TF 检测 ecDNA 保留变化
   - **验证方式**：敲除后活细胞成像 + 质粒保留实验
   - **创新状态**：unverified

3. **名称**：CpG 甲基化状态作为 ecDNA retention 的可逆开关
   - **来源局限/观察**：本文显示甲基化抑制 retention 活性，但未测试去甲基化是否能恢复
   - **核心假设**：去甲基化药物可恢复 retention 活性，从而影响 ecDNA 维持
   - **增量**：将表观药物与 ecDNA 维持联系起来，可能提供治疗策略
   - **初步方法**：用 5-aza-2'-deoxycytidine 处理 ecDNA 阳性细胞，检测 retention element 甲基化水平和 ecDNA 拷贝数变化
   - **验证方式**：qPCR + 纳米孔甲基化测序 + 活细胞成像
   - **创新状态**：unverified

4. **名称**：基于 retention element 密度的 ecDNA 结构预测
   - **来源局限/观察**：本文显示 retention element 密度影响 ecDNA 大小和结构
   - **核心假设**：retention element 分布决定 ecDNA 的进化稳定性，可用于预测哪些扩增子更可能形成 ecDNA
   - **增量**：将 retention element 密度作为特征，预测癌症基因组中 ecDNA 形成概率
   - **初步方法**：从 TCGA/PCAWG 数据中提取扩增子序列，计算 retention element 密度，训练分类器区分 ecDNA 与线性扩增
   - **验证方式**：交叉验证 + 独立队列验证
   - **创新状态**：unverified

5. **名称**：合成 retention element 设计用于稳定附加体表达系统
   - **来源局限/观察**：本文显示 retention elements 可提高附加体质粒的跨代保留
   - **核心假设**：人工设计的 retention element 组合可构建不整合的稳定表达载体
   - **增量**：将基础发现转化为合成生物学工具
   - **初步方法**：从 retention elements 中提取最小功能序列，设计合成组合，测试在治疗相关细胞类型中的保留效率
   - **验证方式**：长期传代 + 单细胞追踪
   - **创新状态**：unverified