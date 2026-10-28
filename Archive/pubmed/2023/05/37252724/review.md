## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract, without access to full methods, figures, or supporting data
- **Shared manuscript claim summary** The authors use molecular dynamics simulations to compare activation mechanisms of human and mouse cGAS, proposing that sequence differences affect protein stability and DNA binding, that dimerization enhances allosteric signal transmission, and that siteB domain is key for mouse cGAS activation while siteA domain is key for human cGAS activation.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary material provided
- **Missing materials affecting confidence** Full methods, simulation parameters, force field choices, system setup, convergence criteria, structural analyses, statistical validation, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting computational study addressing a clinically relevant species difference in cGAS activation. However, the claims are broad and mechanistic, and the abstract alone provides insufficient detail to evaluate the technical rigor, statistical robustness, or validity of the conclusions. The central mechanistic claims, particularly the differential roles of siteA and siteB domains, are not supported by any quantitative evidence visible in the supplied material.
- **Who would be interested in the results, and why** Researchers in innate immunity, structural biology, and computational biophysics would be interested. The work addresses a practical problem in drug development, namely the species-specific efficacy of cGAS inhibitors, and could inform future design of human-specific therapeutics. Computational biophysicists studying protein-DNA interactions and allostery may also find the methodological approach relevant.
- **Major strengths** The study addresses a clinically important and under-explored question regarding species differences in cGAS activation. The use of multiple cGAS variants, including human mutations, is a sensible design. The focus on allosteric communication between DNA-binding interfaces and the catalytic pocket is mechanistically meaningful.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not report any quantitative measures of structural stability, DNA-binding affinity, or allosteric correlation. Without these, the central claims cannot be evaluated. The absence of methodological details, such as simulation length, force field, and convergence assessment, prevents verification of technical soundness.
- **Assessment against Nature-style criteria** Originality is moderate, as the species difference in cGAS is known and the use of MD to study it is not unprecedented. Scientific importance is potentially high given the drug development context, but the abstract does not establish a definitive advance. Interdisciplinary readership is plausible, but the abstract is written for a specialist audience and does not explain the biological significance in accessible terms. Technical soundness cannot be assessed from the abstract alone. Readability for nonspecialists is limited, as terms such as siteA and siteB domains are introduced without context.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially valuable study, but the claims are not verifiable without full data and methods. A supportive posture would require evidence of technical rigor and quantitative support for the mechanistic conclusions.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that sequence differences between hcGAS and mcGAS directly affect protein structure stability, especially of the siteB domain.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that sequence differences affect structural stability but provides no quantitative measure, such as root-mean-square deviation, root-mean-square fluctuation, or free energy differences, to support this claim. No comparison between variants is shown.
- **Why it matters** Without quantitative stability data, the claim that sequence differences directly affect stability is unsupported. This is a foundational claim for the entire mechanistic argument.
- **Resolution test** Provide numerical stability metrics for each simulated system, with statistical error estimates, and demonstrate significant differences between hcGAS and mcGAS, particularly in the siteB domain.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that dimerization enhances correlation among distant residues and reinforces allosteric signal transmission between DNA-binding interfaces and the catalytic pocket.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract asserts enhanced allosteric communication upon dimerization but does not describe the method used to measure correlation, such as dynamic network analysis or mutual information, nor any quantitative results. No comparison between monomeric and dimeric states is presented.
- **Why it matters** This is a central mechanistic claim. Without defined metrics and statistical comparison, the claim is not verifiable and could be an artifact of the simulation setup.
- **Resolution test** Describe the correlation analysis method, report correlation values or network metrics for monomer and dimer states, and show statistically significant enhancement upon dimerization.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that siteB domain plays a prominent role in mcGAS activation, while siteA domain is key to hcGAS activation.
- **Evidence pointer** Abstract, location not provided
- **Concern** This is the main conclusion of the study, but the abstract provides no direct evidence linking specific domain dynamics to activation. The claim appears to be inferred from stability and correlation data, but the causal link to activation is not established.
- **Why it matters** The conclusion has direct implications for drug design. If the evidence is indirect or correlational, the claim may overstate the findings and mislead future research.
- **Resolution test** Provide functional or structural evidence, such as mutation effects on catalytic activity or DNA binding, that directly links siteA or siteB dynamics to activation in each species.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract text
- **Evidence pointer** Abstract, location not provided
- **Issue** The terms siteA and siteB domains are introduced without definition or context, which may confuse readers unfamiliar with cGAS structure.
- **Required correction** Briefly define these domains in the abstract or refer to established nomenclature with a structural description.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Simulation methodology
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not mention simulation length, force field, or number of replicates, which are essential for evaluating the reliability of MD results.
- **Required correction** Include key simulation parameters in the abstract or state that full details are in the methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Clinical relevance
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions drug development implications but does not explain how the findings could inform inhibitor design, leaving the translational relevance vague.
- **Required correction** Add a sentence connecting the mechanistic differences to specific implications for drug design or species-specific efficacy.

## Risk / unsupported claims
- The claim that sequence differences directly affect protein structure stability is unsupported without quantitative stability data.
- The claim that dimerization enhances allosteric signal transmission is unsupported without defined correlation metrics and statistical comparison.
- The conclusion that siteB is key for mouse cGAS activation and siteA for human cGAS activation is not directly supported by the abstract evidence.
- The claim that conformational fluctuations correlate with catalytic capacity regulation is not substantiated with any data.
- The overall mechanistic model of activation differences is not verifiable from the abstract alone.