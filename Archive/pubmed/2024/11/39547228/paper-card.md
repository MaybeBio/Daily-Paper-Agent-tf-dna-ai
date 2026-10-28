## 01 基本信息
- **标题**：STK19 positions TFIIH for cell-free transcription-coupled DNA repair
- **作者**：Mevissen, Tycho E T; Kummecke, Maximilian; Schmid, Ernst W; Farnung, Lucas; Walter, Johannes C
- **单位**：哈佛医学院（Harvard Medical School）等（基于通讯作者邮箱推断，具体单位列表未提供）
- **期刊/平台**：Cell
- **年份**：2024-11-16（在线发表）
- **论文类型**：研究论文（Research Article）
- **领域**：DNA 修复；转录偶联修复（TC-NER）；结构生物学；生物化学
- **关键词**：TC-NER；STK19；TFIIH；RNA聚合酶II；cryo-EM；AlphaFold
- **DOI/arXiv 号**：10.1016/j.cell.2024.10.020
- **代码**：未提供
- **数据**：cryo-EM 结构数据（PDB 未提供具体编号）；质谱数据（未提供）
- **阅读日期**：2025-01-30（假设）
- **在课题方向中的位置**：本文聚焦转录偶联修复（TC-NER）中 TFIIH 的招募与定位机制，核心对象是 RNA 聚合酶 II（Pol II）停滞后的修复复合物组装。虽非直接研究 TF–DNA 结合特异性，但揭示了 STK19 作为衔接蛋白将 TFIIH 的 XPD 亚基定位至 Pol II 下游 DNA 的机制，为理解 TF–DNA 互作中"辅助因子如何引导修复/解旋酶至特定 DNA 位点"提供了结构基础与可迁移的 AI 辅助工作流（AlphaFold-Multiver 筛选 + cryo-EM 验证）。

## 02 一句话总结
本文通过建立非洲爪蟾卵提取物无细胞转录偶联修复（TC-NER）体系，证明 STK19 是 TC-NER 的核心因子，并利用 1.9 Å cryo-EM 结构与 AlphaFold 预测揭示 STK19 通过结合 CSA/DDB1 和 Pol II 的 RPB1 亚基，将 TFIIH 的 XPD 解旋酶定位至停滞 Pol II 下游 DNA 以进行损伤验证。

## 03 研究问题
- **具体问题**：TC-NER 中，停滞的 RNA 聚合酶 II（Pol II）如何将 TFIIH 招募并正确定位到损伤位点以启动修复？STK19 在这一过程中扮演什么角色？
- **为什么重要**：TC-NER 是清除转录链上 DNA 损伤的关键途径，其缺陷导致 Cockayne 综合征等严重疾病。尽管 CSB、CRL4CSA、UVSA、ELOF1 已被鉴定为关键因子，但 TFIIH 如何被精确"摆放"到 Pol II 前方以进行损伤验证的机制长期不明。
- **现有方法不足**：此前缺乏能够区分 GG-NER 与 TC-NER 的无细胞体系；结构研究仅解析了 Pol II 停滞复合物与 CSB/CRL4CSA 的结合，未包含 TFIIH 的完整组装。
- **精确研究问题**：Can STK19, through its interactions with CSA/DDB1 and Pol II RPB1, position TFIIH's XPD subunit onto the downstream DNA ahead of stalled Pol II to enable lesion verification in TC-NER?

## 04 背景与发展脉络
- **阶段一：TC-NER 因子鉴定（~2000-2015）**：CSB、CSA、UVSSA、ELOF1 相继被鉴定为 TC-NER 核心因子。CSB 结合停滞 Pol II，CRL4CSA 泛素化 Pol II，UVSSA 稳定复合物并招募 TFIIH。局限：缺乏无细胞体系，机制研究依赖体内遗传学。
- **阶段二：结构解析停滞 Pol II 复合物（~2018-2023）**：cryo-EM 解析了 Pol II-CSB、Pol II-CSB-CRL4CSA 等复合物结构（如 8B3D），但 TFIIH 如何被招募并定位仍未解决。局限：TFIIH 高度动态，难以稳定捕获。
- **阶段三：AI 辅助结构预测与无细胞体系（本文，2024）**：利用 AlphaFold-Multimer 大规模筛选 STK19 的互作伙伴，结合无细胞 TC-NER 体系与高分辨率 cryo-EM，首次完整解析含 STK19 的 TC-NER 复合物，提出 STK19 作为"定位器"将 TFIIH 引导至 Pol II 下游。
- **本文主张的位置**：在 TC-NER 机制研究中，填补了"TFIIH 如何被正确定位"的关键空白；在方法上，展示了 AI 结构预测与实验结构生物学、无细胞生化体系的高效协同。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 缺乏无细胞 TC-NER 体系 | 无法在体外区分 TC-NER 与 GG-NER，机制研究受限 | 卵提取物中 TC-NER 因子（CSB、CSA 等）含量低或缺失 | Results 图 1C：未添加 cocktail 时仅 GG-NER；图 S2A：western blot 显示 CSB/CSA 在卵中低表达 |
| TFIIH 招募机制不明 | 已知 UVSSA 招募 TFIIH，但 TFIIH 如何正确定位至损伤位点未知 | TFIIH 与 UVSSA 的 TIR 区域结合为柔性连接，缺乏刚性锚定 | Introduction 末段；Discussion 图 7C-D 模型 |
| STK19 功能不清 | STK19 曾被注释为激酶，但无激酶活性，功能未知 | 纯化的 STK19 无激酶活性，结构上缺乏激酶折叠 | Introduction；Results 图 4A-B 结构分析 |
| 结构解析困难 | TC-NER 复合物高度动态，难以获得高分辨率结构 | 复合物包含多个柔性模块（TFIIH、UVSSA 等） | Results 图 S4-S6：需大量分类与局部 refinement |
| 互作预测噪音 | AlphaFold 预测存在假阳性 | 需要实验验证 | Results 图 3A：SPOC 评分筛选；图 4-5 突变验证 |

## 06 核心思想
1. **表面方法**：建立无细胞 TC-NER 体系（卵提取物 + 重组 TC-NER 因子 cocktail），结合 AlphaFold-Multimer 大规模互作筛选、1.9 Å cryo-EM 结构解析、定点突变与功能回补实验。
2. **核心洞察**：STK19 并非激酶，而是一个"分子定位器"——它通过三个界面同时结合 CSA/DDB1（CRL4CSA 的底物受体模块）和 Pol II 的 RPB1 亚基，从而将整个 CRL4CSA-STK19 复合物锚定在停滞 Pol II 上。随后，STK19 的 WH3 结构域为 TFIIH 的 XPD 亚基提供对接位点，将 XPD 引导至 Pol II 下游 DNA 双链处，使其能够以 5'→3' 方向追踪并验证损伤。UVSSA 的 VHS 结构域在 STK19 结合后发生位移，为 XPD 让出空间。
3. **可能的普适教训 [Analysis]**：① 无激酶活性的"伪激酶"蛋白可能通过支架/定位功能参与 DNA 修复；② AlphaFold 大规模互作筛选 + 高分辨率结构验证是解析动态复合物组装的高效策略；③ 柔性连接（UVSSA TIR）与刚性锚定（STK19 三界面结合）的组合可能是许多 DNA 修复复合物实现"精确摆放"的通用设计原则。

## 07 方法总览
- **输入**：含位点特异性顺铂损伤的质粒 DNA（转录模板链）、非洲爪蟾卵提取物（NPE）、重组 TC-NER 因子（CSB、CRL4CSA、UVSSA、ELOF1、STK19 及其突变体）。
- **输出**：无细胞 TC-NER 活性（PmlI 位点再生检测）、TC-NER 复合物 cryo-EM 结构（1.9 Å）、STK19 互作网络预测。
- **模块**：
  1. 无细胞转录系统（NPE + GAL4-VP64 + TBP + 损伤质粒）
  2. TC-NER 活性检测（限制酶消化 + 凝胶电泳）
  3. AlphaFold-Multimer 互作筛选（STK19 vs 409 个蛋白）
  4. SPOC 分类器评分
  5. cryo-EM 结构解析（含局部 refinement）
  6. 定点突变与功能回补
  7. 体外泛素化实验
  8. 生物层干涉（BLI）DNA 结合实验
- **训练**：无监督训练（AlphaFold-Multimer 为预训练模型；SPOC 为已训练分类器）。
- **反馈回路**：AlphaFold 预测 → 突变设计 → 功能实验验证 → 结构确认 → 修正模型。
- **假设**：① 卵提取物中内源 TC-NER 因子不足可通过重组蛋白补充；② AlphaFold 预测的互作界面具有生物学相关性；③ 无细胞体系中的 TC-NER 反映体内机制。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 无细胞转录系统 | 在卵提取物中实现可诱导转录 | 为 TC-NER 提供停滞 Pol II 底物 | 输入：损伤质粒 + 转录因子；输出：RNA 转录本 | Results 图 1B | 无转录则无 TC-NER（预期） |
| TC-NER 活性检测 | 定量损伤修复效率 | 评估各因子功能 | 输入：修复后质粒；输出：PmlI 位点再生比例 | Results 图 1C-1F | 无法评估修复活性 |
| AlphaFold-Multimer 筛选 | 预测 STK19 互作伙伴 | 缩小候选互作蛋白范围 | 输入：STK19 序列 + 409 个蛋白；输出：互作评分 | Results 图 3A | 无法系统发现 STK19 互作网络 |
| SPOC 分类器 | 区分功能性互作与假阳性 | AlphaFold 预测存在噪音 | 输入：AF-M 结构；输出：0-1 评分 | Results 图 3A | 可能保留更多假阳性 |
| cryo-EM 结构解析 | 确定 TC-NER 复合物原子结构 | 揭示 STK19 结合模式与构象变化 | 输入：体外组装复合物；输出：1.9 Å 密度图 | Results 图 3D-3H | 无法获得结构信息 |
| 定点突变 | 破坏特定互作界面 | 验证功能重要性 | 输入：STK19/CSA/UVSSA 突变体；输出：TC-NER 活性变化 | Results 图 4G, 5E | 无法建立因果关系 |
| 体外泛素化 | 检测 CRL4CSA 活性 | 确认复合物功能完整性 | 输入：CRL4CSA + 底物；输出：泛素化产物 | Results 图 6C | 无法评估 E3 连接酶功能 |
| BLI DNA 结合 | 检测 STK19-DNA 互作 | 验证 STK19 的 DNA 结合能力 | 输入：STK19 + DNA；输出：结合曲线 | Results 图 5G | 无法评估 DNA 结合贡献 |

## 09 关键公式符号
不适用。本文为实验生物学研究，无核心数学公式。定量分析仅涉及简单的百分比计算（修复效率 = 修复产物/总 DNA）和标准偏差统计，未使用复杂数学模型。

## 10 实验设计与证据链
- **数据集/群体**：非洲爪蟾卵提取物（NPE）；重组蛋白（人源 CSB、爪蟾 CSA/DDB1/UVSSA/STK19/ELOF1）；含顺铂损伤的质粒。
- **规模**：cryo-EM 数据集 15,521 张显微照片，484,012 颗粒（最终 1.9 Å 结构）；AlphaFold 筛选 409 个蛋白。
- **指标**：TC-NER 效率（PmlI 位点再生 %）、cryo-EM 分辨率、SPOC 评分、泛素化水平。
- **基线**：无 cocktail 的 NPE（仅 GG-NER）；含全部因子的 cocktail（最大 TC-NER）。
- **预算**：未提供。
- **骨干/仪器**：Titan Krios（300 keV，Falcon 4 探测器，Selectris 能量过滤器）；Octet RED384（BLI）。
- **oracle 输入**：无（非 AI 训练任务）。
- **评测协议**：每个条件 ≥3 次独立实验；TC-NER 活性在 120 分钟时间点量化；突变体与野生型平行比较。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| 无细胞转录 | NPE 支持可诱导转录 | 有/无 GAL4-VP64 + TBP | 转录依赖激活因子 | 系统可用于 TC-NER 研究 | 未证明转录效率与体内一致 | Results 图 1B |
| TC-NER 活性 | cocktail 支持 TC-NER | 有/无 cocktail；有/无 α-amanitin | cocktail 依赖、转录依赖的修复 | 无细胞 TC-NER 重建成功 | 未证明修复完全模拟体内 | Results 图 1C-1F |
| 因子剔除 | 各因子必要性 | 逐一省略 5 个因子 | 每个因子缺失均降低修复 | 5 个因子均为 TC-NER 所需 | 未区分各因子贡献大小 | Results 图 2A |
| 抗体耗竭 | STK19 必要性 | 抗 STK19 耗竭 vs 对照 | 耗竭后修复下降 | STK19 为 TC-NER 核心因子 | 未排除间接效应 | Results 图 2B |
| AlphaFold 筛选 | STK19 互作伙伴 | 409 个蛋白 | CSA、XPD、RPB1 为 top hits | STK19 可能结合这些蛋白 | 预测需实验验证 | Results 图 3A |
| cryo-EM 结构 | STK19 结合模式 | 1.9 Å 结构 | STK19 结合 CSA/DDB1 和 RPB1 | STK19 是复合物结构组分 | 未包含 TFIIH 全酶 | Results 图 3D-3H |
| STK19 突变 | 互作界面功能 | STK19ΔN, 4A, RY-GG, D-R, AS-EY 等 | 界面突变降低修复 | STK19-CSA/DDB1 和 STK19-XPD 互作重要 | 突变可能影响蛋白折叠 | Results 图 4G, 5E |
| UVSSA 突变 | UVSSA-STK19 互作 | UVSSAE10A | 不影响修复 | STK19-UVSSA 直接互作非必需 | 可能存在冗余机制 | Results 图 4F |
| 泛素化实验 | CRL4CSA 活性 | 野生型 vs 突变 STK19 | 突变不影响泛素化 | STK19 不参与泛素化 | 未检测所有底物 | Results 图 6C |
| BLI | STK19-DNA 结合 | 野生型 vs RR-AA | 突变降低 DNA 结合 | STK19 直接结合 DNA | 未证明 DNA 结合是修复所必需 | Results 图 5G-5H |

## 11 结论正确解读
- **任务范围**：本文仅研究 TC-NER 的早期步骤——停滞 Pol II 上 TC-NER 复合物的组装与 TFIIH 定位。未涉及 GG-NER、NER 的后续切除/合成步骤，也未研究转录重启。
- **oracle/真值输入**：无 AI 训练任务；AlphaFold 预测作为假设生成工具，经实验验证。
- **端到端状态**：无细胞体系实现了从损伤识别到修复的完整过程，但效率仅 ~32%，且未在体内（细胞或动物）验证 STK19 的定位模型。
- **算力成本**：未提供。
- **历史数据依赖**：依赖已发表的 Pol II 转录复合物结构（8B3D）和 AlphaFold 预训练模型。
- **模型依赖**：结论依赖 AlphaFold-Multimer 预测的准确性；作者通过突变实验部分验证，但未直接证明 STK19-XPD 互作（未获得含 TFIIH 的复合物结构）。
- **最难情形**：STK19-XPD 互作仅由 AlphaFold 预测支持，缺乏直接生化证据（如 pull-down 或交联质谱）；作者承认无法在体外观察到 STK19 与 XPD 的直接结合。
- **群体/领域边界**：结论基于爪蟾卵提取物体系，可能不完全反映人类细胞中的 TC-NER；STK19 在人类中的功能由伴随论文（van den Heuvel et al.）支持。
- **不确定性**：STK19 是否通过构象变化"释放"UVSSA 以允许 XPD 结合，仍是推测性模型；K1268 泛素化与 TFIIH 定位的因果关系未直接证明。

**有边界的复述**：在爪蟾卵提取物无细胞体系中，STK19 通过结合 CSA/DDB1 和 Pol II RPB1 将自身锚定于停滞 Pol II，并通过其 WH3 结构域为 TFIIH 的 XPD 亚基提供对接位点，从而将 XPD 引导至 Pol II 下游 DNA 进行损伤验证；该过程为 TC-NER 所必需，但 STK19-XPD 直接互作的分子细节及体内相关性仍需进一步验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 修复效率有限 | 无细胞 TC-NER 最大效率 ~32% | 优化体系条件 | Discussion "Limitations of the study" |
| STK19-XPD 互作缺乏直接证据 | 无法观察到重组 STK19 与 XPD 的直接结合 | 需含 TFIIH 的复合物结构 | Discussion "Limitations of the study" |
| 突变体折叠状态未验证 | 无法完全排除突变导致蛋白错误折叠 | 需额外结构/生化验证 | Discussion "Limitations of the study" |
| 体内相关性未验证 | 爪蟾体系可能不完全反映人类细胞 | 需人类细胞中验证 | Discussion "Limitations of the study" |
| STK19 的"粘性" | 重组 STK19 易聚集，阻碍体外互作研究 | 需优化蛋白纯化条件 | Discussion "Limitations of the study" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| STK19-XPD 互作仅由 AlphaFold 预测支持 | AlphaFold 可能预测出非生理相关的界面；STK19 可能通过间接机制（如改变 DNA 构象）促进 XPD 功能 | 核心机制 claim 缺乏直接生化证据 | 交联质谱（XL-MS）、体外 pull-down（优化条件）、NMR 滴定 | Results 图 5A-5E；Discussion 局限 |
| 突变体表型可能源于蛋白不稳定 | 作者未验证所有突变体的折叠状态（仅 SEC 洗脱体积） | 突变体功能缺失可能非特异性 | 圆二色谱（CD）、热稳定性分析（DSF）、有限蛋白酶解 | Results 图 4G, 5E；Discussion 局限 |
| 无细胞体系效率仅 32% | 可能仅捕获了部分 TC-NER 事件；未修复的底物可能代表不同机制 | 结论可能不适用于所有 TC-NER 事件 | 单分子分析、增加修复时间、优化因子浓度 | Discussion "Limitations" |
| STK19 的"粘性"可能影响功能解读 | 高浓度 STK19 可能非特异性结合 DNA 或蛋白 | 可能高估 STK19 的支架功能 | 表面等离子共振（SPR）定量亲和力、竞争实验 | Discussion "Limitations" |
| 未检测 STK19 是否影响 Pol II 转录延伸 | STK19 可能通过影响 Pol II 构象而非直接定位 TFIIH 来促进修复 | 替代机制未排除 | 体外转录延伸实验、单分子 FRET | Results 图 1B（仅检测转录启动） |
| AlphaFold 筛选仅覆盖 409 个蛋白 | 可能遗漏其他 STK19 互作伙伴 | 可能还有其他功能相关互作 | 免疫沉淀-质谱（IP-MS）全蛋白组筛选 | Results 图 3A |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **"伪激酶"支架蛋白的通用设计原则**：STK19 虽名为激酶但无催化活性，其功能是作为支架将多个蛋白（CSA/DDB1、Pol II、TFIIH）组装成超复合物。在 TF–DNA 互作研究中，应警惕注释为激酶/酶但缺乏催化活性的蛋白可能具有支架/定位功能。可迁移：在分析 TF 互作网络时，考虑"无催化活性但含多个互作界面"的蛋白作为复合物组装中心。

2. **AlphaFold-Multimer 大规模互作筛选工作流**：本文展示了将 AF-M 用于 ~400 个蛋白的二元互作筛选，结合 SPOC 分类器过滤假阳性，再以 cryo-EM 验证的策略。可迁移：在 TF–DNA 互作研究中，可用 AF-M 筛选 TF 与候选辅助因子/染色质重塑因子的互作，再用 SPOC 或类似分类器排序，最后用共纯化或交联实验验证。

3. **"柔性系绳 + 刚性锚定"的复合物定位机制**：UVSSA 通过柔性 TIR 区域系住 TFIIH，而 STK19 提供刚性锚定将 XPD 精确摆放。这种"先系住、后定位"的两步机制可能是许多 DNA 修复/转录复合物实现空间精确性的通用策略。可迁移：在模拟 TF 搜索 DNA 靶位点时，考虑辅助因子如何通过刚性互作限制 TF 的构象空间。

4. **无细胞体系重建复杂修复通路的策略**：通过质谱确定卵提取物中缺失的因子，然后以重组蛋白 cocktail 补充，成功重建 TC-NER。可迁移：在研究 TF–DNA 互作的动态过程时，可先鉴定提取物中缺失的辅助因子，再以重组蛋白补充，实现可诱导、可调控的体外系统。

5. **结构预测与实验结构的迭代验证**：AF-M 预测 → 突变设计 → 功能实验 → cryo-EM 确认的闭环流程，有效加速了机制研究。可迁移：在 TF–DNA 复合物结构未知时，可先用 AF-M 预测复合物模型，设计界面突变体，用功能实验（如 EMSA、报告基因）验证，最后用 cryo-EM 或交联质谱确认。

6. **DNA 损伤位点验证的"追踪"模型**：XPD 以 5'→3' 解旋酶活性沿 DNA 追踪损伤，STK19 确保其从正确位置（Pol II 下游）起始追踪。可迁移：在模拟 TF 在 DNA 上搜索靶位点时，考虑"起始位置"如何被上游事件（如 Pol II 停滞）决定，而非随机扩散。

## 15 与已有知识连接
- **TC-NER 经典模型**：与 Hanawalt 等早期发现（1985）及后续 Cockayne 综合征研究一致，本文确认 CSB、CSA、UVSSA、ELOF1 的核心地位，并新增 STK19 为必需因子。可连接至：Vermeulen & Fousteri (2013) TC-NER 综述。
- **CRL4 E3 连接酶机制**：CSA-DDB1-CUL4-RBX1 组装与已知 CRL4 家族（如 CRL4DDB2 在 GG-NER 中）一致。可连接至：Sugasawa et al. (2005) DDB2 研究。
- **TFIIH 在 NER 中的双重功能**：TFIIH 在 GG-NER 和 TC-NER 中均负责 DNA 解旋，本文提出 STK19 提供 TC-NER 特异的定位机制。可连接至：Compe & Egly (2016) TFIIH 综述。
- **AlphaFold 在蛋白互作预测中的应用**：与 Jumper et al. (2021) AlphaFold2 及 Evans et al. (2022) AlphaFold-Multimer 直接相关。本文展示了 AF-M 在筛选级应用（~400 个蛋白）的可行性。
- **cryo-EM 解析大型复合物**：1.9 Å 分辨率接近原子级，与近期 Pol II 转录复合物结构（如 8B3D, 8B3C）可比较。可连接至：Farnung et al. (2021) 相关工作。
- **STK19 的癌症关联**：STK19 突变在皮肤癌中高频出现，本文提供其在 DNA 修复中的功能解释。可连接至：Rodriguez-Martinez et al. (2020) STK19 癌症基因组学研究。
- **与 TF–DNA 互作课题的关联**：本文虽不直接研究 TF 与 DNA 的序列特异性识别，但揭示了"辅助因子如何将解旋酶/修复蛋白引导至特定 DNA 位置"的机制，与 TF 如何寻找靶位点的问题高度相关。可迁移概念：蛋白-蛋白互作如何限制蛋白在 DNA 上的搜索空间。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 互作中辅助因子定位机制的 AlphaFold 筛选
   - **来源局限/观察**：本文用 AF-M 筛选 STK19 互作伙伴，但仅覆盖 409 个蛋白；TF–DNA 互作研究中，辅助因子如何引导 TF 至特定基因组位点的问题同样适用。
   - **核心假设**：许多 TF 的基因组靶向依赖于辅助因子提供的"空间锚定"，这些互作可通过 AF-M 预测。
   - **初步方法**：选取 50-100 个已知 TF，用 AF-M 预测其与染色质重塑因子、组蛋白修饰酶、Mediator 亚基的互作，SPOC 评分排序，选取 top hits 用共免疫沉淀验证。
   - **验证方式**：对预测的互作界面进行突变，检测 TF 在基因组上的结合谱变化（ChIP-seq）。
   - **创新状态**：unverified

2. **候选名称**：TF–DNA 复合物中"柔性系绳"构象动力学的分子模拟
   - **来源局限/观察**：本文提出 UVSSA 柔性 TIR 系住 TFIIH 的模型，但未量化柔性区域的构象空间。TF–DNA 互作中，许多 TF 含 intrinsically disordered regions (IDRs)，其构象动力学影响 DNA 搜索效率。
   - **核心假设**：TF 的 IDR 通过"系绳-释放"机制调节其在 DNA 上的停留时间与搜索速度。
   - **初步方法**：用粗粒化分子动力学（CG-MD）模拟含 IDR 的 TF-DNA 复合物，计算 IDR 构象系综与 DNA 结合自由能。
   - **验证方式**：单分子 FRET 实验测量 IDR 构象变化与 DNA 结合动力学。
   - **创新状态**：unverified

3. **候选名称**：基于结构预测的 TF–DNA 损伤识别特异性分析
   - **来源局限/观察**：本文研究的是 Pol II 停滞后的修复，但 TF 本身也可能识别 DNA 损伤（如 p53 结合损伤 DNA）。STK19 将 XPD 引导至损伤位点的机制提示，TF 可能通过类似"辅助因子引导"机制参与损伤感知。
   - **核心假设**：某些 TF 在 DNA 损伤存在时，其结合特异性会改变，且这种改变可由辅助因子调控。
   - **初步方法**：用 HT-SELEX 或 Bind-seq 比较 TF 在未损伤与顺铂损伤 DNA 上的结合谱；用 AF-M 预测 TF 与 NER 因子（XPC、TFIIH）的互作。
   - **验证方式**：ChIP-seq 检测 UV 处理后 TF 在基因组上的重新分布。
   - **创新状态**：unverified

4. **候选名称**：cryo-EM 结构中"未解析区域"的 AI 补全方法
   - **来源局限/观察**：本文 cryo-EM 结构中 UVSSA TIR 等柔性区域未解析，但这些区域可能对功能至关重要。TF–DNA 复合物结构同样常缺失 IDR。
   - **核心假设**：结合 AlphaFold 预测与 cryo-EM 密度，可准确建模柔性区域。
   - **初步方法**：开发将 AF-M 预测的 IDR 构象与 cryo-EM 低分辨率密度拟合的算法（如基于 MD 的 flexible fitting）。
   - **验证方式**：对已知含 IDR 的 TF-DNA 复合物进行交叉验证，比较模型与突变实验数据。
   - **创新状态**：unverified

5. **候选名称**：TF–DNA 互作中"支架蛋白"的系统鉴定
   - **来源局限/观察**：STK19 作为支架蛋白的功能提示，许多"孤儿"蛋白可能通过支架机制参与 TF 功能调控。
   - **核心假设**：人类基因组中存在大量未被鉴定的支架蛋白，它们通过同时结合 TF 和染色质调节因子来调控 TF 活性。
   - **初步方法**：用 AF-M 对 ~2000 个功能未知的蛋白与 100 个关键 TF 进行互作筛选，SPOC 评分排序，选取高置信度候选进行实验验证。
   - **验证方式**：共免疫沉淀 + 功能丧失实验（CRISPRi）。
   - **创新状态**：unverified