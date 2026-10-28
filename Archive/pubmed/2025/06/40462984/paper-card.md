## 01 基本信息

- **标题**：Reorganizing the RNA polymerase II complex for replication of an infectious noncoding RNA in vivo
- **作者**：Hao, Jie; Qin, Zhuan; Ma, Junfei; Qu, Jie; Wang, Yunhan; Folimonova, Svetlana Y; Liu, Bin; Li, Wenwei; Wang, Ying
- **单位**：未提供（bioRxiv 预印本未列出完整单位信息）
- **期刊/平台**：bioRxiv : the preprint server for biology
- **年份**：2025（预印本发布于 2025-06-04；DOI 记录显示 2025-05-12 提交）
- **论文类型**：预印本（preprint）
- **领域**：植物病毒学 / RNA 聚合酶转录机制 / 类病毒复制
- **关键词**：RNA polymerase II (Pol II)、RNA-dependent RNA polymerase (RdRP) activity、PSTVd (Potato spindle tuber viroid)、TFIIIA-7ZF、AlphaFold3、类病毒复制
- **DOI/arXiv 号**：10.1101/2025.05.12.653476
- **代码**：未提供
- **数据**：未提供（AlphaFold3 结构预测数据未公开）
- **阅读日期**：2025-06-10（基于预印本日期推算，实际阅读日期未记录）
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：本文聚焦 RNA 模板上的 Pol II 转录（RdRP 活性），而非经典 TF–DNA 结合。但其核心机制涉及 **TFIIIA-7ZF（一个含 7 个锌指结构域的转录因子）与 RNA 模板及 Pol II 大亚基 Rpb2 的协同互作**，且使用 **AlphaFold3 预测蛋白-RNA-蛋白三元复合物结构**。对本课题的可迁移点在于：① 锌指蛋白（ZF）作为核酸结合模块的序列-结构-功能关系；② AlphaFold3 在预测多组分核酸-蛋白复合物中的应用策略；③ 转录因子在非经典模板（RNA）上重编程 Pol II 特异性的机制。

---

## 02 一句话总结

本文通过体内实验证明 PSTVd 类病毒 RNA 复制时，12 亚基的 Pol II 被重组为 7 亚基形式（去除 Rpb4/5/6/7/9），并由剪接变体 TFIIIA-7ZF 介导其与 RNA 模板的结合，AlphaFold3 预测及实验验证表明 TFIIIA-7ZF 的 N 端结合 PSTVd 左端结构域、C 端结合 Rpb2，且 PSTVd loop 8 的柔性弯曲对该互作至关重要。

---

## 03 研究问题

- **具体问题**：DNA 依赖的 RNA 聚合酶（DdRP）如何获得 RNA 依赖的 RNA 聚合酶（RdRP）活性，从而在体内以 RNA 为模板进行转录？具体到 PSTVd 类病毒，其复制依赖宿主 Pol II，但 Pol II 如何被重编程以识别 RNA 模板的分子机制未知。
- **为什么重要**：类病毒（viroids）是已知最小的感染性非编码 RNA，其复制完全依赖宿主酶。理解 Pol II 的 RdRP 活性机制不仅揭示宿主-病原互作的新层面，也可能为 RNA 病毒复制、非编码 RNA 代谢提供普适原理。
- **现有方法不足**：此前研究多聚焦于 Pol II 的 DNA 模板转录机制，对 RNA 模板上的 Pol II 组织方式缺乏结构信息；体外重构 RdRP 活性困难；缺乏体内证据表明 Pol II 亚基组成在 RNA 模板上发生改变。
- **精确研究问题**：Can the 12-subunit Pol II complex be reorganized into a 7-subunit form in vivo to support PSTVd RNA-templated transcription, and does TFIIIA-7ZF bridge the remodeled Pol II to the PSTVd RNA template via specific structural elements?

---

## 04 背景与发展脉络

*注：以下脉络基于本文引言及引用，标注为「仅本文框架」——未逐一核验外部文献。*

1. **阶段一：发现 DdRP 的 RdRP 活性**（~1980s-1990s）
   - 代表：类病毒复制依赖宿主核酶；HDV 利用 Pol II 复制。
   - 优点：确立了 RdRP 活性的生物学重要性。
   - 局限：分子机制完全未知。

2. **阶段二：体外生化重构尝试**（~2000s-2010s）
   - 代表：纯化 Pol II 在体外以 RNA 为模板的延伸实验。
   - 优点：证明 Pol II 具有内在 RdRP 活性。
   - 局限：效率极低，缺乏体内相关性；无法解释模板特异性。

3. **阶段三：宿主因子筛选**（~2010s-2020s）
   - 代表：酵母双杂交、遗传筛选鉴定类病毒复制相关宿主蛋白。
   - 优点：发现 TFIIIA 等宿主因子参与。
   - 局限：缺乏结构解释；未阐明 Pol II 亚基组成是否变化。

4. **阶段四：结构预测与体内验证**（本文位置，2025）
   - 代表：AlphaFold3 预测 Pol II-RNA-TFIIIA-7ZF 三元复合物；体内亚基缺失实验。
   - 优点：首次提出 Pol II 在体内以 7 亚基形式行使 RdRP 功能；提供结构模型。
   - 局限：预印本未经同行评审；结构预测未经实验验证（如冷冻电镜）。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Pol II 亚基组成在 RNA 模板上是否改变 | 12 亚基 Pol II 是否全部参与 PSTVd 转录未知 | 作者提出 Rpb4/5/6/7/9 不参与 PSTVd 转录，Pol II 被重组为 7 亚基 | Abstract 及 Results（具体图未提供） |
| TFIIIA 在类病毒复制中的角色模糊 | 此前仅知 TFIIIA 与 PSTVd RNA 结合，但机制不清 | 作者提出剪接变体 TFIIIA-7ZF 作为桥接因子，N 端结合 RNA、C 端结合 Rpb2 | Abstract；Results（图未提供） |
| RNA 模板上 Pol II 复合物的结构未知 | 缺乏 Pol II-RNA-辅助因子复合物的原子模型 | AlphaFold3 预测提供结构模型，但未经实验验证 | Abstract；Results（结构预测部分） |
| PSTVd RNA 结构元件对互作的功能贡献 | loop 8 的柔性是否影响 TFIIIA-7ZF 结合未知 | 作者提出 loop 8 弯曲是结合所必需，刚性双链替换破坏互作 | Abstract；Results（loop 8 替换实验） |

---

## 06 核心思想

### 1) 表面方法
- 在植物体内（in planta）进行 PSTVd 转录实验，通过亚基缺失/敲低验证哪些 Pol II 亚基参与。
- 鉴定 TFIIIA-7ZF 剪接变体为关键辅助因子。
- 使用 AlphaFold3 预测 Pol II（7 亚基）-PSTVd RNA-TFIIIA-7ZF 三元复合物结构。
- 通过 loop 8 替换实验验证结构预测的功能相关性。

### 2) 核心洞察
- **Pol II 的亚基组成是可塑的**：在 RNA 模板上，Pol II 不需要全部 12 个亚基，而是以 7 亚基核心形式行使 RdRP 功能。这打破了「Pol II 必须以全酶形式工作」的假设。
- **TFIIIA-7ZF 是双功能桥接因子**：其 N 端 7 个锌指结构域识别 PSTVd RNA 左端结构域，C 端与 Rpb2 互作，从而将 Pol II 招募到 RNA 模板上。这类似于 TFIIIA 在 5S rRNA 基因上的 DNA 结合功能，但模板从 DNA 切换为 RNA。
- **RNA 结构柔性是功能关键**：PSTVd loop 8 的弯曲构象（而非刚性双链）是 TFIIIA-7ZF 结合所必需，提示 RNA 模板的结构动态性在 Pol II 识别中起决定性作用。

### 3) 可能的普适教训 [Analysis]
- 转录因子的功能可能超越 DNA 模板：同一锌指蛋白家族可通过不同结构域组合识别 DNA 或 RNA，提示「转录因子」的命名可能过于狭窄。
- 聚合酶复合物的亚基组成可能随模板类型动态调整，这为理解其他非经典转录（如 RNA 病毒复制、端粒酶）提供新视角。
- AlphaFold3 在多组分核酸-蛋白复合物预测中的成功（即使未经实验验证）表明，AI 结构预测可作为生成可检验假设的强有力工具，但功能验证仍不可或缺。

---

## 07 方法总览

- **输入**：PSTVd 感染植物组织；Pol II 各亚基的基因序列；TFIIIA-7ZF 序列；PSTVd RNA 序列及二级结构。
- **输出**：① 参与 PSTVd 转录的 Pol II 亚基清单；② TFIIIA-7ZF-PSTVd-Pol II 三元复合物的预测结构；③ loop 8 功能验证结果。
- **模块**：
  1. 体内转录实验（in planta）：检测 PSTVd RNA 积累水平，评估各 Pol II 亚基缺失的影响。
  2. 蛋白-RNA 互作分析：验证 TFIIIA-7ZF 与 PSTVd RNA 的结合。
  3. AlphaFold3 结构预测：生成三元复合物模型。
  4. 结构-功能验证：loop 8 替换突变体实验。
- **训练**：不适用（无新模型训练；AlphaFold3 为已有工具）。
- **工具**：AlphaFold3（结构预测）；植物体内表达系统（具体物种未提供）。
- **反馈回路**：结构预测 → 设计突变体 → 功能验证 → 修正模型。
- **假设**：① Pol II 亚基缺失不影响细胞活力（或可补偿）；② AlphaFold3 预测的复合物构象接近体内真实状态；③ loop 8 替换不影响 PSTVd RNA 整体折叠。

**文字流程**：首先在植物体内验证 PSTVd 复制依赖 Pol II，并通过亚基缺失实验确定 7 亚基核心形式 → 鉴定 TFIIIA-7ZF 为关键因子并验证其与 PSTVd RNA 结合 → 用 AlphaFold3 预测三元复合物结构 → 基于预测设计 loop 8 刚性替换突变体 → 检测突变体对 TFIIIA-7ZF 结合及 PSTVd 复制的影响 → 得出结论。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Pol II 亚基缺失实验 | 确定参与 PSTVd 转录的亚基 | 验证 12→7 亚基重组假说 | 输入：各亚基敲低/缺失植株；输出：PSTVd RNA 水平 | Abstract 明确 Rpb4/5/6/7/9 不参与 | 若移除该模块，无法证明亚基重组（实测消融效应：未提供具体数据） |
| TFIIIA-7ZF 鉴定与结合验证 | 确认剪接变体为辅助因子 | 建立 Pol II-RNA 互作的桥梁 | 输入：TFIIIA 剪接变体；输出：与 PSTVd RNA 结合证据 | Abstract 提及 7ZF 变体 | 若移除，无法解释 Pol II 如何识别 RNA 模板（预期效应） |
| AlphaFold3 结构预测 | 生成三元复合物模型 | 提供原子级互作界面假设 | 输入：序列；输出：预测结构 | Abstract 提及预测结果 | 若移除，缺乏结构框架指导突变设计（预期效应） |
| loop 8 替换实验 | 验证 RNA 结构柔性对结合的功能贡献 | 连接结构预测与功能 | 输入：loop 8 刚性替换突变体；输出：结合/复制表型 | Abstract 明确替换损害互作 | 若移除，无法证明 loop 8 弯曲的功能必要性（实测消融效应：未提供具体数据） |

*注：所有消融效应均为作者主张，具体数值未在摘要中提供。*

---

## 09 关键公式符号

**不适用**。本文为实验生物学论文，摘要及正文未涉及数学公式或定量模型。核心概念为结构域互作（N 端锌指-RNA、C 端-Rpb2），无公式化表达。

---

## 10 实验设计与证据链

- **数据集/群体**：植物体内 PSTVd 感染体系（具体植物物种未在摘要中提供）。
- **规模**：未提供（样本量、重复数等未在摘要中说明）。
- **指标**：PSTVd RNA 积累水平；TFIIIA-7ZF-PSTVd 结合强度；loop 8 突变体对互作的影响。
- **基线**：野生型 Pol II（12 亚基）的 PSTVd 转录水平。
- **预算**：未提供。
- **骨干/仪器**：未提供（植物表达系统、检测方法未在摘要中详述）。
- **Oracle 输入**：不适用（无预测任务）。
- **评测协议**：未提供（摘要未描述具体实验流程）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| Pol II 亚基缺失对 PSTVd 转录的影响 | Rpb4/5/6/7/9 不参与 PSTVd 转录 | 各亚基缺失 vs 野生型 | 缺失上述亚基不影响 PSTVd RNA 积累 | Pol II 以 7 亚基形式行使 RdRP 功能 | 未证明 7 亚基形式是唯一活性形式；未排除其他亚基补偿 | Abstract |
| TFIIIA-7ZF 与 PSTVd RNA 结合 | 7ZF 变体是 PSTVd 转录所需 | 7ZF 变体 vs 其他剪接变体 | 7ZF 变体参与 PSTVd 转录 | TFIIIA-7ZF 是辅助因子 | 未证明结合是直接还是间接 | Abstract |
| AlphaFold3 预测复合物结构 | N 端结合 PSTVd 左端、C 端结合 Rpb2 | 预测结构 vs 实验互作数据 | 预测与实验一致 | 结构模型支持双功能桥接机制 | 预测未经实验结构验证（如 cryo-EM） | Abstract |
| loop 8 刚性替换 | loop 8 弯曲对结合必需 | 刚性双链替换 vs 天然 loop 8 | 替换损害 TFIIIA-7ZF/PSTVd 互作 | loop 8 柔性是结合关键 | 未证明 loop 8 弯曲是唯一决定因素 | Abstract |

---

## 11 结论正确解读

- **任务范围**：本文仅针对 PSTVd 类病毒在植物体内的复制，不涉及其他类病毒、HDV 或动物系统。
- **Oracle/真值输入**：不适用（无预测任务）。
- **端到端状态**：非端到端。研究为机制解析，未构建完整复制系统。
- **算力成本**：AlphaFold3 预测的计算成本未提及。
- **历史数据依赖**：依赖 PSTVd 已知的 RNA 结构信息及 Pol II 亚基组成知识。
- **模型依赖**：AlphaFold3 预测未经实验结构验证，存在假阳性可能。
- **最难情形**：体内亚基缺失实验可能受补偿机制干扰；loop 8 替换可能影响 RNA 整体折叠而非仅局部柔性。
- **群体/领域边界**：结论限于植物类病毒-宿主互作，推广至动物系统（如 HDV）需谨慎。
- **不确定性**：7 亚基 Pol II 的 stoichiometry 未定量；TFIIIA-7ZF 是否直接参与催化或仅起招募作用未明确。

**有边界的复述**：在 PSTVd 感染的植物体内，Pol II 的 Rpb4/5/6/7/9 亚基对类病毒 RNA 转录非必需，TFIIIA-7ZF 通过 N 端锌指结合 PSTVd RNA 左端、C 端结合 Rpb2 来桥接 Pol II 与 RNA 模板，且 PSTVd loop 8 的柔性弯曲对该互作至关重要；这些结论基于体内功能实验和 AlphaFold3 结构预测，但预测结构未经实验验证，且机制细节（如催化是否由 Pol II 核心直接完成）尚待阐明。

---

## 12 作者自认局限

在提供的摘要材料中，作者未明确列出「局限性」章节。以下为摘要中可推断的约束：

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 未提供 | 未提供 | 未提供 | 未提供 |

**作者提及的相关约束**（非正式局限，基于摘要措辞推断）：
- AlphaFold3 预测结构未经实验验证（如 cryo-EM），作者仅称「predicted structure and experimental data both show」，暗示预测与实验一致但未提供独立结构证据。
- 研究限于 PSTVd 单一体系，未扩展到其他类病毒或 HDV。
- 7 亚基 Pol II 的组装 stoichiometry 和动态性未定量描述。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 亚基缺失实验可能受补偿机制干扰 | 缺失 Rpb4/5/6/7/9 后，剩余亚基可能形成非天然复合物，或由其他蛋白补偿功能 | 若存在补偿，则「7 亚基是天然活性形式」的结论不成立 | 纯化内源 7 亚基复合物并体外重构 RdRP 活性；或进行交联质谱（crosslinking-MS）检测体内复合物组成 | Abstract 仅称「not involved」，未提供复合物组装证据 |
| AlphaFold3 预测的复合物可能不代表体内构象 | AF3 对多组分核酸-蛋白复合物的预测精度有限，尤其对柔性 RNA 区域 | 结构模型是后续突变设计的依据，若模型错误则功能解释失效 | 用 cryo-EM 或 SAXS 验证预测结构；或进行 HDX-MS 检测互作界面 | Abstract 未提供预测置信度或验证数据 |
| loop 8 替换实验可能改变 RNA 整体折叠 | 刚性双链替换可能影响 PSTVd 其他结构域，而非仅局部柔性 | 若整体折叠改变，则「loop 8 弯曲是关键」的结论可能过度归因 | 进行 RNA 结构探测（SHAPE）确认替换后整体折叠不变；或做更精细的点突变 | Abstract 仅称「replacing this loop 8 with a rigid double-stranded conformation impairs」，未提供结构对照 |
| TFIIIA-7ZF 的「剪接变体」身份未充分验证 | 7ZF 变体是否在体内天然存在、丰度如何、是否组织特异性表达均未提及 | 若 7ZF 是稀有变体，其生理相关性存疑 | 进行 RT-PCR 或 RNA-seq 验证内源剪接变体；定量蛋白丰度 | Abstract 仅称「a splicing variant」，未提供表达证据 |
| 体内实验缺乏时空分辨率 | 未区分 PSTVd 复制在细胞核/细胞质中的位置，也未区分感染早期/晚期 | 若 Pol II 重组是动态过程，静态敲除实验可能掩盖时间效应 | 进行时间序列实验或细胞分级分离 | Abstract 未提及时空信息 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **锌指蛋白的双功能桥接策略**：TFIIIA-7ZF 通过 N 端锌指结合 RNA、C 端结合 Pol II 大亚基，实现「模板识别 + 聚合酶招募」的一体化。可迁移至 TF–DNA 互作研究：设计双功能锌指蛋白（一个结构域结合 DNA 基序、另一个结构域结合 TF 或辅因子）可能实现人工转录因子的模块化构建。
2. **聚合酶亚基组成的可塑性**：Pol II 在 RNA 模板上以 7 亚基形式工作，提示 TF 可能通过改变 Pol II 亚基组成来调控转录特异性。在 TF–DNA 研究中，可探索 TF 是否诱导 Pol II 亚基解离/重组的机制。
3. **AlphaFold3 用于多组分核酸-蛋白复合物预测的流程**：本文展示了 AF3 在「蛋白-RNA-蛋白」三元复合物预测中的应用，并强调「预测 + 功能验证」闭环。可迁移至 TF–DNA 复合物结构预测：用 AF3 生成 TF-DNA-辅因子模型，再通过突变验证关键界面残基。
4. **RNA 结构柔性作为互作决定因素**：PSTVd loop 8 的弯曲构象对 TFIIIA-7ZF 结合至关重要，提示在 TF–DNA 互作中，DNA 的局部柔性（如 TATA box 弯曲）可能同样是被低估的决定因素。可借鉴此思路，系统扫描 DNA 基序的柔性位点。
5. **体内功能验证优先于纯结构预测**：作者强调「predicted structure and experimental data both show」，提示在 AI 结构预测时代，功能实验仍是验证互作机制的金标准。在 TF–DNA 研究中，应坚持「预测 → 突变 → 功能检测」的闭环。

---

## 15 与已有知识连接

- **TFIIIA 的经典功能**：TFIIIA 是首个被鉴定的锌指蛋白，经典功能是结合 5S rRNA 基因的 DNA 内部启动子（internal control region），招募 Pol III 进行转录。本文发现其剪接变体 TFIIIA-7ZF 参与 Pol II 的 RNA 模板转录，扩展了 TFIIIA 的功能谱系。可连接至 Miller et al. (1985) 对 TFIIIA 锌指结构的经典研究。
- **Pol II 亚基功能研究**：Rpb4/7 异二聚体在经典模型中与 Pol II 的稳定性、启动子逃逸相关（如 Sampath & Sadhale, 2005 综述）。本文提出这些亚基在 RNA 模板上非必需，与经典 DNA 模板转录形成对比。可连接至 Pol II 亚基缺失的表型研究。
- **类病毒复制机制**：类病毒复制依赖宿主 Pol II 的 RdRP 活性，此前研究多集中于 PSTVd RNA 结构（如左端结构域）对复制的影响（如 Flores et al., 2012 综述）。本文首次提出 Pol II 亚基重组机制，补充了该领域。
- **AlphaFold3 在核酸-蛋白复合物预测中的应用**：AF3 已成功预测蛋白-蛋白、蛋白-DNA、蛋白-RNA 复合物（如 Abramson et al., 2024 Nature）。本文将其应用于 Pol II-RNA-TFIIIA 三元复合物，展示了 AF3 在大型多组分复合物预测中的潜力。
- **可迁移领域**：本文的「聚合酶亚基重组 + 辅助因子桥接」机制可能适用于其他非编码 RNA 复制系统（如 HDV、类病毒样卫星 RNA），以及端粒酶（含 RNA 模板的逆转录酶）的组装机制。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选 1：锌指蛋白双功能桥接在 TF–DNA 互作中的普适性
- **名称**：Dual-domain ZF bridging in TF-DNA recognition
- **来源局限/观察**：本文发现 TFIIIA-7ZF 通过 N 端结合 RNA、C 端结合 Pol II 实现桥接；推测类似机制可能存在于 TF–DNA 互作中（如某些 TF 同时结合 DNA 基序和 Pol II 亚基）。
- **核心假设**：在真核 TF 中，存在一类「双功能锌指蛋白」，其 N 端锌指结合 DNA 基序、C 端锌指结合 Pol II 大亚基（如 Rpb2 或 Rpb1），从而增强转录起始效率。
- **初步方法**：对已知 TF 的锌指结构域进行序列比对，筛选 N/C 端功能分离的候选；用 AlphaFold3 预测候选 TF-DNA-Pol II 三元复合物；在报告基因系统中验证突变体对转录的影响。
- **验证方式**：EMSA 验证 DNA 结合；Co-IP 验证 Pol II 互作；报告基因检测转录活性。
- **创新状态**：unverified（基于本文机制的推测性延伸）

### 候选 2：Pol II 亚基可塑性与 TF 诱导的转录重编程
- **名称**：TF-induced Pol II subunit remodeling in DNA-templated transcription
- **来源局限/观察**：本文证明 Pol II 在 RNA 模板上以 7 亚基形式工作；推测某些 TF 可能通过诱导 Pol II 亚基解离来改变转录输出（如从过程性转录转为非过程性转录）。
- **核心假设**：特定 TF 结合 DNA 后，通过变构效应或招募去组装因子，诱导 Pol II 释放 Rpb4/7 等亚基，从而改变转录延伸速率或终止特性。
- **初步方法**：在体外转录系统中，加入候选 TF 后检测 Pol II 亚基组成（native PAGE 或质谱）；在体内用 CLIP 或 ChIP 检测 Pol II 亚基在基因上的分布。
- **验证方式**：单分子转录实验检测延伸速率变化；RNA-seq 检测转录输出变化。
- **创新状态**：unverified（高度推测性，但具有机制新颖性）

### 候选 3：DNA 局部柔性作为 TF 结合的决定因素——从 RNA loop 弯曲迁移
- **名称**：DNA flexibility scanning for TF binding site prediction
- **来源局限/观察**：本文证明 RNA loop 8 的柔性弯曲对 TFIIIA-7ZF 结合至关重要；推测 DNA 基序的局部柔性（如 TATA box 的固有弯曲）可能同样决定 TF 结合亲和力。
- **核心假设**：TF 结合位点的 DNA 柔性特征（如螺旋弯曲、小沟宽度）可作为独立于序列的预测特征，提升 TF 结合位点预测准确率。
- **初步方法**：用分子动力学（MD）模拟或 DNA 形状预测工具（如 DNAshape）计算已知 TF 结合位点的柔性特征；训练机器学习模型（如随机森林或深度学习）整合序列 + 形状特征。
- **验证方式**：在独立数据集上比较加入形状特征前后的预测 AUC；用实验（如 HT-SELEX）验证新预测位点。
- **创新状态**：partially checked（DNA 形状特征已被用于 TF 结合预测，但「柔性弯曲」作为显式特征尚待系统验证）

### 候选 4：AlphaFold3 在 TF-DNA-辅因子三元复合物预测中的系统评估
- **名称**：Benchmarking AlphaFold3 for TF-DNA-cofactor ternary complexes
- **来源局限/观察**：本文用 AF3 预测 Pol II-RNA-TFIIIA 三元复合物，但未提供预测置信度评估；AF3 对 TF-DNA-辅因子复合物的预测能力尚不清楚。
- **核心假设**：AF3 对 TF-DNA-辅因子三元复合物的预测精度与复合物大小、辅因子类型（小分子 vs 蛋白）相关，且可通过多序列比对（MSA）深度提升。
- **初步方法**：收集已知结构的 TF-DNA-辅因子复合物（如 p53-DNA、NF-κB-DNA），用 AF3 预测并与实验结构比对（TM-score、界面 RMSD）；系统变化 MSA 深度和输入特征。
- **验证方式**：结构比对指标；结合自由能计算（MM-PBSA）与实验突变数据对比。
- **创新状态**：prior-art checked（AF3 已有基准测试，但针对 TF-DNA-辅因子三元复合物的系统评估尚缺）

### 候选 5：类病毒复制中 Pol II 重组的动态调控
- **名称**：Dynamic Pol II remodeling during PSTVd replication
- **来源局限/观察**：本文证明 7 亚基 Pol II 参与 PSTVd 转录，但未提供时间分辨证据；推测 Pol II 亚基重组可能是动态、可逆的过程。
- **核心假设**：PSTVd 感染早期，宿主 Pol II 以 12 亚基形式启动转录，随后在感染进程中逐步释放 Rpb4/5/6/7/9，形成 7 亚基活性形式；该过程受宿主激酶或类病毒 RNA 结构调控。
- **初步方法**：在 PSTVd 感染的不同时间点进行 Pol II 免疫沉淀（针对不同亚基），定量亚基组成变化；用 CLIP 检测 Pol II 与 PSTVd RNA 的结合动态。
- **验证方式**：时间序列质谱定量；RNA-FISH 结合免疫荧光检测 Pol II 亚基在感染细胞中的定位。
- **创新状态**：unverified（基于本文静态结论的动态延伸）