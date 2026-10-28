## 01 基本信息

- **标题**：Assessing the validity of leucine zipper constructs predicted by AlphaFold
- **作者**：Mitic, Isobel; Rowell, Keiran; Litfin, Thomas; Michie, Katharine A; Jacques, David A
- **单位**：未提供（据致谢推测为 UNSW Sydney，但原文未明确列出单位列表）
- **期刊/平台**：Protein Science（Wiley）
- **年份**：2025
- **论文类型**：实证评估研究（方法学验证）
- **领域**：结构生物学 × AI 蛋白质结构预测
- **关键词**：AlphaFold、亮氨酸拉链、AP-1 转录因子、蛋白质-蛋白质互作、静电作用
- **DOI/arXiv**：10.1002/pro.70438
- **代码**：未提供
- **数据**：补充材料（L-zip dimer pairs AlphaFold confidence metrics.xlsx；L-zip dimer pairs Newman Ranks and structures.xlsx）
- **阅读日期**：2026-04-27
- **在课题方向中的位置**：本文直接针对 TF–DNA 互作中的关键结构域——AP-1 转录因子的亮氨酸拉链（L-zip）二聚化结构域——评估 AlphaFold2/3 类 AI 方法预测二聚体界面有效性的边界。核心发现是 AlphaFold 对 L-zip 二聚体结构预测的置信度指标（pLDDT、PAE、ipTM）无法区分真实可形成的二聚体与静电上不可能形成的二聚体，这对依赖 AI 结构预测来推断 TF 二聚化网络及后续 DNA 结合特异性的研究提出了重要警示。

---

## 02 一句话总结

本文以 AP-1 转录因子 FosB/JunD 及 49 个人类 L-zip 蛋白的 1928 个二聚体组合为测试集，发现 AlphaFold2/3（含 Boltz-1）对亮氨酸拉链二聚体结构预测的置信度指标（pLDDT、PAE、ipTM）无法区分实验验证的真实二聚体与静电上不可能形成的二聚体，表明当前 AI 结构预测方法在评估 TF 二聚化可行性方面存在系统性局限。

---

## 03 研究问题

**具体问题**：AlphaFold 系列方法能否可靠地区分生物学上可能形成与不可能形成的亮氨酸拉链二聚体界面？

**为什么重要**：AP-1 转录因子通过不同家族成员间的异源/同源二聚化实现组合调控，二聚化特异性决定了 DNA 结合位点选择和下游基因表达。若能用 AI 结构预测快速评估任意 TF 二聚化的可能性，将极大加速对癌症等疾病中转录重编程的理解。但若 AI 预测给出高置信度的假阳性二聚体，将误导后续实验设计和生物学结论。

**现有方法不足**：AlphaFold2/3 的置信度指标（pLDDT、ipTM、PAE）被广泛用于判断预测结构的可靠性，但这些指标主要反映结构确定性而非热力学可行性。对于 L-zip 这类由疏水核心和界面静电共同决定二聚化特异性的结构域，AI 方法可能仅学习到序列模式（如亮氨酸重复）而忽略静电排斥等物理约束。

**精确研究问题**：Can AlphaFold2/AlphaFold3 (Boltz-1) confidence metrics (pLDDT, ipTM, PAE) reliably discriminate between experimentally validated leucine zipper dimer pairs and those that are electrostatically forbidden?

---

## 04 背景与发展脉络

*注：此脉络基于本文引用和讨论，经外部核验标记如下。*

1. **经典实验时代（~1990s-2000s）**：亮氨酸拉链二聚化特异性通过生化实验（酵母双杂交、pull-down）和结构生物学（X-ray、NMR）系统研究。代表性工作包括 Vinson 等（2002, 2006）对 g/e 位点残基耦合能的系统计算，以及 Newman & Keating（2003）对 49 个人类 L-zip 蛋白的全组合二聚化阵列筛选。这些工作建立了 L-zip 二聚化"密码"的经验规则。**[经外部核验：Vinson 2002/2006 和 Newman & Keating 2003 均为该领域经典文献]**

2. **计算预测早期（~2000s-2010s）**：基于统计势能和物理能量函数的二聚化预测方法（如 Rosetta 对接、FoldX）被用于评估 L-zip 界面稳定性，但计算成本高且精度有限。**[仅本文框架]**

3. **AI 结构预测时代（2021-至今）**：AlphaFold2（2021）在 CASP14 中取得突破，随后 AlphaFold-Multimer（2022）扩展至复合物预测，AlphaFold3（2024）进一步支持核酸和修饰。这些方法被迅速应用于预测 TF 二聚化网络。本文指出，尽管这些方法在整体折叠预测上表现优异，但其对 L-zip 二聚体界面可行性的判别能力尚未被系统验证。**[经外部核验：AlphaFold2/3 时间线准确]**

4. **本文位置**：首次以大规模实验数据（1928 个二聚体组合）系统评估 AlphaFold2/3 对 L-zip 二聚化可行性的判别能力，填补了 AI 结构预测在 TF 二聚化网络应用中的验证空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 高置信度假阳性 | AlphaFold 对 FosB 同源二聚体（已知不能形成）给出与真实二聚体（FosB/JunD）几乎相同的置信度指标 | AlphaFold 的置信度指标反映结构确定性而非热力学可行性；网络主要学习序列共进化模式 | Results 图 2-3：FosB 同源二聚体 pLDDT≥90、PAE 低、ipTM 0.7-0.8，与 FosB/JunD 异源二聚体无显著差异 |
| 置信度指标无判别力 | ipTM 对真实/虚假二聚体的 AUC-ROC 仅 0.566（AlphaFold2） | ipTM 设计目标是评估界面预测可靠性，而非结合可行性 | Results 图 7a：真实与虚假二聚体 ipTM 分布几乎完全重叠 |
| 静电相互作用被忽略 | 人为设计的全 Glu 或全 Lys 的 e/g 位点（强静电排斥）仍被预测为高置信度 L-zip 二聚体 | AlphaFold 的图神经网络表示中缺乏显式静电项；静电效应仅通过序列共进化间接体现 | Results 图 5：合成肽（全 Glu 或全 Lys）仍形成高置信度平行 L-zip 结构 |
| 序列模式主导预测 | L-zip 预测主要由亮氨酸重复模式（d 位点）驱动，而非界面残基的理化性质 | 训练数据中 L-zip 的序列特征（亮氨酸七联重复）过于显著，网络倾向于"看到"亮氨酸就预测卷曲螺旋 | Results 表 2：将 d 位点 Leu 突变为 Ile 会逐步"破坏"预测的 L-zip，而改变 e/g 位点电荷影响较小 |
| 无结合强度输出 | AlphaFold 不提供 KD 或结合自由能估计，无法区分强/弱/无结合 | 架构设计目标是结构预测而非亲和力预测 | Discussion：作者指出需额外工具评估结合强度 |

---

## 06 核心思想

### 1) 表面方法
使用 AlphaFold2-Multimer 和 Boltz-1（AlphaFold3 重实现）预测 AP-1 转录因子（FosB/JunD）及 49 个人类 L-zip 蛋白的全部二聚体组合结构，提取置信度指标（pLDDT、PAE、ipTM），与 Newman & Keating (2003) 的实验二聚化数据对比，评估 AI 预测的判别能力。同时通过合成肽设计（全 Glu/全 Lys e/g 位点）和 Leu→Ile 突变实验，探究 AlphaFold 预测 L-zip 的驱动因素。

### 2) 核心洞察
**AlphaFold 的置信度指标衡量的是"结构确定性"而非"物理可行性"**。对于 L-zip 这类二聚化特异性由界面静电决定的系统，AlphaFold 能够准确识别 L-zip 的几何模式（亮氨酸七联重复），但无法判断该界面在静电上是否可能形成。这意味着高 pLDDT/ipTM 的预测结构可能是热力学上不可能的构象。作者进一步指出，Boltz-1 结合 ipSAE 指标（仅考虑低 PAE 残基对）有所改善（AUC-ROC 0.848），但仍存在约 1/3 的假阳性率。

### 3) 可能的普适教训 [Analysis]
- **AI 结构预测的"置信度"≠"功能有效性"**：对于任何由非共价相互作用（静电、疏水、氢键）网络决定结合特异性的蛋白-蛋白或蛋白-DNA 界面，AI 预测的高置信度结构不能替代热力学/动力学验证。
- **序列模式 vs 物理约束**：当训练数据中某一结构 motif 的序列特征过于显著（如 L-zip 的亮氨酸重复），深度网络可能学会"模式匹配"而非"物理推理"，导致对异常序列（如全电荷残基）的预测失效。
- **迁移到 TF-DNA 互作**：若用 AlphaFold 预测 TF-DNA 复合物，需警惕类似问题——DNA 结合界面的静电互补性（如碱性残基与磷酸骨架）可能被网络忽略，导致高置信度但物理上不可能的 TF-DNA 对接模式。

---

## 07 方法总览

**输入**：
- 蛋白质序列（FosB、JunD 全长序列，UniProt ID: P53539, P17535）
- 49 个人类 L-zip 蛋白的 L-zip 结构域序列（来自 Newman & Keating 2003 补充材料）
- 合成肽序列（设计为全 Glu 或全 Lys e/g 位点）

**输出**：
- 预测的二聚体 3D 结构（PDB 格式）
- 置信度指标：pLDDT（每个残基）、PAE（残基对）、ipTM（界面置信度）

**模块**：
1. **AlphaFold2-Multimer**（ColabFold v1.5.5，model_type="alphafold2_multimer_v3"）
2. **Boltz-1**（v0.41，AlphaFold3 开源重实现）
3. **AlphaFold2 变体**：关闭 MSA（msa_mode="single_sequence"）、关闭模板（template_mode="none"）、两者均关闭
4. **AlphaFold3**（Google DeepMind 服务器，2024 年 9 月访问）
5. **静电表面势计算**：PyMOL APBS 插件（默认设置）
6. **结构比对**：PyMOL align 命令（默认设置，cycles=5, cutoff=2.0）

**训练**：无（使用预训练模型）

**反馈回路**：无（单次前向预测）

**流程**：
1. 输入 FosB/JunD 全长序列至 AlphaFold2-Multimer，预测单体结构，确认 L-zip 区域
2. 预测 FosB/JunD 同源/异源二聚体（全长和 L-zip 截短），提取置信度指标
3. 对 49 个人类 L-zip 蛋白的所有可能二聚体组合（1928 对）运行 AlphaFold2 和 Boltz-1 预测
4. 将预测结果与 Newman & Keating (2003) 实验排名对比
5. 设计合成肽（全 Glu/全 Lys e/g 位点），预测其二聚体结构
6. 对合成肽进行 Leu→Ile 逐步突变，观察 L-zip 预测是否"断裂"
7. 计算预测结构的静电表面势，与实验已知的静电互补性对比

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AlphaFold2-Multimer 预测 | 预测二聚体 3D 结构 | 核心预测工具 | 输入：两条序列；输出：结构+置信度 | Results 图 2-3 | 无替代方案（核心工具） |
| 置信度指标提取（pLDDT/PAE/ipTM） | 量化预测可靠性 | 评估预测质量 | 输入：JSON 文件；输出：数值指标 | Results 图 3、表 1 | 移除后无法评估预测可靠性 |
| MSA/模板消融 | 测试输入数据源对预测的影响 | 探究预测偏差来源 | 输入：关闭 MSA/模板的配置；输出：结构+指标 | Results 图 6、Supplementary Figure 4 | 预期影响：无显著改善（实测） |
| Boltz-1 预测 | 测试 AlphaFold3 架构的判别能力 | 对比最新方法 | 输入：序列；输出：结构+指标 | Results 图 7b,d | 预期影响：ipSAE 组合有改善但仍高假阳性 |
| 静电表面势计算（APBS） | 可视化界面电荷互补性 | 物理验证预测界面 | 输入：PDB 结构；输出：静电势图 | Results 图 4 | 移除后无法物理评估界面可行性 |
| Newman & Keating 实验排名 | 提供二聚化可能性的实验基准 | 评估预测的判别能力 | 输入：实验数据；输出：排名（1-6） | Methods 节 | 无此基准则无法量化假阳性率 |
| 合成肽设计 | 构造极端静电排斥的测试用例 | 验证 AlphaFold 是否考虑静电 | 输入：设计序列；输出：预测结构 | Results 图 5、表 2 | 移除后无法直接证明静电盲区 |

**消融效应区分**：
- **实测消融**：关闭 MSA 或模板后，预测结果无显著差异（Supplementary Figure 4），说明 L-zip 预测主要由序列模式驱动而非进化信息。
- **预期效应**：若移除置信度指标，无法判断预测可靠性；若移除实验基准，无法量化假阳性率。

---

## 09 关键公式符号

本文未提出新的数学公式，但涉及以下关键概念：

**1. AUC-ROC（Area Under the Receiver Operating Characteristic Curve）**
- 用于量化 ipTM、pLDDT、PAE、ipSAE 指标区分真实/虚假二聚体的能力
- AUC = 0.5 表示无判别力，1.0 表示完美判别
- 本文结果：AlphaFold2 ipTM AUC = 0.566；Boltz-1 ipTM AUC = 0.736；Boltz-1 ipSAE AUC = 0.848

**2. RMSD（Root Mean Square Deviation）**
- 用于结构比对：预测结构 vs 晶体结构（PDB: 5VPF, 2H7H）
- 公式：RMSD = √(Σᵢδᵢ²/N)，其中 δᵢ 为第 i 对等价原子的距离，N 为原子对数
- 本文结果：所有比对 RMSD < 1 Å

**3. pLDDT（predicted Local Distance Difference Test）**
- 每个残基的局部置信度分数（0-100）
- 本文阈值：≥90 为高置信度

**4. ipTM（interface predicted Template Modelling score）**
- 界面置信度分数（0-1）
- 本文阈值：≥0.8 高置信度，0.6-0.8 中等置信度

**5. ipSAE（interface prediction Score from Aligned Errors）**
- Dunbrack (2025) 提出的改进指标，仅考虑低 PAE 残基对
- 本文使用 PAE cutoff = 3 Å，距离 cutoff = 5 Å

**6. ΔΔΔG_int（耦合能变化）**
- Vinson et al. (2002, 2006) 计算的 g-e 位点残基对耦合能
- 用于设计合成肽（选择最大正耦合能的残基组合）

---

## 10 实验设计与证据链

**数据集/群体**：
- FosB/JunD 系统：2 个蛋白，3 种二聚体组合（FosB/FosB、JunD/JunD、FosB/JunD）
- 大规模 L-zip 数据集：49 个人类 L-zip 蛋白，1928 个二聚体组合（含同源和异源）
- 合成肽：2 条设计序列（全 Glu e/g 位点、全 Lys e/g 位点），各 5 个七联重复

**指标**：
- 结构质量：RMSD（vs 晶体结构）
- 置信度：pLDDT、PAE、ipTM、ipSAE
- 判别能力：AUC-ROC

**基准**：
- Newman & Keating (2003) 实验二聚化排名（1-6 级）
- 晶体结构：FosB/JunD 异源二聚体（PDB: 5VPF）、JunD/JunD 同源二聚体（PDB: 2H7H）

**预算/资源**：
- ColabFold v1.5.5（免费在线服务）
- Galaxy Australia AlphaFold 服务
- Boltz-1 v0.41（本地部署，GPU 加速 MMSeqs）

**实验列表**：

| 实验 | 检验的 Claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-----------------|------|
| FosB/JunD 二聚体预测 | AlphaFold 能否准确预测已知 L-zip 二聚体结构 | 预测 vs 晶体结构（5VPF, 2H7H） | RMSD < 1 Å，结构准确 | AlphaFold 能准确预测 L-zip 几何结构 | 结构准确≠结合可行 | Results 表 1 |
| 置信度指标对比 | AlphaFold 置信度能否区分真实/虚假二聚体 | FosB/FosB（虚假）vs FosB/JunD（真实） | 两者 pLDDT≥90、ipTM 0.7-0.8，无显著差异 | 置信度指标无法区分二聚化可行性 | — | Results 图 2-3 |
| 大规模 AUC-ROC 分析 | ipTM 对 1928 个二聚体的判别能力 | AlphaFold2 vs Boltz-1 | AlphaFold2 AUC=0.566；Boltz-1 AUC=0.736 | 两者判别能力均弱 | Boltz-1 有改善但仍不足 | Results 图 7a,b |
| ipSAE 改进指标 | ipSAE 能否提升判别能力 | ipTM vs ipSAE（Boltz-1） | ipSAE AUC=0.848 | ipSAE 有改善 | 假阳性率仍约 1/3 | Results 图 7c,d |
| MSA/模板消融 | 输入数据源是否影响预测 | 正常 vs 无 MSA vs 无模板 vs 均无 | 结果无显著差异 | L-zip 预测不依赖进化信息 | — | Results 图 6、Supp Fig 4 |
| 合成肽预测 | AlphaFold 是否考虑静电排斥 | 全 Glu/全 Lys e/g 位点 | 仍预测高置信度平行 L-zip | AlphaFold 忽略静电排斥 | — | Results 图 5 |
| Leu→Ile 突变 | 亮氨酸模式是否是预测主驱动 | 1-3 个 Leu 突变为 Ile | 突变越多越易"断裂" | 亮氨酸重复模式主导预测 | 无单一关键 Leu 位点 | Results 表 2 |
| 静电表面势可视化 | 预测界面是否物理合理 | APBS 计算 vs 实验结构 | FosB 同源二聚体界面双负电荷 | 预测结构物理上不可能 | — | Results 图 4 |

---

## 11 结论正确解读

**结论的适用范围**：
- 仅适用于亮氨酸拉链（L-zip）卷曲螺旋二聚体，不适用于其他蛋白-蛋白互作类型
- 仅评估了 AlphaFold2-Multimer、AlphaFold2 变体、Boltz-1 和 AlphaFold3（有限测试），不涵盖其他 AI 结构预测方法
- 实验基准来自 Newman & Keating (2003) 的体外二聚化阵列，反映的是相对亲和力而非体内功能

**关键边界条件**：
1. **置信度≠可行性**：高 pLDDT/ipTM 仅表示网络对结构预测有信心，不表示该结构在热力学上可形成
2. **假阳性率极高**：AlphaFold2 的 ipTM 对真实/虚假二聚体几乎无判别力（AUC=0.566，接近随机）
3. **静电盲区**：AlphaFold 无法感知界面电荷排斥，对全 Glu/全 Lys 的极端序列仍预测高置信度二聚体
4. **改进有限**：Boltz-1 + ipSAE 组合改善明显（AUC=0.848），但假阳性率仍约 1/3，不足以作为筛选工具
5. **序列模式主导**：亮氨酸七联重复是预测的主要驱动因素，而非界面残基的理化性质

**不能得出的结论**：
- 不能认为 AlphaFold 对所有蛋白-蛋白互作预测都不可靠
- 不能认为 AlphaFold 预测的 L-zip 结构本身是错误的（结构几何可能是对的）
- 不能认为 Boltz-1 优于 AlphaFold2（两者判别力均不足，只是 Boltz-1 略好）

**对 TF-DNA 互作研究的启示**：
- 若用 AlphaFold 预测 TF 二聚化网络，需用实验数据（如酵母双杂交、Co-IP）交叉验证
- 高置信度预测不能作为二聚化可能性的证据
- 需结合静电计算（如 APBS、DelPhi）或能量评估工具（如 FoldX、Rosetta）进行二次筛选

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未测试所有 AlphaFold 版本 | 主要使用 AlphaFold2-Multimer 和 Boltz-1，AlphaFold3 仅有限测试 | 未来需系统评估 AlphaFold3 及更新版本 | Discussion 节 |
| 实验数据时间差 | Newman & Keating (2003) 数据可能未覆盖所有 L-zip 蛋白 | 需更新实验数据集 | Discussion 节 |
| 合成肽设计基于文献而非实验验证 | 合成肽的"不可能形成"假设基于 Vinson 等 (2002, 2006) 的耦合能计算 | 需实验验证合成肽确实不能二聚化 | Discussion 节 |
| 未评估结合强度 | AlphaFold 不提供 KD 或结合自由能，无法区分强/弱结合 | 需结合能量计算工具 | Discussion 节 |
| 未测试其他卷曲螺旋类型 | 仅测试了 L-zip，未涵盖其他卷曲螺旋亚型 | 需扩展至更广泛的卷曲螺旋家族 | Discussion 节 |

**作者提及的相关约束**（非正式局限）：
- AlphaFold 的置信度指标设计目标是结构预测而非结合预测，因此其"高置信度"不应被过度解读
- 训练数据中 L-zip 的序列特征可能过于显著，导致网络对异常序列的泛化能力差
- 静电效应在 AlphaFold 的表示中缺乏显式建模，这是架构层面的根本限制

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| AUC-ROC 分析将实验排名二值化（≥4 vs ≤3），可能丢失中间排名信息 | 排名 3-4 之间的二聚体可能具有中等亲和力，二值化可能高估或低估判别力 | 影响结论的定量准确性 | 使用连续分数（如 Z-score）进行回归分析而非分类 | Methods 节：排名 1-6 的划分方式 |
| 合成肽设计基于 Vinson 等 (2002, 2006) 的耦合能计算，但该计算本身可能不准确 | 如果合成肽实际上能形成二聚体，则"AlphaFold 预测正确"的替代解释成立 | 直接影响核心结论的有效性 | 实验验证合成肽的二聚化（如 CD 光谱、SEC-MALS） | Discussion 节：作者承认此局限 |
| 仅测试了 L-zip 卷曲螺旋，未涵盖其他二聚化结构域（如 bZIP 的碱性区、HLH 等） | L-zip 的序列模式（亮氨酸重复）可能特别容易导致"模式匹配"偏差，其他结构域可能表现不同 | 限制结论的泛化性 | 扩展至 bHLH、bZIP 全长度等系统 | 本文范围 |
| Boltz-1 的改进可能部分来自 ipSAE 指标而非模型本身 | 未单独评估 Boltz-1 的 ipTM 与 AlphaFold2 的 ipTM 对比 | 无法区分模型改进与指标改进的贡献 | 对 AlphaFold2 也计算 ipSAE 进行对比 | Results 图 7 |
| 未报告预测结构的物理化学验证（如分子动力学模拟、能量最小化） | 高置信度预测可能通过能量最小化后变得不合理，但作者未测试 | 可能提供额外的判别维度 | 对预测结构进行 MD 模拟或能量评估 | 未提供 |
| 样本量：1928 个二聚体中仅 286 个为"真"（排名≥4），类别不平衡可能影响 AUC 解释 | 类别不平衡下 AUC 可能偏高 | 影响对判别力高低的判断 | 报告 PR-AUC 或平衡精度 | Results 图 7 |

---

## 14 学到什么

### Agent 提炼的知识候选

**K1: 置信度指标的三重区分原则**
- 概念：AI 结构预测的置信度指标（pLDDT、PAE、ipTM）应区分为"结构确定性"、"界面确定性"和"结合可行性"三个层次
- 来源：本文核心发现——AlphaFold 对 L-zip 的几何预测高度自信，但对结合可行性无判别力
- 迁移到 TF-DNA：用 AlphaFold 预测 TF-DNA 复合物时，高 ipTM 不能作为结合特异性的证据；需额外验证 DNA 结合界面的静电互补性和氢键网络

**K2: 序列模式 vs 物理约束的偏差**
- 概念：当训练数据中某一结构 motif 的序列特征过于显著时，深度网络倾向于学习"模式匹配"而非"物理推理"
- 来源：L-zip 的亮氨酸重复模式主导预测，即使 e/g 位点充满排斥电荷仍预测二聚体
- 迁移到 TF-DNA：TF 的 DNA 结合域（如螺旋-转角-螺旋、锌指）有显著序列模式，AI 可能过度依赖这些模式而忽略 DNA 序列特异性相互作用的物理约束

**K3: 大规模实验数据作为 AI 评估基准**
- 概念：使用已发表的大规模实验筛选数据（如 Newman & Keating 2003 的 1928 个二聚体组合）作为 AI 预测的基准测试集
- 来源：本文方法——将 49 个 L-zip 蛋白的全组合实验数据与 AI 预测对比
- 迁移到 TF-DNA：可类似地使用蛋白结合微阵列（PBM）、SELEX 或 HT-SELEX 数据评估 AI 预测的 TF-DNA 结合特异性

**K4: 合成极端序列作为 AI 边界测试**
- 概念：设计物理上极端不利的序列（如全 Glu e/g 位点）来测试 AI 模型的物理感知能力
- 来源：本文合成肽实验——全 Glu/全 Lys 序列仍被预测为高置信度二聚体
- 迁移到 TF-DNA：可设计极端电荷分布的 DNA 序列（如全 A/T 或全 G/C 的识别位点）测试 AI 是否考虑 DNA 弯曲性和静电

**K5: 改进指标 ipSAE 的设计思路**
- 概念：通过仅考虑低 PAE 残基对来过滤界面置信度中的"噪声"贡献
- 来源：Dunbrack (2025) 的 ipSAE 指标，在 Boltz-1 上 AUC 从 0.736 提升至 0.848
- 迁移到 TF-DNA：类似地可设计仅考虑 DNA 接触残基的界面指标，过滤 TF 非结合区域的 PAE 贡献

**K6: 多方法交叉验证的必要性**
- 概念：AI 结构预测需与经典生物物理方法（静电计算、耦合能分析）交叉验证
- 来源：本文使用 APBS 静电势计算补充 AlphaFold 预测
- 迁移到 TF-DNA：AI 预测的 TF-DNA 复合物需用分子动力学模拟、MM-PBSA 或实验突变数据验证

---

## 15 与已有知识连接

**可直接连接的文献**：

1. **Newman & Keating (2003)**：本文的实验基准来源。该文对 49 个人类 L-zip 蛋白进行了全组合二聚化阵列筛选，提供了系统的二聚化亲和力排名。本文将其作为"真实标签"评估 AI 预测。→ 对 TF-DNA 研究：类似地可使用 PBM 或 HT-SELEX 数据作为 TF-DNA 结合特异性的基准。

2. **Vinson et al. (2002, 2006)**：L-zip g/e 位点耦合能的计算框架。本文使用其耦合能数据设计合成肽。→ 对 TF-DNA 研究：类似地可使用位置权重矩阵（PWM）或能量矩阵评估 TF-DNA 结合位点的物理可行性。

3. **Jumper et al. (2021) - AlphaFold2**：本文评估的核心工具。AlphaFold2 的 Evoformer 架构和置信度指标（pLDDT）是本文分析的基础。→ 对 TF-DNA 研究：AlphaFold3 已支持 DNA 预测，但需注意本文揭示的"置信度假象"问题。

4. **Abramson et al. (2024) - AlphaFold3**：本文对比的更新工具。AlphaFold3 支持核酸和共价修饰，但本文显示其 L-zip 判别力仍有限。→ 对 TF-DNA 研究：AlphaFold3 的 DNA 结合预测需同样谨慎。

5. **Dunbrack (2025) - ipSAE**：本文使用的改进指标。ipSAE 通过过滤低 PAE 残基对提升界面置信度评估。→ 对 TF-DNA 研究：可设计类似指标评估 TF-DNA 界面。

6. **Jumper et al. (2021) 的 CASP14 评估**：AlphaFold2 在单体预测上的成功与本文揭示的二聚体预测局限形成对比。→ 提示：AI 结构预测的"成功"可能局限于单链折叠，对互作界面的预测需额外验证。

**与课题方向的连接**：

- **TF-DNA 互作机制**：本文研究的 L-zip 是 bZIP 类 TF 的二聚化结构域，二聚化特异性直接决定 DNA 结合位点选择。本文发现 AI 无法区分 L-zip 二聚化可行性，意味着用 AI 预测 bZIP 网络存在系统性风险。
- **AI 方法**：本文提供了一套评估 AI 结构预测工具的方法论——使用大规模实验数据作为基准，设计极端序列测试边界，结合物理计算交叉验证。这套方法论可直接迁移到 TF-DNA 结合预测的评估。
- **物理模拟**：本文使用 APBS 静电势计算补充 AI 预测，提示静电相互作用是 AI 模型的盲区。对 TF-DNA 研究，静电互补性是 DNA 结合的核心驱动力，需显式纳入评估流程。

---

## 16 研究想法

### Agent 生成的研究候选

**R1: TF-DNA 结合预测的"置信度-可行性"解耦评估框架**
- **名称**：Confidence-Feasibility Decoupling (CFD) Framework for TF-DNA Binding Prediction
- **来源局限/观察**：本文发现 AlphaFold 对 L-zip 二聚体的置信度与结合可行性完全脱钩；TF-DNA 结合可能面临类似问题
- **核心假设**：AI 预测的 TF-DNA 复合物置信度指标无法反映结合特异性，需解耦评估
- **初步方法**：收集已发表的 TF-DNA 共晶结构（PDB）和 PBM/SELEX 数据，用 AlphaFold3 预测 TF-DNA 复合物，提取 ipTM/pLDDT/PAE 指标，与实验结合亲和力对比，计算 AUC-ROC
- **验证方式**：若 AUC 接近 0.5，则证实假设；若 AUC 较高，则 TF-DNA 预测可能优于 L-zip
- **创新状态**：unverified

**R2: 静电感知的 TF-DNA 结合位点筛选管道**
- **名称**：Electrostatic-Aware Filtering (EAF) Pipeline for TF-DNA Complex Validation
- **来源局限/观察**：本文证明静电排斥是 AlphaFold 的盲区；TF-DNA 结合高度依赖静电互补性
- **核心假设**：在 AI 预测后增加静电评估步骤可显著降低假阳性率
- **初步方法**：对 AlphaFold3 预测的 TF-DNA 复合物，用 APBS 或 DelPhi 计算界面静电势，评估 DNA 磷酸骨架与 TF 碱性残基的互补性；设定静电互补性阈值，过滤不合理复合物
- **验证方式**：在已知 TF-DNA 数据集上比较过滤前后的精确率/召回率
- **创新状态**：unverified

**R3: 基于耦合能的 TF 二聚化网络重评估**
- **名称**：Coupling-Energy Informed Re-evaluation of TF Dimerization Networks
- **来源局限/观察**：本文使用 Vinson 等 (2002, 2006) 的耦合能数据设计合成肽；类似方法可用于评估 AI 预测的 TF 二聚化网络
- **核心假设**：将耦合能计算与 AI 结构预测结合，可提高 TF 二聚化网络的预测准确性
- **初步方法**：对 bZIP 家族全部成员，用 AlphaFold-Multimer 预测所有二聚体组合，同时用 Vinson 耦合能表计算每个组合的 ΔΔΔG；将两者结合（如加权评分）与实验数据对比
- **验证方式**：与 Newman & Keating (2003) 及更新的 bZIP 二聚化数据对比
- **创新状态**：unverified

**R4: 极端序列测试集构建——AI 物理感知能力的通用评估**
- **名称**：Extreme Sequence Test Suite (ESTS) for Probing AI Physical Awareness
- **来源局限/观察**：本文的合成肽实验（全 Glu/全 Lys）是测试 AI 物理感知的有效方法
- **核心假设**：通过设计物理上极端不利的序列，可系统评估 AI 模型对静电、疏水等物理约束的感知能力
- **初步方法**：对多种蛋白-蛋白和蛋白-DNA 互作系统，设计极端电荷、极端疏水、极端体积的序列变体，用不同 AI 结构预测工具预测，评估其是否"识别"物理不可行性
- **验证方式**：与实验数据（如突变体的结合亲和力）对比
- **创新状态**：unverified

**R5: 分子动力学模拟作为 AI 预测的二级筛选**
- **名称**：MD-Based Secondary Screening of AI-Predicted TF-DNA Complexes
- **来源局限/观察**：本文指出 AlphaFold 的松弛算法无法克服静电排斥；MD 模拟可能提供更真实的物理评估
- **核心假设**：对 AI 预测的 TF-DNA 复合物进行短时 MD 模拟，复合物的结构稳定性可区分真实与虚假结合
- **初步方法**：选取 AI 预测的 TF-DNA 复合物（包括已知真实和虚假的），进行 100-500 ns 的 MD 模拟，监测复合物稳定性（RMSD、接触面积、氢键保持率）
- **验证方式**：比较真实与虚假复合物的 MD 稳定性指标，评估判别力
- **创新状态**：unverified

**R6: 结合特异性预测的 AUC-ROC 基准测试集构建**
- **名称**：Benchmark Suite for TF-DNA Binding Specificity Prediction
- **来源局限/观察**：本文展示了 AUC-ROC 分析在评估 AI 判别力方面的价值；TF-DNA 领域缺乏类似系统评估
- **核心假设**：构建包含真实和虚假 TF-DNA 结合对的基准测试集，可系统评估不同 AI 工具的预测能力
- **初步方法**：整合 PDB 共晶结构（真实）、PBM/SELEX 阴性数据（虚假）、突变体数据，构建平衡数据集；用 AlphaFold3、Boltz-1、RoseTTAFold 等预测，计算 AUC-ROC 对比
- **验证方式**：多工具对比，识别最优工具和共同盲区
- **创新状态**：unverified