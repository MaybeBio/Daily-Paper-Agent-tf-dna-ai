## Review setup
- **Input scope** Full manuscript text (abstract, introduction, main sections, future perspectives, conflict of interest, author contributions, acknowledgements)
- **Assessment boundary** Scientific content, structural coherence, evidence quality, and alignment with stated aims; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The manuscript is a review article that systematically examines the integration of protein three-dimensional spatial structure with artificial intelligence (AI) for predicting drug synergy and antagonism, covering biological mechanisms, structural basis of protein–drug interactions, AI methodologies, and applications in disease treatment, with emphasis on precision medicine.
- **Visible evidence base** Full text of the manuscript, including three tables (Tables 1–3) and three figures (Figures 1–3) referenced but not provided; 158 cited references listed in the text but not individually accessible
- **Missing materials affecting confidence** Figures 1–3 (referenced but not provided); Tables 1–3 (referenced but not provided); full reference list with complete bibliographic details; supplementary materials if any

## Reviewer
- **Overall assessment** This manuscript presents a broad and ambitious review of drug synergy and antagonism prediction, integrating protein spatial structure with AI. The topic is timely and of potential interest to a wide readership. However, the manuscript suffers from significant structural and conceptual issues. The title promises a "revolution" in precision medicine, but the content largely recapitulates well-known concepts without offering a critical synthesis or novel framework. The organization is fragmented, with overlapping sections and a lack of clear logical progression. The treatment of AI methods is superficial, and the claimed integration of protein structure with AI is not convincingly demonstrated. The absence of figures and tables in the provided material prevents full evaluation of the illustrative content. The manuscript reads more as a collection of loosely connected summaries than as a coherent, critical review. Major revisions are required to establish a clear thesis, provide depth over breadth, and substantiate the central claims.

- **Who would be interested in the results, and why** Researchers in computational drug discovery, medicinal chemistry, and structural biology may find the compilation of tools and methods useful as a starting point. Clinicians and translational researchers interested in precision medicine and combination therapy could also find the disease-specific examples relevant. However, the lack of critical depth and the absence of a unifying framework limit the value for specialists seeking advanced insights.

- **Major strengths** The manuscript covers a wide range of topics, from molecular mechanisms to AI algorithms, providing a broad overview. The inclusion of specific examples, such as the EHF/AJUA complex and sorafenib, grounds the discussion in concrete cases. The tables (though not provided) appear to offer comparative summaries of tools and methods, which could be useful reference material. The future perspectives section touches on important emerging areas, such as multi-omics integration and nanocarrier systems.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance and novelty
- **Claim pointer** The manuscript claims to "systematically reviews the latest research progress and application prospects of drug synergy and antagonism prediction methods that integrate protein three-dimensional spatial structure with artificial intelligence."
- **Evidence pointer** Abstract; Introduction; Sections on AI applications
- **Concern** The central claim of integration between protein spatial structure and AI is not convincingly demonstrated. The manuscript describes protein structure analysis and AI methods largely as separate topics. The AI section focuses on generic machine learning and deep learning algorithms applied to drug synergy prediction, but the specific role of protein three-dimensional structure as an input feature or constraint in these models is not clearly articulated. The "integration" appears to be a juxtaposition of two fields rather than a genuine synthesis.
- **Why it matters** The title and abstract promise a novel, integrated perspective. If the integration is not substantiated, the manuscript fails to deliver on its core promise and offers little beyond existing, separate reviews on drug synergy prediction and structure-based drug design.
- **Resolution test** The authors should provide a dedicated section or framework that explicitly demonstrates how protein structural data (e.g., binding site geometry, allosteric pockets, conformational dynamics) is incorporated into AI models for synergy/antagonism prediction. Concrete examples of such integrated models, with performance comparisons against non-structural models, would be required.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness and depth
- **Claim pointer** The manuscript states that it "systematically evaluates the practical application progress of AI technologies, especially machine learning and deep learning algorithms, in predicting drug synergy–antagonism effects."
- **Evidence pointer** Section "Applications of Artificial Intelligence in Drug Synergy–Antagonism Prediction"; Table 3 (not provided)
- **Concern** The treatment of AI methods is superficial. The manuscript lists algorithms (CNN, GNN, etc.) and mentions challenges such as interpretability and data heterogeneity, but does not provide a critical analysis of how these methods work, their specific advantages and limitations in the context of synergy prediction, or a comparative assessment of their performance. The discussion lacks technical depth, such as details on feature representation, model architectures, training data, and validation strategies. The referenced Table 3, if it contains such details, is not available for assessment.
- **Why it matters** A review that claims to evaluate AI methods must provide sufficient technical detail for readers to understand the state of the art and the relative merits of different approaches. Without this, the manuscript is of limited use to researchers seeking to apply or develop these methods.
- **Resolution test** The authors should expand the AI section to include a critical, method-by-method analysis, discussing model inputs (including structural features), architectures, training and evaluation protocols, and known limitations. A comparative table with performance metrics on benchmark datasets would strengthen the case.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Readability and structure
- **Claim pointer** The manuscript aims to provide a "systematic review" of the topic.
- **Evidence pointer** Overall manuscript structure
- **Concern** The manuscript is poorly organized. The introduction covers multiple concepts (drug synergy, protein structure, AI) without establishing a clear thesis or roadmap. Sections overlap significantly; for example, multi-target drug mechanisms are discussed in both the structural basis section and the disease application section. The flow from biological mechanisms to structural basis to AI methods to disease applications is logical in principle, but the execution is fragmented, with abrupt transitions and repetitive content. The absence of a concluding synthesis section leaves the reader without a clear take-home message.
- **Why it matters** A review must guide the reader through the material in a coherent manner. The current structure impedes comprehension and undermines the authority of the review.
- **Resolution test** The authors should restructure the manuscript with a clear introduction stating the scope and thesis, distinct and non-overlapping sections, and a concluding section that synthesizes the findings and outlines future directions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance and evidence quality
- **Claim pointer** The manuscript states that "protein spatial structures exhibit dynamic characteristics, with different structural conformations leading to configurational changes in binding sites, thereby significantly affecting drug affinity."
- **Evidence pointer** Introduction; Section "Structural Basis of Protein–Drug Interactions"
- **Concern** The discussion of protein dynamics and its impact on drug binding is largely qualitative. The manuscript mentions conformational changes but does not provide specific examples with quantitative data (e.g., binding affinity changes, kinetic parameters) or discuss methods such as molecular dynamics simulations that are essential for studying these phenomena. The claim that dynamics "significantly affect" affinity is presented as a general statement without supporting evidence.
- **Why it matters** The role of protein dynamics is a key aspect of the structural basis of drug action. A review that touches on this topic should provide concrete examples and references to quantitative studies to substantiate the claim.
- **Resolution test** The authors should include specific case studies where conformational dynamics have been shown to affect drug binding, with quantitative data, and discuss computational methods (e.g., MD simulations, ensemble docking) used to capture these effects.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and precision
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and uses jargon without definition (e.g., "druggability," "synergy-antagonism"). It also overstates the scope by claiming to cover "latest research progress" without specifying a timeframe.
- **Required correction** Define key terms at first use and specify the review period (e.g., "over the past five years"). Consider restructuring the abstract to state the review's purpose, methods, key findings, and implications more clearly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Accuracy of references
- **Affected element** Reference list
- **Evidence pointer** Reference list (not fully provided)
- **Issue** Some in-text citations appear to be grouped (e.g., [1,2,3,4]) without clear indication of which claim each supports. This is common but can be problematic if the grouped references do not all support the specific statement.
- **Required correction** Ensure that each citation is appropriate for the specific claim it supports. If grouped citations are used, verify that all cited works are relevant.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Applications of Drug Synergy–Antagonism in Disease Treatment"
- **Evidence pointer** Section text
- **Issue** The section on disease applications is heavily weighted toward cancer, with infectious and metabolic diseases receiving comparatively brief treatment. The metabolic disease subsection is particularly thin, with no specific examples of synergy or antagonism.
- **Required correction** Expand the sections on infectious and metabolic diseases with specific examples, or explicitly state that the focus is on cancer due to space constraints.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Various sections
- **Issue** The terms "synergy" and "antagonism" are used consistently, but the term "drug synergy-antagonism" is used as a compound noun in some places, which is awkward. Also, "AI" is used interchangeably with "machine learning" and "deep learning" without clear distinction.
- **Required correction** Use "drug synergy and antagonism" as separate terms. Clarify the relationship between AI, ML, and DL in the introduction.

- **Technical failings that need to be addressed before the case is established** R1-M1 (integration claim not substantiated), R1-M2 (superficial AI treatment), R1-M3 (poor organization). These are blocking because the manuscript's core promise and utility are compromised.

- **Assessment against Nature-style criteria**
  - **Originality** The topic is not new, and the manuscript does not offer a novel framework or perspective. The claimed integration of protein structure and AI is not demonstrated, so the originality is limited.
  - **Scientific importance** The topic is important, but the manuscript does not provide a critical synthesis that advances understanding. It is a compilation of known information.
  - **Interdisciplinary readership** The topic spans structural biology, computational chemistry, and AI, which could attract a broad audience. However, the lack of depth in each area may disappoint specialists, and the poor organization may deter nonspecialists.
  - **Technical soundness** The technical content is shallow, particularly in the AI section. The claims are not supported by quantitative evidence or critical analysis.
  - **Readability for nonspecialists** The manuscript is not accessible to nonspecialists due to undefined jargon and a fragmented structure. The abstract is particularly dense.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revisions to substantiate its central claim of integration, provide technical depth, and improve organization. If these issues are addressed, the manuscript could become a useful resource, but in its current form, it does not meet the standards for a high-impact review.

## Risk / unsupported claims
- The claim of "revolutionizing" drug synergy-antagonism in precision medicine is unsupported and hyperbolic.
- The claim that AI integration with protein structure "significantly enhances the prediction accuracy" is not backed by specific performance data or comparative studies.
- The statement that "protein spatial structures exhibit dynamic characteristics... significantly affecting drug affinity" is presented without quantitative evidence.
- The assertion that "AI technologies can effectively address these challenges" (referring to multi-target drug development) is speculative and not substantiated.
- The claim that "the integration of these technologies will significantly improve the clinical efficacy of combination therapies" is a forward-looking statement without supporting evidence.
- The effectiveness and comparative performance of the specific AI models mentioned (e.g., MCNN-DDI, Deep Docking) are not evaluated with data.
- The claim that "multi-target drugs... reduce adverse effects" is presented as a general benefit without discussing counterexamples or complexities.