## 01 基本信息
- **标题**：Characterization of promoter elements of isoprene-responsive genes and the ability of isoprene to bind START domain transcription factors
- **作者与单位**：Weraduwage, Sarathi M; Sahu, Abira; Kulke, Martin; Vermaas, Josh V; Sharkey, Thomas D（单位未在摘要中提供，推测为 Michigan State University，因致谢提及该校 Growth Chamber Facility）
- **期刊/预印本平台**：Plant Direct
- **年份**：2023-02-07
- **论文类型**：研究论文（结合生物信息学分析与分子模拟）
- **领域**：植物信号传导、转录调控、异戊二烯（isoprene）生物学
- **关键词**：cis-regulatory elements (CREs)、isoprene signaling、START domain、HD-ZIP transcription factors、molecular dynamics
- **DOI/arXiv 号**：10.1002/pld3.483
- **代码**：未提供
- **数据**：支持信息（Table S1–S4, Figure S1）；基因列表来自 Zuo et al. (2019)
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦植物转录因子（TF）与顺式调控元件（CRE）的互作，并尝试用分子模拟检验小分子配体（isoprene）与 TF 的 START 结构域结合的可能性。对「TF–DNA 结合机制 × 物理模拟」方向而言，本文提供了一个「配体–TF–DNA」三方互作的负结果案例，并展示了如何用 CRE 富集分析反推上游 TF 网络，方法可迁移至其他 TF–DNA 互作研究。

## 02 一句话总结
本文通过分析异戊二烯响应基因启动子中的顺式调控元件（CRE）富集情况，推断参与异戊二烯信号传导的转录因子（主要为 ARR1、Dof、bHLH112、GATA、MYB、WRKY 等），并用分子模拟检验异戊二烯能否结合 HDG11 的 START 结构域，结果未检测到特异性结合。

## 03 研究问题
- **具体问题**：异戊二烯（isoprene）作为信号分子如何调控植物基因表达？哪些转录因子参与其中？异戊二烯是否直接结合 START 结构域蛋白（如 HDG11）？
- **为什么重要**：异戊二烯是植物释放量最大的生物挥发性有机物，可增强植物对高温、干旱、臭氧和虫害的耐受性，但其感知机制完全未知。明确其信号通路对理解植物胁迫适应和异戊二烯排放性状的进化具有重要意义。
- **现有方法为何不足**：转录组研究（Zuo et al., 2019）已鉴定出异戊二烯响应基因，但未系统分析其启动子中的 CRE，也未鉴定上游 TF；且异戊二烯的感知受体完全未知。
- **精确研究问题**：Can the promoter regions of isoprene-responsive genes reveal the transcription factors involved in isoprene signaling, and can isoprene directly bind to the START domain of HDG11?

## 04 背景与发展脉络
- **阶段一：异戊二烯功能假说**（2000s–2010s）：早期认为异戊二烯是膜稳定剂或抗氧化剂（Sharkey et al., 2001; Vickers et al., 2009）。局限：Harvey et al. (2015) 通过浓度计算否定了这两种假说。
- **阶段二：异戊二烯作为信号分子**（2015–2019）：转录组和蛋白组研究表明异戊二烯可改变基因表达（Harvey & Sharkey, 2016; Zuo et al., 2019; Dani et al., 2022）。局限：仅描述现象，未揭示信号传导机制。
- **阶段三：CRE 分析与受体鉴定**（本文，2023）：通过启动子 CRE 富集分析推断上游 TF，并用分子模拟检验候选受体（START 结构域蛋白）。局限：模拟未检测到结合，受体仍未知。
- **脉络标注**：以上脉络为「经外部核验」——各阶段代表性文献在原文引言中均有引用（Dani et al., 2022; Harvey & Sharkey, 2016; Vanzo et al., 2016; Zuo et al., 2019; Behnke et al., 2007, 2010; Sharkey et al., 2001, 2013; Affek & Yakir, 2002; Schwender et al., 1997; Tattini et al., 2014; Loreto et al., 2001; Singsaas et al., 1997; Velikova et al., 2011; Vickers, Possell, et al., 2009; Pollastri et al., 2021; Harvey et al., 2015; Dani et al., 2021; Parveen et al., 2019; Mayrhofer et al., 2005; Park et al., 2015; Zhao et al., 2020; Loivamäki et al., 2007; Sasaki et al., 2013; Sun et al., 2013; Velikova & Loreto, 2005; Ikeda et al., 2009; Lindermayr et al., 2010; Khosla, 2015; Schrick et al., 2004, 2014; Jentsch et al., 2018; Kudo et al., 2019; Nakao et al., 2019; Vermaas & Tajkhorshid, 2017; Baek et al., 2021; Kulke et al., 2018; Phillips et al., 2020; Palaniswamy et al., 2006; Yilmaz et al., 2010; Davuluri et al., 2003; Siwko et al., 2007; Filser et al., 1996; Gargas et al., 1989）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 异戊二烯感知受体未知 | 无法解释异戊二烯如何启动信号传导 | 异戊二烯浓度低、挥发性强，传统生化方法难以追踪；START 结构域是候选但缺乏实验验证 | Discussion: "proteins involved in the putative isoprene-signaling pathway are not known" |
| 转录组数据无法直接揭示上游调控因子 | 仅知道基因表达变化，不知道哪些 TF 驱动这些变化 | 转录组数据不包含调控信息，需通过启动子 CRE 分析反推 | Introduction: "characterization of important cis-regulatory elements (CREs) in promoters of isoprene-responsive genes and their corresponding TFs is yet to be done" |
| 异戊二烯在膜内富集但蛋白无法接触 | 模拟显示 HDG11 START 结构域不深入膜内，无法接触膜内异戊二烯 | START 结构域是水溶性蛋白，缺乏膜插入能力 | Results: "protein residues did not typically come into close contact with the membrane... Without membrane penetration by the HDG11 START domain, isoprene within the lipid bilayer was inaccessible" |
| 异戊二烯-蛋白互作缺乏特异性 | 水相中异戊二烯与 START 结构域仅发生短暂非特异性接触 | 异戊二烯是小的疏水分子，在水相中浓度极低，缺乏特异性结合位点 | Results: "The low isoprene concentration in the aqueous phase engaged in short, nonspecific interactions with the START domain" |

## 06 核心思想
1. **表面方法**：对异戊二烯响应基因（来自 Zuo et al., 2019 的 61 个上调和 54 个下调基因）的启动子区域（上游 3 kb）进行 CRE 富集分析，使用拟南芥 CRE 数据库（AtcisDB/AGRIS）；对富集的 CRE 对应的 TF 进行功能分类；对候选受体 HDG11 的 START 结构域进行同源建模、副本交换分子动力学模拟和膜互作模拟。
2. **核心洞察**：异戊二烯信号传导可能通过「劫持」已有的胁迫信号通路实现——异戊二烯响应基因的启动子富集了 ABA、JA、SA 等胁迫激素响应的 CRE，且这些 CRE 对应的 TF（MYB、WRKY、Dof 等）本身就是胁迫信号通路的核心组分。这意味着异戊二烯不需要全新的信号通路，而是通过调控已有通路的 TF 活性来发挥作用。同时，START 结构域蛋白作为直接受体的假说被模拟结果否定。
3. **可能的普适教训** [Analysis]：当一个小分子配体的直接受体难以鉴定时，通过下游基因启动子的 CRE 富集分析反推上游 TF 网络是一种高效的替代策略；分子模拟的负结果同样有价值——它排除了一个候选受体，缩小了搜索空间。

## 07 方法总览
- **输入**：
  - 异戊二烯响应基因列表（61 上调 + 54 下调，来自 Zuo et al., 2019，三个模式系统：异戊二烯熏蒸的野生型拟南芥、表达桉树 ISPS 的拟南芥、表达银白杨 ISPS 的烟草）
  - 拟南芥 CRE 数据库（AtcisDB）
  - HDG11 蛋白序列（UniProt Q9FX31）
- **输出**：
  - 富集/缺失的 CRE 列表及其对应 TF
  - HDG11 START 结构域的原子模型及与异戊二烯/膜互作的模拟轨迹
- **模块**：
  1. CRE 富集分析（启动子 3 kb 区域，阈值：≥75% 富集 = overrepresented；50–74% = moderately overrepresented；≤49% = underrepresented）
  2. TF 功能分类（基于文献和 AGRIS 数据库）
  3. HDG11 START 结构域同源建模（RoseTTAfold）
  4. 副本交换分子动力学模拟（TIGER2h 方法，NAMD 3.0a9 软件）
  5. 膜互作模拟（START 结构域置于含/不含异戊二烯的类囊体膜模型上方）
- **训练**：不适用（无监督学习/物理模拟）
- **工具**：AtcisDB、AGRIS、RoseTTAfold、TIGER2h、NAMD 3.0a9
- **反馈回路**：无（单轮分析）
- **假设**：① 异戊二烯响应基因的启动子 CRE 富集能反映上游 TF 的参与；② START 结构域是异戊二烯的候选受体；③ 类囊体膜是异戊二烯在叶绿体内的主要富集场所
- **文字流程**：基因列表 → 提取启动子 3 kb → 数据库比对 CRE → 统计富集/缺失 → 映射 TF → 功能分类 → 选择 HDG11 作为候选受体 → 同源建模 → 副本交换模拟采样构象 → 膜互作模拟 → 分析结合/接触 → 得出结论

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CRE 富集分析 | 鉴定异戊二烯响应基因启动子中统计显著的 CRE | 转录组数据不含调控信息，需通过启动子序列反推上游 TF | 输入：基因列表 + 启动子序列；输出：富集/缺失 CRE 列表 | Results 表 1、图 2；22 个 overrepresented CREs（上调基因），10 个（下调基因） | 无法推断参与异戊二烯信号的 TF 种类 |
| TF 映射与功能分类 | 将 CRE 对应到具体 TF 并归类其功能 | 确定哪些信号通路被异戊二烯激活 | 输入：CRE 列表；输出：TF 列表及功能注释 | Results: "CREs that bind ARR1, Dof, DPBF, bHLH112, GATA factors, GT-1, MYB, and WRKY TFs" | 无法判断异戊二烯信号与哪些通路交叉 |
| HDG11 同源建模 | 生成 START 结构域的 3D 结构 | 无实验结构，需计算模型进行后续模拟 | 输入：蛋白序列；输出：原子模型 | Methods: "homology modeled with the RoseTTAfold web server" | 无法进行结合模拟 |
| 副本交换分子动力学 | 采样 START 结构域的构象系综 | 单结构可能不代表生理构象，需广泛采样 | 输入：初始模型；输出：构象簇（4 簇） | Results 图 3a,b,d；"free energy minimum located in cluster 4" | 可能错过真实结合构象 |
| 膜互作模拟 | 检验 START 结构域能否接触膜内异戊二烯 | 异戊二烯主要富集在膜内，蛋白需接触膜才能结合 | 输入：START 结构域 + 类囊体膜模型 ± 异戊二烯；输出：接触轨迹 | Results 图 3c,e,f；"protein residues did not typically come into close contact with the membrane" | 无法评估膜介导的配体结合假说 |

## 09 关键公式符号
不适用——本文未使用定量公式，核心分析为 CRE 富集统计（阈值判定）和分子动力学模拟（无显式公式在正文中给出）。富集判定标准为：≥75% 启动子含某 CRE = overrepresented；50–74% = moderately overrepresented；≤49% = underrepresented（Methods 节）。

## 10 实验设计与证据链
- **数据集**：61 个上调 + 54 个下调的异戊二烯响应基因（来自 Zuo et al., 2019，三个模式系统交集）
- **规模**：115 个基因的启动子区域（上游 3 kb）
- **指标**：CRE 出现频率（百分比）、富集/缺失分类
- **基线**：无明确基线（以 75%/50% 阈值为判定标准）
- **预算**：未提供
- **骨干/仪器**：AtcisDB 数据库、RoseTTAfold 服务器、NAMD 3.0a9
- **oracle 输入**：异戊二烯响应基因列表（来自已发表转录组数据）
- **评测协议**：CRE 频率统计 + 文献交叉验证 TF 功能；分子模拟以接触距离和互作能量为指标

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| CRE 富集分析（上调基因） | 异戊二烯响应基因启动子富集特定 CRE | 22 个 CREs ≥75% 阈值 | 富集 ABA、JA、SA 响应元件及 MYB、WRKY、Dof 结合位点 | 异戊二烯信号与胁迫激素通路交叉 | 不能证明这些 TF 确实被异戊二烯激活 | Results 表 1、图 2 |
| CRE 富集分析（下调基因） | 下调基因启动子有不同 CRE 特征 | 10 个 CREs ≥75% 阈值 | 与上调基因部分重叠（7 个共有） | 上/下调基因共享部分调控逻辑 | 不能解释方向性调控机制 | Results 表 1 |
| HDG11 START 结构域建模 | 可获得可靠的 START 结构域模型 | 同源建模 + 副本交换采样 | 4 个构象簇，簇 4 为自由能最低 | 模型可用于结合模拟 | 模型精度未与实验结构对比 | Results 图 3a,b,d |
| 膜互作模拟 | START 结构域能接触膜内异戊二烯 | 含/不含异戊二烯的类囊体膜 | 蛋白残基距膜表面约 3 nm，无深插入 | START 结构域不深入膜内 | 不能完全排除其他 START 蛋白可插入膜 | Results 图 3c,e,f |
| 异戊二烯结合模拟 | 异戊二烯特异性结合 START 结构域 | 水相中异戊二烯与蛋白互作 | 仅短暂非特异性接触 | 未检测到特异性结合位点 | 不能排除其他 START 蛋白可结合异戊二烯 | Results 图 3e |

## 11 结论正确解读
- **任务范围**：本文仅覆盖拟南芥（及转基因烟草）中异戊二烯响应基因的启动子分析，以及 HDG11 一个 START 蛋白的模拟。结论不适用于其他物种或所有 START 家族蛋白。
- **oracle/真值输入**：基因列表来自转录组数据（Zuo et al., 2019），该数据本身有实验条件依赖性；CRE 数据库为拟南芥注释，可能不完整。
- **端到端状态**：非端到端——CRE 分析是计算预测，未用实验（如 ChIP-seq、EMSA）验证 TF 确实结合这些启动子；分子模拟是计算预测，未用实验（如 ITC、NMR）验证结合。
- **算力成本**：未提供具体算力信息，但副本交换模拟通常需要大量计算资源。
- **历史数据依赖**：依赖 Zuo et al. (2019) 的转录组数据，该数据基于特定实验条件（20 μl/L 异戊二烯熏蒸 24 h 或转基因表达）。
- **模型依赖**：HDG11 结构为同源建模，依赖模板结构质量；膜模型为类囊体膜简化模型。
- **最难情形**：异戊二烯是挥发性小分子，实验验证其与蛋白结合极为困难；START 结构域家族成员众多，逐一验证不现实。
- **群体/领域边界**：结论仅适用于植物（特别是拟南芥）；对动物或微生物的异戊二烯感知无直接推论。
- **不确定性**：作者明确表示「it has not been possible to say how isoprene is sensed to initiate signaling responses」——即感知机制完全未解决。
- **有边界的复述**：在拟南芥中，异戊二烯响应基因的启动子富集了胁迫激素相关 CRE，提示异戊二烯信号与胁迫信号通路交叉；但 HDG11 的 START 结构域不太可能是异戊二烯的直接受体，因为模拟显示该结构域无法接触膜内富集的异戊二烯。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 感知机制未解决 | "it has not been possible to say how isoprene is sensed to initiate signaling responses" | 未明确提及 | Discussion 末段 |
| 模拟的负结果不能完全排除其他 START 蛋白 | 仅测试了 HDG11 一个蛋白 | 未明确提及 | Discussion: "The investigated START domain of HDG11 is probably not such a receptor protein" |
| 转录组数据来源限制 | 基因列表来自三个特定模式系统 | 未明确提及 | Methods: "common to two or all three of the following model systems" |
| 同源建模的精度限制 | 无实验结构，模型依赖模板 | 未明确提及 | Methods: "homology modeled with the RoseTTAfold web server" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| CRE 富集分析仅基于序列 motif 频率，未考虑染色质可及性 | 启动子中存在的 motif 不一定被 TF 结合；异戊二烯可能通过表观遗传改变染色质状态 | 若 motif 富集但实际不结合，则推断的 TF 网络可能不准确 | 用 ATAC-seq 或 DNase-seq 验证异戊二烯处理后的染色质可及性变化 | Methods 仅描述序列分析，无表观数据 |
| HDG11 模拟仅测试了类囊体膜 | 异戊二烯可能在细胞质或核膜中发挥作用，START 结构域可能在其他膜环境中接触配体 | 若异戊二烯在非类囊体膜中感知，则模拟结论不适用 | 测试其他膜系统（质膜、内质网、核膜）中的互作 | Results 图 3c 仅展示类囊体膜结果 |
| 未测试异戊二烯代谢产物 | 异戊二烯可能被代谢为活性分子（如异戊烯醇）后再与蛋白结合 | 若信号分子是代谢产物而非异戊二烯本身，则整个受体搜索方向需调整 | 用同位素标记异戊二烯追踪代谢产物 | 原文未提及代谢转化 |
| 模拟中异戊二烯浓度可能不生理 | 未报告模拟中异戊二烯的浓度设置 | 若浓度远高于生理水平，则观察到的互作可能为假阳性 | 查阅支持信息中的模拟参数 | 原文未在正文报告浓度 |
| 上调/下调基因的 CRE 差异未深入分析 | 仅列出共有和特有 motif，未解释方向性调控的机制 | 理解异戊二烯如何同时激活和抑制不同基因是信号机制的核心 | 分析上/下调基因启动子的位置权重矩阵差异 | Results 表 1 仅列出 motif 名称 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **CRE 富集分析反推 TF 网络的方法**：当研究一个信号分子（如异戊二烯）的转录响应时，可先获取响应基因列表，再对其启动子进行 motif 富集分析，从而推断上游 TF。此方法可迁移至「TF–DNA 互作」课题：对于任何感兴趣的 TF，可反向收集其靶基因，分析靶基因启动子中该 TF 的 motif 是否富集，验证 ChIP-seq 结果。
2. **配体–TF 互作的模拟策略**：本文展示了「同源建模 → 副本交换采样 → 膜互作模拟」的流程，用于检验小分子配体与 TF 结构域的结合。此流程可迁移至「TF–DNA 结合机制」研究：若怀疑某代谢物或激素可调控 TF 的 DNA 结合活性，可用类似流程先做计算筛选，再实验验证。
3. **负结果的价值**：模拟未检测到结合，但作者仍将其作为完整证据链的一部分发表。这提示在 TF–配体互作研究中，计算负结果可以排除候选受体，避免后续实验资源的浪费。
4. **膜定位对配体–蛋白互作的重要性**：异戊二烯在膜内富集，但 START 结构域不插入膜，导致无法接触配体。这一「空间可达性」概念可迁移至 TF–DNA 研究：某些 TF 可能通过膜锚定或相分离改变其与 DNA 的可及性，计算模拟时应考虑亚细胞定位。
5. **多激素信号通路交叉的 CRE 分析**：异戊二烯响应基因同时富集 ABA、JA、SA 的响应元件，提示信号分子可能通过「汇聚」到已有通路上发挥作用。此思路可迁移至 TF–DNA 研究：分析某 TF 的靶基因启动子时，若发现多个激素响应 motif 共存，可能提示该 TF 是多种信号通路的交汇节点。

## 15 与已有知识连接
- **START 结构域家族**：本文引用了 Schrick et al. (2004, 2014) 和 Khosla (2015) 关于 START 结构域结合脂质配体的研究。START 结构域在哺乳动物中已知可结合甾醇类配体（如 STARD1 结合胆固醇），本文将其扩展到植物 HD-ZIP IV 家族。可连接至 Pfam 数据库 PF01852 家族。
- **HD-ZIP IV 家族**：GL2、ATML1、PDF2、HDG11 等是植物表皮发育和胁迫响应的关键 TF。本文发现这些 TF 的结合 motif（L1 box）在异戊二烯响应基因中富集，可连接至已知的 HD-ZIP IV 靶基因研究。
- **异戊二烯信号假说**：本文直接承接 Zuo et al. (2019) 和 Harvey & Sharkey (2016) 的转录组工作，以及 Dani et al. (2022) 的综述。异戊二烯作为信号分子的假说目前仍处于早期阶段。
- **分子模拟方法**：本文使用 RoseTTAfold（Baek et al., 2021）进行结构预测，TIGER2h（Kulke et al., 2018）进行副本交换采样，NAMD（Phillips et al., 2020）进行分子动力学模拟。这些工具可连接至 AlphaFold2、GROMACS 等常用结构预测和模拟工具。
- **CRE 数据库**：AtcisDB（Palaniswamy et al., 2006; Yilmaz et al., 2010）是拟南芥 cis-regulatory element 的权威数据库，可连接至 JASPAR、TRANSFAC 等真核 TF 结合位点数据库。
- **[Analysis] 可迁移方向**：本文的「配体–TF–DNA」三方互作框架可扩展至其他植物挥发性信号（如萜烯类、绿叶挥发物）的感知机制研究；其 CRE 富集分析方法也可用于非模式植物的比较基因组学分析。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：基于深度学习的 TF–DNA 结合特异性预测模型整合 CRE 富集先验
   - **来源局限/观察**：本文的 CRE 富集分析仅基于序列 motif 频率，未考虑 TF 的 DNA 结合域结构特征；现有深度学习模型（如 DeepBind、DeepSEA）虽能预测 TF 结合，但未利用启动子层面的 motif 共富集信息。
   - **核心假设**：将 CRE 共富集信息作为先验特征输入深度学习模型，可提高 TF–DNA 结合预测的准确性，特别是在低亲和力结合位点。
   - **初步方法**：收集拟南芥 TF 的 ChIP-seq 数据，提取靶基因启动子 motif 共富集模式，作为注意力机制的先验输入到 CNN/Transformer 模型中。
   - **验证方式**：与 DeepBind、Basenji 在拟南芥 TF 数据集上比较 AUC 和 PR-AUC。
   - **创新状态**：unverified

2. **候选名称**：分子动力学模拟揭示 TF 构象变化对 DNA 结合亲和力的调控
   - **来源局限/观察**：本文用 MD 模拟检验配体结合，但未研究 TF 的 DNA 结合构象变化；已知 TF 常通过构象变化（如折叠偶联结合）调节 DNA 亲和力。
   - **核心假设**：START 结构域或其他配体结合结构域与配体结合后，可通过变构效应改变 TF 的 DNA 结合域构象，从而调节 DNA 结合亲和力。
   - **初步方法**：对 HD-ZIP IV 家族 TF 进行配体结合/未结合的对照 MD 模拟，比较 DNA 结合域的构象系综和结合自由能（MM-PBSA）。
   - **验证方式**：用表面等离子体共振（SPR）或荧光各向异性实验验证模拟预测的亲和力变化。
   - **创新状态**：unverified

3. **候选名称**：异戊二烯响应基因启动子的进化分析揭示 TF 结合位点的保守性
   - **来源局限/观察**：本文仅分析了拟南芥的 CRE 富集，未涉及进化保守性；异戊二烯排放性状在植物中多次独立进化，其响应基因的调控元件可能具有保守特征。
   - **核心假设**：异戊二烯响应基因启动子中的关键 CRE（如 MYB、WRKY 结合位点）在异戊二烯排放植物中保守，在非排放植物中不保守。
   - **初步方法**：收集多个物种（排放与非排放）的直系同源基因启动子，比较 CRE 的保守性和富集差异。
   - **验证方式**：系统发育独立对比分析（PIC）控制物种亲缘关系。
   - **创新状态**：unverified

4. **候选名称**：基于 AlphaFold 的 START 结构域配体结合位点预测与虚拟筛选
   - **来源局限/观察**：本文用 RoseTTAfold 建模但未做配体对接；START 结构域的配体结合位点可能具有可预测的特征。
   - **核心假设**：AlphaFold 预测的 START 结构域结构中，保守的疏水口袋是配体结合位点，可用于虚拟筛选候选配体。
   - **初步方法**：对拟南芥所有 START 结构域蛋白进行 AlphaFold 预测，用 FPocket 检测结合口袋，用 AutoDock Vina 对接候选配体（包括异戊二烯、脂肪酸、甾醇）。
   - **验证方式**：对得分最高的配体-蛋白对进行 MD 模拟验证结合稳定性。
   - **创新状态**：unverified

5. **候选名称**：TF–DNA 结合与配体结合的协同效应：以 HD-ZIP IV 家族为模型
   - **来源局限/观察**：本文分别检验了 CRE 结合（通过启动子分析）和配体结合（通过 MD 模拟），但未考虑两者的协同性；HD-ZIP IV 的 START 结构域和 DNA 结合域（HD）可能功能耦合。
   - **核心假设**：配体结合 START 结构域可改变 HD 结构域的 DNA 结合特异性或亲和力，形成「配体–TF–DNA」三体协同调控。
   - **初步方法**：对 HD-ZIP IV 蛋白进行「配体结合/未结合 × DNA 结合/未结合」的四组 MD 模拟，比较自由能变化和构象耦合。
   - **验证方式**：用等温滴定量热法（ITC）测量配体存在/不存在时的 TF–DNA 结合热力学参数。
   - **创新状态**：unverified