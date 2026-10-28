## 01 基本信息

- **标题**：A statistical model for quantitative analysis of single-molecular footprinting data
- **作者与单位**：Ozonov EA; Gaspa-Toneu L; Peters AH（Friedrich Miescher Institute for Biomedical Research, Basel，推测，原文未明确标注单位）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025
- **论文类型**：方法学论文（含生物应用验证）
- **领域**：单分子足迹分析（SMF）的统计建模；蛋白质-DNA互作定量分析
- **关键词**：single-molecule footprinting (SMF), NOMe-seq, statistical model, footprint spectral analysis, transcription factors, nucleosomes, Bayesian inference, variational approximation
- **DOI/arXiv 号**：10.1101/2025.05.20.655044
- **代码**：R包 `fetchNOMe`（https://github.com/fmi-basel/gpeters-fetchNOMe）；R包 `nomeR`（https://github.com/fmi-basel/compbio-nomeR）
- **数据**：自产 amplicon-based NOMe-seq 数据（mESCs，48个amplicon）；公开数据 GSE78140（基因组NOMe-seq，mESCs）、GSE112140（ChIP-seq，Ctcf/Rest）、REMAP2022数据库
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文不直接使用AI/深度学习或MD/对接等物理模拟方法，而是为SMF数据（NOMe-seq等）提供严格的统计推断框架，解决TF–DNA结合与核小体占位的单分子水平定量问题。其核心价值在于：为TF–DNA互作研究提供可量化的footprint长度谱与位置预测工具，可作为AI方法（如深度学习footprint识别）的统计基线或特征提取前置步骤，也可为MD/对接模拟提供实验约束（如footprint长度、占据率等）。


## 02 一句话总结

本文提出一个基于随机过程的贝叶斯统计框架（含footprint spectral analysis与动态规划位置预测两个组件），用于从单分子足迹（SMF）数据中无偏推断footprint长度谱、丰度及噪声水平，并在模拟与mESC NOMe-seq数据上验证其能区分TF与核小体footprint、实现de novo TF结合位点鉴定。


## 03 研究问题

- **具体问题**：SMF数据（如NOMe-seq）中，如何在不依赖已知TF结合位点先验信息的情况下，定量推断footprint的长度分布、各类footprint的丰度、背景与footprint内部的噪声水平，并进一步在单分子水平预测每个footprint的具体位置？
- **为什么重要**：SMF技术（NOMe-seq、Fiber-seq、FOODIE、DAF-seq）能在单DNA分子分辨率下反映TF与核小体的结合状态，是研究基因调控中蛋白质-DNA互作随机性的关键工具。但缺乏严格的统计模型来从高噪声、稀疏标记的数据中提取定量信息，限制了其应用深度。
- **现有方法不足**：现有SMF分析方法多依赖平均化窗口（如固定窗口内甲基化率）、已知motif匹配或ChIP-seq先验，无法直接估计footprint长度、无法区分不同长度footprint的贡献、对噪声（不完全标记、检测错误）缺乏显式建模，且难以在无先验情况下进行de novo footprint鉴定。
- **精确研究问题**：Can a stochastic-process-based Bayesian model with variational inference accurately recover footprint length spectra and per-molecule footprint positions from sparse, noisy SMF data, without prior knowledge of binding site locations?


## 04 背景与发展脉络

*注：以下脉络基于本文框架及文中引用，标注「仅本文框架」或「经外部核验」。*

1. **群体平均染色质分析时代**（经外部核验）：ChIP-seq、ATAC-seq、MNase-seq等提供群体平均的TF结合或染色质可及性信息，分辨率低（数百bp），无法反映单分子异质性。
2. **SMF技术兴起**（经外部核验）：NOMe-seq（M.CviPI甲基化GCH位点）、Fiber-seq（Hia5/M.EcoGII甲基化腺嘌呤）、FOODIE/DAF-seq（DddB/SsDddA脱氨）等，在单DNA分子上标记可及位点，实现单分子分辨率footprint检测。
3. **SMF数据分析的早期方法**（仅本文框架）：多采用固定窗口平均、已知motif匹配或与ATAC-seq/ChIP-seq重叠来定义footprint，缺乏对footprint长度、噪声的显式统计建模。
4. **隐马尔可夫模型（HMM）等统计方法**（仅本文框架）：已有研究引入HMM等模型处理SMF数据，但本文指出这些方法在估计footprint长度分布、处理多类型footprint共存及噪声建模方面仍有局限。
5. **本文位置**：提出一个统一的随机过程模型，将footprint长度、丰度、噪声作为可推断参数，通过联合概率推导与贝叶斯变分推断实现无偏的footprint spectral analysis，并进一步用动态规划实现单分子footprint定位，填补了SMF定量分析的统计方法论空白。


## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| SMF数据高噪声 | 不完全酶标记、检测错误导致可及/保护状态误判 | 酶标记效率有限、测序错误、bisulfite转化不完全 | Results 图2B-C；Methods "Statistical footprint spectral analysis" 节对噪声参数 β(1) 和 α(1) 的建模 |
| 标记位点稀疏且不均匀 | GCH位点分布不均，部分区域信息密度低 | 酶识别序列特异性（如M.CviPI仅识别GCH） | Results 图2G；Methods "In-silico simulation" 节对信息密度4%-50%的模拟 |
| footprint长度无法直接观测 | 观测到的是离散标记模式，footprint边界模糊 | footprint边界处标记概率渐变，受噪声干扰 | Results 图1C-D；Supplementary Text 对发射概率的推导 |
| 现有方法依赖先验知识 | 需已知motif或ChIP-seq峰来定义footprint区域 | 缺乏无偏的统计推断框架 | Introduction 第3段；Discussion 对现有方法局限的总结 |
| 无法区分不同长度footprint | TF（短）与核小体（长）footprint混叠 | 不同长度footprint在观测统计上相互干扰 | Results 图3A-C；模拟场景设计（ftp50与ftp150共存） |
| 单分子位置预测困难 | 需要区分footprint覆盖与背景可及状态 | 短片段（500-600bp）边界效应导致统计定位偏差 | Methods "Predicting footprint positions" 节对边界条件的讨论 |


## 06 核心思想

### 1) 表面方法
- 构建一个随机过程模型：在无限长DNA序列上随机放置K种不同长度的footprint（含背景），每种footprint有各自的先验起始概率和发射概率（可及/保护状态）。
- 推导任意距离S下两个位点状态组合的联合概率 P(γ,θ|S)，利用观测到的共现频数表进行贝叶斯推断，估计footprint长度谱、丰度及噪声参数。
- 基于推断得到的footprint参数构建位置权重矩阵（PWM），用动态规划计算每个footprint在每条单分子上的后验覆盖概率。

### 2) 核心洞察
- **footprint在统计上引入位点间相关性**：无footprint时，远距离位点状态独立；footprint的存在使距离S处的联合概率偏离独立假设，且偏离模式编码了footprint的长度与丰度信息。通过全距离联合概率的建模，可在不指定位置的情况下提取footprint长度谱。
- **噪声显式建模**：将背景噪声（β(1)）与footprint内部噪声（α(1)）作为独立参数推断，避免将噪声误判为真实footprint信号。
- **边界条件处理**：通过推导无限序列的渐近边界条件，消除短片段中因统计定位效应（statistical positioning）导致的系统偏差。

### 3) 可能的普适教训 [Analysis]
- 将「观测模式的空间相关性」转化为「组分长度与丰度的可推断统计量」这一思路，可迁移到其他单分子成像或足迹类数据（如Fiber-seq、CUT&Tag等）的分析中。
- 对噪声的显式参数化而非简单阈值过滤，是处理高噪声生物数据的通用原则。
- 在AI方法盛行的当下，本文展示了「可解释的生成式统计模型」在数据量有限、噪声结构明确时的优势——可作为深度学习方法的强基线或训练数据生成器。


## 07 方法总览

- **输入**：
  - SMF数据：每条单分子上标记位点的可及/保护状态（0/1），以及缺失信息（N）
  - 用户定义的footprint长度范围（如10-200bp）
  - 可选：已知footprint长度先验或噪声参数先验
- **输出**：
  - footprint长度谱（各长度footprint的丰度估计）
  - 背景噪声 β(1) 与footprint噪声 α(1) 的估计
  - 每条单分子上每个footprint的后验覆盖概率（位置预测）
- **模块**：
  1. **共现频数表构建**（fetchNOMe）：从BAM文件提取位点状态，计算各距离S下的状态组合频数 N(γθ)
  2. **Footprint spectral analysis**（nomeR, `infer_footprints_vb`）：贝叶斯模型 + 平均场变分推断，估计footprint长度谱与噪声参数
  3. **Footprint位置预测**（nomeR, `predict_footprints`）：基于推断参数构建PWM，动态规划计算后验覆盖概率
- **训练/推断**：平均场变分推断（Stan实现），非MCMC，计算效率高
- **反馈回路**：位置预测结果可反馈用于修正footprint长度范围设定，形成迭代分析
- **假设**：
  - footprint不重叠
  - footprint沿DNA随机放置（无位置偏好）
  - 位点间发射独立（给定footprint覆盖状态）
  - 背景与footprint的发射概率在分析区域内恒定


## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 共现频数表构建（fetchNOMe） | 从BAM文件快速提取位点状态并计算各距离下的共现频数 | 为统计推断提供充分统计量，避免逐分子似然计算 | 输入：BAM文件、参考序列；输出：N(γθ)频数表 | Methods "Co-occurrence count tables" 节；Results 图1D | 预期影响：无法进行后续推断（实测必需模块） |
| 随机过程模型与联合概率推导 | 建立footprint长度、丰度、噪声与观测联合概率的解析关系 | 核心统计基础，将footprint特征编码为可推断参数 | 输入：footprint长度集合、先验；输出：P(γ,θ|S)解析式 | Supplementary Text 式(36)；Results 图1C-D | 预期影响：模型退化为独立位点模型，无法检测footprint（实测必需模块） |
| 贝叶斯变分推断（`infer_footprints_vb`） | 从频数表推断footprint长度谱、背景噪声β(1)、footprint噪声α(1) | 实现无偏的footprint长度估计，量化不确定性 | 输入：频数表、长度范围；输出：参数后验均值与标准差 | Methods "Statistical footprint spectral analysis" 节；Results 图2B-C | 预期影响：无法获得定量footprint谱（实测必需模块） |
| 动态规划位置预测（`predict_footprints`） | 计算每条单分子上各footprint的后验覆盖概率 | 将全局谱信息转化为单分子水平的空间定位 | 输入：推断参数、单分子状态矩阵；输出：后验概率矩阵 | Methods "Predicting footprint positions" 节；Results 图3C-E | 预期影响：无法进行单分子footprint定位与分子分类（实测必需模块） |
| 边界条件处理 | 推导无限序列渐近边界条件，消除统计定位效应 | 短片段（500-600bp）中边界效应会扭曲预测 | 输入：片段长度、footprint长度；输出：修正后的配分函数 | Methods "Predicting footprint positions" 节；Supplementary Text 式(19) | 预期影响：短片段中位置预测出现系统偏差（预期效应，文中通过模拟验证） |
| Sobol'全局敏感性分析 | 量化各实验因素对模型性能的贡献 | 指导实验设计（酶选择、测序深度） | 输入：模拟参数空间；输出：一阶与总效应指数 | Results 图2E-F；Methods "Sobol' sensitivity analysis" 节 | 预期影响：无法系统评估实验参数对分析可行性的影响（分析工具，非模型组件） |


## 09 关键公式符号

*注：以下公式基于文中描述与Supplementary Text推导，仅列理解必需者。*

1. **联合概率 P(γ,θ|S)**（Supplementary Text 式36）：
   P(γ,θ|S) = 描述在距离S处两个位点状态组合(γ,θ)的概率，是footprint长度、丰度、噪声的函数。
   - γ,θ ∈ {0,1}：位点状态（0=可及，1=保护）
   - S：两位点间距离（bp）
   - 用途：核心推断量，连接观测频数与模型参数
   - 直觉：无footprint时P(γ,θ|S)与S无关；footprint引入S依赖的相关性

2. **发射概率**：
   - β(1)：背景（可及区域）中位点被标记为保护（1）的概率（背景噪声）
   - α(1)：footprint内部位点被标记为保护（1）的概率（footprint内噪声）
   - 用途：显式建模标记不完全与检测错误
   - 直觉：β(1) 应接近0（可及区域不应被标记），α(1) 应接近1（保护区域应被标记）

3. **footprint覆盖参数**：
   - ρ = (ρ₁, ρ₂, …, ρ_K)：各footprint（含背景）的覆盖度，ρ₁为背景覆盖度
   - π = (π₁, π₂, …, π_K)：各footprint的先验起始概率
   - l = (l₁, l₂, …, l_K)：各footprint的长度，l₁=1（背景）
   - 用途：footprint spectral analysis的推断目标
   - 直觉：ρ反映各类型footprint在基因组中的丰度比例

4. **Wasserstein距离**（评估指标）：
   - 用于比较推断的footprint谱与真实谱之间的差异
   - 用途：模拟实验中量化模型性能

5. **log-ratio变换**（位置预测评分）：
   - BG score = log((ρ_BG + B) / (ρ_Nucl + ρ_TF + B))
   - TF score = log((ρ_TF + B) / (ρ_BG + ρ_Nucl + B))
   - 其中B = 0.1为伪计数
   - 用途：将后验覆盖概率转化为可比较的评分，用于识别可及位点与TF结合位点


## 10 实验设计与证据链

**数据集与规模：**
- 模拟数据：3,000条染色质纤维，10kb染色体，500bp ROI（位置5001-5500）；两种场景（仅核小体；核小体+TF竞争）
- 自产数据：mESCs（JM8细胞系）amplicon-based NOMe-seq，48个amplicon，39个通过质控（平均1,450分子/amplicon，范围318-4,348）
- 公开数据：GSE78140（mESCs基因组NOMe-seq，4个样本）；GSE112140（Ctcf/Rest ChIP-seq）；REMAP2022数据库

**指标：**
- Footprint谱恢复：Wasserstein距离
- 位置预测：AUROC
- 生物学验证：与ChIP-seq峰重叠、motif富集、DNA甲基化水平关联

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| 模拟场景1（仅核小体） | 模型能从噪声数据中恢复核小体footprint长度谱 | 不同噪声水平、信息密度、测序深度组合 | 在宽参数范围内准确恢复150bp footprint谱 | 模型对核小体footprint谱推断有效 | 未测试极端低信息密度（<4%）下的表现 | Results 图2B-C |
| 模拟场景2（核小体+TF竞争） | 模型能区分短TF与长核小体footprint | 50bp TF footprint（5%覆盖）+ 150bp核小体（50%覆盖） | 成功分离两个谱峰 | 模型能区分不同长度footprint | 未测试多个TF footprint共存场景 | Results 图2D-F |
| 敏感性分析（Sobol'） | 信息密度是最关键实验因素 | 4因素：深度、信息密度、背景噪声、footprint噪声 | 信息密度占55-60%方差，深度占40-45%，噪声仅5-10% | 实验设计应优先优化酶选择（信息密度）和测序深度 | 敏感性分析基于特定参数范围，可能不适用于极端条件 | Results 图2E-F |
| amplicon NOMe-seq（mESC） | 模型在真实数据上能识别核小体footprint | 39个amplicon，footprint长度10-200bp | 核小体footprint峰约100-120bp，短于经典147bp | mESC中核小体footprint在NOMe-seq中表现为100-120bp | 无法区分真实核小体尺寸差异与酶标记偏差 | Results 图4A-D |
| 核小体footprint位置预测 | 预测的核小体位置与已知核小体定位一致 | 与ChIP-seq核小体数据比较 | 预测位置与已知核小体位置显著重叠 | 位置预测具有生物学有效性 | 未进行单分子级别的直接验证 | Results 图4D |
| 基因组NOMe-seq（GSE78140） | 模型能de novo识别TF结合位点 | 11个区域（共12.8Mb），TF footprint 15-80bp | 识别852个TF footprint富集窗口，62%的NOMe-only窗口与ChIP-seq峰重叠 | 模型能无先验发现TF结合位点 | 未与ATAC-seq直接比较灵敏度/特异性 | Results 图6A-B |
| TF footprint长度分析 | 不同TF具有特征性footprint长度 | 16组TF结合位点（含共结合组） | 11组显示25-40bp的显著footprint峰 | TF footprint长度具有因子特异性 | 样本量有限，需更多TF验证 | Results 图5D |


## 11 结论正确解读

- **任务范围**：本文解决的是SMF数据的统计推断问题——从单分子甲基化/可及性模式中估计footprint长度谱和位置。它不预测TF结合序列（motif），不模拟TF-DNA结构互作，也不涉及结合动力学。
- **Oracle/真值输入**：模拟实验中使用已知的footprint配置作为真值；真实数据中无独立真值，仅通过与ChIP-seq、ATAC-seq、motif注释的间接比较验证。
- **端到端状态**：方法已封装为R包（`nomeR` + `fetchNOMe`），可从BAM文件直接运行至footprint谱和位置输出，但需用户指定footprint长度范围等参数。
- **算力成本**：平均场变分推断（非MCMC），计算效率高；未报告具体运行时间。
- **历史数据依赖**：不依赖历史数据训练，属于生成式统计模型，参数从当前数据集推断。
- **模型依赖**：假设footprint不重叠、随机放置、发射独立；这些假设在密集结合区域可能不成立。
- **最难情形**：低信息密度（<10% GCH位点）和短TF footprint（<30bp）场景下，谱推断和位置预测的可靠性显著下降。
- **群体边界**：方法验证于mESCs的NOMe-seq数据；对其他SMF技术（Fiber-seq、FOODIE）的适用性基于原理推断，未直接验证。
- **有边界的复述**：本文证明，在footprint不重叠、标记位点密度≥4-5%的条件下，基于随机过程的贝叶斯变分推断能从SMF数据中无偏恢复footprint长度谱（模拟中误差随信息密度和深度降低），并在真实mESC数据上识别出100-120bp核小体footprint和25-40bp TF footprint，其中62%的de novo TF预测窗口有ChIP-seq支持。


## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 模型假设footprint不重叠 | 密集结合区域（如增强子）中footprint可能重叠，模型未显式建模 | 未明确提及 | Methods "Statistical footprint spectral analysis" 节（假设描述） |
| 依赖信息密度和测序深度 | 低信息密度（<10%）和低深度下性能显著下降 | 建议使用更高分辨率的酶（如FOODIE/DAF-seq） | Results 图2E-F；Discussion 对酶选择的讨论 |
| M.CviPI分辨率有限 | GCH位点密度低，限制TF footprint检测灵敏度 | 预期更高分辨率SMF技术（Fiber-seq等）可改善 | Discussion 第2段 |
| 核小体footprint短于经典147bp | 观测到100-120bp核小体footprint，可能反映酶标记偏差或核小体动态 | 未明确解释，需进一步验证 | Results 图4D-F；Discussion 第3段 |
| 未直接验证单分子水平预测准确性 | 位置预测通过群体水平（ChIP-seq、甲基化）间接验证 | 未明确提及 | Results 图6A-C |


## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 模拟场景仅含两种footprint类型 | 真实染色质中TF、核小体、其他结合蛋白类型更复杂，模型可能无法区分多类型共存 | 模型实用性取决于对复杂场景的鲁棒性 | 设计包含3-4种不同长度footprint的模拟实验 | Results 图2A（仅两种场景） |
| 核小体footprint 100-120bp与经典147bp不符 | 可能反映M.CviPI酶无法标记核小体内部近端DNA，而非真实核小体尺寸差异 | 影响对核小体定位的生物学解释 | 与MNase-seq或高分辨率SMF数据交叉验证 | Results 图4D-F |
| 位置预测依赖用户设定的footprint长度范围 | 若长度范围设定不当，可能引入偏差 | 方法客观性取决于参数选择的敏感性 | 系统测试不同长度范围对预测结果的影响 | Methods "Predicting footprint positions" 节 |
| 与ATAC-seq的比较仅报告重叠率，未报告灵敏度/特异性 | "NOMe-only"窗口可能包含大量假阳性 | 需要更严格的独立验证 | 使用独立ChIP-seq验证集计算精确率/召回率 | Results 图6B |
| 未与现有SMF分析方法（如HMM-based）进行基准比较 | 无法评估相对优势 | 方法学贡献需在现有方法谱系中定位 | 在相同模拟和真实数据上运行现有方法进行比较 | 全文未提及基准比较 |
| 变分推断可能低估后验不确定性 | 平均场近似对强相关性参数可能不准确 | 影响footprint谱估计的置信区间可靠性 | 与MCMC结果对比，或使用更灵活的变分族 | Methods "Statistical footprint spectral analysis" 节 |


## 14 学到什么

**Agent 提炼的知识候选**

1. **空间相关性→组分推断**：footprint在统计上引入位点间距离依赖的相关性，通过全距离联合概率建模可反推footprint长度与丰度。→ 可迁移至TF–DNA互作研究：从SMF或类似单分子数据中无偏估计TF footprint长度，无需已知motif。
2. **噪声显式参数化**：将背景噪声与footprint内部噪声作为独立可推断参数，而非简单阈值过滤。→ 可迁移至AI方法：在训练footprint识别模型时，显式建模噪声结构可提升鲁棒性。
3. **边界条件消除有限尺寸效应**：通过无限序列渐近边界条件消除短片段中的统计定位偏差。→ 可迁移至MD模拟或单分子数据分析：处理有限长度DNA片段时，边界效应不可忽视。
4. **Sobol'全局敏感性分析指导实验设计**：系统量化各实验因素对分析可行性的贡献，识别关键瓶颈（信息密度>深度>噪声）。→ 可迁移至课题：在设计SMF实验（酶选择、测序深度）时，可先通过敏感性分析确定最优参数组合。
5. **生成式模型作为AI训练数据生成器**：本文的随机过程模型可生成带ground truth的模拟SMF数据。→ 可迁移至深度学习footprint识别：用该模型生成大规模训练数据，避免人工标注成本。
6. **footprint长度作为TF结合特征**：不同TF显示特征性footprint长度（25-40bp），可用于TF类型判别。→ 可迁移至TF–DNA互作机制研究：将footprint长度与TF结构域大小、结合模式关联。
7. **核小体footprint短于经典值**：NOMe-seq中核小体footprint约100-120bp，提示核小体边缘DNA动态暴露。→ 可迁移至课题：核小体动态（breathing）可能影响TF可及性，值得在建模中纳入。


## 15 与已有知识连接

- **SMF技术原理**：NOMe-seq（Kelly et al., 2012）、Fiber-seq（Stern et al., 2019; Lee et al., 2020）、FOODIE/DAF-seq（近期）等，均基于酶标记可及DNA位点，本文模型适用于所有提供二元可及性信息的SMF平台。
- **HMM-based SMF分析**：已有研究（如NOMeHMM等）用隐马尔可夫模型处理SMF数据，本文的生成式随机过程模型可视为更灵活的替代方案，直接估计footprint长度谱而非预设状态数。
- **核小体定位与TF竞争**：经典核小体- TF竞争模型（如Wasson & Hartemink, 2009）预测TF结合与核小体占据互斥，本文模拟场景2直接建模了这一竞争关系。
- **统计位置效应（statistical positioning）**：Kornberg & Stryer (1988) 提出的核小体统计定位现象，本文通过边界条件处理直接回应了该问题在短片段中的影响。
- **贝叶斯变分推断**：与MCMC相比，变分推断在大规模基因组数据上计算效率更高，已在生物信息学中广泛应用（如STRUCTURE、fastSTRUCTURE等）。
- **与AI/深度学习方法的衔接**：本文的生成式模型可作为深度学习footprint识别器的训练数据生成器或特征提取前置步骤；其推断的footprint长度谱可作为神经网络的输入特征或正则化约束。
- **与MD/模拟的衔接**：本文推断的footprint长度和占据率可为粗粒化MD模拟或TF-DNA结合自由能计算提供实验约束参数。


## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：SMF数据驱动的TF–DNA结合动力学参数推断
   - **来源局限/观察**：本文模型假设footprint静态、不重叠，未建模结合/解离动力学；SMF数据实际包含单分子异质性信息。
   - **核心假设**：SMF数据中的footprint模式分布可反推TF结合/解离速率常数。
   - **增量**：将本文的静态随机过程扩展为时间依赖的马尔可夫更新过程，推断动力学参数。
   - **初步方法**：在本文模型基础上引入结合/解离速率参数，用变分推断或EM算法估计；用模拟数据验证可辨识性。
   - **验证方式**：与单分子FRET或smFRET数据对比；或设计不同结合动力学的体外SMF实验。
   - **创新状态**：unverified

2. **候选名称**：基于生成式SMF模型的深度学习footprint识别器训练框架
   - **来源局限/观察**：本文模型可生成带ground truth的模拟SMF数据，但未与深度学习方法结合；现有深度学习SMF分析缺乏大规模标注数据。
   - **核心假设**：用本文模型生成的大规模模拟数据训练的深度学习模型，可迁移至真实SMF数据并优于现有方法。
   - **增量**：将生成式统计模型与深度学习结合，实现「模拟训练→真实微调」的迁移学习框架。
   - **初步方法**：用`nomeR`生成多样本模拟数据，训练CNN或Transformer-based footprint分类器；在真实NOMe-seq数据上微调并评估。
   - **验证方式**：与现有HMM-based方法、本文统计模型在相同真实数据上比较F1、AUROC。
   - **创新状态**：unverified

3. **候选名称**：多酶SMF数据的联合统计建模
   - **来源局限/观察**：本文模型针对单一酶（M.CviPI）的GCH位点；不同酶（M.EcoGII、DddB等）位点密度和偏好不同，联合分析可提升分辨率。
   - **核心假设**：多酶SMF数据的联合建模可突破单一酶位点密度的限制，实现更高精度的footprint定位。
   - **增量**：扩展本文模型为多酶联合推断，共享footprint位置参数但各自独立发射概率。
   - **初步方法**：设计多酶联合似然函数，用坐标上升或变分推断优化；在模拟和真实多酶数据上验证。
   - **验证方式**：与单一酶分析比较footprint定位精度和长度谱估计误差。
   - **创新状态**：unverified

4. **候选名称**：TF–DNA结合结构域大小与footprint长度的关联分析
   - **来源局限/观察**：本文在mESCs中观察到不同TF的footprint长度差异（25-40bp），但未系统关联TF结构特征。
   - **核心假设**：TF的DNA结合结构域大小、形状与footprint长度存在可预测的定量关系。
   - **增量**：建立TF结构特征→footprint长度的预测模型，为SMF数据中的TF身份鉴定提供依据。
   - **初步方法**：收集已知TF结构数据（PDB），计算结合界面长度；与SMF推断的footprint长度回归分析。
   - **验证方式**：交叉验证预测精度；在已知TF结合位点上验证。
   - **创新状态**：unverified

5. **候选名称**：核小体动态（breathing）的SMF统计指纹
   - **来源局限/观察**：本文发现核小体footprint（100-120bp）短于经典147bp，提示核小体边缘DNA动态暴露，但未建模该动态。
   - **核心假设**：核小体边缘DNA的呼吸动态在SMF数据中留下可检测的统计特征（如footprint长度分布的不对称性）。
   - **增量**：在本文模型中引入核小体边缘部分展开状态，推断呼吸频率和幅度。
   - **初步方法**：扩展随机过程模型，允许核小体footprint边缘状态概率渐变；用模拟和真实数据拟合。
   - **验证方式**：与核小体呼吸的分子动力学模拟预测对比；或与MNase-seq数据交叉验证。
   - **创新状态**：unverified