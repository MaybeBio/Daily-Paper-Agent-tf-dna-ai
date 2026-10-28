## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and interpretation as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors identify four distinct nucleosomal DNA sequence classes (Types 1-4) based on WW/SS dinucleotide patterns, demonstrate their widespread distribution in human genomes, show type-specific rotational phasing relationships, and propose that the balance between Type-1 (WW/SS) and Type-4 (anti-WW/SS) nucleosomes, quantified as ΔNPS, predicts four distinct modes of transcription factor-nucleosome interaction
- **Visible evidence base** Results text, methods descriptions, references to Figures 1-6 and Supplementary Figures S1-S13, Supplementary Tables S1-S10
- **Missing materials affecting confidence** All figures, supplementary figures, and supplementary tables are referenced but not provided; no quantitative data, statistical details, or computational parameters are shown in the text; no genome coordinates, motif information, or validation datasets are described

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting framework for classifying nucleosome-TF interactions based on intrinsic DNA sequence features. The central idea that DNA-encoded nucleosome positioning strength (ΔNPS) can predict distinct modes of TF-nucleosome interaction is potentially valuable. However, the evidence as presented is insufficient to establish the core claims. The manuscript relies heavily on descriptive correlations and classification schemes without providing adequate quantitative validation, statistical rigor, or mechanistic demonstration. The absence of all figures and supplementary materials makes it impossible to evaluate the quality of the data analysis or the robustness of the classification criteria. The leap from correlative patterns to mechanistic conclusions about competition versus intrinsic nucleosome preference is not adequately supported.

- **Who would be interested in the results, and why** Researchers studying chromatin structure, nucleosome positioning, transcription factor binding mechanisms, and gene regulation would find this framework potentially useful. The proposed classification of TF-nucleosome interaction modes could inform experimental design for studying pioneer factors and chromatin remodeling. Computational biologists developing predictive models of TF binding in chromatin contexts would also be interested. However, the current presentation is too preliminary for broad impact.

- **Major strengths** The conceptual framework of classifying nucleosome-TF interactions based on intrinsic DNA sequence properties is novel and potentially unifying. The use of ΔNPS as a quantitative metric linking DNA sequence to functional interaction modes is elegant. The cross-species analysis (human, mouse, yeast) and the large TF dataset (515 mammalian, 232 yeast) suggest broad applicability. The identification of four distinct nucleosome types with specific rotational phasing relationships provides a systematic way to think about nucleosome heterogeneity.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "All four nucleosome types are widespread across the human genome both in vivo and in vitro"
- **Evidence pointer** Figure 1, Supplementary Figures S1, Supplementary Tables S2-S3; location not provided
- **Concern** The claim of widespread distribution is based on classification of nucleosomes into four types using criteria that are not fully described. The thresholds for classification, the handling of ambiguous cases, and the statistical significance of the observed distributions are not presented. The text states that Type-1 is most abundant but does not provide the actual proportions, confidence intervals, or comparisons across cell types.
- **Why it matters** The entire framework depends on the validity and robustness of the four-type classification. If the classification is arbitrary or highly sensitive to parameters, all downstream analyses are compromised. Without seeing the actual distributions and their variability, the claim of "widespread" cannot be evaluated.
- **Resolution test** Provide the classification criteria with explicit thresholds, show the distribution of all four types across all datasets with statistical comparisons, and demonstrate that the classification is robust to parameter choices.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** "Nucleosomes sharing the same pattern are rotationally in phase, whereas different patterns exhibit specific rotational offsets, revealing distinct DNA-encoded codes for nucleosome positioning"
- **Evidence pointer** Figure 3, Supplementary Figures S4-S5; location not provided
- **Concern** The DAC/DCC analyses show correlations in positioning, but the interpretation that these reflect "DNA-encoded codes" is an inference. The text does not demonstrate that the observed phasing is specifically due to DNA sequence rather than other factors such as chromatin remodelers, histone variants, or boundary elements. The in vitro data partially addresses this, but the comparison between in vitro and in vivo phasing is not quantitatively presented.
- **Why it matters** The central claim of the paper is that DNA sequence encodes rotational positioning information. Correlation analyses alone cannot establish causality. Without demonstrating that the phasing patterns are intrinsic to the DNA sequence (e.g., through in vitro reconstitution with purified histones and defined sequences), the claim remains speculative.
- **Resolution test** Show quantitative comparison of DAC/DCC peaks between in vitro and in vivo conditions, demonstrate that the phasing patterns are recapitulated with purified components, or provide mutational analyses showing that altering the WW/SS pattern disrupts the predicted phasing.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of classification scheme
- **Claim pointer** "Integrating ΔNPS with in vivo nucleosome occupancy uncovers four distinct modes of nucleosome-TF interaction"
- **Evidence pointer** Figure 5, Supplementary Tables S7-S10; location not provided
- **Concern** The classification of TFs into four interaction modes (DIP/PEAK, DIP/DIP, PEAK/PEAK, PEAK/DIP) is based on qualitative pattern matching of in vivo NO and ΔNPS profiles. The criteria for "dip" and "peak" are defined using one-third thresholds of the dynamic range, but the text does not explain how these thresholds were chosen, how sensitive the classification is to these choices, or how many TFs fall into each category. The AMBIGUOUS category is mentioned but its size and characteristics are not described. Most critically, there is no independent validation that these categories represent biologically distinct mechanisms.
- **Why it matters** The four-mode classification is the main conceptual contribution. If the classification is not robust or does not correspond to actual mechanistic differences, the framework loses its utility. The text claims these modes are "evolutionarily conserved" but does not show the actual conservation analysis.
- **Resolution test** Provide the full distribution of TFs across categories, perform sensitivity analysis on classification thresholds, validate the categories using independent experimental data (e.g., TF binding kinetics, chromatin accessibility), and show quantitative conservation analysis across species.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Alternative explanations
- **Claim pointer** "For DIP/DIP TFs, NDRs may arise because the local DNA sequence disfavors the formation of strong, stable nucleosomes"
- **Evidence pointer** Discussion section; location not provided
- **Concern** The interpretation that DIP/DIP NDRs are due to intrinsically weak nucleosome-forming sequences is plausible but not directly tested. The text acknowledges this is one possibility but does not rule out other mechanisms such as active remodeling, competition with other DNA-binding proteins, or sequence-specific nucleosome destabilization. The correlation between low ΔNPS and low in vivo occupancy does not establish causation.
- **Why it matters** The mechanistic interpretation distinguishes this work from purely descriptive analyses. Without experimental perturbation (e.g., altering the DNA sequence at specific loci and measuring nucleosome occupancy), the proposed mechanism remains one of several possibilities.
- **Resolution test** Provide experimental evidence that mutating the WW/SS pattern at DIP/DIP loci increases nucleosome occupancy, or show that the predicted intrinsically weak nucleosomes are indeed weak in in vitro reconstitution assays.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "Analysis of 747 TFs across eukaryotes shows that the WW/SS and anti-WW/SS patterns are strongly associated with TF binding in chromatin"
- **Evidence pointer** Results section, Supplementary Tables S7-S9; location not provided
- **Concern** The analysis covers 515 mammalian and 232 yeast TFs, but the text does not describe how these TFs were selected, whether they represent all known TFs in these species, or whether there is a selection bias. The claim of "strong association" is not quantified. The conservation across species is mentioned but not demonstrated with data.
- **Why it matters** The generality of the framework depends on the representativeness of the TF dataset and the strength of the association. If the TF set is biased toward well-characterized factors or if the association is weak for many TFs, the conclusions would need to be tempered.
- **Resolution test** Provide the complete list of TFs analyzed, describe the selection criteria, quantify the association strength (e.g., effect sizes, confidence intervals), and show the conservation analysis explicitly.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Classification criteria
- **Evidence pointer** Online Methods, "Classification of TF patterns"; location not provided
- **Issue** The description of the classification criteria using "one-third of dynamic range" is vague. It is unclear whether this refers to the full range of the signal across all positions or within a specific window, and how the global maximum/minimum are defined relative to local fluctuations.
- **Required correction** Provide a precise mathematical definition of the classification criteria, including the exact window sizes, normalization procedures, and how the one-third thresholds are applied.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Correlation analyses
- **Evidence pointer** Results, "The four types of nucleosomes exhibit distinctive genomic organization"; location not provided
- **Issue** The correlation values between nucleosome maps are reported (e.g., 0.74, 0.76) but no confidence intervals, significance tests, or correction for multiple comparisons are mentioned.
- **Required correction** Report confidence intervals and p-values for all correlation coefficients, and describe how multiple testing was handled.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** TF motif matching
- **Evidence pointer** Online Methods, "Genome-wide protein-DNA interaction (ChIP-seq) datasets"; location not provided
- **Issue** The text states that motifs were obtained for "approximately 50% of TFs" but does not explain how the remaining 50% were handled. Were they excluded from analysis? Could this introduce bias?
- **Required correction** Describe the handling of TFs without matching motifs, and discuss potential biases introduced by the exclusion.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** GC content analysis
- **Evidence pointer** Results, "In vivo nucleosome occupancy and ΔNPS exhibit distinct patterns around TF binding sites"; location not provided
- **Concern** The text notes that GC content correlates with in vitro NO for some TFs but not others. This is presented descriptively without exploring why this might be the case or what it means for the proposed framework.
- **Required correction** Provide a brief interpretation of the GC content findings and how they relate to the proposed DNA-encoded nucleosome positioning model.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Computational pipeline
- **Evidence pointer** Online Methods, "Availability of methods"; location not provided
- **Issue** The GitHub repository is mentioned, but the text does not describe the computational environment, software versions, or parameters used for the analysis.
- **Required correction** Provide a detailed description of the computational environment, including software versions and key parameters, to ensure reproducibility.

## Risk / unsupported claims
- The claim that "DNA-encoded codes" govern nucleosome positioning is not directly demonstrated; the evidence is correlative
- The four-mode classification of TF-nucleosome interactions is presented without independent validation
- The statement that "chromatin proteins exert stronger regulatory influence" on Type-1 and Type-4 nucleosomes is inferred from abundance differences without direct mechanistic evidence
- The proposed model in Figure 6 is not described in sufficient detail to evaluate its predictive power
- The conservation of interaction modes across species is claimed but not shown with data
- The relationship between ΔNPS and in vitro nucleosome occupancy is described as "strong" but no correlation coefficient or effect size is provided
- The functional significance of the four nucleosome types for gene regulation is not experimentally addressed
- The claim that "NDRs can arise through at least two distinct sequence-driven mechanisms" is presented as a conclusion but is based on correlative analysis without perturbation experiments