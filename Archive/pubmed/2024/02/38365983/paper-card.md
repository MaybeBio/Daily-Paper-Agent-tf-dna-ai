## 01 基本信息

- **标题**：DNA binding redistributes activation domain ensemble and accessibility in pioneer factor Sox2
- **作者**：Bjarnason, Sveinn; McIvor, Jordan A P; Prestel, Andreas; Demeny, Kinga S; Bullerjahn, Jakob T; Kragelund, Birthe B; Mercadante, Davide; Heidarsson, Petur O
- **单位**：University of Iceland（冰岛大学）等（具体单位列表未在摘要中完整提供）
- **期刊/预印本平台**：Nature Communications
- **年份**：2024
- **论文类型**：研究论文（Research Article）
- **领域**：结构生物学 / 生物物理学 / 转录调控
- **关键词**：Sox2, pioneer factor, intrinsically disordered region (IDR), activation domain, smFRET, NMR, coarse-grained simulation, protein-DNA interaction
- **DOI/arXiv**：10.1038/s41467-024-45847-2
- **代码**：未提供（模拟使用GROMACS 5.1.4，分析使用Fretica、MDAnalysis等，但未提供自定义代码仓库）
- **数据**：BMRB accession number 51964（NMR化学位移）；PDB: 6T7B（起始结构）、2LE4（验证用）
- **阅读日期**：2026-05-12
- **在课题方向中的位置**：本文聚焦 pioneer factor Sox2 的 C 端 IDR（含两个 activation domains, AD1/AD2）在 DNA 结合前后的构象 ensemble 变化，属于「TF–DNA 互作机制 × 物理模拟（粗粒化 MD）」交叉方向。核心贡献在于揭示 DNA 结合通过重分布 IDR 与 DBD 之间的电荷互作来改变 activation domain 的可及性，为理解 TF 的 IDR 功能提供了定量 ensemble 模型。

## 02 一句话总结

本文通过整合单分子 FRET、NMR 和粗粒化 Langevin 动力学模拟，发现 pioneer factor Sox2 的 C 端 intrinsically disordered region（IDR）在结合 DNA 后发生 ensemble 重排——从与 DBD 的广泛弱电荷互作转变为更扩展的构象，从而差异化地改变两个 activation domain（AD1/AD2）对共调控因子的可及性，且不改变 DNA 结合亲和力。

## 03 研究问题

- **具体问题**：Sox2 的 C 端 IDR（~200 残基，含 AD1 和 AD2）在自由状态和 DNA 结合状态下的构象 ensemble 有何不同？DNA 结合如何影响 activation domain 的可及性？
- **为什么重要**：超过 1600 个人类 TF 通过 IDR 中的 activation domain 招募共激活因子来调控转录，但缺乏定量构象 ensemble 模型阻碍了机制解码。Pioneer factor Sox2 是研究 IDR 功能的理想模型，因其 IDR 对 pioneering 功能至关重要。
- **现有方法不足**：传统结构生物学（X-ray、cryo-EM）难以解析 IDR 的动态 ensemble；AlphaFold 对 IDR 的预测置信度低；以往研究多聚焦 DBD-DNA 互作，忽略了 IDR 在 DNA 结合前后的构象变化。
- **精确研究问题**：Can DNA binding by the Sox2 DBD induce a redistribution of the C-terminal IDR ensemble that differentially alters the accessibility of its two activation domains, without affecting DNA binding affinity?

## 04 背景与发展脉络

（注：以下脉络基于本文引言与讨论，属「仅本文框架」，未经外部系统核验）

1. **TF 结构-功能研究的经典范式**：早期研究聚焦 DBD 的 DNA 识别机制，认为 TF 功能主要由 DBD 决定，IDR 被视为柔性连接区。
2. **IDR 功能认识的兴起**：近年研究发现 TF 的 IDR 参与转录激活、相分离、翻译后修饰调控等，但缺乏定量构象描述。
3. **IDR ensemble 研究方法的发展**：NMR 化学位移和弛豫提供残基级动态信息；单分子 FRET 提供长程距离分布；粗粒化模拟（如 self-avoiding walk 模型、Langevin 动力学）可重建 ensemble。
4. **TF-IDR 与 DBD 互作的研究**：已有报道（如 p53、MYC/MAX）表明 IDR 与 DBD 存在电荷互作，但多为定性描述，缺乏 DNA 结合前后 ensemble 变化的定量比较。
5. **本文主张的位置**：首次对 full-length pioneer factor 进行「自由 vs DNA 结合」的 IDR ensemble 定量比较，提出 DNA 结合通过重分布 IDR-DBD 电荷互作来调控 activation domain 可及性的机制模型。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| IDR 构象 ensemble 难以实验表征 | 传统结构生物学无法解析 IDR；AlphaFold 预测置信度低 | IDR 高度动态、无单一稳定构象 | 引言：IDR 缺乏定量 ensemble 模型；Fig. 1a 预测显示 IDR 无序 |
| 全长 TF 的 IDR-DBD 互作缺乏定量描述 | 以往研究多分离 DBD 或 IDR 单独研究 | 全长蛋白表达/标记困难，且 IDR 信号重叠严重 | 引言：IDR 在 TF 中研究不足；方法：需设计多种标记构建体 |
| DNA 结合对 IDR 的影响未知 | 经典模型假设 DBD 与 IDR 功能独立 | 缺乏 DNA 结合前后 IDR ensemble 的系统比较 | 本文核心问题（Results 第 2-3 节） |
| 盐浓度敏感性难以解释 | IDR 尺寸对盐浓度高度敏感，生理范围内变化显著 | 电荷屏蔽效应影响 IDR-DBD 静电互作 | Fig. 2f：full-length 在 100-200 mM KCl 出现 roll-over 效应 |
| 模拟与实验的定量对接困难 | 粗粒化模拟参数需反复调优才能复现 FRET | 模拟分辨率与实验可观测量的映射复杂 | Methods：通过调节 εpp 单一参数匹配 22 个 FRET 值 |

## 06 核心思想

### 1) 表面方法
- 用 smFRET 测量 Sox2 多种标记位置的构象距离（11 个自由态 + 11 个 DNA 结合态）
- 用 NMR 化学位移扰动（CSP）和 15N 弛豫检测残基级互作变化
- 用粗粒化 Langevin 动力学模拟重建 ensemble，通过调节单一参数 εpp 匹配实验 FRET

### 2) 核心洞察
- **DNA 结合不是简单地"释放"IDR，而是重分布 IDR-DBD 互作**：自由态中 IDR 与 DBD 存在广泛弱电荷互作，DNA 结合后这些互作被部分破坏，但 IDR 并未完全自由——而是与 N-IDR 形成新的互作，且 AD1 和 AD2 的可及性变化方向相反（AD1 可及性降低，AD2 可及性增加）。
- **IDR ensemble 的"可及性重分布"而非"整体展开"**：DNA 结合使 IDR 整体更扩展（FRET 降低），但不同区域的变化不均匀，AD1 与 DBD 的接触增加，AD2 与 DBD 的接触减少。
- **电荷互作是主要驱动力**：盐浓度实验和模拟均表明 IDR-DBD 互作主要由静电驱动，且这种互作强度在生理盐浓度范围内高度可调。

### 3) 可能的普适教训 [Analysis]
- **TF 的 IDR 不是被动"悬挂"在 DBD 上，而是主动参与 DNA 结合后的构象重排**——这对理解 TF 的 allostery 和共调控因子招募具有重要意义。
- **"可及性"应被视为 ensemble 属性而非单一构象属性**：activation domain 的功能取决于其在 ensemble 中被暴露的概率，而非某一特定构象。
- **单一参数（εpp）调优的粗粒化模拟足以捕捉 IDR ensemble 的关键特征**，提示 IDR 行为可能由少数全局参数主导，这对 AI 辅助的 IDR 建模有启发。

## 07 方法总览

- **输入**：全长 Sox2 蛋白（多种半胱氨酸突变体用于荧光标记）、15N/13C 同位素标记蛋白、含 Sox2 结合位点的 DNA 寡核苷酸（15 bp）和 197 bp 核小体 DNA
- **输出**：自由态和 DNA 结合态的 IDR 构象 ensemble、残基级互作图谱、activation domain 可及性定量描述
- **模块**：
  1. 蛋白表达纯化（SUMO 标签、Lemo21(DE3) 细胞）
  2. 荧光标记（Cy3B 供体、CF660R 受体，maleimide 化学）
  3. smFRET 测量（共聚焦显微镜，PIE 激发）
  4. NMR 波谱（化学位移归属、CSP、15N 弛豫）
  5. 粗粒化 Langevin 动力学模拟（GROMACS 5.1.4）
  6. FRET 值回算与参数调优
- **训练**：无监督学习；模拟参数通过手动调优 εpp 匹配实验 FRET
- **反馈回路**：实验 FRET → 模拟回算 → 调整 εpp → 重新模拟 → 比较
- **假设**：粗粒化模型（每个氨基酸一个 bead）；IDR 互作主要由电荷驱动；荧光标记不影响构象

**文字流程**：表达纯化 Sox2 突变体 → 荧光标记 → smFRET 测量自由态 FRET → 加入 DNA 测量结合态 FRET → NMR 归属并测量 CSP 和弛豫 → 构建粗粒化模型 → 运行 Langevin 模拟 → 回算 FRET 并与实验比较 → 调优 εpp → 获得最终 ensemble → 分析接触图谱和可及性

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| smFRET 构象探针 | 测量 IDR 不同区域间的距离分布 | 提供 ensemble 的长程距离约束 | 输入：标记蛋白 ± DNA；输出：FRET 效率直方图 | Fig. 1c-d, 2a, 3c-d, 4a-b | 失去实验距离约束，模拟 ensemble 无法验证 |
| NMR 化学位移归属与 CSP | 残基级检测 IDR-DBD 互作变化 | 提供序列特异性互作信息 | 输入：15N/13C 标记蛋白 ± DNA；输出：CSP 图谱 | Fig. 2g-i, 3g-h | 无法定位互作热点区域 |
| 15N 弛豫测量 | 检测 ps-ns 时间尺度动力学 | 区分静态与动态构象变化 | 输入：标记蛋白 ± DNA；输出：R2 图谱 | Fig. 3i-k | 无法判断 IDR 是否保持动态 |
| 粗粒化 Langevin 模拟 | 重建构象 ensemble | 将稀疏实验约束转化为全链模型 | 输入：序列、结构、FRET 约束；输出：ensemble 轨迹 | Fig. 4c-f, 5 | 无法获得空间分辨率信息 |
| εpp 参数调优 | 匹配实验 FRET | 校准模拟互作强度 | 输入：实验 FRET；输出：最优 εpp | Fig. 4d-e | 模拟与实验偏差增大 |
| 接触图谱分析 | 量化 IDR-DBD 和 IDR-IDR 接触 | 识别 DNA 结合诱导的互作重分布 | 输入：模拟轨迹；输出：接触差异图 | Fig. 5c-e | 无法解释 ensemble 重排机制 |

## 09 关键公式符号

1. **FRET 效率**：E = n'_A / (n'_A + n'_D)，其中 n'_A 和 n'_D 为校正后的受体和供体光子数。用于从实验测量中提取距离信息。

2. **Förster 方程**：E(r) = 1 / (1 + r⁶/R₀⁶)，其中 r 为供体-受体距离，R₀ = 6.0 nm（Cy3B-CF660R 染料对）。用于将 FRET 效率转换为距离。

3. **SAW-ν 模型距离分布**：P(r) = A(4π/R)(r/R)^(2+(γ-1)/ν) exp(-α(r/R)^(1/(1-ν)))，其中 ν 为 scaling exponent，γ ≈ 1.1615，A 和 α 由归一化和 ⟨r²⟩ = R² 条件确定。用于描述 IDP 的端到端距离分布。

4. **平均 FRET 回算**：⟨E⟩ = ∫₀^∞ dr E(r) P(r)。用于从模拟 ensemble 计算理论 FRET 值并与实验比较。

5. **弱变性剂结合模型**：E(c_D) = (E₀ + ΔE·K_a·c_D) / (1 + K_a·c_D)，其中 c_D 为变性剂浓度，K_a 为表观结合常数。用于拟合变性剂滴定数据。

6. **化学位移扰动**：CSP = √(½[(Δδ_H)² + (0.154·Δδ_N)²])，其中 Δδ_H 和 Δδ_N 分别为 ¹H 和 ¹⁵N 化学位移变化。用于量化 DNA 结合诱导的残基级环境变化。

7. **接触寿命双指数拟合**：C(t) = A·exp(-t/τ₁) + B·exp(-t/τ₂)，用于从自相关函数提取 IDR-DBD 接触的动力学时间尺度。

## 10 实验设计与证据链

**数据集/群体**：
- 重组表达的 Sox2 全长蛋白（317 残基）及截短构建体（N-IDB、C-IDR、DBD）
- 15 bp 双链 DNA（含 Sox2 结合位点 TTGT）
- 197 bp Widom 序列核小体（含 Sox2 结合位点）
- 多种半胱氨酸突变体用于荧光标记定位

**指标**：
- smFRET 平均效率 ⟨E⟩
- NMR CSP（化学位移扰动）
- ¹⁵N R₂ 弛豫率
- 模拟回算 FRET 与实验的 concordance correlation coefficient (ρc = 0.92)
- 接触分数和接触寿命

**基线/对照**：
- 分离的 C-IDR 构建体（无 DBD 和 DNA）
- 非特异性 DNA 对照
- 不同盐浓度（KCl）条件

**评测协议**：
- smFRET：每个构建体测量 >5000 个单分子事件
- NMR：275/290 个主链酰胺峰归属（>95%）
- 模拟：4 个重复 × 5 μs，前 1 μs 作为平衡

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| smFRET 全长 vs 分离 C-IDR | IDR 在全长中更紧凑 | 全长 Sox2 vs 分离 C-IDR，均标记 120/265 | 全长 ⟨E⟩ 更高（更紧凑） | DBD 与 IDR 存在互作 | 无法区分互作类型（静电 vs 疏水） | Fig. 2a |
| 盐浓度滴定 | IDR-DBD 互作为静电驱动 | 0-2000 mM KCl | full-length 在 100-200 mM 出现 roll-over，分离 C-IDR 无此效应 | 电荷互作被盐屏蔽 | 无法排除特定离子效应 | Fig. 2f |
| DNA 结合后 FRET 变化 | DNA 结合改变 IDR ensemble | 自由 vs 15 bp DNA 结合 | ⟨E⟩ 从 0.43 降至 0.28（扩展） | DNA 结合使 IDR 更扩展 | 无法确定是否完全释放 | Fig. 3c |
| NMR CSP 图谱 | DNA 结合诱导残基级变化 | 自由 vs DNA 结合 | CSP 集中在 AD1/AD2 区域 | DNA 结合改变 IDR 局部环境 | CSP 无法直接对应可及性 | Fig. 3h |
| ¹⁵N R₂ 弛豫 | DNA 结合改变 IDR 动力学 | 自由 vs DNA 结合 | R₂ 整体降低但非均匀 | IDR 在 DNA 结合后更快运动 | 无法区分整体 vs 局部效应 | Fig. 3i-k |
| 模拟 vs 实验 FRET | 粗粒化模型能复现实验 | 22 个 FRET 值比较 | ρc = 0.92 | 模型可靠 | 模型可能过度简化 | Fig. 4f |
| 接触图谱分析 | DNA 结合重分布 IDR-DBD 接触 | 自由 vs DNA 结合模拟 | AD1 接触增加，AD2 接触减少 | 可及性差异化重分布 | 模拟接触≠实验可及性 | Fig. 5c-e |
| 核小体结合 | 核小体上同样发生重排 | DNA vs 核小体 | 类似 FRET 变化 | 重排不依赖 DNA 长度 | 核小体特异性效应未排除 | Fig. 3d |

## 11 结论正确解读

- **任务范围**：本文仅研究 Sox2 的 C-IDR 在自由和 DNA 结合状态下的构象 ensemble 变化，不涉及其他 TF 或 IDR 类型。
- **oracle/真值输入**：模拟使用 PDB 6T7B 的 DBD-DNA 结构作为起始构象；IDR 部分无实验结构，由模拟生成。
- **端到端状态**：模拟-实验对接达到 ρc = 0.92，但模拟为粗粒化模型，无法提供原子级分辨率信息。
- **算力成本**：20 μs 总模拟时间（4×5 μs），粗粒化模型计算成本较低，但未提供具体 GPU/CPU 时数。
- **历史数据依赖**：依赖 PDB 6T7B 的 cryo-EM 结构（Sox2 结合核小体），该结构仅覆盖 DBD 区域。
- **模型依赖**：SAW-ν 聚合物模型假设 IDR 为均质聚合物，可能低估序列特异性效应。
- **最难情形**：AD1 区域（~150-200）的构象变化最复杂，因该区域同时与 DBD 和 DNA 有接触。
- **群体/领域边界**：结论限于 Sox2 及 SoxB 家族（Sox1/2/3 共享 IDR 电荷分布特征），推广至其他 TF 需谨慎。
- **不确定性**：FRET 测量提供 ensemble 平均信息，无法区分静态异质与动态平均；NMR CSP 无法直接定量可及性变化。

**有边界的复述**：在 Sox2 这一具体 pioneer factor 中，DNA 结合通过重分布 IDR-DBD 电荷互作，使 C-IDR 整体更扩展，但 AD1 和 AD2 的可及性变化方向相反；该效应在生理盐浓度范围内显著，且不改变 DNA 结合亲和力。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 粗粒化模型分辨率有限 | 每个氨基酸一个 bead，无法捕捉原子级互作细节 | 使用更精细的模型或全原子模拟验证 | Methods（模拟部分） |
| FRET 提供 ensemble 平均信息 | 无法区分静态异质与动态平均 | 结合单分子动力学追踪或 MD 模拟 | Discussion |
| 荧光标记可能影响构象 | 半胱氨酸突变和染料可能扰动 IDR 行为 | 使用非天然氨基酸或更小标签验证 | Methods（标记部分） |
| 核小体结合实验有限 | 仅测试了一种核小体构型 | 测试不同核小体定位和组蛋白修饰 | Discussion |
| 缺乏体内验证 | 所有实验在体外进行 | 在细胞中验证可及性变化的功能后果 | Discussion |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 模拟使用单一 εpp 参数匹配所有 FRET | 可能过度简化 IDR 的序列依赖性互作 | 若 IDR 不同区域互作强度不同，单一参数无法捕捉 | 使用序列依赖性 εpp 或对比不同 IDR 序列 | Methods 模拟部分 |
| DNA 结合后 FRET 变化可能部分来自染料- DNA 相互作用 | 染料可能直接与 DNA 互作，影响 FRET 读数 | 染料-DNA 互作会混淆构象解释 | 使用不同染料对或对照实验 | Methods 标记部分 |
| NMR CSP 与 FRET 变化的相关性未定量 | 两种方法可能报告不同时间尺度的构象变化 | 需要统一的多方法 ensemble 模型 | 联合拟合 NMR 和 FRET 数据 | Fig. 2i vs 3h |
| 盐浓度实验仅测试 KCl | 其他离子（如 Mg²⁺）可能对 IDR-DBD 互作有不同效应 | 生理条件下多种离子共存 | 测试不同离子种类和浓度 | Fig. 2f |
| 可及性变化未直接测量 | 接触分数作为可及性代理可能不准确 | 共调控因子结合实验才能直接验证可及性 | 进行共激活因子结合实验 | Fig. 5c-e |
| 模拟未包含翻译后修饰 | Sox2 的磷酸化等修饰可能改变 IDR 电荷分布 | PTM 是 TF 功能调控的重要机制 | 模拟磷酸化变体 | Discussion |

## 14 学到什么

**Agent 提炼的知识候选**

1. **IDR-DBD 电荷互作作为 TF 功能调控的通用机制**：本文表明 IDR 与 DBD 的弱电荷互作可调控 activation domain 可及性。此概念可迁移至其他 TF 的 IDR 功能研究，特别是预测 TF 突变（改变电荷）对 activation 功能的影响。

2. **DNA 结合诱导的 IDR ensemble 重分布可作为 AI 预测目标**：本文的「自由 vs 结合」ensemble 对比框架可用于训练机器学习模型，预测 DNA 结合对 IDR 构象的影响。输入特征可包括 DBD 电荷分布、DNA 序列、IDR 序列组成。

3. **粗粒化模拟 + 实验 FRET 的迭代调优策略**：通过单一参数（εpp）调优匹配多个实验 FRET 值的方法，为 IDR ensemble 建模提供了高效策略。可迁移至其他 IDP 系统的建模。

4. **可及性作为 ensemble 属性的量化方法**：本文用接触分数和接触寿命量化 activation domain 可及性，此方法可推广至预测 TF 的共调控因子结合位点。

5. **盐浓度敏感性作为 IDR-DBD 互作的诊断工具**：roll-over 效应可作为实验筛选 IDR-DBD 电荷互作的手段，适用于其他 TF 系统。

6. **多方法交叉验证框架**：smFRET（长程距离）+ NMR（残基级）+ 模拟（全链 ensemble）的三重验证框架，为 IDP 研究提供了可复制的实验设计模板。

## 15 与已有知识连接

- **Sox2 结构与功能**：本文与 Sox2 DBD-DNA 共晶结构（如 PDB 1GT0、6T7B）互补，将结构信息从 DBD 扩展到全长蛋白的 IDR 区域。
- **TF IDR 研究**：与 p53（Uversky 等）、MYC/MAX（Fuxreiter 等）的 IDR-DBD 互作研究一致，支持「IDR 与 DBD 互作是 TF 通用特征」的观点。
- **IDP ensemble 建模**：本文的 SAW-ν 模型与 Schuler 组（ETH Zürich）的 IDP 研究一脉相承，其 Fretica 分析包即来自该组。
- **粗粒化模拟方法**：与 Pappu 组、Mittal 组的 IDP 粗粒化模型（如 CALVADOS、MPI）互补，本文强调电荷互作而简化序列特异性。
- **Pioneer factor 机制**：与核小体结合研究（如 Chereji 等）衔接，本文表明 IDR 在核小体结合时同样发生重排，提示 IDR 可能参与核小体靶向。
- **AI 结构预测**：AlphaFold 对 IDR 预测置信度低（本文 Fig. 1a 也显示），本文的实验 ensemble 数据可作为 AI 模型（如 AlphaFold3、ESMFold）的验证基准。

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：TF-IDR 电荷模式预测器（TF-IDR Charge Pattern Predictor）
   - **来源局限/观察**：本文表明 IDR-DBD 电荷互作决定 activation domain 可及性，但缺乏系统预测工具
   - **核心假设**：TF 的 IDR 序列电荷模式（正负电荷分布、blockiness）可预测 DNA 结合后的 ensemble 重排方向
   - **初步方法**：收集已知 TF 的 IDR 序列和 DNA 结合前后 FRET 数据，训练 CNN/Transformer 模型预测 ensemble 变化
   - **验证方式**：留一法交叉验证，与本文 Sox2 数据对比
   - **创新状态**：unverified

2. **候选名称**：DNA 结合诱导 IDR 重排的粗粒化力场优化（CG Force Field Optimization for DNA-Induced IDR Rearrangement）
   - **来源局限/观察**：本文使用单一 εpp 参数，可能无法捕捉序列依赖性
   - **核心假设**：引入序列依赖的电荷-电荷互作参数可提高模拟-实验一致性
   - **初步方法**：在本文 CG 模型基础上，将 εpp 替换为基于序列的电荷模式函数，用贝叶斯优化调参
   - **验证方式**：对比优化前后与实验 FRET 的 ρc，测试多个 TF 系统
   - **创新状态**：partially checked（本文已证明 εpp 调优有效，但未探索序列依赖性）

3. **候选名称**：Activation Domain 可及性打分函数（Activation Domain Accessibility Score, ADAS）
   - **来源局限/观察**：本文用接触分数量化可及性，但未提供可直接使用的打分工具
   - **核心假设**：基于 ensemble 的 ADAS 可预测 TF 的转录激活能力
   - **初步方法**：从模拟 ensemble 计算每个残基的溶剂可及性和 DBD 接触分数，与已知 activation domain 活性数据关联
   - **验证方式**：与大规模 TF activation domain 筛选数据（如 StarActivity 数据库）对比
   - **创新状态**：unverified

4. **候选名称**：Pioneer Factor IDR 突变效应预测（Mutation Effect Prediction for Pioneer Factor IDRs）
   - **来源局限/观察**：本文讨论磷酸化可能改变 IDR 电荷，但未系统研究突变效应
   - **核心假设**：IDR 中电荷改变突变（如磷酸化模拟突变 S→E）可预测性改变 activation domain 可及性
   - **初步方法**：对 Sox2 C-IDR 进行饱和突变模拟，计算 ensemble 变化，与已知功能数据关联
   - **验证方式**：实验验证 top 预测突变体的 FRET 和转录活性
   - **创新状态**：unverified

5. **候选名称**：核小体 vs 裸 DNA 的 IDR 重排差异研究（Nucleosome vs Naked DNA IDR Rearrangement）
   - **来源局限/观察**：本文测试了核小体结合但未深入比较与裸 DNA 的差异
   - **核心假设**：核小体结合诱导的 IDR 重排与裸 DNA 不同，可能涉及组蛋白互作
   - **初步方法**：在本文 CG 模型中引入核小体组蛋白 beads，比较 IDR 接触图谱
   - **验证方式**：与本文核小体 FRET 数据对比，进行组蛋白突变实验
   - **创新状态**：partially checked（本文有核小体数据但未深入分析）