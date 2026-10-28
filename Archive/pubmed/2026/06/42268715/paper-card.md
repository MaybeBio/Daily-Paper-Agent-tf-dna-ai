## 01 基本信息
- **标题**: B cell TET2 recruits OGT for nuclear TET2 and H2B O-GlcNAcylation to drive AID and BLIMP-1 expression and maturation of the antibody response
- **作者与单位**: Li, Shili; Peng, Yibo; Yang, Zhimin; Li, Xin; Xu, Zhenming; Rivera, Carlos E; Casali, Paolo（通讯作者，University of Texas at San Antonio Health Science Center）
- **期刊/预印本平台**: Cell Reports
- **年份**: 2026
- **论文类型**: 研究论文（Research Article）
- **领域**: 免疫学 / 表观遗传学 / B细胞分化
- **关键词**: TET2, OGT, O-GlcNAcylation, AID, BLIMP-1, 抗体应答, 5mC氧化, H2B-S112
- **DOI/arXiv 号**: 10.1016/j.celrep.2026.117370
- **代码**: 未提供（论文明确说明 "This paper does not report original code"）
- **数据**: MiSeq、MeDIP、hMeDIP测序数据已存入NCBI SRA，BioProject ID PRJNA117370（原文写为PRJNA1271607，以原文为准）
- **阅读日期**: 2026-07-14
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**: 本文聚焦TET2（一种5mC双加氧酶）通过招募OGT实现对自身及组蛋白H2B的O-GlcNAcylation修饰，进而调控Aicda和Prdm1基因座的DNA去甲基化与染色质可及性。该文使用AlphaFold 3.0进行蛋白质-DNA-蛋白质三元复合物的结构预测，属于「AI结构预测辅助理解TF/染色质调控因子-DNA互作机制」的典型应用案例。对课题方向的启示在于：TET2作为DNA结合蛋白（非经典TF），其与DNA的结合及对OGT的招募机制可通过AI结构预测获得原子级分辨率见解。

## 02 一句话总结
本文通过B细胞特异性基因敲除、生化互作实验和AlphaFold 3.0结构预测，证明TET2在活化B细胞中通过其C端招募OGT，介导TET2自身及染色质H2B-S112的O-GlcNAcylation，从而促进Aicda和Prdm1位点的活性DNA去甲基化与基因表达，驱动抗体应答成熟。

## 03 研究问题
- **具体问题**: TET2在B细胞抗体应答中如何被调控？TET2是否通过非催化功能（招募OGT）来调控Aicda和Prdm1的表达？
- **为什么重要**: 抗体应答成熟（SHM/CSR、浆细胞分化）依赖于AID和BLIMP-1的精确表达。TET2作为5mC双加氧酶在B细胞分化中起关键作用，但其调控机制（特别是与代谢传感器OGT的关联）尚不清楚。理解这一机制有助于阐明代谢-表观遗传轴在免疫应答中的角色。
- **现有方法不足**: 以往研究多关注TET2的催化功能（5mC→5hmC氧化），对其非催化功能（如蛋白互作、招募染色质修饰酶）在B细胞中的生理意义缺乏系统研究。TET2与OGT的互作在B细胞中未被探索。
- **精确研究问题**: Can B cell TET2 recruit OGT through its C-terminal end to mediate O-GlcNAcylation of TET2 and chromatin H2B-S112, thereby driving Aicda and Prdm1 expression and antibody response maturation?

## 04 背景与发展脉络
（注：以下脉络为「经外部核验」的领域发展框架，结合本文引用与领域共识）

1. **TET蛋白家族发现与功能解析（2009-2015）**: TET1/2/3被鉴定为5mC双加氧酶，催化5mC→5hmC→5fC→5caC的氧化过程，参与DNA去甲基化。TET1主要在ESC中表达，TET2在造血/免疫细胞中高表达。代表工作：Tahiliani et al. 2009; Ito et al. 2010; Pastor et al. 2013。
2. **TET2在免疫细胞中的功能（2015-2020）**: TET2被发现在B细胞分化、T细胞功能中起关键作用。TET2缺失导致B细胞分化异常、抗体应答受损。代表工作：Dominguez et al. 2018; Lio et al. 2019。
3. **OGT与O-GlcNAcylation在染色质调控中的角色（2010-2020）**: OGT作为唯一催化蛋白O-GlcNAcylation的酶，被发现与TET蛋白互作（在ESC中），修饰TET蛋白及组蛋白H2B-S112，参与基因表达调控。代表工作：Chen et al. 2013; Vella et al. 2013; Forma et al. 2020。
4. **AlphaFold系列在蛋白质-DNA/蛋白质-蛋白质复合物预测中的应用（2021-2024）**: AlphaFold 2突破单体蛋白结构预测，AlphaFold 3.0扩展至蛋白质-核酸-小分子复合物预测，为理解转录因子/染色质调控因子与DNA的互作提供了新工具。代表工作：Jumper et al. 2021; Abramson et al. 2024。
5. **本文位置**: 首次在B细胞中系统证明TET2通过C端招募OGT，将TET2的催化功能（DNA去甲基化）与非催化功能（OGT招募、H2B-S112修饰）整合，并利用AlphaFold 3.0提供结构模型支持。填补了TET2在B细胞中调控机制的关键空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| TET2在B细胞中的表达模式不明确 | 静息B细胞中TET蛋白不可检测，活化后TET2诱导表达 | TET2在B细胞活化后被诱导，TET1/TET3不表达 | Results 图1A-1B |
| TET2缺失对B细胞分化的影响机制不清 | 既往研究多关注TET2催化功能，非催化功能被忽视 | TET2可能通过招募OGT发挥非催化功能 | 全文框架 |
| TET2如何调控Aicda/Prdm1的DNA去甲基化 | 具体分子机制（TET2如何被招募至靶位点、如何协同染色质修饰）未知 | TET2通过OGT介导的O-GlcNAcylation稳定自身并修饰H2B-S112 | Results 图4B-4G |
| OGT在B细胞中的功能未被探索 | OGT在B细胞抗体应答中的角色完全未知 | OGT作为TET2的互作蛋白，参与Aicda/Prdm1位点的表观遗传调控 | Results 图3-4 |
| TET2-OGT-DNA三元复合物结构未知 | 缺乏实验结构，无法理解TET2如何同时结合DNA和OGT | 使用AlphaFold 3.0进行结构预测 | Results 图5A |

## 06 核心思想
1. **表面方法**: B细胞特异性基因敲除小鼠（AicdaCre介导的TET2/Ogt缺失）、体外B细胞活化培养、流式细胞术分析B细胞亚群、ELISA检测抗体、MeDIP/hMeDIP-seq检测DNA甲基化状态、ChIP-qPCR检测蛋白-DNA结合、Co-IP检测蛋白互作、AlphaFold 3.0结构预测。
2. **核心洞察**: TET2在B细胞中不仅作为5mC双加氧酶发挥催化功能，还通过其C端招募OGT，形成TET2-OGT复合物。该复合物一方面通过OGT介导TET2自身的O-GlcNAcylation来稳定TET2蛋白，另一方面通过OGT对H2B-S112的O-GlcNAcylation来改变染色质状态，两者协同促进Aicda和Prdm1位点的活性DNA去甲基化与转录。TET2的C端缺失（G1876-V1920）足以破坏TET2-OGT互作，导致功能丧失。
3. **可能的普适教训** [Analysis]: 染色质调控因子的功能不应仅局限于其酶活性（催化功能），其作为"平台蛋白"招募其他染色质修饰酶的能力（非催化功能）可能同样重要。在AI结构预测时代，AlphaFold 3.0可快速生成蛋白质-DNA-蛋白质三元复合物的候选结构，为设计验证实验提供假设。这一思路可迁移至其他DNA结合蛋白（如转录因子）与共调控因子的互作研究。

## 07 方法总览
- **输入**: 小鼠B细胞（静息/活化）、人B细胞、TET2/OGT突变体构建、DNA序列信息（Aicda/Prdm1位点）
- **输出**: B细胞分化状态、抗体水平、DNA甲基化/羟甲基化图谱、蛋白互作网络、TET2-OGT-DNA复合物结构模型
- **模块**:
  1. 基因敲除小鼠构建与免疫（AicdaCre-Tet2fl/fl, AicdaCre-Ogtfl/fl）
  2. B细胞体外活化与分化分析（流式细胞术）
  3. 抗体应答评估（ELISA, ELISPOT）
  4. 表观遗传分析（MeDIP/hMeDIP-seq, MeDIP/hMeDIP-qPCR）
  5. 蛋白-DNA互作分析（ChIP-qPCR）
  6. 蛋白-蛋白互作分析（Co-IP）
  7. 结构预测（AlphaFold 3.0）
- **训练**: 不适用（无监督学习/预训练模型直接应用）
- **工具**: AlphaFold 3.0, FlowJo, GraphPad Prism, IMGT/HighV-QUEST, PHYLOViZ
- **反馈回路**: 基因敲除→表型分析→分子机制验证→结构模型支持→功能回补实验
- **假设**: TET2通过C端招募OGT是B细胞Aicda/Prdm1表达所必需的；O-GlcNAcylation对TET2稳定性和H2B-S112修饰至关重要

**文字流程**: 首先确认TET2在活化B细胞中特异性表达（图1）→ 构建B细胞特异性TET2敲除小鼠，观察抗体应答受损表型（图2）→ 通过Co-IP发现TET2-OGT互作，并定位到C端（图4F）→ 构建C端缺失突变体，验证功能丧失（图5B-5C）→ 用AlphaFold 3.0建模TET2-OGT-DNA复合物，支持C端互作界面（图5A）→ 用OGT抑制剂和TET2抑制剂分别处理，验证催化功能与互作功能各自贡献（图S10-S11）→ 用维生素C和富马酸二甲酯调节TET2活性，验证代谢调控（图6-7）。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| B细胞特异性基因敲除 | 在活化B细胞中条件性删除Tet2或Ogt | 避免全身性敲除的发育缺陷，精准评估B细胞内在功能 | 输入：Tet2fl/fl或Ogtfl/fl × AicdaCre小鼠；输出：B细胞特异性敲除小鼠 | Results 图2-3 | 预期：无法评估TET2/OGT在B细胞中的功能（实测效应） |
| 体外B细胞活化分化体系 | LPS±IL-4、CD154±IL-4等刺激B细胞向浆细胞分化 | 模拟体内抗体应答，便于机制研究 | 输入：纯化B细胞+刺激物；输出：分化B细胞亚群 | Results 图1-2 | 预期：无法在体外评估TET2/OGT功能（实测效应） |
| Co-IP互作分析 | 检测TET2与OGT的物理互作 | 证明TET2-OGT复合物存在 | 输入：核提取物+抗体；输出：互作蛋白鉴定 | Results 图4F | 预期：无法证明TET2-OGT互作（实测效应） |
| AlphaFold 3.0结构预测 | 预测TET2-OGT-DNA三元复合物结构 | 缺乏实验结构，AI预测提供原子级互作模型 | 输入：TET2/OGT蛋白序列+DNA序列；输出：复合物结构模型 | Results 图5A | 预期：无法获得结构层面的互作界面信息（预期效应，因无实验结构对照） |
| MeDIP/hMeDIP-seq | 全基因组检测5mC和5hmC分布 | 评估TET2催化功能对Aicda/Prdm1位点的影响 | 输入：基因组DNA；输出：甲基化/羟甲基化图谱 | Results 图4B, S7B-S7C | 预期：无法评估TET2催化功能（实测效应） |
| ChIP-qPCR | 检测TET2/OGT在Aicda/Prdm1位点的结合 | 证明TET2/OGT直接结合靶基因调控区 | 输入：交联染色质+抗体；输出：富集倍数 | Results 图4G, S7A | 预期：无法证明TET2/OGT直接结合靶位点（实测效应） |
| 小分子抑制剂处理 | TET2抑制剂(TET-IN-C35)、OGT抑制剂(ST 045849) | 药理学验证催化功能与互作功能 | 输入：B细胞+抑制剂；输出：功能表型变化 | Results 图S10-S11 | 预期：无法区分催化与互作功能贡献（实测效应） |
| 代谢物处理 | 维生素C（TET2激活）、富马酸二甲酯（TET2抑制） | 验证代谢-表观遗传轴 | 输入：B细胞+代谢物；输出：功能表型变化 | Results 图6-7 | 预期：无法评估代谢调控TET2的生理意义（实测效应） |

## 09 关键公式符号
不适用。本文为实验生物学研究，未涉及数学公式或计算模型。AlphaFold 3.0的结构预测基于深度学习模型，但论文未提供模型内部公式。

## 10 实验设计与证据链
**数据集/群体**:
- 小鼠：C57BL/6、Tcrβ−/−Tcrδ−/−、Tet2fl/fl、Tet2−/−、AicdaCreTet2fl/fl、AicdaCreTet2+/+、AicdaCreTet3fl/fl、AicdaCreTet3+/+、AicdaCreOgtfl/fl、AicdaCreOgt+/+、Tet2HxD-mut/HxD-mut（8-12周龄，雌雄各半）
- 人源化THX小鼠（20-22周龄，人CD45+细胞≥90%）
- 人B细胞：健康供者外周血/脐带血

**指标**: 
- B细胞亚群（流式细胞术）：GC B细胞、浆母细胞、浆细胞、记忆B细胞
- 抗体水平（ELISA）：总IgG、IgA、IgE、NP特异性IgG1/IgA
- 抗体分泌细胞（ELISPOT）
- SHM频率（Illumina MiSeq测序）
- 5mC/5hmC水平（MeDIP/hMeDIP-seq, MeDIP/hMeDIP-qPCR）
- 蛋白-DNA结合（ChIP-qPCR）
- 蛋白-蛋白互作（Co-IP）
- 蛋白表达水平（Western blot）

**评测协议**: 免疫后不同时间点（第0、7、14、21、28天）分析B细胞应答；体外B细胞培养72-96小时分析分化。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| TET1/2/3表达分析 | 静息B细胞不表达TET蛋白，活化后仅TET2诱导 | 静息vs活化B细胞，小鼠和人 | TET2在活化B细胞中表达，TET1/TET3不可检测 | TET2是B细胞中主要的TET家族成员 | 未排除TET1/3在特定亚群中的低水平表达 | Results 图1A-1B |
| AicdaCreTet2fl/fl小鼠免疫 | TET2缺失损害抗体应答 | AicdaCreTet2+/+ vs AicdaCreTet2fl/fl，NP-CGG免疫 | 总IgG/IgA降低，NP特异性IgG1/IgA降低 | TET2是抗体应答成熟所必需的 | 未评估T细胞非依赖性应答 | Results 图2A |
| SHM分析 | TET2缺失减少SHM | AicdaCreTet2+/+ vs AicdaCreTet2fl/fl，V1-72DJH-Cγ1转录本 | SHM频率降低5.9倍 | TET2促进SHM | 未评估SHM的碱基偏好性变化 | Results 图2F |
| Co-IP | TET2与OGT互作 | 抗TET2 IP vs 对照IgG IP | TET2-OGT共沉淀 | TET2与OGT在B细胞核内互作 | 未证明直接互作（可能通过中间蛋白） | Results 图4F |
| AlphaFold 3.0建模 | TET2 C端与OGT互作 | TET2-OGT-DNA三元复合物 | C端残基与OGT广泛接触 | 支持C端介导互作 | 预测模型未经实验验证 | Results 图5A |
| Tet2OGT-Δmut回补 | C端缺失破坏TET2功能 | Tet2−/− B细胞+ Tet2WT vs Tet2OGT-Δmut | C端缺失突变体无法完全恢复CSR和浆细胞分化 | TET2 C端（OGT结合）对功能至关重要 | 未排除C端其他功能 | Results 图5B-5C |
| 维生素C处理 | 维生素C增强TET2活性 | 对照vs维生素C处理B细胞 | 增加5hmC、AID/BLIMP-1表达、CSR | 代谢信号通过TET2调控B细胞分化 | 未排除维生素C的TET2非依赖性效应 | Results 图6F, 7E |
| 富马酸二甲酯处理 | 富马酸抑制TET2活性 | 对照vs DMF处理THX小鼠 | 降低人B细胞AID/BLIMP-1表达、抗体应答 | 代谢抑制TET2损害抗体应答 | 未排除DMF的TET2非依赖性效应 | Results 图6A-6E |

## 11 结论正确解读
- **任务范围**: 本文聚焦于B细胞中TET2-OGT轴在抗体应答成熟（SHM/CSR、浆细胞分化）中的作用。结论仅限于活化/分化中的B细胞，不涉及静息B细胞或其他免疫细胞类型。
- **oracle/真值输入**: 基因敲除小鼠（AicdaCre介导的条件性敲除）提供了遗传学因果证据；AlphaFold 3.0预测仅作为结构支持，非实验验证。
- **端到端状态**: 本文为完整的实验生物学研究，从表型（抗体应答）到分子机制（DNA去甲基化、组蛋白修饰）均有实验证据。AlphaFold 3.0仅用于结构建模，非端到端计算预测。
- **算力成本**: 未提供（AlphaFold 3.0为云端/本地部署，具体算力未说明）。
- **历史数据依赖**: 依赖既往TET2/OGT在ESC中的研究（如TET1-OGT互作），但本文在B细胞中独立验证。
- **模型依赖**: 不适用（无预测模型）。
- **最难情形**: 未系统评估TET2-OGT轴在低亲和力抗原或慢性抗原刺激下的作用；未评估TET2在人类B细胞淋巴瘤中的潜在角色。
- **群体/领域边界**: 结论基于小鼠模型和人源化小鼠，人类原代B细胞实验有限。TET2-OGT轴在其他组织/细胞类型中的普适性未验证。
- **不确定性**: 作者承认未量化H2B-S113 O-GlcNAcylation对整体基因表达的相对贡献；未排除TET2通过其他互作蛋白发挥功能。

**有边界的复述**: 在B细胞活化和分化的特定情境下，TET2通过其C端（G1876-V1920）招募OGT，介导TET2自身和H2B-S112的O-GlcNAcylation，促进Aicda和Prdm1位点的5mC-to-5hmC氧化和基因表达，从而驱动抗体应答成熟。该结论在小鼠模型中得到遗传学验证，在人类B细胞中得到药理学支持，但未在人类遗传学或临床样本中验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未量化H2B-S112 O-GlcNAcylation的相对贡献 | 实验未区分H2B-S112 O-GlcNAcylation与TET2自身O-GlcNAcylation对基因表达的独立贡献 | 作者建议进行"进一步的定量、顺序生化实验" | Discussion, Limitations of the study |
| 未进行TET2体外DNA去甲基化酶活性测定 | 未直接证明O-GlcNAcylated TET2的酶活性增强 | 未明确提及 | Discussion（间接提及） |
| AlphaFold 3.0模型未经实验验证 | 预测的TET2-OGT-DNA复合物结构缺乏晶体结构或冷冻电镜验证 | 未明确提及 | Results 图5A（模型置信度评估） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| TET2-OGT互作通过Co-IP证明，但未进行内源互作的定量比较 | Co-IP可能捕获间接互作；未比较TET2-OGT互作强度与TET2-TET3或其他互作蛋白 | 互作的特异性和强度决定功能重要性 | 进行定量免疫共沉淀（qCo-IP）或PLA（邻位连接分析） | Results 图4F |
| AlphaFold 3.0预测的TET2-OGT-DNA复合物缺乏实验验证 | AlphaFold 3.0对多蛋白-DNA复合物的预测准确性有限，尤其对 intrinsically disordered regions | 结构模型是论文核心claim（C端互作）的重要支持 | 进行交联质谱（crosslinking-MS）或氢氘交换质谱（HDX-MS）验证 | Results 图5A |
| 维生素C和DMF处理实验未排除脱靶效应 | 维生素C和DMF可能通过TET2非依赖性途径影响B细胞 | 代谢调控结论的因果性依赖TET2特异性 | 使用TET2催化失活突变体（如HxD突变）进行回补实验 | Results 图6-7 |
| 未评估TET2-OGT轴在人类B细胞淋巴瘤中的角色 | TET2在DLBCL中频繁突变，但本文未探讨其与OGT互作的病理意义 | 临床转化潜力 | 在DLBCL细胞系或患者样本中检测TET2-OGT互作状态 | Discussion（提及DLBCL） |
| 未进行TET2-OGT互作的定量结合测定 | 未提供Kd或结合亲和力数据 | 互作强度决定OGT招募效率 | 进行SPR或ITC实验 | 未提供 |

## 14 学到什么
**Agent 提炼的知识候选**:

1. **DNA结合蛋白的非催化功能（adaptor function）**: TET2通过C端招募OGT，这一机制提示在研究TF-DNA互作时，不应仅关注DNA结合域和转录调控域，还应考虑TF作为"平台"招募染色质修饰酶的能力。可迁移至课题：在研究TF-DNA结合时，可系统筛查TF的互作蛋白，特别是染色质修饰酶。

2. **AlphaFold 3.0用于蛋白质-DNA-蛋白质三元复合物预测**: 本文展示了AlphaFold 3.0在无实验结构情况下预测TET2-OGT-DNA复合物的能力。可迁移至课题：对于缺乏晶体结构的TF-DNA复合物，可使用AlphaFold 3.0生成候选结构，指导突变设计和功能验证。

3. **代谢-表观遗传轴在基因调控中的角色**: TET2作为代谢传感器（依赖α-KG、Fe++），其活性受代谢物（维生素C、富马酸）调控。可迁移至课题：在研究TF-DNA结合时，可考虑代谢物对TF活性或DNA结合亲和力的影响。

4. **MeDIP/hMeDIP-seq用于检测DNA甲基化状态**: 本文使用MeDIP/hMeDIP-seq检测Aicda/Prdm1位点的5mC/5hmC分布，结合ChIP-qPCR验证蛋白-DNA结合。可迁移至课题：在研究TF-DNA互作时，可结合DNA甲基化数据（5mC/5hmC）分析TF结合位点的表观遗传状态。

5. **B细胞分化体系作为研究TF-DNA互作的模型**: 本文使用体外B细胞活化分化体系（LPS±IL-4、CD154±IL-4）研究TET2功能。可迁移至课题：B细胞分化体系可用于研究TF在细胞命运决定中的DNA结合动态变化。

6. **O-GlcNAcylation作为TF活性的翻译后修饰**: TET2的O-GlcNAcylation影响其稳定性和功能。可迁移至课题：在研究TF-DNA结合时，可考虑TF的翻译后修饰（特别是O-GlcNAcylation）对DNA结合亲和力和特异性的影响。

## 15 与已有知识连接
- **TET蛋白家族与DNA去甲基化**: 本文与Tahiliani et al. (2009) 和 Ito et al. (2010) 关于TET蛋白催化5mC氧化的研究直接相关。本文在B细胞中验证了TET2的催化功能，并扩展了其非催化功能。
- **TET2在免疫细胞中的功能**: 与Dominguez et al. (2018) 和 Lio et al. (2019) 关于TET2在B细胞和T细胞中功能的研究一致。本文进一步明确了TET2通过OGT互作调控Aicda/Prdm1的机制。
- **OGT与O-GlcNAcylation在染色质调控中的角色**: 与Chen et al. (2013) 和 Vella et al. (2013) 在ESC中发现的TET1-OGT互作一致。本文在B细胞中验证了TET2-OGT互作，并扩展到H2B-S112修饰。
- **AlphaFold系列在复合物预测中的应用**: 与Jumper et al. (2021) 和 Abramson et al. (2024) 关于AlphaFold 2/3的突破性工作相关。本文是AlphaFold 3.0在蛋白质-DNA-蛋白质三元复合物预测中的实际应用案例。
- **代谢物对TET酶活性的调控**: 与Blaschke et al. (2013) 关于维生素C增强TET活性的研究一致。本文在B细胞中验证了维生素C对TET2功能的增强作用。
- **候选方向（未验证）**: TET2-OGT互作是否在其他DNA结合蛋白（如经典TF）中保守？O-GlcNAcylation是否普遍调控TF的DNA结合能力？这些方向可结合AI结构预测和实验验证进行探索。

## 16 研究想法
**Agent 生成的研究候选**:

1. **候选名称**: TF-O-GlcNAc-DNA三元复合物的AI结构预测与验证
   - **来源局限/观察**: 本文用AlphaFold 3.0预测TET2-OGT-DNA复合物，但未进行实验验证。O-GlcNAcylation对TF-DNA结合的影响缺乏系统性研究。
   - **核心假设**: 对已知TF（如p53、NF-κB）的O-GlcNAcylation位点进行预测，并验证这些修饰是否影响TF的DNA结合亲和力和特异性。
   - **初步方法**: 使用AlphaFold 3.0预测TF-O-GlcNAc转移酶（OGT）-DNA三元复合物；结合分子动力学（MD）模拟O-GlcNAc修饰对TF-DNA结合自由能的影响；用EMSA和SPR实验验证。
   - **验证方式**: 比较O-GlcNAc修饰与未修饰TF的DNA结合亲和力（SPR）、结合位点偏好（ChIP-seq）和转录活性（报告基因）。
   - **创新状态**: unverified

2. **候选名称**: 基于深度学习的TF-DNA结合位点表观遗传状态预测
   - **来源局限/观察**: 本文发现TET2介导的DNA去甲基化与H2B-S112 O-GlcNAcylation协同促进Aicda/Prdm1表达。TF-DNA结合可能受局部DNA甲基化和组蛋白修饰状态影响。
   - **核心假设**: 整合DNA甲基化（5mC/5hmC）和组蛋白修饰（H2B-S112 O-GlcNAc）数据可提高TF-DNA结合位点预测的准确性。
   - **初步方法**: 构建多模态深度学习模型（如CNN+Transformer），输入DNA序列、甲基化状态和组蛋白修饰数据，预测TF结合位点；使用本文的MeDIP/hMeDIP-seq和ChIP-seq数据作为训练集。
   - **验证方式**: 在独立数据集上评估预测性能（AUROC、AUPRC）；用ChIP-seq实验验证新预测的TF结合位点。
   - **创新状态**: unverified

3. **候选名称**: 代谢物-TF-DNA互作网络：从TET2到经典TF的扩展
   - **来源局限/观察**: 本文证明TET2受代谢物（维生素C、富马酸）调控。其他TF是否也受代谢物直接调控？
   - **核心假设**: 代谢物（如α-KG、琥珀酸、富马酸）通过影响TF的DNA结合域或共调控因子，系统性调控TF-DNA互作。
   - **初步方法**: 使用代谢物-蛋白质互作预测工具（如AlphaFold 3.0）筛选代谢物与TF DNA结合域的潜在结合位点；用MD模拟验证结合稳定性；用细胞实验验证代谢物对TF-DNA结合的影响。
   - **验证方式**: 在B细胞分化体系中，比较不同代谢物处理下TF的ChIP-seq结合谱变化。
   - **创新状态**: unverified

4. **候选名称**: TET2-OGT互作界面的分子动力学模拟与突变设计
   - **来源局限/观察**: 本文用AlphaFold 3.0预测了TET2-OGT互作界面，但未进行MD模拟或系统突变分析。
   - **核心假设**: TET2 C端（G1876-V1920）与OGT的互作界面可通过MD模拟获得动态结构信息，指导设计破坏互作的突变体。
   - **初步方法**: 对AlphaFold 3.0预测的TET2-OGT复合物进行MD模拟（如GROMACS），分析互作界面的氢键、疏水接触和结合自由能（MM-PBSA）；设计界面突变体，用Co-IP验证。
   - **验证方式**: 突变体在B细胞中丧失OGT招募能力，导致Aicda/Prdm1表达下降和抗体应答受损。
   - **创新状态**: unverified

5. **候选名称**: 基于结构预测的TF-DNA结合特异性重编程
   - **来源局限/观察**: 本文展示了AlphaFold 3.0在蛋白质-DNA复合物预测中的能力。TF的DNA结合特异性可通过结构预测进行工程改造。
   - **核心假设**: 通过AlphaFold 3.0预测TF-DNA复合物结构，可设计TF突变体，使其结合新的DNA基序。
   - **初步方法**: 选择已知TF（如AID的调控因子），用AlphaFold 3.0预测其与不同DNA序列的结合；用深度学习评分函数（如DeepBind）筛选高亲和力突变体；用细菌单杂交或SELEX实验验证。
   - **验证方式**: 工程化TF在B细胞中驱动异源基因表达，或改变内源靶基因的表达谱。
   - **创新状态**: unverified