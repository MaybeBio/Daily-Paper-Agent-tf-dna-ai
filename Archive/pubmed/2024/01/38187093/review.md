## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results and discussion, conclusions, and supplementary figure legends as embedded in the text.
- **Assessment boundary** Scientific validity of the claims as supported by the provided evidence. No assessment of editorial fit or journal-specific policy matters.
- **Shared manuscript claim summary** The authors identify alanine 873 in the transcriptional activator XYR1 of Trichoderma reesei as a novel engineering target based on AlphaFold2-predicted structure. A CRISPR/Cas9-based random mutagenesis approach yielded the A873Y mutant, which shows enhanced lignocellulolytic enzyme production on cellulose and inducer-free (glucose) conditions, outperforming the previously reported V821F mutant. Crude enzymes from the A873Y strain show improved saccharification performance on corn fiber and pretreated corn stover.
- **Visible evidence base** Figures 1–8, supplementary figures S1, supplementary tables S1–S2 (referenced but not provided), methods descriptions for strain construction, enzyme assays, RT-qPCR, saccharification, and molecular dynamics simulations.
- **Missing materials affecting confidence** Supplementary tables S1 and S2 (primer sequences) not provided. Raw numerical data for enzyme activities, qPCR fold changes, and saccharification time courses not provided. Statistical test details (exact P values, number of replicates beyond "triplicate") not fully specified. MD simulation parameters partially described; convergence criteria and replica consistency not reported.

## Reviewer

- **Overall assessment** The manuscript presents a straightforward application of structure-guided mutagenesis to improve lignocellulolytic enzyme production in an industrially relevant fungus. The identification of A873 as a new target and the characterization of the A873Y mutant are potentially useful contributions. However, the mechanistic interpretation is largely speculative, and several quantitative claims lack sufficient statistical and methodological detail to be fully evaluated. The work is competent but incremental, extending known mutational hotspots in XYR1 rather than providing fundamental new insight into the regulatory mechanism.

- **Who would be interested in the results, and why** Researchers in fungal biotechnology and industrial enzymology, particularly those working on Trichoderma reesei or related cellulase-producing fungi. The work may also interest groups applying AlphaFold2-based structure prediction to guide protein engineering in transcription factors. The demonstration of inducer-free enzyme production has practical relevance for cost reduction in lignocellulosic biorefineries.

- **Major Strengths**
  - The use of AlphaFold2-predicted structure to identify a new mutational target is a clear and logical approach, and the structural rationale for selecting A873 is well presented.
  - The CRISPR/Cas9-based saturation mutagenesis strategy is technically sound and represents a useful methodological contribution for this organism.
  - The comparison with the previously reported V821F mutant under identical conditions provides a meaningful benchmark.
  - The saccharification experiments with real lignocellulosic substrates (corn fiber, pretreated corn stover) add practical relevance beyond simple enzyme activity measurements.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and reproducibility
- **Claim pointer** The manuscript claims significant increases in enzyme activities (e.g., 56.7-fold xylanase and 3.3-fold cellulase increases on glucose; 6.7-fold xylanase increase on cellulose) and transcript abundances (e.g., 461-fold xyn2, 636-fold bxl1 increases).
- **Evidence pointer** Figures 3, 4, 5; Statistical analysis section
- **Concern** The statistical analysis section states only that P values were calculated using a one-tailed homoscedastic t-test. No information is provided on the number of biological replicates (the figure legends state "triplicate cultivations" but it is unclear whether these are technical or biological replicates), whether multiple testing corrections were applied, or whether the data met the assumptions of the t-test (e.g., normality, variance homogeneity). The fold-change values are reported without confidence intervals or effect size measures. For the qPCR data, the use of the 2−ΔΔCT method requires validation of amplification efficiency, which is not reported.
- **Why it matters** The central claims of the paper rest on quantitative comparisons between strains. Without adequate statistical reporting, the reader cannot assess the reliability or generalizability of the observed differences. This is particularly important given the large fold-changes reported, which may be inflated by near-zero baseline values in the parent strain.
- **Resolution test** Provide full statistical details: number of independent biological replicates, exact P values, confidence intervals for all reported fold-changes, and confirmation that the t-test assumptions were checked. For qPCR, report amplification efficiencies and include a statement on how the reference gene stability was validated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic interpretation
- **Claim pointer** The manuscript states that "the conformational changes caused by A873Y mutation may affect the above protein-protein interactions and results in constitutive cellulase expression" and that the mutation "caused conflicts and shifting the α-helix 868–884."
- **Evidence pointer** Figure 6; "Possible conformational changes of XYR1 caused by the A873Y mutation" section
- **Concern** The MD simulation results are presented as if they demonstrate a specific conformational pathway, but the methods lack critical details: the initial structure was "refined by MD simulation mentioned above for 50 ns" with a question mark in the text, suggesting uncertainty in the methodology. No information is given on the number of replicas used for the production runs, the convergence of the simulations, the force field validation, or whether the observed differences between wild-type and mutant are statistically significant across replicas. The proposed pathway (A873Y → helix shift → D860 displacement → salt bridge disruption → conformational change) is presented as a coherent narrative but is not tested experimentally. The claim that V821F and A824V would induce "a conformational change similar to A873Y" is purely speculative and not supported by simulation or experimental data.
- **Why it matters** The structural interpretation is a key part of the paper's novelty, but as presented it is not a validated mechanistic model. Overinterpretation of MD simulations without adequate controls or experimental validation weakens the scientific contribution and could mislead future engineering efforts.
- **Resolution test** Provide complete MD simulation details: software version, force field, water model, ion concentration, temperature/pressure coupling, equilibration protocol, production run length, number of replicas, and convergence metrics (e.g., RMSD, RMSF). Show that the observed conformational differences are reproducible across replicas and statistically significant. Alternatively, temper the mechanistic claims and present the MD results as preliminary observations requiring experimental validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of mutagenesis screening
- **Claim pointer** The authors state that "four mutants (A873W, A873Y, A873R, and A873N) were obtained after subsequent strain purification" and that these were tested for enzyme production.
- **Evidence pointer** Figure 2; "CRISPR/Cas9-based mutagenesis identified A873Y as a constitutively active mutant" section
- **Concern** The manuscript does not report how many transformants were screened, what the mutation efficiency was, or whether the four mutants obtained represent the full set of possible amino acid substitutions at position 873. The NNK codon degeneracy encodes 32 codons and 20 amino acids, but only four mutants were recovered. It is unclear whether this reflects the true distribution of mutations or a bias in the screening process. Additionally, the authors state that the effects of mutating A873 to the other 15 residues "are worth being studied in the future," which is appropriate, but the current data do not establish that A873Y is the optimal substitution.
- **Why it matters** The claim that A873Y is a "novel constitutively active mutant" is based on a limited set of substitutions. Without knowing the full mutational landscape at this position, the reader cannot assess whether A873Y is truly the best variant or merely the best among those recovered. This affects the practical utility of the finding.
- **Resolution test** Report the total number of transformants screened, the distribution of amino acid substitutions obtained, and the criteria used to select the four mutants for further characterization. If possible, generate and test additional substitutions at position 873 to establish the optimal amino acid.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of inducer-free production claim
- **Claim pointer** The abstract and conclusions state that the A873Y mutation enables "inducer-free production of lignocellulolytic enzymes" and that enzyme production was "activated under the inducer-free conditions."
- **Evidence pointer** Figure 4; "Inducer-independent expression of lignocellulolytic enzymes in the A873Y mutant" section
- **Concern** The inducer-free experiments were conducted only in glucose medium at a single time point (120 h). The manuscript does not report whether the A873Y mutant also produces enzymes in other repressing carbon sources (e.g., sucrose, glycerol) or whether the effect is glucose-specific. Additionally, the qPCR data in Figure 5B show that at 18 h (when glucose is still present), only bxl1 shows elevated transcript levels, while the other genes are essentially unchanged. This suggests that the "inducer-free" activation is not uniform across all lignocellulolytic enzyme genes and may be time-dependent. The claim of "inducer-free production" is therefore stronger than the evidence supports.
- **Why it matters** The practical value of the A873Y mutant lies in its ability to produce enzymes without inducers, which would reduce production costs. If this effect is limited to glucose or requires glucose exhaustion, the applicability may be narrower than claimed. A more thorough characterization of the inducer-free phenotype is needed.
- **Resolution test** Test the A873Y mutant in multiple repressing carbon sources (e.g., glucose, sucrose, glycerol) at multiple time points. Report enzyme activities and transcript levels for a broader panel of lignocellulolytic enzyme genes. Clarify whether the inducer-free phenotype requires carbon source exhaustion or occurs during active growth.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Materials and methods, "Bioinformatics analyses" section
- **Evidence pointer** "The structure model of XYR1 downloaded from AlphaFold DB [34] and deleted for amino acids 1–319 was first refined by MD simulation mentioned above for 50 ns?"
- **Issue** The question mark at the end of this sentence appears to be an error, and the sentence is grammatically awkward. It is unclear whether the 50 ns refinement was performed or is being questioned.
- **Required correction** Rewrite the sentence to clearly state the simulation protocol, e.g., "The AlphaFold2-predicted structure of XYR1 (residues 320–940) was refined by 50 ns MD simulation prior to production runs."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2B
- **Evidence pointer** Figure 2B shows extracellular protein concentrations for A873 mutants and parent strain.
- **Issue** The figure legend does not specify the time point at which the measurements were taken, nor does it indicate whether the values are normalized to biomass or culture volume. The statistical significance markers are not defined in the legend.
- **Required correction** Add the time point, normalization method, and a clear definition of significance markers to the figure legend.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Materials and methods, "Strain construction" section
- **Evidence pointer** "The transformants obtained from protoplast-mediated transformation were purified, and their genotypes were analyzed by PCR and Sanger sequencing."
- **Issue** The methods do not describe how the A873Y mutation was confirmed to be the only genetic change in the strain, nor whether off-target mutations were assessed. Given the use of CRISPR/Cas9, off-target effects are a potential concern.
- **Required correction** Add a statement on whether off-target mutations were assessed (e.g., by whole-genome sequencing or targeted analysis of predicted off-target sites).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Results and discussion, "Crude enzymes produced by the A873Y mutant showed enhanced performance in lignocellulose degradation" section
- **Evidence pointer** Figures 7 and 8
- **Issue** The saccharification experiments compare crude enzymes at equal protein loading, which is appropriate. However, the manuscript does not discuss whether the improved performance is due to higher enzyme titers, a more favorable enzyme composition, or both. The SDS-PAGE analysis (Figure 3F) suggests compositional differences, but this is not quantitatively analyzed.
- **Required correction** Add a discussion of the potential mechanisms underlying the improved saccharification performance, or acknowledge that the relative contributions of enzyme quantity and composition are not resolved.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** "Mutations of several other amino acid residues around V821 and A824, including T817, E825 and A826, were also reported to increase the production of cellulases and xylanases in T. reesei [18]."
- **Issue** The introduction cites previous mutations but does not provide a comparative summary of their effects relative to the A873Y mutant described here. This would help position the novelty of the current work.
- **Required correction** Add a brief comparison of the performance of previously reported mutants with the A873Y mutant, if such data are available in the literature.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** "The data used to support the findings of this study are available from the corresponding authors upon request."
- **Issue** The data availability statement is vague. For a study of this nature, deposition of key datasets (e.g., MD simulation trajectories, raw qPCR data) in a public repository would be expected.
- **Required correction** Specify what data are available and where they can be accessed, or deposit the data in a public repository.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Inadequate statistical reporting for all quantitative comparisons.
  - R1-M2: Insufficient methodological detail for MD simulations to support the mechanistic claims.
  - R1-M3: Incomplete reporting of the mutagenesis screen, limiting the claim that A873Y is the optimal substitution.

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The application of AlphaFold2-guided mutagenesis to a fungal transcription factor is relatively novel, but the concept of constitutively active XYR1 mutants is already established (V821F, A824V). The A873Y mutant is a new addition to a known class rather than a fundamentally new approach.
  - **Scientific importance** Moderate. The work has practical relevance for industrial enzyme production, but the mechanistic insight is limited. The finding that a single point mutation can enhance enzyme production is useful but does not fundamentally advance understanding of XYR1 regulation.
  - **Interdisciplinary readership** Limited. The work is primarily of interest to fungal biotechnologists and enzyme production researchers. The structural and MD components are not developed sufficiently to attract a broader structural biology audience.
  - **Technical soundness** The experimental approaches are generally sound, but the statistical reporting and MD simulation details are insufficient to fully evaluate the claims. The lack of raw data and detailed methods weakens the technical foundation.
  - **Readability for nonspecialists** The manuscript is generally readable, but the MD simulation section and the discussion of conformational changes may be difficult for nonspecialists to follow. The writing is clear overall, with a few grammatical errors (e.g., the question mark in the methods section).

- **Recommendation posture** Supportive if technical concerns are resolved. The core finding, that A873Y is a novel constitutively active XYR1 mutant with practical utility, is potentially valuable. However, the manuscript requires substantial revision to address the statistical reporting, MD simulation methodology, and completeness of the mutagenesis screen before the claims can be fully accepted.

## Risk / unsupported claims
- The claim that A873Y is a "novel constitutively active mutant" is only supported for the four substitutions tested (A873W, A873Y, A873R, A873N), not for all possible amino acid substitutions at this position.
- The proposed conformational mechanism (A873Y → helix shift → D860 displacement → salt bridge disruption) is not experimentally validated and is based on a single MD simulation protocol with incomplete methodological reporting.
- The claim that the A873Y mutation "results in constitutive cellulase expression" is not directly demonstrated; the data show increased enzyme production in glucose medium, but the term "constitutive" implies a specific regulatory mechanism that is not established.
- The statement that "the effects of A873Y on lignocellulolytic enzyme expression are condition-dependent" is based on limited time points and carbon sources and requires broader testing.
- The comparison of A873Y with V821F is presented as a key finding, but the manuscript does not report statistical comparisons between these two mutants, only between each mutant and the parent strain.