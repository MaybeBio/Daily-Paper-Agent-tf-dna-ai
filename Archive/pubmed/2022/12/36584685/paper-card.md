## 01 基本信息
- **标题**：Gene regulatory network reconfiguration in direct lineage reprogramming
- **作者与单位**：Kamimoto, Kenji; Adil, Mohd Tayyab; Jindal, Kunal; Hoffmann, Christy M; Kong, Wenjun; Yang, Xue; Morris, Samantha A（华盛顿大学圣路易斯分校，Morris实验室）
- **期刊/预印本平台**：Stem Cell Reports
- **年份**：2022-12-31
- **论文类型**：研究论文（Research Article）
- **领域**：直接谱系重编程、基因调控网络（GRN）推断、单细胞多组学、转录因子（TF）功能预测
- **关键词**：CellOracle、GRN推断、直接重编程、iPSC、Fos、Yap1、单细胞转录组、单细胞染色质可及性
- **DOI/arXiv 号**：10.1016/j.stemcr.2022.11.010
- **代码**：https://github.com/morris-lab/CellOracle
- **数据**：GEO: GSE99915（Biddy et al., 2018）、GSE217675（本文新数据）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文是「TF–DNA 互作 × AI/计算方法」方向的代表性工作，核心贡献在于将 GRN 推断（基于 motif 扫描 + 表达相关性）与单细胞谱系追踪（CellTag）结合，实现"早期网络状态→重编程命运"的因果关联分析，并通过 in silico TF perturbation 预测 + 实验验证，发现 Fos-Yap1 轴在直接重编程中的关键作用。对 TF–DNA 结合机制研究提供了"从静态网络到动态命运预测"的方法学范式。

## 02 一句话总结
本文通过 CellOracle 框架（整合 scATAC-seq 的 motif 扫描与 scRNA-seq 的表达相关性来推断 GRN），结合 CellTag 谱系追踪，对成纤维细胞→内胚层祖细胞（iEP）直接重编程过程中的 GRN 重构进行解析，并通过 in silico TF 敲除/过表达模拟与实验验证，发现 Fos（AP-1 亚基）与 Yap1（Hippo 效应因子）协同促进重编程效率与保真度。

## 03 研究问题
- **具体问题**：在直接谱系重编程（成纤维细胞→iEP）过程中，GRN 如何被重构？哪些 TF 在重编程起始阶段决定命运走向（成功重编程 vs. 死胡同状态）？能否通过计算预测新的重编程调控因子？
- **为什么重要**：直接重编程效率低、保真度差，根本原因在于对 GRN 重构机制理解不足。若能识别关键调控节点，可指导重编程方案的优化。
- **现有方法不足**：传统 GRN 推断方法（如 WGCNA、GENIE3）仅基于表达相关性，缺乏调控方向性和因果性；且未与谱系命运关联，无法区分"伴随变化"与"驱动变化"。
- **精确研究问题**：Can CellOracle, by integrating scATAC-seq-derived base GRN and scRNA-seq-derived context-specific GRN with CellTag-based lineage tracing, identify early network states that determine reprogramming outcome and predict novel TF regulators (e.g., Fos, Yap1) that enhance iEP conversion efficiency?

## 04 背景与发展脉络
- **阶段一：基于共表达的 GRN 推断**（如 WGCNA、GENIE3）——仅利用表达相关性，缺乏调控方向性，无法区分直接/间接调控。
- **阶段二：整合 motif 信息的 GRN 推断**（如 SCENIC、pySCENIC）——引入 TF motif 扫描，但通常仅基于表达数据，未充分利用染色质可及性信息。
- **阶段三：多组学整合的 GRN 推断**（如 CellOracle、Pando）——整合 scATAC-seq 的染色质可及性与 scRNA-seq 表达，通过 motif 扫描 + 表达相关性构建"base GRN"→"context-specific GRN"，并支持 in silico perturbation 模拟。
- **阶段四：GRN 推断 + 谱系追踪的因果解析**（本文）——将 CellOracle 与 CellTag 谱系追踪结合，将早期网络状态与最终命运直接关联，实现"状态→命运"的因果推断。
- **本文主张的位置**：在 GRN 推断方法学上，CellOracle 属于"多组学整合 + 可模拟扰动"的第三代方法；在应用上，本文首次将 GRN 推断与谱系追踪结合用于直接重编程的机制解析。
- **脉络核验状态**：仅本文框架（基于本文引言与讨论的梳理，未做外部系统综述核验）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 重编程效率低 | 仅少数细胞成功转化为 iEP，多数进入死胡同状态 | 早期 GRN 重构方向决定命运，但关键调控节点未知 | Results 图 1F：死胡同与 iEP 轨迹分离；图 2F：iEP-enriched 与 iEP-depleted 克隆命运差异 |
| 群体异质性掩盖关键信号 | 传统 bulk 分析无法区分成功与失败重编程的分子差异 | 早期细胞群体内存在命运已定的亚群，需谱系追踪才能解析 | Results 图 2C–2G：CellTag 克隆追踪揭示命运已定的早期亚群 |
| GRN 推断缺乏因果性 | 静态网络无法预测扰动后果 | 传统方法仅描述相关性，无法模拟 TF 敲除/过表达的后果 | Results 图 3A–3C：CellOracle 的 perturbation simulation 框架 |
| 候选 TF 筛选效率低 | 实验验证候选 TF 耗时费力 | 缺乏系统性、 unbiased 的 in silico 筛选方法 | Results 图 3D：基于 perturbation score 的 TF 排名 |
| 非 DNA 结合因子（如 Yap1）难以纳入 GRN 框架 | Yap1 不直接结合 DNA，传统 GRN 方法无法建模 | CellOracle 仅能推断 DNA 结合 TF 的调控关系，Yap1 需通过其靶基因间接推断 | Results 图 5A：Fos 靶基因中富集 Yap1 直接靶标 |

## 06 核心思想
1. **表面方法**：CellOracle 流程——(1) 用 scATAC-seq 数据扫描 TF motif，构建"base GRN"（所有潜在 TF–靶基因调控关系）；(2) 用 scRNA-seq 表达数据修剪 base GRN，保留活跃的调控连接，得到 context-specific GRN；(3) 对候选 TF 进行 in silico perturbation（模拟敲除/过表达），计算 perturbation score 预测其对细胞命运的影响；(4) 结合 CellTag 谱系追踪，将早期网络状态与最终命运关联。
2. **核心洞察**：GRN 重构在重编程起始阶段就已决定命运走向——成功重编程的细胞在早期就建立特定的网络配置（如 Fos 高连接性），而死胡同细胞则保留成纤维细胞网络特征。通过将"网络状态"与"命运"直接关联，可将静态 GRN 转化为动态因果模型。
3. **可能的普适教训** [Analysis]：① 多组学整合（染色质可及性 + 表达）比单一组学更能捕捉调控逻辑；② 谱系追踪是连接"分子状态"与"功能命运"的关键桥梁，尤其适用于异质性过程；③ in silico perturbation 可作为候选基因筛选的"虚拟预实验"，大幅缩小实验验证范围。

## 07 方法总览
- **输入**：
  - scRNA-seq 数据（Biddy et al., 2018 的 27,663 细胞 + 本文新数据 24,799 细胞）
  - scATAC-seq 数据（小鼠 atlas，Cusanovich et al., 2018）
  - CellTag 谱系追踪数据（本文新实验）
- **输出**：
  - 各细胞簇的 context-specific GRN
  - TF perturbation score 排名（预测重编程促进/抑制因子）
  - 命运关联的早期网络状态（iEP-enriched vs. iEP-depleted）
- **模块**：
  1. 数据预处理与聚类（PAGA）
  2. Base GRN 构建（motif 扫描 + 染色质可及性）
  3. Context-specific GRN 推断（表达相关性 + 网络修剪）
  4. In silico perturbation simulation（信号传播 + 命运预测）
  5. CellTag 谱系追踪与命运关联
  6. 实验验证（shRNA 敲低 + 集落形成实验；CRISPR-Cas9 敲除 + 单细胞转录组）
- **训练**：无监督/半监督方法，无传统"训练-测试"范式；GRN 推断基于统计相关性，perturbation simulation 基于网络传播模型
- **工具**：CellOracle（Python）、PAGA、Monocle、CellTag 分析流程、Capybara（细胞类型分类）
- **反馈回路**：计算预测 → 实验验证 → 更新网络模型（本文中实验验证了 Fos、Yap1 的预测，但未明确迭代更新模型）
- **文字流程**：scATAC-seq 构建 base GRN → scRNA-seq 修剪为 context-specific GRN → 对 180 个活跃 TF 逐一进行 in silico KO 模拟 → 计算 perturbation score 排名 → 结合 CellTag 谱系追踪识别命运关联的早期网络状态 → 实验验证（shRNA 敲低筛选 + Fos/Yap1 过表达 + CRISPR 敲除）→ 单细胞转录组确认机制。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Base GRN 构建（motif 扫描） | 从染色质可及性区域识别 TF 结合位点，建立 TF–靶基因潜在调控关系 | 提供调控关系的"候选集"，避免仅靠表达相关性的假阳性 | 输入：scATAC-seq 峰 + motif 数据库；输出：TF–靶基因潜在连接列表 | Results 图 1A–1B；Methods 节 | 预期影响：失去调控方向性先验，GRN 推断退化为纯表达相关性（如 WGCNA），无法区分直接/间接调控 [预期效应] |
| Context-specific GRN 推断 | 用表达数据修剪 base GRN，保留活跃连接 | 不同细胞类型/状态的调控网络不同，需上下文特异化 | 输入：base GRN + scRNA-seq 表达矩阵；输出：各簇的加权 GRN | Results 图 1C–1D；图 1G–1K | 预期影响：网络过于稠密，无法识别关键节点；或过于稀疏，丢失重要调控关系 [预期效应] |
| In silico perturbation simulation | 模拟 TF 敲除/过表达后的网络信号传播，预测细胞状态转变方向 | 将静态网络转化为可测试的功能预测 | 输入：context-specific GRN + 候选 TF；输出：perturbation score + 状态转变向量图 | Results 图 3A–3E；Methods 节 | 预期影响：失去因果预测能力，只能描述网络结构，无法指导实验验证 [预期效应] |
| CellTag 谱系追踪 | 标记早期细胞克隆，追踪其最终命运 | 将早期分子状态与最终命运直接关联，区分"伴随"与"驱动"变化 | 输入：CellTag 条形码 + 多时间点 scRNA-seq；输出：命运已定的早期细胞亚群 | Results 图 2A–2G | 预期影响：无法区分早期网络变化是命运的原因还是结果 [预期效应] |
| 实验验证（shRNA/CRISPR） | 敲低/敲除候选 TF，验证其对重编程效率的影响 | 计算预测需要实验确认 | 输入：候选 TF 的 shRNA/CRISPR 构建；输出：集落形成效率、单细胞转录组变化 | Results 图 3F–3G；图 4G–4J；图 5B–5G | 实测效应：6/8 候选 TF 敲低显著降低重编程效率（图 3G）；Fos 敲除导致 iEP 身份丧失（图 4J） |

## 09 关键公式符号
- **Perturbation score**（核心公式，Methods 节）：
  - 对 TF \( i \) 的扰动，计算其靶基因 \( j \) 的表达变化：\( \Delta x_j = w_{ij} \cdot \Delta x_i \)，其中 \( w_{ij} \) 为 GRN 中 TF \( i \) 到靶基因 \( j \) 的连接权重（由表达相关性估计）
  - 信号传播：\( \Delta x^{(k+1)} = A \cdot \Delta x^{(k)} \)，其中 \( A \) 为归一化的 GRN 邻接矩阵，\( k \) 为传播步数
  - Perturbation score：\( S_i = \langle \Delta x^{(T)}, \nabla f \rangle \)，其中 \( \nabla f \) 为细胞身份评分函数的梯度（基于 marker 基因表达），\( T \) 为传播总步数
- **网络中心性指标**（Results 图 1H）：
  - Degree centrality：\( C_D(v) = \deg(v) \)
  - Eigenvector centrality：\( C_E(v) = \frac{1}{\lambda} \sum_{u \in N(v)} C_E(u) \)，其中 \( \lambda \) 为邻接矩阵最大特征值
- **用途**：Perturbation score 用于量化 TF 敲除对重编程方向的预测影响；中心性指标用于识别网络中的关键调控节点
- **直觉**：Perturbation score 衡量"扰动该 TF 后，细胞状态向 iEP 还是成纤维细胞方向移动"；中心性衡量"该 TF 在网络中的连接重要性和影响力"
- **来源**：Methods 节（Supplemental experimental procedures），原文未给出完整公式推导，以上为基于描述的合理重构 [Analysis]

## 10 实验设计与证据链
- **数据集**：
  - 训练/分析数据：Biddy et al. (2018) 的 MEF→iEP 重编程 scRNA-seq（27,663 细胞，8 个时间点，28 天）
  - 新数据：本文谱系追踪实验（24,799 细胞：day 4 n=8,440；day 10 n=4,836；day 28 n=11,523）
  - 验证数据：shRNA 敲低实验（5 个生物学重复）；Fos/Yap1 过表达实验（6 个技术重复，2 个生物学重复）；CRISPR-Cas9 敲除实验
- **指标**：集落形成效率（重编程效率）；iEP 身份评分（基于 marker 基因表达）；perturbation score；网络中心性指标
- **基线/对照**：非靶向 scramble shRNA 对照；未处理 MEF；Biddy et al. (2018) 的原始重编程数据
- **评测协议**：计算预测 → 实验验证；集落形成实验作为重编程效率的定量指标；单细胞转录组用于确认细胞身份转变

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| GRN 连接强度分析 | Hnf4α-Foxa1 在早期重编程阶段连接强度最高 | 各时间点/簇的 Hnf4α-Foxa1 连接强度比较 | 早期阶段连接强度显著高于后期（p < 0.001） | Hnf4α-Foxa1 在重编程起始阶段发挥核心作用 | 不能证明因果关系，仅相关性 | Results 图 1G |
| 中心性分析 | Fos 在重编程早期是网络中的关键节点 | 各簇的 degree/eigenvector 中心性比较 | Fos 在早期重编程簇中中心性高，且为 connector hub | Fos 是重编程起始的关键调控因子 | 中心性不等于功能重要性，需实验验证 | Results 图 1J–1K；图 4A–4B |
| CellTag 谱系追踪 | 早期网络状态决定重编程命运 | iEP-enriched vs. iEP-depleted 克隆的 GRN 比较 | 命运已定的早期亚群具有不同的网络配置 | 早期 GRN 重构方向决定命运 | 不能排除后期微环境影响的贡献 | Results 图 2F–2H |
| In silico KO 筛选 | 预测 8 个候选 TF 敲低会降低重编程效率 | 180 个活跃 TF 的 perturbation score 排名 | 8 个候选 TF 排名靠前 | CellOracle 可系统性预测重编程调控因子 | 预测需要实验验证 | Results 图 3D–3E |
| shRNA 敲低验证 | 6/8 候选 TF 敲低降低重编程效率 | 各候选 TF 敲低 vs. scramble 对照 | 6/8 显著降低集落形成（20%–50% 减少） | 计算预测具有较高的实验验证率 | 未验证全部 8 个；效应量中等 | Results 图 3F–3G |
| Fos 过表达 | Fos 增强重编程效率 | Hnf4α-Foxa1 vs. Hnf4α-Foxa1+Fos | 集落形成增加 >2 倍 | Fos 是重编程的正向调控因子 | 未测试 Fos 单独是否足够 | Results 图 4G–4H |
| Fos 敲除（CRISPR） | Fos 维持 iEP 身份 | 对照 vs. Fos KO 的 iEP 细胞 | KO 后 iEP 向中间状态回归 | Fos 对 iEP 身份维持至关重要 | 未测试其他 AP-1 亚基的补偿效应 | Results 图 4I–4J |
| Yap1 靶基因分析 | Fos 通过 Yap1 信号通路发挥作用 | Fos 靶基因中 Yap1 靶标的富集分析 | 显著富集（Cyr61, Amotl2, Gadd45g, Ctgf） | Fos-Yap1 轴是重编程的关键机制 | 未直接验证蛋白互作 | Results 图 5A |
| Yap1 过表达 | Yap1 增强重编程效率 | Hnf4α-Foxa1 vs. Hnf4α-Foxa1+Yap1 vs. +Fos+Yap1 | Fos+Yap1 协同增强，集落形成增加近 3 倍 | Fos 与 Yap1 协同促进重编程 | 未测试 Yap1 单独效应 | Results 图 5B–5G |

## 11 结论正确解读
- **任务范围**：本文聚焦于 MEF→iEP 这一特定直接重编程范式，结论不能直接推广到其他重编程系统（如神经元、心肌细胞）或体内重编程。
- **oracle/真值输入**：CellOracle 的 base GRN 依赖 motif 扫描（基于已知 TF 结合 motif 数据库），因此受限于 motif 数据库的覆盖度和准确性；context-specific GRN 依赖表达相关性，无法捕捉翻译后修饰、竞争性结合等调控机制。
- **端到端状态**：计算预测 → 实验验证的闭环已建立，但预测精度有限（8 个候选中有 6 个验证成功，75% 命中率），且未进行大规模盲测。
- **算力成本**：原文未报告具体算力需求；CellOracle 为 Python 实现，基于网络传播模型，计算成本相对可控（未提供具体数据）。
- **历史数据依赖**：依赖 Biddy et al. (2018) 的历史 scRNA-seq 数据，数据质量与批次效应可能影响 GRN 推断。
- **模型依赖**：GRN 推断结果依赖聚类数、相关性阈值等参数选择；perturbation score 依赖网络传播模型假设（线性叠加、无非线性效应）。
- **最难情形**：Yap1 这类非 DNA 结合因子无法直接纳入 GRN 框架，需通过其靶基因间接推断，可能遗漏直接调控关系。
- **群体/领域边界**：结论基于小鼠胚胎成纤维细胞体外培养系统，不适用于人类细胞或体内环境。
- **不确定性**：原文未报告置信区间或不确定性量化；统计检验主要为 Wilcoxon 检验和置换检验，未进行多重比较校正（部分分析）。
- **有边界的复述**：在 MEF→iEP 重编程系统中，CellOracle 结合 CellTag 谱系追踪可识别早期决定命运的 GRN 配置，并预测 Fos 和 Yap1 作为重编程的正向调控因子，实验验证支持该预测；但该结论限于此系统，且预测精度和机制细节仍有待进一步研究。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| Yap1 无法直接纳入 GRN 推断 | Yap1 不直接结合 DNA，CellOracle 无法对其直接建模 | 通过 Fos 靶基因间接推断 Yap1 作用 | Results 图 5A；Discussion |
| 预测需要实验验证 | in silico 预测的候选 TF 需通过实验确认 | 结合 Perturb-seq 等高通量验证方法 | Discussion |
| 重编程效率仍有限 | 即使加入 Fos/Yap1，重编程效率仍非 100% | 进一步解析 GRN 重构的完整机制 | Discussion |
| 细胞异质性 | 即使有谱系追踪，早期细胞群体仍存在异质性 | 更高分辨率的单细胞多组学技术 | Discussion |
| 未检测蛋白水平调控 | GRN 推断基于 mRNA 表达，无法捕捉翻译后修饰 | 整合蛋白质组学数据 | Discussion（隐含） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| Fos 在重编程中的"驱动"作用可能被高估 | Fos 可能是伴随性变化而非驱动因素；shRNA 敲低可能影响细胞增殖而非重编程特异性 | 若 Fos 非特异性作用，则基于其设计的重编程优化策略可能无效 | 进行 Fos 的诱导型过表达/敲除时间序列实验，区分早期与晚期作用；检测 Fos 敲低对细胞增殖、凋亡的非特异性影响 | Results 图 3F–3G；图 4G–4J |
| CellOracle 的 perturbation score 依赖线性网络传播假设 | 真实 GRN 存在非线性、反馈回路、竞争性结合等复杂动态，线性模型可能产生误导性预测 | 若模型假设不成立，则预测的候选 TF 可能不可靠 | 用非线性动力学模型（如 Boolean network、ODE 模型）对比预测结果；用更多实验验证预测的假阳性率 | Methods 节（perturbation simulation 描述） |
| 谱系追踪的克隆分辨率有限 | CellTag 系统可能无法完全追踪所有细胞命运，特别是低丰度克隆 | 若谱系追踪不完整，则"命运已定"的结论可能基于不完整数据 | 使用更高效的谱系追踪系统（如 CRISPR-Cas9 基因组编辑条形码）交叉验证 | Results 图 2A–2G |
| Yap1 的作用可能不依赖 Fos | Fos 靶基因中富集 Yap1 靶标，但 Fos 与 Yap1 可能平行作用于重编程而非上下游关系 | 若两者平行作用，则联合过表达的协同效应可能被错误归因 | 在 Fos 敲除背景下过表达 Yap1，检测是否仍能增强重编程；进行蛋白互作实验（Co-IP、CUT&Tag） | Results 图 5A–5G |
| 未报告多重比较校正 | 180 个 TF 的 perturbation score 排名涉及大量比较，可能产生假阳性 | 若存在假阳性，则候选 TF 列表可能包含无关因子 | 使用 FDR 校正或置换检验控制假阳性率；用独立数据集验证排名稳定性 | Results 图 3D（未报告校正方法） |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **多组学 GRN 推断范式**：将 scATAC-seq 的 motif 扫描（提供调控潜力）与 scRNA-seq 的表达相关性（提供调控活性）结合，构建"base GRN → context-specific GRN"的两步推断流程。可迁移到 TF–DNA 结合机制研究：在特定细胞类型/状态下，用染色质可及性限定候选结合位点，再用表达数据筛选活跃调控关系。
2. **In silico perturbation 作为虚拟筛选工具**：通过模拟 TF 敲除/过表达后的网络信号传播，计算 perturbation score 预测细胞命运变化方向。可迁移到 TF–DNA 结合研究：预测特定 TF 结合位点突变或 TF 表达改变对下游基因调控网络的影响。
3. **谱系追踪与网络状态关联**：将 CellTag 克隆追踪与 GRN 推断结合，将"分子状态"与"功能命运"直接关联。可迁移到 TF–DNA 结合研究：在异质性细胞群体中，将特定 TF 的结合模式（如 ChIP-seq 信号）与细胞命运（如分化方向）关联。
4. **网络中心性分析识别关键调控节点**：使用 degree/eigenvector centrality 和 network cartography 识别网络中的关键 TF。可迁移到 TF–DNA 结合研究：在 TF 互作网络中识别核心调控因子，优先进行功能验证。
5. **实验验证策略**：计算预测 → shRNA 敲低初筛 → 过表达验证 → CRISPR 敲除确认 → 单细胞转录组机制解析。可迁移到 TF–DNA 结合研究：建立"预测-验证"闭环，提高候选 TF 功能验证效率。
6. **TF 组合效应分析**：Fos 与 Yap1 的协同作用提示，单一 TF 分析可能不足以解释重编程机制，需考虑 TF 组合效应。可迁移到 TF–DNA 结合研究：研究 TF 协同结合（co-binding）对基因调控的叠加或协同效应。

## 15 与已有知识连接
- **CellOracle 原始方法**：Kamimoto et al., 2020（bioRxiv/期刊）——本文是 CellOracle 方法在直接重编程中的首次应用，方法细节可追溯至原始论文。
- **直接重编程范式**：Biddy et al., 2018（Nature）——本文使用的 MEF→iEP 重编程系统及 CellTag 谱系追踪方法源自该工作。
- **GRN 推断方法**：SCENIC（Aibar et al., 2017）、Pando（Fleck et al., 2022）——CellOracle 与这些方法同属"motif + 表达"整合推断范式，但 CellOracle 独有 perturbation simulation 功能。
- **AP-1 在重编程中的作用**：Vierbuchen et al., 2017（Nature Neuroscience）、Knaupp et al., 2017（Cell Stem Cell）——AP-1 在神经元重编程和多能性重编程中的增强子重塑作用，与本文 Fos 发现一致。
- **Yap1/Hippo 信号在再生中的作用**：Pepe-Mooney et al., 2019（Cell Stem Cell）、Yui et al., 2019（Nature Medicine）——Yap1 在肝脏和肠道再生中的作用，与本文 iEP 的再生细胞样表型一致。
- **TF 结合 motif 数据库**：Cis-BP、JASPAR——CellOracle 的 base GRN 构建依赖这些数据库的 motif 注释。
- **单细胞多组学整合**：本文属于"转录组 + 染色质可及性 + 谱系追踪"的多组学整合研究，与近年来单细胞多组学技术（如 10x Multiome）的发展趋势一致。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合动态与 GRN 重构的因果推断框架
   - **来源局限/观察**：CellOracle 的 GRN 推断基于稳态表达相关性，无法捕捉 TF 结合的时间动态；且未整合直接 TF–DNA 结合数据（如 ChIP-seq/CUT&Tag）。
   - **核心假设**：整合时间序列 ChIP-seq/CUT&Tag 数据可显著提高 GRN 推断的因果准确性，并识别"早期结合→晚期效应"的时序调控关系。
   - **初步方法**：在 CellOracle 框架中引入时间序列 TF 结合数据，构建"动态 GRN"；用 Granger causality 或转移熵替代静态相关性；在重编程时间序列数据上验证。
   - **验证方式**：与 CellOracle 静态 GRN 预测对比，用 CRISPR 干扰验证新预测的时序调控 TF。
   - **创新状态**：unverified

2. **候选名称**：基于深度学习的 TF–DNA 结合特异性预测增强 GRN 推断
   - **来源局限/观察**：CellOracle 的 base GRN 依赖传统 motif 扫描，无法捕捉 TF 结合特异性的上下文依赖性（如协同因子、染色质状态）。
   - **核心假设**：用深度学习模型（如 BPNet、DeepSEA）预测 TF 结合可显著降低 base GRN 的假阳性，提高 context-specific GRN 的准确性。
   - **初步方法**：用已训练的深度学习模型替换 motif 扫描步骤；或在 CellOracle 框架中引入"可解释性"层，识别关键序列特征。
   - **验证方式**：在已知 TF–DNA 互作数据集上比较 base GRN 精度；用重编程实验验证新预测的调控关系。
   - **创新状态**：partially checked（深度学习预测 TF 结合已有成熟方法，但整合到 GRN 推断框架中尚属新颖）

3. **候选名称**：TF 协同结合（co-binding）的 GRN 模块识别与重编程命运预测
   - **来源局限/观察**：CellOracle 的 perturbation 模拟假设 TF 独立作用，未考虑 TF 协同结合（如 AP-1 与 Yap1 的协同）。
   - **核心假设**：TF 协同结合模块（而非单个 TF）是重编程命运的决定单位，识别这些模块可提高命运预测精度。
   - **初步方法**：在 CellOracle GRN 中引入 TF–TF 共结合信息（从 ChIP-seq 共定位或 motif 共现推断）；用非负矩阵分解或图神经网络识别协同模块；将模块级 perturbation 模拟与单 TF 模拟对比。
   - **验证方式**：在 iEP 重编程系统中验证 Fos-Yap1 模块的预测；扩展到其他重编程系统。
   - **创新状态**：unverified

4. **候选名称**：物理模拟（MD/对接）与 GRN 推断的跨尺度整合
   - **来源局限/观察**：CellOracle 等 GRN 推断方法完全基于统计关联，缺乏对 TF–DNA 物理结合机制的描述。
   - **核心假设**：将分子动力学（MD）模拟或蛋白-DNA 对接预测的 TF–DNA 结合亲和力作为 GRN 边权重的先验，可提高 GRN 推断的物理合理性。
   - **初步方法**：对关键 TF（如 Fos、Hnf4α）进行 MD 模拟或使用 AlphaFold3 预测 TF–DNA 复合物结构；将结合自由能作为 GRN 边权重的先验；在 CellOracle 框架中整合。
   - **验证方式**：比较物理先验增强的 GRN 与原始 GRN 在重编程命运预测中的表现；用突变实验验证结合亲和力预测。
   - **创新状态**：unverified（跨尺度整合尚属空白）

5. **候选名称**：重编程失败状态的 GRN 吸引子分析与干预策略设计
   - **来源局限/观察**：本文识别了死胡同状态，但未深入分析其 GRN 吸引子结构，也未提出干预策略。
   - **核心假设**：死胡同状态对应 GRN 的稳定吸引子，通过识别吸引子间的"鞍点"或"关键转变边"，可设计最优干预策略（如 TF 组合扰动）将细胞从死胡同吸引子推向 iPE 吸引子。
   - **初步方法**：用 CellOracle GRN 构建布尔网络或 ODE 模型；用吸引子分析（如 R 包 BoolNet、pyBoolNet）识别死胡同与 iPE 吸引子；用最优控制理论设计干预策略。
   - **验证方式**：在 iEP 重编程系统中实验验证预测的干预策略（如 Fos+Yap1 过表达 + 死胡同标志基因敲低）。
   - **创新状态**：unverified