## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence. No assessment of formatting, grammar, or stylistic issues beyond those affecting scientific clarity.
- **Shared manuscript claim summary** The authors claim that Cu(II) coordination modulates the structural, electronic, and DNA-binding properties of doxorubicin (DOX), leading to a tenfold increase in apparent DNA-binding affinity, as established through integrated DFT, docking, MD simulations, UV-Vis, and fluorescence spectroscopy.
- **Visible evidence base** Abstract; Sections 1-4; Figures 1, 2, 5, 6 (referenced); Tables 1, 2 (referenced); Supplementary Figures S1-S4, S6, S8-S10 (referenced); Equations 2.1-2.6; Supplementary Table S2, S3 (referenced)
- **Missing materials affecting confidence** Figures 1, 2, 5, 6, 7, 8, 10 and Tables 1, 2 are referenced but not provided in the submitted text. Supplementary figures and tables are referenced but not provided. No raw data, computational output files, or experimental spectra are included. No information on error bars, replicates, or statistical treatment of experimental data is provided.

## Reviewer

- **Overall assessment** This manuscript presents a potentially interesting hypothesis regarding the role of Cu(II) coordination in modulating DOX-DNA binding, combining computational predictions with spectroscopic validation. The integration of multiple techniques is commendable. However, the manuscript in its current form has several significant weaknesses that prevent the claims from being fully established. The most critical issues are: (1) the absence of the actual figures and tables, making it impossible to evaluate the quality of the data; (2) a mismatch between the reported binding constants in the abstract/conclusion and the results section; (3) the use of a semi-empirical method (PM6) for the Cu complex without adequate justification or validation; (4) the lack of a direct computational model of the Cu-DOX-DNA ternary complex; and (5) the absence of any discussion of the potential biological relevance or limitations of the findings. The core hypothesis is interesting and the work could be of interest to the community, but the evidence as presented is insufficient to support the strong claims made.

- **Who would be interested in the results, and why** Researchers in the fields of bioinorganic chemistry, anticancer drug design, and DNA-ligand interactions would find this work relevant. The concept of using metal coordination to modulate the DNA-binding properties of established anthracycline drugs is of potential interest to those seeking to improve the therapeutic index of DOX or develop new metal-based anticancer agents. The combined computational-experimental approach may also appeal to methodologists in computational chemistry and biophysics.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality and availability
  - **Claim pointer** The manuscript claims that "UV-Vis analysis indicating a substantial tenfold increase in apparent DNA-binding affinity" and that "the experimentally determined binding constant increased from approximately 2.059 × 10⁴ M⁻¹ for DOX-DNA to 20.561 × 10⁴ M⁻¹ for DOX-Cu(II)-DNA."
  - **Evidence pointer** Section 3.5, Figure 10, Figure S5, Figure S7
  - **Concern** The actual figures (Figure 10A, 10B) and supplementary figures (S5, S7) containing the UV-Vis titration data and the double-reciprocal plots are not provided in the submitted manuscript. Without these data, it is impossible to assess the quality of the spectroscopic measurements, the validity of the fitting procedure, or the accuracy of the reported binding constants. Furthermore, the binding constant for DOX-DNA is reported as 2.059 x 10⁴ M⁻¹ in Section 3.5, but the abstract and conclusion state a value of 2.059 × 10⁴ M⁻¹, which is consistent. However, the tenfold increase claim relies entirely on the unprovided Figure S7. The quality of the fit, the number of data points, and the reproducibility of the measurements cannot be evaluated.
  - **Why it matters** The central quantitative claim of the manuscript, the tenfold increase in binding affinity, is entirely dependent on data that are not available for review. Without access to the primary data, the claim cannot be verified, and the manuscript's main conclusion is unsupported.
  - **Resolution test** Provide the actual UV-Vis titration spectra, the double-reciprocal plots with the linear regression fits, and the raw data points. Include information on the number of replicates and the standard deviation of the calculated binding constants.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological rigor
  - **Claim pointer** The manuscript claims that "DFT-based characterization of Cu(II)-DOX revealed coordination-induced structural and electronic changes consistent with reduced conformational freedom and increased rigidity."
  - **Evidence pointer** Section 2.1, Section 3.4, Figures 7, 8, 9, Tables 1, 2, Supplementary Figures S2, S3
  - **Concern** The Cu-DOX complex was optimized using a two-layer ONIOM approach, with the inner region (Cu and coordinating oxygens) treated at the B3LYP/LANL2DZ level and the rest at the semi-empirical PM6 level. This is a significant methodological limitation. PM6 is not generally reliable for describing the electronic structure of organic molecules, particularly for properties such as vibrational frequencies and electronic transitions. The use of a small basis set (LANL2DZ) for the metal center is also a concern. The manuscript does not provide any validation of this approach, such as a comparison of the ONIOM-optimized geometry with a full DFT optimization of a model system, or a benchmark of the calculated IR/Raman spectra against experimental data. The claims about "reduced conformational freedom" and "increased rigidity" are based on this potentially unreliable computational model. Furthermore, the NCI and MESP analyses are performed on this ONIOM-optimized structure, and their interpretation is therefore subject to the same limitations.
  - **Why it matters** The computational results form the foundation of the hypothesis that Cu(II) coordination pre-organizes DOX for intercalation. If the computational method is not reliable, the structural and electronic conclusions drawn from it are questionable, and the subsequent interpretation of the experimental data becomes speculative.
  - **Resolution test** Provide a validation of the ONIOM approach. This could include a comparison of the ONIOM-optimized Cu-DOX structure with a full DFT optimization (e.g., using a more appropriate functional and basis set, such as B3LYP/def2-TZVP with a suitable effective core potential for Cu) on a truncated model. Alternatively, provide experimental evidence (e.g., from IR or Raman spectroscopy of the Cu-DOX complex) that supports the calculated vibrational frequencies.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Logical consistency and claim support
  - **Claim pointer** The manuscript claims that "Cu(II) coordination may favor an intercalation-compatible configuration of DOX" and that the experimental results support a "coherent relationship between Cu(II) coordination, DOX conformational modulation, and DNA recognition."
  - **Evidence pointer** Section 3.4, Section 3.5, Section 3.6, Section 4
  - **Concern** The manuscript does not provide a direct computational model of the Cu-DOX-DNA ternary complex. The docking and MD simulations were performed only for DOX with DNA. The DFT calculations were performed only for DOX and the Cu-DOX complex. The hypothesis that Cu(II) coordination enhances DNA binding is inferred from the separate results of these calculations. However, the manuscript does not demonstrate that the Cu-DOX complex can actually bind to DNA in an intercalative mode. The Cu(II) center, with its square-planar coordination geometry, could potentially interfere with the intercalation process or interact with the DNA in a different manner. The experimental data (UV-Vis and fluorescence) are consistent with enhanced binding, but they do not provide direct evidence for the proposed mechanism. The tenfold increase in binding constant could be due to other factors, such as electrostatic interactions between the cationic Cu(II) complex and the anionic DNA backbone, rather than enhanced intercalation.
  - **Why it matters** The manuscript's central narrative is that Cu(II) coordination modulates DOX's conformation to favor intercalation. Without a model of the ternary complex, this mechanism remains a hypothesis. The experimental data alone cannot distinguish between enhanced intercalation and other binding modes.
  - **Resolution test** Perform and report docking and/or MD simulations of the Cu-DOX complex with the DNA hexamer. This would directly test whether the Cu-DOX complex can adopt an intercalative binding mode and would provide insights into the role of the Cu(II) center in the binding process.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Experimental design and interpretation
  - **Claim pointer** The manuscript claims that "fluorescence measurements confirming pronounced perturbation of DNA-associated ethidium bromide" and that the Cu(II)-DOX system "more effectively perturbed the pre-existing EB-DNA equilibrium than DOX alone."
  - **Evidence pointer** Section 3.6, Figure 11, Figures S8-S10
  - **Concern** The fluorescence experiments are performed with a fixed EB-DNA ratio of 1:4 and a fixed EB-DNA-Cu(II) ratio of 1:4:0.4. The Cu(II) is added to the EB-DNA complex before the DOX titration. This experimental design introduces a significant ambiguity. Cu(II) ions are known to interact with DNA directly, potentially competing with EB for binding sites or altering the DNA structure. The observed changes in EB fluorescence upon addition of DOX to the Cu(II)-containing system could be influenced by the pre-existing Cu(II)-DNA interactions, rather than being solely due to the Cu-DOX complex. The manuscript does not include control experiments, such as the effect of Cu(II) alone on the EB-DNA fluorescence, or the effect of DOX on EB-DNA in the presence of a non-binding metal ion. Without these controls, the interpretation of the fluorescence data is not unique.
  - **Why it matters** The fluorescence data are used to support the claim that Cu-DOX has a stronger effect on DNA binding than DOX alone. If the observed effects are partly due to Cu(II)-DNA interactions, the conclusions about the enhanced binding of the Cu-DOX complex are weakened.
  - **Resolution test** Include control experiments: (1) Titrate the EB-DNA complex with Cu(II) alone to assess its effect on EB fluorescence. (2) Titrate the EB-DNA complex with DOX in the presence of a fixed concentration of a metal ion that does not coordinate to DOX (e.g., Zn(II) or Mg(II)) to control for ionic strength effects. (3) Perform the DOX titration on the EB-DNA-Cu(II) system and compare the results with the controls to isolate the effect of the Cu-DOX complex.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and consistency
  - **Affected element** Abstract and Conclusion
  - **Evidence pointer** Abstract, Section 4
  - **Issue** The abstract states "a substantial tenfold increase in apparent DNA-binding affinity," while the conclusion states "the experimentally determined binding constant increased from approximately 2.059 × 10⁴ M⁻¹ for DOX-DNA to 20.561 × 10⁴ M⁻¹ for DOX-Cu(II)-DNA, corresponding to an approximately ten fold increase." The abstract uses "tenfold" and the conclusion uses "ten fold." This is a minor inconsistency in style. More importantly, the abstract claims a "tenfold increase" without mentioning the absolute values, which could be misleading without the context of the initial binding constant.
  - **Required correction** Standardize the use of "tenfold" throughout the manuscript. In the abstract, consider adding the absolute values of the binding constants for clarity.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** Section 2.1
  - **Evidence pointer** Section 2.1
  - **Issue** The manuscript states that the DNA structure was obtained from PDB ID 1Z3F and that it contains an "intercalation gap." It is not clear if this structure is a DNA hexamer with a pre-formed gap or if the gap was created during the docking preparation. The details of the docking grid box are provided, but the specific preparation of the DNA receptor (e.g., how the gap was generated, if applicable) is not described.
  - **Required correction** Clarify the nature of the "intercalation gap" in the PDB structure and describe the steps taken to prepare the DNA receptor for docking.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Section 3.5, Section 3.6
  - **Evidence pointer** Section 3.5, Section 3.6
  - **Issue** The manuscript reports binding constants and other parameters (e.g., K, K_a, K_H, n, n_H, IC50) but does not provide the standard errors or confidence intervals for these values. The text mentions that the regression coefficient r² was between 0.9 and 1.0, but this is not a substitute for error estimates on the fitted parameters.
  - **Required correction** Provide the standard errors or confidence intervals for all reported binding constants and fitted parameters.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 3.4
  - **Evidence pointer** Section 3.4
  - **Issue** The manuscript states that the Cu-DOX complex has a "distorted square-planar coordination geometry" but does not provide the specific bond lengths and angles around the Cu(II) center. This information is crucial for understanding the coordination environment and for validating the computational model.
  - **Required correction** Report the key geometric parameters (bond lengths, bond angles) of the optimized Cu-DOX complex, potentially in a table or in the text.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Section 1, Section 3.5
  - **Evidence pointer** Section 1, Section 3.5
  - **Issue** The introduction mentions that Cu(II) complexes of DOX have been studied, but the discussion of previous work is brief. The manuscript would benefit from a more detailed comparison of the present findings with previously reported binding constants for DOX-DNA and Cu-DOX-DNA systems, if available.
  - **Required correction** Expand the discussion to include a comparison with relevant literature values for DOX-DNA and metal-DOX-DNA binding constants.

## Risk / unsupported claims
- The claim of a "tenfold increase in apparent DNA-binding affinity" is unsupported in the provided text because the primary UV-Vis data (Figure 10, Figure S5, Figure S7) are not available for review.
- The claim that Cu(II) coordination leads to "reduced conformational freedom and increased rigidity" is based on an unvalidated ONIOM (B3LYP/LANL2DZ:PM6) computational model and is therefore not fully supported.
- The claim that the Cu-DOX complex binds to DNA in an intercalative mode is not supported by any direct computational or experimental evidence presented in the text. The experimental data are consistent with enhanced binding but do not establish the binding mode.
- The interpretation of the fluorescence competition experiments is ambiguous due to the lack of control experiments for the effect of Cu(II) alone on the EB-DNA system.
- The manuscript's conclusion that the findings "provide a mechanistic perspective" on how Cu(II) regulates DOX-DNA interaction is overstated, as the mechanism is inferred rather than directly demonstrated.