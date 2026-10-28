## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and conclusions as presented in the manuscript
- **Shared manuscript claim summary** The authors identify homeobox transcription factors in the dimorphic fungus Talaromyces marneffei, analyze their expression across morphological states, and use computational approaches (AlphaFold3, molecular dynamics, MM-GBSA) to predict that conserved IR residues (Asp276, Glu279, Gln282) in the RfeB protein stabilize protein structure and enable interaction with putative partner TmSwi5.
- **Visible evidence base** Abstract, full Methods, Results, Discussion, Conclusions, figure legends referenced in text, tables referenced in text
- **Missing materials affecting confidence** Figures and tables themselves were not provided; Supplemental Data S1 and S2 not accessible; raw qPCR data not shown; AlphaFold3 output files (pLDDT plots) referenced but not visible; statistical details for binding free energy calculations incomplete

## Reviewer
- **Overall assessment** This manuscript presents a genome-wide identification of homeobox transcription factors in T. marneffei and combines expression analysis with computational structural biology to investigate the RfeB protein. The work addresses an understudied area, as homeobox proteins in this pathogen have received limited attention. The expression data provide a useful descriptive resource. However, the central computational claim regarding IR residue function relies on a single in silico mutagenesis approach without experimental validation, and several methodological details and validations are insufficiently described. The manuscript is technically sound in parts but the core conclusion is not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers studying fungal development and dimorphism, particularly in pathogenic fungi; investigators interested in homeobox transcription factor evolution and function; computational biologists working on protein-protein interaction prediction; those interested in antifungal drug target discovery.
- **Major strengths** 1) First genome-wide identification of homeobox transcription factors in T. marneffei, filling a knowledge gap. 2) Expression profiling across morphological states provides a useful resource for the community. 3) The computational pipeline combining AlphaFold3, MD simulations, and MM-GBSA is modern and appropriate for hypothesis generation. 4) The study extends knowledge of Pho2-family IR residues beyond yeast species into a dimorphic pathogen.
- **Major Concerns** 1) The central conclusion that IR residues stabilize RfeB structure and enable interaction is based solely on computational prediction without experimental validation. 2) The choice of TmSwi5 as the interaction partner lacks experimental support. 3) The use of Engrailed DNA sequences rather than T. marneffei-specific promoter sequences weakens biological relevance. 4) The phylogenetic analysis and expression data are presented descriptively without functional validation. 5) Several methodological details for the MD simulations and MM-GBSA calculations are incomplete.
- **Minor Comments** 1) The manuscript would benefit from clearer presentation of the phylogenetic tree results. 2) The relationship between the seven selected TmHox genes and the total ten identified homeobox proteins should be clarified. 3) The discussion of therapeutic applications is speculative and could be tempered. 4) Some statements in the Introduction about transcription factor druggability are overly general.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of experimental validation for the central claim), R1-M2 (insufficient justification for partner selection), R1-M3 (use of heterologous DNA sequences), R1-M4 (incomplete methodological reporting for simulations)
- **Assessment against Nature-style criteria** Originality: Moderate. The identification of homeobox TFs in T. marneffei is novel but the approach is largely descriptive. Scientific importance: Moderate. The work provides a resource and a testable hypothesis, but the central claim is not experimentally validated. Interdisciplinary readership: Limited. The work bridges genomics and computational biology but may not attract broad readership beyond fungal biology and computational structural biology communities. Technical soundness: Partially sound. The computational methods are appropriate but incompletely described and lack experimental grounding. Readability for nonspecialists: Acceptable. The manuscript is generally clear, though some computational details may be challenging for non-specialists.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the need for experimental validation or clear framing of the work as hypothesis-generating rather than definitive.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that mutations at conserved IR residues (Asp276, Glu279, Gln282) destabilize the RfeB-TmSwi5 complex and disrupt protein-protein interaction, concluding these residues are important for RfeB function.
- **Evidence pointer** Section 3.6, Section 3.7, Table 6, Figure 9, Figure 10
- **Concern** The central conclusion that IR residues are functionally important for RfeB-TmSwi5 interaction is based entirely on in silico mutagenesis and MD simulations. No experimental validation (e.g., yeast two-hybrid, co-immunoprecipitation, or in vitro binding assays) is provided. The authors acknowledge this limitation in the Discussion but still present the conclusion as a finding rather than a hypothesis.
- **Why it matters** Computational predictions, while valuable for hypothesis generation, cannot establish biological function. The claim that these residues "play an important role in the binding between RfeB and TmSwi5" (Section 3.6) is presented as a definitive result. Without experimental confirmation, the central message of the paper is overstated.
- **Resolution test** Provide experimental validation of the RfeB-TmSwi5 interaction and the effect of IR mutations, or reframe the manuscript explicitly as a computational prediction study with the central claim presented as a testable hypothesis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The authors selected TmSwi5 as the putative interaction partner of RfeB based on homology with ScSwi5 from S. cerevisiae and the known Pho2-Swi5 interaction.
- **Evidence pointer** Section 3.4, Section 3.5, Section 4
- **Concern** The choice of TmSwi5 as the interaction partner is based solely on sequence homology with S. cerevisiae ScSwi5. No experimental evidence for a physical interaction between RfeB and TmSwi5 in T. marneffei is provided. The authors note that the HO gene (the target of Swi5 in S. cerevisiae) has no homolog in T. marneffei, which raises questions about whether the RfeB-TmSwi5 interaction is biologically relevant in this organism.
- **Why it matters** The entire structural analysis and the conclusions drawn from it depend on the assumption that RfeB and TmSwi5 interact in vivo. If this interaction does not occur in T. marneffei, the computational results have limited biological meaning.
- **Resolution test** Provide experimental evidence for the RfeB-TmSwi5 interaction (e.g., co-IP, Y2H, or pull-down assays), or clearly state that the interaction is hypothetical and the structural analysis is exploratory.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance
- **Claim pointer** The authors used DNA sequences from the Engrailed protein-DNA co-crystal structure to model the RfeB-TmSwi5-DNA complex, as the native RfeB target DNA sequences are unknown.
- **Evidence pointer** Section 2.6, Section 3.5
- **Concern** The use of Engrailed DNA sequences, rather than T. marneffei-specific promoter sequences, limits the biological relevance of the modeled complex. The authors justify this choice by citing prior use of Engrailed sequences for Pho2 modeling, but this does not establish that the RfeB-TmSwi5-DNA complex in T. marneffei resembles the modeled structure.
- **Why it matters** The DNA component of the complex may influence protein-protein interactions and complex stability. Using heterologous DNA sequences could lead to incorrect conclusions about the native complex.
- **Resolution test** Identify putative RfeB binding sites in the T. marneffei genome (e.g., via ChIP-seq or in silico motif prediction) and repeat the modeling with native DNA sequences, or acknowledge this limitation more prominently and temper conclusions accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor
- **Claim pointer** The authors performed 500 ns MD simulations and MM-GBSA calculations to compare wild-type and mutant RfeB-TmSwi5 complexes.
- **Evidence pointer** Section 2.7, Section 3.6, Section 3.7, Table 6
- **Concern** Several methodological details are missing: the number of independent MD replicates, convergence criteria, equilibration protocols, and error estimates for the MM-GBSA calculations are not fully described. The MM-GBSA results are presented as mean ± SD, but the number of samples used for the statistics is unclear. Additionally, the authors do not report whether the simulations were repeated to ensure reproducibility.
- **Why it matters** MD simulations and binding free energy calculations are sensitive to simulation setup and sampling. Without adequate methodological detail and replicate simulations, the reliability of the quantitative results cannot be assessed.
- **Resolution test** Provide complete simulation parameters, number of replicates, convergence analysis, and statistical details for the MM-GBSA calculations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.1
- **Evidence pointer** Figure 1
- **Issue** The manuscript states that homeodomain-containing proteins comprised the second-largest family of transcription factors in T. marneffei, but the total number of transcription factors (713) and the number of homeobox proteins (119) seem inconsistent with the later statement that only ten homeobox proteins contain the homeodomain.
- **Required correction** Clarify the relationship between the 119 proteins identified by InterPro terms and the ten proteins selected for further analysis. Explain the filtering criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Section 3.3
- **Evidence pointer** Figure 4, Figure 5
- **Issue** The expression data are presented as relative expression values, but the statistical analysis is limited to Student's t-test without correction for multiple comparisons. Given that seven genes were tested across multiple conditions, the false discovery rate may be inflated.
- **Required correction** Apply multiple testing correction (e.g., Benjamini-Hochberg) or acknowledge this limitation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 4
- **Evidence pointer** Not applicable
- **Issue** The Discussion speculates about therapeutic applications of targeting the IR region for antifungal drug development. While this is an interesting perspective, it is highly speculative given the lack of experimental validation.
- **Required correction** Soften the therapeutic claims and clearly frame them as long-term possibilities contingent on experimental validation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.2
- **Evidence pointer** Table 3
- **Issue** The primers used for qPCR are listed in Table 3, but the table is not visible in the provided material. The authors should ensure that primer sequences and amplification efficiencies are reported.
- **Required correction** Confirm that Table 3 includes primer sequences, annealing temperatures, and amplification efficiencies.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section 3.5
- **Evidence pointer** Figure S3
- **Issue** The authors state that AlphaFold3 was unable to predict the full-length structure and that some residues were removed. The criteria for removing residues and the impact on the final model are not described.
- **Required correction** Describe the residue removal criteria and discuss how this may affect the interpretation of the modeled complex.

## Risk / unsupported claims
- The claim that IR residues Asp276, Glu279, and Gln282 are functionally important for RfeB-TmSwi5 interaction is unsupported by experimental evidence and should be framed as a computational prediction.
- The biological relevance of the RfeB-TmSwi5 interaction in T. marneffei is unsubstantiated, as no experimental evidence for this interaction is provided.
- The use of Engrailed DNA sequences for modeling the RfeB-TmSwi5-DNA complex may not reflect the native complex in T. marneffei, and conclusions drawn from this model should be tempered.
- The statement that "the IR residues primarily stabilized the RfeB binding sites located in the central region" (Abstract) is a computational inference that has not been experimentally verified.
- The therapeutic potential of targeting the IR region for antifungal drug development is speculative and not supported by the data presented.