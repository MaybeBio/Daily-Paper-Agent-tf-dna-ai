## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) for a research article submitted to RSC Advances.
- **Assessment boundary** Scientific content, technical soundness, internal consistency, and support of claims by presented evidence. No assessment of literature novelty beyond what is cited or discussed in the manuscript.
- **Shared manuscript claim summary** The authors report the synthesis and characterization of two half-sandwich Ru(II) complexes bearing picolinamide ligands (C1 and C2), and investigate their solution stability and DNA-binding properties using spectroscopic and in silico methods. They claim that a para-fluoro substituent on the ligand enhances resistance to ligand exchange, and that both complexes bind DNA with a significant intercalative component, with the aqua form of C1 showing higher apparent binding affinity.
- **Visible evidence base** Full text including methods, results, discussion, and conclusion. Figures and tables are referenced but not all are visible in the provided text. Supplementary information is mentioned but not provided.
- **Missing materials affecting confidence** Supplementary figures (Fig. S1–S18), supplementary tables (Tables S1–S5), full crystallographic data (only CCDC number given), raw spectra, and complete computational details. The ESI methods for docking and MD are not available.

## Reviewer
- **Overall assessment** The manuscript presents a systematic study of two Ru(II) half-sandwich complexes with picolinamide ligands, combining synthesis, characterization, stability assays, and DNA-binding studies. The work is competently executed within a standard medicinal inorganic chemistry framework. However, several claims regarding DNA-binding mode and the role of fluorine substitution are only partially supported by the presented evidence. The computational component is limited in scope and depth, and the authors themselves acknowledge this. The manuscript would benefit from additional experimental data (e.g., viscosity measurements, more rigorous binding constant determination) and a more thorough computational analysis to fully substantiate the conclusions.
- **Who would be interested in the results, and why** Researchers in the field of medicinal inorganic chemistry, particularly those working on ruthenium-based anticancer agents and DNA-targeting metallodrugs. The study provides structure-activity insights relevant to the design of half-sandwich Ru(II) complexes, and the comparative stability data for fluorinated vs. non-fluorinated ligands may be of interest to groups developing improved metallodrug candidates.
- **Major strengths**
  1. Comprehensive characterization of the complexes using multiple complementary techniques (HR-ESI-MS, NMR, FT-IR, elemental analysis, SCXRD).
  2. The stability studies, including pH-dependent speciation, are well-designed and provide useful comparative data for the two complexes.
  3. The combination of experimental and computational approaches (TD-DFT, docking, MD) is commendable, even if the computational depth is limited.
  4. The authors are appropriately cautious in some interpretations, acknowledging limitations of the docking and MD approaches.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Evidence sufficiency
  - **Claim pointer** The manuscript claims that "DNA binding involves a significant intercalative component" based on thermal denaturation and UV-LD data.
  - **Evidence pointer** Results section, "Thermal denaturation of ctDNA" and "UV-CD and LD spectroscopy" subsections; Fig. 6 and 7.
  - **Concern** The evidence presented for intercalation is indirect and not fully conclusive. The thermal denaturation data show a ΔTm of 4.26 °C for C1-aqua, which is modest and could also be consistent with groove binding or partial intercalation. The UV-LD data are described qualitatively, but no quantitative analysis (e.g., reduced linear dichroism values) is provided. The authors themselves note that "contributions from minor groove binding cannot be excluded." The claim of "significant intercalative component" is therefore overstated relative to the evidence. Furthermore, the EtBr displacement assay is an indirect method, and the authors acknowledge that quenching does not necessarily indicate displacement.
  - **Why it matters** The proposed DNA-binding mode is a central conclusion of the paper and is used to frame the complexes as potential therapeutics. If the binding mode is not rigorously established, the mechanistic interpretation and the structure-activity conclusions are weakened.
  - **Resolution test** Provide additional experimental evidence for intercalation, such as viscosity measurements (which are standard for distinguishing intercalation from groove binding), or quantitative analysis of UV-LD data. Alternatively, temper the claim to state that the data are "consistent with partial intercalation or groove binding" and discuss the ambiguity more explicitly.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Data interpretation
  - **Claim pointer** The manuscript claims that the fluorinated complex C2 exhibits "enhanced resistance to ligand substitution" and attributes this to the electron-withdrawing effect of fluorine.
  - **Evidence pointer** Results section, "Stability assay" and "Spectroscopic pKa determinations" subsections; Fig. 3.
  - **Concern** The stability data are based on UV-vis spectroscopy, which is a bulk method that may not distinguish between different chemical species or processes. The interpretation that the spectral changes for C2 are due to "outer-sphere solvation and ion-pairing effects" rather than ligand substitution is speculative and not directly supported by any molecular-level evidence (e.g., mass spectrometry or NMR under the same conditions). The claim that fluorine "stabilises the metal–ligand framework" is plausible but is inferred rather than demonstrated.
  - **Why it matters** The differential stability of C1 and C2 is a key finding that underpins the structure-activity discussion. If the mechanism of stabilization is not rigorously established, the conclusions about electronic effects are weakened.
  - **Resolution test** Provide additional evidence for the speciation of C2 under the assay conditions, such as 1H NMR or HR-ESI-MS of the complexes in aqueous buffer over time. Alternatively, temper the mechanistic interpretation and present the stability data as empirical observations without over-interpreting the underlying cause.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Computational rigor
  - **Claim pointer** The manuscript claims that molecular docking and 100 ns MD simulations "supported favourable interactions with AT-rich regions of DNA and indicated dynamically stable binding modes."
  - **Evidence pointer** Results section, "Molecular docking and molecular dynamics simulations" subsection; Fig. 8.
  - **Concern** The computational analysis is limited to RMSD evaluation of the MD trajectories. The authors acknowledge this limitation but still draw conclusions about "dynamically stable binding modes." RMSD alone is insufficient to establish binding stability or mode; other metrics (e.g., RMSF, contact analysis, hydrogen-bond occupancy, binding free energy) are needed. The docking scores are reported as ΔGbind values, but the authors correctly note that these do not correspond directly to binding free energies. The claim of "favourable interactions" is therefore weakly supported.
  - **Why it matters** The computational results are used to corroborate the experimental DNA-binding data. If the computational evidence is not rigorous, the overall case for the proposed binding mode is weakened.
  - **Resolution test** Provide additional MD analyses (e.g., RMSF, per-residue contact maps, hydrogen-bond occupancy) or perform binding free-energy calculations (e.g., MM-PBSA/GBSA). Alternatively, present the computational results as purely qualitative and exploratory, and rely more heavily on experimental evidence for the conclusions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity / Reproducibility
  - **Affected element** Methods section, "In silico methods"
  - **Evidence pointer** Methods section, "Density functional theory simulations" and "Molecular docking and molecular dynamics simulations" subsections.
  - **Issue** The methods for DFT, docking, and MD are described only briefly, with details deferred to the ESI. For a study that relies on computational results, more detail should be provided in the main text (e.g., software versions, force fields, water models, equilibration protocols).
  - **Required correction** Provide sufficient methodological detail in the main text or ensure the ESI is comprehensive and clearly cross-referenced.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results section, "DNA binding" subsection
  - **Evidence pointer** Table 2 and Fig. 5.
  - **Issue** The binding constants (log Ka) are reported as "apparent" values, which is appropriate given the indirect method. However, the manuscript does not clearly state the units or the model used to derive these values from the fluorescence data.
  - **Required correction** Clarify the calculation method and units for the reported binding constants.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Language / Precision
  - **Affected element** Abstract and Conclusion
  - **Evidence pointer** Abstract, "DNA-binding investigations" sentence; Conclusion, first paragraph.
  - **Issue** The phrase "significant intercalative component" is used in the abstract and conclusion, which overstates the certainty of the binding mode given the limitations discussed above.
  - **Required correction** Use more cautious language, such as "consistent with partial intercalation" or "suggestive of an intercalative component."
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results section, "Cyclic voltammetry" subsection
  - **Evidence pointer** Fig. 4 and Table S5.
  - **Issue** The cyclic voltammetry data are presented but not discussed in the context of the DNA-binding results. The redox potentials are not related to the stability or reactivity of the complexes.
  - **Required correction** Either provide a brief discussion of the electrochemical data in the context of the study's aims, or remove the data if it is not essential.
- **Technical failings that need to be addressed before the case is established**
  1. The evidence for intercalative DNA binding is indirect and not quantitatively supported (R1-M1).
  2. The mechanistic interpretation of the stability differences between C1 and C2 is speculative (R1-M2).
  3. The computational analysis is too shallow to support the claims of stable binding modes (R1-M3).
- **Assessment against Nature-style criteria**
  - **Originality** The work is incremental. While the specific complexes are new, the general approach (Ru(II) half-sandwich complexes with N,N-chelating ligands, DNA-binding studies) is well-established. The study does not introduce a fundamentally new concept or methodology.
  - **Scientific importance** The findings are of moderate interest to the medicinal inorganic chemistry community but do not represent a major advance. The structure-activity insights are preliminary and would need to be validated with more rigorous experiments.
  - **Interdisciplinary readership** The work is primarily of interest to specialists in inorganic chemistry and DNA-binding studies. It is unlikely to attract a broad interdisciplinary audience.
  - **Technical soundness** The synthetic and characterization work appears sound. However, the DNA-binding studies and computational analyses have significant limitations that undermine the strength of the conclusions.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible, but some sections (e.g., the computational methods) are too brief for a nonspecialist to fully evaluate.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has merit and the synthetic/characterization work is solid, but the central claims regarding DNA-binding mode and the role of fluorine substitution are not sufficiently supported. Major revisions are required to address the concerns raised, particularly regarding the evidence for intercalation and the rigor of the computational analysis. If these issues are resolved, the manuscript could be suitable for publication in a specialized journal like RSC Advances.

## Risk / unsupported claims
- The claim of a "significant intercalative component" in DNA binding is not fully supported by the presented evidence (indirect assays, no quantitative analysis).
- The claim that the fluorine substituent "stabilises the metal–ligand framework" is inferred from UV-vis data without direct molecular-level evidence.
- The claim of "dynamically stable binding modes" from MD simulations is based solely on RMSD analysis, which is insufficient.
- The reported log Ka values are "apparent" and derived from an indirect assay; their quantitative reliability is uncertain.
- The statement that "both C1-aqua and C2 are intercalators of DNA" (in the discussion of docking results) is an overstatement given the limitations acknowledged by the authors.