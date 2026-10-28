## 01 基本信息
- **标题**：Factorbook: an updated catalog of transcription factor motifs and candidate regulatory motif sites
- **作者与单位**：Pratt, Henry E; Andrews, Gregory R; Phalke, Nishigandha; Huey, Jack D; Purcaro, Michael J; van der Velde, Arjan; Moore, Jill E; Weng, Zhiping（单位未在摘要中提供，Weng 实验室为 UMass Chan Medical School，但摘要未明确，标注为未提供）
- **期刊/预印本平台**：Nucleic Acids Research
- **年份**：2021-11-11（在线发表）
- **论文类型**：数据库资源描述（Database Resource）
- **领域**：转录调控基因组学、TF–DNA 结合机制、生物信息学数据库
- **关键词**：transcription factor motifs, ChIP-seq, HT-SELEX, cCREs, convolutional neural networks, LD score regression
- **DOI/arXiv 号**：10.1093/nar/gkab1039
- **代码**：未提供（仅提及 Docker 镜像与 GitHub 脚本用于 LD score regression 分析，但未给出具体链接）
- **数据**：https://factorbook.org/downloads
- **阅读日期**：未提供
- **该文在课题方向中的位置**：本文是 TF–DNA 结合机制领域的核心资源型工作，提供约 750 个 TF 的 motif 目录（来自 ChIP-seq 的 MEME 流程与 HT-SELEX 的 ZMotif 深度学习流程），并将 motif 实例定位到 cCREs 与 rDHSs 中，附带保守性、DNase 可及性等注释。对「TF–DNA 结合机制 × AI/物理模拟」课题而言，本文提供：(1) 大规模 motif 训练/验证数据集；(2) 深度学习（CNN）用于 motif 发现的完整流程（ZMotif）；(3) motif 实例的基因组定位与功能注释，可作为结构预测、分子对接或 MD 模拟的候选靶点集。

## 02 一句话总结
本文通过整合 ENCODE Phase II/III 的 ChIP-seq 数据（MEME 流程）与 HT-SELEX 数据（ZMotif 深度学习流程），构建了覆盖约 750 个人类/小鼠 TF 的 motif 目录，并将 motif 实例定位到 cCREs 与 rDHSs 中，提供保守性、染色质可及性等注释，同时支持 SNP 注释与遗传力富集分析。

## 03 研究问题
- **具体问题**：如何系统性地构建一个全面、可机器学习的 TF motif 目录，并将 motif 实例定位到候选调控元件中，以支持下游功能注释与遗传变异解读？
- **为什么重要**：人类基因组中约 1600 个 DNA 结合 TF 通过识别特定 motif 调控基因表达；理解 TF–DNA 结合机制需要高质量的 motif 模型及其基因组定位。现有数据库（如 HOCOMOCO、JASPAR）覆盖有限，且缺乏与调控元件注释的整合。
- **现有方法不足**：HOCOMOCO 和 JASPAR 主要依赖已发表的 motif，覆盖不完整；UniPROBE 仅限体外实验；CisBP 依赖推断；缺乏与 ENCODE cCRE 注册表的系统整合，且未提供深度学习可直接使用的 motif 格式。
- **精确研究问题**：Can we build a comprehensive TF motif catalog from ENCODE ChIP-seq and HT-SELEX data that covers ~750 TFs, integrates with cCRE annotations, and provides machine-learning-ready motif models for downstream regulatory genomics analysis?

## 04 背景与发展脉络
- **阶段一：体外 motif 测定**（HT-SELEX、PBM 等）：代表性方法为 HT-SELEX (2)、UniPROBE (7)。优点：直接测量 TF 结合特异性；局限：体外条件可能不代表体内结合环境，覆盖 TF 有限。
- **阶段二：体内 ChIP-seq motif 发现**：代表性方法为 MEME 套件 (20)。优点：反映体内结合环境；局限：依赖 ChIP-seq 质量，motif 可能受共结合因子影响。
- **阶段三：综合数据库整合**：HOCOMOCO (5)、JASPAR (6)、CisBP (8)。优点：整合多来源数据；局限：更新滞后，覆盖不全，缺乏与调控元件注释的整合。
- **阶段四（本文位置）**：深度学习 motif 发现（ZMotif）+ 大规模 ChIP-seq 整合 + cCRE 定位 + 遗传力分析。本文主张：通过双流程（MEME + ZMotif）构建更全面的 motif 目录，并整合 cCRE 注册表提供基因组定位与功能注释。
- **脉络标注**：以上脉络为「经外部核验」——HOCOMOCO、JASPAR、UniPROBE、CisBP 均为公开数据库，其方法特点与局限在文献中有广泛记载。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| motif 覆盖不全 | 现有数据库（HOCOMOCO、JASPAR）未覆盖所有 TF，尤其缺乏 'likely sequence-specific factors' 的 motif | 现有数据库依赖已发表数据，更新滞后 | Introduction 节：现有目录覆盖有限，本文新增 101 个此前无 motif 的 'likely sequence-specific factors' |
| 缺乏与调控元件注释的整合 | 现有数据库仅提供 motif 模型，不提供基因组定位 | 未与 ENCODE cCRE 注册表系统整合 | Introduction 节：本文利用 cCRE 注册表提供全基因组候选 TF 结合位点 |
| 深度学习模型不可直接复用 | 现有 motif 格式（PWM）不适合直接作为深度学习模型输入 | 缺乏将 motif 模型转化为深度学习可加载格式的机制 | Overview 节：ZMotif 的滤波器以 Numpy 格式提供，可直接用于迁移学习 |
| 体内外数据不一致 | ChIP-seq 与 HT-SELEX 得到的 motif 可能不同 | 体内结合受染色质环境、共结合因子影响 | 未提供（作者未直接讨论此痛点，[Analysis] 推断） |
| 大规模数据计算负担 | 数万 ChIP-seq 数据集需要高效处理 | 计算资源与算法效率限制 | 未提供（作者未直接讨论，[Analysis] 推断） |

## 06 核心思想
1. **表面方法**：构建双流程 motif 发现管道——(1) 对 ENCODE Phase I-III 的 ChIP-seq 数据应用 MEME 进行 de novo motif 发现；(2) 对 HT-SELEX 数据应用自研 CNN 工具 ZMotif 进行 motif 发现。将两类 motif 整合为统一目录，并用 FIMO 扫描 ChIP-seq peaks 和 cCREs/rDHSs 获得基因组定位。提供 SNP 注释、遗传力分析、保守性与染色质可及性注释。
2. **核心洞察**：将 motif 模型从「静态 PWM」升级为「深度学习可加载的滤波器」，并整合 cCRE 注册表，使 motif 目录不仅描述 TF 结合偏好，还能直接用于：(a) 迁移学习初始化新模型；(b) 全基因组定位候选结合位点；(c) 遗传变异功能解读。这种「模型 + 定位 + 注释」三位一体的设计，使数据库从查询工具升级为分析平台。
3. **可能的普适教训** [Analysis]：在 TF–DNA 结合机制研究中，motif 只是「结合偏好」的近似描述，真正的结合机制涉及三维结构、构象变化、共结合因子竞争等。本文的 motif 目录可作为结构预测（如 AlphaFold 3、RoseTTAFoldNA）和 MD 模拟的候选靶点筛选工具，但 motif 本身不提供结构信息。研究者应将其视为「候选位点注释」而非「结合机制解释」。

## 07 方法总览
- **输入**：(1) ENCODE Phase I-III 的 ChIP-seq 数据（人类 249 个细胞类型、小鼠 38 个细胞类型）；(2) 两个公开 HT-SELEX 数据集 (2,24)；(3) ENCODE cCRE 注册表。
- **输出**：(1) 约 750 个 TF 的 motif 目录（PWM 格式 + ZMotif 滤波器 Numpy 格式）；(2) 全基因组候选 motif 位点（BED 格式）；(3) 每个 motif 的保守性、DNase 可及性、峰中心性等注释；(4) 遗传力富集模型。
- **模块**：
  1. **MEME 管道**：对每个 ChIP-seq 数据集取 top 500 peaks，运行 MEME 发现最多 5 个 motif，经质量过滤（峰中心性、富集度）。
  2. **ZMotif 管道**：自研 CNN 从 HT-SELEX 数据中发现 motif，输出可加载的滤波器。
  3. **UMAP 聚类**：对 motif 进行降维聚类，辅助识别冗余和新颖 motif。
  4. **FIMO 扫描**：在 ChIP-seq peaks 和 cCREs/rDHSs 中扫描 motif 实例。
  5. **注释模块**：保守性（phyloP）、DNase-seq/ATAC-seq 可及性、峰中心性。
  6. **SNP 注释模块**：用户输入 rsID，实时注释 SNP 对 motif 的潜在影响。
  7. **遗传力分析模块**：基于 motif 位点构建 LD score regression 模型。
- **训练**：ZMotif 为 CNN，在 HT-SELEX 数据上训练（具体训练细节未在摘要中提供）。
- **反馈回路**：用户可通过 BED 文件上传与 SNP 注释进行交互式分析，结果实时返回。
- **假设**：ChIP-seq peaks 中的 motif 实例代表真实 TF 结合位点；HT-SELEX 的 in vitro 结合特异性可近似 in vivo 结合偏好。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| MEME 管道 | 从 ChIP-seq peaks 中发现 de novo motif | 捕获体内 TF 结合偏好 | 输入：top 500 peaks；输出：PWM motif | 识别 6921 个 motif，覆盖约 750 TF | 失去体内结合信息，仅剩体外数据（预期影响，未实测） |
| ZMotif 管道 | 从 HT-SELEX 中发现 motif，输出深度学习滤波器 | 提供深度学习可直接加载的 motif 模型 | 输入：HT-SELEX reads；输出：Numpy 格式滤波器 | 识别 6700 个 motif | 失去深度学习可迁移的滤波器格式（预期影响，未实测） |
| UMAP 聚类 | 降维可视化 motif 关系 | 识别冗余 motif、发现新颖 motif | 输入：motif 相似性矩阵；输出：2D 投影 | 图 2A、3A | 难以直观评估 motif 新颖性（预期影响，未实测） |
| FIMO 扫描 | 在基因组中定位 motif 实例 | 提供全基因组候选 TF 结合位点 | 输入：PWM + 基因组序列；输出：BED 格式位点 | 识别 1.1 亿个 motif 实例（peaks 内），合并后 672 万 | 失去基因组定位能力（预期影响，未实测） |
| 保守性/可及性注释 | 评估 motif 实例的功能相关性 | 区分功能性结合位点与随机匹配 | 输入：phyloP、DNase-seq/ATAC-seq；输出：注释轨道 | 图 2D-F、4C-D | 失去功能证据支持（预期影响，未实测） |
| SNP 注释模块 | 注释 SNP 对 motif 的潜在影响 | 解读非编码疾病变异 | 输入：rsID + 可选人群；输出：motif 影响排序 | 图 5A-C | 失去变异解读能力（预期影响，未实测） |
| 遗传力分析模块 | 量化 motif 位点的遗传力富集 | 关联 TF 结合与复杂性状 | 输入：GWAS summary statistics；输出：LD score 模型 | 图 5D | 失去性状关联分析能力（预期影响，未实测） |

## 09 关键公式符号
- **FIMO P-value**：用于 motif 扫描的统计显著性阈值，标准为 P < 10⁻⁴（peaks 内），cREs/rDHSs 内更严格为 P < 10⁻⁶（MEME motif）和 P < 10⁻⁵（ZMotif motif），以及 P < 10⁻⁷、P < 10⁻⁸ 的更高严格度版本。
- **phyloP score**：进化保守性评分，用于评估 motif 实例的跨物种保守程度。
- **LD score regression**：分区遗传力富集分析，公式为 E[χ²] = N·Σ_c τ_c·ℓ(c,j) + 1，其中 τ_c 为注释类别 c 的系数，ℓ(c,j) 为 SNP j 在类别 c 的 LD score。文中用于量化 motif 位点对性状遗传力的贡献。
- **峰中心性（peak centrality）**：motif 实例在 ChIP-seq peak 中的位置相对于峰顶的分布，用于评估 motif 是否为真实结合位点。
- **注**：本文为数据库资源论文，未提供新的数学公式；以上为文中使用的标准工具/指标。

## 10 实验设计与证据链
- **数据集**：ENCODE Phase I-III ChIP-seq 数据（人类 249 细胞类型、小鼠 38 细胞类型）；两个公开 HT-SELEX 数据集 (2,24)；ENCODE cCRE 注册表（约 1000+ 细胞类型的 rDHSs）。
- **规模**：694 个人类 + 62 个小鼠转录调控蛋白；MEME 识别 6921 个 motif；ZMotif 识别 6700 个 motif；ChIP-seq peaks 内 1.1 亿个 motif 实例（合并后 672 万）；rDHSs 内 3345 万个 motif 实例（合并后 719 万）。
- **指标**：motif 覆盖率（与 HOCOMOCO/JASPAR 对比）、峰中心性、保守性（phyloP）、DNase 可及性、遗传力富集（LD score regression）。
- **基线**：HOCOMOCO (5)、JASPAR (6) 作为 motif 目录对比基线。
- **评测协议**：将 Factorbook motif 与 HOCOMOCO/JASPAR 对比，评估覆盖率；对 motif 实例计算保守性和 DNase 可及性；用 LD score regression 评估遗传力富集。
- **oracle 输入**：无（本文为资源构建，非预测任务）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| MEME motif 覆盖率 | Factorbook 覆盖超过现有目录 | 与 HOCOMOCO/JASPAR 对比 | 覆盖约 750 TF，包含 101 个此前无 motif 的 'likely sequence-specific factors' | Factorbook 扩展了 motif 目录覆盖 | 覆盖率不代表 motif 质量更高 | Results 图 2B |
| motif 实例保守性 | motif 实例比随机序列更保守 | phyloP 评分对比 | motif 实例显著更保守 | motif 实例具有功能相关性 | 保守性不等于体内结合证据 | Results 图 4C |
| DNase 可及性 | motif 实例处 DNase 信号降低 | DNase-seq 信号对比 | motif 实例处 DNase 切割减少 | 结合 TF 保护 DNA 免受切割 | 保护效应可能由其他蛋白介导 | Results 图 4D |
| 遗传力富集 | motif 位点富集性状遗传力 | LD score regression | 疾病相关细胞类型的 motif 位点富集遗传力 | motif 位点可用于解读 GWAS | 富集不等于因果 | Results 图 5D |
| 峰中心性 | 真实 motif 位于峰顶附近 | 与随机位置对比 | motif 实例集中在峰顶附近 | motif 与 ChIP-seq 峰一致 | 峰中心性受 peak 质量影响 | Results 图 2E |

## 11 结论正确解读
- **任务范围**：本文构建的是 TF motif 目录及基因组定位资源，不涉及 TF–DNA 三维结构、结合动力学或分子机制的直接测量。
- **oracle/真值输入**：无预测任务，无 oracle。motif 的「真实性」依赖于 ChIP-seq 和 HT-SELEX 的实验数据质量。
- **端到端状态**：本文提供的是「数据资源 + 分析工具」，非端到端预测模型。用户需自行下载数据并应用于下游分析。
- **算力成本**：未提供具体算力信息。ZMotif 为 CNN 训练，需要 GPU 资源，但具体成本未披露。
- **历史数据依赖**：依赖 ENCODE Phase I-III 数据质量；HT-SELEX 数据来自两个公开数据集 (2,24)。
- **模型依赖**：MEME 和 ZMotif 的 motif 发现结果受算法参数影响；FIMO 扫描受 P-value 阈值影响。
- **最难情形**：对于结合特异性较弱或依赖共结合因子的 TF，motif 可能不明确；对于在测试细胞类型中不表达的 TF，ChIP-seq 无法捕获其结合位点。
- **群体/领域边界**：主要覆盖人类和小鼠 TF；其他物种需另行查询。
- **不确定性**：motif 实例的保守性和 DNase 保护是间接证据，不直接证明体内结合；遗传力富集是统计关联，非因果。
- **有边界的复述**：本文提供了一个覆盖约 750 个人类/小鼠 TF 的 motif 目录，包含 ChIP-seq 和 HT-SELEX 来源的 motif 模型，并将约 700 万个非重叠 motif 实例定位到 cREs/rDHSs 中，这些位点显示出保守性和 DNase 保护特征，且可用于遗传力富集分析。该资源可作为 TF–DNA 结合机制研究的候选位点注释工具，但不提供结合机制的直接解释。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 数据覆盖有限 | 主要基于 ENCODE Phase I-III 数据，细胞类型覆盖有限 | 随 ENCODE Phase IV 数据发布持续扩展 | Abstract、Planned future expansion 节 |
| motif 来源单一 | 主要依赖 ChIP-seq 和 HT-SELEX，未整合 PBM 等体外数据 | 计划纳入 PBM 衍生的体外 motif 以作比较 | Planned future expansion 节 |
| cCRE 注册表待更新 | 使用当前版本的 cCRE 注册表，后续版本发布后需更新 | 随 ENCODE Phase IV 结束更新 cCRE 目录 | Planned future expansion 节 |
| 未覆盖所有 TF | 部分 TF 可能缺乏 ChIP-seq 或 HT-SELEX 数据 | 持续补充新数据 | 未提供（[Analysis] 推断，作者未明确列出） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| motif 实例数量巨大（1.1 亿） | 大量 motif 实例可能是假阳性，FIMO P < 10⁻⁴ 较宽松 | 影响下游功能注释的准确性 | 用更严格 P 值（如 10⁻⁸）重复分析，比较保守性和 DNase 保护信号 | Results 节：提供了多阈值版本 |
| ChIP-seq motif 可能反映共结合因子偏好 | MEME 从 ChIP-seq peaks 中发现的 motif 可能受共结合因子影响，不完全是 TF 自身特异性 | 影响 motif 的生物学解释 | 与 HT-SELEX 体外 motif 对比，检查一致性 | 未提供（作者未直接讨论） |
| ZMotif 为自研工具，未与现有方法对比 | 缺乏与 DESSO、DeepBind 等现有深度学习 motif 发现工具的基准对比 | 影响 ZMotif 结果的可靠性评估 | 在标准数据集上与现有工具对比 | 未提供（作者标注 manuscript in preparation） |
| 遗传力富集分析依赖 LD score regression 假设 | LD score regression 假设多基因遗传结构，可能不适用于所有性状 | 影响遗传力富集结果的解释 | 用其他方法（如 S-LDSC 的替代实现）交叉验证 | 未提供（作者未直接讨论） |
| 保守性和 DNase 保护是间接证据 | 保守性可能反映中性进化而非功能约束；DNase 保护可能由其他 DNA 结合蛋白介导 | 影响 motif 位点功能注释的可信度 | 用 CRISPR 干扰或报告基因实验验证部分位点 | 未提供（作者未直接讨论） |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **双管道 motif 发现策略**：同时使用传统 MEME（ChIP-seq）和深度学习 CNN（HT-SELEX）进行 motif 发现，可互补体内外数据。迁移到本课题：可借鉴此策略，将结构预测（如 AlphaFold 3）与实验数据（ChIP-seq、SELEX）结合，交叉验证 TF–DNA 结合模式。
2. **深度学习滤波器作为可迁移模型**：ZMotif 输出的滤波器以 Numpy 格式提供，可直接用于迁移学习。迁移到本课题：在构建 TF–DNA 结合预测模型时，可加载这些预训练滤波器作为初始权重，减少训练时间并提高可解释性。
3. **cCRE 定位作为功能注释框架**：将 motif 实例定位到 cREs/rDHSs 中，结合保守性和染色质可及性注释，可区分功能性结合位点与随机匹配。迁移到本课题：在 MD 模拟或对接研究中，可优先选择位于 cREs 且保守的 motif 实例作为候选靶点，提高模拟的生物学相关性。
4. **峰中心性作为 motif 质量指标**：真实 motif 倾向于位于 ChIP-seq 峰顶附近，可作为 motif 质量过滤标准。迁移到本课题：在评估结构预测或对接结果时，可结合 ChIP-seq 峰中心性信息，优先考虑与峰顶一致的候选结合构象。
5. **遗传力富集作为功能验证工具**：通过 LD score regression 评估 motif 位点的遗传力富集，可关联 TF 结合与复杂性状。迁移到本课题：在预测 TF–DNA 结合机制时，可结合 GWAS 数据，优先研究与疾病相关变异重叠的结合位点。
6. **多细胞类型覆盖的重要性**：TF 结合具有细胞类型特异性，数据库覆盖 249 个人类细胞类型。迁移到本课题：在构建结合机制模型时，需考虑细胞类型特异性因素（如染色质状态、共结合因子表达），避免过度泛化。

## 15 与已有知识连接
- **HOCOMOCO (5)**：与本文 motif 目录高度重叠，可交叉验证 motif 质量。本文声称覆盖 HOCOMOCO 中几乎所有 motif，并新增 101 个此前无 motif 的 TF。
- **JASPAR (6)**：与 HOCOMOCO 类似，为 motif 目录的基准对比来源。本文通过 TOMTOM 与 JASPAR 对比。
- **ENCODE cCRE Registry (14)**：本文直接利用该注册表进行 motif 实例定位，是 cCRE 的 TF 结合位点注释层。
- **LD score regression (15)**：本文使用该方法进行遗传力富集分析，该方法由 Bulik-Sullivan 等提出，广泛用于 GWAS 功能注释。
- **DeepBind (11)、Basenji (12)、DeepSEA (13)**：这些深度学习模型预测 TF 结合，本文的 motif 目录可作为其训练数据或可解释性分析工具。
- **AlphaFold 3 / RoseTTAFoldNA**：候选连接方向——本文的 motif 实例可作为结构预测的靶点集，用于预测 TF–DNA 复合物三维结构。
- **分子动力学模拟**：候选连接方向——本文提供的保守 motif 实例可作为 MD 模拟的初始结合位点，研究结合动力学和构象变化。
- **用户已有知识**：若读者熟悉 ENCODE 项目、ChIP-seq 分析、motif 发现算法（MEME、TOMTOM），本文的方法论框架易于理解。

## 16 研究想法
**Agent 生成的研究候选**：

1. **名称**：基于 Factorbook motif 的 TF–DNA 复合物结构预测基准集
   - **来源局限/观察**：Factorbook 提供约 700 万个 motif 实例，但缺乏三维结构信息；AlphaFold 3 等工具可预测 TF–DNA 复合物结构，但缺乏大规模验证基准。
   - **核心假设**：Factorbook 中保守且位于 cREs 的 motif 实例可作为高质量结构预测靶点，预测结构可与实验结构（如 PDB）对比验证。
   - **初步方法**：从 Factorbook 筛选高保守性、高 DNase 保护信号的 motif 实例，提取对应 TF 和 DNA 序列，用 AlphaFold 3 预测复合物结构，与 PDB 中已知结构对比，评估预测精度。
   - **验证方式**：TM-score、界面 RMSD、DNA 构象准确性。
   - **创新状态**：unverified

2. **名称**：整合 Factorbook motif 与 MD 模拟的 TF 结合动力学研究
   - **来源局限/观察**：Factorbook 提供静态 motif 和结合位点，但不提供结合动力学信息；MD 模拟可研究结合过程，但需要初始结合构象。
   - **核心假设**：以 Factorbook 中高置信 motif 实例为初始构象，MD 模拟可揭示 TF 结合的特异性来源（如构象选择 vs. 诱导拟合）。
   - **初步方法**：选取 3-5 个代表性 TF（如 CTCF、ZNF407），从 Factorbook 获取 motif 实例，构建 TF–DNA 复合物初始结构，进行微秒级 MD 模拟，分析结合自由能、关键接触残基、DNA 构象变化。
   - **验证方式**：与实验突变数据对比，计算结合自由能变化。
   - **创新状态**：unverified

3. **名称**：基于 Factorbook 深度学习滤波器的迁移学习预测新 TF 结合位点
   - **来源局限/观察**：ZNF407 等 TF 的 motif 由 ZMotif 发现，但未在 ChIP-seq 中验证；迁移学习可将其应用于新细胞类型或新 TF。
   - **核心假设**：ZMotif 滤波器作为预训练权重，可迁移到新任务（如预测未测细胞类型的 TF 结合），优于从头训练。
   - **初步方法**：加载 Factorbook 提供的 Numpy 格式滤波器，初始化 CNN 第一层，在 ENCODE Phase IV 新数据上微调，预测 TF 结合。
   - **验证方式**：AUPRC、与 ChIP-seq 实验数据对比。
   - **创新状态**：unverified

4. **名称**：Factorbook motif 位点与 GWAS 变异的共定位分析揭示 TF 结合机制
   - **来源局限/观察**：Factorbook 提供 SNP 注释功能，但未系统分析变异对 TF 结合的影响模式。
   - **核心假设**：位于 motif 核心区域的疾病相关变异更可能破坏 TF 结合，且破坏模式与 TF 家族相关。
   - **初步方法**：从 Factorbook 提取所有 motif 实例，与 GWAS 变异重叠，计算变异对 PWM 匹配分数的影响，分析不同 TF 家族的变异敏感性差异。
   - **验证方式**：与实验数据（如 MPRA、eQTL）对比。
   - **创新状态**：unverified

5. **名称**：基于 Factorbook 的 TF 结合位点染色质状态预测模型
   - **来源局限/观察**：Factorbook 提供 DNase/ATAC 可及性数据，但未建模染色质状态对 TF 结合的影响。
   - **核心假设**：整合 motif 序列特征与染色质可及性特征，可更准确预测 TF 结合位点。
   - **初步方法**：从 Factorbook 提取 motif 实例及对应 DNase/ATAC 信号，训练梯度提升或深度学习模型，预测 TF 结合概率。
   - **验证方式**：交叉验证 AUC、与 ChIP-seq 数据对比。
   - **创新状态**：unverified