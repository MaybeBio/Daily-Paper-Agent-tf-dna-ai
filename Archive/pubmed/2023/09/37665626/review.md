## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use molecular modelling and molecular dynamics simulations to propose that mono-phosphorylation at Ser4 of Banf1 reduces its DNA binding capability by inducing N-terminal secondary structure changes that alter the DNA binding surface, and that phosphorylated Banf1 variants bind DNA with lower affinity and unstable docked poses
- **Visible evidence base** Abstract text only; no quantitative data, simulation parameters, or structural analyses are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation methodology, force field parameters, system setup, convergence criteria, and any experimental validation

## Reviewer

- **Overall assessment** The abstract presents a plausible computational study addressing a biologically important question, namely the molecular mechanism by which Ser4 phosphorylation abolishes Banf1 DNA binding. The claim that mono-phosphorylation induces local conformational changes that alter the DNA binding surface is mechanistically reasonable and consistent with prior experimental observations. However, the abstract provides no quantitative evidence, no methodological detail, and no validation of the simulation approach. The central mechanistic claim is therefore not assessable from the supplied material. The work may be of interest to the biophysics and cell biology communities, but the case is currently not established from the abstract alone.

- **Who would be interested in the results, and why** Researchers studying DNA binding proteins, phosphorylation-dependent regulation of protein nucleic acid interactions, and computational biophysics of protein DNA complexes. The potential link to cell proliferation and cancer therapeutics may also attract investigators in cancer biology, though the translational relevance is speculative at this stage.

- **Major strengths** The biological question is well motivated and addresses a long standing observation that mono-phosphorylated Banf1 cannot bind DNA. The abstract indicates a systematic approach covering unphosphorylated, mono-phosphorylated, and di-phosphorylated states, which is appropriate for the question. The reported residue-level interaction analysis, including hydrogen bonds and water bridges, suggests a detailed computational effort.

- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** The abstract claims that mono-phosphorylation of Banf1 causes N-terminal secondary structure changes that induce significant changes in the DNA binding surface, thereby eliminating DNA binding capability  
  - **Evidence pointer** Abstract text; location not provided  
  - **Concern** The central mechanistic claim is presented without any supporting quantitative data. No free energy values, structural metrics, or comparison of binding affinities are provided. The abstract states that residue-level binding energies were computed, but no numbers are given. The claim that the docked binding poses are not stable in MD simulations is asserted without any measure of instability, such as RMSD or dissociation timescales.  
  - **Why it matters** Without quantitative evidence, the reader cannot evaluate the magnitude of the proposed effects or the reliability of the simulations. The claim that phosphorylation eliminates DNA binding is a strong statement that requires quantitative support, particularly because the abstract also states that phosphorylated Banf1 binds with significantly lower affinity, which implies residual binding rather than complete elimination.  
  - **Resolution test** Provide quantitative data from the simulations, including binding free energies for all three states, structural descriptors of the N-terminal region in each state, and stability metrics for the docked complexes. Show that the differences between unphosphorylated and phosphorylated states exceed the statistical uncertainty of the simulations.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Methodological transparency  
  - **Claim pointer** The abstract claims that comprehensive and systematic molecular modelling and molecular dynamics simulations were used  
  - **Evidence pointer** Abstract text; location not provided  
  - **Concern** No methodological details are provided. The force field, water model, simulation length, temperature, pressure coupling, system size, and equilibration protocol are all absent. The docking method and scoring function are not described. Without this information, the reliability of the results cannot be assessed.  
  - **Why it matters** Molecular dynamics results are highly sensitive to simulation parameters and force field choice. The absence of methodological detail prevents any assessment of whether the simulations were adequately converged and whether the conclusions are robust to parameter choices.  
  - **Resolution test** Provide a full methods section in the manuscript, including all simulation parameters, convergence criteria, and validation of the simulation setup against experimental data where available.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Experimental validation  
  - **Claim pointer** The abstract claims that mono-phosphorylation eliminates DNA binding capability and that the findings help predict effects of mutations and open avenues for therapeutic development  
  - **Evidence pointer** Abstract text; location not provided  
  - **Concern** The study is purely computational. No experimental validation is mentioned, such as mutagenesis, binding assays, or structural comparisons with known Banf1 structures. The abstract also makes a translational claim about cancer drug development that is not supported by any data.  
  - **Why it matters** Computational predictions of phosphorylation effects on protein DNA interactions are valuable but require experimental confirmation, particularly when the claim is that binding is eliminated. The therapeutic claim is speculative and not supported by the presented work.  
  - **Resolution test** Include experimental validation, such as electrophoretic mobility shift assays with phosphorylated and unphosphorylated Banf1, or cite existing experimental data that directly supports the simulation results. Moderate the therapeutic claims or provide a clear rationale for how the computational findings directly inform drug development.

- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Abstract wording  
  - **Evidence pointer** Abstract text  
  - **Issue** The abstract states that mono-phosphorylated Banf1 cannot bind DNA, but later states that phosphorylated Banf1 binds with significantly lower affinity. These statements are not fully consistent, as lower affinity implies some binding.  
  - **Required correction** Clarify whether the claim is complete elimination of binding or a substantial reduction in affinity, and ensure the abstract wording is consistent throughout.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Specificity  
  - **Affected element** Abstract claims  
  - **Evidence pointer** Abstract text  
  - **Issue** The abstract mentions that some residue-level binding energies, hydrogen bonds, and water bridges have not been reported previously, but does not specify which ones are novel.  
  - **Required correction** Identify the specific novel interactions in the abstract or indicate that they will be highlighted in the full manuscript.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Abstract claims  
  - **Evidence pointer** Abstract text  
  - **Issue** The abstract does not state the simulation length or the number of replicates, which are important for assessing the statistical robustness of the conclusions.  
  - **Required correction** Include simulation times and replicate numbers in the abstract or indicate that they are provided in the methods section.

## Risk / unsupported claims

- The claim that mono-phosphorylation eliminates Banf1 DNA binding capability is not quantitatively supported in the abstract and is partially contradicted by the statement that phosphorylated Banf1 binds with significantly lower affinity.
- The claim that N-terminal secondary structure changes induce significant changes in the DNA binding surface is not supported by any structural data in the abstract.
- The claim that the findings open a novel avenue for cancer drug development is speculative and not supported by the presented computational work.
- The claim that some residue-level interactions have not been reported previously is not verifiable from the abstract.
- The overall reliability of the simulation results is not assessable due to the complete absence of methodological detail.