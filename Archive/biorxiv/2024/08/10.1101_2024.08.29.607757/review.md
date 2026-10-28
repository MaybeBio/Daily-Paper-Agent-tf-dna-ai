## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, and data resources. No figures, tables, or supplementary materials were provided for review.
- **Assessment boundary** The review is based solely on the textual content of the manuscript as provided. Structural coordinates, experimental data, and figures referenced in the text could not be independently verified.
- **Shared manuscript claim summary** The authors report crystal structures of the cyanobacterial nitrogen regulator NtcA from *Synechococcus elongatus* PCC7942 in complex with DNA and 2-oxoglutarate (2OG), and of a quaternary PipX-NtcA-2OG-DNA complex. They further model this complex onto a recently reported cryo-EM structure of an NtcA transcription activity complex (TAC) with RNA polymerase, and use bacterial two-hybrid assays to support predicted PipX-RNAP interactions. The authors propose that PipX stabilizes the active DNA-binding-competent conformation of NtcA, increases NtcA-DNA contacts, and helps recruit RNA polymerase through direct interactions with the gamma and sigma subunits.
- **Visible evidence base** Text descriptions of crystallographic structures at 3.0 Å (NtcA-DNA-2OG), 3.8 Å (PipX-NtcA-DNA, crystal I), and 4.3 Å (PipX-NtcA-DNA, crystal II); EMSA data for wild-type and V187E mutant NtcA; bacterial two-hybrid interaction data; structural superimposition analyses; PDB accession codes for six deposited models.
- **Missing materials affecting confidence** Figures, tables (including Table 1 with crystallographic statistics), supplementary figures and tables, PDB coordinate files, EMSA gel images, and raw bacterial two-hybrid data were not available for inspection. This limits verification of structural quality, data interpretation, and the robustness of functional assays.

## Reviewer

- **Overall assessment** This manuscript addresses an important question in cyanobacterial gene regulation: how the master nitrogen regulator NtcA achieves DNA-binding specificity and how its coactivator PipX contributes to transcriptional activation. The authors provide the first experimental structure of NtcA bound to DNA, which is a significant advance given that previous structures lacked DNA. The structural analysis of DNA recognition is detailed and plausible, and the identification of residue V187 as a key specificity determinant is well supported by the EMSA data described. The modelling of PipX onto the NtcA-TAC structure and the subsequent bacterial two-hybrid validation of predicted PipX-RNAP contacts is a reasonable approach, though the moderate resolution of the PipX-NtcA-DNA structures (3.8-4.3 Å) and the indirect nature of the modelling warrant caution. The manuscript is generally well written and the logic is clear, but several technical aspects require clarification and additional evidence before the conclusions can be fully accepted.

- **Who would be interested in the results, and why** Researchers studying transcriptional regulation in bacteria, particularly those working on the CRP-FNR superfamily, will find the structural details of NtcA-DNA recognition valuable. The cyanobacterial research community will be interested in the mechanistic insights into nitrogen regulation and the role of PipX. More broadly, those interested in coactivator mechanisms and the diversity of transcriptional activation strategies across bacterial phyla will find the proposed PipX-RNAP recruitment model noteworthy. The work may also be relevant to researchers studying signaling integration, given the connection between PII, PipX, and NtcA.

- **Major strengths**
  1. The first experimental structure of NtcA bound to DNA, filling a significant gap in the field.
  2. Detailed analysis of DNA recognition, including identification of specific residues involved in base-specific contacts.
  3. The combination of structural, modelling, and functional approaches to address the role of PipX.
  4. The observation of a partially occupied PipX-binding site in one crystal form, which may have functional implications.
  5. Clear writing and logical presentation of the structural and functional data.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the crystal structure of the NtcA-DNA-2OG ternary complex at 3.0 Å resolution provides "unique detail on the specific recognition of the NtcA box" and that the interactions described explain the "exquisite specificity" of NtcA for its target DNA.
- **Evidence pointer** Results section, "The structure of the NtcA-DNA-2OG ternary complex" and "NtcA box recognition"; Table 1 (not provided)
- **Concern** The resolution of 3.0 Å is moderate for a protein-DNA complex, and the manuscript does not provide sufficient detail on the quality of the electron density for the DNA and the protein-DNA interface. At this resolution, the assignment of specific hydrogen bonds and van der Waals contacts between side chains and DNA bases requires careful validation. The authors state that the map allowed tracing of "most amino acid side chains" in the PipX-NtcA-DNA complex at 3.8 Å, which is concerning for the reliability of the detailed interaction analysis. Without access to the electron density maps, refinement statistics, or B-factor information, the accuracy of the described base-specific contacts cannot be fully assessed. The authors should provide a more detailed validation of the DNA conformation, including helical parameters, and demonstrate that the observed contacts are robust to model building choices.
- **Why it matters** The central claim of the paper rests on the accuracy of the protein-DNA interface. If the contacts are not well supported by the density, the conclusions about specificity determinants and the role of V187 would be weakened.
- **Resolution test** Provide electron density maps (e.g., 2Fo-Fc and Fo-Fc) for the DNA and the key interacting residues, along with refinement statistics including R-free, Ramachandran statistics, and coordinate error estimates. Show that the DNA conformation is well-defined and that the described contacts are consistent with the density. Ideally, the authors could also perform a systematic analysis of the interface using a program such as PISA or CONTACT to quantify buried surface area and hydrogen bonding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "PipX does not interact with DNA" and that it "increases NtcA-DNA contacts" based on the crystal structures of the PipX-NtcA-DNA complex.
- **Evidence pointer** Results section, "Structures of the PipX-NtcA-DNA complex"; Figures 2A-C (not provided)
- **Concern** The claim that PipX does not contact DNA is based on the crystal structure, but the resolution of the PipX-NtcA-DNA structures (3.8 and 4.3 Å) is limited. At these resolutions, weak or disordered contacts could be missed. The authors should provide a quantitative analysis of the distance between PipX and the DNA in the crystal structures, and ideally support this with complementary solution data, such as hydrogen-deuterium exchange or crosslinking, to confirm that PipX does not make direct DNA contacts. Additionally, the claim that PipX "increases NtcA-DNA contacts" is based on a comparison between the ternary and quaternary complexes, but the DNA sequences used in the two crystal forms differ (one is a half-site, the other a full site), which could confound the comparison.
- **Why it matters** The proposed mechanism of PipX action, which involves stabilizing the active conformation of NtcA and increasing its DNA contacts, depends on the accuracy of these structural observations. If PipX does make direct DNA contacts that were not resolved, the mechanism would need to be revised.
- **Resolution test** Provide a detailed comparison of the NtcA-DNA interface in the ternary and quaternary complexes, including a table of all protein-DNA contacts and their distances. Show that the additional contacts in the quaternary complex are statistically significant and not an artifact of the different DNA constructs. Ideally, the authors could perform mutagenesis of the PipX residues predicted to be near the DNA to test whether they affect DNA binding.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their modelling of the PipX-NtcA-DNA complex onto the NtcA-TAC structure (PDB 8H40) shows that PipX interacts with the gamma and sigma subunits of RNA polymerase, and that this is supported by bacterial two-hybrid assays.
- **Evidence pointer** Results section, "Modelling of PipX-RNAP interactions in the NtcA-TAC complex" and "Functional evidence for PipX-RNAP interactions provided by bacterial two-hybrid assays"; Figure 3 (not provided)
- **Concern** The modelling approach is described only briefly. The authors state that they superimposed their NtcA-DNA complex onto the NtcA subunit of the TAC structure, but the details of the superimposition (e.g., which atoms were used, the resulting RMSD) are not provided. The TAC structure is from *Anabaena* sp. PCC7120, while the NtcA structures are from *S. elongatus*, and the sequence identity between the two NtcA orthologs is not stated. The bacterial two-hybrid assays are described as providing "clear support" for the interactions, but the data are not shown, and the authors acknowledge false negatives. The specificity of the interactions is not fully established, as the authors do not report testing whether mutations in the predicted interface abolish the interaction.
- **Why it matters** The claim that PipX recruits RNA polymerase is a key novel finding of the paper. If the modelling is not robust or the two-hybrid data are not conclusive, this conclusion would be significantly weakened.
- **Resolution test** Provide details of the superimposition, including the RMSD and the number of residues used. Show the two-hybrid data in full, including all controls and replicates. Ideally, the authors should test the predicted interface by mutating key residues in PipX or the RNAP subunits and showing that the interaction is abolished. They could also perform a more rigorous computational analysis, such as a protein-protein docking or a molecular dynamics simulation, to support the predicted interface.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Originality
- **Claim pointer** The authors state that their work "expands the repertoire of mechanisms of transcriptional regulation, calling attention to the PipX coactivator protein, a specific regulator of cyanobacteria with no known functional counterparts in other taxonomic groups."
- **Evidence pointer** Introduction and Discussion sections
- **Concern** While the structural data are novel, the concept that PipX acts as a coactivator by stabilizing the active conformation of NtcA and potentially recruiting RNAP was already proposed in previous work by the same group (Llácer et al., 2010). The current manuscript provides additional structural support for this model, but the conceptual advance is incremental. The claim that PipX has "no known functional counterparts" is strong and would benefit from a more thorough discussion of potential analogous coactivators in other bacterial systems, even if they are not sequence homologs.
- **Why it matters** The novelty of the work is a key criterion for publication in a high-impact journal. If the conceptual advance is limited, the manuscript may be better suited for a more specialized journal.
- **Resolution test** The authors should clearly articulate what is conceptually new about their findings beyond the previous structural and functional data. They should also provide a more balanced discussion of potential functional analogs of PipX in other organisms.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction assume significant familiarity with the CRP-FNR superfamily and cyanobacterial nitrogen regulation. Terms such as "CRP-FNR superfamily," "2-oxoglutarate," and "PipX" are introduced without sufficient context for a general reader.
- **Required correction** Provide a brief explanation of the biological significance of nitrogen regulation in cyanobacteria and the role of NtcA in this process. Define key terms and acronyms upon first use.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, "Production and crystallization of NtcA-DNA, PipX-NtcA-DNA and of NtcA in inactive apo forms"
- **Evidence pointer** Methods section
- **Issue** The DNA sequence used for crystallization of the NtcA-DNA complex is described as containing "one half of the NtcA binding site of the S. elongatus glnA promoter," but the full sequence of the annealed duplex is not provided. The sequence shown in the text appears to have an asymmetry that may affect the binding mode.
- **Required correction** Provide the full sequences of all DNA constructs used, including the 30-bp duplex used for the PipX-NtcA-DNA complex. Clarify the rationale for using a half-site for the ternary complex.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section, "Structures of the PipX-NtcA-DNA complex"
- **Evidence pointer** Results section
- **Concern** The authors describe an "aberrant binding" of PipX in crystal II, where a PipX molecule from one complex contacts a neighboring complex. This is presented as potentially relevant to the in vivo situation, but it could also be a crystal packing artifact.
- **Required correction** Discuss the possibility that the aberrant binding is a crystallographic artifact and provide evidence that the observed interaction is specific and not simply a consequence of crystal packing.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section, "Functional evidence for PipX-RNAP interactions provided by bacterial two-hybrid assays"
- **Evidence pointer** Results section
- **Issue** The bacterial two-hybrid assays are described as supporting the predicted PipX-RNAP interactions, but the authors note that false negatives were obtained. The data are not shown, and the number of replicates and the statistical significance of the results are not reported.
- **Required correction** Provide the full two-hybrid data, including all constructs tested, all controls, and the number of independent experiments. Report the results quantitatively and discuss the false negatives in more detail.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the potential applications in biotechnology and medicine is brief and speculative, without concrete examples or references.
- **Required correction** Either expand on the potential applications with specific examples or remove this statement to avoid overreach.

## Risk / unsupported claims

1. The claim that PipX "increases NtcA-DNA contacts" is based on a comparison between structures with different DNA constructs and resolutions, and is not fully supported by the data presented.
2. The claim that the modelling of PipX onto the NtcA-TAC structure shows specific interactions with RNAP gamma and sigma subunits is based on an indirect approach and requires additional validation.
3. The statement that PipX has "no known functional counterparts in other taxonomic groups" is a strong claim that is not fully substantiated by a comprehensive literature search.
4. The functional significance of the "aberrant binding" of PipX observed in crystal II is speculative and could be a crystallographic artifact.
5. The claim that the V187E mutation abolishes DNA binding is based on EMSA data that are not shown and are described only qualitatively.

## Assessment against Nature-style criteria

- **Originality** The manuscript presents the first experimental structure of NtcA bound to DNA, which is a significant technical achievement. However, the conceptual framework, including the role of PipX as a coactivator and its potential interaction with RNAP, was largely proposed in previous work. The advance is therefore incremental rather than paradigm-shifting.
- **Scientific importance** The work provides important mechanistic insights into a key regulatory system in cyanobacteria, which are of significant environmental and biotechnological interest. The findings may have implications for understanding transcriptional regulation in other members of the CRP-FNR superfamily. However, the broader significance beyond the cyanobacterial field is not fully articulated.
- **Interdisciplinary readership** The manuscript is likely to appeal primarily to structural biologists and researchers in the cyanobacterial and bacterial gene regulation fields. The broader readership may find the detailed structural analysis less accessible. The authors should make a stronger case for the wider relevance of their findings.
- **Technical soundness** The crystallographic work appears to be carefully executed, but the moderate resolution of the key complexes and the lack of detailed validation data limit the strength of the conclusions. The functional assays are described but not shown, and the modelling approach requires more detail. Several technical concerns need to be addressed before the case is fully established.
- **Readability for nonspecialists** The manuscript is generally well written, but the abstract and introduction assume significant background knowledge. The authors should provide more context for readers outside the immediate field.

## Recommendation posture

Supportive if technical concerns are resolved. The manuscript addresses an important question and provides novel structural data that will be of interest to the field. However, the strength of the conclusions is currently limited by the moderate resolution of the key structures, the lack of detailed validation data, and the indirect nature of the PipX-RNAP interaction evidence. If the authors can address these concerns by providing additional data and analysis, the manuscript would be suitable for publication.