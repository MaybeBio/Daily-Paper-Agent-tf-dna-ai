## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose that, despite high sequence and structural similarity between LXRalpha and LXRbeta, the two isotypes exhibit distinct protein dynamics that can be detected through molecular dynamics simulations. They further claim that these dynamic differences are traceable to distinct structural and/or dynamical features inherited from an ancestral vertebrate LXR, and that such differences may inform isoform-specific modulator design.
- **Visible evidence base** Abstract text only; no quantitative results, simulation details, statistical analyses, or structural comparisons are available
- **Missing materials affecting confidence** Full manuscript, methods section, simulation parameters, force field choices, convergence criteria, all figures and tables, ancestral sequence reconstruction details, and any statistical validation

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting hypothesis, namely that dynamic differences, rather than static structural differences, distinguish LXRalpha and LXRbeta. However, the current abstract provides insufficient evidence to evaluate the validity of the central claims. Key methodological details, quantitative outcomes, and validation of the ancestral reconstruction are absent. The claim that dynamic differences are inherited from an ancestral receptor is particularly under-supported without phylogenetic or functional data. The work may be of interest to the nuclear receptor and drug design communities, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in nuclear receptor biology, structural biophysics, and computational drug discovery would be interested. The potential to exploit dynamic differences for isoform-selective modulation of LXR has direct therapeutic relevance for cholesterol metabolism and metabolic disease. Additionally, the use of ancestral sequence reconstruction to interpret modern isoform dynamics may appeal to evolutionary biochemists.
- **Major strengths** The hypothesis is clearly framed and addresses a genuine gap in the field, namely how ligands distinguish between highly homologous LXR isoforms. The use of a library of 27 oxysterols is a reasonable approach to probe ligand-dependent dynamics. The integration of ancestral sequence reconstruction is an innovative angle that could provide evolutionary context for functional divergence.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract lacks any quantitative evidence for the claimed dynamic differences. No metrics such as root-mean-square fluctuation differences, contact map changes, or allosteric pathway analyses are reported. The ancestral reconstruction is mentioned but not described or validated. Without these, the central claims are not testable from the provided material.
- **Assessment against Nature-style criteria** 
  - Originality: The idea of using dynamics rather than static structure to distinguish LXR isoforms is not entirely novel in the nuclear receptor field, but the combination with ancestral reconstruction adds an original element. However, originality alone is insufficient without robust evidence.
  - Scientific importance: The question of isoform-specific LXR modulation is clinically relevant, and a clear mechanistic answer would be valuable. The importance is moderate to high, but the abstract does not yet demonstrate that such an answer is provided.
  - Interdisciplinary readership: The work bridges structural biology, computational biophysics, and pharmacology, which could attract a broad readership. However, the abstract is written in a way that assumes familiarity with molecular dynamics and nuclear receptor biology, which may limit accessibility.
  - Technical soundness: Cannot be assessed from the abstract. No methodological details or validation are provided.
  - Readability for nonspecialists: The abstract is concise but uses jargon such as "allosteric signaling" and "ancestral vertebrate LXR" without sufficient context. It is readable for specialists but not for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and the approach is reasonable, but the abstract does not provide enough quantitative or methodological detail to support the claims. A revised version with full methods, results, and validation would be needed for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "the dynamic behavior of the receptors is distinct and can reveal fundamental differences between the isoforms" and that they "quickly identify stability differences linked to subtle changes in secondary structure and inter-residue contacts."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract states that stability differences were identified but provides no quantitative data, such as numerical values for fluctuations, contact persistence, or free energy estimates. No comparison between isoforms is shown, and no statistical significance is reported.
- **Why it matters** Without quantitative evidence, the reader cannot assess the magnitude or reliability of the claimed dynamic differences. The central premise of the paper depends on demonstrating that these differences are robust and reproducible, not merely anecdotal.
- **Resolution test** Provide specific metrics, such as per-residue root-mean-square fluctuation differences, contact map overlap scores, or principal component analysis projections, with error bars and statistical tests comparing LXRalpha and LXRbeta across the oxysterol library.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that they used "molecular dynamics simulations on a library of 27 oxysterols" and "reconstructed sequence of ancestral vertebrate LXR."
- **Evidence pointer** Abstract only; location not provided
- **Concern** No details are given on simulation length, force field, water model, temperature coupling, equilibration protocol, or convergence criteria. The ancestral reconstruction method is not described, and no measure of reconstruction confidence, such as posterior probabilities, is mentioned.
- **Why it matters** Molecular dynamics results are highly sensitive to simulation parameters and convergence. Without this information, the reproducibility of the results is questionable. Similarly, ancestral reconstruction requires rigorous statistical support to be credible.
- **Resolution test** Include a methods section that specifies all simulation parameters and convergence checks. For the ancestral reconstruction, report the alignment, phylogenetic tree, model of sequence evolution, and posterior probabilities for the reconstructed nodes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim that "both receptors inherited distinct structural and/or dynamical features of the ancestor which underlie their dynamic differences."
- **Evidence pointer** Abstract only; location not provided
- **Concern** This is a causal evolutionary claim that requires direct comparison between the ancestral sequence and each modern isoform. The abstract does not describe how the ancestral dynamics were simulated or how the inheritance was traced. No data are shown to support the link between ancestral features and modern isoform differences.
- **Why it matters** This claim is a key novelty of the paper. If unsupported, it reduces the paper to a descriptive comparison of dynamics, which is less impactful. The evolutionary interpretation requires explicit evidence that the ancestral state is closer to one or both modern isoforms in specific dynamic features.
- **Resolution test** Provide a comparative analysis of ancestral versus modern dynamics, such as correlation of fluctuation profiles or contact patterns, with statistical measures of similarity. Show that the ancestral features are differentially retained in LXRalpha versus LXRbeta.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, sentence "We quickly identify stability differences"
- **Issue** The word "quickly" is informal and does not convey scientific rigor. It is unclear whether it refers to computational speed or ease of detection.
- **Required correction** Replace with a more precise phrase, such as "We identify robust stability differences" or "We detect consistent stability differences."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Abstract background
- **Evidence pointer** Abstract, first two sentences
- **Issue** The abstract states that LXRalpha and LXRbeta have "nearly identical structures and binding pockets" but does not quantify this similarity. A brief mention of sequence identity percentage would strengthen the context.
- **Required correction** Add a specific value, such as "sharing approximately 78% sequence identity in the ligand binding domain," if accurate, to give readers a concrete sense of the homology.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract, "allosteric signaling"
- **Evidence pointer** Abstract, sentence "we compare dynamic contacts, fluctuations and allosteric signaling"
- **Issue** The term "allosteric signaling" is used without definition or indication of how it was measured. It may be interpreted as a qualitative concept rather than a quantitative output.
- **Required correction** Specify the method used to assess allosteric signaling, such as dynamic network analysis or mutual information, or rephrase to "allosteric communication pathways."

## Risk / unsupported claims
- The claim that dynamic differences are inherited from an ancestral LXR is unsupported in the abstract, as no ancestral reconstruction details or comparative dynamics are provided.
- The claim that stability differences are "linked to subtle changes in secondary structure and inter-residue contacts" is unsupported without specific structural or contact data.
- The overall implication that these dynamic differences can inform isoform-specific modulator design is plausible but not demonstrated, as no functional or ligand selectivity data are presented.
- The abstract's assertion that the two isoforms have "nearly identical structures and binding pockets" is presented without quantitative support, though this is likely well-established in the literature; however, it is not verifiable from the supplied material.