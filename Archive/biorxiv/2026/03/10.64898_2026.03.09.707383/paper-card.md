## 01 基本信息

- **标题**：A DNA foundation model predicts osteoporosis risk genes without proximity bias
- **作者**：Cristian Regep; Chantriolnt-Andreas Kapourani; Emre Sofyali; Agnieszka Dobrowolska; Giannis Loukas; Andrew Anighoro; Eleonora Canale; Torsten Gross; Marco P. Licciardello; Revant Gupta; Sorina Maciuca; Tariq Desai; Alice Del Vecchio; Cameron Field; Karl Gemayel; Avelino Javer; Zicong Zhang; Rika Tsujikawa; Fumitaka Inoue; Edith. M. Hessel; Jake P. Taylor-King; John Whittaker; David Roblin; Rebecca E. McIntyre; Lindsay M. Edwards
- **单位**：未提供（从作者姓名推断可能涉及工业界与学术界合作，具体机构未在摘要中列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（方法学 + 应用验证型）
- **领域**：计算基因组学 / 调控基因组学 / 药物靶点发现
- **关键词**：DNA foundation model, variant-to-gene (V2G), eQTL fine-mapping, GWAS, osteoporosis, CRISPR screen, distal regulation
- **DOI/ID**：10.64898/2026.03.09.707383
- **代码**：未提供
- **数据**：GTEx v8 cis-eQTL summary statistics；Open Targets v25.03；Morris et al. 2019 eBMD GWAS（426,824 例 White British UK Biobank 个体）；酵母与成骨细胞 MPRA 数据集（Weiss et al. 来源）
- **阅读日期**：2026-05-14（按当前日期推断）
- **在该课题方向中的位置**：本文属于「DNA 序列 foundation model → 变异-基因调控关系预测」这一 AI 方法路线，直接面向 TF–DNA 结合机制的下游效应（基因表达调控），但不涉及 3D 结构或分子模拟。其核心贡献在于：(1) 用序列模型直接预测 variant–gene 调控关系，绕开距离近邻假设；(2) 在骨质疏松症中结合 CRISPR 敲除功能实验验证远端基因的因果性。对 TF–DNA 结合机制课题的可迁移点在于：模型架构（Enformer + RoPE）、因果变体分类训练范式、以及「远端调控基因」这一概念对 TF 结合位点远端靶基因识别的启示。

---

## 02 一句话总结

本文提出 Rosalind——一个基于 Enformer 架构、以 RoPE 替换相对位置编码并在 GTEx fine-mapped cis-eQTL 上微调的 DNA foundation model——直接从序列预测 variant–gene 调控关系，不依赖距离近邻假设，并在骨质疏松症 eBMD GWAS 的 1,103 个信号中识别出 239 个高风险基因（多数为远端基因），通过成骨细胞矿化 CRISPR 敲除实验验证了远端基因比最近邻基因更频繁地影响骨形成表型。

---

## 03 研究问题

- **具体问题**：如何从非编码 GWAS 变异准确识别其效应基因（effector gene），尤其是那些距离变异较远的基因？现有 V2G 方法（如 L2G）过度依赖距离近邻假设，导致远端调控基因被系统性忽略。
- **为什么重要**：约 90% 的 GWAS 信号位于非编码区，将变异映射到正确基因是药物靶点发现的关键瓶颈。人类遗传学证据支持的靶点从临床开发到获批的概率翻倍，因此 V2G 映射的准确性直接影响药物研发成功率。
- **现有方法不足**：(1) 距离近邻假设在复杂基因组区域（多个基因邻近）不可靠；(2) 整合 omic 数据（如 L2G）虽有所改进，但预测仍强烈受距离驱动（Fig. 2a 显示 L2G 预测中 <20% 为远端基因）；(3) 基于共定位的 sc-eQTL 方法需要大量临床活检样本，操作上困难且资源密集。
- **精确研究问题（Can 形式）**：Can a DNA foundation model fine-tuned on fine-mapped eQTL variants directly predict causal variant–gene regulatory relationships from sequence alone, without relying on proximity heuristics, and can such distal predictions be experimentally validated as functionally relevant in a disease-relevant cell assay?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注「仅本文框架」或「经外部核验」。

1. **阶段一：距离近邻法（最早期，广泛使用）**
   - 代表方法：最近基因法、距离阈值法
   - 优点：简单、可解释
   - 局限：忽略 3D 基因组结构，在基因密集区域错误率高
   - 来源：本文 Introduction 描述（仅本文框架）

2. **阶段二：整合 omic 数据的 V2G 方法**
   - 代表方法：L2G（Open Targets）
   - 优点：整合 eQTL、pCHi-C、VEP 等多源数据
   - 局限：预测仍强烈受距离驱动（Fig. 2a），远端基因识别能力有限
   - 来源：本文 Introduction 及 Results（经外部核验：L2G 为 Open Targets 公开方法）

3. **阶段三：sc-eQTL 共定位方法**
   - 代表方法：单细胞 eQTL 共定位分析
   - 优点：可在特定细胞类型中识别远端增强子-基因关联
   - 局限：需要大量临床活检样本，操作复杂、资源密集
   - 来源：本文 Introduction（仅本文框架）

4. **阶段四：序列 foundation model 直接预测调控效应（本文位置）**
   - 代表方法：Enformer、Borzoi、AlphaGenome（预训练）；Rosalind（微调）
   - 优点：直接从序列捕获调控语法与长程增强子-启动子互作，不依赖距离假设；可扩展至任意组织/细胞类型
   - 局限：需要高质量 fine-mapping 标签；预测为相关性而非因果性，需实验验证
   - 来源：本文 Introduction 与 Results（经外部核验：Enformer/Borzoi 为已发表方法）

5. **阶段五（本文贡献）：微调 + 功能实验闭环验证**
   - Rosalind 在 GTEx fine-mapped eQTL 上微调，并在骨质疏松症中结合 CRISPR 敲除功能实验验证远端基因的因果性
   - 来源：本文 Results（仅本文框架）

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 距离近邻偏差 | 现有 V2G 方法预测结果中 <20% 为远端基因，大量远端调控基因被忽略 | L2G 等方法的预测强烈受距离驱动，距离特征在模型中权重过高 | Results 图 2a-b |
| 复杂位点基因分配困难 | 同一变异附近可有 0–30 个基因（eBMD 位点），距离近邻法无法区分因果基因 | 线性基因组距离不反映核内 3D 空间邻近性 | Results 图 3b |
| 远端调控机制被系统性低估 | 远端增强子-基因互作在疾病机制中重要但难以通过传统方法识别 | 缺乏直接从序列预测长程调控效应的工具 | Introduction 段落 |
| 功能验证缺失 | 多数 V2G 预测缺乏实验验证，无法区分相关性与因果性 | 高通量功能实验（如 CRISPR 筛选）成本高、周期长 | Results 图 3d-f |
| 组织特异性不足 | 同一变异在不同组织中可能调控不同基因 | 现有方法多使用跨组织平均或单一组织数据 | Methods（GTEx 多组织 fine-mapping 聚合策略） |

---

## 06 核心思想

### 1) 表面方法

Rosalind 是一个两阶段模型：
- **阶段一（预训练）**：采用 Enformer 架构，但将相对位置编码替换为 Rotary Positional Embeddings (RoPE)，在参考基因组上预训练，学习通用调控语法。
- **阶段二（微调）**：在 GTEx v8 fine-mapped cis-eQTL 数据上，以 variant–gene pair 为单位构建二分类任务（因果 vs 非因果），微调整个模型。输入为包含变异的 DNA 序列窗口（参考/替代等位基因分别编码），输出为因果关系的概率。

### 2) 核心洞察

- **洞察一**：长程 transformer 架构（Enformer 类）天然具备捕获远端增强子-启动子互作的能力，但预训练于参考基因组使其对个体水平变异不敏感。通过 fine-mapping 标签微调，可以将「序列 → 调控活性」的通用知识转化为「变异 → 基因」的因果映射。
- **洞察二**：距离近邻假设是 V2G 映射的主要偏差来源。Rosalind 不显式使用距离特征，而是让模型从序列上下文学习调控关系，从而天然规避该偏差。
- **洞察三**：fine-mapped eQTL 的 PIP 值提供了高质量的训练标签——PIP > 0.9 为高置信因果，PIP < 0.01 为高置信非因果，避免了人工标注的主观性。
- **洞察四**：预测的远端基因可以通过疾病相关细胞模型中的 CRISPR 敲除功能实验进行验证，形成「计算预测 → 功能验证」的闭环。

### 3) 可能的普适教训 [Analysis]

- 对 TF–DNA 结合机制课题的启示：序列 foundation model 的微调范式（预训练于通用调控语法 → 微调于特定任务标签）同样适用于 TF 结合位点预测、motif 效应量化等任务。关键在于构造高质量的任务标签（如本文的 PIP 阈值策略）。
- 「规避归纳偏置」的思路值得借鉴：与其在模型中显式编码距离/位置先验，不如让模型从数据中学习，前提是有足够高质量的标签数据。
- 计算预测 + 功能实验验证的闭环设计是建立可信度的关键，尤其当预测结果挑战传统假设（如远端基因）时。

---

## 07 方法总览

- **输入**：variant–gene pair 的 DNA 序列窗口（包含参考/替代等位基因），窗口大小未在摘要中明确给出（推测与 Enformer 一致，约 100–200 kb，但未提供）
- **输出**：二分类概率——该变异是否因果性地影响该基因的表达
- **模型架构**：
  - 主干：Enformer 风格 transformer（卷积 stem + transformer blocks）
  - 位置编码：RoPE 替代相对位置编码（增强长程泛化）
  - 分类头：轻量 MLP，输入为参考/替代等位基因的 embedding 拼接
- **训练数据**：GTEx v8 cis-eQTL fine-mapping 结果（约 17,000 个 variant–gene pairs），PIP > 0.9 为正样本，PIP < 0.01 为负样本
- **训练策略**：交叉熵损失；预训练权重不冻结（end-to-end fine-tuning）；随机位置插入非因果变异作为数据增强
- **评测**：
  - 基准测试：与 Enformer-CAGE 适配、距离近邻基线、L2G 对比（AUPRC / AUROC）
  - 泛化测试：4 个复杂疾病 GWAS（T2D、高血压、哮喘、银屑病）
  - 功能验证：成骨细胞矿化 CRISPR/Cas9 敲除筛选
- **推理流程**：对每个 GWAS lead variant，取以 TSS 为中心的窗口内所有基因，逐一评分，取最高分基因作为预测效应基因

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Enformer 预训练主干 | 从参考基因组序列学习通用调控语法（增强子/启动子/绝缘子等） | 提供强大的序列表示先验，使微调更高效 | 输入：DNA 序列窗口；输出：多任务调控活性预测 | 原文引用 Enformer 性能（Introduction） | 预期：模型从头训练需要更多数据且性能下降 [Analysis] |
| RoPE 位置编码 | 替换相对位置编码，增强对超长序列的泛化 | 使模型能处理训练中未见过的更长序列（如 256 kb 窗口） | 输入：token 位置；输出：旋转位置嵌入 | Methods 节描述 | 预期：长程增强子-启动子互作捕获能力下降 [Analysis] |
| 等位基因双编码 + 分类头 | 分别编码参考/替代等位基因序列，拼接后分类 | 直接学习变异对调控活性的扰动效应 | 输入：ref/alt 序列 embedding；输出：因果概率 | Results 图 1c-d | 预期：模型退化为仅依赖距离或基因注释 [Analysis] |
| PIP 阈值标签策略 | 以 fine-mapping PIP > 0.9 / < 0.01 定义正负样本 | 提供高质量、可扩展的训练标签 | 输入：GTEx fine-mapping 结果；输出：二分类标签 | Methods 节 | 预期：标签噪声增大，模型精度下降 [Analysis] |
| 非因果变异数据增强 | 在训练窗口随机位置插入非因果变异 | 提升模型对随机变异与因果变异的区分能力 | 输入：训练窗口；输出：增强后的训练样本 | Methods 节 | 预期：模型对假阳性更敏感 [Analysis] |
| CRISPR 敲除功能验证 | 在成骨细胞中敲除预测基因，检测矿化表型变化 | 验证计算预测的因果性，建立生物学可信度 | 输入：预测基因列表；输出：矿化表型 hit 列表 | Results 图 3d-f | 不适用（实验模块） |

---

## 09 关键公式符号

本文为深度学习应用型论文，摘要与 Methods 中未出现显式数学公式。以下为可推断的关键概念：

- **PIP（Posterior Inclusion Probability）**：SuSiE fine-mapping 输出的变异因果概率，PIP > 0.9 为正样本阈值，PIP < 0.01 为负样本阈值。
- **交叉熵损失**：用于二分类微调，L = −[y·log(ŷ) + (1−y)·log(1−ŷ)]，其中 y 为 PIP 阈值化标签，ŷ 为模型预测概率。
- **log₂ fold-change**：Enformer 适配时使用的评分方式——log₂(替代等位基因预测值 / 参考等位基因预测值)，用于衡量变异对调控信号的扰动方向与幅度。
- **AUPRC / AUROC**：评估指标，用于比较 Rosalind 与基线方法的排序性能。
- **McNemar's test**：配对二分类结果比较的统计检验，用于 CRISPR 敲除实验中 Rosalind 预测基因与最近邻基因 hit 率的差异显著性检验（p = 0.011）。

---

## 10 实验设计与证据链

### 数据集与资源

| 资源 | 规模/描述 | 用途 |
|------|-----------|------|
| GTEx v8 cis-eQTL | 49 组织，~17,000 样本；fine-mapping 后约 17,000 个 variant–gene pairs | 微调训练/验证/测试 |
| 酵母 MPRA | 高通量启动子活性数据 | 架构基准测试（Enformer vs GeneGenie） |
| 成骨细胞 MPRA | 人原代胎成骨细胞增强子活性数据（Weiss et al. 来源） | 架构基准测试 + 调控语法验证 |
| Open Targets v25.03 | T2D、高血压、哮喘、银屑病 4 个 GWAS，937 个 lead variants，3,766 个 V2G pairs | 泛化性评估 |
| eBMD GWAS（Morris et al. 2019） | 426,824 例 White British UK Biobank；1,103 个条件独立显著信号 | 骨质疏松症案例研究 |
| ChEMBL | 药物-靶点-适应症关系 | 富集分析（已知药物靶点验证） |
| CRISPR/Cas9 敲除筛选 | 人成骨细胞（hFOB1.19）矿化实验，3 次独立重复 | 功能验证 |

### 评测协议

- 训练/验证/测试划分：按染色体划分（chr1-2 为测试集），避免泄漏
- 基线：Enformer-CAGE 适配、最近邻基因基线、距离阈值基线、L2G
- 指标：AUPRC、AUROC、富集倍数（enrichment fold）、hit 率

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 架构基准（酵母 MPRA） | Enformer 风格架构可捕获启动子调控语法 | Rosalind 主干 vs GeneGenie，相同数据/划分 | Enformer 风格 R = 0.98（测试集） | 长程 transformer 可扩展至精细调控语法 | 单一物种/启动子场景，不代表所有调控元件 | Results 图 1a |
| 架构基准（成骨细胞 MPRA） | 同上，在人类增强子场景成立 | 同上 | 未提供具体数值 | 跨物种/元件类型泛化 | 未提供效应量 | Results 图 1b |
| 微调后 V2G 分类（GTEx 测试集） | Rosalind 优于 Enformer-CAGE 与基线 | AUPRC/AUROC，按距离分层 | 未提供具体数值（摘要未给出） | 微调提升因果 V2G 识别 | 未提供与 L2G 的直接数值对比 | Results 图 1e |
| 距离分层分析 | Rosalind 在远端 V2G 上优势更明显 | 按变异-基因距离分层 | 未提供具体数值 | 距离近邻假设是主要偏差来源 | 未提供统计显著性 | Results 图 1e |
| 4 疾病 GWAS 泛化 | Rosalind 可推广至非 GTEx 组织/疾病 | T2D、高血压、哮喘、银屑病 | 预测基因集 >2 倍远端比例 vs L2G | 跨疾病泛化性 | 未提供与 L2G 的富集直接对比 | Results 图 2b |
| ChEMBL 药物靶点富集 | Rosalind 预测基因富集已知药物靶点 | 按临床阶段分层 | 富集随临床阶段递增 | 预测具有治疗相关性 | 未提供具体 p 值/效应量 | Results 图 2c |
| 已知药物靶点恢复 | Rosalind 恢复 L2G 遗漏的靶点 | GIPR、NDUFA7、GUCY1B1 等 | 成功恢复 | 远端预测可发现新靶点 | 案例数量有限 | Results 图 2e |
| eBMD 239 基因预测 | Rosalind 可系统识别骨质疏松风险基因 | 1,103 个信号 → 239 个高置信基因 | 多数为远端基因 | 可扩展至复杂性状 | 未提供与已知骨质疏松基因的重叠率 | Results 图 3c |
| 已知通路恢复 | 预测基因覆盖已知骨生物学通路 | RANK/RANKL/OPG、胶原、WNT | TNFRSF11A/B、COL1A1/2、WNT1 被恢复 | 预测具有生物学合理性 | 未提供系统通路富集分析 | Results 图 3c |
| 单变异案例（rs914615→FDPS） | Rosalind 可识别远端药物靶基因 | FDPS vs 最近邻 THBS3 | FDPS 被预测且为双膦酸盐靶点 | 远端预测具有药理相关性 | 单案例 | Results 图 3c |
| 单变异案例（rs603424→CHUK） | 独立验证孟德尔随机化研究 | CHUK vs 最近邻 PKD2L1 | CHUK 被预测 | 跨方法一致性 | 单案例 | Results 图 3c |
| CRISPR 敲除筛选（整体） | Rosalind 远端预测基因富集功能 hit | 239 预测基因 vs 最近邻基因，成骨细胞矿化 | 远端基因 hit 率显著更高（McNemar p = 0.011） | 远端预测具有功能因果性 | 仅一个细胞类型/表型 | Results 图 3f |
| CRISPR 敲除筛选（分层） | 预测基因中敲除后矿化变化的亚型 | 12 个位点无 hit，8 个位点多个 hit | 存在多位点共调控 | 调控复杂性 | 未提供具体基因列表 | Results 图 3e-f |
| 纤毛基因富集 | Rosalind 预测基因富集纤毛结构基因 | CATIP、GANAB 等 | 2/10 远端 hit 为纤毛基因 | 纤毛在骨形成中的新角色 | 样本量小 | Results 图 3e |

---

## 11 结论正确解读

- **任务范围**：本文解决的是「从 GWAS lead variant 到效应基因」的 V2G 映射问题，而非「从序列预测 TF 结合」或「预测变异对 TF 结合亲和力的影响」。Rosalind 预测的是变异对基因表达的调控效应，不直接提供分子机制（如哪个 TF 介导）。
- **Oracle/真值输入**：训练标签来自 GTEx eQTL fine-mapping 的 PIP 值，这是计算推断而非实验验证的标签。PIP > 0.9 的变异被当作因果，但 fine-mapping 本身存在不确定性。
- **端到端状态**：从序列到基因预测是端到端的，但「变异 → 基因表达」的因果链未在单变异水平上逐一验证。CRISPR 验证的是基因敲除对表型的影响，而非变异对基因表达的因果效应。
- **算力成本**：未提供训练/推理的具体算力需求。Enformer 类模型推理成本较高，但本文未讨论。
- **历史数据依赖**：模型依赖 GTEx 的跨组织 eQTL 数据，可能偏向高表达基因或常见变异；对罕见变异或组织特异性调控的泛化能力未知。
- **最难情形**：距离近邻法表现尚可的简单位点（单基因邻近）不是 Rosalind 的优势场景；其优势在复杂位点（多基因邻近、远端增强子）。模型在无 eQTL 信号的组织或细胞类型中的表现未知。
- **群体/领域边界**：训练数据主要来自欧洲裔人群（GTEx、UK Biobank），对其他群体的适用性未验证。疾病范围限于复杂性状，未测试孟德尔疾病。
- **不确定性**：预测为概率输出，但未提供校准分析或置信区间。CRISPR 验证的统计功效未讨论。
- **有边界的复述**：Rosalind 在 GTEx fine-mapped eQTL 上微调后，能够在多个复杂疾病 GWAS 中优先考虑远端基因，且这些远端基因在成骨细胞矿化实验中比最近邻基因更频繁地产生功能表型。该结论限于：(1) 训练分布内的变异类型；(2) 成骨细胞这一特定细胞类型；(3) 矿化这一特定表型。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 无法排除其他效应细胞 | 作者指出不能排除最近邻基因在骨质疏松症其他效应细胞（如破骨细胞、骨细胞）中更活跃的可能性 | 未明确提及 | Discussion 段落 |
| 预测为相关性而非因果性 | 计算预测本身不证明因果性，需实验验证 | 结合更多功能实验（如报告基因、动物模型） | Discussion 段落 |
| 未覆盖所有信号 | 1,103 个信号中仅 239 个获得高置信基因预测，部分位点无预测 | 未明确提及 | Results 图 3c |
| 多基因调控复杂性 | 8 个位点存在多个基因同时影响矿化，单一基因分配可能过度简化 | 未明确提及 | Results 图 3e-f |
| 纤毛基因发现的样本量小 | 纤毛相关 hit 仅基于 2/10 个远端 hit 基因 | 需要更大规模验证 | Results 图 3e |

> 注：以上为作者在摘要与正文中明确或隐含承认的局限。作者未系统列出局限性清单，以上从 Discussion 与 Results 中提取。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 训练标签来自 fine-mapping PIP，而非实验验证的因果变异 | PIP 阈值可能引入标签噪声；fine-mapping 在 LD 复杂区域可能错误分配因果变异 | 标签质量直接决定模型上限 | 在独立数据集（如 CRISPR 验证的 eQTL）上评估模型性能 | Methods 节 |
| 与 L2G 的对比可能不公平 | L2G 是通用工具，未针对特定疾病优化；Rosalind 在 GTEx 上微调后天然偏向 eQTL 信号 | 基准对比的公平性影响结论强度 | 在相同输入特征和训练数据条件下重训 L2G 或使用更多基线 | Results 图 2a-b |
| 未报告与 Enformer 的详细对比数值 | 摘要仅称「generally outperforms」，未给出 AUPRC/AUROC 具体数值与置信区间 | 无法评估效应量大小 | 补充详细数值对比表 | Results 图 1e |
| CRISPR 验证的细胞模型为永生化/转化细胞系（hFOB1.19） | 细胞系可能不完全代表原代成骨细胞或体内骨形成过程 | 功能验证的外部效度 | 在原代细胞或类器官中重复验证 | Methods 节 |
| 远端基因富集 hit 的统计检验（McNemar p = 0.011）未报告效应量 | 显著但可能效应量小；未报告 hit 率的具体差异 | 效应量决定实际应用价值 | 报告 hit 率差异及 95% CI | Results 图 3f |
| 未讨论模型对罕见变异的性能 | GTEx eQTL 主要覆盖常见变异；罕见变异的调控效应可能不同 | 罕见变异在疾病中可能更重要 | 在罕见变异数据集（如 UK Biobank WES）上评估 | 未提供 |
| 未提供模型不确定性校准 | 二分类概率输出未校准，可能过度自信 | 影响下游决策（如靶点优先级排序） | 进行概率校准分析（如 reliability diagram） | 未提供 |
| 未讨论 RoPE 替换的消融实验 | 未证明 RoPE 相比原始相对位置编码的具体增益 | 架构选择的必要性未验证 | 在相同条件下对比 RoPE vs 原始位置编码 | Methods 节 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

### 可迁移概念

1. **「规避归纳偏置」的建模策略**：Rosalind 的核心贡献不是新架构，而是「不显式使用距离特征」这一设计决策。对 TF–DNA 结合机制课题：若用序列模型预测 TF 结合位点或变异效应，可考虑不预设「结合位点必须在启动子附近」的偏置，让模型从数据中学习长程调控关系。

2. **Fine-mapping PIP 作为弱监督标签**：用计算推断的 PIP 阈值（>0.9 / <0.01）构造二分类训练标签，避免了人工标注的成本和主观性。对 TF–DNA 课题：类似地，可以用 ChIP-seq 的 peak calling 置信度或 SNP 的 regulatory annotation 分数作为弱监督标签。

3. **「计算预测 → 功能验证」闭环**：Rosalind 的 CRISPR 敲除验证设计（预测基因 vs 最近邻基因的 side-by-side 比较）是建立因果性的有效范式。对 TF–DNA 课题：预测的 TF 靶基因可以通过报告基因实验或 CRISPR 干扰进行类似验证。

4. **「远端基因」概念对 TF 靶基因识别的启示**：TF 的结合位点可能远离其靶基因启动子（增强子-启动子环化），Rosalind 的远端预测框架可迁移到 TF 靶基因识别任务。

### 可迁移方法

1. **等位基因双编码 + 分类头**：对每个 SNP，分别编码参考/替代等位基因的序列窗口，拼接 embedding 后分类。这一范式可直接迁移到「预测变异是否影响 TF 结合」的任务。

2. **RoPE 替换相对位置编码**：对需要处理超长序列（>100 kb）的 TF 结合预测任务，RoPE 的外推能力可能优于原始 Enformer 的相对位置编码。

3. **按染色体划分训练/测试**：避免同一位点的连锁不平衡导致的信息泄漏，是序列模型评估的稳健策略。

4. **数据增强：随机插入非因果变异**：在训练窗口随机位置插入非因果变异，迫使模型学习「位置无关的变异效应」，这一策略可迁移到 TF 结合位点变异效应预测。

### 对 TF–DNA 课题的具体迁移建议

- 若目标是「从序列预测 TF 结合位点的变异效应」，可复用 Rosalind 的「参考/替代等位基因双编码 + 分类」框架，但将 GTEx eQTL 标签替换为 ChIP-seq 或 HT-SELEX 的 TF 结合亲和力变化标签。
- 若目标是「从 GWAS 变异识别 TF 介导的效应基因」，Rosalind 的预测可作为先验，再结合 TF motif 扫描和 3D 基因组数据（Hi-C）进行机制注释。
- Rosalind 的「远端基因富集功能验证」设计可迁移到 TF 靶基因验证：在疾病相关细胞类型中敲除预测的远端靶基因，与最近邻基因比较表型效应。

---

## 15 与已有知识连接

- **Enformer（Avsec et al., 2021, Nature Methods）**：Rosalind 的骨干架构直接继承自 Enformer，替换了位置编码并微调。Enformer 已展示从序列预测调控活性的能力，Rosalind 将其扩展到个体变异效应。
- **Borzoi（Calandrelli et al., 2023, Nature Machine Intelligence）**：同为 DNA foundation model，预测 RNA-seq 覆盖度。Rosalind 的「变异 → 表达扰动」思路与 Borzoi 的等位基因差异预测类似，但 Rosalind 直接以 V2G 分类为目标。
- **L2G（Open Targets, Mountjoy et al., 2021, Nature Genetics）**：当前广泛使用的 V2G 方法，整合多源数据但受距离偏置影响。Rosalind 的对比基准，也是本文要超越的对象。
- **SuSiE fine-mapping（Wang et al., 2020, AJHG）**：提供 PIP 标签的统计框架，是 Rosalind 训练数据的来源。
- **GTEx（Consortium, 2020, Science）**：eQTL 数据的标准资源，Rosalind 的微调数据来源。
- **eBMD GWAS（Morris et al., 2019, Nature Genetics）**：骨质疏松症遗传学的基础数据集，本文的应用场景。
- **孟德尔随机化研究（CHUK 与骨质疏松）**：本文独立验证了 rs603424→CHUK 的预测与近期 MR 研究一致，说明 Rosalind 可复现因果推断方法的结果。
- **对 TF–DNA 课题的连接**：本文的「远端调控基因」概念与增强子-启动子环化（Hi-C/3D 基因组）文献直接相关；TF 结合位点变异（如 CTCF、 enhancer TF）的效应预测是本文方法可迁移的自然延伸。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF 结合位点变异效应预测模型（TF-V2E）

- **名称**：TF-aware variant-to-effect predictor
- **来源局限/观察**：Rosalind 预测的是「变异 → 基因表达」，但不提供分子机制（哪个 TF 介导）。TF–DNA 结合机制课题需要更细粒度的「变异 → TF 结合亲和力」预测。
- **核心假设**：在 Rosalind 的「参考/替代等位基因双编码」框架上，加入 TF motif 位置权重矩阵（PWM）作为辅助特征，可以同时预测「变异是否影响 TF 结合」和「影响哪个 TF」。
- **初步方法**：以 HT-SELEX 或 ChIP-seq 的等位基因差异结合数据为标签，输入为包含变异位点的序列窗口 + 候选 TF 的 motif 嵌入，输出为结合亲和力变化（回归）或结合是否改变（分类）。
- **验证方式**：在独立 ChIP-seq 数据集上评估 AUROC；用 CRISPR 干扰验证预测的 TF-靶基因关系。
- **创新状态**：unverified（需验证 RoSALIND 框架在 TF 结合层面的可迁移性）

### 候选 2：无距离偏置的 TF 靶基因识别

- **名称**：Proximity-free TF target identification
- **来源局限/观察**：Rosalind 解决了「变异 → 基因」的距离偏置，但 TF 靶基因识别仍常依赖「结合位点最近基因」假设。Rosalind 的框架可迁移到 TF ChIP-seq 数据的靶基因分配。
- **核心假设**：TF 结合位点（peak）的靶基因可以通过序列模型预测，而非简单取最近基因；远端靶基因在 TF 功能中可能被系统性低估。
- **初步方法**：以 TF ChIP-seq peak 为输入，以 CRISPR 扰动后的差异表达基因（如来自 ENCODE 或 DepMap）为标签，微调 Rosalind 类模型预测「peak → 靶基因」关系。
- **验证方式**：在已知 TF（如 MYC、TP53）上比较预测靶基因与最近基因的 ChIP-seq 信号富集和功能富集。
- **创新状态**：unverified（需验证序列模型能否捕获 TF 靶基因特异性）

### 候选 3：Rosalind 预测与 TF motif 变异的整合分析

- **名称**：Integrating Rosalind V2G predictions with TF motif disruption scores
- **来源局限/观察**：Rosalind 预测的 V2G 关系不解释分子机制；TF motif 破坏（如 FABIAN-variant 或 motifbreakR）可提供机制线索，但两者未整合。
- **核心假设**：Rosalind 预测的远端 V2G 关系中，若变异同时破坏某个 TF 的 motif，则该 TF 可能是介导调控效应的关键因子。
- **初步方法**：对 Rosalind 预测的 V2G 对，计算变异位点的 TF motif 破坏分数；检验 motif 破坏是否富集于 Rosalind 高置信预测中；用共定位或孟德尔随机化验证。
- **验证方式**：在骨质疏松症数据中，检验 FDPS、CHUK 等位点的 motif 破坏模式；在独立 GWAS 中重复。
- **创新状态**：partially checked（motif 破坏分析已有工具，但整合 Rosalind 预测为新方向）

### 候选 4：跨细胞类型的 TF 介导 V2G 预测

- **名称**：Cell-type-specific TF-mediated V2G mapping
- **来源局限/观察**：Rosalind 使用组织无关的 GTEx 聚合数据，但 TF 结合和增强子活性高度细胞类型特异。Rosalind 未利用细胞类型信息。
- **核心假设**：在 Rosalind 框架中加入细胞类型特异的染色质可及性（ATAC-seq）或 TF 表达数据，可提升 V2G 预测的细胞类型特异性。
- **初步方法**：以 ENCODE 或 Roadmap 的细胞类型特异 ATAC-seq 作为辅助输入，微调 Rosalind 预测特定细胞类型中的 V2G 关系；在成骨细胞、破骨细胞等骨质疏松相关细胞类型中验证。
- **验证方式**：在细胞类型特异的 eQTL 数据（如 Osteoblast eQTL）上评估 AUROC；与 Rosalind 原版对比。
- **创新状态**：unverified（需验证细胞类型信息能否提升 V2G 精度）

### 候选 5：Rosalind 预测与 3D 基因组结构的整合

- **名称**：Integrating Rosalind with Hi-C for distal TF-target validation
- **来源局限/观察**：Rosalind 从序列预测 V2G，但未利用 3D 基因组结构（Hi-C、HiChIP）验证物理邻近性。TF 介导的远端调控依赖染色质环化。
- **核心假设**：Rosalind 预测的远端 V2G 对中，若变异位点与基因启动子存在 Hi-C 物理互作，则预测可信度更高。
- **初步方法**：对 Rosalind 预测的 V2G 对，叠加成骨细胞或相关组织的 Hi-C 数据；检验物理互作是否富集于高置信预测；构建整合评分。
- **验证方式**：在骨质疏松症数据中，比较有/无 Hi-C 支持的预测的 CRISPR 验证命中率。
- **创新状态**：partially checked（Hi-C 与 V2G 整合已有先例，但结合 Rosalind 为新方向）