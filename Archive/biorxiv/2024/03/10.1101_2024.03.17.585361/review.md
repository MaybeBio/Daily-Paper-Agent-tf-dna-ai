## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided
- **Assessment boundary** Scientific claims, methodological soundness, and evidentiary support based solely on the supplied text; no external verification of sequences, models, or phylogenetic analyses performed
- **Shared manuscript claim summary** The manuscript proposes that receptor-binding domains (RBDs) in retroviral envelope (Env) proteins have been transferred between divergent retroviral lineages via intragene recombination, and reports the first evidence of RBD acquisition from a mammalian host gene (SIRP) by an alpharetroviral-like Env, based on phylogenetic analyses and AlphaFold2 structural modeling
- **Visible evidence base** Text descriptions of results, figure and table references, supplementary file references, methodological descriptions
- **Missing materials affecting confidence** Figures, tables, supplementary files, sequence alignments, structural model coordinates, phylogenetic trees, and statistical support values are referenced but not provided; no accession numbers for most Env sequences are listed in the text

## Reviewer
- **Overall assessment** This manuscript addresses an interesting and potentially significant question in retroviral evolution, namely whether RBD domains have been exchanged between divergent Env lineages and whether host-derived RBDs have been captured. The central claims are plausible and the use of AlphaFold2 structural modeling is timely. However, the evidence as presented in the text alone is insufficient to fully evaluate the strength of the phylogenetic and structural conclusions. The manuscript would benefit from clearer presentation of the phylogenetic support, explicit documentation of the structural modeling quality metrics, and a more rigorous treatment of alternative evolutionary scenarios. The claim of a mammalian host origin for the SIRP-like RBD is intriguing but requires stronger sequence and phylogenetic evidence than is described here.
- **Who would be interested in the results, and why** Researchers studying retroviral evolution, endogenous retrovirus biology, envelope protein structure-function relationships, and mechanisms of host-virus genetic exchange. The findings on RBD transfer and host gene capture have implications for understanding viral diversification and the origins of viral receptor-binding domains, which would interest virologists and evolutionary biologists. The methodological approach using AlphaFold2 for comparative structural analysis of viral proteins may also appeal to structural biologists.
- **Major strengths** The manuscript addresses a novel and important question about the evolutionary mechanisms underlying Env diversification. The use of AlphaFold2 structural modeling to identify and classify RBD types across a broad set of retroviral Env sequences is innovative and appropriate. The identification of a potential host-derived RBD (SIRP-like) in an alpharetroviral-like Env is a striking finding that, if well-supported, would be of considerable interest. The discussion of functional implications, including a model for stepwise integration of acquired RBDs, is thoughtful and adds conceptual value.
- **Major Concerns** The major concerns are detailed below. The most critical issues are the lack of accessible evidence for the phylogenetic and structural claims, the limited description of how RBD transfer events were inferred, and the need for stronger support for the host-capture claim.
- **Minor Comments** Several minor issues are listed below, primarily related to clarity, terminology, and presentation.
- **Technical failings that need to be addressed before the case is established** R1-M1 (phylogenetic support), R1-M2 (structural modeling evidence), R1-M3 (host-capture claim), R1-M4 (alternative scenarios)
- **Assessment against Nature-style criteria** Originality: The question of intragene env recombination and host RBD capture is original and addresses a gap in the field. Scientific importance: If substantiated, the findings would significantly advance understanding of retroviral Env evolution and host-virus genetic exchange. Interdisciplinary readership: The topic is of interest to virologists, evolutionary biologists, and structural biologists, though the presentation is somewhat specialized. Technical soundness: The methods are appropriate in principle, but the evidence as presented is incomplete and requires additional detail and validation. Readability for nonspecialists: The manuscript is generally well-written but assumes substantial background knowledge in retroviral biology and structural modeling; some terms and concepts could be better explained for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core ideas are promising and potentially important, but the current manuscript does not provide sufficient accessible evidence to fully establish the claims. Substantial revision with additional data presentation and analysis is required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Phylogenetic support
- **Claim pointer** The manuscript claims that phylogenetic analyses of Env TM ectodomains reveal three major groups (Alpha-like, Main, EnvR) and that the distribution of RBD types indicates multiple RBD transfer events.
- **Evidence pointer** Figure 1, Table 1, Supplementary Table 1, Supplementary Files 2-5; location not provided
- **Concern** The phylogenetic analyses are described only in general terms. No details are given regarding the number of sequences analyzed, the alignment methodology, the model of sequence evolution selected, or the statistical support for the major clades. The text states that support values for branching within the Main and EnvR groups were "moderate to low," which raises concerns about the robustness of the inferred relationships and the subsequent inferences about RBD transfer. The claim of multiple RBD transfer events rests critically on the reliability of the phylogenetic tree, but the evidence for this is not presented in the text.
- **Why it matters** Without a clear and statistically supported phylogeny, the inference of RBD transfer events is not robust. If the tree topology is uncertain, alternative scenarios involving ancestral presence or loss of RBDs cannot be excluded. The manuscript's central thesis depends on the reliability of these phylogenetic inferences.
- **Resolution test** Provide the phylogenetic trees with clear clade support values (e.g., bootstrap, aBayes). Include details on the number of sequences, alignment methods, and model selection. Demonstrate that the key nodes supporting the inferred RBD transfer events are well-supported. Consider presenting alternative tree topologies or sensitivity analyses to show that the conclusions are robust to methodological choices.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural modeling evidence
- **Claim pointer** The manuscript claims that AlphaFold2 structural modeling identified distinct RBD classes (RBD-C, RBD-R1, RBD-R2) and a dual RBD configuration in EnvR group 4, and that these structural classifications support the inference of RBD transfer.
- **Evidence pointer** Figures 2-7, Supplementary Figures 1-9; location not provided
- **Concern** The structural modeling results are described qualitatively, but the actual models, their confidence metrics, and the criteria used to classify RBD types are not shown or described in sufficient detail. The text mentions pLDDT scores and PAE scores but does not provide specific values for the key models. The classification of RBD types appears to rely on visual inspection of models, but the reproducibility and objectivity of this classification are not established. The claim that the RBD-C of EnvR group 4 is "closely related" to that of Env-Pb(1) is based on structural similarity, but the quantitative basis for this claim is not given.
- **Why it matters** The structural classifications are central to the identification of RBD types and the inference of transfer events. If the models are of low confidence or the classification criteria are subjective, the conclusions may not be reliable. The reader cannot assess the validity of the structural claims without seeing the models and their quality metrics.
- **Resolution test** Provide representative structural models with pLDDT and PAE score plots for the key RBD and PD regions. Clearly define the structural criteria used to classify RBD types (e.g., fold, disulfide bonding pattern, strand topology). Provide quantitative measures of structural similarity (e.g., RMSD values for core regions) to support claims of relatedness. Discuss any regions of low model confidence and how they might affect the interpretations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Host-capture claim
- **Claim pointer** The manuscript claims that the SIRP-like RBD in alpharetroviral-like Env sequences was acquired from a mammalian host gene, representing the first documented case of RBD capture from a host by a retrovirus.
- **Evidence pointer** Figure 10, Supplementary Figure 8; location not provided
- **Concern** The evidence for a host origin of the SIRP-like RBD is based on structural similarity and sequence alignment to mammalian SIRP proteins. However, the sequence identity/similarity values are not reported, and the phylogenetic analysis supporting a close relationship between the viral RBD and host SIRP genes is not described in detail. The possibility of an alternative origin, such as acquisition from another virus or convergent evolution, is not thoroughly discussed. The claim of "first time" acquisition from a host gene is strong and requires robust evidence.
- **Why it matters** The host-capture claim is a headline finding of the manuscript. If not well-supported, it could be a major weakness. The evolutionary scenario of host gene capture has significant implications and requires strong sequence and phylogenetic evidence to be convincing.
- **Resolution test** Provide sequence identity/similarity statistics between the viral RBD and SIRP proteins. Present a phylogenetic analysis including the viral RBD sequences and a broad sampling of SIRP genes from mammals and other vertebrates, with clear support for the grouping of viral and host sequences. Discuss and rule out alternative scenarios, such as viral origin of the SIRP gene family or long-branch attraction artifacts. Provide evidence that the viral RBD is functional and under selection, if possible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Alternative evolutionary scenarios
- **Claim pointer** The manuscript proposes a specific sequence of RBD and PD insertion/deletion events in the EnvR supergroup and argues that the most parsimonious interpretation is that primordial Env lacked independently-folding RBDs.
- **Evidence pointer** Figure 9, Discussion; location not provided
- **Concern** The manuscript acknowledges that the TM-based phylogeny has low support for branching within the EnvR supergroup and that the sequence of events is not clear. The alternative scenario of ancestral presence of RBDs with subsequent loss is mentioned but not fully explored. The parsimony argument is reasonable but not quantitatively assessed. The possibility of horizontal gene transfer between retroviruses and hosts, or between different retroviral lineages, is discussed but the direction and timing of these events remain speculative.
- **Why it matters** The proposed evolutionary scenario is a key part of the manuscript's narrative. If alternative scenarios are not rigorously excluded, the conclusions about the sequence of events and the mechanisms of RBD transfer are weakened.
- **Resolution test** Perform a more detailed phylogenetic analysis of the EnvR supergroup using combined TM and core PD sequences, as described, and report the support for the key nodes. Use ancestral state reconstruction methods to formally test the presence or absence of RBDs at ancestral nodes. Discuss the implications of the low support for the proposed scenario and consider alternative explanations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Introduction, Results
- **Evidence pointer** location not provided
- **Issue** The term "gamma-like Env" is used throughout, but the definition of this category is not explicitly stated. The relationship between "gamma-like," "gamma-type," and "avian gamma-type" could be clarified for readers.
- **Required correction** Define "gamma-like Env" explicitly in the introduction, perhaps with reference to the defining structural or sequence features, and use terminology consistently throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Materials and Methods
- **Evidence pointer** location not provided
- **Issue** The methods for phylogenetic analysis are described briefly. Details on the alignment trimming, partitioning schemes, and model selection are not provided.
- **Required correction** Provide more detailed methods for the phylogenetic analyses, including software versions, alignment trimming parameters, model selection criteria, and how missing data were handled.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation of structural models
- **Affected element** Results, Figures
- **Evidence pointer** Figures 2, 5, 6, 7; location not provided
- **Issue** The figures are referenced but not available for review. The text descriptions of the structural models are helpful but would be enhanced by specific references to the figures.
- **Required correction** Ensure that the figures clearly show the structural features described in the text, such as the RBD-C and RBD-R folds, the PD expansion regions, and the dual RBD configuration. Add labels to the figures to guide the reader.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of functional implications
- **Affected element** Discussion
- **Evidence pointer** location not provided
- **Issue** The discussion of the functional implications of RBD transfer is interesting but somewhat speculative. The model presented in Figure 12 is not directly tested.
- **Required correction** Clearly distinguish between the evidence-based findings and the speculative model. Consider discussing how the model could be tested experimentally.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability section
- **Evidence pointer** location not provided
- **Issue** The data availability statement indicates that structural model coordinates are available upon request. For a manuscript of this type, it would be preferable to deposit the models in a public repository.
- **Required correction** Deposit the structural models in a public repository (e.g., ModelArchive) and provide accession numbers in the manuscript.

## Risk / unsupported claims
- The claim of "multiple RBD transfer events" is not fully supported by the accessible evidence, as the phylogenetic support for the key nodes is described as "moderate to low" and the trees are not shown.
- The claim of "first time" acquisition of an RBD from a mammalian host gene is not fully supported by the evidence presented in the text; sequence similarity statistics and detailed phylogenetic analyses are not provided.
- The inference that primordial Env lacked independently-folding RBDs is based on a parsimony argument that is not quantitatively assessed and is acknowledged to be uncertain due to low phylogenetic support.
- The functional model presented in Figure 12 is speculative and not directly tested.
- The classification of RBD types (RBD-C, RBD-R1, RBD-R2) and the identification of a dual RBD configuration rely on structural models whose quality and classification criteria are not fully described.