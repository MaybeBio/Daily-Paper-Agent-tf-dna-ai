## Review setup
- **Input scope** Full manuscript text, including figures and figure legends, graphical abstract, and references.
- **Assessment boundary** The review assesses the manuscript as a review article, focusing on the accuracy, completeness, and critical synthesis of the presented computational and experimental evidence on RfaH fold-switching, and the validity of the broader claims about metamorphic proteins.
- **Shared manuscript claim summary** The manuscript argues that the fold-switching protein RfaH is a paradigm for understanding metamorphic proteins. It synthesizes computational (MD simulations, coevolutionary analysis, AlphaFold2 predictions) and experimental (NMR, HDXMS, biochemistry) evidence to propose a mechanistic model of RfaH's α-helix to β-barrel transition, and it argues that such metamorphic behavior may be more common in the NusG protein family and beyond than previously appreciated.
- **Visible evidence base** The manuscript cites a substantial body of published literature, including the authors' own prior experimental and computational studies on RfaH. It presents new computational analyses (e.g., ColabFold predictions for E. coli and V. cholerae RfaH) and summarizes findings from published MD simulations and experimental studies.
- **Missing materials affecting confidence** The manuscript is a review and does not present new experimental data. The primary evidence for the proposed refolding pathway and the role of specific residues (e.g., F130) is derived from previously published studies, which are cited but not fully detailed. The new ColabFold predictions are presented as a figure but without detailed methodological parameters or a systematic comparison across a larger set of homologs, limiting the strength of the claim about AlphaFold2's predictive utility.

## Reviewer
- **Overall assessment** This is a well-written, authoritative, and timely review of the metamorphic protein RfaH, a fascinating example of a single sequence encoding two stable folds. The authors are leading experts in the field, and their synthesis of computational and experimental data is insightful. The review provides a valuable framework for understanding the molecular determinants of fold-switching and offers a compelling perspective on the potential prevalence of metamorphic proteins. The inclusion of new ColabFold predictions is a nice addition, but the claims about the general utility of AlphaFold2 for predicting metamorphic behavior are somewhat overstated given the limited number of examples tested. The review would be strengthened by a more critical discussion of the limitations and potential artifacts of the various computational methods employed.
- **Who would be interested in the results, and why** This review will be of great interest to researchers in the fields of protein folding, protein evolution, structural biology, and biophysics. It is also relevant to those studying transcription regulation and bacterial pathogenesis. The clear explanation of computational methods and their application to a biologically important system makes it accessible to a broad audience, including computational biologists looking for benchmark systems and experimentalists seeking to understand the dynamic behavior of their proteins of interest.
- **Major strengths**
    1.  Authoritative and comprehensive synthesis of a complex and emerging field by leading researchers.
    2.  Clear and logical structure, guiding the reader from the general concept of metamorphic proteins to the specific case of RfaH and its broader implications.
    3.  Excellent integration of computational predictions and experimental validations, providing a strong model for how to study such systems.
    4.  The inclusion of new ColabFold predictions for E. coli and V. cholerae RfaH adds a novel element and demonstrates a practical application of modern AI-based tools.
    5.  The perspective on the potential prevalence of metamorphic proteins in the NusG family and the discussion of their evolutionary and functional significance are thought-provoking and will stimulate future research.
- **Major Concerns**
    - **R1-M1** (Severity: Major, Blocking: No, Axis: Overstatement of claims)
        - **Claim pointer** The manuscript states that AlphaFold2 "correctly predicts the metamorphic state" for E. coli and V. cholerae RfaH and implies this is a general strategy for identifying metamorphic proteins.
        - **Evidence pointer** Section "Metamorphic proteins may be common in the NusG family", Figure 4.
        - **Concern** The claim that AlphaFold2 can predict metamorphic behavior is based on only two examples (E. coli and V. cholerae RfaH). This is a very small sample size from which to draw a general conclusion. The authors also note that a homolog with lower sequence identity (LoaP) was not successfully predicted, which further complicates the narrative. The success of AlphaFold2 here may be due to the specific properties of RfaH (e.g., the domain boundary falling neatly at the sequence provided) and may not be generalizable.
        - **Why it matters** Overstating the predictive power of AlphaFold2 for this purpose could mislead other researchers into thinking it is a simple, reliable tool for identifying novel metamorphic proteins, when in reality it may require significant domain knowledge and manual intervention to work.
        - **Resolution test** The authors should temper their conclusion, explicitly stating that this is a proof-of-concept on a small number of cases and that the failure on LoaP highlights the current limitations. They should also discuss what specific features of RfaH might make it amenable to this approach.
    - **R1-M2** (Severity: Major, Blocking: No, Axis: Incomplete critical assessment of computational methods)
        - **Claim pointer** The manuscript summarizes results from various MD simulations (REMD, MSM, AWSBM, etc.) and presents a consensus model of the refolding pathway.
        - **Evidence pointer** Sections "Watching RfaH-KOW refold in silico" and "RfaH-KOW refolding in the context of the full-length protein", Figure 3.
        - **Concern** While the authors describe the different methods, they do not critically compare their strengths and weaknesses. For example, the potential artifacts of implicit solvent models (which are used in most of the simulations) are mentioned, but the implications of these artifacts for the specific conclusions about the refolding pathway are not deeply discussed. The discrepancies between the different simulations (e.g., the order of α-helix unfolding) are noted but not thoroughly analyzed. A more critical evaluation of the robustness of the consensus model would be valuable.
        - **Why it matters** A review should not just catalog results but also critically evaluate the evidence. Without a deeper discussion of the limitations of each method, the reader cannot assess the confidence level of the proposed model.
        - **Resolution test** The authors should add a paragraph or table that explicitly compares the methods, their key parameters, and their main limitations. They should also discuss whether the discrepancies between simulations are due to methodological differences or to the inherent stochasticity of the process.
    - **R1-M3** (Severity: Major, Blocking: No, Axis: Speculative generalization)
        - **Claim pointer** The manuscript speculates that "up to 4% of known proteins may switch folds" and that metamorphic behavior may be common in the NusG family.
        - **Evidence pointer** Sections "Signatures of metamorphic behavior" and "Metamorphic proteins may be common in the NusG family".
        - **Concern** The 4% figure is from a single bioinformatics study (Porter and Looger) and is based on indirect evidence (secondary structure prediction discrepancies). The authors present this as a plausible estimate but do not critically discuss the assumptions and potential false-positive rate of this approach. Similarly, the claim that many NusGSP may be metamorphic is based on a bioinformatics screen that has only been partially validated experimentally.
        - **Why it matters** These are important and exciting claims, but they are also speculative. Presenting them without a clear caveat about the indirect nature of the evidence could lead to an overestimation of the prevalence of metamorphic proteins.
        - **Resolution test** The authors should more clearly distinguish between direct experimental evidence and indirect computational predictions. They should explicitly state that the 4% figure is an upper-bound estimate that requires experimental validation and discuss the limitations of the bioinformatics approach used to generate it.
- **Minor Comments**
    - **R1-m1** (Severity: Minor, Axis: Clarity)
        - **Affected element** Figure 2 legend.
        - **Evidence pointer** Figure 2.
        - **Issue** The legend states "which range from potent antitermination (in rRNA operons) to efficient termination (in xenogeneic and antisense RNAs." This sentence is missing a closing parenthesis.
        - **Required correction** Add the missing closing parenthesis after "RNAs".
    - **R1-m2** (Severity: Minor, Axis: Terminology)
        - **Affected element** Section "Watching RfaH-KOW refold in silico".
        - **Evidence pointer** Section "Watching RfaH-KOW refold in silico".
        - **Issue** The term "Gō models" is used, which is correct, but the authors may want to define the term "structure-based models (SBMs)" more explicitly for a general audience, as it is a key concept.
        - **Required correction** Briefly define SBMs in a way that is accessible to non-experts, e.g., "models where the energy landscape is biased towards a known native structure."
    - **R1-m3** (Severity: Minor, Axis: Completeness)
        - **Affected element** Section "Experimental observation of the structural dynamics of RfaH".
        - **Evidence pointer** Section "Experimental observation of the structural dynamics of RfaH".
        - **Issue** The section on HDXMS is detailed, but it would be helpful to mention other experimental techniques that have been used to study RfaH dynamics, such as single-molecule FRET, if they exist, to provide a more complete picture.
        - **Required correction** Add a sentence mentioning other complementary techniques, or explicitly state that HDXMS is the primary technique used to date for this purpose.
    - **R1-m4** (Severity: Minor, Axis: Clarity)
        - **Affected element** Section "Metamorphic proteins may be common in the NusG family".
        - **Evidence pointer** Section "Metamorphic proteins may be common in the NusG family".
        - **Issue** The phrase "on-demand transformers" is a bit colloquial. While catchy, it may be better to use a more formal term like "condition-dependent conformational switches" for a scientific review.
        - **Required correction** Consider replacing "on-demand transformers" with a more formal phrase.

## Risk / unsupported claims
- The claim that "up to 4% of known proteins may switch folds" is based on a single computational study and is presented without sufficient critical discussion of the method's limitations. This should be clearly framed as a speculative estimate.
- The claim that AlphaFold2 can be used to "explore hypothetical metamorphic behavior" is based on a very small number of examples (two successful, one failed). This is a proof-of-concept, not a validated general method.
- The speculation that "metamorphism could be an ancient phenomenon" is interesting but is not supported by direct evidence and should be presented as a hypothesis.
- The statement that "the (presumed) pervasiveness of metamorphic proteins among extant NusG homologs suggests that the NusG ancestor was metamorphic" is a logical inference but is based on the same unvalidated bioinformatics predictions.