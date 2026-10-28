# Disruption of CD91 association with AXL and Fgr abrogates HSP-mediated signaling and cancer immunosurveillance


## ABSTRACT
  CD91 serves as a receptor that causes the activation of antigen-presenting cells in response to cancer cells by binding HSPs. In this context, the HSP–CD91 axis is responsible for the rejection of emerging and nascent cancers. The role of CD91 in the cross-presentation of HSP-chaperoned peptides is well established, but its contribution to cell signaling and costimulation is less clear. We investigated CD91-mediated signaling with respect to cancer immunosurveillance by examining two key adaptor proteins, Fgr and AXL. To investigate the interactions between the β chain of CD91 and Fgr and AXL, AlphaFold was used to predict protein‒protein binding areas. Signaling was further investigated by examining NF-κB phosphorylation and cytokine production in iBMDMs with CRISPR-induced tyrosine mutations. Mice conditionally lacking Fgr and AXL in dendritic cells were assessed for their ability to control tumors in inducible and transplantable models of cancer. In silico or CRISPR-mediated disruption of key tyrosines within CD91 abrogates Fgr binding, NF-κB activation, and cytokine release. Using a DC-specific Fgr knockout mouse model, we revealed that loss of Fgr severely impaired tumor immunosurveillance, whereas AXL knockout resulted in a milder phenotype, suggesting a greater downstream role. Loss of Fgr also prevents the development of adaptive immunity to tumors following HSP immunization, but it has no impact on transplantable tumor growth. These findings elucidate key components of the CD91 signaling mechanism, advancing our understanding of how dying tumor cells initiate adaptive immune responses and providing a therapeutic target to enhance this pathway.


## Introduction
  Select members of the heat shock protein (HSP) family are immunogenic and mediate their functions through interaction with CD91, a cell surface receptor expressed on dendritic cells and macrophages.1‐4 Although HSPs are primarily intracellular proteins, their release from cells following cell death, provides an important mechanism by which dying cells elicit immune responses.4‐6 The responses mediated through the HSP-CD91 axis are inflexible for cancer immunosurveillance since it has been shown that nascent, emerging tumors are not controlled and grow progressively in mice lacking CD91 expression on dendritic cells (DCs).7,8 In humans, CD91 dysfunction is firmly linked to more rapid tumor progression.8‐10 As a major conduit for these immune responses, CD91 serves two functions; first it allows the cross-presentation of HSP-chaperoned peptides, which can then be recognized by T cells after presentation on MHC.1‐4 The HSP chaperoned peptides reflect the antigenic repertoire of the dying cell.3,4,11‐13 Second, HSP binding to CD91 initiates signaling cascades within the antigen-presenting cells (APCs) that culminates in release of cytokines and upregulation of co-stimulatory molecules.5,14,15 We have shown that the signaling cascade begins with the phosphorylation of CD91 β chain and association with two key adaptor proteins Fgr and AXL.14 HSP-stimulated APCs therefore possess the signals necessary for priming T cell responses and activating NK cells.15‐17 These constitute the cellular components necessary for tumor rejection in the setting of cancer immunosurveillance8,9 and can be modeled by vaccination and therapy of tumor-bearing mice and humans with tumor-derived HSPs.18‐22

  Here, we investigate a key gap in knowledge regarding the interaction of Fgr and AXL with CD91 and the importance of these interactions in mounting anti-tumor immune responses. We show that Fgr associates with the β chain of CD91 and that this interaction is mediated by the phosphorylation of two Tyr residues within the β chain of CD91. With CRISPR-mediated mutation of one or both Tyr residues, we showed that Fgr forms a bridge between the CD91 β chain and other adaptor proteins, including AXL. Interruption of these interactions abrogates signaling in DCs, as measured by NF-κB activation and cytokine release. We created a first-in-one type of DC-specific Fgr knockout mouse and showed that these mice are deficient in immunosurveillance of cancer. Compared with control mice, DC-specific AXL knockout mice presented a milder phenotype, indicating a more distal location within the signaling cascade. Overall, our studies fill key gaps in our understanding of cancer immunosurveillance, specifically with respect to the identity of tumor-derived molecules that can trigger DC priming of T cell and NK cell responses.


### Methods
  All methods below were carried out in accordance with the relevant guidelines and regulations as outlined by the University of Pittsburgh.


### Mouse models and cell lines
  C57BL/6 mice and B6.Cg-Tg(Itgax-cre)1-1Reiz/J (CD11cCre) mice were purchased from The Jackson Laboratory (Bar Harbor, ME). Fgrfl/fl mice were also obtained from Drs. Joel Greenberger and Amitava Mukherjee at the University of Pittsburgh. AXLfl/fl mice were obtained from Dr. Carla Rothlin at The Masonic Cancer Center, University of Minnesota (MCC). These mice were crossed with CD11cCre mice to obtain Fgrfl/flCD11cCre and AXLfl/flCD11cCre offspring, resulting in specific knockout of these kinases within CD11c-expressing cells. For all tumor studies, female mice aged 6–8 weeks were used. The mice were housed in our DLAR facilities and used under experimental protocols approved by the University of Pittsburgh Institutional Animal Care and Use Committee (IACUC), which is also in accordance with the American Veterinary Medical Association. The D122 cell line (a metastatic derivative of Lewis lung carcinoma)23 was obtained from the American Type Culture Collection (ATCC) and was mycoplasma free. Immortalized bone marrow-derived macrophages (iBMDMs) were a gift from Dr. Maninjay Atian and at the University of Pittsburgh. Both cell lines were cultured in complete DMEM containing 1% pen-strep, 1% sodium pyruvate, 1% L-glutamine, 1% nonessential amino acids, 0.1% 2-mercaptoethanol, and 10% heat-inactivated FBS (GIBCO). At the end of the study, all the mice were euthanized in accordance with the guidelines of the University of Pittsburgh Institutional Animal Care and Use Committee (IACUC) and the American Veterinary Association. For euthanasia and the final disposition of the mice, the following procedure was used: CO2 from the tank into the enclosed chamber at a flow rate of 30%−70% until the mouse stopped breathing and remained unresponsive (to toe pinch). CO2 euthanasia was followed by cervical dislocation or thoracic rupture as a secondary method.


### Protein structure predictions with AlphaFold3.0
  Protein structure and protein‒protein interactions were predicted using AlphaFold 3.0.24,25 All modeling and visualization were performed via PyMOL. The protein sequences used for predictions are provided below. All protein sequences were imported from UniProt (https://www.uniprot.org/). Reference codes for CD91, AXL, and Fgr are Q91ZX7, Q00993, and P14234, respectively.

  AXL isoform 1 peptide comprises amino acids 770−823 as follows:

  DGLYALMSRCWELNPRDRPSFAELREDLENTLKALPPAQEPDEILYVNMDEGGS

  Fgr (SH2-SH3 domain) peptide comprises amino acids 57−296:

  GNMRSISGTGVTIFVALYDYEARTGDDLTFTKGEKFHILNNTEYDWWEARSLSSGHRGYVPSNYVAPVDSIQAEEWYFGKISRKDAERQLLSSGNPQGAFLIRESETTKGAYSLSIRDWDQNRGDHIKHYKIRKLDTGGYYITTRAQFDSIQDLVRHYMEVNDGLCYLLTAPCTTTKPQTLGLAKDAWEIDRNSIALERRLGTGCFGDVWLGTWNCSTKVAVKTLKPGTMSPKAFLEEAQ

  CD91 β chain peptide comprises amino acids 4464−4517 as follows:

  MNVEIGNPTYKMYEGGEPDDVGGLLDADFALDPDKPTNFTNPVYATLYMGGHG

  Mutations to phenylalanine were performed on the same peptide and then reinserted to AlphaFold 3.0 for protein-protein predictions.


### HSP purification
  Gp96 was isolated from C57BL/6 livers or D122 tumors as previously described.11,26 The purity and size of HSP preparations was verified via SDS-PAGE and immunoblotting. For all in vitro experiments, a final concentration of 100 µg/mL gp96 was used. For in vivo tumor prophylaxis experiments, 3 µg of liver or tumor-derived gp96 was injected for each immunization.17,19,27


### CRISPR-targeted mutagenesis of CD91 β chain tyrosines
  HDR donor templates and Cas9 guide RNAs targeting CD91 were designed with the Alt-R™ CRISPR HDR Design Tool. CRISPR was then performed with the IDT quick reference guide for HDR. Nucleofection was performed using the SF Cell Line Kit (Lonza) on the Amaxa™ 4-D Nucleofector® using the DN−100 program. DNA was extracted after 72 hours to assess mutations and then cloned to obtain clonal mutant cell lines.


### Immunoblotting
  To detect the phosphorylation status of signaling proteins, iBMDMs (1 × 106) were seeded in 6-well plates overnight. The wells were then pulsed with HSP for 1 h and lysed with cold NP40 lysis buffer (Halt protease and phosphatase inhibitors added). Laemmli buffer was added to equivalent amounts of cell lysate (30 µg), and the samples were boiled for 5 min prior to separation on SDS‒PAGE gels. The proteins were then transferred to PVDF membranes and probed with the following antibodies: rabbit α-NF-κB p65 pS536 (3033) and rabbit α-NF-κB p65 (8242). The membranes were then incubated with HRP-linked secondary antibodies. Antibodies were purchased from Cell Signaling Technology. All the immunoblots were run on a single membrane when possible. The membranes were developed using a ProteinSimple™ FlourChem E imager and quantified using ImageJ. Raw images are provided in Supplementary Figures 6 and 7.


### Cytokine detection via ELISA
  iBMDMs (1 × 106) were plated in 6-well plates overnight. The cells were treated with gp96 for 20 h. After stimulation, the supernatant was harvested and spun down to remove particulates. Cytokine production was measured in the supernatant using Mouse IL−6 and TNF-α ELISA Kit (Invitrogen) according to the manufacturer's instructions.


### Tissue processing for flow cytometry
  All spleens and LNs obtained from the mice were minced and digested in RPMI with 5% FBS, 250 µg/mL collagenase D (Sigma), and DNase I (Sigma-Aldrich) for 45 min at 37 °C as previously described.28 After digestion was complete, single-cell suspensions from all the tissues were passed through 70 µm strainers.


### Flow Cytometry
  Single-cell suspensions were prepared, and surface staining with antibodies was performed on ice for 20 min in the dark in FACS buffer. Next, the cells were stained with Zombie UV viability dye in the dark for 15 min at room temperature in PBS. Antibodies were obtained from BioLegend and Beckton Dickinson (BD). Data were collected with Cytek Aurora (Cytek Biosciences), and analysis was performed with FlowJo version 10.8.1.


### Carcinogen (MCA) – induced tumors
  Tumours (fibrosarcomas)29 were induced in mice via intradermal injection of 200 µg of MCA (Millipore Sigma) dissolved in peanut oil (Millipore Sigma). The mice were monitored every three days for 16 weeks. The visual appearance of any nodule at the site of injection was considered the tumor incidence. Tumor growth was measured on two axes and plotted as the average tumor diameter.


### D122 Transplantable Tumor Growth Assay
  8.5 × 105 D122 tumor cells were injected intradermally into Fgrfl/flCD11cCre and AXLfl/flCD11cCre mice alongside floxed littermate controls. Tumor growth was measured on two axes and plotted as average tumor diameter.


### HSP-mediated Tumor Prophylaxis
  Fgrfl/flCD11cCre and AXLfl/flCD11cCre mice and floxed littermates were intradermally immunized with 3 µg of liver or D122-derived gp96 at 21 and 14 d prior to intradermal challenge with 850,000 D122 cells.4,30,31 Tumor growth was measured on two axes and plotted as average tumor diameter for 2−3 weeks after tumor challenge.


### Statistical analysis
  Data are presented as the mean ± SD. Statistical analysis was performed using Student's t test or two-way ANOVA with GraphPad Prism. Significance is depicted with asterisks on the graph as follows: *p < 0.05, **p < 0.01.


## Results

### Fgr interacts with the membrane distal NPxY motifs in the β chain of CD91
  We had previously shown the physical association of CD91 and Fgr by co-immunoprecipitation and microscopy.14 To understand the nature of this association at the molecular and structural level, we used AlphaFold 3.0 to predict protein‒protein interactions and identify interacting amino acid residues. In this two-protein model, AlphaFold 3 predicts that these proteins interact with an ipTM of 0.61 in the configuration depicted in Figure 1A. There are two NPxY motifs in the β chain of CD91. In this predicted structure, the membrane distal NPxY motif of CD91 interacts directly with residues R139, R159, T163, Y186, and K187 on Fgr, while the membrane proximal NPxY makes minimal contacts with the CD91 β chain (Figure 1B, C). These residues within the SH2 region of Fgr are canonically involved in phosphotyrosine binding.32 To address the contribution of each CD91 NPxY motif and their phosphorylation, in this interaction, each tyrosine was mutated to phenylalanine and placed in the model with Fgr. Mutating the membrane proximal tyrosine (Y1F) had little impact on protein interactions, with an ipTM of 0.62 (Figure 1D, E). Mutation of the distal tyrosine (Y2F) disrupts the binding with an ipTM of 0.45 (Figure 1F, G). The most drastic interruption of the CD91-Fgr interaction was observed when both NPxY motifs in the β chain were mutated (2YF), with an ipTM of 0.22 (Figure 1H). In this model, the predicted CD91-Fgr interactions are therefore reliant on both NPxY motifs on CD91.


### CD91 β-chain NPxY motifs mediate signal transduction and cytokine release
  Mutations of Tyr within the NPxY motif of CD91 are predicted to disrupt the interaction with Fgr, as shown in Figure 1. To verify this function, we chose the CD91-expressing immortalized macrophage line iBMDM and created single (Y1F, Y2F) and double mutations (2YF) of tyrosine to phenylalanine using CRISPR mutagenesis (Figure 2A). Mutagenesis was confirmed via sequencing after single-cell cloning (Supplemental Figure 1A-C). We pulsed WT or mutated cells with the CD91 ligand gp96 and monitored NF-kB activation. Mutation of each Tyr, alone or together, abrogated NF-kB activation following gp96 treatment (Figure 2B and C). Notably, mutation of the proximal tyrosine (Y1F) leads to increased basal phosphorylation of NF-κB, but this phosphorylation does not increase upon gp96 stimulation (Figure 2B). The mutant cell lines were then assayed for the production of TNF-α and IL−6 following gp96 treatment. Mutation of both Tyr (2YF) residues resulted in significant loss of TNF-α and IL−6 production from cells (Figure 2D and E). Additionally, Y1F mutation also caused the loss of TNF-α but not IL−6 production in cells (Figure 2D). The mutant cells were fully capable of producing cytokines when stimulated with LPS, a CD91-independent mechanism (Supplementary Figure 1D). These results are consistent with the signaling pathway previously described.


### Fgr is required for CD91-mediated cancer immunosurveillance
  CD91 expression on APCs is required for cancer immunosurveillance.7,8 There is a gap in knowledge as to whether CD91 is required for both its endocytic (cross-presentation) and signaling (costimulation) functions in tumorigenesis and cancer immunosurveillance. To examine the latter, we created a first-in-kind DC-specific Fgr knockout mouse. To do this, Fgrfl/fl mice were crossed with CD11cCre mice to create dendritic cell-specific knockout mice. The mice were characterized, and significant loss of Fgr expression, specifically in DCs, was confirmed (Figure 3A, B). Immunoprofiling of the myeloid compartment of these mice revealed no differences in immune cell frequencies compared to WT mice (Supplemental Figures 2, 3). Fgrfl/flCD11cCre or WT littermates (Fgrfl/fl) were then challenged with the carcinogen methylcholanthrene (MCA) (Figure 3C). Fgrfl/flCD11cCre mice presented a significant increase in tumor incidence compared to Fgrfl/fl mice (Figure 3D). Additionally, tumors that formed in Fgrfl/flCD11cCre mice grew progressively at a greater rate compared to tumors that formed in Fgrfl mice (Figure 3E; Supplemental Figure 4 A).


### Fgr in DCs is essential for gp96-mediated anti-tumor immunity
  The immunogenicity of gp96/hsp90, hsp70 and calreticulin, which has clinical applications,20,21,33‐39 is dependent on CD91 expression on APCs. Loss of Fgr attenuates CD91-mediated signaling and the ability of APCs to release cytokines in response to HSPs, a component that drives antitumor responses but not their endocytic function. We purified gp96 from D122 tumors (D122 gp96) or from normal tissue (N-gp96) and tested its immunogenicity in Fgrfl/flCD11cCre or WT littermates (Fgrfl/fl) (Supplemental Figure 5). The mice were immunized with the gp96 preparations according to the schema in Figure 4A and challenged with D122 one week after the last immunization. Compared with normal tissue-derived gp96, tumor-derived gp96 reduced tumor growth in WT mice (Supplemental Figure 4B). This protection was lost in Fgrfl/flCD11cCre mice (Figure 4B; Supplemental Figure 4 C), indicating that CD91 signaling is an essential component of HSP-mediated tumor immune responses.


### Immune responses to transplanted tumors do not require Fgr
  Loss of CD91 function, either by its deletion, inhibition or downregulation, leads to faster growth of mouse and human tumors.8‐10,40 To determine whether CD91 signaling function is responsible for these effects, we transplanted D122 tumors into Fgrfl/flCD11cCre or WT littermates (Fgrfl/fl) (Figure 5A). We observed no difference in the tumor growth rate between the two mice groups (Figure 5B; Supplemental Figure 4D), suggesting that other functions of CD91 are necessary for its ability to protect mice from transplantable tumors.


### Fgr acts as a mediator of interaction between AXL and CD91
  Other adaptor proteins are known to associate with the CD91 intracellular signaling complex. We previously showed that AXL coimmunoprecipitates with CD91 and observed this association via confocal microscopy.14 We used AlphaFold 3.0 to gain structural insight into this association. When CD91, Fgr, and AXL are all modeled together, Fgr mediates the interaction between AXL and CD91 by forming a bridge (Figure 6A). This interaction has an ipTM value of 0.52. Although AXL does not directly associate with the CD91 b-chain, mutation of the two tyrosine residues in the CD91 β chain decreases the ipTM to 0.15 because this mutation impacts the Fgr association (Figure 6B). In the absence of Fgr, AXL and CD91 are not predicted to interact at all, with an ipTM of 0.05 (Figure 6C). Fgr may therefore perform a singular role to bridge the CD91 β chain and AXL, in which case AXL deficiency in DCs should mirror Fgr deficiency or may mediate other effects independently of AXL. To distinguish between these two propositions, we examined the role of AXL in cancer immunosurveillance by generating mice lacking AXL expression in DCs (Supplemental Figures 2, 3, and 6). AXLfl/flCD11cCre or WT littermates (AXLfl/fl) were administered via the MCA, and the tumor incidence was monitored. AXLfl/flCD11cCre mice presented a partial phenotype; although there was a trend toward greater tumor incidence than AXLfl/f mice did, this difference was not statistically significant (Figure 6D). However, tumors in AXLfl/flCD11cCre mice had an increased tumor growth rate compared to tumors in AXLfl/fl mice (Figure 6E; Supplemental Figure 7 A). Like Fgrfl/flCD11cCre mice, AXLfl/flCD11cCre mice presented no difference in the transplantable tumor growth rate compared to wild-type controls (Figure 6F; Supplemental Figure 7B).


## Discussion
  Herein, we examined the interaction between CD91 and Fgr and how its perturbation affects APC function and antitumor immunity. The signaling complex initiated by CD91 appears to be individualized to the ligand engaging the receptor. We previously reported that Fgr and AXL play a role in APCs in response to extracellular HSPs.14 The signals initiated by CD91 allow APCs to release cytokines that are central to antitumor immunity. Here, we investigated in depth the role of Fgr. Fgr forms a protein complex with CD91 that is dependent on its SH2-SH3 domains and on phosphorylated tyrosine residues on the β chain of CD91, which is consistent with known binding patterns.41‐43 Mutations in these CD91 tyrosines significantly lower the confidence of the interaction shown here. This effect has been shown to abrogate the ability of APCs to release the full complement of cytokines. In vivo, the lack of Fgr negatively impacts the ability of mice to reject nascent and emerging tumors and abrogates HSP-mediated antitumor immunity. These observations phenocopy those of mice with a DC-conditional knockout of CD91, suggesting that Fgr mediates all the downstream signaling initiated by CD91.7,8

  In the context of transplantable tumors, no difference was observed in mice lacking Fgr on dendritic cells. Therefore, for a large bolus of tumor cells, other mechanisms may be involved in priming adaptive immune responses, such as tumor-derived ATP or dsDNA, which can drive cytokine and costimulation by APCs.44‐47 This exemplifies the role of CD91 and HSPs in early tumorigenesis events, where low amounts of antigen and maturation markers are available for APC activation.48,49

  According to AlphaFold predictions, there appears to be no direct physical contact between AXL and CD91. We predicted that Fgr mediates the interaction of other adaptor proteins, including AXL, within the complex. AlphaFold predictions gave high confidence that this is the case. In support of these predictions, AXLfl/flCD11cCre mice presented an intermediate phenotype with respect to controlling nascent and emerging tumors. Given the observations in CD91fl/flCD11cCre, Fgrfl/flCD11cCre, and AXLfl/flCD11cCre mice, these findings suggest that Fgr plays a major role in adaptor protein complex formation and that AXL is only one of the other players in signal transmission. These signals were identified in a recent study.14

  This work expands upon the canonical role of AXL-Gas6 signaling in modulating immune responses. AXL has been associated with the promotion of immunosuppressive signaling in specific tumor microenvironments. In non-small cell lung cancer (NSCLC), tumor expression of AXL leads to increased levels of immunosuppressive monocytic DCs, neutrophils, and regulatory T cells (Tregs) within the tumor microenvironment (TME).50 Further supporting AXL's role in immune evasion, studies have shown that inhibiting AXL can restore sensitivity to PD−1 blockade in NSCLC patients.51 Here, we argue that AXL is also responsible for early antitumor responses in the HSP-CD91 pathway.

  Our results provide structural information on how AXL and Fgr interact with CD91 in APCs and translate this to in vivo relevancy. Collectively, these findings highlight the role of CD91-mediated signaling in cancer immunosurveillance mechanisms. We therefore propose that modulating this pathway to increase immune responses against developing tumors may represent a promising therapeutic approach.


## Supplementary Material

## Supplementary material
  Supplemental data for this article can be accessed at https://doi.org/10.1080/2162402X.2025.2581875.


## Disclosure of potential conflicts of interest
  No potential conflicts of interest were reported by the author(s).


## Acknowledgments
  We thank Dr. Smithgall for his input on Fgr biology. The AXLfl/fl mice were a very generous gift from Dr. Carla Rothlin at The Masonic Cancer Center, University of Minnesota (MCC). BioRender was used for the creation of diagrams.


## Author contributions
  RJB conceived the project. TH performed the experiments and analyzed the data in this manuscript with assistance from RJB. ALS, AJ and KS were involved in data collection and analysis. AM and JG aided in mouse experimental design and execution. TH and RJB wrote the manuscript with input from all contributing authors. The authors have no conflicts of interest.


## Data availability statement
  All data will be made available on reasonable request to the corresponding author RJB.


## Animal studies
  The mice were housed in our DLAR facilities and used under experimental protocols approved by the University of Pittsburgh Institutional Animal Care and Use Committee (IACUC), which is also in accordance with the American Veterinary Medical Association.

  We have adhered to ARRIVE guidelines. All animal work was covered by the University of Pittsburgh Institutional Animal Care and Use Committee (IACUC) protocols; 22122458, 23012569, 22121615, 23012459.


## List of Abbreviations
  DCdendritic cellsAPCsAntigen presenting cellsHSPsheat shock proteinsdsDNAdouble-stranded DNAiBMDMimmortalized bone marrow-derived macrophageMCAmethylcholanthrene