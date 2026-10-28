## 01 基本信息
- **标题**：JASPAR 2026: expansion of transcription factor binding profiles and integration of deep learning models
- **作者与单位**：Ovek Baydar, Damla; Rauluseviciute, Ieva; Aronsen, Dina R; Blanc-Mathieu, Romain; Bonthuis, Ine; de Beukelaer, Herman; Ferenc, Katalin; Jegou, Alice; Kumar, Vipin; Lemma, Roza Berhanu; Lucas, Jeremy; Pochon, Mathis; Yun, Chang M; Ramalingam, Vivekanandan; Deshpande, Salil Sanjay; Patel, Aman; Marinov, Georgi K; Wang, Austin T; Aguirre, Alejandro; Castro-Mondragon, Jaime A; Baranasic, Damir; Cheneby, Jeanne; Gundersen, Sveinung; Johansen, Morten; Khan, Vipin; Kuijjer, Marieke L; Hovig, Eivind; Lenhard, Boris; Sandelin, Albin; Vandepoele, Klaas; Wasserman, Wyeth W; Parcy, Francois; Kundaje, Anshul; Mathelier, Anthony（单位未在摘要中列出，部分作者隶属挪威奥斯陆大学、美国斯坦福大学等，具体未提供）
- **期刊/预印本平台**：Nucleic Acids Research
- **年份**：2025
- **论文类型**：数据库资源更新（Database Update）
- **领域**：生物信息学 / 转录调控 / 蛋白质-DNA互作
- **关键词**：JASPAR、转录因子、PFM、BPNet、深度学习、ChIP-seq、TF结合位点
- **DOI/arXiv 号**：10.1093/nar/gkaf1209
- **代码**：未提供（pyJASPAR、inMOTIFin、MotifCompendium、tangermeme 为相关工具，均有独立仓库）
- **数据**：JASPAR 2026 数据库（https://jaspar.elixir.no/），CORE 2633 个、UNVALIDATED 1231 个非冗余 profile；DL 集合含 1259 个 BPNet 模型、240 个 TF、353 个 motif pattern
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文是 TF–DNA 结合机制研究中**基准数据库的年度更新**，首次将深度学习模型（BPNet）作为一等公民整合进 JASPAR，为「AI 方法 × TF–DNA 互作」提供**训练好的模型库、解释性 motif 和标准化评测资源**，是连接经典 PFM 表征与深度序列模型的桥梁。

## 02 一句话总结
JASPAR 2026 在扩充经典 PFM 集合（CORE +306、UNVALIDATED +433）的同时，首次整合 1259 个基于人类 ChIP-seq 训练的 BPNet 深度学习模型，通过 TF-MoDISco 解释得到 353 个 motif pattern，为 TF–DNA 互作提供从经典矩阵到深度模型的互补资源。

## 03 研究问题
- **具体问题**：如何在不牺牲 JASPAR 一贯的高质量、人工审核标准的前提下，将深度学习模型（BPNet）及其解释性 motif 整合进数据库，与经典 PFM 表征互补？
- **为什么重要**：PFM 假设位点内各位置独立，无法捕捉相邻碱基互作、间距和方向性等复杂特征；深度模型（如 BPNet）能以碱基分辨率预测 ChIP-seq 信号并揭示协同 motif，但缺乏标准化、可访问的资源库。
- **现有方法不足**：已有数据库（CIS-BP、HOCOMOCO）仅存 PFM/PWM；深度学习模型分散在各论文中，缺乏统一命名、质量控制和解释性输出。
- **精确研究问题**：Can a curated database integrate BPNet models trained on ENCODE ChIP-seq data to provide interpretable TF–DNA binding motifs that complement classical PFMs?

## 04 背景与发展脉络
（标注：以下脉络为「经外部核验」的领域常识，结合本文叙述整理）
1. **经典矩阵时代（2004–2015）**：JASPAR 自 2004 年发布，以 PFM/PWM 为核心表征，人工审核保证质量；局限是位置独立假设，无法建模碱基互作。
2. **机器学习改进（2015–2020）**：Markov 模型、贝叶斯树、梯度提升等被用于改进 motif 发现，但未改变「单一矩阵」的表征范式。
3. **深度学习时代（2020–至今）**：BPNet（Avsec et al., 2021）等 CNN 模型以碱基分辨率预测 ChIP-seq 绑定和染色质可及性，通过 DeepLIFT/TF-MoDISco 提取可解释 motif，能捕捉协同结合、间距偏好等复杂特征。
4. **数据库整合（本文位置）**：JASPAR 2026 首次将 BPNet 模型作为正式集合纳入，与 PFM 并存，提供模型下载、motif 可视化、序列扫描（tangermeme）等一体化接口。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PFM 表征能力有限 | 无法建模相邻碱基互作、motif 间距和方向性 | PFM 假设各位置独立贡献 | Introduction 第 2 段 |
| 深度学习模型分散、不可复现 | 各论文独立训练，缺乏统一命名和质量控制 | 无标准化数据库托管模型 | Results「Deep learning collection」节 |
| 模型解释性不足 | 黑箱模型难以直接用于生物学假设 | 需借助 DeepLIFT/TF-MoDISco 等事后解释工具 | Results「Deep learning collection」节 |
| 人工审核瓶颈 | 11565 个 profile 需人工评估，耗时 | 数据源多样（ChIP-seq、PBM、SMiLE-seq 等），质量参差 | Results「Expansion and update」节 |
| 经典与深度表征割裂 | 用户需在 PFM 和深度模型间手动切换 | 缺乏统一接口 | Results「Deep learning collection」节 |

## 06 核心思想
1. **表面方法**：扩充 CORE/UNVALIDATED PFM 集合，训练 1259 个 BPNet 模型，用 TF-MoDISco 提取 motif，按 TF 聚类为 240 个 summary profile，提供网页交互界面和 API。
2. **核心洞察**：PFM 和深度学习模型不是替代关系，而是互补——PFM 提供可解释、可移植的经典表征，BPNet 提供碱基分辨率预测和协同 motif 发现能力；将两者并置可让用户根据任务选择合适工具。
3. **可能的普适教训** [Analysis]：数据库的价值不仅在于存储数据，更在于**标准化工作流**（训练→解释→聚类→质控→发布）的固化；将「模型」作为数据库一等公民，是计算资源向可复用基础设施转化的范例。

## 07 方法总览
- **输入**：ENCODE 人类 TF ChIP-seq 数据集（每个数据集对应一个 BPNet 模型）；外部数据库（HOCOMOCO、ModERN、CIS-BP、Codebook/GRECO-BIT、CAP-SELEX）的 PFM 数据。
- **输出**：CORE 2633 个、UNVALIDATED 1231 个 PFM profile；DL 集合 1259 个 BPNet 模型、240 个 TF summary profile、353 个 motif pattern（含 PFM 和 CWM 两种矩阵表示）。
- **模块**：① 人工审核流程（PFM 质控）；② BPNet 训练（每个 ChIP-seq 数据集一个模型）；③ DeepLIFT 贡献分数计算；④ TF-MoDISco motif 发现；⑤ MotifCompendium 跨数据集聚类；⑥ 质控（与体外实验证据比对）；⑦ 网页接口与 API。
- **训练**：BPNet 为已有架构（Avsec et al.），本文未重新设计，仅应用并标准化。
- **反馈回路**：motif 与已有 PFM 匹配，用于验证模型解释的可靠性。
- **工具**：inMOTIFin（序列模拟）、pyJASPAR（Python 访问）、R/Bioconductor 包、tangermeme（序列扫描）。
- **文字流程**：从 ENCODE 获取 ChIP-seq → 对每个数据集训练 BPNet → 用 DeepLIFT 计算贡献分数 → 用 TF-MoDISco 从贡献分数中提取 motif → 用 MotifCompendium 将同一 TF 的 motif 聚类 → 质控（与体外数据比对）→ 发布为 DL 集合，同时保留经典 PFM 集合。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| BPNet 模型训练 | 碱基分辨率预测 ChIP-seq 绑定信号 | 捕捉 PFM 无法建模的序列特征 | 输入：DNA 序列；输出：预测的 ChIP-seq 信号 | Results「Deep learning collection」节 | 失去深度预测能力，退回 PFM 的独立位置假设 |
| DeepLIFT 贡献分数 | 归因每个碱基对预测的贡献 | 使黑箱模型可解释 | 输入：BPNet 模型+序列；输出：贡献分数矩阵 | Results「Deep learning collection」节 | 无法定位关键碱基，模型不可解释 |
| TF-MoDISco motif 发现 | 从贡献分数中提取重复出现的序列模式 | 将模型知识转化为可读 motif | 输入：贡献分数；输出：motif 集合 | Results「Deep learning collection」节 | 无法从模型中提取 motif，模型沦为纯预测工具 |
| MotifCompendium 聚类 | 跨数据集合并同一 TF 的 motif | 处理同一 TF 多个数据集导致的冗余 | 输入：TF-MoDISco motif；输出：聚类后的 summary motif | Results「Deep learning collection」节 | 同一 TF 出现多个高度相似 motif，用户难以选择 |
| 质控流程 | 与体外实验证据比对 | 确保 motif 反映真实结合偏好 | 输入：聚类 motif+体外数据；输出：通过/不通过标记 | Results「Deep learning collection」节 | 低质量 motif 混入，误导用户 |
| inMOTIFin 模拟 | 生成带已知 ground truth 的调控序列 | 支持方法评测和基准测试 | 输入：PFM/参数；输出：模拟序列+注释 | Results「JASPAR-associated tools」节 | 失去合成数据生成能力，难以进行受控实验 |
| LLM TF-target 提取 | 从文献提取 TF-靶基因关系 | 补充 TF 功能注释 | 输入：文献句子；输出：TF-target 关系 | Results「LLM-based TF-target」节 | 失去功能注释，仅剩序列结合信息 |

## 09 关键公式符号
本文为数据库资源论文，未提供新的数学模型或公式。核心概念涉及：
- **PFM**（Position Frequency Matrix）：每个位置各碱基的计数矩阵。
- **PWM**（Position Weight Matrix）：由 PFM 转换的对数似然矩阵。
- **CWM**（Contribution Weight Matrix）：本文引入的概念，类似 PFM 但元素为 DeepLIFT 贡献分数聚合值，用于表示深度模型学到的 motif。
- **BPNet**：基于 CNN 的架构，输出为碱基分辨率的预测信号（如 ChIP-seq 计数），损失函数通常为 Poisson 负对数似然（原文未给出具体公式，属领域常识）。

## 10 实验设计与证据链
- **数据集**：ENCODE 人类 TF ChIP-seq（具体数据集列表未在摘要中提供）；外部 PFM 来源包括 HOCOMOCO、ModERN、CIS-BP、Codebook/GRECO-BIT、CAP-SELEX。
- **规模**：CORE 2633 个 profile（新增 265 个 + 升级 41 个）；UNVALIDATED 1231 个（新增 421 个）；DL 集合 1259 个 BPNet 模型、240 个 TF、353 个 motif pattern。
- **指标**：模型性能指标见 Supplementary Fig. S2（具体数值未在摘要中提供）；LLM 提取准确率 88%（308/350）。
- **基线**：未提供正式基线对比（数据库更新论文，非方法学论文）。
- **评测协议**：人工审核（PFM 质控）；motif 与体外实验证据比对（DL 质控）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|-------------------|------|
| PFM 扩充 | 新增 profile 覆盖更多 TF | 人工审核 11565 个候选 | CORE +306、UNVALIDATED +433 | 数据库覆盖度提升 | 未证明新增 profile 的生物学准确性优于旧版 | Results「Expansion」节 |
| BPNet 训练与解释 | 深度模型可提取可靠 motif | 与体外数据比对 | 240 个 TF 通过质控 | DL 模型可作为 motif 来源 | 未与 PFM 做系统性预测性能对比 | Results「DL collection」节 |
| LLM TF-target 提取 | LLM 可从文献提取 TF-target 关系 | 人工审核 350 条 | 准确率 88% | LLM 可用于自动化注释 | 未评估召回率；仅限人类 TF | Results「LLM-based TF-target」节 |

## 11 结论正确解读
- **任务范围**：本文是数据库资源更新，不提出新算法，不进行端到端预测性能评测。
- **oracle/真值输入**：DL 集合的质控依赖体外实验证据（如 SELEX、PBM）作为真值，但具体匹配阈值未在摘要中提供。
- **端到端状态**：BPNet 模型可下载使用，但未提供「从序列到功能注释」的完整端到端流程。
- **算力成本**：未提供训练成本信息。
- **历史数据依赖**：DL 集合仅覆盖人类 TF，其他物种未包含。
- **模型依赖**：DL 集合仅含 BPNet 架构，不涵盖其他深度模型（如 Enformer、Basenji）。
- **最难情形**：同一 TF 的多个数据集可能产生不一致的 motif；低表达或弱结合 TF 的 ChIP-seq 信号可能不足以训练可靠模型。
- **群体/领域边界**：结论仅适用于人类 TF–DNA 结合，不适用于其他物种或其他 DNA 结合蛋白（如组蛋白、聚合酶）。
- **不确定性**：LLM 提取的 TF-target 关系准确率 88%，存在 12% 错误率；DL motif 的生物学意义需用户自行验证。
- **有边界的复述**：JASPAR 2026 提供了扩充的 PFM 集合和首个整合的 BPNet 深度模型库，后者经 TF-MoDISco 解释并质控，可作为人类 TF–DNA 结合研究的补充资源，但未证明其在预测性能上优于经典 PFM。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| DL 集合仅限人类 | 仅包含 Homo sapiens ChIP-seq 训练的模型 | 计划扩展至其他物种和 taxa | Conclusions 节 |
| LLM 提取存在错误 | 准确率 88%，12% 错误 | 未来将改进提示词和验证流程 | Results「LLM-based TF-target」节 |
| 人工审核瓶颈 | 11565 个 profile 需人工评估 | 期望 LLM 辅助自动化审核 | Conclusions 节 |
| 深度模型解释依赖体外数据 | motif 质控依赖体外实验证据 | 未明确说明 | Results「DL collection」节 |

**作者提及的相关约束**（非正式局限）：DL 集合的 motif 与 PFM 的匹配用于验证，但未提供匹配算法细节；模型训练的具体超参数和数据集版本未在摘要中详述。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| DL 集合仅含 BPNet 架构 | 其他架构（如 Enformer、Basenji）可能表现更好或互补 | 用户可能误以为 BPNet 是唯一选择 | 在相同数据集上对比多种架构的预测性能 | Results「DL collection」节 |
| 质控依赖体外数据 | 体外结合 ≠ 体内结合，可能遗漏染色质上下文效应 | 影响 motif 的生物学可靠性 | 与体内 ChIP-seq 或 CRISPR 扰动数据对比 | Results「DL collection」节 |
| LLM 提取仅限人类 | 其他物种的 TF-target 关系未覆盖 | 限制数据库的通用性 | 扩展至模式生物 | Results「LLM-based TF-target」节 |
| 未提供模型预测性能对比 | 未说明 BPNet 是否优于 PFM 扫描 | 用户无法判断何时该用哪种资源 | 在标准基准（如 ENCODE 测试集）上对比 AUPRC | 全文未提供 |
| 人工审核标准未量化 | 未说明「正交支持」的具体定义和阈值 | 影响 CORE/UNVALIDATED 分类的可重复性 | 检查审核指南和评分标准 | Results「Expansion」节 |

## 14 学到什么
**Agent 提炼的知识候选**（面向 TF–DNA 互作 × AI/物理模拟课题）：
1. **模型-解释-聚类-质控的标准化流水线**：BPNet→DeepLIFT→TF-MoDISco→MotifCompendium→体外验证，可作为「从深度模型提取可解释 motif」的模板，迁移到其他物种或细胞类型。
2. **CWM 作为新表征**：将贡献分数聚合成类似 PFM 的矩阵，为「深度模型输出 → 经典格式」的转换提供思路，可用于与现有 PFM 工具链兼容。
3. **PFM 与 DL 互补的数据库设计**：将经典矩阵和深度模型并置，让用户按任务选择，提示在构建资源时应考虑多种表征的共存而非替代。
4. **LLM 辅助文献挖掘**：用 ChatGPT-5 提取 TF-target 关系并人工审核，展示了 LLM 在生物注释中的可行性和错误率（12%），可作为自动化注释的参考基线。
5. **多数据集 per-TF 建模**：同一 TF 的多个 ChIP-seq 数据集分别训练模型再聚类，可处理批次效应和细胞类型特异性，迁移到 MD 模拟或多构象分析时可按构象/条件分别建模再整合。
6. **inMOTIFin 的 ground-truth 模拟**：生成已知插入位点的调控序列，可用于评测 motif 发现工具或作为深度学习模型的训练/验证数据，迁移到物理模拟中可设计带已知结合位点的序列进行 MD 验证。

## 15 与已有知识连接
- **JASPAR 历史版本**：JASPAR 2024/2022（Rauluseviciute et al., 2024; Castro-Mondragon et al., 2022）——本文为连续更新，CORE/UNVALIDATED 划分和人工审核流程延续自前版。
- **BPNet 原始论文**：Avsec et al., 2021, Nature Genetics——本文直接应用其架构和解释方法，未做修改。
- **TF-MoDISco**：Shrikumar et al., 2018, Bioinformatics——用于从贡献分数中提取 motif，本文沿用。
- **DeepLIFT**：Shrikumar et al., 2017——归因方法，本文用于计算贡献分数。
- **ENCODE 项目**：ENCODE Project Consortium, 2012——ChIP-seq 数据来源。
- **CIS-BP**：Weirauch et al., 2014——PFM 来源之一，与 JASPAR 互补。
- **HOCOMOCO**：Kulakovskiy et al., 2018——PFM 来源之一。
- **ExTRI**：Pavlopoulos et al., 2015——TF-target 文本挖掘资源，本文 LLM 提取的输入。
- **tangermeme**：Kundaje 实验室工具——用于序列扫描，本文集成。
- **候选方向** [Analysis]：本文的 DL 集合可与 AlphaFold 等结构预测工具结合，用于验证预测 motif 的结构基础；CWM 可作为 MD 模拟的初始结合偏好先验。

## 16 研究想法
**Agent 生成的研究候选**（面向 TF–DNA 互作 × AI/物理模拟）：
1. **候选名称**：跨物种 TF–DNA 结合特异性迁移学习
   - **来源局限/观察**：JASPAR DL 集合仅限人类，其他物种缺乏深度模型资源。
   - **核心假设**：同源 TF 的 DNA 结合偏好可跨物种迁移，迁移学习可减少数据需求。
   - **增量**：扩展 DL 集合至模式生物（小鼠、果蝇、拟南芥），用人类模型做预训练。
   - **初步方法**：用 JASPAR 2026 人类 BPNet 权重初始化，在目标物种 ChIP-seq 上微调；评估迁移后 motif 与 PFM 一致性。
   - **验证方式**：与从头训练模型对比 AUPRC；用体外 SELEX 数据验证 motif 准确性。
   - **创新状态**：unverified（领域内已有跨物种 TF 结合预测研究，但未见基于 JASPAR DL 集合的迁移学习）。

2. **候选名称**：CWM 引导的 TF–DNA 分子动力学模拟初始构象选择
   - **来源局限/观察**：CWM 提供碱基级贡献分数，但未与结构信息关联。
   - **核心假设**：高贡献碱基对应直接接触残基，可作为 MD 模拟的约束或初始构象选择依据。
   - **增量**：将深度学习的序列偏好转化为结构模拟的输入，弥合序列-结构鸿沟。
   - **初步方法**：选取 JASPAR DL 集合中高置信 TF，用 CWM 识别关键碱基，与已知 TF–DNA 共晶结构比对；用这些碱基位置引导 MD 模拟的对接构象采样。
   - **验证方式**：MD 模拟的稳定构象与晶体结构 RMSD 对比；预测结合自由能与实验值相关性。
   - **创新状态**：unverified（已有用 PWM 引导 MD 的研究，但 CWM 作为引导信号未见报道）。

3. **候选名称**：TF 协同结合的二聚体 motif 深度预测
   - **来源局限/观察**：JASPAR DL 集合的 motif 聚类主要针对单体，未系统处理二聚体协同。
   - **核心假设**：BPNet 可捕捉间距和方向性特征，可用于预测二聚体 motif 的间距偏好。
   - **增量**：从 1259 个模型中提取二聚体相关特征，构建协同结合预测器。
   - **初步方法**：对同一 TF 的多个 BPNet 模型进行 pairwise 分析，提取间距-方向性特征；用 TF-MoDISco 发现的次级 motif 识别协同位点；与 ChIP-seq 共结合数据验证。
   - **验证方式**：预测的二聚体 motif 与已知晶体结构或生化数据比对；在独立 ChIP-seq 数据集上验证。
   - **创新状态**：partially checked（已有二聚体 motif 预测研究，但基于 JASPAR 2026 大规模模型库的系统分析未见）。

4. **候选名称**：JASPAR DL 集合的变异效应预测基准
   - **来源局限/观察**：DL 集合提供碱基分辨率预测，但未系统评估其在变异效应预测中的表现。
   - **核心假设**：BPNet 的 in silico mutagenesis 可准确预测非编码变异对 TF 结合的影响。
   - **增量**：构建标准基准，对比 BPNet、PWM 扫描和现有变异效应预测工具。
   - **初步方法**：从 JASPAR DL 集合选取 50 个 TF，用 tangermeme 进行 in silico mutagenesis；与 ClinVar、GWAS 中已知致病非编码变异比对；计算 AUROC/AUPRC。
   - **验证方式**：与 MPRA（大规模平行报告基因分析）数据对比。
   - **创新状态**：partially checked（已有 BPNet 变异效应研究，但未见基于 JASPAR 2026 全库的系统基准）。