## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report a computational strategy for de novo design of a nonnatural transcription factor (DLA) by combining prokaryotic LexA, a truncated progesterone receptor LBD, and prokaryotic B42. Molecular dynamics simulations predicted that progesterone binding to the LBD shortens the DBD-AD distance, enabling transcriptional activation. A yeast biosensor using DLA to control GFP expression achieved an EC50 of 27 µg/L, a working range of 0.16-60 µg/L, and a detection time of 2.5 h. A low-cost kit for clinical progesterone detection was developed.
- **Visible evidence base** Abstract text only; no experimental details, simulation parameters, statistical analyses, or validation data are provided
- **Missing materials affecting confidence** Full methods, simulation trajectories and convergence criteria, experimental characterization of DLA (expression, stability, specificity), dose-response data, negative controls, cross-reactivity tests, kit performance metrics, and any comparison with existing biosensors

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially impactful strategy for engineering nonnatural transcription factors via structure-based design. The core concept, using conformational dynamics to guide domain fusion, is intellectually appealing. However, the evidence provided is insufficient to establish that DLA functions as claimed. Key quantitative results are stated without supporting data, and critical controls (e.g., specificity against related steroids, reproducibility, and kit validation) are absent. The work may be of interest to synthetic biologists and biosensor developers, but the current abstract does not substantiate the central claims.
- **Who would be interested in the results, and why** Researchers in synthetic biology, protein engineering, and biosensor development would be interested because the strategy offers a generalizable route to create transcription factors for nonnatural or poorly characterized ligands. Clinicians and point-of-care diagnostics developers might also find the progesterone detection kit relevant, though its validation is not shown.
- **Major strengths** The de novo design approach is conceptually novel, moving beyond natural TF discovery. The use of molecular dynamics to guide domain selection and fusion is a rational, mechanistically informed strategy. The reported performance metrics (EC50, working range, detection time) suggest practical utility, if reproducible.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (simulation evidence), R1-M2 (specificity), R1-M3 (quantitative data), R1-M4 (kit validation)
- **Assessment against Nature-style criteria** Originality is high, as the approach is not a simple repurposing of known TFs. Scientific importance is moderate to high, given the potential for generalizable biosensor design. Interdisciplinary readership is plausible, spanning protein engineering, computational biology, and diagnostics. Technical soundness cannot be assessed from the abstract alone, as no methods or raw data are provided. Readability for nonspecialists is adequate, though the abstract assumes familiarity with TF architecture and yeast reporter systems. Overall, the work is promising but not yet established from the supplied material.
- **Recommendation posture** Supportive if technical concerns are resolved; currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that molecular dynamics simulations predicted a shortening of the DBD-AD distance after progesterone binding, which was used to design DLA.
- **Evidence pointer** Abstract text; location not provided
- **Concern** No simulation details are given, including force field, simulation length, sampling method, convergence, or replicate runs. The claim that a specific conformational change (distance shortening) is robustly predicted cannot be evaluated.
- **Why it matters** The entire design rationale rests on this computational prediction. If the simulation is under-sampled or biased, the designed DLA may not function as intended, undermining the core claim.
- **Resolution test** Provide simulation methods, convergence metrics, and replicate analyses showing that the distance change is statistically significant and reproducible across independent runs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The abstract states that the biosensor is "progesterone-specific," implying no cross-reactivity with other steroids.
- **Evidence pointer** Abstract text; location not provided
- **Concern** No data on specificity are presented. Progesterone is structurally similar to other steroids (e.g., testosterone, cortisol, estradiol), and the truncated LBD may bind these with appreciable affinity. Without cross-reactivity tests, the specificity claim is unsupported.
- **Why it matters** Specificity is a critical performance criterion for any biosensor, especially in clinical samples where interfering steroids are present. Overstated specificity could mislead potential users.
- **Resolution test** Include dose-response curves for at least 5-10 structurally related steroids and demonstrate that the response is significantly lower than for progesterone at relevant concentrations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract reports an EC50 of 27 µg/L, a working range of 0.16-60 µg/L, and a detection time of 2.5 h.
- **Evidence pointer** Abstract text; location not provided
- **Concern** These quantitative metrics are stated without any indication of sample size, error bars, or statistical analysis. It is unclear whether these values are from a single experiment or multiple replicates, and no confidence intervals are provided.
- **Why it matters** Reproducibility and precision are essential for a biosensor to be useful. Without error estimates, the reliability of these metrics cannot be assessed.
- **Resolution test** Provide mean and standard deviation (or confidence intervals) from at least three independent experiments, and describe the fitting method used to derive EC50 and working range.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The abstract claims that a "low-cost, user-friendly kit was developed for the rapid detection of progesterone in the clinic."
- **Evidence pointer** Abstract text; location not provided
- **Concern** No details are given on the kit's components, storage stability, shelf life, or validation in clinical samples (e.g., serum or urine). The claim of clinical utility is premature without such data.
- **Why it matters** A kit intended for clinical use must meet regulatory and practical standards, including accuracy against reference methods and robustness under real-world conditions. The abstract does not support this claim.
- **Resolution test** Provide kit validation data, including recovery rates in spiked clinical matrices, comparison with a gold-standard method (e.g., LC-MS or immunoassay), and stability tests over a defined period.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract uses abbreviations (DLA, LBD, DBD, AD) without defining them at first use, which may hinder readers unfamiliar with TF architecture.
- **Required correction** Define all abbreviations in full at first mention, e.g., "DNA-binding domain (DBD)".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states that "prokaryotic LexA, a truncated LBD from the progesterone receptor, and prokaryotic B42 together constitute DLA," but does not explain how these components are physically linked or whether the fusion was validated for expression and folding.
- **Required correction** Briefly describe the fusion architecture (e.g., linkers, order of domains) and state that expression and structural integrity were confirmed experimentally.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract claims the strategy is generalizable ("can also be used to develop a variety of other biosensors") but provides no evidence for transferability to other ligands or receptors.
- **Required correction** Soften the claim to "may be applicable" and, if possible, cite a proof-of-concept with a second ligand in the full text.

## Risk / unsupported claims
- The claim that DLA functions as a transcription factor is unsupported without experimental evidence of transcriptional activation (e.g., reporter assays with proper controls).
- The claim of progesterone specificity is unsupported without cross-reactivity data.
- The quantitative performance metrics (EC50, working range, detection time) are unsupported without statistical details.
- The claim of clinical utility for the kit is unsupported without validation in clinical samples.
- The generalizability of the strategy to other biosensors is unsupported and speculative.