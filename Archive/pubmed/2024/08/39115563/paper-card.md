## 01 基本信息
- **标题**：Structural characterization of DNA-binding domain of essential mammalian protein TTF 1
- **作者**：Singh, Gajender; Bhopale, Abhinetra Jagdish; Khatri, Saloni; Prakash, Prashant; Kumar, Rajnish; Singh, Sukh Mahendra; Singh, Samarendra Kumar
- **单位**：Institute of Science, Banaras Hindu University (BHU), Varanasi, India（基于致谢部分推断）
- **期刊/平台**：Bioscience Reports
- **年份**：2024-08-08
- **论文类型**：实验 + 计算（结构预测与生物物理表征）
- **领域**：结构生物学、蛋白质-DNA互作、转录终止因子
- **关键词**：TTF1、Myb domain、DNA-binding、homology modelling、molecular dynamics simulation、CD spectroscopy、Raman spectroscopy
- **DOI/arXiv 号**：10.1042/BSR20240800
- **代码**：未提供
- **数据**：未提供（文中声明数据在稿件中）
- **阅读日期**：2025-05-13
- **在课题方向中的位置**：本文聚焦转录因子 TTF1 的 Myb DNA-binding domain 的结构预测与实验验证，属于「TF–DNA 结合机制 × 结构预测/AI 辅助建模」方向。其核心价值在于：① 对无实验结构的 TF DNA-binding domain 采用多方法（homology + ab initio）建模并交叉验证；② 通过 MD 模拟评估结构稳定性；③ 用 CD/Raman 光谱实验验证计算模型的二级结构预测。对课题的可迁移点在于「计算-实验闭环验证」策略，而非新 AI 方法本身。

## 02 一句话总结
本文通过 homology modelling（SWISS-MODEL）和 ab initio（Robetta、I-TASSER、AlphaFold）方法预测小鼠 TTF1 蛋白 Myb DNA-binding domain 的 3D 结构，经 200 ns MD 模拟（三重复）确认其稳定性，并通过克隆表达、CD 和 Raman 光谱实验验证该 domain 以 α-helix 为主（~65%），且单独即可结合 Sal Box DNA。

## 03 研究问题
- **具体问题**：TTF1 蛋白的 Myb DNA-binding domain 的三维结构是什么？该 domain 是否单独足以结合 Sal Box DNA？
- **为什么重要**：TTF1 是哺乳动物必需蛋白，参与 Pol I 转录终止、rRNA 加工、染色质重塑、DNA 损伤修复和复制叉停滞等多种关键过程。其结构未知是理解这些功能机制的主要瓶颈。此前纯化全长 TTF1 蛋白失败，阻碍了实验结构解析。
- **现有方法为何不足**：全长 TTF1 蛋白难以纯化（形成聚集体），无法进行 X 射线晶体学或 NMR 结构解析；且该 domain 与已知模板序列一致性仅 27%（"twilight zone"），单一建模方法可靠性存疑。
- **精确研究问题**：Can a combination of homology modelling, ab initio prediction, and MD simulation produce a reliable structural model of the TTF1 Myb domain that is consistent with experimental biophysical characterization (CD, Raman) and functional DNA-binding activity (EMSA)?

## 04 背景与发展脉络
> 注：以下脉络基于本文框架及引用文献，标注「仅本文框架」或「经外部核验」。

- **阶段一：TF 终止因子的功能研究（~1990s-2000s）**：TTF1 被鉴定为 Pol I 转录终止因子，结合 Sal Box 序列。功能研究为主，结构信息缺失。代表：Grummt 等的工作（本文引用 [2,3]）。局限：无结构信息，机制理解受限。
- **阶段二：同源蛋白结构解析（~2010s）**：酵母同源蛋白 Reb1（S. pombe）的 DNA-binding domain 晶体结构被解析（PDB: 5EYB，本文引用 [1]）。这为 TTF1 的 homology modelling 提供了模板。局限：跨物种序列一致性低（27%），直接建模可靠性有限。
- **阶段三：计算结构预测的兴起（~2018-2021）**：AlphaFold、Rosetta、I-TRASSER 等工具成熟，使得无模板或低序列一致性的结构预测成为可能。本文采用多工具交叉验证策略。局限：单一工具预测结果可能偏差，需实验验证。
- **阶段四：计算-实验闭环验证（本文位置）**：本文首次将多方法计算建模 + MD 模拟 + 生物物理实验（CD、Raman）+ 功能实验（EMSA）整合，对 TTF1 Myb domain 进行系统表征。这是「结构预测 + 实验验证」范式的典型应用。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 全长 TTF1 蛋白无法纯化 | 蛋白以聚集体形式洗脱，无法获得均一、功能活性蛋白 | 作者未明确解释成因，推测与 N 端无序区域有关 | Results 节 "Attempts to purify the functional TTF1 protein have been unsuccessful till date" |
| 模板序列一致性低 | Myb domain 与最佳模板（Reb1）序列一致性仅 27%，处于 homology modelling 的 "twilight zone" | 跨物种进化分歧 | Results 节 "Molecular modelling" 段 |
| 单一建模方法不可靠 | 不同服务器（AlphaFold、SWISS-MODEL、Robetta、I-TASSER）预测结构存在差异，I-TASSER 模型质量明显较差 | 各方法算法原理不同，对低一致性序列的适用性不同 | Results 节 表 2：I-TASSER 模型 72.1% 残基在最适区域，4.2% 在不允许区域 |
| 结构-功能关系不明 | 不清楚 Myb domain 单独是否足以结合 DNA | 此前无该 domain 的独立功能研究 | Results 节 EMSA 部分 |

## 06 核心思想
1. **表面方法**：用四种计算工具（AlphaFold、SWISS-MODEL、Robetta、I-TASSER）预测 TTF1 Myb domain 结构，经 MD 模拟筛选稳定构象，再通过克隆表达、CD/Raman 光谱和 EMSA 实验验证。
2. **核心洞察**：① 多方法交叉验证可弥补单一方法在低序列一致性场景下的不足；② 计算预测的二级结构（~65% α-helix）与实验光谱数据高度一致，说明计算模型可信；③ Myb domain 单独即可结合 Sal Box DNA，说明该 domain 是 TTF1 的最小 DNA 结合单元。
3. **[Analysis] 可能的普适教训**：对于难以纯化的 TF 蛋白，采用「domain-level 结构预测 + 多方法交叉验证 + 光谱实验确认二级结构 + 功能实验确认活性」的流程，是绕过全长蛋白纯化瓶颈的有效策略。这一范式可迁移到其他 TF–DNA 互作研究。

## 07 方法总览
- **输入**：小鼠 TTF1 Myb domain 氨基酸序列（UniProt: Q62187，残基 550-732）
- **输出**：Myb domain 的 3D 结构模型、二级结构组成、DNA 结合活性确认
- **模块**：
  1. 序列分析（ProtParam、DisoPred3）
  2. 结构预测（AlphaFold、SWISS-MODEL、Robetta、I-TASSER）
  3. 结构验证（PROCHECK、SAVESv6.0、ProSA、VADAR）
  4. MD 模拟（GROMACS 2020 + CHARMM36，200 ns × 3 重复）
  5. 轨迹分析（RMSD、RMSF、RoG、SASA、FEL）
  6. 克隆表达（pET28a 载体，E. coli BL21 (DE3)）
  7. 蛋白纯化（Ni-NTA 亲和 + 凝胶过滤）
  8. 二级结构表征（CD 光谱）
  9. 结构组成验证（Raman 光谱）
  10. DNA 结合功能（EMSA）
- **流程**：序列获取 → 理化性质分析 → 多方法结构预测 → 结构质量评估 → 选择最优模型（Robetta）→ MD 模拟稳定性验证 → 克隆表达纯化 → CD/Raman 光谱验证二级结构 → EMSA 验证 DNA 结合活性

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 多方法结构预测 | 生成候选 3D 模型 | 单一方法在低序列一致性下不可靠 | 输入：氨基酸序列；输出：4 个候选模型 | Results 图 2、表 2 | [预期] 移除后无法交叉验证，模型可靠性下降 |
| 结构质量评估（PROCHECK/SAVES/ProSA） | 筛选最优模型 | 不同方法输出质量差异大 | 输入：候选模型；输出：质量评分 | Results 表 2、图 3A | [预期] 移除后可能选择低质量模型（如 I-TASSER） |
| MD 模拟（200 ns × 3） | 验证结构动态稳定性 | 静态模型不足以证明生理相关性 | 输入：Robetta 模型；输出：RMSD/RMSF/RoG/SASA 轨迹 | Results 图 4、图 5 | [预期] 移除后无法确认模型在溶液中的稳定性 |
| FEL 分析 | 识别最稳定构象 | 确认模型收敛到能量最低态 | 输入：MD 轨迹；输出：能量景观图 | Results 图 5 | [预期] 移除后无法确认构象稳定性 |
| 克隆表达与纯化 | 获得实验蛋白 | 验证计算模型需要实验数据 | 输入：Myb domain 基因；输出：纯化蛋白 | Results 图 7 | [实测] 全长蛋白纯化失败，domain 可纯化 |
| CD 光谱 | 实验测定二级结构 | 验证计算预测的 α-helix 含量 | 输入：纯化蛋白；输出：二级结构百分比 | Results 图 9 | [预期] 移除后计算模型缺乏实验支持 |
| Raman 光谱 | 交叉验证二级结构 | 多光谱方法增强可信度 | 输入：纯化蛋白；输出：酰胺 I 带拟合 | Results 图 10 | [预期] 移除后 CD 结果缺乏独立验证 |
| EMSA | 验证 DNA 结合功能 | 确认 domain 单独具有功能 | 输入：蛋白 + Sal Box DNA；输出：迁移条带 | Results 图 8 | [实测] 确认 Myb domain 单独可结合 DNA |

## 09 关键公式符号
- **RMSD（Root Mean Square Deviation）**：衡量模拟构象与初始结构的偏差。公式：RMSD = √(1/N Σᵢ₌₁ᴺ δᵢ²)，其中 N 为原子数，δᵢ 为第 i 个原子的位移。用途：判断模拟是否达到平衡。来源：Methods 节 MD 模拟部分。
- **RMSF（Root Mean Square Fluctuation）**：衡量每个残基在模拟中的柔性。公式：RMSFᵢ = √(1/T Σₜ₌₁ᵀ (rᵢ(t) - r̄ᵢ)²)，其中 T 为帧数，rᵢ(t) 为第 i 个残基在 t 时刻的位置，r̄ᵢ 为平均位置。用途：识别柔性区域。来源：Methods 节 MD 模拟部分。
- **RoG（Radius of Gyration）**：衡量蛋白紧凑性。公式：Rg = √(Σᵢ mᵢ|rᵢ - r̄|² / Σᵢ mᵢ)，其中 mᵢ 为原子质量。用途：判断蛋白是否保持折叠。来源：Methods 节 MD 模拟部分。
- **SASA（Solvent Accessible Surface Area）**：衡量蛋白暴露于溶剂的表面积。用途：评估疏水核心稳定性。来源：Methods 节 MD 模拟部分。
- **Gibbs 自由能（ΔG）**：FEL 分析中，ΔG = -k_B T ln(P)，其中 P 为构象概率。用途：识别能量最低的稳定构象。来源：Methods 节 FEL 分析部分。
- **CD 光谱平均残基摩尔椭圆率 [θ]**：[θ] = [θ]_obs × MRW / (10cl)，其中 [θ]_obs 为实测椭圆率，MRW 为平均残基分子量，c 为蛋白浓度（g/mL），l 为光程（cm）。用途：定量二级结构含量。来源：Results 节 CD 光谱部分。

## 10 实验设计与证据链
- **数据集/群体**：小鼠 TTF1 Myb domain（550-732 aa，183 残基）；Sal Box DNA 序列（18-bp）
- **规模**：MD 模拟 200 ns × 3 重复；CD 光谱 3 次重复；Raman 光谱 5 次采集
- **指标**：RMSD、RMSF、RoG、SASA、ΔG、α-helix 百分比、DNA 结合迁移率
- **基线**：无实验结构作为金标准；以 Reb1 晶体结构（PDB: 5EYB）作为间接参考
- **预算**：未提供
- **骨干/仪器**：GROMACS 2020（MD）、Jasco J-1500 分光偏振仪（CD）、WITec alpha300（Raman）
- **oracle 输入**：无（计算模型无实验结构引导）
- **评测协议**：计算模型间交叉比较（表 2）；计算 vs 实验二级结构对比（图 9）；功能实验（图 8）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 多方法结构预测 | 不同方法可生成可靠模型 | AlphaFold vs SWISS-MODEL vs Robetta vs I-TASSER | Robetta 模型质量最佳（~90% 残基在最适区域）；I-TASSER 最差（72.1%） | 多方法交叉验证可筛选出高质量模型 | 无法确定哪个模型最接近真实结构 | Results 表 2、图 2 |
| MD 模拟（200 ns） | 模型在溶液中稳定 | 3 个独立重复 | RMSD 稳定在 0.5-2 nm；RoG 稳定在 2-2.5 nm（第 3 次运行略有偏差） | 模型具有动态稳定性 | 无法证明模型与体内构象一致 | Results 图 4 |
| FEL 分析 | 存在单一稳定构象 | 3 次运行的能量景观 | 第 1、2 次运行显示单一能量最低点；第 3 次运行显示多个能量最低点 | 模型主要收敛到稳定构象 | 第 3 次运行提示可能存在构象异质性 | Results 图 5 |
| CD 光谱 | Myb domain 以 α-helix 为主 | 计算预测（66.2%）vs 实验（64.3%） | 实验测得 64.3% α-helix，0% β-sheet | 计算模型与实验高度一致 | CD 无法提供残基级结构信息 | Results 图 9 |
| Raman 光谱 | 验证 CD 结果 | 酰胺 I 带拟合 | 主要贡献来自 α-helix 构象 | 独立验证 α-helix 主导 | Raman 对 β-sheet 检测灵敏度有限 | Results 图 10 |
| EMSA | Myb domain 单独可结合 Sal Box DNA | 蛋白浓度梯度 vs 固定 DNA | 蛋白浓度增加导致 DNA 迁移率逐步降低 | Myb domain 是功能性 DNA 结合单元 | 未测定结合亲和力（Kd） | Results 图 8 |

## 11 结论正确解读
- **任务范围**：本文仅针对 TTF1 的 Myb domain（550-732 aa），非全长蛋白；仅预测 apo 状态结构，未研究 DNA 结合后的构象变化。
- **oracle/真值输入**：无实验结构作为真值；模型质量评估基于统计势能（PROCHECK 等）而非与真实结构比对。
- **端到端状态**：计算-实验闭环完成，但未达到原子分辨率结构解析（X-ray/NMR/cryo-EM）。
- **算力成本**：未提供具体算力信息；MD 模拟 200 ns × 3 重复为中等规模。
- **历史数据依赖**：依赖 Reb1 晶体结构（PDB: 5EYB）作为 homology 模板；依赖 UniProt 序列注释。
- **模型依赖**：结果高度依赖所选力场（CHARMM36）和建模工具；不同工具输出存在差异（I-TASSER 明显较差）。
- **最难情形**：N 端区域在 MD 中显示较高柔性（第 3 次运行），提示该区域可能 intrinsically disordered。
- **群体/领域边界**：结论仅适用于小鼠 TTF1 Myb domain；跨物种保守性未验证。
- **不确定性**：计算模型与真实结构的偏差未知；CD/Raman 仅提供整体二级结构信息，无法验证具体残基相互作用。
- **有边界的复述**：本文证明小鼠 TTF1 的 Myb domain 可通过多方法计算建模获得稳定、以 α-helix 为主的结构模型，该模型与 CD/Raman 实验数据一致，且该 domain 单独足以结合 Sal Box DNA。但未解析原子分辨率结构，未定量结合亲和力，未研究 DNA 结合诱导的构象变化。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 全长蛋白无法纯化 | 全长 TTF1 蛋白以聚集体形式洗脱，无法获得均一蛋白 | 作者未明确提及未来方向，但暗示 domain-level 研究是替代路径 | Results 节引言段 |
| 模板序列一致性低 | 与 Reb1 模板一致性仅 27%，处于 "twilight zone" | 未明确提及 | Results 节 "Molecular modelling" 段 |
| 未解析原子分辨率结构 | 仅获得计算模型，未通过 X-ray/NMR 解析实验结构 | "we are moving ahead towards solving the atomic structure of this protein either by crystallography or NMR" | Discussion 节末段 |
| 未定量 DNA 结合亲和力 | EMSA 仅定性确认结合，未测 Kd | 未明确提及 | Results 节 EMSA 部分 |

**作者提及的相关约束**（非正式局限）：第 3 次 MD 运行显示 N 端区域柔性较高，可能影响结构稳定性；I-TASSER 模型质量较差，说明 ab initio 方法在低序列一致性场景下需谨慎使用。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 模型选择依据不充分 | 作者选择 Robetta 模型主要基于 Ramachandran 图统计，但未与其他模型进行功能位点保守性比较 | 统计质量 ≠ 生物学准确性；可能选择了一个统计上合理但功能上不准确的模型 | 将各模型与 Reb1-DNA 复合物结构进行结构比对，检查 DNA 接触残基是否保守 | Results 表 2 |
| MD 模拟未包含 DNA | 模拟仅针对 apo 蛋白，未模拟蛋白-DNA 复合物 | TF 的 DNA 结合域在结合 DNA 时可能发生 induced fit 构象变化，apo 结构可能不代表功能构象 | 进行蛋白-DNA 对接或共模拟，比较结合前后构象变化 | Methods 节 MD 模拟部分 |
| CD/Raman 验证分辨率有限 | 光谱方法仅提供整体二级结构百分比，无法验证具体残基的构象 | 计算模型中的具体残基相互作用可能错误，但整体二级结构仍与实验一致 | 进行突变分析（如关键 α-helix 残基突变后检测 DNA 结合变化） | Results 图 9、图 10 |
| EMSA 未做竞争实验 | 未验证结合特异性（如加入非特异性 DNA 竞争） | 无法排除非特异性 DNA 结合 | 加入非标记非特异性 DNA 竞争，或使用突变 Sal Box 序列 | Results 图 8 |
| 未与其他 TF 的 Myb domain 比较 | 未讨论 TTF1 Myb domain 与其他 Myb 家族蛋白（如 c-Myb）的结构差异 | Myb domain 是广泛存在的 DNA 结合模块，比较可揭示保守结合机制 | 与 c-Myb、Reb1 等 Myb domain 结构进行多重比对 | Discussion 节 |
| 第 3 次 MD 运行结果未深入分析 | 作者仅提及第 3 次运行有偏差，但未解释原因或排除异常 | 可能提示模型存在多构象状态或模拟参数问题 | 延长模拟时间或增加重复次数，分析构象聚类 | Results 图 4、图 5 |

## 14 学到什么
> Agent 提炼的知识候选

1. **多方法交叉验证策略**：在序列一致性低（<30%）时，单一建模工具不可靠。本文用 4 种工具（AlphaFold、SWISS-MODEL、Robetta、I-TASSER）生成候选模型，再通过统计势能（PROCHECK 等）筛选。**可迁移到本课题**：对 TF–DNA 复合物建模时，可同时使用 AlphaFold-Multimer、RosettaDock、HDOCK 等，交叉验证结合界面。

2. **计算-实验闭环验证范式**：计算预测的二级结构（66.2% α-helix）与 CD 实验（64.3%）高度一致，这种「预测-验证」闭环极大增强了模型可信度。**可迁移到本课题**：对 TF–DNA 结合界面进行预测后，可用突变 + EMSA/ITC 实验验证关键接触残基。

3. **domain-level 研究策略**：全长蛋白纯化失败时，聚焦功能 domain 是可行替代路径。**可迁移到本课题**：对难以纯化的 TF，可先研究其 DNA-binding domain 与 DNA 的互作，再逐步扩展至全长蛋白。

4. **MD 模拟的重复性要求**：本文 3 次独立 MD 运行结果存在差异（第 3 次 N 端柔性高），提示单次 MD 结果可能不可靠。**可迁移到本课题**：在评估 TF–DNA 复合物稳定性时，应至少 3 次重复，并报告构象聚类分析。

5. **FEL 分析用于构象筛选**：通过 ΔG 景观识别最稳定构象，是 MD 轨迹分析的有效补充。**可迁移到本课题**：在 TF–DNA 结合模拟中，可用 FEL 识别结合态与解离态的能垒。

6. **光谱方法互补**：CD 和 Raman 光谱联合使用，可交叉验证二级结构组成。**可迁移到本课题**：对 TF–DNA 复合物进行构象表征时，可结合 CD（远紫外）和 Raman（酰胺 I 带）获得互补信息。

7. **Sal Box 结合的最小 domain 确认**：EMSA 证明 Myb domain 单独即可结合 DNA，提示该 domain 是独立折叠的功能单元。**可迁移到本课题**：在 TF–DNA 互作研究中，可通过 domain 截短 + EMSA 快速定位最小 DNA 结合单元。

## 15 与已有知识连接
- **TF–DNA 结合机制**：本文与经典 TF–DNA 互作模型一致——Myb domain 通过 α-helix 插入 DNA 大沟（Discussion 节引用 [25]）。这与 c-Myb、Reb1 等 Myb 家族蛋白的已知结合模式一致（可参考 Ogata et al., 1994, Cell; 本文引用 [1]）。
- **结构预测方法**：本文使用的 AlphaFold 与 SWISS-MODEL 是当前主流工具。AlphaFold 在 CASP14 中表现优异（Jumper et al., 2021, Nature），但本文显示在低序列一致性场景下，传统 homology modelling（SWISS-MODEL）和 ab initio（Robetta）仍有价值。
- **MD 模拟**：本文使用 GROMACS + CHARMM36，这是蛋白模拟的常用组合。CHARMM36 在 α-helix 蛋白模拟中表现良好（Best et al., 2012, JCTC）。
- **光谱学**：CD 光谱的 α-helix 特征峰（208/222 nm）和 Raman 酰胺 I 带（1650-1660 cm⁻¹）是蛋白二级结构表征的标准方法（Greenfield, 2006, Nat Protoc）。
- **TTF1 功能研究**：本文与 TTF1 功能研究直接相关——TTF1 结合 Sal Box 终止 Pol I 转录（Grummt et al., 1986, Cell），并参与复制叉停滞（本文引用 [5]）。本文为这些功能提供了结构基础。
- **[Analysis] 潜在连接**：本文的 domain-level 策略与「最小 DNA 结合单元」概念，可联系到其他 TF 研究（如 p53 DNA-binding domain、NF-κB Rel homology domain）。这些 domain 均可独立折叠并结合 DNA，提示「domain autonomy」是 TF 的普遍特征。

## 16 研究想法
> Agent 生成的研究候选

1. **TF–DNA 复合物诱导拟合机制研究**
   - **名称**：TTF1 Myb domain 结合 Sal Box 的诱导拟合机制
   - **来源局限/观察**：本文仅研究 apo 状态，未涉及 DNA 结合后的构象变化
   - **核心假设**：Myb domain 结合 Sal Box 时发生显著构象重排（特别是 loop 区域）
   - **初步方法**：MD 模拟 + 增强采样（如 GaMD、REMD），模拟 apo → holo 转变；或使用 AlphaFold-Multimer 预测复合物结构
   - **验证方式**：HDX-MS 或 NMR 化学位移扰动比较 apo/holo 状态
   - **创新状态**：unverified

2. **跨物种 Myb domain 结构比较**
   - **名称**：哺乳动物 TTF1 与酵母 Reb1/Nsi1 的 DNA 结合域结构进化比较
   - **来源局限/观察**：本文仅以 Reb1 为模板，未系统比较不同物种同源物
   - **核心假设**：尽管序列一致性低，Myb domain 的 α-helix 骨架和 DNA 接触残基在进化中保守
   - **初步方法**：多序列比对 + 同源建模 + 结构叠合，分析保守残基在 DNA 结合界面的分布
   - **验证方式**：保守残基突变 + EMSA 检测结合活性变化
   - **创新状态**：unverified

3. **Myb domain 的 DNA 结合特异性决定因素**
   - **名称**：TTF1 Myb domain 对 Sal Box 序列特异性的结构基础
   - **来源局限/观察**：本文确认 Myb domain 可结合 Sal Box，但未解析特异性决定残基
   - **核心假设**：Myb domain 中特定 α-helix 的碱基接触残基决定 Sal Box 序列特异性
   - **初步方法**：蛋白-DNA 对接（如 HADDOCK、NPDock）+ 丙氨酸扫描突变 + 荧光各向异性结合实验
   - **验证方式**：突变体对 Sal Box 突变体的结合谱
   - **创新状态**：unverified

4. **无序区域对 Myb domain 功能的影响**
   - **名称**：TTF1 N 端无序区域对 Myb domain DNA 结合活性的调控
   - **来源局限/观察**：MD 显示 N 端区域柔性高，且全长蛋白纯化失败可能与无序区域有关
   - **核心假设**：N 端无序区域通过分子内相互作用或相分离调控 Myb domain 的 DNA 结合
   - **初步方法**：构建 N 端截短突变体，比较 DNA 结合活性；使用 AlphaFold 预测全长蛋白结构
   - **验证方式**：ITC 或 BLI 定量结合亲和力；CD 光谱检测构象变化
   - **创新状态**：unverified

5. **AI 辅助的 TF–DNA 结合界面预测**
   - **名称**：基于 AlphaFold-Multimer 的 TF–DNA 复合物结构预测流程优化
   - **来源局限/观察**：本文未使用 AI 方法预测蛋白-DNA 复合物，仅预测 apo 蛋白
   - **核心假设**：AlphaFold-Multimer 可预测 TF–DNA 复合物结构，但需针对 DNA 输入格式进行优化
   - **初步方法**：使用 AFM 预测 TTF1 Myb domain + Sal Box 复合物，与实验 EMSA 结果交叉验证
   - **验证方式**：与已知 TF–DNA 复合物结构（如 Reb1-DNA）比较，评估界面残基预测准确率
   - **创新状态**：partially checked（AFM 在蛋白-DNA 预测上已有初步应用，但针对 TTF1 未验证）

6. **MD 模拟力场对 TF–DNA 复合物稳定性的影响**
   - **名称**：不同力场（CHARMM36 vs AMBER ff19SB）对 Myb domain-DNA 复合物模拟的影响
   - **来源局限/观察**：本文仅用 CHARMM36 模拟 apo 蛋白，未比较力场效应
   - **核心假设**：力场选择显著影响蛋白-DNA 界面氢键和盐桥的稳定性
   - **初步方法**：分别用 CHARMM36 和 AMBER 力场模拟同一复合物，比较 RMSD、界面接触、氢键占有率
   - **验证方式**：与实验突变数据比较，评估哪种力场更准确预测结合热点残基
   - **创新状态**：unverified