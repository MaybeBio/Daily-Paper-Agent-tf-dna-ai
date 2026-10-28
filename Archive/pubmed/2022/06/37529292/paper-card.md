## 01 基本信息
- **标题**：Homologous basic helix-loop-helix transcription factors induce distinct deformations of torsionally-stressed DNA: a potential transcription regulation mechanism
- **作者与单位**：Horberg, Johanna; Moreau, Kevin; Reymer, Anna（单位未提供）
- **期刊/预印本平台**：QRB Discovery
- **年份**：2022-06-10
- **论文类型**：研究论文（计算模拟 + 生物信息学分析）
- **领域**：蛋白质-DNA 互作；转录因子（TF）–DNA 结合机制；DNA 扭转应力；分子动力学（MD）模拟
- **关键词**：BHLH 转录因子；MycMax；MadMax；MaxMax；DNA 扭转；umbrella sampling；MD 模拟；CHIP-seq
- **DOI/arXiv 号**：10.1017/qrd.2022.5
- **代码**：https://github.com/annareym/PLUMED_DNA-Twist（DNA 扭转约束的 PLUMED 实现）
- **数据**：未提供（作者称可向通讯作者索取）
- **阅读日期**：未提供
- **在该方向中的位置**：本文聚焦 TF–DNA 结合机制在扭转应力下的响应，属于「TF–DNA 互作 × 物理模拟（MD）」交叉方向。其核心贡献在于揭示同源 BHLH 二聚体（MycMax、MadMax、MaxMax）结合同一 E-box 序列时，在扭转应力下诱导出不同的 DNA 变形模式，并提出这一差异可能作为转录调控的补充机制。该工作为「TF 如何通过 DNA 力学响应实现功能分化」提供了原子级证据，与 AI 方法（如结构预测、序列-力学关系建模）可形成互补。

## 02 一句话总结
本文通过微秒级 umbrella sampling MD 模拟，对 MycMax、MadMax、MaxMax 三种同源 BHLH 二聚体结合同一 E-box DNA 序列的系统施加 ±5°/bp 的扭转约束，发现三种复合物使 DNA 的扭转刚度相似地增加（扭转模量 153–168 nm vs 自由 DNA 111 nm），但在扭转应力下诱导出不同的 DNA 局部变形模式（弯曲方向、扭转吸收位点），并推测这种差异可能通过影响协同 TF 的结合来贡献于同源 TF 的差异化转录调控。

## 03 研究问题
- **具体问题**：同源 BHLH 转录因子（MycMax、MadMax、MaxMax）结合相同的 E-box DNA 序列时，在扭转应力下是否诱导不同的 DNA 变形？这些变形差异是否可能构成转录调控的机制？
- **为什么重要**：真核转录调控中，RNA 聚合酶产生的 DNA 扭转应力是重要调控力。TF–DNA 复合物如何响应扭转应力、同源 TF 是否通过不同的 DNA 力学响应实现功能分化，是理解转录调控机制的关键未解问题。
- **现有方法为何不足**：此前研究（如作者对 BZIP 因子 MafB 的工作）表明 TF 结合可增加 DNA 扭转刚度，但仅涉及单一 TF 家族；同源 TF 之间的差异响应尚未被系统研究。实验方法难以在原子尺度解析扭转应力下的 DNA 变形细节。
- **精确的「Can ... ?」问题**：Can homologous BHLH TF dimers that recognize the same DNA sequence induce distinct deformations of torsionally-stressed DNA, thereby providing a mechanism for differential transcriptional regulation?

## 04 背景与发展脉络
（注：以下脉络基于本文框架，未做外部系统核验，标注为「仅本文框架」）

1. **DNA 扭转应力与转录调控**（仅本文框架）：扭转应力由 RNA 聚合酶引入，沿染色质纤维传播，影响核小体稳定性、高级染色质结构，进而调控转录。DNA 局部对扭转应力的响应具有序列特异性。
2. **扭转电容器（twist-capacitor）概念**（仅本文框架）：特定 YpR/RpR 二核苷酸步（如 TpA、CpA）具有 twist 双稳态，可吸收扭转应力，维持 DNA 的 B 型构象。这些位点与蛋白-DNA 识别机制耦合。
3. **TF–DNA 复合物的扭转刚度研究**（仅本文框架）：作者前期对 BZIP 因子 MafB 的研究表明，TF 结合使 DNA 扭转刚度几乎翻倍（207 nm vs 107 nm），并锁定 twist-capacitor 的构象亚态。
4. **本文位置**：将研究扩展到 BHLH 家族的同源二聚体，首次系统比较同源 TF 在扭转应力下的 DNA 变形差异，并提出「TF 特异性 DNA 变形 → 协同因子招募差异 → 转录输出差异」的机制假说。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 同源 TF 功能分化的机制不清 | MycMax、MadMax、MaxMax 识别相同 DNA 序列却调控不同转录程序 | 传统观点归因于 transactivation domain（TAD）差异；作者提出 DNA 力学响应差异可能是补充机制 | Discussion 节：「distinct responses to DNA twisting by homologous TFs may be a complementary mechanism to variations in transactivation domains (TAD)」 |
| 扭转应力下 TF–DNA 复合物的原子级行为未知 | 缺乏同源 TF 在扭转应力下 DNA 变形的系统比较 | 实验方法难以在原子尺度控制并观测 DNA 扭转 | Methods 节：使用自研扭转约束 + umbrella sampling MD |
| 扭转应力在 TF 结合位点的局部吸收机制不清 | 自由 DNA 中扭转应力由 YpR 步吸收，但蛋白结合后吸收位点如何变化未知 | 蛋白-DNA 接触锁定特定二核苷酸步的构象，改变扭转应力分配 | Results 节图 3：蛋白结合后扭转应力主要累积在 E-box 侧翼区 |
| 扭转应力诱导的 DNA 变形是否具有 TF 特异性 | 三种同源二聚体诱导不同的变形模式 | 蛋白-DNA 接触网络差异（尤其是 loop 区接触）导致变形差异 | Results 节图 2b、4、5 及 Supplementary Videos 1–4 |

## 06 核心思想
1. **表面方法**：对四种系统（MycMax-DNA、MadMax-DNA、MaxMax-DNA、自由 DNA）进行微秒级 umbrella sampling MD 模拟，使用自研扭转约束控制 DNA 总扭转（±5°/bp），通过 WHAM 计算 PMF 得到扭转模量；用 Curves+ 分析螺旋参数和沟几何；用 CHIP-seq 数据（TFregulomeR）分析 Myc/Max 的协同结合因子。
2. **核心洞察**：同源 TF 结合使 DNA 扭转刚度相似地增加，但扭转应力诱导的 DNA 变形模式是 TF 特异的——变形主要发生在 E-box 侧翼区，且弯曲方向、扭转吸收位点因 TF 而异。这种「刚度相似、变形特异」的组合可能是一种精细的转录调控机制：TF 通过改变 DNA 的局部力学响应来影响协同因子的结合。
3. **可能的普适教训** [Analysis]：TF 的功能分化可能不仅由序列识别特异性决定，还由「DNA 力学响应指纹」决定。这提示在预测 TF 功能时，除结合序列外，还需考虑 TF 对 DNA 力学性质的调制作用。对 AI 方法而言，这意味着「序列-结构-力学」联合建模可能比单纯序列比对更能捕捉 TF 功能差异。

## 07 方法总览
- **输入**：四种系统的原子坐标（PDB: 1NKP、1NLW、1AN2 及自由 B-DNA），DNA 序列为 23-mer（5′-GGCGAGTAGCACGTGCTACTCGC-3′，含 E-box 响应元件）。
- **输出**：PMF 曲线、扭转模量、DNA 螺旋参数（twist、roll、shift、slide 等）、沟几何参数、蛋白-DNA 接触网络、CHIP-seq 协同结合因子列表。
- **模块**：
  1. 系统构建（UCSF Chimera 修改序列、JUMNA 延伸侧翼并松弛接触）
  2. 无约束 MD 平衡（0.6 μs）
  3. 级联 umbrella sampling（0.5 μs/窗口，共 10.5 μs/系统）
  4. WHAM 分析（PMF）
  5. Curves+ 螺旋参数分析
  6. CPPTRAJ 接触分析
  7. TFregulomeR CHIP-seq 分析
- **训练**：不适用（无监督学习/无训练过程）
- **工具**：GROMACS v2019.4、PLUMED v2.5.3、AMBER 14SB（蛋白）、Parmbsc1（DNA）、SPC/E 水、K+/Cl− 离子（150 mM）、Curves+、Canal、CPPTRAJ、TFregulomeR、MatLab、R
- **反馈回路**：无（非迭代优化方法）
- **假设**：扭转约束范围 ±5°/bp 可代表体内极端局部扭转；Parmbsc1 力场可准确描述 DNA 扭转行为；umbrella sampling 窗口足够重叠以保证 PMF 收敛。

**文字流程**：从 PDB 结构出发 → 修改 DNA 序列匹配目标 E-box → JUMNA 延伸侧翼 → 溶剂化/中和/加盐 → 能量最小化 → 0.6 μs 无约束 MD 平衡 → 从平衡轨迹提取初始扭转值 → 级联 umbrella sampling 逐步改变扭转至 ±5°/bp → WHAM 计算 PMF → 二次回归得扭转模量 → Curves+ 分析螺旋参数 → CPPTRAJ 分析接触 → 对 Myc/Max CHIP-seq 数据用 TFregulomeR 找协同结合因子。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 扭转约束（PLUMED 实现） | 控制 DNA 总扭转至目标值 | 模拟体内扭转应力条件 | 输入：原子坐标；输出：受约束轨迹 | Methods 节；代码公开于 GitHub | 无法系统研究扭转应力效应（预期） |
| 级联 umbrella sampling | 沿扭转坐标采样 | 克服自由能垒，获得 PMF | 输入：平衡结构；输出：各窗口轨迹 | Methods 节；10.5 μs/系统 | 无法获得扭转自由能面（预期） |
| WHAM 分析 | 合并窗口数据得 PMF | 计算扭转模量 | 输入：各窗口 twist 分布；输出：PMF | Results 图 2a | 无法定量比较刚度（预期） |
| Curves+ 螺旋参数分析 | 提取 twist、roll、shift 等 | 解析变形模式 | 输入：轨迹；输出：螺旋参数 | Results 图 3–5 | 无法定位变形位点（预期） |
| CPPTRAJ 接触分析 | 识别蛋白-DNA 接触 | 解释变形差异的分子机制 | 输入：轨迹；输出：接触网络 | Results 图 6、Supplementary Figs 15–17 | 无法关联接触与变形（预期） |
| TFregulomeR CHIP-seq 分析 | 找 Myc/Max 的协同结合因子 | 验证变形差异的生物学相关性 | 输入：CHIP-seq 数据；输出：top-10 协同因子 | Results 节、Supplementary Fig. 18 | 无法支持「变形→协同因子招募」假说（预期） |

## 09 关键公式符号
- **扭转模量公式**（Eq. 1，Methods 节）：
  \[
  T = \frac{K \cdot \Delta\theta}{L}
  \]
  其中：
  - \( T \)：扭矩（torque）
  - \( K \)：扭转力常数（twisting force constant，kcal mol⁻¹ deg⁻²），由 PMF 二次回归获得
  - \( \Delta\theta \)：扭转变化量（deg）
  - \( L \)：标准碱基对长度（0.34 nm）
  
  扭转模量（torsional modulus）单位为 nm，由 K 换算得到（具体换算公式文中未完整给出，仅给出 Eq. 1 的框架）。

- **PMF 计算**（WHAM 方法，Methods 节）：未给出具体公式，但标准 WHAM 方程用于合并 umbrella sampling 窗口。

- **扭转约束势**（Methods 节）：\( K_{tw} (twist - twist_{ref})^2 \)，其中 \( K_{tw} = 0.06 \) kcal mol⁻¹ deg⁻²。

## 10 实验设计与证据链
- **数据集/群体**：4 个模拟系统（MycMax-DNA、MadMax-DNA、MaxMax-DNA、自由 DNA），DNA 序列相同（23-mer，含 E-box）。
- **规模**：每个系统 10.5 μs 总采样（0.6 μs 平衡 + 10.5 μs umbrella sampling），21 个窗口（±5°/bp，步长 0.5°/bp）。
- **指标**：PMF、扭转模量、twist/roll/shift/slide、沟宽/深、蛋白-DNA 接触数、变形能。
- **基线**：自由 DNA 的扭转模量（111 nm）和变形模式。
- **预算**：未提供（SNIC 计算资源）。
- **骨干/仪器**：GROMACS v2019.4 + PLUMED v2.5.3。
- **oracle 输入**：PDB 晶体结构（1NKP、1NLW、1AN2）。
- **评测协议**：PMF 二次回归（±2° 区域）；螺旋参数和接触分析基于全轨迹平均；CHIP-seq 分析用 TFregulomeR 默认参数。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 扭转模量比较 | TF 结合增加 DNA 扭转刚度 | 自由 DNA vs 三种复合物 | 自由 DNA 111 nm；MycMax 153 nm；MadMax 163 nm；MaxMax 168 nm | TF 结合使 DNA 更刚硬 | 无法区分三种复合物的刚度差异是否显著（未给误差棒/统计检验） | Results 节、Supplementary Table 1 |
| 变形模式分析 | 同源 TF 诱导不同 DNA 变形 | 三种复合物在相同扭转应力下 | 弯曲方向、扭转吸收位点因 TF 而异（图 2b、4、5） | 变形模式是 TF 特异的 | 仅一个 DNA 序列，无法推广到其他 E-box 上下文 | Results 节图 2b、4、5 |
| 接触网络分析 | 接触差异解释变形差异 | 三种复合物的接触模式 | Myc/Mad/Max_1 形成特异接触，Max/Max_2 更非特异；Mad loop 的 Arg91 与侧翼 TpA 接触 | 接触网络差异与变形差异相关 | 相关性不等于因果性；未做突变验证 | Results 图 6、Supplementary Figs 15–17 |
| CHIP-seq 协同因子分析 | 变形差异可能影响协同因子招募 | Myc vs Max 的 top-10 协同因子 | 发现 E2F、BZIP、锌指家族成员 | 变形差异可能与协同因子招募相关 | CHIP-seq 分辨率不足以直接证明力学机制；未做功能实验 | Results 节、Supplementary Fig. 18 |

## 11 结论正确解读
- **任务范围**：本文仅研究一个 DNA 序列（含 E-box）在体外（模拟）条件下的扭转响应；未覆盖其他 E-box 序列上下文、其他 BHLF 家族成员、染色质环境。
- **oracle/真值输入**：模拟基于晶体结构（1NKP、1NLW、1AN2），这些结构本身可能不代表溶液中的全部构象。
- **端到端状态**：从模拟到生物学结论是「推测性」的——作者提出变形差异可能影响协同因子招募，但未做实验验证。
- **算力成本**：微秒级 MD 模拟计算成本高，但作者未提供具体资源消耗。
- **历史数据依赖**：CHIP-seq 数据来自公共数据库（TFregulomeR），不同细胞系（A549、NB4、K562）的覆盖度和质量可能影响结果。
- **模型依赖**：结果依赖 AMBER 14SB + Parmbsc1 力场的准确性；Parmbsc1 对扭转行为的描述虽优于旧力场，但仍有局限。
- **最难情形**：高扭转应力（±5°/bp）下可能接近 DNA 结构转变阈值，模拟可能未完全捕捉非 B 型构象。
- **群体/领域边界**：结论限于 BHLF 家族中 Myc/Max/Mad 网络；不能外推到其他 TF 家族。
- **不确定性**：PMF 的统计误差未报告；变形能计算的标准差较高（~10 kcal/mol），说明构象采样可能未完全收敛。

**有边界的复述**：在 AMBER 14SB + Parmbsc1 力场下，对含 E-box 的 23-mer DNA 进行微秒级 umbrella sampling 模拟，发现 MycMax、MadMax、MaxMax 结合均使 DNA 扭转模量从 111 nm 增加至 153–168 nm，但三种复合物在扭转应力下表现出不同的 DNA 变形模式（弯曲方向、扭转吸收位点）。这些变形差异可能与蛋白-DNA 接触网络差异相关，并可能通过影响协同因子招募来贡献于同源 TF 的差异化转录调控——但这一机制假说尚未经实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 单一 DNA 序列 | 仅研究一个 E-box 序列上下文 | 未明确提及 | Discussion 节（隐含） |
| 模拟条件与体内差异 | 扭转应力范围可能高于体内实际值 | 未明确提及 | Results 节（「The selected range may be an exaggeration」） |
| CHIP-seq 分辨率限制 | 无法直接证明力学机制 | 未明确提及 | Discussion 节（「ChIP-seq data is not single-base resolved」） |
| 序列长度有限 | 23-mer 较短，可能无法完全反映染色质环境 | 未明确提及 | Discussion 节（「the studied DNA sequence is relatively short」） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 扭转模量差异（153/163/168 nm）未做统计检验 | 三种复合物的刚度差异可能在误差范围内 | 若差异不显著，「刚度相似」的结论更稳健，但「变形特异」的 claim 不受影响 | 重复模拟（不同初始条件/力场）并报告标准差；用 bootstrap 或 Bayesian 分析 | Supplementary Table 1 未给误差 |
| 变形差异可能来自初始结构差异而非 TF 特异性 | 三种复合物的 PDB 结构本身可能处于不同构象状态 | 若初始构象差异主导，则「TF 特异性变形」的结论被削弱 | 从同一初始结构出发，分别模拟三种 TF 结合；或做多副本模拟 | Methods 节未说明初始结构准备细节 |
| CHIP-seq 协同因子分析是相关性而非因果性 | 协同因子共定位可能由其他机制（如染色质状态）驱动 | 若力学机制不成立，本文的生物学假说需要修正 | 设计实验：突变 TF 的 DNA 变形能力（如改变 loop 区接触）后检测协同因子招募变化 | Discussion 节为推测性语言 |
| 变形能计算标准差高（~10 kcal/mol） | 构象采样可能未收敛，PMF 可能不准确 | 若 PMF 不准确，扭转模量值可能不可靠 | 延长模拟时间；检查窗口间重叠；用不同 WHAM 实现交叉验证 | Results 图 2c 误差棒 |
| 未研究 DNA 序列变异的影响 | E-box 侧翼序列可能影响变形模式 | 若侧翼序列主导变形，则「TF 特异性」可能被高估 | 对多个 E-box 侧翼序列变体进行模拟 | 本文仅一个序列 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **扭转约束 + umbrella sampling 方法可直接迁移**：作者公开了 PLUMED 扭转约束代码（GitHub），可用于研究其他 TF–DNA 复合物在扭转应力下的响应。对课题方向而言，这是研究「TF 如何通过 DNA 力学响应实现功能分化」的现成工具。

2. **「刚度相似、变形特异」的概念框架**：同源 TF 可能通过相似的刚度增加来阻碍扭转应力传播，但通过不同的变形模式（弯曲方向、扭转吸收位点）来差异化地影响协同因子。这一框架可迁移到其他 TF 家族（如锌指、BZIP）的同源成员比较。

3. **变形能计算模型（Liebl & Zacharias 2021）**：基于六碱基对参数的变形能模型可用于量化 TF 结合对 DNA 局部柔性的影响。对 AI 方法而言，该模型可作为「序列→力学性质」预测的物理先验或训练标签。

4. **CHIP-seq 共定位分析的力学解释**：TF 共定位数据（TFregulomeR）可用于生成「哪些 TF 可能受 DNA 变形影响」的假设，再通过模拟验证。这为「AI 预测 TF 协同结合」提供了力学维度的补充特征。

5. **TF 的 loop 区可参与 DNA 力学调制**：Mad 的 loop 区 Arg91 与侧翼 TpA 的接触改变了扭转应力分配。这提示在预测 TF 结合位点时，不应只关注基础区（basic region）的序列识别，还应考虑 loop 区的非特异接触对 DNA 力学的影响。

6. **扭转应力吸收位点的序列依赖性**：自由 DNA 中扭转应力由 YpR 步吸收，但蛋白结合后吸收位点转移到侧翼区。这提示「TF 结合位点 + 侧翼序列」共同决定 DNA 的力学响应，对设计 TF 结合位点预测模型有参考价值。

## 15 与已有知识连接
- **与作者前期工作（Hörberg & Reymer, 2020）**：本文是作者对 BZIP 因子 MafB 研究的延伸，将「TF 增加 DNA 扭转刚度」的发现扩展到 BHLF 家族，并首次比较同源 TF 的差异。可对比 MafB（207 nm）与 BHLF（153–168 nm）的刚度差异，思考 TF 结合位点长度（13–14 bp vs 6 bp）对力学效应的影响。
- **与 twist-capacitor 文献（Kannan et al., 2006; Liebl & Zacharias, 2017, 2020）**：本文验证了 twist-capacitor 概念在蛋白结合 DNA 中的适用性，并发现蛋白结合可「锁定」这些位点的构象，使其失去吸收扭转应力的能力。
- **与 DNA 扭转应力与转录调控的综述（Lavelle, 2008; Kouzine et al., 2013; Corless & Gilbert, 2016）**：本文为「扭转应力调控转录」提供了分子层面的机制：TF 结合位点作为扭转应力的「障碍物」，其变形模式可能决定协同因子的可及性。
- **与结构预测/AI 方法（候选方向）**：本文的变形能计算模型（Liebl & Zacharias 2021）可作为「序列→力学性质」预测的训练标签；扭转约束模拟数据可用于验证 AI 预测的 DNA 力学响应。AlphaFold 等结构预测工具无法直接预测 DNA 力学性质，本文的模拟方法可补充这一维度。
- **与单分子实验（未直接引用，但相关）**：本文的模拟结果可与单分子扭转实验（如磁镊）对比，验证 TF 结合对 DNA 扭转刚度的预测。

## 16 研究想法
**Agent 生成的研究候选**：

1. **名称**：TF 变形指纹的序列依赖性图谱
   - **来源局限/观察**：本文仅研究一个 DNA 序列，无法判断变形模式是 TF 特异还是序列上下文依赖。
   - **核心假设**：TF 诱导的 DNA 变形模式由「TF 接触模式 × 侧翼序列」共同决定，存在可预测的「变形指纹」。
   - **初步方法**：对多个 E-box 侧翼序列变体，分别模拟 MycMax、MadMax、MaxMax 结合，提取变形特征（弯曲方向、扭转吸收位点、roll 分布），构建「TF × 序列 → 变形」数据集。
   - **验证方式**：用留一序列交叉验证，检验变形指纹的预测性；与单分子实验（磁镊 + 荧光标记）对比。
   - **创新状态**：unverified

2. **名称**：基于图神经网络的 TF–DNA 变形预测模型
   - **来源局限/观察**：MD 模拟成本高，难以覆盖大量 TF–序列组合；本文的变形能模型可作为物理先验。
   - **核心假设**：图神经网络（GNN）以 TF 接触残基和 DNA 序列为输入，可预测扭转应力下的 DNA 变形模式。
   - **初步方法**：将本文的模拟数据（及扩展数据）作为训练集，以 DNA 原子图 + TF 接触信息为输入，预测 twist/roll/shift 变化和变形能。
   - **验证方式**：与 MD 模拟结果对比；在未见过的 TF–序列组合上测试；与实验（如 CHIP-exo 的 footprint 数据）对比。
   - **创新状态**：unverified

3. **名称**：扭转应力下 TF 协同结合的力学模型
   - **来源局限/观察**：本文提出变形差异可能影响协同因子招募，但未验证。
   - **核心假设**：TF 诱导的 DNA 变形模式决定了协同因子（如 E2F、BZIP）能否在邻近位点结合。
   - **初步方法**：对 Myc/Max 的 CHIP-seq 共定位位点，提取侧翼序列，用 MD 模拟预测变形模式，统计变形特征与共定位频率的相关性。
   - **验证方式**：构建「变形特征 → 共定位概率」的预测模型；用 CRISPR 突变破坏变形位点后检测共定位变化。
   - **创新状态**：unverified

4. **名称**：TF loop 区对 DNA 力学调制的系统研究
   - **来源局限/观察**：本文发现 Mad loop 的 Arg91 与侧翼 TpA 接触影响扭转应力分配，但未系统研究 loop 区的作用。
   - **核心假设**：TF loop 区的非特异接触是 DNA 变形特异性的重要决定因素，且可通过序列设计调控。
   - **初步方法**：对 Myc、Max、Mad 的 loop 区进行系统突变，模拟突变体与 DNA 复合物在扭转应力下的变形，建立「loop 序列 → 变形模式」映射。
   - **验证方式**：用表面等离子共振（SPR）或荧光各向异性测量突变体的 DNA 结合亲和力与扭转响应；与模拟预测对比。
   - **创新状态**：unverified

5. **名称**：TF–DNA 复合物扭转模量的机器学习预测
   - **来源局限/观察**：本文报告了三种复合物的扭转模量（153–168 nm），但数据点少，无法建立预测模型。
   - **核心假设**：TF–DNA 复合物的扭转模量可由「TF 结合位点长度、接触残基类型、DNA 序列柔性」等特征预测。
   - **初步方法**：收集文献中 TF–DNA 复合物的扭转模量数据（含本文），提取结构/序列特征，训练回归模型（如随机森林、GNN）。
   - **验证方式**：交叉验证；对未见于训练的 TF 家族进行预测，并用 MD 模拟验证。
   - **创新状态**：unverified