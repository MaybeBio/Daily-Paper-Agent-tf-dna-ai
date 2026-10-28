## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplemental figure/table legends
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. Figures and supplemental data referenced but not fully visible.
- **Shared manuscript claim summary** The authors propose that Early Replication Control Elements (ERCEs) are compound elements composed of multiple subERCEs, defined by master transcription factor binding sites, which function both in transcriptional enhancement and in replication timing control through a transcription-independent mechanism. They further propose that subERCEs act by organizing chromatin domains structurally and creating a subnuclear environment favorable for early replication initiation, independent of specific origin sites.
- **Visible evidence base** Results sections describing allele-specific deletions in the Dppa2/4 domain, replication timing measurements via Repli-seq, transcription measurements via Bru-seq, and bioinformatic analyses of transcription factor binding sites. Statistical methods for comparing replication timing curves are described.
- **Missing materials affecting confidence** Actual figures and supplemental figures are not visible. Supplemental tables (1-5) with genotyping data, pairwise statistical comparisons, and Bru-seq quantification are referenced but not provided. Raw data and quality metrics for Repli-seq and Bru-seq experiments are not available. The referenced HiChIP and Micro-C data are described but not shown.

## Reviewer
- **Overall assessment** This manuscript presents a systematic and carefully executed dissection of replication timing control elements in the Dppa2/4 domain. The authors provide compelling evidence that master transcription factor binding sites constitute functional sub-elements within larger ERCEs, and that these subERCEs can maintain early replication even when transcription is largely eliminated. The work addresses an important gap in understanding how replication timing is regulated at the mechanistic level. However, several concerns regarding the interpretation of deletion phenotypes, the statistical framework, and the generalizability of the findings need to be addressed before the conclusions are fully established.

- **Who would be interested in the results, and why** Researchers studying DNA replication timing, chromatin architecture, transcriptional regulation, and developmental biology would find this work of significant interest. The study provides a refined model for how cis-regulatory elements control large-scale chromatin domain properties, which has implications for understanding cell fate transitions, epigenetic reprogramming, and potentially cancer biology where replication timing programs are often altered.

- **Major strengths** The use of allele-specific deletions in hybrid mouse cells provides an elegant internal control system. The systematic dissection of three ERCEs into smaller functional units is methodologically rigorous. The uncoupling of transcription from replication timing through selective TSS deletions is a conceptually important finding. The integration of multiple data types (Repli-seq, Bru-seq, HiChIP, Micro-C) strengthens the conclusions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and interpretation
- **Claim pointer** The authors claim that deletion of all three OSN sites within ERCE C (ΔCOSN123) fully accounts for the replication timing activity of the entire C element, and that OSN sites constitute the core of ERCE activity.
- **Evidence pointer** Results section "Cooperative Contributions of 3 OSN Sites Maintain Activity of ERCE C", Figure 1
- **Concern** The conclusion that OSN sites account for ERCE C activity is based on comparing ΔCOSN123 to the full C deletion (ΔC). However, the manuscript does not clearly demonstrate that the ΔCOSN123 deletion removes all functional elements within the C region. The C region may contain additional regulatory elements beyond the three identified OSN sites that contribute to replication timing. The statistical equivalence between ΔCOSN123 and ΔC is stated but the power of this equivalence test is not discussed. A failure to detect a significant difference does not establish equivalence.
- **Why it matters** The central claim of the paper is that OSN sites constitute the core of ERCE activity. If the ΔCOSN123 deletion does not fully recapitulate ΔC, then the conclusion that OSN sites fully account for ERCE C activity is overstated, and the subERCE model would need revision.
- **Resolution test** Provide a formal equivalence test with defined equivalence bounds, or demonstrate that the ΔCOSN123 deletion encompasses all active regulatory elements in the C region (e.g., by showing that additional deletions within C do not add to the phenotype). Alternatively, show that the residual difference between ΔCOSN123 and ΔC is not biologically meaningful.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The authors claim that their randomization-based statistical method can determine whether replication timing changes are significant, and they use this to compare deletion phenotypes.
- **Evidence pointer** Results section "Functional dissection of the Dppa2/4 replication domain using allele-specific deletions", Methods section "Statistical Analysis of RT changes", Supplemental Figure 2
- **Concern** The statistical method compares the area between two replication timing curves to a null distribution generated from random genomic regions. However, the manuscript does not describe how the null distribution accounts for the spatial autocorrelation of replication timing data, the variable quality of Repli-seq data across genomic regions, or the multiple testing burden when comparing many deletions. The method also appears to treat the two alleles as independent when they may be correlated. The choice of a 2 Mb window for the Dppa domain is not justified, and it is unclear how sensitive the results are to this window size.
- **Why it matters** The statistical framework is the foundation for all conclusions about which deletions significantly affect replication timing. If the method is not properly calibrated, the classification of deletions as "significant" or "non-significant" could be incorrect, affecting the interpretation of which elements are functionally important.
- **Resolution test** Provide a detailed description of the null model, including how spatial autocorrelation is handled. Show calibration analyses using known positive and negative control regions. Report the false discovery rate or provide adjusted p-values for multiple comparisons. Justify the choice of window size and demonstrate robustness to this choice.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of causal relationships
- **Claim pointer** The authors claim that subERCEs function through a transcription-independent mechanism to maintain early replication, based on the observation that deleting all three TSSs eliminates most transcription but replication remains early.
- **Evidence pointer** Results section "Early RT is independent of where replication initiates", Figure 4
- **Concern** The conclusion that replication timing is maintained independently of transcription relies on the assumption that the TSS deletions do not affect other regulatory elements. However, TSS deletions may remove promoter-associated chromatin features, non-coding RNAs, or other functional elements that could influence replication timing through mechanisms other than transcription. Additionally, the residual transcription detected in the triple TSS deletion (described as "large reductions" but not complete elimination) may be sufficient to support early replication. The manuscript does not address whether the residual transcription level is above a threshold required for replication timing effects.
- **Why it matters** The claim of transcription-independent replication timing control is a key conceptual advance of the paper. If the residual transcription or other TSS-associated functions contribute to the observed replication timing, the interpretation would need to be revised.
- **Resolution test** Provide quantitative analysis of residual transcription levels in the triple TSS deletion and test whether these levels are below a threshold known to affect replication timing. Alternatively, use a system where transcription can be acutely inhibited without deleting TSSs to test whether replication timing is maintained.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The authors propose a general model in which subERCEs, defined by master transcription factor binding sites, constitute the core of early replication control elements across the genome.
- **Evidence pointer** Discussion section "ERCEs consist of multiple smaller subERCEs"
- **Concern** The study is limited to a single genomic locus (the Dppa2/4 domain). While the authors previously identified ERCEs in multiple domains, the current fine-mapping analysis is only performed in this one domain. The claim that subERCEs are general features of ERCEs across the genome is not directly tested. The authors note that the number of elements in their study is too small to identify a unique transcription factor signature, which limits the generalizability of the subERCE concept.
- **Why it matters** The broader significance of the work depends on whether the subERCE model applies to other replication timing control elements. Without evidence from additional loci, the model remains a hypothesis specific to the Dppa domain.
- **Resolution test** Apply the same fine-mapping approach to at least one additional ERC-containing domain. Alternatively, use bioinformatic approaches to test whether master transcription factor binding sites are enriched at ERCEs genome-wide and whether this enrichment predicts replication timing activity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic model
- **Claim pointer** The authors propose that subERCEs create a subnuclear microenvironment, potentially through phase separation, that promotes initiation of replication within the structurally organized replication domain.
- **Evidence pointer** Discussion section "ERCEs and replication origins", Figure 6
- **Concern** The proposed mechanism of subnuclear microenvironment formation through phase separation is highly speculative and not directly tested in this manuscript. While the authors cite supporting data from HiChIP and Micro-C showing interactions between subERCEs, these data are not shown or analyzed in the current manuscript. The connection between transcription factor binding, chromatin interactions, and replication timing control remains correlative.
- **Why it matters** The mechanistic model is a major part of the discussion and frames the significance of the findings. If the model is not supported by direct evidence, it should be presented more cautiously as a hypothesis rather than a conclusion.
- **Resolution test** Provide the HiChIP and Micro-C data analysis showing subERCE interactions. Test whether disrupting these interactions (e.g., by deleting individual subERCEs) affects replication timing. If phase separation is proposed, provide evidence for liquid-liquid phase separation properties of subERCE-associated factors.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Introduction of the term "subERCEs"
- **Evidence pointer** Results section "Cooperative Contributions of 3 OSN Sites Maintain Activity of ERCE C"
- **Issue** The term "subERCEs" is introduced somewhat abruptly in the results section. The authors state that OSN sites are designated as subERCEs, but the criteria for this designation are not clearly defined. It is unclear whether any OSN site within an ERC qualifies as a subERCE, or whether additional functional criteria are required.
- **Required correction** Provide a clear operational definition of subERCEs, including the criteria used to identify them (e.g., functional contribution to replication timing, transcription factor binding, chromatin interactions). Clarify the relationship between OSN sites, subERCEs, and ERCEs.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5 and replication origin analysis
- **Evidence pointer** Results section "Early RT is independent of where replication initiates"
- **Issue** The comparison of replication origin datasets is presented descriptively, but the quantitative analysis is not shown. The statement that "none of the SNS-seq datasets detected peaks within 10kb of any of the subERCEs" is important but the distance calculation and the significance of this observation are not discussed.
- **Required correction** Provide a quantitative analysis of the distance between subERCEs and replication origins. Discuss whether the absence of origins near subERCEs is expected under the proposed model or whether it presents a challenge.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Comparison of deletion phenotypes
- **Evidence pointer** Results sections describing ΔCOSN12 and ΔCOSN123 phenotypes, Supplemental Table 4
- **Issue** The manuscript states that ΔCOSN12 significantly delayed replication timing while ΔCOSN123 gave an effect similar to ΔC. However, the difference between ΔCOSN12 and ΔCOSN123 is not explicitly tested. The claim that "some OSNs play larger roles than others" would be strengthened by a direct statistical comparison.
- **Required correction** Report the statistical comparison between ΔCOSN12 and ΔCOSN123 phenotypes, and discuss the implications for the relative contributions of individual OSN sites.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Repli-seq and Bru-seq quality metrics
- **Evidence pointer** Methods section "Repli-seq Library Preparation and Data Analysis" and "Bru-seq Library Preparation and Data Analysis"
- **Issue** The methods describe the sequencing depth requested (30 million reads for Repli-seq, 100 million for Bru-seq) but do not report the actual number of reads obtained, mapping rates, or other quality metrics for each experiment.
- **Required correction** Provide quality metrics for all sequencing experiments, including read counts, mapping rates, and any quality filtering steps. This is important for assessing the reliability of the quantitative comparisons.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of transcription and replication timing relationship
- **Evidence pointer** Discussion section "ERCEs and transcription"
- **Issue** The discussion of the relationship between transcription and replication timing would benefit from more explicit engagement with prior work showing correlations between these processes, and with studies that have attempted to uncouple them. The authors cite some relevant literature but do not clearly position their findings relative to previous attempts to dissect this relationship.
- **Required correction** Expand the discussion to more explicitly address how the current findings advance understanding beyond previous correlative studies, and what specific predictions the model makes that could be tested in future work.

## Risk / unsupported claims
- The claim that OSN sites fully account for ERCE C activity is not fully supported without a formal equivalence test or demonstration that all functional elements in C have been identified.
- The claim of transcription-independent replication timing control is weakened by the presence of residual transcription in the triple TSS deletion and the lack of direct evidence that residual transcription is below a functionally relevant threshold.
- The proposed phase separation mechanism is speculative and not directly tested in this manuscript.
- The generalizability of the subERCE model to other genomic loci is not established, as the fine-mapping analysis is performed in only one domain.
- The statistical framework for comparing replication timing curves is not fully validated, and the manuscript does not report multiple testing corrections or demonstrate robustness to analysis parameters.
- The HiChIP and Micro-C data referenced in the discussion are not shown or analyzed in the current manuscript, limiting the ability to evaluate the claims about subERCE interactions.