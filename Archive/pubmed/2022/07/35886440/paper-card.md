## 01 基本信息

- **标题**：In Silico Insights on the Pro-Inflammatory Potential of Polycyclic Aromatic Hydrocarbons and the Prospective Anti-Inflammatory Capacity of Andrographis paniculata Phytocompounds
- **作者与单位**：Julaton, Trixia; Taclendo, Aibelou; Oyong, Glenn; Rempillo, Ofelia; Galvez, Maria Cecilia; Vallar, Edgar（单位未在摘要中提供，推测为菲律宾高校，具体未提供）
- **期刊/平台**：International Journal of Environmental Research and Public Health (IJERPH)
- **年份**：2022
- **论文类型**：计算研究（in silico），分子对接 + 分子动力学模拟
- **领域**：环境毒理学 × 计算生物学 × 炎症信号通路
- **关键词**：PAHs；TLR4；NF-κB p50；分子对接；分子动力学模拟；穿心莲（Andrographis paniculata）；抗炎
- **DOI/arXiv 号**：10.3390/ijerph19148588
- **代码**：未提供
- **数据**：PubChem（配体结构）、RCSB-PDB（蛋白结构，PDB ID 4G8A 和 1NFK）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「小分子–蛋白互作」的计算筛选研究，聚焦于环境污染物（PAH）与免疫受体 TLR4 的结合，以及天然产物对转录因子 NF-κB p50 的抑制。与「TF–DNA 结合机制 × AI/物理模拟」课题的关联在于：NF-κB p50 本身是转录因子，本文研究的是小分子（而非 DNA）与 TF 的结合，方法上（对接 + MD）可迁移至 TF–DNA 体系，但本文未涉及 DNA 结合域与 DNA 的互作。

## 02 一句话总结

本文通过 AutoDock Vina 分子对接和 CABS-flex 分子动力学模拟，评估 7 种多环芳烃（PAH）与 TLR4 的结合能力（最强为 indeno(1,2,3-cd)pyrene，−10 kcal/mol）以及 9 种穿心莲植物化合物对 NF-κB p50 转录因子的抑制潜力（最强为 ergosterol peroxide，−5.6 kcal/mol），提出 PAH 通过 TLR4 激活 NF-κB 通路诱导炎症、穿心莲化合物可潜在抑制该通路的理论机制。

## 03 研究问题

- **具体问题**：PAHs 是否通过结合 TLR4 受体激活 NF-κB 炎症通路？穿心莲（A. paniculata）中的哪些植物化合物能够有效结合 NF-κB p50 亚基从而抑制该通路？
- **为什么重要**：PAHs 是普遍存在的环境污染物，与慢性炎症性疾病相关；菲律宾燃煤发电导致 PAH 暴露风险高。现有抗炎药物（NSAIDs、皮质类固醇、生物制剂）存在耐药性和副作用，需要寻找天然替代物。
- **现有方法为何不足**：体外/体内实验成本高、周期长；此前缺乏对 PAH–TLR4 和植物化合物–NF-κB p50 结合亲和力的系统性计算评估。
- **精确的 Can 问题**：Can molecular docking and MD simulations identify PAHs that bind TLR4 with higher affinity than LPS, and A. paniculata phytocompounds that bind NF-κB p50 with higher affinity than dexamethasone?

## 04 背景与发展脉络

> 注：以下脉络基于本文引言和讨论部分，属于「仅本文框架」，未经外部系统核验。

1. **PAH 毒理学研究阶段**：早期研究（Santiago & Cayetano 2007；Zhang et al.）聚焦于 PAH 环境浓度监测和暴露评估，确认菲律宾地区 PAH 浓度高于伦敦和曼彻斯特。局限：未阐明分子机制。
2. **PAH–TLR4 关联研究阶段**：多项研究（[17,18,19]）发现 PAH 可通过 TLR4 引发细胞炎症反应；Sreeja et al. [31] 对 16 种致癌 PAH 与 TLR4 进行对接研究。局限：使用的对接工具（AutoDock 1.5）和评分函数较旧，结合能数值偏高。
3. **NF-κB 作为抗炎靶点的研究阶段**：NF-κB 是炎症核心转录因子，多数抗炎药物通过抑制 NF-κB 激活发挥作用。穿心莲内酯（andrographolide）及其衍生物已被证实抑制 NF-κB 信号通路 [6,15]。
4. **计算筛选天然产物的阶段（本文位置）**：利用分子对接 + MD 模拟，在原子水平评估 PAH–TLR4 和植物化合物–NF-κB p50 的相互作用，为后续体外实验提供候选分子和理论依据。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PAH 暴露与炎症关联的分子机制不清 | 已知 PAH 诱导炎症，但具体受体结合机制未阐明 | PAH 与 TLR4 的结合亲和力及关键残基未知 | 引言部分引用 [17,18,19]；Results 3.2 节 |
| 现有抗炎药物副作用大 | NSAIDs、皮质类固醇存在耐药性和剂量限制性副作用 | 长期使用导致不良反应 | 引言第 1 段 |
| 穿心莲化合物抗炎活性缺乏系统比较 | 已知穿心莲有抗炎作用，但哪种化合物对 NF-κB p50 结合最强不清楚 | 缺乏对多种化合物的平行对接评估 | Results 3.3 节，Table 6 |
| 计算筛选的可靠性问题 | 不同对接工具给出不同结合能 | 评分函数和搜索算法差异 | Discussion 中与 Sreeja et al. 结果对比（−7.02~−8.25 vs −8.1~−10 kcal/mol） |
| 结合稳定性未验证 | 仅对接不足以证明稳定结合 | 需要 MD 模拟验证构象稳定性 | Methods 2.4 节，Results 3.2.4 和 3.3.4 节 |

## 06 核心思想

1. **表面方法**：对 7 种 PAH 与 TLR4、9 种穿心莲化合物与 NF-κB p50 分别进行 AutoDock Vina 分子对接，计算结合能；对结合最强的复合物进行 CABS-flex 10 ns 粗粒化 MD 模拟，通过 RMSF 评估构象稳定性；以 LPS（TLR4 天然配体）和地塞米松（NF-κB 抑制剂）作为阳性对照。

2. **核心洞察**：PAH 分子（尤其是 IP 和 DahA）通过疏水相互作用和 π-π 堆积与 TLR4 的疏水口袋结合，结合能低于 LPS，表明其可能比天然配体更有效地激活 TLR4。穿心莲中的 ergosterol peroxide 通过氢键和疏水作用与 NF-κB p50 的 Arg305 等残基结合，结合能低于地塞米松，提示其可能更有效地阻断 NF-κB 的 DNA 结合功能。

3. **可能的普适教训** [Analysis]：本文展示了一个「环境毒物–受体激活」+「天然产物–转录因子抑制」的双靶点计算筛选范式。对于 TF–DNA 互作课题，其可迁移之处在于：① 以已知内源配体（如 LPS、DNA 共有序列）作为阳性对照来校准对接结果的思路；② 将对接（静态结合）与 MD（动态稳定性）串联验证的工作流；③ 关注配体结合口袋的疏水性和氢键特征来推断功能后果。

## 07 方法总览

- **输入**：
  - 蛋白结构：人 TLR4（PDB ID 4G8A，与 LPS 复合物）、NF-κB p50 同源二聚体（PDB ID 1NFK，与 κB 位点 DNA 复合物）
  - 配体结构：7 种 PAH（苯并(a)蒽、苯并(a)芘、苯并(b)荧蒽、苯并(k)荧蒽、䓛、二苯并(a,h)蒽、茚并(1,2,3-cd)芘）+ 9 种穿心莲化合物，均来自 PubChem
  - 阳性对照：LPS（TLR4 配体）、地塞米松（NF-κB 抑制剂）

- **输出**：结合能（kcal/mol）、RMSD、RMSF 值、氨基酸互作图谱、MD 构象变化

- **模块**：
  1. 配体准备：PubChem 获取 3D SDF → Open Babel 转换为 PDBQT
  2. 蛋白准备：RCSB-PDB 获取 → 去除水分子/异源原子 → AutoDock Tools 加氢和 Kollman 电荷
  3. 结合位点定义：TLR4 以 LPS 结合位点为中心；p50 以 DNA 结合区为中心，15 Å 半径网格
  4. 分子对接：AutoDock Vina 1.2.0，exhaustiveness = 8
  5. MD 模拟：CABS-flex 2.0，10 ns，默认参数
  6. 统计分析：双尾 t 检验（α = 0.05）比较 apo 与结合态 RMSF

- **文字流程**：配体/蛋白准备 → 结合位点定义 → 分子对接筛选（以结合能排序）→ 选出最高亲和力复合物 → CABS-flex MD 模拟 → RMSF 分析 apo vs. bound 构象差异 → t 检验判断显著性 → 结合氨基酸互作分析推断功能意义

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 配体准备（Open Babel） | 将 PubChem SDF 转为 PDBQT 格式 | 对接需要特定格式和原子类型 | 输入：SDF；输出：PDBQT | Methods 2.1 节 | 预期影响：格式错误导致对接失败或结果不可靠 [预期效应] |
| 蛋白准备（AutoDock Tools） | 加氢、加电荷、去水/异源物 | 对接需要正确的质子化状态和电荷 | 输入：PDB；输出：PDBQT | Methods 2.3 节 | 预期影响：电荷/质子化错误导致结合能偏差 [预期效应] |
| 结合位点定义 | 以已知配体结合区为中心设 15 Å 网格 | 限制搜索空间，提高效率 | 输入：蛋白-配体复合物坐标；输出：网格参数 | Methods 2.3 节 | 预期影响：位点定义错误导致错过真实结合模式 [预期效应] |
| 分子对接（AutoDock Vina） | 计算配体-蛋白结合能 | 筛选高亲和力候选物 | 输入：PDBQT 配体+蛋白；输出：结合能、构象 | Results 表 3、表 6 | 实测效应：Vina 与 AutoDock 1.5 结果差异显著（Discussion 对比 Sreeja et al.）[实测效应] |
| MD 模拟（CABS-flex） | 验证复合物动态稳定性 | 对接是静态快照，需验证时间演化 | 输入：对接复合物 PDB；输出：RMSF、构象系综 | Results 3.2.4、3.3.4 节 | 预期影响：无 MD 则无法判断结合是否稳定 [预期效应] |
| 统计分析（t 检验） | 比较 apo 与 bound RMSF | 判断结合是否引起显著构象变化 | 输入：RMSF 数据；输出：p 值 | Results 3.2.4、3.3.4 节 | 预期影响：无统计检验则结论缺乏显著性支持 [预期效应] |

## 09 关键公式符号

本文未提供明确的数学公式。核心量化指标为：

- **结合能（Binding Energy, ΔG_binding）**：AutoDock Vina 输出的打分值，单位 kcal/mol。更负的值表示更强的预测结合亲和力。Vina 的评分函数为经验式：ΔG = ΔG_intermolecular + ΔG_torsional + ΔG_internal（作者未给出具体参数，此为 Vina 默认评分函数的一般形式）。
- **RMSD（Root Mean Square Deviation）**：用于验证对接构象与晶体构象的偏差，文中报告为 0.00 Å，表示对接构象与参考构象完全一致。
- **RMSF（Root Mean Square Fluctuation）**：MD 模拟中每个残基的均方根波动，单位 Å，用于表征蛋白质局部柔性变化。文中通过比较 apo 与 bound 状态的 RMSF 判断配体结合对蛋白构象的影响。
- **t 检验**：双尾配对 t 检验，α = 0.05，用于判断 apo 与 bound RMSF 差异的统计显著性。

## 10 实验设计与证据链

- **数据集/群体**：
  - 配体：7 种 PAH（EPA 致癌物分类）+ 9 种穿心莲化合物 + 2 个阳性对照（LPS、地塞米松）
  - 蛋白：TLR4（PDB 4G8A）、NF-κB p50（PDB 1NFK）
- **规模**：共 18 个对接实验（7 PAH-TLR4 + 9 AP-p50 + 2 对照）
- **指标**：结合能（kcal/mol）、RMSD（Å）、RMSF（Å）、p 值
- **基线/对照**：LPS 作为 TLR4 的天然配体对照；地塞米松作为 NF-κB 抑制剂的临床药物对照
- **预算**：未提供
- **骨干/仪器**：AutoDock Vina 1.2.0、CABS-flex 2.0、AutoDock Tools 4.2、Open Babel 2.4.1、BIOVIA Discovery Studio Visualizer 2021
- **oracle 输入**：LPS 在 TLR4 上的结合位点坐标、DNA 在 p50 上的结合位点坐标（来自晶体结构）
- **评测协议**：对接后取最低结合能构象，RMSD = 0 验证；MD 模拟 10 ns 后比较 apo/bound RMSF，t 检验判断显著性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| PAH-TLR4 对接 | PAHs 能结合 TLR4 且亲和力高于 LPS | 7 种 PAH vs LPS 对照 | 所有 PAH 结合能 −8.1~−10 kcal/mol，低于 LPS 的 −4.1 kcal/mol | PAHs 是 TLR4 的潜在强激动剂 | 结合能高低不等于功能激活强度，需实验验证 | Results 表 3 |
| AP-p50 对接 | 穿心莲化合物能结合 NF-κB p50 | 9 种化合物 vs 地塞米松对照 | Ergosterol peroxide −5.6 kcal/mol 低于地塞米松 −5.4 kcal/mol；14-deoxy-14,15-dehydroandrographolide −5.3 kcal/mol | 两种化合物具有优于或接近地塞米松的结合潜力 | 结合亲和力不等于抑制活性 | Results 表 6 |
| MD 模拟（TLR4-IP） | IP 结合不破坏 TLR4 结构稳定性 | apo vs bound，10 ns，t 检验 | 链 A（p=0.2890）和链 D（p=0.0525）无显著差异 | IP 稳定结合 TLR4 链 D | 链 B、C 有显著差异（p<0.0001），可能影响蛋白功能 | Results 3.2.4 节 |
| MD 模拟（TLR4-DahA） | DahA 结合不破坏 TLR4 结构稳定性 | apo vs bound，10 ns，t 检验 | 链 A、B、D 无显著差异；链 C 显著差异（p<0.0001） | DahA 稳定结合 TLR4 链 D | 链 C 的显著波动可能影响蛋白功能 | Results 3.2.4 节 |
| MD 模拟（p50-ergosterol peroxide） | 化合物结合不破坏 p50 结构 | apo vs bound，10 ns，t 检验 | 链 A（p=0.9966）和链 B（p=0.8286）无显著差异 | 稳定结合 | 未检测功能抑制效果 | Results 3.3.4 节 |
| MD 模拟（p50-14-deoxy-14,15-dehydroandrographolide） | 化合物结合不破坏 p50 结构 | apo vs bound，10 ns，t 检验 | 链 B 无显著差异（p=0.3147）；链 A 显著差异（p=0.0038） | 链 B 稳定结合 | 链 A 的不稳定可能影响抑制效果 | Results 3.3.4 节 |

## 11 结论正确解读

- **任务范围**：本文仅覆盖计算层面的结合亲和力预测和构象稳定性评估，不包含任何体外或体内功能实验。
- **oracle/真值输入**：TLR4 的 LPS 结合位点和 p50 的 DNA 结合位点来自晶体结构，是可靠的先验信息；但配体结合能完全依赖 Vina 评分函数，未经实验校准。
- **端到端状态**：非端到端。本文是筛选性研究，输出为候选分子排名和理论机制假设，而非经过验证的药物或毒理学结论。
- **算力成本**：CABS-flex 为粗粒化 MD，计算成本低；但 10 ns 时间尺度远短于生物相关过程（μs-ms），无法捕捉慢构象变化。
- **历史数据依赖**：配体选择依赖文献报道的 EPA 致癌物列表和穿心莲已知活性成分，存在选择偏差。
- **模型依赖**：AutoDock Vina 对疏水相互作用的评分可能高估 PAH 这类高疏水分子的结合；CABS-flex 粗粒化模型无法描述氢键网络的精细变化。
- **最难情形**：PAH 分子小且高度疏水，可能非特异性结合蛋白表面而非特定口袋；Vina 可能产生假阳性。
- **群体/领域边界**：结论仅适用于所测试的 7 种 PAH 和 9 种穿心莲化合物，不能外推至所有 PAH 或所有植物化合物。
- **不确定性**：结合能差异（如 −5.6 vs −5.4 kcal/mol）在 Vina 评分函数的误差范围内（通常 ±1-2 kcal/mol），不能过度解读。
- **有边界的复述**：在 AutoDock Vina 和 CABS-flex 的计算框架下，IP 和 DahA 是 TLR4 的潜在高亲和力配体，ergosterol peroxide 是 NF-κB p50 的潜在抑制剂；这些预测需要实验验证，且不构成对功能活性的直接证据。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 缺乏实验验证 | 所有结论基于计算预测 | 推荐进行体外（in vitro）和体内（in vivo）研究以确认抗炎和细胞毒性 | Conclusions 最后一段 |
| 未评估细胞毒性 | 未测试候选化合物的细胞毒性 | 未来研究需确定 ameliorative 和 cytotoxic 特性 | Conclusions 最后一段 |
| 结合机制未完全阐明 | 对 NF-κB 抑制的分子机制仅提出理论 | 需进一步阐明 IKK 磷酸化和配体共价结合机制 | Discussion 最后一段 |
| 其他化合物未深入研究 | 仅深入分析了结合能最高的两种 PAH 和两种 AP 化合物 | 其他化合物值得在体外研究中进一步考察 | Discussion 中对 5-hydroxy-7,8-dimethoxyflavanone 的讨论 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 结合能差异可能不显著 | IP（−10 kcal/mol）vs DahA（−9.2 kcal/mol）vs LPS（−4.1 kcal/mol）的差异在 Vina 评分函数中可能受分子大小和疏水性影响 | 疏水分子天然倾向获得更负的 Vina 分数，可能不代表更高的特异性 | 使用多种对接软件（如 Glide、GOLD）交叉验证；或进行 MM-PBSA 自由能计算 | Results 表 3；Vina 评分函数已知对疏水相互作用权重较高 |
| MD 模拟时间过短 | 10 ns 粗粒化模拟不足以评估结合稳定性 | 蛋白质-配体复合物可能在更长的时间尺度上解离或重排 | 延长至 100 ns-1 μs 全原子 MD；或使用增强采样方法 | Methods 2.4 节 |
| 阳性对照选择有限 | 仅用 LPS 和地塞米松作为对照，缺乏已知的 TLR4 拮抗剂或 NF-κB 抑制剂作为阴性对照 | 无法评估筛选的特异性 | 加入已知无活性化合物作为阴性对照 | Results 表 3、表 6 |
| 未讨论结合位点可竞争性 | 未验证 PAH 和 AP 化合物是否结合同一口袋，也未讨论 AP 化合物是否可竞争性阻断 PAH 诱导的 TLR4 激活 | 理论机制的核心假设是 AP 抑制 NF-κB 而非阻断 TLR4 激活 | 进行 TLR4-AP 化合物对接；或设计竞争性结合实验 | 引言中提出的机制假设 |
| 统计检验的适用性 | 对 RMSF 使用 t 检验假设残基波动独立，但相邻残基波动高度相关 | 可能低估或高估显著性 | 使用更合适的统计方法（如协方差分析） | Results 3.2.4、3.3.4 节 |
| 缺乏构象系综分析 | 仅比较 apo 和 bound 的 RMSF，未分析 MD 轨迹中的构象转变路径 | 配体结合可能诱导变构效应而非局部波动变化 | 进行主成分分析（PCA）或动态网络分析 | Results 3.2.4、3.3.4 节 |

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题。

1. **以天然配体结合位点作为对接网格中心的策略**：本文以 LPS 在 TLR4 上的已知结合位点定义对接网格，避免了盲目搜索。迁移到 TF–DNA 课题：可以 TF 的 DNA 结合域（DBD）中已知的 DNA 识别残基为中心定义对接网格，筛选可能干扰 TF–DNA 结合的小分子或评估 TF 突变体对 DNA 结合的影响。

2. **双对照设计（天然配体 + 临床药物）**：TLR4 实验用 LPS 作阳性对照，p50 实验用地塞米松作阳性对照。迁移到 TF–DNA 课题：评估候选分子对 TF–DNA 结合的干扰时，应以已知的 DNA 共有序列作为阳性对照，以已知无结合活性的随机序列作为阴性对照，校准打分函数。

3. **对接 + MD 串联验证的工作流**：先对接筛选（静态、快速），再对 top 候选做 MD 验证（动态、慢速）。迁移到 TF–DNA 课题：对 TF–DNA 复合物，可先做蛋白-DNA 对接（如 HDOCK、NPDock）筛选 TF 突变体或 DNA 序列变体，再用全原子 MD（如 AMBER、GROMACS）验证 top 候选的稳定性。

4. **RMSF 差异作为结合稳定性的代理指标**：本文通过比较 apo 和 bound 状态的 RMSF 判断配体结合是否引起显著构象变化。迁移到 TF–DNA 课题：比较 TF 单独与 TF-DNA 复合物中 DBD 区域的 RMSF，可识别 DNA 结合诱导的构象变化区域，帮助定位关键功能残基。

5. **π-π 堆积和疏水作用在芳香族配体结合中的主导地位**：PAH 与 TLR4 的互作以 π 体系和疏水作用为主。迁移到 TF–DNA 课题：TF 的芳香族残基（Phe、Tyr、Trp）常通过 π-π 堆积、阳离子-π 或疏水作用与 DNA 碱基互作，这一化学直觉可用于设计 TF–DNA 结合预测模型的特征工程。

6. **结合能数值的跨研究可比性问题**：本文指出与 Sreeja et al. 的差异源于对接工具不同。迁移到 TF–DNA 课题：不同软件/力场给出的 TF–DNA 结合能不可直接比较，应统一工具和参数，或使用相对排名而非绝对值。

7. **计算筛选作为实验前导的定位**：本文明确将计算研究定位为体外实验的 preliminary study。迁移到 TF–DNA 课题：AI 预测或 MD 模拟的 TF–DNA 结合结果应视为假设生成工具，而非替代实验验证。

## 15 与已有知识连接

- **TF–DNA 互作机制**：本文研究的 NF-κB p50 是 Rel 同源结构域（RHD）家族转录因子，其与 DNA 的结合通过 RHD 中的 loop 区域识别 κB 位点（5'-GGGRNNYYCC-3'）。本文研究的是小分子与 p50 的结合，而非 p50 与 DNA 的结合，但 p50 的 DNA 结合域也是小分子抑制剂的潜在靶点。可连接至 Chen et al. (1998) 的 NF-κB p50-DNA 共晶结构（PDB 1SVC）等文献。
- **TLR4 信号通路**：TLR4 是模式识别受体，LPS 结合后通过 MyD88/TRIF 通路激活 NF-κB。本文的 PAH–TLR4 结合研究可连接至 Park et al. (2009) 的 TLR4-MD-2-LPS 复合物结构（PDB 3FXI）。
- **分子对接方法学**：AutoDock Vina 的评分函数基于经验势，对疏水相互作用敏感。可连接至 Trott & Olson (2010) 的 Vina 原始论文，以及后续的 AutoDock Vina 1.2.0 改进版本。
- **CABS-flex 方法**：CABS-flex 是基于粗粒化模型的快速柔性预测工具，适用于中等规模构象采样。可连接至 Jamroz et al. (2013) 的 CABS-flex 原始论文。
- **天然产物抗炎研究**：穿心莲内酯及其衍生物抑制 NF-κB 通路的机制已有较多体外研究（如 Xia et al., 2004），本文的贡献在于对穿心莲中其他化合物的计算筛选。
- **环境毒理学与计算毒理学**：PAH 的毒性评估传统上依赖实验，本文展示了计算毒理学在预测受体结合方面的应用，可连接至 EPA 的 ToxCast 计划和 DSSTox 数据库。

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题。

### 候选 1：基于深度学习的 TF–DNA 结合亲和力预测模型，以对接打分作为特征
- **名称**：Docking-Enhanced TF-DNA Binding Affinity Prediction
- **来源局限/观察**：本文的对接方法仅评估小分子-蛋白结合，未涉及 TF-DNA 相互作用；现有 TF-DNA 预测模型（如 DeepBind、DeepSEA）主要基于序列特征，缺乏结构信息
- **核心假设**：将分子对接产生的结构特征（结合能、接触残基、氢键网络）与序列特征结合，可提高 TF-DNA 结合亲和力的预测精度
- **初步方法**：对已知 TF-DNA 复合物（如来自 CIS-BP 数据库）进行批量对接，提取结构特征；训练一个多模态深度学习模型（序列 CNN + 结构特征 MLP），预测结合亲和力
- **验证方式**：在独立测试集上比较与 DeepBind、DeepSEA 的 AUC 和 Pearson 相关系数
- **创新状态**：unverified

### 候选 2：TF 突变体对 DNA 结合影响的 MD 模拟系统评估
- **名称**：Systematic MD Assessment of TF Mutants on DNA Binding
- **来源局限/观察**：本文仅对 top 结合配体做了 MD 验证，未系统评估突变效应；TF 致病突变对 DNA 结合的影响通常通过实验逐点验证，效率低
- **核心假设**：MD 模拟的 RMSF 变化和结合自由能可以区分致病突变与中性突变对 TF-DNA 结合的影响
- **初步方法**：选取一个 TF（如 p53、MYC），对其 DBD 中的所有癌症相关突变进行 MD 模拟（每个 100 ns），计算结合自由能（MM-PBSA）和 DBD 区域 RMSF；与 ClinVar 注释比较
- **验证方式**：ROC 曲线评估 MD 指标区分致病/良性的能力
- **创新状态**：unverified

### 候选 3：TF-DNA 结合口袋的几何深度学习表征
- **名称**：Geometric Deep Learning for TF-DNA Binding Pocket Characterization
- **来源局限/观察**：本文通过残基互作分析推断结合口袋特征，但方法依赖人工观察；TF 的 DBD 结构多样，需要自动化表征方法
- **核心假设**：TF 的 DNA 结合口袋的几何特征（形状、静电势、疏水性）可以预测其 DNA 结合特异性
- **初步方法**：使用三维 CNN 或图神经网络（如 GNN）对 TF-DBD 结构进行编码，预测其 DNA 结合基序（motif）；训练数据来自 CIS-BP 和 JASPAR
- **验证方式**：预测的 motif 与实验测定的 motif 之间的 Tomtom 相似性评分
- **创新状态**：unverified

### 候选 4：PAH 类环境污染物对 TF-DNA 结合的干扰机制研究
- **名称**：Environmental PAH Interference with TF-DNA Binding
- **来源局限/观察**：本文发现 PAH 可结合 TLR4 激活炎症通路，但未探讨 PAH 是否可直接干扰下游 TF（如 NF-κB）的 DNA 结合；PAH 的芳香环结构可能插入 TF-DNA 界面
- **核心假设**：PAH 分子可通过插入 TF-DNA 结合界面或竞争 DNA 结合口袋来干扰 TF-DNA 互作
- **初步方法**：对 NF-κB p50-DNA 复合物（PDB 1NFK）进行 PAH 分子的对接，评估 PAH 是否可结合在 p50-DNA 界面；对 top 候选做 MD 模拟验证干扰稳定性
- **验证方式**：计算 PAH 结合 p50-DNA 复合物与 p50 单独的结合能差异；预测干扰热点残基
- **创新状态**：unverified

### 候选 5：TF-DNA 结合动力学的增强采样模拟
- **名称**：Enhanced Sampling of TF-DNA Binding/Unbinding Pathways
- **来源局限/观察**：本文的 MD 模拟仅 10 ns 且为粗粒化，无法捕捉 TF-DNA 结合/解离的完整路径；TF-DNA 结合是动态过程，静态结构不足以描述
- **核心假设**：使用增强采样方法（如 metadynamics、umbrella sampling）可以揭示 TF-DNA 结合的自由能景观和关键中间态
- **初步方法**：选取一个 TF-DNA 体系，使用 Well-Tempered Metadynamics 以 DNA 与 DBD 的距离为集体变量，计算结合自由能剖面；识别结合路径上的关键残基
- **验证方式**：与实验测定的结合常数（Kd）比较；与突变实验数据交叉验证
- **创新状态**：unverified