## 01 基本信息

- **标题**：Benchmarking and building DNA binding affinity models using allele-specific and allele-agnostic transcription factor binding data
- **作者**：Li, Xiaoting; Melo, Lucas A N; Bussemaker, Harmen J
- **单位**：未提供（根据作者信息推测为 Columbia University，但原文未明确标注）
- **期刊/平台**：Genome Biology
- **年份**：2024-11-04
- **论文类型**：方法学/基准测试研究（含新软件工具）
- **领域**：计算生物学；转录因子-DNA结合机制；机器学习
- **关键词**：Allele-specific binding (ASB)、ChIP-seq、转录因子、DNA结合亲和力模型、PyProBound、beta-binomial
- **DOI/arXiv 号**：10.1186/s13059-024-03424-2
- **代码**：PyProBound（未提供具体 URL，原文提及为对原 Java 版 ProBound 的 reimplementation）
- **数据**：AlleleDB 数据库（CTCF、EBF1、PU.1 的 ASB 数据）；ENCODE ChIP-seq（ENCLB048DBS、ENCLB581JXH）；SRA ChIP-exo（SRR6736394、SRR6736387）和 CUT&Tag（SRR8754587）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦 TF–DNA 结合机制，提出基于 beta-binomial 的 ASB 似然函数用于基准测试序列-亲和力模型，并开发 PyProBound 从等位基因非特异性（allele-agnostic）的 ChIP-seq/ChIP-exo/CUT&Tag 数据中从头推断 TF 结合模型。属于「AI/机器学习 × TF–DNA 结合机制」方向，核心贡献在于：(1) 提供无需单变异显著性即可聚合全基因组证据的模型评估框架；(2) 显式建模 DNA 片段化偏倚以改进 ChIP-seq 训练。

## 02 一句话总结

本文提出基于 beta-binomial 分布的全基因组等位基因特异性似然函数，用于定量评估 TF–DNA 结合亲和力模型预测等位基因不平衡的能力，并开发 PyProBound 框架从 ChIP-seq/ChIP-exo/CUT&Tag 数据中直接推断结合模型，显式建模 DNA 片段化偏倚后显著提升模型质量。

## 03 研究问题

- **具体问题**：如何在不依赖单变异统计显著性的前提下，定量评估和构建 TF–DNA 结合亲和力模型，使其能够准确预测等位基因特异性结合（ASB）？
- **为什么重要**：非编码区遗传变异通过改变 TF 结合影响基因调控，是 GWAS 信号解释的关键。但 ChIP-seq 在单个变异位点的覆盖度通常不足以检测 ASB，限制了基于序列的变异效应预测。
- **现有方法不足**：(1) 传统 ASB 分析需要逐变异统计检验，统计功效低；(2) 体外（in vitro）模型（如 SELEX 衍生模型）在体内（in vivo）预测能力有限；(3) 直接从 ChIP-seq 训练模型时未考虑 DNA 片段化偏倚和片段长度异质性。
- **精确研究问题**：Can a genome-wide beta-binomial likelihood function that aggregates allele-specific ChIP-seq counts across all heterozygous variants provide a statistically robust and unbiased metric for benchmarking and building TF–DNA binding affinity models?

## 04 背景与发展脉络

**注：以下脉络基于本文框架及文中引用，部分经外部核验（标注）。**

1. **阶段一：体外高通量结合实验（SELEX 等）**（经外部核验）
   - 代表方法：HT-SELEX [12]、SMiLE-seq [13]
   - 优点：可大规模表征纯化 TF 的内在 DNA 结合偏好
   - 局限：缺乏体内染色质环境（共因子、可及性）信息

2. **阶段二：体内 ChIP-seq 峰调用与 motif 扫描**（经外部核验）
   - 代表方法：MACS 峰调用 + JASPAR/HOCOMOCO motif 扫描
   - 优点：反映体内结合环境
   - 局限：峰调用丢失定量信息；motif 数据库质量参差

3. **阶段三：等位基因特异性结合（ASB）分析**（经外部核验）
   - 代表方法：AlleleDB [5]、ADASTRA [7]
   - 优点：在同一细胞内比较两个等位基因，控制环境差异
   - 局限：需要高覆盖度；单变异统计检验功效低

4. **阶段四：生物物理可解释的机器学习模型**（本文位置）
   - 代表方法：ProBound [18]（原 Java 实现）
   - 本文贡献：PyProBound reimplementation + ASB 似然基准框架
   - 关键创新：显式建模 DNA 片段化偏倚；利用全基因组等位基因计数聚合证据

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单变异 ASB 检测统计功效低 | 仅少数变异达到 ASB 统计显著性（CTCF 仅 2231 个 ASB 变异） | ChIP-seq 覆盖度有限，beta-binomial 检验需要足够 reads | Results 节；Methods "Allele-specific TF binding data" |
| 体外模型预测体内结合不准确 | 基于 SELEX 的模型在预测 ChIP-seq 等位基因不平衡时表现有限 | 体内结合受染色质可及性、共因子等影响 | Results 图 2；Discussion 节 |
| ChIP-seq 训练受 DNA 片段化偏倚干扰 | 模型在片段末端出现强烈位置偏倚 | 超声打断的序列偏好与 TF 结合偏好混淆 | Results 节；Additional file 1: Figure S4A |
| 片段长度异质性限制模型训练 | 原始 ProBound 无法处理变长序列 | Java 实现设计为固定长度输入 | Methods "In vivo binding data analysis with PyProBound" |
| 模型评估缺乏统一基准 | 不同模型难以公平比较 | 缺乏不依赖单变异显著性的全基因组评估指标 | Results 图 3、图 4 |

## 06 核心思想

### 1) 表面方法
- 提出基于 beta-binomial 分布的似然函数，将每个杂合变异位点的等位基因 ChIP-seq 计数建模为预测亲和力比值的函数
- 开发 PyProBound（PyTorch 实现），支持变长序列训练，显式建模 DNA 片段化偏倚
- 在 CTCF、EBF1、PU.1 上系统比较多种来源的模型（体外 SELEX、体内 ChIP-seq/ChIP-exo/CUT&Tag、数据库 motif）

### 2) 核心洞察
- **等位基因计数是天然的"配对实验"**：同一变异位点的两个等位基因共享相同的染色质环境，因此等位基因计数比值直接反映 TF 结合亲和力差异，无需控制环境变量
- **聚合优于逐点检验**：通过全基因组似然函数聚合所有变异的证据，即使单个变异不显著，整体信号仍可检测
- **片段化偏倚是 ChIP-seq 训练的主要混淆因素**：显式建模片段化序列偏好后，模型性能显著提升，且位置偏倚消失
- **体内模型优于体外模型**：在预测 ASB 方面，从体内数据训练的模型（尤其是 CUT&Tag）优于 SELEX 衍生模型

### 3) 可能的普适教训 [Analysis]
- 在生物序列模型中，**技术性偏倚（如片段化）与生物学信号的混淆**是普遍问题，显式建模技术偏倚可能比增加模型复杂度更有效
- **利用自然实验设计（如等位基因配对）** 可以规避许多混杂因素，这一思路可迁移到其他基因组功能预测任务
- 模型评估指标应与下游应用对齐：如果目标是预测变异效应，评估指标应基于变异效应数据而非仅拟合训练分布

## 07 方法总览

- **输入**：
  - 等位基因特异性 ChIP-seq 计数（来自 AlleleDB，含参考/替代等位基因 reads 数）
  - 等位基因非特异性 ChIP-seq/ChIP-exo/CUT&Tag 片段序列（来自 ENCODE/SRA）
  - 外部 TF 结合模型（MotifCentral、JASPAR、HOCOMOCO）
- **输出**：
  - 各模型的 ASB 似然值（用于基准测试）
  - PyProBound 训练的 TF 结合模型（含结合位点能量谱）
- **核心模块**：
  1. **ASB 似然函数**：beta-binomial 模型，以预测亲和力比值作为等位基因计数的概率
  2. **PyProBound 训练框架**：Poisson 损失 + L-BFGS 优化，支持变长序列
  3. **片段化偏倚建模**：在片段两端各 10bp 训练独立的序列偏好模型
  4. **滑动窗口亲和力求和**：对每个变异位点，在所有可能的结合偏移上求和亲和力
- **训练**：L-BFGS 优化 Poisson 损失；L2 正则化（λ=10⁻⁶ 用于体内模型，λ=10⁻⁴ 用于 ASB 衍生模型）；指数屏障正则化防止数值错误
- **反馈回路**：ASB 似然函数既用于评估外部模型，也用于从头训练（de novo motif discovery），形成"评估-训练-再评估"闭环
- **文字流程**：
  1. 从 AlleleDB 获取等位基因 ChIP-seq 计数
  2. 对每个变异，提取两侧各 29bp 的参考/替代序列
  3. 用候选模型计算每个等位基因的滑动窗口亲和力总和
  4. 将亲和力比值代入 beta-binomial 似然函数，计算全基因组对数似然
  5. 对 PyProBound 训练：从 ChIP-seq/ChIP-exo/CUT&Tag 片段直接优化 Poisson 损失，同时拟合结合模型和片段化偏倚模型
  6. 比较各模型的对数似然（bootstrap 评估显著性）

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ASB 似然函数（beta-binomial） | 聚合全基因组等位基因计数，量化模型预测能力 | 单变异检验功效低，需要全局指标 | 输入：等位基因计数、预测亲和力比值；输出：对数似然 | Results 图 3：bootstrap 分布显示模型显著优于对照 | 预期影响：失去统一的模型比较基准 [Analysis] |
| PyProBound 训练框架 | 从体内数据直接推断 TF 结合模型 | 体外模型预测体内结合不准确 | 输入：片段序列+计数；输出：结合能量谱 | Results 图 4：体内模型优于体外模型 | 预期影响：无法利用体内数据训练模型 [Analysis] |
| 片段化偏倚建模 | 显式建模 DNA 片段化序列偏好 | 片段化偏倚与 TF 结合偏好混淆 | 输入：片段两端 10bp 序列；输出：偏倚能量谱 | Additional file 1: Figure S4A→S4C：位置偏倚消失 | 实测消融效应：模型在片段末端出现强偏倚，预测性能下降 |
| 滑动窗口亲和力求和 | 计算变异位点周围所有可能结合偏移的总亲和力 | TF 可在多个偏移结合，需累加效应 | 输入：变异序列+模型；输出：总亲和力 | Methods 节公式 (1) | 预期影响：忽略多偏移结合贡献 [Analysis] |
| Bootstrap 评估 | 构建对数似然的采样分布 | 需要统计显著性判断 | 输入：变异重采样；输出：似然分布 | Results 图 3、图 4 | 预期影响：无法判断模型间差异显著性 [Analysis] |
| 序列延伸（29bp flanking） | 为每个变异构建足够长的评估序列 | 需容纳不同大小的结合模型 | 输入：变异坐标；输出：参考/替代序列 | Methods "Sequence-based prediction" 节 | 预期影响：短序列可能遗漏远端结合位点 [Analysis] |

## 09 关键公式符号

**公式 1：滑动窗口亲和力求和**
$$K_a(S) = \sum_x K_a(S_x) = \sum_x \exp\left(-\frac{\Delta\Delta G(S_x)}{RT}\right)$$

- $K_a(S)$：序列 S 的总相对结合常数
- $S_x$：在偏移 x 处、与结合模型对齐的序列窗口
- $\Delta\Delta G(S_x) = \Delta G(S_x) - \Delta G(S_{ref})$：相对结合自由能惩罚
- $R$：气体常数；$T$：温度

**公式 2：beta-binomial 模型**
$$Y_i \sim \text{BetaBinomial}(n_i, p_i, \rho)$$

- $Y_i = (Y_i^{ref}, Y_i^{alt})$：变异 i 的参考/替代等位基因 ChIP-seq 计数
- $n_i = Y_i^{ref} + Y_i^{alt}$：总计数
- $p_i$：由预测亲和力比值决定的等位基因概率
- $\rho$：过离散参数（over-dispersion）

**公式 3：Poisson 损失函数（PyProBound 训练）**
$$\log \mathcal{L} = \frac{1}{\sum_{ir} k_{i,r}} \sum_{i,r} \left[ k_{i,r} \log\left(\frac{\eta_r f_{i,r} \sum_{ir'} k_{i,r'}}{\sum_{ir'} \eta_{r'} f_{i,r'}}\right) - k_{i,r} - \log(k_{i,r}!) \right]$$

- $k_{i,r}$：片段 i 在文库 r（对照或结合）中的观测计数
- $f_{i,r}$：预测的片段计数
- $\eta_r$：文库深度调整参数
- 约定 $\eta_{control} f_{i,control} = 1$

**公式 4：PyProBound 完整计数模型**
$$f_{i,bound} = \left(\alpha_{CTCF}^{NS} + \sum_x \omega_{\lfloor x/5 \rfloor} e^{-\Delta\Delta G_{CTCF}(S_x)/RT}\right) \prod_i \left(\alpha_{left,i}^{NS} + e^{-\Delta\Delta G_{left,i}(S_{1:10})/RT}\right)\left(\alpha_{right,i}^{NS} + e^{-\Delta\Delta G_{right,i}(S_{n-9:n})/RT}\right)$$

- $\alpha^{NS}$：非特异性结合参数
- $\omega_{\lfloor x/5 \rfloor}$：每 5 个偏移一组的位置偏倚权重
- $S_{1:10}$、$S_{n-9:n}$：片段两端各 10bp 的序列

## 10 实验设计与证据链

**数据集与资源**：
- AlleleDB 数据库：CTCF（2231 ASB 变异，44422 非 ASB 变异）、EBF1（189 ASB）、PU.1（387 ASB）
- ENCODE ChIP-seq：CTCF，paired-end，accession ENCLB048DBS、ENCLB581JXH
- SRA ChIP-exo：SRR6736394、SRR6736387；CUT&Tag：SRR8754587
- 外部模型：MotifCentral（ProBERT 训练的 SELEX 模型）、JASPAR、HOCOMOCO
- 基因组：GRCh38（hg38）用于 ChIP-exo/CUT&Tag 比对；hg19 用于 AlleleDB 变异注释

**指标**：
- 对数似然（log-likelihood）及 bootstrap 分布
- Pearson R²（模型间参数比较）
- 等位基因偏好一致性（concordance，方向预测准确率）

**评测协议**：
- 对每个变异，计算参考/替代等位基因的预测亲和力比值
- 用 beta-binomial 似然函数聚合所有变异
- Bootstrap 1000 次重采样构建似然分布
- 比较不同模型的似然值及 bootstrap 置信区间

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-------------------|------|
| CTCF ASB 方向预测 | 体外模型能预测等位基因偏好方向 | MotifCentral CTCF 模型 vs 随机 | 62.4% 一致性（binomial p<10⁻¹⁶） | 模型预测显著优于随机 | 远未达到 100%，不能作为可靠的单变异预测器 | Results 图 2 |
| 似然比分层 | 高预测亲和力差异的变异更可能一致 | 按预测亲和力比值分层 | 高比值层一致性更高 | 模型在强效应位点更可靠 | 未给出各层精确数值 | Results 图 2C-E |
| 体内 vs 体外模型 | 体内训练的模型优于体外模型 | PyProBound(ChIP-seq) vs MotifCentral(SELEX) | 体内模型 ASB 似然更高 | 体内数据包含体外数据缺失的信息 | 未明确量化提升幅度 | Results 图 4 |
| 片段化偏倚建模 | 显式建模片段化偏倚提升模型质量 | 含 vs 不含片段化模型 | 含片段化模型似然更高，位置偏倚消失 | 片段化偏倚是重要混淆因素 | 未做消融实验的统计检验 | Results 图 4；Additional file 1: Figure S4 |
| 片段长度处理 | 变长序列训练优于固定长度截断 | PyProBound(变长) vs 截断至 200bp | 变长训练表现更好 | 保留完整片段信息有益 | 未给出具体数值 | Results 节；Additional file 1: Figure S4B |
| de novo motif discovery | ASB 似然可用于从头发现 motif | PyProBound 优化 ASB 似然 vs 标准训练 | 与 MotifCentral 模型高度一致（R²=0.890 for CTCF） | ASB 数据可直接驱动 motif 发现 | 仅验证 3 个 TF；PU.1 需更宽模型 | Results 图 5；Additional file 1: Figure S7 |
| 外部数据库模型比较 | 不同来源模型在 ASB 预测上表现不同 | JASPAR、HOCOMOCO vs MotifCentral vs PyProBound | PyProBound(CUT&Tag) 最优 | 模型来源和质量影响 ASB 预测 | 未系统比较所有 TF | Results 图 4 |

## 11 结论正确解读

- **任务范围**：本文聚焦于 TF–DNA 结合亲和力模型的**评估**与**构建**，而非预测所有非编码变异效应。结论限于 ChIP-seq 可检测的 TF 结合位点。
- **oracle/真值输入**：ASB 标签来自 AlleleDB 的 ChIP-seq 等位基因计数，这些计数本身受测序深度、比对偏差、拷贝数变异等影响。模型评估依赖这些计数的可靠性。
- **端到端状态**：本文方法**不是端到端**的变异效应预测器。它提供的是：(1) 模型评估指标；(2) 模型训练框架。实际变异效应预测仍需结合染色质状态、共因子等信息。
- **算力成本**：PyProBound 基于 PyTorch，支持 GPU 加速，但论文未报告具体训练时间或硬件需求。
- **历史数据依赖**：模型训练依赖 ChIP-seq 数据的质量；AlleleDB 基于 14 个个体的数据，可能不覆盖所有人群变异。
- **模型依赖**：结果高度依赖 ChIP-seq 抗体质量、细胞类型、以及 AlleleDB 的变异注释流程。
- **最难情形**：PU.1 的 ASB 衍生模型与体外模型差异较大，提示某些 TF 的体内结合可能受共因子或染色质状态显著影响，单一结合模型不足以捕捉。
- **有边界的复述**：本文证明，在 ChIP-seq 等位基因计数可获取的前提下，基于 beta-binomial 的全基因组似然函数能够区分不同 TF 结合模型的预测能力；且从体内数据（尤其是 CUT&Tag）训练的模型在预测 ASB 方面优于体外模型。该结论适用于 CTCF、EBF1、PU.1 三个 TF，推广到其他 TF 需谨慎。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 单变异 ASB 检测统计功效低 | 仅少数变异达到 ASB 显著性 | 使用全基因组似然聚合证据 | Results 节；Discussion 节 |
| 未明确考虑共因子效应 | 模型仅捕捉单个 TF 的结合 | 未来可扩展为多 TF 协同模型 | Discussion 节（提及 cooperative interactions） |
| PU.1 体内外模型差异 | ASB 衍生模型发现额外特异性 | 可能反映体内共因子或染色质效应 | Results 节；Additional file 1: Figure S7 |
| 训练数据量有限 | ASB 变异数量少（CTCF 2231 个） | 需要更多等位基因感知的 ChIP-seq 数据 | Methods 节 |
| 未系统评估所有 TF | 仅详细分析 CTCF、EBF1、PU.1 | 未来可扩展到更多 TF | Discussion 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 62.4% 的一致性虽显著但远非完美 | 可能反映模型精度不足，也可能反映 ASB 中非亲和力因素（如染色质可及性差异）的贡献 | 影响对"序列决定结合"这一假设的信心 | 在匹配的染色质可及性数据上分层分析 | Results 图 2 |
| 体内模型优于体外模型 | 可能因为体内模型隐式学习了共因子或染色质信息，而非纯亲和力 | 影响模型的可解释性和迁移性 | 比较模型在体外验证数据上的表现 | Results 图 4 |
| 片段化偏倚建模仅在 ChIP-seq 上验证 | CUT-Tag/ChIP-exo 的片段化机制不同，可能不需要同样处理 | 影响方法普适性 | 在更多数据类型上测试 | Additional file 1: Figure S4 |
| 未报告交叉验证或独立验证集 | 模型可能过拟合训练数据 | 影响结论的稳健性 | 要求作者提供交叉验证结果 | Methods 节未提及 |
| 仅使用 3 个 TF | 不同 TF 的 DNA 结合域结构差异大，结论可能不普适 | 影响方法推广性 | 在更多结构类型的 TF 上测试 | Results 节 |
| beta-binomial 假设过离散参数全局共享 | 不同位点的变异可能具有不同的过离散程度 | 可能引入偏倚 | 允许位点特异性过离散参数 | Methods 节 |
| 未比较深度学习方法 | 仅比较了基于能量的模型和数据库 motif | 无法判断深度学习模型在 ASB 预测上的相对表现 | 加入 DeepBind、BPNet 等模型对比 | Results 图 4 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **等位基因计数作为"配对实验"设计**：在 TF–DNA 结合预测中，利用杂合位点的等位基因计数可以天然控制染色质环境、细胞状态等混杂因素。这一设计可迁移到任何"同一位置两种序列状态"的预测任务。

2. **全基因组似然聚合替代逐点检验**：当单点统计功效不足时，通过似然函数聚合所有位点的证据，可显著提升检测灵敏度。适用于 eQTL、sQTL 等调控变异的效应评估。

3. **显式建模技术偏倚**：ChIP-seq 的 DNA 片段化序列偏好是重要混淆因素。在训练序列-功能模型时，应显式建模实验技术偏倚，而非假设其为噪声。可迁移到 ATAC-seq、Hi-C 等数据的建模。

4. **体内 vs 体外模型的差异信息**：体内模型与体外模型的差异可揭示共因子依赖或染色质状态效应。比较两类模型可作为发现"上下文依赖结合"的系统性方法。

5. **滑动窗口亲和力求和**：在评估变异效应时，不应只考虑变异位点与 motif 的重叠，而应累加所有可能偏移的结合贡献。这一策略可迁移到任何"序列窗口-结合事件"的预测。

6. **bootstrap 评估模型差异**：用 bootstrap 构建对数似然分布来比较模型，比单点估计更稳健，且无需假设正态性。

7. **CUT&Tag 作为训练数据源的潜力**：CUT&Tag 数据训练的模型优于 ChIP-seq，可能因其信噪比更高或片段化偏倚更小。未来 TF 结合模型训练可优先考虑 CUT&Tag 数据。

## 15 与已有知识连接

- **ProBound 原版**：本文是 Bussemaker 实验室 ProBound [18] 的 PyTorch reimplementation。原版 ProBound 已证明可从 SELEX 数据推断生物物理可解释的结合模型。本文扩展了其应用范围至体内 ChIP-seq 数据。
- **AlleleDB [5]**：本文使用的 ASB 数据来自 AlleleDB，该数据库基于 1000 Genomes 变异和 ChIP-seq 数据。本文的似然函数与 AlleleDB 的 beta-binomial 检验同源，但用途从"检测 ASB"转为"评估模型"。
- **JASPAR [19] / HOCOMOCO [21]**：作为基准比较的传统 motif 数据库。本文显示这些数据库的模型在 ASB 预测上不如从体内数据训练的模型。
- **DeepBind [20]**：深度学习结合模型代表。本文未直接比较，但指出其模型在预测体内结合时可能不如体内训练的模型。
- **转录因子结合机制**：本文结果支持"序列亲和力是 TF 结合的主要决定因素"这一模型，但也揭示体内外差异（如 PU.1），提示共因子和染色质状态的重要性。
- **可迁移方向**：本文的 ASB 似然框架可迁移到：(1) 评估其他序列-功能模型（如剪接、甲基化）；(2) 整合多 TF 协同模型；(3) 结合 3D 基因组结构预测变异效应。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：多 TF 协同 ASB 模型
   - **来源局限/观察**：本文仅考虑单个 TF 的结合模型，但 PU.1 的体内外差异提示共因子效应
   - **核心假设**：在等位基因不平衡位点，多个 TF 的协同结合可解释部分单 TF 模型无法解释的变异
   - **增量**：将 PyProBound 扩展为多 TF 联合模型，同时拟合多个 TF 的结合能量谱和协同参数
   - **初步方法**：在 ASB 似然函数中引入多 TF 乘积项；使用 CUT&Tag 多 TF 数据训练
   - **验证方式**：在独立 ASB 数据集上比较单 TF vs 多 TF 模型的对数似然
   - **创新状态**：unverified

2. **候选名称**：基于深度学习的 ASB 预测器
   - **来源局限/观察**：本文的模型是生物物理可解释的，但可能受限于模型形式（位置独立能量）
   - **核心假设**：深度学习模型（如 CNN/Transformer）可捕捉位置依赖和非线性相互作用，在 ASB 预测上优于能量模型
   - **增量**：将 ASB 似然函数作为损失函数，训练端到端的深度学习模型
   - **初步方法**：以变异位点两侧序列为输入，以等位基因计数为监督信号，优化 beta-binomial 似然
   - **验证方式**：与本文的 PyProBound 模型在相同 ASB 数据上比较
   - **创新状态**：unverified

3. **候选名称**：片段化偏倚的通用校正框架
   - **来源局限/观察**：本文发现 ChIP-seq 片段化偏倚显著影响模型训练，但仅在 CTCF 上验证
   - **核心假设**：片段化偏倚是 ChIP-seq 的普遍现象，校正可提升所有 TF 的模型质量
   - **增量**：开发通用的片段化偏倚校正模块，可插入任意序列-功能模型
   - **初步方法**：在多个 TF 的 ChIP-seq 数据上训练偏倚模型，评估校正前后的模型性能
   - **验证方式**：跨 TF 交叉验证，比较校正前后 ASB 似然
   - **创新状态**：unverified

4. **候选名称**：ASB 似然作为模型选择的通用指标
   - **来源局限/观察**：本文的 ASB 似然函数能区分不同模型质量，但仅用于 TF 结合模型
   - **核心假设**：ASB 似然可作为任何序列-功能模型（如剪接、甲基化）的通用评估指标
   - **增量**：将 beta-binomial 似然框架推广到其他分子表型
   - **初步方法**：收集等位基因特异性的 RNA-seq、甲基化数据，构建类似似然函数
   - **验证方式**：在已知因果变异上比较不同模型的似然值
   - **创新状态**：unverified

5. **候选名称**：体内外模型差异的系统性分析
   - **来源局限/观察**：PU.1 的体内外模型差异提示某些 TF 的结合受上下文影响
   - **核心假设**：TF 的体内外模型差异程度与其共因子依赖性或染色质重塑活性相关
   - **增量**：量化多个 TF 的体内外模型差异，关联到 TF 的生化特性
   - **初步方法**：对 50+ TF 分别训练体外（SELEX）和体内（CUT&Tag）模型，计算模型间距离
   - **验证方式**：聚类分析，检验差异程度与已知共因子相互作用的关联
   - **创新状态**：unverified