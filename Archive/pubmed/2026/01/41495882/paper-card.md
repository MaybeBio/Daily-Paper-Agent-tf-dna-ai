## 01 基本信息
- **标题**：A structure-guided approach to noncoding variant evaluation for transcription factor binding using AlphaFold 3
- **作者**：Gerasimavicius, Lukas; Biddie, Simon C; Marsh, Joseph A
- **单位**：未提供（推测为 University of Edinburgh，依据基金信息，但原文未明确列出）
- **期刊/平台**：Nucleic Acids Research
- **年份**：2026
- **论文类型**：方法学/基准测试研究
- **领域**：计算结构生物学 × 调控基因组学 × 蛋白质-DNA 互作
- **关键词**：AlphaFold 3, transcription factor, noncoding variant, SNP-SELEX, FoldX, ipTM, TF-DNA binding
- **DOI/arXiv 号**：10.1093/nar/gkaf1417
- **代码**：未提供
- **数据**：OSF 数据库，https://doi.org/10.17605/OSF.IO/UZKG5
- **阅读日期**：2026-05-13
- **在该课题方向中的位置**：本文是「TF–DNA 结合机制 × AI 结构预测」交叉方向的代表性工作，首次系统评估 AF3 在非编码 SNV 功能预测中的表现，提出 ΔipTM 作为无需额外训练的替代指标，并与 FoldX 物理模拟形成互补。对「AI 预测结构 + 物理能量评估」的混合范式提供了基准证据。

## 02 一句话总结
本文使用 AlphaFold 3 建模六个转录因子（SPIB、ELK3、ETV4、SF-1、PAX5、MEIS2）与参考/替代等位基因 DNA 的复合物结构，结合 FoldX 能量计算和 AF3 的 ipTM 分数，评估非编码 SNV 对 TF 结合的影响，发现 ΔipTM 在区分差异结合位点方面总体优于能量指标，但性能因 TF 而异，且与 deltaSVM 等序列方法相比准确率较低但无需训练数据。

## 03 研究问题
- **具体问题**：能否利用 AF3 预测的 TF–DNA 复合物结构，通过结构/物理指标评估非编码 SNV 对 TF 结合的影响？
- **为什么重要**：超过 90% 的 GWAS 相关 SNV 位于非编码区，其中约 70% 可能影响 TF 结合。现有序列方法（如 deltaSVM）依赖大量实验训练数据，对缺乏数据的 TF 和罕见变异无能为力。结构方法有望提供无需训练的通用评估框架。
- **现有方法不足**：序列方法（PWM、deltaSVM、深度学习）依赖训练数据且缺乏机制解释；传统结构方法受限于 TF–DNA 复合物结构数据的稀缺；AF3 虽能预测复合物结构，但其在非编码变异评估中的系统验证尚属空白。
- **精确研究问题**："Can AlphaFold 3-predicted TF–DNA complex structures, combined with physics-based energy calculations (FoldX) and deep learning confidence scores (ipTM), accurately identify noncoding SNVs that alter transcription factor binding, as benchmarked against SNP-SELEX data?"

## 04 背景与发展脉络
*注：以下脉络基于本文框架，部分经外部核验（标注）。*

1. **实验方法时代**：ChIP-seq、SELEX、蛋白结合微阵列等高通量实验可鉴定 TF 结合位点，但成本高、通量有限，难以覆盖所有 SNV。
2. **序列基序方法**：PWM（如 JASPAR）基于位置权重矩阵预测结合位点，简单但忽略序列间依赖性和结构背景。
3. **机器学习/深度学习时代**：deltaSVM（gapped k-mer）、DeepSEA 等方法利用大规模实验数据训练，在常见 TF 上表现优异，但依赖训练数据质量与覆盖度，对稀有 TF 和新型变异泛化能力有限。
4. **结构预测突破**：AlphaFold 2 在蛋白质结构预测上达到实验精度；AlphaFold 3（2024）扩展至蛋白质-核酸复合物，使大规模 TF–DNA 结构建模成为可能。
5. **本文位置**：首次系统评估 AF3 + FoldX 在非编码 SNV 功能预测中的表现，提出 ΔipTM 作为无需额外训练的替代指标，并揭示 TF 特异性性能差异。属于「AI 结构预测 + 物理能量评估」混合范式的早期基准工作。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 序列方法依赖训练数据 | deltaSVM 仅对 94/533 个 TF 有高质量模型 | 需要大规模 HT-SELEX 实验数据，成本高且覆盖有限 | Results 节："only 94 made it into the high-confidence category" |
| AF3 对核酸复合物预测精度有限 | 部分 TF（PAX5、MEIS2）性能差 | PDB 中 TF–DNA 复合物结构数据稀缺，训练样本不足 | Discussion 节："limitations of structure model prediction for complexes containing nucleic acids are well known" |
| 单次 AF3 预测的随机性 | 单 seed 预测可能错过真实结合位点 | AF3 对同一序列可能预测多个可能的结合位点，单次采样无法覆盖 | Discussion 节："single-seed predictions do not reveal whether AF3 can capture the probabilistic binding site landscape" |
| 能量指标噪声大 | FoldX 指标（ΔΔGsym、ΔInterface）性能不稳定 | 结构松弛和侧链调整引入额外噪声 | Results 节："provide additional noise through structure relaxation and sidechain adjustment" |
| 多结构域 TF 建模困难 | PAX5 等含多个 DNA 结合域的 TF 预测不准 | 多结构域蛋白的构象灵活性及域间协同难以建模 | Discussion 节："PAX5 and similar proteins which have multiple DNA-interacting domains" |

## 06 核心思想
1. **表面方法**：用 AF3 对每个 SNV 的参考/替代等位基因序列分别建模 TF–DNA 复合物，提取三种指标——FoldX 对称 ΔΔG（ΔΔGsym）、FoldX 界面能量差（ΔInterface）、AF3 置信度差（ΔipTM），并与 SNP-SELEX 实验数据对比验证。
2. **核心洞察**：AF3 的 ipTM 分数虽然是为评估整体模型质量而设计，但其对序列变异的敏感性使其天然编码了 TF 的 DNA 序列偏好信息。ΔipTM 作为「零成本」的深度学习副产品，无需额外训练或能量计算，即可在多数 TF 上达到与 FoldX 相当甚至更好的预测性能。这表明 AF3 在训练过程中已隐式学习了 TF–DNA 结合特异性的表征。
3. **可能的普适教训** [Analysis]：深度学习模型的置信度分数（如 ipTM、pLDDT）可能包含超出模型质量评估的生物学信息，可作为「免费」的预测指标。在缺乏专门训练数据的场景下，利用预训练模型的内部表征或置信度输出，可能比从头训练或物理模拟更高效。此外，结构方法不应被视为序列方法的替代，而是互补——两者结合可兼顾准确性与可解释性。

## 07 方法总览
- **输入**：六个 TF 的参考/替代等位基因 40-bp DNA 寡核苷酸序列（来自 SNP-SELEX 数据），TF 全长或 DBD 氨基酸序列
- **输出**：每个 SNV 的三种结构指标（ΔΔGsym、ΔInterface、ΔipTM），以及分类预测（是否差异结合）
- **模块**：
  1. 数据获取与筛选：从 GVATdb 获取 SNP-SELEX 数据，提取 40-bp 序列
  2. AF3 结构预测：本地运行 AF3（单 seed），生成 TF–DNA 复合物模型
  3. 结构转换：BeEM 将 CIF 转为 PDB 格式
  4. FoldX 能量计算：RepairPDB 预处理 → BuildModel（对称 ΔΔG）→ AnalyseComplex（ΔInterface）
  5. 指标提取：从 AF3 JSON 提取 ipTM，计算 ΔipTM；FreeSASA 计算 DNA SASA 相关性
  6. 基准评估：与 SNP-SELEX 的 PBS 值进行相关性和分类性能分析
- **反馈回路**：无显式训练/反馈回路；方法为前馈式预测流程
- **文字流程**：从 SNP-SELEX 数据库获取 40-bp 参考/替代序列对 → 对每个序列对运行 AF3 预测 TF–DNA 复合物结构 → 用 BeEM 转换格式 → 对结构执行 FoldX RepairPDB 和 BuildModel/AnalyseComplex 计算能量指标 → 从 AF3 输出提取 ipTM 并计算差值 → 用 FreeSASA 计算 DNA 溶剂可及表面积相关性 → 将所有指标与 SNP-SELEX 的 PBS 值进行统计比较和 ROC/PR 分析

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AF3 结构预测 | 生成 TF–DNA 复合物三维结构 | 提供结构基础，使下游能量计算和置信度评估成为可能 | 输入：TF 序列 + DNA 序列；输出：复合物结构 + ipTM 分数 | Results 图 1a：ΔipTM 显著区分偏好组 | 移除后整个框架无法运行；预期影响：无结构信息可用 |
| FoldX BuildModel（ΔΔGsym） | 计算 SNV 引起的结合自由能变化 | 提供物理化学层面的变异效应评估 | 输入：参考/替代结构；输出：对称 ΔΔG 值 | Results 图 1a：ΔΔGsym 区分偏好组但分布偏移 | 预期影响：失去物理能量视角，但 ΔipTM 可部分补偿 |
| FoldX AnalyseComplex（ΔInterface） | 计算界面相互作用能量差异 | 直接评估蛋白-DNA 界面稳定性变化 | 输入：参考/替代结构；输出：界面能量差 | Results 图 1a：ΔInterface 区分偏好组 | 预期影响：与 ΔΔGsym 部分冗余，移除后影响较小 |
| ΔipTM 提取 | 从 AF3 输出提取置信度差值 | 利用深度学习内部表征，无需额外计算 | 输入：AF3 JSON 文件；输出：ipTM 差值 | Results 图 1a、2a：ΔipTM 为最佳通用指标 | 预期影响：失去最强预测指标 |
| DNA SASA 相关性 | 检测 AF3 预测的结合位点是否发生位移 | 识别 SNV 引起的结合位点转移 | 输入：参考/替代结构；输出：SASA 向量 Spearman 相关 | Results 图 1c：pbSNP 显示较低相关性 | 预期影响：失去对结合位点位移的检测能力 |
| deltaSVM 基准 | 与序列方法对比 | 评估结构方法的相对优劣 | 输入：序列；输出：预测分数 | Results 图 S9：deltaSVM 在三个 TF 上近乎完美 | 预期影响：无法直接对比结构方法的相对性能 |

## 09 关键公式符号

**公式 1：对称 ΔΔG（ΔΔGsym）**
ΔΔGsym = (ΔΔG_ref→alt + ΔΔG_alt→ref) / 2

- ΔΔG_ref→alt：从参考结构出发，将参考等位基因突变为替代等位基因引起的自由能变化（FoldX BuildModel 正向突变）
- ΔΔG_alt→ref：从替代结构出发，将替代等位基因突变为参考等位基因引起的自由能变化（反向突变）
- 对称化处理用于减少方向依赖性和结构初始化偏差

**公式 2：界面能量差（ΔInterface）**
ΔInterface = Interface_alt − Interface_ref

- Interface_ref：参考等位基因结构的 FoldX AnalyseComplex 界面能量
- Interface_alt：替代等位基因结构的界面能量
- 正值表示替代等位基因降低结合亲和力

**公式 3：ΔipTM**
ΔipTM = ipTM_ref − ipTM_alt

- ipTM_ref：参考等位基因复合物的 AF3 界面预测模板建模分数
- ipTM_alt：替代等位基因复合物的 ipTM 分数
- 正值表示参考等位基因更稳定结合

**公式 4：ΔΔGmax(ipTM)**
ΔΔGmax(ipTM) = 从 ipTM 较高的模型中计算的 ΔΔG 值

- 选择每个等位基因对中 ipTM 更高的模型进行 FoldX 突变计算
- 旨在减少 AF3 结合位点预测错误的影响

## 10 实验设计与证据链
- **数据集**：SNP-SELEX 数据（来自 GVATdb），六个 TF：SPIB、ELTV4、ELK3（ETS 家族）、SF-1/NR5A1（核受体家族）、PAX5（PAX 家族）、MEIS2（TALE 同源异型盒家族）
- **规模**：75,134 个 AF3 复合物模型（覆盖所有参考/替代等位基因对）
- **指标**：PBS（preferential binding score）作为实验金标准；ΔΔGsym、ΔInterface、ΔipTM、ΔΔGmax(ipTM)、DNA SASA cor. 作为预测指标
- **基准**：deltaSVM（仅对 SPIB、ELK3、SF-1 有高质量模型）
- **评测协议**：Spearman 相关分析（全数据集）；ROC/PR 曲线区分 pbSNP vs non-pbSNP；方向分类（参考偏好 vs 替代偏好）；按 TF 分层分析

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| 指标分布分析 | 结构指标能区分 SNP-SELEX 偏好组 | 三个指标在 ref/alt/non-pbSNP 三组间比较 | 所有指标显著区分三组（p<0.05） | 结构方法可捕获 SNV 对 TF 结合的影响 | 不能证明因果性，仅相关性 | Results 图 1a |
| 全数据集相关分析 | 结构指标与 PBS 值相关 | Spearman 相关，全数据集 | 弱到中等相关（具体 r 值未提供） | 结构指标与实验偏好存在一致性 | 相关强度不足以做精确预测 | Results 节 |
| pbSNP vs non-pbSNP 分类 | 结构指标能识别差异结合位点 | ROC/PR 曲线，ΔipTM vs FoldX 指标 | ΔipTM AUC=0.685（最优）；ΔΔGmax(ipTM) 次优 | ΔipTM 是通用性最好的结构指标 | 分类性能远低于 deltaSVM | Results 图 2a |
| 方向分类 | 结构指标能判断偏好方向 | 仅 pbSNP 内，ref vs alt 偏好 | ΔipTM AUC=0.792 | 结构指标可判断偏好方向 | 存在 TF 特异性偏差 | Results 图 3a |
| 按 TF 分层 | 性能是否 TF 依赖 | 各 TF 单独分析 | SPIB、SF-1 性能好；PAX5、MEIS2 差 | 性能高度 TF 依赖 | 不能推广到所有 TF | Results 图 2b、S1 |
| DNA SASA 相关分析 | AF3 预测结合位点位移与 SNV 相关 | pbSNP vs non-pbSNP 的 SASA 相关分布 | pbSNP 显示更多低相关（位点位移） | AF3 可预测 SNV 引起的结合位点变化 | 位点位移不直接等于功能效应 | Results 图 1c、S3 |
| 临床变异验证 | 结构指标能复现已知临床变异效应 | 6 个已发表病例（PAX6、FOXE3/USF2A-USF1、NKX2-5×2、GATA3/LMO1、HOXB13/RFX6） | 5/6 病例至少两个指标方向正确 | 结构方法对临床变异有潜在应用价值 | 样本量小，不能推广 | Results 图 5a-f |
| deltaSVM 对比 | 结构方法 vs 序列方法 | 三个 TF（SPIB、ELK3、SF-1） | deltaSVM 近乎完美（AUC>0.9），结构方法 AUC 0.6-0.8 | 序列方法在数据充足时更优 | 结构方法在无数据 TF 上仍有价值 | Results 图 S9 |

## 11 结论正确解读
- **任务范围**：仅评估 SNV 对 TF–DNA 结合的影响，不涉及染色质可及性、表观遗传修饰、共调控因子等体内复杂因素。
- **Oracle/真值输入**：SNP-SELEX 数据是体外实验，排除了体内染色质环境；deltaSVM 模型本身也基于 HT-SELEX 数据训练，存在数据重叠。
- **端到端状态**：非端到端——AF3 结构预测 + FoldX 能量计算是串联流程，误差会累积；ΔipTM 虽为端到端副产品，但未针对该任务优化。
- **算力成本**：75,134 个 AF3 模型需要大量 GPU 计算（单 RTX 6000 Ada），全基因组扩展不现实。
- **历史数据依赖**：AF3 训练数据包含 PDB 中的 TF–DNA 复合物，对某些 TF 家族可能存在数据偏差。
- **模型依赖**：结果基于 AF3 特定版本，后续版本更新可能改变性能。
- **最难情形**：PAX5（多结构域）、MEIS2（协同结合）等复杂结合模式的 TF 预测性能差。
- **群体/领域边界**：仅测试 6 个 TF，不能推广到所有 1600+ 人类 TF；仅测试 SNP-SELEX 的 40-bp 寡核苷酸场景。
- **不确定性**：ΔipTM 与 PBS 的相关性弱到中等，不能作为独立诊断工具；临床变异验证样本量极小（n=6）。
- **有边界的复述**：本文证明 AF3 结构预测 + FoldX/ΔipTM 指标可以在体外 40-bp 场景下部分复现 SNP-SELEX 的 TF 结合偏好，但性能远低于有充足训练数据的序列方法，且高度依赖 TF 类型。该方法应视为序列方法的补充而非替代，适用于缺乏训练数据的 TF 或需要机制解释的场景。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 计算资源限制 | 仅测试 6 个 TF，无法覆盖全部 TF 类型 | 扩展至更多 TF，利用更高效的采样策略 | Discussion 节 |
| 单 seed 预测 | 单次 AF3 预测可能错过真实结合位点 | 多 seed 运行以评估预测变异性 | Discussion 节："Performing multiseed AF3 runs could provide an auxiliary approach" |
| 忽略水分子 | 未考虑水分子在 TF–DNA 相互作用中的介导作用 | 纳入显式水分子模拟 | Discussion 节："does not take into account the contribution from water molecules" |
| 体外场景简化 | SNP-SELEX 无法反映体内染色质状态、DNA 甲基化、协同结合 | 结合 ChIP-seq 等体内数据进行验证 | Discussion 节："does not account for chromatin state, DNA methylation, or cooperative interactions" |
| 性能低于序列方法 | 结构方法准确率不如 deltaSVM | 与序列方法集成，构建混合框架 | Discussion 节："Hybrid frameworks that integrate structural physics-based scores with sequence-based predictors" |
| 单结构域建模 | 仅建模单体 TF 或 DBD，未考虑多聚体协同结合 | 扩展至多聚体复合物建模 | Discussion 节："extending to homomeric and heteromeric TF complexes" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| ΔipTM 性能最优但机制不明 | ΔipTM 可能反映的是 AF3 对序列变化的敏感性而非真实的结合亲和力变化 | 如果 ΔipTM 仅反映模型噪声，则其预测能力可能无法泛化到新 TF | 在未见过的 TF 家族上进行盲测；比较 ΔipTM 与 AF3 训练数据覆盖度的关系 | Results 图 2a：ΔipTM AUC=0.685，但作者未解释其生物学基础 |
| 临床变异验证存在选择偏差 | 6 个病例均为已发表、实验验证的变异，可能偏向于效应显著的案例 | 真实临床场景中效应量分布未知，可能高估方法实用性 | 在 ClinVar 等数据库中系统收集未经验证的变异进行前瞻性测试 | Results 图 5a-f：仅 6 例，且均为已知病例 |
| deltaSVM 对比不公平 | deltaSVM 模型本身使用 HT-SELEX 数据训练，而 SNP-SELEX 与 HT-SELEX 数据高度相关 | 对比可能高估序列方法的优势 | 使用独立于训练数据的验证集；测试结构方法在 deltaSVM 无模型 TF 上的表现 | Results 图 S9：deltaSVM 在三个 TF 上近乎完美 |
| 单 seed AF3 预测的随机性未量化 | 作者承认单 seed 局限，但未提供多 seed 变异性数据 | 如果 AF3 预测对 seed 高度敏感，则所有指标都不可靠 | 对子集运行多 seed 并报告指标分布 | Discussion 节：作者仅建议多 seed，未提供数据 |
| 未报告 AF3 预测成功率 | 部分序列可能无法产生有效复合物模型，但作者未报告失败率 | 如果失败率高，方法实用性受限 | 报告每个 TF 的模型生成成功率及失败原因 | 未提供 |
| 与现有方法缺乏系统集成 | 未测试结构指标与序列方法（如 deltaSVM）的互补性 | 混合方法可能优于任一单独方法 | 构建结构+序列集成模型，比较与单独方法的性能 | Discussion 节：仅提出未来方向，未实施 |

## 14 学到什么
**Agent 提炼的知识候选**

1. **ΔipTM 作为「免费」预测指标**：AF3 的 ipTM 分数差异（ΔipTM）无需额外计算即可预测 TF 结合偏好变化。可迁移至本课题：在评估 TF–DNA 结合时，优先检查 AF3 输出的 ipTM 差异，而非仅依赖结构坐标。

2. **对称 ΔΔG 设计**：ΔΔGsym 取正向和反向突变的平均值，减少结构初始化偏差。可迁移至本课题：在使用 FoldX 或其他能量函数评估 TF–DNA 结合时，采用对称化策略提高稳健性。

3. **TF 特异性性能差异**：结构方法对某些 TF 家族（ETS、核受体）有效，对多结构域/协同结合 TF（PAX5、MEIS2）失效。可迁移至本课题：在设计 TF–DNA 结合预测流程时，需根据 TF 家族特征选择建模策略（单体 vs 多聚体、全长 vs DBD）。

4. **DNA SASA 相关性作为结合位点位移指标**：通过比较参考/替代等位基因模型的 DNA 溶剂可及表面积，可检测 AF3 预测的结合位点位移。可迁移至本课题：在分析 SNV 效应时，不仅关注结合亲和力变化，还应检查结合位点是否发生位移。

5. **结构方法定位为「补充」而非「替代」**：作者明确将结构方法定位为序列方法的补充，适用于缺乏训练数据的场景。可迁移至本课题：在开发 TF–DNA 结合预测工具时，考虑混合架构——序列方法提供高精度预测，结构方法提供机制解释和泛化能力。

6. **单 seed 局限与多 seed 策略**：单次 AF3 预测可能错过真实结合位点，多 seed 运行可提供预测变异性估计。可迁移至本课题：在使用 AF3 进行 TF–DNA 结构预测时，至少运行 3-5 个 seed 并报告一致性。

7. **临床变异验证的「定性共识」策略**：作者采用多指标方向一致性（而非单一指标阈值）来判断临床变异效应。可迁移至本课题：在评估致病性非编码变异时，采用多指标共识策略提高鲁棒性。

## 15 与已有知识连接
- **AlphaFold 3 能力边界**：与 Abramson et al. (2024, Nature) 的 AF3 原始论文连接——AF3 虽能预测蛋白-核酸复合物，但作者指出其核酸复合物预测精度受限于 PDB 训练数据。本文是 AF3 在非编码变异评估中的首次系统验证。
- **SNP-SELEX 数据集**：与 Yan et al. (2021, Nat Commun) 的 SNP-SELEX 方法原始论文连接——本文使用其 GVATdb 数据库作为金标准，该数据已被 deltaSVM 等序列方法使用。
- **deltaSVM 方法**：与 Lee et al. (2015, Nat Genet) 的 deltaSVM 原始论文连接——本文将其作为序列方法代表进行对比，并指出其依赖 HT-SELEX 训练数据的局限。
- **FoldX 在蛋白-DNA 互作中的应用**：与 Schymkowitz et al. (2005, Nucleic Acids Res) 的 FoldX 原始论文连接——本文扩展了 FoldX 在 DNA 突变评估中的应用，此前主要用于蛋白质突变。
- **结构变异预测的早期工作**：与 Srivastava et al. (2021) 等使用 Rosetta 评估 TF–DNA 变异的工作连接——本文使用 AF3 替代实验结构，解决了结构数据稀缺问题。
- **ipTM 指标的扩展应用**：与 AF3 原始论文中 ipTM 作为复合物预测置信度指标的连接——本文首次将 ipTM 差异（ΔipTM）用作变异效应预测指标，属于「模型置信度作为生物学信号」的新思路。
- **TF 结合特异性的结构基础**：与 Jolma et al. (2013, Genome Res) 的 TF 家族 DNA 结合偏好分类连接——本文的 TF 选择（ETS、核受体、PAX、TALE 家族）基于该分类，并验证了单体 vs 多聚体结合对结构预测的影响。

## 16 研究想法
**Agent 生成的研究候选**

1. **多 seed AF3 集成预测框架**
   - **来源局限/观察**：作者使用单 seed 预测，承认可能错过真实结合位点
   - **核心假设**：多 seed AF3 预测的 ipTM 分布（而非单点估计）能更稳健地预测 TF 结合偏好
   - **初步方法**：对每个 SNV 运行 10-20 个 seed，提取 ipTM 均值、方差、最大值等统计量，训练轻量级分类器
   - **验证方式**：在 SNP-SELEX 全数据集上比较单 seed vs 多 seed 的 AUC
   - **创新状态**：unverified

2. **结构-序列混合预测模型**
   - **来源局限/观察**：结构方法（AUC 0.6-0.8）远低于序列方法 deltaSVM（AUC>0.9），但结构方法无需训练数据
   - **核心假设**：结构指标（ΔipTM、ΔΔG）与序列特征（k-mer、motif score）提供互补信息，混合模型可超越任一单独方法
   - **初步方法**：将 ΔipTM、ΔΔGsym、ΔInterface 作为特征，与 deltaSVM 分数或 PWM 分数拼接，训练逻辑回归或梯度提升模型
   - **验证方式**：在 SNP-SELEX 数据上交叉验证，比较混合模型与单独方法的 AUC
   - **创新状态**：partially checked（作者在 Discussion 中提出类似方向，但未实施）

3. **多聚体 TF–DNA 复合物建模**
   - **来源局限/观察**：MEIS2（协同结合）性能差，作者归因于单体建模忽略了协同效应
   - **核心假设**：对已知形成二聚体/多聚体的 TF，建模多聚体复合物可提高预测性能
   - **初步方法**：选择 10-20 个已知二聚体 TF，使用 AF3 建模同源/异源二聚体与 DNA 的复合物，比较单体 vs 二聚体模型的 ΔipTM 预测性能
   - **验证方式**：与 SNP-SELEX 数据对比，检验二聚体模型是否改善 MEIS2 等协同结合 TF 的预测
   - **创新状态**：unverified

4. **水分子介导的 TF–DNA 相互作用分析**
   - **来源局限/观察**：作者承认未考虑水分子在 TF–DNA 互作中的作用
   - **核心假设**：在 AF3 预测结构上执行显式水分子分子动力学模拟，可揭示 SNV 通过水分子网络影响结合的机制
   - **初步方法**：对 10-20 个 SNP-SELEX 阳性位点执行短时 MD 模拟（100-500 ns），分析水分子驻留时间和氢键网络变化
   - **验证方式**：比较 MD 衍生的水分子指标与 SNP-SELEX PBS 值的相关性
   - **创新状态**：unverified

5. **AF3 结合位点位移作为功能预测指标**
   - **来源局限/观察**：作者发现 pbSNP 常伴随 AF3 预测结合位点位移，但未系统利用
   - **核心假设**：SNV 引起的结合位点位移程度（通过 DNA SASA 相关或结构比对量化）可独立预测功能效应
   - **初步方法**：开发结合位点位移量化指标（如 DNA 接触图谱的 Jensen-Shannon 距离），与 ΔipTM 联合使用
   - **验证方式**：在 SNP-SELEX 数据上评估位移指标的独立预测能力
   - **创新状态**：partially checked（作者展示了位移现象，但未开发为预测指标）

6. **无训练数据的 TF 结合预测框架**
   - **来源局限/观察**：deltaSVM 仅覆盖 94/533 个 TF，大量 TF 缺乏训练数据
   - **核心假设**：AF3 结构预测 + FoldX 能量计算可为无训练数据的 TF 提供「零样本」结合预测
   - **初步方法**：选择 20-30 个无 deltaSVM 模型的 TF，用 SNP-SELEX 数据验证结构方法的预测性能，建立「结构优先」预测流程
   - **验证方式**：与现有 ChIP-seq 或 HT-SELEX 数据对比
   - **创新状态**：unverified