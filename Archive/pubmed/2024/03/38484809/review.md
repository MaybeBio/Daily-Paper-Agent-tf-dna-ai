## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the supplied abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose a mechanistic explanation for why the CXC domain of CHT7, a regulator of quiescence repression in *Chlamydomonas reinhardtii*, is restrained from participating in transcriptional activities. They report that CHT7-CXC exhibits sequence-selective DNA binding through differential subdomain affinities, and that steric constraints, modeled by fusing CHT7-CXC with AsLOV2, limit the domain's DNA binding stability. They infer that such steric forces may explain how algal cells withhold CHT7-CXC from quiescence repression.
- **Visible evidence base** Biophysical experiments and molecular dynamics approaches, as described in the abstract; specific methods, data, and statistical analyses are not provided
- **Missing materials affecting confidence** Full text, experimental protocols, quantitative results, figures, tables, statistical details, and any supplementary information

## Reviewer
- **Overall assessment** The abstract addresses a focused and mechanistically interesting question regarding the functional restraint of the CHT7-CXC domain. The proposed hypothesis, that steric constraints limit DNA binding and thereby prevent CXC from engaging in transcriptional activities, is plausible and testable. However, the abstract provides insufficient experimental detail to evaluate the robustness of the claims. Key quantitative outcomes, controls, and the logical link between the AsLOV2 fusion experiments and the in vivo quiescence context are not described. The conclusion that steric forces explain the cellular restraint of CXC is currently under-supported by the visible evidence.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation in algae, particularly quiescence and stress responses in *Chlamydomonas reinhardtii*, as well as those interested in the structure-function relationships of DNA-binding domains and the role of steric regulation in protein-nucleic acid interactions. The biophysical and computational approach may also appeal to investigators in protein dynamics and molecular recognition.
- **Major strengths** The question is well-motivated by prior findings that the CXC domain is dispensable for CHT7 activity despite the presence of CXC binding regions in misregulated gene promoters. The combination of biophysical experiments and molecular dynamics is appropriate for probing DNA recognition behavior. The use of AsLOV2 to create spatial constraints is a creative approach to test the steric hypothesis.
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
  **Originality** The question of why a DNA-binding domain is functionally restrained is somewhat novel, but the conceptual framework, steric hindrance limiting protein function, is not new. The specific application to CHT7-CXC is original.  
  **Scientific importance** The findings may clarify the regulatory logic of quiescence in a model alga, but the broader significance beyond this system is not established from the abstract.  
  **Interdisciplinary readership** The topic is likely to interest plant and algal biologists, biophysicists, and computational biologists, but the abstract does not frame the work for a broad audience.  
  **Technical soundness** Cannot be assessed from the abstract alone. The described methods are appropriate in principle, but the absence of quantitative data and controls prevents evaluation.  
  **Readability for nonspecialists** The abstract is reasonably clear but uses domain-specific terminology without sufficient context. The logical flow from observation to hypothesis to conclusion is understandable, though the mechanistic link is not fully articulated.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and the approach is reasonable, but the abstract lacks the quantitative and methodological detail needed to support the central claim. Supportive if technical concerns are resolved in the full manuscript.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that CHT7-CXC possesses sequence selectivity due to the differential binding abilities of its subdomains.  
- **Evidence pointer** Biophysical experiments and molecular dynamics approaches, location not provided  
- **Concern** The abstract states that sequence selectivity arises from differential subdomain binding abilities, but no quantitative data, such as binding affinities, dissociation constants, or comparative measurements across subdomains, are presented. It is unclear how many subdomains were tested, what DNA sequences were used, or how selectivity was defined and measured.  
- **Why it matters** The claim of sequence selectivity is foundational to the mechanistic argument. Without quantitative evidence, the reader cannot assess whether the observed binding differences are significant or biologically meaningful.  
- **Resolution test** Provide binding affinity measurements for each subdomain against a panel of DNA sequences, including the promoter regions of misregulated genes in cht7 mutants, with appropriate statistical comparisons and controls.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Logical inference  
- **Claim pointer** The authors claim that limited ability of CHT7-CXC to withstand steric forces provides insights into why algal cells hold back CHT7-CXC's involvement in quiescence repression.  
- **Evidence pointer** AsLOV2 fusion experiments, location not provided  
- **Concern** The abstract does not describe how the AsLOV2 fusion experiments were designed, what conformational changes were induced, or how DNA binding stability was measured under spatial constraint. The leap from in vitro steric effects to in vivo cellular restraint is not justified without evidence that such steric constraints exist in the cellular environment or that the fusion system accurately mimics the native context.  
- **Why it matters** The central conclusion of the paper rests on this inference. If the steric constraint model does not reflect the in vivo situation, the mechanistic explanation is unsupported.  
- **Resolution test** Show that the steric effects observed in the AsLOV2 system are comparable to conditions expected in the cell, or provide complementary in vivo or in cellulo data demonstrating that CXC is physically constrained in a manner consistent with the model.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency  
- **Claim pointer** The authors claim that molecular dynamics approaches were used to study DNA recognition behavior.  
- **Evidence pointer** Molecular dynamics approaches, location not provided  
- **Concern** No details are given regarding the simulation system, force field, timescales, or analysis criteria. It is impossible to evaluate whether the simulations were sufficiently converged, whether the results are reproducible, or whether the computational findings corroborate the biophysical data.  
- **Why it matters** Molecular dynamics results are only meaningful if the simulation setup and analysis are rigorous. Without this information, the computational component of the study cannot be assessed.  
- **Resolution test** Describe the simulation parameters, system construction, equilibration and production run lengths, and the specific metrics used to assess DNA binding stability and subdomain behavior.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Title  
- **Evidence pointer** Title, location not provided  
- **Issue** The title contains grammatical and stylistic issues, including "it's" instead of "its" and the phrase "restrains the involvement of it's CXC domain from quiescence repression," which is awkward and potentially ambiguous.  
- **Required correction** Revise the title for grammatical accuracy and clarity, for example, "A mechanistic insight into how compromised hydrolysis of triacylglycerol 7 (CHT7) restrains its CXC domain from quiescence repression."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Contextual framing  
- **Affected element** Background  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not explain what CHT7's predicted protein domains are or how they are proposed to bind other repressors. This context is necessary to understand why the CXC domain's restraint is mechanistically significant.  
- **Required correction** Briefly describe the predicted domains and the proposed regulatory model involving other repressors to frame the question more clearly.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "compromised hydrolysis of triacylglycerol 7" is used in the title but not explained in the abstract. The relationship between triacylglycerol hydrolysis and quiescence repression is unclear.  
- **Required correction** Define or clarify the acronym CHT7 and its connection to triacylglycerol hydrolysis in the abstract, or avoid the full phrase if it is not central to the study.

## Risk / unsupported claims
- The claim that CHT7-CXC possesses sequence selectivity due to differential subdomain binding abilities is unsupported by quantitative data in the abstract.
- The claim that steric forces, modeled by AsLOV2 fusion, explain the cellular restraint of CHT7-CXC is unsupported without evidence that the in vitro system reflects in vivo conditions.
- The molecular dynamics results are not assessable due to the absence of methodological details.
- The broader relevance of the findings to quiescence regulation in *Chlamydomonas reinhardtii* is asserted but not demonstrated in the abstract.