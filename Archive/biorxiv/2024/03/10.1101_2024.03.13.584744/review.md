## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and extended data descriptions
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors use time-resolved cryo-electron microscopy (tr-Spotiton) to capture four structural intermediates (I1a–I1d) populated 120 or 500 ms after mixing E. coli σ70-RNAP with the λPR promoter. They propose a stepwise mechanism of promoter melting involving rapid nucleation, sequential nt-strand read-out, clamp closure, and σ70 ejection, with full bubble opening preceding the rate-limiting step.
- **Visible evidence base** Cryo-EM maps and atomic models for four intermediates (I1a–I1d) and one closed complex (RPc at 5°C); 3D variability analysis; disulfide crosslinking and abortive transcription assays; deposition IDs for EMDB and PDB
- **Missing materials affecting confidence** No supplementary figures, videos, or tables were provided; no detailed validation statistics (e.g., FSC curves, model-to-map fit metrics) beyond nominal resolutions; no kinetic data directly measuring interconversion rates between intermediates; no quantitative comparison of population distributions across conditions beyond Jensen-Shannon distances

## Reviewer
- **Overall assessment** This manuscript presents a technically impressive application of time-resolved cryo-EM to capture transient intermediates in bacterial RNA polymerase promoter melting. The structural data are likely of high quality and the proposed mechanistic model is plausible and well-aligned with prior biochemical studies. However, several claims, particularly regarding the order of events and the universality of the proposed mechanism, are not fully supported by the evidence presented. The lack of detailed validation metrics and the limited kinetic context reduce confidence in some conclusions.
- **Who would be interested in the results, and why** Researchers studying transcription initiation mechanisms, RNA polymerase structure and function, and those interested in time-resolved cryo-EM methodology. The work provides a new view of promoter melting intermediates and may inform studies on transcriptional regulation and antibiotic action.
- **Major strengths** 1) Novel application of time-resolved cryo-EM to a biologically important and previously intractable problem. 2) High-quality structural data with multiple intermediates resolved at sub-second timescales. 3) Integration of structural findings with prior biochemical and biophysical data. 4) Clear presentation of a stepwise mechanism with testable predictions.
- **Major Concerns** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Minor Comments** R1-m1, R1-m2, R1-m3, R1-m4, R1-m5
- **Technical failings that need to be addressed before the case is established** R1-M1 (kinetic assignment), R1-M2 (validation metrics), R1-M4 (generality of mechanism)
- **Assessment against Nature-style criteria** Originality: High. The use of time-resolved cryo-EM to capture promoter melting intermediates is novel and represents a methodological advance. Scientific importance: High. The results address a long-standing question in transcription initiation and provide a structural framework for understanding promoter melting. Interdisciplinary readership: Moderate. The work will appeal primarily to structural biologists and transcription researchers, though the methodological aspects may interest a broader cryo-EM audience. Technical soundness: Generally strong, but with gaps in validation and kinetic support as noted. Readability for nonspecialists: The abstract and introduction are accessible, but the results section assumes significant background in transcription and cryo-EM.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding kinetic interpretation and validation metrics.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Kinetic interpretation
- **Claim pointer** The authors state that the four intermediates (I1a–I1d) represent sequential steps in the promoter melting pathway and that full bubble opening precedes the rate-limiting step.
- **Evidence pointer** Results section "Direct visualization of DNA melting intermediates by tr-Spotiton"; Figure 1c; Discussion section "Full promoter opening precedes the rate-limiting step at λPR"
- **Concern** The assignment of the four intermediates as sequential steps on a single pathway is inferred from population distributions and structural features, but no direct kinetic data (e.g., time-dependent population changes) are presented. The claim that full bubble opening precedes the rate-limiting step relies on the assumption that I1d is on-pathway and that its formation is fast relative to the I1-to-I2 conversion. However, the manuscript does not provide measurements of interconversion rates between I1a–I1d, nor does it rule out the possibility that some intermediates are off-pathway or represent alternative conformations in equilibrium.
- **Why it matters** The central mechanistic conclusion of the paper depends on the temporal ordering of the intermediates. Without kinetic evidence, the proposed sequence remains speculative and could mislead subsequent studies.
- **Resolution test** Provide time-resolved population data (e.g., from multiple time points) showing that the population of I1d increases at the expense of earlier intermediates, or use computational approaches (e.g., Markov state models) to infer kinetic connectivity. Alternatively, clearly state the limitation that the ordering is inferred from structural progression and not directly measured.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural validation
- **Claim pointer** The manuscript claims high-resolution structures for four intermediates with nominal resolutions from 3.0 to 3.4 Å.
- **Evidence pointer** Table 1; Extended Data Figures 2, 3, 6, 7
- **Concern** The manuscript reports nominal resolutions but does not provide key validation metrics such as gold-standard FSC curves, model-to-map correlation coefficients, or per-residue model quality indicators (e.g., Ramachandran outliers, rotamer outliers). Without these, the reliability of the structural interpretations, particularly for the dynamic single-stranded DNA regions, cannot be fully assessed.
- **Why it matters** The structural models are the foundation of the mechanistic claims. Inadequate validation undermines confidence in the interpretation of specific interactions (e.g., nt-strand read-out, σ70 ejection).
- **Resolution test** Include supplementary validation figures with FSC curves, model-to-map fit statistics, and a table of model refinement statistics. Provide representative density for key regions, especially the nt-strand and σ70 domains.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Population analysis
- **Claim pointer** The authors report that the population distribution of intermediates is reproducible across three independent 120 ms datasets and that the 500 ms dataset is skewed towards I1d.
- **Evidence pointer** Results section "Direct visualization of DNA melting intermediates by tr-Spotiton"; Supplementary Table 1
- **Concern** The statistical significance of the population differences between time points is not assessed. The Jensen-Shannon distance is reported, but no confidence intervals or significance tests are provided. Additionally, the criteria for assigning particles to discrete classes via 3DVA clustering are not fully described, and the possibility of continuous conformational variability being over-discretized is not discussed.
- **Why it matters** The claim that the 500 ms population is "significantly different" and skewed towards I1d is used to support the temporal ordering. Without statistical rigor, this conclusion is weakened.
- **Resolution test** Provide statistical tests (e.g., bootstrap or permutation tests) for population differences. Describe the clustering procedure in detail, including the number of clusters tested and the stability of the solution.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generality of mechanism
- **Claim pointer** The authors suggest that the observed mechanism likely describes DNA opening at many bacterial promoters.
- **Evidence pointer** Discussion section "Transcription bubble nucleation" and final paragraph
- **Concern** The study is performed at a single promoter (λPR) under specific conditions (high concentrations, presence of CHAPSO or FC8F). The claim of generality is extrapolated from conserved structural features but is not tested. The authors do note that sequence differences may alter the order of events, but the extent of this variability is not explored.
- **Why it matters** Overgeneralization could lead to incorrect assumptions about promoter-specific regulation. The claim should be tempered or supported by additional data from other promoters.
- **Resolution test** Either soften the claim to be specific to λPR and similar promoters, or provide preliminary data from one or more additional promoters to support generality.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Role of σ70 ejection
- **Claim pointer** The authors propose that clamp closure drives σ70 unfolding and ejection, and that this is essential for progress through the pathway.
- **Evidence pointer** Results section "Stepwise closure of the RNAP clamp partially unfolds and ejects σ70"; Figure 4; Figure 5
- **Concern** The crosslinking experiments show that preventing σ70 unfolding inhibits transcription, but the structural data do not directly demonstrate that σ70 ejection is required for the I1-to-I2 transition. The correlation between clamp closure and σ70 disorder is suggestive but not causal. The possibility that σ70 ejection is a consequence rather than a driver of the transition is not excluded.
- **Why it matters** The proposed mechanism assigns a specific functional role to σ70 ejection. If this is incorrect, the model of the rate-limiting step would need revision.
- **Resolution test** Perform additional experiments, such as time-resolved crosslinking or single-molecule FRET, to directly monitor σ70 ejection relative to DNA opening and clamp closure.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "transient intermediates pile up before overcoming a rate-limiting step" is somewhat vague. It is unclear whether "pile up" refers to a kinetic bottleneck or a thermodynamic accumulation.
- **Required correction** Clarify the meaning, e.g., "transient intermediates accumulate transiently before the rate-limiting step" or rephrase to describe the kinetic context more precisely.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section
- **Evidence pointer** Results section "Duplex DNA rapidly unwinds at λPR"
- **Issue** The term "unwinds" is used to describe DNA melting, but "unwinding" typically implies a rotational component. The structural data may not directly measure unwinding.
- **Required correction** Use "melts" or "separates" instead of "unwinds" unless unwinding is directly demonstrated.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1c
- **Evidence pointer** Figure 1c
- **Issue** The correlation between clamp position and progress along the pathway is shown, but the axes and units are not fully described in the text.
- **Required correction** Provide a clear description of the metric used for clamp position (e.g., degrees relative to RPo) and the measure of progress (e.g., interface area or RMSD).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods section "Cryo-EM data acquisition and processing"
- **Issue** The description of the 3DVA clustering procedure is brief. The number of components, the choice of GMM clusters, and the criteria for selecting the clamp-related component are not fully detailed.
- **Required correction** Expand the methods to include these details, or reference a prior publication where the approach is fully described.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Discussion
- **Evidence pointer** Discussion, final paragraph
- **Issue** The sentence "Because these events likely describe DNA opening at many bacterial promoters" is speculative and could be seen as overstating the findings.
- **Required correction** Soften to "may describe" or "could inform understanding of" to avoid overgeneralization.

## Risk / unsupported claims
- The claim that the four intermediates represent a sequential pathway is not directly supported by kinetic data; the ordering is inferred from structural progression.
- The claim that full bubble opening precedes the rate-limiting step is based on the assumption that I1d is on-pathway and that its formation is fast; this is not directly measured.
- The claim that the mechanism is general to many bacterial promoters is extrapolated from a single promoter and is not tested.
- The assertion that σ70 ejection is essential for progress through the pathway is supported by crosslinking data but not by direct structural observation of the ejection event.
- The manuscript states that "the same four intermediates were observed" in the FC8F experiment, but no quantitative comparison of populations or structures is provided to support this claim.