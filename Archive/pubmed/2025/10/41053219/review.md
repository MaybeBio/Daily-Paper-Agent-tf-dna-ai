## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors propose that the transcription factor AflR achieves sequence-diverse DNA recognition through a combination of a structured zinc cluster motif and conformationally plastic disordered terminal regions, which retain flexibility in the DNA-bound state and enable adaptation to sequence variations across target promoters.
- **Visible evidence base** NMR spectroscopy (HSQC, relaxation, NOE), CD spectroscopy, size exclusion chromatography, fluorescence correlation spectroscopy, isothermal titration calorimetry, EMSA with mutant and truncation constructs, native mass spectrometry, and extensive MD simulations (54 μs free protein, 12 μs per complex)
- **Missing materials affecting confidence** No atomic-resolution structure of any AflR-DBD/DNA complex is presented; NMR chemical shift assignments are mentioned but not deposited or shown; MD simulation validation is limited to chemical shift back-calculation without experimental structures for comparison; no in vivo functional validation of the proposed model is provided

## Reviewer

- **Overall assessment** This manuscript addresses a significant question in transcription factor biology: how a single TF can recognize diverse DNA sequences while maintaining specificity. The authors combine a wide range of biophysical and biochemical techniques to characterize AflR-DBD, revealing an interesting mechanism involving a structured zinc cluster core flanked by dynamic termini. The work is potentially important for understanding multi-target gene regulation, particularly in the context of aflatoxin biosynthesis. However, several concerns limit the strength of the conclusions as currently presented. The central claim that disordered regions "enable" sequence-diverse recognition is supported largely by correlative evidence and computational modeling rather than direct experimental demonstration. The absence of a high-resolution structure of any protein-DNA complex, the lack of deposited NMR data, and the reliance on steered MD for complex generation weaken the atomic-level claims. The functional data, while suggestive, do not fully establish the mechanistic model proposed.

- **Who would be interested in the results, and why** Researchers studying transcription factor-DNA recognition mechanisms, particularly those interested in the role of intrinsically disordered regions in DNA binding specificity and plasticity. The work also has relevance for the fungal secondary metabolism community, given AflR's central role in regulating aflatoxin biosynthesis genes. Additionally, those developing approaches to target transcription factors in pathogenic fungi may find the identification of functionally important terminal regions of interest.

- **Major strengths**
  1. The combination of multiple complementary biophysical techniques (NMR, CD, SEC, FCS, ITC, native MS) provides a comprehensive characterization of the free protein's conformational properties.
  2. The systematic truncation and mutagenesis approach effectively maps functionally important regions of AflR-DBD.
  3. The integration of MD simulations with experimental data, including validation via chemical shift back-calculation, represents a thoughtful approach to studying a challenging partially disordered system.
  4. The identification of promoter-specific dynamic changes in the bound state is an interesting observation that could have broad implications for understanding TF binding plasticity.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for central claim
- **Claim pointer** The abstract states that "conformational plasticity of disordered regions enables sequence-diverse DNA recognition" and the discussion claims that "dynamic termini optimize binding through distributed interactions."
- **Evidence pointer** Figures 3, 4; Supplementary Figures 22, 23; location not provided for specific residue-level data
- **Concern** The central mechanistic claim that disordered terminal regions "enable" sequence-diverse recognition is not directly demonstrated. The evidence presented is largely correlative: MD simulations show terminal flexibility, NMR shows reduced order parameters in termini, and mutations in these regions reduce binding. However, no experiment directly shows that conformational plasticity per se, rather than specific side-chain contacts, is what enables recognition of diverse sequences. The mutational analysis (Fig. 4c) shows that specific residues (R63, G65, R66) are important, but this could reflect specific contacts rather than conformational plasticity. The authors do not test whether increasing or decreasing terminal flexibility (e.g., through rigidifying mutations or linker modifications) correspondingly alters the range of sequences recognized.
- **Why it matters** The title and abstract make a strong mechanistic claim that goes beyond the data. If the claim is that plasticity enables diversity, the authors need to show a causal relationship, not just correlation. Without such evidence, the conclusion is overstated and the conceptual advance over existing models is diminished.
- **Resolution test** Provide direct experimental manipulation of terminal region flexibility (e.g., proline mutations to rigidify, glycine mutations to increase flexibility) and show corresponding changes in the range of DNA sequences bound. Alternatively, demonstrate that the same terminal residues make different contacts with different DNA sequences in a way that requires conformational adaptation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural evidence
- **Claim pointer** The manuscript claims to provide "atomic-level details of AflR-DBD's interactions with target DNA sequences" through MD simulations, and Figure 3 presents "structural ensembles" of the complexes.
- **Evidence pointer** Figure 3; Supplementary Figures 15-17; Methods section on MD simulations
- **Concern** No experimental structure of any AflR-DBD/DNA complex is presented. The complex models are generated through a multi-step computational pipeline involving steered MD to force the protein into a binding-competent conformation, followed by alignment to a Ppr1-DNA template. This approach is highly indirect and may introduce significant bias. The authors acknowledge initial docking failures due to steric clashes but do not adequately address how this computational pipeline might bias the resulting "structural ensembles." The validation is limited to chemical shift back-calculation for the free protein, not the complexes. Without experimental validation (e.g., intermolecular NOEs, paramagnetic relaxation enhancement, or cross-linking data), the atomic-level claims about the bound state are not established.
- **Why it matters** The structural models underpin the central claims about how terminal regions adapt to different DNA sequences. If the models are unreliable, the mechanistic conclusions drawn from them are correspondingly uncertain. The field of IDP/IDR biology is particularly sensitive to over-interpretation of computational models.
- **Resolution test** Provide experimental validation of the complex models, such as intermolecular NOE-derived distance restraints, HADDOCK or similar docking with experimental restraints, or hydrogen/deuterium exchange data. At minimum, deposit the chemical shift assignments and provide a more rigorous validation of the computational pipeline.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance and in vivo relevance
- **Claim pointer** The discussion states that "understanding this mechanism suggests strategies for targeting transcription factor function in pathogenic fungi" and implies the mechanism is relevant to AflR's regulatory role in aflatoxin biosynthesis.
- **Evidence pointer** Discussion section; no in vivo experiments presented
- **Concern** All functional experiments are performed in vitro with purified components. No experiments demonstrate that the identified residues or the proposed mechanism are important for AflR function in vivo, such as regulation of aflatoxin biosynthesis genes in Aspergillus. The claim about therapeutic targeting is speculative without any cellular or organismal validation. Additionally, the physiological relevance of the binding affinities (μM range) is not discussed in the context of nuclear concentrations of AflR.
- **Why it matters** For a study with potential agricultural and clinical implications, the absence of any in vivo validation significantly weakens the translational claims. Moreover, without demonstrating that the proposed mechanism operates in the native context, the broader significance of the work for understanding multi-target gene regulation remains uncertain.
- **Resolution test** Perform in vivo experiments in Aspergillus species, such as complementation of aflR deletion with mutants defective in terminal region function, or ChIP-seq comparing binding site occupancy of wild-type vs. mutant AflR. At minimum, discuss the physiological relevance of measured binding affinities.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative analysis and data availability
- **Claim pointer** The manuscript reports KD values from FCS and ITC experiments and KD-app values from EMSA titrations, and claims "comparable dissociation constants across promoters."
- **Evidence pointer** Figure 1e; Supplementary Figures 4, 12, 13; Supplementary Table 3
- **Concern** The quantitative binding data are presented with limited statistical analysis. The KD values from FCS show large errors (e.g., 408.8 ± 137.1 nM), and the EMSA-derived KD-app values in Supplementary Table 3 are reported with units of μM², which is unusual for a dissociation constant and suggests the fitting model may not be appropriate. The claim of "comparable" binding across promoters is not supported by statistical comparison. Additionally, the relationship between the different binding measurements (FCS, ITC, EMSA) is not reconciled; they appear to give different absolute values.
- **Why it matters** Quantitative binding parameters are central to the claim that AflR recognizes diverse sequences with similar affinity. If the measurements are not robust or the analysis is flawed, this aspect of the argument is weakened. The unusual units for KD-app raise questions about the fitting procedure.
- **Resolution test** Provide a rigorous statistical comparison of binding affinities across promoters and methods. Clarify the fitting model used for EMSA data and explain the units. Reconcile discrepancies between methods or discuss why they differ.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data availability
- **Affected element** NMR chemical shift assignments
- **Evidence pointer** Methods section on NMR spectroscopy
- **Issue** The manuscript mentions that assignments were made using ARTINA followed by manual verification, but no deposition statement for chemical shifts or restraints is provided.
- **Required correction** Deposit chemical shift assignments in BMRB and provide accession numbers. Also deposit MD trajectories or at least the analysis scripts for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Figure 2b
- **Evidence pointer** Figure 2b
- **Issue** The figure combines multiple types of information (gene cluster organization, sequence logo, EMSA gels) in a single panel, making it difficult to interpret. The sequence logo is small and the EMSA gels are not clearly labeled with all conditions.
- **Required correction** Split into separate panels with clear labels. Provide a larger, more readable sequence logo and clearly indicate all experimental conditions for each EMSA lane.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Disordered regions" designation
- **Evidence pointer** Throughout manuscript
- **Issue** The manuscript refers to "disordered regions" based on prediction and CD/NMR data, but the degree of disorder is not quantitatively characterized (e.g., no Cα secondary shift analysis for the terminal regions is shown, no relaxation-derived order parameters S² are presented).
- **Required correction** Provide quantitative measures of disorder (e.g., predicted disorder scores, Cα secondary shifts for terminal residues, or S² values) to support the designation of these regions as disordered.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Figure 4c binding curves
- **Evidence pointer** Figure 4c; Supplementary Table 3
- **Issue** The EMSA titration curves appear to lack error bars and the number of independent replicates is not clearly stated for each mutant.
- **Required correction** Add error bars to all titration curves and clearly state the number of replicates for each experiment in the figure legend.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion section
- **Issue** The "Dynamic-Anchor" model is presented without discussing alternative interpretations or models that could explain the data, such as conformational selection versus induced fit, or the possibility that the terminal regions act through non-specific electrostatic interactions rather than specific adaptive contacts.
- **Required correction** Add a paragraph discussing alternative models and why the presented data favor the proposed mechanism over these alternatives.

## Risk / unsupported claims
- The claim that disordered terminal regions "enable" sequence-diverse recognition is not directly established; evidence is correlative rather than causal.
- The atomic-level structural models of AflR-DBD/DNA complexes are computationally derived without experimental validation and should be treated as speculative.
- The therapeutic implications discussed in the final section are speculative and not supported by any experimental data in the manuscript.
- The statement that AflR "lacks the predicted helical secondary structure for dimerization" (Introduction) is used to argue for a distinct mechanism, but this is based on prediction only and not experimentally verified.
- The claim of "comparable" binding affinities across promoters is not statistically validated.
- The biological significance of the measured binding affinities (μM range) in the context of intracellular AflR concentrations is not discussed.