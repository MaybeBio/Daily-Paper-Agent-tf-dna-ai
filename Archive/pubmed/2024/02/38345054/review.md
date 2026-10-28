## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose an allosteric mechanism for the MntR transcription factor from *Halalkalibacterium halodurans*, activated by Mn(2+) binding, based on long-range all-atom molecular dynamics simulations (500 ns to 1.25 microseconds). They report that Mn(2+) binding alters the non-covalent interaction network, leading to conformational changes that primarily affect DNA-binding domain positions and thereby DNA-binding affinity. Key residues are identified and their roles computationally confirmed via in silico mutants.
- **Visible evidence base** Abstract text only; no simulation details, structural coordinates, trajectory analyses, or mutant validation data are provided
- **Missing materials affecting confidence** Full manuscript, methods section, simulation parameters, force field details, convergence criteria, structural figures, quantitative results, mutant design rationale, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible computational study of an allosteric mechanism in a bacterial transcription factor. The topic is of interest to the structural biology and metalloregulation communities. However, the abstract alone provides insufficient detail to evaluate the technical rigor of the simulations, the robustness of the proposed mechanism, or the validity of the mutant-based confirmation. The claims are broad relative to the evidence presented, and several key aspects are not assessable from the supplied material.
- **Who would be interested in the results, and why** Researchers studying metal-dependent transcription factors, allosteric regulation in prokaryotes, and molecular dynamics approaches to protein conformational change. The industrial relevance of *H. halodurans* enzymes may also attract applied microbiologists interested in regulatory mechanisms in alkalophilic organisms.
- **Major strengths** The study addresses a mechanistically important question in metalloregulation. The use of long-range simulations (up to 1.25 microseconds) is appropriate for capturing conformational transitions. The inclusion of in silico mutants to test the proposed mechanism is a constructive approach.
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
  - **Originality** The proposed allosteric mechanism may be novel for MntR in this organism, but the abstract does not establish how it differs from known MntR mechanisms in other bacteria. Originality is plausible but not demonstrated.  
  - **Scientific importance** The work has potential relevance to understanding metal homeostasis regulation, but the abstract does not articulate broader implications beyond the specific system.  
  - **Interdisciplinary readership** The topic bridges structural biology, computational biophysics, and microbiology. However, the abstract is written in a way that assumes familiarity with MntR and allostery, limiting accessibility.  
  - **Technical soundness** Not assessable from the abstract. No simulation details, validation metrics, or statistical analyses are provided.  
  - **Readability for nonspecialists** The abstract is concise but uses domain-specific terminology without sufficient context. The mechanistic description is clear at a high level but lacks explanatory depth.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially interesting study, but the technical basis and the strength of the claims cannot be evaluated without the full manuscript.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that "simulations revealed an allosteric mechanism which is activated by Mn(2+) binding" and that this mechanism "leads to a conformational change that primarily affects the positions of the DNA binding domains."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract provides no information on simulation methodology, including force field parameters, water model, ionic conditions, temperature/pressure coupling, equilibration protocols, or convergence assessment. Without these details, the reliability of the simulated conformational changes cannot be evaluated.  
- **Why it matters** Allosteric mechanisms inferred from MD simulations are highly sensitive to simulation setup and sampling quality. If the simulations are not converged or the force field is inappropriate for the metal-binding site, the proposed mechanism could be an artifact.  
- **Resolution test** Provide full methods, including simulation parameters, convergence metrics (e.g., RMSD stability, principal component analysis, replica or independent run consistency), and validation of the Mn(2+) coordination geometry against known structures or experimental data.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence strength  
- **Claim pointer** The abstract claims that "the key amino acid residues of the proposed mechanism were identified and their role in the proposed mechanism was computationally confirmed by MD simulations of in silico mutants."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** No information is given on which residues were mutated, how the mutations were designed, what the expected effect was, or how the mutant simulations differed from the wild type. The term "computationally confirmed" implies a quantitative comparison that is not described.  
- **Why it matters** Mutational analysis is a central pillar of the proposed mechanism. Without details on the mutant phenotypes (e.g., loss of allosteric response, altered DNA-binding domain dynamics), the claim of confirmation is unsupported.  
- **Resolution test** Specify the mutated residues, the rationale for their selection, and the quantitative differences observed between wild-type and mutant simulations (e.g., domain displacement, interaction network changes, free energy estimates).

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim scope  
- **Claim pointer** The abstract states that Mn(2+) binding "alters the non-covalent interaction network of the protein structure which leads to a conformational change that primarily affects the positions of the DNA binding domains and, consequently, the DNA binding affinity."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract asserts a direct link between conformational change and DNA-binding affinity, but no binding free energy calculations, experimental binding data, or even qualitative estimates of affinity changes are presented. The phrase "consequently" implies a causal relationship that is not demonstrated.  
- **Why it matters** The functional significance of the proposed allosteric mechanism depends on demonstrating that the conformational change actually affects DNA binding. Without any affinity-related evidence, the biological relevance of the mechanism remains speculative.  
- **Resolution test** Provide either computational binding free energy estimates (e.g., MM-PBSA, FEP) or experimental DNA-binding data (e.g., EMSA, ITC) for wild-type and mutant proteins, or clearly state that affinity changes are inferred rather than measured.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The phrase "industrially important alkalophilic bacteria" is grammatically awkward and the industrial relevance is not connected to the study's purpose.  
- **Required correction** Rephrase to clarify the industrial context and its relevance to the regulatory mechanism studied.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract scope  
- **Evidence pointer** Abstract, final sentence  
- **Issue** The abstract does not state whether any experimental validation was performed or is planned, which would strengthen the claims.  
- **Required correction** Add a sentence indicating whether experimental validation exists or is proposed.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Simulation details  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract mentions "long range all-atom molecular dynamics simulations" but does not specify the number of replicates or whether independent simulations were performed.  
- **Required correction** State the number of independent simulations and whether results were consistent across replicates.

## Risk / unsupported claims
- The claim that Mn(2+) binding "leads to a conformational change that primarily affects the positions of the DNA binding domains" is unsupported without structural or dynamic data showing the magnitude and direction of domain movement.
- The claim that the proposed mechanism "consequently" affects DNA-binding affinity is unsupported; no affinity data are presented.
- The claim that key residues were "computationally confirmed" is unsupported without details on mutant design and comparative simulation outcomes.
- The overall allosteric mechanism is presented as established, but the abstract provides no quantitative evidence (e.g., free energy differences, domain displacement values, interaction energy changes) to support it.