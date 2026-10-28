## 01 基本信息

- **标题**: A druggable conformational switch in the c-MYC transactivation domain
- **作者**: Lama, Dilraj; Vosselman, Thibault; Sahin, Cagla; Liano-Pons, Judit; Cerrato, Carmine P; Nilsson, Kaare; Teilum, Kaare; Lane, David P; Landreh, Michael; Arsenian Henriksson, Marie
- **单位**: 未提供（根据作者信息推测为瑞典卡罗林斯卡医学院（Karolinska Institutet）等机构，但原文未明确列出）
- **期刊/平台**: Nature Communications
- **年份**: 2024
- **论文类型**: 研究论文（Research Article）
- **领域**: 蛋白质动态构象、 intrinsically disordered proteins (IDPs)、转录因子c-MYC、分子动力学模拟、药物靶向
- **关键词**: c-MYC, transactivation domain, conformational switch, intrinsically disordered protein, molecular dynamics, EGCG, drug targeting
- **DOI/arXiv 号**: 10.1038/s41467-024-45826-7
- **代码**: 未提供
- **数据**: 未提供（补充信息中可能包含，但原文未明确列出）
- **阅读日期**: 2026-05-13（按当前日期）
- **在课题方向中的位置**: 本文聚焦于转录因子c-MYC的N端反式激活域（TAD）的构象动态，通过MD模拟与机器学习识别构象开关，并利用EGCG作为模型化合物进行实验验证。该文属于「蛋白质-DNA互作（TF–DNA结合机制）× 物理模拟（MD）」方向，但重点不在DNA结合本身，而在TF的转录激活域（TAD）如何通过构象变化调控蛋白-蛋白互作（PPI），进而影响转录活性。对课题的启示在于：TF的DNA结合域（DBD）之外的区域（如TAD）的构象动态同样关键，且可通过小分子调控。

---

## 02 一句话总结

本文通过探针式MD模拟与机器学习，在c-MYC的N端反式激活域（TAD）中识别出一个构象开关（coreMYC，残基101–150），该开关在开放（活性）与闭合（非活性）构象间切换；EGCG通过非特异性疏水相互作用稳定闭合构象，从而抑制coreMYC与TRRAP和TBP的结合，但不影响c-MYC与MAX的互作。

---

## 03 研究问题

- **具体问题**: c-MYC的TAD区域（特别是残基101–150，即coreMYC）是否具有可被小分子调控的构象开关？该开关是否控制c-MYC与关键转录共激活因子（TRRAP、TBP）的互作？
- **为什么重要**: c-MYC在超过70%的人类癌症中异常激活，是重要的抗癌靶点。但其内在无序性（IDP）使其难以用传统结构生物学方法靶向。若能识别并调控其构象开关，将为靶向“不可成药”的IDP提供新策略。
- **现有方法为何不足**: 传统药物设计依赖稳定三维结构，而IDP无固定结构；现有c-MYC靶向策略多聚焦于C端bHLHZip域（与MAX二聚化及DNA结合），忽略了N端TAD的调控潜力。
- **精确的「Can ... ?」问题**: Can a small-molecule ligand (e.g., EGCG) induce a conformational switch in the intrinsically disordered c-MYC TAD (coreMYC) that blocks its interaction with essential transcriptional cofactors (TRRAP, TBP) without affecting its dimerization partner MAX?

---

## 04 背景与发展脉络

**注：以下脉络基于本文框架，部分经外部核验（标注）。**

1. **IDP靶向的早期探索（2010s）**:
   - 代表方法: 传统结构生物学（X-ray, NMR）难以解析IDP结构；早期尝试用小分子结合IDP的“预折叠”构象（如p53 TAD）。
   - 优点: 概念验证表明IDP可被小分子调控。
   - 局限: 缺乏系统性方法识别IDP中的可成药位点。
   - 本文位置: 提出“探针式MD + 机器学习”筛选IDP构象开关。

2. **c-MYC靶向策略（2010s–2020s）**:
   - 代表方法: 靶向c-MYC/MAX二聚化（如OMOMYC肽）、靶向MAX-DNA互作、抑制c-MYC转录。
   - 优点: 临床前有效，OMOMYC进入临床试验（NCT04808362）。
   - 局限: 均聚焦于C端DBD/bHLHZip域，N端TAD的调控潜力未被开发。
   - 本文位置: 首次在TAD中识别构象开关，并证明其可被小分子调控。

3. **MD模拟在IDP研究中的应用（2015–2023）**:
   - 代表方法: 全原子MD（ff19SB, OPC水模型）、增强采样（REMD, metadynamics）、共溶剂MD（co-solvent MD）识别隐式结合口袋。
   - 优点: 可捕捉IDP的构象动态；共溶剂MD可识别“隐式”药物结合位点。
   - 局限: 力场准确性、采样时间尺度有限。
   - 本文位置: 采用苯、丙烷等探针的共溶剂MD，系统扫描c-MYC全长的构象响应。

4. **机器学习在IDP构象分析中的应用（2020s）**:
   - 代表方法: AlphaFold2（AF2）预测蛋白-肽复合物结构；聚类算法分析MD轨迹。
   - 优点: AF2可预测IDP与伙伴蛋白的复合物构象；ML可加速构象分类。
   - 局限: AF2对IDP单体结构预测不可靠；ML需大量训练数据。
   - 本文位置: 使用AF2预测coreMYC与18个互作蛋白的复合物结构，验证构象开关的生物学相关性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| IDP结构不可解析 | c-MYC全长无法用X-ray/NMR解析 | 内在无序性导致构象异质性 | Introduction: "intrinsic disorder... severely limits efforts to target its function" |
| 传统药物设计失效 | 无稳定三维结构，无法进行基于结构的药物筛选 | IDP无单一结合口袋 | Introduction: "lack of a stable tertiary fold" |
| c-MYC靶向策略单一 | 现有策略聚焦C端bHLHZip域（MAX二聚化） | N端TAD的调控潜力未被探索 | Discussion: "efforts... focused on impeding dimerization of c-MYC and MAX" |
| IDP-配体互作难以表征 | NMR化学位移扰动无法与结合事件区分 | 非特异性结合导致谱图重叠 | Results: "chemical shift perturbations... could not be separated from potential titration artefacts" |
| 非特异性结合问题 | EGCG结合位点不唯一，呈动态异质性 | IDP的“模糊”结合特性 | Results: "dynamic mode of association with multiple residues involved" |

---

## 06 核心思想

1. **表面方法**: 
   - 将c-MYC全长分为9个50残基肽段，分别进行全原子MD模拟（水+苯探针），计算Rg分布。
   - 识别出残基101–150（coreMYC）在苯存在下显著压缩，提示疏水探针诱导闭合构象。
   - 用AF2预测coreMYC与18个已知互作蛋白的复合物结构，验证开放构象是结合所必需。
   - 用EGCG（多酚类化合物）作为模型配体，通过MD、native MS、IM-MS和细胞实验验证其诱导闭合构象并抑制互作。

2. **核心洞察**:
   - IDP中存在“条件性折叠”的构象开关：coreMYC在无配体时呈开放/闭合动态平衡，疏水配体（苯、EGCG）可将其锁定在闭合态。
   - 闭合态通过疏水残基的“分子内胶水”作用稳定，掩盖了MBII（残基128–143）这一关键互作位点。
   - 该开关是“可成药”的：即使配体结合是非特异性的，只要它能稳定非活性构象，就能抑制功能。

3. **可能的普适教训** [Analysis]:
   - IDP的“构象开关”可能广泛存在于其他转录因子的TAD中，尤其是富含疏水残基的区域。
   - 共溶剂MD（如苯探针）可作为IDP“可成药性”的快速筛选工具，无需高分辨率结构。
   - 非特异性配体（如EGCG）虽非理想药物，但可作为概念验证，证明“构象锁定”策略的可行性。

---

## 07 方法总览

- **输入**: 
  - c-MYC全长氨基酸序列（UniProt ID未提供）
  - 18个已知c-MYC互作蛋白的序列（Supplementary Table 1）
  - EGCG分子结构
- **输出**: 
  - 9个肽段的Rg分布（MD模拟）
  - coreMYC的开放/闭合构象模型
  - coreMYC与18个互作蛋白的AF2复合物模型
  - coreMYC-EGCG复合物的结合模式与构象变化
  - 细胞水平EGCG抑制c-MYC-TBP/TRRAP互作的证据
- **模块**:
  1. MD模拟（AMBER 18, ff19SB, OPC水模型）
  2. 共溶剂MD（苯、丙烷、甲醇、乙醛探针）
  3. AF2复合物预测（Colabfold, AlphaFold-multimer-v2）
  4. Native MS / IM-MS（Waters Synapt G1）
  5. 细胞实验（isPLA, Western blot, RT-qPCR）
- **训练**: 无监督MD采样；AF2为预训练模型，未微调
- **工具**: AMBER 18, Colabfold, MassLynx, Pulsar, IMPACT
- **反馈回路**: MD模拟 → 识别构象开关 → AF2验证互作 → EGCG实验验证 → 细胞功能验证
- **假设**: 
  - 苯探针可模拟疏水配体结合行为
  - AF2可准确预测IDP-蛋白复合物结构
  - EGCG的细胞效应主要通过直接结合coreMYC介导
- **文字流程**: 
  1. 将c-MYC分为9个肽段，分别进行MD模拟（水 vs 水+苯），比较Rg分布。
  2. 识别coreMYC（101–150）为唯一显著响应苯的肽段。
  3. 用AF2预测coreMYC与18个互作蛋白的复合物，确认开放构象是结合所需。
  4. 用EGCG进行MD模拟，验证其诱导闭合构象。
  5. 用native MS和IM-MS验证EGCG结合与构象变化。
  6. 在SH-SY5Y细胞中用isPLA验证EGCG抑制c-MYC-TBP/TRRAP互作，Western blot确认蛋白水平不变。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 肽段MD模拟 | 系统扫描c-MYC全长构象动态 | 全长IDP无法直接模拟 | 输入：9个50残基肽段；输出：Rg分布 | Results 图1b | 无法定位构象开关区域 |
| 共溶剂MD（苯探针） | 识别疏水配体响应区域 | 模拟药物结合对构象的影响 | 输入：肽段+0.4M苯；输出：Rg分布变化 | Results 图1b, d | 无法预测可成药位点 |
| AF2复合物预测 | 验证开放构象的生物学相关性 | 确认开放态是互作所需 | 输入：coreMYC+18个互作蛋白序列；输出：复合物结构 | Results 图3a, b | 无法建立构象-功能关联 |
| EGCG-MD模拟 | 验证EGCG诱导闭合构象 | 提供分子机制解释 | 输入：coreMYC+1或2个EGCG；输出：Rg-E分布 | Results 图2d, e | 无法解释EGCG的抑制机制 |
| Native MS / IM-MS | 实验验证EGCG结合与构象变化 | 提供实验证据支持MD预测 | 输入：coreMYC±EGCG；输出：质谱图、CCS值 | Results 图2b, c | 无法确认EGCG的生理相关性 |
| isPLA细胞实验 | 验证EGCG在细胞内抑制互作 | 证明构象调控的生物学效应 | 输入：SH-SY5Y细胞±EGCG；输出：PLA信号定量 | Results 图4a–d | 无法证明EGCG直接作用于coreMYC |
| Western blot / RT-qPCR | 排除蛋白表达变化的影响 | 确认抑制效应非因蛋白水平下降 | 输入：细胞裂解物；输出：蛋白/mRNA水平 | Results 图4e, Supplementary 图21 | 无法排除间接效应 |

---

## 09 关键公式符号

1. **结合自由能（MM/GBSA）**:
   ΔG_Binding = [G]_complex − [G]_peptide-A − [G]_peptide-B
   G = E_bon + E_vdw + E_ele + E_pol + E_npol
   - E_bon: 键、角、二面角能量之和
   - E_vdw: 范德华相互作用能
   - E_ele: 静电相互作用能
   - E_pol: 极性溶剂化能（广义Born模型）
   - E_npol: 非极性溶剂化能（γ × SASA）
   - 用途: 计算coreMYC与TRRAP/TBP的结合亲和力及残基能量分解
   - 来源: Methods "Computation of enthalpic and binding energies"

2. **碰撞截面（CCS）**:
   - 实验值: TWCCS_N2（氮气中行波离子迁移率）
   - 理论值: 由MD结构经IMPACT计算
   - 用途: 验证MD预测的构象变化与实验一致
   - 来源: Results "the experimental TWCCS_N2 values of 820, 825, and 897 Å² are in reasonable agreement with the theoretical CCSs of 820, 881, and 923 Å²"

---

## 10 实验设计与证据链

**数据集/群体**:
- 9个c-MYC肽段（50残基，覆盖全长439残基）
- 18个c-MYC互作蛋白（Supplementary Table 1）
- SH-SY5Y人神经母细胞瘤细胞系

**指标**:
- Rg分布（MD模拟）
- 结合化学计量（native MS）
- CCS值（IM-MS）
- PLA信号/细胞核（isPLA）
- 蛋白/mRNA水平（Western blot, RT-qPCR）

**基线/对照**:
- 水 vs 水+苯（MD模拟）
- 无EGCG vs 有EGCG（native MS, isPLA）
- c-MYC-MAX互作作为阳性对照（不受EGCG影响）

**预算/资源**:
- MD模拟: 每肽段5 µs（水+苯），总计约45 µs；另有ff14SB和ff14IDPSFF力场验证（各1 µs/肽段）
- AF2: Colabfold, 3个recycles, 无模板
- 细胞实验: 3次独立生物学重复

**评测协议**:
- MD: 比较水 vs 水+苯的Rg分布差异
- AF2: ipTM评分（0.3–0.9），与实验结构对比验证
- Native MS: 滴定EGCG，监测结合峰
- IM-MS: 比较apo vs EGCG结合态的CCS
- isPLA: 定量核内PLA信号，统计比较

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 肽段MD筛选 | coreMYC是唯一响应苯的肽段 | 9个肽段，水 vs 水+苯 | 仅101–150显著压缩 | coreMYC是构象开关区域 | 苯探针不能代表所有药物 | Results 图1b |
| EGCG-MD模拟 | EGCG诱导coreMYC闭合 | 无EGCG vs 1/2个EGCG | Rg显著降低 | EGCG稳定闭合构象 | 模拟条件与细胞环境不同 | Results 图2d |
| Native MS | EGCG结合coreMYC | 0–200 µM EGCG | 1:1和1:2结合峰 | EGCG直接结合coreMYC | 结合亲和力未定量 | Results 图2b |
| IM-MS | EGCG改变coreMYC构象 | apo vs EGCG结合态 | CCS从897降至820–825 Å² | EGCG诱导更紧凑构象 | 仅检测到部分构象变化 | Results 图2c |
| AF2复合物预测 | 开放构象是互作所需 | 18个互作蛋白 | coreMYC在复合物中呈开放态 | 闭合态抑制互作 | AF2预测可能不准确 | Results 图3a, b |
| isPLA（TBP） | EGCG抑制c-MYC-TBP互作 | 0 vs 25 µM EGCG | 核内PLA信号显著降低 | EGCG在细胞内抑制互作 | 未检测其他细胞类型 | Results 图4a, b |
| isPLA（TRRAP） | EGCG抑制c-MYC-TRRAP互作 | 0 vs 25 µM EGCG | 核内PLA信号显著降低 | EGCG在细胞内抑制互作 | 未检测其他细胞类型 | Results 图4c |
| isPLA（MAX） | EGCG不影响c-MYC-MAX互作 | 0 vs 25 µM EGCG | 信号无显著变化 | EGCG特异性作用于TAD | 未检测MAX结合位点 | Results 图4d |
| Western blot | EGCG不改变蛋白表达 | 0–50 µM EGCG | 蛋白水平不变 | 抑制效应非因表达下降 | 未检测蛋白降解 | Results 图4e |

---

## 11 结论正确解读

- **任务范围**: 本文仅研究了c-MYC的N端TAD（残基101–150），未涉及C端bHLHZip域或DNA结合功能。结论不能推广到c-MYC全长蛋白的DNA结合活性。
- **oracle/真值输入**: AF2预测的复合物结构未经实验验证（如X-ray/NMR），仅通过ipTM评分和与已知互作位点的比对间接验证。
- **端到端状态**: 从MD模拟到细胞实验的完整链条已建立，但缺乏动物模型或临床数据。EGCG的体内效应未验证。
- **算力成本**: MD模拟总计约45 µs（主模拟）+ 额外力场验证，计算成本较高，但未提供具体GPU/CPU资源信息。
- **历史数据依赖**: 依赖已知的c-MYC互作蛋白列表（Supplementary Table 1），可能遗漏未发现的互作伙伴。
- **模型依赖**: 结果依赖于ff19SB力场和OPC水模型的准确性；AF2预测依赖训练数据。
- **最难情形**: EGCG的非特异性结合意味着其选择性差，可能影响其他IDP。细胞实验中EGCG浓度（25 µM）远高于其与coreMYC的结合亲和力（未定量），可能存在脱靶效应。
- **群体/领域边界**: 结论仅适用于c-MYC的TAD区域，不能推广到其他IDP。EGCG作为多酚类化合物，其药代动力学特性未研究。
- **不确定性**: NMR实验因化学位移扰动无法与滴定伪影区分而被排除，说明实验验证构象变化存在技术挑战。MD模拟的构象采样可能未覆盖全部能量景观。
- **有边界的复述**: 本文证明，在体外和细胞水平，EGCG可通过非特异性疏水互作诱导c-MYC TAD（残基101–150）的闭合构象，从而抑制其与TRRAP和TBP的结合，但不影响c-MYC-MAX互作。该构象开关的生物学相关性依赖于AF2预测和细胞实验的间接证据，其体内可成药性尚未验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| EGCG结合的非特异性 | 多个结合位点，动态异质性 | 设计更特异性的配体，添加功能基团与关键残基互作 | Discussion: "adding functional groups to the EGCG scaffold that specifically interact with key residues" |
| NMR验证失败 | 化学位移扰动无法与滴定伪影区分 | 未明确提及 | Results: "could not be separated with sufficient confidence from potential titration artefacts" |
| 缺乏高分辨率结构 | 未获得coreMYC-EGCG复合物的原子级结构 | 未明确提及 | 全文未提供复合物晶体/NMR结构 |
| 细胞模型单一 | 仅使用SH-SY5Y一种细胞系 | 未明确提及 | Methods: 仅SH-SY5Y |
| 体内效应未验证 | 无动物模型或临床数据 | 未明确提及 | 全文未涉及动物实验 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| 苯探针作为疏水配体模型的代表性有限 | 苯是简单芳香烃，不能代表复杂药物分子的结合行为 | 若苯的效应是特异的，则EGCG的效应可能也是特异的；若苯的效应是普遍的疏水效应，则EGCG的效应可能缺乏选择性 | 使用多种不同化学性质的探针（如环己烷、苯酚）重复MD筛选 | Results 图1b, d |
| AF2预测IDP复合物的可靠性未充分验证 | AF2对IDP的预测准确性有限，尤其对“模糊复合物” | 若AF2预测的开放构象不准确，则“闭合态抑制互作”的结论可能不成立 | 用实验方法（如交联质谱、SAXS）验证AF2预测的复合物结构 | Results 图3a, b |
| EGCG的细胞效应可能通过其他机制介导 | EGCG是多靶点化合物，可能通过氧化应激、信号通路等间接影响c-MYC互作 | 若EGCG的效应非直接结合coreMYC，则“构象开关”机制在细胞中可能不成立 | 使用无EGCG结合能力的coreMYC突变体进行isPLA实验 | Results 图4a–d |
| native MS中EGCG结合的非特异性可能被过度解读 | 非特异性结合在气相中可能被放大，不代表溶液中的真实结合 | 若EGCG在溶液中结合较弱，则其生理相关性存疑 | 使用ITC或SPR定量溶液中的结合亲和力 | Results 图2b |
| 未检测EGCG对c-MYC转录活性的直接影响 | isPLA检测的是蛋白-蛋白互作，而非转录输出 | 若EGCG抑制互作但不影响转录，则其治疗意义有限 | 检测EGCG处理后的c-MYC靶基因表达 | Results 图4 |
| 缺乏对coreMYC构象开关的动态时间尺度分析 | MD模拟虽长（5 µs），但IDP的构象转换可能发生在更长时间尺度 | 若开关的转换时间远长于模拟时间，则模拟可能未捕捉完整构象景观 | 使用增强采样方法（REMD, metadynamics）验证 | Methods "Molecular dynamics simulations" |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **共溶剂MD筛选IDP构象开关的方法**:
   - 可迁移性: 对任何TF的TAD区域，可用苯/丙烷等疏水探针进行共溶剂MD，快速识别对疏水环境敏感的“构象开关”区域。
   - 迁移方法: 将c-MYC的9肽段策略应用于其他TF（如p53, NF-κB），系统扫描全长序列的构象响应。

2. **“闭合态抑制互作”的调控逻辑**:
   - 可迁移性: 对TF-DNA互作，若TF的DBD附近存在类似coreMYC的疏水开关，可通过小分子锁定非活性构象，间接抑制DNA结合。
   - 迁移方法: 对TF的DBD进行共溶剂MD，识别可诱导闭合构象的位点，再筛选小分子。

3. **AF2用于IDP-蛋白复合物预测的验证流程**:
   - 可迁移性: AF2可预测IDP与伙伴蛋白的复合物结构，但需用ipTM评分和已知互作位点进行验证。
   - 迁移方法: 对TF-DNA复合物，可用AF2预测TF的DBD与DNA的复合物结构，但需注意IDP区域的预测不确定性。

4. **Native MS/IM-MS用于IDP构象验证**:
   - 可迁移性: IM-MS可提供溶液中蛋白构象的碰撞截面，与MD预测的Rg/CCS直接对比。
   - 迁移方法: 对TF-DNA复合物，可用IM-MS检测TF在DNA结合前后的构象变化，验证MD预测。

5. **“非特异性结合”作为概念验证的合理性**:
   - 可迁移性: 即使配体结合是非特异的，只要能稳定非活性构象，就足以抑制功能。这为IDP靶向提供了“构象锁定”而非“位点占据”的新思路。
   - 迁移方法: 对TF-DNA互作，可筛选非特异性疏水配体，验证其是否能通过构象变化抑制DNA结合。

---

## 15 与已有知识连接

1. **p53 TAD的类似研究**:
   - 已知p53的TAD与MDM2互作，且EGCG等多酚类化合物可调控p53活性（外部核验：Moll et al., 2015）。
   - 本文引用了p53 TAD与EGCG的研究（Discussion: "shown to interact with the disordered amino-terminal TAD of the tumor suppressor p53"），提示TF的TAD是IDP靶向的共性靶点。

2. **c-MYC结构研究**:
   - 已知c-MYC的C端bHLHZip域与MAX形成异二聚体并结合DNA（外部核验：Nair & Burley, 2003）。
   - 本文聚焦N端TAD，与C端DBD研究互补，提示TF的多个功能域均可作为药物靶点。

3. **IDP药物发现方法**:
   - 共溶剂MD已被用于识别折叠蛋白的隐式口袋（外部核验：Seco et al., 2008），本文将其扩展至IDP。
   - 提示: 该方法可进一步与机器学习结合，用于预测IDP的“可成药构象”。

4. **EGCG的多靶点特性**:
   - EGCG已知可结合多种蛋白（外部核验：Yang et al., 2009），本文证明其可调控c-MYC TAD构象，提示多酚类化合物在IDP靶向中的潜力。

5. **TF-DNA互作调控的新视角**:
   - 传统TF-DNA互作研究聚焦于DBD与DNA的识别，本文提示TF的TAD构象变化可间接调控转录活性，为TF-DNA互作研究提供了“远程调控”的新维度。

---

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**: 基于共溶剂MD的TF-TAD构象开关全基因组筛选
   - **来源局限/观察**: 本文仅研究了c-MYC一个TF，但共溶剂MD方法可推广至其他TF。
   - **核心假设**: 多种TF的TAD区域存在类似的疏水构象开关，可被小分子锁定。
   - **初步方法**: 选取10–20个与癌症相关的TF（如p53, NF-κB, STAT3），将其TAD分为50残基肽段，进行共溶剂MD筛选，识别构象开关区域。
   - **验证方式**: 对候选TF的TAD进行native MS/IM-MS验证，检测小分子诱导的构象变化。
   - **创新状态**: unverified

2. **候选名称**: 基于AF2的TF-TAD互作组预测与构象开关功能验证
   - **来源局限/观察**: 本文用AF2预测了coreMYC与18个互作蛋白的复合物，但未系统验证。
   - **核心假设**: AF2可准确预测TF-TAD与共激活因子的复合物结构，从而预测构象开关的功能影响。
   - **初步方法**: 对c-MYC及其他TF的TAD，用AF2预测与所有已知互作蛋白的复合物结构，比较开放/闭合构象的结合亲和力差异。
   - **验证方式**: 用突变体（锁定开放或闭合构象）进行pull-down或ITC实验验证。
   - **创新状态**: unverified

3. **候选名称**: EGCG衍生物的设计与构象锁定活性优化
   - **来源局限/观察**: EGCG结合是非特异的，亲和力未定量，且细胞实验浓度较高。
   - **核心假设**: 基于coreMYC-EGCG复合物结构，可设计更高亲和力、更特异性的衍生物。
   - **初步方法**: 从MD模拟中提取coreMYC-EGCG的结合模式，进行药效团建模和虚拟筛选，设计衍生物。
   - **验证方式**: 用native MS定量结合亲和力，用isPLA验证细胞活性。
   - **创新状态**: unverified

4. **候选名称**: TF-TAD构象开关与DNA结合活性的远程调控机制研究
   - **来源局限/观察**: 本文未检测EGCG对c-MYC-DNA结合的影响，但TAD构象变化可能通过变构效应影响DBD。
   - **核心假设**: TAD的构象开关通过长程变构效应调控DBD的DNA结合活性。
   - **初步方法**: 用MD模拟全长c-MYC（或与DNA复合物），比较开放/闭合TAD构象下DBD的构象变化。
   - **验证方式**: 用EMSA或ChIP-seq检测EGCG处理后的c-MYC-DNA结合变化。
   - **创新状态**: unverified

5. **候选名称**: 基于机器学习预测IDP构象开关的通用算法
   - **来源局限/观察**: 本文的构象开关识别依赖MD模拟，计算成本高，难以扩展到全蛋白质组。
   - **核心假设**: 氨基酸序列特征（疏水性、电荷分布、预测的二级结构）可预测IDP中的构象开关区域。
   - **初步方法**: 以本文的MD数据为训练集，提取序列特征，训练分类器预测构象开关。
   - **验证方式**: 在独立TF数据集上验证预测准确性，并用MD模拟验证。
   - **创新状态**: unverified