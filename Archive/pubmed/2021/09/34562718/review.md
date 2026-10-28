## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full methods, figures, or statistical details
- **Shared manuscript claim summary** The authors report that a clustered DNA lesion containing a bulky fluorescein-modified non-nucleoside residue (nFlu) and a diethylene glycol phosphodiester (DEG) apurinic/apyrimidinic site analog is processed by mammalian nucleotide excision repair (NER) in a topology-dependent manner. Specifically, nFlu removal efficiency decreases when DEG is present in the complementary strand and is abolished when DEG is opposite nFlu. The initiating factor XPC-RAD23B shows increased affinity for clustered damage, with affinity strengthening as the lesions are positioned closer. Molecular dynamics simulations and geometric analyses are used to propose structural determinants of repair efficiency.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full experimental methods, quantitative repair assays, binding affinity data, molecular dynamics simulation parameters and trajectories, statistical analyses, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a focused and mechanistically interesting question about how clustered DNA lesions of mixed topology are recognized and processed by NER. The finding that XPC-RAD23B binding affinity increases while repair efficiency decreases for clustered substrates is counterintuitive and potentially significant. However, the abstract alone does not provide sufficient quantitative detail to evaluate the robustness of the claims, the experimental controls, or the validity of the molecular dynamics conclusions. The work is likely of interest to the DNA repair community, but the case for a generalizable mechanistic insight is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying DNA repair mechanisms, particularly nucleotide excision repair and clustered lesion processing; investigators interested in the cellular consequences of complex DNA damage induced by ionizing radiation or chemotherapeutic agents; and computational biologists working on DNA structural dynamics and lesion recognition.
- **Major strengths** The study addresses a biologically relevant and under-explored question, namely how clustered lesions of mixed chemical nature are handled by NER. The combination of biochemical repair assays, binding affinity measurements, and molecular dynamics simulations provides a multi-pronged approach. The observation that XPC-RAD23B affinity and repair efficiency diverge for clustered substrates is a potentially novel and thought-provoking result.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The question of how clustered lesions of mixed topology are processed by NER is relatively underexplored, and the specific use of a DEG analog paired with a bulky fluorescein lesion appears novel. However, the conceptual advance over existing clustered damage studies is incremental rather than paradigm-shifting.  
  Scientific importance: The topic is relevant to understanding DNA repair under conditions of complex damage, which has implications for mutagenesis and cancer therapy. The importance is moderate and field-specific rather than broad.  
  Interdisciplinary readership: The work bridges biochemistry and computational structural biology, which may attract readers from both communities, but the appeal beyond DNA repair specialists is limited.  
  Technical soundness: Cannot be fully assessed from the abstract. The lack of quantitative data, controls, and simulation validation details prevents a definitive evaluation.  
  Readability for nonspecialists: The abstract is reasonably clear but assumes familiarity with NER terminology and lesion chemistry. It is accessible to a specialized audience but not to a general scientific readership.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis and preliminary data, but the absence of experimental detail and quantitative support means the core claims cannot be verified. A supportive posture would require access to the full manuscript.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that "the efficiency of nFlu removal decreases in the presence of DEG in the complementary strand and is completely suppressed when the DEG is located opposite the nFlu."  
- **Evidence pointer** Location not provided  
- **Concern** The abstract states that nFlu removal efficiency decreases or is suppressed depending on DEG position, but no quantitative data are provided. It is unclear what magnitude of decrease is observed, how many replicates were performed, what statistical tests were used, and whether the suppression is absolute or below detection limits.  
- **Why it matters** The central conclusion of the paper rests on this differential repair efficiency. Without quantitative support, the reader cannot assess whether the effect is robust, biologically meaningful, or an artifact of the specific experimental conditions.  
- **Resolution test** Provide repair efficiency values with standard deviations, statistical significance, and a description of the assay sensitivity and detection limits. Show that the suppression is not due to substrate instability or assay failure.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Internal consistency  
- **Claim pointer** The authors claim that XPC-RAD23B has "higher affinity for DNA containing clustered damage as compared to DNA containing a single bulky lesion" and that "the affinity of XPC strengthens as the positions of DEG and nFlu become closer."  
- **Evidence pointer** Location not provided  
- **Concern** The abstract reports increased XPC-RAD23B binding affinity for clustered lesions while simultaneously reporting decreased repair efficiency. This apparent disconnect is intriguing but is not explained. The abstract does not address whether the increased binding is productive or non-productive, whether it reflects a kinetic or thermodynamic effect, or whether the binding measurements are directly comparable to the repair assays.  
- **Why it matters** If XPC binds more tightly but repair is less efficient, the mechanistic interpretation is ambiguous. The authors may be observing a non-productive binding mode, a sequestration effect, or a difference in the rate-limiting step. Without reconciliation, the two main findings appear contradictory and weaken the overall narrative.  
- **Resolution test** Provide binding affinity values (e.g., Kd) for all substrate configurations, and discuss how increased binding affinity relates to the observed repair outcomes. Include a model or hypothesis that reconciles the binding and repair data.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical validation  
- **Claim pointer** The authors state that "the changes in the double-stranded DNA's geometry caused by the presence of clustered damage were also assessed" and that "the obtained experimental data together with the results of molecular dynamics simulations make it possible to get insight into the structural features of DNA containing clustered lesions that determine the efficiency of repair."  
- **Evidence pointer** Location not provided  
- **Concern** The abstract mentions geometric assessments and molecular dynamics simulations but provides no details on the methods used, the parameters of the simulations, the force field, the simulation timescale, or how the simulations were validated against experimental data. It is unclear whether the simulations are predictive or merely descriptive.  
- **Why it matters** The structural interpretation is a key component of the paper's contribution. If the simulations are not robustly validated or if the geometric changes are not directly linked to repair outcomes, the mechanistic insight claimed by the authors is speculative.  
- **Resolution test** Describe the experimental methods used for geometric assessment (e.g., gel mobility, FRET, crystallography) and provide simulation details including force field, water model, simulation length, and convergence criteria. Show that the simulated structures are consistent with experimental observations and that the proposed structural determinants correlate with repair efficiency across all substrate configurations.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The term "clustered damage" is defined as "two or more lesions located within one or two turns of the DNA helix," but the abstract does not specify the exact distance between nFlu and DEG in the substrates used.  
- **Required correction** Specify the inter-lesion distances (in base pairs) for each substrate configuration tested, so the reader can interpret the positional effects described.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Experimental scope  
- **Evidence pointer** Abstract, overall  
- **Issue** The abstract focuses exclusively on XPC-RAD23B as the initiating factor. It is unclear whether other NER factors (e.g., XPA, TFIIH) were examined or whether the observed effects are specific to the recognition step.  
- **Required correction** Clarify whether the study is limited to the recognition step or whether downstream NER factors were also assessed. If not, state this limitation explicitly.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Generalizability  
- **Affected element** Biological relevance  
- **Evidence pointer** Abstract, final sentence  
- **Issue** The abstract states that the study "should help to understand the probable fate of bulky adduct-containing clusters of various topologies in the mammalian cell," but no cellular experiments are described. The claim of cellular relevance is speculative.  
- **Required correction** Soften the concluding statement to reflect that the findings are based on in vitro and computational analyses, and that cellular validation would be needed to confirm the proposed biological implications.

## Risk / unsupported claims
- The claim that nFlu removal is "completely suppressed" when DEG is opposite nFlu is unsupported without quantitative data and detection limit information.
- The claim that XPC-RAD23B affinity "strengthens as the positions of DEG and nFlu become closer" is unsupported without binding data for multiple inter-lesion distances.
- The claim that molecular dynamics simulations provide "insight into the structural features... that determine the efficiency of repair" is unsupported without simulation details and validation.
- The concluding statement about the "probable fate of bulky adduct-containing clusters in the mammalian cell" is speculative and not supported by the in vitro and computational data described in the abstract.