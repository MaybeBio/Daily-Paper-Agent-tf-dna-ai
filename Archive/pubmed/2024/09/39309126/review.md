## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, logical coherence, support for claims, and alignment with stated objectives
- **Shared manuscript claim summary** The manuscript reviews structural, biophysical, and bioinformatic evidence on p53-DNA binding, arguing that p53 recognizes binding sites through a combination of direct consensus sequence contacts and indirect readout involving DNA flexibility and allostery. It further claims that new computational methods, including machine learning, graph theory, and sector analysis, can be integrated into a pipeline for de novo allosteric drug design to restore mutant p53 function.
- **Visible evidence base** Literature cited throughout; structural data from PDB entries 1TUP, 2OJC, 3Q05, 4MZR, 3KMD, 1IGT; computational modeling described in prior work by the authors (Thayer and Han 2017; Fabry and Thayer 2023); experimental data from cited studies (e.g., Petty et al. 2011; Nguyen et al. 2018; Smeenk et al. 2011)
- **Missing materials affecting confidence** No figures or supplementary materials were provided; specific quantitative results from the authors' own computational models are not shown; no detailed methodology for the described machine learning pipeline is given; the graphical abstract is described but not visible

## Reviewer
- **Overall assessment** This is a broad narrative review covering p53 structure, DNA binding mechanisms, allostery, and computational drug design. The topic is timely and of interest to the biophysics and cancer biology communities. The manuscript is generally well-written and accessible, with a logical progression from structural biology to therapeutic implications. However, the review is largely descriptive and lacks critical depth in several areas. The central claim that indirect readout and allostery are key to p53 binding site discrimination is supported by cited literature, but the authors' own contributions (e.g., the additive energy model, MD sector analysis) are presented without sufficient quantitative detail or validation. The proposed machine learning drug design pipeline is speculative and not backed by demonstrated results. The clinical relevance section overstates the translational readiness of the described approaches. Overall, the manuscript provides a useful overview but does not establish a novel or definitive case for the proposed computational pipeline.
- **Who would be interested in the results, and why** Biophysicists studying protein-DNA interactions and allostery; cancer biologists interested in p53 reactivation strategies; computational chemists and structural biologists working on drug discovery; researchers in the machine learning for drug design community. The review synthesizes a wide range of literature and could serve as an entry point for those new to the field.
- **Major strengths** 1) Comprehensive coverage of p53 structural biology, from early crystallography to recent cryo-EM and MD studies. 2) Clear articulation of the indirect readout hypothesis and its experimental support, particularly the L1 loop dynamics work. 3) Good integration of biophysical, bioinformatic, and computational perspectives. 4) Accessible writing style suitable for a broad audience. 5) Timely discussion of machine learning and graph theory applications to drug design.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The authors' own computational models (additive energy model, MD sector analysis) are referenced but not described with enough detail to evaluate their validity. The proposed machine learning pipeline is presented as promising but no proof-of-concept results are shown. The claim that "new computational methods have emerged capable of capturing such information" is not substantiated with specific examples or benchmarks.
- **Assessment against Nature-style criteria** 
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for central claims
- **Claim pointer** The manuscript claims that "new computational methods have emerged capable of capturing such information, which can then be utilized as input to machine learning algorithms towards the goal of more intelligent and efficient de novo allosteric drug design."
- **Evidence pointer** Section "Machine learning in allosteric drug design"; Section "Sectors: identifying allosteric points of control for drug design"; Section "Drug design summary"
- **Concern** The manuscript describes a proposed pipeline combining generative adversarial neural networks, molecular docking, MD simulations, sector analysis, and heat kernel analysis, but provides no results, benchmarks, or validation demonstrating that this pipeline works. The authors state "we propose exciting advances and ideas that, although have not yet realized the molecules needed, provide a way forward" which is honest but means the central forward-looking claim of the review is entirely speculative. No evidence is presented that the described methods can actually generate viable drug candidates or that the feedback loop between docking scores, MD simulations, and machine learning is functional.
- **Why it matters** The stated objective of the review includes "consider cutting-edge ideas in the field coupled with recent advances in graph theory and machine learning, which we envision as an exciting and novel path forward." If the proposed approach has not been tested, the review cannot claim it "holds great promise" as a validated strategy. Readers cannot assess whether the pipeline is feasible, and the scientific case for the manuscript's main forward-looking claim is not established.
- **Resolution test** Provide proof-of-concept results, even preliminary, demonstrating that the described pipeline can generate molecules that bind p53 mutants and restore wild-type-like dynamics. Alternatively, clearly reframe the manuscript as a perspective piece that explicitly identifies the proposed pipeline as untested speculation, and temper the language accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for authors' own models
- **Claim pointer** The manuscript describes an "additive energy model" (Thayer and Han 2017) that "attempt[s] to quantitate the enthalpic contributions and estimate the corresponding contributions from indirect readout" and reports that results "suggested partitioning binding sequences into several categories."
- **Evidence pointer** Section "Additive energy model"
- **Concern** The additive energy model is described qualitatively, with categories of binding sequences discussed, but no quantitative results are presented. No scores, correlation coefficients, validation against experimental binding data, or comparison to alternative models are shown. The reader cannot evaluate whether the model is predictive, accurate, or useful. Similarly, the MD sector analysis (Fabry and Thayer 2023) is mentioned but no details of the methodology or results are given.
- **Why it matters** The manuscript's argument that indirect readout contributes to binding site discrimination in a quantifiable way rests on this model. Without quantitative evidence, the claim that the model supports the indirect readout hypothesis is unverifiable. For a review that aims to inform future drug design, presenting an unvalidated model as evidence is problematic.
- **Resolution test** Include key quantitative results from the additive energy model, such as predicted versus measured binding affinities for a set of p53 binding sites, or a clear statement of the model's predictive accuracy. For the MD sector analysis, provide details on the simulation setup, the identified sectors, and how they correlate with known allosteric communication pathways.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Overstatement of clinical relevance
- **Claim pointer** The manuscript's title and conclusion state implications for cancer therapy, and the Clinical relevance section claims "The ideas brought to light by this review constitute a significant advance that can be applied to ongoing biophysical studies of drugs for p53, paving the way for the development of new methodologies for allosteric drugs. Our discoveries hold promise to provide molecular therapeutics which restore p53 native activity, thereby offering new insights for cancer therapies."
- **Evidence pointer** Section "Clinical relevance"; Section "Conclusion"
- **Concern** The review describes no new discoveries of its own, and the only drug discussed (PK11000) failed clinical trials. The claim that the review's ideas "constitute a significant advance" and that "our discoveries hold promise" overstates what is a synthesis of existing literature plus a speculative computational proposal. The phrase "our discoveries" is particularly problematic for a review article.
- **Why it matters** Overstating translational readiness can mislead readers, particularly those in clinical or pharmaceutical research, into believing that p53-targeting allosteric drugs are closer to clinical use than they are. This undermines the credibility of the review.
- **Resolution test** Rewrite the Clinical relevance section to accurately reflect the current state of the field, acknowledging that no p53-restoring drug has passed clinical trials and that the proposed computational pipeline is at an early conceptual stage. Remove or soften claims of "discoveries" and "significant advance."

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Depth of critical analysis
- **Claim pointer** The manuscript states "Considerable literature corroborates the idea that p53 is a complex allosteric protein that discriminates its binding sites not only via consensus sequence through direct H-bond contacts, but also a complex combination of factors involving the flexibility of the binding site."
- **Evidence pointer** Throughout the manuscript, particularly sections on indirect readout, L1 loop dynamics, and allostery
- **Concern** The review presents a largely uncritical synthesis of the literature. Contradictory evidence or alternative interpretations are rarely discussed. For example, the controversy over the relative importance of direct versus indirect readout in p53 binding is mentioned but not critically evaluated. The debate over whether the tetramer binds DNA in a head-to-head or head-to-tail arrangement is noted but not resolved or discussed in depth. The authors do not identify gaps in the current understanding or propose specific experiments to resolve open questions.
- **Why it matters** A review that merely summarizes without critical evaluation does not advance the field. Readers, especially those new to the topic, need guidance on which claims are well-supported, which are contested, and what the key open questions are. The current manuscript reads more as an annotated bibliography than a critical review.
- **Resolution test** Add a section or subsections that explicitly discuss controversies, conflicting evidence, and unresolved questions in the field. For each major claim, indicate the strength of the supporting evidence and note where the literature is incomplete or contradictory.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and accuracy of structural descriptions
- **Affected element** Section "H-bond interaction surface"
- **Evidence pointer** "In this binding interface, six of the eight interactions mediate protein side chain H-bond interactions to the DNA backbone: K120, S241, R248, R273, A276, R283. Only three residues, K120, C277, and R80, have capabilities of making discriminate interactions occurring in the DNA major groove."
- **Issue** There are inconsistencies in the residue numbering. Earlier in the text, the eight residues directly H-bonding with DNA are listed as K120, R241, K248, K273, A276, A277, R280, and R283. In the quoted sentence, S241, C277, and R80 appear, which do not match the earlier list. This appears to be a typographical error.
- **Required correction** Correct the residue names to be consistent with the earlier list. If the intent is to describe different residues, clarify which residues are being referred to and ensure consistency throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Section "p53–non-B-DNA interactions"
- **Evidence pointer** "p53 exhibits structure-specific DNA binding properties; it has the ability to bind a wide array of DNA structures including positively and negatively supercoiled DNA, three-way and four-way junctions, telomere T-loops, hemicatenate DNA, and cruciforms"
- **Issue** The term "structure-specific DNA binding" is used without definition. It is not clear whether this refers to binding to non-B-form DNA structures, to specific DNA geometries, or to something else. The term could be confused with sequence-specific binding.
- **Required correction** Define what is meant by "structure-specific" in this context, or use a more precise term such as "non-canonical DNA structure binding."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure referencing
- **Affected element** Section "Insights from the first crystal structure"
- **Evidence pointer** "it contains a variety of important structural elements involved with DNA binding: the L1 loop, the L2 loop, the L3 loop, and the strand loop helix (Fig. 1B)."
- **Issue** The figure is referenced but was not provided for review. The figure legend in the text describes a structural representation of the p53 DBD with colored beads, but it is unclear whether Fig. 1B corresponds to the described elements.
- **Required correction** Ensure that the figure, when published, clearly labels the L1, L2, L3 loops and the strand-loop-helix as described. In the text, consider adding a brief description of what is shown in each panel of the figure.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Citation completeness
- **Affected element** Section "p53 PTMs"
- **Evidence pointer** "Ten PTMs independently capable of regulating promoter-specific enhancement exist in the combinatorically complex PTM regulatory scheme"
- **Issue** This specific claim about ten PTMs is not accompanied by a citation. Given that this is a specific quantitative claim, it should be supported by a reference.
- **Required correction** Add a citation to the source of this claim, or clarify whether this is the authors' own synthesis of the literature.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Equation presentation
- **Affected element** Section "Sectors: identifying allosteric points of control for drug design"
- **Evidence pointer** "The solution to the heat kernel for a given time t is given by the equation: ht = Pe−tLPT"
- **Issue** The equation is presented without defining all variables clearly. While P and L are defined in the following sentence, the notation is not standard and could be confusing. The superscript T for transpose is not explicitly stated.
- **Required correction** Define all variables explicitly, including stating that PT denotes the transpose of P. Consider using standard notation for the matrix exponential.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Consistency of terminology
- **Affected element** Section "Machine learning in allosteric drug design"
- **Evidence pointer** "Generative adversarial neural networks (GANNs)"
- **Issue** The standard acronym for generative adversarial networks is GAN, not GANN. The authors use GANN throughout, which may cause confusion with graph neural networks (GNNs).
- **Required correction** Use the standard acronym GAN, or clearly define GANN as the authors' preferred abbreviation and note the distinction from GNN.

## Risk / unsupported claims
- The claim that "new computational methods have emerged capable of capturing such information" is unsupported by specific examples or benchmarks in the text.
- The proposed machine learning pipeline for de novo allosteric drug design is presented as promising but is entirely untested; no proof-of-concept results are shown.
- The statement that "our discoveries hold promise to provide molecular therapeutics" is unsupported, as the manuscript presents no new discoveries.
- The claim that "recent iterations of MD sectors display that residues analyzed from MD trajectories can be quantified into a sector" is not accompanied by any quantitative data or methodological detail.
- The assertion that "the method holds great promise for advances in the development of molecular therapeutics" is speculative and not backed by demonstrated results.
- The claim that "p53 has been shown in vitro to bind to hemicatenate DNA, and can adopt one of three different complexes" is presented without a specific citation in the text provided.
- The statement that "the most commonly found p53 target fragment consisted of the consensus binding site without any spacers, as expected" is presented as a summary of cited work but the expectation is not justified in the text.