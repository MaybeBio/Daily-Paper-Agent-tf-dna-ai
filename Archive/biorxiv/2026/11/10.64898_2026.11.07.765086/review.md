## Review setup
- **Input scope** Full manuscript text (abstract and body as provided)
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality based solely on the supplied material
- **Shared manuscript claim summary** The authors claim that protamine, an arginine-rich intrinsically disordered protein, binds DNA with nucleobase specificity, preferring GC over AT in the major groove and AT over GC in the minor groove, with a net GC bias, as demonstrated by all-atom molecular dynamics simulations and supported by experimental aggregation assays.
- **Visible evidence base** Simulation results (35-bp and 20-bp DNA), free-energy calculations, and experimental aggregation data with designed DNA sequences of 0–40% GC content.
- **Missing materials affecting confidence** No figures, tables, simulation parameters, force field details, error estimates, statistical analyses, or experimental protocols are provided. The manuscript text alone is insufficient to verify quantitative claims.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and interesting question about whether intrinsically disordered proteins can exhibit DNA sequence specificity. The central claim, that protamine shows nucleobase-specific binding with a net GC preference, is plausible and potentially significant. However, the provided material lacks the methodological detail and quantitative evidence needed to assess the robustness of the simulations and experiments. The claim of experimental validation is particularly under-supported, as no data are shown. The work is not yet established from the supplied evidence.
- **Who would be interested in the results, and why** Researchers in chromatin biology, sperm biology, and intrinsically disordered protein function would be interested. The findings could inform understanding of protamine-mediated DNA compaction and transcriptional silencing, and more broadly, whether IDPs can achieve sequence-specific recognition, which has implications for protein-DNA interaction paradigms.
- **Major strengths** The question is well-framed and addresses a gap in the literature on IDP-DNA interactions. The use of all-atom simulations to probe groove-specific preferences is a reasonable approach. The design of experimental sequences with varying GC content and G-tract shuffling is a thoughtful strategy to test the simulation predictions.
- **Major Concerns**  
  - **Concern ID** R1-M1  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Technical soundness  
    **Claim pointer** The claim that protamine prefers GC over AT in the major groove by a 2.6-to-1 ratio and AT over GC in the minor groove by a 2.1-to-1 ratio.  
    **Evidence pointer** Simulation results, location not provided  
    **Concern** The quantitative ratios are presented without any supporting data, such as histograms, error bars, or statistical tests. No information is given on how these ratios were computed, how many independent simulations were run, or how sampling convergence was assessed.  
    **Why it matters** Without error estimates and methodological detail, the precision of the claimed ratios cannot be evaluated, and the reader cannot determine whether the preferences are statistically robust or artifacts of limited sampling.  
    **Resolution test** Provide a detailed description of the simulation protocol, including force field, water model, salt concentration, simulation length, number of replicates, and analysis methods. Show distributions of interaction frequencies with error bars and statistical significance tests.  
  - **Concern ID** R1-M2  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Evidence quality  
    **Claim pointer** The claim that experimental validation with DNA sequences of 0–40% GC content shows increasing aggregation propensity at higher GC content and upon shuffling into G-tracts.  
    **Evidence pointer** Experimental validation, location not provided  
    **Concern** No experimental data are shown. The text states that aggregates form with increasing propensity, but no quantification, representative images, or statistical analysis are provided. The link between aggregation propensity and nucleobase-specific binding is asserted but not demonstrated.  
    **Why it matters** The experimental results are presented as validation of the simulation findings, but without data, the claim is unsupported. Aggregation could arise from non-specific effects, such as charge neutralization, rather than sequence-specific recognition.  
    **Resolution test** Provide raw data, such as turbidity measurements, dynamic light scattering, or microscopy images, with quantitative analysis and appropriate controls, including a non-specific protein or a scrambled sequence control.  
  - **Concern ID** R1-M3  
    **Severity** Major  
    **Blocking** No  
    **Axis** Scientific importance  
    **Claim pointer** The claim that this work demonstrates that IDPs can bind DNA in a nucleobase-specific manner, with implications for protamine-mediated transcription silencing and remodeling of paternal chromatin.  
    **Evidence pointer** Discussion, location not provided  
    **Concern** The broader implications are stated without a mechanistic link. The simulations show binding preferences in a simplified system, but the connection to transcription silencing and chromatin remodeling in vivo is speculative.  
    **Why it matters** The significance of the work depends on whether the observed preferences translate to biological function. Without experimental evidence in a cellular or chromatin context, the implications remain untested.  
    **Resolution test** Discuss how the observed binding preferences could affect nucleosome assembly or transcription factor access, and propose testable predictions for future experiments.  
- **Minor Comments**  
  - **Concern ID** R1-m1  
    **Severity** Minor  
    **Axis** Readability  
    **Affected element** Abstract  
    **Evidence pointer** Abstract, location not provided  
    **Issue** The abstract states that eight copies of protamine wrap around a 35-bp DNA molecule, but the stoichiometry and its relevance to the binding preferences are not explained.  
    **Required correction** Clarify whether the eight copies are used to mimic physiological conditions and how this affects the interpretation of the sequence preferences.  
  - **Concern ID** R1-m2  
    **Severity** Minor  
    **Axis** Technical soundness  
    **Affected element** Free-energy calculations  
    **Evidence pointer** Simulation results, location not provided  
    **Issue** The free-energy calculations are mentioned but not described. No method, such as umbrella sampling or metadynamics, is specified.  
    **Required correction** Provide details of the free-energy calculation method, including the reaction coordinate and convergence criteria.  
  - **Concern ID** R1-m3  
    **Severity** Minor  
    **Axis** Clarity  
    **Affected element** Experimental design  
    **Evidence pointer** Experimental validation, location not provided  
    **Issue** The range of 0–40% GC content is mentioned, but the rationale for this range and the number of sequences tested are not given.  
    **Required correction** Specify the number of sequences, their lengths, and the rationale for the GC content range.  
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The lack of simulation details and experimental data prevents verification of the central claims. The free-energy calculations and the stoichiometry of protamine copies also require clarification.
- **Assessment against Nature-style criteria**  
  - Originality: The question of IDP sequence specificity is novel and addresses a gap in the field. The work is original in concept.  
  - Scientific importance: Potentially high, as it could change views on IDP-DNA interactions, but the biological implications are not yet established.  
  - Interdisciplinary readership: The topic bridges biophysics, chromatin biology, and reproductive biology, which could attract a broad audience.  
  - Technical soundness: Currently insufficient. The simulation and experimental methods are not described in enough detail to assess robustness.  
  - Readability for nonspecialists: The text is generally clear, but the lack of data and methodological detail makes it difficult for nonspecialists to evaluate the claims.  
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the central claims require substantial additional detail and data. I would be supportive if the technical concerns are resolved with full methodological transparency and quantitative evidence.

## Risk / unsupported claims
- The quantitative binding ratios (2.6-to-1 and 2.1-to-1) are unsupported without simulation data and error analysis.
- The experimental validation of aggregation propensity is unsupported without any shown data.
- The claim that protamine binding preferences have implications for transcription silencing and chromatin remodeling is speculative and not directly tested.
- The free-energy calculations are mentioned but not described, making their contribution unassessable.