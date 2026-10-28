## 01 基本信息
- **标题**：Structure–Function Analysis of RBP7910: An Editosome Z-Binding Protein in Trypanosomatids
- **作者**：Ehlert, Curtis; Poorinmohammad, Naghmeh; Mohammaei, Saba; Zhang, Linhua; Salavati, Reza
- **单位**：未提供（通讯作者 Salavati, Reza 所属机构未在摘要中列出）
- **期刊/平台**：Molecules (Basel, Switzerland)
- **年份**：2023
- **论文类型**：实验研究（结合计算预测与体外结合实验）
- **领域**：分子生物学 / 结构生物学 / 寄生虫学（锥虫线粒体 RNA 编辑）
- **关键词**：RBP7910；Z-DNA 结合蛋白；RNA 编辑体（editosome）；微尺度热泳（MST）；分子对接；AlphaFold2
- **DOI/arXiv 号**：10.3390/molecules28196963
- **代码**：未提供
- **数据**：未提供（AlphaFold2 模型未提及是否公开）
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文聚焦于锥虫线粒体 RNA 编辑体组分 RBP7910 的 Z-DNA/Z-RNA 结合活性，属于「蛋白质–核酸互作」中 Z-构象核酸识别这一特殊子类。对 TF–DNA 互作课题的可迁移点在于：(1) 展示了 AlphaFold2 预测结构 + 分子对接 + MST 结合实验的「计算-实验」闭环流程；(2) 揭示了 Z-α 结构域对 Z-构象核酸的广谱识别机制（ss/ds、DNA/RNA 均可结合），这对理解 TF 如何区分不同核酸构象具有参考价值；(3) 提出了「保守残基可能不直接参与结合而发挥稳定/变构作用」的判别思路，可迁移到 TF–DNA 结合位点解析中。

## 02 一句话总结
本文通过 MST 结合实验与 AlphaFold2/HDOCK 计算分析，发现锥虫 RNA 编辑体蛋白 RBP7910 对 (CG)n Z-DNA（单链和双链）具有最高亲和力，其 N 端 Z-α 结构域在与 Z-构象核酸结合时展现出比非 Z 核酸更广泛的互作界面，而保守残基 Arg53/Thr52 可能不直接参与结合而是发挥结构稳定作用。

## 03 研究问题
- **具体问题**：RBP7910 是否真正具有 Z-DNA/Z-RNA 结合活性？其结合偏好（ss vs ds、DNA vs RNA、Z 构象 vs 非 Z 构象）如何？哪些残基构成互作界面？
- **为什么重要**：RBP7910 是锥虫线粒体 RNA 编辑体（editosome）的组分，而 RNA 编辑是锥虫线粒体基因表达的关键步骤。此前仅通过序列同源性推测其含 Z-DNA 结合域，但缺乏直接结合证据。理解其核酸结合特性有助于阐明编辑体如何识别和加工 gRNA-mRNA 底物。
- **现有方法不足**：此前研究（如 EMSA）仅证明 RBP7910 对 AU/U 富集 RNA 有亲和力，但未系统比较 Z 构象 vs 非 Z 构象、DNA vs RNA、ss vs ds 的差异；且缺乏结构层面的互作界面信息。
- **精确研究问题**：Can RBP7910 bind Z-form nucleic acids (Z-DNA/Z-RNA) with higher affinity than non-Z-form ligands, and can computational docking identify the specific interacting residues within its Z-α domain?

## 04 背景与发展脉络
*（标注：以下脉络为「经外部核验」——基于摘要中引用的文献及领域常识，但具体细节以原文为准）*

1. **锥虫 RNA 编辑系统**：锥虫线粒体 mRNA 需通过 U 插入/删除进行编辑，由多蛋白复合体（editosome）完成。编辑体包含三个亚复合体：RECC（催化核心）、RESC（底物结合）、REH2C（RNA 解旋酶）[1-3]。
2. **Z-核酸结合蛋白（ZBP）家族**：Z-α 结构域是已知的 Z-DNA/Z-RNA 结合模块，最早在 ADAR1 中发现。ADAR1 的 Z-α 域既能结合 Z-DNA 也能结合 Z-RNA，参与 RNA 编辑调控 [5]。
3. **RBP7910 的发现**：RBP7910 是首个被鉴定的锥虫 ZBP，含 N 端 Z-α 和 C 端 Z-β 两个推定 Z 结合域 [4]。此前研究（EMSA）显示其对 AU/U 富集 RNA 有高亲和力 [4]。
4. **结构预测方法**：AlphaFold2 的出现使无晶体结构的蛋白也能获得高质量 3D 模型，结合分子对接（HDOCK）可预测蛋白-核酸互作界面。
5. **本文位置**：首次将 MST 定量结合实验与 AlphaFold2/HDOCK 计算对接结合，系统评估 RBP7910 对不同核酸配体的结合偏好，并定位潜在互作残基。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Z 结合活性缺乏直接证据 | RBP7910 被推测为 ZBP，但无直接结合实验证明 | 此前仅基于序列同源性推断，缺乏定量结合数据 | 摘要： "the specific Z-DNA/Z-RNA binding activity and the interacting interface of RBP7910 have yet to be determined" |
| 结合偏好不明确 | 不清楚 RBP7910 对 ss/ds、DNA/RNA、Z/非 Z 构象的偏好 | 此前 EMSA 仅测试了少数 RNA 序列，未系统比较 | 摘要： "comparative analysis of the binding behavior of RBP7910 with different potential ligands" |
| 互作界面未知 | 不知道哪些残基直接参与核酸结合 | 缺乏晶体结构或突变扫描数据 | 摘要： "potential interacting surface regions of RBP7910 with notable oligonucleotide ligands were identified" |
| 保守残基功能矛盾 | Arg53/Thr52 高度保守但对接中很少出现 | 可能不直接结合而是稳定结构或介导变构效应 | Results 2.3： "instead of directly participating in ligand binding, these residues may stabilize protein conformation or contribute to its allosteric effects" |

## 06 核心思想
1. **表面方法**：用 MST 定量测定 RBP7910 与 6 种寡核苷酸（ss/ds × DNA/RNA × Z/非 Z）的结合亲和力；用 AlphaFold2 预测全长结构；用 HDOCK 做全局对接并统计互作残基频率。
2. **核心洞察**：
   - RBP7910 对 (CG)n Z-DNA（尤其 ss 形式）亲和力最高，证实其确为功能性 ZBP。
   - 与 Z 构象核酸结合时，互作界面覆盖 Z-α 域更广的残基范围；与非 Z 配体结合时界面更局限。
   - 高度保守的 Arg53/Thr52 在对接中很少出现，提示保守性 ≠ 直接结合，可能发挥结构稳定或变构调节作用。
3. **可能的普适教训** [Analysis]：
   - 序列保守性不能直接等同于功能重要性——需结合结构/对接/突变数据综合判断。
   - 计算对接的残基频率统计可作为「候选互作残基」的筛选工具，但需实验验证。
   - 对核酸结合蛋白，应系统比较 ss/ds、DNA/RNA、不同构象的配体，避免单一底物导致的偏好误判。

## 07 方法总览
- **输入**：RBP7910 全长氨基酸序列（Tritryp ID: Tb927.10.7910）；6 种 Cy5 标记寡核苷酸配体（r(UUUU)3, r(AUUU)4, r(AUUC)3, r(UA)6, d(GC)6, r(GC)6，各含 ss/ds 形式）
- **输出**：Kd 值（MST）；3D 结构模型（AlphaFold2）；互作残基频率图与 H 键分布（HDOCK 对接）
- **模块**：
  1. 蛋白表达纯化（E. coli 表达，Ni-NTA 纯化）
  2. MST 结合实验（Monolith NT.115，16 点 1:2 稀释）
  3. AlphaFold2 结构预测（ColabFold 实现）
  4. HDOCK 分子对接（全局对接，统计 top5 模型互作残基）
  5. 结构相似性搜索（RUPEE webserver）
- **训练**：不适用（AlphaFold2 为预训练模型，HDOCK 为对接工具）
- **工具**：AlphaFold2/ColabFold、HDOCK、RUPEE、ChimeraX、Discovery Studio Visualizer、Python
- **反馈回路**：MST 结果与对接结果相互印证（如 d(GC)6 ss 的 Kd 最低，对接中该配体也显示更广的互作界面）
- **文字流程**：表达纯化 RBP7910 → MST 测定 6 种配体 Kd → AlphaFold2 预测结构 → RUPEE 结构相似性搜索 → HDOCK 对接各配体 → 统计 top5 模型互作残基与 H 键 → 对比 Z/非 Z 配体的界面差异 → 结合序列保守性分析（引用 Nikpour 等）讨论 Arg53/Thr52 角色。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| MST 结合实验 | 定量测定蛋白-核酸亲和力 | 提供直接的结合证据和 Kd 值 | 输入：蛋白+Cy5 标记寡核苷酸；输出：Kd 及置信区间 | Table 1（Kd 汇总）；"lowest recorded Kd value is observed for the d(GC)6 ss" | 移除后无法区分不同配体的亲和力差异，无法证实 Z 结合活性 |
| AlphaFold2 结构预测 | 生成全长 3D 模型 | 无实验结构，需计算模型用于对接 | 输入：氨基酸序列；输出：3D 坐标 + pLDDT/PAE | "pLDDT values exceeding 90 for most parts of these domains" | 移除后无法进行结构层面的对接分析 |
| HDOCK 分子对接 | 预测蛋白-核酸互作界面 | 定位潜在结合残基 | 输入：蛋白结构+配体结构；输出：对接模型+互作残基 | Figure 2/3（残基频率与 H 键分布） | 移除后无法获得残基级别的互作信息 |
| RUPEE 结构相似性搜索 | 评估预测结构域与已知 ZBP 的相似性 | 验证结构域归属 | 输入：查询结构域；输出：相似 PDB 结构列表 | "each PDB chain ID within the top 30 structures was found to originate from a ZBP" | 移除后缺乏结构同源性佐证 |
| 序列保守性分析（引用） | 评估残基进化保守性 | 辅助判断残基功能重要性 | 输入：多序列比对；输出：保守性评分 | 引用 Nikpour 等 [4]；"these two residues exhibited conservation within the Trypanosoma genus" | 移除后无法讨论保守残基的功能角色 |

## 09 关键公式符号
本文未提供显式数学公式。MST 数据拟合采用标准 Hill 方程（未在摘要中给出具体形式），Kd 值通过仪器软件（MonitoNT 分析软件）计算。HDOCK 对接评分函数为内置算法，未在摘要中详述。因此：
- **Kd（解离常数）**：MST 实验输出，用于量化结合亲和力，数值越低亲和力越高。
- **pLDDT（predicted Local Distance Difference Test）**：AlphaFold2 输出的每个残基的置信度分数，0-100，>90 表示高置信度。
- **PAE（Predicted Aligned Error）**：AlphaFold2 输出的结构域间相对位置误差估计。
- **RMSD / TM-score**：RUPEE 结构比对输出指标，用于评估结构相似性。

## 10 实验设计与证据链
- **数据集/群体**：6 种寡核苷酸配体（r(UUUU)3 ss/ds, r(AUUU)4 ss/ds, r(AUUC)3 ss/ds, r(UA)6 ss/ds, d(GC)6 ss/ds, r(GC)6 ss/ds）；RBP7910 蛋白（重组表达）
- **规模**：每种配体 MST 实验 16 点稀释系列；对接每种配体 top5 模型
- **指标**：Kd 值（MST）；互作残基频率（对接）；H 键数量与位置
- **基线**：非 Z 构象配体（r(UUUU)3, r(AUUU)4, r(AUUC)3）作为对照
- **预算**：未提供
- **骨干/仪器**：Monolith NT.115（NanoTemper）；AlphaFold2/ColabFold；HDOCK webserver；RUPEE webserver；ChimeraX
- **oracle 输入**：AlphaFold2 预测结构作为对接受体（无实验结构）
- **评测协议**：MST 计算 Kd 及 68% 置信区间；对接统计 top5 模型互作残基频率

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| MST 结合实验 | RBP7910 对 Z-DNA 有高亲和力 | 6 种配体对比 | d(GC)6 ss 的 Kd 最低；d(GC)6 ds 次低 | RBP7910 偏好 (CG)n Z-DNA | 无法确定体内是否真的结合 Z-DNA（体外实验） | Table 1; Results 2.1 |
| AlphaFold2 结构预测 | RBP7910 含 Z-α 和 Z-β 结构域 | 与已知 ZBP 结构比对 | pLDDT>90；RUPEE 搜索 top30 均为 ZBP | 结构域归属可信 | 预测结构未经晶体学验证 | Results 2.2; Figure 1 |
| HDOCK 对接 | Z 配体结合界面更广 | Z vs 非 Z 配体对比 | Z 配体互作残基范围更广，H 键更多 | Z 结合涉及更多残基 | 对接预测需突变验证 | Results 2.3; Figure 2/3 |
| 保守性分析（引用） | Arg53/Thr52 功能重要 | 保守 vs 非保守残基 | 保守但对接中少出现 | 可能发挥稳定/变构作用 | 无直接功能实验证据 | Results 2.3; 引用 [4] |

## 11 结论正确解读
- **任务范围**：仅针对 RBP7910 蛋白与 6 种合成寡核苷酸的体外结合，未涉及编辑体完整复合物或体内环境。
- **oracle/真值输入**：AlphaFold2 预测结构作为对接受体，无实验解析结构（如 X-ray/Cryo-EM）作为金标准。
- **端到端状态**：计算预测（结构+对接）与体外实验（MST）相互印证，但未做突变验证，未达到「端到端」的功能验证。
- **算力成本**：未提供（AlphaFold2 和 HDOCK 均为在线服务，成本较低）。
- **历史数据依赖**：依赖 AlphaFold2 训练数据（PDB 中已知 ZBP 结构）；RUPEE 搜索依赖 PDB 数据库。
- **模型依赖**：AlphaFold2 预测质量受多序列比对深度影响；HDOCK 评分函数对核酸配体精度有限。
- **最难情形**：Z-RNA 配体（r(GC)6, r(UA)6）的 Kd 值高于 Z-DNA，说明蛋白对 Z-RNA 的亲和力较弱，但对接结果未显示明显界面差异——计算与实验之间存在张力。
- **群体/领域边界**：结论仅适用于锥虫 RBP7910，不可直接推广到其他 ZBP 或编辑体蛋白。
- **不确定性**：Kd 值置信区间未在摘要中给出具体数值；对接残基频率统计的显著性未做检验。
- **有边界的复述**：在体外条件下，RBP7910 对 (CG)n Z-DNA（尤其 ss 形式）表现出最高结合亲和力，其 N 端 Z-α 结构域在与 Z 构象核酸结合时互作界面更广；但保守残基 Arg53/Thr52 可能不直接参与结合，其功能需进一步实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 计算结构未经实验验证 | AlphaFold2 预测结构需晶体学确认 | "Crystallographic validation would be required to validate the predicted structure of this domain" | Results 2.2 |
| 对接结果与实验存在差异 | Kd 显示 Z-DNA vs Z-RNA 差异大，但对接界面差异不明显 | "further work must be carried out to pinpoint key residues and their impact on protein binding" | Results 2.3 |
| 关键残基功能未验证 | Arg53/Thr52 的变构/稳定假说缺乏直接证据 | "further in vitro experimental testing will be necessary" | Results 2.3 |
| 体内相关性未建立 | 体外结合实验不能反映编辑体中的真实互作 | "Further research will result in a model framework substantially advancing our understanding of the dynamic interactions of RESC proteins" | Conclusions |

**作者提及的相关约束**（非正式局限）：MST 实验使用合成寡核苷酸，未包含 gRNA-mRNA 嵌合底物；对接仅统计 top5 模型，可能遗漏低概率但重要的结合构象；Z-β 结构域的功能未深入探讨。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| d(GC)6 ss 的 Kd 最低，但 ss DNA 在溶液中是否真形成 Z 构象？ | ss (CG)n 可能形成 Z-构象的茎环结构，但未做 CD 光谱验证 | 若配体未处于 Z 构象，则「Z-DNA 结合」结论不成立 | 用 CD 光谱或 2D NMR 验证配体构象 | Results 2.1 仅报告 Kd，未提供构象证据 |
| HDOCK 对接使用 AlphaFold2 预测结构，但预测结构可能未处于适合核酸结合的构象 | AlphaFold2 预测的是 apo 状态，可能未捕捉诱导 fit 效应 | 对接结果可能遗漏真实结合所需的构象变化 | 使用 MD 模拟或 ensemble docking 测试构象灵活性 | Methods 3.4 未提及构象采样 |
| 对接统计 top5 模型，但未报告 docking score 的分布或显著性 | top5 可能不代表所有高概率结合模式 | 残基频率统计可能受模型选择偏差影响 | 增加模型数量或使用聚类分析 | Methods 3.4 "top five docking models" |
| Arg53/Thr52 保守但对接中少出现，作者推测为变构/稳定作用 | 也可能是对接评分函数对这两个残基的贡献评估不准确 | 若为变构作用，则突变实验应显示结合亲和力不变但编辑体功能受损 | 设计 Arg53A/Thr52A 突变体，检测结合与编辑体活性 | Results 2.3 仅提出假说，无实验验证 |
| 未比较 RBP7910 与其他 ZBP（如 ADAR1）的结合偏好 | 不同 ZBP 可能对 Z-DNA vs Z-RNA 有不同偏好 | 比较可揭示 Z-α 结构域的进化分化 | 平行 MST 实验比较 | 摘要未提及比较实验 |

## 14 学到什么
**Agent 提炼的知识候选**（面向 TF–DNA 互作 × AI/物理模拟课题）：

1. **「计算预测 + 定量实验」闭环流程**：AlphaFold2 预测结构 → HDOCK 对接 → MST 验证，这一流程可直接迁移到 TF–DNA 互作研究中。对无晶体结构的 TF，可用 AlphaFold2 预测 apo 结构，再用 HDOCK/其他对接工具预测 TF–DNA 复合物，最后用 MST/ITC 验证关键残基。
2. **保守残基 ≠ 直接结合残基**：本文发现高度保守的 Arg53/Thr52 在对接中很少出现，提示保守性可能反映结构稳定性或变构功能而非直接互作。对 TF–DNA 研究，这意味着序列保守的 DNA 结合域残基不一定直接接触 DNA，需结合结构/对接数据判别。
3. **配体构象验证的必要性**：本文未验证 ss (CG)n 是否真处于 Z 构象，这是实验设计的潜在缺陷。对 TF–DNA 研究，应使用 CD 光谱、NMR 或 EMSA 竞争实验验证 DNA 配体的构象状态，避免「假设构象」导致的误判。
4. **对接结果的统计处理**：本文用 top5 模型的残基频率来识别互作界面，方法简单但可能受模型选择偏差影响。可迁移的改进：使用聚类分析、增加模型数量、或结合 MD 模拟的 ensemble docking。
5. **ss vs ds 结合偏好**：RBP7910 对 ss Z-DNA 亲和力最高，提示 TF 可能也区分 ssDNA/dsDNA 底物。对 TF–DNA 研究，应系统比较 TF 对 ssDNA、dsDNA、以及不同构象（B/Z/A）的亲和力差异。
6. **Z-α 结构域的广谱核酸识别**：RBP7910 的 Z-α 域能结合 Z-DNA 和 Z-RNA，说明同一结构域可识别不同核酸类型。对 TF 研究，这提示 DNA 结合域可能也有 RNA 结合能力，值得检测。

## 15 与已有知识连接
- **Z-DNA 结合蛋白家族**：本文与 ADAR1（人类 RNA 编辑酶）的 Z-α 结构域研究直接相关。ADAR1 的 Z-α 域（PDB: 2gxb）是 Z-核酸结合的模式结构，本文通过 RUPEE 搜索确认 RBP7910 的 Z-α 域与 ADAR1、PKZ（斑马鱼）、E3L（痘苗病毒）等 ZBP 结构相似。可连接至 ZBP 家族的进化比较研究。
- **锥虫 RNA 编辑体**：本文补充了 RESC 复合体的组分功能研究。此前研究（如 Aphasizhev 等）已鉴定编辑体多个蛋白，但 RBP7910 的核酸结合特性是首次系统表征。可连接至 RNA 编辑体组装与底物识别机制研究。
- **AlphaFold2 在核酸结合蛋白研究中的应用**：本文展示了 AlphaFold2 在无实验结构蛋白上的应用。可连接至 AlphaFold2 在 TF–DNA 复合物预测中的表现（如 AlphaFold3 的发布），以及 AF2 预测结构用于对接的可靠性讨论。
- **分子对接在蛋白-核酸互作中的局限**：HDOCK 的核酸对接精度有限，本文也承认 docking score 不能直接反映结合亲和力。可连接至蛋白-核酸对接方法的综述（如 HADDOCK、NPDock 等）。
- **MST 在蛋白-核酸互作定量中的应用**：MST 是近年来流行的低耗样结合检测方法，可连接至 ITC、SPR 等传统方法的比较。
- **TF–DNA 互作的可迁移性** [Analysis]：本文的「结构预测 + 对接 + 定量结合」流程可直接迁移到 TF–DNA 研究。特别是「保守残基可能不直接结合」的发现，对 TF 的 DNA 结合域（如锌指、螺旋-转角-螺旋）功能解析有警示意义——序列保守的残基可能维持结构而非直接接触 DNA。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 互作中「保守但非接触」残基的系统识别
   - **来源局限/观察**：本文发现 RBP7910 的保守残基 Arg53/Thr52 不直接参与结合，提示序列保守性 ≠ 直接互作。TF 家族中可能普遍存在此类「结构稳定型」保守残基。
   - **核心假设**：在 TF 家族中，相当比例的保守残基不直接接触 DNA，而是通过稳定结构域折叠或调控变构来影响 DNA 结合。
   - **初步方法**：收集已知 TF–DNA 复合物结构（PDB），对每个 TF 家族做多序列比对，将残基分为「直接接触」「结构稳定」「变构调控」三类；用 AlphaFold2 预测 apo 结构，比较 holo/apo 构象差异。
   - **验证方式**：对预测的「结构稳定型」残基做饱和突变，检测 DNA 结合亲和力（MST/ITC）与结构稳定性（CD/DSF）。
   - **创新状态**：unverified（需文献调研确认是否已有类似系统分析）

2. **候选名称**：TF 对 Z-DNA 构象的识别能力筛查
   - **来源局限/观察**：RBP7910 作为编辑体蛋白能结合 Z-DNA，提示 Z-构象核酸在基因调控中可能被多种蛋白识别。TF 是否也能结合 Z-DNA 尚未系统研究。
   - **核心假设**：部分 TF 的 DNA 结合域具有 Z-DNA 结合能力，可能参与启动子区域的构象调控。
   - **初步方法**：选取 50-100 个已知 TF，用 AlphaFold2 预测结构，与已知 ZBP 的 Z-α 域做结构比对；对候选 TF 用 MST 检测与 (CG)n Z-DNA 的结合。
   - **验证方式**：阳性候选做 EMSA 竞争实验、CD 光谱验证 DNA 构象、ChIP-seq 检测基因组 Z-DNA 位点共定位。
   - **创新状态**：unverified（需确认是否已有 TF–Z-DNA 互作的系统筛查）

3. **候选名称**：AlphaFold2 预测结构在 TF–DNA 对接中的可靠性评估
   - **来源局限/观察**：本文使用 AF2 预测结构进行对接，但未评估预测结构对对接结果的影响。TF 的 apo 结构可能因柔性区域导致对接偏差。
   - **核心假设**：AF2 预测的 TF 结构在 DNA 结合域的构象准确性高于整体结构，但柔性连接区会引入对接噪声。
   - **初步方法**：选取有实验结构的 TF–DNA 复合物，用 AF2 预测 apo 结构，分别用实验结构和预测结构做 HDOCK/HADDOCK 对接，比较互作残基预测准确率。
   - **验证方式**：计算预测互作残基与实验互作残基的匹配率（如 Matthews 相关系数）。
   - **创新状态**：partially checked（已有部分研究评估 AF2 在蛋白-蛋白对接中的表现，但 TF–DNA 特异性评估较少）

4. **候选名称**：编辑体蛋白的 Z-RNA 结合在 gRNA 识别中的作用
   - **来源局限/观察**：RBP7910 对 Z-RNA 也有结合能力（Kd 高于 Z-DNA 但低于非 Z RNA），且编辑体需要处理 gRNA-mRNA 双链。Z-构象可能在编辑底物中瞬时形成。
   - **核心假设**：编辑体通过 RBP7910 的 Z-RNA 结合活性识别 gRNA-mRNA 双链中的 Z-构象区域，作为编辑起始的信号。
   - **初步方法**：用 CD 光谱检测 gRNA-mRNA 双链是否在特定序列（如 (CG)n 富集区）形成 Z-构象；用 RBP7910 突变体（Z-α 域失活）检测编辑体活性变化。
   - **验证方式**：体外编辑实验（检测编辑产物）、RBP7910 敲低/敲除株的编辑效率比较。
   - **创新状态**：unverified（需确认是否已有编辑体 Z-RNA 功能研究）

5. **候选名称**：TF 家族中螺旋-转角-螺旋（HTH）结构域对核酸构象的敏感性
   - **来源局限/观察**：RBP7910 属于 winged-HTH 超家族，其 Z-α 域能识别 Z-构象。经典 TF 的 HTH 结构域是否也有构象选择性？
   - **核心假设**：HTH 结构域的 wing 区域（β-折叠）对核酸构象变化敏感，可能赋予 TF 区分 B-DNA/Z-DNA 的能力。
   - **初步方法**：对 winged-HTH 家族 TF 做结构比对，分析 wing 区域的序列/结构特征；用 MST 检测代表性 TF 对 B-DNA vs Z-DNA 的亲和力差异。
   - **验证方式**：对 wing 区域做突变，检测构象选择性变化；MD 模拟分析 wing 区域与 Z-DNA 的相互作用。
   - **创新状态**：unverified（需确认是否已有 HTH 结构域构象选择性的研究）