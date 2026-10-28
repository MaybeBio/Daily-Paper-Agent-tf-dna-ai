## 01 基本信息
- **标题**: T and Z, partial seed coat patterning genes in common bean, provide insight into the structure and protein interactions of a plant MBW complex
- **作者与单位**: McClean, Phillip E; Roy, Jayanta; Colbert, Christopher L; Osborne, Caroline; Lee, Rian; Miklas, Phillip N; Osorno, Juan M（单位未在摘要中提供）
- **期刊/平台**: G3 (Bethesda, Md.)
- **年份**: 2024-08-21
- **论文类型**: 研究论文（遗传学 + 计算结构生物学）
- **领域**: 植物遗传学；类黄酮生物合成调控；MBW（MYB-bHLH-WDR）蛋白复合物
- **关键词**: 类黄酮、种子种皮着色、MBW复合物、AlphaFold2、菜豆（Phaseolus vulgaris）
- **DOI/ID**: 10.1093/g3journal/jkae184
- **代码**: 未提供
- **数据**: NCBI 蛋白序列（T: OR500718-OR500721；Z: OR475097-OR475098）
- **阅读日期**: 2026-05-13
- **在本课题方向中的位置**: 本文以植物 MBW 三元复合物为对象，利用 AlphaFold2/AF-Multimer 进行蛋白-蛋白互作结构预测，属于「蛋白质-DNA 互作 × AI 结构预测」方向中「蛋白复合物组装与互作界面解析」的子类。虽不直接涉及 TF-DNA 结合，但其「预测突变体对复合物互作影响」的范式可直接迁移至 TF-DNA 结合机制研究。

## 02 一句话总结
通过遗传定位、系统发育分析和 AlphaFold2/AF-Multimer 结构预测，鉴定菜豆 T 基因为七叶 β-propeller WDR 蛋白、Z 基因为 R2R3-MYB 蛋白，并首次构建了植物 MBW 三元复合物的计算结构模型，揭示 Z MYB 与 T WDR 间存在一个此前未报道的 β-MoRF 互作基序，且突变体蛋白会改变复合物内互作界面。

## 03 研究问题
- **具体问题**: 菜豆中控制种子种皮部分着色（partial seed coat patterning）的 T 和 Z 基因分别编码什么蛋白？它们如何作为 MBW 复合物的组分参与类黄酮通路调控？突变体如何影响复合物组装？
- **为什么重要**: MBW 复合物是植物类黄酮（花青素、原花青素）生物合成的核心调控模块，但植物中完整 MBW 三元复合物的结构模型此前缺失；T/Z 基因的分子身份长期未知，限制了对种皮着色空间调控机制的理解。
- **现有方法不足**: 传统遗传定位只能界定候选区间；单个蛋白的结构预测无法揭示复合物内互作界面；缺乏对突变体蛋白结构后果的系统评估。
- **精确研究问题**: Can AlphaFold2-based multimer modeling identify the molecular identities of T and Z and define the interaction interfaces within a plant MBW complex, such that mutant alleles' structural consequences can be predicted?

## 04 背景与发展脉络
- **阶段一：经典遗传学定位（~1900-2000s）**。T（Tschermak 1912）和 Z（Emerson 1909）等基因通过经典遗传学被定义，控制菜豆种皮着色模式，但分子身份未知。代表方法：连锁分析、表型分类。局限：无法直接鉴定基因。
- **阶段二：类黄酮通路基因克隆（~2000-2020）**。P 被克隆为 bHLH 蛋白（McClean et al. 2018）；V 编码类黄酮 3'5' 羟化酶（McClean et al. 2022）。MBW 复合物在拟南芥中被广泛研究（TT2/TT8/TTG1），但菜豆 T/Z 的分子身份仍缺失。
- **阶段三：结构预测时代（2021-）**。AlphaFold2 发布后，单体结构预测成为常规工具；AF-Multimer 扩展至复合物预测。本文首次将 AF-Multimer 应用于植物 MBW 三元复合物建模。
- **本文主张的位置**: 在遗传定位和系统发育分析基础上，用 AF2/AF-Multimer 填补「MBW 复合物结构」空白，并首次提出 Z MYB 的 β-MoRF 互作基序。
- **脉络标注**: 以上脉络基于本文引言及参考文献重建，属「经外部核验」的领域共识框架。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| T/Z 基因分子身份未知 | 经典遗传学定义了 T/Z 位点，但无法确定其编码蛋白 | 缺乏精细定位和候选基因筛选 | Results "Identifying T and Z candidate genes" 节 |
| 植物 MBW 复合物无结构模型 | 仅有单体结构或片段共晶结构，缺乏三元复合物整体结构 | 膜蛋白/复合物表达纯化困难；此前无计算建模尝试 | Results "Computational modeling of a common bean MBW complex" 节 |
| 突变体功能后果难以预测 | 序列突变无法直接推断对蛋白互作的影响 | 缺乏结构上下文 | Results "Structural prediction for mutant T and Z alleles gene products" 节 |
| 互作界面信息缺失 | 已知 MYB-bHLH 互作，但 MYB-WDR 互作界面在植物中未明确定义 | 缺乏高分辨率复合物结构 | Results "Modeling of the P bHLH homodimer and Z MYB/P bHLH heterodimer" 节 |

## 06 核心思想
1. **表面方法**: 遗传定位 + 系统发育 + AlphaFold2/AF-Multimer 结构预测 + PISA 界面分析，鉴定 T/Z 候选基因并建模 MBW 复合物。
2. **核心洞察**: 
   - T 编码七叶 β-propeller WDR 蛋白（TTG1 直系同源），Z 编码 R2R3-MYB 蛋白（TT2 直系同源），二者与 P（bHLH）共同构成 MBW 复合物。
   - Z MYB 中存在一个此前未报道的 β-MoRF 基序：在单体状态下为无序区，与 T WDR 结合时转变为 β-strand 结构——这是「偶联折叠与结合」的典型特征。
   - 突变体蛋白（tEW 缺失第 6/7 叶、zEW K105N 替换）的结构预测显示，它们通过不同机制破坏复合物功能：tEW 破坏 WDR 支架完整性，zEW 破坏 MYB-DNA 结合能力而非复合物组装。
3. **可能的普适教训** [Analysis]: 
   - AF-Multimer 可用于快速生成复合物互作假说，但需警惕「预测界面」与「生理界面」的区分——本文对 tEW 复合物中 P bHLH 的异常结合位点明确标注为「可能非生理性」。
   - 无序区（IDR）在转录因子复合物组装中的功能角色可能被低估；β-MoRF 是值得关注的互作基序类型。

## 07 方法总览
- **输入**: 菜豆种质资源（5-593 及突变体系 65-73、Earliwax、PI 632734 等）；遗传定位数据（Brady et al. 1998 的 RAPD 标记）；参考基因组（5-593 v1.1）；NCBI 蛋白序列数据库。
- **输出**: T/Z 候选基因的分子身份；AF2 单体结构模型；AF-Multimer 三元复合物模型；PISA 互作界面分析；突变体结构后果预测。
- **模块**:
  1. 遗传定位（区间界定）
  2. 候选基因筛选（类黄酮通路功能注释）
  3. 系统发育分析（NJ 树，MEGA 7）
  4. 序列多态性分析（Sanger 测序 + 40× 重测序数据）
  5. AF2 单体结构预测（ColabFold）
  6. AF-Multimer 复合物预测（二聚体、三聚体）
  7. PISA 界面分析
  8. 结构比对（RMSD 计算，ChimeraX Matchmaker）
- **训练**: 无（使用预训练 AF2/AF-Multimer 模型）
- **反馈回路**: 结构预测结果与遗传共分离数据交叉验证（PACE 标记）
- **假设**: (1) T/Z 是 MBW 复合物组分；(2) AF2 预测结构可反映生理构象；(3) 突变体表型源于蛋白互作改变。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 遗传定位 | 界定 T/Z 候选区间 | 经典遗传学无法直接鉴定基因 | 输入：RAPD 标记连锁数据；输出：染色体区间 | Results "Identifying T and Z candidate genes" 节 | 无法聚焦候选基因（实测依赖） |
| 系统发育分析 | 确定 T/Z 与已知 MBW 组分的直系同源关系 | 功能注释需要进化证据 | 输入：蛋白序列；输出：NJ 树 | Results "Phylogenetic analyses" 节 | 候选基因功能推断失去依据（实测依赖） |
| AF2 单体预测 | 生成 T/Z/P 蛋白的三维结构模型 | 无实验结构可用 | 输入：氨基酸序列；输出：pLDDT 标注的 PDB 结构 | Results "Protein modeling" 节 | 无法进行后续复合物建模（实测依赖） |
| AF-Multimer 复合物预测 | 生成 MBW 三元复合物模型 | 复合物结构是理解互作的基础 | 输入：多链序列；输出：复合物结构模型 | Results "Computational modeling of a common bean MBW complex" 节 | 无法定义互作界面（实测依赖） |
| PISA 界面分析 | 量化互作界面残基、面积、氢键 | 识别关键互作残基 | 输入：复合物结构；输出：界面残基列表、SAA 百分比 | Results "Modeling of the P bHLH homodimer..." 节 | 无法区分生理/非生理界面（实测依赖） |
| 突变体结构建模 | 预测 tEW、zEW 突变蛋白的结构后果 | 解释突变表型 | 输入：突变序列；输出：突变体结构模型 | Results "Structural prediction for mutant T and Z alleles" 节 | 突变机制无法从序列层面解释（实测依赖） |

## 09 关键公式符号
不适用（本文无数学公式；核心定量指标为 RMSD、pLDDT、SAA 百分比，均为结构生物学标准度量，非公式化模型）。

## 10 实验设计与证据链
- **数据集/群体**: 
  - 遗传定位：F2 群体（4-68、4-76、6-273、6-160.161），n = 60-225
  - 种质多样性：Middle America Diversity Panel (MDP, n=284) + Andean Diversity Panel (ADP, n=256)
  - 突变体系：65-73（t65-73）、Earliwax（tEW + zEW）、PI 632734（tPI632734）
- **指标**: 共分离（cosegregation）、氨基酸序列一致性、pLDDT、RMSD、SAA 百分比
- **基线**: 拟南芥 TT2/TT8/TTG1 复合物（已知互作模式）；WER-EGL3 共晶结构（PDB 6KKS, 7FDL）
- **预算/仪器**: 未提供
- **oracle 输入**: 遗传定位数据（Brady et al. 1998）作为候选基因筛选的 ground truth
- **评测协议**: PACE 标记基因分型 + 表型关联；结构预测质量以 pLDDT 评估；复合物模型以 RMSD 与已知结构比对验证

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| T/Z 候选基因定位 | T 位于 9 号染色体区间，Z 位于 3 号染色体区间 | 与 RAPD 标记 OM19400/AM10560 的连锁 | T 候选区间 10.11-11.53 Mb；Z 区间 33.70-35.11 Mb | 候选基因位于预期区间 | 未排除区间内其他基因 | Results "Identifying T and Z candidate genes" 节 |
| 系统发育分析 | T 为 TTG1 直系同源，Z 为 TT2 直系同源 | 与拟南芥、苜蓿、大豆、豌豆等 22 个物种序列比对 | T 与 TTG1 聚为一支，Z 与 TT2 聚为一支 | T/Z 分别编码 WDR 和 MYB 蛋白 | 系统发育不能证明功能等价 | Results "Phylogenetic analyses" 节 |
| 突变体序列分析 | t65-73 为 39 bp 框内缺失，tEW 为 1 bp 缺失，zEW 为 K105N 替换 | 与 5-593 参考序列比对 | 确认三种突变 | 突变与表型共分离 | 未做互补实验 | Results "T WDR and z MYB polymorphisms" 节 |
| AF2 单体结构预测 | T 形成七叶 β-propeller，Z 为 R2R3-MYB 折叠 | pLDDT > 90（T 82% 残基；Z MYB 结构域） | 结构模型与实验结构 RMSD < 2.6 Å | 预测结构可靠 | 未覆盖无序区 | Results "Protein modeling" 节 |
| AF-Multimer 三元复合物预测 | Z MYB/P bHLH/T WDR 可形成稳定复合物 | 与大豆、拟南芥复合物预测对比 | 鉴定 Z-T 互作界面含 β-MoRF；P-T 界面含保守残基 | 首次获得植物 MBW 复合物计算模型 | 无实验验证（如 co-IP、Y2H） | Results "Computational modeling of a common bean MBW complex" 节 |
| 突变体复合物建模 | tEW 破坏 WDR 支架，zEW 破坏 DNA 结合 | 突变体 vs 野生型复合物模型对比 | tEW 缺失第 6/7 叶导致 P 异常结合；zEW K105N 消除 DNA 主沟互作 | 突变机制可解释 | 预测的异常界面可能非生理性 | Results "Effects of mutant Z MYB and T WDR proteins" 节 |

## 11 结论正确解读
- **任务范围**: 本文仅鉴定 T/Z 候选基因并预测其蛋白结构及复合物互作，未进行转基因互补、酵母双杂交或体外结合实验验证。
- **oracle/真值输入**: 遗传定位数据（Brady et al. 1998）是候选基因筛选的 ground truth；AF2 预测结构以 pLDDT 和与实验结构 RMSD 作为间接验证。
- **端到端状态**: 非端到端——从基因型到表型的因果链未闭合（无功能实验）。
- **算力成本**: 未提供（ColabFold 为免费云服务，但具体资源未说明）。
- **历史数据依赖**: 依赖 Brady et al. (1998) 的 RAPD 标记数据；依赖 Phytozome 参考基因组注释。
- **模型依赖**: 全部结构结论依赖 AF2/AF-Multimer 预测，无实验结构验证。
- **最难情形**: 无序区（IDR）的构象采样；tEW 复合物中预测的异常 P 结合界面可能为假阳性。
- **群体/领域边界**: 结论仅适用于菜豆（及近缘豆科）；MBW 复合物结构模型为计算预测，需实验验证。
- **不确定性**: 作者明确标注 tEW 复合物界面「需要实验验证」；zEW 的 K105N 效应基于与 WER-DNA 共晶结构的类比推断。
- **有边界的复述**: 在菜豆中，T 和 Z 分别编码 TTG1 类 WDR 蛋白和 TT2 类 R2R3-MYB 蛋白；AF2 预测表明二者与 P bHLH 形成三元复合物，Z 的 β-MoRF 基序介导与 T 的互作；tEW 和 zEW 突变分别通过破坏 WDR 支架和 MYB-DNA 结合来影响复合物功能——以上均为计算预测，未经实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 复合物模型未经实验验证 | 所有互作界面来自 AF2/AF-Multimer 预测 | 酵母双杂交、共免疫沉淀、晶体结构解析 | Results "Computational modeling of a common bean MBW complex" 节末尾 |
| tEW 复合物中异常界面可能非生理性 | P bHLH 与 tEW WDR 的异常结合位点存在空间冲突 | 需实验验证该界面是否真实存在 | Results "Effects of mutant Z MYB and T WDR proteins" 节 |
| 突变体功能后果未做体内验证 | K105N 对 DNA 结合的影响基于与 WER 的类比 | 电泳迁移率变动分析（EMSA）、报告基因实验 | Results "Structural prediction for mutant T and Z alleles" 节 |
| 未进行互补实验 | 候选基因身份仅基于共分离和系统发育 | 转基因互补验证 T/Z 功能 | Results "Identifying T and Z candidate genes" 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| AF-Multimer 对三元复合物的预测可靠性未与实验数据对比 | AF-Multimer 对多蛋白复合物的预测准确率低于二聚体；本文仅与 WER-EGL3 二聚体片段比对 | 若复合物拓扑错误，所有互作界面结论失效 | 用交联质谱（XL-MS）或共沉淀验证预测界面 | Methods "Protein structure predictions" 节；AF-Multimer 已知局限 |
| β-MoRF 基序的鉴定依赖 AF2 单体预测的无序区注释 | 无序区预测（如 IUPred3）与 AF2 pLDDT 的一致性未系统评估；β-MoRF 在单体中可能并非完全无序 | β-MoRF 是本文核心新发现，若注释不可靠则结论弱化 | 用圆二色谱或 NMR 验证单体无序性；突变 β-MoRF 残基做结合实验 | Results "Computational modeling of a common bean MBW complex" 节 |
| 遗传定位区间较大，候选基因筛选依赖功能注释 | 区间内可能还有其他类黄酮相关基因未被排除 | T/Z 身份若错误，后续所有分析失去基础 | 对更多突变体等位基因测序；单倍型分析 | Results "Identifying T and Z candidate genes" 节 |
| 突变体表型与分子机制的因果链未闭合 | tEW 的 1 bp 缺失和 t65-73 的 39 bp 缺失可能通过 mRNA 降解而非蛋白结构改变起作用 | 若突变导致无义突变介导的 mRNA 降解，则结构预测失去意义 | 检测突变体 mRNA 水平；western blot 检测蛋白 | Results "T WDR and z MYB polymorphisms" 节 |
| 种质多样性筛选仅用两个 PCR 标记 | MDP/ADP 的筛选只覆盖 T/Z 两个位点，未评估其他修饰基因 | 部分着色表型可能受多基因影响 | 全基因组关联分析（GWAS） | Results "T and Z gene diversity" 节 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **β-MoRF 作为 TF 复合物互作基序的检测方法**：本文展示了如何用 AF2 单体预测 + AF-Multimer 复合物预测的组合，识别「无序→有序」的偶联折叠结合基序。可迁移至 TF-DNA 研究：预测 TF 的 DNA 结合域（DBD）中是否存在类似 β-MoRF，在结合 DNA 或辅因子时发生无序-有序转变。
2. **突变体结构后果预测流程**：对自然突变体等位基因进行 AF2 建模，比较突变体与野生型的结构差异（RMSD、界面残基变化），可系统预测突变如何影响蛋白互作。可迁移至 TF 突变体（如癌症相关 TF 突变）对 DNA 结合亲和力或辅因子招募的影响预测。
3. **PISA 界面分析的定量指标**：SAA 百分比、氢键网络、界面残基列表可作为互作强度的结构代理指标。可迁移至 TF-DNA 界面分析：用类似指标量化 TF 与 DNA 的接触面积和关键碱基接触。
4. **多物种保守性 + 结构预测的交叉验证**：本文用系统发育树 + 序列保守性 + 结构 RMSD 三重证据支持候选基因身份。可迁移至 TF 研究：对未知 TF 进行直系同源鉴定时，结合结构预测可提高可信度。
5. **「预测界面」与「生理界面」的区分意识**：作者对 tEW 复合物中可能的假阳性界面保持警惕，提示在 AI 结构预测中需对异常界面持怀疑态度。可迁移至 TF-DNA 对接：AF2 预测的 TF-DNA 复合物需用实验（如 EMSA、SELEX）验证。

## 15 与已有知识连接
- **MBW 复合物研究**：本文与拟南芥 TT2/TT8/TTG1 复合物研究（Baudry et al. 2004; Xu et al. 2015）直接衔接，将已知的 MBW 互作模式扩展到菜豆，并首次提供结构模型。可对比：拟南芥中 MYB-bHLH 互作依赖 R3 域的保守残基，本文确认了菜豆 Z MYB 中对应残基的保守性。
- **WDR 蛋白结构**：本文 T WDR 的七叶 β-propeller 结构与人类 WDR5、酵母 Tup1 等已知 WDR 结构域一致（Smith et al. 1999; Jain & Pandey 2018），支持 AF2 预测的可靠性。
- **TF 无序区功能**：本文 β-MoRF 发现与动物系统中 TF 无序区介导相分离和增强子组装的研究（Boija et al. 2018; Sabari et al. 2018）形成跨物种呼应，提示植物 TF 复合物可能也存在类似机制。
- **AlphaFold2 在复合物预测中的应用**：本文与 AF-Multimer 在其他蛋白复合物预测中的应用（Evans et al. 2021; Bryant et al. 2022）一致，但本文是少数将 AF-Multimer 应用于植物 TF 复合物的案例。
- **可迁移方向** [Analysis]：本文方法可直接迁移至「TF-DNA 结合机制 × AI」课题——用 AF2 预测 TF 单体和 DNA 结合域，用 AF-Multimer 预测 TF-辅因子复合物，结合 PISA 分析识别关键互作残基，再用突变体验证。尤其适用于缺乏实验结构的非模式植物 TF。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**: TF-DNA 结合界面中 β-MoRF 基序的系统鉴定与功能验证
   - **来源局限/观察**: 本文首次在植物 MBW 复合物中发现 β-MoRF 介导 MYB-WDR 互作；TF-DNA 结合中是否也存在类似「无序→有序」转变尚未系统研究。
   - **核心假设**: 植物 R2R3-MYB 家族中，与 bHLH 或 WDR 互作的 R3 域附近存在保守的 β-MoRF 基序，且该基序在 DNA 结合时也参与界面形成。
   - **初步方法**: 对菜豆、拟南芥、水稻等物种的 R2R3-MYB 蛋白进行 AF2 单体预测，用 IUPred3/DISOPRED3 注释无序区；用 AF-Multimer 预测 MYB-DNA 和 MYB-bHLH 复合物；筛选候选 β-MoRF 基序；用 EMSA 和酵母双杂交验证突变效应。
   - **验证方式**: 体外结合实验（EMSA、ITC）+ 体内报告基因实验。
   - **创新状态**: unverified

2. **候选名称**: 自然突变体等位基因的「结构-功能」预测流程标准化
   - **来源局限/观察**: 本文对 tEW、t65-73、zEW 三种突变体进行了结构预测，但流程未系统化；该方法可推广至其他作物 TF 突变体。
   - **核心假设**: 对 TF 基因自然突变体进行 AF2 结构预测 + PISA 界面分析，可优先排序候选致病变异（影响 DNA 结合 vs 影响辅因子互作）。
   - **初步方法**: 收集作物 TF 基因的已知突变体等位基因；AF2 预测野生型和突变体结构；计算 RMSD、界面残基变化、pLDDT 差异；与表型数据关联。
   - **验证方式**: 对预测「破坏 DNA 结合」的突变体进行 EMSA；对预测「破坏辅因子互作」的突变体进行 Y2H。
   - **创新状态**: unverified

3. **候选名称**: 植物 MBW 复合物与 DNA 共结合模型的全原子模拟
   - **来源局限/观察**: 本文仅建模了蛋白-蛋白互作，未包含 DNA；MBW 复合物如何协同结合靶基因启动子仍未知。
   - **核心假设**: MBW 三元复合物通过 MYB 的 R3 域和 bHLH 的碱性区协同识别 DNA 基序，且 WDR 蛋白不直接接触 DNA 但稳定复合物构象。
   - **初步方法**: 用 AF-Multimer 预测 MBW-DNA 四元复合物；用分子动力学（MD）模拟验证复合物稳定性；用 PISA 和 DNA 足迹法预测结合位点。
   - **验证方式**: 表面等离子共振（SPR）或荧光各向异性测量结合亲和力；DNase I 足迹法验证结合位点。
   - **创新状态**: unverified

4. **候选名称**: 豆科作物 TF-DNA 结合特异性的跨物种比较
   - **来源局限/观察**: 本文发现 T WDR 在豆科中高度保守（98-93% 一致性），但 Z MYB 的 C 端变异大；这种保守性模式是否反映 DNA 结合特异性差异未知。
   - **核心假设**: 豆科 MYB 的 DNA 结合域高度保守，但 C 端调控域变异导致辅因子互作特异性差异，进而产生物种特异的类黄酮谱。
   - **初步方法**: 对豆科 MYB 进行系统发育 + 结构比对；用 DAP-seq 或 SELEX 比较不同物种 MYB 的 DNA 结合基序；用 AF-Multimer 预测跨物种 MBW 复合物。
   - **验证方式**: 体外 DNA 结合芯片；转基因互补实验。
   - **创新状态**: unverified

5. **候选名称**: AF2 预测界面与实验互作数据的系统比较——以植物 TF 复合物为对象
   - **来源局限/观察**: 本文的复合物模型未经实验验证；AF-Multimer 在植物 TF 复合物上的预测准确率缺乏基准测试。
   - **核心假设**: AF-Multimer 对植物 TF 复合物的预测准确率与动物系统相当，但对含无序区的互作界面（如 β-MoRF）预测可靠性较低。
   - **初步方法**: 收集已有实验结构的植物 TF 复合物（如拟南芥 MYB-bHLH）；用 AF-Multimer 重新预测并与实验结构比对；系统评估 pLDDT、PAE 与预测准确率的关系。
   - **验证方式**: 与 PDB 实验结构比对；对无实验结构的复合物用交联质谱验证。
   - **创新状态**: unverified