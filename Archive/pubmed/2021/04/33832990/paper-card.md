## 01 基本信息
- **标题**：Interpretation of allele-specific chromatin accessibility using cell state-aware deep learning
- **作者与单位**：Atak, Zeynep Kalender; Taskiran, Ibrahim Ihsan; Demeulemeester, Jonas; Flerin, Christopher; Mauduit, David; Minnoye, Liesbeth; Hulselmans, Gert; Christiaens, Valerie; Ghanem, Ghanem-Elias; Wouters, Jasper; Aerts, Stein（VIB-KU Leuven 等，具体单位未提供）
- **期刊/预印本平台**：Genome Research
- **年份**：2021-04-10
- **论文类型**：研究论文（Research Article）
- **领域**：计算基因组学；调控基因组学；深度学习
- **关键词**：allele-specific chromatin accessibility; deep learning; melanoma; transcription factor binding; cis-regulatory variants
- **DOI/arXiv 号**：10.1101/gr.260851.120
- **代码**：https://github.com/aertslab/AS_variant_pipeline；https://github.com/aertslab/DeepMEL
- **数据**：GEO: GSE134432, GSE142238, GSE159965；EGA: EGAS00001004136
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向，聚焦于利用细胞状态感知的深度学习模型（DeepMEL2）解释等位基因特异的染色质开放性（ASCAV），并验证 TF 结合位点的获得/丢失（尤其是 AP-1 和 SOX10）对染色质开放性的因果影响。该文是 DeepMEL 系列工作的延伸，展示了将细胞状态（melanocytic vs. mesenchymal）纳入模型可显著提升非编码变异解释能力，并提供了从变异到 TF 结合、染色质开放性、基因表达的多层验证框架。

## 02 一句话总结
本文通过构建细胞状态感知的深度学习模型 DeepMEL2（在 30 个黑色素瘤细胞系的 ATAC-seq 数据上训练，并以 JASPAR PWM 初始化卷积核），对 10 个黑色素瘤样本中检测到的等位基因特异性染色质开放性变异（ASCAV）进行解释，发现 15%–20% 的 ASCAV 可由 TF 结合位点的获得/丢失解释，其中 AP-1 家族（JUN、FOSL1）占主导，并通过 ChIP-seq 和荧光素酶报告实验验证了 AP-1 和 SOX10 结合位点变异的因果效应。

## 03 研究问题
- **具体问题**：如何从数百万个非编码基因组变异中识别那些影响顺式调控功能（尤其是染色质开放性）的变异？如何解释等位基因特异的染色质开放性（ASCAV）的分子机制？
- **为什么重要**：非编码变异在癌症（如黑色素瘤）中驱动肿瘤表型和治疗耐药，但绝大多数变异是"乘客"突变，缺乏功能注释。识别功能性非编码变异对理解肿瘤生物学和精准医学至关重要。
- **现有方法不足**：基于 PWM 的 motif 扫描方法假阳性率高、灵敏度低（仅能解释 3.3%–6.2% 的变异）；通用深度学习模型（如 DeepSEA、Basset）虽能捕捉更复杂的序列特征，但未考虑细胞状态特异性，在黑色素瘤 melanocytic 亚型上表现不佳。
- **精确研究问题**：Can a cell state-aware deep learning model trained on matched melanoma ATAC-seq data outperform generic models and PWM-based approaches in identifying allele-specific chromatin accessibility variants (ASCAVs) and explaining their underlying TF binding changes?

## 04 背景与发展脉络
（注：以下脉络为「经外部核验」的领域发展概述，结合本文引用与领域常识）
1. **PWM/motif 扫描时代**：利用位置权重矩阵（PWM）扫描变异是否影响 TF 结合位点（如 FABIAN-variant、snpEff）。局限：假阳性高、灵敏度低，无法捕捉协同结合和染色质环境。
2. **通用深度学习模型**：DeepSEA（Zhou & Troyanovsky, 2015）和 Basset（Kelley et al., 2016）在大规模 DNase-seq/ChIP-seq 数据上训练，可预测变异对染色质特征的影响。局限：训练数据来自多种细胞类型，缺乏细胞状态特异性，对罕见细胞状态（如黑色素瘤 melanocytic 亚型）预测不准。
3. **细胞状态感知模型**：本文提出的 DeepMEL2 是 DeepMEL（Minnoye et al., 2020）的扩展，在 30 个黑色素瘤细胞系的 ATAC-seq 数据上训练，并以 JASPAR PWM 初始化卷积核，显式建模 melanocytic 和 mesenchymal 两种细胞状态的调控程序。
4. **等位基因特异性分析**：利用 phased 基因组和 ATAC-seq 的等位基因计数，直接检测染色质开放性的等位基因不平衡（ASCAV），为变异功能验证提供更直接的证据。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PWM 方法灵敏度低 | 仅能解释 3.3%–6.2% 的等位基因特异性变异 | PWM 扫描需要严格阈值，且不考虑序列上下文和协同结合 | Results 节 "PWM-based approaches typically have low sensitivity (e.g., 3.3%–6.2% explainable variants)" |
| 通用深度学习模型缺乏细胞状态特异性 | DeepSEA/Basset 在 melanocytic 亚型上表现不佳 | 训练数据以常见细胞类型为主，黑色素瘤 melanocytic 状态在 ENCODE 中代表性不足 | Results 节 "melanocyte and MEL-melanoma states are likely underrepresented in ENCODE" |
| 癌症基因组中拷贝数变异干扰等位基因分析 | 拷贝数改变导致等位基因比例偏离预期，影响 ASCAV 检测 | 传统二项/β-二项检验未考虑拷贝数状态 | Methods 节 "BaCHIP enabled us to correct the allelic ratios... for the extensive copy number variation" |
| 非编码变异功能验证困难 | 大量 ASCAV 无法用单一 motif 解释 | 变异可能影响多个 TF 结合位点或非 motif 序列特征 | Results 节 "15%–20% can be explained by gains or losses of TF binding sites" |

## 06 核心思想
1. **表面方法**：构建一个混合 CNN-RNN 深度学习模型（DeepMEL2），在 30 个黑色素瘤细胞系的 ATAC-seq 数据上训练，预测 47 个顺式调控主题（cis-regulatory topics）。模型以 JASPAR PWM 初始化卷积核，输入 500-bp DNA 序列，输出 47 维向量。对每个 ASCAV，通过计算参考/替代等位基因的预测差异（delta score）来评估变异的功能影响。
2. **核心洞察**：细胞状态是解释非编码变异功能的关键上下文。同一变异在不同细胞状态（melanocytic vs. mesenchymal）下可能有完全不同的功能影响。通过将细胞状态纳入模型训练（而非使用通用模型），可以显著提高对黑色素瘤特异性调控变异的解释能力。此外，将 ChIP-seq 数据（如 GABPA）作为额外标签加入模型，可以针对特定 TF 家族进行微调，从而识别出常规模型无法捕捉的致癌突变（如 TERT 启动子突变）。
3. **可能的普适教训** [Analysis]：深度学习模型的可解释性不仅取决于模型架构，还取决于训练数据的"上下文匹配度"。对于组织/细胞类型特异的调控变异，使用匹配的细胞状态数据训练模型比使用大规模但异质的数据更有效。此外，将先验生物学知识（如 PWM）注入模型初始化，可以加速收敛并提高可解释性。

## 07 方法总览
- **输入**：500-bp DNA 序列（以 ASCAV 或对照变异为中心）；等位基因特异的 ATAC-seq 计数；phased 基因组变异（SNV/indel）
- **输出**：47 个 cis-regulatory topics 的预测分数（DeepMEL2）；48 个 topics（DeepMEL2+GABPA）；每个变异的 delta score（参考 vs 替代等位基因的预测差异）
- **模块**：
  1. 数据生成：10 个黑色素瘤细胞系的 phased WGS + ATAC-seq；30 个细胞系的 ATAC-seq 用于训练
  2. 变异检测：修改的 AlleleSeq 流程 + BaCHIP 拷贝数校正
  3. 主题识别：cisTopic 从 30 个细胞系的 ATAC-seq 中识别 47 个共可及区域主题
  4. 深度学习模型：CNN（300 个卷积核，其中 283 个以 JASPAR PWM 初始化）→ 池化 → BiLSTM → 全连接 → 47 维输出
  5. 变异评分：对每个 ASCAV，计算参考/替代等位基因的 delta 预测分数
  6. 验证：AP-1 ChIP-seq（JUN、JUNB、FOS、FOSL1）验证等位基因特异性结合；荧光素酶报告实验验证增强子活性
- **训练**：80% 训练、10% 验证、10% 测试；评估指标为 auROC 和 auPR
- **反馈回路**：无显式反馈回路；模型为前馈预测
- **假设**：染色质开放性（ATAC-seq 信号）主要由顺式序列决定；等位基因不平衡反映顺式调控变异的影响；细胞状态（MEL vs. MES）可通过 ATAC-seq 模式区分

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Phased WGS + 变异检测 | 获得单倍型分辨的基因组变异 | 等位基因特异性分析需要知道变异所在的单倍型 | 输入：WGS reads；输出：phased 变异 + 等位基因计数 | Results 图 1A-D；Methods "Identification of ASCAVs" | 无法区分等位基因来源，ASCAV 检测不可行 |
| BaCHIP 拷贝数校正 | 校正拷贝数变异导致的等位基因比例偏移 | 癌症基因组普遍存在拷贝数改变，违反等位基因平衡假设 | 输入：WGS 等位基因比例 + ATAC-seq 计数；输出：校正后的 ASCAV | Methods "BaCHIP enabled us to correct the allelic ratios" | 大量假阳性/假阴性 ASCAV |
| cisTopic 主题识别 | 从 ATAC-seq 中识别共可及区域 | 定义细胞状态特异的调控程序 | 输入：30 个细胞系 ATAC-seq；输出：47 个主题 | Results 图 3A；Methods "cisTopic analysis" | 无法定义细胞状态特异的训练标签 |
| DeepMEL2 深度学习模型 | 预测 500-bp 序列的调控活性 | 捕捉 PWM 无法建模的序列特征和协同结合 | 输入：500-bp DNA；输出：47 维主题分数 | Results 图 3C-D；Supplemental Table S12 | 无法解释非 motif 变异 |
| PWM 初始化卷积核 | 将先验 TF 结合知识注入模型 | 加速收敛、提高可解释性 | 输入：JASPAR PWM；输出：初始化的卷积核 | Methods "283 of 300 filters are populated with JASPAR PWMs" | 模型可能收敛更慢，可解释性降低 |
| Delta score 变异评分 | 计算参考/替代等位基因的预测差异 | 评估变异对调控活性的影响 | 输入：参考/替代序列；输出：delta score | Results 图 3E-F；Methods "Scoring enhancers and ASCAVs" | 无法评估变异功能影响 |
| AP-1 ChIP-seq 验证 | 验证等位基因特异的 TF 结合 | 确认预测的 TF 结合变化在体内真实发生 | 输入：ChIP-seq reads；输出：等位基因特异的结合事件 | Results 图 4A-C；Supplemental Fig. S13 | 预测缺乏实验验证 |
| 荧光素酶报告实验 | 验证增强子活性的等位基因差异 | 确认变异对增强子功能的因果影响 | 输入：参考/替代等位基因的增强子序列；输出：荧光素酶活性 | Results 图 4D-F | 无法确认变异对基因表达的因果效应 |

## 09 关键公式符号
本文未提供显式的数学公式。核心概念包括：
- **Delta score**：Δ = f(seq_alt) − f(seq_ref)，其中 f 为 DeepMEL2 对给定 500-bp 序列的预测输出（47 维向量中的某一主题分数）
- **BaCHIP 贝叶斯模型**：后验估计 Beta(1 + #A, 1 + #B)，用于校正拷贝数变异下的等位基因比例
- **β-二项检验**：用于检测 RNA-seq 等位基因特异性表达，其中 WGS 后验等位基因频率作为先验

## 10 实验设计与证据链
- **数据集**：10 个患者来源的黑色素瘤细胞系（MM 系）；30 个黑色素瘤细胞系（含上述 10 个）用于训练
- **数据规模**：WGS 平均深度 38×（MM087 为 68×，MM099 为 133×）；ATAC-seq 平均 65M reads/样本
- **指标**：auROC、auPR（模型性能）；ASCAV 解释率（15%–20%）；ASCAV 与 ASE/ASHV 的重叠率
- **基线**：PWM 方法（22,000 个 motif）、DeepSEA、Basset、DeepMEL
- **评测协议**：留出法（80/10/10 划分）；ASCAV 检测使用 5% FDR 阈值；ASCAV 解释使用 95% 特异性阈值
- **验证实验**：AP-1 ChIP-seq（JUN、JUNB、FOS、FOSL1）检测等位基因特异性结合；荧光素酶报告实验验证增强子活性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| ASCAV 检测 | 等位基因特异性染色质开放性可被可靠检测 | 10 个 MM 系；BaCHIP 校正拷贝数 | 19,983 个显著 ASCAV（8.6% 的峰内变异） | 等位基因不平衡在黑色素瘤中普遍存在 | 未证明所有 ASCAV 均有功能 | Results 图 1C-D |
| Motif 富集分析 | ASCAV 富集于 TF 结合位点 | 22,000 个 PWM；Fisher 精确检验 | AP-1 家族（191 个 motif）为最显著富集 | AP-1 结合位点变化是 ASCAV 的主要驱动因素 | 未证明 AP-1 是唯一机制 | Results 图 2A-D |
| DeepMEL2 vs 基线 | 细胞状态感知模型优于通用模型 | DeepMEL2 vs DeepSEA、Basset、PWM | DeepMEL2 在 MEL 系上解释率最高（15%–20%） | 细胞状态匹配显著提升解释能力 | 未在非黑色素瘤癌症中验证 | Results 图 3G；Supplemental Fig. S11 |
| AP-1 ChIP-seq 验证 | 预测的 AP-1 结合变化在体内真实发生 | MM099 中 JUN/FOSL1 ChIP-seq | 583 个 JUN 和 241 个 FOSL1 等位基因特异性结合事件 | 预测的 AP-1 位点变化具有生物学真实性 | 未覆盖所有 ASCAV | Results 图 4A-C |
| 荧光素酶报告实验 | ASCAV 影响增强子活性 | MM057 中 3 个增强子（PEPD、MITF、EVA1C） | 仅含预测 motif 的等位基因驱动增强子活性 | 变异对增强子功能有因果影响 | 样本量小（n=3） | Results 图 4D-F |
| TERT 启动子分析 | 模型可识别致癌突变 | GABPA ChIP-seq 增强模型 | 模型识别 TERT 启动子突变（C228T/C250T） | 模型可推广到已知致癌突变 | 未在更大队列中验证 | Results 图 5A-E |

## 11 结论正确解读
- **任务范围**：本文聚焦于黑色素瘤细胞系中的等位基因特异性染色质开放性变异（ASCAV）解释，不涉及其他癌症类型或正常组织。
- **Oracle/真值输入**：ASCAV 的检测依赖于 ATAC-seq 等位基因计数，其准确性受测序深度、拷贝数状态和等位基因特异性表达的影响；ChIP-seq 验证仅覆盖 AP-1 家族（JUN、FOSL1）和部分位点。
- **端到端状态**：模型预测（delta score）与实验验证（ChIP-seq、报告基因）之间存在一致性，但并非所有 ASCAV 都经过实验验证；模型解释率（15%–20%）意味着大部分 ASCAV 的机制仍未知。
- **算力成本**：未提供具体训练时间或硬件信息。
- **历史数据依赖**：模型训练依赖 30 个黑色素瘤细胞系的 ATAC-seq 数据，这些数据来自体外培养的细胞系，可能不完全代表体内肿瘤微环境。
- **模型依赖**：DeepMEL2 的性能依赖于 cisTopic 主题识别的质量；主题数量（47）的选择基于 log-likelihood，但未进行敏感性分析。
- **最难情形**：melanocytic 亚型（如 MM001）的 ASCAV 解释率最低，可能反映该亚型中非 AP-1 机制（如 SOX10）的主导作用。
- **群体/领域边界**：结论仅适用于黑色素瘤；模型对其他细胞类型或组织的适用性未验证。
- **不确定性**：ASCAV 与 ASE/ASHV 的重叠率较低（6% 与 343/4016），表明染色质开放性的等位基因不平衡不一定导致基因表达或组蛋白修饰的等位基因不平衡。

**有边界的复述**：在 10 个黑色素瘤细胞系中，约 8.6% 的峰内变异表现为等位基因特异的染色质开放性；其中 15%–20% 可由 TF 结合位点的获得/丢失解释，AP-1 家族（尤其是 JUN 和 FOSL1）是主要贡献者；细胞状态感知的 DeepMEL2 模型在 melanocytic 亚型上优于通用模型，且通过 ChIP-seq 增强可识别 TERT 启动子致癌突变。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 样本量有限 | 仅 10 个黑色素瘤细胞系 | 扩展到更多样本和癌症类型 | Discussion 节 "each cancer type may require its own 'matched' deep learning model" |
| 模型解释率有限 | 15%–20% 的 ASCAV 可被解释 | 纳入更多 TF 结合数据和调控机制 | Discussion 节 "a sizable fraction of these events... without any other observed consequences" |
| 细胞系与体内差异 | 体外培养可能不反映体内肿瘤微环境 | 应用于单细胞 ATAC-seq 和活检样本 | Discussion 节 "our framework is in principle also applicable to data obtained from bulk tumor biopsies" |
| 模型对特定 TF 的盲区 | 初始模型无法识别 TERT 启动子突变 | 通过 ChIP-seq 数据增强模型 | Results 节 "the model does not predict the oncogenic gains of GABPA sites themselves" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| ASCAV 检测依赖 ATAC-seq 等位基因计数 | 等位基因计数可能受测序偏好、PCR 重复和比对偏差影响 | 若计数有偏，ASCAV 检测可能产生假阳性 | 使用独立技术（如 RNA-seq 或 ChIP-seq 的等位基因计数）交叉验证 | Methods "Identification of ASCAVs" 未提及技术重复或偏差校正 |
| AP-1 富集可能反映 motif 数据库偏差 | JASPAR 中 AP-1 motif 数量多，可能造成富集假象 | 若富集是数据库偏差，则 AP-1 的主导作用可能被高估 | 使用 motif 家族聚类或独立 motif 数据库验证 | Results 图 2A-D 未进行 motif 家族层面的多重检验校正 |
| DeepMEL2 与基线模型的比较未报告置信区间 | 解释率差异可能不显著 | 若差异不显著，细胞状态感知的优势不成立 | 报告多次重复实验的方差或使用统计检验 | Results 图 3G 未提供误差线或统计检验 |
| 荧光素酶报告实验仅验证 3 个位点 | 样本量小，可能无法代表整体 | 若 3 个位点有选择偏差，结论可能过度推广 | 扩大验证位点数量或使用高通量报告实验（如 STARR-seq） | Results 图 4D-F 仅 3 个增强子 |
| TERT 启动子分析依赖 GABPA ChIP-seq 数据 | 模型增强可能仅对 GABPA 有效，对其他 TF 无效 | 若增强不可推广，模型的应用范围有限 | 用其他 TF 的 ChIP-seq 数据测试模型增强 | Results 图 5A-E 仅测试了 GABPA |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **细胞状态感知的训练策略**：在训练深度学习模型时，使用与目标细胞类型/状态匹配的数据（而非大规模异质数据）可显著提升变异解释能力。可迁移到 TF–DNA 结合预测：针对特定细胞类型训练模型，而非依赖通用模型。
2. **PWM 初始化卷积核**：用 JASPAR PWM 初始化 CNN 卷积核是一种有效的先验注入方式，可提高模型可解释性并加速收敛。可迁移到 TF–DNA 结合预测模型的架构设计中。
3. **等位基因特异性分析作为变异功能验证的桥梁**：利用 phased 基因组和 ATAC-seq 等位基因计数直接检测调控变异的功能影响，比单纯预测变异效应更接近生物学真实。可迁移到 TF–DNA 结合机制研究：结合等位基因特异性 ChIP-seq 或 ATAC-seq 验证预测的 TF 结合变化。
4. **ChIP-seq 数据增强模型**：将特定 TF 的 ChIP-seq 数据作为额外标签加入模型训练，可识别常规模型无法捕捉的致癌突变（如 TERT 启动子）。可迁移到 TF–DNA 结合预测：针对特定 TF 家族微调模型，提高对罕见但重要突变的检测能力。
5. **多组学验证框架**：从变异检测（WGS）→ 功能预测（深度学习）→ 分子验证（ChIP-seq、报告基因）的完整流程，为 TF–DNA 结合机制研究提供了可复制的实验设计模板。
6. **拷贝数校正的重要性**：在癌症基因组中分析等位基因特异性事件时，必须考虑拷贝数变异的影响（BaCHIP 方法）。可迁移到 TF–DNA 结合研究：在肿瘤样本中分析 TF 结合时，需校正拷贝数对等位基因比例的影响。

## 15 与已有知识连接
- **DeepSEA**（Zhou & Troyanovsky, 2015）和 **Basset**（Kelley et al., 2016）：本文直接比较了 DeepMEL2 与这两个通用深度学习模型的性能，展示了细胞状态感知的优势。
- **DeepMEL**（Minnoye et al., 2020）：本文是 DeepMEL 的扩展，增加了训练样本量（16→30）和 PWM 初始化。
- **AlleleSeq**（Chen et al., 2016）：本文修改了 AlleleSeq 流程用于 ASCAV 检测。
- **BaCHIP**（de Santiago et al., 2017）：本文使用 BaCHIP 进行拷贝数校正的等位基因特异性分析。
- **cisTopic**（González-Blas et al., 2019）：本文使用 cisTopic 识别顺式调控主题。
- **JASPAR**（Fornes et al., 2020）：本文使用 JASPAR PWM 初始化卷积核。
- **TF–DNA 结合机制**：AP-1 作为先锋因子（pioneer factor）在染色质重塑中的作用（Biddie et al., 2011）与本文发现的 AP-1 主导 ASCAV 一致。
- **TERT 启动子突变**：已知的致癌突变（Horn et al., 2013; Huang et al., 2013）在本文中被用作模型验证案例。
- **可迁移方向**：本文的「细胞状态感知」策略可迁移到其他 TF–DNA 结合预测任务（如预测细胞类型特异的 TF 结合位点）；「PWM 初始化」可迁移到可解释的深度学习模型设计；「等位基因特异性分析」可迁移到任何 TF–DNA 结合机制的功能验证研究。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：Cell-type-aware TF–DNA binding prediction with PWM-initialized hybrid CNN-RNN
   - **来源局限/观察**：本文展示了细胞状态感知在染色质开放性预测中的优势，但未直接预测 TF 结合；通用 TF 结合预测模型（如 DeepBind）缺乏细胞类型特异性。
   - **核心假设**：在特定细胞类型的 ChIP-seq 数据上训练、以 PWM 初始化的深度学习模型，能比通用模型更准确地预测该细胞类型中的 TF 结合位点。
   - **初步方法**：收集多种细胞类型的 TF ChIP-seq 数据，训练细胞类型特异的 CNN-RNN 模型，以 PWM 初始化卷积核；比较与通用模型的性能。
   - **验证方式**：在留出细胞类型上评估 auROC/auPR；用等位基因特异性 ChIP-seq 数据验证预测的变异效应。
   - **创新状态**：unverified（需验证细胞类型特异性的增益是否在 TF 结合预测中成立）

2. **候选名称**：Integrating allele-specific chromatin accessibility with TF binding prediction for variant prioritization
   - **来源局限/观察**：本文的 ASCAV 检测与 DeepMEL2 预测是分离的；将两者整合可能提高变异优先级排序的准确性。
   - **核心假设**：结合 ASCAV 的等位基因不平衡信号和深度学习预测的 delta score，可以更准确地识别功能性非编码变异。
   - **初步方法**：开发一个联合模型，输入为变异序列和等位基因特异的 ATAC-seq 计数，输出为变异功能影响的概率。
   - **验证方式**：在独立黑色素瘤数据集中评估变异优先级排序的精确率；用 CRISPR 干扰实验验证 top-ranked 变异。
   - **创新状态**：unverified（需验证联合模型是否优于单独使用任一信号）

3. **候选名称**：Transfer learning from chromatin accessibility to TF binding with cell state adaptation
   - **来源局限/观察**：本文的 DeepMEL2 在染色质开放性上训练，但可迁移到 TF 结合预测；TF ChIP-seq 数据稀缺，而 ATAC-seq 数据丰富。
   - **核心假设**：在 ATAC-seq 上预训练的模型，通过少量 TF ChIP-seq 数据微调，可以比从头训练的模型更准确地预测 TF 结合。
   - **初步方法**：使用 DeepMEL2 作为预训练模型，在 TF ChIP-seq 数据上微调；比较与从头训练模型的性能。
   - **验证方式**：在多种 TF 和细胞类型上评估预测精度；用 motif 富集分析验证模型学到的序列特征。
   - **创新状态**：unverified（需验证迁移学习的增益是否显著）

4. **候选名称**：Predicting allele-specific TF binding from sequence with explainable deep learning
   - **来源局限/观察**：本文验证了 AP-1 和 SOX10 的等位基因特异性结合，但未开发专门的预测模型；现有 ASB 预测方法依赖 motif 扫描。
   - **核心假设**：深度学习模型可以捕捉 motif 之外的序列特征（如协同结合、染色质环境），从而更准确地预测等位基因特异的 TF 结合。
   - **初步方法**：在等位基因特异性 ChIP-seq 数据上训练 CNN 模型，预测变异是否导致 ASB；用 SHAP 或 DeepExplainer 解释模型。
   - **验证方式**：在独立 ASB 数据集中评估预测精度；用荧光素酶报告实验验证 top-ranked 变异。
   - **创新状态**：unverified（需验证深度学习是否优于 motif 扫描）

5. **候选名称**：Multi-omics integration for cis-regulatory variant interpretation in cancer
   - **来源局限/观察**：本文整合了 WGS、ATAC-seq、ChIP-seq、RNA-seq 数据，但未开发统一的整合模型；现有方法通常只使用单一数据源。
   - **核心假设**：整合等位基因特异的染色质开放性、TF 结合、组蛋白修饰和基因表达数据，可以更全面地解释非编码变异的功能。
   - **初步方法**：开发一个多模态深度学习模型，输入为序列和多种表观遗传信号，输出为变异功能影响的综合评分。
   - **验证方式**：在黑色素瘤和其他癌症数据集中评估变异优先级排序；用 CRISPR 筛选验证 top-ranked 变异。
   - **创新状态**：unverified（需验证多模态整合是否优于单模态）