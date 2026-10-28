## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, supplemental figure legends referenced but not provided)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. Figures and tables are referenced but not directly viewable; assessment relies on textual descriptions.
- **Shared manuscript claim summary** The authors report that two transcription factors, ERα and Sox2, exhibit multiphasic (bi- or tri-phasic) association and dissociation kinetics when binding to both DNA and RNA, as measured by fluorescence polarization and surface plasmon resonance. They propose that Sox2 kinetics are explained by sequential monomer binding, while ERα kinetics require a novel model involving complex isomerization and product feedback.
- **Visible evidence base** Text descriptions of FP-based equilibrium binding, competitive dissociation, jump dilution, association experiments, SPR experiments, and simulation results. Figures 1–7 and Supplemental Figures S1–S6 are referenced but not directly inspectable.
- **Missing materials affecting confidence** Actual figures and tables (data points, fits, error bars), supplemental methods details, raw kinetic traces, simulation code outputs, and detailed statistical analyses. Without these, quantitative claims cannot be fully verified.

## Reviewer
- **Overall assessment** This manuscript presents a systematic biophysical characterization of nucleic acid binding kinetics for two important transcription factors. The observation of multiphasic kinetics is potentially significant, and the authors are appropriately cautious in their interpretation. However, the central claim of a "novel" mechanism for ERα rests on simulations that are described but not fully validated against alternative models, and the manuscript would benefit from clearer presentation of model selection criteria. The work is technically sound in its core measurements but the conceptual advance is incremental rather than transformative.
- **Who would be interested in the results, and why** Researchers studying transcription factor–nucleic acid interactions, particularly those interested in RNA-mediated regulation of gene expression. The kinetic framework and the proposed models for multiphasic binding could inform studies of other TFs and nucleic acid binding proteins. The work may also interest biophysicists studying protein–nucleic acid interaction mechanisms.
- **Major strengths** 1) Systematic application of multiple complementary biophysical methods (FP, SPR, jump dilution) to characterize both association and dissociation kinetics. 2) Careful control experiments, including testing for direct transfer and ruling out protein construct artifacts. 3) The authors explicitly test and reject several conventional models before proposing their framework. 4) The work addresses an important and understudied question: whether RNA and DNA binding by TFs occur via similar or different mechanisms.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data interpretation / model validation
  - **Claim pointer** The claim that ERα binding requires a novel mechanism involving complex isomerization and product feedback (Abstract, Discussion).
  - **Evidence pointer** Figure 7C, Supplemental Figures S5 and S6, Discussion section
  - **Concern** The proposed model for ERα (Figure 7C) is presented as the best explanation for the observed triphasic association kinetics, but the manuscript does not provide a systematic comparison of this model against all plausible alternatives. The authors state that "none of which adequately explained all the ERα nucleic acid–binding data" for conventional models, but the criteria for "adequately" are not quantified. The simulations shown in Supplemental Figures S5 and S6 are described as recapitulating "general kinetic trends," which is a weak standard for model validation.
  - **Why it matters** The central novelty of the paper rests on this proposed mechanism. If the model is not uniquely constrained by the data, or if simpler models could also reproduce the kinetics, the claim of a "novel reaction mechanism" is overstated. The manuscript needs to demonstrate that the proposed model is both necessary and sufficient.
  - **Resolution test** Provide quantitative model comparison (e.g., AIC or BIC scores) for the proposed model versus all considered alternatives, using the same datasets. Show that the proposed model fits significantly better and that its parameters are identifiable from the data.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Quantitative rigor / data presentation
  - **Claim pointer** The claim that kon and koff values differ between DNA and RNA for ERα and Sox2 (Abstract, Results).
  - **Evidence pointer** Table 1, Figures 2, 4, 6
  - **Concern** The manuscript reports rate constants but does not provide confidence intervals or statistical comparisons between DNA and RNA conditions. Given the complexity of the kinetic traces and the need for multi-exponential fitting, it is unclear whether the reported differences are statistically significant. The text states "similar rate constants for all the nucleic acids tested" for ERα dissociation, but the basis for this similarity claim is not quantified.
  - **Why it matters** The comparison between DNA and RNA binding is a key aspect of the paper's message. Without proper statistical treatment, readers cannot assess whether the observed similarities or differences are meaningful.
  - **Resolution test** Provide confidence intervals for all reported rate constants, and perform appropriate statistical tests (e.g., extra sum-of-squares F test) to compare models and conditions.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Experimental design / controls
  - **Claim pointer** The claim that the observed multiphasic kinetics are intrinsic to the protein–nucleic acid interaction and not artifacts of the experimental system (Results, Discussion).
  - **Evidence pointer** Figures 2–6, Supplemental Figures S2–S3
  - **Concern** The authors rule out direct transfer and the extended basic region in ERα as causes of biphasic dissociation, but other potential sources of multiphasic behavior are not fully addressed. These include: (1) heterogeneous protein preparations (e.g., partial oxidation, aggregation, or post-translational modifications), (2) nucleic acid heterogeneity (e.g., alternative conformations of the RNA), (3) surface artifacts in SPR (e.g., avidity effects, mass transport), and (4) fluorophore effects in FP. The authors mention checking protein purity by SDS-PAGE and size-exclusion chromatography, but do not describe tests for nucleic acid heterogeneity or fluorophore effects.
  - **Why it matters** Multiphasic kinetics can arise from experimental artifacts. If the authors cannot exclude these possibilities, the biological interpretation of the multiphasic behavior is weakened.
  - **Resolution test** Include control experiments such as: (1) testing multiple independent protein preparations, (2) testing RNA with different fluorophore positions or labels, (3) varying SPR surface density to test for avidity effects, and (4) characterizing nucleic acid conformational homogeneity (e.g., by native gel electrophoresis under binding conditions).
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity / presentation
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract states "multiphasic nucleic acid–binding kinetics" without specifying the number of phases or the conditions under which they are observed. This is vague for a general audience.
  - **Required correction** Specify the number of phases observed (e.g., "biphasic dissociation and triphasic association") and note the concentration ranges where multiphasic behavior is evident.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility / methods detail
  - **Affected element** Materials and Methods, FP-based Kdapp and association rate determination
  - **Evidence pointer** Materials and Methods section
  - **Issue** The description of the FP-based association experiments is brief. It is unclear how the "initial association rate constants" were extracted from the data, particularly for the triphasic traces. The smoothing spline approach is mentioned but not described in sufficient detail for reproduction.
  - **Required correction** Provide more detail on the data processing pipeline, including the smoothing spline parameters, how initial slopes were determined, and how the linear regression was performed.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation / framing
  - **Affected element** Discussion, paragraph on ERα model
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of the ERα model's biological implications is speculative and not well connected to existing literature on ERα function. The relevance of the proposed feedback mechanism to ERα biology is unclear.
  - **Required correction** Either strengthen the connection to known ERα biology (e.g., dimerization dynamics, chromatin scanning) or explicitly state that the biological relevance remains to be determined.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Table 1
  - **Evidence pointer** Table 1
  - **Issue** The table reports Kdapp, konapp, and koffapp values but does not include the number of replicates or the error type (SD, SEM, 50% range as stated in text). The text mentions "50% range" but this is unusual and not defined.
  - **Required correction** Define the error metric clearly and report the number of independent experiments for each measurement.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Introduction
  - **Evidence pointer** Introduction section
  - **Issue** The introduction cites several studies on TF–RNA interactions but does not discuss prior kinetic studies of TF–DNA binding in detail. The claim that multiphasic kinetics are "previously unappreciated" should be better contextualized with respect to known examples of complex binding kinetics in other DNA-binding proteins.
  - **Required correction** Add a brief discussion of prior kinetic studies on other TFs or DNA-binding proteins that have reported multiphasic behavior, to strengthen the novelty claim.

## Technical failings that need to be addressed before the case is established
- R1-M1: Model validation is insufficient; quantitative model comparison is needed.
- R1-M2: Statistical treatment of rate constants is lacking.
- R1-M3: Control experiments for potential artifacts are incomplete.

## Risk / unsupported claims
- The claim of a "novel reaction mechanism" for ERα is not fully supported without quantitative model comparison.
- The statement that Sox2 and ERα "bind RNA and DNA with previously unappreciated multiphasic binding kinetics" is only weakly supported because the authors do not comprehensively review prior kinetic studies of these specific proteins.
- The biological relevance of the proposed ERα feedback mechanism is speculative and not experimentally tested.
- The claim that "the two ligands could share an underlying mechanism" for ERα is based on qualitative similarity and is not rigorously tested.
- The statement that SPR and FP findings "are reporting the same phenomenon" is based on qualitative agreement; quantitative concordance is not demonstrated.

## Assessment against Nature-style criteria
- **Originality** Moderate. The observation of multiphasic kinetics for TF–nucleic acid interactions is novel, but the conceptual framework (sequential binding, isomerization) is not new. The proposed feedback mechanism is original but not fully validated.
- **Scientific importance** Moderate. The work provides useful kinetic parameters for two important TFs and raises questions about the complexity of TF–nucleic acid interactions. However, the direct biological implications are not demonstrated, limiting immediate impact.
- **Interdisciplinary readership** Limited. The manuscript is primarily of interest to biophysicists and biochemists studying protein–nucleic acid interactions. The relevance to broader cell biology or gene regulation is not made concrete.
- **Technical soundness** Generally sound in the core measurements, but the model validation and statistical treatment are insufficient. The use of multiple complementary methods is a strength.
- **Readability for nonspecialists** The manuscript is clearly written but assumes familiarity with kinetic analysis and TF biology. The abstract could be more accessible with specific numbers and clearer framing of significance.

## Recommendation posture
**Supportive if technical concerns are resolved.** The core measurements appear carefully executed and the observations are potentially interesting. However, the central mechanistic claim requires stronger validation through quantitative model comparison and additional control experiments. The statistical treatment of rate constants must be improved. If these issues are addressed, the manuscript could make a solid contribution to the field of TF–nucleic acid interactions.