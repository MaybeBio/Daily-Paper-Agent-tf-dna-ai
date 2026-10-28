## 01 基本信息

- **标题**：Interpretable biophysical neural networks of transcriptional activation domains separate roles of protein abundance and coactivator binding
- **作者与单位**：Claire LeBlanc; Pooja Agarwal; Jack Demaray; Gean Hu; Marissa Zintel; Angelica Lam; Joel Enrique Castro Hernandez; Max Staller（Staller Lab，UC Berkeley）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025
- **论文类型**：预印本（方法学 + 机制发现）
- **领域**：转录因子激活域（activation domain）序列-功能预测；可解释神经网络；蛋白质-蛋白质互作（TF-共激活因子）
- **关键词**：activation domain, interpretable neural network, biophysical model, TF abundance, coactivator binding, sequence grammar
- **DOI/arXiv 号**：10.1101/2025.09.19.677413
- **代码**：https://github.com/staller-lab/NN_interpretability_for_AD_prediction；Zenodo: 10.5281/zenodo.17102617
- **数据**：NIH SRA Accession #PRJNA1186961
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文聚焦转录因子（TF）内部的激活域（AD）——即 TF 中负责招募共激活因子的功能模块，而非 TF 与 DNA 的直接结合。但其核心方法——将生物物理模型嵌入神经网络架构以分离不同分子过程（蛋白丰度 vs. 共激活因子结合）的贡献——对 TF-DNA 互作研究具有直接可迁移性：同样的思路可用于分离 TF 结合亲和力与 TF 丰度对下游基因表达的贡献。此外，本文对深度网络（如 PADDLE）的 post-hoc 解释与生物物理网络参数的交叉验证，为 TF-DNA 结合模型的解释性分析提供了方法论模板。

## 02 一句话总结

本文设计了仅含一个卷积滤波器的简单神经网络（SimpleNN）及嵌入两态/三态生物物理模型的 BiophysicalNN，以酵母高通量筛选数据预测转录激活域（AD）的强度与 TF 丰度，通过直接可视化网络参数发现：疏水残基（尤其 C 端）同时增强共激活因子结合但降低 TF 丰度，酸性残基在 N 端促进结合、C 端则通过提高丰度间接增强激活——从而分离了氨基酸对蛋白丰度与共激活因子结合的独立贡献。

## 03 研究问题

- **具体问题**：激活域（AD）的序列语法（sequence grammar）——即氨基酸排列方式如何控制 AD 功能——尚不清楚。现有深度神经网络（TADA、PADDLE、ADPred）能准确预测 AD，但其内部表征难以解释，无法揭示氨基酸残基的具体功能角色。
- **为什么重要**：AD 是真核转录调控的核心效应模块，其序列多样性高、保守性低，理解其语法对预测致病突变、设计合成转录因子至关重要。此外，AD 功能受两个独立过程共同控制——蛋白丰度（降解速率）与共激活因子结合亲和力——传统分析无法区分二者。
- **现有方法不足**：深度网络（TADA、PADDLE、ADPred）参数过多（数万至数十万），post-hoc 解释（如 DeepLIFT、SHAP）虽能给出特征重要性，但无法区分"氨基酸影响丰度"与"氨基酸影响结合"两条路径；线性模型（如基于组成的回归）则无法捕捉非线性语法。
- **精确研究问题**：Can a minimally parameterized neural network with an embedded biophysical model separate the contributions of protein abundance and coactivator binding to transcriptional activation domain function, and reveal sequence grammar that deep networks learn implicitly?

## 04 背景与发展脉络

*（注：以下脉络基于本文引用与讨论，标注为「经外部核验」的部分来自文中引用的已发表工作，其余为本文框架。）*

1. **AD 功能的高通量测量**：Sort-seq 技术（Kwasnieski 等；本文引文 23）使大规模测量 AD 活性成为可能。本文数据来自 Staller 实验室前期工作（引文 17），测量了 17,732 个 40aa 肽段的 GFP（激活强度）与 mCherry（TF 丰度）。
2. **AD 预测的深度学习方法**：TADA（引文 28, 29）、PADDLE（引文 25）、ADPred（引文 21）相继开发，均能高精度预测 AD，但不可解释。ADhunter 为 Staller 实验室内部深度网络。
3. **生物物理模型**：酸性暴露模型（acidic exposure model，引文 26）提出 AD 功能由酸性残基（促进暴露）与芳香族/疏水残基（介导结合）的平衡控制。本文将其形式化为三态模型。
4. **可解释神经网络**：MAVE-NN（引文 10）和 MoCHI（引文 11）将生物物理模型嵌入网络架构以预测基因型-表型图谱；BoltzNet（引文 13）用单卷积滤波器预测 TF-DNA 结合平衡常数。本文借鉴三者，首次将此类方法应用于 AD 的双表型（丰度+活性）联合预测。
5. **本文主张的位置**：在"深度网络高精度但不可解释"与"线性模型可解释但精度不足"之间，提出"最小复杂度 + 生物物理约束"的中间路线，并证明其精度接近深度网络、可解释性远超之。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 深度网络不可解释 | TADA、PADDLE、ADPred 预测准确但无法揭示序列语法 | 数万至数十万参数，内部表征为分布式编码 | Results 节 "The simple neural network..." 段；参数对比（234 vs 96,769 vs 80,005×8） |
| Post-hoc 解释无法区分因果路径 | DeepLIFT 显示酸性/芳香族残基重要，但无法判断是影响丰度还是影响结合 | 深度网络同时编码两条路径，post-hoc 归因混合二者 | Results 节 "Biophysical Neural Networks help to interpret..." 段；图 3G-H |
| 丰度与活性混淆 | 传统分析将 GFP 信号直接视为 AD 强度，忽略 mCherry 反映的丰度差异 | 高丰度可补偿弱结合，低丰度可掩盖强结合 | Results 节 "The simple neural network for predicting transcription factor abundance" 段；图 2 |
| 线性模型精度不足 | 基于组成的回归（如线性 one-hot 回归）无法捕捉位置效应 | AD 语法包含位置依赖的非线性相互作用 | Results 节 "The simple neural network for predicting activation domain strength" 段（Pearson 0.801 vs 0.841） |
| 生物物理模型参数不可直接测量 | 两态/三态模型的平衡常数缺乏实验测量手段 | AD-共激活因子结合为弱、瞬态互作，难以体外定量 | Results 节 "Biophysical Neural Networks retain prediction accuracy" 段；图 S10 用 FINCHES 间接验证 |

## 06 核心思想

**1) 表面方法**：
- 设计仅含一个卷积滤波器 + 一个全连接层的 SimpleNN，分别预测 GFP（AD 强度）和 mCherry（TF 丰度）。
- 设计 BiophysicalNN：两个平行卷积分支分别预测两态/三态模型的平衡常数（K₁、K₂），再通过解析公式将平衡常数映射为 GFP 和 mCherry 预测值。
- 两态模型：AD 在"未结合"与"结合共激活因子"两态间平衡；三态模型：增加"塌缩/隐藏"态（酸性暴露模型的形式化）。
- 训练后直接可视化卷积滤波器权重和全连接层权重，解读每个氨基酸的角色。

**2) 核心洞察**：
- 网络参数即生物物理假设的检验：如果 BiophysicalNN 能达到与 SimpleNN 相当的精度，说明两态/三态模型足以解释数据，无需更复杂机制。
- 通过将"丰度"和"结合"建模为独立分支，网络被迫将氨基酸效应分配到两条路径，从而分离此前混淆的贡献。
- 关键发现：疏水残基（W、F、I、L、V）在 C 端同时增加结合（K₂↑）但降低丰度（mCherry↓）；酸性残基（D、E）在 N 端促进结合、C 端则主要通过提高丰度起作用。这解释了为何组成分析会得出矛盾结论——同一残基在不同位置有相反功能。

**3) 可能的普适教训** [Analysis]：
- 对 TF-DNA 互作研究：DNA 结合域（DBD）的序列-亲和力关系同样受"蛋白丰度"与"结合亲和力"双重控制，本文的"双分支生物物理网络"可直接迁移为"DBD 结合分支 + 蛋白稳定性分支"。
- 对可解释 AI 的一般启示：与其对黑箱做 post-hoc 解释，不如将领域知识（生物物理模型）作为网络结构的硬约束，使参数本身即科学假设的估计值。
- 对序列-功能映射研究：当表型由多个独立分子过程共同决定时，显式建模中间变量（如平衡常数）比直接端到端预测更能揭示机制。

## 07 方法总览

- **输入**：40aa 氨基酸序列（one-hot 编码为 20×40 矩阵）。
- **输出**：GFP 荧光（AD 强度）、mCherry 荧光（TF 丰度）。
- **模块**：
  1. 卷积层（单滤波器，大小可变：1aa 至 40aa）——扫描序列中的功能基序。
  2. 全连接层（权重维度 = 滤波器输出长度）——对滤波器输出按位置加权。
  3. 生物物理映射层（仅 BiophysicalNN）：将预测的平衡常数 K₁、K₂ 通过解析公式转换为 GFP/mCherry 预测值。
- **训练**：
  - 每个架构训练 30 个随机种子，200 epochs，early stopping，学习率 0.001。
  - SimpleNN 损失：MAE。
  - BiophysicalNN 两阶段训练：先训练丰度分支（冻结结合分支），再训练结合分支；损失含惩罚项（负权重惩罚、负平衡常数惩罚）。
- **工具**：PyTorch；代码与数据公开。
- **反馈回路**：无显式主动学习回路；但通过"训练→可视化参数→回到数据验证"的迭代解释流程实现科学发现闭环。
- **假设**：
  1. 两态/三态模型足以描述 AD 功能（模型选择假设）。
  2. mCherry 荧光线性反映 TF 丰度。
  3. GFP 荧光通过 Hill 函数与结合态 TF 数量相关。
  4. 卷积滤波器捕获的基序是位置无关的（位置效应由全连接层捕获）。
- **文字流程**：输入 40aa 序列 → one-hot 编码 → 卷积滤波器扫描（捕获氨基酸类型偏好）→ 全连接层按位置加权（捕获位置效应）→ 输出预测值（SimpleNN 直接输出 GFP/mCherry；BiophysicalNN 先输出平衡常数再映射为 GFP/mCherry）→ 训练完成后直接读取滤波器权重和全连接层权重作为"氨基酸角色图谱"。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 单卷积滤波器 | 扫描 40aa 序列，捕获氨基酸类型偏好（如酸性、芳香族） | 最小化参数以实现直接解释；卷积天然适合基序检测 | 输入：20×40 one-hot；输出：长度 40-k+1 的向量 | Results 节 "The simple neural network..." 段；图 1E-F 显示滤波器权重与已知 AD 特征一致 | 预期：若移除，网络退化为纯线性模型，精度下降（文中未做消融，[Analysis] 推测） |
| 全连接层（位置权重） | 对滤波器输出按序列位置加权 | 捕获位置效应（如 C 端 vs N 端差异） | 输入：卷积输出向量；输出：标量 | 图 1E-F 显示 C 端权重显著高于 N 端 | 预期：若移除，无法捕获位置特异性语法（文中未做消融，[Analysis] 推测） |
| 生物物理映射层（两态/三态） | 将平衡常数 K₁、K₂ 映射为 GFP/mCherry 预测 | 强制网络学习有物理意义的中间变量，分离丰度与结合贡献 | 输入：预测的 K₁、K₂；输出：GFP、mCherry | Results 节 "Biophysical Neural Networks retain prediction accuracy" 段；图 3D 显示精度与 SimpleNN 相当 | 实测：三态模型未比两态模型更优（图 4D），说明数据不支持更复杂模型 |
| 双分支架构（丰度分支 vs. 结合分支） | 分别预测 mCherry 和 K₂ | 将氨基酸效应分配到两条独立路径，避免混淆 | 输入：同一序列；输出：mCherry 和 K₂ | Results 节 "Biophysical Neural Networks reveal activation domain grammar" 段；图 3E-F 显示两分支权重模式不同 | 实测：若合并为单分支，将无法发现疏水残基的双向作用（文中未做消融，[Analysis] 基于逻辑推断） |
| 损失函数惩罚项 | 惩罚负权重和负平衡常数 | 保证网络学到物理上合理的解 | 输入：当前权重/预测值；输出：惩罚项加入损失 | Methods 节 "Neural Network training" 段 | 预期：若移除，网络可能学到负平衡常数等非物理解（文中未做消融，[Analysis] 推测） |

## 09 关键公式符号

**两态模型**（图 3B）：
- 设 AD 在未结合态（U）与结合态（B）间平衡：U ⇌ B，平衡常数 K₁ = [B]/[U]。
- 结合态分数：p_bound = K₁ / (1 + K₁)。
- GFP 预测：GFP = Hill(p_bound · [共激活因子])，其中 Hill 函数为 Hill(x) = x^n / (x^n + K_d^n)。

**三态模型**（图 4B，酸性暴露模型形式化）：
- 三态：塌缩态（C）、暴露态（E）、结合态（B）。
- 平衡：C ⇌ E（K₁），E + 共激活因子 ⇌ B（K₂）。
- 结合态分数：p_bound = K₁·K₂ / (1 + K₁ + K₁·K₂)。
- GFP 预测：GFP = Hill(p_bound · [共激活因子])。

**mCherry 预测**（丰度）：
- mCherry = f(序列)，由独立分支直接预测，反映蛋白稳定性/降解速率。

**损失函数**（BiophysicalNN 第二阶段）：
- loss = MAE(GFP_pred, GFP_exp) + 0.1·(-Σ负权重) + 0.1·(-Σ负平衡常数)

**符号说明**：
- K₁：塌缩/暴露平衡常数（三态）或未结合/结合平衡常数（两态）
- K₂：暴露态与共激活因子结合平衡常数
- n：Hill 系数
- K_d：Hill 函数中的解离常数

## 10 实验设计与证据链

**数据集**：
- 来源：Staller 实验室前期 Sort-seq 筛选（引文 17）
- 规模：17,732 个 40aa 肽段（来自 Gcn4 同源物 tiling）
- 表型：GFP（激活强度）、mCherry（TF 丰度）
- 划分：按同源序列层级聚类分为 train/validation/test，确保测试集与训练集序列相似性最小

**指标**：Pearson 相关系数（预测 vs 实验）

**基线/对比模型**：
- 线性回归（one-hot 编码）
- ADhunter（深度残差网络，内部模型）
- TADA、PADDLE、ADPred（已发表深度网络）
- SimpleNN（本文，单卷积滤波器）

**评测协议**：在相同 train/test 划分下比较 Pearson 相关；分类任务（是否激活域）比较 AUC 等

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| SimpleNN 预测 GFP | 最小网络可达接近深度网络的精度 | vs ADhunter、TADA、PADDLE、ADPred | Pearson 0.841（test）；略低于 ADhunter 但参数少 300-2500 倍 | 简单网络足以捕获 AD 主要信号 | 不能证明 SimpleNN 捕获了深度网络的全部信号 | Results 节 "The simple neural network..." 段；图 1C-D |
| SimpleNN 预测 mCherry | 丰度可被序列预测 | vs ADhunter-Cherry | Pearson 0.532（test） | 丰度受序列控制，但噪声较大 | 不能确定丰度预测的生物学机制 | Results 节 "The simple neural network for predicting transcription factor abundance" 段；图 2B |
| BiophysicalNN（两态）预测 GFP+mCherry | 生物物理模型嵌入不损失精度 | vs SimpleNN | 精度相当（图 3D） | 两态模型足以描述数据 | 不能排除更复杂模型同样适用 | Results 节 "Biophysical Neural Networks retain prediction accuracy" 段 |
| BiophysicalNN 参数可视化 | 网络学到氨基酸的双向作用 | 对比 SimpleNN 权重 | 疏水残基 C 端↑结合↓丰度；酸性残基 N 端↑结合、C 端↑丰度 | AD 语法包含位置依赖的双向调控 | 不能证明因果方向（观察性） | Results 节 "Biophysical Neural Networks reveal activation domain grammar" 段；图 3E-F |
| 三态 BiophysicalNN | 酸性暴露模型可被网络学习 | vs 两态模型 | 未优于两态模型（图 4D） | 数据不支持三态模型的额外复杂度 | 不能否定酸性暴露模型本身 | Results 节 "The Three-State Biophysical NN is not learning the acidic exposure model" 段 |
| FINCHES 验证 | 预测的 K₁ 与共激活因子结合相关 | 计算预测 vs 实验 | K₁ 与 FINCHES 预测的结合强度相关（图 S10） | 平衡常数具有物理意义 | 相关性非因果，FINCHES 本身为计算预测 | Results 节 "Biophysical Neural Networks reveal activation domain grammar" 段；图 S10 |
| DeepLIFT 解释 ADhunter | 深度网络也学到双向作用 | DeepLIFT vs BiophysicalNN 权重 | 深度网络显示酸性残基双向作用，与 BiophysicalNN 一致 | 两种方法收敛到相同生物学结论 | DeepLIFT 无法分离丰度与结合路径 | Results 节 "Biophysical Neural Networks help to interpret..." 段；图 3G |
| PADDLE 突变扫描 | 深度网络学到 C 端疏水效应 | 全单点突变扫描 | C 端疏水残基降低预测活性 | 与 BiophysicalNN 的丰度效应一致 | 无法区分丰度 vs 结合机制 | Results 节 "Biophysical Neural Networks help to interpret..." 段；图 3H |

## 11 结论正确解读

- **任务范围**：本文仅针对酵母 Gcn4 同源物的 40aa 激活域肽段，预测 GFP/mCherry 两种表型。结论不直接推广到其他 TF 家族、其他物种或全长 TF 上下文。
- **Oracle/真值输入**：实验数据来自 Sort-seq 筛选，GFP/mCherry 为代理表型，非直接测量共激活因子结合亲和力或蛋白降解速率。平衡常数 K₁、K₂ 为网络隐变量，未经实验直接验证。
- **端到端状态**：完整端到端（序列→表型），但中间变量（平衡常数）的生物学解释依赖模型假设。
- **算力成本**：极低（单卷积滤波器网络，数百参数），可在 CPU 上快速训练。
- **历史数据依赖**：训练数据来自单一筛选平台（Sort-seq），存在平台特异性偏差；测试集与训练集按同源序列分层，泛化到远缘序列的能力未充分验证。
- **模型依赖**：结论（疏水残基双向作用、酸性残基位置效应）依赖 BiophysicalNN 的特定架构假设（两态模型、Hill 函数映射）。若改用其他生物物理模型，结论可能变化。
- **最难情形**：mCherry 预测精度显著低于 GFP（Pearson 0.532 vs 0.841），说明丰度预测是薄弱环节；三态模型未优于两态模型，说明当前数据无法区分更复杂的构象模型。
- **群体/领域边界**：结论限于"酸性激活域"（acidic ADs），不适用于富含脯氨酸、富含谷氨酰胺等其他 AD 类型。
- **不确定性**：作者未报告置信区间或重复实验变异性；30 个随机种子的结果差异未展示。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 预测精度略低于深度网络 | SimpleNN 的 Pearson 0.841 vs ADhunter 更高 | 未明确提及（暗示可结合两者） | Results 节 "The simple neural network..." 段 |
| 三态模型未学到酸性暴露模型 | 网络未表现出预期的"酸性残基促进暴露"模式 | 需要更复杂的网络设计、损失函数或中间态实验测量 | Results 节 "The Three-State Biophysical NN is not learning the acidic exposure model" 段 |
| 平衡常数缺乏实验验证 | K₁、K₂ 为网络隐变量，仅与 FINCHES 计算预测间接相关 | 需要直接测量 AD-共激活因子结合的实验 | Results 节 "Biophysical Neural Networks reveal activation domain grammar" 段；图 S10 |
| 丰度预测噪声大 | mCherry 预测 Pearson 仅 0.532 | 未明确提及 | Results 节 "The simple neural network for predicting transcription factor abundance" 段 |
| 网络冗余性 | 即使简单网络也可能存在参数冗余，影响解释唯一性 | 训练多个随机种子并取平均 | Methods 节 "Neural Network training" 段 |
| 数据来自单一物种/平台 | 仅酵母 Gcn4 同源物，Sort-seq 平台 | 未明确提及 | Methods 节 "Dataset preparation" 段 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 单卷积滤波器 + 全连接层的"可解释性"依赖权重直接对应氨基酸贡献的假设 | 卷积滤波器在滑动扫描时，同一位置的权重可能混合了相邻残基的效应；全连接层的负权重可能不代表抑制，而是与其他特征的交互 | 若权重解读有误，则"疏水残基双向作用"的结论可能不成立 | 对滤波器权重做置换检验：随机打乱序列位置，观察权重变化；或用合成序列验证预测 | Results 节 "The simple neural network..." 段；图 1E-F |
| 两态模型与三态模型精度相当，但作者选择两态作为主要解释框架 | 三态模型可能因训练不充分或损失函数设计不当而未发挥潜力；"数据不支持三态"与"三态模型错误"是不同结论 | 若三态模型（酸性暴露模型）实际正确，则两态解释可能遗漏关键机制 | 用模拟数据测试三态模型能否恢复已知参数；增加训练 epoch 或调整损失权重 | Results 节 "The Three-State Biophysical NN is not learning the acidic exposure model" 段 |
| FINES 验证仅用相关性，未做因果检验 | FINCHES 本身为计算预测，与实验测量可能系统性偏差；相关性可能由第三变量（如疏水性）驱动 | 若 K₁ 与 FINCHES 的相关是虚假的，则"平衡常数有物理意义"的 claim 被削弱 | 用实验测定的 AD-共激活因子结合数据（如 ITC、NMR）直接验证 | Results 节 "Biophysical Neural Networks reveal activation domain grammar" 段；图 S10 |
| 训练 30 个随机种子但未报告参数变异性 | 若不同种子的权重差异大，则"网络学到稳定模式"的 claim 不成立 | 可解释性结论的稳健性取决于参数估计的稳定性 | 报告 30 个种子的权重分布（均值±标准差），或聚类分析 | Methods 节 "Neural Network training" 段 |
| 测试集按同源序列分层，但未报告测试集与训练集的序列相似度分布 | 若测试集仍与训练集高度相似，泛化性能被高估 | TF 激活域多样性高，跨家族泛化是实际应用的关键 | 报告测试集与训练集的最大序列同一性；用远缘物种 AD 做外部验证 | Methods 节 "Dataset preparation" 段 |
| 对 PADDLE 的突变扫描解释中，C 端疏水残基降低预测活性被归因于丰度效应 | PADDLE 训练数据可能本身包含丰度偏差（未控制 mCherry），其预测降低可能反映训练集伪影而非真实生物学 | 若 PADDLE 的预测受丰度混淆影响，则"深度网络也学到双向作用"的结论需重新审视 | 检查 PADDLE 训练数据是否控制丰度；用丰度归一化数据重新训练 PADDLE | Results 节 "Biophysical Neural Networks help to interpret..." 段；图 3H |

## 14 学到什么

*（本节标题为「Agent 提炼的知识候选」，面向课题方向：蛋白质-DNA 互作（聚焦 TF-DNA 结合机制）× AI/深度学习 或 物理模拟）*

1. **双分支生物物理网络架构**：将"丰度/稳定性"与"结合亲和力"建模为独立分支，可分离同一残基对两个分子过程的不同贡献。迁移到 TF-DNA：可将"TF 蛋白丰度"与"TF-DNA 结合亲和力"分为两个分支，联合预测下游基因表达，从而解析致病突变是通过 destabilize 蛋白还是削弱 DNA 结合来致病。

2. **最小复杂度原则**：单卷积滤波器 + 全连接层的网络即可达到接近深度网络的精度（Pearson 0.841 vs 深度网络），且参数可直接可视化。对 TF-DNA 结合预测：在追求更高精度的深度网络之前，先尝试最小可解释模型，可能已捕获主要信号。

3. **生物物理模型作为网络结构的硬约束**：将平衡常数作为中间隐变量，比端到端黑箱预测更具解释力。迁移到 TF-DNA：可将 TF-DNA 结合的自由能（ΔG）或解离常数（K_d）作为中间变量，网络学习序列→ΔG→表达水平的映射，而非直接序列→表达。

4. **多网络交叉验证**：用简单可解释网络解释深度网络的 post-hoc 归因（DeepLIFT），两者收敛到一致结论时可信度大增。对 TF-DNA：当对深度网络（如 Enformer）做 feature attribution 时，用可解释的浅层网络（如基于 PWM 的模型）交叉验证归因结果。

5. **位置权重揭示语法**：全连接层的权重分布显示 C 端残基效应更强，提示激活域功能存在位置依赖性。对 TF-DNA：类似的位置权重分析可揭示 TF 结合位点内不同位置的碱基偏好强度，区分"核心识别"与"辅助接触"位置。

6. **负权重惩罚的正则化作用**：在损失函数中加入负权重惩罚，不仅提升可解释性，还可能改善泛化（文中未直接验证，[Analysis] 推测）。对 TF-DNA 模型：在训练结合亲和力预测模型时，约束权重非负可强制模型学习"增强"而非"抑制"的基序，避免过拟合。

7. **Hill 函数作为表型映射**：用 Hill 函数将结合态分数映射为表达水平，隐含了协同性假设。对 TF-DNA：在预测 TF 结合对基因表达的剂量-响应关系时，Hill 函数是比线性映射更合理的先验。

## 15 与已有知识连接

- **Sort-seq 技术**：本文数据来自 Sort-seq 高通量筛选（Kwasnieski 等，引文 23），与深度突变扫描（DMS）方法互补。在 TF-DNA 领域，类似的 Sort-seq 或 MITOMI 方法已用于测量 TF 结合亲和力的大规模突变效应。
- **酸性暴露模型**：本文形式化的三态模型源自 Staller 实验室前期工作（引文 26），与 TF-DNA 领域的"构象选择"与"诱导拟合"模型在概念上同构——蛋白质在无配体时存在多种构象，配体选择并稳定特定构象。
- **MAVE/MoCHI**：本文明确借鉴了 MAVE-NN（引文 10）和 MoCHI（引文 11）的生物物理网络框架。这两个工具已应用于蛋白质-蛋白质互作和 RNA 剪接的突变效应预测，其"序列→生物物理参数→表型"的框架可直接迁移到 TF-DNA 结合。
- **BoltzNet**：本文引用了 BoltzNet（引文 13），该工作用单卷积滤波器预测 TF-DNA 结合平衡常数，与本文方法高度同源。两者共同表明：卷积滤波器权重可解释为序列基序的物理贡献。
- **DeepLIFT**：本文使用 DeepLIFT（引文 9）解释深度网络，该方法在基因组学中被广泛用于解释 TF 结合预测模型（如 DeepSEA、Basenji）。本文的创新在于用可解释网络验证 DeepLIFT 归因。
- **FINCHES**：本文用 FINCHES（引文 40）预测 AD-共激活因子相互作用强度作为外部验证。FINCHES 基于分子动力学力场，与 TF-DNA 领域的 MD 模拟（如 AMBER、CHARMM）方法同源，提示计算预测与神经网络隐变量的交叉验证策略。
- **与 AlphaFold 等结构预测工具的关系**：本文不涉及结构预测，但其"序列→功能"的直接映射思路与 AlphaFold 的"序列→结构"形成互补。对 TF-DNA 领域，可考虑将 AlphaFold 预测的 TF 结构作为先验特征输入到结合预测模型中。

## 16 研究想法

*（本节标题为「Agent 生成的研究候选」）*

**候选 1：双分支生物物理网络用于 TF-DNA 结合突变效应预测**
- **名称**：BiophysicalTF-DNA：分离 TF 稳定性与 DNA 结合亲和力的突变效应预测器
- **来源局限/观察**：现有 TF 突变效应预测模型（如基于深度学习的 saturation mutagenesis 预测）通常直接预测表达或结合变化，无法区分突变是通过 destabilize TF 蛋白还是削弱 DNA 结合来致病。本文的双分支架构提供了分离策略。
- **核心假设**：TF 序列变异对下游基因表达的影响 = 对蛋白稳定性的影响 + 对 DNA 结合亲和力的影响，二者可加性分解。
- **初步方法**：以本文 BiophysicalNN 为模板，输入 TF 的 DBD 序列（或全长序列），两个分支分别预测蛋白稳定性（可用 mCherry 或蛋白丰度数据训练）和 DNA 结合 K_d（可用 HT-SELEX、MITOMI 数据训练），联合预测下游表达。
- **验证方式**：在已知致病 TF 突变（如 p53、MYC 的癌症突变）上测试，比较双分支模型与单任务模型的解释力；用实验测定的稳定性与结合数据验证分支预测。
- **创新状态**：unverified（需验证可加性假设）

**候选 2：卷积滤波器权重作为 TF 结合位点语法图谱**
- **名称**：Position-Resolved TF Binding Grammar via Minimal CNNs
- **来源局限/观察**：本文的单卷积滤波器权重直接可视化为"氨基酸角色图谱"，揭示了位置依赖的语法。类似方法可应用于 TF-DNA 结合位点，揭示碱基位置依赖的偏好。
- **核心假设**：TF 结合位点的序列语法可由单卷积滤波器 + 位置权重完全捕获，无需深度网络。
- **初步方法**：用本文 SimpleNN 架构训练 TF-DNA 结合预测模型（输入为 DNA 序列，输出为结合强度），可视化滤波器权重（碱基偏好）和位置权重（位置效应），与已知 TF 结合 motif（如 JASPAR PWM）对比。
- **验证方式**：在多个 TF 的 HT-SELEX 数据上测试，比较 SimpleNN 与深度网络（如 DeepSEA）的精度和可解释性；用 PWM 一致性评估滤波器权重。
- **创新状态**：partially checked（BoltzNet 已用类似思路预测 TF-DNA 结合，但未系统分析位置语法）

**候选 3：三态模型在 TF-DNA 结合中的形式化**
- **名称**：Three-State Conformational Model of TF-DNA Binding
- **来源局限/观察**：本文三态模型（塌缩/暴露/结合）未优于两态模型，作者归因于数据不足以区分。但 TF-DNA 结合已知存在构象选择（如 bZIP 的卷曲螺旋预组装 vs 诱导拟合），三态模型可能更适用。
- **核心假设**：TF-DNA 结合存在"未折叠/折叠但未结合/结合"三态，且三态平衡常数可由序列预测。
- **初步方法**：将本文三态 BiophysicalNN 架构应用于 TF-DNA 结合数据（如 MITOMI 测量的结合亲和力 + 蛋白稳定性数据），比较两态与三态模型的拟合优度。
- **验证方式**：用 MD 模拟或 NMR 实验测定的构象分布验证三态模型的平衡常数预测。
- **创新状态**：unverified

**候选 4：跨物种激活域语法迁移**
- **名称**：Cross-Species Transfer of Activation Domain Grammar
- **来源局限/观察**：本文仅在酵母 Gcn4 同源物上训练。TF 激活域在真核生物中功能保守但序列多样，跨物种迁移能力未知。
- **核心假设**：激活域语法（疏水/酸性残基的位置效应）在物种间保守，可迁移。
- **初步方法**：用本文 SimpleNN 在酵母数据上训练，在人类 TF 激活域（如 p53 TAD、MYC TAD）上测试零样本预测；或用迁移学习微调。
- **验证方式**：与人类激活域实验数据（如点突变扫描）对比。
- **创新状态**：unverified

**候选 5：激活域语法与 DNA 结合域语法的联合建模**
- **名称**：Unified Grammar of TF Function：AD + DBD
- **来源局限/观察**：本文仅建模 AD，未考虑 DBD。TF 功能由 AD（招募共激活因子）和 DBD（结合 DNA）共同决定，二者可能存在协同或补偿效应。
- **核心假设**：TF 的序列-功能映射可分解为 AD 和 DBD 两个模块的独立贡献加上交互项。
- **初步方法**：将本文 BiophysicalNN 扩展为双模块架构，输入为 AD 序列 + DBD 序列，分别预测共激活因子结合和 DNA 结合，联合预测转录输出。
- **验证方式**：在合成 TF 文库（同时变异 AD 和 DBD）上测试。
- **创新状态**：unverified