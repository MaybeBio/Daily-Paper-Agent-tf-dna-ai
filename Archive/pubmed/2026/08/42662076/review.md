## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, technical accuracy, logical coherence, and completeness of the review as presented in the provided text
- **Shared manuscript claim summary** The manuscript argues that effective epigenetic editing requires prior characterization of the target epigenetic landscape, and that programmable epigenetic modifiers (PEMs) represent a more precise therapeutic alternative to global epigenetic drugs. It reviews detection technologies, editing platforms, machine learning approaches, heritability considerations, and therapeutic applications across cancer, inherited disorders, and infectious diseases.
- **Visible evidence base** Abstract, Introduction, sections on epigenetic detection technologies, strategies to modify the epigenome, machine learning for editor design, epigenetic memory, therapeutic applications, Conclusions, Acknowledgments, Author contributions, Declaration of interests
- **Missing materials affecting confidence** Figures 1-3 and Tables 1-4 are referenced but not fully visible in the provided text. Reference list is not provided. Specific methodological details for several cited studies are not available.

## Reviewer
- **Overall assessment** This review addresses a timely and important topic at the interface of epigenomic profiling and programmable epigenetic editing. The central thesis, that pre-existing chromatin state determines editing outcomes and therefore must be characterized before intervention, is well articulated and supported by cited literature. The manuscript covers a broad range of relevant technologies and applications, and the inclusion of delivery constraints and heritability considerations adds practical value. However, several technical inaccuracies, unclear statements, and structural issues weaken the overall quality. The distinction between epigenetic editing and transcriptional modulation is sometimes blurred, and some claims about specific systems require more precise description. The review would benefit from more critical evaluation of the technologies discussed rather than primarily descriptive summaries.

- **Who would be interested in the results, and why** Researchers in epigenetic editing, gene therapy, and chromatin biology would find this review useful as an entry point to the field. Clinicians and translational scientists interested in epigenetic therapies for cancer, genetic disorders, and chronic viral infections would also benefit. The integration of detection technologies with editing strategies provides a framework that could guide experimental design for practitioners entering this space.

- **Major strengths** The central concept, that epigenetic landscape characterization should precede editor selection, is a valuable and somewhat underappreciated perspective. The review covers a wide range of technologies and systems, providing a useful survey. The discussion of heritability and delivery constraints addresses practical translational challenges often omitted from similar reviews. The inclusion of machine learning approaches reflects an emerging trend in the field.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical accuracy
- **Claim pointer** The manuscript states that KRAB domain is "150-300 bp" and that EZH2 has a "large size (about 2,200 bp)" with a "truncated version of about 800 bp" that requires "co-delivery of DNMT3L."
- **Evidence pointer** Section "Programmable transcriptional repression", location not provided
- **Concern** The size estimates for effector domains appear inconsistent and potentially inaccurate. The KRAB domain from ZNF10 is typically around 300-400 bp, not 150-300 bp. More critically, the statement that EZH2 requires co-delivery of DNMT3L is misleading. While some studies have used DNMT3L to enhance EZH2 activity, EZH2 does not universally require DNMT3L for function. The truncated EZH2 variant referenced is not clearly identified, making the claim difficult to evaluate.
- **Why it matters** Accurate description of effector domain sizes and functional requirements is essential for researchers designing epigenetic editing constructs. Incorrect size estimates could mislead construct design, and the claim about DNMT3L co-delivery could lead to unnecessary experimental complexity.
- **Resolution test** Provide accurate size ranges for each effector domain with appropriate citations. Clarify the specific EZH2 variant being described and specify under what conditions DNMT3L co-delivery is required.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Logical coherence
- **Claim pointer** The manuscript states that "the pre-existing epigenetic landscape of a target locus is a major determinant of the outcome of programmable epigenetic editing" and later claims that "durable epigenetic editing is achieved not simply by depositing a regulatory mark but by initiating endogenous maintenance circuits."
- **Evidence pointer** Sections "Chromatin context as a determinant of editing efficiency" and "Epigenetic memory and the heritability of installed marks", location not provided
- **Concern** The manuscript does not clearly distinguish between epigenetic editing (modification of marks) and transcriptional modulation (direct activation or repression of transcription). Several systems described, such as VP64 and VPR, are primarily transcriptional activators that do not necessarily establish stable epigenetic marks. The claim that these systems achieve "epigenetic editing" conflates transient transcriptional effects with heritable epigenetic changes. This distinction is critical for the central thesis of the review.
- **Why it matters** The review's premise is that epigenetic landscape characterization guides editing strategy. If the systems discussed do not actually edit the epigenome but rather modulate transcription transiently, the framework presented is incomplete or misleading. Readers need clarity on which systems establish heritable changes and which produce transient effects.
- **Resolution test** Clearly define epigenetic editing versus transcriptional modulation. For each system described, specify whether it establishes heritable epigenetic changes or produces transient transcriptional effects, and adjust the central framework accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The manuscript discusses machine learning approaches for predicting editing outcomes and states that "deep-learning models trained on large CRISPR activity datasets now outperform traditional rule-based approaches for predicting on-target efficiency."
- **Evidence pointer** Section "Machine learning for epigenetic editor design", location not provided
- **Concern** The machine learning section is underdeveloped relative to its stated importance. Only one specific example (Song et al.) is described in any detail, and the discussion of deep learning models for CRISPR activity prediction is generic without specific model names, training data characteristics, or performance metrics. The claim that transfer learning approaches "further refine these predictions" is made without specific examples or citations.
- **Why it matters** The review positions machine learning as an increasingly important component of rational editor design. Without concrete examples, model descriptions, and performance comparisons, this section does not adequately support the claim that AI-driven approaches are advancing the field.
- **Resolution test** Expand the machine learning section with specific models, their training data, validation approaches, and quantitative performance comparisons. Provide concrete examples of how these models have been applied to epigenetic editing design.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical accuracy
- **Claim pointer** The manuscript states that "nucleosome occupancy can directly impede dCas9 binding, so that dense, compact chromatin occludes access while accessible regions permit efficient recruitment and effector activity."
- **Evidence pointer** Section "Chromatin context as a determinant of editing efficiency", location not provided
- **Concern** This statement oversimplifies the relationship between chromatin state and dCas9 binding. While nucleosome occupancy can impede dCas9 binding, the relationship is more nuanced. Studies have shown that dCas9 can bind to nucleosomal DNA under certain conditions, and chromatin state effects on dCas9 binding are context-dependent. The statement as written implies a binary relationship that does not reflect the current understanding.
- **Why it matters** The central thesis of the review depends on the claim that chromatin state determines editing outcomes. An oversimplified description of this relationship could mislead readers about the predictability of editing outcomes based on chromatin features alone.
- **Resolution test** Provide a more nuanced discussion of the relationship between chromatin state and dCas9 binding, citing specific studies that examine nucleosome occupancy effects on dCas9 binding and editing efficiency.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The manuscript discusses therapeutic applications in cancer, inherited disorders, and infectious diseases, and claims that epigenetic editing "represents a promising therapeutic paradigm" for these conditions.
- **Evidence pointer** Section "Therapeutic applications", location not provided
- **Concern** The therapeutic applications section is largely descriptive and lacks critical evaluation of the translational challenges. For example, the discussion of CAR T cell epigenetic editing mentions the work of Azcona et al. but does not discuss potential off-target effects, delivery efficiency in primary T cells, or long-term stability of the edited state in vivo. The HBV example is presented as promising but the limited clinical data available is not critically assessed.
- **Why it matters** A review aimed at informing translational research should provide balanced assessment of both promise and challenges. Without critical evaluation, the review risks presenting an overly optimistic view that does not adequately prepare readers for the realities of clinical translation.
- **Resolution test** Add critical discussion of translational barriers for each therapeutic application, including delivery efficiency, off-target effects, durability of effects, and regulatory considerations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that epigenetic marks are "reversible chemical modifications" but does not mention that some marks are more stable than others, which is relevant to the heritability discussion later in the review.
- **Required correction** Consider adding a brief qualifier about the variable stability of different epigenetic marks.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "Programmable transcriptional repression"
- **Evidence pointer** Section "Programmable transcriptional repression", location not provided
- **Issue** The description of KRAB-mediated silencing states that it recruits "KAP1 and thus SETDB1, which introduces H3K9me3 and HP1 family proteins." The phrasing is slightly ambiguous regarding whether HP1 proteins are introduced by SETDB1 or independently recruited.
- **Required correction** Clarify the recruitment hierarchy: KRAB recruits KAP1, which recruits SETDB1 (depositing H3K9me3) and other factors including HP1.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Programmable transcriptional repression"
- **Evidence pointer** Section "Programmable transcriptional repression", location not provided
- **Issue** The sentence describing ZIM3-KRAB contains a parenthetical with an exclamation mark, which is inappropriate for a scientific review.
- **Required correction** Remove the exclamation mark and rephrase the sentence for formal scientific tone.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Epigenetic memory and the heritability of installed marks"
- **Evidence pointer** Section "Epigenetic memory and the heritability of installed marks", location not provided
- **Issue** The discussion of heritability focuses on DNA methylation and H3K9me3 but does not mention other heritable marks such as H3K27me3 or the role of histone variants.
- **Required correction** Consider adding brief discussion of other heritable marks or justify the focus on DNA methylation and H3K9me3.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Therapeutic applications"
- **Evidence pointer** Section "Cancer epigenetics and therapy", location not provided
- **Issue** The sentence "therapeutically derepresses transposable elements (TEs) in cancer cells" appears to be missing a subject, likely referring to DNMT inhibitors.
- **Required correction** Add the subject, e.g., "DNMT inhibitors therapeutically derepress transposable elements (TEs) in cancer cells."

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "Therapeutic applications"
- **Evidence pointer** Section "Inherited disorders", location not provided
- **Issue** The manuscript states that epigenetic editing can "selectively silence a disease-causing allele or activate a silenced beneficial allele while preserving the normal counterpart." This implies allele-specific editing, which is not always achievable with the systems described.
- **Required correction** Clarify that allele-specific editing requires additional specificity mechanisms beyond standard PEMs.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Structure
- **Affected element** Conclusions
- **Evidence pointer** Conclusions, location not provided
- **Issue** The Conclusions section contains a duplicated phrase: "Despite progress, several challenges remain. Despite substantial advances, several challenges must be addressed before widespread clinical implementation."
- **Required correction** Remove the redundant sentence and merge the two statements.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Epigenetic detection technologies"
- **Evidence pointer** Section "DNA methylation", location not provided
- **Issue** The discussion of bisulfite sequencing limitations mentions inability to distinguish 5-methylcytosine from 5-hydroxymethylcytosine, but does not mention oxidative bisulfite sequencing (oxBS-seq) or Tet-assisted bisulfite sequencing (TAB-seq) as solutions.
- **Required correction** Consider adding brief mention of these methods to provide a more complete picture.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Multicomponent recruitment platforms"
- **Evidence pointer** Section "Multicomponent recruitment platforms", location not provided
- **Issue** The description of the coiled-coil platform states it "can also serve as an alternative to SunTag" but does not clearly explain the advantages or disadvantages compared to SunTag.
- **Required correction** Add brief comparison of the two systems in terms of size, modularity, and efficacy.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "Programmable transcriptional activation"
- **Evidence pointer** Section "Programmable transcriptional activation", location not provided
- **Issue** The manuscript states that VP64 "activates transcription by recruiting general transcription factors, Mediator components, and RNA polymerase II." This is a simplified description; VP64 primarily recruits Mediator and general transcription factors indirectly.
- **Required correction** Refine the mechanistic description to reflect current understanding of VP64 function.

## Risk / unsupported claims
- The claim that "systematic analyses of dCas9-based epigenome editors make this dependence explicit" (referring to chromatin state predicting editing outcomes) is supported by a single citation without specific data presented; the strength of this claim cannot be fully evaluated from the provided text.
- The statement that CHARM is "compact" and "particularly attractive for delivery-constrained applications" is presented without quantitative size comparison to other systems.
- The claim that "CRISPRoff can reverse CRISPRoff-induced silencing" (in the CRISPRon description) is circular and likely a typographical error; the intended meaning appears to be that CRISPRon can reverse CRISPRoff-induced silencing.
- The clinical trial description for EPI-003 (HBV epigenetic editing) is presented as factual but no trial phase, patient data, or interim results are provided; the claim that it offers a "functional cure" is speculative at this stage.
- The statement that epigenetic editing "eliminates the risks of genotoxicity, chromosomal translocations, and deleterious indels" in the context of CAR T cells is presented as absolute; while these risks are reduced, the claim of complete elimination is not supported by the evidence provided.
- The assertion that "AI-driven frameworks are expected to evolve from guide RNA-prediction tools into integrated decision-support systems" is speculative and presented as near-certain rather than as a possibility.
- The manuscript claims that "the pre-existing epigenetic landscape of a target locus is a major determinant of the outcome of programmable epigenetic editing" but does not provide quantitative evidence or effect sizes from the cited studies to support the magnitude of this dependence.