## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report identification of a 13-mer minimal binding core within a stapled alpha-helical peptide targeting the transcription factor NF-Y. Two crystal structures were obtained showing an altered C-terminal peptide conformation in the bound state. Molecular dynamics simulations indicated that the C-terminal region of the stapled peptide is relatively flexible while retaining defined interactions with NF-Y. The authors conclude that flexibility in the bound state of peptides can contribute to overall binding affinity.
- **Visible evidence base** Abstract text only; no structural coordinates, simulation parameters, quantitative binding data, or statistical analyses are provided
- **Missing materials affecting confidence** Full manuscript, crystallographic data and refinement statistics, simulation protocols and convergence criteria, binding affinity measurements, sequence details of the stapled peptide, comparison with previously reported NF-Y peptide inhibitors, and any control experiments

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting observation regarding conformational flexibility in a stapled peptide bound to NF-Y, with implications for peptide inhibitor design. However, the evidence base available for assessment is limited to the abstract, and several key claims cannot be evaluated without access to the underlying data. The central conclusion that bound-state flexibility contributes to binding affinity is plausible but not quantitatively supported by the information provided.
- **Who would be interested in the results, and why** Researchers working on peptide-based inhibitors of transcription factors, particularly those targeting protein-protein interactions; structural biologists studying intrinsically disordered or flexible regions in protein-ligand complexes; computational chemists developing molecular dynamics approaches for peptide binding studies; and medicinal chemists interested in stapled peptide optimization strategies.
- **Major strengths** The study addresses a relevant and underexplored question regarding the role of conformational dynamics in stapled peptide binding. The combination of crystallography and molecular dynamics simulations is appropriate for investigating conformational flexibility. Identification of a minimal binding core provides practical value for future inhibitor design efforts.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  **Originality** The concept of examining bound-state flexibility in stapled peptides is not entirely new, but the specific application to NF-Y and the identification of a minimal binding core may offer incremental novelty. The abstract does not clearly articulate how this work advances beyond existing structural and computational studies of NF-Y peptide inhibitors.  
  **Scientific importance** The broader importance of understanding peptide flexibility for inhibitor design is clear, but the abstract does not demonstrate that the findings lead to testable predictions or improved inhibitor potency. The claim that flexibility contributes to binding affinity is not supported by quantitative data in the abstract.  
  **Interdisciplinary readership** The topic bridges structural biology, computational chemistry, and chemical biology, which could attract a broad readership. However, the abstract is written in a way that is accessible to specialists in these fields but may not be fully accessible to a general scientific audience.  
  **Technical soundness** The combination of crystallography and molecular dynamics is methodologically appropriate, but the abstract provides insufficient detail to assess the quality of the structures, the convergence of simulations, or the robustness of the flexibility analysis.  
  **Readability for nonspecialists** The abstract is concise and generally clear, but terms such as "stapled peptide" and "minimal binding core" are used without sufficient context for readers outside the peptide chemistry field.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting observation, but the central claim regarding the contribution of flexibility to binding affinity requires quantitative support that is not visible in the abstract. A supportive posture would require access to the full manuscript and verification of the structural and simulation data.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that "flexibility in the bound state of peptides... can contribute to overall binding affinity."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract states that molecular dynamics simulations confirmed flexibility of the C-terminal region, but no quantitative data are presented linking this flexibility to binding affinity. No binding free energy calculations, mutation studies, or comparative analyses with less flexible analogs are described.  
- **Why it matters** The central conclusion of the study rests on a causal relationship between conformational flexibility and binding affinity. Without quantitative evidence, this claim remains speculative and cannot be distinguished from a descriptive observation of dynamics.  
- **Resolution test** Provide binding affinity measurements for the stapled peptide and variants with restricted or enhanced C-terminal flexibility, or present free energy calculations that quantitatively correlate flexibility with binding affinity.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical validation  
- **Claim pointer** The authors report obtaining "two crystal structures with an altered C-terminal peptide conformation when bound to NF-Y."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not provide any crystallographic details, including resolution, R-factors, or the nature of the conformational difference between the two structures. It is unclear whether the two structures represent distinct biological conformations or crystallization artifacts.  
- **Why it matters** The structural observation is foundational to the subsequent simulation and the flexibility claim. If the two conformations are not robustly determined, the interpretation of flexibility is weakened.  
- **Resolution test** Provide crystallographic statistics, electron density quality for the C-terminal region, and a clear description of the conformational differences, including whether they are observed in multiple crystal forms or supported by other biophysical methods.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility and completeness  
- **Claim pointer** The authors state that "molecular dynamics simulations confirmed that the C-terminal part of the stapled peptide is indeed relatively flexible while still showing defined interactions with NF-Y."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No simulation details are provided, including force field, simulation length, number of replicas, convergence criteria, or analysis methods for flexibility. The term "confirmed" implies a level of certainty that cannot be assessed without these details.  
- **Why it matters** Molecular dynamics results are highly dependent on simulation setup and analysis choices. Without this information, the reliability of the flexibility conclusion cannot be evaluated, and the study cannot be reproduced.  
- **Resolution test** Provide full simulation protocols, convergence assessments, and quantitative measures of flexibility (e.g., root-mean-square fluctuations) with error estimates.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Definition of "minimal binding core"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract states that a "13-mer minimal binding core region" was identified, but it is not clear how this was determined. Was it based on truncation studies, structural analysis, or sequence conservation?  
- **Required correction** Clarify the experimental or computational basis for defining the minimal binding core.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Comparison with prior work  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not place the findings in the context of previously reported NF-Y peptide inhibitors or stapled peptide studies targeting transcription factors.  
- **Required correction** Add a brief statement in the abstract or introduction that contextualizes the novelty of the findings relative to existing literature.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Use of "confirmed"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The word "confirmed" in the context of molecular dynamics simulations is overly strong, as simulations provide a model-based interpretation rather than direct experimental confirmation.  
- **Required correction** Replace "confirmed" with a more measured term such as "suggested" or "indicated."

## Risk / unsupported claims
- The claim that bound-state flexibility contributes to binding affinity is unsupported by quantitative data in the abstract.
- The claim that the two crystal structures demonstrate an "altered C-terminal peptide conformation" is not assessable without crystallographic details.
- The claim that molecular dynamics simulations "confirmed" flexibility is not assessable without simulation protocols and analysis details.
- The identification of a "13-mer minimal binding core" is not supported by any experimental evidence in the abstract.