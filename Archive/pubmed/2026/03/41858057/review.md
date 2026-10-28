## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, experimental section) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and evidentiary support as presented in the provided text; structural and reporting quality
- **Shared manuscript claim summary** The authors report the in silico discovery of a small molecule (NFYi5) targeting a pocket on the NF-YB/NF-YC dimer, with evidence for reduced NF-Y transcriptional activity, reduced NF-Y target gene expression, inhibition of cardiac fibroblast proliferation, reduced NF-Y DNA binding in EMSA, and accelerated NF-YA protein degradation via a ubiquitin-independent mechanism
- **Visible evidence base** Text descriptions of docking screens, reporter assays, qPCR, EdU incorporation, EMSA, Western blotting, NMR, and MD simulations; figure and table references are present but the actual figures, tables, and supplementary materials were not provided
- **Missing materials affecting confidence** All figures, tables, supplementary figures, supplementary tables, and supplementary videos; raw numerical data; statistical outputs; compound characterization data (HPLC chromatograms, NMR spectra); MD simulation trajectories and analysis outputs; experimental replicates and controls

## Reviewer
- **Overall assessment** This manuscript describes a structure-based virtual screening campaign that identifies a novel small molecule inhibitor of the NF-Y transcription factor complex. The work addresses a genuine gap, as no selective small molecule NF-Y inhibitor with cellular activity has been previously described. The authors combine computational docking, molecular dynamics, and a panel of cellular and biochemical assays to characterize NFYi5. The core claims are plausible and the experimental design is generally appropriate, but the provided text lacks the quantitative data, figures, and statistical details necessary to fully evaluate the strength of the evidence. Several claims, particularly regarding selectivity and mechanism of action, are supported by limited evidence as described. The dual-mode mechanism (inhibition of DNA binding plus accelerated NF-YA degradation) is interesting but the causal relationship between compound binding and degradation is not established. The manuscript would benefit from clearer presentation of key data and additional controls to support the selectivity claims.

- **Who would be interested in the results, and why** Researchers in transcription factor pharmacology, cancer biology, fibrosis biology, and cardiovascular disease would find these results of interest. The demonstration that NF-Y is pharmacologically tractable with a drug-like small molecule opens new avenues for targeting this transcription factor in diseases where NF-Y drives pathological gene expression. The computational approach combining large-scale docking with MD refinement may also interest investigators working on structure-based drug discovery for protein-protein interaction interfaces. The potential therapeutic relevance for fibrotic diseases and cancers driven by aberrant NF-Y activity provides a translational rationale.

- **Major strengths**
  1. The study addresses an important unmet need: no selective small molecule NF-Y inhibitor with demonstrated cellular activity has been previously reported
  2. The virtual screening approach is rigorous, using a large library (8 million compounds) with explicit filtering criteria and manual curation
  3. The combination of computational predictions with multiple orthogonal experimental validations (reporter assays, qPCR, EMSA, Western blot, NMR) strengthens the conclusions
  4. The identification of a specific binding pocket on NF-YB/NF-YC that accommodates a conserved arginine residue provides a structurally rational basis for inhibitor design
  5. The authors acknowledge limitations, including the lack of cellular target engagement assays and the need for off-target profiling
  6. The dual mechanism of action (inhibition of DNA binding and accelerated NF-YA degradation) is novel and potentially significant

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that NFYi5 "reduced NF-Y activity" and "inhibited NF-Y-dependent transcriptional activity" based on reporter assays
- **Evidence pointer** Results section "NFYi5 Inhibits NF-Y Activity"; Figure references not visible
- **Concern** The text states that only one of seven compounds "significantly (>60%) inhibited NF-Y-sNLUC reporter activity" but does not provide the actual data, number of replicates, statistical test used, or the magnitude of inhibition for the other six compounds. The dose-response data are described but the IC50 values (19.95 μM and 12.73 μM) are presented without confidence intervals or the number of independent experiments. The selectivity data showing lack of effect on CMV, UBC, and NF-κB reporters are described qualitatively without numerical values or statistical analysis. Without the actual figures and quantitative data, the strength and reproducibility of these key claims cannot be assessed.
- **Why it matters** The central claim of the manuscript is that NFYi5 is a selective inhibitor of NF-Y transcriptional activity. If the reporter assay data are not robust or the selectivity is not clearly demonstrated, the entire premise of the study is weakened. The IC50 values are used later to correlate with proliferation effects, so their reliability is important.
- **Resolution test** Provide the actual reporter assay data with replicate numbers, statistical analysis, and dose-response curves. Show the full panel of seven compounds tested with quantitative inhibition values. Present the selectivity data with numerical values and statistical comparisons for all promoters tested.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic support
- **Claim pointer** The authors claim that NFYi5 "impaired NF-Y–DNA binding" based on EMSA experiments
- **Evidence pointer** Results section "NFYi5 Inhibits NF-Y DNA Binding"; Figure references not visible
- **Concern** The EMSA experiments are described as showing "modest (35%) inhibition" of the NF-Y-DNA complex, but the text does not specify whether this was observed with nuclear extracts, recombinant protein, or both. The concentration of NFYi5 used (40 μM) is described as higher than in cell-based assays, but the rationale for this concentration and whether lower concentrations were tested is not stated. The text does not indicate whether the inhibition was dose-dependent or whether the effect plateaued. A 35% inhibition in a binding assay is relatively modest and may not fully explain the more substantial effects observed on transcriptional activity and proliferation.
- **Why it matters** The EMSA data are presented as evidence for one of the two proposed mechanisms of action. If the inhibition of DNA binding is only partial, the authors' claim that this contributes to the observed cellular effects needs to be more carefully quantified and contextualized. The relationship between the EMSA results and the cellular potency needs to be clarified.
- **Resolution test** Provide the EMSA data with quantitative analysis, including dose-response experiments, and clarify whether the 35% inhibition was observed at a single concentration or across a range. Show data for both nuclear extracts and recombinant protein, and discuss how the partial inhibition relates to the cellular effects.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic support
- **Claim pointer** The authors claim that NFYi5 "accelerated NF-YA protein degradation" and that this occurs "independently of increased ubiquitination"
- **Evidence pointer** Results section "NFYi5 Induces Ubiquitin-Independent NF-YA Degradation"; Figure references not visible
- **Concern** The text describes cycloheximide chase experiments showing reduced NF-YA half-life from 16.5 ± 1.5 h to 8.5 ± 0.7 h, but the number of replicates, the statistical test, and the actual Western blot data are not shown. The claim of ubiquitin-independence is based on the absence of increased ubiquitinated NF-YA after MG132 treatment, but the text does not describe the quality of the ubiquitination assay or whether the basal ubiquitination signal was robust. The authors generated a NF-YA 6KtoR mutant but the text does not clearly state whether this mutant was tested for degradation in the presence of NFYi5, which would be the critical experiment to support the ubiquitin-independence claim. The statement that "both the wild type and the lysine-mutated proteins were destabilized" is presented without quantitative data.
- **Why it matters** The ubiquitin-independent degradation mechanism is a novel and potentially important finding. However, the evidence as described is incomplete. The key experiment (testing the 6KtoR mutant with NFYi5) is mentioned but the results are not clearly presented. Without this, the claim of ubiquitin-independence is not established.
- **Resolution test** Provide the cycloheximide chase data with replicates and statistical analysis. Show the ubiquitination assay results with appropriate controls. Clearly present the data for the 6KtoR mutant degradation in the presence and absence of NFYi5, with quantitative analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Target engagement
- **Claim pointer** The authors claim that NFYi5 "physically interacts with NF-YB/NF-YC" based on STD and water-LOGSY NMR experiments
- **Evidence pointer** Results section "NFYi5 Physically Interacts with NF-YB/NF-YC"; Figure references not visible
- **Concern** The NMR experiments are described qualitatively, with statements that NFYi5 "gives strong STD signals" and "negative signals" in water-LOGSY, but no quantitative data are provided. The text does not describe the protein concentration, the ligand-to-protein ratio, or whether control experiments with a non-binding compound were performed. The statement that "the ligand NFYi5 exhibits saturation transfer responses across the entire molecule" is presented without the actual STD spectrum or epitope mapping data. The concentration used (500 μM) is substantially higher than the cellular active concentrations, and the relevance of the binding observed at this concentration to the cellular effects is not discussed.
- **Why it matters** Direct evidence of physical binding to the target is important for validating the mechanism of action. However, the NMR data as described are qualitative and the high concentrations used raise questions about the affinity and specificity of the interaction. Without quantitative binding data or competition experiments, the significance of the observed NMR signals is unclear.
- **Resolution test** Provide the NMR spectra with quantitative analysis, including binding curves or affinity estimates if possible. Include control experiments with a non-binding compound. Discuss the relationship between the concentrations used in NMR and the concentrations effective in cellular assays.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Selectivity assessment
- **Claim pointer** The authors claim that NFYi5 shows "at least some degree of selectivity" for NF-Y based on lack of effect on housekeeping genes and other promoters
- **Evidence pointer** Results sections "NFYi5 Inhibits NF-Y Target Gene Expression" and "NFYi5 Inhibits NF-Y Activity"; Figure references not visible
- **Concern** The selectivity assessment is limited to a small number of promoters (CMV, UBC, NF-κB) and housekeeping genes (GAPDH, TBP, 36B4, UBC). The text notes a "modest stimulation" of the NF-κB reporter at the higher dose, which is not further investigated. No genome-wide transcriptional profiling or broader selectivity panel is described. The authors acknowledge that "a comprehensive off-target profiling remains to be conducted," but the current data are insufficient to support a strong selectivity claim. The potential for off-target effects on other transcription factors or cellular pathways is not addressed.
- **Why it matters** The therapeutic potential of NFYi5 depends on its selectivity. If the compound affects other transcription factors or pathways at the concentrations used, the observed effects may not be solely attributable to NF-Y inhibition. The limited selectivity data weaken the claim that NFYi5 is a specific NF-Y inhibitor.
- **Resolution test** Provide additional selectivity data, such as RNA-seq or a broader panel of transcription factor reporters. Investigate the NF-κB stimulation observed at higher doses. Discuss the potential off-target effects and how they might influence the interpretation of the results.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reporting quality
- **Affected element** Compound characterization
- **Evidence pointer** Experimental Section "Reagents"; Supplement Table 2
- **Issue** The text states that compounds were purchased at >95% purity and validated by HPLC and NMR, but the actual purity data are only in the supplementary materials. The text does not describe the physicochemical properties of NFYi5 (e.g., molecular weight, calculated logP, solubility) beyond a brief mention of favorable cLogP in the selection criteria.
- **Required correction** Include key physicochemical properties of NFYi5 in the main text and provide the purity data in a main-text table or clearly reference the supplementary table with specific values.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Cell culture and treatment conditions
- **Evidence pointer** Experimental Section "Cardiac Fibroblast Culture" and "Reporter Gene Assays"
- **Issue** The text does not specify the serum concentration or growth factor conditions used during compound treatment, the vehicle control used (presumably DMSO, but not stated), or the range of concentrations tested for the dose-response experiments. The duration of treatment for the reporter assays is stated as 18 h, but the rationale for this time point is not given.
- **Required correction** Specify the culture conditions during treatment, the vehicle control, the concentration range tested, and the rationale for the treatment duration.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Data presentation
- **Evidence pointer** Results sections throughout; Data and Statistical Analysis
- **Issue** The text states that data are presented as means ± SEM and that statistical tests were performed, but the specific statistical tests used for each experiment are not consistently described. The number of independent experiments (n) is mentioned as "reported number of independent experiments" but the actual n values are not given in the text.
- **Required correction** Clearly state the statistical test used for each experiment and provide the n values in the figure legends or in the text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Mechanistic interpretation
- **Affected element** Discussion of NF-YA degradation mechanism
- **Evidence pointer** Results section "NFYi5 Induces Ubiquitin-Independent NF-YA Degradation"; Discussion
- **Issue** The authors propose that NFYi5 induces conformational changes in NF-YA that lead to ubiquitin-independent degradation, but the specific pathway (e.g., proteasomal, lysosomal, calpain-mediated) is not investigated. The text mentions "ubiquitin-independent proteasomal degradation" as a possibility but does not test this with proteasome inhibitors.
- **Required correction** Discuss alternative degradation pathways and, if possible, include experiments with proteasome or lysosome inhibitors to clarify the degradation mechanism.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Docking validation
- **Affected element** In silico docking results
- **Evidence pointer** Results section "In Silico Docking"; Figure references not visible
- **Issue** The text describes the docking approach but does not provide docking scores or ranks for NFYi5 or the other six selected compounds. The criteria for selecting the final seven compounds are described qualitatively, but the specific docking scores and ranks are not given.
- **Required correction** Provide the docking scores and ranks for the selected compounds in a table or in the text to allow readers to assess the quality of the docking predictions.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Experimental consistency
- **Affected element** NFYi5 concentrations across assays
- **Evidence pointer** Results sections throughout
- **Issue** The concentrations of NFYi5 used vary across experiments: 1-20 μM in reporter assays, 15-20 μM in proliferation assays, 40 μM in EMSA, and 500 μM in NMR. The text does not explain why different concentrations were used or how the concentrations relate to the IC50 values.
- **Required correction** Provide a rationale for the concentrations used in each assay and discuss how they relate to the calculated IC50 values and the binding affinity.

## Risk / unsupported claims
- The claim that NFYi5 "reduced NF-Y activity" and "inhibited NF-Y-dependent transcriptional activity" is supported by reporter assay data, but the actual data are not visible in the provided text
- The claim that NFYi5 "impaired NF-Y–DNA binding" is supported by EMSA data showing 35% inhibition, but the quantitative data and experimental details are not fully provided
- The claim that NFYi5 "accelerated NF-YA protein degradation" is supported by cycloheximide chase data, but the data are not shown and the mechanism is not fully characterized
- The claim that NFYi5 induces "ubiquitin-independent" degradation is not fully supported, as the key experiment with the 6KtoR mutant is mentioned but the results are not clearly presented
- The claim that NFYi5 "physically interacts with NF-YB/NF-YC" is supported by NMR data, but the data are qualitative and the binding affinity is not quantified
- The claim of selectivity for NF-Y over other transcription factors is weakly supported, as only a limited number of promoters and housekeeping genes were tested
- The claim that NFYi5 has "antimitogenic properties" is supported by proliferation data, but the relationship between the anti-proliferative effects and NF-Y inhibition is not directly established
- The statement that "NF-Y is pharmacologically tractable" is a reasonable conclusion from the data, but the lack of cellular target engagement assays means this claim is not fully established
- The claim that the identified pocket on NF-YB/NF-YC is functionally important is based on the observation that NF-YA R266 is conserved, but the functional significance of this residue is not directly tested (the R266A mutant showed no reduction in reporter activity, which is mentioned but not discussed in detail)