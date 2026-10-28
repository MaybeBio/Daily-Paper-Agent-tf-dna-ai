## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract; no methods, figures, or supplementary data were provided for evaluation
- **Shared manuscript claim summary** The authors introduce Footprint-seq, a sequencing-based in vitro method that maps protein–DNA interactions genome-wide at high spatial resolution by measuring local protection from transposition. Using E. coli CRP as a test case, they report detection of binding sites on plasmid and genomic DNA, and inference of dissociation constants for hundreds of genomic sites. They conclude the method is rapid, accessible, and quantitative for bacteria and other systems.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials were supplied
- **Missing materials affecting confidence** Full manuscript, methods description, all figures and tables, statistical analyses, validation data, and any comparison with existing methods

## Reviewer

- **Overall assessment** The abstract presents a potentially useful methodological advance with a clear conceptual basis. The claim that Footprint-seq enables genome-wide, high-resolution mapping and quantitative dissociation constant inference is ambitious and, if fully supported, would be of interest to the bacterial gene regulation community. However, the evidence base provided is insufficient to evaluate the technical soundness, reproducibility, or robustness of the method. Several key claims, particularly regarding quantitative accuracy and generalizability, cannot be assessed from the abstract alone.
- **Who would be interested in the results, and why** Researchers studying bacterial transcription regulation, DNA-binding protein specificity, and quantitative biophysics of protein–DNA interactions. The method could also appeal to those developing or using in vitro genomic assays for regulatory element mapping.
- **Major strengths** The conceptual simplicity of using transposition protection as a readout is appealing. The claim of combining genome-wide coverage with high spatial resolution and quantitative dissociation constant inference addresses a recognized gap in existing methods. The use of a well-characterized test case (CRP in E. coli) is appropriate for initial validation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "Footprint-seq detects CRP binding sites with high resolution across plasmid or genomic DNA"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not describe how spatial resolution is defined or measured, nor how detection sensitivity and specificity were assessed. No information is given on false positive rates, background signal, or how the method compares with established footprinting or ChIP-based approaches.
  - **Why it matters** Without a clear definition of resolution and a demonstration of detection accuracy, the core claim of high-resolution mapping cannot be evaluated. The utility of the method depends on its ability to distinguish true binding sites from noise.
  - **Resolution test** Provide quantitative metrics for resolution (e.g., base-pair precision of detected footprints), sensitivity, and specificity, including comparison with an orthogonal method (e.g., DNase footprinting or ChIP-seq) on the same DNA samples.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Quantitative rigor
  - **Claim pointer** "Footprint-seq enables inference of dissociation constants for hundreds of genomic sites"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that dissociation constants can be inferred but provides no information on the model used, the range of protein concentrations tested, the goodness-of-fit criteria, or how inferred values compare with known Kd values for CRP sites. No error analysis or reproducibility assessment is mentioned.
  - **Why it matters** Quantitative claims require demonstration of accuracy and precision. If inferred Kd values are not validated against independent measurements, the quantitative utility of the method is unsubstantiated.
  - **Resolution test** Show a comparison of inferred Kd values with published or experimentally measured values for a set of known CRP sites, including confidence intervals and replicate variability.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generalizability
  - **Claim pointer** "Footprint-seq provides a rapid, accessible, and quantitative method for mapping protein–DNA interactions in bacteria and other systems"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract only demonstrates the method with a single protein (CRP) in a single organism (E. coli). The claim of applicability to "other systems" is speculative without evidence. No discussion is provided on potential limitations such as protein size, DNA sequence context, or transposase accessibility biases.
  - **Why it matters** Generalizability is a key selling point for a new method. Without evidence across multiple proteins or organisms, the claim of broad applicability is unsupported.
  - **Resolution test** Provide data from at least one additional DNA-binding protein with different DNA-binding domain architecture, or a clear rationale with preliminary data for why the method should generalize.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Method description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract does not specify the transposase used, the transposition reaction conditions, or how "local protection" is quantified.
  - **Required correction** Add a brief description of the transposition-based readout and the quantification approach in the abstract or methods.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Experimental design
  - **Evidence pointer** Abstract; location not provided
  - **Issue** No mention of replicates, controls (e.g., no-protein condition), or data processing pipelines.
  - **Required correction** State the number of biological and technical replicates and describe key controls in the methods.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Comparison with existing methods
  - **Affected element** Contextualization
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions existing genome-scale methods but does not state how Footprint-seq compares in terms of cost, time, or resolution.
  - **Required correction** Include a brief comparison with at least one existing method (e.g., ChIP-seq, DNase-seq, or MITOMI) in terms of resolution and throughput.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The abstract does not provide sufficient evidence to establish the core claims of high-resolution detection, quantitative accuracy, or generalizability.
- **Assessment against Nature-style criteria**  
  - Originality: The concept of using transposition protection for genome-wide footprinting appears novel, but the abstract does not distinguish it sufficiently from existing in vitro methods.  
  - Scientific importance: If validated, the method could fill a niche for quantitative, high-resolution mapping in bacteria. The importance is moderate and depends on demonstrated advantages over existing tools.  
  - Interdisciplinary readership: The method is primarily of interest to molecular microbiologists and biophysicists; broader appeal is not evident from the abstract.  
  - Technical soundness: Not assessable from the abstract; major concerns remain unresolved.  
  - Readability for nonspecialists: The abstract is clear and accessible, though some terms (e.g., "transposition protection") could be briefly defined.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising concept, but the absence of methods, data, and validation prevents assessment of the core claims. I would be supportive if the technical concerns are resolved with full data and rigorous validation.

## Risk / unsupported claims

- The claim that Footprint-seq maps protein–DNA interactions "on a genome-wide scale at high spatial resolution" is unsupported without resolution metrics and detection accuracy data.
- The claim that dissociation constants can be inferred for "hundreds of genomic sites" is unsupported without model details, validation against known values, and error analysis.
- The claim of applicability to "other systems" is speculative and unsupported by the provided evidence.
- The claim that the method is "rapid" and "accessible" is not quantifiable from the abstract.