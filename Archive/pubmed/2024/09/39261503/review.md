## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors categorize the prokaryotic histone space into 17 distinct groups based on AlphaFold2 structure predictions, identify a major family termed "α3 histones" present in archaea and some bacteria, and establish the existence of DNA-bridging histones throughout archaea and in some bacteriophages, diverging from conventional nucleosomal histones
- **Visible evidence base** AlphaFold2 monomer and multimer predictions, CLANS sequence clustering, HMM profiles, one crystal structure of HTkC, DNA-bridging assays for HMfC, transcriptome and proteome data from public databases
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (Supplementary Figs. 1-36, Supplementary Tables 1-4) were not provided; source data files not provided; detailed sequence accession lists not provided

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive bioinformatic survey of prokaryotic histones, leveraging AlphaFold2 to expand the known diversity of these proteins. The identification of 17 distinct groups, including the α3 family and DNA-bridging histones, is a valuable contribution to the field. The experimental validation, including the crystal structure of HTkC and DNA-bridging assays for HMfC, strengthens the core claims. However, several concerns regarding classification criteria, the generalizability of the DNA-bridging conclusion, and the interpretation of transcriptome data need to be addressed. The manuscript is well-written and will be of interest to a broad readership in chromatin biology and microbial genomics.
- **Who would be interested in the results, and why** Chromatin biologists studying histone evolution and diversity; microbiologists interested in archaeal and bacterial genome organization; structural biologists using AlphaFold for protein classification; researchers studying the evolution of eukaryotic chromatin from prokaryotic ancestors
- **Major strengths** 1) Comprehensive and systematic classification of prokaryotic histones using state-of-the-art structure prediction; 2) Experimental validation of predicted structures through crystallography; 3) Functional demonstration of DNA bridging for a representative coiled-coil histone; 4) Clear identification of a major new family (α3 histones) with distinct structural features; 5) The work provides a valuable resource for the community
- **Major Concerns** See detailed items below
- **Minor Comments** See detailed items below
- **Technical failings that need to be addressed before the case is established** R1-M1 (classification criteria), R1-M2 (DNA-bridging generalizability), R1-M3 (transcriptome interpretation)
- **Assessment against Nature-style criteria** **Originality**: High. The systematic categorization of prokaryotic histones using AlphaFold2 is novel and goes beyond previous studies that focused on individual examples. **Scientific importance**: High. The identification of a major new histone family and the demonstration that DNA-bridging histones are widespread has implications for understanding chromatin evolution and the diversity of genome organization strategies. **Interdisciplinary readership**: Moderate to high. The work bridges structural biology, bioinformatics, and microbiology, and will appeal to researchers in these fields. **Technical soundness**: Generally sound, but with concerns about classification criteria and the strength of the DNA-bridging conclusion (see Major Concerns). **Readability for nonspecialists**: Good. The manuscript is clearly written, with helpful figures and explanations of key concepts. The use of terms like "α3 histones" is well-defined.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that they "categorize the prokaryotic histone space into 17 distinct groups based on AlphaFold2 predictions" and that these groups are defined by "similar quaternary structures" and "similar additional domains."
- **Evidence pointer** Results section "Identifying prokaryotic histones", Methods section "Histone classification", Supplementary Table 2
- **Concern** The criteria for grouping histones into the 17 categories are not fully transparent. The authors state that grouping was based on "similar quaternary structures" and "similar additional domains," but the specific thresholds or rules for these groupings are not clearly defined. For example, how much structural similarity is required for two histones to be in the same group? How were borderline cases handled? The statement that "Histones that are similar in sequence to the recently described bacterial histone Bd0055/HBb were classified into the group 'bacterial dimer histones' as they lack unique quaternary structures" suggests a somewhat ad hoc approach. Without clear, reproducible criteria, the classification may be difficult for others to apply or verify.
- **Why it matters** The 17-group classification is a central claim of the manuscript. If the criteria are not transparent and reproducible, the classification cannot be independently validated or extended by other researchers. This undermines the utility of the work as a resource.
- **Resolution test** The authors should provide a more detailed and quantitative description of the classification criteria, including specific thresholds for structural similarity (e.g., RMSD or TM-score cutoffs) and a decision tree or flowchart for how histones were assigned to groups. Ideally, the classification should be reproducible by an independent researcher using the provided criteria and data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "we established the existence of a large family of histones throughout archaea and in some bacteriophages that, instead of wrapping DNA, bridge DNA" and that "the predicted quaternary structures of four [groups] suggest potential DNA bridging capabilities."
- **Evidence pointer** Results section "DNA bridging histones", Figure 6, Supplementary Fig. 25
- **Concern** The claim that DNA bridging is a general property of the four identified groups (Methanococcales, coiled-coil, RgdC, and phage histones) is based primarily on structural predictions. Experimental evidence for DNA bridging is only provided for one representative, HMfC from the coiled-coil group. The authors do not experimentally test representatives from the other three groups. While the structural similarity to MJ1647 (a known bridging histone) is suggestive, it is not conclusive. Different groups may have different DNA-binding modes despite superficial structural similarities.
- **Why it matters** The existence of a "large family" of DNA-bridging histones is a major claim of the manuscript. If this claim is based only on structural prediction for most groups, it may be overstated. The title and abstract emphasize this finding, so it is important that the evidence is commensurate with the claim.
- **Resolution test** The authors should either (a) provide experimental evidence for DNA bridging for at least one representative from each of the four groups, or (b) temper the claim to reflect that DNA bridging is experimentally confirmed for the coiled-coil group and predicted for the others. Alternatively, they could provide a more detailed structural argument for why the predicted structures of the other groups are likely to bridge DNA, such as electrostatic surface analysis or comparison with known DNA-bridging proteins.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the FtF histone is essential to Leptospira interrogans serovar Lai, as attempts to delete the gene from its genome have failed" and cite this as evidence for the functional importance of FtF histones.
- **Evidence pointer** Results section "Face-to-face histones", reference 25
- **Concern** The claim that the FtF histone is essential is based on a single reference (reference 25) that is not described in detail. The authors do not provide any experimental data of their own to support this claim. Furthermore, the statement "attempts to delete the gene from its genome have failed" is ambiguous. It could mean that the gene is essential, or it could mean that the deletion was technically difficult for other reasons. Without more details about the experimental approach and the number of attempts, this claim is not well-supported.
- **Why it matters** The essentiality of the FtF histone in Leptospira is used to support the functional significance of this protein family. If this claim is not well-supported, it weakens the argument that FtF histones are important for bacterial physiology.
- **Resolution test** The authors should either provide more details about the experiments described in reference 25, or temper the claim to say that the FtF histone "may be essential" or "is suggested to be essential" based on the cited study. If possible, they could also perform their own genetic experiments to test essentiality.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2a
- **Evidence pointer** Results section "Identifying prokaryotic histones", Figure 2a
- **Issue** The CLANS plot in Figure 2a is described as showing the sequence space of prokaryotic histones, with clusters colored by category. However, it is not clear how the colors correspond to the categories listed in Supplementary Table 2. A legend or direct labeling of the clusters would improve readability.
- **Required correction** Add a legend to Figure 2a that maps colors to the histone categories, or label the clusters directly in the figure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3e
- **Evidence pointer** Results section "Face-to-face histones", Figure 3e
- **Issue** The proposed model for how FtF histones bind and wrap DNA is described in the text but the figure legend for Figure 3e is not provided in the manuscript text. It is unclear what the figure shows and how it supports the model.
- **Required correction** Provide a clear figure legend for Figure 3e that explains the model and the evidence supporting it.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Identifying and predicting histones"
- **Evidence pointer** Methods section "Identifying and predicting histones"
- **Issue** The methods state that "all bacterial, archaeal, and viral histone-fold proteins in InterPro (IPR009072) were retrieved." It is not specified how many sequences were retrieved, how many were excluded after structure prediction, and how many were ultimately classified into each of the 17 groups. This information would be useful for assessing the completeness and robustness of the analysis.
- **Required correction** Add a summary of the number of sequences at each stage of the analysis (retrieved, predicted, classified, and per group).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Accuracy
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors state that "the literature on prokaryotic histones is currently limited." This is somewhat inaccurate, as there is a substantial body of literature on archaeal histones and nucleosomes. The statement may be intended to refer to the diversity of histone families, but as written it is misleading.
- **Required correction** Rephrase to be more precise, e.g., "the literature on the diversity of prokaryotic histone families is currently limited."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Face-to-face histones"
- **Evidence pointer** Results section "Face-to-face histones"
- **Issue** The text states that "Residues R47, T49, and D54 form an RxTxxxxD motif which is also present in nucleosomal histones from archaea." It is not clear whether this motif is present in all archaeal nucleosomal histones or only some. The statement should be qualified.
- **Required correction** Clarify the statement, e.g., "which is also present in many archaeal nucleosomal histones."

## Risk / unsupported claims
- The claim that DNA-bridging is a general property of the four identified groups (Methanococcales, coiled-coil, RgdC, and phage histones) is not fully supported by experimental evidence, as only one representative (HMfC) was tested.
- The claim that the FtF histone is essential in Leptospira interrogans is based on a single reference and is not well-supported without more details.
- The classification of histones into 17 groups is not fully reproducible without more detailed criteria.
- The statement that "half of the 5823 histones have not been previously identified" is not verifiable without a clear definition of "previously identified" and a comparison to specific databases.
- The functional significance of the negatively charged tails in CC histones is speculative and not experimentally tested.