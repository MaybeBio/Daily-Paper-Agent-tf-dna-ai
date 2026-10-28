## 01 基本信息
- **标题**：Spatial arrangement of functional domains in OxyS stress response sRNA
- **作者**：Stih, Vesna; Amenitsch, Heinz; Plavec, Janez; Podbevsek, Peter
- **单位**：未提供（推测为斯洛文尼亚研究机构，基于ARRS基金资助）
- **期刊/平台**：RNA (New York, N.Y.)
- **年份**：2023-06-29
- **论文类型**：实验研究（结构生物学 + 计算模拟）
- **领域**：RNA结构生物学；细菌sRNA调控；RNA–RNA互作
- **关键词**：OxyS sRNA；fhlA mRNA；NMR；SAXS；分子动力学模拟；茎环结构
- **DOI/arXiv 号**：10.1261/rna.079618.123
- **代码**：未提供
- **数据**：SAXS数据与3D模型已存入SASBDB，条目SASDQP8（https://www.sasbdb.org/data/SASDQP8/bzsjs8zm83）
- **阅读日期**：2025年（具体日期未记录）
- **在本课题方向中的位置**：本文研究对象为细菌sRNA（非TF蛋白），但其核心机制——RNA通过碱基互补配对识别靶mRNA、多结构域空间排布决定互作效率——与TF–DNA结合机制高度类比。方法上整合NMR、SAXS与无偏MD模拟，为「实验约束 + 计算采样」解析核酸-核酸互作构象提供了可迁移范式，尤其对TF–DNA复合物中多结构域协同结合的空间组织问题有直接借鉴价值。

## 02 一句话总结
通过NMR、SAXS与无偏MD模拟的整合方法，解析了E. coli OxyS sRNA的二级结构（含新发现的SL4茎环）与三维构象（伸展的boomerang状），并证实其SL1与SL3两个功能域分别与fhlA mRNA的CDS和RBS区域形成碱基配对，且两功能域的空间距离与靶位点间距匹配。

## 03 研究问题
- **具体问题**：OxyS sRNA（110 nt）的完整二级结构是什么？其四个功能域（茎环）在三维空间中如何排布？SL1和SL3两个与fhlA mRNA互作的位点是否在空间上预组织以支持双位点（bipartite）结合？
- **为什么重要**：OxyS是氧化应激响应中的关键调控因子，通过碱基配对抑制fhlA翻译。理解其结构-功能关系是阐明sRNA调控机制的基础，也为设计人工sRNA提供结构模板。
- **现有方法不足**：此前仅有预测的二级结构（含3个茎环）和化学足迹实验数据，缺乏高分辨率结构信息；sRNA的构象动态性使晶体学方法难以应用。
- **精确研究问题**：Can the combination of NMR-derived secondary structure constraints, SAXS envelope, and unbiased MD simulations produce 3D models of OxyS that (a) satisfy all experimental data and (b) reveal spatial preorganization of SL1 and SL3 for bipartite fhlA recognition?

## 04 背景与发展脉络
- **阶段一：sRNA发现与功能研究（1985–2000）**：OxyS于1985年被发现，后续研究确定其受OxyR调控、响应H₂O₂胁迫、调控40+基因表达。代表性方法：遗传筛选、报告基因。局限：无结构信息。
- **阶段二：sRNA二级结构预测与化学探测（2000–2015）**：使用MFOLD等预测工具和化学足迹法（如SHAPE）获得OxyS二级结构模型，含3个茎环。局限：分辨率低，无法揭示三维排布。
- **阶段三：sRNA与靶标互作的生化研究（2000–2020）**：通过突变和报告基因确定OxyS与fhlA的互作位点（SL1–CDS、SL3–RBS），提出bipartite互作模型。局限：缺乏结构证据支持空间预组织假说。
- **阶段四：整合结构生物学（本文，2023）**：结合NMR（二级结构+碱基配对）、SAXS（整体形状）、FARFAR2 de novo建模与无偏MD（构象采样），首次提出OxyS的4茎环结构模型和boomerang状三维构象，并验证SL1/SL3的空间排布支持bipartite互作。
- **脉络标注**：以上脉络为「经外部核验」——OxyS发现年份、调控机制、fhlA互作位点等均引用自该领域已发表文献（如Altuvia et al. 1997, 1998; Argaman and Altuvia 2000），非本文首创。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| sRNA高分辨率结构缺失 | OxyS的3D结构从未被解析 | 分子量小（37.8 kDa）、构象动态性强，难以结晶；NMR全结构解析受限于谱图重叠 | Introduction: "the structure of OxyS and its complexes with mRNAs have not been studied by high-resolution methods" |
| 预测的二级结构不完整 | 预测仅含3个茎环，遗漏SL4 | 预测工具（如Zuker算法）未考虑实验约束；SL4区域序列看似非结构化 | Results: "Unexpectedly, stem–loop SL4 was identified in the region that was predicted to be unstructured" |
| 功能域空间排布未知 | SL1与SL3的互作位点距离无法从序列推断 | 缺乏实验约束的三维结构信息 | Discussion: "we reveal that OxyS comprises four stem–loops and propose their possible spatial arrangement" |
| 构象动态性难以捕捉 | 单一静态结构无法描述OxyS的多构象行为 | sRNA的柔性连接区允许茎环相对运动 | Discussion: "the motions of individual stem–loops are beyond the timescale of MD simulations" |
| 实验与计算数据整合困难 | FARFAR2模型Rg值远低于实验值 | de novo建模偏向紧凑构象，未充分采样伸展态 | Results: "the Rg values of the models were nowhere near the experimentally determined value (47.6 ± 3.8 Å)" |

## 06 核心思想
1. **表面方法**：采用「分而治之」策略——先分别解析OxyS的3个预测茎环（SL1、SL2、SL3）的NMR结构，再通过SAXS获取全长OxyS的整体形状约束，最后用FARFAR2 de novo建模生成候选3D结构，并以无偏MD模拟扩展构象空间，筛选满足SAXS数据的模型。
2. **核心洞察**：OxyS并非由3个茎环组成，而是包含4个茎环——SL4位于此前被认为非结构化的区域（nt 72–89）。SL4的存在显著缩短了SL1与SL3之间的非结构化连接区（从26 nt减至8 nt），使两个功能域在空间上更接近，从而支持与fhlA mRNA的bipartite互作。此外，SL3与SL4的共轴堆叠（coaxial stacking）进一步稳定了整体构象。
3. **可能的普适教训** [Analysis]：对于多结构域RNA（或蛋白质），「预测的非结构化区域」可能隐藏着功能性结构单元；实验约束（NMR化学位移、SAXS形状）与无偏MD的结合能有效揭示这类隐藏结构。该策略可迁移至TF–DNA互作研究：TF中预测为无序的连接区可能包含功能性DNA结合亚结构域，需以实验约束+MD采样验证。

## 07 方法总览
- **输入**：OxyS全长序列（110 nt）；fhlA mRNA的CDS和RBS区域序列；NMR化学位移数据；SAXS散射曲线。
- **输出**：OxyS的二级结构模型（含4个茎环）；3D结构系综（5个代表性模型）；OxyS–fhlA互作位点及碱基配对信息。
- **模块**：
  1. **RNA样品制备**：体外转录（IVT）合成天然丰度及¹³C/¹⁵N标记的OxyS；化学合成短寡核苷酸（茎环片段、fhlA片段）。
  2. **NMR结构解析**：1D ¹H谱、2D NOESY、JR-NOESY、¹H–¹⁵N SF-HMQC、¹H–¹⁵N BEST-TROSY、¹H–¹⁵N BEST-TROSY-HNN-COSY；用于二级结构确定、碱基配对鉴定、互作位点映射。
  3. **UV热变性**：测定各茎环的热稳定性（T₁/₂）。
  4. **SAXS数据采集与分析**：同步辐射SAXS（奥地利线站），Guinier分析、Kratky图、对分布函数P(r)、ab initio形状重建（DAMMIF/DAMAVER）。
  5. **De novo 3D建模**：FARFAR2（Rosetta rna_denovo），以NMR二级结构为约束，生成2389个候选结构。
  6. **无偏MD模拟**：AMBER18 + OL3力场，TIP3P水模型，20 ns/轨迹，10个起始结构，共2000快照/轨迹。
  7. **模型筛选与系综优化**：CRYSOL计算理论散射曲线，与实验SAXS数据比对；NNLSJOE优化系综组成。
- **训练**：不适用（无监督学习/无训练过程）。
- **工具**：NMR（Bruker/Agilent谱仪）、SAXS（Elettra同步辐射）、FARFAR2/Rosetta、AMBER18、CRYSOL、GNOM、DAMMIF、DAMAVER、NNLSJOE、cpptraj。
- **反馈回路**：NMR二级结构 → FARFAR2建模 → MD扩展构象 → CRYSOL拟合SAXS → NNLSJOE系综优化 → 最终模型。
- **文字流程**：先通过NMR确定各分离茎环的二级结构并验证其在全长中的保守性 → 用SAXS获取全长OxyS的整体形状参数 → 以NMR二级结构为约束，FARFAR2生成初始3D模型库 → 选取10个低χ²模型进行无偏MD模拟 → 从MD轨迹中提取2000快照/模型，用CRYSOL计算理论散射 → 以NNLSJOE优化系综，选出5个最佳模型 → 将模型与SAXS包络比对，确定各茎环的空间位置 → 设计fhlA片段，用NMR滴定验证互作位点。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| NMR二级结构解析 | 确定各茎环的碱基配对模式 | 为3D建模提供实验约束；验证预测结构 | 输入：茎环RNA样品；输出：二级结构模型 | Results 图2-4；Methods NMR部分 | 无法区分预测与真实结构，3D建模失去关键约束 [预期] |
| SAXS形状分析 | 获取全长OxyS的整体尺寸和形状 | 提供低分辨率但全局性的构象约束 | 输入：全长OxyS散射曲线；输出：Rg=47.6±3.8 Å，Dmax=155 Å，boomerang状包络 | Results 图6；Methods SAXS部分 | 无法验证3D模型的全局形状正确性 [预期] |
| FARFAR2 de novo建模 | 生成满足二级结构约束的3D候选结构 | 从序列和二级结构出发构建原子模型 | 输入：序列+二级结构；输出：2389个候选结构 | Methods "De novo 3D structure prediction" | 无初始模型，MD无起点 [预期] |
| 无偏MD模拟 | 扩展构象空间，生成更伸展的构象 | FARFAR2模型Rg偏低，需MD探索更大构象空间 | 输入：10个FARFAR2结构；输出：2000快照/轨迹 | Results: "Rg values...nowhere near experimental"; Methods MD部分 | 模型无法达到实验Rg值，SAXS拟合失败 [实测：FARFAR2模型Rg 22.54–36.78 Å vs 实验47.6 Å] |
| CRYSOL/SAXS拟合 | 计算模型理论散射并与实验比对 | 筛选与实验数据一致的构象 | 输入：MD快照+实验散射；输出：χ²值 | Results 图7；Supplemental 表S5-S7 | 无法客观筛选模型 [预期] |
| NNLSJOE系综优化 | 确定最优系综组成 | 单一结构无法描述构象动态性 | 输入：候选模型+实验散射；输出：5模型系综，χ²=0.22 | Results 图7；Supplemental 表S7 | 无法获得定量系综描述 [预期] |
| NMR互作滴定 | 验证OxyS与fhlA的碱基配对位点 | 直接证据支持功能域的空间排布意义 | 输入：OxyS+fhlA片段；输出：6+4个碱基配对 | Results 图8 | 无法确认SL1/SL3的功能角色 [预期] |

## 09 关键公式符号
- **Guinier近似**：ln I(q) ≈ ln I(0) − (Rg²/3)q²，用于从SAXS低q区提取回转半径Rg。
  - I(q)：散射强度；q：散射矢量；Rg：回转半径。
- **对分布函数P(r)**：P(r) = (1/2π²)∫I(q)qr·sin(qr)dq，反映分子内原子对距离分布，用于确定Dmax。
  - r：原子对距离；Dmax：最大分子尺寸。
- **χ²（拟合优度）**：χ² = (1/N)Σ[(I_exp(q) − c·I_calc(q))/σ(q)]²，用于评估模型与实验SAXS数据的匹配度。
  - N：数据点数；c：缩放因子；σ(q)：实验误差。
- **归一化空间差异（NSD）**：用于量化ab initio重建包络之间的相似性，NSD < 1表示结构相似。
- **T₁/₂（热变性中点温度）**：从UV熔解曲线二阶导数确定，反映RNA茎环热稳定性。

## 10 实验设计与证据链
- **数据集/群体**：OxyS全长（110 nt）及截短/延伸茎环片段（SL1、SL2、SL3、SL4、SL1Δ17、SL3ext、SL4+SL3）；fhlA mRNA片段（fhlA1: nt 81–100；fhlA41: nt 16–56）。
- **规模**：NMR实验涉及约10个RNA样品；SAXS 1个全长样品；MD模拟10条轨迹×20 ns；FARFAR2生成2389个结构。
- **指标**：NMR化学位移、NOE连接、T₁/₂、Rg、Dmax、χ²、NSD。
- **基线**：预测的3-茎环二级结构模型（Zuker算法）；FARFAR2无SAXS约束的模型。
- **预算**：未提供。
- **骨干/仪器**：600/800 MHz NMR谱仪（Bruker/Agilent）；Elettra同步辐射奥地利SAXS线站。
- **Oracle输入**：NMR二级结构约束（用于FARFAR2）；实验SAXS散射曲线（用于模型筛选）。
- **评测协议**：模型选择标准为Rg ≥ 40 Å且χ² ≤ 1.5；最终系综经NNLSJOE优化，χ² = 0.22。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| 分离茎环NMR结构解析 | SL1、SL2、SL3各自形成稳定茎环 | 各茎环单独制备，NMR谱图分析 | 所有茎环形成预期二级结构；SL3含U90·U110错配 | 预测的3个茎环结构正确 | 无法证明全长中结构不变 | Results 图2-4 |
| SL4鉴定 | OxyS含第4个茎环（nt 72–89） | 全长NMR谱中未归属信号分析 | SL4形成稳定茎环，与SL3共轴堆叠 | OxyS含4个茎环而非3个 | 无法确定SL4的功能角色 | Results 图5 |
| SAXS形状分析 | OxyS呈伸展构象 | Guinier、Kratky、P(r)分析 | Rg=47.6±3.8 Å，Dmax=155 Å，boomerang状 | OxyS整体为伸展双臂结构 | 无法分辨各茎环具体位置 | Results 图6 |
| FARFAR2建模+MD | 生成满足实验数据的3D模型 | 2389个de novo结构→10个MD→2000快照筛选 | 5个模型满足Rg≥40 Å且χ²≤1.5 | 模型与SAXS包络一致 | 模型非唯一解，存在构象系综 | Results 图7；Supplemental 表S5-S7 |
| NMR互作滴定 | SL1与fhlA CDS、SL3与fhlA RBS碱基配对 | 分别混合OxyS茎环与fhlA片段，观察新信号 | SL1Δ17-fhlA1形成6 bp；SL3-fhlA41形成4 bp | 确认双位点互作 | 无法证明全长中同时发生 | Results 图8 |
| UV热变性 | 各茎环热稳定性 | 比较T₁/₂ | SL3 T₁/₂=84°C；SL2 T₁/₂=57°C | SL3高度稳定，SL2较不稳定 | 热稳定性与功能相关性未直接证明 | Results；Supplemental 图S5 |

## 11 结论正确解读
- **任务范围**：本文仅解析了OxyS在无蛋白条件下的游离态结构，未涉及OxyS–fhlA复合物的高分辨率结构，也未研究Hfq结合后的构象变化。
- **Oracle/真值输入**：NMR二级结构约束来自分离茎环而非全长OxyS；SAXS数据为溶液态系综平均，无法区分单个构象。
- **端到端状态**：非端到端——3D模型为「实验约束+计算采样」的系综，非实验测定的唯一结构。
- **算力成本**：MD模拟仅20 ns/轨迹，可能未充分采样大尺度构象变化；作者明确承认"motions of individual stem–loops are beyond the timescale of MD simulations"。
- **历史数据依赖**：二级结构预测依赖Zuker算法（2003），未使用更新的机器学习方法（如RNAfold 2.0、SPOT-RNA）。
- **模型依赖**：FARFAR2和AMBER OL3力场对RNA构象采样的准确性有限，尤其对长距离相互作用。
- **最难情形**：SL2在OxyS中信号宽化，表明其构象动态性强，难以精确建模；SL4的共轴堆叠仅基于NMR化学位移推断，缺乏直接结构证据。
- **群体/领域边界**：结论仅适用于E. coli OxyS，不可外推至其他sRNA；bipartite互作模型基于体外实验，体内条件（如Hfq存在、拥挤环境）可能不同。
- **不确定性**：最终系综含5个模型，模型间茎环相对取向存在差异；作者未提供模型间的RMSD或构象聚类分析。
- **有边界的复述**：在NMR和SAXS实验约束下，OxyS采用含4个茎环的伸展boomerang状构象，SL1与SL3分别位于两臂末端，空间距离与fhlA双位点间距匹配，支持bipartite互作的预组织假说；但该模型为低分辨率系综，不排除其他构象状态。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 模型非高分辨率结构 | "our models have atomic resolution, they should not be regarded as high-resolution structures" | 未明确提及 | Discussion |
| 构象采样不完整 | "the motions of individual stem–loops are beyond the timescale of MD simulations" | 未明确提及 | Discussion |
| 可能遗漏构象 | "despite a large ensemble obtained from de novo modeling, some conformations might have been missed" | 未明确提及 | Discussion |
| SAXS系综平均限制 | SAXS数据反映系综平均，无法区分单个构象 | 未明确提及 | Discussion（隐含） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| SL4的鉴定仅基于NMR化学位移和NOE，缺乏突变验证 | SL4可能为体外折叠的人工产物，体内未必形成 | 若SL4非体内结构，则「缩短连接区」的结论不成立 | 在体内进行SHAPE或DMS足迹实验，验证SL4区域的结构 | Results 图5；Methods NMR部分 |
| MD模拟仅20 ns，且仅10个起始结构 | 可能未充分采样OxyS的构象空间，尤其大尺度茎环重排 | 若采样不足，最终系综可能偏向初始构象 | 延长模拟至μs级，或使用增强采样方法（如replica exchange） | Methods "De novo 3D modeling" |
| 互作实验使用分离茎环而非全长OxyS | 分离茎环可能丧失全长中的构象约束，互作亲和力与特异性可能不同 | 全长中的茎环相对取向可能影响互作效率 | 用全长OxyS进行NMR滴定或单分子FRET实验 | Results 图8 |
| 未研究Hfq对OxyS构象的影响 | Hfq可能显著改变OxyS结构，使游离态模型不适用于体内 | Hfq是sRNA功能的关键辅助因子，其结合可能重排功能域 | 进行Hfq存在下的SAXS或NMR实验 | Introduction引用Hfq相关文献 |
| 模型与SAXS包络的拟合未提供定量误差分析 | χ²=0.22可能过拟合，或存在多个等效系综 | 缺乏误差分析无法评估模型唯一性 | 使用贝叶斯系综优化或重采样方法 | Results 图7；Supplemental 表S7 |
| 未与已知sRNA结构数据库进行系统比较 | OxyS的boomerang构象是否代表sRNA通用折叠模式未知 | 若为通用模式，可指导其他sRNA结构预测 | 对其他sRNA进行类似NMR+SAXS+MD分析 | Discussion |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **「分而治之」+「全局约束」的结构解析策略**：先解析分离结构域，再用整体形状约束（SAXS）组装全长模型，最后以MD扩展构象空间。可迁移至TF–DNA互作：先解析TF各DNA结合域（DBD）的游离态结构，再用SAXS或FRET约束全长TF构象，以MD采样DBD相对取向。
2. **「预测非结构化区域可能隐藏功能结构」**：OxyS的SL4位于预测非结构化区，但实际形成稳定茎环。对TF而言，预测为无序的N/C端延伸或连接区可能包含隐蔽的DNA结合基序或辅助识别元件，需以实验验证。
3. **双位点互作的空间预组织原则**：OxyS的SL1与SL3空间距离与fhlA双位点间距匹配，提示TF中多个DBD的空间排布可能预组织以匹配DNA识别位点的间距（如锌指蛋白的指间距、bZIP的二聚化间距）。
4. **Mg²⁺依赖的构象开关**：Mg²⁺部分解开fhlA茎环以暴露配对位点，提示TF–DNA互作中金属离子（如Zn²⁺、Mg²⁺）可能通过诱导DNA或TF构象变化来调控结合。
5. **系综描述优于单一结构**：最终模型为5个成员的系综，反映构象动态性。对TF–DNA复合物，应使用系综而非单一静态结构描述结合机制。
6. **NMR化学位移作为互作位点映射工具**：通过¹⁵N标记和HSQC滴定，可精确鉴定RNA–RNA互作的碱基对。类似地，¹⁵N标记TF蛋白，用DNA滴定可映射DNA结合界面。

## 15 与已有知识连接
- **OxyS功能研究**：Altuvia et al. (1997, 1998) 首次鉴定OxyS并确定其与fhlA的互作位点；Argaman and Altuvia (2000) 提出bipartite互作模型。本文为该模型提供了结构证据。
- **sRNA结构研究**：与RyR sRNA、DsrA等sRNA的结构研究形成对比——多数sRNA结构研究聚焦单一茎环，本文首次提供完整sRNA的三维排布。
- **RNA–RNA互作机制**：与miRNA–mRNA互作、CRISPR RNA–DNA识别等系统类比，均涉及多结构域协同识别。
- **TF–DNA互作（本课题核心）**：本文的「多结构域空间排布决定双位点识别」与TF中多个DBD协同结合DNA的机制高度相似（如GAL4、Zif268、p53）。本文的「实验约束+MD采样」方法可直接迁移至TF–DNA复合物建模。
- **结构生物学方法**：与SAXS+MD联用解析蛋白质构象的已有工作（如Bernadó et al.）一致，本文将该策略扩展至RNA系统。
- **Hfq–sRNA互作**：本文讨论Hfq结合位点（SL4的AU-rich motif），与Santiago-Frangos and Woodson (2018) 的Hfq识别机制研究衔接。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA双位点识别的空间预组织原则验证
   - **来源局限/观察**：OxyS的SL1/SL3空间排布支持bipartite识别预组织；TF中多个DBD是否同样预组织未知
   - **核心假设**：TF的DBD间距与DNA识别位点间距存在统计相关性，且游离态TF的DBD相对取向偏向DNA结合态
   - **初步方法**：收集已知TF–DNA复合物结构，统计DBD间距；对游离态TF进行SAXS+MD分析，比较游离态与结合态DBD取向
   - **验证方式**：与PDB中复合物结构比对，计算游离态与结合态DBD取向的RMSD
   - **创新状态**：unverified

2. **候选名称**：预测无序区中的隐蔽DNA结合基序挖掘
   - **来源局限/观察**：OxyS的SL4位于预测非结构化区；TF中预测无序区可能含隐蔽DBD
   - **核心假设**：部分TF的预测无序区包含功能性DNA结合基序，其结构在结合DNA时折叠
   - **初步方法**：对预测无序区进行序列分析（如IUPred、AlphaFold3），筛选候选基序；用NMR/CD检测DNA诱导的折叠
   - **验证方式**：突变分析+EMSA验证DNA结合功能
   - **创新状态**：unverified

3. **候选名称**：金属离子诱导的TF–DNA构象开关
   - **来源局限/观察**：Mg²⁺部分解开fhlA茎环以促进配对；TF–DNA互作中金属离子（Zn²⁺、Mg²⁺）可能类似地调控构象
   - **核心假设**：金属离子通过诱导TF或DNA的局部构象变化来调控结合亲和力
   - **初步方法**：对锌指TF进行MD模拟（有/无Zn²⁺），比较DBD构象；用ITC测量不同金属离子条件下的结合常数
   - **验证方式**：MD模拟预测的构象变化与ITC/SAXS实验数据比对
   - **创新状态**：unverified

4. **候选名称**：sRNA–mRNA与TF–DNA互作的结构比较分析
   - **来源局限/观察**：OxyS–fhlA与TF–DNA均涉及双位点识别，但分子机制（碱基配对 vs 氨基酸–碱基接触）不同
   - **核心假设**：两种系统的双位点识别遵循共同的几何原则（间距、角度、柔性）
   - **初步方法**：系统比较sRNA–mRNA和TF–DNA复合物结构，提取双位点间距、角度分布
   - **验证方式**：统计分析+分子模拟验证几何原则的普适性
   - **创新状态**：unverified

5. **候选名称**：基于系综的TF–DNA结合预测模型
   - **来源局限/观察**：OxyS的系综模型优于单一结构；TF–DNA结合预测多依赖单一静态结构
   - **核心假设**：TF的构象系综比单一结构更能预测DNA结合位点选择
   - **初步方法**：对TF进行MD采样生成系综，用系综对接（如HADDOCK）预测DNA结合位点
   - **验证方式**：与已知TF–DNA复合物结构比对，比较系综对接与单结构对接的预测准确率
   - **创新状态**：unverified