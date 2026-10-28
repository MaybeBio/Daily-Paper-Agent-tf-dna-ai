## 01 基本信息

- **标题**：The transcription factor FoxP3 can fold into two dimerization states with divergent implications for regulatory T cell function and immune homeostasis
- **作者与单位**：Leng, Fangwei; Zhang, Wenxiang; Ramirez, Ricardo N; Leon, Juliette; Zhong, Yi; Hou, Lifei; Yuki, Koichi; van der Veeken, Joris; Rudensky, Alexander Y; Benoist, Christophe; Hur, Sun（哈佛医学院/波士顿儿童医院等）
- **期刊/预印本平台**：Immunity
- **年份**：2022-08-05
- **论文类型**：研究论文（结构生物学 + 功能验证）
- **领域**：免疫学；转录因子结构与功能；蛋白质-DNA互作
- **关键词**：FoxP3；forkhead domain；dimerization；regulatory T cell；Runx1；IPEX syndrome
- **DOI/arXiv 号**：10.1016/j.immuni.2022.07.002
- **代码**：未提供
- **数据**：PDB 7TDW、7TDX（晶体结构坐标）
- **阅读日期**：未提供
- **在该方向中的位置**：本文聚焦转录因子 FoxP3 的 forkhead 结构域（DBD）如何通过二聚化状态转换实现功能分化，属于「TF–DNA 结合机制」的结构生物学研究。对 AI/深度学习方向而言，本文提供了 TF 二聚化状态与 DNA 结合特异性之间的结构基础，可作为结构预测（如 AlphaFold2 多聚体预测）和 DNA 结合特异性预测模型的重要验证与训练数据来源；对物理模拟方向，本文的 head-to-head 二聚体结构可作为 MD 模拟和对接研究的靶标体系。

## 02 一句话总结

本文通过晶体结构、生化实验和细胞功能实验证明：FoxP3 的 forkhead 结构域在 RBR linker 存在时折叠为非交换（non-swap）单体，并在结合 DNA 时形成 head-to-head 二聚体；而 RBR 缺失或 IPEX 突变（如 R337Q）会导致 forkhead 形成 domain-swap 二聚体，从而损害 DNA 结合、Runx1 招募和 Treg 抑制功能。

## 03 研究问题

- **具体问题**：FoxP3 作为 forkhead 家族转录因子，其 forkhead DBD 如何通过特定的二聚化模式实现独特的 DNA 结合特异性和功能？此前报道的 domain-swap 二聚体是否为 FoxP3 的生理相关构象？
- **为什么重要**：FoxP3 是 Treg 细胞命运决定的关键转录因子，其突变导致 IPEX 综合征。理解 FoxP3 的生理构象对于阐明其调控机制和疾病机理至关重要。
- **现有方法为何不足**：此前研究仅使用分离的 forkhead 结构域进行结构解析，忽略了 RBR linker 对结构折叠的影响，导致 domain-swap 二聚体被误认为生理构象。
- **精确的 Can 问题**：Can FoxP3 的 forkhead 结构域在包含 RBR linker 的完整上下文（native context）中折叠为非交换单体，并通过 head-to-head 二聚化实现 DNA 结合和功能？

## 04 背景与发展脉络

**注：以下脉络基于本文引言与讨论，属于「仅本文框架」，未经外部系统核验。**

1. **阶段一：forkhead DBD 的经典结构研究**（2000s-2010s）
   - 代表性方法：X 射线晶体学解析分离的 forkhead DBD 与 DNA 复合物
   - 发现：forkhead DBD 呈 winged-helix 折叠，以单体形式识别 7 bp 核心基序（TGTTTAC）
   - 局限：无法解释 FoxP 家族成员在 Treg 中的独特功能

2. **阶段二：FoxP 家族 domain-swap 二聚体的发现**（2011）
   - 代表性方法：分离的 FoxP3 forkhead 结构域晶体结构解析（Bandukwala et al., 2011）
   - 发现：FoxP3 forkhead 形成 domain-swap 二聚体，被认为是 FoxP 家族的独特特征
   - 局限：使用分离的 DBD，忽略了 N 端 linker（RBR）对折叠的影响

3. **阶段三：本文的修正与整合**（2022）
   - 代表性方法：包含 RBR 的更长构建体（FoxP3ΔN）的晶体结构 + 生化 + 细胞功能验证
   - 发现：RBR 是 forkhead 正确折叠所必需；生理构象为 head-to-head 二聚体；domain-swap 是 RBR 缺失或突变导致的病理性构象
   - 意义：为 forkhead 家族 TF 的功能分化提供了「二聚化状态转换」的新范式

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 分离 DBD 结构误导生理构象 | 仅用 forkhead 结构域解析结构，得到 domain-swap 二聚体，被误认为生理形式 | RBR linker 对 forkhead 折叠至关重要，缺失 RBR 导致疏水残基暴露，驱动 swap 二聚化 | Results 图 1B：FoxP3forkhead 为二聚体，FoxP3RBR-forkhead 为单体；Results 图 2A 结构对比 |
| FoxP3 的 DNA 结合特异性不明 | 单体 forkhead 仅识别 7 bp 基序，无法解释 FoxP3 在基因组中的广泛结合 | head-to-head 二聚体可识别约 18 bp 的倒置重复序列（IR-FKHM），扩展了结合谱 | Results 图 1C-D：FoxP3ΔN 偏好 IR-FKHM4g；Results 图 5A-B：ChIP-seq 分析 |
| IPEX 突变的致病机制不清 | 多个 IPEX 突变位于 forkhead 表面，但机制不明 | 部分突变（如 R337Q）通过破坏非交换折叠、诱导 swap 二聚化来损害功能 | Results 图 7G-H：R337Q 诱导 swap 二聚体，A372S 可逆转 |
| Runx1 协同结合机制不明 | FoxP3 与 Runx1 的相互作用机制缺乏结构解释 | head-to-head 二聚化形成的大疏水表面为 Runx1 提供对接位点 | Results 图 6A-D：二聚化界面突变降低 Runx1 结合 |

## 06 核心思想

### 1) 表面方法
- 纯化包含 RBR linker 的 FoxP3 截短体（FoxP3ΔN），与 IR-FKHM4g DNA 共结晶
- 解析 3.1-4.0 Å 晶体结构（PDB: 7TDW, 7TDX）
- 结合 SEC-MALS、EMSA、pull-down、细胞功能实验验证构象与功能关系

### 2) 核心洞察
- **RBR linker 是 forkhead 正确折叠的「分子伴侣」**：RBR 通过保护 forkhead 疏水核心，防止 domain-swap 二聚化，维持非交换单体构象
- **head-to-head 二聚化是 FoxP3 功能的关键**：两个 forkhead 单体以 head-to-head 方式结合 DNA 倒置重复序列，扩展识别长度至约 18 bp，并形成 Runx1 对接表面
- **domain-swap 是病理性构象**：RBR 缺失或特定 IPEX 突变（R337Q）导致 forkhead 错误折叠为 swap 二聚体，功能受损

### 3) 可能的普适教训 [Analysis]
- **结构生物学中构建体设计决定结论**：仅用分离 DBD 研究 TF-DNA 互作可能得出误导性结论；包含 linker/侧翼序列的更长构建体更接近生理状态
- **二聚化状态可作为 TF 功能分化的进化策略**：同一 DBD 折叠可通过二聚化模式转换实现 DNA 结合特异性与辅因子招募的多样化
- **对 AI 结构预测的启示**：AlphaFold2 等工具预测单体结构时可能无法捕捉 RBR 对折叠的远程影响；多聚体预测和 linker 效应建模是未来方向

## 07 方法总览

- **输入**：小鼠 FoxP3 截短构建体（FoxP3ΔN: 残基188-423；FoxP3ΔN': 204-276+305-417；FoxP3ΔN": 204-276+315-417）、IR-FKHM4g DNA（5'-AAATTTGTTTACTCGAGTAAACAAATTT-3'）
- **输出**：FoxP3ΔN-DNA 复合物晶体结构（3.1 Å 和 4.0 Å）、FoxP3 二聚化状态与功能关系模型
- **模块**：
  1. 蛋白表达与纯化（大肠杆菌/哺乳动物细胞）
  2. SEC-MALS 分析寡聚状态
  3. 晶体筛选与 X 射线衍射数据收集（APS NECAT-24-ID-E）
  4. 分子置换法结构解析（以 FoxN1 结构为模板）
  5. EMSA 和 pull-down 检测 DNA 结合
  6. 293T 细胞共转染/共沉淀检测 Runx1 互作
  7. 原代 CD4+ T 细胞逆转录病毒转导 + 流式检测 CD25/CTLA4
  8. T 细胞抑制实验
  9. 小鼠模型（CRISPR 敲入 R337Q）
- **训练**：不适用（非机器学习方法）
- **工具**：XDS、HKL2000、Phaser、COOT、PHENIX、REFMAC5、PyMOL
- **反馈回路**：结构 → 突变设计 → 生化验证 → 细胞功能验证 → 小鼠模型验证
- **假设**：RBR 对 forkhead 折叠的稳定作用是 FoxP3 功能的前提；head-to-head 二聚化是 FoxP3 的生理 DNA 结合模式

**文字流程**：纯化 FoxP3 截短体 → SEC-MALS 确认寡聚状态 → 与 IR-FKHM4g DNA 共结晶 → 收集衍射数据并解析结构 → 结构分析确定 head-to-head 二聚化模式 → 设计界面突变 → 体外 DNA 结合实验验证 → 细胞功能实验验证 → 小鼠模型验证 R337Q 致病机制

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| RBR linker | 稳定 forkhead 非交换折叠 | 缺失 RBR 导致疏水残基暴露，驱动 swap 二聚化 | 输入：RBR 序列；输出：forkhead 正确折叠 | Results 图 1B：FoxP3RBR-forkhead 为单体 vs FoxP3forkhead 为二聚体；图 2A 结构对比 | 移除后 forkhead 错误折叠为 swap 二聚体，DNA 结合特异性丧失（实测） |
| Head-to-head 二聚化界面 | 介导两个 forkhead 单体的功能二聚化 | 扩展 DNA 识别长度至约 18 bp，形成 Runx1 对接位点 | 输入：两个 forkhead 单体；输出：head-to-head 二聚体 | Results 图 1E：晶体结构显示 head-to-head 排列；图 3A：界面残基 | 界面突变（F331D, W348D）降低 IR-FKHM4g 结合和 Runx1 互作（实测） |
| RBR loop（残基321-336） | 介导 head-to-head 二聚化的疏水相互作用 | 提供二聚化驱动力和 Runx1 结合表面 | 输入：RBR loop 残基；输出：二聚化界面 | Results 图 3A：loop 残基参与界面；图 6A-D：Runx1 结合依赖 | 突变后二聚化受损，DNA 结合和 Runx1 招募降低（预期，部分实测） |
| Forkhead DBD | 序列特异性 DNA 识别 | 识别 forkhead 基序（FKHM） | 输入：DBD 序列；输出：DNA 结合 | Results 图 1C-D：IR-FKHM4g 偏好性 | 移除后完全丧失 DNA 结合（预期） |
| CC 二聚化结构域 | 介导 FoxP3 蛋白水平的二聚化 | 与 head-to-head 二聚化协同，稳定 DNA 结合 | 输入：CC 结构域；输出：蛋白二聚体 | Results 图 1B：FoxP3ΔN 为二聚体（通过 CC） | 移除后蛋白单体化，DNA 结合亲和力降低（预期） |

## 09 关键公式符号

**不适用** — 本文为实验结构生物学研究，未使用数学公式或计算模型。核心定量参数包括：

- 晶体衍射分辨率：3.1 Å（FoxP3ΔN"）和 4.0 Å（FoxP3ΔN'）
- SEC-MALS 分子量测定：用于判断寡聚状态
- EMSA 结合常数：未提供具体数值
- 统计检验：Student's t test 或 Mann-Whitney test，p < 0.05

## 10 实验设计与证据链

### 数据集/群体/规模
- 重组蛋白：FoxP3ΔN、FoxP3RBR-forkhead、FoxP3forkhead、FoxP1/2/4 对应构建体
- 突变体：F331D、W348D、R337Q、A372S、A372G、A372P、Y373V 等
- 细胞：293T（过表达）、原代 CD4+ T 细胞（功能实验）
- 小鼠：CRISPR 敲入 R337Q 突变小鼠
- 晶体：FoxP3ΔN'-DNA 和 FoxP3ΔN"-DNA 复合物
- ChIP-seq 数据：已发表的 FoxP3 ChIP-seq 数据集（Kitagawa et al., 2017; Samstein et al., 2012）

### 指标
- 寡聚状态（SEC-MALS）
- DNA 结合亲和力/特异性（EMSA、pull-down）
- 转录活性（CD25、CTLA4 表达）
- T 细胞抑制能力
- 蛋白热稳定性（热位移实验）

### 评测协议
- 体外：重组蛋白 + 合成 DNA 的生化实验
- 细胞：293T 过表达 + 原代 T 细胞转导
- 体内：R337Q 敲入小鼠表型分析

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| SEC-MALS 寡聚状态分析 | FoxP3forkhead 在 RBR 存在时为单体 | FoxP3forkhead vs FoxP3RBR-forkhead vs FoxP3ΔN | FoxP3forkhead 为二聚体；含 RBR 构建体为单体 | RBR 抑制 swap 二聚化 | 未直接证明 RBR 的分子机制 | Results 图 1B |
| 晶体结构解析 | FoxP3 的生理构象为非交换 head-to-head 二聚体 | FoxP3ΔN'-DNA 和 FoxP3ΔN"-DNA 复合物 | 非交换 winged-helix 折叠，head-to-head 二聚化 | 生理构象为非交换单体，DNA 结合时形成 head-to-head 二聚体 | 分辨率有限（3.1-4.0 Å），部分 loop 未解析 | Results 图 1E, 图 3A |
| EMSA DNA 结合 | FoxP3 偏好 IR-FKHM4g | IR-FKHM4g vs DR-FKHM vs sFKHM | 强偏好 IR-FKHM4g | Head-to-head 二聚化赋予 IR 特异性 | 未系统测试所有可能的 DNA 序列 | Results 图 1C-D |
| 突变体功能分析 | Head-to-head 二聚化对功能至关重要 | F331D、W348D 突变 vs WT | 突变体 DNA 结合和转录活性降低 | 二聚化界面残基对功能必要 | 未排除突变对蛋白折叠的间接影响 | Results 图 3B-D |
| R337Q 突变体分析 | IPEX 突变通过诱导 swap 二聚化致病 | R337Q vs WT vs R337Q/A372S | R337Q 诱导 swap 二聚化，功能受损；A372S 部分恢复 | R337Q 致病机制为折叠错误 | 未在人类患者细胞中验证 | Results 图 7G-M |
| R337Q 敲入小鼠 | R337Q 在体内导致 Treg 功能受损 | R337Q 小鼠 vs WT 同窝 | Treg 比例和功能部分受损，但无严重自身免疫 | R337Q 为亚效等位基因 | 未观察到完全 IPEX 样表型 | Results 图 7B-F |
| ChIP-seq 基序分析 | 体内 FoxP3 结合位点富集 IR 基序 | 已发表 ChIP-seq 数据重分析 | 未发现 IR-FKHM4g 的显著富集 | 体内结合可能依赖其他因素 | 分析限于已发表数据，可能遗漏亚型 | Results 图 5A-B |

## 11 结论正确解读

- **任务范围**：本文仅研究了 FoxP3 的 forkhead 结构域及其邻近 RBR linker 的折叠与 DNA 结合机制，未涉及 FoxP3 全长蛋白在染色质环境中的行为。
- **oracle/真值输入**：晶体结构解析使用了截短构建体（FoxP3ΔN' 和 FoxP3ΔN"），其中包含内部缺失突变（删除 RBR loop 部分残基）以促进结晶。这些构建体虽比分离 DBD 更接近生理状态，但仍非全长蛋白。
- **端到端状态**：从结构到功能的证据链完整，但部分环节（如 R337Q 在人类患者中的具体影响）未直接验证。
- **算力成本**：不适用（实验研究）。
- **历史数据依赖**：ChIP-seq 分析依赖已发表数据，未进行新的全基因组实验。
- **模型依赖**：不适用。
- **最难情形**：R337Q 敲入小鼠仅表现部分表型，说明体内存在补偿机制或其他调控层。
- **群体/领域边界**：结论基于小鼠 FoxP3 和体外重组蛋白，人类 FoxP3 的普适性需进一步验证。
- **不确定性**：3.1-4.0 Å 分辨率限制了精细相互作用分析；RBR loop 的柔性导致部分结构未解析。

**有边界的复述**：在包含 RBR linker 的截短构建体条件下，FoxP3 的 forkhead 结构域折叠为非交换单体，并在结合倒置重复 DNA 基序时形成 head-to-head 二聚体；RBR 缺失或特定突变可诱导 domain-swap 二聚化，损害 DNA 结合和 Treg 功能。该结论基于体外重组蛋白、细胞实验和小鼠模型，尚未在人类患者中直接验证。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 基因组直接靶点鉴定不足 | 基于 head-to-head 二聚化模型，无法确定基因组中哪些位点被 FoxP3 直接结合 | 需要进一步研究以理解 FoxP3 直接结合位点的完整谱系 | Discussion, Limitations |
| Runx1 招募机制细节不清 | 结构显示 head-to-head 二聚化形成疏水表面可能对接 Runx1，但缺乏高分辨率共结构 | 需要更详细的结构模型说明 head-to-head 二聚化如何促进 Runx1 招募 | Discussion, Limitations |
| 体内结合位点与体外偏好不一致 | ChIP-seq 分析未发现 IR-FKHM4g 的显著富集 | 需要将体外 DNA 结合偏好与体内 ChIP-seq/Cut&Run 数据更系统地关联 | Results 图 5A-B, Discussion |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 晶体结构使用了含内部缺失的构建体（ΔN' 和 ΔN"） | 缺失 RBR loop 残基可能影响二聚化界面的真实构象 | 结构结论可能不完全代表野生型蛋白的生理构象 | 尝试全长或更少缺失的构建体进行冷冻电镜或交联质谱验证 | Methods, 晶体构建体描述 |
| ChIP-seq 未发现 IR-FKHM4g 富集，与体外偏好矛盾 | 体内 FoxP3 结合可能主要依赖协同因子或染色质状态，而非固有 DNA 偏好 | 挑战了 head-to-head 二聚化作为体内 DNA 结合主要决定因素的结论 | 使用更严格的体内结合位点定义，或在敲入突变小鼠中进行 ChIP-seq | Results 图 5A-B |
| R337Q 小鼠表型远轻于完全 FoxP3 缺陷 | 可能存在其他 FoxP3 二聚化模式或补偿机制 | 影响对 IPEX 突变致病机制的理解 | 在 R337Q 小鼠中检测 swap 二聚体的体内存在及功能 | Results 图 7B-F |
| 分辨率 3.1-4.0 Å 限制了精细相互作用分析 | 关键残基的侧链构象可能不确定 | 影响对突变效应的精确解释 | 尝试更高分辨率晶体或 cryo-EM 验证 | Table S1 |
| 未检测 FoxP3 在染色质环境中的二聚化状态 | 体外 DNA 结合实验可能无法反映染色质环境中的行为 | 影响对 FoxP3 在基因组中实际结合模式的推断 | 使用单分子成像或染色质免疫沉淀结合交联分析 | 未提供 |

## 14 学到什么

**Agent 提炼的知识候选**

1. **构建体设计对 TF-DNA 结构研究的关键影响**：本文证明包含 linker 的构建体与分离 DBD 得出截然不同的结构结论。迁移到本课题：在 AI 结构预测（如 AlphaFold2）和 MD 模拟中，应包含 linker/侧翼序列，而非仅预测 DBD 结构域；预测结果需用包含完整上下文的实验验证。

2. **二聚化状态转换作为 TF 功能分化的机制**：同一 DBD 可通过单体/二聚体状态转换实现不同的 DNA 结合特异性和辅因子招募。迁移到本课题：在预测 TF-DNA 结合时，应考虑 TF 的寡聚状态；二聚化界面的突变可能通过改变寡聚状态间接影响 DNA 结合，而非直接改变 DNA 接触残基。

3. **"模糊"疏水相互作用介导的蛋白-蛋白互作**：head-to-head 二聚化界面由疏水残基介导，具有构象柔性。迁移到本课题：在 MD 模拟中，这类"模糊"界面可能需要增强采样方法（如副本交换）才能充分采样构象空间；在 AI 模型中，预测这类界面的结合亲和力可能比刚性界面更具挑战性。

4. **体外 DNA 偏好与体内结合位点的不一致**：FoxP3 体外偏好 IR-FKHM4g，但 ChIP-seq 未发现该基序富集。迁移到本课题：AI 模型基于体外数据（如 SELEX、PBM）训练的 DNA 结合特异性预测可能无法直接推广到体内；需要整合染色质可及性、协同因子等信息。

5. **疾病突变可作为构象状态的探针**：R337Q 通过诱导 swap 二聚化致病，说明表面突变可通过改变折叠/寡聚状态影响功能。迁移到本课题：在预测 TF 突变致病性时，不能仅关注 DNA 接触残基；需考虑突变对蛋白折叠和寡聚状态的影响，这可能需要结合结构预测和 MD 模拟。

6. **RBR 作为"分子伴侣"的远程调控**：RBR 通过远程相互作用影响 forkhead 折叠。迁移到本课题：在预测 TF 结构时，需考虑结构域间相互作用对 DBD 折叠的影响；AlphaFold2 的完整蛋白预测可能比单独 DBD 预测更准确。

## 15 与已有知识连接

1. **Bandukwala et al. (2011)**：此前报道 FoxP3 forkhead 形成 domain-swap 二聚体。本文直接挑战此结论，证明 domain-swap 是 RBR 缺失导致的体外假象。连接：本课题中引用 FoxP3 结构时需注意构建体差异。

2. **Stroud et al. (2006); Chu et al. (2011)**：FoxP2 和 FoxP1 的 domain-swap 二聚体结构。本文证明 FoxP1/2/4 在含 RBR 时也为非交换单体，但 head-to-head 二聚化仅 FoxP3 特有。连接：FoxP 家族成员间功能差异可能源于二聚化能力差异。

3. **Ono et al. (2007)**：RBR 是 Runx1 结合区域。本文进一步证明 RBR 同时参与 forkhead 折叠稳定和 Runx1 招募，说明该区域的多功能性。

4. **Samstein et al. (2012); Kitagawa et al. (2017)**：FoxP3 ChIP-seq 数据。本文重分析未发现 IR-FKHM4g 富集，提示体内结合机制更复杂。

5. **AlphaFold2 (Jumper et al., 2021)**：本文引用 AF2 预测支持 FoxP3 非交换折叠。连接：AF2 预测可作为结构生物学假设生成的工具，但需实验验证。

6. **IPEX 综合征突变数据库**：本文分析多个 IPEX 突变（R337Q、Y373V 等）的折叠效应。连接：本课题中预测 TF 突变致病性时，可参考本文建立的"折叠错误"机制。

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：基于 AlphaFold2 多聚体预测的 TF 二聚化状态分类器
   - **来源局限/观察**：本文证明 FoxP3 的 head-to-head 二聚化是功能关键，但 AF2 对多聚体界面的预测准确性有限；现有工具未系统评估 TF 二聚化状态与 DNA 结合特异性的关系
   - **核心假设**：TF 的 DNA 结合特异性可通过其寡聚化状态（单体/同源二聚体/异源二聚体）和二聚化几何（head-to-head vs head-to-tail）预测
   - **初步方法**：收集已知 TF 二聚化结构（含 FoxP3 等），用 AF2-multimer 预测二聚化界面，与实验结构对比；训练分类器区分 head-to-head 和 domain-swap 二聚化模式；结合 DNA 结合基序数据建立「二聚化模式-结合特异性」映射
   - **验证方式**：对未知二聚化状态的 TF 进行预测，用 SEC-MALS/交联质谱实验验证
   - **创新状态**：unverified

2. **候选名称**：TF-DNA 结合特异性的「上下文感知」预测模型
   - **来源局限/观察**：本文发现 FoxP3 体外偏好 IR-FKHM4g 但体内 ChIP-seq 无该基序富集，提示现有基于体外数据的 DNA 结合预测模型存在系统性偏差
   - **核心假设**：TF 的体内 DNA 结合位点选择受蛋白上下文（linker、侧翼结构域）和染色质状态调控，仅用 DBD 序列无法准确预测
   - **初步方法**：整合 TF 全长序列、结构域组成、linker 长度/序列、染色质可及性数据，训练多模态深度学习模型预测体内结合位点；以 FoxP3 为测试案例，比较 DBD-only 与 full-length 模型的预测差异
   - **验证方式**：在 R337Q 突变小鼠中进行 ChIP-seq，检验模型对突变效应的预测
   - **创新状态**：unverified

3. **候选名称**：MD 模拟研究 FoxP3 二聚化状态转换的自由能景观
   - **来源局限/观察**：本文提出 FoxP3 可在非交换单体和 domain-swap 二聚体之间转换，但未提供动力学证据；R337Q 突变如何促进 swap 二聚化的分子机制不明
   - **核心假设**：R337Q 通过破坏 R337-Y373 的相互作用，降低非交换折叠的动力学稳定性，从而增加 swap 二聚化的概率
   - **初步方法**：对 FoxP3RBR-forkhead（WT 和 R337Q）进行增强采样 MD 模拟（如 metadynamics 或 replica exchange），计算非交换单体与 swap 二聚体之间的自由能差；分析 R337 和 Y373 在折叠转变中的关键作用
   - **验证方式**：模拟预测的突变效应与实验热稳定性数据对比；设计新的突变验证模拟预测
   - **创新状态**：unverified

4. **候选名称**：基于结构的 TF 二聚化界面突变致病性预测工具
   - **来源局限/观察**：本文发现多个 IPEX 突变通过影响折叠/二聚化而非直接 DNA 接触致病，现有突变致病性预测工具（如 PolyPhen、SIFT）未考虑二聚化状态
   - **核心假设**：位于二聚化界面或折叠关键位点的突变可通过改变寡聚状态致病，这类突变可通过结构分析识别
   - **初步方法**：以 FoxP3 为训练集，标注已知 IPEX 突变的结构效应（折叠破坏 vs 界面破坏 vs DNA 接触破坏）；训练图神经网络（GNN）基于结构预测突变的结构效应类别；扩展到其他二聚化 TF
   - **验证方式**：对未知致病性突变进行预测，用实验验证
   - **创新状态**：unverified

5. **候选名称**：TF 二聚化状态与辅因子招募的共进化分析
   - **来源局限/观察**：本文证明 FoxP3 的 head-to-head 二聚化同时促进 DNA 结合和 Runx1 招募，提示二聚化界面与辅因子结合位点可能共进化
   - **核心假设**：在 forkhead 家族中，二聚化能力与辅因子结合位点的共进化可预测 TF 的功能分化
   - **初步方法**：对 forkhead 家族进行系统发育分析，比较二聚化界面残基和辅因子结合位点的共进化模式；结合 AlphaFold2 预测的结构进行验证
   - **验证方式**：对预测的共进化残基进行突变实验，检测对二聚化和辅因子结合的影响
   - **创新状态**：unverified