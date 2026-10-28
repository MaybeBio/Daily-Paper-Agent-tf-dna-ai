## Abstract

Human experts are good at summarizing explicit strong patterns from small samples, while deep learning models can learn implicit weak patterns from big data. Biologists have traditionally described the sequence patterns of promoters via transcription factor binding sites (TFBSs), while the flanking sequences among TFBSs, which can also significantly influence promoter activity and function, remain largely uncharacterized. Thus, current synthetic promoters are mainly designed by the manipulation of TFBSs, while the flanking sequence is often chosen arbitrarily or by previous experience due to a lack of well-summarized optimization criteria. Here, we introduced an AI-aided promoter design framework, DeepSEED, that employs expert knowledge and deep learning methods to efficiently design synthetic promoters that have various desirable functions. DeepSEED incorporates the user-defined cis-regulatory sequences as ‘seeds’ and generates flanking sequences that match the ‘seeds’. We showed that DeepSEED can automatically capture k-mer frequencies and DNA shape features from active promoters in the training set and efficiently optimize the flanking sequences to better match desired properties in synthetic promoters. We validated the effectiveness of this framework for diverse synthetic promoter design tasks in both prokaryotic and eukaryotic cells. DeepSEED successfully designed E. coli constitutive, isopropyl-beta-D-1-thiogalactopyranoside (IPTG)-inducible, and mammalian cell doxycycline (Dox)-inducible promoters with significant performance improvements, suggesting that DeepSEED has potential as an efficient AI-aided flanking sequence optimization approach for promoter design that may be of great benefit in synthetic biology applications.

Availability https://github.com/WangLabTHU/deepseed


## Main

Promoters are core genetic elements that regulate gene expression 1 . Designing synthetic promoters with desirable properties to precisely control gene expression is a requisite for biosynthetic engineering and gene therapy 2 . It has been believed that the properties of a promoter are mostly determined by cis-regulatory elements 3 , 4 , i.e., transcription factor binding sites (TFBSs), such as the –10/–35 elements in prokaryotes and the TATA-box in eukaryotes 5 , 6 . The sequence preference of TFBSs is commonly summarized as motifs and represented by position weight matrices (PWMs). As the sequences and functions of TFBSs are usually well known, most researchers design new promoters by manipulating the combinations and arrangements of TFBS motifs 7 , 8 . However, recent evidence has highlighted that TFBS flanking sequences also significantly influence promoter properties 9 – 11 . The roles of the flanking sequence have been explained at multiple levels and include the dependency between TFBSs and their flanking regions 8 , 10 , potential low-affinity binding sites 11 , 12 , non-canonical DNA structures 13 , 14 , and physicochemical properties such as DNA shapes 15 , 16 . It is difficult to summarize these features into explicit promoter design rules; thus, the optimization of flanking sequences is largely unexplored in current promoter design approaches.

Recently, deep learning models have shown great potential in both eukaryotic and prokaryotic promoter engineering 6 , 17 , 18 . By capturing shared sequence patterns from a large number of natural promoters, these models have been able to generate numerous de novo constitutive promoters with high diversity. However, these data-driven deep learning models cannot address the demands of designing promoters with specific properties such as inducible promoters or tissue-specific promoters, as in nature there exist only a handful of promoters or even just a single promoter with the desired property for use in training 19 – 21 . Consequently, most synthetic promoters used in practice were designed through expert prior knowledge. For example, researchers may put TFBSs with related functions into a backbone sequence and then optimize the sequence with mutagenesis 8 , 21 , 22 . Such approaches lack instructive schemes for optimizing flanking sequences that also affect promoter properties, usually resulting in poorer-than-expected outcomes or painstaking trial-and-error tests.

Here, we propose DeepSEED ( Deep learning-based flanking S equence E ngineering for E fficient promoter D esign), an AI-aided flanking sequence optimization method for synthetic promoter design. DeepSEED aims to integrate expert knowledge with the power of data-driven models to facilitate efficient promoter design. DeepSEED is composed of two deep learning models: a conditional generative adversarial network (cGAN) 23 , 24 that generates flanking sequences based on preset sequence elements, and a DenseNet-LSTM-based model (where LSTM denotes “long short-term memory”) that predicts promoter properties. To design a synthetic promoter with desired properties, users can—based on their prior knowledge—first input any number of sequence elements (e.g., TFBSs) of interest at any position as a ‘seed’, and then DeepSEED will generate the flanking sequences based on the ‘seed’ to fit into the implicit patterns of promoters. We tested DeepSEED in three different promoter design tasks: prokaryotic constitutive promoters, prokaryotic IPTG-inducible promoters, and eukaryotic doxycycline-inducible promoters ( Fig. 1d ). In all three cases, DeepSEED showed significant improvement in achieving desired promoter properties with high success rates. The synthetic promoters generated by DeepSEED showed high sequence diversity and maintained similar features like k-mer frequencies and DNA shape features with training samples at both local and global promoter regions. These results showed the vital importance of flanking sequences to promoter activity and suggested DeepSEED as a powerful AI-aided tool for designing synthetic promoters.


## Results


## Overview of the AI-aided flanking sequence optimization method DeepSEED

DeepSEED constructed a probabilistic view to unify the expert knowledge to define the ‘seed’ of promoters and deep learning methods to fill up the flanking sequences that match the ‘seed’ to improve the promoter performance. The promoter design problem can be formulated in probabilistic terms as maximizing the joint probability of the promoter sequence s and the target property T , i.e.,

The promoter sequence s is divided into two parts: ‘seed’ sequences m derived from expert knowledge and flanking regions of ‘seed’ f . By applying the chain rule, the following is obtained:

The formula suggests that the maximization of the probability could be achieved in two stages ( Fig. 1a ). The first term P ( m | T ) indicates the process of assigning m compatible with the target property according to expert knowledge (Stage I, Expert Knowledge Integration). The second term P ( f | m , T ) represents optimizing flanking regions f conditioned on the ‘seed’ sequences m and the property T (Stage II, Sequence Optimization, see details in Methods).


## Expert Knowledge Integration

In Stage I, the maximization of the first term P ( m | T ) is achieved by selecting ‘seed’ based on expert knowledge that has been proven to be essential for achieving the target property T . In the next stage, we assume that ‘seed’ sequences are fixed, defined as m ∗


## Sequence Optimization

Given m ∗ determined in Stage I, Stage II maximizes P ( f | m ∗ , T ). According to the Bayes rule,

where the first term, P ( f | m ∗ ), is related to the flanking sequence generation problem, in which one seeks the compatible flanking sequence f based on m ∗ . The second term, P ( T | f , m ∗ ), is the probability of a promoter property T for the given sequence s = ( f , m ∗ ).

A cGAN-based flanking sequence generation model was adopted in DeepSEED to estimate P ( f | m ∗ ) (Methods). Attention-based layers were applied because of their ability to capture the widespread long-range interactions in regulatory codes. A DenseNet-LSTM-based predictor was trained to evaluate the properties of input promoters, i.e., P ( T | f , m ∗ ) ( Fig. 1c , Supplementary Fig. S1). This predictor achieved a high Pearson correlation coefficient (PCC) of 0.74 compared with our previous CNN-based predictive model 17 (PCC = 0.65) in the E. coli promoter training dataset (Supplementary Fig. S5). The genetic algorithm (GA) combining the cGAN generator and the predictor was applied to maximize the probability of P ( f | m ∗ , T ) to design synthetic promoters with target properties ( Fig. 1b , Supplementary Fig. S7b). In the following sections, we will demonstrate that DeepSEED can learn the implicit pattern in flanking sequences and can design high-activity promoters based on expert knowledge ( Fig. 1d ).


## DeepSEED captures essential features of natural promoter sequences

We first investigated the importance of flanking sequences in predicting promoter activity in silico . We predicted the expression level of 2000 functional E. coli promoters by the predictor model and clustered their saliency maps 25 (Methods). As shown in Fig. 2a and Supplementary Fig. S6, we found that the –10 and –35 elements strongly influence promoter activity, as reported by previous studies 26 . However, the influence of flanking regions is also important. Each cluster showed distinct patterns in flanking regions on the saliency maps, and the potential relationship of flanking sequences to promoter activity is difficult to describe explicitly.

We then evaluated whether the DeepSEED architecture can capture the implicit patterns of flanking sequences at local and global promoter regions. For E. coli promoters, we observed that the K-mer frequency between natural and DeepSEED-designed sequences correlated well (K = 4 to 6) at the global scale ( Fig. 2c , Supplementary Fig. S3a), which was much better than the sequences designed by our previous Wasserstein generative adversarial network–gradient penalty (WGAN-GP) model 17 (Supplementary Fig. S3d). We further investigated the K-mer frequencies at the distal and proximal ends of the promoter, as they exhibit different K-mer patterns in natural sequences (Supplement Fig. S3c), and the results showed that DeepSEED successfully captured the K-mer features on both ends ( Fig. 2c ). The K-mer frequency in designed Dox-inducible promoters with preserved tetO sequences also showed a high correlation with natural sequences ( Fig. 2d , Supplementary Fig. S3b).

DNA shapes are physicochemical features of DNA sequences that contain structural information, such as the minor groove width (MGW), roll, propeller twist (ProT), and helix twist (HelT) 27 . Appropriate DNA shapes near TFBSs could enable TF binding and thus influence transcriptional activity 28 – 30 . We first examined the four kinds of DNA shape features on the left side of two widespread –10 elements, ‘TATAAT’ and ‘TATAAA’, in E. coli and found that DeepSEED-designed promoters showed patterns more similar to those of natural promoters than to random sequences at the local scale ( Fig. 2e , Methods). We further embedded DNA shape features of whole promoter sequences by t-distributed stochastic neighbor embedding (t-SNE) (Methods) and found that E. coli promoters in the training dataset can be divided into two groups in the embedding space related to their transcriptional activities, implying the strong dependence between DNA shapes and promoter activities ( Fig. 2b ). Moreover, we noticed that DeepSEED optimization can successfully move a promoter sequence from the low-activity region to the high-activity region in the embedding space.

We also investigated the promoter sequences from the perspective of the DNA semantic sequence space (Methods). Compared with promoter sequences of other species in the training dataset, the DeepSEED-designed promoter sequences and natural E. coli promoters are co-located in the same low-dimensional space (Supplementary Fig. S4b). Furthermore, we demonstrated that DeepSEED-designed promoters showed similar diversity to natural sequences by comparing the editing distance distributions (Supplementary Fig. S4a, Methods), indicating that DeepSEED has the ability to generate brand-new promoters rather than simply modifying natural promoters. All the above results suggested that DeepSEED was able to capture essential features of natural promoter sequences and direct the model to generate de novo high-activity promoters.


## Design of constitutive promoters in E. coli

We first used DeepSEED to design constitutive promoters in E. coli . We fixed the sequence and position of –10/–35 elements as ‘seed’ sequences ( Fig. 3a ). DeepSEED was trained on promoters from the massively parallel reporter assay (MPRA) dataset 31 to optimize flanking sequences to improve the activity of promoters (Supplementary Fig. S2a). Compared with natural E. coli promoters containing the same –10 and –35 elements, DeepSEED-designed sequences were predicted to have higher expression levels in silico (Supplementary Fig. S7a).

Then, we verified the properties of DeepSEED-designed sequences in vivo . Three widely used constitutive promoters adopted from the Internationally Genetically Engineered Machine (iGEM) parts registry (BBa_J23119, BBa_J23118, and BBa_J23114, http://parts.igem.org/Promoters/Catalog/Constitutive ) with different –10 and –35 elements were selected as the initial sequences to be optimized. The three promoters showed high, medium, and low expression levels in vivo (Supplemental Fig. S8). For each initial sequence, we kept the ‘seed’ sequences and designed 16 new sequences with DeepSEED (Supplementary Notes). For the sake of comparison, we also generated two control groups ( Fig. 3b ): the Control-1 group using random sequences to extend the initial promoter sequences to 165 bp, the same length as promoters in the training dataset, to prevent the effect of length on promoter activity; and the Control-2 group in which the ‘seed’ sequences were maintained while randomizing all the other regions. The detailed sequences of promoters are provided in Supplementary Table S1.

We measured the constructed promoter activities by the fluorescence intensity of downstream sfGFP (Methods). As shown in Fig. 3c and Supplementary Fig. S9a, the promoter activities of the Control-1 group were comparable to those of the initial promoters. The Control-2 group showed a higher variance in promoter activities due to the introduction of more random sequences. The high variability in the activities of random flanking sequences in the Control-1 and Control-2 groups also indicated the importance of flanking sequences for promoter activity. After DeepSEED optimization, the activities of synthetic promoters in the DeepSEED group exhibited great improvement, increasing by an average of 1.42-, 4.11- and 33.43-fold compared with the Control-2 group based on the initial promoters BBa_J23119, BBa_J23118, and BBa_J23114, respectively. We also compared the DeepSEED results with our previous whole sequence generation method 17 and found that DeepSEED showed an average 6.73-fold increase in promoter activity ( Fig. 3e , Supplementary Fig. S9b), suggesting that compared to learning only the general patterns from training samples, introducing expert knowledge such as the consensus motif in the promoter region may help the model generate promoters with better performance.

To exclude the possibility that the increase in promoter activity is due to the generation of a second promoter rather than to flanking sequence optimization, we analyzed the DeepSEED-designed promoters with motif-finding algorithms to evaluate the existence of the alternative promoter within the flanking sequence (Methods). We found that the signals of ‘promoter structure’ motifs in flanking sequence regions were almost always lower than those in the original regions (Supplementary Fig. S10). Although some increasing signals in flanking regions appeared, they were still much lower than those in the strongest promoter BBa_J23119. The results indicated that DeepSEED did not generate alternative high-activity promoter structures in flanking regions.

We plotted all the promoters and control samples in the DNA shape embedding space ( Fig. 3d ). Most of the Control-1 and Control-2 samples were located in low promoter activity regions, which indicated that random sequences in flanking regions fail to configure the DNA shape for higher transcriptional activity. In contrast, DeepSEED optimized the flanking regions and generated highly expressed DNA shape features. These results indicated that the improvement of DeepSEED-designed promoters could partly be explained by the optimization of DNA shape features in flanking regions.


## Design of IPTG-inducible promoters in E. coli

In bacteria, the promoter contains not only the –10 and –35 elements but also regulatory sequences that could be bound by transcription factors to activate or repress gene expression, as with the lac promoter in the typical lac operon in E. coli 32 . The activity of the lac promoter is repressed when the LacI protein binds to lacO sites, and the repression can be relieved in the presence of lactose or its analogs, such as IPTG ( Fig. 1d ). The lac promoter is widely used in synthetic biology as an inducible promoter. We aimed to use DeepSEED to design new IPTG-inducible promoters based on the LacI-DNA interaction pattern as expert knowledge ( Fig. 4a ). Here, DeepSEED was trained on promoters from the MPRA dataset 31 to optimize flanking sequences to increase transcription under induced conditions (Supplementary Fig. S2b).

The number and position of the lacO sites are crucial for promoter performance. Appropriate spacing between different lacO sites may help to form a repression loop and further reduce leakiness expression 19 , 33 . Here, we adopted two, three, or four lacO sites at suitable positions and spacing for LacI protein binding and loop formation 19 to design promoters (Supplementary Fig. S11). We randomly chose 25 constitutive promoters from the training samples as backbone sequences. We identified –10 and –35 elements and their spacer lengths for each sequence and adopted these features as well as the number and position of lacO sites as expert knowledge for the generation model ( Fig. 4b ). For each backbone sequence, we selected three sequences that were predicted to have high activity for experimental validation (Supplementary Notes). In addition, we directly substituted the corresponding sequence with lacO sites on the backbone sequence as the substitution control group and measured their activities in vivo . The detailed sequences of promoters are provided in Supplementary Table S1.

We found that after the direct substitution, sequences showed different degrees of activity loss under the induced condition ( Fig. 4c , Supplementary Fig. S13-15). The average induced expression level was reduced by 52.8%, 80.8%, and 97.1% with two, three, or four lacO direct substitutions, respectively. The loss of expression may be due to the disruption of promoter structures by direct substitution, which is a common problem in inducible promoter design 34 . In contrast, the DeepSEED-designed promoter restored high expression levels and could even outperform the original promoters ( Fig. 4c , left). The average expression level of DeepSEED-designed promoters under induced conditions decreased with increasing lacO site numbers and showed 8.96-, 6.54-, and 47.96-fold increases compared with the corresponding substitution promoters with two, three, or four lacO sites, respectively. Meanwhile, introducing lacO sites certainly generated the ability to respond to IPTG. The fold-change of DeepSEED-designed promoters showed great improvement with an increase in the number of lacO sites ( Fig. 4c , right). The average fold-change of the designed promoters with two lacO sites was lower than that of the substitution group, which was caused by the higher leakage expression level under the uninduced condition. For designed promoters with three or four lacO sites, each had on average 2.20- and 2.94-fold increases compared with the corresponding substitution promoters. The results showed that DeepSEED has the ability to design high-performance inducible promoters with different lacO sites introduced.

We further compared the performance of synthetic promoters with two widely used IPTG-inducible promoters, placUV5 35 and pLlacO1 36 ( Fig. 4d ). Almost all of the substitution promoters showed extremely low induced expression levels and thus are difficult to be employed for synthetic biology applications. In contrast, DeepSEED-designed promoters showed wide distribution with different induced expression levels and fold-changes, which could satisfy various demands for fine-tuning genetic circuits. Moreover, there was a trade-off in fold-change and maximum induced expression levels, with different numbers of lacO sites ( Fig. 4d , Supplementary Fig. S12), suggesting that the performance of synthetic promoters could be easily adjusted by altering the number of lacO sites.

We investigated the distribution of synthetic promoters in the functional space by embedding the outputs of the penultimate layer in the predictor model using t-SNE ( Fig. 4e ). We found that both backbone and substitution promoters were widely distributed in space, while DeepSEED-designed promoters tended to fall in the high-activity region. These results supported the notion that the generated flanking regions were more compatible with the motif seeds and target properties.


## Design of Dox-inducible promoters in mammalian cells

We further extended the DeepSEED model to mammalian cell data to test its potential in designing eukaryotic promoters. Here, we focused on the Tet response element (TRE) promoter 37 , 38 , one of the most widely used inducible promoters in mammalian cells. Taking the Tet-On system as an example, the transcription of the TRE promoter would be repressed in the presence of the reverse tetracycline-controlled transactivator (rtTA) protein, which binds to the tetO site in the TRE promoter. When tetracycline or its analogs, such as doxycycline, are added, the repression would be relieved, and thus, gene expression would be activated ( Fig. 1c ). The classic TRE promoter contains seven direct repeats of tetO sites linked by repeated flanking sequences and has been used in the Tet-On system since 1995 38 . Previous engineering approaches for the TRE system focused on altering key amino acid residues in tetracycline-controlled proteins to achieve higher fold changes between induced and repressed states 39 . However, the design of the TRE promoter sequence progressed slowly due to the lack of an effective optimization strategy.

We chose the Tet-On system as an example to validate the performance of DeepSEED ( Fig. 5a ). We preserved the miniCMV promoter sequence as well as the tetO sites as ‘seed’ sequences and then generated flanking sequences with DeepSEED. The generator model was trained on the enhancer sequences in the HEK293 cell line from the Human ACtive Enhancers to interpret Regulatory variants (HACER) dataset 40 . During the training process, we annotated all known motifs of sequences in the training dataset with the JASPAR database 41 and kept the motifs while masking their flanking sequences as model input. DeepSEED aimed to recover their masked sequences to learn the regulatory patterns within flanking sequences. To avoid the increase in non-induced baseline expression, we removed all DeepSEED-designed sequences with potential binding sites of other TFs (Supplementary Fig. S2c). The detailed sequences of the in vivo validated promoters are provided in Supplementary Table S1.

Due to the sequence length limit in the training data sequence lengths, we first truncated the TRE promoter with three tetO sites as the initial template for flanking sequence optimization ( Fig. 5b ). After examining the predicted promoter performance from the predictor model and filtering out all sequences with known motifs, we obtained 12 optimized promoters to test in vivo (Supplementary Notes). As a result, 75% of the DeepSEED-designed promoters showed higher expression levels than the 3-tetO template, with improvements of up to 2.46-fold ( Fig. 5c , Supplementary Fig. S16a). Moreover, 50% of the designed promoters showed a higher fold-change, with improvements of up to 1.41-fold. Four designed promoter sequences showed improvement in both induced activity and fold-change. It is worth noting that some designed 3-tetO promoters even showed comparable induced activity to the whole-length TRE promoter with seven tetO sites, but the length is only 54.4% of the whole length. In addition, as the flanking sequences among tetO sites were optimized to non-repeating sequences, the designed promoter might have increased the DNA stability. These shorter promoters could facilitate vector construction while maintaining comparable promoter properties.

We then integrated the flanking sequences of the well-performing 3-tetO promoters to design 7-tetO promoters ( Fig. 5b ). We validated eight double-combination promoters and ten triple-combination promoters by integrating two and three types of optimized 3-tetO flanking sequences, respectively, in vivo . As a result, 77.8% of designed promoters showed induced activity improvement compared with the original 7-tetO-TRE promoter ( Fig. 5d , Supplementary Fig. S16b, c), with an average 1.134-fold improvement and a maximum improvement of 1.234-fold. A total of 83.3% of the DeepSEED design promoters showed a higher fold-change, with improvements of up to 1.61-fold. A total of 72.2% of the designed promoters showed improvement in both induced activity and fold-change. It should be noted that the activity of the original 7-tetO-TRE promoter is comparable to that of the very strong constitutive promoters EF1A and CAGG in mammalian cells 42 ; however, DeepSEED was still able to improve promoter activity without changing the main sequence architecture. All the results suggested the necessity of optimizing flanking sequences in designing eukaryotic promoters and again indicated the power of DeepSEED to learn regulatory patterns within flanking sequences.


## Discussion

In this study, we proposed DeepSEED, an AI-aided flanking sequence optimization method for synthetic promoter design. DeepSEED divided the promoter design process into two steps: first setting ‘seed’ sequences as model constraints based on expert knowledge and then generating flanking sequences via a deep learning model trained on big data. We demonstrated that this co-driven knowledge-data strategy can capture the implicit patterns in flanking sequences and thus gain the ability to efficiently optimize various types of promoters with high performance.

DeepSEED can be applied to design not only constitutive promoters but also other types of promoters that have just a single or a handful of natural references. The key to this success was that we did not treat constitutive and inducible promoters as distinct objects. Instead, we proposed a probabilistic view to unify these design tasks into the same conditional optimization framework. The specific desired promoter functions were encoded by the ‘seed’ sequences, while DeepSEED was employed to optimize promoters as a whole to better fit the general implicit pattern preference of active promoters. This strategy helped us overcome the small sample size problem in inducible promoter design.

This study indicated that flanking sequences are of vital importance to the properties of promoters once again 10 . DeepSEED successfully learned the implicit patterns of flanking sequences, and the results of saliency maps and embedding space exploration showed that the features extracted by DeepSEED are related to promoter activity. However, how these virtual features are related to real biochemical properties and biological functions is still unknown. With the rapid development of interpretation methods of deep learning models 43 , it would be possible to combine deep learning and biological experiments to uncover how features of flanking sequences matter to promoter properties in an explicit way to gain new expert knowledge.

The current version of DeepSEED is specialized to optimize the expression level of a promoter due to the lack of other types of big data training sets with sufficient data. It can be extended to optimize other functional properties in the future when sufficient experimental data become available. For example, most of the DeepSEED-designed promoters achieve high induction rates by elevating the maximum expression level. However, some of the designed IPTG-inducible promoters also exhibited increased basal expression levels without induction, leading to dampened induction rates. To overcome these problems, future work needs to be done to generate sufficient task-specific experimental data, e.g., induction rate, with a massively parallel reporter assay 44 . Then DeepSEED can be trained to extract patterns related to the specific task. Using such a strategy, it is also possible to further apply the DeepSEED framework to design other types of synthetic genetic elements in a variety of organisms.


## Online Methods


## Bacterial strain and plasmids

All bacterial transformations and fluorescence assays were performed in the E. coli strain trans5α [F-, φ80d, lacZΔM15, Δ(lacZYA-argF), U169, endA1, recA1, hsdR17(rk-, mk+), supE44λ-, thi-1, gyrA96, relA1, phoA]. All plasmid construction was carried out using the NEBuilder HiFi DNA assembly reaction according to standard Gibson assembly. All E. coli promoter constructs were cloned into the vector pTPR with a p15A origin of replication and chloramphenicol resistance. A terminator DT5 was inserted at the 5’ end of the E. coli promoter to avoid the influence of the upstream sequence, and the insulator Riboj was inserted at the 3’ end of the promoter to ensure that the same transcript was produced. The ribosomal binding site sequence BBA_B0034 was used at the 5’ end of the sfgfp gene. Double terminators BBa_B0015 were used to terminate sfgfp gene transcription. For IPTG-inducible promoter constructs, an additional LacI protein expression cassette was inserted at the 5’ end of terminator DT5 in the opposite reading direction. For the Dox-inducible two-plasmid system, pwx156 contains the reverse tetracycline-controlled transactivator (rtTA), and pwx158 contains the Dox-inducible promoter to express EYFP. The designed Dox-inducible promoters replaced the original promoter sequence for activity measurement. The detailed sequences of the plasmids used in this article are provided in Supplementary Table S2.


## Cell line and transfection

HEK293 (293-H) cell line was used to test the Dox-inducible system from Invitrogen. HEK293 cells were cultured in Dulbecco’s modified eagle medium (DMEM) with 4.5 g/L glucose (GIBCO, 11965118) supplemented with 10% FBS (GIBCO, 16000-044), 1x NEAA (GIBCO, 11140050), and 0.5x penicillin-streptomycin (Solarbio, P1400) at 37°C and 5% CO2. Lipofectamine LTX and PLUS Reagent (Invitrogen, 15338100) were used for transfection according to the manufacturer’s protocol. In transfection experiments, approximately ∼1.8*10 5 HEK293 cells with 1 mL culture medium were seeded into each well of 12-well plates to be 70-90% confluent after being grown for ∼24 h. For the observation of Dox-inducible systems, transfection with 600 ng of the plasmids carrying design promoters with expression cassette and 600 ng of the plasmids carrying the reverse tetracycline controlled transactivator (rtTA) gene were performed in the wells of a 12-well plate. Before transfection, the culture medium containing 1 µg/ml Dox was used to induce the expression of the promoter. Cells were harvested 24 h after transfection before flow cytometry analysis.


## Assay of E. coli promoter strength

The strain containing the target promoter plasmid was cultured overnight (16 hours) in 5 ml LB medium supplemented with 50 µg/ml chloramphenicol at 37°C in a shaker at 220 rpm for promoter activity validation. The overnight cultures were diluted 1:100 in fresh Luria–Bertani (LB) medium supplemented with 50 µg/ml chloramphenicol in triplicate. For inducible promoters, a final concentration of 0.1 mM IPTG was added to the medium when diluted. After incubating for another 6 hours, 150 ul of culture was added to a flat-bottomed 96-well microplate (Corning 3603), and the measurements of the optical density at 600 nm (OD600) and fluorescence (relative fluorescence units [RFU]; excitation at 485 nm and emission at 520 nm) were repeated with the Varioskan Flash (Thermo). The background fluorescence was measured using 150 µl fresh LB medium and a strain harboring a promoterless plasmid. The strength of the promoter was defined as the average fluorescence/OD600 after subtracting background fluorescence. All the constitutive and IPTG-inducible promoter sequences with their promoter activity in E. coli were shown in Supplementary Table S1.


## Flow cytometry and data analysis

Cells were trypsinized 24 h after transfection and were then centrifuged at 300 × g for 5 min at room temperature. Then, the cells were washed with phosphate-buffered saline (PBS) once and resuspended in 1x PBS in a total volume of 400 µl. Next, the cells were analyzed using LSRFortessa (BD Biosciences). The excitation lasers (Ex), emission filters (Em), and photomultiplier tube (PMT) voltage used for respective fluorescent protein measurements are as follows: TagBFP (Ex: 405 nm laser, Em: 450/50 filter, PMT: 350 V). EYFP (Ex: 488 nm laser, Em: 530/30 filter, PMT: 200 V). For each sample, ∼1*10 6 cell events were collected for downstream analysis. For data analysis, raw data were filtered through the FlowAI plugin to remove bad-quality data. Cells with a TagBFP intensity between 1*10 4 ∼5*10 4 were selected containing the proper concentration of rtTA proteins. The EYFP mean was the activity of the designed promoters. Three independent biological replicates were performed for each promoter. All the Dox-inducible promoter sequences with their promoter activity in the HEK293 cell line were shown in Supplementary Table S1.


## Experimental dataset for model training

Three high-throughput datasets were used for training the DeepSEED model. A detailed description of datasets and training data generation are as follows:

This dataset was obtained from Johns et al 31 . Briefly, the author defined the regulatory sequence as 165 bp upstream of the gene start codon. The regulatory library was cloned into a p15A vector and transformed into E. coli MG1655. RNA-seq was performed to measure the activity of each sequence. The RNA-seq dataset contained a total of 29249 regulatory sequences from 184 prokaryotic genomes. The 165 bp sequences with the activity label were used in the training process of both constitutive and inducible E. coli promoter design.

This dataset was obtained from Wang et al. 40 The dataset contains enhancer sequences from a large number of human cell types. From the HEK293 cell line dataset, we randomly obtained 150 bp sequences in each enhancer region and finally got a total of 26,604 enhancer sequences to train the generator in the Dox-inducible promoter design task.

This dataset was obtained from Ernst et al. 45 The dataset targets 15,720 regulatory regions and tiles at 5-nucleotide resolution in two human cell types. The RNA-seq dataset was used to train the predictors in the Dox-inducible promoter design.


## Promoter design approach

The promoter design problem can be formulated from the probability perspective. The designed sequence is denoted as s ∼ p s , where p s represents the natural sequence distribution. To find a sequence compatible with the targeted property T , we maximize:

Expert knowledge determines motifs related to target properties, which we note as m . Other regions are defined as flanking regions and can be denoted as f . Then, the designed sequence can be split into:

Therefore, our objective can be written as follows:

The first factor refers to the process of assigning ‘seed’ sequences compatible with the target property according to expert knowledge. The second factor represents the flanking region distribution conditioned on ‘seed’ sequences and the property. We first optimized the first term and then optimized the second term fixing m at the optimal value.


## Objective function

The maximization of the first factor is achieved by selecting the strong motifs responsible for the desired property, such as high or inducible transcriptional activity, according to curated observations and discoveries from laborious biology experiments. These motifs were assigned with the highest confidence, resulting in defined sequences and positions. One benefit of determining unique motifs here was to simplify the objective by reducing the optimizable variables to only flanking regions f . We denote the assigned motifs as m ∗ ; then, the objective is to maximize:

Since m ∗ has been decided in the previous section, according to the Bayes rule in probability theory:

We use p f|m* to denote the natural distributions of flanking regions conditioned on m ∗ . Suppose that there are K kinds of flanking region combinations f 1 …, f K .

Notably, K is extremely large; for example, K = 4 100 when the length of concatenated flanking regions is 100 bp. To approximate p f|m , a generative neural network G was trained to approximate the sample distribution, i.e., p g ∼ p f|m ∗, where

where z is a latent variable in the generative model.

Given the large search space, we narrow it to the output sequences of G . To simplify this equation, all flanking regions generated by G are treated as equivalently important, with the probability of p 0 , while the probability of other combinations is zero. Therefore,

where the term P ( T | G ( m ∗ , z ), m ∗ ) is the probability of the target property given the generated sequence. We use F to denote that the predictive model of properties T and F is trained separately. When optimizing to enhance the property, the objective function is:


## DeepSEED generative and predictive networks

The flanking regions are generated through the generator G while preserving predetermined motifs. The input is the concatenation of m ∗ and z , and then we feed forward the input to a linear layer, and the results are reshaped into X m ∈ R n×d k , where n represents the number of samples and d k denotes the channels. To embed the long-range dependency between regions into the network, we utilize the multi-head attention mechanism to learn the genetic element semantics in both the generator and discriminator models. The multi-head attention operation can be written as:

where we denote the learnable parameters as A i Q , A i K , A i V . After passing one attention layer, two resblock layers with convolution operations are added to further extract features. The WGAN-GP architecture is chosen to alleviate mode collapse during the training process. Let us define the discriminator in cGANs as D . The loss function of cGANs can be described as follows:

Following similar tasks in image generation such as Pix2Pix 24 , we add one L1 loss, which can be written as:

The final optimizing object in implicit pattern learning is:

We take E. coli constitutive promoter design as an example. The training dataset contains 165 bp functional E. coli promoters with different TSSs from the library. We filtered these promoters by finding the regions from distal to TSS larger than 75 bp, finding promoters restricting -10 and -35 regions to 1-21 bp and 25-45 bp upstream of TSS with the spacer region length ranging from 10-24 bp. The input of the DeepSEED generator is the combination of one-hot sequence encodings with determined motifs, where regions other than these motifs are set to zero, and a 165-dim latent code vector. For the discriminator, the input is the concatenate of one-hot encodings with motifs and the generated sequences. The batch size of the training samples is 32, and we trained the model for 50000 batches with the Adam optimization method. The learning rate, beta1, and beta2 were set to 0.0001, 0.5, and 0.9, respectively.

Accurate predictions of target properties are crucial to optimize the flanking regions. Predictions of biological properties with a deep learning model often suffer from the overfitting problem, requiring a carefully designed network architecture. The first layer of the DeepSEED prediction model was 1d convolutional kernels with 64 output channels to capture regional information. Then, we added the long short-term memory (LSTM) 46 architecture to capture the relationships between regions. To extract potential long-range relationship factors leading to the target properties, we adopted the DenseNet 47 architecture to efficiently improve the network depth. We set 4 dense blocks with 2, 2, 4, and 2 dense layers in each block. The growth rate was set to 32. Each dense layer contains two convolutional layers, the kernel sizes of 1 and 3. Finally, we added one fully connected layer to predict the property of interest (Supplementary Notes).


## Optimization through the genetic algorithm

As mentioned above, the objective function is:

We utilized the genetic algorithm (GA) to optimize the objective function. The GA 48 module in the sko Python package was adopted to implement the genetic algorithm. The optimization process using the genetic algorithm from step t to t+1 can be written as:

We set the number of seeds in GA to 5*1024 with a mutation probability of 0.005. We set the epochs of GA optimization to 100 for each task. We used the “vectorization” mode in the sko package to facilitate optimization.


## DNA shape analysis

Four kinds of DNA shape, minor groove width (MGW), roll, propeller twist (ProT) and helix twist (HelT), were estimated by the prediction model 27 . In Fig. 2e , DNA shapes on the 5’ end of the ‘TATAAT’ motif and ‘TATAAA’ motif were estimated by the model, then the distributions of four kinds of DNA shapes were calculated. In Fig. 2b and 3d , the DNA shapes of high- and low-activity promoters in the training datasets, Control1 group promoters, Control2 group promoters, and DeepSEED group promoters were calculated. Then, four kinds of DNA shapes of each promoter were combined to form a DNA shape feature vector. All the feature vectors were encoded by the unsupervised learning model Deepinfomax 49 , and then the encoded features were projected into 2-dimensional space by the dimension reduction algorithm t-SNE.


## Second promoter finding

To prevent the model from generating the second promoter in a 165 bp sequence, we checked the RNA polymerase binding possibility in a sequence. To be more specific, the −10 motif, −35 motif and their spacing length were taken into consideration as ‘promoter structure’. The −10 motif and −35 motif were combined together with a 17 bp spacer sequence, and then the sequence was scanned with Find Individual Motif Occurrences (FIMO) 50 to check whether the combined motif appeared in the sequence. The p-value of the combined motif matched in the position of the sequences is shown in the figure (Supplementary Fig. S10).


## Saliency map analysis

We calculated saliency map features 25 of 2,000 functional sequences by using the predictor model. The saliency map of each sequence represents the contribution of each nucleotide to the predicted activity. Then, the 2,000 saliency maps were clustered into seven clusters by k-means. Then, 30 sequences in each cluster were randomly selected to represent the cluster (Supplementary Fig. S6).


## Semantic sequence space

The semantic sequence space was defined as the space representing the semantic information directly obtained from the DNA sequence. A total of 2,000 natural promoter sequences in E. coli , 2,000 promoter sequences generated by DeepSEED, and 14,700 promoter sequences from 147 different prokaryotic species 31 were used to define the semantic sequence space. All the sequences were first encoded by Deepinfomax 49 , and then the encoded features were projected into 2-dimensional space by the dimension reduction algorithm t-SNE (Supplementary Fig. S4b).


## Sequence similar diversity

The sequence similar diversity is defined as the edit distance distribution between sequences from different sequence groups. 60 random sequences, 60 natural sequences, and 60 cGAN-generated sequences in E. coli were selected. The random sequence similar diversity was calculated by the edit distance between each sequence in the random sequence group and each sequence in the natural sequence group as well as the cGAN-generated sequence group. Then all the calculated edit distances formed the edit distance distribution, which could be written as:

Where P r represents the edit distance distribution of random sequence group, ed represents the edit distance calculation, r represents sequences in the random sequence group, g represents sequences in the generated sequence group and n represents sequences in the natural sequence group. The natural and cGAN-generated sequence similar diversity were calculated in the same way (Supplementary Fig. S4a).


## Data availability

All data are available in Supplementary Table S1 and S2.


## Code availability

The computer source code is available from the public GitHub repository at https://github.com/WangLabTHU/deepseed .


## Funding

This work was supported by the National Key R&D Program of China (No. 2020YFA0906900), National Natural Science Foundation of China (No. 62250007, 62225307, 61721003), and the grant from the Guoqiang Institute, Tsinghua University.


## Competing interests

Tsinghua University has filed patent applications on behalf of X.W.W., H.C.W., H.W.X., P.C.Z. and W.L., pertaining to the AI-aided promoter design framework DeepSEED. The remaining authors declare no competing interests.


## Acknowledgements

X.W.W., P.C.Z., H.C.W. and H.W.X. conceived the study. H.C.W. and H.W.X implemented in silico designs. P.C.Z. and W.L. designed the experiments. P.C.Z. performed the experiments and analyzed the data. P.C.Z., H.C.W. and H.W.X. wrote the manuscript. We also thank Ye Wang for the positive discussion.


## Footnotes

↵ * Equally contributed