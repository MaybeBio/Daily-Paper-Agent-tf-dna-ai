## 01 基本信息
- **标题**：Dissecting crosstalk induced by cell-cell communication using single-cell transcriptomic data
- **作者与单位**：Hou, Jiawen; Zhao, Wei; Nie, Qing（单位未在摘要中提供）
- **期刊/预印本平台**：bioRxiv : the preprint server for biology
- **年份**：2025（预印本发布于2025-06-12；DOI 显示 2025.05.31 提交）
- **论文类型**：预印本（方法学论文）
- **领域**：单细胞转录组学、细胞间通讯（CCC）、基因调控网络（GRN）、机器学习
- **关键词**：cell-cell communication, crosstalk, single-cell RNA-seq, hypergraph learning, fidelity, specificity, transcription factors, target genes
- **DOI/arXiv 号**：10.1101/2025.05.31.657197
- **代码**：未提供
- **数据**：GSE152325（肠道谱系）、GSE103322（HNSCC）、SCP1219（COVID-19）、GSE141259（小鼠肺）、10x Genomics 小鼠脑空间转录组数据
- **阅读日期**：2026-05-13（基于系统日期）
- **在课题方向中的位置**：本文聚焦 CCC 诱导的细胞内信号通路之间的 crosstalk，核心对象是受体（信号）→ 转录因子（TF，共享信号组件 SSC）→ 靶基因（TG）的三层调控通路。与「TF–DNA 结合机制 × AI」课题直接相关：① 方法上采用超图学习（hypergraph learning）编码受体-TF-靶基因的高阶调控关系，可迁移至 TF–DNA 结合位点的多对多关系建模；② 引入 fidelity 和 specificity 两个量化指标，衡量信号-靶标之间的选择性，可类比 TF 对多个 DNA 基序的结合选择性；③ 使用随机森林（Random Forest）回归估计通路调控强度，可作为 TF–DNA 结合亲和力预测的基线方法。

## 02 一句话总结
SigXTalk 利用超图神经网络（HGNN）编码受体-转录因子-靶基因之间的高阶调控关系，通过随机森林回归估计通路调控强度（PRS），并引入 fidelity 和 specificity 两个指标量化 crosstalk 通路的选择性，在模拟数据和多个真实 scRNA-seq 数据集上验证了其识别共享调控组件和区分病理状态的能力。

## 03 研究问题
- **具体问题**：在细胞间通讯（CCC）中，不同配体-受体对激活的信号通路可能共享转录因子（TF）或靶基因，从而产生 crosstalk。现有方法（如 CellChat、NicheNet、CytoTalk）仅推断配体-受体、TF-靶基因或配体-靶基因的成对（pairwise）相互作用，忽略了多个通路之间通过共享组件产生的相互影响。本文要解决的核心问题是：**如何从 scRNA-seq 数据中系统识别并量化 CCC 诱导的 crosstalk 通路及其选择性？**
- **为什么重要**：Crosstalk 是信号转导的基本特征，决定了细胞对多个外部信号的整合响应。理解 crosstalk 有助于揭示疾病（如癌症、纤维化）中信号通路的异常激活机制，并为药物靶点提供依据。
- **现有方法不足**：① 成对相互作用方法无法捕捉超过两个基因的高阶调控关系；② 需要用户预先指定关注的通路或配体-受体对，缺乏系统性；③ 无法量化通路之间的相对贡献和选择性。
- **精确的「Can ... ?」研究问题**：Can a hypergraph-based machine learning framework accurately identify activated receptor-TF-target gene pathways from scRNA-seq data and quantify their fidelity and specificity in the presence of crosstalk?

## 04 背景与发展脉络
*注：以下脉络基于本文框架整理，部分外部信息未逐一核验，标注为「部分经外部核验」。*

1. **CCC 推断方法（第一代）**：CellChat、CellPhoneDB、Connectome 等，基于配体-受体数据库和基因表达估计通讯强度。局限：仅输出成对 LR 相互作用，不涉及下游调控。
2. **配体-靶基因映射方法（第二代）**：NicheNet 通过先验调控网络将配体连接到靶基因，CytoTalk 构建细胞间信号网络。局限：仍以成对关系为主，未显式建模通路间共享组件。
3. **GRN 推断方法（并行发展）**：GENELink、PIDC、GRNBoost2、SCENIC 等，从 scRNA-seq 推断 TF-靶基因调控网络。局限：不考虑上游配体-受体信号，无法连接 CCC 与下游调控。
4. **高阶关系建模（本文主张的位置）**：SigXTalk 首次将超图学习引入 CCC 下游调控分析，以受体、TF、靶基因为节点，以「信号-SSC-靶基因」三元组为超边，编码高阶调控关系。同时引入 fidelity/specificity 量化 crosstalk 选择性，填补了成对方法与系统级通路分析之间的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 忽略通路间 crosstalk | 现有方法仅推断成对 LR、TF-TG 或 L-TG 关系，无法识别共享 TF 或靶基因的多通路交叉调控 | 成对关系建模无法表达「多个信号→同一 TF→多个靶基因」的高阶结构 | Introduction 第 1-2 段；Results 图 1b-c |
| 缺乏系统性通路分析 | 用户需预先指定关注的配体-受体对或通路，无法自动发现 crosstalk 模块 | 方法设计依赖先验知识，未利用数据驱动的高阶关系挖掘 | Introduction 第 3 段 |
| 无法量化通路选择性 | 现有方法输出调控强度或概率，但不区分「信号对靶标的专属贡献」与「共享贡献」 | 缺少 fidelity/specificity 这类相对度量指标 | Results 图 1e；Methods「Measuring the pathway fidelity and specificity」节 |
| 成对 GRN 方法在 crosstalk 场景下性能下降 | 模拟数据中，12 种 GRN 方法在恢复含共享组件的通路时 AUROC/AUPRC 显著低于 SigXTalk | 成对方法无法利用高阶上下文信息，低估共享组件的调控作用 | Results 图 2b-c；Discussion 第 2 段 |

## 06 核心思想
1. **表面方法**：构建受体-转录因子-靶基因三层超图，用 HGNN 编码节点特征，预测三元组形成通路的概率（PA），再用随机森林回归估计通路调控强度（PRS），最后基于 PRS 计算 fidelity 和 specificity。
2. **核心洞察**：Crosstalk 的本质是多个信号通路共享中间组件（TF）或下游靶标。将「信号-SSC-靶基因」建模为超边（而非成对边），可以同时捕捉「一个信号调控多个靶基因」和「多个信号调控一个靶基因」的高阶关系。Fidelity 和 specificity 分别从信号→靶标和靶标→信号两个方向量化选择性，形成互补的 crosstalk 度量。
3. **可能的普适教训 [Analysis]**：① 生物调控网络中的「共享组件」是功能模块化的关键，超图是比普通图更自然的建模工具；② 「选择性」度量（fidelity/specificity）比绝对强度更能刻画调控的生物学意义，可推广到 TF–DNA 结合特异性分析；③ 自监督训练策略（用高置信度先验关系生成正样本）在缺乏 ground truth 的真实数据中具有实用价值。

## 07 方法总览
- **输入**：scRNA-seq 表达矩阵（基因 × 细胞）、细胞聚类标签、先验基因互作数据库（NicheNet 数据库，含受体-TF 和 TF-靶基因关系）
- **输出**：激活通路列表（PA > 0.75）、通路调控强度（PRS）、fidelity/specificity 值、crosstalk 模块（Xmod）注释
- **模块**：
  1. 数据预处理（Seurat 标准化、缩放）
  2. CCC 推断（CellChat 识别激活受体）
  3. 超图构建（节点 = 基因，超边 = 信号-SSC-靶基因三元组）
  4. HGNN 编码（HGNNConv+ 卷积层 + MLP）
  5. 通路激活预测（PA 值）
  6. PRS 回归（随机森林）
  7. Fidelity/specificity 计算
- **训练**：监督或自监督；正样本 = 先验数据库中高置信度三元组，负样本 = 随机组合
- **反馈回路**：无显式反馈回路；超图结构固定，训练仅更新 HGNN 参数
- **文字流程**：输入表达矩阵 → 预处理 → CellChat 识别激活受体 → 结合先验数据库构建超图 → HGNN 编码节点 → MLP 预测三元组 PA → 过滤 PA > 0.75 的激活通路 → 随机森林回归估计 PRS → 按 Xmod 类型计算 fidelity/specificity → 输出 crosstalk 分析结果

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 超图构建 | 将受体-TF-靶基因三元组编码为超边 | 成对边无法表达高阶调控关系 | 输入：先验数据库 + 激活受体列表；输出：超图 H=(V,E) | Methods「Construction of intracellular regulatory hypergraph」节 | [预期] 退化为成对图，丢失共享组件信息，crosstalk 识别能力下降 |
| HGNN 编码（HGNNConv+） | 通过超图卷积聚合邻居信息，生成节点低维表示 | 需要融合高阶拓扑结构到节点特征 | 输入：超图 + 表达矩阵；输出：节点嵌入 z | Methods「Identifying activated regulatory pathways」节；公式 (5) | [预期] 无法捕捉跨通路上下文，PA 预测精度下降 |
| PA 预测（MLP） | 估计三元组形成通路的概率 | 区分激活与未激活通路 | 输入：节点嵌入拼接；输出：PA ∈ [0,1] | 公式 (6)-(7) | [预期] 无法筛选激活通路，下游分析失效 |
| PRS 回归（随机森林） | 估计信号对 SSC-靶基因对的调控强度 | 需要量化调控强度而非仅二分类 | 输入：信号表达 + SSC-靶基因表达；输出：PRS | Methods「Measuring the pathway fidelity and specificity」节；公式 (10) | [预期] 无法计算 fidelity/specificity |
| Fidelity/specificity 计算 | 量化通路选择性 | 回答「信号对靶标的专属贡献」和「靶标对信号的专属响应」 | 输入：PRS 值；输出：fidelity/specificity ∈ [0,1] | 公式 (11)-(14) | [预期] 退化为仅输出 PRS，无法区分 crosstalk 方向性 |
| 自监督训练策略 | 无 ground truth 时生成训练样本 | 真实数据缺乏已知通路标签 | 输入：先验数据库 + 表达数据；输出：正/负样本 | Methods「Training of the hypergraph neural network」节 | [预期] 需依赖人工标注，难以扩展到新数据集 |

## 09 关键公式符号
| 公式 | 符号含义 | 用途 | 直觉 | 来源 |
|------|----------|------|------|------|
| (1) P_ijk = (L_i R_j)/(K_h + L_i R_j) × (1 + AG_i)/(K_h + AG_i) × (1 + AG_j)/(K_h + AG_j) × K_h/(K_h + AN_i) × K_h/(K_h + AN_j) × (n_i n_j)/n² | L_i, R_j：配体/受体表达；AG, AN：激动剂/拮抗剂；K_h：Hill 常数；n：细胞数 | CellChat 通讯强度计算 | 质量作用定律 + Hill 函数，考虑辅助分子和细胞群大小 | Methods「Inference of cell-cell communication」节 |
| (3) SH(v_si, v_cj, v_tk) = PPR(x_si, x_cj) × Cor(x_cj, x_tk) | PPR：个性化 PageRank 分数；Cor：Spearman 相关系数 | 三元组初始超边权重 | 信号→TF 用网络拓扑距离，TF→靶基因用表达相关性 | Methods「Construction of intracellular regulatory hypergraph」节 |
| (5) Z_{k+1} = σ(D_v^{-1} H D_e H^T Z_k Θ_k) | H：关联矩阵；D_v, D_e：节点/超边度矩阵；Θ：可训练参数；σ：ELU | HGNN 层更新 | 节点特征经超边聚合邻居信息 | Methods「Identifying activated regulatory pathways」节 |
| (7) PA(v_si, v_cj, v_tk) = Cos(y_si, y_cj) × Cos(y_cj, y_tk) | y：MLP 输出嵌入；Cos：余弦相似度 | 通路激活概率 | 信号-SSC 和 SSC-靶标两段嵌入的相似度乘积 | 公式 (7) |
| (11) Fid(e_q) = PRS(e_q) / Σ_{e_r ∈ XMt(v_tk)} PRS(e_r) | PRS：通路调控强度；XMt：靶标共享模块 | 靶标视角的 fidelity | 该通路对靶标的贡献占所有共享通路总贡献的比例 | Methods「Measuring the pathway fidelity and specificity」节 |
| (12) Spe(e_q) = PRS(e_q) / Σ_{e_r ∈ XMs(v_si)} PRS(e_r) | XMs：信号共享模块 | 信号视角的 specificity | 该通路对靶标的贡献占该信号所有通路总贡献的比例 | 同上 |
| (13) TRS(v_si, v_tk) = Σ_j PRS(v_si, v_cj, v_tk) | TRS：总调控强度 | 信号-靶标对的汇总强度 | 对所有中间 TF 求和 | 同上 |
| (18) ACI_mk = (x_k,m y_k,m)/(K_h + x_k,m y_k,m) | x, y：受体/TF 表达 | 单细胞通路激活指数 | 与 CellChat 相同的 Hill 函数形式 | Methods「Estimating the activation of pathways in an individual cell」节 |

## 10 实验设计与证据链
- **数据集**：
  - 模拟数据：SERGI O 生成，200 基因，1,500 细胞，3 个聚类；10 次独立重复
  - HNSCC：GSE103322，15,467 细胞，9,842 基因，8 个主要聚类
  - COVID-19 肺：SCP1219，4,636（COVID）/ 5,668（HC）细胞
  - 小鼠肺损伤：GSE141259，bleomycin 处理多时间点
  - 小鼠脑空间转录组：10x Visium
- **指标**：AUROC、AUPRC（模拟数据）；重叠率、Fisher 精确检验 p 值、卡方检验 p 值（HNSCC 共享 TF 识别）；t 检验 p 值（COVID 通路比较）
- **基线**：12 种 GRN 方法（GENELink, PIDC, GRNVBEM, GRNBoost2, PPCOR, SCODE, SINCERITIES, LEAP, GRISLI, SINGE, Scribe, SCSGL）；NicheNet（两种策略：NicheNet-db, NicheNet-comp）；CytoTalk
- **评测协议**：模拟数据中 80% 训练 / 20% 测试；真实数据中与先验数据库（KEGG）比对

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| 模拟数据通路恢复 | SigXTalk 能恢复激活通路 | 13 种方法，10 次独立模拟 | SigXTalk AUROC/AUPRC 最高，比第二名高 15%/20% | 超图学习优于成对方法 | 模拟数据可能简化了真实调控复杂性 | Results 图 2b-c |
| HNSCC 共享 TF 识别 | SigXTalk 识别共享 TF 优于 NicheNet/CytoTalk | 3 种方法，CAF 为接收细胞 | SigXTalk 平均重叠率 36%，p 值更显著 | 超图方法更擅长识别 crosstalk 共享组件 | 仅验证了 TF 层面，未验证下游靶基因 | Results 图 2e；Supplementary Table 1 |
| COVID vs HC 通路比较 | SigXTalk 能区分病理状态 | CD44/PTPRM 信号，COVID vs HC | CD44 通路数增加但 PRS 降低；PTPRM fidelity 升高 | crosstalk 模式随病理状态改变 | 样本量小（单患者 vs 单对照） | Results 图 5d-f |
| 时间序列追踪 | SigXTalk 能追踪 crosstalk 演化 | 小鼠肺 bleomycin 损伤 3 时间点 | 通路数随时间增加，fidelity 变化 | crosstalk 是动态过程 | 未与实验验证对照 | Results 图 6 |
| 空间数据细化 | SigXTalk 能细化空间 CCC | 小鼠脑 Visium 数据 | 识别出空间邻近的通讯细胞 | 可结合空间信息 | 仅一个数据集 | Results 图 7 |

## 11 结论正确解读
- **任务范围**：本文解决的是「CCC 信号 → 胞内 TF → 靶基因」这一特定层级的 crosstalk 识别与量化，不涉及配体-受体结合本身、也不涉及 TF 与 DNA 的物理结合机制。
- **oracle/真值输入**：模拟数据使用 SERGIO 生成的已知调控网络作为 ground truth；真实数据使用 KEGG 通路数据库作为先验，但 KEGG 并非细胞类型特异的 oracle。
- **端到端状态**：方法依赖 CellChat 预选激活受体，并非完全端到端；超图结构依赖先验数据库，非纯数据驱动。
- **算力成本**：未报告具体训练时间或硬件需求；HGNN 结构轻量，预期可在标准 GPU 上运行。
- **历史数据依赖**：需要先验基因互作数据库（NicheNet 数据库），对新物种或非模式生物适用性受限。
- **模型依赖**：性能依赖 CellChat 的受体激活判断和 NicheNet 数据库的覆盖度。
- **最难情形**：低表达 TF 被过滤、先验数据库中缺失的调控关系、高度重叠的 crosstalk 模块。
- **群体/领域边界**：方法在 HNSCC、COVID-19 肺、小鼠肺损伤、小鼠脑中验证，未覆盖植物、微生物等非动物系统。
- **不确定性**：fidelity/specificity 基于 PRS 的比例计算，PRS 本身来自随机森林的置换重要性，存在估计方差；未报告置信区间。

**有边界的复述**：SigXTalk 在模拟数据上优于 12 种成对 GRN 方法，在 HNSCC 中比 NicheNet/Cyrotalk 更准确地识别共享 TF，并能区分 COVID-19 与健康对照的 crosstalk 模式；但方法依赖先验数据库和 CellChat 预选，未验证 TF–DNA 物理结合层面的预测。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 静态表达数据 | 通路调控强度基于静态 scRNA-seq 表达谱，无法捕捉动态调控 | 引入时间序列数据或 RNA 速率分析 | Discussion 第 3 段 |
| 简化通路结构 | 仅考虑受体-TF-靶基因三层结构，忽略中间激酶等信号分子 | 扩展超图以包含更多中间节点类型 | Discussion 第 3 段 |
| 先验数据库依赖 | 超图构建依赖 NicheNet 数据库，可能遗漏未知调控关系 | 结合无监督/自监督方法减少先验依赖 | Discussion 第 4 段 |
| 低表达 TF 过滤 | 低表达但功能重要的 TF 可能被过滤 | 采用更敏感的检测技术或插补方法 | Discussion 第 4 段 |
| 缺乏实验验证 | 真实数据预测未通过湿实验（如敲除/过表达）验证 | 与实验团队合作进行功能验证 | Discussion 第 5 段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 模拟数据中 SigXTalk 优势可能被高估 | SERGIO 模拟数据由已知调控网络生成，SigXTalk 的超图结构直接编码了该网络的三元组形式，存在「方法-数据同构」偏差 | 模拟基准可能对超图方法有利，成对方法天然劣势 | 使用不依赖三元组结构的模拟器（如 Boolean 网络）或真实数据交叉验证 | Results 图 2；Methods「Method evaluation using simulated datasets」节 |
| fidelity/specificity 定义依赖 PRS 估计质量 | 随机森林置换重要性对特征相关性敏感，共享 TF 的高相关性可能导致 PRS 估计偏差 | 若 PRS 有偏，fidelity/specificity 的生物学解释可能失真 | 使用多种回归方法（如 LASSO、GAM）交叉验证 PRS 稳定性 | Methods「Measuring the pathway fidelity and specificity」节 |
| 与 NicheNet/Cyrotalk 的比较可能不公平 | NicheNet 和 Cyrotalk 设计目标不同（配体-靶标映射 vs 全网络构建），直接比较共享 TF 识别可能低估其能力 | 方法比较需在同一任务定义下进行 | 设计统一任务（如已知 crosstalk 通路恢复）重新评估 | Results 图 2e |
| 超图构建依赖先验数据库的「正确性」 | NicheNet 数据库可能包含组织非特异性或错误的调控关系，导致超图结构噪声 | 先验噪声会传播到下游所有分析 | 使用多个数据库（如 TRRUST、RegNetwork）进行敏感性分析 | Methods「Prior databases of intracellular gene-gene interactions」节 |
| 未报告计算资源与运行时间 | 方法实用性评估缺少计算成本信息 | 大规模数据集（>10 万细胞）的可扩展性未知 | 补充运行时间、内存占用随数据规模变化的基准测试 | 全文未提供 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **超图建模高阶调控关系**：将「信号-SSC-靶基因」三元组建模为超边，而非分解为成对边，可保留共享组件的上下文信息。**迁移到 TF–DNA 结合**：可将「TF-辅因子-靶基因」或「多个 TF-同一增强子」建模为超边，捕捉协同结合（cooperative binding）和竞争结合的高阶关系。

2. **Fidelity/specificity 作为选择性度量**：fidelity 衡量靶标视角的信号贡献分配，specificity 衡量信号视角的靶标优先级。**迁移到 TF–DNA 结合**：可定义 TF 对多个 DNA 基序的 binding fidelity（某基序占该 TF 总结合的比例）和 binding specificity（某 TF 对某基序的专属结合程度），用于量化 TF 结合选择性。

3. **自监督训练策略**：无 ground truth 时，用先验数据库高置信度关系生成正样本，随机组合生成负样本。**迁移到 TF–DNA 结合**：可用已知 TF 结合位点（如 JASPAR、CIS-BP）作为正样本，随机基因组序列作为负样本，训练结合预测模型。

4. **HGNN 用于基因调控网络嵌入**：HGNNConv+ 通过超图卷积聚合邻居信息，生成节点嵌入。**迁移到 TF–DNA 结合**：可将 TF、DNA 基序、靶基因构建为异质超图，用 HGNN 学习 TF 和基序的联合嵌入，用于结合位点预测。

5. **随机森林置换重要性估计调控强度**：用置换重要性作为 PRS，避免神经网络黑箱问题。**迁移到 TF–DNA 结合**：可用随机森林评估每个序列特征（如基序位置、GC 含量、染色质可及性）对 TF 结合亲和力的贡献。

6. **时间序列 crosstalk 追踪**：通过多时间点数据比较 fidelity/specificity 变化，揭示调控重编程。**迁移到 TF–DNA 结合**：可在细胞分化或刺激时间序列中追踪 TF 结合特异性的动态变化。

## 15 与已有知识连接
- **CellChat (Jin et al., 2021, Nature Communications)**：本文使用 CellChat 进行 CCC 推断，CellChat 的 Hill 函数模型被直接复用（公式 1）。**连接点**：CellChat 提供受体激活的先验，SigXTalk 在其下游增加胞内调控分析。
- **NicheNet (Browaeys et al., 2020, Nature Methods)**：本文使用 NicheNet 数据库构建先验调控网络，并作为基线方法比较。**连接点**：NicheNet 的配体-靶标先验矩阵可被 SigXTalk 的超图构建直接采用。
- **CytoTalk (Hu et al., 2021, Nature Methods)**：作为基线方法比较。**连接点**：CytoTalk 构建细胞间信号网络，SigXTalk 可视为其胞内 crosstalk 扩展。
- **HGNN (Feng et al., 2019, AAAI)**：HGNNConv+ 层基于超图神经网络框架。**连接点**：超图卷积的数学框架可直接迁移到 TF–DNA 结合位点预测。
- **SERGIO (Dibaeinia & Sinha, 2020, Cell Systems)**：模拟数据生成器。**连接点**：可用于生成具有已知 crosstalk 结构的 TF–DNA 调控模拟数据。
- **SCENIC (Aibar et al., 2017, Nature Methods)**：GRN 推断与 TF 活性分析。**连接点**：SCENIC 的 regulon 概念与本文的「信号-SSC-靶基因」通路类似，但 SCENIC 不建模 crosstalk。
- **[候选方向] TF–DNA 结合预测 (DeepBind, Alipanahi et al., 2015)**：本文的超图方法可扩展至 TF-基序-靶基因三元组预测，与 DeepBind 的序列-结合预测互补。

## 16 研究想法
**Agent 生成的研究候选**：

1. **TF–DNA 结合选择性超图模型（TF-Bind-Hyper）**
   - **来源局限/观察**：SigXTalk 的超图框架仅用于转录组数据，未利用 DNA 序列信息；TF–DNA 结合预测方法（如 DeepBind）仅考虑成对 TF-基序关系，忽略 TF 间协同/竞争。
   - **核心假设**：将 TF、DNA 基序、靶基因构建为超图，可捕捉「多 TF 协同结合同一增强子」和「一 TF 结合多基序」的高阶关系，提升结合位点预测精度。
   - **增量**：在 SigXTalk 超图框架中加入 DNA 序列编码（如 k-mer 嵌入），预测 TF-基序-靶基因三元组的结合概率。
   - **初步方法**：构建 TF-基序-靶基因超图，节点特征 = 表达 + 序列嵌入，超边 = 已知结合关系（ENCODE ChIP-seq），HGNN 编码后预测新结合位点。
   - **验证方式**：使用 ENCODE 或 Cistrome 数据库的 ChIP-seq 数据，与 DeepBind、DeepSEA 比较 AUROC/AUPRC。
   - **创新状态**：unverified

2. **TF 结合 fidelity/specificity 的跨细胞类型比较**
   - **来源局限/观察**：SigXTalk 的 fidelity/specificity 定义在信号-靶标层面，未细化到 TF–DNA 结合层面；不同细胞类型中同一 TF 的结合选择性可能不同。
   - **核心假设**：同一 TF 在不同细胞类型中的 binding fidelity/specificity 差异可预测细胞类型特异的增强子-启动子互作。
   - **增量**：将 fidelity/specificity 从信号-靶标扩展到 TF-基序层面，定义 binding fidelity（某基序占 TF 总结合的比例）和 binding specificity（TF 对某基序的专属结合）。
   - **初步方法**：使用 scATAC-seq 数据推断 TF 结合位点，计算每个细胞类型中的 binding fidelity/specificity，与 SigXTalk 的 crosstalk 分析结合。
   - **验证方式**：与 CRISPR 干扰（CRISPRi）验证的增强子-基因对比较，检验预测准确性。
   - **创新状态**：unverified

3. **时间序列 crosstalk 动态追踪框架（TimeXTalk）**
   - **来源局限/观察**：SigXTalk 仅处理静态数据，但 crosstalk 是动态过程（如发育、疾病进展）。
   - **核心假设**：将 SigXTalk 扩展至时间序列 scRNA-seq 数据，可追踪 crosstalk 通路的动态重编程，识别关键转换点。
   - **增量**：在超图框架中加入时间维度，用循环神经网络或神经 ODE 建模通路强度的时间演化。
   - **初步方法**：对 bleomycin 肺损伤数据（GSE141259）按时间点分别运行 SigXTalk，比较 fidelity/specificity 的时间轨迹，识别关键 TF 转换。
   - **验证方式**：与已知肺纤维化时间线（炎症期→增殖期→纤维化期）对照，检验识别的转换点是否与病理阶段吻合。
   - **创新状态**：partially checked（本文已展示时间点分析，但未建模连续动态）

4. **空间转录组 crosstalk 细化（SpatialXTalk）**
   - **来源局限/观察**：SigXTalk 在空间数据中仅用于验证 CCC 距离，未利用空间信息改进 crosstalk 推断。
   - **核心假设**：空间邻近的细胞对之间的 crosstalk 通路与远距离细胞对不同，空间约束可提高 crosstalk 推断的特异性。
   - **增量**：在超图构建中加入空间距离权重，邻近细胞的信号-靶标关系赋予更高权重。
   - **初步方法**：使用 Visium 数据，将空间坐标编码为超边权重，比较加权与未加权模型的 crosstalk 识别差异。
   - **验证方式**：与配体-受体共表达的空间共定位分析比较，检验空间特异性。
   - **创新状态**：unverified

5. **crosstalk 驱动的药物靶点预测（DrugXTalk）**
   - **来源局限/观察**：SigXTalk 可识别疾病特异性的 crosstalk 通路，但未连接药物反应数据。
   - **核心假设**：疾病中 fidelity/specificity 异常的 crosstalk 通路可作为药物靶点，靶向共享 TF 可同时抑制多条异常通路。
   - **增量**：将 SigXTalk 输出与药物-靶点数据库（如 DrugBank）整合，预测靶向 crosstalk 枢纽 TF 的药物。
   - **初步方法**：在 HNSCC 数据中识别高 crosstalk 的 TF，查询已知药物靶点，预测可能有效的药物组合。
   - **验证方式**：使用药物敏感性数据（如 GDSC、CCLE）检验预测药物的敏感性关联。
   - **创新状态**：unverified