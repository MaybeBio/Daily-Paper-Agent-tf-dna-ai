## 01 基本信息
- **标题**：Sp100A isoform promotes localization of the histone chaperone HIRA to PML nuclear bodies
- **作者与单位**：Della Fera, Ashley N; Arman, Warda; Powers, Maceo E; Cachau, Raul E; Warburton, Alix; McBride, Alison A（单位未提供，推测为 NIH/NIAID 相关实验室，依据为致谢中的 Intramural Research Program of NIAID）
- **期刊/预印本平台**：The Journal of Biological Chemistry
- **年份**：2025-10-16
- **论文类型**：实验研究（含 AI 结构预测与分子动力学模拟）
- **领域**：细胞生物学 / 染色质调控 / 固有免疫；涉及蛋白质-蛋白质互作与亚核结构（PML-NBs）
- **关键词**：Sp100、HIRA、PML nuclear bodies、histone chaperone、H3.3、SUMO-SIM、interferon、keratinocytes
- **DOI/arXiv 号**：10.1016/j.jbc.2025.110814
- **代码**：未提供
- **数据**：RNA-seq 数据（GEO: GSE290877）；结构模型（ModelArchive: ma-7mo0m, ma-0hla7, ma-ew0pl, ma-xw697）
- **阅读日期**：2026-05-13
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：本文核心对象是 **Sp100 蛋白家族（含 DNA 结合域 SAND、HMG 等）与组蛋白伴侣 HIRA 的互作**，以及该互作在 **PML 核体（PML-NBs）** 这一亚核结构中的定位调控。虽非直接研究 TF-DNA 结合，但 Sp100 含 SAND 与 HMG 两个 DNA 结合结构域，且 PML-NBs 是染色质调控与固有免疫的关键枢纽。本文展示了 **AI 结构预测（AlphaFold 3、Chai-1、Boltz-2）+ 分子动力学（MD）模拟** 用于解析多结构域蛋白异构体功能差异的完整流程，对 TF-DNA 互作的结构-功能研究具有直接的方法学迁移价值。

## 02 一句话总结
本文通过 CRISPR 敲除 Sp100 并回补各异构体，证明 **Sp100A 是驱动组蛋白伴侣 HIRA 及其复合物成员（UBN1、ASF1a）定位到 PML 核体的主要异构体**，且该过程依赖 Sp100A 的 SUMO 互作基序（SIM），但不影响干扰素信号的即时转录响应。

## 03 研究问题
- **具体问题**：Sp100 的四个主要异构体（A/B/C/HMG）中，哪一个负责将 HIRA 招募到 PML 核体？其分子机制是什么？
- **为什么重要**：PML-NBs 是染色质动态调控与抗病毒防御的关键枢纽；HIRA 作为 H3.3 组蛋白伴侣，在干扰素刺激基因（ISGs）的表观遗传记忆建立中起核心作用。理解 Sp100 异构体如何差异性地招募 HIRA，有助于阐明固有免疫记忆的分子基础。
- **现有方法为何不足**：此前研究（McFarlane et al., Kleijwegt et al.）已报道 HIRA 定位到 PML-NBs 依赖 Sp100，但均使用 siRNA 敲低或过表达体系，未在完全敲除背景下系统比较各异构体的功能；且 Sp100 异构体功能差异的分子基础（尤其是结构域与无序区的作用）尚不清楚。
- **精确的「Can ... ?」研究问题**：Can the Sp100A isoform alone, in the absence of other Sp100 isoforms, promote the localization of HIRA and its complex members to PML-NBs in human keratinocytes, and is this function dependent on specific sequence motifs such as the SUMO-interacting motif (SIM)?

## 04 背景与发展脉络
> 注：此脉络基于本文引文与讨论部分，属「经外部核验」的领域发展框架。

1. **PML-NBs 的发现与功能研究**：PML 核体作为动态亚核结构，参与染色质调控、DNA 损伤应答与抗病毒防御（引用 1-3）。
2. **Sp100 作为 PML-NBs 核心组分的鉴定**：Sp100 是 PML-NBs 的标志性蛋白，含 SAND 与 HMG 两个 DNA 结合结构域，提示其可能直接参与染色质互作（引用 20）。
3. **HIRA 与 H3.3 沉积**：HIRA 作为 H3.3 特异性组蛋白伴侣，在基因体与调控元件处沉积 H3.3；近年研究发现 HIRA 可被招募到 PML-NBs（引用 12-15）。
4. **Sp100 与 HIRA 的关联**：McFarlane et al.（2019）与 Kleijwegt et al.（2023）先后报道 HIRA 定位到 PML-NBs 依赖 Sp100，但机制不清（引用 17, 18）。
5. **本文位置**：在完全敲除背景下，首次系统比较四个 Sp100 异构体的功能，明确 Sp100A 为关键异构体，并利用 AI 结构预测 + MD 模拟提出结构-功能假说。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Sp100 异构体功能冗余/重叠 | 此前 siRNA 敲低无法区分各异构体贡献 | 四个异构体共享 N 端 483 个氨基酸，仅 C 端不同；siRNA 同时敲低所有异构体 | Results 节 "Generation of Sp100-deficient NIKS cell lines" |
| HIRA 定位到 PML-NBs 的分子机制不清 | 已知依赖 Sp100，但具体结构域/基序未知 | 缺乏完全敲除背景下的系统回补实验 | Results 节 "The Sp100A isoform promotes HIRA localization to PML-NBs" |
| Sp100 长异构体（B/C/HMG）的 C 端结构域功能不明 | 长异构体含 SAND/HMG 等 DNA 结合域，但不促进 HIRA 定位 | 作者推测 C 端结构域可能通过空间位阻或构象变化影响 N 端互作界面 | Discussion 节；结构预测部分（Fig. S7） |
| 干扰素刺激后 HIRA 定位的诱导机制 | IFN 增强 HIRA-PML-NBs 共定位，但机制不清 | 可能与 IFN 诱导的 SUMOylation 增强有关 | Results 节 Fig. 3；Discussion 节 |
| 结构预测全局置信度低 | AI 模型整体 pLDDT < 50 | Sp100 含大量无序区（IDRs），仅结构化结构域（HRS/SAND/HMG）置信度高 | Results 节 "Structural prediction"；Fig. S7 |

## 06 核心思想
1. **表面方法**：CRISPR-Cas9 敲除 Sp100 → 回补各 YFP-Sp100 异构体 → 免疫荧光共定位分析 HIRA/PML-NBs → 定点突变解析功能基序 → AI 结构预测 + MD 模拟解释异构体差异。
2. **核心洞察**：**Sp100 异构体功能差异不取决于其 DNA 结合结构域（SAND/HMG），而取决于 N 端共享区域中特定基序（如 SIM）的可及性**。长异构体因 C 端结构域的存在可能通过构象效应遮蔽 N 端互作界面，从而丧失招募 HIRA 的能力。
3. **可能的普适教训** [Analysis]：多结构域蛋白的异构体功能差异，不能仅从结构域组成推断；**无序区（IDRs）与结构域间的动态构象平衡**可能决定功能特异性。AI 结构预测 + MD 模拟是解析此类「构象调控」问题的有效组合。

## 07 方法总览
- **输入**：人角质形成细胞系 NIKS（正常二倍体）；Sp100 敲除克隆；YFP-Sp100 异构体表达质粒
- **输出**：HIRA/PML-NBs 共定位频率（免疫荧光定量）；RNA-seq 转录组差异
- **模块**：
  1. CRISPR 敲除与克隆筛选（5 条 gRNA 靶向 Sp100 外显子 3/6/8）
  2. 异构体回补表达（YFP-Sp100A/B/C/HMG）
  3. 免疫荧光共定位定量（手动计数，≥30 核/条件）
  4. 定点突变（SIM、SUMO、HP1、磷酸化位点等）
  5. AI 结构预测（AlphaFold 3、Chai-1、Boltz-2）
  6. MD 模拟（YASARA，AMBER14 力场，1000 ns）
  7. RNA-seq（±IFNα 12h/48h，3 重复）
- **训练**：不适用（无监督学习/预训练模型直接推理）
- **工具**：CHOPCHOP（gRNA 设计）、FACS、共聚焦显微镜、YASARA 2025.1.13、AIUPRED、VoroMQA、ProQ3
- **反馈回路**：结构预测 → MD 弛豫 → 突变设计 → 功能验证 → 结构解释
- **假设**：Sp100 异构体功能差异源于结构域组成与构象动态；HIRA 招募依赖 SUMO-SIM 互作
- **文字流程**：敲除 Sp100 → 确认无 Sp100 表达 → 回补各异构体 → IFN 刺激 → 免疫荧光检测 HIRA 是否共定位 PML-NBs → 定量比较 → 对 Sp100A 做系列突变 → 鉴定关键基序 → AI 预测结构 + MD 模拟解释机制 → RNA-seq 排除转录组层面的间接效应

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CRISPR Sp100 KO | 消除所有内源 Sp100 异构体 | 在无背景条件下测试各异构体功能 | 输入：NIKS 细胞 + 5 gRNA；输出：无 Sp100 表达的克隆 | Results 节 Fig. 1；Western blot 验证（Fig. S1B） | 无法区分异构体功能（此前 siRNA 的局限） |
| 异构体回补 | 逐一测试 A/B/C/HMG 功能 | 确定哪个异构体驱动 HIRA 定位 | 输入：YFP-Sp100 质粒；输出：各异构体表达细胞 | Results 节 Fig. 5 | 无法归因具体异构体 |
| 免疫荧光共定位定量 | 量化 HIRA 与 PML-NBs 的关联 | 功能读出的核心指标 | 输入：固定细胞 + 抗体；输出：% 核含 HIRA-PML 共定位 | Results 节 Fig. 3, 5, 6 | 无法评估 HIRA 定位 |
| 定点突变系列 | 解析 Sp100A 功能基序 | 确定哪些序列特征负责 HIRA 招募 | 输入：突变质粒；输出：突变体定位表型 | Results 节 Fig. 6, 7 | 无法鉴定关键残基 |
| AI 结构预测（AF3/Chai-1/Boltz-2） | 生成 Sp100 异构体 3D 模型 | 解释异构体功能差异的结构基础 | 输入：氨基酸序列；输出：pLDDT 标注的 3D 模型 | Results 节 "Structural prediction"；ModelArchive | 缺乏结构解释 |
| MD 模拟（YASARA） | 评估模型动态稳定性 | 验证预测结构、识别半稳定区域 | 输入：AI 模型；输出：RMSF、构象系综 | Results 节 "Molecular dynamics"；Fig. S9 | 无法评估构象动态 |
| RNA-seq | 排除转录组层面的间接效应 | 确认 Sp100 KO 不影响 IFN 信号通路 | 输入：±IFN RNA；输出：差异表达基因 | Results 节 Fig. 8 | 无法排除间接效应 |

**消融效应区分**：CRISPR KO 与回补实验为「实测消融效应」；结构预测与 MD 为「预期效应」支撑（未做计算预测驱动的功能验证突变，如预测界面残基突变）。

## 09 关键公式符号
**不适用**。本文为实验生物学论文，无定量数学模型或核心公式。结构预测与 MD 模拟使用既有软件（AlphaFold 3、Chai-1、Boltz-2、YASARA），未提出新公式。MD 模拟参数（AMBER14 力场、PME、NPT 298K/1atm）为行业标准设置，非本文创新。

## 10 实验设计与证据链
- **数据集/群体**：NIKS 细胞（自发永生化人角质形成细胞）；5 个 Sp100 KO 克隆 + 2 个载体对照克隆
- **规模**：免疫荧光 ≥30 核/条件/重复，2-3 次独立实验；RNA-seq 3 重复/条件
- **指标**：% 核含 HIRA-PML 共定位；% 核含 Sp100-PML 共定位；蛋白表达水平（Western blot 定量）
- **基线**：载体对照（YFP 空载体）转染的 Sp100 KO 细胞
- **预算**：未提供
- **骨干/仪器**：共聚焦显微镜（Leica TCS-SP8）；Illumina NextSeq
- **oracle 输入**：不适用（无监督/预测任务）
- **评测协议**：手动计数共定位，未使用自动共定位系数（如 Pearson/Mander's）；未设盲法

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| Sp100 KO 细胞生成 | CRISPR 可完全消除 Sp100 表达 | KO vs 载体对照；±IFN | 5/7 克隆无 Sp100 蛋白 | Sp100 被成功敲除 | 未检测残留低水平表达 | Results 节 Fig. 1, S1 |
| 角质形成细胞分化 | Sp100 KO 不影响分化 | KO vs 对照 raft 培养 | 组织学无差异 | Sp100 非分化必需 | 未做定量分化标志物 | Results 节 Fig. S2 |
| HIRA 定位依赖 Sp100 | Sp100 KO 消除 HIRA-PML 共定位 | KO vs 对照 ±IFN | KO 中 HIRA 几乎不共定位 PML | Sp100 是 HIRA 定位的必要条件 | 未排除其他蛋白参与 | Results 节 Fig. 3 |
| 异构体回补 | Sp100A 特异性驱动 HIRA 定位 | A/B/C/HMG 回补 ±IFN | 仅 Sp100A 高效恢复 HIRA 共定位 | Sp100A 是主要功能异构体 | 长异构体在特定条件下可能也有微弱功能 | Results 节 Fig. 5 |
| Sp100A 突变分析 | SIM 基序对 HIRA 招募关键 | 7 种突变体 ±IFN | mSIM 在无 IFN 时丧失招募；IFN 可部分恢复 | SIM 参与但非唯一决定因素 | 未做 SIM 与 HIRA 直接结合实验 | Results 节 Fig. 6, 7 |
| RNA-seq | Sp100 KO 不影响 IFN 转录应答 | KO vs 对照 ±IFN 12h/48h | 无显著差异 | HIRA 定位缺失不影响即时 IFN 信号 | 未检测表观遗传记忆（二次刺激） | Results 节 Fig. 8 |
| 结构预测 + MD | 异构体构象差异解释功能差异 | AF3/Chai-1/Boltz-2 交叉验证 | 长异构体 C 端可能遮蔽 N 端互作界面 | 构象假说与功能数据一致 | 预测未经突变验证 | Results 节 "Structural prediction"；Fig. S7-S9 |

## 11 结论正确解读
- **任务范围**：本文仅证明 Sp100A 在角质形成细胞中驱动 HIRA 及其复合物成员（UBN1、ASF1a）定位到 PML-NBs；未涉及 HIRA 的组蛋白沉积活性是否受 Sp100A 调控。
- **oracle/真值输入**：共定位判定依赖手动计数，无自动量化；未使用共定位统计系数。
- **端到端状态**：非端到端。结构预测与 MD 模拟为独立计算分析，未与功能突变实验闭环验证。
- **算力成本**：未提供。
- **历史数据依赖**：RNA-seq 比对至 hg19（较旧参考基因组），可能遗漏新注释转录本。
- **模型依赖**：AlphaFold 3、Chai-1、Boltz-2 预测的 IDR 区域置信度低（pLDDT < 50），MD 模拟基于低置信度模型，结论需谨慎。
- **最难情形**：IFN 刺激下 mSIM 突变体部分恢复 HIRA 招募，说明存在 SIM 非依赖的补偿机制，机制未完全阐明。
- **群体/领域边界**：结论限于人角质形成细胞（NIKS）；其他细胞类型或体内环境可能不同。
- **不确定性**：Sp100A 与 HIRA 之间未检测到直接蛋白互作（作者引用他人数据说明无直接互作），中间衔接分子未知。
- **有边界的复述**：在人角质形成细胞中，Sp100A 通过其 SIM 基序（可能依赖 SUMO 化修饰）驱动 HIRA 复合物定位到 PML-NBs；该过程对 IFN 即时转录应答非必需，但可能参与 ISGs 的表观遗传记忆建立。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未检测直接蛋白互作 | Sp100A 与 HIRA 之间无直接结合证据 | 需鉴定衔接蛋白或复合物 | Discussion 节 |
| mSIM 表型不完全 | IFN 可部分恢复 mSIM 突变体的 HIRA 招募 | 需解析 IFN 诱导的补偿机制 | Discussion 节 |
| 结构预测置信度有限 | 整体 pLDDT < 50，仅结构域可信 | 需实验结构（如 Cryo-EM）验证 | Results 节 "Structural prediction" |
| 细胞类型局限 | 仅 NIKS 角质形成细胞 | 需在其它细胞类型验证 | Discussion 节 |
| 未检测表观遗传记忆 | RNA-seq 仅覆盖即时 IFN 应答 | 需二次刺激实验检测记忆效应 | Discussion 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 共定位定量依赖手动计数 | 主观偏差；未报告计数者间一致性 | 核心表型读出的可靠性 | 使用自动共定位分析（如 Coloc 2）或深度学习分割 | Methods 节 "Image analysis" |
| 回补实验未做剂量匹配 | 各异构体表达水平差异可能影响表型 | 功能差异可能源于表达量而非内在活性 | 定量 Western blot 校正；使用等摩尔表达系统 | Results 节 Fig. S5 |
| mSIM 突变体在 IFN 下恢复功能 | 可能说明 SIM 非必需，或存在替代 SUMO 互作界面 | 对 SIM 核心作用的结论构成挑战 | 构建 SIM + SUMO 双突变；检测 SUMO 化水平 | Results 节 Fig. 7 |
| 结构预测未与功能突变闭环 | 构象假说（C 端遮蔽）无直接实验验证 | 计算预测可能过度解读 | 设计 C 端截短或结构域交换突变体 | Results 节 "Structural prediction" |
| RNA-seq 仅 2 个时间点 | 可能遗漏早期或晚期差异表达 | 无法排除 Sp100 对 IFN 信号的间接影响 | 增加时间点；ATAC-seq 检测染色质可及性 | Results 节 Fig. 8 |
| 未检测 H3.3 沉积 | 文章标题强调 HIRA 定位，但未验证功能后果 | HIRA 定位 ≠ H3.3 沉积功能 | ChIP-seq 检测 H3.3 在 ISGs 的沉积 | Discussion 节 |

## 14 学到什么
> **Agent 提炼的知识候选**

1. **异构体功能解析的实验范式**：CRISPR 完全敲除 + 逐一回补各异构体，是解析多异构体蛋白功能差异的金标准。可迁移至 TF 异构体（如 p53、RUNX 家族）的 DNA 结合特异性研究。
2. **AI 结构预测 + MD 模拟的「构象假说」生成流程**：当实验数据表明序列高度相似的异构体功能迥异时，可用 AF3/Chai-1/Boltz-2 多方法交叉验证 + MD 模拟评估构象动态，生成「C 端结构域遮蔽 N 端互作界面」类假说。对 TF-DNA 互作研究，可迁移至解释同一 TF 不同剪接异构体的 DNA 结合差异。
3. **SUMO-SIM 互作在亚核结构组装中的核心作用**：PML-NBs 作为 SUMO 化枢纽，通过 SUMO-SIM 网络招募底物。对 TF 研究，需关注 TF 的 SUMO 化修饰状态如何影响其在亚核结构（如 PML-NBs、SC35 斑点）中的定位与活性。
4. **功能冗余与特异性的结构基础**：Sp100 异构体共享 N 端但功能不同，提示**结构域排列顺序与空间构象**（而非结构域组成）决定功能。对 TF-DNA 研究，需考虑 DNA 结合域与调控域之间的构象偶联。
5. **IFN 诱导的 SUMOylation 全局增强**：IFN 刺激增强 SUMO-SIM 互作，可补偿单个 SIM 突变。提示在研究 TF 的 SUMO 调控时，需考虑刺激条件下的全局 SUMO 化变化。
6. **阴性结果的价值**：Sp100 KO 不影响 IFN 即时转录应答，排除了 HIRA 定位在即时信号传导中的作用，将功能聚焦于表观遗传记忆。对 TF 研究，区分「即时转录调控」与「长期表观遗传印记」是重要的实验设计思路。

## 15 与已有知识连接
- **PML-NBs 与 SUMO-SIM 网络**：与 Shen et al. (2006) 关于 PML 作为 SUMO E3 连接酶的工作、以及 Banani et al. (2016) 关于 SUMO-SIM 驱动相分离的综述直接相关。本文支持 PML-NBs 通过 SUMO-SIM 网络招募底物的模型。
- **HIRA 与 H3.3 沉积**：与 Goldberg et al. (2010) 关于 HIRA 在基因体沉积 H3.3 的工作、以及 Rai et al. (2011) 关于 HIRA 在衰老中作用的研究衔接。本文补充了 HIRA 亚核定位的调控层面。
- **Sp100 与固有免疫**：与 Guldner et al. (1992) 首次克隆 Sp100、以及 Negorev & Maul (2001) 关于 Sp100 异构体的综述直接相关。本文首次在完全敲除背景下区分异构体功能。
- **AI 结构预测在染色质蛋白中的应用**：与 Abramson et al. (2024, AF3 论文)、Chai-1 (2024) 和 Boltz-2 (2024) 的方法学进展衔接。本文展示了多方法交叉验证 + MD 弛豫的实践流程。
- **可迁移领域**：TF 异构体功能分化（如 p53 异构体）、固有无序蛋白（IDPs）在转录调控中的作用、亚核结构（相分离凝聚体）对 TF 活性的调控。

## 16 研究想法
> **Agent 生成的研究候选**

1. **候选名称**：TF 异构体 DNA 结合特异性的构象调控机制研究
   - **来源局限/观察**：本文发现 Sp100 异构体功能差异源于构象而非结构域组成；TF 异构体（如 p53、FOXP3）常共享 DNA 结合域但功能迥异
   - **核心假设**：TF 异构体的 C 端调控域通过构象遮蔽/暴露 DNA 结合域，调控其结合特异性与亲和力
   - **初步方法**：对目标 TF 异构体做 AF3/Chai-1 多方法预测 + 长时程 MD（>1 μs）模拟，比较 DNA 结合域的可及性与构象系综；设计 C 端截短突变体验证
   - **验证方式**：SMF（单分子荧光）或 HT-SELEX 测量 WT vs 截短体的 DNA 结合谱
   - **创新状态**：unverified

2. **候选名称**：SUMO-SIM 网络调控 TF 亚核定位的计算模型
   - **来源局限/观察**：本文证明 Sp100A 的 SIM 对 HIRA 招募关键，但 IFN 可部分补偿；PML-NBs 是 SUMO 化枢纽
   - **核心假设**：TF 的 SUMO 化状态与 PML-NBs 的 SUMO 化水平共同决定其亚核定位，可用化学计量模型描述
   - **初步方法**：构建 SUMO-SIM 互作的热力学模型（质量作用定律），参数化自文献（SUMO-SIM 亲和力 ~μM 级）；预测不同 SUMO 化水平下的 TF 分配
   - **验证方式**：FLIM-FRET 测量活细胞中 TF-SUMO 互作；与模型预测对比
   - **创新状态**：unverified

3. **候选名称**：基于 AlphaFold 3 的 TF-DNA 复合物异构体特异性预测
   - **来源局限/观察**：本文用 AF3 预测 Sp100 异构体结构，但未做 DNA 复合物预测；AF3 已支持蛋白-核酸复合物建模
   - **核心假设**：AF3 可区分 TF 异构体与不同 DNA 基序的结合偏好
   - **初步方法**：对同一 TF 的多个异构体，用 AF3 预测其与已知/候选 DNA 基序的复合物结构，比较界面残基与结合能（经 AF3 置信度或 MM-PBSA 打分）
   - **验证方式**：EMSA 或 HT-SELEX 实验验证预测的异构体-基序配对
   - **创新状态**：partially checked（AF3 的 DNA 结合预测已有初步验证，但异构体比较未见报道）

4. **候选名称**：IDR 介导的 TF 凝聚体形成与 DNA 结合协同性
   - **来源局限/观察**：本文强调 IDR 在 Sp100 功能中的潜在作用；PML-NBs 依赖相分离
   - **核心假设**：TF 的 IDR 通过相分离形成局部高浓度凝聚体，增强其对低亲和力基序的结合
   - **初步方法**：用 AF3 预测 IDR 的瞬态结构 + 粗粒化 MD（如 MARTINI）模拟 TF-IDR 的相分离行为；测量凝聚体中的 TF 浓度
   - **验证方式**：体外液-液相分离实验 + 单分子 DNA 结合实验（凝聚体 vs 稀相）
   - **创新状态**：unverified

5. **候选名称**：Sp100A 介导的 HIRA 招募在 HPV 感染中的表观遗传记忆
   - **来源局限/观察**：本文使用角质形成细胞（HPV 宿主细胞），但未涉及病毒感染；讨论中提及 Sp100 的抗病毒功能
   - **核心假设**：HPV 感染通过干扰 Sp100A-HIRA 互作，抑制 ISGs 的表观遗传记忆建立
   - **初步方法**：HPV 阳性/阴性角质形成细胞中比较 Sp100A-HIRA 共定位与 H3.3 沉积（CUT&Tag）
   - **验证方式**：HPV 敲低/回补实验 + 二次 IFN 刺激检测记忆应答
   - **创新状态**：unverified