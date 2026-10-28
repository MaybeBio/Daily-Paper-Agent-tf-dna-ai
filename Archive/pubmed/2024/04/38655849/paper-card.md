## 01 基本信息

- **标题**：PURA syndrome-causing mutations impair PUR-domain integrity and affect P-body association
- **作者与单位**：Proske, Marcel; Janowski, Robert; Bacher, Sabrina; Kang, Hyun-Seo; Monecke, Thomas; Koehler, Tony; Hutten, Saskia; Tretter, Jana; Crois, Anna; Molitor, Lena; Donati, Elisa; De Fabritiis, Gianni; Dormann, Dorothee; Sattler, Michael; Niessing, Dierk（单位：Helmholtz Center Munich, Ludwig-Maximilians University Munich, 等，具体单位未逐一列出）
- **期刊/预印本平台**：eLife
- **年份**：2024
- **论文类型**：实验研究（结构生物学 + 细胞生物学 + 计算模拟）
- **领域**：结构生物学、神经发育疾病、RNA结合蛋白
- **关键词**：PURA syndrome, PUR domain, P-bodies, stress granules, X-ray crystallography, NMR, molecular dynamics
- **DOI/arXiv 号**：10.7554/eLife.93561
- **代码**：未提供
- **数据**：PDB 8CHT, 8CHU, 8CHV, 8CHW
- **阅读日期**：2026-05-13（按当前日期）
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：本文聚焦于转录因子/核酸结合蛋白 PURA 的 PUR 结构域，通过 X-ray 晶体学、NMR、MD 模拟和细胞实验，揭示疾病突变如何破坏结构域完整性和 P-body 定位。对 TF-DNA 互作课题的可迁移点在于：① 展示了如何用实验结构 + MD 模拟评估点突变对结构域稳定性的影响；② 揭示了结构域柔性（conformational promiscuity）如何使蛋白对突变敏感；③ 提供了从结构到细胞定位的功能验证范式。

---

## 02 一句话总结

本文通过解析人 PURA 蛋白 N-端和 C-端 PUR 结构域的晶体结构，结合 MD 模拟、NMR 和细胞定位实验，证明 PURA 综合征致病突变通过破坏 PUR 结构域折叠完整性（而非仅影响核酸结合）导致 P-body 定位受损，并解释了为何几乎所有突变都导致完全外显的疾病表型。

---

## 03 研究问题

- **具体问题**：为什么 PURA 基因上几乎所有突变（包括保守性替换）都导致完全外显的 PURA 综合征，而缺乏良性多态性？这些突变如何影响 PURA 蛋白的结构和功能？
- **为什么重要**：PURA 综合征是一种严重的神经发育障碍，理解其分子机制有助于诊断、预后和潜在治疗策略的开发。此外，PURA 是核酸结合蛋白，其机制可能推广到其他 PC4-fold 蛋白家族。
- **现有方法不足**：此前仅有基于果蝇同源蛋白的晶体结构和基于同源建模的 in silico 预测，缺乏人源蛋白的实验结构；且以往研究未将结构效应与细胞定位（P-body/stress granule）联系起来。
- **精确的「Can ... ?」问题**：Can experimentally determined human PURA structures, combined with MD simulations and cellular assays, explain why nearly all PURA mutations cause full-penetrance disease and distinguish pathogenic from benign variants?

---

## 04 背景与发展脉络

（标注：以下脉络为「经外部核验」——基于本文引用及领域常识）

1. **PURA 蛋白发现与功能研究（1990s–2000s）**：PURA 作为 purine-rich element 结合蛋白被发现，参与转录调控、mRNA 运输等（Bergemann and Johnson, 1992; Haas et al., 1993, 1995）。
2. **PURA 综合征的临床定义（2014）**：两个独立研究组报道 PURA 基因突变导致神经发育障碍（Hunt et al., 2014; Lalani et al., 2014），此后大量患者突变被报道。
3. **果蝇 PURA 结构解析（2009–2016）**：Graebsch 等解析了果蝇 PURA 的 N-端和 C-端 PUR 结构域晶体结构（PDB: 3k44, 5FGO），揭示了 PC4-fold 拓扑（β-β-β-β-α-linker-β-β-β-β-α）。
4. **基于同源建模的突变效应预测（2018）**：Reijnders 等基于果蝇结构构建人源同源模型，尝试预测突变对结构的影响，但缺乏实验验证。
5. **本文（2024）**：首次解析人源 PURA 结构域晶体结构，结合 MD、NMR、细胞实验，系统评估突变效应，提出「结构域完整性受损 → P-body 定位异常」的机制。

**本文主张的位置**：填补了从果蝇结构到人源结构的空白，将结构生物学与细胞定位联系起来，为突变致病性评估提供了实验框架。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 突变致病性预测困难 | 几乎所有 PURA 突变都导致完全外显疾病，缺乏良性多态性 | PUR 结构域具有构象柔性（promiscuity），即使表面突变也能通过改变折叠状态影响功能 | Results 图 5B–E；Discussion 节 |
| 人源结构缺失 | 此前仅有果蝇同源结构，人源与果蝇序列一致性仅 46% | 缺乏人源实验结构，无法准确评估突变效应 | Introduction 节；Results 图 3A |
| 结构预测与功能脱节 | 以往 in silico 预测未与细胞功能（P-body/stress granule 定位）关联 | 缺乏从结构到细胞定位的完整证据链 | Results 图 1–2；Discussion 节 |
| 表面突变效应被低估 | K97E 位于表面，但导致显著功能缺陷 | 表面突变可通过影响结构域动态和折叠状态（而非仅破坏疏水核心）致病 | Results 图 5；Discussion 节 |
| 突变体蛋白难以重组表达 | R199P、I206F、F233del、R245P 等突变体在 E. coli 中不溶 | 突变破坏结构域折叠，导致蛋白聚集/不溶 | Results 节；Supplementary file 1a |

---

## 06 核心思想

**1) 表面方法**：
- 解析人 PURA N-端（PURA I–II）和 C-端（PURA III）结构域的晶体结构
- 对致病突变体（K97E、R140P 等）进行重组表达、纯化、晶体学、CD、NMR 和 MD 模拟
- 在 HeLa 细胞中检测野生型和突变型 PURA 的 P-body 和 stress granule 定位
- 用 nanoBRET 检测突变对二聚化的影响

**2) 核心洞察**：
- PUR 结构域具有异常的构象柔性（conformational promiscuity），其 β-sheet 边缘和 loop 区域在晶体不对称单元中呈现多种构象
- 这种柔性使 PURA 对突变高度敏感：即使是表面突变（如 K97E）也能通过改变 β-sheet 的 register（移位 1–2 个氨基酸）导致结构域部分重折叠
- 结构域完整性受损 → 核酸结合/解链活性下降 → P-body 定位受损，而 stress granule 定位相对保留
- 这解释了为何 PURA 突变几乎全部致病：结构域柔性意味着「容忍突变」的空间很小

**3) 可能的普适教训 [Analysis]**：
- 对 TF-DNA 互作研究：评估突变效应时，不能仅看突变位点是否位于结合界面或疏水核心，还需考虑结构域的内在动力学和折叠能垒。MD 模拟和 NMR 可以捕捉到晶体结构无法显示的构象状态。
- 对 AI 结构预测：AlphaFold 等预测的静态结构可能低估蛋白的构象异质性，对「柔性区域突变」的致病性预测需谨慎。

---

## 07 方法总览

- **输入**：人 PURA 蛋白片段（PURA I–II: E57–E212；PURA III: P215–K280）、致病突变体（K97E、R140P、I206F、F233del、R245P）、m11 核酸结合缺陷突变体
- **输出**：晶体结构（4 个 PDB 条目）、突变体表达/溶解性表型、RNA 结合亲和力、DNA 解链活性、P-body/stress granule 共定位定量、二聚化能力（nanoBRET）
- **模块**：
  1. 重组蛋白表达与纯化（E. coli）
  2. X-ray 晶体学（结构解析）
  3. EMSA（RNA 结合）
  4. 荧光解链实验（dsDNA unwinding）
  5. CD 光谱（二级结构）
  6. NMR HSQC（溶液态构象比较）
  7. MD 模拟（构象动力学）
  8. 细胞实验（HeLa 稳定细胞系，免疫荧光共定位）
  9. nanoBRET（二聚化检测）
- **流程**：先解析 WT 结构 → 选择代表性突变体 → 表达测试（发现多个突变体不溶）→ 对可溶突变体做功能/结构表征 → 细胞定位实验 → MD 模拟解释构象变化 → 综合提出机制模型

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| X-ray 晶体学（WT PURA I–II, III） | 提供人源结构基准 | 此前无人源结构，无法准确评估突变 | 输入：纯化蛋白；输出：1.7–2.15 Å 结构 | Results 图 3A, 4A；Supplementary file 1b | 失去结构基准，所有突变效应分析失去参照 |
| 重组表达测试 | 快速评估突变对折叠的影响 | 多个突变体不溶，提示折叠缺陷 | 输入：突变体质粒；输出：可溶/不溶表型 | Results 节；Supplementary file 1a | 无法区分「折叠缺陷」与「功能缺陷」突变 |
| EMSA | 定量 RNA 结合能力 | 验证核酸结合是否受损 | 输入：蛋白+荧光 RNA；输出：结合曲线 | Results 图 4C, D | 无法判断结合缺陷是否由折叠问题导致 |
| 荧光解链实验 | 检测 dsDNA 解链活性 | PURA 具有解链酶活性，可能参与转录调控 | 输入：蛋白+双标记 DNA；输出：荧光信号 | Results 图 3D, E, 4E, F | 无法评估功能后果 |
| CD 光谱 | 检测二级结构变化 | 初步判断突变是否改变整体折叠 | 输入：蛋白溶液；输出：CD 谱 | Results 图 5A | 无法定位具体结构变化区域 |
| NMR HSQC | 比较 WT vs K97E 溶液态构象 | 晶体结构可能捕捉不到溶液态差异 | 输入：15N 标记蛋白；输出：HSQC 谱 | Results 图 5F | 无法确认 K97E 的构象重排是否在溶液态存在 |
| MD 模拟 | 解释构象柔性和突变效应 | 实验结构显示多构象，MD 可揭示动态过程 | 输入：晶体结构；输出：RMSF、构象轨迹 | Results 图 5—figure supplement 3B | 无法从原子层面解释 K97E 的远距离效应 |
| 细胞定位实验（P-body/stress granule） | 将结构缺陷与细胞表型关联 | 建立从分子到细胞的功能证据链 | 输入：稳定细胞系；输出：共定位定量 | Results 图 1–2 | 无法判断结构缺陷的病理相关性 |
| nanoBRET | 检测二聚化 | C-端结构域介导二聚化，突变可能影响 | 输入：Halo/NLuc 融合蛋白；输出：mBU | Results 图 3F | 无法区分二聚化缺陷与折叠缺陷 |

---

## 09 关键公式符号

本文为实验结构生物学论文，无核心数学公式。MD 模拟部分使用标准力场（AMBER 14SB）和 RMSF 计算，但未给出具体公式。以下为隐含使用的标准定义：

- **RMSF（Root Mean Square Fluctuation）**：用于量化每个 Cα 原子的构象波动，公式为：
  \[
  \text{RMSF}_i = \sqrt{\frac{1}{T} \sum_{t=1}^{T} (r_i(t) - \bar{r}_i)^2}
  \]
  其中 \( r_i(t) \) 为原子 i 在时间 t 的坐标，\( \bar{r}_i \) 为平均坐标。用于比较 WT 与 K97E 的动力学差异（Results 图 5—figure supplement 3B）。

- **nanoBRET 比值**：mBU = (618 nm 发射 / 460 nm 发射) × 1000，用于定量二聚化效率（Methods 节）。

---

## 10 实验设计与证据链

**数据集/群体**：
- 蛋白：人 PURA 片段（WT、K97E、R140P、I206F、F233del、R245P、m11）
- 细胞：HeLa（稳定细胞系，免疫荧光）、HEK293（nanoBRET）
- 结构：4 个晶体结构（WT PURA I–II, WT PURA III, K97E, R140P）

**指标**：
- 蛋白溶解性（可溶/不溶）
- RNA 结合亲和力（EMSA 迁移率）
- dsDNA 解链活性（荧光强度变化）
- CD 谱（二级结构含量）
- HSQC 谱峰位移/消失
- P-body/stress granule 共定位比率
- nanoBRET mBU 值

**评测协议**：
- 每个实验至少 3 次独立重复（EMSA、解链实验）
- 细胞实验用生物学重复 + 技术重复
- MD 模拟：10 个独立轨迹 × 100 ns（WT 和 K97E 各 1 µs 总时长）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| 重组表达测试 | 突变导致折叠缺陷 | WT vs 6 个突变体 | R199P、I206F、F233del、R245P 不溶；K97E、R140P 可溶 | 多数致病突变破坏折叠 | 不溶性不等于体内完全无功能 | Results 节；Supplementary file 1a |
| EMSA（RNA 结合） | K97E 影响核酸结合 | WT vs K97E vs R140P vs m11 | K97E 结合减弱；R140P 正常；m11 无结合 | K97E 部分损害 RNA 结合 | 结合减弱程度与致病性关系未定量 | Results 图 4C, D |
| 解链实验 | K97E 影响解链活性 | WT vs K97E vs R140P vs m11 | K97E 解链活性下降 90%；R140P 正常 | K97E 严重损害解链功能 | 解链活性与 P-body 定位的因果关系未直接证明 | Results 图 4E, F |
| CD 光谱 | K97E 改变二级结构 | WT vs K97E vs R140P | K97E 谱图异常；R140P 正常 | K97E 导致折叠改变 | CD 无法定位具体结构变化 | Results 图 5A |
| 晶体结构（K97E） | 揭示突变诱导的构象变化 | K97E vs WT | β5/β6 移位 1–2 个氨基酸；β-sheet register 改变 | K97E 诱导局部重折叠 | 晶体堆积可能放大构象差异 | Results 图 5B–E |
| NMR HSQC | 确认溶液态构象差异 | WT vs K97E | 多个 β-strand 区域峰位移/消失 | K97E 在溶液态也存在构象重排 | 未做完整主链归属，无法逐残基定位 | Results 图 5F |
| MD 模拟 | 支持构象柔性假说 | WT vs K97E | K97E 在 β5–β7 区域 RMSF 增加 | 突变增加局部动力学 | 模拟时间短（100 ns），可能未达平衡 | Results 图 5—figure supplement 3B |
| 细胞定位（P-body） | 突变影响 P-body 定位 | WT vs K97E vs F233del | K97E、F233del 的 P-body 共定位显著降低 | 突变损害 P-body 定位 | 未检测内源蛋白，仅过表达 | Results 图 2 |
| 细胞定位（stress granule） | 突变不影响 SG 定位 | WT vs K97E vs F233del | SG 共定位正常 | P-body 缺陷是特异性的 | 未做定量比较 | Results 图 1B, C |
| nanoBRET | 突变影响二聚化 | WT vs F233del vs R245P | F233del、R245P 二聚化显著降低 | C-端突变损害二聚化 | 未检测 K97E 的二聚化 | Results 图 3F |

---

## 11 结论正确解读

- **任务范围**：本文仅评估了 6 个代表性突变体（K97E、R140P、I206F、F233del、R199P、R245P），而非全部 270+ 已知突变。结论的推广需谨慎。
- **oracle/真值输入**：致病性分类来自 ClinVar 和文献报道，非本文独立验证。
- **端到端状态**：本文建立了「结构 → 功能 → 细胞定位」的证据链，但未做动物模型或患者细胞验证，因此「P-body 缺陷导致疾病」仍是假说而非因果证明。
- **算力成本**：MD 模拟为 10×100 ns，属于中等规模，足以捕捉局部构象变化，但不足以观察大规模构象重排。
- **历史数据依赖**：依赖 ClinVar 和既往文献的致病性注释，这些注释本身可能包含错误。
- **模型依赖**：MD 模拟基于 AMBER 14SB 力场，结果受力场参数影响。
- **最难情形**：对「不确定意义」（VUS）突变（如 R140P）的判定是本文的亮点，但仅凭一个例子不足以建立通用分类标准。
- **群体/领域边界**：结论限于 PURA 蛋白和 PUR 结构域家族，不能直接推广到所有 PC4-fold 蛋白。
- **不确定性**：K97E 的构象重排是否在体内（而非晶体/高浓度溶液）发生，未直接验证。

**有边界的复述**：本文证明，在体外和过表达细胞模型中，PURA 综合征相关突变（特别是 K97E 和 C-端结构域突变）通过损害 PUR 结构域折叠完整性，导致核酸结合/解链活性下降和 P-body 定位受损，而 stress granule 定位相对保留。这为「结构域完整性缺陷」作为 PURA 综合征的通用机制提供了实验支持，但因果链的最终验证（P-body 缺陷 → 疾病表型）仍需动物模型或患者来源细胞的研究。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 仅测试了代表性突变 | 6 个突变体不能覆盖所有已知致病突变 | 未明确说明，但暗示需要更系统的突变扫描 | Results 节 |
| 过表达系统 | 实验在 HeLa 过表达体系中进行，非内源水平 | 未明确说明 | Results 图 1–2 相关描述 |
| MD 模拟时间尺度有限 | 100 ns 模拟不足以观察大规模构象变化 | 未明确说明 | Methods 节 |
| P-body 缺陷与疾病的因果关系未直接证明 | 未做动物模型或患者细胞验证 | 未明确说明 | Discussion 节 |
| R140P 的判定依赖单一案例 | 仅凭一个 VUS 突变体的功能正常来支持其良性 | 未明确说明 | Discussion 节 |
| 未做完整的 NMR 主链归属 | 无法逐残基定位 K97E 的构象变化 | 未明确说明 | Results 图 5F 相关描述 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| K97E 的构象重排仅在晶体中一个分子（chain B）观察到 | 晶体堆积可能放大或诱导构象差异；溶液态 NMR 虽显示差异但未做归属 | 如果构象重排是晶体伪影，则「折叠 promiscuity」假说被削弱 | 做 SAXS 或 SEC-MALS 比较 WT/K97E 的溶液态形状；或做更长 MD 模拟（µs 级）观察构象平衡 | Results 图 5B–F |
| P-body 定位实验仅用 FLAG 标签过表达 | 过表达可能掩盖或放大定位缺陷；FLAG 标签可能影响蛋白行为 | 需要确认内源 PURA 的定位是否也受影响 | 用 CRISPR 敲入内源标签或做内源抗体染色 | Results 图 2 |
| 「P-body 缺陷导致疾病」缺乏功能因果证据 | P-body 定位受损可能是伴随现象而非致病原因 | 如果 P-body 缺陷不是致病的，则治疗靶点可能错误 | 在 P-body 缺陷的细胞中回补 P-body 功能（如表达 PURA 突变体 + P-body 锚定序列）看是否能挽救表型 | Discussion 节 |
| R140P 被判定为「可能良性」仅基于功能实验 | 功能正常不等于完全良性；可能存在其他组织特异性效应 | 对 VUS 的临床解读需要多维度证据 | 做患者来源 iPSC 神经元或类器官验证 | Discussion 节 |
| MD 模拟未报告力场验证或收敛性分析 | 100 ns 可能不足以收敛；未报告 RMSD 随时间变化 | 模拟结论的可靠性取决于收敛性 | 检查模拟 RMSD 是否达到平台期；增加模拟时间或重复次数 | Methods 节（未提供细节） |
| 未检测 K97E 对 DNA 结合的影响 | 仅检测了 RNA 结合和解链活性，PURA 也结合 DNA | 如果 K97E 主要影响 DNA 结合，则机制解释不完整 | 用 EMSA 或荧光各向异性检测 dsDNA 结合 | Results 图 4C–F |

---

## 14 与已有知识连接

- **PURA 结构域家族**：本文结构与人 PURA 与果蝇 PURA（PDB: 3k44, 5FGO）高度相似，验证了 PC4-fold 的保守性。与 PC4-fold 蛋白家族（如 PC4、C1D）的核酸结合机制可类比（Janowski and Niessing, 2020 综述）。
- **TF-DNA 互作中的突变效应**：本文展示了「表面突变通过影响结构域动力学而非直接破坏结合界面」的机制，与 p53 DNA 结合域突变研究（如 Joerger & Fersht, 2010, Cold Spring Harb Perspect Biol）中的「结构稳定性突变」概念一致。
- **构象 promiscuity 与疾病**：本文的「折叠 promiscuity」概念与 intrinsically disordered proteins 的「fuzzy complexes」概念相关，但 PURA 是有序结构域，其 promiscuity 体现在 β-sheet register 的可变性。
- **P-body 与 RNA 代谢**：PURA 与 P-body 的关联（Molitor et al., 2023）提示 PURA 可能参与 mRNA 储存/降解的调控，与 TF 的转录调控功能形成互补。
- **AI 结构预测的局限**：本文作者指出，此前基于 AlphaFold 的突变效应预测（如 Dai et al., 2023; López-Rivera et al., 2023）使用了不完整的单体结构，忽略了二聚化和构象柔性，这为 AI 结构预测在疾病突变解读中的局限性提供了实验证据。

---

## 15 学到什么

**Agent 提炼的知识候选**：

1. **结构域柔性作为突变敏感性的通用指标**：评估 TF 突变致病性时，不能仅看突变位点是否在结合界面或疏水核心。PURA 的案例表明，结构域的内在构象柔性（β-sheet register 可变性）使表面突变也能致病。可迁移到其他 TF：对候选 TF 进行 MD 模拟，计算 apo 态的构象系综宽度，作为突变敏感性的预测指标。

2. **多构象晶体学 + MD 联合分析**：本文利用晶体不对称单元中多个分子的构象差异 + MD 模拟 RMSF，揭示了 WT 蛋白本身的构象异质性。方法可迁移：对 TF-DNA 复合物和 apo-TF 分别做晶体学 + MD，比较 DNA 结合如何改变构象系综。

3. **功能验证的层次化设计**：本文从「表达可溶性 → 核酸结合 → 解链活性 → 细胞定位 → 二聚化」逐层验证，每一层都提供独立证据。对 TF 突变研究，可设计类似层次：表达/折叠 → DNA 结合 → 转录激活 → 染色质定位 → 蛋白互作。

4. **区分「折叠缺陷」与「功能缺陷」突变**：本文发现 R199P、I206F、F233del、R245P 导致不溶性（折叠缺陷），而 K97E 可溶但功能受损（功能缺陷）。这种分类对 TF 突变研究有直接价值：不同突变类型可能需要不同的治疗策略（如化学伴侣 vs 功能补偿）。

5. **P-body 定位作为 TF 功能的新维度**：PURA 的 P-body 定位提示 TF 可能参与细胞质 RNA 代谢，而不仅是核内转录调控。对 TF 研究，可检查候选 TF 是否在应激条件下定位于 P-body/stress granule，这可能揭示非经典功能。

6. **对 AI 结构预测的验证策略**：本文明确批评了基于 AlphaFold 单体的突变预测，强调需要实验结构 + 二聚体 + 动力学信息。可迁移：对 AI 预测的 TF 结构，至少用 MD 或 SAXS 验证其构象稳定性，再用于突变解读。

---

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF 突变致病性的「构象脆弱性」预测框架
   - **来源局限/观察**：PURA 的 K97E 表面突变通过构象 promiscuity 致病，但现有 AI 工具（AlphaFold, ESM）无法预测此类效应
   - **核心假设**：TF 结构域的构象系综宽度（由 MD 模拟或 NMR 测量）与突变致病性正相关
   - **初步方法**：选取 10-20 个已知 TF（如 p53, MYC, FOXP3），对每个 TF 的致病/良性突变做 MD 模拟（µs 级），计算 apo 态 RMSF、构象态数量、折叠自由能面；用 ClinVar 标注训练分类器
   - **验证方式**：留一法交叉验证；对预测为「致病」但 ClinVar 标注 VUS 的突变做实验验证（表达、结合、细胞定位）
   - **创新状态**：unverified

2. **候选名称**：TF-DNA 结合诱导的构象选择 vs 诱导拟合的 MD 判别
   - **来源局限/观察**：PURA 的 N-端结构域在 apo 态呈现多种构象，DNA 结合可能选择特定构象（构象选择）而非诱导折叠
   - **核心假设**：TF 的 DNA 结合机制（构象选择 vs 诱导拟合）可通过比较 apo 态构象系综与 holo 态结构来判别
   - **初步方法**：对 5-10 个 TF（含 PURA），做 apo 态增强采样 MD（REMD, GaMD），提取主要构象态；与 holo 态晶体结构比较；计算构象态与 DNA 结合构象的相似度
   - **验证方式**：用 NMR CSP 或 smFRET 实验验证 MD 预测的构象态
   - **创新状态**：unverified

3. **候选名称**：TF 的 P-body 定位预测与功能注释
   - **来源局限/观察**：PURA 的 P-body 定位受损与疾病相关，但大多数 TF 的 P-body 定位未被系统研究
   - **核心假设**：TF 的 P-body 定位由特定序列/结构特征决定，且与疾病相关
   - **初步方法**：从文献和数据库收集 TF 的 P-body 定位数据；用序列特征（ intrinsically disordered regions, RGG motifs, low complexity domains）训练预测器；对预测定位的 TF 做实验验证
   - **验证方式**：免疫荧光共定位；P-body 敲除细胞中检测 TF 功能变化
   - **创新状态**：unverified

4. **候选名称**：基于实验结构的 TF 突变致病性分类器（优于 AlphaFold）
   - **来源局限/观察**：本文显示 AlphaFold 单体结构不足以预测 PURA 突变效应，实验结构 + 二聚体信息更可靠
   - **核心假设**：结合实验结构（或高质量 AF2 多聚体模型）+ MD 模拟的突变效应预测优于基于单体 AF2 的预测
   - **初步方法**：构建包含 PURA 及其他 PC4-fold 蛋白的突变数据集；对每个突变计算：ΔΔG（FoldX, Rosetta）、RMSF 变化、二聚体界面接触变化；训练梯度提升分类器
   - **验证方式**：在独立数据集上比较与 AlphaFold-based 方法（如 AlphaMissense）的 AUC
   - **创新状态**：unverified

5. **候选名称**：PURA 的 DNA 结合特异性与 P-body 定位的结构基础
   - **来源局限/观察**：本文未解析 PURA 与 DNA 的共晶结构，也未测试 DNA 结合对 P-body 定位的影响
   - **核心假设**：PURA 的 DNA 结合活性与其 P-body 定位功能解耦，或存在不同的核酸底物偏好
   - **初步方法**：解析 PURA I–II 与 ssDNA/dsDNA 的共晶结构；用 SELEX 或 RIP-seq 鉴定 PURA 的核酸底物；在 HeLa 中表达 DNA 结合缺陷但折叠正常的突变体，检测 P-body 定位
   - **验证方式**：共晶结构 + 细胞定位实验
   - **创新状态**：unverified