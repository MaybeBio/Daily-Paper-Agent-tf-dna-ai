## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific and technical evaluation of the presented method, results, and claims
- **Shared manuscript claim summary** The authors present DeepDISE, a fully convolutional neural network that predicts DNA binding sites on protein surfaces using 3D coordinates and atom-type information of surface atoms as input. They report that the model outperforms several existing methods on two commonly used datasets (PDNA62 and PDNA224) and demonstrates consistent performance across three evaluation datasets.
- **Visible evidence base** Abstract, Introduction, Results (Sections 2.1 and 2.2), Discussion, Materials and Methods (Sections 4.1 to 4.6), Conclusions, Acknowledgments. Tables 1-4 and Figures 1-3 are referenced but not visible in the provided material.
- **Missing materials affecting confidence** Tables 1-4, Figures 1-3, Supplementary Materials (including sequence alignment outcomes and training curves), and details of the comparison methods' performance metrics are not provided. This limits the ability to independently verify the reported quantitative results and the claimed performance improvements.

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in structural bioinformatics, namely the prediction of DNA binding sites on protein surfaces. The use of a fully convolutional architecture (UNET with DenseNet blocks) applied directly to 3D voxelized protein surface data is a reasonable and potentially valuable approach. The authors provide a clear rationale for moving away from MLP-based methods that require fixed-size inputs. However, the provided material does not include the actual results tables and figures, which are essential for evaluating the strength of the reported performance. The methodological description is generally clear but lacks some quantitative details (e.g., number of training parameters, exact training hyperparameters, computational cost). The claims of outperformance and robustness cannot be fully assessed without the missing data. The discussion of limitations is somewhat brief, particularly regarding the clustering step and the definition of binding residues.
- **Who would be interested in the results, and why** Researchers in computational biology, structural bioinformatics, and protein function prediction would be interested. The method could have practical applications in drug discovery and in annotating protein function, particularly for proteins whose DNA-binding behavior is not yet characterized. The approach of using 3D surface information with a fully convolutional network may also be of interest to those working on similar prediction problems for other ligand types.
- **Major strengths** The problem is well motivated and relevant. The choice of a fully convolutional architecture is a sensible response to the limitations of MLP-based approaches for 3D structural data. The use of atom-type information on the protein surface is a reasonable feature representation. The authors acknowledge the issue of dataset redundancy and provide some analysis of homology between training and test sets. The writing is generally clear and accessible.
- **Major Concerns** The absence of the actual results (Tables 1-3, Figures 1-3) is a critical gap. The claim of outperformance over existing methods cannot be verified. The description of the clustering step is somewhat heuristic, and its impact on the final performance is not quantified. The authors state that the model was trained for 48 hours and stopped after roughly 2.5 epochs, which seems unusually short and may raise questions about convergence and generalizability. The definition of the binding region (6 Å cutoff) is mentioned but not critically discussed in the context of alternative definitions.
- **Minor Comments** The Introduction could be slightly more concise. The Discussion section could benefit from a more explicit comparison of the advantages and disadvantages of the proposed method relative to existing ones. The statement that "atom type alone may contain many integrated physicochemical properties" is plausible but not directly demonstrated. The Acknowledgments section contains a minor typo ("acknowledgement" should be "acknowledge").
- **Technical failings that need to be addressed before the case is established** The lack of visible results tables and figures is the primary technical failing. Without these, the core claims of the paper cannot be evaluated. Additionally, the training procedure (48 hours, 2.5 epochs) is described without sufficient context to judge whether the model was adequately trained.
- **Assessment against Nature-style criteria**  
  - **Originality:** The application of a fully convolutional UNET-like architecture to voxelized protein surface data for DNA binding site prediction is a reasonable and somewhat novel combination, though the individual components are established. The originality is moderate.  
  - **Scientific importance:** The problem is important, and a reliable method would be valuable. However, the demonstrated improvement over existing methods is not verifiable from the provided material.  
  - **Interdisciplinary readership:** The work is primarily of interest to computational biologists and bioinformaticians. The broader biological or clinical impact is not strongly articulated.  
  - **Technical soundness:** The methodological approach is sound in principle, but the lack of results prevents a full assessment. The training details are somewhat sparse.  
  - **Readability for nonspecialists:** The manuscript is generally readable, but some sections (e.g., the description of the network architecture) may be challenging for readers without a deep learning background. The abstract is clear.
- **Recommendation posture** Currently not established from the provided evidence. The core quantitative claims cannot be assessed without the missing tables and figures. The methodological approach is promising, but the case for its superiority and robustness is not made in the provided material.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that DeepDISE outperforms several existing methods on PDNA62 and PDNA224 in terms of accuracy, specificity, precision, and MCC.
- **Evidence pointer** Tables 2 and 3, location not provided
- **Concern** The actual performance metrics for DeepDISE and the comparison methods are not visible in the provided material. Without these tables, the central claim of outperformance cannot be verified or evaluated.
- **Why it matters** The primary contribution of the paper is the claimed improvement in prediction performance. If this cannot be substantiated with data, the value of the method is not established.
- **Resolution test** Provide the full tables with performance metrics for all methods on both datasets, including confidence intervals or statistical significance tests where appropriate.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the model was trained for 48 hours and stopped after roughly 2.5 epochs.
- **Evidence pointer** Section 4.4.2, location not provided
- **Concern** Training for only 2.5 epochs is unusual and may indicate that the model was not fully trained. The authors do not provide learning curves or convergence criteria. This raises questions about whether the reported performance is optimal or representative.
- **Why it matters** If the model is undertrained, the reported performance may be suboptimal, and the comparison with other methods may be unfair or misleading.
- **Resolution test** Provide training and validation loss curves over the full training period, and justify the stopping criterion. If 2.5 epochs was sufficient, explain why.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodology clarity
- **Claim pointer** The clustering step is described as using k-means with two rounds, where the score dimension is increased by 5x to bias the clustering.
- **Evidence pointer** Section 4.5, location not provided
- **Concern** The clustering procedure is described heuristically, and its impact on the final binary classification is not quantified. It is unclear how sensitive the results are to the choice of the 5x weighting factor or the number of clusters.
- **Why it matters** The clustering step is an integral part of the prediction pipeline. If it is not robust or well-justified, the reliability of the final predictions is questionable.
- **Resolution test** Provide a sensitivity analysis of the clustering parameters, or demonstrate that the final results are not strongly dependent on these choices.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Section 1, location not provided
- **Issue** The Introduction is somewhat lengthy and could be more focused on the specific gap that DeepDISE addresses.
- **Required correction** Consider condensing the background and more explicitly stating the novelty of the approach relative to prior work.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Section 3, location not provided
- **Issue** The Discussion does not critically address the choice of the 6 Å cutoff for defining binding residues, which is known to vary across studies.
- **Required correction** Add a brief discussion of how the choice of cutoff might affect results and how it compares with other definitions in the literature.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Acknowledgments
- **Evidence pointer** Acknowledgments, location not provided
- **Issue** There is a typo: "acknowledgement" should be "acknowledge".
- **Required correction** Fix the typo.

## Risk / unsupported claims
- The claim that DeepDISE outperforms existing methods on PDNA62 and PDNA224 is unsupported in the provided material because the relevant tables are not visible.
- The claim that the model demonstrates robust and consistent performance across three datasets is not fully verifiable without the results for all three datasets.
- The statement that the model does not present the issue of overfitting is not directly supported by the provided evidence, as the training and validation curves are not shown.
- The claim that atom type alone may contain many integrated physicochemical properties is plausible but not demonstrated in the provided material.