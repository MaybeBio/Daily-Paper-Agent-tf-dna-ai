## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, tables, methods, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce PIC-NIC, a high-throughput platform using site-specific DNA backbone nicks to perturb DNA mechanics without altering base identity. Across 15 transcription factors (TFs) from eight structural families, they report position-dependent effects of nicking on TF binding, with sensitive sites often coinciding with strain-adapted DNA geometries such as Hoogsteen conformations. They further propose that genomic single-strand breaks and repair maps suggest TF retention at nicked DNA may influence local repair-factor accessibility.
- **Visible evidence base** Abstract text only; no experimental data, statistical analyses, structural coordinates, simulation details, or genomic datasets are visible
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods section, supplementary information, statistical details, structural data, simulation parameters, and genomic analysis pipelines

## Reviewer
- **Overall assessment** The abstract presents a conceptually appealing and potentially significant advance in mapping DNA mechanical strain as a determinant of TF recognition. The platform concept is novel and the breadth across 15 TFs and eight structural families is commendable. However, the abstract alone provides insufficient evidence to evaluate the technical rigor, statistical robustness, or biological significance of the claims. Several assertions, particularly regarding Hoogsteen conformations and repair-factor accessibility, require substantially more evidence than is visible here. The work is promising but not yet established from the provided material.
- **Who would be interested in the results, and why** Researchers in transcription regulation, DNA repair, chromatin biology, and biophysics would find these results relevant. The work bridges DNA mechanics and protein-DNA recognition, which is of interest to structural biologists studying TF-DNA complexes, computational biologists modeling binding specificity, and investigators exploring how DNA damage and repair intersect with transcription factor occupancy.
- **Major strengths** The platform concept is innovative, addressing a genuinely under-explored layer of TF recognition. The breadth across 15 TFs and eight structural families suggests generalizability. The integration of multiple approaches, including structural comparisons, kinetics, and simulations, indicates a multi-pronged strategy. The potential link to repair-factor accessibility adds a biologically compelling dimension.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: High. The concept of systematically mapping DNA backbone mechanics as a position-resolved layer of TF recognition appears novel and distinct from prior base-preference mapping efforts.  
  - Scientific importance: Potentially high, if the claims hold. The work could reshape understanding of how DNA mechanics contribute to TF binding specificity and may have implications for DNA repair biology.  
  - Interdisciplinary readership: Broad. The topic spans transcription, DNA repair, structural biology, and biophysics, which would attract readers across these communities.  
  - Technical soundness: Not assessable from the abstract alone. The platform design, controls, statistical methods, and validation are not visible.  
  - Readability for nonspecialists: The abstract is well-written and accessible, with clear framing of the problem and the approach. Technical terms such as Hoogsteen conformations are used without definition, which may challenge some readers, but this is acceptable for a specialist journal.
- **Recommendation posture** Supportive if technical concerns are resolved. The concept is compelling and the scope is appropriate for a high-impact venue, but the current evidence base is insufficient to establish the core claims.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that PIC-NIC uses site-specific backbone nicks to perturb DNA mechanics while preserving base identity and minimizing accompanying chemical changes.  
- **Evidence pointer** Location not provided  
- **Concern** The abstract does not describe how the platform controls for unintended effects of nicking beyond mechanical perturbation, such as changes in DNA flexibility, base-pair opening dynamics, or potential chemical modifications at the nick site. The claim of minimizing chemical changes is not substantiated with any data.  
- **Why it matters** If nicking introduces confounding effects beyond mechanical strain, the interpretation that observed binding changes are due to mechanical perturbation would be compromised. This is the foundational premise of the entire study.  
- **Resolution test** Provide detailed characterization of the nicked DNA substrates, including structural validation, demonstration that base identity and chemistry are unaltered, and controls showing that observed effects are specifically due to mechanical perturbation rather than other nick-induced changes.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The abstract claims that PIC-NIC reveals a highly position-dependent response to backbone disruption across 15 TFs, with most positions permissive and nicking at mechanically sensitive sites substantially reshaping binding.  
- **Evidence pointer** Location not provided  
- **Concern** No statistical details are provided regarding the number of replicates, the magnitude of binding changes considered significant, the criteria for classifying positions as permissive versus sensitive, or how multiple testing was handled across the large number of positions and TFs examined.  
- **Why it matters** Without clear statistical thresholds and error analysis, the classification of positions as sensitive or permissive could be arbitrary or driven by noise. The claim of position-dependence requires robust statistical support.  
- **Resolution test** Provide complete statistical methods, including replicate numbers, effect size thresholds, multiple testing corrections, and validation of the classification scheme, ideally with independent experimental confirmation of sensitive positions.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mechanistic evidence  
- **Claim pointer** The abstract claims that sensitive positions often coincide with strain-adapted DNA geometries, including Hoogsteen conformations, whose relaxation can enhance binding or rewire sequence specificity.  
- **Evidence pointer** Location not provided  
- **Concern** The abstract asserts a mechanistic link between nicking-sensitive positions and Hoogsteen conformations, but no structural or simulation data are visible to support this. The claim that relaxation of these conformations can enhance binding or rewire specificity is a strong mechanistic statement that requires direct evidence.  
- **Why it matters** This is the central mechanistic claim of the study. If the link to Hoogsteen conformations is not rigorously established, the interpretation of why certain positions are sensitive remains speculative.  
- **Resolution test** Provide structural evidence for Hoogsteen conformations at sensitive positions, simulation data showing how nicking relaxes these conformations, and functional assays demonstrating that this relaxation directly causes the observed binding changes.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Biological significance  
- **Claim pointer** The abstract claims that genomic single-strand breaks and repair maps suggest that TF retention at nicked DNA may influence local repair-factor accessibility.  
- **Evidence pointer** Location not provided  
- **Concern** This claim extends the in vitro findings to a genomic and cellular context, but no data are presented to support the connection between TF retention at nicked DNA and repair-factor accessibility. The word "suggest" indicates speculation, but the claim is presented as a finding.  
- **Why it matters** This is the most biologically consequential claim in the abstract. If not supported by direct evidence, it overreaches beyond what the data can establish and could mislead readers about the in vivo relevance of the findings.  
- **Resolution test** Provide genomic data showing TF occupancy at sites of single-strand breaks, functional assays demonstrating that TF binding affects repair-factor recruitment or activity, and appropriate controls to establish causality.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract terminology  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The phrase "mechanically constrained polymer" is somewhat vague and could be more precisely defined in the context of DNA.  
- **Required correction** Clarify what specific mechanical constraints are being referenced, such as bending stiffness, torsional rigidity, or backbone connectivity.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** TF family representation  
- **Evidence pointer** Abstract, "15 TFs spanning eight structural families"  
- **Issue** The abstract does not specify which TF families are included or how representative they are of the broader TF repertoire.  
- **Required correction** List the TF families studied and justify their selection as representative of diverse DNA-binding domains.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Repair-factor accessibility claim  
- **Evidence pointer** Abstract, final sentence  
- **Issue** The phrase "may influence" is appropriately cautious, but the preceding sentence presents the genomic data as if it directly supports this possibility.  
- **Required correction** Clearly distinguish between the in vitro findings and the speculative extension to repair biology, perhaps by explicitly labeling the latter as a hypothesis.

## Risk / unsupported claims
- The claim that PIC-NIC minimizes chemical changes accompanying nicking is unsupported without detailed characterization data.
- The claim that sensitive positions coincide with Hoogsteen conformations is unsupported without structural or simulation evidence.
- The claim that relaxation of Hoogsteen conformations can enhance binding or rewire specificity is unsupported without direct functional data.
- The claim that TF retention at nicked DNA may influence repair-factor accessibility is speculative and not supported by any visible evidence.
- The generalizability of findings across 15 TFs and eight structural families is not assessable without per-TF data.