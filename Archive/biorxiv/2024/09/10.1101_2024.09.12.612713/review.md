## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, funding, and supplementary table descriptions
- **Assessment boundary** Scientific validity of the claims as presented in the provided manuscript text; no assessment of supplementary data files or figures beyond what is described in the text
- **Shared manuscript claim summary** The authors propose that coupling human exome/genome sequencing with G0 CRISPR/Cas9 knockout screening in zebrafish and protein binding microarrays can functionally prioritize candidate genes and variants for ocular congenital cranial dysinnervation disorders (oCCDDs). They report three novel candidate genes (SEMA3F, OLIG2, FRMD4B) and functional evidence for three transcription factor variants (PHOX2A p.(Trp137Cys), MAFB p.(Glu223Lys), OLIG2 p.(Arg156Leu)).
- **Visible evidence base** Abstract, Introduction, Methods (abbreviated), Results, Discussion, Funding, Commercial Relationships Disclosure, Supplementary table descriptions
- **Missing materials affecting confidence** Supplementary Methods, Supplementary Tables 1-5, all figures (Fig. 1-8), Supplementary Figures 1-4, detailed statistical analyses, raw sequencing data, PBM data files

## Reviewer

- **Overall assessment** This manuscript addresses a significant challenge in Mendelian disease gene discovery, namely the functional prioritization of candidate genes and variants identified through human sequencing. The authors combine three complementary approaches: human sequencing, zebrafish G0 knockout screening, and protein binding microarrays. The pilot validation using known oCCDD genes (phox2a and mafba) is a sensible design. However, the evidence presented in the text is insufficient to fully establish the three novel candidate genes as bona fide oCCDD genes, and several claims regarding variant pathogenicity require additional supporting data. The manuscript is well-structured and the writing is clear, but the current evidence base, as presented, does not fully support the strength of the conclusions.
- **Who would be interested in the results, and why** Researchers in Mendelian disease gene discovery, particularly those studying neurodevelopmental disorders affecting cranial nerve development. The G0 CRISPR screening approach may interest zebrafish geneticists and those developing high-throughput functional genomics pipelines. Clinicians and geneticists involved in diagnosing oCCDDs would find the candidate gene nominations relevant. The PBM methodology for variant interpretation may interest molecular pathologists and those working on variant classification frameworks.
- **Major strengths** The study addresses a real bottleneck in genomic medicine, namely the functional validation of candidate variants. The use of G0 CRISPR screening to accelerate zebrafish phenotyping is methodologically innovative and could have broad applicability. The combination of gene-level (zebrafish) and variant-level (PBM) functional assays is a thoughtful two-tier approach. The pilot validation using known genes provides a useful positive control. The authors acknowledge limitations honestly, including the possibility of missed phenotypes and the need for additional human alleles.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for novel gene claims
- **Claim pointer** The manuscript states that SEMA3F, OLIG2, and FRMD4B are "strong novel candidate oCCDD genes" based on the zebrafish screening and human sequencing data.
- **Evidence pointer** Results section, Figures 4-6, Supplementary Tables 1, 4, 5
- **Concern** The claim that these three genes are "strong" candidates rests on the observation of cranial motor neuron phenotypes in G0 and F2 zebrafish mutants, plus the presence of rare human variants in single pedigrees. However, the text does not provide details on the statistical significance of the human variant burden, the number of pedigrees per gene, the segregation patterns, or whether any of these genes reached genome-wide significance in the human sequencing analysis. For OLIG2, the variant was found in a single pedigree with incomplete penetrance, and for FRMD4B, the specific variant was not functionally tested. The zebrafish phenotypes, while consistent with oCCDD-like defects, are not described in sufficient detail to assess their specificity or severity.
- **Why it matters** The term "strong candidate gene" implies a high probability of true disease association. Without evidence of statistical enrichment in the human cohort, replication in independent pedigrees, or functional data directly linking the human variant to the phenotype, the strength of this claim is not justified. Overstating candidate gene status can lead to premature clinical interpretation.
- **Resolution test** Provide quantitative human genetic evidence (e.g., variant burden analysis, number of independent pedigrees, segregation LOD scores) and detailed phenotypic characterization of the zebrafish mutants, including penetrance and expressivity data. For FRMD4B, functional testing of the specific human variant is needed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Variant pathogenicity interpretation
- **Claim pointer** The manuscript concludes that the PBM data "support the functionality and putative pathogenicity" of PHOX2A p.(Trp137Cys), MAFB p.(Glu223Lys), and OLIG2 p.(Arg156Leu).
- **Evidence pointer** Results section, Figure 7
- **Concern** The PBM experiments demonstrate reduced or abolished DNA binding for the three variants. However, the text does not provide quantitative thresholds for what constitutes a "significant" reduction, nor does it compare the variant effects to known benign or pathogenic controls beyond the wild-type. The authors themselves note that "more data will be needed over time, including testing additional pathogenic and benign variants once their clinical impact has been established." This admission undermines the strength of the pathogenicity claim. For MAFB p.(Glu223Lys), the partial loss of binding is described, but the functional significance of this partial reduction is unclear.
- **Why it matters** Variant classification requires calibrated evidence. Without established thresholds or control variants, the PBM data cannot be used to assign pathogenicity. The claim of "putative pathogenicity" is too strong given the acknowledged lack of validation.
- **Resolution test** Provide a clear statistical framework for interpreting PBM E-score differences, include known pathogenic and benign variants as controls, and temper the pathogenicity claim to "functional effect demonstrated" rather than "putative pathogenicity."

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of G0 screening approach
- **Claim pointer** The authors state that their findings "support that G0 loss-of-function screening in zebrafish can be coupled with human sequence analysis and protein binding microarrays to aid in prioritizing oCCDD candidate genes/variants."
- **Evidence pointer** Results section, Figures 2-3, Discussion
- **Concern** The pilot validation with phox2a and mafba shows that G0 screening can recapitulate known phenotypes in 70-90% of injected fish. However, the manuscript does not report the false positive or false negative rates for the broader screen of 55 genes. The text notes that "we cannot definitively exclude candidates that screened negative," which is appropriate, but the positive predictive value of the screen is unclear. The authors also note that phenotypes were screened at 72 hpf, potentially missing later-onset phenotypes.
- **Why it matters** The utility of the G0 screening approach depends on its sensitivity and specificity. Without a systematic assessment of screen performance, the recommendation to adopt this approach is not fully supported.
- **Resolution test** Report the number of genes that screened positive in the initial pilot, the rate of confirmation in F2 mutants, and any known false negatives. Provide a more detailed assessment of the screen's limitations and potential improvements.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Phenotypic specificity in zebrafish
- **Claim pointer** The manuscript describes cranial motor neuron phenotypes in zebrafish mutants for sema3fa, olig2, and frmd4bb, and implies these are relevant to human oCCDDs.
- **Evidence pointer** Results section, Figures 4-6, Supplementary Table 5
- **Concern** The text does not provide sufficient detail on the nature of the zebrafish phenotypes. For example, are the CN3/CN6 defects specific to motor neurons, or could they reflect broader developmental abnormalities? The authors note that sema3fa mutants had CN3 axonal defasciculation but CN4 was grossly intact, which differs from the mouse model. The relevance of these phenotypes to human oCCDDs, which are defined by specific patterns of innervation defects, is not fully established.
- **Why it matters** The interpretation of zebrafish phenotypes as models of human disease requires careful consideration of species differences and phenotypic specificity. Overinterpretation could lead to incorrect gene prioritization.
- **Resolution test** Provide more detailed phenotypic characterization, including assessment of other cranial nerves and non-motor neuron cell types, and discuss the implications of species differences for the interpretation of the zebrafish phenotypes.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** G0 screening protocol
- **Evidence pointer** Methods section
- **Issue** The methods section is abbreviated and refers to Supplementary Methods for details. The text does not specify the number of embryos injected per gene, the criteria for classifying a phenotype as "positive," or the statistical methods used to compare phenotype frequencies between treatment and control groups.
- **Required correction** Provide these details in the main text or ensure they are clearly described in the Supplementary Methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Zebrafish phenotype quantification
- **Evidence pointer** Results section, Figures 2-6
- **Issue** The text reports percentages of fish with phenotypes (e.g., 70-90% for phox2a and mafba) but does not report confidence intervals or statistical tests comparing treatment and control groups.
- **Required correction** Include statistical comparisons and effect size estimates for the key phenotype assessments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Variant interpretation framework
- **Affected element** PBM data interpretation
- **Evidence pointer** Results section, Figure 7
- **Issue** The text describes E-score distributions but does not provide a clear framework for what constitutes a "significant" reduction in binding. The comparison to negative controls is mentioned but not quantified.
- **Required correction** Define a threshold for significant binding reduction and report the number of replicates and variability for each PBM experiment.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Human phenotype detail
- **Affected element** Clinical descriptions
- **Evidence pointer** Results section, Table 1, Figure 8
- **Issue** The clinical descriptions of the human pedigrees are brief. For example, the PHOX2A variant is described as causing "characteristic" MRI findings, but the specific features are not enumerated in the text.
- **Required correction** Provide more detailed clinical and radiological descriptions, or refer clearly to the supplementary tables where these are provided.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of SEMA3F, OLIG2, and FRMD4B as candidate genes would benefit from a more thorough comparison with existing literature on these genes in other developmental contexts.
- **Required correction** Add a brief review of what is known about these genes in relevant developmental pathways.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Strong candidate gene"
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "strong" is used repeatedly to describe candidate genes, but the criteria for this designation are not defined.
- **Required correction** Define the criteria for "strong candidate gene" or use more measured language.

## Risk / unsupported claims

- The designation of SEMA3F, OLIG2, and FRMD4B as "strong novel candidate oCCDD genes" is not fully supported by the evidence presented in the text, as the human genetic evidence is limited to single pedigrees and the zebrafish phenotypes are not described in sufficient detail.
- The claim that the PBM data support "putative pathogenicity" of the three transcription factor variants is not fully supported, as the authors acknowledge the lack of calibrated thresholds and control variants.
- The generalizability of the G0 screening approach is not fully established, as the manuscript does not report false positive/negative rates or a systematic assessment of screen performance.
- The relevance of the zebrafish phenotypes to human oCCDDs is not fully established, given the noted species differences and the lack of detailed phenotypic characterization.
- The statement that "this is the first reported PHOX2A-CFEOM candidate missense allele that localizes to the DNA binding domain and is demonstrated to abolish transcription factor-DNA binding" is a strong claim that requires careful verification of the literature and the experimental evidence.
- The manuscript does not provide evidence that the human variants in SEMA3F, OLIG2, and FRMD4B are absent from large population databases beyond a general statement, which is insufficient to establish rarity.

## Assessment against Nature-style criteria

- **Originality** The combination of G0 CRISPR screening with PBM analysis for oCCDD gene prioritization is a novel methodological contribution. The application of PBM to variant interpretation in this context is not widely used and adds originality.
- **Scientific importance** The work addresses a significant problem in Mendelian genetics, namely the functional validation of candidate genes and variants. If the approach is robust, it could be applied to other disorders. However, the importance is somewhat limited by the small number of genes validated and the lack of definitive human genetic evidence.
- **Interdisciplinary readership** The work bridges human genetics, zebrafish developmental biology, and molecular biology. It would appeal to a broad readership in these fields, but the clinical relevance is limited by the rarity of the disorders and the preliminary nature of the candidate gene claims.
- **Technical soundness** The technical approach is generally sound, but the manuscript lacks key details on statistical methods, thresholds, and controls. The PBM experiments are described without a clear framework for interpretation, and the zebrafish screening is described without a systematic assessment of its performance.
- **Readability for nonspecialists** The manuscript is clearly written and the logic is easy to follow. The figures, as described, would likely aid comprehension. However, the abbreviated methods section may hinder readers who are not familiar with the techniques.

## Recommendation posture

Currently not established from the provided evidence. The manuscript presents a promising methodological framework and some intriguing candidate genes, but the strength of the claims exceeds the evidence provided. The human genetic evidence is limited to single pedigrees, the zebrafish phenotypes are not described in sufficient detail, and the PBM data lack a calibrated interpretation framework. The manuscript would be suitable for reconsideration after major revisions that address these concerns, particularly the need for quantitative human genetic evidence, detailed phenotypic characterization, and a more cautious interpretation of variant pathogenicity.