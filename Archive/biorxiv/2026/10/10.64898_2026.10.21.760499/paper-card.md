## 01 基本信息

- **标题**：Structures of MyD88 and its oncogenic mutant reveal DNA binding with implications for cytosolic DNA sensing
- **作者与单位**：Pietro Fontana; Ahmet B. Tufan; Patrick Günther; Elena Goldberg; Sebastian Dörfler; Setu M. Vora; Leo Schirokauer; Joao A. Paulo; Hyung Suk Oh; Steven P. Gygi; David M. Knipe; Hao Wu（哈佛医学院/波士顿儿童医院等，具体单位未在摘要中逐一列出）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2026-10-29
- **论文类型**：结构生物学 + 功能验证（cryo-EM 结构 + 生化/细胞/转录组学）
- **领域**：先天免疫信号转导；MyD88 适配器蛋白；TIR 结构域；胞质 DNA 感知
- **关键词**：MyD88, TIR domain, cryo-EM, dsDNA binding, L252P/L265P oncogenic mutant, innate immunity, cGAS, TLR signaling
- **DOI/arXiv 号**：10.64898/2026.10.21.760499
- **代码**：未提供
- **数据**：cryo-EM 图谱（EMDB，登录号未在摘要中给出）；原子坐标（PDB，登录号未在摘要中给出）；RNA-seq 数据（补充表 S2、S3）
- **阅读日期**：未提供
- **在该方向中的位置**：本文聚焦于 **MyD88 TIR 结构域与 dsDNA 的直接结合**，属于「蛋白质–核酸互作」范畴，但**对象不是转录因子（TF）**，而是先天免疫适配器蛋白。对 TF–DNA 结合机制课题的可迁移点在于：(1) TIR 结构域通过**正电荷残基（K261/K262）结合 DNA 磷酸骨架**的机制，与 TF 识别 DNA 的静电互补原则相通；(2) cryo-EM 解析**丝状/环状蛋白–DNA 复合物**的方法学可迁移至 TF–DNA 复合物结构研究；(3) 突变体（L252P）通过**构象变化改变组装模式**的思路，可类比 TF 突变如何改变 DNA 结合特异性或亲和力。

---

## 02 一句话总结

本文通过 cryo-EM 解析了人 MyD88 TIR 结构域野生型环状和癌相关突变体 L252P 螺旋状双丝组装体的高分辨率结构，发现两者均通过 TIR 结构域内侧正电荷残基 K261/K262 结合 dsDNA 磷酸骨架，并利用生化、细胞和 RNA-seq 实验证明 MyD88 直接结合胞质 dsDNA、与 cGAS 协同促进先天免疫炎症转录程序，且该 DNA 结合功能独立于 TLR/IL-1R 信号通路。

---

## 03 研究问题

- **具体问题**：MyD88 的 TIR 结构域除了作为 TLR/IL-1R 信号通路的适配器平台之外，是否具有独立于受体信号的全新功能（如直接感知胞质 DNA）？其癌相关突变 L252P 如何改变 TIR 结构域的组装和功能？
- **为什么重要**：MyD88 是先天免疫中最重要的适配器蛋白之一，其功能获得性突变（L252P/L265P）在多种 B 细胞淋巴瘤中高频出现，但突变如何导致自激活的分子机制长期不明。若 MyD88 直接结合 DNA，则意味着存在一条全新的、不依赖 TLR 的 DNA 感知通路，对感染免疫、自身炎症和肿瘤免疫均有重要意义。
- **现有方法为何不足**：此前仅有 MyD88 TIR 的单体 NMR 结构和晶体堆积中的线性丝状结构，缺乏生理相关的高阶组装结构；L252P 突变体的结构完全未知；MyD88 是否直接结合核酸从未被系统检验。
- **精确的「Can ... ?」研究问题**：Can MyD88 TIR directly bind cytosolic dsDNA via a structurally defined positively charged surface, and does this DNA-binding activity contribute to dsDNA-induced inflammatory gene expression independently of TLR signaling?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及引用，标注为「经外部核验」的部分仅指文中明确引用的已发表工作；其余为本文框架。

1. **TLR/IL-1R 信号通路中的 MyD88 适配器功能（经典框架）**：MyD88 通过 DD 招募 IRAK 家族激酶形成 Myddosome（DD–DD 相互作用，6:4:4 化学计量），通过 TIR–TIR 相互作用与受体及 TIRAP/TRAM 等桥接蛋白结合，最终激活 NF-κB 和 MAPK 通路。代表方法：Myddosome 晶体结构（Lin et al., 2010 等）。局限：仅解释受体近端信号，未涉及核酸直接结合。
2. **TIR 结构域的高阶组装研究**：多种 TIR 结构域（包括 MyD88、Mal、SARM1、植物 TIR 等）在晶体堆积中形成丝状或环状组装，提示 TIR 结构域具有内在的寡聚化倾向。代表方法：X 射线晶体学、MicroED。局限：晶体堆积可能不代表溶液中的生理组装；缺乏与配体（如核酸）共结构的证据。
3. **TIR 结构域作为核酸结合模块的萌芽**：植物 TIR 结构域（如 EDS1 复合物）被证明具有 NADase 活性并参与免疫信号；细菌 TIR 结构域（如 AbTir、SPARTA）可结合核酸或具有酶活。本文作者据此推测哺乳动物 TIR 也可能具有核酸结合能力。局限：哺乳动物 TIR 的核酸结合缺乏直接结构证据。
4. **本文位置**：首次报道哺乳动物 TIR（MyD88）与 dsDNA 的复合物结构，提出 TIR 结构域的双丝环/螺旋组装是 DNA 结合的结构基础，并将该功能与胞质 DNA 感知和淋巴瘤突变联系起来。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| MyD88 TIR 的生理组装形式不明 | 此前仅有单体 NMR 结构和晶体堆积中的线性丝状结构，无法解释信号激活中的寡聚化机制 | 缺乏溶液中的高分辨率结构；晶体堆积可能不代表生理状态 | 引言部分引用 NMR（PDB 2Z5V/2JS7）和晶体/MicroED 结构（PDB 4DOM/4EO7/7BEQ/7L6W） |
| L252P 癌突变的结构后果未知 | 突变导致自激活和淋巴瘤，但机制不清 | 缺乏突变体结构；仅知突变位于 TIR 结构域核心 β-折叠 | 引言部分；本文首次解析 L252P 结构 |
| MyD88 是否直接结合核酸从未被检验 | 经典模型将 MyD88 定位为受体近端适配器，不涉及核酸感知 | 研究范式集中于 TLR/IL-1R 信号；TIR 结构域核酸结合在哺乳动物中无先例 | 引言部分；本文结构中发现 DNA 密度 |
| 胞质 DNA 感知通路中 MyD88 的角色被忽视 | cGAS-STING 被认为是胞质 DNA 感知的主通路，MyD88 未被纳入该框架 | cGAS 发现后研究集中于 STING 通路；MyD88 的核酸结合活性未被探索 | 本文 RNA-seq 显示约半数 cGAS 依赖基因也依赖 MyD88（Results 图 5） |
| 正电荷残基 K261/K262 的功能未知 | 该残基对在 TIR 结构域中保守但无已知功能 | 此前结构未显示该区域参与互作 | 本文结构显示 K261/K262 直接接触 DNA 磷酸骨架（Results 图 1G–I）；K2E 突变消除 DNA 结合（Results 图 2F） |

---

## 06 核心思想

### 1) 表面方法
- 表达纯化人 MyD88 TIR 结构域（残基 155–296），利用凝胶过滤层析发现 void volume 中的高分子量组分，通过负染 EM 确认环状/丝状组装。
- 用 cryo-EM 分别解析 WT（环状双丝，3.6 Å）和 L252P（螺旋状双丝，3.4 Å）的高分辨率结构。
- 通过 EMSA、荧光尺寸排阻色谱（FSEC）验证 MyD88 与 dsDNA 的直接结合，并通过 K2E 突变体验证结合位点。
- 在 iBMDM 和原代 BMDM 中进行 dsDNA 转染、HSV-1 感染实验，结合 RNA-seq 分析 MyD88 对 DNA 诱导基因表达的贡献。

### 2) 核心洞察
- **TIR 结构域的双丝反向平行组装**在 WT 和 L252P 中保守，但 WT 形成闭合环状，L252P 因 CD 环构象变化（~6.4 Å 位移、K250/R251 侧链翻转）而无法闭合，形成开放螺旋。
- **DNA 结合位点位于双丝内侧凹面**，由每个亚基的 K261/K262 正电荷残基形成连续的「正电荷轨道」，与 DNA 磷酸骨架互补。
- **DNA 结合与 TIR 寡聚化耦合**：双丝组装为 DNA 结合提供了多价平台，32 个赖氨酸残基协同结合约 60 bp dsDNA。
- **功能分离**：K2E 突变体保留 TLR 信号能力但丧失 DNA 结合和 DNA 诱导的炎症反应，证明 DNA 结合是独立于 TLR 适配器功能的新活性。

### 3) 可能的普适教训 [Analysis]
- **正电荷残基簇是蛋白质结合核酸磷酸骨架的通用「锚点」**：TF 的 DNA 结合结构域（如锌指、bZIP、HTH）同样依赖精氨酸/赖氨酸与磷酸骨架的静电互作。本文 K261/K262 的「双赖氨酸钳」模式可类比 TF 中的「arginine fork」或「lysine patch」。
- **寡聚化状态决定核酸结合亲和力与特异性**：单体 TF 结合 DNA 的亲和力通常较低，寡聚化（如同源二聚体 bZIP、异源二聚体 bHLH）可大幅提高亲和力和序列特异性。MyD88 的 16 亚基环/螺旋组装提供了超多价 DNA 结合表面，提示「组装增强结合」是核酸结合蛋白的普遍策略。
- **致病突变可通过改变组装几何而非直接破坏活性位点来改变功能**：L252P 并未直接接触 DNA，而是通过改变 CD 环构象将闭合环变为开放螺旋。这提示在研究 TF 致病突变时，应关注突变对寡聚化状态和组装拓扑的影响，而非仅关注 DNA 接触残基。

---

## 07 方法总览

- **输入**：人 MyD88 TIR 结构域（155–296）重组蛋白（WT 和 L252P 突变体）；不同长度的 dsDNA（30–75 bp 及 2 kb、7 kb）；iBMDM 细胞系（WT、MyD88 KO、cGAS KO、双 KO）；原代 BMDM（WT 和 MyD88 KO 小鼠）；HSV-1 病毒（WT 和 ΔICP0 株）。
- **输出**：cryo-EM 原子模型（WT 环状 16 亚基双丝、L252P 螺旋双丝）；DNA 结合亲和力/特异性数据；细胞信号通路激活数据；全基因组转录组数据。
- **模块**：
  1. 蛋白表达与纯化（细菌表达，Ni-NTA + SEC）
  2. 负染 EM 筛选与 cryo-EM 数据采集（WT：7,946 张图像；L252P：32,194 张图像）
  3. 单颗粒分析（cryoSPARC：Patch Motion、PatchCTF、2D/3D 分类、非均匀细化、局部细化）
  4. 模型构建与精修（ChimeraX 刚性拟合、iSOLDE、Phenix 迭代精修）
  5. 生化验证（EMSA、FSEC、K2E 突变体）
  6. 细胞实验（dsDNA 转染、HSV-1 感染、qRT-PCR、ELISA）
  7. 转录组学（RNA-seq + DESeq2 差异表达分析）
- **训练**：不适用（无深度学习模型）。
- **工具**：cryoSPARC v4.5.3、ChimeraX、iSOLDE、Phenix、MolProbity、DESeq2、R。
- **反馈回路**：结构 → 突变设计（K2E、CD 环突变）→ 功能验证 → 回到结构解释。
- **假设**：凝胶过滤 void volume 中的蛋白组装代表生理相关状态；cryo-EM 结构中的额外密度为 dsDNA；K2E 突变不影响 TIR 结构域整体折叠。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| **cryo-EM 结构解析（WT 环状双丝）** | 确定 WT MyD88 TIR 的高阶组装结构 | 此前无生理相关组装结构 | 输入：纯化蛋白；输出：3.6 Å 环状 16 亚基双丝模型 | Results 图 1A–D；Table S1 | 无法得知 DNA 结合的结构基础 |
| **cryo-EM 结构解析（L252P 螺旋双丝）** | 确定癌突变体的组装结构 | 突变体结构完全未知 | 输入：L252P 突变蛋白；输出：3.4 Å 螺旋双丝模型 | Results 图 6A–C；Table S1 | 无法解释突变如何导致自激活 |
| **DNA 密度识别与建模** | 鉴定并建模结合在 TIR 双丝凹面的 dsDNA | 结构中的额外密度来源不明 | 输入：cryo-EM 图谱；输出：60 bp dsDNA 模型 | Results 图 1F–I；图 6B | 无法确定 DNA 结合位点和结合模式 |
| **K2E 突变体设计** | 验证 K261/K262 是否为 DNA 结合关键残基 | 需要因果证据证明 DNA 结合位点 | 输入：K261E/K262E 突变；输出：丧失 DNA 结合的蛋白 | Results 图 2F；图 4B–E | 无法将 DNA 结合与功能表型因果关联 |
| **EMSA** | 定量检测 MyD88 与不同长度 dsDNA 的结合 | 验证体外直接结合 | 输入：蛋白 + Cy3-dsDNA；输出：结合位移/亲和力 | Results 图 2A–E | 无法证明直接物理互作 |
| **FSEC** | 在溶液状态下验证 MyD88–DNA 复合物形成 | 排除凝胶迁移假象 | 输入：蛋白 + Cy3-dsDNA；输出：复合物洗脱峰 | Results 图 2G | 无法排除 EMSA 中的非特异结合 |
| **细胞转染/感染实验** | 验证 DNA 诱导的 MyD88 依赖性炎症反应 | 需要生理相关性证据 | 输入：dsDNA 转染或 HSV-1 感染；输出：细胞因子表达 | Results 图 3A–E, I–K | 无法将体外 DNA 结合与细胞功能联系 |
| **RNA-seq** | 全基因组评估 MyD88 对 DNA 诱导转录的贡献 | 需要 unbiased 的转录组证据 | 输入：WT/KO 细胞 ± DNA 刺激；输出：差异表达基因列表 | Results 图 5；Table S2, S3 | 无法评估 MyD88 在 DNA 感应中的全局作用 |
| **STED 显微镜** | 观察 DNA 诱导的 MyD88 puncta 形成 | 需要亚细胞定位证据 | 输入：GFP-MyD88 细胞 + dsDNA；输出：puncta 图像 | Results 图 4A；图 S8A | 无法确认 MyD88–DNA 共定位 |

---

## 09 关键公式符号

本文为结构生物学 + 功能验证论文，**无数学公式**。以下列出与数据分析和结构验证相关的关键参数：

- **分辨率评估**：Gold-standard FSC（Fourier shell correlation）0.143 截断标准；WT 3.6 Å，L252P 3.4 Å。
- **EM 数据统计**：WT 7,946 张图像 → 3,792,682 颗粒 → 2D 分类 → 391,591 颗粒 → 3D 分类/细化 → 132,657 颗粒 → 最终 90,711 颗粒；L252P 32,194 张图像 → 6,949,592 颗粒 → 230,088 颗粒 → 78,342 颗粒。
- **模型验证**：Molprobity 评分、EM Ringer 评分（数值未在摘要中给出）。
- **结构比对**：Cα RMSD（WT vs L252P：0.703 Å over 129 Cα；WT vs MicroED 结构：0.8 Å over 129 Cα）。
- **结合亲和力**：EMSA 中未给出具体 Kd 值（摘要未提供）。
- **RNA-seq 分析**：DESeq2 差异表达分析，padj < 0.05（具体阈值未在摘要中给出）。

---

## 10 实验设计与证据链

### 数据集/群体/规模/指标/基线/预算/仪器/评测协议

| 项目 | 详情 |
|------|------|
| 蛋白样本 | 人 MyD88 TIR（155–296）WT 和 L252P，细菌表达 |
| cryo-EM 仪器 | Titan Krios（300 keV）+ K3 探测器（WT）；Titan Krios + Falcon 4i（L252P） |
| 细胞系 | iBMDM（WT、MyD88 KO、cGAS KO、cGAS/MyD88 双 KO）；原代 BMDM（WT、MyD88 KO） |
| 刺激物 | HSV-1 dsDNA 片段（30–90 bp、2 kb、7 kb）；poly dA:dT；HSV-1 病毒（WT 和 ΔICP0 株） |
| 功能指标 | Tnf、Il1b、Il6、Ifnb1、Cxcl10 mRNA 水平（qRT-PCR）；TNFα、IFN-β 分泌（ELISA）；IKKα/IKKβ 磷酸化（Western blot） |
| 转录组 | bulk RNA-seq（iBMDM，WT vs KO，±dsDNA 刺激），DESeq2 分析 |
| 结构验证 | EMSA（Cy3 标记 dsDNA）、FSEC、负染 EM、STED 显微镜 |
| 基线/对照 | 未转染/未感染对照；K2E 突变体作为 DNA 结合缺陷对照；cGAS KO 作为已知 DNA 感应通路对照 |

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| cryo-EM 结构解析（WT） | MyD88 TIR 形成环状双丝组装 | 无直接对照；与已知单体结构比较 | 3.6 Å 环状 16 亚基双丝结构 | MyD88 TIR 可形成高阶环状组装 | 该组装是否在细胞内天然存在 | Results 图 1A–D |
| cryo-EM 结构解析（L252P） | 癌突变改变组装拓扑 | WT vs L252P | 3.4 Å 螺旋双丝；CD 环位移 6.4 Å | L252P 通过 CD 环构象变化驱动螺旋组装 | 螺旋组装是否直接导致信号激活 | Results 图 6A–F |
| 结构中的 DNA 密度 | MyD88 TIR 结合 dsDNA | 无 DNA 对照 vs 有 DNA | 凹面正电荷轨道结合 60 bp dsDNA | MyD88 TIR 直接结合 dsDNA | DNA 序列是否具有选择性 | Results 图 1F–I |
| EMSA（WT vs K2E） | K261/K262 是 DNA 结合关键残基 | WT vs K2E；不同 DNA 长度 | K2E 完全丧失 DNA 结合 | DNA 结合由 K261/K262 介导 | 其他残基是否也参与 | Results 图 2F |
| FSEC | 溶液状态下 MyD88–DNA 复合物形成 | 蛋白 ± DNA | 复合物峰提前洗脱 | 溶液状态下确实形成复合物 | 复合物的化学计量比 | Results 图 2G |
| dsDNA 转染 iBMDM（WT vs MyD88 KO） | MyD88 介导 DNA 诱导的炎症基因表达 | WT vs KO；±dsDNA | Tnf、Il1b 在 KO 中显著降低 | MyD88 是 DNA 诱导炎症反应所必需 | MyD88 是否直接感应 DNA（vs 间接） | Results 图 3A–E |
| HSV-1 感染原代 BMDM（WT vs MyD88 KO） | 病毒感染中 MyD88 的贡献 | WT vs KO；不同病毒株 | TNFα 依赖 MyD88，IFN-β 不依赖 | MyD88 特异性调控炎症而非干扰素通路 | 病毒 DNA 是否为唯一刺激 | Results 图 3I–K |
| Unc93b1 KO 实验 | DNA 感应不依赖内体 TLR | WT vs Unc93b1 KO | 无差异 | 排除 TLR3/7/8/9 介导 | 其他 TLR 是否参与 | Results 图 3L–M |
| RNA-seq（WT vs MyD88 KO，±dsDNA） | MyD88 调控的全局转录程序 | 4 组比较 | 约半数 cGAS 依赖基因也依赖 MyD88 | MyD88 与 cGAS 协同调控转录 | MyD88 是否独立于 cGAS 发挥作用 | Results 图 5A–F |
| K2E 回补实验 | DNA 结合是 MyD88 功能所必需 | WT vs K2E 回补 | K2E 无法回补 DNA 诱导的基因表达 | DNA 结合是 MyD88 功能所必需 | DNA 结合是否足以驱动激活 | Results 图 4B–C |
| STED 显微镜 | DNA 诱导 MyD88 puncta 形成 | ±dsDNA | 形成 puncta 且与 DNA 共定位 | MyD88 在细胞内与 DNA 共聚集 | puncta 是否为信号激活所必需 | Results 图 4A；图 S8A |

---

## 11 结论正确解读

- **任务范围**：本文仅研究了 MyD88 TIR 结构域（155–296）的体外组装和 DNA 结合，以及 iBMDM/BMDM 中 DNA 转染/HSV-1 感染后的细胞反应。**未涉及**全长 MyD88 在完整动物体内的功能、其他细胞类型中的行为、DNA 序列特异性的系统筛选。
- **oracle/真值输入**：cryo-EM 结构中的 DNA 密度通过拟合 60 bp B-form dsDNA 模型验证；K2E 突变体的功能缺陷作为 DNA 结合必要性的因果证据。这些是「oracle」性质的验证手段。
- **端到端状态**：**非端到端**。结构解析、体外结合、细胞功能、转录组是分步验证的，各环节独立但相互支持。
- **算力成本**：cryo-EM 数据采集和处理需要高性能计算资源，但本文未报告具体算力消耗。
- **历史数据依赖**：依赖此前发表的 MyD88 单体 NMR 结构（PDB 2Z5V/2JS7）和 MicroED 丝状结构（PDB 7BEQ/7L6W）作为参照。
- **模型依赖**：结构解析依赖 cryoSPARC 软件和标准单颗粒分析流程；DNA 模型为理想 B-form 螺旋，未考虑序列依赖性构象变化。
- **最难情形**：L252P 螺旋结构的局部细化仅达到 3.4 Å，CD 环区域的构象变化可能受分辨率限制；DNA 密度在 3D 分类中表现出异质性，提示 DNA 结合可能具有动态性。
- **群体/领域边界**：结论局限于**先天免疫中的 MyD88 功能**，不能直接推广到其他 TIR 结构域蛋白（如 SARM1、TLR 自身）或其他核酸感应通路。
- **不确定性**：MyD88 在胞质中结合 DNA 的生理触发条件（何种 DNA、何种细胞状态）尚不明确；MyD88 与 cGAS 协同的分子机制（直接互作 vs 平行通路汇聚）未完全阐明；L252P 的自激活是否完全由 DNA 结合介导未直接证明。

**有边界的复述**：在 iBMDM 和原代 BMDM 中，MyD88 通过其 TIR 结构域内侧 K261/K262 残基直接结合胞质 dsDNA，该结合对 dsDNA 诱导的炎症基因表达（特别是 NF-κB 靶基因）是必需的，且不依赖内体 TLR 或 cGAS 的活性；L252P 突变通过改变 CD 环构象将 TIR 组装从闭合环变为开放螺旋，可能增强 DNA 结合和自激活。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| DNA 结合序列特异性未系统研究 | 仅测试了 HSV-1 来源的 dsDNA 片段，未进行随机序列筛选 | 未明确提及 | Discussion 节（推测性讨论 DNA 长度依赖性） |
| 全长 MyD88 的结构缺失 | 仅解析了 TIR 结构域（155–296），不含 DD 和 linker | 未明确提及 | 摘要及 Results 节 |
| L252P 自激活与 DNA 结合的因果关系未完全证明 | K2E 突变体在 TLR 信号中功能正常，但未直接证明 L252P 的自激活完全由 DNA 结合驱动 | 未明确提及 | Discussion 节 |
| 体内生理相关性未验证 | 未进行小鼠体内实验验证 MyD88-DNA 感应功能 | 未明确提及 | 摘要及 Discussion 节 |
| DNA 结合是否具有长度/结构选择性 | 观察到 DNA 长度影响结合，但未系统定量 | 未明确提及 | Results 图 2A–E 相关讨论 |
| cryo-EM 分辨率限制 | WT 环 3.6 Å、L252P 螺旋 3.4 Å，CD 环区域构象变化细节可能不完整 | 未明确提及 | Results 图 6D–F |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 体外组装的生理相关性 | 凝胶过滤 void volume 中的环/螺旋结构可能是在高浓度蛋白纯化过程中形成的非生理聚集 | 若组装非生理，则 DNA 结合模型不成立 | 在细胞内用交联质谱（cross-linking MS）或荧光相关光谱（FCS）检测内源 MyD88 的组装状态 | Methods 节纯化流程；Results 图 S1C–E |
| K2E 突变体功能解读 | K2E 可能通过改变 TIR 结构域整体稳定性而非仅消除 DNA 结合来影响功能 | 需要排除突变导致的全局构象变化 | 对 K2E 突变体做圆二色谱（CD）或热稳定性分析（DSF），确认其折叠状态与 WT 一致 | Results 图 2F；图 4B–C |
| DNA 共纯化的偶然性 | 大肠杆菌表达系统中可能共纯化宿主 DNA 片段，结构中的 DNA 密度可能不代表生理配体 | 若为纯化假象，则 MyD88-DNA 互作的生理意义存疑 | 用核酸酶处理纯化样本后重复结构解析；用表面等离子共振（SPR）或微量热泳动（MST）测定溶液中的结合亲和力 | Results 图 S1C（A260/A280 比值） |
| RNA-seq 中 MyD88 与 cGAS 的「协同」 | 双 KO 实验未展示，无法区分 MyD88 和 cGAS 是平行通路还是同一通路的不同节点 | 影响对通路架构的理解 | 在 cGAS KO 背景中回补 MyD88 并检测 DNA 诱导基因表达；进行双 KO 回补实验 | Results 图 5A–F |
| L252P 螺旋的「自激活」解释 | 螺旋开放可能只是突变导致的蛋白不稳定表现，而非功能性构象 | 若螺旋与激活无关，则癌突变机制解释不成立 | 在细胞中表达不能形成螺旋但保留 DNA 结合的 L252P 变体，检测是否仍自激活 | Results 图 6A–F；图 6I |
| DNA 长度依赖性的解释 | 观察到 30–90 bp DNA 结合差异，但未系统改变 DNA 序列组成 | 无法排除 GC 含量或特定序列基序的影响 | 使用随机序列库进行 SELEX 或 HT-SELEX 筛选 | Results 图 2A–E |
| STED 显微镜中 puncta 的解读 | puncta 可能代表蛋白聚集而非功能性信号复合物 | 需要区分功能性 Myddosome 与非特异聚集 | 用超分辨显微镜结合荧光漂白恢复（FRAP）检测 puncta 的动态性 | Results 图 4A；图 S8A |

---

## 14 学到什么

> 以下为面向「蛋白质–DNA 互作（聚焦 TF–DNA 结合机制）× AI/深度学习或物理模拟」课题的可迁移知识。

### 概念层面
1. **正电荷残基簇作为 DNA 结合「锚点」的通用性**：MyD88 TIR 通过 K261/K262 双赖氨酸与 DNA 磷酸骨架互作，这与 TF 中精氨酸/赖氨酸富集区域（如 basic region of bZIP、zinc finger 的 arginine 残基）的静电识别机制高度一致。**可迁移**：在预测 TF–DNA 结合界面时，可将「连续正电荷表面」作为特征，而非仅依赖已知 DNA 结合 motif。
2. **寡聚化增强 DNA 结合亲和力**：MyD88 的 16 亚基组装提供了 32 个赖氨酸残基协同结合 DNA，实现高亲和力多价互作。**可迁移**：TF 的协同 DNA 结合（如 enhanceosome、TF 二聚体/四聚体）可类比为「多价结合平台」，在建模时应考虑 TF 寡聚状态对 DNA 结合亲和力和特异性的影响。
3. **突变通过改变组装拓扑而非直接破坏 DNA 接触残基来改变功能**：L252P 突变位于 CD 环，不直接接触 DNA，但通过构象变化将闭合环变为开放螺旋。**可迁移**：在分析 TF 致病突变时，应关注突变对 TF 二聚化/寡聚化界面的影响，而非仅关注 DNA 接触残基。

### 方法层面
4. **cryo-EM 解析丝状/环状蛋白–核酸复合物的策略**：本文采用「分段拾取」（segment picking）策略处理环状结构，类似于 NINJ1 寡聚体的处理方法。**可迁移**：对于 TF–DNA 纤维/凝聚体（如 TF 在 DNA 上形成的簇），cryo-EM 分段分析是可行路径。
5. **结构引导的突变设计验证功能**：K2E 突变体设计直接基于结构中的 DNA 接触残基，并在细胞水平验证功能丧失。**可迁移**：在 TF–DNA 结合机制研究中，结构引导的「电荷反转」突变（如 Lys→Glu）是验证 DNA 结合界面的高效策略。
6. **多层级证据链**：结构（cryo-EM）→ 体外生化（EMSA/FSEC）→ 细胞功能（KO/回补）→ 转录组（RNA-seq）的递进式验证。**可迁移**：TF–DNA 研究应避免仅依赖单一方法，尤其是结构预测（如 AlphaFold）结果需用生化实验交叉验证。

### 对 TF–DNA 课题的具体迁移建议
7. **AlphaFold3 用于 DNA 建模的参考**：本文用 AlphaFold3 生成 60 bp dsDNA 初始模型用于拟合 cryo-EM 密度。**可迁移**：在 TF–DNA 复合物结构预测中，AlphaFold3 可作为 DNA 构象初始模型生成工具，但需注意其预测的 DNA 构象可能偏离真实结合状态。
8. **正电荷表面计算作为 DNA 结合预测的快速筛选**：本文通过表面电荷分布分析识别 DNA 结合位点。**可迁移**：在缺乏结构的情况下，可用 Poisson-Boltzmann 或 APBS 计算 TF 表面静电势，快速预测潜在 DNA 结合面。
9. **突变体库 + 功能读出的筛选策略**：本文通过单个突变体（K2E）验证功能。**可迁移**：在 TF–DNA 研究中，可构建正电荷残基的系统突变库（如 Ala 扫描 + 电荷反转），结合高通量结合实验（如 MITOMI、HT-SELEX）系统性绘制 DNA 结合界面。

---

## 15 与已有知识连接

- **MyD88 经典信号通路**：MyD88 作为 TLR/IL-1R 适配器的功能已有大量综述和结构研究（如 Lin et al., 2010, Nature 的 Myddosome 结构；Nyman et al., 2008 的 TIR 结构域 NMR）。本文在此基础上提出 TIR 结构域的新功能（DNA 结合），与经典模型互补而非矛盾。
- **TIR 结构域核酸结合的先例**：植物 TIR 结构域（如 EDS1、RPS4）和细菌 TIR 结构域（如 AbTir、SPARTA）已被证明具有核酸结合或 NADase 活性。本文首次将这一范式扩展到哺乳动物 TIR 蛋白。
- **cGAS-STING 通路**：cGAS 是公认的胞质 DNA 传感器（Sun et al., 2013, Science）。本文提出 MyD88 作为 cGAS 的协同因子，与 cGAS 共同调控 DNA 诱导的炎症反应，但 MyD88 是否直接激活 STING 或独立于 STING 发挥作用仍需进一步验证。
- **L252P/L265P 突变与淋巴瘤**：L265P 是 Waldenström macroglobulinemia 中最常见的 MyD88 突变（Treon et al., 2012, NEJM），此前研究集中于其激活 NF-κB 的机制。本文首次提供该突变体的结构，揭示其通过改变组装拓扑导致自激活的机制。
- **与 TF–DNA 互作研究的连接**：本文的「多价正电荷表面结合 DNA 磷酸骨架」机制与 TF 的静电识别原则一致。可参考的 TF–DNA 经典文献包括：bZIP 家族碱性区与 DNA 的静电互作（Ellenberger et al., 1992, Cell）、锌指蛋白的磷酸骨架识别（Pavletich & Pabo, 1991, Science）。
- **结构预测工具**：本文使用 AlphaFold3 生成 DNA 模型，反映了 AlphaFold3 在蛋白–核酸复合物建模中的新应用。可连接至 AlphaFold3 原论文（Abramson et al., 2024, Nature）及后续在 TF–DNA 复合物预测中的评估工作。

---

## 16 研究想法

> 以下为面向「TF–DNA 结合机制 × AI/深度学习或物理模拟」课题的研究候选。

### 候选 1：基于正电荷表面特征的 TF–DNA 结合界面预测器
- **名称**：PosCharge-DNA Interface Predictor (PCDIP)
- **来源局限/观察**：MyD88 TIR 的 DNA 结合依赖连续正电荷表面（K261/K262），而非经典 DNA 结合 motif。现有 TF–DNA 预测工具（如 DeepBind、DeepSEA）主要基于序列 motif，对非经典 DNA 结合界面（如 TIR 结构域）预测能力有限。
- **核心假设**：TF 表面连续正电荷斑块（patch）是 DNA 结合的必要条件，可作为独立于序列 motif 的预测特征。
- **初步方法**：用 APBS 计算蛋白表面静电势，识别正电荷簇（>3 个 Lys/Arg 残基，间距 <8 Å）；结合 AlphaFold2/3 预测结构，训练一个轻量级分类器（如 gradient boosting）区分 DNA 结合蛋白与非结合蛋白；在 PDB 中已知 TF–DNA 复合物上验证。
- **验证方式**：在 MyD88 TIR、SARM1 TIR、植物 TIR 等非经典 DNA 结合蛋白上测试；与 DeepBind 等序列方法比较 AUC。
- **创新状态**：unverified

### 候选 2：TF 寡聚化状态对 DNA 结合亲和力的多尺度模拟
- **名称**：OligoBind: Multiscale Simulation of TF Oligomerization-Enhanced DNA Binding
- **来源局限/观察**：MyD88 的 16 亚基组装通过多价效应实现高亲和力 DNA 结合。现有 TF–DNA 模拟（如 MD、MM/PBSA）通常以单体 TF 为起点，忽略寡聚化对结合自由能的贡献。
- **核心假设**：TF 寡聚化通过增加 DNA 接触残基数量（多价效应）显著提高结合亲和力，且这种效应可通过自由能分解定量预测。
- **初步方法**：以 MyD88 TIR 环状组装为模型系统，用粗粒化 MD（如 Martini）模拟不同寡聚状态（单体、二聚体、环状 16 亚基）与 60 bp dsDNA 的结合；用 MM/PBSA 或伞形采样计算结合自由能；将多价效应参数化为「每亚基结合自由能 × 接触亚基数」的线性模型。
- **验证方式**：与本文 EMSA 数据（不同 DNA 长度的结合差异）对比；在已知寡聚化 TF（如 p53 四聚体、NF-κB 二聚体）上测试。
- **创新状态**：unverified

### 候选 3：突变诱导的 TF 组装拓扑变化对 DNA 结合影响的 AI 预测
- **名称**：MutTopo-DNA: Predicting Mutation-Induced Topological Transitions in TF Assemblies and Their DNA-Binding Consequences
- **来源局限/观察**：L252P 突变通过改变 CD 环构象将环状组装变为螺旋，且不影响 TLR 信号但影响 DNA 结合。现有突变效应预测工具（如 AlphaMissense、PolyPhen）主要评估蛋白稳定性，不预测组装拓扑变化。
- **核心假设**：特定残基突变可通过改变 loop 构象驱动 TF 组装拓扑转变（环→螺旋、开→闭），进而改变 DNA 结合能力；这种转变可通过结构能量学预测。
- **初步方法**：收集已知 TF 组装突变体（如 p53 寡聚化突变、MyD88 L252P），用 AlphaFold2-multimer 或 AlphaFold3 预测突变体的组装模式；计算组装界面的构象熵和接触能变化；训练一个图神经网络（GNN）预测突变是否导致拓扑转变。
- **验证方式**：在 MyD88 L252P 上回顾性验证（预测螺旋 vs 环）；前瞻性设计 3–5 个 MyD88 新突变体，用 EMSA 和负染 EM 验证。
- **创新状态**：unverified

### 候选 4：TF–DNA 复合物 cryo-EM 结构的自动建模管线
- **名称**：AutoFit-DNA: Automated Cryo-EM Modeling Pipeline for TF-DNA Complexes
- **来源局限/观察**：本文用 AlphaFold3 生成 DNA 初始模型后手动拟合到 cryo-EM 密度中，过程繁琐且依赖人工。现有自动建模工具（如 ModelAngelo）主要针对蛋白，对 DNA 支持有限。
- **核心假设**：结合 AlphaFold3 的 DNA 构象预测和 cryo-EM 密度图，可实现 TF–DNA 复合物的全自动建模。
- **初步方法**：开发一个管线：输入 cryo-EM 密度图 + TF 序列 + DNA 序列 → AlphaFold3 生成初始复合物模型 → 用 FlexEM 或 ISOLDE 柔性拟合到密度 → 用 Phenix 精修 → 输出 PDB 文件；在本文 WT 和 L252P 数据集上测试。
- **验证方式**：与手动建模结果对比 RMSD 和 MolProbity 分数；在公开的 TF–DNA cryo-EM 数据集（如 EMDB 中 p53-DNA、NF-κB-DNA 复合物）上泛化测试。
- **创新状态**：unverified

### 候选 5：TF 正电荷表面与 DNA 序列偏好的共进化分析
- **名称**：CoEvol-DNA: Co-evolutionary Analysis of TF Positive-Charge Surfaces and DNA Sequence Preferences
- **来源局限/观察**：MyD88 的 DNA 结合似乎不依赖特定序列（结合磷酸骨架），但 TF 通常有序列特异性。正电荷表面与序列特异性之间的关系尚不明确。
- **核心假设**：TF 的 DNA 结合可分为「磷酸骨架识别」（序列非特异，依赖正电荷表面）和「碱基识别」（序列特异，依赖氢键/疏水接触）两个正交维度；两者可通过共进化分析解耦。
- **初步方法**：收集 TF 家族序列和 DNA 结合位点数据（Cis-BP、JASPAR），计算 TF 表面正电荷残基的共进化网络；将正电荷表面特征与 DNA 结合位点序列偏好做关联分析；用机器学习（如随机森林）预测 TF 是「序列特异型」还是「骨架识别型」。
- **验证方式**：在 MyD88（预测为骨架识别型）和已知序列特异 TF（如 p53、GCN4）上测试；用 SELEX 数据验证预测。
- **创新状态**：unverified