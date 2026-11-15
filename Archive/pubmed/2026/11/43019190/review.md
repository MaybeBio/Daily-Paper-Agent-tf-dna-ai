## Review setup
- **Input scope** Full manuscript text (title, abstract, introduction, methods, results, discussion, conclusion, supplementary information description)
- **Assessment boundary** Scientific soundness, methodological rigor, internal consistency, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors report an integrative in silico analysis of 10 SP110 single nucleotide polymorphisms previously associated with pulmonary tuberculosis, evaluating their potential effects on transcription factor binding, pre-mRNA splicing, protein function, and mRNA secondary structure. They conclude that these variants predominantly exert regulatory effects through transcription factor binding alterations and RNA structural changes rather than through splicing disruption or protein destabilization.
- **Visible evidence base** Methods descriptions, Table 1 (variant list), Table 2 (splicing and protein predictions), Supplementary Table S1 (referenced), Supplementary Figure 1 (referenced), Supplementary data S3 (referenced)
- **Missing materials affecting confidence** Supplementary Table S1, Supplementary Figure 1, Supplementary data S3, full SNP2TFBS output tables, AlphaGenome output details, RNAfold raw output values, and any code or configuration files

## Reviewer

- **Overall assessment** This manuscript presents a purely computational analysis of 10 SP110 variants using established in silico tools. The study is clearly described and the authors are appropriately cautious in framing their findings as predictive. However, the manuscript has several substantive issues that limit its current suitability for publication. The variant selection criteria are described inconsistently, the results section omits key quantitative data that would allow readers to evaluate the claims, and the discussion overinterprets computational predictions in several places. The novelty is modest given that in silico prediction of variant effects is a well-established approach, and the manuscript does not provide a compelling biological advance beyond what individual tools would already report. The writing is generally clear but contains some redundancy and occasional overstatement.

- **Who would be interested in the results, and why** Researchers studying the genetic architecture of tuberculosis susceptibility, particularly those focused on SP110 as a candidate gene, may find this analysis useful as a variant prioritization resource. Computational biologists working on regulatory variant prediction may also be interested in the multi-tool integration approach. However, the audience is relatively narrow, and the lack of experimental validation limits the broader appeal to immunologists or clinicians.

- **Major Strengths**
  1. The authors apply multiple complementary prediction tools (SNP2TFBS, SpliceAI, Pangolin, REVEL, AlphaMissense, PolyPhen-2, SIFT, PrimateAI-3D, AlphaGenome, RNAfold) and integrate their outputs, which is methodologically thorough.
  2. The manuscript is honest about the limitations of in silico prediction and repeatedly cautions against overinterpretation.
  3. The variant set is well contextualized with respect to prior association studies and African population relevance.
  4. The inclusion of AlphaGenome, a recently released model, adds a contemporary dimension to the analysis.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and data availability
- **Claim pointer** The authors claim to have performed an "integrative in silico analysis" and report specific quantitative results (e.g., ScoreDiff values, splice delta scores, quantile scores, MFE differences).
- **Evidence pointer** Results sections; Table 2; Supplementary Table S1; Supplementary Figure 1; Supplementary data S3
- **Concern** The results section reports only a small subset of the data generated. For example, only four of ten SNPs returned SNP2TFBS predictions, but the full output for all ten variants is not shown. AlphaGenome quantile scores are reported for only a few variants and tracks, with no comprehensive table. RNAfold results are summarized only as |ΔMFE| and |ΔCentroid| ranges, with individual values relegated to supplementary material that was not provided for review. Without full output tables, readers cannot independently verify the claims or assess the completeness of the analysis.
- **Why it matters** Reproducibility is a core requirement for computational studies. The manuscript cannot be properly evaluated without access to the complete prediction outputs for all variants across all tools. Selective reporting of favorable results introduces potential bias and prevents readers from assessing the overall pattern of predictions.
- **Resolution test** Provide complete output tables for all tools across all 10 variants as supplementary data files, including raw scores, thresholds applied, and any filtering steps. These should be made available for review.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency of variant selection criteria
- **Claim pointer** The authors state variants were selected based on "prior association with PTB and minor allele frequency > 1% in African populations, together with specific biological and epidemiological relevance to a Ugandan cohort with PTB." The introduction states the selection was based on "prior PTB association and minor allele frequency > 1% in African populations, and with specific epidemiological relevance to a Ugandan cohort affected by pulmonary tuberculosis."
- **Evidence pointer** Introduction; Materials and methods, Study design
- **Concern** The manuscript repeatedly references a "Ugandan cohort" and "epidemiological relevance to a Ugandan cohort," but the methods also state that "Reference to a Ugandan pulmonary tuberculosis context reflects the epidemiological framework guiding variant prioritization rather than a directly sampled cohort." This is contradictory. If no Ugandan cohort data were used, the repeated emphasis on Ugandan relevance is misleading. If cohort data were used, the methods must describe how these data informed variant selection. The current text is ambiguous and could mislead readers about the empirical basis of the study.
- **Why it matters** The scientific integrity of the study depends on transparent reporting of how variants were selected. The ambiguity between "cohort relevance" and "epidemiological framework" obscures whether the authors had access to Ugandan patient data or not. This affects the interpretation of the study's claims about pulmonary tuberculosis relevance.
- **Resolution test** Clarify in the methods whether any Ugandan cohort data were used in variant selection. If not, remove all references to a "Ugandan cohort" and instead state that variants were selected based on published association studies and African population allele frequencies. If yes, describe the cohort, sample size, and how data were accessed and analyzed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Overinterpretation of computational predictions
- **Claim pointer** The discussion states: "The dominance of CTCF as the top transcription factor hit further suggests that this region of SP110 harbors one or more architectural CTCF binding sites, disruption of which could plausibly influence chromatin looping or insulator function relevant to immune gene regulation in the context of pulmonary tuberculosis susceptibility."
- **Evidence pointer** Discussion, Implications of allele-specific modulation section
- **Concern** This statement extrapolates from AlphaGenome predictions of CTCF binding disruption to claims about chromatin looping and insulator function. AlphaGenome is a sequence-based prediction model, not a chromatin conformation assay. The authors themselves acknowledge this limitation in the same paragraph, but the speculative language ("could plausibly influence") is still presented as a substantive finding. Similar overreach appears in the discussion of rs7580900, where the authors suggest the variant "may redirect SP110 regulation toward alternative transcriptional programs" based solely on predicted binding changes for TP63 and Zfx.
- **Why it matters** The discussion should distinguish clearly between what the computational tools predict and what biological consequences might follow. Overinterpretation of in silico results can mislead readers who are not familiar with the limitations of these prediction tools and can contribute to the broader problem of unvalidated computational claims in the genetics literature.
- **Resolution test** Revise the discussion to explicitly separate predictions from biological hypotheses. For each predicted effect, state clearly that the biological consequence is speculative and requires experimental validation. Remove or substantially soften claims about chromatin looping, insulator function, and redirected transcriptional programs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Incomplete reporting of AlphaGenome methodology
- **Claim pointer** The authors state: "We assessed the predicted regulatory effects of the 10 SP110 variants using AlphaGenome (Google DeepMind), a unified DNA sequence model that predicts genome-wide functional tracks from 1 Mb input sequences at single-base resolution."
- **Evidence pointer** Materials and methods, Cross-modality regulatory effect prediction
- **Concern** The description of the AlphaGenome analysis is insufficiently detailed. The authors do not specify which model version was used, how input sequences were constructed, what reference genome build was used for the input sequences, how the "quantile score" was computed, what the "CenterMaskScorer" does in detail, or how the 13 variants (mentioned in the results as "13 variants" for CTCF analysis) relate to the 10 SNPs listed in Table 1. The discrepancy between 10 SNPs and 13 variants is not explained.
- **Why it matters** AlphaGenome is a complex model, and the results cannot be reproduced or properly interpreted without detailed methodological reporting. The 10 versus 13 variant discrepancy raises questions about whether additional variants were analyzed or whether the text contains an error.
- **Resolution test** Provide a detailed description of the AlphaGenome analysis, including model version, input construction, scoring methodology, and the relationship between the 10 SNPs and the 13 variants mentioned in the results. Clarify the quantile score computation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical and comparative analysis lacking
- **Claim pointer** The authors report various prediction scores and classify variants as having "minimal" or "moderate" effects without any statistical framework or comparison to a null distribution.
- **Evidence pointer** Results sections throughout
- **Concern** The manuscript reports raw prediction scores and qualitative classifications (e.g., "low splice-altering effects," "minimal effects on MFE") without any statistical analysis. There is no comparison to a set of control or neutral variants, no confidence intervals, and no assessment of whether the observed effects are significantly different from what would be expected by chance. The classification of variants as having "minimal" or "moderate" effects appears to be based on arbitrary thresholds.
- **Why it matters** Without a statistical framework or comparison to neutral variants, the reader cannot assess whether the reported effects are meaningful or within the range of what would be expected for any random variant in the genome. This weakens the conclusions about which variants are functionally relevant.
- **Resolution test** Include a comparative analysis with a set of matched neutral or control variants, and apply appropriate statistical tests to determine whether the observed prediction scores for the 10 SP110 variants differ significantly from the control set.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and precision
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table contains formatting errors. The "Source" column appears to have merged entries, and the variant consequence column contains multiple entries for some rows (e.g., "Missense" and "AG" appear on the same line for rs11556887). The table is difficult to read and contains what appear to be typographical errors.
- **Required correction** Reformat Table 1 to ensure each row contains a single variant with clear, separate columns for each attribute. Verify that all entries are correct and properly aligned.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results, In silico analysis of SP110 variants on splicing and protein function
- **Evidence pointer** Results section; Table 2
- **Issue** The text states "Three missense variants (rs11556887, rs3948464, and rs9061) and one stop-gained allele of rs3948464 were evaluated" but Table 2 lists rs3948464 with three alternate alleles (A>C, A>G, A>T). The text should clarify that rs3948464 has multiple alternate alleles, each analyzed separately.
- **Required correction** Revise the text to accurately describe the number of variants and alleles analyzed, and ensure consistency between the text and Table 2.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Materials and methods, Cross-modality regulatory effect prediction
- **Evidence pointer** Materials and methods section
- **Issue** The description of AlphaGenome and the CenterMaskScorer is written at a level that assumes familiarity with the tool. Nonspecialist readers will not understand what "CenterMaskScorer" does or how "quantile scores" are derived.
- **Required correction** Provide a brief plain-language explanation of what AlphaGenome predicts, what the CenterMaskScorer computes, and how quantile scores should be interpreted.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** Materials and methods, Computing infrastructure
- **Evidence pointer** Materials and methods section
- **Issue** The authors report using "Google Chrome version 147.0.7727.56" and "macOS Tahoe version 26.4.1" in the computing infrastructure section. These details are irrelevant to the scientific content and suggest the authors may have included system information that does not belong in a scientific methods section. Additionally, "macOS Tahoe" is not a recognized macOS version name.
- **Required correction** Remove irrelevant browser and operating system details. If software versions are important for reproducibility, report the versions of the actual analysis tools used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Referencing and support
- **Affected element** Discussion, Implications of RNA secondary structure alterations
- **Evidence pointer** Discussion section
- **Issue** The discussion of RNA secondary structure alterations cites reference 52 and 53 in a general way but does not provide specific context for how these references support the claim that "disease-associated and regulatory SNPs frequently preserve overall RNA stability while reshaping structural conformational landscapes." The connection between the cited literature and the specific claim is not clear.
- **Required correction** Provide more specific context for how the cited references support the stated claim, or revise the claim to more accurately reflect what the cited literature demonstrates.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language and style
- **Affected element** Throughout
- **Evidence pointer** Entire manuscript
- **Issue** The manuscript contains several instances of informal or imprecise language. For example, "we set out to conduct" in the introduction is unnecessarily informal, and the phrase "as these findings derive from sequence-based computational predictions rather than direct chromatin measurements, they should be regarded as variant-prioritization evidence" is wordy and could be more concise.
- **Required correction** Revise for formal scientific tone and conciseness throughout.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Ethical reporting
- **Affected element** Acknowledgements
- **Evidence pointer** Acknowledgements section
- **Issue** The acknowledgement states that "Dr. Jeff Britton Ssemuddu" contributed to "professional writing and organisation of the manuscript." If this individual provided substantial writing assistance, it may be appropriate to consider whether this constitutes authorship per standard guidelines. The current acknowledgement is vague about the nature and extent of the contribution.
- **Required correction** Clarify the nature of Dr. Ssemuddu's contribution and consider whether this individual meets authorship criteria. If not, ensure the acknowledgement accurately describes the level of contribution.

## Risk / unsupported claims
- The claim that "the analyzed variants showed uniformly low splicing disruption signals and consistently benign protein pathogenicity classifications" is only partially supported by the data shown. Table 2 shows results for only 4 alleles (3 missense and 1 stop-gained), while the remaining 6 SNPs are intronic and were not assessed for protein effects. The claim of "uniformly low" splicing signals is based on data not fully presented.
- The claim that "SP110 variants predominantly influence gene regulation rather than splicing or protein function" is an interpretation based on negative results from prediction tools. The absence of predicted splicing or protein effects does not establish that regulation is the predominant mechanism, particularly without experimental validation.
- The statement that "the data supports a model in which SP110 SNPs influence gene function primarily through regulatory fine-tuning rather than structural perturbation" is not directly supported by the data presented. The data show predictions of transcription factor binding changes for only 4 of 10 SNPs, and the biological consequences of these predicted changes are not established.
- The claim that "the position chr2:230185999 (rs3948464) demonstrated the most consistently disruptive site in the dataset" is based on AlphaGenome predictions that are not fully described or validated.
- The discussion of RNA secondary structure alterations as a "post-transcriptional regulatory mechanism" is speculative. The authors report ΔMFE and ΔCentroid values but do not establish that these predicted structural changes have any functional consequence.
- The statement that "future studies should experimentally validate the predicted regulatory effects" is appropriate, but the manuscript does not adequately acknowledge that without such validation, the current findings remain entirely predictive and their biological relevance is unestablished.

## Assessment against Nature-style criteria
- **Originality** Limited. The application of existing in silico prediction tools to a set of previously identified SP110 variants is a straightforward use of established methods. The integration of multiple tools is mildly novel but does not represent a conceptual advance. The manuscript does not introduce new methods, new biological insights, or a new framework for analysis.
- **Scientific importance** Moderate. SP110 is a candidate gene for tuberculosis susceptibility, and understanding the functional consequences of associated variants is of interest to the tuberculosis genetics community. However, the purely computational nature of the study and the lack of experimental validation limit the importance of the findings. The study does not resolve any existing controversy or provide definitive evidence about the functional mechanisms of SP110 variants.
- **Interdisciplinary readership** Limited. The manuscript will primarily appeal to researchers working on tuberculosis genetics and computational prediction of regulatory variants. The findings are unlikely to attract interest from immunologists, clinicians, or researchers in other fields, as the study does not provide experimentally validated biological insights.
- **Technical soundness** The methods are generally appropriate for the stated aims, and the authors apply widely used tools with established performance. However, the incomplete reporting of results, the lack of statistical analysis, and the unexplained discrepancy between 10 SNPs and 13 variants in the AlphaGenome analysis raise concerns about technical rigor. The manuscript would benefit from more complete data reporting and a more rigorous comparative framework.
- **Readability for nonspecialists** The manuscript is generally readable, with clear section structure and appropriate use of technical terms. However, the methods section assumes familiarity with the specific prediction tools used, and the discussion contains some speculative language that may be difficult for nonspecialists to evaluate critically. The manuscript would benefit from clearer explanations of what each tool does and what the scores mean.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents a computational analysis that is methodologically reasonable but has several substantive issues that must be addressed before the case is established. The incomplete reporting of results, the ambiguity regarding the Ugandan cohort, the lack of statistical analysis, and the overinterpretation of computational predictions in the discussion all need to be resolved. The authors should provide complete data outputs, clarify their variant selection criteria, temper their interpretive claims, and more clearly distinguish predictions from established findings. If these concerns are addressed, the manuscript could be suitable for publication as a variant prioritization study, but in its current form, the evidence does not support the strength of the conclusions presented.