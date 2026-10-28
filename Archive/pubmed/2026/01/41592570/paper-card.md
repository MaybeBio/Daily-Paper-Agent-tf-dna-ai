## 01 基本信息

- **标题**：ChromBERT: A foundation model for learning interpretable representations for context-specific transcriptional regulatory networks
- **作者与单位**：Yu, Zhaowei; Yang, Dongxu; Chen, Qianqian; Zhang, Yuxuan; Li, Zhanhao; Wang, Yucheng; Wang, Chenfei; Zhang, Yong（同济大学，Zhang Yong 为通讯作者）
- **期刊/预印本平台**：Cell Genomics
- **年份**：2026-01-28
- **论文类型**：研究论文（Research Article）
- **领域**：计算基因组学 / 转录调控 / 基础模型（Foundation Model）
- **关键词**：ChromBERT, transcriptional regulatory networks, foundation model, ChIP-seq, cistrome imputation, interpretability, context-specific regulation
- **DOI/arXiv 号**：10.1016/j.xgen.2025.101130
- **代码**：https://github.com/TongjiZhanglab/ChromBERT（含预训练模型，200 bp/1/2/4 kb 分辨率人类版本及 1 kb 小鼠版本）
- **数据**：Cistrome-Human-6K 数据集（Hugging Face: TongjiZhanglab/chrombert）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「蛋白质-DNA 互作 × AI 方法」方向，聚焦于**转录因子（TF）与 DNA 结合**的全局模式建模。与传统的序列基序方法不同，ChromBERT 直接以 ChIP-seq 结合谱（cistrome）为输入，通过掩码语言建模学习 TF 之间的共结合语法（co-binding syntax），并利用提示（prompt）增强的微调实现未见细胞类型的 cistrome 推断。其核心创新在于：(1) 将 TF–DNA 互作建模为「TF 语言」而非「DNA 序列语言」；(2) 通过嵌入位移（embedding shift）实现可解释的 TF 功能推断。该文为 TF–DNA 互作研究提供了一种不依赖 DNA 序列基序的互补路径，尤其适用于基序信息不完整或 TF 缺乏已知基序的场景。

---

## 02 一句话总结

ChromBERT 是一个在约 1,000 个转录调控因子的 ChIP-seq 结合谱上预训练的基础模型，通过掩码建模学习 TF 间的共结合语法，并利用提示增强微调在未见细胞类型中实现 cistrome 推断，同时通过嵌入位移分析揭示细胞类型特异的 TF 功能角色。

---

## 03 研究问题

- **具体问题**：如何在不依赖 DNA 序列基序的前提下，建模转录因子在不同细胞类型中的上下文特异性（context-specific）协同结合模式，并推断驱动特定调控结果的 TF？
- **为什么重要**：细胞类型特异的 ChIP-seq 数据极为稀疏，绝大多数 TF 在大多数细胞类型中缺乏结合谱。传统方法依赖 DNA 基序，但基序仅覆盖实际结合事件的一小部分，且许多 TF 缺乏已知基序。若能学习 TF 间的通用共结合语法，则可在缺乏直接实验数据的细胞类型中推断 TF 结合与功能。
- **现有方法不足**：
  - 序列基础模型（如 DNABERT-2、Enformer）主要建模 DNA 序列语法，难以直接捕捉反式作用因子（trans-acting regulators）的角色；
  - 传统 cistrome 推断方法（如 Avocado）缺乏可解释性，无法揭示 TF 间的功能协作关系；
  - 基序中心方法（motif-centric）受限于基序覆盖不全和上下文调制（co-factor、染色质状态等）的缺失。
- **精确的「Can ... ?」问题**：Can a foundation model pre-trained on large-scale ChIP-seq binding profiles learn the context-specific syntax of TF co-binding, and can this knowledge be transferred via prompt-enhanced fine-tuning to impute unseen cistromes and identify key regulatory drivers without requiring additional ChIP-seq experiments?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注「仅本文框架」的部分未经外部文献核验。

1. **ENCODE 与 Cistrome 时代（2012–2020）**：大规模 ChIP-seq 计划（ENCODE、Cistrome）提供了数千个 TF 结合谱，但覆盖的细胞类型有限，且数据高度稀疏。代表性方法：Cistrome Data Browser 的数据整合与质控流程。（经外部核验：Cistrome DB 为公开资源）
2. **序列基础模型（2021–2024）**：DNABERT、Enformer、Nucleotide Transformer 等模型在 DNA 序列上预训练，学习顺式调控语法。代表工作：Enformer（Avsec et al., 2021）利用长程序列上下文预测表达；DNABERT-2（Zhou et al., 2023）在基因组序列上预训练。局限：无法显式建模反式因子角色。（经外部核验：Enformer、DNABERT-2 为公开工作）
3. **染色质状态模型（2022–2024）**：EpiBERT、EPCOT 等模型整合染色质可及性与组蛋白修饰，但主要聚焦于顺式调控元件状态推断，未直接建模 TF 间互作。（仅本文框架）
4. **Cistrome 推断方法（2018–2023）**：Avocado（Schreiber et al., 2020）通过矩阵分解推断缺失的 ChIP-seq 信号，但缺乏可解释性，无法揭示 TF 功能角色。（经外部核验：Avocado 为公开工作）
5. **ChromBERT 的位置（2026）**：本文提出将 TF 结合谱本身作为「语言」进行建模，直接学习 TF 间的共结合语法。与序列模型互补，与 Avocado 相比提供可解释的 TF 嵌入。该方法填补了「反式因子互作语法」建模的空白。（仅本文框架）

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| ChIP-seq 数据极度稀疏 | 大多数 TF 在大多数细胞类型中缺乏结合谱；细胞类型特异数据难以获取 | 实验成本高、抗体质量参差、细胞类型多样性 | Results 节：cistrome imputation 任务设定；Figure 2B 中 baseline 性能低 |
| 基序信息不完整 | 许多 TF 缺乏已知基序；基序仅覆盖实际结合事件的一小部分 | TF 结合受 co-factor、染色质状态、竞争结合等上下文因素调制 | Introduction 节：motif-centric approaches are insufficient |
| 序列模型无法捕捉反式因子角色 | DNA 序列模型（Enformer、DNABERT-2）无法显式建模 TF 间的协同/竞争关系 | 序列模型输入为 DNA，输出为调控信号，中间表征不直接对应 TF 身份 | Introduction 节：models often fall short in addressing the roles of trans-acting regulators |
| 现有 cistrome 推断缺乏可解释性 | Avocado 等矩阵分解方法可预测信号但无法揭示 TF 功能角色 | 潜在表征不分解为每个 TF 的独立嵌入 | Results 节：与 Avocado 对比；Figure 2F |
| 细胞类型特异性难以建模 | 同一 TF 在不同细胞类型中可能扮演不同角色（激活 vs 抑制） | 共结合伙伴和染色质环境随细胞类型变化 | Results 节：EZH2 双角色分析；Figure 3I |
| 注意力权重不适合直接推断 TF 互作 | 注意力矩阵对层、头敏感，难以跨层稳定比较 | 注意力描述信息流而非功能关系 | Methods 节：Interpretation analysis 部分，作者选择嵌入位移而非注意力 |

---

## 06 核心思想

### 1) 表面方法

ChromBERT 将每个 1 kb 基因组区间的 TF 结合状态编码为一个「句子」，其中每个「词」是一个 cistrome（即一个 TF 在一个细胞类型中的结合谱）的结合状态。采用 BERT 风格的掩码语言建模：随机掩码 15% 的结合状态，训练模型从其余 TF 的上下文预测被掩码的 TF 是否结合。预训练后，通过提示增强微调（prompt-enhanced fine-tuning）将细胞类型信息（如染色质可及性或转录组）作为提示注入模型，实现未见细胞类型的 cistrome 推断。

### 2) 核心洞察

- **TF 结合谱是「语言」而非「序列」**：TF 间的共结合模式（谁与谁在同一区域共现）构成一种可学习的语法，这种语法比 DNA 序列基序更直接地反映功能互作。
- **嵌入位移作为功能变化的指标**：当模型被微调以预测特定细胞类型的调控结果时，如果某个 TF 的嵌入在结果不同的区域间发生系统性位移，则该 TF 很可能是驱动该结果的关键调控因子。这一原则不依赖任何先验知识或 ChIP-seq 数据。
- **提示（Prompt）作为细胞类型信息的载体**：将染色质可及性或转录组数据编码为提示向量，与 TF 嵌入拼接，使模型能够将预训练中学到的通用共结合语法适配到特定细胞类型。

### 3) 可能的普适教训 [Analysis]

- **将「实体间共现关系」而非「实体自身属性」作为建模对象**：ChromBERT 的成功表明，在数据稀疏的生物场景中，建模实体间的相对关系（谁与谁共现）可能比建模实体本身的绝对属性更鲁棒、更可迁移。
- **嵌入位移作为可解释性工具**：在监督微调后比较嵌入空间中的位移，是一种不依赖注意力权重或梯度归因的通用可解释性方法，尤其适用于高维、多模态输入的场景。
- **提示工程在生物基础模型中的价值**：将稀缺的细胞类型信息编码为提示而非重新训练，是应对生物数据稀疏性的有效策略。

---

## 07 方法总览

- **输入**：每个 1 kb 基因组区间的 TF 结合状态向量 X ∈ R^P，其中 P = 6,391 为 cistrome 数量（覆盖 991 个 TF、76 个组蛋白修饰和染色质可及性）。结合状态由 ChIP-seq 信号经阈值化离散为 5 类（从「强阴性」到「强阳性」）。
- **输出**：
  - 预训练：被掩码的结合状态的类别预测；
  - 微调：下游任务的预测（如 cistrome 结合概率、基因表达变化、染色质可及性变化）；
  - 解释：每个 TF 在每个基因组区间的嵌入向量（768 维）。
- **模型架构**：
  - 输入嵌入层：位置嵌入（区分不同 cistrome）+ token 嵌入（结合状态类别）；
  - 编码器：8 层 Transformer，每层含多头自注意力（8 头）和前馈网络，隐藏维度 768；
  - 解码器：2 层 MLP，将编码器输出映射到 5 类结合状态的概率分布。
- **预训练**：掩码语言建模，掩码率 15%，损失函数为 focal loss（γ=2）以应对类别不平衡。训练数据为 2,137,894 个 1 kb 区间。
- **微调**：
  - 选择性解冻：冻结早期 Transformer 层，仅解冻最后若干层和解码器；
  - 提示注入：将细胞类型特异的染色质可及性或转录组数据编码为提示向量，与 TF 嵌入拼接后输入解码器；
  - 任务类型：分类（cistrome 有无）或回归（表达/可及性变化）。
- **解释分析**：对每个 TF，计算其在两组区域（如表达升高 vs 不变）间的平均嵌入位移（1 − cosine similarity），按位移大小排序识别关键调控因子。
- **训练资源**：4× NVIDIA A800 80GB GPU，约 23 天完成预训练（100 epochs）。

**文字流程**：
1. 从 Cistrome Data Browser 收集所有人类 ChIP-seq/DNase-seq/ATAC-seq 数据，经质控筛选（5 项 QC 指标中至少满足 4 项）得到 6,391 个 cistrome；
2. 将每个 cistrome 的信号在 1 kb 区间上离散化为 5 类结合状态；
3. 构建输入矩阵 S ∈ R^(N×P)，N = 2,137,894 个区间，P = 6,391 个 cistrome；
4. 随机掩码 15% 的条目，训练 Transformer 编码器 + MLP 解码器重建被掩码条目；
5. 预训练完成后，针对下游任务进行提示增强微调：将细胞类型信息（染色质可及性或转录组）编码为提示向量，与 TF 嵌入拼接，训练解码器预测目标；
6. 微调后，对每个 TF 计算嵌入位移，排序识别关键调控因子。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 输入嵌入层（位置 + token 嵌入） | 将离散结合状态映射为稠密向量，并编码 cistrome 身份 | Transformer 需要稠密向量输入，且需区分不同 cistrome | 输入：结合状态类别 + cistrome 索引；输出：768 维嵌入 | Methods 节：Equation 1 | 预期影响：模型无法区分不同 TF，退化为全局共现统计 [预期效应] |
| 8 层 Transformer 编码器 | 通过自注意力学习 TF 间的共结合依赖 | 核心机制：捕捉任意两个 cistrome 间的上下文依赖 | 输入：输入嵌入；输出：上下文感知的 TF 嵌入 | Methods 节：Architecture；Figure 1A | 预期影响：模型退化为线性模型，无法捕捉高阶互作 [预期效应] |
| 掩码语言建模预训练目标 | 从上下文预测被掩码 TF 的结合状态 | 自监督学习 TF 共结合语法，无需标注数据 | 输入：掩码后的结合状态矩阵；输出：被掩码条目的类别分布 | Methods 节：Pre-training；Figure 1A | 预期影响：模型无法学习 TF 间依赖关系 [预期效应] |
| Focal loss | 缓解 5 类结合状态的类别不平衡 | 大多数区间为「强阴性」，简单交叉熵会被多数类主导 | 输入：预测分布 + 真实标签；输出：损失标量 | Methods 节：Equation 4 | 预期影响：模型偏向预测多数类，稀有结合模式被忽略 [预期效应] |
| 提示增强微调（Prompt-enhanced fine-tuning） | 将细胞类型信息注入模型，实现跨细胞类型泛化 | 预训练是细胞类型无关的，需要适配特定细胞类型 | 输入：TF 嵌入 + 提示向量（染色质可及性或转录组）；输出：下游任务预测 | Results 节：Figure 2A；Methods 节：Fine-tuning with prompts | 预期影响：模型无法区分细胞类型，cistrome 推断退化为全局平均 [预期效应] |
| 嵌入位移分析（Embedding shift） | 量化 TF 在两组区域间的嵌入变化，识别关键调控因子 | 提供可解释的 TF 功能推断，不依赖额外实验 | 输入：微调后的 TF 嵌入；输出：每个 TF 的位移分数及排名 | Results 节：Figure 3A；Methods 节：Interpretation analysis | 预期影响：无法识别驱动调控结果的 TF [预期效应] |
| 选择性解冻（Selective unfreezing） | 冻结早期层，仅微调后期层和解码器 | 保留预训练学到的通用语法，避免小样本过拟合 | 输入：预训练权重；输出：微调后的权重 | Methods 节：Basic principle of fine-tuning | 预期影响：全量微调可能导致灾难性遗忘 [预期效应] |

---

## 09 关键公式符号

**1. 输入嵌入（Equation 1）**：
E_i^(input) = Emb_position(v) + Emb_token(X_i)

- E_i^(input) ∈ R^(P×d_input)：第 i 个 1 kb 区间的输入嵌入，d_input = 768
- v = [id(1), id(2), ..., id(P)]：cistrome 的位置索引向量
- X_i = [X_i,1, X_i,2, ..., X_i,P]：第 i 个区间的结合状态向量，X_i,j ∈ {1,2,3,4,5}（5 类离散状态）
- Emb_position、Emb_token：PyTorch 嵌入层

**2. 自注意力（Equations 2-3）**：
Q = E_i^(l−1) W_q^(l), K = E_i^(l−1) W_k^(l), V = E_i^(l−1) W_v^(l)
Attention(Q, K, V) = softmax(QK^T / √d_model) V

- E_i^(l−1)：第 (l−1) 层输出，E_i^(0) = E_i^(input)
- W_q^(l), W_k^(l), W_v^(l) ∈ R^(d_model×d_model)：第 l 层的查询、键、值权重矩阵
- d_model = 768：隐藏维度
- 8 个注意力头并行计算

**3. Focal loss（Equation 4）**：
FL_multi(ŷ, y) = −Σ_{c_j ∈ c_masked} Σ_{t=1}^{5} (1 − ŷ_{j,t})^γ · y_{j,t} · log(ŷ_{j,t})

- ŷ_{j,t}：模型对 cistrome c_j 在类别 t 的预测概率
- y_{j,t}：指示变量，真实类别为 t 时取 1
- γ = 2：聚焦参数
- c_masked：被掩码的 cistrome 集合

**4. 嵌入位移（Equation 8）**：
D_m(G1, G2) = 1 − (Ē'_G1,m · Ē'_G2,m) / (‖Ē'_G1,m‖ · ‖Ē'_G2,m‖)

- Ē'_G,m = (1/|G|) Σ_{i∈G} E'_i,m^(TRN)：TF m 在区域集合 G 上的平均嵌入
- G1, G2：具有不同调控结果的两组区域
- D_m 值越大，表示 TF m 在两组区域间的上下文变化越大，越可能是关键调控因子

**5. 余弦相似度（Equation 6）**：
CS_bi(r_j, r_k) = (E'_i,j^(TRN) · E'_i,k^(TRN)) / (‖E'_i,j^(TRN)‖ · ‖E'_i,k^(TRN)‖)

- 用于量化两个 TF 在给定区域中的嵌入相似度，推断功能协作关系

---

## 10 实验设计与证据链

- **数据集**：
  - 预训练：Cistrome-Human-6K，6,391 个 cistrome（991 个 TF、76 个组蛋白修饰、染色质可及性），2,137,894 个 1 kb 区间，覆盖 100+ 组织/细胞类型
  - cistrome imputation 测试：241 个未见 cistrome（细胞系 + 原代细胞）
  - 单细胞测试：PBMC 10× Multiome 数据集（9,493 个细胞，5 大细胞类型）
  - eQTL 精细定位：EBI eQTL Catalog，49 个组织
  - 增强子活性：STARR-seq（HCT116 细胞，EP300/CREBBP、BRD2、CDK7 扰动）
  - EZH2 分类：hESC（H1）中 EZH2 与 H3K27me3 ChIP-seq

- **指标**：AUROC、AUPRC、Pearson 相关系数

- **基线**：
  - cistrome imputation：Avocado、基于候选峰+染色质可及性的 baseline
  - eQTL 分类：Enformer、DNABERT-2、ChromBERT（无预训练）
  - EZH2 分类：Enformer、DNABERT-2、ChromBERT（无预训练）

- **评测协议**：10 折交叉验证（eQTL 任务）；训练/测试 6:4 划分；cistrome imputation 中测试 cistrome 完全排除在预训练和微调之外

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 预训练嵌入聚类分析 | 嵌入能反映已知调控元件类型 | 对 ChromHMM 状态分组计算嵌入相似度 | 不同 ChromHMM 状态聚类分离；TAD 内区域相似度更高 | 嵌入编码了调控元件类型和 3D 基因组结构 | 未证明嵌入因果性地编码调控功能 | Results 图 S2A–S2D |
| Hi-C 接触预测 | 嵌入相似度与染色质接触相关 | 嵌入相似度 vs Hi-C 接触 vs 随机 | 有接触的区域对嵌入相似度显著更高 | 嵌入捕捉了 3D 染色质组织信息 | 未证明嵌入可用于从头预测 Hi-C | Results 图 S2E–S2H |
| cistrome imputation（241 个未见 cistrome） | ChromBERT 优于现有方法 | ChromBERT-D vs baseline vs Avocado | ChromBERT-D AUPRC=0.554，baseline=0.271；vs Avocado：0.659 vs 0.514 | ChromBERT-D 显著优于 baseline 和 Avocado | 未在全部 241 个 cistrome 上与 Avocado 对比（仅 57 个可比） | Results 图 2B、2F |
| 细胞类型特异结合位点识别 | 能区分染色质可及性相似但结合特异的位点 | ChromBERT-D 预测 vs ChIP-seq 真实值 | 在可及性相似的位点中，ChromBERT-D 能正确区分结合与不结合 | 模型捕捉了超出染色质可及性的结合特异性 | 未证明模型学到了 TF 特异的序列偏好 | Results 图 2C–2E |
| 单细胞 cistrome 推断 | 能从单细胞转录组推断单细胞结合谱 | ChromBERT-R 预测 vs 单细胞 ATAC-seq 基序可及性 | 8 个 TF 在 B 细胞中预测准确率显著高于基序+可及性 baseline | 单细胞 RNA-seq 提示可有效推断单细胞结合 | 仅验证了 B 细胞，未覆盖所有细胞类型 | Results 图 S5A–S5C |
| eQTL 因果变异分类（49 组织） | ChromBERT 优于序列模型 | ChromBERT vs Enformer vs DNABERT-2 vs 无预训练 | ChromBERT AUROC=0.828，Enformer=0.770，DNABERT-2=0.788，无预训练=0.804 | 预训练和 TF 共结合上下文均提升分类性能 | 未与更近期序列模型（如 Nucleotide Transformer）对比 | Results 图 3B |
| 嵌入位移识别 eQTL 关键 TF | 位移大的 TF 更可能是因果调控因子 | 位移排名 vs 基序富集 | 位移前 20% 的 TF 在因果 eQTL 处基序出现率更高、基序亲和力变化更大 | 嵌入位移可识别功能相关的 TF | 未用 CRISPR 等实验验证因果性 | Results 图 3C、3D |
| EP300 扰动预测 | 模型能预测增强子对 EP300 的依赖性 | 预测 vs STARR-seq 实测（EP300 降解） | 预测与实测 Pearson r 显著为正；识别出 FOSL1、JUND 等 EP300 共因子 | 嵌入位移可揭示共因子依赖关系 | 仅验证了 EP300，未推广到其他因子 | Results 图 3E–3H |
| EZH2 经典/非经典位点分类 | 模型能区分 EZH2 的两种功能模式 | ChromBERT vs Enformer vs DNABERT-2 | ChromBERT 分类性能最优 | 嵌入可区分 EZH2 的经典（H3K27me3 依赖）和非经典功能 | 未验证非经典位点的生物学功能 | Results 图 3I、S7G |
| 数据稀疏鲁棒性 | 在训练数据减少时仍保持性能 | 不同训练集大小 | 即使训练数据减少，ChromBERT 仍优于 baseline | 预训练提供了鲁棒的初始化 | 未测试极端稀疏（<10% 数据）场景 | Results 图 S9 |

---

## 11 结论正确解读

- **任务范围**：本文的 cistrome imputation 任务预测的是 TF 结合的有无（二分类），而非结合强度或占据率。预测分辨率是 1 kb，无法区分同一区间内的多个结合事件。
- **Oracle/真值输入**：cistrome imputation 使用了染色质可及性（DNase-seq）作为提示，这本身是实验数据。在完全没有实验数据的「冷启动」场景下，模型性能未经验证。
- **端到端状态**：模型并非端到端地从 DNA 序列预测 TF 结合。它需要至少一种细胞类型特异性的提示数据（染色质可及性或转录组）。因此，它不能替代从头预测，而是「填充缺失 TF」的工具。
- **算力成本**：预训练约 23 天（4× A800），对大多数实验室而言成本较高。但微调成本较低，且预训练模型已公开。
- **历史数据依赖**：预训练数据来自 Cistrome 数据库，存在对已充分研究的 TF 和细胞类型的偏向。未充分研究的 TF 可能嵌入质量较低。
- **最难场景**：对于缺乏任何细胞类型特异性提示数据的场景，或对于在预训练数据中极少出现的 TF，模型性能可能显著下降。
- **群体/领域边界**：模型基于人类数据预训练，小鼠版本仅提供 1 kb 分辨率。跨物种迁移未验证。
- **不确定性**：嵌入位移分析提供的是相关性而非因果性证据。作者未用遗传扰动实验验证预测的 TF 确实驱动调控结果。

**有边界的复述**：ChromBERT 在已有染色质可及性或转录组数据的细胞类型中，能够以优于现有方法的准确率推断未见 TF 的结合谱，并通过嵌入位移分析识别候选关键调控因子；但其预测依赖于提示数据的可用性，且功能推断未经实验因果验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 预训练数据覆盖有限 | 仅约 1,000 个 TF 有 ChIP-seq 数据，许多 TF 未被覆盖 | 扩展 ChIP-seq 数据覆盖范围 | Limitations 节 |
| 细胞类型特异性模糊 | 预训练数据跨细胞类型池化，可能模糊细胞类型特异的结合模式 | 在预训练中引入细胞类型标签或条件编码 | Limitations 节 |
| 跨模态对齐困难 | 将染色质可及性、组蛋白修饰、TF 结合统一编码为离散状态，可能丢失定量信息 | 探索连续值编码或更细粒度的离散化 | Limitations 节 |
| 单细胞分辨率有限 | 单细胞推断依赖 scGPT 的细胞嵌入，可能无法捕捉稀有细胞状态 | 开发更精细的单细胞提示编码 | Limitations 节 |
| 超参数未系统优化 | Transformer 层数、隐藏维度等未进行系统搜索 | 进行更全面的超参数优化 | Limitations 节 |
| 多模态融合简单 | 提示通过简单拼接注入，未学习复杂的跨模态交互 | 探索更复杂的注意力融合机制 | Limitations 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| cistrome imputation 的 baseline 较弱 | baseline 仅使用候选峰+染色质可及性，未与更近期方法（如基于深度学习的 TF 结合预测器）对比 | 若 baseline 过弱，性能优势可能被夸大 | 与 Enformer 微调、DeepSEA、Basenji 等模型在相同任务上对比 | Results 图 2B、2F |
| 嵌入位移分析缺乏因果验证 | 位移大的 TF 可能只是与染色质状态变化相关，而非驱动变化 | 无法区分因果与关联，限制了生物学结论的强度 | 对预测的 TF 进行 CRISPR 敲低/降解实验，验证调控结果是否改变 | Results 图 3C–3I |
| 1 kb 分辨率可能掩盖精细结合模式 | 多个 TF 结合位点可能共存于同一 1 kb 区间，离散化丢失了结合位点的精确位置 | TF 结合是位点级事件，1 kb 分辨率可能不足以捕捉竞争性结合等精细机制 | 在更高分辨率（如 100 bp）上重新训练并比较性能 | Methods 节：Binding status encoding |
| 预训练数据存在选择偏差 | Cistrome 数据库偏向已充分研究的 TF 和细胞类型 | 模型对稀有 TF 或罕见细胞类型的泛化能力可能有限 | 在低资源 TF/细胞类型上评估性能，与高资源子集对比 | Methods 节：Assembly of cistromes |
| 与序列模型的比较不公平 | ChromBERT 使用 ChIP-seq 作为输入，而 Enformer/DNABERT-2 仅使用 DNA 序列 | 输入信息量不同，性能差异可能主要来自输入而非模型架构 | 在相同输入条件下对比（如仅用 DNA 序列微调 ChromBERT） | Results 图 3B |
| 注意力机制未用于解释 | 作者选择嵌入位移而非注意力权重进行解释，但未系统比较两种解释的一致性 | 若注意力与嵌入位移给出矛盾结论，解释框架的可信度存疑 | 在多个任务中比较注意力权重与嵌入位移排名的一致性 | Methods 节：Interpretation analysis |
| 单细胞验证仅限 B 细胞 | 单细胞 cistrome 推断仅在 PBMC 的 B 细胞中验证 | 其他细胞类型的泛化能力未知 | 在更多细胞类型（如 T 细胞、单核细胞）中验证 | Results 图 S5 |

---

## 14 学到什么

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的可迁移知识。

### 概念层面

1. **「TF 语言」范式**：将 TF 结合谱视为一种语言，用掩码建模学习 TF 间的共现语法。这一范式可迁移到任何「实体-实体」互作网络建模，尤其是当实体数量大、互作数据稀疏时。
2. **嵌入位移作为功能指标**：在监督微调后比较嵌入位移，是一种不依赖先验知识的功能推断方法。可迁移到 TF–DNA 结合机制研究：例如，比较 TF 在激活 vs 抑制靶基因区域的嵌入差异，识别决定功能方向的序列或染色质特征。
3. **提示增强的跨条件泛化**：将稀缺的条件信息（细胞类型、处理条件）编码为提示，而非重新训练模型。可迁移到物理模拟中：将温度、离子浓度等条件作为提示注入 MD 模拟的势函数或增强采样偏置。

### 方法层面

4. **离散化结合状态**：将连续 ChIP-seq 信号离散化为 5 类状态，既保留强度信息又降低噪声敏感性。可迁移到 TF–DNA 结合机制研究中：将结合亲和力（如 Kd 值）离散化，用于训练分类模型。
5. **选择性解冻微调**：冻结早期层、微调后期层，在数据稀疏时保留预训练知识。可迁移到小样本场景下的 TF–DNA 结合预测模型微调。
6. **Focal loss 处理类别不平衡**：TF 结合事件在基因组上极为稀疏（大多数区域无结合），focal loss 可迁移到任何结合位点预测任务。

### 实验设计层面

7. **多任务验证框架**：同一模型在 cistrome imputation、eQTL 精细定位、增强子活性预测、EZH2 功能分类等多个任务上验证，增强了结论的稳健性。可迁移到 TF–DNA 结合机制研究：用同一模型同时预测结合、功能、进化保守性，交叉验证。
8. **嵌入位移与外部数据的交叉验证**：用基序富集、ChIP-seq 等独立数据验证嵌入位移的生物学意义。可迁移到物理模拟：用 MD 模拟的接触频率或结合自由能验证 AI 模型的嵌入位移。

---

## 15 与已有知识连接

- **与序列基础模型的关系**：ChromBERT 与 DNABERT-2、Enformer 等序列模型互补。序列模型捕捉顺式调控语法（DNA 序列特征），ChromBERT 捕捉反式调控语法（TF 共结合模式）。两者可组合：序列模型提供序列嵌入，ChromBERT 提供 TF 上下文嵌入，联合预测结合。本文在 eQTL 任务中展示了这种组合的潜力（DNABERT-2 序列嵌入作为提示）。
- **与 cistrome 推断方法的关系**：Avocado 是矩阵分解方法，ChromBERT 是深度学习方法。ChromBERT 的优势在于可解释的 TF 嵌入和提示增强的泛化能力。Avocado 的优势在于计算效率。两者可视为互补工具。
- **与 3D 基因组的关系**：ChromBERT 嵌入与 TAD 和染色质接触相关（图 S2D–S2H），表明 TF 共结合模式与 3D 基因组组织密切相关。这为「TF 结合 → 染色质折叠 → 基因表达」的因果链提供了新的表征工具。
- **与 TF–DNA 结合机制研究的连接**：ChromBERT 的嵌入位移分析可视为一种「计算表型」——将 TF 的功能角色（激活 vs 抑制、经典 vs 非经典）编码为嵌入空间中的方向。这与物理模拟中的「结合自由能变化」或「构象集合位移」形成类比：两者都试图量化 TF 在不同上下文中的行为变化。
- **与单细胞调控研究的连接**：ChromBERT 的单细胞推断（图 S5）表明，转录组提示可以替代染色质可及性提示，这为 scRNA-seq 数据丰富的场景提供了 TF 结合推断的新途径。
- **潜在冲突**：ChromBERT 的输入是 ChIP-seq 结合状态，而 ChIP-seq 反映的是 TF 在固定细胞状态下的平均结合。对于动态结合过程（如 TF 在增强子-启动子环上的瞬时结合），ChromBERT 的表征可能不够精细。物理模拟（如 MD）可补充这一时间分辨率缺口。

---

## 16 研究想法

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的研究候选。

### 候选 1：TF–DNA 结合机制的多尺度嵌入对齐
- **名称**：Cross-scale TF binding embedding alignment
- **来源局限/观察**：ChromBERT 的嵌入编码了 TF 共结合上下文，但缺乏序列级和原子级分辨率；MD 模拟提供原子级结合机制，但难以覆盖全基因组。
- **核心假设**：TF 在 ChromBERT 嵌入空间中的位移方向与 MD 模拟中 TF 结合构象的变化方向存在可学习映射。
- **初步方法**：选取 10-20 个 TF，对每个 TF 的典型结合位点（已知激活 vs 抑制靶标）进行 MD 模拟，提取结合自由能、构象集合差异等特征；将 ChromBERT 的嵌入位移作为「计算表型」，训练一个映射模型（如 CCA 或神经网络）将两者对齐。
- **验证方式**：在未见 TF 上测试映射的泛化能力；用突变实验（如 TF 的 DNA 结合域点突变）验证预测的构象变化。
- **创新状态**：unverified

### 候选 2：提示增强的 TF–DNA 结合自由能预测
- **名称**：Prompt-conditioned binding free energy prediction
- **来源局限/观察**：ChromBERT 的提示机制表明，条件信息（细胞类型、染色质状态）可以高效注入预训练模型。MD 模拟的势函数同样需要条件化（如离子浓度、温度）。
- **核心假设**：将 ChromBERT 的 TF 嵌入作为条件输入，可以提升 MD 或对接方法对 TF–DNA 结合自由能的预测精度，尤其是在缺乏实验数据的 TF 上。
- **初步方法**：对一组 TF–DNA 复合物，计算 ChromBERT 的 TF 嵌入和 DNA 序列嵌入；将嵌入作为条件特征，训练一个图神经网络或等变网络预测结合自由能；与仅使用序列特征的基线对比。
- **验证方式**：在实验测定的结合亲和力数据集（如 PBAD、CIS-BP）上评估；在未见 TF 上进行零样本测试。
- **创新状态**：unverified

### 候选 3：TF 功能二态性的嵌入-构象联合分析
- **名称**：Dual-state TF functional embedding analysis
- **来源局限/观察**：ChromBERT 成功区分了 EZH2 的经典（H3K27me3 依赖）和非经典功能，但未提供分子机制解释。MD 模拟可以揭示这两种功能状态下的构象差异。
- **核心假设**：TF 在功能二态（如激活 vs 抑制）下的 ChromBERT 嵌入位移与 MD 模拟中的构象状态转换（如 apo vs holo、单体 vs 二聚体）存在对应关系。
- **初步方法**：以 EZH2 为案例，对其经典和非经典结合位点分别进行 MD 模拟，比较构象集合；将 ChromBERT 的嵌入位移与构象差异特征（如 RMSD、接触图差异）进行关联分析。
- **验证方式**：在 3-5 个具有已知双功能的 TF 上重复分析；用 FRET 或 HDX 实验验证预测的构象状态。
- **创新状态**：unverified

### 候选 4：跨物种 TF 共结合语法迁移
- **名称**：Cross-species TF co-binding syntax transfer
- **来源局限/观察**：ChromBERT 仅提供人类和小鼠版本，但 TF 共结合语法可能部分保守。MD 模拟的力场参数通常也是跨物种的。
- **核心假设**：人类预训练的 TF 共结合语法可以部分迁移到其他物种，迁移效果与物种的系统发育距离和 TF 保守性相关。
- **初步方法**：在人类 ChromBERT 基础上，用少量其他物种（如斑马鱼、果蝇）的 ChIP-seq 数据进行微调；评估 cistrome imputation 性能与物种距离的关系；对迁移效果差的 TF 进行 MD 模拟，检查其 DNA 结合域的结构保守性。
- **验证方式**：在 3-5 个物种上评估迁移性能；与从头训练的模型对比。
- **创新状态**：unverified

### 候选 5：TF 结合位点的可解释序列-上下文联合表征
- **名称**：Interpretable sequence-context joint representation for TF binding
- **来源局限/观察**：ChromBERT 的输入是结合状态而非 DNA 序列，因此无法直接解释序列变异（如 SNP）对 TF 结合的影响。序列模型（如 Enformer）可以处理序列变异，但缺乏 TF 共结合上下文。
- **核心假设**：将 ChromBERT 的 TF 共结合嵌入与序列模型的序列嵌入联合，可以同时捕捉序列基序和共结合上下文，从而更准确地预测 SNP 对 TF 结合的影响。
- **初步方法**：对每个 1 kb 区间，分别计算 ChromBERT 的 TF 共结合嵌入和 DNABERT-2/Enformer 的序列嵌入；训练一个融合模型预测 TF 结合；用 eQTL 数据评估 SNP 效应的预测精度。
- **验证方式**：在 eQTL 精细定位任务上与 ChromBERT 单独使用对比；用 CRISPR 突变验证预测的 SNP 效应。
- **创新状态**：unverified