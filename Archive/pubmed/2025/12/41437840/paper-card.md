## 01 基本信息

- **标题**：Structural bases of signal generation and transduction by the SPS amino acid sensor of *Saccharomyces cerevisiae*
- **作者与单位**：Scharff-Poulsen, Peter; Kielland-Brandt, Morten C（单位未在摘要中提供）
- **期刊/预印本平台**：G3 (Bethesda, Md.)
- **年份**：2025-12-24
- **论文类型**：研究论文（计算建模 + 突变分析）
- **领域**：酵母氨基酸感知信号转导；膜蛋白结构预测；蛋白质-配体互作
- **关键词**：SPS sensor, Ssy1, amino acid sensing, AlphaFold, Phyre2, signal transduction, yeast
- **DOI/arXiv 号**：10.1093/g3journal/jkaf312
- **代码**：未提供
- **数据**：蛋白质序列来自 UniProt；结构来自 PDB 和 AlphaFold 数据库（文中声明）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文以酵母 SPS 氨基酸传感器（Ssy1-Ptr3-Ssy5 复合物）为对象，利用 AlphaFold、Phyre2 和 AlphaFold 3 进行结构预测与互作界面分析，属于「蛋白质-配体互作 × 结构预测/AI 建模」方向。对 TF–DNA 互作课题的可迁移点在于：**利用 AI 结构预测（AlphaFold/AlphaFold 3）解析膜蛋白/多亚基复合物的构象状态与互作界面**，以及**将组成型激活突变映射到 3D 模型上推断信号传导构象变化**的方法论。

## 02 一句话总结

本文通过将 7 个组成型激活/超敏 SSY1 突变映射到基于 Phyre2 和 AlphaFold 构建的 Ssy1 同源模型中，提出 Ssy1 的信号传导构象为「内向封闭（inward-facing occluded）」状态，并利用 AlphaFold 3 预测 SPS 复合物（Ssy1-Ptr3-Ssy5）及 PP2A 的互作界面，构建了从氨基酸结合到转录因子激活的早期信号传导步骤模型。

## 03 研究问题

- **具体问题**：Ssy1 作为从氨基酸转运蛋白进化而来的受体，其信号传导的构象基础是什么？配体结合如何触发胞内信号级联？
- **为什么重要**：SPS 传感器是真核细胞感知胞外氨基酸浓度的原型系统，理解其机制有助于揭示「转运蛋白→受体」的进化转变，以及膜蛋白构象变化如何转化为胞内信号。
- **现有方法为何不足**：Ssy1 尚无实验解析的 3D 结构；传统突变分析缺乏结构上下文；单一构象模型无法解释组成型激活突变的分布模式。
- **Can 问题**：Can the signaling conformation of Ssy1 be identified by mapping gain-of-function mutations onto homology models, and can AlphaFold 3 predict the architecture of the SPS signaling complex?

## 04 背景与发展脉络

*（标注：以下脉络为「经外部核验」——基于摘要中引用的文献及领域公认发展）*

1. **SPS 传感器发现与遗传学鉴定（1987–2001）**：从亮氨酸感知的遗传筛选（Island et al. 1987）到 SPS 复合物三组分鉴定（Forsberg and Ljungdahl 2001）。代表性方法：酵母遗传学、突变体筛选。局限：缺乏结构信息。
2. **Ssy1 作为转运蛋白样受体的概念建立（1998–2006）**：Ssy1 序列与氨基酸转运蛋白同源但不具转运功能（Didion et al. 1998; Jørgensen et al. 1998; Iraqui et al. 1999）。Wu et al. (2006) 提出双构象模型（外向开放 vs 内向开放）。局限：无 3D 结构验证。
3. **同源建模与结构预测时代（2018–2025）**：Scharff-Poulsen et al. (2018) 对葡萄糖传感器 Rgt2 的类似分析；本文利用 Phyre2 和 AlphaFold 对 Ssy1 建模，并用 AlphaFold 3 预测复合物结构。局限：计算模型需实验验证。
4. **本文主张的位置**：在双构象模型基础上，提出「内向封闭」为信号传导构象，并首次给出 SPS 复合物与 PP2A 的互作模型。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Ssy1 缺乏实验 3D 结构 | 无法直接观察配体结合与构象变化 | 膜蛋白结晶困难；Ssy1 表达量低 | 摘要：「Experimental determination of a 3D structure of Ssy1 has not been achieved」 |
| 组成型激活突变缺乏结构解释 | 7 个突变分散在序列各处，难以从一维序列理解 | 突变影响的是构象平衡而非单一功能位点 | 摘要：「mapped 7 constitutively signaling and hyper-responsive SSY1 mutations onto AlphaFold and Phyre2-based 3D models」 |
| 信号传导构象不确定 | 原模型（Wu et al. 2006）认为外向开放为信号态，与突变数据不符 | 转运蛋白存在多种中间构象（occluded） | 摘要：「The predictions suggest a model in which an occluded, inward-facing conformation of Ssy1 leads to signaling」 |
| Ptr3 磷酸化机制不明 | 磷酸化位点未知，去磷酸化调控不清 | Ptr3 为无序蛋白，难以结晶 | 摘要：「We found Yck phosphorylation motifs as well as binding motifs for regulatory subunit Rts1 of PP2A in both Ptr3 and Ssy5」 |
| 复合物组装方式未知 | Ssy1-Ptr3-Ssy5 如何组装、PP2A 如何结合不清楚 | 多亚基膜蛋白复合物结构解析困难 | 摘要：「AlphaFold 3 modeling suggests that conserved sequence boxes in the N-terminal cytoplasmic domain of Ssy1 serve as interaction faces」 |

## 06 核心思想

### 1) 表面方法
- 用 Phyre2 和 AlphaFold 构建 Ssy1 的 3D 同源模型（基于 APC 家族转运蛋白模板）
- 将 7 个组成型激活/超敏 SSY1 突变映射到模型上，分析其空间位置与潜在结构效应
- 用 AlphaFold 3 预测 SPS 复合物（Ssy1-Ptr3-Ssy5）及 Ssy1 与 PP2A 的互作
- 用 Metapredict 预测无序区域
- 结合酵母双杂交数据与已知磷酸化/去磷酸化调控，构建信号传导模型

### 2) 核心洞察
- **信号构象是「内向封闭」而非「外向开放」**：突变分布在胞内/胞外两侧，提示信号态是配体结合后、转运循环中间的封闭构象
- **C 端「门闩」（latch）机制**：TM12 中的铰链（hinge）配合 C 端 latch 的释放/结合，控制胞内门控
- **Ptr3 的磷酸化位点位于无序区域**，与 Ssy1 的 C 端 latch 空间邻近，提示磷酸化调控 latch 释放
- **PP2A 通过 Rts1 亚基的 LxxIxE 基序结合 Ssy5**，与已知的 PP2A-B56 互作模式一致

### 3) 可能的普适教训 [Analysis]
- **AI 结构预测的价值不仅在于「折叠」，更在于「构象状态注释」**：将功能突变映射到预测结构上，可以推断蛋白的功能构象，这一策略可直接迁移到 TF–DNA 互作研究（如将组成型激活 TF 突变映射到 DNA 结合域模型上）
- **无序区域（IDR）在信号传导中可能充当「可调控的互作平台」**：本文中 Ptr3 和 Ssy5 的 IDR 是磷酸化调控的关键，TF 的 IDR 同样常参与相分离和转录调控
- **多亚基复合物的 AlphaFold 3 预测需要结合生化验证**：作者对低置信度区域持谨慎态度，这种「计算预测 + 实验验证」的循环是结构生物学与 AI 结合的正确范式

## 07 方法总览

- **输入**：Ssy1、Ptr3、Ssy5、Yck1/2、PP2A 亚基（Rts1、Pph21、Tpd3）的氨基酸序列；7 个 SSY1 激活突变位点；已知的酵母双杂交互作数据
- **输出**：Ssy1 的 3D 构象模型（外向开放、封闭、内向开放）；SPS 复合物互作模型；信号传导步骤模型
- **模块**：
  1. 同源建模（Phyre2，基于 APC 家族转运蛋白模板）
  2. AlphaFold 单链结构预测（AlphaFold DB）
  3. AlphaFold 3 多亚基复合物预测
  4. 无序区域预测（Metapredict）
  5. 突变映射与结构分析
  6. 序列保守性分析（多序列比对）
- **训练**：不适用（使用预训练模型）
- **工具**：Phyre2、AlphaFold/AlphaFold 3、Metapredict、Clustal Omega、ESPript、PyMOL
- **反馈回路**：无（计算预测为主，实验验证为未来方向）
- **文字流程**：序列比对 → 同源建模/AlphaFold 预测 Ssy1 构象 → 突变映射到模型 → 分析突变对构象平衡的影响 → AlphaFold 3 预测复合物互作 → 结合已知生化数据构建信号传导模型

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Phyre2 同源建模 | 生成 Ssy1 的 3D 模型 | Ssy1 无实验结构；同源模板可提供折叠框架 | 输入：Ssy1 序列；输出：3D 模型 | 摘要：「Phyre2-based 3D models of Ssy1」 | 预期影响：失去与转运蛋白构象状态的对应关系 [预期效应] |
| AlphaFold 单链预测 | 预测 Ssy1 及 N 端结构域结构 | 补充同源建模无法覆盖的区域 | 输入：序列；输出：pLDDT 注释的结构 | 摘要：「AlphaFold and Phyre2-based 3D models」 | 预期影响：N 端结构域和 IDR 的结构信息缺失 [预期效应] |
| AlphaFold 3 复合物预测 | 预测 Ssy1-Ptr3-Ssy5、Ssy1-Yck、Ssy5-PP2A 互作 | 揭示信号传导中的蛋白-蛋白互作界面 | 输入：多链序列；输出：复合物模型 + ipTM/pTM | 摘要：「AlphaFold 3 modeling suggests that conserved sequence boxes...」 | 预期影响：无法定位互作界面 [预期效应] |
| 突变映射分析 | 将 7 个激活突变定位到 3D 模型 | 推断突变如何影响构象平衡 | 输入：突变位点 + 3D 模型；输出：空间聚类/互作破坏分析 | 摘要：「mapped 7 constitutively signaling...mutations onto...3D models」 | 预期影响：无法推断信号构象 [预期效应] |
| Metapredict 无序预测 | 预测 IDR 区域 | IDR 在信号传导中可能起关键作用 | 输入：序列；输出：无序打分 | 摘要：「Metapredict analysis of the Ssy1 sequence identified IDRs」 | 预期影响：无法解释 IDR 介导的互作 [预期效应] |
| 序列保守性分析 | 识别功能关键残基 | 保守残基提示功能重要性 | 输入：多序列比对；输出：保守性打分 | 摘要：「conserved sequence boxes」 | 预期影响：无法区分功能关键 vs 非关键残基 [预期效应] |

## 09 关键公式符号

不适用。本文为结构生物学/计算建模研究，未使用定量公式。核心「符号」为结构生物学概念：

- **ipTM**（interface predicted Template Modeling score）：衡量复合物界面预测置信度，>0.8 为高置信
- **pTM**（predicted Template Modeling score）：衡量整体结构预测置信度，>0.5 为有意义
- **pLDDT**（predicted Local Distance Difference Test）：逐残基置信度打分，70–90 为自信，>90 为非常自信
- **EC50**：半数有效浓度，用于量化突变体的超敏表型（如 T382K 降低 EC50）

## 10 实验设计与证据链

**数据集/群体**：
- 7 个 SSY1 组成型激活/超敏突变体（来自 Poulsen et al. 2008 的遗传筛选）
- 37 个 Ssy1 直系同源序列（真菌）
- 15 个酿酒酵母 YAT 家族转运蛋白序列
- 18 个 Ssy1 酿酒酵母科直系同源序列
- 32 个 Ptr3 直系同源序列
- 18 个 Ssy5 直系同源序列

**指标**：EC50（氨基酸浓度）、组成型信号水平（Stp1 加工量）、ipTM/pTM（AlphaFold 3 置信度）、pLDDT（逐残基置信度）

**评测协议**：计算预测为主，无 wet-lab 实验验证

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| 7 个 SSY1 突变映射到 AlphaFold/Phyre2 模型 | 突变位点位于功能关键区域 | 突变位点 vs 保守残基/互作界面 | 突变分布在胞外/胞内两侧，无一在配体结合位点 | 突变影响构象平衡而非配体结合 | 无法确定具体构象变化方向 | Results 图 1 |
| T382K/V694F 空间分析 | 突变通过「楔入」TM3-TM4 促进胞外门关闭 | 突变残基 vs 邻近残基空间距离 | 两个突变残基指向同一空间区域 | 支持「楔入」机制 | 无法排除其他机制 | Results 图 3 |
| F333S 突变分析 | 破坏 F333-F521 pi-pi 互作 | 突变 vs 野生型互作网络 | F333-F521 在模型中空间邻近 | 支持 pi-pi 互作破坏假说 | 无法直接验证 pi-pi 互作 | Results 图 3 |
| AlphaFold 3 SPS 复合物预测 | Ssy1 N 端与 Ptr3、Ssy5 的互作界面 | 复合物模型 vs 已知双杂交数据 | 预测互作界面与双杂交数据一致 | 支持复合物模型 | ipTM 值未全部 >0.8 | Supplementary 图 22–24 |
| AlphaFold 3 Ssy5-PP2A 预测 | Ssy5 的 LxxIxE 基序结合 Rts1 | 预测模型 vs 已知 PP2A-B56 互作模式 | 互作模式与已知结构一致 | 支持 PP2A 结合模型 | 整体置信度低（ipTM=0.58） | Results 图 6 |
| Ptr3 磷酸化位点分析 | S511-S521 为 Yck 靶点 | 磷酸化基序 vs 保守性 | 基序保守且位于 IDR | 支持 Yck 磷酸化假说 | 无实验磷酸化数据 | Results 图 5 |
| T639I 突变分析 | 影响 TM1 loop 构象 | 突变 vs 野生型构象 | T639I 与 TM1 loop 残基 V297 冲突 | 支持构象约束假说 | 无法排除配体亲和力影响 | Results 图 10 |

## 11 结论正确解读

- **任务范围**：本文是**纯计算研究**，所有结论均为「基于结构预测的假说」，未经 wet-lab 验证。作者明确声明「Results presented here have been obtained by computational modeling」。
- **oracle/真值输入**：无实验结构作为真值；使用同源模板（APC 家族转运蛋白）和 AlphaFold 预测。
- **端到端状态**：非端到端。从序列到结构到信号模型的完整链条中，每一步都有不确定性累积。
- **算力成本**：未提供。AlphaFold 3 使用服务器版，成本由服务器承担。
- **历史数据依赖**：依赖 Poulsen et al. (2008) 的突变体表型数据、酵母双杂交互作数据、已知的 PP2A-B56 互作结构。
- **模型依赖**：强依赖 AlphaFold/AlphaFold 3 的预测准确性。作者对低置信度区域（如 PP2A-Ssy5 整体模型 ipTM=0.58）持谨慎态度。
- **最难情形**：Ssy1 的 N 端结构域和 IDR 区域预测置信度低；Ptr3 的 IDR 无法建模；PP2A 复合物整体预测置信度不足。
- **群体/领域边界**：结论仅适用于 *S. cerevisiae* SPS 传感器；跨物种推广需谨慎（尽管作者做了直系同源分析）。
- **不确定性**：所有结构均为预测模型，构象状态分配（如「内向封闭」为信号态）是推断而非直接观察。

**有边界的复述**：基于计算建模，本文提出 Ssy1 的信号传导构象为「内向封闭」状态，C 端 latch 的释放是关键步骤，Ptr3 的磷酸化由 Yck 介导、受 PP2A-Rts1 拮抗，但这些结论需要在实验上验证。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 计算模型未经实验验证 | 所有结构预测和互作模型均为计算推断 | 建议 wet-lab 实验验证，如 cryo-EM、定点突变 | 摘要：「Results presented here have been obtained by computational modeling...it will be of obvious interest to test many of the suggestions and possibilities by wet-lab experiments」 |
| AlphaFold 3 整体复合物预测置信度低 | Ssy1-Ptr3-Ssy5 三聚体 ipTM=0.46，PP2A-Ssy5 ipTM=0.58 | 使用截短/结构化区域进行预测以提高置信度 | Results 图 8、Supplementary 图 25 |
| IDR 区域无法建模 | Ptr3 的 G112-D263 和 Ssy5 的 N 端 1-164 为无序区域 | 使用 Metapredict 等工具预测 IDR 特征 | Supplementary 图 11、15 |
| 缺乏磷酸化实验数据 | Yck 磷酸化位点和 PP2A 去磷酸化位点为预测 | 建议进行磷酸化位点突变和质谱分析 | Results 图 5、6 |
| 突变体表型数据来自早期研究 | 7 个 SSY1 突变体的表型数据来自 Poulsen et al. (2008) | 未明确说明 | Results 图 1 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 「内向封闭为信号态」的结论基于 7 个突变的间接推断 | 突变可能通过改变蛋白稳定性/表达量而非构象平衡来影响信号；「内向封闭」可能只是多种中间构象之一 | 这是全文核心结论，若错误则整个信号模型需修正 | 用 cryo-EM 解析 Ssy1 在有无配体、有无突变条件下的结构；用 MD 模拟比较各构象的稳定性 | 摘要：「The predictions suggest a model in which an occluded, inward-facing conformation of Ssy1 leads to signaling」 |
| AlphaFold 3 预测的互作界面缺乏实验验证 | AlphaFold 3 对膜蛋白复合物的预测准确性尚未系统验证；预测的互作界面可能是假阳性 | 复合物模型是信号传导机制的基础 | 用交联质谱（cross-linking MS）、共免疫沉淀、突变-互作实验验证 | 摘要：「AlphaFold 3 modeling suggests...」 |
| 磷酸化位点预测基于序列基序，缺乏实验证据 | Yck 基序预测可能漏掉非经典位点；PP2A 结合位点预测可能不准确 | 磷酸化是信号传导的核心调控步骤 | 磷酸化蛋白质组学、体外激酶实验、磷酸化位点突变 | 摘要：「We found Yck phosphorylation motifs...」 |
| 同源建模依赖 APC 家族模板，可能无法捕捉 Ssy1 特有构象 | Ssy1 已失去转运功能，其构象动态可能不同于功能性转运蛋白 | 模板偏差可能导致系统性构象误判 | 用无模板的从头预测（如 RoseTTAFold）交叉验证；MD 模拟验证构象稳定性 | 摘要：「based on recently reported structures of amino acid transporters」 |
| 7 个突变均为组成型激活/超敏，缺乏失活突变对照 | 仅分析激活突变可能高估特定构象的重要性；失活突变可能指向不同机制 | 完整的突变-结构关系需要双向验证 | 分析失活突变在模型中的位置；构建新的突变体验证预测 | 摘要：「mapped 7 constitutively signaling and hyper-responsive SSY1 mutations」 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **「突变映射到 AI 预测结构」的方法论**：将功能获得性突变映射到 AlphaFold 预测的 3D 模型上，通过突变的空间聚类和互作破坏分析推断蛋白的功能构象。**迁移到 TF–DNA 互作**：将组成型激活或失活的 TF 突变映射到 AlphaFold 预测的 TF 结构上，可推断 DNA 结合域与调控域的构象耦合方式。

2. **「构象状态注释」而非仅「折叠预测」**：本文展示了 AI 结构预测不仅用于获得静态结构，更用于注释蛋白在信号传导中的构象状态（外向开放 vs 封闭 vs 内向开放）。**迁移**：TF 在结合 DNA 前后、招募共激活因子/共抑制因子前后存在构象变化，可用类似方法注释。

3. **IDR 作为信号传导平台**：Ptr3 和 Ssy5 的 IDR 区域是磷酸化调控的关键，且 IDR 与有序结构域的互作（如 Ssy5 的 LxxIxE 基序结合 PP2A）是信号传导的核心。**迁移**：TF 的 IDR（如激活域 AD）常介导相分离和共激活因子招募，可借鉴本文的「IDR 预测 + 互作基序分析」策略。

4. **AlphaFold 3 多亚基预测的置信度评估**：作者对 ipTM<0.6 的预测持谨慎态度，仅采用局部高置信度界面。**迁移**：预测 TF-共激活因子或 TF-DNA 复合物时，应区分整体置信度与局部界面置信度，避免过度解读。

5. **「门闩-铰链」（latch-hinge）机制**：TM12 的铰链配合 C 端 latch 控制胞内门控，这一「机械」概念可能适用于 TF 的 DNA 结合域与调控域之间的构象传递。

6. **进化视角：转运蛋白→受体的功能转变**：Ssy1 从转运蛋白进化为受体，保留了配体结合能力但失去了转运功能。**迁移**：理解 TF 如何从祖先蛋白进化出新的 DNA 结合特异性，可借鉴这种「功能重编程」的进化视角。

## 15 与已有知识连接

- **SPS 传感器领域**：本文直接建立在 Wu et al. (2006) 的双构象模型之上，并修正了「外向开放为信号态」的旧假设。与 Van Zeebroeck et al. (2009) 对 Gap1 转受体（transceptor）的研究一致——Gap1 的信号传导构象也被认为是封闭态。
- **APC 家族转运蛋白结构**：本文使用的模板包括 LeuT（Yamashita et al. 2005）、AdiC（Ilgü et al. 2021）、LAT1/LAT2（Lee et al. 2019; Yan et al. 2019, 2020）等已解析结构。这些结构为 Ssy1 建模提供了构象模板。
- **PP2A-B56 互作**：本文预测的 Ssy5-PP2A 互作模式与已知的 B56-LxxIxE 互作结构（Hertz et al. 2016; Wang et al. 2016）一致，属于「已知互作模式在新系统中的预测应用」。
- **AlphaFold 系列**：本文使用 AlphaFold 单链预测（Jumper et al. 2021）和 AlphaFold 3 复合物预测（Abramson et al. 2024），属于 AI 结构预测在膜蛋白复合物中的前沿应用。
- **与 TF–DNA 互作课题的潜在连接**：本文的「突变映射 + 构象推断」策略与 TF 研究中「将 DNA 结合域突变映射到结构上推断结合特异性」的方法高度类似。此外，Ssy1 的 N 端结构域与下游信号蛋白的互作方式，可类比 TF 的调控域与共激活因子/基础转录机器的互作。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF 组成型激活突变的结构映射分析
   - **来源局限/观察**：本文对 Ssy1 激活突变的分析策略可迁移到 TF；许多 TF 的组成型激活突变（如癌症相关突变）缺乏结构解释
   - **核心假设**：TF 的组成型激活突变倾向于分布在 DNA 结合域与调控域的界面或构象铰链区，而非 DNA 结合界面本身
   - **初步方法**：收集癌症基因组数据库（如 COSMIC）中 TF 的 recurrent 激活突变 → AlphaFold 预测结构 → 映射突变 → 分析空间聚类与互作破坏 → 与已知 DNA 结合特异性数据交叉验证
   - **验证方式**：用饱和突变扫描（如 MPRA）验证预测的「构象敏感」残基；用 MD 模拟比较突变对 TF 构象稳定性的影响
   - **创新状态**：unverified

2. **候选名称**：TF-DNA 复合物的 AlphaFold 3 预测与置信度评估
   - **来源局限/观察**：本文对 AlphaFold 3 复合物预测的置信度评估策略（ipTM 分层解读）可迁移到 TF-DNA 复合物预测
   - **核心假设**：AlphaFold 3 对 TF-DNA 复合物的预测精度与 TF 家族、DNA 基序长度、辅因子存在与否相关
   - **初步方法**：系统评估 AlphaFold 3 在已知 TF-DNA 复合物结构（如 PDB 中的 TF-DNA 共晶结构）上的预测精度 → 建立「可预测性」评分体系 → 应用于未知 TF-DNA 复合物预测
   - **验证方式**：与实验解析的 TF-DNA 结构对比；用 EMSA/SELEX 验证预测的结合基序
   - **创新状态**：partially checked（AlphaFold 3 对蛋白-DNA 的预测能力已有初步评估，但系统性的 TF 家族覆盖评估尚缺）

3. **候选名称**：TF 无序区域（IDR）作为共激活因子招募平台的预测
   - **来源局限/观察**：本文强调 IDR 在 SPS 信号传导中的关键作用（Ptr3、Ssy5 的 IDR）；TF 的激活域/抑制域多为 IDR，但缺乏结构层面的互作模型
   - **核心假设**：TF 的 IDR 通过「耦合折叠与结合」机制招募共激活因子，且 IDR 内的磷酸化位点调控这一过程
   - **初步方法**：用 AlphaFold 3 预测 TF-IDR 与共激活因子（如 p300、Mediator 亚基）的复合物 → 结合磷酸化位点预测（如 NetPhos）→ 构建「磷酸化调控的 IDR 互作」模型
   - **验证方式**：NMR 或交联质谱验证 IDR-共激活因子互作；磷酸化位点突变后检测转录活性变化
   - **创新状态**：unverified

4. **候选名称**：TF 构象状态注释数据库（TF-CSM）
   - **来源局限/观察**：本文展示了「构象状态注释」的价值（区分外向开放/封闭/内向开放）；TF 领域缺乏类似的系统注释
   - **核心假设**：TF 的 DNA 结合域存在可注释的构象状态（未结合/部分结合/完全结合/封闭），且这些状态与转录活性相关
   - **初步方法**：对全部人类 TF 进行 AlphaFold 预测 → 用 MD 模拟采样构象空间 → 聚类注释构象状态 → 与 TF 活性数据（如 ENCODE）关联
   - **验证方式**：对代表性 TF 用 HDX-MS 或 FRET 验证构象状态；与已知 TF 突变体表型交叉验证
   - **创新状态**：unverified

5. **候选名称**：TF 的「门闩-铰链」机制在 DNA 结合中的角色
   - **来源局限/观察**：本文提出的 TM12 铰链 + C 端 latch 机制可能具有普遍性；TF 的 DNA 结合域可能也存在类似的「门闩」控制 DNA 结合与释放
   - **核心假设**：TF 的 DNA 结合域中存在保守的「门闩」残基，控制 DNA 结合与释放的构象转换，且这些残基是癌症突变的 hotspot
   - **初步方法**：分析 TF 家族中保守的铰链/门闩残基 → 与癌症突变数据库交叉 → 用 MD 模拟验证突变对 DNA 结合动力学的影响
   - **验证方式**：表面等离子共振（SPR）测量突变体的 DNA 结合/解离动力学；单分子 FRET 观察构象转换
   - **创新状态**：unverified