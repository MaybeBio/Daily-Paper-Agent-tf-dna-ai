## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract, without access to full methods, figures, or supplementary data
- **Shared manuscript claim summary** The authors report that CSB interacts with SNM1A via specific domains, that CSB stimulates SNM1A nuclease activity on model substrates including ICL-containing DNA, that AlphaFold3 models map the interaction interface, and that the CSB C-terminal region is a novel DNA binding domain. They further suggest that targeting this protein-protein interaction may be a therapeutic strategy.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, experimental methods, all figures and tables, statistical analyses, AlphaFold3 model details, and any control experiments

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting mechanistic finding regarding the CSB-SNM1A interaction in ICL repair. However, the evidence base is limited to the abstract, and several claims require detailed experimental validation that cannot be assessed from the provided material. The work may be of interest to the DNA repair community, but the strength of the conclusions cannot be fully evaluated without the full manuscript.
- **Who would be interested in the results, and why** Researchers studying DNA repair mechanisms, particularly interstrand crosslink repair and transcription-coupled repair. The work may also interest structural biologists using AlphaFold for protein-protein interaction studies, and those exploring alternative therapeutic strategies targeting protein-protein interactions in nuclease-driven pathways.
- **Major strengths** The abstract identifies a specific and testable molecular interaction with domain-level resolution. The use of purified proteins and in vitro substrates suggests a biochemical approach. The combination of computational modeling with experimental confirmation is a constructive strategy. The potential therapeutic implication is clearly stated.
- **Major Concerns** The abstract makes several strong claims that require detailed evidence not visible here. The AlphaFold3-based mapping is presented as definitive, but the accuracy of such models for this interaction is not established. The claim that CSB stimulates digestion through ICLs in vitro is central but lacks quantitative or comparative detail. The therapeutic suggestion is speculative and not supported by any efficacy data.
- **Minor Comments** The abstract would benefit from clarifying the distinction between binding affinity and functional stimulation. The phrase "two copies of the C-terminal domain of CSB are necessary" is ambiguous regarding whether this refers to a dimer or two separate domains. The novelty of the "novel DNA binding region" claim should be contextualized against prior CSB DNA binding studies.
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient detail to assess the rigor of the biochemical assays, the statistical treatment of stimulation data, or the validation of AlphaFold3 predictions. Without these, the core claims remain plausible but unverified.
- **Assessment against Nature-style criteria** Originality: The interaction between CSB and SNM1A has been previously suggested, so the novelty lies in the mechanistic detail, which is moderate. Scientific importance: The work addresses a relevant DNA repair pathway, but the broader significance beyond the specialist community is not clearly demonstrated. Interdisciplinary readership: The abstract is likely to appeal mainly to DNA repair specialists, with limited cross-disciplinary reach. Technical soundness: Cannot be assessed from the abstract alone; the reliance on AlphaFold3 without experimental structure validation is a concern. Readability for nonspecialists: The abstract is dense and assumes familiarity with multiple domain names and repair pathways, limiting accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved, but currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "CSB stimulates SNM1A nuclease activity on varied model DNA repair intermediate substrates" and "CSB was observed to stimulate digestion through ICLs in vitro"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract claims stimulation of nuclease activity on multiple substrates and specifically through ICLs, but no quantitative data, reaction conditions, enzyme concentrations, or comparison to controls are provided. The magnitude of stimulation, its substrate dependence, and whether it is specific to CSB or shared by other proteins are not described.
- **Why it matters** The central functional claim of the paper rests on this stimulation. Without detailed kinetic or endpoint data, the reader cannot judge whether the effect is robust, specific, or biologically meaningful. Overstated functional claims without supporting numbers are a common source of irreproducibility.
- **Resolution test** Provide dose-response curves for CSB stimulation of SNM1A on each substrate, include negative controls with a non-interacting protein or a CSB mutant lacking the SNM1A-binding domain, and show statistical analysis of at least three independent replicates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** "AlphaFold3 models of CSB constructs complexed with the SNM1A catalytic domain enabled mapping of the molecular contacts required for the CSB-SNM1A interaction"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract presents AlphaFold3 predictions as a basis for mapping molecular contacts and identifying specific protein-protein interactions that were then confirmed experimentally. However, AlphaFold3 accuracy for multi-domain complexes involving intrinsically disordered regions or induced-fit binding is variable. The abstract does not state whether the models were validated by any orthogonal structural method, such as crosslinking, mutagenesis scanning, or hydrogen-deuterium exchange.
- **Why it matters** If the AlphaFold3 models are inaccurate, the "specific protein-protein interactions" identified and confirmed may be coincidental or incomplete. The claim that the interaction interface is understood at molecular resolution is a strong statement that requires structural or biophysical corroboration.
- **Resolution test** Provide experimental validation of the predicted interface, such as alanine-scanning mutagenesis of the predicted contact residues with binding and activity assays, or a low-resolution structural method like crosslinking mass spectrometry. State the AlphaFold3 confidence scores and whether alternative conformations were considered.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Claim scope
- **Claim pointer** "targeting protein-protein interactions that are vital for specific nuclease activities, such as CSB's stimulation of SNM1A's nuclease activity, may be a productive alternative therapeutic strategy to nuclease active site inhibition"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The therapeutic suggestion is presented without any evidence that disrupting the CSB-SNM1A interaction would be beneficial in a disease context. No data on cellular phenotypes, patient-derived models, or in vivo efficacy are mentioned. The logic that inhibiting a protein-protein interaction could substitute for active site inhibition is plausible but requires demonstration that the interaction is rate-limiting in a pathological setting.
- **Why it matters** This claim extends the work beyond basic mechanism into translational territory. If included in the abstract, it invites scrutiny from a broader audience and may overstate the immediate applicability of the findings.
- **Resolution test** Either remove the therapeutic claim from the abstract or support it with at least one cellular experiment showing that disrupting the interaction phenocopies SNM1A loss in an ICL repair assay, and discuss the context in which such inhibition would be therapeutically relevant.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Domain nomenclature
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "two copies of the C-terminal domain of CSB are necessary for a stable interaction" is ambiguous. It is unclear whether this means a dimer of the C-terminal domain, two separate binding sites within the C-terminal region, or two molecules of CSB per SNM1A complex.
- **Required correction** Clarify the stoichiometry and the exact domain architecture, for example by stating whether the C-terminal region contains two tandem copies of a folded domain or whether dimerization is required.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Novelty claim
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that the C-terminal region of CSB is a "novel DNA binding region." Without context on prior studies of CSB DNA binding, it is unclear what is novel. CSB is a known ATP-dependent chromatin remodeler with established DNA interactions.
- **Required correction** Briefly state what distinguishes this DNA binding region from previously characterized CSB DNA binding surfaces, or cite prior work that missed this region.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Experimental conditions
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not specify the type of ICL substrate used, the lesion chemistry, or the sequence context. ICL unhooking by SNM1A is known to be influenced by the chemical nature of the crosslink.
- **Required correction** Specify the ICL structure used in the in vitro assays, or state that the effect was observed across multiple ICL chemistries if that is the case.

## Risk / unsupported claims
- The claim that CSB stimulates SNM1A digestion through ICLs in vitro is unsupported by quantitative data in the abstract.
- The AlphaFold3-based mapping of molecular contacts is presented as definitive without evidence of model validation.
- The therapeutic strategy suggestion is unsupported by any functional or disease-relevant data.
- The "novel DNA binding region" claim is unverifiable without comparison to prior CSB DNA binding studies.
- The stoichiometry of the CSB-SNM1A interaction is unclear from the abstract.