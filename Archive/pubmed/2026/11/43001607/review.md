## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and author contributions. No figures or supplementary information were provided for review.
- **Assessment boundary** Assessment is limited to the claims as presented in the text. Figures, tables, and supplementary materials referenced in the text were not available for direct evaluation. Experimental validation is assessed based on the described methods and reported outcomes.
- **Shared manuscript claim summary** The manuscript claims that the FCS finger of the Drosophila PRC1 accessory subunit Scm directly binds the atypical Tudor domain of the PRC2.1 accessory subunit Pcl, and that this interaction provides the molecular basis for the selective association between canonical PRC1 and PRC2.1. The authors further claim that a native affinity-purification strategy using cryo-milled embryos preserves higher-order Polycomb assemblies, and that AlphaFold3 predictions were validated by mutagenesis and biophysical experiments.
- **Visible evidence base** The evidence base consists of the textual description of affinity purification results, AlphaFold3 predictions, size-exclusion chromatography experiments, and native mass spectrometry data. Specific numerical results, chromatograms, mass spectra, and statistical analyses are referenced but not shown in the provided material.
- **Missing materials affecting confidence** Figures 1-3, Supplementary Figures S1 and S2, all raw proteomics and mass spectrometry data, statistical analysis outputs, and the independent study by Lyons et al. (2026) are not available. Without these, the quantitative support for claims regarding complex recovery, interaction stoichiometry, and mutagenesis effects cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a significant open question in Polycomb biology by identifying a direct molecular interaction between Scm and Pcl that links canonical PRC1 and PRC2.1 in Drosophila. The combination of native affinity purification, AlphaFold3 prediction, and biochemical validation is a logical and potentially powerful approach. However, the current text does not provide sufficient quantitative detail to fully evaluate the robustness of the affinity purification results, and the absence of figures limits verification of the biophysical data. The core interaction claim is plausible and well-supported by the described mutagenesis and mass spectrometry experiments, but the broader claim regarding preservation of higher-order assemblies requires more evidence than is presented in the text alone.
- **Who would be interested in the results, and why** Researchers studying Polycomb group proteins, epigenetic regulation, chromatin biology, and transcriptional repression in Drosophila and other organisms. The identification of a direct Scm-Pcl interaction will be of interest to those investigating how different Polycomb complexes coordinate at target loci. The native purification method may also attract biochemists interested in preserving protein complexes in near-physiological conditions. The evolutionary discussion regarding divergence of this interaction in mammals will interest comparative epigenetics researchers.
- **Major strengths** The study addresses a previously unresolved question with a clear hypothesis-driven approach. The use of AlphaFold3 to systematically screen interactions is innovative and well-integrated with experimental validation. The complementary charge-reversal mutagenesis strategy provides strong evidence for the specificity of the predicted interface. The native purification method represents a technical advance that may have broader utility. The discussion of evolutionary divergence is thoughtful and appropriately cautious.
- **Major Concerns** The following concerns are identified.
- **Minor Comments** The following comments are identified.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3.
- **Assessment against Nature-style criteria** Originality: The identification of a direct Scm-Pcl interaction is novel and addresses a gap in the field. Scientific importance: The finding has implications for understanding how Polycomb complexes coordinate, which is a central question in epigenetic regulation. Interdisciplinary readership: The work will primarily interest specialists in chromatin biology and epigenetics; the broader cell biology community may find the native purification method of interest. Technical soundness: The described methods are generally appropriate, but the lack of quantitative detail in the affinity purification results and the absence of figures prevent full assessment. Readability for nonspecialists: The text is clearly written and accessible, though some domain-specific terminology may require familiarity with Polycomb biology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core interaction claim appears well-supported, but the affinity purification evidence and the broader claim about higher-order assemblies require additional quantitative detail and figure verification.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that their native affinity-purification strategy "recovers intact canonical PRC1 together with the complete PRC2.1 complex" and that this recovery is selective, based on the described experiments.
- **Evidence pointer** Results section "Affinity purification of Polycomb complexes from cryo-milled embryos preserves higher-order Polycomb assemblies under native conditions", Figure 1a-b, location not provided
- **Concern** The text states that affinity purification from cryo-milled embryos recovered canonical PRC1, PRC2.1, PhoRC subunit Sfmbt, and Sxc/Ogt, but no quantitative data are presented. The methods describe a differential abundance analysis using proDA with significance thresholds of adjusted p-value below 0.1 and fold change above 4, yet no results of this analysis are reported in the text. It is unclear how many replicates were analyzed, what the magnitude of enrichment was for each identified protein, and whether the recovery of PRC2.1 was statistically significant relative to controls. The claim that the purification preserves "higher-order Polycomb assemblies" is not directly supported by any experimental evidence described, as no size exclusion, cross-linking, or other assembly-state analysis of the purified material is presented.
- **Why it matters** The selective association between canonical PRC1 and PRC2.1 is the foundational observation of the study. Without quantitative evidence demonstrating specific and reproducible co-purification, the premise for the subsequent interaction studies is weakened. The claim about preserving higher-order assemblies is a significant methodological assertion that requires direct evidence.
- **Resolution test** Provide the results of the differential abundance analysis, including the number of replicates, the fold changes and adjusted p-values for all identified PRC1, PRC2.1, PhoRC, and Sxc/Ogt subunits, and a clear description of how specificity was assessed. To support the claim of higher-order assemblies, include size-exclusion chromatography or native gel analysis of the purified material showing co-elution of the complexes at high molecular weight.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation
- **Claim pointer** The authors claim that AlphaFold3 identified "a single high-confidence interaction between the FCS finger of the Scm and the Tudor domain of Pcl" and that this prediction was validated by mutagenesis.
- **Evidence pointer** Results section "AlphaFold3 identifies the Scm FCS finger–Pcl Tudor interface as the only high-confidence predicted interaction between canonical PRC1 and PRC2.1", Figure 1c-f, location not provided
- **Concern** The text states that AlphaFold3 was used to "systematically model interactions between canonical PRC1 and PRC2.1 subunits" and that only one high-confidence interaction was identified. However, no details are provided regarding the AlphaFold3 confidence metrics used, the number of models generated, the specific subunits tested, or how "high-confidence" was defined. The description of the predicted interface is limited to a list of residues without any structural context or model quality assessment. The mutagenesis experiments are described as validating the interface, but the text does not specify how many mutations were tested beyond the two charge-reversal pairs, nor whether the effects were dose-dependent or specific to the predicted interface.
- **Why it matters** AlphaFold3 predictions require careful interpretation, and the claim that this is the only high-confidence interaction is central to the conclusion that Scm-Pcl is the sole molecular link. Without transparency in the prediction methodology and confidence thresholds, the reader cannot assess whether other potential interactions were missed. The mutagenesis validation is the key experimental support, and its rigor directly affects confidence in the interaction model.
- **Resolution test** Provide details on the AlphaFold3 prediction settings, the confidence scores (e.g., ipTM, pTM) for the Scm-Pcl model and for all other subunit combinations tested, and the criteria used to define high-confidence. For the mutagenesis, report the number of independent experiments, the quantitative binding data (e.g., elution volumes, mass spectrometry peak intensities) for all mutant combinations, and include negative controls showing that mutations do not cause global misfolding.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance
- **Claim pointer** The authors claim that the Scm-Pcl interaction "provides the molecular basis for the selective association between canonical PRC1 and PRC2.1" and that this has implications for PRC2.1 recruitment to Polycomb target genes.
- **Evidence pointer** Discussion section, Figure 3, location not provided
- **Concern** The manuscript does not present any functional experiments demonstrating that the Scm-Pcl interaction is required for the association between canonical PRC1 and PRC2.1 in cells or embryos. The biochemical data show that the purified domains interact in vitro, but there is no evidence that disrupting this interaction in vivo affects complex association, PRC2.1 recruitment, or Polycomb-mediated repression. The discussion speculates about the role of this interaction in recruiting PRC2.1 to PREs, but this is not tested. The reference to the independent study by Lyons et al. (2026) suggests that functional validation may exist elsewhere, but it is not part of this manuscript.
- **Why it matters** The title and abstract make a strong claim about the functional significance of the Scm-Pcl interaction. Without in vivo evidence, the manuscript establishes a molecular interaction but does not demonstrate its biological role. The claim that this interaction is "the molecular basis" for the selective association requires cellular or genetic validation.
- **Resolution test** Include experiments showing that mutations disrupting the Scm-Pcl interaction affect the co-purification of canonical PRC1 and PRC2.1 from embryos, or that they alter PRC2.1 occupancy at Polycomb target genes. Alternatively, temper the claims in the title and abstract to reflect that the study identifies a direct interaction that may mediate the association, pending functional validation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the interaction was identified "using AlphaFold3 to systematically model interactions between canonical PRC1 and PRC2.1 subunits," but does not mention the native purification method that is a key advance of the study. The abstract also does not specify the stoichiometry of the complex, which is a notable finding from the mass spectrometry.
- **Required correction** Briefly mention the native purification approach in the abstract and include the 1:1 stoichiometry finding to better represent the full scope of the study.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section on affinity purification
- **Evidence pointer** Results section "Affinity purification of Polycomb complexes from cryo-milled embryos preserves higher-order Polycomb assemblies under native conditions", location not provided
- **Issue** The text mentions that the purification recovered "the PRC2.1 subunits Pcl, E(z), Su(z)12, and Esc" but does not mention whether the PRC2.2-specific subunits (e.g., Jing) were detected. This is relevant because the claim is about selective association with PRC2.1, and the absence of PRC2.2 subunits would strengthen this claim.
- **Required correction** State explicitly whether PRC2.2-specific subunits were detected in the purification, and if not, note this as evidence for selectivity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Materials and Methods, affinity purification
- **Evidence pointer** Materials and Methods section "Affinity purification from cryo-milled embryos", location not provided
- **Issue** The methods state that affinity purification was performed in triplicates, but the text does not describe how variability between replicates was handled or whether the results were consistent. The use of proDA for differential analysis is mentioned, but the specific comparison (e.g., Ph-tagged vs. untagged control) is not clearly defined.
- **Required correction** Clarify the experimental design, including the exact comparison used for differential analysis, and describe how reproducibility across replicates was assessed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section, location not provided
- **Issue** The discussion states that the Scm-Pcl interaction is "unlikely to be evolutionarily conserved in mammals" based on the absence of the FCS finger in mammalian SCMH1 and SCML2. However, the text does not discuss whether other regions of Scm or other mammalian proteins could compensate for this interaction. The evolutionary argument would be strengthened by a more nuanced discussion.
- **Required correction** Add a sentence acknowledging that the absence of the FCS finger does not exclude the possibility of convergent evolution or alternative interaction mechanisms in mammals.

## Risk / unsupported claims
- The claim that the native affinity-purification strategy "preserves higher-order Polycomb assemblies" is not supported by direct experimental evidence in the text. No assembly-state analysis is described.
- The claim that the Scm-Pcl interaction is "the molecular basis for the selective association between canonical PRC1 and PRC2.1" is not supported by in vivo functional experiments. The manuscript demonstrates an in vitro interaction but does not show that this interaction is necessary or sufficient for the association in cells.
- The claim that AlphaFold3 identified "a single high-confidence interaction" cannot be fully evaluated without details on the prediction methodology and confidence metrics.
- The statement that the purification recovered "the complete PRC2.1 complex" is not quantitatively supported, as no data on subunit stoichiometry or completeness are presented.
- The evolutionary argument that the interaction is unlikely to be conserved in mammals is speculative and not directly tested.