## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, conclusion, and data availability statements. Supplementary materials referenced but not provided.

- **Assessment boundary** Assessment is limited to the scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. Supplementary figures, tables, and methods referenced in the text were not available for review.

- **Shared manuscript claim summary** The authors report that ETS-family transcription factors from all three major classes (Ets1, ELF1, PU.1) bind DNA containing a cis-syn TpT cyclobutane pyrimidine dimer (CPD) at the central position of the ETS binding motif, that this binding inhibits cleavage by the model repair enzyme T4 PDG, and that structural and thermodynamic analyses reveal a mechanism involving CPD-induced dynamics in free DNA that are linked to entropy-driven binding.

- **Visible evidence base** Electrophoretic mobility shift assays (Fig. 1C-E, Supplementary Figs. S1-S3), T4 PDG cleavage assays (Fig. 2A-C, Supplementary Fig. S4), X-ray crystal structures of PU.1/DNA complexes (Fig. 3A-D, PDB entries 9YNZ, 9OA4, 9OB0), molecular dynamics simulations (Fig. 4, Supplementary Figs. S8-S11), fluorescence polarization binding assays (Fig. 5A), isothermal titration calorimetry (Fig. 5B), and osmotic stress experiments (Fig. 5C-D).

- **Missing materials affecting confidence** Supplementary figures S1-S11, Supplementary tables S1-S2, and Supplemental methods (including CPD oligo synthesis details) were not provided. Crystal structure validation reports and refinement statistics were referenced but not available. This limits full assessment of data quality, particularly for crystallographic and simulation analyses.

## Reviewer

- **Overall assessment** This manuscript presents a comprehensive and well-executed study addressing an important question in cancer biology: how ETS transcription factors bind damaged DNA and inhibit repair, thereby promoting mutation hotspots in melanoma. The combination of biochemical, structural, and computational approaches is impressive and provides a plausible molecular mechanism. The finding that CPD lesions at the central position of the ETS motif enhance binding across all three ETS classes is novel and significant. However, several concerns regarding data interpretation, particularly the thermodynamic analysis and the physiological relevance of the T4 PDG inhibition assays, need to be addressed. The manuscript is well-written and the logic is clear, but some claims extend beyond what the data directly support.

- **Who would be interested in the results, and why** Researchers in DNA repair, transcription factor biology, skin cancer genetics, and structural biology would find this work of interest. The study provides mechanistic insight into how transcription factors can both promote DNA damage formation and inhibit its repair, which has implications for understanding mutagenesis in cancer genomes. The structural data on how a bulky DNA lesion is accommodated within a transcription factor binding site will be of interest to the structural biology community. The thermodynamic analysis linking DNA dynamics to binding affinity may appeal to biophysical chemists studying protein-DNA interactions.

- **Major strengths** The study addresses a significant and timely question with clear clinical relevance to melanoma genetics. The experimental design is logical, progressing from biochemical observations to structural and thermodynamic characterization. The inclusion of representatives from all three ETS classes strengthens the generalizability of the findings. The crystallographic work provides high-quality structural data, and the MD simulations complement the experimental observations. The thermodynamic analysis is sophisticated and reveals an unexpected entropy-driven binding mechanism for CPD-containing DNA.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation / claim support
- **Claim pointer** The authors claim that "formation of the 1:1 ETS/DNA complex by each ETS paralog can restrict its access to a CPD lesion by the model repair enzyme, T4 PDG" and that this provides a molecular basis for repair inhibition in cells.
- **Evidence pointer** Fig. 2A-C, Results section "ETS binding inhibits cleavage of a CPD lesion by a model repair enzyme"
- **Concern** The T4 PDG inhibition assays are performed with a large excess of ETS protein (10-fold molar excess relative to DNA). The physiological relevance of this stoichiometry is unclear. In cells, ETS factors are present at much lower concentrations relative to the vast excess of genomic DNA. The claim that ETS binding "can inhibit accessibility of the lesion to repair enzymes" in a cellular context requires more careful consideration of the relevant concentrations and competition kinetics. Additionally, T4 PDG is a bacterial enzyme with different DNA binding properties than human NER factors; the authors acknowledge this but do not adequately address whether the observed inhibition would translate to human NER machinery.
- **Why it matters** The central biological claim of the manuscript is that ETS factors inhibit CPD repair in cells, promoting mutation hotspots. If the inhibition only occurs at non-physiological protein concentrations, the relevance of the findings to melanoma genetics is weakened.
- **Resolution test** The authors should either (a) perform T4 PDG inhibition assays at lower, more physiologically relevant ETS concentrations, (b) test whether ETS binding inhibits repair by a human NER system (e.g., using cell extracts or reconstituted NER), or (c) provide quantitative modeling showing that the observed binding affinities and cellular concentrations would result in significant repair inhibition at ETS binding sites.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation / thermodynamic analysis
- **Claim pointer** The authors claim that the thermodynamic analysis reveals "the first example of high-affinity PU.1 interactions without favorable enthalpic contributions from the noncovalent contacts" and that the entropy-driven binding is linked to "CPD-induced heterogeneity in the conformational dynamics of free DNA."
- **Evidence pointer** Fig. 5A-D, Results section "Probing the structural dynamics of CPD-bound ETS complexes" and "ETS binding to CPD is thermodynamically linked to CPD-induced dynamics in the free DNA"
- **Concern** The interpretation of the osmotic stress experiments is complex and the conclusions drawn may be overreaching. The authors interpret the convex dependence of binding free energy on osmolyte concentration as evidence for coupled release of osmolyte and water. However, osmolyte effects on protein-DNA binding can be influenced by many factors, including preferential exclusion from specific surfaces, changes in water activity, and direct osmolyte-protein interactions. The authors do not provide sufficient control experiments to rule out alternative interpretations. Furthermore, the link between the MD simulations and the thermodynamic observations is largely qualitative; the simulations do not directly compute free energy differences or solvent distributions that would quantitatively support the proposed mechanism.
- **Why it matters** The thermodynamic mechanism proposed is a key novel finding of the manuscript. If the interpretation is not robust, the mechanistic insight is weakened.
- **Resolution test** The authors should provide additional experimental evidence supporting their interpretation, such as (a) direct measurement of water release using osmotic stress with multiple different osmolytes of varying sizes, (b) computational analysis of solvent distributions in the free and bound states from the MD simulations, or (c) mutational analysis targeting residues predicted to be involved in the differential solvation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor / crystallography
- **Claim pointer** The authors state that "co-crystal structures of PU.1 reveal that CPDs and mismatches are recognized within the framework of canonical ETS/DNA complexes" and use these structures to support their mechanistic conclusions.
- **Evidence pointer** Fig. 3A-D, Results section "Structural bases of ETS interactions with damaged and mismatched DNA"
- **Concern** The crystallographic analysis is complicated by the observation of low electron density over the CPD lesion, which the authors attribute to potential photoreversion or inherent dynamics. The manuscript does not provide sufficient detail on how the CPD-containing structure was refined given this ambiguity, nor does it provide clear evidence that the deposited structure accurately represents the CPD-bound state. The resolution and refinement statistics are only given in supplementary Table S1, which was not available for review. Without these details, it is difficult to assess the reliability of the structural conclusions.
- **Why it matters** The structural data are central to the manuscript's claims about how CPD lesions are accommodated in ETS/DNA complexes. If the CPD structure is not well-defined, the structural conclusions are weakened.
- **Resolution test** The authors should provide the refinement statistics and electron density maps for the CPD-containing structure, and discuss in more detail how the low density over the lesion was handled. If possible, additional crystallographic or solution-state data (e.g., NMR) should be presented to confirm the CPD-bound conformation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scope / physiological relevance
- **Claim pointer** The authors conclude that their findings "offer a molecular basis for how ETS factors induce mutation hotspots in skin cancers and other UV-exposed tissues by binding to CPD-containing sites and inhibiting their repair."
- **Evidence pointer** Discussion section, Conclusion
- **Concern** The study uses purified ETS domains rather than full-length proteins, and the DNA constructs are short oligonucleotides rather than genomic contexts. The authors do not address whether the presence of flanking domains, post-translational modifications, or chromatin context would affect the observed binding and inhibition. Additionally, the study focuses on a single DNA sequence context (the DPH3 promoter); the generality of the findings to other ETS binding sites is not established.
- **Why it matters** The claim of broad relevance to melanoma mutagenesis requires that the observed phenomena are generalizable beyond the specific in vitro conditions tested.
- **Resolution test** The authors should either (a) test additional ETS binding site contexts, (b) use full-length proteins in at least some experiments, or (c) temper the conclusions to acknowledge the limitations of the in vitro system.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / presentation
- **Affected element** Fig. 1D-E
- **Evidence pointer** Results section "Paralogs from all major ETS classes bind cognate CPD-containing motifs"
- **Issue** The quantification of EMSA data using "r at 50% loss of unbound DNA" is unconventional. Standard binding isotherms (fraction bound vs. protein concentration) would be more informative and allow direct comparison of binding affinities.
- **Required correction** Consider presenting standard binding curves with fitted dissociation constants, or at least providing a clear explanation of why the alternative metric was chosen.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "Molecular dynamics simulations"
- **Evidence pointer** Methods, Supplementary Table S2
- **Issue** The simulation protocol is described briefly, and details such as the force field parameters for the CPD lesion, equilibration protocol, and analysis methods are not fully described in the main text.
- **Required correction** Provide more complete simulation details, either in the main text or in the supplementary methods, to allow reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 5C-D
- **Evidence pointer** Results section "ETS binding to CPD is thermodynamically linked to CPD-induced dynamics in the free DNA"
- **Issue** The osmotic stress data are presented as log KD vs. osmolyte concentration. It would be helpful to also show the raw binding data and the fitted curves to demonstrate the quality of the measurements.
- **Required correction** Include representative binding isotherms or a statement about the quality of the fits.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript does not discuss recent structural studies of other transcription factors bound to damaged DNA, which could provide important context for the novelty of the findings.
- **Required correction** Add a brief discussion of related work on transcription factor binding to damaged DNA to better position the novelty of this study.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Fig. 2C
- **Evidence pointer** Results section "ETS binding inhibits cleavage of a CPD lesion by a model repair enzyme"
- **Issue** The statistical analysis of the T4 PDG inhibition data is not described. It is unclear whether the differences in initial velocities are statistically significant and how many replicates were performed.
- **Required correction** Provide details on the number of replicates and the statistical tests used.

## Risk / unsupported claims

1. The claim that ETS binding inhibits repair in a manner directly relevant to cellular NER is not fully supported, as only the bacterial enzyme T4 PDG was tested and at high protein concentrations.

2. The interpretation of the osmotic stress experiments as evidence for coupled release of osmolyte and water is not uniquely supported by the data; alternative explanations are possible.

3. The claim that the thermodynamic findings represent "the first example of high-affinity PU.1 interactions without favorable enthalpic contributions" is strong and would benefit from comparison with other high-affinity protein-DNA interactions that are entropy-driven.

4. The structural conclusions regarding the CPD-containing complex are weakened by the low electron density over the lesion, and the deposited structure may not fully represent the CPD-bound state.

5. The generalization of findings from purified ETS domains on short oligonucleotides to the in vivo context of melanoma mutagenesis is not fully justified without additional experiments or discussion of potential confounding factors.