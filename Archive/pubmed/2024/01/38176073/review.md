## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report development of an AI and knowledge-based method for rational design of *E. coli* sigma70 promoters. Strong promoters were identified via high-throughput screening with eGFP as reporter, and features of these promoters guided design using a previously reported deep learning model. In case studies, the promoters increased collagen expression by 81.4% and microbial transglutaminase (mTG) expression by 33.4%, and enabled soluble expression of mTG-activating protease leading to active mTG production.
- **Visible evidence base** Abstract text only; no quantitative data, sequence information, model architecture, screening details, or experimental methods are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, promoter sequence data, model training and validation details, HTS methodology, strain and plasmid information, statistical analyses, and raw expression data

## Reviewer
- **Overall assessment** The abstract describes a potentially useful integrated approach combining high-throughput screening with deep learning for sigma70 promoter design. The reported expression improvements are modest but tangible, and the demonstration of soluble protease expression is a notable practical outcome. However, the abstract alone provides insufficient detail to evaluate the novelty of the method relative to existing promoter engineering tools, the robustness of the deep learning component, or the statistical significance of the reported improvements. The case studies are limited to two proteins, and no comparison against existing promoter design methods is described. The claim that the combined method "may be effective" is appropriately cautious, but the evidence base visible here does not establish the broader utility or superiority of the approach.
- **Who would be interested in the results, and why** Researchers in synthetic biology, metabolic engineering, and recombinant protein production would be interested. The work addresses a practical bottleneck in promoter engineering for *E. coli*, a widely used production host. Those developing AI-based design tools for genetic parts, and those seeking constitutive promoters for protein expression, would find the approach relevant. The demonstration with collagen and mTG, both industrially relevant proteins, broadens the appeal to biotechnology audiences.
- **Major strengths** The integration of high-throughput screening with deep learning is a sensible workflow that leverages empirical data to inform model-guided design. The use of eGFP as a reporter for promoter strength quantification is a standard and reliable approach. The case studies with two distinct proteins, including a challenging target (mTG-activating protease requiring soluble expression), provide practical validation. The reported improvements, while modest, are concrete and suggest the method has at least some predictive utility.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any statistical context for the reported 81.4% and 33.4% improvements. Without information on replicate numbers, variance, or control conditions, these values cannot be assessed for significance. The deep learning model is referenced as "previously reported," but no details are given on how it was adapted or retrained for this application, leaving the novelty of the AI component unclear. The screening methodology is described only as "high-throughput screening," with no information on library size, selection stringency, or how "strong" promoters were defined. These gaps prevent evaluation of the method's robustness and generalizability.
- **Assessment against Nature-style criteria** 
  - Originality: The combination of HTS with deep learning for promoter design is not entirely new, and the abstract does not articulate a distinct conceptual advance over existing approaches. The originality appears incremental rather than transformative.
  - Scientific importance: Promoter engineering is a relevant topic for synthetic biology, but the abstract does not demonstrate that this method solves a problem that current tools cannot address. The importance is moderate and application-specific.
  - Interdisciplinary readership: The work sits at the interface of machine learning and synthetic biology, which could attract cross-disciplinary interest. However, the abstract lacks sufficient technical detail in either domain to engage specialists from both fields deeply.
  - Technical soundness: The visible evidence is too limited to assess technical soundness. The workflow is plausible, but no data are shown to verify the claims.
  - Readability for nonspecialists: The abstract is clearly written and accessible, with jargon kept to a minimum. The logic from screening to design to validation is easy to follow.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible workflow with modest positive results, but the lack of methodological detail, statistical context, and comparison to existing methods means the core claims cannot be evaluated. A supportive posture would require access to the full manuscript and its data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the combined AI and knowledge-based method is "effective for promoter engineering," supported by increased expression of collagen (81.4%) and mTG (33.4%).
- **Evidence pointer** Abstract, case study section; location not provided
- **Concern** The abstract reports percentage improvements without any statistical context. No information is given on the number of biological replicates, standard deviations, or the baseline promoter used for comparison. The improvements could be within experimental noise, or the baseline could be a weak promoter chosen to inflate relative gains.
- **Why it matters** Without statistical validation, the central claim of method effectiveness is unsupported. Percentage changes alone do not establish that the designed promoters outperform existing strong promoters or that the improvement is reproducible.
- **Resolution test** Provide replicate numbers, error bars, statistical tests (e.g., t-test or ANOVA), and a clear description of the reference promoter used for comparison. Show that the improvements are significant and that the designed promoters are competitive with or superior to established strong sigma70 promoters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that "features of these strong promoters were adopted to guide promoter design based on our previous reported deep learning model."
- **Evidence pointer** Abstract, methods description; location not provided
- **Concern** The abstract does not describe how the deep learning model was used for design. Was the model retrained on the newly screened promoter data, or was it applied as previously published? What features were extracted from the strong promoters, and how were they incorporated into the design process? The term "knowledge-based" is also undefined, leaving the reader uncertain about what prior knowledge was used and how it was encoded.
- **Why it matters** The novelty of the method hinges on the integration of screening data with the AI model. Without clarity on the model's role and the nature of the "knowledge-based" component, the approach cannot be distinguished from simpler sequence-based design or from the previously reported model alone.
- **Resolution test** Describe the model architecture, training data, and how the screened promoter features were used. Clarify what "knowledge-based" means in this context, and provide a schematic or workflow figure showing the design pipeline.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability and comparison
- **Claim pointer** The authors imply the method is broadly useful for promoter engineering, supported by two case studies with collagen and mTG.
- **Evidence pointer** Abstract, case study section; location not provided
- **Concern** Only two target proteins are tested, and both are expressed in the same host (*E. coli*). No comparison is made against existing promoter engineering methods, such as random mutagenesis, hybrid promoter construction, or other computational design tools. The abstract does not report how many designed promoters were tested, what fraction were successful, or whether the method consistently produces strong promoters across different sequence contexts.
- **Why it matters** The claim of effectiveness requires evidence that the method generalizes beyond the specific cases shown. Without a success rate or comparison to alternative approaches, the reader cannot judge whether this method offers an advantage over existing practice.
- **Resolution test** Report the number of designed promoters tested, the success rate, and a comparison with at least one established promoter engineering method. Include data on promoter activity distribution and sequence diversity to demonstrate generalizability.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, first sentence; location not provided
- **Issue** The phrase "Expanding sigma70 promoter libraries" is vague. It is unclear whether the goal is to create new promoters, characterize existing ones, or both.
- **Required correction** Specify the intended outcome, such as "generating novel sigma70 promoter variants with a range of strengths" or "increasing the number of characterized strong sigma70 promoters."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reporting completeness
- **Affected element** Screening details
- **Evidence pointer** Abstract, methods description; location not provided
- **Issue** The high-throughput screening is described in a single sentence with no information on library size, screening format, or how fluorescence was measured and normalized.
- **Required correction** Provide at least the library size and the range of promoter strengths observed, and state the number of "strong" promoters selected for downstream analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Quantitative reporting
- **Affected element** Expression improvements
- **Evidence pointer** Abstract, case study section; location not provided
- **Issue** The 81.4% and 33.4% improvements are presented without context on the absolute expression levels or the strength of the reference promoter.
- **Required correction** State the absolute fluorescence or protein yield values for both the reference and the designed promoters, and indicate whether the reference is a commonly used promoter such as Ptac or Ptrc.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model availability
- **Evidence pointer** Abstract, methods description; location not provided
- **Issue** The deep learning model is described as "previously reported," but no citation or model identifier is given in the abstract.
- **Required correction** Include a citation to the prior work and, if applicable, a link to the model code or repository in the full manuscript.

## Risk / unsupported claims
- The claim that the combined method is "effective for promoter engineering" is unsupported by the abstract alone, as no statistical analysis or comparison to existing methods is provided.
- The claim that the method enabled "soluble expression of mTG-activating protease" is stated without any data on protein solubility, yield, or activity, making it unverifiable from the supplied material.
- The assertion that "features of these strong promoters were adopted to guide promoter design" is unverifiable, as the specific features and their role in the design process are not described.
- The generalizability of the method to other promoters, genes, or hosts is not assessable from the abstract, as only two case studies in *E. coli* are mentioned.