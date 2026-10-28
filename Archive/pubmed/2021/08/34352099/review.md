## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, concluding remarks) as provided by the author. Supplementary materials referenced but not provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and internal consistency of the claims as presented in the provided text. No external validation of data or methods was performed.
- **Shared manuscript claim summary** The authors propose that architectural DNA-binding proteins (ADBPs) such as Nhp6A, Fis, and HU slide along DNA via a "DNA surface sliding" mechanism, where the protein transiently unbinds from the DNA groove(s) and diffuses along the DNA backbone, rather than via rotation-coupled sliding within the groove. This claim is supported by single-molecule tracking of wild-type and mutant proteins in vitro and in vivo, and by coarse-grained molecular dynamics simulations for Nhp6A.
- **Visible evidence base** Single-molecule fluorescence tracking data (MSD plots, displacement distributions, diffusion coefficients) for Nhp6A and Fis mutants in vitro; in vivo single-molecule tracking in E. coli; ensemble dissociation lifetime measurements; coarse-grained MD simulations for Nhp6A variants. Figures and tables are referenced but not fully visible in the provided text.
- **Missing materials affecting confidence** Supplementary figures, tables, and methods (e.g., Supplementary Figures S1–S8, Supplementary Tables S1–S2, Supplementary Movie S1) are referenced but not provided. Detailed simulation parameters and validation of the CG model are not fully described. Raw trajectory data and statistical details for some comparisons are not shown.

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in protein-DNA interactions: how architectural DNA-binding proteins achieve 1D diffusion despite inducing large conformational changes in DNA. The combination of targeted mutagenesis, single-molecule tracking, and MD simulations is powerful and appropriate. The data are largely internally consistent and support the proposed "DNA surface sliding" model for Nhp6A and Fis. However, several technical concerns regarding data analysis, statistical rigor, and the interpretation of in vivo results need to be addressed before the case is fully established. The manuscript is well-written and will be of interest to a broad readership in biophysics, molecular biology, and chromosome biology.
- **Who would be interested in the results, and why** Researchers studying protein-DNA interactions, DNA target search mechanisms, chromatin structure and dynamics, and bacterial nucleoid organization. The work is also relevant to those interested in single-molecule biophysics and molecular simulation of protein-DNA complexes.
- **Major strengths**
  1. The study uses a well-chosen set of mutants to dissect the molecular determinants of DNA sliding, guided by high-resolution structures.
  2. The combination of in vitro single-molecule assays, in vivo tracking, and MD simulations provides complementary perspectives on the sliding mechanism.
  3. The proposal of a "DNA surface sliding" model, distinct from groove-coupled rotation, is a conceptually important contribution.
  4. The in vivo experiments extend the findings to a physiological context, which is often lacking in such studies.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Data analysis
  - **Claim pointer** The authors claim that Nhp6A-Δ(2–16) is "immobile" on DNA based on single-molecule tracking at 50 mM Kglu, and that this immobility is due to the loss of the N-terminal arm's role in sliding.
  - **Evidence pointer** Results section "Single-molecule tracking of Nhp6A mutants on DNA", Figure 2D–H; location not provided.
  - **Concern** The diffusion coefficient for Nhp6A-Δ(2–16) is reported to be comparable to the spatial resolution of the imaging system (96 nm). The authors conclude the protein is "immobile." However, the manuscript does not provide a clear statistical comparison between the D value of the mutant and the expected D value for a truly immobile particle, nor does it account for potential artifacts from surface interactions or DNA tethering. The conclusion of immobility is central to the claim that the N-terminal arm is required for sliding, but the evidence as presented is not sufficiently quantitative.
  - **Why it matters** If the Δ(2–16) mutant is not truly immobile but merely very slow, the interpretation that the N-terminal arm is specifically required for sliding (rather than just for binding stability) is weakened. The distinction between "immobile" and "very slow" is critical for the mechanistic model.
  - **Resolution test** Provide a quantitative comparison of the D value for Δ(2–16) with the localization error and with a control of a known immobile protein. Perform a statistical test (e.g., t-test) to show that the D value is not significantly different from zero. Alternatively, provide a lower bound on the D value based on the tracking precision.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Data interpretation
  - **Claim pointer** The authors propose that Fis slides on the DNA surface after unbinding from the major groove, based on the behavior of Fis-K90A, Fis-N84A, and Fis-R71A mutants.
  - **Evidence pointer** Results section "The Fis-R85A mutant", "The Fis-K90A mutant", "The Fis-N84A mutant", "The Fis-R71A mutant", Figure 4; location not provided.
  - **Concern** The interpretation of the Fis mutant data relies on the assumption that changes in diffusion coefficients directly reflect changes in the sliding mechanism. However, the authors do not rule out alternative explanations, such as changes in the frequency of hopping events (transient dissociation and rebinding) or changes in the effective "sticking" time to the DNA. The manuscript does not provide a quantitative model that links the observed D values to specific molecular events (e.g., groove unbinding vs. surface sliding). The distinction between "surface sliding" and "hopping" is particularly blurred for the K90A mutant, which shows a large drift component.
  - **Why it matters** The central claim of the paper is that these proteins slide on the DNA surface, not in the groove. If the observed mobility changes can be explained by altered hopping kinetics, the proposed mechanism is not uniquely supported.
  - **Resolution test** Perform experiments or simulations that can distinguish between surface sliding and hopping, e.g., by measuring the ionic strength dependence of D in a way that discriminates between the two models, or by using a DNA substrate with barriers that would differentially affect sliding vs. hopping. Provide a quantitative model that fits the observed D values and displacement distributions with explicit parameters for sliding and hopping.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Simulation methodology
  - **Claim pointer** The MD simulations show that Nhp6A switches between a static (mode 1) and a mobile (mode 2) state, and that the mobile state involves the N-terminal arm interacting with the DNA backbone.
  - **Evidence pointer** Results section "Molecular dynamics simulations", Figure 6; location not provided.
  - **Concern** The coarse-grained MD simulations are used to support the two-state model. However, the manuscript does not provide sufficient details on the validation of the CG model, the force field parameters, or the convergence of the simulations. The clustering analysis (DBSCAN) is described, but the robustness of the two-state classification is not demonstrated (e.g., how sensitive is the result to the clustering parameters?). The timescales of the simulations (108 steps) may not be sufficient to observe the full dynamics of the sliding process.
  - **Why it matters** The simulations are a key piece of evidence for the proposed mechanism. If the simulations are not well-validated or the analysis is not robust, the structural model derived from them is not reliable.
  - **Resolution test** Provide additional details on the CG model validation (e.g., comparison with experimental data or all-atom simulations). Show that the two-state clustering is robust to parameter choices. Discuss the timescale limitations and whether the observed mode switching is converged.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance / Generalizability
  - **Claim pointer** The authors state that "Nhp6A, Fis, and bacterial HU are all near exclusively associated with the chromosome, as packaged within the bacterial nucleoid, and can be modeled by three diffusion modes where HU exhibits the fastest and Fis the slowest diffusion."
  - **Evidence pointer** Results section "in vivo dynamics", Figure 3, Table 1; location not provided.
  - **Concern** The in vivo data are presented as supporting the in vitro findings, but the connection is not fully developed. The authors do not discuss how the three diffusion modes observed in vivo relate to the two-state model proposed from in vitro and simulation data. The in vivo environment is highly crowded and complex, and the interpretation of diffusion coefficients in terms of DNA sliding is not straightforward. The authors should more explicitly address how the in vivo data inform the mechanism of sliding, or acknowledge the limitations of such comparisons.
  - **Why it matters** The in vivo experiments are a major part of the manuscript's scope, but their contribution to the mechanistic model is unclear. If the in vivo data do not directly test the sliding mechanism, the claim that they support it is overstated.
  - **Resolution test** Provide a more explicit discussion of how the in vivo diffusion modes map onto the in vitro sliding states. Alternatively, present the in vivo data as a separate, descriptive finding and temper the claim that they support the proposed mechanism.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity / Presentation
  - **Affected element** Abstract
  - **Evidence pointer** Abstract; location not provided.
  - **Issue** The abstract states that "Nhp6A switches between two binding modes" but does not mention the role of the N-terminal arm in this switch, which is a key finding of the paper.
  - **Required correction** Add a brief mention of the N-terminal arm's role in the abstract to better summarize the main conclusion.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness / Statistics
  - **Affected element** Methods, single-molecule tracking analysis
  - **Evidence pointer** Methods section "Single-molecule tracking of Nhp6A mutants on DNA"; location not provided.
  - **Issue** The manuscript states that "Welch's t test was used to evaluate significant differences between the mutants and WT" but does not report the p-values or effect sizes for the key comparisons (e.g., D values of WT vs. MF, WT vs. Δ(2–16)).
  - **Required correction** Report the p-values and confidence intervals for the key statistical comparisons, or provide a supplementary table with these values.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Clarity / Presentation
  - **Affected element** Discussion, Fis section
  - **Evidence pointer** Discussion section "1-D diffusion by the bacterial protein Fis"; location not provided.
  - **Issue** The discussion of Fis is somewhat speculative, particularly regarding the role of the N-terminal β-hairpin arms. The authors should clearly distinguish between conclusions directly supported by data and those that are speculative.
  - **Required correction** Add a sentence clarifying which parts of the Fis model are directly supported by the mutant data and which are hypotheses.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness / Methods
  - **Affected element** Methods, in vivo experiments
  - **Evidence pointer** Methods section "Single-molecule measurements in vivo"; location not provided.
  - **Issue** The manuscript states that "low amounts of ADBPs fused with eGFP were generated by basal expression" but does not provide details on how the expression level was quantified or how the authors ensured that the fusion proteins were functional.
  - **Required correction** Provide a brief description of how expression levels were assessed and any controls for fusion protein functionality.

## Risk / unsupported claims
- The claim that Nhp6A-Δ(2–16) is "immobile" on DNA is not fully supported by the quantitative data presented; the D value is close to the spatial resolution limit, and no statistical test against zero is shown.
- The claim that the Fis mutant data uniquely support a "surface sliding" mechanism over alternative explanations (e.g., altered hopping) is not fully established, as no quantitative model distinguishing these possibilities is provided.
- The in vivo data are presented as supporting the in vitro sliding mechanism, but the connection between the three in vivo diffusion modes and the two-state in vitro model is not explicitly made.
- The MD simulation results are used to support the two-state model, but the validation and robustness of the CG model and clustering analysis are not sufficiently described.