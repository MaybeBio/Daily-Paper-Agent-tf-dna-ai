## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, data/code availability statements)
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text; no external validation or replication attempted
- **Shared manuscript claim summary** The authors present a computational method (NISE) combining a novel graph neural network (LASErMPNN) for sequence design with an existing structure prediction network (RoseTTAFold-All Atom) to achieve zero-shot design of small-molecule binding proteins, demonstrated on the drug exatecan with 100% experimental hit rate and affinities reaching the low nanomolar range after neural proofreading.
- **Visible evidence base** Abstract, main text sections (NISE algorithm, LASErMPNN, design, characterization), methods descriptions, supplementary figure/table references, data availability statements
- **Missing materials affecting confidence** Supplementary figures and tables (E1-E25, S1-S5, T1-T3) referenced but not provided; experimental raw data (binding curves, crystallographic statistics) not shown; sequence alignments and structural coordinates not available for inspection

## Reviewer
- **Overall assessment** This manuscript presents a compelling computational framework for de novo design of small-molecule binding proteins, with impressive experimental validation. The core innovation, LASErMPNN, extends existing message-passing architectures with ligand awareness and sidechain prediction, and the NISE iterative algorithm demonstrates clear advantages over traditional energy-based optimization. The experimental results, particularly the 100% hit rate and sub-nanomolar affinity after proofreading, are notable. However, several technical aspects require clarification, and the absence of key supplementary data limits full evaluation of the claims.

- **Who would be interested in the results, and why** Computational protein designers, structural biologists, and drug delivery researchers would find this work directly relevant. The method addresses a long-standing challenge in the field and offers a practical pipeline that could be adopted for other ligand targets. The neural proofreading concept may also interest those working on affinity maturation and protein engineering more broadly.

- **Major strengths** 1) The NISE algorithm is conceptually elegant, leveraging reciprocal neural networks to navigate the joint sequence-structure-ligand space without energy functions. 2) The experimental validation is thorough, with multiple designs tested and structural confirmation via X-ray crystallography. 3) The neural proofreading approach demonstrates a novel use of the model for affinity maturation, achieving dramatic improvements. 4) The benchmarking against existing methods (LigandMPNN, Rosetta) provides useful context for the field.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that LASErMPNN outperforms LigandMPNN in sequence recovery and design quality is central to the method's novelty.
- **Evidence pointer** Figure 2b, Table E1, Figures S3-S5
- **Concern** The comparison with LigandMPNN appears incomplete. The authors state that LigandMPNN training code and dataset are not publicly available, and they reconstruct the training set. However, the details of this reconstruction, including how sequence identity clustering was performed and whether the test set truly represents a fair comparison, are not fully described. The reported performance differences are modest, and the statistical significance of these differences is not established.
- **Why it matters** The claimed superiority of LASErMPNN over existing methods is a key selling point. If the comparison is not rigorously controlled, the incremental benefit of the new architecture becomes unclear.
- **Resolution test** Provide full details of the LigandMPNN reconstruction, including clustering parameters, and report confidence intervals or statistical tests for the performance differences. Ideally, the authors should also compare against the original LigandMPNN weights on a common benchmark.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The NISE algorithm is claimed to optimize the joint distribution of sequence, structure, and ligand conformation, converging to high-confidence modes.
- **Evidence pointer** Figure 1c, Figure E5, Figure E24
- **Concern** The convergence behavior of NISE is not rigorously characterized. The authors show that ligand pLDDT and sequence NLL improve over iterations, but the criteria for convergence are not defined. It is unclear how many independent NISE trajectories were run, whether they converge to similar solutions, and how sensitive the final designs are to the initial pose and random seed. The comparison with Rosetta-based optimization (Figure E6) is also limited to a single trajectory.
- **Why it matters** For a method to be broadly adopted, its reproducibility and robustness must be established. If NISE is highly sensitive to initial conditions, its practical utility is diminished.
- **Resolution test** Run multiple independent NISE trajectories from different initial poses and random seeds, report the distribution of final metrics (pLDDT, NLL, RMSD), and define explicit convergence criteria. Provide a more comprehensive comparison with Rosetta-based optimization across multiple trajectories.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The claim that the designed proteins protect exatecan from hydrolysis, with potential applications in drug delivery, is a significant translational claim.
- **Evidence pointer** Figure 6, Figures E22-E23
- **Concern** The hydrolysis protection experiments are described only briefly. The kinetic model used to fit the time-resolved absorption data is not fully specified, and the constraint applied to the EPIC fit (90% ring-closed equilibrium) appears to be derived from a thermodynamic model that is not described. The physiological relevance of the PBS buffer experiments is unclear, and the single experiment with HSA shows a growing scattering component that complicates interpretation.
- **Why it matters** The translational potential of the designed proteins depends on their ability to protect the drug in relevant biological conditions. If the protection is only demonstrated in simplified buffer systems, the claim is overstated.
- **Resolution test** Provide full details of the kinetic and thermodynamic models, including equations and parameter values. Perform hydrolysis experiments in more physiologically relevant conditions (e.g., plasma or serum) and quantify the protection effect with appropriate controls.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The X-ray crystal structures confirm the designed binding mode and structural accuracy of EPIC and EPIC Q51N.
- **Evidence pointer** Figure 5, Tables S4-S5
- **Concern** The crystallographic analysis is presented with limited detail. The resolution of 2.0 Å is reasonable, but the refinement statistics (R-free, Ramachandran outliers, B-factors) are not reported in the main text. The comparison between the designed model and the experimental structure is described qualitatively, but quantitative measures (e.g., RMSD over the binding site) are not provided. The electron density for the ligand is not shown.
- **Why it matters** Structural validation is critical for computational design claims. Without detailed crystallographic statistics and quantitative comparisons, the accuracy of the design cannot be fully assessed.
- **Resolution test** Provide complete refinement statistics in the main text or supplementary tables, show electron density maps for the ligand and binding site, and report quantitative RMSD values between the design model and experimental structure for the backbone, binding site, and ligand.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The schematic in Figure 1 is referenced multiple times but not described in the text. The relationship between panels a-d is unclear without a figure legend.
- **Required correction** Add a brief description of each panel in the main text or ensure the figure legend is comprehensive.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, LASErMPNN training
- **Evidence pointer** Methods section
- **Issue** The training details for LASErMPNN are incomplete. The number of training epochs, batch size, learning rate schedule, and data augmentation strategies are not fully specified. The statement "trained until convergence" is vague.
- **Required correction** Provide complete training hyperparameters and convergence criteria in the methods or supplementary information.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code availability
- **Evidence pointer** Code availability statement
- **Issue** The code repositories are mentioned, but it is unclear whether they contain the full training pipeline, the NISE implementation, and the specific model weights used for the exatecan designs.
- **Required correction** Clarify what exactly is available in each repository and provide a versioned release with documentation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations is brief. The authors acknowledge RFAA's difficulty with ligand orientation but do not discuss potential failure modes of the overall approach, such as targets with flexible ligands or non-drug-like small molecules.
- **Required correction** Expand the discussion of limitations and potential scope of applicability.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Experimental methods
- **Evidence pointer** Methods, binding assays
- **Issue** The fluorescence polarization binding assays are described, but the protein concentrations used, the number of replicates, and the error bars in Figure 3f are not specified.
- **Required correction** Provide experimental details for the binding assays, including replicate numbers and error analysis.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract claims "100% hit rate" but this refers to 4 out of 4 tested designs. While impressive, the sample size is small, and the claim could be misinterpreted as a general property of the method.
- **Required correction** Qualify the claim with the sample size, e.g., "all four tested designs."

## Risk / unsupported claims
- The claim that LASErMPNR outperforms LigandMPNN is not fully supported due to incomplete comparison details and lack of statistical testing.
- The claim that NISE converges to a high-probability mode in the joint distribution is not rigorously demonstrated; convergence criteria and trajectory variability are not reported.
- The claim that designed proteins protect exatecan from hydrolysis "for days" is based on a single experiment with a constrained kinetic model; the robustness of this finding is unclear.
- The claim that the method achieves "zero-shot" design is somewhat misleading, as the initial pose was generated by COMBS and Rosetta, which required substantial computational effort and filtering.
- The generalizability of the method to other ligands and protein scaffolds is not demonstrated; only one target (exatecan) and one fold (four-helix bundle) are presented.