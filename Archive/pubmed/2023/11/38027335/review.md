## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, conclusions, and supplementary figure references.
- **Assessment boundary** Scientific validity, technical soundness, interpretation of results, and alignment with claims made in the abstract and conclusions. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors report that PTER-ITC, a semi-synthetic hybrid of pterostilbene and isothiocyanate, selectively inhibits proliferation and migration of MG-63 osteosarcoma cells, induces apoptosis via mitochondrial membrane potential disruption, reverses EMT, and disrupts the β-catenin/TCF-4 interaction as shown by in silico docking, MD simulation, Co-IP, and luciferase reporter assays.
- **Visible evidence base** MTT viability assays, wound-healing and transwell migration assays, immunofluorescence, RT-qPCR, immunoblotting, molecular docking, MD simulation, Co-IP, TOPFlash luciferase assay. Figures referenced: 1, 2, 3, 4, 5, 6, 7, 8; Supplementary Figure S1.
- **Missing materials affecting confidence** Raw numerical data for viability curves, migration quantifications, and densitometry values are not provided. No information on biological replicates or statistical test details beyond p-value thresholds. No validation of antibody specificity. No positive control for Wnt pathway activation. No data on compound stability or solubility in culture media. No information on whether experiments were blinded or randomized.

## Reviewer
- **Overall assessment** The manuscript presents a straightforward in vitro study of a semi-synthetic compound with potential anticancer activity against osteosarcoma cells. The work combines phenotypic assays with in silico and biochemical approaches to propose a mechanism involving disruption of the β-catenin/TCF-4 interaction. While the data are internally consistent and the conclusions are generally supported by the presented results, several technical limitations and missing experimental details reduce confidence in the strength of the mechanistic claims. The study is preliminary and would benefit from additional validation, particularly regarding the specificity of the proposed mechanism and the translational relevance of the findings.
- **Who would be interested in the results, and why** Researchers in osteosarcoma biology, Wnt signaling, and natural product-based drug discovery would find this work relevant. The compound's selectivity for cancer cells over normal osteoblasts is of interest to those developing targeted therapies. The proposed mechanism of disrupting β-catenin/TCF-4 interaction may also interest investigators studying protein-protein interaction inhibitors in oncology.
- **Major strengths** The study addresses an important clinical need for safer osteosarcoma therapies. The use of multiple complementary assays (viability, migration, apoptosis, EMT markers, and transcriptional readouts) strengthens the phenotypic characterization. The combination of in silico predictions with biochemical validation (Co-IP and luciferase reporter) is a reasonable approach to support the proposed mechanism. The selectivity for cancer cells over normal osteoblasts is a notable finding with therapeutic implications.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (dose-response and IC50 determination), R1-M2 (quantitative rigor of imaging data), R1-M3 (mechanistic specificity), R1-M4 (statistical reporting).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The compound is novel in the context of osteosarcoma, and the proposed mechanism of disrupting β-catenin/TCF-4 interaction is of interest. However, the approach of testing a semi-synthetic compound against cancer cell lines is not conceptually new.  
  *Scientific importance*: Moderate. Osteosarcoma treatment remains challenging, and new therapeutic options are needed. However, the study is limited to in vitro data, and the clinical relevance is not yet established.  
  *Interdisciplinary readership*: Limited. The work is primarily of interest to cancer biologists and medicinal chemists. The mechanistic depth is not sufficient to attract a broader readership.  
  *Technical soundness*: Adequate but with notable gaps. The experimental design is generally reasonable, but missing details on replicates, statistical methods, and quantitative analyses weaken the technical rigor.  
  *Readability for nonspecialists*: Acceptable. The manuscript is clearly written, though some sections assume familiarity with Wnt signaling and molecular biology techniques.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially interesting, but the current evidence does not fully establish the mechanistic claim of β-catenin/TCF-4 disruption as the primary mode of action. Additional experiments and improved quantitative reporting are required.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that PTER-ITC "specifically inhibited the survival, proliferation, and migration of osteosarcoma cells" and report an IC50 of 34.67 μM for MG-63 cells.  
- **Evidence pointer** Results section, Figure 1B and 1C  
- **Concern** The IC50 value is derived from a single time point (24 h) with no time-course analysis. The selectivity claim is based on comparison with hFOB 1.19 cells, but only one normal cell line was used, and the concentration range tested is not fully described. Additionally, the MTT assay measures metabolic activity, not directly cell survival or proliferation, and no confirmatory assays (e.g., colony formation, EdU incorporation) were performed.  
- **Why it matters** The selectivity and potency claims are central to the paper's conclusions. Without robust dose-response data across multiple time points and confirmatory proliferation assays, the IC50 and selectivity conclusions are not firmly established.  
- **Resolution test** Provide full dose-response curves at multiple time points (e.g., 24, 48, 72 h) for both MG-63 and hFOB 1.19 cells. Include a second normal cell line and a second osteosarcoma cell line. Confirm proliferation effects with an independent assay such as colony formation or EdU incorporation.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that PTER-ITC "reversed EMT" based on increased E-cadherin and decreased N-cadherin levels, and that it "induced apoptosis" based on staining assays.  
- **Evidence pointer** Results section, Figures 2A, 2B, 3A, 3B, 3C, 3D, 3E  
- **Concern** The immunofluorescence images are presented as representative micrographs without quantification of fluorescence intensity across multiple fields or replicates. The apoptosis data rely on qualitative staining (AO/EtBr, DAPI, TUNEL) with no flow cytometry or immunoblotting for cleaved caspase-3 or PARP to confirm the apoptotic pathway. The claim of EMT reversal is based on only two markers and no functional assessment of cell morphology or migration in the context of EMT.  
- **Why it matters** The conclusions regarding apoptosis and EMT reversal are based on subjective image interpretation and limited molecular markers. Quantitative data and additional markers are needed to support these claims.  
- **Resolution test** Provide quantitative fluorescence intensity measurements from at least three independent experiments with multiple fields per condition. Include flow cytometric analysis of apoptosis (Annexin V/PI) and immunoblotting for cleaved caspase-3 and PARP. For EMT, include additional markers (e.g., vimentin, Snail, Twist) and a functional migration/invasion assay.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mechanistic specificity  
- **Claim pointer** The authors claim that PTER-ITC "abrogates the β-catenin/TCF-4 interaction" and that this is the underlying mechanism of its anticancer effects.  
- **Evidence pointer** Results section, Figures 5, 6, 7, 8  
- **Concern** The Co-IP experiment shows reduced β-catenin/TCF-4 interaction, but the quantification is not shown and the experiment appears to be performed only once. The TOPFlash luciferase assay shows reduced TCF transcriptional activity, but this could be due to effects on β-catenin stability, nuclear localization, or other components of the Wnt pathway rather than direct disruption of the interaction. The molecular docking and MD simulation are computational predictions and do not provide direct biochemical evidence of binding. No competition experiments or binding affinity measurements were performed.  
- **Why it matters** The central mechanistic claim of the paper is that PTER-ITC directly disrupts the β-catenin/TCF-4 interaction. The current evidence is suggestive but not conclusive, as alternative explanations for reduced TCF activity are not excluded.  
- **Resolution test** Perform quantitative Co-IP with densitometry from at least three independent experiments. Include a competition assay with a known β-catenin/TCF-4 inhibitor or a mutant TCF-4 lacking the β-catenin binding domain. Measure β-catenin stability and nuclear localization to rule out indirect effects. Consider surface plasmon resonance or isothermal titration calorimetry to directly measure binding affinity.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The authors report statistical significance (p < 0.05, p < 0.01, p < 0.001) for multiple comparisons.  
- **Evidence pointer** Throughout Results section  
- **Concern** The statistical methods are not described in detail. It is unclear which specific test was used for each comparison, whether data were tested for normality, and how many independent biological replicates were performed. The figure legends do not specify error bar types (SD vs SEM) or the number of replicates.  
- **Why it matters** Without clear statistical reporting, the reliability of the significance claims cannot be assessed. This is a fundamental requirement for the validity of the conclusions.  
- **Resolution test** Provide a detailed statistical analysis section specifying the tests used, the number of biological and technical replicates, and the criteria for significance. Include this information in figure legends.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The opening sentence states that osteosarcoma is "a leading cause of death and disability in children and adolescents worldwide," which is somewhat imprecise. Osteosarcoma is the most common primary bone tumor in this age group, but it is not a leading cause of death overall.  
- **Required correction** Rephrase to "the most common primary bone malignancy in children and adolescents" or similar.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Technical detail  
- **Affected element** Methods, Molecular Docking  
- **Evidence pointer** Methods section, Molecular Docking subsection  
- **Issue** The docking protocol states that 100 conformations were generated, but the selection criteria for the "best conformation" are not described.  
- **Required correction** Specify the scoring function and selection criteria used to choose the best conformation.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Discussion  
- **Evidence pointer** Discussion, paragraph 3  
- **Issue** The discussion states that PTER-ITC "exclusively disrupted the interaction of β-catenin/TCF-4," but the data do not demonstrate exclusivity. Other Wnt pathway components or off-target effects are not excluded.  
- **Required correction** Soften the language to "selectively disrupted" or "disrupted" without the claim of exclusivity.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Methods, Cell Culture  
- **Evidence pointer** Methods section, Cell Culture subsection  
- **Issue** The passage number of cells used in experiments is not stated.  
- **Required correction** Include the passage number or range for both cell lines.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Results, Figure 4  
- **Evidence pointer** Results section, Figure 4  
- **Issue** The immunoblot panels are shown without molecular weight markers or indication of which bands correspond to the target proteins.  
- **Required correction** Add molecular weight markers and label the target bands in the figure.

## Risk / unsupported claims
- The claim that PTER-ITC "specifically" targets cancer cells is not fully supported, as only one normal cell line was tested and the mechanism of selectivity is not addressed.
- The claim that PTER-ITC "reverses EMT" is based on limited markers and no functional assessment.
- The claim that PTER-ITC "abrogates the β-catenin/TCF-4 interaction" as the primary mechanism is not conclusively established, as alternative explanations are not excluded.
- The statement in the conclusions that this is "the first ever report on the potent antiosteosarcoma properties" of PTER-ITC is not verifiable from the provided materials.
- The claim that PTER-ITC is "safe for normal cells" is based on a single cell line and limited assays, and is therefore not generalizable.