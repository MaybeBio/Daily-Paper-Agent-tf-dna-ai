## 01 基本信息
- **标题**：Epigenomic landscapes during prefrontal cortex development and aging in rhesus
- **作者与单位**：Ning, Chao; Wu, Xi; Zhao, Xudong; Lu, Zongyang; Yao, Xuelong; Zhou, Tao; Yi, Lizhi; Sun, Yaoyu; Wu, Shuaishuai; Liu, Zhenbo; Huang, Xingxu; Gao, Lei; Liu, Jiang（单位未在摘要中提供，正文提及中国科学院动物研究所、昆明动物研究所、北京基因组研究所等）
- **期刊/预印本平台**：National Science Review
- **年份**：2024-08-26
- **论文类型**：研究论文（多组学图谱 + 功能验证）
- **领域**：表观基因组学、神经发育与衰老、非人灵长类
- **关键词**：prefrontal cortex, epigenomics, development, aging, rhesus, Hi-C, ChIP-seq, DNase-seq, DNA methylation, super enhancer, bivalent promoter
- **DOI/arXiv 号**：10.1093/nsr/nwae213
- **代码**：https://github.com/ningchaozky/rheMac8paper.git
- **数据**：国家基因组科学数据中心（GSA）CRA011791 / PRJCA018217
- **阅读日期**：未提供
- **在「蛋白质-DNA互作(聚焦TF–DNA结合机制) × AI/物理模拟」方向中的位置**：本文不直接开发AI或物理模拟方法，但提供了猕猴PFC发育与衰老过程中TF–DNA结合的表观基因组基础数据（ChIP-seq、DNase-seq、Hi-C、DNA甲基化、RNA-seq），并识别了bRG发育相关的TF（GLI3、CREB5、SOX9等）及cis-regulatory module。对本课题方向的价值在于：提供TF–DNA互作的时空动态参考数据集、TF motif富集分析流程、以及可用于训练/验证TF–DNA结合预测模型的非人灵长类脑发育表观基因组资源。

## 02 一句话总结
本文通过整合Hi-C、DNase-seq、ChIP-seq（H3K4me3、H3K27ac、H3K27me3、Pol2、CTCF）、DNA甲基化和RNA-seq数据，绘制了猕猴PFC从胚胎到衰老的表观基因组图谱，发现出生前后表观信号剧烈重编程、bivalent promoter预配置神经分化与分层基因、super enhancer富集精神疾病风险SNP，并鉴定出调控bRG发育的cis-element module及候选TF（GLI3、CREB5、SOX9等）。

## 03 研究问题
- **具体问题**：猕猴PFC从胚胎发育到衰老过程中，表观遗传景观（染色质高级结构、染色质可及性、组蛋白修饰、DNA甲基化）如何动态变化？这些变化如何与阶段特异性基因表达、神经发育事件（如bRG增殖、神经元迁移、分层、突触形成）及衰老相关基因表达异常相关联？
- **为什么重要**：PFC是高级认知功能的核心脑区，其发育与衰老的失调与多种神经精神疾病（如精神分裂症、阿尔茨海默病）密切相关。猕猴作为与人类进化关系密切的模式动物，其PFC表观基因组图谱可为理解人类脑发育与疾病提供关键参考。
- **现有方法为何不足**：此前缺乏跨越多发育阶段（胚胎到老年）的非人灵长类PFC多维表观基因组数据；多数研究集中于转录组层面，缺乏染色质高级结构、组蛋白修饰与cis-regulatory element的系统整合。
- **精确的「Can ... ?」研究问题**：Can integrated epigenomic profiling across prenatal-to-aging stages in rhesus PFC reveal stage-specific cis-regulatory modules and transcription factors that govern neurodevelopment and aging-related gene dysregulation?

## 04 背景与发展脉络
- **阶段一：脑发育转录组图谱**。代表性工作如人类和小鼠脑发育的转录组研究（如Miller et al. 2014; Bakken et al. 2016），揭示了发育阶段特异性基因表达，但缺乏表观调控层面的解释。
- **阶段二：单细胞转录组与表观组**。单细胞RNA-seq和ATAC-seq揭示了脑细胞异质性和细胞类型特异的调控状态，但难以覆盖全生命周期且缺乏多组学整合。
- **阶段三：非人灵长类多组学脑图谱**。近年来恒河猴脑发育的转录组（如Bakken et al. 2021）和表观组研究逐步出现，但多聚焦于单一组学或有限阶段。
- **本文主张的位置**：首次系统整合5种表观组学（Hi-C、DNase-seq、ChIP-seq×5、DNA甲基化、RNA-seq）覆盖猕猴PFC 7个发育阶段（E50至PY20），构建跨生命周期的cis-regulatory landscape，并连接至神经发育事件、疾病风险位点与衰老。
- **脉络核验说明**：以上脉络为「仅本文框架」——基于本文引言与结果叙述整理，未逐一核验外部文献。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 缺乏跨生命周期的非人灵长类PFC表观基因组数据 | 已有研究多聚焦单一阶段或单一组学 | 样本采集困难、多组学成本高 | 引言：rhesus PFC表观基因组图谱此前未见系统报道 |
| 表观信号与基因表达的关系在发育中不明确 | 阶段特异性表观信号与表达信号高度一致，但机制不清 | 作者未深入解释因果方向 | Results 图1b：表观信号与表达信号一致 |
| 出生前后表观重编程的幅度与功能意义未知 | 表观信号在P0至P4M变化最剧烈，但基因表达变化不大 | 作者推测表观信号先于表达变化，起预配置作用 | Results 图1j：表观动态率在出生前后最高，表达动态率最低 |
| bivalent promoter在脑发育中的功能不明确 | 78.5%基因在E50/E90具bivalent标记，但功能未知 | 作者通过BTA基因分析揭示其预配置分化与分层基因 | Results 图3a–d |
| super enhancer与神经精神疾病的关系缺乏非人灵长类证据 | SCZ风险SNP在SE中富集，但机制不清 | 作者推测SE调控神经网络建立相关基因 | Results 图4d–f |
| 衰老相关表观变化与疾病关联缺乏系统描述 | 衰老期出现TAD分裂、长距离互作减少、转座子激活 | 作者认为表观失稳是衰老的重要特征 | Results 图6a–f |

## 06 核心思想
1. **表面方法**：对猕猴PFC 7个发育阶段（E50、E90、E120、P0、P4M、PY4.5、PY20）进行多组学测序（Hi-C、DNase-seq、ChIP-seq、WGBS、RNA-seq），系统分析染色质状态、cis-regulatory element、TF motif富集、bivalent promoter、super enhancer的动态变化，并结合人类疾病GWAS数据进行功能关联分析，最后用类脑器官CRISPR敲除验证候选cis-regulatory element功能。
2. **核心洞察**：表观遗传信号在出生前后发生剧烈重编程，但基因表达变化滞后——表观信号先于表达建立，起「预配置」作用。bivalent promoter预配置神经分化与分层基因，super enhancer在神经网络建立阶段富集精神疾病风险SNP。衰老期以染色质互作缩短、TAD分裂、转座子激活为特征。
3. **可能的普适教训 [Analysis]**：表观基因组重编程与转录组变化在时间上解耦——表观信号的变化可能先于基因表达变化，提示在研究发育调控时需同时追踪表观状态与表达状态，而非仅关注表达。这一「表观预配置」概念可迁移至TF–DNA结合研究：TF结合位点的表观状态（如bivalent chromatin）可能在TF表达之前就已建立，为后续TF结合和基因激活做准备。

## 07 方法总览
- **输入**：猕猴PFC组织样本（7个发育阶段，每阶段2个生物学重复），人类疾病GWAS数据，人类基因组比对数据。
- **输出**：表观基因组图谱（染色质状态、A/B compartment、TAD、cis-regulatory element、bivalent promoter、super enhancer）、阶段特异性调控模块、候选TF、疾病关联分析结果、类脑器官功能验证数据。
- **模块**：
  1. 多组学数据生成：Hi-C、DNase-seq、ChIP-seq（H3K4me3、H3K27ac、H3K27me3、Pol2、CTCF）、WGBS、RNA-seq。
  2. 染色质状态注释：整合组蛋白修饰与CTCF信号，定义活性/抑制/增强子/启动子状态。
  3. 3D基因组分析：A/B compartment、TAD鉴定与动态比较（TADCompare）。
  4. cis-regulatory element鉴定：整合H3K27ac、DNase-seq、Hi-C loop、CTCF。
  5. TF motif富集分析：在阶段特异性cis-element module中富集TF结合motif。
  6. 疾病关联分析：精神分裂症、双相情感障碍、AD等GWAS SNP在SE中的富集分析。
  7. 功能验证：CRISPR/Cas9敲除DBN1增强子，评估类脑器官表型。
- **训练**：不涉及传统机器学习训练；使用统计方法（富集分析、相关分析、WGCNA）。
- **反馈回路**：无显式反馈回路。
- **假设**：表观信号变化先于基因表达变化；SE在神经网络建立中起关键作用；衰老期表观失稳导致基因表达异常。
- **文字流程**：样本采集 → 多组学测序 → 数据质控与比对 → 表观信号定量 → 染色质状态注释 → A/B compartment与TAD分析 → cis-regulatory element鉴定 → 阶段特异性模块识别（WGCNA）→ TF motif富集 → 疾病GWAS关联 → 候选增强子功能验证（类脑器官）→ 整合解释。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 多组学数据生成 | 获取表观与转录信息 | 多维度解析调控机制 | 输入：PFC组织；输出：Hi-C、DNase-seq、ChIP-seq、WGBS、RNA-seq数据 | Methods节；数据质控见Fig. S1 | 无法进行后续分析 |
| 染色质状态注释 | 定义基因组功能状态 | 区分启动子/增强子/抑制状态 | 输入：组蛋白修饰+CTCF；输出：染色质状态注释 | Results 图1b；Methods节 | 无法识别cis-regulatory element |
| A/B compartment与TAD分析 | 解析3D基因组结构 | 理解长距离调控 | 输入：Hi-C；输出：compartment、TAD、动态TAD边界 | Results 图1c–e；Fig. S3–S4 | 无法关联结构变异与表达 |
| cis-regulatory element鉴定 | 定位候选调控元件 | 连接表观与表达 | 输入：H3K27ac、DNase、Hi-C loop、CTCF；输出：推定增强子/启动子 | Results 图4a；Methods节 | 无法进行TF motif与疾病分析 |
| WGCNA模块分析 | 识别共调控cis-element模块 | 发现协同调控的调控元件 | 输入：cis-element活性与基因表达；输出：5个模块 | Results 图2a–c；Fig. S7 | 无法识别bRG/aRG特异性模块 |
| TF motif富集 | 预测调控模块的关键TF | 识别候选调控因子 | 输入：模块cis-element序列；输出：富集TF motif | Results 图2e；Fig. S8d | 无法提出TF–DNA结合候选 |
| 疾病GWAS关联 | 连接表观调控与疾病风险 | 解释疾病遗传风险机制 | 输入：SE、GWAS SNP；输出：富集分析结果 | Results 图4d–f | 无法建立表观-疾病关联 |
| 类脑器官功能验证 | 验证候选增强子功能 | 因果验证 | 输入：DBN1增强子敲除类脑器官；输出：表型与基因表达变化 | Results 图5e–j | 无法确认调控元件的功能重要性 |

**消融效应说明**：本文未进行系统性消融实验；类脑器官敲除实验仅验证了DBN1增强子，其他模块的移除效应为「预期效应」[Analysis]。

## 09 关键公式符号
本文为描述性多组学图谱研究，未使用核心数学模型或公式。涉及的主要统计方法包括：
- **Pearson相关系数**：用于评估生物学重复间相关性（Fig. S1a–b）。
- **富集分析**：超几何检验或Fisher精确检验用于评估SNP在SE中的富集（Results 图4d–f）。
- **WGCNA**：加权基因共表达网络分析，使用软阈值幂律（soft-thresholding power）构建网络，公式为 `a_ij = |cor(x_i, x_j)|^β`，其中β为软阈值。
- **TADCompare**：用于比较相邻阶段TAD差异的统计方法（Methods节）。
- **GAS（gene active signal）**：整合H3K4me3、H3K27ac、Pol2、Dnase信号减去H3K27me3信号，公式为 `GAS = (H3K4me3 + H3K27ac + Pol2 + Dnase) - H3K27me3`（Supplementary Methods）。

## 10 实验设计与证据链
- **数据集**：猕猴PFC 7个发育阶段（E50、E90、E120、P0、P4M、PY4.5、PY20），每阶段2个生物学重复；共70个ChIP-seq、14个DNase-seq、14个Hi-C、14个WGBS、14个RNA-seq数据集。
- **指标**：染色质状态、A/B compartment转换、TAD边界动态、cis-element活性、基因表达、TF motif富集、SNP富集、类脑器官大小与基因表达。
- **基线**：相邻发育阶段比较；PY4.5 vs PY20作为衰老比较。
- **类脑器官验证**：H9人胚胎干细胞，DBN1增强子敲除（CRISPR/Cas9），与野生型对照比较。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| 表观信号聚类 | 样本按发育阶段聚类 | 7个阶段，2重复 | 样本按阶段聚类，重复间高相关（r=0.76–0.99） | 表观信号具有阶段特异性 | 不能证明阶段特异性表观信号驱动阶段特异性表达 | Fig. S1a–b |
| 表观信号动态分析 | 表观信号在出生前后变化最剧烈 | 相邻阶段比较 | 表观信号变化率在P0–P4M最高 | 出生前后是表观重编程关键期 | 不能证明表观变化先于表达变化 | Fig. 1j |
| A/B compartment转换 | 发育过程中存在compartment转换 | 相邻阶段比较 | 3480个基因位于转换区，表达动态 | compartment转换与表达变化相关 | 不能证明因果关系 | Fig. 1c；Table S4 |
| TAD边界动态 | TAD边界在发育中动态变化 | TADCompare | 12%边界动态；ARHGAP11A边界移位伴随表达下降 | TAD边界变化与基因调控相关 | 单个案例，不能推广 | Fig. 1e；Fig. S4 |
| bivalent promoter分析 | bivalent promoter预配置分化基因 | E50–PY20 | 78.5%基因在E50/E90具bivalent标记；BTA基因富集分化与分层功能 | bivalent promoter预配置神经分化 | 未直接验证bivalent→active转换的因果性 | Fig. 3a–d |
| SE与疾病SNP关联 | SE富集精神疾病风险SNP | SCZ、BD、AD、Crohn's | SCZ SNP在SE中富集（OR=2.89, P=0.0243） | SE参与神经网络建立相关疾病 | 相关性非因果；样本量有限 | Fig. 4d–f |
| DBN1增强子敲除 | 该增强子调控DBN1表达与神经发育 | 类脑器官，敲除vs对照 | 敲除后类脑器官变小，DBN1表达下降，突触减少 | 该增强子对神经发育至关重要 | 仅验证一个增强子，不能推广至所有SE | Fig. 5e–j |

## 11 结论正确解读
- **任务范围**：本文是描述性多组学图谱研究，覆盖猕猴PFC从胚胎（E50）到老年（PY20）的7个时间点，不涉及干预性实验（除类脑器官验证）。
- **oracle/真值输入**：无监督学习或人工注释的染色质状态；类脑器官实验使用野生型作为对照。
- **端到端状态**：非端到端；各分析模块独立进行，最后整合解释。
- **算力成本**：未提供。
- **历史数据依赖**：依赖已发表的猕猴和人类基因组注释、GWAS数据、人类脑发育转录组数据。
- **模型依赖**：依赖WGCNA、TADCompare等统计工具的参数选择。
- **最难情形**：衰老期（PY20）样本量有限（仅1个时间点），无法刻画衰老的动态过程；bivalent→active转换的因果机制未直接验证。
- **群体/领域边界**：结论基于猕猴PFC，外推至人类需谨慎；类脑器官验证仅针对一个增强子。
- **不确定性**：作者未提供置信区间或效应量；部分结论基于相关性分析。
- **有边界的复述**：在猕猴PFC中，表观遗传信号在出生前后发生最剧烈的重编程，bivalent promoter预配置神经分化与分层基因，SE在神经网络建立阶段富集精神疾病风险SNP，衰老期以染色质互作缩短和转座子激活为特征；DBN1增强子对类脑器官神经发育至关重要。这些结论限于猕猴PFC，且主要基于相关性分析。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 无法解释细胞异质性 | 使用bulk测序，无法区分细胞类型特异的表观变化 | 采用单细胞测序技术研究不同神经细胞类型的表观动态 | Discussion 末段 |
| 样本量有限 | 每阶段仅2个生物学重复，衰老期仅1个时间点 | 增加样本量和时间点 | Methods 节 |
| 因果关系未验证 | 表观变化与表达变化的相关性不等于因果性 | 未来需功能实验验证 | Discussion |
| 类脑器官验证有限 | 仅验证一个增强子（DBN1） | 需更多功能验证 | Discussion |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 表观信号变化先于表达变化的结论基于相关性 | 表观信号与表达信号在时间上可能同时变化，或表达变化驱动表观变化 | 若「表观预配置」概念不成立，则bivalent promoter的功能解释需修正 | 使用时间序列因果推断方法（如Granger因果检验）或药物干预实验 | Fig. 1j |
| SE中SCZ SNP富集分析未校正连锁不平衡 | 富集结果可能受LD结构影响 | 影响疾病关联结论的可靠性 | 使用LD校正的富集方法（如LDSC） | Fig. 4d–f |
| 类脑器官敲除实验仅验证一个增强子 | 单个案例不能推广至所有SE | 影响SE功能重要性的普适性结论 | 验证多个SE敲除 | Fig. 5e–j |
| WGCNA模块分析依赖参数选择 | 不同软阈值可能产生不同模块 | 影响bRG/aRG模块的稳定性 | 进行参数敏感性分析 | Methods 节 |
| 未提供效应量和置信区间 | 无法评估效应大小和统计功效 | 影响结论的定量解释 | 补充效应量和CI | 全文 |
| 衰老期仅1个时间点 | 无法区分年龄相关变化与个体差异 | 影响衰老结论的可靠性 | 增加多个老年时间点 | Fig. 1a |

## 14 学到什么
**Agent 提炼的知识候选**
1. **表观预配置概念**：表观信号（如bivalent promoter、H3K27ac增强子）可能在基因表达变化之前建立，为后续转录激活做准备。可迁移至TF–DNA结合研究：TF结合位点的染色质状态（如bivalent chromatin）可能在TF表达前已建立，预测TF结合时机。
2. **多组学整合策略**：整合Hi-C、ChIP-seq、DNase-seq、甲基化、RNA-seq可系统解析cis-regulatory landscape。可迁移至TF–DNA结合研究：结合3D基因组（Hi-C）与TF ChIP-seq可识别远程TF–enhancer–promoter互作。
3. **TF motif富集流程**：在阶段特异性cis-regulatory module中富集TF motif，结合TF表达筛选候选调控因子。可迁移至TF–DNA结合研究：从表观基因组数据中预测特定发育阶段的活跃TF。
4. **bivalent promoter分析框架**：同时标记H3K4me3和H3K27me3的启动子预配置分化基因。可迁移至TF–DNA结合研究：bivalent状态可能影响TF的可及性和结合动力学。
5. **SE与疾病风险关联**：SE富集疾病风险SNP，提示SE在疾病易感性中的角色。可迁移至TF–DNA结合研究：疾病风险SNP可能通过影响TF结合位点（motif破坏/创建）发挥作用。
6. **类脑器官功能验证**：CRISPR/Cas9敲除候选增强子，评估神经发育表型。可迁移至TF–DNA结合研究：敲除TF结合位点验证TF–DNA互作的功能重要性。
7. **衰老相关表观失稳**：衰老期TAD分裂、长距离互作减少、转座子激活。可迁移至TF–DNA结合研究：衰老可能改变TF结合位点的可及性和3D互作，影响TF–DNA结合动力学。

## 15 与已有知识连接
- **相似工作**：与人类脑发育表观基因组研究（如Won et al. 2016, Science; de la Torre-Ubieta et al. 2018, Neuron）方法类似，但本文聚焦猕猴并覆盖衰老期。
- **TF–DNA结合机制**：本文识别的bRG相关TF（GLI3、CREB5、SOX9）已有文献支持其在神经发育中的作用（如GLI3在SHH信号通路中调控bRG增殖，Wang et al. 2016）。本文提供了这些TF结合位点的表观基因组背景。
- **3D基因组与TF结合**：本文Hi-C数据可连接至CTCF介导的TAD边界与TF结合位点的关系，与CTCF在3D基因组组织中的已知功能（Phillips-Cremins et al. 2013）一致。
- **疾病风险SNP与TF结合**：SCZ风险SNP在SE中富集，与「风险SNP影响TF结合」的假说一致（如ENCODE项目eQTL研究）。
- **可迁移方向**：本文的表观基因组数据可作为TF–DNA结合预测模型的训练/验证集；bivalent promoter和SE注释可用于特征工程；TF motif富集流程可迁移至其他物种或细胞类型。

## 16 研究想法
**Agent 生成的研究候选**

1. **名称**：基于猕猴PFC表观基因组的TF–DNA结合预测模型
   - **来源局限/观察**：本文提供了丰富的表观基因组数据，但未开发计算模型预测TF–DNA结合。
   - **核心假设**：整合染色质可及性（DNase）、组蛋白修饰（H3K27ac、H3K4me3、H3K27me3）、3D基因组（Hi-C loop）和TF motif可显著提高TF–DNA结合预测精度。
   - **初步方法**：使用深度学习（如CNN或Transformer）整合多组学特征，以本文的ChIP-seq TF结合位点为标签，训练TF–DNA结合预测模型。
   - **验证方式**：交叉验证AUC；在独立数据集（如人类PFC）上测试跨物种泛化。
   - **创新状态**：unverified

2. **名称**：bivalent promoter状态转换的TF–DNA结合动力学模拟
   - **来源局限/观察**：本文发现bivalent promoter在发育中转换为活性或抑制状态，但未研究TF结合在此转换中的角色。
   - **核心假设**：bivalent promoter的H3K4me3/H3K27me3比例变化影响TF的可及性和结合动力学，特定TF（如GLI3、SOX9）在bivalent→active转换中起关键作用。
   - **初步方法**：使用分子动力学（MD）模拟TF与bivalent chromatin（含H3K4me3/H3K27me3修饰的核小体）的结合自由能变化；结合本文的时序数据构建TF–DNA结合动态模型。
   - **验证方式**：MD模拟预测的结合亲和力变化与本文观察到的基因表达时序比较。
   - **创新状态**：unverified

3. **名称**：衰老相关TAD边界重排对TF–enhancer–promoter互作的影响
   - **来源局限/观察**：本文发现衰老期TAD分裂和长距离互作减少，但未深入分析其对TF介导的增强子-启动子互作的影响。
   - **核心假设**：衰老期TAD边界重排导致TF结合位点与增强子的空间邻近性改变，影响TF–DNA互作效率和基因表达。
   - **初步方法**：整合本文Hi-C数据与TF ChIP-seq，使用Hi-C loop和TAD边界信息构建TF–enhancer–promoter互作网络，比较PY4.5与PY20的差异。
   - **验证方式**：差异互作网络与差异表达基因的富集分析；与人类衰老脑数据比较。
   - **创新状态**：unverified

4. **名称**：基于TF motif的bRG/aRG命运决定调控网络建模
   - **来源局限/观察**：本文识别了bRG和aRG特异的cis-regulatory module及候选TF，但未构建调控网络。
   - **核心假设**：bRG和aRG的命运决定由一组TF（GLI3、CREB5、SOX9 vs ZNF423、TEAD2、TCF7L1）的协同结合调控。
   - **初步方法**：使用本文的cis-element模块和TF motif富集结果，构建TF–cis-element–基因调控网络，使用布尔网络或常微分方程建模。
   - **验证方式**：网络预测的bRG/aRG标记基因与文献比较；类器官实验验证。
   - **创新状态**：unverified

5. **名称**：跨物种TF–DNA结合保守性分析（猕猴 vs 人类 vs 小鼠）
   - **来源局限/观察**：本文发现bRG相关cis-element module在猕猴中富集年轻基因，但未进行跨物种比较。
   - **核心假设**：bRG相关TF结合位点在猕猴和人类中保守，但在小鼠中差异显著，这解释了物种间脑尺寸差异。
   - **初步方法**：将本文的猕猴cis-element与人类和小鼠同源区域比对，分析TF motif保守性和染色质状态差异。
   - **验证方式**：保守性得分与基因功能富集分析；与已知的物种差异基因比较。
   - **创新状态**：unverified