## Review setup
- **Input scope** Full manuscript text (preprint, Research Square, 2026)
- **Assessment boundary** Scientific content, methodology, evidence quality, and claims as presented in the provided text. No external validation or replication attempted.
- **Shared manuscript claim summary** The authors introduce PIC-NIC, a high-throughput platform that introduces site-specific single-strand breaks (nicks) into DNA to probe how backbone mechanics influence transcription factor (TF) binding. Across 15 TFs from eight structural families, they report position-specific nick sensitivity, identify mechanically sensitive sites that correlate with strained DNA geometries (e.g., Hoogsteen conformations), and show that nicks can enhance, rewire, or disrupt TF binding. They further link TF occupancy at nicked sites to potential modulation of DNA repair factor access.
- **Visible evidence base** Main text, Methods, Extended Data figure/table legends referenced in text, Supplementary Tables (referenced but not provided in full), PDB accession numbers, and genome-wide dataset accessions.
- **Missing materials affecting confidence** Supplementary Tables 1–12, Extended Data Figures 1–13, Extended Data Tables 1–3, and the Supplementary Discussion were not provided. These are essential for evaluating the quantitative claims, statistical analyses, and structural details. Molecular dynamics simulation parameters and full genome-wide analysis methods are only partially described.

## Reviewer

- **Overall assessment** This manuscript presents a conceptually interesting and technically ambitious platform for probing DNA backbone mechanics in TF recognition. The central idea, that backbone continuity at specific positions can act as a mechanical determinant of binding, is well-motivated and the data appear to support a heterogeneous, position-specific response to nicking. The integration of structural, kinetic, and genomic analyses is commendable. However, the strength of the conclusions is currently limited by the absence of key supplementary data, the reliance on a single high-throughput assay without extensive orthogonal validation, and the correlative nature of the genomic analyses. The mechanistic claims, particularly regarding Hoogsteen conformations and repair-factor interference, require more direct evidence to be fully established.
- **Who would be interested in the results, and why** Researchers in the fields of transcription factor biology, protein–DNA recognition, DNA mechanics and structure, and DNA repair. The work is also relevant to those studying the role of DNA damage in gene regulation and genome stability. The PIC-NIC platform itself may be of interest to method developers in high-throughput biochemistry.
- **Major strengths**
  1. The conceptual advance of systematically mapping "mechanical sensitivity" across TF binding sites is novel and addresses a gap in the field.
  2. The PIC-NIC platform, with its phosphate-retaining and phosphate-removing designs, is a clever approach to decouple backbone continuity from phosphate chemistry.
  3. The integration of multiple techniques (microarrays, crystallography, kinetics, MD simulations, genomics) provides a multi-layered view of the phenomenon.
  4. The identification of specific examples (ETS1, TBP, SOX2) where nicks have distinct, mechanistically interpretable effects strengthens the central thesis.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that PIC-NIC reveals a "highly position-dependent response to backbone disruption" across 15 TFs, with specific percentages of positions classified into disruption categories.
- **Evidence pointer** Fig. 2a, Extended Data Fig. 3, Supplementary Table 1 (not provided)
- **Concern** The core quantitative results, including the classification of all positions across all 15 TFs, are presented in Supplementary Table 1, which was not available for review. The main text provides only a summary (e.g., "major disruption was observed at ~30% of positions"). Without the full dataset, it is impossible to assess the reproducibility, the distribution of effects, the statistical significance of the classifications, or the validity of the "minimal/minor/major/severe" thresholds.
- **Why it matters** The central claim of the paper rests on this dataset. If the classification scheme is arbitrary or the data are noisy, the entire premise of "mechanical sensitivity" as a distinct, position-specific feature is weakened. The reader cannot evaluate the robustness of the findings.
- **Resolution test** Provide Supplementary Table 1 with all raw and processed data, including replicate information, error estimates, and the specific criteria used for classification. The main text should include a representative example of the data distribution to allow visual inspection.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The claim that PIC-NIC signal intensities "quantitatively reflect binding preferences" and correlate with KD values.
- **Evidence pointer** Methods, Extended Data Fig. 1 (not provided)
- **Concern** The manuscript states that PBM signal intensities correlate with KD values, citing prior work. However, the validation of the PIC-NIC platform itself, particularly for nicked constructs, is not described in detail. It is unclear whether the nicked DNA constructs are stable under assay conditions, whether the nick position is maintained, and whether the fluorescence readout is a faithful proxy for binding affinity for these perturbed substrates. The "thermodynamic parameters of hybridization" were evaluated computationally, but no experimental validation of the nicked duplex integrity is presented.
- **Why it matters** If the platform does not accurately report on binding affinity for nicked substrates, all downstream conclusions are compromised. The assay must be rigorously validated against an orthogonal method (e.g., ITC, SPR, or EMSA) for at least a few representative nicked constructs.
- **Resolution test** Include a validation section showing direct comparison of PIC-NIC signals with KD values measured by an orthogonal method for a panel of nicked and intact constructs. Demonstrate that the nicked duplexes are stable and correctly formed under assay conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic evidence
- **Claim pointer** The claim that nick-sensitive sites are enriched for "deviations in base-step parameters, most prominently twist and buckle" and that this supports a model of "strain-adapted DNA geometry."
- **Evidence pointer** Fig. 2e, Supplementary Table 2 (not provided)
- **Concern** The structural analysis correlating nick sensitivity with base-step deviations is described only briefly. The specific statistical test used, the correction for multiple comparisons, and the effect sizes are not reported in the main text. The analysis appears to be performed on a subset of positions (those without hydrogen bonds), but the criteria for this subset are not fully clear. The link between a static crystal structure deviation and the dynamic "strain" that a nick would relieve is inferential.
- **Why it matters** This is a key mechanistic pillar of the paper. A weak or confounded correlation would not support the claim that nicks act by relieving specific mechanical strain. The analysis needs to be transparent and robust.
- **Resolution test** Provide a detailed description of the statistical analysis, including the number of positions tested, the distribution of deviations, and the effect sizes. Show a clear, quantitative relationship between the magnitude of the structural deviation and the degree of nick sensitivity. Consider whether the analysis is confounded by other factors, such as the presence of modified bases or unusual backbone conformations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of genomic data
- **Claim pointer** The claim that genomic analyses "suggest that TF retention at nicked DNA can reduce repair-factor accessibility in a position-dependent manner."
- **Evidence pointer** Fig. 6, Extended Data Fig. 13 (not provided)
- **Concern** The genomic analyses are purely correlative. The observation that SSBs are enriched at TF binding sites and that repair synthesis shows a local minimum at the motif center is consistent with the proposed model, but it is equally consistent with other explanations (e.g., sequence-specific repair inhibition, chromatin structure effects, or the presence of other bound proteins). The resolution of the SAR-seq data (~150-200 nt) is too coarse to directly link specific nick positions to repair outcomes. The in vitro competition experiments with PARP1 are more direct, but the results are described qualitatively and the data are not shown.
- **Why it matters** The claim that TF binding can modulate repair is a significant and potentially impactful conclusion. However, the evidence presented is not sufficient to establish a causal or even a clear mechanistic link. Overstating this finding could mislead the field.
- **Resolution test** Either temper the claims to reflect the correlative nature of the data, or provide more direct evidence. This could include higher-resolution repair mapping, experiments where the TF binding site is mutated to alter its affinity for the nicked DNA, or in vitro repair assays with defined nicked substrates in the presence and absence of TF.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The claim that the findings "systematically map DNA backbone mechanics as a position-resolved layer of TF recognition across diverse protein families."
- **Evidence pointer** Fig. 2a, Extended Data Fig. 2 (not provided)
- **Concern** The panel of 15 TFs is described as diverse, but the selection criteria are not stated. It is unclear if this is a representative sample of TF families or a convenience sample. The observation that "features of PIC-NIC profiles are shared within some structural classes" is based on a small number of family members (e.g., only two bZIP factors). The generalizability of the findings to the broader TF repertoire is therefore uncertain.
- **Why it matters** The title and abstract imply a general principle. If the findings are specific to the chosen TFs or DNA sequences, the impact is significantly reduced. The authors should be more cautious in their claims of generality.
- **Resolution test** Clarify the selection criteria for the TF panel. Discuss the limitations of the sample size for each family. If possible, include a broader range of TFs or provide a rationale for why the chosen set is representative.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, PIC-NIC library design
- **Evidence pointer** Methods section
- **Issue** The description of the two library designs (phosphate-retaining and phosphate-removing) is clear, but the exact method for generating the nicked constructs (e.g., enzymatic vs. chemical synthesis) is not fully detailed.
- **Required correction** Provide a more detailed description of the oligonucleotide synthesis and annealing steps, including the source of enzymes or chemicals used to create the nicks.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Genome-wide analysis
- **Evidence pointer** Methods, Fig. 6
- **Issue** The permutation testing for SSB enrichment is mentioned, but the number of permutations, the specific test statistic, and the resulting p-values are not reported in the main text.
- **Required correction** Include the key statistical parameters and results in the main text or in the Methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 2d-e (CTCF example)
- **Evidence pointer** Fig. 2d-e
- **Issue** The CTCF example is compelling, but the figure legend does not clearly state the statistical significance of the difference between the nick-sensitive and nick-insensitive positions.
- **Required correction** Add significance indicators (e.g., p-values) to the figure or its legend.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract
- **Issue** The term "mechanical strain" is used throughout, but its precise definition in the context of a DNA duplex is not provided. It is used to describe both static structural deviations and dynamic energetic penalties.
- **Required correction** Provide a clear operational definition of "mechanical strain" as used in this study, and distinguish it from related concepts like "bendability" or "flexibility."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the potential in vivo relevance of the findings is speculative and does not fully consider alternative interpretations of the genomic data.
- **Required correction** Add a paragraph acknowledging the limitations of the correlative genomic analyses and discussing alternative models that could explain the observed patterns.

- **Technical failings that need to be addressed before the case is established**
  1. Lack of access to Supplementary Tables 1–12, which contain the primary quantitative data (R1-M1).
  2. Insufficient validation of the PIC-NIC platform for nicked substrates (R1-M2).
  3. Incomplete description of the structural statistical analysis (R1-M3).
  4. Overstated conclusions from correlative genomic data (R1-M4).

- **Assessment against Nature-style criteria**
  - **Originality** High. The concept of systematically mapping "mechanical sensitivity" at nucleotide resolution is a novel contribution that goes beyond standard base-preference or phosphate-interference analyses.
  - **Scientific importance** Potentially high. If the findings are robust, they could reshape our understanding of TF–DNA recognition and its modulation by DNA damage and chromatin dynamics. The link to DNA repair is particularly significant.
  - **Interdisciplinary readership** Broad. The work bridges structural biology, biophysics, genomics, and DNA repair, and should appeal to a wide audience.
  - **Technical soundness** Currently not fully established. The core platform is clever, but the lack of detailed validation and the incomplete presentation of key data prevent a full assessment. The structural and genomic analyses are suggestive but not definitive.
  - **Readability for nonspecialists** Good. The main text is clearly written and the conceptual framework is accessible. The figures, as described, appear to be well-designed to convey the main points.

- **Recommendation posture** Supportive if technical concerns are resolved. The central idea is promising and the initial data are intriguing. However, the manuscript in its current form does not fully establish the case. The authors must provide the missing supplementary data, strengthen the validation of the platform, and temper the conclusions drawn from the correlative genomic analyses. If these issues are addressed, this could be a significant contribution.