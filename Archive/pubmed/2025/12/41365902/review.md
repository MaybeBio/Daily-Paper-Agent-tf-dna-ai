## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends as provided.
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided text. No assessment of supplementary information, raw data files, or external databases beyond what is described.
- **Shared manuscript claim summary** The authors report the first direct small-molecule ligands targeting the MITF bHLH-LZ domain, discovered via fragment-based screening. They provide biophysical and structural characterization of binding to a "kink pocket" formed by a three-residue insertion, show selectivity over MYC/MAX, and present genetic evidence suggesting functional relevance of this region in melanoma cell lines.
- **Visible evidence base** NMR screening data, X-ray co-crystal structures, ITC, SPR, nanoDSF, MD simulations, RNA-seq, Cut&Tag, cell viability assays, and xenograft experiments, as described in the text.
- **Missing materials affecting confidence** Supplementary figures and tables, source data files, PDB deposition details, compound synthesis procedures, full bioinformatics pipelines, and raw sequencing data are not available for independent verification.

## Reviewer
- **Overall assessment** This manuscript addresses a challenging and important target in melanoma biology. The discovery of ligands for the MITF kink pocket is a notable technical achievement, and the biophysical characterization is thorough. However, the functional significance of the kink pocket and the therapeutic potential of the compounds remain incompletely established. The genetic experiments are suggestive but limited, and the lack of cellular activity data for the optimized compounds weakens the translational claims. The manuscript is technically strong in structural biology but falls short of demonstrating that targeting the kink pocket leads to meaningful MITF inhibition in a disease-relevant context.
- **Who would be interested in the results, and why** Structural biologists and medicinal chemists working on transcription factor targeting, particularly those interested in bHLH-LZ family proteins. Researchers in melanoma biology and drug discovery will also find the work relevant, as it provides a potential new approach to a previously undruggable target. The methodological advances in fragment screening and biophysical characterization of weak protein-ligand interactions may interest a broader audience in chemical biology.
- **Major strengths**
  1. The first demonstration of direct, structurally characterized small-molecule binding to a bHLH-LZ transcription factor, addressing a long-standing challenge in the field.
  2. Rigorous use of orthogonal biophysical methods (NMR, ITC, SPR, X-ray crystallography) to validate binding.
  3. The identification and characterization of the kink pocket as a unique structural feature of MITF, with selectivity data over MYC/MAX.
  4. Integration of MD simulations with experimental data to propose a mechanism of action involving modulation of helix dynamics.
  5. Clinical data analysis provides a reasonable rationale for targeting MITF in melanoma.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** "Genetic experiments suggest a functional role for the kink pocket, warranting further investigation" and "targeting the kink pocket may lead to functional MITF inhibition"
- **Evidence pointer** Figure 10, Supplementary Figures 12 and 13
- **Concern** The functional significance of the kink pocket is inferred solely from mutagenesis experiments in which residues Q261, R263, and A264 are mutated. These mutations are in the dimerization domain, and the authors do not demonstrate that the mutations specifically disrupt kink pocket function rather than globally destabilizing the protein or affecting dimerization. The rescue experiments show incomplete phenocopy of WT, but the interpretation is confounded by potential effects on protein folding, stability, or dimerization that are not fully addressed. The authors state that CD and nanoDSF confirm structural integrity, but these are bulk measurements that may not detect subtle conformational changes.
- **Why it matters** The central claim of the paper is that the kink pocket is functionally important and that targeting it can inhibit MITF. Without a clear demonstration that the observed phenotypes are due specifically to disruption of the kink pocket, the therapeutic rationale for the discovered ligands is weakened. The compounds themselves are not tested in cellular assays, so the link between binding and functional inhibition is entirely dependent on the mutagenesis data.
- **Resolution test** The authors should demonstrate that the kink pocket mutations do not affect dimerization affinity or overall protein stability using quantitative methods (e.g., SEC-MALS, analytical ultracentrifugation). Additionally, they should test whether the optimized compounds can modulate MITF transcriptional activity in cell-based reporter assays or affect melanoma cell viability, even if only at high concentrations. Alternatively, a chemical biology approach using a negative control compound with similar physicochemical properties but no binding could strengthen the case.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Selectivity and specificity
- **Claim pointer** "Selected ligands are further characterized by orthogonal biophysical methods that, along with extensive use of X-ray crystallography, provide evidence of unprecedented binding of small molecules to MITF" and "selectivity of the MITF ligands of at least 100-fold over binding to the DBD of MYC/MAX"
- **Evidence pointer** Supplementary Figure 7
- **Concern** Selectivity is only demonstrated against MYC/MAX, which is a reasonable comparator given sequence homology. However, the broader selectivity of the compounds is not assessed. The kink pocket is a unique feature of MITF, but the compounds may bind to other proteins with similar hydrophobic pockets. No proteome-wide selectivity data (e.g., chemoproteomics) or testing against a panel of related bHLH-LZ transcription factors is provided. The claim of "selectivity" is therefore limited in scope.
- **Why it matters** For a potential therapeutic, off-target effects are a major concern. The manuscript positions these compounds as a starting point for drug development, but without broader selectivity data, the translational potential is unclear. The 100-fold selectivity claim is based on a single comparator and may not hold against other proteins.
- **Resolution test** The authors should test the compounds against a panel of related bHLH-LZ transcription factors (e.g., TFE3, TFEB, TFEC) and ideally perform a broader selectivity screen (e.g., a kinome panel or a limited proteome-wide profiling). At minimum, they should acknowledge the limited scope of the selectivity data and temper their claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Translational relevance
- **Claim pointer** "This work indicates a path forward towards the development of therapeutic inhibitors of MITF in the clinic"
- **Evidence pointer** Figures 1 and 2, Discussion
- **Concern** The clinical data analysis (Figure 1) shows that MITF is expressed across a broad range in patient tumors, but the authors do not demonstrate that MITF expression levels correlate with response to therapy or patient outcomes in a statistically robust manner. The analysis appears descriptive rather than hypothesis-driven. The preclinical data show that MITF knockdown affects cell viability, but the effect sizes are modest and the experiments are limited to a small number of cell lines. The xenograft experiment is only briefly mentioned and lacks detail on the magnitude and duration of tumor growth inhibition.
- **Why it matters** The manuscript claims clinical relevance and a path to therapeutic development, but the evidence for MITF as a viable therapeutic target in the context of resistance is not fully established. The clinical data are correlative, and the preclinical data do not demonstrate that the discovered compounds themselves have any effect in disease models.
- **Resolution test** The authors should provide a more rigorous statistical analysis of the clinical data, including survival analysis or multivariate analysis controlling for known prognostic factors. For the preclinical data, they should show that the optimized compounds can inhibit MITF transcriptional activity in cells or affect tumor growth in the xenograft model. If the compounds lack cellular activity, this should be stated explicitly, and the manuscript should be framed as a structural and biophysical study rather than a therapeutic development effort.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic understanding
- **Claim pointer** "NMR experiments and molecular dynamics simulations reveal a dynamic conformational exchange between helices in the asymmetric homodimer, a phenomenon that is perturbed by ligand binding"
- **Evidence pointer** Figures 8 and 9
- **Concern** The MD simulations are used to support a mechanism involving ligand-induced stabilization of a particular conformational state. However, the simulations are performed on a chimeric structure (mouse DBD merged with human bHLH), and the authors do not validate the force field parameters or the simulation protocol against experimental data beyond qualitative agreement with NMR line broadening. The NMR data show line broadening, which is interpreted as intermediate exchange, but the authors do not provide quantitative analysis (e.g., relaxation dispersion) to support the specific mechanism proposed.
- **Why it matters** The proposed mechanism of action is a key novelty of the paper. If the MD simulations are not well-validated, the mechanistic claims are speculative. The line broadening could be due to other factors, such as aggregation or non-specific binding.
- **Resolution test** The authors should provide additional experimental evidence for the proposed mechanism, such as relaxation dispersion NMR experiments to quantify exchange rates, or mutagenesis of residues predicted to be important for the ligand-induced stabilization. They should also validate the MD simulations by comparing predicted and experimental observables (e.g., chemical shift perturbations, NOEs).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "direct targeting of MITF or other basic helix-loop-helix leucine zipper (bHLH-LZ) transcription factors is unprecedented." This is a strong claim that should be qualified, as there may be prior reports of small-molecule binding to other bHLH-LZ proteins, even if not structurally characterized.
- **Required correction** Revise to "to our knowledge, no direct small-molecule ligands for MITF or other bHLH-LZ transcription factors have been reported with structural evidence of binding."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The clinical data in Figure 1 are presented as box plots or similar, but the statistical significance of differences between response groups is not reported in the text or figure legend.
- **Required correction** Add statistical analysis (e.g., Kruskal-Wallis test) and report p-values in the figure legend or text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** MD simulations
- **Evidence pointer** Methods section
- **Issue** The MD simulation methods lack details on the equilibration protocol, the number of atoms in the system, and the total simulation time per replicate. The description of the "swap" analysis is somewhat vague.
- **Required correction** Provide a more detailed description of the simulation setup and analysis, including convergence checks and error estimates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the functional implications of slowed helix exchange is speculative. The authors suggest that this may affect DNA binding or protein-protein interactions, but no data support these hypotheses.
- **Required correction** Either provide supporting data or clearly label these as hypotheses requiring future investigation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The methods for the clinical data analysis (Figure 1) are not described. It is unclear how the patient samples were selected, how MITF expression was quantified, and how response groups were defined.
- **Required correction** Add a subsection describing the clinical data sources, inclusion criteria, and analysis methods.

## Risk / unsupported claims
1. The claim that "targeting the kink pocket may lead to functional MITF inhibition" is not directly supported by any experiment using the discovered compounds. The genetic evidence is indirect and confounded by potential off-target effects of the mutations.
2. The claim of "selectivity of the MITF ligands of at least 100-fold over binding to the DBD of MYF/MAX" is based on a single comparator and may not generalize to other proteins.
3. The statement that "this work sets the basis to further explore pharmacological inhibition of MITF" is reasonable as a forward-looking statement, but the manuscript does not demonstrate that the compounds have any cellular activity or drug-like properties.
4. The clinical relevance of MITF expression levels to therapy response is suggested but not rigorously established with statistical analysis.
5. The MD simulation results are used to support a mechanistic model, but the simulations are not validated against experimental data beyond qualitative agreement, and the specific claim that ligand binding slows helix exchange is not directly measured experimentally.