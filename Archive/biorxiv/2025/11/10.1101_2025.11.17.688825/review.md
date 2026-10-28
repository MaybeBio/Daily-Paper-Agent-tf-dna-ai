## Review setup
- **Input scope** Full manuscript text, abstract, methods, and supplementary figure legends as provided
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided material
- **Shared manuscript claim summary** The authors describe the design, synthesis, and characterization of molecular glue-based PROTACs (MG PROTACs) that recruit VHL E3 ligase to the 14-3-3/ERα complex, enabling ubiquitination of the partially disordered ERα protein. They report linker-dependent cooperativity, a cryo-EM structure revealing a de novo VHL-14-3-3 interface, and selective ubiquitination of complex subunits.
- **Visible evidence base** Fluorescence anisotropy binding assays, cellular VHL engagement assays, mass photometry, cryo-EM (4.3 Å locally refined), molecular dynamics simulations, in vitro ubiquitination assays, mass spectrometry-based ubiquitination site mapping
- **Missing materials affecting confidence** Full figures and figure legends, supplementary figures S1-S12, extended data figures 1-9, supplementary tables S1-S4, compound synthesis details and characterization data, exact numerical values for many reported measurements, statistical analysis details, cell-based degradation data

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting approach that merges molecular glue and PROTAC technologies to target a protein complex involving a partially disordered protein. The work is technically ambitious, combining medicinal chemistry, biophysics, structural biology, and biochemistry. However, the manuscript as provided has several significant gaps that prevent full evaluation. The most critical concern is the absence of demonstrated cellular degradation of ERα, which the authors acknowledge. The cryo-EM structure, while valuable, is at moderate resolution (4.3 Å) with substantial heterogeneity, and the molecular details of the cooperative interface rely heavily on MD simulations. The claim of "selective ubiquitination of distinct complex subunits" requires stronger quantitative support. The differential cellular permeability observations are interesting but not fully explained mechanistically. Overall, the work represents a useful proof-of-concept for MG PROTACs targeting protein complexes, but the current evidence does not fully establish the therapeutic potential implied by the framing.

- **Who would be interested in the results, and why** Researchers in targeted protein degradation (TPD), chemical biology, and drug discovery would be interested in this work as it expands the conceptual framework of PROTAC design to protein complexes and partially disordered proteins. The structural characterization of a ligand-induced VHL-14-3-3 interface is novel and could inform future designs. The demonstration that linker chemistry can direct ubiquitination site selectivity within a complex is conceptually important. The work may also interest structural biologists studying 14-3-3 complexes and medicinal chemists working on molecular glues.

- **Major strengths** The conceptual advance of combining molecular glue and PROTAC principles is timely and significant. The systematic linker optimization and the correlation between linker properties and cooperativity is well-executed. The cryo-EM structure revealing a de novo VHL-14-3-3 interface is a notable achievement. The use of multiple orthogonal biophysical and biochemical assays strengthens the conclusions. The identification of specific residues mediating the cooperative interface provides a structural rationale for the observed isoform selectivity.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claims vs evidence
- **Claim pointer** The abstract and introduction frame this as a strategy for targeted protein degradation, yet no cellular degradation of ERα is demonstrated.
- **Evidence pointer** Results section "CV2a-dependent VHL recruitment drives ubiquitination of the 14-3-3ζ/ERα (LBD_F) complex", Discussion
- **Concern** The authors state "we could not detect measurable degradation of ERα in ERα-positive MCF7 cells treated with CV2a" and pivot to studying ubiquitination in vitro. This is a fundamental gap between the stated goal (degradation) and the demonstrated outcome (in vitro ubiquitination). The title and abstract imply a degradation strategy, but the evidence supports only ubiquitination in a reconstituted system.
- **Why it matters** The therapeutic relevance of MG PROTACs depends on cellular degradation. Without demonstrating degradation or at least cellular ubiquitination of endogenous ERα, the significance of the approach for drug discovery is substantially weakened. The manuscript's framing overstates what is actually shown.
- **Resolution test** Provide cellular degradation data (e.g., western blot of ERα levels in MCF7 cells treated with MG PROTACs) or cellular ubiquitination assays demonstrating endogenous target modification. Alternatively, substantially revise the claims to accurately reflect that only in vitro ubiquitination is demonstrated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The cryo-EM structure at 4.3 Å resolution is used to support detailed molecular interactions, including specific hydrogen bonds and hydrophobic contacts.
- **Evidence pointer** Cryo-EM section, Extended Data Figs. 5-6, Tables S3-S4
- **Concern** At 4.3 Å resolution, the confidence in specific side-chain interactions and hydrogen bond assignments is limited. The manuscript reports "well-defined density" for ligands and specific interactions, but at this resolution, such claims require careful validation. The MD simulations are used to rationalize interactions, but the starting model quality directly impacts simulation reliability. The heterogeneity described (multiple poses) further complicates interpretation.
- **Why it matters** The structural model is central to the mechanistic claims about cooperativity and the de novo interface. If the structural interpretation is over-extended relative to the resolution, the mechanistic conclusions are correspondingly weakened.
- **Resolution test** Provide local resolution maps showing the quality of density at the interface regions. Clearly distinguish between residues modeled with high confidence versus those inferred from MD. Consider whether the claims about specific hydrogen bonds are supported at this resolution or should be presented as models.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Claims vs evidence
- **Claim pointer** "Fine-tuning linker design enables selective ubiquitination of distinct complex subunits" (abstract) and related statements in the results.
- **Evidence pointer** Results section "MG PROTAC design controls ubiquitination sites within the protein complex", Extended Data Fig. 9, Table S1
- **Concern** The claim of selective ubiquitination of distinct subunits is based on mass spectrometry identification of ubiquitination sites. However, the quantitative nature of this selectivity is not clear. The manuscript reports ubiquitination at specific lysines (Lys139, Lys158 of 14-3-3ζ; Lys467, Lys531 of ERα) but does not provide quantitative comparison across the MG PROTAC series. The peptide-level data with PSM > 10 threshold may not be sufficient to establish selectivity.
- **Why it matters** The claim of tunable subunit selectivity is a key differentiator of this approach. If the selectivity is not robustly quantified, this claim is overstated.
- **Resolution test** Provide quantitative comparison of ubiquitination site occupancy across different MG PROTACs, ideally with labeled ubiquitin and appropriate controls. Show that the observed selectivity is statistically significant and reproducible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The cellular permeability differences between PEG-linked and alkyl-linked MG PROTACs are attributed to linker properties.
- **Evidence pointer** Results section "MG PROTACs stabilize the 14-3-3/ERα PPI and engage VHL in vitro and in cellulo", Extended Data Fig. 1c
- **Concern** The differential permeability is observed in a BRET-based assay, but the mechanistic basis is not explored. The authors speculate about polarity effects but do not provide direct measurements of intracellular concentrations or permeability coefficients. The relationship between BRET signal and actual intracellular compound concentration is indirect.
- **Why it matters** Understanding permeability is critical for translating these compounds to cellular degradation studies. Without direct permeability measurements, the conclusions about linker effects on permeability remain speculative.
- **Resolution test** Measure intracellular compound concentrations (e.g., by LC-MS) or perform formal permeability assays (e.g., PAMPA or Caco-2) to support the claims about differential permeability.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The ubiquitination assays demonstrate "robust polyubiquitination" and the conclusions about E2 selectivity (UBE2D2 vs UBE2R1).
- **Evidence pointer** Results section "CV2a-dependent VHL recruitment drives ubiquitination of the 14-3-3ζ/ERα (LBD_F) complex", Extended Data Fig. 8
- **Concern** The ubiquitination assays use high concentrations of components (E1 at 2 μM, E2 at 5 μM, 14-3-3ζ/ERα at 12 μM, CRL2 VHL at 500 nM) that may not be physiologically relevant. The observation that UBE2D2 but not UBE2R1 supports ubiquitination is interesting but the mechanistic basis is not explored. The manuscript does not address whether the observed ubiquitination leads to proteasomal degradation in a cellular context.
- **Why it matters** The in vitro conditions may not reflect cellular conditions, and the lack of connection to degradation limits the translational relevance.
- **Resolution test** Perform ubiquitination assays at more physiologically relevant concentrations, and demonstrate that the ubiquitination observed in vitro translates to degradation in cells (e.g., using a reporter system or endogenous ERα).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "selective ubiquitination of distinct complex subunits" but the selectivity is not clearly demonstrated in the provided results.
- **Required correction** Either provide stronger evidence for selectivity or temper the claim in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Compound characterization
- **Evidence pointer** Methods, SI Scheme 1
- **Issue** The manuscript mentions partial cleavage of the 2-methylbut-3-en-2-yl ether moiety (5-43%) in the final products but does not explain how this heterogeneity affects the interpretation of the biophysical and biochemical data.
- **Required correction** Clarify whether the compounds were purified to homogeneity or tested as mixtures, and discuss the potential impact of this heterogeneity on the results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure legends
- **Evidence pointer** Figures 1-6, Extended Data Figures
- **Issue** The figure legends are not provided in the manuscript text, making it difficult to fully interpret the data presented.
- **Required correction** Ensure all figure legends are included and provide sufficient detail for interpretation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Statistical analysis
- **Evidence pointer** Various results sections
- **Issue** The manuscript does not consistently report statistical details (e.g., number of replicates, error bars, significance tests) for the quantitative measurements.
- **Required correction** Add statistical details for all quantitative data, including replicates and appropriate statistical tests.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of why cellular degradation was not observed is brief and speculative. The authors mention "limited characterized phosphorylation state of ERα at Thr594" and "fusicoccin is known to engage multiple 14-3-3 client protein complexes" but do not provide experimental evidence to support these explanations.
- **Required correction** Either provide experimental data supporting these explanations or present them more clearly as hypotheses requiring further testing.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** MD simulations
- **Evidence pointer** Methods, MD simulation section
- **Issue** The MD simulation details are limited. The force field, simulation temperature, pressure coupling, and analysis methods are not fully described.
- **Required correction** Provide complete MD simulation parameters and analysis details to allow reproducibility.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Throughout
- **Issue** The term "MG PROTAC" is used throughout, but the distinction from other PROTAC designs could be clarified. The authors should more explicitly define what makes this a "molecular glue-based" PROTAC versus a conventional PROTAC.
- **Required correction** Provide a clear definition of MG PROTAC and how it differs from existing PROTAC designs.

## Risk / unsupported claims
- The claim that this approach "expands the scope of drug discovery to previously intractable protein complexes" is not fully supported by the data, as no cellular degradation or therapeutic efficacy is demonstrated.
- The claim of "selective ubiquitination of distinct complex subunits" is not quantitatively supported.
- The statement that the partial cleavage of the 2-methylbut-3-en-2-yl ether moiety "had negligible impact on 14-3-3/ERα stabilization" is based on a single supplementary figure and requires more detailed analysis.
- The mechanistic explanation for differential cellular permeability of PEG vs alkyl linkers is speculative without direct permeability measurements.
- The physiological relevance of the in vitro ubiquitination conditions is not established.
- The claim of an "unprecedented ligand-induced interface between a 14-3-3:client complex and a neo-substrate" requires comparison with existing literature on 14-3-3 interactions to substantiate the "unprecedented" claim.