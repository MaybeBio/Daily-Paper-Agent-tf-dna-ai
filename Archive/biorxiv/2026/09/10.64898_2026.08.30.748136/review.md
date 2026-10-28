## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, and supplementary statements) as provided.
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and results as presented. No assessment of code functionality, web server availability, or data repository contents beyond what is stated.
- **Shared manuscript claim summary** The authors present PocketScope, a training-free framework that uses frozen ESM-C 600M protein language model embeddings to represent binding-site residues and performs proteome-scale retrieval of similar binding sites via exact late-interaction MaxSim. They claim it recovers documented drug off-targets, outperforms 22 existing methods on the ProSPECCTs benchmark by mean rank, and is substantially faster than Foldseek.
- **Visible evidence base** Abstract; Sections 1, 2.1–2.9, 3.1–3.6, 4, 5; references to Figures 2–6, Tables 1–4, and Supplementary Tables S1–S5. No figures, tables, or supplementary materials were provided in the submission.
- **Missing materials affecting confidence** All figures, tables, and supplementary files are referenced but not included. This includes Figure 2 (size filter validation), Figure 3 (Foldseek comparison), Figure 4 (ProSPECCTs results), Figure 5 (ablation results), Figure 6 (model size/generation sweep), Figure 7 (cofactor classification), Table 2 (ProSPECCTs summary), Table 3 (pocket size distribution), Table 4 (cofactor classification results), and Supplementary Tables S1–S5. Without these, quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and potentially useful problem: proteome-scale binding-site retrieval for off-target prediction using protein language model representations. The core idea of using per-residue embeddings with exact MaxSim, avoiding pooling and approximate search, is conceptually clean and technically plausible. However, the evidence as presented is incomplete. The central quantitative claims, including the ProSPECCTs ranking, the Foldseek comparison, and the ablation results, all depend on figures and tables that were not provided. Several methodological details are underspecified, particularly regarding the construction of the ChEMBL evaluation set and the handling of the ProSPECCTs benchmark. The claim of "training-free" is accurate in the narrow sense that no model weights are trained, but the framework still requires hyperparameter choices (e.g., alpha, size cutoff) that are tuned on external data. The discussion is honest about the method's limitations on cross-family pairs, which is commendable. Overall, the manuscript has merit but is not yet established from the provided evidence.
- **Who would be interested in the results, and why** Computational biologists and medicinal chemists working on polypharmacology, off-target prediction, and binding-site comparison. Researchers developing protein language model applications for structural biology would also be interested, as the work demonstrates a specific use case for per-residue embeddings. The claim of proteome-scale speed could be of practical interest to those screening large structural databases.
- **Major strengths** 1. The problem is well-motivated and practically relevant. 2. The method is conceptually simple and avoids complex training procedures, which aids reproducibility. 3. The use of exact MaxSim over approximate methods is a principled choice for a retrieval task. 4. The authors are transparent about the method's limitations on cross-family pairs. 5. The manuscript is generally well-written and accessible to a broad audience.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing evidence for ProSPECCTs claim), R1-M2 (underspecified ChEMBL evaluation set), R1-M3 (unclear handling of ProSPECCTs benchmark protocol), R1-M4 (incomplete ablation reporting).
- **Assessment against Nature-style criteria** Originality: Moderate. The combination of PLM embeddings with MaxSim for pocket retrieval is not entirely novel, as the authors acknowledge prior work (DeeplyTough, EPoCS), but the proteome-scale application and the specific design choices have some novelty. Scientific importance: Moderate to high. Off-target prediction is an important problem, and a scalable, accurate method would be valuable. However, the demonstrated advantage over existing methods is not yet clear from the provided evidence. Interdisciplinary readership: Moderate. The work bridges machine learning and structural biology, which could appeal to a broad audience, but the technical details may limit accessibility. Technical soundness: Currently not fully assessable due to missing figures and tables. The methodological description has some gaps. Readability for nonspecialists: Good. The manuscript is clearly written and explains concepts well, though some sections (e.g., MaxSim details) may be dense for non-experts.
- **Recommendation posture** Currently not established from the provided evidence. The core claims are plausible but cannot be verified without the missing figures, tables, and supplementary materials. The authors should be invited to resubmit with complete evidence and clarifications.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "On the ProSPECCTs benchmark, PocketScope ranks 1st of 23 methods by mean rank across the ten collections."
- **Evidence pointer** Section 3.4, Figure 4, Table 2
- **Concern** The central claim of state-of-the-art performance on ProSPECCTs is presented without any of the underlying data. Figure 4, which presumably shows the comparison across all ten collections, is not provided. Table 2, which should summarize the results, is also missing. Without these, it is impossible to assess whether the ranking is statistically meaningful, whether the comparison was fair (e.g., same train/test splits, same evaluation protocol), or whether the margin over other methods is significant.
- **Why it matters** This is the primary quantitative claim of the manuscript. If it cannot be verified, the case for PocketScope's utility is substantially weakened.
- **Resolution test** Provide Figure 4 and Table 2 with full numerical results for all 23 methods across all ten collections, including confidence intervals or statistical tests where appropriate. Clarify the exact evaluation protocol used and how it matches or differs from the original ProSPECCTs benchmark.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** "A second and larger set was assembled from ChEMBL. Every pair of human proteins sharing a reported binder gave a pool of candidate pairs, of which 855 were retained across ten equal-width sequence-identity bands."
- **Evidence pointer** Section 2.5, Figure 3
- **Concern** The construction of the ChEMBL evaluation set is underspecified. The criteria for "sharing a reported binder" are not defined (e.g., what constitutes a binder, what confidence threshold, how promiscuous compounds were handled). The selection of 855 pairs from the initial pool is not described (e.g., random sampling, balanced sampling, any filtering beyond sequence identity). The sequence-identity bands are mentioned but their boundaries and the number of pairs per band are not given. Without this information, the evaluation set may be biased or unrepresentative, and the comparison with Foldseek in Figure 3 cannot be properly interpreted.
- **Why it matters** The ChEMBL evaluation is a key part of the validation. If the set is not carefully constructed, the reported recall rates may not generalize to real off-target prediction scenarios.
- **Resolution test** Provide a detailed description of the ChEMBL data retrieval, filtering, and sampling process. Specify the exact criteria for a "reported binder," the number of pairs in each sequence-identity band, and any steps taken to avoid redundancy or bias. Include the full list of 855 pairs as a supplementary file.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "PocketScope was scored on the datasets' own pair lists with the symmetric MaxSim defined below, under ESM-C 600M in chain context as in Section 2.5."
- **Evidence pointer** Section 2.6, Section 2.3
- **Concern** The manuscript states that the ProSPECCTs benchmark distributes structures with co-crystallised ligands retained, and that pockets are defined as residues within 6.0 Å of the ligand. However, it is unclear how this definition interacts with the benchmark's intended protocol. The original ProSPECCTs benchmark may have specific definitions of binding sites or specific splits that need to be respected. The authors do not clarify whether they used the benchmark's provided pocket definitions or their own, and whether this choice could affect comparability with the 22 other methods. Additionally, the symmetric MaxSim is defined only in passing; the exact formula is not given in the text (it is referenced as "defined below" but not shown).
- **Why it matters** If the evaluation protocol deviates from the benchmark's intended use, the comparison with other methods may be unfair or invalid. The missing definition of symmetric MaxSim also hampers reproducibility.
- **Resolution test** Provide the exact formula for symmetric MaxSim. Clarify whether the pocket definitions used match those of the original ProSPECCTs benchmark, and if not, justify the deviation and discuss its potential impact on the results.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** "The pooled and per-residue scorers tie at 100% on the three same-protein collections, and across the remaining seven the two track each other within a few percentage points in either direction."
- **Evidence pointer** Section 3.5, Figure 5, Supplementary Tables S3 and S4
- **Concern** The ablation study is described qualitatively, but the actual numbers are not provided in the text. Figure 5 and Supplementary Tables S3 and S4 are referenced but not included. The claim that MaxSim "buys little over pooling" is an important negative result, but it cannot be evaluated without the data. Furthermore, the ablation for the physicochemical block is only described for a subset of collections, and the full results are not shown.
- **Why it matters** The ablation is crucial for understanding which components of the method contribute to its performance. Without the data, the reader cannot judge whether the design choices are well-supported.
- **Resolution test** Provide Figure 5 and Supplementary Tables S3, S4, and S5 with full numerical results for all ablations across all ten collections.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Equation 1
- **Evidence pointer** Section 2.2
- **Issue** The equation for the per-residue match feature is referenced but not displayed in the text provided. The description of the physicochemical descriptor is clear, but the exact composition of the feature vector is not fully specified (e.g., how the seven scalars are normalized, what "approximately [1, 1]" means precisely).
- **Required correction** Display the equation explicitly and provide the exact normalization procedure for the physicochemical descriptor.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.5, off-target evaluation pairs
- **Evidence pointer** Section 2.5, Supplementary Table S2
- **Issue** The 30 curated off-target pairs are described as "documented" with sources in Supplementary Table S2, but the criteria for inclusion are not stated. It is unclear whether these pairs were selected to be representative or were chosen because they are easy cases.
- **Required correction** State the inclusion criteria for the 30 pairs and discuss any potential selection bias.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.3, Foldseek comparison
- **Evidence pointer** Section 3.3, Figure 3
- **Concern** The comparison with Foldseek is presented as a head-to-head, but the two methods use different representations (sequence/structure alignment vs. PLM embeddings). The authors note that both search the same database, but it is unclear whether Foldseek was run with its default parameters or tuned for this task.
- **Required correction** Specify the Foldseek parameters used and discuss whether the comparison is fair given the different methodological paradigms.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.9, Implementation
- **Evidence pointer** Section 2.9
- **Issue** The web server and code are mentioned, but no version numbers, dependencies, or usage examples are provided. The Zenodo DOI is given, but the contents are not described.
- **Required correction** Provide a brief description of the repository contents, software dependencies, and a minimal usage example.

## Risk / unsupported claims
- The claim of ranking 1st of 23 on ProSPECCTs is unsupported without Figure 4 and Table 2.
- The claim of recovering 29 of 30 documented off-target pairs is unsupported without Supplementary Table S2.
- The claim of a 45-fold speed advantage over Foldseek is unsupported without timing methodology details and raw data.
- The claim that the 10-residue cutoff retains 96.7% of ligand-site recall is unsupported without Figure 2.
- The claim that the physicochemical block contributes meaningfully to performance is only weakly supported by the qualitative description in Section 3.5.
- The claim that the method is "training-free" is technically accurate but potentially misleading, as hyperparameters (alpha, size cutoff) are tuned on external data.