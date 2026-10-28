## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion)
- **Assessment boundary** Scientific validity, methodological rigor, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors propose that carbenicillin, identified through virtual screening of 145 FDA-approved antibiotics, binds to and inhibits the biofilm regulator CsgD in Salmonella Typhimurium, thereby suppressing biofilm formation at concentrations below its antibacterial MIC. This claim is supported by molecular docking, 100 ns molecular dynamics simulations, and phenotypic assays including crystal violet biofilm quantification, SEM, and Congo red agar analysis.
- **Visible evidence base** Molecular docking results (Table 1, Figures 1-3), MD simulation analyses (Figure 4a-e), MIC/MBC values, MBIC/MBEC values (Figures 5-6), light microscopy and SEM images (Figures 7-8), Congo red agar results (Figure 9)
- **Missing materials affecting confidence** No supplementary data files, no raw docking scores for all 145 compounds, no statistical output details beyond p-values, no negative control data for docking validation, no replicate information for phenotypic assays, no data on carbenicillin stability or degradation during assays, no information on whether the clinical isolate was genotypically confirmed as S. Typhimurium

## Reviewer
- **Overall assessment** The manuscript presents a potentially interesting application of drug repurposing to target a biofilm regulator, but the evidence provided does not adequately establish the central claim that carbenicillin acts as a specific CsgD inhibitor. The computational results are descriptive rather than validated, and the experimental data do not distinguish between general antibacterial effects and specific anti-biofilm mechanisms. The study would benefit from direct binding assays, genetic complementation experiments, and more rigorous statistical reporting.
- **Who would be interested in the results, and why** Researchers working on anti-biofilm strategies, drug repurposing for infectious diseases, and Salmonella pathogenesis would find the concept relevant. The potential to repurpose an existing antibiotic for anti-biofilm applications at sub-MIC concentrations could interest clinicians managing chronic or device-associated infections. However, the current evidence level is preliminary and would primarily appeal to those interested in computational screening approaches followed by phenotypic validation.
- **Major strengths** The study addresses a clinically relevant problem (biofilm-associated Salmonella infections) with a rational drug repurposing approach. The combination of computational screening and experimental validation is commendable. The use of multiple complementary assays (crystal violet, SEM, Congo red) to assess biofilm inhibition strengthens the phenotypic evidence. The comparison of MBIC/MBEC with MIC/MBC provides useful context for interpreting concentration-dependent effects.
- **Major Concerns** 
- **Minor Comments**
- **Technical failings that need to be addressed before the case is established** The absence of direct binding evidence for carbenicillin-CsgD interaction, lack of genetic controls (e.g., csgD mutant complementation), and insufficient distinction between bactericidal and specific anti-biofilm mechanisms are critical gaps. The docking methodology lacks validation through redocking or cross-validation with known inhibitors.
- **Assessment against Nature-style criteria** Originality: moderate, as drug repurposing for anti-biofilm applications is an active field, though targeting CsgD specifically is relatively novel. Scientific importance: limited at present, as the mechanistic claim is not fully established and clinical relevance is not demonstrated. Interdisciplinary readership: the work bridges computational chemistry, microbiology, and infectious disease, but the depth in each area is insufficient to attract specialists. Technical soundness: computational methods are standard but not rigorously validated; experimental methods are appropriate but lack key controls. Readability for nonspecialists: the manuscript is generally clear, though some methodological details are presented without sufficient context for non-experts.
- **Recommendation posture** Currently not established from the provided evidence. The central claim of specific CsgD inhibition by carbenicillin requires direct binding evidence and genetic validation. The manuscript has potential but needs substantial additional work.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim
- **Claim pointer** The manuscript claims that carbenicillin inhibits biofilm formation by targeting the CsgD protein, implying a specific molecular interaction.
- **Evidence pointer** Molecular docking section, MD simulation section, Discussion
- **Concern** The central mechanistic claim that carbenicillin specifically inhibits CsgD is not supported by direct binding evidence. Molecular docking predictions are computational hypotheses, not experimental proof of interaction. The MD simulations show stability of a predicted complex but do not demonstrate that this interaction occurs in solution or in cells. No surface plasmon resonance, isothermal titration calorimetry, pull-down assays, or other biophysical binding experiments are presented. Furthermore, no genetic experiments (e.g., csgD overexpression or deletion strains) are used to demonstrate that the anti-biofilm effect is mediated through CsgD rather than through other mechanisms.
- **Why it matters** The title and central conclusion rest on the claim that carbenicillin is a CsgD inhibitor. Without direct evidence of binding and functional relevance, the study only demonstrates that carbenicillin reduces biofilm formation, which could occur through many mechanisms including general stress responses, membrane disruption, or off-target effects. The specific mechanistic claim is therefore unsubstantiated.
- **Resolution test** Provide direct binding data (e.g., SPR, ITC, or NMR) showing carbenicillin binds to CsgD with measurable affinity. Alternatively, demonstrate that the anti-biofilm effect is abolished or reduced in a csgD deletion strain, or that overexpression of csgD rescues biofilm formation in the presence of carbenicillin.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The manuscript claims that carbenicillin suppresses biofilm formation at concentrations (MBIC 1 μg/mL) below those required to inhibit planktonic growth (MIC 8 μg/mL), suggesting specific anti-biofilm activity.
- **Evidence pointer** Results section, MIC/MBC and MBIC/MBEC determinations
- **Concern** The interpretation that lower MBIC relative to MIC indicates specific anti-biofilm activity is confounded by the fact that carbenicillin is a beta-lactam antibiotic that kills growing cells. Biofilm assays were conducted in LB without NaCl, while MIC was determined in Mueller-Hinton broth. Different media, inoculum sizes, and growth conditions between assays make direct comparisons of concentration thresholds unreliable. Additionally, the MBIC definition used (biofilm biomass statistically indistinguishable from negative control) is unconventional and may not reflect true inhibition of viability. The MBEC assay measures viable cell counts, but the manuscript does not report whether the observed reductions correlate with CsgD inhibition or simply with general cell death.
- **Why it matters** The claim of specific anti-biofilm activity at sub-MIC concentrations is a key finding that distinguishes this study from simple antibacterial effects. If this comparison is methodologically flawed, the conclusion that carbenicillin acts through a CsgD-specific mechanism is weakened.
- **Resolution test** Perform MIC and MBIC/MBEC assays under identical media and growth conditions. Include a control antibiotic with no known CsgD interaction to demonstrate that the observed MBIC/MIC ratio is specific to carbenicillin. Report viable cell counts for MBIC determinations rather than relying solely on biomass staining.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational validation
- **Claim pointer** The manuscript claims that molecular docking identified carbenicillin as a top candidate with high binding affinity to CsgD, and that MD simulations confirmed complex stability.
- **Evidence pointer** Molecular docking section, MD simulation section, Table 1, Figure 4
- **Concern** The docking methodology lacks critical validation steps. No redocking of the co-crystallized ligand (if present in PDB 5XP0) is reported to validate the docking protocol. No comparison with known CsgD inhibitors or substrates is provided to benchmark the screening approach. The selection of the "active site" is not justified with reference to functional residues or known binding pockets. The MD simulation parameters are incompletely described, and the CHARMM27 force field is outdated for protein-ligand simulations. The RMSD and RMSF values are reported as averages without error estimates or replicate simulations. No binding free energy calculations (e.g., MM-PBSA) are presented to support the claim of stable binding.
- **Why it matters** The computational pipeline is the foundation for selecting carbenicillin as the lead candidate. If the docking and MD methods are not validated, the identification of carbenicillin as a specific CsgD binder is not reliable, and the subsequent experimental work may be based on a false premise.
- **Resolution test** Validate the docking protocol by redocking a known ligand and reproducing its binding pose. Provide justification for the active site selection. Run at least three independent MD replicates and report mean and standard deviation for RMSD, RMSF, and Rg. Include MM-PBSA or similar binding free energy calculations to support the stability claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Strain characterization
- **Claim pointer** The manuscript states that a clinical isolate sourced from the Microbiology Department of Iran University of Medical Sciences was used alongside ATCC 14028.
- **Evidence pointer** Bacterial Strain and Growth Conditions section
- **Concern** The clinical isolate is not characterized beyond being described as a strong biofilm producer. No information is provided on how the species was confirmed, whether it was serotyped, what its antibiotic susceptibility profile is, or how it was determined to be a strong biofilm producer. The reference to a previous study (Narimisa et al. 2024a) is not sufficient for readers to evaluate the isolate's relevance or comparability to the ATCC strain.
- **Why it matters** The use of a clinical isolate is intended to increase the clinical relevance of the findings. Without proper characterization, readers cannot assess whether the isolate is representative of clinically relevant S. Typhimurium strains or whether the observed effects are strain-specific.
- **Resolution test** Provide species confirmation data (e.g., 16S rRNA sequencing, serotyping), antibiotic susceptibility profile, and quantitative biofilm formation data for the clinical isolate compared to ATCC 14028.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Concentration-response relationship
- **Claim pointer** The manuscript claims that SEM analysis showed morphological changes and disrupted biofilm architecture at 0.5-1 μg/mL carbenicillin, and that Congo red assays demonstrated dose-dependent suppression of curli production.
- **Evidence pointer** SEM Analysis section, Congo Red Assay section, Figures 8-9
- **Concern** The manuscript does not report quantitative data for the SEM observations. The claim of "morphological changes" and "disrupted biofilm architecture" is based on visual inspection without image analysis or quantification. Similarly, the Congo red assay results are described qualitatively, with no quantitative measurement of dye binding or curli production. The dose-dependence claim is not supported by statistical analysis or a clear dose-response curve.
- **Why it matters** Qualitative descriptions of microscopy and plate assays are insufficient to support quantitative claims about the extent of biofilm inhibition or the dose-dependence of the effect. Without quantification, the results cannot be compared across conditions or reproduced by other laboratories.
- **Resolution test** Provide quantitative image analysis for SEM (e.g., biofilm coverage, cell length measurements) and quantitative Congo red binding data (e.g., dye extraction and absorbance measurement) across multiple carbenicillin concentrations with statistical analysis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Statistical Analysis section
- **Evidence pointer** Statistical Analysis section
- **Issue** The statistical methods section states that one-way ANOVA with Tukey's post-hoc test was used, but the results section does not report F-statistics, degrees of freedom, or effect sizes. The number of replicates for each experiment is not stated.
- **Required correction** Report full statistical details including F-values, degrees of freedom, and exact p-values. State the number of biological and technical replicates for each assay.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability Statement
- **Evidence pointer** Data Availability Statement
- **Issue** The data availability statement says "The authors have nothing to report," which is inconsistent with a study that generated docking scores, MD trajectories, and experimental data. This statement is ambiguous and does not comply with common data sharing expectations.
- **Required correction** Provide a clear statement on where the data can be accessed, or explicitly state that all relevant data are included in the manuscript and supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion cites several references in a manner that suggests direct comparison with the current findings, but the cited studies used different methodologies (e.g., csgD knockout mutants) that are not directly comparable to pharmacological inhibition. The logical connection between these references and the current study is not clearly articulated.
- **Required correction** Clarify how the cited studies support the interpretation of the current results, and acknowledge the methodological differences that limit direct comparability.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 7-8
- **Evidence pointer** Light Microscopy and SEM Observations section
- **Issue** The manuscript does not describe the magnification or scale bars for the light microscopy and SEM images. Without scale bars, readers cannot assess the size of the observed structures or the extent of the morphological changes.
- **Required correction** Add scale bars to all microscopy images and include magnification information in the figure legends.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "inhibitor" is used throughout to describe carbenicillin's effect on CsgD, but the study does not demonstrate inhibition of CsgD function directly. The term "potential inhibitor" or "putative inhibitor" would be more accurate given the evidence presented.
- **Required correction** Revise the language to reflect the preliminary nature of the evidence, using terms such as "potential inhibitor" or "candidate inhibitor" until direct functional inhibition is demonstrated.

## Risk / unsupported claims
- The claim that carbenicillin is a specific inhibitor of CsgD is unsupported by direct binding or functional evidence.
- The claim that MBIC values lower than MIC indicate specific anti-biofilm activity is confounded by methodological differences between assays.
- The claim that MD simulations "confirmed" complex stability is overstated, as no binding free energy calculations or replicate simulations are reported.
- The claim that carbenicillin suppresses curli production is based on qualitative Congo red observations without quantitative measurement.
- The claim that SEM shows "bacterial cell destruction" at 1 μg/mL is not supported by quantitative data or viability staining.
- The clinical relevance of the findings is asserted without in vivo data or demonstration of therapeutic potential.
- The statement that carbenicillin "acts as a potent CsgD inhibitor" in the Discussion is not supported by the experimental evidence presented.