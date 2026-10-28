## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results and discussion, materials and methods, and figure legends as provided.
- **Assessment boundary** Scientific validity of the claims, experimental design, data interpretation, and consistency between stated methods and reported results. No assessment of editorial fit or publication venue.
- **Shared manuscript claim summary** The authors propose that the Chlamydia plasmid-encoded protein Pgp2 is a replication initiator, based on AlphaFold-predicted structural similarity to known initiators, and that a unique β-hairpin motif (residues 108-118) is conserved across Chlamydia species and essential for plasmid transformation, likely via iteron binding.
- **Visible evidence base** AlphaFold structural predictions, DALI structural homology search results, sequence alignments, plasmid construction and transformation experiments, fluorescence microscopy images. Figures referenced but not fully visible in the provided text.
- **Missing materials affecting confidence** Actual figures and supplementary data, raw transformation data (e.g., number of replicates, quantification), details of AlphaFold model confidence per region, negative control data for transformation experiments, and any direct DNA-binding assays.

## Reviewer
- **Overall assessment** The manuscript presents a plausible hypothesis supported by structural predictions and a functional transformation assay. However, the evidence linking the β-hairpin motif to iteron binding is indirect, and the transformation failure could be due to other factors such as plasmid stability or expression issues. The study is a useful contribution but requires additional experimental validation to firmly establish the mechanistic claim.
- **Who would be interested in the results, and why** Researchers studying Chlamydia biology, plasmid replication mechanisms, and obligate intracellular bacterial genetics. Also of interest to those working on structural prediction-based functional annotation and protein-DNA interactions.
- **Major strengths** The use of AlphaFold to predict function for a protein with no sequence homology is innovative. The identification of a conserved, unique β-hairpin motif is a clear and testable finding. The transformation assay directly tests the functional requirement of the motif in a relevant biological context.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3.
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. Structural prediction to assign function is not entirely new, but the specific application to Pgp2 and the identification of a unique motif are novel.  
  - Scientific importance: Moderate. The work clarifies a previously unknown protein function, but the broader impact is limited to Chlamydia plasmid biology.  
  - Interdisciplinary readership: Limited. Primarily relevant to microbiologists and structural biologists.  
  - Technical soundness: The structural predictions are reasonable, but the functional assay lacks direct mechanistic evidence.  
  - Readability for nonspecialists: The manuscript is generally clear, though some structural biology terms may be challenging for a general audience.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the need for direct DNA-binding evidence and additional controls.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that the β-hairpin motif is necessary for Pgp2 function and likely contributes to DNA binding.  
- **Evidence pointer** Results and Discussion, "Requirement of the β-hairpin motif for Pgp2 activity"; Figure 4  
- **Concern** The transformation failure of the Pgp2Δ108-118 plasmid is interpreted as evidence that the β-hairpin is required for Pgp2 function. However, the deletion could affect protein stability, expression levels, or plasmid maintenance independent of DNA-binding activity. No direct evidence of DNA-binding impairment is provided.  
- **Why it matters** The central mechanistic claim of the paper is that the β-hairpin mediates iteron binding. Without direct binding assays (e.g., electrophoretic mobility shift assay, surface plasmon resonance, or chromatin immunoprecipitation), the conclusion remains speculative.  
- **Resolution test** Perform in vitro DNA-binding assays with wild-type and mutant Pgp2 against the predicted iteron sequences. Alternatively, complementation studies with a mutant Pgp2 that retains structure but lacks the β-hairpin could help distinguish binding from other functions.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Experimental controls  
- **Claim pointer** The authors state that no transformants were detected with the mutant plasmid in three independent experiments.  
- **Evidence pointer** Results and Discussion, "Requirement of the β-hairpin motif for Pgp2 activity"; Figure 4D, E  
- **Concern** The transformation experiments lack critical controls. It is unclear whether the mutant plasmid DNA was successfully introduced into Chlamydia (e.g., via PCR detection of plasmid DNA in passaged cultures) or whether the failure is due to transformation efficiency issues rather than Pgp2 function. Additionally, no positive control for transformation efficiency (e.g., a plasmid with a neutral mutation) is described.  
- **Why it matters** Without these controls, the failure to observe GFP-expressing inclusions could be due to technical issues unrelated to Pgp2 function, undermining the conclusion that the β-hairpin is essential.  
- **Resolution test** Include a control plasmid with a mutation in a non-essential region, and verify plasmid uptake by PCR or sequencing of passaged cultures. Also, assess Pgp2 protein expression from the mutant plasmid in a heterologous system.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Structural evidence  
- **Claim pointer** The authors claim that the β-hairpin motif is unique to Pgp2 and absent in other replication initiators.  
- **Evidence pointer** Results and Discussion, "Identification of a conserved β-hairpin motif"; Figure 2, 3  
- **Concern** The claim of uniqueness is based on comparison with only three structurally similar initiators (π, RepE, RctB). A broader structural comparison across the initiator family is needed to support the claim that this motif is unique. Additionally, the functional significance of the β-hairpin is inferred from its position near the DNA-binding domain, but no structural or mutational data directly link it to iteron binding.  
- **Why it matters** The novelty of the finding rests on the uniqueness of the motif. If similar motifs exist in other initiators, the claim of a unique mechanism is weakened.  
- **Resolution test** Perform a comprehensive structural search against a larger database of initiator proteins and include a multiple sequence alignment of the β-hairpin region across all known Pgp2 homologs and related initiators.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, "In this study, we utilized AlphaFold to predict the 3-dimensional (3-D) structure of C. trachomatis Pgp2."  
- **Issue** The abstract states that the β-hairpin is "necessary for iteron-binding," but the results only show a transformation defect, not direct binding evidence.  
- **Required correction** Rephrase to "necessary for plasmid transformation, likely via iteron-binding" to avoid overstating the evidence.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Consistency  
- **Affected element** Results and Discussion  
- **Evidence pointer** Results and Discussion, "Requirement of the β-hairpin motif for Pgp2 activity"  
- **Issue** The text refers to "Pgp2Δ111-118" in one instance and "Pgp2Δ108-118" in others. This inconsistency is confusing.  
- **Required correction** Use a single nomenclature throughout, preferably "Pgp2Δ108-118" as defined in the methods.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Methodology  
- **Affected element** Materials and Methods, "C. trachomatis transformation"  
- **Evidence pointer** Materials and Methods, "C. trachomatis transformation"  
- **Issue** The transformation protocol states that ampicillin is used for selection, but the timing of addition (2 hpi) and the passaging schedule are not fully detailed.  
- **Required correction** Provide more detail on the selection timeline and criteria for considering a transformation successful or unsuccessful.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Figure 4  
- **Evidence pointer** Figure 4D, E  
- **Issue** The representative images are described but not shown in the text. It is unclear how many fields were examined and whether the images are representative of all replicates.  
- **Required correction** Include scale bars and a statement on the number of independent fields and replicates examined.

## Risk / unsupported claims
- The claim that the β-hairpin motif is "necessary for iteron-binding" is unsupported by direct experimental evidence; only an indirect transformation assay is provided.
- The claim that the β-hairpin is "unique" to Pgp2 is based on a limited structural comparison and may be overstated.
- The statement that Pgp2 "recruits the DNA helicase needed to initiate plasmid replication" is speculative and not tested in this study.
- The assertion that the β-hairpin's positively charged residues "likely facilitate interactions with the negatively charged iteron DNA" is a hypothesis without experimental validation.