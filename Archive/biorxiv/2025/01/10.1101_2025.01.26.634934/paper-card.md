## 01 基本信息

- **标题**：Two CTCF motifs impede cohesin-mediated DNA loop extrusion
- **作者与单位**：Barth R; Janissen R; Muras L; van der Torre J; Litos G; van der Sluis E; van der Graaf A; Davidson IF; Peters J; Dekker C（单位未在摘要中提供，推测为 Delft University of Technology 等，具体未提供）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025（预印本日期 2025-01-26）
- **论文类型**：预印本（研究论文）
- **领域**：分子生物学 / 单分子生物物理 / 基因组组织
- **关键词**：cohesin、CTCF、DNA loop extrusion、YDF motif、KTYQR motif、STAG1、单分子实验
- **DOI/arXiv 号**：10.1101/2025.01.26.634934
- **代码**：未提供（文中提及开发了 step-finding 算法，但未给出代码仓库）
- **数据**：未提供（文中提及数据可向通讯作者索取）
- **阅读日期**：2025-01-27
- **在课题方向中的位置**：本文聚焦转录因子 CTCF 通过其 NTR 上的两个基序（YDF 和 KTYQR）调控 cohesin 介导的 DNA 环挤压（loop extrusion, LE）的分子机制。属于「蛋白质-DNA 互作（TF–DNA 结合机制）× 物理模拟/单分子实验」方向，核心机制是 TF 通过变构调控而非直接阻断来影响 DNA 转位酶活性。对 AI 方法（AlphaFold-Multimer 预测结合位点）与单分子实验（磁镊、荧光）的结合具有示范意义。

---

## 02 一句话总结

本文通过单分子磁镊和荧光实验，发现 CTCF 的 N 端区域（NTR）通过两个独立基序——YDF（增强 STAG1 的 DNA 结合亲和力，使 cohesin 偏向单向挤压）和 KTYQR（抑制 cohesin 的 ATPase 活性和步进式 LE）——协同阻断 cohesin 介导的 DNA 环挤压，且 AlphaFold-Multimer 预测支持 KTYQR 与 STAG1 的直接结合。

---

## 03 研究问题

- **具体问题**：CTCF 的 NTR 如何通过分子机制阻断 cohesin 介导的 DNA 环挤压？具体是哪些氨基酸基序起作用，它们各自通过什么机制发挥作用？
- **为什么重要**：CTCF 是 TAD 边界的主要组织者，其阻断 cohesin 的 LE 是基因组三维结构形成的关键步骤。理解这一机制对揭示基因调控、疾病（如 cohesinopathy、癌症）的分子基础至关重要。
- **现有方法为何不足**：此前已知 YDF 基序与 cohesin 的 CES 表面结合，但 YDF 突变并不能完全消除 CTCF 的阻断功能，提示存在其他基序。且「CTCF 如何物理上阻断 cohesin 的 LE」被称为「mechanistic mystery」。
- **精确的 Can 问题**：Can the CTCF NTR be dissected into distinct amino acid motifs that independently and synergistically impede cohesin-mediated DNA loop extrusion via separable molecular mechanisms?

---

## 04 背景与发展脉络

*注：此脉络基于本文引用与讨论，结合外部知识，标记为「经外部核验」与「仅本文框架」混合。*

1. **阶段一：cohesin 与 LE 的发现（~2010s）**
   - 代表方法：单分子实验（磁镊、光镊）直接观察 LE（Ganji et al., 2018; Davidson et al., 2019）
   - 发现 cohesin 能不对称地挤压 DNA 环，且能切换方向
   - 局限：LE 的调控机制尚不清楚

2. **阶段二：CTCF 作为 LE 屏障（~2015-2020）**
   - 代表方法：Hi-C、ChIP-seq 结合单分子实验
   - 发现 CTCF 在 TAD 边界富集，且其方向性决定边界位置
   - 单分子实验证实 cohesin 从 NTR 侧遇到 CTCF 时停止（Davidson et al., 2023）
   - 局限：分子机制不明，YDF 突变不能完全消除阻断

3. **阶段三：CTCF 基序的遗传学解析（~2020）**
   - Nora et al. (2020) 通过 CRISPR 筛选发现 NTR 1-89 区域（含 KTYQR）和 YDF 基序均影响 TAD 绝缘
   - 局限：体内实验无法区分直接 vs 间接效应

4. **阶段四：本文——单分子水平解析双基序机制（2025）**
   - 结合磁镊、单分子荧光、FCS、AlphaFold-Multimer
   - 首次在单分子水平区分 YDF 和 KTYQR 的独立与协同功能
   - 位置：填补了「CTCF 如何分子层面阻断 cohesin」的关键空白

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| YDF 突变不能完全消除 CTCF 阻断 | 体内 YDF 突变后 TAD 边界仍部分保留 | 存在 YDF 之外的额外基序参与阻断 | 摘要及 Results 图 2D：NTR<sup>ADA</sup> 仍降低 LE 频率 |
| CTCF 阻断 cohesin 的分子机制不明 | 被称为「mechanistic mystery」 | 缺乏单分子水平的高分辨率解析 | 引言部分引用文献 40 |
| YDF 基序如何导致单向挤压未知 | 方向性切换减少，但机制不清 | 可能通过增强 STAG1 的 DNA 结合亲和力，阻止 DNA 链交换 | Results 图 2H：FCS 显示 YDF 增强 STAG1-DNA 结合 |
| KTYQR 基序的功能完全未知 | 此前仅知其影响 TAD 绝缘 | 可能通过结合 STAG1 抑制 ATPase 活性 | Results 图 3C：KTYQR 降低 ATPase 活性约 60% |
| 两个基序的协同关系不清 | 单独效应弱于全长 NTR | 两个基序通过不同机制协同作用 | Results 图 3J,K：联合添加 YDF+KTYQR 效果强于单独 |

---

## 06 核心思想

### 1) 表面方法
将 CTCF 的 NTR 分解为多个肽段和突变体，在单分子磁镊系统中观察它们对 cohesin 介导的 LE 的影响，结合 FCS 测量 DNA 结合亲和力，并用 AlphaFold-Multimer 预测结合位点。

### 2) 核心洞察
CTCF 阻断 cohesin 并非单一机制，而是通过两个独立基序的协同作用：
- **YDF 基序**：增强 STAG1 的 DNA 结合亲和力 → 阻止 DNA 链交换 → 使 cohesin 变为单向挤压器（不切换方向）
- **KTYQR 基序**：直接抑制 cohesin 的 ATPase 活性和步进式 LE（减少连续步数）

两者通过不同靶点（STAG1 的 CES 表面 vs STAG1 的 N 端保守表面）协同作用，共同实现高效阻断。

### 3) 可能的普适教训 [Analysis]
- **TF 对分子马达的调控可以是变构的而非物理阻挡**：CTCF 并非简单地「堵住」cohesin 的 DNA 通道，而是通过改变亚基的 DNA 亲和力来改变马达的动力学模式。这对理解其他 TF-转位酶互作有启发。
- **单分子实验可以区分「步进频率」和「方向性」两个独立参数**：传统 bulk 实验无法区分这两种效应，而单分子磁镊可以。
- **AlphaFold-Multimer 可用于生成可实验检验的结合位点假说**：本文展示了 AF 预测 → FCS 验证的闭环流程。

---

## 07 方法总览

- **输入**：纯化的 human cohesin（STAG1 亚型）、NIPBL-Mau2、CTCF NTR 肽段（野生型及突变体）、λ-DNA
- **输出**：LE 动力学参数（步进频率、方向切换频率、连续步数分布）、ATPase 活性、DNA 结合亲和力
- **主要模块**：
  1. **单分子磁镊 LE 实验**：表面固定 λ-DNA，加入 cohesin + NIPBL-Mau2，在有无 CTCF 肽段的缓冲液中观察 DNA 长度变化（图 1F-G）
  2. **单分子荧光实验**：双色标记 NIPBL-ΔN，观察其与 cohesin 的结合/交换动力学（图 2F-G）
  3. **FCS（荧光相关光谱）**：测量荧光标记 DNA 的扩散常数，推断 STAG1-DNA 结合（图 2H）
  4. **ATPase 活性测定**：bulk 生化实验（图 2C）
  5. **AlphaFold-Multimer 预测**：预测 CTCF NTR 片段与 cohesin 亚基的结合界面（图 4A）
  6. **3D 聚合物模拟**：模拟 stalled cohesin 能否解释 Hi-C 图谱（图 S4）
- **训练**：不适用（无监督学习/深度学习训练）
- **反馈回路**：AF 预测 → FCS 验证 → 修正结合模型
- **文字流程**：先验证全长 NTR 抑制 LE → 分解为 YDF 和 KTYQR 肽段分别测试 → 确认各自独立效应 → FCS 揭示 YDF 增强 STAG1-DNA 结合 → AF 预测 KTYQR-STAG1 结合位点 → FCS 验证 → 联合添加两肽段测试协同效应 → 聚合物模拟验证生物学意义

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 单分子磁镊 LE 实验 | 实时监测 cohesin 的 DNA 环挤压动力学 | 提供单分子分辨率，区分步进、方向切换、暂停等行为 | 输入：cohesin+NIPBL+CTCF 肽段；输出：DNA 长度-时间轨迹 | 图 1F-I；图 2I-L；图 3F-L | 无法区分步进频率与方向性的独立变化（预期影响） |
| 单分子荧光（双色 NIPBL） | 监测 NIPBL 亚基的交换与 cohesin 结合状态 | 检验 YDF 是否通过影响 NIPBL 交换来改变方向性 | 输入：双色标记 NIPBL-ΔN；输出：共定位/交换事件统计 | 图 2F-G | 无法排除 NIPBL 交换机制（实测排除：交换率不变） |
| FCS | 测量 STAG1 与 DNA 的结合亲和力变化 | 直接验证 YDF 增强 DNA 结合的假说 | 输入：STAG1+Scc1+肽段+荧光 DNA；输出：扩散常数/结合分数 | 图 2H | 无法定量结合亲和力变化（预期影响） |
| ATPase 活性测定 | 测量 cohesin 的 ATP 水解速率 | 检验 KTYQR 是否通过抑制 ATPase 来阻断 LE | 输入：cohesin+肽段+ATP；输出：ATP 消耗速率 | 图 3C | 无法区分 ATP 结合 vs 水解步骤（预期影响） |
| AlphaFold-Multimer | 预测 CTCF NTR 与 cohesin 亚基的结合界面 | 生成可检验的结合位点假说 | 输入：CTCF NTR 序列 + cohesin 亚基序列；输出：预测复合物结构 | 图 4A；图 S6 | 无法预测结合亲和力（预期影响） |
| 3D 聚合物模拟 | 模拟 stalled cohesin 的 Hi-C 模式 | 验证单分子观察的生物学相关性 | 输入：stalling 参数；输出：模拟 Hi-C 矩阵 | 图 S4 | 无法模拟动态 stalling 过程（预期影响） |

---

## 09 关键公式符号

本文为实验生物学论文，无核心数学公式。以下为可提取的定量关系：

1. **LE 步进速率**：$v = \frac{\Delta L}{\Delta t}$，其中 $\Delta L$ 为 DNA 长度变化，$\Delta t$ 为时间间隔。用于量化 NTR 对 LE 速率的影响（图 1H）。

2. **方向切换频率**：$f_{switch} = \frac{N_{switch}}{T_{total}}$，其中 $N_{switch}$ 为方向切换次数，$T_{total}$ 为总观察时间。用于量化 YDF 对方向性的影响（图 2E）。

3. **FCS 结合分数**：$F_{bound} = \frac{D_{free} - D_{obs}}{D_{free} - D_{bound}}$，其中 $D$ 为扩散常数。用于量化 YDF 肽段增强 STAG1-DNA 结合的程度（图 2H）。

4. **ATPase 活性抑制率**：$I = 1 - \frac{v_{ATP,peptide}}{v_{ATP,control}}$，用于量化 KTYQR 对 ATP 水解的抑制（图 3C）。

*注：以上公式为本文定量分析中隐含的关系，原文未以公式形式给出。*

---

## 10 实验设计与证据链

### 数据集/群体
- 单分子磁镊：单个 λ-DNA 分子上的 cohesin LE 事件（n 未在摘要中给出）
- 单分子荧光：双色标记 NIPBL-ΔN 的交换事件
- FCS：荧光标记 DNA 与 STAG1 的结合滴定
- ATPase：bulk 溶液酶活测定
- AlphaFold-Multimer：25 次预测采样

### 指标
- LE 步进频率（steps/min）
- 方向切换频率
- 连续步数分布
- ATPase 活性（μmol ATP/min/mg）
- DNA 结合分数（FCS）

### 基线/对照
- 无肽段缓冲液（阴性对照）
- ADA 突变肽段（YDF 失活对照）
- CTR 肽段（阴性对照）
- 酵母 condensin（物种特异性对照）

### 预算/仪器
- 磁镊（自制或商用，未具体说明）
- 全内反射荧光显微镜（TIRF）
- FCS 设备
- AlphaFold-Multimer（计算资源：DelftBlue 超算）

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 全长 NTR 对 LE 的影响 | NTR 抑制 cohesin LE | 有/无 2μM NTR | 活性相频率降低 ~3 倍 | NTR 抑制 LE 起始 | 不能区分步进 vs 起始 | 图 1D |
| NTR 对方向性的影响 | NTR 使 cohesin 单向化 | 有/无 NTR | 双向挤压从 35% 降至 12% | NTR 抑制方向切换 | 不能确定机制 | 图 1E |
| YDF 肽段对 LE 的影响 | YDF 是 NTR 功能的关键基序 | YDF vs ADA 肽段 | YDF 降低活性，ADA 无效果 | YDF 介导抑制 | 不能排除其他基序 | 图 2D |
| YDF 对方向性的影响 | YDF 单独足以驱动单向化 | YDF vs ADA | YDF 增加单向挤压 | YDF 控制方向性 | 不能确定是否通过 STAG1 | 图 2E |
| YDF 对 NIPBL 交换的影响 | YDF 通过阻止 NIPBL 交换来抑制方向切换 | 有/无 YDF 肽段 | NIPBL 交换率不变 | 排除 NIPBL 交换机制 | — | 图 2F-G |
| FCS：YDF 增强 STAG1-DNA 结合 | YDF 通过增强 STAG1-DNA 亲和力阻止链交换 | YDF vs ADA 肽段 | YDF 增加 DNA 结合分数 | YDF 增强 STAG1-DNA 结合 | 不能定量亲和力变化 | 图 2H |
| KTYQR 肽段对 LE 的影响 | KTYQR 是独立抑制基序 | KTYQR vs 对照肽段 | 活性降低 ~50% | KTYQR 独立抑制 LE | 不能确定是否通过 ATPase | 图 3D |
| KTYQR 对 ATPase 的影响 | KTYQR 通过抑制 ATPase 阻断 LE | 有/无 KTYQR | ATPase 降低 ~60% | KTYQR 抑制 ATP 水解 | 不能区分结合 vs 水解步骤 | 图 3C |
| YDF+KTYQR 联合效应 | 两基序协同抑制 LE | 联合 vs 单独 | 联合效果强于单独但弱于加和 | 协同但非完全加和 | 不能排除其他 NTR 基序 | 图 3J-K |
| AlphaFold 预测 KTYQR-STAG1 结合 | KTYQR 直接结合 STAG1 | AF 预测 vs 随机 | 16/25 或 25/25 预测结合 | KTYQR 可能结合 STAG1 | AF 预测需实验验证 | 图 4A |
| FCS 验证 KTYQR-STAG1 结合 | KTYQR 确实结合 STAG1 | 有/无 STAG1 | 结合分数随 STAG1 增加 | KTYQR 直接结合 STAG1 | 不能确定结合位点 | 图 4B |
| 聚合物模拟 | stalled cohesin 解释 Hi-C | 模拟 vs 实验 Hi-C | 模拟重现 TAD 边界 | stalling 模型合理 | 模拟参数可能过度简化 | 图 S4 |

---

## 11 结论正确解读

- **任务范围**：本文仅研究 cohesin（STAG1 亚型）在体外（纯化蛋白 + λ-DNA）的 LE 行为，不涉及体内染色质环境、其他 cohesin 亚型（STAG2）或翻译后修饰的影响。
- **oracle/真值输入**：无监督学习中的 oracle 概念不适用；实验中的「真值」为单分子轨迹中 DNA 长度变化的物理测量。
- **端到端状态**：非端到端。实验分步进行：先观察表型（LE 抑制），再分子机制（STAG1 结合），最后结构预测（AF）。
- **算力成本**：AlphaFold-Multimer 预测需要 GPU 资源（DelftBlue 超算），但具体成本未报告。
- **历史数据依赖**：不依赖历史数据集；所有实验为全新采集。
- **模型依赖**：AlphaFold-Multimer 预测结果依赖训练数据，作者用 FCS 实验验证了 KTYQR-STAG1 结合，但未验证 AF 预测的具体结合界面。
- **最难情形**：单分子实验中，cohesin 的 LE 活性本身具有高度随机性（stochastic switching），需要大量重复才能获得统计显著性。
- **群体/领域边界**：结论仅适用于 human cohesin-STAG1 与 CTCF NTR 的互作；酵母 condensin 对照实验显示物种特异性。
- **不确定性**：作者未报告 FCS 结合亲和力的定量 Kd 值；AF 预测的 KTYQR-STAG1 结合界面未通过突变验证。
- **有边界的复述**：在体外单分子条件下，CTCF NTR 通过 YDF 基序增强 STAG1 的 DNA 结合亲和力（使 cohesin 单向化）和 KTYQR 基序抑制 ATPase 活性（减少步进），两者协同阻断 cohesin 的 LE；AlphaFold 预测支持 KTYQR 直接结合 STAG1 的 N 端保守表面，但该预测的原子级细节尚未实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 体外实验条件 | 使用纯化蛋白和 λ-DNA，缺乏染色质环境 | 未明确提及 | 摘要及方法部分（隐含） |
| AF 预测未定量验证 | AlphaFold 预测 KTYQR-STAG1 结合，但未报告结合亲和力 | 未来研究可捕捉 LE 循环中的构象变化时序 | 结论部分 |
| 未研究 STAG2 亚型 | 实验仅使用 STAG1 亚型 | 未明确提及 | 方法部分（隐含） |
| 未研究体内效应 | 未在细胞中验证双基序的协同作用 | 未明确提及 | 全文（隐含） |
| 肽段 vs 全长蛋白 | 使用短肽段可能无法完全模拟全长 NTR 的构象效应 | 未明确提及 | 方法部分（隐含） |

*注：作者在摘要和结论中未系统列出局限，以上为从文中可推断的约束。*

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 肽段浓度远高于生理浓度 | 2 μM 肽段可能产生非特异性结合 | 可能高估了基序的生理相关性 | 剂量-反应曲线，计算生理浓度下的效应 | 方法部分（浓度未在摘要中给出） |
| FCS 实验未报告 Kd 值 | 仅报告「结合分数增加」是定性结论 | 无法比较 YDF 与 KTYQR 的相对亲和力 | 报告定量 Kd 和 Hill 系数 | 图 2H 描述 |
| AF 预测的 KTYQR 结合位点未突变验证 | AF 预测可能为假阳性 | 若结合位点错误，机制模型需修正 | 对预测界面进行点突变后重复 FCS | 图 4A 描述 |
| 未测试 STAG2 亚型 | STAG2 是体细胞主要亚型 | 结论可能不适用于 STAG2-cohesin | 重复实验使用 STAG2 版本 | 方法部分 |
| 聚合物模拟参数可能过度简化 | 模拟中「stalled」参数可能不反映真实 stalling 动力学 | 模拟结论可能过度乐观 | 使用实验测得的 stalling 效率作为参数 | 图 S4 描述 |
| 未报告单分子实验的 n 数和统计检验 | 无法评估效应量的可靠性 | 影响结论的稳健性 | 补充效应量和置信区间 | 方法部分（未在摘要中给出） |
| 「协同」结论基于肽段联合实验 | 联合效应弱于加和，可能只是部分重叠机制 | 「协同」可能被过度解读 | 使用全长 NTR 突变体验证 | 图 3J-K 描述 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **TF 对分子马达的调控可以是「变构」而非「物理阻挡」**：CTCF 并非堵住 cohesin 的 DNA 通道，而是通过增强 STAG1 的 DNA 结合亲和力来改变马达的动力学模式（单向化）。→ 迁移：在 TF-DNA 互作研究中，考虑 TF 是否通过改变辅因子（如 cohesin 亚基）的构象来间接调控 DNA 转位，而非直接竞争结合位点。

2. **单分子实验可解耦「步进频率」和「方向切换」两个独立参数**：传统 bulk 实验（如 Hi-C、ChIP）无法区分这两种效应。→ 迁移：在设计 TF 对 DNA 马达调控的实验时，优先考虑单分子方法（磁镊、光镊、TIRF）以获得机制级分辨率。

3. **AlphaFold-Multimer 可作为「假设生成器」而非「结论提供者」**：本文用 AF 预测 KTYQR-STAG1 结合，然后用 FCS 实验验证。→ 迁移：在蛋白质-DNA 互作研究中，AF 预测的界面应始终通过突变 + 结合实验（ITC、FCS、EMSA）验证。

4. **「基序分解」策略**：将全长 NTR 分解为短肽段（YDF 肽、KTYQR 肽）逐一测试，再联合测试。→ 迁移：研究 TF 的多基序功能时，使用短肽段 + 点突变体组合，可区分各基序的独立与协同贡献。

5. **聚合物模拟作为生物学解释的桥梁**：用 3D 聚合物模拟将单分子观察（stalled cohesin）与群体水平数据（Hi-C）连接。→ 迁移：在 AI/物理模拟课题中，将单分子参数输入聚合物模型，可验证机制在染色质尺度上的合理性。

6. **CES 表面作为药物/突变靶点的概念**：YDF 结合 CES 表面，KTYQR 结合 CES 附近的保守表面，两个表面可被独立靶向。→ 迁移：在设计干扰 TF-cohesin 互作的分子（如肽段抑制剂）时，可同时靶向多个弱相互作用表面以实现协同抑制。

---

## 15 与已有知识连接

- **Davidson et al., 2023 (Nature)**：此前单分子实验显示 cohesin 从 CTCF NTR 侧遇到时停止。本文在此基础上进一步分解了 NTR 的分子机制。→ 连接：本文是 Davidson 2023 的机制深化。
- **Nora et al., 2020 (Cell)**：CRISPR 筛选发现 NTR 1-89 和 YDF 基序影响 TAD 绝缘。本文在体外单分子水平验证并区分了这两个基序的功能。→ 连接：本文为 Nora 2020 的体内观察提供了分子机制解释。
- **Ganji et al., 2018 (Science)**：首次直接观察 cohesin 的 LE。本文使用类似磁镊平台，但加入了 CTCF 肽段调控。→ 连接：方法学继承。
- **Li et al., 2020 (Nature Genetics)**：CTCF 的 CES 结合界面结构解析。本文的 YDF 结果与此一致。→ 连接：结构基础与功能验证互补。
- **AlphaFold-Multimer (Evans et al., 2022)**：本文使用 AF 预测蛋白-蛋白互作界面。→ 连接：AI 结构预测在机制研究中的应用案例。
- **Higashi et al., 2020 (Mol Cell)**：cohesin 的 ATPase 循环与 LE 步进的关系。本文的 KTYQR 抑制 ATPase 与此相关。→ 连接：ATPase 抑制是阻断 LE 的通用策略。

---

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：基于 AF 预测的 CTCF NTR-cohesin 界面突变体库的功能筛选
   - **来源局限/观察**：本文 AF 预测了 KTYQR-STAG1 结合界面，但未做突变验证
   - **核心假设**：KTYQR 与 STAG1 的 N 端保守表面结合，该界面的点突变将消除 KTYQR 的抑制效应
   - **增量**：将 AF 预测从「计算假说」升级为「实验验证的相互作用模型」
   - **初步方法**：对 STAG1 的预测界面残基进行丙氨酸扫描，用 FCS 和单分子磁镊测试突变体的 LE 抑制能力
   - **验证方式**：突变体应丧失 KTYQR 肽段的结合（FCS）和 LE 抑制（磁镊）效应
   - **创新状态**：unverified

2. **候选名称**：TF 变构调控 DNA 转位酶的通用模型——以 CTCF-cohesin 为范例的 AI 辅助筛选
   - **来源局限/观察**：本文揭示 TF 可通过变构（增强亚基 DNA 亲和力）而非物理阻挡来调控 DNA 马达
   - **核心假设**：其他含 YDF 样基序的 TF 也可能通过类似机制调控 cohesin 或其他 SMC 复合物
   - **增量**：将 CTCF 的机制推广到 TF 家族层面
   - **初步方法**：用序列比对和 AF 筛选含 YDF 或 KTYQR 样基序的 TF，测试其对 cohesin LE 的影响
   - **验证方式**：单分子磁镊筛选 + 体内 Hi-C 验证
   - **创新状态**：unverified

3. **候选名称**：cohesin 单向化对 TAD 边界形成的定量模型
   - **来源局限/观察**：本文发现 YDF 使 cohesin 单向化，但未定量模拟这一行为对 TAD 结构的影响
   - **核心假设**：单向化（而非完全停止）足以解释 TAD 边界的形成
   - **增量**：将单分子参数（单向化概率、步进速率）输入聚合物模拟，定量预测 Hi-C 模式
   - **初步方法**：基于本文图 S4 的模拟框架，加入单向化参数扫描
   - **验证方式**：模拟 Hi-C 与实验 Hi-C 的定量比较（如 insulation score）
   - **创新状态**：partially checked（本文已有初步模拟，但未做参数扫描）

4. **候选名称**：深度学习预测 TF 基序对 SMC 马达的调控效应
   - **来源局限/观察**：本文实验通量有限，仅测试了少数肽段
   - **核心假设**：TF 序列特征（基序组成、电荷分布、疏水性）可预测其对 SMC 马达的调控模式
   - **增量**：建立序列→功能预测模型，加速 TF-cohesin 互作的功能注释
   - **初步方法**：以本文数据为训练集，结合已有文献数据，训练 CNN/Transformer 模型预测肽段对 LE 的抑制效果
   - **验证方式**：留一法交叉验证 + 新肽段的实验验证
   - **创新状态**：unverified

5. **候选名称**：STAG1 DNA 结合亲和力作为 cohesin 方向切换的分子开关——单分子 FRET 验证
   - **来源局限/观察**：本文提出 YDF 增强 STAG1-DNA 结合从而阻止链交换，但未直接观察链交换过程
   - **核心假设**：YDF 结合 CES 后诱导 STAG1 构象变化，增强其 DNA 结合，从而阻止 DNA 链从 extruding 侧切换到 anchoring 侧
   - **增量**：直接观察链交换的分子过程
   - **初步方法**：单分子 FRET 标记 STAG1 和 DNA，在有无 YDF 肽段条件下监测链交换动力学
   - **验证方式**：FRET 效率变化应与 YDF 浓度相关，且 ADA 突变应无效应
   - **创新状态**：unverified