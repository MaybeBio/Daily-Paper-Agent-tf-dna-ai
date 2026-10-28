## 01 基本信息
- **标题**：MDNA: a software module for DNA structure generation and analysis
- **作者与单位**：van Heesch, Thor; Skoruppa, Enrico; Bolhuis, Peter G; Schiessel, Helmut; Vreede, Jocelyne（单位未在摘要中提供，推测为 University of Amsterdam 及合作机构）
- **期刊/预印本平台**：Nucleic Acids Research
- **年份**：2026-06-02
- **论文类型**：方法学/软件工具论文
- **领域**：DNA 结构建模与分子模拟工具开发
- **关键词**：DNA 结构生成、刚性体形式、分子动力学、非经典碱基、蒙特卡洛最小化
- **DOI/arXiv 号**：10.1093/nar/gkag549
- **代码**：https://doi.org/10.6084/m9.figshare.31436725（Figshare 存档，链接至 GitHub 仓库）
- **数据**：未提供（案例使用 PDB: 1KX5 核小体核心颗粒、6MIG/6MIK/6MIH Hachimoji、3SV3/4C8M d5SICS–dNaM、2KV0/1TUQ 荧光碱基）
- **阅读日期**：2026-06-02
- **在课题方向中的位置**：该文属于「蛋白质-DNA 互作 × 物理模拟」方向中的**结构准备与几何分析工具层**。它不直接预测 TF-DNA 结合，而是为 MD 模拟提供任意形状 dsDNA（含 DNA-蛋白质复合物）的初始原子结构，并提供刚性体参数分析工具。对 TF-DNA 结合机制研究而言，它是**上游工具**——解决"如何构建含 TF 的 DNA 底物并分析 DNA 形变"的问题，而非结合预测本身。

## 02 一句话总结
MDNA 通过样条映射技术将任意形状的 dsDNA 结构（含非经典碱基、甲基化、WCF-to-Hoogsteen 翻转）从几何控制点转换为原子分辨率模型，并集成基于刚性体形式的分析工具，为 MD 模拟提供统一的 DNA 结构生成-分析工作流。

## 03 研究问题
- **具体问题**：现有工具无法灵活生成具有任意形状、拓扑和化学修饰的 dsDNA 原子结构，且缺乏与 MD 工作流无缝集成的分析工具。
- **为什么重要**：MD 模拟研究 DNA-蛋白质复合物（如 TF-DNA 结合、核小体动态）需要高质量的初始结构；实验结构（X-ray/cryo-EM）往往缺失 loop 区域或需要构建突变体、修饰碱基的变体结构。
- **现有方法不足**：
  - Avogadro、ChimeraX、PyMOL 只能生成线性 DNA，缺乏形状控制；
  - 3DNA、Curves+ 擅长分析但非生成工具，且依赖外部编译；
  - emDNA 依赖 3DNA/DSSR 做原子映射，集成复杂；
  - 粗粒化工具（oxDNA 等）无法直接输出全原子结构。
- **精确研究问题**：Can a spline-based mapping approach generate atomistic dsDNA structures of arbitrary shape and modification state, integrated with rigid-body analysis, within a single Python framework suitable for MD simulation workflows?

## 04 背景与发展脉络
*标注：以下脉络基于本文 Introduction 的叙述，属「仅本文框架」，未经外部系统核验。*

| 阶段 | 代表方法 | 优点 | 局限 |
|------|----------|------|------|
| 基础建模 | Avogadro, ChimeraX, PyMOL | 易用、可视化强 | 仅线性 DNA，无形状控制 |
| 结构分析 | 3DNA, Curves+ | 刚性体参数标准化 | 非生成工具，需编译安装 |
| 形状建模 | VDNA (VMD 插件) | 支持曲线 DNA | GUI 依赖，难以批处理 |
| 弹性优化 | emDNA | 序列依赖弹性最小化 | 依赖 3DNA/DSSR 映射，集成复杂 |
| 粗粒化模拟 | oxDNA, mrdna | 大规模结构预测 | 非全原子，需反向映射 |
| **本文位置** | **MDNA** | **生成+分析一体化，Python 原生，支持修饰碱基** | **仅 dsDNA，无 ssDNA/RNA 支持** |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 复杂 DNA 结构生成困难 | 无法构建 loop、超螺旋、蛋白-DNA 复合物等非直线结构 | 现有工具仅支持线性或简单弯曲 DNA | Introduction 第 2 段 |
| 修饰碱基支持不足 | 非经典碱基、甲基化、Hoogsteen 配对难以建模 | 工具库缺乏扩展的核苷酸库 | Introduction 第 2 段；Results 图 2A |
| 生成与分析工具割裂 | 生成结构后需用另一套工具分析，格式转换繁琐 | 缺乏统一框架 | Introduction 第 3 段 |
| 可重复性差 | GUI 工具难以脚本化、批处理 | VDNA 等依赖 VMD GUI | Introduction 第 3 段 |
| 与 MD 工作流集成困难 | 输出格式不兼容主流 MD 引擎 | 缺乏 MDTraj 等中间层 | Methods "Overview" 节 |
| 拓扑控制不精确 | 连环数（linking number）与形状（writhe）的耦合难以处理 | 未显式处理 White-Fuller 定理 | Methods "Structure generation" 节（dLk 调整公式） |

## 06 核心思想

**1) 表面方法**：
- 样条映射：用户提供控制点 → 拟合样条曲线 → 沿曲线等距放置碱基对 → 构建 Darboux 框架 → 分配原子坐标
- MC 最小化：基于弹性哈密顿量和硬球势能松弛结构
- 刚性体参数分析：计算 12 个自由度（6 个 intra-base-pair + 6 个 inter-base-pair）

**2) 核心洞察**：
- DNA 结构可以解耦为"几何形状（样条）"和"局部化学（碱基对框架）"两个层次，分别控制后再组合
- 通过调整初始扭转（Tw₀）来满足连环数约束，将拓扑要求转化为局部几何调整
- 将生成与分析统一在 Nucleic 类中，使"构建-松弛-分析"成为单一工作流

**3) 可能的普适教训 [Analysis]**：
- 对 TF-DNA 互作研究：DNA 的**形状自由度**（弯曲、超螺旋）与**局部碱基对几何**（如 Hoogsteen 翻转）可以独立建模再组合——这提示在构建 TF-DNA 复合物初始结构时，可先确定 DNA 骨架路径（如 TF 诱导的弯曲），再优化局部碱基配对
- 工具设计上，"生成器+松弛器+分析器"三合一架构值得借鉴：避免在多个软件间转换格式带来的误差和低效

## 07 方法总览

**输入**：
- 核苷酸序列（可选）
- 控制点坐标（定义 DNA 形状）
- 拓扑参数：n_bp、circular（是否环状）、dLk（连环数变化）
- 可选：已有结构文件（PDB 等）或轨迹

**输出**：
- Nucleic 对象（含原子坐标、拓扑信息）
- MDTraj 对象（可直接用于 MD 模拟）
- 刚性体参数数组（shape: t, n_bp, 12）

**模块**：
1. `mdna.make()` — 从零生成结构
2. `mdna.load()` — 加载已有结构/轨迹
3. `.minimize()` — MC 松弛
4. `.mutate()` / `.methylate()` / `.flip()` — 碱基修饰
5. `.extend()` / `.connect()` — 结构延伸与连接
6. `mdna.compute_rigid_parameters()` — 刚性体分析
7. `mdna.compute_linking_number()` — 连环数计算

**训练**：不适用（非机器学习方法）

**反馈回路**：MC 最小化中，能量评估（弹性 + 硬球排斥）→ 接受/拒绝移动 → 更新结构 → 重复直至收敛

**假设**：
- B-DNA 默认几何（10.5 bp/圈）
- 碱基对间距 0.34 nm
- 弹性模型基于刚性体参数（隐含假设 DNA 形变可用谐波近似描述）

**文字流程**：
```
用户输入（序列/控制点/拓扑参数）
    → mdna.make() 拟合样条 → 构建 Darboux 框架 → 分配原子坐标
    → 可选：.mutate()/.methylate()/.flip() 修饰碱基
    → 可选：.minimize() MC 松弛（弹性 + 硬球势）
    → 输出：Nucleic 对象 / MDTraj 对象
    → 分析：compute_rigid_parameters() / compute_linking_number()
    → 导出：PDB/轨迹文件 → 用于 MD 模拟（如 OpenMM）
```

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 样条映射（make） | 将控制点转换为碱基对框架 | 实现任意形状 DNA 生成 | 输入：控制点、序列；输出：Darboux 框架 | Methods "Structure generation" 节；图 1B | 无法生成非直线 DNA（预期影响，未实测） |
| MC 最小化（minimize） | 松弛结构消除 steric clash 和弹性应变 | 初始结构可能非物理 | 输入：Nucleic 对象；输出：松弛后结构 | Methods "Structure generation" 节；图 1C | 结构可能含原子碰撞或过度弯曲（预期影响） |
| 碱基修饰（mutate/methylate/flip） | 引入非经典碱基、甲基化、Hoogsteen 翻转 | 生物相关修饰影响 DNA 结构和 TF 结合 | 输入：碱基索引列表；输出：修饰后结构 | Results 图 2A；Table 1 | 无法研究修饰 DNA 的构象（预期影响） |
| 刚性体参数计算 | 计算 12 个自由度描述 DNA 几何 | 量化 DNA 形变与 TF 结合的关系 | 输入：轨迹/结构；输出：numpy 数组 (t, n_bp, 12) | Methods "Rigid body analysis" 节；图 2B-C | 无法定量分析 DNA 弯曲/扭转（预期影响） |
| 连环数计算 | 计算 linking number | 验证拓扑约束 | 输入：结构；输出：标量 | Methods "Structure generation" 节（dLk 公式） | 无法验证超螺旋结构正确性（预期影响） |
| extend/connect | 延伸或连接 DNA 片段 | 构建含蛋白的 loop 或长链 | 输入：两个 Nucleic 对象；输出：连接后结构 | Results 图 3B-C | 无法构建蛋白介导的 DNA loop（预期影响） |

*注：本文未提供消融实验，所有"移除后影响"均为 [Analysis] 预期推断，非实测数据。*

## 09 关键公式符号

**1) 连环数约束（White-Fuller 定理）**：
```
Lk = Tw + Wr
Tw_new = Tw_0 + dLk - Wr
```
- Lk：连环数（linking number）
- Tw：扭转数（twist）
- Wr：缠绕数（writhe）
- Tw_0：初始扭转
- dLk：用户指定的连环数变化
- 用途：确保生成的环状 DNA 满足拓扑约束
- 直觉：当形状有 writhe 时，需相应减少 twist 以保持 Lk 不变

**2) 碱基对间距**：
```
d = 0.34 nm（平均 rise）
```
- 用途：沿样条等距分布碱基对

**3) 螺旋密度**：
```
10.5 bp/turn（B-DNA 默认）
```
- 用途：设置相邻碱基对间的扭转角

**4) 刚性体参数**（未给出具体公式，引用 Curves+ 框架）：
- 6 个 intra-base-pair 参数：shear, stretch, stagger, buckle, propeller, opening
- 6 个 inter-base-pair 参数：shift, slide, rise, tilt, roll, twist
- 用途：量化 DNA 局部形变

*注：原文未给出弹性哈密顿量的具体数学形式，仅提及"elastic Hamiltonian and hard sphere potentials"。*

## 10 实验设计与证据链

**数据集/群体**：
- 核小体核心颗粒（NCP），PDB: 1KX5，250 ns MD 轨迹
- H-NS 蛋白丝（12 个亚基），PDB 来源未明确标注
- FoxP3 蛋白介导的 DNA loop 构建

**指标**：
- 刚性体参数分布（图 2B-C）
- 结构可视化对比（图 1D、图 3A-C）
- 计算成本：生成和最小化 ≤1000 bp 结构在普通笔记本上"negligible"时间

**基线/对比**：
- 未提供定量对比实验（无与 3DNA、Curves+ 的数值比较）
- 案例为定性展示（"proof of concept"）

**预算/算力**：
- 未提供具体硬件配置和运行时间数据

**评测协议**：
- 无标准 benchmark；通过案例展示功能

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| NCP 轨迹刚性体分析 | 分析工具能处理真实 MD 轨迹 | 250 ns NCP MD 轨迹 | 成功计算 12 个刚性体参数 | 分析模块可用于真实系统 | 未与 3DNA/Curves+ 输出做数值验证 | 图 2B-C |
| H-NS 丝 DNA 构建 | 能沿蛋白丝生成 DNA | 12 亚基 H-NS 丝 + 4 个 DBD | 生成 12 bp DNA 覆盖丝全长 | 可构建蛋白-DNA 复合物 | 未验证结构能量学合理性 | 图 3A |
| 核小体 DNA 延伸 | extend 能添加 linker DNA | NCP + 36 bp linker（5' 和 3'） | 成功延伸 | 可构建含 linker 的染色质结构 | 未验证 linker 的物理合理性 | 图 3B |
| FoxP3 介导 DNA loop | connect 能创建蛋白介导的 loop | 两个 DNA 片段 + FoxP3 桥 | 成功连接 | 可构建 loop 结构 | 未验证 loop 拓扑正确性 | 图 3C |
| 碱基修饰功能 | 支持非经典碱基和修饰 | Hachimoji、d5SICS-dNaM、2-AP、甲基化 | 库中包含这些碱基 | 可建模修饰 DNA | 未展示修饰后结构的 MD 验证 | 图 2A、Table 1 |

## 11 结论正确解读

**任务范围**：
- 该文是**工具介绍**，非科学发现型论文。其"结论"是功能可用性声明，而非生物学发现。
- 适用范围：**双链 DNA（dsDNA）**，明确不支持 ssDNA 和 RNA。

**oracle/真值输入**：
- 控制点由用户指定（来自实验结构、几何直觉或外部计算）
- 碱基对框架基于 B-DNA 理想几何（10.5 bp/turn, 0.34 nm rise）

**端到端状态**：
- 生成→松弛→分析流程完整，但**未验证**生成结构在 MD 模拟中的稳定性（无 RMSD/能量收敛数据）
- 与 OpenMM 的集成通过 MDTraj 实现，但未展示实际 MD 运行结果

**算力成本**：
- 声称 ≤1000 bp 生成+最小化在普通笔记本上可忽略不计，但未给出具体时间

**历史数据依赖**：
- 不依赖训练数据（非 ML 方法）
- 依赖 PDB 实验结构作为案例输入

**模型依赖**：
- 弹性哈密顿量参数未公开具体数值（可能依赖文献值）
- 硬球势参数未说明

**最难情形**：
- 复杂拓扑（高 writhe 超螺旋）的收敛性未测试
- 蛋白-DNA 复合物中蛋白侧链与 DNA 的 steric clash 处理未详细说明

**群体/领域边界**：
- 仅适用于 B-DNA 构象（未支持 A-DNA、Z-DNA）
- 不适用于 ssDNA、RNA、DNA-RNA 杂交体
- 不适用于含缺口（nick）或交联的 DNA

**不确定性**：
- 生成结构的物理合理性依赖 MC 松弛质量，但收敛判据（能量衰减拟合）可能遗漏亚稳态
- 刚性体参数计算与 3DNA/Curves+ 的一致性未做交叉验证

**有边界的复述**：
MDNA 能够从控制点生成任意形状的 dsDNA 原子结构，支持非经典碱基和化学修饰，并提供刚性体参数分析；其生成-松弛流程在 ≤1000 bp 范围内计算成本低。但该工具仅限 dsDNA，生成结构的 MD 稳定性未经验证，分析结果与既有工具的一致性未做定量比较。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 无 ssDNA 支持 | 不适用于复制、转录、某些 DNA 修复途径 | 开发 ssDNA 和 RNA 生成模块 | Conclusion 第 2 段 |
| 无 RNA 支持 | 无法建模 RNA 或 DNA-RNA 杂交体 | 同上 | Conclusion 第 2 段 |
| 无分支结构 | 不表示 branched architectures | 支持 DNA 纳米技术中的分支结构 | Conclusion 第 2 段 |
| 仅 MC 优化 | MC 是唯一内置优化方法 | 集成 steepest descent 等方法 | Conclusion 第 3 段 |
| 非经典碱基的力场参数依赖外部 | 模拟需自行获取 GAFF/CGenFF 参数 | 未明确提及 | Methods "Sequence library" 节（隐含） |
| 千碱基级 DNA 未优化 | 未针对 kb 级结构优化 | 提高大规模系统可扩展性 | Conclusion 第 3 段 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 未提供与 3DNA/Curves+ 的定量对比 | 刚性体参数计算可能存在系统性偏差 | 用户无法判断分析结果的可靠性 | 用相同 MD 轨迹分别计算，比较 12 参数分布 | Methods "Rigid body analysis" 节未提及验证 |
| 生成结构的 MD 稳定性未验证 | 样条映射可能产生局部不自然构象 | 初始结构质量直接影响 MD 模拟结果 | 对生成结构运行短 MD，检查 RMSD 和能量收敛 | 全文无 MD 运行结果 |
| 弹性哈密顿量参数未公开 | 无法复现 MC 松弛的精确行为 | 科学可复现性要求 | 检查代码仓库是否包含参数文件 | Methods 仅提及"elastic Hamiltonian" |
| 案例规模小（≤1000 bp） | 声称"negligible cost"可能不适用于更大系统 | TF-DNA 复合物常含多个结构域 | 测试 10 kb 级 DNA 的生成时间 | Conclusion 承认 kb 级未优化 |
| 蛋白-DNA 复合物构建依赖手动选择 DBD | 自动化程度有限 | 对高通量建模场景不够友好 | 检查 API 是否支持自动对接 | 图 3A 描述为"selected" |
| 非经典碱基的力场参数需用户自行获取 | 工具本身不解决参数化问题 | 用户可能因参数缺失而无法使用修饰碱基 | 检查文档是否提供参数获取指南 | Methods 提及 GAFF/CGenFF 但未提供参数 |
| 未讨论与 AlphaFold 等结构预测工具的衔接 | 无法从预测的蛋白-DNA 复合物直接生成 MD 初始结构 | 与 AI 结构预测工作流集成是重要需求 | 检查是否支持读取 AlphaFold 输出格式 | 全文未提及 |

## 14 学到什么
*标题：Agent 提炼的知识候选*

**面向「TF-DNA 互作 × AI/物理模拟」课题的可迁移知识：**

1. **形状-化学解耦建模策略**：MDNA 将 DNA 结构分解为"样条形状"与"碱基对框架"两个层次。对 TF-DNA 研究，这意味着可以**先确定 TF 诱导的 DNA 弯曲路径**（如从 cryo-EM 或 MD 获得），再用样条拟合生成完整 DNA 底物，避免从零搭建。

2. **拓扑约束的显式处理**：通过 dLk = Tw + Wr 的 White-Fuller 关系，将连环数约束转化为初始扭转调整。对研究 TF 结合引起的 DNA 超螺旋变化，这一方法可直接用于构建不同超螺旋密度的底物。

3. **MC 松弛作为结构精修手段**：基于弹性哈密顿量 + 硬球势的 MC 最小化，适合在原子细节 MD 之前快速消除 steric clash。对 TF-DNA 复合物，可先用此方法松弛 DNA 部分，再引入蛋白进行全原子 MD。

4. **刚性体参数作为互作定量指标**：12 个自由度（shear, stretch, stagger, buckle, propeller, opening, shift, slide, rise, tilt, roll, twist）是描述 TF 结合后 DNA 形变的标准化指标。可迁移为**评估 AI 预测的 TF-DNA 复合物结构是否物理合理**的度量。

5. **Python 原生 + MDTraj 集成**：工具设计上直接对接 MDTraj/OpenMM 生态，避免格式转换。对构建 AI 预测→MD 验证的自动化 pipeline 有借鉴意义。

6. **非经典碱基库的扩展性**：支持 Hachimoji、荧光碱基等，提示在 TF-DNA 研究中可建模**修饰 DNA 底物**（如甲基化 CpG 对 TF 结合的影响）。

**不可迁移/需注意**：
- 该工具不预测 TF 结合位点或亲和力，仅提供结构生成与分析
- 无 ssDNA 支持，不适用于转录泡、R-loop 等含单链区域的互作
- 生成结构的物理合理性需用户自行通过 MD 验证

## 15 与已有知识连接

**可核验的外部文献/资源：**

1. **3DNA (Lu & Olson, 2003; Nucleic Acids Research)**：刚性体参数分析的标准工具，MDNA 的框架与之兼容但为 Python 原生实现。可对比验证 MDNA 分析结果。

2. **Curves+ (Blanchet et al., 2011; Nucleic Acids Research)**：MDNA 引用其理论框架计算刚性体参数。对 TF-DNA 弯曲分析，Curves+ 是成熟参照。

3. **emDNA (Segal & Widom 相关方法)**：类似的最小化工具，但依赖 3DNA/DSSR 映射，MDNA 提供更集成的替代方案。

4. **oxDNA (Ouldridge et al.)**：粗粒化 DNA 模型，可生成超螺旋结构但非全原子。MDNA 可作为 oxDNA 结构到全原子的桥接工具。

5. **AlphaFold 3 / RoseTTAFold**：可预测蛋白-DNA 复合物结构，但输出常需 MD 精修。MDNA 可作为**从预测结构到 MD 初始结构**的中间工具（需验证格式兼容性）。

6. **PDB 条目**：1KX5（核小体）、6MIG/6MIK/6MIH（Hachimoji）、3SV3/4C8M（d5SICS-dNaM）、2KV0/1TUQ（荧光碱基）——可用于测试 MDNA 的碱基库覆盖。

**与课题方向的连接**：
- 对 TF-DNA 结合机制研究，MDNA 的价值在于**构建含特定 DNA 形变（弯曲、超螺旋、修饰）的底物**，用于 MD 模拟研究 TF 如何识别和诱导 DNA 构象变化
- 其刚性体分析可直接量化 TF 结合前后的 DNA 形变差异，与 ChIP-seq/SELEX 等实验数据结合可建立"结构-亲和力"关系

## 16 研究想法
*标题：Agent 生成的研究候选*

**候选 1：TF 诱导 DNA 弯曲的自动化底物生成 pipeline**
- **来源局限/观察**：MDNA 能生成任意形状 DNA，但需手动指定控制点；TF 结合位点的弯曲路径通常未知
- **核心假设**：结合 MDNA 的样条映射与 TF-DNA 共晶结构中的 DNA 弯曲参数，可自动生成不同弯曲程度的底物
- **增量**：将 MDNA 从"手动工具"升级为"自动生成器"，输入 TF 结合位点序列和弯曲角度，输出 MD-ready 结构
- **初步方法**：从 PDB 提取 TF-DNA 复合物的 DNA 弯曲轨迹 → 参数化弯曲角度 → 用 MDNA 生成不同弯曲度底物 → MD 模拟比较稳定性
- **验证方式**：对已知 TF（如 p53、TBP）生成底物，与实验结构对比 RMSD；MD 模拟检查构象稳定性
- **创新状态**：unverified

**候选 2：刚性体参数作为 TF-DNA 结合亲和力的结构描述符**
- **来源局限/观察**：MDNA 提供 12 个刚性体参数，但未与结合亲和力关联
- **核心假设**：TF 结合位点的 DNA 刚性体参数分布（尤其是 roll、tilt、twist）可预测 TF 结合亲和力
- **增量**：建立"结构参数 → 亲和力"的定量关系，补充序列-based 预测模型
- **初步方法**：收集 TF-DNA 复合物结构 → 计算刚性体参数 → 与实验 Kd 值回归 → 训练小规模预测模型
- **验证方式**：留一法交叉验证；与现有序列-based 模型比较
- **创新状态**：partially checked（已有文献表明 DNA 形变与 TF 结合相关，但 MDNA 提供统一计算框架）

**候选 3：MDNA 生成结构作为 AlphaFold 3 预测的 MD 精修起点**
- **来源局限/观察**：AF3 预测的蛋白-DNA 复合物常含 steric clash 和不自然 DNA 构象；MDNA 可生成理想化 DNA 底物
- **核心假设**：用 MDNA 生成 DNA 部分替换 AF3 预测中的 DNA 坐标，可提高 MD 模拟的初始稳定性
- **增量**：提供 AF3→MD 的自动化精修流程
- **初步方法**：AF3 预测 TF-DNA 复合物 → 提取蛋白坐标 → 用 MDNA 按 AF3 的 DNA 路径生成新 DNA → 组装 → 短 MD 平衡 → 比较 RMSD 和能量
- **验证方式**：对多个 TF-DNA 复合物测试，比较精修前后的 MD 稳定性指标
- **创新状态**：unverified

**候选 4：甲基化 CpG 对 TF 结合影响的 MD 研究**
- **来源局限/观察**：MDNA 支持甲基化修饰，但未展示其在 TF 结合研究中的应用
- **核心假设**：CpG 甲基化通过改变局部 DNA 刚性体参数（尤其是 propeller 和 roll）影响 TF 结合
- **增量**：提供甲基化 DNA 底物的系统生成方法，支持表观遗传学 MD 研究
- **初步方法**：用 MDNA 生成甲基化和未甲基化 DNA → MD 模拟 → 比较刚性体参数分布和 TF 结合自由能（MM-PBSA）
- **验证方式**：与实验甲基化敏感 TF 结合数据比较
- **创新状态**：unverified

**候选 5：DNA 拓扑状态对 TF 搜索动力学的影响**
- **来源局限/观察**：MDNA 支持连环数控制（dLk），可生成不同超螺旋密度的 DNA
- **核心假设**：超螺旋密度通过改变 DNA 弯曲/扭转柔性影响 TF 的一维滑动和三维跳跃动力学
- **增量**：提供系统研究 DNA 拓扑对 TF 搜索机制影响的计算框架
- **初步方法**：生成不同 dLk 的环状 DNA → 与 TF 进行 MD 模拟 → 分析 TF 的扩散系数和结合位点搜索效率
- **验证方式**：与单分子实验（FRET、磁镊）结果对比
- **创新状态**：unverified