## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, author contributions, conflict of interest statement, data availability statement, and acknowledgments. Supporting information files (tables, figures) are referenced but not provided.
- **Assessment boundary** The review assesses the scientific claims, methodology, and conclusions presented in the manuscript. It does not assess the editorial fit for a specific journal, but evaluates the work against general standards of scientific rigor and significance.
- **Shared manuscript claim summary** The authors propose that isoprene functions as a signaling molecule in plants by integrating with existing stress and hormone signaling pathways. They analyze cis-regulatory elements (CREs) in promoters of isoprene-responsive genes to identify transcription factors (TFs) potentially involved in isoprene signaling. They further test, via molecular dynamics simulations, whether isoprene can bind to the START domain of the class IV HD-ZIP TF HDG11, hypothesizing this as a potential sensing mechanism. The results show overrepresentation of specific CREs (e.g., for ARR1, Dof, MYB, WRKY) and underrepresentation of others (e.g., CBF, HSF). Simulations suggest that the HDG11 START domain does not significantly interact with membrane-embedded isoprene, leading the authors to conclude that HDG11 is unlikely to be a direct isoprene receptor.
- **Visible evidence base** The manuscript provides results from promoter analysis (Tables 1, 2, S2, S3, S4) and molecular dynamics simulations (Figure 3, S1). The methods are described in the main text and a supporting information document (not provided). The list of isoprene-responsive genes is from a previous publication (Zuo et al., 2019) and is provided as Table S1 (not provided).
- **Missing materials affecting confidence** The supporting information files (Tables S1-S4, Figure S1, detailed simulation methodology) are not provided. This limits the ability to verify the completeness of the promoter analysis, the specific gene list used, the parameters of the molecular dynamics simulations, and the statistical significance of the findings.

## Reviewer
- **Overall assessment** This manuscript presents a bioinformatics analysis of promoter elements in isoprene-responsive genes, combined with a computational assessment of isoprene binding to a candidate protein, HDG11. The promoter analysis is descriptive and provides a useful catalog of potential TF families involved in isoprene responses. However, the study is largely correlative and does not provide functional validation of the identified CREs or TFs. The negative result from the molecular dynamics simulations, while clearly presented, is based on a homology model and specific simulation conditions that may not fully capture the in vivo context. The manuscript is clearly written and the conclusions are appropriately cautious, but the overall impact is limited by the lack of experimental follow-up and the reliance on a single computational approach for the binding question.
- **Who would be interested in the results, and why** Researchers studying isoprene emission and its biological functions, particularly in the context of abiotic and biotic stress tolerance. The promoter analysis may be of interest to those working on transcriptional regulation in stress responses. The computational methods for testing protein-ligand interactions could be of interest to a niche group of computational biologists, but the negative result limits its broader appeal.
- **Major strengths**
  1. The study addresses a timely and important question regarding the mechanism of isoprene signaling, a topic with significant implications for understanding plant stress responses.
  2. The promoter analysis is systematic and uses a well-established database (AGRIS), providing a comprehensive overview of potential regulatory elements.
  3. The authors are appropriately cautious in their interpretation, particularly regarding the negative simulation results, and clearly state the limitations of their approach.
  4. The integration of bioinformatics and computational biophysics is a novel approach to this problem.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that specific CREs are "overrepresented" or "underrepresented" in promoters of isoprene-responsive genes, and use this to infer the involvement of corresponding TFs in isoprene signaling.
  - **Evidence pointer** Results section, Tables 1, S2, S3, S4. The statistical method for determining over/underrepresentation is not described in the main text and is not available in the provided materials.
  - **Concern** The criteria for overrepresentation (≥75% of promoters) and underrepresentation (≤49%) appear arbitrary and are not based on a statistical test that accounts for background frequency of these motifs in the Arabidopsis genome. Without a proper statistical framework (e.g., hypergeometric test, Fisher's exact test, or comparison to a random promoter set), the identified enrichments may be misleading. For example, a motif present in 75% of a small gene set might not be significantly enriched if it is present in 70% of all promoters genome-wide.
  - **Why it matters** The core conclusion of the promoter analysis, which is the identification of specific TF families as likely mediators of isoprene signaling, rests entirely on the validity of the enrichment calls. If the calls are not statistically robust, the entire premise of the paper is weakened.
  - **Resolution test** The authors must provide a clear description of the statistical test used, including the background model (e.g., all Arabidopsis promoters) and the significance threshold. They should provide p-values or confidence intervals for the enrichment of each reported CRE. If no statistical test was used, the analysis should be re-done with an appropriate method.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors conclude that "a significant interaction between isoprene within the membrane bilayer and the START domain of HDG11 could not be detected" and that HDG11 is "probably not such a receptor protein."
  - **Evidence pointer** Results section, Figure 3, Figure S1. The detailed simulation methodology is in the supporting information, which is not provided.
  - **Concern** The conclusion is based on a single homology model of the HDG11 START domain. The quality of this model is not assessed in the main text. The simulation time, force field parameters, and the method for placing the protein relative to the membrane are not described in the main text. The negative result could be an artifact of the model or the simulation setup. For example, if the protein was not allowed sufficient time to sample membrane-inserted states, or if the initial orientation was unfavorable, the lack of interaction would not be conclusive. Furthermore, the authors only tested one protein (HDG11) and one set of conditions. The claim that HDG11 is "probably not" a receptor is too strong given these limitations.
  - **Why it matters** The negative binding result is a key negative finding of the paper. If it is not technically robust, it could be misleading and could discourage research on START domain proteins as isoprene sensors. The authors' conclusion goes beyond what can be supported by a single computational study.
  - **Resolution test** The authors must provide details of the simulation setup (force field, simulation time, number of replicates, membrane composition) and an assessment of the model quality (e.g., Ramachandran plot, QMEAN score). They should also discuss the limitations of their approach and soften their conclusion to state that "no significant interaction was detected under the conditions tested" rather than making a general claim about HDG11's function.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors state that "the cross-talk between isoprene-mediated signaling and other growth regulator and stress signaling pathways, in terms of common CREs and transcription factors could enhance the stability of the isoprene emission trait when it evolves in a plant."
  - **Evidence pointer** Discussion section. This is a speculative claim.
  - **Concern** This is a purely speculative evolutionary argument. The authors provide no evidence that the presence of common CREs would enhance the "stability" of the isoprene emission trait. This is a complex evolutionary claim that requires a population genetics or comparative genomics framework to be meaningful. As stated, it is an unsupported assertion.
  - **Why it matters** This claim is presented as a key takeaway of the study, but it is not a testable hypothesis derived from the data. It overreaches the scope of the bioinformatics analysis.
  - **Resolution test** The authors should either remove this claim or reframe it as a hypothesis for future research. They should avoid making definitive statements about evolutionary stability without supporting evidence.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, "Molecular simulations and modeling to test interactions between isoprene and a class IV HD-ZIP family START-domain-containing protein were carried out."
  - **Issue** The abstract is dense and uses jargon (e.g., "class IV HD-ZIP family START-domain-containing protein") without sufficient context for a general reader. The significance of the negative result is not clearly stated.
  - **Required correction** The abstract should be revised to briefly explain what a START domain is and why testing isoprene binding to it is relevant. The conclusion should be more explicit, e.g., "Simulations suggest that direct binding of isoprene to the START domain of HDG11 is unlikely, indicating that other mechanisms of isoprene sensing may exist."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods
  - **Evidence pointer** Materials and Methods, "Analysis of CREs present in promoters of isoprene-responsive genes"
  - **Issue** The description of the promoter analysis is brief. It is not clear how the 3-kb upstream regions were defined (e.g., relative to the transcription start site) or how the gene list from Zuo et al. (2019) was filtered (e.g., were all differentially expressed genes used, or only those with a certain fold-change?).
  - **Required correction** Provide more detail on the promoter sequence retrieval and the criteria for including genes in the analysis. This is essential for reproducibility.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Results
  - **Evidence pointer** Results, "CREs overrepresented in promoters of genes responsive to isoprene"
  - **Issue** The results section lists many TF names and motif types, which can be overwhelming. The connection between the identified CREs and the functional categories (e.g., stress responses) is not always explicit.
  - **Required correction** Consider adding a summary figure or table that groups the overrepresented CREs by functional category (e.g., hormone signaling, abiotic stress, biotic stress) to make the findings more accessible.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Results
  - **Evidence pointer** Results, "CREs underrepresented in promoters of genes responsive to isoprene"
  - **Issue** The authors note that CBF and HSF motifs are underrepresented, which is interesting given the known role of isoprene in heat tolerance. However, they do not discuss the potential implications of this underrepresentation in detail.
  - **Required correction** Expand the discussion on the underrepresentation of CBF and HSF motifs. This is a potentially important finding that deserves more interpretation.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of statistical rigor in the promoter enrichment analysis.
  - R1-M2: Insufficient detail and potential limitations of the molecular dynamics simulations.
- **Assessment against Nature-style criteria**
  - **Originality** The question of how isoprene is sensed is novel and important. The combination of promoter analysis and computational binding studies is a creative approach. However, the individual components (promoter analysis, MD simulations) are standard techniques.
  - **Scientific importance** The topic is of significant interest to the plant biology community, given the widespread emission of isoprene and its proposed roles in stress tolerance. However, the study is largely descriptive and does not provide a definitive answer to the sensing question. The negative result for HDG11 is useful but does not identify an alternative mechanism.
  - **Interdisciplinary readership** The work bridges bioinformatics and computational biophysics, which could appeal to a broad readership. However, the technical details of the simulations may be inaccessible to plant biologists, and the promoter analysis may be of limited interest to biophysicists.
  - **Technical soundness** The technical soundness is currently questionable due to the lack of statistical validation in the promoter analysis and the incomplete description of the simulation methodology. These issues must be resolved.
  - **Readability for nonspecialists** The manuscript is generally well-written, but the results section is dense with TF names and motif types. The abstract and discussion could be improved to better highlight the key findings and their significance for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core question is interesting, and the promoter analysis provides a useful resource. However, the statistical issues and the lack of detail in the simulations must be addressed. The conclusions should be tempered to reflect the limitations of the computational approach.

## Risk / unsupported claims
- The claim that specific CREs are "overrepresented" or "underrepresented" is not supported by a described statistical test.
- The claim that HDG11 is "probably not" an isoprene receptor is not fully supported by the simulations, which are based on a homology model and may not capture the full complexity of the in vivo environment.
- The evolutionary claim that common CREs "could enhance the stability of the isoprene emission trait" is speculative and not supported by data presented in this manuscript.
- The statement that "isoprene utilizes existing stress signaling networks for signaling purposes" is presented as a proposal, but the evidence provided is only correlative (promoter analysis) and does not demonstrate a mechanistic link.