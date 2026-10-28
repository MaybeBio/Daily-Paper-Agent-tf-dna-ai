## 01 基本信息
- **标题**：Decoding microglial metabolic cell death and PANoptosis hub genes in subacute phase of traumatic brain injury: a multi-omics and experimental validation study
- **作者与单位**：Wu, Zhe; Yang, Bao-Ya; Lai, Jin-Qing; Lin, Shi-Hong; Lin, Long; Chen, Jian-Long; Pan, Jia-Xiang; Ruan, Yao-Xin; Chen, Xiang-Rong（单位未提供）
- **期刊/预印本平台**：Apoptosis : an international journal on programmed cell death
- **年份**：2026（在线日期 2026-03-19）
- **论文类型**：多组学整合 + 实验验证研究
- **领域**：神经炎症 / 创伤性脑损伤（TBI）/ 细胞死亡（PANoptosis、代谢性细胞死亡）/ 小胶质细胞
- **关键词**：TBI、小胶质细胞、PANoptosis、代谢性细胞死亡、hub genes、WGCNA、AlphaFold3、EMSA
- **DOI/arXiv 号**：10.1007/s10495-025-02236-4
- **代码**：未提供
- **数据**：NCBI GEO 数据库（bulk 与 single-cell RNA-seq 数据集，具体编号未提供）
- **阅读日期**：未提供
- **该文在「蛋白质-DNA 互作(聚焦 TF–DNA 结合机制) × AI 方法/物理模拟」方向中的位置**：本文并非以 TF–DNA 互作为核心，但包含一个关键的可迁移环节——使用 **AlphaFold3 预测转录因子（Batf、Irf8）与靶基因启动子区的结合构象**，并用 **EMSA** 实验验证。这属于「AI 结构预测 + 湿实验验证」的 TF–DNA 结合机制研究范式，可作为该课题方向中「AI 预测结合构象 → 实验确认」流程的参考案例。

## 02 一句话总结
该研究通过整合 bulk 与 single-cell RNA-seq 数据，用 WGCNA 和 MCC 算法鉴定出 TBI 亚急性期小胶质细胞中 PANoptosis 与代谢性细胞死亡共有的 7 个 hub genes，并预测及验证了转录因子 Batf 和 Irf8 对这些基因的协同调控，提示不同细胞死亡通路存在共享的 nodal molecules。

## 03 研究问题
- **具体问题**：在 TBI 亚急性期，小胶质细胞中调控 PANoptosis 与代谢性细胞死亡的关键基因（hub genes）是什么？这些基因是否受共同转录因子调控？
- **为什么重要**：TBI 后小胶质细胞介导的神经炎症与代谢紊乱是病理进展的核心，但不同细胞死亡通路间的交叉调控节点尚不明确，识别共享调控分子可为 TBI 治疗提供新靶点。
- **现有方法为何不足**：既往研究多聚焦单一细胞死亡通路或单一组学，缺乏跨通路、跨组学（bulk + single-cell）的系统性整合，也缺乏对上游转录调控机制的实验验证。
- **精确的「Can ... ?」研究问题**：Can shared transcription factors (e.g., Batf, Irf8) co-regulate hub genes across PANoptosis and metabolic cell death pathways in microglia during the subacute phase of TBI?

## 04 背景与发展脉络
- **脉络标注**：仅本文框架（基于摘要推断，未做外部系统核验）
- **阶段一：单一细胞死亡通路研究**——早期研究分别关注凋亡、坏死性凋亡、焦亡等，代表性方法为单基因或单通路干预。优点：机制清晰；局限：忽略通路间交互。
- **阶段二：PANoptosis 概念提出**——将多种程序性细胞死亡通路整合为 PANoptosis 复合体，强调通路协同。优点：更贴近病理复杂性；局限：上游调控网络仍不明确。
- **阶段三：多组学与网络算法应用**——WGCNA、MCC 等算法用于鉴定疾病相关 hub genes。优点：可系统筛选候选基因；局限：缺乏实验验证与上游调控解析。
- **阶段四（本文主张的位置）**：整合多组学 + 网络算法 + 单细胞轨迹 + 代谢通量预测 + AlphaFold3 结构预测 + EMSA 实验验证，形成「基因筛选 → 调控预测 → 结构验证 → 功能确认」的闭环，特别强调不同细胞死亡通路共享转录调控节点。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 跨通路调控节点不明 | PANoptosis 与代谢性细胞死亡在 TBI 中均被激活，但共享调控基因未知 | 作者认为既往研究局限于单一通路，缺乏系统整合 | 摘要：key regulatory genes governing these processes within microglia remain unclear |
| 上游转录调控机制缺失 | 即使鉴定出 hub genes，其上游转录因子调控网络未被解析 | 作者主张需结合转录因子预测与结合构象验证 | 摘要：ChEA3 predicted that Batf and Irf8 are common transcription factors |
| 计算预测缺乏实验验证 | 多数研究止步于生信筛选，未做湿实验确认 | 作者强调需用 AlphaFold3 + EMSA 双重验证结合构象 | 摘要：validated using both AlphaFold3 and electrophoretic mobility shift assay |
| 细胞异质性被掩盖 | bulk 数据无法区分小胶质细胞亚群差异 | 作者引入 single-cell RNA-seq 与 Monocle2 轨迹分析 | 摘要：Single-cell RNA-seq data revealed differential expression... MG3 |

## 06 核心思想
1. **表面方法**：多组学（bulk + single-cell RNA-seq）数据整合 → WGCNA + MCC 筛选 hub genes → ChEA3 预测转录因子 → AlphaFold3 预测 TF–DNA 结合构象 → EMSA 验证 → CCI 小鼠模型 + 单细胞轨迹 + 代谢通量分析确认。
2. **核心洞察**：不同细胞死亡通路（PANoptosis 与代谢性细胞死亡）可能共享上游转录调控节点（Batf、Irf8），即「通路下游效应不同，但上游调控汇聚」，这为跨通路干预提供了单一靶点可能性。
3. **可能的普适教训 [Analysis]**：在复杂疾病中，与其分别研究各通路，不如先寻找「调控汇聚点」——即多个下游通路共享的转录因子或 hub gene。这一思路可迁移到 TF–DNA 互作研究：优先关注能同时调控多个疾病相关基因的转录因子，而非单个靶基因。

## 07 方法总览
- **输入**：NCBI GEO 数据库中 TBI 亚急性期小鼠的 bulk RNA-seq 与 single-cell RNA-seq 数据。
- **输出**：7 个 hub genes（含 Lgals3、Gbp2、Capg、Timp1）、2 个预测转录因子（Batf、Irf8）、小胶质细胞亚群 MG3 的鉴定及代谢状态预测。
- **模块**：
  1. 数据获取与预处理（GEO 数据库）
  2. WGCNA 共表达网络构建
  3. MCC 算法筛选 hub genes
  4. ChEA3 转录因子预测
  5. AlphaFold3 结构预测（TF–DNA 结合构象）
  6. EMSA 实验验证
  7. CCI 小鼠模型验证
  8. Single-cell RNA-seq 亚群分析 + Monocle2 轨迹 + 代谢通量算法
- **训练**：不适用（非机器学习训练类研究，AlphaFold3 为预训练模型直接应用）。
- **工具**：WGCNA、MCC（cytoscape 插件）、ChEA3、AlphaFold3、Monocle2、代谢通量算法。
- **反馈回路**：计算预测 → 实验验证 → 结果反馈修正对 hub genes 的解读（如 Lgals3、Capg 在不同细胞死亡模态中的差异表达）。
- **文字流程**：从 GEO 获取数据 → bulk 数据经 WGCNA 构建共表达网络 → MCC 筛选 hub genes → ChEA3 预测上游转录因子 → AlphaFold3 预测 TF–DNA 结合构象 → EMSA 验证结合 → 在 CCI 小鼠模型中验证 PANoptosis 与代谢性细胞死亡发生 → single-cell 数据确认 hub genes 在小胶质细胞亚群（MG3）中的差异表达 → Monocle2 分析发育轨迹 → 代谢通量算法预测代谢状态 → 整合所有证据得出结论。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| WGCNA 共表达网络 | 识别与 TBI 亚急性期相关的基因模块 | 无监督筛选疾病相关基因模块，减少维度 | 输入：bulk RNA-seq 表达矩阵；输出：共表达模块 | 摘要：identified through WGCNA | 预期影响：失去模块化筛选，hub gene 鉴定可能被噪声干扰 [Analysis] |
| MCC 算法 | 在网络中筛选 hub genes | 从模块中提取中心性最高的关键基因 | 输入：共表达网络；输出：7 个 hub genes | 摘要：maximum group centricity (MCC) algorithms | 预期影响：可能遗漏非中心但功能关键的基因 [Analysis] |
| ChEA3 转录因子预测 | 预测调控 hub genes 的转录因子 | 连接基因表达与上游调控 | 输入：hub gene 列表；输出：Batf、Irf8 | 摘要：ChEA3 predicted that Batf and Irf8 | 预期影响：失去上游调控线索，无法解释共调控机制 |
| AlphaFold3 结构预测 | 预测 TF–DNA 结合构象 | 提供计算层面的结合可能性证据 | 输入：Batf/Irf8 蛋白序列 + 靶基因启动子序列；输出：结合构象模型 | 摘要：validated using AlphaFold3 | 预期影响：失去结构层面的支持，仅剩序列 motif 预测 [Analysis] |
| EMSA 实验验证 | 湿实验确认 TF–DNA 结合 | 提供物理结合的直接证据 | 输入：核蛋白提取物 + 标记 DNA 探针；输出：结合条带 | 摘要：electrophoretic mobility shift assay | 预期影响：失去实验确认，结论停留在计算预测层面 |
| CCI 小鼠模型 | 体内验证 PANoptosis 与代谢性细胞死亡 | 将生信发现与病理生理关联 | 输入：CCI 手术小鼠；输出：细胞死亡标志物检测 | 摘要：validated in a controlled cortical impact (CCI) mouse model | 预期影响：失去体内相关性，仅剩体外/计算证据 |
| Single-cell RNA-seq + Monocle2 + 代谢通量 | 解析小胶质细胞亚群异质性与状态 | 确认 hub genes 在特定亚群中的表达与代谢状态 | 输入：single-cell 数据；输出：MG3 亚群鉴定、轨迹、代谢预测 | 摘要：Single-cell RNA-seq data revealed... MG3 | 预期影响：失去细胞类型特异性信息，无法定位到疾病相关小胶质细胞亚群 |

## 09 关键公式符号
- **不适用**。摘要中未提供任何数学公式或统计算法细节（如 WGCNA 的软阈值公式、MCC 的中心性计算式等均未给出）。仅提及算法名称，无具体符号定义。

## 10 实验设计与证据链
- **数据集/群体**：NCBI GEO 数据库中 TBI 亚急性期小鼠的 bulk RNA-seq 与 single-cell RNA-seq 数据集（具体编号、样本量未提供）。
- **指标**：hub gene 鉴定（WGCNA 模块成员度、MCC 中心性）、TF 结合（AlphaFold3 预测置信度、EMSA 条带）、细胞死亡验证（标志物表达）、小胶质细胞亚群（单细胞聚类、轨迹、代谢通量评分）。
- **基线**：未提供（无明确对照或基线算法比较）。
- **预算/骨干/仪器**：未提供。
- **oracle 输入**：不适用（非监督学习任务）。
- **评测协议**：未提供（无明确统计检验描述或多重比较校正说明）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| WGCNA + MCC 筛选 | 存在与 TBI 亚急性期相关的 hub genes | 无明确对比组 | 鉴定出 7 个 hub genes | 存在跨通路共享基因 | 无法证明这些基因是因果驱动而非伴随现象 | 摘要 |
| ChEA3 预测 | Batf 和 Irf8 调控 hub genes | 无对比 | 预测出 Batf、Irf8 | 提供候选转录因子 | 预测不等于体内真实调控 | 摘要 |
| AlphaFold3 + EMSA | Batf/Irf8 与靶基因启动子结合 | AlphaFold3 预测 vs EMSA 实验 | 两者一致（结合构象被验证） | 支持 TF–DNA 物理结合 | 未证明结合具有功能后果（如转录激活/抑制） | 摘要 |
| CCI 小鼠模型 | PANoptosis 与代谢性细胞死亡发生 | CCI vs 假手术（推测） | 细胞死亡标志物确认 | 体内病理相关性 | 未直接证明 hub genes 驱动细胞死亡 | 摘要 |
| Single-cell + 轨迹 + 代谢通量 | hub genes 在 MG3 亚群中差异表达 | 不同小胶质细胞亚群间比较 | Lgals3、Gbp2、Capg、Timp1 在 MG3 中差异表达 | 定位到疾病相关亚群 | 未证明 MG3 是唯一功能亚群 | 摘要 |

## 11 结论正确解读
- **任务范围**：本研究仅覆盖 TBI 亚急性期（具体时间窗未提供）小鼠模型，未涉及慢性期或人类样本。
- **oracle/真值输入**：hub gene 鉴定依赖算法定义（WGCNA 模块成员度 + MCC 中心性），无独立功能实验作为真值。
- **端到端状态**：非端到端——计算预测与实验验证分步进行，且实验验证仅覆盖部分环节（细胞死亡发生、TF 结合），未做 hub gene 敲除/过表达的功能实验。
- **算力成本**：未提供（AlphaFold3 运行成本未说明）。
- **历史数据依赖**：完全依赖 GEO 数据库已有数据集，无新测序数据产生。
- **模型依赖**：hub gene 筛选结果依赖 WGCNA 软阈值选择与 MCC 算法参数；TF 预测依赖 ChEA3 数据库完整性；结构预测依赖 AlphaFold3 模型精度。
- **最难情形**：未涉及——未测试 hub genes 在其他细胞类型、其他损伤模型或人类 TBI 中的普适性。
- **群体/领域边界**：结论仅适用于小鼠 TBI 亚急性期小胶质细胞，不能外推至人类或其它神经退行性疾病。
- **不确定性**：未提供统计置信区间、效应量或多重检验校正信息。
- **有边界的复述**：在小鼠 TBI 亚急性期小胶质细胞中，通过多组学整合鉴定出 7 个与 PANoptosis 和代谢性细胞死亡相关的 hub genes，其中 4 个（Lgals3、Gbp2、Capg、Timp1）在疾病相关亚群 MG3 中差异表达，且 Batf 和 Irf8 被预测并验证为共同上游转录因子；但该结论未经过功能获得/缺失实验验证，且不适用于人类。

## 12 作者自认局限
在提供的摘要材料中未发现作者明确承认的局限。作者仅在结尾表示这些发现「warrant further investigation」，暗示需要更多研究，但未具体列出局限。

**作者提及的相关约束**（非正式局限）：
- 研究基于 GEO 数据库已有数据，非前瞻性实验设计。
- 功能验证仅停留在细胞死亡发生与 TF 结合层面，未做基因操作实验。
- 结论基于小鼠模型，人类相关性未验证。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| hub gene 筛选依赖算法定义 | WGCNA 模块划分与 MCC 中心性受参数选择影响，可能产生假阳性/假阴性 | 若 hub gene 列表不稳定，后续所有分析（TF 预测、实验验证）都建立在不可靠基础上 | 进行参数敏感性分析（改变软阈值、中心性阈值），或使用独立数据集重复筛选 | 摘要仅提及算法名称，未提供参数细节 |
| AlphaFold3 预测 TF–DNA 结合构象 | AlphaFold3 对蛋白-核酸复合物的预测精度有限，尤其对多域 TF 或非标准结合模式 | 若预测构象不准确，EMSA 验证可能只是偶然匹配 | 与已知晶体结构（如 PDB 中 Batf/Irf8 复合物）对比，或使用分子动力学模拟验证构象稳定性 | 摘要未提供 AlphaFold3 预测置信度分数 |
| ChEA3 预测的转录因子缺乏功能证据 | Batf/Irf8 可能只是共表达相关，而非直接调控 hub genes | 若 TF 不直接结合并调控靶基因，则「共享调控节点」结论不成立 | 进行 ChIP-seq 或 CUT&Tag 实验确认体内结合；用 siRNA/敲除验证对 hub gene 表达的影响 | 摘要仅提到 ChEA3 预测，无功能实验 |
| 4 个 hub genes 在 MG3 中差异表达 | 差异表达可能是小胶质细胞激活的伴随现象，而非驱动细胞死亡的原因 | 若 hub genes 不驱动病理，则作为治疗靶点的价值有限 | 在 MG3 中特异性敲除 hub genes，观察细胞死亡与神经炎症是否改变 | 摘要未提供因果实验 |
| 代谢通量算法预测代谢状态 | 算法预测可能偏离实际代谢测量（如 seahorse 实验） | 代谢状态是「代谢性细胞死亡」的核心证据，预测不可靠则削弱核心 claim | 用代谢组学或代谢通量实验（如 13C 示踪）验证预测结果 | 摘要仅提到「metabolic flux algorithms were applied to predict」 |
| 未提供统计细节 | 无效应量、置信区间、多重检验校正信息 | 无法评估结果的稳健性与假阳性风险 | 补充统计方法学描述 | 摘要未提供任何统计信息 |

## 14 Agent 提炼的知识候选
**可迁移概念与方法（面向 TF–DNA 互作 × AI/物理模拟课题）**：

1. **「多组学筛选 → 上游 TF 预测 → 结构验证 → 实验确认」的闭环流程**：本文从 bulk + single-cell 数据中筛选 hub genes，再用 ChEA3 预测上游 TF，最后用 AlphaFold3 + EMSA 验证结合。此流程可直接迁移到 TF–DNA 互作研究：先用组学数据（如 ChIP-seq、ATAC-seq）筛选候选 TF 与靶位点，再用 AlphaFold3 预测结合构象，最后用 EMSA/荧光偏振实验验证。
2. **AlphaFold3 用于 TF–DNA 结合构象预测的实践案例**：本文展示了 AlphaFold3 在预测 TF 与启动子区结合方面的应用，并成功用 EMSA 验证。这为「AI 结构预测 + 湿实验验证」的 TF–DNA 互作研究提供了可复用的技术路线。
3. **跨通路共享调控节点的筛选策略**：本文通过 WGCNA + MCC 寻找不同细胞死亡通路共有的 hub genes，再找共同上游 TF。此策略可迁移到 TF–DNA 互作：寻找能同时调控多个疾病相关基因的「master TF」，而非单靶点研究。
4. **Single-cell 数据定位细胞类型特异性调控**：本文用 single-cell RNA-seq 将 hub genes 定位到特定小胶质细胞亚群（MG3）。在 TF–DNA 互作研究中，可借鉴此思路：用单细胞多组学（scATAC-seq + scRNA-seq）定位 TF 在特定细胞亚群中的结合与调控。
5. **代谢通量算法与细胞死亡表型的关联**：本文用代谢通量算法预测细胞代谢状态，与细胞死亡类型关联。在 TF–DNA 互作研究中，可迁移为：将 TF 调控的代谢基因与代谢表型关联，理解 TF 如何通过代谢重编程影响细胞命运。

## 15 与已有知识连接
- **PANoptosis 概念**：Malireddi et al. (2021) 提出 PANoptosis 作为多种细胞死亡通路的整合复合体，本文在此基础上进一步寻找跨通路共享调控节点，是对该概念的延伸。
- **TF–DNA 结合预测方法**：AlphaFold3 (Abramson et al., 2024, Nature) 已展示对蛋白-核酸复合物的预测能力，本文将其应用于 TF–启动子结合预测，与 Jumper et al. (2021) 的 AlphaFold2 蛋白结构预测形成方法学延续。
- **小胶质细胞异质性**：Keren-Shaul et al. (2017, Cell) 鉴定疾病相关小胶质细胞（DAM/MG），本文的 MG3 亚群与此概念呼应，可对比其 marker 基因（如 Lgals3 在 DAM 中高表达）。
- **WGCNA 应用**：Langfelder & Horvath (2008) 的 WGCNA 方法在神经疾病研究中广泛使用，本文是其标准应用案例。
- **可迁移领域**：本文的「多组学 + 结构预测 + 实验验证」框架可迁移至其他疾病中的 TF–DNA 互作研究，如肿瘤中 TF 调控网络、神经退行性疾病中炎症相关 TF 等。

## 16 Agent 生成的研究候选

**候选 1：基于 AlphaFold3 的 TF–DNA 结合构象预测流程标准化**
- **名称**：AF3-TFBS 流程
- **来源局限/观察**：本文用 AlphaFold3 预测 Batf/Irf8 与启动子结合，但未提供预测置信度、失败案例或与已知结构的对比，流程可重复性存疑 [Analysis]
- **核心假设**：AlphaFold3 对 TF–DNA 复合物的预测精度可通过系统化评估（与 PDB 已知结构对比）和参数调优（如 MSA 深度、采样次数）得到提升，形成标准化流程
- **相对本文的增量**：从「单案例应用」到「系统性评估与流程化」，提供可复用的预测-验证协议
- **初步方法**：收集 PDB 中所有 TF–DNA 复合物结构 → 用 AlphaFold3 重新预测 → 计算 RMSD/TM-score 评估精度 → 识别失败模式（如多域 TF、非标准结合）→ 建立推荐参数集
- **验证方式**：在独立 TF–DNA 数据集上测试流程，与 EMSA/ITC 实验数据对比
- **可能的失败模式**：AlphaFold3 对某些 TF 家族（如锌指蛋白）预测精度系统性偏低，流程无法通用
- **创新状态**：unverified

**候选 2：跨通路共享 TF 的 ChIP-seq 验证**
- **名称**：PANoptosis-TF 调控网络验证
- **来源局限/观察**：本文仅用 ChEA3 预测 TF，未做 ChIP-seq 确认体内结合，且未验证 TF 对 hub genes 的功能调控
- **核心假设**：Batf 和 Irf8 在 TBI 小胶质细胞中直接结合并调控 PANoptosis 与代谢性细胞死亡 hub genes 的启动子
- **相对本文的增量**：从「预测 + 体外结合」推进到「体内全基因组结合 + 功能验证」
- **初步方法**：在 CCI 小鼠小胶质细胞中做 Batf/Irf8 ChIP-seq → 与 RNA-seq 数据整合 → 确认结合与表达调控关系 → 用 Batf/Irf8 敲除小鼠验证 hub genes 表达与细胞死亡表型变化
- **验证方式**：ChIP-seq 峰与 RNA-seq 差异表达基因的 overlap 显著性；敲除后表型 rescue 实验
- **可能的失败模式**：Batf/Irf8 在体内结合位点与 ChEA3 预测不一致，或敲除后表型变化微弱（冗余调控）
- **创新状态**：unverified

**候选 3：TF–DNA 结合构象的分子动力学（MD）验证**
- **名称**：AF3-MD 联合验证协议
- **来源局限/观察**：AlphaFold3 预测的静态结构未经过动力学稳定性验证，结合亲和力未量化
- **核心假设**：AlphaFold3 预测的 TF–DNA 复合物构象在 MD 模拟中保持稳定，且计算结合自由能与 EMSA 实验亲和力相关
- **相对本文的增量**：从「静态结构预测」到「动态稳定性 + 能量学评估」，增强结构预测的可信度
- **初步方法**：对 Batf/Irf8–DNA 复合物做显式溶剂 MD 模拟（如 GROMACS/AMBER）→ 计算 RMSD/RMSF 评估稳定性 → 用 MM-PBSA/自由能微扰计算结合自由能 → 与 EMSA 的 Kd 值对比
- **验证方式**：MD 稳定性指标与实验亲和力的相关性；突变体（如 TF 关键残基突变）的预测与实验对比
- **可能的失败模式**：力场参数对蛋白-DNA 相互作用的描述不准确，导致结合自由能计算偏差大
- **创新状态**：unverified

**候选 4：小胶质细胞亚群特异性 TF 调控网络**
- **名称**：Microglia-TF 单细胞调控图谱
- **来源局限/观察**：本文仅用 bulk 数据做 WGCNA，单细胞数据仅用于确认亚群表达，未做单细胞水平的调控网络推断
- **核心假设**：不同小胶质细胞亚群（如 MG3 vs 稳态亚群）中，TF 调控网络存在显著差异，且疾病相关亚群中 Batf/Irf8 的调控强度更高
- **相对本文的增量**：从「亚群表达差异」到「亚群特异性调控网络」，提供更精细的细胞类型分辨率
- **初步方法**：用 SCENIC 或 CellOracle 对 single-cell RNA-seq 数据推断 TF 调控网络 → 比较 MG3 与其他亚群的 regulon 活性 → 用 ATAC-seq 数据验证结合位点可及性
- **验证方式**：SCENIC 预测的 regulon 活性与基因表达的相关性；ATAC-seq 峰在 TF motif 区域的富集
- **可能的失败模式**：单细胞数据稀疏性导致调控网络推断噪声大，亚群间差异不显著
- **创新状态**：unverified