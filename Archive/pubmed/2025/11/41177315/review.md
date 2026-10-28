## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report that the CM18-TAT11 cell-penetrating peptide can deliver an HIV-1 Nef(mut)-Tat DNA vaccine construct, based on bioinformatics predictions, molecular dynamics simulations, in vitro transfection studies in HEK-293T cells, and in vivo immunization in mice, with evidence of Th1 and CTL-mediated cellular immunity.
- **Visible evidence base** Abstract text only; no numerical data, statistical analyses, figure legends, or methodological details provided
- **Missing materials affecting confidence** Full methods, all figures and tables, statistical details, animal numbers, experimental replicates, raw data, and any supplementary information

## Reviewer

- **Overall assessment** The abstract presents a plausible and potentially useful application of a known cell-penetrating peptide for DNA vaccine delivery. The workflow from computational prediction to in vitro and in vivo evaluation is logical. However, the abstract lacks quantitative results, statistical support, and methodological detail, making it impossible to assess the robustness of the claims. The conclusion that CM18-TAT11 is a "promising" delivery system is reasonable as a preliminary statement but is not fully established from the evidence summarized here.
- **Who would be interested in the results, and why** Researchers in DNA vaccine development, non-viral gene delivery, HIV vaccine design, and cell-penetrating peptide applications would find these results relevant. The work addresses a recognized limitation of DNA vaccines, namely poor transfection and immunogenicity, and offers a peptide-based delivery strategy that could be adapted to other antigens.
- **Major strengths** The study integrates computational, in vitro, and in vivo approaches, which strengthens the translational relevance. The use of a well-characterized CPP (CM18-TAT11) with prior literature support adds credibility. The focus on cellular immunity, particularly CTL responses, is appropriate for an HIV therapeutic vaccine context.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide quantitative data for any of the key claims, including transfection efficiency, particle size, zeta potential, antibody titers, cytokine levels, or CTL activity. Without these data, the case for efficacy is not established. Additionally, the absence of statistical methods and group sizes prevents assessment of biological significance.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The use of CM18-TAT11 for DNA vaccine delivery is not entirely novel, as CPPs have been explored for this purpose, but the specific application to an HIV-1 Nef(mut)-Tat construct may offer some new insight.
  - Scientific importance: Moderate. Improving DNA vaccine delivery is a relevant goal, but the abstract does not demonstrate a major advance over existing delivery systems.
  - Interdisciplinary readership: Limited. The work is primarily of interest to vaccine and gene delivery specialists, with less broad appeal.
  - Technical soundness: Not assessable from the abstract. Key experimental details and quantitative outcomes are missing.
  - Readability for nonspecialists: The abstract is generally clear, but terms such as N/P ratio and CTL activity may require prior knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests potential, but the lack of quantitative results and methodological transparency prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that CM18-TAT11 effectively condensed pDNA into nano-sized particles that induced no cytotoxicity and facilitated delivery into HEK-293T cells at an N/P ratio of 2:1.
- **Evidence pointer** Abstract, in vitro analysis section; location not provided
- **Concern** The abstract states that nanoparticles were formed and transfection was achieved, but no numerical values are given for particle size, zeta potential, transfection efficiency, or cytotoxicity. The claim of "no cytotoxicity" is absolute and requires quantitative support.
- **Why it matters** Without quantitative data, the reader cannot evaluate whether the delivery efficiency is competitive with existing methods or whether the cytotoxicity claim is justified. This is central to the paper's premise.
- **Resolution test** Provide specific values for particle size, polydispersity index, zeta potential, transfection percentage, and cell viability, with appropriate statistical comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that in vivo immunization with pDNA/CM18-TAT11 nanoparticles significantly elicited robust Th1 and CTL-mediated cellular immunity.
- **Evidence pointer** Abstract, in vivo analysis section; location not provided
- **Concern** The term "significantly" implies statistical testing, but no p-values, effect sizes, or group comparisons are reported. The claim of "robust" immunity is subjective without quantitative immune response data.
- **Why it matters** The central conclusion of the paper rests on the in vivo immunogenicity data. Without quantitative outcomes, the claim of efficacy cannot be verified or compared to other delivery systems.
- **Resolution test** Report antibody titers, cytokine concentrations, and CTL lysis percentages with statistical analysis and group sizes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that MD simulations revealed interaction of CM18-TAT11 with DNA saturated rather quickly, characterized by two distinct binding patterns.
- **Evidence pointer** Abstract, MD simulation section; location not provided
- **Concern** No details are provided on simulation parameters, force fields, system size, simulation time, or how the "two distinct binding patterns" were defined. The claim is not reproducible from the abstract.
- **Why it matters** Computational results are only meaningful if the methodology is transparent. Without these details, the simulation findings cannot be evaluated or replicated.
- **Resolution test** Provide simulation methods, convergence criteria, and a clear definition of the binding patterns, ideally with representative figures.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, bioinformatics analysis claim
- **Evidence pointer** Abstract, bioinformatics analysis section; location not provided
- **Issue** The claim that CM18-TAT11 has "minimal toxicity" and "low immunogenicity" is based on web server predictions, but the specific tools and prediction scores are not mentioned.
- **Required correction** Name the prediction servers and provide the relevant scores or confidence levels.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract, in vivo study design
- **Evidence pointer** Abstract, in vivo analysis section; location not provided
- **Issue** The abstract does not specify the mouse strain, number of animals per group, immunization route, dose, or schedule.
- **Required correction** Include these details in the abstract or indicate that they are in the full methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Abstract, conclusion
- **Evidence pointer** Abstract, final sentence; location not provided
- **Issue** The conclusion states the system is "promising" but does not acknowledge limitations, such as the lack of comparison to other delivery systems or the absence of challenge studies.
- **Required correction** Add a sentence noting limitations or comparisons to existing delivery approaches.

## Risk / unsupported claims

- The claim of "no cytotoxicity" is unsupported without quantitative viability data.
- The claim of "significantly elicited robust Th1 and CTL-mediated cellular immunity" is unsupported without statistical and quantitative immune data.
- The claim of "high cell-penetrating probability, minimal toxicity, and low immunogenicity" from bioinformatics is unverifiable without tool names and scores.
- The MD simulation findings are not assessable without methodological details.
- The overall conclusion of a "promising gene delivery system" is a reasonable interpretation but is not fully established from the abstract alone.