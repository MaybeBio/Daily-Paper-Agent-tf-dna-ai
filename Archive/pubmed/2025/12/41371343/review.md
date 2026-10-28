## Review setup
- **Input scope** Full manuscript text, including abstract, results, discussion, experimental procedures, and supporting information references
- **Assessment boundary** Scientific content, methodological rigor, validity of conclusions, and clarity of presentation as provided in the manuscript
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics simulations to investigate the kinetics and mechanisms of ternary TF·TF·DNA complex formation in two systems (Sox2·Oct1·DNA and SRF·SAP1·DNA). They report that nonspecific protein-DNA interactions primarily govern ternary complex formation kinetics, that DNA conformational changes do not always dominate kinetics, and that the binding order of transcription factors depends on the relative nonspecific affinities of the proteins and DNA conformation.
- **Visible evidence base** Abstract, Results (including Figures 2-6), Discussion, Experimental Procedures, Data Availability, and Supporting Information references
- **Missing materials affecting confidence** Supporting information files (Figures S1-S7, detailed methods for the deformable DNA model and dual-basin Gaussian potential) were not provided. Raw simulation trajectories and analysis code were not inspected. Experimental validation data referenced from prior studies were not independently verified.

## Reviewer
- **Overall assessment** This manuscript addresses an important and understudied question in gene regulation: how ternary transcription factor complexes assemble on DNA. The use of coarse-grained simulations to explore kinetic mechanisms is timely and the two systems chosen are biologically relevant. The central finding that nonspecific protein-DNA interactions, rather than DNA conformation alone, dictate binding order in one system but not the other is potentially interesting. However, the manuscript has several significant weaknesses. The distinction between "nonspecific affinity" and "site-specific recognition" is not operationally defined in a way that is clearly supported by the simulation data. The claim that DNA conformation does not always dominate kinetics is presented as a novel insight, but the manuscript does not provide a quantitative framework for comparing the relative contributions of different factors. The comparison between the two systems is complicated by the use of different interaction strength parameters (εijC) for each system, which the authors acknowledge limits cross-system comparison. The connection to experimental data is suggestive but not rigorously established. The writing is generally clear but some methodological details are insufficient for reproduction.

- **Who would be interested in the results, and why** Researchers studying transcription factor dynamics, protein-DNA recognition, and gene regulatory mechanisms would find this work relevant. The coarse-grained simulation approach for studying multi-protein-DNA assembly kinetics could interest computational biophysicists. The specific systems studied (Sox2·Oct1 and SRF·SAP1) are of direct interest to developmental biologists and researchers studying immediate-early gene regulation. The broader claim about how protein-protein interactions and DNA deformability jointly shape assembly pathways could interest the gene regulation community at large.

- **Major strengths** The manuscript addresses a genuinely understudied problem: the kinetic mechanisms of ternary complex assembly on DNA. The choice of two well-characterized biological systems with known crystal structures provides a solid foundation. The use of a deformable DNA model that can be tuned between linear and bent conformations is an innovative approach. The analysis of skipping events as a mechanistic readout is thoughtful. The authors make a good faith effort to connect their simulation results to prior experimental findings.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "the kinetics of ternary complex formation is primarily governed by nonspecific TF-DNA interactions" and that "when the TFs exhibit divergent nonspecific affinities, as in the Sox2·Oct1·DNA system, the binding order is dictated largely by diffusion along nonspecific DNA."
- **Evidence pointer** Results, Figures 2, 4, 6; Experimental Procedures
- **Concern** The central claim rests on the distinction between "nonspecific affinity" and "site-specific recognition," but the manuscript does not provide an operational definition of these terms in the context of the simulations. The diffusion coefficients (D1) are measured along nonspecific DNA, but the relationship between D1 and "affinity" is not established. Slower diffusion is interpreted as higher affinity, but this is an assumption that requires justification. Furthermore, the claim that Sox2 has "higher affinity for both nonspecific and specific DNA" is not directly measured; only diffusion coefficients and association rates are reported. The manuscript conflates association rate with affinity, which are distinct quantities.
- **Why it matters** The central mechanistic conclusion depends on correctly attributing the observed kinetic differences to specific molecular properties. If the interpretation of D1 as affinity is incorrect, the entire mechanistic framework collapses. The distinction between nonspecific and specific interactions is fundamental to the proposed model, and without clear operational definitions, the claims are not testable.
- **Resolution test** The authors should provide a clear operational definition of "nonspecific affinity" as used in their simulations. They should either directly measure binding affinities (e.g., via potential of mean force calculations) or provide a theoretical justification for why D1 serves as a proxy for affinity. They should also clarify how "site-specific recognition" is distinguished from nonspecific interactions in their model, given that the DNA sequence is random and the model uses uniform parameters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "DNA conformational change does not always dominate the kinetics" and that this is a key finding that contradicts the initial hypothesis.
- **Evidence pointer** Results, Figures 2, 4; Discussion
- **Concern** The manuscript does not provide a quantitative measure of the relative contribution of DNA conformation versus other factors to the kinetics. The statement that DNA conformation "does not always dominate" is presented as a qualitative observation, but no statistical or quantitative framework is provided to support this claim. The comparison across different α values is made, but the authors do not decompose the total kinetic effect into contributions from DNA conformation, protein properties, and protein-protein interactions. Without such a decomposition, the claim is not rigorously established.
- **Why it matters** The stated novelty of the work depends on this claim. If the authors cannot quantitatively demonstrate the relative importance of different factors, the conclusion is not supported by the data. The claim as stated is too vague to be falsifiable.
- **Resolution test** The authors should perform a quantitative decomposition of the factors contributing to the association rate (e.g., via a kinetic model or sensitivity analysis). They should provide error bars or confidence intervals for the relative contributions of DNA conformation, protein diffusion, and protein-protein interactions to the overall kinetics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the SRF·SAP1·DNA system shows a "shift in preference" between binding orders depending on DNA conformation, with SAP1-first favored for linear DNA and SRF-first favored for bent DNA.
- **Evidence pointer** Results, Figure 4B; Discussion
- **Concern** The difference between the two binding order pathways in the SRF·SAP1·DNA system appears modest based on the described results. The manuscript states that the two pathways are "broadly similar" for most DNA conformations, with a shift only at the extremes. The statistical significance of this shift is not reported. The authors do not provide error estimates for the overall ternary rates in Figure 4B, and it is unclear whether the observed preference reversal is within the noise of the simulations.
- **Why it matters** This is a central mechanistic claim for one of the two systems studied. If the preference shift is not statistically robust, the conclusion that DNA conformation determines binding order in this system is not supported.
- **Resolution test** The authors should provide statistical analysis (e.g., confidence intervals, hypothesis testing) for the difference between the two binding order pathways across α values. They should also report the number of independent simulations and the variance in the estimated rates.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that the findings "highlight how the interplay between TF molecular properties, DNA sequence and deformability, and protein-protein interactions together shape the kinetics and molecular mechanisms underlying ternary TF·TF·DNA complex formation."
- **Evidence pointer** Abstract; Discussion
- **Concern** The manuscript studies only two systems, and the authors acknowledge that the interaction strength parameters differ between them, limiting cross-system comparison. The claim of generalizability is therefore weak. The authors do not provide a framework for predicting which mechanism (nonspecific affinity-driven vs. site-specific recognition-driven) would apply to other TF pairs. The broader significance of the work is asserted but not demonstrated.
- **Why it matters** For a Nature-style journal, the work needs to establish general principles or at least provide a framework that extends beyond the two specific systems studied. As presented, the conclusions are system-specific and the general implications are speculative.
- **Resolution test** The authors should either study additional systems with varying properties (e.g., different DNA binding affinities, different protein-protein interaction strengths) or provide a theoretical framework that allows predictions for other systems. At minimum, they should clearly articulate what specific, testable predictions their model makes for other ternary complexes.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "the presence of pre-bound Sox2 approximately doubles the association rate of Oct1 to DNA" and that this is due to "reducing skipping events and facilitating DNA binding through protein-protein interactions."
- **Evidence pointer** Results, Figures 2A, 5A; Discussion
- **Concern** The mechanism by which Sox2 reduces skipping events is not clearly explained. The authors attribute this to protein-protein interactions, but the specific interactions that stabilize Oct1 binding are not identified or characterized. The manuscript does not analyze which contacts between Sox2 and Oct1 are important, nor does it test whether disrupting these contacts would abolish the cooperative effect. The claim that protein-protein interactions are responsible is therefore not directly tested.
- **Why it matters** The cooperative mechanism is a key finding, but without identifying the specific interactions responsible, the claim is not mechanistically informative. The manuscript would be strengthened by a mutational analysis (in silico) or a detailed contact analysis.
- **Resolution test** The authors should perform a contact analysis to identify which specific Sox2-Oct1 interactions correlate with reduced skipping and enhanced binding. They could also perform simulations with mutated interaction sites to test the causal role of specific contacts.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract uses terms like "coarse-grained molecular dynamics simulations" and "nonspecific TF-DNA interactions" without brief explanations. A general reader may not understand what these mean or why they matter.
- **Required correction** Add brief parenthetical explanations for technical terms, e.g., "coarse-grained molecular dynamics simulations (a simplified computational approach that captures large-scale motions)" and "nonspecific TF-DNA interactions (binding to DNA outside the specific recognition site)."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Experimental Procedures, DNA modeling
- **Evidence pointer** Experimental Procedures, DNA modeling section
- **Issue** The description of the DNA model states that "the sequence information is lost in modeling of nonspecific DNA that are modeled uniformly solely by electrostatic interactions." This is a significant simplification that is mentioned almost in passing. The implications of this simplification for the conclusions should be discussed more thoroughly.
- **Required correction** Add a paragraph in the Discussion addressing the limitations of the uniform DNA model and how sequence-specific effects might alter the conclusions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Experimental Procedures, Analysis of kinetics
- **Evidence pointer** Experimental Procedures, Analysis of kinetics section
- **Issue** The definition of the "first binding event" being ignored is unclear. The authors state that it "depends on protein positioning relative to the target site," but it is not clear how this is determined or why this is a valid approach.
- **Required correction** Provide a more detailed explanation of how the first binding event is identified and why it is excluded. Justify this choice with reference to standard practice in the field.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, Figure 2
- **Evidence pointer** Results, Figure 2 legend
- **Issue** The figure legend is dense and uses abbreviations (e.g., "konOct1·Sox2") that are not immediately clear. The relationship between the different curves and what the reader should take away from the figure is not stated.
- **Required correction** Expand the figure legend to explain the key takeaway from each panel and define all abbreviations in the legend text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, SRF·SAP1 section
- **Evidence pointer** Results, Formation kinetics of the SRF⋅SAP1⋅DNA ternary complex
- **Issue** The manuscript states that "the ratio between ternary and binary rates approaches a value of 2.5 for the Oct1⋅Sox2⋅DNA system, whereas for the SRF⋅SAP1⋅DNA system the maximal value is 1.5, reflecting greater cooperativity in the former system." This comparison is made across systems with different εijC values, which the authors acknowledge limits cross-system comparison. The claim of "greater cooperativity" is therefore not well-supported.
- **Required correction** Either provide a normalized measure of cooperativity that accounts for the different εijC values, or soften the claim and acknowledge that direct comparison is not possible.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The Discussion does not adequately address the limitations of the coarse-grained model, particularly the lack of sequence specificity and the simplified protein representation. The authors should discuss how these simplifications might affect the generality of their conclusions.
- **Required correction** Add a "Limitations" paragraph to the Discussion addressing these issues and suggesting how future work could address them.

## Risk / unsupported claims
- The claim that "nonspecific TF-DNA interactions primarily govern the kinetics of ternary complex formation" is not quantitatively supported, as no decomposition of factors contributing to the kinetics is provided.
- The claim that "DNA conformational change does not always dominate the kinetics" is presented as a key finding but is not supported by a quantitative comparison of the relative contributions of different factors.
- The claim of "greater cooperativity" in the Sox2·Oct1·DNA system compared to the SRF·SAP1·DNA system is not supported due to the different interaction strength parameters used in the two systems.
- The interpretation of D1 (diffusion coefficient) as a proxy for "nonspecific affinity" is an assumption that is not justified or tested.
- The claim that protein-protein interactions are responsible for the cooperative effect of Sox2 on Oct1 binding is not directly tested, as no mutational or contact analysis is performed.
- The statistical significance of the binding order preference shift in the SRF·SAP1·DNA system is not reported, making this claim unverifiable from the provided information.
- The generalizability of the findings to other TF pairs is asserted but not demonstrated, as only two systems were studied.

## Assessment against Nature-style criteria
- **Originality** The question of ternary complex assembly kinetics is relatively underexplored compared to binary complexes, and the use of a deformable DNA model to probe the role of DNA conformation is a creative approach. However, the core finding that nonspecific interactions matter is not entirely novel, as similar ideas exist in the facilitated diffusion literature. The originality is moderate.
- **Scientific importance** The work addresses a fundamental question in gene regulation, and the two systems studied are biologically important. However, the limited scope (two systems) and the lack of a generalizable framework limit the broader significance. The importance is moderate.
- **Interdisciplinary readership** The work bridges computational biophysics and molecular biology, and could interest researchers in both fields. However, the technical nature of the methods and the lack of clear explanations for nonspecialists may limit accessibility. The interdisciplinary appeal is moderate.
- **Technical soundness** The methods are appropriate for the questions asked, but several technical concerns (operational definitions, statistical rigor, cross-system comparison) undermine confidence in the conclusions. The technical soundness is currently insufficient.
- **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear, but technical terms are not always explained and some figure legends are dense. The readability is adequate but could be improved.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an interesting question with a potentially useful approach, but the central claims are not quantitatively supported, and several technical concerns need to be addressed. The authors should provide clearer operational definitions of key concepts, quantitative decomposition of the factors governing kinetics, statistical analysis of the key comparisons, and a more thorough discussion of limitations. If these concerns are addressed, the work could become a valuable contribution to the field.