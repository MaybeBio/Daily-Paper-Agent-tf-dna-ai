## ABSTRACT

Transcription in eukaryotes is regulated by chromatin-based mechanisms that control nucleosome occupancy, chromatin modifications, and transcription factor binding. We have previously shown that the transcription factor ADNP forms the ChAHP complex with the chromatin remodeler CHD4 and HP1 proteins, acting as a site-specific regulator of transcription and antagonist of CTCF binding. However, the molecular basis of these functions remained unclear. Here, we demonstrate that the CHD4 subunit is essential to antagonize CTCF and silence transcription of transposons, while HP1 proteins are dispensable. Although the remodeling activity of CHD4 is not required for ChAHP chromatin association, it is critical for both transposon repression and CTCF antagonism. Our findings support a model wherein ADNP recruits chromatin remodeling activity in a sequence-specific manner, enabling transcriptional control and local modulation of chromatin architecture.


## INTRODUCTION

Eukaryotic transcription is controlled through the coordinated action of multiple chromatin regulatory mechanisms, including chromatin modifications and chromatin remodeling 1 – 8 . One principle underlying this regulation is the inability of many transcription factors (TFs) to associate directly with nucleosome-bound DNA 9 – 12 . Thus, by positioning nucleosomes at key regulatory sequences, cells can regulate transcription in a time- and locus-specific manner. Biochemically, this is achieved by chromatin remodelers which utilize ATP hydrolysis to induce DNA repositioning, nucleosome eviction, or nucleosome incorporation. For example, the NuRD complex deploys chromatin remodeling activity of CHD4 alongside deacetylase activities of HDAC1/2 to facilitate transcriptional silencing 13 , 14 . In a related yet mechanistically distinct manner, the HIRA and ATRX-DAXX complexes place nucleosomes containing the histone variant H3.3 into chromatin to regulate replication-independent chromatin maintenance 15 – 17 . Chromatin remodelers themselves normally lack strong sequence specificity, and many are thought to be targeted to specific loci through interactions with TFs. For instance, SNF2H is thought to collaborate with CTCF, inducing an increase in chromatin accessibility 18 , 19 . Additionally, the remodeler likely liberates CTCF binding sequence motifs from the nucleosome, facilitating CTCF-chromatin binding and resulting in regular nucleosome positioning around these sites. Thus, the functional association of the TF and remodeler is required both for TF recruitment, and for downstream changes in chromatin properties. An equivalent relationship was described for the chromatin remodeler BRG1 and the TF REST 18 . However, in both these and most other cases, the chromatin remodelers are only transiently, weakly, or indirectly associated with the TFs 20 – 23 .

There are two prominent outliers of this labile recruitment principle: the INO80 and ChAHP complexes. INO80 incorporates the TF YY1, and this interaction is important for sequence-specific targeting of INO80 to gene promoters, resulting in transcriptional activaton 24 , 25 . Reciprocally, YY1 binding to chromatin is thought to be dependent on INO80 24 , 26 , mirroring the interdependencies seen with CTCF and REST. ChAHP is composed of the zinc finger TF ADNP, CHD4 and HP1β or HP1γ proteins, which assemble into a stable complex that can be reconstituted in vitro 27 . Disruption of ChAHP through deletion of the central ADNP subunit is embryonically lethal, and heterozygous truncations of ADNP result in a severe developmental disorder in humans 28 , 29 . The most prominent genomic targets of ChAHP are retrotransposons from the SINE family, bound in a sequence-specific fashion 27 , 30 , 31 . ChAHP additionally binds heterochromatin, including transposons from the LTR and LINE families, mediated by the association of the HP1 subunit with H3K9 trimethylated nucleosomes 31 . At the molecular level, loss of ADNP, and consequently the ChAHP complex, leads to upregulation of RNA pol III-transcribed SINE B2 elements in mouse embryonic stem cells (mESCs), accompanied by increased chromatin accessibility 27 , 30 . In addition, many murine SINE B2 elements carry a CTCF motif, and loss of ChAHP results in increased CTCF association with these elements alongside a rearrangement of topologically associated domains 30 . Despite its biological importance and clear link to chromatin biology, the mechanism of action of the ChAHP complex remains unknown.

Several mechanisms have been proposed for ChAHP-mediated genome regulation, including heterochromatin seeding via HP1 32 , competition for chromatin binding with CTCF and other TFs 30 , association with additional remodeler modules such as BRG1 33 , or targeted chromatin remodeling by CHD4 31 . However, none of these models have so far been supported by direct evidence. By generating endogenously edited ADNP mutant mESCs to decouple specific subunits from the complex, here we show that ChAHP-associated CHD4 is necessary for SINE B2 repression, while HP1s are not. We further demonstrate that both SINE B2 repression and CTCF antagonism are specifically effectuated by chromatin remodeling activity of CHD4 within ChAHP. We propose the stable association of ADNP with CHD4 guides ATP-dependent chromatin remodeling activity to locally regulate chromatin.


## RESULTS


## The extreme N-terminus of ADNP interacts with CHD4 to form the ChAHP complex

To test which ChAHP subunits are required to silence SINEs in mESCs, we sought to introduce mutations into the endogenous Adnp gene that specifically decouple either HP1 proteins or CHD4 from ADNP. While the interaction with HP1 can be disrupted by introducing point mutations into a conserved PxVxL motif in ADNP, a suitable small mutation abrogating CHD4 binding has not yet been demonstrated ( Figure 1A ) 27 , 31 , 34 , 35 . To identify such mutations, we used AlphaFold 36 to predict the structure of the ChAHP complex and infer interaction surfaces between ADNP and CHD4. This revealed that an N-terminal region of ADNP interfaces with a C-terminal region of CHD4, consistent with previously published low resolution interaction mapping ( Figure S1A ) 27 , 35 . To validate this prediction, we transiently transfected a series of ADNP truncation constructs into mESCs and probed their interaction with ChAHP subunits by co-IP ( Figure S1B ). All tested constructs where ADNP N-terminal residues were absent showed strongly reduced CHD4 binding, while HP1γ binding scaled with expression level of the constructs. Reciprocally, all constructs encoding N-terminal fragments of ADNP, including the smallest tested construct (amino acids 1-43), robustly interacted with CHD4. We conclude that the highly conserved first ∼40 amino acids of ADNP are both necessary and sufficient to bind CHD4. To facilitate genome editing and keep the perturbation as precise as possible, we sought to identify a narrower region necessary for binding. A detailed look into the structure prediction revealed that the first 8 amino acids of ADNP form extensive polar sidechain-backbone interactions with CHD4, and one close hydrophobic contact ( Figure 1B ). We tested the contribution of these residues to CHD4 binding by performing a co-IP with granular truncations of the N terminus ( Figure 1C ). This revealed that removal of 7 amino acids after the start codon of ADNP results in a comparable decrease in CHD4 binding as the more extensive truncations. Thus, the extreme N-terminus of ADNP is necessary for the ADNP-CHD4 interaction.

We introduced this truncation into mESCs encoding ADNP-Avi-3xFLAG and assessed its effects on ChAHP integrity ( Figure 4D , S1C-E). This endogenous intervention fully agreed with the results obtained by transient transfection ( Figure S1D ). Importantly, the minimal N terminal truncation (hereafter referred to as ADNPΔN) only affected incorporation of CHD4, but not HP1 into the ChAHP complex ( Figure 4D ). Similarly, auxiliary interactors of the ChAHP complex, such as ZMYM2/3, ATRX or TFIIIC subunits were not affected ( Figure S1E ). Vice versa, mutating the PxVxL motif to PGELT in the endogenous Adnp gene affected HP1 but not CHD4 incorporation. Consistent with a loss of association with heterochromatin, the heterochromatin-associated remodeler DAXX did not co-purify with ADNP-PGELT ( Figure S1E ). Thus, we were able to generate a panel of genome-edited mESC lines wherein either CHD4 or HP1 proteins were specifically excluded from the ChAHP complex.


## Removal of CHD4 from ChAHP results in SINE B2 activation

We used these cell lines to assess the contributions each subunit makes to the regulation of transcription by RNA-seq and compared them to the effects of complete loss of ADNP ( Figure 1E ). Consistent with previously published data, SINE B2 retrotransposons were significantly upregulated in ADNP KO cells 30 . Cells harboring the ΔN truncation of ADNP similarly showed a significant increase in SINE B2 RNA level, specifically the less divergent Mm1a and Mm1t subfamilies, while expression of other transposon families was not significantly affected. By contrast, decoupling HP1 from ChAHP induced no significant effects on transposon expression. At the gene expression level, CHD4 decoupling resulted in similar effects as knocking out the Adnp gene, and the magnitude of these changes strongly correlated ( Figure S1F-G ). Conversely, barely any differential gene expression was identified upon HP1 decoupling, and the correlation with effects brought on by Adnp KO or ΔN truncation was poor ( Figure S1F-G ). Together, these data indicate that within ChAHP, CHD4 is required to repress SINE B2s and maintain appropriate gene expression, while HP1 proteins are not.


## ADNP associates with chromatin without CHD4 but inefficiently antagonizes CTCF

Several transcription factors, such as CTCF and REST, rely on auxiliary factors to support their recruitment to chromatin 18 . To test whether ADNP uses CHD4 or HP1 to gain access to its cognate binding sites, we performed ChIP-seq with wild-type ADNP, and both subunit-decoupled mutants ( Figure 2A-C , Figure S2A-B ). ADNPΔN exhibited increased chromatin occupancy compared to WT, most strongly at ChAHP binding sites overlapping SINE B2 elements, and less so at other ChAHP-bound transposons ( Figure 2A-B ). Importantly, the capacity of ADNPΔN to bind regions that do not overlap transposons was unaffected. Consistent with previously described effects, decoupling HP1 proteins from ChAHP resulted in an overall increase of ADNP ChIP signal at loci overlapping euchromatin, including SINEs and regions that do not overlap with transposon sequences 31 . In contrast, this increase was not evident at heterochromatic retrotransposons, such as LINEs and LTRs. Since peak calling does not reliably capture broadly distributed heterochromatin-associated ADNP, we supplemented these analyses with a peak-agnostic quantification over transposable elements globally ( Figure S2B ). Herein, a reduction of heterochromatin occupancy is readily observed upon HP1 decoupling, consistent with previous observations 31 . We conducted the same analysis for ADNPΔN and observed increased occupancy at SINEs ( Figure S2B – B2_Mm1a, B2_Mm1t), but not at LTRs (IAPEz-int) or LINEs (L1MdA_I). These findings demonstrate that association with CHD4 is not required for ADNP to bind chromatin and confirm that the HP1 subunits are required to gain access to heterochromatin.

We have previously shown that CTCF occupancy at SINE B2 elements increases upon ablation of the ChAHP complex 30 , 37 . To test if this is dependent on CHD4 or HP1 subunits, we performed ChIP-seq for CTCF in the subunit-decoupled backgrounds and compared them to ADNP WT controls ( Figure 2D , Figure S2C-D ). Globally, CTCF occupancy was not strongly affected upon CHD4 or HP1 decoupling. However, we observed higher CTCF occupancy at SINE B2s and SINE B3s when CHD4 was decoupled. This effect was also apparent on SINE B3s, but not on SINE B2s, when HP1s were absent from the complex. Conversely, slightly less CTCF binding was evident at non-repeat regions for both mutants. Finally, CTCF occupancy at ADNP-unbound CTCF motifs was unaffected by either mutation.

To strengthen these analyses, we used the guidedNOMe-seq method to probe nucleosome positioning around CTCF motifs, which becomes more pronounced as CTCF occupancy increases ( Figure 2E ) 37 . CTCF and ADNP ChIP signal at the analyzed regions matched the effects seen genome-wide for all tested backgrounds, indicating that the chosen regions are representative ( Figure S2E ). Decoupling CHD4 from ChAHP results in prominent and symmetric protection from methylation around CTCF motifs overlapping ADNP-bound SINE B2s and B3s, with a size matching nucleosome footprints. This effect is similar to the ADNP KO condition, and specific to ADNP and CTCF co-bound regions, while CTCF sites devoid of ADNP were unaffected. Consistent with the CTCF ChIP analyses, decoupling HP1 from the complex resulted in an increase in positioning only at SINE B3s. Lastly, neither of the mutations induced any change at REST-bound regions. Together, these results show that ADNP-bound CHD4 is required for normal nucleosome distribution at ChAHP-bound loci, hinting that chromatin remodeling activity supports CTCF antagonism.


## ChAHP complex-specific inactivation of CHD4

Because CHD4 functions within multiple chromatin remodeling complexes, globally inactivating its ATPase activity obscures complex-specific roles 14 , 31 . To selectively abrogate ChAHP’s chromatin remodeling activity while preserving complex integrity, we generated cell lines wherein the coding sequence of CHD4 was N-terminally fused to the ADNP open reading frame at the endogenous locus. This was done in an ADNP-Avi-3xFLAG background, inserting either WT or catalytic dead CHD4 (E867Q; Walker B motif mutation), yielding a tagged in-frame chimeric transcript encoding both CHD4 and ADNP ( Figure 3A ). To suppress any potential association with endogenous CHD4 protein, we also fused both WT and catalytic dead CHD4 sequences to ADNPΔN. All CHD4-ADNP fusion proteins were expressed comparably to unfused ADNP-Avi-3xFLAG-, and similarly to each other ( Figure S3A , Input). By co-IP, we could confirm that none of the chimeras persistently interact with unfused endogenous CHD4, which can be resolved from the chimeras by molecular weight ( Figure S3A , IP). We further assessed whether the rest of the interactome changes between chimeric and unfused ADNP by proteomics ( Figure S3B-C ). This also allowed us to more accurately assess ADNP-CHD4 stoichiometry, which did not significantly differ between any of the chimeras and the unfused control ( Figure S3B ). Interactome-wide, there were no differentially interacting proteins between any of the chimeras and the unfused controls, apart from three variable background artefacts ( Figure S3C ). This excludes conceivable gain-of-function phenomena, such as formation of unnatural ChAHP-NuRD supercomplexes.


## Catalytically inactive ChAHP is trapped on SINE B2s

We first used this system to assess whether CHD4’s catalytic activity within the ChAHP complex is required for chromatin engagement. To that end, we performed ChIP sequencing, leveraging the affinity tag endogenously encoded at the C-terminus of the CHD4-ADNP chimeras ( Figure 3B-C ). In comparison to the unfused control, ChIP enrichments at ChAHP binding sites were overall slightly reduced for chimeras harboring WT CHD4 ( Figure 3B ). In contrast, chromatin occupancy increased for catalytically inactive chimeric assemblies, specifically at peaks overlapping SINE B2s ( Figure 3B-C ). This increase was not evident at peaks overlapping the more divergent and transcriptionally inert SINE B3 elements, nor at the evolutionarily distinct SINE B1 elements ( Figure 3B-C , Other SINE). These findings indicate that CHD4’s ATPase activity is dispensable for ChAHP chromatin engagement, but its absence may result in retention of the complex at specific genomic loci.


## Remodeling Activity of ChAHP counteracts CTCF binding to SINE B2s

Since the CHD4-ADNP fusion retains chromatin binding independent of CHD4’s catalytic activity, we had a tenable system to discriminate whether ChAHP competes with CTCF at SINE B2 elements through direct steric hindrance or dependent on remodeling activity. To that end, we performed CTCF ChIP-seq in cells expressing each CHD4-ADNP chimera variant ( Figure 4A , Figure S4A ). We observe no change in CTCF ChIP signal between CHD4 WT -ADNP WT and CHD4 WT -ADNP ΔN chimeras, indicating that the ADNP N-terminus does not influence CTCF antagonism per se . Conversely, cells expressing catalytically inactive ChAHP chimeras in either configuration exhibited increased CTCF occupancy at SINE B2 elements. This effect was locationally specific, as the increase was not evident beyond SINE B2s or outside ChAHP target regions. These data demonstrate that remodeling activity of ChAHP, not merely its presence, is necessary to efficiently antagonize CTCF binding at SINE B2s.


## ChAHP remodeling activity silences transcription of SINE B2s

Next, we assessed the impact of ChAHP remodeling activity on transcription of SINE B2 transposons, comparing each mutated CHD4-ADNP chimera to the CHD4 WT -ADNP WT control. Introduction of chimeras containing catalytically inactive CHD4 led to strong and significant derepression of SINE B2 elements compared to the CHD4 WT -ADNP WT control, while other SINE elements were unaffected ( Figure 4B , Figure S4C ). We additionally observed minor differences in LTR expression, but these were not consistent between ADNP WT- and ΔN-containing chimeras. Furthermore, major active murine LTR elements such as IAPEz and MMERVK10C, were not significantly affected ( Figure S4B , Figure S4C ).

These results demonstrate that transcription of SINE B2 elements by RNA polymerase III is counteracted through ChAHP remodeling activity, and not through action as a transcriptional barrier. In a related preprint, we show that ChAHP specifically prevents the transcription factor complex TFIIIB from associating with the SINE B2 promoter (Schnabl-Baumgartner et al . 2025. ChAHP Silences SINE Retrotransposons by Inhibiting TFIIIB Recruitment. bioRxiv , doi: https://doi.org/10.1101/2025.07.02.662776 ). To determine whether this exclusion is mediated by ChAHP’s catalytic activity, we performed ChIP-seq for the TFIIIB subunit BRF1 ( Figure 4C-D ). Indeed, we observed increased BRF1 binding at SINE B2 promoters in cells expressing catalytically dead ADNP-CHD4 chimeras ( Figure 4C-D ). Consistent with elevated transcription, the RNA polymerase III catalytic subunit POLR3A was also more enriched at the same loci. The increase in BRF1 association with SINE B2s was accompanied by a corresponding accumulation of POLR3A genome-wide, and the magnitudes of these increases strongly correlated ( Figure 4E ). Collectively, these data demonstrate that ChAHP represses SINE B2 transcription by preventing the recruitment of TFIIIB through a process dependent on remodeling activity.


## DISCUSSION

Since the discovery of the ChAHP complex, its mode of action has remained a subject of speculation, which included potential recruitment of auxiliary subunits and steric competition with transcription factors such as CTCF. In particular, the role of CHD4 within ChAHP had been elusive. Here, we provide direct evidence that the chromatin remodeling activity of CHD4 is indispensable for ChAHP function, but contrary to common expectation, ChAHP does not require CHD4’s ATPase activity to access its target sites. Instead, this activity is critical to counteract the chromatin binding of other transcription factors, namely CTCF and TFIIIB. This suggests that ChAHP engages with chromatin entirely independent of chromatin remodeling, or, alternatively, relies on a remodeling function that is not an integral part of the complex. Such a unidirectional dependence of a remodeler (CHD4) on a transcription factor (ADNP) is conceptually distinct from previously described TF-remodeler relationships, including labile (e.g., CTCF-SNF2H, REST-BRG1) and stable (e.g., YY1-INO80) assemblies.

Our finding that catalytically inactive ChAHP is trapped on specific chromatin loci argues against the parsimonious model in which the ChAHP complex sterically blocks transcription factor access. That is, catalytically inactive ChAHP does not support SINE B2 repression or CTCF antagonism, despite increased ChAHP occupancy specifically at these elements. This strongly suggests that direct binding competition between ChAHP and CTCF or TFIIIB makes little contribution to ChAHP function. We therefore surmise that the dominant mode of action is active nucleosome remodeling at its target sites. Altering the position or density of nucleosomes relative to key sequence motifs might occlude CTCF and TFIIIB binding sites, consistent with the general principle that nucleosomes bar TF access to DNA. This property has been demonstrated for CTCF, whose ingress to chromatin is supported by the remodeler SNF2H 18 . ChAHP may antagonize this process by disrupting nucleosome arrangements favorable for CTCF binding, thus driving a contraction in CTCF residency time on chromatin. Although it remains to be established whether TFIIIB is excluded from nucleosome-bound DNA in cells, in vitro work suggests RNA Pol III transcription is sensitive to nucleosome positioning 38 – 40 . We therefore speculate ChAHP interferes with TFIIIB function by increasing nucleosome density at TFIIIB recruitment sites.

In conclusion, we propose that ChAHP represents a functional module that enables sequence-specific targeting of chromatin remodeling activity to counteract the binding of other chromatin regulators.


## Limitations of the study

While we favor a model in which ChAHP remodels nucleosomes, an alternative explanation for transcription factor competition is that remodeling by the ChAHP complex directly ejects CTCF or TFIIIB from chromatin without repositioning a nucleosome at the TF binding site 41 . However, such a mechanism would be reliant on saturating concentrations of ChAHP and continuous occupancy at target sites to prevent CTCF/TFIIIB rebinding. Although the weak correlation between repressive potency and ChAHP occupancy at chromatin argues against this model, we cannot definitively exclude it. Since dissecting these chromatin events in more detail by cell-based steady state assays is not tenable, direct biochemical and structural evidence will be required to distinguish between these models.


## Author contributions

J.A. designed and performed most experiments, analyzed data, and generated the figures. F.M. generated cell lines, performed ChIP-seq and advised experiments. M.S. performed bioinformatics analyses. L.K. generated cell lines and performed guidedNOMe-seq. J.S. generated cell lines. D.H. analyzed proteomics data. E.P.F.M. prepared RNA-seq libraries and performed genomics QC. M.B. conceived and supervised the study, and secured funding. J.A., F.M. and M.B. wrote the manuscript. All authors discussed the results and commented on the manuscript.


## Declaration of interest

The Friedrich Miescher Institute for Biomedical Research (FMI) receives significant financial contributions from the Novartis Research Foundation. Published research reagents from the FMI are shared with the academic community under a Material Transfer Agreement (MTA) having terms and conditions corresponding to those of the UBMTA (Uniform Biological Material Transfer Agreement).


## Declaration of generative AI and AI-assisted technologies in the writing process

During the preparation of this work the authors used ChatGPT 4o to improve the readability and language of the manuscript. After using this tool, the authors reviewed and edited the content as needed and take full responsibility for the content of the published article.


## STAR METHODS


## RESOURCE AVAILABILITY

Further information and requests for resources and reagents should be directed to and will be fulfilled by the lead contact, Marc Bühler ( marc.buehler{at}fmi.ch ).


## Materials availability

Cell lines and plasmids are available upon request.


## Data and code availability

Sequencing data from ChIP-seq and mRNA-seq have been deposited at GEO (accession number GSE297864) and are publicly available as of the date of publication. The mass spectrometry proteomics data have been deposited to the ProteomeXchange Consortium via the PRIDE 42 partner repository with the dataset identifier PXD064364 and PXD064333. This paper analyzes existing, publicly available data. Their accession numbers are listed in the key resources table.

All original code has been deposited on GitHub and is publicly available at https://github.com/xxxmichixxx/ADNP_CHD4


## EXPERIMENTAL MODEL AND SUBJECT DETAILS

Mouse embryonic stem cells (129 × C57BL/6 background) with BirA and Cre insertions in the Rosa26 locus 43 , 44 were cultured on gelatin-coated dishes in ES medium containing DMEM (Sigma D5648), supplemented with 15% fetal bovine serum (FBS; GIBCO), 1 × non-essential amino acids (GIBCO), 1 mM sodium pyruvate (GIBCO), 2 mM l-glutamine (GIBCO), 0.1 mM 2-mercaptoethanol (Sigma), 50 mg/ml penicillin, 80 mg/ml streptomycin, 3 μM glycogen synthase kinase 3β (GSK) inhibitor (Sigma, CHIR99021), 10 μM MEK inhibitor (Tocris, PD0325901), and homemade LIF, at 37°C in 5% CO2.


## METHOD DETAILS


## Genome editing

Cells were trypsinized, counted, seeded, and immediately transfected using lipofectamine 3000 (Invitrogen) according to manufacturer instructions. Generally, 300k cells were seeded in 6-well plates and transfected with a total of 1-1.5mg DNA. For endogenous tagging, a plasmid harboring a desired homology repair cassette was included. The cells were then trypsinized, counted and 15000 cells were seeded on a 10cm dish for colony formation without puromycin selection. When colonies were sufficiently large (4-8 days), they were manually picked and split into two 96-well plates for screening and expansion. ADNP KO cells were made as previously described 27 , 30 , 31 . For CHD4-ADNP fusion cell lines, single cells were sorted by FACS into 96-well plates 3-5 days after transfection, selected by matching fluorescence intensity to a homozygously-tagged ADNP-NeonGreen-3xFLAG mESC cell line. 10μM ROCK inhibitor (Y-27632) was included in the media during the first 24h after sorting. Screening for both positive editing events and unedited loci was performed by PCR and Sanger sequencing of the products.


## Western blotting

Protein samples in lauryl-dodecyl sulfate sample buffer (LDS) were separated by standard SDS-PAGE on 4-12% Bis-Tris gradient gels (Novex Bolt, Invitrogen) or 3-8% Tris-acetate gradient gels (NuPage, Invitrogen). Separated proteins were transferred onto PVDF membranes (Milipore) in transfer buffer (Bjerrum-Schaeffer-Nielsen + 0.4% SDS) using a semi-dry transfer procedure (TransBlot Turbo, BioRad) with transfer parameters: 1.3A, 25V, 12min for one gel. The membranes were blocked in 3-5% skimmed milk (Sigma) dissolved in Tris buffered saline + 0.2% v/v Tween-20 (TBST). Antibody incubations were performed with antibodies diluted in blocking solution to empirically determined concentrations for a minimum of 45min up to a maximum of 24h. When re-probing, membranes were first treated with 0.01% NaN 3 for 30-60min to quench the HRP from previous staining rounds. Between each antibody incubation, the membranes were washed for a minimum of 45min in TBST with at least 4 buffer exchanges. The horseradish peroxidase system (Immobilon, Milipore), coupled to camera-based detection (AI600 or AI680, Agilent technologies) was used to visualize protein bands.


## Immune precipitations

Cells from one 10cm dish per condition were harvested by trypsinization before centrifugation (200g av , 5min). Cells were washed once in room temperature PBS and snap frozen or immediately taken forward for lysis. Pellets were lysed in NP-40 lysis buffer supplemented with protease inhibitors and benzonase (20mM Tris-HCl pH7.4, 150mM NaCl, 1% (v/v) NP-40, 0.1% (v/v) sodium deoxycholate,1xHALT protease inhibitor cocktail, 200U Turbo Benzonase (Milipore)) for 20min at 12°C and cleared by centrifugation at 4°C (16000g av , 20min). Protein concentration in the lysates was determined by Bradford assay against BSA and 1-3mg protein-lysate equivalent was loaded onto 10μL of bead slurry (Dynabeads, GE healthcare) prewashed twice with lysis buffer. For FLAG IPs, 2μg of antibody was added per 1mg of protein. For Strep IP Streptavidin M280 dynabeads (Invitrogen) were used. Beads were incubated with lysate for 2h at 4°C, washed twice with lysis buffer and twice with wash buffer (20mM Tris-HCl pH7.4, 150mM NaCl, 0.1%(v/v) NP-40) before addition of LDS. All bead separation steps were done using magnetic racks.


## Proteomics

For IP-MS, immune precipitations were performed as normal with the addition of 2 washing steps without detergent (20mM Tris pH7.5, 150mM NaCl), followed by on-bead digestion. Beads were resuspended in 5 µL of digestion buffer (3M GuaHCl, 20mM EPPS pH8.5, 10mM CAA, 5mM TCEP) and 1 µL of 0.2 mg/mL LysC protease (Promega) in 50 mM HEPES (pH 8.5) was added. Proteins were digested for 2 h rotating at room temperature. The samples were diluted with 17 µL of 50 mM HEPES (pH 8.5) and digested with 1 µL of 0.2 mg/mL trypsin (Promega) in 0.2 mM HCl at 37°C with interval mixing at 2000 RPM for 30 s every 15 min.

Digested peptides were acidified with 0.8% TFA (final) and analyzed by LC–MS/MS as follows:

For Figure S1E :

Instrument: Orbitrap LUMOS (Thermo Fisher Scientific) with VanquishNeo-nLC and an easy source with a 75umx15cm EasyC18 column was used. The samples were loaded on a C18 (0.3x5mm) trap and backward flush was used for the analysis.

Gradient 80min: 0-1min 2-6%B in A, 1-43min 6-20%, 43-65.5min 20-35%, 65.5-67.5min 35-45%, 67.5-68.5min 45-100%, 68.5-80min 100%. Buffer A: 0.1%FA in H2O; Buffer B: 0.1%FA, 80% MeCN in H2O, at RT and the flow rate during the gradient was 200ul/min.

For Figure S3B-C :

Instrument: Orbitrap LUMOS (Thermo Fisher Scientific) with VanquishNeo-nLC and an easy source with a 75umx15cm EasyC18 column was used. The samples were loaded on a C18 (0.3x5mm) trap and backward flush was used for the analysis.

Gradient 80min: 0-1min 2-6%B in A, 1-43min 6-20%, 43-65.5min 20-35%, 65.5-67.5min 35-45%, 67.5-68.5min 45-100%, 68.5-80min 100%. Buffer A: 0.1%FA in H2O; Buffer B: 0.1%FA, 80% MeCN in H2O, at RT and the flow rate during the gradient was 200ul/min.

Data were acquired using 120,000 resolution for the peptide measurements in the Orbitrap and a top T (3-sec) method with HCD fragmentation for each precursor and fragment measurement in the ion trap following the manufacturer guidelines (Thermo Scientific).


## ChIP-seq

ChIP experiments were performed with at least 2 different clones from endogenously tagged cell lines. For ADNP, CHD4-ADNP chimeras, and BRF1, the ChIPs were performed using antibodies against the affinity tag (3xFLAG), and for CTCF and POLR3A using specific antibodies as detailed further below. Harvesting was performed by trypsinization, and cells were counted for each sample. For each ChIP 10 7 cells were collected. The cells were crosslinked for 8 min at room temperature in 10ml PBS supplemented with 1% formaldehyde (Sigma, F8775). Cross-linking was quenched by adding glycine to a final concentration of 0.125 mM and incubating at room temperature for 1min, and on ice for 3min. Cells were pelleted by centrifugation at 500 g for 3 min at 4°C and the pellet was lysed in 10mL lysis buffer A (50 mM HEPES pH 8.0, 140 mM NaCl, 1 mM EDTA, 10% glycerol, 0.5% NP40, 0.25% Triton X-100) for 10 minutes on ice. After centrifugation the pellet was resuspended in 10 mL buffer B (10 mM Tris pH 8, 1 mM EDTA, 0.5 mM EGTA and 200 mM NaCl) and incubated for on ice for 5min. The samples were centrifuged at 500 g for 3 min at 4°C, and the pellets lysed in 180ul buffer C (50 mM Tris pH 8, 5 mM EDTA, 1% SDS, 100 mM NaCl) for 2min at room temperature and on ice for 10 min. The lysates were diluted in 1.6 mL ice cold TE buffer and sonicated in 15 mL tubes two times 10 cycles, 30 s ON / 30 s OFF, at 4°C (Bioruptor Pico, BioRad). Then, 200ul 10x ChIP buffer (0.1% SDS, 10% Triton X-100, 12mM EDTA, 167mM Tris-HCl pH 8, 1.67M NaCl) was added, and the chromatin was transferred into 2 mL Eppendorf tubes before centrifugation for 10 min at 16000 g, 4°C. 5% sheared chromatin was reserved for the input control, while the rest was transferred into fresh tubes. Generally, beads were prebound with antibody in PBS+0.2% Tween, and washed twice with 1x ChIP buffer, before being added to sonicated chromatin. For FLAG ChIPs, 20uL Protein G Dynabeads and 3uL α-FLAG. For CTCF and POLR3A, 15uL Protein G were mixed with 15uL Protein A Dynabeads and 3uL antibody added. Samples were incubated for 4h at 4°C. ChIPs were washed for 1 minute each for each step, 4 times RIPA (10mM Tris-HCl pH 8.0, 1mM EDTA pH 8.0, 140mM NaCl, 1% Triton X-100, 0.1% SDS, 0.1% Na-deoxycholate), 2 times RIPA500 (10mM Tris-HCl pH 8.0, 1mM EDTA pH 8.0, 500mM NaCl, 1% Triton X-100, 0.1% SDS, 0.1% Na-deoxycholate), 2 times Li-wash buffer (10mM Tris-HCl pH 8.0, 1mM EDTA, pH 8.0, 250mM LiCl, 0.5% NP-40, 0.5% Na-deoxycholate), 1x TE (10mM Tris-HCl pH 8.0, 1mM EDTA). Beads were transferred to a fresh tube during the last wash and wash buffer was completely removed before adding 50uL elution buffer (10mM Tris-HCl pH 8.0, 1mM EDTA pH 8.0, 150mM NaCl, 1% SDS) and incubating 20 minutes at 65°C with constant shaking. Elution was repeated once more with 50uL elution buffer for 20 minutes and eluates were pooled, 2 ul RNaseA (20μg/ul) were added and incubated for 1 h at 37°C. Then 2ul Proteinase K (20mg/ml) was added and samples were incubated 2 h at 55°C followed by decrosslinking for 6 h at 65°C. Input samples were adjusted to 100ul total volume with elution buffer and processed equivalently to ChIP samples. DNA was purified by adding 20ul AMPure XP beads, 6 ul 5M NaCl, and 130ul Isopropanol and incubating for 10 min at RT after thorough mixing. The beads were collected on a magnetic rack, washed twice with 80% EtOH and DNA was eluted in 30ul 10mM Tris pH8.0 for 5 min at 37°C. 25ul ChIP DNA or 10ng Input DNA were used to generate libraries using the NEBNext Ultra II Library Prep Kit for Illumina (NEB). Reactions were scaled down to half otherwise processing was according to the manufacturer’s manual. Libraries were sequenced 51bp paired-end on a NovaSeq6000 instrument (Illumina).


## RNA-seq

RNA was isolated from cells using the RNeasy miniprep kit (Qiagen) according to the manufacturer’s instructions, including genomic DNA pre-filtering and DNaseI treatment using 2U of RQ1 DNaseI (Promega) for 30min. The concentration was determined with the RNA Broad Range reagents on a Qubit 2.0 system according to the manufacturer’s instruction. Libraries were prepared using the Illumina Stranded Total RNA Library Prep, including a ribosomal RNA depletion step, and sequenced on the Illumina NovaSeq 6000 (51-nt paired-end reads).


## Computational methods Structure prediction

ChAHP structure prediction was performed on the AlphaFold Server (version from October 2024) 36 , by importing the full length mouse protein sequences of CHD4, ADNP, and two HP1γ units, alongside 1 ATP molecule, 1 Mg 2+ ion, and 13 Zn 2+ ions. The output folder was imported into AlphaBridge 45 for interpretation, and individual models further examined in ChimeraX 46 .


## ChIP seq alignment

Reads were mapped to the mouse mm39 genome using STAR version 2.7.3 47 and repeat sensitive settings as suggested by Teissandier et al 48 . The parameters used were STAR: --outSAMtype BAM SortedByCoordinate --winAnchorMultimapNmax 5000 --alignEndsType EndToEnd --alignIntronMax 1 --alignMatesGapMax 2000 -- seedSearchStartLmax 30 --alignTranscriptsPerReadNmax 100000 -- alignWindowsPerReadNmax 100000 --alignTranscriptsPerWindowNmax 300 -- seedPerReadNmax 1000 --seedPerWindowNmax 300 --seedNoneLociPerWindow 1000 --outBAMsortingBinsN 100 --clip3pAdapterSeq CTGTCTCTTATACACATCT AGATGTGTATAAGAGACAG --limitBAMsortRAM 10000000000 -- alignSJDBoverhangMin 999.


## Peak finding

Peak calling was performed using MACS3 version 3.0.1 49 on combined replicates for each ChIP condition. Read counts within peaks (resized to 300 bp around peak summits) were calculated for both ChIP and Input samples using featureCounts() from the Rsubread package 50 . Counts were normalized to library size (counts per million, CPM), and peaks were retained if they showed >1.2-fold ChIP/Input enrichment and CPM >1 in all replicates.


## ChIP-seq coverage plots

Representative ChIP-seq tracks were generated by merging replicate bam files, and converting them to the bigwig format. Tracks were visualized using the IGV genome browser software (version 2.8.6) 51 , and arranged for display in Adobe Illustrator (29.0.1).


## ChIP-seq heatmap generation

ChIP-seq heatmaps were generated using the MiniChip R package (version 0.0.0.9600). The SummitHeatmap() function was used with parameters: span = 900, step = 9, minOverlap = 1, useCPM = TRUE, PairedEnd = TRUE, minMQS = 0, strand = 0, readExtension3 = 0, readShiftSize = "halfInsert", read2pos = 5, mode = "Q". Heatmaps were drawn using DrawSummitHeatmaps() with parameters: use.log = FALSE, medianCpm = medianCpm, topCpm = topCpm, TargetHeight = 1000, orderSample = 1, orderWindows = 15, summarizing = "mean", show_axis = FALSE.


## ChIP-seq metaplots

To generate metaplots we used the CumulativePlots() function of the MiniChip R package(version 0.0.0.9600).


## RNA-seq read mapping and quantification

RNA-seq reads were aligned to the mouse genome (GRCm39) using STAR aligner with following parameters: --outFilterType BySJout --outFilterMultimapNmax 100000 -- outFilterMismatchNmax 3 --winAnchorMultimapNmax 20000 --alignMatesGapMax 350 - -seedSearchStartLmax 30 alignTranscriptsPerReadNmax 30000 -- alignWindowsPerReadNmax 30000 --alignTranscriptsPerWindowNmax 300 -- seedPerReadNmax 3000 --seedPerWindowNmax 300 --seedNoneLociPerWindow 1000--outSAMattributes NH HI NM MD AS nM --outMultimapperOrder Random -- outSAMmultNmax 1 --outSAMunmapped Within --limitBAMsortRAM 10000000000.

Uniquely mapped reads were quantified at the gene level using featureCounts with the GENCODE vM34 annotation.

For repetitive element analysis, a custom annotation file was created from RepeatMasker data (GRCm39.primary_assembly.repMasker_sensitive.bed). including multimapping reads. Read counts were generated using featureCounts with settings allowing for multiple mapping reads, multiple overlaps, and no read fraction assignment. Simple repeats, low complexity regions, and rRNA were excluded from the analysis to focus on biologically relevant elements. Only repeats with at least 100 normalized read counts summed across samples were included in downstream analyses.


## Differential expression analysis

Differential expression analysis was performed using DESeq2 52 for both genes and repetitive elements. For differential expression significance, a fold change threshold of 2-fold (|log₂FC| > 1) and FDR < 0.05 were used. Expression changes were evaluated at each condition compared to the respective controls as indicated in the figures.

For quantitative analysis of specific repeat families, normalized count data was extracted from the DESeq2 object to allow direct comparison between conditions. Count normalization was performed using DESeq2’s variance stabilizing transformation. Mean normalized counts with standard deviation were calculated for each experimental condition across biological replicates.


## MA-plots

RNA-seq data visualization was performed using R (version 4.1.0) with the tidyverse, and ggplot2 packages. Differential expression results were visualized using MA plots, with significantly regulated genes and repeat elements highlighted (|log₂FC| > 1 and FDR < 0.05). For repeat elements, specific families were color-coded by class.


## Proteomics

Peptides were identified with MaxQuant version 2.2.0.0 using the search engine Andromeda 53 or using FragPipe version 22.0 54 . The mouse subset of the UniProt version 2023_03 or 2023_08 combined with the contaminant DB from MaxQuant was searched and the protein and peptide FDR values were set to 0.05. Statistical analysis was done using limma within the einProt package (version 0.9.6) 55 . Results were filtered to remove reverse hits, contaminants and peptides found in only one sample. Missing values were imputed and potential interactors visualized in volcano plots.


## SUPPLEMENTAL INFORMATION

Document S1. Figures S1-S4

Table S1. mESC lines used in this study, related to STAR Methods

Table S2. Oligonucleotides used in this study, related to STAR Methods

Table S3. Plasmids used in this study, related to STAR Methods

Data S1. Annotated GenBank files for all plasmids used in this study, related to STAR Methods


## ACKNOWLEDGEMENTS

We thank the members of the Bühler lab for their constant support and discussions. Special thanks to Yukiko Shimada for technical support. We thank Hubertus Kohler for cell sorting and the members of the FMI genomics and proteomics platforms for their continuous support. We are grateful to Jakob Schnabl-Baumgartner, Nazerke Atinbayeva, Fabian Pötz, and Arjun Udupa for their comments on the manuscript. This work was supported by the Novartis Research Foundation and the Swiss National Science Foundation (SNSF; grant 310030_188835).


## Funder Information Declared


## Footnotes

↵ 5 Lead contact: marc.buehler{at}fmi.ch

https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE297864

https://www.proteomexchange.org/

https://github.com/xxxmichixxx/ADNP_CHD4