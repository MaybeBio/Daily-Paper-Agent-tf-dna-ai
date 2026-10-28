# Global research trends and hotspots of artificial intelligence research in spinal cord neural injury and restoration—a bibliometrics and visualization analysis


## Background
  Artificial intelligence (AI) technology has made breakthroughs in spinal cord neural injury and restoration in recent years. It has a positive impact on clinical treatment. This study explores AI research’s progress and hotspots in spinal cord neural injury and restoration. It also analyzes research shortcomings related to this area and proposes potential solutions.


## Methods
  We used CiteSpace 6.1.R6 and VOSviewer 1.6.19 to research WOS articles on AI research in spinal cord neural injury and restoration.


## Results
  A total of 1,502 articles were screened, in which the United States dominated; Kadone, Hideki (13 articles, University of Tsukuba, JAPAN) was the author with the highest number of publications; ARCH PHYS MED REHAB (IF = 4.3) was the most cited journal, and topics included molecular biology, immunology, neurology, sports, among other related areas.


## Conclusion
  We pinpointed three research hotspots for AI research in spinal cord neural injury and restoration: (1) intelligent robots and limb exoskeletons to assist rehabilitation training; (2) brain-computer interfaces; and (3) neuromodulation and noninvasive electrical stimulation. In addition, many new hotspots were discussed: (1) starting with image segmentation models based on convolutional neural networks; (2) the use of AI to fabricate polymeric biomaterials to provide the microenvironment required for neural stem cell-derived neural network tissues; (3) AI survival prediction tools, and transcription factor regulatory networks in the field of genetics were discussed. Although AI research in spinal cord neural injury and restoration has many benefits, the technology has several limitations (data and ethical issues). The data-gathering problem should be addressed in future research, which requires a significant sample of quality clinical data to build valid AI models. At the same time, research on genomics and other mechanisms in this field is fragile. In the future, machine learning techniques, such as AI survival prediction tools and transcription factor regulatory networks, can be utilized for studies related to the up-regulation of regeneration-related genes and the production of structural proteins for axonal growth.


## Introduction
  Spinal cord neural injury is a neurological injury due to direct or indirect factors, characterized by motor and perceptual dysfunction, abnormal muscle tone, and various other pathological feedbacks in the corresponding injured segment (1, 2). Currently, applied treatments in medicine usually fail to meet expectations, and research focuses mainly on using drugs, cellular therapies, and tissue engineering.

  Artificial Intelligence (AI) is a generic term that implies the use of computers to model intelligent behavior with minimal human intervention, and it is described as the science and engineering of building intelligent machines. There are two main branches of AI in medicine: virtual and physical. The virtual branch consists of informatics methods ranging from deep learning information management to control of health management systems, including electronic health records and active guidance of physicians in treatment decisions. The physical branch is represented by robots used to help patients or surgeons. Artificial intelligence has recently emerged to analyze and manipulate nerve reproduction and recovery information. AI can rate the extent of neural plastination and efficacy of nerve stem cells, and studies of neural injury and restoration could also offer valuable data resources for AI (3). Meanwhile, AI can also help translate nerve signaling and control machine exoskeletons (4). In addition, artificial intelligence can also discern which gene and signaling pathway is critical for nerve recovery (5).

  Therefore, AI systems and research on spinal cord neural injury and restoration can mutually reinforce each other and drive medical innovation. We used popular bibliometric software (CiteSpace and VOSviewer) to visualize and analyze the development history and research hotspots of AI research in spinal cord neural injury and restoration to analyze research shortcomings related to this area and propose potential solutions.


## Data and methods

### Retrieval strategy
  We searched the Web of Science (WOS) core collection for literature on AI research in spinal cord neural injury and restoration. A literature search was completed on March 5, 2024. The WOS retrieval formula (6) was #1TS = (“Artificial Intelligence” OR “AI” OR “Robot*” OR “Natural Language Processing” OR “Deep Learning” OR “Machine Learning” OR “Hierarchical Learning” OR “Autonomous System “OR “Intelligent System”); #2TS = (“Spinal Nerv*” OR “Spinal Cord*” OR “Spinal Nerve Regeneration” OR “Neural Repair, Spinal” OR “Neural Protection, Spinal” OR “Neural Rehabilitation, Spinal”); #1AND #2 (see Figure 1). Select article, review, and English.


### Data collection
  After the preliminary data retrieval, two researchers (T Gy and Y Bin) screened all manuscripts separately to ensure they were relevant to the theme of this study (see Figure 1). The final results were exported as a “plain text file,” with “Full Record and Cited References” selected as the record content and stored in download_*.txt format.


### Parameter settings and critical observations
  Parameterization of VOSviewer 1.6.19: Inter-country publication analysis (up to a minimum number of 24 papers) and keyword clustering analysis were performed using VOSviewer software.

  Parameterization of CiteSpace 6.1.R6: The time parameter was set from January 2004 to March 2024, 1 year as the time zone, Top N = 50, cropping was Pathfinder, Pruning sliced network and Pruning the merged networks, and the other settings were kept as default; Select keywords, literature, and journals for co-occurrence analyses and co-citation analyses.Conducting co-citation analyses of papers to define main research directions and hotspots. The following aspects are proposed to construct the co-citation graph: take the papers as nodes, cite frequency as the node size, link the literature with the co-citation relationship, and perform cluster analysis.Creating a keyword co-occurrence graph to analyze the emergent words.Creating the co-citation analysis graph of “hot” journals and studying its distribution in various disciplines.Creating a two-plot superimposed journal map showing, among other things, citation trajectories and focus drift in the field.


## Results

### Trend analysis of global publication output
  Based on the selection procedure, 1,502 papers on AI research in spinal cord neural injury and restoration were collected from the WoS database. Only 12 articles were published in this field in 2004, and no relevant literature was published before 2004. On the whole, the number of published papers is on the rise, indicating that the attempts and explorations made by scholars for AI research in spinal cord neural injury and restoration are gradually increasing, and its research value has been emphasized by many researchers in the academic community, see Figure 2.


### Country/region analysis and author analysis
  The VOSviewer 1.6.19 result indicates that 20 nations have at least 19 publications on the research topic (see Figure 3). As can be seen in Figure 3, there is a growing global enthusiasm for AI research in spinal cord neural injury and restoration, with the highest number of papers published in Asia and America. However, as a whole, the strength of the connection between countries is relatively fragmented, indicating that international cooperation still needs to be strengthened.

  The analysis results of the authors and institutions are shown in Table 1. Among them, Northwestern Univ and Univ Zurich have higher centrality, indicating that they have close connections with other institutions and frequently cooperate in conducting research and publishing articles.


### Analysis of research hotspots and “hot” journals based on journal citations

#### Analysis of journal co-citation bursts
  NEUROREPORT has paid the most attention to AI-assisted repair of spinal cord neural injury and restoration research and has paid attention to related hotspots for a more extended period (2004–2017). In the last 5 years (2019–2023), MED DEVICES-EVID RES, WORLD NEUROSURG, FRONT NEUROL, and IEEE ACCESS are the major journals focusing on the field of AI-assisted repair of spinal cord neural injury and restoration (see Figure 4). ARCH PHYS MED REHAB is the most cited journal (see Table 2).


#### Journal biplot overlay analysis
  Based on CiteSpace’s research base data, Journal Citation Reports (JCR) 2011 data were analyzed using the Blondel algorithm for journal biplot overlay analysis of the literature in this area (see Figure 5), with the citing journals on the left and the cited journals on the right—the citing journal concentrated on MOLECULAR, BIOLOGY, IMMUNOLOGY; or NEUROLOGY, SPORTS, OPHTHALMOLOGY. The most significant direction of cited journals was SPORTS, REHABILITATION. NEUROLOGY, SPORTS, OPHTHALMOLOGY, and MOLECULAR BIOLOGY GENETICS are most strongly associated with the journal and are the “hot” areas for AI-assisted repair of spinal cord neural injury and restoration (z = 5.211, f = 219).


### Keyword clustering analysis and burst analysis
  Keyword clustering analysis was performed using CiteSpace 6.1.R6 software (see Figure 6A), including nine main clusters: #0 Muscle synergy, #1 spinal cord injury, #3 assistive technology, #4 central pattern generator, #6 rehabilitation training, #7 functional electrical stimulation, #10 hybrid assistive limbs, #12 brain-computer interface, and #14 neural networks. Three main research directions for AI research in spinal cord neural injury and restoration were identified: (1) research on assistive exoskeletons and motor rehabilitation (#0, #3, #6, #10); (2) research on brain-computer interfaces (#4, #12, #14); and (3) research on functional electrical nerve stimulation (#7).

  Keyword bursting was performed using CiteSpace 6.1.R6 software. It consisted of two main phases: (1) the 2004-2017 focus direction was less intelligent robotic exoskeletons assisting weight support and locomotion in paraplegic patients and (2) the 2021-2024 focus direction was deep learning algorithms to enhance artificial intelligence (see Figure 6B).


### Literature co-citation analysis

#### Literature co-citation cluster analysis
  We obtained 25 clusters, including the 15 most significant clusters in the literature co-citation network (Figure 7A with Table 3).

  Clusters #0, #1, #2, #7, #8: Technology, Exoskeletons, Gait, treadmill training and Actuation. These clusters are all focused on machine exoskeletons to assist patients with rehabilitation exercises, and the main cited articles are Evans et al. (9) and Sanchez et al. (10). In recent years, robotic motion exoskeletons have provided standing and walking opportunities for people with spinal cord injury and considerable solutions for gait assistance and rehabilitation. The field focuses on actuation, structure, and interface connectivity components.

  Clusters #3, #4, #5, #14: Rehabilitation Robot-Assisted Gait Training. The principal cited articles for these two clusters are Banala et al. (11) and Fang et al. (12). Gait training is critical for promoting neuromuscular plasticity, which is necessary to improve functional walking ability. Robot-assisted gait training was developed for spinal cord injury patients using active leg exoskeletons and force field controllers, which effectively apply force at the subject’s ankle through actuators on the hip and knee joints for rehabilitation.

  Clusters #9, #10: Brain-Computer Interfaces and Noninvasive Brain Stimulation. The primary cited article in this cluster is Collinger et al. (13). Upper limb paralysis or amputation results in the loss of the ability to grasp., manipulate, and carry objects in the upper limbs. These functions are critical for activities of daily living. Brain-computer interfaces can provide a solution for restoring many of these lost functions. In this paper, two 96-channel intracortical microelectrodes were implanted in a patient’s motor cortex to test that quadriplegic patients can use this brain-computer interface to rapidly achieve neural control of a high-performance prosthesis.

  Cluster #6: neuromodulation. The primary cited article in this cluster is Angeli et al. (14), which demonstrated that neuromodulation of spinal circuits by epidural stimulation enables wholly paralyzed patients to regain relatively fine autonomous control over paralyzed muscles. That neuromodulation of excitatory subthreshold motor states in the lumbosacral spinal cord network is the key to restoring conscious movement in individuals diagnosed with complete leg paralysis. A novel intervention strategy was discovered that significantly impacts the recovery of voluntary action in completely paralyzed individuals even years after injury.


#### Cluster analysis of co-cited literature on research hotspots in the last 5 years
  We obtained the nine most significant clusters in the literature co-citation network (Figure 7B with Table 4).

  Clusters #0, #3, #7, #8: Robotic Motion Exoskeleton Assisted Movement and Rehabilitation. Both groups are focused on machine exoskeletons, and the main cited articles are Fang et al. (12) and Sanchez et al. (10). The field focuses on actuation, structure, and interface connections.

  Cluster #1, #10: Brain-computer interface technologies. The principal cited article in this cluster is Ajiboye et al. (15), which allows for the restoration of limb movement in patients with chronic quadriplegia through coordinated electrical stimulation of the surrounding muscles and nerves (also known as functional electrical stimulation); the patient’s cortical signals can be used to direct limb movement through an implanted practical electrical stimulation component and an intracortical brain-computer interface. This is the first co-implanted functional electrical stimulation + intracortical brain-computer interface neuroprosthesis and represents a significant advancement in the clinical feasibility of neuroprostheses.

  Cluster #11, #12: Overview of Neuromodulation and Electrical Stimulation. The primary cited article in this cluster is Gill et al. (16), where spinal sensory-motor networks that are functionally disconnected from the brain as a result of spinal cord injury can be facilitated by epidural electrical stimulation to encourage the return of robust, coordinated motor activity in paralyzed patients. Dynamic task training in the presence of epidural electrical stimulation is referred to as multimodal rehabilitation in this study. This article is the first report of such multimodal rehabilitation in patients with sensory and motor loss of the lower extremities due to spinal cord injury.


#### Hot spot analysis of co-cited literature
  The cited literature of all nodes was ranked according to the number of co-citations, and the 10 articles with the highest number of co-citations are shown in Table 5. The main hotspots are AI exoskeleton and robot-assisted gait training (Table 6).


## Discussion

### Summary and interpretation of visual analysis results
  A total of 1,502 articles were screened, in which the United States dominated; Kadone, Hideki (13 articles, University of Tsukuba, JAPAN) was the author with the highest number of publications; ARCH PHYS MED REHAB (IF = 4.3) was the most cited journal, and topics included molecular biology, immunology, neurology, sports, among other related areas.

  Keyword clustering analysis reveals two main research directions for AI research in spinal cord neural injury and restoration: (1) research on physically biased robot-assisted rehabilitation exercises in AI and (2) research on virtual branches of AI such as deep learning algorithm-assisted brain-computer interfaces and functional electrical stimulation. The results of the keyword breakout analyses show that deep learning and artificial intelligence have been the hottest in the past 5 years (Figure 8).

  We performed a co-citation clustering analysis of the included articles to explore the hot directions further and obtained 15 clusters. We performed further analysis to show that the use of artificial intelligence in spinal cord neural injury and restoration focuses on artificial intelligence control electrical stimulation of the spinal cord neuroprosthesis (brain and spinal cord) and information processing. The ultimate goal is to enable patients with paralysis and limb injuries to recover limb function faster through artificially intelligent therapies such as robotic exoskeletons

  neuromodulation and brain-computer interfaces.

  Next, we performed a co-citation cluster analysis of the literature over the last 5 years. The top research topics in the past 5 years were robotic motion exoskeletons for assisted motor rehabilitation and brain-computer interface and neuromodulation. The field of robotic exoskeleton focuses on three aspects: AI drive, structure, and interface connection; the area of brain-computer interface mainly focuses on functional electrical stimulation + intracortical brain-computer interface technology for the feasibility of clinical neuroprosthesis.


### Integration of research hotspots on AI research in spinal cord neural injury and restoration
  Based on the above bibliometric results, combined with the authors’ understanding, we identified research hotspots for AI research in spinal cord neural injury and restoration:Intelligent robots and limb exoskeletons for assisted rehabilitation: there is no doubt that these physical branches of AI are the most significant research hotspot of AI in the field of spinal cord neural injury and restoration, which is multiply verified from the keyword analysis, literature co-citation analysis, and the hotspot analysis of highly co-cited literature. Rehabilitation robots are interactive motorized devices that allow fine limb movement and precise measurements (27). They are typically divided into exoskeletons that assist in limb movement by controlling the displacement of each segment and end-effector devices capable of mobilizing the limb from a distal point of application. Sanchez (10) concluded that the field of machine exoskeletons focuses on three aspects: actuation, structure, and interface connectivity. From the above keyword analysis, it can be seen that with time, intelligent robots with deep learning will gradually replace ordinary machine exoskeletons as the emerging hotspot in this field. The authors believe that researchers should vigorously develop various artificial intelligence models, such as feed-forward topological neural networks and supervised learning (8, 28), to improve the safety, tolerance, and walking functional efficacy of robotic exoskeletons to satisfy the needs of clinical patients for more efficient and high-quality treatments.Brain-computer interfaces: a cluster analysis of literature co-citations and co-citations over the last 5 years shows that brain-computer interfaces with deep learning algorithms are one of the continuing hotspots in this field. Brain-computer interface devices are designed to restore lost function and can be used to form electronic “neural bypasses” to circumvent damaged pathways in the nervous system (29, 30). Artificial intelligence techniques applied to brain-computer interfaces can enable disabled and mobility-impaired people to control machines or other devices. Through implanted intracortical brain-computer interfaces, the patient’s cortical signals can be used to direct limb movements (31). For example, Collinger (13) implanted two 96-channel intracortical microelectrodes in a patient’s motor cortex and tested that quadriplegic patients could use this brain-computer interface to achieve neural control of high-performance prostheses rapidly. In addition, Ajiboye (15) restored limb movement in paralyzed patients through an implanted functional electrical stimulation component and an intracortical brain-computer interface. The authors concluded that neuroelectrical stimulation and intracortical brain-computer interface techniques could be combined to restore the neurophysiologic and motor status of SCI patients more effectively. In addition, in the future, researchers could apply machine learning algorithms to decode neuronal activity and control the activation of nerves and muscles in SCI patients with a customized, high-resolution neuromuscular electrical stimulation system, empowering patients with the critical ability to manipulate and release objects.Neuromodulation and noninvasive electrical stimulation: the cluster analysis of literature co-citations and literature co-citations in the last 5 years shows that neuromodulation and noninvasive electrical stimulation are continuing hotspots in this field. Neuroelectrical stimulation is a noninvasive stimulation strategy (32) that transforms neuronal networks from dormant to functional, thereby gradually restoring control over paralyzed muscles (33, 34). In this regard, “numerical models” enhanced by deep learning algorithms are the basis for theoretical simulations of neurostimulation techniques and provide technical guidance for clinical applications. Alexandre Boutet (35) constructed a machine-learning model using fMRI patterns of patients that predicts optimal versus non-optimal settings and has a priori clinically optimized DBS (88% accuracy). The authors suggest that future neuroelectrical stimulation research could incorporate deep learning algorithms, such as convolutional neural networks, and use various strategies to neuromodulate the physiological state of the nerves and restore motor function in paralyzed patients. In addition, finding more targeted neuroelectrical stimulation techniques by performing a series of spatially selective stimulations may be one of the future directions.

  In summary, our results are relatively reliable based on the bibliometric results and the authors’ understanding.


### Experts’ discussion on new research hotspots
  In recent years, breakthroughs have been made for AI research in spinal cord neural injury and restoration, positively impacting clinical care. Firstly, artificial intelligence is widely used in neural imaging. For example, image segmentation models based on convolutional neural networks can make excellent contributions to imaging parameters, disease classification, and diagnosis of spinal cord neural injury patients before and after surgery (36, 37). Second, AI can track and analyze in real-time all neural components of various nervous systems, i.e., neural structure, neurodynamics, neuroplasticity, and neural memory (38).

  In addition, AI has many applications in repairing spinal cord nerve injuries using biomaterial technology (39). Transplantation of stem cells to the site of injury is a promising approach. Still, it faces many challenges and is highly dependent on the microenvironment provided by the lesion site and the delivery material (7). Using AI to fabricate polymeric biomaterials can provide the microenvironment required for neural stem cell-derived neural network organization to facilitate neural remodeling and repair (40). For example, Li (39) designed a 3D bioactive scaffold and demonstrated that neural network tissues derived from neural stem cells modified by pro-myosin receptor kinase C had strong viability within the scaffold. In addition, Yuan (41) designed DNA hydrogel with extremely high permeability properties by artificial intelligence for repairing a 2-mm spinal cord gap in rats and implanted the proliferation and differentiation of endogenous stem cells to form a nascent neural network. The authors concluded that neural network organization formed by transplantation in 3D innovative bioactive scaffolds may represent a valuable therapy for studying and developing SCI. Still, this technology has not yet been studied on a large scale, and future development should focus on this direction.

  Research in the field of genetics: genomic data have high complexity and dimensionality due to differences in genetic structure and functional gene diversity. It is difficult to reveal the sequence patterns and biological mechanisms of genomes using classical analysis methods. At the same time, AI can mine critical biological information from massive multidimensional data, so they are widely used in genome analysis for various diseases (42–44). For example, Artificial intelligence can also discern which gene and signaling pathway is critical for nerve recovery. However, in the field of AI-assisted repair of spinal cord neural injury, the study of genomics and other mechanisms is fragile. In the future, various machine learning techniques, such as AI survival prediction tools, transcription factor regulatory networks, etc., can be utilized to conduct studies related to regeneration-related gene up-regulation and axon growth structural protein production.


### Limitations of the study
  The WOS core database was searched in this study, and no other English databases were searched. Only WOS data can be analyzed for journal and literature co-citation analysis (a core bibliometrics technique). There is no doubt that WOS, as an authoritative mainstream database, still contains comprehensive and reliable data. Secondly, due to the limitation of the length of the article, this paper does not fully present the details of the specific research methodology in the selected literature but only provides an overview of the ideas in the literature.


### Outlook
  The following research themes are crucial for future AI research in spinal cord neural injury and restoration.Optimizing data quality and scale: Training AI models require larger, high-quality data pools, and when conducting biomedical explorations, it also requires innovative experimental means to collect relevant data sets.Conducting large-scale clinical trials: Conducting large-scale clinical studies research on AI in spinal cord neural injury and restoration lacks substantial and high-quality clinical trials; therefore, high-quality multicenter and randomized controlled clinical trials should be conducted in the future for in-depth research.Application feasibility of ChatGPT: ChatGPT has recently become a hot topic of discussion, and diagnosing diseases and providing therapeutic advice are promising research areas for ChatGPT. Nonetheless, users who lack specialized knowledge may not be able to recognize the authenticity. People should use ChatGPT cautiously, e.g., just for some initial understanding of the disease.


## Conclusion
  This literature metric study reveals dynamic trends in publication patterns and research hotspots for AI-assisted neural injury and restoration of spinal cord neural injuries across the globe. In addition, it identifies potential partners and institutions, major research hotspots, and upcoming research directions in the fields, thereby providing precious guidance for future studies in this area. Finally, the results of this study will be a valuable resource for clinical practitioners, researchers, industrial collaborators, and other interested stakeholders.


## Data availability statement
  The original contributions presented in the study are included in the article/Supplementary material, further inquiries can be directed to the corresponding author.


## Author contributions
  BY: Writing – review & editing, Writing – original draft, Visualization, Validation, Supervision, Software, Resources, Project administration, Methodology, Investigation, Funding acquisition, Formal analysis, Data curation, Conceptualization. GT: Writing – review & editing, Writing – original draft, Visualization, Validation, Supervision, Software, Resources, Project administration, Methodology, Investigation, Formal analysis, Data curation, Conceptualization. SY: Writing – review & editing, Software, Methodology, Investigation, Data curation, Conceptualization. JX: Writing – review & editing, Software, Methodology, Investigation, Data curation, Conceptualization. LW: Writing – review & editing, Software, Methodology, Investigation, Data curation, Conceptualization.


## Conflict of interest
  The authors declare that the research was conducted in the absence of any commercial or financial relationships that could be construed as a potential conflict of interest.


## Publisher’s note
  All claims expressed in this article are solely those of the authors and do not necessarily represent those of their affiliated organizations, or those of the publisher, the editors and the reviewers. Any product that may be evaluated in this article, or claim that may be made by its manufacturer, is not guaranteed or endorsed by the publisher.


## Supplementary material
  The Supplementary material for this article can be found online at:

  https://www.frontiersin.org/articles/10.3389/fneur.2024.1361235/full#supplementary-material