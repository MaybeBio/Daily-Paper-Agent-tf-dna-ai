## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, technical soundness, structural biology claims, biophysical data interpretation, and consistency with stated conclusions
- **Shared manuscript claim summary** The authors report the NMR-derived structure of a DNA duplex containing four consecutive AT repeats bound to JNII40, a bis(pyridine-2-carboxamidine) antileishmanial compound. They claim that direct amidinium–phosphate interactions, supported by water-mediated contacts, guide AT-selective minor-groove binding, and that this binding mode explains the compound's affinity and selectivity. They also report an improved multigram-scale synthesis and SPR data suggesting multiple binding events on extended AT tracts.
- **Visible evidence base** Main text figures 1–6, tables 1, supplementary figures 1–12 (referenced), supplementary tables 1–5 (referenced), PDB deposition 9SQC
- **Missing materials affecting confidence** Supplementary figures and tables were not provided in full; PDB coordinates and restraint lists were not independently examined; raw ITC thermograms and SPR sensorgrams beyond what is described were not available; details of the rMD protocol were only partially described

## Reviewer
- **Overall assessment** This manuscript presents a structurally detailed and potentially significant contribution to the understanding of minor-groove binding by arylimidamide compounds. The claim of direct amidinium–phosphate interactions is unusual and, if well supported, would expand the known interaction repertoire of minor-groove ligands. However, the evidence as presented has several gaps that need to be addressed before the structural conclusions can be fully accepted. The NMR data appear consistent with minor-groove binding, but the distinction between direct and water-mediated contacts, the justification for the imposed hydrogen-bond restraint, and the functional relevance of the observed binding mode require stronger support. The synthesis improvement is straightforward and useful. The SPR data on extended AT tracts are suggestive but not conclusive regarding multiple binding sites.
- **Who would be interested in the results, and why** Medicinal chemists working on antiparasitic drug discovery, particularly those targeting kinetoplastid infections; structural biologists studying DNA–ligand interactions; researchers interested in minor-groove binders and their sequence selectivity mechanisms. The structural insight into a new binding mode could inform rational design of improved antileishmanial agents.
- **Major strengths** The study addresses a clinically relevant problem with a clear translational motivation. The NMR structure determination appears carefully executed, with appropriate assignment strategies and a reasonable number of experimental restraints for a complex of this size. The observation of direct amidine–phosphate contacts is novel and potentially important. The improved synthesis with 44% overall yield and no chromatography is a practical advance. The combination of ITC, NMR, and SPR provides complementary views of the binding.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural evidence
- **Claim pointer** The authors claim that "direct amidinium–phosphate interactions" are a distinctive feature of the binding mode and that these contacts "guide AT-selective DNA binding."
- **Evidence pointer** Results and discussion, "Structure and binding mode of the (AT)4–JNII40 complex"; Figures 5 and 6; Supplementary Table 5
- **Concern** The central claim of direct amidinium–phosphate interactions rests on a small number of NOE restraints and a single imposed distance restraint of 2.0 Å between the amide proton and O2 of T7. The authors state that this restraint was "justified by the observation that this proton forms a hydrogen bond," but this reasoning is circular. The visibility of the amide proton in the NMR spectrum is consistent with hydrogen bonding, but it does not establish the acceptor atom. The distinction between direct and water-mediated contacts in the rMD trajectories is not clearly quantified. How many of the 16 unambiguous DNA–ligand NOEs directly support the amidine–phosphate contacts? What is the occupancy of these contacts across the ensemble? Without this information, the structural basis for the central claim is not fully established.
- **Why it matters** The novelty of this manuscript hinges on the direct amidine–phosphate interaction. If these contacts are instead water-mediated or transient, the binding mode would be less distinct from previously characterized minor-groove binders. The authors themselves note that such direct contacts have "very rarely" been described, so the evidence must be unambiguous.
- **Resolution test** Provide a per-restraint analysis showing which NOEs specifically support the amidine–phosphate contacts, report the occupancy and distance distributions for these contacts across the final ensemble, and clarify whether the 2.0 Å restraint was derived from an observed NOE or imposed based on the chemical shift argument. If the latter, the structure should be recalculated without this restraint to test whether the contact persists.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Biophysical data interpretation
- **Claim pointer** The authors state that ITC experiments with (AT)10 "did not provide interpretable binding isotherms" and attribute this to the presence of multiple species in equilibrium, supported by native PAGE showing "at least two species."
- **Evidence pointer** Results and discussion, "Sequence selectivity and binding to extended AT-rich DNA"; Supplementary Figures 1 and 9
- **Concern** The native PAGE evidence for multiple species is mentioned but not shown in the main text, and the interpretation is ambiguous. The sequence 5'-CATATATATATATATATATATG-3' is self-complementary and could form a hairpin, a duplex, or higher-order structures. The authors then switch to SPR with hairpin constructs to circumvent this issue. However, the SPR data for h(AT)10 show two apparent Kd values, and the authors interpret the second, weaker binding event as a second ligand binding within the stem. This interpretation is speculative. The weaker event could also represent nonspecific binding to the loop, a conformational change in the hairpin, or a binding-induced structural rearrangement. The authors do not provide a control experiment with a hairpin lacking the AT stem or with a scrambled stem sequence.
- **Why it matters** The claim that multiple JNII40 molecules could bind to extended AT-rich tracts in mitochondrial DNA is presented as a relevant biological implication. If the second binding event is not within the stem, this conclusion is not supported.
- **Resolution test** Provide the native PAGE data in the main text or supplementary with appropriate molecular weight markers. Include a control SPR experiment with a hairpin of the same length but with a GC-rich stem, or with a hairpin where the stem is scrambled to remove AT tracts. If the second binding event is specific to the AT stem, this control should show only one binding event.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Selectivity mechanism
- **Claim pointer** The authors state that "direct hydrogen bonds, such as the interaction between the ligand amide proton and the O atom of T7, as well as water-mediated contacts involving thymine oxygen atoms, explain favoured binding to thymine-containing sequences."
- **Evidence pointer** Results and discussion, "Sequence selectivity and binding to extended AT-rich DNA"; Figures 5 and 6
- **Concern** The structural explanation for AT selectivity is largely inferred from a single structure with one sequence. The authors argue that the adenine H2 proton faces the minor groove and that a guanine exocyclic amino group would sterically hinder binding, but this is a general argument that applies to most minor-groove binders and does not specifically validate the role of the amidine–phosphate contacts in selectivity. The authors do not present binding data for a GC-containing sequence beyond the h(GC)4 control, which shows no detectable binding. This is consistent with AT selectivity but does not distinguish between the proposed mechanism and other possible explanations, such as differences in groove width or electrostatic potential.
- **Why it matters** The manuscript claims to provide a structural basis for AT selectivity. If the selectivity mechanism is not uniquely determined by the structure, the claim is overstated.
- **Resolution test** Perform binding assays with a series of sequences containing single AT-to-GC substitutions within the binding site and correlate the affinity changes with the structural model. Alternatively, use molecular dynamics to compare binding to an AT-containing and a GC-containing sequence and show that the amidine–phosphate contacts are disrupted in the GC context.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance
- **Claim pointer** The authors state that the binding mode "provides key insights for developing selective DNA-targeting agents with improved stability and therapeutic promise against kinetoplastid parasites."
- **Evidence pointer** Introduction; Results and discussion, "Sequence selectivity and binding to extended AT-rich DNA"
- **Concern** The manuscript does not establish a direct link between the structural findings and the antiparasitic activity of JNII40. The compound's potency and selectivity against Leishmania are mentioned in the abstract and introduction, but no data are presented connecting the DNA binding mode to the biological activity. The authors note that JNII40 can inhibit AT-hook 1 binding, but this is presented as a consistency argument rather than a functional demonstration.
- **Why it matters** The translational relevance of the structural work depends on the assumption that DNA binding is the mechanism of action. If the compound has other targets or if the DNA binding is not the primary determinant of antiparasitic activity, the structural insights may have limited therapeutic relevance.
- **Resolution test** Provide data linking DNA binding affinity or selectivity to antiparasitic activity, for example by testing a series of analogues with varying DNA binding properties and correlating their activities. Alternatively, demonstrate that the compound's antiparasitic effect is correlated with its ability to displace AT-hook proteins in a cellular context.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "potent antileishmanial drug" in the title and abstract implies clinical use, but the compound is described as a "promising" candidate in the introduction. The distinction between a drug and a drug candidate should be maintained.
- **Required correction** Change "drug" to "drug candidate" or "lead compound" in the title and abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 6
- **Evidence pointer** Figure 6c
- **Issue** The ensemble of ten NMR structures is shown, but the figure does not indicate which regions are well-defined and which are disordered. The global RMSD of 0.6 Å is reported, but per-residue RMSD values would be more informative.
- **Required correction** Add a per-residue RMSD plot as a supplementary figure, or color the ensemble representation by per-residue RMSD.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods, "Structural calculation"
- **Evidence pointer** Methods, "Structural calculation"
- **Issue** The description of the rMD protocol is brief. The force constants for the experimental restraints are given, but the equilibration and production phases are not described in sufficient detail for reproduction. The number of rMD trajectories and the criteria for selecting the ten final structures are not fully specified.
- **Required correction** Expand the methods section to include the number of independent trajectories, the length of each trajectory, the temperature coupling scheme, and the criteria for selecting representative structures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results and discussion, "Thermodynamics of JNII40–DNA binding"
- **Evidence pointer** Table 1
- **Issue** The thermodynamic parameters are reported with units of kcal·mol⁻¹, but the entropic term TΔS is reported as a combined value. It would be clearer to report ΔH, ΔS, and TΔS separately.
- **Required correction** Report ΔS separately in Table 1 or in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and discussion, "NMR analysis of JNII40–DNA interaction"
- **Evidence pointer** Supplementary Figure 2
- **Issue** The titration of JNII40 with (CG)4 is described as producing no significant changes in the imino region, but the aromatic region shows changes attributed to the ligand. The authors do not comment on whether this indicates any binding to the GC-containing duplex, even if weak or nonspecific.
- **Required correction** Add a brief comment on whether the aromatic region changes in the (CG)4 titration indicate any interaction, and if so, how this is reconciled with the ITC and SPR data showing no detectable binding.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Results and discussion, "Structure and binding mode of the (AT)4–JNII40 complex"
- **Evidence pointer** Figure 6e, f
- **Issue** The hydrogen-bond network is described in the text, but the specific distances and angles for the proposed hydrogen bonds are not reported. The figure shows the interactions, but quantitative values would strengthen the description.
- **Required correction** Report the donor–acceptor distances and angles for the key hydrogen bonds in the text or as a supplementary table.

- **Technical failings that need to be addressed before the case is established** The imposed 2.0 Å hydrogen-bond restraint between the amide proton and O2 of T7 must be justified with direct experimental evidence or removed and the structure recalculated. The occupancy of the amidine–phosphate contacts across the ensemble must be quantified. The SPR data for h(AT)10 require a control experiment to rule out nonspecific binding. The native PAGE data supporting the multiple-species interpretation of (AT)10 should be shown.
- **Assessment against Nature-style criteria** Originality: The claim of direct amidinium–phosphate interactions in minor-groove binding is novel and, if confirmed, would represent a new interaction mode. Scientific importance: The work has clear translational relevance for antiparasitic drug design, and the structural insights could inform the development of improved compounds. Interdisciplinary readership: The work bridges medicinal chemistry, structural biology, and parasitology, and would appeal to researchers in all three fields. Technical soundness: The NMR methodology appears generally sound, but the key structural claim requires additional validation as described above. Readability for nonspecialists: The manuscript is generally well written and accessible, though some sections assume familiarity with NMR methodology.
- **Recommendation posture** Supportive if technical concerns are resolved. The structural claim of direct amidinium–phosphate interactions is potentially significant but requires stronger experimental support. The synthesis improvement and biophysical characterization are solid contributions. The manuscript would be suitable for publication after the major concerns are addressed.

## Risk / unsupported claims
- The claim that direct amidinium–phosphate interactions "guide AT-selective DNA binding" is not fully supported by the presented evidence, as the selectivity argument relies on a single structure and general steric considerations.
- The interpretation of the second binding event in h(AT)10 SPR data as a second ligand binding within the stem is speculative without appropriate controls.
- The statement that the binding mode "provides key insights for developing selective DNA-targeting agents with improved stability and therapeutic promise" is an extrapolation not directly supported by functional data.
- The claim that the amide proton at 9.5 ppm participates in a hydrogen bond that "slows solvent exchange" is inferred from its visibility in the NMR spectrum, but no exchange rate measurements are presented.
- The assertion that the two ordered water molecules "critically contribute" to complex stabilization is based on their presence in the rMD trajectories, but no free energy calculations or mutation studies are provided to quantify their contribution.