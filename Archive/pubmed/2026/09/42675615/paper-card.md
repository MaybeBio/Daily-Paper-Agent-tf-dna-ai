## 01 基本信息
- **标题**：mmVelo: a deep generative model for estimating cell state-dependent dynamics across multiple modalities
- **作者与单位**：Nomura, Satoshi; Kojima, Yasuhiro; Minoura, Kodai; Hayashi, Shuto; Abe, Ko; Hirose, Haruka; Shimamura, Teppei（单位未在提供材料中明确列出，推测为日本研究机构，如 Institute of Science Tokyo 相关，因 Funding 中提及该机构）
- **期刊/预印本平台**：Bioinformatics (Oxford, England)
- **年份**：2026-09-01（在线发表；DOI 含 btag652，实际接收/发表年份可能更早，以原文为准）
- **论文类型**：方法学（Method）论文，含应用验证
- **领域**：单细胞多组学、计算生物学、深度学习生成模型
- **关键词**：单细胞多组学、RNA velocity、染色质可及性、深度生成模型、多模态
- **DOI/arXiv 号**：10.1093/bioinformatics/btag652
- **代码**：https://github.com/nomuhyooon/mmVelo（MIT 许可证）
- **数据**：10× 胚胎 E18 小鼠脑（10× Genomics 网站）；SHARE-seq 小鼠皮肤（GEO: GSE140203）；10× 人类皮层发育（GEO: GSE162170）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「蛋白质-DNA 互作 × AI/深度学习」方向中的**调控动力学推断**分支。它不直接预测 TF-DNA 结合结构，而是利用 RNA velocity 框架推断染色质可及性（regulome）的动态变化，并进一步推断调控染色质可及性的候选 TF（通过 motif 富集 + 回归）。对 TF-DNA 互作课题的可迁移点在于：(1) 将 RNA 剪接动力学映射到染色质可及性动态的生成建模思路；(2) 用染色质 velocity 识别调控特定 peak 的 TF 的流程；(3) 不确定性分解（on/off-manifold）用于识别谱系分支附近的调控波动。

## 02 一句话总结
mmVelo 是一个基于 mixture-of-experts VAE 的深度生成模型，利用剪接 mRNA 的 RNA velocity 推断细胞状态转移，并将该转移映射到染色质可及性空间，从而在单 peak 分辨率下估计染色质 velocity，并进一步推断调控这些动态变化的候选转录因子。

## 03 研究问题
- **具体问题**：单细胞多组学数据（如 RNA + 染色质可及性）是静态快照，无法直接观测跨模态协调的动态变化。RNA velocity 只能推断转录组动态，无法推广到染色质可及性等非 RNA 模态。
- **为什么重要**：基因表达调控是动态过程，染色质可及性的时序变化（如增强子先开放、启动子后开放、最后基因表达）是理解谱系决定和 TF 调控机制的关键。缺乏跨模态动态推断工具限制了调控机制的解析。
- **现有方法不足**：
  - 轨迹推断（trajectory inference）需要先验方向性，且无法捕捉一维时间线之外的正交变化。
  - RNA velocity 仅适用于有剪接动力学模型的 RNA 模态。
  - MultiVelo 虽扩展了染色质动态，但在基因水平聚合 peak，无法达到单 peak 分辨率。
  - 现有跨模态预测方法（如 scMM、MultiVI）只能预测 profile，不能预测动态（velocity）。
- **精确的 "Can ... ?" 问题**：Can we infer cell state-dependent chromatin accessibility dynamics (chromatin velocity) at single-peak resolution from single-cell multiomics data, and use it to identify regulatory TFs and predict missing-modality dynamics from single-modality data?

## 04 背景与发展脉络
（注：以下脉络基于本文 Introduction 的叙述，标注为「仅本文框架」；未逐一核验外部文献。）
- **阶段 1：静态调控关系推断**。单细胞多组学技术（SNARE-seq、Paired-seq、SHARE-seq、10× Multiome）可同时测量 RNA 和染色质可及性，但只能提供静态快照。调控网络推断依赖时间序列或常微分方程，不适用于静态单细胞数据。
- **阶段 2：轨迹推断**。基于细胞相似性构建图并分配伪时间（如 Monocle、Slingshot 等），但需要已知方向性，且无法捕捉一维时间线之外的正交状态变化。
- **阶段 3：RNA velocity**。利用剪接动力学（unspliced/spliced mRNA 比例）推断基因表达的时间导数，无需先验方向性（La Manno et al. 2018; Bergen et al. 2020）。局限：仅适用于 RNA，无法推广到其他模态。
- **阶段 4：多模态动态扩展**。MultiVelo 将染色质可及性纳入微分方程模型，但 peak 在基因水平聚合，丢失单 peak 分辨率。Chromatin velocity（Tedesco et al. 2022）需专门测量技术（heterochromatin/euchromatin 区分），通用性受限。
- **本文主张的位置**：在 mixture-of-experts VAE 框架下，用 RNA velocity 驱动细胞状态转移，再解码到染色质空间，实现单 peak 分辨率的染色质 velocity，并支持缺失模态推断和 TF 调控关系推断。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单细胞数据是静态快照 | 无法直接观测跨模态动态变化 | 测序实验破坏细胞，只能测量一次 | Introduction 第 1 段 |
| RNA velocity 无法推广到非 RNA 模态 | 染色质可及性动态无法用剪接动力学建模 | RNA velocity 依赖 unspliced/spliced mRNA 的剪接动力学模型，其他模态无对应物 | Introduction 第 2 段 |
| 现有染色质动态方法分辨率不足 | MultiVelo 在基因水平聚合 peak，无法区分同一基因内不同调控元件的动态差异 | 基因水平聚合丢失 peak 特异性信息 | Introduction 第 3 段；Results 3.3 单 peak 分析 |
| 染色质 velocity 需要专门测量技术 | Chromatin velocity 需 heterochromatin/euchromatin 区分，通用性受限 | 依赖特殊实验协议，不适用于常规 10× Multiome 数据 | Introduction 第 3 段 |
| 单模态数据无法推断缺失模态动态 | 只有 scRNA-seq 或 scATAC-seq 时无法获得另一模态的 velocity | 缺乏跨模态桥接机制 | Results 3.7；Methods 2.11 |

## 06 核心思想
1. **表面方法**：构建 mixture-of-experts VAE，输入多模态数据（染色质可及性、unspliced/spliced mRNA），推断共享细胞状态表示；用 RNA velocity 约束细胞状态转移方向；将转移向量解码到各模态空间，得到各模态的 velocity。
2. **核心洞察**：
   - 细胞状态转移（latent dynamics）由 RNA velocity 驱动，但转移向量本身定义在共享低维流形上，因此可以投影到任何模态空间。
   - 通过 fine-tuning 解码器重建平滑后的 profile（kNN 平滑），缓解单细胞染色质数据的稀疏性和噪声。
   - 将染色质 velocity 用于 peak 聚类、motif 富集、TF 表达回归，从而推断调控特定 peak 的候选 TF。
3. **可能的普适教训 [Analysis]**：
   - 跨模态动态推断的关键不是为每个模态建立独立动力学模型，而是建立一个共享状态空间，用可建模的模态（RNA）驱动状态转移，再解码到其他模态。
   - 单 peak 分辨率的重要性：基因水平聚合会掩盖同一基因内不同调控元件的时序差异，这对 TF 调控机制研究至关重要。
   - 不确定性分解（on/off-manifold）为 velocity 估计提供了质量评估维度，可识别谱系分支附近的生物学相关波动。

## 07 方法总览
- **输入**：单细胞多组学数据，包括染色质可及性矩阵（peak × cell）、unspliced mRNA 矩阵、spliced mRNA 矩阵。可选：仅单模态数据（scRNA-seq 或 scATAC-seq）+ 多组学桥接数据。
- **输出**：
  - 每细胞的染色质 velocity（ΔATAC，peak 分辨率）
  - 每细胞的 RNA velocity（Δspliced、Δunspliced）
  - 细胞状态表示（latent z）
  - 推断的 TF-peak 调控关系（通过 motif + 回归）
- **模块**：
  1. Mixture-of-experts VAE：各模态独立 encoder → 共享 latent z（高斯混合）；各模态 decoder 重建观测。
  2. 动力学推断模块：给定 z，用 encoder 推断转移向量 d 的分布 q(d|z)；d 的方向由 RNA velocity 约束。
  3. 平滑 profile 重建：fine-tuning 阶段，decoder 预测 kNN 平滑后的 profile（k=50），而非原始稀疏计数。
  4. 染色质 velocity 计算：将 z 和 z+ρd 分别解码到染色质空间，取差值。
  5. 下游分析：peak 聚类（基于染色质 velocity 余弦相似度）、motif 富集（pycisTarget）、TF 表达回归（GRNBoost2 + 置换检验）。
- **训练**：
  - 优化目标：ELBO（证据下界）+ 动力学一致性项（RNA velocity 约束）。
  - 优化器：AdamW，学习率 0.0001（推断阶段）/ 0.01（fine-tuning 阶段）。
  - 批次大小 128，最多 500 epochs，早停（30 epochs 无改善）。
  - 训练分阶段：先训练 VAE 重建，再 fine-tuning decoder 重建平滑 profile，最后训练动力学模块。
- **反馈回路**：动力学模块的 encoder 以 z 为输入，输出 d 的分布；d 通过 decoder 映射到 RNA 空间，与观测的 RNA velocity 计算似然，形成闭环。
- **假设**：
  - 细胞状态转移在共享 latent 流形上是平滑的、局部的（ρ=0.01 小步长）。
  - RNA velocity 提供了细胞状态转移方向的可靠估计。
  - 平滑 profile 保留了生物学信号，同时去除了技术噪声。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Mixture-of-experts VAE encoder | 从各模态观测推断共享细胞状态 z 的分布 | 多模态数据异构性强，单模态 encoder 无法统一表示；MoE 允许各模态对 z 的贡献不同 | 输入：a_n, s_n, u_n；输出：q(z_n|a_n,s_n,u_n) 的均值和方差 | Methods 2.2；Fig 1 | 预期：无法整合多模态信息，细胞状态估计受稀疏模态主导 [预期效应] |
| 各模态 decoder（a/s/u） | 将 z 映射回各模态观测空间 | 需要将 latent 状态解码为可解释的生物学变量 | 输入：z；输出：各模态的均值/零膨胀概率 | Methods 2.2 | 预期：无法重建观测，ELBO 无法优化 [预期效应] |
| 平滑 profile 重建（fine-tuning） | 预测 kNN 平滑后的 profile 而非原始计数 | 单细胞染色质数据极度稀疏，直接重建原始计数噪声过大 | 输入：z；输出：平滑后的 profile 均值 | Methods 2.3；Fig S5 消融 | 实测：无平滑时 velocity 场出现 terminal 区域回流（Fig S5b,d），平滑提升 VCS |
| 动力学 encoder q(d|z) | 推断细胞状态转移向量 d | 需要估计 latent 空间中的速度场 | 输入：z；输出：d 的分布（高斯） | Methods 2.4 | 预期：无法估计速度场，无法计算任何模态的 velocity [预期效应] |
| RNA velocity 似然约束 | 将 d 映射到 RNA 空间并与观测 velocity 比较 | 提供动力学学习的监督信号 | 输入：z, d；输出：ds/dt 的预测分布（von Mises-Fisher） | Methods 2.4 | 预期：动力学学习无监督信号，d 估计无生物学意义 [预期效应] |
| 染色质 velocity 计算 | 将 z 和 z+ρd 解码到染色质空间并取差 | 核心输出，用于下游分析 | 输入：z, d；输出：ΔATAC（peak 分辨率） | Methods 2.5；Results 3.3 | 预期：无法获得 peak 分辨率动态 [预期效应] |
| 峰值聚类 + motif 富集 + TF 回归 | 从染色质 velocity 推断调控 TF | 将动态信息转化为可验证的调控关系 | 输入：ΔATAC、peak 序列、TF 表达；输出：TF-peak 调控关系 | Methods 2.11；Results 3.6 | 预期：无法从动态数据中识别调控因子 [预期效应] |
| 缺失模态推断 | 用单模态数据 + 预训练模型推断缺失模态 velocity | 扩展适用性到单模态数据 | 输入：单模态数据；输出：缺失模态的 profile 和 velocity | Results 3.7；Methods 2.12 | 预期：无法从单模态数据推断跨模态动态 [预期效应] |

## 09 关键公式符号
（注：原文公式以文字描述为主，以下为可辨识的关键符号与含义；具体公式编号未在提供材料中明确标注。）
- **生成模型**：a_n ~ ZeroInflatedNegativeBinomial(mean = l_n^a · exp(μ_l^a + σ_l^{a,2}/2) · C_p^a · f_p^a(z_n), dispersion = θ_p^a, zero-inflation = g_p^a(z_n))
  - a_n：细胞 n 的染色质可及性向量
  - z_n：细胞状态 latent 变量
  - l_n^a：染色质模态的 scaling factor（log-normal 分布）
  - μ_l^a, σ_l^{a,2}：scaling factor 对数正态分布的均值/方差（经验估计）
  - C_p^a：peak p 的平均可及性 scale
  - f_p^a：decoder 神经网络，输出平均可及性
  - θ_p^a：peak 特异性 inverse dispersion
  - g_p^a：零膨胀概率（decoder 输出）
- **RNA 模态**：s_n ~ NegativeBinomial(mean = l_n^r · exp(μ_l^r + σ_l^{r,2}/2) · C_g^s · f_g^s(z_n), dispersion = θ_g^s)；u_n 类似
  - s_n, u_n：spliced/unspliced mRNA 计数
  - l_n^r：RNA 模态 scaling factor
  - C_g^s, C_g^u：基因 g 的平均表达 scale
  - f_g^s, f_g^u：decoder 神经网络
  - θ_g^s, θ_g^u：基因特异性 inverse dispersion
- **动力学模型**：d(s_n)/dt = β ⊙ f_w^s(z_n) − γ ⊙ f_w^s(z_n)（RNA velocity 的生成式定义）
  - β, γ：剪接/降解速率向量（可学习参数）
  - ⊙：Hadamard 积
  - f_w^s(z_n)：decoder 输出的 spliced mRNA 平均表达
- **转移向量**：z_{n+ρ} = z_n + ρ · d_n，ρ = 0.01
  - d_n：latent 空间中的细胞状态转移向量
- **变分推断**：ELBO = E_q[log p(a,s,u|z,l)] − KL(q(z,l|a,s,u) || p(z,l)) + 动力学项
  - 动力学项：q(d|z) 与 RNA velocity 观测的似然
- **VCS（vector consistency score）**：VCS = (1/|C_t|) Σ_{c∈C_t} cos(v_c, mean_{c'∈C_t}(v_{c'}))，用于评估 velocity 场与伪时间的一致性

## 10 实验设计与证据链
- **数据集**：
  1. 10× 胚胎 E18 小鼠脑多组学数据（RNA + ATAC），来源：10× Genomics 网站
  2. SHARE-seq 小鼠皮肤（毛囊）数据，来源：GEO GSE140203
  3. 10× 人类皮层发育数据（PCW21），来源：GEO GSE162170
- **指标**：VCS（vector consistency score）；velocity 场与已知谱系方向的视觉一致性（streamline plots）；TF-peak 调控关系的富集显著性（置换检验）
- **基线/对比方法**：scVelo（RNA velocity）、MultiVelo（基因水平染色质 velocity）
- **预算/仪器**：未明确提供（提及使用 Shirokane、TSUBAME3.0、ABCI 超算资源）
- **评测协议**：在毛囊数据中，选取 hair shaft-cuticle/cortex 谱系细胞，用 diffusion pseudotime 分 10 个 bin，计算 VCS 比较各方法

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 消融分析：latent 维度与平滑 | 默认设置（z=10, 平滑）在 VCS 和 streamline 上最优 | z=5/10/30/50 × 有/无平滑，小鼠脑 + 毛囊数据 | z=10+平滑 VCS 最高；无平滑时 terminal 区域出现回流 | 平滑对稳定 velocity 场必要；z=10 平衡拟合与泛化 | 未系统比较其他平滑参数（k 值） | Results 3.2；Fig S5 |
| 小鼠脑染色质 velocity 重建 | mmVelo 能恢复已知皮层发育轨迹的染色质动态 | 与已知谱系（放射状胶质→神经元/胶质）对比 | velocity 场与已知轨迹一致；Neurod2 增强子先于启动子开放 | 单 peak 分辨率染色质 velocity 可捕获调控时序 | 未与 ground truth 动态直接定量比较 | Results 3.3；Fig 2 |
| 毛囊数据基准测试 | mmVelo 的染色质/RNA velocity 优于现有方法 | 与 scVelo、MultiVelo 在 hair shaft-cuticle/cortex 谱系比较 VCS | mmVelo VCS 高于 scVelo 和 MultiVelo | mmVelo 在 velocity 准确性上优于基线 | VCS 仅衡量与伪时间一致性，非真实动态 | Results 3.4；Fig S3j-m |
| motif velocity 分析 | 染色质 velocity 可转化为 TF motif 动态 | 毛囊数据，Hoxc13、Gata3 等已知谱系 TF | motif velocity 捕获谱系特异性动态，与基因表达同步 | 染色质 velocity 可用于推断 TF 调控动态 | 未验证 motif velocity 与 ChIP-seq 等直接实验的一致性 | Results 3.4；Fig 3 |
| 不确定性分解 | on/off-manifold 分量具有不同生物学意义 | 毛囊数据，沿伪时间分析 | off-manifold 在 terminal 区域升高；on-manifold 在谱系分支附近升高 | 不确定性分解可识别谱系决策相关波动 | 未与实验扰动验证因果关系 | Results 3.5；Fig 4 |
| 缺失模态推断 | 从单模态数据推断缺失模态 velocity | 人类皮层发育数据，模拟缺失 RNA 或 ATAC | 推断的 velocity 与已知方向一致 | 模型可桥接单模态数据到跨模态动态 | 仅验证了同一发育阶段，未测试跨数据集泛化 | Results 3.7；Fig 6 |
| TF-peak 调控关系推断 | 染色质 velocity 可识别调控 peak 的 TF | 毛囊数据，GRNBoost2 + 置换检验 | 推断的 TF-peak 关系在已知调控区域（如 Lef1）富集 | 染色质 velocity 可增强调控关系推断 | 未与 CRISPR 等实验验证 | Results 3.6；Fig 5 |

## 11 结论正确解读
- **任务范围**：mmVelo 适用于有剪接动力学信息的单细胞多组学数据（RNA + ATAC），推断染色质可及性的动态变化。它不预测 TF 的结合结构或亲和力，而是从动态共变模式中推断调控关系。
- **oracle/真值输入**：RNA velocity 的观测值（由 splicing kinetics 模型计算）作为动力学学习的监督信号；kNN 平滑后的 profile 作为重建目标。
- **端到端状态**：模型端到端可训练，但依赖预计算的 RNA velocity 作为监督信号，并非完全自监督。
- **算力成本**：未提供具体训练时间或硬件需求；提及使用超算资源，暗示计算成本较高。
- **历史数据依赖**：依赖静态快照数据，无时间序列；动力学完全由 RNA velocity 推断。
- **模型依赖**：依赖 VAE 结构、MoE 组合策略、平滑参数（k=50）、转移步长（ρ=0.01）等超参数选择。
- **最难情形**：稀疏的染色质数据、低丰度 peak、谱系末端（terminal）区域（off-manifold 不稳定）、跨数据集泛化。
- **群体/领域边界**：验证限于小鼠脑、小鼠毛囊、人类皮层发育三个系统；未测试疾病状态、体外分化等场景。
- **不确定性**：velocity 估计存在不确定性，作者通过 on/off-manifold 分解部分刻画，但未提供置信区间或贝叶斯不确定性量化。
- **有边界的复述**：mmVelo 在测试的三个发育系统中，能够从多组学数据推断出与已知谱系方向一致的染色质可及性动态，其单 peak 分辨率优于基因水平聚合方法，并能从动态模式中识别候选调控 TF；但该方法依赖 RNA velocity 的可靠性，在 RNA velocity 不适用的系统中可能失效。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 依赖 RNA velocity 的适用性 | 在 RNA velocity 难以估计方向性的生物系统中，mmVelo 无法应用 | 结合其他动力学模型（如 MultiVelo、scKINETICS） | Discussion 4.1 |
| 平滑可能模糊生物学变异 | 使用 kNN 平滑处理稀疏性，可能丢失稀有细胞类型或瞬时状态的信息 | 引入更精细的稀疏数据处理方法 | Discussion 4.1（隐含） |
| 单一动力学速率假设 | 假设剪接/降解速率为常数（或可学习但全局共享），可能不适用于速率变化的系统 | 扩展为可变速率模型 | Discussion 4.1（隐含） |
| 未建模 count 分布 | 使用平滑 profile 而非原始 count 建模，可能损失定量信息 | 引入 count 模型（如 ZINB）到动力学推断 | Discussion 4.1（隐含） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| VCS 仅衡量与伪时间的一致性 | VCS 高可能反映的是平滑造成的假象，而非真实生物学动态；伪时间本身由表达相似性推断，存在循环论证风险 | 若 VCS 主要反映平滑效应，则方法优势可能被高估 | 在无平滑条件下比较 VCS；使用独立的时间信息（如标记基因时序、实验时间点）验证 | Results 3.2；Methods 2.7 |
| 与 scVelo/MultiVelo 的比较条件可能不公平 | mmVelo 使用了多模态信息，而 scVelo 仅用 RNA；MultiVelo 的输入处理可能不同 | 公平基准需要控制输入信息量 | 在仅 RNA 输入条件下比较 mmVelo 与 scVelo；在相同 peak 集上比较 MultiVelo | Results 3.4；Fig S3 |
| TF-peak 调控关系推断缺乏直接验证 | 仅通过 motif 富集和回归推断，未与 ChIP-seq、ATAC-seq 扰动实验等直接证据对比 | 推断的调控关系可能是间接相关而非因果 | 在已知调控关系的位点（如 Lef1）进行 ChIP-seq 验证；CRISPR 干扰实验 | Results 3.6；Fig 5 |
| 缺失模态推断的验证仅在同一发育阶段 | 未测试跨数据集、跨物种或跨发育阶段的泛化能力 | 实际应用中数据常来自不同批次/条件，泛化性决定实用性 | 在独立数据集上测试，评估批次效应影响 | Results 3.7；Fig 6 |
| 不确定性分解的解释缺乏实验支持 | on/off-manifold 分量的生物学解释（谱系分支 vs 末端不稳定）是事后解释，未与实验表型关联 | 若该分解无生物学意义，则其作为不确定性度量的价值有限 | 在已知谱系决策时间点检测 on-manifold 波动是否先于命运决定 | Results 3.5；Fig 4 |
| 未报告超参数敏感性 | 除 latent 维度和平滑外，其他超参数（如 ρ、k、网络结构）的影响未系统评估 | 方法稳健性未知，可能对特定数据集过拟合 | 在多个数据集上系统扫描超参数 | Methods 2.6 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **跨模态动力学推断的生成建模框架**：用可建模模态（RNA splicing kinetics）驱动共享 latent 空间的转移，再解码到其他模态（染色质）。可迁移到 TF-DNA 互作：用 TF 表达动力学驱动染色质可及性动态推断，或反之。
2. **单 peak 分辨率的重要性**：基因水平聚合会掩盖同一基因内不同调控元件的时序差异。在 TF-DNA 互作研究中，应追求 peak/位点级别的分辨率，而非基因级别。
3. **平滑策略对 velocity 场稳定性的影响**：kNN 平滑显著改善 velocity 场质量（消除 terminal 回流），但可能模糊稀有状态。在单细胞 ATAC 数据分析中，平滑参数选择需权衡。
4. **不确定性分解（on/off-manifold）作为质量指标**：将 velocity 不确定性分解为流形内（生物学相关）和流形外（技术不稳定）分量，可识别谱系分支附近的调控波动。可迁移到 TF 结合动力学预测中的置信度评估。
5. **从动态模式推断调控关系的流程**：peak 聚类（基于 velocity 相似度）→ motif 富集 → TF 表达回归 → 置换检验。该流程可迁移到 TF-DNA 互作预测中，利用动态共变模式补充静态结合数据。
6. **缺失模态推断的桥接策略**：用多组学数据预训练共享 latent 空间，再用单模态数据推断缺失模态的 profile 和 velocity。可迁移到仅有一维数据（如 RNA）时推断另一维（如染色质）动态的场景。
7. **MoE VAE 处理异构模态**：不同模态用独立 encoder，通过 mixture-of-experts 组合，避免单一 encoder 被高维模态主导。可迁移到整合 TF 结合、表达、染色质可及性等多源异构数据。

## 15 与已有知识连接
- **RNA velocity 基础**：La Manno et al. (2018) 提出 RNA velocity 概念；Bergen et al. (2020) 的 scVelo 扩展了动态模型。mmVelo 在此基础上将 velocity 从 RNA 推广到染色质。
- **多模态 VAE**：与 scMM（Minoura et al. 2021）、MultiVI（Ashuach et al. 2023）同属多模态生成模型家族，但 mmVelo 增加了动力学推断能力。
- **染色质动态方法**：MultiVelo（Li et al. 2023）是直接前身，mmVelo 通过 MoE VAE 和单 peak 分辨率改进之。Chromatin velocity（Tedesco et al. 2022）需专门实验，mmVelo 适用于常规 10× Multiome 数据。
- **调控网络推断**：与 SCENIC+（Bravo González-Blas et al. 2023）互补——SCENIC+ 从静态共变推断调控子，mmVelo 从动态共变推断调控关系。
- **TF-DNA 互作课题的连接点**：
  - mmVelo 的染色质 velocity 可作为 TF 结合动态的代理指标，补充 ChIP-seq 等静态结合数据。
  - 其 TF-peak 调控推断流程可迁移到 TF 结合位点预测中，利用动态信息增强静态序列特征。
  - 不确定性分解思想可迁移到 TF-DNA 结合预测的置信度校准中。
  - 缺失模态推断策略可迁移到仅有一维数据时推断另一维动态的场景（如从 RNA 推断染色质状态变化）。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF-velocity：基于 TF 表达动力学推断 TF-DNA 结合动态的生成模型
   - **来源局限/观察**：mmVelo 用 RNA velocity 驱动染色质动态推断，但未显式建模 TF 蛋白活性；TF 的 DNA 结合亲和力受翻译后修饰、竞争性结合等影响，mRNA 丰度只是代理。
   - **核心假设**：TF 的染色质结合动态可由其 mRNA 剪接动力学 + 靶 peak 可及性共变推断，且结合动态先于靶基因表达变化。
   - **增量**：将 mmVelo 框架扩展到 TF 结合事件（通过 motif 匹配的 peak 集合），引入 TF 特异性先验（如 motif 亲和力、ChIP-seq 峰强度）。
   - **初步方法**：在 mmVelo 的 latent 空间中增加 TF 活性节点，用 TF 的 unspliced/spliced mRNA 驱动其靶 peak 的染色质 velocity；用已知 ChIP-seq 数据作为弱监督。
   - **验证方式**：在已有 ChIP-seq 时间序列的数据集（如 ESC 分化）中，比较推断的 TF 结合动态与实验测量。
   - **创新状态**：unverified

2. **候选名称**：单 peak 分辨率染色质 velocity 的贝叶斯不确定性量化
   - **来源局限/观察**：mmVelo 的 on/off-manifold 分解是启发式的，未提供严格的不确定性区间；velocity 估计在稀疏 peak 上可能高度不确定。
   - **核心假设**：通过贝叶斯变分推断（如 MC-dropout 或 ensemble）可量化每 peak 的 velocity 不确定性，且不确定性在谱系决策点附近具有生物学意义。
   - **增量**：将 mmVelo 的确定性 velocity 估计替换为后验分布，提供 peak 级别的置信区间。
   - **初步方法**：在 mmVelo 的 decoder 中引入 dropout 或深度 ensemble，对每 peak 的 ΔATAC 估计多次采样，计算方差；将不确定性作为权重引入下游 TF-peak 推断。
   - **验证方式**：在已知调控元件的数据集上，检查高不确定性 peak 是否富集于已知的谱系决策相关区域。
   - **创新状态**：unverified

3. **候选名称**：跨物种 TF-DNA 动态调控的迁移学习
   - **来源局限/观察**：mmVelo 的缺失模态推断依赖同一数据集的桥接；跨物种或跨组织时，peak 集和 TF 表达程序差异大，直接迁移可能失败。
   - **核心假设**：TF 的调控逻辑（哪些 TF 控制哪些 peak 的动态）在进化上保守，可通过迁移学习从模式生物（小鼠）迁移到人类。
   - **增量**：在 mmVelo 的 latent 空间中引入物种/组织条件向量，用对抗训练对齐不同数据集的 latent 分布。
   - **初步方法**：用小鼠毛囊数据预训练 mmVelo，再用少量人类皮肤数据 fine-tune，评估人类毛囊的染色质 velocity 推断质量。
   - **验证方式**：比较迁移模型与从头训练模型在人类数据上的 VCS 和 TF-peak 推断准确率。
   - **创新状态**：unverified

4. **候选名称**：染色质 velocity 引导的 TF 结合位点预测（cis-regulatory 动态建模）
   - **来源局限/观察**：现有 TF 结合位点预测主要基于静态序列特征和染色质可及性，未利用动态信息；mmVelo 的染色质 velocity 提供了 peak 的时序变化信息。
   - **核心假设**：TF 结合位点的可及性动态模式（开放→关闭、关闭→开放）可区分功能性结合与非功能性结合。
   - **增量**：将 mmVelo 的染色质 velocity 作为特征，输入到 TF 结合位点预测模型（如基于 CNN 或 Transformer 的模型），与静态特征联合建模。
   - **初步方法**：在 ENCODE 数据上，为每个 peak 计算染色质 velocity 特征，与 DNA 序列特征拼接，训练 TF 结合分类器。
   - **验证方式**：与仅用静态特征的模型比较 AUC；在 ChIP-seq 验证的位点上检查动态特征的重要性。
   - **创新状态**：unverified

5. **候选名称**：多模态 velocity 一致性约束的联合调控网络推断
   - **来源局限/观察**：mmVelo 分别估计各模态的 velocity，但未显式约束跨模态 velocity 的一致性（如染色质开放应先于基因表达）。
   - **核心假设**：跨模态 velocity 的时序一致性（染色质→RNA→蛋白）可提供额外的正则化信号，改善调控网络推断。
   - **增量**：在 mmVelo 的目标函数中增加跨模态时序一致性损失，强制染色质 velocity 与 RNA velocity 的时序关系符合生物学预期。
   - **初步方法**：在 latent 空间中定义跨模态转移向量的夹角或时序顺序损失，与 ELBO 联合优化。
   - **验证方式**：在已知时序关系的数据集（如 ESC 分化）中，检查推断的跨模态时序关系是否与已知调控逻辑一致。
   - **创新状态**：unverified