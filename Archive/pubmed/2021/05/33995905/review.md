## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, technical accuracy, completeness of the review, and alignment with stated aims
- **Shared manuscript claim summary** The authors present a review of integrative approaches combining sparse NMR and EPR constraints with molecular dynamics simulations to assess structural dynamics of transcription factors, with emphasis on intrinsically disordered TFs and TF-DNA interactions
- **Visible evidence base** Full text including introduction, four main sections, figures (5), references cited within text
- **Missing materials affecting confidence** Figure 1 and Figure 5 are described but not fully visible in the provided material; graphical abstract not accessible; full reference list not provided

## Reviewer
- **Overall assessment** This is a well-structured and readable review article that addresses a timely and relevant topic in structural biology. The authors successfully illustrate the complementary nature of NMR, EPR, and MD simulations for studying intrinsically disordered transcription factors. The manuscript is clearly written and logically organized, progressing from NMR-MD combinations to EPR-MD combinations and concluding with methodological considerations. The selection of examples is appropriate and representative of recent developments in the field. However, the review would benefit from a more critical and balanced discussion of limitations, particularly regarding force field accuracy, spin-label perturbations, and the quantitative rigor of ensemble validation. The methodological considerations section is useful but could be expanded with more practical guidance for newcomers to the field.

- **Who would be interested in the results, and why** Structural biologists, biophysicists, and computational chemists working on intrinsically disordered proteins, transcription factor dynamics, and integrative structural biology. Researchers interested in combining experimental restraints with molecular dynamics simulations would find the practical examples and methodological discussion valuable. The review is also accessible to graduate students and early-career researchers seeking an entry point into this interdisciplinary area.

- **Major strengths** The review provides a clear and concise overview of an emerging integrative approach. The use of specific examples, particularly the MAX:MAX system, effectively illustrates the power of combining sparse experimental restraints with MD simulations. The figures are informative and well-designed. The methodological considerations section addresses important practical issues such as system size limitations and spin-label selection. The writing is accessible to nonspecialists while maintaining technical accuracy.

- **Major Concerns** The review lacks a critical assessment of the quantitative agreement between experimental and computational data in the examples presented. The authors state that MD simulations "confirmed" or "validated" experimental observations, but the criteria for such validation are not discussed. The treatment of force field limitations and their impact on the reliability of simulated ensembles is superficial. The discussion of maximum entropy approaches is brief and does not address practical challenges in their implementation. The review would also benefit from a more explicit comparison of the information content and complementarity of NMR versus EPR restraints in the context of MD refinement.

- **Minor Comments** Some statements lack specific citations where they would be expected. The transition between sections could be smoother. The outlook section is somewhat generic and could be strengthened with more specific predictions about future developments. The figure captions are detailed but some figures are not fully visible in the provided material.

- **Technical failings that need to be addressed before the case is established** The review does not critically evaluate the accuracy of MD force fields for describing intrinsically disordered proteins, which is a known limitation. The criteria for assessing agreement between experimental and simulated data (e.g., in the MAX:MAX example) are not specified. The discussion of spin-label artifacts in EPR studies is insufficient given the known impact of MTSL on protein dynamics and structure.

- **Assessment against Nature-style criteria**  
  *Originality*: The review covers a niche but growing area; however, similar reviews exist on integrative NMR-MD approaches. The specific focus on transcription factors and the inclusion of EPR adds some originality.  
  *Scientific importance*: The topic is relevant to understanding transcription factor dynamics and DNA recognition, which has broad implications for gene regulation.  
  *Interdisciplinary readership*: The review bridges NMR, EPR, and computational methods, appealing to multiple communities.  
  *Technical soundness*: The technical content is generally accurate, but the lack of critical depth on limitations reduces the rigor.  
  *Readability for nonspecialists*: The writing is clear and accessible, with helpful figures and examples.

- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding critical assessment of limitations and validation criteria.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that MD simulations could "confirm" or "validate" experimental observations in several examples (e.g., MAX:MAX PRE data, Brinker folding, MAX:MAX EPR distance distributions).
- **Evidence pointer** Section 2, Figures 1, 3, 5; location not provided
- **Concern** The criteria for agreement between experimental and simulated data are not defined. The authors do not specify what level of agreement constitutes validation, nor do they discuss potential sources of discrepancy (e.g., force field inaccuracies, spin-label dynamics, ensemble averaging effects). This weakens the scientific rigor of the claims.
- **Why it matters** Without explicit validation criteria, readers cannot assess the reliability of the conclusions drawn from the integrative approach. This is particularly important for intrinsically disordered proteins, where force field accuracy is a known challenge.
- **Resolution test** The authors should add a paragraph in the methodological considerations section discussing quantitative metrics for comparing experimental and simulated data (e.g., reduced chi-square, ensemble overlap) and acknowledge the limitations of such comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "MD simulations of intrinsically disordered biomacromolecules often face the question, which fraction of the conformational space is represented by the computed trajectories" and suggest that cross-validation with experimental data can "ascertain the representativity of the computed ensemble."
- **Evidence pointer** Section 4, "MD and magnetic resonance" paragraph; location not provided
- **Concern** The discussion of ensemble representativity is superficial. The authors do not address known issues such as force field bias toward collapsed or extended states, the impact of simulation length on convergence, or the challenge of validating ensembles against sparse experimental data that may be consistent with multiple ensembles.
- **Why it matters** The central premise of the review is that integrative approaches can overcome limitations of individual methods. A more critical discussion of when and how this works in practice is essential for the review to be scientifically useful.
- **Resolution test** The authors should expand this section to include a discussion of ensemble validation methods (e.g., reweighting approaches, Bayesian inference) and acknowledge the degeneracy problem in ensemble determination from sparse data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "the combination of both methods allows for a description of biological macromolecules at a level of detail that would remain elusive to a single technique."
- **Evidence pointer** Introduction, final paragraph; location not provided
- **Concern** While this claim is plausible, the review does not provide a systematic comparison of what information each method uniquely contributes. The examples are illustrative but do not demonstrate a general framework for assessing the added value of integration versus standalone methods.
- **Why it matters** The review aims to advocate for integrative approaches. A more systematic analysis of the unique contributions of each method would strengthen this advocacy and help readers decide when integration is worthwhile.
- **Resolution test** The authors should include a summary table or figure comparing the information content, resolution, and limitations of NMR, EPR, and MD, and explicitly state what integration adds in each example.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2, "Combining NMR and MD simulations"
- **Evidence pointer** Section 2, first paragraph; location not provided
- **Issue** The transition from the general introduction of NMR-MD integration to the specific PRE-based example is abrupt. The reader is not prepared for the focus on PRE.
- **Required correction** Add a brief introductory sentence that outlines the structure of Section 2 and explains why PRE is highlighted as a key technique.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4, "Choosing the method"
- **Evidence pointer** Section 4, final paragraph; location not provided
- **Issue** The statement that NMR is suitable for proteins "less than (typically) 400-500 residues" is presented without discussion of recent advances in deuteration, TROSY, and 1H detection that have pushed size limits higher.
- **Required correction** Qualify this statement with a note that recent methodological advances are extending the size range, and cite relevant examples.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3, "Combining EPR and MD simulations"
- **Evidence pointer** Section 3, first paragraph; location not provided
- **Issue** The section on EPR-MD integration is shorter than the NMR section and does not discuss the use of EPR to study protein dynamics beyond distance measurements (e.g., site-directed spin labeling for mobility analysis).
- **Required correction** Add a brief discussion of complementary EPR techniques (e.g., relaxation enhancement, lineshape analysis) and their potential integration with MD.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 2
- **Evidence pointer** Figure 2 caption; location not provided
- **Issue** The figure caption mentions "NMR and EPR data" but the text in Section 2 focuses on NMR. The connection between the figure and the EPR discussion in Section 3 is not made explicit.
- **Required correction** Either add a cross-reference to Section 3 in the figure caption or clarify the figure's role in the NMR discussion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2, "Examples of the combination of NMR and MD Simulations"
- **Evidence pointer** Section 2, final paragraph; location not provided
- **Issue** The examples provided are described briefly, and the reader is not given enough detail to evaluate the quality of the integrative approach in each case.
- **Required correction** For at least one example, provide more detail on how the integration was performed (e.g., how restraints were applied, what validation was done).

## Risk / unsupported claims
- The claim that MD simulations "confirmed" experimental observations in the MAX:MAX example is not supported by quantitative criteria for agreement.
- The statement that "cross-validation versus experimental data can help to ascertain the representativity of the computed ensemble" is presented without discussion of the degeneracy problem or the limitations of sparse restraints.
- The claim that "the combination of both methods allows for a description of biological macromolecules at a level of detail that would remain elusive to a single technique" is plausible but not systematically demonstrated.
- The assertion that EPR is "not size limited" is an oversimplification; while EPR does not suffer from the same size limitations as NMR, sensitivity and labeling efficiency can still be challenging for large complexes.
- The statement that "NMR alone could not provide three-dimensional models of such dynamic systems in the absence of NOE constraints" is too absolute; other NMR parameters (e.g., RDCs, PREs, chemical shifts) can provide structural information in the absence of NOEs.