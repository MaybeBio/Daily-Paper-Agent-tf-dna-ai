## 01 基本信息
- **标题**：Genome-wide identification and expression analysis of the WRKY transcription factors related to sesquiterpenes biosynthesis in Atractylodes lancea
- **作者与单位**：Liang, Hua; Liu, Weiwei; Zhao, Zhiqiang; Li, Yaqing; Zha, Liangping（单位未提供）
- **期刊/预印本平台**：Frontiers in Genetics
- **年份**：2025
- **论文类型**：基因组学 + 转录组学 + 分子对接（计算+实验验证）
- **领域**：植物功能基因组学；次生代谢调控；转录因子（WRKY）– DNA 互作
- **关键词**：WRKY transcription factor；Atractylodes lancea；sesquiterpene biosynthesis；co-expression；molecular docking；methyl jasmonate
- **DOI/arXiv 号**：10.3389/fgene.2025.1551991
- **代码**：未提供
- **数据**：基因组与转录组数据（来源未提供 accession 号）；补充材料含引物与 docking 结果
- **阅读日期**：2026-05-12
- **在该课题方向中的位置**：本文属于「植物药用成分（倍半萜）生物合成调控」中转录因子（WRKY）– 靶基因启动子（含 W-box）互作的**基因组规模鉴定 + 表达关联 + 分子对接预测**研究。对「TF–DNA 互作 × AI/物理模拟」课题的参考价值在于：提供了**非模式植物中 TF–靶启动子互作的筛选与验证流程**（共表达 + 启动子顺式元件 + 分子对接），可作为 AI 预测 TF–DNA 结合位点的生物学验证案例，但其互作证据强度有限（仅 docking，无 EMSA/ChIP）。

## 02 一句话总结
在 Atractylodes lancea 中通过 HMM 鉴定出 65 个 WRKY 转录因子基因，结合组织/地理表达谱、共表达网络、MeJA 诱导实验和 HDOCK 分子对接，提出 AlWRKY20 与 AlWRKY37 可能通过结合 AlTPS70/AlTPS71 启动子正向调控倍半萜（cis-β-farnesene、α-curcumene）生物合成。

## 03 研究问题
- **具体问题**：Atractylodes lancea 中 WRKY 转录因子家族的全基因组组成如何？哪些 AlWRKY 成员参与倍半萜生物合成调控，其可能的靶基因与结合机制是什么？
- **为什么重要**：A. lancea 的药用活性成分（倍半萜）含量存在显著地理差异，但调控其合成的转录因子机制未知。阐明 WRKY–TPS 调控模块可为代谢工程与优质种质筛选提供靶点。
- **现有方法为何不足**：此前在 A. lancea 中仅有个别 TPS 酶基因的功能研究，缺乏对上游转录调控因子的系统鉴定；在其他植物中 WRKY–萜烯合酶调控已有报道，但物种特异性强，无法直接迁移。
- **精确研究问题（Can...?）**：Can genome-wide identification combined with co-expression and molecular docking predict which AlWRKY transcription factors regulate sesquiterpene biosynthesis via binding to AlTPS gene promoters in Atractylodes lancea?

## 04 背景与发展脉络
*（标注：以下脉络为「经外部核验」的领域常识 + 本文框架的定位）*

1. **WRKY 家族鉴定阶段（2000s–2010s）**：以拟南芥（71 个）、水稻等模式植物为代表，基于 WRKYGQK 保守结构域和锌指结构进行全基因组鉴定与分组（I/II/III 组）。局限：多为序列与表达描述，缺乏功能验证。
2. **WRKY–次生代谢调控阶段（2010s–至今）**：在青蒿（AaWRKY1→ADS）、丹参（SmWRKY2→CPS）、柠檬香茅等药用植物中证实 WRKY 通过结合靶基因启动子 W-box 调控萜类合成。方法以酵母单杂交、EMSA、ChIP-qPCR 为主。
3. **组学 + 共表达 + 计算互作预测阶段（2020s–）**：利用转录组共表达网络筛选候选 TF–靶基因对，结合启动子顺式元件分析与分子对接（如 HDOCK）预测 TF–DNA 结合，再以 qPCR/代谢物测定验证。优点：通量高、适用于无遗传转化体系的非模式植物；局限：docking 预测的 TF–DNA 互作缺乏直接生化证据。
4. **本文位置**：处于第 3 阶段，首次在 A. lancea 中完成 WRKY 全基因组鉴定，并以「共表达 + MeJA 诱导 + docking」三线证据锁定 AlWRKY20/37–AlTPS70/71 调控模块。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 非模式植物中 TF 功能难以直接验证 | A. lancea 缺乏成熟的遗传转化体系，无法进行过表达/敲除实验 | 作者未明确解释，但 Discussion 中仅提出「future functional validation」需求 | Discussion 末段（"Further studies should focus on validating these regulatory networks through genetic transformation"） |
| 地理种群间倍半萜含量差异的分子机制不明 | 湖北（Yingshan）与江苏（Nanjing）种群中 hinesol/β-eudesmol 含量差异达 15–20 倍 | 作者认为可能与 WRKY–TPS 调控差异相关，但未做因果验证 | Results 3.9 节（GC–MS 数据） |
| 分子 docking 预测 TF–DNA 互作的可靠性 | HDOCK 得分仅作为结合潜力的间接指标，无法区分直接/间接结合 | 作者采用 score < −200 与 confidence > 0.7 作为阈值，但未用 EMSA/ChIP 验证 | Methods 2.10 节 |
| 共表达 ≠ 调控关系 | 共表达网络中的相关性可能来自间接效应或共同上游调控 | 作者仅以相关性（|r| > 0.8）筛选，未做因果推断 | Results 3.8 节 |
| WRKY 家族成员命名与分组存在歧义 | 部分成员（如 AlWRKY02/14/15/37）因 C 端结构域缺失或变异，分组归属不稳定 | 作者归因于可能的组装注释误差或进化过程中的结构域丢失 | Results 3.2 节、Discussion |

## 06 核心思想
1. **表面方法**：HMM 搜索 + 保守结构域验证 → 系统发育分组 → 组织/地理表达谱 → 共表达网络 → MeJA 诱导实验 → 分子对接 → qPCR 验证。
2. **核心洞察**：在无法进行遗传操作的药用植物中，**将「表达共变 + 诱导共响应 + 结构互作预测」三者叠加**，可以在不依赖转基因实验的情况下，将候选 TF 从 65 个缩小到 2 个（AlWRKY20/37），并锁定其可能靶基因（AlTPS70/71）。其隐含逻辑是：**同一调控模块的成员应在表达、诱导响应和物理结合三个层面同时关联**。
3. **可能的普适教训 [Analysis]**：对于 TF–DNA 互作研究，当缺乏 ChIP/EMSA 等直接证据时，**多维度间接证据的收敛**（共表达 + 顺式元件 + docking + 诱导动力学）可以产生高置信度的候选假设，但必须明确标注为「预测性结论」而非「验证性结论」。这一策略尤其适用于非模式生物与临床样本（无法扰动）场景。

## 07 方法总览
- **输入**：A. lancea 基因组（未提供版本/组装 accession）、转录组数据（湖北 Yingshan vs 江苏 Nanjing 的根/茎/叶）、MeJA 处理（0/6/12/24 h）样本、A. thaliana WRKY 蛋白序列（71 个，作为系统发育参考）。
- **输出**：65 个 AlWRKY 基因的注释与分组；5 个根茎富集候选基因；AlWRKY20/37 与 AlTPS70/71 的互作预测模型。
- **模块**：
  1. **家族鉴定**：HMMER 3.0 + Pfam PF03106（WRKY 结构域）→ NCBI CDD 验证 → 手动检查。
  2. **系统发育**：MAFFT v.7 比对 → IQ-TREE（ML 法，VT + R5 模型）→ iTOL 可视化。
  3. **保守 motif 与基因结构**：MEME（10 个 motif）→ 外显子-内含子结构可视化。
  4. **染色体定位与共线性**：TBtools + MCScanX（与 A. thaliana、H. annuus 比较）。
  5. **表达分析**：DESeq2（差异表达）、RSEM（FPKM）、Pearson 相关（AlWRKY–AlTPS 共表达）。
  6. **启动子顺式元件**：PlantCARE（2 kb 上游区域）。
  7. **分子 docking**：SWISS-MODEL 同源建模 → HDOCK 服务器（TF 蛋白 vs TPS 启动子 DNA 片段）。
  8. **实验验证**：qRT-PCR（5 个候选基因 × 2 地理种群）、亚细胞定位（烟草瞬时表达，GFP 融合）。
- **反馈回路**：docking 结果与共表达网络相互印证 → 选出 AlWRKY20/37 做 qPCR 与定位验证 → 结果支持表达模式，但未返回修正 docking 模型。
- **假设**：① WRKY 通过结合靶基因启动子 W-box 调控转录；② 共表达 + 诱导共响应可识别直接调控关系；③ HDOCK 得分可反映 TF–DNA 结合亲和力。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| HMM 家族鉴定 | 从基因组中识别全部 WRKY 基因 | 建立家族全集，避免遗漏 | 输入：基因组蛋白组；输出：65 个候选基因 | Results 3.1 节（表 1） | 若移除，后续所有分析失去候选集基础（预期影响） |
| 系统发育分组 | 将 AlWRKY 分为 I/II/III 组及亚组 | 参考拟南芥功能注释推断潜在功能 | 输入：65 个 AlWRKY + 71 个 AtWRKY 蛋白序列；输出：系统发育树 | Results 3.2 节（图 1） | 无法进行功能类比，候选筛选失去先验（预期影响） |
| 共表达网络 | 筛选与 TPS 基因显著相关的 WRKY | 缩小候选范围（65 → 5） | 输入：转录组 FPKM；输出：Pearson 相关矩阵 | Results 3.8 节（图 6A） | 候选基因数量无法收敛（预期影响） |
| MeJA 诱导实验 | 验证 WRKY 与 TPS 对诱导剂的共响应 | 提供动态调控证据 | 输入：MeJA 处理样本；输出：qPCR 表达曲线 | Results 3.10 节（图 7B） | 失去「诱导共响应」维度，仅剩静态共表达（预期影响） |
| 分子 docking（HDOCK） | 预测 TF 蛋白与 TPS 启动子 DNA 的结合 | 提供物理互作的结构证据（间接） | 输入：SWISS-MODEL 同源结构 + 启动子 DNA 序列；输出：docking score、confidence、氢键数 | Results 3.11 节（表 S6、图 8） | 失去结构层面的支持，但共表达与诱导证据仍可独立成立（预期影响） |
| 亚细胞定位 | 验证 AlWRKY20/37 定位于细胞核 | 支持其作为转录因子的功能前提 | 输入：GFP 融合载体；输出：荧光显微图像 | Results 3.12 节（图 9C） | 若不在核内，则转录调控假设不成立（预期影响） |

*注：本文未提供消融实验（如移除某模块后重新分析），以上「预期影响」为 [Analysis] 推断。*

## 09 关键公式符号
本文为基因组学 + 表达分析 + docking 研究，**无核心数学模型或公式**。仅涉及以下统计/计算概念（非公式化呈现）：

- **Pearson 相关系数 r**：用于共表达分析，阈值 |r| > 0.8，p < 0.05（Methods 2.7 节）。符号含义：r 为两基因表达向量的线性相关强度；用途：筛选共表达基因对；来源：Methods 2.7 节。
- **Ka/Ks 比值**：用于选择压力分析，Ka 为非同义替换率，Ks 为同义替换率，Ka/Ks < 1 表示纯化选择（Results 3.3 节）。用途：判断复制基因的进化约束。
- **HDOCK docking score**：< −200 且 confidence > 0.7 视为强结合（Methods 2.10 节）。用途：预测 TF–DNA 结合潜力。
- **qRT-PCR 相对表达量（2^−ΔΔCT）**：用于基因表达定量（Methods 2.8 节）。用途：验证 RNA-seq 差异表达。

## 10 实验设计与证据链
- **数据集/群体**：A. lancea 野生植株（3 年生），来自湖北 Yingshan 与江苏 Nanjing 两个地理种群；每器官 3 个生物学重复；MeJA 处理（200 μM，0/6/12/24 h）。
- **规模**：65 个 AlWRKY 基因；74 个 AlTPS 基因；5 个候选基因做 qPCR 验证；2 个基因做 docking 与亚细胞定位。
- **指标**：表达差异（DESeq2 Q ≤ 0.05）、共表达（|r| > 0.8）、docking score/confidence、氢键数、GC–MS 相对含量。
- **基线/对照**：MeJA 处理 0 h 作为对照；江苏种群作为湖北种群的对照；空 GFP 载体作为亚细胞定位对照。
- **骨干/仪器**：未提供测序平台与仪器信息。
- **oracle 输入**：无（本文无监督学习或结构预测的 ground truth 输入；docking 的「真值」未用实验验证）。
- **评测协议**：无独立测试集；所有结论基于同一数据集的内部一致性。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 全基因组鉴定 | A. lancea 含有 65 个 WRKY 基因 | HMM 搜索 + CDD 验证 | 65 个基因，分 3 组 | 家族规模与分组明确 | 未验证这些基因均有功能 | Results 3.1–3.2 |
| 组织/地理表达谱 | 部分 AlWRKY 在根茎中富集且湖北高于江苏 | 湖北 vs 江苏 × 根/茎/叶 | 5 个基因（含 AlWRKY20/37）根茎富集且湖北高表达 | 候选基因与倍半萜积累模式一致 | 相关性不等于因果 | Results 3.7 |
| 共表达网络 | 候选 AlWRKY 与 TPS 基因共表达 | Pearson | 16 个 AlTPS 与候选 WRKY 显著相关 | 支持 WRKY–TPS 调控模块假设 | 共表达可能来自间接效应 | Results 3.8 |
| MeJA 诱导 | AlWRKY20/37 与 AlTPS70/71 在 MeJA 下共上调 | 0 h vs 12 h | 4 基因同步上调，cis-β-farnesene 与 α-curcumene 增加 | 支持诱导共调控 | 未做启动子突变或 ChIP 验证直接结合 | Results 3.10 |
| 分子 docking | AlWRKY20/37 可结合 AlTPS70/71 启动子 | HDOCK score < −200 | AlWRKY20–AlTPS70/71 与 AlWRKY37–AlTPS70 强结合；AlWRKY37–AlTPS71 弱结合 | 提供结构互作预测 | docking 不能证明体内结合；AlWRKY37–AlTPS71 预测弱结合与共表达矛盾 | Results 3.11、表 S6 |
| 亚细胞定位 | AlWRKY20/37 定位于细胞核 | 烟草瞬时表达 + DAPI 共定位 | 两者均核定位 | 支持其作为 TF 的功能前提 | 核定位不证明调控功能 | Results 3.12 |

## 11 结论正确解读
- **任务范围**：本文仅完成「候选基因鉴定 + 关联分析 + 互作预测」，**未进行**转基因功能验证、EMSA、ChIP-qPCR、酵母单杂交或启动子截断实验。因此「AlWRKY20/37 调控倍半萜合成」是**预测性结论**，而非功能验证结论。
- **oracle/真值输入**：无。docking 的「结合」是计算预测，未以实验结合数据（如 KD、IC50）校准。
- **端到端状态**：非端到端。从基因组到代谢物含量之间存在多个未验证环节（TF 表达 → TF 蛋白 → 结合启动子 → 激活 TPS 转录 → 酶活 → 代谢物积累）。
- **算力成本**：未提供。docking 与系统发育分析的计算资源未说明。
- **历史数据依赖**：依赖 A. lancea 基因组注释质量；若基因组存在组装错误，可能影响基因计数与分组。
- **模型依赖**：docking 结果依赖同源建模模板质量（AlWRKY20 模板为 A0A2J6JT24.1，AlWRKY37 为 A0A118K6T8.1，均来自相关物种）；HDOCK 对蛋白-DNA 复合物的预测精度有限。
- **最难情形**：AlWRKY37–AlTPS71 的 docking 得分未达阈值，但共表达显示二者相关——说明计算预测与表达数据存在不一致，需实验裁决。
- **群体/领域边界**：结论仅适用于 A. lancea 的两个地理种群（湖北/江苏），不可外推至其他种群或物种。
- **不确定性**：作者未提供 docking 的置信区间、重复次数或阴性对照（如随机 DNA 序列的 docking 得分分布）。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 缺乏功能验证 | 未进行转基因或基因编辑实验 | "Further studies should focus on validating these regulatory networks through genetic transformation and detailed functional analyses" | Conclusion 节 |
| 分子机制未完全阐明 | WRKY 调控 TPS 的具体分子机制仍不清楚 | 未明确给出 | Introduction 末段（"the molecular mechanism underlying AlWRKY regulation of terpenoid synthesis unclear"） |
| 仅初步验证 | 研究为「初步验证」（preliminary validation） | 未明确给出 | Methods 节（"preliminary validation was performed"） |

*注：作者未明确讨论 docking 方法的局限、样本量限制、或缺乏 ChIP/EMSA 证据等问题。*

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| docking 仅用 HDOCK 单一方法，无实验验证 | HDOCK 对蛋白-DNA 复合物预测精度有限；score < −200 的阈值缺乏文献依据；未做随机 DNA 阴性对照 | TF–DNA 互作结论的核心证据之一可能不可靠 | 用 EMSA 或表面等离子共振（SPR）验证 AlWRKY20/37 与 AlTPS70/71 启动子片段的直接结合；或改用 RoseTTAFoldNA、AlphaFold3 交叉验证 | Methods 2.10 节 |
| 共表达网络未做因果推断 | 共表达可能来自共同上游调控因子或间接效应；未用孟德尔随机化或 GRN 推断（如 GENIE3） | 「调控模块」结论可能过度解读 | 用 GENIE3/GRNBoost2 重建调控网络，或做启动子报告基因实验 | Results 3.8 节 |
| 地理种群比较仅 2 个位点 | 湖北 vs 江苏的差异可能来自环境（气候/土壤）而非遗传；样本量小（3 重复） | 「化学型差异与 WRKY 表达相关」的结论可能混淆环境与遗传因素 | 增加种群数量；或做同园实验（common garden）控制环境 | Methods 2.1 节 |
| 未报告 docking 的 DNA 序列长度与位置 | 启动子区域选择标准未说明；不同长度的 DNA 片段影响 docking 结果 | 结果不可重复 | 补充启动子片段序列、长度、位置及选择依据 | Methods 2.10 节 |
| 亚细胞定位仅用烟草瞬时表达 | 烟草中定位可能不同于 A. lancea 原生环境；未做内源蛋白免疫定位 | 核定位结论可能不具物种特异性 | 用 A. lancea 原生质体或稳定转化体验证 | Results 3.12 节 |
| 未提供基因组版本与组装质量 | 基因计数可能受组装质量影响；65 个基因的完整性未知 | 家族鉴定结论的可重复性存疑 | 提供基因组 assembly accession、BUSCO 完整性评估 | Methods 2.2 节 |

## 14 学到什么
**Agent 提炼的知识候选**

1. **多证据收敛策略（可迁移）**：在无法进行 ChIP/EMSA 的体系中，将「共表达 + 诱导共响应 + docking」三者叠加可有效缩小候选 TF–靶基因对。迁移到 TF–DNA 互作课题：可用此策略筛选候选 TF–motif 对，再用 AI 模型（如 DeepBind、DeepSEA）或 MD 模拟做优先级排序。
2. **docking 阈值的设定经验（可迁移）**：本文以 score < −200 且 confidence > 0.7 为阈值，但未做阴性对照。迁移建议：在类似 docking 研究中，应加入随机 DNA 序列或已知不结合序列作为阴性对照，以校准阈值。
3. **共表达网络与 docking 结果不一致时的处理（可迁移）**：AlWRKY37–AlTPS71 共表达显著但 docking 弱结合——说明表达相关性与结构互作预测可能反映不同层面的调控（如间接调控、辅助因子介导）。迁移到课题：当 AI 预测与实验数据冲突时，应视为「不同假设」而非「错误」，可设计区分实验。
4. **WRKY 结构域变异的生物学意义（领域知识）**：部分 AlWRKY 因 C 端结构域缺失导致分组不稳定，提示结构域完整性可能影响 DNA 结合特异性。迁移到 TF–DNA 互作课题：在预测 TF 结合位点时，应检查 TF 是否含有完整 DNA 结合域，否则预测可能失效。
5. **MeJA 诱导作为功能筛选维度（可迁移）**：MeJA 是萜类生物合成的经典诱导子，本文利用其诱导动力学筛选候选基因。迁移到课题：在 TF–DNA 互作研究中，可利用小分子诱导子处理 + 时间序列表达数据，为 TF–靶基因关系提供动态证据。

## 15 与已有知识连接
- **WRKY 家族与萜类调控（可验证）**：本文引用的 AaWRKY1（青蒿，调控紫穗槐二烯合成）与 SmWRKY2（丹参，调控次丹参酮二烯合成）均为已发表的功能验证案例（Ma et al., 2009; Deng et al., 2019）。可进一步查阅这些文献获取 TF–启动子结合的直接证据（EMSA/Y1H）。
- **WRKY–DNA 结合机制（领域常识）**：WRKY 结构域结合 W-box（TTGACC/T）顺式元件，本文在 AlTPS 启动子中预测到 W-box 但未做突变验证。可参考拟南芥 WRKY 结构域晶体结构（PDB: 2AYD 等）进行结构比对。
- **分子 docking 方法（可迁移）**：HDOCK 为通用蛋白-核酸 docking 工具；如需更高精度，可尝试 HADDOCK（支持柔性对接）或 NPDock（专为蛋白-DNA 设计）。
- **与 AI 方法的连接（候选方向）**：本文的共表达网络 + docking 流程可视为「无监督特征筛选 + 物理打分」的组合；可对比基于深度学习的 TF–DNA 结合预测（如 DeepBind、FactorNet）在同一数据集上的表现。
- **与 MD 模拟的连接（候选方向）**：本文仅做静态 docking；可进一步对 AlWRKY20–W-box 复合物做 μs 级 MD 模拟（如 GROMACS/AMBER），评估结合稳定性与关键残基。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：WRKY–TPS 调控模块的 AI 增强型预测框架
   - **来源局限/观察**：本文仅用共表达 + docking，未利用序列特征做泛化预测；docking 阈值缺乏校准。
   - **核心假设**：将共表达特征、启动子 W-box 密度、docking 得分三者作为输入特征，训练一个轻量级分类器（如 XGBoost），可优于任一单一特征对「真实 TF–靶基因对」的预测。
   - **初步方法**：以本文 65 个 AlWRKY × 74 个 AlTPS 为候选对，以「共表达 |r| > 0.8 + MeJA 共响应 + docking 强结合」为伪标签，训练分类器；用留一法评估。
   - **验证方式**：对 top-ranked 的 3–5 对做 EMSA 验证。
   - **创新状态**：unverified

2. **候选名称**：TF–DNA docking 得分的阴性对照校准协议
   - **来源局限/观察**：本文未报告随机 DNA 序列的 docking 得分分布，导致阈值缺乏统计依据。
   - **核心假设**：对每个 TF，用随机/shuffled DNA 序列做 docking 可建立得分零分布，从而将绝对阈值转化为相对 p 值。
   - **初步方法**：对 AlWRKY20/37 分别与 100 条随机启动子序列 docking，计算得分分布；以 95 分位数作为显著结合阈值。
   - **验证方式**：与已知不结合序列（如突变 W-box）对比。
   - **创新状态**：unverified

3. **候选名称**：WRKY 结构域变异对 DNA 结合特异性的 MD 模拟研究
   - **来源局限/观察**：本文发现部分 AlWRKY 因 C 端结构域缺失导致分组不稳定，但未探讨其对结合的影响。
   - **核心假设**：C 端结构域缺失的 WRKY 变体对 W-box 的结合亲和力显著低于全长蛋白。
   - **初步方法**：对 AlWRKY20（全长）与人工截短变体做 500 ns MD 模拟（AMBER ff19SB + OL15 DNA 力场），计算结合自由能（MM-PBSA）。
   - **验证方式**：SPR 测量结合动力学。
   - **创新状态**：unverified

4. **候选名称**：基于 AlphaFold3 的 WRKY–DNA 复合物结构预测与 docking 交叉验证
   - **来源局限/观察**：本文用同源建模 + HDOCK，未利用最新结构预测工具。
   - **核心假设**：AlphaFold3 对 WRKY–W-box 复合物的预测结构与 HDOCK 结果显著一致，且能提供 HDOCK 无法给出的构象变化信息。
   - **初步方法**：对 AlWRKY20/37 与 AlTPS70/71 启动子片段做 AlphaFold3 预测，与 HDOCK 结果对比 RMSD 与界面残基。
   - **验证方式**：突变界面残基后做 EMSA。
   - **创新状态**：unverified

5. **候选名称**：多物种 WRKY–萜烯合酶调控模块的系统发育比较
   - **来源局限/观察**：本文仅研究 A. lancea 一个物种，未利用近缘物种（如向日葵、青蒿）的已有数据。
   - **核心假设**：WRKY–TPS 调控模块在菊科植物中保守，可通过跨物种共表达网络比对识别保守调控边。
   - **初步方法**：整合 A. lancea、向日葵、青蒿的转录组数据，构建跨物种共表达网络，识别保守的 WRKY–TPS 边。
   - **验证方式**：对保守边对应的启动子做 W-box 富集分析。
   - **创新状态**：unverified