## 01 基本信息

- **标题**：Deep dynamical models of single-cell multiomic velocities predict loss-of-function and rescue perturbations in B cells
- **作者与单位**：Karbalayghareh, Alireza; Pelzer, Benedikt; Chin, Christopher R; Melnick, Ari; Barisic, Darko; Leslie, Christina S（单位未在摘要中提供）
- **期刊/预印本平台**：bioRxiv : the preprint server for biology
- **年份**：2026-07-03（预印本日期）
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：计算生物学 / 单细胞多组学 / 深度学习 / 基因调控网络
- **关键词**：neural ODE, single-cell multiome, RNA velocity, TF motif accessibility, germinal center B cells, perturbation prediction, gene regulatory networks
- **DOI/arXiv 号**：10.1101/2025.04.24.650458
- **代码**：https://github.com/karbalayghareh/DynaVelo
- **数据**：GSE237990, GSE294051, GSE334370；预处理 AnnData 对象见 Figshare（https://figshare.com/s/84862d73cc45f47c9d94）
- **阅读日期**：未提供
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：本文聚焦 TF–DNA 结合的功能后果——通过单细胞多组学（RNA + ATAC）数据，用 neural ODE 联合建模基因表达与 TF motif 可及性动态，推断 TF 驱动的细胞命运转变，并预测 TF 敲除/扰动对细胞动态的 rescue 效应。与经典 TF–DNA 结合机制研究（如结合位点预测、结构模拟）不同，本文从系统层面将 TF 活性（motif accessibility）作为动态变量纳入微分方程，属于「TF–DNA 互作 × 深度学习」中偏动态建模与扰动预测的一支。

## 02 一句话总结

本文提出 DynaVelo——一个生成式 neural ODE 模型，联合建模单细胞多组学数据中的基因表达与 TF motif 可及性动态，在生发中心 B 细胞中恢复已知的复杂分化轨迹，并通过对 Arid1a 功能缺失突变的 in silico 扰动预测出可实验验证的 rescue 靶点（Ctcf、Bcl6、Stat3）。

## 03 研究问题

- **具体问题**：如何从单细胞多组学（同一细胞的 RNA 表达 + 染色质可及性）快照数据中，推断细胞状态随时间的动态变化，并预测基因/TF 扰动（如功能缺失突变）对细胞命运轨迹的影响？
- **为什么重要**：单细胞测序是破坏性的，无法直接追踪同一细胞随时间的变化；而细胞命运决定（如生发中心 B 细胞分化）本质上是动态过程。若能可靠地推断动态并预测扰动效应，将极大加速对基因调控机制的理解和疾病干预靶点的发现。
- **现有方法不足**：
  - RNA velocity 方法（Velocyto, scVelo）仅利用剪接动力学，且只覆盖部分基因，未利用染色质可及性信息；
  - MultiVelo 虽整合了染色质可及性，但仍是基于基因的 ODE，不提供生成式框架，无法进行 in silico 扰动；
  - Dynamo 和 scDiffEq 等深度学习方法只建模基因表达，未利用 TF motif 活性这一关键调控层。
- **精确的「Can ... ?」问题**：Can a generative neural ODE model that jointly learns RNA expression and TF motif accessibility dynamics from single-cell multiome data predict the effects of loss-of-function perturbations and identify rescue perturbations in a complex in vivo system (germinal center B cells)?

## 04 背景与发展脉络

> 注：以下脉络基于本文摘要与引言的描述，属于「仅本文框架」的梳理，未经外部文献核验。

1. **RNA velocity 时代**：Velocyto（2018）提出用剪接/未剪接 mRNA 比例推断细胞状态变化方向；scVelo（2020）将其推广为可估计基因特异动力学参数的模型。局限：仅覆盖部分基因，对染色质动态不敏感。
2. **多组学 velocity**：MultiVelo（2023）将染色质可及性纳入 ODE 框架，扩展了 velocity 的适用范围。局限：仍为基因级 ODE，无生成能力，无法做扰动预测。
3. **深度生成模型用于细胞动态**：Dynamo（2022）用向量场重建细胞状态流形；scDiffEq（2023）用神经微分方程建模细胞动态。局限：仅用 RNA 表达，未利用 TF motif 活性。
4. **本文位置**：DynaVelo 首次将 neural ODE 与单细胞多组学结合，联合建模 RNA 表达与 TF motif 可及性动态，并利用生成式框架实现 in silico 扰动预测——填补了「多组学动态建模」与「扰动预测」之间的空白。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| RNA velocity 覆盖度有限 | 仅部分基因有可靠的剪接动力学估计 | 剪接/未剪接计数稀疏，低表达基因无法估计 | 摘要：「partial RNA velocity information」；Methods 中 velocity genes 仅 ~400–1000 个 |
| 单模态建模信息不足 | 仅用 RNA 无法捕捉 TF 调控的动态 | 染色质可及性变化先于或独立于 RNA 变化 | 摘要：「TF motif accessibility data to improve the modeling of cell state dynamics」 |
| 静态 GRN 无法反映动态调控 | 文献 GRN 是静态的，无法区分细胞状态特异的调控 | 传统 GRN 推断基于相关性或 ChIP-seq 的静态结合 | Results 图 5：「known TF-to-gene regulatory relationships are reported as static rather than cell-state-dependent」 |
| 无法预测扰动效应 | 现有 velocity 方法只能描述，不能干预 | 缺乏生成式模型，无法在 silico 中模拟基因敲除 | 摘要：「in silico perturbation analysis further enables DynaVelo to infer dynamic and cell-state-specific GRNs」 |
| 突变表型难以在体内验证 | 体内验证每个预测靶点成本高、周期长 | 需要先验筛选候选靶点 | Results 图 6：仅对 3 个预测靶点（Ctcf、Bcl6、Stat3）进行体内验证 |

## 06 核心思想

**1) 表面方法**：
DynaVelo 是一个变分 neural ODE 框架。它将每个细胞的 RNA 表达向量 x(t) 和 TF motif 可及性向量 y(t) 分别编码到低维潜空间，在潜空间中用 neural ODE 联合建模两者的动态，通过重建损失、KL 正则、RNA velocity 监督（来自 scVelo）和跨模态 velocity 一致性损失联合训练。训练后可生成轨迹、计算 Jacobian 矩阵推断 GRN、执行 in silico 扰动。

**2) 核心洞察**：
- **TF motif 可及性是 RNA 动态的「前导指标」**：染色质开放状态的变化往往先于或驱动基因表达变化，将两者联合建模可提供比单模态更丰富的动态信息。
- **生成式框架使「干预」成为可能**：一旦学到向量场 f(z)，就可以在 silico 中修改某个基因/TF 的状态，观察轨迹如何偏离，从而预测扰动效应——这是判别式 velocity 方法无法做到的。
- **Jacobian 矩阵提供细胞特异的调控关系**：通过计算 velocity 对输入状态的偏导数，可以在单个细胞水平上推断「谁调控谁」，超越静态 GRN 的平均化描述。

**3) 可能的普适教训 [Analysis]**：
- 在动态系统建模中，「可干预性」是生成模型相对判别模型的根本优势——不仅描述系统，还能询问「如果……会怎样」。
- 多模态信息（RNA + 染色质）的联合建模不是简单拼接，而是通过跨模态一致性损失实现「相互校准」，这可能是处理高噪声单细胞数据的有效策略。
- 对 TF–DNA 互作研究而言，motif accessibility 作为 TF 活性的代理变量，与 RNA 表达联合建模，提供了一种不依赖 ChIP-seq 或 ATAC-seq 峰值注释的动态调控推断途径。

## 07 方法总览

- **输入**：单细胞多组学数据——每个细胞的 (1) 基因表达向量 x ∈ R^m（log-normalized），(2) TF motif 可及性向量 y ∈ R^k（chromVAR z-scores），(3) scVelo 提供的部分基因 RNA velocity 估计（作为监督信号）。
- **输出**：(1) 每个细胞的潜空间表示 z(t) 和潜时间 t；(2) 所有基因的 RNA velocity 和所有 TF motif 的 motif velocity；(3) 细胞特异的 Jacobian 矩阵（4 类：RNA→RNA、RNA→motif、motif→RNA、motif→motif）；(4) in silico 扰动后的 delta velocity 场。
- **模块**：RNA 编码器、motif 编码器、潜空间 neural ODE（两个并行子网络分别预测 RNA 和 motif 潜速度）、RNA 解码器（ReLU 输出）、motif 解码器（线性输出）、时间编码器（Beta 分布）。
- **训练**：Adam 优化器，初始学习率 1e-3，plateau 调度（factor=0.5, patience=5），early stopping（patience=10），batch size 128/256，单张 RTX A6000 GPU，最多 200 epochs，通常 3 小时内完成。
- **推理**：默认确定性模式（使用后验均值），也可随机采样（nsamples=100）估计不确定性。
- **反馈回路**：训练时通过 4 个损失项形成反馈——重建损失（确保解码保真）、KL 损失（正则化潜空间）、RNA velocity 监督（对齐 scVelo 估计）、跨模态 velocity 一致性（确保 RNA 和 motif 轨迹一致）。
- **文字流程**：输入 x,y → 编码器得到潜状态 z_x(0), z_y(0) 和潜时间 t → neural ODE 从 t=0 积分到 t → 解码器重建 x̂, ŷ → 计算损失 → 反向传播更新编码器、ODE、解码器参数。训练后，对任意细胞可计算其 Jacobian 矩阵（用于 GRN）或执行 in silico 扰动（修改输入状态，重新积分 ODE，比较 delta velocity）。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| RNA 编码器 | 将高维基因表达映射到低维潜空间 | 高维稀疏数据难以直接建模动态 | 输入 x ∈ R^m → 输出 z_x(0) 的均值/方差 | Methods 节 | 预期：无法有效降维，训练不稳定 [Analysis] |
| Motif 编码器 | 将 TF motif 可及性映射到低维潜空间 | 提供 RNA 之外的独立调控信息通道 | 输入 y ∈ R^k → 输出 z_y(0) 的均值/方差 | Methods 节 | 预期：失去跨模态信息，动态推断退化 [Analysis] |
| 潜空间 neural ODE | 联合建模 RNA 和 motif 潜状态的动态 | 核心动态模型，提供向量场 f(z) | 输入 z(0), t → 输出 z(t) | Methods 节；Results 图 2 轨迹恢复 | 移除后模型退化为静态 VAE，无法推断 velocity 或做扰动 |
| RNA 解码器 | 从潜状态重建基因表达 | 确保潜空间保留表达信息 | 输入 z_x(t) → 输出 x̂(t)（ReLU） | Methods 节 | 预期：重建质量下降，潜空间失去生物学意义 [Analysis] |
| Motif 解码器 | 从潜状态重建 motif 可及性 | 确保潜空间保留染色质信息 | 输入 z_y(t) → 输出 ŷ(t)（线性） | Methods 节 | 预期：motif 动态无法恢复 [Analysis] |
| 时间编码器 | 推断每个细胞的潜时间 t | 提供细胞沿轨迹的时间排序 | 输入 x, y → 输出 Beta(α_t, β_t) | Methods 节 | 预期：失去时间排序，轨迹无法构建 [Analysis] |
| RNA velocity 监督损失 | 对齐 scVelo 估计的 velocity | 提供动态方向的先验知识 | 预测 v_x vs scVelo v_x → cosine 损失 | Methods 节；Results 图 2 对比 | 移除后动态方向可能偏离真实生物学 |
| 跨模态 velocity 一致性损失 | 确保 RNA 和 motif 轨迹一致 | 防止两个模态动态分叉 | K_vx vs K_vy → MSE | Methods 节 | 移除后 RNA 和 motif 轨迹可能不一致，GRN 推断不可靠 |
| Jacobian 计算模块 | 计算 velocity 对输入的偏导数 | 推断细胞特异的调控关系 | 输入细胞状态 → 输出 4 类 Jacobian 矩阵 | Results 图 5 | 移除后无法获得 GRN 边 |
| in silico 扰动模块 | 模拟基因/TF 敲除 | 预测扰动对动态的影响 | 输入扰动靶点 → 输出 delta velocity | Results 图 6 | 移除后丧失核心应用价值 |

## 09 关键公式符号

**1) 联合 ODE 模型**（Methods 节，公式 1）：
```
dx(t)/dt = f_x(x(t), y(t))
dy(t)/dt = f_y(x(t), y(t))
```
- x(t) ∈ R^m：log-normalized 基因表达
- y(t) ∈ R^k：chromVAR TF motif z-scores
- f_x, f_y：待学习的动态函数（由 neural ODE 参数化）

**2) 潜空间 ODE**（Methods 节，公式 2）：
```
dz_x(t)/dt = f_zx(z_x(t), z_y(t))
dz_y(t)/dt = f_zy(z_x(t), z_y(t))
```
- z_x ∈ R^dx, z_y ∈ R^dy：潜状态，默认 dx = dy = 50
- 解为初值问题：z(t) = z(0) + ∫₀ᵗ f_z(z(τ))dτ

**3) 观测空间速度**（Methods 节，公式 4）：
```
v_x(t) = dμ_x(t)/dt = J_gx × dz_x(t)/dt = J_gx f_zx
v_y(t) = dμ_y(t)/dt = J_gy × dz_y(t)/dt = J_gy f_zy
```
- J_gx = ∂g_x/∂z_x ∈ R^(m×dx)：RNA 解码器 Jacobian
- J_gy = ∂g_y/∂z_y ∈ R^(k×dy)：motif 解码器 Jacobian

**4) 总损失**（Methods 节，公式 4-7）：
```
L = L_reconstruction + κ₁·L_velocity + κ₂·L_velocity_consistency + κ₃·L_regularization
```
- L_reconstruction：高斯似然重建损失（RNA + motif）
- L_velocity = -cos(v_x^Gv, v_x^scVelo^Gv)：RNA velocity 余弦相似度
- L_velocity_consistency = ‖K_vx - K_vy‖²：跨模态速度一致性
- L_regularization：KL(潜状态 || N(0,I)) + KL(潜时间 || Beta(2,2))
- 默认 κ₁ = κ₂ = 10000，κ₃ = 1000（velocity/时间任务）或 1（扰动预测任务）

**5) Jacobian 矩阵**（Methods 节，公式 11）：
```
J_xx^(c)[i,j] = ∂f_x[i]/∂x[j] |_{x=x(c), y=y(c)}
J_yx^(c)[i,j] = ∂f_y[i]/∂x[j] |_{x=x(c), y=y(c)}
J_xy^(c)[i,j] = ∂f_x[i]/∂y[j] |_{x=x(c), y=y(c)}
J_yy^(c)[i,j] = ∂f_y[i]/∂y[j] |_{x=x(c), y=y(c)}
```
- 用于推断 GRN 边：J_xx 和 J_yx 表示 RNA 表达对速度的影响，J_xy 和 J_yy 表示 motif 可及性对速度的影响

## 10 实验设计与证据链

**数据集与群体**：
- 7 个小鼠生发中心 B 细胞多组学样本（10x Multiome，RNA + ATAC）：3 个 WT、1 个 Arid1aHet、1 个 CtcfHet、2 个 Arid1aHom
- 细胞数：5,000–20,000（训练后过滤）
- 验证用新样本：6 个多组学样本（WT×2、Arid1aHet×2、Arid1aHet;CtcfHet DKO×2），细胞数 12,460–15,327

**指标**：
- 轨迹恢复质量（定性：与已知 GC 分化的 UMAP 对比）
- GRN 边恢复（与文献已知调控关系对比）
- 扰动预测准确率（DV overlap、DV direction agreement）
- Rescue 率（预测扰动后向 WT 方向恢复的速度比例）

**基线**：scVelo、MultiVelo（velocity 质量对比）；未提供 GRN 推断的定量基线对比

**评测协议**：
- 训练/验证 90%/10% 划分
- 潜时间与已知细胞类型注释的对应关系
- 对 Arid1aHet 模型进行全基因组 in silico 敲除扫描，计算每个基因敲除后的 rescue 率
- 对 top 候选（Ctcf、Bcl6、Stat3）进行体内验证（DKO 小鼠 + 流式细胞术）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| WT GC 轨迹恢复 | DynaVelo 能恢复已知 GC 动态 | 与 scVelo、MultiVelo 对比 | DynaVelo 恢复 CB→CC→prememory 及 CB 细胞周期分支；scVelo 无法区分 CB/CC 潜时间；MultiVelo 轨迹方向错误 | 联合建模 RNA + motif 优于单模态或基因级方法 | 未提供定量轨迹相似度指标 | Results 图 2, Supp. Fig. S2 |
| 突变体动态变化 | DynaVelo 能捕捉 Arid1aHet/CtcfHet 的轨迹改变 | WT vs 突变体模型对比 | 突变体失去 CC→CB 再循环轨迹，prememory 出口增加 | 模型能捕捉遗传扰动的动态后果 | 未提供统计显著性检验 | Results 图 4 |
| Jacobian GRN 恢复 | DynaVelo 能恢复已知 TF→gene 调控边 | 与文献已知 GC GRN 对比 | 恢复 Spi1→Bcl6、Foxo1→Cxcr4 等已知边 | 动态 GRN 推断可行 | 未提供精确率/召回率 | Results 图 5 |
| In silico Arid1a KO 预测 | 预测的 delta velocity 与真实 Arid1aHet 一致 | 预测 vs 真实突变体 | motif velocity 预测更准确（DV overlap 更高） | 模型可预测扰动效应 | RNA velocity 预测精度有限 | Results 图 6b-c |
| Rescue 靶点预测 | 敲除 Ctcf/Bcl6/Stat3 可 rescue Arid1aHet 表型 | 全基因组扫描 + top 3 体内验证 | 3/3 靶点在 DKO 小鼠中恢复 WT DZ/LZ 比值 | 模型可识别功能性遗传互作 | 未测试其他预测靶点 | Results 图 6d-g |

## 11 结论正确解读

- **任务范围**：本文的预测限于「生发中心 B 细胞」这一特定系统，且扰动类型为基因/TF 的完全敲除（设为最小值），不涵盖过表达、条件性敲除、药物抑制等更复杂的扰动模式。
- **Oracle/真值输入**：模型依赖 scVelo 提供的部分基因 RNA velocity 作为监督信号。scVelo 本身的估计误差会传播到 DynaVelo 中；作者未分析这种误差传播的边界。
- **端到端状态**：模型并非完全端到端——需要先运行 scVelo 获得 velocity 估计，再运行 chromVAR 获得 motif 活性，然后才训练 DynaVelo。上游工具的选择会影响下游结果。
- **算力成本**：训练在单张 RTX A6000 上最多 3 小时，成本可控；但 Jacobian 计算和全基因组扰动扫描的计算成本未报告。
- **历史数据依赖**：模型使用单时间点快照数据推断动态，本质上是「横断面推断纵向」，无法替代真正的时序实验。预测的轨迹需要实验验证。
- **最难情形**：模型在快速增殖的 CB 细胞周期轨迹上表现较好，但在区分相似细胞状态（如 CC 亚型）时可能失效；对低表达基因的 velocity 预测不可靠。
- **群体/领域边界**：结论仅适用于小鼠生发中心 B 细胞。作者未在人类样本或其他组织类型上验证。
- **不确定性**：模型提供后验采样（nsamples=100），但作者未报告预测的置信区间如何随细胞类型或基因类型变化。

**有边界的复述**：DynaVelo 能够从单细胞多组学快照中推断生发中心 B 细胞的动态轨迹，并在该系统中以可实验验证的准确率预测基因敲除对细胞命运的影响——但这一能力目前仅限于小鼠 GC B 细胞、完全敲除型扰动、以及有 scVelo 可靠估计的基因子集。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 依赖 scVelo 的 velocity 估计 | 仅部分基因有可靠的 velocity 监督信号 | 未明确提及 | 摘要：「partial RNA velocity information」 |
| 静态 GRN 对比困难 | 文献 GRN 是静态的，无法直接对比动态 GRN | 未明确提及 | Results 图 5 讨论 |
| 扰动类型有限 | 仅模拟完全敲除（设为最小值） | 未明确提及 | Methods「In silico perturbations」节 |
| 计算成本 | 全基因组扰动扫描计算量大 | 未明确提及 | Methods 节 |
| 模型超参数敏感性 | κ₁, κ₂, κ₃ 需根据任务调整 | 未明确提及 | Methods「Hyperparameter selection」节 |
| 体内验证范围 | 仅验证了 3 个 rescue 靶点 | 未明确提及 | Results 图 6 |

> 注：作者在摘要和正文中未系统列出局限性；以上为从文中可明确识别的作者承认的约束。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 轨迹恢复的评估主要依赖定性 UMAP 对比 | 可能选择性展示有利视角；缺乏定量指标（如轨迹一致性分数） | 定性对比容易受主观影响，无法判断模型是否真的优于基线 | 计算轨迹相似度的定量指标（如 F1 score、Earth Mover's Distance） | Results 图 2 描述 |
| 体内验证仅覆盖 3 个靶点 | 可能只报告了成功的验证；未报告失败案例 | 若存在大量未验证的预测，模型的泛化能力被高估 | 要求作者报告所有预测靶点的验证结果，包括阴性结果 | Results 图 6 |
| 未与现有 GRN 推断方法定量对比 | 无法判断 Jacobian 方法是否优于相关性或回归方法 | 读者无法评估该方法的增量贡献 | 与 GENIE3、GRNBoost2 等标准方法在相同数据上对比 AUROC/AUPRC | Results 图 5 |
| 模型对 scVelo 的依赖未被消融 | 若 scVelo 估计有偏，DynaVelo 的改进可能来自噪声拟合 | 需要确认模型对上游噪声的鲁棒性 | 用不同 scVelo 参数或不同 velocity 方法（如 Velocyto）重复训练，比较稳定性 | Methods 节 |
| 未报告 Jacobian 估计的方差 | 单细胞数据噪声大，Jacobian 可能不稳定 | 若 Jacobian 不稳定，GRN 边的可靠性存疑 | 用 bootstrap 或多次采样估计 Jacobian 的置信区间 | Methods「Calculating the Jacobian matrices」节 |
| 潜时间先验 Beta(2,2) 的选择缺乏论证 | 可能不适用于所有细胞类型 | 不合适的先验可能扭曲时间推断 | 比较不同先验（如均匀分布、对数正态）对轨迹的影响 | Methods 节 |
| 未讨论模型在非 GC 系统上的可迁移性 | 可能过拟合 GC B 细胞的特定动态 | 限制了方法的通用性声明 | 在独立数据集（如造血分化、胚胎发育）上测试 | 未提供 |

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **多模态联合动态建模**：将 RNA 表达与 TF motif 可及性作为耦合的动态变量联合建模，而非独立处理，可提供比单模态更丰富的动态信息。**迁移到本课题**：在 TF–DNA 互作研究中，可将 ChIP-seq 或 ATAC-seq 衍生的 TF 结合活性与下游基因表达联合建模，推断 TF 结合的动态功能后果。

2. **生成式框架的「可干预性」**：一旦学到向量场，就可以在 silico 中模拟扰动（如敲除某个 TF），观察系统如何响应——这是判别式方法无法做到的。**迁移到本课题**：对 TF–DNA 互作，可模拟 TF 结合位点突变或 TF 表达降低对下游调控网络的影响，优先排序实验验证靶点。

3. **Jacobian 矩阵作为动态 GRN 的数学工具**：通过计算 velocity 对输入状态的偏导数，可以在单细胞水平推断「谁调控谁」，且是细胞状态特异的。**迁移到本课题**：可用于推断 TF–靶基因调控关系的方向性和强度，超越静态相关性网络。

4. **跨模态一致性损失**：通过约束 RNA 和 motif 两个模态的轨迹一致性，实现相互校准，减少单模态噪声。**迁移到本课题**：在整合多组学数据（如 ChIP-seq + RNA-seq + 3D 基因组）时，可设计类似的一致性约束，提高推断稳健性。

5. **潜时间推断优于伪时间**：通过变分推断学习每个细胞的潜时间（而非启发式伪时间），可更好地处理分支和循环轨迹。**迁移到本课题**：在研究 TF 驱动的细胞命运决定时，潜时间可提供比现有伪时间方法更准确的时间排序。

6. **扰动预测的定量评估框架**：DV overlap 和 DV direction agreement 提供了评估扰动预测准确性的可量化指标。**迁移到本课题**：可用于评估 TF 扰动预测模型（如基于深度学习的 TF 结合位点突变效应预测）的性能。

## 15 与已有知识连接

- **RNA velocity 方法**：Velocyto（La Manno et al., 2018, Nature）、scVelo（Bergen et al., 2020, Nature Biotechnology）——本文的 velocity 监督信号来源，也是主要对比基线。
- **多组学 velocity**：MultiVelo（Li et al., 2023, Nature Biotechnology）——本文直接对比的方法，同样利用染色质可及性但缺乏生成式框架。
- **Neural ODE**：Chen et al. (2018, NeurIPS) 首次提出；本文将其扩展为变分生成式框架用于单细胞动态建模。
- **单细胞动态建模**：Dynamo（Qiu et al., 2022, Cell）——用向量场重建细胞状态流形，但仅用 RNA；scDiffEq（Tong et al., 2023, NeurIPS）——用神经微分方程建模细胞动态，同样仅用 RNA。
- **生发中心 B 细胞生物学**：GC 反应中 B 细胞在暗区（CB）增殖和体细胞超突变、亮区（CC）选择和亲和力成熟之间循环（Victora & Nussenzweig, 2012, Annual Review of Immunology）——本文的生物学背景。
- **TF–DNA 互作与染色质**：chromVAR（Schep et al., 2017, Nature Methods）——本文的 TF motif 活性来源；TF 作为 pioneer factor 调控染色质开放（如 Spi1 在 GC 中的作用，文献 30）。
- **扰动预测**：CPA（Lotfollahi et al., 2023, Nature Biotechnology）——用条件自编码器预测单细胞扰动响应，与本文的 in silico 扰动目标相似但方法不同。
- **候选方向 [Analysis]**：本文的 Jacobian 动态 GRN 方法可与基于 ATAC-seq 的 cis-regulatory 推断（如 SCENIC）结合，或与基于结构的 TF–DNA 结合预测（如 AlphaFold 3、DeepMind）整合，形成从「结合」到「功能」的完整链条。

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选 1：基于结构的 TF–DNA 结合预测与动态 GRN 的整合**
- **来源局限/观察**：DynaVelo 的 GRN 推断基于统计关联（Jacobian），不包含 TF–DNA 结合的物理化学约束；而基于结构的预测（如 AlphaFold 3、RoseTTAFold 或分子对接）可提供结合亲和力信息，但缺乏动态和细胞状态特异性。
- **核心假设**：将结构预测的 TF–DNA 结合亲和力作为先验约束，可提高动态 GRN 推断的准确性和可解释性。
- **初步方法**：对 GC B 细胞中关键 TF（如 Spi1、Bcl6、Foxo1）与其靶基因启动子/增强子区域进行结构预测或对接打分，将结合亲和力作为 Jacobian 推断的正则化先验。
- **验证方式**：在已知调控关系的数据集上比较有无结构先验的 GRN 推断 AUROC；用 ChIP-seq 数据验证预测的 TF 结合位点。
- **创新状态**：unverified

**候选 2：TF 结合位点突变的 in silico 饱和扫描**
- **来源局限/观察**：DynaVelo 的扰动仅模拟基因表达水平的敲除，不模拟顺式调控元件（如 TF 结合位点）的序列变异；而实际疾病相关变异多位于非编码调控区。
- **核心假设**：在 DynaVelo 框架中引入序列级别的扰动（如 TF motif 的碱基替换），可预测非编码变异对细胞命运的影响。
- **初步方法**：对 GC B 细胞中关键增强子的 TF 结合位点进行饱和突变，将突变后的 motif 活性变化作为扰动输入，观察 delta velocity 的变化。
- **验证方式**：用 CRISPR 编辑或报告基因实验验证 top 预测位点；与 GWAS 中 B 细胞相关疾病的非编码变异交叉验证。
- **创新状态**：unverified

**候选 3：跨物种 TF–DNA 互作动态的迁移学习**
- **来源局限/观察**：DynaVelo 仅在鼠类 GC B 细胞上验证；人类 GC B 细胞动态可能不同，但数据更稀缺。
- **核心假设**：TF–DNA 互作的核心调控逻辑在物种间保守，可通过迁移学习从鼠类模型适应到人类。
- **初步方法**：在鼠类 GC B 细胞上预训练 DynaVelo，用少量人类 GC B 细胞多组学数据微调，比较迁移学习与从头训练的性能。
- **验证方式**：在人类扁桃体或淋巴结 GC B 细胞数据上评估轨迹恢复和 GRN 推断质量。
- **创新状态**：unverified

**候选 4：结合分子动力学模拟的 TF–DNA 结合动态**
- **来源局限/观察**：DynaVelo 的 motif accessibility 是静态快照，不包含 TF–DNA 结合的构象动态；而 MD 模拟可提供结合/解离的动力学参数。
- **核心假设**：将 MD 模拟得到的 TF–DNA 结合动力学参数（如 residence time、结合自由能）作为 motif 活性的动态权重，可改进 velocity 预测。
- **初步方法**：对 GC 关键 TF–DNA 复合物进行 μs 级 MD 模拟，提取结合动力学特征，将其作为 DynaVelo 中 motif 输入的时变权重。
- **验证方式**：比较有无 MD 增强的 velocity 预测与实验（如 RNA 代谢标记）的一致性。
- **创新状态**：unverified

**候选 5：TF 协同性的动态建模**
- **来源局限/观察**：DynaVelo 的 Jacobian 推断主要捕捉单基因→单基因的调控关系，未显式建模多个 TF 在同一增强子上的协同结合。
- **核心假设**：TF 协同结合（如 Spi1 与 Nfkb1 在 GC 中的协同）可通过高阶 Jacobian 或注意力机制捕捉。
- **初步方法**：在 DynaVelo 的 ODE 中引入 TF–TF 交互项，或使用图注意力网络建模 TF 协同模块。
- **验证方式**：与 ChIP-seq 共结合数据对比；用 CRISPR 双敲除验证预测的协同效应。
- **创新状态**：unverified