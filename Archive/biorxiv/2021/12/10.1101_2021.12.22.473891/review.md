## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends as provided.
- **Assessment boundary** Scientific content, technical validity, and clarity of claims as presented in the provided text. No assessment of data files, supplementary materials, or deposited structures beyond what is described.
- **Shared manuscript claim summary** The authors report the purification of human RNA polymerase I (Pol I) from a genomically tagged cell line, its cryo-EM structure at 4.09 Å resolution, and functional assays indicating reduced proofreading activity compared to yeast. They identify a novel 'dock II' domain in the RPA1 subunit, resembling a truncated HMG-box, which may serve as a binding platform for transcription factors such as Topoisomerase 2a in metazoans.
- **Visible evidence base** Abstract, Introduction, Results sections (including subsections on purification, structure determination, architecture, disease mutations, and dock II), Discussion, Methods (including CRISPR, purification, assays, EM, and phylogenetics), and figure legends as referenced in the text.
- **Missing materials affecting confidence** The manuscript text does not include the actual figures, supplementary tables, or supplementary data files. Key quantitative data (e.g., resolution values, statistical analyses, gel images, ChIP-seq plots) are referenced but not visible. The deposited cryo-EM density and model coordinates are mentioned but not accessible for verification.

## Reviewer
- **Overall assessment** This manuscript presents a valuable contribution to the structural biology of human RNA polymerase I, addressing a significant gap in the field. The identification of a novel HMG-like domain ('dock II') in RPA1 and its potential role in recruiting Topoisomerase 2a is intriguing and of broad interest. However, the current evidence base, as presented in the text, has several limitations. The cryo-EM resolution is modest, and the functional data supporting the dock II-Top2a interaction are preliminary. The phylogenetic analysis is descriptive but lacks statistical rigor. The claims regarding reduced proofreading and the role of dock II require stronger experimental support. The manuscript would benefit from clearer presentation of quantitative results and a more cautious interpretation of the structural and functional data.
- **Who would be interested in the results, and why** Structural biologists studying RNA polymerases and transcription mechanisms would find the human Pol I structure valuable. Researchers in the field of ribosome biogenesis and its regulation, particularly in the context of cancer and developmental disorders, would be interested in the disease mutation mapping and the potential role of Top2a. The evolutionary analysis of Pol I subunit composition may appeal to those studying molecular evolution. The identification of a metazoan-specific domain could also attract interest from researchers studying transcription factor interactions and chromatin dynamics.
- **Major strengths** The manuscript addresses a clear gap in the field by providing the first structural characterization of human Pol I. The use of a genomically tagged cell line for purification is a methodological strength, enabling native complex isolation. The identification of the 'dock II' domain is a novel finding with potential functional significance. The mapping of disease-associated mutations onto the structure provides a useful framework for understanding pathology. The phylogenetic analysis, while descriptive, offers a broad evolutionary perspective.
- **Major Concerns** The major concerns are detailed below. They primarily relate to the strength of the functional claims, the resolution and interpretability of the structural data, and the preliminary nature of the protein interaction studies.
- **Minor Comments** Several minor issues regarding clarity, presentation, and interpretation are listed below.
- **Technical failings that need to be addressed before the case is established** The primary technical failing is the lack of direct, quantitative evidence for the dock II-Top2a interaction. The native gel shift and co-IP data are suggestive but not conclusive. The cryo-EM resolution of 4.09 Å limits the certainty of the structural interpretation, particularly for the novel domain. The functional assays for proofreading are qualitative and lack statistical analysis. The phylogenetic analysis lacks formal statistical support for the evolutionary conclusions.
- **Assessment against Nature-style criteria** 
  - **Originality** High. The structure of human Pol I and the identification of the 'dock II' domain are novel.
  - **Scientific importance** High. The work addresses a fundamental question in eukaryotic transcription and has implications for human disease.
  - **Interdisciplinary readership** Moderate. The primary audience is structural biologists and transcription researchers. The disease and cancer connections may broaden appeal, but the technical nature of the work may limit accessibility.
  - **Technical soundness** Moderate. The methods are generally sound, but the key functional claims are not fully supported by the presented evidence.
  - **Readability for nonspecialists** Moderate. The manuscript is well-written but assumes significant background knowledge in transcription and structural biology. The abstract is accessible, but the results and discussion are dense.
- **Recommendation posture** Supportive if technical concerns are resolved. The core structural finding is likely to be of interest, but the functional claims regarding dock II and Top2a need to be substantiated with more rigorous experiments. The manuscript would be strengthened by a more cautious interpretation of the data and a clearer presentation of quantitative results.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional claim
- **Claim pointer** "Biochemical analysis and ChIP data indicate that Topoisomerase 2a can be recruited to Pol I via the domain and cooperates with the HMG-box domain containing factor UBF."
- **Evidence pointer** Results section "The HMG box-containing 'dock II' domain may serve as interface for Topoisomerase 2a"; Sup. Fig. 7E; Fig. 5A-C
- **Concern** The claim that Top2a is recruited to Pol I via the dock II domain is based on a native PAGE shift and a co-IP from cell lysates. The native PAGE shows a shift with the full-length dock II domain but not the minimal domain, which is interpreted as an interaction. However, this is a qualitative assay and does not provide binding affinity or specificity data. The co-IP shows Top2a and RPA49 in a complex, but this does not demonstrate that the interaction is mediated by the dock II domain. The ChIP-seq data show Top2a localization across the rDNA, but this is not direct evidence of recruitment via dock II. The claim of cooperation with UBF is based on co-localization of ChIP peaks and a co-IP, which is suggestive but not conclusive.
- **Why it matters** The proposed function of the novel dock II domain as a recruitment platform for Top2a is a central claim of the manuscript. If this interaction is not robustly demonstrated, the functional significance of the domain remains speculative. The manuscript's title and abstract highlight this domain, so the evidence must be convincing.
- **Resolution test** Provide quantitative binding data (e.g., ITC, SPR, or MST) for the dock II domain and Top2a. Perform mutagenesis of the dock II domain to disrupt the interaction and show loss of Top2a recruitment in cells. Use a more specific assay, such as a proximity ligation assay or a targeted pull-down with purified components, to demonstrate a direct interaction. For the ChIP-seq data, show that Top2a recruitment to the rDNA is dependent on the dock II domain, for example by comparing wild-type and mutant cell lines.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural interpretation
- **Claim pointer** "Determination of the human Pol I cryo-EM reconstruction in a close-to-native state rationalizes the effects of disease-associated mutations and uncovers an additional domain that is built into the sequence of Pol I subunit RPA1."
- **Evidence pointer** Results section "Structure determination of hPol I"; Fig. 2; Sup. Fig. 4; Sup. Table 1
- **Concern** The cryo-EM reconstruction is reported at an overall resolution of 4.09 Å. At this resolution, while secondary structure elements can be identified, the precise registration of amino acid side chains and the accurate assignment of novel domains can be challenging. The authors state that the 'dock II' domain was identified and modeled, but the confidence in this model is not discussed. The manuscript mentions that the model was aided by AlphaFold predictions, but the extent to which the cryo-EM density supports the placement of this domain is unclear. The claim that the structure is "close-to-native" is based on the absence of crosslinking, but the sample preparation and grid conditions could still introduce artifacts.
- **Why it matters** The structural interpretation is the foundation of the manuscript. If the 'dock II' domain is not confidently placed, the subsequent functional hypotheses are weakened. The resolution also affects the reliability of the disease mutation mapping, as the local environment of these mutations may not be accurately resolved.
- **Resolution test** Provide a detailed analysis of the local resolution of the map, particularly around the 'dock II' domain. Show the cryo-EM density and the fitted model for this domain in a supplementary figure, with clear evidence of side-chain density or unambiguous secondary structure assignment. Discuss the confidence of the model in this region, including any validation metrics (e.g., Q-scores, MolProbity). If possible, compare the model to the AlphaFold prediction and highlight any differences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional claim
- **Claim pointer** "Human Pol I carries a single-subunit stalk and in vitro transcription indicates a reduced proofreading activity."
- **Evidence pointer** Results section "Human Pol I shows reduced proofreading in vitro"; Fig. 2B; Sup. Fig. 3
- **Concern** The claim of reduced proofreading is based on in vitro elongation and cleavage assays comparing human Pol I with yeast Pol I. The data show that human Pol I generates transcripts with incorrectly incorporated NTPs and has a reduced cleavage/backtracking ability. However, the assays are qualitative, and the differences are not quantified or subjected to statistical analysis. The manuscript does not discuss potential confounding factors, such as the presence of the RPA49/34 subcomplex at sub-stoichiometric levels in the human sample, which could affect the observed activity. The addition of recombinant RPA49/34 did not rescue the phenotype, but this does not rule out other factors.
- **Why it matters** The reduced proofreading activity is presented as a key functional difference between human and yeast Pol I. If this claim is not robust, the evolutionary and functional conclusions are weakened. The manuscript suggests that this may be an intrinsic feature of the human enzyme, but the evidence is not definitive.
- **Resolution test** Quantify the misincorporation and cleavage rates in the assays and provide statistical analysis (e.g., mean ± SD from at least three independent experiments). Include a control with a known proofreading-deficient Pol I mutant to validate the assay. Discuss the potential impact of sample heterogeneity (e.g., sub-stoichiometric RPA49/34) on the results. Consider testing the activity of the human enzyme with a fully reconstituted RPA49/34 complex to rule out a concentration effect.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evolutionary claim
- **Claim pointer** "Phylogenetic analysis also showed that the 'expander' (DNA-mimicking) element is present in all analyzed organisms." and "We clearly find that only organisms of the Saccharomycotina in the Dikarya clade carry sequences for the subunit A14, indicating that a single-subunit stalk is the standard Pol I configuration."
- **Evidence pointer** Results section "A single-subunit stalk is the predominant configuration for Pol I"; Fig. 3; Sup. Fig. 9
- **Concern** The phylogenetic analysis is based on sequence similarity searches and a tree constructed from concatenated sequences of RPA1, RPA34, and RPA43. The conclusion that A14 is only present in Saccharomycotina is based on the absence of a sequence in other taxa. This is a negative result and is sensitive to the quality of the sequence databases and the search parameters. The manuscript does not provide statistical support for the tree topology or the presence/absence of A14. The analysis of the 'expander' element is similarly descriptive.
- **Why it matters** The evolutionary conclusions are a significant part of the manuscript's narrative, suggesting that the single-subunit stalk and the 'dock II' domain are metazoan-specific adaptations. If the phylogenetic analysis is not robust, these conclusions are speculative.
- **Resolution test** Provide a more rigorous phylogenetic analysis, including bootstrap support values for the tree. For the presence/absence of A14, use a more sensitive search strategy (e.g., HMMER) and explicitly state the search parameters and database versions. Consider using a species tree to map the presence/absence of A14 and the 'dock II' domain, and perform a statistical test (e.g., ancestral state reconstruction) to support the claim of lineage-specific gains/losses.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "in vitro transcription indicates a reduced proofreading activity" but does not specify the comparison to yeast. This could be clearer for a general audience.
- **Required correction** Specify the comparison, e.g., "compared to yeast Pol I."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Specific tagging and purification of human RNA polymerase I"
- **Evidence pointer** Fig. 1C; Sup. Fig. 1
- **Issue** The text mentions an "optional subsequent ion-exchange chromatography step" that results in loss of RRN3 and RPA49/34. It is unclear whether the structural and functional data were obtained with the affinity-purified or the ion-exchange-purified sample.
- **Required correction** Clarify which purification protocol was used for each experiment (structure, activity assays, etc.).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "The HMG box-containing 'dock II' domain may serve as interface for Topoisomerase 2a"
- **Evidence pointer** Sup. Fig. 7E
- **Issue** The native PAGE shift is described as indicating an interaction, but the stoichiometry and specificity are not discussed. The minimal domain does not show a shift, which is interpreted as a lack of interaction, but this could be due to a lower affinity or a different binding mode.
- **Required correction** Discuss the potential reasons for the difference between the full-length and minimal domain in the binding assay. Consider performing a titration to assess affinity.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results section "Mapping of disease-associated mutations to Pol I subunit structures rationalizes enzyme deficiencies"
- **Evidence pointer** Sup. Fig. 6
- **Issue** The text describes the location of mutations but does not provide a clear summary table or figure legend that allows the reader to easily understand the structural context of each mutation.
- **Required correction** Consider adding a supplementary table listing each mutation, its location, and the proposed structural/functional consequence.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "Cryo-EM image processing and model building"
- **Evidence pointer** Methods
- **Issue** The methods state that "released AlphaFold 59 models were used to guide chain-tracing in poorly resolved areas." The specific version of AlphaFold and the criteria for using these models are not described.
- **Required correction** Provide the version of AlphaFold used and describe the criteria for incorporating the models into the refinement process.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion speculates on the function of the 'dock II' domain in recruiting Top2a and releasing supercoils, but does not fully consider alternative explanations or the limitations of the current data.
- **Required correction** Add a paragraph discussing alternative functions for the 'dock II' domain and the limitations of the current evidence, such as the lack of direct binding data and the preliminary nature of the ChIP-seq analysis.

## Risk / unsupported claims
- The claim that Top2a is recruited to Pol I via the 'dock II' domain is not fully supported by the presented data. The native PAGE and co-IP are suggestive but not conclusive, and the ChIP-seq data do not directly demonstrate a recruitment mechanism.
- The claim that the 'dock II' domain is a "transcription factor docking domain" is speculative, as no transcription factor has been shown to bind to it directly.
- The claim that the human Pol I structure is "close-to-native" is based on the absence of crosslinking, but this is not a definitive measure of native state.
- The phylogenetic conclusion that A14 is absent in all non-Saccharomycotina species is based on negative evidence and is sensitive to database completeness and search parameters.
- The claim of "reduced proofreading activity" is based on qualitative assays and lacks statistical support.
- The functional significance of the 'dock II' domain in supercoil release is a hypothesis that is not directly tested.