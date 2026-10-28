## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors introduce GRAPE-LM, a generative AI framework combining a transformer-based conditional autoencoder with nucleic acid language models, guided by CRISPR-Cas-based aptamer screening data from intracellular environments. They claim that GRAPE-LM enables single-round evolution of RNA aptamers and outperforms aptamers obtained through multiple rounds of human selection across three targets: CD3epsilon, SARS-CoV-2 RBD, and c-Myc.
- **Visible evidence base** Abstract text only; no quantitative results, experimental details, or validation data are visible
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary information, sequence data, binding assay details, statistical analyses, and comparison datasets

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting application of language models to RNA aptamer evolution, a problem that has received less attention than protein evolution. The choice of three disparate targets, including an intracellular disordered protein, is commendable. However, the abstract lacks quantitative evidence, methodological detail, and clear definitions of the comparison benchmarks. The central claim of outperforming multi-round human selection cannot be evaluated from the supplied material. The work may be of interest to the aptamer and directed evolution communities, but the evidence base is insufficient to assess technical soundness or scientific impact at the level implied by the claims.
- **Who would be interested in the results, and why** Researchers in RNA biology, aptamer engineering, directed evolution, and generative AI for biomolecular design would be interested. The potential to reduce screening rounds from multiple to one could have practical implications for diagnostic and therapeutic aptamer development. The application to an intracellular disordered protein target may also attract those studying transcription factor targeting.
- **Major strengths** The problem addressed is timely and relevant. The integration of a conditional autoencoder with nucleic acid language models is a plausible architectural choice. The use of CRISPR-Cas-based screening data from intracellular environments is an interesting departure from conventional in vitro selection. The choice of three structurally and functionally distinct targets strengthens the claim of generality.
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
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The application of language models to RNA aptamer evolution is relatively novel, though the underlying concept of generative models for biomolecular design is not new. The single-round evolution claim, if substantiated, would represent a meaningful advance.  
  Scientific importance: The potential to reduce screening burden is practically significant, but the abstract does not provide enough evidence to assess whether the improvement is transformative or incremental.  
  Interdisciplinary readership: The work bridges AI, RNA biology, and molecular engineering, which could appeal to a broad audience. However, the abstract assumes familiarity with both aptamer screening and language model architectures, which may limit accessibility.  
  Technical soundness: Cannot be assessed from the abstract alone. No quantitative metrics, statistical tests, or experimental controls are described.  
  Readability for nonspecialists: The abstract is dense and uses field-specific terminology without sufficient context. The acronym GRAPE-LM is not unpacked in a way that clarifies the method for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but lacks the quantitative and methodological detail required to support the central claims. A full manuscript with detailed methods, control experiments, and statistical analyses would be needed to assess whether the case can be made.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** GRAPE-LM, informed with only a single round of CRISPR-Cas-based screening, successfully obtains RNA aptamers that outperform those driven from multiple rounds of human selection and optimization.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract provides no quantitative data to support the claim of outperformance. No binding affinities, specificity measurements, functional assays, or statistical comparisons are reported. The term "outperform" is undefined in this context.  
- **Why it matters** The central claim of the manuscript rests on a comparative performance assertion. Without defined metrics and numerical results, the claim is unfalsifiable and cannot be evaluated by reviewers or readers.  
- **Resolution test** Provide quantitative comparison data, including binding affinities or functional readouts for GRAPE-LM-derived aptamers versus those from multi-round selection, with appropriate statistical tests and effect sizes.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency  
- **Claim pointer** GRAPE-LM integrates a transformer-based conditional autoencoder with nucleic acid language models and is guided by CRISPR-Cas-based aptamer screening data derived from intracellular environments.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not describe how the CRISPR-Cas screening data are generated, what the screening readout is, how the data are encoded for the model, or how the conditional autoencoder is trained and conditioned. The nature of the "guidance" is unclear.  
- **Why it matters** Reproducibility is a core requirement for a methods-oriented manuscript. Without a clear description of the data generation and model architecture, the method cannot be replicated or assessed for validity.  
- **Resolution test** Provide a detailed methods section describing the CRISPR-Cas screening protocol, the data preprocessing pipeline, the model architecture, training procedure, and conditioning mechanism.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation rigor  
- **Claim pointer** We validate GRAPE-LM on three disparate targets: the human T cell receptor CD3epsilon, the receptor-binding domain of the SARS-CoV-2 spike protein and the human oncogenic transcription factor c-Myc.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract states validation on three targets but provides no experimental details. It is unclear whether validation includes functional assays in relevant biological contexts, whether the aptamers are tested in vitro or in cells, and whether appropriate negative controls are included.  
- **Why it matters** Validation across disparate targets is only meaningful if the experimental conditions are rigorous and consistent. Without details on assay design, the claim of generalizability is unsupported.  
- **Resolution test** Describe the validation assays for each target, including positive and negative controls, replicate numbers, and the biological context in which aptamer function is assessed.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Comparison fairness  
- **Claim pointer** GRAPE-LM outperforms those driven from multiple rounds of human selection and optimization.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not specify what the "multiple rounds of human selection" refers to. It is unclear whether the comparison is against published aptamers, in-house selections, or a benchmark dataset. The selection conditions, target formats, and screening stringency may differ between the GRAPE-LM pipeline and the comparator.  
- **Why it matters** An unfair or poorly defined comparison undermines the validity of the central claim. The reader cannot determine whether the observed advantage is due to the method or to differences in experimental conditions.  
- **Resolution test** Clearly define the comparator aptamers, including their selection history, and ensure that binding and functional assays are performed under identical conditions for both GRAPE-LM-derived and comparator aptamers.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Title and abstract terminology  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "single-round evolution" is used without defining what constitutes a "round" in this context. It is unclear whether this refers to one screening cycle, one model training pass, or one experimental iteration.  
- **Required correction** Define "single-round" explicitly in the abstract or introduction, and clarify the distinction between computational evolution and experimental screening rounds.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract uses the acronym GRAPE-LM without explaining the rationale for the name or unpacking the components in a way that is accessible to nonspecialists. The phrase "activity-guided evolution" is not defined.  
- **Required correction** Briefly explain what "activity-guided" means in this context and consider spelling out the acronym or providing a one-sentence description of the framework for general readers.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Target selection rationale  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract lists three targets but does not explain why these targets were chosen or what challenges they represent for aptamer selection. The inclusion of an intracellular disordered protein is mentioned but not contextualized.  
- **Required correction** Add a sentence explaining the rationale for target selection, particularly the distinct challenges posed by each target class.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "Generator" terminology  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "generator" in the acronym GRAPE-LM is not standard in the language model literature and may be confused with other generative model types.  
- **Required correction** Clarify whether "generator" refers to a generative model in the GAN sense or simply to a model that generates sequences, and use terminology consistent with the broader literature.

## Risk / unsupported claims
- The claim that GRAPE-LM "successfully obtains RNA aptamers that outperform those driven from multiple rounds of human selection" is unsupported by any quantitative data in the abstract.
- The claim of "single-round evolution" is not defined and cannot be assessed without methodological detail.
- The generalizability claim across three targets is unverifiable without experimental validation details.
- The nature and quality of the CRISPR-Cas-based screening data are not described, making the "guidance" mechanism unassessable.
- No information is provided on aptamer length, sequence diversity, or binding specificity, which are standard metrics in aptamer characterization.