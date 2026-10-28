## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract, without access to full methods, figures, or supporting data
- **Shared manuscript claim summary** The authors report a combined experimental and computational study of a cationic benzo[a]phenoxazin ligand binding to a parallel c-MYC G-quadruplex (G4) DNA. They claim high binding affinity (K = (2.9 ± 0.3) x 10^7 M^-1), rapid association (k_on = (2.4 ± 0.2) x 10^9 M^-1 s^-1), and a residence time of ~10 ms from fluorescence correlation spectroscopy (FCS). Well-tempered metadynamics (WT-MetaD) and infrequent metadynamics (iMetaD) simulations are claimed to reproduce the binding free energy and residence time (~9 ms), respectively, and to reveal binding orientations and dissociation pathways. The work is framed as a generalizable multiscale framework for ligand-G4 recognition.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary information provided
- **Missing materials affecting confidence** Full manuscript, experimental methods, simulation parameters, convergence criteria, error analysis, structural models, and all primary data

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable integration of FCS and enhanced-sampling simulations to characterize ligand-G4 binding kinetics and thermodynamics. The claim of quantitative agreement between simulation and experiment for residence time is notable. However, the abstract alone provides insufficient detail to assess the robustness of the methods, the validity of the error estimates, or the generalizability of the framework. Several claims, particularly regarding simulation convergence and the mechanistic interpretation, require scrutiny against the full data.
- **Who would be interested in the results, and why** Researchers in chemical biology, biophysics, and computational chemistry focused on G-quadruplex targeting, drug residence time optimization, and the development of enhanced-sampling methods for nucleic acid-ligand interactions. The work may also interest medicinal chemists designing G4-targeted anticancer agents.
- **Major strengths** The combination of FCS with multiple metadynamics variants is a sophisticated approach that addresses both thermodynamic and kinetic aspects. The reported agreement between simulated and experimental residence times is a strong point, if substantiated. The identification of specific binding orientations and dissociation pathways provides mechanistic insight beyond simple affinity measurements.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The integration of FCS with iMetaD for residence time prediction in G4 systems appears novel, but the abstract does not clearly differentiate from prior ligand-G4 kinetic studies. Scientific importance: The focus on residence time as a design parameter is timely and relevant, but the generalizability claim is not supported by a single ligand-G4 pair. Interdisciplinary readership: The work bridges experimental biophysics and computational chemistry, which could appeal to a broad audience, but the abstract is dense and may not be accessible to nonspecialists. Technical soundness: The methods are state-of-the-art, but the abstract lacks details on convergence, force field accuracy, and error propagation, which are critical for assessing reliability. Readability for nonspecialists: The abstract uses specialized terminology without sufficient context, limiting accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved; currently not established from the provided evidence

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that WT-MetaD simulations enable reconstruction of a converged free-energy surface and that iMetaD simulations recover a ligand residence time of ~9 ms, closely matching the FCS result.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract does not provide any details on the convergence criteria for the WT-MetaD simulations, the number of iMetaD trajectories, the choice of collective variables beyond naming them, or the statistical uncertainty in the simulated residence time. Without these, the claim of quantitative agreement cannot be evaluated.  
- **Why it matters** Enhanced-sampling methods are highly sensitive to parameter choices and convergence. Overstated convergence or insufficient sampling can lead to misleading free-energy and kinetic estimates. The central claim of the paper rests on the reliability of these simulations.  
- **Resolution test** Provide convergence metrics (e.g., free-energy difference as a function of simulation time, reweighting checks), the number of independent iMetaD runs, and error bars on the simulated residence time. Show that the simulated residence time distribution is consistent with a single exponential and that the mean is robust to trajectory length.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract reports a binding affinity of K = (2.9 ± 0.3) x 10^7 M^-1 and an association rate of k_on = (2.4 ± 0.2) x 10^9 M^-1 s^-1 from FCS, with a residence time of ~10 ms.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The FCS analysis relies on a reaction-coupled diffusion model. The abstract does not specify how the model was validated, whether alternative models (e.g., pure diffusion or two-state without coupling) were tested, or how the errors were propagated. The association rate is near the diffusion limit, which raises questions about the accuracy of the concentration calibration and the assumption of a single binding site.  
- **Why it matters** FCS-derived kinetic parameters are model-dependent. If the model is misspecified, the reported k_on and residence time could be artifacts. The near-diffusion-limited k_on also requires careful control of fluorophore photophysics and sample purity.  
- **Resolution test** Provide details of the FCS model selection, including fits to autocorrelation functions under varying conditions, control experiments with non-binding ligands or mutated G4 sequences, and a clear description of how the diffusion coefficient and binding contributions were separated.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The abstract claims that the work provides a generalizable multiscale framework for ligand-G4 recognition and identifies residence time as a critical parameter for rational design.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The study is based on a single ligand and a single G4 sequence. The claim of generalizability is not supported by the evidence presented. The abstract does not discuss how the framework would transfer to other ligands with different chemical properties or to other G4 topologies (e.g., antiparallel or hybrid).  
- **Why it matters** The broader significance of the work depends on its applicability beyond the specific system studied. Without demonstration of transferability or at least a discussion of the expected limitations, the claim of a general framework is overstated.  
- **Resolution test** Either provide additional data on a second ligand or G4 sequence, or temper the claim to reflect that the framework is demonstrated for one system and outline the conditions under which it is expected to hold.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Interdisciplinary readership  
- **Claim pointer** The abstract states that the work provides a generalizable multiscale framework and that residence time may be optimized through rational design.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract is written in a way that assumes familiarity with both FCS and metadynamics. Terms such as "reaction-coupled diffusion kinetics," "well-tempered metadynamics," and "infrequent metadynamics" are used without brief explanation. This limits accessibility to readers who are not specialists in both fields.  
- **Why it matters** For a Nature-style audience, the abstract should be comprehensible to a broad scientific readership. The current level of jargon may obscure the significance of the findings.  
- **Resolution test** Revise the abstract to include brief, plain-language descriptions of the key methods and their purpose, or provide a schematic figure that illustrates the approach and findings.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Binding affinity notation  
- **Evidence pointer** Abstract text  
- **Issue** The binding constant is written as "K = (2.9 ∓ 0.3) x 10^7 M^-1" using a minus-plus sign, which is unconventional. Typically, the plus-minus sign is used for uncertainty.  
- **Required correction** Replace "∓" with "±" to avoid confusion.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Rate constant notation  
- **Evidence pointer** Abstract text  
- **Issue** The association rate is written as "k_on = (2.4 ∓ 0.2) x 10^9 M^-1 s^-1" with a subscript "on" but the preceding text uses "k_on" with a Greek kappa symbol. The notation is inconsistent.  
- **Required correction** Use a consistent notation for the rate constant throughout the abstract.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Simulation details  
- **Evidence pointer** Abstract text  
- **Issue** The abstract mentions "contact-pair-based and hydration collective variables" but does not specify the force field used for the DNA and ligand, nor the water model.  
- **Required correction** Add a brief mention of the force field and water model in the abstract or refer to the methods section for these details.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Dissociation pathway  
- **Evidence pointer** Abstract text  
- **Issue** The abstract states that dissociation occurs "through the loop region formed by T7, G8 and G9" but does not explain why this pathway is favored over others.  
- **Required correction** Provide a brief mechanistic rationale for the observed pathway, or note that the structural basis is discussed in the full manuscript.

## Risk / unsupported claims
- The claim of a "converged free-energy surface" is unsupported without convergence metrics.
- The claim that iMetaD "directly validate[s]" the FCS-derived residence time is unsupported without details on the number of trajectories and statistical uncertainty.
- The claim of a "generalizable multiscale framework" is unsupported by evidence from a single ligand-G4 pair.
- The mechanistic claim of "multiple π-stacked binding orientations" is not verifiable from the abstract alone.
- The statement that "ligand dissociation is the rate-limiting step" is a reasonable inference but is not explicitly demonstrated with independent measurements.