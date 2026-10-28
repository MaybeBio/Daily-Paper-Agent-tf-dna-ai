## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, materials and methods, discussion) as provided
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with stated evidence; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors propose a computational protocol combining docking, clustering, and molecular dynamics simulations to predict protein-RNA binding affinity, using a covariance-based descriptor of interface residue motion. They apply this to six RNA aptamers designed against TDP-43, report a correlation of approximately 0.9 between the descriptor and experimentally measured dissociation constants, and suggest the method's generalizability for aptamer design.
- **Visible evidence base** Main text figures (Figures 2, 3, 4, 5), Table 1 (referenced), supplementary figures (Figure 2a, 2b, 3a, 3b of SI), supplementary tables (Table S1), and methods descriptions
- **Missing materials affecting confidence** Full supplementary data file (Data S1) not provided; specific numerical values for all six Kd measurements not shown in main text; detailed catRAPID design parameters referenced to an external citation not available; exact definitions of "binding site" thresholds and their biological justification partially described; no raw simulation trajectories or convergence metrics beyond RMSD

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach linking interfacial residue dynamics to binding affinity, with a potentially useful application to TDP-43 aptamer design. The reported correlation of approximately 0.9 is striking and warrants attention. However, the evidence base as presented has several gaps that temper confidence: the primary correlation is based on only six data points, the distance-based descriptor shows weaker performance, and the generalizability claim rests on only two additional complexes. The methodological details are mostly clear, but some choices (e.g., temperature ramping for RNA conformational sampling, docking constraints) require stronger justification. The manuscript would benefit from additional validation, clearer reporting of uncertainties, and a more cautious framing of the predictive power.
- **Who would be interested in the results, and why** Researchers in computational structural biology, particularly those working on protein-RNA interactions and aptamer design; groups studying TDP-43 biology and neurodegeneration; method developers interested in dynamic descriptors for binding affinity prediction. The approach could be relevant to those seeking alternatives to static docking scores or sequence-based predictors.
- **Major strengths** 1) The core hypothesis linking synchronized interfacial motion to binding stability is physically plausible and well-motivated. 2) The protocol integrates multiple established tools (catRAPID, HDOCK, GROMACS) in a coherent pipeline. 3) The use of experimental Kd measurements for validation is appropriate and strengthens the study. 4) The analysis of per-residue covariance contributions provides mechanistic insight beyond a single global descriptor. 5) The writing is generally clear and the methods are described in sufficient detail for reproduction.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical robustness
  - **Claim pointer** "We tested the results against experimental measurements of binding affinity (in this case, the dissociation constant) for six RNA molecules, resulting in a linear correlation of about 0.9."
  - **Evidence pointer** Figure 4, Table 1
  - **Concern** The primary claim of predictive power rests on a correlation computed from only six data points. With n=6, a Pearson correlation is highly sensitive to individual points, and the reported value of approximately 0.9 (or -0.89) does not convey the uncertainty. The manuscript does not report confidence intervals, leave-one-out analysis, or any other robustness measure. The p-value of 0.007 is reported, but with such a small sample, this is not sufficient to establish reliability.
  - **Why it matters** The central conclusion of the paper, that the covariance descriptor can estimate binding affinity, depends entirely on this correlation. Without robustness analysis, the reader cannot assess whether the result is driven by one or two influential points or whether it would generalize to new aptamers.
  - **Resolution test** Provide confidence intervals for the correlation coefficient, perform leave-one-out cross-validation, and report the correlation after removing each single data point. If the correlation remains consistently high (e.g., above 0.7) across all subsets, the claim is strengthened. Additionally, report the raw data (Kd values and descriptor values) in a table or supplementary figure to allow independent assessment.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** "This promising pipeline could thus contribute to the design of RNA aptamers interacting with proteins."
  - **Evidence pointer** Section "Testing the covariance-based descriptor in two additional complexes with high and low affinity", Figure 3 of SI
  - **Concern** The generalizability claim is supported by only two additional complexes, selected to maximize Kd difference. This is a minimal test and does not address whether the descriptor works for intermediate affinities, different protein families, or RNA aptamers of different lengths or structures. The choice of these two complexes is not justified beyond their Kd values, and no criteria are given for why they should be representative.
  - **Why it matters** The stated potential for broad applicability in aptamer design requires evidence that the descriptor is not specific to the TDP-43 system or to the particular range of Kd values tested. Two test cases are insufficient to establish this.
  - **Resolution test** Add at least 3-5 additional protein-RNA complexes spanning a wider range of Kd values and structural contexts. If this is not feasible, temper the generalizability claim to be explicitly preliminary and describe the limitations clearly.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological justification
  - **Claim pointer** "We assume that the RNA configuration most suitable for the binding has an overall open (unfolded) configuration, characterized by a high distance between 5' and 3' terminal nucleotides."
  - **Evidence pointer** Section 4.5.3, Figure 1
  - **Concern** The assumption that open RNA conformations are most suitable for binding is stated without direct evidence or citation. While plausible for some RNA-protein interactions, it is not universally true; some proteins bind structured or partially folded RNA elements. The temperature ramping procedure (up to 500 K) to force open conformations may generate non-physiological states that could bias downstream docking and simulation results.
  - **Why it matters** If the initial RNA conformations are not representative of the biologically relevant bound state, the entire pipeline could produce misleading complexes, and the covariance descriptor would reflect artifacts rather than true binding dynamics.
  - **Resolution test** Justify the open-conformation assumption with literature evidence or a control experiment comparing binding affinity predictions using closed versus open RNA conformations. Alternatively, test whether the descriptor is robust to the choice of initial RNA conformation by repeating the pipeline with different starting structures.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evidence completeness
  - **Claim pointer** "The analysis presented in the following section concerns the binding of a selected set of aptamers with the TDP-43 protein. The results concerning two additional and independent systems are reported in the Data S1."
  - **Evidence pointer** Data S1 (not provided)
  - **Concern** The supplementary data file containing results for the two additional systems is not available for review. The main text references this data for the generalizability test, but the actual evidence cannot be evaluated.
  - **Why it matters** The generalizability claim (R1-M2) depends entirely on this unreviewed data. Without access, the claim cannot be verified.
  - **Resolution test** Provide the supplementary data file for review, or include the key results (e.g., correlation values, descriptor values, Kd values) in the main text or a table.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, last sentence
  - **Issue** The abstract states "providing insights into the contribution of each interface residue" but does not specify what those insights are or how they are derived.
  - **Required correction** Briefly summarize the key finding from the per-residue analysis (e.g., which residues dominate the covariance) or remove the phrase to avoid overstating.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, Section 4.5.3
  - **Evidence pointer** Section 4.5.3
  - **Issue** The criterion for "sufficiently populated" open conformational space (10% of trajectory) is arbitrary and not justified.
  - **Required correction** Provide a rationale for the 10% threshold or cite precedent for this choice.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results, Figure 4
  - **Evidence pointer** Figure 4
  - **Issue** The p-value for the correlation is reported, but the degrees of freedom and the exact test used are not stated.
  - **Required correction** Specify the statistical test (e.g., two-sided t-test for Pearson correlation) and report degrees of freedom.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Table 1
  - **Evidence pointer** Table 1
  - **Issue** The table lists Kd values but does not report experimental uncertainties or replicate information.
  - **Required correction** Add standard deviations or confidence intervals for each Kd measurement, and state the number of replicates.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Discussion, paragraph 2
  - **Evidence pointer** Discussion
  - **Issue** The discussion of the distance-based descriptor's limitations is brief and does not address why it failed to reach significance.
  - **Required correction** Expand on possible reasons (e.g., insensitivity to correlated motions, averaging effects) to help readers understand the descriptor's scope.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical robustness of the primary correlation) is the most critical. The central claim of the paper cannot be fully assessed without robustness analysis. R1-M4 (missing supplementary data) also needs resolution to evaluate the generalizability claim.
- **Assessment against Nature-style criteria**  
  *Originality*: The concept of using synchronized interfacial motion as a binding affinity descriptor is a novel angle, distinct from common energy-based or contact-based approaches. This is a genuine contribution to the field.  
  *Scientific importance*: If validated, the method could offer a computationally tractable way to rank aptamer candidates, which is relevant for therapeutic design. However, the current evidence base is too limited to establish broad importance.  
  *Interdisciplinary readership*: The work bridges computational biophysics, RNA biology, and neurodegeneration, which could attract a broad audience. The writing is accessible to nonspecialists in each area, though some methodological details assume familiarity with MD simulations.  
  *Technical soundness*: The pipeline is logically constructed and uses established tools, but the small sample size, arbitrary thresholds, and lack of robustness checks undermine technical confidence.  
  *Readability for nonspecialists*: The manuscript is generally well-written, with clear figure descriptions and a logical flow. The abstract and introduction effectively set the context. Some methods sections are dense but acceptable for a specialized journal.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the application to TDP-43 is timely, but the statistical robustness of the main result and the generalizability claim must be strengthened before the case is fully established.

## Risk / unsupported claims
- The claim of a linear correlation of approximately 0.9 between the covariance descriptor and Kd is not robustly supported due to the small sample size (n=6) and lack of uncertainty quantification.
- The generalizability of the approach to other protein-RNA systems is not established from the two additional complexes described only in the unavailable supplementary data.
- The assumption that open RNA conformations are optimal for binding is stated without direct evidence.
- The identification of specific residues (G245, C244, S258, C198, R197, G196, V195, A228, P187, F229) as key contributors to high-affinity binding is presented without validation against experimental mutagenesis or other independent data.
- The claim that the method "could contribute to the design of RNA aptamers" is speculative and not directly demonstrated by the results.