## 01 基本信息

- **标题**：Integrating multi-omic QTLs and predictive models reveals regulatory architectures at immune related GWAS loci in CD4+ T cells
- **作者**：Matos, Marliette R; Ghatan, Samuel; Bankier, Sean; Thompson, Taylor V; Lundy-Perez, Kassidy; Suzuki, Masako; Dona-Termine, Reanna; Stauber, Jacob; Reynolds, David; Rosales, Kathleen; Griffen, Anthony; Isshihara, Mariko; Simpson, Danny; Andrews, Nathanael; Ahmed, Omar; Gold, Samantha; Ostrowiak, Sophia R; Raj, Srilakshmi; Milman, Sofiya; Lappalainen, Tuuli; Greally, John M
- **单位**：未提供（从基金信息推断含 Albert Einstein College of Medicine 等，但原文未明确列出作者单位列表）
- **期刊/平台**：medRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（研究论文）
- **领域**：功能基因组学、调控基因组学、免疫遗传学
- **关键词**：eQTL、caQTL、CD4+ T细胞、ChromBPNet、GWAS、染色质可及性、单细胞RNA-seq、调控架构
- **DOI/ID**：10.64898/2026.01.27.26344979
- **代码**：https://github.com/marlmatos/cd4t-qtl-map
- **数据**：Zenodo（eQTL summary statistics: https://doi.org/10.5281/zenodo.18261455；caQTL summary statistics: https://doi.org/10.5281/zenodo.18317807；ChromBPNet models: https://doi.org/10.5281/zenodo.18394129）
- **阅读日期**：2026-05-13（基于当前日期推断）
- **在课题方向中的位置**：本文属于「蛋白质-DNA互作 × AI/深度学习」交叉方向，聚焦于利用深度学习模型（ChromBPNet）预测染色质可及性变异的调控效应，并与经验性QTL定位（eQTL/caQTL）进行系统比较。对TF–DNA结合机制研究而言，本文提供了：(1) 将序列到功能的深度学习模型（ChromBPNet）应用于变异效应预测的完整流程；(2) 深度学习预测与经验QTL证据的系统性整合与比较框架；(3) TF-MoDISco + Fi-NeMo 从深度学习模型中提取TF motif并结合变异进行TF结合破坏预测的方法链。该文不直接研究TF–DNA结合的物理机制（如结构、动力学），而是从序列决定论角度预测TF结合位点的调控效应。

---

## 02 一句话总结

本文在362名供体的CD4+ T细胞中整合单细胞RNA-seq eQTL、bulk ATAC-seq caQTL和基于ChromBPNet的深度学习变异效应预测，发现经验性molQTL与深度学习预测仅有部分重叠（深度学习仅覆盖约4.7%的GWAS位点），但两者在效应方向和大体上高度一致，且通过TF-MoDISco/Fi-NeMo可识别出TF motif破坏机制，为免疫相关GWAS位点提供了多层次的调控架构解读。

---

## 03 研究问题

**具体问题**：在CD4+ T细胞中，如何系统性地整合多组学QTL（eQTL、caQTL）与基于序列的深度学习预测模型（ChromBPNet），以解析免疫相关GWAS位点的调控架构？经验性QTL定位与深度学习预测在识别调控变异方面的一致性和互补性如何？

**为什么重要**：GWAS位点大多位于非编码区，功能解读困难。CD4+ T细胞是免疫疾病的关键细胞类型，但缺乏该细胞类型的多组学调控QTL资源。理解调控变异的机制（特别是通过TF结合破坏）对于从关联到机制的转化至关重要。

**现有方法不足**：
- 单一组学QTL（如仅eQTL）无法捕捉染色质层面的调控效应
- 深度学习模型（如ChromBPNet）虽可预测变异效应，但缺乏与经验QTL的系统比较，其独立解释能力未知
- 传统QTL定位受LD、等位基因频率和样本量限制，难以精确定位因果变异
- 缺乏将深度学习预测与TF motif破坏机制直接关联的系统流程

**精确研究问题**：Can integrating multi-omic QTLs (eQTLs and caQTLs) with deep learning-based variant effect predictions (ChromBPNet) reveal regulatory architectures at immune-related GWAS loci in CD4+ T cells that neither approach alone can provide?

---

## 04 背景与发展脉络

**阶段一：bulk eQTL定位时代**
- 代表方法：GTEx等项目的cis-eQTL mapping
- 优点：建立了基因表达遗传调控的基本框架
- 局限：bulk组织混合细胞类型，无法捕捉细胞类型特异性效应；仅覆盖mRNA层面

**阶段二：多组学QTL与单细胞QTL**
- 代表方法：caQTL（染色质可及性QTL）、scRNA-seq eQTL、动态eQTL（CellRegMap）
- 优点：扩展到染色质层面，可检测细胞状态依赖的调控效应
- 局限：仍依赖经验关联，受LD和样本量限制

**阶段三：序列到功能的深度学习模型**
- 代表方法：ChromBPNet（Bias Factorized Basenji）、Enformer、Basenji2
- 优点：直接从序列预测调控活性，可评估任意变异的效应，不受LD限制
- 局限：预测局限于模型训练时的细胞类型/条件；预测的生物学机制解释性有限

**阶段四：深度学习+QTL整合（本文位置）**
- 本文主张：将经验QTL与深度学习预测作为互补资源，系统比较两者的一致性，并利用TF-MoDISco/Fi-NeMo从深度学习模型中提取TF结合机制信息
- 位置：处于「经验QTL定位 × 深度学习预测」交叉整合的前沿，强调两种方法的互补性而非替代性

> 注：此脉络基于本文引言和结果内容整理，属于「仅本文框架」，未经外部系统综述核验。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| GWAS位点功能解读困难 | 大多数GWAS位点位于非编码区，难以确定因果变异和机制 | GWAS关联信号受LD影响，且非编码变异的功能效应难以直接预测 | Introduction 第1段 |
| 单一组学QTL覆盖不足 | eQTL无法捕捉染色质层面的调控效应 | 基因表达是调控级联的最终输出，中间层（染色质可及性）的变异效应可能不反映在稳态表达中 | Results 图1G：仅30.5%的caQTL与eQTL共定位 |
| 深度学习预测缺乏经验验证 | 模型预测的变异效应缺乏与真实QTL的系统比较 | 深度学习模型训练于特定细胞类型/条件，其预测的泛化性和生物学有效性未知 | Results 图4C：深度学习仅覆盖少量molQTL |
| 因果变异精确定位困难 | QTL定位受LD、等位基因频率和样本量限制 | 关联分析无法区分LD中的共变异位点 | Introduction 第2段 |
| TF结合破坏机制难以系统预测 | 需要将变异效应与TF motif结合变化直接关联 | 需要从深度学习模型中提取可解释的TF motif模式，并与变异效应整合 | Results 图5A：TF-MoDISco + Fi-NeMo流程 |
| 细胞状态依赖的调控效应难以捕捉 | 传统eQTL假设效应恒定，忽略细胞状态转变 | CD4+ T细胞包含多种亚型和状态，调控效应可能具有状态特异性 | Results 图2：动态eQTL（CellRegMap）识别210个状态依赖eQTL |

---

## 06 核心思想

**1) 表面方法**：
- 在362名供体的CD4+ T细胞中生成三种数据模态：基因型（低深度WGS + 填充）、单细胞RNA-seq（用于eQTL和动态eQTL）、bulk ATAC-seq（用于caQTL）
- 训练CD4+ T细胞特异性的ChromBPNet模型（基于染色质可及性数据）
- 对全部常见SNP进行ChromBPNet变异效应预测（评分）
- 将三种证据源（eQTL、caQTL、ChromBPNet预测）进行系统整合和交叉比较
- 使用TF-MoDISco从ChromBPNet模型中提取TF motif模式，用Fi-NeMo预测变异导致的TF motif破坏
- 将整合结果映射到51个免疫相关GWAS性状的位点

**2) 核心洞察**：
- 经验QTL与深度学习预测是**互补而非冗余**的资源：深度学习模型能识别QTL定位遗漏的变异（特别是低频变异），而QTL提供了深度学习预测的经验验证
- 染色质可及性（caQTL）是连接序列变异与基因表达的关键中间层，caQTL比eQTL更接近因果机制
- 深度学习模型的**核苷酸级分辨率**使其能够预测TF motif破坏事件，这是传统QTL定位无法直接提供的信息
- 两种方法的一致性（效应方向、效应大小）验证了深度学习预测的生物学有效性，而差异则揭示了各自的方法学盲区

**3) 可能的普适教训 [Analysis]**：
- 在调控基因组学中，**经验关联与机制预测的整合**比单一方法更强大：经验方法提供真实性和广度，预测方法提供分辨率和机制可解释性
- 深度学习模型的「可解释性提取」（如TF-MoDISco）是将黑盒预测转化为生物学机制假设的关键桥梁
- 多组学整合的价值在于**中间表型**（如染色质可及性）往往比终端表型（如基因表达）更接近因果变异的作用机制

---

## 07 方法总览

**输入**：
- 362名供体的基因型（7,824,658个变异，MAF>0.05）
- 单细胞RNA-seq表达谱（475,552个细胞，来自398名供体）
- Bulk ATAC-seq染色质可及性谱（397名供体，71,348个peak）
- 51个免疫相关GWAS性状的汇总统计

**输出**：
- 10,424个条件独立cis-eQTL和68,294个caQTL
- 210个动态eQTL（细胞状态依赖）
- 11,440个ChromBPNet显著变异
- 4,361个预测破坏TF motif的SNP
- 每个GWAS位点的多层次调控注释

**模块**：
1. **QTL定位模块**：TensorQTL（cis-eQTL/caQTL mapping，5% FDR）
2. **动态eQTL模块**：CellRegMap（基因型×细胞状态互作）
3. **统计精细定位模块**：SuSiE（识别条件独立信号和可信集）
4. **共定位模块**：coloc（eQTL-caQTL共定位，PP.H4>0.5）
5. **深度学习预测模块**：ChromBPNet（bias-factorized，8个供体训练）
6. **TF motif发现模块**：TF-MoDISco（从ChromBPNet中提取de novo motif）
7. **TF motif破坏预测模块**：Fi-NeMo（变异效应下的motif匹配变化）
8. **GWAS整合模块**：SuSiE-coloc（molQTL与GWAS共定位）

**训练**：
- ChromBPNet：8个供体（>100M reads/供体），5折交叉验证（fold 0-4），bias模型用fold 0训练
- 变异效应预测：对所有位于ChromBPNet peak内的SNP计算预测log fold-change

**反馈回路**：
- ChromBPNet预测与caQTL经验效应的比较（Pearson相关）用于验证预测有效性
- 预测与经验不一致的位点用于识别方法学盲区

**文字流程**：
1. 从362名供体收集CD4+ T细胞，分别进行scRNA-seq和bulk ATAC-seq
2. 对scRNA-seq数据进行细胞类型注释和伪批量聚合，使用TensorQTL定位cis-eQTL
3. 对bulk ATAC-seq数据进行peak calling和定量，使用TensorQTL定位caQTL
4. 对eQTL和caQTL分别进行SuSiE精细定位，获得条件独立信号和可信集
5. 使用coloc检测eQTL-caQTL共定位
6. 使用CellRegMap检测动态eQTL（基因型×细胞状态互作）
7. 并行地，用8个供体的ATAC-seq数据训练ChromBPNet模型
8. 对peak内所有SNP进行ChromBPNet变异效应预测
9. 用TF-MoDISco从模型中提取TF motif，用Fi-NeMo预测SNP导致的motif破坏
10. 将molQTL与51个GWAS性状进行共定位分析
11. 在GWAS位点上整合所有证据源，构建调控架构

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| cis-eQTL定位（TensorQTL） | 识别与基因表达相关的遗传变异 | 建立基因表达层面的调控证据 | 输入：基因型+伪批量表达；输出：10,424个条件独立eQTL | Results 图1B | 失去表达层面的调控证据，无法评估染色质效应是否传导至表达 |
| cis-caQTL定位（TensorQTL） | 识别与染色质可及性相关的遗传变异 | 捕捉序列变异对染色质状态的直接效应 | 输入：基因型+ATAC-seq peak定量；输出：68,294个caQTL | Results 图1B | 失去染色质层面的调控证据，无法评估TF结合位点的可及性变化 |
| 动态eQTL（CellRegMap） | 识别细胞状态依赖的eQTL效应 | 捕捉CD4+ T细胞亚型和状态特异的调控 | 输入：基因型+单细胞表达+细胞状态；输出：210个动态eQTL | Results 图2 | 失去状态依赖的调控信息，可能遗漏免疫激活特异的调控机制 |
| SuSiE精细定位 | 识别条件独立信号和可信集 | 解决LD导致的关联信号模糊 | 输入：QTL summary statistics；输出：可信集（中位7个SNP） | Methods "eQTL and caQTL statistical fine-mapping" | 无法精确定位因果变异，下游分析将基于LD块而非可信变异 |
| ChromBPNet训练与变异评分 | 从序列预测染色质可及性效应 | 提供不依赖关联分析的独立变异效应预测 | 输入：DNA序列+ATAC-seq；输出：11,440个显著变异（IPS p<0.05） | Results 图4A-C | 失去序列层面的独立预测能力，无法评估QTL遗漏的变异 |
| TF-MoDISco motif发现 | 从深度学习模型中提取可解释的TF motif模式 | 将黑盒预测转化为TF结合机制假设 | 输入：ChromBPNet贡献分数；输出：20个TF家族motif | Results 图5A | 失去从模型中提取TF结合模式的能力，无法将变异效应与TF机制关联 |
| Fi-NeMo motif破坏预测 | 预测SNP对TF motif匹配的影响 | 直接评估变异是否破坏TF结合位点 | 输入：变异+motif+贡献分数；输出：4,361个预测破坏motif的SNP | Results 图5A | 失去TF结合破坏的机制层面预测，只能停留在可及性变化层面 |
| GWAS共定位（SuSiE-coloc） | 将molQTL与疾病关联信号共定位 | 将调控变异与疾病风险关联 | 输入：molQTL+GWAS summary statistics；输出：51个性状的共定位位点 | Results 图6 | 无法将调控变异与疾病关联，失去疾病相关性解读 |

**消融效应说明**：原文未提供系统消融实验。上述「移除后的影响」为基于方法逻辑的预期效应，非实测消融结果。

---

## 09 关键公式符号

本文核心方法为统计遗传学和深度学习工具的应用，未提出新公式。以下为理解关键分析所必需的公式：

**1. cis-QTL线性回归模型**（TensorQTL，Methods "cis-eQTL mapping"）：
$$y_{ij} = \beta_0 + \beta_G G_{ij} + \sum_k \beta_k C_{ik} + \epsilon_{ij}$$

- $y_{ij}$：供体$i$中基因/peak$j$的表达或可及性水平（经协变量校正）
- $G_{ij}$：供体$i$在基因/peak$j$附近变异的基因型（0/1/2）
- $\beta_G$：遗传效应大小（即QTL效应）
- $C_{ik}$：第$k$个协变量（年龄、性别、批次、PCs等）
- $\epsilon_{ij}$：残差

**2. 共定位后验概率**（coloc，Methods "Colocalization between eQTLs and caQTLs"）：
$$PP.H4 = P(H_4 | \text{data}) = \frac{P(\text{data} | H_4) \pi_4}{\sum_{k=0}^{4} P(\text{data} | H_k) \pi_k}$$

- $H_4$：两个性状共享同一因果变异的假设
- $\pi_k$：各假设的先验概率

**3. ChromBPNet变异效应评分**（IPS，Methods "ChromBPNet variant scoring"）：
$$\text{IPS} = f(\text{AAQ}, \log\text{FC}, \text{JSD})$$

- AAQ：Active Allele Quantile，活性等位基因在预测分布中的分位数
- logFC：log fold-change，变异对预测可及性的对数倍数变化
- JSD：Jensen-Shannon距离，变异前后预测分布的差异
- 具体函数形式未在原文中给出

**4. 动态eQTL互作模型**（CellRegMap，Methods "Dynamic-eQTL mapping"）：
$$y = \beta_G G + \beta_{G \times C} G \times C + \beta_C C + \epsilon$$

- $G \times C$：基因型与细胞状态（MOFA因子）的互作项
- $\beta_{G \times C}$：状态依赖的遗传效应

---

## 10 实验设计与证据链

**数据集/群体**：
- 362名自报Ashkenazi Jewish供体（最终分析集）
- 年龄分布：20-41岁（年轻组，中位27岁）和66-100岁（老年组，中位78岁）
- 来源：Albert Einstein College of Medicine Institute of Aging Research的LifeLong和Longevity队列

**数据规模**：
- 基因型：7,824,658个变异（MAF>0.05）
- scRNA-seq：475,552个细胞（中位1,310细胞/供体，1,492基因/细胞）
- ATAC-seq：71,348个peak（平均深度59.9M paired reads/供体）
- 动态eQTL分析：372,552个细胞（88.3%保留率）

**指标**：
- QTL：5% FDR
- 共定位：PP.H4 > 0.5
- ChromBPNet：IPS经验p值 < 0.05
- 效应一致性：Pearson相关

**基线/对比**：
- ChromBPNet预测 vs. caQTL经验效应
- eQTL vs. caQTL的共定位率
- 不同证据源的GWAS位点覆盖率

**评测协议**：
- 5折交叉验证训练ChromBPNet（fold 0-4）
- 变异效应预测与经验QTL效应的Pearson相关
- 共定位分析使用SuSei-coloc

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| cis-eQTL/caQTL定位 | CD4+ T细胞中存在广泛的遗传调控效应 | 5% FDR，cis窗口±1Mb | 10,424个eQTL（6,790个eGene）；68,294个caQTL（37,114个caPeak） | CD4+ T细胞具有丰富的调控QTL | 未提供与其它细胞类型QTL的正式比较 | Results 图1B |
| eQTL-caQTL共定位 | 部分eQTL与caQTL共享因果变异 | PP.H4>0.5 | 69%的eQTL显示染色质关联证据 | 多数eQTL伴随染色质可及性变化 | 共定位不等于因果关系 | Results 图1G |
| 动态eQTL（CellRegMap） | 部分eQTL效应随细胞状态变化 | 5% FDR，MOFA因子作为状态 | 210个动态eQTL | 存在状态依赖的调控效应 | 未验证这些动态eQTL的生物学功能 | Results 图2 |
| ChromBPNet变异评分 | 深度学习可预测CD4+ T细胞染色质变异的效应 | IPS p<0.05，159,908个peak内SNP | 11,440个显著变异 | 深度学习可识别潜在调控变异 | 预测未经实验验证 | Results 图4A |
| ChromBPNet vs. caQTL一致性 | 两种方法识别的变异效应一致 | Pearson相关，双显著变异 | 效应方向高度一致（R²=0.451） | 深度学习预测具有经验有效性 | 相关不等于因果；仅覆盖双方法均检测的变异 | Results 图4E |
| ChromBPNet与GWAS共定位 | 深度学习预测可解释GWAS位点 | 与51个免疫性状共定位 | 中位4.57%的GWAS可信集含ChromBPNet变异 | 深度学习提供部分GWAS位点的调控解读 | 覆盖率低，不能替代QTL | Results 图6A |
| TF-MOdisCO/Fi-NeMo motif破坏 | 变异通过破坏TF motif影响染色质 | 20个TF家族，4,361个SNP | 鉴定出ETS、KLF、AP-1、CTCF、RUNX等家族 | 可预测TF结合破坏机制 | 未实验验证具体TF结合变化 | Results 图5A |

---

## 11 结论正确解读

**任务范围**：
- 本研究聚焦于CD4+ T细胞（外周血，未刺激状态）的顺式调控变异
- 覆盖基因表达（eQTL）和染色质可及性（caQTL）两个分子层
- 深度学习预测限于ChromBPNet peak内的SNP

**oracle/真值输入**：
- ChromBPNet训练使用8个供体的ATAC-seq数据（非全部362个）
- 变异效应预测基于序列，不依赖QTL定位结果（独立性来源）
- 共定位分析使用GWAS summary statistics（外部数据）

**端到端状态**：
- 非端到端：QTL定位、深度学习预测、共定位分析为独立模块，通过整合分析连接
- 未进行实验验证（如CRISPR扰动、报告基因实验）

**算力成本**：
- 原文未报告具体算力需求

**历史数据依赖**：
- 依赖1000 Genomes参考面板进行基因型填充
- 依赖ENCODE染色质状态注释
- 依赖JASPAR、HOCOMOCO、CIS-BP motif数据库

**模型依赖**：
- ChromBPNet预测限于训练数据覆盖的细胞类型（CD4+ T细胞）
- 预测限于peak区域内的SNP，不覆盖peak外调控变异

**最难情形**：
- 低频变异（MAF 0.05-0.1）：QTL定位功效低，但ChromBPNet可预测
- 非peak区域的调控变异：两种方法均可能遗漏
- 细胞状态特异的调控效应：bulk ATAC-seq可能稀释

**群体/领域边界**：
- Ashkenazi Jewish群体，可能不完全代表其他人群的LD结构
- 外周血CD4+ T细胞，不覆盖组织驻留或激活状态的T细胞
- 51个免疫性状，不覆盖非免疫性状

**有边界的复述**：
在362名Ashkenazi Jewish供体的外周血CD4+ T细胞中，经验性QTL定位（eQTL+caQTL）与ChromBPNet深度学习预测提供了部分重叠但互补的调控变异证据：约69%的eQTL伴随染色质共定位信号，而ChromBPNet预测的变异与经验QTL在效应方向上高度一致（R²=0.451），但仅覆盖约4.7%的GWAS位点。通过TF-MOdisCO/Fi-NeMo可从深度学习模型中提取TF motif破坏机制，为免疫疾病位点提供核苷酸级的调控解读。该结论限于CD4+ T细胞、顺式调控、常见变异（MAF>0.05）和51个免疫性状的范围。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 未刺激状态的外周血CD4+ T细胞 | 所有分析基于未刺激的外周血CD4+ T细胞，可能遗漏激活状态特异的调控效应 | 未明确提及（隐含需要刺激条件下的研究） | Discussion 第1段 |
| 动态eQTL检测功效有限 | 稀有细胞状态或瞬时状态难以检测 | 未明确提及 | Discussion 第1段 |
| ChromBPNet预测覆盖有限 | 仅覆盖peak内SNP，且预测的变异仅占GWAS位点的一小部分（约4.7%） | 未明确提及（隐含需要更全面的预测模型） | Discussion 第2段 |
| 方法间比较存在技术差异 | ChromBPNet与QTL定位在peak定义、变异集和统计框架上存在差异，使直接比较复杂化 | 未明确提及 | Discussion 第2段 |
| 未进行实验验证 | 预测的TF motif破坏和调控机制未经实验验证 | 未明确提及（隐含需要实验验证） | Discussion 第3段 |

**作者提及的相关约束**（非正式局限）：
- 队列为Ashkenazi Jewish人群，可能影响LD结构和等位基因频率分布
- 样本量（362）限制了低频变异的QTL检测功效
- 使用伪批量方法聚合单细胞数据，可能损失部分单细胞分辨率信息

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| ChromBPNet训练仅用8个供体 | 模型可能过拟合于这8个供体的特定染色质景观，泛化性存疑 | 深度学习预测的可靠性取决于训练数据的代表性 | 用更多供体训练模型，比较预测稳定性；或使用独立数据集验证预测 | Methods "ChromBPNet model for pan CD4+ T cells" |
| 共定位阈值PP.H4>0.5相对宽松 | 可能包含大量假阳性共定位信号 | 影响对eQTL-caQTL共享机制的判断 | 使用更严格的阈值（如PP.H4>0.8）进行敏感性分析 | Methods "Colocalization between eQTLs and caQTLs" |
| ChromBPNet与QTL的效应比较存在选择偏差 | 仅比较双方法均检测到的变异，可能高估一致性 | 一致性估计可能不代表全部变异 | 对所有peak内SNP进行无阈值比较；或使用排序相关性 | Results 图4E |
| TF-MOdisCO motif匹配的生物学验证缺失 | 预测的TF motif破坏可能不代表真实的TF结合变化 | TF机制解读的可靠性未经验证 | 使用ChIP-seq或PBM数据验证特定SNP的TF结合变化 | Results 图5A |
| 动态eQTL的细胞状态定义依赖MOFA因子 | MOFA因子可能捕捉技术伪影而非真实生物学状态 | 动态eQTL的生物学解释可能不准确 | 使用已知细胞类型标记验证MOFA因子的生物学意义 | Methods "Dynamic-eQTL mapping" |
| 未报告多重检验校正的细节 | QTL定位和动态eQTL分析涉及大量检验，校正方法影响结果可靠性 | 可能影响QTL列表的假阳性率 | 检查原文补充材料中的校正方法 | Methods "cis-eQTL mapping" |
| Ashkenazi Jewish人群的LD结构可能不同于其他人群 | 精细定位结果可能不直接迁移到其他人群 | 影响GWAS位点解读的普适性 | 在其他人群队列中重复精细定位分析 | Methods "Cohort description" |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **深度学习预测与经验QTL的互补整合框架**：本文展示了如何将序列到功能的深度学习模型（ChromBPNet）与经验QTL定位进行系统比较和整合。对于TF–DNA互作研究，这一框架可迁移为：将基于结构的TF–DNA结合预测（如AlphaFold、RoseTTAFold或MD模拟）与经验结合数据（如ChIP-seq、PBM）进行类似的互补整合，以识别结构预测的可靠性和盲区。

2. **TF-MOdisCO + Fi-NeMo 方法链**：从深度学习模型中提取可解释的TF motif模式，再结合变异效应预测TF motif破坏。这一「模型解释→机制预测」的流程可直接迁移到TF–DNA结合研究：从任意序列到功能的深度学习模型（如DeepSEA、Enformer）中提取TF结合motif，再预测SNP对结合的影响。

3. **中间表型（染色质可及性）作为调控机制的关键层**：本文发现caQTL比eQTL更接近因果机制，且大量caQTL不传导至表达变化。对TF–DNA互作研究而言，这提示染色质可及性（或TF占据）是连接序列变异与基因表达的关键中间层，研究TF–DNA结合时应优先考虑中间表型而非终端表型。

4. **多组学共定位作为调控架构解析工具**：通过eQTL-caQTL共定位和GWAS共定位，本文构建了从变异→染色质→表达→疾病的调控链。这一思路可迁移到TF–DNA互作研究：将TF结合QTL（bQTL）与eQTL、caQTL和GWAS进行多层共定位，以解析TF结合变异在疾病中的因果链。

5. **细胞状态依赖的调控效应检测**：使用CellRegMap检测基因型×细胞状态互作，识别状态特异的eQTL。对TF–DNA互作研究，这提示TF结合效应可能具有细胞状态依赖性，应在多种状态（如激活、分化）下检测TF–DNA结合QTL。

6. **深度学习预测的核苷酸级分辨率优势**：ChromBPNet可预测单个SNP的效应，不受LD限制，弥补了QTL定位在低频变异上的不足。对TF–DNA互作研究，这提示基于序列的预测模型可用于评估QTL定位无法覆盖的变异（如低频、罕见变异）对TF结合的影响。

7. **效应方向一致性作为验证指标**：本文使用Pearson相关（R²=0.451）验证深度学习预测与经验QTL的效应方向一致性。这一验证策略可迁移到TF–DNA结合预测模型的评估中：预测的TF结合变化应与经验测量的结合变化在方向上一致。

---

## 15 与已有知识连接

1. **ChromBPNet（Pampari et al., 2025）**：本文使用的深度学习模型，基于Bias Factorized Basenji架构，从序列预测染色质可及性。与TF–DNA互作研究相关的是，该模型可解释为学习TF结合序列特征，其贡献分数可反映TF结合位点的重要性。

2. **CellRegMap（Cuomo et al., 2023）**：用于检测基因型×细胞状态互作的统计框架，在单细胞eQTL分析中应用广泛。与TF–DNA互作研究相关的是，该框架可迁移为检测TF结合QTL的细胞状态依赖性。

3. **TF-MOdisCO（Shrikumar et al., 2018）**：从深度学习模型中提取序列motif的工具，本文用于从ChromBPNet中提取TF结合模式。与TF–DNA互作研究直接相关，可用于从任意序列到功能的模型中提取TF结合motif。

4. **Findr（Wang et al., 2017）**：因果推断工具，本文用于推断染色质可及性与基因表达之间的因果方向。与TF–DNA互作研究相关的是，该工具可迁移为推断TF结合与基因表达之间的因果关系。

5. **SuSiE（Wang et al., 2020）**：贝叶斯精细定位方法，本文用于识别条件独立QTL信号。与TF–DNA互作研究相关的是，可用于TF结合QTL的精细定位。

6. **ENCODE染色质状态注释**：本文用于功能注释QTL变异。与TF–DNA互作研究相关的是，可用于注释TF结合位点的染色质环境。

7. **GTEx eQTL资源**：本文与GTEx等bulk eQTL资源进行对比。与TF–DNA互作研究相关的是，GTEx提供了多种组织的eQTL数据，可用于跨组织比较TF结合调控效应。

8. **1000 Genomes Project**：本文用于基因型填充参考面板。与TF–DNA互作研究相关的是，提供了人群水平的变异频率和LD信息。

9. **候选方向 [Analysis]**：本文的方法链（QTL定位→深度学习预测→TF motif破坏→GWAS整合）可进一步与以下方向结合：(1) AlphaFold等结构预测方法，预测TF–DNA结合的三维结构变化；(2) 分子动力学模拟，评估SNP对TF–DNA结合动力学的影响；(3) 高通量实验方法（如STARR-seq、MPRA），验证预测的调控效应。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选1：基于深度学习的TF–DNA结合预测与经验bQTL的系统整合框架

- **名称**：TF-BindQTL：整合深度学习结合预测与经验bQTL的TF–DNA调控变异解析框架
- **来源局限/观察**：本文展示了ChromBPNet与caQTL的整合价值，但未直接研究TF–DNA结合。目前缺乏将深度学习TF结合预测与经验TF结合QTL（bQTL）进行系统比较的框架。
- **核心假设**：深度学习TF结合预测（如DeepSEA、Enformer的TF贡献分数）与经验bQTL在效应方向和大小上部分一致，且互补覆盖不同类型的调控变异。
- **增量**：将本文的「深度学习+QTL」整合框架从染色质可及性扩展到TF–DNA结合层面，提供TF特异性的调控变异解读。
- **初步方法**：(1) 在公共数据（如ENCODE、Roadmap）中获取多种TF的ChIP-seq bQTL；(2) 用深度学习模型预测同一TF的结合效应；(3) 系统比较两种方法的覆盖率、一致性和互补性；(4) 在GWAS位点上整合bQTL和深度学习预测。
- **验证方式**：使用独立数据集（如GTEx、ImmVar）验证预测的TF结合变异是否影响基因表达；使用CRISPR扰动实验验证关键位点。
- **创新状态**：unverified

### 候选2：从深度学习模型中提取TF–DNA结合机制的可解释motif图谱

- **名称**：TF-BindExplainer：从深度学习模型中提取TF–DNA结合机制的可解释图谱
- **来源局限/观察**：本文使用TF-MOdisCO从ChromBPNet中提取TF motif，但仅关注染色质可及性。TF–DNA结合预测模型（如AlphaFold3、RoseTTAFold）的可解释性提取尚未系统开展。
- **核心假设**：从深度学习模型中提取的序列特征可映射到已知TF–DNA结合基序，并揭示新的结合模式。
- **增量**：将TF-MOdisCO方法从染色质可及性模型扩展到TF–DNA结合预测模型，提供TF结合机制的可解释性分析。
- **初步方法**：(1) 训练或使用已有的TF–DNA结合预测模型；(2) 应用TF-MOdisCO提取de novo motif；(3) 与JASPAR、CIS-BP等数据库比对；(4) 分析motif与TF家族、结合亲和力的关系。
- **验证方式**：使用PBM、SELEX等体外结合数据验证提取的motif；使用突变实验验证关键核苷酸。
- **创新状态**：unverified

### 候选3：TF–DNA结合变异的细胞状态依赖性系统分析

- **名称**：TF-BindDynamic：TF–DNA结合变异的细胞状态依赖性分析
- **来源局限/观察**：本文使用CellRegMap检测了动态eQTL，但未扩展到TF–DNA结合层面。TF结合可能具有更强的细胞状态依赖性。
- **核心假设**：TF–DNA结合QTL（bQTL）的效应在T细胞不同状态（如naive、记忆、激活）间存在显著差异，且这些差异与免疫疾病相关。
- **增量**：将动态QTL分析从基因表达扩展到TF–DNA结合层面，提供TF结合调控的细胞状态分辨率。
- **初步方法**：(1) 在多种T细胞状态（naive、记忆、激活、调节性T细胞）中检测TF结合（如ChIP-seq）；(2) 使用CellRegMap检测状态依赖的bQTL；(3) 将动态bQTL与动态eQTL和GWAS整合。
- **验证方式**：使用独立队列验证动态bQTL；使用功能实验（如报告基因）验证状态依赖的调控效应。
- **创新状态**：unverified

### 候选4：TF–DNA结合变异的物理模拟与深度学习预测的交叉验证

- **名称**：TF-BindPhys：MD模拟与深度学习预测的TF–DNA结合变异交叉验证
- **来源局限/观察**：本文仅使用深度学习预测，未涉及物理模拟。TF–DNA结合的物理模拟（如MD）可提供深度学习预测的机制验证。
- **核心假设**：深度学习预测的TF–DNA结合变异效应与MD模拟的结合自由能变化在关键位点上一致，且MD可解释深度学习预测失败的案例。
- **增量**：将物理模拟与深度学习预测结合，提供TF–DNA结合变异的机制级验证。
- **初步方法**：(1) 选择深度学习预测的TF–DNA结合变异；(2) 使用MD模拟计算结合自由能变化；(3) 比较两种方法的一致性和差异；(4) 分析差异案例的分子机制。
- **验证方式**：使用实验结合数据（如ITC、SPR）验证关键位点的结合变化。
- **创新状态**：unverified

### 候选5：免疫疾病GWAS位点的TF–DNA结合变异优先级排序工具

- **名称**：TF-BindPrioritize：免疫疾病GWAS位点的TF–DNA结合变异优先级排序工具
- **来源局限/观察**：本文整合了molQTL和深度学习预测来解读免疫疾病GWAS位点，但未提供可直接使用的工具。目前缺乏专门针对TF–DNA结合变异的优先级排序工具。
- **核心假设**：整合bQTL、深度学习预测和TF motif破坏信息可显著提高免疫疾病GWAS位点中因果变异的识别效率。
- **增量**：提供一个可复用的计算工具，整合多种证据源进行TF–DNA结合变异的优先级排序。
- **初步方法**：(1) 整合公共bQTL数据、深度学习预测和TF motif数据库；(2) 开发加权评分系统；(3) 在免疫疾病GWAS位点上验证；(4) 与现有工具（如VEP、CADD）比较。
- **验证方式**：使用已知的免疫疾病因果变异作为金标准；使用CRISPR验证高优先级位点。
- **创新状态**：unverified