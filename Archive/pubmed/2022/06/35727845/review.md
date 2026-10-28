## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Materials and methods) as provided by the user.
- **Assessment boundary** The scientific content, methodology, data interpretation, and claims as presented in the provided text. No external data, figures, or supplementary files were accessed.
- **Shared manuscript claim summary** The authors propose that missense variants causing Wiedemann-Steiner syndrome (WDSTS) are preferentially located in the CXXC domain of KMT2A, not the catalytic SET domain. They support this with genetic enrichment analyses and mouse model data showing disrupted histone methylation at CpG-rich regions without systematic gene expression changes. They further present an AlphaFold2-based classifier for missense variants in the CXXC domain, reporting high predictive values and applying it to an in silico saturation mutagenesis of 445 variants.
- **Visible evidence base** The manuscript text includes descriptions of statistical tests (Fisher's exact test), specific p-values, effect sizes (e.g., 61.9-fold enrichment), classifier performance metrics (92.6% PPV, 92.9% NPV), and methodological details for ChIP-seq, RNA-seq, and AF2 structure prediction. Specific figure and table references are made but their contents are not visible.
- **Missing materials affecting confidence** The actual figures, tables, and supplementary files are not provided. This includes the detailed results of the enrichment analysis (Fig 1), the mouse histone methylation and expression data (Fig 2), the classifier performance metrics (Fig 3), and the saturation mutagenesis results (Fig 4). The specific list of variants used for training and testing the classifier is also not visible.

## Reviewer
- **Overall assessment** This manuscript addresses a clinically relevant question in a Mendelian disorder of the epigenetic machinery. The genetic enrichment analysis is straightforward and the finding of CXXC domain enrichment is potentially important. However, the manuscript's central claim is weakened by the lack of visible data for the key figures, making it impossible to fully assess the robustness of the statistical analyses and the validity of the classifier. The mouse model data, while interesting, is presented as a correlative observation with unclear mechanistic links to the human genetics. The AlphaFold2-based classifier is a novel approach, but its development and validation are described in a way that leaves several methodological questions unanswered, particularly regarding the training set size and the generalizability of the decision rules.
- **Who would be interested in the results, and why** Clinical geneticists and molecular diagnosticians would be interested in the variant classification tool for interpreting KMT2A variants. Researchers studying KMT2A function, histone methylation, and the molecular basis of neurodevelopmental disorders would be interested in the domain-specific enrichment findings and the mouse model data. The broader community interested in applying AlphaFold2 to variant effect prediction would also find this study relevant.
- **Major Strengths**
    1.  The study addresses a clinically important question with a clear hypothesis-driven approach.
    2.  The use of a genetic enrichment strategy comparing disease variants to population controls is a sound and unbiased method to identify critical protein domains.
    3.  The integration of AlphaFold2 structure prediction with functional classification is a forward-looking and potentially impactful methodological contribution.
    4.  The authors are appropriately cautious in their interpretation of the mouse model data and acknowledge the limitations of their study.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence
    - **Claim pointer** The claim that WDSTS missense variants are 61.9-fold overrepresented in the CXXC domain and not enriched in the SET domain.
    - **Evidence pointer** Fig 1B, S1A–S1E Fig, location not provided.
    - **Concern** The core genetic finding is presented without the underlying data being visible. The number of variants in each domain, the total number of variants in each group, and the confidence intervals for the enrichment estimates are not provided in the text. The robustness of the finding to the inclusion of VUSs is mentioned but the data is not shown. The analysis using tumor somatic variants as a control is described but the results are not visible.
    - **Why it matters** The entire premise of the paper rests on this enrichment analysis. Without seeing the data, it is impossible to verify the magnitude of the effect, the statistical soundness of the analysis, or the validity of the conclusions drawn from it. The claim that the CXXC domain is the most important domain is a strong one that requires a high level of evidence.
    - **Resolution test** The authors must provide the full data for the enrichment analysis, including a table of variant counts per domain for each dataset, the calculated odds ratios with confidence intervals, and the raw p-values. The results of the sensitivity analyses (excluding VUSs, using tumor variants) must be shown in full.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Methodology
    - **Claim pointer** The claim that the AlphaFold2-based classifier achieves 92.6% positive and 92.9% negative predictive value on a hold-out test set.
    - **Evidence pointer** Fig 3D, S6B and S6C Fig, location not provided.
    - **Concern** The development and validation of the classifier is described, but the details are insufficient. The training set consists of only 14 variants, which is very small. The test set of 41 variants is also small, and the confidence intervals for the reported PPV and NPV are not given. The decision rules are derived from this small training set and prior knowledge, but the process of how these rules were finalized is not clear. The performance of the classifier is likely to be highly dependent on the specific variants in the training and test sets.
    - **Why it matters** The claim of high accuracy is a central part of the paper's contribution. If the classifier is not robustly validated, its utility for clinical or research purposes is questionable. The small sample sizes raise concerns about overfitting and the generalizability of the decision rules to unseen variants.
    - **Resolution test** The authors should provide a more detailed breakdown of the training and test sets, including the specific variants and their experimental annotations. They should report confidence intervals for the PPV and NPV. Ideally, they would use a more robust cross-validation strategy or an independent, larger validation cohort to demonstrate the classifier's performance.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Interpretation
    - **Claim pointer** The claim that the mouse model data corroborates the human genetic findings and suggests that the phenotype is not mediated via gene expression changes.
    - **Evidence pointer** Fig 2A–2D, S3A and S3B Fig, location not provided.
    - **Concern** The mouse model data is presented as a key piece of corroborating evidence. However, the text states that histone methylation disruption has "no systematic impact on gene expression." This is a negative result that is difficult to interpret. The link between the observed histone methylation changes at CpG-rich regions and the WDSTS phenotype is not established. The authors suggest alternative mechanisms, but these are speculative.
    - **Why it matters** The paper's narrative is that the CXXC domain is critical for WDSTS pathogenesis. The mouse data is used to support this by showing that loss of Kmt2a affects CpG-rich regions. However, the lack of a gene expression phenotype weakens the direct link between this molecular event and the organismal phenotype. The interpretation of this data is a key part of the paper's argument and needs to be more carefully developed.
    - **Resolution test** The authors should clarify the rationale for the mouse model experiment and how it directly tests the hypothesis derived from the human genetics. They should discuss the limitations of the negative gene expression result and provide a more concrete model for how the histone methylation changes could lead to the WDSTS phenotype, even in the absence of gene expression changes in the tested cell type and time point.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Methods, "Derivation of the variant effect classifier"
    - **Evidence pointer** Methods section, location not provided.
    - **Issue** The description of the decision rules is complex and difficult to follow. The logic of the cascades and the specific criteria for each classification (benign, compromised DNA binding, unfolding) could be presented more clearly, perhaps with a flowchart or a more structured list.
    - **Required correction** The authors should rewrite this section to be more accessible. A step-by-step description of the decision tree, with clear examples, would greatly improve the clarity and reproducibility of the method.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Results, "Preferential occurrence of missense variants..."
    - **Evidence pointer** Fig 1B, location not provided.
    - **Issue** The text mentions that the PHD fingers 1 and 4 also show significant enrichment. The functional significance of these domains in the context of WDSTS is not discussed in the results or the discussion.
    - **Required correction** A brief discussion of the potential role of these PHD fingers in KMT2A function and how their enrichment might relate to the CXXC domain findings would strengthen the paper.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Rigor
    - **Affected element** Results, "An AlphaFold2-based scheme..."
    - **Evidence pointer** Fig 3E, location not provided.
    - **Issue** The example in Fig 3E is described as showing two variants that "compromise DNA binding because they decrease the electrostatic potential." It is not clear how the electrostatic potential change is quantitatively linked to the functional outcome. Is there a threshold for the change in electrostatic potential that is considered damaging?
    - **Required correction** The authors should clarify the quantitative relationship between the change in electrostatic potential and the predicted functional effect. A more explicit description of the criteria used to define a "functionally important" change would be helpful.

- **Technical failings that need to be addressed before the case is established**
    1.  The primary genetic enrichment data (Fig 1) is not visible, preventing verification of the central claim.
    2.  The classifier's performance is based on a very small number of variants, and the confidence intervals for the reported metrics are not provided.
    3.  The link between the mouse model's molecular phenotype (histone methylation changes) and the lack of a gene expression phenotype is not adequately reconciled, leaving the mechanistic interpretation unclear.

## Risk / unsupported claims
- The claim of a 61.9-fold enrichment of WDSTS variants in the CXXC domain is unverifiable without the underlying data.
- The claim that the classifier is "accurate" is not fully supported due to the small validation set and lack of confidence intervals.
- The claim that the mouse model data "corroborates" the human genetic findings is an interpretation that is not fully supported by the presented text, especially given the negative gene expression result.
- The claim that the classifier's performance "enabled" the saturation mutagenesis is logical, but the biological validity of the saturation mutagenesis results is not assessed, as no experimental validation is presented.