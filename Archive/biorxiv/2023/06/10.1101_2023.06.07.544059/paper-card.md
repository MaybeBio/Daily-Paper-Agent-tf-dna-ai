## 01 基本信息

- **标题**：Modelling protein complexes with crosslinking mass spectrometry and deep learning
- **作者**：Stahl K; Demann L; Bremenkamp R; Warneke R; Hormes B; Stülke J; Brock O; Rappsilber J
- **单位**：未提供（根据作者信息推测涉及 Rappsilber 实验室，具体单位未在摘要中列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2023-06-09
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：结构生物学 × 深度学习 × 交联质谱（crosslinking MS）
- **关键词**：AlphaFold-Multimer、AlphaLink、crosslinking mass spectrometry、protein complex、distance restraints、SDA、DSSO
- **DOI/arXiv 号**：10.1101/2023.06.07.544059
- **代码**：https://github.com/Rappsilber-Laboratory/AlphaLink2
- **数据**：模型权重存放于 Zenodo（doi:10.5281/zenodo.8007238）；整合模型存放于 PDB-Dev（PDBDEV_00000221 和 PDBDEV_G_1000003）
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：本文聚焦蛋白质复合物（protein complex）结构预测，而非直接的 TF–DNA 互作。但其核心方法——将实验距离约束（crosslinking MS）整合进 AlphaFold-Multimer 的 pair representation——对 TF–DNA 互作建模具有高度可迁移性：TF–DNA 复合物同样面临共进化信号弱、结构数据稀缺的问题，实验约束（如交联、足迹法、突变数据）可类似地引导采样和模型选择。本文属于「实验数据引导的深度学习结构预测」这一子方向。

---

## 02 一句话总结

本文将交联质谱（crosslinking MS）产生的距离约束整合进 AlphaFold-Multimer（扩展 AlphaLink 至复合物），在挑战性异源复合物（CASP15 靶标、抗体-抗原、CRL4 复合物）上显著提升结构预测质量，并利用全细胞交联数据揭示了枯草芽孢杆菌铁稳态调控的分子机制。

---

## 03 研究问题

- **具体问题**：蛋白质复合物的结构预测因缺乏共进化信息和已解析结构而困难重重。能否将实验获得的距离约束（crosslinking MS）直接整合进深度学习结构预测流程，以提升复合物预测质量？
- **为什么重要**：蛋白质复合物是生命过程的核心执行者，但其结构解析远难于单体蛋白。实验约束（如交联）可提供直接的物理邻近信息，弥补进化信息的不足。
- **现有方法不足**：AlphaFold-Multimer 依赖 MSA 中的共进化信号，在复合物上信号弱；传统交联数据仅用于验证或后处理，未在预测过程中直接引导模型。
- **精确的「Can ... ?」研究问题**：Can integrating crosslinking MS-derived distance restraints into AlphaFold-Multimer (via AlphaLink) substantially improve the modelling of challenging heteromeric protein complexes, even with sparse, noisy, and cross-linker-heterogeneous data?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架，未做外部系统核验，标注为「仅本文框架」。

1. **单体蛋白结构预测**：AlphaFold2 通过 MSA 共进化信息实现高精度单体预测（引用 1）。
2. **复合物预测的挑战**：AlphaFold-Multimer 扩展至复合物，但共进化信号弱、搜索空间随链数指数增长（引用 2）。
3. **交联质谱作为实验约束**：交联可识别邻近残基对，用于验证互作界面（引用 3–6）。
4. **AlphaLink（单体版）**：将交联距离约束直接注入 AlphaFold2 的 pair representation，提升单体预测（引用 7，即作者前期工作）。
5. **本文扩展**：将 AlphaLink 从单体扩展至复合物（AlphaLink-Multimer），系统评估在 CASP15、抗体-抗原、全细胞交联数据、CRL4 复合物上的表现。

**本文主张的位置**：在「深度学习结构预测 + 实验约束」交叉点上，首次系统验证了交联约束对复合物预测的增益，并展示了全细胞尺度应用的可行性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 复合物共进化信号弱 | AlphaFold-Multimer 在挑战性异源复合物上 DockQ 低（平均 0.14） | 异源复合物缺乏足够的共进化序列信息 | Results 图 1a |
| 交联数据稀疏且含噪声 | 模拟数据仅 10% 序列覆盖、20% FDR | 实验交联数据天然稀疏且含假阳性 | Methods 节（模拟设置） |
| 交联剂异质性 | 训练用 SDA，测试用 DSSO 和 sulfo-SDA | 不同交联剂反应残基、连接长度不同 | Results（B. subtilis 和 CRL4 部分） |
| 同源复合物中交联归属模糊 | "self" 交联无法区分链内/链间 | 同源亚基对称性导致歧义 | 引言部分 |
| 计算成本高 | 5900 AA 复合物单样本约 30 小时（A100, 20 recycling） | 大复合物采样和 recycling 开销大 | Results 节（H1129 部分） |
| 模型选择困难 | 高置信度预测不一定对应高 DockQ | 模型置信度在困难靶标上高估 | Extended Data 图 10 |

---

## 06 核心思想

### 1) 表面方法
将交联质谱产生的距离约束（残基对）编码为 soft label contact map，通过一个 crosslink embedding layer 投影到 AlphaFold-Multimer 的 pair representation（z-space），在结构预测过程中直接偏置注意力计算。

### 2) 核心洞察
交联约束不仅是验证工具，更是可参与预测的「软约束」——通过注入 pair representation，交联信息与 MSA 共进化信息耦合更新，使网络学会在噪声中提取真实空间邻近信号（噪声拒绝机制）。稀疏的约束足以大幅缩小构象搜索空间，尤其在共进化信号弱的复合物上。

### 3) 可能的普适教训 [Analysis]
- 实验约束与进化信息的「耦合」比「后处理过滤」更有效——约束应在模型内部参与推理，而非仅作为评分函数。
- 对 TF–DNA 互作：DNA 结合位点、足迹法、突变数据等实验约束可类似地编码为「位置对」或「界面偏置」，注入结构预测模型。
- 稀疏但高信息量的约束（如单条交联）足以产生质的提升，提示「少而准」的实验数据策略。

---

## 07 方法总览

- **输入**：氨基酸序列（复合物各链）、MSA（与 AlphaFold-Multimer 相同）、交联距离约束（残基对列表，含 soft label）
- **输出**：复合物三维结构（原子坐标）、模型置信度（pLDDT / ipTM）
- **模块**：
  1. AlphaFold-Multimer 主干（v2.2 或 v2.3 权重）
  2. Crosslink embedding layer（新增）：将 soft label contact map 投影到 128-d z-space，加到 pair representation
  3. 训练：在 DIPS-Plus 数据集（11,424 个复合物，34,054 条链）上微调，模拟 SDA 交联（XWalk 生成，25 Å Cα-Cα 截断，10% 覆盖，20% FDR）
- **推理**：与 AlphaFold-Multimer 相同，但 recycling 增至 20，采样数增至 200（部分靶标）
- **反馈回路**：交联信息与 MSA 表示耦合更新，实现噪声拒绝
- **假设**：交联距离约束（< 25 Å Cα-Cα）能提供足够的空间邻近信息以引导折叠和对接

**文字流程**：
1. 输入序列 → 生成 MSA 和模板特征
2. 交联列表 → 构建 soft label contact map → crosslink embedding → 加入 pair representation
3. Evoformer 迭代更新（MSA + pair 表示耦合）
4. Structure module 输出三维坐标
5. 按模型置信度 + 交联满足度选择最佳模型

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Crosslink embedding layer | 将交联距离约束投影到 pair representation | 使交联信息直接参与注意力计算，而非后处理 | 输入：soft label contact map；输出：128-d 向量加到 z | Results 图 1a（DockQ 0.14→0.62） | 预期：移除后性能回退至 AlphaFold-Multimer 基线 [Analysis：作者未做显式消融，但对比实验支持此推断] |
| 噪声拒绝机制（MSA-pair 耦合更新） | 在迭代中区分真实交联与假阳性 | 交联数据含 20% FDR，需网络自行学习过滤 | 输入：MSA + pair 表示；输出：更新后的表示 | Results 图 1c,d（H1142、H1166 假交联全被拒绝） | 预期：移除后假交联将误导预测 [Analysis：作者未做显式消融] |
| Recycling 增加（3→20） | 更多迭代优化 | 交联约束需要更多轮次传播到全局结构 | 输入：中间表示；输出：更新表示 | Results 节（H1141 需更多 recycling 选择正确簇） | 实测：增加 recycling 对部分靶标（H1141）必要 |
| 采样增加（25→200） | 更充分探索构象空间 | 交联约束缩小搜索空间，但仍有多个局部最优 | 输入：随机种子；输出：多样预测 | Results 图 1a | 预期：减少采样会降低找到正确构象概率 [Analysis] |
| 微调训练（DIPS-Plus） | 适应复合物交联数据分布 | 预训练权重未见过交联特征 | 输入：复合物 + 模拟交联；输出：微调权重 | Methods 节 | 预期：不微调则交联 embedding 无法有效学习 [Analysis] |

---

## 09 关键公式符号

本文为深度学习方法论文，未提供显式数学公式。核心概念可用以下形式化描述：

- **Soft label contact map**：对每个残基对 (i, j)，若存在交联证据，则 C(i,j) = 1（或概率权重），否则 C(i,j) = 0
- **Crosslink embedding**：E = W · C，其中 W 为可学习投影矩阵，E 加到 pair representation z：z' = z + E
- **DockQ 评分**（评估指标，非模型公式）：
  DockQ = (F_nat + iRMS_norm + LRMS_norm) / 3
  其中 F_nat 为天然接触恢复率，iRMS 为界面 RMSD，LRMS 为配体 RMSD（引用 12, 33）

> 注：作者未在摘要中给出具体公式，以上为基于方法描述的合理形式化 [Analysis]。

---

## 10 实验设计与证据链

### 数据集与设置
- **CASP15 异源复合物**：8 个挑战性靶标（H1129, H1134, H1140, H1141, H1142, H1144, H1166, H1167），模拟 SDA 交联（10% 覆盖，20% FDR）
- **抗体-抗原**：33 个 SAbDab 靶标（2022-01-01 至 2023-10-11），模拟交联
- **B. subtilis 全细胞**：135 个二聚体 PPI，DSSO 交联（真实数据，中位 1 条交联/PPI）
- **CRL4 复合物**：6 亚基，360 kDa，3118 AA，sulfo-SDA 真实数据
- **基线**：AlphaFold-Multimer（v2.2 或 v2.3）
- **指标**：DockQ、模型置信度（ipTM/pTM）
- **计算资源**：4× A100 GPU，训练 10 天

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| CASP15 异源复合物 | 交联约束提升挑战性靶标预测 | AlphaLink vs AlphaFold-Multimer（同 MSA，recycling 20, 200 样本） | DockQ 平均 0.14→0.62，与 CASP15 最佳方法相当 | 交联约束显著提升异源复合物预测 | 样本量小（8 靶标），模拟数据与真实数据有差距 | Results 图 1a |
| 控制实验（recycling=3, 10 样本） | 排除采样量增加的影响 | AlphaLink vs AF-M（同 recycling=3, 10 样本） | AlphaLink 仍优于 AF-M | 提升来自交联约束而非采样量 | 未提供具体数值 | Extended Data 图 1 |
| 抗体-抗原 | 交联约束在低共进化信号场景有效 | AlphaLink vs AF-M（3 recycling, 5 样本） | DockQ 平均 0.29→0.6；AF-M 5/6 错误，AlphaLink 5/6 中高质量 | 交联约束对免疫复合物特别有效 | 模拟交联，非实验数据 | Results 图 1b |
| B. subtilis 全细胞 | 单条真实交联足以提升预测 | AlphaLink vs AF-M（135 个 PPI） | 中位置信度 0.42→0.6；12 个额外 PPI 达 >0.75 | 稀疏真实数据可用；跨交联剂泛化 | 无晶体结构验证，依赖模型置信度 | Results 图 2 |
| CodY-YppF 案例 | 单条交联的因果效应 | 有/无该交联的预测对比 | 置信度 0.25→0.81 | 单条交联可戏剧性改变预测 | 单案例 | Results 图 2b |
| RpoA-RpoC 案例 | 交联提升 DockQ | AlphaLink vs AF-M（4 条真实交联） | DockQ 0.22→0.69（AF-M v2.2）；0.69-0.7（各单条交联） | 每条交联独立足以提升 | 小样本 | Results 图 2c |
| Fur-Fpa 复合物 | 交联约束揭示真实生物学机制 | AlphaLink 预测 vs 突变验证 | 预测模型置信度 0.84；突变破坏互作 | 预测结构具有生物学可验证性 | 仅一个系统 | Results 图 3 |
| CRL4 复合物 | 多亚基大复合物可行性 | AlphaLink v2.3 vs AF-M v2.3 | 置信度 0.56→0.64；Vpr 定位正确 | 交联约束对 6 亚基复合物有效 | 仅一个复合物 | Results 图 4 |

---

## 11 结论正确解读

- **任务范围**：异源蛋白质复合物结构预测（二聚体至 6 亚基），聚焦挑战性靶标（低共进化信号、柔性界面）。
- **Oracle/真值输入**：交联距离约束（模拟或真实）作为额外输入，非端到端自动生成。
- **端到端状态**：非端到端——需要实验交联数据作为输入；预测后仍需模型置信度/交联满足度进行模型选择。
- **算力成本**：高——5900 AA 复合物单样本约 30 小时（A100, 20 recycling），200 样本约 6000 GPU 小时。
- **历史数据依赖**：依赖 DIPS-Plus 训练集（PDB 复合物），交联模拟参数（25 Å 截断、20% FDR）影响泛化。
- **模型依赖**：基于 AlphaFold-Multimer v2.2/v2.3 权重微调，非从头训练。
- **最难情形**：柔性复合物（H1134）、交联约束不足或模糊（同源复合物）、大复合物（计算成本）。
- **群体/领域边界**：异源复合物；同源复合物明确排除（交联归属歧义）；未涉及 TF–DNA 或蛋白质-核酸复合物。
- **不确定性**：B. subtilis 结果依赖模型置信度而非实验结构验证；模拟交联与真实交联存在分布差异。

**有边界的复述**：在异源蛋白质复合物上，整合交联距离约束的 AlphaLink 较 AlphaFold-Multimer 显著提升 DockQ（0.14→0.62），且对稀疏真实数据（单条交联）有效；但该方法需要实验交联输入、计算成本高、未覆盖同源复合物和核酸复合物。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 同源复合物中交联归属模糊 | "self" 交联无法区分链内/链间 | 未明确提及 | 引言部分 |
| 模拟交联与真实数据存在差异 | 训练用 SDA 模拟，测试用 DSSO/sulfo-SDA | 未明确提及 | Methods 节 |
| 计算成本高 | 大复合物采样昂贵 | 未明确提及 | Results 节（H1129） |
| 模型置信度在困难靶标上高估 | 置信度与 DockQ 相关性有限 | 用交联满足度辅助模型选择 | Extended Data 图 10 |
| 训练数据覆盖偏差 | 模拟交联均匀采样，真实数据有残基偏好 | 未明确提及 | Methods 节 |

> 注：作者在摘要中未系统列出局限，以上为从正文中提取的明确或隐含局限 [Analysis]。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 模拟交联与真实交联的分布差异 | 模拟数据（均匀采样、25 Å 截断）可能过于理想；真实交联有残基偏好、连接长度分布更宽 | 影响方法在真实数据上的泛化性 | 在更多真实交联数据集上评估（如 CrossLink-DB） | Methods 节（模拟设置） |
| 评估靶标数量有限 | CASP15 仅 8 个异源复合物，统计功效有限 | 结论可能过度泛化 | 扩大评估集（如 CAMEO 复合物、自建数据集） | Results 图 1a |
| 未与其它实验约束方法对比 | 未对比如 distance geometry、restrained MD 等传统方法 | 无法判断深度学习方法相对传统方法的增量 | 在相同靶标上运行多种方法对比 | 未提供 |
| 模型置信度作为主要评估指标 | B. subtilis 部分无晶体结构验证，依赖 pLDDT/ipTM | 置信度可能系统性高估 | 对部分预测进行实验验证（如突变、交联验证） | Results 图 2, 3 |
| 未报告失败案例 | 未讨论哪些靶标交联约束无效或有害 | 无法判断方法的适用边界 | 系统分析失败案例特征 | 未提供 |
| 计算成本未系统报告 | 仅提及单样本 30 小时，未报告总预算 | 影响方法可复现性和实用性 | 报告完整计算预算和资源需求 | Results 节（H1129） |
| 对 TF–DNA 互作的适用性未验证 | 方法针对蛋白质复合物设计，未测试蛋白质-核酸体系 | 本课题读者需自行评估迁移性 | 在 TF–DNA 复合物上测试交联约束（如 DNA-protein crosslinking） | 未提供 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **实验约束注入 pair representation 的架构设计**：将稀疏、含噪的距离约束编码为 soft label contact map，通过可学习投影加入 pair representation，与 MSA 信息耦合更新。可迁移至 TF–DNA 互作：将 DNA 足迹法、甲基化保护、突变扰动等实验数据编码为「位置对约束」或「界面偏置」，注入结构预测模型（如 AlphaFold3 或 RoseTTAFoldNA）。

2. **噪声拒绝机制**：网络在迭代中学会区分真实交联与假阳性（H1142、H1166 中 100% 假交联被拒绝）。对 TF–DNA 互作：实验数据（如 ChIP-seq 峰、突变效应）含大量噪声，类似机制可提升鲁棒性。

3. **单条约束的因果效应**：单条真实交联即可戏剧性提升预测（CodY-YppF 置信度 0.25→0.81）。对 TF–DNA 互作：单个关键残基的突变数据或单条 DNA 交联可能足以区分竞争构象。

4. **模型选择策略**：用「交联满足度 + 模型置信度」联合选择预测，优于单一置信度。对 TF–DNA 互作：可用实验约束满足度（如突变数据一致性）辅助选择 TF–DNA 复合物构象。

5. **跨交联剂泛化**：训练用 SDA，测试用 DSSO/sulfo-SDA 仍有效，说明模型学到的是「空间邻近」的通用概念而非特定化学特征。对 TF–DNA 互作：不同实验方法（足迹法、交联、突变）产生的约束可统一编码。

6. **全细胞尺度应用**：从全细胞交联数据中提取单条约束即可用于结构预测，提示「体内」实验数据可直接引导结构建模。对 TF–DNA 互作：体内 ChIP-seq 或 Hi-C 类数据可能提供类似的空间约束。

7. **生物学发现驱动**：方法不仅提升预测，还揭示了铁稳态调控机制（Fur-Fpa 拮抗）。对 TF–DNA 互作：结构预测可直接产生可验证的生物学假说（如 TF 如何被小分子或蛋白拮抗剂调控）。

---

## 15 与已有知识连接

- **AlphaFold2 / AlphaFold-Multimer**（Jumper et al., Nature 2021; Evans et al., 2021）：本文基于其架构，扩展了输入特征（交联约束）。本课题读者应熟悉 AF2 的 pair representation 和 Evoformer 机制。
- **AlphaLink（单体版）**（Stahl et al., 2022）：本文是其复合物扩展。单体版已验证交联约束对单体预测的增益。
- **交联质谱（crosslinking MS）**：CX-MS 技术（如 DSSO、SDA、sulfo-SDA）用于识别空间邻近残基对。本课题读者可参考 Graziadei & Rappsilber 等综述。
- **CASP15 复合物预测评估**：本文与 CASP15 最佳方法对比，说明交联约束可达到与大规模采样相当的效果。
- **DockQ 评分**（Basu & Wallner, 2016）：复合物结构评估标准指标。
- **B. subtilis 铁稳态**：Fur 蛋白是铁摄取调节因子，Fpa（YlaN）为其拮抗剂。本课题读者若研究 TF–DNA 互作，Fur–DNA 结合机制是经典模型系统。
- **可迁移领域**：蛋白质-核酸复合物预测（AlphaFold3、RoseTTAFoldNA）、实验约束引导的结构预测（如 cryo-EM 密度引导的 AF2）、交联数据在结构生物学中的应用。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF–DNA 复合物的交联约束引导预测
- **名称**：Crosslink-guided TF–DNA complex structure prediction
- **来源局限/观察**：本文方法针对蛋白质复合物，未验证蛋白质-核酸体系；TF–DNA 复合物共进化信号弱、结构数据稀缺。
- **核心假设**：将 DNA-protein 交联数据（如 UV 交联、 formaldehyde crosslinking）编码为距离约束，注入 AlphaFold3 或 RoseTTAFoldNA，可提升 TF–DNA 复合物预测精度。
- **初步方法**：扩展 AlphaLink 的 crosslink embedding 至核酸残基；在已知 TF–DNA 复合物（如 LacI、p53、Fur）上模拟交联数据训练；用真实交联数据（如 ChIP-exo 或 XChIP）验证。
- **验证方式**：与 AlphaFold3 基线对比 DockQ / DNA 界面 RMSD；在挑战性 TF（如柔性 bZIP 家族）上测试。
- **创新状态**：unverified

### 候选 2：单残基突变数据作为「软约束」引导 TF–DNA 构象选择
- **名称**：Mutation-guided conformational selection for TF–DNA complexes
- **来源局限/观察**：本文显示单条交联足以戏剧性改变预测；TF–DNA 互作中大量突变数据（如 DNase footprinting、SELEX 突变体）未被用于结构预测。
- **核心假设**：将突变对结合亲和力的影响编码为「界面偏好」约束，可辅助选择正确的 TF–DNA 构象。
- **初步方法**：从文献/数据库（如 ProTherm、CisBP）收集 TF–DNA 突变数据；将突变效应映射为残基对约束；在 AF2/AF3 预测后处理中作为重排序信号。
- **验证方式**：在已知结构的 TF–DNA 复合物上测试重排序是否提升 DockQ。
- **创新状态**：unverified

### 候选 3：全细胞交联数据驱动的 TF–DNA 互作组学
- **名称**：In-cell crosslinking for genome-scale TF–DNA interaction modelling
- **来源局限/观察**：本文用全细胞交联数据（B. subtilis）揭示了新的蛋白-蛋白互作机制；类似策略可扩展至 TF–DNA 互作。
- **核心假设**：全细胞交联数据（如 in vivo UV crosslinking + ChIP）可提供 TF–DNA 空间邻近信息，用于大规模互作建模。
- **初步方法**：整合已发表的 in vivo 交联数据（如 ChIA-PET、HiChIP）与结构预测；开发将交联信号转换为结构约束的流程。
- **验证方式**：在已知调控子（如 Fur、LexA）上验证预测结构与实验数据一致性。
- **创新状态**：unverified

### 候选 4：交联约束对同源 TF 二聚体的去模糊化
- **名称**：Disambiguating homo-dimeric TF–DNA complexes with crosslinking
- **来源局限/观察**：本文明确排除同源复合物（交联归属歧义）；但许多 TF 以同源二聚体结合 DNA（如 bZIP、bHLH）。
- **核心假设**：结合 DNA 足迹数据（区分链内/链间交联）可解决同源二聚体的交联归属问题。
- **初步方法**：开发链特异性交联归属算法；在已知同源二聚体 TF–DNA 复合物上测试。
- **验证方式**：与晶体结构对比 DockQ。
- **创新状态**：unverified

### 候选 5：交联约束与分子动力学模拟的联合采样
- **名称**：Integrating crosslinking restraints into MD-based TF–DNA docking
- **来源局限/观察**：本文方法为静态预测；TF–DNA 结合涉及构象变化，MD 模拟可捕捉动态过程。
- **核心假设**：将交联约束作为 MD 模拟中的偏置势（restraint potential），可加速 TF–DNA 结合路径采样。
- **初步方法**：在 MD 模拟（如 GROMACS、OpenMM）中实现交联约束的 harmonic potential；在已知 TF–DNA 体系上测试结合自由能面。
- **验证方式**：与无约束 MD 对比结合路径和构象分布。
- **创新状态**：unverified

---

> **证据与来源说明**：本 Card 所有数值（DockQ 0.14→0.62、置信度 0.25→0.81、30 小时/样本等）均直接引自摘要或正文；未提供的信息标注「未提供」或「Not assessable」。标注 [Analysis] 的内容为基于原文的合理推断，非作者原话。