## 01 基本信息
- **标题**：Genomic and structural insights into TATA-Binding protein from cestodes
- **作者**：Landa, Abraham; Heredia-Gomez, Elisa; Gonzalez-Kulikova, Cristina; Velazquez-Villegas, Laura A; Rodriguez-Lima, Oscar
- **单位**：未提供
- **期刊/预印本平台**：Transcription
- **年份**：2026
- **论文类型**：研究论文（综合基因组学、系统发育、结构建模与分子模拟）
- **领域**：寄生虫（绦虫）转录机制；TATA-box 结合蛋白（TBP）进化与结构
- **关键词**：TATA-binding protein; cestodes; TBP1; TBP2; homology modeling; molecular dynamics; protein–DNA docking
- **DOI/arXiv 号**：10.1080/21541264.2026.2633940
- **代码**：未提供
- **数据**：序列数据来自 WormBase ParaSite 与 GenBank；结构模型与模拟数据未公开提供（可向通讯作者索取）
- **阅读日期**：2026-05-15（按当前日期推断）
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：本文属于「TF–DNA 结合机制」中的 **TBP–TATA box 识别** 子课题，采用 **同源建模（AlphaFold2）+ 蛋白–DNA 对接（HDOCK）+ 分子动力学（MD, YASARA/AMBER14）** 的物理模拟路线，并结合系统发育与静电分析。其方法可迁移至其他 TF–DNA 体系，但未涉及深度学习训练或高通量结合预测。

## 02 一句话总结
本文通过基因组注释、多序列比对、系统发育、AlphaFold2 同源建模、静电势计算、HDOCK 蛋白–DNA 对接与 MD 模拟，揭示绦虫 TBP1 与 TBP2 两个旁系同源物均保留经典 α/β 马鞍形结构域和 TATA-box 小沟识别残基，且 TBP2 在序列与互作网络上比 TBP1 更保守，提示二者可能具有非冗余的调控功能。

## 03 研究问题
- **具体问题**：绦虫（cestodes）中 TBP1 与 TBP2 两个旁系同源物的基因组结构、进化关系、三维结构、静电性质及 TATA-box 结合模式是否保守？二者是否存在功能分化？
- **为什么重要**：TBP 是真核转录起始的核心因子，连接所有三类 RNA 聚合酶。绦虫是重要的人兽共患寄生虫，其发育转换（如中间宿主/终宿主切换、节片化）依赖精确的转录调控，但 TBP 家族在该类群中从未被系统研究。
- **现有方法为何不足**：此前仅在 *Taenia solium* 中鉴定到两个 TBP 旁系同源物（TsTBP1/TsTBP2），但缺乏跨物种的系统比较、结构验证与 DNA 结合预测；且绦虫 TBP 与已知 TBP 结构模板的序列一致性有限，需用高置信度建模与模拟补充。
- **精确的「Can ... ?」研究问题**：Can cestode TBP1 and TBP2 paralogs retain the canonical TBP fold and TATA-box recognition determinants despite sequence divergence, and do they exhibit paralog-specific structural/electrostatic features that suggest functional specialization?

## 04 背景与发展脉络
> 注：以下脉络为「仅本文框架」，未做外部系统核验。

1. **TBP 核心功能的确立（经典期）**：TBP 作为 TFIID 亚基，通过小沟插入 TATA box 并诱导 DNA 大幅弯曲，招募 TFIIA/TFIIB 等通用转录因子（GTF），启动 Pol II 转录。代表结构：酵母/人 TBP–DNA 复合物晶体结构（PDB: 1CDW, 1YTB, 1NVP）。
2. **TBP 家族扩展（旁系同源发现期）**：后生动物中 TBP 基因复制产生 TBP 相关因子（TBPL1/TRF2、TBPL2/TRF3），功能从通用转录转向发育/组织特异性调控。代表：果蝇 TRF1、脊椎动物 TBPL2。
3. **寄生虫转录机制探索（本领域空白期）**：绦虫等寄生扁虫的转录机器研究极少，仅 *T. solium* 有 TBP 基因的初步报道，无结构或互作数据。
4. **计算结构生物学介入（本方法期）**：AlphaFold2 提供高置信度单体结构；HDOCK 等对接工具预测蛋白–DNA 复合物；MD 模拟验证复合物稳定性与互作网络。本文首次将该流程系统应用于绦虫 TBP 家族。

**本文主张的位置**：填补绦虫 TBP 家族「基因组—进化—结构—互作」的系统性空白，并指出 TBP2 可能代表一种更特化/保守的 TBP 谱系。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 绦虫 TBP 家族完全未被系统研究 | 仅 *T. solium* 有 TBP1/TBP2 基因报道，无跨物种比较 | 寄生扁虫基因组资源分散、注释质量差，且非模式生物研究优先级低 | Introduction 末段；Results 首段 |
| 基因组注释错误导致序列不可靠 | 多个检索到的 TBP 序列存在错误外显子/内含子边界、错误起始/终止密码子 | 自动注释算法对低复杂度 NTD 区域和可变剪接处理不佳 | Methods「Data sources」段；Results 首段「manually inspected and corrected」 |
| 序列一致性不足以直接使用实验结构 | 绦虫 TBP 与已知晶体结构模板一致性有限，尤其 NTD 区域 | TBP 的 NTD 进化快、 intrinsically disordered，CTD 虽保守但存在旁系特异替换 | Methods「Homology modeling」段（模板选择策略） |
| 缺乏实验结构时无法验证结合模式 | 无法直接获得绦虫 TBP–DNA 共晶结构 | 寄生虫蛋白表达纯化困难，且 TBP–DNA 复合物结晶难度高 | Discussion「Future work」段（呼吁生化验证） |
| 静电性质与结合保守性未知 | 不清楚 TBP1/TBP2 是否在 DNA 结合面或 GTF 互作面存在物种/旁系特异的电荷差异 | 序列比对无法直接反映表面电荷分布，需结构映射 | Results「Electrostatic isosurface」段 |

## 06 核心思想
1. **表面方法**：对 13 个绦虫 TBP 基因（7 个 TBP1 + 6 个 TBP2）进行基因组注释、多序列比对、系统发育重建、AlphaFold2 同源建模、APBS 静电计算、HDOCK 对接与 YASARA MD 模拟，系统比较 TBP1/TBP2 的结构与互作保守性。
2. **核心洞察**：TBP1 与 TBP2 虽然整体序列一致性仅 38–47%，但 CTD 的 α/β 马鞍形折叠、TATA-box 小沟插入残基（芳香族/碱性）及 GTF 互作位点全部保留；TBP2 的互作网络比 TBP1 更均匀、更少物种间变异，提示 TBP2 可能受到更强的纯化选择，承担更特化或更基础的转录功能。
3. **可能的普适教训 [Analysis]**：在缺乏实验结构的非模式生物体系中，「序列保守性 + 结构建模 + 静电映射 + 对接/MD」的组合可以在不依赖晶体数据的情况下，对 TF–DNA 结合机制给出可检验的假设；且「旁系同源物中更保守者可能功能更特化」这一模式可能适用于其他 TF 家族。

## 07 方法总览
- **输入**：13 个绦虫 TBP 基因/蛋白序列（来自 WormBase ParaSite 与 GenBank），外加人、小鼠、酵母、果蝇 TBP/TBPL 参考序列。
- **输出**：基因组结构注释表、系统发育树、TBP1/TBP2 同源模型、静电表面图、TBP–TATA box 对接复合物模型、MD 模拟轨迹与互作网络分析。
- **模块**：
  1. 序列检索与人工校正（BLASTP/TBLASTN + 手动检查外显子边界）
  2. 多序列比对与二级结构预测（ClustalW + JPred4）
  3. 系统发育重建（MEGA X, 最大似然法）
  4. 同源建模（AlphaFold2；模板 PDB: 1CDW, 1YTB, 1NVP）
  5. 静电势计算（APBS via PDB2PQR, ±5 kT/e）
  6. 蛋白–DNA 对接（HDOCK, 配体为 AdML TATA box: TATAAAAG）
  7. MD 模拟（YASARA, AMBER14 力场, 周期性边界条件）
  8. 互作分析（DNAproDB 可视化）
- **训练**：无监督训练（AlphaFold2 为预训练模型，未微调）。
- **反馈回路**：MD 模拟结果反馈至对接 pose 筛选（选择最稳定复合物）。
- **假设**：① 绦虫 TBP 采用与已知真核 TBP 相同的折叠；② AdML TATA box 可作为通用代表序列；③ 同源建模精度足以支撑静电与互作分析。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 基因组注释与人工校正 | 获得准确的 TBP 基因结构（外显子/内含子、编码产物） | 自动注释错误会直接导致下游序列与结构分析失真 | 输入：BLAST 命中序列；输出：校正后的基因模型与蛋白序列 | Results 首段「manually inspected and corrected」；Table 1 | 预期影响：错误序列会导致系统发育树拓扑错误与结构模型失真 [预期效应] |
| 多序列比对 + 二级结构预测 | 定位保守残基与结构单元 | 识别 DNA 结合与 GTF 互作的关键位点 | 输入：13 条绦虫 + 参考序列；输出：比对 + JPred4 二级结构 | Figure 1(A) 功能残基标注 | 预期影响：无法区分保守功能位点与中性变异 [预期效应] |
| 系统发育重建 | 确定 TBP1/TBP2 的进化关系与旁系同源归属 | 判断 TBP2 是否独立于经典 TBP 谱系 | 输入：比对后的序列；输出：ML 树 | Figure 2（TBP2 单系群，与 TBPL2 聚类） | 预期影响：无法确认 TBP2 的旁系同源身份 [预期效应] |
| AlphaFold2 同源建模 | 生成 TBP1/TBP2 CTD 三维结构 | 无实验结构，需结构支撑静电与对接分析 | 输入：序列；输出：高置信度 PDB 模型 | Methods「Homology modeling」；Figure 3 | 预期影响：无结构则静电与对接分析无法进行 [预期效应] |
| APBS 静电势计算 | 映射表面电荷分布 | 评估 DNA 结合面与 GTF 互作面的电荷互补性 | 输入：PDB 模型；输出：±5 kT/e 静电表面 | Figure 4, 5 | 预期影响：无法解释物种/旁系特异的结合亲和力差异 [预期效应] |
| HDOCK 蛋白–DNA 对接 | 预测 TBP–TATA box 复合物构象 | 验证保守残基是否形成实际 DNA 接触 | 输入：TBP 模型 + AdML TATA 双链；输出：top-ranked 复合物 | Methods「Docking」；Figure 6, 7 | 预期影响：无法确认结合模式 [预期效应] |
| MD 模拟（YASARA/AMBER14） | 验证复合物稳定性与互作网络 | 静态对接无法反映动态稳定性 | 输入：对接复合物；输出：轨迹、RMSD、互作网络 | Methods「MD」；Results「interaction networks」 | 预期影响：无法区分稳定复合物与瞬时碰撞 [预期效应] |

## 09 关键公式符号
不适用。本文未使用定量公式或评分函数；核心分析为序列一致性（百分比）、系统发育分支长度（如 TBP2 分支 ≈0.38，种内 <0.012）、RMSD（结构叠加）与静电势（±5 kT/e），均为描述性指标而非公式化模型。

## 10 实验设计与证据链
- **数据集**：13 个绦虫 TBP 基因（7 个 TBP1：*T. solium*, *T. saginata*, *T. asiatica*, *E. granulosus*, *E. multilocularis*, *H. taeniformis*, *H. diminuta*, *H. nana* 等；6 个 TBP2：*T. solium*, *T. saginata*, *T. asiatica*, *T. multiceps*, *E. granulosus*, *E. multilocularis*, *H. diminuta*）。参考序列：人、小鼠、酵母 TBP，人/小鼠 TBPL2，果蝇 TRF。
- **规模**：13 个基因；结构模型约 13 个（TBP1/TBP2 各物种）；对接复合物约 13 个；MD 模拟未说明总时长（未提供）。
- **指标**：序列一致性（%）、系统发育分支长度、结构 RMSD、静电势分布、对接得分（HDOCK 输出）、MD 互作网络（残基–碱基接触）。
- **基线**：人/小鼠/酵母 TBP 与 TATA box 的已知结合模式（文献与 PDB 结构）。
- **预算/资源**：未提供（计算资源未说明）。
- **骨干/仪器**：AlphaFold2（服务器版）、HDOCK web server、YASARA Structure、APBS/PDB2PQR、MEGA X、ClustalW、JPred4、PyMOL、ChimeraX、DNAproDB。
- **Oracle 输入**：AdML 启动子 TATA box 序列（TATAAAAG）作为唯一 DNA 配体；无变异体或突变体测试。
- **评测协议**：无定量基准；通过结构叠加 RMSD、静电图对比与互作残基保守性进行定性评估。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|--------------------|------|
| 基因组注释与基因结构比较 | TBP1/TBP2 基因结构在绦虫中保守 | 13 个基因跨 6 属比较 | 外显子数、内含子位置高度保守；TBP2 基因更短（648 bp CDS） | 基因结构受强约束 | 无法推断功能差异 | Table 1 |
| 多序列比对 + 功能残基标注 | 关键 DNA/GTF 结合残基保留 | 绦虫 vs 人/小鼠/酵母 TBP | 芳香族残基（如插入小沟的 Phe）、TFIIA/TFIIB 结合位点全部保留 | TATA 识别机制保守 | 无法证明这些残基在绦虫中实际发挥相同功能 | Figure 1(A) |
| 系统发育重建 | TBP1 与 TBP2 为独立旁系同源群 | 含 TBPL1/TBPL2/TRF 外群 | TBP2 与 TBPL2 聚类，TBP1 与经典 TBP 聚类；TBP2 分支长度更短 | TBP2 更接近 TBPL2 谱系 | 无法确定 TBP2 是否具有 TBPL2 的发育特异功能 | Figure 2 |
| AlphaFold2 建模 + 结构叠加 | 绦虫 TBP 保留 α/β 马鞍形折叠 | 与 PDB 模板（1CDW 等）比对 | RMSD 窄范围，核心 β-sheet 与 α-helix 对齐 | 结构保守 | 无法评估 loop 区动态行为 | Figure 3 |
| 静电势映射 | DNA 结合面电荷特征保守 | 绦虫 TBP1/TBP2 vs 人/鼠 TBP | 凹面负电、凸面正电的全局模式一致；边缘区域有物种差异 | 静电互补机制保守 | 无法量化结合亲和力差异 | Figure 4, 5 |
| HDOCK 对接 + MD 模拟 | TBP1/TBP2 均以经典方式结合 TATA box | 所有模型对接同一 AdML TATA 序列 | 所有复合物均形成小沟插入，互作残基一致；TBP2 互作网络更均匀 | 结合模式保守；TBP2 更特化 | 无法证明体内真实结合；无突变验证 | Figure 6, 7 |

## 11 结论正确解读
- **任务范围**：本文仅覆盖 **序列与结构预测层面** 的保守性分析，未包含任何湿实验（EMSA、ChIP、报告基因、敲低等）验证。
- **Oracle/真值输入**：DNA 配体固定为 AdML TATA box（TATAAAAG），未测试其他启动子序列；结构模型基于 AlphaFold2 预测，非实验解析结构。
- **端到端状态**：非端到端。从基因组序列到结构模型的流程中，每个环节（注释、建模、对接、MD）均为独立步骤，误差会累积。
- **算力成本**：未报告 MD 模拟时长、体系大小或计算资源，无法评估可重复性。
- **历史数据依赖**：依赖 WormBase ParaSite 与 GenBank 的基因组注释质量；作者手动修正了部分错误，但未说明修正规则。
- **模型依赖**：AlphaFold2 对 TBP 这类高度保守蛋白预测置信度高，但对 NTD 无序区域不可靠；HDOCK 对蛋白–DNA 复合物的精度有限，MD 仅验证稳定性而非结合自由能。
- **最难情形**：TBP1 的 NTD 区域和 loop 区变异最大，但本文未对这些区域做功能预测；TBP2 在 *H. diminuta* 中的分支位置较远，但未深入讨论。
- **群体/领域边界**：结论仅适用于绦虫（Cestoda）类群，外推至其他扁虫（如吸虫、涡虫）需谨慎。
- **不确定性**：作者未提供置信区间、统计检验或交叉验证；所有结论为定性描述。
- **有边界的复述**：在绦虫已测序基因组中，TBP1 与 TBP2 的基因结构、核心折叠、TATA 识别残基和静电模式均保守；TBP2 在序列与互作网络上比 TBP1 更均匀，提示其可能受更强纯化选择，但本文未证明其功能差异。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 缺乏功能实验验证 | 所有结论基于序列与结构预测，无体内/体外功能数据 | 呼吁进行启动子占用研究、发育阶段表达谱、组织定位、与 GTF 亲和力的生化测定 | Discussion「Future work」段 |
| 未检测 TBP2 的发育特异性功能 | 虽提示 TBP2 可能特化，但未验证其在卵子发生或胚胎早期的作用 | 建议在绦虫中开展 TBP2 特异性敲低或过表达研究 | Discussion 末段 |
| 结构模型为预测而非实验解析 | AlphaFold2 模型未经过晶体或冷冻电镜验证 | 未明确提及，但暗示需要实验结构 | Methods「Homology modeling」段 |
| 仅使用单一 DNA 序列（AdML TATA） | 未测试 TBP1/TBP2 对不同 TATA 变体的偏好 | 未明确提及，但讨论中提及启动子选择性 | Methods「Docking」段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| TBP2 与 TBPL2 聚类，但未讨论 TBPL2 的已知功能 | TBPL2 在脊椎动物中为卵母细胞/胚胎特异，绦虫 TBP2 可能只是「丢失了 NTD 的 TBP」而非功能特化 | 系统发育聚类 ≠ 功能同源，需谨慎解读 | 比较绦虫 TBP2 与脊椎动物 TBPL2 的启动子偏好或蛋白互作网络 | Figure 2；Discussion 中「TBP2 更保守」的论述 |
| 静电差异仅定性描述，未量化 | 「负电增强」等描述无数值支撑，无法判断是否显著 | 静电差异可能是噪声而非功能信号 | 计算表面静电势的定量指标（如 zeta 电位或残基电荷密度）并做统计检验 | Figure 4, 5 无数值标注 |
| HDOCK 对接未报告 docking score 或 pose 聚类 | 无法判断 top pose 是否唯一或可靠 | 对接结果可能依赖初始 pose 选择 | 报告 HDOCK 置信度分数、多种 pose 聚类结果 | Methods「Docking」段未提供分数 |
| MD 模拟细节缺失 | 未报告模拟时长、温度、盐浓度、水模型、力场版本 | MD 结论（「稳定互作网络」）无法复现 | 补充 MD 参数与收敛性分析（RMSD 平台期） | Methods「MD」段仅一句描述 |
| 未测试 TATA 变体或非 TATA 启动子 | 绦虫可能大量使用非 TATA 启动子，TBP 在这些启动子上的行为未知 | 若 TBP2 偏好非 TATA 启动子，则「保守结合」结论需修正 | 对多种启动子序列做对接/MD 或体外结合实验 | 全文仅使用 AdML TATA |
| 人工注释修正缺乏规则说明 | 手动修正可能引入主观偏差 | 影响所有下游分析的输入质量 | 提供修正前后对比与判定标准 | Results 首段「manually inspected」无细节 |

## 14 学到什么
> 标题：Agent 提炼的知识候选

1. **「旁系同源物保守性梯度」可作为功能特化预测器**：TBP2 比 TBP1 更保守（序列、互作网络），提示更保守的旁系同源物可能承担更基础或更特化的功能。可迁移至其他 TF 家族（如 bZIP、Homeodomain）的旁系同源分析。
2. **「序列保守 + 结构建模 + 静电映射 + 对接/MD」四步流水线**：在无实验结构的非模式生物中，该流程可系统评估 TF–DNA 结合保守性。迁移至课题：对任意 TF 家族，先做多序列比对定位 DNA 结合域，再 AlphaFold2 建模，APBS 看电荷互补，HDOCK+MD 验证结合模式。
3. **静电势的「全局保守、局部变异」模式**：绦虫 TBP 的凹面负电（DNA 结合）全局保守，但边缘区域有物种差异。迁移至课题：分析 TF 家族时，应区分「核心结合面」与「外围调节面」的进化约束差异。
4. **AdML TATA box 作为通用 DNA 配体的局限性**：单一配体无法揭示 TF 的启动子选择性。迁移至课题：设计对接/MD 实验时，应使用多种 DNA 序列（含突变体）以区分保守结合与序列特异结合。
5. **系统发育聚类 ≠ 功能同源**：TBP2 与 TBPL2 聚类，但功能可能不同。迁移至课题：在解释 TF 旁系同源物的系统发育位置时，需结合表达谱或互作数据，避免过度推断。
6. **NTD 无序区域是功能分化的热点**：绦虫 TBP1/TBP2 的差异集中在 NTD 和 loop 区，而非 DNA 结合域。迁移至课题：研究 TF 家族时，关注 NTD 的长度/序列变异可能比关注 DNA 结合域更能解释功能分化。

## 15 与已有知识连接
- **TBP 结构与功能经典文献**：本文引用的 PDB 模板（1CDW, 1YTB, 1NVP）对应酵母/人 TBP–DNA 复合物，与 Kim et al. (1993) *Nature*、Nikolov et al. (1995) *Nature* 等经典结构一致。可连接至 TFIIA/TFIIB 互作界面的已知残基。
- **TBP 旁系同源物研究**：脊椎动物 TBPL2/TRF3 的功能（卵母细胞特异转录）见 Gazdag et al. (2009) *PNAS*；果蝇 TRF1 见 Hansen et al. (1997) *EMBO J*。本文的 TBP2 聚类结果与此类研究一致，但未深入功能比较。
- **AlphaFold2 在 TF 结构预测中的应用**：与 Jumper et al. (2021) *Nature* 的 AF2 方法一致；本文未使用 AF2 的 PAE 或 pLDDT 做置信度过滤，可对比其他 TF 结构预测研究（如 Akdel et al. 2022）。
- **蛋白–DNA 对接与 MD 方法**：HDOCK（Yan et al. 2020 *Nature Protocols*）与 YASARA/AMBER14（Krieger et al. 2014）为常用工具；本文未报告 docking score 或 MD 收敛性，可对比更严格的流程（如 HADDOCK 或 Rosetta DNA）。
- **绦虫转录机制**：本文是首个系统研究绦虫 TBP 家族的工作，可连接至 *Taenia solium* 基因组计划（Tsai et al. 2013 *Nature Genetics*）及扁虫转录因子数据库（如 SchistoTFdb）。
- **[Analysis] 候选方向**：本文的「TBP2 更保守」结论与脊椎动物 TBPL2 的发育特异功能形成有趣对比——若绦虫 TBP2 也参与生殖发育，则可能成为抗寄生虫药物靶点；但需功能实验验证。

## 16 研究想法
> 标题：Agent 生成的研究候选

1. **候选名称**：绦虫 TBP2 启动子选择性预测（TBP2 promoter selectivity prediction）
   - **来源局限/观察**：本文仅用 AdML TATA box 做对接，未测试 TBP2 是否偏好非 TATA 或 TATA 变体启动子。
   - **核心假设**：TBP2 与 TBP1 对 TATA 变体（如 TATATAAA vs TATAAAAG）或非 TATA 元件（如 INR/DPE）有不同亲和力。
   - **增量**：将单一配体扩展为启动子序列库，结合深度学习（如 CNN 或 Transformer 编码 DNA 序列）预测结合偏好。
   - **初步方法**：用本文的 TBP1/TBP2 模型对 1000 条随机启动子序列做 HDOCK 对接 + 短 MD，提取结合能特征；训练分类器区分 TBP1/TBP2 偏好序列；用 MEME 或 Tomtom 做 motif 富集。
   - **验证方式**：EMSA 或荧光各向异性实验验证 top 预测序列；或与 RNA-seq 启动子占用数据交叉验证。
   - **创新状态**：unverified

2. **候选名称**：TF 旁系同源物保守性-功能特化通用框架（Paralog conservation-function specialization framework）
   - **来源局限/观察**：本文发现 TBP2 更保守且互作网络更均匀，但未量化「保守性」与「功能特化」的关系。
   - **核心假设**：在任意 TF 家族中，旁系同源物的序列保守性（dN/dS 或 Shannon entropy）与互作网络均匀性呈正相关，且可预测功能冗余度。
   - **增量**：将本文的定性观察转化为可计算的框架，适用于其他 TF 家族（如 bHLH、Nuclear receptor）。
   - **初步方法**：收集 10 个 TF 家族的旁系同源物序列与结构，计算保守性指标；用蛋白–蛋白互作数据库（BioGRID/STRING）量化互作网络均匀性；回归分析二者相关性。
   - **验证方式**：对预测为「高特化」的旁系同源物，检索已有敲除表型数据（如 Mouse Genome Informatics）验证。
   - **创新状态**：unverified

3. **候选名称**：静电势差异驱动的 TF–DNA 结合亲和力预测（Electrostatic-difference-driven TF-DNA affinity prediction）
   - **来源局限/观察**：本文静电分析仅定性描述，未量化电荷差异对结合的影响。
   - **核心假设**：TF 表面静电势的局部差异（尤其是 DNA 结合面边缘）可预测对不同 DNA 序列的相对亲和力。
   - **增量**：将 APBS 静电势图转化为数值特征（如残基电荷密度、表面电势梯度），与实验结合数据关联。
   - **初步方法**：对本文 13 个 TBP 模型计算残基级静电势；用 PB 方程或 Poisson-Boltzmann 计算与不同 DNA 序列的结合自由能；与 HDOCK 分数或实验数据（如 SELEX）对比。
   - **验证方式**：用已知突变体（如 TBP 的 K→A 突变）验证预测的亲和力变化。
   - **创新状态**：unverified

4. **候选名称**：绦虫 TBP2 作为抗寄生虫药物靶点的结构评估（Structural assessment of cestode TBP2 as drug target）
   - **来源局限/观察**：本文未讨论 TBP2 作为药物靶点的可能性，但 TBP2 与宿主 TBP 的差异可能提供选择性空间。
   - **核心假设**：绦虫 TBP2 的 NTD 或 loop 区存在宿主 TBP 不具有的药物结合口袋。
   - **增量**：从结构生物学角度评估 TBP2 的可成药性，为抗绦虫药物设计提供起点。
   - **初步方法**：用 Fpocket 或 DoGSiteScorer 检测 TBP2 模型表面的潜在口袋；与宿主 TBP 结构比对，筛选差异口袋；对小分子库做虚拟筛选。
   - **验证方式**：分子对接 + MD 验证候选分子的结合稳定性；后续细胞实验验证。
   - **创新状态**：unverified

5. **候选名称**：TBP 家族进化的「NTD 长度-功能分化」假说检验（NTD length-function divergence hypothesis in TBP family）
   - **来源局限/观察**：本文发现 TBP1/TBP2 差异集中在 NTD，但未分析 NTD 长度与功能的关系。
   - **核心假设**：TBP 旁系同源物的 NTD 长度与无序程度与其功能特化程度（如组织特异性）正相关。
   - **增量**：将 NTD 的序列特征与功能数据关联，可能揭示 TF 家族进化的普遍规律。
   - **初步方法**：收集 50 个物种的 TBP/TBPL 序列，用 IUPred 或 AlphaFold2 pLDDT 预测 NTD 无序性；与已知表达谱（如 Bgee 数据库）关联。
   - **验证方式**：对预测为「高无序 NTD」的 TBP2，检索其是否在生殖组织中高表达。
   - **创新状态**：unverified