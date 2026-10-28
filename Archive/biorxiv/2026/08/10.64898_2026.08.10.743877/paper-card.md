## 01 基本信息

- **标题**：CALFP-MHC: Interpretable Pan-Allelic Prediction of Peptide-MHC Binding and Presentation Using Chemically Grounded Fingerprints and Contrastive Learning
- **作者**：My-Diem Nguyen Pham; Thi-Kim-Cuong Ho; Hoai-Nghia Nguyen; Le-Son Tran; Minh-Duy Phan; Vy Nguyen
- **单位**：未提供（作者单位未在摘要中列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026-08-14
- **论文类型**：预印本（方法学 + 基准评测）
- **领域**：计算免疫学 / 肽-MHC 结合预测 / 深度学习
- **关键词**：peptide-MHC binding, cheminformatics fingerprints, contrastive learning, interpretability, pan-allelic prediction
- **DOI/ID**：10.64898/2026.08.10.743877
- **代码**：https://github.com/ddiem-ri-4D/CALFP-MHC
- **数据**：MHCflurry-2.0、NetMHCpan-4.1、NetMHCIIpan-4.1、DeepMHCII、TESLA（均公开来源）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文虽聚焦肽-MHC 结合（而非 TF-DNA），但其核心方法——用化学指纹（MACCS/ECFP/RDKit）编码氨基酸残基、以监督对比学习组织潜在空间、用混合卷积-Transformer 建模序列互作、以及通过注意力/积分梯度提供可解释性——对 TF-DNA 结合预测具有高度可迁移性。其"化学接地表示 + 对比预训练 + 可解释归因"的范式可直接迁移到 TF 结合位点预测与结合机制解析。

---

## 02 一句话总结

本文提出 CALFP-MHC 框架，用四种化学指纹（MACCS、ECFP4、ECFP6、RDKit）编码肽段和 MHC 伪序列的每个氨基酸残基，结合正弦位置编码，通过监督对比预训练 + 二分类微调的两阶段训练，在 112 个 HLA-I 和 53 个 HLA-II 等位基因上实现 AUC 0.93–0.97 的肽-MHC 结合预测，并在 200:1 类别不平衡下保持 AUC > 0.90，同时通过注意力与积分梯度归因恢复已知锚定残基位置。

---

## 03 研究问题

- **具体问题**：现有肽-MHC 结合预测器将氨基酸编码为离散符号或 one-hot 向量，丢失了残基层面的化学信息（官能团、原子连接性、亚结构特征），导致在类别不平衡、稀有等位基因和分布外肽段上性能退化，且缺乏可解释性。
- **为什么重要**：准确且可解释的肽-MHC 结合预测是肿瘤新抗原筛选、疫苗设计和精准免疫治疗的核心环节；理解"哪些残基、哪些化学基团驱动结合"对机制研究和临床转化同样关键。
- **现有方法不足**：NetMHCpan、MHCflurry、BigMHC 等使用序列符号或 one-hot 编码，无法显式捕捉残基侧链的化学性质；多数模型在类别不平衡下崩溃；可解释性有限，无法定位结合核心。
- **精确研究问题**：Can chemically grounded amino acid representations (molecular fingerprints) combined with supervised contrastive learning improve both the accuracy and interpretability of pan-allelic peptide-MHC binding prediction under class imbalance and distribution shift?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 的引用与叙述，属「仅本文框架」，未经外部独立核验。

1. **第一代：基于序列 motif 与位置权重矩阵（PWM）**。早期方法用序列 logo 和位置权重矩阵描述结合基序，简单但无法捕捉残基间协同效应和非线性互作。
2. **第二代：基于神经网络的序列编码**。NetMHCpan 系列（1）、MHCflurry（2）、MixMHCpred（4）、DeepMHCII（5）等用序列符号或 one-hot 编码 + CNN/RNN/Transformer，显著提升预测精度，但氨基酸被当作离散符号，丢失化学信息。
3. **第三代：化学信息学表示**。Lee 和 Min（2023）（9）提出用分子指纹编码氨基酸；Adamczyk 等（2026）（10）系统评估了 MACCS、ECFP4、ECFP6、RDKit 指纹在肽基准上的表现，证明化学接地表示可达到与符号编码竞争的性能。
4. **对比学习在生物序列中的应用**。Khosla 等（24）提出监督对比学习框架；ConBoTNet（11）将其应用于 MHC-II 肽结合预测，证明对比预训练可改善潜在空间结构。
5. **本文位置**：首次将化学指纹表示 + 监督对比学习 + 混合卷积-Transformer 架构统一在一个框架中，同时覆盖 MHC-I 和 MHC-II，并强调可解释性（注意力 + 积分梯度）与极端类别不平衡下的鲁棒性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 氨基酸离散符号编码丢失化学信息 | 模型无法区分化学性质相似但符号不同的残基，或符号相同但化学环境不同的场景 | 离散符号/one-hot 编码不包含官能团、原子连接性、亚结构等化学信息 | Introduction 第 1 段；"Existing methods represent amino acids as discrete symbols... which inadequately capture the physicochemical properties of residue side chains" |
| 类别不平衡下性能退化 | 竞争方法在 100:1 或 200:1 负正比下 AUC 降至 0.5–0.6，PPV ≤ 0.2 | 训练数据分布不平衡导致模型偏向多数类 | Results 图 2b、图 3b；"at a 100:1 ratio, NetMHCpan and BigMHC fell below 0.6, whereas deepAntigen, MixMHCpred and MHCflurry approached near-random performance" |
| 稀有等位基因泛化差 | 部分等位基因（如 HLA-B*39:10、HLA-B*35:04）上竞争方法接近随机 | 训练数据中稀有等位基因样本不足 | Results 图 2a；"some alleles... approaching near-random performance (AUC ~0.5–0.6; PPV < 0.3)" |
| 可解释性不足 | 黑盒模型无法指出哪些残基/化学基团驱动结合决策 | 现有模型缺乏注意力归因或化学层面的解释输出 | Introduction 第 1 段；"Many current approaches also provide limited interpretability" |
| 分布外泛化差 | 未见过的肽段或 MHC 分子上性能下降 | 符号编码无法泛化到化学性质相似但序列不同的残基组合 | Results 图 2b；"This trend was also observed for unseen peptides and MHC molecules" |

---

## 06 核心思想

**1) 表面方法**：
- 将每个氨基酸残基编码为 4,263 维化学指纹向量（MACCS 166-bit + ECFP4 1,024-bit + ECFP6 2,048-bit + RDKit 1,024-bit，共 4,262 bit，文中写 4,263 维）
- 肽段和 MHC 伪序列（34 残基）分别编码为指纹矩阵，加入正弦位置编码
- 用可学习线性投影将 MHC 表示映射为与肽段结合核心长度 k 匹配的核（kernel）
- 对肽段每个滑动窗口与 MHC 核做逐元素乘（element-wise multiplication），生成互作矩阵
- 混合卷积-Transformer（瓶颈 Transformer + ResNet 块）骨干网络处理互作矩阵
- 两阶段训练：阶段 1 监督对比学习（supervised contrastive loss, τ=0.07）组织潜在空间；阶段 2 冻结编码器，微调二分类头（binding/non-binding）

**2) 核心洞察**：
- 化学指纹将残基从"离散符号"转化为"连续化学空间中的向量"，使模型能泛化到化学性质相似但序列不同的残基——这是分布外泛化的关键
- 对比预训练在微调前先按结合类别组织潜在空间，使正负样本在嵌入空间中分离，从而在极端类别不平衡下保持判别力
- 可学习 MHC 核 + 滑动窗口互操作建模了"肽段残基与 MHC 结合口袋残基"的局部化学互补性，而非仅序列共现

**3) 可能的普适教训 [Analysis]**：
- 对 TF-DNA 互作：DNA 碱基同样可被编码为化学指纹（如功能团、氢键供体/受体模式、静电势），而非仅 one-hot 的 A/C/G/T——这可能提升对非经典结合位点的泛化
- 对比预训练"先聚类、后分类"的两阶段策略，对 TF 结合位点预测中正负样本极度不平衡（少数结合位点 vs 大量非结合位点）的场景可能同样有效
- 可学习核 + 滑动窗口的互作建模方式，可迁移为"TF 结构域残基 vs DNA 碱基"的成对化学互补打分

---

## 07 方法总览

- **输入**：肽段氨基酸序列（MHC-I: 8–11 aa；MHC-II: 13–18 aa）+ MHC 等位基因（以 34 残基伪序列表示）
- **输出**：结合概率（二分类）；注意力权重与积分梯度归因（可解释性输出）
- **模块**：
  1. 指纹编码器：每个残基 → 4,263 维化学指纹向量
  2. 位置编码：正弦位置编码，逐元素加到指纹向量
  3. MHC 核投影：可学习线性层将 MHC 伪序列矩阵投影为结合核心核
  4. 互作层：肽段滑动窗口 × MHC 核逐元素乘 → 互作矩阵
  5. 骨干网络：瓶颈 Transformer（2 blocks, 9 heads, bottleneck 256）+ ResNet 块（1-D depthwise conv, kernel 9, 3,200 channels, GLU）
  6. 对比投影头：两层 FC（800→64）+ SiLU + L2 归一化（仅阶段 1）
  7. 分类头：单线性层（64 维 → 2 类），softmax（阶段 2）
- **训练**：Adam 优化器，weight decay 1×10⁻⁴（文中写 1×10□□，推测为 1e-4）；阶段 1 监督对比损失（τ=0.07）；阶段 2 冻结编码器，微调分类头，binary cross-entropy；batch size 256，学习率 1×10⁻⁴（文中写 1×10□□），100 epochs，early stopping patience 10
- **硬件**：NVIDIA A100 GPU，CUDA 11.4
- **流程**：肽段和 MHC 伪序列 → 逐残基指纹编码 → 加位置编码 → MHC 核投影 → 滑动窗口互作 → 瓶颈 Transformer 编码 → 对比预训练 → 冻结编码器 → 微调分类头 → 输出结合概率 + 注意力/梯度归因

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 化学指纹编码（MACCS/ECFP4/ECFP6/RDKit） | 将残基编码为化学特征向量 | 捕获官能团、原子连接性、亚结构等离散符号丢失的化学信息 | 输入：氨基酸残基；输出：4,263 维向量 | Results 图 2a–c、图 3a–c；作者声称优于符号编码基线 | 预期影响 [Analysis]：退化为 one-hot 类表示，丢失化学相似性泛化能力；实测消融未提供 |
| 正弦位置编码 | 注入残基位置信息 | 区分相同残基在不同位置的贡献 | 输入：指纹向量 + 位置索引；输出：位置调制向量 | Methods 节；引用 Vaswani et al. (12) | 预期影响 [Analysis]：无法区分序列顺序不同的同组成肽段；实测消融未提供 |
| MHC 核投影（可学习线性层） | 将 MHC 伪序列映射为结合核心 | 使 MHC 表示与肽段窗口维度匹配，建模口袋-残基互补 | 输入：34×4263 MHC 矩阵；输出：k×4263 核 | Methods 节；公式 (1) | 预期影响 [Analysis]：移除后 MHC 与肽段无法在残基级别对齐互作；实测消融未提供 |
| 滑动窗口互作层（逐元素乘） | 计算肽段窗口与 MHC 核的化学互补 | 显式建模局部残基-残基互作 | 输入：肽段窗口 × MHC 核；输出：互作矩阵 F_t | Methods 节；公式 (2) | 预期影响 [Analysis]：移除后模型退化为独立编码肽段和 MHC，丢失互作信息；实测消融未提供 |
| 瓶颈 Transformer + ResNet 骨干 | 建模长程依赖与局部特征 | 捕获结合核心内外的协同效应 | 输入：互作矩阵；输出：全局表示 g | Methods 节；图 1c–d | 预期影响 [Analysis]：移除 Transformer 后可能丢失跨窗口依赖；实测消融未提供 |
| 监督对比预训练 | 按结合类别组织潜在空间 | 在微调前使同类样本聚拢、异类分离，提升不平衡鲁棒性 | 输入：全局表示 g；输出：对比损失 | Results 图 4g、4k；引用 Khosla et al. (24) | 预期影响 [Analysis]：移除后在不平衡数据上判别力下降；实测消融未提供 |
| 注意力 + 积分梯度归因 | 输出残基/化学基团重要性 | 提供可解释性，定位结合核心 | 输入：训练好的模型；输出：注意力权重 + 梯度归因图 | Results 图 4a–f、4h–i；恢复已知锚定残基 | 预期影响 [Analysis]：移除后模型变为黑盒，无法用于机制研究；实测消融未提供 |

---

## 09 关键公式符号

**1) MHC 核投影**：
C = W·H_MHC
- C：MHC 核矩阵，形状 k × d（k = 结合核心长度，d = 4,263）
- W：可学习投影矩阵
- H_MHC：MHC 伪序列的指纹矩阵（34 × d）

**2) 滑动窗口互作**：
F_t = P_t ⊙ C
- F_t：第 t 个窗口的互作向量
- P_t：肽段第 t 个长度为 k 的窗口的指纹矩阵
- ⊙：逐元素乘法（element-wise multiplication）
- t = 1, ..., T，T = L - k + 1（L = 肽段长度）

**3) 多头自注意力（MHSA）**：
Q = X·W_Q, K = X·W_K, V = X·W_V
- Q, K, V：查询、键、值矩阵
- W_Q, W_K, W_V：可学习投影矩阵
- 注意力更新：Attention(Q,K,V) = softmax(QKᵀ/√d_h + B)·V
  - d_h：每个头的维度
  - B：相对位置偏置（relative positional bias）

**4) 监督对比损失**：
L_sup = Σᵢ (-1/|P(i)|) Σ_{p∈P(i)} log [ exp(zᵢ·z_p/τ) / Σ_{a∈A(i)} exp(zᵢ·z_a/τ) ]
- zᵢ：样本 i 的 L2 归一化嵌入
- P(i)：与 i 同类的正样本集合
- A(i)：除 i 外的所有样本
- τ：温度参数（= 0.07）

**5) 二分类损失**：
L_BCE = -[y·log(ŷ) + (1-y)·log(1-ŷ)]
- y：真实标签（1 = 结合，0 = 非结合）
- ŷ：预测结合概率

---

## 10 实验设计与证据链

**数据集/群体**：
- 训练集：基于 NetMHCpan-4.1 和 MHCflurry-2.0 的大规模预测生成，共 567,816 阳性 + 18,520,426 阴性（MHC-I）；MHC-II 用 NetMHCIIpan-4.1 和 DeepMHCII 生成，262,731 阳性 + 464,455 阴性
- 验证集：MHC-I 322,842 阳性 + 18,275,454 阴性；MHC-II 90,070 阳性 + 95,014 阴性
- 等位基因覆盖：MHC-I 112 个等位基因（48 个用于 head-to-head 对比）；MHC-II 53 个等位基因
- 独立实验数据：MHC-I MS/MS 数据集（2,827 阳性 + 800 阴性，16 个等位基因）；MHC-II 复合数据集（MS/MS + IC50，306 阳性 + 214 阴性）
- TESLA 新抗原数据集：608 对（37 阳性 + 571 阴性），预处理后 570 对（36 阳性 + 534 阴性），13 个等位基因

**指标**：AUC（ROC 曲线下面积）、PPV（阳性预测值）、敏感性、特异性

**基线/对比工具**：NetMHCpan、MHCflurry、MixMHCpred、BigMHC、deepAntigen（MHC-I）；NetMHCIIpan、DeepMHCII、DeepSeqPanII、MixMHC2pred、TLimmuno2（MHC-II）

**硬件**：NVIDIA A100 GPU，CUDA 11.4

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| MHC-I 等位基因级基准 | CALFP-MHCI 在 48 个等位基因上优于现有工具 | 对比 NetMHCpan、BigMHC、deepAntigen、MixMHCpred、MHCflurry | AUC 0.95–1.0，PPV > 0.8；竞争方法部分等位基因 AUC 0.5–0.6 | CALFP-MHCI 在多样等位基因上更稳健 | 未提供逐等位基因统计显著性检验 | Results 图 2a |
| 类别不平衡压力测试 | 在 200:1 负正比下保持性能 | 负正比从 1:1 增至 200:1 | CALFP-MHCI AUC > 0.9，PPV 0.8–0.9；竞争方法 AUC < 0.6，PPV ≤ 0.2 | 对比预训练 + 平衡训练提升不平衡鲁棒性 | 未提供消融证明是具体哪个组件贡献了鲁棒性 | Results 图 2b |
| MHC-II 等位基因级基准 | CALFP-MHCII 优于现有工具 | 对比 NetMHCIIpan、DeepMHCII、DeepSeqPanII、MixMHC2pred、TLimmuno2 | AUC 0.9–1.0，PPV > 0.7；稀有等位基因（如 HLA-DPB1*15:01, n=34）上竞争方法 AUC=0.50，CALFP-MHCII AUC=0.87 | 在数据稀疏等位基因上泛化更好 | 稀有等位基因样本量小，置信区间未报告 | Results 图 3a |
| MS/MS 独立验证 | 在实验确认的 MHC 配体上保持区分度 | 2,827 阳性 + 800 阴性（MHC-I）；306 阳性 + 214 阴性（MHC-II） | 显著分离（p < 0.001 MHC-I；p < 0.01 MHC-II） | 模型泛化到实验数据 | 未报告具体 AUC 值 | Results 图 5a–c |
| TESLA 新抗原优先级排序 | 区分免疫原性与非免疫原性新抗原 | 36 阳性 + 534 阴性 | CALFP-MHCI p < 0.001；NetMHCpan p = 0.980；BigMHC p = 0.086 | CALFP-MHCI 捕捉了 T 细胞识别相关特征 | 样本量小（36 阳性），无法可靠区分 AUC 差异 < 0.10–0.15 的模型 | Results 图 6b |
| 可解释性分析 | 注意力/积分梯度恢复已知锚定残基 | 与已知结构/基序对比 | 恢复 MHC-I 的 P2 和 PΩ 锚定位、MHC-II 的 P1/P4/P6/P9；官能团归因指向胺、羰基、羟基、芳香环 | 模型内部表征与已知结合机制一致 | 未与晶体结构接触图定量对比 | Results 图 4a–f、4h–i |

---

## 11 结论正确解读

- **任务范围**：本文评测的是肽-MHC 结合与呈递预测，而非免疫原性预测。TESLA 数据上的表现仅表明模型能部分区分免疫原性肽，但作者明确承认样本量限制。
- **oracle/真值输入**：训练标签来自 NetMHCpan-4.1 和 MHCflurry-2.0 的预测输出，而非实验测量。这意味着训练集上的性能反映的是与现有工具的"一致性"，而非真实生物学准确性。独立 MS/MS 和 TESLA 数据提供了部分实验验证，但覆盖的等位基因和组织类型有限。
- **端到端状态**：模型是端到端训练的（从指纹输入到结合概率），但 MHC 伪序列的 34 残基定义依赖先验结构知识（Nielsen 等），并非完全从数据中学习。
- **算力成本**：训练在单张 NVIDIA A100 上完成（文中未报告具体训练时间），推理成本未报告。
- **历史数据依赖**：训练数据来自现有预测器的输出，因此模型性能上界受限于这些预测器的质量。如果这些预测器本身有系统性偏差，CALFP-MHC 会继承这些偏差。
- **最难情况**：稀有等位基因（如 HLA-DPB1*15:01，仅 34 个训练对）和极端类别不平衡（200:1）是模型表现最受挑战的场景，但 CALFP-MHC 在此类情况下仍保持 AUC > 0.87。
- **有边界的复述**：CALFP-MHC 在"与现有预测器输出一致"的基准上优于 SOTA 工具，在有限的外部实验数据上保持区分度，并提供了与已知结合基序一致的归因解释。其性能优势在类别不平衡和稀有等位基因场景下最为显著，但训练标签的预测器依赖性意味着其绝对准确性尚未被大规模实验数据直接验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 训练标签依赖预测器输出 | 训练数据来自 NetMHCpan 和 MHCflurry 的预测，而非实验测量 | 未明确提及（但 Discussion 中强调独立实验验证的重要性） | Methods "Data collection and preprocessing" 段 |
| 静态指纹不反映构象柔性 | 指纹编码不包含侧链构象变化、肽段折叠或结合诱导的构象重排 | 作者在 Discussion 中承认"fingerprint representations... do not account for conformational flexibility, peptide folding, or binding-induced structural rearrangements" | Discussion 第 2 段 |
| 未建模抗原加工上游过程 | 不包含蛋白酶体切割、TAP 转运等抗原加工步骤 | 作者承认"does not explicitly model upstream antigen-processing mechanisms such as proteasomal cleavage or TAP transport" | Discussion 第 2 段 |
| TESLA 样本量小 | 仅 36 个免疫原性肽，统计功效有限 | 作者指出"the dataset is adequately powered to detect large discrimination effects (AUC ≥ 0.65) but cannot reliably rank predictors whose true AUC difference is smaller than approximately 0.10-0.15" | Results 图 6b 相关段落 |
| 注意力权重非因果证据 | 作者明确警告"attention weights are not equivalent to causal feature importance and should be interpreted as indicative rather than definitive evidence" | 建议用晶体接触数据验证归因 | Results 图 4 相关段落；Discussion 第 3 段 |
| MS/MS 数据覆盖有限 | 外部验证数据覆盖的等位基因和组织类型有限 | 未明确提及 | Results 图 5 相关段落 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 训练标签来自预测器输出 | 模型可能只是在"模仿"NetMHCpan/MHCflurry 的偏差，而非学习真实结合规则。性能提升可能反映的是"蒸馏"了多个预测器的共识，而非发现了新生物学 | 如果训练标签有系统性错误，模型会继承并放大这些错误 | 在 IEDB 等实验基准上独立评测；与仅用实验数据训练的模型对比 | Methods "Data collection and preprocessing" 段 |
| 指纹维度 4,263 远高于序列长度 | 高维稀疏输入可能导致过拟合，尤其在稀有等位基因上。对比预训练可能部分缓解，但未做消融 | 高维输入增加计算成本，且可能引入噪声维度 | 对比不同指纹组合（仅 MACCS vs 仅 ECFP vs 全部）的性能与过拟合程度 | Methods "CALFP-MHC training" 段 |
| 注意力权重 ≠ 因果重要性 | 作者自己承认这一点，但论文标题含"Interpretable"，读者可能过度解读注意力图为"结合机制" | 可解释性声明需要更严格的验证标准 | 用 in silico 突变实验（如 alanine scanning）验证归因预测的锚定残基 | Results 图 4 相关段落；Discussion 第 3 段 |
| 类别不平衡鲁棒性可能来自训练策略而非指纹 | 作者将鲁棒性归因于对比预训练 + 平衡训练，但未做消融区分指纹表示 vs 训练策略的贡献 | 如果鲁棒性主要来自平衡采样，则指纹表示的优势需要重新评估 | 用 one-hot 编码 + 相同对比预训练/平衡策略做对照实验 | Results 图 2b、图 3b |
| 与竞争工具的比较公平性存疑 | 竞争工具（NetMHCpan 等）未在相同平衡条件下重训练，比较可能不公平 | 如果竞争工具在非平衡数据上训练，其性能下降可能反映训练数据差异而非模型能力 | 在相同训练/验证划分下重训练所有基线 | Results 图 2a、图 3a |
| 伪序列 34 残基定义依赖先验结构知识 | 该定义来自 Nielsen 等的晶体结构分析，可能不适用于所有等位基因或非常规结合模式 | 对未知构象或非经典结合模式的泛化能力受限 | 在结构未知的等位基因上测试；对比端到端学习 MHC 表示 | Methods "Data collection and preprocessing" 段 |
| 未报告置信区间和统计检验 | 除 TESLA 上的 DeLong 检验外，未报告逐等位基因的置信区间 | 无法判断性能差异是否统计显著 | 补充 bootstrap 置信区间和配对检验 | Results 图 2、图 3；Methods "Statistical analysis" 段 |

---

## 14 学到什么

> 以下为面向「蛋白质-DNA 互作（TF-DNA 结合机制）× AI/物理模拟」课题的可迁移知识。

### 概念性迁移

1. **化学接地表示优于离散符号**：将氨基酸从 one-hot 符号改为化学指纹（官能团、原子连接性、亚结构），使模型能泛化到"化学相似但序列不同"的残基。对 TF-DNA：DNA 碱基同样可编码为化学描述符（氢键供体/受体模式、静电势、疏水性、major/minor groove 几何特征），而非仅 A/C/G/T 四类符号。这可能提升对非经典结合位点（如甲基化 CpG、氧化损伤碱基）的泛化。

2. **"先聚类、后分类"的两阶段训练**：监督对比预训练先按结合类别组织潜在空间，再冻结编码器微调分类头。对 TF-DNA 结合预测中正负样本极度不平衡（全基因组扫描中结合位点占比极低）的场景，这种策略可能比直接端到端训练更鲁棒。

3. **可学习核 + 滑动窗口的互作建模**：用 MHC 伪序列生成可学习核，与肽段窗口逐元素乘，显式建模"口袋残基-配体残基"的化学互补。对 TF-DNA：可类比为"TF 结合域残基 vs DNA 碱基"的成对化学互补打分，而非仅序列 motif 匹配。

4. **多层级可解释性**：注意力权重定位残基位置，积分梯度归因定位化学基团。对 TF-DNA：可同时输出"哪些 DNA 位置"和"哪些化学特征（氢键、疏水、静电）"驱动结合，为机制研究提供假设。

### 方法性迁移

5. **指纹拼接策略**：多种互补指纹（MACCS 的官能团 + ECFP 的局部环境 + RDKit 的连通性）拼接，比单一描述符更全面。对 TF-DNA：可组合 DNA 的几何描述符（helical twist、roll、slide）、静电描述符（PO₄ 电荷分布）和氢键描述符。

6. **瓶颈 Transformer 的架构选择**：先降维再自注意力，降低计算成本同时保留长程依赖。对 TF-DNA 结合位点通常较短（6–20 bp），但 ChIP-seq 数据中侧翼序列效应可能长达数百 bp，瓶颈设计可处理多尺度上下文。

7. **伪序列策略**：用 34 个接触残基代表整个 MHC 分子，大幅降低输入维度。对 TF-DNA：可用 TF 结合域中与 DNA 直接接触的残基子集（如锌指基序的 α-helix 残基）代表整个 TF，而非全蛋白序列。

### 实验设计迁移

8. **类别不平衡压力测试**：系统变化负正比（1:1 至 200:1）评估模型鲁棒性。对 TF-DNA 全基因组预测，这是必要的评测维度。

9. **多层级验证策略**：从计算基准 → 独立实验数据（MS/MS）→ 免疫原性数据（TESLA）的递进验证。对 TF-DNA：可从 ChIP-seq 基准 → 独立 ChIP-exo/SELEX 数据 → 功能验证（报告基因/突变体）递进。

10. **归因分析与已知基序对比**：将模型归因与已知锚定残基/基序对比，作为可解释性的验证。对 TF-DNA：可将注意力/梯度归因与已知 TF 结合 motif（如 JASPAR）和晶体结构接触残基对比。

---

## 15 与已有知识连接

- **Nielsen 等（13, 14）的 MHC 伪序列定义**：本文的 34 残基伪序列直接沿用 Nielsen 等的结构定义。该思路可类比 TF-DNA 领域中的"接触残基定义"（如 PDB 结构中 4.0 Å 内残基），已有工作如 DeepBind、DeepSEA 用全序列编码，而"接触残基子集"策略可降低维度并提升可解释性。

- **Khosla 等（24）的监督对比学习**：本文的对比预训练直接引用此框架。在 TF-DNA 领域，对比学习已被用于增强表示（如 Enformer 的预训练策略），但"按结合类别做监督对比"而非自监督对比，是一个值得尝试的变体。

- **Lee 和 Min（9）、Adamczyk 等（10）的指纹编码氨基酸**：本文直接建立在此工作之上。TF-DNA 领域目前主流仍为 one-hot 或 BLOSUM 编码，化学指纹编码 DNA 碱基是未充分探索的方向。

- **ConBoTNet（11）的对比学习 + 瓶颈 Transformer**：本文的架构与 ConBoTNet 高度相关，但扩展到了 MHC-I 和指纹输入。TF-DNA 领域已有类似瓶颈 Transformer 架构（如 Enformer 的卷积-Transformer 混合），但未与化学指纹结合。

- **NetMHCpan（1）、MHCflurry（2）、BigMHC（3）等基线**：本文的评测基线。TF-DNA 领域的对应基线为 DeepBind、DeepSEA、FactorNet、BPNet 等。

- **TESLA 数据集（23）**：本文用于免疫原性验证。TF-DNA 领域无直接对应，但可类比 ENCODE 的 ChIP-seq 和 CRISPR 扰动数据作为功能验证。

- **与物理模拟的连接 [Analysis]**：本文的"化学指纹 + 互作矩阵"在概念上接近分子力学中的"接触势"（contact potential），但缺乏三维结构信息。TF-DNA 领域可考虑将 MD 模拟或 docking 得到的接触几何特征（如氢键距离、角度）作为额外通道输入深度学习模型，弥合"序列化学"与"结构物理"的鸿沟。

---

## 16 研究想法

> 以下为面向「蛋白质-DNA 互作（TF-DNA 结合机制）× AI/物理模拟」的研究候选。

### 候选 1：ChemDNA-TF——化学指纹编码的 TF-DNA 结合预测器
- **名称**：ChemDNA-TF: Chemically Grounded Nucleotide Encoding for TF-DNA Binding Prediction
- **来源局限/观察**：现有 TF-DNA 预测器（DeepBind、BPNet）用 one-hot 编码 DNA 碱基，丢失碱基的化学性质（氢键供体/受体模式、疏水性、静电势），导致对非经典结合位点（甲基化、氧化损伤）泛化差。本文证明化学指纹编码氨基酸可提升肽-MHC 预测的泛化性。
- **核心假设**：将 DNA 碱基编码为化学指纹（如碱基的氢键模式、π 电子密度、major/minor groove 化学特征），可提升 TF-DNA 结合预测的分布外泛化。
- **初步方法**：为 A/T/C/G 及修饰碱基（5mC、5hmC、8-oxoG）计算 RDKit 或自建化学描述符；用本文的"指纹 + 位置编码 + 滑动窗口互作"框架替换 one-hot 输入；在 ENCODE ChIP-seq 和甲基化敏感数据集上评测。
- **验证方式**：对比 one-hot vs 化学指纹编码在标准基准（如 ENCODE-DREAM）和修饰碱基数据集上的 AUC；用积分梯度检查模型是否关注已知的化学决定因素。
- **创新状态**：unverified（化学指纹编码 DNA 碱基在 TF-DNA 领域未见先例）

### 候选 2：TF 接触残基核 + DNA 滑动窗口的互作建模
- **名称**：Contact-Kernel TF: Modeling TF-DNA Binding via Learnable Contact Residue Kernels
- **来源局限/观察**：本文用 MHC 伪序列生成可学习核，与肽段窗口逐元素乘，显式建模口袋-配体互补。TF-DNA 领域多数模型将 TF 和 DNA 独立编码后拼接，未显式建模"TF 接触残基 vs DNA 碱基"的成对互作。
- **核心假设**：用 TF 结合域中已知接触 DNA 的残基（来自 PDB 结构）生成可学习核，与 DNA 滑动窗口做逐元素互作，可提升结合预测精度并提供结构可解释性。
- **初步方法**：从 PDB 提取 TF-DNA 复合物中 4.0 Å 内接触残基；用这些残基的化学指纹生成核；对 DNA 序列做滑动窗口互作；在 JASPAR motif 和 ChIP-seq 数据上评测。
- **验证方式**：对比"接触残基核" vs "全 TF 序列编码"的 AUC；检查学习到的核是否对应已知的 DNA 接触偏好。
- **创新状态**：unverified（结构引导的互作核在 TF-DNA 深度学习中有部分先例如 PDB 引导的注意力，但"化学指纹核 + 滑动窗口"组合未见）

### 候选 3：对比预训练 + 平衡训练提升 TF 结合位点不平衡鲁棒性
- **名称**：Contrastive Pretraining for Imbalanced TF-DNA Binding Prediction
- **来源局限/观察**：本文证明监督对比预训练 + 平衡训练在 200:1 负正比下保持 AUC > 0.9，而竞争方法崩溃。TF 结合位点全基因组扫描中负正比可达 10⁴:1 以上，不平衡鲁棒性至关重要。
- **核心假设**：监督对比预训练（按结合/非结合聚类）可提升 TF-DNA 预测器在极端不平衡下的判别力。
- **初步方法**：在 ChIP-seq 数据上先做对比预训练（正样本 = 同一 TF 的结合位点，负样本 = 非结合位点），再冻结编码器微调分类头；在 10:1 至 10⁴:1 负正比下评测。
- **验证方式**：对比有无对比预训练的 AUC-PR 和 PPV；检查潜在空间的聚类质量。
- **创新状态**：partially checked（对比学习已用于 TF-DNA 表示学习，但"监督对比 + 不平衡鲁棒性"的系统评测未见）

### 候选 4：多层级可解释性——从序列 motif 到化学基团归因
- **名称**：ChemAttrib: Multi-Level Attribution for TF-DNA Binding Mechanisms
- **来源局限/观察**：本文用注意力 + 积分梯度同时定位残基位置和化学官能团。TF-DNA 领域多数可解释性工作仅定位 motif 位置，未深入到化学基团层面。
- **核心假设**：积分梯度在化学指纹维度上的归因可揭示 TF-DNA 结合的化学决定因素（如特定氢键供体、疏水基团），与 MD 模拟的接触能一致。
- **初步方法**：在训练好的 ChemDNA-TF 上对指纹维度做积分梯度归因；将归因的化学基团与已知 TF-DNA 晶体结构的接触残基对比；用 MD 模拟（如 GROMACS）计算结合自由能分解验证。
- **验证方式**：归因的化学基团是否与 MD 接触能热点一致；是否能在未见过的 TF 上泛化。
- **创新状态**：unverified（化学指纹维度的归因在 TF-DNA 领域未见先例）

### 候选 5：TF-DNA 结合预测与 MD 模拟的混合框架
- **名称**：Hybrid Chem-MD: Integrating Chemical Fingerprints with Molecular Dynamics for TF-DNA Binding
- **来源局限/观察**：本文的指纹表示是静态的，不包含构象柔性。作者承认此局限。TF-DNA 结合涉及显著构象变化（induced fit），静态指纹可能遗漏关键结合自由能贡献。
- **核心假设**：将 MD 模拟得到的构象系综特征（如接触残基的构象熵、氢键占有率）作为补充输入，可提升静态指纹模型的精度。
- **初步方法**：对代表性 TF-DNA 复合物做短 MD 模拟（如 100 ns），提取接触残基的构象特征；将这些特征作为辅助输入与化学指纹拼接；在有限数据集上评测增量贡献。
- **验证方式**：对比有无 MD 特征的 AUC 增量；检查 MD 特征是否在稀有 TF 上提供最大增益。
- **创新状态**：unverified（MD 特征与化学指纹的混合在 TF-DNA 领域未见先例，但 MD 特征增强深度学习已有部分工作如 AlphaFold 的蒸馏）

### 候选 6：跨物种/跨家族泛化的"化学相似性"迁移
- **名称**：ChemTransfer: Cross-Family TF-DNA Binding Prediction via Chemical Similarity
- **来源局限/观察**：本文的指纹编码使模型能泛化到化学相似但序列不同的残基。TF 家族间（如锌指、bZIP、homeodomain）的 DNA 结合偏好差异巨大，但化学上可能共享相似的接触模式。
- **核心假设**：化学指纹编码可使 TF-DNA 模型在未见过的 TF 家族上实现零样本泛化，只要其 DNA 接触化学与训练家族相似。
- **初步方法**：在多个 TF 家族的 ChIP-seq 数据上训练 ChemDNA-TF；在留出家族上评测零样本泛化；分析哪些化学特征跨家族共享。
- **验证方式**：对比 one-hot 编码的跨家族泛化差距；检查化学指纹的共享维度。
- **创新状态**：unverified（跨家族零样本泛化在 TF-DNA 领域有部分先例如 ZeroBind，但化学指纹驱动的迁移未见）