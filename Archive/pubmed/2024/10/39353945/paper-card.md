## 01 基本信息

- **标题**：Molecular architecture and functional dynamics of the pre-incision complex in nucleotide excision repair
- **作者**：Yu, Jina; Yan, Chunli; Paul, Tanmoy; Brewer, Lucas; Tsutakawa, Susan E; Tsai, Chi-Lin; Hamdan, Samir M; Tainer, John A; Ivanov, Ivaylo
- **单位**：未提供（根据作者信息推测涉及美国多机构合作，具体单位未在摘要中列出）
- **期刊/平台**：Nature Communications
- **年份**：2024
- **论文类型**：研究论文（integrative modeling + MD simulation + network analysis）
- **领域**：结构生物学、DNA修复机制（核苷酸切除修复，NER）
- **关键词**：NER、pre-incision complex、cryo-EM、XL-MS、AlphaFold2、分子动力学模拟、动态网络分析
- **DOI/arXiv 号**：10.1038/s41467-024-52860-y
- **代码**：未提供
- **数据**：PDB ID: 6RO4, 6TUR, 6TUW, 6VBH, 5UM9, 6SXA, 6SXB, 2JNW, 4MQV, 1JMC, 1L1O, 4GOP, 6I52；EMDB: EMD-4970
- **阅读日期**：2026-05-12（按当前日期推算）
- **在课题方向中的位置**：本文虽非直接研究TF–DNA结合，但提供了**多亚基蛋白-DNA复合物**的整合建模范式（cryo-EM + XL-MS + AlphaFold2 + MD + 网络分析），其方法学可直接迁移至TF–DNA复合物的结构解析与动态研究。特别是**TFIIH作为分子尺子**的概念、**XPG桥接双切口**的机制，对理解TF如何协同其他因子实现精确DNA识别与切割具有重要参考价值。

---

## 02 一句话总结

本文通过整合cryo-EM、XL-MS和AlphaFold2构建了人类NER pre-incision complex（PInC）的近乎完整结构模型，结合微秒级MD模拟和动态网络分析，揭示了TFIIH作为分子尺子定义DNA bubble大小、XPG桥接3′/5′双切口并感知XPF切割事件的新机制，并将疾病突变映射到动态网络的关键界面上。

---

## 03 研究问题

- **具体问题**：NER通路中pre-incision complex（PInC）的完整三维结构是什么？XPG和XPF/ERCC1两个核酸酶如何在空间上协调实现精确的双切口（dual incision）？疾病突变如何通过破坏PInC的结构和动态来导致XP/CS表型？
- **为什么重要**：NER是修复紫外线、化学致癌物等引起的DNA损伤的关键通路。PInC是NER中决定"是否切割、在哪里切割"的核心决策复合物。理解其结构机制对于解释XP/CS等遗传病的分子病理至关重要。
- **现有方法为何不足**：此前缺乏PInC的完整结构——单个亚基或亚复合物的结构已有，但完整组装体的结构未知；cryo-EM密度中部分区域无法解析；XPG的spacer区域完全无实验结构；XPF/ERCC1在NER中的构象状态不清楚。
- **精确的"Can..."问题**：Can an integrative model combining cryo-EM, XL-MS, and AlphaFold2 predictions reveal the structural basis for coordinated dual incision in the NER pre-incision complex, and can MD-based dynamic network analysis explain the molecular pathology of XP/CS mutations?

---

## 04 背景与发展脉络

*注：此脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。*

1. **早期NER研究（~1990s-2000s）**：通过生化和遗传学鉴定NER核心因子（XPA、XPG、XPF/ERCC1、TFIIH、RPA等），建立"切割-修复"基本模型。局限：缺乏结构信息。
2. **单亚基/亚复合物结构解析（~2010s）**：cryo-EM和X-ray解析了apo-TFIIH、TFIIH/XPA/DNA、XPF/ERCC1、XPG催化核心等结构。局限：无法解释完整组装体中各因子的空间关系和协同机制。
3. **整合建模兴起（~2020s）**：AlphaFold2的出现使得预测无实验结构的区域成为可能；XL-MS提供远距离约束；cryo-EM提供整体密度框架。本文代表此阶段的典型方法——**"cryo-EM + XL-MS + AF2 + MD"四合一整合策略**。
4. **本文主张的位置**：首次构建了包含TFIIH、XPG、XPF/ERCC1、XPA、RPA和DNA的近乎完整PInC模型，并引入动态网络分析将结构-动态-疾病突变联系起来。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PInC完整结构缺失 | 无法解释双切口如何协调 | 单个亚基结构已有但组装体结构未知；XPG spacer区域无实验结构 | Results 节 "practically complete structural model" 的构建动机 |
| XPG spacer区域无法解析 | 该区域在cryo-EM密度中不可见 | 高度柔性/无序，难以用实验方法捕获 | Methods "Model building" 节：使用AlphaFold2预测该区域 |
| XPF/ERCC1在NER中的构象状态不明 | 已有结构为DNA-free或DNA-engaged状态，但NER中的具体构象未知 | 缺乏NER上下文中的结构约束 | Results 节对XPF/ERCC1构象转变的描述 |
| 疾病突变缺乏结构解释 | XP/CS突变分散在多个蛋白中，难以统一解释 | 缺乏完整组装体结构来映射突变位置 | Results 节 "Mapping disease mutations" 部分 |
| 动态信息缺失 | 静态结构无法解释"切割许可"的动态过程 | 结构方法提供静态快照，缺乏功能动态信息 | 引入MD模拟和动态网络分析的动机 |

---

## 06 核心思想

### 1) 表面方法
整合cryo-EM密度、XL-MS交联约束、AlphaFold2结构预测，构建PInC的近乎完整原子模型；随后进行1μs级MD模拟，并基于MD轨迹做动态网络分析（community detection + betweenness centrality）来识别功能相关的动态模块。

### 2) 核心洞察
- **TFIIH作为分子尺子**：TFIIH的闭合环状构象定义了DNA bubble的大小（23 nt），从而精确控制XPG和XPF/ERCC1的切割位点间距。
- **XPG桥接双切口**：XPG的spacer区域使其能够同时接触3′和5′两个DNA junction，从而在空间上"感知"XPF/ERCC1在5′端的切割事件，实现双切口的顺序协调。
- **动态模块而非静态结构决定功能**：PInC的22个动态community中，疾病突变富集在community界面上，说明突变通过破坏模块间的动态耦合来致病。

### 3) 可能的普适教训 [Analysis]
- **"分子尺子"概念可推广**：任何需要精确空间定位的多酶复合物（如TF–DNA + 共调控因子）都可能存在一个"结构骨架"来定义底物长度或切割位点间距。
- **整合建模是处理柔性区域的有效策略**：当实验结构无法解析关键功能区域时，AF2预测 + 交联约束 + MD验证的三步策略可提供可检验的假设。
- **动态网络分析将结构-突变-表型联系起来**：将疾病突变映射到动态community界面而非静态结构表面，可能比传统"突变位于活性位点"的解释更具解释力。

---

## 07 方法总览

- **输入**：
  - cryo-EM结构/密度：apo-TFIIH (PDB 6RO4等)、TFIIH/XPA/DNA (EMD-4970)、XPF/ERCC1 (6SXA, 6SXB)
  - X-ray结构：XPG催化核心 (6TUR, 6TUW, 6VBH)、RPA-ssDNA (4GOP, 6I52, 1JMC, 1L1O)、XPA/ERCC1 (2JNW)、RPA32C/Smarcal1 (4MQV)
  - XL-MS交联数据（来自TFIIH/XPA/DNA研究）
  - AlphaFold2预测：XPG spacer区域、XPA N-末端等无实验结构区域
  - 疾病突变数据（XP/CS相关）

- **输出**：
  - PInC完整原子模型（含DNA）
  - MD轨迹（1μs × 3体系：PInC、LSC、apo-TFIIH）
  - 动态网络图（22个community）
  - 疾病突变的结构-动态映射

- **模块**：
  1. 模型构建（Model building）：基于实验结构 + AF2预测 + XL-MS约束的逐步组装
  2. MD模拟：AMBER力场（Parm14SB + OL15），NAMD 2.14，TIP3P水，150mM盐，1μs生产模拟
  3. 动态网络分析：基于MD轨迹的协方差矩阵 → 网络图 → Girvan-Newman community detection
  4. PCA：识别主要运动模式
  5. Rosetta ddG：评估突变对蛋白稳定性的影响

- **训练**：无监督学习/无训练过程（非ML方法）；AF2为预训练模型直接推理

- **反馈回路**：XL-MS约束指导模型构建 → MD验证模型稳定性 → 网络分析识别关键界面 → 突变映射验证生物学相关性

- **假设**：
  - XL-MS交联反映溶液中的真实空间邻近关系
  - AF2预测的柔性区域结构在PInC上下文中保持其折叠
  - MD模拟（1μs）足以捕获PInC的功能相关动态
  - 动态community反映功能模块

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 整合模型构建 | 将多个实验结构+预测结构组装为完整PInC | 单一实验方法无法提供完整结构 | 输入：各亚基结构、XL-MS约束、AF2预测；输出：PInC原子模型 | Results 图1；模型与XL-MS数据一致 | 无模型则无法进行后续MD和网络分析（预期影响） |
| AlphaFold2预测 | 预测XPG spacer、XPA N-末端等无结构区域 | 这些区域在实验密度中不可见但对功能关键 | 输入：氨基酸序列；输出：预测结构+plDDT | Results 图2c-d；plDDT值报告 | 移除后PInC模型不完整，XPG桥接机制无法揭示（预期影响） |
| MD模拟 | 揭示PInC的动态行为和稳定性 | 静态结构无法解释功能动态 | 输入：PInC/LSC/apo-TFIIH模型；输出：1μs轨迹 | Results 图S6；B-factor分析 | 无MD则无法进行动态网络分析（预期影响） |
| 动态网络分析 | 将PInC划分为功能相关的动态community | 识别协同运动的模块和关键通信界面 | 输入：MD轨迹协方差矩阵；输出：22个community + betweenness图 | Results 图6；community结构与已知功能域对应 | 移除后无法将突变与动态界面关联（预期影响） |
| PCA | 识别PInC的主要集体运动模式 | 理解大尺度构象变化的方向性 | 输入：MD轨迹；输出：主成分模式 | Results 图S7 | 移除后仍可进行网络分析，但失去运动方向信息（预期影响） |
| Rosetta ddG | 评估疾病突变对蛋白稳定性的影响 | 区分"稳定性破坏"与"界面破坏"两种突变机制 | 输入：突变体结构；输出：ddG值 | Results 图S9；XPG突变ddG显著更高 | 移除后无法区分突变机制（预期影响） |

---

## 09 关键公式符号

1. **网络边权重（协方差加权）**：
   \[
   w_{i,j} = -\ln(|c_{i,j}|)
   \]
   - \( w_{i,j} \)：残基i和j之间的网络边权重
   - \( c_{i,j} \)：残基i和j的成对相关（协方差）系数
   - 用途：将MD轨迹中的运动相关性转化为网络图中的边权重，用于community detection
   - 直觉：相关性越强（|c|越接近1），权重越小（w越接近0），在Girvan-Newman算法中越不容易被移除

2. **Girvan-Newman算法**（未给出具体公式，但为社区发现的标准方法）：
   - 通过迭代移除边介数（edge betweenness）最高的边来划分community
   - 用途：将PInC划分为22个动态community

3. **Rosetta ddG**（未给出具体公式）：
   - ddG = ΔG_mutant - ΔG_wildtype
   - 正值表示突变降低蛋白稳定性
   - 用途：评估疾病突变对蛋白稳定性的影响

---

## 10 实验设计与证据链

### 数据集/群体
- **结构数据**：6个实验结构（cryo-EM + X-ray + NMR）+ 2个AF2预测区域
- **XL-MS数据**：来自TFIIH/XPA/DNA复合物研究（具体交联对数量未在摘要中提供）
- **MD模拟体系**：3个（PInC、LSC、apo-TFIIH），各1μs
- **疾病突变**：XP、XP/CS、TTD相关突变（具体数量未在摘要中提供，见补充表1）

### 指标
- plDDT（AF2预测置信度）
- B-factor（MD模拟的残基灵活性）
- 动态community划分
- 边介数（betweenness）
- Rosetta ddG值

### 基线/对比
- PInC vs LSC vs apo-TFIIH的MD比较
- 突变体 vs 野生型的ddG比较

### 评测协议
- 模型与XL-MS交联数据的一致性检验
- MD模拟的结构稳定性评估
- 突变在结构上的空间聚类分析

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| 整合模型构建 | PInC可被构建为完整结构 | 多来源数据整合 | 成功构建含23-nt bubble的PInC模型 | PInC的完整结构可被确定 | 模型精度未与实验结构直接比较 | Results 图1 |
| XPG锚定域拟合 | XPG锚定域占据cryo-EM密度 | AF2预测结构 vs 实验密度 | 完美匹配侧链密度 | XPG锚定域在PInC中的位置确定 | 该域的动态构象可能不止一种 | Results 图2c |
| MD模拟 | PInC在1μs内保持稳定 | PInC vs LSC vs apo-TFIIH | PInC的B-factor显著低于LSC | PInC比LSC更刚性 | 1μs不足以覆盖所有功能相关构象变化 | Results 图S6 |
| 动态网络分析 | PInC可划分为功能community | 协方差矩阵 → 网络图 | 22个community，XPG核心分为M/R两个community | 动态模块跨越亚基边界 | community划分对算法参数敏感 | Results 图6 |
| 疾病突变映射 | 突变富集在community界面 | 突变位置 vs community边界 | XPG核心突变富集在M/R界面 | 突变通过破坏动态耦合致病 | 未做突变体MD验证 | Results 图7 |
| Rosetta ddG | XPG突变降低蛋白稳定性 | 突变体 vs 野生型 | XPG突变ddG显著更高 | XPG突变主要通过去稳定化致病 | ddG预测与体内稳定性相关性未验证 | Results 图S9 |

---

## 11 结论正确解读

- **任务范围**：本文仅针对GG-NER亚通路的PInC阶段，不涉及TC-NER、损伤识别早期步骤或修复后期（合成、连接）。
- **oracle/真值输入**：模型构建依赖实验结构（cryo-EM密度、X-ray、NMR）和XL-MS交联约束作为"真值"；AF2预测仅用于填补无实验数据的区域。
- **端到端状态**：**非端到端**。模型是整合的而非单一方法从头构建；MD和网络分析是验证和解释手段，非结构预测本身。
- **算力成本**：MD模拟在Summit超级计算机（ORNL）上运行，1μs × 3体系，具体节点时数未提供。
- **历史数据依赖**：依赖已发表的实验结构（PDB）和XL-MS数据；AF2预训练模型隐含依赖PDB训练集。
- **模型依赖**：结果依赖于AF2预测的准确性（plDDT报告）、MD力场选择（Parm14SB/OL15）和网络分析参数（接触阈值4.5Å/75%）。
- **最难情形**：XPG spacer区域（~600残基）完全无实验结构，其建模完全依赖AF2预测，不确定性最高。
- **群体/领域边界**：结论基于人类蛋白序列和结构；其他物种的NER机制可能不同。疾病突变分析限于XP/CS/TTD相关突变。
- **不确定性**：作者未提供模型与实验结构的定量比较（如RMSD）；MD采样可能未覆盖所有功能相关构象；动态community划分的稳健性未系统评估。

**有边界的复述**：本文基于现有实验结构+交联数据+AF2预测，构建了人类GG-NER PInC的整合模型，并通过MD和网络分析提出TFIIH定义bubble大小、XPG桥接双切口并感知5′切割的机制假说；该假说在1μs MD模拟和突变映射层面得到支持，但未经突变体功能实验或更高分辨率结构直接验证。

---

## 12 作者自认局限

在提供的摘要和正文中，作者明确承认的局限较少，主要包括：

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| XPF/ERCC1的SF2解旋酶样N端结构域未纳入模型 | "The SF2 helicase-like N-terminal domain of XPF was omitted from the hybrid PInC model due to lack of sufficient structural or biochemical restraints" | 未明确提及 | Methods "Model building" 节 |
| XPG spacer区域无实验结构 | 该区域完全依赖AF2预测 | 未明确提及 | Methods "Model building" 节 |
| 模型是静态快照 | 整合模型本身不包含动态信息 | 通过MD模拟补充 | Results 节 |

**作者提及的相关约束**（非正式局限）：
- XL-MS数据来自TFIIH/XPA/DNA复合物，可能不完全代表PInC中的交联状态
- 疾病突变分析限于错义突变，未涵盖截短突变或调控区突变
- MD模拟仅1μs，可能不足以捕获所有功能相关构象变化

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| XPG锚定域"完美匹配"cryo-EM密度 | 该密度可能来自其他蛋白（如p62）而非XPG锚定域；AF2预测可能过拟合 | 锚定域位置是XPG桥接机制的关键证据 | 用XPG特异性抗体进行cryo-EM验证；或突变锚定域关键残基后观察PInC组装变化 | Results 图2c |
| 动态community划分依赖MD力场和参数选择 | 不同力场/参数可能产生不同community结构 | community划分是突变聚类分析的基础 | 使用不同力场（如CHARMM36）和不同接触阈值重复分析 | Methods "Covariance-based community network analysis" 节 |
| 疾病突变"聚类在community界面"可能是偶然 | 突变在蛋白表面的分布本身可能不均匀 | 该结论是"突变通过破坏动态耦合致病"假说的核心 | 用随机突变集做置换检验（permutation test） | Results 图7 |
| Rosetta ddG预测与实验稳定性数据未验证 | ddG预测误差可能较大，尤其对界面残基 | 突变"去稳定化"结论依赖ddG准确性 | 用差示扫描荧光法（DSF）或圆二色谱（CD）验证代表性突变体的热稳定性 | Results 图S9 |
| 模型未包含翻译后修饰（PTM） | 磷酸化、泛素化等PTM可能调控PInC组装和活性 | PTM是NER调控的重要机制 | 在模型中纳入已知PTM位点并重新评估 | 未提供 |
| 仅一个构象状态被建模 | PInC可能经历多个功能相关构象状态 | 单一构象可能无法解释"切割许可"的动态过程 | 使用增强采样MD（如replica exchange）探索构象空间 | 未提供 |

---

## 14 学到什么

### Agent 提炼的知识候选

1. **整合建模策略（可直接迁移）**
   - **概念**：cryo-EM密度 + XL-MS交联约束 + AF2预测 + MD验证的四步整合策略
   - **迁移到TF–DNA研究**：当TF–DNA复合物的cryo-EM密度分辨率不足以解析柔性区域（如激活域、DNA结合域之间的linker）时，可用XL-MS提供远距离约束，AF2预测缺失区域，MD验证模型稳定性
   - **操作**：先收集所有可用的实验结构数据 → 用XL-MS确定亚基间/结构域间邻近关系 → AF2填补缺失区域 → 组装后做MD验证

2. **"分子尺子"概念**
   - **概念**：TFIIH的闭合环状构象通过物理尺寸定义DNA bubble长度（23 nt），从而控制切割位点间距
   - **迁移到TF–DNA研究**：TF如何通过其结构尺寸"测量"DNA结合位点间距？例如，增强子-启动子环化中，TF二聚体或多聚体的空间尺寸可能决定DNA loop的长度
   - **操作**：分析TF多聚体结构中DNA结合域之间的空间距离，与已知的DNA结合位点间距进行关联

3. **动态网络分析（community detection）**
   - **概念**：基于MD轨迹的协方差矩阵构建网络图，用Girvan-Newman算法划分动态community，识别功能模块和关键通信界面
   - **迁移到TF–DNA研究**：TF的DNA结合域、二聚化域、调控域可能属于不同的动态community，突变通过破坏community间通信来影响功能
   - **操作**：对TF–DNA复合物做MD模拟 → 计算残基间协方差 → 构建网络图 → 识别community → 将已知功能突变映射到community界面

4. **"XPG桥接双切口"的协同感知机制**
   - **概念**：一个蛋白（XPG）通过其空间延伸同时接触两个DNA junction，从而感知另一个核酸酶（XPF）的切割事件
   - **迁移到TF–DNA研究**：TF可能通过类似机制"感知"远端调控元件的状态——例如，一个TF二聚体同时接触两个DNA位点，当其中一个位点被其他因子占据或修饰时，TF通过构象变化传递信号
   - **操作**：在TF–DNA复合物结构中检查是否存在单一蛋白结构域同时接触两个DNA位点的可能性

5. **疾病突变的功能分类框架**
   - **概念**：将突变分为"破坏稳定性"（高ddG）和"破坏动态界面"（位于community边界）两类
   - **迁移到TF–DNA研究**：对TF相关疾病突变（如癌症中的TF突变）进行类似分类，可能揭示不同突变机制
   - **操作**：收集TF相关疾病突变 → 映射到TF–DNA复合物结构 → 计算ddG + 动态网络分析 → 分类突变机制

6. **MD模拟的体系设计**
   - **概念**：对同一复合物的不同状态（PInC vs LSC vs apo）做平行MD，通过比较B-factor和动态模式来识别功能相关构象变化
   - **迁移到TF–DNA研究**：对TF的DNA结合态 vs 游离态、或TF–DNA复合物 vs TF–DNA–共调控因子三元复合物做平行MD，比较动态差异
   - **操作**：构建多个状态的原子模型 → 相同MD参数平行模拟 → 比较B-factor、community结构、PCA主成分

---

## 15 与已有知识连接

- **TFIIH在NER中的双重角色**：本文与已知的TFIIH在转录和NER中的双重功能一致（Compe & Egly, 2016, *Nat Rev Mol Cell Biol*）。本文进一步揭示了TFIIH在NER中作为结构骨架的"分子尺子"角色。
- **XPG的FEN1家族特征**：本文利用XPG与FEN1的30%序列同一性，基于FEN1-DNA结构建模XPG-DNA相互作用。这与已知的FEN1家族底物识别机制（Tsutakawa et al., 2011, *Cell*）一致。
- **XPA作为"损伤验证者"**：本文支持XPA在NER中的中心协调角色（Sugasawa, 2010, *DNA Repair*），并进一步展示了XPA如何通过多结构域纠缠将RPA、XPF/ERCC1和TFIIH连接在一起。
- **AlphaFold2在复合物建模中的应用**：本文是AF2应用于大型多亚基复合物建模的代表性案例，与AlphaFold-Multimer（Evans et al., 2022）的方法论一致。
- **动态网络分析在蛋白复合物研究中的应用**：本文的方法与Luthey-Schulten组在核糖体动态网络分析中的工作（Sethi et al., 2009, *PNAS*）方法学上一致。
- **与TF–DNA研究的相关性**：本文的"整合建模 + MD + 网络分析"策略与近期TF–DNA复合物研究（如p53–DNA、NF-κB–DNA）中的方法高度相似，但本文展示了在更大、更复杂复合物中的应用。

---

## 16 研究想法

### Agent 生成的研究候选

**候选1：TF–DNA复合物的"分子尺子"机制研究**
- **名称**：Transcription factor dimer spacing as a molecular ruler for DNA binding site selection
- **来源局限/观察**：本文发现TFIIH通过结构尺寸定义DNA bubble长度。类似地，TF二聚体（如bZIP、bHLH家族）的DNA结合域间距可能决定其识别的DNA位点间距
- **核心假设**：TF二聚体的结构间距与其识别的DNA位点半周期间距存在精确匹配，且该匹配是TF–DNA结合特异性的重要决定因素
- **增量**：将"分子尺子"概念从NER扩展到TF–DNA识别
- **初步方法**：收集bZIP/bHLH家族TF–DNA共晶结构 → 测量DNA结合域间距 → 与DNA位点间距关联 → MD模拟验证
- **验证方式**：突变TF二聚化界面改变间距 → 检测DNA结合特异性变化（EMSA、SELEX）
- **创新状态**：partially checked（已有部分结构生物学证据，但未系统验证）

**候选2：TF–DNA复合物的动态网络分析框架**
- **名称**：Dynamic community analysis of TF–DNA complexes for functional annotation of disease mutations
- **来源局限/观察**：本文将疾病突变映射到PInC的动态community界面，发现突变富集在界面而非活性位点。类似方法可应用于TF–DNA复合物中的癌症突变
- **核心假设**：TF相关癌症突变通过破坏TF–DNA复合物的动态community通信（而非直接破坏DNA结合）来致病
- **增量**：将动态网络分析从NER扩展到TF–DNA研究
- **初步方法**：选择p53、MYC、TP63等TF → 构建TF–DNA复合物模型 → MD模拟 → 动态网络分析 → 映射癌症突变
- **验证方式**：对预测破坏community界面的突变体做功能实验（转录活性报告基因、ChIP-seq）
- **创新状态**：unverified

**候选3：整合建模方法迁移——TF–共调控因子–DNA三元复合物**
- **名称**：Integrative modeling of TF–cofactor–DNA ternary complexes using cryo-EM + XL-MS + AF2
- **来源局限/观察**：本文展示了整合建模在大型多亚基复合物中的可行性。TF–共调控因子–DNA三元复合物（如增强子-启动子环化中的复合物）同样面临柔性区域无法解析的问题
- **核心假设**：整合建模策略可成功应用于TF–共调控因子–DNA三元复合物，揭示共调控因子如何调控TF的DNA结合特异性
- **增量**：将整合建模从DNA修复扩展到基因调控
- **初步方法**：选择p53–p300–DNA或MYC–MAX–DNA系统 → 收集cryo-EM密度 + XL-MS数据 → AF2预测缺失区域 → 组装 + MD验证
- **验证方式**：与已知突变功能数据交叉验证；设计突变体做功能实验
- **创新状态**：unverified

**候选4：TF–DNA结合动力学的MD模拟比较研究**
- **名称**：Comparative MD simulations of TF–DNA binding: free vs bound vs ternary complex states
- **来源局限/观察**：本文对PInC、LSC和apo-TFIIH做了平行MD，通过比较B-factor和动态模式识别功能相关构象变化。类似策略可应用于TF–DNA系统
- **核心假设**：TF–DNA复合物的动态模式（而非静态结构）决定其结合亲和力和特异性
- **增量**：将"多状态平行MD比较"策略从NER扩展到TF–DNA
- **初步方法**：选择3-5个TF–DNA系统 → 构建游离TF、TF–DNA二元复合物、TF–DNA–共调控因子三元复合物 → 各1μs MD → 比较B-factor、community结构、PCA
- **验证方式**：MD预测的动态热点与突变功能数据比较
- **创新状态**：partially checked（已有TF–DNA MD研究，但缺乏系统多状态比较）

**候选5：TF–DNA复合物中"切割许可"类似机制的探索**
- **名称**：Allosteric communication pathways in TF–DNA complexes: sensing distal regulatory events
- **来源局限/观察**：本文发现XPG通过桥接双切口感知XPF的切割事件。类似地，TF可能通过变构通路感知远端DNA位点的状态（如甲基化、其他因子结合）
- **核心假设**：TF–DNA复合物中存在从远端DNA位点到转录激活域的变构通信通路
- **增量**：将"变构感知"概念从DNA修复扩展到基因调控
- **初步方法**：选择含多个DNA结合域的TF（如CTCF、YY1）→ 动态网络分析识别变构通路 → 突变通路关键残基 → 检测转录活性变化
- **验证方式**：突变体功能实验 + HDX-MS验证构象变化
- **创新状态**：unverified