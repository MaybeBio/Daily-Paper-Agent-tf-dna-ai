## 01 基本信息

- **标题**：scTFBridge: A Disentangled Deep Generative Model Informed by TF-Motif Binding for Gene Regulation Inference in Single-Cell Multi-Omics
- **作者与单位**：Feng-ao Wang; Ruikun He; Junwei Liu; Yixue Li（单位未在提供材料中明确列出，推测与广州实验室/中国科学院相关，依据致谢部分）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025-01-20
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：单细胞多组学 × 深度学习 × 基因调控网络推断
- **关键词**：单细胞多组学、深度生成模型、解耦表征学习、TF-motif 结合、基因调控网络、可解释性
- **DOI/arXiv 号**：10.1101/2025.01.16.633293
- **代码**：https://github.com/FengAoWang/scTFBridge
- **数据**：BMMC (GSE194122)、PBMC (10x Genomics)、类风湿关节炎 (GSE243917)、肺组织 (GSE2414468)；eQTL 数据来自 scQTLbase；ChIP-seq 数据来自 Cistrome；GWAS 数据 GCST90132222
- **阅读日期**：2025-06-30（按当前日期推断）
- **在课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向，核心创新在于将 TF–motif 结合先验知识嵌入深度生成模型的解码器权重约束中，实现生物学可解释的共享潜空间，并利用 SHAP 进行 cis/trans 调控推断。与纯物理模拟（MD/对接）路线互补，属于「知识引导的 AI 建模」范式。

---

## 02 一句话总结

本文提出 scTFBridge——一个基于混合 VAE 的解耦深度生成模型，通过互信息最小化将单细胞 RNA-seq 和 ATAC-seq 潜变量分解为共享/私有子空间，并用 TF–motif 结合分数约束 ATAC 解码器权重，使共享潜变量对应特定 TF 调控活性，最终用 SHAP 推断 cis（RE–TG）和 trans（TF–TG）调控关系，在多个单细胞多组学数据集上优于基线方法。

---

## 03 研究问题

- **具体问题**：如何从配对的单细胞 RNA-seq 和 ATAC-seq 数据中，推断细胞类型特异的基因调控网络（GRN），同时保证模型的生物学可解释性？
- **为什么重要**：GRN 是理解细胞身份建立、维持及疾病机制的核心。单细胞多组学提供了同一细胞内转录组和染色质可及性的联合测量，为单细胞分辨率 GRN 推断提供了前所未有的机会，但多组学数据的高维性、异质性和模态差异（modality gap）使得现有方法难以准确捕获调控关系。
- **现有方法不足**：
  - 单组学方法（如仅用 scRNA-seq 的 GENIE3、PIDC）无法利用染色质可及性信息，且对数据稀疏性敏感；
  - 多组学整合方法（如 MultiVI、scGLUE）主要优化细胞嵌入对齐，未显式建模 TF–RE–TG 调控链；
  - 现有 GRN 推断方法（如 SCENIC+）虽整合多组学，但缺乏对共享/私有信息的显式解耦，且可解释性有限。
- **精确研究问题**：Can a deep generative model that disentangles shared/private latent spaces and incorporates TF–motif binding priors achieve more accurate and biologically interpretable cis- and trans-regulatory inference from single-cell multi-omics data than existing baselines?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引用与论述整理，属于「经外部核验」的领域发展框架，但具体分期表述为本文框架。

1. **单组学 GRN 推断阶段**：早期方法（GENIE3、PIDC 等）仅利用 scRNA-seq 表达数据推断 TF–TG 调控，受限于数据稀疏性和缺乏表观遗传信息，无法区分直接/间接调控。
2. **单细胞多组学技术成熟阶段**：10x Multiome、SHARE-seq 等技术实现同一细胞内 RNA 表达和染色质可及性的同时测量，为联合建模提供了数据基础。
3. **多组学整合方法阶段**：MultiVI、scGLUE、scButterfly 等方法通过 VAE 或对抗学习将多组学数据映射到共享潜空间，主要用于数据整合和细胞注释，但未针对 GRN 推断优化。
4. **知识引导的 GRN 推断阶段**：SCENIC+ 等工具开始利用 TF–motif 信息增强调控推断，但主要基于相关性或回归框架，缺乏深度生成模型的表征学习能力。
5. **本文位置**：scTFBridge 将「解耦表征学习」（disentangled representation learning）与「TF–motif 先验约束」结合，在深度生成模型框架内同时实现多组学整合、生物学可解释的潜空间学习，以及 cis/trans 调控推断，代表了「知识引导 + 深度生成模型」的融合方向。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 模态间隙（modality gap） | RNA-seq 和 ATAC-seq 数据分布差异大，直接拼接或简单对齐难以捕获跨模态调控信号 | 不同组学层测量生物学过程的不同方面，各自包含独特的私有信息，阻碍共享表征学习 | Results 引言段；"each modality retains unique private information that can impede the integration of a shared multi-omics latent space" |
| 共享/私有信息纠缠 | 传统 VAE 将多组学数据编码到单一潜空间，无法区分跨模态共享的调控信号与模态特异的噪声 | 缺乏显式的解耦机制，导致共享表征被私有信息污染 | Results 框架段；"disentangles latent variables of both RNA-seq and ATAC-seq data into modality-shared and modality-private subspaces" |
| 生物学可解释性不足 | 深度学习的潜变量维度缺乏明确生物学含义，难以直接映射到 TF 调控活性 | 潜空间学习仅由数据驱动，未引入 TF–motif 结合先验 | Results 框架段；"incorporating prior knowledge of TF-motif binding to regularize the biological learning of modality-shared embedding" |
| GRN 推断精度有限 | 现有方法在 cis/trans 调控推断上 AUC/AUPR 不高，尤其在远距离调控和稀疏数据场景 | 缺乏对 TF–RE–TG 调控链的显式建模，且未利用可解释性工具量化特征贡献 | Results 图 4；scTFBridge 在多个距离分组中 AUC/AUPR 均优于基线 |
| 数据稀疏性与 dropout | 单细胞数据高稀疏性导致重建和推断不稳定 | 单细胞测序技术本身的限制，需要模型具备鲁棒的重建能力 | Methods 数据预处理段；"binarized and filtered to retain peaks with open accessibility in at least 1% of all cells" |

---

## 06 核心思想

### 1) 表面方法

scTFBridge 是一个混合 VAE 架构：
- 分别编码 RNA-seq 和 ATAC-seq 到共享/私有潜空间；
- 用互信息最小化（CLUB 上界）解耦共享与私有表征；
- 用对比学习对齐跨模态共享表征；
- 用 TF–motif 结合分数矩阵约束 ATAC 解码器权重；
- 用 SHAP 计算 RE 和 TF 对 TG 的调控分数。

### 2) 核心洞察

**生物学先验可以作为网络架构约束**：TF–motif 结合分数矩阵 B 直接作为 ATAC 解码器权重的掩码（mask），使得从共享潜变量（对应 TF）到重建峰（对应 RE）的连接仅存在于已知有结合关系的 TF–RE 对上。这一设计将「TF 结合 DNA」的分子机制直接编码进网络结构，而非仅作为训练信号，从而保证潜变量具有明确的 TF 调控活性含义。

**解耦是跨模态调控推断的前提**：只有将共享的调控信号与模态特异的噪声分离，才能从共享潜空间中可靠地提取 TF 调控活性，避免私有信息（如批次效应、技术噪声）干扰调控推断。

### 3) 可能的普适教训 [Analysis]

- 在 AI for biology 中，**将分子机制（如结合亲和力、结构约束）转化为网络结构约束**，比仅作为损失函数项更有效，因为结构约束直接限制了假设空间。
- 解耦表征学习（disentanglement）不仅是一种表征学习技巧，更是**生物学问题本身的需求**——生物学过程中共享与特异的区分天然对应数学上的子空间分解。
- SHAP 等可解释性工具与生物学先验结合，可以将「黑箱」模型转化为可验证的调控假设生成器。

---

## 07 方法总览

- **输入**：
  - scRNA-seq 数据：TF 表达矩阵（128 个高表达 TF）和 TG 表达矩阵（top 3000 高变基因）
  - scATAC-seq 数据：峰（peak）可及性二值矩阵
  - TF–motif 结合分数矩阵 B（713 个 PWM，来自 JASPAR/TRANSFAC/UniPROBE，经 HOMER 扫描）
  - 批次标签 c（作为条件变量）
- **输出**：
  - 解耦的共享/私有潜空间表征
  - cis 调控分数（RE–TG）
  - trans 调控分数（TF–TG）
  - 细胞类型特异的 GRN
- **模块**：
  1. 编码器：RNA 编码器、ATAC 编码器（各自输出共享 + 私有潜变量）
  2. 共享潜空间对齐：对比学习损失
  3. 解耦模块：CLUB 互信息上界最小化
  4. 解码器：RNA 解码器（重建 TG 表达）、ATAC 解码器（重建峰可及性，权重受 B 矩阵约束）
  5. 可解释性模块：SHAP 计算调控分数
- **训练**：
  - 优化器：Adam，lr=1e-4，weight decay=1e-6
  - 150 epochs，early stopping（10 steps）
  - 5 折交叉验证（64% 训练 / 16% 测试 / 20% 验证）
  - 损失 = 重建损失（RNA + ATAC）+ KL 散度 + 互信息最小化项 + 对比学习项
- **流程**：
  1. 预处理：RNA 归一化、ATAC 二值化、TF 筛选、峰过滤
  2. 编码：RNA/ATAC 分别编码为共享 + 私有潜变量
  3. 对齐：对比学习对齐 RNA-shared 和 ATAC-shared
  4. 解耦：CLUB 最小化共享与私有之间的互信息
  5. 解码：RNA 解码器重建 TG；ATAC 解码器（B 掩码约束）重建峰
  6. 推断：SHAP 计算 RE→TG（cis）和 TF→TG（trans）调控分数
  7. 验证：eQTL、pcHi-C、ChIP-seq 作为 ground truth 评估

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 编码器（RNA/ATAC 双分支） | 将各模态数据映射到共享 + 私有潜空间 | 不同组学层需要独立特征提取，同时为共享表征提供跨模态对齐基础 | 输入：RNA 表达 / ATAC 峰矩阵；输出：共享潜变量 z_s、私有潜变量 z_p | Results 框架段；图 1b | 预期：无法分离模态特异信息，共享表征被私有噪声污染 [Analysis] |
| 共享潜空间对齐（对比学习） | 拉近 RNA-shared 与 ATAC-shared 表征 | 确保共享潜空间编码跨模态一致的调控信号 | 输入：z_sr, z_sa；输出：对齐损失 | Results 框架段；"contrastive learning loss was incorporated to align shared embeddings" | 预期：共享表征无法统一，跨模态推断失效 [Analysis] |
| 互信息最小化（CLUB） | 最小化共享与私有表征之间的互信息 | 实现真正的解耦，防止私有信息泄漏到共享空间 | 输入：z_s, z_p；输出：CLUB 损失 | Methods 框架段；公式 (10)-(17) | 预期：共享/私有纠缠，调控信号被稀释 [Analysis] |
| TF–motif 约束解码器 | 用 B 矩阵掩码 ATAC 解码器权重 | 将 TF–motif 结合先验直接编码进网络结构，保证潜变量对应 TF 调控活性 | 输入：z_sa, z_pa；输出：重建峰矩阵；权重 W 受 B 约束 | Results 框架段；图 1d；Methods 公式 (18) | 实测：本文核心创新，移除后模型退化为普通 VAE，可解释性大幅下降（作者未做消融，[Analysis] 预期） |
| SHAP 可解释性模块 | 计算 RE 和 TF 对 TG 的贡献分数 | 将模型内部计算转化为可验证的调控关系 | 输入：训练好的模型 + 数据；输出：cis/trans 调控分数 | Results 框架段；图 1f, g；Methods SHAP 段 | 预期：无法量化调控强度，GRN 推断退化为相关性分析 [Analysis] |
| 交叉模态生成 | 用 ATAC 共享潜变量 + 高斯采样私有变量生成 RNA | 实现缺失模态的数据重建，增强模型鲁棒性 | 输入：z_sa + z_p~N(0,1)；输出：重建 RNA | Methods 框架段；公式 (19)-(20) | 预期：模型无法处理模态缺失场景 [Analysis] |

---

## 09 关键公式符号

1. **VAE 证据下界（ELBO）**：
   \[
   \log p(x; \theta) \geq \mathbb{E}_{q(z|x;\phi)}[\log p(x|z;\theta)] - KL(q(z|x;\phi) \| p(z))
   \]
   - \( x \)：观测数据（RNA 或 ATAC）
   - \( z \)：潜变量
   - \( \theta, \phi \)：解码器/编码器参数
   - 用途：深度生成模型的基本优化目标
   - 来源：Methods 公式 (1)-(4)

2. **互信息 CLUB 上界**：
   \[
   I_{CLUB}(x, y) = \mathbb{E}_{p(x,y)}[\log q(y|x)] - \mathbb{E}_{p(x)p(y)}[\log q(y|x)]
   \]
   - 用途：估计并最小化共享与私有表征之间的互信息
   - 来源：Methods 公式 (12)-(17)

3. **TF–motif 约束解码器权重**：
   \[
   W_{ij} = B_{ij} \cdot \tilde{W}_{ij}
   \]
   - \( B_{ij} \)：TF \( i \) 与 RE \( j \) 的 motif 结合分数
   - \( \tilde{W}_{ij} \)：可学习权重
   - 用途：将生物学先验硬编码为网络结构约束
   - 来源：Methods 公式 (18)

4. **cis 调控分数**：
   \[
   \text{cis-score}_{i,j} = \rho_{i,j} \cdot O_j \cdot E_i \cdot f(d_{i,j})
   \]
   - \( \rho_{i,j} \)：SHAP 值（RE \( j \) 对 TG \( i \)）
   - \( O_j \)：RE \( j \) 的平均染色质可及性
   - \( E_i \)：TG \( i \) 的平均表达
   - \( d_{i,j} \)：RE 与 TG 的基因组距离，\( d_0 = 30,000 \) bp 为归一化因子
   - 来源：Methods SHAP 段

5. **trans 调控分数**：
   \[
   \text{trans-score}_{k,i} = \alpha_{k,i}
   \]
   - \( \alpha_{k,i} \)：TF 潜变量 \( k \) 对 TG \( i \) 的 SHAP 值
   - 来源：Methods SHAP 段

---

## 10 实验设计与证据链

### 数据集与设置

| 数据集 | 来源 | 规模 | 用途 |
|--------|------|------|------|
| BMMC | GSE194122 | 健康供体骨髓单核细胞，多批次 | 解耦表征学习评估（图 2a-c） |
| PBMC | 10x Genomics Multiome | 粒细胞分选 PBMC | cis/trans 调控推断基准测试（图 4） |
| 类风湿关节炎 | GSE243917 | 关节炎组织免疫细胞 | 疾病相关调控推断（图 3） |
| 肺组织 | GSE2414468 | 吸烟/非吸烟者正常肺组织 | 疾病易感性分析（图 6） |

### Ground truth 数据
- cis 调控：pcHi-C（三种血细胞类型）、eQTL（八种免疫细胞类型，scQTLbase）
- trans 调控：ChIP-seq（Cistrome 数据库，17 个 TF，四种血细胞类型）

### 指标
- AUC、AUPR Ratio（相对随机预测的提升倍数）、F1 Score

### 基线方法
- cis 调控：PCC、TSS 距离、随机预测、SCENIC+
- trans 调控：PCC、SCENIC+、GENIE3、PIDC

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 解耦表征学习（BMMC） | scTFBridge 能分离共享/私有信息 | 比较 RNA-private、ATAC-private、shared 嵌入的 UMAP 可视化 | 不同模态私有嵌入捕获不同细胞信息；共享嵌入整合跨模态信号 | 解耦机制有效，共享/私有信息分离 | 未提供定量指标（如互信息数值） | Results 图 2a；图 S1 |
| TG 表达重建（BMMC） | 共享嵌入 + ATAC 数据能准确重建 TG 表达 | 与基线方法比较重建精度 | scTFBridge 重建精度优于基线 | 跨模态信息有效整合 | 未提供具体数值 | Results 图 2b；图 S2 |
| cis 调控推断（PBMC） | scTFBridge 能准确推断 RE–TG 调控 | 与 PCC、距离、随机、SCENIC+ 比较，按距离分组（0-5kb 至 100-200kb） | 所有距离分组中 AUC/AUPR 最高 | 多组学整合优于单模态相关性方法 | 仅在血细胞类型中验证 | Results 图 4a-c |
| trans 调控推断（PBMC） | scTFBridge 能准确推断 TF–TG 调控 | 与 GENIE3、PIDC、PCC、SCENIC+ 比较 | AUC 0.776（基线 0.531-0.583），AUPR 2.654（基线 1.166-1.388） | 多组学 + TF-motif 先验显著提升 trans 推断 | 仅 17 个 TF 的 ChIP-seq 验证 | Results 图 5b-e |
| 细胞类型特异调控（RA） | scTFBridge 能捕获疾病相关调控 | 与动态/恒定峰比较，S-LDSC 富集分析 | 共享峰显著富集 RA 遗传力 | 共享调控信号与疾病相关 | 未做因果验证 | Results 图 3e-f |
| 肺腺癌易感性（肺组织） | scTFBridge 能识别癌症易感基因 | 比较吸烟/非吸烟组调控分数 | 识别出细胞类型特异的易感基因和调控程序 | 方法可迁移到疾病场景 | 未做功能实验验证 | Results 图 6 |

---

## 11 结论正确解读

- **任务范围**：本文方法适用于**配对的单细胞多组学数据**（同一细胞的 RNA + ATAC），不适用于非配对数据或仅单组学数据。
- **Oracle/真值输入**：TF–motif 结合分数矩阵 B 来自外部数据库（JASPAR/TRANSFEC/UniPROBE），是预先计算的先验知识，而非从数据中学习。这意味着方法的性能部分依赖于 motif 数据库的覆盖度和质量。
- **端到端状态**：模型端到端训练，但 GRN 推断依赖训练后的 SHAP 分析，属于两阶段流程。
- **算力成本**：使用 8×RTX 4090 GPU，但未报告具体训练时间；模型为浅层 VAE，推测算力需求中等。
- **历史数据依赖**：依赖已发表的 ChIP-seq、eQTL、pcHi-C 数据作为 ground truth，这些数据本身存在组织/细胞类型覆盖偏差。
- **最难场景**：远距离 cis 调控（100-200kb）和稀疏细胞类型中表现可能下降（作者未明确报告，[Analysis] 推断）。
- **群体/领域边界**：验证集中在血液细胞（BMMC、PBMC、RA 免疫细胞）和肺组织；其他组织/物种的泛化性未验证。
- **不确定性**：SHAP 分数反映的是模型内部的贡献分配，不等同于因果调控效应；未提供置信区间或统计显著性检验。

**有边界的复述**：scTFBridge 在配对单细胞 RNA+ATAC 数据上，通过 TF-motif 先验约束的解耦 VAE，能够以优于现有基线（PCC、距离、随机、SCENIC+、GENIE3、PIDC）的精度推断 cis 和 trans 调控关系，并在 RA 和肺癌数据中识别出细胞类型特异的疾病相关调控程序；但该结论局限于血液和肺组织、依赖外部 motif 数据库质量、且未经过功能实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 基准测试局限于血液来源数据 | 主要验证在 BMMC、PBMC、RA 免疫细胞 | 未明确说明 | Discussion 段；"benchmarking analysis was primarily conducted on blood-derived datasets" |
| 简化 TF–RE 结合模型 | 仅考虑 TF–motif 结合，未纳入更复杂的调控机制（如竞争性结合、协同作用、染色质三维结构） | 需探索更复杂的 TF 调控机制 | Discussion 段；"concentrated on a simplified model of TF and RE binding" |
| 未考虑非编码 RNA 调控 | 模型未纳入 microRNA、lncRNA 等非编码调控因子 | 需开发互补方法 | Discussion 段；"does not account for potential regulatory mechanisms involving microRNAs, non-coding RNAs" |
| 未利用私有峰信息 | 私有 ATAC 峰（非共享调控信号）未纳入 GRN 推断 | 需进一步探索私有峰的功能 | Discussion 段；"private Peaks... require further exploration" |
| 泛化性受限 | 因 ground truth 数据（eQTL、ChIP-seq、pcHi-C）主要来自血液，其他组织的泛化性未验证 | 未明确说明 | Discussion 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| TF-motif 结合分数矩阵 B 作为硬掩码可能过于严格 | 已知的 TF–motif 结合数据不完整，硬掩码可能排除未知但真实的 TF–RE 相互作用；软约束（如加权正则化）可能更鲁棒 | 影响 GRN 推断的召回率，尤其对新发现的调控关系 | 对比硬掩码 vs. 软权重 vs. 无先验的消融实验 | Methods 公式 (18)；[Analysis] 基于 motif 数据库覆盖度有限的常识 |
| 未报告消融实验 | 无法判断各模块（CLUB、对比学习、TF-motif 约束）的独立贡献 | 核心创新声称（解耦 + 先验约束）缺乏定量验证 | 逐一移除各模块并比较 AUC/AUPR | 全文未提供消融分析 |
| SHAP 分数作为调控强度的有效性未验证 | SHAP 反映的是模型内部的贡献分配，与真实调控强度（如 ChIP-seq 结合峰度、报告基因实验）的对应关系未知 | 若 SHAP 分数与生物学强度不一致，则 GRN 推断的定量解读不可靠 | 将 SHAP 分数与 ChIP-seq 信号强度、eQTL effect size 做相关性分析 | Methods SHAP 段；[Analysis] |
| 与基线方法比较的公平性 | SCENIC+ 等基线方法可能未在同一数据预处理/交叉验证协议下运行 | 影响结论「优于基线」的可信度 | 检查是否使用相同的数据划分、超参数调优预算 | Results 图 4-5；未提供详细比较协议 |
| 未报告不确定性量化 | 单次运行结果，无多次重复的标准差或置信区间 | 模型初始化和数据划分的随机性可能影响结论稳定性 | 多次重复实验并报告均值±标准差 | 全文未提及重复实验 |
| 细胞类型特异的 TF 活性与已知生物学的一致性 | 仅展示了与已知调控关系一致的例子，未系统评估 | 选择性展示可能高估方法性能 | 对所有细胞类型的所有 TF 进行系统富集分析 | Results 图 2d-e；[Analysis] |
| 与纯数据驱动方法（无先验）的对比缺失 | 未比较不使用 TF-motif 先验的相同架构 | 无法区分「先验知识」与「架构设计」各自的贡献 | 训练无 B 矩阵约束的相同 VAE 作为对照 | 全文未提供此对照 |

---

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题方向。

### 概念层面

1. **生物学先验的「结构编码」优于「损失编码」**：将 TF–motif 结合分数作为网络权重的掩码（而非仅作为训练信号），直接限制了假设空间，使潜变量具有明确的生物学含义。这一思想可迁移到其他分子互作建模——例如将蛋白质结构域-基序相互作用作为注意力掩码。

2. **解耦表征是「共享机制 vs 特异调控」的数学对应**：多组学/多条件数据中，共享潜空间捕获跨模态/跨条件的通用调控规则，私有空间捕获模态/条件特异因素。这一框架可迁移到 TF–DNA 结合的特异性与可塑性研究——例如区分序列编码的通用结合偏好与细胞类型特异的染色质环境效应。

3. **可解释性工具（SHAP）与生物学先验结合生成可验证假设**：SHAP 分数在生物学约束的模型上计算，输出的调控关系可直接用外部数据（eQTL、ChIP-seq）验证，形成「模型生成假设 → 实验验证 → 模型修正」的闭环。

### 方法层面

4. **互信息最小化（CLUB 上界）是解耦的实用工具**：CLUB 提供了互信息的可计算上界，可用于高维潜空间的解耦。在 TF–DNA 结合建模中，可用于分离「序列特征」与「染色质环境特征」对结合的影响。

5. **交叉模态生成作为正则化**：用 ATAC 生成 RNA（或反之）迫使共享潜空间编码跨模态一致的调控信号。在物理模拟中，可类比为「用结构预测约束序列模型」或「用结合能预测约束构象采样」。

6. **TF–motif 结合分数矩阵作为「可微的先验层」**：B 矩阵既不是硬编码规则也不是纯数据驱动，而是可微的权重掩码，允许梯度通过先验知识传播。这为将分子对接分数、MD 模拟结合自由能等物理量嵌入深度学习模型提供了范式。

### 实验设计层面

7. **分层基准测试策略**：按基因组距离分层（0-5kb 至 100-200kb）评估 cis 调控推断，可揭示方法在不同调控范围的优势与局限。类似地，TF–DNA 结合预测可按结合 motif 类型、结合亲和力范围分层评估。

8. **多源 ground truth 交叉验证**：同时使用 eQTL（遗传证据）、pcHi-C（三维结构证据）、ChIP-seq（直接结合证据）验证模型输出，增强结论的鲁棒性。这一策略可迁移到 TF–DNA 结合预测的验证中。

---

## 15 与已有知识连接

- **VAE 家族**：本文架构基于条件 VAE 和 multi-modal VAE（如 MVAE、MMVAE），与 scVI、scArches 等单细胞 VAE 方法同源。区别在于本文引入显式解耦和生物学先验约束。
- **解耦表征学习**：与 β-VAE、FactorVAE、InfoGAN 等解耦方法相关，但本文的互信息最小化（CLUB）是更直接的目标函数。
- **GRN 推断方法谱系**：与 SCENIC/SCENIC+（regulon 分析）、GENIE3（随机森林）、PIDC（互信息）、DeepSEM（结构化变分自编码器）等一脉相承。本文的差异化在于多组学解耦 + 先验约束 + SHAP 可解释性。
- **TF–motif 数据库**：JASPAR、TRANSFAC、UniPROBE 是 TF–DNA 结合先验的标准来源，本文的 B 矩阵构建方式可复用于其他 TF–DNA 结合预测任务。
- **可解释性方法**：SHAP 在单细胞分析中已有应用（如 PAUSE），本文将其扩展到 GRN 推断场景。
- **与物理模拟的关联 [Analysis]**：本文的「先验约束解码器」思想可类比为物理模拟中的「约束满足」——将已知的分子间相互作用（如氢键、疏水接触）作为模拟的硬约束。未来可将 MD 模拟的结合自由能或对接分数作为 B 矩阵的替代或补充，实现「AI + 物理」的深度融合。
- **与 AlphaFold 等结构预测方法的关联 [Analysis]**：AlphaFold 利用共进化信息预测结构，本文利用 motif 结合信息约束潜空间，两者共享「利用生物学先验缩小假设空间」的核心思想。

---

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题方向。

### 候选 1：scTFBridge-Phys——将物理结合自由能嵌入解耦生成模型

- **名称**：Physics-Informed Disentangled VAE for TF-DNA Binding Prediction
- **来源局限/观察**：scTFBridge 使用 motif 结合分数作为先验，但 motif 分数仅反映序列偏好，未纳入三维结构、构象变化、溶剂效应等物理化学因素。
- **核心假设**：将 MD 模拟或分子对接计算的结合自由能（ΔG）作为额外的先验约束，可以提升 TF–DNA 结合预测的准确性和泛化性，尤其在 motif 数据库覆盖不足的 TF 家族中。
- **初步方法**：对已知 TF–DNA 复合物结构进行 MD 模拟或对接计算，获得每个 TF–motif 对的 ΔG 估计；将 ΔG 与 motif 分数共同编码为 B 矩阵的扩展；在 scTFBridge 框架中增加物理先验项。
- **验证方式**：在多个细胞类型的多组学数据上比较「仅 motif 先验」vs.「motif + 物理先验」的 cis/trans 推断 AUC/AUPR；对预测的新调控关系用 ChIP-seq 或报告基因实验验证。
- **创新状态**：unverified

### 候选 2：TF 结合特异性的解耦表征——分离序列编码与染色质环境效应

- **名称**：Disentangling Sequence-Encoded vs. Chromatin-Context TF Binding Specificity
- **来源局限/观察**：scTFBridge 的共享潜空间整合了 RNA 和 ATAC 信息，但未显式区分「TF 的序列偏好」与「染色质可及性/修饰对结合的调控」这两个不同层面的机制。
- **核心假设**：通过额外的解耦约束，可以将 TF 结合表征分解为「内在序列偏好」和「环境依赖性」两个子空间，从而预测同一 TF 在不同细胞类型中的结合行为差异。
- **初步方法**：在 scTFBridge 的共享潜空间中增加子空间分解层，一个子空间仅由序列特征驱动，另一个由染色质特征驱动；用互信息最小化确保两个子空间独立；比较两个子空间对 cis/trans 调控的贡献。
- **验证方式**：在不同细胞类型中比较同一 TF 的「序列子空间」表征是否一致（应一致），「环境子空间」表征是否反映染色质状态差异；用已知的细胞类型特异性 TF 结合数据验证。
- **创新状态**：unverified

### 候选 3：从静态结合到动态调控——用潜空间动力学建模 TF 结合的时间演化

- **名称**：Latent Dynamics of TF-DNA Binding Across Cellular States
- **来源局限/观察**：scTFBridge 是静态模型，无法捕捉 TF 结合随时间或细胞状态转变的动态变化。
- **核心假设**：在解耦潜空间上学习一个动力学模型（如神经 ODE），可以预测 TF 结合活性在细胞分化或刺激响应过程中的演化轨迹。
- **初步方法**：使用时序单细胞多组学数据（如分化时间序列），训练 scTFBridge 获得每个时间点的潜表征；在共享潜空间上拟合神经 ODE 或状态空间模型；用学习到的动力学预测未来时间点的调控状态。
- **验证方式**：在已知分化轨迹的数据集上，比较动力学模型预测的 TF 活性与实测数据的吻合度；检验预测的调控转变是否与已知的细胞命运决定事件对齐。
- **创新状态**：unverified

### 候选 4：跨物种 TF–DNA 结合预测——利用解耦表征迁移

- **名称**：Cross-Species Transfer of TF-DNA Binding Rules via Disentangled Representations
- **来源局限/观察**：scTFBridge 在人类数据上验证，但 TF–DNA 结合机制在物种间保守性如何，以及如何迁移到非模式生物，尚未探索。
- **核心假设**：共享潜空间中「序列编码的 TF 结合规则」在物种间保守，而「环境依赖性」部分物种特异；通过固定共享子空间、微调私有子空间，可以实现跨物种迁移。
- **初步方法**：在人类多组学数据上预训练 scTFBridge；对目标物种（如小鼠、斑马鱼），固定共享编码器，仅微调私有编码器和解码器；评估迁移后的 cis/trans 推断性能。
- **验证方式**：使用小鼠等物种的配对多组学数据，比较「从头训练」vs.「迁移学习」的性能差异；检验迁移后共享子空间是否仍对应保守的 TF 结合规则。
- **创新状态**：unverified

### 候选 5：不确定性量化的 GRN 推断——贝叶斯 scTFBridge

- **名称**：Bayesian scTFBridge with Uncertainty-Aware Regulatory Inference
- **来源局限/观察**：scTFBridge 的 SHAP 分数是点估计，无法反映调控关系的不确定性；在稀疏细胞类型或低质量数据中，这可能导致虚假的调控推断。
- **核心假设**：通过变分 dropout 或深度集成，可以为 SHAP 分数提供不确定性区间，从而区分「可靠的调控关系」与「噪声驱动的虚假关联」。
- **初步方法**：在 scTFBridge 中引入 MC-dropout 或深度集成；对每个 RE–TG 和 TF–TG 关系计算 SHAP 分数的均值和方差；将不确定性作为调控关系的置信度指标。
- **验证方式**：在已知调控关系的数据集上，比较「不确定性过滤前/后」的精确率；检验低置信度调控关系是否富集在已知的假阳性区域。
- **创新状态**：unverified

### 候选 6：结合 motif 扫描与结构预测的混合先验

- **名称**：Hybrid Motif-Structure Priors for TF-DNA Binding Prediction
- **来源局限/观察**：scTFBridge 的 B 矩阵仅覆盖已知 motif 的 TF，对 motif 未知或结合非经典 motif 的 TF（如先锋因子）效果有限。
- **核心假设**：将 AlphaFold 等结构预测工具输出的 TF–DNA 复合物结构特征与 motif 扫描结合，可以构建更全面的先验矩阵，覆盖 motif 数据库之外的 TF–RE 相互作用。
- **初步方法**：对目标 TF 使用 AlphaFold 预测其 DNA 结合域结构，与 DNA 片段进行对接模拟；将结构预测的结合亲和力与 motif 分数融合为 B 矩阵；在 scTFBridge 中比较「motif-only」vs.「motif+structure」先验的性能。
- **验证方式**：在包含非经典 motif TF 的数据集上比较推断精度；用实验数据（如 SELEX、HT-SELEX）验证新预测的 TF–RE 关系。
- **创新状态**：unverified