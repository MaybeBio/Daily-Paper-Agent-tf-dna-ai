## 01 基本信息

- **标题**：DNA-PK controls Apollo's access to leading-end telomeres
- **作者与单位**：Sonmez, Ceylan; Toia, Beatrice; Eickhoff, Patrik; Matei, Andreea Medeea; El Beyrouthy, Michael; Douglas, Max E; de Lange, Titia; Lottersberger, Francisca（单位未在摘要中提供）
- **期刊/预印本平台**：Nucleic Acids Research
- **年份**：2024-02-26
- **论文类型**：实验生物学研究（含结构预测）
- **领域**：DNA 损伤修复、端粒生物学、蛋白质-DNA 互作
- **关键词**：DNA-PK、Apollo/DCLRE1B、端粒、leading-end telomere、Artemis、AlphaFold-Multimer
- **DOI/arXiv 号**：10.1093/nar/gkae105
- **代码**：未提供
- **数据**：结构模型已提交至 ModelArchive（DOI 10.5452/ma-4yuqe）；原始图像见 FigShare（https://doi.org/10.6084/m9.figshare.25028588）
- **阅读日期**：未提供
- **在该方向中的位置**：本文聚焦 DNA-PK 如何通过结合 Apollo 并依赖其激酶活性及 ABCDE/Thr2609 簇磷酸化，调控 Apollo 对 leading-end 端粒 DNA 末端的切割。该文属于「蛋白质-DNA 互作 × 结构预测（AlphaFold-Multimer）」方向，为 TF-DNA 结合机制研究提供了「激酶-核酸酶-底物 DNA 末端」三元调控的类比框架。

## 02 一句话总结

本文通过遗传学、细胞生物学和 AlphaFold-Multimer 结构预测，证明 DNA-PK 通过其激酶活性及 ABCDE/Thr2609 簇的（自）磷酸化，直接结合 Apollo 并调控其进入 leading-end 端粒 DNA 末端，从而促进 3'-overhang 形成并防止 alt-EJ 介导的端粒融合。

## 03 研究问题

- **具体问题**：DNA-PK 如何调控 Apollo 在 leading-end 端粒上的核酸酶活性？其机制是否与 Artemis 在 V(D)J 重组中的调控类似？
- **为什么重要**：端粒末端加工是维持基因组稳定性的关键步骤，leading-end 端粒的 3'-overhang 形成异常会导致端粒融合和基因组不稳定。DNA-PK 作为 DSB 修复核心因子，其在端粒上的非经典功能尚不清楚。
- **现有方法不足**：此前已知 Apollo 由 TRF2 招募至端粒，但 TRF2 招募是否足以让 Apollo 发挥活性未知；DNA-PK 抑制剂导致端粒融合的机制未明；Apollo 是否直接受 DNA-PK 调控缺乏证据。
- **精确研究问题**：Can DNA-PK's kinase activity and direct binding to Apollo grant Apollo access to leading-end telomeres in a phosphorylation-dependent manner, analogous to Artemis regulation?

## 04 背景与发展脉络

（标注：以下脉络为「经外部核验」的领域共识，结合本文框架整理）

1. **DNA-PK 在 c-NHEJ 中的经典功能**：Ku70/80 结合 DNA 末端后招募 DNA-PKcs，形成突触复合物，促进 DSB 连接。DNA-PKcs 的 ABCDE/Thr2609 簇自磷酸化是末端加工和连接所必需。
2. **Artemis 的发现与调控机制**：Artemis 是 DNA-PK 调控的核酸酶，在 V(D)J 重组中打开 DNA 发夹结构。近期 cryo-EM 结构（PDB: 7SGL）显示，DNA-PK 自磷酸化后构象变化使 Artemis 进入 DNA 结合槽。
3. **Apollo 的端粒功能**：Apollo（DCLRE1B/SNM1B）是 Artemis 家族成员，由 TRF2 招募至端粒，负责 leading-end 端粒的 5' 末端切除，形成 3'-overhang。Apollo 缺失导致 leading-end 端粒融合。
4. **DNA-PK 在端粒上的矛盾角色**：DNA-PK 缺失或抑制导致端粒融合，但其在端粒上的底物和机制长期不明。
5. **本文位置**：首次将 Artemis 的调控模型推广至 Apollo，提出 DNA-PK 通过直接结合和磷酸化依赖的构象变化调控 Apollo 的端粒核酸酶活性。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| DNA-PK 抑制剂导致 leading-end 端粒融合的机制不明 | DNA-PKi 处理细胞出现端粒融合，但不知其底物 | 作者假设 DNA-PK 通过调控 Apollo 活性起作用 | Results 图 1A,B；图 2A-C |
| Apollo 被 TRF2 招募后是否足以发挥活性未知 | TRF2 招募 Apollo 但端粒加工仍异常 | 作者提出需要 DNA-PK 的额外调控 | Results 图 3A-F |
| Apollo 是否直接与 DNA-PK 互作未知 | 无直接生化证据 | 作者通过 co-IP 和结构预测验证 | Results 图 6C；Methods 结构预测节 |
| DNA-PK 激酶活性的靶标不明 | 抑制激酶活性导致端粒表型，但不知磷酸化何底物 | 作者排除 Apollo 的 S/T-Q 位点，指向 DNA-PK 自身（自磷酸化） | Results 图 4A,B；图 4C,D |
| 药物抑制剂的脱靶效应干扰解释 | DNA-PKi 导致 Apollo 蛋白降解 | 作者发现该效应不依赖 DNA-PK，用遗传突变和人类细胞系排除干扰 | Supplementary 图 S3A-G；图 2A-C |

## 06 核心思想

**1) 表面方法**：
- 遗传上位性分析（DNA-PK 抑制剂 + Apollo 缺失）
- 定点突变（Apollo 的 S/T-Q 位点、DNA-PKcs 激酶死突变）
- 免疫共沉淀（co-IP）验证蛋白互作
- AlphaFold-Multimer（AFsample）结构预测
- CO-FISH 检测端粒融合，IF-FISH 检测端粒定位

**2) 核心洞察**：
DNA-PK 对 Apollo 的调控并非通过磷酸化 Apollo 本身（其 S/T-Q 位点突变无表型），而是通过 DNA-PK 自身的 ABCDE/Thr2609 簇自磷酸化，诱导构象变化，使 Apollo 的核酸酶结构域进入 DNA 结合槽并接触 DNA 末端。Apollo 通过其 C 端区域（344-360 位氨基酸）直接结合 DNA-PK，该结合是端粒保护所必需的。

**3) 可能的普适教训 [Analysis]**：
- 激酶对核酸酶的调控可以「间接」实现：激酶自磷酸化改变自身构象，而非直接磷酸化底物酶。
- 结构预测（AlphaFold-Multimer）可作为实验假设生成工具，但需与生化实验（co-IP、突变）和功能实验（端粒融合表型）交叉验证。
- 对 TF-DNA 互作研究而言，本文提示：DNA 结合蛋白的「招募」与「激活」是两个独立调控步骤，可能由不同因子分别控制。

## 07 方法总览

- **输入**：小鼠胚胎成纤维细胞（MEFs）多种基因型（Apollo F/F、DNA-PKcs−/−、Ku70−/−、Lig4−/−、DNA-PKcsKD/KD、DNA-PKcs3A/3A）、HT1080 人细胞系、Apollo 突变体（AA、ΔPK）、DNA-PK 抑制剂（NU7441、IC7026、IC86621）
- **输出**：端粒融合频率（CO-FISH）、3'-overhang 信号（in-gel）、端粒定位（IF-FISH）、蛋白互作（co-IP）、结构模型（AFsample）
- **模块**：
  1. 遗传上位性实验（DNA-PKi + Apollo 缺失）
  2. 突变体功能分析（Apollo-AA、Apollo-ΔPK）
  3. 蛋白互作分析（co-IP）
  4. 结构预测（AFsample）
  5. 端粒表型分析（CO-FISH、in-gel、IF-FISH）
- **训练**：不适用（无监督学习/训练）
- **工具**：AFsample（AlphaFold-Multimer 改进版）、CO-FISH、IF-FISH、CHEF 凝胶电泳、共聚焦显微镜
- **反馈回路**：结构预测 → 突变设计 → 功能验证 → 模型修正
- **文字流程**：首先在 MEFs 中确认 DNA-PKi 与 Apollo 缺失的上位性关系 → 排除 DNA-PKi 脱靶降解 Apollo 的干扰（人类细胞系验证）→ 检测 Apollo 的 S/T-Q 位点突变无表型 → 验证 DNA-PKcs 激酶活性（KD/KD）和 ABCDE 簇（3A/3A）的必要性 → co-IP 证明 Apollo-DNA-PK 互作 → 鉴定 Apollo 344-360 为 DNA-PK 结合域 → AFsample 预测互作模式并与 Artemis cryo-EM 结构比对 → 提出模型。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 遗传上位性分析 | 判断 DNA-PK 与 Apollo 是否在同一通路 | 确定二者功能关系 | 输入：不同基因型 MEFs + DNA-PKi；输出：端粒融合频率 | Results 图 1A,B；图 2C | 若移除，无法建立因果关联 |
| Apollo S/T-Q 突变体（AA） | 检验 Apollo 是否为 DNA-PK 直接磷酸化底物 | 区分直接 vs 间接调控 | 输入：Apollo-AA 表达；输出：端粒表型 | Results 图 4A,B；Supplementary 图 S6 | 若移除，无法排除直接磷酸化模型 |
| DNA-PKcs 激酶死突变（KD/KD） | 验证激酶活性必要性 | 确认激酶活性而非支架功能 | 输入：DNA-PKcsKD/KD MEFs；输出：端粒融合 | Results 图 2D,E；Supplementary 图 S4 | 若移除，无法区分激酶活性与蛋白存在 |
| DNA-PKcs ABCDE 簇突变（3A/3A） | 验证自磷酸化位点必要性 | 定位关键磷酸化位点 | 输入：DNA-PKcs3A/3A MEFs；输出：端粒融合 | Results 图 4C,D | 若移除，无法将表型归因于特定磷酸化事件 |
| co-IP | 验证 Apollo-DNA-PK 直接互作 | 建立物理互作证据 | 输入：细胞裂解液；输出：互作信号 | Results 图 6C | 若移除，互作仅靠预测 |
| Apollo-ΔPK（344-360 缺失） | 鉴定 DNA-PK 结合域 | 证明互作的功能重要性 | 输入：Apollo-ΔPK 表达；输出：端粒表型 | Results 图 6G,H | 若移除，无法证明互作的功能必要性 |
| AFsample 结构预测 | 预测 Apollo-DNA-PK 互作模式 | 生成结构假设 | 输入：序列；输出：复合物模型 | Results 图 5B-D；Methods 结构预测节 | 若移除，缺乏结构层面的机制解释 |
| 与 Artemis cryo-EM 结构比对 | 检验机制相似性 | 建立类比模型 | 输入：预测模型 + PDB 7SGL/7SU3 | Results 图 5E-G | 若移除，无法支持「类似 Artemis」的结论 |

## 09 关键公式符号

不适用。本文为实验生物学研究，未使用数学公式或统计模型。统计分析采用 GraphPad 软件的非参数检验（Kruskal-Wallis ANOVA、Mann-Whitney t-test），未提供具体公式。

## 10 实验设计与证据链

**数据集/群体**：
- 小鼠胚胎成纤维细胞（MEFs）：ApolloF/F、ApolloF/F DNA-PKcs−/−、ApolloF/F Ku70−/−、ApolloF/F DNA-PKcs−/− Ku70−/−、ApolloF/F Lig4−/−、DNA-PKcsKD/KD、DNA-PKcs3A/3A
- 人纤维肉瘤细胞系 HT1080
- 293T 细胞（co-IP 实验）

**指标**：
- leading-end 端粒融合频率（CO-FISH）
- 3'-overhang 信号强度（in-gel 分析）
- γ-H2AX 端粒 foci（IF-FISH）
- Apollo-端粒共定位（IF-FISH）
- 蛋白互作强度（co-IP）

**基线/对照**：
- 未处理对照、DMSO 溶剂对照、野生型 Apollo 回补、Apollo-WT vs 突变体

**预算/仪器**：未提供

**评测协议**：至少 3 次独立实验，CO-FISH 每次 ≥10 个中期分裂相，IF-FISH 每次 >80 个细胞核

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| DNA-PKi 处理 ApolloF/F MEFs | DNA-PK 激酶活性参与端粒保护 | DNA-PKi vs DMSO；ApolloF/F vs Apollo−/− | 端粒融合频率相似 | DNA-PK 与 Apollo 在同一通路 | 不能排除平行通路 | Results 图 1A,B |
| DNA-PKi + Apollo 缺失 | 二者是否上位 | ApolloF/F + DNA-PKi vs Apollo−/− ± DNA-PKi | 无叠加效应 | 同一通路 | 不能确定上下游关系 | Results 图 1A,B |
| HT1080 中 DNA-PKi | 排除脱靶降解 Apollo | HT1080 + DNA-PKi；Apollo 蛋白水平检测 | 内源 Apollo 稳定，端粒融合增加 | 脱靶效应不解释表型 | 不能完全排除其他脱靶 | Results 图 2A-C；Supplementary 图 S3 |
| Apollo-AA（S/T-Q 突变） | Apollo 是否被 DNA-PK 直接磷酸化 | Apollo-AA vs Apollo-WT 回补 Apollo−/− | 表型无差异 | Apollo 的 S/T-Q 非关键靶点 | 不能排除其他磷酸化位点 | Results 图 4A,B；Supplementary 图 S6 |
| DNA-PKcsKD/KD | 激酶活性必要性 | KD/KD vs +/+ MEFs | 端粒融合增加 | 激酶活性必需 | 不能排除支架功能贡献 | Results 图 2D,E；Supplementary 图 S4 |
| DNA-PKcs3A/3A | ABCDE 簇必要性 | 3A/3A vs +/+ MEFs | 端粒融合增加 | ABCDE 簇磷酸化必需 | 不能排除其他簇参与 | Results 图 4C,D |
| co-IP Apollo + DNA-PKcs | 直接互作 | 293T 共转染；Apollo-WT vs ΔPK | WT 互作，ΔPK 减弱 | 344-360 介导互作 | 不能排除间接互作 | Results 图 6C |
| Apollo-ΔPK 功能 | 互作的功能必要性 | ΔPK vs WT 回补 Apollo−/− | ΔPK 无法挽救端粒融合 | 互作对端粒保护必需 | 不能排除 ΔPK 影响折叠 | Results 图 6G,H |
| AFsample 结构预测 | 互作模式 | 预测模型 vs Artemis cryo-EM | Apollo 催化域可进入 DNA-PK 开放构象 | 机制与 Artemis 类似 | 预测需实验验证 | Results 图 5B-G |

## 11 结论正确解读

- **任务范围**：本文仅研究 leading-end 端粒的 3'-overhang 形成，不涉及 lagging-end 端粒加工、端粒长度调节或端粒酶功能。
- **oracle/真值输入**：所有结论基于小鼠 MEFs 和人 HT1080 细胞系，未在体内（动物模型）验证。
- **端到端状态**：从表型（端粒融合）到分子机制（互作、磷酸化、构象变化）的链条完整，但结构预测部分未经实验验证（如交联质谱或突变体结构）。
- **算力成本**：未提供。
- **历史数据依赖**：依赖既往 Artemis 研究（cryo-EM 结构 PDB 7SGL/7SU3）作为类比基础。
- **模型依赖**：AFsample 预测的置信度仅部分区域高（N 端 1-344），C 端低置信度被排除。
- **最难情形**：DNA-PKi 的脱靶效应（Apollo 降解）是解释的主要障碍，作者通过多种抑制剂、遗传突变和人类细胞系交叉验证。
- **群体/领域边界**：结论限于哺乳动物细胞；Apollo 344-360 区域在人类中保守性未明确讨论。
- **不确定性**：DNA-PK 是否在体内直接磷酸化 Apollo 以外的底物来调控端粒加工未排除；Apollo 的核酸酶活性是否直接被 DNA-PK 构象变化激活，还是仅通过「开放 DNA 末端」间接实现，未完全区分。
- **有边界的复述**：在哺乳动物细胞中，DNA-PK 通过其激酶活性和 ABCDE/Thr2609 簇自磷酸化，结合 Apollo 的 344-360 区域，使 Apollo 进入 DNA-PK 的 DNA 结合槽并接触 leading-end 端粒 DNA 末端，从而促进 3'-overhang 形成并防止 alt-EJ 介导的端粒融合。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 无法检测内源 Apollo 蛋白 | 商业抗体无法检测小鼠内源 Apollo，部分实验依赖外源 HA-Apollo 表达 | 未明确提及 | Results 图 2A 相关讨论 |
| DNA-PKi 脱靶效应 | DNA-PKi 导致 HA-Apollo 降解，需用多种抑制剂和遗传突变排除 | 使用 HT1080 人类细胞验证 | Supplementary 图 S3；Results 图 2A-C |
| 结构预测的局限性 | AFsample 预测的 C 端区域置信度低，被排除分析 | 未明确提及 | Results 图 5B-D 相关讨论 |
| 无法完全排除其他 DNA-PK 底物 | DNA-PK 可能通过磷酸化其他蛋白（非 Apollo）调控端粒 | 未明确提及 | Discussion 节 |
| 体外 vs 体内差异 | 结构预测和 co-IP 为体外或过表达系统，体内互作未验证 | 未明确提及 | Discussion 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| DNA-PKi 导致 HA-Apollo 降解，但作者声称内源 Apollo 不受影响 | 脱靶效应可能部分解释表型；HT1080 中内源 Apollo 稳定，但 HT1080 的端粒表型可能不同于 MEFs | 若脱靶效应是主要驱动因素，则 DNA-PK-Apollo 通路模型不成立 | 使用遗传激酶死突变（KD/KD）而非抑制剂重复关键实验；在多种细胞类型中验证 | Results 图 2A-C；Supplementary 图 S3 |
| Apollo-ΔPK 缺失 344-360 可能影响蛋白折叠而非仅破坏 DNA-PK 结合 | 表型可能源于蛋白不稳定或错误折叠，而非互作丧失 | 若 ΔPK 导致蛋白不稳定，则「互作必需」结论不成立 | 检测 ΔPK 蛋白稳定性；引入点突变而非大段缺失 | Results 图 6C-H |
| AFsample 预测的互作模式与 Artemis 类似，但未与 Apollo 的 DNA 底物（端粒序列）共预测 | 端粒 DNA 序列可能影响 Apollo 的定位和活性 | 若 DNA 序列特异性重要，则「DNA-PK 开放通道」模型可能不完整 | 在预测模型中引入端粒 DNA；进行 EMSA 或体外切割实验 | Results 图 5E-G |
| 上位性实验仅用 DNA-PKi 处理，未用遗传激酶死突变与 Apollo 缺失组合 | 药物抑制与遗传缺失的表型相似性可能巧合 | 遗传证据更可靠 | 构建 DNA-PKcsKD/KD ApolloF/F 双突变 MEFs 进行 CO-FISH | Results 图 1A,B；图 2D,E |
| 作者未检测 Apollo 的核酸酶活性是否直接被 DNA-PK 激活 | 可能 DNA-PK 仅提供「通道」而非「激活」 | 区分「准入」与「激活」对机制模型至关重要 | 体外切割实验：纯化 Apollo + DNA-PK ± ATP ± 磷酸化 | Discussion 节 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **「招募」与「激活」分离的调控范式**：Apollo 由 TRF2 招募至端粒，但需 DNA-PK 的构象变化才能接触 DNA 末端。对 TF-DNA 互作研究而言，可类比为：TF 的 DNA 结合域招募至特定位点后，可能需要伴侣蛋白的构象变化才能暴露活性位点或接触 DNA 主沟。

2. **激酶自磷酸化作为构象开关**：DNA-PK 的自磷酸化（而非底物磷酸化）是调控核酸酶准入的关键。对 TF 研究，可迁移思路：某些 TF 的活性可能由共结合激酶的自磷酸化构象变化调控，而非 TF 本身的磷酸化。

3. **AlphaFold-Multimer 用于蛋白-蛋白-DNA 三元复合物预测**：AFsample 成功预测了 Apollo-DNA-PK 互作界面，并与 cryo-EM 结构类比。对 TF-DNA 研究，可用类似方法预测 TF-辅因子-DNA 三元复合物，但需注意预测置信度区域的选择（本文仅取 pLDDT > 0.8 区域）。

4. **结构类比作为机制假设来源**：将 Apollo 与 Artemis 的结构类比（RMSD 2.304 Å）直接指导了功能实验设计。对 TF 研究，可对同一家族 TF 进行结构类比，预测其与不同辅因子的互作模式。

5. **遗传上位性 + 药物抑制的组合策略**：用 DNA-PKi 和 Apollo 缺失的组合排除平行通路，同时用多种抑制剂排除脱靶效应。对 TF 研究，可用类似策略区分 TF 与其互作蛋白在同一通路中的上下游关系。

6. **排除脱靶效应的系统方法**：作者发现 DNA-PKi 导致 Apollo 降解后，用遗传激酶死突变和人类细胞系交叉验证。对 AI/药物筛选研究，提示化合物处理实验需配套遗传对照。

## 15 与已有知识连接

- **Artemis 调控机制**：本文直接类比了 cryo-EM 结构（PDB 7SGL/7SU3）中 Artemis 与 DNA-PK 的互作模式（参考文献 7），将「DNA-PK 自磷酸化开放 DNA 结合槽」的模型从 Artemis 推广至 Apollo。
- **Apollo 的端粒功能**：与既往研究一致，Apollo 由 TRF2 招募至端粒（参考文献 40-47），本文补充了 DNA-PK 作为第二层调控。
- **DNA-PK 在端粒上的非经典功能**：与既往报道 DNA-PK 抑制导致端粒融合一致（参考文献 55-64），本文提供了机制解释。
- **alt-EJ 通路**：本文确认 DNA-PKi 诱导的端粒融合依赖 alt-EJ（Lig3/PolQ），与既往 alt-EJ 研究一致（参考文献 50）。
- **可迁移领域**：对 TF-DNA 互作研究，本文的「激酶-核酸酶-底物」三元调控模型可类比「激酶-TF-染色质」的调控轴；AlphaFold-Multimer 的使用方法可迁移至 TF-辅因子复合物预测。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF-激酶互作的结构预测筛选
   - **来源局限/观察**：本文用 AFsample 成功预测 Apollo-DNA-PK 互作，但对 TF 家族尚未系统应用。
   - **核心假设**：对已知参与 DNA 损伤应答的 TF（如 p53、FOXO），其与 DNA-PK 的互作模式可通过 AlphaFold-Multimer 预测，且互作界面可能位于 DNA 结合域附近。
   - **初步方法**：对候选 TF 与 DNA-PKcs 进行 AlphaFold-Multimer 预测，筛选高置信度互作界面，用 co-IP 验证，再用 EMSA 检测 TF 的 DNA 结合是否受 DNA-PK 影响。
   - **验证方式**：突变预测界面残基，检测 TF 的 DNA 结合活性和下游转录输出。
   - **创新状态**：unverified

2. **候选名称**：DNA-PK 自磷酸化对 TF-DNA 结合的直接调控
   - **来源局限/观察**：本文证明 DNA-PK 自磷酸化调控 Apollo 的 DNA 末端准入，但未测试其他 DNA 结合蛋白。
   - **核心假设**：DNA-PK 的自磷酸化状态可改变其与多种 DNA 结合蛋白的互作，从而全局调控 DNA 损伤位点的蛋白准入。
   - **初步方法**：用 DNA-PKcs 磷酸化缺陷突变体（3A/3A）进行蛋白质组学（AP-MS），比较 WT vs 3A/3A 的互作蛋白谱。
   - **验证方式**：对候选蛋白进行 DNA 结合实验（EMSA）和端粒/DSB 功能验证。
   - **创新状态**：unverified

3. **候选名称**：TF-DNA 结合的时间动态调控模型
   - **来源局限/观察**：本文提出 DNA-PK 在 S 期/G2 期调控 Apollo 的时序性准入，但未建立定量模型。
   - **核心假设**：TF 在 DNA 上的结合时间受「招募因子」和「激活因子」双重控制，可通过延时成像和单分子追踪量化。
   - **初步方法**：用 HaloTag 标记 TF，结合 DNA-PK 抑制剂处理，进行单分子追踪，比较结合时间分布。
   - **验证方式**：结合时间变化与下游转录输出的相关性分析。
   - **创新状态**：unverified

4. **候选名称**：Apollo 344-360 基序的跨物种保守性分析
   - **来源局限/观察**：本文鉴定了 Apollo 的 DNA-PK 结合域（344-360），但未分析其进化保守性。
   - **核心假设**：该基序在哺乳动物中保守，且可能存在于其他 Artemis 家族成员中。
   - **初步方法**：对 Apollo/Artemis 家族进行多序列比对，鉴定保守基序，用 AlphaFold 预测其与 DNA-PK 的互作。
   - **验证方式**：跨物种回补实验（如人 Apollo 回补小鼠 Apollo 缺失细胞）。
   - **创新状态**：unverified

5. **候选名称**：DNA-PK 抑制剂脱靶效应的系统评估
   - **来源局限/观察**：本文发现 DNA-PKi 导致 Apollo 降解，提示抑制剂脱靶效应可能广泛存在。
   - **核心假设**：常用 DNA-PKi（NU7441、IC86621）可能通过泛素-蛋白酶体途径降解多种蛋白，影响实验解读。
   - **初步方法**：用蛋白质组学比较 DNA-PKi 处理前后的蛋白丰度变化，重点关注 DNA 修复和转录因子。
   - **验证方式**：对受影响蛋白进行功能验证，建立「抑制剂脱靶数据库」。
   - **创新状态**：unverified