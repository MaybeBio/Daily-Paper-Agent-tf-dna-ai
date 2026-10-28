## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends.
- **Assessment boundary** Scientific soundness, logical coherence, and support of claims by the presented evidence. No assessment of editorial fit or novelty relative to other journals.
- **Shared manuscript claim summary** The manuscript proposes that the alternatively spliced, acidic β-domain of MEF2D regulates context-dependent higher-order assembly (liquid-like and solid-like states) during myogenesis, and that this assembly modulates transcriptional activity and differentiation.
- **Visible evidence base** Computational predictions (FuzDrop, FuzPred), transcriptional activity assays in C2C2 cells, differentiation assays, immunocytochemistry, Western blotting, FRAP analysis, NMR spectroscopy, and molecular dynamics simulations.
- **Missing materials affecting confidence** Supplementary figures and tables are referenced but not provided. Raw data for Western blots, FRAP curves, and NMR spectra are not shown. Statistical details for some comparisons are incomplete. The ChIP-seq protocol is described but no results are presented in the main text.

## Reviewer
- **Overall assessment** The manuscript addresses an interesting question about how alternative splicing of a short, acidic domain in a transcription factor could modulate its higher-order assembly and function during myogenesis. The combination of computational predictions, cellular assays, and biophysical experiments is ambitious. However, the evidence linking the observed higher-order assemblies to the proposed functional mechanism is largely correlative, and several key claims are not directly supported by the data presented. The causal relationship between β-domain dynamics, specific assembly states, and transcriptional outcomes remains unclear. The manuscript would benefit from a more focused experimental design that directly tests the proposed model.
- **Who would be interested in the results, and why** Researchers studying transcription factor regulation, particularly the role of intrinsically disordered regions and phase separation in gene control. The work may also be of interest to those studying myogenesis and the MEF2 family of transcription factors. The potential link between alternative splicing and the material properties of transcriptional assemblies is a timely topic.
- **Major strengths**
    1.  The study tackles a sophisticated and timely question about the functional role of a specific alternatively spliced domain in modulating protein phase behavior.
    2.  The integration of multiple techniques, from computational prediction to cellular imaging and biophysical analysis, is commendable.
    3.  The design of MEF2D variants with predicted distinct dynamic properties is a logical approach to probe the structure-function relationship.
    4.  The observation of both liquid-like and solid-like assemblies in cells is interesting and potentially significant.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Causal Link
        - **Claim pointer** The manuscript claims that the β-domain "fine-tunes Mef2D higher-order assembly to the cellular context, which provides a platform for myogenic regulatory factors and the transcriptional apparatus during the developmental process." This implies a direct, functional link between the assembly state and transcriptional activity.
        - **Evidence pointer** Results sections "β-domain rigidity potentiates transcription activity" and "Mef2D forms higher-order assemblies in C2C12 cells with both liquid-like and solid-like properties"; Figures 2 and 4.
        - **Concern** The central claim of the paper is that the specific higher-order assembly state (liquid vs. solid) directly controls transcriptional activity. However, the data presented are correlative. Transcriptional activity is measured in bulk cell populations, while the assembly state is assessed by microscopy in individual cells. There is no direct evidence that the cells with higher transcriptional activity are the same cells exhibiting the solid-like assemblies. The manuscript does not demonstrate that disrupting the formation of one specific assembly state (e.g., solid-like) abolishes the transcriptional effect, or that forcing the formation of a specific state is sufficient to enhance transcription. The link between the in vitro biophysical properties of the β-domain peptides and the in cellulo observations is also not firmly established.
        - **Why it matters** Without a direct causal link, the central hypothesis of the paper remains unproven. The observed correlation could be an epiphenomenon, with both transcriptional activity and assembly formation being downstream of another, unmeasured factor.
        - **Resolution test** To resolve this, the authors could perform experiments where they specifically modulate the assembly state (e.g., using optogenetics, or by adding a chemical dimerizer that promotes solid-like assembly) and measure the immediate effect on transcription from a MEF2D-dependent reporter. Alternatively, they could use a single-cell approach to simultaneously measure transcriptional activity and assembly state. Mutating the specific residues identified in the β-domain to specifically block solid-like assembly without affecting liquid-like assembly would also be a strong test.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Evidence for Solid-like Assemblies
        - **Claim pointer** The manuscript states that "we found solid-like aggregates in the cytosol, the presence of which correlated with higher transcriptional activity."
        - **Evidence pointer** Results section "Mef2D forms higher-order assemblies in C2C12 cells with both liquid-like and solid-like properties"; Figure 4.
        - **Concern** The classification of the cytoplasmic foci as "solid-like" is based solely on their low mobility in FRAP experiments. Low mobility in a FRAP experiment can be due to many factors, including the size of the structure, its viscosity, or the strength of interactions within it, and does not necessarily indicate a solid-like state. The manuscript does not provide any other evidence for a solid-like state, such as resistance to detergent extraction, insensitivity to 1,6-hexanediol, or a specific morphology by electron microscopy. The term "solid-like" is a strong biophysical claim that requires more rigorous evidence.
        - **Why it matters** The distinction between liquid-like and solid-like states is a central part of the proposed model. If the cytoplasmic foci are not truly solid-like, the model's premise is weakened. The functional significance of these structures is also unclear.
        - **Resolution test** The authors should perform additional characterization of the cytoplasmic foci. This could include testing their sensitivity to 1,6-hexanediol, a compound that disrupts liquid-liquid phase separation but not solid aggregates. They could also perform fluorescence recovery experiments over a longer time scale to see if there is any recovery at all, and use fluorescence loss in photobleaching (FLIP) to assess the connectivity of the structure. Staining with amyloid-specific dyes, such as Thioflavin T, could also be informative.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Relevance of Peptide Models
        - **Claim pointer** The manuscript uses NMR and MD simulations on 37-residue peptides to conclude that "the β-domain can sample both ordered and disordered interactions leading to compact and extended conformations."
        - **Evidence pointer** Results section "Structure and dynamics of Mef2D model peptides"; Figure 5.
        - **Concern** The biophysical experiments are performed on short, isolated peptides. While this is a common approach, it is a significant simplification. The behavior of this short domain within the context of the full-length, intrinsically disordered TAD, and in the presence of binding partners, could be very different. The relevance of the conformations sampled by the isolated peptide to the behavior of the full-length protein in cells is not directly demonstrated.
        - **Why it matters** The conclusions drawn from the peptide studies are used to support the model of how the β-domain functions in the full-length protein. If the peptide's behavior is not representative, the model is built on a weak foundation.
        - **Resolution test** The authors could perform similar NMR or MD studies on a longer construct that includes more of the TAD, or they could use cross-linking mass spectrometry to probe the conformations of the full-length protein in cells. They could also test the effect of the β-domain mutations on the assembly of the full-length protein in vitro.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Statistical Reporting
        - **Affected element** Figure 2
        - **Evidence pointer** Figure 2 legend
        - **Issue** The statistical analysis is described as a "two-sided student t-test" but it is not clear if the data meet the assumptions of this test. The number of independent experiments is stated, but the exact p-values for all comparisons are not always given in the text or figure.
        - **Required correction** Provide a more detailed description of the statistical methods, including how normality was tested. Report exact p-values for all significant and non-significant comparisons.
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Data Presentation
        - **Affected element** Figure 4
        - **Evidence pointer** Figure 4c, 4d
        - **Issue** The number of foci analyzed for the FRAP experiments is very low (e.g., n=3 for nuclear foci). This is a very small sample size from which to draw conclusions about the mobility of the assemblies.
        - **Required correction** The authors should analyze a larger number of foci from multiple independent experiments to increase the statistical power of the FRAP analysis.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Clarity of Model
        - **Affected element** Discussion
        - **Evidence pointer** Discussion section
        - **Issue** The model proposed in the discussion is somewhat vague. The statement "a transition of Mef2D between liquid-like and solid-like states may be required during myogenesis" is not a specific, testable model.
        - **Required correction** The authors should articulate a more specific and mechanistic model. For example, what is the molecular trigger for the transition? What are the downstream consequences of the solid-like state? How does this transition affect the interaction with specific co-factors?
    - **R1-m4**
        - **Severity** Minor
        - **Axis** Missing Data
        - **Affected element** ChIP-seq
        - **Evidence pointer** Methods section "ChIP-seq data analysis"
        - **Issue** A ChIP-seq protocol is described, but no results from these experiments are presented in the main text or figures. It is unclear if this data is meant to be part of this manuscript or a separate study.
        - **Required correction** The authors should either present the ChIP-seq results and explain how they support the main findings, or remove the protocol from the methods section to avoid confusion.
- **Technical failings that need to be addressed before the case is established**
    1.  The causal link between the specific higher-order assembly state and transcriptional activity is not established (R1-M1).
    2.  The evidence for the "solid-like" nature of the cytoplasmic aggregates is insufficient (R1-M2).
    3.  The relevance of the isolated peptide models to the behavior of the full-length protein is not demonstrated (R1-M3).
- **Assessment against Nature-style criteria**
    - **Originality** The idea that a specific alternatively spliced domain can modulate the material state of a transcription factor's assembly is a novel and interesting angle. The work is not simply a rehash of known concepts.
    - **Scientific importance** The potential link between alternative splicing, phase separation, and transcriptional control is of high importance. If the causal link were proven, this would be a significant advance. However, as it stands, the importance is more potential than demonstrated.
    - **Interdisciplinary readership** The topic is likely to appeal to a broad readership, including cell biologists, biophysicists, and those interested in gene regulation. The combination of methods is attractive.
    - **Technical soundness** The individual techniques are, for the most part, applied soundly. However, the overall experimental design has a critical flaw in that it does not directly test the central hypothesis. The interpretation of the FRAP data as evidence for "solid-like" states is an overreach.
    - **Readability for nonspecialists** The manuscript is generally well-written and the logic is easy to follow. The figures are clear. However, the use of terms like "solid-like" without rigorous definition could be confusing for a non-specialist.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an interesting hypothesis and a large body of correlative data, but the central claim of a causal link between β-domain dynamics, specific higher-order assembly states, and transcriptional activity is not supported by the experimental design. The technical concerns regarding the characterization of the "solid-like" state and the relevance of the peptide models must also be addressed. I would be supportive of the manuscript if the authors can provide direct experimental evidence for the causal model they propose.

## Risk / unsupported claims
- The claim that the cytoplasmic foci are "solid-like" is unsupported by the evidence presented. Low mobility in FRAP is not sufficient to define a solid-like state.
- The claim that the β-domain "fine-tunes Mef2D higher-order assembly to the cellular context, which provides a platform for myogenic regulatory factors and the transcriptional apparatus" is a strong functional statement that is not directly supported by the data. The data show correlation, not causation.
- The claim that the β-domain can "switch between ordered and disordered interactions" is based on peptide models and is not directly demonstrated in the context of the full-length protein in cells.
- The functional significance of the nuclear liquid-like condensates is not explored. It is assumed they are transcriptionally active, but this is not directly shown.
- The ChIP-seq data is mentioned in the methods but not presented, making any claims related to it unevaluable.