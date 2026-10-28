## 01 基本信息

- **标题**：SIGNET: single-cell RNA-seq-based gene regulatory network prediction using multiple-layer perceptron bagging
- **作者**：Luo, Qinhuan; Yu, Yongzhen; Lan, Xun
- **单位**：未提供（推测为清华大学，依据基金信息）
- **期刊/平台**：Briefings in Bioinformatics
- **年份**：2021-12-29（在线发表）
- **论文类型**：方法学（Method）论文
- **领域**：单细胞转录组学；基因调控网络（GRN）推断；深度学习
- **关键词**：gene regulatory network; single-cell RNA-seq; deep learning; multilayer perceptron; bagging
- **DOI/arXiv 号**：10.1093/bib/bbab547
- **代码**：https://github.com/Lan-lab/SIGNET
- **数据**：GSE60361（小鼠大脑皮层）、GSE115978（人皮肤黑色素瘤）、GSE103322（人头颈鳞癌）、GSE109774（小鼠多器官）；ChIP-seq 数据来自 http://chip-atlas.org/
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「TF–DNA 互作 × 深度学习」交叉方向，但**不涉及物理模拟或结构预测**。其核心贡献在于：以 TF 表达作为预测因子、以靶基因表达作为响应变量，通过 MLP + bagging 学习 TF→靶基因的非线性调控关系，再以 motif 富集（RcisTarget）验证直接结合，最终以 AUCell 打分表征 regulon 活性。对 TF–DNA 结合机制课题的可迁移点在于：**将 TF 表达扰动（case-deletion）作为识别调控边界的因果近似手段**，以及**将 motif 富集作为直接结合的验证层**。

---

## 02 一句话总结

SIGNET 提出一个三阶段框架：先用 MLP 以全部 TF 的二元表达预测每个靶基因的表达，再用 case-deletion 方法逐一删除 TF 并观察预测精度变化以识别候选 TF–靶基因调控对，随后用 RcisTarget 的 motif 富集过滤出可能直接结合的 regulon，最后用 AUCell 对 regulon 活性打分并用于细胞聚类；在三个 scRNA-seq 数据集上，SIGNET 比 SCENIC 对 ChIP-seq 验证的 TF–靶基因互作具有更高灵敏度，且对稀有细胞类型的 regulon 识别更稳健。

---

## 03 研究问题

- **具体问题**：如何从单细胞 RNA-seq 数据中推断 TF 与其靶基因之间的调控关系（GRN），特别是如何捕捉非线性/非单调的调控模式，并提高对稀有细胞类型中调控模块的识别能力？
- **为什么重要**：基因调控网络是理解细胞命运决定、疾病机制的核心。单细胞数据提供了细胞异质性分辨率，但调控关系复杂、非线性，传统线性模型（如相关性、回归）难以捕捉。稀有细胞（如肿瘤干细胞、祖细胞）中的调控模块往往被淹没在群体信号中。
- **现有方法不足**：线性回归/相关性方法无法建模非线性调控；SCENIC 虽用随机森林（可捕捉非线性），但其输入为全部基因，对稀有细胞信号不敏感，且其调控对识别依赖共表达模块，缺乏对单个 TF 贡献的显式量化。
- **精确研究问题（Can...?）**：Can a multilayer perceptron with case-deletion-based feature importance, combined with motif enrichment filtering, infer TF–target gene regulatory interactions from single-cell RNA-seq data with higher sensitivity to ChIP-seq-validated binding events than existing methods (e.g., SCENIC), particularly for rare cell populations?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论，属于「仅本文框架」，未经外部系统核验。

1. **线性回归/相关性方法**（如 WGCNA、GENIE3 的线性版本）：简单、可解释，但无法捕捉非线性/非单调调控。
2. **信息论方法**（如互信息、PIDC）：可捕捉非线性，但对噪声敏感，且不区分直接/间接调控。
3. **基于树的集成方法**（如 GENIE3、GRNBoost2）：可捕捉非线性，但缺乏对调控方向的显式建模。
4. **SCENIC**：将随机森林预测的 TF–靶基因共表达模块与 motif 富集（RcisTarget）结合，再以 AUCell 打分。优点：整合了顺式调控序列信息；缺点：对稀有细胞不敏感，且随机森林的变量重要性度量不如 case-deletion 直接。
5. **深度学习在 scRNA-seq 中的应用**：此前多用于 dropout 插补（如 DCA、scVI）和细胞聚类，**很少用于 GRN 推断**。本文是较早将 MLP 用于 GRN 推断的工作之一。
6. **SIGNET 的位置**：在 SCENIC 的「共表达 + motif 验证」框架上，将共表达模块识别替换为 MLP + case-deletion 的「预测精度扰动」度量，以更直接地量化单个 TF 对靶基因表达的因果贡献（在观察数据意义下）。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 线性模型无法捕捉复杂调控 | 调控关系常为非线性或非单调，线性模型漏检大量真实互作 | 基因调控涉及多个 TF 协同、反馈、剂量效应 | Abstract: "complex and often nonlinear or nonmonotonic, which makes their inference using linear models challenging" |
| 稀有细胞类型调控模块丢失 | 稀有细胞（如 19 个肌细胞）被当作噪声，无法识别其特异 regulon | 群体中稀有细胞信号被主导群体掩盖；SCENIC 使用全部基因作为输入，稀有细胞贡献被稀释 | Results: SIGNET 准确聚类 19 个肌细胞并识别 MYF5/MYF6/MYOG regulon，而 SCENIC 将肌细胞与成纤维细胞混为一类（图 5B） |
| 现有方法对直接结合验证不足 | 共表达不等于直接结合，假阳性率高 | 共表达模块可能由间接调控或共调控产生 | 方法：引入 RcisTarget motif 富集作为第二层过滤 |
| 类别不平衡导致预测偏差 | 靶基因表达二元化后正负样本比例严重失衡 | 大多数细胞中基因不表达（0）远多于表达（1） | Methods: "columns of the binary matrix may possess an unbalanced distribution of positive and negative cases... we used bootstrapping to generate new columns with a ratio not less than 1:5" |
| 稀有细胞对全局模型影响小 | 删除稀有细胞中高表达的 TF 对整体预测精度影响微弱，难以检测 | 稀有细胞在总样本中占比极低，其信号被稀释 | Discussion: "the few microglial cells in the downsampled cluster that were regarded as noise affected the computation of the entire dataset"（作者对 SCENIC 的解释） |

---

## 06 核心思想

### 1) 表面方法
- 数据预处理：基因过滤 + Hodges-Lehmann 估计器（HLE）对每个基因的表达进行二元化（0/1）。
- 对每个靶基因训练一个 3 层 MLP，输入为所有 TF 的二元表达，输出为该靶基因的二元表达预测。
- 用 bagging（bootstrap）重采样平衡正负样本比例（≤1:5）。
- 用 case-deletion 方法：逐一将某个 TF 的表达置 0，重新预测靶基因，计算预测精度变化（ACC 矩阵），用广义极端学生化偏差检验（gESD）识别显著离群 TF。
- 用 RcisTarget 对候选 TF–靶基因对做 motif 富集过滤，保留可能直接结合的 regulon。
- 用 AUCell 对 regulon 在每细胞中的活性打分，用于聚类和下游分析。

### 2) 核心洞察
- **预测精度扰动作为调控边界的代理**：如果一个 TF 对靶基因的预测精度有显著影响（删除后精度下降），则该 TF 很可能调控该靶基因。这比相关性或变量重要性更直接地反映了「去除该 TF 后系统行为变化」的因果含义（在观察数据框架内）。
- **二元化 + bagging 解决稀疏性问题**：单细胞数据 dropout 严重，二元化降低噪声敏感性；bagging 平衡类别，使稀有细胞中表达的基因（正样本）不被淹没。
- **motif 富集作为直接结合的验证层**：共表达/预测关系可能是间接的，motif 富集提供顺式调控证据，将「预测的调控对」升级为「可能的直接结合事件」。

### 3) 可能的普适教训 [Analysis]
- **对 TF–DNA 结合机制课题的启示**：在缺乏 ChIP-seq 或 ATAC-seq 的实验场景下，可以用「表达预测扰动」作为 TF–靶基因调控关系的计算代理，再用 motif 扫描作为直接结合的验证。这种「计算预测 → 序列验证」的两层架构可迁移到其他物种或细胞类型。
- **稀有细胞信号增强**：通过重采样平衡类别，可以显著提升稀有细胞中调控模块的检出率。这对研究肿瘤干细胞、组织祖细胞等稀有群体的 TF 调控网络尤为重要。
- **非线性模型的敏感性优势**：MLP 比线性模型更能捕捉非单调调控（如双相剂量响应），这对 TF 浓度依赖的结合机制研究有参考价值。

---

## 07 方法总览

- **输入**：单细胞 RNA-seq 表达矩阵（细胞 × 基因），TF 列表（来自 pySCENIC 资源）。
- **输出**：TF–靶基因调控对（regulon 列表）；每细胞 regulon 活性打分矩阵（AUC 矩阵）；细胞聚类结果。
- **模块**：
  1. 预处理模块：基因过滤（高变基因）、HLE 二元化。
  2. MLP 预测模块：对每个靶基因训练一个 3 层全连接 MLP（ReLU 激活，交叉熵损失，L1 正则化），输入为所有 TF 的二元表达。
  3. Bagging 模块：bootstrap 重采样训练数据，控制正负样本比例 ≤1:5。
  4. Case-deletion 模块：逐一删除 TF（置 0），计算预测精度变化，生成 ACC 矩阵。
  5. 统计检验模块：gESD 检验（α=0.05）识别显著离群 TF。
  6. Motif 富集模块：RcisTarget 对候选 TF–靶基因对做 motif 富集，过滤出 regulon。
  7. 活性打分模块：AUCell 计算每细胞 regulon 活性。
- **训练**：随机梯度下降（momentum），学习率 0.01，训练/测试 7:3 划分。
- **反馈回路**：无显式反馈回路；各模块串联执行。
- **文字流程**：原始表达矩阵 → 基因过滤 → HLE 二元化 → 对每个靶基因用 bagging 训练 MLP → 对每个 TF 做 case-deletion 并计算 ACC → gESD 检验筛选显著 TF → 候选 TF–靶基因对 → RcisTarget motif 富集 → regulon 列表 → AUCell 打分 → 细胞聚类/下游分析。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| HLE 二元化 | 将表达量转为 0/1 | 降低 dropout 噪声，使 MLP 输出为二分类 | 输入：原始计数矩阵；输出：二元矩阵 | Methods 公式 (2)–(4) | 预期：模型对表达水平的定量信息不敏感，可能丢失剂量效应 [预期效应，未实测] |
| MLP 预测器 | 以 TF 表达预测靶基因表达 | 捕捉非线性/非单调调控 | 输入：所有 TF 的二元表达（每细胞）；输出：靶基因二元表达预测 | Methods "Prediction of the relationship between genes" | 移除后退化为线性模型，可能漏检非线性调控 [预期效应，未实测] |
| Bagging（bootstrap） | 平衡正负样本比例 | 解决类别不平衡，提升稀有细胞信号 | 输入：原始训练集；输出：重采样后的平衡训练集 | Methods: "ratio not less than 1:5" | 预期：移除后稀有细胞 regulon 检出率下降 [预期效应，未实测] |
| Case-deletion 重要性 | 删除 TF 后观察预测精度变化 | 直接量化单个 TF 对靶基因的调控贡献 | 输入：训练好的 MLP + 二元矩阵；输出：ACC 矩阵（M×N） | Methods 公式 (7)–(8) | 移除后无法识别调控对，整个方法失效 [核心模块] |
| gESD 检验 | 识别显著离群 TF | 统计筛选而非阈值截断 | 输入：ACC 矩阵；输出：显著 TF 列表 | Methods 公式 (9)–(10) | 预期：替换为简单阈值可能增加假阳性 [预期效应，未实测] |
| RcisTarget motif 富集 | 验证 TF 是否可能直接结合靶基因启动子 | 过滤间接调控，提供顺式调控证据 | 输入：候选 TF–靶基因对 + 基因组序列；输出：regulon 列表 | Methods "RcisTarget" | 移除后保留共表达/预测关系，但假阳性增加 [预期效应，未实测] |
| AUCell 活性打分 | 量化 regulon 在每细胞的活性 | 连接 regulon 与细胞状态 | 输入：regulon 基因集 + 表达矩阵；输出：AUC 矩阵 | Methods "AUCell" | 移除后无法进行基于 regulon 的聚类和下游分析 [核心模块] |

---

## 09 关键公式符号

1. **HLE 二元化阈值**（公式 2–4）：
   - 对每个基因，计算所有细胞对 (i,j) 表达值的中位数：HLE = med_{i,j∈{1,…,n}} (x_i + x_j)/2
   - 阈值 T_l = HLE（对第 l 列）
   - 二元化：b_{kl} = I{c_{kl} ≥ T_l}

2. **MLP 损失函数**（公式 6）：
   - L = −Σ_{i=1}^{T} p_i log q_i + λ‖ω_i‖₁
   - p_i：真实标签；q_i：预测概率；λ：L1 正则化权重；ω_i：网络权重

3. **Case-deletion 精度**（公式 8）：
   - ACC_{mn} = 1 − (1/K)‖f_n(B_m) − b_{M+n}‖₀
   - f_n(B_m)：删除第 m 个 TF 后对第 n 个靶基因的预测；b_{M+n}：第 n 个靶基因的真实二元表达；‖·‖₀：非零元素计数（即预测错误数）

4. **gESD 检验**（公式 9–10）：
   - R_i = max_i |x_i − x̄| / s（第 i 次迭代的 R 统计量）
   - λ_i = (n−i) t_p(n−i−1) / √[(n−i+1)(n−i−1 + t_p²(n−i−1))]，p = 1 − α/[2(n−i+1)]
   - 用于检测 ACC 矩阵中的显著离群值

---

## 10 实验设计与证据链

- **数据集**：
  - 小鼠大脑皮层 scRNA-seq（GSE60361，3005 细胞）
  - 人皮肤黑色素瘤 SKCM（GSE115978，7186 细胞）
  - 人头颈鳞癌 HNSCC（GSE103322，5902 细胞）
  - 小鼠多器官（GSE109774，53760 细胞，用于大规模验证）
- **指标**：聚类精度（F score、CSI、PSI、ARI、NMI）；regulon 与 ChIP-seq 重叠的敏感性/特异性
- **基线**：SCENIC（随机森林 + RcisTarget + AUCell）；Seurat（仅聚类比较）
- **预算**：未提供
- **骨干/仪器**：未提供
- **oracle 输入**：ChIP-seq 验证的 TF 靶基因（来自 ChIP-Atlas）
- **评测协议**：对每个数据集，分别用 SIGNET 和 SCENIC 生成 regulon，计算与 ChIP-seq 的重叠；对聚类结果用 5 种外部指标评估

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|--------------------|------|
| 细胞聚类（大脑） | SIGNET 聚类优于 SCENIC/Seurat | 同一数据集，5 种指标 | SIGNET 在 F score、CSI、PSI、ARI、NMI 上均最优 | SIGNET 的 regulon 活性矩阵携带更多细胞类型区分信息 | 未与其他深度学习方法（如 scVI）对比 | Results 图 2A–B |
| 肿瘤细胞聚类（SKCM/HNSCC） | SIGNET 对肿瘤细胞聚类更紧凑 | 内部指标 RMSSTD、MHG | SIGNET 优于 SCENIC 和 Seurat 各变体 | SIGNET 能更好分离肿瘤细胞 | 未评估临床意义 | Results 图 2D、F |
| ChIP-seq 交叉验证（HNSCC） | SIGNET 对 ChIP-seq 验证互作更敏感 | 对每个 regulon 计算与 ChIP-seq 重叠 | SIGNET 敏感性显著高于 SCENIC，特异性略低或相当 | SIGNET 能捕获更多真实调控对 | 特异性略低，需 motif 过滤控制 | Results 图 3C |
| 稀有细胞 regulon 识别（HNSCC 肌细胞） | SIGNET 能识别稀有细胞特异 regulon | 19 个肌细胞 vs 其余细胞 | SIGNET 识别 MYF5/MYF6/MYOG 三个肌源 regulon；SCENIC 将肌细胞与成纤维细胞混为一类 | SIGNET 对稀有细胞更敏感 | 未做功能实验验证 | Results 图 5B |
| 下采样稳健性（大脑小胶质细胞） | SIGNET 对稀有细胞下采样更稳健 | 小胶质细胞降至 20 个 | SIGNET 仍识别 Irf1/Irf5/Irf8/Maff regulon；SCENIC 性能显著下降 | SIGNET 的 bagging 策略增强稀有细胞信号 | 未测试更低细胞数 | Results 图 5C–D |
| 生存分析（SKCM 巨噬细胞 regulon） | SIGNET regulon 与患者生存相关 | TCGA SKCM 队列，CD163 归一化 | 多个巨噬细胞 regulon 与生存显著相关 | SIGNET regulon 具有临床相关性 | 未做多变量 Cox 回归 | Results 图 4B |

---

## 11 结论正确解读

- **任务范围**：本文仅针对**转录水平**的 TF–靶基因调控关系推断，不涉及 TF 蛋白–DNA 直接结合的物理机制、不涉及染色质可及性、不涉及翻译后修饰。
- **oracle/真值输入**：ChIP-seq 数据作为验证真值，但 ChIP-seq 本身有细胞类型特异性和批次效应，且仅覆盖部分 TF。
- **端到端状态**：SIGNET 是端到端可运行的流程（输入表达矩阵 → 输出 regulon + 聚类），但每个模块的独立贡献未做消融实验。
- **算力成本**：未报告训练时间或硬件需求；MLP 为 3 层全连接，bagging 增加训练次数，但整体规模较小。
- **历史数据依赖**：依赖 TF 列表的完整性（来自 pySCENIC 资源），若 TF 列表不全，则漏检相应调控。
- **模型依赖**：MLP 的预测精度对超参数（层宽、正则化强度、bagging 比例）敏感，但未做敏感性分析。
- **最难情形**：稀有细胞中低表达 TF 的调控关系、非直接结合（间接调控）的区分、motif 数据库覆盖不足的 TF。
- **群体/领域边界**：方法验证限于小鼠大脑、人黑色素瘤、头颈鳞癌；未在植物、微生物或非模式动物中验证。
- **不确定性**：未报告置信区间或重复实验的变异性；gESD 检验的 α=0.05 是唯一统计阈值。

**有边界的复述**：SIGNET 在三个 scRNA-seq 数据集上，相比 SCENIC，对 ChIP-seq 验证的 TF–靶基因互作具有更高的敏感性，且对稀有细胞（如 19 个肌细胞、20 个小胶质细胞）的 regulon 识别更稳健；但其特异性略低，且未与其他深度学习方法对比，也未在更多样化的物种或细胞类型中验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|----------------------|------|
| 特异性略低 | SIGNET 预测的靶基因中，ChIP-seq 验证比例低于 SCENIC | 调整 motif 富集阈值；整合更多 ChIP-seq 数据 | Results 图 3C 讨论 |
| 未整合多组学数据 | 仅使用 scRNA-seq，未利用 ChIP-seq/ATAC-seq 作为输入 | 未来工作整合多组学信息（提及 DeepSEM、LISA、MAESTRO） | Discussion 末段 |
| 未利用时间序列信息 | 无法预测基因表达的动态变化 | 结合 RNA velocity 等方法 | Discussion 末段 |
| 参数选择依赖经验 | motif 富集阈值需根据数据集调整 | 未提供自适应阈值方案 | Discussion: "adjusting the threshold of motif enrichment score" |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| case-deletion 的因果解释有限 | 删除 TF 表达后预测精度下降可能反映的是共表达关系而非直接调控；TF 之间的共调控（redundancy）可能导致删除单个 TF 影响不大 | 若将预测扰动解释为因果，可能高估调控关系 | 用已知调控网络（如 E. coli RegulonDB）做基准测试，比较 case-deletion 与随机删除的 AUC 差异 | Methods 公式 (7)–(8) |
| 二元化丢失定量信息 | HLE 阈值将表达量二值化，可能丢失剂量依赖的调控关系（如 TF 浓度梯度） | TF 结合具有剂量效应，二元化可能漏检弱调控 | 对比连续值 MLP 与二元 MLP 在模拟数据上的召回率 | Methods 公式 (2)–(4) |
| 未与其他深度学习方法对比 | 仅与 SCENIC 和 Seurat 对比，未与 GENIE3、GRNBoost2、DeepSEM 等比较 | 无法判断 MLP 架构是否优于现有非线性方法 | 在相同数据集上运行多种方法，统一用 ChIP-seq 验证 | Results 全文 |
| 稀有细胞验证样本量极小 | 19 个肌细胞、20 个小胶质细胞的 regulon 识别可能受随机性影响 | 稀有细胞分析是本文核心卖点，但统计功效存疑 | 用 bootstrap 重采样评估 regulon 识别的稳定性 | Results 图 5B–D |
| 生存分析未做多变量校正 | 仅用 CD163 归一化，未校正年龄、性别、分期等混杂因素 | 可能高估 regulon 与生存的关联 | 重新分析 TCGA 数据，加入临床协变量做多变量 Cox 回归 | Results 图 4B |
| motif 富集依赖数据库覆盖 | RcisTarget 的 motif 数据库可能不完整，导致假阴性 | 对非模式物种或新发现 TF 不适用 | 用 DNase-seq/ATAC-seq 足迹分析交叉验证 | Methods "RcisTarget" |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **预测扰动作为调控边界的代理**：SIGNET 的核心可迁移思想是——用「删除某特征后预测精度的变化」来量化该特征对目标的调控贡献。在 TF–DNA 结合机制研究中，可类比为：在深度学习模型中，将某个 TF 的输入通道置零（或掩蔽），观察对靶基因表达预测的影响，以此识别候选调控对。这比 SHAP 值或注意力权重更直接地对应「该 TF 缺失后系统行为变化」的干预语义。

2. **两层验证架构（计算预测 + 序列验证）**：SIGNET 先用 MLP 预测调控对，再用 RcisTarget 的 motif 富集验证直接结合。这一「先预测后验证」的流程可迁移到 TF–DNA 结合机制研究：先用深度学习预测 TF 的靶基因，再用 ChIP-seq 或 motif 扫描验证结合位点，最后用结构预测（如 AlphaFold3）或 MD 模拟验证结合模式。

3. **类别不平衡处理对稀有细胞研究至关重要**：bagging 重采样（正负比 ≤1:5）显著提升稀有细胞 regulon 检出率。在 TF–DNA 结合研究中，稀有细胞类型（如循环肿瘤细胞、组织干细胞）的调控网络往往被淹没，可借鉴此策略在训练数据中过采样稀有细胞。

4. **二元化作为噪声鲁棒性手段**：HLE 二元化将表达量转为 0/1，降低 dropout 噪声影响。在 TF–DNA 结合预测中，若输入特征（如 ChIP-seq 峰强度）噪声大，可考虑类似的鲁棒化预处理。

5. **非线性模型对非单调调控的敏感性**：MLP 能捕捉非线性/非单调调控，这对 TF 浓度依赖的双相调控（低浓度激活、高浓度抑制）有参考价值。在物理模拟中，可结合此类预测结果设计 MD 模拟的浓度梯度条件。

---

## 15 与已有知识连接

- **SCENIC**（Aibar et al., 2017, Nature Methods）：SIGNET 直接对标 SCENIC，将随机森林替换为 MLP + case-deletion，保留 RcisTarget 和 AUCell 模块。可迁移点：RcisTarget 的 motif 富集方法可直接用于 TF–DNA 结合验证。
- **GENIE3 / GRNBoost2**（Huynh-Thu et al., 2010; Moerman et al., 2019）：基于树模型的 GRN 推断方法，SIGNET 的 MLP 可视为其非线性扩展。
- **DeepSEM**（Schubert et al., 2020）：结合深度学习和结构方程模型的 GRN 推断，SIGNET 未与其对比，但两者可互补。
- **ENCODE ChIP-seq 数据**：本文用 ChIP-seq 作为验证真值，ENCODE 的 TF 结合数据可作为本课题的基准测试集。
- **AlphaFold3 / RoseTTAFold**：本文未涉及结构预测，但 motif 富集验证的「直接结合」可进一步用结构预测验证结合模式。
- **分子动力学（MD）模拟**：本文的 regulon 预测可作为 MD 模拟的候选体系筛选工具——预测高置信 TF–靶基因对后，用 MD 模拟验证结合自由能。
- **用户已有知识**：若用户熟悉单细胞分析流程（Seurat、Scanpy），SIGNET 的输入输出格式与这些工具兼容，可直接嵌入现有流程。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

1. **候选名称**：TF–DNA 结合预测的「预测扰动 + 结构验证」级联框架
   - **来源局限/观察**：SIGNET 的 case-deletion 仅基于表达数据，缺乏对结合位点序列特征的直接利用；且 motif 富集验证是统计性的，不提供结合模式的结构信息。
   - **核心假设**：将 SIGNET 的预测扰动重要性作为候选 TF–靶基因对筛选器，再用 AlphaFold3 或 MD 模拟验证结合模式，可显著降低假阳性率。
   - **初步方法**：在 SIGNET 输出的 regulon 基础上，提取靶基因启动子序列，用 TF 的 DNA 结合域结构做 docking 或 MD 模拟，计算结合自由能；以能量阈值过滤 regulon。
   - **验证方式**：在 ENCODE ChIP-seq 数据上比较级联框架与单独 SIGNET 的精确率/召回率。
   - **创新状态**：unverified

2. **候选名称**：稀有细胞 TF 调控网络的过采样增强策略
   - **来源局限/观察**：SIGNET 的 bagging 策略对稀有细胞有效，但仅调整了正负样本比例，未利用细胞类型先验。
   - **核心假设**：在训练 MLP 时，对稀有细胞类型进行显式过采样（而非仅平衡正负样本），可进一步提升稀有细胞 regulon 的检出率。
   - **初步方法**：在预处理阶段识别稀有细胞簇（如通过聚类），在 bagging 中对这些细胞的样本进行加权过采样；对比 SIGNET 原始 bagging。
   - **验证方式**：在 GSE109774 多器官数据上，对已知稀有细胞类型（如干细胞）进行 regulon 召回率评估。
   - **创新状态**：unverified

3. **候选名称**：基于 MLP 预测扰动的 TF 结合位点序列特征重要性分析
   - **来源局限/观察**：SIGNET 的 MLP 输入是 TF 表达，未利用 DNA 序列特征；但 TF–DNA 结合机制研究中，序列 motif 是关键。
   - **核心假设**：将 MLP 的输入扩展为「TF 表达 + 靶基因启动子序列编码」，通过 case-deletion 同时评估 TF 表达和序列特征的重要性，可识别对结合至关重要的序列基序。
   - **初步方法**：用 k-mer 或 DNABERT 编码启动子序列，与 TF 表达拼接作为 MLP 输入；对每个序列特征做 case-deletion，生成序列重要性图谱。
   - **验证方式**：与 ChIP-seq 峰内的已知 motif 比对，评估重要性图谱的富集精度。
   - **创新状态**：unverified

4. **候选名称**：TF–DNA 结合动力学的深度学习代理模型
   - **来源局限/观察**：SIGNET 是静态的（基于表达快照），无法捕捉 TF–DNA 结合的动态过程；MD 模拟虽能提供动力学，但计算成本高。
   - **核心假设**：用 SIGNET 的 regulon 预测结果作为 MD 模拟的初始候选，训练一个图神经网络（GNN）作为 MD 的代理模型，预测结合自由能变化。
   - **初步方法**：对 SIGNET 输出的高置信 TF–靶基因对，用 MD 模拟生成结合轨迹，提取结合自由能作为标签；训练 GNN 预测自由能，替代全 MD 模拟。
   - **验证方式**：在留出集上比较 GNN 预测与 MD 模拟的自由能误差。
   - **创新状态**：unverified

5. **候选名称**：跨物种 TF–DNA 结合调控网络的迁移学习
   - **来源局限/观察**：SIGNET 的模型在单一数据集上训练，未利用跨物种的保守调控信息。
   - **核心假设**：在模式生物（如小鼠）上预训练的 MLP，通过迁移学习可提升非模式生物（如斑马鱼）的 regulon 推断精度。
   - **初步方法**：用小鼠大脑数据预训练 MLP，冻结前两层，在斑马鱼数据上微调最后一层；对比从头训练的 MLP。
   - **验证方式**：用 ChIP-seq 数据评估迁移学习模型的 regulon 精度。
   - **创新状态**：unverified