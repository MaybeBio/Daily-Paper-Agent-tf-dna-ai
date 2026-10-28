## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report molecular dynamics simulations of the SRY-DNA complex for the wild-type protein and two clinically identified mutants, I13T and G40R. They claim that the mutants destabilize the complex, consistent with prior in vitro assays, and that altered DNA bending contributes to the observed disorders. Potential of mean force calculations over short separation distances are stated to confirm higher stability of the wild-type complex.
- **Visible evidence base** Abstract text only; no numerical data, simulation parameters, convergence metrics, or methodological details are provided
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, system setup, trajectory analysis details, PMF methodology, error estimates, and all figures or tables

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially valuable computational study addressing a clinically relevant question, namely how two naturally occurring point mutations in SRY affect its DNA-binding complex. The topic is of interest to biophysicists and structural biologists. However, the abstract alone provides insufficient detail to evaluate the technical soundness of the simulations, the robustness of the PMF calculations, or the strength of the link between simulated destabilization and clinical phenotypes. The claims are reasonable but currently not verifiable from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational biophysics, protein-DNA interactions, and molecular mechanisms of sex development disorders would find these results relevant. The study also speaks to the broader question of how single-point mutations alter transcription factor binding dynamics, which is of interest to those studying transcriptional regulation and protein engineering.
- **Major strengths** The study addresses a clinically relevant problem with atomistic simulations, which can provide mechanistic insight not accessible by experimental methods alone. The use of microsecond-scale MD and PMF calculations suggests an attempt to go beyond static structures and capture dynamic and thermodynamic properties. The explicit connection to prior in vitro assays is a positive feature, as it grounds the computational findings in experimental context.
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
  - Originality: The question of how SRY mutations affect DNA binding is not entirely new, but the specific use of long-timescale MD and PMF to compare wild-type and two mutants may offer a fresh perspective. The originality is moderate and depends on whether the full study provides new mechanistic insight beyond prior experimental work.  
  - Scientific importance: The topic is clinically relevant, but the importance is limited by the narrow scope of two mutants and one transcription factor. The broader implications for protein-DNA binding mechanisms are plausible but not strongly articulated in the abstract.  
  - Interdisciplinary readership: The work would appeal primarily to computational biophysicists and structural biologists. The clinical connection may attract a wider audience, but the abstract does not sufficiently explain the biological context for nonspecialists.  
  - Technical soundness: Cannot be assessed from the abstract. Key details on simulation convergence, force field choice, system size, sampling adequacy, and PMF methodology are absent.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses jargon such as "mus-long MD" and "potential of mean force" without explanation. The clinical relevance is stated but not elaborated.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide enough information to judge the validity of the claims. A supportive posture would require access to the full manuscript and verification of the simulation methodology and PMF calculations.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "mus-long MD" simulations were conducted and that the results suggest destabilization of the mutant complexes.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract provides no information on simulation parameters, such as force field, water model, ionic conditions, temperature and pressure coupling, simulation length, number of replicas, or convergence criteria. Without these details, it is impossible to assess whether the simulations were adequately sampled or whether the observed differences between wild-type and mutants are statistically meaningful.  
- **Why it matters** Molecular dynamics results are highly sensitive to simulation setup and sampling. If the simulations are not converged or if the force field is inappropriate for protein-DNA systems, the reported destabilization could be an artifact. The claim of "mus-long" simulations is not sufficient to establish reliability.  
- **Resolution test** Provide full simulation protocols, including force field parameters, system construction, equilibration procedure, production run lengths, and convergence analysis such as root-mean-square deviation stabilization or block error estimates. Show that the observed differences are reproducible across independent simulations or statistically significant.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence strength  
- **Claim pointer** The authors claim that "comparative potential of mean force computations, over a sequence of short separation distances for the three complexes, verified a higher stability of the normal SRY-DNA."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The PMF methodology is not described. It is unclear what reaction coordinate was used, how the separation distances were defined, whether umbrella sampling or steered MD was employed, and how the PMF profiles were computed and compared. The phrase "short separation distances" raises questions about whether the PMF covers the full dissociation pathway or only a limited range, which could bias the stability comparison.  
- **Why it matters** PMF calculations are only meaningful if the reaction coordinate is well-defined, the sampling is sufficient, and the profiles are properly converged. A limited range of separation distances may not capture the relevant free energy barrier or the overall binding affinity. The claim of "higher stability" for the wild-type complex depends critically on the quality and range of the PMF calculations.  
- **Resolution test** Describe the PMF methodology in detail, including the reaction coordinate, the range of separations sampled, the number of windows, the sampling time per window, and the error analysis. Show that the PMF profiles are converged and that the stability ranking is robust to changes in the reaction coordinate or sampling protocol.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim support  
- **Claim pointer** The authors claim that "the observed disorders brought about by the G40R-DNA and I13T-DNA may arise predominantly from the destabilization of the complex being in accord with in vitro assays found elsewhere and from modifications of the DNA bending as revealed in this study."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract states that the results are "in accord with in vitro assays found elsewhere," but no specific experimental data or citation is provided. Furthermore, the claim that DNA bending modifications contribute to the disorders is presented as a finding of this study, but no quantitative measure of DNA bending is described. The causal link between simulated structural changes and clinical phenotypes is asserted rather than demonstrated.  
- **Why it matters** The clinical relevance of the study rests on the connection between simulated molecular behavior and the observed developmental disorders. Without explicit experimental comparison or a clear metric for DNA bending, the claim that destabilization and bending changes are the "predominant" causes is speculative. The abstract does not provide enough evidence to support this causal interpretation.  
- **Resolution test** Provide specific comparisons to the cited in vitro assays, including quantitative agreement or correlation. Define the DNA bending metric used, show the values for wild-type and mutants, and demonstrate that the bending changes are statistically significant and correlate with the proposed functional impact.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract terminology  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "mus-long MD" is nonstandard and unclear. It likely means microsecond-long simulations, but the abbreviation is not defined.  
- **Required correction** Replace "mus-long MD" with "microsecond-long molecular dynamics simulations" or define the abbreviation at first use.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Contextualization  
- **Affected element** Clinical relevance  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract mentions "patients with sex developmental disorders" but does not specify the nature of the disorders or the clinical significance of the I13T and G40R mutations. This limits the accessibility of the work to a broader audience.  
- **Required correction** Add a brief sentence describing the clinical phenotype associated with these mutations and why understanding the molecular basis is important.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Claim precision  
- **Affected element** Causal language  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "may arise predominantly from" is appropriately cautious, but the abstract does not discuss alternative mechanisms or limitations of the simulation approach in establishing causality.  
- **Required correction** Add a sentence acknowledging that simulations provide correlative rather than definitive causal evidence and that experimental validation is needed to confirm the proposed mechanism.

## Risk / unsupported claims
- The claim that the mutants destabilize the SRY-DNA complex is unsupported in the abstract because no quantitative data or error analysis is provided.
- The claim that DNA bending modifications contribute to the disorders is unsupported because no bending metric or values are given.
- The claim that the results are "in accord with in vitro assays found elsewhere" is unverifiable without specific citations or data.
- The PMF-based stability ranking is unverifiable without methodological details and convergence evidence.
- The overall causal link between simulated molecular changes and clinical phenotypes is not established from the abstract alone.