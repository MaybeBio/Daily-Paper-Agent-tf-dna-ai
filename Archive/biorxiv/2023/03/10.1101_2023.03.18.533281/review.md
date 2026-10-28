## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness based solely on the provided text
- **Shared manuscript claim summary** The authors propose that pioneer-factor (PF) activity is not a binary intrinsic property but occurs on a spectrum, regulated by protein-intrinsic features (e.g., regions outside the DNA-binding domain) and context-dependent factors (e.g., motif content, local chromatin state, protein concentration). Using ectopic expression of Zelda, Grainy head, and Twist in Drosophila S2 cells, they classify binding sites into three classes and argue that high chromatin occupancy is a key determinant of pioneering activity.
- **Visible evidence base** Results sections describe ChIP-seq, ATAC-seq, RNA-seq, CUT&RUN, and immunostaining experiments; references to Extended Data Figures 1–10, Figure 1–6, and Supplementary Tables 1–2; methods for cell culture, induction, immunoblotting, ChIP-seq, RNA-seq, ATAC-seq, CUT&RUN, and data analysis
- **Missing materials affecting confidence** Figure panels and legends, exact statistical parameters, quality metrics for sequencing data, replicate numbers, and detailed bioinformatics parameters for published data reanalysis; no raw data or code were inspected

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question in gene regulation: what determines pioneer-factor binding and chromatin-opening activity. The use of a well-controlled ectopic expression system in S2 cells is a strength, allowing separation of protein-intrinsic from context-dependent effects. The classification of binding sites into three functional classes is conceptually useful. However, the evidence as presented is incomplete in several key areas: the distinction between class II and III sites relies on correlative analyses without direct mechanistic validation; the claim that regions outside the DBD are required for binding and opening is based on DBD-only constructs without demonstrating that these regions are sufficient or identifying the responsible sequences; and the concentration-dependence experiments lack quantitative dose-response analysis. The manuscript would be strengthened by additional experiments or clearer presentation of existing data.
- **Who would be interested in the results, and why** Researchers studying transcription factor biology, chromatin structure, gene regulation, and developmental biology. The findings have implications for understanding cell-fate specification, reprogramming, and diseases caused by pioneer-factor misexpression. The conceptual framework of a "spectrum" of pioneering activity will be of broad interest.
- **Major strengths** 1) Well-designed ectopic expression system in a cell type lacking endogenous expression of the factors, enabling controlled analysis. 2) Integration of multiple genome-wide datasets (ChIP-seq, ATAC-seq, RNA-seq) to classify binding sites and link binding to function. 3) Comparative analysis of three factors with distinct DNA-binding domains, providing generality. 4) Direct testing of concentration dependence and DBD-only constructs, addressing mechanistic questions.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (class II/III distinction), R1-M2 (DBD-only interpretation), R1-M3 (concentration dependence quantification), R1-M4 (H3K27me3 inhibitor specificity)
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate to high. The concept of a spectrum of pioneering activity is not entirely new but is articulated clearly and supported with comparative data.  
  *Scientific importance*: High. Understanding PF regulation is central to developmental biology and reprogramming.  
  *Interdisciplinary readership*: Moderate. Primarily of interest to chromatin and transcription biologists; may appeal to computational biologists given the genomic analyses.  
  *Technical soundness*: Currently not fully established due to missing controls and quantitative details.  
  *Readability for nonspecialists*: Good. The writing is clear, and the conceptual framing is accessible, though some genomic methods may require background knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The core claims are plausible and potentially important, but the current evidence does not fully establish the mechanistic conclusions.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Data interpretation / claim support  
- **Claim pointer** The authors claim that class II and III sites are distinct in that class III sites undergo chromatin opening upon PF binding, while class II sites do not, and that this difference is driven by motif content.  
- **Evidence pointer** Results section "Chromatin opening by pioneer factors is driven by motif content"; Figures 1 and 3; Extended Data Figures 5 and 6  
- **Concern** The classification of sites into class II and III is based on differential ATAC-seq signal, but the authors do not provide a clear threshold or statistical framework for this classification. It is unclear whether class II sites are truly bound but not opened, or whether they represent weaker binding events that fall below a detection threshold. The claim that motif content drives the difference is correlative; no perturbation of motif number or strength is performed to establish causality.  
- **Why it matters** The central conclusion that pioneering activity is determined by the level of chromatin occupancy (and thus motif content) rests on this distinction. If class II sites are simply low-affinity binding events, the conclusion would be trivial.  
- **Resolution test** Provide a clear definition of class II vs. III with statistical thresholds. Perform motif mutagenesis or use synthetic reporters to test whether increasing motif number/strength converts class II to class III behavior. Alternatively, show that class II sites can be opened at higher PF concentrations, linking occupancy directly to opening.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Experimental design / interpretation  
- **Claim pointer** The authors claim that regions outside the DNA-binding domain are required for binding and opening of closed chromatin, based on DBD-only constructs.  
- **Evidence pointer** Results section "Pioneer-factor binding and chromatin opening is concentration dependent" and "Regions outside the DNA-binding domain are required for binding and opening of closed chromatin"; Figure 6; Extended Data Figure 10  
- **Concern** The DBD-only constructs may have lower protein stability, different nuclear localization, or reduced DNA-binding affinity compared to full-length proteins. The authors do not report protein levels of DBD-only constructs relative to full-length, nor do they assess DNA-binding affinity directly. The conclusion that regions outside the DBD are required for binding to closed chromatin is therefore not firmly established.  
- **Why it matters** This is a key mechanistic claim about protein-intrinsic features. If the DBD-only phenotype is due to trivial reasons (e.g., low expression), the conclusion is invalid.  
- **Resolution test** Measure protein levels of DBD-only constructs by immunoblot and normalize for expression. Perform electrophoretic mobility shift assays (EMSAs) or similar to compare DNA-binding affinity of DBD-only vs. full-length proteins. If possible, rescue DBD-only binding by fusing to a heterologous activation domain or oligomerization domain to test whether the requirement is specific.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Quantitative analysis  
- **Claim pointer** The authors claim that pioneer-factor binding and chromatin opening are concentration dependent.  
- **Evidence pointer** Results section "Pioneer-factor binding and chromatin opening is concentration dependent"; Figure 5; Extended Data Figure 9  
- **Concern** The concentration-dependence experiments are described qualitatively. No dose-response curves, EC50 values, or statistical comparisons across concentrations are provided. It is unclear whether the effects are linear, saturable, or cooperative.  
- **Why it matters** The claim that "the level of chromatin occupancy is a key determinant of pioneering activity" requires quantitative support. Without dose-response analysis, it is not possible to assess the relationship between occupancy and opening.  
- **Resolution test** Provide quantitative analysis of ChIP-seq and ATAC-seq signal across concentrations, with statistical tests for trend. Fit dose-response curves and report parameters. If possible, correlate occupancy levels with opening at individual sites.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Experimental design / interpretation  
- **Claim pointer** The authors use tazemetostat to test whether H3K27me3 restricts PF binding, concluding that H3K27me3 is not a barrier.  
- **Evidence pointer** Results section "Cell-type specific variables affect Zld, Grh and Twi binding"; Extended Data Figure 8  
- **Concern** Tazemetostat is a competitive inhibitor of EZH2, but its efficacy in S2 cells is not demonstrated. The authors report reduced H3K27me3 levels but do not quantify the extent of reduction or assess potential off-target effects. The conclusion that H3K27me3 is not a barrier is based on a single inhibitor concentration and time point.  
- **Why it matters** This is a negative result that informs the model of context-dependent regulation. If the inhibitor is ineffective, the conclusion is unsupported.  
- **Resolution test** Quantify H3K27me3 reduction by CUT&RUN or ChIP-qPCR. Include a positive control (e.g., a known PRC2 target) to demonstrate functional inhibition. Test multiple concentrations and time points. Consider genetic depletion of PRC2 components as an alternative.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity / presentation  
- **Affected element** Classification of binding sites  
- **Evidence pointer** Results section "Ectopically expressed pioneer factors bind and open closed chromatin"; Figure 1  
- **Issue** The terms "class I, II, III" are introduced without a clear schematic or summary table in the main text. The reader must infer the definitions from the text.  
- **Required correction** Add a schematic figure or table summarizing the classification criteria and the number of sites in each class for each factor.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Data availability  
- **Affected element** Published data reanalysis  
- **Evidence pointer** Methods section "Analysis of previously published data"; Supplementary Table 2  
- **Issue** The authors state that published datasets were analyzed "in parallel" but do not specify which parameters were used for normalization or peak calling for each dataset.  
- **Required correction** Provide a detailed table of analysis parameters for each published dataset, including alignment, peak calling, and normalization methods.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical reporting  
- **Affected element** Differential expression and accessibility analyses  
- **Evidence pointer** Methods section "RNA-seq analysis" and "ATAC-seq analysis"  
- **Issue** The thresholds for differential expression (adjusted p-value < 0.05, fold change > 2) are stated, but the number of replicates and the dispersion estimation method are not described.  
- **Required correction** Specify the number of biological replicates for each condition and the DESeq2 settings used.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Class I sites  
- **Evidence pointer** Results section "Ectopically expressed pioneer factors bind and open chromatin"; Figure 1  
- **Issue** The authors note that class I sites are accessible in wild-type cells and remain accessible upon binding, but they do not discuss whether these sites are functionally relevant or simply represent non-specific binding to open chromatin.  
- **Required correction** Add a brief discussion of the potential significance of class I sites, or explicitly state that they are not the focus of the study.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "Physiological levels"  
- **Evidence pointer** Methods section "Induction of transcription factor expression"  
- **Issue** The term "physiological levels" is used but not defined quantitatively. It is unclear how these levels were determined to match endogenous expression.  
- **Required correction** Provide a reference or method for determining physiological levels, such as comparison to endogenous protein levels in embryos or tissues.

## Risk / unsupported claims
- The claim that "pioneering activity is not a binary feature intrinsic to a protein but occurs on a spectrum" is a conceptual interpretation that is not directly tested; it is inferred from the data.
- The claim that "regions outside the DNA-binding domain are required for binding and opening of closed chromatin" is not fully supported because DBD-only constructs may have reduced stability or affinity.
- The claim that "H3K27me3 is not a barrier to PF binding" is based on a single inhibitor treatment without demonstrated efficacy.
- The claim that "increased chromatin occupancy, as assayed by ChIP-seq, could result in chromatin accessibility" is correlative; no causal link is established.
- The generalizability of the findings to other pioneer factors or in vivo contexts is not tested, and the authors do not provide evidence that the S2 cell system recapitulates endogenous regulation.