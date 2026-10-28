## 01 基本信息
- **标题**：Farrerol inhibits ferroptosis and protects against LPS-induced acute lung injury by targeting the RUNX1/SLC7A11 axis
- **作者**：Yang, Yueyan; Deng, Shihua; Liu, Teng; Yin, Qing; Yang, Min; Zhang, Xintao; Jiang, Zhongyong; Wang, Xiaobian; Zhang, Sunhan; Zhang, Ting; Wu, Dongming; Xu, Ying
- **单位**：未提供（通讯作者 Xu Ying 所属机构未在摘要中列出；文中提及成都医学院第一附属医院实验室）
- **期刊/平台**：Frontiers in Immunology
- **年份**：2026-01-23（在线发表）
- **论文类型**：实验研究（in vitro + in vivo + 分子机制）
- **领域**：急性肺损伤（ALI）/ 铁死亡（ferroptosis）/ 天然药物药理 / 转录因子调控
- **关键词**：farrerol, ferroptosis, acute lung injury, RUNX1, SLC7A11, LPS
- **DOI/ID**：10.3389/fimmu.2025.1720843
- **代码**：未提供
- **数据**：原始数据包含在文章/补充材料中（Data availability statement）
- **阅读日期**：2026-05-13（按当前日期）
- **在该方向中的位置**：本文属于「小分子药物（天然黄酮类）→ 转录因子（RUNX1）→ 下游靶基因（SLC7A11）→ 铁死亡抑制」的调控轴研究。与课题方向（TF–DNA 互作 × AI/物理模拟）的关联点在于：RUNX1 作为转录因子直接结合 SLC7A11 启动子（ChIP + 双荧光素酶验证），且分子对接用于预测 farrerol 与 RUNX1 的结合模式。本文提供了 TF–DNA 结合调控的生物学证据链，可作为 AI/物理模拟方法验证的参考数据集或基准。

## 02 一句话总结
本文通过 pull-down/质谱、CETSA、Co-IP、分子对接、ChIP、双荧光素酶等实验，证明天然黄酮 farrerol 直接结合并稳定转录因子 RUNX1，进而转录激活 SLC7A11 表达、抑制铁死亡，从而减轻 LPS 诱导的急性肺损伤（ALI）。

## 03 研究问题
- **具体问题**：Farrerol 对 LPS 诱导的 ALI 是否具有保护作用？其直接分子靶点是谁？通过何种下游信号通路发挥保护作用？
- **为什么重要**：ALI/ARDS 死亡率高、缺乏特异性治疗药物；铁死亡是 ALI 的重要病理机制；farrerol 虽已知有抗炎抗氧化活性，但其直接分子靶点和调控铁死亡的具体机制不清。
- **现有方法不足**：已有研究仅报道 farrerol 通过 Nrf2/Keap1、ROS/Nox4/ERK1/2 等通路发挥保护作用，但未鉴定其直接结合蛋白，也未系统阐明其调控铁死亡的分子机制。
- **精确研究问题**：Can farrerol directly bind to and stabilize RUNX1, thereby transcriptionally activating SLC7A11 expression and inhibiting ferroptosis to protect against LPS-induced ALI?

## 04 背景与发展脉络
> 注：以下脉络基于本文引言及讨论，属「仅本文框架」，未经外部系统综述核验。

1. **ALI 病理机制研究阶段**：从炎症因子风暴、氧化应激，到近年聚焦铁死亡（ferroptosis）——一种铁依赖、脂质过氧化驱动的程序性细胞死亡。标志物包括 GPX4 抑制、SLC7A11 下调、脂质过氧化物堆积。
2. **天然黄酮类药物的肺保护研究**：黄酮类因多靶点、低毒性受关注，代表机制包括自由基清除、铁代谢调节、脂质过氧化抑制。Farrerol 来自满山红（Rhododendron dauricum），已知有抗炎、抗氧化、抗铁死亡活性，但直接靶点不明。
3. **转录因子 RUNX1 的功能研究**：RUNX1 是 RUNX 家族转录因子，在造血、肿瘤中研究较多；其在肺上皮细胞铁死亡调控中的作用此前未见报道。本文首次将 RUNX1 与 SLC7A11 转录调控、铁死亡抑制联系起来。
4. **本文主张的位置**：在「天然药物 → 直接靶蛋白 → 转录调控 → 铁死亡」链条中，本文填补了 farrerol 直接靶点（RUNX1）及其下游转录机制（SLC7A11）的空白，并首次提出 RUNX1 是肺上皮细胞铁死亡的转录调控因子。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| farrerol 直接分子靶点不明 | 已知 farrerol 有抗炎抗氧化活性，但不知其直接结合哪个蛋白 | 作者通过 pull-down + 质谱筛选直接结合蛋白，鉴定出 RUNX1、EIF3E、SLC7A11 三个候选 | Results 图 3A-B |
| farrerol 是否通过铁死亡通路保护 ALI 不清 | 已有研究报道 farrerol 抗氧化，但未与铁死亡机制直接挂钩 | 作者用 erastin 经典铁死亡模型验证 farrerol 的抗铁死亡作用 | Results 补充图 1 |
| RUNX1 是否调控 SLC7A11 转录未知 | RUNX1 在肺上皮细胞铁死亡中的角色此前无报道 | 作者通过 ChIP、双荧光素酶、突变分析验证 RUNX1 直接结合 SLC7A11 启动子 | Results 图 6J-M |
| farrerol 与 RUNX1 的结合模式不清 | 需要分子层面的结合证据 | 作者用 CETSA 验证热稳定性增强、Co-IP 验证物理互作、分子对接预测结合位点 | Results 图 3C-I, L-O |
| 既往报道 farrerol 对 LPS-ALI 无效的矛盾 | 有文献报道 farrerol 在 LPS-ALI 模型中无保护作用 | 作者归因于小鼠品系、性别、给药途径、剂量、时间点的差异 | Discussion 第 2 段 |

## 06 核心思想
1. **表面方法**：用 pull-down + 质谱筛选 farrerol 的直接结合蛋白 → 用 CETSA、Co-IP、分子对接验证 farrerol–RUNX1 互作 → 用 ChIP、双荧光素酶验证 RUNX1 对 SLC7A11 的转录调控 → 用 siRNA 敲低/过表达 RUNX1 验证功能必要性 → 在 LPS-ALI 小鼠模型中验证整体保护效果。
2. **核心洞察**：farrerol 不是通过直接抑制脂质过氧化或螯合铁离子来抗铁死亡，而是通过**稳定转录因子 RUNX1 蛋白**（而非上调其 mRNA），进而**转录激活 SLC7A11**——SLC7A11 是胱氨酸/谷氨酸反向转运体（system Xc⁻）的关键亚基，其上调促进 GSH 合成、抑制脂质过氧化。这构成了「药物 → 转录因子蛋白稳定性 → 下游靶基因转录 → 代谢通路」的间接调控链条。
3. **可能的普适教训** [Analysis]：天然小分子药物的直接靶点可能不是代谢酶或受体，而是**转录因子的蛋白稳定性调控因子**。这提示在药物靶点发现中，应关注「蛋白稳态调节」这一维度；同时，转录因子作为药物靶点可通过「稳定其表达」而非「抑制其活性」来实现治疗目的，这对 TF–DNA 互作研究提供了新的干预思路。

## 07 方法总览
- **输入**：farrerol（天然黄酮化合物）、LPS（造模剂）、BEAS-2B 人支气管上皮细胞系、C57BL/6 小鼠
- **输出**：farrerol 通过 RUNX1/SLC7A11 轴抑制铁死亡、减轻 ALI 的机制结论
- **模块**：
  1. **靶点发现**：生物素标记 farrerol pull-down + 质谱鉴定候选蛋白
  2. **互作验证**：CETSA（热稳定性）、Co-IP（物理互作）、分子对接（结合模式预测）
  3. **转录调控验证**：ChIP（RUNX1 结合 SLC7A11 启动子）、双荧光素酶报告基因（转录激活）、启动子突变分析（结合位点特异性）
  4. **功能验证（in vitro）**：siRNA 敲低 RUNX1、RUNX1 过表达质粒、铁死亡指标检测（Fe²⁺、ROS、脂质过氧化、GSH/MDA、线粒体形态）
  5. **功能验证（in vivo）**：LPS 气管内滴注诱导 ALI 小鼠模型，farrerol 预处理，评估肺水肿（W/D 比）、组织病理（H&E）、铁死亡标志物（SLC7A11、4-HNE IHC）
  6. **安全性评估**：主要器官病理 + 血清生化指标
- **训练**：不适用（非机器学习方法）
- **工具**：AutoDock-GPU（分子对接）、MOE（能量最小化）、I-TASSER（RUNX1 结构预测）、CavityPlus（结合口袋预测）
- **反馈回路**：无（非迭代优化方法）
- **假设**：farrerol 通过直接结合并稳定 RUNX1 蛋白，增强 SLC7A11 转录，从而抑制铁死亡

**文字流程**：farrerol 预处理 → LPS 刺激（in vitro/in vivo）→ 表型评估（细胞活力、肺损伤）→ 靶点筛选（pull-down/MS）→ 互作验证（CETSA/Co-IP/对接）→ 下游机制（ChIP/荧光素酶/铁死亡指标）→ 功能必要性（敲低/过表达）→ 整体保护效果确认。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Pull-down + 质谱 | 鉴定 farrerol 直接结合蛋白 | 确定直接靶点是机制研究的前提 | 输入：生物素-farrerol + 细胞裂解液；输出：候选蛋白列表（RUNX1, EIF3E, SLC7A24） | Results 图 3A-B | 无法确定 farrerol 的直接靶点，机制研究失去起点 |
| CETSA | 验证 farrerol 与 RUNX1 的直接结合（热稳定性） | 提供小分子-蛋白直接互作的物理化学证据 | 输入：farrerol 处理细胞 + 温度梯度；输出：RUNX1 热稳定性曲线 | Results 图 3C-H | 无法区分直接结合与间接效应 |
| Co-IP | 验证 farrerol-RUNX1 物理互作 | 在细胞环境中确认互作 | 输入：farrerol 处理细胞裂解液 + 抗体；输出：共沉淀条带 | Results 图 3I | 缺乏互作的生化证据 |
| 分子对接 | 预测 farrerol 在 RUNX1 上的结合位点 | 提供结构层面的结合模式预测 | 输入：RUNX1 结构（I-TASSER 预测）+ farrerol 结构；输出：对接构象、结合能 | Results 图 3L-O | 无法预测结合位点，后续突变验证缺乏指导 |
| ChIP | 验证 RUNX1 直接结合 SLC7A11 启动子 | 证明 RUNX1 是 SLC7A11 的直接转录因子 | 输入：RUNX1 抗体 + 交联染色质；输出：SLC7A11 启动子富集信号 | Results 图 6J | 无法证明 RUNX1 直接调控 SLC7A11 转录 |
| 双荧光素酶报告基因 | 验证 RUNX1 转录激活 SLC7A11 启动子 | 功能验证 RUNX1 的转录激活能力 | 输入：SLC7A11 启动子-Luc 质粒 + RUNX1 过表达；输出：荧光素酶活性比值 | Results 图 6K-M | 无法确认 RUNX1 对 SLC7A11 的转录激活作用 |
| 启动子突变分析 | 定位 RUNX1 在 SLC7A11 启动子上的精确结合位点 | 证明结合位点特异性 | 输入：野生型/突变型启动子-Luc；输出：突变后荧光素酶活性下降 | Results 图 6M | 无法确认 RUNX1 结合的具体 DNA 序列 |
| siRNA 敲低 RUNX1 | 验证 RUNX1 在 farrerol 抗铁死亡中的必要性 | 因果性验证 | 输入：siRNA-RUNX1 转染；输出：farrerol 保护效应消失 | Results 图 5A-G | 无法证明 RUNX1 是 farrerol 效应的必要介质 |
| 铁死亡指标检测（Fe²⁺、ROS、脂质过氧化、GSH/MDA、线粒体 TEM） | 确认铁死亡通路被抑制 | 表型验证 | 输入：处理细胞/组织；输出：各指标变化 | Results 图 4D-F, 7D | 无法确认 farrerol 抑制的是铁死亡而非其他死亡方式 |
| 体内 ALI 模型 | 验证整体保护效果 | 从体外到体内的转化验证 | 输入：LPS ± farrerol 处理小鼠；输出：肺组织病理、W/D 比、铁死亡标志物 | Results 图 2, 7 | 无法确认 farrerol 在整体动物水平的疗效 |

## 09 关键公式符号
**不适用**。本文为实验生物学研究，未使用数学模型或计算公式。分子对接部分使用 AutoDock 的评分函数（经验自由能评分），但文中未给出具体公式或数值。

## 10 实验设计与证据链
**数据集/群体**：
- 体外：BEAS-2B 人支气管上皮细胞系
- 体内：C57BL/6 小鼠（雄性，6-8 周龄，25-30 g），共 70 只（50 只用于 ALI 模型，20 只用于机制研究，每组 n=5）
- 造模：LPS 气管内滴注（5 mg/kg 或 10 mg/kg，不同实验组）

**指标**：细胞活力（CCK-8）、细胞毒性（LDH 释放）、细胞增殖（EdU）、ROS 水平（DCFH-DA）、线粒体膜电位（JC-1）、Fe²⁺（FerroOrange）、脂质过氧化（C11-BODIPY）、GSH/MDA 含量、组织病理（H&E）、肺水肿（W/D 比）、蛋白表达（WB、IHC）

**基线/对照**：Control 组（溶剂对照）、LPS 组（模型对照）、LPS + farrerol 组（治疗组）、siRNA 对照 + LPS + farrerol 组

**预算**：未提供

**骨干/仪器**：流式细胞仪、荧光显微镜、透射电镜、Western blot 系统、qPCR 系统（CFX96）

**oracle 输入**：不适用（非计算方法）

**评测协议**：每组至少 3 次独立重复实验，数据以 mean ± SD 表示，多组比较用 one-way ANOVA + Tukey 事后检验，两组比较用 t 检验，p < 0.05 为显著。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| CCK-8/LDH（体外） | farrerol 保护 LPS 诱导的 BEAS-2B 损伤 | LPS vs LPS+farrerol（10/20/40 μM） | farrerol 剂量依赖性恢复活力、降低 LDH | farrerol 体外保护支气管上皮细胞 | 未证明保护作用特异性针对铁死亡 | Results 图 1D-E |
| 体内 ALI 模型 | farrerol 减轻 LPS 诱导的肺损伤 | Control vs LPS vs LPS+farrerol（10/20/40 mg/kg） | farrerol 减轻肺水肿、病理损伤 | farrerol 体内保护 ALI | 未证明是直接靶向 RUNX1 的效应 | Results 图 2 |
| Pull-down + MS | farrerol 直接结合 RUNX1 | 生物素-farrerol vs 对照 | 鉴定 RUNX1 为候选靶点 | farrerol 可能直接结合 RUNX1 | 需要进一步验证 | Results 图 3A-B |
| CETSA | farrerol 稳定 RUNX1 蛋白 | farrerol 处理 vs 未处理 | RUNX1 热稳定性增强 | farrerol 直接结合并稳定 RUNX1 | 未提供结合亲和力数值 | Results 图 3C-H |
| Co-IP | farrerol 与 RUNX1 物理互作 | 抗 RUNX1 抗体免疫沉淀 | 共沉淀验证互作 | farrerol-RUNX1 在细胞内互作 | 未区分直接/间接互作 | Results 图 3I |
| 分子对接 | farrerol 结合 RUNX1 DNA 结合域 | AutoDock 对接 | 预测结合于 DNA 结合域（Arg45, Asp48, Lys90, Arg130） | farrerol 可能结合 RUNX1 DNA 结合域 | 未实验验证突变效应 | Results 图 3L-O |
| RUNX1 过表达 | RUNX1 抑制铁死亡 | 过表达 vs 对照 | 过表达抑制铁死亡指标 | RUNX1 本身具有抗铁死亡功能 | 未在体内验证 | Results 图 4 |
| RUNX1 敲低 | farrerol 保护依赖 RUNX1 | siRNA-RUNX1 + farrerol vs 对照 | 敲低后 farrerol 保护消失 | farrerol 效应依赖 RUNX1 | 未排除其他靶点贡献 | Results 图 5 |
| 铁死亡 PCR array | RUNX1 调控铁死亡相关基因 | 过表达 vs 对照 | SLC7A11 为最显著上调基因 | RUNX1 转录调控 SLC7A11 | 需要 ChIP 验证直接结合 | Results 图 6A-F |
| ChIP | RUNX1 直接结合 SLC7A11 启动子 | 抗 RUNX1 ChIP vs IgG | SLC7A11 启动子富集 | RUNX1 直接结合 SLC7A11 启动子 | 未给出结合位点序列 | Results 图 6J |
| 双荧光素酶 + 突变 | RUNX1 转录激活 SLC7A11 启动子 | 野生型 vs 突变型启动子 | 突变后激活消失 | RUNX1 通过特定 DNA 序列激活 SLC7A11 | 未验证体内结合 | Results 图 6K-M |
| 体内铁死亡指标 | farrerol 抑制体内铁死亡 | LPS vs LPS+farrerol | SLC7A11 恢复、4-HNE 降低 | farrerol 体内抑制铁死亡 | 未用铁死亡抑制剂对照 | Results 图 7 |
| 毒性评估 | farrerol 安全性 | farrerol vs 对照 | 无显著器官损伤或生化异常 | farrerol 在所用剂量下安全 | 未做长期毒性 | Results 图 8 |

## 11 结论正确解读
- **任务范围**：本文仅研究了 farrerol 在 LPS 诱导的 ALI 模型（体外 BEAS-2B + 体内小鼠）中的保护作用及其分子机制。结论不能推广到其他 ALI 病因（如 CLP 脓毒症模型，作者明确承认未验证）、其他肺细胞类型（如肺泡上皮细胞、内皮细胞）、其他物种。
- **oracle/真值输入**：不适用（非计算方法）。
- **端到端状态**：从药物处理到表型保护、靶点鉴定、下游机制、功能必要性验证，链条完整。但「farrerol 直接结合 RUNX1」的证据主要来自 CETSA 和 Co-IP，分子对接仅为预测，未做结合位点突变验证（作者在讨论中承认此局限）。
- **算力成本**：不适用。
- **历史数据依赖**：不适用。
- **模型依赖**：不适用。
- **最难情形**：作者未讨论 farrerol 在更严重 ALI 或合并感染模型中的效果；未比较 farrerol 与已知铁死亡抑制剂（如 ferrostatin-1、liproxstatin-1）的疗效差异。
- **群体/领域边界**：结论限于支气管上皮细胞（BEAS-2B）和小鼠肺组织；未涉及人原代细胞或临床样本。
- **不确定性**：farrerol 是否还有其他直接靶点？RUNX1 是否还调控其他铁死亡相关基因？farrerol 对 RUNX1 的稳定化是通过抑制泛素-蛋白酶体降解还是其他机制？这些问题未回答。

**有边界的复述**：在 LPS 诱导的 ALI 模型（BEAS-2B 细胞和 C57BL/6 小鼠）中，farrerol 通过直接结合并稳定 RUNX1 蛋白，转录激活 SLC7A11 表达，从而抑制铁死亡、减轻肺损伤。此结论限于该模型系统，且 RUNX1-farrerol 结合的精确结构基础尚未实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 分子对接预测未实验验证 | 预测 farrerol 结合 RUNX1 DNA 结合域，但未做结合位点突变验证 | 结构生物学研究 RUNX1-farrerol 复合物 | Discussion 第 3 段 |
| 仅使用 LPS 模型 | 未在 CLP 脓毒症模型中验证 | 在 CLP 诱导的 ALI 模型中进一步验证 | Discussion 第 4 段 |
| 未覆盖其他肺细胞类型 | 主要关注支气管上皮细胞（BEAS-2B） | 研究 farrerol 对肺泡上皮细胞、内皮细胞的作用 | Discussion 第 4 段 |
| 与既往文献矛盾未完全解释 | 有研究报道 farrerol 对 LPS-ALI 无保护作用 | 归因于品系、性别、给药方案差异，但未做系统比较 | Discussion 第 2 段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| farrerol 对 RUNX1 的稳定化机制未阐明 | 可能是抑制泛素-蛋白酶体降解、增强翻译、或减少自噬降解；也可能是通过结合 RUNX1 改变其构象从而减少降解 | 理解稳定化机制是药物开发的关键 | 用蛋白酶体抑制剂（MG132）和翻译抑制剂（CHX）处理，检测 RUNX1 半衰期变化 | Results 图 3 仅显示蛋白水平升高，mRNA 不变 |
| 分子对接使用 I-TASSER 预测结构 | I-TASSER 预测的 RUNX1 结构可能不准确，尤其 DNA 结合域的构象；对接结果可能为假阳性 | 对接预测的 4 个氢键残基（Arg45, Asp48, Lys90, Arg130）未被实验验证 | 对预测残基做点突变，检测 farrerol 结合是否消失 | Results 图 3L-O |
| 「直接结合」证据链不完整 | CETSA 和 Co-IP 只能证明 farrerol 与 RUNX1 存在互作，但不能排除通过中间蛋白的间接互作；也未提供结合亲和力（Kd） | 「直接结合」是全文机制的核心前提 | 用表面等离子共振（SPR）或等温滴定量热（ITC）测定结合亲和力 | Results 图 3C-I |
| 未检测 farrerol 对其他 RUNX 家族成员（RUNX2, RUNX3）的选择性 | farrerol 可能也结合 RUNX2/RUNX3，导致脱靶效应 | 选择性决定药物安全性 | 对 RUNX2/RUNX3 做同样的 CETSA/Co-IP 实验 | 未提供 |
| 体内实验中 farrerol 的给药剂量与临床相关性未讨论 | 10-40 mg/kg 的剂量在小鼠中的药代动力学参数（生物利用度、组织分布）未报告 | 影响临床转化评估 | 补充药代动力学数据 | Results 图 2 |
| 未使用铁死亡特异性抑制剂作为阳性对照 | 未比较 farrerol 与 ferrostatin-1 或 liproxstatin-1 的效果 | 无法评估 farrerol 作为铁死亡抑制剂的相对效力 | 加入铁死亡抑制剂阳性对照组 | 未提供 |
| 未检测 farrerol 对 system Xc⁻ 转运活性的直接影响 | SLC7A11 上调是转录水平证据，但未直接测量胱氨酸摄取或谷氨酸释放 | 转录上调不一定等于功能增强 | 用放射性标记胱氨酸摄取实验验证 | Results 图 6 仅显示表达水平 |

## 14 学到什么
> Agent 提炼的知识候选

1. **TF 蛋白稳定性作为药物干预靶点**：本文展示了「小分子 → 稳定 TF 蛋白 → 转录激活下游基因」的调控模式。在 TF–DNA 互作研究中，可迁移的思路是：不仅关注 TF 的 DNA 结合亲和力，还要关注 TF 蛋白的稳态调控（泛素化、降解、构象稳定化）。AI 模型可预测小分子与 TF 非 DNA 结合域（如 Runt 域外的区域）的互作，物理模拟可研究小分子结合对 TF 构象稳定性的影响。

2. **TF–DNA 结合位点预测的生物学验证范式**：本文通过 ChIP + 双荧光素酶 + 启动子突变分析，完整验证了 RUNX1 对 SLC7A11 启动子的直接结合和转录激活。这一「三步验证」范式（体内结合 → 功能激活 → 位点特异性）可直接迁移到课题中，用于验证 AI 预测的 TF–DNA 结合位点。

3. **分子对接在 TF–小分子互作中的应用**：本文用 AutoDock-GPU 预测 farrerol 与 RUNX1 的结合模式，结合 CETSA 实验验证。这提示：分子对接可作为 TF–小分子互作的初筛工具，但必须与实验验证（CETSA、Co-IP、突变分析）结合。课题中可借鉴此「计算预测 + 实验验证」闭环。

4. **铁死亡调控网络中的 TF 角色**：RUNX1 是 SLC7A11 的转录激活因子，而 SLC7A11 是铁死亡的核心调控节点。这提示在 TF–DNA 互作研究中，可关注 TF 对代谢基因（如胱氨酸转运、GSH 合成）的调控，将 TF 结合谱与代谢表型联系起来。

5. **天然产物靶点发现的方法学**：pull-down + 质谱是鉴定天然小分子直接靶点的经典方法。对于课题方向，可迁移的思路是：用类似方法鉴定其他天然黄酮/多酚类化合物在 TF–DNA 互作中的直接靶点。

6. **体内外模型的一致性验证**：本文从体外细胞到体内小鼠模型，验证了同一机制（RUNX1/SLC7A11/铁死亡）的一致性。课题中若开发 AI 预测模型，应强调在多个生物学层面（分子、细胞、组织）的验证。

## 15 与已有知识连接
- **RUNX1 的已知功能**：RUNX1（AML1）是造血发育的关键转录因子，在急性髓系白血病中频繁突变（如 t(8;21) 易位产生 RUNX1-ETO 融合蛋白）。本文将其功能扩展到肺上皮细胞的铁死亡调控，属于 RUNX1 非造血功能的新发现。可连接 RUNX1 在实体瘤中的研究（如乳腺癌、胃癌）。
- **SLC7A11 与铁死亡**：SLC7A11（xCT）是 system Xc⁻ 的轻链亚基，是铁死亡的核心调控节点。已知 p53、ATF4、NRF2 等转录因子调控 SLC7A11 表达。本文新增 RUNX1 作为 SLC7A11 的转录激活因子，扩展了铁死亡转录调控网络。
- **黄酮类化合物与铁死亡**：多种黄酮（如 quercetin、baicalein、luteolin）已被报道通过 Nrf2、GPX4 等通路抑制铁死亡。本文的 farrerol 通过 RUNX1/SLC7A11 轴发挥作用，属于新机制。可连接黄酮类化合物在 ALI/ARDS 中的保护作用研究。
- **TF–DNA 互作的计算研究**：本文的 ChIP 实验验证了 RUNX1 结合 SLC7A11 启动子，但未给出具体结合位点序列。可连接 JASPAR、TRANSFAC 等 TF 结合位点数据库，以及 AlphaFold 3、RoseTTAFold 等结构预测工具在 TF–DNA 互作预测中的应用。
- **分子对接在天然药物研究中的应用**：AutoDock 系列是常用的分子对接工具。可连接其他天然产物-TF 对接研究，以及 MD 模拟在验证对接构象稳定性中的应用。

## 16 研究想法
> Agent 生成的研究候选

1. **候选名称**：RUNX1–DNA 结合特异性的 AI 预测模型
   - **来源局限/观察**：本文通过 ChIP 验证 RUNX1 结合 SLC7A11 启动子，但未给出结合位点序列，也未系统分析 RUNX1 在肺上皮细胞中的全基因组结合谱。
   - **核心假设**：RUNX1 在肺上皮细胞中的 DNA 结合基序与其在造血细胞中的已知基序（TGTGGT）存在差异，可能受细胞类型特异性共调控因子影响。
   - **增量**：利用 ChIP-seq 数据 + 深度学习（如 CNN、Transformer）构建 RUNX1 结合位点预测模型，并与已知基序数据库比较。
   - **初步方法**：收集 RUNX1 ChIP-seq 数据（ENCODE、GEO），训练 DNA 序列 → 结合概率模型，用 SHAP 或注意力权重解释关键序列特征。
   - **验证方式**：在 BEAS-2B 细胞中验证预测的新结合位点，用 ChIP-qPCR 和荧光素酶报告基因确认。
   - **创新状态**：unverified

2. **候选名称**：farrerol–RUNX1 结合模式的 MD 模拟与自由能计算
   - **来源局限/观察**：本文分子对接预测 farrerol 结合 RUNX1 DNA 结合域，但未做突变验证，也未计算结合亲和力。
   - **核心假设**：farrerol 通过稳定 RUNX1 的 Runt 域构象（而非直接竞争 DNA 结合）来增强其转录活性。
   - **增量**：用 MD 模拟（如 GROMACS、AMBER）研究 farrerol 结合对 RUNX1 构象动力学的影响，用 MM-PBSA/GBSA 计算结合自由能。
   - **初步方法**：用 AlphaFold 2/3 预测 RUNX1 全长结构，分子对接获得 farrerol 结合构象，进行 100 ns 级 MD 模拟，分析 RMSD、RMSF、氢键占有率。
   - **验证方式**：对预测的关键残基（Arg45, Asp48, Lys90, Arg130）做点突变，用 CETSA 和 ITC 验证结合变化。
   - **创新状态**：unverified

3. **候选名称**：RUNX1 调控 SLC7A11 的进化保守性分析
   - **来源局限/观察**：本文在小鼠和人类细胞中验证了 RUNX1/SLC7A11 轴，但未分析该调控关系的进化保守性。
   - **核心假设**：RUNX1 结合 SLC7A11 启动子的调控机制在哺乳动物中保守，但在非哺乳动物中可能缺失。
   - **增量**：跨物种比较 SLC7A11 启动子区域的 RUNX1 结合基序保守性，结合系统发育分析。
   - **初步方法**：用 UCSC Genome Browser 获取多物种 SLC7A11 启动子序列，用 MEME 或 FIMO 扫描 RUNX1 基序，构建系统发育树。
   - **验证方式**：在非哺乳动物模型（如斑马鱼）中检测 RUNX1 对 SLC7A11 的调控。
   - **创新状态**：unverified

4. **候选名称**：铁死亡转录调控网络的图神经网络建模
   - **来源局限/观察**：本文仅关注 RUNX1→SLC7A11 单条通路，但铁死亡受多个 TF（p53、NRF2、ATF4）协同调控。
   - **核心假设**：TF 之间的协同/拮抗关系决定了铁死亡敏感性，单一 TF 的调控不足以预测细胞命运。
   - **增量**：构建 TF–靶基因–代谢通路的异构图，用 GNN 预测铁死亡敏感性。
   - **初步方法**：整合 ChIP-seq、RNA-seq、铁死亡表型数据，构建 TF–基因调控图，训练 GNN 模型预测铁死亡诱导剂敏感性。
   - **验证方式**：在多种细胞系中验证模型预测，用 CRISPR 敲除关键 TF 检验因果性。
   - **创新状态**：unverified

5. **候选名称**：天然黄酮类化合物与 RUNX 家族结合的虚拟筛选
   - **来源局限/观察**：本文仅研究了 farrerol 一个化合物，未系统筛选其他黄酮类化合物对 RUNX1 的结合能力。
   - **核心假设**：多种黄酮类化合物可能结合 RUNX1 的 Runt 域，但结合亲和力和选择性不同。
   - **增量**：对天然黄酮库进行虚拟筛选，识别新的 RUNX1 稳定剂。
   - **初步方法**：用 AutoDock Vina 或 Glide 对黄酮库（如 ZINC Natural Products）进行对接筛选，用 MD 模拟验证 top hits 的稳定性。
   - **验证方式**：CETSA、SPR 验证结合，细胞实验验证铁死亡抑制效果。
   - **创新状态**：unverified