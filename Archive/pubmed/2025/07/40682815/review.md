## Review setup
- **Input scope** Full manuscript text (abstract, materials and methods, results, discussion) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and evidentiary support as presented in the text; no assessment of figures, tables, or supplementary data that were not provided
- **Shared manuscript claim summary** The authors report that AR structure and function are conserved from cartilaginous fish to humans; that specific ELMs, including a 23FxxLF27 motif mediating N/C interactions and an 860LxxLL864 motif in the LBD, are conserved and functionally required; that a cryptic phosphorylation site at S792 is an ancient suppressive signal conserved from fish to humans; and that similar phospho-regulatory motifs exist in other steroid hormone receptors and their ancestors
- **Visible evidence base** Multiple sequence alignments of 536 AR orthologs; SWISS-Model and AlphaFold3 structural predictions; molecular dynamics simulations using ratchet-and-pawl MD with bias functional selection; site-directed mutagenesis with transcriptional assays, western blotting, immunofluorescence, and radioligand binding in HEK293T and COS1 cells
- **Missing materials affecting confidence** All figures, tables, and supplementary materials; specific numerical data for transcriptional assays, binding experiments, and statistical analyses; sequence alignment details; structural model quality metrics; MD simulation convergence and validation data

## Reviewer
- **Overall assessment** This manuscript addresses an interesting evolutionary question about the conservation of linear motifs and regulatory phosphorylation sites in the androgen receptor across vertebrates. The phylogenetic scope is broad and the combination of computational and experimental approaches is commendable. However, the central claims regarding the functional requirement of the LxxLL motif for androgen binding and the evolutionary conservation of the S792 phospho-regulatory mechanism rest on evidence that cannot be fully evaluated from the text alone. The manuscript would benefit from clearer presentation of quantitative data and more rigorous statistical support for key conclusions.

- **Who would be interested in the results, and why** Researchers studying nuclear receptor biology, particularly androgen receptor structure-function relationships and their evolution; investigators interested in the evolution of linear motifs and intrinsically disordered regions in transcription factors; those studying post-translational regulation of steroid hormone receptors; and evolutionary biologists examining the molecular basis of conserved regulatory mechanisms across vertebrates.

- **Major strengths** The phylogenetic sampling across 536 species spanning major vertebrate classes is substantial. The combination of in silico structure prediction, molecular dynamics simulations, and experimental validation represents a multidisciplinary approach appropriate for the question. The identification of a potential cryptic phosphorylation site with functional consequences for AR regulation is interesting. The comparative analysis across the SHR family and ancestral receptors adds evolutionary depth.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the LxxLL motif in the LBD is "required for androgen binding" based on the observation that the LxxAA mutation "nearly abolishes androgen binding."
- **Evidence pointer** Results section, Figure 3E (figure not provided)
- **Concern** The text states that the LxxAA mutation nearly abolishes androgen binding, but no quantitative data are presented. The radioligand binding assay methodology is not described in sufficient detail to assess its reliability. Specifically, it is unclear whether saturation binding or single-point assays were performed, what concentrations of radioligand were used, how specific binding was calculated, and whether the effect on binding could be due to protein misfolding or degradation rather than a direct role of the motif in ligand coordination. The claim that this motif is "required" for androgen binding is strong and requires demonstration that the mutant protein is properly folded and expressed at levels comparable to wild-type.
- **Why it matters** This claim is central to the paper's thesis that the LxxLL motif is functionally essential. If the mutation causes global misfolding rather than specifically disrupting ligand binding, the conclusion would be substantially weakened. The distinction between a direct role in ligand binding versus a structural role in protein stability is important for interpreting the evolutionary conservation of this motif.
- **Resolution test** Provide quantitative binding data (Kd and Bmax values) for wild-type and mutant AR from saturation binding experiments, with evidence of equivalent protein expression and proper folding (e.g., circular dichroism, limited proteolysis, or binding of a conformation-specific antibody). Alternatively, demonstrate that the mutant retains activity in an assay that does not require ligand binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that molecular dynamics simulations reveal that S792 is exposed only in the unfolded state and that phosphorylation at this site interferes with folding towards a ligand-binding-competent conformation.
- **Evidence pointer** Results section, Figure 4C-E (figures not provided)
- **Concern** The MD simulation methodology is described in the Materials and methods, but critical details are missing. The force field, water model, simulation box size, ionic conditions, temperature coupling, and pressure coupling are not specified. More importantly, the bias functional selection of "least biased" trajectories is described, but no convergence criteria are provided. The claim that S792 is "exposed only in the U state" is based on three trajectories per condition, which is a very small sample. The text does not report the statistical significance of this observation or whether it was consistent across all trajectories. The extrapolation from in silico folding simulations to a biological mechanism of phosphorylation-dependent regulation requires stronger validation.
- **Why it matters** The MD simulations provide the mechanistic basis for the proposed model that S792 phosphorylation occurs during folding and prevents maturation. If the simulations are not converged or the sampling is insufficient, the conclusions drawn from them are not reliable. The small number of trajectories and lack of quantitative analysis undermine confidence in this central mechanistic claim.
- **Resolution test** Provide evidence of simulation convergence (e.g., block averaging, multiple independent runs with consistent results), report the number of independent folding events observed, and quantify the fraction of trajectories in which S792 exposure occurs in the unfolded state. Ideally, validate the computational predictions with experimental approaches such as hydrogen-deuterium exchange or limited proteolysis under conditions that trap folding intermediates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive caution
- **Claim pointer** The authors claim that the presence of the RxRxxSxxF motif in fish and its conservation through humans indicates that this is an "ancient suppressive signal" that evolved early and has been maintained.
- **Evidence pointer** Results section, Figure 5A and Supplementary Figures S1-S5 (figures not provided)
- **Concern** The evolutionary interpretation assumes that sequence conservation implies functional conservation. While the authors test fish AR variants in a human cell line, this heterologous system may not reflect the endogenous regulatory context in fish. The finding that alanine substitution enhances transactivation in response to DHT but not 11-KT for hsAR and nfAR, but not drAR, is not explained mechanistically. The claim of an "ancient suppressive signal" would be strengthened by demonstrating that the phosphorylation site is actually utilized in fish, for example by showing endogenous phosphorylation of fish AR or by testing the effect of kinase inhibitors in fish cells.
- **Why it matters** The evolutionary narrative is a key selling point of the paper. If the functional significance of the S792 site is only demonstrated in a heterologous human cell system, the claim that this is an ancient conserved regulatory mechanism is overstated. The differential effects between DHT and 11-KT, and between drAR and nfAR, suggest a more complex picture than a simple conserved suppressive signal.
- **Resolution test** Demonstrate phosphorylation of the corresponding serine in fish AR in a relevant fish cell line or in vitro with fish kinases. Alternatively, show that the differential effects between drAR and nfAR can be explained by structural or sequence differences in the surrounding motif. Provide a more nuanced interpretation that accounts for the observed species-specific differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation
- **Claim pointer** The authors claim that SWISS-Model and AlphaFold3 predictions show that AR structure is conserved across species and that the S792A substitution does not affect folding.
- **Evidence pointer** Results section, Figure 5B (figure not provided)
- **Concern** The text states that "SWISS-Model returned highly similar structures for the species analyzed" and that "SWISS-Model and Alphafold3 predictions for the structures of nfAR isoforms 1 and 2 yielded highly similar structures." However, no quantitative measures of structural similarity are provided (e.g., RMSD values, TM-scores). The claim that the S792A substitution does not affect folding is based on comparison of predicted structures, but the text does not specify whether the predictions were made for the mutant or only for the wild-type. If only wild-type structures were compared across species, this does not directly address the effect of the mutation.
- **Why it matters** The structural predictions are used to support the interpretation that the functional effects of the LxxAA and S792D mutations are due to specific disruption of protein-protein interactions or phosphorylation mimicry rather than global misfolding. Without quantitative comparison of predicted structures, this interpretation is not well supported.
- **Resolution test** Provide quantitative structural comparison metrics (RMSD, TM-score) for the predicted structures across species and for wild-type versus mutant proteins. If mutant structures were not predicted, perform these predictions and include the comparison.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The opening sentence is vague and does not clearly state the specific question being addressed. The phrase "How essential trans-active factors that control gene expression evolved while maintaining their ability to interact with their natural effectors and cis-active elements on DNA" is overly general and could apply to any transcription factor.
- **Required correction** Revise the opening to state the specific question more directly, such as "How did the androgen receptor evolve its regulatory linear motifs and phosphorylation sites while maintaining ligand-binding and transactivation functions across vertebrates?"

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, transcriptional assays
- **Evidence pointer** Results section, Figure 3D (figure not provided)
- **Issue** The text states that the LxxAA mutation "suppressed" transactivation but does not report effect sizes, confidence intervals, or the number of independent experiments. The statistical methods are not described in the Materials and methods.
- **Required correction** Report the number of biological and technical replicates, the magnitude of the effect, and the statistical test used. Add a statistical analysis subsection to Materials and methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and methods, MD simulations
- **Evidence pointer** Materials and methods, "Folding pathways simulations"
- **Issue** The description of the MD simulations lacks essential technical details, including the specific force field, water model, salt concentration, simulation length, and temperature. The bias functional method is described but the implementation details are insufficient for reproduction.
- **Required correction** Provide complete simulation parameters, software versions, and analysis details. If the methods have been published previously, cite the original description and specify any modifications.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretive clarity
- **Affected element** Discussion, evolutionary interpretation
- **Evidence pointer** Discussion, paragraph on HReps
- **Issue** The discussion of HReps in relation to environmental adaptation is speculative and not directly supported by the data presented. The connection between HReps in AR and adaptation to environmental stressors is presented as a hypothesis but is not clearly framed as such.
- **Required correction** Clearly label this section as speculative and distinguish between conclusions supported by the data and hypotheses for future investigation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Data availability section
- **Issue** The data availability statement is minimal and does not specify where the sequence alignments, structural models, or MD simulation trajectories can be accessed.
- **Required correction** Provide specific accession numbers or repository links for the sequence data, structural models, and simulation data, or state clearly that these are available upon request.

## Risk / unsupported claims
- The claim that the LxxLL motif is "required for androgen binding" is not fully supported by the evidence presented in the text, as quantitative binding data are not provided.
- The claim that S792 phosphorylation occurs during folding and prevents maturation is based on MD simulations with limited sampling and no experimental validation of the folding intermediate.
- The claim that the S792 phospho-regulatory mechanism is an "ancient suppressive signal" conserved from fish to humans is not fully supported, as the functional data are derived from a heterologous human cell system and the differential effects between species are not explained.
- The claim that HReps in AR may contribute to environmental adaptation is speculative and not directly tested in this study.
- The structural conservation claims based on SWISS-Model and AlphaFold3 predictions lack quantitative metrics and are therefore not fully assessable from the text.