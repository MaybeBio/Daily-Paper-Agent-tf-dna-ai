## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the provided text
- **Shared manuscript claim summary** The authors present a high-throughput screening platform (histFlow) to identify histone sequence variants that modulate chromatin organization in human cells. They identify H4 tail mutants, particularly H4G4D, that disrupt heterochromatin through cis and trans mechanisms, alter transcription factor binding landscapes, and potentiate TF-driven proliferation. They further develop a predictive model (histForge) trained on double-mutant screening data to design synthetic histone variants (synH4) with enhanced heterochromatin-repressing activity.
- **Visible evidence base** Abstract, Introduction, Results sections (4 main sections), Discussion, Materials and Methods, Funding, Author contributions, Competing interests, Data availability statement
- **Missing materials affecting confidence** Figure panels and legends (Figures 1-4, S1-S5 referenced but not provided), raw screening data, statistical analysis details, validation datasets, code availability, accession numbers for deposited data

## Reviewer

- **Overall assessment** This manuscript presents an ambitious and potentially impactful framework for engineering histone variants to modulate chromatin state. The combination of evolutionary sequence mining, high-throughput pooled screening, mechanistic dissection, and machine learning-guided design is conceptually novel and methodologically sophisticated. The identification of H4G4D as a dominant heterochromatin disruptor with both cis and trans effects is intriguing, and the demonstration that histone mutants can potentiate TF-driven phenotypes is a significant conceptual advance. However, the manuscript as presented has several critical gaps that prevent full evaluation: key figure data are not available, statistical rigor of the screening pipeline is not fully described, the mechanistic basis for the trans effects remains speculative, and the predictive performance of histForge is modest. The work is likely to be of broad interest to chromatin biologists, synthetic biologists, and those interested in cellular reprogramming, but the current evidence base is insufficient to fully establish the central claims.

- **Who would be interested in the results, and why** Chromatin biologists studying histone variants and nucleosome dynamics would find the systematic mutagenesis approach valuable. Synthetic biologists interested in engineering chromatin state would be attracted to the histForge design framework. Researchers in cellular reprogramming and regenerative medicine would be interested in the demonstration that histone variants can potentiate TF-driven phenotypes. Evolutionary biologists studying histone sequence diversity across species would also find the phylogenetic mining approach relevant.

- **Major strengths** 1) The evolutionary mining strategy to build a gain-of-function histone variant library is conceptually novel and well-motivated. 2) The histFlow platform enables systematic, quantitative assessment of histone variant effects on chromatin state at scale. 3) The identification of non-PTM-site mutations in the H4 tail as dominant modulators of heterochromatin challenges existing paradigms. 4) The combination of imaging, proteomics, and genomics to dissect mechanism is comprehensive. 5) The integration of double-mutant screening with protein language models for predictive design represents a forward-looking approach.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "By expressing libraries of sequence variants of core histones in human cells, we identify variants that dominantly modulate chromatin structure."
- **Evidence pointer** Results section "histFlow screens reveal modulators of global chromatin organization"; Figures 1D-1J referenced but not provided
- **Concern** The screening methodology relies on pooled lentiviral libraries with flow cytometry-based sorting of top and bottom 10% of cells based on chromatin accessibility (ATAC-see) or histone modification staining. However, the manuscript does not provide details on the dynamic range of the sorting gates, the reproducibility of the screen across biological replicates, the false discovery rate for hit calling, or the validation rate of individual hits. The R² values of 0.88-0.92 between replicates are reported, but the criteria for defining "significant" enrichment or depletion (signed FDR < 0.05) are not contextualized with effect size thresholds. Without these details, it is difficult to assess whether the identified variants represent robust biological effects or technical artifacts of the screening pipeline.
- **Why it matters** The entire manuscript rests on the reliability of the histFlow screening platform. If the hit-calling criteria are not rigorously defined and validated, all downstream claims about specific mutants (including H4G4D) and the training data for histForge are compromised.
- **Resolution test** Provide detailed screening statistics including: number of biological replicates, sorting gate definitions, hit-calling thresholds with effect sizes, validation rates of individual mutants in orthogonal assays, and a comparison of screen results with known histone mutant phenotypes as a positive control.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** "We highlight the H4G4D mutant, which disrupts heterochromatin in cis and trans, alters spatial compartmentalization within the nucleus, and reconfigures the functional TF binding landscape in T cells."
- **Evidence pointer** Results section "Spatial characterization of H4 tail mutants"; Figures 2A-2L, S3A-S3G referenced but not provided
- **Concern** The claim of both cis and trans mechanisms is central to the paper's conceptual contribution, yet the evidence presented in the text is insufficient to distinguish these mechanisms. The imaging data showing GFP-H4G4D exclusion from heterochromatin foci (Figure 2B, 2E) could reflect either cis effects (altered nucleosome properties preventing heterochromatin incorporation) or trans effects (sequestration of heterochromatin factors). The RIME proteomics data (Figure 2J, S3D-G) identifies differential interactors, but the text only mentions loss of macroH2A.1 interaction and gain of lamin/nucleophosmin interactions without quantitative details. The claim that H4G4D causes "downstream trans effects via altered partitioning of chromatin components" (based on HP1a localization changes in Figure 2I) is suggestive but not definitive evidence of a trans mechanism.
- **Why it matters** The cis/trans distinction is a major conceptual claim of the paper. If the evidence does not clearly separate these mechanisms, the mechanistic model proposed is not established. This distinction also has implications for how the field would think about using such mutants therapeutically.
- **Resolution test** Provide quantitative imaging data showing the fraction of H4G4D nucleosomes within versus adjacent to heterochromatin domains, time-course experiments showing whether HP1a displacement precedes or follows H4G4D incorporation, and proteomics data with statistical comparisons showing differential interactors with effect sizes and significance values.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Functional screening with transcription factor libraries identifies transcriptional programs that are facilitated by engineered histone expression."
- **Evidence pointer** Results section "H4G4D alters the transcription factor binding chromatin landscape"; Figures 3A-3I, S4A-S4E referenced but not provided
- **Concern** The TF screening data are presented with limited methodological detail. The MORF595 library is described, but the screen design (overexpression of TFs in H4G4D versus H4 background), the proliferation readout, and the statistical framework for identifying "role switchers" are not fully described. The R² of 0.62-0.65 between screen replicates is notably lower than the histFlow screens, raising concerns about reproducibility. The validation of LEF1 as a "role switcher" is mentioned, but the text does not provide the magnitude of the effect, the number of replicates, or the specificity of the effect (i.e., whether LEF1 also promotes proliferation in other chromatin contexts).
- **Why it matters** The claim that histone variants can "license" TF activity is a key translational implication of the work. If the screening data are noisy or the validation is incomplete, this claim is not supported. The modest replicate correlation suggests the screen may have high technical variability.
- **Resolution test** Provide detailed screen statistics including replicate numbers, effect sizes for LEF1 and other "role switchers," specificity controls (e.g., LEF1 overexpression in wild-type cells), and orthogonal validation of LEF1 target gene activation in H4G4D cells.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Double mutation screens combined with protein language models allow us to learn sequence-to-function patterns and design synthetic histone proteins optimized to drive specific chromatin states."
- **Evidence pointer** Results section "Evolved and designed histones"; Figures 4A-4K, S5A-S5H referenced but not provided
- **Concern** The histForge model is described as a binary classifier predicting H3K9me3 repression probability, with an enrichment of 1.51x over random guessing for top-ranked predictions. This performance metric is modest and its practical utility is unclear. The manuscript does not report the AUC, precision-recall characteristics, or the false discovery rate among top predictions. The validation of designed synH4s is described qualitatively ("successfully decreased H3K9me3 levels past the level of G4D alone"), but quantitative data with statistical comparisons are not provided in the text. The claim that synH4s "integrated correctly into interphase and mitotic chromatin" is based on imaging data not shown. The statement about "∼10^39 possible combinations" is not contextualized with the actual search space explored.
- **Why it matters** The predictive design capability is a central claim of the paper and represents the "synthetic biology" contribution. If the model performance is marginal and the validation is not rigorously quantified, the claim that the authors can "design" histone variants with predictable effects is not established.
- **Resolution test** Report full model performance metrics (AUC, precision-recall, calibration), provide quantitative validation data for designed synH4s with statistical comparisons to G4D and wild-type controls, and describe the search algorithm and computational cost more precisely.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence strength
- **Claim pointer** "We make the first advance towards engineered histone-driven chromatin organization."
- **Evidence pointer** Abstract; Introduction
- **Concern** The claim of "first advance" is strong and requires careful contextualization against prior work. The authors cite prior studies using histone variants for cell reprogramming and senescence, but do not systematically discuss whether any prior work has attempted engineered histone design. The phrase "first advance" is ambiguous: first in the field of synthetic histones? First high-throughput screen? First predictive model? Without clear scoping, this claim is difficult to evaluate.
- **Why it matters** Priority claims are important for the field and for the authors' scientific credit. An imprecise or overstated priority claim could be challenged by reviewers or readers familiar with related work.
- **Resolution test** Clarify the scope of the "first advance" claim and provide a more systematic comparison with prior efforts to engineer histones or chromatin-associated proteins.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Throughout
- **Issue** The term "histFlow" is used to describe both the screening platform and the specific screens performed. The term "histForge" is used for the predictive model. While these names are memorable, the manuscript would benefit from a clear definition of the scope of each term early in the text.
- **Required correction** Define histFlow and histForge explicitly in the Introduction or at first use, and use consistent terminology throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data and materials availability section
- **Issue** The data availability statement indicates that data and code are still being uploaded, with the preprint to be updated "soon." This is understandable for a preprint, but the statement is vague about timelines and specific contents.
- **Required correction** Provide a more specific timeline for data deposition and list the specific datasets and code repositories that will be made available.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods
- **Evidence pointer** Materials and Methods, "Computational nomination of histone sequence variants"
- **Issue** The filtering criteria for the evolutionary sequence mining are described, but the threshold of "more than 20% different by amino acid content" is not justified. The rationale for this cutoff and its impact on the final library composition are not discussed.
- **Required correction** Provide justification for the 20% cutoff and discuss how varying this threshold might affect the library composition and screening results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Screen analysis
- **Evidence pointer** Materials and Methods, "Screen sequencing and data analysis"
- **Issue** The use of DESeq2 for analyzing screen data is mentioned, but the specific design formula, the handling of technical versus biological replicates, and the multiple testing correction approach are not described.
- **Required correction** Provide the full statistical model used for DESeq2 analysis, including design formula, replicate structure, and multiple testing correction method.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the "chassis-tail paradigm" is conceptually interesting but somewhat speculative. The authors do not address potential limitations of this paradigm, such as whether the tail can be arbitrarily engineered without affecting nucleosome stability or histone chaperone recognition.
- **Required correction** Add a paragraph discussing potential limitations and constraints of the chassis-tail paradigm, including consideration of biophysical constraints on tail sequence diversity.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Materials and Methods, "Cell culture"
- **Issue** The methods state that multiple FBS lots were tested and one was selected, but the criteria for selection and the potential batch effects are not described.
- **Required correction** Provide the criteria for FBS lot selection and discuss potential batch effects on screening results.

## Risk / unsupported claims
- The claim of "first advance towards engineered histone-driven chromatin organization" is not fully contextualized against prior work and may be overstated.
- The mechanistic distinction between cis and trans effects of H4G4D is not clearly established from the evidence described in the text.
- The claim that histForge can "design" synthetic histones with predictable effects is based on modest model performance (1.51x enrichment) and qualitative validation.
- The claim that synH4s "integrated correctly into chromatin" is based on imaging data not shown in the provided text.
- The statement that engineered histones could be used for "cellular reprogramming" and "synthetic genome engineering" in the Discussion is speculative and not directly supported by the data presented.
- The claim that all screened variants were "compatible with life" based on viability screens is only supported for the time scale of the screen (5 days) and in specific cell types (K562, Jurkat).
- The generalizability of the histFlow approach to other cell types and chromatin states beyond those tested is not demonstrated.