## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends (where provided).
- **Assessment boundary** The scientific claims, experimental design, data interpretation, and technical soundness of the presented work. This review does not assess the decision to post on a preprint server.
- **Shared manuscript claim summary** The authors claim that the Intervening domain (I domain) of plant MADS transcription factors is an essential component of the DNA-binding module, required for DNA binding in both type I and type II lineages, and that it contributes to DNA-binding specificity, dimerization specificity, and functional identity in planta.
- **Visible evidence base** The manuscript provides structural data (X-ray crystallography of SEP3 MI), biochemical data (pull-down assays, EMSA), genome-wide binding data (seq-DAP-seq), yeast two-hybrid interaction data, and in planta complementation studies.
- **Missing materials affecting confidence** The manuscript is a preprint and lacks several key items that would be present in a final published version. These include: (1) final figure files with all panels and detailed legends, (2) supplementary figures and tables referenced in the text (e.g., Supplementary Figures 1-8, Supplementary Tables 1-2), (3) a clear statement of data and code availability, (4) detailed statistical analysis and reproducibility information for the seq-DAP-seq and ChIP-seq comparisons, and (5) a final, copy-edited version of the text. The absence of these materials limits the depth of the technical review.

## Reviewer
- **Overall assessment** This manuscript addresses a long-standing question in plant transcription factor biology: how MADS domain proteins with highly conserved DNA-binding domains achieve functional specificity. The authors provide a compelling and multi-faceted dataset, including a novel crystal structure of the SEP3 MI domain, demonstrating that the I domain is structurally integral to the MADS domain and is absolutely required for DNA binding. The functional experiments, particularly the domain-swap complementation in the ap1 mutant, are elegant and provide strong evidence for the I domain's role in determining functional identity. The study is technically sound in its core components and the conclusions are largely supported by the data presented. However, the manuscript would be significantly strengthened by addressing several concerns related to the interpretation of the structural data, the quantitative analysis of the genomic data, and the generalizability of the findings to the broader MADS TF family.
- **Who would be interested in the results, and why** This work will be of high interest to plant developmental biologists, particularly those studying flower development and the ABCE model. It is also highly relevant to the broader transcription factor community, including researchers studying MADS-box proteins in other eukaryotes, and those interested in the structural basis of protein-DNA recognition and specificity. The findings have implications for understanding how highly conserved DNA-binding domains can evolve new functions, a topic of interest to evolutionary and systems biologists.
- **Major strengths**
    1.  The study provides a novel, high-resolution crystal structure of a plant MADS-box protein (SEP3 MI), which is a significant contribution to the field. The structural analysis clearly shows the I domain forming an alpha-helix that packs against the MADS-box core, providing a mechanistic basis for its role in stabilization.
    2.  The combination of structural, biochemical, and in vivo data is powerful. The demonstration that the I domain is required for DNA binding in both type I and type II MADS TFs is a clear and important finding.
    3.  The in planta domain-swap experiments are particularly elegant. The finding that replacing the I domain of AG with that of AP1 confers significant AP1-like function is a strong and direct demonstration of the I domain's role in determining functional identity.
    4.  The use of seq-DAP-seq to show that the I domain alters genome-wide binding specificity and preferred intersite spacing provides a mechanistic link between the I domain and target gene selection.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness and interpretation of structural data
    - **Claim pointer** The authors state that the I domain acts to stabilize the M domain and that the structure shows a "highly conserved MADS-box fold with the I domain forming an alpha helix and acting to stabilize the M domain."
    - **Evidence pointer** Results section "Structure of the SEP3ALLATA3 MI domain", Figure 1
    - **Concern** The structural analysis is based on the apo-form of the SEP3 MI domain. The claim that the I domain "stabilizes" the M domain is inferred from the structure and from the observation that the M domain alone is unstable or unable to bind DNA. However, without a structure of the M domain alone or a structure of the MI domain in complex with DNA, the precise mechanism of stabilization (e.g., entropic, enthalpic, or via induced fit) remains speculative. The authors should temper their language or provide additional biophysical data (e.g., circular dichroism, size-exclusion chromatography with multi-angle light scattering) to directly compare the stability of the M domain versus the MI domain.
    - **Why it matters** The central claim of the paper is that the I domain is a required part of the DNA-binding domain. While the functional data strongly support this, the structural mechanism is presented as a key piece of evidence. Over-interpreting the structural data could weaken the overall argument.
    - **Resolution test** Provide direct biophysical evidence of differential stability between the M and MI domains, or rephrase the claim to be more descriptive of the structural observations (e.g., "the I domain forms an integral part of the folded domain, packing against the MADS-box core") rather than mechanistic.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness and data analysis of genomic data
    - **Claim pointer** The authors claim that the I domain alters DNA-binding specificity based on seq-DAP-seq experiments, showing "unique binding sites for each complex, changes in preferred site spacing and a loss of carpel and fourth whorl-specific targets for the chimeric protein."
    - **Evidence pointer** Results section "Impact of the I domain on DNA-binding specificity and intersite spacing", Figure 4
    - **Concern** The analysis of the seq-DAP-seq data is described, but the manuscript lacks a clear description of the statistical framework used to define "differential binding" between SEP3-AG and SEP3-AG IAP1. The authors state that peaks with a "two-fold difference in binding intensity" were considered, but it is unclear if this is a simple ratio or if a statistical test (e.g., DESeq2, edgeR) was applied to the count data. Furthermore, the comparison to ChIP-seq data is described as a "weak positive correlation," but the correlation coefficient and its significance are not reported. The lack of quantitative rigor in this section makes it difficult to assess the strength of the claim that the I domain changes binding specificity.
    - **Why it matters** The genome-wide binding data is a key piece of evidence linking the I domain to target gene selection. If the analysis is not statistically robust, the conclusion that the I domain alters binding specificity is weakened.
    - **Resolution test** Provide a detailed description of the statistical methods used to identify differentially bound peaks, including the model and thresholds. Report the correlation coefficient and p-value for the ChIP-seq comparison. Consider using a more standard differential binding analysis pipeline.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Generalizability and scope of claims
    - **Claim pointer** The authors conclude that "the I domain acts both as an integral part of the DNA-binding domain and strongly contributes to the functional identity of the MADS TF." They also state that "sequences fulfilling the same function as the SEP3 I domain can be found in both lineages of plant MADS TFs, suggesting the I domain is a conserved and required part of the DNA-binding domain."
    - **Evidence pointer** Abstract, Discussion
    - **Concern** The functional in planta data is based on a single pair of proteins (AG and AP1) and a single mutant background (ap1). While the biochemical data includes type I MADS TFs, the in planta experiments are limited to type II floral organ identity MADS TFs. The claim that the I domain is a "conserved and required part of the DNA-binding domain" for all plant MADS TFs is a significant extrapolation from the data presented. The authors should either provide additional evidence from other MADS TF subfamilies or temper their conclusions to be more specific to the proteins tested.
    - **Why it matters** The title and abstract make a broad claim about the I domain's role in all plant MADS TFs. If the data only supports this for a subset, the manuscript overstates its findings.
    - **Resolution test** Add a caveat to the discussion about the generalizability of the findings, or provide additional data (e.g., complementation of a different MADS TF mutant with a chimeric protein) to support the broader claim.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and presentation
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract, Introduction
    - **Issue** The abstract and introduction are dense and may be difficult for a non-specialist to follow. The distinction between type I and type II MADS TFs, and the significance of the I domain, could be explained more clearly.
    - **Required correction** Consider revising the abstract to more clearly state the problem and the key finding. In the introduction, provide a brief, clear explanation of the MIKC structure and the functional significance of the different domains.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Figure 4
    - **Evidence pointer** Results section "Impact of the I domain on DNA-binding specificity and intersite spacing", Figure 4
    - **Issue** The panels in Figure 4 are complex and the figure legend is not fully self-explanatory. The description of the KSM analysis and the meaning of the "AUC" values could be clearer.
    - **Required correction** Expand the figure legend to explain each panel in detail. Consider simplifying the figure or moving some of the more complex analyses to a supplementary figure.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical detail
    - **Affected element** Methods section "Yeast two-hybrid screening"
    - **Evidence pointer** Methods section "Yeast two-hybrid screening"
    - **Issue** The methods for the yeast two-hybrid screen are described, but the criteria for a "positive interaction" are not fully quantitative. The authors state that interactions were scored based on growth on three selective media, but it is unclear if this was a binary yes/no or if there was a quantitative measure of growth.
    - **Required correction** Provide more detail on how growth was scored. Was it a visual inspection or was there a quantitative assay (e.g., beta-galactosidase activity)?
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Clarity and presentation
    - **Affected element** Discussion
    - **Evidence pointer** Discussion
    - **Issue** The discussion is somewhat speculative in places, particularly regarding the role of the I domain in recruiting ternary factors. While this is an interesting hypothesis, it is not directly tested in this manuscript.
    - **Required correction** Clearly distinguish between conclusions that are directly supported by the data and those that are speculative hypotheses. Consider moving some of the more speculative points to a "Future Directions" section.
- **Technical failings that need to be addressed before the case is established**
    - The statistical analysis of the seq-DAP-seq data needs to be more rigorous and clearly described (R1-M2).
    - The structural interpretation of the I domain's role in stabilization should be supported by direct biophysical data or rephrased to be more descriptive (R1-M1).
- **Assessment against Nature-style criteria**
    - **Originality** High. The study provides a novel structure of a plant MADS TF and a new functional role for the I domain, which was previously considered primarily a dimerization determinant. The finding that the I domain is part of the DNA-binding module is a significant conceptual advance.
    - **Scientific importance** High. The work addresses a fundamental question in developmental biology: how transcription factors with highly conserved DNA-binding domains achieve functional specificity. The findings have broad implications for understanding the evolution of gene regulatory networks.
    - **Interdisciplinary readership** Moderate. The work will be of great interest to plant biologists and structural biologists. The broader transcription factor community will also find it relevant. However, the heavy focus on plant development may limit its appeal to a wider audience.
    - **Technical soundness** Good, but with caveats. The structural and biochemical experiments are well-executed. The genomic and in planta experiments are compelling but require more rigorous quantitative analysis to fully support the claims.
    - **Readability for nonspecialists** Fair. The manuscript is well-written but is dense and assumes a high level of background knowledge in plant development and MADS-box biology. The abstract could be more accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are novel and important, and the data largely support the main conclusions. However, the manuscript would be significantly strengthened by addressing the concerns related to the quantitative analysis of the genomic data and the interpretation of the structural data. The authors should also consider tempering the broad claims about the I domain's role in all plant MADS TFs.

## Risk / unsupported claims
- The claim that the I domain is a "conserved and required part of the DNA-binding domain" for all plant MADS TFs is an extrapolation from the data, which only directly tests a small number of type I and type II proteins.
- The claim that the I domain "acts to stabilize the M domain" is inferred from the structure and functional data but is not directly demonstrated by biophysical measurements.
- The statement that the I domain's effect on DNA-binding specificity is due to "allosteric contributions" is a hypothesis that is not directly tested.
- The correlation between in vitro seq-DAP-seq binding and in vivo ChIP-seq data is described as "weak" but the statistical significance of this correlation is not reported, making it difficult to assess the strength of this claim.