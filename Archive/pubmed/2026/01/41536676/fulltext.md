# 心房颤动中免疫细胞与衰老相关生物标志物的鉴定及分子机制研究


## 目的
  探讨免疫细胞（immune cells, ICs）与衰老相关生物标志物在心房颤动（atrial fibrillation, AF）中的分子机制。


## 方法
  本研究通过加权基因共表达网络分析（WGCNA）在GSE2240数据集获得免疫细胞相关基因（immune cell-related genes, ICRGs）。随后，将ICRGs、衰老相关基因（senescence-related genes, SRGs）和通过AF组与窦性心律（sinus rhythm, SR）组差异表达分析得到的差异表达基因（differentially expressed genes, DEGs）取交集，筛选出候选基因。进一步利用最小绝对收缩与选择算子（LASSO）算法获得生物标志物并在GSE115571数据集中进行验证。接着，进行基因集富集分析（GSEA）、GeneMANIA网络构建、分子调控网络构建以及分子对接实验，以探讨AF中生物标志物的分子机制。8只87周龄、体质量632～656 g的Sprague-Dawley雄性大鼠随机分为AF组和SR组（n=4），制备AF大鼠模型，RT-qPCR检测大鼠心肌组织中肌球蛋白轻链激酶（myosin light chain kinase, MYLK）和胰岛素样生长因子结合蛋白2（insulin-like growth factor binding protein 2, IGFBP2）mRNA的表达水平。


## 结果
  本研究识别出2个生物标志物MYLK和IGFBP2。GSEA分析显示，MYLK显著富集于嗅觉传导通路，IGFBP2显著富集于细胞外基质-受体相互作用通路。GeneMANIA网络显示，这些生物标志物与20个基因在功能上具有相似性。此外，MYLK受28个转录因子（TFs）和41个miRNA调控，而IGFBP2受63个TFs和包括TAF1、MIRT020526在内的4个miRNA调控。药物预测表明，仅MYLK与3种药物存在潜在相互作用，其中，与MYLK结合能力最强的药物为tozasertib，其结合能为－7.8 kcal/mol。RT-qPCR结果显示，AF组大鼠心肌组织中IGFBP2 mRNA表达上调（P<0.05），MYLK mRNA表达下调（P<0.05）。


## 结论
  本研究鉴定出2种与AF相关的生物标志物MYLK和IGFBP2，并揭示了其潜在的分子机制，为AF的研究提供了新的理论依据。


## 资料与方法

### 数据库和实验动物
  本研究所使用的数据均来源于GEO数据库（https://www.ncbi.nlm.nih.gov/geo/）。其中，GSE2240数据集被用作训练集，包含20例AF心房组织样本（AF组）和10例窦性心律（sinus rhythm, SR）心房组织样本（SR组）[9]。GSE115574数据集作为验证集，包含28例AF心房组织样本和31例SR心房组织样本[10]。两个数据集的测序平台均为GPL97。

  此外，本研究共采用541个衰老相关基因（senescence-related genes, SRGs）进行分析。其中，279个SRGs来源于CellAge数据库（https://genomics.senescence.info/cells/），另有262个SRGs从相关文献中整理获得[11]。

  根据“3R”原则，动物使用数量应最小化，本研究在每组3只大鼠的基础上增加1只大鼠。本研究使用8只Sprague-Dawley雄性大鼠（北京华阜康生物科技股份有限公司），87周龄，体质量632～656 g，动物生产许可证号SYXK（津）2021-0012。采用随机数字表法进行完全随机化分组，AF组4只，SR组4只，由不参与后续实验的第三方人员对动物和样本进行随机编号，隐藏其分组信息。大鼠被饲养在无特定病原菌（specific-pathogen-free, SPF）、12 h/12 h明暗交替环境下，其间给予充足水和食物。排除标准：AF造模失败或存在间发性疾病。实验动物均遵循天津医科大学实验动物伦理委员会相关规定（编号：TMUaMEC2021012）。


### 免疫浸润分析
  在训练集GSE2240数据集中，AF组与SR组中ICs的丰度差异采用R软件包immunedeconv (v2.1.0) 中的abis方法进行评估[12]，采用Wilcoxon秩和检验比较GSE2240数据集中AF组与SR组样本中各类IC的比例差异，并对所有免疫细胞类型进行Benjamini-Hochberg FDR校正，显著性阈值设定为FDR<0.05，并剔除低置信度样本，将其作为差异 ICs用于后续分析。


### 加权基因共表达网络分析（WGCNA）
  为了筛选与差异ICs相关的模块基因，本研究采用R软件包WGCNA (v1.18.0)进行分析[13]。首先，利用WGCNA包中的goodSamplesGenes函数对训练集GSE2240数据进行质量控制，检测是否存在缺失值。随后，使用hclust函数对样本进行聚类分析，以识别并剔除离群样本，从而确保后续分析的准确性和可靠性。随后使用pickSoftThreshold函数计算不同软阈值的平均连接数和无尺度拟合指数（R2），同时对备选软阈值进行检验。一般认为R2>0.8满足无尺度条件。为了构建与差异ICs相关的模块基因，本研究基于基因之间的相似性，采用dynamic Tree Cut函数的动态剪枝算法对共表达模块进行划分，并通过聚类分析识别高度相似的模块。随后，设定模块中最小基因数为50，并使用0.25作为高度剪切临界值，以合并相似模块。接下来，计算模块内基因之间的相关性，并基于相关性进行聚类分析，使用hclust函数绘制树形聚类图。随后，利用Psych (v2.4.12)包中的cor函数进行Spearman相关性分析，计算模块与差异ICs之间的相关性，设定阈值为FDR<0.05。最终，选择与差异ICs相关性最强的模块，定义为关键模块。


### 差异表达基因的鉴定
  在训练集GSE2240中，采用R软件包limma (v3.54.0)进行差异表达基因（differentially expressed genes, DEGs）的筛选[14]。筛选标准设定为|log2FC|>0.5且adj.P<0.05，符合此标准的基因被定义为DEGs，用于后续分析。


### 富集分析
  采用R软件包clusterprofiler (v4.2.2)对候选基因进行基因本体（GO）、京都基因和基因组百科全书（KEGG）富集分析以及基因集富集分析（GSEA）[15]。进行GSEA分析前使用R软件包psych通过cor函数对每个生物标志物与其余基因进行Spearman相关性分析，获得相关性系数。根据相关系数由大到小将生物标志物进行排序后，从MSigDB分子特征数据库（https://www.gsea-msigdb.org/gsea/msigdb）中获取参考基因集“c2.cp.kegg.v7.0.symbols.gmt”进行分析。


### 互作网络构建
  首先，将候选基因导入R软件包STRINGdb (v3.20)以构建蛋白互作网络（PPI）[16]，随后，利用R软件包igraph (v2.1.4.9003)对PPI网络进行可视化分析。接着，将筛选出的生物标志物导入GeneMANIA数据库（http://genemania.org），预测与每个生物标志物相关的基因，并构建生物标志物的共表达网络。此外，使用JASPAR数据库（http://jaspar.genereg.net/）预测调控生物标志物的转录因子（TFs）。随后，利用miRTarBase数据库（https://mirtarbase.cuhk.edu.cn/）预测调控生物标志物的miRNA，并使用R软件包igraph进行可视化分析。此外，基于药物-基因互作数据库（DGIdb, https://dgidb.genome.wustl.edu/）进行检索，获得靶向生物标志物的潜在治疗药物并使用Cytoscape软件（v3.8.2）构建生物标志物-药物相互作用网络[17]。


### 机器学习
  本研究采用最小绝对收缩和选择算子（LASSO）对GSE2240数据集中AF组和SR组样本的候选基因进行筛选。首先，使用R软件包glmnet (v4.1)对候选基因进行LASSO分析，并将筛选出的基因在验证集GSE115574中检测其表达水平。


### 分子对接
  首先，从PDB数据库（https://www.rcsb.org/）下载生物标志物的活性成分结构，并将 PDB格式转换为PDBQT格式。随后，从PubChem数据库（https://pubchem.ncbi.nlm.nih.gov/）下载药物小分子的3D结构并保存为mol3格式文件。随后，使用AutoDockTools软件对生物标志物和药物小分子进行分子对接，探究它们之间的结合模式和分子相互作用。结合自由能以kcal/mol为单位，负值表示结合力更强。最后，使用PyMOL软件对对接结果进行可视化分析。


### AF模型的建立
  用浓度为3%的三溴乙醇（由叔戊醇及去离子水按比例配制）以10 mL/kg的标准通过腹腔注射对大鼠进行麻醉，将其头部及四肢固定于小动物操作台上，使用EPR导管延长电缆连接电生理刺激器/放大器（STG3008-FA）和大鼠电生理导管EPR802，将红色、绿色、黑色体表针电极连接对应的生物电放大器bio amp输入端口（正极、正极、负极），将其分别插入左下肢、右下肢和右上肢皮下，分析心房电生理参数及体表ECG各项参数（Lab Chart Pro8.0）并记录体表心电图。

  对大鼠进行颈部皮肤暴露后，执行标准消毒流程，并通过竖切口分离右侧颈动脉，使用缝合线对颈总静脉向上分叉处结扎。使用1 mm注射器针头在右锁骨上方约5 mm处进行穿刺，并接入多极电极，沿动脉推送至小鼠右心房。AF组采用burst刺激（初始周期40 ms，持续2 s；每周期递减2 ms至20 ms，重复5次，间隔1 min）诱发AF，以持续超过1 s的快速不规则房性心律伴RR间期不规律为AF模型成功标准；SR组进行相同的手术暴露和电极放置，但不诱导房颤。测量结束后拔下针电极和EPR802电生理导管，清洁EPR802电生理导管（肝素氯化钠溶液浸泡），棉球按压创口止血。


### 样本制备
  在麻醉状态下，沿剑突剪开大鼠胸腔，切断肋骨并掀开，暴露心脏后剥离心包膜。轻提心脏，剪开下腔静脉放血，用1 mL针头PBS从心尖灌洗2次，夹闭主动脉后离断血管取出心脏。PBS漂洗去残血，剔除周围组织，吸水纸吸干后称质量，分离心房心室，标记并冻存于－80 ℃。


### RT-qPCR
  取50 mg冻存组织，加1 mL TRIzol试剂（Ambion, 15596-018CN），匀浆后冰上静置10 min。加入300 μL氯仿，剧烈震荡30 s，室温静置10 min，4 ℃、12000×g离心15 min。吸取上清，加入等体积异丙醇，混匀后静置10 min，4 ℃、12000×g离心10 min。弃上清，用1 mL 75%乙醇洗涤沉淀（4 ℃、7500×g离心5 min，重复两次）。干燥后，用20～50 μL无RNase水溶解RNA，静置15 min后检测浓度及纯度，用于逆转录。

  使用Hifair® Ⅲ逆转录试剂盒，按如下体系配制反应液（20 μL）：1 μL 5× Reaction Buffer；4 μL Primer；1 μL SweScript RT Ⅰ Enzyme Mix；2 μL Total RNA；补Nuclease-Free Water至20 μL。短暂离心后使用S1000TM Thermal Cycler普通PCR仪（BIO-RAD）进行逆转录（25 ℃ 5 min，50 ℃ 15 min，85 ℃ 5 s，4 ℃ hold）。

  将上述逆转录产物cDNA加ddH2O（RNase/DNase free）稀释5～20倍。加入3 μL cDNA、5 μL 2× Universal Blue SYBR Green qPCR Master Mix、1 μL Forward primer (10 µmol/L)、1 μL Reverse primer (10 µmol/L)，短暂离心混匀后，使用CFX Connect实时定量荧光PCR仪（BIO-RAD, XLFZ006）进行循环反应（40个），并采集数据（仪器自动生成扩增曲线、熔解曲线，读取Ct值）。PCR循环参数：预变性 95 ℃ 1 min，变性 95 ℃ 20 s，退火 55 ℃ 20 s，延伸72 ℃ 30 s。相关引物序列如下：肌球蛋白轻链激酶（myosin light chain kinase, MYLK）F， 5'-GGGACGTGAAACTGTTTGCC-3'，R，5'-GGCTCCTTCTTTGACGCAGAG-3'；胰岛素样生长因子结合蛋白2（insulin-like growth factor binding protein 2, IGFBP2）F， 5'-TTCCTTCTGGCGTTGGGAGA-3'，R，5'-TGGTTCCGTCCACATGGTTC-3'；内参GAPDH F， 5'-GGCCGGAGACGAATGGAAATTA-3'，R，5'-CCAAATCCGTTCACACCGAC-3'。引物序列合成均由擎科生物科技有限公司提供。所有RT-PCR结果均进行对数化处理。


### 统计学方法
  采用Graphpad Prism 10分析研究数据，以\begin{document}$ \bar{x} \pm s $\end{document}表示计量资料。采用非参数检验比较两组间基因表达差异，多重检验以FDR≤0.05为差异有统计学意义。


## 结果

### 免疫浸润分析
  在AF组中NK细胞和CD4+记忆T细胞相较SR组有更高的浸润水平，而CD8+记忆T细胞、CD4+初始T细胞、VD2 T细胞以及non-conventional单核细胞则在SR组有更高的丰度，见图1。


### WGCNA筛选差异ICs相关模块基因
  本研究经过质量控制后，未发现离群样本。随后，选择软阈值为19（R2=0.85）来构建模块基因。最终筛选出41个与差异ICs显著相关的模块，共包含7475个免疫细胞相关基因（immune cell-related genes, ICRGs），见网络资源附件附图1A。其中，深灰色模块与NK细胞的相关性最高（－0.57），紫罗兰色模块与CD8+记忆T细胞的相关性最高（0.56），深红色模块与CD4+初始T细胞的相关性最高（－0.77），而深红色模块和深褐色模块与CD4+记忆T细胞的相关性最高（0.72），紫罗兰色模块与VD2 T细胞的相关性最高（0.72），绿松石色模块与非经典单核细胞的相关性最高（－0.88），见网络资源附件附图1B。


### 候选基因的筛选及其功能
  本研究在GSE2240数据集中检测到AF组相对于SR组的200个DEGs，包括50个上调基因和150个下调基因。随后将这些DEGs与WGCNA分析得到的ICRGs以及SRGs取交集得到13个候选基因，见图2A。GO富集分析显示这些基因与对激素和化学刺激的反应相关，见图2B。PPI网络则表明这些基因在蛋白水平上存在大量的相互作用，可能共同参与上述生物学功能，见图2C。


### 机器学习进一步筛选生物标志物
  将13个候选基因进行LASSO回归，λ值取0.212，得到6个基因作为候选生物标志物，见网络资源附件附图2。该6个生物标志物在训练集GSE2240中的AF组和SR组中的表达水平差异均有统计学意义，图3A。而在验证集GSE115574中，只有两个生物标志物差异有统计学意义，其中IGFBP2在AF组中显著上调，MYLK在AF组中显著下调，与训练集中的趋势一致。RT-qPCR也在动物组织样本中展示了相同的发现，见图3B，进一步验证了生物信息学分析的结果。分别将IGFBP2和MYLK及其相关基因进行GSEA富集分析，发现MYLK主要与神经兴奋性的配受体交互以及嗅觉传导通路相关，而IGFBP2则与细胞粘连以及细胞外基质通路相关，见网络资源附件附图3。


### MYLK和IGFBP2的调控网络
  为了进一步探索两个生物标志物的作用机制，本研究将其导入GeneMANIA数据库预测与每一个生物标志物相关的基因并构建共表达网络。结果显示，MYLK与MYO18A、CTTN以及CAMK2G等基因共表达，见附图2A；IGFBP2则与IGF1和IGF2等基因共表达，见附图2B。通过JASPAR数据库和miRTarBase数据库，本研究分析了生物标志物的调控网络，结果显示，MYLK受28个TFs和41个miRNAs调控，见附图3A；而IGFBP2受63个TFs和4个miRNAs调控，见附图3B。


### 药物预测
  通过在DGIdb数据库进行检索，本研究找到了3个MYLK特异性的药物抑制剂RKI-1447、calmodulin以及tozasertib。然而并未发现IGFBP2特异性抑制剂。随后为了研究预测的药物与生物标志物的结合亲和力和相互作用模式，本研究对MYLK与3种药物进行分子对接：MYLK与RKI-1447结合的自由能为－7.4 kcal/mol，与calmodulin结合的自由能为－5.5 kcal/mol，与tozasertib结合的自由能为－7.8 kcal/mol。MYLK与RKI-1447、calmodulin和tozasertib的对接模式见图4。


## 讨论
  本研究系统地探讨了ICs与衰老在AF中的分子机制，并鉴定了MYLK和IGFBP2作为关键生物标志物。MYLK编码的肌球蛋白轻链激酶在细胞收缩、细胞骨架重塑以及血管通透性调节中发挥重要作用，通过钙信号通路直接调控钙瞬变和离子通道，而Rho/ROCK通路则通过细胞骨架重组和离子通道修饰间接影响电生理特性。两者共同导致动作电位时程缩短和钙处理异常，成为心律失常的结构和功能基础[18]。在心血管系统中，MYLK参与平滑肌收缩和心肌细胞的机械信号转导，已有研究表明其异常表达可能与心律失常相关[19]。IGFBP2是胰岛素样生长因子（IGFs）的重要调节因子，能通过高亲和力结合IGF-1/2调控其生物利用度及下游PI3K/AKT和MAPK信号通路活性，进而影响细胞增殖、分化及存活。此外，IGFBP2的肝素结合域和RGD基序使其能够直接与细胞外基质成分或整合素相互作用，独立于IGFs信号促进细胞迁移与组织重塑，在病理状态下，IGFBP2的异常表达可通过促血管生成或激活MMPs加剧细胞外基质降解[20]。IGFBP2 在多种心血管疾病和纤维化相关疾病中均显示出重要的调节作用，提示其可能在AF发生发展中发挥关键作用[21]。本研究通过综合WGCNA、LASSO、GSEA、GeneMANIA网络分析、分子调控网络构建以及分子对接实验，揭示了这两个基因MYLK和IGFBP2在AF发生和发展中的潜在作用。

  功能分析表明IGFBP2显著富集于细胞外基质-受体相互作用通路。已有研究指出，细胞外基质重塑在心房纤维化及AF的发生过程中起着至关重要的作用[22]。IGFBP2作为胰岛素样生长因子结合蛋白，可能通过影响细胞外基质的组成和功能，促进AF的结构性重塑。此外，MYLK的作用主要涉及细胞收缩和信号转导，其在心脏电活动中的作用仍需进一步研究[23]。

  进一步的分子调控网络分析显示，MYLK受28个TFs和41个miRNAs调控，而IGFBP2受63个TFs和4个miRNAs调控。提示转录和转录后调控可能在AF的发生和发展中发挥关键作用。此外，药物预测分析表明，MYLK可能是AF治疗的潜在药物靶点，尤其是tozasertib与MYLK具有较强结合能力（－7.8 kcal/mol）。tozasertib是一种Aurora激酶抑制剂，最初用于抑制肿瘤细胞的增殖[24]，但研究表明其在调节心血管信号通路方面可能具有潜在作用[24]。Aurora激酶在细胞周期调控、微管动力学和心肌细胞增殖中起关键作用[25]，而tozasertib可能通过影响MYLK介导的信号转导，对心房肌细胞的收缩功能产生影响[26]。尽管tozasertib在AF相关研究中的具体作用尚未被深入探讨，但本研究的分子对接结果提示其可能作为AF相关信号通路的调节剂，值得进一步实验验证。这些发现为AF的个性化治疗提供了新的思路。体外实验进一步验证了MYLK和IGFBP2在AF心肌组织和对照心肌组织中的表达差异，与生物信息学分析结果一致。MYLK和IGFBP2在AF的发生发展中可能通过复杂的转录及转录后调控网络发挥协同作用，MYLK活性受到多层次的动态调节，可能影响心房肌细胞的收缩功能；而IGFBP2更倾向于转录水平的调控，可能参与细胞增殖或代谢通路的改变，联合来看，MYLK可能通过肌动蛋白-肌球蛋白收缩通路直接影响电机械耦合，而IGFBP2可能通过生长因子信号调控心肌重构，二者的协同失调共同促进了AF的病理进程，为靶向干预提供了新的联合策略。

  尽管本研究通过多组学分析鉴定了MYLK和IGFBP2作为AF的关键生物标志物，并揭示了它们在细胞收缩、细胞外基质重塑及转录调控中的作用，但仍存在一定局限性：①AF的分子机制可能受遗传背景、环境因素和区域性疾病管理差异的影响，而本研究基于国际公开数据库分析，尽管通过独立数据集GSE115574进行了验证，但研究结果在推广至中国人群时需要进一步验证；②研究主要依赖生物信息学分析，临床样本验证不足，未来需要更多的体内和体外实验来深入解析MYLK和IGFBP2在AF中的具体作用机制；③此外，虽然分子对接分析预测了MYLK与tozasertib的潜在相互作用，但其实际药理作用仍需进一步实验验证。

  综上所述，本研究通过综合多种分析方法，识别并验证了MYLK和IGFBP2作为AF的关键生物标志物，并揭示了它们在AF发生中的潜在机制。这些发现不仅为AF的发病机制提供了新的见解，还为其早期诊断和靶向治疗提供了新的潜在靶点。未来研究应进一步探索MYLK和IGFBP2的具体作用机制，并评估其作为AF治疗靶点的临床应用价值。

  *　　　　*　　　　*

  作者贡献声明　黄薇负责数据审编、正式分析、调查研究、研究方法、软件、验证、可视化和初稿写作，刘恩照负责论文构思、经费获取、研究项目管理、提供资源、监督指导和审读与编辑写作，富华颖负责经费获取、研究项目管理和提供资源。所有作者已经同意将文章提交给本刊，且对将要发表的版本进行最终定稿，并同意对工作的所有方面负责。

  Author Contribution　HUANG Wei is responsible for data curation, formal analysis, investigation, methodology, software, validation, visualization, and writing--original draft. LIU Enzhao is responsible for conceptualization, funding acquisition, project administration, resources, supervision, and writing--review and editing. FU Huaying is responsible for funding acquisition, project administration, and resources. All authors consented to the submission of the article to the Journal. All authors approved the final version to be published and agreed to take responsibility for all aspects of the work.

  利益冲突　所有作者均声明不存在利益冲突

  Declaration of Conflicting Interests　All authors declare no competing interests.