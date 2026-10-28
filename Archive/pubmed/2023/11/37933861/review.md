## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, data availability, and supplementary figure/table references.
- **Assessment boundary** Scientific content, methodological rigor, logical coherence, and support of claims by the presented evidence. No assessment of grammar or style beyond readability for the target audience.
- **Shared manuscript claim summary** The authors use extensive molecular dynamics simulations to show that the human XPD helicase verifies CPD and 6-4PP photolesions via distinct mechanisms, with 6-4PP capable of translocating into the XPD pore and inducing Arch domain displacement, while CPD is sterically blocked and trapped by external sensors, potentially explaining differential repair efficiencies.
- **Visible evidence base** Main text figures 1-5 (referenced), supplementary figures S1-S8, supplementary tables S1-S6, two supplementary movies, and simulation trajectory data deposited on Figshare.
- **Missing materials affecting confidence** The actual figures, supplementary figures, tables, and movies were not provided. Simulation parameters, force field details, and convergence criteria are only referenced as "Supplementary Methods" and not visible. The Figshare deposition could not be accessed for verification.

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive and potentially valuable study of how the XPD helicase differentially engages with two major UV photolesions. The authors have performed an impressive 20 independent ~8 microsecond simulations per lesion, which represents a substantial sampling effort. The central observation that 6-4PP can translocate into the XPD pore while CPD cannot, due to steric constraints, is mechanistically plausible and could have implications for understanding differential NER efficiencies. However, the manuscript has several significant weaknesses. The evidence presented is entirely computational, and the connection to experimental observations is largely speculative. The claim that Arch domain displacement "may facilitate repair" is not directly supported by any functional data. The presentation of results relies heavily on qualitative descriptions of a small number of trajectories, and the quantitative analysis appears limited. The readability is generally good, but the Discussion extends beyond what the data can support in several places. Overall, the study is interesting but the case for its biological significance is not fully established from the provided material.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, particularly nucleotide excision repair, and computational biophysics studying protein-DNA interactions. The study provides atomistic detail on how a key helicase distinguishes between lesion types, which is relevant to understanding cancer susceptibility and the development of repair-targeted therapies. The methodological approach of extensive sampling may also interest computational biologists studying rare conformational events.
- **Major strengths**
  1. The scale of the simulation effort is substantial, with 20 independent ~8 microsecond simulations per lesion, which is commendable for studying rare events like lesion translocation.
  2. The study addresses a biologically important question, namely how XPD differentially verifies two major UV lesions, which has implications for understanding why 6-4PP is repaired more efficiently than CPD.
  3. The authors have made their trajectories available on Figshare, which supports reproducibility and further analysis by the community.
  4. The comparison between the two lesions under identical simulation conditions is a well-designed approach that allows for direct mechanistic comparison.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that "the movement of the Arch domain, only in the case of 6-4PP, may trigger signaling to the XPG nuclease for subsequent lesion incision by fostering direct contact between the Arch domain and XPG, and thereby facilitating repair of 6-4PP."
  - **Evidence pointer** Discussion section, Figure 5 (referenced but not provided)
  - **Concern** This is a central claim of the manuscript, linking the observed Arch domain displacement to downstream repair outcomes. However, the evidence presented is entirely speculative. Figure 5 is described as a model of XPG-XPD-XPB-DNA, but no simulation or experimental data involving XPG is presented. The claim that Arch displacement "may trigger signaling" is not supported by any direct evidence, and the connection to repair efficiency is inferred rather than demonstrated. The authors themselves use "may" and "speculate," but the claim is presented prominently in the abstract and conclusion as a key finding.
  - **Why it matters** The biological significance of the study rests on the claim that the observed conformational differences translate into functional differences in repair. Without direct evidence linking the Arch domain movement to XPG recruitment or incision activity, this remains an untested hypothesis. The manuscript would be strengthened by either tempering this claim or providing additional computational or experimental support.
  - **Resolution test** The authors should either (a) provide additional simulations or analyses that directly test the interaction between the displaced Arch domain and XPG, (b) cite and discuss experimental evidence that supports this mechanism, or (c) clearly reframe this as a hypothesis for future testing rather than a finding of the current study.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological transparency
  - **Claim pointer** The authors state that they "carried out a very comprehensive study of XPD bound to the photodamaged DNA for each lesion: 20 independent simulations, over 8 microseconds each, allowing their strict comparison under the present very extensive, identical sampling regime."
  - **Evidence pointer** Materials and methods, Supplementary Methods (referenced but not provided)
  - **Concern** The methods section is critically under-specified. The force field, water model, ion conditions, temperature/pressure coupling, and equilibration protocol are all relegated to "Supplementary Methods" which was not provided. More importantly, the criteria for considering simulations "converged" or "equilibrated" are not stated. The authors state they used "the last 2 microseconds" for analysis, but do not justify this choice or show convergence metrics. Without this information, the reliability of the sampling and the conclusions drawn from it cannot be assessed.
  - **Why it matters** Molecular dynamics results are highly sensitive to simulation setup and convergence. The claim of "strict comparison" between the two lesions requires that the simulation conditions are truly identical and that the sampling is sufficient. The lack of methodological detail prevents other researchers from reproducing the work and undermines confidence in the conclusions.
  - **Resolution test** The authors should provide the full simulation details in the main text or a clearly accessible supplement, including force field parameters, water model, ion concentration, temperature/pressure control, equilibration protocol, and convergence analysis (e.g., RMSD time series, block averaging, or replica convergence metrics).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Quantitative support
  - **Claim pointer** The authors describe that "in 4 out 20 simulations (i.e. 20% of the population), our MD results showed that 6-4PP initially positioned outside the pore enters into the unoccupied space within the pore" and that "in one of 20 simulations for XPD-CPD, the CPD initially positioned outside the pore undergoes a large displacement."
  - **Evidence pointer** Results section, Figures 2-4 (referenced but not provided)
  - **Concern** The central findings are based on a small number of trajectories (4 of 20 for 6-4PP, 1 of 20 for CPD). While the authors acknowledge this, the manuscript does not provide a quantitative analysis of why these events occur in some trajectories and not others. There is no statistical analysis of the probability of these events, no free energy calculations, and no analysis of the timescales involved. The reader is left with qualitative descriptions of individual trajectories without a sense of whether these are robust findings or rare stochastic events.
  - **Why it matters** The claim that the two lesions are verified by "strikingly different" mechanisms rests on the observation that 6-4PP can enter the pore in 20% of simulations while CPD cannot. However, with only 20 simulations per lesion, the statistical power is limited. A more rigorous analysis, such as Markov state models or free energy calculations, would strengthen the claim that these differences are mechanistically significant rather than sampling artifacts.
  - **Resolution test** The authors should provide quantitative analyses that support the statistical significance of their observations, such as free energy profiles for lesion entry, transition path analysis, or additional independent simulations to confirm the reproducibility of the observed events.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Results section, subsection on CPD interactions
  - **Evidence pointer** Results section, "CPD interacts with lesion sensors outside the pore entry as its bases are inhibited from entering"
  - **Issue** The subsection title states that CPD bases are "inhibited from entering" the pore, but the text describes that in one simulation, the CPD backbone translocated while the bases remained blocked. This is a subtle distinction that could confuse readers. The title could be more precise.
  - **Required correction** Consider revising the title to "CPD bases are sterically blocked from entering the XPD pore" or similar, to more accurately reflect the finding that the bases themselves do not enter, even when the backbone moves.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Interpretation of prior work
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section, paragraph on prior work
  - **Issue** The authors state that their prior work (reference 67) characterized a "trapped in the pore" structure for 6-4PP, and the current work adds the "base-translocation pathway" and "entrapment of 6-4PP by lesion sensors outside the pore." However, the relationship between these findings is not fully clarified. Does the current work supersede or complement the prior study? Are the findings consistent?
  - **Required correction** Clarify how the current findings relate to and extend the prior study, and whether the prior "trapped in the pore" structure is consistent with the new observations of translocation into the pore.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Figure accessibility
  - **Affected element** Figures 1-5
  - **Evidence pointer** All figures referenced in the text
  - **Issue** The figures were not provided for review, so it is impossible to assess whether the visual evidence supports the textual descriptions. In particular, Figure 5, which is central to the XPG signaling claim, is described as a model but its construction and basis are unclear.
  - **Required correction** Ensure that all figures are clearly labeled, self-explanatory, and directly support the claims made in the text. For Figure 5, specify whether this is a structural model, a schematic, or a simulation snapshot, and how it was generated.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology consistency
  - **Affected element** Abstract and Discussion
  - **Evidence pointer** Abstract, Discussion section
  - **Issue** The terms "verification," "recognition," and "sensing" are used somewhat interchangeably throughout the manuscript. While this is common in the field, it could lead to confusion about what exactly is being measured or claimed.
  - **Required correction** Define these terms early in the manuscript and use them consistently to distinguish between initial lesion recognition, the verification process, and downstream signaling.

## Risk / unsupported claims
- The claim that Arch domain displacement "may trigger signaling to the XPG nuclease" is unsupported by direct evidence and is presented as speculation in the text but as a more definitive finding in the abstract.
- The claim that the observed differences in XPD verification "may contribute to varying NER lesion susceptibilities" is presented as a possible implication but is not tested or directly supported by the data.
- The statement that "the absence of any population manifesting translocation indicates that the barrier imposed by the sensors and the steric bulk of the lesion is unlikely to be overcome" for CPD is based on 20 simulations and may not be generalizable.
- The assertion that the 6-4PP "trapped in the pore" state "would not be feasible if replaced with CPD" is based on a single trajectory and is not quantitatively demonstrated.
- The biological relevance of the observed Arch domain displacement to repair outcomes is not established, as no functional assays or experimental validation are presented.