## 01 基本信息

- **标题**：PARP1 inhibitors regulate PARP1 structure independent of DNA, reducing binding affinity for single strand breaks
- **作者与单位**：Mark Pailing; Lotte van Beek; Taiana Maia de Oliveira; Maria M. Flocco; Bart W. Hoogenboom（伦敦大学学院；阿斯利康）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025
- **论文类型**：预印本（研究论文）
- **领域**：结构生物学 / 单分子生物物理 / 癌症药物机制
- **关键词**：PARP1、PARP抑制剂、原子力显微镜、DNA损伤修复、单链断裂
- **DOI/arXiv 号**：10.1101/2025.08.30.673248
- **代码**：未提供
- **数据**：未提供（补充材料含视频和表格）
- **阅读日期**：2025-09-04
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：本文属于**单分子实验生物物理**方法（AFM/HS-AFM），研究**蛋白质构象动态与DNA结合功能**的关系。虽未使用AI或MD模拟，但其核心发现——**配体诱导的蛋白质构象变化（不依赖DNA）可调控DNA结合亲和力**——为TF–DNA结合机制的构象调控模型提供了直接实验证据，可作为AI/模拟方法（如MD、增强采样、构象集合预测）的验证基准和建模目标。

## 02 一句话总结

本文通过原子力显微镜（AFM）和高速度AFM（HS-AFM）直接可视化单个PARP1/PARP2分子，发现PARP抑制剂（特别是强捕获型talazoparib和olaparib）在**无DNA存在时**即可诱导PARP1发生显著压实（compaction）和构象灵活性丧失，且这种DNA非依赖的构象变化与后续PARP1对单链断裂DNA的结合能力下降（4-6倍）相关。

## 03 研究问题

- **具体问题**：PARP抑制剂是否能在DNA不存在的情况下直接改变PARP1的构象？这种构象变化是否影响PARP1随后与DNA损伤位点的结合？
- **为什么重要**：PARP抑制剂是BRCA1/2突变癌症的临床药物，其机制被广泛归因于"PARP捕获"（trapping）——即抑制剂将PARP1锁定在DNA损伤位点。但不同抑制剂的捕获效力差异巨大（talazoparib >> olaparib > veliparib），且捕获机制本身存在争议（催化抑制 vs. 变构调控）。理解抑制剂是否通过DNA非依赖的构象调控影响PARP1功能，对药物设计具有重要意义。
- **现有方法为何不足**：传统结构方法（X射线晶体学、冷冻电镜）难以捕捉PARP1这种高度柔性蛋白的构象异质性和动态变化；bulk生化实验无法区分"DNA依赖的捕获"与"DNA非依赖的构象预调控"。
- **精确的"Can ... ?"问题**：Can PARP inhibitors induce conformational changes in PARP1 in the absence of DNA, and does this DNA-independent conformational regulation reduce PARP1's subsequent binding affinity for single-strand breaks?

## 04 背景与发展脉络

*注：以下脉络基于本文引文和框架整理，标记为「仅本文框架」，未经外部系统核验。*

1. **PARP1结构域模型阶段**：PARP1被描述为"beads on a string"——由N端DNA结合域（DBD，含3个锌指）、自身修饰域（含BRCT）、WGR域和C端催化域（CAT，含HD和ART亚域）组成，各域间由柔性linker连接。代表工作：Lilyestrom (JMB, 2010)；Langelier et al. (2010, 2012, 2018)。
2. **DNA结合诱导的构象激活模型**：PARP1结合DNA损伤后发生大规模构象重排，HD从CAT中抽出，暴露NAD+结合位点，激活PARylation。代表工作：Dawicki-McKenna et al. (2015)；Eustermann et al. (2015)。
3. **PARP抑制剂变构调控阶段**：Zandarashvili et al. (2020) 通过结构生物学发现不同抑制剂诱导不同的变构效应——弱捕获型抑制剂（veliparib）使HD不稳定但保持域间接触，强捕获型抑制剂（talazoparib, olaparib）则促进域间接触稳定化。但该工作主要在DNA结合状态下研究。
4. **本文位置**：将变构调控的概念**扩展到DNA非依赖状态**，用单分子AFM直接证明抑制剂在无DNA时即可诱导PARP1压实，并首次将这种构象变化与后续DNA结合能力下降建立因果联系。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PARP1柔性导致结构研究困难 | 全长PARP1难以用传统结构方法解析 | PARP1由柔性linker连接多个结构域，构象高度异质和动态 | Introduction："The ambiguity remains in large part due to the flexible nature of PARP1, which makes it less amenable to traditional structural methods." |
| 不同抑制剂捕获效力与细胞毒性不匹配 | talazoparib/olaparib/veliparib捕获效力差异大，但细胞毒性和催化抑制相似 | 可能存在DNA非依赖的补充机制 | Introduction："different PARP inhibitors have very similar toxicities and catalytic inhibition despite a wide range of trapping potency" |
| PARP捕获机制争议 | 捕获是由催化抑制、变构调控还是两者共同导致尚不明确 | 缺乏DNA非依赖状态下的构象信息 | Introduction："it is still debated if PARP trapping is caused by catalytic inhibition, allosteric regulation or a combination of both" |
| 传统bulk实验无法区分构象亚群 | 无法判断抑制剂是否影响未结合DNA的PARP1群体 | 缺乏单分子分辨率的方法 | 本文采用AFM/HS-AFM直接可视化单个分子 |

## 06 核心思想

**1) 表面方法**：
- 用AFM（PeakForce Tapping模式）在云母表面成像单个PARP1/PARP2蛋白，测量体积（volume）变化
- 用HS-AFM（高速AFM）以时间分辨率追踪单个蛋白的构象动态，通过圆度（circularity）分析量化形状变化
- 用DLS（动态光散射）在溶液中验证AFM观察到的尺寸变化趋势
- 用荧光偏振（FP）bulk实验验证抑制剂预处理对PARP1-DNA结合的影响
- 设计两种孵育顺序：PARP1-抑制剂先孵育再加DNA（PARP-inhibitor first）vs. PARP1-DNA先孵育再加抑制剂（PARP-DNA first）

**2) 核心洞察**：
- **抑制剂在无DNA时即可诱导PARP1压实**，且压实程度与抑制剂的捕获效力相关（talazoparib > olaparib > veliparib）
- **压实伴随构象灵活性丧失**：HS-AFM显示talazoparib处理的PARP1从动态、异质的构象变为静态、均匀的球状结构
- **PARP1与PARP2的差异**：PARP2（无大DBD）对抑制剂的构象响应远小于PARP1，表明压实主要发生在DBD
- **功能后果**：抑制剂预处理的PARP1对单链断裂DNA的结合能力显著下降（AFM计数和FP均证实），且这种效应在PARP-DNA先孵育时不存在——说明抑制剂通过改变PARP1的"预结合状态"而非竞争DNA位点来降低结合

**3) 可能的普适教训** [Analysis]：
- **配体诱导的构象预调控（conformational pre-regulation）** 可能是DNA结合蛋白的普遍调控机制——配体（不一定是DNA）可以改变蛋白的构象集合（conformational ensemble），从而改变其对DNA的亲和力。这对TF–DNA互作研究有直接启示：**小分子或共因子可能通过改变TF的构象动态来调控其DNA结合特异性/亲和力**，而不一定需要直接竞争DNA结合位点。
- **单分子动态测量（HS-AFM）** 能捕捉到bulk实验和静态结构方法无法分辨的构象异质性和动态变化，是研究柔性蛋白-DNA互作的强有力工具。

## 07 方法总览

- **输入**：重组全长人PARP1（V762A变体）和PARP2蛋白；含单链断裂的496 bp PCR产物DNA（两端生物素标记）；荧光标记的44-nt dumbbell DNA（含单链断裂）；三种PARP抑制剂（veliparib, olaparib, talazoparib）；NAD和BAD（非水解NAD类似物）
- **输出**：AFM单分子体积分布、HS-AFM时间分辨圆度轨迹、DLS粒径分布、FP结合曲线（EC50值）
- **模块**：
  1. AFM静态成像 + 体积分析（Gwyddion软件）
  2. HS-AFM动态成像 + 圆度/方差分析（NanoLocz + ImageJ）
  3. DLS溶液粒径验证
  4. FP结合实验（两种孵育顺序）
  5. 统计分析（Student's t-test）
- **训练**：不适用（无机器学习）
- **反馈回路**：AFM观察到的构象变化 → 预测功能影响 → FP和AFM-DNA结合实验验证
- **文字流程**：纯化蛋白 → 与抑制剂/NAD/BAD孵育30分钟 → AFM成像（静态或动态）→ 体积/圆度分析 → 与未处理对照比较 → 另设PARP1-DNA结合实验（两种孵育顺序）→ AFM计数或FP定量结合 → 比较抑制剂预处理对结合的影响

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AFM静态体积分析 | 定量检测抑制剂诱导的蛋白尺寸变化 | 直接测量单分子构象变化 | 输入：AFM图像；输出：蛋白体积分布 | Results 图1B：三种抑制剂均显著降低PARP1体积，且与捕获效力相关 | 无法定量构象变化程度（预期影响） |
| HS-AFM动态成像 + 圆度分析 | 检测构象灵活性和动态变化 | 区分"静态压实"与"动态波动" | 输入：HS-AFM视频；输出：圆度均值和方差 | Results 图2B-C：talazoparib显著降低圆度方差，表明构象被锁定 | 无法区分构象动态性差异（预期影响） |
| DLS溶液验证 | 排除云母表面吸附造成的假象 | 确认AFM观察在溶液中成立 | 输入：蛋白溶液；输出：水合直径 | Results 图1D-E：DLS趋势与AFM一致 | 无法排除表面效应（预期影响） |
| FP结合实验（两种孵育顺序） | 验证构象变化的功能后果 | 区分"构象预调控"与"竞争性抑制" | 输入：PARP1+抑制剂+荧光DNA；输出：FP信号/EC50 | Results 图4B：PARP-inhibitor first显著降低最大FP信号；PARP-DNA first无此效应 | 无法建立构象-功能因果链（预期影响） |
| AFM单分子DNA结合计数 | 直接可视化PARP1在DNA上的结合 | 单分子水平验证FP结果 | 输入：PARP1+DNA±抑制剂；输出：DNA上结合蛋白的计数 | Results 图3B：talazoparib和olaparib预处理导致4-6倍结合减少 | 无法确认bulk水平的结合变化（预期影响） |
| PARP2对照实验 | 定位构象变化的结构域来源 | PARP2缺乏大DBD，可作为结构域功能对照 | 输入：PARP2±抑制剂；输出：体积/圆度数据 | Results 图1C, 2B-C：PARP2对抑制剂响应远小于PARP1 | 无法将压实归因于特定结构域（预期影响） |

## 09 关键公式符号

本文为实验生物物理论文，无核心数学模型或公式。以下为数据分析中使用的定义：

- **圆度（Circularity）**：$C = 4\pi A / P^2$，其中 $A$ 为投影面积，$P$ 为周长。$C=1$ 表示完美圆形，$C<1$ 表示不规则形状。用于量化蛋白形状的规则程度。
- **圆度方差（Variance in circularity）**：$Var(C) = \frac{1}{N-1}\sum_{i=1}^{N}(C_i - \bar{C})^2$，其中 $N$ 为时间帧数，$C_i$ 为第 $i$ 帧的圆度，$\bar{C}$ 为平均圆度。用于量化构象随时间波动的程度。
- **蛋白体积（Volume）**：AFM中通过"zero-basis volume"函数计算，基于蛋白高度轮廓的积分体积。
- **EC50**：FP剂量-响应曲线中达到50%最大信号变化时的抑制剂浓度（Supplementary Table 2）。

## 10 实验设计与证据链

**数据集/群体**：
- 蛋白：重组全长人PARP1（V762A）和PARP2，表达于昆虫细胞（Sf21），纯度约95%
- DNA：496 bp PCR产物（含Nt.BsmAI切口，位于172 bp处）；44-nt荧光标记dumbbell DNA（含单链断裂）
- 抑制剂：veliparib（弱捕获）、olaparib（中等捕获）、talazoparib（强捕获）；浓度1 µM（AFM）或10 pM-300 µM（FP剂量响应）
- 对照：NAD（天然底物）、BAD（非水解NAD类似物）、无药物处理

**指标**：蛋白体积（AFM）、圆度均值与方差（HS-AFM）、水合直径（DLS）、FP信号/EC50（结合实验）、DNA上结合蛋白计数（AFM）

**预算/资源**：未提供具体实验预算；AFM设备为Bruker FastScan Bio和NanoRacer

**评测协议**：每种条件至少3个生物学重复；AFM每张图像测量10个蛋白；统计检验为Student's t-test

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| AFM体积分析（PARP1） | 抑制剂在无DNA时诱导PARP1压实 | 未处理 vs. veliparib/olaparib/talazoparib处理 | 三种抑制剂均显著降低PARP1体积；talazoparib和olaparib效果大于veliparib | 抑制剂在无DNA时即可改变PARP1构象 | 无法确定压实的具体结构域或分子机制 | Results 图1B |
| AFM体积分析（PARP2） | 压实效应是否依赖DBD | 未处理 vs. 抑制剂处理的PARP2 | PARP2体积变化远小于PARP1 | 压实主要发生在PARP1的DBD | 无法排除其他结构域贡献 | Results 图1C |
| DLS验证 | AFM观察是否在溶液中成立 | 未处理 vs. 抑制剂处理的PARP1/PARP2 | DLS粒径变化趋势与AFM一致 | 压实不是云母表面假象 | DLS分辨率有限，无法提供单分子信息 | Results 图1D-E |
| HS-AFM圆度分析 | 抑制剂是否降低构象灵活性 | 未处理 vs. talazoparib处理的PARP1 | talazoparib显著降低圆度方差，蛋白呈静态球状 | 强捕获型抑制剂锁定PARP1构象 | 无法确定锁定是否可逆 | Results 图2B-C |
| AFM DNA结合计数 | 抑制剂预处理是否降低DNA结合 | PARP-inhibitor first vs. PARP-DNA first vs. 未处理 | talazoparib和olaparib预处理导致4-6倍结合减少；veliparib无显著效应 | 强捕获型抑制剂通过构象预调控降低DNA结合 | 无法区分"结合速率降低"与"结合稳定性降低" | Results 图3B |
| FP结合实验 | 在bulk水平验证DNA结合降低 | PARP-inhibitor first vs. PARP-DNA first | talazoparib和olaparib在inhibitor-first条件下显著降低最大FP信号和升高EC50 | 构象预调控导致功能性DNA结合能力下降 | FP信号变化可能部分反映DNA构象变化而非仅蛋白结合 | Results 图4B, Supplementary Table 2 |
| FP恢复实验 | 确认信号降低由PARP1失活而非DNA竞争引起 | 加入新鲜未处理PARP1 | 新鲜PARP1恢复FP信号 | 抑制剂处理使PARP1功能失活而非占据DNA位点 | 未测试其他抑制剂浓度下的恢复 | Results 图4C |

## 11 结论正确解读

- **任务范围**：本文仅研究**无DNA条件下**PARP抑制剂对PARP1/PARP2构象的影响，以及这种预处理的后续功能后果。不涉及抑制剂与DNA结合PARP1的竞争关系、不涉及细胞内环境、不涉及其他PARP家族成员。
- **oracle/真值输入**：无（实验测量，非预测模型）
- **端到端状态**：实验链条完整——从单分子构象观察到功能验证（AFM计数+FP），但未延伸到细胞水平或动物模型。
- **算力成本**：不适用
- **历史数据依赖**：不适用
- **模型依赖**：不适用
- **最难情形**：AFM对软性、柔性蛋白的体积测量存在固有不确定性（作者在Discussion中承认）；云母表面吸附可能影响蛋白构象（尽管DLS部分缓解此担忧）；PARP1的V762A变体可能不完全代表野生型行为。
- **群体/领域边界**：结论仅适用于所测试的三种抑制剂（veliparib, olaparib, talazoparib）和体外纯化蛋白体系；不能外推至其他PARP抑制剂或细胞内环境。
- **不确定性**：作者未提供压实效应的定量结构模型（如具体哪些结构域接触发生变化）；未测试抑制剂浓度依赖性构象变化的详细动力学；未直接测量PARP1-DNA结合的动力学速率常数（kon/koff）。
- **有边界的复述**：在体外纯化体系中，强捕获型PARP抑制剂（talazoparib, olaparib）可在无DNA时诱导PARP1压实和构象灵活性丧失，这种DNA非依赖的构象预调控显著降低PARP1随后对单链断裂DNA的结合能力；弱捕获型抑制剂veliparib的效应较弱且不显著影响DNA结合。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| AFM体积测量对软性样品的不确定性 | 对柔性蛋白的体积估计存在固有误差 | 未明确提及 | Discussion："may be due to the inherent uncertainty in AFM volume estimates for soft and flexible samples" |
| 未直接解析压实态的具体结构 | AFM提供形状信息但无法提供原子级结构 | 未明确提及 | Discussion（隐含） |
| 体外体系与细胞环境的差异 | 未在细胞中验证DNA非依赖构象调控的存在 | "The observed inhibitor induced loss of PARP1 – DNA binding warrants further investigation as to how this population of DNA-binding deficient PARP1 proteins impacts the non-DNA repair PARP1 roles in cells" | Discussion |
| PARP1 V762A变体的使用 | 该变体可能不完全代表野生型PARP1 | 未明确提及 | Methods（隐含） |

**作者提及的相关约束**（非正式局限）：
- 未测试抑制剂浓度对构象变化的剂量依赖性细节
- 未直接测量PARP1-DNA结合的动力学参数
- 未研究抑制剂诱导的构象变化是否影响PARP1的其他功能（如转录调控、染色质重塑）

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 体积测量依赖AFM探针-蛋白相互作用 | 不同抑制剂可能改变蛋白表面电荷/疏水性，影响AFM成像中的形貌而非真实体积 | 若为成像伪影，则"压实"结论不成立 | 用不同AFP探针（不同化学修饰）重复实验；或用负染EM/冷冻EM交叉验证 | Methods AFM部分 |
| PARP1 V762A变体的使用 | V762A是已知的临床相关多态性，可能改变蛋白的构象动态和药物响应 | 若V762A增强或减弱压实效应，则结论不能推广至野生型 | 用野生型PARP1重复关键实验 | Methods Proteins部分 |
| 抑制剂浓度（1 µM）远高于临床暴露水平 | 高浓度可能产生非特异性疏水效应或聚集 | 若效应仅在超药理浓度出现，临床相关性存疑 | 做浓度梯度实验，测试纳摩尔至微摩尔范围的构象变化 | Methods AFM部分 |
| "压实"与"聚集"的区分 | AFM体积减小也可能反映蛋白在云母表面的去折叠或部分解析叠 | 若为解析叠而非压实，则机制解释不同 | 用圆二色谱（CD）或氢氘交换质谱（HDX-MS）检测二级结构变化 | Results 图1 |
| FP实验中EC50变化方向 | 作者报告PARP-inhibitor first导致EC50升高（需要更多PARP1达到50%信号），但最大信号降低可能使EC50拟合不稳定 | 若EC50变化不稳健，则"降低亲和力"的定量结论需谨慎 | 报告完整剂量-响应曲线和拟合参数；用独立方法（如ITC或SPR）验证 | Results 图4B, Supplementary Table 2 |
| 未测试抑制剂是否改变PARP1的DNA结合特异性（而非仅亲和力） | 压实可能改变PARP1对DNA损伤类型的偏好 | 若特异性也改变，则对机制理解有重要影响 | 用不同DNA底物（单链断裂、双链断裂、发夹结构）测试结合 | Results 图3 |
| 未讨论抑制剂诱导的构象变化是否影响PARP1的酶活（PARylation） | 压实可能同时影响催化活性，而不仅仅是DNA结合 | 若酶活也改变，则"捕获"机制需要重新定义 | 在无DNA条件下测量抑制剂处理后的PARP1自修饰活性 | Discussion（未提及） |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **构象预调控（Conformational Pre-regulation）概念**：配体可在靶蛋白未结合DNA时诱导其构象变化，从而改变后续DNA结合能力。对TF–DNA互作研究：**小分子、共因子或翻译后修饰可能通过改变TF的构象集合来调控其DNA结合**，而非仅通过直接竞争或变构调节DNA结合界面。可迁移至TF–DNA结合机制的建模中——将TF的构象动态纳入结合亲和力预测。

2. **单分子动态测量作为构象-功能关联的工具**：HS-AFM的圆度方差分析提供了一种量化蛋白质构象灵活性的方法。对TF–DNA研究：**构象灵活性（而非静态结构）可能是DNA结合特异性的关键决定因素**。AI模型（如AlphaFold）预测的静态结构可能遗漏这一维度；可考虑将MD模拟的构象集合（ensemble）与实验圆度/灵活性数据对接验证。

3. **结构域缺失对照实验设计**：通过比较PARP1（含大DBD）和PARP2（无大DBD）对配体的构象响应差异，定位构象变化的结构域来源。对TF–DNA研究：**设计不同结构域截短体，结合单分子测量，可系统定位DNA结合域在配体诱导构象变化中的角色**。

4. **两种孵育顺序的实验设计**：PARP-inhibitor first vs. PARP-DNA first的对比，可区分"配体对游离蛋白的构象预调控"与"配体对已结合DNA蛋白的竞争/置换"。对TF–DNA研究：**类似实验设计可用于区分小分子调控TF-DNA结合的两种机制**——是改变TF的DNA结合能力，还是竞争DNA结合位点。

5. **AFM体积测量的定量分析流程**：从AFM图像提取单分子体积、建立统计分布、比较不同处理条件。对TF–DNA研究：**AFM可直接可视化TF在DNA上的结合位置和构象**，可用于验证AI预测的TF-DNA结合模式。

6. **"捕获效力"与"构象变化程度"的相关性**：强捕获型抑制剂（talazoparib）诱导最大构象变化，弱捕获型（veliparib）最小。对TF–DNA研究：**配体对TF构象的影响程度可能预测其对DNA结合的调控强度**——这一关系可用于药物筛选或设计。

## 15 与已有知识连接

- **PARP1结构域组织与"beads on a string"模型**：本文引用的Lilyestrom (JMB, 2010) 和Langelier et al. (2010, 2012, 2018) 工作，建立了PARP1的多域柔性结构模型。本文的AFM数据直接支持这一模型，并提供了动态证据。
- **Zandarashvili et al. (2020) 的变构调控框架**：该工作提出不同PARP抑制剂诱导不同的变构效应（HD稳定性、域间接触）。本文将其扩展到DNA非依赖状态，并补充了单分子动态证据。
- **PARP捕获机制争议**：本文与Kanev et al. (2024) 等关于捕获机制的讨论直接相关，提供了"构象预调控"作为补充机制的证据。
- **与TF–DNA互作研究的连接** [Analysis]：本文的"配体诱导构象预调控"概念与转录因子领域的"allostery"研究（如配体结合域与DNA结合域之间的长程构象耦合）高度相似。例如，核受体（如雌激素受体）的配体结合诱导构象变化进而调控DNA结合，与本文PARP1的现象在概念上同构。本文的单分子方法（AFM/HS-AFM）可直接迁移至TF–DNA结合动态研究。
- **与AI/模拟方法的连接** [Analysis]：本文提供的实验数据（体积变化、圆度变化、结合亲和力变化）可作为MD模拟或增强采样方法的验证基准。例如，可用MD模拟talazoparib结合PARP1催化域后的全蛋白构象变化，与AFM观察到的压实效应对比。AlphaFold预测的PARP1结构（多为静态、单一构象）无法捕捉本文揭示的构象异质性，提示需要结合构象集合方法（如ensemble docking, metadynamics）。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA结合亲和力的构象集合预测模型
   - **来源局限/观察**：本文证明配体诱导的构象压实可降低DNA结合亲和力；现有AI模型（如AlphaFold, RoseTTAFold）预测静态结构，无法捕捉构象动态对DNA结合的影响。
   - **核心假设**：TF的构象灵活性（由MD模拟的RMSF或构象集合熵量化）与DNA结合亲和力呈负相关；配体结合诱导的构象压实可预测DNA结合亲和力的变化。
   - **初步方法**：对一组TF（如p53, MYC, FOXO）进行MD模拟（apo vs. 配体结合态），计算构象集合特征（如域间距离分布、RMSF、构象熵）；用这些特征训练回归模型预测实验测定的DNA结合亲和力（如SPR/EMSA数据）。
   - **验证方式**：与本文PARP1数据对比（AFM体积变化 vs. MD预测的压实程度）；用已知TF-配体对（如核受体-激素）验证预测的亲和力变化方向。
   - **创新状态**：unverified

2. **候选名称**：基于AFM单分子数据的TF-DNA结合动力学参数提取
   - **来源局限/观察**：本文用AFM计数和FP获得稳态结合数据，但未提取结合/解离动力学速率常数；TF-DNA结合的动力学（而非仅亲和力）对基因调控时间尺度至关重要。
   - **核心假设**：HS-AFM时间序列可提取单分子水平的TF-DNA结合/解离事件，获得kon/koff分布。
   - **初步方法**：将HS-AFM应用于TF-DNA系统（如p53与含p53响应元件的DNA），追踪单个TF分子在DNA上的结合-解离事件，用隐马尔可夫模型（HMM）或机器学习分类器自动识别结合状态，提取速率常数分布。
   - **验证方式**：与表面等离子共振（SPR）或停流荧光获得的bulk动力学常数对比。
   - **创新状态**：unverified

3. **候选名称**：配体诱导TF构象变化对DNA结合特异性的影响——以核受体为例
   - **来源局限/观察**：本文发现PARP1压实降低DNA结合亲和力，但未测试是否改变DNA序列选择性；核受体（如ER, GR）的配体已知可改变其DNA结合基序偏好（"选择性调节"）。
   - **核心假设**：配体诱导的TF构象变化不仅改变DNA结合亲和力，还可能改变DNA序列特异性。
   - **初步方法**：对ERα进行MD模拟（apo vs. 不同配体结合态），用蛋白-DNA对接或机器学习评分预测不同DNA响应元件的结合偏好；用Protein Binding Microarray (PBM) 或SELEX-seq实验验证。
   - **验证方式**：预测的基序偏好变化与实验测定的基序矩阵（PWM）对比。
   - **创新状态**：partially checked（核受体领域已有部分证据，但未与构象集合建模结合）

4. **候选名称**：TF-DNA结合中"构象预调控"与"诱导拟合"的区分——单分子FRET验证
   - **来源局限/观察**：本文的AFM数据支持配体诱导的构象预调控，但无法区分"预调控"（ligand-induced conformational selection）与"诱导拟合"（ligand binding后DNA结合域才发生构象变化）。
   - **核心假设**：TF在无DNA时存在构象平衡（开放/闭合态），配体结合改变平衡位置（conformational selection），而非在DNA结合时诱导新构象（induced fit）。
   - **初步方法**：在TF的DNA结合域和配体结合域分别标记FRET对，用单分子FRET（smFRET）追踪配体结合前后的构象分布变化；结合MD模拟的构象集合分析。
   - **验证方式**：FRET效率分布是否呈现双峰（预存构象平衡）vs. 单峰位移（诱导拟合）；与MD预测的构象自由能面（PMF）对比。
   - **创新状态**：unverified

5. **候选名称**：基于深度学习的TF构象动态预测——从序列到构象集合
   - **来源局限/观察**：本文揭示构象动态对DNA结合的重要性，但实验测量构象动态耗时且低通量；现有AI结构预测工具无法输出构象集合。
   - **核心假设**：TF的氨基酸序列和配体结合状态可预测其构象集合特征（如域间距离分布、灵活性），进而预测DNA结合亲和力。
   - **初步方法**：用AlphaFold的pLDDT和PAE作为构象灵活性的代理特征，结合MD模拟生成的构象集合作为训练数据，训练图神经网络（GNN）或扩散模型预测构象集合；将预测的构象集合特征输入DNA结合亲和力预测模型。
   - **验证方式**：对已知TF-配体-DNA三元复合物进行留一法交叉验证；与本文PARP1的AFM数据对比。
   - **创新状态**：unverified