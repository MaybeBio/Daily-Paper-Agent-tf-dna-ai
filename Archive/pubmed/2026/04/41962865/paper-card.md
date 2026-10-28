## 01 基本信息
- **标题**：An artificial intelligence optimized hepatic differentiation unveils NR5A2 and AP-1 transcriptional regulation in hepatic maturation
- **作者**：Huo, Zijun; Tu, Jian; Yang, Wei-Lei; Huang, Mo-Fan; Wang, Ruoyu; Huang, Chih-Wei; Tavakol, Tara N; Kizilbash, Mikal; Fisher, Megan E; Huang, Yu-Wen; Zhu, Dandan; Phan, Trinh T T; Shoemaker, Rosemary; Huang, Yu-Wen; Zhang, Yang; Huff, Chad D; Chen, Shih-Yu; Liu, Tien-Jen; Xiao, Haipeng; Lee, Dung-Fang; Zhao, Ruiying
- **单位**：The University of Texas Health Science Center at Houston; Icahn School of Medicine at Mount Sinai; AIxMed, Inc. 等（部分作者单位未在摘要中列出）
- **期刊/平台**：The Journal of Biological Chemistry
- **年份**：2026（在线发表日期 2026-04-11）
- **论文类型**：研究论文（Research Article）
- **领域**：干细胞分化、肝细胞成熟、转录调控、AI/机器学习辅助细胞培养优化
- **关键词**：hepatic differentiation, hepatocyte-like cells, NR5A2, AP-1, machine learning, ATAC-seq, scRNA-seq
- **DOI/ID**：10.1016/j.jbc.2026.111435
- **代码**：未提供
- **数据**：RNA-seq、ATAC-seq、WGS 数据已存入 GEO（GSE246557）
- **阅读日期**：2026-05-15（假设）
- **在课题方向中的位置**：本文聚焦于**肝细胞分化过程中的转录因子调控网络**，核心发现为 NR5A2 和 AP-1 家族在肝细胞成熟中的关键作用。虽然研究对象是肝细胞而非通用 TF–DNA 互作，但其**多组学整合策略（RNA-seq + ATAC-seq + scRNA-seq + ChIP-seq 公共数据）** 以及**AI/ML 辅助细胞分化监测方法**，对 TF–DNA 结合机制研究具有方法学借鉴意义。本文属于「AI 辅助实验优化 × 转录因子调控机制解析」的交叉方向。

## 02 一句话总结
本文开发了一个基于机器学习（CNN）的 AI 工具，通过分析肝祖细胞（HPCs）的明场显微镜图像来预测和优化肝细胞分化效率，并利用多组学分析（RNA-seq、ATAC-seq、scRNA-seq）揭示了 NR5A2 和 AP-1 转录因子在肝细胞成熟中的关键调控作用。

## 03 研究问题
- **具体问题**：如何提高人多能干细胞（hPSCs）向肝细胞样细胞（HLCs）分化的效率和成功率？肝细胞成熟过程中关键的转录因子调控机制是什么？
- **为什么重要**：HLCs 在药物筛选和细胞治疗中具有巨大潜力，但现有分化方案复杂且不稳定，成功率低；同时，肝细胞成熟的转录调控机制尚未完全阐明。
- **现有方法不足**：传统分化方案依赖经验性调整，缺乏客观、定量的分化效率评估手段；免疫染色和谱系追踪等方法耗时且无法实时监测；对肝细胞成熟阶段的转录因子调控网络认识有限。
- **精确研究问题**：Can a machine learning-based AI tool using bright-field microscopy images accurately predict hepatic differentiation efficiency and enable the identification of key transcription factors (NR5A2, AP-1) regulating hepatic maturation?

## 04 背景与发展脉络
- **阶段一：传统肝细胞分化方案**（4-10 等文献）：基于发育生物学知识，逐步添加生长因子和细胞因子（如 activin A, BMP4, FGF2, HGF, OSM）模拟肝脏发育过程。局限：方案复杂、效率不稳定、缺乏客观评估手段。
- **阶段二：AI/ML 辅助细胞分化监测**（14, 15, 50-52 等文献）：利用深度学习（如 CNN）分析细胞图像，预测分化状态。如 Kusumoto 等识别 iPSC 来源的内皮细胞，Orita 等对 iPSC 来源心肌细胞进行质量控制。局限：多聚焦于单一细胞类型，未与下游分子机制研究深度整合。
- **阶段三：多组学解析分化调控机制**（35, 41, 42 等文献）：利用 RNA-seq、ATAC-seq、scRNA-seq 等技术解析分化过程中的转录和表观遗传变化。局限：多组学数据与分化方案优化之间的闭环反馈不足。
- **本文位置**：将 AI/ML 辅助分化监测与多组学机制解析**闭环整合**，既优化了分化方案，又通过多组学揭示了 NR5A2 和 AP-1 的新调控作用。在 TF–DNA 互作课题方向上，本文展示了**如何从多组学数据中推断转录因子调控网络**，并利用 ChIP-seq 公共数据验证 TF 结合。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 分化效率低且不稳定 | 多步骤分化方案成功率低，不同批次差异大 | 缺乏客观、定量的分化效率评估手段；HPC 阶段细胞异质性高 | Results 节 "a low percentage of HPCs may exhibit the desired molecular and functional characteristics" |
| 分化状态评估依赖主观判断 | 传统方法依赖免疫染色、形态学观察，耗时且无法实时 | 缺乏基于图像的自动化评估工具 | Results 节 "accurately identifying differentiated HPC cells can be challenging due to the heterogeneous nature of the cell population" |
| 肝细胞成熟调控机制不明 | NR5A2 和 AP-1 在肝细胞成熟中的具体作用未被阐明 | 以往研究多关注早期分化阶段，对成熟阶段转录因子网络认识不足 | Discussion 节 "the mechanism through which NR5A2 regulates the AP-1 family during hepatic differentiation remains unexplored" |
| 多组学数据与方案优化脱节 | 转录组/表观组数据难以直接指导分化方案改进 | 缺乏将分子机制发现转化为方案优化的闭环策略 | 本文通过 AI 监测 + 多组学解析建立闭环 |

## 06 核心思想
1. **表面方法**：开发基于 CNN 的机器学习 AI 工具，用明场显微镜图像（而非免疫染色）对 HPC 分化状态进行分类（成功/失败/不确定），并据此优化四阶段分化方案；同时结合 RNA-seq、ATAC-seq、scRNA-seq 和公共 ChIP-seq 数据解析转录调控网络。
2. **核心洞察**：HPC 阶段的形态学特征可作为分化效率的客观指标；NR5A2 在 HPC→HLC 成熟过程中上调，并通过结合 AP-1 家族基因启动子区域调控其表达，进而影响肝细胞成熟。
3. **可能的普适教训** [Analysis]：AI/ML 辅助的形态学分析可以作为一种**非侵入性、实时、客观**的分化监测手段，适用于多种干细胞分化体系；多组学整合（转录组+表观组+单细胞）是解析复杂转录调控网络的有效策略，尤其适用于 TF–DNA 互作研究。

## 07 方法总览
- **输入**：hPSCs（H1, H9, HES2, RUES2）分化过程中的明场显微镜图像（1163 个 FOVs）；分化各阶段的细胞样本（RNA-seq、ATAC-seq、scRNA-seq）
- **输出**：分化效率预测（成功/失败/不确定）；关键转录因子（NR5A2, AP-1）及其调控网络
- **模块**：
  1. CNN 图像分类模块（强/弱监督学习）
  2. 四阶段分化方案优化模块
  3. 转录组分析模块（RNA-seq）
  4. 染色质可及性分析模块（ATAC-seq）
  5. 单细胞转录组分析模块（scRNA-seq）
  6. ChIP-seq 公共数据整合模块（ENCODE）
- **训练**：CNN 使用标注的 FOVs 训练（70% 训练，20% 验证，10% 测试）
- **工具**：未提供具体软件版本
- **反馈回路**：AI 预测分化效率 → 优化分化方案 → 提高 HLC 产量和纯度 → 多组学分析验证分子机制
- **文字流程**：hPSCs →（activin A + CHIR99021）→ DE（Day 3）→（BMP4/FGF2）→ HPCs（Day 9）→（HGF）→ IMHs →（OSM）→ HLCs（Day 21）；AI 工具在 HPC 阶段监测分化状态，指导方案调整；最终 HLCs 进行多组学分析。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN 图像分类 | 预测 HPC 分化成功/失败 | 客观评估分化效率，减少主观判断 | 输入：明场 FOVs；输出：分类标签 | Results 图 1G（accuracy 0.978, F1 0.975） | 预期影响：失去客观监测手段，分化方案优化缺乏定量依据 [预期效应] |
| 四阶段分化方案 | 将 hPSCs 分化为 HLCs | 产生功能性肝细胞 | 输入：hPSCs；输出：HLCs | Results 图 2A（成功率 >90%） | 预期影响：无法获得 HLCs，后续分析无法进行 [预期效应] |
| RNA-seq 分析 | 鉴定分化各阶段差异表达基因 | 揭示转录动态变化 | 输入：各阶段 mRNA；输出：差异表达基因、聚类 | Results 图 3A-D | 预期影响：无法识别关键转录因子 [预期效应] |
| ATAC-seq 分析 | 鉴定染色质可及性变化 | 揭示表观遗传调控 | 输入：各阶段细胞核；输出：可及性峰、motif | Results 图 4A-C | 预期影响：无法识别阶段特异性 TF 结合位点 [预期效应] |
| scRNA-seq 分析 | 解析细胞异质性 | 确认 NR5A2/AP-1 在特定细胞亚群中的表达 | 输入：HLCs 单细胞；输出：细胞亚群、基因表达 | Results 图 5A-F | 预期影响：无法确认细胞亚群特异性调控 [预期效应] |
| ChIP-seq 公共数据整合 | 验证 NR5A2/AP-1 结合靶基因 | 提供 TF 直接结合的实验证据 | 输入：ENCODE 公共 ChIP-seq；输出：结合峰 | Results 图 4D-E | 预期影响：缺乏 TF 直接结合证据，调控关系仅为相关性 [预期效应] |
| NR5A2 敲低实验 | 验证 NR5A2 对 AP-1 的调控 | 功能验证 | 输入：shRNA；输出：AP-1 表达变化 | Results 图 4F | 预期影响：无法建立因果调控关系 [预期效应] |

## 09 关键公式符号
- **Accuracy**：Accuracy = (TP + TN) / (TP + TN + FP + FN)，用于评估 CNN 分类性能。TP = 真阳性，TN = 真阴性，FP = 假阳性，FN = 假阴性。来源：Methods 节 "Evaluation of the AI algorithm"。
- **F1 score**：F1 = 2 × (precision × recall) / (precision + recall) = TP / (TP + 0.5 × (FP + FN))，用于平衡精确率和召回率的综合评价指标。来源：Methods 节 "Evaluation of the AI algorithm"。
- **2^(-ΔΔCT) 法**：用于 qRT-PCR 相对定量分析。来源：Methods 节 "RNA isolation and qRT-PCR"（未给出具体公式，但为常规方法）。

## 10 实验设计与证据链
- **数据集/群体**：
  - 4 个 hPSC 系（H1, H9, HES2, RUES2）
  - 1163 个 FOVs（12 个 hPSC, 413 个 DE, 738 个 HPC）
  - RNA-seq：4 个时间点（Day 0, 3, 9, 21）
  - ATAC-seq：H1 和 H9 来源的各分化阶段
  - scRNA-seq：整合已发表数据（GSE81252, GSE96981）
  - ChIP-seq：ENCODE 公共数据（GSM935364, GSM935649, GSM846875）
  - 3 个 PHC 供体（OSZ, ZMC, JYN）
- **指标**：accuracy, F1 score, precision, recall（AI 性能）；ALB 阳性率（流式）；ALB 分泌（ELISA）；尿素合成、CYP3A4 活性（肝功能）；基因表达（qRT-PCR, RNA-seq）；染色质可及性（ATAC-seq）；TF 结合（ChIP-seq）
- **基线**：未明确指定基线方法，但对比了已发表分化方案（4-10 文献）
- **预算**：未提供
- **骨干/仪器**：Illumina HiSeq X10（测序）；Leica DMi8（显微镜）；未提供其他仪器
- **oracle 输入**：senior researcher 的标注作为 CNN 训练的 ground truth
- **评测协议**：CNN 在独立测试集上评估；分化效率通过流式、ELISA、功能实验验证；调控网络通过多组学整合验证

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| CNN 分类性能 | AI 能准确预测 HPC 分化状态 | 训练/验证/测试集划分 | accuracy 0.978, F1 0.975（测试集） | AI 工具可客观评估分化效率 | 未与其他 ML 方法对比 | Results 图 1G |
| 分化效率验证 | 优化方案提高 HLC 产量 | 4 个 hPSC 系 | 成功率 >90%，ALB 阳性 >95% | 优化方案高效稳定 | 未与所有已发表方案对比 | Results 图 2A-C |
| 肝功能验证 | HLCs 具有肝细胞功能 | 与 PHCs 对比 | 尿素合成、CYP3A4 活性与 PHCs 相当 | HLCs 功能成熟 | 未进行体内功能验证 | Results 图 2E-F |
| RNA-seq 聚类 | 分化各阶段转录组不同 | 4 个时间点 | 15 个动态表达聚类 | 转录组动态变化明显 | 未鉴定所有调控因子 | Results 图 3D |
| ATAC-seq motif | 阶段特异性 TF 结合 | 各阶段 ATAC-seq | NR5A2 motif 在 HPC/HLC 阶段富集 | NR5A2 参与 HPC/HLC 调控 | motif 富集不等于实际结合 | Results 图 4C |
| ChIP-seq 整合 | NR5A2/AP-1 直接结合靶基因 | ENCODE 公共数据 | JUN/JUND 结合 HLC 标记基因 TSS | AP-1 直接调控 HLC 标记基因 | 未在本文分化体系中验证 | Results 图 4D |
| NR5A2 敲低 | NR5A2 调控 AP-1 表达 | shRNA 敲低 | AP-1 基因下调 | NR5A2 正调控 AP-1 | 未进行 ChIP-seq 验证 NR5A2 直接结合 AP-1 启动子 | Results 图 4F |
| 异位表达拯救 | AP-1 是 NR5A2 下游效应器 | FOS/JUN 过表达 | 细胞死亡被拯救，分化恢复 | AP-1 介导 NR5A2 功能 | 未验证所有 AP-1 家族成员 | Results 图 S4D |
| scRNA-seq 轨迹 | NR5A2/AP-1 沿分化轨迹动态变化 | 整合已发表数据 | NR5A2 在 IMH/HLC 阶段上调，AP-1 在 HLC 阶段上调 | 与 bulk 数据一致 | 未进行拟时间分析验证因果 | Results 图 5A-F |
| 安全性评估 | 分化方案不引入致癌突变 | WGS 分析 | 未检测到显著突变 | 方案安全性良好 | 样本量小（6 个） | Results 图 6 |

## 11 结论正确解读
- **任务范围**：本文的 AI 工具仅用于 HPC 阶段的分化状态监测，未覆盖整个分化过程；多组学分析聚焦于 H1 和 H9 两个 hPSC 系。
- **oracle/真值输入**：CNN 训练的 ground truth 来自 senior researcher 的主观标注，存在标注偏差风险。
- **端到端状态**：AI 工具与分化方案优化、多组学分析是**串联**而非端到端整合；AI 预测结果未直接用于实时反馈控制。
- **算力成本**：未提供 CNN 训练和推理的算力需求。
- **历史数据依赖**：scRNA-seq 分析依赖已发表数据（GSE81252, GSE96981），非本文独立产生。
- **模型依赖**：CNN 架构细节未完全公开，可复现性受限。
- **最难情形**：HPC 阶段细胞异质性高，部分 FOVs 被标注为"不确定"，AI 对边界情形的分类能力未充分讨论。
- **群体/领域边界**：结论基于体外分化体系，未在体内验证；NR5A2/AP-1 调控网络在肝细胞成熟中的普适性需进一步验证。
- **有边界的复述**：本文开发的 CNN 工具能在 HPC 阶段以高准确率（97.8%）预测肝细胞分化成败，优化的分化方案在 4 个 hPSC 系中实现 >90% 成功率；多组学分析提示 NR5A2 在 HPC→HLC 成熟过程中上调，可能通过调控 AP-1 家族基因表达促进肝细胞成熟，但 NR5A2 直接结合 AP-1 启动子的证据来自公共 ChIP-seq 数据而非本文实验。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| AI 算法未用于测试多种实验条件 | "the model was not applied to test multiple experimental conditions" | 建议纳入纵向图像建立实时 AI 算法 | Results 节（图 1B 描述） |
| NR5A2/AP-1 机制需进一步研究 | "Further investigations are necessary to elucidate the NR5A2-AP-1 regulatory network" | 深入研究 NR5A2-AP-1 调控网络 | Discussion 节 |
| 未提供 AI 算法架构细节 | 未在正文中详细描述 CNN 架构 | 未提供 | 未提供 |
| 样本量有限 | WGS 仅 6 个样本 | 未提供 | Results 节（图 6） |

**作者提及的相关约束**（非正式局限）：
- scRNA-seq 数据来自已发表研究，非本文独立产生
- ChIP-seq 数据来自 ENCODE 数据库，非本文实验验证
- 体内功能验证缺失

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| CNN 训练集仅 1163 个 FOVs，且来自 3 个分化阶段 | 样本量较小，可能过拟合；类别不平衡（hPSC 仅 12 个 FOVs） | 影响模型泛化能力 | 增加样本量，采用交叉验证，报告类别分布 | Results 节（图 1B-C） |
| "不确定"类别的处理方式未明确 | 标注为"不确定"的 FOVs 如何影响训练和评估？ | 影响模型性能评估的可靠性 | 明确"不确定"类别的处理策略，进行敏感性分析 | Results 节（图 1C） |
| NR5A2 敲低导致细胞死亡，异位表达 AP-1 拯救 | 细胞死亡可能是非特异性毒性效应，而非分化失败 | 影响 NR5A2-AP-1 因果关系的解释 | 增加对照实验（如无关 TF 敲低），检测凋亡/坏死标志物 | Results 节（图 S4D） |
| ChIP-seq 数据来自 ENCODE 而非本文分化体系 | 结合位点可能具有细胞类型特异性 | 影响 NR5A2/AP-1 直接调控结论的可靠性 | 在本文 HLCs 中进行 ChIP-seq 验证 | Results 节（图 4D-E） |
| 未报告 CNN 的架构、超参数和训练细节 | 可复现性受限 | 影响方法推广 | 公开代码和训练配置 | Methods 节（未提供） |
| 分化效率 >90% 的定义标准未明确 | 是形态学标准还是分子标志物标准？ | 影响结果可比性 | 明确效率计算标准，提供流式原始数据 | Results 节（图 2A） |
| 未与其他 AI 方法（如传统机器学习、其他 CNN 架构）对比 | 无法评估方法优越性 | 影响方法选择的合理性 | 增加基线对比实验 | Results 节（图 1G） |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **AI 辅助分化监测的可迁移方法**：本文展示了用 CNN 分析明场显微镜图像来预测分化状态的方法。在 TF–DNA 互作研究中，可迁移至**基于图像的 TF 结合位点预测**或**染色质状态分类**，利用形态学特征作为表观状态的代理指标。

2. **多组学整合策略**：RNA-seq + ATAC-seq + scRNA-seq + 公共 ChIP-seq 的四层整合，是解析 TF 调控网络的有效范式。在 TF–DNA 互作研究中，可借鉴此策略：**转录组（表达变化）+ 表观组（可及性变化）+ 单细胞（异质性解析）+ ChIP-seq（直接结合证据）** 的组合可提供从相关性到因果性的完整证据链。

3. **TF 调控层级推断**：本文通过 ATAC-seq motif 富集发现 NR5A2 和 AP-1，再通过 ChIP-seq 验证结合，最后通过敲低/过表达验证功能。这种**从开放染色质到 TF 推断再到功能验证**的流程，可直接迁移至其他细胞分化体系中的 TF–DNA 互作研究。

4. **NR5A2-AP-1 调控轴**：NR5A2 可能直接结合 AP-1 家族基因启动子并调控其表达，形成转录因子级联。在 TF–DNA 互作研究中，可关注**TF 调控 TF** 的级联模式，而非仅关注 TF 对效应基因的直接调控。

5. **安全性评估范式**：WGS 突变分析 + 体外/体内致瘤性实验，为干细胞分化产品的安全性评估提供了参考框架。在 TF–DNA 互作研究中，可借鉴此思路评估 TF 过表达或敲除的基因组稳定性影响。

6. **弱监督学习的应用**：本文采用弱监督学习减少标注工作量。在 TF–DNA 互作研究中，可迁移至**大规模 ChIP-seq 峰标注**或**TF 结合位点预测模型的训练**，降低人工标注成本。

## 15 与已有知识连接
- **NR5A2（LRH-1）**：核受体家族成员，已知在肝脏发育、胆汁酸代谢和肝细胞增殖中发挥重要作用（Fayard et al., 2004; Lee & Moore, 2008）。本文发现其在肝细胞成熟中的新功能，与已有知识一致并扩展。
- **AP-1 转录因子**：由 FOS/JUN 家族组成，参与细胞增殖、分化和应激反应（Shaulian & Karin, 2002）。本文首次系统揭示其在肝细胞成熟中的作用。
- **肝细胞分化方案**：与既往方案（Si-Tayeb et al., 2010; Hay et al., 2008）相比，本文通过 AI 优化提高了效率和稳定性。
- **ATAC-seq 在分化研究中的应用**：与 Buenrostro et al. (2013) 的方法一致，本文将其应用于肝细胞分化的染色质动态分析。
- **scRNA-seq 在发育生物学中的应用**：与 Camp et al. (2017) 等人肝脏发育单细胞研究互补，本文聚焦于体外分化体系。
- **AI/ML 在干细胞领域的应用**：与 Kusumoto et al. (2018)、Orita et al. (2019) 等工作一致，本文进一步将 AI 与多组学机制解析整合。
- **[Analysis] 候选方向**：本文的 NR5A2-AP-1 调控轴可能与其他已知肝细胞 TF（如 HNF4A、FOXA2）存在交叉调控，值得进一步探索。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：基于深度学习的 TF–DNA 结合位点预测模型（TF-BindNet）
   - **来源局限/观察**：本文 CNN 仅用于分化状态分类，未直接用于 TF 结合预测；ATAC-seq motif 分析依赖传统工具
   - **核心假设**：CNN 可从 ATAC-seq 峰序列和染色质可及性特征中学习 TF 结合特异性，优于传统 motif 匹配
   - **相对本文的增量**：将 AI 从分化监测扩展到 TF–DNA 互作预测
   - **初步方法**：使用本文 ATAC-seq 数据 + ENCODE ChIP-seq 作为训练标签，构建 CNN 模型预测 TF 结合位点
   - **验证方式**：在独立细胞类型中验证预测准确性，与现有工具（如 DeepSEA、Basenji）对比
   - **创新状态**：partially checked（已有类似工具，但未在肝细胞分化体系中验证）

2. **候选名称**：NR5A2-AP-1 调控网络的单细胞解析
   - **来源局限/观察**：本文 bulk RNA-seq 和 scRNA-seq 未在单细胞水平解析 NR5A2-AP-1 的共表达和调控关系
   - **核心假设**：NR5A2 和 AP-1 在特定肝细胞亚群中形成调控模块，驱动成熟
   - **相对本文的增量**：从群体水平到单细胞水平的调控机制解析
   - **初步方法**：对本文分化体系进行 scRNA-seq + scATAC-seq 多组学分析，构建 NR5A2-AP-1 调控网络
   - **验证方式**：通过 CRISPR 干扰在特定亚群中验证调控关系
   - **创新状态**：unverified

3. **候选名称**：TF 级联调控的通用推断框架（CascadeTF）
   - **来源局限/观察**：本文发现 NR5A2 调控 AP-1，提示 TF 级联在分化中的重要性，但缺乏通用推断工具
   - **核心假设**：通过整合时间序列转录组和 ATAC-seq，可系统推断 TF 级联调控关系
   - **相对本文的增量**：从单一体系到通用方法
   - **初步方法**：基于本文的 NR5A2-AP-1 案例，开发 TF 级联推断算法，整合 motif、表达和染色质数据
   - **验证方式**：在多个分化体系中验证推断的 TF 级联
   - **创新状态**：unverified

4. **候选名称**：AI 辅助的实时分化反馈控制系统
   - **来源局限/观察**：本文 AI 工具是离线评估，未实现实时反馈控制
   - **核心假设**：将 AI 预测与自动化培养系统整合，可实现分化过程的实时优化
   - **相对本文的增量**：从监测到控制的闭环
   - **初步方法**：开发微流控培养系统 + 实时成像 + AI 决策算法，自动调整培养基成分
   - **验证方式**：比较 AI 控制与人工控制的分化效率和一致性
   - **创新状态**：unverified

5. **候选名称**：肝细胞成熟 TF 调控的进化保守性分析
   - **来源局限/观察**：本文发现 NR5A2/AP-1 在人类肝细胞成熟中的作用，未探讨其进化保守性
   - **核心假设**：NR5A2-AP-1 调控模块在脊椎动物肝脏发育中保守
   - **相对本文的增量**：从人类到跨物种的调控机制验证
   - **初步方法**：比较人类、小鼠、斑马鱼肝脏发育的转录组和 ATAC-seq 数据
   - **验证方式**：在模式生物中验证 NR5A2-AP-1 调控关系
   - **创新状态**：unverified