## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors report structure-based computational design of five peptide ligands targeting the RpoC-SigA interface in *Helicobacter pylori* transcription machinery, with three peptides (P1, P3, P5) showing significant predicted binding affinity and potential to inhibit holoenzyme formation.
- **Visible evidence base** Abstract text only; no quantitative data, model validation metrics, or experimental results provided
- **Missing materials affecting confidence** Full manuscript, structural models, docking/scoring data, validation statistics, supplementary information, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible computational workflow for peptide design targeting a specific protein-protein interaction in *H. pylori*. However, the evidence base is insufficient to evaluate the technical soundness of the modeling approach, the reliability of the binding affinity predictions, or the biological relevance of the proposed inhibition mechanism. The claims of "significant affinity" and "potential hindrance" are not supported by any quantitative data in the abstract.
- **Who would be interested in the results, and why** Researchers in antimicrobial drug discovery, particularly those focused on *H. pylori* and alternative strategies to combat antibiotic resistance. Computational biologists working on protein-protein interaction inhibitors and peptide design may also find the methodological approach relevant.
- **Major strengths** The study addresses a clinically important problem (antibiotic resistance in *H. pylori*) with a rational structure-based approach. Targeting a specific protein-protein interaction in the transcription machinery is a mechanistically sound strategy. The use of template-based modeling in the absence of experimental structures is a reasonable starting point.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** Model quality validation, binding affinity calculation methodology, and demonstration of specificity are not described in the abstract. Without these, the core claims cannot be assessed.
- **Assessment against Nature-style criteria**  
  - **Originality** The approach is not novel in concept; structure-based peptide design targeting protein-protein interactions is an established strategy. The specific target (RpoC-SigA in *H. pylori*) may offer some novelty, but this is not sufficient for high-impact publication.  
  - **Scientific importance** The problem is important, but the abstract does not demonstrate that the proposed peptides would work in a biological context. The potential clinical relevance is speculative.  
  - **Interdisciplinary readership** The work sits at the interface of computational biology and antimicrobial drug discovery, which could attract a moderate interdisciplinary audience. However, the abstract lacks sufficient detail to engage experimentalists.  
  - **Technical soundness** Cannot be evaluated from the abstract. No model validation, scoring function details, or statistical measures are provided.  
  - **Readability for nonspecialists** The abstract is generally clear but uses jargon (e.g., "hybrid template-based modeling") without explanation. The logic from modeling to peptide design to inhibition is understandable at a high level.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient information to support the claims. A full manuscript with detailed methods and validation would be required for a more definitive assessment.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "The complex was built based on hybrid template-based modeling (TBM) techniques" and "Investigation of the binding affinity of all five peptides suggests that P1, P3, and P5 exhibit significant affinity"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract provides no information on how the structural models were validated, what templates were used, or what quality metrics (e.g., RMSD, MolProbity scores, Ramachandran statistics) were achieved. Similarly, the binding affinity calculations are described only qualitatively with no mention of the method (e.g., molecular docking, molecular dynamics, MM-PBSA) or any numerical results.  
- **Why it matters** Without model validation, the structural basis for peptide design is unreliable. Without quantitative binding data, the claim of "significant affinity" is unsupported and cannot be compared against known thresholds or controls.  
- **Resolution test** Provide model validation statistics, template details, and a clear description of the binding affinity method with numerical results (e.g., binding energies, confidence intervals) and appropriate controls.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Specificity and selectivity  
- **Claim pointer** "design specific peptide ligands" and "potential hindrance to RNAP interaction with transcription factors prior to holoenzyme formation"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not demonstrate that the designed peptides are specific to the RpoC-SigA interface. No off-target analysis, sequence similarity checks against other *H. pylori* proteins or host proteins, or experimental selectivity data are mentioned. The proposed mechanism of hindering holoenzyme formation is speculative without evidence that the peptides would not interfere with other protein-protein interactions in the transcription machinery.  
- **Why it matters** Specificity is a core requirement for any proposed therapeutic agent. Without evidence of selectivity, the peptides could have unintended effects, undermining the proposed therapeutic value.  
- **Resolution test** Provide sequence alignment analyses against relevant proteomes, docking against unrelated interfaces as negative controls, or experimental binding assays with mutant or unrelated targets.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Biological relevance and translational potential  
- **Claim pointer** "These peptides may serve as promising inhibitors against H. pylori infection"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract reports only computational predictions. There is no mention of any experimental validation, such as bacterial growth inhibition assays, transcription activity measurements, or cell-based studies. The leap from in silico binding affinity to "promising inhibitors" is not justified.  
- **Why it matters** Computational predictions frequently do not translate to biological activity. Without experimental evidence, the clinical or therapeutic relevance of these peptides remains entirely speculative.  
- **Resolution test** Provide experimental data demonstrating peptide activity in relevant assays (e.g., in vitro transcription inhibition, bacterial viability assays) or clearly frame the work as a computational proof-of-concept with appropriate caveats.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity and completeness  
- **Affected element** Methods description  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "hybrid template-based modeling (TBM) techniques" is vague. It is unclear what "hybrid" refers to (e.g., combination of homology modeling and ab initio methods, or multiple templates).  
- **Required correction** Specify the exact modeling approach, including software used, template PDB IDs, and the nature of the hybrid strategy.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Quantitative reporting  
- **Affected element** Binding affinity results  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract states that P1, P3, and P5 "exhibit significant affinity" but provides no numerical values, units, or comparison to P2 and P4.  
- **Required correction** Report quantitative binding scores (e.g., docking scores, binding free energies) for all five peptides, with appropriate statistical measures and a clear definition of "significant."

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Biological context  
- **Affected element** Introduction of biological rationale  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract states that *H. pylori* "colonize the gastric epithelial cells" and "poses a strong risk factor" but does not explain why targeting the RpoC-SigA interaction is a viable therapeutic strategy compared to other essential processes in the bacterium.  
- **Required correction** Briefly justify the choice of this specific protein-protein interaction as a drug target, referencing its essentiality and conservation.

## Risk / unsupported claims
- The claim that P1, P3, and P5 exhibit "significant affinity" is unsupported by any quantitative data in the abstract.
- The claim that these peptides "may serve as promising inhibitors against H. pylori infection" is unsupported by any experimental evidence.
- The structural models and the complex structure are described but their quality and reliability cannot be assessed from the abstract.
- The proposed mechanism of "potential hindrance to RNAP interaction with transcription factors prior to holoenzyme formation" is speculative and not backed by functional data.