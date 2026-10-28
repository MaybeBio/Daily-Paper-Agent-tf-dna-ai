## 01 基本信息
- **标题**：Machine learning identifies activation of RUNX/AP-1 as drivers of mesenchymal and fibrotic regulatory programs in gastric cancer
- **作者与单位**：Razavi-Mohseni, Milad; Huang, Weitai; Guo, Yu A; Shigaki, Dustin; Shigaki, Dustin; Tan, Patrick; Skanderup, Anders J; Beer, Michael A（单位未在摘要中提供）
- **期刊/预印本平台**：Genome Research
- **年份**：2024-05-23
- **论文类型**：研究论文（Research Article）
- **领域**：癌症基因组学；表观基因组学；转录调控；机器学习
- **关键词**：gastric cancer; ATAC-seq; machine learning; transcription factors; EMT; mesenchymal; RUNX; AP-1
- **DOI/arXiv 号**：10.1101/gr.278565.123
- **代码**：http://beerlab.org/gccl（含 gkm-SVM 模型与补充代码）
- **数据**：GEO 登录号 GSE264550、GSE266159（另有 GSE157750、GSE85465、GSE62254、GSE150290 等外部数据）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作（TF–DNA 结合机制）× 机器学习」方向，核心方法为 gkm-SVM（基于 gapped k-mer 的序列模型）从 ATAC-seq 数据推断 TF 活性，识别驱动胃癌间质/纤维化表观调控程序的转录因子（RUNX、AP-1 等），并验证其与增强子开放、靶基因表达及拷贝数变异的关系。对 TF–DNA 结合机制研究提供了「从开放染色质序列推断 TF 活性」的可迁移框架。

## 02 一句话总结
本文用 gkm-SVM 对 25 株胃癌细胞系及 TCGA 原发肿瘤的 ATAC-seq 数据建模，识别出 RUNX2、AP-1（FOS/JUN）、ZEB1、SNAI2 等转录因子驱动间质样（Mes-like）调控程序，并通过增强子开放、RNA-seq、拷贝数及单细胞数据验证，表明 RUNX/AP-1 激活是胃癌间质/纤维化表观调控程序的关键驱动因素。

## 03 研究问题
- **具体问题**：胃癌中驱动间质样（Mes-like）与上皮样（Epi-like）表观调控状态差异的关键转录因子（TF）是哪些？这些 TF 如何通过染色质可及性变化驱动下游基因表达？
- **为什么重要**：胃癌是全球第五大常见癌症，间质表型更具侵袭性。理解调控这一表型转换的 TF 网络，有助于揭示胃癌异质性和进展机制，并可能提供预后标志物或治疗靶点。
- **现有方法不足**：此前研究多关注 EMT 的基因表达变化，但缺乏对调控层面（染色质可及性、TF 结合）的系统性解析；且传统差异可及性分析难以直接推断驱动性 TF。
- **精确研究问题（Can...?）**：Can a sequence-based machine learning model (gkm-SVM) trained on ATAC-seq data identify the transcription factors that drive the mesenchymal versus epithelial regulatory programs in gastric cancer?

## 04 背景与发展脉络
（标注：以下脉络为「经外部核验」的领域常识，结合本文框架整理）
- **阶段一：差异表达分析**（约 2000s-2010s）：通过 RNA-seq 比较上皮/间质状态，识别 EMT 相关基因（如 ZEB1、SNAI2、VIM），但无法区分驱动因子与下游效应。
- **阶段二：染色质可及性分析**（约 2010s 中期）：ATAC-seq/DNase-seq 揭示开放染色质区域，但差异可及性峰本身不直接指示结合 TF。
- **阶段三：序列模型推断 TF 活性**（约 2010s 后期至今）：gkm-SVM（Ghandi et al. 2014; Lee et al. 2015; Beer et al. 2020）等序列模型从开放染色质序列中学习 TF 结合 motif 的贡献权重，实现「从序列到 TF 活性」的推断。本文属于此阶段，并进一步结合 RNA-seq、CNV、单细胞数据验证。
- **本文主张的位置**：在胃癌中首次系统性地用 gkm-SVM 绘制 TF 活性图谱，识别 RUNX/AP-1 为间质/纤维化程序的核心驱动因子，并建立「TF 活性 → 增强子开放 → 靶基因表达 → 拷贝数变异」的因果链条。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 差异可及性峰无法直接指示驱动性 TF | ATAC-seq 差异峰众多，但不知道哪些 TF 结合并驱动状态变化 | 开放染色质区域包含大量 TF 结合位点，需序列模型推断 TF 贡献 | Results 图 1C；Methods "gkm-SVM training" 节 |
| 小样本下深度学习模型过拟合 | 差异可及性峰约 2000 个，DNN 训练不稳定 | gkm-SVM 在较小数据集上表现稳健，且可解释性强 | Results 首段；Methods 节 |
| 细胞系与肿瘤组织的调控状态差异 | 细胞系可能不反映原发肿瘤的异质性 | 需在 TCGA-STAD 原发肿瘤 ATAC-seq 中验证 | Results 图 1C；Supplemental Figs. S4, S5 |
| 间质样细胞系与成纤维细胞的区分 | Mes-like 细胞系表达谱类似成纤维细胞，可能被误判 | 通过突变负荷、CN 负荷及差异 motif 分析区分 | Results 图 7A-G；Methods "CN and mutation analyses" 节 |
| 增强子-基因连接的因果性 | 差异可及性峰与差异表达基因的对应关系不明确 | 通过峰-基因距离（50 kb 内）及 LE 模型预测的 CTCF 环验证 | Results 图 6A-E；Methods "ATAC-seq analysis around DE genes" 节 |

## 06 核心思想
1. **表面方法**：对 25 株胃癌细胞系的 ATAC-seq 数据，训练 gkm-SVM 序列模型（以 top 10,000 远端峰为正集，随机基因组序列为负集），通过 gkm-PWM 将 gapped k-mer 权重映射为 TF motif 活性分数，聚类识别调控程序。
2. **核心洞察**：胃癌细胞系的表观调控差异主要由少数 TF（RUNX、AP-1、ZEB、GATA、KLF、GRHL 等）的活性差异驱动，而非大量 TF 的随机变化。Mes-like 状态由 RUNX/AP-1 激活驱动，伴随 ZEB 抑制活性；Epi-like 状态由 GATA/KLF/GRHL 维持。
3. **可能的普适教训**（[Analysis]）：从开放染色质序列推断 TF 活性时，gkm-SVM 的「小样本稳健性 + 可解释性」组合优于黑箱 DNN；且将 TF 活性与下游表达、拷贝数变异、单细胞数据交叉验证，可构建「驱动因子 → 调控程序 → 表型」的因果链，这一框架可迁移至其他癌症类型或细胞状态转换研究。

## 07 方法总览
- **输入**：25 株胃癌细胞系 ATAC-seq 数据（Ho et al. 2023）；TCGA-STAD 原发肿瘤 ATAC-seq；ENCODE 正常胃/成纤维细胞 DNase-seq；RNA-seq（细胞系、TCGA-STAD、GTEx）；scRNA-seq（Kim et al. 2022）；WGS（细胞系 CNV）。
- **输出**：TF 活性图谱（gkm-PWM 分数）、细胞系分组（Epi-like/Intermediate/Mes-like）、差异表达基因、增强子-基因连接、CNV 关联、预后分层。
- **模块**：
  1. ATAC-seq 处理（MACS2 峰 calling，远端峰定义）
  2. gkm-SVM 训练（每细胞系 vs 随机序列；成对比较）
  3. gkm-PWM motif 活性推断
  4. 聚类与 PCA（基于 motif 活性）
  5. RNA-seq 差异表达与 GSEA
  6. 峰-基因关联（50 kb 内）
  7. CNV 与突变分析
  8. 单细胞相关性分析
  9. 生存分析（ACRG、TCGA-STAD）
- **训练**：gkm-SVM 默认参数，五折交叉验证，中位 AUROC = 0.925（细胞系 vs 随机）；成对比较中位 AUROC = 0.922。
- **反馈回路**：gkm-SVM 预测的 TF 活性 → 差异表达基因 → 峰-基因关联 → 实验验证（ChIP-seq 数据）→ 支持 TF 驱动结论。
- **假设**：开放染色质序列的 gapped k-mer 组成足以反映 TF 结合活性；远端峰（>2 kb 从 TSS）主要代表增强子调控。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| gkm-SVM 序列模型 | 从开放染色质序列学习 TF 结合 motif 贡献 | 将 ATAC-seq 峰转化为可解释的 TF 活性分数 | 输入：峰序列 + 随机负集；输出：gapped k-mer 权重向量 | 中位 AUROC 0.925；聚类与 PCA 分组一致（图 1A,B） | 预期：无法识别驱动性 TF，仅剩差异峰列表（[Analysis] 预期效应） |
| gkm-PWM motif 推断 | 将 k-mer 权重映射为 TF motif 活性 | 将抽象权重转化为生物学可解释的 TF 活性 | 输入：k-mer 权重；输出：TF motif 活性分数 | 图 1C-E；Supplemental Fig. S3 | 预期：TF 活性不可解释，无法命名驱动因子（[Analysis] 预期效应） |
| 成对细胞系比较 | 识别细胞系间差异活性 TF | 捕捉异质性，而非仅平均信号 | 输入：300 对细胞系；输出：差异 motif 活性 | 图 1D,E | 预期：丢失细胞系特异性调控信息（[Analysis] 预期效应） |
| 峰-基因关联（50 kb） | 连接增强子开放与基因表达 | 建立 TF 活性 → 表达的直接证据 | 输入：差异峰 + DE 基因；输出：关联对 | 图 6A,B；Supplemental Figs. S21-23 | 预期：无法区分直接与间接调控（[Analysis] 预期效应） |
| CNV 分析 | 识别拷贝数变异与 TF 活性的关联 | 提供遗传学驱动证据 | 输入：WGS/TCGA CNV；输出：GATA4 缺失、MAPK9 扩增 | 图 3B-E | 预期：失去遗传学因果支持（[Analysis] 预期效应） |
| 单细胞相关性 | 验证细胞系状态与体内细胞类型对应 | 确认细胞系模型反映原发肿瘤异质性 | 输入：scRNA-seq 聚类；输出：细胞类型相关性 | 图 5A-E | 预期：无法确认细胞系-体内一致性（[Analysis] 预期效应） |

## 09 关键公式符号
- **gkm-SVM 核函数**（Ghandi et al. 2014）：K(x, y) = Σ_{k-mers} w_k · I(k ∈ x) · I(k ∈ y)，其中 w_k 为 gapped k-mer k 的权重，x, y 为序列。用途：计算序列间相似性，训练分类器。直觉：序列共享的 gapped k-mer 越多，越可能属于同一类（开放 vs 随机）。
- **gkm-PWM 推断**（Beer et al. 2020）：将 gapped k-mer 权重 w_k 线性映射为 motif m 的活性分数：S_m = Σ_{k} w_k · f_{m,k}，其中 f_{m,k} 为 motif m 与 k-mer k 的匹配度。用途：将 k-mer 权重转化为 TF motif 活性。直觉：motif 在开放峰中越富集，其活性分数越高。
- **AUROC**（五折交叉验证）：衡量模型区分开放峰与随机序列的能力。中位值 0.925（细胞系 vs 随机）、0.922（成对比较）。
- **Pearson 相关系数**：用于细胞系与 GTEx/ENCODE 组织表达谱相关性（图 4A-D）。
- **Mann-Whitney U 检验**：用于 DE 基因、CNV 差异显著性检验（图 6C）。

## 10 实验设计与证据链
- **数据集**：
  - 25 株胃癌细胞系 ATAC-seq（Ho et al. 2023）
  - TCGA-STAD 原发肿瘤 ATAC-seq（10 个样本，>10,000 远端峰，AUROC > 0.9）
  - ENCODE 正常胃 DNase-seq（ENCSR782SSS）及成纤维细胞 DNase-seq（30 个样本）
  - RNA-seq：细胞系、TCGA-STAD（322 肿瘤 + 17 正常）、GTEx（54 组织）
  - scRNA-seq：24 例胃癌患者（GSE150290）
  - ChIP-seq：RUNX2、JUN（LPS141，Bevill et al. 2023）；KLF5（AGS，Liu et al. 2020）；GATA4/GATA6（AGS，Chia et al. 2015）
- **指标**：AUROC（模型性能）、Pearson r（表达相关性）、log2FC 与 FDR（差异表达）、超几何检验 FDR（GSEA）、生存分析 P 值。
- **基线**：随机基因组序列（gkm-SVM 负集）；正常胃组织（TCGA-Normal、ENCODE 胃）作为上皮状态参照。
- **评测协议**：五折交叉验证；成对细胞系比较（300 对）；与 ChIP-seq 结合位点重叠验证。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| gkm-SVM 训练（每细胞系 vs 随机） | 开放染色质序列可被序列模型区分 | 25 细胞系，top 10,000 远端峰 vs 随机 | 中位 AUROC 0.925 | 开放峰具有可学习的序列特征 | 未直接证明 TF 因果性 | Results 首段；Supplemental Fig. S24 |
| 成对细胞系比较（300 对） | 细胞系间差异由特定 TF 驱动 | 每对取 2000 差异峰 | 中位 AUROC 0.922；RUNX/AP-1 为最强信号 | RUNX/AP-1 驱动 Mes-like 状态 | 未排除其他 TF 的贡献 | Results 图 1D,E；Supplemental Fig. S27 |
| TCGA-STAD 验证 | 细胞系发现的 TF 在原发肿瘤中激活 | 10 个 STAD 样本 vs 正常胃 | 70% 检测到 RUNX，70% 检测到 AP-1 | 细胞系模型反映原发肿瘤 | 样本量小，需更大队列 | Results 图 1C；Supplemental Fig. S5 |
| ChIP-seq 验证 | gkm-SVM 预测的 TF 确实结合增强子 | LPS141 RUNX2/JUN ChIP-seq | 强结合信号 | 预测的 TF 结合具有实验支持 | 仅一个细胞系验证 | Results 图 1F；Supplemental Fig. S6 |
| 峰-基因关联 | 增强子开放与靶基因表达相关 | 50 kb 内峰活性 vs DE 基因 | 1.73 倍（Epi）和 1.60 倍（Mes）富集 | 开放峰与表达直接相关 | 相关性不等于因果性 | Results 图 6A,B |
| CNV 分析 | 拷贝数变异驱动 TF 失调 | GATA4 缺失、MAPK9 扩增 | 与 Mes-like 状态显著关联 | CNV 是潜在驱动机制 | 未做功能实验验证 | Results 图 3B-E |
| 单细胞相关性 | Mes-like 细胞系类似成纤维细胞 | 24 例患者 scRNA-seq | 高相关性 | 细胞系状态在体内存在 | 未做谱系追踪 | Results 图 5A-E |
| 生存分析 | TF 表达有预后价值 | ACRG（300 例）、TCGA-STAD（315 例） | 显著分层 | 具有临床相关性 | 未做多变量校正 | Results 图 2G；Supplemental Fig. S11 |

## 11 结论正确解读
- **任务范围**：本文仅针对胃癌细胞系及 TCGA 原发肿瘤的 ATAC-seq/RNA-seq 数据，推断 TF 活性并关联表型。未涉及 TF 结合的直接生化验证（如 EMSA、SELEX）或三维结构。
- **oracle/真值输入**：gkm-SVM 训练使用开放染色质峰（ATAC-seq 定义）作为正集，随机基因组序列作为负集；TF 活性推断依赖已知 motif 数据库（gkm-PWM）。
- **端到端状态**：非端到端。流程为「ATAC-seq → gkm-SVM → gkm-PWM → TF 活性 → 聚类/关联」，各步骤独立，未联合优化。
- **算力成本**：未提供具体算力信息。gkm-SVM 在数千序列规模上训练，计算成本远低于 DNN。
- **历史数据依赖**：依赖已发表的 ATAC-seq、RNA-seq、ChIP-seq 数据（Ho et al. 2023; Bevill et al. 2023; Chia et al. 2015; Liu et al. 2020），未生成新实验数据。
- **模型依赖**：结果依赖 gkm-SVM 的 gapped k-mer 表示和 gkm-PWM 的 motif 推断方法；不同序列模型（如 DNN）可能给出不同 TF 排名。
- **最难情形**：间质样细胞系与成纤维细胞的区分（图 7）；低质量 ATAC-seq 样本（<10,000 峰）被排除。
- **群体/领域边界**：结论限于胃癌细胞系和 TCGA-STAD 队列，未在独立胃癌队列或体内模型验证。
- **不确定性**：TF 活性推断为计算预测，未直接测量 TF 结合；CNV 关联为相关性，未做功能实验。
- **有边界的复述**：在 25 株胃癌细胞系和 TCGA-STAD 样本中，gkm-SVM 推断的 RUNX/AP-1 活性与间质/纤维化基因表达程序显著相关，且该程序在单细胞水平与成纤维细胞状态对应，但 TF 的因果驱动作用仍需功能实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 细胞系模型的代表性 | 细胞系可能不完全反映原发肿瘤的异质性 | 在 TCGA-STAD 原发肿瘤中验证（已部分完成） | Discussion 首段 |
| 样本量有限 | 仅 25 株细胞系、10 个高质量 STAD ATAC-seq 样本 | 需更大队列验证 | Results 图 1C；Supplemental Fig. S5 |
| 计算预测未直接验证 | TF 活性为推断，未直接测量 TF 结合 | 需 ChIP-seq 或功能实验验证 | Discussion 末段 |
| 相关性不等于因果性 | CNV 与 TF 失调的关联未做功能实验 | 需 CRISPR 或过表达实验 | Results 图 3B-E |
| 单细胞数据为公开数据 | 未生成新的单细胞数据，依赖 Kim et al. (2022) | 需独立单细胞队列验证 | Methods "scRNA-seq data processing" 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| gkm-SVM 的 TF 活性推断依赖已知 motif 数据库 | 未知 motif 或非经典结合位点可能被遗漏 | 可能低估新型 TF 的贡献 | 使用 de novo motif 发现方法交叉验证 | Methods "gkm-PWM" 节 |
| 细胞系分组基于 ATAC-seq 聚类，可能存在循环论证 | 分组与 TF 活性推断使用同一数据 | 可能高估 TF 与分组的关联 | 使用独立数据（如 RNA-seq）验证分组 | Results 图 1A, 2A |
| 50 kb 峰-基因关联可能包含大量非功能性增强子 | 距离近不等于功能相关 | 可能高估增强子-基因连接 | 使用 Hi-C 或 CRISPR 干扰验证 | Results 图 6A,B |
| TCGA-STAD ATAC-seq 样本量小（10 个） | 统计功效有限 | 可能无法代表 STAD 异质性 | 扩大样本量或使用独立队列 | Results 图 1C；Supplemental Fig. S5 |
| 未比较其他序列模型（如 DNN） | gkm-SVM 可能不是最优模型 | 无法评估方法选择的合理性 | 在相同数据上比较多种模型 | Methods "gkm-SVM training" 节 |
| 生存分析基于 TF 表达而非活性 | 表达与活性可能不一致 | 可能混淆预后关联 | 使用 TF 活性评分进行生存分析 | Results 图 2G |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **gkm-SVM 作为小样本 TF 活性推断工具**：在差异峰数量有限（~2000）时，gkm-SVM 比 DNN 更稳健且可解释。可迁移至其他癌症类型或细胞状态转换研究，用于从 ATAC-seq 数据快速推断驱动性 TF。
2. **「TF 活性 → 增强子开放 → 靶基因表达」的验证框架**：将序列模型预测的 TF 活性与 RNA-seq 差异表达、峰-基因距离关联、ChIP-seq 结合位点交叉验证，构建因果链。此框架可迁移至 TF–DNA 互作研究，用于区分驱动因子与下游效应。
3. **成对比较策略**：对细胞系两两比较（300 对）而非仅平均信号，可捕捉异质性并识别状态特异的 TF 活性变化。可迁移至单细胞 ATAC-seq 分析，用于识别细胞状态转换的驱动 TF。
4. **拷贝数变异与 TF 活性关联**：将 CNV 与 TF 活性变化关联，可识别遗传学驱动事件。可迁移至其他癌症类型，用于发现 TF 失调的基因组机制。
5. **与单细胞数据交叉验证**：将 bulk 细胞系状态与 scRNA-seq 细胞类型对应，可确认细胞系模型反映体内异质性。可迁移至 TF–DNA 互作研究，用于验证体外模型的生理相关性。

## 15 与已有知识连接
- **gkm-SVM 方法**：源自 Ghandi et al. (2014) 和 Lee et al. (2015) 的 gapped k-mer SVM 方法，本文将其应用于胃癌 ATAC-seq 数据，扩展了该方法在癌症表观基因组学中的应用。
- **EMT 调控网络**：与已知 EMT 调控因子（ZEB1、SNAI2、TWIST）一致，本文新增 RUNX2 和 AP-1 作为胃癌 EMT 的驱动因子，与已有文献中 RUNX2 在乳腺癌、前列腺癌中促进 EMT 的报道一致。
- **TCGA-STAD 数据**：使用了 TCGA 胃癌队列的 ATAC-seq、RNA-seq 和 CNV 数据，与 TCGA 泛癌分析（Hoadley et al. 2018）中胃癌分子分型相关联。
- **单细胞胃癌图谱**：与 Kim et al. (2022) 的胃癌 scRNA-seq 数据对比，确认 Mes-like 细胞系与成纤维细胞状态的对应关系。
- **候选方向**：本文的「TF 活性推断 + 多组学验证」框架可迁移至其他癌症类型（如乳腺癌、肺癌）的 EMT 研究，或用于预测 TF 结合位点的功能影响（如结合突变）。

## 16 研究想法
**Agent 生成的研究候选**：
1. **名称**：基于 gkm-SVM 的泛癌 EMT 驱动 TF 图谱
   - **来源局限/观察**：本文仅聚焦胃癌，EMT 驱动 TF 可能具有癌症类型特异性或普遍性。
   - **核心假设**：RUNX/AP-1 驱动的间质程序在多种癌症类型中保守，但伴随组织特异的辅助 TF。
   - **增量**：将 gkm-SVM 流程应用于 TCGA 泛癌 ATAC-seq 数据，构建跨癌种 EMT 驱动 TF 图谱。
   - **初步方法**：对 TCGA 各癌种的 ATAC-seq 数据训练 gkm-SVM，提取差异活性 TF，与 EMT 评分关联。
   - **验证方式**：与已发表的 ChIP-seq 数据交叉验证，并在独立队列中验证预后价值。
   - **创新状态**：unverified

2. **名称**：RUNX/AP-1 协同结合增强子的结构机制
   - **来源局限/观察**：本文预测 RUNX/AP-1 驱动间质程序，但未解析其协同结合的分子机制。
   - **核心假设**：RUNX 与 AP-1 在增强子上形成协同复合物，通过蛋白质-蛋白质互作稳定结合。
   - **增量**：结合结构预测（AlphaFold）与分子动力学模拟，解析 RUNX2-FOS/JUN-DNA 三元复合物的结构。
   - **初步方法**：使用 AlphaFold 预测 RUNX2 与 FOS/JUN 的互作界面，MD 模拟验证稳定性，突变实验验证关键残基。
   - **验证方式**：EMSA 和 ChIP-seq 验证突变对结合的影响。
   - **创新状态**：unverified

3. **名称**：拷贝数变异驱动的 TF 调控网络重构
   - **来源局限/观察**：本文发现 GATA4 缺失和 MAPK9 扩增与间质状态相关，但未系统分析 CNV 对 TF 网络的影响。
   - **核心假设**：CNV 通过改变 TF 剂量和信号通路活性，系统性重构调控网络。
   - **增量**：整合 CNV、ATAC-seq、RNA-seq 数据，构建 CNV-TF-靶基因调控网络。
   - **初步方法**：使用贝叶斯网络或因果推断方法，识别 CNV 驱动的 TF 活性变化。
   - **验证方式**：在细胞系中敲除/扩增候选基因，验证网络预测。
   - **创新状态**：unverified

4. **名称**：单细胞 ATAC-seq 的 TF 活性推断方法
   - **来源局限/观察**：本文使用 bulk ATAC-seq，单细胞水平的 TF 活性异质性未解析。
   - **核心假设**：单细胞 ATAC-seq 数据可通过 gkm-SVM 推断细胞类型特异的 TF 活性。
   - **增量**：将 gkm-SVM 扩展到单细胞数据，处理稀疏性和噪声问题。
   - **初步方法**：使用 scATAC-seq 数据，对每个细胞或细胞簇训练 gkm-SVM，推断 TF 活性。
   - **验证方式**：与 scRNA-seq 的 TF 表达关联，验证细胞类型特异性。
   - **创新状态**：unverified

5. **名称**：增强子突变对 RUNX/AP-1 结合的影响预测
   - **来源局限/观察**：本文识别了 RUNX/AP-1 结合的增强子，但未分析增强子突变对结合的影响。
   - **核心假设**：间质程序相关增强子的体细胞突变可改变 RUNX/AP-1 结合，影响靶基因表达。
   - **增量**：使用 gkm-SVM 预测突变对 TF 结合的影响，结合 TCGA 突变数据。
   - **初步方法**：对间质程序相关增强子进行突变扫描，预测结合分数变化。
   - **验证方式**：在细胞系中引入突变，验证对靶基因表达的影响。
   - **创新状态**：unverified