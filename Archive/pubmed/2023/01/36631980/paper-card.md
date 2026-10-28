## 01 基本信息

- **标题**：The homeodomain of Oct4 is a dimeric binder of methylated CpG elements
- **作者与单位**：Tan, Daisylyn Senna; Cheung, Shun Lai; Gao, Ya; Weinbuch, Maike; Hu, Haoqing; Shi, Liyang; Ti, Shih-Chieh; Hutchins, Andrew P; Cojocaru, Vlad; Jauch, Ralf（单位未在摘要中提供）
- **期刊/预印本平台**：Nucleic Acids Research
- **年份**：2023-01-13
- **论文类型**：研究论文（实验+计算+结构生物学）
- **领域**：转录因子-DNA互作；表观遗传学（DNA甲基化）；结构生物学
- **关键词**：Oct4、POU结构域、homeodomain、甲基化CpG、二聚化、先驱转录因子
- **DOI/arXiv 号**：10.1093/nar/gkac1262
- **代码**：未提供
- **数据**：PDB ID: 7XRC；Zenodo: https://zenodo.org/record/7436073；XRDa ID: XRD-00080
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦于转录因子Oct4（POU家族）对甲基化CpG元件（CpGpal）的二聚化结合机制，属于「TF–DNA结合机制 × 结构生物学/分子模拟」方向。其核心发现——POUHD单独驱动二聚化结合甲基化DNA、POUS结构域脱离DNA——为理解TF如何识别甲基化DNA提供了新的结构机制，对AI/深度学习预测TF-DNA结合（尤其是甲基化状态下的结合）和分子动力学模拟方法均有直接参考价值。

---

## 02 一句话总结

本文通过生化结合实验、晶体结构和分子动力学模拟，证明Oct4的POU同源结构域（POUHD）能以正协同方式二聚化结合含甲基化CpG核心的紧凑回文元件CpGpal，且该结合不依赖POU特异性结构域（POUS），而Brn2等其他POU因子无法有效结合该元件。

---

## 03 研究问题

- **具体问题**：Oct4如何识别并结合含甲基化CpG的DNA元件（CpGpal，序列ATGCGCAT）？其结合模式与已知的Oct4/Octamer或Oct4/MORE结合模式有何不同？该能力是否为Oct4所特有？
- **为什么重要**：Oct4是维持多能性和重编程的关键先驱转录因子。传统观点认为DNA甲基化排斥TF结合，但Oct4被报道可结合甲基化DNA。理解其分子机制对阐明先驱因子如何在关闭的染色质上发挥功能至关重要。
- **现有方法为何不足**：此前仅通过SELEX和ChIP-seq发现Oct4偏好CpGpal元件，但缺乏结构层面的解释；且不清楚该结合是否依赖POUS、是否具有协同性、是否为Oct4特有。
- **精确研究问题**：Can the POU homeodomain of Oct4 alone drive cooperative dimerization on methylated CpGpal elements, and is this binding mode unique to Oct4 among POU factors?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及引用，属于「经外部核验」的领域共识，但具体叙述框架为本文作者构建。

1. **经典模型：CpG甲基化排斥TF结合**（5,6）：早期认为5mC通过空间位阻或改变DNA结构阻止TF结合，这是甲基化导致转录抑制的机制之一。
2. **修正模型：部分TF偏好甲基化DNA**（7–10）：SELEX等研究发现一类「methyl-plus」TF（如Oct4、HOXB13等）反而被甲基化DNA吸引。但机制不清。
3. **Oct4的已知结合模式**：Oct4通过POU结构域（POUS + POUHD）结合Octamer（ATGCAAAT）或与Sox2形成二聚体结合SoxOct元件；在MORE/PORE回文元件上可形成同源二聚体，但协同性弱于POU3因子（如Brn2）。
4. **本文位置**：在「methyl-plus TF」框架下，首次提出Oct4通过POUHD单独介导的二聚化结合甲基化CpGpal，且该模式与已知的POU二聚化模式（依赖POUS-POUHD互作）不同，属于新的结合范式。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 甲基化DNA如何被TF识别 | 传统模型认为5mC排斥TF，但Oct4等可结合甲基化DNA | 作者认为Oct4通过POUHD二聚化识别CpGpal，POUS脱离DNA，避免空间冲突 | Results 图4-6；结构模型 |
| Oct4结合CpGpal的分子机制不清 | 仅知SELEX偏好，不知结合模式 | 缺乏结构信息；POUS与POUHD的分工不明 | 引言；Results 图5 |
| Oct4与Brn2功能差异的分子基础 | Brn2无法有效结合CpGpal | POUHD序列差异（尤其N端RK motif）导致二聚化协同性不同 | Results 图4E, 5C |
| 甲基化CpGpal位点在重编程中不被去甲基化 | 多数Oct4位点去甲基化，但CpGpal位点保持甲基化 | Oct4结合CpGpal不诱导去甲基化，可能维持沉默状态 | Results 图2D-F |
| 先驱因子模型与甲基化DNA的矛盾 | 先驱因子应打开染色质，但CpGpal位点保持关闭 | 作者提出Oct4在CpGpal上的功能可能不依赖染色质打开 | Discussion |

---

## 06 核心思想

### 1) 表面方法
- 纯化Oct4和Brn2的POU结构域及亚结构域（POUHD、POUS），用EMSA检测与甲基化/非甲基化CpGpal DNA的结合。
- 解析Brn2/MORE复合物晶体结构（1.89 Å），并基于已知POU/DNA结构构建Oct4/CpGpal二聚体模型。
- 对两种构型进行470 ns分子动力学（MD）模拟。
- 重分析已发表的ChIP-seq、WGBS、ATAC-seq数据，评估CpGpal在重编程中的动态。

### 2) 核心洞察
- **POUHD单独驱动二聚化**：Oct4的POUHD足以在CpGpal上形成同源二聚体，且具有正协同性（ω > 1）；POUS不参与DNA接触，反而可能因空间位阻降低结合。
- **甲基化不改变结合模式**：5mC/5hmC修饰对二聚化无显著影响，说明识别机制不依赖甲基基团的特异性接触，而是通过形状读码（shape readout）和间接读码。
- **Oct4特异性**：Brn2的POUHD在CpGpal上二聚化协同性极低，解释了为何其他POU因子不结合该元件。
- **功能意义**：CpGpal位点在重编程中保持甲基化，Oct4可能通过POUHD二聚化在沉默染色质上发挥调控作用，挑战了先驱因子必须打开染色质的简单模型。

### 3) 可能的普适教训 [Analysis]
- **结构域分工的可塑性**：同一TF的不同DNA结合结构域可在不同DNA元件上承担不同角色（POUS在Octamer上结合DNA，在CpGpal上脱离DNA），提示AI预测TF结合位点时需考虑结构域级别的构象状态。
- **甲基化识别的间接机制**：TF对甲基化DNA的偏好可能不通过直接接触甲基基团，而是通过DNA形状（如MGW变窄）实现——这对基于序列的深度学习模型是重要提示：需纳入DNA结构特征。
- **协同性作为特异性来源**：二聚化协同性（ω）的差异可能是TF家族成员功能分化的关键参数，值得在建模中显式编码。

---

## 07 方法总览

- **输入**：纯化的Oct4/Brn2 POU结构域及亚结构域蛋白；合成的甲基化/非甲基化CpGpal、Octamer、MORE DNA探针；已发表的ChIP-seq/WGBS/ATAC-seq数据。
- **输出**：结合亲和力与协同性参数（EMSA）；Brn2/MORE晶体结构（PDB 7XRC）；Oct4/CpGpal二聚体结构模型；MD模拟轨迹；基因组位点甲基化/染色质状态注释。
- **模块**：
  1. 蛋白表达纯化（大肠杆菌）
  2. EMSA结合实验（含单管双色竞争实验）
  3. 晶体筛选与结构解析（X射线衍射）
  4. 同源建模（基于Brn2/MORE结构）
  5. MD模拟（470 ns，AMBER）
  6. 生物信息学重分析（ChIP-seq peak calling、motif扫描、WGBS甲基化提取、ATAC-seq）
- **训练**：不适用（无监督学习/物理模拟）
- **工具**：XDSapp、Phaser、Phenix、Coot、AMBER、bowtie2、MACS2、HOMER、bedtools等
- **反馈回路**：结构模型→MD模拟→稳定性验证→与EMSA结果交叉验证
- **假设**：POUHD在CpGpal上的结合模式与MORE类似（基于序列相似性）；MD模拟的力场参数适用于甲基化DNA。

**文字流程**：  
纯化蛋白 → EMSA验证全长POU及亚结构域结合 → 确定POUHD为关键结构域 → 解析Brn2/MORE结构作为模板 → 构建Oct4/CpGpal模型（两种构型）→ MD模拟验证稳定性 → 结合ChIP-seq/WGBS数据评估基因组相关性 → 整合得出结论。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| EMSA结合实验 | 定量检测蛋白-DNA结合亲和力与协同性 | 验证POUHD是否足以驱动二聚化；比较Oct4 vs Brn2 | 输入：纯化蛋白+荧光标记DNA；输出：结合分数、协同性因子ω | Results 图4B-E, 5B-C | 无法区分亚结构域贡献；无法确定协同性 |
| 单管双色竞争EMSA | 直接比较不同蛋白对同一DNA的偏好 | 排除实验间差异，确认Oct4 vs Brn2的差异 | 输入：两种蛋白+两种标记DNA；输出：相对结合偏好 | Results 图S5B-D | 无法定量绝对亲和力 |
| 晶体结构解析（Brn2/MORE） | 提供原子分辨率的结构模板 | 为Oct4/CpGpal建模提供参考 | 输入：Brn2 POU + MORE DNA晶体；输出：1.89 Å结构（PDB 7XRC） | Results 图6B-C | 无法直接获得Oct4/CpGpal实验结构 |
| 同源建模 | 构建Oct4/CpGpal二聚体模型 | 解释POUHD如何二聚化结合CpGpal | 输入：Brn2/MORE结构+序列比对；输出：两种构型模型 | Results 图6D-F | 模型可靠性依赖模板相似性 |
| MD模拟 | 验证模型稳定性 | 排除不合理的构型 | 输入：模型+AMBER力场；输出：470 ns轨迹、RMSD/RMSF | Results 图S8F | 无法证明模型是唯一正确构型 |
| ChIP-seq重分析 | 评估CpGpal在基因组中的占用 | 将体外发现与体内数据关联 | 输入：16个已发表数据集；输出：motif富集、peak注释 | Results 图1, 2 | 无法区分直接/间接结合 |
| WGBS/ATAC-seq整合 | 分析CpGpal位点的甲基化与染色质状态 | 检验CpGpal是否保持甲基化 | 输入：重编程时间序列数据；输出：甲基化/可及性动态 | Results 图2C-G | 相关性不等于因果性 |

---

## 09 关键公式符号

本文未使用复杂数学公式，核心定量概念为协同性因子（cooperativity factor）：

- **ω（协同性因子）**：描述二聚体结合中两个单体结合事件之间的耦合程度。ω > 1 表示正协同（第一个单体结合增强第二个单体结合）；ω = 1 表示独立结合；ω < 1 表示负协同。
- **K_d（解离常数）**：用于描述单体结合亲和力，EMSA定量中通过结合等温线拟合获得。
- **ΔG（结合自由能）**：MD模拟中通过MM-PBSA/GBSA方法估算（文中提及但未给出具体数值）。

> 注：文中未给出具体公式推导，以上为领域通用定义。来源：Methods（EMSA定量部分）、Results 图4C。

---

## 10 实验设计与证据链

### 数据集/群体/规模/指标/基线/预算/仪器/评测协议

| 项目 | 详情 |
|------|------|
| 蛋白样本 | 小鼠Oct4（残基131–289）、Brn2（残基264–421）的POU结构域及亚结构域（POUHD、POUS） |
| DNA探针 | CpGpal（ATGCGCAT）、Octamer（ATGCAAAT）、MORE（ATGCATATGCAT），含甲基化/非甲基化版本 |
| 细胞实验 | HEK293T转染全长Oct4；OG2-MEF重编程体系 |
| 基因组数据 | 16个已发表ChIP-seq数据集（小鼠/人ESC、重编程时间序列）、WGBS、ATAC-seq |
| 结构数据 | Brn2/MORE晶体（1.89 Å，PDB 7XRC） |
| 计算资源 | Max Planck计算设施（MD模拟） |
| 指标 | EMSA结合分数、协同性因子ω、ChIP-seq peak富集、motif出现频率、甲基化百分比 |
| 基线 | Brn2作为对照POU因子；非甲基化DNA作为对照底物 |
| 评测协议 | 标准化ChIP-seq分析流程（bowtie2→MACS2→HOMER motif扫描）；WGBS用bismark处理 |

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| EMSA滴定（Oct4 POU vs CpGpal） | Oct4结合CpGpal | 甲基化 vs 非甲基化DNA | 结合亲和力nM级，甲基化无显著影响 | Oct4直接结合CpGpal，不依赖甲基化状态 | 无法确定体内是否发生 | Results 图4B-C |
| 亚结构域EMSA | POUHD足以驱动二聚化 | POUHD vs 全长POU vs POUS | POUHD形成二聚体，POUS不结合 | POUHD是CpGpal结合的关键结构域 | 无法排除POUS在体内有辅助作用 | Results 图5B-C |
| 协同性定量 | Oct4在CpGpal上正协同二聚化 | Oct4 vs Brn2 | Oct4 ω > 1，Brn2 ω < 1 | Oct4特异性协同结合CpGpal | 无法确定协同性的结构基础 | Results 图4E, 5C |
| 单管竞争EMSA | Oct4优先于Brn2结合CpGpal | Oct4+Brn2+双标记DNA | Oct4二聚体带占优 | Oct4对CpGpal有更高特异性 | 无法排除其他POU因子 | Results 图S5B-D |
| Brn2/MORE晶体结构 | 提供POU二聚化模板 | Brn2 + MORE DNA | 1.89 Å结构，POUHD-POUHD互作 | 结构可用于建模Oct4/CpGpal | 无法直接外推至Oct4 | Results 图6B-C |
| Oct4/CpGpal建模+MD | 模型稳定性 | 两种构型，470 ns | 构型1稳定，构型2不稳定 | 构型1是合理结合模式 | 模型非实验验证 | Results 图6D-F, S8 |
| ChIP-seq重分析 | CpGpal在体内被Oct4占用 | 16个数据集 | CpGpal在Oct4 peak中富集 | Oct4在体内结合CpGpal | 无法排除其他因子共结合 | Results 图1 |
| WGBS整合 | CpGpal位点保持甲基化 | 重编程时间序列 | >50% CpGpal位点保持甲基化 | Oct4结合不诱导去甲基化 | 无法确定因果方向 | Results 图2D-F |
| 突变分析（RK motif） | N端RK motif影响功能 | ePOU vs ePOU+K | 插入K降低重编程效率 | RK motif长度影响Oct4功能 | 机制未完全阐明 | Results 图S6G-H |

---

## 11 结论正确解读

- **任务范围**：本文仅研究了Oct4和Brn2两个POU因子对CpGpal的体外结合及基因组占用，未系统评估所有POU家族成员。
- **oracle/真值输入**：结构模型基于同源建模（非实验结构），MD模拟验证的是模型稳定性而非真实结合路径。
- **端到端状态**：从序列→结构→功能的全链条尚未打通；缺乏Oct4/CpGpal复合物的实验结构。
- **算力成本**：MD模拟470 ns，属于中等规模，未涉及增强采样或自由能计算。
- **历史数据依赖**：ChIP-seq重分析依赖已发表数据，不同实验室的抗体、细胞状态可能引入偏差。
- **模型依赖**：MD结果依赖AMBER力场对甲基化DNA的描述准确性。
- **最难情形**：体内CpGpal位点通常处于核小体包裹状态，本文未测试POUHD在核小体上的结合。
- **群体/领域边界**：结论仅适用于POU家族，不能推广至所有methyl-plus TF。
- **不确定性**：协同性因子ω的误差范围未报告；MD模拟的收敛性未充分讨论。

**有边界的复述**：  
在体外条件下，Oct4的POUHD能以正协同方式二聚化结合甲基化或非甲基化的CpGpal DNA，该结合不依赖POUS结构域；Brn2不具备此能力。在已发表ChIP-seq数据中，CpGpal motif在Oct4结合位点中富集，且这些位点在重编程中倾向于保持甲基化。但缺乏实验结构直接证明Oct4/CpGpal的结合构型。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 缺乏Oct4/CpGpal实验结构 | 仅获得Brn2/MORE晶体结构，Oct4/CpGpal为模型 | 未来需解析Oct4/CpGpal复合物晶体结构 | Results 图6；Discussion |
| 结构模型的不确定性 | 两种构型均基于同源建模，MD仅验证稳定性 | 需通过突变实验进一步验证关键残基 | Results 图S8 |
| 体外结合与体内功能的差距 | EMSA证明结合，但体内功能未直接验证 | 需在细胞中验证CpGpal位点的功能 | Discussion |
| 未测试核小体环境 | CpGpal在体内可能被核小体包裹 | 未来需研究POUHD在核小体上的结合 | Discussion |
| 仅测试了Brn2作为对照 | 未系统评估其他POU因子 | 需扩展至更多POU家族成员 | Results 图4F-G |
| 重编程中CpGpal的功能未明确 | 观察到甲基化维持，但未证明功能意义 | 需功能实验验证 | Results 图2 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| POUHD单独结合CpGpal的生理相关性 | 体内全长Oct4可能以不同构型结合，POUHD单独实验可能高估其独立性 | 决定该结合模式是否在体内真实发生 | 在细胞中表达POUHD缺失突变体，检测CpGpal占用 | Results 图5 |
| 甲基化不改变结合亲和力 | EMSA缓冲液条件可能掩盖甲基化效应；体内染色质环境可能不同 | 甲基化是否真正中性影响该结合模式 | 在核小体底物上重复EMSA；使用更长DNA片段 | Results 图4 |
| ChIP-seq中CpGpal富集的因果性 | 富集可能由其他共结合因子驱动，而非Oct4直接结合 | 决定Oct4是否直接结合CpGpal | 敲低Oct4后检测CpGpal占用变化 | Results 图1 |
| 结构模型的可靠性 | 同源建模可能遗漏关键构象变化；MD模拟时间尺度有限 | 模型是机制解释的基础 | 尝试共结晶；使用增强采样MD | Results 图6 |
| RK motif突变影响重编程的机制 | 突变可能影响蛋白稳定性或核定位，而非直接通过CpGpal结合 | 决定RK motif的功能归因 | 检测突变体蛋白表达水平和定位 | Results 图S6 |
| CpGpal位点甲基化维持的解读 | 甲基化维持可能由其他蛋白（如DNMT）驱动，Oct4只是旁观者 | 决定Oct4是否主动保护甲基化 | 在Oct4缺失细胞中检测CpGpal甲基化 | Results 图2 |
| 样本量问题 | 16个ChIP-seq数据集中，部分来自不同细胞类型和条件，异质性可能影响结论 | 决定结论的普适性 | 分层分析不同细胞类型 | Results 图1 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **结构域级别的结合模式可切换**：Oct4的POUHD在CpGpal上独立驱动二聚化，而POUS脱离DNA。这提示在预测TF-DNA结合时，不能将多结构域蛋白视为刚性整体，需考虑结构域独立结合的可能性。**可迁移至**：深度学习模型可尝试预测「结构域参与状态」作为中间变量，而非直接预测全蛋白结合。

2. **甲基化识别可通过间接读码实现**：Oct4对甲基化DNA的偏好不依赖直接接触甲基基团，而是通过DNA形状（MGW变窄）和静电势。**可迁移至**：AI模型可纳入DNA形状特征（如DNAShape）作为输入，而非仅依赖序列；MD模拟可用来生成甲基化DNA的结构特征训练集。

3. **协同性因子ω是TF特异性的定量指标**：Oct4在CpGpal上ω > 1，Brn2 ω < 1，这一差异可能解释功能分化。**可迁移至**：在预测TF结合位点时，可显式建模二聚化协同性，而非仅预测单体结合。

4. **先驱因子功能不必然伴随染色质打开**：Oct4在CpGpal位点结合但不诱导去甲基化或开放，提示先驱因子的功能可能比「打开染色质」更复杂。**可迁移至**：评估TF功能时需区分「结合」与「染色质重塑」两个维度。

5. **结构引导的建模+MD验证流程**：本文展示了「实验结构（Brn2/MORE）→同源建模（Oct4/CpGpal）→MD验证」的可行路径。**可迁移至**：当目标复合物难以结晶时，可利用同源结构建模+MD筛选合理构型。

6. **多组学整合验证体外发现**：将EMSA结果与ChIP-seq/WGBS/ATAC-seq关联，增强了体外发现的生理相关性。**可迁移至**：AI预测的TF结合位点应通过公开的ChIP-seq、甲基化数据进行验证。

---

## 15 与已有知识连接

- **POU结构域二聚化**：本文与Oct1/Oct6在MORE/PORE上的二聚化研究（Reményi et al., 2001; Jauch et al., 2012）直接相关，但提出了一种新的二聚化模式（仅POUHD参与）。可对比：POU家族二聚化的多样性。
- **methyl-plus TF**：本文扩展了「methyl-plus」TF列表，与HOXB13（Yin et al., 2017）等直接结合甲基化CpG的TF形成对比——Oct4不直接接触甲基，而是通过形状读码。
- **先驱因子与DNA甲基化**：与Soufi et al. (2015) 关于Oct4结合核小体的研究互补，本文提供了甲基化DNA结合的新视角。
- **DNA形状读码**：与DNAShape方法（Zhou et al., 2013）和MGW介导的TF识别（Chiu et al., 2017）一致，本文的R105-MGW机制是具体案例。
- **MD模拟在TF-DNA研究中的应用**：与Perez et al. (2019) 等MD模拟TF-DNA结合的工作一致，本文展示了MD在验证结构模型中的价值。
- **重编程中的表观遗传动态**：与Hanna实验室的重编程时间序列数据（Raissi et al., 2023）直接关联，本文的CpGpal甲基化维持现象为该数据提供了机制解释。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选1：基于结构的甲基化CpG识别预测模型
- **名称**：MethylCpG-BindNet：结构感知的TF-甲基化DNA结合预测
- **来源局限/观察**：本文证明Oct4通过形状读码识别甲基化CpG，而非直接接触甲基。现有深度学习模型（如DeepSEA、BPNet）仅使用序列输入，无法捕捉甲基化依赖的形状变化。
- **核心假设**：将DNA形状特征（MGW、Roll、Propeller Twist）和甲基化状态作为输入，可显著提高对methyl-plus TF结合位点的预测精度。
- **初步方法**：使用DNAShapeR2计算甲基化/非甲基化DNA的形状特征，结合卷积神经网络（CNN）或Transformer架构，在本文的ChIP-seq数据和公开的methyl-TF数据集上训练。
- **验证方式**：与仅序列输入的基线模型对比AUC/PRC；在本文的CpGpal位点上进行零样本测试。
- **创新状态**：unverified

### 候选2：POUHD二聚化协同性的自由能计算
- **名称**：协同性开关：POU家族二聚化协同性的分子动力学研究
- **来源局限/观察**：本文实验测得Oct4在CpGpal上ω > 1而Brn2 ω < 1，但未提供自由能解释。POUHD序列差异（尤其N端RK motif）如何影响协同性未知。
- **核心假设**：Oct4 POUHD的N端RK motif通过分子间静电互作稳定二聚体，而Brn2的额外赖氨酸破坏互作。
- **初步方法**：对Oct4/Brn2 POUHD在CpGpal上的二聚化进行伞形采样（umbrella sampling）或副本交换MD，计算结合自由能曲线；对RK motif进行丙氨酸扫描突变模拟。
- **验证方式**：预测的突变效应与EMSA实验对比；自由能差异与ω值相关性分析。
- **创新状态**：unverified

### 候选3：CpGpal位点的进化稳定性分析
- **名称**：进化陷阱：CpGpal在哺乳动物基因组中的保守性与功能
- **来源局限/观察**：本文发现CpGpal位点在重编程中保持甲基化，且不保守（负PhyloP）。这些位点可能是「进化不稳定但功能重要」的元件。
- **核心假设**：CpGpal位点通过甲基化依赖的方式在种系中快速演化，但Oct4结合能力被选择保留。
- **初步方法**：跨物种（人、鼠、猪、斑马鱼）比较CpGpal位点的序列保守性、甲基化状态和Oct4 ChIP-seq占用；分析C-T转换速率。
- **验证方式**：统计CpGpal位点的dN/dS或PhyloP分布与随机位点的差异；功能实验验证代表性位点。
- **创新状态**：unverified

### 候选4：POUHD二聚化对核小体结合的影响
- **名称**：核小体上的二聚体：Oct4 POUHD在甲基化核小体上的结合模式
- **来源局限/观察**：本文仅测试了裸DNA上的结合，但体内CpGpal可能被核小体包裹。POUHD二聚体能否结合核小体上的CpGpal未知。
- **核心假设**：POUHD二聚体通过结合核小体DNA的入口/出口位置识别CpGpal，POUS的脱离有利于在核小体上结合。
- **初步方法**：制备含CpGpal的核小体底物，进行EMSA和MNase实验；使用冷冻电镜或交联质谱解析POUHD/核小体复合物结构。
- **验证方式**：与裸DNA结合亲和力对比；突变POUHD二聚化界面后检测核小体结合变化。
- **创新状态**：unverified

### 候选5：深度学习预测CpGpal结合位点的可解释性分析
- **名称**：可解释的甲基化偏好：从深度学习模型中提取Oct4的识别规则
- **来源局限/观察**：本文的ChIP-seq数据提供了CpGpal结合位点的基因组分布，但缺乏序列-结构-功能映射规则。
- **核心假设**：深度学习模型（如BPNet）可以从ChIP-seq数据中学习到POUHD二聚化的序列语法，且该语法与结构模型一致。
- **初步方法**：在本文的ChIP-seq数据上训练BPNet模型，使用DeepLIFT或SHAP进行可解释性分析，提取关键序列基序和位置权重。
- **验证方式**：提取的基序与结构模型中的接触残基对应；预测的突变效应与EMSA结果对比。
- **创新状态**：unverified