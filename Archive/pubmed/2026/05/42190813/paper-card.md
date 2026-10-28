## 01 基本信息
- **标题**: Constitutive activation of a hybrid two-component regulator reveals cross-regulation of polysaccharide utilization genes in Bacteroides
- **作者与单位**: Gao, Rong; Sillick, Brynn; Thomas, Leonard M; Wu, Crystal; Wu, Ti; Stock, Ann M（单位未在摘要中提供）
- **期刊/预印本平台**: The Journal of Biological Chemistry
- **年份**: 2026-05-27
- **论文类型**: 研究论文（实验 + 计算模拟）
- **领域**: 微生物学 / 转录调控 / 蛋白质-DNA互作 / 结构生物学
- **关键词**: Bacteroides, hybrid two-component system (HTCS), polysaccharide utilization loci (PUL), transcription regulation, DNA-binding domain, latch mutation, crystallography, molecular dynamics
- **DOI/arXiv 号**: 10.1016/j.jbc.2026.113195
- **代码**: 未提供
- **数据**: PDB ID 12AW（BT4124R晶体结构）；其余数据按需提供
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文聚焦细菌HTCS（一种跨膜融合的组氨酸激酶-响应调节因子）的转录调控机制，核心是REC-DBD结构域间的抑制性互作与激活机制。与「TF-DNA结合机制 × AI/物理模拟」课题的关联在于：(1) 使用AlphaFold预测蛋白-DNA复合物结构；(2) 使用深度学习蛋白动力学模拟器BioEmu模拟构象平衡；(3) 通过点突变破坏结构域间抑制界面实现组成型激活，为研究TF-DNA结合提供了「无需天然信号即可激活」的通用策略。

## 02 一句话总结
通过晶体结构解析和BioEmu深度学习构象模拟，揭示Bacteroides HTCS转录因子BT4124的REC-DBD结构域间由保守C/SHIP-D.K基序介导的「闭态」抑制机制，并通过破坏该界面的「AD」双突变实现组成型激活，进而鉴定其DNA结合位点并发现其交叉调控多个果胶利用PUL。

## 03 研究问题
- **具体问题**: HTCS（hybrid two-component system）是Bacteroides中调控多糖利用基因座（PUL）的主要转录因子类型，但其激活机制和DNA结合位点大多未知，主要障碍是大多数HTCS的天然糖信号未知，无法在体外选择性激活。
- **为什么重要**: 理解PUL的调控网络是理解肠道菌群中微生物-微生物、宿主-微生物互作的基础；HTCS占Bacteroides转录因子的主要部分，但其调控机制研究长期受阻于无法激活。
- **现有方法不足**: 传统方法需要已知信号分子来磷酸化激活RR（response regulator），但大多数HTCS的天然信号未知；磷酸化RR的酰基磷酸高能键不稳定，难以维持磷酸化状态进行DNA结合位点作图（如DNase footprinting）。
- **精确研究问题**: Can a targeted mutation of the conserved interdomain latch motif constitutively activate an HTCS regulator without its native glycan signal, thereby enabling identification of its DNA-binding sites and regulated genes?

## 04 背景与发展脉络
*注：以下脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。*

1. **PUL调控的发现与HTCS的识别**（早期）: Bacteroides依赖PUL代谢复杂多糖；HTCS是PUL的主要调控因子，含跨膜传感组氨酸激酶（HK）和胞内响应调节因子（RR）于同一多肽链。
2. **HTCS激活机制研究受阻**（中期）: 大多数HTCS的天然糖信号未知，无法在体外激活；少数已知信号的HTCS研究依赖磷酸化模拟或信号分子添加，但磷酸化RR不稳定。
3. **结构预测与计算方法的介入**（近期）: AlphaFold预测了BT4124R的结构域排列，提示REC-DBD间存在抑制性互作；但AlphaFold对侧链堆积和氢键网络的预测精度有限（误差可达1/3氢键和范德华接触）。
4. **本文位置**: 在AlphaFold预测基础上，用晶体结构精确刻画抑制性界面，用BioEmu深度学习模拟器预测突变对构象平衡的影响，用AD突变实现组成型激活，从而绕过信号未知的瓶颈，建立「突变激活 → DNA结合位点鉴定 → 调控网络发现」的通用流程。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| HTCS天然信号未知 | 大多数HTCS无法在体外被激活，无法研究其DNA结合和调控功能 | 天然糖信号未鉴定 | Abstract: "the specific glycan signals required to activate most HTCSs remain unknown" |
| 磷酸化RR不稳定 | 酰基磷酸高能键易水解，难以维持磷酸化状态进行DNA结合位点作图 | 磷酸化RR的化学不稳定性 | Results: "The lability of high-energy acyl phosphate makes RR phosphorylation often short-lived" |
| AlphaFold对侧链精度有限 | AlphaFold预测的结构无法精确刻画抑制性氢键网络 | AlphaFold对侧链堆积和氢键预测误差大 | Discussion: "AlphaFold often produces less accurate predictions on sidechain packing, with the error amounting to one-third of all hydrogen bonds and van der Waals contacts" |
| 结构域交换二聚体可能是结晶假象 | 晶体中观察到结构域交换二聚体，但溶液态为单体 | 高浓度结晶条件可能导致部分去折叠 | Results: "The domain-swapped dimer observed in the structure appears to be an artifact of crystallization conditions" |

## 06 核心思想
1. **表面方法**: 解析BT4124R（RR结构域）的晶体结构；用BioEmu深度学习模拟器比较WT与AD突变体的构象分布；构建AD组成型激活突变体；用EMSA和DNase footprinting鉴定DNA结合位点；用AlphaFold预测蛋白-DNA复合物结构；在B. theta细胞内用qPCR验证调控效果。
2. **核心洞察**: HTCS的RR结构域通过保守的C/SHIP-D.K基序形成分子内「锁扣」（latch），将DBD锁定在非活性「闭态」。破坏该锁扣的氢键网络（AD突变）即可绕过磷酸化信号，直接将蛋白锁定在活性「开态」，从而无需知道天然信号即可研究其DNA结合功能。
3. **可能的普适教训** [Analysis]: 对于信号未知的TF，通过结构-guided的突变破坏抑制性结构域间界面，可以实现「组成型激活」，这是一种可推广的「信号绕过」策略。此外，BioEmu等深度学习构象模拟器可以预测突变对构象平衡的影响，为「结构-guided突变设计」提供计算先验，减少试错成本。

## 07 方法总览
- **输入**: BT4124R蛋白序列（来自B. thetaiotaomicron）；bt4114和bt4108启动子区DNA片段；B. theta菌株
- **输出**: BT4124R晶体结构（PDB 12AW）；WT与AD突变体的构象分布；DNA结合位点位置；受调控基因列表
- **模块**:
  1. 蛋白表达纯化（E. coli表达系统）
  2. 晶体学（X射线衍射，分子置换法，AlphaFold模型为搜索模型）
  3. BioEmu构象模拟（深度学习蛋白动力学模拟器，4000个构象样本）
  4. EMSA（凝胶迁移实验）
  5. DNase I footprinting（荧光标记 + 毛细管电泳）
  6. AlphaFold3蛋白-DNA复合物预测
  7. qPCR基因表达分析
- **训练**: 无新模型训练；BioEmu和AlphaFold为预训练模型
- **反馈回路**: 晶体结构 → 识别锁扣残基 → 设计AD突变 → BioEmu验证构象偏移 → 实验验证DNA结合 → 体内验证调控 → 反馈到结构解释
- **文字流程**: 纯化BT4124R → 结晶并解析结构 → 识别C/SHIP-D.K基序的锁扣互作 → 设计C1262A/D1344A双突变（AD）→ BioEmu模拟WT vs AD构象分布 → EMSA验证AD组成型DNA结合 → DNase footprinting定位结合位点 → AlphaFold3预测DBD-DNA复合物结构 → 在B. theta中诱导表达AD突变体 → qPCR检测多个PUL基因表达变化

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 晶体结构解析 | 精确刻画REC-DBD界面 | AlphaFold侧链精度不足，无法指导突变设计 | 输入：纯化蛋白；输出：2.0-2.5Å分辨率结构 | Results 图1；PDB 12AW | 无法精确选择突变位点，AD突变设计失去结构依据 |
| BioEmu构象模拟 | 预测WT vs AD的构象平衡偏移 | 验证突变是否确实破坏闭态 | 输入：蛋白序列；输出：4000构象的RMSD分布 | Results 图3 | 突变设计缺乏计算验证，可能盲目试错 |
| AD组成型激活突变 | 绕过磷酸化信号，实现无需信号的激活 | 天然信号未知，无法用传统方法激活 | 输入：C1262A/D1344A双突变；输出：组成型DNA结合活性 | Results 图4；Abstract | 无法研究该HTCS的DNA结合功能 |
| EMSA | 检测DNA结合活性 | 验证AD突变体是否组成型结合DNA | 输入：蛋白+荧光DNA；输出：结合曲线（KD≈1.6μM） | Results 图4A | 无法确认AD突变体的DNA结合能力 |
| DNase I footprinting | 精确定位DNA结合位点 | 确定TF在启动子上的具体结合序列 | 输入：蛋白+荧光DNA+DNase I；输出：保护区域 | Results 图4B-D | 无法确定结合位点，AlphaFold预测缺乏约束 |
| AlphaFold3蛋白-DNA复合物预测 | 预测DBD-DNA互作结构 | 解释footprinting结果，理解识别机制 | 输入：DBD序列+DNA序列；输出：复合物结构模型 | Results 图5 | 缺乏结构解释，无法理解序列识别机制 |
| qPCR | 验证体内调控效果 | 确认AD突变体在细胞内能调控基因表达 | 输入：aTc诱导的B. theta RNA；输出：基因表达log2 fold change | Results 图6 | 无法确认AD突变体的生理相关性 |

## 09 关键公式符号
不适用。本文无定量数学模型或公式；主要定量分析为BioEmu构象分布的RMSD/RMSF统计、EMSA结合曲线拟合（Hill方程）、DNase footprinting的峰强度比值计算。这些均为标准生物化学/生物物理数据分析方法，无需要特殊符号说明的公式。

## 10 实验设计与证据链
- **数据集/群体**: B. thetaiotaomicron VPI-5462（WT）；Δbt4124敲除株（RUB001）；Δbt4124 + aTc诱导BT4124RAD整合株（RUB002）
- **规模**: 蛋白结晶（1个结构）；BioEmu模拟（WT和AD各4000构象）；EMSA（3个DNA片段×多个蛋白浓度）；DNase footprinting（2个启动子）；qPCR（5个PUL基因+对照）
- **指标**: RMSD/RMSF（构象）；KD（DNA结合亲和力）；保护区域（footprinting）；log2 fold change（基因表达）
- **基线**: WT未磷酸化BT4124R（无DNA结合活性）；WT B. theta（aTc诱导对照）
- **预算**: 未提供
- **骨干/仪器**: SSRL同步辐射光束线9-2（X射线衍射）；ÄKTA纯化系统；Beckman Optima XL-I分析超速离心机；QuantStudio 3 qPCR仪
- **oracle输入**: AlphaFold预测的BT4124R结构（作为分子置换搜索模型）；RegPrecise数据库中的预测结合位点
- **评测协议**: 无标准benchmark；实验自洽验证（体外DNA结合 + 体内基因表达）

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 晶体结构解析 | REC-DBD界面由C/SHIP-D.K基序介导 | 无对比；结构解析 | 闭态构象，锁扣氢键网络清晰可见 | 锁扣残基确实介导抑制性互作 | 无法证明该互作在溶液态存在（晶体可能为假象） | Results 图1 |
| 凝胶过滤/AUC | BT4124R在溶液中为单体 | WT vs 磷酸化 vs AD突变体 | 所有状态均为单体（~32-35kDa） | 激活不依赖二聚化 | 无法排除体内二聚化的可能 | Results 图2 |
| BioEmu模拟 | AD突变破坏闭态 | WT vs AD，各4000构象 | WT约50%闭态，AD闭态几乎消失 | AD突变确实改变构象平衡 | 模拟为计算预测，未经实验直接验证构象分布 | Results 图3 |
| EMSA | AD突变体组成型结合DNA | WT（无结合）vs AD（结合）vs 磷酸化WT（结合） | AD结合KD≈1.6μM | AD突变绕过磷酸化实现激活 | 体外结合亲和力可能不同于体内 | Results 图4A |
| DNase footprinting | 结合位点位于bt4114启动子-126至-34区域 | AD vs 无蛋白对照 | 两个保护区域，各含两个半位点 | 结合位点定位成功 | 未验证这些位点在体内的功能重要性 | Results 图4B-D |
| AlphaFold3预测 | DBD-DNA复合物结构 | 预测 vs footprinting实验 | 预测的识别螺旋与实验保护区域一致 | 结构预测与实验互补 | 预测的侧链接触未经验证 | Results 图5 |
| qPCR | AD突变体在体内抑制多个PUL | RUB002+aTc vs RUB002-aTc vs WT+aTc | 多个PUL基因显著下调 | BT4124交叉调控多个果胶相关PUL | 未区分直接与间接调控 | Results 图6 |

## 11 结论正确解读
- **任务范围**: 本研究仅针对B. thetaiotaomicron中一个HTCS（BT4124）的RR结构域。结论不能外推到所有HTCS，尽管作者推测该策略可能通用（基于C/SHIP-D.K基序的保守性）。
- **oracle/真值输入**: AlphaFold预测结构用于分子置换，但最终晶体结构为实验真值；RegPrecise预测位点用于引导footprinting分析，但实验footprinting为独立验证。
- **端到端状态**: 从结构到功能的全链条验证已完成（结构→突变→体外DNA结合→体内调控），但未做全基因组ChIP-seq或转录组学，调控网络的全貌未知。
- **算力成本**: 未提供；BioEmu和AlphaFold3为云端/本地预训练模型推理，成本相对低。
- **历史数据依赖**: 依赖AlphaFold预测（用于分子置换）和RegPrecise数据库（用于预测位点）；这些预测的准确性影响实验设计但最终由实验验证。
- **模型依赖**: BioEmu的构象分布预测未经实验直接验证（如H/D交换或NMR）；AlphaFold3的蛋白-DNA复合物预测仅与footprinting间接一致。
- **最难情形**: 下游PUL基因（bt4118, bt4121）的表达变化被aTc全局响应掩盖，无法判断BT4124RAD是否直接调控这些基因。
- **群体/领域边界**: 结论限于Bacteroides属的HTCS调控；对真核TF-DNA结合研究的直接适用性有限，但「结构-guided组成型激活突变」策略可能可迁移。
- **不确定性**: 闭态/开态的具体构象比例未经实验定量；AD突变体在体内的激活程度未知；交叉调控的直接性（直接结合 vs 间接效应）未完全区分。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| aTc全局响应掩盖部分基因的调控判断 | bt4118和bt4121在WT中也因aTc诱导而表达上升，无法判断BT4124RAD是否直接调控 | 未明确提及 | Results 图6B |
| 下游PUL基因的调控可能为间接效应 | 交叉调控可能通过其他调控因子介导 | 未明确提及 | Discussion: "This cross-regulation can be direct... or indirect" |
| AlphaFold对蛋白-DNA复合物预测的局限性 | 预测的复合物结构多样性大，仅部分收敛 | 未明确提及 | Results 图5 |
| 结构域交换二聚体可能是结晶假象 | 晶体中观察到的二聚体在溶液中不存在 | 未明确提及 | Results: "appears to be an artifact of crystallization conditions" |
| 未在全基因组水平验证调控网络 | 仅验证了少数基因 | 未明确提及 | 未提供 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| BioEmu预测的「闭态消失」缺乏实验验证 | BioEmu为深度学习模拟器，其构象分布预测可能不准确；AD突变可能通过其他机制（如改变蛋白稳定性）而非破坏锁扣来激活 | 如果构象预测不准确，则「锁扣破坏」机制的解释可能不成立 | 用H/D交换质谱、NMR或SAXS实验直接比较WT和AD的构象分布 | Results 图3 |
| AD突变体在体内的调控效果仅用qPCR验证了少数基因 | 可能遗漏了大量受调控基因；也可能存在脱靶效应 | 交叉调控网络的结论可能不完整 | 进行RNA-seq或ChIP-seq全基因组分析 | Results 图6 |
| AlphaFold3预测的蛋白-DNA复合物与footprinting的一致性有限 | 预测的复合物结构多样性大，仅8/10收敛；收敛部分可能与footprinting保护区域一致，但未验证具体碱基接触 | 如果预测不准确，则「识别机制」的解释可能不完整 | 用突变分析（如碱基替换）验证预测的关键接触残基 | Results 图5 |
| 未测试AD突变对HTCS全长蛋白（含HK结构域）的影响 | 本研究仅使用RR结构域（BT4124R），全长HTCS中REC-DBD互作可能受HK结构域或跨膜区影响 | 如果全长蛋白中锁扣机制不同，则策略的通用性存疑 | 在体外表达全长HTCS并测试AD突变的激活效果 | Methods: "RR components of HTCS proteins" |
| 「AD突变策略可能广泛适用」的推测缺乏多序列验证 | 仅测试了一个HTCS（BT4124），C/SHIP-D.K基序的保守性虽高，但不同HTCS的锁扣互作细节可能不同 | 如果策略不通用，则其作为「通用工具」的价值有限 | 在多个Bacteroides HTCS中测试AD突变策略 | Discussion: "may be broadly applicable because of the high conservation" |

## 14 学到什么
**Agent 提炼的知识候选**（面向TF-DNA结合 × AI/物理模拟课题）:

1. **「结构-guided组成型激活突变」策略**: 对于信号未知的TF，通过晶体结构或高精度预测识别抑制性结构域间界面，设计破坏该界面的突变，可实现无需配体/信号的组成型激活。可迁移到真核TF研究：例如，对于含自抑制结构域的TF（如某些bZIP、bHLH蛋白），可通过破坏抑制性界面来研究其DNA结合特异性。

2. **AlphaFold预测的「粗粒度」用途**: 本文展示了AlphaFold预测可用于分子置换（MR）和初步构象假设，但侧链精度不足，需晶体结构或实验验证。对TF-DNA复合物预测的启示：AlphaFold3预测的复合物结构可能多样性大，需结合实验约束（如footprinting、突变分析）进行筛选。

3. **深度学习构象模拟器（BioEmu）作为突变设计工具**: BioEmu可快速预测突变对构象平衡的影响，为「结构-guided突变设计」提供计算先验。可迁移到TF-DNA研究：在设计TF突变体（如组成型激活、组成型失活）时，先用BioEmu或类似工具（如AlphaFold2/3的突变扫描）预测构象影响，再进行实验验证。

4. **「单体激活」vs「二聚化激活」的区分**: 本文通过AUC和凝胶过滤排除了二聚化在激活中的作用，强调构象变化而非寡聚状态变化是激活机制。对TF-DNA结合研究的启示：在设计激活突变时，需区分「构象释放」和「二聚化促进」两种机制，避免混淆。

5. **DNase footprinting + 荧光毛细管电泳的高通量方案**: 本文使用荧光标记DNA + 毛细管电泳进行footprinting，比传统放射性标记更安全、更定量。可迁移到TF-DNA结合位点鉴定：结合组成型激活突变体，可在无信号条件下快速定位TF的结合位点。

6. **「交叉调控」的发现路径**: 通过组成型激活突变体，发现一个TF调控多个PUL，揭示了TF的交叉调控网络。对TF-DNA研究的启示：组成型激活突变体可用于发现TF的「非经典」靶基因，揭示TF的多效性调控。

## 15 与已有知识连接
- **HTCS与双组分系统（TCS）**: 本文的HTCS是经典TCS的融合变体。经典TCS（如E. coli PhoB/PhoR）的REC-DBD互作已有大量研究（如PhoB的激活机制，参考文献19, 23-25）。本文的「锁扣」机制与PhoB的REC-DBD互作有相似性，但HTCS的融合拓扑可能改变互作细节。
- **AraC家族DBD**: BT4124的DBD属于AraC家族，该家族的DNA结合机制已有广泛研究（如MarA, 参考文献39-42）。本文的AlphaFold预测与MarA晶体结构（PDB 1BL0）的比较，为AraC家族DBD的DNA识别提供了新案例。
- **AlphaFold在蛋白-DNA复合物预测中的应用**: AlphaFold3（参考文献37）已被广泛用于蛋白-DNA复合物预测，但本文指出其局限性（多样性大、需实验约束）。这与近期文献中关于AlphaFold3在蛋白-DNA预测中表现不稳定的报道一致。
- **深度学习构象模拟器**: BioEmu（参考文献31）是新兴的深度学习蛋白动力学模拟器，本文展示了其在突变效应预测中的应用。与MD模拟相比，BioEmu速度更快但精度可能有限，适合作为初步筛选工具。
- **Bacteroides多糖利用与肠道菌群**: PUL调控是肠道微生物组研究的热点（参考文献16-17, 52-56）。本文发现的交叉调控网络与已知的PUL共调控现象一致，为理解肠道菌群的碳水化合物竞争提供了分子机制。
- **可迁移领域**: 「结构-guided组成型激活突变」策略可迁移到其他信号未知的TF研究，尤其是微生物中大量未表征的HTCS和孤儿RR。在真核系统中，类似策略可用于研究含自抑制结构域的TF（如STAT、NF-κB等）。

## 16 研究想法
**Agent 生成的研究候选**:

1. **候选名称**: HTCS组成型激活突变策略的泛化验证
   - **来源局限/观察**: 本文仅验证了一个HTCS（BT4124），C/SHIP-D.K基序虽保守，但不同HTCS的锁扣互作细节可能不同。
   - **核心假设**: 基于C/SHIP-D.K基序的AD突变策略可在多个Bacteroides HTCS中实现组成型激活。
   - **初步方法**: 选取10-20个B. thetaiotaomicron中未表征的HTCS，用AlphaFold预测结构，识别对应锁扣残基，设计AD突变，用体内报告基因系统（如PUL启动子-lacZ融合）筛选组成型激活突变体。
   - **验证方式**: EMSA验证DNA结合；RNA-seq验证调控网络；与已知HTCS的调控网络比较。
   - **创新状态**: unverified

2. **候选名称**: BioEmu vs MD模拟在TF构象平衡预测中的系统比较
   - **来源局限/观察**: 本文用BioEmu预测WT vs AD的构象平衡，但未与MD模拟或实验验证对比。
   - **核心假设**: BioEmu对TF结构域间构象平衡的预测与MD模拟定性一致，但定量精度有限。
   - **初步方法**: 以BT4124R为模型，分别用BioEmu和MD模拟（如OpenMM + AMBER力场）计算WT和AD突变体的构象分布，比较RMSD/RMSF和开闭态比例；用H/D交换质谱实验验证。
   - **验证方式**: 计算-实验一致性评估；误差分析。
   - **创新状态**: unverified

3. **候选名称**: AlphaFold3蛋白-DNA复合物预测的「实验约束筛选」流程
   - **来源局限/观察**: 本文AlphaFold3预测的复合物结构多样性大，仅部分收敛，需footprinting实验约束。
   - **核心假设**: 结合DNase footprinting和EMSA数据作为约束，可显著提高AlphaFold3对TF-DNA复合物预测的准确性。
   - **初步方法**: 以BT4124-AD与bt4114启动子为模型，将footprinting保护区域作为距离约束，重新运行AlphaFold3或使用AF2Complex等工具，比较约束前后预测精度。
   - **验证方式**: 与突变分析（碱基替换）和晶体结构（如有）对比。
   - **创新状态**: unverified

4. **候选名称**: HTCS交叉调控网络的系统图谱构建
   - **来源局限/观察**: 本文发现BT4124交叉调控多个PUL，但仅验证了少数基因，全基因组范围未知。
   - **核心假设**: B. thetaiotaomicron中HTCS存在广泛的交叉调控网络，而非一一对应的线性调控。
   - **初步方法**: 对多个HTCS构建组成型激活突变体，进行ChIP-seq + RNA-seq，构建HTCS-靶基因调控网络；结合PUL的代谢功能注释分析网络结构。
   - **验证方式**: 网络motif分析；与已知PUL共调控数据比较。
   - **创新状态**: unverified

5. **候选名称**: 「锁扣」机制在真核TF中的同源搜索
   - **来源局限/观察**: 本文的「锁扣」机制是原核HTCS特有的，但「自抑制结构域」在真核TF中普遍存在。
   - **核心假设**: 真核TF中可能存在结构类似的「锁扣」界面，可通过类似AD突变策略实现组成型激活。
   - **初步方法**: 对真核TF（如bZIP、bHLH、核受体）进行结构比对，搜索与C/SHIP-D.K基序功能类似的抑制性界面；用AlphaFold预测和共进化分析（如EVcouplings）识别候选残基。
   - **验证方式**: 突变体DNA结合实验；报告基因系统验证。
   - **创新状态**: unverified