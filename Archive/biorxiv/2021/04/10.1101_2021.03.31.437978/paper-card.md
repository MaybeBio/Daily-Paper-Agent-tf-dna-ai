## 01 基本信息

- **标题**：Chromatin interaction aware gene regulatory modeling with graph attention networks
- **作者与单位**：Karbalayghareh A; Sahin M; Leslie CS（计算与系统生物学项目，Sloan Kettering Institute，Memorial Sloan Kettering Cancer Center）
- **期刊/预印本平台**：bioRxiv
- **年份**：2021-04-02
- **论文类型**：预印本（方法学 + 应用验证）
- **领域**：调控基因组学；深度学习；基因表达预测；染色质三维互作
- **关键词**：GraphReg；图注意力网络（GAT）；Hi-C/HiChIP/Micro-C；增强子-启动子互作；基因表达预测；TF 直接靶标预测
- **DOI/arXiv 号**：10.1101/2021.03.31.437978
- **代码**：https://github.com/karbalayghareh/GraphReg
- **数据**：ENCODE（GM12878、K562、hESC、mESC 的 CAGE、DNase、H3K4me3、H3K27ac）；GEO（HiChIP：GSE101498、GSE113339；Hi-C：GSE63525）；4DN portal（Micro-C：4DNFI2TK7L2F）；CRISPRi-FlowFISH（Fulco et al., 2019）；TAP-seq（Schraivogel et al., 2020）；ENCODE CRISPRi TF KO RNA-seq（51 个 TF）
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文是「TF–DNA 结合机制 × 深度学习」方向的代表性工作，核心贡献在于将 3D 染色质互作图（Hi-C/HiChIP/Micro-C）作为图结构引入基因表达预测模型，通过图注意力网络（GAT）显式建模增强子-启动子（E-P）与增强子-增强子（E-E）互作，并利用特征归因（saliency、DeepSHAP）与 in silico motif ablation 识别功能性增强子与 TF 直接靶标。对 TF–DNA 结合机制研究而言，其可迁移价值在于：① 将 TF 结合位点（motif）的远端调控效应通过 3D 互作图纳入预测；② 提供了一种从序列直接预测 TF 敲低后靶基因表达变化的计算框架。

## 02 一句话总结

本文提出 GraphReg——一种结合 1D 表观基因组数据（或 DNA 序列）与 3D 染色质互作图（Hi-C/HiChIP/Micro-C）的图注意力网络模型，通过将远端增强子信息沿互作图传播到启动子节点，在 4 种细胞系中比 CNN 基线更准确地预测 CAGE 基因表达，并能通过特征归因与 motif ablation 识别功能性增强子和 TF 直接靶标。

## 03 研究问题

- **具体问题**：如何利用 3D 染色质互作数据（Hi-C/HiChIP/Micro-C）将远端增强子对目标基因的调控效应纳入深度学习模型，从而更准确地预测基因表达，并进一步识别功能性增强子与 TF 直接靶标？
- **为什么重要**：增强子可位于目标基因 1–2 Mb 之外，传统 CNN 模型（如 Basenji）的感受野有限（通常 ≤100 kb），无法覆盖远端调控元件；而线性模型（如 ABC）虽使用 Hi-C 互作，但缺乏序列信息与非线性建模能力。准确建模远端调控对解读非编码变异功能至关重要。
- **现有方法不足**：
  - CNN 模型（Basenji、Xpresso 等）感受野有限，无法整合 >100 kb 的远端增强子；
  - 线性回归模型（如 ABC）依赖人工定义的活性/接触度乘积，缺乏序列特征学习能力；
  - 已有 GNN 方法（如 GC-MERGE）使用 GCN，无法学习不同 E-P 互作的重要性权重，且未进行功能增强子/TF 靶标验证。
- **精确研究问题（Can 问题）**：Can a graph attention network that propagates local CNN features over 3D chromatin interaction graphs (up to 2 Mb) predict gene expression more accurately than dilated CNNs, and can its feature attribution identify functional enhancers and direct TF targets validated by CRISPRi experiments?

## 04 背景与发展脉络

（注：以下脉络基于本文引言与讨论，结合公开文献常识，标注「经外部核验」部分）

1. **阶段一：基于 1D 表观基因组/序列的基因表达预测**
   - 代表方法：Basenji（Kelley et al., 2018）、Xpresso（Agarwal & Shendure, 2020）、ExPecto（Zhou et al., 2018）、BPNet（Avsec et al., 2021b）
   - 优点：可从序列直接预测表达/染色质状态，端到端可微
   - 局限：感受野有限（≤100 kb），无法覆盖远端增强子（经外部核验：Basenji 默认窗口约 131 kb）
   
2. **阶段二：引入 3D 互作数据的线性/统计模型**
   - 代表方法：ABC（Activity-by-Contact，Fulco et al., 2019）
   - 优点：显式使用 Hi-C 接触频率，可识别远端增强子
   - 局限：线性乘积形式，缺乏序列特征学习；依赖人工阈值与归一化

3. **阶段三：图神经网络用于调控建模**
   - 代表方法：GC-MERGE（Bigness et al., 2021）——使用 GCN 结合 Hi-C 与组蛋白修饰预测表达
   - 优点：首次将图结构引入调控预测
   - 局限：GCN 无法学习边权重（所有 E-P 互作等权）；未进行功能验证（增强子/TF 靶标）
   - 本文主张位置：GraphReg 使用 GAT 替代 GCN，可学习不同互作的重要性；同时提供 Epi-（表观输入）与 Seq-（序列输入）两个版本，并通过 CRISPRi-FlowFISH/TAP-seq 与 TF KO 实验验证可解释性。

4. **阶段四（本文之后，经外部核验）**：后续工作如 Enformer（Avsec et al., 2021a）通过 transformer 将感受野扩至 100 kb，但仍未达 2 Mb；GraphReg 的图传播策略为超长程调控建模提供了替代路径。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| CNN 感受野不足 | Basenji 等模型无法利用 >100 kb 的远端增强子信息 | 卷积核堆叠的局部性；内存限制 | Introduction 第 1 段；Discussion 对 Enformer 的讨论 |
| 线性模型缺乏序列学习 | ABC 分数 = 活性 × 接触度，无法捕捉 TF 结合基序的序列特异性 | 人工定义的特征组合，非线性表达能力有限 | Introduction 第 2 段；Results 图 3 中 ABC 对比 |
| GCN 无法区分互作重要性 | GC-MERGE 对所有 E-P 边等权聚合 | GCN 的固定邻域聚合方式，无注意力机制 | Methods「Graph attention networks」节；Discussion 对 GCN 的讨论 |
| 3D 互作数据噪声大 | 不同 FDR 阈值下互作图差异大，影响预测稳定性 | Hi-C/HiChIP 文库复杂度、测序深度差异 | Results 图 2 与 Supplemental Figs. S2-S6 中不同 FDR 对比 |
| 模型可解释性不足 | 仅预测表达无法回答「哪个增强子调控哪个基因」 | 缺乏特征归因与扰动验证框架 | Results 图 3-4；Discussion 对可解释性的强调 |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| CNN 感受野有限 | 无法整合 >100 kb 的远端增强子 | 卷积核堆叠的局部性；内存限制 | Introduction 第 1 段；Discussion 对 Enformer 的讨论 |
| 线性模型缺乏序列学习 | ABC 分数 = 活性 × 接触度，无法捕捉 TF 结合基序的序列特异性 | 人工定义的特征组合，非线性表达能力有限 | Introduction 第 2 段；Results 图 3 中 ABC 对比 |
| GCN 无法区分互作重要性 | GC-MERGE 对所有 E-P 边等权聚合 | GCN 的固定邻域聚合方式，无注意力机制 | Methods「Graph attention networks」节；Discussion 对 GCN 的讨论 |
| 3D 互作数据噪声大 | 不同 FDR 阈值下互作图差异大，影响预测稳定性 | Hi-C/HiChIP 文库复杂度、测序深度差异 | Results 图 2 与 Supplemental Figs. S2-S6 中不同 FDR 对比 |
| 模型可解释性不足 | 仅预测表达无法回答「哪个增强子调控哪个基因」 | 缺乏特征归因与扰动验证框架 | Results 图 3-4；Discussion 对可解释性的强调 |

## 06 核心思想

1. **表面方法**：构建一个两阶段深度学习模型——先用 CNN 从 1D 输入（表观基因组信号或 DNA 序列）学习局部特征，再将特征作为节点表示输入图注意力网络（GAT），在 3D 互作图（Hi-C/HiChIP/Micro-C 显著互作）上传播信息，最终预测每个 5 kb bin 的 CAGE 表达值。提供 Epi-GraphReg（表观输入）与 Seq-GraphReg（序列输入）两个版本。

2. **核心洞察**：
   - **生物学先验作为归纳偏置**：3D 互作图提供了「哪些远端区域可能调控该启动子」的先验结构，GAT 在此图上传播信息，使模型无需学习任意长程序列依赖，而是聚焦于实验支持的候选互作。
   - **注意力即生物学重要性**：GAT 学习的边权重可解释为不同增强子对目标基因的调控贡献，这比 GCN 的等权聚合更符合生物学直觉（不同增强子对基因表达的贡献不同）。
   - **序列与 3D 的互补**：Seq-GraphReg 从序列预测表观状态（多任务学习），再结合 3D 互作预测表达，使模型能捕捉 TF 结合基序的远端效应。

3. **可能的普适教训 [Analysis]**：
   - 对于 TF–DNA 结合机制研究，将「实验测得的物理互作（Hi-C/ChIP）」作为图结构先验，比纯序列模型更高效——因为序列模型需要从零学习「哪些远端区域会环化到启动子」，而 3D 数据直接提供了这一信息。
   - 特征归因（saliency/DeepSHAP）与 in silico 扰动（motif ablation）的结合，是从「预测模型」走向「机制发现」的关键路径。

## 07 方法总览

- **输入**：
  - Epi-GraphReg：1D 表观基因组信号（DNase、H3K4me3、H3K27ac），100 bp bin，6 Mb 窗口（N=60000 个 bin）
  - Seq-GraphReg：DNA 序列（one-hot 编码），6 Mb 窗口
  - 两者共享：3D 互作图（Hi-C/HiChIP/Micro-C 显著互作，5 kb bin 分辨率，最多 2 Mb 距离）
- **输出**：每个 5 kb bin 的 CAGE 表达预测值（Poisson 分布均值）
- **模块**：
  1. CNN 编码器（Epi 或 Seq）：学习局部特征，输出 5 kb bin 的节点特征 h_i ∈ ℝ^128
  2. GAT 层（2-3 层，4 头注意力）：在 3D 互作图上传播节点特征
  3. 全连接输出层：预测 CAGE 值
  4. （Seq-GraphReg 附加）表观基因组预测头：从序列预测 DNase/H3K4me3/H3K27ac（多任务学习）
- **训练**：
  - 损失：CAGE 的 Poisson 负对数似然 + 表观预测的损失（Seq 版本）+ 可选的 FFT 损失（用于平滑 saliency）
  - 优化：Adam；学习率调度
  - 数据划分：留出 2 条染色体测试、2 条验证、其余训练（10 折交叉验证）
  - 细胞系：GM12878、K562、hESC、mESC
- **反馈回路**：无显式主动学习/迭代实验闭环；但特征归因结果可反馈指导实验设计（如选择增强子进行 CRISPRi 验证）。
- **假设**：
  - 3D 互作图（显著互作）足以捕捉功能性 E-P 调控关系；
  - CAGE 信号可近似为 Poisson 分布；
  - 5 kb bin 分辨率足以代表增强子/启动子调控单元。

**文字流程**：
1. 将 6 Mb 基因组窗口的 1D 输入（表观信号或序列）送入 CNN 编码器，得到 5 kb bin 的局部特征表示。
2. 从 3D 数据（Hi-C/HiChIP/Micro-C）提取显著互作，构建以 5 kb bin 为节点的图。
3. 将 CNN 特征作为节点初始特征，经多层 GAT 传播（注意力权重学习 E-P 与 E-E 互作的重要性）。
4. 对每个节点（bin）用全连接层输出 CAGE 预测值，训练时最小化 Poisson NLL。
5. 推理时，对目标基因 TSS 所在 bin 的预测值即为该基因的表达预测；特征归因（saliency/DeepSHAP）用于识别贡献最大的远端增强子。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN 编码器（Epi/Seq） | 从 1D 输入学习局部序列/表观特征 | 将原始输入转换为有意义的节点特征；CNN 擅长捕捉局部 motif 模式 | 输入：100 bp bin 的 1D 信号或 one-hot 序列；输出：5 kb bin 特征 h_i ∈ ℝ^128 | Results 图 2 中 Epi/Seq 模型均优于随机；Methods「CNN layers」节 | 预期影响：模型退化为仅依赖图结构而无节点特征的随机预测（[Analysis] 预期，未做消融） |
| GAT 层 | 在 3D 互作图上传播信息，学习 E-P/E-E 互作权重 | 使远端增强子信息能影响启动子节点；注意力机制区分不同增强子的贡献 | 输入：节点特征 + 图邻接矩阵；输出：更新后的节点特征 | Results 图 2 中 GraphReg > CNN；Methods「Graph attention networks」节 | 实测影响：替换为 GCN 后性能下降（Discussion 中对比 GC-MERGE）；移除后模型退化为纯 CNN，无法利用远端信息 |
| 多任务表观预测头（Seq 版本） | 从序列预测 DNase/H3K4me3/H3K27ac | 引导 CNN 学习有生物学意义的 motif 表示 | 输入：CNN bottleneck 特征；输出：3 个表观信号的预测 | Methods「Model architecture」节；Supplemental Fig. S1 | 预期影响：移除后 Seq-GraphReg 的 motif 表示质量下降，CAGE 预测可能降低（[Analysis] 预期，未单独消融） |
| FFT 损失 | 惩罚 saliency 的高频成分，使归因图更平滑 | 提高特征归因的可解释性，减少噪声 | 输入：saliency 图的傅里叶分量；输出：标量损失 | Methods「Dilated CNN layers and FFT loss」节；Fig. 4E | 预期影响：移除后 saliency 图噪声增大，motif 识别精度下降（[Analysis] 预期，文中仅用于 Seq-GraphReg 单独训练） |
| 输出层（Poisson 回归） | 预测每个 bin 的 CAGE 计数 | CAGE 为计数数据，Poisson 分布合适 | 输入：GAT 输出特征；输出：CAGE 预测值 λ_i | Methods「Poisson regression」节 | 预期影响：替换为 MSE 损失可能对低表达基因预测更差（[Analysis] 预期，未做对比） |

## 09 关键公式符号

1. **GAT 注意力系数**（Methods「Graph attention networks」节）：
   - e_ij^(t) = σ( a^(t)ᵀ [W_self^(t) h_i^(t) ⊕ W_neigh^(t) h_j^(t)] )
   - 其中：e_ij^(t) 为层 t 中节点 j 对节点 i 的注意力分数；σ 为 sigmoid 函数；a^(t) 为注意力权重向量；W_self^(t) 和 W_neigh^(t) 分别为自节点（启动子）和邻居节点（增强子）的线性变换矩阵；⊕ 表示拼接；h_i^(t) 为节点 i 在层 t 的特征。
   - 用途：计算每个邻居对目标节点的贡献权重。

2. **归一化注意力系数**（Methods 同节）：
   - η_ij^(t) = e_ij^(t) / ( e_ii^(t) + Σ_{k∈N(i)} e_ik^(t) )
   - 其中：N(i) 为节点 i 的邻居集合（不含自身）；e_ii^(t) 为自环注意力分数。
   - 用途：确保所有注意力系数之和为 1，且显式建模启动子自身特征与增强子特征的相对贡献。

3. **节点特征更新**（Methods 同节）：
   - h_i^(t+1) = f( η_ii^(t) W_self^(t) h_i^(t) + Σ_{j∈N(i)} η_ij^(t) W_neigh^(t) h_j^(t) )
   - 其中：f 为 ELU 非线性激活函数。
   - 用途：将增强子特征按注意力权重聚合到启动子节点。

4. **Poisson 负对数似然损失**（Methods「Poisson regression and loss function」节）：
   - L_E = -Σ_i log( λ_i^(y_i) e^(-λ_i) / y_i! ) = Σ_i [ λ_i - y_i log(λ_i) + log(Γ(y_i+1)) ]
   - 其中：y_i 为观测 CAGE 计数，λ_i = f_θ(X, G)_i 为模型预测的 Poisson 均值。
   - 用途：训练 Epi-GraphReg 的损失函数。

5. **Seq-GraphReg 总损失**（Methods 同节）：
   - L_total = λ L_CAGE + (1-λ) Σ_e L_e + γ L_p(g(H⋆, X))
   - 其中：L_CAGE 为 CAGE 的 Poisson NLL，L_e 为表观预测损失，L_p 为 FFT 归因先验损失，λ 为权衡超参数，γ 为归因损失权重。
   - 用途：多任务学习 + 归因平滑。

6. **FFT 归因先验**（Methods「Dilated CNN layers and FFT loss」节）：
   - L_p(g) = Σ_i w_i |a_i|²，其中 a 为 saliency 图的傅里叶分量幅度，w_i = 1（i ≤ T）或 w_i = s（i > T）
   - 用途：惩罚高频噪声，使归因图聚焦于低频、连续的调控区域。

## 10 实验设计与证据链

**数据集与规模**：
- 4 个细胞系：GM12878（B 淋巴细胞）、K562（慢性粒细胞白血病）、hESC（H1 胚胎干细胞）、mESC（小鼠胚胎干细胞）
- 输入数据：DNase-seq、H3K4me3 ChIP-seq、H3K27ac ChIP-seq（100 bp bin）；DNA 序列（one-hot）
- 3D 数据：H3K27ac HiChIP（K562、GM12878、mESC）、Hi-C（GM12878、K562）、Micro-C（hESC）
- 表达数据：CAGE-seq（5 kb bin）
- 验证数据：CRISPRi-FlowFISH（K562，19 个基因，2574 个 E-P 对）；TAP-seq（K562 chr8/11，35 个基因，4423 个 E-P 对）；CRISPRi TF KO RNA-seq（K562，51 个 TF）

**指标**：
- 基因表达预测：Pearson 相关系数（R）、负对数似然（NLL）
- 增强子识别：AUPR（area under precision-recall curve）
- TF 靶标预测：预测靶基因与真实 CRISPRi 下调基因的重叠（通过排序与富集评估）

**评测协议**：
- 交叉验证：留出 2 条染色体测试、2 条验证、其余训练，10 次运行
- 对比基线：Epi-CNN、Seq-CNN（无图结构的 CNN）、ABC 模型
- 消融：不同 3D 数据来源（HiChIP vs Hi-C vs Micro-C）、不同 FDR 阈值

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 表达预测（Epi） | 3D 互作信息提升表达预测 | Epi-GraphReg vs Epi-CNN，4 细胞系 | GraphReg 在多数细胞系中 R 更高、NLL 更低（如 GM12878 R=0.654 vs 0.63） | 3D 互作图提供额外预测信息 | 未报告所有细胞系的完整统计显著性 | Results 图 2A；Supplemental Figs. S2-S6 |
| 表达预测（Seq） | 序列+3D 联合建模优于纯序列 | Seq-GraphReg vs Seq-CNN，K562/GM12878 | Seq-GraphReg R=0.494 vs Seq-CNN（显著更优） | 3D 互作对序列模型同样有益 | 未与 Enformer 等更大模型对比 | Results 图 2B |
| 增强子识别（FlowFISH） | 特征归因识别功能性增强子 | GraphReg saliency/DeepSHAP vs ABC vs CNN 归因 | GraphReg AUPR 最高 0.4236（Epi-saliency），优于 ABC（0.364）和 CNN（0.366） | 图注意力传播使归因更准确 | 仅 19 个基因，可能偏向高表达基因 | Results 图 3A-B |
| 远端增强子识别（MYC 案例） | 模型捕获 >1 Mb 增强子 | 仅考虑 >10 kb 的远端 E-P 对 | GraphReg AUPR=0.576 vs CNN=0.079 vs ABC=0.357 | 3D 图传播对远端增强子识别至关重要 | 单基因案例，需更多验证 | Results 图 3E；Supplemental Fig. S22A |
| TF 靶标预测（motif ablation） | 序列模型编码 TF 调控关系 | Seq-GraphReg vs Seq-CNN，51 个 TF KO | Seq-GraphReg 预测的靶基因与真实下调基因重叠显著更高 | 3D 互作使 TF 远端靶标可被识别 | 仅预测下调基因，未评估上调 | Results 图 4A-D |
| 跨细胞系泛化 | 模型可迁移至新细胞类型 | 训练 K562 测试 GM12878（反之亦然） | Epi-GraphReg 显著优于 Epi-CNN | 3D 互作先验具有跨细胞系泛化性 | 仅两个细胞系互测 | Results 图 2D；Supplemental Figs. S11-S13 |

## 11 结论正确解读

- **任务范围**：本文解决的是「给定 1D 表观信号或序列 + 3D 互作图，预测 5 kb bin 的 CAGE 表达」以及「从模型归因中识别功能性增强子和 TF 靶标」。它不解决：变异效应预测（如 eQTL）、增强子-启动子因果方向推断、动态调控建模。
- **oracle/真值输入**：3D 互作图（HiChIP/Hi-C/Micro-C）是实验测量数据，作为图结构输入；CAGE 是表达真值标签。模型并未从序列预测 3D 结构，而是直接使用实验测得的互作。
- **端到端状态**：Epi-GraphReg 是端到端可微的（输入→CNN→GAT→输出）。Seq-GraphReg 有两种模式：端到端（序列→CNN→表观预测 + GAT→CAGE）和分离训练（先训练序列→表观，再冻结 CNN 训练 GAT→CAGE）。分离训练性能更优，但失去序列级反向传播归因能力。
- **算力成本**：文中未报告具体训练时间/GPU 型号。6 Mb 窗口 + 1200 节点图 + 4 头注意力，训练成本中等（[Analysis] 估计：单细胞系在单张 V100 上约数小时至一天）。
- **历史数据依赖**：模型依赖 ENCODE 的成熟实验数据（CAGE、ChIP-seq、Hi-C 等），对数据质量敏感；3D 互作图的构建方式（显著互作阈值）影响结果。
- **模型依赖**：GAT 层数、注意力头数、CNN 架构均影响性能；文中未做全面超参数搜索。
- **最难情形**：低表达基因（CAGE 信号弱）、无显著 3D 互作的基因（图信息稀疏）、细胞类型特异性强的调控。
- **群体/领域边界**：模型在 4 个细胞系上验证，主要覆盖 ENCODE 常见细胞类型；对疾病相关细胞类型或非模式生物的适用性未验证。
- **不确定性**：特征归因（saliency/DeepSHAP）识别增强子的 AUPR 最高约 0.42，意味着仍有大量假阳性；TF 靶标预测依赖 motif 数据库质量。

**有边界的复述**：GraphReg 在 4 个 ENCODE 细胞系中，利用 3D 染色质互作图通过 GAT 传播 CNN 特征，比无图结构的 CNN 更准确地预测 CAGE 表达；其归因分析在 K562 的 CRISPRi 验证数据上优于 ABC 和 CNN，但绝对精度仍有限（AUPR 0.42-0.58），且未在更大规模或更多样化的细胞类型中验证。

## 12 作者自认局限

在提供的材料中，作者明确承认的局限如下：

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 分离训练失去序列级归因 | 分离训练的 Seq-GraphReg 无法通过反向传播获得碱基级 saliency，只能使用较慢的 ISM | 未来可探索在分离训练后微调端到端模型 | Methods「End-to-end versus separate training」节 |
| 3D 数据分辨率限制 | 使用 5 kb bin 的互作数据，无法区分单个增强子内部的精细调控元件 | 使用更高分辨率的 HiChIP/Micro-C 数据 | Discussion（隐含，未单列） |
| 细胞类型覆盖有限 | 仅在 4 个细胞系验证，未覆盖更多原代细胞或疾病状态 | 扩展到更多细胞类型和疾病相关样本 | Discussion（隐含） |
| 归因精度有限 | AUPR 最高 0.42-0.58，仍有大量假阳性增强子预测 | 结合更精细的 3D 数据与更多验证实验 | Results 图 3 讨论 |

**作者提及的相关约束**（非正式局限）：
- 3D 互作图的构建依赖 Hi-C 数据处理流程（HiC-DC+），不同流程可能影响结果；
- Seq-GraphReg 是细胞类型特异的，无法直接跨细胞类型迁移（与 Epi-GraphReg 不同）；
- FFT 损失仅用于单独训练的 Seq-GraphReg，端到端模型未使用。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 3D 互作图的构建依赖显著互作阈值 | 不同 FDR 阈值（0.1 vs 0.01 vs 0.001）下互作图差异大，可能引入选择偏差 | 若结果对阈值敏感，则模型性能提升可能来自特定阈值下的偶然优势 | 系统扫描 FDR 阈值，报告性能-阈值曲线 | Results 图 2 与 Supplemental Figs. S2-S6 中不同 FDR 对比 |
| 与 ABC 的对比可能不公平 | ABC 是线性模型且未使用序列信息，GraphReg 使用 CNN+序列，对比基线较弱 | 若仅与 ABC 对比，无法说明 GAT 优于其他图神经网络或 transformer | 增加与 GC-MERGE、Enformer、GCN 的公平对比 | Discussion 中仅提及 GC-MERGE 未做直接对比 |
| 增强子识别验证仅限 K562 且基因数少 | FlowScript 19 个基因、TAP-seq 35 个基因，可能偏向高表达或已知调控基因 | 小规模验证可能高估模型泛化能力 | 在更多细胞系和全基因组范围验证 | Results 图 3A-D |
| TF 靶标预测仅评估下调基因 | 未评估上调基因或间接靶标，可能高估模型对直接靶标的识别能力 | TF 调控包括激活和抑制，仅看下调会遗漏一半生物学信号 | 扩展分析到上调和双向变化基因 | Results 图 4A-D |
| 未报告不确定性量化 | 预测值无置信区间，归因分数无显著性检验 | 实际应用中需知道哪些增强子预测是可靠的 | 增加模型集成或贝叶斯方法量化不确定性 | 全文未提及 |
| 分离训练与端到端性能差异未充分解释 | 分离训练更优可能因为端到端优化困难（梯度消失/爆炸），而非方法本身优势 | 若端到端可改进，可同时获得性能与归因能力 | 尝试更好的优化策略（如课程学习、梯度裁剪） | Methods「End-to-end versus separate training」节 |
| 未与基于 transformer 的长程模型对比 | Enformer 等模型可处理 100 kb 窗口，虽未达 2 Mb，但可能已捕获大部分调控信息 | 若 transformer 在 100 kb 内已足够，3D 图传播的增量价值需重新评估 | 在相同数据上对比 GraphReg 与 Enformer | Discussion 中提及 Enformer 但未对比 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **图结构先验优于纯序列长程建模**：对于 TF–DNA 互作研究，与其让模型从序列中隐式学习「哪些远端区域会环化」，不如直接使用 Hi-C/HiChIP 测得的 3D 互作图作为显式图结构。这一归纳偏置大幅降低了学习难度，且使模型输出可解释（注意力权重 = 调控重要性）。**可迁移到本课题**：在预测 TF 结合位点功能影响时，可将 3D 互作作为边、TF 结合位点作为节点特征，构建图神经网络。

2. **注意力机制 = 可解释的调控权重**：GAT 的注意力系数直接给出了每个增强子对目标基因的贡献权重，这比黑盒 CNN 的 saliency 更符合生物学直觉。**可迁移到本课题**：在 TF–DNA 结合机制研究中，可用 GAT 学习「哪些 TF 结合位点对靶基因表达贡献最大」，从而优先验证高权重位点。

3. **多任务学习引导更好的中间表示**：Seq-GraphReg 同时预测表观基因组信号和 CAGE 表达，使 CNN 学习到有生物学意义的 motif 表示。**可迁移到本课题**：在 TF–DNA 结合预测中，可同时预测 ChIP-seq 峰、DNase 可及性和表达，迫使模型学习更鲁棒的 TF 结合特征。

4. **In silico motif ablation 作为 TF 靶标预测框架**：通过将 TF 的 motif 从序列中抹去并比较预测表达变化，可以预测 TF 敲低的直接靶标。**可迁移到本课题**：对于任意 TF，可先用 GraphReg 类模型预测 motif 敲除后的表达变化，再与 CRISPRi 实验对比，形成「计算预测 → 实验验证」闭环。

5. **分离训练缓解长序列内存瓶颈**：将 6 Mb 序列的表观预测与表达预测分离，先用小窗口（100 kb）训练表观预测，再冻结 CNN 训练图传播，避免了端到端训练的内存爆炸。**可迁移到本课题**：在长序列（>1 Mb）的 TF 结合预测中，可先训练局部 motif 检测器，再在 3D 图上传播信息。

6. **FFT 损失平滑归因图**：通过惩罚 saliency 的高频成分，使归因图更聚焦于连续调控区域。**可迁移到本课题**：在 TF 结合位点的 saliency 分析中，FFT 损失可减少单碱基噪声，突出功能域级别的调控区域。

## 15 与已有知识连接

- **Basenji（Kelley et al., 2018）**：本文的 CNN 编码器设计直接借鉴 Basenji 的架构思路，但 Basenji 仅用 dilated CNN 扩大感受野（约 100 kb），而 GraphReg 通过 3D 图传播将感受野扩展至 2 Mb。可对比：Basenji 的 dilated CNN 在 100 kb 内有效，但无法覆盖更远增强子。
- **Enformer（Avsec et al., 2021a）**：transformer 架构将感受野扩至 100 kb，但计算成本高且仍受限于序列距离。GraphReg 的图传播策略是替代方案，且更直接利用实验互作数据。
- **ABC 模型（Fulco et al., 2019）**：线性模型，分数 = 活性 × 接触度。GraphReg 在增强子识别上优于 ABC，说明非线性特征学习 + 序列信息有增量价值。
- **GC-MERGE（Bigness et al., 2021）**：使用 GCN 结合 Hi-C 预测表达。GraphReg 的 GAT 可学习边权重，优于 GCN 的等权聚合。
- **DeepSEA / DeepBind（Zhou & Troyanskaya, 2015；Alipanahi et al., 2015）**：序列→染色质/结合预测的 CNN 模型，GraphReg 的 Seq 版本扩展了这类模型到表达预测。
- **TF–DNA 结合机制相关**：本文的 motif ablation 方法可视为「计算版 TF 敲低」，与 ChIP-seq 基序分析互补——ChIP-seq 给出结合位置，GraphReg 给出结合对表达的功能影响。
- **Hi-C 数据处理（HiC-DC+，Carty et al., 2017；Sahin et al., 2021）**：本文的图构建依赖 HiC-DC+ 的显著互作识别，这一流程可迁移到其他 3D 基因组 + 深度学习任务。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF 结合位点功能评分模型（TFBS-FuncScore）
   - **来源局限/观察**：GraphReg 的 motif ablation 只能评估 TF 对基因表达的整体影响，无法定位到具体结合位点；且仅适用于有已知 motif 的 TF。
   - **核心假设**：将 TF 结合位点作为图节点、3D 互作作为边，用 GAT 学习每个结合位点对靶基因表达的功能贡献，可实现对单个 SNP 或结合位点的功能评分。
   - **增量**：相比 GraphReg 的 bin 级归因，实现位点级归因；可扩展到无已知 motif 的 TF（用 ChIP-seq 峰定义结合位点）。
   - **初步方法**：在 GraphReg 框架中，将 TF 结合位点（ChIP-seq 峰或 motif 预测）作为额外节点，与 bin 节点共同参与 GAT 传播；训练后对每个 TFBS 节点计算注意力权重 × 梯度，作为功能评分。
   - **验证方式**：用 CRISPRi-FlowFISH/TAP-seq 数据验证评分与实验增强子功能的相关性；用已知致病 SNP 验证评分与疾病关联的富集。
   - **创新状态**：unverified

2. **候选名称**：跨细胞类型 TF 调控泛化模型（CrossCell-TFReg）
   - **来源局限/观察**：GraphReg 的 Seq 版本是细胞类型特异的，无法直接迁移到新细胞类型；而 Epi 版本虽可迁移，但需要目标细胞类型的表观数据。
   - **核心假设**：TF 结合基序的序列特征在不同细胞类型间共享，细胞类型特异性来自 3D 互作和表观状态的差异。通过对抗训练或元学习，可分离「共享的 TF 结合规则」与「细胞类型特异的调控环境」。
   - **增量**：实现从训练细胞类型到新细胞类型的零样本或少样本表达预测。
   - **初步方法**：在 Seq-GraphReg 中引入细胞类型嵌入向量，用对抗训练使 CNN 编码器学习细胞类型无关的 motif 表示；GAT 层接收细胞类型特异的 3D 互作图。
   - **验证方式**：在 4 个细胞系上留一交叉验证，评估新细胞类型的表达预测 R；用 TF 敲除数据验证跨细胞类型的靶标预测一致性。
   - **创新状态**：unverified

3. **候选名称**：3D 互作引导的 TF–DNA 结合特异性预测（HiC-TFBind）
   - **来源局限/观察**：现有 TF 结合预测模型（如 DeepSEA）仅使用序列，忽略 3D 互作对结合的影响；GraphReg 虽用 3D 互作预测表达，但不直接预测 TF 结合。
   - **核心假设**：3D 互作信息（特别是 E-P 互作）能提高 TF 结合位点预测的准确性，尤其是远端结合位点。
   - **增量**：将 3D 互作作为图结构，预测 TF 在特定细胞类型中的结合（ChIP-seq 峰），而非仅预测表达。
   - **初步方法**：以序列 CNN 为编码器，将候选结合位点作为节点，3D 互作作为边，用 GAT 聚合邻域信息，预测每个位点的 TF 结合概率。
   - **验证方式**：用 ENCODE ChIP-seq 数据（如 JUND、CTCF）评估 AUPR，与 DeepSEA、BPNet 对比；特别评估远端（>100 kb）结合位点的预测提升。
   - **创新状态**：unverified

4. **候选名称**：变异效应预测的 3D 感知框架（Variant3D）
   - **来源局限/观察**：GraphReg 未直接评估非编码变异对表达的影响；现有变异效应预测工具（如 Enformer）受限于 100 kb 窗口。
   - **核心假设**：通过 3D 互作图传播，可预测远端非编码变异对靶基因表达的影响，且比序列窗口方法更准确。
   - **增量**：将 GraphReg 扩展到变异效应预测，特别是远端增强子区域的 SNP。
   - **初步方法**：对每个 SNP，分别用参考/变异等位基因替换序列输入，计算预测 CAGE 的差异；结合 GAT 注意力权重，将变异效应归因到具体靶基因。
   - **验证方式**：用 eQTL 数据验证预测效应方向与真实 eQTL 的一致性；用已知致病非编码变异验证富集。
   - **创新状态**：unverified

5. **候选名称**：单细胞 3D 调控建模（scGraphReg）
   - **来源局限/观察**：GraphReg 使用 bulk CAGE 和 bulk Hi-C，无法解析细胞异质性；单细胞多组学（scATAC + scRNA + scHi-C）数据日益丰富。
   - **核心假设**：在单细胞水平，3D 互作和表观状态的共变可揭示细胞类型特异的 TF 调控逻辑。
   - **增量**：将 GraphReg 扩展到单细胞数据，实现细胞类型特异的增强子-基因调控网络推断。
   - **初步方法**：用 scATAC 构建每类细胞的表观特征，用 scHi-C 或预测的 3D 互作构建图，用 GAT 预测 scRNA 表达；通过注意力权重推断细胞类型特异的调控网络。
   - **验证方式**：在已有单细胞多组学数据（如骨髓、脑组织）上验证表达预测准确性；与已知细胞类型标记基因的调控网络对比。
   - **创新状态**：unverified