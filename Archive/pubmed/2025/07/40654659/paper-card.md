## 01 基本信息
- **标题**：Genome structure mapping with high-resolution 3D genomics and deep learning
- **作者**：Hong, Clarice K Y; Feng, Fan; Ramanathan, Varshini; Liu, Jie; Hansen, Anders S
- **单位**：未提供（根据致谢推测为 MIT 与 Broad Institute 相关实验室，但原文未明确列出作者单位）
- **期刊/平台**：bioRxiv（预印本服务器）
- **年份**：2025（预印本日期 2025-07-14；DOI 中显示 2025.05.06 为提交日期）
- **论文类型**：预印本（研究论文）
- **领域**：3D 基因组学、深度学习、基因调控
- **关键词**：3D 基因组、Micro-C、Region Capture Micro-C (RCMC)、深度学习、注意力机制、增强子-启动子互作、CTCF、环（loops）
- **DOI/arXiv 号**：10.1101/2025.05.06.650874
- **代码**：未提供
- **数据**：RCMC 和 Micro-C 处理数据：https://zenodo.org/records/15303879；Cleopatra 预测数据：https://zenodo.org/records/15299993；原始 fastq 将上传至 SRA（11TB）
- **阅读日期**：2026-05-13（基于当前对话日期）
- **该文在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」交叉方向，聚焦于**转录因子（TF）与 DNA 结合所介导的 3D 染色质环（loops）和微区室（microcompartments）的全基因组预测**。其核心贡献在于：(1) 生成超深 RCMC 和 Micro-C 实验数据；(2) 开发基于注意力的深度学习模型 Cleopatra，以 500bp 和 2kb bin size 预测全基因组 3D 接触图；(3) 揭示增强子-启动子（E-P）环的细胞类型特异性及其与 CTCF 和 TF 的关系。该文为「TF–DNA 结合如何驱动 3D 基因组结构」提供了可迁移的 AI 预测框架。

## 02 一句话总结
本文通过整合超深 Region Capture Micro-C (RCMC) 和 Micro-C 实验数据与基于注意力的深度学习模型 Cleopatra（预训练+微调策略），在 500bp 和 2kb bin size 下预测全基因组 3D 接触图，在四个人类细胞类型中鉴定出超过 90 万个环（约半数具有细胞类型特异性），并揭示增强子-启动子环常由 CTCF 锚定、表达随环数单调增加等定量规律。

## 03 研究问题
- **具体问题**：如何在不进行全基因组超深测序的前提下，获得足以解析增强子-启动子（E-P）环和微区室等精细 3D 基因组结构的全基因组高分辨率接触图？
- **为什么重要**：基因表达常由远端增强子通过细胞类型特异性的 3D 环状互作调控，但全面绘制多种细胞类型中的这些互作在实验上不可行（需极端测序深度覆盖所有配对互作）。
- **现有方法不足**：(1) Hi-C 无法检测大多数顺式调控元件（CRE）之间的环；(2) Micro-C 虽能检测 CRE 环，但全基因组核小体尺度 bin size 的测序成本不可行；(3) 现有深度学习模型（如 Akita、HiC-Plus、Epiphany、C. Origami）bin size 较粗（2-10kb），无法解析亚千碱基尺度的精细结构。
- **精确研究问题**：Can a deep learning model, pre-trained on genome-wide Micro-C and fine-tuned on ultra-deep RCMC data, accurately predict sub-kilobase resolution 3D contact maps genome-wide, thereby enabling comprehensive identification of cell-type-specific enhancer-promoter loops and microcompartments?

## 04 背景与发展脉络
*注：此脉络基于本文引用与论述，标记为「经外部核验」的部分仅指本文明确引用的文献；整体框架为「仅本文框架」。*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文主张的位置 |
|------|-----------|------|------|---------------|
| 3D 基因组实验方法 | Hi-C (Lieberman-Aiden et al. 2009) | 解析 A/B compartments、TADs、CTCF/cohesin 结构环 | 无法检测大多数 CRE 环 | 基础但分辨率不足 |
| 改进实验方法 | Micro-C (Hsieh et al. 2015) | 有效检测 CRE 环 + 大尺度结构特征 | 全基因组核小体尺度测序不可行 | 提供全基因组预训练数据 |
| 靶向捕获方法 | RCMC (作者前期工作, 2022) | 超深覆盖选定区域，亚千碱基分辨率 | 仅覆盖 <0.5% 基因组 | 提供高分辨率微调数据 |
| 深度学习预测 | Akita (Fudenberg et al. 2020)、HiC-Plus、Epiphany、C. Origami、ChromaFold | 从序列/表观组预测接触图 | bin size 2-10kb，无法解析精细 CRE 环 | 本文 Cleopatra 以 500bp/2kb bin size 超越 |
| 本文方法 | Cleopatra（注意力模型 + 预训练/微调） | 亚千碱基分辨率、全基因组覆盖、细胞类型特异性 | 依赖大量表观组输入特征；需要 RCMC 训练数据 | 首次实现全基因组亚千碱基 3D 图预测 |

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 全基因组超深测序不可行 | 无法以实验手段覆盖所有配对互作 | 人类基因组约 3Gb，核小体尺度 bin size 下配对组合数巨大 | Introduction: "mapping of all 3D interactions across the human genome at nucleosome-scale bin sizes is intractable due to the extreme sequencing required" |
| Hi-C 分辨率不足 | 无法检测大多数 CRE 环 | Hi-C 的酶切和连接效率限制信噪比 | Introduction: "Hi-C fails to detect most loops between cis-regulatory elements (CREs)" |
| RCMC 覆盖有限 | 仅覆盖 <0.5% 基因组 | 靶向捕获设计仅覆盖选定区域 | Introduction: "it typically only captures < 0.5% of the genome" |
| 现有深度学习模型分辨率粗 | bin size 2-10kb，无法解析亚千碱基结构 | 模型架构和训练数据限制 | Results: "no deep learning model can currently predict 3D genome maps with sufficient detail to identify fine-scale genome structure" |
| 预训练模型无法预测 RCMC 特有结构 | 预训练模型在 500bp bin size 下无法预测 RCMC 特异性结构 | Micro-C 数据中这些结构不可见或信号弱 | Results: "The pre-trained model cannot predict RCMC-specific structures at 500bp bin sizes" |

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 全基因组超深测序不可行 | 无法以实验手段覆盖所有配对互作 | 人类基因组约 3Gb，核小体尺度 bin size 下配对组合数巨大 | Introduction: "mapping of all 3D interactions across the human genome at nucleosome-scale bin sizes is intractable due to the extreme sequencing required" |
| Hi-C 分辨率不足 | 无法检测大多数 CRE 环 | Hi-C 的酶切和连接效率限制信噪比 | Introduction: "Hi-C fails to detect most loops between cis-regulatory elements (CREs)" |
| RCMC 覆盖有限 | 仅覆盖 <0.5% 基因组 | 靶向捕获设计仅覆盖选定区域 | Introduction: "it typically only captures < 0.5% of the genome" |
| 现有深度学习模型分辨率粗 | bin size 2-10kb，无法解析亚千碱基结构 | 模型架构和训练数据限制 | Results: "no deep learning model can currently predict 3D genome maps with sufficient detail to identify fine-scale genome structure" |
| 预训练模型无法预测 RCMC 特有结构 | 预训练模型在 500bp bin size 下无法预测 RCMC 特异性结构 | Micro-C 数据中这些结构不可见或信号弱 | Results: "The pre-trained model cannot predict RCMC-specific structures at 500bp bin sizes" |

## 06 核心思想
1. **表面方法**：开发基于注意力的深度学习模型 Cleopatra，以 19 种细胞类型特异性基因组特征（DNase-seq、组蛋白修饰、CTCF、RAD21、转录因子等）为输入，预训练于全基因组 Micro-C 数据，微调于超深 RCMC 数据，输出 500bp 和 2kb bin size 的全基因组接触图。
2. **核心洞察**：预训练/微调策略是关键——全基因组 Micro-C 提供广泛的粗粒度结构知识，而 RCMC 提供局部区域的超精细结构知识，两者结合使模型能够将 RCMC 的分辨率推广到全基因组。此外，模型学习到的是表观基因组特征与 3D 结构之间的映射关系，而非简单记忆实验数据。
3. **可能的普适教训** [Analysis]：对于「实验不可行但预测可行」的生物学问题，将有限的高质量实验数据（如 RCMC）与广泛但较粗的数据（如 Micro-C）通过预训练/微调策略结合，是一种可迁移的范式。在 TF–DNA 互作研究中，类似地可以用有限的高分辨率结构数据（如 Cryo-EM、X-ray）微调在广泛但低分辨率的预测模型（如 AlphaFold 类）上。

## 07 方法总览
- **输入**：19 种细胞类型特异性基因组特征（DNase-seq、H3K4me1/2/3、H3K9ac/me3、H3K27ac/me3、H3K36me3、H3K79me2、H4K20me1、CTCF、EZH2、POLR2A、JUND、REST、RAD21、H2AFZ、phastCons score）
- **输出**：500bp bin size（互作距离 ≤500kb）和 2kb bin size（互作距离 ≤2Mb）的全基因组接触图
- **模型架构**：三个卷积块（学习局部模式）+ 自注意力块（捕捉长程依赖，对应环状互作）
- **训练策略**：两阶段——先在基因组范围 Micro-C 数据上预训练，再在 RCMC 数据上微调
- **损失函数**：MSE + 微调阶段加入绝缘性分数（insulation scores）的 MSE + 环区域额外权重
- **数据处理**：接触图转换为 log(observed/expected)；基因组分段为 1,250 bins 的窗口（500bp: 625kb；2kb: 2.5Mb），预测时以 250-bin 步长滑动窗口，合并生成连续预测
- **反馈回路**：无显式反馈回路（非强化学习或迭代优化）
- **假设**：表观基因组特征足以预测 3D 接触图；RCMC 中可见的精细结构在基因组其他区域可由表观特征推断

**文字流程**：输入 19 种表观基因组特征 → 卷积块提取局部染色质状态模式 → 自注意力块建模长程互作依赖 → 输出 log(observed/expected) 接触图 → 后处理缩放为 observed 值 → 与实验数据比较验证

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| 卷积块（3个） | 提取局部基因组模式，如染色质状态、核小体定位 | 捕获局部表观基因组特征与 3D 结构的关联 | 输入：19 特征向量；输出：局部特征表示 | Results: 模型整体性能高（图 3C-3D） | [预期] 局部模式无法提取，模型退化为仅依赖长程特征，性能显著下降 |
| 自注意力块 | 建模长程依赖，对应环状互作 | 环涉及远端元件（可达 1Mb+），需全局上下文 | 输入：局部特征序列；输出：全局上下文增强的特征 | Results: 与 Akita 等相比能预测更精细结构（图 S11） | [预期] 无法捕捉远端互作，环预测能力大幅下降 |
| 预训练阶段 | 在全基因组 Micro-C 上学习粗粒度 3D 结构规律 | Micro-C 覆盖全基因组但分辨率有限 | 输入：19 特征；输出：Micro-C 接触图 | Results: 预训练模型可预测 2kb 尺度结构（图 S10C-D） | [预期] 无预训练则微调数据不足，过拟合严重 |
| 微调阶段 | 在 RCMC 上学习超精细结构 | RCMC 提供亚千碱基分辨率但覆盖有限 | 输入：19 特征；输出：RCMC 接触图 | Results: 微调后 500bp 预测准确（图 3B） | [预期] 无微调则无法预测 500bp 精细结构（图 S10A-B） |
| 绝缘性分数损失 | 增强微区室和边界预测 | 微区室是 RCMC 特有的精细结构 | 输入：预测接触图；输出：绝缘性分数 MSE | Methods: 微调阶段加入 | [预期] 微区室边界模糊，边界预测精度下降 |
| 环区域加权 | 增强环预测准确性 | 环是稀疏但重要的特征，需重点优化 | 输入：预测接触图；输出：环区域加权 MSE | Methods: 微调阶段加入 | [预期] 环预测精度下降，特别是弱环 |

## 09 关键公式符号
*注：原文未提供显式公式，以下基于方法描述重建核心概念。*

1. **log(observed/expected) 转换**：
   - 符号：`O(i,j)` = 观察到的接触频率；`E(i,j)` = 期望接触频率（基于距离衰减模型）
   - 公式：`M(i,j) = log(O(i,j) / E(i,j))`
   - 用途：标准化接触图，消除距离衰减效应
   - 直觉：正值表示增强互作（如环），负值表示减弱互作
   - 来源：Methods 节

2. **损失函数（微调阶段）**：
   - 符号：`L_total` = 总损失；`L_MSE` = 接触图 MSE；`L_ins` = 绝缘性分数 MSE；`λ` = 权重
   - 公式：`L_total = L_MSE + λ_ins * L_ins + λ_loop * L_loop`
   - 用途：联合优化接触图精度、微区室边界和环区域
   - 直觉：多任务学习，不同损失项引导模型关注不同结构特征
   - 来源：Methods 节（公式为 [Analysis] 重建）

3. **绝缘性分数（Insulation Score）**：
   - 符号：`I(b)` = bin b 处的绝缘性分数
   - 公式：`I(b) = mean(M(i,j))` 其中 `i < b < j` 且 `|i-b| = |j-b| = w`（窗口大小）
   - 用途：检测微区室边界（TAD-like domains）
   - 直觉：低绝缘性分数表示边界（互作被绝缘）
   - 来源：Methods 节（公式为 [Analysis] 重建）

## 10 实验设计与证据链
- **数据集**：
  - 4 个人类细胞类型：GM12878（淋巴母细胞）、HCT116（结直肠癌）、K562（慢性髓系白血病）、H1（人胚胎干细胞）
  - RCMC：14 个区域，每个 2-3Mb，平均 950 亿基因组等效 reads/区域，最深 GM12878 区域 >5000 亿
  - Micro-C：GM12878、HCT116、K562，约 50-70 亿唯一配对接触
  - 表观基因组特征：19 种（来自 ENCODE/Roadmap）
- **指标**：Pearson 相关系数（预测 vs 实验接触图）；环强度相关性；边界/微区室检测一致性
- **基线**：Akita v2、C. Origami（图 S11）；预训练模型（无微调，图 S10）
- **评测协议**：3 个 holdout 区域（区域 4、6、11）不参与微调，用于评估泛化能力
- **预算/资源**：未提供具体计算资源信息
- **Orcale 输入**：实验 RCMC 和 Micro-C 数据作为训练目标；19 种表观基因组特征作为模型输入

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| RCMC 数据质量验证 | RCMC 在 500bp/1kb bin size 下可检测精细结构 | 与 Micro-C、Hi-C 对比 | RCMC 分辨率远超 Micro-C 和 Hi-C（图 1B, S2D-G） | RCMC 提供亚千碱基分辨率 | 未直接比较所有区域 | Results 图 1, S2 |
| 边界检测 | RCMC 边界比 Micro-C 更准确 | RCMC vs Micro-C 边界调用 | RCMC 边界更少假阳性（图 S4A-D） | RCMC 边界更可靠 | 未用独立实验验证边界功能 | Results 图 S4 |
| 环检测 | RCMC 检测到更多 CRE 环 | RCMC vs Micro-C 环数 | RCMC 环数远多于 Micro-C（图 2C） | RCMC 检测 CRE 环能力更强 | 未验证所有环的功能 | Results 图 2C |
| Cleopatra 预测精度 | 模型可预测 RCMC 级分辨率 | holdout 区域预测 vs 实验 | 高 Pearson 相关（图 3C-D） | 模型泛化到未见区域 | 未在所有 14 区域验证 | Results 图 3 |
| 预训练 vs 微调 | 微调对 500bp 预测必要 | 预训练模型 vs 微调模型 | 预训练模型无法预测 500bp 精细结构（图 S10A-B） | 微调是关键步骤 | 未测试其他微调策略 | Results 图 S10 |
| 与现有模型对比 | Cleopatra 优于 Akita v2 和 C. Origami | 同区域预测对比 | Cleopatra 预测精细结构，其他模型仅粗结构（图 S11） | Cleopatra 分辨率更高 | 未系统比较所有指标 | Results 图 S11 |
| 特征消融 | CTCF 对环预测重要 | 7-input vs 无 CTCF 模型 | 无 CTCF 时性能下降（图 S13A-C） | CTCF 是环预测关键特征 | 未测试其他特征组合 | Results 图 S13 |
| 环-表达关系 | 环数与表达正相关 | 环数 vs 表达水平 | 表达随环数单调增加（图 5B） | 环与表达相关 | 因果关系未验证 | Results 图 5B |
| E-P 环与 CTCF | 多数 E-P 环由 CTCF 锚定 | CTCF 结合位点 vs E-P 环 | 约 3/4 E-P 环至少一端有 CTCF（图 5F-H） | CTCF 广泛参与 E-P 环 | 未做 CTCF 敲除验证 | Results 图 5F-H |

## 11 结论正确解读
- **任务范围**：预测 3D 接触图（而非直接预测 TF 结合或基因表达）；环和微区室为预测目标
- **Orcale/真值输入**：训练目标为实验 RCMC/Micro-C 数据；输入为 19 种表观基因组特征（非序列）
- **端到端状态**：非端到端——需要预先计算的表观基因组特征（如 ChIP-seq、DNase-seq），不能仅从序列预测
- **算力成本**：未提供具体训练成本；但预训练+微调策略暗示需要大量 GPU 资源
- **历史数据依赖**：依赖 ENCODE/Roadmap 的表观基因组数据，这些数据本身来自大量实验
- **模型依赖**：注意力架构（Transformer 类）；对 19 种输入特征的依赖（7-input 模型性能略降但可用）
- **最难情形**：其他类型细胞（非训练细胞类型）的预测未验证；罕见细胞类型因缺乏表观基因组数据而无法预测
- **群体/领域边界**：仅限人类细胞；未测试其他物种
- **不确定性**：预测的环和微区室未经过实验验证（如 3C、FISH）；"其他"（other）锚点的身份未明确
- **有边界的复述**：在 4 个人类细胞类型中，以 19 种表观基因组特征为输入，通过预训练（Micro-C）+微调（RCMC）的注意力模型，可生成 500bp/2kb bin size 的全基因组接触图，预测超过 90 万个环，其中约半数具有细胞类型特异性；预测的 E-P 环中约 3/4 至少一端有 CTCF 结合，且环数与基因表达正相关。这些预测未经实验扰动验证，且仅适用于具有表观基因组数据的细胞类型。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 训练数据需求大 | 需要大量同质细胞和深度测序 | 用更多细胞类型的 RCMC 数据扩展训练 | Discussion: "generating the Micro-C and RCMC training data requires tens of millions of homogeneous cells" |
| 特征依赖多 | 需要 19 种表观基因组特征 | 减少特征数量，7-input 模型已接近全模型性能 | Results: "7-input models perform almost as well as the full model" |
| 罕见细胞类型不可用 | 无法预测缺乏表观基因组数据的细胞类型 | 用有限特征预测罕见细胞类型 | Discussion: "ultimately allowing for in-silico prediction of ultra-high-resolution 3D genome structure even from rare cell types and tissues" |
| "其他"锚点未明确 | 约半数环的锚点未注释为已知元件 | 需要进一步表征"其他"锚点的身份 | Results: "about half of the loops have one unannotated anchor" |
| 预测未经实验验证 | 环和微区室预测未做扰动实验 | 需要 CRISPR 等实验验证 | Discussion: "perturbation experiments will be required for validation" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 19 种特征均为表观基因组修饰，无序列信息 | 模型可能无法泛化到表观基因组数据缺失的细胞类型；序列特征（如 TF motif）可能提供更直接的信息 | 若模型仅记忆表观-结构关联，则对新细胞类型预测能力有限 | 用仅含序列信息的输入训练模型，比较性能 | Methods: 输入特征列表 |
| 环数-表达正相关可能混淆因果方向 | 表达高的基因可能更活跃，导致更多环，而非环驱动表达 | 若环是表达的因，则干预环应改变表达；若为果，则相反 | 用 CRISPRi 干扰特定环，检测表达变化 | Results 图 5B |
| "其他"锚点占约半数环，但未明确其身份 | 这些锚点可能代表新的调控元件类型，也可能是注释不完整 | 若存在新元件类型，对理解 TF-DNA 互作有重要意义 | 对"其他"锚点做 motif 富集分析、ChIP-seq 交叉验证 | Results 图 2C |
| 与 Akita v2 和 C. Origami 的比较仅定性 | 未提供定量比较指标（如环检测 F1、边界匹配率） | 无法客观评估 Cleopatra 的增量优势 | 在相同 holdout 区域上计算标准指标 | Results 图 S11 |
| 预训练/微调策略的消融不完整 | 仅比较了预训练 vs 微调，未测试不同预训练数据量、微调策略 | 无法确定最优训练策略 | 系统变化预训练数据比例、微调层数 | Results 图 S10 |
| 模型预测的环未做实验验证 | 预测环可能是假阳性，特别是"其他-其他"环 | 若预测环不可靠，下游分析结论受影响 | 用 3C、FISH 或 CRISPR 验证部分预测环 | Discussion: "perturbation experiments will be required" |
| 仅 4 种细胞类型，且均为癌细胞系或永生系 | 可能不反映原代细胞或体内情况 | 若模型在正常组织中表现不同，则普适性受限 | 在原代细胞或组织样本上测试 | Results: 细胞类型列表 |

## 14 学到什么
**Agent 提炼的知识候选**

1. **预训练/微调策略（可迁移性高）**：在 TF–DNA 互作预测中，可用广泛但低分辨率的 ChIP-seq/DNase-seq 数据预训练，再用高分辨率但覆盖有限的数据（如 SNP 效应、突变体结合数据）微调，以提升全基因组预测精度。
2. **多任务损失设计**：将绝缘性分数和环区域加权纳入损失函数，可同时优化多个结构特征。在 TF–DNA 结合预测中，可类似地联合优化结合强度、结合位点边界和协同结合模式。
3. **"其他"锚点分析**：未注释的环锚点可能代表新的调控元件。在 TF–DNA 研究中，对未注释的结合位点做 motif 富集和功能分析，可能发现新的 TF 或结合模式。
4. **环数-表达单调关系**：该定量关系提示，在 TF–DNA 互作模型中，可将环数作为基因表达预测的中间特征，而非仅依赖 TF 结合强度。
5. **特征消融方法**：通过逐步减少输入特征（19→7→5→3）评估各特征贡献，可识别关键调控特征。在 TF–DNA 模型中，可类似地评估各 TF 对结合预测的贡献。
6. **注意力机制用于长程互作**：自注意力块天然适合建模 TF 结合位点之间的长程协同作用（如增强子-启动子环），可迁移到 TF 协同结合预测。
7. **数据质量评估**：通过 downsampling 实验评估数据深度对边界检测的影响（图 S4C），提示在 TF–DNA 实验中应评估测序深度对结合位点检测的影响。

## 15 与已有知识连接
- **Hi-C 与 3D 基因组**：本文建立在 Hi-C (Lieberman-Aiden et al. 2009)、Micro-C (Hsieh et al. 2015) 基础上，RCMC 为作者前期工作（Hansen lab, 2022）。与 Rao et al. (2014) 的 loop 定义和分辨率标准直接相关。
- **深度学习预测 3D 基因组**：与 Akita (Fudenberg et al. 2020)、HiC-Plus (Zhang et al. 2019)、Epiphany (Rinzema et al. 2022)、C. Origami (Fudenberg et al. 2023)、ChromaFold (2023) 等模型对比，本文首次实现 500bp bin size 全基因组预测。
- **CTCF 与环**：CTCF/cohesin 在环形成中的作用（Rao et al. 2014; Nora et al. 2017）是本文分析框架的基础；本文进一步量化了 CTCF 在 E-P 环中的参与比例。
- **增强子-启动子互作**：与 CRISPRi 验证的 E-P 对（Fulco et al. 2019; Gasperini et al. 2019）比较，验证了预测环的功能相关性。
- **TF 与 3D 结构**：本文通过 motif 富集分析提名可能调控细胞类型特异性环的 TF（如 IRF、GATA），与已知的细胞类型特异性 TF 功能（如 IRF 在 B 细胞、GATA 在造血）一致。
- **eQTL 与 3D 基因组**：使用 GTEx eQTL 数据验证预测环的功能，与 3D 基因组在疾病变异解释中的应用（如 GWAS 变异-基因映射）相关。
- **与 AlphaFold 类结构预测的关系** [Analysis]：本文预测的是染色质 3D 结构（接触图），而非蛋白质 3D 结构；但「预训练+微调」策略与 AlphaFold 的「物理先验+深度学习」思路有相似之处，可互相借鉴。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：TF–DNA 结合驱动的环预测模型（TF-LoopNet）
   - **来源局限/观察**：Cleopatra 使用表观基因组特征预测环，但未显式建模 TF 结合 motif 与环形成的关系；"其他"锚点可能由未知 TF 驱动。
   - **核心假设**：将 TF 结合 motif 扫描结果作为额外输入特征，可提高细胞类型特异性环的预测精度，特别是"其他"锚点环。
   - **初步方法**：在 Cleopatra 架构基础上，增加 TF motif 特征通道（如 JASPAR motif 扫描分数），比较有/无 motif 特征的环预测性能。
   - **验证方式**：在 GM12878/K562 的 holdout 区域比较环检测 F1；对预测的"其他"锚点做 motif 富集分析。
   - **创新状态**：unverified

2. **候选名称**：单细胞 3D 基因组预测（sc-3D）
   - **来源局限/观察**：Cleopatra 需要大量同质细胞，无法应用于稀有细胞类型；单细胞 3D 基因组数据稀疏且噪声大。
   - **核心假设**：利用单细胞表观基因组（scATAC-seq）特征，通过迁移学习可从 Cleopatra 微调出单细胞 3D 结构预测模型。
   - **初步方法**：将 Cleopatra 预训练权重迁移至单细胞数据，使用 scATAC-seq 特征预测单细胞接触图；用 scHi-C 数据验证。
   - **验证方式**：在 scHi-C 数据上比较预测接触图与实验接触图的相似性（如 HiCRep 分数）。
   - **创新状态**：unverified

3. **候选名称**：TF 协同结合与环形成的因果推断（TF-CoLoop）
   - **来源局限/观察**：Cleopatra 预测环数-表达正相关，但因果方向未定；TF 协同结合可能驱动环形成。
   - **核心假设**：特定 TF 对（如 IRF-SMAD）的协同结合是细胞类型特异性环形成的驱动因素。
   - **初步方法**：利用 Cleopatra 预测的环，对环锚点做 TF motif 对共现分析；用 CRISPR 敲除候选 TF 后检测环变化。
   - **验证方式**：比较敲除前后 Hi-C/Micro-C 环强度变化；检查预测的协同 TF 对是否在敲除后失去环。
   - **创新状态**：unverified

4. **候选名称**：序列-表观-结构端到端预测模型（Seq2Struct）
   - **来源局限/观察**：Cleopatra 依赖 19 种表观基因组特征，无法用于无实验数据的细胞类型；DNA 序列本身包含 TF 结合信息。
   - **核心假设**：仅用 DNA 序列（通过预训练语言模型如 DNABERT）即可预测表观基因组特征，进而预测 3D 结构。
   - **初步方法**：构建序列→表观特征→3D 结构的两阶段模型；第一阶段用 DNABERT 预测表观特征，第二阶段用 Cleopatra 预测结构。
   - **验证方式**：在无表观数据的细胞类型上预测结构，与实验数据（如有）比较；评估预测误差来源。
   - **创新状态**：unverified

5. **候选名称**：3D 基因组结构变异效应预测（StructVar）
   - **来源局限/观察**：Cleopatra 预测的是野生型结构；结构变异（SV）可能改变环和 TF 互作，但实验检测困难。
   - **核心假设**：将 SV 信息（如删除、倒位）编码为输入特征，可预测 SV 对 3D 结构和 E-P 环的影响。
   - **初步方法**：在 Cleopatra 输入中增加 SV 特征通道；用已知 SV 的细胞系（如癌症基因组）验证预测。
   - **验证方式**：比较预测的 SV 前后接触图变化与实验数据（如 Hi-C 在 SV 细胞系中）的一致性。
   - **创新状态**：unverified