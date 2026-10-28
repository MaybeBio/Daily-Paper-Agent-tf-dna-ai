## 01 基本信息
- **标题**: AIRE relies on Z-DNA to flag gene targets for thymic T cell tolerization
- **作者**: Fang, Yuan; Bansal, Kushagra; Mostafavi, Sara; Benoist, Christophe; Mathis, Diane
- **单位**: 哈佛医学院（Harvard Medical School）等（具体单位列表未在摘要中完整提供）
- **期刊/平台**: Nature
- **年份**: 2024-03-14
- **论文类型**: 研究论文（Research Article）
- **领域**: 免疫学 × 基因调控 × 深度学习
- **关键词**: AIRE, Z-DNA, 胸腺T细胞耐受, 转录调控, CNN, 非B型DNA
- **DOI/arXiv 号**: 10.1038/s41586-024-07169-7
- **代码**: 未提供
- **数据**: GEO SuperSeries GSE224557（含ATAC-seq、BLISS、ChIP-seq、ChIPmentation、CUT&Tag、bulk RNA-seq、scRNA-seq等子数据集）
- **阅读日期**: 2024-12-01（假设）
- **在课题方向中的位置**: 本文聚焦转录因子AIRE（一种特殊的TF）如何通过识别Z-DNA（非B型DNA构象）来选择靶基因，属于「TF–DNA结合机制 × 深度学习（CNN）」交叉方向。其核心贡献在于揭示TF并非仅通过经典基序识别靶标，而是通过DNA结构特征（Z-DNA）实现靶标选择，为TF–DNA互作研究提供了「结构基序」新维度，并展示了CNN+可解释性分析在发现非经典调控元件中的方法论价值。

## 02 一句话总结
本文通过CNN模型结合梯度解释分析，发现AIRE（一种调控胸腺T细胞耐受的转录因子）的靶基因选择依赖于启动子区域的Z-DNA形成序列（(CA)n重复），并通过体内实验（精胺处理增强Z-DNA、BLISS检测DNA双链断裂）验证了Z-DNA通过促进DNA双链断裂（DSB）和启动子poising来协助AIRE识别低表达靶基因的机制。

## 03 研究问题
- **具体问题**: AIRE（自身免疫调节因子）如何从数千个基因中选择其靶基因？其靶标选择的顺式调控逻辑是什么？
- **为什么重要**: AIRE是胸腺髓质上皮细胞（mTEC）中驱动组织特异性抗原（TRA）异位表达的关键转录因子，对建立免疫耐受至关重要。理解其靶标选择机制对自身免疫病发病机制和治疗有直接意义。
- **现有方法为何不足**: 此前研究（包括作者前期工作）发现AIRE倾向于结合弱表达基因的启动子，但未找到明确的DNA序列基序（经典TF结合基序富集分析失败），说明AIRE的靶标选择可能不依赖经典基序，而是依赖某种结构特征。
- **精确的"Can..."问题**: Can a deep learning model trained on promoter sequences identify the cis-regulatory features (beyond canonical TF motifs) that determine AIRE's target gene specificity?

## 04 背景与发展脉络
*（标注：以下脉络为「经外部核验」+「仅本文框架」混合，具体标注于各阶段）*

1. **AIRE功能研究阶段**（~2000-2015）：AIRE被鉴定为胸腺T细胞耐受的关键调控因子，通过驱动mTEC中组织特异性抗原的表达来教育T细胞。代表性工作包括AIRE敲除小鼠模型、AIRE靶基因的鉴定。局限：靶标选择机制不明。
2. **AIRE靶标特征描述阶段**（~2015-2020）：多项研究（包括作者前期工作）发现AIRE优先结合弱表达基因的启动子，且与转录延伸、RNA Pol II暂停释放相关。局限：未找到决定性序列特征。
3. **深度学习应用于顺式调控元件发现**（~2018-至今）：以Basenji、Enformer等为代表的CNN模型成功从DNA序列预测功能基因组学数据，并可通过梯度解释识别关键序列特征。局限：多数应用于通用调控元件，未聚焦特定TF的靶标选择。
4. **非B型DNA（Z-DNA）功能研究**（~2010-至今）：Z-DNA（左手螺旋DNA）在转录调控中的作用逐渐被认识，但缺乏系统性的全基因组功能证据。
5. **本文位置**：将深度学习（CNN+可解释性）与Z-DNA结构生物学结合，首次提出AIRE通过Z-DNA（而非经典基序）选择靶基因的模型，并提供了多组学验证（ChIP-seq、BLISS、ATAC-seq、RNA-seq、scRNA-seq）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 经典基序分析失败 | 简单基序富集分析无法区分AIRE诱导与AIRE中性基因的启动子 | AIRE靶标选择不依赖经典TF结合基序，而依赖结构特征（Z-DNA） | Extended Data Fig. 2c：简单基序富集无法识别(CA)n和Nfe2•Maf基序 |
| AIRE靶标选择逻辑不明 | AIRE结合数千个基因，但缺乏统一解释 | 靶标选择由Z-DNA形成潜力+弱表达状态共同决定 | 图1g,h：Z-DNA基序长度与AIRE靶标概率正相关，距离TSS近者更有效 |
| 弱表达基因的识别机制 | AIRE优先上调低表达基因，但机制不清 | Z-DNA在低表达基因启动子处形成，通过DSB和启动子poising标记这些基因 | 图4c-e：BLISS信号与启动子可及性、Pol II暂停正相关 |
| 非B型DNA的功能验证困难 | Z-DNA在体内难以直接检测和操纵 | 使用Z-DNA稳定剂（精胺）和TOP1抑制剂（拓扑替康）间接验证 | 图3d, 5a-c：精胺处理增强AIRE靶基因表达；拓扑替康增强AIRE结合 |

## 06 核心思想
1. **表面方法**：构建CNN模型（基于Basenji架构）区分AIRE诱导与AIRE中性基因的启动子序列，通过梯度×输入（Gradient×Input）计算贡献分数，提取高贡献区域进行基序分析，发现(CA)n重复和Nfe2•Maf基序；随后通过F1杂交小鼠（B6×NOD）利用自然遗传变异验证因果性；最后通过药理学操纵（精胺、拓扑替康）和多种测序技术（BLISS、ChIP-seq、ATAC-seq、CUT&Tag）验证机制。
2. **核心洞察**：AIRE的靶标选择不依赖经典TF基序，而是通过Z-DNA（一种非B型DNA构象）来"标记"靶基因。Z-DNA形成序列（(CA)n重复）在弱表达基因启动子处富集，通过促进DSB生成和启动子poising，为AIRE的招募创造有利的染色质环境。AIRE本身可能不直接结合Z-DNA，而是通过识别Z-DNA介导的染色质状态（DSB、开放染色质、Pol II暂停）来选择靶标。
3. **可能的普适教训** [Analysis]：TF的靶标选择可能比"基序匹配"更复杂，DNA结构特征（非B型DNA）和染色质状态（DSB、poising）可能构成一种"结构密码"，与经典基序协同或独立决定TF的特异性。深度学习方法（CNN+可解释性）能够发现这类非经典特征，但需要多组学验证才能确立因果性。

## 07 方法总览
- **输入**：DNA序列（±1024 bp 围绕TSS，来自B6小鼠基因组）
- **输出**：二分类预测（AIRE诱导 vs AIRE中性基因）
- **模块**：
  1. 预训练CNN主干（Basenji架构，在ENCODE/小鼠功能基因组数据上预训练）
  2. 微调分类头（二分类）
  3. 梯度解释模块（Gradient×Input）
  4. 基序分析模块（MEME套件）
  5. F1杂交等位基因分析模块
  6. 药理学验证模块（精胺、拓扑替康）
- **训练**：预训练（多任务，预测1643个功能基因组学readout）→ 微调（二分类）
- **工具**：TensorFlow（v1.14.0预训练，v2.3.0微调）、MEME套件（XSTREME、STREME、FIMO）、HOMER、DESeq2、Seurat等
- **反馈回路**：CNN预测 → 梯度解释 → 基序发现 → F1验证 → 药理学验证 → 机制模型
- **文字流程**：从B6基因组提取AIRE诱导/中性基因启动子序列 → CNN预训练+微调 → 计算每个核苷酸的贡献分数 → 提取高贡献区域 → 基序发现（(CA)n和Nfe2•Maf）→ 在F1杂交中验证等位基因效应 → 精胺/拓扑替康处理验证Z-DNA功能 → BLISS/ChIP-seq/ATAC-seq/CUT&Tag验证DSB、AIRE结合、染色质状态 → 提出Z-DNA介导的靶标选择模型

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN预训练主干 | 学习通用顺式调控序列特征 | 小样本微调需要预训练知识迁移 | 输入：2048bp DNA序列；输出：1643个功能readout预测 | Methods "CNN model pre-train" | 预期：模型泛化能力下降，微调效果变差 [预期效应] |
| 微调分类头 | 区分AIRE诱导/中性基因 | 目标任务特异性分类 | 输入：预训练特征；输出：二分类概率 | Methods "CNN model fine-tune" | 预期：无法完成AIRE靶标预测 [预期效应] |
| 梯度×输入解释 | 定位对预测贡献最大的序列区域 | 识别关键调控元件 | 输入：模型+序列；输出：每个核苷酸的贡献分数 | Methods "CNN model interpretation" | 预期：无法发现(CA)n和Nfe2•Maf基序 [预期效应] |
| 基序分析（XSTREME） | 从高贡献区域发现富集基序 | 将黑盒模型转化为可解释的序列特征 | 输入：高贡献序列；输出：富集基序 | 图1a；Extended Data Fig. 2a | 预期：无法识别Z-DNA相关特征 [预期效应] |
| F1杂交等位基因分析 | 利用自然遗传变异验证因果性 | 区分相关性与因果性 | 输入：B6×NOD F1 RNA-seq/ATAC-seq/BLISS；输出：等位基因偏向 | 图2a-d；Extended Data Fig. 3-4 | 预期：无法确认(CA)n和Nfe2•Maf的因果作用 [预期效应] |
| 药理学验证（精胺/拓扑替康） | 操纵Z-DNA/DSB水平验证功能 | 直接检验Z-DNA的因果作用 | 输入：药物处理小鼠；输出：RNA-seq/BLISS/ChIP-seq变化 | 图3d, 5a-c；Extended Data Fig. 5-6 | 预期：无法建立Z-DNA→DSB→AIRE靶标的因果链 [预期效应] |
| 多组学整合分析 | 验证机制模型 | 提供多角度证据 | 输入：ATAC-seq、BLISS、ChIP-seq、CUT&Tag、RNA-seq、scRNA-seq | 图3-5；Extended Data Fig. 7-10 | 预期：机制模型缺乏完整性 [预期效应] |

## 09 关键公式符号
1. **Gradient×Input贡献分数**：
   - 公式：\( S_i = x_i \cdot \frac{\partial f(x)}{\partial x_i} \)
   - 符号：\( x_i \) = 第i个核苷酸的one-hot编码值；\( f(x) \) = 模型输出（AIRE诱导概率）；\( S_i \) = 第i个核苷酸的贡献分数
   - 用途：定位对预测贡献最大的序列位置
   - 来源：Methods "CNN model interpretation"

2. **ISM分数**：
   - 公式：\( \text{ISM}_i = \log_2 \frac{P_0}{1-P_0} - \log_2 \frac{P_1}{1-P_1} \)
   - 符号：\( P_0 \) = 原始序列的预测概率；\( P_1 \) = 第i个核苷酸突变后的预测概率
   - 用途：评估每个核苷酸对预测的影响
   - 来源：Methods "CNN model interpretation"

3. **Beta-binomial检验**（用于等位基因不平衡）：
   - 公式：\( x_i \sim \text{BetaBin}(n_i, p_i, \theta_i) \)
   - 符号：\( x_i \) = 区域i中来自参考/替代基因组的reads数；\( n_i \) = 总reads数；\( p_i \) = 来自参考基因组的概率（零假设为0.5）；\( \theta_i \) = 过度离散参数
   - 用途：识别等位基因特异性表达/可及性/DSB
   - 来源：Methods "Statistical testing of allelic imbalance"

## 10 实验设计与证据链
**数据集/群体**：
- 训练/测试：B6小鼠基因组中AIRE诱导基因（n=3231）和AIRE中性基因（n=3121）的启动子序列
- F1杂交：B6×NOD（n=3-4只/组）和B6×CAST（n=3-4只/组）mTEC
- 药理学处理：精胺（7天，15mg/kg IP）、拓扑替康（3天，0.5mg/kg IP）
- 测序类型：RNA-seq（bulk和single-cell）、ATAC-seq、BLISS、ChIP-seq（AIRE、Pol II、Z-DNA）、ChIPmentation（NELF）、CUT&Tag（Pol II-S5P）

**指标**：
- CNN分类准确率（AUC）
- 等位基因不平衡（beta-binomial检验p值）
- DSB信号强度（BLISS）
- 基因表达变化（RNA-seq fold-change）

**关键实验**：
| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| CNN训练+解释 | AIRE靶标选择可由序列特征预测 | AIRE诱导 vs 中性基因启动子 | 模型可区分；高贡献区域富集(CA)n和Nfe2•Maf基序 | 序列特征（Z-DNA潜力）决定AIRE靶标选择 | 不能证明Z-DNA是唯一决定因素 | 图1a-c |
| F1等位基因分析 | (CA)n和Nfe2•Maf基序变异影响AIRE靶标 | B6 vs NOD等位基因 | 等位基因偏向与基序强度相关 | 基序变异因果性影响AIRE靶标 | 不能排除连锁不平衡 | 图2a-d |
| 精胺处理 | 增强Z-DNA可促进AIRE靶标表达 | 精胺 vs PBS处理Aire-KO小鼠 | 部分AIRE诱导基因表达恢复 | Z-DNA形成是AIRE靶标表达的必要条件 | 精胺可能有脱靶效应 | 图3d |
| 拓扑替康处理 | 增强DSB可促进AIRE结合 | 拓扑替康 vs DMSO处理Aire-WT小鼠 | AIRE结合增加，靶基因表达上调 | DSB促进AIRE招募 | 不能区分DSB直接vs间接效应 | 图5a-c |
| Z-DNA ChIP-seq | AIRE结合位点富集Z-DNA | AIRE结合位点 vs 非结合位点 | Z-DNA信号在AIRE结合位点富集 | Z-DNA与AIRE结合共定位 | 不能证明直接物理互作 | 图3b-c |
| Nfe2l2敲除 | Nfe2l2影响AIRE靶标表达 | Nfe2l2-KO vs WT mTEC | AIRE靶基因表达下降 | Nfe2l2是AIRE靶标表达的正调控因子 | 效应温和，可能有冗余 | Extended Data Fig. 9h |

## 11 结论正确解读
- **任务范围**：本文研究的是AIRE在mTEC中的靶标选择机制，不涉及AIRE在其他细胞类型或条件下的功能。
- **Oracle/真值输入**：CNN训练使用了已发表的AIRE诱导/中性基因列表（基于AIRE敲除前后的RNA-seq差异），这些列表本身可能不完整或有噪声。
- **端到端状态**：从序列到表型的完整链条（Z-DNA→DSB→启动子poising→AIRE结合→基因表达）已通过多组学验证，但每个环节的因果关系强度不同：Z-DNA→DSB的证据最强（精胺/拓扑替康+BLISS），DSB→AIRE结合的机制细节（如何招募）仍不完全清楚。
- **算力成本**：CNN预训练需要GPU（2×V100），但微调和解释计算成本较低。
- **历史数据依赖**：依赖已发表的AIRE靶基因列表和ENCODE功能基因组数据，这些数据的质量影响模型训练。
- **模型依赖**：CNN架构基于Basenji，不同架构可能发现不同特征；梯度解释方法（Gradient×Input）有已知局限性（如梯度饱和）。
- **最难情形**：低表达基因的启动子信号弱，模型区分度有限；Z-DNA预测的准确性依赖于Z-DNA形成潜力的计算模型。
- **群体/领域边界**：研究在小鼠中进行，人类AIRE（以及AIRE突变导致的APECED综合征）是否采用相同机制尚未验证。
- **有边界的复述**：在小鼠mTEC中，AIRE的靶标选择部分依赖于启动子区域的Z-DNA形成序列（(CA)n重复），Z-DNA通过促进DSB和启动子poising为AIRE招募创造有利条件，但AIRE本身可能不直接结合Z-DNA，且该机制不能完全解释所有AIRE靶标选择。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| Z-DNA检测的间接性 | 使用Z-DNA ChIP-seq（Z22抗体）检测Z-DNA，但Z22同时识别Z-RNA | 未明确提及 | Methods "ChIP-seq library preparation" |
| 精胺的脱靶效应 | 精胺除稳定Z-DNA外可能影响其他细胞过程 | 未明确提及 | 图3d相关讨论 |
| Nfe2l2的冗余性 | Nfe2l2敲除对AIRE靶标表达影响温和，可能存在家族成员冗余 | 未明确提及 | Extended Data Fig. 9h相关讨论 |
| 物种局限性 | 研究仅在小鼠中进行 | 未明确提及 | 全文 |
| CNN解释的近似性 | 梯度×输入方法只能近似识别关键序列特征 | 未明确提及 | Methods "CNN model interpretation" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| Z-DNA ChIP-seq使用Z22抗体 | Z22抗体同时识别Z-RNA，可能高估Z-DNA信号；ChIP-seq的Z-DNA信号可能来自交叉反应 | Z-DNA是核心机制，检测准确性直接影响结论 | 使用Z-DNA特异性探针或Zα结构域进行独立验证；RNA酶处理排除Z-RNA贡献 | Methods "ChIP-seq library preparation" |
| CNN发现的(CA)n重复可能只是与Z-DNA形成相关的代理特征 | (CA)n重复可能通过其他机制（如核小体定位、TF结合位点）影响AIRE靶标选择 | 区分直接机制与代理特征 | 在(CA)n重复中引入Z-DNA破坏突变（如CG替换）但保持长度不变，检测AIRE结合变化 | 图1f-h相关分析 |
| F1等位基因分析中基序强度与等位基因偏向的相关性可能受连锁不平衡影响 | 与(CA)n重复连锁的其他变异可能才是因果变异 | 因果变异定位需要精细定位 | 使用CRISPR在等位基因中精确编辑(CA)n长度，检测等位基因偏向变化 | 图2a-d |
| 精胺和拓扑替康的效应可能通过Z-DNA非依赖途径 | 精胺影响多胺代谢，拓扑替康抑制TOP1可能影响全局转录 | 药物处理的特异性需要验证 | 使用Z-DNA形成缺陷的突变小鼠（如Z-DNA基序敲除）进行遗传验证 | 图3d, 5a-c |
| CNN模型仅在B6基因组上训练，可能无法泛化到其他品系 | 不同品系的Z-DNA基序分布可能不同 | 泛化性影响结论的普适性 | 在NOD、CAST等品系上测试模型性能 | Methods "CNN model fine-tune" |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **非经典TF靶标选择机制**：TF（如AIRE）可能通过识别DNA结构特征（Z-DNA）而非经典基序来选择靶基因。迁移到本课题：在研究TF–DNA互作时，不应仅扫描经典基序，还应考虑非B型DNA（Z-DNA、G4等）的贡献。
2. **CNN+可解释性发现新调控特征**：预训练CNN（Basenji架构）+梯度解释（Gradient×Input）能够从序列中提取非经典调控特征。迁移到本课题：可构建类似流程，对任意TF的靶基因启动子进行建模，发现新的结合特征。
3. **F1杂交等位基因分析验证因果性**：利用自然遗传变异（B6×NOD）验证序列特征与表型（表达、可及性、DSB）的因果关系。迁移到本课题：在TF–DNA互作研究中，可用F1杂交策略区分等位基因特异性结合与反式效应。
4. **多组学三角验证**：将深度学习预测与ChIP-seq、ATAC-seq、BLISS、RNA-seq等多组学数据结合，构建从序列特征到功能表型的完整证据链。迁移到本课题：AI预测的TF结合位点应通过多组学实验验证，而非仅依赖计算预测。
5. **Z-DNA与DSB的调控功能**：Z-DNA形成序列通过促进DSB和启动子poising参与转录调控。迁移到本课题：在MD模拟或结构预测中，可考虑非B型DNA构象对TF结合的贡献，而非仅模拟B型DNA。
6. **弱表达基因的调控逻辑**：AIRE优先靶向弱表达基因，Z-DNA可能作为一种"可诱导性"标记。迁移到本课题：TF对低表达靶基因的选择可能依赖染色质状态而非基序强度，这对预测TF结合位点的算法设计有启示。

## 15 与已有知识连接
- **Basenji架构**：本文CNN主干基于Basenji（Kelley et al., PNAS 2018），该模型已成功用于预测DNA序列的调控功能。本文展示了其在新任务（TF靶标分类）中的迁移能力。
- **Z-DNA研究**：Z-DNA的调控功能已有报道（如Rich & Zhang, Nat Rev Genet 2003），但本文首次将Z-DNA与AIRE功能直接联系，并提供了全基因组证据。
- **AIRE研究**：AIRE的靶标选择机制此前被认为与染色质状态（H3K4me0）和转录延伸相关（如Giraud et al., J Exp Med 2012），本文补充了Z-DNA这一新维度。
- **深度学习可解释性**：Gradient×Input方法（Shrikumar et al., 2017）和ISM方法（Finder et al., 2018）是深度学习解释的常用工具，本文展示了其在调控基因组学中的应用。
- **非B型DNA与疾病**：Z-DNA形成序列与基因组不稳定性和疾病相关（如Herbert, J Cell Biochem 2019），本文提示Z-DNA可能通过DSB机制参与免疫调控，与肿瘤免疫和自身免疫病有潜在联系。
- **候选方向** [Analysis]：本文的Z-DNA机制可能与其他TF（如p53、MYC等）的靶标选择相关，值得在其他系统中验证；Z-DNA预测模型（如Z-DNABERT）可进一步整合到TF结合位点预测流程中。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**: Z-DNA基序在人类AIRE靶基因中的保守性分析
   - **来源局限/观察**: 本文在小鼠中发现了Z-DNA对AIRE靶标选择的作用，但人类AIRE（APECED相关）是否采用相同机制未知。
   - **核心假设**: 人类AIRE靶基因启动子同样富集Z-DNA形成序列，且Z-DNA基序强度与AIRE结合水平正相关。
   - **初步方法**: 使用Z-DNABERT对人类mTEC AIRE ChIP-seq数据（如来自GTEx或ENCODE）进行Z-DNA评分，比较AIRE结合位点与非结合位点的Z-DNA潜力；使用CNN模型（本文架构）在人类基因组上训练并测试。
   - **验证方式**: 统计检验Z-DNA评分差异；CRISPR在人类细胞系中编辑Z-DNA基序验证AIRE结合变化。
   - **创新状态**: unverified

2. **候选名称**: Z-DNA介导的DSB在TF靶标选择中的普适性研究
   - **来源局限/观察**: 本文提出Z-DNA通过DSB促进AIRE靶标选择，但该机制是否适用于其他TF未知。
   - **核心假设**: 多种TF（特别是与DNA损伤修复相关的TF）的靶标选择部分依赖于Z-DNA介导的DSB。
   - **初步方法**: 对多个TF的ChIP-seq数据（ENCODE）进行Z-DNA评分和DSB信号（如BLISS或END-seq）关联分析；使用拓扑替康处理检测TF结合变化。
   - **验证方式**: 统计关联分析；药物处理实验验证因果关系。
   - **创新状态**: unverified

3. **候选名称**: 基于深度学习的Z-DNA形成序列预测模型改进
   - **来源局限/观察**: 本文使用Z-DNABERT预测Z-DNA形成，但该模型可能未充分捕捉Z-DNA形成的序列上下文依赖。
   - **核心假设**: 结合CNN（序列特征）和结构预测（如AlphaFold3或MD模拟）的混合模型能更准确预测Z-DNA形成。
   - **初步方法**: 构建多模态模型，输入DNA序列和预测的DNA结构特征，在Z-DNA ChIP-seq数据上训练。
   - **验证方式**: 与Z-DNABERT比较AUC；在独立数据集上验证。
   - **创新状态**: unverified

4. **候选名称**: Z-DNA基序与TF结合基序的协同作用模型
   - **来源局限/观察**: 本文发现Z-DNA和Nfe2•Maf基序共同预测AIRE靶标，但两者如何协同未知。
   - **核心假设**: Z-DNA通过改变DNA构象增强邻近TF结合基序的可及性，形成"结构-序列"协同调控模块。
   - **初步方法**: 对AIRE靶基因启动子进行Z-DNA和TF基序的共定位分析；使用MD模拟比较Z-DNA形成前后的TF结合自由能。
   - **验证方式**: 统计共定位富集；MD模拟结果与实验结合数据对比。
   - **创新状态**: unverified

5. **候选名称**: 精胺作为Z-DNA增强剂在自身免疫病治疗中的潜力
   - **来源局限/观察**: 本文发现精胺可增强Z-DNA形成并部分恢复AIRE功能，提示其可能对AIRE功能缺陷相关疾病有治疗价值。
   - **核心假设**: 精胺处理可增强AIRE靶基因表达，改善胸腺耐受建立，减轻自身免疫症状。
   - **初步方法**: 在AIRE缺陷小鼠模型中给予精胺处理，检测AIRE靶基因表达、Treg生成和自身免疫表型。
   - **验证方式**: 表型改善的统计检验；机制验证（Z-DNA水平、AIRE结合）。
   - **创新状态**: unverified