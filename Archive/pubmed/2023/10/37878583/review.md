## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract, without access to full methods, figures, or supplementary data
- **Shared manuscript claim summary** The authors identify a 25-nucleotide G-rich sequence in the SMO oncogene promoter, confirm formation of a parallel G-quadruplex (SMO1-GQ) via biophysical and biochemical assays, show primate conservation, characterize interactions with ligands TMPyP4 and BRACO-19, perform structural characterization via DMS footprinting and computational methods, and present ChIP evidence that the element binds multiple transcription factors, proposing SMO1-GQ as a master regulator of SMO transcription and a druggable anti-cancer target.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or supplementary information provided
- **Missing materials affecting confidence** Full manuscript, experimental protocols, raw data, statistical analyses, structural coordinates, ChIP details, and validation controls

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting finding regarding a G-quadruplex in the SMO promoter and its proposed regulatory role. However, the evidence as summarized is insufficient to substantiate the strong claims of "master regulator" status and druggable target potential. The abstract lacks quantitative data, control details, and methodological transparency, making the central conclusions currently not established from the provided material.
- **Who would be interested in the results, and why** Researchers in G-quadruplex biology, transcriptional regulation, oncogene promoter structure, and targeted cancer therapeutics would find the topic relevant. The potential link between a promoter G-quadruplex and SMO oncogene regulation could interest those studying hedgehog signaling and drug development.
- **Major strengths** The study addresses a relevant oncogene and combines multiple experimental approaches, including biophysical, biochemical, computational, and in vivo methods. The identification of a conserved G-rich element and its interaction with known GQ ligands provides a foundation for further investigation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that SMO1-GQ is the "master regulator of SMO1 transcriptional activity" based on ChIP data showing binding of five transcription factors.
  - **Evidence pointer** ChIP assay, location not provided
  - **Concern** The abstract states that ChIP revealed the element functions as a scaffold for five transcription factors, but no quantitative data, enrichment values, or negative controls are described. The term "master regulator" implies a dominant and causal role, which cannot be established from binding alone without functional perturbation experiments such as mutagenesis, knockdown, or reporter assays.
  - **Why it matters** Overstating regulatory hierarchy from correlative binding data could mislead the field and overstate the therapeutic relevance. A "master regulator" claim requires demonstration of functional necessity and sufficiency, not just occupancy.
  - **Resolution test** Provide ChIP enrichment values relative to controls, show that mutation or deletion of the GQ element alters SMO transcription in reporter or endogenous contexts, and demonstrate that loss of individual transcription factor binding reduces SMO expression.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical validation
  - **Claim pointer** The abstract claims "comparatively higher stable interaction of BRACO-19 with SMO1-GQ" and that this "contemplates the potential of the G quadruplex as a promising anti-cancer druggable target."
  - **Evidence pointer** Spectroscopic and in silico analysis, location not provided
  - **Concern** No binding affinities, thermodynamic parameters, or comparative metrics are provided. The claim of higher stability for BRACO-19 is qualitative. Moreover, extrapolating from in vitro ligand binding to "anti-cancer druggable target" potential requires cellular or in vivo efficacy data, which are absent.
  - **Why it matters** Without quantitative binding data and functional validation in cellular models, the therapeutic claim is speculative. The field requires evidence that ligand binding translates to transcriptional downregulation and phenotypic effects.
  - **Resolution test** Report dissociation constants or comparable binding metrics for both ligands, and include cellular assays showing BRACO-19 or TMPyP4 treatment reduces SMO expression and cancer cell viability in a GQ-dependent manner.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Structural evidence
  - **Claim pointer** The abstract claims "structural characterisation of the SMO1-GQ using DMS footprinting assay and molecular modelling, docking, and MD simulation to identify the probable atomic regions."
  - **Evidence pointer** DMS footprinting and computational methods, location not provided
  - **Concern** DMS footprinting provides nucleotide-level protection patterns but does not yield a high-resolution structure. Molecular modelling and MD simulation are predictive and require experimental validation. The abstract does not specify the resolution of the structural model, the force fields used, or whether the model was validated against experimental constraints beyond DMS.
  - **Why it matters** The stated goal of "detailed molecular anatomy" for rational drug design requires a reliable structural model. Overclaiming structural characterization from low-resolution and computational data could undermine confidence in downstream docking results.
  - **Resolution test** Provide the structural model with validation metrics, such as comparison to experimental restraints, and clarify the resolution limits. If possible, include NMR or crystallographic data, or clearly state the model is a prediction.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Conservation claim
  - **Evidence pointer** "SMO1-GQ is highly conserved in primates," location not provided
  - **Issue** The abstract does not specify the alignment method, the number of primate species analyzed, or the conservation metric used.
  - **Required correction** Specify the species set, alignment tool, and conservation threshold, and provide a supplementary alignment figure.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Nomenclature
  - **Affected element** GQ naming
  - **Evidence pointer** "SMO1-GQ" and "SMO1-P1 G-quadruplex," location not provided
  - **Issue** The abstract uses two different names for the same element, which could confuse readers.
  - **Required correction** Use a single consistent name throughout the manuscript and abstract.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** Assay description
  - **Evidence pointer** "array of biophysical and biochemical assays," location not provided
  - **Issue** The abstract does not list which assays were performed to confirm GQ formation, such as CD, UV melting, or PAGE.
  - **Required correction** Briefly enumerate the key assays in the abstract or refer to a methods figure.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The core claims of master regulation, druggable potential, and structural characterization are not supported by the abstract-level evidence.
- **Assessment against Nature-style criteria** Originality is moderate, as G-quadruplexes in oncogene promoters are a known theme, though the SMO promoter context may be novel. Scientific importance is potentially high given SMO's role in cancer, but the evidence does not yet establish a significant advance. Interdisciplinary readership is plausible, spanning structural biology, transcription, and drug discovery, but the abstract lacks the depth needed for broad appeal. Technical soundness cannot be fully assessed from the abstract, but the described methods are appropriate in principle, with concerns about validation. Readability for nonspecialists is acceptable, though the abstract uses jargon without sufficient context.
- **Recommendation posture** Currently not established from the provided evidence. The authors should provide full experimental details, quantitative data, and functional validation to support the major claims. If the full manuscript addresses these gaps, the work could be reconsidered.

## Risk / unsupported claims

- The claim that SMO1-GQ is a "master regulator" of SMO1 transcriptional activity is unsupported without functional perturbation data.
- The claim of "promising anti-cancer druggable target" is unsupported without cellular or in vivo efficacy data.
- The claim of "structural characterisation" is overstated given the reliance on DMS footprinting and computational modeling without high-resolution experimental validation.
- The relative binding stability of BRACO-19 versus TMPyP4 is unquantified and therefore not assessable.
- The conservation claim is not verifiable without alignment details.