## 01 基本信息
- **标题**: The developmental and evolutionary characteristics of transcription factor binding site clustered regions based on an explainable machine learning model
- **作者与单位**: Ouyang Zhangyi, Liu Feng, Li Wanying, Wang Junting, Chen Bijia, Zheng Yang, Li Yaru, Tao Huan, Xu Xiang, Li Cheng, Cong Yuwen, Li Hao, Bo Xiaochen, Chen Hebing（单位未在提供材料中列出）
- **期刊/预印本平台**: Nucleic Acids Research
- **年份**: 2024-05-30
- **论文类型**: 研究论文（Research Article）
- **领域**: 计算基因组学；转录调控；进化生物学；机器学习可解释性
- **关键词**: TFBS clustered regions (TFCRs)；embryonic development；cross-species comparison；RegulatoryScore；explainable machine learning；SHAP
- **DOI/arXiv 号**: 10.1093/nar/gkae441
- **代码**: https://doi.org/10.5281/zenodo.11149753（TFCR 识别代码及结果）
- **数据**: 公开数据（GEO: GSE101571, GSE66581, GSE66582, DRP004498, GSE143658, GSE52415, GSE101779, GSE106428, GSM1289382, GSE106431, GSE106450, GSE89608, GSE113240, GSE145619, GSE143288, GSE130871, E-MTAB-2633）
- **阅读日期**: 未提供
- **在该课题方向中的位置**: 本文属于「蛋白质-DNA互作（TF–DNA结合机制）× AI方法」交叉方向，聚焦于TFBS在基因组上的聚集区域（TFCRs）的发育动态与跨物种进化特征。其核心贡献在于：(1) 提出RegulatoryScore量化TFCR复杂度与基因表达的同步性；(2) 用可解释机器学习（CatBoost + SHAP）识别影响调控能力的关键特征，发现TFCR-启动子距离是最重要因素。对TF–DNA结合机制研究而言，本文提供了从TFBS聚集模式出发、结合可解释AI推断调控逻辑的范式，而非直接研究TF-DNA结合的物理化学机制。

## 02 一句话总结
本文通过跨物种（人、鼠、牛、鸡、斑马鱼、青鳉）胚胎发育期的ATAC-seq数据识别TFBS聚集区域（TFCRs），定义RegulatoryScore量化TFCR复杂度与基因表达的同步性，并用可解释机器学习模型（CatBoost + SHAP）发现TFCR与启动子之间的距离是预测RegulatoryScore的最重要特征，且距离越近调控越强。

## 03 研究问题
- **具体问题**: TFBS在基因组上呈聚集分布（TFCRs），但不同物种、不同胚胎发育阶段中TFCRs的分布如何变化？TFCR复杂度与基因表达之间的同步性（RegulatoryScore）受哪些因素调控？这些因素在物种间和发育阶段间是否一致？
- **为什么重要**: TF–DNA互作是转录调控的核心。TFBS聚集区域（类似增强子簇/Super-enhancers）被认为与基因表达的协同调控有关，但其发育动态和进化模式尚不清楚。理解TFCRs如何进化、如何与基因表达耦合，有助于揭示表型多样性的调控基础。
- **现有方法不足**: 以往研究多聚焦单一物种（尤其是人类）的增强子簇或Super-enhancers，缺乏跨物种、跨发育阶段的系统比较；且对TFCR调控基因表达的贡献因素缺乏定量、可解释的建模。
- **精确的「Can ... ?」问题**: Can an explainable machine learning model identify the key genomic features (e.g., TFCR-promoter distance) that determine the synchronization between TFCR complexity and gene expression across species and developmental stages?

## 04 背景与发展脉络
*注：以下脉络基于本文引用与论述，标注为「仅本文框架」；未逐一核验外部文献。*

1. **TFBS聚集现象的发现与描述**（仅本文框架）: 早期研究观察到TFBS在真核基因组中非均匀分布，呈聚集特征（引用13-16）。代表性方法为基于密度估计的聚类识别。
2. **增强子簇/Super-enhancers的识别**（仅本文框架）: 后续研究开发了从染色质可及性（ATAC-seq）或组蛋白修饰（H3K27ac）数据中识别增强子簇的方法（引用17-18），发现其与细胞身份和疾病相关。局限：多集中于人类，缺乏跨物种比较。
3. **跨物种调控元件比较**（仅本文框架）: 已有研究比较了哺乳动物间候选CREs的进化保守性（引用4），但未系统覆盖鱼类、鸟类等。
4. **机器学习在调控基因组学中的应用**（仅本文框架）: 多种ML方法（SVR、RF、XGBoost等）被用于预测基因表达或调控元件活性，但多为黑箱模型，缺乏可解释性分析。
5. **本文主张的位置**: 在上述脉络中，本文首次将TFCRs识别扩展到6个物种的多个胚胎发育阶段，提出RegulatoryScore作为跨物种可比的调控同步性指标，并用可解释ML（CatBoost + SHAP）揭示TFCR-启动子距离的核心作用，填补了跨物种发育调控比较与可解释建模的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| TFBS分布不均，难以系统比较 | TFBS在基因组上聚集程度不同，直接比较困难 | TFBS密度受序列组成、染色质状态等多因素影响 | Results 图1D-E；Supplementary Figure S5 |
| 跨物种发育阶段难以对齐 | 不同物种胚胎发育时间不同，难以直接比较同一发育事件 | 发育速率和时序存在物种差异 | Methods「Dataset collection」节：选择相对相似的发育阶段 |
| 缺乏量化TFCR调控能力的指标 | 已有方法多关注TFCR识别，未量化其与基因表达的关系 | 缺乏统一的跨物种可比指标 | Results「RegulatoryScore」节 |
| 机器学习模型可解释性不足 | 黑箱模型难以揭示生物学机制 | 复杂模型（如深度学习）的决策过程不透明 | Results「Explainable machine learning」节；Discussion |
| 测序深度差异可能引入偏差 | 不同物种/样本的ATAC-seq深度不同，影响TFCR识别 | 深度不足可能漏检低信号区域 | Supplementary Figure S3, S4（通过下采样评估稳健性） |

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| TFBS分布不均，难以系统比较 | TFBS在基因组上聚集程度不同，直接比较困难 | TFBS密度受序列组成、染色质状态等多因素影响 | Results 图1D-E；Supplementary Figure S5 |
| 跨物种发育阶段难以对齐 | 不同物种胚胎发育时间不同，难以直接比较同一发育事件 | 发育速率和时序存在物种差异 | Methods「Dataset collection」节：选择相对相似的发育阶段 |
| 缺乏量化TFCR调控能力的指标 | 已有方法多关注TFCR识别，未量化其与基因表达的关系 | 缺乏统一的跨物种可比指标 | Results「RegulatoryScore」节 |
| 机器学习模型可解释性不足 | 黑箱模型难以揭示生物学机制 | 复杂模型（如深度学习）的决策过程不透明 | Results「Explainable machine learning」节；Discussion |
| 测序深度差异可能引入偏差 | 不同物种/样本的ATAC-seq深度不同，影响TFCR识别 | 深度不足可能漏检低信号区域 | Supplementary Figure S3, S4（通过下采样评估稳健性） |

## 06 核心思想
1. **表面方法**: 收集6个物种（人、鼠、牛、鸡、斑马鱼、青鳉）多个胚胎发育阶段的ATAC-seq数据 → 用FIMO扫描TFBS → 高斯核密度估计识别TFCRs → 定义RegulatoryScore量化TFCR复杂度与基因表达同步性 → 用11种ML模型预测RegulatoryScore → 用SHAP解释特征重要性。
2. **核心洞察**: TFCR与启动子之间的距离是预测RegulatoryScore的最重要特征，且呈负相关——距离越近，TFCR对基因表达的调控同步性越强。这一规律在6个物种、所有发育阶段中一致，提示距离是跨物种保守的调控组织原则。此外，人类胚胎干细胞中高RegulatoryScore基因富集于神经发育通路，提示人类特异的调控模式。
3. **可能的普适教训** [Analysis]: 在调控基因组学中，空间距离（线性基因组上的邻近性）可能是比序列特征更稳健、更跨物种可比的调控指标。可解释ML（如SHAP）不仅能预测，还能揭示生物学上可检验的排序性假设（如距离的负贡献），这比单纯追求预测精度更有科学价值。

## 07 方法总览
- **输入**: 6个物种的ATAC-seq peak文件（BED格式）及对应RNA-seq表达数据；参考基因组（hg19, mm10, bosTau9, galGal5, danRer10, oryLat2等）；CIS-BP TF motif库
- **输出**: 每个物种/发育阶段的TFCRs（基因组坐标+复杂度）；每个基因的RegulatoryScore；ML模型预测值及SHAP特征重要性
- **主要模块**:
  1. TFBS识别: FIMO扫描开放染色质区域，P-value阈值1e-5
  2. TFCR识别: 高斯核密度估计（带宽300bp），密度峰视为TFCR
  3. TFCR复杂度计算: 基于贡献TFBS的数量和邻近度
  4. RegulatoryScore计算: 将TFCR复杂度和基因表达各分10组，计算两者组别的同步性（公式见Methods）
  5. ML预测: 11种方法（CatBoost, SVR, MLP, KNN, DT, RF, AdaBoost, GBDT, XGBoost, LightGBM, CNN），输入特征包括启动子序列（one-hot）、TFCR序列（one-hot）、TFCR-启动子距离
  6. 可解释性: Tree SHAP计算特征贡献
- **训练**: 每个物种/阶段单独训练（共37个模型）；另构建跨物种pooled模型（每物种30,000样本，共180,000样本）训练CatBoost
- **反馈回路**: 无显式闭环优化；ML模型用于预测和解释，而非迭代改进TFCR识别
- **假设**: (1) ATAC-seq可及性反映TF结合潜力；(2) TFBS在开放染色质内的聚集（TFCR）具有调控意义；(3) 最近基因的启动子为TFCR的调控靶标

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TFBS识别（FIMO） | 在开放染色质区域扫描TF motif | 确定TF潜在结合位点 | 输入: ATAC-seq peak序列 + CIS-BP motifs；输出: TFBS坐标 | Methods「Identification of TFCRs」节 | 移除后无法定义TFCR；预期TFCR数量大幅减少 [预期效应] |
| TFCR识别（高斯核密度估计） | 将邻近TFBS聚集成簇 | TFBS单独作用弱，聚集才有调控意义 | 输入: TFBS坐标；输出: TFCRs（密度峰） | Methods；Results 图1C | 移除后无法研究聚集效应；预期丢失调控协同信息 [预期效应] |
| TFCR复杂度计算 | 量化TFCR内TFBS的数量和邻近度 | 复杂度反映调控潜力 | 输入: TFCR内TFBS；输出: 复杂度值 | Methods「Identification of TFCRs」节 | 移除后无法计算RegulatoryScore [预期效应] |
| RegulatoryScore | 量化TFCR复杂度与基因表达的同步性 | 提供跨物种可比的调控指标 | 输入: TFCR复杂度 + 基因表达；输出: 0-1分数 | Methods「Synchronization assessment」节；Results 图4 | 移除后无法进行跨物种比较 [预期效应] |
| ML预测（11种方法） | 基于序列和距离特征预测RegulatoryScore | 识别影响调控能力的关键因素 | 输入: 启动子序列、TFCR序列、距离；输出: 预测RegulatoryScore | Results 图5；Supplementary Figure S16 | 移除后无法进行特征重要性分析 [预期效应] |
| SHAP解释 | 量化每个特征对预测的贡献 | 揭示模型决策的生物学依据 | 输入: CatBoost模型+样本；输出: SHAP值 | Results 图6；Methods「Tree SHAP」节 | 移除后无法识别距离为最重要特征 [实测效应：作者通过SHAP得出核心结论] |

## 09 关键公式符号
**RegulatoryScore公式**（Methods「Synchronization assessment」节）:

$$\text{RegulatoryScore} = 1 - \frac{1}{N} \sum_{i=1}^{N} \frac{|G_{\text{TFCR},i} - G_{\text{expr},i}|}{9}$$

- $G_{\text{TFCR},i}$: 第i个基因关联TFCR的复杂度分组编号（1-10，从低到高）
- $G_{\text{expr},i}$: 第i个基因的表达量分组编号（1-10，从低到高）
- $N$: 基因总数
- 分数范围0-1，越高表示TFCR复杂度与基因表达越同步

**高斯核密度估计**（Methods「Identification of TFCRs」节，引用17,35）:
$$\hat{f}(x) = \frac{1}{n h} \sum_{i=1}^{n} K\left(\frac{x - x_i}{h}\right)$$
- $K$: 高斯核函数
- $h$: 带宽（300 bp）
- $x_i$: TFBS位置
- 密度峰定义为TFCR

## 10 实验设计与证据链
- **数据集**: 6个物种（人、鼠、牛、鸡、斑马鱼、青鳉）的ATAC-seq和RNA-seq数据，来自已发表研究（GSE101571, GSE66581, GSE66582, DRP004498, GSE143658, GSE101779, GSE106428等）；每个物种1-14个发育阶段
- **规模**: 人、鼠各约50,000个TFCRs（图1D）；跨物种pooled训练集180,000样本
- **指标**: Pearson r, Spearman R, R², MAE, RMSE（ML预测）；RegulatoryScore（同步性）
- **基线**: 11种ML方法互比（CatBoost最优）；随机shuffled TFBS作为对照（Supplementary Figure S2, S6）
- **评测协议**: 每个物种/阶段80%训练/20%测试；pooled模型用各物种独立测试集评估

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| TFCRs基因组分布 | 人类TFCRs更富集于启动子 | 6物种比较 | 人37%位于启动子，鼠、牛、鸡、鱼较低 | 人类偏好近端调控 | 未证明因果性 | Results 图1E |
| ZGA期TFCR动态 | ZGA期大量新TFCR出现 | 相邻发育阶段比较 | ZGA期gained TFCRs达70-80% | ZGA伴随大规模调控重编程 | 未区分因果与伴随 | Results 图2A |
| 稳定TFCR特征 | 稳定TFCRs复杂度更高、更近启动子 | 稳定vs动态TFCRs | 稳定TFCRs复杂度显著更高，启动子比例更高 | 稳定TFCRs可能维持核心调控 | 未直接验证功能 | Results 图2B |
| RegulatoryScore跨物种聚类 | RegulatoryScore反映物种进化关系 | 6物种聚类分析 | 聚类大致符合物种树 | RegulatoryScore具有进化信号 | 聚类受样本量影响 | Results 图4C |
| ML预测性能 | 序列+距离可预测RegulatoryScore | 11种方法对比 | CatBoost最优（r≈0.7-0.8） | 特征可预测调控同步性 | 未达到完美预测 | Results 图5B；Supplementary Figure S16 |
| SHAP特征重要性 | 距离是最重要特征 | 所有特征排名 | 距离排名第一，负贡献 | 距离是调控同步性的关键决定因素 | 相关性非因果 | Results 图6A-B |
| 距离-发育阶段交互 | 距离重要性在早期胚胎更高 | 不同阶段SHAP值比较 | 早期（ZGA前）距离重要性更高 | 早期调控更依赖近端元件 | 样本量有限 | Results 图6C |

## 11 结论正确解读
- **任务范围**: 本文结论限于TFCRs（TFBS聚集区域）与基因表达的统计关联，不涉及TF-DNA结合的物理化学机制（如结合亲和力、构象变化）。
- **oracle/真值输入**: RegulatoryScore基于TFCR复杂度和基因表达的分组同步性，是作者定义的代理指标，非实验验证的调控强度。
- **端到端状态**: 非端到端。TFCR识别依赖FIMO motif扫描（阈值1e-5），可能漏检非经典motif结合；ML预测基于序列和距离特征，未包含染色质三维结构、TF浓度等。
- **算力成本**: 未报告具体算力需求；11种ML方法+37个阶段模型+1个pooled模型，计算量中等。
- **历史数据依赖**: 依赖已发表的ATAC-seq/RNA-seq数据，不同实验室的文库制备和测序深度可能引入批次效应（作者通过下采样评估部分缓解）。
- **模型依赖**: 结论（距离最重要）基于CatBoost+SHAP，不同ML框架或特征编码可能改变特征排名。
- **最难情形**: 鸡和青鳉的TFCRs分布与其他物种差异较大（图1D），可能反映技术差异或真实生物学差异，作者未深入解析。
- **群体/领域边界**: 结论适用于所分析的6个物种的胚胎发育阶段，不能外推至成体组织或其他物种。
- **不确定性**: 未报告置信区间或统计检验的效应量；SHAP值仅反映模型内的特征贡献，非因果效应。
- **有边界的复述**: 在6个脊椎动物物种的胚胎发育过程中，TFCRs的复杂度与基因表达的同步性（RegulatoryScore）可被序列特征和距离特征预测，其中TFCR-启动子距离是最重要的预测因子，且距离越近同步性越高；该规律在物种间保守，但在人类胚胎干细胞中高RegulatoryScore基因特异富集于神经发育通路。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 发育阶段难以精确对齐 | 不同物种胚胎发育时间不同，选择相似阶段但非精确对应 | 未明确提及 | Methods「Dataset collection」节 |
| 鸡的调控模式与其他物种差异大 | 鸡的TFCRs分布和RegulatoryScore聚类均偏离 | 未明确提及 | Results 图1D, 4C |
| 未纳入三维基因组信息 | 仅用线性距离，未考虑染色质空间邻近性 | 未来可结合Hi-C数据 | Discussion |
| 机器学习模型为统计关联 | SHAP揭示的是模型内特征贡献，非因果机制 | 需实验验证 | Discussion |
| 物种覆盖有限 | 仅6个物种，缺乏两栖类、爬行类等 | 未明确提及 | 未提供 |

**作者提及的相关约束**（非正式局限）: 作者在Discussion中提到，由于胚胎取样困难，跨物种Hi-C数据稀缺，限制了三维基因组层面的分析；此外，TFCRs与Super-enhancers的关系需进一步阐明。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| RegulatoryScore基于最近基因关联 | TFCR可能调控非最近基因（如三维空间邻近） | 若关联错误，同步性度量有偏 | 用Hi-C数据验证TFCR-基因空间互作 | Methods「Synchronization assessment」节 |
| FIMO阈值1e-5可能过严 | 漏检低亲和力但功能重要的TFBS | 可能低估TFCR复杂度 | 用更宽松阈值或ChIP-seq验证 | Methods「Identification of TFCRs」节 |
| 距离作为最重要特征可能反映技术偏差 | ATAC-seq片段长度、peak calling偏好可能影响距离分布 | 若为技术假象，生物学结论不成立 | 用不同peak caller、不同片段长度重复分析 | Supplementary Figure S1 |
| 鸡的异常未深入解释 | 可能是真实生物学差异（鸟类调控模式不同）或数据质量问题 | 影响跨物种结论的普适性 | 增加鸟类物种、检查数据质量 | Results 图1D, 4C |
| SHAP重要性未与因果推断结合 | 距离可能只是其他未测量变量（如染色质状态）的代理 | 无法确定距离本身是否因果 | 用CRISPR干扰或报告基因实验操纵距离 | Results 图6 |
| 未报告模型预测的误差分解 | 无法判断预测误差主要来自特征不足还是标签噪声 | 影响对特征重要性的信心 | 进行误差成分分析 | Results 图5B |
| 跨物种pooled模型可能掩盖物种特异模式 | 平均效应可能不适用于特定物种 | 物种特异调控机制可能被忽略 | 比较pooled vs 物种特异模型 | Methods「pooled training set」节 |

## 14 学到什么
**Agent 提炼的知识候选**:

1. **TFCR识别流程可迁移**: 高斯核密度估计（带宽300bp）识别TFBS聚集区域的方法，可直接迁移到本课题中分析TF结合模式的空间分布。若研究特定TF的DNA结合机制，可用该流程识别该TF结合位点的聚集区域，并分析其与靶基因表达的关系。

2. **RegulatoryScore作为跨物种可比指标**: 将TFCR复杂度与基因表达分组后计算同步性的思路，可迁移到本课题中量化TF-DNA结合强度与下游转录输出的耦合程度。例如，对ChIP-seq + RNA-seq数据，可定义类似指标评估TF结合强度与靶基因表达的同步性。

3. **可解释ML（CatBoost + SHAP）用于特征归因**: 本文展示了如何用SHAP从序列和距离特征中识别关键调控因素。本课题可借鉴此思路，在TF-DNA结合预测模型中引入SHAP分析，识别决定结合特异性的关键序列特征（如motif位置、侧翼序列组成），而非仅追求预测精度。

4. **距离作为调控组织原则**: 本文发现TFCR-启动子距离是跨物种保守的调控因素。本课题可进一步探索：在三维基因组中，TF结合位点与启动子的空间距离（而非线性距离）是否同样重要？这为整合Hi-C数据提供了假设。

5. **跨物种比较揭示保守与特异调控模式**: 本文通过6物种比较发现人类神经发育基因的调控特异性。本课题可借鉴此设计，比较不同物种中同一TF的结合谱（binding profiles），区分保守结合位点与物种特异结合位点，进而推断调控演化的机制。

6. **ZGA期调控重编程的量化方法**: 本文用gained/lost TFCRs比例量化ZGA期的调控变化。本课题可迁移此方法，分析特定TF在发育转变期的结合位点动态变化，识别关键调控转换事件。

## 15 与已有知识连接
- **Super-enhancers/增强子簇**: 本文TFCRs与Super-enhancers概念高度相关（Discussion中提及）。Hnisz et al. (2013) 的Super-enhancer定义基于增强子密度，本文TFCRs基于TFBS密度，两者互补。本课题可比较TFCRs与Super-enhancers在TF结合机制上的异同。
- **CIS-BP数据库**: 本文使用CIS-BP motif库（Weirauch et al., 2014），该数据库覆盖多物种TF motif，适合跨物种比较。本课题若研究特定TF家族，可优先使用CIS-BP中对应物种的motif。
- **可解释AI在基因组学中的应用**: 本文使用SHAP（Lundberg & Lee, 2017），与DeepSEA（Zhou & Troyanskaya, 2015）、Basenji（Kelley et al., 2018）等深度学习模型的解释性分析互补。本课题可结合序列深度模型与SHAP，识别TF结合的关键序列特征。
- **跨物种调控进化**: 本文与Villar et al. (2015) 的跨物种增强子比较研究互补。Villar等关注增强子活性进化，本文关注TFBS聚集模式进化。本课题可整合两者，分析TF结合位点聚集与增强子活性的协同进化。
- **ZGA与调控重编程**: 本文ZGA期TFCR动态与Lee et al. (2014) 的斑马鱼ZGA染色质研究相关。本课题可结合这些数据，深入分析ZGA期TF结合机制的变化。
- **三维基因组与调控**: 本文在Discussion中提及Hi-C数据缺乏的限制，与Dixon et al. (2012) 的TAD研究、Rao et al. (2014) 的Hi-C图谱相关。本课题可探索TFCRs在TAD边界和染色质环锚点的富集情况。

## 16 研究想法
**Agent 生成的研究候选**:

1. **候选名称**: TFCR-启动子距离的因果性检验
   - **来源局限/观察**: 本文发现距离与RegulatoryScore负相关，但为相关性证据
   - **核心假设**: 缩短TFCR-启动子距离本身可增强TF对靶基因的调控（因果效应）
   - **初步方法**: 利用CRISPR-Cas9在细胞系中删除或插入TFCR与启动子之间的序列，改变线性距离；用报告基因或内源基因表达检测调控变化；同时用Hi-C检测三维距离是否改变
   - **验证方式**: 距离改变后表达变化的剂量-反应关系；与SHAP预测值对比
   - **创新状态**: unverified

2. **候选名称**: 三维基因组距离对RegulatoryScore的增量预测
   - **来源局限/观察**: 本文仅用线性距离，未考虑三维空间邻近性
   - **核心假设**: 加入Hi-C衍生的空间距离特征可显著提升RegulatoryScore预测性能，且空间距离可能比线性距离更重要
   - **初步方法**: 在本文CatBoost框架中加入Hi-C contact frequency作为特征；比较线性距离vs空间距离的SHAP重要性；在人类和小鼠ESC数据上验证
   - **验证方式**: 预测性能（r, R²）提升；SHAP重要性排序变化
   - **创新状态**: unverified

3. **候选名称**: 单TF水平的TFCR-启动子距离效应
   - **来源局限/观察**: 本文TFCRs为多TF聚集，未区分单个TF的结合模式
   - **核心假设**: 不同TF对距离的敏感性不同，某些TF（如先锋因子）可在远距离发挥作用，而另一些TF需要近距离
   - **初步方法**: 对每个TF的ChIP-seq数据单独识别结合簇，计算其与启动子的距离及对靶基因表达的影响；比较不同TF的距离-表达关系曲线
   - **验证方式**: 不同TF的距离敏感性差异是否与已知的先锋因子/settler因子分类一致
   - **创新状态**: unverified

4. **候选名称**: 基于深度学习的TFCR调控潜力预测
   - **来源局限/观察**: 本文使用CatBoost+手工特征（序列one-hot+距离），未利用深度序列模型
   - **核心假设**: 端到端深度模型（如CNN/Transformer）可从原始序列中学习比手工特征更强的TFCR调控潜力表征
   - **初步方法**: 用本文的RegulatoryScore作为标签，训练序列深度模型（如Basenji架构）预测TFCR调控潜力；与CatBoost对比；用注意力机制识别关键序列基序
   - **验证方式**: 预测性能对比；注意力权重是否富集已知TF motif
   - **创新状态**: unverified

5. **候选名称**: TFCR进化的系统发育比较
   - **来源局限/观察**: 本文比较了6个物种，但未构建系统发育框架
   - **核心假设**: TFCR-启动子距离的调控模式在脊椎动物中保守，但特定谱系（如灵长类）中出现了距离压缩或扩张的适应性进化
   - **初步方法**: 扩展更多物种（如灵长类、啮齿类、鸟类、鱼类），用系统发育比较方法（PIC, PGLS）检验距离与RegulatoryScore关系的进化速率；结合dN/dS分析鉴定正选择基因
   - **验证方式**: 系统发育信号检测；祖先状态重建
   - **创新状态**: unverified

6. **候选名称**: TFCR复杂度与TF结合协同性的单细胞解析
   - **来源局限/观察**: 本文使用bulk ATAC-seq，无法解析细胞异质性
   - **核心假设**: 单细胞水平上TFCR复杂度的异质性反映调控噪声，高复杂度TFCR在特定细胞类型中更稳定
   - **初步方法**: 用scATAC-seq数据识别单细胞TFCRs，计算每个细胞的TFCR复杂度分布；与scRNA-seq整合，分析TFCR复杂度与基因表达噪声的关系
   - **验证方式**: 高复杂度TFCR是否对应更低的表达噪声（Fano factor）
   - **创新状态**: unverified