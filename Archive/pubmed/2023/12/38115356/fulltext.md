# Integrating network pharmacology and experimental verification to explore the mechanism of Tripterygium wilfordii in ankylosing spondylitis


## Objective:
  This study aimed to validate the mechanism of triptolide in treating ankylosing spondylitis (AS) through network pharmacology, molecular docking, and in vitro experiments.


## Methods:
  We gathered AS-related genes using databases including DrugBank, OMIM, GeneCards, TTD and DisGeNET. TCMSP database was used to collect Tripterygium wilfordii (TWHF)-related data. Additionally, the potential targets of TWHF in treating AS were predicted by consulting databases such as Venny, String, Cytoscape, and Cytohubba. Subsequently, a protein-protein interaction network was created and the gene ontology and Kyoto Encyclopedia of Genes and Genomes enrichment analysis were performed by metascape database. After selecting the most active ingredient of TWHF, molecular docking was performed to confirm the predicted results. Furthermore, we explore the potential mechanism of the most active ingredient of TWHF in the treatment of AS in vitro.


## Result:
  By integrating the results of network pharmacological analysis, 62 genes were found to be strongly associated with AS, such as STAT3, TNF, MMP9, VEGFA, CXCL8, PTGS2, etc. Triptolide (TP) is one of the most active ingredients in TWHF. The enrichment analysis indicated that 292 biological processes and 132 signaling pathways were involved, with the T helper 17 cells cell differentiation pathway as the key pathway. TP was selected for molecular docking and in vitro experiments. The molecular docking results indicated that TP had excellent affinity with 6 key targets. Further, flow cytometry, cell counting assay, and ELISA demonstrated that the serum level of IL-17 was higher in AS patients compared to XXX, and 25 μg/mL TP was the optimal intervention concentration. RT-qPCR and Western blotting further verified that TP could inhibit the activation of RORγt and the JAK2/STAT3 signaling pathway.


## Conclusion:
  In conclusion, based on network pharmacology, molecular docking, and experimental verification in vitro, we proposed that the TP can inhibit the activation of RORγt and the JAK2/STAT3 signaling pathway and inhibit the differentiation of T helper 17 cells cells. The article provide a theoretical basis for further development and utilization of TWHF in AS management.


## 1. Introduction
  Ankylosing spondylitis (AS), as a subtype of spondyloarthritis, which was characterized by inflammatory spondylitis, peripheral arthritis, and enthesitis.[1] Immune-mediated inflammation in the spine and sacroiliac joints are response for bone destruction, pathological bone formation, and subsequent ankylosis.[2] The global prevalence of AS is 0.1% to 0.4%, which is similar to rheumatoid arthritis.[3] The disease occurs mostly in young men, has a high disability rate, which seriously affects the quality of life with patients, and increases a huge burden on patients and society. Up to now, the drugs used for the treatment of AS mainly include nonsteroidal anti-inflammatory, traditional antirheumatic drugs, biologicals, and glucocorticoids.[4] However, these drugs do not fundamentally cure AS and have side effects that make patients unbearable.[5]

  Traditional Chinese herb Tripterygium wilfordii (TWHF) is a kind of woody vine in Celastraceae family with a long medicinal history and was first recorded in the Shennong Materia Medica in 100 B.C., which mainly distributed in Eastern and Southern China, Korea, and Japan.[6] It has reported that TWHF has the effects of detoxifying, relieving swelling and pain, activating blood circulation, and dispelling dampness, and it has been widely used in clinical practice. Previous studies have demonstrated that TWHF has an excellent effect on various diseases, such as cancer,[7] rheumatic disease,[7] and kidney disease.[8] In several clinical trials, TWHF has been shown to be effective in treating AS.[9] Moreover, it can inhibit proliferation and differentiation, as well as induce apoptosis of osteoblastic MC3T3E1 cells.[10] Nevertheless, the effect and mechanism of TWHF in managing and treating AS remains unclear.

  Network pharmacology emphasizes the analysis of the molecular mechanism between drugs and diseases from the perspective of systems biology.[11] It has been widely used in exploring the active components of traditional Chinese medicine and the interpretation of the overall mechanism, which provides a scientific method for studying the mechanism of traditional Chinese medicine applied to diseases. Molecular docking can verify the degree of binding affinity between targets and active ingredients of traditional Chinese medicine, so as to verify the reliability of the target.[9] This study aims to reveal the potential role of TWHF in treating AS through network pharmacology, molecular docking, and in vitro experiments. The flow chart is shown in Figure 1.


## 2. Materials and methods

### 2.1. Potential target genes of TWHF in the treatment of AS
  To evaluate the biological information of TWHF, oral bioavailability ≥ 40% and drug-likeness ≥ 0.18 were obtained from the TCMSP database (https://tcmspw.com/tcmsp.php).[12] Afterwards, all targets were converted into gene symbols standardized through the Uniprot database (https://www.uniprot.org/).[13] Untransformed genes were used in the Pubchem database (https://pubchem.ncbi.nlm.nih.gov/) to convert.[14]


### 2.2. Collection of AS related genes
  AS-related genes were collected from 5 databases, including: OMMI database (https://www.omim.org/) , DrugBank database (https://go.drugbank.com/), GeneCards database (https://www.genecards.org/), Therapeutic Target Database (http://db.idrblab.net/ttd/) and DisGeNET (https://www.disgenet.org/) with “ankylosing spondylitis” as keyword.[15,16]


### 2.3. Protein-protein interaction (PPI) network analysis
  Through, draw a Venn diagram was obtained by Venny 2.1.0 (https://bioinfogp.cnb.csic.es/tools/venny/), which the potential targets of TWHF and AS-related genes could be collected. Then, use the String database (https://string-db.org/) to analyze the targets and establish a PPI network. Further, the PPI network was imported to Cytoscape 3.7.2 software (http://www.cytoscape.org), and the maximal clique centrality was calculated by the Cytohubba tool.


### 2.4. Gene ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) enrichment analysis
  Based on the aforementioned data, GO and KEGG enrichment analysis were performed in the Metascape database (http://metascape.org/gp/index.html). The GO enrichment analysis includes cellular composition, biological process, and molecular function, nonetheless the KEGG analysis metabolic pathways. The top 10 enrichment results were analyzed by the Bioinformatic online tool (http:// bioinformatics.com.cn/).


### 2.5. Molecular docking
  The proteins corresponding to the top 5 essential genes were selected to dock with the most active component of TWHF to prove their affinity. The small molecule was obtained from TCMSP in “mol” format, and the protein structure was derived from the PDB database (https://www.rcsb.org/).[17] Using AutoDockTools 1.5.7 software (http://autodock.scripps.edu/)[18] to remove water molecules and different ligands, add hydrogen, and then add the charge to a protein molecule and set up a docking grid box at the center of the molecule. Then, using AutoDock Vina 1.1.2 software (http://vina.scripps.edu/)[19] to finish molecular docking and choose the conformation with the lowest binding energy. Saving the structure with the lowest binding energy conformation and the binding diagram was drawn by Pymol 2.2.0.


### 2.6. Study subjects
  Fifteen active patients were selected from Guang’anmen Hospital Department of Rheumatology. The clinical diagnosis was entirely based on the modified New York criteria. Active AS was defined as Bath AS disease activity index ≥ 4 points. Peripheral blood mononuclear cells (PBMCs) were collected from the 2 groups exposed to TP and DMSO. The research adheres to the Declaration of Helsinki. All subjects provided written informed consent.


### 2.7. PBMC preparation and study of drugs
  PBMCs were prepared by lymphocyte separation medium density gradient centrifugation. The lymphocyte separation medium (human) was from TIAN JIN HAO YANG BIOLOGICAL MANUFACTURE CO. (Tianjin, China). TP was from the China Institute of Food and Drug Control. DMSO was from Solarbio (Sigma, USA, D2650).


### 2.8. Flow cytometry
  T lymphocyte subsets were analyzed by flow cytometry (Mindray Bricyte E6, China). The cells were stained with anti-Human CD3 FITC (Product # 11-0037-42) and anti-Mouse CD4 FITC (Product # 11-0041-82) (eBioscience, USA). Intracellular IL-17 expression was examined by fluorescein isothiocyanate-labeled anti-IL-17 (Product # 11-7177-81) (eBioscience).


### 2.9. Cell counting assay
  PBMCs were harvested and seeded into 96-well plates at a density of 1 × 105 cells/µL and cultured in an environment containing 5% CO2 at 37ºC. Cells were incubated with TP (12.5–100 μg/mL) for 24 hours. Then, a 10-µL cell counting solution (Dojindo, Shanghai, China) was added to plates for 3 hours. And the absorbance at 450 nm was measured by a microplate reader. All experiments were done in triplicate.


### 2.10. ELISA
  Prepare all reagents, samples, and standards as instructed. Add 50 μL of standards or samples to wells. Add 50 μL of antibody cocktail to all wells. Incubate at room temperature for 1 hour. Each well was aspirated and washed 3 times with 350 μL 1X Wash Buffer PT. Add 100 μL TMB. Develop a Solution for each well and incubate for 10 minutes. Add 100 μL Stop Solution and read OD at 450 nm. The human IL-17a ELISA kit was purchased from Abcam (ab83688, Cambridge, UK).


### 2.11. Western blotting
  The antibodies for western blotting were as follows: anti-RORC (1:250, SAB1100574) was from Sigma, and JAK2 (Product # 3230), and phospho-JAK2 antibody (Product # 3776), STAT3 (Product # 12640) and phospho-STAT3 antibody (Product # 9145), and GAPDH antibody (Product # 5174) were purchased from Cell Signaling Technology. Secondary antibodies were bought from ZSGB-BIO (Beijing, China). All experiments were conducted in triplicate.


### 2.12. Real-time PCR
  Total RNA was extracted using ultrapure RNA extraction kit, separated on 1% agarose gel, and the reverse transcribed experiment was carried out by commercial kit (Applied Biosystems, USA). amplified for 45 cycles by iTaqTM Universal SYBR Green Supermix (Bio-Rad, USA). The mRNA expressions were normalized by GAPDH. The primers are listed in Table 1. The reaction conditions were as follows: 95ºC for 10 minutes, 40 cycles at 95ºC for 15 seconds, 60ºC for the 60 seconds, and 72ºC for 15 seconds. Relative expression of candidate genes was quantified with the 2−ΔΔCt method.


### 2.13. Statistical analysis
  Data following normal distribution are expressed as mean ± standard deviation and analyzed using one-way ANOVA followed by Tukey test for pairwise comparison. All statistical analyses were conducted using GraphPad Prism Version 6.00 for Windows. Statistical significance was set at P < .05.


## 3. Results

### 3.1. Target screening of TWHF and AS
  A total of 28 compounds and 137 potential targets were obtained by TCMSP and converted into gene symbols standardized through the Uniprot and Pubchem databases, removing duplicates. The maximal clique centrality was calculated by the Cytohubba tool to Screening of active components. Kaempferol, triptolide, and beta-sitosterol are the top 3 active ingredients (Table 2, Fig. 2). Then 312 genes of AS were collected from the OMMI database, 104 genes from the DrugBank database, 113 genes from the GeneCards database, 3 genes from TTD, and 710 genes from the DisGeNET database. Totally, 2631 genes of AS were obtained after removing duplicates.


### 3.2. PPI network analysis
  The TWHF targets were intersected with the AS genes to obtain the essential genes and plotted a Venn diagram (Fig. 3). Sixty-two common genes were uploaded to the String database to produce the PPI network. And then, the results were imported into Cytoscape 3.7.2 and calculated by the Cytohubba tool (Fig. 4). The core 6 targets are TNF, VEGFA, STAT3, CXCL8, PTGS2, and MMP9 (Table 3).


### 3.3. GO and KEGG enrichment analysis
  There are 292 GO items were collected by Metascape database, and the KEGG entries were 137. The enrichment dot bubble and GO term were drawn by the bioinformatic online tool (Fig. 5). The results show that the most significant molecular function included nuclear receptor activity, heme binding, protein homodimerization activity, cytokine activity, Hsp90 protein binding, and so on. The biological processes mainly included inflammatory response, response to lipopolysaccharide, positive regulation of cell migration, cellular response to nitrogen compound, xenobiotic stimulus, and so on. In contrast, the Cellular Components are primarily involved in the membrane raft external side of the plasma membrane, extracellular matrix, transcription regulator complex, and receptor complex. KEGG results showed that genes shared by TWHF and AS were mainly enriched in the T helper 17 cells (Th17) cell differentiation (Fig. 5), pathways in cancer, and VEGF signaling pathway.


### 3.4. Molecular docking analysis
  They are importing the 6 core targets into the AutoDuck tools and AutoDuck vina to dock with the most active ingredients of TWHF and TP. Affinity was the score used by the software to calculate the binding ability. It is generally believed that affinity < −7 kcal/mol indicates a more substantial binding activity.[20] The results were shown in Table 4. The affinity of 6 core targets is all < −7 kcal/mol. The docking diagrams of AS and genes were competed with Pymol software (Fig. 6). In addition, we found the hydrogen bonds formed between molecules and represented by yellow dotted lines in the diagrams.


### 3.5. Increased frequency of IL-17–positive CD4 + T cells in PBMCs from AS patients
  The percentage of Th17 in PBMC was 3.30%, 2.93%, and 3.14% in the AS patients vs 2.05% and 2.27% in healthy subjects, with a trend of higher IL-17 positive CD4+ T cells in active AS patients (Fig. 7A).


### 3.6. Dose-response curves of TP
  In the pilot experiments using cell counting assay after 24 hours exposure to PBMCs, IC50 was 73.54-μg/mL for TP (Fig. 7B). Subsequent experiments in PBMCs showed a significant reduction of IL-17 expression by 25-μg/mL TP (P < .05, Fig. 7C). We, therefore, used 25-μg/mL TP for all subsequent experiments.


### 3.7. Effect of TP on Th17 differentiation
  TP (25-μg/mL) significantly reduced the mRNA and protein expression of RORc (P < .05 for both; Fig. 8A), and also inhibited the activation of the JAK2/STAT3 signaling pathway assisted by total expression and phosphorylation level of the signal molecules (JAK2, STAT3, pJAK2, pSTAT3) were significantly reduced (P < .05 for all molecules with TP; Fig. 8 2B/2C). There was no significant difference in the mRNA levels of JAK2 and STAT3 in the TP and control groups (P > .05, Fig. 8 2B/2C).


## 4. Discussion
  AS is a worldwide refractory autoimmune disease with complex pathogenesis. Current therapeutic strategies mainly focused on inflammation control. TWHF is an effective herbal for the treatment of various inflammatory and autoimmune diseases, including rheumatoid arthritis, systemic lupus erythematosus, psoriatic arthritis, and Behcet disease.[21,22] Traditional Chinese medicine has the characteristics of multiple active ingredients and multiple targets. Identifying its mechanism of action is of great significance for treating diseases and developing new drugs.[23] This study explored the core active ingredients of TWHF and the key targets and pathways for treating AS through network pharmacology. Their reliability was verified through molecular docking and experiments.

  TWHF could decrease erythrocyte sedimentation rate, C-reactive protein, Spinal Pain Visual Analog Score, bath AS Functional Index, and Bath AS disease activity index significantly,[9] but the mechanism remains unclear. Through network pharmacology, the biological processes mainly included inflammatory response, and the Th17 differentiation pathway was further considered as the core pathological mechanism of AS. We found that not only is the Th17 differentiation pathway at the top of the KEGG pathways, but STAT3 of the Th17 differentiation pathway is still one of the core targets of the PPI network.

  Th17 is the core effector cell mediating AS inflammation, and the initial migration of CD4 + T cells to Th17 differentiation initiates AS inflammation. It is widely accepted that the differentiation of Th17 cells plays a crucial role in AS. IL-17 secreted by Th17 cells at the lesion sites recruits monocytes and neutrophils, aggravating inflammatory response. RORγt is a key transcription factor that promotes the differentiation of CD4 + T cells into Th17 cells and increases the capacity of Th17 cells to produce IL-17.[24] Multiple signal pathways, including the JAK/STAT signal pathway, the Notch signal pathway, the NF-B signal pathway, and the AKT/mTOR signal pathway, have been implicated in Th17 cell differentiation. STAT3, a downstream regulator of the JAK/STAT signal pathway, binds to RORγt and then promotes Th17 differentiation.[25] Then we used molecular docking to verify that 6 core targets, including STAT3, had a higher binding degree with AS.

  Triptolide is one of the most active ingredients in TWHF,[26] which was also confirmed by the results of network pharmacology. Therefore, we investigated whether TP can inhibit the differentiation of Th17 in AS. In the study, we selected 25-μg/mL TP, with minimal effect on cell proliferation toxicity. We found that TP could suppress the expression of transcription factor RORc and the activation of the JAK2/STAT3 signaling pathway, thereby supporting the role of JAK2/STAT3 signaling pathway in Th17 cell differentiation. It is consistent with the results of network pharmacology and molecular docking.

  There is no cure for AS, and the treat-to-target strategy is accepted worldwide.[4] The primary purpose of treat-to-target is to reduce disease activity and control inflammation to improve patients’ quality of life, improve motor function, delay bone structural damage, and reduce disability.[27] Inhibiting inflammation early in the disease suppress disease progression and protect the function of joints.[28] Abnormal differentiation of Th17 and excessive production of proinflammatory cytokines are critical parts of immune dysfunction in AS. RORc induces the transcription of several key cytokines and is essential for Th17 differentiation.[28–30] The JAK/STAT pathway plays a vital role in the activation of several transcription factors, including T-box transcription factor TBX21 (T-bet), GATA binding protein 3 (GATA-3), RORγt and Foxp3.[31] STAT3 is required for RORc activation and Th17 secretion of IL-17.[25] It has also posed that the JAK inhibitor can serve as the fourth-line therapy other than NSAIDs, TNF inhibitors, and IL-17 inhibitors to control inflammation.[32] Nevertheless, the use of JAK inhibitors increases the risk of major cardiovascular events (such as heart attack or stroke), cancer, blood clots, and even death.[27] Consequently, TP can inhibit the activation of RORγt and the JAK2/STAT3 signaling pathways, inhibit the differentiation of Th17 cells, and thus control inflammation.TP may provide a new treatment strategy for AS.


## 5. Conclusions
  In summary, we verified that TWHF inhibits the activation of RORγt and the JAK2/STAT3 signaling pathway and inhibits the differentiation of Th17 cells through network pharmacology, molecular docking, and experimental verification. In conclusion, this study is helpful to elucidate the related molecular mechanism of TWHF in the treatment of AS, and provide methodological reference for finding new therapeutic candidates from Chinese herbal medicines.


## Acknowledgments
  We thank the Stem Cell Center and the Medical Molecular Biology Laboratory of Peking University Health Science Center for providing technical support.


## Author contributions
  Conceptualization: Yuening Chen, Xinning Qu, Hongxiao Liu.

  Data curation: Yuening Chen, Zhaoyi Liu, Qing Yu.

  Formal analysis: Zhaoyi Liu, Qing Yu.

  Funding acquisition: Hongxiao Liu.

  Methodology: Yuening Chen, Xinning Qu.

  Resources: Qing Yu, Xinning Qu.

  Software: Yuening Chen, Zhaoyi Liu, Xinning Qu.

  Supervision: Hongxiao Liu.

  Validation: Qing Yu, Hongxiao Liu.

  Writing – original draft: Yuening Chen, Zhaoyi Liu.

  Writing – review & editing: Hongxiao Liu.