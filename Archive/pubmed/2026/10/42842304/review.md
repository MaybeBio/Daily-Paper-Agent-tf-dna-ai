## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report a comparative genomic analysis of 1,740 chromosome-level Pseudomonas genomes to examine the distribution, evolution, and ecological associations of LuxI/R quorum sensing systems and LuxR solo regulators. They claim that LuxI/R systems are patchily distributed with lineage-dependent retention and dynamic gain/loss, that LuxR solos are pervasive and expanded especially in environmental and plant-associated species, that phylogenetic and AlphaFold3-guided structural analyses suggest diversification of ligand-binding domains, that multiple LuxR solos in single genomes occupy distinct clades implying non-redundancy, and that LuxI/R expansion associates with rhizosphere lifestyles while LuxR solo diversification correlates with intimate plant-associated niches.
- **Visible evidence base** Abstract text only; no genomic datasets, phylogenetic trees, structural models, statistical analyses, or ecological metadata are visible
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, phylogenetic tree files, AlphaFold3 structural predictions, ecological association analyses, and statistical details

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting and broad survey of quorum sensing architecture across Pseudomonas, with a plausible central thesis that LuxR solos rather than canonical LuxI/R systems drive diversification. However, the evidence base available for review is limited to the abstract, and several claims are stated with strong interpretive language that goes beyond what can be verified from the summary alone. The phylogenetic and structural analyses are mentioned but not described in sufficient detail to assess technical validity. The ecological associations are asserted without presentation of statistical support. The work may be of interest to microbiologists studying quorum sensing and bacterial communication, but the current abstract does not provide enough information to establish the robustness of the central conclusions.
- **Who would be interested in the results, and why** Researchers in bacterial quorum sensing, Pseudomonas biology, microbial ecology, and evolutionary genomics would be interested. The claim that LuxR solos are more ecologically and evolutionarily significant than canonical LuxI/R systems in Pseudomonas challenges a classical view and could inform studies on bacterial communication in plant-associated and environmental niches. The potential diversification of ligand-binding domains may also interest those studying signal recognition and receptor evolution.
- **Major strengths** The study addresses a large and well-defined dataset of 1,740 chromosome-level genomes, which is a substantial resource for comparative analysis. The focus on both canonical LuxI/R systems and LuxR solos provides a broader perspective than many prior studies. The integration of phylogenetic and structural predictions (AlphaFold3) is a modern and potentially powerful approach. The ecological framing linking QS architecture to lifestyle is conceptually appealing and could generate testable hypotheses.
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
  - Originality: The abstract suggests a novel synthesis regarding the primacy of LuxR solos over canonical LuxI/R systems in Pseudomonas, which is a fresh angle on a well-studied topic. However, the originality cannot be fully assessed without seeing how the findings compare to prior genomic surveys.  
  - Scientific importance: If the claims are robust, the work could shift thinking about quorum sensing evolution and ecological adaptation. The importance is potentially high, but the abstract does not yet demonstrate the strength of the evidence.  
  - Interdisciplinary readership: The topic bridges microbiology, genomics, ecology, and structural biology, which could attract a broad audience. The abstract is written in a way that is largely accessible, though some terms assume specialist knowledge.  
  - Technical soundness: Not assessable from the abstract. The phylogenetic methods, structural prediction validation, and ecological statistical approaches are not described.  
  - Readability for nonspecialists: The abstract is generally clear and well-structured, but phrases such as "weak lineage constraint" and "AlphaFold3-guided structural analyses" may require more explanation for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis and a large-scale approach, but the absence of methods, data, and statistical details means the core claims cannot be evaluated. A supportive posture would require access to the full manuscript and verification of the phylogenetic, structural, and ecological analyses.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "complete LuxI/R systems are patchily distributed across the genus" and that "LuxI/R systems display strong lineage-dependent retention patterns, with selective expansion in specific taxa and recurrent absence in many others, suggesting dynamic evolutionary gain, loss and diversification."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract states these distribution and evolutionary patterns but provides no details on how they were determined. No information is given on the criteria used to define a "complete" LuxI/R system, the phylogenetic methods used to infer gain and loss, or the statistical framework for assessing lineage-dependent retention.  
- **Why it matters** The central claim that LuxI/R systems are not universally conserved and are dynamically gained and lost depends entirely on the robustness of the comparative genomic and phylogenetic analyses. Without methodological transparency, the claim cannot be distinguished from artifacts of genome annotation or incomplete assemblies.  
- **Resolution test** The full manuscript must describe the genome selection criteria, the annotation and curation of LuxI/R genes, the phylogenetic reconstruction methods, and the ancestral state reconstruction or other approaches used to infer gain and loss. The authors should also provide a measure of confidence in the inferred evolutionary events.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "Phylogenetic and AlphaFold3-guided structural analyses of LuxR solo ligand-binding domains revealed potential diversification of predicted signal response, suggesting possible broad evolution of ligand-recognition capabilities."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract mentions AlphaFold3-guided structural analyses but does not specify how the structural predictions were validated, how ligand-binding domains were defined, or how "potential diversification" was assessed. AlphaFold3 predictions are computational and require experimental or comparative validation to support claims about functional diversification.  
- **Why it matters** The claim that LuxR solos have diversified ligand-recognition capabilities is a key part of the paper's thesis. If the structural analyses are not rigorously validated, the claim remains speculative and could mislead readers about the functional significance of the observed sequence diversity.  
- **Resolution test** The manuscript must describe the structural prediction pipeline, the criteria for identifying ligand-binding domains, any quality metrics for the AlphaFold3 models, and the comparative framework used to infer diversification. Ideally, the authors would also discuss limitations of computational predictions and any supporting experimental or literature-based evidence.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The authors claim that "expansion of canonical LuxI/R systems appears to be associated primarily with rhizosphere-associated lifestyles, whereas LuxR solo diversification correlates with intimate plant-associated niches."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract asserts ecological associations but provides no statistical details. It is unclear how "rhizosphere-associated" and "intimate plant-associated" lifestyles were defined, how the associations were tested, and whether confounding factors such as phylogenetic relatedness were accounted for.  
- **Why it matters** The ecological correlation is a major conclusion of the study. Without proper statistical testing, the association could be driven by phylogenetic non-independence or by biased sampling of genome sequences from certain ecological niches.  
- **Resolution test** The full manuscript must present the ecological metadata sources, the statistical tests used, and the methods for controlling for phylogenetic confounding. The authors should also report effect sizes and confidence intervals for the claimed associations.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that "Multiple LuxR solos within single genomes frequently occupied distinct phylogenetic and structural clades, possibly indicating that they are unlikely to be functionally redundant and this leads us to speculate that they could mediate responses to diverse environmental, microbial or host-derived signals."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract itself uses the word "speculate" for the functional interpretation, which is appropriate, but the claim of non-redundancy is presented as a strong inference from phylogenetic and structural clustering. No evidence is provided that distinct clades correspond to distinct functions, and the possibility of redundancy despite sequence divergence is not addressed.  
- **Why it matters** The functional interpretation of LuxR solo diversity is central to the paper's broader message about ecological adaptability. If the inference is purely speculative, it should be clearly framed as a hypothesis rather than a finding.  
- **Resolution test** The manuscript should clarify the distinction between observed phylogenetic/structural patterns and functional inferences. The authors should either provide additional evidence for functional non-redundancy or explicitly state that this is a hypothesis requiring experimental testing.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The authors claim to have performed "a comprehensive comparative genomic analysis of 1,740 chromosome-level genomes across the genus Pseudomonas."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not state how the 1,740 genomes were selected, whether they represent the full diversity of the genus, or whether the dataset is publicly accessible. No accession numbers, database sources, or inclusion criteria are provided.  
- **Why it matters** Reproducibility is a core requirement for genomic studies. Without clear information on the dataset and its provenance, other researchers cannot verify the results or build on the work.  
- **Resolution test** The full manuscript must list the genome accession numbers, the source databases, the selection criteria, and any filtering steps. The authors should also state whether the dataset is available in a public repository.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The phrase "weak lineage constraint" is used without explanation. It is unclear whether this refers to low phylogenetic signal, low purifying selection, or something else.  
- **Required correction** Define the term explicitly or rephrase to describe the specific observation, such as "phylogenetic trees showed limited clustering by taxonomic lineage."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Precision  
- **Affected element** Abstract claim  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract states that LuxR solos are "pervasive and frequently expanded" but does not define what constitutes "expansion" in this context.  
- **Required correction** Specify the metric used to define expansion, such as gene copy number per genome or lineage-specific duplication events.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Abstract terminology  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "intimate plant-associated niches" is vague and could encompass endophytic, phyllosphere, or rhizoplane habitats.  
- **Required correction** Use more precise ecological categories and define them in the methods.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract scope  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not mention any limitations of the study, such as the reliance on computational predictions or the potential for annotation errors.  
- **Required correction** Add a sentence acknowledging key limitations in the abstract or ensure they are prominently discussed in the main text.

## Risk / unsupported claims

- The claim that LuxI/R systems are "patchily distributed" and show "dynamic evolutionary gain, loss and diversification" is unsupported without details on the phylogenetic and ancestral state reconstruction methods.
- The claim that AlphaFold3-guided structural analyses revealed "potential diversification of predicted signal response" is unsupported without validation of the structural predictions and a clear definition of the comparison framework.
- The claim that LuxR solos "could mediate responses to diverse environmental, microbial or host-derived signals" is explicitly speculative in the abstract and should be treated as a hypothesis, not a finding.
- The ecological associations between LuxI/R expansion and rhizosphere lifestyles, and between LuxR solo diversification and plant-associated niches, are unsupported without statistical details and control for phylogenetic confounding.
- The representativeness of the 1,740 genome dataset for the entire Pseudomonas genus is not assessable from the abstract.