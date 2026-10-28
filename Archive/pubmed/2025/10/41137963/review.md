## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report the first description of CTNNB1 syndrome in the Tunisian population, based on two unrelated pediatric patients presenting with spastic paraplegia, intellectual disability, and visual defects. Whole exome sequencing identified a de novo nonsense variant (c.999 C>A; p.Tyr333X) and a novel de novo frameshift variant (c.1041-1044 del; p.Val349Alafs*9) in CTNNB1. In silico pathogenicity prediction and molecular docking/molecular dynamics simulations were used to characterize the impact of the frameshift variant on beta-catenin structure and function.
- **Visible evidence base** Abstract text only; no clinical data tables, sequencing metrics, variant validation details, or simulation parameters are provided
- **Missing materials affecting confidence** Full clinical phenotyping details, segregation data, variant calling and filtering criteria, ACMG classification evidence, structural coordinates, simulation protocols, convergence metrics, and any validation experiments

## Reviewer
- **Overall assessment** The abstract describes a clinically relevant case series with a plausible genetic basis, and the use of computational approaches to explore variant effects is commendable. However, the evidence presented is insufficient to fully establish the pathogenicity of the reported variants or the robustness of the simulation-based conclusions. The novelty claim for the Tunisian population is reasonable but requires confirmation that no prior Tunisian cases exist in the literature. The abstract lacks key methodological details that would allow assessment of the rigor of the genetic and computational analyses.
- **Who would be interested in the results, and why** Clinicians and geneticists working on neurodevelopmental disorders and rare disease diagnostics, particularly those focused on CTNNB1-related phenotypes and population-specific variant spectra. Computational biologists interested in applying molecular dynamics to interpret missense and frameshift variants may also find the approach relevant, though the novelty of the methodology itself is limited.
- **Major strengths** The study addresses an underreported population, which is valuable for expanding the ethnic and geographic representation of CTNNB1 syndrome. The identification of a novel frameshift variant adds to the mutational spectrum. The combination of clinical phenotyping with computational structural analysis is a useful approach for variant interpretation when functional assays are not available.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient evidence to confirm that the variants are the causative basis of the phenotype. Specifically, the lack of ACMG criteria, segregation data beyond "de novo" status, and functional validation means the pathogenicity claim is not fully established. The molecular dynamics results are described qualitatively without quantitative metrics, making the conclusions difficult to evaluate.
- **Assessment against Nature-style criteria** Originality: moderate, as the population-specific novelty is incremental and the computational approach is not new. Scientific importance: limited to a narrow clinical and genetic audience, with no broad conceptual advance. Interdisciplinary readership: the abstract may attract both clinicians and computational biologists, but the depth in each area is insufficient for a high-impact general journal. Technical soundness: not assessable from the abstract alone, but the lack of methodological detail raises concerns. Readability for nonspecialists: the abstract is generally clear, though some terms such as "ARM domains" and "nonsense-mediated decay" are used without explanation.
- **Recommendation posture** Currently not established from the provided evidence. The clinical and genetic findings are potentially valuable, but the abstract does not provide enough detail to support the pathogenicity claims or the simulation-based conclusions. A revised manuscript with full methodological transparency and quantitative results could change this assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Genetic evidence sufficiency
- **Claim pointer** The abstract states that the identified variants "were predicted to be pathogenic using in silico investigations" and implies they are causative of CTNNB1 syndrome.
- **Evidence pointer** Methods and Results section, abstract
- **Concern** The abstract does not provide ACMG/AMP classification criteria, population frequency data, or any functional validation for either variant. The claim of pathogenicity rests solely on in silico prediction and the de novo status, which is insufficient for a definitive diagnosis of a rare genetic syndrome.
- **Why it matters** Without robust genetic evidence, the clinical diagnosis of CTNNB1 syndrome cannot be confirmed, and the novelty claim for the Tunisian population is weakened. Overinterpretation of in silico predictions is a common pitfall in rare disease reports.
- **Resolution test** Provide ACMG criteria with evidence codes, population allele frequencies, and any additional segregation or functional data. If functional assays are not available, clearly state this limitation and temper the pathogenicity claim accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational analysis rigor
- **Claim pointer** The abstract claims that molecular dynamics simulations "uncovered the disruption of beta-catenin function and the loss of its interacting counterparts" and provide "a comprehensive understanding of the conformational changes, compactness, folding and stability of the mutated beta-catenin protein."
- **Evidence pointer** Methods and Results section, abstract
- **Concern** No simulation parameters, force fields, simulation times, convergence criteria, or quantitative results (e.g., RMSD, RMSF, binding free energies) are reported. The qualitative language ("disruption", "loss", "comprehensive understanding") is not supported by any numerical evidence in the abstract.
- **Why it matters** Molecular dynamics results are only meaningful when reproducibility and statistical rigor are demonstrated. Without these details, the conclusions from the simulations cannot be evaluated or reproduced, undermining the scientific value of the computational component.
- **Resolution test** Include a summary of simulation setup, validation of system stability, and key quantitative metrics comparing wildtype and mutant. Provide access to full methods in the manuscript or supplementary materials.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Clinical phenotype completeness
- **Claim pointer** The abstract states that both patients have "spastic paraplegia, intellectual disability and visual defect" and that this constitutes CTNNB1 syndrome.
- **Evidence pointer** Methods and Results section, abstract
- **Concern** The clinical features are described in a single sentence without detail on severity, age of onset, neurological examination findings, or ophthalmological assessments. It is unclear whether the phenotype is consistent with the known CTNNB1 syndrome spectrum or whether other differential diagnoses were excluded.
- **Why it matters** Accurate genotype-phenotype correlation is essential for validating a new population-specific description. Incomplete phenotyping may lead to misattribution of the syndrome.
- **Resolution test** Provide a detailed clinical table for each patient, including developmental milestones, neurological exam, ophthalmology reports, and any additional systemic features. Clarify how other causes of spastic paraplegia were excluded.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology clarity
- **Affected element** "nonsense-mediated decay" and "ARM domains"
- **Evidence pointer** Methods and Results section, abstract
- **Issue** These terms are used without definition, which may reduce readability for nonspecialist readers.
- **Required correction** Briefly define or contextualize these terms, or rephrase to make the sentence accessible to a broader audience.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Novelty claim substantiation
- **Affected element** "first description of CTNNB1 syndrome in the Tunisian population"
- **Evidence pointer** Background and Conclusions sections, abstract
- **Issue** The abstract does not cite or discuss prior literature on CTNNB1 syndrome in North African or Arab populations, so the novelty claim cannot be verified.
- **Required correction** Add a brief literature search statement or citation to confirm that no prior Tunisian cases have been reported.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Variant nomenclature consistency
- **Affected element** "c.1041-1044 del; p.Val349Alafs*9"
- **Evidence pointer** Methods and Results section, abstract
- **Issue** The notation "c.1041-1044 del" is ambiguous as it does not specify the exact deleted nucleotides. Standard HGVS nomenclature should be used.
- **Required correction** Revise to a full HGVS format, e.g., c.1041_1044del, and confirm the predicted protein change accordingly.

## Risk / unsupported claims
- The claim that the frameshift variant "would probably escape nonsense-mediated decay" is speculative and not supported by experimental evidence in the abstract.
- The statement that the simulations "uncovered the disruption of beta-catenin function" is unsupported without quantitative data.
- The assertion of "first description in the Tunisian population" is unverifiable without a literature search statement.
- The overall pathogenicity of both variants is not established from the provided evidence, as no ACMG classification or functional validation is reported.