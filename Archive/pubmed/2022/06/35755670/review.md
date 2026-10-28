## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report identification of a novel protein interaction network involving the E3 ligase BTSL1, bHLH subgroup IVc transcription factors, and POPEYE, modulated by the small protein FEP3/IMA1. They propose that FEP3/IMA1 acts as an effector that attenuates BTSL1-bHLH interactions, thereby promoting iron uptake, and they map interaction sites using deletion analysis and computational modeling.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Concluding Remarks, Materials and Methods, Accession Numbers, Data Availability Statement, Author Contributions, Conflict of Interest, Publisher's Note, Funding, Supplementary Material description, Acknowledgements
- **Missing materials affecting confidence** Supplementary figures and tables (Supplementary Figures 1-14, Supplementary Tables 1-2) are referenced but not provided; raw data for Y2H assays, quantitative β-galactosidase measurements, and statistical analyses are not fully accessible; details of AlphaFold/HADDOCK parameters and validation metrics are incomplete

## Reviewer

### **Overall assessment**
This manuscript presents a systematic yeast two-hybrid screen that identifies a novel interaction network centered on BTSL1, bHLH IVc transcription factors, and FEP3/IMA1. The work addresses an important open question in plant iron homeostasis: how positive and negative regulators coordinate to control iron acquisition. The authors provide evidence for a new mechanism whereby FEP3/IMA1 acts as an effector that attenuates BTSL1-bHLH interactions. The deletion mapping and computational modeling are valuable contributions. However, the central mechanistic claim that FEP3/IMA1 modulates BTSL1-bHLH interactions in planta is not fully established from the provided evidence, primarily because the authors acknowledge difficulties in detecting BTSL1 protein in plant cells and the key functional experiments rely on overexpression lines rather than loss-of-function or complementation approaches. The manuscript is technically sound in its Y2H methodology but would benefit from stronger in planta validation.

### **Who would be interested in the results, and why**
Plant molecular biologists studying iron homeostasis, particularly those focused on regulatory networks and protein-protein interactions. Researchers working on bHLH transcription factor cascades, E3 ligase function, and small protein effectors will find the interaction map and mechanistic model of interest. The work also has relevance for crop improvement efforts aimed at iron biofortification, as understanding the regulatory network could inform breeding strategies for iron-efficient crops. The structural modeling approach may interest computational biologists working on protein interaction prediction.

### **Major strengths**
- Systematic Y2H screening approach with 23 candidate proteins, providing a broad interaction map
- Identification of a novel interaction network (BTSL1-bHLH IVc-FEP3/IMA1) that integrates previously known components
- Detailed deletion mapping that localizes interaction sites to specific regions
- Combination of experimental and computational approaches (Y2H, AlphaFold, HADDOCK) to support interaction models
- Phenotypic characterization of FEP3 overexpression lines and btsl1 btsl2 mutants provides physiological context
- Clear presentation of a working model that can guide future experiments

### **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** "FEP3/IMA1 attenuated interaction of BTSL1 and bHLH proteins in a yeast three-hybrid assay, in line with physiological data pointing to enhanced Fe acquisition and allocation in FEP3/IMA1 overexpression and btsl1 btsl2 mutant plants"
- **Evidence pointer** Results section "FEP3/IMA1 Attenuated the Interaction of BTSL1 With PYE and bHLH IVC Transcription Factors, Providing Evidence for an Effector Interaction"; Figure 7
- **Concern** The central claim that FEP3/IMA1 acts as an effector modulating BTSL1-bHLH interactions in planta is primarily supported by Y3H data and phenotypic correlations. The authors acknowledge that BTSL1 protein could not be reliably detected in plant cells, and the key functional evidence comes from overexpression lines rather than loss-of-function or complementation experiments. The Y3H assay, while informative, is a heterologous system that may not fully recapitulate the in planta context, particularly given the authors' own observation that FEP3/IMA1 protein levels were not regulated by methionine as expected in the Y3H system.
- **Why it matters** The mechanistic model proposed requires direct evidence that FEP3/IMA1 modulates BTSL1-bHLH interactions in the native plant context. Without this, the physiological relevance of the observed Y3H interactions remains correlative rather than causal.
- **Resolution test** Provide in planta evidence for the FEP3/IMA1-BTSL1 interaction and its functional consequence, such as co-immunoprecipitation from plant extracts, or genetic epistasis analysis showing that fep3/ima1 mutations suppress or enhance btsl1 phenotypes. Alternatively, demonstrate that FEP3/IMA1 affects BTSL1 protein stability or BTSL1-bHLH complex formation in a plant-based system.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation of interaction data
- **Claim pointer** "5–6% of tested interactions were positive and they comprised 20 heterodimeric and six homodimeric interactions"
- **Evidence pointer** Results section "A Targeted Yeast Two-Hybrid Screen Uncovered the BTSL1-bHLH-FEP3/IMA1 Interactome"; Figure 1; Supplementary Figures 1-2
- **Concern** The Y2H screen results are presented as a summary, but the supplementary data showing individual interaction tests are not provided in the manuscript text. The authors note that some interactions differed from previous reports (e.g., PYE-PYE positive here but negative in Selote et al., 2015; BTS-FEP3/IMA1 negative here but positive in Li et al., 2021), and attribute these differences to experimental conditions. However, without access to the full interaction matrix and appropriate controls for each pair, it is difficult to assess the reliability of the screen and the specificity of the reported interactions.
- **Why it matters** The interaction network is the foundation of the manuscript's conclusions. If the Y2H data are not fully transparent and reproducible, the downstream interpretations and mechanistic model are compromised.
- **Resolution test** Provide the complete interaction matrix with all tested pairs, including negative controls and the specific 3-AT concentrations used for each pair. Include quantification of growth assays and, where possible, confirm key interactions using an independent method such as co-immunoprecipitation or in vitro pull-down.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance of mapped interaction sites
- **Claim pointer** "The 14-aa M-C site located close to the BTSL1 E3 RING domain is needed for interaction with FEP3/IMA1, ILR3 and bHLH104-C"
- **Evidence pointer** Results section "Interaction Sites Between BTSL1, bHLH Proteins, and FEP3/IMA1 Were Mapped"; Figures 3-5
- **Concern** The deletion mapping identifies regions required for interaction, but the functional significance of these specific residues is not tested. The authors show that deleting the M-C site abolishes interactions, but do not demonstrate that this region is important for BTSL1 function in planta. The computational docking predictions, while consistent with experimental data, are not validated by mutagenesis of specific predicted contact residues.
- **Why it matters** Identifying interaction sites is valuable, but the physiological relevance of these sites needs to be established. Without functional validation, the structural model remains speculative and the potential for engineering BTSL1 or FEP3/IMA1 for crop improvement is not demonstrated.
- **Resolution test** Generate point mutations in the M-C site and predicted contact residues, and test their effects on BTSL1 function in planta, such as complementation of btsl1 btsl2 phenotypes or effects on iron accumulation. Alternatively, test whether FEP3/IMA1 variants with altered C-terminal sequences lose the ability to modulate BTSL1-bHLH interactions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor of physiological data
- **Claim pointer** "FEP3-Ox plants and btsl1 btsl2 mutants had increased Fe contents per dry weight in seeds, longer roots than wild type at –Fe and partly also at +Fe"
- **Evidence pointer** Results section "FEP3/IMA1 Attenuated the Interaction of BTSL1 With bHLH IVC Transcription Factors, Providing Evidence for an Effector Interaction"; Supplementary Figures 9-12
- **Concern** The physiological data supporting the functional relevance of the identified interactions are presented in supplementary figures without full statistical details in the main text. The authors mention specific significant differences but do not provide effect sizes, exact p-values, or information about multiple testing corrections. The number of biological replicates for each experiment is stated to be in the figure legends, but these are not accessible in the provided text.
- **Why it matters** The phenotypic correlations between FEP3 overexpression and btsl1 btsl2 mutants are used to support the mechanistic model. Without rigorous statistical reporting, the strength of this evidence cannot be fully evaluated.
- **Resolution test** Provide complete statistical details for all physiological experiments, including exact p-values, effect sizes, and information about experimental design and replication. Consider presenting key phenotypic data in the main figures rather than relegating them to supplementary material.

### **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methodology
- **Affected element** Y2H screening conditions
- **Evidence pointer** Materials and Methods "Yeast Assays"
- **Issue** The description of the Y2H screen mentions that 3-AT concentrations were adjusted individually, but the specific concentrations and criteria for determining positive interactions are not clearly stated.
- **Required correction** Provide a clear description of the screening conditions, including 3-AT concentrations used, the threshold for scoring positive interactions, and how auto-activation was assessed for each construct.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation of computational methods
- **Affected element** AlphaFold and HADDOCK parameters
- **Evidence pointer** Materials and Methods "Protein Structure Prediction and Molecular Docking"
- **Issue** The description of computational methods is brief and lacks key parameters such as AlphaFold model confidence scores, number of models generated, and HADDOCK scoring details.
- **Required correction** Provide more detailed methods for structure prediction and docking, including confidence metrics (e.g., pLDDT scores) and validation of the docking results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of localization data
- **Affected element** Subcellular localization experiments
- **Evidence pointer** Results section "Interaction Sites Between BTSL1, bHLH Proteins, and FEP3/IMA1 Were Mapped"; Supplementary Figures 4-5
- **Issue** The authors report differential localization of BTSL1 and BTSL2 but the functional implications of these differences are not discussed in depth.
- **Required correction** Expand the discussion of how the observed localization patterns relate to the proposed mechanism of FEP3/IMA1 action and whether localization changes are iron-dependent.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Gene expression analysis
- **Affected element** RT-qPCR data
- **Evidence pointer** Materials and Methods "Gene Expression Analysis by RT-qPCR"; Supplementary Figures 11-12
- **Issue** The choice of reference genes for normalization is not stated, and the authors do not discuss potential iron-dependent changes in reference gene expression.
- **Required correction** State the reference genes used and provide validation of their stability under the experimental conditions tested.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Main figures
- **Evidence pointer** Figures 1-7
- **Issue** Several key results are presented only in supplementary figures, making it difficult for readers to assess the main findings without accessing supplementary materials.
- **Required correction** Consider moving key data points, such as representative Y2H results and the most important physiological phenotypes, to main figures.

### **Technical failings that need to be addressed before the case is established**
- R1-M1: Lack of in planta validation of the FEP3/IMA1-BTSL1 interaction and its functional consequence
- R1-M2: Incomplete transparency of Y2H screening data and conditions
- R1-M3: No functional validation of mapped interaction sites through mutagenesis

### **Assessment against Nature-style criteria**

**Originality:** The manuscript identifies a novel interaction network and proposes a new mechanism for FEP3/IMA1 action. While the components were individually known, their integration into a coherent model with mapped interaction sites is original. The work extends recent findings on FEP/IMA-BTS interactions.

**Scientific importance:** The work addresses a fundamental question in plant iron homeostasis: how positive and negative regulators coordinate. The proposed mechanism has implications for understanding iron sensing and signaling, and could inform crop improvement strategies. However, the importance is somewhat limited by the lack of in planta validation of the central mechanism.

**Interdisciplinary readership:** The work is primarily of interest to plant molecular biologists and iron homeostasis researchers. The structural modeling component may attract computational biologists, but the overall scope is relatively narrow. The potential applications to crop biofortification could broaden interest.

**Technical soundness:** The Y2H methodology is well-established and carefully executed, with appropriate controls and reciprocal testing. The deletion mapping is systematic. The computational approaches are appropriate but would benefit from more detailed validation. The main technical weakness is the reliance on heterologous systems and the acknowledged difficulty in detecting BTSL1 in plant cells.

**Readability for nonspecialists:** The manuscript is clearly written and the logic is easy to follow. The figures, as described, appear to support the text. However, the heavy reliance on supplementary materials for key data makes it difficult for readers to fully evaluate the findings without accessing additional resources.

### **Recommendation posture**
Supportive if technical concerns are resolved. The manuscript presents a valuable interaction map and a plausible mechanistic model, but the central claim that FEP3/IMA1 modulates BTSL1-bHLH interactions in planta requires stronger evidence. The authors should provide in planta validation of the key interaction and its functional significance, and improve transparency of the Y2H screening data. With these revisions, the work would make a solid contribution to the field of plant iron homeostasis.

## Risk / unsupported claims
- The claim that FEP3/IMA1 acts as an effector protein modulating BTSL1-bHLH interactions in planta is not fully supported by the provided evidence; Y3H data and phenotypic correlations are suggestive but not conclusive.
- The statement that "FEP3/IMA1 attenuated interaction of BTSL1 and bHLH proteins" is supported only in the Y3H system, not in plant cells.
- The prediction that "bHLH proteins bind BTSL1 at two interfaces" is based on computational modeling and requires experimental validation.
- The claim that "FEP3/IMA1 binds in close proximity to the MC site of BTSL1" is based on docking predictions and requires experimental confirmation.
- The physiological significance of the differential localization of BTSL1 and BTSL2 is not established.
- The statement that "exploiting –Fe-induced gene co-expression networks identified FEP3/IMA1 as a small effector protein" overstates the role of co-expression analysis; the identification was primarily through Y2H screening.