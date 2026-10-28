## Review setup
- **Input scope** Full manuscript text (preprint, arXiv ID 2512.02864v1)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No external data or supplementary materials were assessed.
- **Shared manuscript claim summary** The authors report that the transcription factor NANOG forms self-limited micelle-like clusters via its intrinsically disordered tryptophan-rich domain, that these clusters expose DNA-binding domains, and that at high concentrations NANOG forms aging microgels that modulate DNA rheology. They propose that this mechanism may regulate gene expression by stabilizing genome dynamics at key regulatory sites.
- **Visible evidence base** Results sections describing EMSA, microrheology, cryo-EM, mass photometry, DLS, and Mpipi residue-level simulations. Figures referenced but not directly viewable. No supplementary information was provided.
- **Missing materials affecting confidence** Figures and supplementary information were not accessible. Detailed simulation parameters, raw rheological data, statistical analyses, and control experiments are referenced but not fully described in the text.

## Reviewer
- **Overall assessment** This manuscript presents a novel and potentially significant finding: a transcription factor with an intrinsically disordered domain can form aging microgels that modulate DNA rheology. The combination of experimental and computational approaches is ambitious and appropriate. However, several technical concerns must be addressed before the central claims are fully established. The link between in vitro rheology and in vivo transcriptional regulation remains speculative, and key quantitative details are missing.
- **Who would be interested in the results, and why** Researchers in biophysics, soft matter physics, and molecular biology, particularly those studying phase separation, intrinsically disordered proteins, transcription factor dynamics, and chromatin organization. The work bridges materials science and gene regulation, which could attract a broad interdisciplinary audience.
- **Major strengths** The study addresses an important and under-explored question: how the material properties of transcription factor complexes might influence genome function. The combination of multiple orthogonal techniques (simulations, cryo-EM, mass photometry, DLS, microrheology) is rigorous. The use of two well-characterized mutants provides a clear structure-function framework. The discovery of self-limited micelle-like clusters is novel and mechanistically interesting.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria**  
  *Originality*: High. The concept of a transcription factor forming aging microgels to modulate DNA rheology is novel and not anticipated by prior work on phase separation.  
  *Scientific importance*: Potentially high, if the in vivo relevance is established. The proposed mechanism could reshape understanding of how TFs regulate gene expression.  
  *Interdisciplinary readership*: Strong. The work speaks to biophysicists, soft matter scientists, and molecular biologists. The writing is accessible but assumes familiarity with rheology and IDP concepts.  
  *Technical soundness*: Currently not fully established. Several methodological details and quantitative analyses are missing or under-described.  
  *Readability for nonspecialists*: Generally good, but the results section is dense and would benefit from clearer explanations of key concepts (e.g., aging, micelle-like clusters, microgels) for a broad audience.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that NANOG forms "macroscopic aging gels" at high concentrations and that this is mediated by the WR domain.
- **Evidence pointer** Figure 1c, 1d, 1f, 1h, 1i; Results section "Results"
- **Concern** The evidence for gel formation relies on microrheology measurements of tracer MSDs and derived moduli. However, the text does not provide quantitative details on how the gel point is defined, how many independent replicates were performed, or how the effective viscosity increase of 10^4-fold was calculated. The GSER analysis requires assumptions about tracer-particle interactions and homogeneity that may not hold in aging, heterogeneous systems. The claim that W10A "remained liquid" is based on a single qualitative observation (Figure 1c) and lacks quantitative rheological confirmation.
- **Why it matters** The central claim of the paper is that NANOG forms aging gels. If the rheological characterization is not robust, the entire premise is weakened.
- **Resolution test** Provide quantitative rheological data (e.g., frequency-dependent moduli, gel point determination, replicate numbers, error bars) for all three variants. Include a control experiment with a non-aggregating protein or a WR-deleted construct to confirm specificity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that NANOG forms "self-limited micelle-like clusters" with a well-defined maximum size of approximately 30 proteins, and that these clusters expose DNA-binding domains.
- **Evidence pointer** Figure 2a-2e; Results section "Results"
- **Concern** The simulation results are presented as evidence for micelle-like cluster formation, but the text lacks critical details: how cluster size was defined and measured, how the "well-defined maximum size" was determined, whether the simulations reached equilibrium, and how sensitive the results are to the Mpipi model parameters. The cryo-EM and mass photometry data are described as confirming the simulations, but no quantitative comparison (e.g., size distributions, cluster occupancy) is provided. The claim that the DNA-binding domain is "exposed" on the cluster surface is inferred from distance measurements but not directly validated experimentally.
- **Why it matters** The proposed mechanism of DNA bridging depends on the structural organization of the clusters. If the cluster structure is not robustly established, the mechanism is speculative.
- **Resolution test** Provide quantitative cluster size distributions from simulations and experiments, with statistical comparisons. Include a direct experimental test of DNA-binding domain exposure (e.g., antibody labeling or crosslinking). Show that the simulation results are robust to model parameter variations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that WT NANOG, but not W51A or W10A, modulates DNA rheology by bridging DNA molecules.
- **Evidence pointer** Figure 3a-3d; Results section "Results"
- **Concern** The microrheology data for DNA-NANOG mixtures are described qualitatively ("marked reduction in tracer mobility") without quantitative metrics (e.g., MSD exponents, viscosity values, statistical significance). The concentration of NANOG used (7.9 µM) is much lower than in the gelation experiments (1 mM), yet the authors claim a significant rheological effect. The mechanism of "bridging" is inferred but not directly demonstrated. No control experiments with a non-DNA-binding protein or with DNA alone at matched ionic conditions are described.
- **Why it matters** The claim that NANOG modulates DNA rheology through bridging is central to the proposed biological mechanism. Without robust quantitative evidence and appropriate controls, this claim is not established.
- **Resolution test** Provide quantitative rheological data (e.g., MSD exponents, viscosity, elastic modulus) with error bars and statistical tests. Include control experiments with DNA alone, with a non-specific protein, and with a DNA-binding-deficient mutant. Directly test bridging (e.g., via single-molecule imaging or sedimentation assays).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "aging occurs in WT and N51A, but not in W10A, indicating that oligomerization is sufficient to drive slow restructuring toward gel-like states."
- **Evidence pointer** Figure 4a-4d; Results section "Results"
- **Concern** The aging data are presented as time-dependent increases in viscosity and elasticity, but the timescales, magnitudes, and statistical significance are not quantified. The claim that W10A "remains in a viscous-dominated state" is based on a single time point or qualitative observation. The relationship between aging in DNA-NANOG mixtures and the macroscopic gelation observed at higher concentrations is not clarified.
- **Why it matters** The aging behavior is a key part of the proposed mechanism for "mechanical memory." If the aging is not robustly characterized, this aspect of the model is unsupported.
- **Resolution test** Provide time-resolved rheological data with quantitative metrics (e.g., viscosity vs. time curves, aging exponents) for all three variants, with replicates and statistical analysis. Clarify the relationship between the aging observed in DNA mixtures and the gelation at high protein concentration.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors speculate that NANOG's gel-like properties "may provide a physical basis for stabilizing long-range chromatin interactions and enhancer-promoter contacts, thereby contributing to transcriptional regulation in pluripotent cells."
- **Evidence pointer** Conclusions section
- **Concern** This is the central biological claim of the paper, but it is entirely speculative. No in vivo experiments are presented to test whether NANOG forms microgels in cells, whether these affect chromatin dynamics, or whether this mechanism contributes to transcriptional regulation. The authors acknowledge this limitation but do not provide a clear experimental roadmap to test the hypothesis.
- **Why it matters** The broader significance of the work depends on the biological relevance of the observed in vitro phenomena. Without any in vivo validation, the claim remains a hypothesis.
- **Resolution test** Provide preliminary in vivo data (e.g., imaging of NANOG clusters in embryonic stem cells, measurement of chromatin dynamics at NANOG-bound loci) or clearly frame the work as an in vitro biophysical study with the biological relevance as a testable hypothesis for future work.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that NANOG "forms macroscopic aging gels" and "microgel-like structures" without clearly distinguishing between these two phenomena. The relationship between the macroscopic gel (at 1 mM) and the microgel (in DNA mixtures at 7.9 µM) is not explained.
- **Required correction** Clarify the distinction between macroscopic gelation and microgel formation, and specify the concentration regimes in which each occurs.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Results section "Results"
- **Issue** The text states that simulations were performed using the Mpiri framework with specific parameters, but the full simulation protocol (e.g., box size, equilibration time, number of replicates, analysis methods) is not described in the main text. The authors refer to the SI, but this was not provided.
- **Required correction** Provide a summary of the simulation protocol in the main text or ensure the SI is accessible and contains all necessary details.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1c
- **Issue** The qualitative observation of gel formation (Figure 1c) is described as "sol-gel transition" but no quantitative measure (e.g., tube inversion angle, rheological criterion) is provided.
- **Required correction** Define the operational criterion for gel formation and provide quantitative confirmation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "Results"
- **Issue** The authors state that the lack of gelation at room temperature "indicates that the aging process is driven by WR re-configuration and exploration of a rugged free energy landscape." This is a plausible interpretation but is not directly tested.
- **Required correction** Acknowledge this as a hypothesis and suggest experiments (e.g., temperature-dependent rheology, mutation of specific tryptophan residues) to test it.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction cites relevant literature on phase separation and IDPs but does not discuss prior work on transcription factor oligomerization or DNA bridging in detail.
- **Required correction** Add a brief discussion of prior studies on TF oligomerization and DNA crosslinking to contextualize the novelty of the findings.

## Risk / unsupported claims
- The claim that NANOG forms "macroscopic aging gels" is supported by qualitative observations but lacks quantitative rheological validation.
- The claim that NANOG forms "self-limited micelle-like clusters" with a specific size is based on simulations and preliminary experiments, but quantitative comparisons are missing.
- The claim that NANOG modulates DNA rheology via bridging is inferred from microrheology but not directly demonstrated.
- The claim that aging in DNA-NANOG mixtures is driven by oligomerization is supported by the W10A control but lacks detailed time-resolved data.
- The biological relevance of the observed in vitro phenomena to transcriptional regulation in embryonic stem cells is entirely speculative and not tested experimentally.