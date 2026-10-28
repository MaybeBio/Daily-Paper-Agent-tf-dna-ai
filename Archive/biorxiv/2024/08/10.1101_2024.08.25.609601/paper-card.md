## 01 基本信息

- **标题**：Intrinsically Disordered Regions Define Unique Protein Interaction Networks in CHD Family Remodelers
- **作者与单位**：Tabar MS; Parsania C; Giardina C; Feng Y; Wong AC; Metierre C; Nagarajah R; Dhungel BP; Rasko JE; Bailey CG（单位未在摘要中提供，推测为澳大利亚悉尼大学相关机构）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2024
- **论文类型**：预印本（研究论文）
- **领域**：染色质重塑、蛋白质-蛋白质互作、 intrinsically disordered regions (IDRs)、AlphaFold 结构预测
- **关键词**：CHD 家族、染色质重塑、IDR、APR、AlphaFold Multimer、蛋白质互作网络、NuRD、ChAHP
- **DOI/arXiv 号**：10.1101/2024.08.25.609601
- **代码**：未提供
- **数据**：质谱数据（ProteomeXchange PXD055009）；RNA-Seq 数据（GEO GSE275475）
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文聚焦 CHD 家族染色质重塑因子 N/C 末端的 IDR 与 APR 在蛋白质-蛋白质互作（PPI）中的作用，采用 AP-MS 与 AlphaFold Multimer 结合的策略。对「TF–DNA 结合机制 × AI/物理模拟」课题的启示在于：展示了如何用 AlphaFold Multimer 评估无序区域介导的互作界面，以及如何将预测与实验（AP-MS、Co-IP、肽段竞争）结合验证互作热点——该方法论可直接迁移到 TF–DNA 互作界面预测与验证中。

## 02 一句话总结

本文通过 AP-MS 与 AlphaFold Multimer 结合，绘制了 CHD1-9 家族 N/C 末端的 PPI 网络，并证明 CHD4 C 末端一个保守的 APR（YWLLAGII）是介导其与 NuRD 和 ChAHP 复合物互作的关键界面，该界面调控红系分化过程中的基因转录程序。

## 03 研究问题

- **具体问题**：CHD 家族染色质重塑因子 N/C 末端富含 IDR 和 APR，但这些区域在 CHD 功能（特别是蛋白质互作）中的作用尚不清楚。具体而言：CHD4 的 C 末端 APR 是否以及如何介导其与 NuRD 和 ChAHP 复合物的互作？
- **为什么重要**：CHD 蛋白通过互作网络实现功能多样性，但因其大尺寸和高 DNA/组蛋白亲和力，传统 PPI 研究困难。理解 IDR/APR 介导的互作机制有助于揭示 CHD 亚家族特异性功能及染色质调控的精细机制。
- **现有方法不足**：全长 CHD 蛋白的 PPI 研究受限于技术难度（大蛋白、高核酸亲和力导致非特异性结合）；AlphaFold 对无序区域的预测置信度低，单独使用难以判定互作界面。
- **精确的 Can 问题**：Can a conserved APR within the CHD4 C-terminus mediate its interaction with both NuRD and ChAHP complexes in a mutually exclusive manner, and is this interaction functionally required for erythroid gene transcription?

## 04 背景与发展脉络

*注：以下脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。*

1. **阶段一：CHD 家族发现与分类**（~2000s）——基于序列和结构域将 CHD 分为三个亚家族（I: CHD1-2; II: CHD3-5; III: CHD6-9），核心功能为 ATP 依赖的核小体重塑。
2. **阶段二：CHD 互作研究**（~2010s）——已知 CHD3-5 与 NuRD 复合物互作，CHD4 也存在于 ChAHP 复合物中；但互作界面和分子机制不清。全长蛋白 PPI 研究受技术限制。
3. **阶段三：IDR/APR 功能认识**（~2020s）——IDR 在信号传导、相分离和互作网络中的重要性被广泛认识；APR 被认为与聚集和互作相关，但在 CHD 家族中的系统研究缺乏。
4. **阶段四：AI 结构预测辅助互作研究**（2021-）——AlphaFold2/Multimer 的出现使得预测蛋白复合物结构成为可能，但对无序区域预测仍有限。
5. **本文位置**：将 AP-MS 实验互作组学与 AlphaFold Multimer 预测结合，系统绘制 CHD 家族 N/C 末端 PPI 网络，并聚焦验证 CHD4 APR 的功能——处于「实验互作组学 × AI 结构预测」交叉点。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 全长 CHD 蛋白 PPI 研究困难 | 传统方法难以获得高质量互作数据 | CHD 蛋白大（197-336 kDa）、含 DNA/组蛋白结合域，导致非特异性结合和实验噪音 | Discussion 首段 |
| IDR 区域功能未知 | CHD N/C 末端高度无序，功能注释缺乏 | IDR 不形成稳定三维结构，传统结构-功能研究难以开展 | Results 图 1B；PONDR 预测 |
| AlphaFold 对无序区域预测置信度低 | 预测复合物时 IDR 区域 pLDDT 分数低 | 无序区域缺乏进化约束，难以从序列预测稳定结构 | Discussion；Results 图 4 |
| APR 在互作中的角色不清 | APR 是否直接参与互作、如何介导互作未知 | APR 通常与聚集相关，其在特异性互作中的功能未被系统研究 | Results 图 4-5 |
| 互作界面验证困难 | 预测的互作界面缺乏实验验证 | 需要多种正交方法（突变、肽段竞争、Co-IP）交叉验证 | Results 图 5 |

## 06 核心思想

**1) 表面方法**：
- 将 CHD1-9 的 N/C 末端（共 22 个片段）克隆为 FLAG 标签构建体，在 Expi293 细胞中过表达，核分级后 AP-MS 鉴定互作蛋白。
- 用 PONDR 预测 IDR、TANGO 预测 APR。
- 用 AlphaFold Multimer 预测候选互作复合物结构，以 PAE 和 pLDDT 评估互作置信度。
- 对 CHD4 APR 进行缺失突变（APR Del）和肽段竞争实验验证功能。

**2) 核心洞察**：
- CHD 家族 N/C 末端虽高度无序，但其中嵌合的短 APR 序列（如 CHD4 的 YWLLAGII）可作为特异性互作热点，介导与不同复合物的结合。
- AlphaFold Multimer 对「无序区域+结构化伴侣」复合物的预测，即使对无序区域本身置信度低，仍可识别互作界面的大致位置——预测与实验结合可弥补各自局限。
- CHD4 的 APR 可能以「相互排斥」的方式介导与 NuRD 或 ChAHP 的结合，提示单一短序列可作为互作开关。

**3) 可能的普适教训 [Analysis]**：
- 对无序蛋白/区域，短线性基序（SLiMs）而非整体折叠结构可能是互作的主要决定因素——这提示在 TF–DNA 互作研究中，应关注 TF 无序区域内的短 DNA 结合基序或互作基序。
- AlphaFold 预测与实验互作组学的结合是「AI 辅助互作研究」的高效范式：预测提供候选界面，实验提供功能验证。
- 肽段竞争实验是验证「短序列介导互作」的强有力工具，可迁移到 TF–DNA 互作抑制研究中。

## 07 方法总览

- **输入**：CHD1-9 全长蛋白序列（用于片段设计）；CHD N/C 末端片段（22 个）；候选互作蛋白序列（AlphaFold 输入）。
- **输出**：CHD 家族 N/C 末端 PPI 网络；CHD4 APR 介导互作的结构模型；APR 功能验证数据（Co-IP、肽段竞争、RNA-Seq）。
- **模块**：
  1. 片段克隆与表达（FLAG 标签，Expi293 细胞）
  2. 核分级与 AP-MS（FLAG 免疫沉淀 + 质谱）
  3. 生物信息学预测（PONDR 预测 IDR；TANGO 预测 APR）
  4. AlphaFold Multimer 复合物结构预测（ColabFold 实现）
  5. 互作界面分析（PAE/pLDDT 评估 + ChimeraX 距离测量）
  6. 功能验证（APR 缺失突变、肽段竞争、Co-IP）
  7. 功能基因组学（G1E-ER4 红系分化模型 + RNA-Seq）
- **训练**：无监督训练（AlphaFold2/Multimer 为预训练模型，本文未进行微调）。
- **工具**：PONDR、TANGO、ColabFold（AlphaFold2/Multimer）、MaxQuant、Perseus、STAR、DESeq2、ShinyGO、ChimeraX。
- **反馈回路**：AP-MS 候选互作 → AlphaFold 结构预测 → 界面距离测量 → 突变/肽段验证 → 功能实验（RNA-Seq）→ 修正互作模型。
- **假设**：① N/C 末端片段过表达可反映全长蛋白的互作特性；② AlphaFold 预测的界面在生理条件下具有相关性；③ APR 缺失不影响整体蛋白折叠（因区域本身无序）。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AP-MS 互作组学 | 系统鉴定 CHD N/C 末端互作蛋白 | 建立 PPI 网络，发现候选互作 | 输入：FLAG-CHD 片段；输出：互作蛋白列表 | Results 图 2-3；已知互作（NuRD、ChAHP）被验证 | 无此模块则无法获得实验互作数据，AlphaFold 预测缺乏候选输入 |
| PONDR/TANGO 预测 | 鉴定 IDR 和 APR 位置 | 定位潜在互作热点区域 | 输入：CHD 序列；输出：无序/聚集倾向分数 | Results 图 1B；CHD4 APR 被 TANGO 识别 | 移除后无法系统定位 APR，CHD4 功能研究缺乏起点 |
| AlphaFold Multimer | 预测候选互作复合物结构 | 评估互作可能性与界面位置 | 输入：候选蛋白对序列；输出：复合物模型 + PAE/pLDDT | Results 图 4；CHD4-C:ADNP、CHD4-C:GATADB2 高置信预测 | 移除后无法获得结构层面的互作证据，界面定位依赖纯实验（成本高） |
| 距离测量（ChimeraX） | 量化 APR 与互作伴侣的距离 | 判断 APR 是否直接参与界面 | 输入：AlphaFold 模型；输出：原子距离 | Results 图 4C；CHD2-C-APR 与 RTF1 距离 3-7Å | 移除后无法区分「直接互作」与「间接贡献」 |
| APR 缺失突变 + AP-MS | 功能验证 APR 在互作中的必要性 | 建立因果联系 | 输入：CHD4-C-APR Del 构建体；输出：互作蛋白丰度变化 | Results 图 5B-C；NuRD 和 ADNP 富集显著降低 | 移除后 APR 功能仅停留在预测层面 |
| 肽段竞争实验 | 验证 APR 是否直接参与互作界面 | 排除间接效应 | 输入：CHD4-APR 肽段 + 细胞裂解液；输出：互作蛋白下拉量变化 | Results 图 5E；肽段竞争消除 NuRD/ADNP 互作 | 移除后无法区分「APR 直接介导」与「APR 影响蛋白折叠」 |
| G1E-ER4 红系分化 + RNA-Seq | 评估 APR 功能的生物学后果 | 将分子互作与表型联系 | 输入：APR 肽段处理细胞；输出：差异表达基因 | Results 图 6；248 个基因差异表达 | 移除后 APR 功能仅停留在体外互作层面 |

## 09 关键公式符号

**不适用**——本文为实验生物学与结构预测研究，未使用数学公式或统计模型。核心定量指标为质谱丰度（iBAQ）、差异表达（log2 fold-change, FDR）和 AlphaFold 置信度分数（PAE, pLDDT），均为软件输出而非公式推导。

## 10 实验设计与证据链

**数据集/群体**：
- AP-MS：22 个 CHD 片段（19 个成功表达），3 次重复；9 次空载体对照
- AlphaFold：7 个候选复合物（CHD1-N:EHMT1, CHD5-N:BRD8, CHD6-N:ANP32A, CHD9-C2:DNBJ6, CHD2-C:RTF1, CHD4-C:ADNP, CHD4-C:GATADB2）
- 肽段实验：CHD4-APR（YWLLAGII-Tat）vs CTRL（AAAAAAA-Tat）
- RNA-Seq：G1E-ER4 细胞，APR vs CTRL 处理，3 次重复

**指标**：
- AP-MS：蛋白富集倍数（vs 空载体）、唯一肽段数
- AlphaFold：PAE（<5Å 为高置信互作）、pLDDT（>70 为高置信结构域）
- RNA-Seq：FDR < 0.05，|log2FC| > 1.5

**基线/对照**：
- AP-MS：空载体 FLAG 对照
- 肽段实验：丙氨酸替换肽段（CTRL）
- RNA-Seq：CTRL 肽段处理

**预算/仪器**：未提供具体预算；质谱为 Q-Exactive HF-X；结构预测为 ColabFold（免费）。

**评测协议**：AP-MS 数据经 MaxQuant 处理，Perseus 缺失值插补；RNA-Seq 经 STAR 比对、DESeq2 差异分析。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| AP-MS（N 端） | CHD N 端存在亚家族特异性互作 | 19 个片段 vs 空载体 | 鉴定到多种染色质相关因子，亚家族间互作谱不同 | CHD N 端介导特异性 PPI | 互作是否直接（vs 间接）未证明 | Results 图 2 |
| AP-MS（C 端） | CHD C 端存在亚家族特异性互作 | 同上 | NuRD 亚基富集于 CHD3-5；ADNP 富集于 CHD4 | CHD3-5 C 端介导 NuRD/ChAHP 互作 | 互作界面未定位 | Results 图 3 |
| AlphaFold Multimer | 候选互作为直接互作 | 7 对复合物预测 | CHD2-C:RTF1、CHD4-C:ADNP、CHD4-C:GATADB2 高置信（低 PAE） | 这些互作可能为直接互作 | 预测需实验验证；无序区域 pLDDT 低 | Results 图 4A-B |
| 距离测量 | APR 直接参与互作界面 | ChimeraX 测量 | CHD2-C-APR 与 RTF1 距离 3-7Å；CHD4-C-APR 与 ADNP/GATADB2 距离 >7Å | CHD2-C-APR 可能直接互作；CHD4-C-APR 可能间接贡献 | 距离测量基于预测模型，非实验结构 | Results 图 4C |
| APR 缺失突变 + AP-MS | CHD4 APR 对互作必要 | CHD4-C vs CHD4-C-APR Del | NuRD 亚基和 ADNP 富集显著降低 | APR 是 CHD4 互作的关键区域 | 其他区域（1453-1513）也可能参与 | Results 图 5B-C |
| Co-IP 验证 | APR 介导的直接互作 | GATADB2-C + CHD4-C vs Del | 突变体结合减少但未完全消除 | APR 部分介导互作 | 存在其他互作界面 | Results 图 5D |
| 肽段竞争 | APR 直接参与互作界面 | APR 肽段 vs CTRL 肽段 | APR 肽段消除 NuRD/ADNP 下拉 | APR 直接介导互作 | 竞争是否完全特异未量化 | Results 图 5E |
| RNA-Seq（红系分化） | APR 功能影响转录程序 | APR vs CTRL 肽段处理 | 248 个基因差异表达，涉及代谢和转录调控 | APR 功能影响红系分化转录 | 因果关系（直接 vs 间接）未建立 | Results 图 6 |

## 11 结论正确解读

- **任务范围**：本文仅覆盖 CHD 家族 N/C 末端片段（非全长蛋白）的互作；互作网络为过表达条件下的互作组，非内源水平。
- **oracle/真值输入**：AlphaFold Multimer 预测以序列为输入，无实验结构约束；预测结果仅作为候选假设，非真值。
- **端到端状态**：从互作鉴定到功能验证的完整链条已建立，但未达到「端到端」——未在动物模型中验证 APR 功能，未解析全长 CHD4 复合物的高分辨率结构。
- **算力成本**：未提供；ColabFold 为免费云服务，成本可控。
- **历史数据依赖**：依赖已有互作数据库（如已知 NuRD/ChAHP 亚基组成）来验证 AP-MS 结果。
- **模型依赖**：AlphaFold Multimer 对无序区域的预测置信度低（作者明确承认），互作界面定位可能不精确。
- **最难情形**：无序区域介导的互作（AlphaFold 预测困难）；多亚基复合物中的竞争性互作（AP-MS 难以区分直接/间接）。
- **群体/领域边界**：结论局限于 CHD 家族和红系分化模型；不适用于其他染色质重塑家族或细胞类型。
- **不确定性**：APR 缺失突变可能影响蛋白稳定性（作者未做结构验证）；肽段竞争实验的 IC50 未测定；RNA-Seq 差异基因的因果关系未验证。

**有边界的复述**：在 CHD 家族 N/C 末端片段过表达条件下，AP-MS 鉴定到亚家族特异性互作网络；AlphaFold Multimer 预测 CHD4 C 末端 APR（YWLLAGII）可能介导与 ADNP/GATADB2 的互作；APR 缺失和肽段竞争实验支持该 APR 对互作的功能贡献；在 G1E-ER4 红系分化模型中，APR 肽段处理导致 248 个基因差异表达。这些结论不推广至全长蛋白内源互作或其他细胞类型。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| AlphaFold 对无序区域预测置信度低 | CHD 多肽在复合物预测中 pLDDT 分数低 | 未明确提及 | Results 图 4 讨论 |
| 全长 CHD 蛋白 PPI 研究困难 | 大蛋白、高核酸亲和力导致技术挑战 | 聚焦 N/C 末端片段以规避 | Discussion 首段 |
| 过表达可能导致互作假象 | 片段过表达可能产生非生理互作 | 未明确提及 | Discussion（间接） |
| RNA-Seq 使用低浓度 APR 肽段 | 可能仅部分抑制互作，限制表型幅度 | 使用更高浓度或遗传突变模型 | Discussion（间接） |
| 未验证 APR 缺失对蛋白折叠的影响 | 突变可能影响蛋白稳定性而非仅互作 | 未明确提及 | 未提供 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| AP-MS 使用片段而非全长蛋白 | 片段可能暴露隐藏互作界面或失去全长构象依赖的互作 | 互作网络可能不代表内源状态 | 使用全长 CHD4 进行 AP-MS 或 CRISPR 内源标签 | Methods 节 |
| AlphaFold 对无序区域预测的可靠性存疑 | 低 pLDDT 区域的界面预测可能为假阳性 | 互作界面定位可能不准确 | 用交联质谱（XL-MS）或 NMR 验证界面 | Results 图 4 |
| APR 缺失突变可能影响蛋白稳定性 | 观察到的互作减少可能源于蛋白降解而非互作界面破坏 | 功能归因可能错误 | 检测突变体蛋白稳定性（如 western blot 半衰期） | Results 图 5B-C |
| 肽段竞争实验缺乏剂量-反应曲线 | 未提供 IC50，无法判断互作亲和力 | 无法评估 APR 互作的强度 | 进行梯度肽段竞争实验 | Results 图 5E |
| RNA-Seq 差异基因与 APR 功能的因果关系未验证 | 248 个差异基因可能为间接效应 | 无法确定 APR 的直接转录靶点 | ChIP-Seq 定位 CHD4 结合位点，与 RNA-Seq 联合分析 | Results 图 6 |
| 未检测 DNA 结合活性 | CHD 是染色质重塑因子，APR 可能影响 DNA 结合而非仅蛋白互作 | 功能机制可能涉及 DNA 结合 | 电泳迁移率变动分析（EMSA）或 DNA 下拉实验 | 未提供 |
| 「相互排斥」假说缺乏直接证据 | 作者提出 APR 可能以互斥方式结合 NuRD 或 ChAHP，但未进行竞争实验 | 互作调控机制不明 | 同时表达 ADNP 和 GATADB2 观察竞争 | Discussion |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **无序区域中的短线性基序（SLiMs）作为互作热点**：本文证明 CHD4 C 末端一个 8 残基 APR（YWLLAGII）即可介导与多个复合物的互作。**迁移到 TF–DNA 互作**：TF 的 IDR 中可能含有类似的短 DNA 结合基序或蛋白互作基序，可用类似策略（预测 + 突变 + 肽段竞争）鉴定。

2. **AP-MS + AlphaFold Multimer 的联合工作流**：AP-MS 提供候选互作列表，AlphaFold 提供结构层面的互作可能性评估，两者互补。**迁移**：在 TF–DNA 互作研究中，可用 ChIP-Seq/DAP-Seq 鉴定候选 DNA 靶点，再用 AlphaFold 或 RoseTTAFold 预测 TF-DNA 复合物结构，最后用突变/EMSA 验证。

3. **PAE 作为互作可能性指标**：低 PAE 区域指示高置信互作界面，即使整体复合物预测置信度不高。**迁移**：在 TF-DNA 复合物预测中，可关注 PAE 较低的 DNA 结合界面区域，优先进行实验验证。

4. **肽段竞争实验验证短序列介导的互作**：用含 APR 的肽段竞争内源互作，是验证「短序列直接介导互作」的高效方法。**迁移**：可设计含 TF DNA 结合基序的肽段，竞争 TF-DNA 互作，用于功能研究或治疗干预。

5. **互斥性互作界面的概念**：同一 APR 可能以互斥方式结合不同伴侣，实现功能切换。**迁移**：TF 的同一 DNA 结合域可能以互斥方式结合不同 DNA 基序或不同辅因子，这可能是 TF 功能多样性的机制。

6. **IDR 富集区域的系统分析策略**：先用 PONDR/TANGO 等工具定位 IDR/APR，再聚焦功能验证。**迁移**：对 TF 家族进行系统 IDR 分析，可发现未被注释的功能性短基序。

## 15 与已有知识连接

- **CHD 家族与 NuRD/ChAHP 复合物**：已知 CHD3-5 是 NuRD 复合物的 ATP 酶亚基（Torrado et al., 2017），CHD4 也存在于 ChAHP 复合物（Ostapcuk et al., 2018）。本文进一步定位了互作界面在 C 末端 APR 区域。
- **IDR 在染色质调控中的作用**：IDR 介导相分离和染色质互作的报道日益增多（Patil et al., 2023）。本文为 IDR 在染色质重塑因子中的功能提供了新证据。
- **AlphaFold 在互作预测中的应用**：AlphaFold-Multimer（Evans et al., 2022）已被广泛用于蛋白复合物预测，但对无序区域的局限已有报道（Bret et al., 2024）。本文的「预测 + 实验验证」策略与此共识一致。
- **与 TF–DNA 互作课题的关联**：本文方法（AP-MS + AlphaFold + 肽段竞争）可迁移至 TF-辅因子互作研究；IDR 中短基序介导互作的发现提示 TF 的 IDR 区域可能含有未被注释的 DNA 结合或蛋白互作基序。
- **候选方向**：将本文的「IDR/APR 定位 → 互作网络 → 功能验证」流程应用于 TF 家族，可能发现新的 TF-辅因子互作界面；AlphaFold 预测 + 实验验证的组合策略可直接用于 TF-DNA 复合物研究。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF-IDR 短基序互作网络图谱
   - **来源局限/观察**：本文证明 CHD 家族 IDR 中短 APR 介导特异性互作；TF 的 IDR 可能具有类似功能但未被系统研究。
   - **核心假设**：TF 家族 IDR 中的短线性基序（SLiMs）介导与辅因子或 DNA 的特异性互作，决定 TF 功能特异性。
   - **初步方法**：对全部人类 TF 进行 IDR/SLiM 预测（IUPred, ANCHOR, SLiMPrints），结合 AP-MS 或 BioID 鉴定互作网络，用 AlphaFold-Multimer 预测候选互作界面，突变 + 肽段竞争验证。
   - **验证方式**：在细胞模型中验证关键互作对功能（如报告基因、ChIP-Seq）；比较不同 TF 亚家族互作网络差异。
   - **创新状态**：unverified

2. **候选名称**：AlphaFold 预测 TF-DNA 复合物的可靠性评估
   - **来源局限/观察**：本文用 AlphaFold-Multimer 预测蛋白-蛋白互作，但对无序区域置信度低；TF-DNA 复合物预测的可靠性尚未系统评估。
   - **核心假设**：AlphaFold 对 TF-DNA 复合物的预测精度与 TF 的 IDR 含量负相关；对结构化 DNA 结合域预测可靠，对 IDR 介导的 DNA 结合不可靠。
   - **初步方法**：收集已知 TF-DNA 复合物结构（PDB），用 AlphaFold 预测并与实验结构比对；按 IDR 含量分层分析预测精度；开发 IDR 感知的预测后处理流程。
   - **验证方式**：用 EMSA 或表面等离子共振（SPR）验证预测的 TF-DNA 互作界面。
   - **创新状态**：unverified

3. **候选名称**：TF 互作界面肽段抑制剂设计
   - **来源局限/观察**：本文的肽段竞争实验成功干扰 CHD4-辅因子互作；TF-辅因子互作界面可作为药物靶点。
   - **核心假设**：针对 TF IDR 中关键 SLiM 的肽段可特异性阻断 TF-辅因子互作，调控下游转录程序。
   - **初步方法**：从本文的 TF-IDR 互作网络中选择关键互作对，设计含 SLiM 序列的细胞穿透肽（CPP 偶联），在细胞模型中测试对靶基因表达的影响。
   - **验证方式**：RNA-Seq 评估转录组变化；ChIP-Seq 验证 TF 染色质结合变化。
   - **创新状态**：unverified

4. **候选名称**：互斥性互作界面的分子动力学研究
   - **来源局限/观察**：本文提出 CHD4 APR 可能以互斥方式结合 NuRD 或 ChAHP；这种「一个基序、多个伴侣」的机制在 TF 中可能普遍存在。
   - **核心假设**：TF 的同一 SLiM 可通过构象选择或竞争结合不同辅因子，实现信号整合和功能切换。
   - **初步方法**：选择 TF 中已知的互斥互作对，用分子动力学（MD）模拟 SLiM 与不同伴侣的结合自由能，比较结合模式；用突变体破坏一个互作观察另一个互作是否增强。
   - **验证方式**：等温滴定量热法（ITC）测量结合亲和力；细胞实验验证互斥性。
   - **创新状态**：unverified