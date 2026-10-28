## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided
- **Assessment boundary** Scientific claims, methodology, evidence quality, and internal consistency of the manuscript as submitted; no external literature verification performed
- **Shared manuscript claim summary** The author proposes that RNA-DNA triplexes (TRX), a class of flipons, form through Hoogsteen base pairing and interact with a set of proteins (HMGB1, HNRNPU, TP53, AGO, PIWI, REL domain proteins) to regulate chromatin architecture, suppress retroelements, and generate phenotypic diversity. AlphaFold V3 (AF3) models are presented as evidence for these interactions, with claims that TRX nucleate folding of intrinsically disordered proteins and seed context-specific chromatin states.
- **Visible evidence base** AF3 structural models (Figures 1, 3-10), computational triplex sequence analysis (Supplemental Data S1, S2), cited experimental literature, and prior publications by the author
- **Missing materials affecting confidence** AF3 model confidence scores, PDB files (referenced as Supplemental Data S3 but not provided), experimental validation data, negative controls, sequence coordinates for modeled TRX, and details of AF3 input parameters beyond seed and ion counts

## Reviewer
- **Overall assessment** This manuscript presents a broad, speculative framework linking triplex-forming noncoding RNAs to chromatin regulation through AF3-predicted protein interactions. The central thesis is interesting but rests almost entirely on computational predictions that are not experimentally validated. The manuscript lacks quantitative evidence, confidence metrics for the AF3 models, and any direct biochemical or biophysical confirmation of the proposed TRX-protein interactions. While the author acknowledges the predictive nature of the work, the strength of the claims in the abstract and conclusions far exceeds what the evidence supports. The manuscript reads more as a perspective or hypothesis paper than a results-driven research article, yet it is structured as the latter. The writing is dense and assumes substantial prior knowledge, limiting accessibility for a broad readership.
- **Who would be interested in the results, and why** Researchers studying noncoding RNA function, chromatin architecture, retroelement regulation, and structural biology of nucleic acid-protein interactions may find the proposed framework of interest. The AF3 models could serve as a starting point for experimentalists investigating triplex-binding proteins. However, the lack of validation means the audience is limited to specialists who can evaluate the plausibility of the computational predictions and who may use them to generate hypotheses for their own work.
- **Major strengths** The manuscript integrates diverse areas (flipon biology, retroelement evolution, chromatin structure, intrinsically disordered proteins) into a coherent conceptual framework. The use of AF3 to explore TRX-protein interactions is a creative application of a powerful tool. The author is transparent about the predictive nature of the models and provides specific suggestions for experimental follow-up. The discussion of copolar versus apolar TRX and the proposal of RDL (RNA-DNA lasso) structures adds conceptual nuance to the field.
- **Major Concerns** The following concerns are detailed below.
- **Minor Comments** The following comments are detailed below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no confidence metrics for AF3 models), R1-M2 (no experimental validation), R1-M3 (overstated conclusions relative to evidence), R1-M4 (unsubstantiated functional claims for specific proteins)
- **Assessment against Nature-style criteria** Originality: The conceptual framework is original in its synthesis, though individual components (triplex biology, flipons, retroelement regulation) are established. Scientific importance: Potentially high if validated, but currently speculative. Interdisciplinary readership: The manuscript is written for a specialist audience and would not engage a broad interdisciplinary readership in its current form. Technical soundness: The AF3 methodology is not rigorously presented; confidence scores and validation metrics are absent, and the selection criteria for models are subjective. Readability for nonspecialists: Poor; the text assumes deep familiarity with triplex nomenclature, flipon biology, and chromatin terminology without adequate introduction.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a hypothesis-generating framework supported only by unvalidated computational models. Major revisions including confidence metrics, experimental validation (even preliminary), and tempering of claims would be required before the case is established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that AF3 models "reveal interactions" between TRX and specific proteins (abstract, Sections 2.4.1-2.4.4, 2.5, 2.6), implying structural reliability.
- **Evidence pointer** Figures 3-10; Methods Section 4
- **Concern** No AF3 confidence metrics (ipTM, pTM, PAE, or per-residue confidence) are reported for any model. The author states that "AF3 default scoring... did not always assign high scores" and that "manual inspection" was used to select models, but no criteria for this manual selection are provided. Without quantitative confidence measures, the reader cannot assess whether the predicted TRX-protein interfaces are statistically meaningful or artifacts of the modeling process.
- **Why it matters** AF3 predictions are only as reliable as their confidence scores. The absence of these metrics makes the central evidence of the manuscript unverifiable. The author's admission that default scoring was disregarded in favor of manual inspection raises concerns about selection bias and reproducibility.
- **Resolution test** Provide ipTM, pTM, and per-residue confidence scores for all models in the main text or supplementary materials. Include PAE plots for key interfaces. Justify the manual selection criteria with explicit, reproducible rules. If models with low confidence are included, state this clearly and discuss the implications.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim** The manuscript implies that the modeled TRX-protein interactions are biologically relevant, stating that "TRXs help nucleate folding of intrinsically disordered proteins" and that specific proteins "dock" to TRX.
- **Evidence pointer** Abstract; Sections 2.4-2.6; Figures 3-10
- **Concern** No experimental data (biochemical, biophysical, or cellular) are presented to support any of the proposed TRX-protein interactions. The author cites prior experimental work for some proteins (e.g., HNRNPU, TP53) but does not provide direct evidence that these proteins bind TRX in the configurations modeled. The claim that TRX nucleate IDR folding is purely speculative and unsupported by any experimental observation.
- **Why it matters** Computational predictions without experimental validation cannot establish biological function. The manuscript's conclusions depend entirely on the assumption that AF3 models reflect in vivo reality, which is not demonstrated.
- **Resolution test** Include at least one experimental validation, such as electrophoretic mobility shift assays, surface plasmon resonance, or isothermal titration calorimetry, demonstrating binding of a representative protein to a representative TRX. For the IDR folding claim, provide circular dichroism or NMR data showing conformational change upon TRX addition. If such experiments are not feasible, explicitly frame the manuscript as a hypothesis paper and remove definitive language.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim strength
- **Claim** The abstract states that "TRXs help set the boundaries of active chromatin, repressing the expression of most EREs" and that the models "reveal interactions" between proteins and TRX, implying established fact.
- **Evidence pointer** Abstract; Section 5 (Conclusions)
- **Concern** The language throughout the abstract and conclusions presents speculative computational findings as established biological mechanisms. The author uses "reveal," "help set," and "repressing" without qualifying that these are predictions. The conclusions section states that "flipons connect the early tinkers with the lifeforms that we see today" and that "each cell is likely unique, as each colors its chromaverse differently," which are philosophical extrapolations presented as scientific conclusions.
- **Why it matters** Overstatement of claims misleads readers and undermines scientific integrity. The distinction between hypothesis and established finding is critical for the manuscript to be evaluated fairly.
- **Resolution test** Revise the abstract and conclusions to clearly distinguish predictions from established findings. Use conditional language (e.g., "may," "suggests," "is predicted to") for all AF3-based claims. Remove or clearly label speculative evolutionary and philosophical statements.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Specificity of claims
- **Claim** The manuscript claims specific functional roles for individual proteins, e.g., "HNPRNPU can dock to both anti-parallel and parallel TRX" and "TP53 tetramers... dock to both copolar and apolar TRX," with implied functional consequences.
- **Evidence pointer** Sections 2.4.1-2.4.2; Figures 3-4
- **Concern** The AF3 models show predicted binding poses, but the manuscript does not demonstrate that these interactions are specific (i.e., that the proteins do not bind any nucleic acid structure promiscuously) or that the modeled TRX sequences are physiologically relevant. The functional implications (e.g., TP53 suppressing EREs via TRX binding) are inferred without direct testing.
- **Why it matters** Without specificity controls and functional assays, the reader cannot distinguish meaningful interactions from artifacts of the modeling approach. The manuscript risks overinterpreting computational poses as biological mechanisms.
- **Resolution test** Include AF3 models with mutated TRX sequences or scrambled controls to show that binding is sequence- or structure-specific. For at least one protein, perform a functional assay (e.g., reporter gene assay, chromatin immunoprecipitation) to test the predicted regulatory outcome.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods Section 4
- **Evidence pointer** Section 4
- **Issue** The Methods section provides insufficient detail for reproducing the AF3 models. The author states that "a subset of putative triplex-forming sequences would not fold" and that "the incorporation of non-canonical triplets would overcome this limitation," but does not specify which sequences were used, how non-canonical triplets were defined, or how the "particular AF3 seed and a set of ion conditions" were selected.
- **Required correction** Provide a complete list of TRX sequences used, including their genomic coordinates or source, the exact AF3 input parameters (seed, ion concentrations, number of ions), and a description of the filtering criteria for including or excluding models. This information should be in the main text or supplementary materials.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2
- **Issue** The distinction between copolar and apolar TRX is introduced with reference to Figure 1E,F, but the figure is not described in sufficient detail in the text. The reader is expected to understand the structural difference without a clear explanation of the hydrogen bonding patterns or strand orientations.
- **Required correction** Add a brief textual description of the structural differences between copolar and apolar TRX, including a schematic explanation of the hydrogen bonding patterns, before referring the reader to the figure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract; Sections 1, 2, 3
- **Issue** The term "chromaverse" is used without a formal definition. While it is described as capturing "the multiplicity of chromatin states produced," the term is not standard in the field and its introduction is not clearly motivated.
- **Required correction** Define "chromaverse" explicitly at first use, explain its relationship to existing concepts (e.g., chromatin states, topologically associating domains), and justify why a new term is needed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Section 2.4.1 vs. Section 2.4.2
- **Evidence pointer** Sections 2.4.1-2.4.2
- **Issue** The manuscript states that HNRNPU binds TRX "independent of the C-terminal RGG domain," but later discusses the RGG domain's role in G-quadruplex binding. The relationship between these two binding modes is not clarified, and the reader is left wondering whether the two functions are mutually exclusive or cooperative.
- **Required correction** Clarify whether HNRNPU can simultaneously bind TRX and G-quadruplexes, and discuss the potential functional interplay between these two binding activities.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 3-10
- **Evidence pointer** Figures 3-10
- **Issue** The figure legends do not specify the color scheme, the representation of the TRX (e.g., cartoon, surface), or the orientation of the protein relative to the nucleic acid. This makes it difficult to interpret the models without accessing the PDB files.
- **Required correction** Expand the figure legends to describe the visualization parameters, including color coding for protein domains, nucleic acid strands, and any ions or water molecules shown.

## Risk / unsupported claims
- The claim that "TRXs help nucleate folding of intrinsically disordered proteins" is unsupported by any experimental or computational evidence presented in the manuscript.
- The claim that "TRXs help set the boundaries of active chromatin, repressing the expression of most EREs" is presented as established fact but is inferred from unvalidated models and prior literature without direct evidence in this manuscript.
- The claim that "PIWIL4 generates these fragments de novo from DRHs, after localization to RDLs, via its RNase H activity" is speculative and not directly tested.
- The claim that "the interaction of HMGB1 with TRX is supported by the HMGB1 AF3 models" is unverifiable without confidence metrics.
- The claim that "AF3 can be nudged by setting input conditions and specifying the model seed" implies a level of control over the modeling process that is not standard practice and requires justification.
- The evolutionary narrative connecting "early tinkers" to modern life is philosophical speculation and is not testable from the presented evidence.
- The statement that "each cell is likely unique, as each colors its chromaverse differently" is an unsupported generalization.