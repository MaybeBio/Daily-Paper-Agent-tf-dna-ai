## 01 基本信息
- **标题**：Mechanism of High-Affinity KEAP1 Recruitment by USP25 via a Specialized ETGQ Motif
- **作者与单位**：Ning, Xuan; Hu, Fangning; Su, Zihui; Ming, Zhenhua; Luo, Beibei（单位未提供）
- **期刊/预印本平台**：Journal of Molecular Biology
- **年份**：2026
- **论文类型**：实验研究（含结构建模与突变分析）
- **领域**：蛋白质-蛋白质互作；KEAP1-NRF2 信号通路；去泛素化酶
- **关键词**：KEAP1；USP25；ETGQ motif；Kelch domain；AlphaFold 3；蛋白质-蛋白质互作抑制剂
- **DOI/arXiv 号**：10.1016/j.jmb.2026.169955
- **代码**：未提供
- **数据**：未提供（结构模型与突变数据见正文，未附公共数据库编号）
- **阅读日期**：未提供
- **该文在「蛋白质-DNA 互作(聚焦 TF–DNA 结合机制) × AI 方法/物理模拟」方向中的位置**：本文研究对象为蛋白质-蛋白质互作（KEAP1 Kelch 结构域与 USP25 催化结构域），而非蛋白质-DNA 互作。但其核心方法——AlphaFold 3 结构预测 + 结构引导突变 + 经典结合口袋突变分析——可直接迁移至 TF–DNA 结合机制研究，尤其是预测 TF 的 DNA 结合 motif 与识别特异性、设计结合界面突变体等场景。本文的「非经典 motif 识别」思路对理解 TF 的非经典 DNA 结合模式亦有借鉴意义。

## 02 一句话总结
本文通过凝胶过滤、ITC、经典 Kelch 口袋突变分析、简单序列搜索、AlphaFold 3 建模与结构引导突变，证明 USP25 催化结构域通过一个非经典 ETGQ motif 以高亲和力直接结合 KEAP1 Kelch 结构域，并解释了 USP28 因缺乏该 motif 而不调控 KEAP1-NRF2 轴。

## 03 研究问题
- **具体问题**：USP25 与 KEAP1 相互作用的分子基础是什么？USP25 如何以高亲和力结合 KEAP1 Kelch 结构域？为何同源蛋白 USP28 不参与该互作？
- **为什么重要**：KEAP1-NRF2 轴是细胞抗氧化反应的主要调控通路，USP25 被鉴定为 KEAP1 的关键稳定因子，但其结合机制不明，阻碍了针对氧化应激相关疾病的 PPI 抑制剂设计。
- **现有方法为何不足**：此前仅知 USP25 稳定 KEAP1，缺乏对结合界面、关键 motif 及亲和力贡献的分子层面解析；经典 Kelch 结合 motif（如 ETGE、DLG）搜索未能解释 USP25 的结合方式。
- **精确研究问题（Can 问题）**：Can a non-canonical ETGQ motif in USP25's catalytic domain mediate high-affinity binding to the KEAP1 Kelch domain, and does its absence in USP28 explain the functional divergence?

## 04 背景与发展脉络
- **阶段一：KEAP1-NRF2 通路发现与功能研究**。代表性方法：遗传与生化鉴定。优点：确立通路核心地位。局限：缺乏互作分子细节。
- **阶段二：KEAP1 Kelch 结构域经典 motif 识别研究**。代表性方法：晶体结构、肽段 pull-down、突变分析。优点：鉴定 ETGE、DLG 等经典结合 motif。局限：主要针对 NRF2 等已知配体，对去泛素化酶类配体覆盖不足。
- **阶段三：USP25 作为 KEAP1 稳定因子的功能研究**。代表性方法：RNAi 筛选、泛素化实验。优点：确立 USP25 的功能角色。局限：未解析结合界面与 motif。
- **阶段四（本文）**：结合 AlphaFold 3 结构预测、ITC、结构引导突变与经典口袋突变分析，鉴定非经典 ETGQ motif，并解释 USP28 的功能差异。
- **脉络标注**：以上脉络为「经外部核验」的领域常识（KEAP1-NRF2 通路、Kelch 经典 motif 为公开文献内容），但阶段划分与本文定位为「仅本文框架」的整理。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 经典 motif 搜索无法解释 USP25 结合 | 已知 Kelch 结合 motif（ETGE/DLG）在 USP25 中不匹配 | USP25 使用非经典 ETGQ motif，序列搜索需扩展 | 摘要「simple sequence searching」识别 ETGQ；正文未提供具体搜索细节 |
| 同源蛋白功能差异无分子解释 | USP28 不调控 KEAP1-NRF2 轴 | USP28 缺乏 ETGQ motif，无法结合 Kelch 结构域 | 摘要「closely related homolog USP28 does not regulate」；具体序列比对未提供 |
| 缺乏高分辨率互作界面信息 | 无 USP25-KEAP1 复合物晶体结构 | 作者未声明；可能因复合物难以结晶 | 未提供；作者改用 AlphaFold 3 建模替代 |
| 亲和力贡献的残基级解析缺失 | 未知哪些残基驱动高亲和力 | 作者通过结构引导突变逐点验证 | 摘要「structure-guided mutagenesis」；具体残基与数据未提供 |

## 06 核心思想
1. **表面方法**：凝胶过滤验证直接结合；ITC 测定亲和力；经典 Kelch 口袋突变确认结合位点；简单序列搜索寻找候选 motif；AlphaFold 3 建模预测复合物结构；结构引导突变验证 motif 关键残基。
2. **核心洞察**：USP25 通过一个非经典 ETGQ motif 结合 KEAP1 Kelch 结构域的经典结合口袋，该 motif 在序列上不同于已知的 ETGE/DLG，但功能上等效；USP28 因缺乏该 motif 而丧失结合能力，从而解释了同源蛋白的功能分化。
3. **可能的普适教训 [Analysis]**：在蛋白质互作研究中，当经典 motif 搜索失败时，应结合结构预测（如 AlphaFold 3）与口袋突变分析反向鉴定非经典 motif；同源蛋白的功能差异常可追溯到单个 motif 的获得/缺失，这为功能演化研究提供切入点。

## 07 方法总览
- **输入**：USP25 催化结构域、KEAP1 Kelch 结构域的重组蛋白；USP25 与 USP28 的序列；AlphaFold 3 的序列输入。
- **输出**：结合亲和力（ITC 数据）、结合界面模型（AlphaFold 3）、关键残基功能验证（突变体结合实验）。
- **模块**：
  1. 蛋白表达与纯化（凝胶过滤）
  2. 结合亲和力测定（ITC）
  3. 经典口袋突变分析（KEAP1 侧）
  4. 序列搜索（USP25 侧 motif 鉴定）
  5. AlphaFold 3 结构建模
  6. 结构引导突变（USP25 侧验证）
- **训练**：不适用（无机器学习训练；AlphaFold 3 为预训练模型）。
- **工具**：AlphaFold 3；ITC 仪器；凝胶过滤系统。
- **反馈回路**：AlphaFold 3 预测 → 突变设计 → 结合实验 → 模型修正（若突变结果与预测不符）。
- **假设**：KEAP1 Kelch 结构域的结合口袋是 USP25 结合的唯一/主要位点；AlphaFold 3 预测的界面在溶液中真实存在。
- **文字流程**：纯化 USP25 催化结构域与 KEAP1 Kelch 结构域 → 凝胶过滤确认复合物形成 → ITC 测定亲和力 → 对 KEAP1 经典口袋残基突变，检测对 USP25 结合的影响 → 在 USP25 序列中搜索与已知 motif 相似的序列，发现 ETGQ → 用 AlphaFold 3 建模 USP25-KEAP1 复合物 → 根据模型对 ETGQ 及周围残基突变 → 验证突变体结合能力 → 对比 USP28 序列，确认缺乏 ETGQ → 得出结论。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 凝胶过滤 | 验证 USP25 与 KEAP1 是否形成稳定复合物 | 初步确认直接互作 | 输入：两蛋白混合液；输出：复合物峰 | 摘要「gel filtration ... show that ... binds directly」 | 预期影响：失去互作初步证据，后续实验缺乏前提（预期效应） |
| ITC | 定量结合亲和力与热力学参数 | 确认高亲和力并量化 | 输入：两蛋白溶液；输出：Kd、ΔH、ΔS | 摘要「high affinity」；具体数值未提供 | 预期影响：无法判断亲和力高低，削弱「高亲和力」结论（预期效应） |
| 经典口袋突变分析 | 确认 USP25 结合于 Kelch 经典结合口袋 | 验证结合位点特异性 | 输入：KEAP1 口袋突变体；输出：结合变化 | 摘要「mutational analysis of the canonical Kelch binding pocket」 | 预期影响：无法确认结合位点，AlphaFold 模型缺乏实验锚定（预期效应） |
| 简单序列搜索 | 在 USP25 中寻找候选 motif | 经典 motif 不匹配，需扩展搜索 | 输入：USP25 序列；输出：ETGQ motif | 摘要「simple sequence searching」；具体方法未提供 | 预期影响：无法定位候选 motif，后续验证无靶点（预期效应） |
| AlphaFold 3 建模 | 预测 USP25-KEAP1 复合物结构 | 无晶体结构，需结构信息指导突变 | 输入：两蛋白序列；输出：预测复合物模型 | 摘要「AlphaFold 3 structural modeling」 | 预期影响：失去结构指导，突变设计盲目（预期效应） |
| 结构引导突变 | 验证 ETGQ motif 关键残基的功能 | 确认 motif 对结合的必要性与充分性 | 输入：USP25 突变体；输出：结合能力变化 | 摘要「structure-guided mutagenesis ... required and sufficient」 | 预期影响：无法证明 motif 的因果作用（预期效应） |

## 09 关键公式符号
不适用。本文为实验与结构建模研究，摘要中未出现定量公式；ITC 数据（Kd 等）未在摘要中给出具体数值。

## 10 实验设计与证据链
- **数据集/群体**：重组蛋白（USP25 催化结构域、KEAP1 Kelch 结构域、USP28 同源蛋白）；突变体库（KEAP1 口袋突变体、USP25 ETGQ 突变体）。
- **规模**：未提供（突变体数量、实验重复数未在摘要中说明）。
- **指标**：结合亲和力（ITC Kd）、复合物形成（凝胶过滤峰位）、结合能力变化（突变体对比）。
- **基线**：野生型 USP25 与 KEAP1 的结合；USP28 与 KEAP1 的结合（阴性对照）。
- **预算**：未提供。
- **骨干/仪器**：凝胶过滤系统、ITC 仪器、AlphaFold 3（计算）。
- **oracle 输入**：AlphaFold 3 预测结构作为突变设计的指导。
- **评测协议**：未提供（无明确统计检验描述）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|------------------|------|
| 凝胶过滤 | USP25 与 KEAP1 直接结合 | 两蛋白混合 vs 单独 | 出现复合物峰 | 直接互作 | 无法判断亲和力高低 | 摘要 |
| ITC | 高亲和力结合 | 野生型 USP25 vs KEAP1 | 高亲和力（数值未提供） | 高亲和力互作 | 无法判断热力学细节 | 摘要 |
| 经典口袋突变 | USP25 结合于 Kelch 经典口袋 | 口袋突变体 vs 野生型 KEAP1 | 结合减弱或消失（具体未提供） | 结合位点为经典口袋 | 无法排除其他口袋外接触 | 摘要 |
| 序列搜索 | USP25 含非经典 motif | USP25 vs 已知 motif 数据库 | 发现 ETGQ | ETGQ 为候选 motif | 无法证明功能 | 摘要 |
| AlphaFold 3 建模 | 预测复合物结构 | 预测 vs 无实验结构 | 获得模型 | 提供结构假设 | 无法替代实验验证 | 摘要 |
| 结构引导突变 | ETGQ 对结合必要且充分 | ETGQ 突变体 vs 野生型；USP28 对照 | 突变体结合丧失；USP28 不结合 | ETGQ 是结合的关键 motif | 无法证明 ETGQ 单独足以驱动结合（需嵌合实验） | 摘要 |

## 11 结论正确解读
- **任务范围**：本文仅覆盖 USP25 催化结构域与 KEAP1 Kelch 结构域的结合机制，不涉及全长 USP25 的其他功能域、KEAP1 的其他配体、或细胞内的动态调控。
- **oracle/真值输入**：AlphaFold 3 预测结构作为突变设计的指导，但预测本身未经晶体学验证；结论依赖预测模型的准确性。
- **端到端状态**：非端到端；实验验证了结合，但未在细胞或动物水平验证功能后果。
- **算力成本**：未提供（AlphaFold 3 运行成本未说明）。
- **历史数据依赖**：依赖已知 Kelch 经典 motif 知识（ETGE/DLG）作为搜索起点。
- **模型依赖**：结论部分依赖 AlphaFold 3 预测的界面，若预测有误，突变设计可能偏离真实界面。
- **最难情形**：未测试 USP25 在氧化应激条件下的动态结合变化；未测试 ETGQ 突变对 USP25 酶活性的影响。
- **群体/领域边界**：结论限于 USP25-KEAP1 互作，不能推广至所有去泛素化酶-Kelch 互作。
- **不确定性**：ITC 具体数值、突变体表型数据、统计检验均未在摘要中提供，无法评估效应量。
- **有边界的复述**：在重组蛋白体系中，USP25 催化结构域通过 ETGQ motif 以高亲和力结合 KEAP1 Kelch 结构域的经典口袋，且 USP28 因缺乏该 motif 而不结合；该结论限于体外生化与结构预测层面。

## 12 作者自认局限
在提供的材料（摘要）中未发现作者明确承认的局限。
- **作者提及的相关约束**（非正式局限）：摘要未提及；但可推断 AlphaFold 3 预测未经晶体学验证、未进行细胞水平功能实验，这些是摘要中未声明的约束。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| ETGQ motif 的鉴定依赖「simple sequence searching」 | 搜索策略可能偏向已知 motif 相似序列，可能遗漏更远缘的 motif | 若搜索策略有偏，可能错过其他功能相关序列 | 要求作者提供搜索算法、数据库与阈值；用无偏的 motif 发现工具（如 MEME）重新分析 | 摘要「simple sequence searching」未提供细节 |
| AlphaFold 3 预测未经实验结构验证 | 预测界面可能不同于真实结合界面，导致突变设计偏离 | 结构预测误差会直接影响「required and sufficient」结论 | 尝试共结晶或交联质谱验证预测界面 | 摘要「AlphaFold 3 structural modeling」未提及实验验证 |
| 「required and sufficient」的证明强度 | 摘要未说明是否做了嵌合/移植实验（如将 ETGQ 移植到 USP28 上测试结合） | 「sufficient」需要移植实验证明，仅突变丧失结合不足以证明充分性 | 检查正文是否有 USP28-ETGQ 嵌合体结合实验 | 摘要「required and sufficient」但未提供实验细节 |
| USP28 不结合的结论 | 可能因 USP28 整体结构差异而非仅缺 motif | 若 USP28 有其他抑制因素，则「motif 缺失」解释不完整 | 做 USP28 结构域交换或点突变回补实验 | 摘要「closely related homolog USP28 does not regulate」未提供机制证据 |
| 高亲和力的生理相关性 | 体外高亲和力未必反映细胞内竞争环境下的结合 | 若细胞内存在竞争性配体，实际结合可能被调节 | 在细胞裂解液或竞争实验中测试结合 | 摘要未提供细胞实验 |

## 14 Agent 提炼的知识候选
- **候选 1：非经典 motif 的鉴定流程**。本文展示了「经典 motif 搜索失败 → 简单序列搜索扩展 → 结构预测辅助 → 突变验证」的流程。可迁移至 TF–DNA 互作：当已知 DNA 结合 motif（如锌指、bZIP 的经典识别序列）无法解释某 TF 的结合特异性时，可用类似流程（如 ChIP-seq 峰序列的 de novo motif 发现 + AlphaFold 3 预测 TF-DNA 复合物 + 关键碱基突变验证）鉴定非经典 DNA 识别模式。
- **候选 2：同源蛋白功能分化的 motif 归因**。本文通过对比 USP25/USP28 的序列差异解释功能分化。可迁移至 TF 家族研究：对同一 TF 家族中结合特异性不同的成员，通过序列比对定位关键差异残基/motif，再用结构预测与突变验证其因果作用。
- **候选 3：AlphaFold 3 作为突变设计指导**。本文用 AlphaFold 3 预测复合物界面并指导突变。可迁移至 TF–DNA：用 AlphaFold 3（或 RoseTTAFoldNA）预测 TF-DNA 复合物，预测界面残基/碱基，设计突变体验证结合特异性。
- **候选 4：经典口袋突变作为结合位点锚定**。本文通过突变 KEAP1 经典口袋确认 USP25 结合位点。可迁移至 TF–DNA：通过突变 TF 的已知 DNA 结合口袋（如螺旋-转角-螺旋的识别螺旋）确认新配体（DNA 序列）是否结合同一口袋。
- **候选 5：ITC 用于亲和力定量**。本文用 ITC 定量结合亲和力。可迁移至 TF–DNA：用 ITC 或表面等离子共振（SPR）定量 TF 与不同 DNA 序列的亲和力，验证 motif 突变对特异性的影响。

## 15 与已有知识连接
- **KEAP1-NRF2 通路**：本文直接连接至 KEAP1-NRF2 抗氧化通路（公开文献，如 Itoh et al. 1999, Genes Dev；Taguchi et al. 2011, Genes Dev），本文补充了 USP25 作为 KEAP1 稳定因子的分子机制。
- **Kelch 结构域经典 motif**：本文连接至 Kelch 结构域识别 ETGE/DLG motif 的经典研究（如 Tong et al. 2006, Mol Cell Biol；Lo et al. 2006, J Biol Chem），本文扩展了非经典 motif 的识别。
- **AlphaFold 3 应用**：本文连接至 AlphaFold 3 在蛋白质-蛋白质互作预测中的应用（Abramson et al. 2024, Nature），本文为其在去泛素化酶-Kelch 互作中的具体应用。
- **USP 家族功能分化**：本文连接至 USP 家族去泛素化酶的功能研究（公开文献），本文为 USP25/USP28 的功能分化提供分子解释。
- **可迁移领域**：本文的「非经典 motif 鉴定 + 结构预测 + 突变验证」流程可迁移至 TF–DNA 互作研究，尤其是非经典 DNA 结合模式的发现。

## 16 Agent 生成的研究候选
- **候选 1：TF 非经典 DNA 结合 motif 的系统鉴定**
  - 名称：Non-canonical DNA-binding motif discovery in TFs
  - 来源局限/观察：经典 DNA 结合 motif 搜索常无法解释部分 TF 的结合特异性（本文中经典 Kelch motif 搜索失败的平行情况）
  - 核心假设：部分 TF 通过非经典 motif 结合 DNA，且这些 motif 可通过「de novo motif 发现 + 结构预测 + 突变验证」流程鉴定
  - 初步方法：对 ChIP-seq 峰序列做 de novo motif 发现（如 MEME）；用 AlphaFold 3 预测 TF-DNA 复合物；对候选 motif 残基/碱基做突变验证
  - 验证方式：体外结合实验（EMSA、ITC）验证突变体结合变化；体内报告基因实验验证功能
  - 可能的失败模式：结构预测误差导致 motif 定位错误；非经典 motif 可能依赖协同因子，体外难以重现
  - 创新状态：unverified
- **候选 2：TF 家族同源蛋白 DNA 结合特异性的 motif 归因**
  - 名称：Motif-based divergence of DNA-binding specificity in TF families
  - 来源局限/观察：本文通过 USP25/USP28 序列差异解释功能分化，TF 家族中类似问题普遍存在
  - 核心假设：TF 家族成员间的 DNA 结合特异性差异可定位到少数关键残基/motif
  - 初步方法：对 TF 家族成员做序列比对，定位差异残基；用 AlphaFold 3 预测各成员与不同 DNA 序列的复合物；对候选残基做交换突变
  - 验证方式：突变体结合特异性检测（蛋白结合微阵列或 SELEX）
  - 可能的失败模式：特异性差异可能由多个残基协同决定，单点突变不足以改变特异性
  - 创新状态：unverified
- **候选 3：AlphaFold 3 预测 TF-DNA 复合物的系统评估**
  - 名称：Benchmarking AlphaFold 3 for TF-DNA complex prediction
  - 来源局限/观察：本文用 AlphaFold 3 预测蛋白质-蛋白质复合物，但 TF-DNA 复合物预测的准确性未知
  - 核心假设：AlphaFold 3 对 TF-DNA 复合物的预测准确性足以指导突变设计
  - 初步方法：收集已知 TF-DNA 复合物晶体结构，用 AlphaFold 3 预测，对比界面残基/碱基的预测准确率
  - 验证方式：与 PDB 结构比对，计算界面残基/碱基的预测精度
  - 可能的失败模式：AlphaFold 3 对 DNA 构象的预测精度不足，导致界面预测偏差
  - 创新状态：partially checked（AlphaFold 3 已有公开基准，但针对 TF-DNA 的系统评估未在本文中提供）
- **候选 4：KEAP1 非经典配体的全基因组搜索**
  - 名称：Genome-wide search for non-canonical KEAP1-binding motifs
  - 来源局限/观察：本文发现 USP25 用非经典 ETGQ motif 结合 KEAP1，提示可能存在其他非经典配体
  - 核心假设：人类蛋白质组中存在多个含 ETGQ 类似 motif 的 KEAP1 结合蛋白
  - 初步方法：用 ETGQ 及变体 motif 搜索人类蛋白质组；对候选蛋白做结合实验验证
  - 验证方式：ITC 或 pull-down 验证结合；细胞实验验证功能
  - 可能的失败模式：motif 单独不足以驱动结合，需结构上下文支持
  - 创新状态：unverified