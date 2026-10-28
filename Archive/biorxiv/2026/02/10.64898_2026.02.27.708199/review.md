## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report proteome-scale coarse-grained simulations of 14,283 human proteins with IDRs, comparing conformational properties of 8,988 long IDRs (≥100 residues) in isolated versus full-length contexts. They claim that over 30% of these IDRs undergo significant conformational shifts when embedded in full-length architectures, that central IDRs are evolutionarily biased toward compact and rigid conformations, that charge-clustered IDRs prefer extended and flexible states, and that compact-rigid versus extended-flexible IDRs are functionally enriched in DNA-binding versus RNA-binding proteins, respectively. They conclude that long IDRs co-evolve with structured domains as integrated architectural modules.
- **Visible evidence base** Abstract text only; no quantitative results, simulation details, statistical analyses, or functional enrichment data are visible
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, simulation parameters, validation of the coarse-grained model, statistical significance values, enrichment analysis details, and any control analyses

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting and large-scale computational study addressing an important question about the evolutionary and structural constraints imposed by full-length protein architecture on intrinsically disordered regions. However, the claims as stated are broad and far-reaching, and the visible evidence base is insufficient to evaluate their validity. The central findings, including the percentage of IDRs undergoing conformational shifts, the evolutionary bias claims, and the functional enrichment results, are presented without any quantitative detail, statistical support, or methodological context. The manuscript may have merit, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Researchers in protein biophysics, computational biology, and evolutionary genomics would be interested. The work addresses a fundamental question about whether IDRs evolve independently or as part of integrated protein architectures, which has implications for understanding protein structure-function relationships, disorder-based regulatory mechanisms, and the evolutionary dynamics of multidomain proteins. The proteome-scale scope and the proposed framework for domain-disorder co-evolution could attract broad attention in the structural biology and molecular evolution communities.
- **Major strengths** The question addressed is timely and important, as most studies of IDR conformational properties have focused on isolated peptides or domains. The proposed proteome-scale approach, integrating a coarse-grained force field with elastic network representations, is ambitious and potentially powerful. The abstract articulates a clear conceptual framework that distinguishes isolated versus full-length contexts, which is a meaningful advance in framing the problem.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4  
  - R1-M5
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria**  
  Originality: The conceptual framing of IDRs as co-evolving architectural modules rather than independent polymers is a potentially original contribution, though the abstract does not fully distinguish this from prior work on IDR evolution.  
  Scientific importance: The question of whether full-length architecture constrains IDR evolution is of high importance for understanding protein evolution and function.  
  Interdisciplinary readership: The topic bridges structural biology, computational biophysics, and evolutionary genomics, and could appeal to a broad readership if the evidence is compelling.  
  Technical soundness: Cannot be assessed from the abstract. The simulation methodology, force field validation, and statistical treatment are not described.  
  Readability for nonspecialists: The abstract is clearly written and accessible, with technical terms defined in context.
- **Recommendation posture** Currently not established from the provided evidence. The claims are potentially significant, but the abstract alone does not provide sufficient quantitative or methodological detail to support them. A full manuscript with detailed methods, validation, and statistical analyses would be required to assess whether the case can be made.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The claim that 2,733 IDRs (over 30%) undergo significant conformational shifts when embedded in their native protein architecture.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract states that over 30% of long IDRs undergo significant conformational shifts, but no definition of "significant" is provided. It is unclear what metric was used to quantify conformational change, what threshold was applied, and whether this threshold was pre-specified or derived post hoc.  
- **Why it matters** The central quantitative claim of the paper rests on this percentage. Without a clear and defensible definition of what constitutes a significant conformational shift, the headline result cannot be interpreted or reproduced.  
- **Resolution test** Provide the specific metric used to compare isolated versus full-length conformations, the threshold for significance, and justification for that threshold. Include a distribution of the conformational change metric across all IDRs to show that the 30% figure is robust and not an artifact of threshold selection.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The claim that the Calvados coarse-grained force field combined with an elastic network representation of structured domains can accurately model full-length protein architectures.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** No validation of the simulation approach is described. It is not clear whether the elastic network representation preserves the native dynamics of structured domains, whether the Calvados force field has been benchmarked for IDRs in the context of full-length proteins, or whether the simulation lengths are sufficient for convergence of conformational ensembles.  
- **Why it matters** The entire study depends on the reliability of the simulation methodology. If the coarse-grained model does not accurately capture the coupling between structured domains and IDRs, all downstream conclusions about conformational shifts and evolutionary constraints would be compromised.  
- **Resolution test** Provide validation against experimental data, such as small-angle X-ray scattering or Förster resonance energy transfer measurements for a subset of proteins. Demonstrate convergence of conformational ensembles and show that the elastic network representation does not introduce artifacts in IDR behavior.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The claim that IDRs positioned centrally within proteins are evolutionarily biased toward compact and rigid conformations, and that charge-clustered IDRs preferentially adopt extended and flexible states.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract reports evolutionary biases and conformational preferences without any statistical measures. No effect sizes, confidence intervals, or p-values are provided. It is unclear how "evolutionarily biased" was determined, what evolutionary metric was used, and whether confounding factors such as protein length, domain composition, or IDR sequence composition were controlled for.  
- **Why it matters** These claims form the core of the evolutionary conclusions. Without statistical support and appropriate controls, the observed associations could arise from confounding variables or be statistically weak.  
- **Resolution test** Provide statistical analyses with effect sizes and confidence intervals for the associations between IDR position, conformational properties, and evolutionary conservation. Describe the evolutionary metric used and demonstrate robustness to confounding factors through multivariate analysis or propensity score matching.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The claim that compact-rigid IDRs are overrepresented in DNA-binding proteins while extended-flexible IDRs are enriched in RNA-binding functions.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The functional enrichment analysis is mentioned but no details are given. It is unclear what functional annotation database was used, how enrichment was calculated, what the significance thresholds were, and whether multiple testing corrections were applied. The biological interpretation that compact-rigid IDRs are suited to DNA binding and extended-flexible IDRs to RNA binding is plausible but requires quantitative support.  
- **Why it matters** The functional specialization claim links the biophysical findings to biological function, which is a key part of the paper's significance. Without proper enrichment analysis details, this claim cannot be evaluated.  
- **Resolution test** Provide the full enrichment analysis with the database used, the statistical test, multiple testing correction, and the list of significant functional categories. Show that the DNA-binding and RNA-binding enrichments are robust and not driven by a small number of outlier proteins.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim scope  
- **Claim pointer** The claim that long IDRs do not evolve as independent polymeric segments but co-evolve with structured domains as integrated architectural modules.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** This is a strong evolutionary conclusion drawn from simulation-based conformational comparisons. The abstract does not present any direct evolutionary analysis, such as phylogenetic comparisons, sequence conservation across species, or co-evolution between IDR and domain sequences. The leap from conformational observations to evolutionary conclusions is not justified by the described evidence.  
- **Why it matters** The title and the concluding claim of the paper are evolutionary in nature, but the visible evidence is purely biophysical. Without direct evolutionary data, the central thesis of the paper is not supported.  
- **Resolution test** Include direct evolutionary analyses, such as comparative genomics across species, co-evolutionary sequence analysis between IDRs and adjacent domains, or phylogenetic tests of correlated evolution. Alternatively, temper the evolutionary claims to what the simulation data can directly support.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Definition of long IDRs  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The abstract states that 8,988 long IDRs of ≥100 residues were analyzed, but it is unclear whether this threshold was chosen based on prior literature or on the distribution of IDR lengths in the dataset.  
- **Required correction** Provide justification for the 100-residue threshold or state that it follows established conventions in the field.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Simulation scope  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The abstract mentions 14,283 human proteins but does not clarify how this set was selected, whether it represents the full human proteome, or whether any filtering criteria were applied.  
- **Required correction** Describe the selection criteria for the protein set and state whether it is a complete proteome or a filtered subset.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretability  
- **Affected element** Conformational descriptors  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The terms "compact," "rigid," "extended," and "flexible" are used to describe IDR conformations, but no operational definitions are provided. These terms could refer to radius of gyration, end-to-end distance, or other metrics.  
- **Required correction** Define the specific conformational descriptors used and how they map to the qualitative terms in the abstract.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Simulation parameters  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** No information is given about simulation length, temperature, salt concentration, or other key parameters that would affect the conformational ensembles.  
- **Required correction** Provide key simulation parameters in the methods or state that they follow standard protocols for the Calvados force field.

## Risk / unsupported claims
- The claim that over 30% of long IDRs undergo significant conformational shifts is unsupported without a definition of "significant" and the underlying distribution of conformational changes.
- The claim that central IDRs are evolutionarily biased toward compact and rigid conformations is unsupported without any evolutionary analysis or statistical measures.
- The claim that charge-clustered IDRs preferentially adopt extended and flexible states is unsupported without quantitative conformational data and statistical testing.
- The claim that compact-rigid IDRs are enriched in DNA-binding proteins and extended-flexible IDRs in RNA-binding proteins is unsupported without details of the enrichment analysis.
- The overarching conclusion that long IDRs co-evolve with structured domains as integrated architectural modules is not supported by the visible evidence, which is purely simulation-based and lacks direct evolutionary data.
- The accuracy and reliability of the simulation approach cannot be assessed without validation data or methodological details.