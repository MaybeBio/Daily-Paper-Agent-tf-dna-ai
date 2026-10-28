## 01 基本信息

- **标题**：Structural basis of the AlgU-MucA(cyto) interaction and SspB-mediated degradation in Pseudomonas aeruginosa stress response
- **作者与单位**：Li, Tao; Wang, Yingzhi; Zhao, Ninglin; Ge, Chunlei; Wu, Cuiling; Li, Ke; Li, Li; Wang, Zhiqiang; Chen, Ying; Chen, Zhenpu; Li, Weike; Liu, Yang; Wang, Zhonghui; Sha, Yun; Yao, Hong; Zhu, Yibo; Bao, Rui（单位未在摘要中提供）
- **期刊/预印本平台**：mBio
- **年份**：2026（在线日期 2026-05-19）
- **论文类型**：研究论文（结构生物学 + 生化验证）
- **领域**：结构生物学、微生物应激响应、蛋白质-蛋白质互作、蛋白酶体降解
- **关键词**：AlgU、MucA、SspB、ClpX/ClpP、σ^ECF、铜绿假单胞菌、晶体结构、应激响应
- **DOI/arXiv 号**：10.1128/mbio.00148-26
- **代码**：未提供
- **数据**：PDB 8Z6G（AlgU-MucAcyto 复合物晶体结构）
- **阅读日期**：2026-05-20
- **在课题方向中的位置**：本文聚焦细菌 σ^ECF 转录因子（AlgU）与其抗 sigma 因子（MucA）的互作机制，以及适配器蛋白 SspB 介导的蛋白酶体降解。虽非真核 TF-DNA 互作，但 σ^ECF-抗 sigma 因子互作是 TF 活性调控的经典模型，其"结合冗余 vs 稳定性必需"的界面设计、融合蛋白表达策略、AlphaFold3 辅助互作建模等方法，对 TF-DNA 互作研究具有直接可迁移价值。

## 02 一句话总结

通过融合蛋白表达策略获得 AlgU-MucAcyto 复合物 2.1 Å 晶体结构，揭示其界面由冗余的盐桥/氢键网络驱动结合但关键残基维持热稳定性，并鉴定 SspB 为双界面适配器，其 N 端结构域识别 AlgU 发夹表面、C 端无序尾结合 ClpX，从而将 MucAcyto 递送至 ClpX/ClpP 进行降解以释放 AlgU。

## 03 研究问题

- **具体问题**：AlgU-MucAcyto 复合物如何以高亲和力稳定结合？SspB 如何识别该复合物并将其递送至 ClpX/ClpP 蛋白酶体以降解 MucAcyto，从而激活 AlgU？
- **为什么重要**：AlgU 是铜绿假单胞菌包膜应激响应（ESR）的核心 σ^ECF 因子，调控藻酸盐（mucoid 表型）、绿脓菌素、pyoverdine 等毒力因子的产生。MucA 作为抗 sigma 因子，其降解是 AlgU 激活的限速步骤。理解这一机制对开发针对铜绿假单胞菌慢性感染（尤其囊性纤维化患者）的新策略至关重要。
- **现有方法不足**：此前虽有 AlgU-MucAcyto 结构（PDB 6IN7），但 AlgU 与 MucA 单独表达产量低、纯化困难，限制了对界面残基功能的系统研究；SspB 是否及如何参与 AlgU-MucAcyto 的 ClpX/ClpP 递送此前完全未知。
- **精确研究问题**：Can the AlgU-MucAcyto interface tolerate multi-site alanine substitutions while maintaining complex formation, and does SspB serve as a dual-interface adaptor bridging the preassembled AlgU-MucAcyto complex to ClpX/ClpP?

## 04 背景与发展脉络

**注：以下脉络基于本文引文及作者论述，属「仅本文框架」，未经外部系统核验。**

1. **σ^ECF-抗 sigma 因子互作的结构研究（~2000s-2010s）**
   - 代表：E. coli RpoE-RseA 复合物结构（PDB 1OR7）
   - 优点：揭示了 σ^ECF 被抗 sigma 因子"包裹"的通用模式
   - 局限：单一物种、单一复合物状态，缺乏对界面冗余性的系统分析

2. **MucA-RIP 通路研究（~1990s-2020s）**
   - 代表：AlgW、MucP、ClpX/ClpP 依次切割 MucA 的模型
   - 优点：建立了 MucA 降解的蛋白酶级联框架
   - 局限：适配器蛋白的角色不明确；AlgU-MucAcyto 复合物如何被识别未知

3. **AlgU-MucAcyto 结构解析（2020，PDB 6IN7）**
   - 代表：本文作者前期工作
   - 优点：首次获得 AlgU-MucAcyto 复合物结构
   - 局限：表达产量低，无法进行系统突变分析

4. **本文位置**：在 6IN7 基础上，通过融合蛋白策略突破表达瓶颈，获得更高分辨率结构（2.1 Å），系统验证界面残基功能，并首次鉴定 SspB 为连接 AlgU-MucAcyto 与 ClpX/ClpP 的适配器，填补了 MucA-RIP 通路中"底物如何被递送至蛋白酶"的关键空白。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| AlgU 与 MucA 单独表达产量低 | 无法获得足量高纯度蛋白用于结晶 | 两者单独表达时不稳定，可能因暴露疏水表面或快速降解 | Results 节 "Overcoming low-yield expression" 段落 |
| 界面残基功能未知 | 不清楚哪些残基驱动结合、哪些维持稳定性 | 缺乏系统突变分析；单点突变不足以破坏冗余网络 | Results 节 "Critical residues" 段落 |
| SspB 在 MucA-RIP 中的角色未知 | 无法解释 AlgU-MucAcyto 如何被 ClpX/ClpP 识别 | 此前研究聚焦蛋白酶本身，未考虑适配器蛋白 | Results 节 "SspB acts as a potential adaptor" 段落 |
| 多突变体结合仍不被破坏 | 三连/六连突变均无法破坏结合 | 界面存在高度冗余的电荷互补网络 | Results 图 4A-B；DSF 数据 |
| 热稳定性与结合解耦 | 突变体结合正常但 Tm 显著降低 | 界面残基同时承担"结合"与"结构刚性"双重角色 | Results 图 4B；图 S8 |

## 06 核心思想

### 1) 表面方法
- 融合蛋白表达策略（AlgU-H3H-MucAcyto，含 HRV 3C 切割位点）解决低产量问题
- X 射线晶体学解析复合物结构（2.1 Å）
- 多站点突变 + pull-down + DSF 热稳定性分析
- AlphaFold3 模拟 SspB-AlgU-MucAcyto-ClpX/ClpP 四元复合物
- BLI 定量测量 SspB 与各组分亲和力

### 2) 核心洞察
- **结合冗余性**：AlgU-MucAcyto 界面由大面积电荷互补网络驱动，单点甚至六连突变均不足以破坏结合——这是进化上的"防误激活"策略
- **稳定性-结合解耦**：界面残基虽对结合冗余，但对维持复合物热稳定性至关重要——"binding-redundant yet stability-essential"
- **SspB 双界面适配器**：SspB 的 N 端结构域识别 AlgU 发夹表面（而非 MucA），C 端无序尾结合 ClpX，从而将整个复合物递送至蛋白酶——这解释了为何 MucA 的 C 端延伸虽不进入 ClpX 孔道，仍能被有效降解

### 3) 可能的普适教训 [Analysis]
- 蛋白质互作界面的"冗余性"设计可能是 TF-调控因子互作的普遍策略，防止单点突变导致异常激活——对 TF-DNA 互作研究提示：DNA 结合域的多点接触也可能存在类似冗余
- 融合蛋白策略可推广至其他难以共表达/共纯化的蛋白复合物
- AlphaFold3 预测 + BLI 验证的组合可作为"结构预测-定量验证"的标准流程

## 07 方法总览

- **输入**：AlgU 全长、MucAcyto（1-80）、SspB、ClpX 的基因序列；PDB 6IN7 结构
- **输出**：AlgU-MucAcyto 复合物晶体结构（PDB 8Z6G）；SspB 与各组分结合亲和力（Kd）；突变体热稳定性数据
- **模块**：
  1. 基因敲除与表型分析（ΔalgU 菌株构建）
  2. 融合蛋白表达与纯化（AlgU-H3H-MucAcyto）
  3. 晶体筛选与结构解析（X 射线衍射，2.1 Å）
  4. 结构分析与界面鉴定（PDBePISA）
  5. 定点突变 + pull-down（结合功能验证）
  6. DSF 热稳定性分析
  7. AlphaFold3 四元复合物建模
  8. BLI 亲和力定量
- **训练**：不适用（无机器学习模型训练）
- **反馈回路**：结构预测（AlphaFold3）→ 突变设计 → 实验验证（pull-down/BLI）→ 修正模型
- **文字流程**：先通过基因敲除确认 AlgU 表型 → 融合蛋白表达获得复合物 → 结晶解析结构 → 基于结构设计突变 → pull-down 验证结合冗余性 → DSF 验证稳定性 → AlphaFold3 预测 SspB 结合模式 → BLI 定量验证 → 整合提出 SspB 双界面适配器模型

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 融合蛋白表达系统 | 解决 AlgU/MucA 单独表达产量低的问题 | 获得足量复合物用于结晶 | 输入：AlgU-MucAcyto 融合基因；输出：高纯度复合物 | Results 节 "Overcoming low-yield expression"；SEC 共洗脱 | 预期：无法获得晶体（实测：融合策略成功） |
| X 射线晶体学 | 解析复合物原子分辨率结构 | 揭示界面残基和相互作用网络 | 输入：复合物晶体；输出：2.1 Å 结构（PDB 8Z6G） | Results 图 2B-D | 预期：无法进行后续理性突变设计 |
| 多站点突变 + pull-down | 测试界面残基对结合的功能贡献 | 区分"结合必需"与"结合冗余"残基 | 输入：突变体库；输出：结合有无 | Results 图 4A-B | 预期：无法证明结合冗余性 |
| DSF 热稳定性 | 评估突变对复合物稳定性的影响 | 揭示"稳定性必需"残基 | 输入：突变体蛋白；输出：Tm 值 | Results 图 4B；图 S8 | 预期：无法发现结合-稳定性解耦 |
| AlphaFold3 建模 | 预测 SspB-AlgU-MucAcyto-ClpX/ClpP 四元复合物 | 提供 SspB 结合模式的原子模型 | 输入：蛋白序列；输出：预测复合物结构 | Results 图 5D | 预期：无法指导 SspB 突变设计 |
| BLI 定量 | 测量 SspB 与各组分亲和力 | 验证双界面适配器模型 | 输入：SspB 与 AlgU-MucAcyto/ClpX；输出：Kd 值 | Results 图 6B-D | 预期：无法定量支持双界面模型 |

## 09 关键公式符号

**不适用**。本文为结构生物学研究，无核心数学公式。涉及的关键定量参数包括：
- RMSD（均方根偏差）：结构比对指标，本文中 AlgU-MucAcyto 与 6IN7 比对 RMSD = 0.01 Å（253 Cα 原子）
- ΔiG（溶剂化自由能变化）：-28.6 kcal/mol（PDBePISA 计算）
- Kd（解离常数）：SspB-AlgU-MucAcyto = 5.551 × 10⁻⁸ M；SspB-ClpX = 2.683 × 10⁻⁸ M；突变体 Kd 值变化见 Results 图 6

## 10 实验设计与证据链

**数据集/群体**：
- P. aeruginosa PAO1 和 PA14 菌株（野生型及 ΔalgU 突变体）
- 重组蛋白：AlgU-MucAcyto 复合物（野生型及突变体）、SspB、ClpX

**指标**：
- 结构分辨率（2.1 Å）、Rfree/Rwork（0.244/0.217）
- 结合亲和力（Kd，BLI）
- 热稳定性（Tm，DSF）
- 表型：藻酸盐、绿脓菌素、pyoverdine 产量；细胞侵袭能力

**基线/对照**：
- 野生型 AlgU-MucAcyto 复合物（pull-down 阳性对照）
- 已知结构 PDB 6IN7（结构比对）
- E. coli RpoE-RseAcyto（PDB 1OR7，跨物种结构比较）

**预算/仪器**：
- 上海同步辐射光源（SSRF）BL18U/BL19U 线站
- GatorPrime（BLI 仪器）
- QuantStudio 5 实时 PCR 系统（DSF）

**oracle 输入**：不适用（无 AI 模型训练）

**评测协议**：pull-down 结合实验、DSF 热稳定性、BLI 动力学/亲和力测定

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| ΔalgU 表型分析 | AlgU 调控多种毒力因子 | WT vs ΔalgU vs 互补株 | 藻酸盐显著降低；绿脓菌素略降；pyoverdine 无显著变化；侵袭能力增强 | AlgU 参与藻酸盐合成和细胞侵袭调控 | 不能确定 AlgU 直接调控这些基因 | Results 图 1C-F |
| 融合蛋白表达与 SEC | 融合策略可获得稳定复合物 | 切割前后 SEC 图谱 | 切割前后共洗脱，图谱一致 | AlgU 与 MucAcyto 形成稳定复合物 | 不能排除切割后构象变化 | Results 图 2A；图 S3 |
| 晶体结构解析 | 获得高分辨率复合物结构 | 与 6IN7 比对 | RMSD = 0.01 Å（253 Cα） | 结构可靠，与已知结构一致 | 不能说明溶液态与晶态完全一致 | Results 图 2B-D；图 S5A |
| 三连/六连突变 + pull-down | 界面残基对结合非必需 | WT vs 突变体 | 所有突变体均保持结合 | 界面存在高度冗余 | 不能排除这些残基在体内有其他功能 | Results 图 4A-B |
| DSF 热稳定性 | 界面残基对稳定性必需 | WT vs 突变体 | 突变体 Tm 显著降低 | 结合与稳定性解耦 | 不能确定 Tm 降低的生理后果 | Results 图 4B；图 S8 |
| SspB pull-down | SspB 结合 AlgU-MucAcyto 和 ClpX | SspB + 各组分 | SspB 与两者均结合 | SspB 是双界面适配器 | 不能排除其他适配器存在 | Results 图 5A-C |
| BLI 亲和力 | 定量 SspB 结合强度 | WT vs 突变体 | Kd 从 5.551×10⁻⁸ 升至 1.997×10⁻⁷ M | 界面突变削弱但未消除 SspB 结合 | 不能确定体内降解效率变化 | Results 图 6B-D |
| AlphaFold3 建模 | 预测四元复合物结构 | 预测 vs 实验 | 模型显示 SspB N 端结合 AlgU 发夹，C 端尾结合 ClpX | 提供结构框架 | 预测模型未经实验验证 | Results 图 5D |

## 11 结论正确解读

- **任务范围**：本文仅研究了 AlgU-MucAcyto 复合物的体外结合与稳定性，以及 SspB 的体外结合能力。未进行体内降解实验或 ΔsspB 菌株表型分析。
- **oracle/真值输入**：AlphaFold3 预测为计算模型，未经冷冻电镜或共结晶实验验证；SspB-AlgU-MucAcyto-ClpX 三元复合物的原子结构未解析。
- **端到端状态**：非端到端。结构解析（实验）+ 互作验证（实验）+ 复合物建模（计算）为分步完成。
- **算力成本**：未提供。
- **历史数据依赖**：依赖 PDB 6IN7 结构作为比对参考；AlphaFold3 预测依赖其训练数据。
- **模型依赖**：AlphaFold3 预测结果未经独立实验验证。
- **最难情形**：六连突变仍不能破坏结合，说明该界面极难通过点突变扰动——这对设计干扰肽或小分子抑制剂构成挑战。
- **群体/领域边界**：结论基于 P. aeruginosa PAO1/PA14 菌株及体外重组蛋白，不能直接推广至其他细菌物种或体内条件。
- **不确定性**：SspB 介导降解的体内证据缺失；MucAcyto C 端延伸如何被 ClpX 识别并易位至 ClpP 的分子机制仍不明确。

**有边界的复述**：在体外条件下，AlgU-MucAcyto 复合物界面由冗余的电荷网络驱动结合，关键残基维持热稳定性；SspB 通过 N 端结构域识别 AlgU 发夹表面、C 端尾结合 ClpX，具备作为双界面适配器将复合物递送至 ClpX/ClpP 的生化能力。体内功能验证尚待开展。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 互补实验的剂量问题 | 多拷贝质粒 + IPTG 诱导可能超出生理水平 | 单拷贝染色体互补 | Discussion 节 |
| SspB 体内功能未验证 | 未进行 ΔsspB 菌株表型分析 | 结合 ΔsspB 表型分析与体外重建 ClpXP 降解实验 | Discussion 节 |
| AlphaFold3 模型未经实验验证 | 四元复合物为计算预测 | 共结晶或冷冻电镜验证 | Discussion 节 |
| 突变体非天然组合 | 三连/六连突变是系统扰动工具，不代表天然变异 | 染色体水平突变 + 表型分析 | Discussion 节 |
| 体外结合 ≠ 体内功能 | pull-down/BLI 证明结合能力，未证明体内降解效率 | 体内降解动力学实验 | Discussion 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 融合蛋白策略可能改变界面构象 | 连接肽可能引入人为约束，影响界面几何 | 结构生物学结论的可靠性取决于样品是否代表天然状态 | 比较融合蛋白与分别表达共组装复合物的 SAXS 或负染电镜 | Results 图 2A；图 S3 |
| "结合冗余"结论基于体外 pull-down | 体内条件下，局部浓度、竞争因子可能放大突变效应 | 体外冗余可能不代表体内冗余 | 在 ΔalgU 菌株中表达突变体，检测表型恢复程度 | Results 图 4A-B |
| SspB 结合实验未排除非特异性 | pull-down 中 SspB 可能通过非特异性静电结合 | 适配器特异性是模型成立的前提 | 使用 SspB 结构域截短突变体 + 竞争实验 | Results 图 5A-C |
| AlphaFold3 预测的置信度未报告 | 未提供 pLDDT 或 PAE 分数 | 预测模型的可靠性无法评估 | 检查 AlphaFold3 输出置信度指标 | Results 图 5D |
| DSF Tm 降低的机制未阐明 | 突变可能通过去折叠而非界面破坏降低 Tm | "稳定性必需"的分子机制不清晰 | 圆二色谱或氢氘交换质谱分析突变体构象 | Results 图 4B |
| 未检测 SspB 是否影响 ClpX 的 ATPase 活性 | 适配器可能不仅递送底物，还激活蛋白酶 | 可能遗漏 SspB 的催化性功能 | 体外 ClpX ATPase 活性测定 | Discussion 节 |

## 14 学到什么

**Agent 提炼的知识候选**

1. **融合蛋白策略解决难表达复合物**：AlgU-H3H-MucAcyto 融合表达 + HRV 3C 切割，可迁移至 TF-DNA 复合物中难以单独表达的组分（如不稳定的 TF 结构域与 DNA 结合域的共表达）。

2. **"结合冗余 vs 稳定性必需"的界面设计原则**：对 TF-DNA 互作研究提示，TF 的 DNA 结合界面可能同样存在多点冗余接触，单点突变不足以解释疾病相关 SNP 的功能影响——需系统评估突变对结合亲和力与复合物稳定性的解耦效应。

3. **双界面适配器模型**：SspB 通过 N 端结构域识别底物复合物、C 端无序尾结合蛋白酶——这一"双界面桥接"策略可迁移至研究 TF 如何被递送至降解机器（如泛素-蛋白酶体系统）或其他染色质修饰复合物。

4. **AlphaFold3 + BLI 的"预测-验证"闭环**：先用 AlphaFold3 生成互作模型，再通过 BLI 定量验证关键界面残基贡献——该流程可直接迁移至 TF-DNA 互作研究，用于预测 TF 突变对 DNA 结合的影响。

5. **多站点突变 + 热稳定性分析**：DSF 作为快速评估突变体稳定性的手段，可迁移至 TF 突变体库的功能筛选，区分"结合缺陷"与"折叠缺陷"突变。

6. **跨物种结构比较**：AlgU-MucAcyto 与 RpoE-RseAcyto 的结构比对（RMSD 2.529 Å）提示 σ^ECF-抗 sigma 因子互作模式保守——对 TF-DNA 研究提示，同一 TF 家族在不同物种中的 DNA 结合模式可能高度保守，可利用跨物种结构比对指导突变设计。

## 15 与已有知识连接

- **PDB 6IN7**：本文作者前期解析的 AlgU-MucAcyto 结构，本文在更高分辨率（2.1 Å vs 此前）下确认并扩展了界面分析。可交叉验证界面残基注释。
- **PDB 1OR7**：E. coli RpoE-RseAcyto 复合物结构，本文用于跨物种结构比较，支持 σ^ECF-抗 sigma 因子互作模式的保守性。
- **SspB 已知功能**：SspB 在 E. coli 中作为 ClpXP 的适配器，识别含 ssrA 标签的底物。本文发现 P. aeruginosa SspB 通过不同机制（识别 AlgU 而非 MucA 标签）工作，扩展了 SspB 适配器家族的功能谱。
- **MucA-RIP 通路**：此前研究（AlgW、MucP、ClpX/ClpP 级联）已建立，本文填补了"底物如何被递送至 ClpX/ClpP"的空白。
- **σ^ECF 调控的一般模型**：与 Mycobacterium tuberculosis 的 σ^E-RseA、E. coli 的 σ^E-RseA 等系统可进行跨物种比较，检验"结合冗余性"是否为 σ^ECF-抗 sigma 因子互作的普遍特征。
- **AlphaFold3 应用**：本文展示了 AlphaFold3 在蛋白-蛋白互作预测中的应用，与 AlphaFold2 在结构预测中的广泛应用形成衔接。

## 16 研究想法

**Agent 生成的研究候选**

### 候选 1：TF-DNA 界面"结合冗余性"的系统验证
- **名称**：TF-DNA 结合界面的突变冗余性图谱
- **来源局限/观察**：本文发现 AlgU-MucAcyto 蛋白界面存在结合冗余性；TF-DNA 界面是否同样冗余未知
- **核心假设**：TF 的 DNA 结合域中，直接接触碱基的残基对结合特异性的贡献存在冗余，单点突变不足以完全消除结合
- **初步方法**：选取一个已知结构的 TF-DNA 复合物（如 p53、GATA 家族），对界面残基进行饱和突变 + 高通量结合测定（如 MITOMI 或 HT-SELEX），结合 DSF 评估突变体稳定性
- **验证方式**：比较"结合丧失"与"稳定性丧失"突变的比例；与疾病相关突变数据库（如 ClinVar）交叉比对
- **创新状态**：unverified

### 候选 2：TF 降解适配器的双界面桥接模型
- **名称**：真核 TF 的泛素-蛋白酶体递送适配器鉴定
- **来源局限/观察**：SspB 通过双界面（N 端识别底物、C 端结合 ClpX）桥接底物与蛋白酶；真核 TF 降解是否依赖类似适配器未知
- **核心假设**：真核细胞中存在识别 TF 复合物并桥接泛素连接酶的适配器蛋白
- **初步方法**：以应激响应 TF（如 HIF-1α 或 p53）为模型，进行 proximity labeling（TurboID）结合质谱鉴定候选适配器；用 AlphaFold3 预测候选适配器与 TF 的互作模式
- **验证方式**：siRNA 敲低候选适配器后检测 TF 降解速率；体外重建泛素化-降解体系
- **创新状态**：unverified

### 候选 3：融合蛋白策略用于 TF-DNA 共结晶
- **名称**：TF-DNA 复合物的融合表达结晶策略
- **来源局限/观察**：本文融合蛋白策略解决了蛋白复合物表达难题；TF-DNA 复合物结晶常受限于 TF 溶解度或 DNA 结合亲和力
- **核心假设**：将 TF 与 DNA 结合域融合表达可提高复合物稳定性，利于结晶
- **初步方法**：选取难结晶的 TF-DNA 复合物，设计 TF-DNA 结合域融合构建体（含柔性连接肽），表达纯化后尝试结晶
- **验证方式**：与分别表达共组装方法比较结晶成功率与衍射质量
- **创新状态**：partially checked（本文在蛋白-蛋白复合物中验证，TF-DNA 场景未验证）

### 候选 4：σ^ECF 家族跨物种界面保守性分析
- **名称**：σ^ECF-抗 sigma 因子互作界面的进化保守性
- **来源局限/观察**：AlgU-MucAcyto 与 RpoE-RseAcyto 结构相似（RMSD 2.529 Å），但界面残基保守性未系统分析
- **核心假设**：σ^ECF-抗 sigma 因子互作界面的"结合冗余"残基在进化上保守，而"稳定性必需"残基可变
- **初步方法**：收集已解析的 σ^ECF-抗 sigma 因子复合物结构（PDB），进行界面残基的序列保守性分析（ConSurf），结合突变数据验证
- **验证方式**：预测保守残基的突变效应与实验数据（本文及文献）的一致性
- **创新状态**：unverified

### 候选 5：AlphaFold3 预测的置信度指标用于互作界面筛选
- **名称**：基于 AlphaFold3 置信度指标的 TF-共调控因子互作筛选
- **来源局限/观察**：本文使用 AlphaFold3 预测四元复合物但未报告置信度指标；AlphaFold3 的 pLDDT/PAE 可用于评估预测可靠性
- **核心假设**：AlphaFold3 的 PAE 分数可区分真实互作界面与假阳性接触
- **初步方法**：对一组已知 TF-共调控因子互作对（阳性）和随机蛋白对（阴性）进行 AlphaFold3 预测，提取界面残基的 pLDDT/PAE 特征，训练分类器
- **验证方式**：在独立测试集上评估分类器性能；用 BLI 或 pull-down 验证新预测的互作对
- **创新状态**：unverified