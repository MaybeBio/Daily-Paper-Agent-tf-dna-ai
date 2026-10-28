## 01 基本信息

- **标题**：GAME: Genomic API for Model Evaluation
- **作者与单位**：Luthra I; Priyadarshi S; Guo R; Mahieu L; Kempynck N; Dooley D; Penzar D; Vorontsov I; Sheng Y; Tu X; Klie A; Drusinsky S; Floren A; Armand E; Alasoo K; Seelig G; Tewhey R; Koo P; Agarwal V; Gosai S; Pinello L; White MA; Lal A; Zeitlinger J; Pollard KS; Libbrecht M; Carter H; Mostafavi S; Kulakovskiy I; Hsiao W; Aerts S; Zhou J; de Boer CG（单位未在摘要中提供）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025
- **论文类型**：方法/系统/资源论文（预印本）
- **领域**：基因组学、机器学习模型基准测试、API 设计
- **关键词**：genomics models, benchmarking, API, sequence-to-activity, LLM, containerization
- **DOI/arXiv 号**：10.1101/2025.07.04.663250
- **代码**：https://github.com/de-Boer-Lab/Genomic-API-for-Model-Evaluation/tree/main
- **数据**：模块列表见 https://github.com/de-Boer-Lab/GAME_modules；具体基准数据未在摘要中详列
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文不直接提出新的 TF–DNA 结合预测模型，而是提供一个**社区驱动的标准化基准测试框架**，使任何序列-活性模型（包括 TF–DNA 结合模型）能与任何功能基因组学基准（如 DNA 结合、染色质可及性、表达）通过统一 API 通信。对本课题（TF–DNA 结合 × AI/物理模拟）而言，其价值在于：① 提供**可复现、可比较的评测协议**，解决 TF–DNA 结合模型评估中常见的"架构异质、任务异质、评估随意"问题；② 通过**隐藏 assay 类型**的设计原则，迫使模型学习底层生物学（如真正的 TF 结合）而非 assay 特异性偏差；③ **Matcher 模块**可自动对齐物种/细胞类型/分子术语，便于跨模型、跨基准的公平比较。

---

## 02 一句话总结

为解决基因组学序列-活性模型评估中架构与任务异质、评估方式随意的问题，本文构建了 GAME——一个基于 API 范式的社区驱动标准化基准测试系统，通过 Predictor（模型封装）、Evaluator（基准封装）和 LLM 驱动的 Matcher（任务自动对齐）三个模块，实现任意模型与任意基准的无缝通信与统一评测，并以基因表达和 3D 染色质构象两类任务展示了其可行性。

---

## 03 研究问题

- **具体问题**：基因组学序列-活性模型（sequence-to-activity models）的评估高度碎片化——每个项目用自定义方式评估自己的模型，导致模型之间难以公平比较，也难以判断性能提升究竟来自架构创新、训练数据差异还是评估任务差异。
- **为什么重要**：没有标准化基准，领域无法可靠追踪进展；用户也无法为特定任务（如预测某细胞类型中的 TF 结合）选择最合适的模型。
- **现有方法不足**：
  - 已有基准（如 CASP、CIFAR）针对单一明确任务，但基因组学包含多种相互交织的活性（表达、开放染色质、TF 结合、组蛋白修饰、3D 构象），且跨物种、跨细胞类型、跨条件，单一基准无法覆盖。
  - 挑战赛（DREAM、Kaggle）虽好，但局限于特定任务，无法持续扩展。
  - 现有模型评估常混淆"预测底层生物学"与"预测 assay 特异性偏差"（如用 CAGE 预测 mRNA 表达）。
- **精确研究问题**：Can a standardized, API-based, community-driven framework enable seamless and consistent benchmarking of any sequence-to-activity genomics model against any user-defined evaluation task, while minimizing assay-specific bias and supporting scalable, reproducible evaluation across computing platforms?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文摘要与引言，属「仅本文框架」，未经外部系统核验。

1. **早期阶段：单一任务基准**——如 CASP（蛋白质结构预测）、CIFAR（图像分类），依赖领域共识的固定数据集，适合任务定义清晰、评估指标统一的领域。
2. **基因组学模型兴起**——序列-活性模型（如 Enformer、Borzoi）能力不断增强，但评估方式各异，缺乏统一标准。
3. **挑战赛模式**——DREAM、Kaggle 等通过竞赛形式评估特定任务上的模型，能激发创新，但受限于单一任务、一次性举办，无法持续覆盖多样化的基因组学任务。
4. **数据整合尝试**——如 Kipoi（Avsec et al., 2019）用 API 访问基因组学 ML 模型，但缺少基准模块，且要求用户精确了解每个模型的预测目标，难以规模化统一评测。
5. **关键洞察**：基因组学任务多样性（物种 × 细胞类型 × 分子 × assay）使得"固定数据集"式基准不可行；需要的是**协议标准化**而非**数据集固定化**。
6. **GAME 的位置**：将 API 范式引入基因组学模型评测，通过 Predictor/Evaluator/Matcher 三模块解耦模型与基准，实现"任意模型 × 任意基准"的即插即用评测，并借助容器化（Apptainer）保证跨平台可复现性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 评估碎片化 | 每个项目自定义评估方式，模型间难以比较 | 缺乏统一协议；模型架构、训练数据、评估任务同时差异，难以归因 | 引言："model evaluations are siloed within publications, resulting in duplicated efforts" |
| 性能归因模糊 | 无法判断性能提升来自架构、数据还是评估任务 | 架构、数据、任务三者同时变化 | 引言："simultaneous differences in model architectures, training data, and evaluation tasks often obscure where any innovation lies" |
| Assay 偏差混淆 | 模型可能学习 assay 特异性偏差而非底层生物学 | 功能基因组学 assay 间接测量生物活性，各有偏差 | 引言："some performance gains are likely attributable to the models capturing assay-specific biases better" |
| 任务错配 | 用相关但不同的任务评估模型（如 CAGE 预测 mRNA 表达） | 用户对模型预测目标理解不足 | 引言："using CAGE predictions for mRNA expression even though they capture different RNA subsets" |
| 评估自由度大 | 实现细节（如窗口、链方向、聚合方式）影响结果 | 缺乏标准化协议约束 | Methods 节 "Module responsibilities" 中 Evaluator 需指定返回点/轨迹、链方向、窗口位置等 |
| 可扩展性差 | 新模型/新基准接入成本高 | 缺乏统一接口 | 引言："the continual addition of new models and new benchmarks is easy"（GAME 的解决方案） |

---

## 06 核心思想

### 1) 表面方法
构建一个三模块系统：**Predictor**（封装预训练模型，作为服务器监听请求并返回预测）、**Evaluator**（封装基准数据集与评估指标，作为客户端发起请求）、**Matcher**（基于本地 LLM 自动对齐任务术语，如物种、细胞类型、分子）。三者通过 TCP/IP socket 通信，各自容器化（Apptainer），支持跨平台部署。

### 2) 核心洞察
- **API 范式适用于科学模型评测**：正如 API 让不同软件系统无需了解彼此实现细节即可通信，GAME 让模型与基准无需了解彼此内部细节即可评测——模型只需实现"输入 DNA 序列，输出预测"的接口，基准只需实现"请求预测，计算指标"的接口。
- **隐藏 assay 信息以逼近底层生物学**：不向模型提供 assay 类型，迫使模型学习真正的生物学信号（如 TF 结合）而非 assay 特异性偏差。
- **LLM 解决术语对齐问题**：不同数据集对同一细胞类型/分子可能有不同命名（如 "cardiomyocyte" vs "heart"），手工映射不可扩展，LLM 可自动化这一过程。
- **社区驱动 + 最小中心化**：模块列表由社区维护（GitHub），无需中心机构持续运营，可持续扩展。

### 3) 可能的普适教训 [Analysis]
- **标准化协议比标准化数据集更可扩展**：在任务高度多样化的领域，与其争论"哪个数据集是标准"，不如定义"如何通信"的协议，让数据集和模型自由组合。
- **评测设计本身是科学问题**：如何设计评测（隐藏什么信息、提供什么上下文）直接影响结论的生物学意义——GAME 隐藏 assay 类型的设计提醒我们，评测协议的设计决策应服务于"想回答的科学问题"。
- **LLM 可作为科学工作流中的"胶水"**：不仅是生成文本，还可用于术语映射、任务对齐等结构化决策，降低人工维护成本。

---

## 07 方法总览

- **输入**：用户定义的评估任务（含 DNA 序列、物种、细胞类型、分子类型、assay 类型等元数据）；预训练序列-活性模型（封装为 Predictor）。
- **输出**：模型在指定基准上的标准化评估指标（如相关性、AUPRC 等，具体指标由 Evaluator 决定）。
- **模块**：
  1. **Evaluator**（客户端）：持有基准数据，构造请求（含序列、任务描述），发送给 Predictor，接收预测，计算指标。
  2. **Predictor**（服务器）：接收请求，解析序列以满足模型输入要求（padding/trimming/flanking），运行模型，聚合输出（跨轨迹/跨 bin），返回标准格式预测。
  3. **Matcher**（辅助服务器）：接收模糊术语（如 "cardiomyocyte"），从 Predictor 支持的术语列表中选择最佳匹配，返回映射结果。
- **通信**：TCP/IP socket，数据序列化为 JSON 或 MessagePack（MsgPack）。
- **容器化**：Apptainer（Singularity），适配 HPC 环境，无需 root 权限。
- **LLM 组件**：Gemma 3（本地部署，通过 Ollama 管理），LangChain 框架（ChatPromptTemplate + OllamaLLM）构建结构化查询。
- **流程**（7 步，对应 Fig. 1）：
  1. Evaluator 向 Predictor 发送预测请求
  2. Predictor 解析请求，必要时咨询 Matcher
  3. Matcher 返回任务映射（如细胞类型对齐）
  4. Predictor 处理序列并运行模型
  5. Predictor 格式化预测结果
  6. Predictor 返回预测给 Evaluator
  7. Evaluator 计算评估指标并输出

- **已实现模块**：5 个模型（Borzoi、Enformer、DREAM-RNN、Orca、DeepBICCN2）、6 个基准（含 3 个基因表达 Evaluator、1 个 3D 染色质 Evaluator、一致性 Evaluator 等）。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| **Predictor** | 封装预训练模型，作为服务器响应预测请求 | 统一模型接入接口，隐藏模型内部实现差异 | 输入：标准格式请求（序列+任务描述）；输出：标准格式预测 | 已实现 Borzoi、Enformer、DREAM-RNN、Orca、DeepBICCN2 五个 Predictor（Fig. 2） | 预期：移除后模型无法接入 GAME，回到各自为政的评估方式 [Analysis] |
| **Evaluator** | 封装基准数据集与评估指标，发起预测请求 | 统一基准接入接口，使不同数据集可用相同协议评估模型 | 输入：基准数据文件（.json/.npy/.txt/.xlsx）；输出：评估指标报告 | 已实现 3 个基因表达 Evaluator（MPRA 基因组/合成、合成变异）和 1 个 3D 染色质 Evaluator（Fig. 2） | 预期：移除后基准无法与模型通信，评估回到手动、非标准化流程 [Analysis] |
| **Matcher** | 自动对齐任务术语（细胞类型/物种/分子） | 不同数据集对同一实体命名不同，手工映射不可扩展 | 输入：模糊术语 + 候选列表；输出：最佳匹配 | 摘要明确说明 Matcher 由 LLM 驱动，处理 "cardiomyocyte vs heart" 等映射 | 预期：移除后需人工维护术语映射表，新基准接入成本显著上升 [Analysis] |
| **通信协议** | 定义数据交换格式（JSON/MsgPack）与 socket 通信 | 保证跨语言、跨平台、跨网络通信 | 输入：序列化请求；输出：序列化响应 | Methods 节 "Communication protocol" 详述 | 预期：移除后模块间无法通信，系统崩溃 [Analysis] |
| **容器化（Apptainer）** | 隔离运行环境，保证可复现性 | HPC 环境依赖管理复杂，Docker 需 root 权限 | 输入：容器镜像；输出：可运行环境 | Methods 节 "Containerization" 明确说明 | 预期：移除后依赖冲突风险上升，跨平台部署困难 [Analysis] |
| **一致性 Evaluator** | 检查模型对正/反向互补序列的预测一致性 | 评估模型是否学习到 DNA 双链对称性这一基本生物学约束 | 输入：序列及其反向互补；输出：预测一致性指标 | Fig. 3b 展示 Borzoi、Enformer、DeepBICCN2 的一致性评估 | 未提供消融数据；预期：移除后无法检测模型在链方向上的系统性偏差 [Analysis] |

> 注：所有"预期影响"均为 [Analysis] 推断，原文未提供消融实验。

---

## 09 关键公式符号

**不适用**。本文为系统/框架论文，未提出新的数学模型或算法公式。核心"公式"是通信协议与数据格式规范（JSON schema、socket 通信流程），而非数学表达式。

---

## 10 实验设计与证据链

### 数据集/群体、规模、指标、基线、预算、骨干/仪器、oracle 输入、评测协议

- **数据集**：
  - 基因表达任务：3 个 Evaluator——(a) Agarwal et al. MPRA（基因组来源），(b) Gosai et al. MPRA（含合成非基因组探针），(c) Martyn et al. 合成变异效应（CRISPR 引入的变异）
  - 3D 染色质构象：Orca 模型对应的构象数据
  - 一致性评估：DNA 可及性预测（Borzoi、Enformer、DeepBICCN2）
- **规模**：未在摘要中提供具体样本量
- **指标**：未在摘要中详列（Evaluator 自定义，如相关性等）
- **基线**：未在摘要中提供（各 Evaluator 内部定义）
- **预算/算力**：未提供
- **骨干/仪器**：无（框架论文）
- **Oracle 输入**：不适用（评测框架，非预测任务）
- **评测协议**：7 步 GAME 流程（Fig. 1），Evaluator 发起请求 → Predictor 处理 → 返回预测 → 计算指标

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 基因表达评估（3 个 Evaluator） | GAME 能对多种基因表达基准统一评估多个模型 | Borzoi、Enformer、DREAM-RNN 在 3 个表达 Evaluator 上分别评估 | 成功运行，产出各模型在各基准上的指标（具体数值未在摘要中给出） | GAME 协议支持不同架构模型与不同表达基准的即插即用 | 未提供模型间性能排序或与已有评估的对比，无法判断 GAME 评估结果是否与已知结论一致 | Fig. 2a |
| 3D 染色质构象评估 | GAME 能扩展到非表达类任务 | Orca Predictor 与 3D 构象 Evaluator | 成功运行 | GAME 不限于表达任务，可覆盖多种基因组活性 | 仅一个 3D 模型/基准，无法证明对所有构象类任务的普适性 | Fig. 2b |
| 一致性评估 | GAME 能评估模型对反向互补序列的对称性 | Borzoi、Enformer、DeepBICCN2 在 DNA 可及性预测上比较正/反向互补一致性 | 展示了一致性指标（具体数值未给出） | GAME 支持非标准评估维度（如链对称性） | 未提供与其他评估框架的对比 | Fig. 3b |

> 注：摘要中未提供具体数值结果，所有实验均为"成功运行/展示"级别的证据，无定量比较。

---

## 11 结论正确解读

- **任务范围**：GAME 是一个**评测框架**，不是预测模型。它解决的问题是"如何标准化地评估序列-活性模型"，而非"如何提高预测精度"。
- **Oracle/真值输入**：不适用——GAME 不涉及预测任务本身，而是模型与基准之间的通信协议。
- **端到端状态**：GAME 已实现 5 个模型和 6 个基准的接入，但属于**初步展示**（proof-of-concept），非大规模社区采用后的成熟系统。
- **算力成本**：未报告。框架本身开销主要在 LLM（Gemma 3）推理和容器构建，但具体成本未量化。
- **历史数据依赖**：GAME 依赖社区持续贡献新模型和新基准；其长期价值取决于社区采纳度，而非一次性构建。
- **模型依赖**：Matcher 依赖 Gemma 3（可通过 Ollama 替换为其他本地 LLM），但 LLM 的映射准确性未在摘要中评估。
- **最难情形**：跨物种/跨细胞类型的术语映射（如 "cardiomyocyte" vs "heart"）是 Matcher 的核心挑战，但摘要未报告失败率或人工校验成本。
- **群体/领域边界**：GAME 面向**序列-活性模型**（DNA 序列输入 → 功能活性输出），不覆盖蛋白质序列模型、结构预测模型等。对 TF–DNA 结合课题而言，GAME 适用于评估**基于 DNA 序列的 TF 结合预测模型**，但不适用于评估基于结构的 TF–DNA 对接方法。
- **不确定性**：GAME 的评估结果是否与领域已知结论一致（如 Enformer vs Borzoi 的相对优劣）未在摘要中验证；框架的"隐藏 assay 类型"设计是否能真正消除 assay 偏差也未被定量检验。

**有边界的复述**：GAME 提供了一个 API 标准，使任何 DNA 序列-活性模型（包括 TF–DNA 结合预测模型）能与任何功能基因组学基准（包括 TF 结合数据）通过统一协议通信并计算评估指标；其设计通过隐藏 assay 类型和 LLM 自动术语映射来减少评估偏差和人工成本，但该框架的评估结果尚未与领域已知结论进行系统对比验证。

---

## 12 作者自认局限

在提供的摘要和正文中，作者明确承认的局限如下：

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| Matcher 的术语匹配是"实质性挑战" | 细胞类型/物种/分子的模糊匹配难以完美解决 | 未明确说明（仅提及 Matcher 可因模块化设计而持续改进） | 摘要："determining the best way to match tasks turned out to be a substantial challenge" |
| 为降低计算成本对某些 Evaluator 数据集进行了下采样 | 摘要提到 "down-sampled certain Evaluator datasets" | 未明确说明（提及 Evaluator/Predictor 可拆分数据集实现并行化） | 摘要："we down-sampled certain Evaluator datasets (Fig. 2)" |

> 注：作者未在摘要中系统列出局限性清单；以上为摘要中明确出现的约束性陈述。未发现对 GAME 评估结果与领域已知结论一致性、LLM 映射准确率、框架可扩展性上限等问题的作者自认局限。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 摘要未报告任何定量评估结果 | 框架"可用"不等于"评估结果可靠"；GAME 可能只是把不合理的评估协议标准化了 | 如果 GAME 的评估指标或协议设计有偏差，标准化反而会放大错误 | 将 GAME 评估结果与领域已知结论（如 Enformer vs Borzoi 在特定任务上的相对表现）对比 | 摘要仅描述"成功运行"，无数值结果 |
| "隐藏 assay 类型"的设计未被验证 | 模型可能仍能从序列特征间接推断 assay 类型（如不同 assay 的文库制备偏好），从而"作弊" | 如果 assay 偏差未被真正消除，GAME 的评估结果仍可能反映 assay 伪影而非生物学 | 设计对照实验：同一模型在"提供 assay 类型"与"隐藏 assay 类型"条件下的表现差异；检查模型是否隐式编码 assay 信息 | 摘要："assay types are not provided to the models" |
| 仅展示 5 个模型、6 个基准 | 样本量小，无法证明协议对"任意"模型/基准的普适性 | 框架声称社区驱动、可扩展，但未展示接入异构模型（如不同输入长度、不同输出类型）的边界情况 | 接入更多异质模型（如短序列模型 vs 长序列模型、分类任务 vs 回归任务）测试协议鲁棒性 | 摘要："We applied GAME to several models and two representative benchmarking tasks" |
| Matcher 依赖 LLM 但未评估其准确性 | LLM 可能产生错误映射且难以察觉；"锦标赛式"分块策略可能累积错误 | 错误映射直接导致评估结果无效，且错误可能被标准化流程掩盖 | 构建人工标注的术语映射测试集，量化 Matcher 准确率；对比 LLM 映射与专家映射的差异 | 摘要："Matcher must map the cell types requested by the Evaluator to the closest matched cell types" |
| 下采样 Evaluator 数据集可能引入偏差 | 下采样可能改变数据分布，使评估结果不代表全量数据上的表现 | 如果下采样方式不当，GAME 评估结果可能误导模型选择 | 对比全量数据与下采样数据上的评估结果一致性 | 摘要："we down-sampled certain Evaluator datasets" |
| 未讨论评估指标的选择标准 | 不同任务可能需要不同指标，但 GAME 未提供指标选择指导 | 指标选择不当可能使模型比较失去意义 | 检查各 Evaluator 的指标选择是否与领域共识一致 | 摘要未提及指标设计细节 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **API 范式可迁移到 TF–DNA 结合模型评测**：本课题中，不同 TF–DNA 结合预测模型（如基于 CNN 的、基于 Transformer 的、基于物理势能的）常使用不同数据集和评估方式，难以公平比较。可借鉴 GAME 的 Predictor/Evaluator 分离思想，为 TF–DNA 结合模型定义统一接口（输入：DNA 序列 + TF 标识；输出：结合分数/概率），为 ChIP-seq、HT-SELEX、PBM 等不同实验数据定义统一评估协议。

2. **隐藏 assay 类型以逼近底层生物学**：TF–DNA 结合数据来自不同实验技术（ChIP-seq、ChIP-exo、HT-SELEX、PBM、MPRA），各有偏差。GAME 的设计原则——不向模型提供 assay 类型——可迁移到 TF–DNA 结合模型评估中：如果模型在不知道数据来源的情况下仍能准确预测结合，说明其学到了真正的序列-结合关系而非实验伪影。

3. **LLM 驱动的术语对齐可解决跨数据集元数据不一致**：TF–DNA 结合数据集中，同一 TF 可能有不同命名（如 "NF-kB" vs "NFKB1"）、同一细胞类型可能有不同描述。GAME 的 Matcher 思路（本地 LLM + 锦标赛式分块匹配）可迁移为 TF–DNA 结合数据集的自动元数据标准化工具。

4. **一致性评估作为模型质量维度**：GAME 对 DNA 可及性模型检查正/反向互补序列预测一致性。对 TF–DNA 结合模型，这一思路可扩展为：检查模型对反向互补序列的结合预测是否一致（考虑到 TF 结合基序通常具有回文或反向重复特征），作为模型生物学合理性的额外检验维度。

5. **容器化保证评测可复现性**：TF–DNA 结合模型依赖的深度学习框架、版本、GPU 环境差异大，GAME 使用 Apptainer 容器化的做法可直接迁移，确保同一模型在不同平台上评测结果一致。

6. **社区驱动的模块列表比中心化基准更可持续**：TF–DNA 结合领域新模型、新数据不断涌现，中心化基准难以跟上。GAME 的"社区维护模块列表 + 统一协议"模式可迁移为 TF–DNA 结合领域的持续评测生态。

---

## 15 与已有知识连接

- **Kipoi (Avsec et al., 2019)**：GAME 明确提及 Kipoi 作为前驱——Kipoi 用 API 访问基因组学 ML 模型，但缺少基准模块且要求用户精确了解模型预测目标。GAME 在此基础上增加了 Evaluator 基准模块和 Matcher 自动对齐，解决了 Kipoi 的扩展性问题。对本课题：TF–DNA 结合模型可参考 Kipoi 的模型仓库模式 + GAME 的评测协议，构建"模型 + 基准"一体化的社区资源。
- **ENCODE 基准与 DREAM 挑战赛**：GAME 的"社区驱动"理念与 DREAM 挑战赛一脉相承，但 DREAM 是"一次性竞赛"，GAME 是"持续协议"。TF–DNA 结合领域已有 ENCODE 的 ChIP-seq 统一处理流程，可视为数据层面的标准化，GAME 则补充了模型评估层面的标准化。
- **CASP（蛋白质结构预测）**：GAME 引用 CASP 作为"领域共识基准"的典范，但指出基因组学任务多样性使 CASP 模式不可直接复制。对本课题：TF–DNA 结合预测可类比 CASP 的"盲测"模式，但需借助 GAME 式协议来管理任务多样性。
- **Encode 的"瓶颈"问题（Sasse et al., 2023）**：GAME 引言引用 Sasse 等发现模型能预测变异效应大小但难以预测方向，说明"标准化评测能揭示模型局限"。对本课题：TF–DNA 结合模型评估中，应同样关注"模型在哪些维度上失败"而非仅报告平均性能。
- **LLM 在科学工作流中的应用**：GAME 的 Matcher 使用 Gemma 3 + LangChain + Ollama，代表 LLM 作为科学工具（而非预测模型）的新趋势。对本课题：LLM 可用于 TF–DNA 结合数据集的元数据标准化、文献知识提取、跨数据库实体对齐等辅助任务。
- **容器化与可复现性（Apptainer/Singularity）**：GAME 选择 Apptainer 而非 Docker，因其适配 HPC 且无需 root 权限。对本课题：TF–DNA 结合模型评测常需 GPU 集群，Apptainer 是更实际的容器化选择。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF–DNA 结合模型的 GAME 化基准测试协议
- **名称**：TF-GAME: A Standardized Benchmarking Protocol for Transcription Factor–DNA Binding Models
- **来源局限/观察**：TF–DNA 结合预测模型（基于序列的深度模型、基于结构的物理模型）评估碎片化，无法公平比较；GAME 框架提供了可迁移的 API 范式。
- **核心假设**：将 GAME 的 Predictor/Evaluator/Matcher 架构适配到 TF–DNA 结合领域，能显著降低跨模型比较的难度，并揭示模型在特定 TF 家族、特定细胞类型或特定变异类型上的系统性优劣。
- **初步方法**：定义 TF–DNA 结合预测的统一 API（输入：DNA 序列 + TF 标识 + 物种/细胞类型；输出：结合分数），封装现有模型（如 DeepSEA、Enformer 微调版、基于 AlphaFold 结构的打分函数）为 Predictor；将 ChIP-seq、HT-SELEX、PBM、MPRA 等数据封装为 Evaluator；用 Matcher 自动对齐 TF 命名和细胞类型术语。
- **验证方式**：在 3-5 个已有公开基准（如 ENCODE ChIP-seq、UniPROBE）上运行，对比 GAME 化评估结果与原始论文报告结果的一致性；邀请第三方模型接入测试协议鲁棒性。
- **创新状态**：unverified（框架迁移思路已有先例，但 TF–DNA 结合领域的实现未见报道）

### 候选 2：Assay-Blind 评估揭示 TF 结合模型是否学到底层生物学
- **名称**：Assay-Blind Evaluation: Do TF–DNA Binding Models Learn Biology or Assay Artifacts?
- **来源局限/观察**：GAME 隐藏 assay 类型的设计原则未被验证；TF–DNA 结合数据跨技术差异大（ChIP-seq 有抗体偏好、HT-SELEX 为体外、MPRA 为合成环境），模型可能学习技术伪影。
- **核心假设**：在"不提供 assay 类型"条件下，当前 TF–DNA 结合模型的性能会显著下降，且下降幅度与模型架构相关——这能定量揭示模型对 assay 伪影的依赖程度。
- **初步方法**：选取 3-5 个 TF，收集其在不同 assay（ChIP-seq、HT-SELEX、PBM、MPRA）下的结合数据；训练/微调同一模型架构，分别在"提供 assay 标签"和"隐藏 assay 标签"条件下评估；比较性能差异并分析模型注意力/特征归因在两种条件下的变化。
- **验证方式**：若模型在 assay-blind 条件下仍保持较高性能，说明其学到了跨技术稳健的生物学信号；若性能骤降，则需检查训练数据中 assay 偏差的贡献。
- **创新状态**：unverified（GAME 提出该原则但未验证；TF–DNA 结合领域未见类似系统研究）

### 候选 3：LLM 驱动的 TF 结合数据元数据自动对齐
- **名称**：AutoMeta-TF: LLM-Based Metadata Alignment for Cross-Dataset TF–DNA Binding Benchmarking
- **来源局限/观察**：GAME 的 Matcher 模块展示了 LLM 在术语对齐中的潜力，但未评估其准确性；TF–DNA 结合数据集中 TF 命名、细胞类型描述、物种标识高度不一致。
- **核心假设**：本地部署的 LLM（如 Gemma 3）配合锦标赛式分块策略，能在 TF–DNA 结合数据集的元数据对齐任务上达到可接受准确率（>95%），且可通过人工抽查校验。
- **初步方法**：构建 TF–DNA 结合数据集元数据测试集（含 TF 别名、细胞类型同义词、物种名变体）；实现 GAME 式 Matcher（LLM + 分块 + 锦标赛选择）；对比 LLM 映射与专家人工映射的一致性；量化错误类型（如"无法匹配"vs"错误匹配"）。
- **验证方式**：在 100+ 对（查询术语，候选列表）上评估准确率；分析失败案例并迭代 prompt 设计。
- **创新状态**：unverified（GAME 提出思路但未提供评估数据）

### 候选 4：TF 结合模型的一致性评估作为质量指标
- **名称**：Strand-Symmetry Consistency as a Quality Metric for TF–DNA Binding Models
- **来源局限/观察**：GAME 对 DNA 可及性模型检查正/反向互补序列预测一致性；TF 结合基序常具有回文或反向重复特征，模型对反向互补序列的预测应具有对称性。
- **核心假设**：当前 TF–DNA 结合模型在反向互补序列上的预测不一致程度与模型泛化能力负相关，可作为无需标注数据的模型质量指标。
- **初步方法**：对多个 TF–DNA 结合模型（不同架构、不同训练数据），计算其在正/反向互补序列上的预测差异（如余弦距离、秩相关）；将该指标与模型在独立测试集上的性能（AUPRC）做相关分析。
- **验证方式**：若一致性指标与泛化性能显著相关，则支持其作为无监督质量指标；否则需分析不一致性的来源（如训练数据链偏好）。
- **创新状态**：unverified（GAME 展示了一致性评估的可行性，但未建立其与模型质量的关系）

### 候选 5：GAME 框架扩展到 TF–DNA 结合变体效应预测
- **名称**：Variant-GAME: Standardized Evaluation of TF–DNA Binding Models on Variant Effect Prediction
- **来源局限/观察**：GAME 的 Martyn 等 Evaluator 评估了合成变异效应，但未聚焦 TF 结合；TF–DNA 结合模型的变体效应预测（如 eQTL、GWAS 变异的功能注释）是重要应用场景，但评估方式各异。
- **核心假设**：将 GAME 协议应用于 TF–DNA 结合变体效应预测，能统一现有分散的评估（如不同 eQTL 数据集、不同细胞类型），并揭示模型在"预测变异方向"上的系统性失败（呼应 Sasse et al. 的发现）。
- **初步方法**：定义变体效应预测的统一接口（输入：参考/变异序列 + TF + 细胞类型；输出：结合分数变化）；封装现有模型；构建包含多个 eQTL 数据集和 CRISPR 扰动数据的 Evaluator；用 GAME 协议运行并分析模型在变异方向预测上的表现。
- **验证方式**：对比 GAME 化评估结果与各数据集原始论文报告的一致性；重点分析"方向预测失败"的普遍性。
- **创新状态**：unverified（GAME 提及变体效应 Evaluator 但未深入 TF 结合场景）