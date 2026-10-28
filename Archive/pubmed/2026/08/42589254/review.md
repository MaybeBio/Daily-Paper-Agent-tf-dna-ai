## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Biochemical and structural characterization of three AAG SNP variants, including thermal stability, DNA binding, glycosylase activity, and molecular dynamics simulations
- **Shared manuscript claim summary** Three tumor-associated AAG SNPs (P94L, V158M, E293K) destabilize the enzyme, retain near-WT DNA binding, but show substrate-specific loss of catalytic activity, with P94L inactive against both εA and Hx, V158M active only against εA, and E293K active only against Hx
- **Visible evidence base** Full text including abstract, introduction, results and discussion, materials and methods, conclusions; figures and tables referenced but not provided
- **Missing materials affecting confidence** Figures 1-9 and Tables 1-5 are referenced but not included; raw gel images, MD trajectory analyses, and statistical details are not available; no supplementary information provided

## Reviewer
- **Overall assessment** The manuscript addresses an important question regarding the functional impact of tumor-associated SNPs in human AAG, a key DNA repair enzyme. The finding that non-active-site variants can qualitatively reprogram substrate specificity is potentially significant. However, the evidence as presented is incomplete. The central claims rest on biochemical assays and MD simulations, but the actual data (figures, tables) are not available for inspection. The differential activity pattern is striking but requires rigorous quantitative support, including replicates, error analysis, and appropriate statistical testing. The MD simulations are described in reasonable detail but the connection between simulated structural changes and observed biochemical outcomes is largely qualitative. The manuscript is clearly written and the conceptual framing is sound, but the current evidence base is insufficient to fully establish the claims.

- **Who would be interested in the results, and why** Researchers in DNA repair, cancer genetics, and pharmacogenomics would be interested. The work addresses whether common SNPs in AAG, a clinically relevant enzyme, can alter substrate specificity, which has implications for cancer risk stratification and predicting response to alkylating chemotherapy. The finding that different variants show opposite substrate preferences is conceptually novel and could inform inhibitor design. The proposed experimental pipeline for functional SNP screening may also be of interest to the broader genome-to-phenotype community.

- **Major strengths** The study addresses a clinically relevant and understudied question. The choice of three variants with predicted deleterious effects, found in tumor databases, is well justified. The combination of biochemical assays and MD simulations is appropriate. The finding of substrate-specific inactivation, rather than a general loss of function, is potentially important and non-obvious. The authors are appropriately cautious about the limitations of in vitro data and in silico predictions.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence completeness
  - **Claim pointer** "All three mutations reduce the protein's melting temperature by 7-10 °C compared to the WT" and "the P94L, V158M, and E293K variants retain their ability to bind to damaged DNA containing either εA or Hx residues, with dissociation constants Kd close to those of the WT AAG"
  - **Evidence pointer** Figure 2, Table 1, Figure 5, Figure 6, Table 2; location not provided
  - **Concern** The actual data supporting the thermal stability and DNA binding claims are not available. The figures and tables are referenced but not included in the provided material. Without the raw melting curves, binding isotherms, and fitted parameters with errors, the claims of "7-10 °C reduction" and "Kd close to WT" cannot be independently assessed. The number of replicates, statistical treatment, and quality of fits are unknown.
  - **Why it matters** These measurements are foundational to the entire manuscript. If the stability or binding data are not robust, the interpretation of the activity differences becomes unreliable. The claim that binding is retained while activity is lost is central to the argument that these variants affect catalysis specifically, not substrate recognition.
  - **Resolution test** Provide the actual figures and tables with error bars, replicate numbers, and statistical comparisons. Show representative raw data and fitted curves. Report mean ± SD or SEM for all parameters.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Quantitative support for activity claims
  - **Claim pointer** "P94L was inactive against both εA and Hx; V158M retained activity against εA but lost activity against Hx; and E293K was active against Hx but inactive against εA"
  - **Evidence pointer** Figure 7, Figure 8, Table 3; location not provided
  - **Concern** The central claim of substrate-specific inactivation is based on activity assays shown in Figure 7 and quantified in Figure 8 and Table 3, none of which are available. The threshold for "inactive" is not defined. The observed rate constants kobs are reported in Table 3 but the values, errors, and statistical comparisons are not visible. It is unclear whether "inactive" means no detectable activity above background, or activity below an arbitrary cutoff. The time courses and extents of conversion are not shown.
  - **Why it matters** The differential activity pattern is the main novel finding. If the activity measurements are not rigorously quantified and compared, the claim of substrate-specific inactivation is not established. The distinction between complete loss of activity and reduced activity is critical for the interpretation.
  - **Resolution test** Provide the activity data with full quantitative detail: time courses, product yields, kobs values with errors, limits of detection, and statistical comparisons between variants and substrates. Define the criteria for "inactive" and show that the assay can detect low levels of activity.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** MD simulation robustness
  - **Claim pointer** "MD simulations revealed that P94L alters the flexible R138-T143 loop, V158M narrows the active site cleft, and E293K disrupts a C-terminal salt bridge while increasing DNA engagement by the positively charged tail"
  - **Evidence pointer** Figure 3, Figure 4, Section 3.6; location not provided
  - **Concern** The MD simulation results are described qualitatively. The specific metrics used to support claims of "narrowing" of the active site cleft, "alteration" of the loop, and "increased DNA engagement" are not defined. The figures showing these structural changes are not available. The number of replicates, convergence criteria, and error estimates for the simulation-derived quantities are not reported. The relationship between the simulated structural changes and the observed biochemical outcomes is inferred but not quantitatively demonstrated.
  - **Why it matters** The MD simulations are used to provide mechanistic explanations for the biochemical observations. If the simulation analyses are not rigorous and quantitative, the proposed mechanisms remain speculative. The claim that specific structural changes cause specific functional outcomes requires a clear chain of evidence.
  - **Resolution test** Provide quantitative metrics from the simulations (e.g., distances, RMSD, contact maps) with error estimates across replicate simulations. Show that the observed differences between WT and variants are statistically significant. Clarify how the simulated structural changes relate to the biochemical activity data.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of substrate-specificity claim
  - **Claim pointer** "These findings demonstrate that non-active-site SNPs can qualitatively reprogram the substrate specificity of AAG"
  - **Evidence pointer** Section 2.3, Section 4; location not provided
  - **Concern** The claim of "qualitative reprogramming" is based on only two substrates (εA and Hx). AAG processes a broader range of substrates, including 3-methyladenine and 7-methylguanine. It is unclear whether the observed substrate specificity changes are specific to εA versus Hx, or whether they reflect a more general alteration in substrate preference. Without testing additional substrates, the claim of "qualitative reprogramming" may be overstated.
  - **Why it matters** The broader significance of the work depends on whether the observed substrate-specific effects are general or limited to the two substrates tested. If the effects are substrate-specific, the implications for cancer risk and chemotherapy response may be more limited.
  - **Resolution test** Test additional AAG substrates, or temper the claim to reflect the limited substrate range tested. Alternatively, provide a mechanistic argument based on the structural data that explains why the observed specificity changes would be general.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Sections 2.1-2.3
  - **Evidence pointer** Tables 1-3; location not provided
  - **Issue** The number of independent replicates for each assay is not stated. Error bars and statistical significance are not reported in the text.
  - **Required correction** Report the number of replicates, mean ± SD or SEM, and the statistical tests used for comparisons between WT and variants.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** Section 3.4
  - **Evidence pointer** Section 3.4; location not provided
  - **Issue** The EMSA method reports multiple shifted bands for some variants, but the interpretation of these bands is not discussed. It is unclear whether they represent different stoichiometries or conformations.
  - **Required correction** Clarify the nature of the multiple bands and how they were treated in the Kd calculation.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Simulation validation
  - **Affected element** Section 3.6
  - **Evidence pointer** Section 3.6; location not provided
  - **Issue** The MD simulation force field parameters for the modified bases (εA and Hx) are cited to references [57,58], but the validation of these parameters in the context of AAG is not discussed.
  - **Required correction** Briefly describe how the parameters were validated or note any limitations.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clinical relevance framing
  - **Affected element** Section 4
  - **Evidence pointer** Section 4; location not provided
  - **Issue** The conclusion states these variants "could be considered as potential biomarkers," but no data on allele frequencies in patient populations or functional impact in cellular contexts are provided.
  - **Required correction** Soften the biomarker claim or clearly state that this is speculative and requires further validation.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Terminology consistency
  - **Affected element** Throughout
  - **Evidence pointer** Abstract, Section 2.1, Section 4; location not provided
  - **Issue** The terms "inactive," "loss of activity," and "unable to remove" are used interchangeably. The quantitative threshold for these terms is not defined.
  - **Required correction** Define the threshold for "inactive" and use consistent terminology throughout.

## Risk / unsupported claims
- The claim that P94L, V158M, and E293K are "tumor-associated" is supported only by database citations, not by direct evidence presented in this manuscript.
- The claim that these variants "could be considered as potential functional biomarkers for cancer risk and response to alkylating chemotherapy" is speculative and not supported by any clinical or cellular data in the manuscript.
- The claim that "non-active-site SNPs can qualitatively reprogram the substrate specificity of AAG" is based on only two substrates and requires additional evidence to be fully supported.
- The mechanistic explanations derived from MD simulations are not quantitatively supported in the provided text.
- The statement that "these variants have been found to be common in various types tumors" is not supported by data presented in this manuscript; the cited databases are not described in sufficient detail.