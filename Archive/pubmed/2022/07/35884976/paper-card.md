## 01 基本信息

- **标题**：CDI Exerts Anti-Tumor Effects by Blocking the FoxM1-DNA Interaction
- **作者与单位**：Jang, Woo Dae; Lee, Mi Young; Mun, Jihye; Lim, Gyutae; Oh, Kwang-Seok（单位未在摘要中提供）
- **期刊/预印本平台**：Biomedicines
- **年份**：2022-07-28
- **论文类型**：实验研究（含计算模拟）
- **领域**：癌症生物学；转录因子抑制剂发现；蛋白质-DNA 互作
- **关键词**：FoxM1；转录因子；DNA 结合抑制剂；TR-FRET；分子对接；分子动力学模拟；乳腺癌
- **DOI/arXiv 号**：10.3390/biomedicines10071671
- **代码**：未提供
- **数据**：RNA-Seq 数据（未提供 accession 号）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「小分子抑制剂阻断 TF–DNA 物理互作」这一子方向，核心是转录因子 FoxM1 的 DNA 结合结构域（DBD）作为药物靶点。方法上结合了体外生化实验（TR-FRET）、细胞实验（增殖/凋亡/RNA-Seq）与计算模拟（对接 + MD），属于「物理模拟（对接/MD）辅助 TF–DNA 互作抑制剂发现」的典型范例。对课题的启示在于：如何用 TR-FRET 定量 TF–DNA 结合、如何用对接/MD 解释小分子阻断机制、以及如何用 RNA-Seq 验证靶向 TF 的转录组后果。

## 02 一句话总结

本文通过 TR-FRET 筛选发现小分子 CDI 能抑制 FoxM1-DBD 与共识 DNA 序列的结合（IC50 = 4.9 µM），在 MDA-MB-231 乳腺癌细胞中抑制增殖、诱导凋亡并下调 FoxM1 及其下游靶基因表达，对接与 MD 模拟提示 CDI 结合于 FoxM1-DBD 的 DNA 互作界面附近。

## 03 研究问题

- **具体问题**：能否找到一种小分子化合物，通过直接阻断 FoxM1 转录因子与其靶 DNA 序列的物理结合，从而抑制 FoxM1 驱动的肿瘤细胞增殖？
- **为什么重要**：FoxM1 在大多数人类癌症中过表达，是公认的癌症治疗靶点。然而已有的 FoxM1 抑制剂（如天然产物 honokiol、thiostrepton、sinomycin A）存在脱靶效应强、选择性差的问题；合成化合物 FDI-6 虽选择性较好，但对 FoxM1 蛋白水平影响微弱。因此需要开发具有明确作用机制（直接阻断 DNA 结合）的新型抑制剂。
- **现有方法为何不足**：天然产物类抑制剂多靶点、脱靶效应强，无法用于阐明 FoxM1 抑制的特异性后果；FDI-6 虽能阻断 DNA 结合，但对 FoxM1 蛋白水平影响小，且其作用机制尚未被计算模拟充分验证。
- **精确的 Can 问题**：Can a small molecule (CDI) directly block the FoxM1-DBD–DNA interaction, and does this blockade translate into anti-proliferative and pro-apoptotic effects in FoxM1-high breast cancer cells?

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论，属于「仅本文框架」，未经外部系统核验。

1. **FoxM1 作为癌症靶点的确立**：FoxM1 属于 Forkhead box 家族，含保守的「 winged helix 」DNA 结合结构域，在增殖细胞中表达，调控细胞周期与有丝分裂相关基因（cyclin B、survivin、Aurora B、Cdc25b、Plk1）。在多种癌症中过表达，与肿瘤侵袭、血管生成、转移和耐药相关。
2. **FoxM1 抑制策略的演进**：
   - 早期策略：RNAi 或条件性敲除动物模型证明 FoxM1 抑制可缩小肿瘤 → 确立 FoxM1 为可行靶点。
   - 直接抑制剂阶段：FDI-6（合成小分子，选择性阻断 FoxM1-DNA 结合）、honokiol/thiostrepton/sinomycin A（天然产物，但脱靶效应强）。
   - 局限：天然产物多靶点；FDI-6 对 FoxM1 蛋白水平影响小，机制细节不清。
3. **本文主张的位置**：在已有直接抑制剂基础上，通过 TR-FRET 高通量筛选发现新化合物 CDI（含 pimaric 骨架），并首次报道其抗肿瘤活性；结合对接与 MD 模拟提供分子层面的结合模式解释，同时用 RNA-Seq 验证其对 FoxM1 转录网络的全局影响。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 天然产物抑制剂脱靶效应强 | honokiol、thiostrepton、sinomycin A 为多靶点分子，无法归因于 FoxM1 特异性抑制 | 天然产物结构复杂，与多个蛋白靶点相互作用 | Introduction 第 2 段（作者陈述） |
| FDI-6 对 FoxM1 蛋白水平影响微弱 | FDI-6 处理后 FoxM1 蛋白量几乎不变 | FDI-6 仅阻断 DNA 结合，不促进 FoxM1 降解 | Introduction 第 2 段（作者陈述） |
| 缺乏对 FoxM1 抑制后转录组全局变化的系统分析 | 已有抑制剂研究未做 RNA-Seq 层面的 FoxM1 靶基因富集分析 | 未提供 | 本文通过 RNA-Seq + GSEA 填补此空白（Results 3.5） |
| 小分子与 FoxM1-DBD 结合的分子机制不清晰 | 已有抑制剂缺乏对接/MD 模拟证据 | 未提供 | 本文用 Autodock Vina + GROMACS 提供结合模式（Results 3.6） |

## 06 核心思想

1. **表面方法**：用 TR-FRET 生化筛选发现 CDI 抑制 FoxM1-DBD 与共识 dsDNA 的结合；在乳腺癌细胞系中验证抗增殖/促凋亡效应；用 RNA-Seq 验证 FoxM1 靶基因网络的下调；用对接 + MD 模拟解释结合机制。
2. **核心洞察**：FoxM1 的 DBD 是一个可药靶（druggable）的口袋——小分子可以通过物理占据 DNA 互作界面来阻断 TF–DNA 结合，而不必靶向 FoxM1 的蛋白水平。CDI 的 pimaric 骨架提供了新的化学起点，且其结合位点位于 Wing 区与 helix h3 之间，与 DNA 直接竞争。
3. **可能的普适教训 [Analysis]**：对于 TF–DNA 互作抑制剂发现，**体外定量结合实验（TR-FRET）→ 细胞功能验证 → 转录组靶基因富集分析 → 计算模拟解释机制** 是一条可迁移的完整 pipeline。特别是「用 ChIP-seq 定义的靶基因集做 GSEA 富集」这一验证策略，可推广到其他转录因子靶向药物的评估中。

## 07 方法总览

- **输入**：
  - 化合物库（含 quinopimaric/maleopimaric acid 衍生物，来自 Korea Chemical Bank）
  - 重组 FoxM1-DBD 蛋白（His×6 标签）
  - 生物素标记的共识 dsDNA 寡核苷酸（5′-AAA CAA ACA AAC AAT C-3′ / 5′-GAT TGT TTG TTT GTT T-3′）
  - MDA-MB-231 乳腺癌细胞系
  - FoxM1-DBD 晶体结构（PDB: 3G73）
- **输出**：
  - CDI 的 IC50 值（TR-FRET）
  - 细胞活力（WST-1）、凋亡/坏死比例（流式）
  - FoxM1 及下游靶基因（Cdc25b）的 mRNA/蛋白表达变化
  - RNA-Seq 差异表达基因列表及 GSEA 富集结果
  - CDI-FoxM1-DBD 对接构象与 MD 模拟轨迹
- **模块**：
  1. TR-FRET 结合抑制实验（定量 IC50）
  2. 细胞增殖/凋亡实验（功能验证）
  3. RT-qPCR + Western blot（靶基因验证）
  4. RNA-Seq + GSEA（全局转录组验证）
  5. Autodock Vina 对接 + GROMACS MD 模拟（机制解释）
- **训练**：不适用（无机器学习模型）
- **工具**：Envision 多功能酶标仪（TR-FRET）、NucleoCounter NC-3000（凋亡分析）、Illumina NovaSeq（RNA-Seq）、Autodock Vina v1.1.2（对接）、GROMACS v2020.4（MD）、CHARMM36 力场、CGenFF（配体参数化）
- **反馈回路**：TR-FRET 初筛 → 细胞验证 → 转录组验证 → 计算模拟解释；计算模拟结果反过来支持生化实验的抑制机制
- **假设**：
  - FoxM1-DBD 与共识 dsDNA 的结合可被小分子竞争性抑制
  - CDI 的细胞效应主要归因于 FoxM1–DNA 互作阻断（而非脱靶）
  - 3G73 晶体结构适用于对接模拟

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TR-FRET 结合抑制实验 | 定量检测 CDI 对 FoxM1-DBD–dsDNA 结合的抑制 | 直接验证「阻断互作」这一核心机制 | 输入：FoxM1-DBD、生物素-dsDNA、CDI；输出：IC50 = 4.9 ± 1.5 µM | Results 3.1，图 1 | 若移除，则无法证明 CDI 直接作用于 FoxM1–DNA 互作，细胞效应可能被归因于脱靶 |
| 细胞增殖实验（WST-1） | 评估 CDI 的抗增殖活性 | 验证生化抑制能否转化为细胞表型 | 输入：MDA-MB-231 + CDI (0.1–30 µM)；输出：IC50 = 4.1 ± 0.6 µM | Results 3.2，图 2 | 若移除，则无法建立「互作抑制 → 抗肿瘤」的因果链 |
| 凋亡分析 | 区分凋亡/坏死 | 明确细胞死亡方式 | 输入：CDI 处理细胞 + Annexin V/PI 染色；输出：凋亡比例增加 | Results 3.4，图 4 | 若移除，无法判断 CDI 是诱导凋亡还是坏死 |
| RT-qPCR + Western blot | 验证 FoxM1 及下游靶基因（Cdc25b）表达变化 | 确认转录因子功能被抑制 | 输入：CDI 处理细胞 RNA/蛋白；输出：FoxM1c、Cdc25b 表达下降 | Results 3.3，图 3 | 若移除，则无法证明 FoxM1 通路被特异性抑制 |
| RNA-Seq + GSEA | 全局评估 FoxM1 靶基因网络的变化 | 验证 CDI 的转录组效应与 FoxM1 功能一致 | 输入：CDI vs DMSO 处理细胞 RNA；输出：差异表达基因 + FoxM1 靶基因集负富集 | Results 3.5，图 5D | 若移除，则无法排除 CDI 的效应是脱靶所致 |
| 分子对接（Autodock Vina） | 预测 CDI 在 FoxM1-DBD 上的结合位点 | 提供分子层面的结合模式假设 | 输入：3G73 结构 + CDI 3D 结构；输出：结合构象（Wing 区与 h3 之间） | Results 3.6，图 7A-B | 若移除，则缺乏 CDI 结合位点的结构证据 |
| MD 模拟（GROMACS） | 验证对接构象的稳定性与结合自由能 | 确认 CDI 结合不是对接假象 | 输入：对接复合物；输出：100 ns 轨迹、结合能 −146.45 kJ/mol | Results 3.6，图 7C-E | 若移除，则结合模式的可靠性降低 |

## 09 关键公式符号

本文未提供明确的数学公式。以下为方法中隐含的定量关系：

- **IC50 计算**：TR-FRET 信号抑制率 vs. CDI 浓度，通过非线性回归（PRISM）拟合四参数 logistic 曲线，IC50 为抑制 50% 信号时的浓度。符号：IC50（半数抑制浓度）。
- **结合自由能（MD 模拟）**：文中报告 CDI 结合能从 −80.04 kJ/mol（初始位点）变为 −146.45 kJ/mol（移动后位点），但未给出具体计算公式。符号：ΔG（结合自由能）。
- **差异表达基因筛选阈值**：|log2FC| > 2 且 p < 0.05（DESeq2 分析）。符号：log2FC（log2 倍数变化）。

## 10 实验设计与证据链

**数据集/群体**：
- 生化实验：重组 FoxM1-DBD 蛋白 + 共识 dsDNA 寡核苷酸
- 细胞实验：MDA-MB-231 人乳腺癌细胞系（购自 Korean Cell Line Bank）
- RNA-Seq：CDI (8 µM, 6 h) vs DMSO 对照，三重复
- 计算模拟：PDB 3G73（FoxM1-DBD 晶体结构）

**指标**：IC50（TR-FRET 和细胞增殖）、凋亡/坏死比例、mRNA/蛋白表达水平、log2FC、GSEA 富集分数、对接能量、MD 结合能

**基线/对照**：DMSO 处理组（细胞实验）、FDI-6（TR-FRET 参考化合物）、未处理对照（RNA-Seq）

**预算/资源**：未提供

**骨干/仪器**：Envision 多功能酶标仪、NucleoCounter NC-3000、Illumina NovaSeq

**oracle 输入**：不适用（无监督学习或预测模型）

**评测协议**：TR-FRET 信号定量、WST-1 活力测定、Annexin V/PI 流式、RT-qPCR（4 次独立实验）、Western blot、DESeq2 差异表达、GSEA 富集分析

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| TR-FRET 结合抑制 | CDI 直接抑制 FoxM1-DBD–DNA 互作 | CDI 浓度梯度 vs. FDI-6 参考 | IC50 = 4.9 ± 1.5 µM | CDI 是 FoxM1-DNA 互作的直接抑制剂 | 未证明是竞争性还是别构抑制 | Results 3.1，图 1 |
| WST-1 细胞活力 | CDI 抑制 MDA-MB-231 增殖 | CDI (0.1–30 µM) vs. DMSO | IC50 = 4.1 ± 0.6 µM，优于 FDI-6（28.6 µM） | CDI 具有抗增殖活性 | 未在正常细胞中验证选择性 | Results 3.2，图 2 |
| 凋亡分析 | CDI 诱导凋亡 | CDI (2/4/8 µM) vs. DMSO | 晚期凋亡比例从 2.0% 升至 18.2%（8 µM） | CDI 诱导凋亡 | 未做 caspase 活性或线粒体通路分析 | Results 3.4，图 4 |
| RT-qPCR/Western | CDI 下调 FoxM1 及下游靶基因 | CDI 浓度梯度 vs. DMSO | FoxM1c、Cdc25b mRNA/蛋白下降 | CDI 抑制 FoxM1 转录功能 | 未检测其他 FoxM1 靶基因 | Results 3.3，图 3 |
| RNA-Seq + GSEA | CDI 全局下调 FoxM1 靶基因 | CDI (8 µM, 6 h) vs. DMSO | 260 上调、17 下调；FoxM1 靶基因集负富集 | CDI 的转录组效应与 FoxM1 抑制一致 | 未做 ChIP-seq 验证 CDI 对 FoxM1 占据的影响 | Results 3.5，图 5 |
| 分子对接 | CDI 结合于 FoxM1-DBD 的 DNA 互作位点 | 3G73 结构 + CDI | 结合于 Wing 区与 h3 之间，−8.3 kcal/mol | CDI 可能物理阻断 DNA 结合 | 对接能量未与实验 IC50 直接关联 | Results 3.6，图 7A-B |
| MD 模拟 | CDI 结合构象稳定 | 100 ns 模拟 | 结合能 −146.45 kJ/mol，移动至 h3 对侧 | CDI 在动态条件下稳定结合 | 未做自由能微扰或 MM-PBSA 验证 | Results 3.6，图 7C-E |

## 11 结论正确解读

- **任务范围**：本文仅证明 CDI 在体外（生化）和细胞水平（MDA-MB-231）抑制 FoxM1–DNA 互作及其功能后果；未涉及动物模型、其他癌症类型或正常组织毒性。
- **oracle/真值输入**：FoxM1 靶基因集来自已发表的 ChIP-seq 数据（文献 37），非本文独立鉴定。
- **端到端状态**：从筛选到机制解释的完整 pipeline 已走通，但**未达到临床前候选药物阶段**——无 PK/PD、无动物药效、无毒性数据。
- **算力成本**：MD 模拟 100 ns，未报告具体计算资源。
- **历史数据依赖**：FoxM1 靶基因集依赖 ChIP-seq 数据库；化合物库来自 Korea Chemical Bank。
- **模型依赖**：对接结果依赖 3G73 晶体结构（可能不代表溶液中的全部构象）；MD 结果依赖 CHARMM36 力场和 CGenFF 参数化。
- **最难情形**：CDI 对 FoxM1 的选择性（相对其他 Forkhead 家族成员如 FoxO3）未做直接结合实验验证；仅通过 FoxO 靶基因未下调间接推断。
- **群体/领域边界**：结论仅适用于 MDA-MB-231 三阴性乳腺癌细胞系；FoxM1 高表达的其他癌症类型未验证。
- **不确定性**：IC50 值有标准差（4.9 ± 1.5 µM），但未报告重复次数；MD 结合能变化（−80 到 −146 kJ/mol）的统计显著性未评估。
- **有边界的复述**：CDI 在体外以微摩尔浓度抑制 FoxM1-DBD 与共识 DNA 的结合，在 MDA-MB-231 细胞中抑制增殖、诱导凋亡并下调 FoxM1 靶基因；计算模拟提示其结合于 DBD 的 DNA 互作界面附近。这些结论限于该细胞系和体外条件，不构成对 CDI 临床疗效的证明。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 仅细胞系验证 | 所有实验在乳腺癌细胞系中完成 | 需在动物模型中验证 | Discussion 最后一段 |
| 未覆盖其他癌症类型 | 未测试 CDI 对其他 FoxM1 高表达癌症的效果 | 需在其他癌症中测试 | Discussion 最后一段 |
| 未做选择性验证 | 未直接证明 CDI 对 FoxM1 相对其他 Fox 蛋白的选择性 | 未提供 | Discussion 第 2 段（间接通过 FoxO 靶基因未下调推断） |

> 注：作者在 Discussion 中仅明确承认了「动物模型缺失」这一局限。其他约束（如选择性、脱靶）为间接提及，非正式局限声明。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| CDI 的细胞效应可能部分来自脱靶 | 作者未做 CDI 的全基因组靶点谱（如 pull-down + proteomics 或 CETSA），也未在 FoxM1 敲低细胞中验证 CDI 效应是否消失 | 若脱靶贡献大，则「阻断 FoxM1-DNA」的核心机制 claim 被削弱 | 在 FoxM1 敲低/敲除的 MDA-MB-231 中重复 CDI 处理，比较表型差异；或做药物亲和层析 | Results 3.2–3.5 均未包含遗传学对照 |
| 对接/MD 模拟缺乏实验验证 | 作者未用突变实验（如将 DBD 关键残基突变后检测 CDI 结合）验证预测的结合位点 | 计算模拟可能给出假阳性结合模式 | 对预测的关键残基（如 R286、R297）做点突变，检测 CDI 结合与抑制活性变化 | Results 3.6 仅报告计算预测 |
| RNA-Seq 差异基因数量少（17 下调） | 8 µM、6 h 的处理条件可能不足以捕捉 FoxM1 的完整转录组效应；或 CDI 的抑制效率有限 | 若转录组效应弱，则「CDI 有效抑制 FoxM1 功能」的结论需谨慎 | 延长处理时间、提高浓度，或做时间梯度实验 | Results 3.5 报告 17 个下调基因 |
| 未报告 CDI 的物理化学性质 | 未提供溶解度、渗透性、代谢稳定性等数据 | 影响 CDI 作为先导化合物的可开发性评估 | 补充 ADME 相关实验 | 全文未提及 |
| 未与已知 FoxM1 抑制剂（如 FDI-6）做直接头对头比较 | 仅报告了 IC50 数值差异，未在相同实验条件下比较两者的结合抑制效率和细胞活性 | 无法判断 CDI 是否真正优于现有工具 | 在相同 assay 中平行比较 CDI 与 FDI-6 的 IC50、细胞活性、选择性 | Results 3.1–3.2 分别报告，未做同批比较 |

## 14 学到什么

> **Agent 提炼的知识候选**

1. **TR-FRET 作为 TF–DNA 互作定量平台**：本文用 TR-FRET 直接定量小分子对 TF–DNA 结合的抑制，无需细胞裂解或凝胶迁移实验。可迁移到课题中：若研究其他 TF（如 p53、MYC）的 DNA 结合抑制剂，可构建「生物素-dsDNA + His 标签 TF-DBD + 抗 His 铕穴状化合物 + 链霉亲和素-XL665」的四元复合物体系，实现高通量筛选。
2. **「ChIP-seq 靶基因集 + GSEA」验证 TF 功能抑制**：作者用已发表的 FoxM1 ChIP-seq 数据定义靶基因集，再用 CDI 处理后的 RNA-Seq 数据做 GSEA，验证「TF 功能被抑制」这一 claim。可迁移到课题：任何 TF 抑制剂的转录组验证都可复用此策略，前提是目标 TF 的 ChIP-seq 数据可获取。
3. **对接 + MD 的「两阶段」结合机制解释**：先用 Autodock Vina 快速筛选结合位点，再用 GROMACS 做 100 ns MD 验证稳定性并计算结合能。可迁移到课题：对于 TF–DNA 互作的小分子阻断机制研究，此 pipeline 成本可控且能提供动态信息（如结合位点迁移、氢键网络变化）。
4. **「Wing 区 + helix h3」作为 TF–DNA 互作界面的可药靶口袋**：FoxM1-DBD 的 DNA 结合界面包含 Wing 区和 helix h3，小分子可结合于此。可迁移到课题：其他 Forkhead 家族成员（如 FOXO、FOXA）的 DBD 可能也有类似的可药靶口袋，值得系统分析。
5. **「先体外互作、再细胞功能、后转录组」的三级验证逻辑**：本文的验证顺序（生化结合 → 细胞增殖/凋亡 → 转录组）逻辑清晰，可迁移到课题中作为 TF 抑制剂验证的标准流程。
6. **选择性验证的间接策略**：作者通过比较 FoxM1 与 FoxO 靶基因的表达变化来间接推断选择性。可迁移到课题：当直接结合实验不可行时，可用「家族成员靶基因集差异富集」作为选择性的间接证据，但需注意其局限性。

## 15 与已有知识连接

- **FoxM1 生物学**：本文与已发表的 FoxM1 在细胞周期调控中的作用（cyclin B、Cdc25b、Aurora B 等靶基因）一致，可连接至 Laoukili et al. (2007) 等综述。
- **TF–DNA 互作抑制剂领域**：本文的 FDI-6 参考化合物来自 Gormally et al. (2014) 的研究；可连接至更广泛的「转录因子直接抑制剂」领域（如 p53-MDM2、MYC-MAX 抑制剂）。
- **Forkhead 家族 DBD 结构**：PDB 3G73 是 FoxM1-DBD 与 DNA 的共晶结构，可连接至 Forkhead 家族 DBD 的保守结构研究（winged helix 结构域）。
- **计算模拟方法**：Autodock Vina + GROMACS 的组合是药物发现中常见的「对接 + MD」流程，可连接至 Trott & Olson (2010) 和 Abraham et al. (2015) 的方法学文献。
- **RNA-Seq + GSEA 验证策略**：可连接至 Subramanian et al. (2005) 的 GSEA 方法学，以及 ChIP-seq 定义的靶基因集用于药物机制验证的范例。
- **[Analysis] 候选方向**：本文未做但可连接的包括：CDI 与 FoxM1-DBD 的共晶结构解析（可连接至结构生物学方法）、CDI 的泛 Forkhead 家族选择性谱（可连接至 FOXO/FOXA 抑制剂研究）、以及基于 MD 的自由能微扰（FEP）计算来优化 CDI 衍生物。

## 16 研究想法

> **Agent 生成的研究候选**

1. **候选名称**：基于 MD 的 FoxM1-DBD 可药靶口袋系统分析
   - **来源局限/观察**：本文仅对 CDI 一个化合物做了对接/MD，未系统分析 FoxM1-DBD 表面的可药靶口袋。
   - **核心假设**：FoxM1-DBD 的 DNA 结合界面（Wing 区 + h3）存在多个可药靶亚口袋，不同小分子可能结合于不同亚口袋。
   - **增量**：对 3G73 结构做全表面可药靶性分析（如 FTMap、SiteMap），结合 MD 的构象采样，绘制 FoxM1-DBD 的可药靶口袋图谱。
   - **初步方法**：对 3G73 做 1 µs 级 MD 模拟，提取代表性构象，用 FTMap 或 SiteMap 识别可药靶口袋，与已知抑制剂（CDI、FDI-6）的结合位点比对。
   - **验证方式**：对预测的新口袋设计突变体，用 TR-FRET 检测突变对已知抑制剂活性的影响。
   - **创新状态**：unverified

2. **候选名称**：CDI 的泛 Forkhead 家族选择性谱测定
   - **来源局限/观察**：作者仅通过 FoxO 靶基因未下调间接推断 CDI 对 FoxM1 的选择性，未做直接结合实验。
   - **核心假设**：CDI 对 FoxM1-DBD 的选择性高于其他 Forkhead 家族成员（FOXO1/3、FOXA1/2、FOXC1 等）。
   - **增量**：提供 CDI 的定量选择性数据，为后续结构优化提供依据。
   - **初步方法**：表达纯化多个 Forkhead 家族成员的 DBD 蛋白，用 TR-FRET 或 MST（微量热泳动）测定 CDI 对各 DBD-DNA 结合的 IC50。
   - **验证方式**：若 CDI 对某些家族成员也有抑制，则需重新评估其机制归因。
   - **创新状态**：unverified

3. **候选名称**：CDI 处理下 FoxM1 染色质占据变化的 ChIP-seq 验证
   - **来源局限/观察**：本文用 RNA-Seq 间接推断 FoxM1 功能抑制，但未直接检测 FoxM1 在染色质上的占据变化。
   - **核心假设**：CDI 处理会减少 FoxM1 在全基因组范围内的染色质结合，且减少程度与靶基因下调相关。
   - **增量**：提供「小分子阻断 TF-DNA 互作」的直接染色质证据，弥补 RNA-Seq 间接推断的不足。
   - **初步方法**：CDI 处理 MDA-MB-231 细胞后做 FoxM1 ChIP-seq，与 DMSO 对照比较 FoxM1 结合峰的变化。
   - **验证方式**：结合 RNA-Seq 数据，检验「染色质结合减少的基因」与「表达下调的基因」的重叠度。
   - **创新状态**：unverified

4. **候选名称**：基于 MD 的 CDI 衍生物设计与自由能微扰优化
   - **来源局限/观察**：本文 MD 显示 CDI 结合能约 −146 kJ/mol，但未做结构-活性关系（SAR）优化。
   - **核心假设**：对 CDI 的 pimaric 骨架进行系统修饰，可提高其与 FoxM1-DBD 的结合亲和力和选择性。
   - **增量**：提供 CDI 的 SAR 图谱和优化先导物。
   - **初步方法**：基于 MD 结合构象，用 FEP 计算预测系列 CDI 衍生物的结合自由能变化，合成高排名化合物并用 TR-FRET 验证。
   - **验证方式**：实验 IC50 与 FEP 预测值的相关性评估。
   - **创新状态**：unverified

5. **候选名称**：TF–DNA 互作抑制剂的通用 TR-FRET 筛选平台构建
   - **来源局限/观察**：本文的 TR-FRET 体系针对 FoxM1 定制，但方法可推广。
   - **核心假设**：同一 TR-FRET 平台可适配多个 TF-DBD 靶点，实现「一个平台、多靶点」的抑制剂筛选。
   - **增量**：为课题方向提供可复用的筛选基础设施。
   - **初步方法**：构建多个 TF-DBD 的表达载体和对应共识 dsDNA 探针，验证 TR-FRET 信号动态范围和 Z' 因子。
   - **验证方式**：用已知抑制剂（如 FDI-6 对 FoxM1）验证平台灵敏度，再用平台筛选小规模化合物库。
   - **创新状态**：unverified