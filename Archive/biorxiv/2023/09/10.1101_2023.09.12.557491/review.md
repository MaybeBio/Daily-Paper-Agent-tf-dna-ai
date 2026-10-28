## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, supporting information references)
- **Assessment boundary** Scientific validity of computational predictions and mechanistic claims; no experimental validation data provided
- **Shared manuscript claim summary** The authors use docking and molecular dynamics simulations to predict binding sites of three small molecule inhibitors (SPIs) at the Pol II-Spt5 interface, and report that strongly bound SPIs alter RNA and DNA stability at the exit site through indirect effects on Spt5-nucleic acid interactions
- **Visible evidence base** Docking energies (Table 1), MD simulation analyses (RMSD, RMSF, distance maps, contact maps, PCA, MM/GBSA binding energies), Figures 1-6, Figures S1-S14
- **Missing materials affecting confidence** No experimental binding affinity data, no functional assays, no validation of force field parameters for SPI molecules, no convergence analysis for MD simulations, no error estimates for MM/GBSA calculations, no sequence information for nucleic acids used

## Reviewer
- **Overall assessment** The manuscript presents a computational study aimed at elucidating the binding modes of three small molecule inhibitors to the Pol II-Spt5 complex and their effects on nucleic acid dynamics. The work addresses a relevant question in transcription regulation and potential therapeutic intervention for Huntington's disease. However, the study is purely computational and the claims regarding mechanistic implications for transcription inhibition are not sufficiently supported by the evidence presented. Several technical aspects require clarification and additional analysis before the conclusions can be considered robust.

- **Who would be interested in the results, and why** Researchers in transcription regulation, structural biology of RNA polymerase complexes, and computational drug discovery would find this work of interest. The study provides initial structural hypotheses for SPI binding that could guide future experimental studies. Those working on therapeutic strategies for repeat-expansion disorders may also be interested in the potential mechanism of action of these inhibitors.

- **Major strengths**
  1. The study addresses an important and timely question regarding the mechanism of action of recently discovered Spt5-Pol II inhibitors
  2. The computational approach combining docking and MD simulations is appropriate for generating testable hypotheses
  3. The authors acknowledge limitations of their approach and discuss potential sources of error
  4. The analysis of enantiomer-specific effects adds depth to the study
  5. The work provides specific predictions that can be experimentally tested

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "two molecules out of three demonstrated strong binding with Spt5 and Pol II, while the other molecule was more loosely bound and sampled multiple binding sites" based on MD simulations
- **Evidence pointer** Figure 3, Table 1, Methods section (MD simulations)
- **Concern** The classification of "strong" versus "loose" binding is based on qualitative observations of ligand density and MM/GBSA binding energies. However, no quantitative criteria are provided for this classification. The MM/GBSA binding energies are reported without standard errors or confidence intervals, making it impossible to assess whether the differences between SPI-II and the other two molecules are statistically significant. Additionally, the authors note that MM/GBSA is known to overestimate binding energies, yet they do not provide any calibration or correction for this systematic bias.
- **Why it matters** The central claim of the paper rests on the distinction between strong and weak binding of the three SPIs. Without quantitative measures of uncertainty, the reader cannot evaluate whether the observed differences are meaningful or within the noise of the computational method.
- **Resolution test** Provide standard errors for MM/GBSA binding energies across replicate simulations. Perform statistical tests (e.g., bootstrap or t-test) to demonstrate that the binding energy differences between SPI-II and SPI-I/III are significant. Alternatively, provide additional metrics such as residence times or dissociation constants estimated from the simulations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "SPIs indirectly affected RNA and DNA dynamics at the exit site as DNA became more flexible while RNA was stabilized by increased interactions with Spt5"
- **Evidence pointer** Figure 5, Figure 6, Figures S7-S14
- **Concern** The claim that SPI binding causes DNA destabilization and RNA stabilization is based on RMSF and RMSD comparisons between SPI-bound and apo systems. However, the magnitude of the reported differences is not quantified, and no statistical analysis is provided to demonstrate that these differences are significant given the expected thermal fluctuations. Furthermore, the authors do not address whether the observed effects on nucleic acid dynamics are within the range expected from sampling variability across replicate simulations. The distance map analysis (Figure 5c) shows qualitative differences, but no quantitative comparison is made.
- **Why it matters** The mechanistic conclusion that SPI binding alters nucleic acid stability is the primary scientific contribution of this work. If the observed differences are not statistically robust, the central conclusion is not supported.
- **Resolution test** Provide quantitative measures of RMSF differences with error bars across replicates. Perform statistical tests to compare SPI-bound and apo systems. Report the magnitude of changes in interaction distances and assess whether they exceed thermal fluctuations. Consider computing free energy differences for nucleic acid binding in the presence and absence of SPIs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "we predicted the binding sites of three selected SPIs at the Pol II-Spt5 interface by docking and molecular dynamics simulations"
- **Evidence pointer** Methods section (Docking of SPIs), Figure 2, Figure S4
- **Concern** The docking protocol uses a grid that covers the experimentally suggested binding region, which introduces bias into the docking results. The authors acknowledge this limitation but do not assess how this bias affects the predicted binding modes. Additionally, the docking was performed on a cryo-EM structure with 3.7 Å resolution, which may not accurately represent the conformational state relevant for inhibitor binding. No ensemble docking or induced-fit effects were considered. The authors also do not validate their docking protocol against known binding modes or use multiple docking programs to assess robustness.
- **Why it matters** The predicted binding sites are the foundation for all subsequent MD simulations and mechanistic interpretations. If the initial docking poses are incorrect or biased, the entire downstream analysis may be compromised.
- **Resolution test** Perform docking without the experimental bias (e.g., blind docking on the entire protein surface) and compare results. Use multiple docking programs or scoring functions to assess the robustness of predicted binding modes. Consider ensemble docking using multiple conformations of the complex. Validate the docking protocol on a test set with known binding modes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors suggest that "the transcription inhibition mechanism induced by SPIs can be related to Spt5-nucleic acid interactions, which were altered to some extent with strong binding of SPIs"
- **Evidence pointer** Discussion section
- **Concern** The connection between the observed changes in nucleic acid dynamics and the experimentally observed transcription inhibition is speculative. The authors do not provide a mechanistic model linking altered RNA/DNA stability to inhibition of transcription elongation or initiation. The relevance of the observed effects to the selective inhibition of mutant huntingtin gene transcription is not addressed. The authors acknowledge that the nucleic acid sequences used are not those of the huntingtin gene, which limits the direct relevance of their findings.
- **Why it matters** The broader significance of this work depends on its ability to explain the selective inhibition of mutant huntingtin gene transcription. Without a clear mechanistic link, the study provides only descriptive observations of SPI binding effects.
- **Resolution test** Provide a more detailed mechanistic model connecting altered nucleic acid dynamics to transcription inhibition. Discuss how the observed effects could explain the selectivity for mutant huntingtin gene transcription. Consider performing simulations with huntingtin gene sequences to test the relevance of the findings.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "we performed simulations of both S- and R-enantiomers (S-I and R-I). We presented the results of R-I in the main text as this enantiomer has stronger binding to the complex and more impact on the dynamics of nucleic acids"
- **Evidence pointer** Methods section, Figure S2
- **Concern** The choice to present only the R-enantiomer in the main text is not well justified. The authors state that R-I has stronger binding and more impact, but no quantitative comparison is provided. The implications of the enantiomer-specific effects for the experimental observations are not discussed. If the experimental studies used a racemic mixture or the S-enantiomer, the relevance of the presented results would be unclear.
- **Why it matters** The enantiomer-specific effects could be important for understanding the mechanism of action of these inhibitors and for drug development. The lack of quantitative comparison and discussion limits the utility of this finding.
- **Resolution test** Provide quantitative comparison of binding energies and nucleic acid dynamics for both enantiomers. Discuss the implications of enantiomer-specific effects for the experimental observations and drug development.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section
- **Evidence pointer** Methods section (MD simulations)
- **Issue** The description of the MD simulation setup lacks some details that would be important for reproducibility, such as the specific ions added, the salt concentration, and the temperature coupling scheme details.
- **Required correction** Provide additional details on the ion concentration, the specific ions used, and the temperature coupling scheme. Consider adding a table summarizing the simulation setup for each system.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section
- **Evidence pointer** Figure 3, Table 1
- **Concern** The MM/GBSA binding energies are reported without any measure of uncertainty. The authors note that the method is known to overestimate binding energies but do not provide any assessment of the reliability of their calculated values.
- **Required correction** Provide standard deviations or standard errors for the MM/GBSA binding energies across replicate simulations. Discuss the expected accuracy of the method for this system.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Concern** The discussion of the implications for Huntington's disease treatment is brief and does not fully address the potential therapeutic relevance of the findings.
- **Required correction** Expand the discussion of the therapeutic implications, including how the predicted binding modes could inform the design of more potent or selective inhibitors.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Concern** The chemical structures of the SPIs are shown in Figure 1, but the figure caption does not provide sufficient detail about the structural features of each molecule.
- **Required correction** Expand the figure caption to describe the key structural features of each SPI and highlight the differences between them.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section
- **Evidence pointer** Methods section (Analysis of the simulations)
- **Concern** The PCA analysis on the relative center of mass of ligands is described, but the number of principal components used and the variance explained are not reported.
- **Required correction** Report the number of principal components used and the fraction of variance explained by each component.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Concern** The abstract is dense and could be more accessible to a broader audience. The key finding regarding the differential effects on RNA and DNA stability could be stated more clearly.
- **Required correction** Consider revising the abstract to more clearly state the main finding and its potential significance.

## Risk / unsupported claims
- The claim that SPI binding "causes" DNA destabilization and RNA stabilization is not supported by the evidence, as the study is correlational and does not establish causality
- The statement that "the transcription inhibition mechanism induced by SPIs can be related to Spt5-nucleic acid interactions" is speculative and not directly supported by the simulation data
- The relevance of the findings to the selective inhibition of mutant huntingtin gene transcription is not established, as the simulations use nucleic acid sequences from the cryo-EM structure rather than huntingtin gene sequences
- The classification of SPI-II as "loosely bound" based on qualitative observations is not quantitatively supported
- The claim that R-I is the more active enantiomer is not supported by any quantitative comparison with S-I
- The MM/GBSA binding energies are reported without uncertainty estimates, making it impossible to assess their reliability
- The docking results are biased by the use of a grid covering the experimentally suggested binding region, and the impact of this bias is not assessed
- The study does not provide any experimental validation of the predicted binding modes or their functional consequences