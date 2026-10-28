## Review setup
- **Input scope** Full manuscript text (Summary, Introduction, Results, Discussion, Resource Availability, STAR Methods, Acknowledgements) as provided by the author. No figures, tables, or supplementary materials were included in the supplied material.
- **Assessment boundary** Scientific content, methodological soundness, logical coherence, and alignment with stated claims. No assessment of formatting, grammar, or editorial style beyond readability for a general scientific audience.
- **Shared manuscript claim summary** The authors present a modular computational workflow that combines existing machine learning models for protein function prediction and MHC-II peptide presentation prediction to engineer human-derived proteins with reduced immunogenicity while maintaining or restoring therapeutic function. They demonstrate this workflow on transcriptional activation domains, RNA-binding domains, and zinc finger arrays, including generation of small-molecule-controllable transcription factors and deimmunized zinc finger arrays targeting therapeutically relevant genes UTRN and SCN1A.
- **Visible evidence base** Text descriptions of experimental results, including flow cytometry, RT-qPCR, RNA-seq, and computational predictions. Specific figures and tables are referenced but not provided. Supplementary tables (S1–S4) and figures (S1–S6) are mentioned but not included.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are absent. This includes primary data for flow cytometry, RT-qPCR, RNA-seq analyses, computational predictions, and sequence information. Without these, quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a timely and conceptually valuable framework for addressing immunogenicity in cell and gene therapies by combining computational predictions of protein function and MHC presentation. The modular design and emphasis on human-derived components are strengths. However, the evidence base as provided is insufficient to fully evaluate the central claims. Key quantitative results, such as the extent of deimmunization, the functional equivalence of engineered proteins, and the specificity of genome targeting, are described but not shown. The workflow's reliance on prediction algorithms with known limitations is acknowledged but not critically examined. The manuscript would benefit from clearer articulation of validation criteria and limitations. Overall, the concept is promising, but the current evidence does not fully establish the effectiveness and generalizability of the workflow.
- **Who would be interested in the results, and why** Researchers and developers in cell and gene therapy, protein engineering, immunology, and computational biology. The workflow addresses a critical bottleneck in translating engineered proteins to clinical use. Those working on CAR-T cells, gene editors, synthetic transcription factors, and therapeutic proteins would find the deimmunization strategy relevant. Computational biologists interested in applying machine learning to protein design would also be interested.
- **Major strengths** 1) The conceptual framework is clear and addresses a significant, underappreciated problem: immunogenicity arising from nonhuman peptides at junctions and mutations in humanized proteins. 2) The modular design allows for swapping of prediction algorithms, which is forward-looking given the rapid evolution of such tools. 3) The demonstration across multiple protein classes (activation domains, RNA-binding domains, DNA-binding domains) suggests generalizability. 4) The inclusion of small-molecule control and endogenous gene targeting adds practical relevance.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that deimmunized proteins retain function comparable to original versions, specifically for PUF-9R after optimization and for zinc finger arrays targeting UTRN and SCN1A.
  - **Evidence pointer** Figures 2f, 6d, 6e, 6f, 6g; location not provided
  - **Concern** The text states that deimmunized PUF-9R initially had reduced function but was restored to "comparable" levels after optimization, and that zinc finger arrays induced transcription of target genes. However, the actual data (fluorescence values, transcript levels, statistical comparisons) are not shown. The magnitude of functional restoration, the variability across replicates, and the statistical significance are not assessable.
  - **Why it matters** The central claim of the workflow is that deimmunization can be achieved without compromising function. Without quantitative evidence, this claim is unsupported. If functional loss is substantial or variable, the practical utility of the workflow is questionable.
  - **Resolution test** Provide the primary data for Figures 2f, 6d–g, including raw values, replicates, and statistical tests. Show that the deimmunized and optimized proteins achieve functional levels within a predefined acceptable range (e.g., not statistically significantly different from original, or exceeding a threshold of activity).
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that the deimmunized zinc finger arrays are "genome-orthogonal" and have minimal off-target effects, with the exception of ZNF35/IKZF1.
  - **Evidence pointer** Figure 3g, Figure S4; location not provided
  - **Concern** The RNA-seq analysis is described as showing "variable" results, with ZNF35/IKZF1 having "widespread off-target effects." The authors offer possible explanations (copy number, expression level) but do not provide data to distinguish between these. The claim of genome orthogonality for the other constructs is based on "modest" off-target effects, but the criteria for "modest" are not defined.
  - **Why it matters** Off-target effects are a critical safety concern for any genome-targeting therapeutic. If the workflow cannot reliably produce specific binders, its clinical relevance is diminished. The ambiguity in the data undermines confidence in the approach.
  - **Resolution test** Provide the full RNA-seq analysis, including differential expression lists, effect sizes, and statistical thresholds. Define a priori criteria for acceptable off-target effects. For ZNF35/IKZF1, provide data on copy number and expression to support or refute the proposed explanations.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological rigor
  - **Claim pointer** The authors state that the threshold for deimmunization corresponds to a false omission rate (FOR) of 0.001, and that this is "beyond adequate" because few proteins will contain close to 1000 nonhuman peptides.
  - **Evidence pointer** Methods, "MARIA threshold determination"; location not provided
  - **Concern** The FOR calculation relies on prevalence (fraction of peptides actually presented by MHC) assumed to be 1%. This is a critical parameter that is not justified. The statement that the threshold is "beyond adequate" is a logical argument, not a biological one. The number of nonhuman peptides in a protein is finite, but the risk is not simply the number of peptides; it is the probability that any one peptide is presented and immunogenic. A single highly presented peptide could be sufficient to elicit an immune response.
  - **Why it matters** The threshold determines which proteins are considered "deimmunized." If the threshold is too lenient, the workflow may produce proteins that are still immunogenic. If too stringent, it may unnecessarily restrict the design space.
  - **Resolution test** Justify the prevalence assumption with literature or data. Provide a sensitivity analysis showing how the number of accepted proteins changes with different prevalence values. Discuss the biological rationale for the threshold in terms of actual immunogenic risk, not just peptide count.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** The authors suggest the workflow is applicable to "any protein primarily sourced from human proteins with non-natural fusions or mutations."
  - **Evidence pointer** Discussion; location not provided
  - **Concern** The demonstration is limited to transcriptional activators, an RNA-binding domain, and zinc finger arrays. These are all nuclear or cytoplasmic proteins. The workflow's applicability to secreted proteins, membrane proteins, or proteins requiring complex post-translational modifications is not discussed. The immunogenicity of such proteins may involve different mechanisms (e.g., B cell responses, antibody-dependent effects) not captured by MHC-II presentation prediction alone.
  - **Why it matters** The stated scope of the workflow is broad, but the evidence is narrow. Overclaiming generalizability without demonstration or discussion of limitations could mislead potential users.
  - **Resolution test** Either provide additional examples from diverse protein classes or explicitly discuss the limitations and assumptions that would need to be addressed for broader applicability.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1f and Figure 6h
  - **Evidence pointer** location not provided
  - **Issue** The text mentions a "relatively weak effect of MHC-II allele on the prediction of peptide presentation" but does not explain what this means practically. Does it imply that deimmunization for one allele is likely to be effective for others?
  - **Required correction** Clarify the interpretation of this finding and its implications for patient-specific design.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, "Zinc finger binding specificity prediction"
  - **Evidence pointer** location not provided
  - **Issue** The method for determining binding specificity is described as taking "the nucleotide for each position with the maximum weight" from the position weight matrix. This is a simplification that may not reflect the true binding affinity or specificity, especially for positions with low information content.
  - **Required correction** Acknowledge this simplification and discuss its potential impact on the accuracy of target site prediction.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Discussion of limitations
  - **Evidence pointer** location not provided
  - **Issue** The Discussion does not explicitly address the limitations of the prediction algorithms used. For example, MARIA and NetMHCIIpan are known to have imperfect accuracy, and the choice of threshold is arbitrary to some extent.
  - **Required correction** Add a paragraph discussing the known limitations of the computational tools and how they might affect the conclusions.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** RT-qPCR analysis
  - **Evidence pointer** Methods, "RT-qPCR data analysis"
  - **Issue** The method for calculating the ratio of gene of interest to TBP is described, but the statistical test used is not specified in the text (though it is mentioned as a Welch's t-test). It is unclear if the data were tested for normality or if a non-parametric test was considered.
  - **Required correction** Specify the statistical test used and any assumptions checked.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The central claims of functional retention and genome specificity cannot be evaluated without the primary data. R1-M3, while not blocking, is important for establishing the validity of the deimmunization threshold.
- **Assessment against Nature-style criteria**  
  *Originality*: The concept of combining function prediction and immunogenicity prediction in a modular workflow is novel and timely. The specific application to human-derived domains with junction deimmunization is a creative contribution.  
  *Scientific importance*: The problem of immunogenicity in cell and gene therapy is of high importance. A reliable computational workflow to address it would be a significant advance. The potential impact is high if the claims are substantiated.  
  *Interdisciplinary readership*: The work bridges computational biology, immunology, and therapeutic development. It should be of interest to a broad audience, but the current presentation may be too technical for non-specialists in computational methods.  
  *Technical soundness*: The computational approach is reasonable, but the validation is incomplete. The lack of primary data and the acknowledged variability in off-target effects are concerns. The reliance on prediction algorithms without critical discussion of their limitations is a weakness.  
  *Readability for nonspecialists*: The Introduction and Discussion are generally clear. The Results section is dense and assumes familiarity with the specific tools and methods. A brief explanation of key concepts (e.g., MHC presentation, false omission rate) would improve accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework is valuable and the demonstrations, if validated by the missing data, would constitute a useful contribution. However, the current evidence is insufficient to establish the central claims. The authors should be encouraged to provide the primary data and address the methodological concerns.

## Risk / unsupported claims
- The claim that deimmunized proteins retain function comparable to original versions is unsupported without primary data (Figures 2f, 6d–g).
- The claim of genome orthogonality for the zinc finger arrays is weakly supported due to the acknowledged off-target effects and lack of detailed analysis (Figure 3g, S4).
- The claim that the FOR threshold of 0.001 is "beyond adequate" is a logical assertion, not a biologically validated one.
- The generalizability of the workflow to all protein types is overclaimed given the limited demonstration.
- The statement that "no patient-specific engineering" would be required for most alleles is speculative and based on a limited analysis (Figure 6h).