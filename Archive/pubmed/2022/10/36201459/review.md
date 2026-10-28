## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract, without access to full methods, figures, or supplementary data
- **Shared manuscript claim summary** The abstract reports that FurC (PerR) from *Anabaena* sp. PCC7120 contains a tightly bound zinc per subunit, binds zinc and manganese at a second site with manganese being more efficient for DNA binding, forms oligomers from dimers to octamers, undergoes reversible oxidation-dependent tetramerization via thiols (not involving intermolecular disulfides in dimerization), and can be irreversibly inactivated by metal-catalyzed oxidation. Structural models are used to infer metal-binding residues and the role of Cys86 in reversible tetramer formation. The authors propose two levels of inactivation, one reversible and one irreversible, with the reversible layer possibly specific to cyanobacteria.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full methods, experimental data (e.g., stoichiometry measurements, DNA binding assays, oligomerization analyses, redox experiments), structural model details, and any statistical analyses

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting regulatory mechanism for a cyanobacterial PerR homolog, with a clear distinction between reversible and irreversible inactivation pathways. However, the evidence base is limited to the abstract, and several claims require experimental detail to be properly evaluated. The proposal of a cyanobacteria-specific reversible regulation is intriguing but not yet substantiated from the provided material.
- **Who would be interested in the results, and why** Researchers studying metal homeostasis and oxidative stress responses in cyanobacteria, as well as those interested in FUR family regulators and PerR homologs across bacterial species. The work may also appeal to structural biologists using predictive modeling to infer functional mechanisms.
- **Major strengths** The abstract clearly identifies a gap in knowledge regarding FurC characterization and addresses it with a combination of biochemical and computational approaches. The distinction between reversible (disulfide-mediated) and irreversible (metal-catalyzed oxidation) inactivation provides a conceptually useful framework. The use of AlphaFold and SWISS-MODEL to guide residue-level hypotheses is a modern and appropriate approach.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "FurC: Zn stoichiometrically binds zinc and manganese in a second site, manganese being more efficient in the binding of FurC: Zn to its DNA target PprxA."
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states stoichiometric binding of both zinc and manganese at a second site, but no quantitative data (e.g., binding constants, stoichiometry values, competition experiments) are provided. The claim that manganese is "more efficient" for DNA binding is not supported by any comparative data in the abstract.
  - **Why it matters** The relative metal specificity and its functional consequence for DNA binding are central to the proposed regulatory model. Without quantitative evidence, the reader cannot assess whether this is a robust effect or a minor difference.
  - **Resolution test** Provide binding isotherms or titration data for zinc and manganese at the second site, and DNA binding assays comparing FurC: Zn with and without each metal under identical conditions, with appropriate replicates and statistical analysis.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "Oligomerization analyses of FurC: Zn evidence the occurrence of different aggregates ranging from dimers to octamers. Notably, intermolecular disulfide bonds are not involved in FurC: Zn dimerization, dimer being the most reduced form of the protein. Oligomerization of dimers occurs upon oxidation of thiols by H2O2 or diamide and can be reversed by 1,4-Dithiothreitol (DTT)."
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract reports a range of oligomeric states and a redox-dependent transition from dimers to higher-order species, but no experimental technique (e.g., size-exclusion chromatography, native gel electrophoresis, analytical ultracentrifugation) or quantitative data (e.g., relative populations, oxidation conditions, kinetics) are described. The claim that "dimer is the most reduced form" requires a clear definition of the redox conditions used.
  - **Why it matters** The oligomerization behavior is the core of the proposed reversible regulation. Without methodological detail and quantitative characterization, the reader cannot evaluate the robustness of the observed transitions or the reversibility claim.
  - **Resolution test** Present oligomerization data from at least one biophysical method with clear controls for redox state, and show dose-response or time-course data for H2O2 and diamide-induced oligomerization and DTT-mediated reversal.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "Comparison of models for FurC: Zn dimers and tetramers obtained using AlphaFold Colab and SWISS-MODEL allowed to infer the residues forming both metal-binding sites and to propose the involvement of Cys86 in reversible tetramer formation."
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that structural models were used to infer metal-binding residues and the role of Cys86, but no validation of these models (e.g., comparison with experimental mutagenesis, conservation analysis, or model confidence metrics) is mentioned. The claim that Cys86 is involved in tetramer formation is presented as a proposal, but the abstract does not indicate whether this was tested experimentally.
  - **Why it matters** Predictive models can generate hypotheses, but the claim of a specific cysteine residue mediating reversible tetramerization requires experimental support (e.g., mutagenesis or mass spectrometry) to be convincing. Without such evidence, the mechanistic conclusion remains speculative.
  - **Resolution test** Provide experimental validation of Cys86 involvement, such as site-directed mutagenesis with functional assays, or clearly label this as a hypothesis requiring future testing rather than a supported conclusion.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract uses "FurC: Zn" without defining whether this notation refers to the zinc-bound form of the protein or a specific complex. This could confuse readers unfamiliar with the system.
  - **Required correction** Define "FurC: Zn" at first use, for example as "FurC with its tightly bound zinc (FurC: Zn)".
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Context
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions "the typical CXXC motifs present in FUR proteins" but does not explain the functional relevance of their absence in FurC. This leaves the reader wondering whether this is a known feature of PerR homologs or unique to this protein.
  - **Required correction** Add a brief statement on the expected role of CXXC motifs in FUR proteins and why their absence in FurC is notable.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Specificity
  - **Affected element** Claim of cyanobacterial specificity
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The final claim that "This additional reversible regulation may be specific of cyanobacteria" is presented without comparative evidence from other organisms.
  - **Required correction** Either provide a reference or brief comparative analysis supporting this claim, or soften the statement to indicate it is a speculation.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The abstract does not provide sufficient quantitative or methodological evidence to establish the core claims of metal binding specificity, redox-dependent oligomerization, and Cys86-mediated tetramer formation.
- **Assessment against Nature-style criteria**  
  - Originality: The concept of two distinct inactivation levels (reversible and irreversible) for a PerR homolog is somewhat novel, but the abstract does not clearly differentiate this from known PerR regulatory mechanisms in other organisms.  
  - Scientific importance: The work addresses a relevant question in cyanobacterial metal and redox homeostasis, but the broader significance beyond this specific organism is not established from the abstract.  
  - Interdisciplinary readership: The topic bridges microbiology, biochemistry, and structural biology, but the abstract is written in a way that assumes familiarity with FUR protein nomenclature and metal-binding assays, which may limit accessibility.  
  - Technical soundness: Cannot be fully assessed from the abstract alone. The claims require experimental detail that is not provided.  
  - Readability for nonspecialists: The abstract is concise but uses field-specific terms without sufficient context, making it difficult for a general scientific audience to follow the significance.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis, but the lack of quantitative data and methodological detail prevents a supportive recommendation. The authors should provide the full experimental evidence to substantiate the claims before the case can be considered.

## Risk / unsupported claims

- The claim that manganese is "more efficient" than zinc for DNA binding is unsupported without comparative binding data.
- The claim that "dimer is the most reduced form" is unsupported without defined redox conditions and quantitative oligomerization data.
- The proposal that Cys86 is involved in reversible tetramer formation is unsupported without experimental validation.
- The claim that the reversible regulation "may be specific of cyanobacteria" is unsupported without comparative evidence from other organisms.
- The overall conclusion of "two levels of inactivation" is not fully supported from the abstract, as the distinction between reversible and irreversible pathways lacks mechanistic detail.