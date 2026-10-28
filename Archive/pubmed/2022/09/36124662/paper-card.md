## 01 基本信息

- **标题**：The high mobility group protein HMG20A cooperates with the histone reader PHF14 to modulate TGFbeta and Hippo pathways
- **作者**：Gomez-Marin, Elena; Posavec-Marjanovic, Melanija; Zarzuela, Laura; Basurto-Cayuela, Laura; Guerrero-Martinez, Jose A; Arribas, Gonzalo; Yerbes, Rosario; Ceballos-Chavez, Maria; Rodriguez-Perez, Manuel; Tome, Mercedes; Duran, Raul V; Buschbeck, Marcus; Reyes, Jose C
- **单位**：未提供（推测为西班牙安达卢西亚分子生物学与再生医学中心 CABIMER 等，但原文未明确列出）
- **期刊/预印本平台**：Nucleic Acids Research
- **年份**：2022
- **论文类型**：实验研究（湿实验为主，辅以 AlphaFold2 结构预测）
- **领域**：染色质调控 / 表观遗传学 / 转录调控 / 蛋白质-蛋白质互作
- **关键词**：HMG20A、PHF14、HMG box、coiled-coil、TGFβ、Hippo、EMT、AlphaFold2
- **DOI/arXiv 号**：10.1093/nar/gkac766
- **代码**：未提供
- **数据**：RNA-seq 数据已存入 GEO（GSE193476）；蛋白质组学数据存入 ProteomeXchange/PRIDE（PXD030769）；结构模型存入 ModelArchive（https://modelarchive.org/doi/10.5452/ma-1us57）
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文聚焦 HMG20A（含 HMG box 的染色质调控因子）与组蛋白阅读器 PHF14 的互作，通过 AlphaFold2 预测复合物结构，揭示二者通过 coiled-coil 结构域形成复合物并共同调控 TGFβ 与 Hippo 通路。对「TF–DNA 结合机制 × AI/物理模拟」课题的启示在于：① AlphaFold2 不仅可用于单蛋白结构预测，还可用于蛋白-蛋白复合物建模，为理解 TF 与辅助因子协同结合 DNA 的机制提供结构基础；② HMG box 对四向连接 DNA（4WJ）的偏好性提示 TF 对 DNA 结构的识别（而非仅序列）是重要研究方向；③ 蛋白互作网络（而非单个 TF）决定转录输出，为 AI 建模提供「多因子协同」的框架。

---

## 02 一句话总结

本文通过 AlphaFold2 结构预测、蛋白质组学、共免疫沉淀和功能实验，证明 HMG20A 通过其 C 端 coiled-coil 结构域与组蛋白阅读器 PHF14 形成复合物，该复合物通过直接结合 TEAD1 转录因子调控 Hippo 通路靶基因，并参与 TGFβ 诱导的上皮-间质转化（EMT），从而在 MDA-MB-231 三阴性乳腺癌细胞中共同维持间质表型。

---

## 03 研究问题

- **具体问题**：HMG20A 除已知的 LSD1-CoREST 复合物互作外，是否还存在其他功能性蛋白互作伙伴？这些互作如何解释 HMG20A 在 EMT 和细胞迁移/侵袭中的功能？
- **为什么重要**：HMG20A 是 HMG 家族染色质调控因子，已知参与神经元分化、胰岛 β 细胞成熟和 EMT，但其分子机制（特别是 DNA 结合特异性低的情况下如何实现靶基因特异性调控）尚不清楚。理解其互作网络有助于揭示染色质调控因子如何实现功能多样性。
- **现有方法为何不足**：此前研究主要聚焦 HMG20A 与 LSD1-CoREST 复合物的互作，但无法解释 HMG20A 缺失与 LSD1 缺失表型差异；高通量蛋白质组学数据库虽提示 HMG20A 可能有其他伙伴，但缺乏功能验证。
- **精确的「Can ... ?」研究问题**：Can HMG20A form a functional complex with the histone reader PHF14 through its coiled-coil domain, and does this complex modulate TGFβ and Hippo pathways to control epithelial-mesenchymal plasticity?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及引文，属「经外部核验」的领域发展框架。

1. **HMG 蛋白家族研究（~1980s-2000s）**：HMG（high mobility group）蛋白是染色质调控因子，含 HMG box 结构域，分为序列特异性（如 SOX 家族）和非序列特异性（如 HMGB 家族）两类。代表性工作包括 HMG box 结构解析、DNA 弯曲/4WJ 结合特性等。
2. **HMG20A/B 功能研究（~2000s-2010s）**：HMG20A（iBRAF）最初被鉴定为 LSD1-CoREST 复合物的拮抗因子，在神经元分化中发挥作用。HMG20A 与 HMG20B（BRAF35）通过 C 端 coiled-coil 形成同/异二聚体。本课题组此前发现 HMG20A 在胰岛 β 细胞成熟和 EMT 中起关键作用。
3. **PHF14 研究（~2010s-2020s）**：PHF14 含 PHD 指结构域，被报道与间质生长、肺纤维化等相关，但其分子机制（特别是组蛋白阅读功能）尚不明确。Zheng 等（2021）解析了 PHF14 的 PZP 结构域（PHD1+ePHD）识别未修饰 H3 的机制。
4. **AlphaFold2 革命（2020-）**：DeepMind 开发的 AlphaFold2 实现了高精度蛋白结构预测，并扩展至蛋白-蛋白复合物预测（AlphaFold-multimer），为无晶体结构的蛋白互作研究提供了计算手段。
5. **本文位置**：首次将 HMG20A 与 PHF14 联系起来，通过 AlphaFold2 预测复合物结构并实验验证，将两个此前独立的领域（HMG 蛋白与 PHD 指蛋白）整合到 TGFβ/Hippo 通路调控框架中。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| HMG20A 功能机制不清 | HMG20A 已知参与多种过程（神经元分化、β 细胞、EMT），但分子机制不明 | HMG20A 的 HMG box 对线性 DNA 结合特异性低，难以解释靶基因特异性 | Results 图 1D-E：EMSA 显示 HMG20A 对线性 DNA 产生 smear 而非特异条带 |
| 已知互作伙伴不足以解释表型 | HMG20A 与 LSD1-CoREST 互作，但 HMG20A 缺失表型与 LSD1 缺失不完全一致 | 可能存在其他功能性互作伙伴 | 引言部分：作者指出「some phenotypes of HMG20A-depleted cells differ from LSD1-depleted cells」 |
| PHF14 功能机制不明 | PHF14 被报道与间质生长相关，但下游机制不清 | PHF14 的组蛋白阅读功能与转录调控的关联缺乏直接证据 | 引言部分：引用 PHF14 相关文献（16-18） |
| 蛋白质组学数据缺乏功能验证 | 高通量蛋白质组学提示 HMG20A 可能有多个伙伴，但未经验证 | 需要生化验证和功能实验确认 | Results 图 2A：LC-MS 鉴定到 PHF14 等新互作伙伴 |
| PHF14 抗体不适用于 ChIP | 两种商业抗 PHF14 抗体均无法获得特异性 ChIP 信号 | PHF14 可能不直接接触 DNA，或抗体表位被遮蔽 | Results 图 6 及 Methods：作者明确报告「no specific PHF14 ChIP signal was obtained」 |

---

## 06 核心思想

### 1) 表面方法
- 用 AlphaFold2-multimer 预测 HMG20A-PHF14 复合物结构
- 用 LC-MS 蛋白质组学鉴定 HMG20A 互作伙伴
- 用共免疫沉淀（co-IP）验证内源互作
- 用 siRNA 敲低 + 转录组测序（RNA-seq）分析功能
- 用 EMT 诱导实验（TGFβ 处理）和功能实验（迁移、侵袭、黏附）验证表型
- 用 ChIP 检测 HMG20A 在靶基因启动子上的结合

### 2) 核心洞察
- **HMG20A 与 PHF14 通过 coiled-coil 结构域形成异源二聚体**，而非通过 HMG box 或 PHD 结构域直接互作。AlphaFold2 预测的复合物结构显示二者形成两股 α-螺旋卷曲螺旋结构。
- **HMG20A 的 HMG box 负责 DNA 结合（偏好 4WJ/弯曲 DNA），PHF14 的 PHD 结构域负责识别未修饰 H3 组蛋白**，二者协同实现「组蛋白状态 + DNA 结构」的双重识别，从而靶向特定染色质区域。
- **HMG20A-PHF14 复合物直接与 TEAD1 转录因子互作**，调控 Hippo 通路靶基因（如 CTGF、CYR61），同时影响 TGFβ 通路，形成「染色质调控因子-转录因子」的协同调控模块。
- **HMG20A 的 IDR 结构域具有转录激活功能**，可能通过相分离或招募共激活因子发挥作用。

### 3) 可能的普适教训 [Analysis]
- **AlphaFold2 不仅可用于单蛋白结构预测，更可用于发现新的蛋白-蛋白互作界面**，为湿实验提供可检验的假设。本文展示了「计算预测 → 生化验证 → 功能验证」的完整闭环。
- **低序列特异性的 DNA 结合蛋白（如 HMG box 蛋白）通过蛋白互作伙伴实现靶基因特异性**，这是染色质调控因子的普遍策略。对 TF-DNA 互作建模时，不能仅考虑 TF 与 DNA 的二元互作，需纳入辅助因子。
- **「组蛋白修饰阅读器 + DNA 结构传感器」的双重识别模块**可能是染色质调控的通用设计原则，值得在 AI 模型中显式建模。

---

## 07 方法总览

- **输入**：
  - 人 HMG20A 和 PHF14 全长氨基酸序列（AlphaFold2 建模）
  - MDA-MB-231 细胞（人三阴性乳腺癌）
  - NMuMG 细胞（小鼠正常乳腺上皮）
  - HEK293T、U2OS 细胞（互作验证和报告基因实验）
  - 抗 HMG20A、PHF14、TEAD1 抗体
  - siRNA 序列（靶向 HMG20A、PHF14）
  - TGFβ 细胞因子

- **输出**：
  - HMG20A-PHF14 复合物结构模型（AlphaFold2）
  - 互作蛋白列表（LC-MS）
  - 敲低后的转录组变化（RNA-seq）
  - 迁移、侵袭、黏附表型数据
  - HMG20A 在靶基因启动子上的结合数据（ChIP-qPCR）

- **模块**：
  1. **结构预测模块**：AlphaFold2-multimer 预测 HMG20A-PHF14 复合物
  2. **互作鉴定模块**：Flag-HMG20A 亲和纯化 + LC-MS；co-IP 验证
  3. **功能敲低模块**：siRNA 敲低 HMG20A 或 PHF14
  4. **转录组分析模块**：RNA-seq + DESeq2 差异表达 + GSEA
  5. **表型分析模块**：迁移（伤口愈合）、侵袭（Boyden 小室）、黏附实验
  6. **染色质结合模块**：ChIP-qPCR 检测 HMG20A 在 CDH1、TP63 启动子上的结合
  7. **报告基因模块**：TEAD 报告基因（萤火虫荧光素酶）检测 Hippo 通路活性

- **训练**：不适用（无监督学习/预训练模型直接推理）

- **工具**：AlphaFold2 v2.1.1（AlphaFold-multimer）、Rsubread、DESeq2、GSEA v2.0.14、DAVID、Prism/Graphpad、ImageJ（JACoP 共定位分析）

- **反馈回路**：AlphaFold2 预测的互作界面 → 设计 HMG20A 截短突变体 → co-IP 验证关键结构域 → 功能实验确认生物学相关性

- **假设**：
  - HMG20A 与 PHF14 的互作是直接的（而非通过中间蛋白）
  - 敲低 HMG20A 或 PHF14 的表型相似性反映二者在同一通路中功能
  - AlphaFold2 预测的复合物结构具有生物学相关性

- **文字流程**：
  1. 用 AlphaFold2 预测 HMG20A 结构，识别三个结构域（IDR、HMG box、coiled-coil）
  2. 用 LC-MS 鉴定 HMG20A 互作伙伴，发现 PHF14
  3. 用 co-IP 验证内源 HMG20A-PHF14 互作，并用截短突变体定位互作结构域（coiled-coil）
  4. 用 AlphaFold2-multimer 建模复合物，确认 coiled-coil 互作模式
  5. 在 MDA-MB-231 中敲低 HMG20A 或 PHF14，进行 RNA-seq 分析共同靶基因
  6. 功能实验验证迁移、侵袭、黏附表型
  7. 聚焦 Hippo 通路：检测靶基因表达、TEAD1 互作、YAP 活性
  8. 用 TGFβ 处理 NMuMG 细胞验证 EMT 表型
  9. ChIP 检测 HMG20A 在 CDH1、TP63 启动子上的结合

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AlphaFold2 结构预测 | 预测 HMG20A 单体和 HMG20A-PHF14 复合物结构 | 无实验结构可用，需计算模型指导突变设计 | 输入：氨基酸序列；输出：3D 结构模型 | Results 图 1A-B、图 2F-G | 预期影响：无法定位互作结构域，突变设计缺乏指导 [预期效应] |
| LC-MS 蛋白质组学 | 鉴定 HMG20A 互作伙伴 | 发现新互作伙伴 | 输入：Flag-HMG20A 亲和纯化产物；输出：候选互作蛋白列表 | Results 图 2A、Supplementary Table S2 | 预期影响：无法发现 PHF14 这一关键伙伴 [预期效应] |
| co-IP 验证 | 验证内源蛋白互作 | 确认蛋白质组学结果 | 输入：细胞裂解液 + 抗体；输出：免疫印迹信号 | Results 图 2D | 预期影响：无法确认互作真实性 [预期效应] |
| 截短突变体分析 | 定位互作所需结构域 | 确定 coiled-coil 的关键作用 | 输入：HMG20A 截短突变体；输出：co-IP 结果 | Results 图 2E | 预期影响：无法确定 coiled-coil 为互作界面 [预期效应] |
| siRNA 敲低 + RNA-seq | 分析敲低后的转录组变化 | 鉴定共同靶基因和通路 | 输入：siRNA 处理细胞 RNA；输出：差异表达基因列表 | Results 图 5A-C、Supplementary Table S3 | 预期影响：无法建立功能联系 [预期效应] |
| GSEA 通路分析 | 识别富集的信号通路 | 将转录组变化与已知通路关联 | 输入：差异表达基因列表；输出：富集通路 | Results 图 5D-G、Supplementary Fig S6-7 | 预期影响：无法定位到 TGFβ/Hippo 通路 [预期效应] |
| 功能表型实验 | 验证迁移、侵袭、黏附变化 | 确认生物学功能 | 输入：敲低细胞；输出：表型数据 | Results 图 4B-E | 预期影响：无法确认功能重要性 [预期效应] |
| ChIP-qPCR | 检测 HMG20A 在靶基因启动子上的结合 | 确认直接调控 | 输入：交联染色质 + 抗 HMG20A 抗体；输出：富集倍数 | Results 图 6F | 预期影响：无法确认直接结合 [预期效应] |
| TEAD 报告基因 | 检测 Hippo 通路转录活性 | 确认功能影响 | 输入：报告基因质粒 + 敲低细胞；输出：荧光素酶活性 | Results 图 5I | 预期影响：无法确认对 Hippo 通路的直接调控 [预期效应] |

---

## 09 关键公式符号

本文为湿实验为主的研究，无核心数学模型或公式。以下为数据分析中使用的统计方法：

- **差异表达分析**：DESeq2 使用负二项分布模型，统计量为 Wald test 或 LRT。调整后 p 值（padj）< 0.05 且 |log2(fold change)| > 0.5 为显著差异基因。
- **GSEA**：使用加权富集分数（weighted enrichment score, ES），通过表型置换检验（phenotype permutation, 1000 次）计算名义 p 值，并用 FDR 校正。
- **Pearson 相关系数**：用于评估 HMG20A 与 PHF14 在 DepMap 和 CCLE 数据中的依赖性/表达相关性（图 2B、Supplementary Fig S2C-D）。
- **超几何分布**：用于计算基因集重叠的显著性（如 HMG20A 和 PHF14 共同靶基因的富集）。
- **共定位分析**：Pearson 相关系数用于评估 HMG20A 与 PHF14 免疫荧光的共定位程度（Supplementary Fig S3B）。

---

## 10 实验设计与证据链

### 数据集/群体/规模
- **细胞系**：MDA-MB-231（人三阴性乳腺癌）、NMuMG（小鼠正常乳腺上皮）、HEK293T（人胚肾）、U2OS（人骨肉瘤）
- **RNA-seq**：MDA-MB-231 细胞，siControl、siHMG20A、siPHF14 各 2 个生物学重复
- **LC-MS**：Flag-HMG20A 或空载体转染的 HEK293T 细胞核提取物
- **DepMap**：940 个细胞系的 CRISPR-Cas9 依赖性数据（21Q3 版本）
- **CCLE**：1269 个细胞系的基因表达数据

### 指标
- 差异表达基因数（padj < 0.05, |log2FC| > 0.5）
- 迁移/侵袭细胞数
- 黏附细胞百分比
- 报告基因相对荧光素酶活性
- ChIP 富集倍数

### 基线/对照
- siControl（非靶向 siRNA）
- 空载体转染
- IgG 抗体作为 ChIP 阴性对照
- 未处理细胞（TGFβ 实验）

### 评测协议
- 每个实验至少 3 次独立生物学重复
- 统计检验：双尾 Student's t-test，p < 0.05 为显著

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| AlphaFold2 结构预测 | HMG20A 含 IDR、HMG box、coiled-coil 三结构域 | 预测 vs 已知 HMG box 结构 | 预测出三结构域，coiled-coil 为长 α 螺旋 | HMG20A 结构域组织 | 预测需实验验证 | Results 图 1A-B |
| EMSA | HMG20A 结合 DNA | 线性 vs 4WJ DNA；不同蛋白量 | 4WJ 结合强于线性 DNA；线性 DNA 产生 smear | HMG20A 偏好弯曲 DNA | 未定量结合亲和力 | Results 图 1D-E |
| LC-MS | 鉴定 HMG20A 互作伙伴 | Flag-HMG20A vs 空载体 | 鉴定到 PHF14 等 | PHF14 是 HMG20A 候选伙伴 | 需验证直接互作 | Results 图 2A |
| co-IP（内源） | HMG20A 与 PHF14 内源互作 | 抗 HMG20A IP vs IgG | 检测到 PHF14 共沉淀 | 内源互作存在 | 未排除间接互作 | Results 图 2D |
| co-IP（截短突变体） | coiled-coil 介导互作 | WT vs ΔIDR vs Δcc1 vs Δcc2 | Δcc1/Δcc2 丧失互作 | coiled-coil 为互作所需 | 未做点突变精细定位 | Results 图 2E |
| AlphaFold-multimer | 预测复合物结构 | 5 个模型 | 预测 coiled-coil 互作 | 支持实验发现 | 预测需实验验证 | Results 图 2F-G |
| RNA-seq | 敲低 HMG20A/PHF14 的转录组变化 | siHMG20A/siPHF14 vs siControl | 2235/1154 差异基因，高度重叠 | 二者共同调控大量基因 | 未做时间序列 | Results 图 5A-C |
| GSEA | 通路富集 | 敲低 vs 对照 | TGFβ、Hippo、EMT 通路富集 | 参与这些通路 | 通路分析为相关性 | Results 图 5D-G |
| 迁移/侵袭实验 | 敲低影响迁移侵袭 | siHMG20A/siPHF14 vs siControl | 迁移侵袭显著降低 | 促进迁移侵袭 | 未做回复实验 | Results 图 4B-D |
| 黏附实验 | 敲低影响细胞黏附 | siHMG20A/siPHF14 vs siControl | 黏附增加 | 抑制黏附 | 未做机制解析 | Results 图 4E |
| ChIP-qPCR | HMG20A 结合 CDH1/TP63 启动子 | 抗 HMG20A vs IgG；siHMG20A vs siControl | 检测到结合，敲低后信号降低 | 直接结合靶启动子 | PHF14 无法用 ChIP 检测 | Results 图 6F |
| TGFβ 诱导 EMT | 敲低影响 TGFβ 诱导的 EMT | TGFβ ± siHMG20A/siPHF14 | EMT 标志物变化受损 | 参与 TGFβ 诱导 EMT | 未做 TGFβ 通路蛋白水平分析 | Results 图 7D |
| TEAD 报告基因 | 敲低影响 Hippo 靶基因转录 | siHMG20A/siPHF14 vs siControl | 报告基因活性降低 | 调控 Hippo 转录输出 | 未做 YAP 磷酸化分析 | Results 图 5I |

---

## 11 结论正确解读

- **任务范围**：本文仅在人三阴性乳腺癌细胞系 MDA-MB-231 和小鼠乳腺上皮细胞 NMuMG 中验证了 HMG20A-PHF14 复合物的功能。结论不能推广到所有细胞类型或组织。
- **oracle/真值输入**：AlphaFold2 预测的复合物结构未经晶体学或冷冻电镜验证，属于计算模型。作者用 co-IP 和截短突变体验证了互作，但未提供高分辨率实验结构。
- **端到端状态**：本文不是端到端的「序列 → 功能」预测流程。AlphaFold2 仅用于结构预测，功能结论来自湿实验。
- **算力成本**：未提供 AlphaFold2 运行的具体算力需求。
- **历史数据依赖**：RNA-seq 和蛋白质组学数据依赖参考基因组（hg19）和数据库注释；DepMap/CCLE 数据为公共数据。
- **模型依赖**：AlphaFold2 预测的置信度未系统报告（pLDDT 或 PAE 值未在文中展示）。
- **最难情形**：PHF14 的 ChIP 实验无法进行（抗体不适用），因此无法直接证明 PHF14 在靶基因启动子上的结合。HMG20A 的 ChIP 信号较弱，需要敲低验证。
- **群体/领域边界**：结论限于哺乳动物细胞（人、小鼠），未涉及其他物种。HMG20A-PHF14 复合物在神经元、胰岛 β 细胞等其他 HMG20A 功能场景中的作用未验证。
- **不确定性**：作者未提供效应量（effect size）的置信区间；部分实验（如迁移、侵袭）的定量数据未在摘要中展示。

**有边界的复述**：在 MDA-MB-231 三阴性乳腺癌细胞中，HMG20A 与 PHF14 通过 coiled-coil 结构域形成复合物，该复合物与 TEAD1 互作并调控 Hippo 通路靶基因表达；在 NMuMG 细胞中，二者为 TGFβ 诱导的 EMT 所必需。这些结论基于 siRNA 敲低、co-IP、RNA-seq 和功能实验，未在体内动物模型中验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| PHF14 ChIP 无法进行 | 两种商业抗 PHF14 抗体均无法获得特异性 ChIP 信号 | 未明确提及 | Results 图 6 及 Materials and Methods |
| HMG20A 结合 CDH1/TP53 启动子的机制不完全清楚 | 无法区分直接结合与间接结合 | 未明确提及 | Results 图 6F |
| 复合物调控转录的精确机制未知 | 作者提出可能通过维持染色质「ground state」 | 需进一步研究组蛋白修饰变化 | Discussion |
| HMG20A 的 IDR 功能未深入解析 | 仅证明具有转录激活活性 | 未明确提及 | Results 图 1C |
| 未在体内模型中验证 | 所有实验均为体外细胞系 | 未明确提及 | 全文 |
| 未解决 HMG20A 如何在不同复合物（LSD1-CoREST vs PHF14）之间切换 | 作者提出「complex choreography of interactions」 | 需进一步研究 | Discussion |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| AlphaFold2 预测的复合物结构未经实验验证 | AlphaFold2 对 coiled-coil 互作的预测可能不准确；预测的界面可能不是真实互作界面 | 结构模型是后续突变设计的基础，若模型错误则结论受影响 | 用 SEC-MALS、交联质谱或冷冻电镜验证复合物结构 | Results 图 2F-G |
| HMG20A 与 PHF14 的共依赖性分析仅基于 DepMap 数据 | 相关性不等于因果关系；细胞系背景差异可能影响结论 | 支持二者功能相关的证据强度有限 | 在更多细胞系中验证共依赖性；用 CRISPR 双敲除验证遗传互作 | Results 图 2B |
| RNA-seq 差异基因重叠分析未展示具体重叠比例 | 作者仅报告「高度重叠」但未给出具体数字 | 无法评估二者功能冗余程度 | 补充 Venn 图的具体数字和统计检验 | Results 图 5C |
| HMG20A 敲低对 PHF14 蛋白水平的影响未深入分析 | 可能是蛋白稳定性而非转录调控 | 区分「复合物功能」与「蛋白相互依赖」 | 用蛋白酶体抑制剂处理 + 蛋白半衰期实验 | Results 图 3 |
| TGFβ 诱导 EMT 实验仅检测了部分标志物 | 未检测所有经典 EMT 标志物（如 vimentin、N-cadherin 蛋白水平） | EMT 结论可能不完整 | 补充更多 EMT 标志物的蛋白和 mRNA 水平检测 | Results 图 7D |
| 未检测 HMG20A-PHF14 复合物在基因组上的全基因组分布 | 仅检测了 CDH1 和 TP53 两个位点 | 无法评估复合物的全基因组靶标范围 | 用 CUT&Tag 或 ChIP-seq 检测 HMG20A 全基因组结合 | Results 图 6F |
| 未检测 YAP/TAZ 的核质定位变化 | 仅检测了靶基因表达 | Hippo 通路的核心是 YAP/TAZ 核质穿梭 | 用免疫荧光检测 YAP/TAZ 定位 | Results 图 5 |

---

## 14 学到什么

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/深度学习/物理模拟」课题的可迁移知识。

### 概念性知识
1. **HMG box 结构域对 DNA 结构的识别优先于序列识别**：HMG20A 对 4WJ DNA 的亲和力高于线性 DNA，提示 TF-DNA 互作建模时需考虑 DNA 结构特征（弯曲、十字结构、G4 等），而非仅序列 motif。
2. **「组蛋白阅读器 + DNA 结合蛋白」的双模块复合物设计**：PHF14（识别未修饰 H3）+ HMG20A（结合 DNA）的复合物实现了「表观状态 + DNA 结构」的双重识别。这种设计在 TF 中可能普遍存在，AI 模型应考虑多模块协同。
3. **coiled-coil 介导的 TF-辅助因子互作**：HMG20A 通过 coiled-coil（而非 HMG box）与 PHF14 互作，说明蛋白-蛋白互作界面与 DNA 结合界面在空间上分离，允许独立进化。

### 方法论知识
4. **AlphaFold2-multimer 用于发现新互作界面的工作流**：计算预测 → 突变验证 → 功能验证的闭环，可迁移到 TF-辅助因子复合物建模。
5. **蛋白质组学 + 转录组学 + 表型组学的多组学整合策略**：LC-MS 发现互作 → RNA-seq 发现共同靶标 → 功能实验验证表型，是研究 TF 功能模块的完整范式。
6. **GSEA 用于通路级功能注释**：从差异基因列表到通路富集的流程，可用于 AI 预测结果的生物学解释。

### 可迁移到本课题的具体思路
7. **对 TF-DNA 结合特异性低的 TF，应建模「TF + 辅助因子」的复合物-DNA 互作**，而非仅 TF 单体。HMG20A 单独结合 DNA 特异性低，但与 PHF14 形成复合物后实现靶标特异性。
8. **DNA 结构特征（弯曲、4WJ）应作为 TF-DNA 结合预测模型的特征**。当前多数模型仅用序列特征，忽略 DNA 结构。
9. **IDR 结构域的转录激活功能**：HMG20A 的 IDR 具有转录激活活性，提示无序区域在 TF 功能中的重要性。AI 模型可考虑将 IDR 特征纳入转录活性预测。

---

## 15 与已有知识连接

- **HMG box 蛋白家族**：本文与 HMGB1、HMGB2 等经典 HMG box 蛋白研究一致，均显示对结构化 DNA（4WJ、顺铂损伤 DNA）的偏好。可连接至 Thomas & Travers (2001) 关于 HMG box-DNA 互作的综述。
- **LSD1/Co-REST 复合物**：HMG20A 此前已知作为该复合物的拮抗因子（本文引言引用文献 1-5），本文扩展了 HMG20A 的互作网络。可连接至 Whyte et al. (2012) 关于 CoREST 复合物的研究。
- **PHF14 与 PHD 指结构域**：PHF14 的 PZP 结构域识别未修饰 H3（Zheng et al., 2021），与本文发现的「HMG20A-PHF14 复合物结合 CDH1/TP63 启动子」一致。可连接至 Musselman & Kutateladze (2011) 关于 PHD 指结构域的综述。
- **Hippo 通路与 TEAD 转录因子**：TEAD 家族是 Hippo 通路核心效应器，本文发现 HMG20A-PHF14 与 TEAD1 互作。可连接至 Zanconato et al. (2016) 关于 YAP/TAZ-TEAD 的综述。
- **TGFβ 通路与 EMT**：HMG20A 与 SMAD4 的互作此前已有报道（本文引言引用文献 4, 86），本文进一步证明 HMG20A-PHF14 复合物参与 TGFβ 诱导的 EMT。可连接至 Thiery et al. (2009) 关于 EMT 的经典综述。
- **AlphaFold2 在蛋白复合物预测中的应用**：本文使用 AlphaFold2-multimer 预测 HMG20A-PHF14 复合物，可连接至 Evans et al. (2022) 关于 AlphaFold-multimer 的原始论文。
- **DepMap/CCLE 数据资源**：本文使用 DepMap 依赖性数据和 CCLE 表达数据验证 HMG20A-PHF14 功能相关性，可连接至 Tsherniak et al. (2017) 和 Barretina et al. (2012)。

---

## 16 研究想法

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/深度学习/物理模拟」课题的研究候选。

### 候选 1：基于 AlphaFold2 的 TF-辅助因子复合物-DNA 三元互作预测框架
- **来源局限/观察**：本文发现 HMG20A 单独结合 DNA 特异性低，但与 PHF14 形成复合物后实现靶标特异性。现有 TF-DNA 预测模型大多仅考虑 TF 单体。
- **核心假设**：TF 与辅助因子形成复合物后，其 DNA 结合特异性发生改变，且这种改变可通过复合物结构预测。
- **初步方法**：用 AlphaFold2-multimer 预测 TF-辅助因子复合物结构，再用分子对接（如 HADDOCK）或 MD 模拟将复合物对接到 DNA 上，提取界面特征训练特异性预测模型。
- **验证方式**：在已知 TF-辅助因子-DNA 三元复合物数据集（如 PDB 中的 TF 二聚体-DNA 结构）上测试；用 SELEX 或 HT-SELEX 实验验证预测的 motif 变化。
- **创新状态**：unverified

### 候选 2：DNA 结构特征（弯曲/4WJ）作为 TF-DNA 结合预测的增强特征
- **来源局限/观察**：HMG20A 对 4WJ DNA 的亲和力显著高于线性 DNA，提示 DNA 结构特征对 TF 结合有重要影响。
- **核心假设**：将 DNA 结构特征（弯曲度、柔韧性、十字结构概率）纳入深度学习模型，可提高对低序列特异性 TF 的结合预测精度。
- **初步方法**：用 DNAShape 或 ABC 服务器计算 DNA 结构特征，与序列特征（one-hot、k-mer）拼接，输入 CNN/Transformer 模型；在 ENCODE TF ChIP-seq 数据集上比较有无结构特征的性能。
- **验证方式**：对 HMG box 家族蛋白（HMGB1、SOX 等）进行留一法验证；用 EMSA 实验验证模型预测的高/低亲和力位点。
- **创新状态**：unverified

### 候选 3：TF-IDR 结构域在转录激活中的功能预测模型
- **来源局限/观察**：HMG20A 的 IDR 具有转录激活活性，但 IDR 序列与功能的关系尚不清楚。
- **核心假设**：TF 的 IDR 序列特征（电荷分布、疏水性、预测的相分离倾向）可预测其转录激活/抑制功能。
- **初步方法**：收集已知 TF 的 IDR 序列和转录激活/抑制实验数据，用序列特征（如酸性残基比例、预测的相分离倾向）训练分类模型；与 AlphaFold2 预测的 IDR 结构特征结合。
- **验证方式**：在独立数据集上验证；用报告基因实验验证新预测的激活型 IDR。
- **创新状态**：unverified

### 候选 4：TF-辅助因子复合物的全基因组结合位点预测
- **来源局限/观察**：本文仅检测了 HMG20A 在 CDH1 和 TP53 两个启动子上的结合，未提供全基因组数据。
- **核心假设**：HMG20A-PHF14 复合物的全基因组结合位点可通过整合 ChIP-seq（HMG20A）和组蛋白修饰数据（H3K4me0/未修饰 H3）来预测。
- **初步方法**：在 MDA-MB-231 细胞中做 HMG20A ChIP-seq（作者已具备 ChIP 条件），结合 PHF14 的已知组蛋白结合偏好（未修饰 H3），训练「序列 + 表观状态」的联合预测模型。
- **验证方式**：用 CRISPR 敲除 PHF14 后检测 HMG20A 结合位点的变化；用 CUT&Tag 验证预测的新位点。
- **创新状态**：unverified

### 候选 5：HMG20A-PHF14-TEAD1 三元复合物的结构建模与功能验证
- **来源局限/观察**：本文证明 HMG20A-PHF14 与 TEAD1 互作，但未提供三元复合物的结构模型。
- **核心假设**：HMG20A-PHF14 复合物通过直接结合 TEAD1 稳定其与 DNA 的结合，且这种稳定作用可通过结构建模预测。
- **初步方法**：用 AlphaFold2-multimer 预测 HMG20A-PHF14-TEAD1 三元复合物结构，再用 MD 模拟（如 GROMACS）研究复合物与 DNA 的结合动力学；用突变体破坏预测的互作界面并验证功能。
- **验证方式**：用 co-IP 验证突变体对互作的影响；用报告基因实验验证对 Hippo 通路靶基因表达的影响。
- **创新状态**：unverified