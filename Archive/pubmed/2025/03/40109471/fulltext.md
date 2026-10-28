# 6-羟基染料木素治疗高原缺氧小鼠肺损伤的作用机制


## 目的
  探讨6-羟基染料木素（6-hydroxygenistein, 6-OHG）治疗高原缺氧诱导肺损伤的作用机制。


## 方法
  从Swiss Target Prediction、SuperPred、GeneCards和OMIM等数据库中筛选获得6-OHG和高原缺氧肺损伤的交集靶点。运用STRING数据库和Cytoscape软件对药物与疾病的交集靶点构建蛋白互作网络，并将度值大于中位数的作为关键靶点；使用DAVID数据库对关键靶点进行GO富集和KEGG富集分析获得相关信号通路；用Maestro 13.7软件进行分子对接验证。采用大型低压低氧舱建立小鼠高原肺损伤模型，将42只雄性Balb/c小鼠随机分为3组，每组14只：正常对照组（当地海拔1400 m，一次性腹腔注射生理盐水）、模型组（一次性腹腔注射生理盐水）、6-OHG组（一次性腹腔注射100 mg/kg 6-OHG）。给药1 h后，模型组和6-OHG组小鼠置于大型低压低氧模拟动物实验舱中，然后以10 m/s上升至海拔8000 m，并维持24 h，再降至海拔3500 m。处死3组小鼠，取肺组织，测定肺含水量，HE染色观察病理学变化，测定MDA（malondialdehyde）、H2O2、T-SOD（total superoxide dismutase）和GSH（glutathione）的水平，Western blot检测p-PI3K/PI3K、p-AKT/AKT、缺氧诱导因子1α（HIF-1α）和VEGF（vascular endothelial growth factor）蛋白表达。


## 结果
  筛选出丝氨酸/苏氨酸蛋白激酶1（AKT1）、HIF-1α、表皮生长因子受体（EGFR）、基质金属蛋白酶9（MMP9）、过氧化物酶增殖物激活受体A（PPARA）等关键靶点，GO富集和KEGG富集分析显示6-OHG治疗高原缺氧肺损伤的靶点主要参与PI3K/AKT、HIF-1α/VEGF、肿瘤坏死因子（TNF）等信号通路。动物实验结果显示，与模型组相比，6-OHG可以显著改善高原缺氧诱导的肺组织病理损伤，且MDA、H2O2、GSH和T-SOD水平与模型组相比，差异有统计学意义（P<0.01）。Western blot实验结果显示，6-OHG组肺组织p-PI3K/PI3K、p-AKT/AKT、HIF-1α和VEGF较模型组相比，差异有统计学意义（P<0.01）。分子对接结果表明6-OHG可与PI3K、AKT、HIF-1α和VEGF形成稳定的结合。


## 结论
  6-OHG可能通过激活PI3K/AKT信号通路和抑制HIF/VEGF信号通路改善高原缺氧所致的小鼠肺组织损伤。


## 材料与方法

### 网络药理学分析

#### 6-OHG化学成分的筛选与收集
  在ChemoDraw 20.0软件中绘制6-OHG结构式并于Chem3D 20.0软件中进行立场最小化，优化构象后获得6-OHG结构式。将所获得的结构式导入Swiss Target Prediction、PharmMapper、SEA、SuperPred数据库中获取6-OHG药物靶点；随后将所得靶点通过UniProt数据库将蛋白名转换为基因名，去除重复项后得到6-OHG潜在靶点。


#### 疾病靶点获取
  在Genecard和OMIM数据库中以“high altitude lung injury”“hypobaric hypoxia lung injury”“high altitude lung damage”“hypobaric hypoxia lung damage”为检索词获得疾病靶点，删除重复靶点后，获得高原肺损伤疾病靶点。


#### 交集靶点的获取
  将药物靶点以及疾病靶点导入FunRich3.1.3软件中获得交集靶点。


#### 蛋白互作网络的构建及关键靶点的获取
  将获得的交集靶点导入STRING平台中，设置限定物种为“homo sapiens”，随后将所得数据导入Cytoscape_v3.7.1将这些靶标映射到人类蛋白质-蛋白质相互作用网络，节点大小表示节点的度数，节点越大反映度值越高。同时，节点颜色与其交互级别成正比。对软件计算得到的蛋白互作网络（PPI）信息，运用“Network Analyze”进行拓扑学分析，选取Degree值大于中位数的作为关键靶点。


#### 基因本体和京都基因与基因组百科全书富集分析
  使用DAVID数据库对6-OHG治疗高原肺损伤的关键靶点进行基因组百科全书富集分析（KEGG）和生物学过程（BP）、细胞组成（CC）和分子功能（MF）的基因本体论（GO）富集分析。所得数据取P<0.05，且FDR<0.05。其物种设置为“人”，得到GO富集分析相关数据以及KEGG富集分析相关数据。数据调整P<0.05，且FDR<0.05为其相关关键信号通路。其中，GO分为BP、MF和CC；KEGG主要用于分析与基因相关的生物功能和潜在作用途径。


#### 分子对接
  6-OHG结构式获取同“1.1.1”项。从 PDB 蛋白数据库中下载相关靶点蛋白，将其导入Maestro 13.7软件中进行去水、提取配体、生成对接盒子及保存，在运行Ligand Docking插件进行分子对接后，导入PyMOL进行可视化。一般认为结合能越低越稳定，得分也越高[8]。


### 动物实验验证

#### 实验动物
  SPF级雄性Balb/c小鼠18只，体质量18～22 g，周龄6～8周，购自空军军医大学（原第四军医大学），实验动物生产许可证号：SCXK（京）2019-0010，实验动物使用许可证号：SYXK（军）2014-0029。实验方案由中国人民解放军联勤保障部队第九四〇医院医学伦理委员会审核通过，伦理编号为：2023KYLL361。


#### 药物、试剂与仪器
  大型低压低氧动物实验舱（贵州雷航空军械公司，型号：DYC-3070型），组织研磨仪（上海净信实业发展有限公司，型号：Tissuelyser），全自动荧光酶标仪〔美谷分子仪器（上海）有限公司，型号：SpectraMax i3〕，BCA试剂盒（Solarbio公司，货号：PC0020），T-SOD（total superoxide dismutase）测试盒（南京建成生物工程研究所，货号：20220113）、MDA（malondialdehyde）测试盒（南京建成生物工程研究所，货号：20220114）、H2O2测试盒（南京建成生物工程研究所，货号：20220115）、GSH（glutathione）测试盒（南京建成生物工程研究所，货号：20220118），p-PI3K（phosphorylated phosphatidylinositol 3-kinase, Abcam，货号：ab278545）、PI3K（phosphatidylinositol 3-kinase, Abcam，货号：ab191606）、p-AKT（ phosphorylated protein kinase B, Abcam，货号：ab18785）、AKT（ protein kinase B, Abcam，货号：ab38449）、HIF-1α（hypoxia inducible factor-1α, Abcam，货号：ab179483）、VEGF（vascular endothelial growth factor, Abcam，货号：ab46154）。


#### 方法

##### 实验造模
  将42只雄性Balb/c小鼠随机分为3组，每组14只，分别为正常对照组(Control)、模型组（Model）、6-OHG组（6-OHG，100 mg/kg）。正常对照组与模型组按照0.2 mL/20 g小鼠体质量进行腹腔注射生理盐水，根据课题组前期研究[9]确定6-OHG组给予一次性腹腔注射100 mg/kg 6-OHG，给药1 h后，将正常对照组小鼠置于氧舱外（当地海拔1400 m）处，而模型组和6-OHG组小鼠置于大型低压低氧模拟动物实验舱中，然后以10 m/s的速度上升至海拔8000 m，并维持24 h。结束后，将氧舱内海拔高度降至3500 m，处死小鼠，取肺组织，用于后续实验。


##### 肺含水量测定
  每组取5只小鼠，取肺组织，生理盐水洗净后用无菌滤纸吸干水分，置于锡箔纸上称量得湿重。再将肺组织置恒温烘箱于60 ℃连续干燥72 h至恒重。肺含水量计算：含水量（%）=（湿重－干重）÷湿重×100%。


##### HE染色观察肺组织病理学变化
  每组取3只小鼠，取出肺组织后，用体积分数为4%多聚甲醛固定，脱水包埋在石蜡中，沿纵轴切片4 μm薄片后，进行HE染色，光镜下观察肺部病理变化。


##### 生化指标检测
  随机选取各组小鼠6只，将肺组织分为两部分，一部分行生化指标检测，一部分行Western blot实验分析（见1.2.3.5小节）。

  取肺组织在冰上加入10倍量生理盐水，进行组织匀浆，随后2500 r/min离心10 min后取上清液，−80 ℃保存，按照试剂盒说明书测定MDA、H2O2、T-SOD和GSH的水平。


##### Western blot实验分析
  每组取6只小鼠，将肺组织于冰浴环境下加入适量RIPA（含蛋白酶抑制剂），匀浆，12000 r/min离心10 min取上清，BCA法测定蛋白浓度。向上清中按比例加入上样缓冲液后置于沸水浴中10 min后。取50 μg蛋白进行上样，使用SDS聚丙烯酰胺凝胶电泳分离，然后将蛋白电转至PVDF膜上，5%脱脂奶粉封闭2 h，4 ℃孵育一抗p-PI3K(1∶1000)、PI3K（1∶1000）、p-AKT（1∶1000）、AKT（1∶1000）、缺氧诱导因子1α（HIF-1α）（1∶1000）、血管内皮生长因子（VEGF）（1∶1000）过夜，TBST洗膜，再孵育二抗（1∶4000）2 h，洗膜，化学发光显色。使用ImageJ软件对所得蛋白图进行数据处理。


##### 统计学方法
  使用GraphPad Prism8 软件进行数据分析，计量数据均以\begin{document}$\bar x\pm s $\end{document}表示，多组间比较采One-way ANOVA分析，两两比较采用Dunnett's test。P<0.05为差异有统计学意义。


## 结果

### 网络药理学结果

#### 潜在靶点筛选
  从Swiss Target Prediction、PharmMapper、SEA、SuperPred数据库中分别获得靶点104、168、38、125个，汇总删除重复靶点后，共得到373个6-OHG潜在靶点。

  使用OMIM和Genecard数据库分别筛选出高原肺损伤相关靶点419和1305个，合并两者数据删除重复项后，最终得到1705个高原肺损伤相关靶点。

  将得到的6-OHG潜在靶点和高原肺损伤相关靶点进行交集，获取到61个交集靶点。见附图1及表1。所有附图请见网络资源附件。


#### PPI网络分析结果
  将61个6-OHG治疗高原肺损伤的潜在靶点输入String数据库以收集蛋白质相互作用的数据。结果如附图2所示，共涉及156个靶标和3539个边缘，主要包括白蛋白（ALB）、丝氨酸/苏氨酸蛋白激酶1（AKT1）、表皮生长因子受体（EGFR）、HIF-1α、基质金属蛋白酶9（MMP9）等。


#### GO富集和KEGG富集分析
  在GO富集分析（P<0.05）结果（附图3）中，共筛选出BP途径36个，如RNA聚合酶Ⅱ启动子pri-miRNA转录的正向调节（positive regulation of pri-miRNA transcription from RNA polymerase Ⅱ promoter）、基因表达的负调控（negative regulation of gene expression）、蛋白质磷酸化的正向调节（positive regulation of protein phosphorylation）等；CC途径12个，如大分子复合物（macromolecular complex）、细胞外区域（extracellular region）、细胞外泌体（extracellular exosome）等；MF途径11个，如酶结合（enzyme binding）、一氧化氮合酶调节活性（nitric-oxide synthase regulator activity）、类固醇结合（steroid binding）等。KEGG富集分析（P<0.05）（附图4）结果表明，其涉及HIF-1信号通路、VEGF信号通路、PI3K/AKT信号通路等信号通路，这表明6-OHG可能通过HIF/VEGF、PI3K/AKT信号通路治疗高原肺损伤。本文将从动物实验对其进行验证。


#### 分子对接结果
  如图1和表2所示，6-OHG可以与PI3K蛋白相互作用，作用于其残基脯氨酸（PRO）671、谷氨酸（GLU）172和天冬酰胺（ASN）167以及AKT蛋白中残基谷氨酸（GLU） 228相互作用；此外，6-OHG可以与HIF-1α蛋白残基ASN 321、GLU 202和TYR 276相互作用，并且与VEGF蛋白残基LEU 97、GLU 38和ASP 41相互作用。6-OHG与PI3K、AKT、HIF-1α和VEGF的对接分数分别为−5.486、−6.016、−6.266和−5.868，结合自由能分别为−41.79 kcal/mol、−37.24 kcal/mol、−29.04 kcal/mol和−24.60 kcal/mol。以上结果表明6-OHG可与PI3K、AKT、HIF-1α和VEGF形成稳定的结合。


### 动物实验结果

#### 6-OHG对高原缺氧肺组织含水量的影响
  通过肺含水量测定结果发现，正常对照组为78.06±1.68，模型组小鼠为81.43±0.36，6-OHG组为78.25±1.26。与模型组相比，含水量增加，差异有统计学意义（P<0.01）。与模型组相比，6-OHG给药治疗后含水量下降，差异有统计学意义（P<0.01）。


#### 6-OHG对高原缺氧肺组织病理学变化的影响
  HE染色结果（图2A）显示，正常对照组肺组织肺泡壁结构完整，细胞分布均匀，无明显炎症细胞浸润；与正常对照组相比，模型组肺泡结构紊乱，支气管腔狭窄且变形，细胞大小不一，可观察到炎症浸润；而6-OHG组给药后肺组织损伤有所减轻，炎性细胞减少。


#### 6-OHG对高原缺氧肺组织氧化应激水平的影响
  实验结果如图2B所示，与正常对照组比较，模型组小鼠肺组织中MDA和H2O2含量升高（P < 0.01），GSH和T-SOD水平降低（P<0.01），与模型组对比，其6-OHG组小鼠肺组织中MDA（P < 0.01）和H2O2（P<0.01）含量降低，GSH和T-SOD水平提高（P < 0.01）。


#### 6-OHG对高原缺氧损伤小鼠肺组织中HIF/VEGF信号通路的影响
  如图3，与正常对照组相比，模型组中小鼠肺组织HIF-1α和VEGF蛋白表达升高（P<0.05）；与模型组相比，6-OHG组中HIF和VEGF蛋白表达降低（P<0.01）。


#### 6-OHG对高原缺氧损伤小鼠肺组织中PI3K/AKT信号通路的影响
  如图3所示，模型组小鼠肺组织中p-PI3K/PI3K、p-AKT/AKT的比值均低于正常对照组（P<0.001，P<0.05）；与模型组对比，6-OHG组小鼠肺组织中p-PI3K/PI3K和p-AKT/AKT的比值均升高（P<0.01）。


## 讨论
  高海拔环境是最极端的环境之一，可诱发肺血管重塑和持续性肺动脉高压等肺部疾病的发生[10]，但是目前仍缺乏有效的防治手段。本研究首先运用网络药理学对6-OHG治疗高原肺损伤的作用和相关靶点进行了预测，再通过PPI分析、GO富集和KEGG富集分析出关键靶点和信号通路，最后通过动物实验对其结果进行验证，为6-OHG的开发利用奠定基础。

  高原缺氧可导致肺通气丧失，引起呼吸抑制、呼吸节律不齐和中枢性呼吸衰竭等，从而对肺部造成一定的损伤[11]。李从艺等[12]研究表明高原缺氧后，其大鼠出现支气管壁以及肺间质充血和水肿等。本研究结果与以上研究一致，高原缺氧暴露后小鼠肺组织出现病理损伤，而6-OHG给药后明显改善。大量研究表明：低压低氧诱发的氧化应激在高原肺损伤的发生发展中发挥着重要作用[13-14]。SHI等[15]研究表明缺氧会导致过量的活性氧（ROS）产生，继而过量的ROS可通过多种途径攻击细胞、组织和器官，导致氧化应激，诱发大鼠肺组织损伤。与先前的研究结果一致，本研究也发现低压低氧能够诱导小鼠肺组织MDA和H2O2含量升高，GSH和T-SOD水平显著降低，而6-OHG能够逆转这些变化，缓解肺组织氧化应激损伤。

  为了进一步阐明6-OHG治疗高原缺氧肺损伤可能的作用靶点和机制，本研究采用网络药理学方法，结果显示，6-OHG治疗高原缺氧肺损伤的关键靶点包括AKT1、HIF-1α、EGFR和MMP9等。KEGG通路富集分析表明HIF/VEGF、PI3K/AKT信号通路可能在6-OHG改善高原缺氧诱导肺损伤中发挥重要作用。缺氧诱导因子-1（HIF-1）是一种异二聚体（HIF-1α/HIF-1β）转录因子，其中氧敏感型HIF-1α亚基调节基因转录从而介导组织对缺氧的适应[16]。此外，在高原肺损伤的研究中已证明，在高原缺氧条件下阻断HIF-1α的激活，可以抑制下游促炎因子的产生，进而发挥治疗效果[15]。VEGF是调控血管内皮细胞功能的重要因子，研究表明其可以通过保护肺血管内皮细胞功能从而抑制肺血管的重塑[17]。PI3K/AKT信号通路参与细胞存活和抑制细胞凋亡。当激活PI3K时，PI3K会进一步激活PIP3，进而激活下游的各种信号分子，从而调节细胞凋亡、分化、增殖和迁移；AKT为PI3K下游靶点，而磷酸化AKT可通过丝氨酸473残基的磷酸化进而发挥调节作用[18]。JI等[19]研究表明PI3K/AKT信号通路会在缺氧肺动脉高压模型组中明显下调，而PI3K/AKT通路的激活可上调大鼠肺泡上皮钠通道的表达，增强肺泡钠通道和Na+-K+-ATP活性，从而减轻肺部损伤[20]。另一方面，一些异黄酮类化合物能够通过激活PI3K/AKT信号通路发挥有益作用。石娅等[21]研究表明毛蕊异黄酮能通过激活PI3K/AKT信号通路，调节Bcl-2和Bax蛋白表达，发挥抗凋亡作用，缓解肺组织的损伤。染料木素可以通过激活PI3K/AKT信号通路减轻缺氧[22]和野百合碱[23]诱发的肺动脉高压。本研究表明：低压低氧显著下调了PI3K和AKT的磷酸化，增高了HIF-1α和VEGF的表达；而6-OHG能够上调p-PI3K和p-AKT的表达，抑制HIF-1α和VEGF的表达。分子对接结果也表明：6-OHG能够与PI3K、AKT、HIF-1α和VEGF稳定结合，以上结果表明：从而6-OHG可能通过激活PI3K/AKT信号通路和抑制HIF/VEGF信号通路改善高原缺氧诱导的肺组织损伤。

  综上所述，本文采用网络药理学结合动物实验阐明了6-OHG通过激活PI3K/AKT信号通路和抑制HIF/VEGF信号通路，抑制氧化应激，改善高原缺氧肺组织损伤机制，有望将6-OHG开发成为治疗高原缺氧肺损伤的潜在药物。

  *　　　　*　　　　*

  作者贡献声明　马川负责论文构思、数据审编、正式分析、调查研究、研究方法、研究项目管理、初稿写作和审读与编辑写作，王小娟负责调查研究、研究方法、研究项目管理、验证和审读与编辑写作，杨陈煜负责研究方法、软件、验证和审读与编辑写作，张书瑜负责研究方法、研究项目管理、可视化和审读与编辑写作，杨宝乐负责研究方法、监督指导、可视化和审读与编辑写作，景临林负责论文构思、经费获取和审读与编辑写作，马慧萍负责经费获取、研究项目管理和提供资源。所有作者已经同意将文章提交给本刊，且对将要发表的版本进行最终定稿，并同意对工作的所有方面负责。

  Author Contribution　 MA Chuan is responsible for conceptualization, data curation, formal analysis, investigation, methodology, project administration, writing--original draft, and writing--review and editing. WANG Xiaojuan is responsible for investigation, methodology, project administration, validation, and writing--review and editing. YANG Chenyu is responsible for methodology, software, validation, and writing--review and editing. ZHANG Shuyu is responsible for methodology, project administration, visualization, and writing--review and editing. YANG Baole is responsible for methodology, supervision, visualization, and writing--review and editing. JING Linlin is responsible for conceptualization, funding acquisition, and writing--review and editing. MA Huiping is responsible for funding acquisition, project administration, and resources. All authors consented to the submission of the article to the Journal. All authors approved the final version to be published and agreed to take responsibility for all aspects of the work.

  利益冲突　所有作者均声明不存在利益冲突

  Declaration of Conflicting Interests　All authors declare no competing interests.