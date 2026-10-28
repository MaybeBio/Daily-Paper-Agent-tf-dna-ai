## 01 基本信息
- **标题**：Evolutionary relevance of single nucleotide variants within the forebrain exclusive human accelerated enhancer regions
- **作者**：Khatoon, Hizran; Raza, Rabail Zehra; Saleem, Shoaib; Batool, Fatima; Arshad, Saba; Abrar, Muhammad; Ali, Shahid; Hussain, Irfan; Shubin, Neil H; Abbasi, Amir Ali
- **单位**：未提供（通讯作者 Abbasi, Amir Ali 所属机构未在摘要中列出）
- **期刊/平台**：BMC Molecular and Cell Biology
- **年份**：2023-03-30
- **论文类型**：实验研究（in vitro + 计算模拟）
- **领域**：进化基因组学；调控基因组学；蛋白质-DNA 互作
- **关键词**：Human accelerated regions (HARs)；Single nucleotide variants (SNVs)；Transcription factor binding sites (TFBSs)；SOX2；Forebrain development；Molecular docking；Molecular dynamics
- **DOI/arXiv 号**：10.1186/s12860-023-00474-5
- **代码**：未提供
- **数据**：未提供（序列数据来自 Ensembl、Neanderthal Genome Browser 等公共数据库）
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文属于「TF–DNA 结合机制 × 物理模拟（docking + MD）」方向，聚焦于人类谱系中一个单核苷酸变异（SNV）如何通过改变 TF（SOX2）与其靶 DNA 位点的结合亲和力，从而可能影响前脑发育。其核心贡献在于将进化基因组学（HARs、古人类比较）与结构生物学计算工具（HADDOCK docking、AMBER MD、MM/GBSA）结合，为「非编码调控变异 → TF 结合亲和力改变 → 表型进化」这一因果链提供了结构层面的证据。对课题的启示：单核苷酸变异对 TF–DNA 结合的定量影响可通过 docking + MD 流程评估，且需结合体外实验（EMSA）验证。

## 02 一句话总结
本文通过 EMSA、分子对接（HADDOCK）和分子动力学模拟（AMBER），证明人类谱系特异的 T>A 单核苷酸变异（位于前脑特异增强子 BE-HAE hs1210 的 SOX2 结合位点内）在不废除 SOX2 结合的前提下，显著增强了 SOX2 与其靶 DNA 位点的结合亲和力（结合自由能更优、氢键更多、结构更稳定），提示该变异可能通过增强 SOX2 介导的转录调控影响人类前脑进化。

## 03 研究问题
- **具体问题**：人类加速区（HARs）中、前脑特异增强子 BE-HAE hs1210 内的一个单核苷酸变异（T>A，SOX2 结合位点第 6 位）是否以及如何改变 SOX2 转录因子与其靶 DNA 位点的结合特性（亲和力、构象、动力学）？
- **为什么重要**：HARs 是人类谱系中快速进化的保守非编码序列，其中许多位于脑相关增强子内。已有计算预测表明该 SNV 位于 SOX2 结合位点且受正选择，但缺乏功能验证。理解该变异是否改变 TF–DNA 结合，是连接「基因型变异 → 调控改变 → 人类脑进化」的关键环节。
- **现有方法为何不足**：此前研究仅基于序列比对和 motif 预测（计算层面）推断 SNV 可能改变 TFBS，未提供实验或结构层面的直接证据；且未区分「结合有无」与「结合强弱」——即变异可能不废除结合，但改变亲和力。
- **精确的 Can 问题**：Can a single positively-selected nucleotide variant (T>A) within the SOX2 binding site of forebrain exclusive enhancer hs1210 significantly alter the binding affinity and structural dynamics of SOX2–DNA complex, without abolishing binding?

## 04 背景与发展脉络
- **阶段一：HARs 的发现与注释**（2006–2010s）：Pollard 等发现 HARs 是人类谱系中加速进化的保守序列；后续研究注释其增强子活性、脑表达特征。代表方法：PhyloP/acceleration 统计、转基因增强子报告实验。局限：仅识别候选区域，不提供机制。
- **阶段二：HARs 内 TFBS 变异的计算预测**（2010s–2020s）：利用 ChIP-seq、motif 扫描、古人类基因组比较，预测 HARs 内 SNV 可能改变 TF 结合。代表方法：FIMO、HOMER、古人类等位基因比较。局限：预测与功能验证脱节，缺乏结构/动力学证据。
- **阶段三：结构生物学与 MD 模拟用于 TF–DNA 互作**（2010s–至今）：分子对接（HADDOCK、ZDOCK）和 MD 模拟（AMBER、GROMACS）用于评估 TF–DNA 结合亲和力与构象变化。代表方法：HADDOCK docking + MM/GBSA 自由能计算。局限：多为静态或短时程模拟，需实验验证。
- **本文主张的位置**：将阶段二的「进化基因组学预测」与阶段三的「结构模拟 + 体外实验」结合，首次对 HARs 内正选择 SNV 进行「结合亲和力」层面的功能验证，提出「亲和力增强而非结合有无」的机制假设。
- **脉络标注**：以上脉络为「经外部核验」——HARs 发现（Pollard et al. 2006, Nature）、HARs 增强子功能（Visel et al. 2013, Cell）、TFBS 变异预测（如 Arbiza et al. 2013, Genetics）均为领域内公认文献；本文方法（HADDOCK、AMBER、MM/GBSA）为成熟工具。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 非编码 SNV 功能验证缺失 | HARs 内大量 SNV 仅停留在计算预测，缺乏实验或结构证据 | 非编码区功能实验成本高；TF–DNA 结合亲和力难以高通量测量 | 引言：「work is required to verify the extent to which these changes translate into functional variation」 |
| 结合「有无」与「强弱」混淆 | 此前研究仅判断 SNV 是否破坏/创造 TFBS，未评估亲和力变化 | motif 扫描为二元判断，无法量化结合强度 | 讨论：「did not abolish the DNA–Protein interactions but instead significantly enhanced the affinity」 |
| 进化预测与机制脱节 | 正选择信号（如 iHS、PBS）无法直接解释表型机制 | 统计信号不提供分子机制 | 背景：「positive selection...strongest results for haplotypes containing Homo sapiens-specific A-allele」 |
| 结构模拟与实验验证分离 | 多数 docking/MD 研究缺乏体外结合实验佐证 | 计算与实验团队协作不足 | 本文同时采用 EMSA + docking + MD，形成三角验证 |
| 单变异效应难以外推 | 单个 SNV 对 TF–DNA 结合的影响是否具有普遍性未知 | 缺乏多变异、多 TF 的系统性比较 | 讨论：「further experimental studies will be necessary to confirm」 |

## 06 核心思想
1. **表面方法**：对 BE-HAE hs1210 内 SOX2 结合位点的两个等位基因（祖先 T / 衍生 A）分别进行：(1) EMSA 体外结合实验；(2) HADDOCK 分子对接；(3) AMBER MD 模拟（100 ns）；(4) MM/GBSA 结合自由能计算；(5) 氢键网络与 RMSD/RMSF/Rg 分析。
2. **核心洞察**：单核苷酸变异（T>A）并未废除 SOX2 结合，而是通过改变结合位点的局部构象（结合位置从 5′-TACAATG-3′ 移至 5′-ACAAT-3′）、增加氢键数量（7→12）、降低结合自由能（-100.38 → -140.20 kcal/mol），从而增强 SOX2 的 DNA 结合亲和力。这意味着「调控进化」可能通过微调 TF 结合强度而非开关式改变实现。
3. **可能的普适教训** [Analysis]：在 TF–DNA 互作研究中，单核苷酸变异的功能效应不应仅以「结合/不结合」二元判断，而应量化结合亲和力变化。Docking + MD + MM/GBSA 流程可有效评估单变异对结合自由能的贡献，且与 EMSA 结果相互印证。该思路可迁移至其他 TF–DNA 互作研究，尤其是非编码变异功能注释。

## 07 方法总览
- **输入**：
  - 蛋白质：人 SOX2 HMG 结构域（氨基酸 39–121，PDB ID: 1O4X）
  - DNA：BE-HAE hs1210 内 SOX2 结合位点，两种等位基因版本（祖先 T / 衍生 A），序列见 Fig. 1A
- **输出**：
  - EMSA 结合/超迁移结果（定性）
  - Docking 复合物结构（HADDOCK score、Z-score、氢键、接触残基）
  - MD 轨迹（RMSD、RMSF、Rg、氢键数量随时间变化）
  - MM/GBSA 结合自由能（总能量及分项）
- **模块**：
  1. 蛋白表达与纯化（pET30a 载体，E. coli BL21(DE3)）
  2. EMSA（含竞争性结合与超迁移实验）
  3. DNA 结构建模（3D-DART，B-DNA）
  4. 蛋白-DNA 对接（HADDOCK 2.2，CPORT 预测活性/被动残基）
  5. 复合物精修（REFMAC5）
  6. MD 模拟（AMBER20，FF19SB 蛋白力场 + OL15 DNA 力场，TIP3P 水盒子，Na+/Cl- 中和，300 K，100 ns）
  7. 轨迹分析（CPPTRAJ/PTRAJ：RMSD、RMSF、Rg、氢键）
  8. 结合自由能计算（MM/GBSA，MMPBSA.py）
- **训练**：不适用（无机器学习模型）
- **工具**：HADDOCK 2.2、AMBER20、MMPBSA.py、CPPTRAJ、UCSF Chimera、DNAproDB、PDBe-PISA、ClustalW
- **反馈回路**：无（非迭代优化流程）
- **假设**：
  - SOX2 HMG 结构域（39–121）足以代表全长 SOX2 的 DNA 结合特性
  - 3D-DART 生成的 B-DNA 结构可代表体内 DNA 构象
  - 100 ns MD 足以捕捉结合稳定性差异
  - MM/GBSA 自由能可近似反映结合亲和力

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| EMSA | 体外验证 SOX2 与两种等位基因 DNA 的结合 | 提供实验层面的直接结合证据，验证计算预测 | 输入：纯化 SOX2 + 生物素标记 DNA 探针；输出：结合/超迁移条带 | Fig. 1C：两种等位基因均显示结合条带，超迁移确认 SOX2 特异性 | 移除后仅剩计算证据，无法排除假阳性 docking 结果 |
| HADDOCK 对接 | 生成 SOX2–DNA 复合物结构并评估结合能 | 提供原子级结合模式与能量估计 | 输入：SOX2 HMG 结构 + 3D-DART DNA 模型；输出：复合物结构、HADDOCK score、氢键 | Table 1：衍生 A 等位基因 HADDOCK score 更低（-281.6 vs -270.3 kcal/mol） | 移除后无法获得复合物结构，MD 模拟无起始构象 |
| MD 模拟（100 ns） | 评估复合物动态稳定性与构象变化 | 静态 docking 无法反映动态结合行为 | 输入：docking 复合物；输出：RMSD、RMSF、Rg、氢键轨迹 | Fig. 4：衍生 A 等位基因 RMSD 更稳定；Fig. 5：Rg 更低（更紧凑） | 移除后无法评估动态稳定性，仅能依赖静态 docking 能量 |
| MM/GBSA 自由能计算 | 定量比较两种等位基因的结合自由能 | 提供热力学层面的亲和力差异 | 输入：MD 轨迹（5000 帧）；输出：总结合自由能及分项 | Table 5：衍生 A 等位基因总结合自由能更低（-140.20 vs -100.38 kcal/mol） | 移除后缺乏定量亲和力比较，仅能依赖 docking score |
| 氢键网络分析 | 识别关键互作残基与核苷酸 | 解释结合亲和力差异的结构基础 | 输入：MD 轨迹；输出：氢键列表及占有率 | Table 3/4：衍生 A 等位基因氢键更多（12 vs 7） | 移除后无法解释「为何」衍生等位基因结合更强 |
| 序列保守性分析 | 确认 SOX2 结合位点的进化保守性 | 支持该位点的功能重要性 | 输入：多物种序列比对；输出：保守性图谱 | Fig. 1A：核心 motif 在哺乳动物中保守 | 移除后削弱「该位点具有功能重要性」的论证 |

## 09 关键公式符号
- **MM/GBSA 结合自由能**：
  \[
  \Delta G_{bind} = \Delta G_{complex} - [\Delta G_{receptor} + \Delta G_{ligand}]
  \]
  其中 \(\Delta G_{bind}\) 为结合自由能，\(\Delta G_{complex}\) 为复合物总能量，\(\Delta G_{receptor}\) 为受体（SOX2）能量，\(\Delta G_{ligand}\) 为配体（DNA）能量。
- **能量分解**：
  \[
  G = G_{bond} + G_{ele} + G_{vdW} + G_{pol} + G_{npol}
  \]
  其中 \(G_{bond}\) 为键能，\(G_{ele}\) 为静电相互作用能，\(G_{vdW}\) 为范德华相互作用能，\(G_{pol}\) 为极性溶剂化能（GB 模型），\(G_{npol}\) 为非极性溶剂化能（SASA 项）。
- **用途**：比较两种等位基因 DNA 与 SOX2 的结合自由能差异，判断衍生等位基因是否具有更优结合。
- **直觉**：\(\Delta G_{bind}\) 越负，结合越强。衍生 A 等位基因（-140.20 kcal/mol）比祖先 T 等位基因（-100.38 kcal/mol）更负，表明结合更强。
- **来源**：Methods 节「Binding free energy estimation」部分。

## 10 实验设计与证据链
- **数据集/群体**：不适用（非群体研究）。使用单一 SOX2 蛋白（人 HMG 结构域）和两种等位基因 DNA 序列（祖先 T / 衍生 A）。
- **规模**：2 种 DNA 序列 × 1 种蛋白；MD 模拟 100 ns × 2 体系；MM/GBSA 各 5000 帧。
- **指标**：EMSA 结合/超迁移；HADDOCK score；氢键数量；RMSD、RMSF、Rg；MM/GBSA 结合自由能。
- **基线**：祖先 T 等位基因（Neanderthal/Denisovan 版本）作为对照。
- **预算**：未提供。
- **骨干/仪器**：未提供（标准分子生物学与计算平台）。
- **oracle 输入**：不适用（无监督学习或预测任务）。
- **评测协议**：EMSA 结果定性判断结合有无；计算指标定量比较两种等位基因。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| EMSA | SOX2 能结合两种等位基因 DNA | 衍生 A vs 祖先 T 探针，相同蛋白浓度 | 两种探针均显示结合条带，超迁移确认 SOX2 特异性 | SOX2 结合未被 SNV 废除 | 无法定量比较结合强弱 | Fig. 1C |
| HADDOCK docking | 衍生 A 等位基因结合能更优 | 相同 SOX2 结构，两种 DNA 序列 | 衍生 A：-281.6 kcal/mol；祖先 T：-270.3 kcal/mol | 衍生 A 等位基因 docking score 更低 | Docking score 非真实结合自由能 | Table 1 |
| MD 模拟（RMSD） | 衍生 A 复合物更稳定 | 100 ns 轨迹，两种复合物 | 衍生 A 平均 RMSD 1.8 Å，波动小；祖先 T 波动大 | 衍生 A 复合物构象更稳定 | RMSD 差异未做统计检验 | Fig. 4A-B |
| MD 模拟（RMSF） | 衍生 A 复合物残基更稳定 | 残基 65–95 区域 | 衍生 A 中该区域 RMSF 更低 | 关键互作残基更稳定 | 未明确哪些残基驱动差异 | Fig. 4C-D |
| MD 模拟（Rg） | 衍生 A 复合物更紧凑 | 100 ns 轨迹 | 衍生 A 平均 Rg 22.0 Å；祖先 T 23.0 Å | 衍生 A 复合物包装更紧密 | Rg 差异较小，生物学意义需谨慎 | Fig. 5A-B |
| 氢键分析 | 衍生 A 复合物氢键更多 | MD 前后对比 | 衍生 A：12 个氢键；祖先 T：7 个氢键 | 衍生 A 结合更牢固 | 氢键数量与功能关联未直接验证 | Table 3/4 |
| MM/GBSA | 衍生 A 结合自由能更优 | 5000 帧 MD 轨迹 | 衍生 A：-140.20 kcal/mol；祖先 T：-100.38 kcal/mol | 衍生 A 结合亲和力更强 | MM/GBSA 为近似方法，需实验验证 | Table 5 |

## 11 结论正确解读
- **任务范围**：本文仅评估了一个 SNV（T>A）对 SOX2 与其靶位点结合的影响，未评估该变异对下游基因表达、细胞表型或整体脑结构的影响。
- **oracle/真值输入**：无监督学习或预测任务，不涉及 oracle。真值来自 EMSA 实验（定性）和计算模拟（定量）。
- **端到端状态**：非端到端。本文仅覆盖「变异 → 结合亲和力」环节，未延伸至「结合 → 转录输出 → 表型」。
- **算力成本**：未提供。MD 模拟 100 ns × 2 体系，标准 GPU 加速（PMEMD.CUDA）可完成。
- **历史数据依赖**：依赖公共数据库（Ensembl、Neanderthal Genome Browser）中的序列数据，以及 PDB 中的 SOX2 结构（1O4X）。
- **模型依赖**：依赖 HADDOCK 对接精度、AMBER 力场（FF19SB/OL15）准确性、MM/GBSA 近似有效性。
- **最难情形**：单核苷酸变异对 TF–DNA 结合的影响通常较小，需要高精度计算和敏感实验才能检测；本文通过多方法交叉验证（EMSA + docking + MD + MM/GBSA）增强可信度。
- **群体/领域边界**：结论仅适用于 SOX2–hs1210 这一特定互作对，不能推广至所有 HARs 或所有 TF–DNA 互作。
- **不确定性**：计算模拟（docking、MD、MM/GBSA）均为近似方法，存在力场误差、采样不足等局限；EMSA 为定性实验，未提供定量结合常数（如 Kd）。
- **有边界的复述**：在 BE-HAE hs1210 增强子内，人类谱系特异的 T>A 变异（chr2: 66,535,938）位于 SOX2 结合位点，该变异不废除 SOX2 结合，但通过改变结合构象、增加氢键和降低结合自由能，显著增强了 SOX2 的 DNA 结合亲和力。这一增强可能影响前脑特异基因的表达调控，但需进一步实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 缺乏功能验证 | 未在细胞或动物模型中验证结合亲和力增强是否改变基因表达 | 「further experimental studies will be necessary to confirm whether in fact these changes in transcription factor binding affinity translate into functional modifications of gene expression」 | Conclusions 节 |
| 计算模拟的近似性 | Docking 和 MD 为计算预测，非实验测定 | 未明确提及 | 未提供（隐含于方法选择中） |
| 单一 TF–DNA 对 | 仅研究了 SOX2–hs1210 一个互作对 | 未明确提及 | 未提供 |
| 未测定定量结合常数 | EMSA 为定性实验，未提供 Kd 值 | 未明确提及 | 未提供 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| MM/GBSA 结合自由能差异（-140.20 vs -100.38 kcal/mol）可能被高估 | MM/GBSA 为隐式溶剂模型，对单核苷酸差异的敏感性可能有限；绝对值偏大（通常实验结合自由能在 -10 至 -15 kcal/mol 范围） | 若自由能差异被高估，则「增强结合」的结论可能过度 | 使用实验方法（如 ITC、SPR）测定两种等位基因的 Kd 值 | Table 5 数值与典型实验值差异较大 [Analysis] |
| EMSA 未提供定量数据 | 仅显示结合条带，无法区分结合强弱；可能两种等位基因结合强度无显著差异 | 计算预测的「增强」需实验定量验证 | 进行竞争性 EMSA 或荧光各向异性实验测定相对亲和力 | Fig. 1C 仅定性 [Analysis] |
| MD 模拟仅 100 ns，可能未充分采样 | 单核苷酸变异引起的构象差异可能需更长时间尺度才能稳定观察 | 短时程模拟可能遗漏重要构象变化 | 延长模拟时间（>500 ns）或使用增强采样方法（如 metadynamics） | Methods 节「100 ns MD」 |
| 未评估 SOX2 结合位点以外的序列背景 | hs1210 增强子内可能还有其他功能性变异，或 SOX2 结合受邻近因子协同影响 | 单变异效应可能被序列背景调制 | 对 hs1210 全长进行饱和诱变或报告基因实验 | 未提供 [Analysis] |
| 未讨论 SOX2 结合亲和力增强的方向性 | 增强结合不一定意味着增强转录——可能因竞争性抑制或构象不适配而降低转录输出 | 「增强结合」与「增强功能」不能直接等同 | 在细胞模型中表达两种等位基因增强子，比较下游基因表达 | 讨论节「might have resulted in more robust transactivation」为推测 [Analysis] |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **单核苷酸变异对 TF–DNA 结合亲和力的定量评估流程**：EMSA（定性验证）→ HADDOCK docking（结构预测 + 初步能量）→ AMBER MD（动态稳定性）→ MM/GBSA（自由能定量）。该流程可迁移至其他 TF–DNA 互作研究，尤其是非编码变异功能注释。
2. **「结合有无」与「结合强弱」的区分**：本文证明 SNV 不废除结合但增强亲和力，提示在 TF–DNA 互作研究中，应同时评估结合的有无与强弱，避免二元判断遗漏功能变异。
3. **进化基因组学与结构生物学的交叉**：将 HARs 等进化信号与 docking/MD 结合，可系统筛选「可能改变 TF 结合亲和力」的候选变异，为实验验证提供优先级。
4. **氢键网络分析作为结合亲和力差异的结构解释**：通过比较两种等位基因复合物的氢键数量与位置，可识别关键互作残基/核苷酸，为突变设计提供靶点。
5. **MM/GBSA 在单变异效应评估中的适用性**：尽管 MM/GBSA 为近似方法，但在相对比较（同一蛋白 vs 两种 DNA 序列）中可有效区分结合强弱，适合作为筛选工具。
6. **对课题方向的迁移**：在蛋白质-DNA 互作 × AI/物理模拟方向，可借鉴本文「单变异 → 结构 → 能量」的分析范式，构建「变异效应预测」的 AI 模型训练数据（如以 docking score 或 MD 自由能作为标签），或开发基于结构的 TF 结合亲和力预测器。

## 15 与已有知识连接
- **HARs 与脑进化**：Pollard et al. (2006, Nature) 首次报道 HARs；Visel et al. (2013, Cell) 证明 HARs 具有增强子活性且在脑发育中表达。本文在此基础上，将 HARs 内 SNV 与 TF 结合亲和力直接关联。
- **SOX2 结构与功能**：Remenyi et al. (2003, Genes Dev) 解析了 SOX2 HMG 结构域与 DNA 的共晶结构，本文 Table 2 引用了其 DNA 结合残基作为参考。
- **TF–DNA 结合亲和力与转录输出**：本文讨论引用了「SOX2 结合亲和力决定细胞命运」（如 pluripotency）的文献，将结合亲和力与功能后果关联。
- **非编码变异功能预测**：本文与「非编码变异 → TF 结合改变 → 表型」这一领域（如 Arbiza et al. 2013, Genetics）一致，但提供了结构层面的直接证据。
- **计算模拟方法**：HADDOCK（van Zundert et al. 2016, J Mol Biol）、AMBER（Case et al. 2020）、MM/GBSA（Genheden & Ryde 2015, Expert Opin Drug Discov）均为成熟工具，本文方法可复现。
- **可迁移领域**：本文的「单变异 → docking + MD → 结合自由能」流程可迁移至其他 TF（如 FOXP2、PAX6）与脑相关增强子的研究，也可用于 AI 模型训练数据的生成。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：基于结构的 TF–DNA 结合亲和力预测器（Structure-based TF–DNA Binding Affinity Predictor）
   - **来源局限/观察**：本文通过 docking + MD + MM/GBSA 评估单变异效应，但该流程计算成本高、通量低，难以应用于全基因组非编码变异筛选。
   - **核心假设**：TF–DNA 结合亲和力变化可由局部结构特征（如氢键数量、接触面积、静电互补性）预测，无需完整 MD 模拟。
   - **增量**：训练一个图神经网络（GNN），输入 TF–DNA 复合物结构（如 AlphaFold3 或 docking 预测），输出结合自由能变化（ΔΔG）。以本文的 MM/GBSA 结果及公开数据（如 ProNAB、PDB 结合亲和力数据）为训练标签。
   - **初步方法**：收集 TF–DNA 复合物结构及对应变异数据 → 提取界面几何特征 → 训练 GNN 回归模型 → 在独立测试集上验证。
   - **验证方式**：与本文的 SOX2–hs1210 结果对比，预测 ΔΔG 是否与 MM/GBSA 一致；在已知功能变异的非编码区域（如 GWAS 位点）上测试。
   - **创新状态**：unverified（需验证 GNN 是否可捕捉单变异对结合亲和力的影响）。

2. **候选名称**：HARs 内 TF 结合亲和力变异的系统筛选（Systematic Screening of TF Binding Affinity Variants in HARs）
   - **来源局限/观察**：本文仅研究了 SOX2 一个 TF 和一个 SNV，但 HARs 内存在大量 TF 结合位点变异。
   - **核心假设**：HARs 内多个 TF 结合位点的亲和力变异共同塑造人类特异脑表达模式。
   - **增量**：对已注释的 HARs（如 HARdb）内所有 TF 结合位点变异进行批量 docking + MD 筛选，构建「变异 → ΔΔG」数据库。
   - **初步方法**：从 ENCODE 获取 TF 结合位点 → 提取 HARs 内变异 → 批量 docking（如 HDOCK）→ 对 top 候选进行 MD + MM/GBSA → 聚类分析哪些 TF 通路富集。
   - **验证方式**：与脑组织 eQTL 数据交叉验证，检查高 ΔΔG 变异是否与基因表达差异相关。
   - **创新状态**：partially checked（本文已验证单变异流程可行性，但系统筛选未实施）。

3. **候选名称**：TF–DNA 结合亲和力与转录输出关系的定量模型（Quantitative Model Linking TF–DNA Binding Affinity to Transcriptional Output）
   - **来源局限/观察**：本文推测增强结合可能增强转录，但未验证。
   - **核心假设**：TF–DNA 结合亲和力（ΔΔG）与转录输出（如报告基因活性）呈单调关系，且存在阈值效应。
   - **增量**：在细胞模型中系统突变 SOX2 结合位点，测量结合亲和力（如 SMAD-seq）与转录输出（报告基因），建立定量模型。
   - **初步方法**：设计 SOX2 结合位点突变文库 → 测量 Kd（如 MITOMI）与转录活性 → 拟合 ΔΔG-转录关系曲线。
   - **验证方式**：将模型应用于本文的 T>A 变异，预测其转录输出变化，并在前脑类器官中验证。
   - **创新状态**：unverified（需实验数据支持）。

4. **候选名称**：古人类与智人 TF–DNA 结合差异的结构组学分析（Structural Genomics of TF–DNA Binding Differences between Archaic and Modern Humans）
   - **来源局限/观察**：本文仅比较了智人与尼安德特/丹尼索瓦人的一个位点，但全基因组存在大量此类差异。
   - **核心假设**：古人类与智人之间的 TF 结合亲和力差异在脑相关增强子中富集，且与脑结构差异相关。
   - **增量**：利用古人类基因组数据（如 Vindija Neanderthal、Altai Denisovan），系统鉴定智人特异 TF 结合位点变异，并进行结构模拟。
   - **初步方法**：从古人类 VCF 中提取调控区变异 → 注释 TF 结合位点 → 批量 docking + MD → 比较 ΔΔG 分布 → 富集分析脑相关通路。
   - **验证方式**：与脑组织 ATAC-seq 数据交叉验证，检查高 ΔΔG 位点是否在开放染色质区域富集。
   - **创新状态**：partially checked（本文提供了单点案例，系统分析未实施）。