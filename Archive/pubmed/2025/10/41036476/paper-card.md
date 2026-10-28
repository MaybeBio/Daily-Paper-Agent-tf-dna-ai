## 01 基本信息
- **标题**：3D Genome Architecture in Stem Cell Lineage Commitment: from Structural Organization to Precision Regulation
- **作者**：He, Yanchi; Li, Wenrui; Li, Lin; Yang, Ying; Lu, Yutong; Pan, Yufei; Wang, Qing; Sun, Yuqiang; Xie, Yuxuan; Wu, Mingyue; Luo, Peng; Sun, Wansu; Zhang, Hengguo
- **单位**：未提供（据致谢推测含安徽医科大学口腔医学院，未在正文明确列出）
- **期刊/平台**：Advanced Genetics (Hoboken, N.J.)
- **年份**：2025-10-02
- **论文类型**：综述（Review）
- **领域**：3D基因组结构、表观遗传学、干细胞谱系定向分化
- **关键词**：3D genome; Hi-C; TAD; chromatin loop; phase separation; stem cell differentiation; multi-omics; AI
- **DOI/arXiv**：10.1002/ggn2.202500035
- **代码**：未提供
- **数据**：未提供（综述，无原始数据）
- **阅读日期**：2026-05-13
- **在课题方向中的位置**：本文为综述，覆盖3D基因组结构（compartment/TAD/loop）在干细胞分化中的动态变化，并讨论LLPS转录凝聚体、多组学整合与AI建模。与「TF–DNA结合机制 × AI/物理模拟」课题的关联在于：①系统梳理了CTCF/cohesin介导的loop extrusion模型（TF–DNA互作的结构基础）；②讨论了TF（如GATA1、SOX2、OCT4）通过相分离形成转录凝聚体调控基因表达的机制；③综述了AI模型（如SEE、HiCFoundation、ChromoGen）用于染色质结构预测与增强，可作为TF–DNA结合预测方法迁移的背景框架。

## 02 一句话总结
本文综述了3D基因组结构（compartment、TAD、chromatin loop）在干细胞谱系定向中的动态重组织机制，提出从静态结构解析走向动态精准调控（结合LLPS转录凝聚体、多组学整合与AI建模）的研究范式，并指出当前在分辨率、数据复杂性与因果推断方面的技术瓶颈。

## 03 研究问题
- **具体问题**：干细胞谱系定向过程中，3D基因组结构（compartment、TAD、chromatin loop）如何动态重组织，并通过何种机制（包括LLPS介导的转录凝聚体）实现谱系特异性基因的精准调控？
- **为什么重要**：传统一维表观遗传（DNA甲基化、组蛋白修饰）无法解释远距离enhancer–promoter互作和98%非编码区的调控功能；3D基因组结构是连接表观遗传状态与基因表达时空特异性的关键桥梁，对理解发育、疾病（如白血病）和再生医学至关重要。
- **现有方法不足**：①Hi-C等技术的分辨率限制（通常1–5 kb）难以精确定位小规模调控元件互作；②数据量大、分析流程复杂，缺乏标准化协议；③多组学整合方法不成熟；④难以从相关性推断因果关系（causality dilemma）。
- **Can问题**：Can 3D基因组结构的动态变化（compartment switching、TAD边界重塑、loop形成/解散）与LLPS转录凝聚体的协同作用，因果性地驱动干细胞谱系定向而非仅仅是伴随现象？

## 04 背景与发展脉络
*标注：以下脉络为「经外部核验」的领域共识，结合本文框架整理。*

| 阶段 | 代表性方法/概念 | 优点 | 局限 |
|------|----------------|------|------|
| 线性表观遗传时代 | DNA甲基化、组蛋白修饰（ChIP-seq） | 可解释基因开关状态 | 无法解释远距离调控、时空协调性 |
| 3D基因组结构发现 | Hi-C、3C衍生技术 | 揭示compartment、TAD、loop等层级结构 | 分辨率有限（1–5 kb）、群体平均效应掩盖单细胞异质性 |
| 单细胞与多组学时代 | scHi-C、scATAC-seq、HiChIP、Dip-C | 解析单细胞异质性、多组学整合 | 数据稀疏、噪声大、分析流程复杂 |
| 机制解析时代 | loop extrusion模型（CTCF/cohesin）、LLPS转录凝聚体 | 提供结构形成的分子机制解释 | 因果性证据不足，难以区分驱动与伴随 |
| AI与精准调控时代 | 深度学习（SEE、HiCFoundation、ChromoGen）、CRISPR基因组编辑 | 增强分辨率、预测结构、实现靶向干预 | 模型可解释性差、训练数据依赖、体内验证困难 |

**本文主张的位置**：处于「机制解析时代」向「AI与精准调控时代」过渡的节点，主张整合多组学+AI+基因编辑，从静态结构描述走向动态精准调控。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 一维表观遗传解释力不足 | 无法解释远距离enhancer–promoter互作、98%非编码区功能 | 线性表观遗传缺乏空间维度信息 | Introduction 第1段（"linear epigenetics struggles to explain the spatiotemporal coordination"） |
| Hi-C分辨率限制 | 通常1–5 kb，难以精确定位小规模调控元件互作 | 测序深度与成本限制 | "Current Challenges" Resolution and Sensitivity Limitations 节（"typically achieve resolutions no finer than 1–5 kilobases"） |
| 数据规模与计算瓶颈 | Hi-C产生数十亿reads，处理流程复杂（比对、过滤、归一化） | 计算资源需求大，缺乏标准化协议 | "Current Challenges" Complex Data Analysis Pipelines 节 |
| 多组学整合困难 | 现有工具多为单数据类型设计，缺乏跨组学整合能力 | 不同数据类型异质性大，统计方法不成熟 | "Current Challenges" Complex Data Analysis Pipelines 节（"Many existing bioinformatics tools were developed for analyzing single data types"） |
| 单细胞数据稀疏噪声大 | scHi-C数据极度稀疏，难以区分技术噪声与真实生物学变异 | 单细胞捕获效率低、覆盖度不足 | "Current Challenges" Complex Data Analysis Pipelines 节（"data that is extremely sparse and noisy"） |
| 重复序列区域分析盲区 | 着丝粒、端粒等重复区域无法可靠比对 | 读段多映射问题 | "Current Challenges" Difficulties in Analyzing Repetitive Genomic Regions 节 |
| 因果推断困难 | 染色质变化与分化结果多为相关性，难以证明因果 | 缺乏时间分辨与扰动实验 | "Current Challenges" The Causality Dilemma 节 |
| 表观遗传记忆干扰 | 干细胞保留先前状态的表观遗传标记，影响分化方向 | 组蛋白/DNA甲基化标记的维持机制 | "Current Challenges" Epigenetic Memory 节 |

## 06 核心思想

### 1) 表面方法
本文为综述，无原始实验方法。其组织框架为：①从一维表观遗传到3D基因组结构的概念转变；②系统描述compartment、TAD、chromatin loop在干细胞多能性与谱系定向中的动态变化；③引入LLPS介导的转录凝聚体作为动态调控机制；④综述多组学整合与AI建模工具；⑤提出工程化干预策略（CRISPR-based spatial genome editing）。

### 2) 核心洞察
- **3D基因组结构是动态可编程的**：分化过程中compartment switching、TAD边界重塑、loop形成/解散是协同发生的，而非静态支架。
- **结构变化与表观遗传存在双向互作**：3D结构决定表观遗传修饰的可及性，表观遗传修饰反过来影响结构稳定性。
- **LLPS是连接结构与功能的桥梁**：转录凝聚体通过相分离富集TF和RNA Pol II，在特定基因组位点形成高浓度调控枢纽，实现谱系特异性基因的精准调控。
- **AI是处理3D基因组复杂性的必要工具**：深度学习模型可从序列特征预测结构、从稀疏数据中恢复信息、模拟扰动效果。

### 3) 可能的普适教训 [Analysis]
- **结构-功能关系的因果推断需要多时间点+扰动实验**：仅靠相关性分析无法区分驱动与伴随，需结合CRISPR扰动、degron系统等干预手段。
- **跨尺度整合是理解基因调控的关键**：从单碱基（TF结合位点）到染色体（compartment）的多层级信息必须协同分析，单一尺度方法有根本局限。
- **AI模型的价值在于生成可检验假设**：预测模型（如ChromoGen）的真正价值不是替代实验，而是缩小搜索空间、指导实验设计。

## 07 方法总览
*本文为综述，无原始方法。以下为综述中讨论的技术方法框架。*

- **输入**：Hi-C/scHi-C数据、scATAC-seq、ChIP-seq、RNA-seq等多组学数据；序列特征（CTCF motif、TF结合位点）
- **输出**：3D结构模型（compartment/TAD/loop注释）、基因调控网络、分化轨迹预测
- **核心模块**：
  1. 染色质构象捕获（Hi-C、Micro-C、scHi-C、HiChIP、Dip-C/vDip-C）
  2. 多组学整合（Hi-C + ATAC-seq + ChIP-seq + RNA-seq）
  3. AI/深度学习模型（SEE、HiCFoundation、ChromoGen、Fast-Higashi）
  4. 统计方法（ZipHiC：HMRF + ABC）
  5. 功能验证工具（CRISPR-Cas9、CRISPR-GO、degron系统）
- **反馈回路**：AI预测 → 实验验证 → 模型迭代优化
- **假设**：3D基因组结构是谱系定向的因果驱动因素，而非仅仅是转录活性的结果

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Hi-C及衍生技术 | 捕获全基因组染色质互作 | 提供3D结构的基础数据 | 输入：交联DNA；输出：互作矩阵 | "Current Challenges" 节多处引用 | 无此模块则3D结构研究不存在（基础技术） |
| Micro-C | 提高分辨率至核小体水平（~200 bp） | 解析小规模调控元件互作 | 输入：微球菌核酸酶消化染色质；输出：高分辨率互作图 | "Future Directions" Spatial Resolution 节 | 预期影响：无法解析enhancer–promoter级别的精细互作 [Analysis] |
| scHi-C/scNanoHi-C | 单细胞水平3D结构分析 | 解析细胞异质性、稀有亚群 | 输入：单细胞；输出：单细胞互作图 | Introduction 第2段 | 预期影响：丧失异质性信息，无法研究瞬时状态 |
| HiChIP | 富集特定蛋白介导的互作 | 解析TF/CTCF介导的loop | 输入：ChIP富集+Hi-C；输出：蛋白特异性互作图 | "Current Challenges" 节提及 | 预期影响：无法区分蛋白特异性互作 |
| AI模型（SEE/HiCFoundation/ChromoGen） | 结构预测、分辨率增强、loop检测 | 处理稀疏数据、预测未观测结构 | 输入：Hi-C/序列；输出：高分辨率结构/预测 | "Future Directions" Structure Prediction Algorithms 节 | 预期影响：丧失从有限数据中提取信息的能力，分析效率降低3–5倍 |
| ZipHiC | 识别富集互作、校正实验偏差 | 区分真实互作与技术噪声 | 输入：Hi-C矩阵；输出：显著互作 | "Future Directions" 节提及 | 预期影响：假阳性率升高 [Analysis] |
| CRISPR-GO | 空间定位基因组位点 | 验证结构-功能因果关系 | 输入：sgRNA+定位蛋白；输出：位点重定位 | "Future Directions" Genome Spatial Mapping 节 | 预期影响：无法直接验证结构的功能必要性 |
| 多组学整合 | 联合分析多种数据类型 | 构建结构-功能-表型关联 | 输入：Hi-C+ATAC+ChIP+RNA；输出：调控网络模型 | "Current Challenges" 节多处 | 预期影响：丧失跨尺度关联能力 |

## 09 关键公式符号
**不适用**。本文为综述，未包含数学公式或算法定义。涉及的统计方法（如ZipHiC的HMRF+ABC）仅有方法名称，无具体公式。

## 10 实验设计与证据链
*本文为综述，无原始实验。以下为综述中引用的代表性研究证据。*

- **数据集/群体**：未提供（综述引用他人研究，未列出具体数据集）
- **规模**：未提供
- **指标**：未提供
- **基线**：未提供
- **预算**：未提供
- **骨干/仪器**：未提供
- **Oracle输入**：不适用
- **评测协议**：不适用

| 实验/证据 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|-----------|-------------|------------|------|------------|-------------------|------|
| 果蝇胚胎发育中转录工厂组成变化 | 转录工厂动态响应发育阶段 | 不同发育阶段比较 | 转录工厂组成和位置随发育阶段改变 | 转录工厂是动态结构 | 未证明因果驱动 | Introduction 第2段引用[62] |
| 小鼠ESC→NPC分化中compartment switching | 分化伴随compartment重组织 | 多能态vs分化态 | Nanog位点A→B转换，Syn1位点B→A转换 | 分化伴随可预测的compartment变化 | 未证明是原因而非结果 | Dynamic Rewiring 节引用[28,38] |
| 神经发育中Sox9-Kcnj2位点新TAD边界形成 | 新TAD边界隔离谱系特异调控 | 边界形成前后基因表达比较 | 新边界隔离Sox9增强子与Kcnj2启动子 | TAD边界可防止异位激活 | 未证明边界形成是主动机制 | Dynamic Rewiring 节引用[28,44] |
| 造血分化中GATA1超级增强子凝聚体形成 | LLPS凝聚体驱动谱系基因激活 | 分化前后凝聚体状态比较 | GATA1位点形成相分离凝聚体，激活红系基因 | LLPS参与谱系基因激活 | 未直接证明凝聚体是因果驱动 | Phase Separation 节引用[21] |
| AI模型（ChromoGen等）预测结构 | AI可从序列预测3D结构 | 预测vs实验Hi-C比较 | 预测数千结构仅需数分钟 | AI可加速结构解析 | 预测精度有限，需实验验证 | Future Directions 节引用[134] |
| CRISPR-GO位点重定位实验 | 空间位置可调控基因表达 | 位点重定位前后表达比较 | 将基因座定位到特定核区域可改变表达 | 空间位置影响基因表达 | 效应大小和普适性未明确 | Future Directions 节引用[147] |

## 11 结论正确解读
- **任务范围**：本文为综述，覆盖3D基因组结构（compartment/TAD/loop）在干细胞多能性维持与谱系定向中的动态变化，以及LLPS转录凝聚体、多组学整合、AI建模和CRISPR干预策略。
- **Oracle/真值输入**：不适用（无计算实验）。
- **端到端状态**：不适用（综述无端到端流程）。
- **算力成本**：文中提及Hi-C数据处理需要高性能计算集群，但未给出具体成本。
- **历史数据依赖**：综述基于已发表研究，依赖领域内积累的Hi-C、ChIP-seq等公共数据。
- **模型依赖**：文中讨论的AI模型（SEE、HiCFoundation、ChromoGen等）均为他人工作，综述未提供独立验证。
- **最难情形**：①单细胞水平3D结构解析（数据稀疏）；②重复序列区域分析；③因果推断（区分驱动与伴随）。
- **群体/领域边界**：结论主要基于干细胞（ESC、HSC、NPC等）研究，对其他细胞类型的普适性未充分讨论。
- **不确定性**：作者明确指出causality dilemma——染色质结构变化与基因表达变化的因果关系尚未解决。
- **有边界的复述**：本文主张，3D基因组结构（compartment、TAD、loop）在干细胞分化中发生动态重组织，这些变化与表观遗传修饰和LLPS转录凝聚体协同作用，共同塑造谱系特异性基因表达；但现有证据多为相关性，因果性需通过CRISPR等扰动实验进一步验证；AI模型和多组学整合是推动该领域从静态描述走向动态精准调控的关键工具。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 分辨率限制 | Hi-C通常1–5 kb，难以精确定位小规模调控元件互作 | Micro-C等新技术提高至核小体水平 | "Current Challenges" Resolution and Sensitivity Limitations 节 |
| 灵敏度不足 | 低频但功能重要的互作难以检测 | 改进检测方法、结合单分子成像 | 同上 |
| 活细胞成像局限 | 光漂白和光毒性限制长时间追踪 | 超分辨显微镜与测序方法整合 | 同上 |
| 重复序列分析困难 | 着丝粒、端粒等区域无法可靠分析 | 长读长测序、专门比对算法 | "Current Challenges" Difficulties in Analyzing Repetitive Genomic Regions 节 |
| 因果推断困难 | 染色质变化与分化结果多为相关性 | 结合CRISPR扰动、degron系统、时间序列分析 | "Current Challenges" The Causality Dilemma 节 |
| 单细胞数据稀疏 | scHi-C数据极度稀疏、噪声大 | 专门统计方法、机器学习降噪 | "Current Challenges" Complex Data Analysis Pipelines 节 |
| 多组学整合不成熟 | 现有工具缺乏跨组学整合能力 | 开发统一分析框架、标准化基准 | 同上 |
| 体内干预精度不足 | 系统性3D结构干预存在基因组不稳定风险 | 优化CRISPR-GO等工具的特异性和安全性 | "Future Directions" Engineered Intervention Strategies 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 综述将LLPS描述为转录调控的关键机制，但未讨论LLPS在体内的直接证据强度 | LLPS体外证据多，体内证据可能受固定/成像伪影影响；凝聚体可能是转录活性的结果而非原因 | 若LLPS非因果驱动，则基于相分离的治疗策略可能无效 | 使用光遗传学工具在活细胞中操纵凝聚体形成，观察转录变化的时间顺序 | Phase Separation 节；[Analysis] 基于领域内对LLPS证据强度的已知争议 |
| 综述主张AI模型可增强3D基因组分析，但未讨论模型的可解释性和泛化问题 | 深度学习模型可能在训练数据分布内表现好，但对新细胞类型或物种泛化差；"黑箱"特性限制生物学洞察 | 若模型不可解释，则难以从中提取可检验的机制假说 | 在独立数据集上交叉验证模型；使用可解释性工具（如注意力分析）检查模型关注的序列特征 | Future Directions 节；[Analysis] |
| 综述将compartment switching描述为分化驱动因素，但未讨论结构变化与转录变化的时序关系 | 结构变化可能滞后于转录变化，是转录的伴随现象而非驱动 | 若结构变化是结果，则靶向结构的治疗策略可能无效 | 高时间分辨率的多组学追踪（如等位基因特异Hi-C + RNA-seq） | Dynamic Rewiring 节；[Analysis] |
| 综述引用CRISPR-GO等工具作为验证因果性的手段，但未讨论这些工具的效率和组织特异性问题 | CRISPR-GO效率可能低，且系统性操作可能引入脱靶效应 | 若工具效率不足，则因果验证实验可能产生假阴性 | 系统比较不同细胞类型中CRISPR-GO的效率；结合单细胞读出来验证 | Future Directions 节；[Analysis] |
| 综述未讨论3D基因组结构在不同干细胞类型（如成体干细胞vs多能干细胞）中的差异 | 不同干细胞类型可能依赖不同的结构维持机制 | 若机制不同，则从ESC得到的结论不能直接推广到成体干细胞 | 跨细胞类型的系统比较研究 | 全文；[Analysis] |

## 14 学到什么
**Agent 提炼的知识候选**

1. **TF–DNA结合的结构背景框架**：本文系统梳理了compartment/TAD/loop的层级结构，为理解TF–DNA结合提供了空间背景——TF结合位点的可及性受3D结构调控，而非仅由线性序列决定。可迁移：在构建TF–DNA结合预测模型时，应纳入3D结构特征（如TAD边界距离、compartment类型）作为输入特征。

2. **CTCF/cohesin介导的loop extrusion模型**：CTCF作为边界因子和loop锚点，其结合位点方向性决定loop形成。可迁移：在TF–DNA结合预测中，CTCF共结合特征可作为重要特征；在物理模拟（如MD）中，可模拟CTCF–cohesin–DNA三元复合物的动态过程。

3. **LLPS与TF凝聚体的定量表征**：TF通过IDR介导相分离形成转录凝聚体，富集RNA Pol II和共激活因子。可迁移：在AI模型中，可将TF的IDR序列特征（氨基酸组成、电荷分布）作为预测TF凝聚体形成能力的输入；在物理模拟中，可用粗粒化模型模拟IDR介导的多价相互作用。

4. **多组学整合的分析范式**：Hi-C + ATAC-seq + ChIP-seq + RNA-seq的联合分析可建立结构-可及性-结合-表达的全链条关联。可迁移：在TF–DNA结合研究中，可构建多组学整合的深度学习框架，同时预测结合位点、染色质状态和表达变化。

5. **AI模型在3D基因组中的应用清单**：本文列举了SEE（超分辨率）、HiCFoundation（预训练大模型）、ChromoGen（结构生成）等工具。可迁移：这些模型的架构（如Transformer、扩散模型）可直接借鉴用于TF–DNA结合预测；HiCFoundation的预训练-微调范式可用于小样本TF结合数据。

6. **因果推断的实验设计**：本文强调causality dilemma，提出结合CRISPR扰动、degron系统和时间序列分析来建立因果关系。可迁移：在TF–DNA结合研究中，可通过CRISPR破坏预测的TF结合位点或loop锚点，验证结构-功能因果关系。

7. **单细胞3D基因组的分析挑战**：scHi-C数据稀疏、噪声大，需要专门统计方法。可迁移：在单细胞TF–DNA结合分析中，可借鉴Fast-Higashi等方法的降维和插补策略。

8. **重复序列区域的特殊处理**：本文指出重复区域是3D基因组分析的盲区。可迁移：在TF–DNA结合预测中，对重复区域的结合位点需特殊处理（如多映射读段的分配策略）。

## 15 与已有知识连接

- **与Hi-C技术发展脉络的连接**：本文引用的Hi-C、Micro-C、scHi-C、HiChIP等技术谱系，与Lieberman-Aiden et al. (2009) 的Hi-C原始方法、Rao et al. (2014) 的TAD/loop注释方法一脉相承。可进一步阅读Dixon et al. (2012) 关于TAD的经典定义，以及Beagan & Phillips-Cremins (2020) 关于3D基因组在发育中作用的综述。
- **与CTCF/cohesin机制的连接**：本文讨论的loop extrusion模型，可追溯到Fudenberg et al. (2016) 的loop extrusion理论、Sanborn et al. (2015) 的CTCF方向性规则。Nora et al. (2017) 的degron实验直接证明了cohesin在TAD形成中的因果作用。
- **与LLPS领域的连接**：本文关于转录凝聚体的讨论，与Hnisz et al. (2017) 提出的super-enhancer相分离模型、Sabari et al. (2018) 的活细胞凝聚体成像工作直接相关。Boija et al. (2018) 关于TF IDR驱动相分离的工作是本文论述的分子基础。
- **与AI/深度学习在基因组学应用的连接**：本文提及的HiCFoundation、ChromoGen等模型，属于基因组学中预训练大模型和生成模型的新趋势。可连接Zhou & Troyanskaya (2015) 的DeepSEA（序列-功能预测）、Avsec et al. (2021) 的Enformer（序列-表达预测）作为TF–DNA结合预测的基线方法。
- **与TF–DNA结合预测的连接**：本文虽未直接讨论TF–DNA结合预测，但其3D结构框架与经典的TF结合预测方法（如PWM、DeepBind、DeepSEA）形成互补——后者主要基于序列特征，本文提供了结构维度的补充。可迁移思路：将TAD/loop信息作为TF结合预测的结构先验。
- **与物理模拟的连接**：本文讨论的loop extrusion和LLPS机制，为分子动力学（MD）模拟和粗粒化模拟提供了建模目标。可连接Brackley et al. (2013) 的聚合物模拟、Chiariello et al. (2020) 的相分离-染色质耦合模拟。
- **候选方向（未验证）**：本文提出的"AI预测→CRISPR验证→模型迭代"闭环范式，可迁移到TF–DNA结合研究，但具体实施细节（如模型选择、验证标准）需进一步文献调研。

## 16 研究想法
**Agent 生成的研究候选**

---

**候选1：TF–DNA结合预测的3D结构增强模型**
- **名称**：Structure-Aware TF Binding Predictor (SATBP)
- **来源局限/观察**：现有TF–DNA结合预测主要基于序列特征（PWM、DeepBind等），忽略3D基因组结构对结合位点可及性的调控；本文指出TAD/loop结构决定enhancer-promoter互作，但未提供可计算的预测框架。
- **核心假设**：将TAD边界距离、compartment类型、CTCF共结合特征作为TF–DNA结合预测的附加输入，可显著提升预测精度，尤其在远距离调控位点。
- **初步方法**：以Enformer或DeepSEA为基线，在输入序列特征基础上加入3D结构特征（从Hi-C数据提取的TAD/loop注释、compartment状态）；用注意力机制融合序列和结构信息；在ENCODE TF ChIP-seq数据上训练和评估。
- **验证方式**：与序列-only基线比较AUPRC；在独立细胞类型上测试泛化；对预测错误的位点进行3D结构特征分析，确认结构特征是否提供互补信息。
- **创新状态**：partially checked（已有研究将Hi-C特征用于增强子-启动子预测，但用于TF–DNA结合预测的较少）

---

**候选2：CTCF–cohesin–DNA三元复合物的粗粒化MD模拟**
- **名称**：Coarse-Grained Simulation of CTCF-Cohesin-DNA Ternary Complex
- **来源局限/观察**：本文讨论了loop extrusion模型和CTCF方向性规则，但未涉及分子层面的物理模拟；TF–DNA结合的动态过程（如CTCF如何识别方向性motif）缺乏原子级理解。
- **核心假设**：CTCF的锌指结构域通过特定氨基酸残基识别方向性motif，cohesin的ATP水解驱动loop extrusion；粗粒化模拟可重现这一过程并预测突变效应。
- **初步方法**：基于MARTINI力场构建CTCF-DNA粗粒化模型；模拟CTCF结合方向性motif的动力学过程；引入cohesin环挤压机制，模拟loop extrusion的力学生物学。
- **验证方式**：与已知CTCF ChIP-seq数据比较结合位点预测；与Hi-C数据比较loop形成预测；设计CTCF突变体进行模拟，预测结合亲和力变化。
- **创新状态**：unverified（已有loop extrusion的聚合物模拟，但CTCF-DNA原子互作的粗粒化模拟较少）

---

**候选3：基于扩散模型的染色质结构生成与TF结合位点共预测**
- **名称**：Diffusion-Based Chromatin Structure Generator with TF Binding Co-Prediction (DiffChrom)
- **来源局限/观察**：本文指出AI模型（如ChromoGen）可生成3D结构，但未将结构生成与TF–DNA结合预测联合建模；TF结合位点与局部染色质结构存在双向关系。
- **核心假设**：扩散模型可学习序列-结构-结合位点的联合分布，生成结构的同时预测TF结合概率，比独立建模更准确。
- **初步方法**：以ChromoGen为基线，扩展为条件扩散模型：输入序列特征和TF motif，输出3D结构ensemble和结合位点概率；在GM12878等细胞系的Hi-C和ChIP-seq数据上训练。
- **验证方式**：结构生成质量（与实验Hi-C比较）；TF结合预测精度（与ChIP-seq比较）；生成结构的生物学合理性（TAD/loop富集检验）。
- **创新状态**：unverified（ChromoGen已实现结构生成，但联合TF结合预测未见报道）

---

**候选4：TF凝聚体形成的序列决定因子预测模型**
- **名称**：Sequence Determinants of TF Condensate Formation Predictor (SeqCond)
- **来源局限/观察**：本文讨论了LLPS介导的转录凝聚体在谱系定向中的作用，但未提供预测TF凝聚体形成能力的计算工具；TF的IDR序列特征（氨基酸组成、电荷分布）可能决定其相分离倾向。
- **核心假设**：TF的IDR序列特征（特别是芳香族残基含量、电荷模式、疏水性）可预测其形成转录凝聚体的能力，且与谱系定向功能相关。
- **初步方法**：收集已知相分离蛋白数据集（如PhaSepDB）；提取TF IDR序列特征；训练分类器（如XGBoost或深度学习）预测相分离倾向；与干细胞分化中TF功能数据关联分析。
- **验证方式**：交叉验证AUC；在独立相分离数据集上测试；与实验验证的凝聚体形成TF比较；分析预测高倾向TF是否富集于谱系决定基因。
- **创新状态**：partially checked（已有相分离预测工具如catGRANULE，但针对TF-IDR的专项预测较少）

---

**候选5：3D基因组结构变化的因果推断框架**
- **名称**：Causal Inference Framework for 3D Genome Rewiring in Differentiation (Causal3D)
- **来源局限/观察**：本文明确指出causality dilemma——染色质结构变化与基因表达变化的因果关系未解决；现有研究多为相关性分析。
- **核心假设**：结合CRISPR扰动数据（如CTCF敲除、cohesin降解）和时间序列Hi-C/RNA-seq数据，可构建因果图模型区分驱动与伴随关系。
- **初步方法**：整合CRISPR扰动前后的Hi-C和RNA-seq时间序列数据；使用因果发现算法（如PCMCI或DoWhy）构建结构-表达因果图；识别关键driver结构变化。
- **验证方式**：在已有数据集（如cohesin degron数据）上验证因果图与已知生物学一致性；预测新扰动实验的结果；与孟德尔随机化方法交叉验证。
- **创新状态**：unverified（因果推断在3D基因组领域应用较少，方法迁移有创新性）