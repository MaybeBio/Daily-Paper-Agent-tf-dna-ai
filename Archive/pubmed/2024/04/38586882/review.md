## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided
- **Assessment boundary** Scientific validity of the in silico screening workflow, data interpretation, and claims made regarding FoxO1 inhibition by natural products
- **Shared manuscript claim summary** The authors report an in silico screening of 550 natural products against FoxO1 (PDB 3CO6) using docking, MMGBSA, ADMET prediction, and MD simulations, identifying neochlorogenic acid and fraxin as promising FoxO1 inhibitors, with fraxin showing stable binding over 25 ns MD simulation
- **Visible evidence base** Abstract, full text narrative, Tables 1 and 2 referenced, Figures 1-5 referenced
- **Missing materials affecting confidence** Tables 1 and 2 data not provided; Figures 1-5 not provided; no coordinates, trajectories, or raw scoring data; no statistical analysis details; no validation metrics for docking or MD protocols

## Reviewer
- **Overall assessment** The manuscript presents a straightforward in silico screening workflow that is methodologically conventional but contains several critical scientific gaps. The central claim that fraxin and neochlorogenic acid are potential FoxO1 inhibitors is not adequately supported by the evidence presented. The docking scores reported (below -6.0) are modest and not contextualized against known inhibitors or decoy sets. The MMGBSA values are presented without error estimates or comparison to reference compounds. The MD simulation of 25 ns is short by current standards and lacks convergence analysis. Most concerning, the manuscript does not address whether the identified compounds bind to a functionally relevant site on FoxO1, nor does it provide any experimental validation or comparison to the known inhibitor AS1842856. The ADMET discussion contains internal inconsistencies, including mention of dihydromyricetin which was not among the nine selected compounds. The manuscript would benefit from substantial revision and additional analyses before the claims can be considered established.

- **Who would be interested in the results, and why** Researchers in computational drug discovery and natural product screening might find the workflow of interest as a methodological template. Investigators studying FoxO1 as a therapeutic target in metabolic disease or cancer could be interested in the identified compounds as starting points, though the lack of experimental validation limits immediate utility. The broader natural product screening community may find the compound library composition and screening results useful for comparative purposes.

- **Major strengths** The manuscript addresses an underexplored target (FoxO1) with limited known inhibitors, which is a relevant gap. The workflow integrates multiple computational methods (docking, MMGBSA, ADMET, MD) in a logical sequence. The use of free web servers for ADMET prediction enhances reproducibility. The authors appropriately acknowledge the limitations of docking as a static method and employ MD to assess dynamic stability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Several natural products demonstrated high docking scores with FoxO1, indicating their potential as FoxO1 inhibitors. Specifically, the docking scores of neochlorogenic acid and fraxin were both below -6.0."
- **Evidence pointer** Table 1, Figure 3, location not provided
- **Concern** The docking scores are presented without any benchmark or comparator. A score below -6.0 is not inherently meaningful without reference to known FoxO1 inhibitors, decoy molecules, or a validated threshold for this specific protein-ligand system. The authors do not report docking of the known inhibitor AS1842856 (mentioned in the introduction) as a positive control, nor do they report docking of decoy compounds to establish a baseline. Additionally, the functional relevance of the binding site is not established. The authors used SiteMap to identify a binding site but do not demonstrate that this site corresponds to a functionally important region of FoxO1, such as the DNA-binding domain or a known protein-protein interaction interface.
- **Why it matters** Without contextualization against known binders and validation of the binding site relevance, the docking scores cannot be interpreted as evidence of potential inhibition. A compound can bind with high affinity to a non-functional site and have no inhibitory activity. The central claim of the manuscript depends on this evidence.
- **Resolution test** The authors should dock AS1842856 (or another known FoxO1 inhibitor) to the same grid and report comparative scores. They should also dock a set of decoy compounds to establish a score distribution. The functional relevance of the predicted binding site should be demonstrated by mapping it to known functional domains of FoxO1 and discussing whether binding at this site would plausibly inhibit FoxO1 function.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "MD simulations confirmed that the interaction with fraxin remained stable throughout the simulation period."
- **Evidence pointer** Figure 4, Figure 5, location not provided
- **Concern** The MD simulation of 25 ns is short by contemporary standards for establishing binding stability. The authors report RMSD values between 1.6 and 3.2 Å for neochlorogenic acid, which they describe as acceptable, but they do not report RMSD values for fraxin. The statement that fraxin "remained stable for the entire duration" is not supported by quantitative data in the text. Additionally, the authors do not report root mean square fluctuation (RMSF), radius of gyration, hydrogen bond occupancy, or binding free energy calculations from the MD trajectory. The ligand interaction diagram (Figure 5) is a static representation and does not demonstrate dynamic stability. No replicate simulations or statistical analysis of trajectory data are reported.
- **Why it matters** The MD simulation is the primary evidence for the claim that fraxin forms a stable interaction with FoxO1. Without quantitative analysis of the trajectory, convergence assessment, and ideally replicate simulations, the stability claim is not established. A 25 ns simulation may not capture conformational changes or binding/unbinding events relevant to inhibitor function.
- **Resolution test** The authors should report RMSD and RMSF values for both protein and ligand over the simulation, hydrogen bond occupancy analysis, and ideally extend the simulation to at least 100 ns or provide replicate simulations. Binding free energy calculations (e.g., MM-PBSA or similar) from the MD trajectory would strengthen the stability claim. Convergence of the simulation should be demonstrated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency
- **Claim pointer** "compounds such as neochlorogenic acid, fraxin, quercitrin, and dihydromyricetin exhibited good intestinal absorption rates of greater than 30%"
- **Evidence pointer** Discussion section, location not provided
- **Concern** Dihydromyricetin is mentioned in the ADMET discussion but was not among the nine selected compounds listed in the results section. The nine compounds were cellobiose, scutellarin, neochlorogenic acid, chondroitin sulfate, amygdalin, fraxin, salvianolic acid A, desacetyl asperulosidic acid, and quercitrin. Dihydromyricetin appears nowhere in the results. This internal inconsistency suggests either an error in the discussion or undisclosed additional analysis. Additionally, the authors state that "most of them—except for neochlorogenic acid, salvianolic acid A, and fraxin—had more than two Lipinski violations and were therefore excluded from further study," but the selection criteria for MD studies are not clearly defined. The relationship between Lipinski violations, intestinal absorption, and the final selection of neochlorogenic acid and fraxin for MD is not transparent.
- **Why it matters** Internal inconsistencies undermine confidence in the reliability of the reported results. The selection process for compounds advancing to MD simulation should be clearly documented and reproducible. The mention of a compound not in the selected set raises questions about the rigor of the analysis.
- **Resolution test** The authors should correct the mention of dihydromyricetin or clarify its role. The compound selection criteria for MD simulation should be explicitly stated, including any thresholds for Lipinski violations, intestinal absorption, or other ADMET parameters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** "These compounds also exhibit favorable drug-like properties, and a 25 ns MD study revealed a stable interaction between fraxin and FoxO1."
- **Evidence pointer** Table 2, location not provided
- **Concern** The ADMET predictions are presented as favorable, but the actual data in Table 2 are not available for review. The discussion mentions specific parameters (molecular weight, BBB permeability, CYP inhibition, P-gp inhibition, Ames toxicity, hERG inhibition, Lipinski violations, synthetic accessibility, intestinal absorption) but does not provide the actual values in the text. Without the data, the claim of "favorable drug-like properties" cannot be assessed. Furthermore, the authors do not discuss the limitations of in silico ADMET predictions, which are known to have variable accuracy.
- **Why it matters** The ADMET profile is a key component of the claim that these compounds are promising drug candidates. Without access to the actual predicted values, this claim is not verifiable from the provided material.
- **Resolution test** The authors should ensure Table 2 is included with complete data for all nine compounds across all reported ADMET parameters. The discussion should reference specific values and interpret them in the context of established drug-likeness criteria.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "Our findings highlight the potential of various natural products, particularly fraxin, as effective FoxO1 inhibitors with strong binding affinity, dynamic stability, and suitable ADMET profiles."
- **Evidence pointer** Abstract, Discussion, location not provided
- **Concern** The manuscript does not compare the identified compounds to known FoxO1 inhibitors in terms of binding affinity, binding mode, or predicted efficacy. The known inhibitor AS1842856 is mentioned in the introduction but is not used as a comparator in any analysis. The authors also do not discuss whether the predicted binding site overlaps with the binding site of known inhibitors or with functionally critical regions of FoxO1. The potential mechanism of inhibition (e.g., competitive binding to the DNA-binding domain, allosteric modulation) is not addressed.
- **Why it matters** Without comparison to known inhibitors and discussion of mechanism, the significance of the findings is unclear. The claim that these compounds are "effective FoxO1 inhibitors" is not supported by the evidence, which only shows predicted binding affinity and stability. The manuscript does not establish that binding translates to functional inhibition.
- **Resolution test** The authors should dock AS1842856 to the same grid and compare binding modes and scores. They should discuss whether the predicted binding site is consistent with known inhibitor binding sites or with functionally relevant regions of FoxO1. The manuscript should be revised to frame the findings as identifying candidate compounds for experimental validation rather than as established inhibitors.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, protein-protein interaction analysis
- **Evidence pointer** Materials and Methods, location not provided
- **Issue** The protein-protein interaction analysis using STRING is presented as part of the methods but its results are not clearly connected to the main screening workflow. The relevance of identifying interaction partners to the inhibitor screening is not explained.
- **Required correction** Clarify the purpose of the STRING analysis in the context of the study. If it is meant to provide biological context for FoxO1 function, state this explicitly. If it is not essential to the screening workflow, consider moving it to supplementary material.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section, binding free energy calculation
- **Evidence pointer** Materials and Methods, location not provided
- **Issue** The equation for binding free energy calculation is mentioned but not shown. The specific parameters used in the MM-GBSA calculation (e.g., dielectric constant, solvent model) are not reported.
- **Required correction** Include the equation and report all relevant parameters for reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section, virtual screening
- **Evidence pointer** Results, location not provided
- **Issue** The statement "over 80 natural products in the test library achieved a docking score below -5.0" is presented without a distribution or histogram. The selection of the nine compounds for further study is not justified beyond having the "most favorable docking scores."
- **Required correction** Provide a distribution of docking scores for the full library and clearly state the selection criteria for the nine compounds (e.g., score threshold, diversity of scaffolds, known bioactivity).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, MD simulation
- **Evidence pointer** Results, location not provided
- **Issue** The MD simulation section reports RMSD values for neochlorogenic acid but not for fraxin. The statement that fraxin remained stable is not quantified.
- **Required correction** Report RMSD and RMSF values for both compounds, including the range and average values over the simulation period.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Discussion section
- **Evidence pointer** Discussion, location not provided
- **Issue** The phrase "DMPK studies, also referred to as ADMET investigations" is imprecise. DMPK (drug metabolism and pharmacokinetics) and ADMET (absorption, distribution, metabolism, excretion, toxicity) are related but distinct concepts.
- **Required correction** Use the terms accurately. Either refer to ADMET studies or DMPK studies, and define the scope of the analysis performed.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion of the biological relevance of FoxO1 inhibition is brief and does not connect the identified compounds to specific therapeutic applications beyond general statements about carcinogenesis, metabolic disorders, and skeletal muscle differentiation.
- **Required correction** Expand the discussion to address which specific disease contexts would be most relevant for the identified compounds and how FoxO1 inhibition in those contexts could be therapeutically beneficial.

## Risk / unsupported claims
- The claim that fraxin and neochlorogenic acid are "effective FoxO1 inhibitors" is unsupported. The study only demonstrates predicted binding affinity and stability in silico, not functional inhibition.
- The claim of "favorable drug-like properties" is not assessable without the actual ADMET data from Table 2.
- The claim that the identified compounds bind to a functionally relevant site on FoxO1 is unsupported. The authors do not map the predicted binding site to known functional domains.
- The claim that the MD simulation demonstrates stable interaction is weakly supported. Only qualitative statements are provided for fraxin, and no quantitative trajectory analysis is reported.
- The mention of dihydromyricetin in the discussion without its presence in the results creates an unsupported claim about this compound's ADMET properties.
- The relevance of the STRING protein-protein interaction analysis to the inhibitor screening is not established.