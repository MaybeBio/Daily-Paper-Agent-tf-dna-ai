## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors compare structural features of X proteins from mammalian and avian hepadnaviruses, propose that avian X proteins lack a BH3-like domain due to a truncating stop codon, and suggest that a theoretical read-through or frameshift could restore an analogous BH3-like domain capable of binding Bcl-2. They further hypothesize that a single-nucleotide insertion may explain the loss of this domain and the absence of hepatocellular carcinoma in birds.
- **Visible evidence base** Abstract text only; no sequence alignments, modeling outputs, binding assays, or phylogenetic analyses are visible
- **Missing materials affecting confidence** Full manuscript, consensus sequence construction details, alignment figures, RoseTTAFold and AlphaFold3 outputs, confidence scores, Bcl-2 binding data, evolutionary analysis, and any statistical or experimental validation

## Reviewer
- **Overall assessment** The abstract presents an intriguing evolutionary and structural hypothesis linking the absence of a BH3-like domain in avian X proteins to the lack of HCC in birds. The premise is biologically plausible and potentially of interest to virologists and cancer biologists. However, the evidence base provided is insufficient to evaluate the technical soundness of the modeling, the validity of the sequence analyses, or the strength of the evolutionary claim. The central hypothesis rests on speculative mechanisms (read-through, frameshift, single-nucleotide insertion) that are not supported by direct evidence in the abstract. The case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying HBV pathogenesis, viral oncoproteins, hepadnavirus evolution, and the molecular basis of species-specific cancer susceptibility. The structural comparison across mammalian and avian viruses could inform understanding of HBx function and potential therapeutic targets, and the evolutionary hypothesis may interest comparative virologists.
- **Major strengths** The question is well-framed and addresses a clinically relevant gap in understanding why avian hepadnaviruses do not cause HCC. The use of modern structure prediction tools (RoseTTAFold and AlphaFold3) is appropriate for a comparative structural study. The hypothesis is testable and could stimulate further experimental work.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any validation of the predicted structures, no experimental evidence for Bcl-2 binding, and no phylogenetic or sequence-based support for the proposed single-nucleotide insertion event. The modeling results are presented without confidence metrics or comparison to experimental structures.
- **Assessment against Nature-style criteria** 
  - Originality: The hypothesis is novel in linking a specific structural domain loss to species-specific cancer outcomes, but the conceptual framework (BH3 domain in HBx) is not new.
  - Scientific importance: Potentially high if the structural and evolutionary claims are rigorously supported, as it could explain a long-standing observation in hepadnavirus biology.
  - Interdisciplinary readership: Would appeal to virologists, structural biologists, and cancer researchers, but the abstract does not currently make the case accessible or compelling beyond a narrow specialty.
  - Technical soundness: Not assessable from the abstract; no details on sequence curation, alignment quality, modeling parameters, or binding predictions.
  - Readability for nonspecialists: The abstract is generally clear but uses domain-specific terminology without sufficient context for a broad audience.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if the full manuscript provides robust structural validation, experimental binding data, and a defensible evolutionary analysis.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that comparative analyses show mammalian X proteins have a BH3-like domain in their C-terminal region, while avian X proteins lack this domain due to truncation.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract states that mammalian X proteins are longer and have distinct C-terminal domains including a BH3-like domain, but no sequence alignment, domain prediction method, or structural evidence is shown. The claim that avian X proteins are truncated with a "similarly located stop codon" is presented without supporting sequence data or alignment figures.
- **Why it matters** The central structural distinction between mammalian and avian X proteins is the foundation of the entire hypothesis. Without visible evidence of the alignments, domain annotations, or structural models, the reader cannot assess whether the BH3-like domain assignment is accurate or whether the truncation is consistently observed across avian species.
- **Resolution test** Provide the consensus sequence alignments with clear domain annotations, the method used to identify the BH3-like domain (e.g., sequence profile, structural homology), and the confidence scores from RoseTTAFold and AlphaFold3 for the relevant regions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that a theoretical read-through or frameshift in avian X proteins reveals an analogous BH3-like domain that can bind Bcl-2.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract reports that an analogous BH3-like domain is found by theoretical read-through or frameshifts and that it "can similarly bind" Bcl-2. No details are given on how the read-through or frameshift was modeled, what criteria were used to define the domain, or how binding was predicted or measured. The term "can bind" implies a functional result, but no experimental or computational binding assay is described.
- **Why it matters** This is the key mechanistic claim linking the lost domain to the absence of HCC. If the binding prediction is based solely on sequence similarity or docking without experimental validation, the claim is speculative. The evolutionary hypothesis depends on this domain being functionally relevant, not merely present in a hypothetical translation product.
- **Resolution test** Describe the computational method for identifying the read-through or frameshift product, provide the predicted structure with confidence metrics, and include either experimental binding data (e.g., co-immunoprecipitation, isothermal titration calorimetry) or a well-validated docking study with appropriate controls.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evolutionary inference
- **Claim pointer** The authors suggest that a single-nucleotide insertion led to the stop codon and BH3-domain loss, which may account for the lack of HCC in avian species.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract proposes an evolutionary scenario (single-nucleotide insertion) without presenting any phylogenetic analysis, ancestral sequence reconstruction, or comparative genomic evidence. The causal link between BH3-domain loss and absence of HCC is asserted as "may account for," but no functional or epidemiological data are provided to support this connection.
- **Why it matters** The evolutionary claim is the broader significance of the paper. Without evidence that the proposed insertion event occurred at a specific point in avian hepadnavirus evolution, or that the BH3 domain is functionally required for HCC in mammals, the hypothesis remains untested speculation. The absence of HCC in birds could have many other explanations.
- **Resolution test** Provide a phylogenetic analysis of X protein sequences across hepadnaviruses, reconstruct ancestral sequences to date the proposed insertion event, and discuss alternative explanations for the lack of HCC in birds. If possible, include functional experiments showing that restoring the BH3 domain in an avian X protein confers oncogenic activity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract text; location not provided
- **Issue** The phrase "the 'lost' BH3-like domain" in the title is ambiguous. It is unclear whether "lost" refers to an evolutionary loss, a functional loss, or a detection failure.
- **Required correction** Clarify the meaning of "lost" in the title or abstract, for example by specifying "evolutionarily lost" or "undetectable by standard sequence analysis."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Modeling approach
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract mentions using both RoseTTAFold and AlphaFold3 but does not state whether the two methods produced consistent results or how discrepancies were resolved.
- **Required correction** Add a sentence in the abstract or methods indicating the level of agreement between the two modeling tools and how any differences were handled.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Domain nomenclature
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "BH3-like domain" is used without defining the criteria for "like." It is unclear whether this refers to sequence homology, structural similarity, or functional mimicry.
- **Required correction** Define the criteria used to classify a region as BH3-like, including the sequence motif or structural feature used for identification.

## Risk / unsupported claims
- The claim that avian X proteins lack a BH3-like domain is unsupported without visible alignment or domain prediction data.
- The claim that a theoretical read-through or frameshift produces a BH3-like domain that binds Bcl-2 is unsupported without binding data or detailed computational predictions.
- The claim that a single-nucleotide insertion led to the stop codon and BH3-domain loss is unsupported without phylogenetic or ancestral sequence analysis.
- The causal link between BH3-domain loss and the absence of HCC in birds is not established and is presented as speculation.