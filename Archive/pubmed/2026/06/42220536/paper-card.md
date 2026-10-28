## 01 基本信息
- **标题**: Burden of novel and ultra-rare missense variants in the NF-kappaB pathway genes associated to Meniere's disease
- **作者**: Cruz-Granados, Pablo; Rivero de Jesus, Victoria; Soto-Varela, Andres; Gonzalez-Aguado, Rocio; Lopez-Escamez, Jose A
- **单位**: 未提供（通讯作者 Lopez-Escamez 隶属 University of Sydney，依据伦理声明推断）
- **期刊/平台**: Frontiers in Immunology
- **年份**: 2026-06-01
- **论文类型**: 遗传关联研究 + 计算结构预测（病例队列）
- **领域**: 免疫遗传学 / 内耳疾病（梅尼埃病）
- **关键词**: Ménière's disease; NF-κB pathway; ultra-rare variants; TLR9; TNFRSF1B; FAS; protein modelling; molecular docking
- **DOI/arXiv**: 10.3389/fimmu.2026.1789753
- **代码**: 未提供
- **数据**: ClinVar 提交号 SUB15898535（TLR9、TNFRSF1B、FAS 变异）
- **阅读日期**: 2026-06-01（按出版日期推定）
- **在该课题方向中的位置**: 本文属于「蛋白质-DNA互作 × 物理模拟」方向的间接相关研究——聚焦 NF-κB 通路（含转录因子 NF-κB 本身）上游受体（TLR9、TNFRSF1B、FAS）的罕见错义变异，通过 AlphaFold2 建模 + MODELLER 同源建模 + ClusPort 蛋白-蛋白对接 + Dynamut2 稳定性预测，评估变异对蛋白结构、二聚化及配体结合的影响。对 TF–DNA 互作课题的可迁移点在于：① 变异→结构→功能的计算流程；② 蛋白-蛋白对接方法可迁移至 TF–DNA 对接；③ NF-κB 通路本身即转录因子信号轴，变异可能间接影响 NF-κB 的 DNA 结合活性。

## 02 一句话总结
本文对 371 例西班牙梅尼埃病（MD）患者外显子组中 63 个 NF-κB 通路基因进行 burden 分析，发现 12 个基因富集超罕见错义变异，并通过蛋白建模与分子对接预测 TLR9、TNFRSF1B、FAS 的变异（如 TLR9 p.Leu673Val、FAS p.Ile122Thr）具有去稳定化效应或改变受体-配体/二聚体界面接触，提示其可能通过 NF-κB 信号失调促成 MD 的自身炎症免疫表型。

## 03 研究问题
- **具体问题**: MD 患者中 NF-κB 通路基因是否富集超罕见（ultra-rare）错义变异？这些变异是否通过影响蛋白结构、二聚化或配体结合而具有功能后果？
- **为什么重要**: MD 约 60% 患者存在免疫失调，已鉴定出自身炎症性、Th2 驱动及合并自身免疫病三种免疫表型；NF-κB 是先天/适应性免疫核心转录因子，其通路基因变异可能解释 MD 免疫表型的遗传基础，并为患者分层提供标志物。
- **现有方法不足**: 既往 MD 遗传研究多聚焦常见变异（如 TLR10、NFKB1 调控变异），对超罕见错义变异（大效应量）的系统评估缺乏；且罕见变异的功能验证成本高，需要计算预测先行筛选。
- **精确研究问题**: "Can ultra-rare missense variants in NF-κB pathway genes contribute to the immune phenotypes observed in Ménière's disease through structural and interaction-altering effects?"

## 04 背景与发展脉络
- **阶段一（临床表型分层）**: MD 免疫表型通过转录组/细胞因子谱定义（自身炎症性、Th2、合并自身免疫病），代表文献 [13-18]。
- **阶段二（常见变异关联）**: TLR10 p.Ile369Leu 保护性变异 [24]；NFKB1 调控变异加速 SNHL [25]；rs4947296 通过 TWEAK/Fn14 非经典 NF-κB 通路影响双侧 MD [26]。
- **阶段三（单细胞/空间组学）**: 2025 年 stria vascularis 单细胞 RNA-seq 定位 TWEAK/Fn14 表达细胞类型 [27]。
- **阶段四（本研究）**: 从常见变异转向超罕见错义变异 burden 分析，结合计算结构预测（AlphaFold2 + MODELLER + ClusPro + Dynamut2）评估功能后果。
- **脉络标注**: 以上脉络基于本文引用的文献框架，未经外部独立核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 罕见变异功能注释困难 | 超罕见错义变异频率极低，无法用传统关联分析达到统计功效 | 单变异效应量虽大但个体数少，需聚合到基因/通路水平 | Methods "Variant burden" 节；Results 首段 |
| 计算预测工具不一致 | SpliceAI/Pangolin 未预测到剪接改变，但 HSF Pro 预测到隐性剪接位点激活 | 深度学习方法对隐性剪接位点敏感度有限，基序方法可捕获辅助剪接元件变化 | Results "Pathogenicity assessment" 节；Discussion 末段 |
| 结构预测缺乏实验验证 | 蛋白建模和对接结果仅为计算预测，无 wet-lab 功能实验 | 作者明确承认计算预测是假设生成性质 | Discussion "limitations" 段 |
| 队列异质性 | 多人群（NFE/EAS/AMR）合并分析可能引入混杂 | 不同人群等位基因频率差异大，且样本量不均衡 | Methods "Dataset retrieval" 节；Tables 1-2 |
| 免疫表型与基因型关联弱 | 仅 4 例携带目标变异的患者有临床/转录组数据 | 罕见变异携带者数量少，无法做基因型-表型统计关联 | Results "Clinical phenotypes" 节；Discussion |

## 06 核心思想
1. **表面方法**: 对 63 个 NF-κB 通路基因做基因水平 burden 分析（Fisher 精确检验，Bonferroni 校正），筛选显著基因后，对携带超罕见错义变异的个体进行：AlphaFold2 结构检索 → MODELLER 同源建模生成突变体 → Dynamut2 预测 ΔΔG 稳定性 → ClusPro 蛋白-蛋白对接（TLR9 二聚体、FAS-FASGL、TNFRSF1B-TRAF2）→ Arpeggio 分析原子接触变化。
2. **核心洞察**: ① 超罕见错义变异在 NF-κB 通路基因中显著富集（12/63 基因），提示通路水平而非单基因水平的遗传负荷；② 结构预测显示变异效应呈"分布性"——不直接破坏配体结合位点，而是通过改变界面接触类型（极性→疏水）和减少互作残基数量来削弱或重排蛋白-蛋白互作；③ 剪接预测工具间的分歧提示：深度学习方法（SpliceAI）可能遗漏基序层面的剪接调控变异。
3. **可能的普适教训** [Analysis]: 对罕见变异的功能注释，单一预测工具不可靠，需多工具交叉验证（结构 + 剪接 + 对接）；蛋白-蛋白互作界面的"接触类型重分布"可能比简单的结合亲和力变化更常见，值得在 TF–DNA 互作研究中关注类似效应。

## 07 方法总览
- **输入**: 891 例 NFE（511 美国 + 380 西班牙）、16 例 EAS、22 例 AMR 的 WGS/WES 数据；63 个 NF-κB 通路基因列表；gnomAD v4.1 等位频率；MD 患者 bulk RNA-seq、WGBS、ATAC-seq 数据
- **输出**: 显著 burden 基因列表；候选变异的功能预测（剪接、稳定性、对接）
- **模块**:
  1. 变异 calling 与质控（来源文献 [8,11,31,32]）
  2. Gene burden analysis（Fisher 精确检验，Bonferroni 校正，OR>5, FDR<0.05）
  3. 剪接预测（SpliceAI, Pangolin, HSF Pro）
  4. 蛋白建模（AlphaFold2 模板 + MODELLER 突变体生成）
  5. 稳定性预测（Dynamut2, ΔΔG）
  6. 分子对接（ClusPro, 蛋白-蛋白）
  7. 互作接触分析（Arpeggio）
  8. 共表达网络（WGCNA + elastic-net 逻辑回归）
  9. 表观/染色质可及性分析（WGBS, ATAC-seq）
- **训练**: 无模型训练；使用预训练工具（AlphaFold2, SpliceAI 等）
- **反馈回路**: 无显式反馈回路；计算预测结果未回流至实验验证
- **假设**: ① 超罕见变异（AF<0.001）具有大效应量；② AlphaFold2 结构可作为对接模板；③ 蛋白-蛋白对接可反映体内互作变化

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Gene burden analysis | 在基因水平聚合超罕见变异信号 | 单变异统计功效不足 | 输入：变异注释+等位频率；输出：显著基因列表 | Results 首段：12/63 基因显著 | 无法筛选候选基因，后续分析无对象 |
| 剪接预测（SpliceAI/Pangolin/HSF Pro） | 评估变异对剪接的影响 | 错义变异可能破坏剪接调控元件 | 输入：变异坐标+基因注释；输出：剪接评分/基序变化 | Results "Pathogenicity" 节：HSF Pro 预测到 TLR9/TNFRSF1B 隐性剪接位点 | 遗漏潜在的剪接效应变异 |
| 蛋白建模（AlphaFold2+MODELLER） | 生成突变体三维结构 | 实验结构缺失，需计算模板 | 输入：UniProt 序列+变异位点；输出：突变体 PDB | Results "Protein models" 节：TLR9 p.Leu673Val ΔΔG=-1.15 kcal/mol | 无法评估结构效应 |
| 分子对接（ClusPro） | 预测受体-配体/二聚体互作变化 | 变异可能影响互作界面而非单体稳定性 | 输入：野生型/突变体 PDB+配体结构；输出：对接复合物+结合亲和力 | Results "Molecular docking" 节：FAS-FASGL 突变体失去 2 个疏水接触和 14 个互作残基 | 无法评估互作层面的功能后果 |
| 共表达网络（WGCNA+elastic-net） | 识别 NF-κB 通路基因的共表达模块和预测关系 | 连接基因型与免疫表型 | 输入：bulk RNA-seq 归一化计数；输出：共表达模块+预测模型 | Results "NF-κB pathway gene co-expression" 节：MD 中模块数从 6 降至 3 | 无法将变异与免疫表型关联 |

## 09 关键公式符号
本文无显式数学公式。核心统计方法为 Fisher 精确检验（用于 burden 分析），其概率质量函数为：

P = (C(a+b, a) × C(c+d, c)) / C(n, a+c)

其中 a、b、c、d 为 2×2 列联表单元格计数（病例/对照 × 变异/非变异），n 为总样本量。用途：比较病例与对照中变异等位基因频率差异。来源：Methods "Variant burden" 节（未给出具体公式，此为 Fisher 检验标准形式）。

ΔΔG（稳定性变化）由 Dynamut2 输出，单位为 kcal/mol，负值表示去稳定化。用途：预测错义变异对蛋白折叠自由能的影响。

## 10 实验设计与证据链
- **数据集**: 891 NFE（511 美国 + 380 西班牙）、16 EAS、22 AMR；对照为 gnomAD v4.1 NFE 和全球人群
- **指标**: 基因水平 burden 的 OR 和 FDR；ΔΔG；对接评分；剪接评分
- **基线**: gnomAD 等位频率作为对照；无独立验证队列
- **预算**: 未提供
- **骨干/仪器**: 计算工具（AlphaFold2, MODELLER v10.6, ClusPro, Dynamut2, SpliceAI, Pangolin, HSF Pro）
- **oracle 输入**: AlphaFold2 预测结构作为野生型模板
- **评测协议**: 无标准 benchmark；结果基于计算预测一致性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| Gene burden analysis（西班牙队列） | NF-κB 通路基因富集超罕见错义变异 | 371 例 MD vs gnomAD NFE/CSVS | 12/63 基因显著，152 个超罕见变异 | 存在通路水平遗传负荷 | 无法确定因果性 | Results 首段；Table 3 |
| 跨队列复制 | 变异在独立队列中重现 | NFE 美国、EAS、AMR 队列 | 仅 FAS 变异在 AMR 中部分重现 | 部分变异可能具有跨人群意义 | 样本量小，无法统计验证 | Results "Variant burden" 节 |
| 剪接预测 | 变异影响剪接 | SpliceAI/Pangolin vs HSF Pro | HSF Pro 预测 TLR9/TNFRSF1B 隐性剪接位点 | 可能存在剪接调控效应 | 无 RNA 实验验证 | Results "Pathogenicity" 节；Table 5 |
| 蛋白稳定性预测 | 变异去稳定化蛋白 | Dynamut2 ΔΔG | TLR9 p.Leu673Val ΔΔG=-1.15；TNFRSF1B 两变异均去稳定化；FAS p.Ile122Thr ΔΔG=-0.7 | 变异可能影响蛋白折叠 | 计算预测不等于实验验证 | Results "Protein models" 节；Tables 11-14 |
| 分子对接 | 变异改变受体-配体/二聚体互作 | 野生型 vs 突变体对接 | FAS-FASGL 突变体失去 2 疏水接触+14 互作残基；TLR9 二聚体界面接触重分布 | 变异可能削弱互作 | 无结合亲和力实验 | Results "Molecular docking" 节；Figures 3-4 |
| 共表达网络 | NF-κB 通路基因与免疫表型关联 | MD vs 对照 WGCNA | 模块数从 6 降至 3，TNFRSF1B 共表达模式改变 | 变异可能影响免疫通路 | 无功能验证 | Results "Co-expression" 节 |

## 11 结论正确解读
- **任务范围**: 本文仅覆盖 NF-κB 通路 63 个基因的编码区超罕见变异，不涉及非编码区、结构变异或拷贝数变异；分析限于计算预测，无 wet-lab 功能实验。
- **oracle/真值输入**: AlphaFold2 预测结构作为建模模板，其准确性在膜蛋白/多结构域蛋白上有限；对接评分（ClusPro）为粗粒度预测。
- **端到端状态**: 非端到端——从变异→结构→互作的完整链条中，每一步均为计算预测，无实验闭环验证。
- **算力成本**: 未提供；AlphaFold2 建模和 ClusPro 对接为计算密集型，但未报告具体资源。
- **历史数据依赖**: 依赖 gnomAD v4.1 和 CSVS 的等位频率作为对照，这些数据库的人群覆盖度和测序深度影响 burden 分析可靠性。
- **模型依赖**: 结果高度依赖 AlphaFold2 结构质量、Dynamut2 稳定性预测精度、ClusPro 对接算法和 HSF Pro 剪接预测的灵敏度。
- **最难情形**: 超罕见变异的因果性验证——单变异在个体水平无法做统计关联，需功能实验。
- **群体/领域边界**: 结果限于 MD 患者（主要为西班牙裔 NFE），不能推广至其他内耳疾病或人群；NF-κB 通路变异与 MD 免疫表型的因果关系未确立。
- **不确定性**: 作者未提供置信区间或敏感性分析；ΔΔG 预测误差未报告。
- **有边界的复述**: 在 371 例西班牙 MD 患者中，NF-κB 通路基因（特别是 TLR9、TNFRSF1B、FAS）存在超罕见错义变异富集，计算结构预测提示这些变异可能通过去稳定化蛋白或改变互作界面而影响 NF-κB 信号，但该结论限于计算层面，需实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 缺乏实验验证 | 剪接预测、蛋白稳定性、对接结果均为计算预测，无 RNA 或蛋白功能实验 | 需要 RNA  assays 或蛋白功能研究验证 | Discussion "limitations" 段 |
| 队列异质性 | 数据集包含多个种群（NFE/EAS/AMR），可能引入混杂 | 未明确提及 | Discussion "limitations" 段 |
| 统计功效有限 | 超罕见变异与表型的关联统计功效不足 | 需要更大队列 | Discussion "limitations" 段 |
| 计算工具分歧 | SpliceAI/Pangolin 与 HSF Pro 预测结果不一致 | 未明确提及 | Discussion 末段 |

**作者提及的相关约束**（非正式局限）：分析依赖外部参考人群（gnomAD、CSVS），可能因人群分层导致偏差；AlphaFold2 结构对膜蛋白（如 TLR9）的预测精度有限。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| Burden 分析仅用 Fisher 精确检验，未校正人群分层/隐式结构 | 西班牙队列内部可能存在亚结构，导致假阳性 | 超罕见变异对人群分层极敏感 | 使用 PCA 或混合模型（如 SAIGE）重分析 | Methods "Variant burden" 节未提及人群协变量 |
| 12/63 基因显著但未报告效应量分布 | 可能由少数高贡献基因驱动，而非通路整体效应 | 影响对"通路水平负荷"的解释 | 按基因拆分报告 OR 和贡献度 | Results 首段仅列基因名 |
| AlphaFold2 结构用于膜蛋白 TLR9 的胞外域建模 | AF2 对膜蛋白构象采样有限，可能错过配体诱导的构象变化 | 对接结果可能不可靠 | 使用实验结构（如 Cryo-EM）或 MD 模拟验证 | Methods "Protein modelling" 节未讨论 AF2 局限性 |
| 剪接预测工具间分歧被轻描淡写 | HSF Pro 的基序方法假阳性率高，SpliceAI 漏检可能反映真实无剪接效应 | 影响对变异功能后果的解读 | 用 minigene 剪接 assay 验证 | Results "Pathogenicity" 节；Discussion 末段 |
| 共表达网络分析样本量未报告 | WGCNA 在小样本（n<20）中模块不稳定 | 模块数从 6 降至 3 可能为噪声 | 报告样本量并做 bootstrap 稳定性检验 | Results "Co-expression" 节未给出 n |
| 未做多重检验校正的敏感性分析 | Bonferroni 校正 63 个基因后仍显著，但未报告校正后 p 值 | 影响结论稳健性 | 报告 q 值或 permutation-based FDR | Methods 仅提及 Bonferroni |

## 14 学到什么
**Agent 提炼的知识候选**（面向 TF–DNA 互作 × AI/物理模拟课题）：
1. **变异→结构→互作的计算流程可迁移**: 本文的 AlphaFold2 建模 + MODELLER 突变 + Dynamut2 稳定性 + ClusPro 对接 + Arpeggio 接触分析流程，可直接迁移至 TF 变异（如 DNA 结合域错义突变）的功能预测——将"蛋白-蛋白对接"替换为"蛋白-DNA 对接"（如 HDOCK、HADDOCK 的 DNA 模式），用 Arpeggio 分析蛋白-DNA 原子接触变化。
2. **"接触类型重分布"概念**: 本文发现变异不直接破坏结合位点，而是改变界面接触类型（极性→疏水）和互作残基数量。对 TF–DNA 互作，类似思路可用于预测错义变异如何通过改变 DNA 结合界面的氢键/疏水/盐桥网络来微调结合特异性或亲和力，而非简单的"破坏/不破坏"二分法。
3. **多工具交叉验证的必要性**: SpliceAI（深度学习）与 HSF Pro（基序）的预测分歧提示：对 TF 变异的功能注释，应同时使用基于结构的预测（如 AlphaFold2 + 对接）和基于序列的预测（如 DeepSEA、Enformer），交叉验证不一致处。
4. **通路水平 burden 分析策略**: 将变异聚合到通路（而非单基因）水平，可提高罕见变异的统计功效。对 TF–DNA 互作课题，可对"转录因子家族"或"特定信号通路（如 NF-κB、Wnt）"的全部 TF 基因做类似 burden 分析，识别疾病相关 TF 通路。
5. **跨物种保守性作为过滤标准**: 本文用人类-黑猩猩保守性评估变异重要性，可迁移至 TF 研究——优先关注在哺乳动物中高度保守的 DNA 结合域残基变异。
6. **计算预测的边界意识**: 本文明确承认计算预测是"假设生成"而非验证，这提醒 TF–DNA 互作课题中，AI/物理模拟结果必须标注为候选，需实验（EMSA、ChIP-seq、报告基因）闭环。

## 15 与已有知识连接
- **NF-κB 通路与疾病**: 本文与 NF-κB 在自身免疫病中的已知作用一致（如类风湿关节炎、SLE），可连接 Lawrence (2009) Cold Spring Harb Perspect Biol 的 NF-κB 通路综述；本文发现的 TLR9、TNFRSF1B、FAS 变异可能通过 NF-κB 影响炎症，与 MD 免疫表型 [13-18] 的转录组证据吻合。
- **罕见变异 burden 分析方法**: 本文方法与 Lee et al. (2014) Am J Hum Genet 的基因 burden 测试框架一致；可连接 Lek et al. (2016) Nature 的 gnomAD 约束指标（pLI、missense Z-score）用于 TF 基因的耐受性评估。
- **AlphaFold2 在变异功能预测中的应用**: 本文使用 AF2 结构作为建模模板，可连接 Jumper et al. (2021) Nature 的 AF2 方法学，以及 Akdel et al. (2022) Nat Struct Mol Biol 的 AF2 在变异效应预测中的基准测试。
- **蛋白-DNA 对接方法**: 本文的 ClusPro 蛋白-蛋白对接可类比至 TF–DNA 对接工具（如 HADDOCK-DNA、HDOCK），后者在 Yan & Huang (2021) Nat Protoc 中有系统描述。
- **剪接预测工具比较**: 本文 SpliceAI（Jaganathan et al. 2019 Cell）与 HSF Pro（Desmet et al. 2009 NAR）的分歧，可连接 Rowlands et al. (2021) Am J Hum Genet 的剪接预测工具基准。
- **MD 遗传学**: 本文扩展了既往 MD 遗传研究（如 Lopez-Escamez et al. 2022 Ear Hear 的罕见变异研究），将免疫通路基因纳入 MD 遗传架构。

## 16 研究想法
**Agent 生成的研究候选**：

1. **TF 错义变异的蛋白-DNA 对接功能预测流程**
   - 名称: TF-DNA-docking variant effect pipeline
   - 来源局限/观察: 本文对受体-配体对接的方法可迁移至 TF-DNA，但未覆盖 DNA 结合域变异
   - 核心假设: TF 错义变异通过改变 DNA 结合界面的接触类型（而非直接破坏）来微调结合特异性
   - 初步方法: 选取 NF-κB 家族（RELA、NFKB1 等）已知致病/良性错义变异，用 AlphaFold2 建模 + HADDOCK-DNA 对接 + Arpin 分析蛋白-DNA 原子接触变化，比较变异组 vs 野生型的接触类型分布
   - 验证方式: 用公开 ChIP-seq 数据（ENCODE）中 TF 结合峰内的变异等位基因频率，检验预测的结合亲和力变化是否与等位基因特异性结合（ASB）信号一致
   - 创新状态: unverified

2. **NF-κB 通路基因的跨人群 burden 复制研究**
   - 名称: NF-κB pathway burden replication in MD
   - 来源局限/观察: 本文仅用西班牙队列，EAS/AMR 样本量极小（16/22），无法验证跨人群普适性
   - 核心假设: NF-κB 通路基因的超罕见变异负荷在 MD 中跨人群可复制
   - 初步方法: 在 UK Biobank 或 FinnGen 中提取 MD 表型（ICD-10 H81.0），对 63 个 NF-κB 基因做相同 burden 分析，并纳入人群协变量
   - 验证方式: 比较西班牙与 UKB/FinnGen 的 burden 信号一致性；对显著基因做 Mendelian randomization（以 eQTL 为工具变量）检验因果方向
   - 创新状态: unverified

3. **多工具剪接预测不一致变异的 RNA-seq 验证**
   - 名称: Splicing prediction discordance resolution in MD variants
   - 来源局限/观察: 本文 SpliceAI/Pangolin 与 HSF Pro 对 TLR9/TNFRSF1B 变异预测不一致，作者未解决
   - 核心假设: 基序方法（HSF Pro）预测的隐性剪接位点变异在 RNA 水平可检测到异常剪接
   - 初步方法: 对携带 TLR9/TNFRSF1B 变异的患者 PBMC 样本做靶向 RNA-seq，用 rMATS 或 LeafCutter 检测剪接差异；同时用 minigene 报告系统验证
   - 验证方式: 比较 RNA-seq 剪接事件与 HSF Pro 预测位点的一致性；评估异常剪接是否导致蛋白截短或 NMD
   - 创新状态: unverified

4. **TF 变异对 NF-κB 转录活性的功能基因组学评估**
   - 名称: NF-κB TF variant transcriptional activity assay
   - 来源局限/观察: 本文预测 NF-κB 通路基因变异可能影响信号，但未直接评估转录因子活性
   - 核心假设: 携带 NF-κB 通路基因变异的 MD 患者，其 PBMC 中 NF-κB 靶基因表达谱与免疫表型相关
   - 初步方法: 用本文鉴定的变异携带者 RNA-seq 数据，做 NF-κB 靶基因集富集分析（GSEA）；结合 ATAC-seq 数据评估染色质可及性变化
   - 验证方式: 比较不同免疫表型（自身炎症 vs Th2）的 NF-κB 靶基因激活模式；用弹性网络回归评估变异负荷对靶基因表达的预测力
   - 创新状态: unverified

5. **TF-DNA 结合界面变异的深度学习预测器**
   - 名称: TF-DNA interface variant effect predictor (TFIVE)
   - 来源局限/观察: 本文依赖传统结构预测工具，未利用深度学习；且未覆盖 TF-DNA 特异性
   - 核心假设: 图神经网络（GNN）可学习 TF-DNA 共折叠结构中的变异效应，优于基于序列的预测器
   - 初步方法: 用 Protein-DNA 复合物结构数据库（PDB + AF2 预测）构建训练集，以错义变异为输入，预测 DNA 结合亲和力变化（ΔΔG_binding）；用本文的 TLR9/FAS 变异作为外部测试集
   - 验证方式: 与现有工具（如 DeepDDG、mCSM-DNA）比较 AUC；用 SELEX 或 HT-SELEX 数据验证预测的序列偏好变化
   - 创新状态: unverified