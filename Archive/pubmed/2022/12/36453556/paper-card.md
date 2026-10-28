## 01 基本信息
- **标题**：Impact of Asp/Glu-ADP-ribosylation on protein-protein interaction and protein function
- **作者与单位**：Pei, Jimin; Zhang, Jing; Wang, Xu-Dong; Kim, Chiho; Yu, Yonghao; Cong, Qian（美国德州大学西南医学中心，UT Southwestern Medical Center）
- **期刊/预印本平台**：Proteomics
- **年份**：2022-12-02（在线发表）
- **论文类型**：研究论文（Research Article）
- **领域**：蛋白质翻译后修饰（PARylation）× 蛋白质-蛋白质互作（PPI）× 结构预测（AlphaFold）
- **关键词**：ADP-ribosylation, AlphaFold, protein-protein interaction, PARylation, post-translational modification
- **DOI/arXiv 号**：10.1002/pmic.202200083
- **代码**：未提供
- **数据**：预测复合物结构模型可在 https://conglab.swmed.edu/DE_PARylation/ 下载
- **阅读日期**：未提供
- **在「蛋白质-DNA互作(聚焦TF–DNA结合机制) × AI方法/物理模拟」方向中的位置**：本文不直接研究蛋白质-DNA互作，而是研究PARylation修饰对蛋白质-蛋白质互作界面的影响。但其核心方法论——利用AlphaFold基于共进化信号大规模预测PPI界面、将PTM位点映射到界面结构上——可直接迁移到TF-DNA结合机制研究：用AlphaFold预测TF与DNA结合域/辅因子复合物结构，将PTM位点映射到DNA结合界面，推断修饰对结合亲和力与特异性的调控。

## 02 一句话总结
本文用AlphaFold对360个含Asp/Glu-PARylation位点的人源蛋白进行大规模PPI预测（5,361对中260对高置信），将修饰位点映射到预测复合物界面，发现D/E-PARylation位点偏好位于无序区/卷曲区且约1/4预测PPI界面含修饰位点，提示PARylation通过空间位阻和静电改变调控PPI组装，尤其在RNA加工和DNA损伤应答复合物中。

## 03 研究问题
- **具体问题**：D/E-PARylation（天冬氨酸/谷氨酸残基上的ADP-核糖基化）如何通过影响蛋白质-蛋白质互作界面来调控蛋白质功能？
- **为什么重要**：PARylation在DNA损伤应答、转录调控、RNA加工等关键过程中发挥核心作用，但此前研究多聚焦于PARylation对酶活性的直接调控，缺乏对PPI界面层面系统性影响的结构视角。
- **现有方法不足**：实验解析PTM修饰后复合物结构困难；传统PPI预测方法（如对接）精度有限；缺乏将PTM位点与PPI界面关联的大规模结构分析方法。
- **精确研究问题**：Can AlphaFold-based coevolution-driven PPI prediction, combined with PTM site mapping onto predicted interfaces, reveal whether D/E-PARylation sites are preferentially located at protein-protein interaction interfaces and thus modulate complex assembly?

## 04 背景与发展脉络
*标注：以下脉络为「经外部核验」的领域通识，结合本文框架。*

1. **阶段一：PARylation位点鉴定（生化/质谱时代）**——通过质谱方法大规模鉴定PARylation底物和位点。代表：Zhang et al. 2013; Martello et al. 2016; 本文作者前期工作[25,26]。优点：提供真实修饰位点；局限：缺乏结构上下文，无法判断位点是否位于功能界面。
2. **阶段二：单复合物结构解析（实验结构生物学）**——X射线晶体学、冷冻电镜解析PARylation相关复合物。优点：原子级精度；局限：通量低，难以覆盖PTM修饰后的动态构象。
3. **阶段三：基于共进化的深度学习结构预测（AlphaFold时代）**——AlphaFold2[24]利用MSA共进化信息预测单体和复合物结构。优点：可大规模预测PPI；局限：对无序区、PTM修饰、构象变化不敏感。
4. **本文位置**：将阶段一的PTM位点数据与阶段三的AlphaFold预测结合，首次在蛋白质组尺度上系统分析D/E-PARylation位点与PPI界面的空间关系，填补了PTM功能注释的结构空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PTM位点缺乏结构上下文 | 已知数百个PARylation位点，但无法判断其功能重要性 | 实验解析每个修饰后复合物结构不现实；传统结构预测精度不足 | Introduction: "Mapping D/E-PARylation sites onto the 3D structures of these PPIs allowed us to identify PARylation sites residing on the PPI interfaces" |
| 高通量PPI数据噪声大 | 数据库PPI假阳性率高，难以聚焦功能相关互作 | 大规模实验（亲和纯化-质谱）存在非特异结合 | Methods: 使用文献支持度加权评分筛选5,859个高置信PPI |
| AlphaFold对无序区预测不可靠 | 修饰位点偏好无序区，而AlphaFold对无序区结构预测置信度低 | AlphaFold训练数据以有序结构域为主 | Results: D/E-PARylation位点pLDDT显著低于平均水平（mean 59.6 vs 62.7） |
| 修饰对界面影响机制不明 | 无法判断PARylation是破坏还是增强PPI | 缺乏修饰后复合物结构；PAR聚合物长度和分支可变 | Discussion: "The PAR moiety could sterically disrupt PPIs...the negative charges on the PAR moiety near the interaction interface may stabilize or destabilize the interactions" |

## 06 核心思想
1. **表面方法**：收集360个D/E-PARylated蛋白（1,215个位点），从公共数据库整合72,431个候选PPI，经文献支持度加权筛选出5,859个高置信PPI，其中5,361对用AlphaFold建模，以接触概率>0.9为阈值得到260个高置信PPI，再将修饰位点映射到预测界面上。
2. **核心洞察**：D/E-PARylation位点并非随机分布，而是偏好位于蛋白质的卷曲区和无序区，这些区域恰恰是短线性基序（SLiMs）介导PPI的热点区域。将修饰位点映射到预测复合物结构后，约1/4的PPI界面含有修饰位点，提示PARylation通过在界面处引入大体积、高负电荷的ADP-核糖聚合物，以空间位阻和静电排斥方式调控复合物组装。
3. **可能的普适教训 [Analysis]**：PTM位点的功能重要性不能仅看序列保守性或修饰丰度，而应结合结构上下文判断——位于PPI界面的修饰位点即使保守性低，也可能具有重要调控功能。这一"PTM-结构-功能"整合分析范式可推广到其他PTM类型（磷酸化、乙酰化、SUMO化等）和其他互作类型（蛋白-DNA、蛋白-RNA）。

## 07 方法总览
- **输入**：(1) 360个D/E-PARylated人源蛋白及其1,215个修饰位点（来自前期质谱数据[25,26]）；(2) 来自BIOGRID、IntAct、DIP、MINT数据库的72,431个候选PPI；(3) 真核生物蛋白质组序列库（用于构建MSA）。
- **处理流程**：
  1. 文献支持度加权评分筛选候选PPI → 5,859个高置信PPI；
  2. 对5,361个PPI对构建联合MSA（OrthoDB直系同源组 + 真核蛋白质组搜索）；
  3. AlphaFold建模复合物结构（引入200残基连接肽）；
  4. 计算链间接触概率矩阵，取最高值为PPI置信度；
  5. 阈值>0.9 → 260个高置信PPI（294个结构域级互作）；
  6. 将D/E-PARylation位点映射到预测界面（接触概率>0.5的残基对）；
  7. 对高置信PPI网络进行功能聚类分析（Cytoscape + Glay）。
- **输出**：260个高置信PPI的结构模型、69个含修饰位点的PPI界面、功能聚类网络图。
- **训练**：无（AlphaFold为预训练模型，本文仅做推理）。
- **反馈回路**：无（单轮预测，无迭代优化）。
- **假设**：(1) 共进化信号可反映真实PPI；(2) AlphaFold接触概率>0.9对应真实互作；(3) 修饰位点映射到预测界面可反映体内情况。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 文献支持度加权PPI筛选 | 从72,431个候选PPI中筛选高置信子集 | 大规模数据库PPI假阳性率高，直接建模浪费算力且噪声大 | 输入：数据库PPI+PubMed文献关联；输出：5,859个高置信PPI | Methods节：支持度评分=Σ(1/文献关联PPI数) | 预期：假阳性率上升，AlphaFold高置信PPI数量下降 [预期效应] |
| 联合MSA构建 | 为每对蛋白生成共进化信号 | AlphaFold依赖MSA中的共进化信息预测链间接触 | 输入：两个蛋白序列+OrthoDB直系同源组；输出：联合MSA | Methods节：排除ZNF-C2H2等旁系同源过多家族 | 预期：无MSA则AlphaFold无法预测链间接触 [预期效应] |
| AlphaFold复合物建模 | 预测PPI三维结构和链间接触概率 | 提供结构上下文以判断修饰位点是否位于界面 | 输入：联合MSA+序列；输出：复合物结构+接触概率矩阵 | Methods节：200残基连接肽策略；Results节：260个高置信PPI | 实测：无法建模的498对（8.5%）因MSA或显存限制被排除 [实测效应] |
| 修饰位点-界面映射 | 判断D/E-PARylation位点是否位于PPI界面 | 核心科学问题：修饰是否影响互作 | 输入：修饰位点列表+预测复合物结构；输出：69个含修饰位点的界面 | Results节：约1/4高置信PPI界面含修饰位点 | 预期：无此模块则无法回答核心问题 [预期效应] |
| 功能聚类分析 | 将高置信PPI网络分为功能相关模块 | 识别PARylation调控的生物学通路 | 输入：260个PPI网络；输出：功能聚类（DNA修复、RNA加工等） | Results节图2：主要聚类涉及DNA损伤修复、RNA加工 | 预期：无法系统总结PARylation的功能影响 [预期效应] |

## 09 关键公式符号
本文无显式数学公式。核心定量指标定义如下：

- **接触概率（contact probability）**：AlphaFold输出的Cβ-Cβ距离分布中，距离<12Å的概率之和。对链间残基对(i,j)，$P_{ij}^{contact} = \sum_{b: d_b < 12Å} p_{ij}(b)$，其中$p_{ij}(b)$为残基对(i,j)落入距离箱b的概率。PPI置信度取所有链间残基对的最大接触概率。
- **文献支持度评分**：$S_{PPI} = \sum_{p \in P} \frac{1}{N_p}$，其中P为支持该PPI的文献集合，$N_p$为文献p中报道的PPI总数。筛选阈值：单篇文献支持时$S \geq 0.1$；多篇文献支持时$S \geq 0.01$。
- **界面残基定义**：接触概率>0.5的链间残基对。

## 10 实验设计与证据链
- **数据集**：360个D/E-PARylated人源蛋白（1,215个位点），来自前期质谱研究[25,26]；72,431个数据库PPI；5,859个高置信PPI；5,361对经AlphaFold建模。
- **指标**：AlphaFold接触概率（阈值0.9为高置信，0.5为界面残基）。
- **基线**：无显式基线模型；以实验验证的PPI（98个有实验结构支持）作为间接验证。
- **评测协议**：无独立测试集；通过已知实验结构（如PCNA-PIP盒复合物）进行定性验证。
- **算力预算**：未提供。
- **oracle输入**：无（AlphaFold为无监督预测，不依赖实验结构模板）。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| D/E-PARylation位点二级结构偏好分析 | 修饰位点偏好卷曲/无序区 | 对比所有Asp/Glu位点 vs 实际修饰位点 | 修饰位点在卷曲区比例显著更高（p<0.04），β-折叠中比例显著更低（p<0.0001） | 修饰位点偏好柔性区域 | 无法区分"修饰导致无序"还是"无序促进修饰" | Results节图1C |
| AlphaFold PPI预测 | 共进化信号可预测PARylated蛋白的PPI | 5,361对建模，接触概率>0.9为阈值 | 260个高置信PPI（4.8%阳性率） | AlphaFold可识别高置信PPI | 无法评估假阴性率（未建模的498对可能含真实PPI） | Results节 |
| 修饰位点-界面映射 | 部分修饰位点位于PPI界面 | 260个高置信PPI中映射修饰位点 | 69个界面含修饰位点（约26.5%） | PARylation可能直接调控PPI | 无法判断体内是否真实发生界面修饰 | Results节 |
| PCNA hub分析 | PCNA通过PIP盒与多种蛋白互作且界面含修饰位点 | 23个PCNA预测PPI，22个含界面修饰位点 | PCNA的D120/D122/E124/E130/D257/E258/E259位于PIP盒结合界面 | PARylation可能调控PCNA的hub功能 | 无实验验证修饰是否影响具体互作 | Results节图3 |
| DDX39B-ALYREF/FYTTD1分析 | RNA输出复合物界面含修饰位点 | AlphaFold预测+修饰位点映射 | ALYREF N端(1-20)和C端(238-257)基序均含修饰位点且位于DDX39B结合界面 | PARylation可能调控mRNA输出 | 无功能实验验证 | Results节图4 |
| ERH-POLDIP3/CIZ1分析 | DNA损伤应答复合物界面含修饰位点 | AlphaFold预测+修饰位点映射 | POLDIP3 E416位于与ERH互作的β-折叠起始处 | PARylation可能调控DNA损伤应答 | 无法判断修饰是增强还是抑制互作 | Results节图5 |
| SUMO2-CHAF1A分析 | PARylation与SUMOylation交叉调控 | AlphaFold预测+修饰位点映射 | SUMO2 E13位于CHAF1A互作界面 | PARylation可能调控SUMO化底物识别 | 仅一个位点，证据有限 | Results节图7D |

## 11 结论正确解读
- **任务范围**：仅覆盖D/E-PARylation（酸性残基上的修饰），不涉及K/R/S/T/Y等其他氨基酸上的ADP-核糖基化；仅分析人源蛋白。
- **oracle/真值输入**：修饰位点来自质谱鉴定（可能存在假阳性/假阴性）；PPI来自数据库+AlphaFold预测（无湿实验验证）。
- **端到端状态**：非端到端验证——从预测到功能结论之间存在多个推断步骤（预测PPI→预测界面→映射位点→推断调控），每一步都有不确定性累积。
- **算力成本**：未报告；AlphaFold建模5,361对蛋白的计算成本未量化。
- **历史数据依赖**：依赖OrthoDB直系同源注释和真核基因组数据库质量；排除ZNF-C2H2等大旁系同源家族可能引入偏差。
- **模型依赖**：AlphaFold对无序区预测不可靠，而修饰位点偏好无序区，可能导致界面映射的系统性偏差。
- **最难情形**：修饰位点位于高度无序区时，AlphaFold无法可靠预测该区域结构，界面映射置信度低。
- **群体/领域边界**：结论限于PARylation对PPI的潜在调控，未涉及蛋白-DNA/RNA互作；未考虑PAR聚合物长度、分支和动态修饰/去修饰过程。
- **不确定性**：作者未提供置信区间或统计检验细节；69个含修饰位点界面的假阳性率未评估。
- **有边界的复述**：在AlphaFold预测可靠的前提下，约1/4的D/E-PARylated蛋白高置信PPI界面含有修饰位点，这些位点偏好位于无序区/卷曲区，提示PARylation可能通过空间位阻和静电效应调控这些复合物的组装，尤其在RNA加工和DNA损伤应答通路中。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| AlphaFold预测精度限制 | 无法建模498对PPI（8.5%），因MSA不可用或显存不足 | 未明确提及 | Methods节 |
| 无序区预测不可靠 | 修饰位点偏好无序区，而AlphaFold对无序区结构预测置信度低 | 未明确提及 | Results节（pLDDT分析） |
| 缺乏实验验证 | 预测的PPI和界面修饰效应未经湿实验证实 | "Future development of structural modeling tools incorporating the PAR moiety could further shed light on the functional mechanisms" | Concluding remarks |
| 修饰位点数据来源有限 | 仅来自两个前期质谱研究，可能未覆盖全部D/E-PARylation位点 | 未明确提及 | Methods节 |

**作者提及的相关约束**（非正式局限）：PAR聚合物长度和分支可变，不同PARylation状态（单/多/聚ADP-核糖）对PPI的影响可能不同，本文未区分。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| AlphaFold接触概率>0.9作为PPI判据缺乏独立验证 | 高接触概率可能反映非特异性共进化信号或假阳性；无实验互作数据交叉验证 | 若PPI预测假阳性率高，则后续界面映射分析的基础不牢 | 用独立实验PPI数据集（如CORUM、hu.MAP）交叉验证预测精度；对部分预测PPI做共免疫沉淀验证 | Methods节：仅以"支持度评分"筛选输入，未报告预测精度 |
| 修饰位点-界面映射的因果方向不明 | 位点位于界面≠修饰发生在界面；修饰可能发生在蛋白未组装时，影响的是组装动力学而非稳态结构 | 因果方向决定功能解读：是"修饰破坏已有互作"还是"修饰阻止互作形成"？ | 时间分辨实验（修饰诱导后不同时间点检测复合物组装）；分子动力学模拟修饰后界面稳定性 | Results节：仅静态映射，无动态信息 |
| 无序区偏好可能反映检测偏差 | 质谱鉴定修饰位点可能偏好易被蛋白酶消化的无序区，而非生物学意义上的偏好 | 若为检测偏差，则"修饰位点偏好无序区"的结论可能不成立 | 用独立方法（如ADP-ribose-specific抗体富集）验证位点分布；对比不同蛋白酶消化方案的结果 | Results节图1C：仅基于现有质谱数据 |
| PCNA hub结论的过度解读 | PCNA已知互作蛋白众多，23个预测PPI中22个含界面修饰位点可能反映PCNA界面本身较大而非PARylation特异性 | 若界面大是主因，则"PARylation调控PCNA hub"的结论被削弱 | 对照分析：随机蛋白的PPI界面含D/E位点比例 vs PCNA；统计检验界面大小与位点密度的关系 | Results节图3：未提供对照分析 |
| 缺乏定量比较 | 未报告含修饰位点界面的比例是否显著高于随机预期 | 无统计显著性支持，"约1/4界面含修饰位点"可能只是基线水平 | 置换检验：随机打乱修饰位点位置，计算界面含位点比例的零分布 | Results节：仅描述性统计 |
| 未考虑PAR聚合物长度 | 单ADP-核糖基化与poly-ADP-核糖基化对PPI的影响机制可能完全不同 | 不同修饰形式的功能后果差异大，混为一谈会误导 | 区分单/多/聚ADP-核糖基化位点分别分析；用不同长度PAR体外实验验证 | Introduction：提及poly-ADP-ribose可长达200个单位，但分析未区分 |

## 14 学到什么
**Agent 提炼的知识候选**

1. **PTM-结构整合分析范式**：将质谱鉴定的PTM位点映射到AlphaFold预测的复合物结构上，系统筛选"位于互作界面的修饰位点"。可迁移到TF-DNA结合研究：将TF的PTM位点（磷酸化、乙酰化、ADP-核糖基化等）映射到TF-DNA复合物结构（AlphaFold3或实验结构），筛选位于DNA结合界面或二聚化界面的修饰位点，预测其对结合亲和力和特异性的调控。

2. **无序区-短线性基序（SLiM）介导互作的识别**：本文发现修饰位点偏好无序区，而这些区域常含SLiMs介导弱但特异的PPI。对TF研究：许多TF的激活域（AD）或抑制域（RD）本质上是无序区，通过SLiMs招募共激活因子/共抑制因子。可将TF无序区中的PTM位点与已知SLiM数据库（ELM、PROSITE）交叉分析，预测修饰对共调节因子招募的影响。

3. **文献支持度加权的PPI筛选策略**：以$S = \sum 1/N_p$加权，优先保留被低通量研究支持的PPI。可迁移到TF-靶基因调控网络构建：对ChIP-seq、DAP-seq等数据鉴定的TF结合位点，用文献支持度加权筛选高置信靶基因，减少高通量数据的假阳性。

4. **AlphaFold复合物预测的"接触概率"指标**：以链间残基对接触概率>0.9作为互作置信度、>0.5作为界面残基。可迁移到TF-DNA互作：用AlphaFold3预测TF-DNA复合物，以蛋白-核酸链间接触概率筛选高置信DNA结合模式，并识别DNA结合界面残基。

5. **功能聚类引导的生物学发现**：对高置信PPI网络做功能聚类，聚焦特定通路（如RNA加工、DNA修复）中的修饰调控。可迁移到TF研究：将TF的互作网络按功能聚类，识别PARylation/磷酸化富集的特定调控模块（如"DNA损伤应答TF网络"、"发育相关TF网络"）。

6. **PTM交叉对话（cross-talk）的结构基础**：本文提出PARylation与SUMOylation通过共享/邻近位点实现交叉对话。对TF研究：可系统分析TF上不同PTM位点在三维结构上的邻近性，预测PTM交叉对话对DNA结合和转录活性的协同调控。

## 15 与已有知识连接
- **可验证的外部文献**：
  - Jumper et al. 2021, Nature（AlphaFold2原始方法）——本文的PPI预测基础。
  - Evans et al. 2022, Science（AlphaFold2 multimer）——本文未使用但相关。
  - Zhang et al. 2013, Mol Cell Proteomics; Martello et al. 2016, Cell Reports——PARylation位点质谱鉴定，本文数据来源[25,26]。
  - 作者前期工作：Cong et al. 2019, Science（AlphaFold前体方法应用于PPI预测）——本文方法学直接延续。
  - Hendriks et al. 2017, Nat Struct Mol Biol——ADP-核糖基化位点组学，可交叉验证本文位点列表。
  - 对TF-DNA方向：AlphaFold3（Abramson et al. 2024, Nature）已支持蛋白-核酸复合物预测，可迁移本文的"PTM-结构映射"范式。

- **与用户已有知识的连接**：
  - 若用户熟悉TF-DNA结合机制：本文的"修饰位点位于互作界面"分析可直接类比为"TF磷酸化位点位于DNA结合域（DBD）与DNA的接触面"——例如p53的Ser15磷酸化位于DBD附近，可能通过静电改变影响DNA结合。
  - 若用户熟悉MD模拟：本文的静态结构映射可作为MD模拟的起点——对含修饰位点的界面做修饰后MD，比较结合自由能变化。
  - 若用户熟悉ChIP-seq分析：本文的PPI网络聚类方法可迁移为"TF结合位点-共调节因子"共富集分析。

- **可迁移领域**：蛋白质-RNA互作（RBPs的修饰调控）、蛋白质-小分子互作（代谢物传感）、染色质互作（组蛋白修饰对核小体组装的影响）。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：TF-DNA结合界面的PTM调控图谱（PTM-TF-DNA Interactome Atlas）
   - **来源局限/观察**：本文仅分析PPI界面，未涉及蛋白-DNA界面；TF-DNA结合受多种PTM调控，但缺乏系统结构分析。
   - **核心假设**：TF上位于DNA结合界面的PTM位点（磷酸化、乙酰化、ADP-核糖基化）显著富集于已知调控转录活性的修饰事件。
   - **增量**：将本文的"PTM-结构映射"范式从PPI扩展到蛋白-DNA互作；利用AlphaFold3预测TF-DNA复合物。
   - **初步方法**：收集TF PTM数据库（PhosphoSitePlus、dbPTM）→ AlphaFold3预测TF-DNA复合物 → 映射PTM位点到DNA接触面 → 与已知功能调控事件交叉验证 → 对候选位点做分子动力学模拟（修饰前后DNA结合自由能比较）。
   - **验证方式**：电泳迁移率变动分析（EMSA）验证修饰模拟突变（如D/E→A）对DNA结合的影响；ChIP-seq比较修饰状态改变后的基因组结合谱。
   - **创新状态**：unverified（未见类似系统分析发表）。

2. **候选名称**：PARylation对TF凝聚体（condensate）形成的调控机制
   - **来源局限/观察**：本文发现PARylation位点偏好无序区，而无序区是相分离的关键驱动因素；TF的相分离在转录调控中起重要作用。
   - **核心假设**：TF无序区中的D/E-PARylation通过改变局部电荷分布调控TF的相分离行为，进而影响其DNA结合和转录活性。
   - **增量**：将PTM-结构分析从"界面调控"扩展到"相分离调控"；连接PARylation与转录凝聚体生物学。
   - **初步方法**：对TF无序区中的D/E-PARylation位点做电荷效应分析 → 用AlphaFold预测无序区构象ensemble → 粗粒化模拟修饰前后相分离倾向 → 体外液-液相分离实验验证。
   - **验证方式**：体外相分离实验（浊度、荧光恢复后光漂白）；细胞内核体成像比较PARP抑制前后的TF凝聚体形成。
   - **创新状态**：unverified（PARylation与相分离的直接关联研究较少）。

3. **候选名称**：基于共进化的TF-DNA结合特异性预测增强
   - **来源局限/观察**：本文用共进化信号预测PPI，但TF-DNA结合特异性预测（如DeepSEA、BPNet）多基于实验数据，未充分利用共进化信息。
   - **核心假设**：TF与DNA的共进化信号可增强现有深度学习模型的结合特异性预测。
   - **增量**：将本文的联合MSA策略从蛋白-蛋白扩展到蛋白-DNA；为TF-DNA预测提供正交信号。
   - **初步方法**：构建TF-DNA联合MSA（含直系同源TF及其靶基因启动子） → 提取共进化特征 → 与现有模型（如BPNet）特征融合 → 在ENCODE ChIP-seq数据上评估。
   - **验证方式**：独立测试集上的AUROC/AUPRC比较；对预测的共进化关键碱基做突变验证。
   - **创新状态**：partially checked（已有研究用共进化预测蛋白-DNA接触，但未与深度学习模型系统融合）。

4. **候选名称**：PARylation调控的TF-DNA结合动态网络
   - **来源局限/观察**：本文静态映射了修饰位点与界面，但未考虑修饰的动态性（PARP激活/降解的时序）。
   - **核心假设**：DNA损伤诱导的PARylation通过动态调控多个TF的DNA结合能力，形成时序性的转录重编程。
   - **增量**：将静态结构分析扩展到动态网络模型；连接PARylation时序与转录输出。
   - **初步方法**：对DNA损伤时间序列的PARylation组学数据（已有公共数据）→ 结合本文的界面映射方法 → 构建"修饰-结合-转录"动态网络 → 用动态贝叶斯网络建模。
   - **验证方式**：时间序列ChIP-seq验证预测的TF结合动态；CRISPR敲除关键PARP后检测转录表型。
   - **创新状态**：unverified。

5. **候选名称**：PTM界面富集分析工具（PTM-Interface Enrichment Tool, PIET）
   - **来源局限/观察**：本文手工分析了69个含修饰位点的界面，但缺乏自动化工具供领域使用。
   - **核心假设**：将本文的分析流程工具化，可帮助领域内研究者快速评估任意PTM类型在任意互作界面的富集程度。
   - **增量**：提供标准化工具，降低PTM-结构整合分析门槛。
   - **初步方法**：整合AlphaFold/AlphaFold3预测、PTM数据库、PDB结构 → 自动计算PTM位点与界面残基的重叠 → 置换检验评估富集显著性 → 输出可视化报告。
   - **验证方式**：在已知PTM调控的复合物（如p53-MDM2、PCNA-PIP盒）上验证工具准确性；与本文结果交叉验证。
   - **创新状态**：unverified（未见类似工具发表）。