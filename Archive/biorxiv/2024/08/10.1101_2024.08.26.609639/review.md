## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, figure legends, and supplementary legends. No figures or supplementary data files were provided for direct inspection.
- **Assessment boundary** The assessment is limited to the scientific content, methodological soundness, and logical coherence of the text as provided. Claims are evaluated against the evidence described in the manuscript, not against external literature or unpublished data.
- **Shared manuscript claim summary** The authors introduce a native holdup (nHU) assay adapted for DNA-protein interactions, validate it using the ATP2B4 erythroid promoter, and use it to quantify the DNA-binding affinities of full-length GATA1 and six disease-associated mutants. They report that GATA1s (short isoform) binds DNA with increased affinity and shows increased transcriptional activity, while R307C shows reduced DNA binding and reduced activity. Other mutants (V205M, R216W, D218Y) show reduced transcriptional activity without detectable changes in DNA binding.
- **Visible evidence base** The manuscript text includes descriptions of luciferase reporter assays, nHU-MS experiments, nHU titration experiments with Western blot detection, immunostaining and colocalization analysis, and references to supplementary figures and data files. The actual figures, supplementary figures, and supplementary data files were not available for review.
- **Missing materials affecting confidence** Figures 1-7, Supplementary Figures S1-S7, and Supplementary Data 1-4 were not provided. These contain the primary quantitative data, Western blot images, binding curves, statistical analyses, and proteomics results that are essential for verifying the claims. Without these, the quantitative accuracy of reported affinities, the statistical robustness of comparisons, and the validity of the proteome-wide interaction assignments cannot be independently assessed.

## Reviewer

- **Overall assessment** This manuscript presents a potentially valuable methodological adaptation, extending the native holdup assay to DNA-protein interactions, and applies it to a clinically relevant question regarding GATA1 mutations in hematopoietic disorders. The conceptual framing is clear, and the authors address a genuine gap in the field, namely the lack of a quantitative, high-throughput, wash-free method for measuring DNA-binding affinities of full-length transcription factors in crude extracts. The application to GATA1 and its disease-associated mutants is timely and of interest to both basic and clinical researchers. However, the manuscript as presented has several significant weaknesses. The most critical concern is that the primary data, figures, and supplementary materials were not available for review, making it impossible to verify the quantitative claims, the statistical analyses, and the reproducibility of the results. Even based on the text alone, there are concerns about the interpretation of the luciferase assay data, the potential for indirect DNA-binding effects in the nHU-MS experiments, the limited validation of the nHU method against an orthogonal biophysical technique, and the generalizability of the findings given the use of a single promoter model. The discussion is somewhat speculative in places, particularly regarding the allosteric effects of the N-TAD deletion and the mechanistic interpretation of the NF mutations. Overall, the manuscript is promising but requires substantial revision and access to the primary data before the claims can be considered established.

- **Who would be interested in the results, and why** Researchers in the fields of transcription factor biology, gene regulation, and hematopoiesis would be the primary audience. The methodological advance, the nHU assay for DNA-protein interactions, would be of interest to biochemists and molecular biologists studying DNA-binding proteins, particularly those working with difficult-to-purify full-length proteins or studying disease-associated mutations. Clinically oriented researchers studying GATA1-related disorders, including anemia, thrombocytopenia, and Down syndrome-associated leukemias, would also find the results relevant. The work bridges a methodological gap and provides mechanistic insights into how specific mutations alter GATA1 function, which could inform future therapeutic strategies.

- **Major strengths**
  1. The methodological innovation is significant. Adapting the holdup assay to DNA-protein interactions addresses a real need for a quantitative, wash-free, high-throughput method that works with crude extracts and does not require protein purification. This has broad applicability.
  2. The use of full-length GATA1 in a near-native context is a strength. Many previous biophysical studies have used isolated zinc fingers, which may not capture the full binding behavior of the protein. The nHU approach avoids this limitation.
  3. The combination of functional (luciferase) and biophysical (nHU) data for the same set of mutants provides a more complete picture than either approach alone. The integration of these data with previous protein-protein interaction studies is a thoughtful approach.
  4. The identification of GATA1s as a gain-of-function mutant in terms of DNA binding, and the correlation with increased transcriptional activity, is a novel and potentially important finding that could have implications for understanding the pathogenesis of DS-TAM and DS-AMKL.
  5. The manuscript is generally well-written and logically structured. The authors clearly explain the limitations of existing methods and the rationale for developing the nHU assay.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence integrity and reproducibility
- **Claim pointer** The manuscript claims that the nHU assay can "systematically quantify DNA-protein interactions" and "detect even subtle differences in DNA binding affinities" of GATA1 variants, with specific dissociation constants reported (e.g., 17 nM for 51_WT, 100 nM for 4945_WT, 130 nM for 51_HAP, and 140 nM for the palindromic control).
- **Evidence pointer** Figures 5 and 6, Supplementary Figures S3, S5, S6, and Supplementary Data 1-4. Location not provided for specific data points.
- **Concern** The primary quantitative data supporting the central claims of this manuscript are not available for review. The reported dissociation constants, the statistical significance of differences between mutants, the binding curves, and the Western blot images are all contained in figures and supplementary files that were not provided. Without access to these data, it is impossible to verify the accuracy of the reported values, the appropriateness of the curve fitting, the reproducibility of the measurements, or the statistical power of the comparisons. This is a fundamental limitation that prevents a full assessment of the manuscript's claims.
- **Why it matters** The entire premise of the paper rests on the quantitative accuracy of the nHU measurements. If the reported affinities are not robust, reproducible, and statistically sound, then the conclusions about which mutations affect DNA binding and which do not are not reliable. The claim that the method can detect "subtle differences" in affinity is particularly dependent on the quality of the data and the statistical analysis.
- **Resolution test** The authors must provide the primary data, including all binding curves, Western blot images, replicate measurements, and statistical analyses, for full review. The data should be presented in a clear and accessible format that allows independent verification of the reported affinities and their associated errors.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The manuscript claims that the nHU assay provides quantitative binding affinities that are "comparable to conventional biophysical assays, such as ITC or SPR."
- **Evidence pointer** Figure 5D and the associated text describing the validation using a palindromic DNA fragment previously characterized by SPR.
- **Concern** The validation of the nHU method against an orthogonal technique is limited to a single DNA fragment and a single comparison with previously published SPR data. This is insufficient to establish the general accuracy and reliability of the method. The comparison is made with a palindromic sequence, which may not be representative of the more complex, physiologically relevant sequences used in the rest of the study. Furthermore, the SPR data were obtained with purified recombinant GATA1, while the nHU measurements were performed with GATA1 in crude cell extracts. The agreement between the two could be coincidental or could mask systematic errors that cancel out in this specific case.
- **Why it matters** The claim that nHU produces data comparable to gold-standard biophysical techniques is a key selling point of the method. If this is not rigorously demonstrated, the broader applicability and credibility of the method are called into question. A single-point validation is not sufficient to rule out systematic errors in the nHU approach, such as incorrect estimation of active bait concentration, non-specific binding to the resin, or interference from other proteins in the extract.
- **Resolution test** The authors should validate the nHU method against an orthogonal technique (e.g., ITC, SPR, or fluorescence anisotropy) using multiple DNA sequences with a range of affinities, including both strong and weak binders. Ideally, this validation should be performed with the same full-length GATA1 protein in the same buffer conditions. This would provide a more robust demonstration of the method's accuracy and generalizability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of functional data
- **Claim pointer** The manuscript claims that the short isoform GATA1s "exhibits increased functional activity" based on the luciferase reporter assay, and that this is explained by its increased DNA-binding affinity.
- **Evidence pointer** Figure 1B and the associated text in the Results section.
- **Concern** The interpretation of the luciferase assay data is potentially confounded by the significantly lower expression level of GATA1s compared to wild-type GATA1, as noted in the text. While the authors normalize the luciferase activity to protein expression, this normalization assumes a linear relationship between protein amount and transcriptional activity, which may not hold. Furthermore, the increased activity of GATA1s could be due to factors other than increased DNA binding, such as altered interactions with co-activators or co-repressors, changes in nuclear localization, or differences in protein stability. The manuscript does not adequately address these alternative explanations.
- **Why it matters** The conclusion that GATA1s has increased intrinsic transcriptional activity due to increased DNA binding is a central finding of the paper. If this conclusion is not robust, it weakens the overall narrative and the mechanistic insights derived from it. The potential confounding effect of differential protein expression and the lack of consideration of alternative mechanisms undermine the strength of this claim.
- **Resolution test** The authors should perform additional experiments to directly test the relationship between GATA1s expression level and transcriptional activity, for example by titrating the amount of transfected DNA or using a more quantitative reporter assay. They should also investigate whether the increased activity of GATA1s is due to altered protein-protein interactions, for example by performing co-immunoprecipitation experiments with known GATA1 interaction partners.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and physiological relevance
- **Claim pointer** The manuscript claims that the findings provide "insight into the molecular mechanism of related diseases" and that the nHU assay is a versatile tool for studying transcription factor mutations.
- **Evidence pointer** The use of a single promoter (ATP2B4) and a single cell line (K562) for the functional assays, and HEK293T for the nHU binding assays.
- **Concern** The study is based on a single model system. The ATP2B4 promoter is used for both the functional and binding assays, and the binding assays are performed in HEK293T cells, which are not of hematopoietic origin. It is unclear whether the observed effects on DNA binding and transcriptional activity are specific to this promoter context or generalizable to other GATA1 target genes. The physiological relevance of the findings to hematopoietic disorders is inferred but not directly demonstrated. The manuscript would be strengthened by showing that the effects on DNA binding are consistent across multiple GATA1 target sequences and that the functional consequences are observed in a more physiologically relevant cell type, such as primary erythroid progenitors.
- **Why it matters** The claim that the findings provide insight into disease mechanisms requires that the observed effects are relevant to the physiological context in which GATA1 functions. If the effects are specific to the ATP2B4 promoter or to the artificial context of HEK293T cells, the broader implications for understanding and treating GATA1-related disorders are limited.
- **Resolution test** The authors should extend their analysis to include additional GATA1 target promoters with different numbers and arrangements of GATA binding sites. They should also consider performing the nHU binding assays in a hematopoietic cell line, such as K562, to confirm that the observed affinities are similar in a more relevant cellular context. Ideally, the functional consequences of the mutations would be validated in a primary cell model.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor and data analysis
- **Claim pointer** The manuscript claims that the nHU assay can "detect even subtle differences in DNA binding affinities" and reports specific fold-changes and affinities for different mutants.
- **Evidence pointer** The text describes statistical analyses (t-tests) for the luciferase assay, but the statistical treatment of the nHU binding data is not described in detail. The number of replicates, the error analysis, and the criteria for significance are not clearly stated.
- **Concern** The statistical rigor of the nHU binding measurements is not adequately described. It is unclear how many independent experiments were performed, how the binding curves were fit, how the errors on the reported dissociation constants were calculated, and what statistical test was used to compare the affinities of different mutants. The manuscript mentions "minimum two replicates" for the titration experiments, which is a relatively low number for quantitative binding measurements. The lack of detailed statistical information makes it difficult to assess the reliability of the reported differences in binding affinity.
- **Why it matters** The central claim of the paper is that the nHU assay can quantitatively distinguish between the DNA-binding properties of different GATA1 mutants. This claim requires robust statistical support. Without a clear description of the statistical methods and the associated errors, the significance of the reported differences is uncertain.
- **Resolution test** The authors should provide a detailed description of the statistical analysis of the nHU data, including the number of replicates, the error model, the curve-fitting procedure, and the statistical tests used to compare affinities. They should also consider reporting confidence intervals for the reported dissociation constants.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness of methods
- **Affected element** Materials and Methods, nHU assay description
- **Evidence pointer** Section "Single point and titration native holdup"
- **Issue** The description of the nHU assay methodology is somewhat brief. Key parameters such as the exact composition of the binding buffer, the incubation time, the temperature, and the method for determining the "active" bait concentration are not fully specified. The description of how the apparent affinities are calculated from the measured fold-changes is also abbreviated, referring to a previous publication.
- **Required correction** The authors should provide a more detailed description of the nHU assay protocol, including all buffer compositions, incubation conditions, and the equations used to convert measured fold-changes to apparent affinities. This is essential for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation of data
- **Affected element** Figures and tables
- **Evidence pointer** Figures 1-7, Tables 1
- **Issue** The figures and tables are not available for review. Based on the text, it is unclear how the data are presented, whether error bars are shown, and whether individual data points are displayed. The table of transcription factor binding partners (Table 1) is mentioned but not shown.
- **Required correction** The authors should ensure that all figures and tables are clearly presented, with appropriate error bars, statistical annotations, and clear labels. The data should be made available in a format that allows independent verification.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Section "Opening new frontiers in transcription factor research with native holdup"
- **Issue** The discussion does not adequately address the limitations of the nHU assay. For example, the potential for non-specific binding to the DNA bait, the inability to distinguish between direct and indirect binding, and the fact that the assay measures apparent affinities in a complex mixture are not discussed.
- **Required correction** The authors should include a paragraph in the discussion acknowledging the limitations of the nHU assay and how they might affect the interpretation of the results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology and consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract, Introduction, Results
- **Issue** The manuscript uses the terms "affinity," "apparent affinity," and "dissociation constant" somewhat interchangeably. It is important to be consistent and precise in the use of these terms, as they have distinct meanings in biophysical chemistry.
- **Required correction** The authors should define their terms clearly and use them consistently throughout the manuscript. In particular, they should clarify whether the values reported are true dissociation constants or apparent affinities measured under specific experimental conditions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript would benefit from a more thorough discussion of existing methods for studying DNA-protein interactions, including their strengths and weaknesses. While some methods are mentioned (EMSA, ChIP-seq), a more comprehensive comparison would help to position the nHU assay within the field.
- **Required correction** The authors should expand the introduction and discussion to provide a more complete overview of existing techniques for studying DNA-protein interactions and clearly articulate the specific advantages of the nHU assay over these methods.

- **Technical failings that need to be addressed before the case is established**
  1. The primary data (figures, supplementary figures, and supplementary data) are not available for review, preventing verification of all quantitative claims (R1-M1).
  2. The validation of the nHU method against an orthogonal technique is limited to a single comparison and is insufficient to establish the method's general accuracy (R1-M2).
  3. The statistical analysis of the nHU binding data is not described in sufficient detail to assess the reliability of the reported differences in affinity (R1-M5).
  4. The potential confounding effect of differential protein expression on the interpretation of the luciferase assay data for GATA1s is not adequately addressed (R1-M3).

- **Assessment against Nature-style criteria**
  - **Originality**: The adaptation of the holdup assay to DNA-protein interactions is a novel methodological contribution. While the concept of the holdup assay is not new, its application to nucleic acid binding proteins in a quantitative, high-throughput manner is original and addresses a real need in the field.
  - **Scientific importance**: The application of the method to GATA1 mutations associated with hematopoietic disorders is clinically relevant and provides mechanistic insights that could be important for understanding disease pathogenesis. The finding that GATA1s has increased DNA-binding affinity is potentially significant. However, the importance is somewhat tempered by the limited scope of the validation and the use of a single promoter model.
  - **Interdisciplinary readership**: The work is likely to appeal to a broad readership, including molecular biologists, biochemists, hematologists, and clinical geneticists. The methodological advance is of general interest, and the application to a clinically relevant transcription factor broadens the appeal.
  - **Technical soundness**: The technical soundness of the study cannot be fully assessed without access to the primary data. The described methodology is plausible, but the limited validation and the lack of detailed statistical information are concerns. The use of crude cell extracts and the potential for indirect effects are also potential weaknesses.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible. The introduction provides sufficient background, and the logic of the study is clear. However, some of the methodological details may be challenging for nonspecialists, and the discussion could be more accessible.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a promising methodological advance and potentially important biological findings. However, the lack of access to the primary data, the limited validation of the method, and the insufficient statistical detail prevent a full endorsement at this stage. The authors should be encouraged to resubmit after addressing the major concerns, particularly by providing the primary data for review, expanding the validation of the nHU method, and providing a more detailed description of the statistical analysis.

## Risk / unsupported claims

- The claim that the nHU assay can "systematically quantify DNA-protein interactions" and detect "subtle differences" in affinity is not fully supported without access to the primary data and a more robust validation against an orthogonal technique.
- The specific dissociation constants reported for GATA1 binding to the ATP2B4 promoter fragments (17 nM, 100 nM, 130 nM) cannot be verified without the underlying binding curves and replicate data.
- The claim that GATA1s exhibits increased functional activity due to increased DNA-binding affinity is not fully supported, as the luciferase assay data may be confounded by differential protein expression, and alternative mechanisms are not excluded.
- The claim that the findings provide "insight into the molecular mechanism of related diseases" is an inference that is not directly tested in a physiologically relevant disease model.
- The statement that the nHU assay can identify binding partners "proteome-wide" is based on the mass spectrometry data, but the completeness and sensitivity of this approach are not fully evaluated.
- The claim that the R307C mutation reduces DNA binding and that this explains its reduced activity is supported by the data described, but the mechanistic link is not fully established, and the possibility of other contributing factors is not excluded.