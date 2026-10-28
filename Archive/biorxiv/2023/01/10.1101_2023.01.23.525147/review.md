## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, supplementary data references)
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the supplied text; no external data or unpublished materials consulted
- **Shared manuscript claim summary** The authors present a new crystal structure of the JBP1 J-DNA binding domain (JDBD) with a previously disordered loop resolved, use molecular dynamics simulations and docking to model JDBD:J-DNA interactions, identify and experimentally validate two new residues (Arg448, Asn455) involved in DNA binding, and propose that the N-terminal region of JBP1 contributes to DNA binding based on AlphaFold modeling and truncation experiments
- **Visible evidence base** Crystal structure (PDB 8BBM), MD simulation trajectories, HADDOCK docking models, SAXS fitting, HDX-MS data (from prior work), fluorescence polarization binding assays, nanoDSF thermal stability measurements, AlphaFold predictions, sequence alignments
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S11, S2, S3, S4, S5) referenced but not provided; full experimental details for mutagenesis and binding assays only partially described; no raw data or statistical analysis details for binding affinities; no electron density map figures for the new loop; no validation metrics for the final full-length JBP1 model

## Reviewer
- **Overall assessment** This manuscript presents a structurally grounded computational and experimental study of JBP1:J-DNA recognition. The new crystal structure resolving the previously disordered loop is a valuable contribution, and the identification of Arg448 and Asn455 as functionally important residues is supported by mutagenesis and binding data. However, the central claim that the N-terminus contributes to DNA binding rests on relatively modest affinity differences and a modeling approach that the authors themselves acknowledge does not yield a satisfactory full-length complex. The study is technically competent but incremental, and the broader mechanistic conclusions remain speculative without a high-resolution complex structure.
- **Who would be interested in the results, and why** Researchers studying DNA modification and epigenetic regulation in kinetoplastids, structural biologists interested in protein-DNA recognition, and computational biologists using MD/docking approaches to model protein-nucleic acid complexes. The TET-JBP family connection may also attract interest from the epitranscriptomics community.
- **Major strengths** 1) New crystal structure with resolved loop provides improved template for modeling; 2) Integration of multiple computational and experimental methods is thorough; 3) Identification of novel residues via structure-guided approach is well executed; 4) AlphaFold analysis adds contemporary relevance; 5) Clear writing and logical flow
- **Major Concerns** See detailed items below
- **Minor Comments** See detailed items below
- **Technical failings that need to be addressed before the case is established** R1-M1 (N-terminal contribution claim), R1-M2 (docking model validation), R1-M3 (full-length model construction)
- **Assessment against Nature-style criteria** **Originality**: Moderate. The new crystal structure is original but represents an incremental improvement over the existing 2XSE structure. The identification of two new binding residues is a useful but not transformative advance. **Scientific importance**: Moderate. The study advances understanding of JBP1:J-DNA recognition but does not resolve the fundamental mechanistic question of how THD and JDBD cooperate during replication. **Interdisciplinary readership**: Limited. The work will primarily interest specialists in kinetoplastid biology and protein-DNA interactions. **Technical soundness**: Generally sound for the individual methods employed, but the integration of results into a coherent model is not fully validated. **Readability for nonspecialists**: Acceptable, though some sections assume familiarity with structural biology and MD methods.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the strength of the N-terminal contribution claim and validation of the docking models

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim strength vs. evidence
- **Claim pointer** "The N-terminal region of JBP1 contributes to DNA binding" and "the flexible JBP1 N-terminus contributes to DNA-binding, which we confirmed experimentally"
- **Evidence pointer** Results section "New insights through AI-based modeling of JBP1", Figure 7E, Supplemental Table S5
- **Concern** The experimental evidence for N-terminal involvement in DNA binding consists of affinity measurements showing wt-JBP1 binds J-DNA at 6.4 nM, Δ23-JBP1 at 20.8 nM, and Δ38-JBP1 at 31.2 nM. While these differences are in the expected direction, the authors do not report statistical significance, replicate numbers, or error estimates. The difference between Δ23 and Δ38 (20.8 vs 31.2 nM) is not discussed, and the claim that the N-terminus "contributes" to binding is not quantitatively supported. Furthermore, the derived free energy differences are small (3 kJ/mol or less), which the authors acknowledge but do not contextualize. The modeling shown in Figure 7F is illustrative rather than validated, and the authors state that "several modelling attempts did not yield a model that fits with the SAXS data," undermining confidence in the proposed wrapping model.
- **Why it matters** The N-terminal contribution is a central novel claim of the manuscript. If the affinity differences are not statistically robust or are within experimental variability, the claim is not established. The small free energy differences may not be biologically meaningful, and the proposed structural model is not supported by experimental validation.
- **Resolution test** Provide replicate numbers, statistical analysis (e.g., t-tests or ANOVA) for binding affinities, and error bars in Figure 7E. Discuss whether the Δ23 vs Δ38 difference is significant and what it implies for the contribution of residues 24-38. If possible, perform competition or truncation experiments that more directly test the N-terminal DNA-binding role, or provide a validated structural model showing N-terminal-DNA contacts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** "These models guided mutagenesis experiments, providing additional data for docking, which reveals a binding mode for JDBD onto J-DNA"
- **Evidence pointer** Results section "Computational modeling provides new insight into JDBD mediated J-DNA recognition", Figures 3-5, Supplemental Figures S4-S7
- **Concern** The docking models are validated primarily by comparison to SAXS data and HDX-MS data, but the χ² values for SAXS fitting are only mentioned qualitatively ("fit well") without numerical values. The HDX-MS comparison is described but not shown quantitatively. The authors state that Arg448 and Asn455 were added as "additional active residues" in a second round of docking, but it is unclear whether this was done in a blinded manner or whether the experimental results were used to refine the model in a circular fashion. The final model shows Arg532 forming hydrogen bonds with J+2' position, but the authors note that in the initial models the distances were too long (≥2.5 Å) for direct hydrogen bonds, raising questions about the reliability of the refined model.
- **Why it matters** The docking models are the foundation for the proposed binding mode and for the identification of new residues. If the models are not rigorously validated, the subsequent experimental work is not well motivated, and the proposed binding mode may be incorrect.
- **Resolution test** Provide numerical χ² values for SAXS fitting for all models. Show quantitative comparison of HDX-MS data to the models (e.g., protection factors mapped onto the structure). Clarify the docking protocol: were the second-round docking runs performed with the same restraints, and were the experimental results used to select or refine the model? If possible, validate the final model with independent experimental data (e.g., cross-linking, mutagenesis of predicted contact residues).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model construction and interpretation
- **Claim pointer** "The AlphaFold model, in combination with the X-ray structure model of TET2 in complex with DNA and our JDBD:J-DNA docking model, did now allow to construct a reliable model structure for full length JBP1 bound to J-DNA"
- **Evidence pointer** Results section "New insights through AI-based modeling of JBP1", Figure 6, Supplemental Figure S11
- **Concern** The authors state that they attempted to construct a full-length JBP1:J-DNA model but that "several modelling attempts did not yield a model that fits with the SAXS data." Despite this, they propose a model in which the N-terminus wraps around DNA and the THD and JDBD bind simultaneously with DNA bending. This model is presented in Figure 7F as an illustration, but it is not validated by any experimental data. The claim that a "reliable model structure" was obtained is contradicted by the authors' own statement that the modeling attempts failed to fit SAXS data. The PAE analysis and pLDDT scores are used to infer N-terminal proximity to JDBD, but these are predictions, not experimental evidence.
- **Why it matters** The full-length model is used to support the central mechanistic claim about how JBP1 recognizes J-DNA and positions the THD for hydroxylation. If the model is not reliable, the proposed mechanism remains speculative, and the conclusions overreach the data.
- **Resolution test** Either provide a validated full-length model that fits experimental data (SAXS, cross-linking, etc.) or temper the conclusions to clearly state that the full-length model is hypothetical. If the modeling attempts failed, explain why and what alternative models are consistent with the data. Consider whether the N-terminal contribution could be tested more directly (e.g., by NMR or cross-linking).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Binding affinity measurements
- **Evidence pointer** Results section "New insights through AI-based modeling of JBP1", Figure 7E, Supplemental Table S5
- **Issue** The binding affinities are reported as single values without error estimates or replicate numbers. The authors state that wt-JBP1 binds at 6.4 nM, Δ23 at 20.8 nM, and Δ38 at 31.2 nM, but it is unclear how many independent measurements were performed and what the variability is.
- **Required correction** Report mean ± SD or SEM with the number of replicates for each measurement. If the assays were performed in duplicate or triplicate, state this explicitly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** MD simulation analysis
- **Evidence pointer** Methods section "Molecular dynamics simulations of JDBD"
- **Issue** The clustering method is described as using Daura's algorithm with a 2.25 Å RMSD cutoff, but the number of clusters generated and the population of each cluster are not reported in the main text. The authors state that "the three most occupied clusters" were used, but it is unclear what fraction of the total conformations these represent for each simulation.
- **Required correction** Report the number of clusters, the population of each cluster, and the fraction of total conformations represented by the selected clusters. This information is important for assessing whether the selected structures are representative.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 3C
- **Evidence pointer** Results section "Computational modeling provides new insight into JDBD mediated J-DNA recognition"
- **Issue** The text refers to "Figure 33C" which appears to be a typo for Figure 3C. The figure is described as showing different orientations of the α1 helix, but the figure itself is not provided in the manuscript text.
- **Required correction** Correct the typo and ensure the figure clearly shows the differences in α1 helix orientation across clusters. Consider adding a supplementary figure with a quantitative comparison of the orientations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and conclusions
- **Evidence pointer** Abstract, Conclusions
- **Issue** The abstract states that the N-terminus "contributes" to DNA binding, but the conclusions state that the N-terminus "is involved in DNA binding." These are slightly different claims, and the latter is stronger. The authors should be consistent in their language and ensure the conclusions match the strength of the evidence.
- **Required correction** Use consistent terminology throughout. If the evidence supports only a modest contribution, avoid stronger language in the conclusions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction mentions that JBP1 has a thymidine hydroxylase domain and a J-DNA binding domain, but does not discuss the structural basis of the THD in detail or compare it to other TET family members beyond citing the TET-JBP family relationship.
- **Required correction** Consider adding a brief discussion of the THD structure and how it relates to the JBP1 function, particularly in the context of the proposed model where the THD must hydroxylate a thymidine 13 bp downstream.

## Risk / unsupported claims
- The claim that the N-terminus of JBP1 contributes to DNA binding is supported by affinity differences that lack statistical analysis and may be within experimental variability
- The proposed model of full-length JBP1 bound to J-DNA with N-terminal wrapping and DNA bending is not validated by experimental data and is contradicted by the authors' own statement that modeling attempts did not fit SAXS data
- The statement that a "reliable model structure" for full-length JBP1 was obtained is not supported by the evidence presented
- The functional significance of the newly identified residues Arg448 and Asn455 is inferred from binding assays but not tested in a functional context (e.g., in vivo or in a full-length protein activity assay)
- The claim that the docking models are validated by HDX-MS data is not quantitatively supported in the text
- The biological relevance of the proposed JBP1:J-DNA binding mode for the replication of epigenetic information is speculative and not directly tested