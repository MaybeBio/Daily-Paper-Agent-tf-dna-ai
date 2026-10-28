## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific and technical evaluation of the described tool, methodology, validation approach, and claims; no assessment of code functionality or server availability beyond what is described
- **Shared manuscript claim summary** The authors present NABhClassifier, a web server that identifies small helical sequences with nucleic acid-binding potential in proteins. The tool extracts putative alpha helices from input protein sequences, computes 20 physicochemical features, and integrates eight machine learning models into a consensus score (INABh). The authors claim high accuracy (above 0.99 for individual models), rapid analysis (under 2 seconds per sequence), and successful validation on RNA-binding protein datasets and whole-genome analyses across five organisms.
- **Visible evidence base** Methods section describing helix extraction, featurization, training data, and model selection; Results section with validation on ssRBP/dsRBP datasets and whole-genome analyses; Tables 1-4 referenced; Figures 1-4 referenced; Supplementary Files 1-3 referenced
- **Missing materials affecting confidence** Actual data tables and figures not provided; Supplementary Files not accessible; no detailed performance metrics per model; no confusion matrix data; no comparison with existing tools beyond qualitative statements; no information on server availability or uptime; no statistical significance testing reported

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful web-based tool for identifying helical nucleic acid-binding sequences in proteins. The concept of focusing on small helical segments rather than whole proteins is interesting and could have practical applications. However, the manuscript has substantial methodological weaknesses that undermine confidence in the reported performance. The training data construction is problematic, the validation approach is circular in places, and the reported accuracy metrics are not supported by sufficient detail. The tool's novelty relative to existing methods is not clearly established, and several claims go beyond what the presented evidence supports.
- **Who would be interested in the results, and why** Researchers working on RNA interference, nucleic acid delivery systems, and protein engineering for biotechnological applications would find this tool potentially useful. The ability to identify small helical peptides with nucleic acid-binding capacity could aid in designing peptide-based delivery vehicles for siRNA or other nucleic acid therapeutics. The tool's simplicity and speed may appeal to experimental biologists without specialized bioinformatics training.
- **Major strengths** The manuscript addresses a practical need for identifying small nucleic acid-binding domains rather than classifying whole proteins. The web server implementation with automated pipeline is user-friendly. The consensus scoring approach (INABh) is a reasonable strategy to account for model variability. The validation on diverse organisms and protein classes suggests potential generalizability.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (training data construction), R1-M2 (validation circularity), R1-M3 (accuracy metric reporting), R1-M4 (novelty claim)
- **Assessment against Nature-style criteria** Originality: Moderate. The idea of identifying small helical nucleic acid-binding sequences is not entirely new, and the approach of using physicochemical features with machine learning is standard. The specific focus on helical segments is a minor variation. Scientific importance: Moderate. The tool could be useful for biotechnological applications, but the impact is incremental rather than transformative. Interdisciplinary readership: Limited. The manuscript is primarily of interest to computational biologists and protein engineers. Technical soundness: Weak. Several methodological issues undermine confidence in the reported performance. Readability for nonspecialists: Adequate. The manuscript is generally clear, though some technical details are under-specified.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial revisions to address methodological concerns before the claims can be evaluated.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that models were trained on "22 amino acid long helical sequences" with a positive set from "KhpB carboxy-terminal α helix from 2560 different bacterial species" and a negative set from "701 α helices present in the albumin structure from 90 different organisms plus 1859 random generated sequences of 22 amino acids."
- **Evidence pointer** Methods section, Training Data Sets; Figure 1
- **Concern** The training data construction is problematic for several reasons. First, the positive set is derived from a single protein (KhpB) across species, which means the models may learn features specific to KhpB rather than general nucleic acid-binding properties. Second, the negative set combines albumin helices with random sequences, which are not representative of the diversity of non-binding helices in real proteins. Third, the use of random sequences as negatives is particularly concerning because they may not form stable helices in reality, making the classification task artificially easy. The authors do not provide any analysis of sequence similarity between training and test sets, raising concerns about potential data leakage. The imbalance between positive (2560) and negative (701 + 1859 = 2560) is exactly balanced, which is unusual and may not reflect real-world distributions.
- **Why it matters** If the training data are not representative of the target application space, the reported accuracy metrics will not generalize to real-world use. The use of a single protein family for positives and random sequences for negatives could lead to models that identify KhpB-like features rather than genuine nucleic acid-binding properties.
- **Resolution test** The authors should provide a more diverse positive training set derived from multiple known nucleic acid-binding proteins. The negative set should include helices from proteins that do not bind nucleic acids, drawn from a variety of protein families. Cross-validation should be performed with sequence-similarity-based partitioning to avoid inflated performance estimates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** The authors claim that "NABhClassifier accurately identified approximately 75% (352) of dsRBP and 71% (327) of ssRBP proteins when using an INABh threshold of 1.0" and "achieved a recovery rate of about 96% (454/474) for dsRBP and 95% (434/458) for ssRBP" at a threshold of 0.75.
- **Evidence pointer** Results section, Proof-of-Concept Validation; Table 3
- **Concern** The validation approach is circular. The positive training set was derived from KhpB, which is itself an RNA-binding protein. The validation datasets (ssRBPs and dsRBPs) are also RNA-binding proteins. The models were trained to recognize features of RNA-binding helices, so it is not surprising that they perform well on other RNA-binding proteins. This does not demonstrate that the tool can identify novel nucleic acid-binding sequences. Additionally, the authors report "recovery rates" but do not report precision or false positive rates. Without knowing how many non-binding proteins were incorrectly classified as binders, the practical utility of the tool cannot be assessed. The whole-genome analysis in Table 4 uses functional annotations to define "true" NABPs, but this approach is inherently limited by the completeness and accuracy of those annotations.
- **Why it matters** The validation does not establish that the tool can distinguish nucleic acid-binding helices from non-binding helices in a general setting. The reported recovery rates may reflect the similarity between the validation proteins and the training protein rather than genuine predictive power.
- **Resolution test** The authors should validate on a held-out set of nucleic acid-binding proteins that are evolutionarily distant from KhpB. They should also include a set of non-binding proteins and report precision, specificity, and false positive rates. Ideally, experimental validation of predicted novel binding sequences should be performed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "eight demonstrated accuracy above 0.99 and were selected to form the NABhClassifier core" and that "Combining these models outperformed individual models."
- **Evidence pointer** Results section; Figure 3; Table 2
- **Concern** The reported accuracy of above 0.99 is suspiciously high and likely reflects the artificial nature of the classification task. With a balanced dataset of 2560 positive and 2560 negative examples, achieving 0.99 accuracy means fewer than 50 misclassifications. Given the simplicity of the features used (20 physicochemical properties), such high accuracy suggests the task is too easy, likely because the negative set (random sequences) is not representative of real non-binding helices. The authors do not report confidence intervals or statistical significance of the accuracy differences between models. The claim that "adding more models beyond these eight did not further improve performance" is not supported by any data shown.
- **Why it matters** If the reported accuracy is inflated due to the artificial classification task, the tool's real-world performance will be substantially lower. Users may be misled into trusting predictions that are not reliable.
- **Resolution test** The authors should report performance on a realistic test set that includes challenging negative examples (e.g., helices from non-binding proteins that are similar in composition to binding helices). They should also report confidence intervals and perform statistical comparisons between models.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Originality
- **Claim pointer** The authors state that "while other sequence-based and structure-aware algorithms focus on the identification of nucleic acid-binding sites on proteins, the NABhClassifier server also identifies NABPs based only in the sequence, in addition to extracting small helical peptides with the ability to bind nucleic acids."
- **Evidence pointer** Results and Discussion section
- **Concern** The novelty claim is not well supported. The authors mention catRAPID omics v2 and GraphSite as existing tools but do not provide a systematic comparison with these or other relevant tools (e.g., RNABindR, PPRInt, BindN). The claim that NABhClassifier is unique in extracting small helical peptides is not substantiated with a literature search. The authors do not demonstrate any advantage over existing methods in terms of accuracy, speed, or usability beyond qualitative statements.
- **Why it matters** For a tool to be publishable, its novelty and advantage over existing methods must be clearly established. Without a quantitative comparison, readers cannot assess whether NABhClassifier offers any benefit over existing approaches.
- **Resolution test** The authors should perform a benchmark comparison with existing tools on the same datasets, reporting accuracy, precision, recall, and computational time. They should also clearly articulate what specific gap NABhClassifier fills that existing tools do not.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, Identifying and Extracting Helical Secondary Structures
- **Evidence pointer** Methods section
- **Issue** The helix extraction criterion is based solely on amino acid composition (presence of alanine, glutamate, histidine, lysine, leucine, methionine, glutamine, and arginine). This is a very simplistic definition of a helix and may not correspond to actual helical structures in proteins. The authors do not validate that the extracted segments indeed form helices in known structures.
- **Required correction** The authors should clarify whether this composition-based criterion was validated against known protein structures. If not, they should acknowledge this limitation and discuss its potential impact on the tool's utility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Machine Learning Models
- **Evidence pointer** Methods section
- **Issue** The description of hyperparameter tuning is vague. The authors state that "Hyperparameters were set using Grid search technique, and each model underwent cross-validation through 50 iterations" but do not provide the hyperparameter ranges tested or the final selected parameters for each model.
- **Required correction** The authors should provide the full hyperparameter search space and the final parameters for each of the eight selected models, either in the main text or in a supplementary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, Proof-of-Concept Validation
- **Evidence pointer** Results section; Table 4
- **Issue** The whole-genome analysis in Table 4 is described only qualitatively. The authors state that "NABhClassifier recovered at least one helix per NABP and correctly identified 93-99% true NABPs" but do not provide the actual numbers of proteins analyzed, the number of true positives and false positives, or the criteria used to define "true NABPs" beyond keyword matching.
- **Required correction** The authors should provide the full data for Table 4, including the number of proteins in each category, the number of true and false positives at each threshold, and the specific keywords used for annotation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Web server
- **Evidence pointer** Methods, NABhClassifier Web Server Interface and Infrastructure
- **Issue** The server is hosted at an IP address (http://143.54.25.149) rather than a domain name. This is unusual and may raise concerns about long-term availability and accessibility. The authors do not provide any information about server maintenance, uptime guarantees, or data privacy policies.
- **Required correction** The authors should consider obtaining a proper domain name and provide information about server maintenance and data handling policies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Conclusions
- **Evidence pointer** Abstract; Conclusions
- **Issue** The abstract and conclusions state that the tool identifies sequences that bind "single- and double-stranded RNA," but the training data were derived from KhpB, which is described as an RNA-binding protein. The validation datasets include both ssRBPs and dsRBPs, but the authors do not clarify whether the tool can distinguish between single-stranded and double-stranded RNA binding. The conclusions also mention "DNA-binding" in the context of validation, but the training data do not include DNA-binding proteins.
- **Required correction** The authors should clarify the scope of the tool's binding specificity and avoid overstating its capabilities.

## Risk / unsupported claims
- The claim that the tool "provides a powerful tool for identifying small helices with nucleic acid-binding capacity" is not fully supported because the validation is circular and does not include challenging negative examples.
- The claim that "combining these models outperformed individual models" is not supported by any quantitative comparison data shown.
- The claim that the tool "surpasses the limitations of conventional algorithms" is not substantiated with a quantitative comparison.
- The claim that the tool can identify "DNA-binding and single- and double-stranded RNA-binding protein data sets" is not supported by the training data, which only include RNA-binding proteins.
- The reported accuracy of above 0.99 for individual models is not credible given the simplicity of the features and the artificial nature of the negative set.
- The statement that "adding more models beyond these eight did not further improve performance" is not supported by any data.
- The claim that the tool "offers superior performance" compared to existing methods is not supported by any benchmark comparison.