## 01 基本信息
- **标题**：Chromatin folding principles underlying the generation of antibody diversity
- **作者**：Ollikainen, Noah; Ma, Fei; Braikia, Fatima Zohra; Sen, Ranjan
- **单位**：National Institute on Aging (NIH, Baltimore, MD)（基于致谢推断，具体单位列表未提供）
- **期刊/平台**：Molecular Cell
- **年份**：2026
- **论文类型**：研究论文（结合生物物理模拟与实验数据）
- **领域**：染色质三维结构、V(D)J重组、抗体多样性、环挤压（loop extrusion）机制
- **关键词**：V(D)J recombination, Igh locus, cohesin, loop extrusion, chromatin folding, enhancer, H3K27ac
- **DOI/ID**：10.1016/j.molcel.2025.12.023
- **代码**：polychrom (https://github.com/open2c/polychrom)
- **数据**：GEO: GSE214438, GSE241661, GSE151910, GSE140975, GSE113023
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文聚焦转录因子（Pax5、Yy1）调控下的染色质折叠如何决定TF–DNA互作的可及性，核心机制为cohesin介导的loop extrusion与CTCF/增强子（Eμ）的互作。对「TF–DNA结合机制 × 物理模拟」方向，本文提供了将cohesin动力学、CTCF方向性、增强子阻断效应整合进聚合物模拟的完整范式，可直接迁移至其他TF–DNA互作位点的三维空间调控研究。

## 02 一句话总结
通过polychrom聚合物模拟结合Hi-C、Hi-ChIP、ChIP-seq及VH使用频率数据，本文发现小鼠Igh基因座的三维折叠需要cohesin在全基因座广泛装载、Eμ作为双向loop extrusion阻断器、以及H3K27ac标记区域间的长程互作，三者共同实现VH基因片段与重组中心（RC）的空间接近，从而产生多样化的抗体库。

## 03 研究问题
- **具体问题**：小鼠Igh基因座中，分布在2.5 Mb范围内的约100个VH基因片段如何以大致相当的频率与位于3'端的DJH重组中心（RC）发生重组，从而最大化抗体多样性？
- **为何重要**：V(D)J重组是适应性免疫的基础，理解VH基因片段空间接近RC的机制，对阐明抗体库多样性产生的原理至关重要，也为理解长程基因组互作如何调控基因表达提供范式。
- **现有方法不足**：先前模型（FISH、Hi-C静态结构推断）仅提供静态快照，未纳入loop extrusion等动态过程；RAG扫描模型虽提出单向loop extrusion，但无法解释VH基因片段距离无关的均匀使用。
- **精确研究问题**：Can cohesin loading throughout the Igh locus, combined with Eμ as a bidirectional loop extrusion blocker and H3K27ac-mediated long-range interactions, recapitulate experimentally observed chromatin structure and VH gene usage patterns?

## 04 背景与发展脉络
*（注：以下脉络基于本文引言与讨论，属「仅本文框架」，未经外部系统核验）*

1. **静态结构描述阶段**：FISH实验揭示pro-B细胞中Igh基因座发生"locus contraction"，远端VH区域与3'端空间接近，依赖Pax5、Yy1和Eμ增强子。局限：无法解析分子机制。
2. **loop extrusion理论阶段**：cohesin作为ATP驱动马达，通过loop extrusion建立染色质三维结构，在CTCF结合位点处停滞。Nipbl负责cohesin装载，Wapl介导卸载。局限：对Igh基因座的具体应用仍停留在定性描述。
3. **RAG扫描模型阶段**：提出cohesin从RC单向挤出loop，依次将远端VH基因片段的RSS呈递给RC。局限：无法解释距离无关的VH使用，且未考虑cohesin全基因座装载。
4. **本文动态模拟阶段**：将polychrom模拟与多种实验数据结合，提出cohesin全基因座装载、Eμ双向阻断、H3K27ac互作三原则，动态解释VH基因片段的空间接近与重组频率。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 静态模型无法解释动态过程 | FISH/Hi-C推断的结构无法说明locus contraction如何建立 | 静态结构推断省略了loop extrusion等动态机制 | 引言：先前模型"omitted dynamic processes like loop extrusion" |
| 单向loop extrusion无法解释均匀VH使用 | RAG扫描模型仅能解释近端VH重组 | 单向挤出在遇到CTCF后停滞，无法覆盖远端VH | 引言：单向模型"fails to adequately explain distance independent VH utilization" |
| Eμ增强子缺乏CTCF却影响染色质结构 | Eμ不结合CTCF，但删除后改变3'域结构 | Eμ可能作为非CTCF依赖的loop extrusion阻断器 | Results 图2：Eμ−/−等位基因的Hi-C结构变化 |
| H3K27ac互作机制不明 | 远端VH区域与RC的互作强度不均 | H3K27ac标记区域间的优先互作可能稳定远端接触 | Results 图4：H3K27ac Hi-ChIP显示Eμ与VH区域点状互作 |
| 模拟参数与实验数据匹配困难 | 模拟需同时复现TAD、stripe和VH使用频率 | 需要cohesin装载分布、停留时间、阻断效率等多参数协同 | Results 图1-4：多条件模拟与实验对比 |

## 06 核心思想
1. **表面方法**：使用polychrom软件对2.8 Mb Igh基因座进行聚合物模拟，将cohesin loop extrusion、CTCF方向性阻断、Eμ增强子阻断、H3K27ac互作等生物物理规则编码为模拟参数，生成群体水平的接触图，并与Hi-C、Hi-ChIP、VH使用频率等实验数据对比验证。

2. **核心洞察**：Igh基因座的三维折叠不是由单一机制驱动，而是三个原则协同作用：(1) cohesin需在整个基因座广泛装载，而非仅在RC附近；(2) Eμ虽不结合CTCF，但作为双向loop extrusion阻断器，与CTCF共同塑造3'域结构；(3) H3K27ac标记区域间的优先互作提供额外的长程稳定化，使远端VH基因片段得以接近RC。

3. **可能的普适教训** [Analysis]：增强子等非CTCF调控元件可能通过物理阻断loop extrusion来塑造染色质结构，这一机制可能普遍存在于其他基因座；H3K27ac不仅是活性染色质标记，还可能直接参与三维基因组互作网络。

## 07 方法总览
- **输入**：Igh基因座序列（chr12:113,100,000-116,100,000, mm10，约3 Mb，3000个1 kb单体）、CTCF结合位点位置与方向（来自CTCF ChIP-seq）、H3K27ac标记分布（来自H3K27ac ChIP-seq）、cohesin装载/停留/卸载参数、Eμ位置
- **输出**：群体水平接触图（模拟Hi-C）、每个VH基因片段与RC的平均接触时间（作为重组频率的代理指标）
- **模块**：
  1. 1D loop extrusion模拟：cohesin沿聚合物的线性运动、CTCF/Eμ阻断、停留时间
  2. 3D分子动力学模拟：使用OpenMM计算聚合物三维构象
  3. 接触图生成：定义接触阈值（6个单体直径单位），聚合10,000次模拟
  4. VH-RC接触时间计算：在1,000次模拟中统计每个VH基因片段与RC（2个直径单位内）的接触时间
  5. H3K27ac互作模块：当VH基因片段带H3K27ac标记且cohesin同时结合RC和该VH区域时，增强其互作
- **训练**：非传统训练，通过调整cohesin装载分布、停留时间、Eμ阻断模式等参数，使模拟接触图与实验Hi-C/Hi-ChIP数据匹配
- **反馈回路**：模拟结果与实验数据对比，参数迭代调整
- **假设**：VH重组频率与VH-RC空间接触时间成正比；cohesin行为可用简化概率模型描述；H3K27ac互作可通过接触增强规则近似

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 1D loop extrusion模拟 | 模拟cohesin沿聚合物的线性运动与阻断 | 建立cohesin轨迹，决定loop大小与范围 | 输入：cohesin装载位置、CTCF/Eμ位置与方向；输出：cohesin运动轨迹 | Results 图1D：cohesin装载分布影响TAD结构 | [预期] 移除后无法生成loop结构，TAD消失 |
| CTCF方向性阻断 | 模拟cohesin在CTCF位点的停滞 | CTCF是已知的loop extrusion主要阻断因子 | 输入：CTCF位点位置与方向；输出：cohesin停滞位置 | Results 图1C：3'CBE锚定的stripe | [预期] 移除后stripe消失，TAD边界模糊 |
| Eμ双向阻断模块 | 将Eμ模拟为双向loop extrusion阻断器 | Eμ不结合CTCF但影响3'域结构 | 输入：Eμ位置；输出：cohesin在Eμ处双向停滞 | Results 图2D：仅双向阻断模式复现实验结构 | [实测] 单向阻断或非阻断模式无法复现WT结构（图S2） |
| 3D分子动力学模拟 | 计算聚合物三维构象 | 将1D轨迹转化为空间接触 | 输入：1D cohesin轨迹、聚合物力学参数；输出：三维构象轨迹 | Methods：使用OpenMM | [预期] 移除后无法生成接触图 |
| 接触图生成 | 聚合模拟结果生成群体接触图 | 与实验Hi-C数据对比验证 | 输入：10,000次模拟的三维构象；输出：模拟接触图 | Results 图1C：模拟与实验接触图对比 | [预期] 移除后无法与实验数据定量比较 |
| VH-RC接触时间计算 | 统计每个VH基因片段与RC的接触时间 | 作为重组频率的代理指标 | 输入：1,000次模拟轨迹；输出：每个VH基因片段的平均接触时间 | Results 图3：模拟VH使用与实验对比 | [预期] 移除后无法预测VH重组频率 |
| H3K27ac互作模块 | 增强H3K27ac标记区域与RC的互作 | 远端VH基因片段需要额外稳定化 | 输入：H3K27ac ChIP-seq标记、cohesin结合状态；输出：增强的VH-RC接触 | Results 图4：H3K27ac Hi-ChIP显示点状互作 | [实测] 移除后远端VH基因片段使用频率下降（图4D） |

## 09 关键公式符号
本文为模拟研究，未提供显式数学公式。核心参数与符号如下：

- **cohesin停留时间**：平均停留时间2500步（Wapl抑制）或250步（Wapl未抑制），用于模拟pro-B细胞与细胞系差异
- **cohesin阻断概率**：CTCF位点90%概率阻断，0.003%/步的旁路概率（平均停滞约333步）
- **接触定义**：两个单体距离≤6个单体直径单位视为接触（Hi-C模拟）；VH-RC接触定义为≤2个直径单位
- **VH-RC接触时间**：每个VH基因片段在模拟时间步（10,000-20,000步）内与RC接触的步数比例
- **H3K27ac互作条件**：VH基因片段带H3K27ac标记且cohesin同时结合RC和该VH区域时，增强接触

## 10 实验设计与证据链
- **数据集**：
  - 模拟：polychrom模拟，10,000次（接触图）/1,000次（VH接触时间）
  - 实验：Rag2−/−原代pro-B细胞（GSE214438: Hi-C, Hi-ChIP, ChIP-seq）；D345 pro-B细胞系WT与Eμ−/−（GSE241661）；IGCR−/− pro-B细胞系（本研究新产生）；VH使用频率数据（GSE151910, GSE140975, GSE113023）
- **指标**：接触图相似性、VH基因片段与RC接触时间、VH使用频率
- **基线**：cohesin仅RC装载模型、单向Eμ阻断模型、无H3K27ac互作模型
- **评测协议**：模拟接触图与实验Hi-C/Hi-ChIP对比；模拟VH使用频率与实验VH使用数据对比

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| cohesin装载位置对比 | 全基因座装载优于仅RC装载 | 全基因座装载 vs. 仅RC装载 | 全基因座装载复现TAD和stripe | cohesin需全基因座装载 | 未测试中间装载模式 | Results 图1C-D |
| Eμ阻断模式对比 | Eμ为双向阻断器 | 双向 vs. 单向 vs. 非阻断 | 仅双向阻断复现WT 3'域结构 | Eμ是双向loop extrusion阻断器 | 未测试部分阻断效率 | Results 图2D, 图S2 |
| Eμ−/−模拟 | 删除Eμ后结构变化 | WT vs. Eμ−/−模拟与实验 | 模拟复现实验结构变化 | Eμ对3'域结构至关重要 | 未测试其他增强子 | Results 图2E |
| IGCR1−/−模拟 | 删除IGCR1后结构变化 | WT vs. IGCR1−/−模拟与实验 | 模拟复现实验结构变化 | IGCR1作为CTCF依赖阻断器 | 未测试部分删除 | Results 图2F |
| VH使用频率预测 | 模型预测VH重组频率 | 模拟接触时间 vs. 实验VH使用 | 近端VH匹配；远端需H3K27ac模块 | 空间接近驱动VH重组 | 未纳入RSS强度等参数 | Results 图3 |
| H3K27ac互作模块 | 增强远端VH使用 | 有 vs. 无H3K27ac互作模块 | 有模块时远端VH使用更均匀 | H3K27ac互作稳定远端接触 | 未测试其他组蛋白修饰 | Results 图4C-D |
| 大片段倒位模拟 | 验证模型预测倒位效应 | WT vs. 2.4 Mb倒位 vs. 890 kb倒位 | 模拟复现实验VH使用模式 | 模型可预测倒位突变效应 | 未测试其他倒位 | Results 图5 |

## 11 结论正确解读
- **任务范围**：本文仅针对小鼠Igh基因座在pro-B细胞中的三维折叠与VH重组频率，不涉及其他抗原受体位点（如Igk、Tcrb）的定量预测。
- **oracle/真值输入**：模拟使用了实验测定的CTCF结合位点位置与方向、H3K27ac ChIP-seq标记，这些是实验输入而非模型预测。
- **端到端状态**：模型从序列和表观遗传标记出发，预测三维结构和VH使用频率，但VH使用频率的预测仅基于空间接触时间，未纳入RSS序列强度、基因转录活性等已知影响重组频率的因素。
- **算力成本**：未提供具体计算资源与时间。
- **历史数据依赖**：模拟参数（cohesin停留时间、阻断概率）部分来自文献（Nuebler et al.），部分为默认值，未系统校准。
- **模型依赖**：结果依赖polychrom的loop extrusion实现，不同模拟框架可能产生差异。
- **最难情形**：远端VH基因片段（>1 Mb）的均匀使用需要H3K27ac互作模块，该模块的机制基础（如何实现H3K27ac区域间互作）尚未实验验证。
- **群体/领域边界**：结论基于pro-B细胞，其他发育阶段或细胞类型中cohesin装载、Eμ阻断效率可能不同。
- **不确定性**：模拟与实验的定量匹配程度未提供统计检验；VH使用频率预测的误差范围未报告。
- **有边界的复述**：在小鼠pro-B细胞中，Igh基因座的三维折叠需要cohesin全基因座装载、Eμ双向阻断loop extrusion、以及H3K27ac标记区域间的长程互作，这些机制共同使远端VH基因片段接近RC，从而解释实验观察到的VH使用模式。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| cohesin数量未知 | 活细胞中Igh等位基因上cohesin复合物的确切数量未知 | 未明确提及 | Limitations of the Study |
| cohesin装载位点未知 | Igh TAD中cohesin的优先装载位点不清楚 | 未明确提及 | Limitations of the Study |
| VH重组限速步骤简化 | 模型假设重组频率仅由空间接触时间决定 | 需纳入RSS强度、VH启动子活性等因素 | Limitations of the Study |
| H3K27ac互作机制不明 | H3K27ac标记区域间如何实现优先互作尚不清楚 | 未明确提及 | Limitations of the Study |
| RSS捕获机制未建模 | 空间接近后的RSS捕获、突触复合物形成等未纳入模型 | 需在模型中整合RAG介导的捕获机制 | Limitations of the Study |

**作者提及的相关约束**（非正式局限）：模拟参数（cohesin停留时间、阻断概率）部分来自文献默认值，未针对Igh基因座系统校准；H3K27ac互作模块的规则是启发式的，缺乏独立实验验证。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| Eμ双向阻断的机制基础 | 作者假设Eμ不结合CTCF但双向阻断loop extrusion，但未提供Eμ阻断cohesin的分子机制证据 | 若Eμ阻断机制不成立，3'域结构模型需重新解释 | 体外单分子实验检测cohesin在Eμ处的停滞；或Eμ突变体（保留增强子活性但改变序列）的Hi-C分析 | Results 图2D；Discussion |
| H3K27ac互作模块的因果性 | H3K27ac与互作增强的关联可能是伴随现象而非因果关系 | 若H3K27ac仅是活性染色质的标记，而非互作媒介，模型机制需修正 | 去除H3K27ac阅读器（如Brd4）后检测VH使用频率；或H3K27ac位点定向突变 | Results 图4；Discussion |
| 模拟与实验的定量匹配 | 作者未提供模拟与实验接触图的定量相似性指标（如相关性系数） | 缺乏定量评估难以判断模型预测精度 | 计算模拟与实验接触图的Spearman相关系数或结构相似性指数 | Results 图1-4 |
| VH使用频率预测的简化 | 仅用空间接触时间预测重组频率，未纳入RSS强度、基因表达等已知因素 | 可能高估空间接近的作用，低估其他因素 | 在模型中纳入RSS强度参数，比较预测精度变化 | Results 图3；Limitations |
| 倒位模拟的验证范围 | 仅测试了两个倒位突变，样本量有限 | 模型对更复杂重排（如缺失、重复）的预测能力未知 | 测试更多突变类型，与实验VH使用数据对比 | Results 图5 |
| cohesin装载的均匀性假设 | 模拟假设cohesin均匀装载，但实际可能存在装载偏好 | 装载偏好可能改变loop结构预测 | 使用Nipbl ChIP-seq数据指导cohesin装载分布 | Methods |

## 14 学到什么
**Agent 提炼的知识候选**

1. **增强子作为loop extrusion阻断器的概念**：Eμ不结合CTCF但双向阻断cohesin，这一发现提示增强子可能通过物理阻断loop extrusion来塑造三维基因组结构。**迁移**：在研究TF–DNA结合时，可检验TF结合位点（尤其是增强子区域）是否也作为loop extrusion阻断器，影响远端调控元件的互作频率。

2. **cohesin装载分布决定TAD结构的模拟方法**：通过对比全基因座装载与局部装载的模拟结果，确定cohesin装载模式对三维结构的影响。**迁移**：在模拟TF–DNA互作时，可系统变化cohesin装载分布、停留时间等参数，探索不同细胞类型或发育阶段中TF结合位点可达性的变化。

3. **H3K27ac介导的长程互作增强规则**：将H3K27ac标记区域间的优先互作编码为模拟规则，成功预测远端VH基因片段的使用。**迁移**：在预测TF–DNA结合时，可将H3K27ac或其他组蛋白修饰作为长程互作的增强因子，纳入三维基因组模型。

4. **空间接触时间作为重组频率代理指标**：用VH基因片段与RC的接触时间预测重组频率，避免了复杂的生化反应建模。**迁移**：在研究TF–DNA结合时，可用TF结合位点与目标基因启动子的空间接触时间作为结合频率的代理指标，简化计算。

5. **倒位突变作为模型验证工具**：通过模拟大片段倒位并预测VH使用模式，验证模型对基因组重排的预测能力。**迁移**：在设计TF–DNA互作模型时，可利用天然或工程化的基因组倒位/易位突变作为验证集。

6. **多尺度模拟框架（1D loop extrusion + 3D MD）**：将cohesin线性运动与聚合物三维构象分离模拟，提高计算效率。**迁移**：在模拟TF–DNA互作时，可先计算一维cohesin/CTCF动态，再映射到三维空间，避免全原子模拟的高计算成本。

## 15 与已有知识连接
- **cohesin loop extrusion机制**：与Davidson et al. (2019) 和Kim et al. (2019) 的体外单分子实验一致，本文将其应用于Igh基因座的三维结构模拟。
- **CTCF方向性阻断**：与de Wit et al. (2015) 和Rao et al. (2014) 的Hi-C研究一致，CTCF位点的方向性决定loop extrusion阻断效率。
- **增强子-启动子互作**：与Chen et al. (2018) 的Hi-ChIP研究一致，H3K27ac标记区域间的互作可能介导增强子功能。
- **V(D)J重组三维调控**：与Lin et al. (2015) 和Hu et al. (2015) 的FISH研究一致，locus contraction依赖Pax5和Yy1。
- **RAG扫描模型**：与Dai et al. (2021) 的模型一致，但本文提出cohesin全基因座装载而非仅RC装载。
- **polychrom模拟框架**：与Nuebler et al. (2018) 的loop extrusion模拟一致，本文扩展了Eμ阻断和H3K27ac互作模块。
- **候选方向** [Analysis]：本文的Eμ双向阻断机制可能与其他已知的non-CTCF loop extrusion阻断因子（如YY1、TFIIIC）相关，值得系统比较。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：TF结合位点作为loop extrusion阻断器的系统鉴定
   - **来源局限/观察**：本文发现Eμ（不结合CTCF的增强子）双向阻断loop extrusion，提示其他TF结合位点可能具有类似功能。
   - **核心假设**：在哺乳动物基因组中，除CTCF外，特定TF（如YY1、GATA1）结合位点可作为loop extrusion阻断器，影响三维基因组结构。
   - **初步方法**：利用polychrom模拟，将候选TF结合位点编码为阻断器，与Hi-C数据对比；结合TF ChIP-seq和Hi-C的联合分析。
   - **验证方式**：CRISPR删除或突变TF结合位点后检测Hi-C接触变化；单分子实验验证cohesin在TF结合位点的停滞。
   - **创新状态**：unverified

2. **候选名称**：H3K27ac互作强度与TF–DNA结合频率的定量关系
   - **来源局限/观察**：本文用H3K27ac互作模块预测VH使用频率，但未定量分析互作强度与结合频率的关系。
   - **核心假设**：H3K27ac标记区域的互作强度与TF–DNA结合频率呈正相关，且可通过模拟定量预测。
   - **初步方法**：在polychrom中系统变化H3K27ac互作强度参数，与实验VH使用频率拟合；扩展到其他基因座。
   - **验证方式**：使用CRISPRa/dCas9-p300增强H3K27ac后检测目标基因表达和三维接触变化。
   - **创新状态**：unverified

3. **候选名称**：cohesin装载分布对TF–DNA可及性的影响
   - **来源局限/观察**：本文发现cohesin全基因座装载是Igh三维结构的关键，但未系统探索装载分布变化对TF结合的影响。
   - **核心假设**：cohesin装载分布的变化（如Nipbl突变）通过改变loop extrusion模式，影响TF–DNA结合的可及性。
   - **初步方法**：模拟不同cohesin装载分布，计算TF结合位点的空间可及性；与Nipbl敲除细胞的ATAC-seq和ChIP-seq数据对比。
   - **验证方式**：Nipbl条件敲除小鼠的pro-B细胞中进行Hi-C和VH使用频率分析。
   - **创新状态**：unverified

4. **候选名称**：倒位突变作为TF–DNA互作模型验证平台
   - **来源局限/观察**：本文用倒位突变验证模型预测，但仅测试了两个位点。
   - **核心假设**：系统性的倒位突变文库可用于验证三维基因组模型的预测能力，并揭示TF–DNA互作的方向性依赖。
   - **初步方法**：在Igh或其他基因座构建系列倒位突变，模拟预测VH使用频率，与实验数据对比。
   - **验证方式**：CRISPR/Cas9构建倒位突变细胞系，进行VH使用频率和Hi-C分析。
   - **创新状态**：unverified

5. **候选名称**：增强子阻断loop extrusion的通用机制研究
   - **来源局限/观察**：本文提出Eμ双向阻断loop extrusion，但机制不清（可能涉及Pol II、Brd4或其他因子）。
   - **核心假设**：增强子通过招募特定蛋白复合物（如Brd4、Pol II）物理阻断cohesin，这一机制在多个基因座中保守。
   - **初步方法**：比较多个增强子（Eμ、Eκ、Eβ）的loop extrusion阻断能力；鉴定阻断所需的最小序列和蛋白因子。
   - **验证方式**：体外单分子实验检测cohesin在增强子序列上的停滞；Brd4抑制剂处理后的Hi-C分析。
   - **创新状态**：unverified