## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, data availability)
- **Assessment boundary** Scientific claims, methodology, validation, and interpretation as presented in the provided text
- **Shared manuscript claim summary** The authors introduce "nucleotide dependencies" computed from DNA language models as a novel, alignment-free, unsupervised approach to identify functional genomic elements, including transcription factor binding sites, RNA secondary and tertiary structures, and to reveal limitations of existing DNA language model architectures and training strategies.
- **Visible evidence base** Abstract, Introduction, Results sections (including figure descriptions), Methods sections, Data and code availability statements
- **Missing materials affecting confidence** Figures and supplementary figures are referenced but not provided; detailed mathematical definitions of nucleotide dependencies are incomplete; specific benchmark datasets and statistical test details are not fully described; full model training hyperparameters are not provided

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting and potentially impactful approach to interpreting DNA language models by computing pairwise nucleotide dependencies. The authors demonstrate applications across variant effect prediction, regulatory element identification, and RNA structure inference, with some experimental validation in E. coli. However, the manuscript as provided has several significant gaps in methodological detail, statistical rigor, and clarity of presentation that prevent full evaluation of the claims. The central concept is promising, but the evidence base is currently insufficient to fully establish the superiority or broad utility of the approach over existing methods.
- **Who would be interested in the results, and why** Computational biologists developing and applying language models to genomics, researchers studying regulatory genomics and transcription factor binding, RNA structural biologists interested in novel prediction methods, and researchers working on variant effect prediction and functional annotation of genomes. The approach offers a new way to extract interpretable information from complex models, which is of broad interest to the growing community using foundation models in genomics.
- **Major strengths** 1. The concept of nucleotide dependencies is novel and provides a more interpretable output from DNA language models compared to simple reconstruction probabilities. 2. The breadth of applications explored (variants, TF binding, splicing, RNA structure) demonstrates the potential general utility of the approach. 3. The inclusion of experimental validation for novel RNA structures in E. coli strengthens the claims. 4. The critical analysis of existing DNA language model architectures and training strategies is valuable for the field.
- **Major Concerns** 1. The mathematical definition of nucleotide dependencies is incomplete and difficult to follow. 2. The statistical framework for comparing methods and assessing significance is not fully described. 3. The claim that the approach outperforms alignment-based methods for variant effect prediction requires more rigorous benchmarking. 4. The generalizability of the approach across different model architectures and species is not systematically evaluated. 5. The practical utility of the method for genome-wide scans is not clearly demonstrated with runtime and scalability considerations.
- **Minor Comments** 1. The manuscript would benefit from a clearer explanation of the relationship between nucleotide dependencies and existing concepts like mutual information or covariation. 2. The choice of the 6-nucleotide window for block detection appears arbitrary and should be justified. 3. The description of the convolutional filter approach for detecting parallel and anti-parallel dependencies is too brief. 4. The discussion of limitations of the approach is minimal and should be expanded.
- **Technical failings that need to be addressed before the case is established** The incomplete mathematical definition of the core metric (nucleotide dependencies) is a fundamental issue that prevents reproduction and full understanding. The lack of clear statistical testing frameworks for key comparisons (e.g., variant effect prediction, TF binding site detection) undermines confidence in the reported performance differences.
- **Assessment against Nature-style criteria** Originality: High. The concept of using pairwise nucleotide dependencies from language models is novel and distinct from prior work. Scientific importance: Potentially high, as it offers a new interpretable framework for a widely used class of models. Interdisciplinary readership: The approach bridges machine learning, genomics, and RNA biology, which could appeal to a broad audience. Technical soundness: Currently insufficient. The incomplete methodological details and lack of rigorous statistical comparisons prevent full assessment. Readability for nonspecialists: The core concept is explained reasonably well, but the methods section is dense and would benefit from clearer exposition and a more intuitive explanation of the dependency metric.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript defines "nucleotide dependencies" as a measure of how nucleotide substitutions at one position affect probabilities at other positions, and this forms the basis for all subsequent analyses.
- **Evidence pointer** Methods section, "Nucleotide Dependencies and variant influence score"
- **Concern** The mathematical definition of nucleotide dependencies is incomplete. The text states "We define the dependency between a variant nucleotide 𝑘 𝑎𝑙𝑡 at position 𝑖 and a target position 𝑗 as where 𝑘 is one of the 4 possible nucleotides..." but the actual formula is missing. Similarly, the equation for nucleotide dependency 𝑒 𝑖,𝑗 is referenced but not fully presented. This is a fundamental issue as the entire manuscript rests on this metric.
- **Why it matters** Without a complete and precise definition, the work cannot be reproduced, verified, or built upon. This is a critical flaw for a methodological paper.
- **Resolution test** Provide the complete mathematical formulation for nucleotide dependencies, including all variables, indices, and the exact computation procedure. This should be presented in a clear, unambiguous manner.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the variant influence score "outperformed reconstruction, as well as alignment-based conservation scores" for distinguishing fine-mapped promoter eQTL SNPs from matched controls.
- **Evidence pointer** Results section, "Nucleotide Dependency Maps", Figure S1B-E
- **Concern** The statistical framework for this comparison is not described. It is unclear what metric was used to measure performance (e.g., AUC, correlation), how significance was assessed, and whether the comparison was fair (e.g., were the same variants and matched controls used for all methods?).
- **Why it matters** The claim of superiority over existing methods is a key selling point of the approach. Without a clear statistical framework, this claim cannot be evaluated or trusted.
- **Resolution test** Provide a detailed description of the evaluation protocol, including the performance metric, the statistical test used to compare methods, and the exact datasets and variant sets used. Report confidence intervals and p-values for all comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that "nucleotide dependencies also highlight bases in contact within RNA structures, including pseudoknots and tertiary structure contacts, with remarkable accuracy."
- **Evidence pointer** Results section, "Nucleotide dependencies reveal RNA secondary and tertiary structure contacts", Figure 4A-D
- **Concern** While the AUC values reported for secondary structure prediction are high, the comparison to existing state-of-the-art RNA structure prediction methods is not provided. The claim of "remarkable accuracy" needs to be contextualized against existing approaches.
- **Why it matters** Without benchmarking against existing methods, it is unclear whether the approach offers a significant advance or is merely comparable to what already exists.
- **Resolution test** Include a comparison with at least one or two established RNA secondary structure prediction methods on the same benchmark datasets. Report the same evaluation metrics for all methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "regulatory elements appear as dense blocks in dependency maps, enabling the systematic identification of transcription factor binding sites as accurately as models trained on experimental binding data."
- **Evidence pointer** Results section, "Blocks along the diagonal highlight regulatory sequence motif instances", Figure 2C-D
- **Concern** The comparison to "models trained on experimental binding data" is vague. It is unclear which specific models were used for comparison, what the evaluation metric was, and whether the comparison was performed on the same set of TF binding sites.
- **Why it matters** This is a strong claim that needs to be substantiated with a clear and fair comparison to existing supervised methods.
- **Resolution test** Specify the exact supervised models used for comparison, the evaluation metric (e.g., area under the precision-recall curve), and the dataset and cross-validation scheme used. Provide a detailed description of how the comparison was performed.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that the analysis "reveal critical limitations of several DNA LM architectures and training sequence selection strategies."
- **Evidence pointer** Results section, "Dependency maps uncover shortcomings in DNA LM model designs and training data selection", Figure 7A-C
- **Concern** The analysis of model limitations is based on visual inspection of dependency maps for a small number of examples (e.g., one human tRNA). It is unclear how representative these examples are and whether the conclusions hold systematically across many loci.
- **Why it matters** The claim of revealing "critical limitations" is strong and needs to be supported by a more systematic and quantitative analysis.
- **Resolution test** Provide a quantitative analysis of the identified artifacts across a larger set of loci, with statistical tests to support the claims of systematic differences between model architectures and training strategies.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Introduction, paragraph 1
- **Evidence pointer** Introduction
- **Issue** The sentence "Sequence comparison not only leverages nucleotide-level conservation, but also statistical dependencies between nucleotides" is slightly awkward. The phrase "leverages" is used twice in close proximity.
- **Required correction** Rephrase to improve flow, e.g., "Sequence comparison leverages not only nucleotide-level conservation but also statistical dependencies between nucleotides."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Nucleotide Dependencies and variant influence score"
- **Evidence pointer** Methods section
- **Issue** The description of how the variant influence score is computed for the ClinVar analysis is unclear. The text states "we computed the dependency map centered on the variant of interest" but does not specify the window size or how the score is aggregated across targets.
- **Required correction** Provide a clear description of the computational procedure for the ClinVar analysis, including the window size and the aggregation method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Evaluation of artificial forward and inverted duplications"
- **Evidence pointer** Methods section
- **Issue** The description of how "average dependencies" are computed for the artificial duplication experiments is vague. It is not clear whether the average is taken over all pairs of duplicated positions or over all positions in the sequence.
- **Required correction** Clarify the exact computation of the average dependency in this context.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results, "Dependency maps uncover shortcomings in DNA LM model designs and training data selection"
- **Evidence pointer** Results section, Figure 7A
- **Issue** The description of the artifacts in the Nucleotide Transformer models is brief and relies heavily on the reader interpreting the figure. A more explicit description of the observed artifacts would be helpful.
- **Required correction** Provide a more detailed textual description of the artifacts observed in the dependency maps of the Nucleotide Transformer models.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the relationship between nucleotide dependencies and sequence conservation is brief. A more detailed discussion of how the two concepts relate and differ would be valuable.
- **Required correction** Expand the discussion to more thoroughly address the relationship and differences between nucleotide dependencies and traditional sequence conservation measures.

## Risk / unsupported claims
- The claim that nucleotide dependencies "indicate deleteriousness of human genetic variants more effectively than sequence alignment and DNA LM reconstruction" is not fully supported without a detailed description of the statistical framework and benchmarking.
- The claim of "remarkable accuracy" in capturing RNA tertiary structure contacts is not supported by comparison to existing methods.
- The claim that the approach identifies TF binding sites "as accurately as models trained on experimental binding data" is not fully substantiated without a clear description of the comparison.
- The claim that the analysis reveals "critical limitations" of DNA LM architectures is based on limited examples and lacks systematic quantitative support.
- The generalizability of the findings across different species and model architectures is not systematically demonstrated.
- The practical scalability of the approach for genome-wide analyses is not discussed.