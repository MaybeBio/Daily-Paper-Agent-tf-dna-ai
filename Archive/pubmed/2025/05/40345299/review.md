## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that BRCA1 preferentially binds an open-planar conformation of the Holliday junction (HJ) over a stacked conformation, with approximately 10-fold lower affinity for the stacked form. This preference is stated to be independent of the nucleotide sequence at the branch point. Molecular docking and all-atom molecular dynamics simulations implicate charged and polar residues in the exon 11 DNA binding region of BRCA1 in the interaction, and many of these residues are sites of missense mutations. Computational mutation studies are reported to disrupt the interaction.
- **Visible evidence base** Abstract text only; no experimental data, figures, tables, or methodological details are provided
- **Missing materials affecting confidence** Full manuscript, experimental methods for fluorescence correlation spectroscopy (FCS), docking and simulation parameters, statistical analyses, structural coordinates, mutation selection criteria, and any validation or control experiments

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting biophysical finding regarding BRCA1 conformational selectivity for Holliday junctions, with implications for understanding mutation-associated dysfunction in DNA repair. However, the evidence base is limited to a summary, and several claims cannot be evaluated without access to the underlying data and methodological details. The computational component, in particular, requires careful scrutiny regarding force field choices, sampling adequacy, and the biological relevance of the simulated conformations. The claim of sequence independence and the functional interpretation of missense mutations are not sufficiently supported from the abstract alone.
- **Who would be interested in the results, and why** Researchers in DNA repair mechanisms, particularly homologous recombination and BRCA1 biology, would find these results relevant. Structural biologists and computational biophysicists studying protein-DNA interactions and conformational dynamics may also be interested. Clinically oriented investigators studying BRCA1 missense variants of uncertain significance could find the mutation-focused computational predictions useful as a hypothesis-generating resource.
- **Major strengths** The study addresses a specific and unresolved question regarding BRCA1 conformational preference for HJ isomers. The combination of single-molecule spectroscopy with computational approaches is appropriate for interrogating both binding affinity and molecular determinants. The focus on missense mutation hotspots provides a potential translational link to disease-associated variants.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is moderate; the question of HJ conformational preference has been explored for other proteins, and the novelty here lies in the specific application to BRCA1. Scientific importance is potentially high given BRCA1's clinical relevance, but the abstract does not establish a mechanistic advance beyond a binding preference. Interdisciplinary readership is plausible, spanning biophysics, structural biology, and cancer biology, but the abstract lacks sufficient context for nonspecialists to appreciate the significance of open-planar versus stacked HJ conformations. Technical soundness cannot be assessed from the abstract alone, particularly for the computational methods. Readability for nonspecialists is adequate but would benefit from a brief explanation of HJ conformations and their biological relevance.
- **Recommendation posture** Currently not established from the provided evidence. The core claims require full experimental and computational details for evaluation. Supportive if technical concerns are resolved upon full manuscript review.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Experimental evidence  
- **Claim pointer** The authors claim that BRCA1 prefers an open-planar conformation of HJ and has a 10-fold lesser affinity for stacked HJ, and that this preference is independent of the nucleotide sequence at the branch point.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract reports single-molecule FCS data but provides no information on how the open-planar and stacked HJ conformations were prepared, stabilized, or verified. No experimental details are given regarding the number of replicates, error estimates, or statistical significance of the 10-fold affinity difference. The claim of sequence independence is stated without any indication of how many sequences were tested or how the branch point sequence was varied.  
- **Why it matters** The central conclusion of conformational preference rests entirely on the FCS measurements. Without evidence that the HJ conformations were properly controlled and that the affinity difference is statistically robust, the primary claim is unsupported. Sequence independence is a strong claim that requires demonstration across a meaningful sequence space.  
- **Resolution test** Provide full FCS methods including HJ construct design, conformational verification (e.g., by gel electrophoresis or FRET), titration protocols, fitting models, replicate numbers, and statistical analysis. Show data for at least two or three distinct branch point sequences with error bars and significance testing.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Computational methodology  
- **Claim pointer** The authors claim that molecular docking and all-atom molecular dynamics simulations revealed that primarily charged and polar residues in the DNA binding region from exon 11 of BRCA1 participated in the interaction.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** No details are provided on the docking protocol, the starting structures used for BRCA1 and HJ, the force field parameters, simulation length, equilibration procedures, or convergence criteria. The abstract does not specify how "participation" in the interaction was defined, whether by contact frequency, binding free energy decomposition, or other metrics. Without these details, the reliability of the computational predictions cannot be assessed.  
- **Why it matters** Molecular dynamics results are highly sensitive to simulation setup and sampling. If the simulations were too short or poorly converged, the identified residue contacts may be artifacts. The claim that specific residues participate in the interaction is a key mechanistic finding that must be robust to methodological choices.  
- **Resolution test** Provide complete computational methods including software versions, force fields, water models, salt concentrations, simulation times, and convergence analyses. Show contact maps or interaction energy decompositions with error estimates. Ideally, include independent validation such as mutational free energy calculations or comparison with experimental binding data.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mutation analysis  
- **Claim pointer** The authors claim that mutating these residues disrupted the interaction, based on further computational studies.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract states that mutating the identified residues disrupted the interaction but provides no information on which mutations were modeled, how the mutations were introduced, or what metric was used to define disruption. It is unclear whether the mutations correspond to known disease-associated variants or were arbitrary substitutions. The phrase "further computational studies" is vague and does not specify the method, such as alchemical free energy calculations, MM-PBSA, or simple contact analysis.  
- **Why it matters** The link between specific BRCA1 missense mutations and impaired HJ binding is a potentially clinically relevant finding. However, without details on the mutation selection and the computational approach, the claim cannot be evaluated. Overinterpretation of computational mutation effects without experimental validation is a common pitfall.  
- **Resolution test** Specify the exact mutations modeled, their correspondence to known BRCA1 variants, the computational method used, and the criteria for defining disruption. Provide quantitative results such as changes in binding free energy or contact persistence. Ideally, include experimental validation, such as binding assays with mutant proteins.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Biological interpretation  
- **Claim pointer** The abstract implies that the identified residues, which are sites of missense changes, may explain why specific mutations in BRCA1 lead to impaired DNA repair.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not establish a direct causal link between the computational binding disruption and the observed impairment of DNA repair in BRCA1-mutant cells. The connection is inferred but not demonstrated. No data are presented to show that the mutations studied computationally actually affect HJ binding in cells or in vitro, nor that this binding defect is responsible for the repair phenotype.  
- **Why it matters** The clinical and biological significance of the findings depends on this link. Without experimental evidence connecting the computational predictions to functional outcomes, the broader implications remain speculative.  
- **Resolution test** Provide experimental data, such as in vitro binding assays with purified mutant proteins or cellular assays measuring HR efficiency in cells expressing the mutants, to support the functional relevance of the identified residues.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract background  
- **Evidence pointer** Abstract text  
- **Issue** The abstract states that BRCA1 recruits several proteins to the DNA damage site but does not specify which proteins or how HJ binding relates to this recruitment. This context is relevant for understanding the functional significance of the conformational preference.  
- **Required correction** Briefly mention one or two known interaction partners recruited by BRCA1 to HJ and clarify how the conformational preference might affect this recruitment.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Abstract methods description  
- **Evidence pointer** Abstract text  
- **Issue** The term "single-molecule Fluorescence Correlation Spectroscopy" is used, but FCS is typically not considered a single-molecule technique in the strict sense, as it measures fluctuations from ensembles of molecules in a confocal volume. This may be a misnomer or require clarification.  
- **Required correction** Clarify whether the measurements were truly single-molecule, such as using single-molecule FRET or fluorescence burst analysis, or revise the terminology to "Fluorescence Correlation Spectroscopy" if appropriate.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract conclusions  
- **Evidence pointer** Abstract text  
- **Issue** The abstract does not state the number of missense mutations identified among the interacting residues or whether these correspond to known pathogenic variants. This information would strengthen the translational relevance.  
- **Required correction** Include the count of mutation sites and, if available, their classification as pathogenic or variants of uncertain significance in the abstract.

## Risk / unsupported claims
- The claim of a 10-fold affinity difference between open-planar and stacked HJ is unsupported without experimental details and statistical analysis.
- The claim of sequence independence of the conformational preference is unsupported without data from multiple branch point sequences.
- The identification of specific residues participating in the interaction is unsupported without computational methods and convergence evidence.
- The claim that mutating these residues disrupts the interaction is unsupported without details on the mutation modeling and the disruption criteria.
- The implied link between computational binding disruption and impaired DNA repair in BRCA1-mutant cells is unsupported and speculative from the abstract alone.