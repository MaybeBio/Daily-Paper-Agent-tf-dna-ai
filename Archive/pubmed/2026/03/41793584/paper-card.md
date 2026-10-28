## 01 基本信息

- **标题**：C620Y Mutation-Induced Destabilization of the Androgen Receptor Disrupts DNA Recognition Specificity in Prostate Cancer: Insights from Extensive Parametric Normal Mode Simulations
- **作者**：Paul, Ishani; Ray, Sujay
- **单位**：未提供
- **期刊/平台**：Cell Biochemistry and Biophysics
- **年份**：2026（在线日期 2026-03-07）
- **论文类型**：计算模拟研究（normal mode simulation）
- **领域**：蛋白质-DNA 互作（雄激素受体 AR DBD 突变 C620Y 对 DNA 识别的影响）× 物理模拟（normal mode analysis）
- **关键词**：Androgen receptor; DNA binding domain; C620Y; normal mode simulation; prostate cancer; DNA recognition
- **DOI/arXiv**：10.1007/s12013-026-02034-y
- **代码**：未提供
- **数据**：未提供（模拟轨迹数据未公开）
- **阅读日期**：2026-05-12
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × 物理模拟」类别，聚焦于 AR（核受体家族转录因子）DBD 中一个点突变（C620Y）如何通过构象失稳削弱 DNA 结合亲和力与识别特异性。方法上采用参数化 normal mode 模拟（非 MD），属于中等精度的构象采样方法，可作为 MD/对接/结构预测方法的补充或预筛工具。对本课题的可迁移价值在于：展示了如何用 normal mode 分析系统性地将「突变→构象动力学改变→DNA 结合位点偏移→识别特异性丧失」串成因果链。

---

## 02 一句话总结

本文用参数化 normal mode 模拟比较野生型（WT_AR）与 C620Y 突变型（C620Y_AR）雄激素受体 DNA 结合域（DBD）在未结合与结合状态下的构象动力学，发现突变导致 DBD 整体失稳、DNA 结合位点从 K581-R586 偏移至 K591-K610、核苷酸识别模式紊乱，从而解释了 C620Y 突变导致的 DNA 结合亲和力下降与受体失活。

---

## 03 研究问题

- **具体问题**：AR DBD 中保守半胱氨酸 C620 突变为酪氨酸（C620Y）为何会导致 DNA 结合亲和力下降和受体失活？其分子机制是什么？
- **为什么重要**：AR 是前列腺癌（PC）及转移性去势抵抗性前列腺癌（mCRPC）的关键驱动因子，多种 AR 突变体在临床样本中被发现。理解突变如何削弱 DNA 结合，有助于靶向治疗策略的开发和耐药机制的解析。
- **现有方法为何不足**：此前已知 C620Y 导致受体失活和 DNA 结合减弱，但缺乏对「突变如何从构象动力学层面破坏 DNA 识别」的系统性机制解释。实验方法难以捕捉瞬时的构象变化和残基间协同运动。
- **精确研究问题（Can...?）**：Can parametric normal mode simulations reveal the mechanistic link between C620Y-induced conformational destabilization of AR DBD and its reduced DNA-binding affinity and altered recognition specificity?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论的框架，未做外部文献核验，标记为「仅本文框架」。

1. **阶段一：AR 突变的功能表征（实验为主）**——通过报告基因、结合实验等确认 C620Y 导致受体失活、DNA 结合减弱。优点：直接的功能证据；局限：缺乏原子层面的机制解释。
2. **阶段二：静态结构分析**——基于晶体结构比较 WT 与突变体的结构差异。优点：提供静态快照；局限：无法捕捉构象动态和残基协同运动。
3. **阶段三：分子动力学（MD）模拟**——用 MD 研究突变对蛋白动态的影响。优点：原子级精度、含溶剂效应；局限：计算成本高、采样时间有限，难以覆盖大尺度构象变化。
4. **阶段四（本文位置）：参数化 normal mode 模拟**——用简谐近似描述蛋白的集体运动模式，计算成本远低于 MD，可系统比较 WT 与突变体的构象系综。优点：高效、可覆盖大尺度运动；局限：忽略非谐效应和显式溶剂细节。

**本文主张的位置**：在 MD 与静态结构之间提供一个「中等精度、低成本」的动力学比较框架，用于快速评估突变对 DNA 结合域稳定性和识别特异性的影响。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 构象稳定性丧失 | C620Y_AR 的 RMSD 曲线波动显著高于 WT_AR | 突变破坏了 DBD 的整体构象稳定性 | 摘要：「An unsettling root mean square deviation curve hinted at the loss of conformational stability upon mutation」 |
| 结构紧凑性下降 | C620Y_AR 的 radius of gyration 和溶剂暴露程度更高 | 突变导致蛋白结构更松散、更易暴露于溶剂 | 摘要：「Radius of gyration and solvent exposure also described a more perpetuating stability in WT_AR」 |
| 二级结构网络破坏 | 模拟后半段 C620Y_AR 末端残基的氢键网络改变 | 氢键数量变化影响末端残基的二级结构组织 | 摘要：「Intramolecular forces of hydrogen bond count affected the secondary structural network of the terminal residues of C620Y_AR during the second half of the simulation」 |
| 疏水相互作用不稳定 | 蛋白表面疏水簇分布不一致 | 突变改变了表面疏水残基的聚集模式 | 摘要：「inconsistent hydrophobic interactions implied varied hydrophobicity clusters on protein surfaces」 |
| DNA 结合位点偏移 | 结合位点从 K581-R586 移至 K591-K610 | 残基灵活性增加和交叉相关网络改变导致结合位点漂移 | 摘要：「altered residual cross-correlation network especially, at DNA-binding sites which caused the binding site to shift beyond K581-R586 to K591-K610」 |
| 核苷酸识别模式紊乱 | C620Y 中核苷酸模式识别被破坏 | 局部溶剂可及性失衡和静电分布改变 | 摘要：「a disrupted nucleotide pattern recognition, imbalanced loss of local solvent accessibility and altered electrostatic charge distribution was observed in C620Y」 |

---

## 06 核心思想

### 1) 表面方法
用参数化 normal mode 模拟（parametric normal mode simulation）对 WT_AR 和 C620Y_AR 的 DBD 进行构象动力学比较，分析 RMSD、radius of gyration、溶剂暴露、氢键、疏水相互作用、RMSF、残基交叉相关网络、主成分分析（PCA）等指标，在未结合与结合 DNA 两种状态下进行。

### 2) 核心洞察
C620Y 突变并非简单地「破坏一个关键残基」，而是通过改变 DBD 的整体构象动力学——增加残基灵活性、破坏协同运动网络、使 DNA 结合位点从 K581-R586 漂移至 K591-K610——从而在多个层面（结构稳定性、溶剂可及性、静电分布、核苷酸识别）协同削弱 DNA 结合能力。这是一个「全局动力学失稳」而非「局部点损伤」的机制。

### 3) 可能的普适教训 [Analysis]
- 对 TF–DNA 互作而言，DNA 结合位点并非静态的「口袋」，而是由残基协同运动网络定义的动态区域。突变可通过改变协同网络使结合位点「漂移」，即使不直接接触 DNA 的残基突变也可能产生深远影响。
- Normal mode 分析可作为 MD 的低成本替代或预筛工具，尤其适合快速比较多个突变体的构象动力学特征。
- 「结合位点偏移」这一概念可推广到其他 TF 突变研究：评估突变效应时，不应只看直接接触 DNA 的残基，还应检查整个 DBD 的动力学重排。

---

## 07 方法总览

- **输入**：WT_AR DBD 与 C620Y_AR DBD 的结构（来源未明确说明，推测基于已知晶体结构或同源建模）；DNA 结合状态与未结合状态。
- **输出**：构象动力学指标（RMSD、RMSF、Rg、溶剂可及性、氢键数、疏水相互作用、交叉相关网络、PCA 主成分）、DNA 结合位点定位、核苷酸识别模式描述。
- **模块**：
  1. 结构准备与突变建模
  2. 参数化 normal mode 模拟（简谐近似，计算集体运动模式）
  3. 构象系综生成与轨迹分析
  4. 动力学指标计算（RMSD/RMSF/Rg/氢键/疏水）
  5. 交叉相关网络分析
  6. PCA 降维与构象态分类
  7. DNA 结合位点与识别模式分析
- **训练**：不适用（非机器学习方法）。
- **工具**：未提供具体软件名称。
- **反馈回路**：无显式反馈回路；为单向模拟-分析流程。
- **文字流程**：构建 WT 与 C620Y 突变体结构 → 在未结合与结合 DNA 两种状态下分别进行参数化 normal mode 模拟 → 生成构象系综 → 计算多种动力学指标 → 比较 WT 与突变体的差异 → 分析 DNA 结合位点偏移与识别模式变化 → 归纳突变失活机制。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 参数化 normal mode 模拟 | 生成蛋白构象系综，捕捉集体运动模式 | 以低成本获得 WT 与突变体的动力学差异 | 输入：结构；输出：构象系综/运动模式 | 摘要整体依赖此方法 | 预期影响：无法获得动力学信息，只能做静态比较（预期效应，未实测） |
| RMSD 分析 | 评估整体构象稳定性 | 判断突变是否导致结构失稳 | 输入：轨迹；输出：RMSD 曲线 | 摘要：「An unsettling root mean square deviation curve hinted at the loss of conformational stability」 | 预期影响：失去最直接的稳定性指标（预期效应） |
| Radius of gyration / 溶剂暴露分析 | 评估结构紧凑性与溶剂接触 | 判断突变是否导致结构松散 | 输入：轨迹；输出：Rg 值、溶剂可及性 | 摘要：「Radius of gyration and solvent exposure also described a more perpetuating stability in WT_AR」 | 预期影响：无法判断结构松散程度（预期效应） |
| 氢键与疏水相互作用分析 | 评估分子内作用力网络 | 判断突变对二级结构和表面性质的影响 | 输入：轨迹；输出：氢键数、疏水簇分布 | 摘要：「Intramolecular forces of hydrogen bond count affected the secondary structural network... inconsistent hydrophobic interactions」 | 预期影响：无法解释二级结构变化和表面性质差异（预期效应） |
| RMSF 与交叉相关网络分析 | 评估残基灵活性与协同运动 | 定位灵活性增加的区域，判断结合位点是否漂移 | 输入：轨迹；输出：RMSF 谱、相关矩阵 | 摘要：「altered residual cross-correlation network especially, at DNA-binding sites which caused the binding site to shift beyond K581-R586 to K591-K610」 | 预期影响：无法定位结合位点偏移（预期效应） |
| PCA | 降维表征构象态分布 | 判断 WT 与突变体的构象系综是否不同 | 输入：轨迹；输出：主成分、构象态分布 | 摘要：「Principal component analysis symbolized WT_AR conformational homogeneity, with kinetically microstable states」 | 预期影响：无法判断构象系综的异质性（预期效应） |
| DNA 结合位点与识别模式分析 | 定位 DNA 接触残基，评估识别特异性 | 直接关联突变与 DNA 结合能力下降 | 输入：构象系综 + DNA 结构；输出：结合位点、识别模式 | 摘要：「disrupted nucleotide pattern recognition, imbalanced loss of local solvent accessibility and altered electrostatic charge distribution」 | 预期影响：无法建立突变与 DNA 结合下降的直接联系（预期效应） |

> 注：本文未提供消融实验（如移除某模块后重新分析），所有「移除后影响」均为预期效应，非实测。

---

## 09 关键公式符号

本文为 normal mode 模拟研究，摘要中未给出具体公式。基于方法学常识，normal mode 分析通常涉及以下公式（标注为 [Analysis] 推断，非原文明确给出）：

1. **运动方程简谐近似**：  
   \( M \ddot{\mathbf{x}} = -K \mathbf{x} \)  
   其中 M 为质量矩阵，K 为 Hessian 矩阵（力常数矩阵），x 为位移向量。  
   用途：描述蛋白在能量极小点附近的集体振动模式。  
   来源：normal mode 分析标准框架（原文未明确给出，[Analysis] 推断）。

2. **本征值问题**：  
   \( K \mathbf{e}_i = \lambda_i \mathbf{e}_i \)  
   其中 λᵢ 为本征值（对应模式频率），eᵢ 为本征向量（对应振动方向）。  
   用途：提取低频大尺度运动模式，这些模式通常与功能相关构象变化有关。  
   来源：同上。

3. **RMSD 定义**（标准定义，原文未给出公式）：  
   \( \text{RMSD} = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (\mathbf{r}_i - \mathbf{r}_i^{\text{ref}})^2} \)  
   用途：量化构象偏离参考结构的程度。  
   来源：标准分析工具，原文未明确给出。

4. **RMSF 定义**（标准定义）：  
   \( \text{RMSF}_i = \sqrt{\frac{1}{T} \sum_{t=1}^{T} (\mathbf{r}_i(t) - \bar{\mathbf{r}}_i)^2} \)  
   用途：量化每个残基的时间平均波动幅度。  
   来源：标准分析工具，原文未明确给出。

> 注：原文摘要未提供任何公式，以上为基于方法学常识的推断，标注 [Analysis]。

---

## 10 实验设计与证据链

- **数据集/群体**：WT_AR DBD 与 C620Y_AR DBD 两种蛋白体系；每种体系在未结合（unbound）与结合（bound，即与 DNA 结合）两种状态下进行模拟。
- **规模**：未提供（模拟时长、体系大小等未在摘要中说明）。
- **指标**：RMSD、radius of gyration、溶剂暴露、氢键数、疏水相互作用、RMSF、残基交叉相关网络、PCA 主成分、DNA 结合位点位置、核苷酸识别模式、静电分布。
- **基线**：WT_AR 作为 C620Y_AR 的对照。
- **预算/资源**：未提供。
- **骨干/仪器**：未提供（计算资源未说明）。
- **oracle 输入**：不适用（非机器学习方法）。
- **评测协议**：比较 WT 与突变体在各指标上的差异，推断突变效应。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| RMSD 比较 | C620Y 导致构象稳定性下降 | WT_AR vs C620Y_AR（未结合与结合状态） | C620Y_AR 的 RMSD 曲线波动更大 | 突变导致构象失稳 | 无法定量判断失稳程度（无数值） | 摘要 |
| Radius of gyration / 溶剂暴露比较 | C620Y 导致结构松散 | WT_AR vs C620Y_AR | WT_AR 更稳定、更紧凑 | 突变导致结构松散、溶剂暴露增加 | 无法判断是否影响 DNA 结合的直接证据 | 摘要 |
| 氢键与疏水相互作用分析 | C620Y 破坏分子内作用力网络 | WT_AR vs C620Y_AR | 末端残基二级结构网络改变，疏水簇分布不一致 | 突变影响二级结构和表面性质 | 无法判断具体哪些残基受影响 | 摘要 |
| RMSF 与交叉相关网络分析 | C620Y 改变残基灵活性与协同运动 | WT_AR vs C620Y_AR | 结合位点区域灵活性增加，交叉相关网络改变 | 突变导致结合位点从 K581-R586 漂移至 K591-K610 | 无法判断漂移的功能后果（是否完全丧失结合） | 摘要 |
| PCA 比较 | C620Y 改变构象系综分布 | WT_AR vs C620Y_AR | WT_AR 构象均一，具有动力学微稳态 | 突变破坏构象均一性 | 无法判断微稳态的功能意义 | 摘要 |
| 核苷酸识别与静电分析 | C620Y 破坏 DNA 识别特异性 | C620Y_AR 结合状态 | 核苷酸模式识别紊乱，溶剂可及性失衡，静电分布改变 | 突变削弱 DNA 识别特异性 | 无法定量判断亲和力下降幅度 | 摘要 |

---

## 11 结论正确解读

- **任务范围**：本文仅覆盖 AR DBD 结构域（未包含全长 AR 或其他结构域），模拟方法为 normal mode（简谐近似），非全原子 MD。
- **oracle/真值输入**：不适用（无监督学习方法）。
- **端到端状态**：非端到端；为计算模拟-分析流程，未包含实验验证（如 EMSA、ITC 等）。
- **算力成本**：未提供。
- **历史数据依赖**：依赖已知的 AR DBD 结构（具体来源未说明）。
- **模型依赖**：依赖 normal mode 近似的有效性；简谐近似无法捕捉非谐效应（如构象跃迁、部分折叠）。
- **最难情形**：突变对 DNA 结合的影响是间接的（通过动力学改变），难以用单一静态结构解释；normal mode 无法模拟 DNA 结合/解离的完整热力学过程。
- **群体/领域边界**：结论仅针对 AR DBD 的 C620Y 突变；推广到其他 TF 或其他 AR 突变需谨慎。
- **不确定性**：摘要未提供定量误差估计、统计显著性检验或重复实验；所有结论为定性描述。
- **有边界的复述**：在 normal mode 模拟的近似框架下，C620Y 突变导致 AR DBD 构象失稳、结合位点从 K581-R586 漂移至 K591-K610、核苷酸识别模式紊乱，这些变化与已知的 DNA 结合亲和力下降和受体失活一致，但本文未提供定量结合自由能变化或实验验证。

---

## 12 作者自认局限

在提供的材料（摘要）中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，基于摘要措辞推断）：
- 方法为 normal mode 模拟，属于近似方法，未提及与 MD 或实验的交叉验证。
- 摘要未提供定量数据（如 RMSD 数值、结合自由能变化），可能暗示结果以定性描述为主。
- 未提及对模拟参数选择的敏感性分析。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 摘要未提供任何定量数值（RMSD 值、Rg 值、氢键数等） | 结论可能仅基于定性趋势，缺乏统计显著性 | 无法评估效应大小和可信度 | 要求作者提供具体数值和误差范围 | 摘要全文无数字 |
| Normal mode 模拟的简谐近似可能无法捕捉非谐效应 | 突变可能诱导非谐性构象变化（如部分折叠、构象跃迁），normal mode 会低估这些效应 | 可能高估或低估突变效应 | 用全原子 MD 或增强采样方法交叉验证 | 方法学常识 [Analysis] |
| 未提及 DNA 结合状态的建模方式 | DNA 的初始位置、取向、序列可能影响结合位点分析结果 | 结合位点偏移结论可能依赖初始建模 | 检查方法部分是否说明 DNA 对接/放置方式 | 摘要未提供方法细节 |
| 未提供与实验数据的直接对比 | 已知 C620Y 导致 DNA 结合减弱，但本文未定量复现这一结果 | 计算预测与实验的定量一致性未知 | 计算结合自由能变化并与实验 Kd 比较 | 摘要未提及实验对比 |
| 结合位点从 K581-R586 漂移至 K591-K610 的结论 | 该偏移是否意味着完全丧失结合，还是仅改变结合模式？ | 功能后果的解读依赖此区分 | 分析漂移后位点是否仍能形成 DNA 接触 | 摘要仅描述「shift」未说明功能后果 |
| PCA 显示 WT 具有「动力学微稳态」 | 微稳态的功能意义未解释 | 无法判断微稳态是否与 DNA 结合功能相关 | 分析微稳态间的转换是否与 DNA 结合/释放相关 | 摘要仅描述现象未解释功能 |

---

## 14 Agent 提炼的知识候选

### 可迁移概念

1. **「结合位点漂移」概念**：TF 的 DNA 结合位点不是静态的，而是由残基协同运动网络定义的动态区域。突变可通过改变协同网络使结合位点「漂移」，即使突变残基不直接接触 DNA。
   - **迁移到本课题**：在研究其他 TF（如 p53、MYC、FOXO 等）的致病突变时，不应只关注直接接触 DNA 的残基，还应检查整个 DBD 的动力学重排。可用 normal mode 或 MD 的交叉相关分析来检测结合位点是否发生漂移。

2. **Normal mode 作为低成本预筛工具**：在 MD 之前，用 normal mode 快速比较多个突变体的构象动力学特征，筛选出值得深入研究的候选突变。
   - **迁移到本课题**：对于 TF 突变体库（如癌症基因组图谱中的 TF 突变），可先用 normal mode 批量筛选影响构象稳定性和结合位点完整性的突变，再用 MD 或实验验证。

3. **多指标联合诊断框架**：RMSD（整体稳定性）+ Rg（紧凑性）+ RMSF（残基灵活性）+ 交叉相关（协同运动）+ PCA（构象系综分布）的组合，可系统评估突变对 TF-DNA 结合的影响。
   - **迁移到本课题**：建立 TF 突变评估的标准流程，将多个动力学指标整合为「突变危害评分」。

4. **未结合 vs 结合状态的双状态比较**：在无 DNA 和有 DNA 两种状态下分别模拟，可区分突变对「预组织」和「诱导拟合」的影响。
   - **迁移到本课题**：研究 TF 突变时，分别分析 apo 和 holo 状态，判断突变是破坏 DNA 结合前的预组织，还是破坏结合后的稳定化。

### 可迁移方法

5. **交叉相关网络分析定位功能热点**：通过残基间运动相关性矩阵，识别与 DNA 结合位点耦合的残基网络。
   - **迁移到本课题**：可用于预测 TF 中「远端突变通过变构影响 DNA 结合」的路径。

6. **PCA 识别构象亚态**：用 PCA 将构象系综分为不同亚态，比较 WT 与突变体的亚态分布差异。
   - **迁移到本课题**：可用于判断突变是否将 TF 锁定在非功能性构象亚态。

### 可迁移实验设计

7. **WT vs 突变体的系统比较框架**：以 WT 为基线，对突变体进行多维度动力学比较，而非仅看单一指标。
   - **迁移到本课题**：设计 TF 突变功能评估实验时，采用「多指标 + 双状态 + 系统比较」的框架。

---

## 15 与已有知识连接

- **核受体超家族 DNA 结合机制**：AR 属于核受体超家族，其 DBD 包含两个锌指结构，P-box 残基直接接触 DNA 大沟。C620 位于 DBD 的保守区域，其突变影响 DNA 结合与已知的核受体 DBD 功能研究一致（如 GR、ER 的类似突变研究）。[Analysis：基于核受体领域常识，原文未引用具体文献]
- **Normal mode 分析在蛋白-DNA 互作中的应用**：normal mode 已被用于研究蛋白-DNA 结合的结构变化（如 T7 RNA polymerase、lac repressor 等体系），本文将其应用于 TF 突变效应评估，属于该方法的合理延伸。[Analysis：方法学常识]
- **TF 突变与疾病**：与 p53 的 DNA 结合域突变研究（如 R175H、R248Q 等）类似，本文展示了「突变通过构象动力学改变而非直接接触破坏来削弱 DNA 结合」的机制，与 p53 突变研究中的「构象突变体」概念一致。[Analysis：基于 p53 领域常识]
- **前列腺癌 AR 突变谱**：AR 突变在 mCRPC 中常见（如 T877A、W741C 等配体结合域突变），C620Y 属于 DBD 突变，与配体结合域突变机制不同，补充了 AR 突变功能图谱。[Analysis：基于前列腺癌领域常识]
- **与 AlphaFold 等结构预测方法的关系**：本文未使用 AI 结构预测，但 normal mode 分析可与 AlphaFold 预测的结构结合使用——用预测结构作为 normal mode 的输入，快速评估突变效应。[Analysis：潜在组合方向]

---

## 16 Agent 生成的研究候选

### 候选 1：TF 突变「结合位点漂移」的系统检测框架
- **名称**：TF-BindShift：基于 normal mode 的 TF 突变结合位点漂移检测工具
- **来源局限/观察**：本文展示了 C620Y 导致 AR DBD 结合位点从 K581-R586 漂移至 K591-K610，但未提供自动化检测方法
- **核心假设**：TF 致病突变可通过改变残基协同运动网络使 DNA 结合位点发生可检测的漂移
- **初步方法**：对 TF 突变体库进行 normal mode 模拟，计算残基-DNA 接触概率谱，用 Wasserstein 距离量化 WT 与突变体的结合位点分布差异
- **验证方式**：在已知 TF 突变数据集（如 p53、AR、ER 突变）上验证，与实验结合亲和力数据比较
- **创新状态**：unverified

### 候选 2：Normal mode 与 AlphaFold 结合的 TF 突变快速预筛
- **名称**：AF-NM 预筛管道：AlphaFold 结构 + normal mode 动力学评分
- **来源局限/观察**：本文用 normal mode 评估突变效应，但未与 AI 结构预测结合；AlphaFold 可提供无实验结构的 TF 突变体模型
- **核心假设**：AlphaFold 预测的突变体结构 + normal mode 动力学分析可快速区分「良性」与「致病」TF 突变
- **初步方法**：用 AlphaFold 预测 TF 突变体结构 → 以预测结构为输入进行 normal mode 模拟 → 提取 RMSF、交叉相关、结合位点漂移等特征 → 训练分类器区分致病/良性突变
- **验证方式**：在 ClinVar 或 COSMIC 中标注的 TF 突变上评估分类性能
- **创新状态**：unverified

### 候选 3：TF-DNA 结合位点「动力学预组织」的定量表征
- **名称**：DynPreOrg 指数：TF DNA 结合位点的动力学预组织度量
- **来源局限/观察**：本文比较了未结合与结合状态，但未定量表征「预组织」程度
- **核心假设**：TF 的 DNA 结合位点在未结合状态下已部分预组织为结合构象，突变可破坏这种预组织
- **初步方法**：对 apo 状态 TF 进行 normal mode 或 MD 模拟，计算结合位点残基与 DNA 结合构象的 RMSD 分布，定义「预组织指数」= 结合构象占比
- **验证方式**：在多个 TF 体系上验证预组织指数与实验结合亲和力的相关性
- **创新状态**：unverified

### 候选 4：TF 突变「远端变构路径」的 normal mode 预测
- **名称**：AlloPath-TF：基于 normal mode 的 TF 远端突变变构路径预测
- **来源局限/观察**：本文发现 C620Y 突变影响整个 DBD 的动力学，暗示存在变构传播路径，但未系统分析
- **核心假设**：TF 中远离 DNA 结合位点的突变可通过蛋白内部的协同运动网络影响 DNA 结合
- **初步方法**：用 normal mode 的交叉相关矩阵构建残基网络，用图论方法（如最短路径、介数中心性）识别从突变位点到 DNA 结合位点的变构传播路径
- **验证方式**：在已知变构 TF 突变（如 p53 的远端突变）上验证预测路径与实验突变效应的对应关系
- **创新状态**：unverified

### 候选 5：TF-DNA 识别特异性的动力学指纹
- **名称**：DynFingerprint-TF：TF-DNA 识别特异性的动力学指纹图谱
- **来源局限/观察**：本文提到 C620Y 导致「disrupted nucleotide pattern recognition」，但未系统表征识别特异性的动力学基础
- **核心假设**：TF 对 DNA 序列的识别特异性不仅取决于静态接触，还取决于结合位点残基的动力学指纹（波动模式、协同运动）
- **初步方法**：对 TF 与不同 DNA 序列的复合物进行 normal mode 模拟，提取结合位点残基的波动谱和交叉相关模式，构建「动力学指纹」，比较不同 DNA 序列的指纹差异
- **验证方式**：在已知 TF 结合偏好（如 SELEX 数据）上验证动力学指纹与序列偏好的相关性
- **创新状态**：unverified