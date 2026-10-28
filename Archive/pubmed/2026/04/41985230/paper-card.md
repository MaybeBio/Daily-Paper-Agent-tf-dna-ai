## 01 基本信息

- **标题**：Polyphyllin VI induces Forkhead box O3 nuclear liquid-liquid phase separation to promote mitophagy in breast cancer
- **作者**：Zhan, Xiangrong; Zhong, Yifan; Liu, Xuewen; Peng, Wenkang; Zhang, Xu; Xiang, Ke; Yu, Qingqing; Chai, Yanting; Chen, Yingli; Liu, Ying; Si, Yuan
- **单位**：未提供
- **期刊/平台**：Phytomedicine: International Journal of Phytotherapy and Phytopharmacology
- **年份**：2026（在线日期 2026-04-16）
- **论文类型**：实验研究（体外 + 体内）
- **领域**：肿瘤药理学；蛋白质相分离；线粒体自噬；转录因子调控
- **关键词**：Polyphyllin VI; FOXO3; liquid-liquid phase separation; mitophagy; breast cancer; BNIP3/NIX
- **DOI/arXiv 号**：10.1016/j.phymed.2026.158166
- **代码**：未提供
- **数据**：RNA-seq 数据（未提供 accession）；分子动力学模拟参数未提供
- **阅读日期**：2026-05-12
- **在课题方向中的位置**：本文属于「小分子药物直接结合转录因子（TF）并调控其相分离行为」的典型案例。对「TF–DNA 互作 × AI/物理模拟」课题的启示在于：(1) FOXO3 的 LLPS 由其内在无序区（IDR，C2 区 151–673 aa）驱动，这为预测 TF 相分离倾向提供了序列特征线索；(2) 小分子直接结合 TF 并增强其核内 LLPS，提示 TF 的相分离状态可作为药物调控的新维度；(3) 分子动力学（MD）模拟被用于验证小分子–TF 结合对构象/相分离的影响，是物理模拟与实验结合的可迁移范式。

---

## 02 一句话总结

本文发现 Polyphyllin VI（PPVI）直接结合转录因子 FOXO3，增强其核内液-液相分离（LLPS，主要由 C2 区 151–673 aa 驱动），从而促进 BNIP3/NIX 介导的线粒体自噬，在乳腺癌模型中发挥抗肿瘤作用，但伴随心脏毒性和极低口服生物利用度。

---

## 03 研究问题

- **具体问题**：PPVI 在乳腺癌中通过何种分子机制发挥抗肿瘤作用？特别是，PPVI 是否通过直接结合 FOXO3 并调控其相分离行为来促进线粒体自噬？
- **为什么重要**：线粒体功能障碍和缺陷性线粒体自噬与癌症进展密切相关；FOXO3 是调控自噬相关基因的关键转录因子。阐明小分子如何通过调控 TF 的相分离来影响下游转录程序，可为癌症治疗提供新靶点和新策略。
- **现有方法为何不足**：此前对 PPVI 的抗肿瘤机制研究多停留在凋亡、周期阻滞等层面，未深入探讨其与 TF 的直接物理互作及相分离调控；对 FOXO3 的研究多聚焦其磷酸化/乙酰化修饰和核转位，未涉及其 LLPS 行为在自噬调控中的作用。
- **精确的「Can ... ?」问题**：Can PPVI directly bind FOXO3 and enhance its nuclear liquid-liquid phase separation to drive BNIP3/NIX-mediated mitophagy in breast cancer?

---

## 04 背景与发展脉络

> 注：以下脉络为「仅本文框架」——基于本文引言与讨论的叙述整理，未经外部系统核验。

1. **阶段一：线粒体自噬与癌症**——线粒体自噬（mitophagy）作为选择性自噬，清除受损线粒体；其失调与肿瘤发生发展相关。代表机制：PINK1/Parkin 通路、BNIP3/NIX 受体通路。局限：对上游转录调控因子的研究不足。
2. **阶段二：FOXO3 作为自噬转录因子**——FOXO3 激活自噬相关基因（如 BNIP3、LC3、ATG 家族）的转录。调控方式以翻译后修饰（磷酸化、乙酰化）和核质穿梭为主。局限：未考虑 FOXO3 的相分离行为对其转录活性的影响。
3. **阶段三：TF 的液-液相分离（LLPS）**——近年发现多种 TF 通过其 IDR 发生 LLPS，形成转录凝聚体（transcriptional condensates），增强局部转录效率。局限：对药物小分子直接调控 TF LLPS 的研究极少。
4. **阶段四（本文位置）**：首次报道天然小分子 PPVI 直接结合 FOXO3，增强其核内 LLPS，从而促进 BNIP3/NIX 介导的线粒体自噬。将「小分子–TF 直接互作」「TF 相分离」「线粒体自噬」三者串联，提出 FOXO3 相分离作为药物调控新靶点。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 线粒体自噬调控机制不明确 | 对 PPVI 诱导的线粒体自噬的上游调控因子不清楚 | 作者认为 FOXO3 是 PPVI 诱导自噬的关键转录因子，但此前未被识别 | Results（FOXO3 敲除后 PPVI 诱导的 mitophagy 显著减弱） |
| TF 相分离在药物作用中的角色被忽视 | 小分子药物是否通过调控 TF LLPS 发挥疗效，此前无报道 | 作者认为 FOXO3 的 LLPS 是其转录激活的新机制，PPVI 通过增强 LLPS 来放大转录输出 | Results（PPVI 增强 FOXO3 核内 puncta 形成，FRAP 恢复时间变化） |
| PPVI 的直接靶点不明 | 此前研究未鉴定 PPVI 的直接结合蛋白 | 作者通过 biotin-PPVI 亲和纯化 + 质谱鉴定 FOXO3 为直接靶点 | Methods（biotin-labeled PPVI pull-down + MS）；Results（MST 验证结合） |
| 药物递送与毒性问题 | PPVI 口服生物利用度极低，且表现心脏毒性 | 作者归因于 PPVI 的理化性质（皂苷类）和体内分布（肝脏富集、半衰期短） | Results（药代动力学与组织分布实验） |

---

## 06 核心思想

### 1) 表面方法
- 用 biotin 标记的 PPVI 进行 pull-down + 质谱鉴定直接结合蛋白 → 锁定 FOXO3。
- 用 MST 验证 PPVI–FOXO3 直接结合。
- 用 mKeima-Red-Mito-7 报告线粒体自噬流。
- 用活细胞成像、FRAP、截短突变体、MD 模拟研究 FOXO3 LLPS 及 PPVI 的调控作用。
- 用 zebrafish 和 xenograft 小鼠模型评估体内抗肿瘤效果与毒性。

### 2) 核心洞察
- **FOXO3 的 LLPS 由其 C2 区（151–673 aa）驱动**，该区域富含内在无序特征，是相分离的结构基础。
- **PPVI 直接结合 FOXO3 并增强其核内 LLPS**，而非仅仅促进核转位或改变其转录活性——即药物通过调控 TF 的物理状态（相分离）来放大其转录功能。
- **FOXO3 相分离 → 转录激活 BNIP3/NIX → 线粒体自噬**，构成一条「小分子–TF 相分离–细胞器自噬」的完整信号链。

### 3) 可能的普适教训 [Analysis]
- 小分子药物可以直接靶向 TF 的 IDR/相分离行为，而不必靶向其 DNA 结合域（DBD）或配体结合域——这为「不可成药」转录因子提供了新思路。
- TF 的相分离能力可能与其转录输出强度正相关，提示在预测 TF 活性时，应同时考虑其序列中的 IDR 特征和相分离倾向。
- MD 模拟可用于验证小分子与 TF IDR 的互作模式，为「药物–相分离」研究提供原子级解释。

---

## 07 方法总览

- **输入**：乳腺癌细胞系（具体名称未提供）、PPVI 化合物、biotin-PPVI 探针、FOXO3 截短突变体、mKeima-Red-Mito-7 质粒、zebrafish 与 xenograft 小鼠模型。
- **输出**：PPVI 抗乳腺癌效果、FOXO3 结合与相分离调控机制、线粒体自噬水平、体内药效与毒性数据。
- **模块**：
  1. 转录组学（RNA-seq）→ 差异基因与通路富集；
  2. 蛋白互作鉴定（biotin pull-down + MS + MST）；
  3. 线粒体自噬检测（mKeima-Red-Mito-7、qPCR、Western blot）；
  4. LLPS 表征（活细胞成像、FRAP、截短突变体）；
  5. 分子动力学模拟（PPVI–FOXO3 互作）；
  6. 体内实验（zebrafish 毒性、xenograft 药效、大鼠药代动力学）。
- **训练**：不适用（非机器学习方法）。
- **工具**：RNA-seq 分析流程（未提供具体工具）、MST（Microscale Thermophoresis）、共聚焦显微镜、FRAP、MD 模拟软件（未提供具体名称）。
- **反馈回路**：体外机制 → 体内验证 → 药代/毒性评估。
- **假设**：FOXO3 是 PPVI 诱导线粒体自噬的关键转录因子；FOXO3 的 LLPS 是其转录激活的必要条件；PPVI 通过增强 FOXO3 LLPS 来放大 BNIP3/NIX 转录。

**文字流程**：
1. 对 PPVI 处理的乳腺癌细胞进行 RNA-seq，发现线粒体自噬相关通路富集；
2. 用 biotin-PPVI 亲和纯化 + 质谱鉴定 FOXO3 为直接结合蛋白，MST 验证结合亲和力；
3. 在细胞中敲除 FOXO3，验证 PPVI 诱导的线粒体自噬依赖 FOXO3；
4. 用活细胞成像观察 FOXO3 核内 puncta 形成，FRAP 验证液滴动态性，截短突变体定位驱动 LLPS 的区域（C2 区 151–673 aa）；
5. 用 MD 模拟揭示 PPVI 与 FOXO3 的互作模式；
6. 在 zebrafish 和 xenograft 模型中验证 PPVI 的体内抗肿瘤效果，同时评估毒性与药代动力学。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| biotin-PPVI pull-down + MS | 鉴定 PPVI 的直接结合蛋白 | 确定药物靶点，避免脱靶假设 | 输入：细胞裂解液 + biotin-PPVI；输出：候选蛋白列表 | Methods（biotin-labeled PPVI + MS） | 若移除，无法确定 FOXO3 为直接靶点，机制链条断裂 |
| MST 结合验证 | 定量验证 PPVI–FOXO3 直接互作 | 排除 pull-down 假阳性 | 输入：纯化 FOXO3 + PPVI；输出：结合亲和力（Kd） | Results（MST 数据） | 若移除，PPVI–FOXO3 互作缺乏定量证据 |
| FOXO3 敲除实验 | 验证 FOXO3 在 PPVI 诱导 mitophagy 中的必要性 | 建立因果关系 | 输入：FOXO3-KO 细胞 + PPVI；输出：mitophagy 水平变化 | Results（KO 后 mitophagy 减弱） | 若移除，无法证明 FOXO3 是功能必需节点 |
| 活细胞成像 + FRAP | 表征 FOXO3 核内 LLPS 液滴 | 证明相分离而非简单聚集 | 输入：GFP-FOXO3 细胞 + PPVI；输出：puncta 形态、FRAP 恢复曲线 | Results（活细胞成像、FRAP） | 若移除，无法区分 LLPS 与非特异性聚集 |
| 截短突变体 | 定位驱动 LLPS 的 FOXO3 区域 | 确定相分离的结构基础 | 输入：FOXO3 截短片段；输出：各片段 LLPS 能力 | Results（C2 区 151–673 aa 驱动 LLPS） | 若移除，无法明确 LLPS 的序列决定因素 |
| MD 模拟 | 原子级解释 PPVI–FOXO3 互作 | 提供机制性解释 | 输入：FOXO3 结构 + PPVI；输出：结合模式与构象变化 | Methods（MD 模拟） | 若移除，PPVI 增强 LLPS 的分子机制缺乏物理解释 |
| 体内模型（zebrafish + xenograft） | 验证体内药效与毒性 | 评估转化潜力 | 输入：PPVI 处理动物；输出：肿瘤体积、毒性指标 | Results（体内实验） | 若移除，无法评估 PPVI 的体内可行性 |

> 注：以上「移除后的影响」多为预期效应（基于逻辑推断），原文未提供系统性消融实验（如删除 LLPS 驱动区后 PPVI 是否失效）。[Analysis]

---

## 09 关键公式符号

**不适用**。本文为实验药理学研究，未涉及数学模型或形式化公式。MST 结合数据通常以 Kd 值报告，但原文摘要未给出具体数值或公式。

---

## 10 实验设计与证据链

- **数据集/群体**：乳腺癌细胞系（具体名称未提供）；zebrafish 胚胎；xenograft 小鼠；大鼠（药代动力学）。
- **规模**：未提供具体样本量。
- **指标**：线粒体自噬流（mKeima-Red-Mito-7 比率）、BNIP3/NIX 表达（qPCR/WB）、FOXO3 核定位、LLPS puncta 数量/大小、FRAP 恢复时间、肿瘤体积、心脏毒性指标、药代参数（半衰期、生物利用度）。
- **基线**：未提供明确基线（如未处理组或载体对照组）。
- **预算**：未提供。
- **骨干/仪器**：共聚焦显微镜（FRAP）、质谱仪、MST 仪器、MD 模拟计算资源（具体未提供）。
- **oracle 输入**：不适用（非 AI 方法）。
- **评测协议**：未提供详细统计方法。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| RNA-seq | PPVI 诱导 mitophagy 相关通路 | PPVI 处理 vs 未处理 | 线粒体自噬通路富集 | PPVI 激活 mitophagy 转录程序 | 未证明 FOXO3 是唯一上游调控因子 | Results |
| biotin-PPVI pull-down + MS | FOXO3 是 PPVI 直接靶点 | biotin-PPVI vs 对照 | FOXO3 被鉴定 | PPVI 直接结合 FOXO3 | 未提供结合位点信息 | Methods/Results |
| MST | PPVI–FOXO3 直接互作 | 梯度浓度 PPVI | 结合亲和力可测 | 直接物理互作 | 未提供 Kd 数值 | Results |
| FOXO3 KO | FOXO3 是 PPVI 诱导 mitophagy 的必要因子 | KO vs WT | KO 后 mitophagy 减弱 | FOXO3 功能必需 | 未排除其他 TF 的补偿作用 | Results |
| 活细胞成像 + FRAP | FOXO3 发生 LLPS | PPVI 处理 vs 未处理 | puncta 形成、FRAP 恢复 | FOXO3 核内 LLPS | 未证明 LLPS 是 mitophagy 的直接原因 | Results |
| 截短突变体 | C2 区驱动 LLPS | 各截短片段 | C2 区（151–673 aa）驱动 | LLPS 结构基础明确 | 未测试 C2 区缺失对 PPVI 响应的影响 | Results |
| MD 模拟 | PPVI 与 FOXO3 互作模式 | 模拟结合 vs 未结合 | 结合模式描述 | 原子级互作解释 | 未与实验突变验证交叉 | Methods |
| xenograft + zebrafish | PPVI 体内抗肿瘤与毒性 | PPVI 处理 vs 对照 | 肿瘤抑制 + 心脏毒性 | 体内有效但有毒性 | 未评估长期毒性或治疗窗口 | Results |

---

## 11 结论正确解读

- **任务范围**：本文仅证明 PPVI 在乳腺癌模型（体外细胞 + 异种移植小鼠 + zebrafish）中通过 FOXO3 依赖的 BNIP3/NIX 介导线粒体自噬发挥抗肿瘤作用。结论不适用于其他癌症类型或正常组织背景。
- **oracle/真值输入**：FOXO3 作为靶点的鉴定依赖 biotin-PPVI pull-down + MS，存在非特异性结合可能；MST 验证了直接互作，但未提供结合位点突变验证。
- **端到端状态**：从药物处理到表型（mitophagy、肿瘤抑制）的完整链条已建立，但「FOXO3 LLPS → BNIP3 转录激活」之间的因果证据为相关性（LLPS 增强与转录激活同时发生），未使用 LLPS 缺陷突变体进行功能回补实验。
- **算力成本**：MD 模拟的具体规模与成本未报告。
- **历史数据依赖**：RNA-seq 分析依赖参考基因组注释，未提供版本信息。
- **模型依赖**：不适用（非 AI 模型）。
- **最难情形**：体内实验中 PPVI 的极低口服生物利用度（<5%）和心脏毒性提示其作为临床药物的可行性存疑；zebrafish 心脏毒性结果是否外推至哺乳动物未验证。
- **群体/领域边界**：结论限于乳腺癌；FOXO3 相分离在其他肿瘤或正常组织中的作用未探讨。
- **不确定性**：PPVI 是否还通过其他靶点发挥作用未排除；FOXO3 LLPS 的生理相关性（是否在未处理细胞中也存在）未充分表征。

**有边界的复述**：在乳腺癌细胞和异种移植模型中，PPVI 通过直接结合 FOXO3 并增强其核内 LLPS（由 C2 区驱动），上调 BNIP3/NIX 介导的线粒体自噬，从而抑制肿瘤生长；但该化合物存在显著心脏毒性和极低口服生物利用度，其临床转化潜力有限。

---

## 12 作者自认局限

在提供的材料（摘要）中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，基于摘要措辞推断）：
- PPVI 的口服生物利用度极低（「extremely low oral bioavailability」），且表现心脏毒性（「cardiotoxicity in zebrafish」）——这暗示作者认识到该化合物的成药性障碍。
- 摘要未提供 FOXO3 结合位点、LLPS 驱动区的精细图谱，也未提供 LLPS 与转录激活之间的直接因果实验。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| FOXO3 被鉴定为 PPVI 直接靶点，但未提供结合位点 | PPVI 可能通过非特异性疏水作用与 FOXO3 的 IDR 结合，而非特异性口袋 | 若结合无特异性，则「药物–TF 相分离」调控的可设计性存疑 | 做 FOXO3 截短/点突变 + MST 竞争实验；用 HDX-MS 或 NMR 定位结合区域 | Methods（biotin pull-down + MS）；Results（MST） |
| LLPS 增强与 mitophagy 激活同时发生，但因果性未证明 | PPVI 可能先激活线粒体自噬，再间接导致 FOXO3 聚集；或两者平行发生 | 若 LLPS 不是 mitophagy 的原因，则「相分离–转录」模型不成立 | 使用 LLPS 缺陷 FOXO3 突变体（如 C2 区缺失）回补 KO 细胞，观察 mitophagy 是否恢复 | Results（截短突变体定位 C2 区） |
| 体内实验仅报告肿瘤抑制和毒性，未提供剂量-反应关系 | 抗肿瘤效果可能仅在接近毒性剂量时出现，治疗窗口极窄 | 治疗窗口决定临床可行性 | 做多剂量梯度实验，同时监测肿瘤体积和心脏功能 | Results（体内实验） |
| MD 模拟未与实验突变验证交叉 | 模拟可能预测了结合模式，但缺乏实验验证 | 模拟结果若无实验支撑，说服力有限 | 对模拟预测的关键残基做突变 + 结合/功能实验 | Methods（MD 模拟） |
| 未报告 RNA-seq 的差异基因列表或通路富集的统计阈值 | 无法独立评估 mitophagy 通路富集的强度 | 数据透明度影响结论可重复性 | 补充差异基因列表、GSEA 结果、多重检验校正方法 | Results（RNA-seq） |
| FOXO3 敲除后 mitophagy 减弱，但未检测 BNIP3/NIX 启动子上的 FOXO3 占位 | 「FOXO3 转录激活 BNIP3/NIX」是推断而非直接证据 | 若 FOXO3 不直接结合 BNIP3/NIX 启动子，则「相分离增强转录」模型需修正 | ChIP-seq/qPCR 检测 FOXO3 在 BNIP3/NIX 启动子上的结合 | Results（qPCR/WB 检测表达） |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **TF 相分离的序列决定因素**：FOXO3 的 C2 区（151–673 aa）驱动 LLPS。可迁移到课题：在预测 TF–DNA 互作时，可将 IDR 长度、电荷分布、疏水残基比例作为相分离倾向的特征，纳入深度学习模型的输入（如将 IDR 特征与 DBD 序列特征联合编码）。
2. **小分子–TF 直接互作可作为调控手段**：PPVI 直接结合 FOXO3 而非其 DNA 结合域，提示 TF 的 IDR 区域可作为药物靶点。可迁移：在虚拟筛选中，可将 TF 的 IDR 构象 ensemble 作为对接靶标，而非仅关注 DBD。
3. **MD 模拟用于验证小分子–IDR 互作**：本文用 MD 模拟解释 PPVI 与 FOXO3 的互作。可迁移：对候选小分子–TF IDR 复合物做 MD 模拟，计算结合自由能（MM-PBSA）或评估 IDR 构象变化（如 radius of gyration、contact map），为实验提供原子级假设。
4. **相分离–转录激活的关联**：FOXO3 的 LLPS 增强与其转录活性增强相关。可迁移：在构建 TF–DNA 结合预测模型时，可将「TF 是否具备相分离能力」作为特征，或预测 TF 在特定细胞状态下的相分离倾向，作为转录活性的代理指标。
5. **实验范式**：biotin 标记小分子 + pull-down + MS 鉴定靶点，是「小分子–TF 互作」研究的通用流程。可迁移：在课题中若发现某化合物影响 TF–DNA 结合，可用此流程鉴定直接靶点。
6. **体内外一致性验证**：zebrafish + xenograft 双模型验证，提示在课题中若开发 TF–DNA 互作调控分子，应至少使用两种体内模型评估效果与毒性。

---

## 15 与已有知识连接

- **FOXO3 与自噬**：FOXO3 是已知的自噬相关转录因子，激活 BNIP3、LC3、ATG 等基因（外部知识：Webb & Brunet, 2014, *Oncogene*）。本文将其与 LLPS 关联，扩展了 FOXO3 调控机制的理解。
- **TF 相分离与转录**：已知多种 TF（如 p53、Oct4、Gcn4）通过 LLPS 形成转录凝聚体（外部知识：Boija et al., 2018, *Cell*；Shin & Brangwynne, 2017, *Science*）。本文首次将 FOXO3 纳入该框架。
- **天然产物靶向 TF**：已有报道天然产物直接结合 TF 并调控其活性（如 curcumin 结合 p53；外部知识：Moos et al., 2004）。本文的独特之处在于靶向 TF 的相分离行为而非经典活性位点。
- **小分子–相分离调控**：近年有研究报道小分子可诱导或抑制蛋白相分离（如 1,6-hexanediol 抑制 LLPS；外部知识：Kroschwald et al., 2015）。本文提供了一种天然产物增强 TF LLPS 的案例。
- **MD 模拟在蛋白–配体互作中的应用**：MD 模拟广泛用于预测小分子–蛋白结合模式（外部知识：Hollingsworth & Dror, 2018, *Neuron*）。本文将其用于 TF IDR 与小分子的互作分析，是该方法的延伸。
- **可迁移领域**：本文的「小分子–TF 相分离–转录输出」框架可迁移至其他 TF（如 p53、MYC、NF-κB）的研究，也可用于设计基于相分离调控的 TF 活性预测模型。

---

## 16 研究想法

**Agent 生成的研究候选**

1. **名称**：TF-LLPS 预测模型（TF-LLPS-Predictor）
   - **来源局限/观察**：本文发现 FOXO3 的 C2 区（IDR）驱动 LLPS，但现有 TF–DNA 结合预测模型（如 DeepBind、DeepSEA）未考虑 TF 的相分离倾向。
   - **核心假设**：TF 的 IDR 特征（长度、电荷、疏水性、低复杂度序列比例）可预测其相分离能力，且相分离能力与转录激活强度正相关。
   - **增量**：将 IDR 特征编码加入 TF–DNA 结合预测模型，或在现有模型（如 CNN/Transformer）中引入相分离倾向作为辅助任务。
   - **初步方法**：从 UniProt 获取 TF 序列，用 catGRANULE 或 PLAAC 计算相分离倾向；用 ENCODE 数据训练 TF–DNA 结合模型，加入相分离特征做多任务学习。
   - **验证方式**：在已知相分离 TF（如 FOXO3、p53、Oct4）上做留一法验证；用 CRISPR 突变 IDR 后检测转录活性变化。
   - **创新状态**：unverified

2. **名称**：小分子–TF IDR 结合虚拟筛选流程
   - **来源局限/观察**：PPVI 直接结合 FOXO3 的 IDR 区域，但现有虚拟筛选工具（如 AutoDock、Glide）主要针对折叠结构域，对 IDR 靶标支持不足。
   - **核心假设**：用 MD 生成的 IDR 构象 ensemble 作为对接靶标，可提高小分子–IDR 结合预测的准确性。
   - **增量**：建立「IDR 构象采样 → ensemble 对接 → MD 验证」的标准流程，并应用于 TF 家族。
   - **初步方法**：用 AlphaFold3 或 MD 模拟生成 FOXO3 IDR 构象 ensemble；用 Glide/ AutoDock Vina 对接 PPVI 类似物库；对 top hits 做 100 ns MD 模拟计算结合自由能。
   - **验证方式**：用 MST/ITC 验证 top hits 与 FOXO3 的结合；用细胞实验检测 LLPS 增强效果。
   - **创新状态**：unverified

3. **名称**：相分离–转录活性耦合的定量模型
   - **来源局限/观察**：本文证明 PPVI 增强 FOXO3 LLPS 并促进转录，但未建立 LLPS 强度与转录输出之间的定量关系。
   - **核心假设**：TF 的核内凝聚体大小/数量与其靶基因表达水平之间存在可量化的剂量-响应关系。
   - **增量**：将 LLPS 定量指标（puncta 大小、FRAP 恢复时间、凝聚体数量）与 RNA-seq 数据联合建模。
   - **初步方法**：用高内涵成像获取 FOXO3 puncta 特征；用 RNA-seq 获取 BNIP3/NIX 表达；用回归模型（如随机森林或高斯过程）拟合 LLPS 指标与转录输出的关系。
   - **验证方式**：在不同 PPVI 浓度下验证模型预测；用 LLPS 缺陷突变体检验模型外推性。
   - **创新状态**：unverified

4. **名称**：TF 相分离作为药物毒性预测标志物
   - **来源局限/观察**：PPVI 增强 FOXO3 LLPS 的同时表现出心脏毒性，提示 TF 相分离过度增强可能与毒性相关。
   - **核心假设**：小分子诱导的 TF 相分离强度与脱靶毒性（如心脏毒性）相关，可作为早期毒性筛选指标。
   - **增量**：建立「TF 相分离增强倍数 vs 毒性剂量」的关联数据库。
   - **初步方法**：用 zebrafish 心脏毒性模型测试多个 PPVI 类似物；用成像定量 LLPS 增强程度；用相关性分析建立预测模型。
   - **验证方式**：在独立化合物库中验证预测准确性。
   - **创新状态**：unverified

5. **名称**：FOXO3 相分离的序列-结构-功能图谱
   - **来源局限/观察**：本文仅定位 C2 区（151–673 aa）驱动 LLPS，未精细到关键残基。
   - **核心假设**：C2 区内的特定基序（如酪氨酸/精氨酸富集区）是 LLPS 的关键驱动子，且与 DNA 结合活性协同。
   - **增量**：提供 FOXO3 LLPS 的残基级解析，为设计相分离调控肽或小分子提供靶点。
   - **初步方法**：系统性丙氨酸扫描 C2 区；用共聚焦成像和 FRAP 检测各突变体的 LLPS 能力；用 ChIP-seq 检测 DNA 结合变化。
   - **验证方式**：在细胞和体外重建系统中验证关键残基的功能。
   - **创新状态**：unverified