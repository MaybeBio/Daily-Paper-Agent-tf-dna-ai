## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, and materials and methods
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and conclusions as presented in the provided text
- **Shared manuscript claim summary** The authors propose that DONSON, a metazoan protein associated with microcephalic primordial dwarfism, is required for CMG helicase assembly during DNA replication initiation in vertebrates. Using AlphaFold-Multimer in silico screening followed by experimental validation in Xenopus egg extracts and mammalian cells, they identify DONSON as a scaffold for a pre-loading complex containing GINS, TOPBP1, and DNA polymerase epsilon, which docks onto MCM2-7 to deliver GINS. A patient-derived mutation (M446T) modeled in mice recapitulates microcephalic dwarfism phenotypes, linking defective CMG assembly to disease.
- **Visible evidence base** Abstract, Results sections (7 subsections), Discussion, Materials and Methods, figure legends referenced in text (Figs. 1-6, S1-S21), tables S1-S3
- **Missing materials affecting confidence** Actual figures and figure panels are not provided; supplementary figures and tables are referenced but not included; raw data and statistical details are not fully available; the full proteome screen results (table S2) are not shown

## Reviewer
- **Overall assessment** This manuscript presents a compelling and well-integrated study combining computational prediction with biochemical and genetic validation to establish a novel role for DONSON in CMG helicase assembly. The work addresses a fundamental question in eukaryotic DNA replication and provides a plausible mechanistic framework that unifies observations across species. The use of AlphaFold-Multimer as a discovery tool is innovative and timely. However, several technical concerns regarding the strength of the in silico predictions, the interpretation of chromatin-binding experiments, and the causal link between CMG assembly defects and the observed dwarfism phenotype require careful consideration. The manuscript is well-written and the logic is generally clear, but some claims extend beyond the direct evidence presented.
- **Who would be interested in the results, and why** Researchers in DNA replication, genome stability, and cell cycle biology will find this work directly relevant. The study also has broader appeal to the structural biology community interested in applying AlphaFold-based approaches to biological discovery, and to clinicians and geneticists studying microcephalic dwarfism and related developmental disorders. The demonstration that in silico interaction screening can identify biologically meaningful protein complexes may interest a wide audience in computational biology and proteomics.
- **Major strengths**
  - The study addresses a long-standing question in the field: how CMG helicase assembly is orchestrated in metazoans, where the yeast paradigm does not fully apply.
  - The combination of AlphaFold-Multimer screening with rigorous biochemical validation in a physiologically relevant cell-free system (Xenopus egg extracts) is powerful and mutually reinforcing.
  - The identification of a patient-derived mutation that disrupts CMG assembly and recapitulates disease in a mouse model provides a direct link between the molecular mechanism and human pathology.
  - The proposed model, in which DONSON functionally replaces yeast Sld2 in the pre-LC, is conceptually elegant and testable.
  - The demonstration that in silico screening can be used for ab initio functional discovery is timely and will likely stimulate similar approaches.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of in silico predictions
- **Claim pointer** The authors claim that AlphaFold-Multimer screening identified DONSON interactions with SLD5, TOPBP1, POLE2, and MCM3 with high confidence, and that these predictions were validated experimentally.
- **Evidence pointer** Results section "A model for DONSON function based on in silico protein-protein interaction screening"; Figs. 2B-E; table S1
- **Concern** The manuscript does not provide sufficient detail on the criteria used to define a "positive" interaction in the AlphaFold-Multimer screen. The authors mention confidence metrics (pLDDT, pAE, pDOCKQ) but do not specify thresholds, how false positives were controlled, or how the screen was benchmarked. Given that AlphaFold-Multimer is known to produce high-confidence predictions for some non-biological contacts, the absence of a clear statistical framework for ranking candidates weakens the claim that the screen was genuinely predictive. Additionally, the screen was limited to ~70 replication factors, and it is unclear whether known non-interactors were included as negative controls.
- **Why it matters** The in silico screen is a central pillar of the paper's novelty and its claim to methodological innovation. If the screen's specificity and sensitivity are not rigorously established, the conclusion that DONSON's role in CMG assembly was discovered through this approach is not fully supported. The paper's broader claim that in silico screening can accelerate mechanistic discovery depends on demonstrating that the method reliably distinguishes true interactors from artifacts.
- **Resolution test** Provide a detailed description of the screen's scoring criteria, including specific thresholds for pDOCKQ, interface pLDDT, and pAE. Include a benchmark against known protein complexes and non-interacting pairs to demonstrate specificity. Show the full ranked list of candidates for at least one species, with the scores for all 70 factors, so readers can assess the separation between top candidates and the rest.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for direct DONSON-MCM3 interaction
- **Claim pointer** The authors state that "DONSON docks the pre-LC onto MCM2-7" and that the predicted DONSON-MCM3 interaction is important for delivering GINS to chromatin.
- **Evidence pointer** Results section "DONSON's predicted MCM3 binding domain is necessary for CMG assembly"; Fig. 4C-E; fig. S11E
- **Concern** The evidence for a direct DONSON-MCM3 interaction is indirect. The authors show that mutations in the predicted MCM3-binding helix of DONSON (DEWE→RRAR) impair chromatin binding and CMG assembly, but they do not demonstrate direct binding between DONSON and MCM3 using purified proteins or co-immunoprecipitation from replicating extracts. The authors acknowledge that MCM3 did not co-IP with DONSON from nonreplicating extract, which is consistent with a context-dependent interaction, but this also means the proposed docking mechanism is inferred rather than demonstrated. The possibility that the DEWE→RRAR mutations disrupt DONSON folding or stability, rather than specifically the MCM3 interaction, is not excluded.
- **Why it matters** The proposed mechanism hinges on a specific docking event between DONSON and MCM3. Without direct biochemical evidence for this interaction, alternative explanations for the mutant phenotype (e.g., misfolding, altered dynamics, indirect effects on complex stability) remain viable. The claim that DONSON acts as a "molecular matchmaker" delivering GINS to its binding site requires demonstration of the physical interaction it is supposed to mediate.
- **Resolution test** Perform direct binding assays (e.g., pull-down with purified proteins, surface plasmon resonance, or cross-linking) between DONSON and MCM3 or the MCM2-7 complex. Show that the DEWE→RRAR mutation specifically abolishes this interaction without affecting DONSON dimerization or binding to GINS and TOPBP1. Alternatively, demonstrate that a DONSON mutant lacking the MCM3-binding helix cannot rescue replication in DONSON-depleted extracts, while a mutant that retains MCM3 binding but lacks other functions can.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Causal link between CMG assembly defect and dwarfism phenotype
- **Claim pointer** The authors state that "A patient-derived DONSON mutation compromises CMG assembly and recapitulates microcephalic dwarfism in mice," implying a causal relationship between defective CMG assembly and the disease phenotype.
- **Evidence pointer** Results section "Defective CMG assembly is associated with microcephalic dwarfism in a mouse model"; Fig. 6; figs. S18-S19
- **Concern** The mouse model demonstrates an association between the M446T mutation and dwarfism phenotypes, and the authors show reduced chromatin-bound CDC45 and GINS in mutant cells. However, the manuscript does not establish that the CMG assembly defect is the primary cause of the observed developmental abnormalities. The M446T mutation also reduces DONSON protein levels, and the authors previously reported roles for DONSON in fork progression and ATR signaling. It is possible that reduced DONSON levels affect multiple processes, and the dwarfism phenotype could result from combined effects on replication initiation, elongation, and checkpoint signaling rather than from the CMG assembly defect alone. The authors do not attempt to separate these contributions.
- **Why it matters** The paper claims to unify understanding of microcephalic dwarfism by implicating defective CMG assembly. If the phenotype is primarily due to reduced DONSON levels or impaired elongation, the mechanistic link to CMG assembly is weakened. This distinction matters for understanding the pathophysiology of DONSON-associated diseases and for potential therapeutic strategies.
- **Resolution test** Rescue experiments in the mouse model or in patient-derived cells with a DONSON variant that restores CMG assembly but not elongation (or vice versa) would help disentangle these contributions. Alternatively, a knock-in mouse carrying a mutation that specifically disrupts CMG assembly without affecting protein stability or elongation would provide stronger causal evidence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the proposed model across metazoans
- **Claim pointer** The authors state that "DONSON scaffolds a vertebrate pre-LC" and suggest that this mechanism is general across metazoans, citing predictions in worms and flies.
- **Evidence pointer** Results section "A model for DONSON function based on in silico protein-protein interaction screening"; table S1; Discussion
- **Concern** The experimental validation is performed exclusively in Xenopus and human cells. The in silico predictions for worms and flies are presented as supporting evidence for evolutionary conservation, but no functional data from these organisms are provided. The authors cite a worm study (ref 44) but do not describe its findings in sufficient detail to assess whether it supports their model. Given that the yeast pre-LC differs substantially from the proposed vertebrate complex, the claim of a unified metazoan mechanism requires stronger cross-species validation.
- **Why it matters** The paper's conceptual contribution includes the claim that the DONSON-based pre-LC is a conserved metazoan feature. If the mechanism is specific to vertebrates or differs in important ways in other metazoans, the generality of the model is overstated. This affects how the findings will be interpreted by the broader community.
- **Resolution test** Provide functional data from at least one non-vertebrate metazoan (e.g., worm or fly) demonstrating that DONSON is required for CMG assembly and that the key interactions are conserved. Alternatively, temper the claims of generalizability and clearly state that the model is based on vertebrate data with in silico support from other species.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of replication assays
- **Claim pointer** The authors conclude that DONSON is required for CMG assembly and DNA replication based on depletion and rescue experiments in Xenopus egg extracts.
- **Evidence pointer** Results section "DONSON is required for CMG assembly in frog egg extracts"; Fig. 1C-E; fig. S1
- **Concern** The manuscript reports that DONSON depletion abolishes DNA replication and that recombinant DONSON fully rescues replication. However, the quantitative details are limited. The extent of depletion is not quantified (e.g., what fraction of endogenous DONSON remains after immunodepletion?), and the efficiency of rescue is described qualitatively. The figure legends referenced do not provide numerical values or statistical comparisons. Without these details, it is difficult to assess the robustness of the conclusion that DONSON is essential for replication.
- **Why it matters** The central claim that DONSON is required for CMG assembly depends on the quality of the depletion and rescue experiments. If depletion is incomplete or rescue is partial, the interpretation could be more nuanced. Quantitative data would also allow readers to compare the severity of the DONSON phenotype with that of other replication factors.
- **Resolution test** Provide quantification of depletion efficiency (e.g., western blot band intensities with standard deviations), replication levels across multiple independent experiments, and statistical tests comparing control, depleted, and rescued conditions. Include dose-response data for recombinant DONSON rescue if available.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of model presentation
- **Affected element** Fig. 2H and associated text
- **Evidence pointer** Results section "A model for DONSON function based on in silico protein-protein interaction screening"
- **Issue** The model figure (Fig. 2H) is described in the text but the actual figure is not available for review. The description of the docking mechanism and the conformational changes proposed during CMG assembly would benefit from a clearer step-by-step explanation in the text, particularly regarding the order of events (e.g., when TOPBP1 dissociates, when Pol ε is displaced).
- **Required correction** Expand the text description of the model to include a numbered sequence of events, and ensure the figure legend clearly labels each component and step. Consider adding a schematic timeline of CMG assembly with and without DONSON.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figs. 4A, 5B, 6A-C, and associated legends
- **Evidence pointer** Results sections "DONSON binding to GINS and TOPBP1, but not Pol ε, is required for CMG assembly" and "Defective CMG assembly is associated with microcephalic dwarfism in a mouse model"
- **Issue** The text reports significant differences but does not consistently provide effect sizes, confidence intervals, or exact p-values. For the mouse phenotype data, the number of animals per genotype and the statistical tests used are not clearly stated in the text.
- **Required correction** Add a supplemental table summarizing all statistical tests, sample sizes, effect sizes, and exact p-values for each comparison. Ensure figure legends state the statistical test used and the number of biological replicates.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of alternative interpretations
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraphs on DONSON function and mechanism
- **Issue** The discussion does not adequately address alternative interpretations of the data. For example, the possibility that DONSON's role in CMG assembly is indirect (e.g., through effects on chromatin structure or MCM complex stability) is not discussed. The authors also do not discuss why DONSON is not required for CMG assembly in yeast, given that the proposed mechanism is presented as a metazoan-specific adaptation.
- **Required correction** Add a paragraph in the Discussion that explicitly considers alternative models and explains why the proposed mechanism is favored. Address the evolutionary question of why metazoans require DONSON while yeast does not.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of methods for AlphaFold screen
- **Affected element** Materials and Methods, "AlphaFold2-multimer (AF-M) screen"
- **Evidence pointer** Materials and Methods section
- **Issue** The methods describe the computational setup but do not specify the version of AlphaFold-Multimer, the exact parameters used for MSA generation, or how the "common set of ~70 core DNA replication factors" was selected. The criteria for including orthologs from different species are also unclear.
- **Required correction** Provide the full list of 70 proteins for each species, the version and parameters of AlphaFold-Multimer, and the rationale for protein selection. Consider depositing the code and raw predictions in a public repository.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Not applicable
- **Issue** The manuscript references many supplementary figures and tables, but the main text does not always clearly indicate which figure panel supports a specific claim. For example, the statement that "DONSON binding to chromatin was blocked by CDKi, DDKi, and geminin" references Fig. 1F, but the reader cannot tell from the text which panels show which inhibitor.
- **Required correction** In the text, explicitly reference the specific panels (e.g., "Fig. 1F, lanes 3-4") for each experimental result. Ensure all supplementary figures are mentioned in the main text at the appropriate point.

## Risk / unsupported claims
- The claim that "in silico screening alone would point towards DONSON's function in CMG assembly" is not fully supported. The proteome-wide screen (table S2) is described but the results are not shown, and the authors acknowledge that GO-term analysis did not identify DNA replication as a top function. The claim that the second round of predictions improved the ranking is based on data not presented.
- The statement that "DONSON has replaced the function of Sld2 in vertebrate pre-LC assembly" is presented as a conclusion but is more accurately a hypothesis. The authors show functional analogy but do not demonstrate evolutionary replacement or functional equivalence.
- The claim that "DONSON is generally required for CMG assembly in metazoans" extends beyond the experimental data, which are limited to vertebrates. The worm data are cited but not described in sufficient detail.
- The proposed model of sequential CMG assembly involving DONSON dimer disengagement and MCM rotation is speculative and is acknowledged as such by the authors, but the speculative nature should be more clearly flagged in the main text.
- The statement that "DONSON functions at the final stage of CMG assembly" is based on the observation that TRESLIN-MTBP recruitment is unaffected while CDC45 and GINS recruitment is defective. This is a reasonable inference but is not directly demonstrated; the authors do not show that DONSON acts after TRESLIN-MTBP loading in a temporal sequence.