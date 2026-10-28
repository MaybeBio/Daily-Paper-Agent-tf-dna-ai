## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, data availability, funding, declarations, acknowledgements)
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided manuscript text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors characterise cancer-associated mutations in the IRF4 DNA-binding domain (DBD) using biophysical, structural, and cellular assays. They report that most mutations do not abolish DNA binding but alter binding kinetics, particularly increasing dissociation rates, and that the K123R mutation enhances transcriptional activity and nuclear localisation, suggesting an activating role in multiple myeloma.
- **Visible evidence base** Abstract, full introduction, full methods (including crystallisation, FP, SPR, DSF, MD simulations, cell-based assays), results sections (as embedded in text), discussion, conclusion, supplementary figure/table references (S1-S15, T1-T6), PDB deposition (6TD4)
- **Missing materials affecting confidence** Raw data files, full supplementary figures and tables (only referenced, not provided), detailed statistical outputs, experimental replicates for cell-based assays, full crystallographic data table (referenced as Table S3 but not shown), sequence alignments, and validation of the reporter assay system

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive and technically rigorous characterisation of IRF4 DBD mutations associated with multiple myeloma and T-cell lymphoma. The combination of structural, biophysical, and cellular approaches is commendable and provides a nuanced picture that challenges the initial hypothesis that these mutations simply disrupt DNA binding. The finding that most mutants retain or enhance binding affinity while showing altered kinetics, particularly faster dissociation, is interesting and potentially clinically relevant. However, several concerns limit the strength of the conclusions. The cellular data are preliminary, with limited replicates and no mechanistic depth. The link between increased transcriptional activity and improved prognosis is speculative. The MD simulations are short and may not fully capture conformational dynamics. The manuscript would benefit from clearer presentation of statistical methods and effect sizes. Overall, this is a solid descriptive study that advances understanding of IRF4 mutants, but the functional significance and clinical implications require further validation.
- **Who would be interested in the results, and why** Haematological oncologists and researchers studying multiple myeloma and lymphoma pathogenesis would be interested in the functional characterisation of IRF4 mutations and their potential impact on treatment response. Structural biologists and biophysicists studying transcription factor DNA-binding mechanisms would value the apo IRF4 DBD structure and the kinetic analyses. Cancer geneticists interpreting somatic mutation data would benefit from understanding that not all DBD mutations are loss-of-function. Additionally, researchers developing targeted therapies against IRF4 or its downstream pathways would find the activating nature of K123R relevant for therapeutic stratification.
- **Major strengths** 1) Comprehensive multi-technique approach combining X-ray crystallography, FP, SPR, DSF, and MD simulations to characterise a panel of 17 mutants. 2) The new apo IRF4 DBD crystal structure provides valuable structural insights, including the conformational flexibility of the DNA-binding loop and the R98 side-chain. 3) The finding that most cancer-associated mutants retain or enhance DNA-binding affinity, with altered kinetics, challenges simplistic loss-of-function assumptions. 4) The cellular validation of K123R showing increased transcriptional activity and nuclear localisation is a valuable addition. 5) The discussion of clinical implications, particularly the link to improved prognosis, is thoughtful and appropriately cautious.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental rigour and reproducibility
  - **Claim pointer** The authors claim that K123R shows increased transcriptional activity (4.2-fold) and increased nuclear localisation based on luciferase reporter assays and immunoblotting.
  - **Evidence pointer** Figure 4a-b, Methods section "Mammalian cell expression, nuclear localisation and IRF4-dependent reporter assay"
  - **Concern** The cellular data are presented with minimal experimental detail. The luciferase assay reports n=3 and the immunoblotting reports 3 technical replicates of 3 biological replicates, but the statistical analysis is not described. The normalisation strategy (GFP for transfection, GAPDH/PARP for loading) is reasonable, but the variability across replicates is not shown. The claim of "increased nuclear localisation" is based on a single representative blot and densitometry is not described. The choice of HEK293T cells, which are not of B-cell or plasma-cell lineage, limits the physiological relevance. The reporter construct uses a 2.5 kb region upstream of ZBT32, but the specificity for IRF4 versus other IRFs is not validated.
  - **Why it matters** The cellular data are central to the conclusion that K123R is an activating mutation. Without robust statistical analysis, clear replicate data, and appropriate cell context, this claim is not fully supported. Overinterpretation of preliminary cellular data could mislead the field.
  - **Resolution test** Provide full statistical analysis (mean, SD/SEM, individual data points) for all replicates. Include densitometry quantification for nuclear/cytoplasmic fractions with error bars. Validate the reporter assay for IRF4 specificity (e.g., using a known IRF4-responsive element and a negative control with mutated binding site). Consider repeating key experiments in a B-cell or myeloma cell line.
  - **Concern ID** R1-M2
  - **Severity** Major
  umber **Blocking** Yes
  - **Axis** Data interpretation and claim support
  - **Claim pointer** The authors state that "cancer-associated mutations in the IRF4 DBD confer changes which act to modestly reduce thermostability in the majority (7/17) of cases, and increase the dissociation rate from DNA, whilst maintaining functional DNA-binding ability of similar or tighter binding affinity."
  - **Evidence pointer** Table 1, Figure 3, Supplementary Figures S8, S10, S13
  - **Concern** The relationship between the biophysical measurements and the functional outcome is not clearly established. While the authors report faster koff rates for most mutants, the physiological relevance of these changes is unclear. The residence times are calculated but not discussed in the context of transcriptional output. The claim that "maintaining functional DNA-binding ability" is supported by affinity measurements, but the kinetic changes could still have significant functional consequences that are not explored. The correlation between in vitro binding kinetics and cellular transcriptional activity is not directly tested.
  - **Why it matters** The central thesis is that these mutations alter DNA-binding dynamics in a way that may explain clinical outcomes. Without a direct link between the biophysical changes and cellular function, the conclusions remain correlative. The manuscript would be strengthened by testing whether the altered kinetics translate to changes in target gene expression or chromatin occupancy.
  - **Resolution test** Perform chromatin immunoprecipitation (ChIP) for IRF4 mutants at known target genes to assess occupancy. Correlate binding kinetics with transcriptional output in a dose-response manner. Alternatively, use a more physiologically relevant DNA substrate (e.g., nucleosomal DNA or a longer promoter fragment) to test whether kinetic differences are maintained.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical validity of computational methods
  - **Claim pointer** The authors use MD simulations and MM/PBSA calculations to support their experimental findings, stating that "in agreement with the biophysical data, although the method is not sensitive enough to differentiate wild type IRF4 and mutants that are capable of binding DNA, the mutants R98A and R98A/C99A are clearly delineated from the cohort as weaker interactors."
  - **Evidence pointer** Methods section "Molecular dynamics simulations and MM/PBSA calculations", Supplementary Figure S12
  - **Concern** The MD simulations are only 8 ns in length, which is short for capturing conformational changes associated with DNA binding. The MM/PBSA method is known to be sensitive to force field parameters, solute dielectric constant, and entropy contributions, which are not fully described. The use of a single trajectory approach and the choice of solute dielectric constant of 4 are not justified. The convergence criteria (tracking Lennard-Jones and Coulombic energies, RMSD) are mentioned but no data are shown. The statistical treatment of the triplicate simulations is not described.
  - **Why it matters** The computational results are used to corroborate experimental findings, but if the methods are not robust, the conclusions drawn from them are weakened. The MM/PBSA approach may not be sufficiently accurate to distinguish subtle differences in binding affinity among the mutants.
  - **Resolution test** Provide convergence plots (RMSD vs time, energy vs time) for all simulations. Justify the choice of solute dielectric constant and force field. Consider longer simulations (50-100 ns) or enhanced sampling methods. Report standard errors for MM/PBSA energies across triplicates. If possible, validate with an independent computational method (e.g., FEP or TI).
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Structural interpretation
  - **Claim pointer** The authors state that "the engineered C99S mutation lies within the DNA-binding interface" and that "R98 conformational change upon DNA-binding may be a common feature across the IRF family."
  - **Evidence pointer** Figure 2, Results section "The crystal structure of IRF4 in the apo state reveals conformational change in the DNA-binding site"
  - **Concern** The apo structure is derived from a mutant (C99S and E45A/E46A/K47A) that may not fully represent the wild-type protein. The authors acknowledge this but do not fully address the potential impact of these mutations on the observed conformation. The claim that R98 conformational change is a common feature across the IRF family is based on comparison with only a few structures (IRF2, IRF3, IRF7), and the functional significance of this change is not experimentally tested.
  - **Why it matters** The structural interpretation underpins the discussion of how mutations may affect DNA binding. If the apo structure is not representative, the conclusions about conformational changes may be misleading.
  - **Resolution test** Compare the apo structure with the wild-type NMR structure (PDB 2DLL) more quantitatively (e.g., RMSD per residue). Discuss the potential effects of the surface mutations on the observed conformation. Consider validating the R98 conformational change with mutagenesis experiments (e.g., R98A in the context of the full-length protein).
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and presentation
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The abstract states "IRF4, a transcription factor in the interferon regulatory factor family, is a key regulator in immune cell differentiation indicated to have an essential role in the development of lymphoid malignancies." The phrase "indicated to have" is vague and could be more direct.
  - **Required correction** Rephrase to "IRF4, a transcription factor in the interferon regulatory factor family, is a key regulator of immune cell differentiation and has an essential role in the development of lymphoid malignancies."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results, Table 1
  - **Evidence pointer** Table 1, Supplementary Figure S8
  - **Issue** The statistical significance of DSF and binding affinity differences is indicated with asterisks, but the exact p-values and effect sizes are not reported. The number of replicates for each measurement is not consistently stated.
  - **Required correction** Add a statistical methods subsection detailing the tests used, the number of replicates, and how significance thresholds were set. Report p-values and confidence intervals in Table 1 or supplementary tables.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** Methods, FP assay
  - **Evidence pointer** Methods section "FP assay development, optimisation and data generation"
  - **Issue** The FP assay description lacks details on the protein concentration range used, the exact buffer conditions, and how the Kd values were calculated (e.g., nonlinear regression model). The use of a one-site binding model is mentioned but not justified.
  - **Required correction** Provide full experimental details including protein concentrations, buffer composition, and the fitting equation used. Justify the choice of a one-site model and discuss potential limitations.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 3
  - **Evidence pointer** Figure 3, Supplementary Figure S13
  - **Issue** The SPR data presentation is dense, with multiple panels and supplementary figures. The reader is referred to supplementary figures for key details (e.g., sensorgrams, replicate data), which makes it difficult to assess the quality of the data from the main text alone.
  - **Required correction** Include representative sensorgrams in the main figure and move detailed replicate data to supplementary. Add a summary table of kinetic parameters with confidence intervals.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion
  - **Evidence pointer** Discussion, first paragraph
  - **Issue** The discussion of the improved prognosis associated with IRF4 mutations is brief and does not fully engage with the clinical literature. The authors mention the association but do not discuss potential mechanisms or alternative explanations.
  - **Required correction** Expand the discussion to include a more detailed consideration of how the observed biochemical changes might relate to clinical outcomes, and acknowledge alternative interpretations (e.g., passenger mutations, clonal selection).
  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Throughout
  - **Evidence pointer** Results, Discussion
  - **Issue** The term "activating mutation" is used for K123R, but the evidence supports increased transcriptional activity in a reporter assay, not necessarily activation of endogenous IRF4 targets. This terminology may be premature.
  - **Required correction** Use more cautious language such as "gain-of-function" or "transcriptionally activating" and clarify that this is based on reporter assays and requires validation at endogenous target genes.

## Risk / unsupported claims
- The claim that K123R is an "activating mutation" that is "preferentially selected for in multiple myeloma" is not fully supported by the data. The increased transcriptional activity is shown in a heterologous reporter assay in HEK293T cells, and the selection argument is speculative.
- The statement that "the enhanced nuclear localisation and transcriptional activity of K123R IRF4 support the notion that it is an activating mutation" overreaches, as the mechanism linking nuclear localisation to transcriptional activity is not established.
- The claim that "cancer-associated mutations in the IRF4 DBD confer changes which act to modestly reduce thermostability in the majority (7/17) of cases" is based on DSF data, but the physiological relevance of these small changes is not demonstrated.
- The assertion that "the R98 conformational change upon DNA-binding may be a common feature across the IRF family" is speculative and based on limited structural comparisons.
- The statement that "the second binding event observed from the two-state model is weakly specific" is not fully supported, as the nature of this secondary binding is not characterised.
- The claim that "the C99R mutant may expand the range of potential protein-DNA interactions and thus alter base specificity" is a hypothesis without direct experimental evidence.

## Assessment against Nature-style criteria
- **Originality** The manuscript offers a novel and comprehensive characterisation of IRF4 DBD mutations, challenging the prevailing assumption that these are loss-of-function. The combination of structural, biophysical, and cellular approaches is original in this context. However, the individual techniques are well-established, and the novelty lies primarily in the application to this specific mutation panel.
- **Scientific importance** The findings have potential clinical relevance for multiple myeloma and T-cell lymphoma, where IRF4 is a key driver. Understanding the functional consequences of mutations could inform prognosis and treatment stratification. The study also provides a valuable resource for interpreting IRF4 mutations in future genomic studies. However, the clinical implications are not directly tested, and the importance is somewhat limited by the preliminary nature of the cellular data.
- **Interdisciplinary readership** The manuscript will appeal to a broad audience including structural biologists, biophysicists, cancer biologists, and clinical haematologists. The writing is generally accessible, and the figures are well-organised. However, the dense presentation of biophysical data may be challenging for non-specialists.
- **Technical soundness** The biophysical methods (FP, SPR, DSF) are well-executed and appropriately controlled. The crystallographic work appears sound, though the full data table is not provided. The MD simulations are technically adequate but limited in scope. The cellular experiments are the weakest technically, with limited replicates and no mechanistic depth.
- **Readability for nonspecialists** The manuscript is generally well-written and logically structured. The abstract and introduction are accessible. However, the results section is dense and may be difficult for non-specialists to follow, particularly the kinetic analyses and the discussion of two-state binding models. The authors could improve readability by providing more context and simplifying the presentation of complex data.

## Risk / unsupported claims
- The claim that K123R is an "activating mutation" that is "preferentially selected for in multiple myeloma" is not fully supported by the data. The increased transcriptional activity is shown in a heterologous reporter assay in HEK293T cells, and the selection argument is speculative.
- The statement that "the enhanced nuclear localisation and transcriptional activity of K123R IRF4 support the notion that it is an activating mutation" overreaches, as the mechanism linking nuclear localisation to transcriptional activity is not established.
- The claim that "cancer-associated mutations in the IRF4 DBD confer changes which act to modestly reduce thermostability in the majority (7/17) of cases" is based on DSF data, but the physiological relevance of these small changes is not demonstrated.
- The assertion that "the R98 conformational change upon DNA-binding may be a common feature across the IRF family" is speculative and based on limited structural comparisons.
- The statement that "the second binding event observed from the two-state model is weakly specific" is not fully supported, as the nature of this secondary binding is not characterised.
- The claim that "the C99R mutant may expand the range of potential protein-DNA interactions and thus alter base specificity" is a hypothesis without direct experimental evidence.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a valuable and comprehensive characterisation of IRF4 DBD mutations, with robust biophysical data and a novel structural contribution. However, the cellular data require strengthening, and the interpretation of the clinical implications should be more cautious. Addressing the major concerns, particularly around the cellular experiments and the link between biophysical changes and functional outcomes, would significantly improve the manuscript.