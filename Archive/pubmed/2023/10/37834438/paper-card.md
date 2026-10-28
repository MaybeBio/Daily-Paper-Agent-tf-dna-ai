## 01 基本信息
- **标题**：Three-Dimensional Modeling of CpG DNA Binding with Matrix Lumican Shows Leucine-Rich Repeat Motif Involvement as in TLR9-CpG DNA Interactions
- **作者与单位**：Choi, Tansol; Maiti, George; Chakravarti, Shukti（单位未提供）
- **期刊/预印本平台**：International Journal of Molecular Sciences
- **年份**：2023
- **论文类型**：计算建模研究（in silico）
- **领域**：蛋白质-DNA 互作；细胞外基质蛋白（lumican）与 CpG DNA 结合机制
- **关键词**：lumican；TLR9；CpG DNA；LRR motif；同源建模；分子对接
- **DOI/arXiv 号**：10.3390/ijms241914990
- **代码**：未提供
- **数据**：UniProt 序列（Q9EQU3, P51885）、PDB 结构（3WPF）、AlphaFold 数据库
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦 SLRP 家族蛋白 lumican 与 CpG DNA 的分子互作机制，通过同源建模与刚性对接预测结合界面，与 TLR9-CpG DNA 互作进行结构类比。对「TF–DNA 结合机制 × AI/物理模拟」课题的可迁移点在于：LRR 重复基序的 DNA 结合模式、AlphaFold 结构在无晶体结构蛋白-DNA 对接中的应用、以及刚性对接的局限性与 MD 模拟的改进方向。

## 02 一句话总结
本文通过同源建模和刚性对接（HDOCK），预测了 lumican 的 LRR1–11 基序与 22-mer CpG ODN_2395 的结合界面（32 个氨基酸残基，BSA 1803 Å²），并发现其互作模式（氢键、盐桥、疏水作用）与 TLR9-CpG DNA 结合类似，但结合面积更小、强度可能更低。

## 03 研究问题
- **具体问题**：lumican 蛋白核心区域中哪些氨基酸残基与 CpG DNA 互作？互作的分子机制（键合类型、结合面积）是什么？与 TLR9-CpG DNA 互作有何异同？
- **为什么重要**：lumican 在实验中被证明可结合并隔离 CpG DNA，从而抑制 TLR9 信号通路，但其分子层面的结合细节未知。阐明该机制有助于理解 ECM 蛋白如何调控先天免疫，并为 TLR9 介导的炎症和自身免疫病提供潜在药物靶点。
- **现有方法为何不足**：lumican 无晶体结构；TLR9 与 CpG DNA 的晶体结构（如 PDB: 3WPC）仅针对较短配体（12-mer），而本研究使用的 22-mer CpG ODN_2395 是实验验证的强效 TLR9 激动剂，其与 TLR9 的互作尚无结构信息。
- **精确研究问题**：Can homology modeling and rigid docking predict the LRR motifs and amino acid residues in lumican that mediate CpG ODN_2395 binding, and do these interactions resemble TLR9-CpG DNA binding?

## 04 背景与发展脉络
- **阶段一：LRR 基序的发现与分类**（1985 年起）：LRR 为约 24 氨基酸的重复基序，含保守疏水残基，形成马蹄形结构。SLRP 家族（含 lumican）与 TLR 家族均属 LRR 超家族。
- **阶段二：TLR9-CpG DNA 结构解析**：TLR9 胞外域（ECD）与 CpG DNA 的晶体结构（如 PDB: 3WPC）揭示了 LRR 基序与 DNA 的互作模式，主要涉及 N 端 LRR1–8 和 C 端 LRR20–22。
- **阶段三：lumican 的免疫调控功能发现**：实验表明 lumican 可结合 CpG DNA 并抑制 TLR9 信号，但分子机制未知。
- **阶段四（本文）**：利用 AlphaFold 预测 lumican 结构，结合 HDOCK 刚性对接，首次在分子水平预测 lumican-CpG DNA 互作界面。
- **脉络标注**：仅本文框架（基于本文引言与讨论的归纳，未进行外部文献系统核验）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| lumican 无实验结构 | 无法直接进行结构生物学分析 | lumican 未被结晶 | Methods 4.1 节：使用 AlphaFold 预测结构 |
| 22-mer CpG ODN_2395 与 TLR9 无共晶结构 | 无法直接比对 lumican 与 TLR9 的互作模式 | 现有 TLR9-CpG DNA 晶体结构仅针对 12-mer 配体 | Introduction 节：提及 PDB: 3WPC 为 12-mer CpG ODN_1668 |
| ssDNA 构象柔性 | 刚性对接可能无法准确反映真实结合构象 | ssDNA 磷酸基团间静电排斥导致构象多变 | Discussion 节：作者承认刚性 B 型 DNA 模型的局限 |
| 模板选择受限 | HDOCK 无法使用 TLR9-CpG DNA 共晶结构作为模板 | CpG ODN_2395 与 CpG ODN_1668 序列覆盖率仅 27%，低于 50% 阈值 | Methods 4.5 节：HDOCK 自动排除低覆盖率模板 |
| 结合强度无法直接测量 | 仅能通过 BSA 间接推断 | 计算模型无法提供实验结合亲和力数据 | Results 2.2 节：BSA 比较（lumican 1803 Å² vs TLR9 2094 Å²） |

## 06 核心思想
1. **表面方法**：使用 AlphaFold 预测 lumican 三维结构，通过 HDOCK 服务器进行 lumican-CpG ODN_2395 和 TLR9 ECD-CpG ODN_2395 的刚性对接，并用 PLIP 分析互作键合类型。
2. **核心洞察**：lumican 的 LRR1–11 基序（特别是 LRR2–8）形成与 TLR9 N 端 LRR2–13 类似的 DNA 结合凹槽，两者均通过氢键、盐桥和疏水作用与 CpG DNA 互作，但 lumican 的结合面积更小（1803 vs 2094 Å²），提示其结合强度可能更低。这一发现将 ECM 蛋白与 TLR 家族的 DNA 识别机制联系起来，支持「LRR 基序是通用的 DNA 结合模块」假说。
3. **可能的普适教训** [Analysis]：LRR 超家族蛋白可能共享保守的 DNA 结合模式，即使整体序列相似性低（22% 同一性），结构域级别的功能趋同仍可发生。对于 TF–DNA 互作研究，这提示在预测新型 DNA 结合蛋白时，应关注结构域级别的保守性而非全序列相似性。

## 07 方法总览
- **输入**：小鼠 lumican 氨基酸序列（UniProt P51885）、小鼠 TLR9 ECD 序列（UniProt Q9EQU3）、CpG ODN_2395 序列（5′-TCGTCGTTTTCGGCGCGCGCCG-3′）、TLR9 未结合配体晶体结构（PDB: 3WPF）
- **输出**：lumican-CpG ODN_2395 和 TLR9 ECD-CpG ODN_2395 的预测复合物结构、互作残基列表、BSA 值、键合类型
- **模块**：
  1. 结构获取：AlphaFold 数据库获取 lumican 预测结构；PDB 获取 TLR9 ECD 结构
  2. 序列比对：Clustal Omega 进行 lumican 与 TLR9 的局部序列比对
  3. 结构比对：PyMOL Align 进行结构叠加
  4. 表面电荷分析：APBS 计算静电势分布
  5. 分子对接：HDOCK 服务器进行刚性对接，生成 100 个复合物，取 top1
  6. 互作分析：PLIP 检测氢键、盐桥、疏水互作
- **训练**：不适用（无机器学习训练）
- **工具**：AlphaFold DB、Clustal Omega、PyMOL（含 APBS 插件）、HDOCK 服务器、PLIP
- **反馈回路**：无（单轮对接，无迭代优化）
- **假设**：① AlphaFold 预测的 lumican 结构准确；② 刚性对接足以捕捉关键互作模式；③ B 型 DNA 构象适用于 CpG ODN_2395
- **文字流程**：获取 lumican 和 TLR9 序列 → 从 AlphaFold DB 获取 lumican 预测结构 → 从 PDB 获取 TLR9 ECD 结构 → Clustal Omega 序列比对确认 LRR 区域对应关系 → PyMOL 结构叠加 → APBS 表面电荷分析 → 构建 B 型 CpG ODN_2395 结构 → HDOCK 分别对接 lumican 和 TLR9 ECD 与 CpG ODN_2395 → 取 top1 复合物 → PLIP 分析互作键合 → 计算 BSA → 比较两种蛋白的互作模式

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AlphaFold 结构预测 | 获取 lumican 三维结构 | lumican 无晶体结构 | 输入：氨基酸序列；输出：预测结构（PDB 格式） | Methods 4.1 节：pLDDT > 90%，PAE 0–15 Å | 无 lumican 结构则无法进行后续对接（必需模块） |
| Clustal Omega 序列比对 | 确认 lumican 与 TLR9 的 LRR 基序对应关系 | 识别保守区域，指导结构比对 | 输入：两条序列；输出：比对结果（22% 同一性，40% 相似性） | Results 2.1 节：Figure S1 | 无法定位 LRR 对应区域，影响后续分析 |
| PyMOL 结构比对 | 叠加 lumican 与 TLR9 的 LRR 结构域 | 比较结构相似性 | 输入：两个结构；输出：RMSD 6.4 Å 的叠加结构 | Results 2.1 节：Figure 1A | 无法直接比较结构相似性 |
| APBS 表面电荷分析 | 可视化蛋白表面静电势 | 预测 DNA 结合偏好（正电荷区域利于结合负电荷 DNA 骨架） | 输入：蛋白结构；输出：静电势图 | Results 2.1 节：Figure 1B,C | 无法评估静电互补性 |
| HDOCK 刚性对接 | 预测蛋白-DNA 复合物结构 | 核心预测模块 | 输入：蛋白结构 + DNA 结构；输出：100 个复合物，取 top1 | Methods 4.5 节：Table 5 | 无对接则无法获得结合界面（必需模块） |
| PLIP 互作分析 | 检测氢键、盐桥、疏水互作 | 表征结合机制 | 输入：复合物结构；输出：互作残基和键合类型列表 | Results 2.3 节：Table 3 | 无法了解具体互作化学性质 |
| BSA 计算 | 量化结合界面大小 | 间接推断结合强度 | 输入：复合物结构；输出：BSA 值（lumican 1803 Å²，TLR9 2094 Å²） | Results 2.2 节：Figure 2 | 无法比较两种蛋白的结合强度 |

## 09 关键公式符号
- **BSA（Buried Surface Area）**：BSA = (ASA_protein + ASA_DNA) − ASA_complex，其中 ASA 为可及表面积（accessible surface area），单位为 Å²。用于量化蛋白-DNA 结合界面大小，BSA 越大通常表示结合亲和力越高。来源：Methods 4.6 节。
- **单残基 BSA 百分比**：BSA_residue (%) = (ASA_free − ASA_bound) / ASA_free × 100%，用于评估每个残基在结合中的贡献。来源：Methods 4.6 节。
- **pLDDT（predicted Local Distance Difference Test）**：AlphaFold 的逐残基置信度评分（0–100），>90 表示高置信度。用于评估预测结构的可靠性。来源：Methods 4.1 节。
- **PAE（Predicted Aligned Error）**：预测对齐误差（Å），用于评估结构域间相对位置的不确定性。来源：Methods 4.1 节。
- **RMSD（Root Mean Square Deviation）**：结构叠加后的原子均方根偏差（Å），用于衡量结构相似性。本文中 lumican 与 TLR9 的 LRR 结构比对 RMSD = 6.4 Å。来源：Methods 4.2 节。

## 10 实验设计与证据链
- **数据集/群体**：小鼠 lumican（UniProt P51885）、小鼠 TLR9（UniProt Q9EQU3）、CpG ODN_2395（22-mer，Class C）、TLR9 ECD 未结合配体结构（PDB: 3WPF）
- **规模**：单蛋白对单配体对接，HDOCK 生成 100 个复合物，仅分析 top1
- **指标**：BSA、互作残基数、氢键数、盐桥数、疏水互作数、pLDDT、RMSD
- **基线**：TLR9 ECD-CpG ODN_2395 对接结果作为 lumican 的参照
- **预算**：未提供
- **骨干/仪器**：不适用（纯计算研究）
- **oracle 输入**：AlphaFold 预测结构（lumican）、PDB 实验结构（TLR9 ECD）
- **评测协议**：无实验验证；通过与 TLR9 已知互作模式进行间接比对

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| lumican-CpG ODN_2395 对接 | lumican 的 LRR 基序参与 DNA 结合 | HDOCK top1 复合物 | 32 个 lumican 残基与 9 个 DNA 碱基互作，BSA 1803 Å² | LRR1–11 是 lumican 的 DNA 结合区域 | 无法确定结合亲和力或动态结合过程 | Results 2.2, 2.3 节 |
| TLR9 ECD-CpG ODN_2395 对接 | TLR9 与 22-mer CpG DNA 的互作模式 | HDOCK top1 复合物 | 33 个 TLR9 残基与 10 个 DNA 碱基互作，BSA 2094 Å² | TLR9 N 端 LRR2–13 是主要结合区域 | 无法与实验结构直接验证（无 22-mer 共晶结构） | Results 2.4 节 |
| lumican vs TLR9 互作模式比较 | 两者共享类似的 DNA 结合机制 | BSA、键合类型、残基组成对比 | lumican BSA 较小（1803 vs 2094 Å²），但键合类型相似（氢键、盐桥、疏水） | lumican 可能以较低亲和力模拟 TLR9 的 DNA 结合 | 无法推断功能等效性 | Results 2.2–2.4 节 |
| 序列与结构比对 | lumican LRR1–11 与 TLR9 LRR1–13 结构相似 | Clustal Omega + PyMOL 叠加 | 22% 同一性，40% 相似性，RMSD 6.4 Å | 结构域级别的保守性支持功能类比 | 低序列同一性意味着结合细节可能不同 | Results 2.1 节 |
| 胶原结合位点重叠分析 | lumican 的 DNA 结合位点与胶原结合位点重叠 | 对接界面与已知胶原结合残基比对 | Asp212 等残基同时参与 DNA 和胶原结合 | 胶原可能竞争性抑制 lumican-DNA 结合 | 未进行竞争实验验证 | Results 2.5 节 |

## 11 结论正确解读
- **任务范围**：本研究仅预测了 lumican 与 CpG ODN_2395 的静态结合模式，未涉及动态结合过程、结合动力学或细胞内环境效应。
- **oracle/真值输入**：lumican 结构来自 AlphaFold 预测（非实验结构），TLR9 结构来自未结合配体的晶体结构（PDB: 3WPF），DNA 采用刚性 B 型构象。
- **端到端状态**：非端到端；仅完成对接预测，无 MD 模拟、无实验验证（如突变分析、SPR/ITC 亲和力测定）。
- **算力成本**：未提供；HDOCK 为轻量级对接工具，计算成本较低。
- **历史数据依赖**：依赖 AlphaFold 训练数据（PDB 中已知蛋白结构）和 HDOCK 模板库（含 TLR3-dsRNA 复合物等）。
- **模型依赖**：结果高度依赖 AlphaFold 预测准确性、HDOCK 刚性对接假设（蛋白和 DNA 均视为刚体）、以及 B 型 DNA 构象假设。
- **最难情形**：ssDNA 的构象柔性是最大挑战；作者承认刚性 B 型模型可能无法捕捉真实结合构象。
- **群体/领域边界**：结果仅适用于小鼠 lumican 和 TLR9；人类同源蛋白可能因序列差异而结合模式不同。
- **不确定性**：BSA 差异（1803 vs 2094 Å²）仅间接暗示结合强度差异，未通过自由能计算或实验验证。
- **有边界的复述**：在 AlphaFold 预测结构和刚性对接条件下，lumican 的 LRR1–11 基序（特别是 LRR2–8）可能通过氢键、盐桥和疏水作用与 CpG ODN_2395 结合，结合界面小于 TLR9 ECD 与同一配体的结合界面，但两者共享类似的 LRR 介导的 DNA 识别模式。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 使用刚性 B 型 DNA 模型 | ssDNA 的构象柔性未被考虑，真实结合构象可能不同 | 使用 MD 模拟（如 AMBER）在 100 ns 时间尺度上研究动态互作 | Discussion 节 |
| 使用 lumican 核心蛋白而非糖蛋白/蛋白聚糖形式 | 忽略了 KS 糖胺聚糖侧链对 DNA 结合的影响 | 未来研究可纳入糖基化形式 | Discussion 节 |
| 缺乏实验验证 | 计算预测未经突变分析或结合实验验证 | 未明确提及 | Discussion 节（隐含） |
| 模板选择受限 | HDCPK 无法使用 TLR9-CpG ODN_1668 共晶结构作为模板（序列覆盖率不足） | 未明确提及 | Methods 4.5 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 仅分析 HDOCK top1 复合物 | 对接评分最高的复合物不一定代表真实结合构象；未报告 top1 与其它复合物的差异 | 若 top1 是假阳性，则所有后续分析无效 | 分析 top10 或 top100 复合物的聚类，检查结合位点一致性 | Methods 4.5 节：仅取 top1 |
| BSA 差异（1803 vs 2094 Å²）被解释为结合强度差异 | BSA 与亲和力并非严格线性相关；未计算结合自由能 | 结论「lumican 结合更弱」缺乏定量支持 | 使用 MM-PBSA 或 FEP 计算结合自由能 | Results 2.2 节 |
| 使用 TLR3-dsRNA 复合物作为对接模板 | TLR3 识别 dsRNA，而 TLR9 识别 ssDNA，核酸结合模式可能不同 | 模板选择可能引入系统性偏差 | 尝试其它 DNA-蛋白复合物模板，比较结果稳健性 | Methods 4.5 节：Table 5 |
| 未进行 MD 模拟验证 | 刚性对接无法评估结合稳定性；作者在讨论中承认此局限 | 动态模拟可能揭示不同的结合模式 | 对 top1 复合物进行 100 ns MD 模拟，检查 RMSD 稳定性和关键互作保持 | Discussion 节 |
| 胶原结合位点重叠分析缺乏定量支持 | 仅基于残基位置重叠推断竞争关系，未计算胶原存在时的结合自由能变化 | 若胶原竞争结合，则 lumican 在 ECM 中的 DNA 隔离功能可能受胶原调控 | 进行三分子体系（lumican-DNA-胶原）对接或 MD 模拟 | Results 2.5 节 |
| 未报告 HDOCK 评分或置信度 | 无法评估对接预测的可靠性 | 低置信度预测可能不可靠 | 报告 HDOCK 评分、置信度分数及与已知结构的基准测试 | Methods 4.5 节：未提供具体评分 |

## 14 学到什么
**Agent 提炼的知识候选**

1. **LRR 基序作为通用 DNA 结合模块**：本文表明，即使整体序列同一性仅 22%，lumican 的 LRR1–11 与 TLR9 的 LRR1–13 仍共享类似的 DNA 结合模式。对 TF–DNA 互作研究的启示：在预测新型 DNA 结合蛋白时，应关注结构域级别的保守性（如 LRR 重复数、凹槽曲率、正电荷分布），而非仅依赖序列同源性。可迁移方法：对候选 TF 进行 LRR 基序扫描 + 结构预测 + 表面电荷分析，快速筛选潜在 DNA 结合位点。

2. **AlphaFold 预测结构在无晶体结构蛋白-DNA 对接中的可行性**：本文使用 AlphaFold 预测的 lumican 结构进行对接，pLDDT > 90% 的区域（残基 40–309）被用于分析。对 TF–DNA 研究的启示：对于缺乏实验结构的 TF，可先用 AlphaFold 获取高置信度结构域，再进行对接预测。注意：仅使用 pLDDT > 90% 的区域可减少预测误差影响。

3. **刚性对接的适用边界与 MD 模拟的必要性**：本文明确承认刚性 B 型 DNA 模型的局限，并建议 MD 模拟作为后续验证。对 TF–DNA 研究的启示：刚性对接适合初步筛选结合位点，但 ssDNA 的构象柔性要求 MD 模拟（如 AMBER）来捕捉动态结合过程。可迁移方法：对接后对 top 复合物进行 100 ns MD 模拟，检查关键残基互作稳定性。

4. **BSA 作为结合强度间接指标的使用与局限**：本文用 BSA 比较 lumican 和 TLR9 的结合强度，但未计算自由能。对 TF–DNA 研究的启示：BSA 可用于初步比较，但应辅以 MM-PBSA/GBSA 或实验亲和力测定（SPR/ITF）来定量验证。

5. **表面电荷互补性分析**：APBS 静电势分析显示 lumican 凹面存在正负电荷斑块，与 DNA 的负电荷骨架互补。对 TF–DNA 研究的启示：在预测 TF 的 DNA 结合偏好时，可先进行静电势分析，识别正电荷富集区域作为候选 DNA 结合位点。

6. **功能位点重叠分析**：本文发现 lumican 的 DNA 结合残基（如 Asp212）与胶原结合位点重叠，提示配体竞争可能性。对 TF–DNA 研究的启示：TF 可能同时结合 DNA 和其它蛋白/配体，分析结合位点重叠可揭示竞争性调控机制。

## 15 与已有知识连接
- **TLR9-CpG DNA 晶体结构**：本文引用了 TLR9 与 CpG ODN_1668 的共晶结构（PDB: 3WPC），并与其预测结果进行比对。该结构是 TLR9-DNA 互作的关键实验参考，可进一步查阅 Ohto et al. (2015) 或类似文献获取详细互作残基信息。
- **LRR 超家族结构-功能关系**：本文基于 LRR 基序的保守性将 lumican 与 TLR9 联系起来。LRR 超家族还包括 NLR、RLR 等免疫受体，其 DNA/RNA 结合机制可作横向比较。
- **AlphaFold 在蛋白-核酸互作预测中的应用**：本文是 AlphaFold 预测结构用于蛋白-DNA 对接的案例之一。可对比其他使用 AlphaFold + 对接/MD 研究 TF-DNA 互作的文献（如 AlphaFold2 在转录因子结构预测中的应用）。
- **SLRP 家族功能**：lumican 属于 SLRP 家族，该家族成员（如 decorin、biglycan）也参与免疫调控。本文为 SLRP 的核酸结合功能提供了首个分子模型，可扩展至其他 SLRP 成员。
- **CpG ODN 作为免疫调节剂**：CpG ODN_2395 是 Class C 型 TLR9 激动剂，在疫苗佐剂和免疫治疗中有应用。本文的 lumican 结合模型提示 ECM 蛋白可能影响 CpG ODN 的生物利用度，与药物递送研究相关。
- **候选方向（未验证）** [Analysis]：本文的 lumican-CpG DNA 模型可进一步与 TF-DNA 互作数据库（如 CIS-BP、JASPAR）中的结构信息比较，探索 LRR 类蛋白与经典 TF（如锌指、bZIP）在 DNA 识别策略上的异同。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：LRR-TF 结构域扫描与 DNA 结合偏好预测
   - **来源局限/观察**：本文发现 lumican 的 LRR 基序可结合 DNA，但仅测试了单一 CpG 序列。LRR 基序是否具有序列特异性 DNA 结合能力未知。
   - **核心假设**：LRR 基序的 DNA 结合具有序列偏好性，可通过凹槽残基组成预测。
   - **初步方法**：对 lumican 及 TLR9 的 LRR 基序进行丙氨酸扫描突变 + 对接评分比较；使用 ChIP-seq 或 SELEX 数据（如有）验证序列偏好。
   - **验证方式**：SPR/ITC 测定不同序列 DNA 的结合亲和力；MD 模拟比较不同序列的结合自由能。
   - **创新状态**：unverified

2. **候选名称**：AlphaFold 结构 + 柔性对接 + MD 的 TF-DNA 结合预测流程
   - **来源局限/观察**：本文使用刚性 B 型 DNA 和刚性对接，作者承认无法捕捉 ssDNA 构象柔性。TF-DNA 互作同样面临 DNA 构象变化问题。
   - **核心假设**：结合柔性对接（如 HADDOCK）和 MD 模拟（AMBER）可提高 TF-DNA 结合构象预测准确性。
   - **初步方法**：选取已知结构的 TF-DNA 复合物作为基准，比较刚性对接 vs 柔性对接 vs 对接+MD 的预测精度（RMSD、native contact 保留率）。
   - **验证方式**：与 PDB 中实验结构比对；对未知复合物进行预测后，用突变实验验证关键残基。
   - **创新状态**：partially checked（柔性对接和 MD 在蛋白-DNA 互作中已有应用，但针对 LRR 类蛋白的系统评估较少）

3. **候选名称**：lumican 与 TF 的 DNA 结合竞争调控网络
   - **来源局限/观察**：本文提出 lumican 可能通过隔离 CpG DNA 来抑制 TLR9 信号。类似地，ECM 蛋白可能隔离 TF 的 DNA 配体，从而调控基因表达。
   - **核心假设**：lumican（及 SLRP 家族）可通过结合特定 DNA 序列，竞争性抑制 TF 与启动子/增强子的结合。
   - **初步方法**：从本文鉴定的 lumican DNA 结合残基出发，预测其结合的 DNA 序列基序；与 JASPAR 数据库中 TF 基序比对，寻找重叠；在炎症相关基因启动子中搜索候选结合位点。
   - **验证方式**：EMSA 竞争实验（lumican + TF + DNA）；报告基因实验检测 lumican 对 TF 转录活性的影响。
   - **创新状态**：unverified

4. **候选名称**：糖基化对 lumican-DNA 结合的影响
   - **来源局限/观察**：本文使用 lumican 核心蛋白建模，但成熟 lumican 常带有 KS 糖链，作者承认此局限。
   - **核心假设**：KS 糖链的空间位阻或电荷效应会显著改变 lumican 的 DNA 结合能力。
   - **初步方法**：使用 Glycam 力场构建糖基化 lumican 模型，与 DNA 进行对接和 MD 模拟；比较糖基化/非糖基化形式的 BSA 和结合自由能。
   - **验证方式**：表达纯化糖基化和非糖基化 lumican，用 SPR 比较 DNA 结合亲和力。
   - **创新状态**：unverified

5. **候选名称**：LRR 基序 DNA 结合的结构决定因素的系统进化分析
   - **来源局限/观察**：本文发现 lumican 与 TLR9 的 LRR 基序共享 DNA 结合功能，但两者序列同一性仅 22%。LRR 基序中哪些残基是 DNA 结合的关键决定因素未知。
   - **核心假设**：LRR 基序中特定位置的疏水残基和正电荷残基是 DNA 结合的关键，可通过进化保守性识别。
   - **初步方法**：收集 LRR 超家族中已知 DNA/RNA 结合蛋白（TLR3/7/8/9、NLR 等），进行多序列比对和保守残基分析；结合结构比对识别共同 DNA 结合残基。
   - **验证方式**：对预测的关键残基进行突变，检测 DNA 结合能力变化。
   - **创新状态**：unverified