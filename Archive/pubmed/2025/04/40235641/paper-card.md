## 01 基本信息
- **标题**: Substrate binding of human and bacterial type IA topoisomerase: An experimentation with AlphaFold 3.0
- **作者与单位**: Mamun, Yasir; Aguado, Ally; Preza, Ana; Kadel, Abhilasha; Mogallur, Anjani; Gonzalez, Briana; De La Rosa, Jayleen; Diaz, Daniel; Evdokimova, Polina; Karki, Ukesh; Tse-Dinh, Yuk-Ching; Chapagain, Prem（佛罗里达国际大学等，具体单位未提供）
- **期刊/预印本平台**: Computational and Structural Biotechnology Journal
- **年份**: 2025
- **论文类型**: 方法评估/基准测试研究（benchmarking study）
- **领域**: 结构生物学 × 深度学习（AlphaFold 3 蛋白-核酸复合物预测）
- **关键词**: AlphaFold 3; Type IA topoisomerase; Protein-DNA complex; Substrate binding; Sequence specificity
- **DOI/arXiv 号**: 10.1016/j.csbj.2025.03.041
- **代码**: 未提供
- **数据**: 序列信息见补充材料 Table S1；AF3 预测模型未公开提供
- **阅读日期**: 2026-05-13（按当前日期）
- **在课题方向中的位置**: 本文直接评估 AF3 在 **TF–DNA 结合机制** 相关场景（type IA topoisomerase–ssDNA）中的预测能力，重点检验：(1) 复合物结构预测的可靠性；(2) 序列偏好（sequence specificity）能否被 AF3 复现。对「AI 预测蛋白-核酸复合物」这一方法学方向具有直接参考价值，可作为 AI 结构预测工具在 DNA 结合蛋白上应用的基准测试案例。

## 02 一句话总结
本文用 AlphaFold 3 预测人 hTOP3B 和结核分枝杆菌 MtbTOP1 两种 type IA topoisomerase 与 ssDNA 的复合物结构，发现 AF3 能将短寡核苷酸（9-mer）放入结合口袋并接近催化酪氨酸，但无法可靠复现实验已知的序列偏好（如 hTOP3B 的 C 在 −5 位、MtbTOP1 的 C 在 −4 位），且长底物（>25-mer）预测不可靠。

## 03 研究问题
- **具体问题**: AlphaFold 3 能否准确预测 type IA topoisomerase 与 ssDNA 的复合物结构，并复现实验观察到的序列偏好？
- **为什么重要**: 蛋白-DNA 复合物结构难以通过实验获得（晶体化困难、Cryo-EM 分辨率有限），若 AI 能可靠预测，将极大加速对 DNA 结合蛋白（包括转录因子）结合机制的理解，并可用于药物筛选。
- **现有方法不足**: 传统 docking 工具主要针对蛋白-蛋白相互作用，对蛋白-核酸复合物预测能力有限；AlphaFold 2 无法预测核酸；实验方法耗时且对难结晶体系不适用。
- **精确研究问题**: Can AlphaFold 3 generate reliable protein-ssDNA complex models for type IA topoisomerases that reproduce experimentally known sequence preferences at the cleavage site?

## 04 背景与发展脉络
*（标注：以下脉络为「经外部核验」+「本文框架」混合，已分别注明）*

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|------|----------|------|------|----------|
| 实验结构解析 | X-ray crystallography, Cryo-EM | 高分辨率、真实 | 难结晶体系受限、耗时、蛋白-核酸复合物仅占 PDB 约 6.7% | 提供 ground truth（3PX7, 5GVC, 8CZQ 等） |
| 传统计算预测 | Protein-protein docking | 对蛋白复合物有效 | 对蛋白-核酸复合物预测能力弱 | 被替代 |
| 深度学习单链预测 | AlphaFold 2, RoseTTAFold | 蛋白结构预测精度高 | 无法预测核酸或蛋白-核酸复合物 | 被超越 |
| 深度学习复合物预测 | AlphaFold 3 | 唯一能预测蛋白-核酸复合物的工具 | 对核酸序列偏好的复现能力未经验证 | **本文评估对象** |

*（标注：此脉络中「实验结构解析」「AlphaFold 2 局限」为经外部核验的领域常识；「AF3 是唯一能预测蛋白-核酸复合物的工具」为作者主张，见 Introduction）*

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| AF3 对长 ssDNA 底物预测不可靠 | 40-mer、36-mer、31-mer 底物预测时，3' 端进入 toroid hole 形成单螺旋 | AF3 倾向于将长单链 DNA 建模为螺旋结构，且 toroid hole 被错误填充 | Results 图 2d；"the 3' tail of the DNA was found to enter the protein's toroid hole in the form of a single helix" |
| AF3 无法复现已知序列偏好 | hTOP3B 的 C 在 −5 位偏好、MtbTOP1 的 C 在 −4 位偏好均未在预测中稳定出现 | 训练数据中蛋白-核酸复合物数量有限（仅约 13,400 个），且 DNA 片段短（~7 nt）、序列多样性不足 | Conclusion："it fails to accurately reproduce sequence-dependent substrate positioning" |
| 预测置信度与准确性脱节 | 蛋白结构 pIDDT>90 但复合物 iPTM<0.55 | AF3 对蛋白单体结构预测强，但对复合物整体构象的置信度评估不可靠 | Results："iPTM scores below 0.55, indicating potentially unsuccessful models" |
| 序列上下文依赖的位点偏移 | 同一碱基在不同序列背景下被放置在 −5、−4、−3 等不同位置 | AF3 的序列-结构映射存在系统性偏差，非随机噪声 | Results 图 4c、5c；"sequence-dependent position shift in the predicted complexes" |
| 关键残基-碱基互作特异性丢失 | R194 在 hTOP3B 中与 C(−5) 或 T(−4) 均可互作，缺乏特异性 | AF3 能复现残基-磷酸骨架互作，但无法区分碱基类型 | Results："R194 is found to interact with C at −5 in one sequence but with T at −4 position for the other" |

## 06 核心思想

### 1) 表面方法
用 AF3 批量生成 topoisomerase-ssDNA 复合物模型（共 1024 个 9-mer 序列 × 2 种蛋白），通过几何分析（催化酪氨酸与磷酸基团距离）确定预测切割位点，再与实验已知的序列偏好对比。

### 2) 核心洞察
AF3 的蛋白-核酸复合物预测存在「结构正确但序列特异性缺失」的脱节：底物能被放入正确的结合口袋、与正确的残基互作，但碱基级别的序列偏好无法被复现。这意味着 AF3 的核酸结合预测可能主要基于静电/形状互补，而非碱基特异的氢键识别。

### 3) 可能的普适教训 [Analysis]
- 对 TF–DNA 互作研究：AF3 可用于生成「候选复合物构象」，但**不能**作为序列偏好（motif discovery）的可靠工具。任何基于 AF3 预测的 TF 结合位点偏好，必须用实验（EMSA、SELEX、ChIP-seq）或经典打分函数交叉验证。
- 对方法开发者：AF3 训练数据中蛋白-核酸复合物的稀缺（~13,400 vs 200,000+ 蛋白结构）是序列特异性丢失的直接原因。增加多样化的蛋白-核酸共晶结构（尤其是不同碱基组合）是提升模型的关键。
- 对物理模拟方向：AF3 预测的复合物可作为 MD 模拟的起始构象，但需注意其碱基放置的系统性偏差可能影响模拟结果。

## 07 方法总览
- **输入**: 蛋白序列（hTOP3B 全长 862 aa 或截短 611 aa；MtbTOP1 全长或截短 689 aa）+ ssDNA 序列（9-mer、11-mer、15-mer、25-mer、31-mer、36-mer、40-mer）+ Mg²⁺ 离子
- **输出**: 预测的蛋白-DNA 复合物三维结构（PDB 格式）
- **模块**:
  1. 序列准备：从 Uniprot 获取蛋白序列，从文献获取 DNA 序列
  2. 复合物生成：通过 AlphaFold 服务器（golgi.sandbox.google.com）提交预测任务
  3. 切割位点识别：Python 脚本计算每个磷酸基团氧原子与催化酪氨酸羟基氧原子的距离，最近者标记为预测切割位点
  4. 位点编号：切割位点 5' 端为 −1, −2, ...；3' 端为 +1, +2, ...
  5. 质量控制：排除底物在结合口袋外或方向翻转的模型
- **训练**: 无（使用预训练 AF3 模型）
- **工具**: AlphaFold 服务器；Python 脚本（未公开）
- **反馈回路**: 无（单轮预测，无迭代优化）
- **假设**: (1) 预测切割位点 = 距催化酪氨酸最近的磷酸基团；(2) 模型_0（最佳模型）代表最可能构象；(3) 排除标准（口袋外、翻转）不会引入选择偏差

**文字流程**: 获取序列 → 提交 AF3 服务器 → 下载模型 → 几何分析确定切割位点 → 统计各位置碱基频率 → 与实验已知偏好对比 → 分析互作残基。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 蛋白截短 | 去除柔性 C 端结构域（CTD） | 提高预测置信度；CTD 在晶体结构中未解析 | 输入：全长序列；输出：截短序列 | Methods："we used the truncated sequences with the same number of residues as in the crystal structures" | 预期影响：若保留 CTD，iPTM 可能进一步降低（[预期]）；作者未做消融对比 |
| 9-mer 序列设计 | 仅变化中间 4 个碱基，两侧固定 | 控制变量，系统扫描序列空间 | 输入：4 种侧翼 × 4⁴ 中间序列；输出：1024 条 9-mer | Methods："we limited the sequence variations to 1024 by only varying the middle four nucleotides" | 若移除：无法系统评估序列-位置关系；但侧翼固定可能引入上下文偏差（[Analysis]） |
| 切割位点识别 | 计算磷酸基团-酪氨酸距离 | 将结构预测转化为可比较的序列偏好数据 | 输入：AF3 模型；输出：预测切割位点及相对位置 | Methods："the phosphate group that was closest to the catalytic tyrosine was assigned as the possible scissile phosphate" | 若移除：无法定量比较预测与实验；但该假设可能过于简化（[Analysis]：实际切割位点可能非最近磷酸） |
| 质量控制 | 排除口袋外/翻转模型 | 避免无效预测干扰统计 | 输入：全部模型；输出：990 个 MtbTOP1 + 1024 个 hTOP3B 模型 | Results："After curation, we were left with 990 predicted models" | 若不移除：统计噪声增大；但排除标准可能引入主观偏差（[Analysis]） |
| 碱基频率统计 | 计算各相对位置碱基出现频率 | 与实验序列偏好对比 | 输入：对齐后的模型；输出：位置-碱基频率矩阵 | Results 图 3c、4d | 若移除：无法评估序列特异性 |

## 09 关键公式符号
本文无显式数学公式。核心几何判据为：

- **切割位点判据**: $d(P_i, Y_{cat}) = \min_j \| \mathbf{r}_{P_j} - \mathbf{r}_{Y_{cat}} \|$，其中 $P_j$ 为第 $j$ 个磷酸基团的氧原子位置，$Y_{cat}$ 为催化酪氨酸羟基氧原子位置。判据：$d < 4$ Å 视为有效结合（Methods 中隐含，作者未给出公式，[Analysis] 重构）。

- **位置编号**: 切割位点 5' 端碱基编号为 −1, −2, ...；3' 端为 +1, +2, ...（Methods 图 1a,b）

- **置信度指标**: pIDDT（蛋白残基级）、iPTM（复合物整体）——AF3 输出，作者未给出具体公式。

## 10 实验设计与证据链
- **数据集**: 
  - 蛋白：hTOP3B（Uniprot O95985；PDB 5GVC 截短 611 aa）、MtbTOP1（Uniprot P9WG49；PDB 8CZQ 截短 689 aa）
  - DNA：40-mer（来自 Yang et al. 2018）、11-mer/15-mer（来自 Yang et al. 的切割位点序列）、1024 条 9-mer（系统扫描）
- **规模**: 40-mer × 5 次试验；11-mer × 15 条；15-mer × 15 条；9-mer × 1024 条 × 2 蛋白
- **指标**: 预测切割位点 vs 实验切割位点的一致性；碱基频率分布 vs 实验偏好
- **基线**: 实验晶体结构（3PX7 用于 EcTOP1 的 C(−4) 偏好；5GVC 用于 hTOP3B；8CZQ 用于 MtbTOP1）
- **预算**: 未提供
- **骨干/仪器**: AlphaFold 服务器（Google DeepMind）
- **oracle 输入**: 实验已知的切割位点位置（用于对比）
- **评测协议**: 无标准 benchmark，作者自定义几何判据 + 与文献对比

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|-------------------|------|
| 40-mer 全长预测 | AF3 能否预测长底物复合物 | 5 次独立预测 vs Yang et al. 实验切割位点 | 2/5 次切割位点接近 14-nt；iPTM<0.55 | AF3 可偶发预测正确切割位点 | 预测不稳定，不可靠 | Results 图 2b |
| 40-mer 截短预测 | 截短能否改善预测 | 截短 611 aa vs 全长 862 aa | iPTM>0.70 但 3' 端进入 toroid hole | 截短提高置信度 | 结构仍不准确 | Results 图 2d |
| 11-mer 预测 | 短底物能否复现切割位点 | 15 条序列 vs Yang et al. 实验 | 仅 1/15 完全匹配 | AF3 对短底物预测仍不可靠 | 无 | Results 图 3b |
| 9-mer 全扫描（hTOP3B） | 能否复现 C(−5) 偏好 | 1024 序列 vs Yang et al. 偏好 | C 在 −5 出现频率最高，但非绝对 | 部分复现偏好 | 存在大量例外，非可靠预测 | Results 图 4d |
| 9-mer 全扫描（MtbTOP1） | 能否复现 C(−4) 偏好 | 1024 序列 vs 已知 C(−4) 偏好 | C 在 −3 或 +4 更常见 | 未复现已知偏好 | 无 | Results 图 5b |
| 互作残基分析 | 预测的残基-碱基互作是否与实验一致 | 2 条序列 vs Cryo-EM/MD 数据 | 残基类型一致但碱基特异性缺失 | AF3 能预测结合口袋残基 | 无法预测碱基特异互作 | Results 图 S5 |

## 11 结论正确解读
- **任务范围**: 仅评估 AF3 对 type IA topoisomerase-ssDNA 复合物的预测，不涉及其他蛋白家族或 dsDNA。
- **oracle/真值输入**: 实验已知的切割位点（来自 Yang et al. 的生化实验）和晶体结构（3PX7, 5GVC, 8CZQ）作为对比基准。
- **端到端状态**: 非端到端——作者手动排除了无效模型（990/1024 通过质控），且切割位点识别依赖自定义几何判据。
- **算力成本**: 未报告；AF3 服务器运行，无本地计算。
- **历史数据依赖**: AF3 训练数据包含 PDB 中约 13,400 个蛋白-核酸复合物，其中 type IA topoisomerase-DNA 复合物极少（作者列举 7 个），这是预测失败的可能原因。
- **模型依赖**: 仅测试 AF3（未测试 AlphaFold 2 的核酸版本或其他工具如 RoseTTAFoldNA）。
- **最难情形**: 长底物（>25-mer）和需要序列特异识别的场景。
- **群体/领域边界**: 结论仅适用于 type IA topoisomerase 家族；对 DNA 结合蛋白的普适性需进一步验证。
- **不确定性**: 作者未提供置信区间或统计检验；碱基频率差异未做显著性分析。

**有边界的复述**: 在 type IA topoisomerase-ssDNA 复合物预测中，AF3 能将 9-mer 底物放入结合口袋并接近催化酪氨酸，但预测的切割位点与实验已知序列偏好不一致，且长底物预测不可靠。该结论仅基于两种蛋白、有限序列集和单次预测，不适用于其他 DNA 结合蛋白。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 长底物预测不可靠 | 40-mer、36-mer、31-mer 底物预测时 3' 端进入 toroid hole | 未明确提及 | Results 图 2d,e |
| 序列偏好无法复现 | C(−5) 和 C(−4) 偏好未稳定出现 | 未明确提及 | Conclusion |
| 训练数据不足 | PDB 中 type IA topoisomerase-DNA 复合物数量有限 | "benchmarking various features of the generated models with known observables is important...to guide further developments" | Conclusion |
| 预测置信度低 | iPTM 分数普遍低于 0.55 | 未明确提及 | Results |

*（注：作者在 Conclusion 中未系统列出局限，以上为从 Results 和 Discussion 中提取的明确陈述。作者提及的相关约束：PDB 中蛋白-核酸复合物仅约 13,400 个，且 DNA 片段短、序列多样性有限——见 Introduction，此为作者提及的非正式约束。）*

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|---------------------|----------|----------|------|
| 切割位点判据过于简化 | 仅用「距催化酪氨酸最近的磷酸基团」定义切割位点，但实际催化可能涉及构象变化或多位点协同 | 若判据不准确，所有后续序列偏好分析均无效 | 用 MD 模拟或 QM/MM 验证切割位点的几何判据 | Methods 描述 |
| 排除标准可能引入偏差 | 手动排除「口袋外/翻转」模型，但未说明排除标准的具体阈值和可重复性 | 排除标准不透明可能导致结果不可复现 | 提供排除模型的完整列表和排除理由 | Results："After curation" |
| 未做统计显著性检验 | 碱基频率差异（如 C 在 −5 出现频率最高）未报告 p 值或效应量 | 无法判断观察到的模式是否显著 | 对频率分布做卡方检验或置换检验 | Results 图 4d |
| 未测试其他工具 | 仅测试 AF3，未与 RoseTTAFoldNA、MD 对接等方法对比 | 无法判断 AF3 的相对优劣 | 用相同数据集测试其他预测工具 | 未提及 |
| 训练数据偏差未量化 | 作者推测 PDB 中复合物数量少是失败原因，但未分析 AF3 训练集中 type IA topoisomerase 的具体覆盖情况 | 若训练集中已有类似复合物，则失败原因需重新解释 | 分析 AF3 训练集（如 PDB 子集）中 topoisomerase-DNA 复合物的数量和序列多样性 | Introduction 中 PDB 统计 |
| 未讨论 AF3 的随机性 | AF3 预测可能具有随机性（不同 seed 产生不同结果），但作者未报告多次运行的变异性 | 若预测不稳定，单次预测的结论不可靠 | 对同一序列重复预测多次，报告结构变异度 | 未提及 |
| 9-mer 设计可能引入上下文偏差 | 固定侧翼序列（AAA/CCC/GGG/TTT）可能影响中间 4 碱基的放置 | 观察到的「序列依赖位置偏移」可能反映侧翼效应而非真实偏好 | 使用随机侧翼或不同侧翼长度重复实验 | Methods 描述 |

## 14 学到什么
**Agent 提炼的知识候选**（面向 TF–DNA 结合机制 × AI/物理模拟方向）:

1. **概念**: AF3 的蛋白-核酸复合物预测存在「结构正确但序列特异性缺失」的脱节。
   - **迁移**: 对 TF–DNA 互作研究，AF3 可用于生成复合物构象（如结合口袋形状、残基互作网络），但**不可**用于预测 TF 的结合 motif 或序列偏好。任何基于 AF3 的 TF 结合位点预测需用实验或经典打分函数验证。

2. **方法**: 系统扫描序列（1024 个 9-mer）评估预测的序列偏好。
   - **迁移**: 可设计类似策略评估其他 AI 结构预测工具（如 RoseTTAFoldNA、Boltz-1）对 TF-DNA 序列偏好的复现能力，建立标准 benchmark。

3. **方法**: 几何判据（催化残基-底物距离）定义功能位点。
   - **迁移**: 对 TF 研究，可用「识别螺旋-碱基距离」或「关键残基-碱基氢键」作为几何判据，评估预测复合物是否处于功能相关构象。

4. **概念**: 训练数据中蛋白-核酸复合物的稀缺是序列特异性预测失败的主因。
   - **迁移**: 对 AI 方法开发者，增加多样化的 TF-DNA 共晶结构（覆盖不同碱基组合和 TF 家族）是提升模型序列特异性的关键。对实验研究者，优先解析序列多样性高的 TF-DNA 复合物结构。

5. **方法**: 截短蛋白（去除柔性结构域）可提高预测置信度。
   - **迁移**: 对 TF 预测，可尝试截去非保守的 N/C 端或柔性 linker 区域，提高 AF3 对 DNA 结合结构域的预测质量。

6. **概念**: 长底物（>25-mer）预测不可靠，短底物（9-mer）相对可靠。
   - **迁移**: 对 TF-DNA 研究，优先使用短 DNA 片段（如 9-15 bp）进行 AF3 预测；对长片段（如 nucleosome 或 enhancer 区域），需结合实验结构或 MD 模拟。

7. **方法**: 通过添加辅助分子（如 Mg²⁺）模拟真实生理条件。
   - **迁移**: 对 TF-DNA 预测，可尝试添加已知的辅助因子（如 Zn²⁺、小分子配体）看是否能改善预测准确性。

8. **概念**: 预测的残基-磷酸骨架互作可靠，但碱基特异互作不可靠。
   - **迁移**: 对 TF 研究，AF3 预测可用于识别 DNA 结合残基（与磷酸骨架互作的残基），但碱基识别残基（base-specific readout）需通过实验或 MD 模拟验证。

## 15 与已有知识连接
- **AlphaFold 2 与 AF3 的对比**: 本文结果与 AlphaFold 2 在蛋白-蛋白复合物预测上的成功形成对比——AF3 扩展到了蛋白-核酸复合物，但序列特异性预测能力不足。这与 [Abramson et al., Nature 2024] 中 AF3 对蛋白-核酸复合物预测的总体评估一致（AF3 在蛋白-核酸复合物上精度低于蛋白-蛋白复合物）。
- **Topoisomerase 结构研究**: 本文使用的 hTOP3B 晶体结构（PDB 5GVC, [21]）和 MtbTOP1 结构（PDB 8CZQ, [22]）是已知的。EcTOP1 的 C(−4) 偏好已有晶体学证据（PDB 3PX7, [12]），本文尝试用 AF3 复现但失败。
- **序列偏好预测方法**: 传统方法如 SELEX、ChIP-seq、PWM 模型可可靠预测 TF 结合位点；本文表明 AF3 目前无法替代这些方法。这与 [Yan et al., Nature Methods 2024] 对 AF3 在蛋白-核酸复合物预测上的评估一致。
- **MD 模拟互补**: 本文提到 MD 模拟数据（[28]）已用于揭示 hTOP3B-ssDNA 互作残基，而 AF3 预测的残基互作与 MD 结果部分一致（图 S5），说明 AF3 + MD 的组合可能比单独使用更可靠。
- **候选方向**: 本文的「系统扫描 + 几何判据」方法可迁移到 TF-DNA 预测评估；「截短蛋白提高置信度」策略可推广到其他 DNA 结合蛋白的 AF3 预测。

## 16 研究想法
**Agent 生成的研究候选**:

1. **名称**: TF-DNA 序列偏好预测的 AI 工具基准测试框架
   - **来源局限/观察**: 本文仅测试了 topoisomerase，未覆盖 TF 家族；且未与其他 AI 工具对比。
   - **核心假设**: 不同 AI 结构预测工具（AF3、RoseTTAFoldNA、Boltz-1）对 TF-DNA 序列偏好的复现能力存在显著差异，且与 TF 家族（如 C2H2、bZIP、homeodomain）相关。
   - **增量**: 建立覆盖多个 TF 家族、多种 DNA 序列的 benchmark，量化各工具的序列特异性预测能力。
   - **初步方法**: 选取 5-10 个有实验结构（PDB）和生化数据（SELEX/PBM）的 TF，设计 9-15 bp 的 DNA 序列库，用各工具预测复合物，用几何判据（识别螺旋-碱基距离）确定预测结合位点，与实验 motif 对比。
   - **验证方式**: 计算预测 motif 与实验 motif 的相似性（如 Tomtom 比较）；用 AUC 评估预测结合位点的准确性。
   - **创新状态**: unverified

2. **名称**: AF3 预测 + MD 精修的 TF-DNA 复合物工作流
   - **来源局限/观察**: 本文发现 AF3 预测的残基-磷酸骨架互作可靠但碱基特异性缺失；MD 模拟可提供动态信息。
   - **核心假设**: 以 AF3 预测的复合物为起点，用 MD 模拟（含增强采样）精修，可恢复部分碱基特异性互作，提高预测准确性。
   - **增量**: 提出「AF3 粗预测 + MD 精修」的两阶段工作流，并系统评估其在不同 TF 上的表现。
   - **初步方法**: 对 3-5 个 TF，用 AF3 生成复合物，进行 100-500 ns 的 MD 模拟，分析碱基-残基氢键占有率，与实验结构对比。
   - **验证方式**: 比较 MD 精修前后预测结构与实验结构的 RMSD、氢键网络一致性。
   - **创新状态**: unverified

3. **名称**: 基于 AF3 预测的 TF-DNA 结合口袋形状分析
   - **来源局限/观察**: 本文显示 AF3 能正确放置底物在结合口袋中，但未分析口袋形状与序列选择的关系。
   - **核心假设**: AF3 预测的 TF-DNA 复合物中，结合口袋的几何形状（如口袋深度、电荷分布）与实验观察一致，可用于预测 TF 的 DNA 结合模式（major/minor groove）。
   - **增量**: 将 AF3 预测从「序列偏好」扩展到「结合模式」分析，为 TF 分类提供新工具。
   - **初步方法**: 对多个 TF 的 AF3 预测复合物，计算口袋形状描述符（如 DoGSiteScorer），与实验结构对比。
   - **验证方式**: 比较预测与实验的口袋形状相似性；用分类器评估结合模式预测准确性。
   - **创新状态**: unverified

4. **名称**: 数据增强策略：利用 AF3 生成训练数据提升 TF-DNA 结合预测模型
   - **来源局限/观察**: 本文指出 PDB 中蛋白-核酸复合物数量有限是 AF3 序列特异性不足的原因。
   - **核心假设**: 用 AF3 生成大量 TF-DNA 复合物结构（即使序列特异性不完美），作为训练数据增强，可提升下游机器学习模型（如 DNA 结合特异性预测器）的性能。
   - **增量**: 提出「AI 生成结构数据增强」策略，缓解实验数据稀缺问题。
   - **初步方法**: 用 AF3 生成 1000+ TF-DNA 复合物，提取结构特征（如残基-碱基接触），训练 CNN/Transformer 模型预测 TF 结合位点，与仅用实验数据训练的模型对比。
   - **验证方式**: 在独立测试集（如 ChIP-seq 数据）上比较 AUC、Precision-Recall。
   - **创新状态**: unverified

5. **名称**: 长 ssDNA 底物预测的 toroid hole 伪影分析与规避
   - **来源局限/观察**: 本文发现 AF3 预测长底物时 3' 端进入 toroid hole，形成不真实的单螺旋结构。
   - **核心假设**: 该伪影源于 AF3 对长核酸的建模偏差，可通过分段预测或添加约束（如二面角限制）规避。
   - **增量**: 提出针对长 DNA 底物的 AF3 预测改进策略，适用于 TF 结合长调控区域的研究。
   - **初步方法**: 将 40-mer 分段为 9-mer 片段分别预测，再拼接；或使用 AF3 的「自定义模板」功能添加 toroid hole 的空间约束。
   - **验证方式**: 比较分段预测与全长预测的结构合理性（如 toroid hole 是否被正确保留）、与实验结构的 RMSD。
   - **创新状态**: unverified