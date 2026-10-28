## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, figure legends not fully provided, references partially listed)
- **Assessment boundary** Scientific validity, methodological soundness, interpretability of claims, and generalizability of the reported model based on the provided text
- **Shared manuscript claim summary** The authors present IDEA, a residue-level coarse-grained biophysical model that learns an interpretable amino acid-nucleotide interaction energy matrix from known protein-DNA complex structures and sequences. The model is claimed to predict sequence-specific DNA binding affinities, transfer across protein families within the same CATH superfamily, identify genomic binding sites at base-pair resolution, and, when integrated into a simulation framework, capture absolute binding free energies.
- **Visible evidence base** Results sections describing predictions against MITOMI data for MAX and Pho4, HT-SELEX data for 22 proteins across 12 families, ChIP-seq data for MAX, EGR1, and CTCF, and simulation-based free energy calculations for nine TF-DNA complexes. Methods sections describing the optimization protocol, structural modeling, and simulation integration.
- **Missing materials affecting confidence** Figure panels and supplements referenced but not fully visible; exact numerical values for many reported correlations and AUC scores are stated but underlying data distributions are not shown; details on the simulation protocol and umbrella sampling parameters are only partially described; no comparison of computational cost or runtime; no discussion of limitations regarding the assumption of a single fixed structure for each protein-DNA pair.

## Reviewer

- **Overall assessment** The manuscript presents a conceptually appealing and timely approach to a long-standing problem in quantitative biology: predicting protein-DNA binding specificity from structure and sequence in an interpretable manner. The core idea of learning a residue-level interaction energy matrix from known complexes and applying it to predict affinities, transfer across homologs, and even drive simulations is attractive and could be of broad interest. However, the current evidence base is insufficient to fully establish the claimed generality and quantitative accuracy. Several key validations are presented with modest correlations, and the treatment of structural flexibility, cooperative effects, and the choice of decoy generation are not sufficiently scrutinized. The manuscript would benefit from a more rigorous statistical framework, additional benchmarks against existing methods, and a clearer articulation of the model's limitations.

- **Who would be interested in the results, and why** Computational biologists studying protein-DNA recognition, experimentalists using ChIP-seq or SELEX who need predictive tools for variant interpretation, and researchers in the gene regulation field interested in mechanistic models of transcription factor binding. The interpretable nature of the model could also appeal to those seeking to understand the "molecular grammar" of binding specificity.

- **Major strengths**
  - The model is interpretable by design, providing a direct readout of amino acid-nucleotide interaction energies, which is a significant advantage over black-box deep learning approaches.
  - The integration of the learned energy model into a coarse-grained simulation framework is a novel and potentially powerful extension, allowing for dynamic studies of binding.
  - The demonstration of transferability across a CATH superfamily is a valuable practical feature, suggesting the model can be applied to proteins without direct experimental binding data.
  - The use of multiple independent datasets (MITOMI, HT-SELEX, ChIP-seq) for validation strengthens the claims of generalizability.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "IDEA enables accurate prediction of sequence-specific DNA binding affinities" and "accurately predicts the majority of the MAX binding sites, achieving an AUC score of 0.81"
  - **Evidence pointer** Results sections "IDEA accurately predicts sequence-specific protein-DNA binding affinity" and "Identification of genomic protein-DNA binding sites"; Figure 2A, Figure 4B
  - **Concern** The reported Pearson correlation of 0.67 for MAX binding affinity predictions, while positive, explains less than half of the variance in the experimental data. The improvement to 0.79 with SELEX data incorporation is modest. For the genomic prediction, an AUC of 0.81 is reported for a single 1 Mb region, which is a limited test. The choice of the Z-score threshold (< -0.75) for defining binding sites is not justified, and the sensitivity of the AUC to this threshold is not explored. The manuscript does not report confidence intervals for these metrics, nor does it compare performance against a null model or a simple sequence-only baseline.
  - **Why it matters** The central claim of the paper is that IDEA provides accurate predictions. The reported metrics, while positive, are not overwhelmingly strong, and without a rigorous statistical framework or comparison to simpler baselines, it is difficult to assess whether the model's complexity is justified. The limited genomic validation (one region, one cell type) raises questions about generalizability to other loci and conditions.
  - **Resolution test** Provide confidence intervals for all reported correlation and AUC values. Compare IDEA's performance against a sequence-only model (e.g., a position weight matrix) and a simple electrostatic model on the same datasets. Validate genomic predictions on multiple independent ChIP-seq datasets and across different genomic regions, and report the precision-recall trade-off at various thresholds.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "IDEA enables direct interpretation of physicochemical interactions among individual amino acids and nucleotides" and "learns a family-specific interaction matrix that quantifies energetic interactions between each amino acid and nucleotide"
  - **Evidence pointer** Results section "IDEA decodes the molecular grammar governing protein-DNA interactions"; Figure 2B, Figure 2C
  - **Concern** The interpretability claim is supported by a single example: the strong interaction between arginine and deoxycytidine in the MAX complex. While this is consistent with known biology, it is a very limited demonstration. The manuscript does not systematically validate the learned interaction matrix against known structural contacts or mutagenesis data across multiple proteins. The PCA analysis (Figure 3—figure supplement 2) shows clustering by family, but the biological meaning of the learned interaction energies is not deeply explored. The model assumes a single fixed structure for each protein-DNA pair, which may not be valid for proteins that bind DNA with significant conformational changes or for multi-domain proteins.
  - **Why it matters** The interpretability of the model is a key selling point and a major differentiator from deep learning approaches. If the learned interaction energies are not robustly validated or are highly sensitive to the training set, the interpretability claim is weakened. The assumption of a fixed structure is a significant simplification that could limit the model's accuracy and interpretability for dynamic or flexible complexes.
  - **Resolution test** Validate the learned interaction matrix against a larger set of known protein-DNA contacts (e.g., from a structural database) and against experimental mutagenesis data. Perform a sensitivity analysis to show how the interaction matrix changes with different training sets. Discuss and, if possible, test the model's performance on proteins with known conformational flexibility upon DNA binding.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** "IDEA provides an integrated computational platform that alleviates experimental costs and biases in assessing DNA recognition"
  - **Evidence pointer** Results section "Integration of IDEA into a residue-resolution simulation model captures protein-DNA binding dynamics"; Figure 5
  - **Concern** The simulation results are presented for only nine TF-DNA complexes, and the improvement in correlation from 0.46 to 0.81 is based on a small sample size. The manuscript does not report the statistical significance of this improvement, nor does it compare the simulation results to other computational methods for predicting absolute binding free energies. The claim that the simulation can predict "absolute binding free energies with physical units" is strong, but the accuracy of these predictions is not benchmarked against experimental values in absolute terms (e.g., kcal/mol), only in terms of correlation.
  - **Why it matters** The simulation component is a significant extension of the model, but its practical utility depends on its accuracy and computational cost. A small validation set and a lack of absolute error reporting make it difficult to assess whether this approach is competitive with existing methods or useful for quantitative predictions.
  - **Resolution test** Expand the simulation validation to a larger set of protein-DNA complexes with known absolute binding free energies. Report the mean absolute error and root-mean-square error of the predicted free energies in physical units. Compare the computational cost and accuracy of the IDEA-based simulation to other established methods (e.g., MMPBSA, alchemical free energy calculations).

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** "IDEA is transferable across the same protein superfamily" and "generalized to enable base-pair resolution predictions of genomic DNA-binding sites"
  - **Evidence pointer** Results section "IDEA demonstrates transferability across proteins in the same CATH superfamily"; Figure 3A
  - **Concern** The transferability test is performed within a single CATH superfamily (4.10.280.10) for the MAX-related proteins. The manuscript does not test transferability across more distantly related proteins or across different structural classes of DNA-binding domains (e.g., zinc fingers, homeodomains, winged helix). The genomic prediction for EGR1 and CTCF is mentioned but not described in detail, and the performance metrics for these additional proteins are not reported in the main text.
  - **Why it matters** The claim of transferability is important for the model's practical utility, as it would allow predictions for proteins without direct structural data. A demonstration on a single superfamily is insufficient to establish this claim broadly. The lack of detailed results for EGR1 and CTCF weakens the claim of generalizability to different protein families.
  - **Resolution test** Test transferability across multiple CATH superfamilies and structural classes. Provide detailed results for the genomic predictions for EGR1 and CTCF, including AUC scores and comparison to ChIP-seq peaks. Discuss the limitations of transferability for proteins with very different DNA-binding domain architectures.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction and Results section "Predictive protein-DNA energy model at residue resolution"
  - **Evidence pointer** Introduction, first paragraph
  - **Issue** The introduction is dense and assumes familiarity with the specific experimental techniques (ChIP-seq, PBM, SELEX) and computational methods. The description of the model in the first results section is technical and could benefit from a more intuitive explanation of the optimization procedure and the meaning of the interaction matrix.
  - **Required correction** Add a brief, plain-language summary of the model's workflow and the key concept of the interaction matrix. Consider adding a schematic figure that illustrates the input, optimization, and output of the model in a way that is accessible to a broad readership.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods section "Treatment of complementary DNA sequences"
  - **Evidence pointer** Methods, "Treatment of complementary DNA sequences"
  - **Issue** The method for determining whether a target sequence belongs to the forward or reverse strand is based on sequence similarity. This is a reasonable heuristic, but it may fail for palindromic or highly repetitive sequences. The manuscript does not discuss this potential limitation.
  - **Required correction** Acknowledge this limitation and suggest a strategy for handling ambiguous cases (e.g., testing both orientations and reporting the higher affinity prediction).

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods section "Enhanced modeling prediction with SELEX data"
  - **Evidence pointer** Methods, "Enhanced modeling prediction with SELEX data"
  - **Issue** The ridge regression parameter α=0.01 is stated as being "consistently applied," but no sensitivity analysis is provided. The choice of this parameter could affect the learned interaction matrix and the resulting predictions.
  - **Required correction** Provide a brief sensitivity analysis showing how the predictive performance changes with different values of α.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Results section "Identification of genomic protein-DNA binding sites"
  - **Evidence pointer** Results, "Identification of genomic protein-DNA binding sites"
  - **Issue** The description of the genomic prediction is brief and lacks detail on the computational steps involved, such as how the 1 Mb region was scanned, how the Z-scores were calculated, and how the threshold was chosen.
  - **Required correction** Expand this section to provide a clearer step-by-step description of the genomic prediction pipeline, including the choice of threshold and the rationale behind it.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Insufficient statistical rigor in reporting prediction accuracy; lack of comparison to simpler baselines.
  - R1-M2: Limited validation of the interpretability of the learned interaction matrix.
  - R1-M3: Small validation set for the simulation component; lack of absolute error reporting.
  - R1-M4: Limited demonstration of transferability across protein families.

## Risk / unsupported claims
- The claim that IDEA "alleviates experimental costs and biases" is not directly supported by any cost-benefit analysis or comparison to experimental throughput.
- The claim that the simulation can predict "absolute binding free energies" is not supported by a comparison to experimental values in absolute terms.
- The claim that IDEA "can be generalized to enable base-pair resolution predictions of genomic DNA-binding sites" is based on a single detailed example (MAX) and brief mentions of EGR1 and CTCF without full results.
- The statement that the model "accurately ranks the binding affinities" is based on Spearman correlations that are not reported with confidence intervals or significance tests.
- The biological interpretation of the PCA clustering (Figure 3—figure supplement 2) is not discussed in detail, and the claim that "the relative distance between energy models in PCA space reflects the degree of transferability" is not quantitatively tested.