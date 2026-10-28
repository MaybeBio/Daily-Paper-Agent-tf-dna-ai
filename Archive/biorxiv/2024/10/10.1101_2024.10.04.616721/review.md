## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure legends as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors report that YY1 contains two nucleic acid binding domains: the canonical C-terminal four C2H2 zinc-finger module and a previously unannotated domain within the REPO region (termed REPO-NAB). They further report that the N-terminus of YY1 autoinhibits nucleic acid binding of both domains, and that the zinc-finger module binds single-stranded RNA with higher affinity than double-stranded DNA.
- **Visible evidence base** Fluorescence polarization binding assays, circular dichroism spectra, mutagenesis experiments, and computational structural predictions (RoseTTAFold, AlphaFold3). Supplementary figures referenced include Figures S1-S7 and Supplemental Tables 1.
- **Missing materials affecting confidence** Raw binding isotherms, replicate numbers, exact protein concentrations for each experiment, full supplementary figures and tables, and details of the computational analyses (e.g., parameters for RoseTTAFold/AlphaFold3) were not available in the provided text. The manuscript appears to be formatted for Nucleic Acids Research, not Nature.

## Reviewer
- **Overall assessment** This manuscript presents a systematic biochemical dissection of YY1 nucleic acid binding properties, resolving a controversy in the literature regarding the RNA binding interface. The identification of a second nucleic acid binding domain within the REPO region and the observation of N-terminal autoinhibition are potentially significant findings. However, several technical concerns regarding the quantitative rigor of the binding assays, the interpretation of the autoinhibition mechanism, and the generalizability of the conclusions need to be addressed. The work is solid but incremental in nature, and the claims of broad relevance to transcription factor biology require stronger support.
- **Who would be interested in the results, and why** Researchers studying transcription factor biology, particularly those interested in YY1 function, the role of intrinsically disordered regions in nucleic acid binding, and the interplay between DNA and RNA binding in gene regulation. The findings may also be of interest to those studying Polycomb group protein recruitment and genome architecture.
- **Major strengths** The study addresses a clear controversy in the literature with systematic side-by-side comparisons. The use of quantitative fluorescence polarization is appropriate for measuring binding affinities. The identification of a previously unannotated nucleic acid binding domain in the REPO region is novel. The mutagenesis approach to separate DNA and RNA binding functions is thoughtful and provides useful tools for future studies.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of binding measurements
  - **Claim pointer** The authors claim that the zinc-finger module binds ssRNA with nearly 10-fold higher affinity than dsDNA, and that the REPO-NAB binds both DNA and RNA with little sequence specificity.
  - **Evidence pointer** Figure 2B, Figure 4B, Methods section "Fluorescence polarization"
  - **Concern** The fluorescence polarization assays are described as using 5' FAM-labeled oligonucleotides at 10 or 20 nM final concentration. However, the protein concentration range for each experiment is only stated in figure legends, which were not fully provided. More critically, the authors report Kd values with "correlation coefficients ≥ 0.9" but do not report the number of independent replicates, the standard error of the mean across replicates, or whether the reported uncertainties represent fitting errors or biological variability. For a study that hinges on quantitative comparisons of binding affinities, this level of detail is insufficient. Additionally, the use of a single fluorescent label at the 5' end can influence binding measurements for proteins that may bind nucleic acids in a length- or end-dependent manner.
  - **Why it matters** The central claims of the paper rely on quantitative differences in binding affinities (e.g., 10-fold difference between ssRNA and dsDNA for the zinc-finger module, and differences between full-length YY1 and individual domains). Without rigorous statistical treatment and demonstration of reproducibility, these quantitative claims are not fully supported.
  - **Resolution test** Provide the number of independent experiments (n ≥ 3), report mean ± SEM or SD for all Kd values, and show individual data points. Include a statistical comparison (e.g., t-test or ANOVA) for the key affinity differences. Also, consider testing whether the 5' FAM label affects binding by comparing with a 3' labeled or internally labeled probe for at least one key interaction.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Interpretation of autoinhibition mechanism
  - **Claim pointer** The authors claim that the N-terminus of YY1 autoinhibits nucleic acid binding of both the zinc-finger module and the REPO-NAB, and that this inhibition can occur in trans.
  - **Evidence pointer** Figure 5A and 5B, Figure 3B, Discussion section
  - **Concern** The trans inhibition experiments shown in Figure 5A and 5B use the N-terminus (amino acids 1-297) added in trans to the zinc-finger module. However, the N-terminus itself does not bind nucleic acids in the concentration range tested (Figure 3B). The authors interpret the decreased binding of the zinc-finger module to nucleic acids in the presence of the N-terminus as inhibition. An alternative explanation is that the N-terminus and zinc-finger module form a non-covalent complex that has lower nucleic acid binding affinity, but this complex formation is not directly demonstrated. Furthermore, the authors do not test whether the N-terminus inhibits the REPO-NAB in trans, only in cis (by comparing the full N-terminus construct with the isolated REPO-NAB). The claim of a general autoinhibitory mechanism is therefore not fully supported by the data presented.
  - **Why it matters** The autoinhibition mechanism is a major conceptual advance claimed by the authors. If the mechanism is not rigorously established, the significance of the work is substantially diminished. The distinction between cis and trans inhibition has implications for the proposed model of YY1 regulation.
  - **Resolution test** Perform direct binding assays to demonstrate complex formation between the N-terminus and the zinc-finger module (e.g., size exclusion chromatography, pull-down, or analytical ultracentrifugation). Test whether the N-terminus inhibits REPO-NAB binding in trans. Also, test whether the inhibition is competitive with nucleic acid binding or allosteric by varying the order of addition and the concentration of nucleic acid substrate.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Specificity and physiological relevance
  - **Claim pointer** The authors suggest that the nucleic acid binding properties of YY1 and their autoinhibition are relevant to YY1's function in transcription, repression, and genome architecture.
  - **Evidence pointer** Discussion section, Figure 1B
  - **Concern** The manuscript does not provide any in vivo or cellular data to support the physiological relevance of the observed biochemical properties. The computational analysis shown in Figure 1B is used to motivate the study but does not directly test the functional significance of the newly identified binding properties. The authors acknowledge this limitation but do not provide a clear path forward. The claim that these findings "enable future mechanistically precise functional investigations" is reasonable, but the current manuscript does not establish the relevance of the autoinhibition mechanism in a cellular context.
  - **Why it matters** For a Nature-style audience, the significance of biochemical findings is greatly enhanced by demonstrating their relevance in a biological context. Without such evidence, the work may be seen as descriptive rather than mechanistically insightful.
  - **Resolution test** Provide at least one experiment in a cellular or in vivo context that tests the functional importance of the identified nucleic acid binding domains or the autoinhibition mechanism. For example, express the separation-of-function mutants in cells and assess their effects on YY1 target gene expression, chromatin localization, or genome architecture.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of figure presentation
  - **Affected element** Figure 2A
  - **Evidence pointer** Figure 2A, Methods section
  - **Issue** The panel of nucleic acid substrates in Figure 2A is described but the full figure was not available. The authors should ensure that the sequences, lengths, and structures of all oligonucleotides are clearly annotated in the figure or legend.
  - **Required correction** Provide a table or figure panel listing all nucleic acid substrates with their sequences, modifications, and predicted secondary structures.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** All binding data
  - **Evidence pointer** Figures 2-5, Methods section
  - **Issue** The authors report Kd values with uncertainties but do not specify whether these are standard errors of the fit, standard deviations across replicates, or confidence intervals. The number of replicates is not stated.
  - **Required correction** Clearly state the number of independent experiments and the type of error reported for all Kd values. Consider reporting 95% confidence intervals.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "REPO-NAB" nomenclature
  - **Evidence pointer** Throughout the manuscript
  - **Issue** The term "REPO-NAB" is introduced but the rationale for this specific name is not fully explained. The authors should clarify whether this domain corresponds to a previously defined structural or functional element.
  - **Required correction** Provide a brief explanation for the naming and discuss any relationship to known nucleic acid binding motifs.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness of methods
  - **Affected element** Circular dichroism experiments
  - **Evidence pointer** Methods section "Circular dichroism"
  - **Issue** The CD experiments are described but the analysis of the melting curve is not detailed. The authors state the melting transition is "not sharply defined" but do not provide quantitative analysis.
  - **Required correction** Provide the raw CD spectra, the melting curve, and any quantitative analysis (e.g., Tm estimation or comparison with a folded control).
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Computational analysis details
  - **Affected element** Figure 1B
  - **Evidence pointer** Methods section "Computational analyses of YY1 genomic binding sites"
  - **Issue** The computational analysis used to generate Figure 1B is described but the full details of the intersection analysis and the statistical significance of the overlap are not provided.
  - **Required correction** Provide the number of peaks/regions in each dataset, the expected overlap by chance, and the statistical test used to assess significance.

## Risk / unsupported claims
- The claim that the N-terminus autoinhibits nucleic acid binding of the REPO-NAB in cis is supported by comparing the full N-terminus construct with the isolated REPO-NAB, but the mechanism of this inhibition is not characterized.
- The claim that the N-terminus inhibits zinc-finger module binding in trans is supported by competition experiments, but the physical basis of this inhibition (e.g., direct interaction) is not demonstrated.
- The claim that the zinc-finger module binds ssRNA with higher affinity than dsDNA is based on quantitative comparisons that lack statistical rigor as described above.
- The claim that the REPO-NAB binds nucleic acids with "little apparent sequence specificity" is based on a limited panel of substrates and may not be generalizable.
- The physiological relevance of the identified nucleic acid binding properties and autoinhibition is not experimentally tested and remains speculative.

## Assessment against Nature-style criteria
- **Originality** The identification of a second nucleic acid binding domain in the REPO region of YY1 and the observation of N-terminal autoinhibition are novel findings. However, the concept of transcription factors having multiple nucleic acid binding domains and autoinhibitory regulation is not entirely new, and the work builds on prior studies.
- **Scientific importance** The findings have the potential to inform our understanding of YY1 function and the broader role of IDRs in transcription factor regulation. However, the lack of in vivo validation limits the immediate impact.
- **Interdisciplinary readership** The work is primarily of interest to biochemists and molecular biologists studying transcription. The methods and concepts may not appeal to a broad interdisciplinary audience.
- **Technical soundness** The experimental approach is generally sound, but the lack of detailed statistical reporting and the incomplete characterization of the autoinhibition mechanism are significant weaknesses.
- **Readability for nonspecialists** The manuscript is clearly written and the logic is easy to follow. However, the heavy reliance on binding affinity measurements and the lack of a clear biological context may make it less accessible to nonspecialists.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents interesting and potentially important findings, but the technical concerns regarding the quantitative rigor of the binding assays and the incomplete characterization of the autoinhibition mechanism need to be addressed. The lack of in vivo validation also limits the significance of the work. I would be supportive if the authors can provide more rigorous statistical analysis, demonstrate the physical basis of the autoinhibition, and provide at least one experiment showing the functional relevance of these findings in a cellular context.