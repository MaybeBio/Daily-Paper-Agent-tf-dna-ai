## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and conclusions as presented in the manuscript
- **Shared manuscript claim summary** The authors analyze 20 purportedly pure Ophiocordyceps sinensis strains and report that each simultaneously produces naturally paired MAT1-1-1 and MAT1-2-1 proteins with structural diversity, including N- and/or C-terminal truncations and amino acid substitutions in DNA-binding domains. They interpret this heterogeneity as evidence for multiple co-occurring fungal taxa within these strains, supporting a self-sterile reproductive model involving heterothallic mating or hybridization rather than self-fertilization.
- **Visible evidence base** Sequence alignments (Figures S1, S2), AlphaFold-predicted 3D structural models, TM-align and SW 3D superposition analyses (Figures 4, 5, S3–S10), ExPASy ProtScale plots, Tables 1–3, and previously published genomic/transcriptomic data
- **Missing materials affecting confidence** Raw sequence data, AlphaFold confidence scores (pLDDT) for individual models, statistical analyses, experimental validation of predicted structural differences, and details on strain purity verification

## Reviewer
- **Overall assessment** The manuscript addresses an important question regarding the reproductive biology of Ophiocordyceps sinensis, a species of significant medicinal and economic value. The authors present a descriptive analysis of structural variation in mating-type proteins across 20 strains and interpret this as evidence for heterogeneous fungal origins. While the topic is of interest, the study is largely computational and descriptive, lacking experimental validation. The central claim that structural diversity in mating proteins indicates multiple fungal taxa within purportedly pure strains is plausible but not definitively established by the evidence presented. The manuscript would benefit from clearer presentation of methods, quantitative comparisons, and acknowledgment of alternative interpretations.
- **Who would be interested in the results, and why** Researchers studying fungal reproductive biology, particularly mating-type systems in ascomycetes; scientists working on Ophiocordyceps sinensis and the Cordyceps sinensis insect-fungal complex; those interested in the systematics and population genetics of medicinal fungi; and researchers studying the limitations of single-strain cultivation for complex fungal life cycles.
- **Major strengths** The manuscript addresses a significant and understudied question about the reproductive strategy of an economically important fungus. The use of AlphaFold-predicted structures to compare mating protein variants across multiple strains is a novel approach. The authors integrate genomic, transcriptomic, and protein-level evidence from previous studies to support their interpretation. The discussion of methodological limitations in strain purity assessment is thoughtful and adds nuance to the interpretation.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of experimental validation), R1-M2 (overinterpretation of AlphaFold predictions), R1-M3 (insufficient quantitative analysis), R1-M4 (unresolved strain purity question)
- **Assessment against Nature-style criteria** Originality: The study applies structural prediction approaches to mating-type proteins in a novel context, but the conceptual framework builds heavily on prior work by the same group. Scientific importance: The question of reproductive strategy in O. sinensis is important for understanding its biology and cultivation, but the findings are largely confirmatory of previous suggestions rather than transformative. Interdisciplinary readership: The topic bridges mycology, structural biology, and medicinal plant research, but the narrow focus on one species may limit broader appeal. Technical soundness: The computational methods are appropriate but lack validation; the absence of experimental confirmation weakens the conclusions. Readability for nonspecialists: The manuscript is dense and assumes significant background knowledge; the extensive use of strain identifiers and protein accession numbers without clear contextualization may hinder accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an interesting hypothesis supported by descriptive computational analysis, but the central claims require experimental validation and more rigorous quantitative support before the case is convincing.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that structural diversity in naturally paired MAT1-1-1 and MAT1-2-1 proteins indicates heterogeneous fungal origins within purportedly pure O. sinensis strains.
- **Evidence pointer** Sections 2.1–2.6, Tables 1–2, Figures 1–5
- **Concern** The central conclusion rests entirely on computational predictions and sequence analysis. No experimental validation is provided to confirm that the observed protein variants are actually expressed, functional, or derived from distinct fungal genomes. The authors do not perform any biochemical assays, protein-protein interaction studies, or functional complementation experiments to support their claims about mating compatibility or reproductive mode.
- **Why it matters** Without experimental validation, the interpretation that structural diversity reflects heterogeneous fungal origins remains speculative. Alternative explanations, such as allelic variation within a single species, post-translational modifications, or artifacts of cDNA amplification, cannot be excluded. The claim that these variants support a self-sterile reproductive model requires functional evidence.
- **Resolution test** Provide experimental evidence such as heterologous expression and DNA-binding assays for representative variants, co-immunoprecipitation of MAT1-1-1 and MAT1-2-1 proteins, or genetic crosses demonstrating mating compatibility. Alternatively, use genome sequencing of individual strains to confirm the presence or absence of MAT loci and rule out contamination.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural interpretation
- **Claim pointer** The authors claim that AlphaFold-predicted 3D structural models reveal distinct heteromorphic stereostructures across strains, with altered hydrophobic properties and secondary/tertiary configurations.
- **Evidence pointer** Sections 2.1–2.5, Figures 4–5, Figures S3–S10
- **Concern** The manuscript relies heavily on AlphaFold-predicted structures without reporting confidence metrics (pLDDT scores) for the specific models used. The authors describe "completely separated overall stereostructures" and "non-overlaid structures" based on TM-align and SW 3D superposition, but no quantitative measures of structural similarity or dissimilarity are provided. The biological significance of the observed structural differences is asserted rather than demonstrated.
- **Why it matters** AlphaFold predictions are computational models, not experimentally determined structures. Without confidence scores and quantitative comparisons, readers cannot assess whether the reported structural differences are meaningful or within the range of prediction error. The claim that these differences alter DNA-binding affinity or specificity is speculative without functional data.
- **Resolution test** Report pLDDT scores for all AlphaFold models used, provide quantitative structural similarity metrics (e.g., RMSD, TM-score) with appropriate statistical comparisons, and validate key structural predictions using experimental methods such as circular dichroism, NMR, or X-ray crystallography for at least representative variants.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative analysis
- **Claim pointer** The authors describe "differential natural pairings" and categorize strains into Group I and Group II based on the pairing patterns of truncated and full-length mating proteins.
- **Evidence pointer** Section 2.3, Tables 1–2, Figure 3
- **Concern** The classification of strains into groups and the description of "differential natural pairings" are presented without any statistical analysis. No tests are performed to determine whether the observed patterns are significantly different from what would be expected by chance, nor are any measures of variability or confidence provided. The manuscript does not quantify the frequency or distribution of the observed variants across strains.
- **Why it matters** The central claim of "differential natural pairings" implies a systematic pattern that supports the heterogeneous origin hypothesis. Without statistical support, the observed patterns could be due to random variation, sampling artifacts, or technical errors in cDNA amplification. The lack of quantitative rigor undermines the strength of the conclusions.
- **Resolution test** Provide statistical analyses such as chi-square tests or Fisher's exact tests for the distribution of protein variants across strains, calculate confidence intervals for the observed frequencies, and perform power analyses to determine whether the sample size of 20 strains is sufficient to support the claimed patterns.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Strain purity
- **Claim pointer** The authors state that the 20 O. sinensis strains were "purportedly homogenous" and use this assumption as a basis for interpreting the observed protein diversity as evidence for heterogeneous fungal origins.
- **Evidence pointer** Sections 2.3, 3.2, 4.1, Tables 1–2
- **Concern** The manuscript does not provide any direct evidence that the 20 strains are actually pure cultures. The authors acknowledge that the strains were previously reported as pure by Li et al. [36], but they also present extensive arguments questioning the reliability of that assessment. However, they do not perform any new experimental work to verify strain purity, such as single-spore isolation followed by genome sequencing or strain-specific molecular markers.
- **Why it matters** The interpretation of the results depends critically on whether the strains are truly homogeneous. If the strains contain multiple fungal taxa, the observed protein diversity could simply reflect contamination rather than a biologically meaningful pattern. Conversely, if the strains are pure, the diversity might represent allelic variation within a single species, which would not support the heterogeneous origin hypothesis. The manuscript cannot resolve this fundamental ambiguity with the data presented.
- **Resolution test** Perform genome sequencing of multiple single-spore isolates from each strain to assess genetic homogeneity, use strain-specific molecular markers to test for the presence of multiple genotypes, or employ culture-independent methods (e.g., metagenomic sequencing) to characterize the full microbial community within each strain.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Section 4.4
- **Evidence pointer** Section 4.4
- **Issue** The description of the structural superposition methods is brief and lacks specific parameters. The authors mention TM-align and SW 3D algorithms but do not specify the versions, default settings, or criteria for determining "complete separation" or "non-overlaid" structures.
- **Required correction** Provide detailed parameters for the structural alignment analyses, including software versions, scoring functions, and thresholds used to classify structures as similar or dissimilar. Consider including a supplementary methods section with step-by-step protocols.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 4–5, Figures S3–S10
- **Evidence pointer** Figures 4–5, Figures S3–S10
- **Issue** The figures showing structural superpositions are described in the text but not included in the main manuscript. The supplementary figures are referenced but their content is not described in sufficient detail in the figure legends.
- **Required correction** Ensure that all figures are clearly labeled and that figure legends provide sufficient context for readers to interpret the structural comparisons without referring back to the main text. Consider including at least one representative structural superposition figure in the main text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Sections 2.1–2.6, Tables 1–2
- **Issue** The terms "authentic," "variant," "truncated," and "full-length" are used to describe the mating proteins, but the definitions are not consistently applied. For example, the reference protein AGW27560 is described as "authentic" and "full-length," while other proteins are described as "truncated" or "variant" without clear criteria for these classifications.
- **Required correction** Define the terms used to classify the proteins in the Methods section and apply them consistently throughout the manuscript. Consider using a standardized nomenclature for the protein variants.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1
- **Issue** The discussion of the functional significance of the HMG-box domains would benefit from more direct comparison with experimental studies in other fungi that have characterized the DNA-binding properties of MAT1-1-1 and MAT1-2-1 proteins.
- **Required correction** Add references to experimental studies that have characterized the DNA-binding specificity and affinity of mating-type HMG-box domains in other ascomycetes, and discuss how the structural variations observed here might affect these properties.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Section 4.1
- **Evidence pointer** Section 4.1
- **Issue** The manuscript does not state whether the sequence data and AlphaFold models used in this study are publicly available or how readers can access them.
- **Required correction** Include a data availability statement specifying where the sequence data, AlphaFold models, and analysis scripts can be accessed, or state that they are available upon request.

## Risk / unsupported claims
- The claim that structural diversity in mating proteins provides "protein-level evidence supporting heterogeneous fungal origins" is not supported by direct experimental evidence and remains an interpretation.
- The assertion that the observed patterns are "inconsistent with a strictly self-fertilization reproductive model" is based on indirect evidence and does not exclude other explanations.
- The claim that "differential natural pairings" of mating proteins support a self-sterile reproductive strategy is not quantitatively established.
- The statement that the strains are "purportedly homogenous" is acknowledged as uncertain, yet the analysis proceeds without resolving this fundamental issue.
- The biological significance of the observed structural differences in DNA-binding domains is asserted but not demonstrated through functional assays.
- The use of AlphaFold-predicted structures without reporting confidence metrics makes the structural comparisons difficult to evaluate.