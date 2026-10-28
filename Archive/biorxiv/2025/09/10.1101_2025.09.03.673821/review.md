## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by evidence presented in the supplied material
- **Shared manuscript claim summary** The authors combine molecular dynamics simulations with graph-theoretic network analyses to propose that efficient PAM recognition in three Cas9 variants (VQR, VRER, EQR) depends on three interdependent features: local stabilization of the PAM-interacting domain, preservation of long-range allosteric communication with the REC3 domain, and entropic tuning of DNA engagement. They contrast these active variants with two engineered constructs (ENG1, ENG2) that fail to expand PAM recognition, attributing the failure to disruption of distal networks rather than to the PAM-contacting substitutions alone.
- **Visible evidence base** MD simulation protocols, community network analysis methodology, eigenvector centrality analysis, communication pathway analysis, and qualitative descriptions of results (Figures 2-5, Figure S1 referenced but not visible)
- **Missing materials affecting confidence** Figures 1-5 and Figure S1 are referenced but not provided; no quantitative data (numerical values, error bars, statistical tests) are presented; no simulation convergence metrics are reported; no experimental validation data are included; the Supporting Information is mentioned but not supplied

## Reviewer

- **Overall assessment** This manuscript addresses a mechanistically important question in CRISPR-Cas9 engineering: why certain combinations of mutations expand PAM compatibility while others, despite seemingly favorable amino acid substitutions, fail to do so. The proposed framework, emphasizing distal allosteric networks over local contacts, is conceptually appealing and potentially useful for future engineering efforts. However, the evidence presented in the supplied material is largely qualitative and descriptive. The central claims rest on interpretations of network metrics and interaction analyses, but the absence of quantitative data, statistical treatment, and validation against experimental observations substantially limits the strength of the conclusions. The manuscript would benefit from clearer presentation of numerical results, explicit comparisons across systems, and a more critical discussion of the limitations of the computational approach.
- **Who would be interested in the results, and why** Researchers in CRISPR biology and genome engineering, particularly those involved in rational design of Cas9 variants with altered or expanded PAM specificity. Computational biophysicists studying allosteric communication in large protein-nucleic acid complexes may also find the methodological framework of interest. The proposed design rules, if substantiated, could inform future engineering strategies beyond the specific variants studied.
- **Major strengths** The manuscript addresses a significant and timely problem in genome editing. The combination of MD simulations with graph-theoretic analyses is methodologically sophisticated and appropriate for studying allosteric communication. The comparison of active variants with inactive engineered constructs provides a useful contrast that helps isolate the role of distal networks. The proposed three-principle framework is clear and potentially generalizable. The authors appropriately reference their prior work on xCas9, suggesting a coherent research program.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that "efficient recognition is not dictated solely by direct contacts between PAM-interacting residues and DNA, but also by a distal network that stabilizes the PAM-binding domain and preserves long-range communication with REC3."
  - **Evidence pointer** Results sections describing Figures 2-5; location not provided
  - **Concern** The central claim of the manuscript is presented without quantitative support in the supplied text. The results sections describe qualitative trends (e.g., "markedly weakened," "pronounced decrease," "robust communication pathway") but provide no numerical values, statistical comparisons, or effect sizes. For a claim that distinguishes between competing mechanistic hypotheses, the evidence must be presented in a form that allows the reader to assess the magnitude and significance of the observed differences between active and inactive variants.
  - **Why it matters** Without quantitative data, it is impossible to determine whether the observed differences between active and inactive variants are meaningful or within the range of normal fluctuation. The claim that distal networks, rather than local contacts, determine PAM recognition success is a strong mechanistic statement that requires robust quantitative evidence.
  - **Resolution test** Provide numerical values for key metrics (e.g., community edge strengths, eigenvector centrality values, path scores) with appropriate statistical treatment across replicate simulations. Include comparisons between all systems with measures of variability and, where appropriate, statistical significance.
  
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validation
  - **Claim pointer** The authors state that "in the ENG1-2 systems, D1135 forms a stable salt bridge with K1007" and that this "sequesters K1107 from DNA, destabilizing its interaction."
  - **Evidence pointer** Results section "Effect of Mutations on PAM Recognition"; location not provided
  - **Concern** The manuscript does not report any validation of the simulation methodology. No convergence metrics (e.g., RMSD stabilization, equilibration checks), no force field validation against experimental data, and no assessment of sampling adequacy are presented. The claim that a specific salt bridge is "stable" requires demonstration that the simulation has reached equilibrium and that the observed interaction persists over a meaningful timescale. Additionally, the manuscript does not address whether the ~1 microsecond simulation time per replicate is sufficient to capture the relevant conformational dynamics of a large multi-domain complex.
  - **Why it matters** The conclusions depend entirely on the reliability of the MD simulations. Without evidence of convergence and adequate sampling, the observed differences between systems could be artifacts of insufficient simulation time or incomplete equilibration. The specific claim about salt bridge stability is particularly sensitive to sampling adequacy.
  - **Resolution test** Report convergence metrics (e.g., RMSD time series, block averaging of key observables), provide evidence that key interactions have reached steady-state occupancy, and discuss the expected timescales for the conformational changes being studied. If possible, validate the simulation results against available experimental data for these variants.
  
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretive rigor
  - **Claim pointer** The authors propose that "PAM recognition requires local stabilization, distal coupling, and entropic tuning, rather than a simple consequence of base-specific contacts."
  - **Evidence pointer** Discussion and Conclusions sections; location not provided
  - **Concern** The manuscript presents a three-principle framework but does not clearly define how each principle is operationalized or measured. Specifically, "entropic tuning" is mentioned as a key principle, but no entropy calculations or related analyses are described in the methods or results. The relationship between the network metrics (community structure, eigenvector centrality, path analysis) and the proposed principles is not explicitly mapped.
  - **Why it matters** A framework intended to provide "design rules" must have clearly defined, measurable components. If "entropic tuning" is not directly assessed, its inclusion as a core principle is not supported by the evidence presented. The manuscript would be strengthened by explicitly connecting each proposed principle to specific, quantifiable observables.
  - **Resolution test** Define how each of the three principles is measured in the simulations. If entropy is not directly calculated, either add such calculations or reframe the principle in terms of the observables that are actually measured. Provide a clear mapping between the proposed principles and the specific metrics reported.
  
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** External validity
  - **Claim pointer** The authors state that their findings "establish general design rules that can guide the rational engineering of Cas9 variants with expanded PAM compatibility and enhanced genome-editing performance."
  - **Evidence pointer** Conclusions section; location not provided
  - **Concern** The manuscript does not include any experimental validation of the proposed design rules. While the authors compare active variants with inactive engineered constructs, all systems are studied computationally. The claim that these rules can "guide" engineering efforts implies predictive power that is not demonstrated. No new variant is designed and tested based on the proposed principles.
  - **Why it matters** The stated goal of providing design rules for engineering is not fully met without demonstrating that the rules can predict or explain the behavior of variants beyond those already characterized. The manuscript would be substantially strengthened by including at least one test of the framework's predictive power.
  - **Resolution test** Either include experimental validation of at least one prediction derived from the framework, or temper the claims to reflect that these are hypotheses requiring experimental testing. If experimental data are not available, clearly state this limitation and suggest specific testable predictions.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods section, community network analysis
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The description of the community network analysis methodology is brief and refers to the Supporting Information for details. The Girvan-Newman algorithm and edge betweenness are mentioned, but the specific parameters (e.g., number of communities, cutoff criteria) are not stated.
  - **Required correction** Provide sufficient methodological detail in the main text or clearly indicate which parameters are described in the Supporting Information. At minimum, state the key parameters used for community detection and path analysis.
  
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Internal consistency
  - **Affected element** Results section, eigenvector centrality analysis
  - **Evidence pointer** Results section "Dynamic Remodeling of Cas9 Variants"; location not provided
  - **Issue** The text states that "the inactive variants (ENG1 and ENG2) show a pronounced reduction in centrality within the REC3 domain" but also notes "increased fluctuations in the per-residue EC" for these variants. The relationship between reduced mean centrality and increased variability is not discussed.
  - **Required correction** Clarify whether the reduced centrality is observed in the mean values, the distribution, or both. Discuss what increased variability implies for the interpretation of the centrality differences.
  
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results section, communication pathway analysis
  - **Evidence pointer** Results section "Alteration of the HNH-REC3 Allosteric Signaling"; location not provided
  - **Issue** The pathway analysis identifies the 50 highest-scoring paths, but the criteria for selecting this number and the sensitivity of the results to this choice are not discussed.
  - **Required correction** Briefly justify the choice of 50 paths and, if possible, state whether the conclusions are robust to this parameter.
  
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Referencing
  - **Affected element** Introduction, statement about engineered variants
  - **Evidence pointer** Introduction; location not provided
  - **Issue** The statement that "variants carrying only substitutions of the arginine residues that directly contact the canonical 5'-TGG-3' PAM (i.e., R1335/R1335 Q/E) abolish DNA cleavage activity without altering PAM specificity" is presented without a citation.
  - **Required correction** Add a citation to the original experimental work demonstrating this observation, or clarify if this is a new finding from the present study.
  
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Throughout
  - **Evidence pointer** Multiple sections; location not provided
  - **Issue** The term "entropic tuning" is used as a core principle but is not defined or measured. This creates ambiguity about what is being claimed.
  - **Required correction** Either define what is meant by "entropic tuning" in operational terms, or replace this term with a more concrete description of the observed phenomenon.
- **Technical failings that need to be addressed before the case is established** R1-M1 (absence of quantitative evidence), R1-M2 (lack of methodological validation), R1-M3 (undefined operationalization of key principles)
- **Assessment against Nature-style criteria** 
  - Originality: The conceptual framework, emphasizing distal allosteric networks over local contacts in PAM recognition, offers a potentially novel perspective. However, the authors have previously published related work on xCas9 using similar methods, so the incremental novelty of applying this framework to VQR, VRER, and EQR variants needs to be more clearly articulated.
  - Scientific importance: The question of how to rationally engineer Cas9 variants with expanded PAM compatibility is of significant importance to the genome editing field. If the proposed design rules are validated, they could have substantial practical impact.
  - Interdisciplinary readership: The topic bridges computational biophysics, structural biology, and genome engineering. The manuscript is likely to appeal to researchers in these intersecting communities, though the presentation is currently more oriented toward computational specialists.
  - Technical soundness: The methodological approach is appropriate in principle, but the lack of quantitative results, validation metrics, and statistical treatment in the supplied material prevents assessment of technical soundness. The manuscript cannot be evaluated for technical rigor without these elements.
  - Readability for nonspecialists: The manuscript is generally clearly written, but the qualitative nature of the results and the reliance on specialized network analysis terminology may limit accessibility. A more explicit explanation of the biological significance of the network metrics would improve readability.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is interesting and the methodological approach is appropriate, but the supplied material lacks the quantitative detail, validation, and rigor required to support the strong mechanistic claims made. The manuscript could become suitable for publication after substantial revision that addresses the major concerns, particularly the absence of quantitative evidence and methodological validation.

## Risk / unsupported claims
- The claim that "efficient recognition is not dictated solely by direct contacts" is not quantitatively supported in the supplied text
- The claim that "entropic tuning" is a key principle of PAM recognition is not supported by any entropy-related analysis
- The claim that the findings "establish general design rules" for engineering is not supported without experimental validation or predictive testing
- The assertion that ENG1 and ENG2 "fail to establish stable contacts" with the PAM is presented without quantitative interaction data
- The claim that the D1135-K1107 salt bridge "sequesters K1107 from DNA" is presented without occupancy or distance data
- The statement that communication pathways are "markedly attenuated or rerouted" in inactive variants is not supported by quantitative path analysis data
- The relationship between the proposed three principles and the specific network metrics used is not explicitly established