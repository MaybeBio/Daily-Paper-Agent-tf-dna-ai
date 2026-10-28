## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors use SIRAH coarse-grained molecular dynamics simulations to study the CENP-A nucleosome in complex with CENP-N. They report enhanced flexibility in the N-terminal region of CENP-A, stabilization of its RG loop upon CENP-N binding, allosteric changes affecting histone-DNA contacts, minor effects on overall nucleosome stability and compactness, identification of key residue contacts via distance-based contact map analysis, and binding free energy quantification via umbrella sampling.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or simulation parameters provided
- **Missing materials affecting confidence** Full manuscript, simulation setup and parameters, force field validation details, convergence criteria, error analysis, contact map definitions, umbrella sampling protocol, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible computational study addressing an important question in centromere biology. The claims are internally consistent and the methodological approach is appropriate for the stated goals. However, the abstract alone provides insufficient detail to assess technical rigor, convergence of simulations, or robustness of the binding free energy estimates. The biological significance is framed reasonably, but the impact of the findings relative to existing literature cannot be evaluated without the full manuscript.
- **Who would be interested in the results, and why** Researchers in chromatin biology, centromere function, and chromosome segregation would be interested in the mechanistic details of CENP-A regulation by CENP-N. Computational biophysicists and method developers using coarse-grained simulations would also find value in the application of SIRAH to a nucleosome complex. The binding free energy estimates may be of interest to those studying protein-protein interactions in epigenetic contexts.
- **Major strengths** The study addresses a biologically important and mechanistically underexplored question. The use of multiple simulation approaches (long MDs, contact map analysis, umbrella sampling) provides a multi-faceted view. The claim that CENP-N binding has minor effects on overall nucleosome stability is a potentially useful counterpoint to assumptions of large-scale structural remodeling.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The authors claim that "umbrella sampling simulations quantify their binding free energy" for the CENP-A and CENP-N interaction.  
  - **Evidence pointer** Abstract; location not provided  
  - **Concern** The abstract provides no details on the umbrella sampling protocol, including the reaction coordinate, number of windows, sampling time per window, convergence assessment, or error estimates. Without these, the reliability of the reported binding free energy cannot be evaluated.  
  - **Why it matters** Binding free energy values from simulations are highly sensitive to setup and convergence. If the estimate is not rigorously validated, the quantitative claim may be misleading to readers who cannot assess its accuracy.  
  - **Resolution test** Provide in the full manuscript the complete umbrella sampling setup, convergence plots, and statistical uncertainties. If the free energy is a central quantitative result, a comparison with experimental values or independent computational estimates would strengthen the claim.  
  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The authors claim "enhanced flexibility in the N-terminal region of CENP-A and the stabilization of its RG loop in the complex with CENP-N."  
  - **Evidence pointer** Abstract; location not provided  
  - **Concern** The abstract does not specify how flexibility and stabilization were quantified, nor how many independent simulations were performed to establish reproducibility. Coarse-grained simulations can produce conformational changes that are not converged within the simulation time, and the absence of convergence criteria or replicate information undermines confidence in these structural claims.  
  - **Why it matters** The central mechanistic claims rest on observed conformational changes. If these are not robust across replicates or sufficiently converged, the conclusions may be artifacts of limited sampling.  
  - **Resolution test** In the full manuscript, report the number of replicates, simulation lengths, convergence metrics (e.g., RMSD stabilization, block averaging), and statistical analysis of flexibility measures. Show that the observed changes are consistent across replicates.  
  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Scientific importance  
  - **Claim pointer** The authors state that the allosteric changes "have rather minor effects on the overall stability of the nucleosome and its compactness."  
  - **Evidence pointer** Abstract; location not provided  
  - **Concern** The abstract does not clarify what metrics were used to define stability and compactness, nor how these were compared between the free and bound states. The phrase "rather minor" is vague and lacks quantitative context.  
  - **Why it matters** This claim is potentially important because it challenges assumptions about CENP-N function. Without quantitative definitions and statistical comparison, the claim is not falsifiable from the abstract.  
  - **Resolution test** Provide specific metrics (e.g., RMSD, radius of gyration, contact probabilities) with numerical values and statistical significance tests comparing the two states in the full manuscript.
- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Readability for nonspecialists  
  - **Affected element** Abstract text  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The term "mus-long MDs" is unclear and likely a typographical or formatting artifact.  
  - **Required correction** Replace with a clear description such as "microsecond-long molecular dynamics simulations" or specify the actual simulation length.  
  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Technical soundness  
  - **Affected element** Contact map analysis  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The abstract states that "distance-based contact map analysis further elucidates key residues" but does not specify the distance cutoff or the criteria for defining a contact.  
  - **Required correction** In the full manuscript, define the contact criteria explicitly and justify the chosen cutoff.  
  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Scientific importance  
  - **Affected element** Contextualization  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The abstract does not mention how these findings compare with previous experimental or computational studies on CENP-A and CENP-N interactions.  
  - **Required correction** Add a sentence in the abstract or introduction that situates the findings relative to existing knowledge, particularly any prior structural or binding data.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking because the quantitative binding free energy claim and the central conformational change claims cannot be assessed without methodological detail and convergence evidence. R1-M3 is important but not blocking if the full manuscript provides quantitative metrics.

## Assessment against Nature-style criteria
- **Originality** The application of SIRAH coarse-grained simulations to the CENP-A nucleosome-CENP-N complex appears novel, and the focus on allosteric effects is a reasonable contribution. However, the abstract does not demonstrate how this extends beyond prior computational studies of nucleosome dynamics.
- **Scientific importance** The question of how CENP-N regulates CENP-A is of clear biological relevance. The claim of minor effects on overall stability is potentially interesting but needs quantitative support to be impactful.
- **Interdisciplinary readership** The topic bridges chromatin biology and computational biophysics, which could attract readers from both communities. The abstract is accessible but uses jargon that may limit broader appeal.
- **Technical soundness** Not assessable from the abstract alone. The blocking concerns above must be resolved to establish technical credibility.
- **Readability for nonspecialists** The abstract is generally clear but contains undefined terms and lacks context for the significance of the findings. The "mus-long" typo detracts from professionalism.

## Recommendation posture
Supportive if technical concerns are resolved. The biological question is important and the methodological approach is appropriate, but the abstract does not provide sufficient evidence to establish the central claims. The full manuscript must demonstrate convergence, statistical rigor, and quantitative definitions to support the conclusions. Currently, the case is not established from the provided evidence.

## Risk / unsupported claims
- The binding free energy value is unsupported without protocol details and error analysis.
- The enhanced flexibility and RG loop stabilization claims are unsupported without convergence and replicate information.
- The claim of minor effects on nucleosome stability and compactness is unsupported without quantitative metrics.
- The identification of key residue contacts is unsupported without contact criteria definitions.
- Any implied biological regulatory mechanism beyond the described conformational changes is not supported by the abstract.