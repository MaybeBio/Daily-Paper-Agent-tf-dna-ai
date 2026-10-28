## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report the cryo-EM structure of the vaccinia virus D5 helicase-primase C-terminal hexameric construct (D5323–785) at 4.1 Å resolution, aided by AlphaFold2 prediction. They assign three structural domains (collar, AAA+ helicase, C-terminal), identify a central channel potentially accommodating dsDNA, and propose evolutionary relationships with other SF3 helicases based on structural comparisons.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusions, figure legends referenced in text (Figures 1–7, Supplementary Figures S1–S3, Tables 1–3)
- **Missing materials affecting confidence** Raw cryo-EM density maps, validation reports, full figure panels, supplementary data files, and detailed refinement statistics beyond what is summarized in Table 2

## Reviewer
- **Overall assessment** The manuscript presents a technically competent cryo-EM structure determination of a biologically relevant viral replication protein, with sensible use of AlphaFold2 for model building. The work is of interest to the poxvirus and helicase communities. However, several claims regarding DNA binding, domain organization, and evolutionary implications are supported by limited or indirect evidence, and the resolution limitations of the C-terminal domain reduce confidence in some structural interpretations. The manuscript would benefit from clearer presentation of validation metrics and more cautious framing of functional inferences.
- **Who would be interested in the results, and why** Researchers studying poxvirus replication and pathogenesis, structural biologists interested in AAA+ helicases and SF3 family proteins, and computational biologists evaluating AlphaFold2 applications in experimental structure determination. The proposed domain organization and evolutionary links may also interest virologists studying nucleo-cytoplasmic large DNA viruses and related mobile genetic elements.
- **Major strengths** The combination of cryo-EM with AlphaFold2 prediction is timely and well-executed. The authors provide the first experimental structure for the D5_N and Pox_D5 domains, which fills a clear gap in the field. The discussion of symmetry breakdown and potential DNA binding modes is thoughtful and appropriately cautious given the resolution limits.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (resolution of C-terminal domain), R1-M2 (DNA assignment), R1-M3 (AlphaFold2 bias assessment)
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The structure is new, but the approach (cryo-EM plus AlphaFold2) is increasingly standard, and the functional insights are largely speculative.  
  *Scientific importance*: Moderate. Relevant to poxvirus biology and SF3 helicase evolution, but the lack of functional validation limits broader impact.  
  *Interdisciplinary readership*: Limited. Primarily of interest to structural virologists and helicase specialists.  
  *Technical soundness*: Generally sound for the core structure, but concerns about resolution-dependent interpretations and model bias need addressing.  
  *Readability for nonspecialists*: Acceptable, though some domain nomenclature and evolutionary arguments may be dense for general readers.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the C-terminal domain interpretation and DNA assignment.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The manuscript states the C-terminal domain structure is resolved at approximately 6 Å resolution and that the model "stayed as close as possible to the Alphafold2 model" for this region.  
- **Evidence pointer** Section 3.1, Figure 3a, Table 2  
- **Concern** At 6 Å resolution, secondary structure elements are not reliably resolved, and side-chain information is absent. The authors acknowledge this limitation but still present the C-terminal domain as a structural entity with specific features (e.g., topology conservation with NrS-1). The refined model for this domain is essentially the AlphaFold2 prediction placed into weak density, which does not constitute experimental validation.  
- **Why it matters** The C-terminal domain is discussed in the context of evolutionary relationships and potential functional roles (e.g., DNA interaction). If the experimental data cannot support domain-specific structural claims, these inferences are not established.  
- **Resolution test** Provide local resolution estimates for the C-terminal domain, show representative density for this region, and clearly state which features are experimentally supported versus modeled. If the density is insufficient, remove or explicitly downgrade claims about C-terminal domain structure.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim support  
- **Claim pointer** The manuscript proposes that the central channel can accommodate dsDNA and that additional density in the channel may represent bound DNA, with specific base-pair interpretations.  
- **Evidence pointer** Section 3.2, Figure 6b–f  
- **Concern** The assignment of additional density to dsDNA is highly speculative. The authors state the density is "not well defined enough to assign single-stranded or double-stranded DNA strands," yet they proceed to model six base pairs with specific strand paths. The sample contained a dsDNA 30-mer, but no biochemical evidence (e.g., crosslinking, mutation, or binding assays) is presented to confirm that the observed density corresponds to DNA rather than buffer components or protein conformational heterogeneity.  
- **Why it matters** The DNA binding mode is a central functional claim. Without validation, the proposed interaction geometry and the mechanistic implications drawn from it are unsupported.  
- **Resolution test** Provide biochemical or mutagenesis data supporting DNA binding at the proposed site, or clearly label the density as unassigned and remove the specific DNA model.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Technical soundness  
- **Claim pointer** The manuscript states that AlphaFold2 prediction "greatly helped" model building and that the final model matches the prediction with low RMSD values.  
- **Evidence pointer** Section 2.7, Section 3.1, Table 2  
- **Concern** The degree to which the final model is biased by the AlphaFold2 prediction is not quantitatively assessed. The reported RMSD values (1.0–1.3 Å) between the refined model and the prediction are expected if the prediction was used as the starting point, especially in lower-resolution regions. No independent validation (e.g., omit maps, cross-validation) is presented to demonstrate that the experimental density alone would support the same model.  
- **Why it matters** The claim that the structure is "determined" by cryo-EM is weakened if the model is largely derived from prediction in key regions. This affects the reliability of all structural interpretations.  
- **Resolution test** Provide a model-map correlation analysis per domain, show density for regions where the model deviates from the prediction, and discuss how model bias was minimized.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 2.5  
- **Evidence pointer** "Figure S1a shows the pipeline for particle reconstruction"  
- **Issue** The description of the image processing pipeline is brief and refers to supplementary material without summarizing key parameters (e.g., number of particles, symmetry enforcement steps, final particle counts per class).  
- **Required correction** Add a concise summary of the processing workflow in the main text, including final particle numbers and resolution determination details.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Section 2.4, Table 1  
- **Evidence pointer** "The parameters are described in Table 1"  
- **Issue** Table 1 is referenced but not visible in the provided text. Key data collection parameters (e.g., microscope, detector, magnification, dose) are essential for reproducibility.  
- **Required correction** Ensure Table 1 is included and complete, or summarize the most critical parameters in the text.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Claim support  
- **Affected element** Section 4.1  
- **Evidence pointer** "The structure shows the power of structure calculation by Alphafold2"  
- **Issue** This statement is overly broad. The manuscript demonstrates that AlphaFold2 was useful for this specific case, but does not provide a systematic evaluation of its predictive power for this class of proteins.  
- **Required correction** Rephrase to a more specific statement about the utility of AlphaFold2 in this study.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 4.2  
- **Evidence pointer** "Dali homologies with the C-terminal domain appear weak with a best, but not necessarily significant, hit"  
- **Issue** The evolutionary discussion relies on weak structural similarities. The authors should clarify the statistical significance thresholds used and avoid overinterpreting marginal hits.  
- **Required correction** Provide Z-scores or significance measures for the Dali hits and temper the evolutionary claims accordingly.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Section 3.1  
- **Evidence pointer** "The D5_N domain is composed of an N-terminal α-helix, followed by a three-stranded β-sheet..."  
- **Issue** The domain description is dense and would benefit from a schematic figure or simplified summary for nonspecialist readers.  
- **Required correction** Consider adding a domain architecture diagram or a brief plain-language summary of the structural organization.

## Risk / unsupported claims
- The specific DNA binding model (six base pairs with defined strand paths) is not supported by the presented evidence and should be considered speculative.
- The evolutionary relationship between D5 and ribosomal protein S17, based on a single domain match, is presented with insufficient statistical support.
- The claim that the structure "validates" AlphaFold2 predictions for thousands of viral helicases is an overstatement not supported by the data presented.
- The functional relevance of the C-terminal domain, including its potential role in DNA interaction, is not experimentally tested and should be framed as hypothesis-generating.
- The statement that the central channel "could be large enough to accommodate dsDNA" is based on geometric considerations only and should not be presented as a functional conclusion.