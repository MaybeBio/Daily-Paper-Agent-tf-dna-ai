# Structural Heterogeneity of TDP‐43 Fragments in Alzheimer's Disease and Primary Age‐Related Tauopathy by Artificial Intelligence (AI)–Based 3D Segmentation


## ABSTRACT
  TAR DNA‐binding protein 43 (TDP‐43) inclusions are defining pathological features of frontotemporal lobar degeneration (FTLD) but are also often observed in Alzheimer's disease (ad) and primary age‐related tauopathy (PART). TDP‐43 in ad is either associated with cognitive impairment or a protective‐life prolonging impact, and yet the localization, cellular and fragment characteristics of TDP‐43 need to be determined. We investigated the relationships between TDP‐43 volumetric inclusion burden in low likelihood ad (lAD) and definite PART by immunostaining against phosphorylated TDP‐43 (pTDP‐43), TDP‐43 C terminal (TDP‐C) and TDP‐43 N‐terminal (TDP‐N) fragments combined with 3D confocal imaging taken from eight regions: amygdala (basolateral [amygdala‐BL] and centromedial amygdala [amygdala‐CM]), the hippocampus (Cornu Ammonis [CA]‐1, CA2/3, CA4, dentate gyrus [DG] and subiculum [SUB]) and entorhinal cortex (ERC) and artificial intelligence (AI)–based segmentation via object recognition, reconstruction and quantification. We found amygdala‐CM in lAD and PART to have the overall greatest burden of pTDP‐43 whereas TDP‐N burden in amygdala‐BL of PART cases was greater than other TDP‐43 fragments. There was no difference in TDP‐43 burden in hippocampal subfields in PART. However, CA2/3 region showed greater pTDP‐43 burden while TDP‐N stood out in DG and SUB. Multiple comparisons among the groups revealed that TDP‐C was the only fragment showing differences among PART and lAD in CA2/3, DG and SUB regions. Overall, unbiased AI‐based volumetric burden analysis pipeline demonstrated unique fragment aggregation patterns in the neurodegenerative processes of PART and ad.


## Introduction
  TAR DNA–binding protein 43 (TDP‐43) is a key pathological protein in frontotemporal lobar degeneration (FTLD) and is also frequently detected in Alzheimer's disease (ad) and primary age‐related tauopathy (PART) [1]. Across these disorders, TDP‐43 forms characteristic neuronal cytoplasmic and intranuclear inclusions, perivascular aggregates and dystrophic neurites, each defined by distinct molecular signatures involving phosphorylated TDP‐43, C‐terminal fragments and N‐terminal fragments [2, 3, 4]. TDP‐43 contains an N‐terminal domain, two RNA‐recognition motifs and a C‐terminal prion‐like domain. It undergoes pathogenic phosphorylation at serines 409/410 and proteolytic cleavage, generating aggregation‐prone C‐terminal fragments [3]. The protein also adopts multiple conformational states, including a native dimeric form, and RNA binding can modulate its solubility by promoting N‐terminal dimerization and by spatially separating TDP‐43 molecules [5].

  Despite these known biochemical features, the molecular composition and regional distribution of TDP‐43 inclusions in PART (PART‐TDP) and low‐likelihood ad (lAD‐TDP) remain poorly characterized, and their relationship to inclusion types described in FTLD‐TDP remains unclear. This study examines the molecular features, anatomical distribution and burden of TDP‐43 inclusions in lAD‐TDP and PART‐TDP. Distinguishing these entities is clinically important because they reflect different underlying disease mechanisms and have distinct implications for memory impairment and disease progression [6]. We hypothesize that individual TDP‐43 fragments exhibit distinct regional and molecular patterns capable of differentiating lAD‐TDP from PART‐TDP in early neurodegeneration.


## Methods
  Between December 2020 and October 2023, we prospectively recruited three definite PART‐TDP and three lAD‐TDP participants from NIH‐funded Neurodegenerative Research Group studies at Mayo Clinic (Rochester, MN). Autopsy‐confirmed individuals without neurodegenerative disease served as controls. All participants underwent standardized behavioural evaluation and neuropathological assessment, and informed consent was obtained under Mayo Clinic IRB approval which included the ethical standards of the Committee on Human Experimentation at Mayo Clinic by the Helsinki Declaration of 1975. All patients or proxies consented to the research study (their proxies provided consent for patients when needed).

  Eight regions of interest—amygdala‐BL and amygdala‐CM, CA1, CA2/3, CA4, DG, SUB and ERC—were sampled from two FFPE limbic tissue blocks per case. Sections (10 μm) were permeabilized, subjected to 10‐mM sodium citrate (pH: 6.0) at 80°C for 30 min, blocked (2% normal donkey serum and 0.1% bovine serum albumin (BSA) in 1× PBS) for 1 h, and then incubated with primary antibodies of different TDP‐43 types: (1) anti‐phospho TDP‐43 (pS409/410) (Proteintech, rabbit polyclonal, catalogue #22309‐1‐AP, 1:200), (2) anti‐TDP‐43 C‐terminal fragment (Proteintech, rabbit polyclonal, catalogue #12892‐1‐AP, 1:200), (3) anti‐TDP‐43 N‐terminal fragment (Proteintech, rabbit polyclonal, catalogue # 80002‐1‐RR, 1:200) overnight at 4°C. Alexa Fluor 568 Donkey Anti‐Rabbit IgG (Jackson ImmunoResearch, #711‐575‐152, 1:200) secondary antibody was applied for 2 h, followed by TrueBlack lipofuscin autofluorescence quencher (Biotium, catalogue #23007) for 3 min at room temperature, and PBS washes for five mins three times. Stained sections were mounted on glass slides in antifade mounting medium (Vector Laboratories, VECTASHIELD Vibrance Antifade Mounting Medium (H‐1700)). Omission of primary or secondary antibodies produced no detectable signal.

  Z‐stacks (10 optical sections, 1 μm apart from each other, 20× magnification [stack size = 606.09 μm × 606.09 μm × 10 μm]) confocal imaging was performed on a Zeiss 980 LSM spinning‐disk microscope under uniform acquisition settings. TDP‐43–positive inclusions were segmented from 3D z‐stacks after reconstruction. Quantitative volume analysis of reconstructed 3D TDP‐43 particles was performed using supervised AI‐based object recognition in AIVIA 15.0, with classifier training performed on representative images from multiple regions and cases. Alexa Fluor 568 labelled pTDP‐43, TDP‐C and TDP‐N were separately trained in the software to detect all positive particles with supervision. All AI pixel classifier training was conducted with four to five images from various regions of two to three cases per pathological group in a supervised fashion. Custom workflows generated 3D reconstructions and morphometric measurements as μm3 for all raw z‐stacks in a blinded manner.

  Statistical analyses were conducted using nonparametric tests on GraphPad 11. Data are presented as median ± interquartile range. Group comparisons used Kruskal–Wallis tests (multiple groups) or Mann–Whitney U tests (two groups). All imaging and analyses were performed by investigators blinded to the pathological group.


## Results
  Across the six cases, the median age at presentation was 92.5 years (mean 89.3 years), with comparable ages at death in PART (97 ± 1.5) and lAD (86 ± 10). Two participants (33.3%) were female. TDP‐43 pathological stage was similar across groups, indicating low variability in the overall distribution of inclusions (Table S1).

  Immunostaining for TDP‐43 fragments in lAD revealed distinct inclusion morphologies across the amygdala and hippocampal subfields (Figure 1A). Still, the absence of an unbiased shape‐based classifier prompted a shift toward volumetric burden analysis. In lAD, pTDP‐43 burden was greatest in the amygdala‐CM compared with TDP‐C and TDP‐N, whereas the amygdala‐BL and ERC showed no significant differences (Figure 1A–D). PART demonstrated a similar pattern in the amygdala‐CM, with pTDP‐43 exceeding other fragments (Figure 2A,C), while the amygdala‐BL and ERC showed higher TDP‐N burden (Figure 2A,C,D).

  Hippocampal subfields in PART showed no significant differences among TDP‐43 fragments (Figure S1A–E). In lAD, pTDP‐43 burden was highest in CA2/3 (Figure S1G), whereas TDP‐N predominated in the dentate gyrus and subiculum (Figure S1I,J).

  Direct comparison of PART and lAD revealed that TDP‐C burden was significantly greater in PART within CA2/3, DG and SUB (Figure 3D,F,G). Analysis of regional distribution across all ROIs (Figure S2) showed that the amygdala‐CM harboured the highest pTDP‐43 and TDP‐C burden in PART (Figure S2A,B,D). In lAD, the amygdala‐BL showed the greatest TDP‐C burden (Figure S2E), while both amygdala‐BL and SUB exhibited the highest TDP‐N burden in each pathology (Figure S2C,F).


## Discussion
  Our previous studies in neurodegeneration demonstrated the importance of TDP‐43 inclusions [1, 6, 7, 8, 9, 10]. TDP‐43 fragment profiles show heterogeneity across limbic regions in PART‐TDP and lAD‐TDP, revealing molecular patterns that may help distinguish these two age‐associated TDP‐43 proteinopathies by 3D AI object segmentation and volumetric burden analyses. Although overall TDP‐43 pathological stage was similar between groups, fragment‐specific analyses uncovered regionally selective vulnerabilities. Both PART and lAD showed a shared signature in the amygdala‐CM, where pTDP‐43 burden predominated, consistent with early limbic involvement described in age‐related TDP‐43 pathology [7, 11]. In contrast, the amygdala‐BL and ERC diverged between groups, with PART showing greater TDP‐N burden, suggesting differential processing, stability or solubility of N‐terminal fragments in this region since TDP‐N dimerization is known to favour higher solubility [5, 10].

  Hippocampal subfields further highlighted disease‐specific patterns. PART exhibited relatively uniform fragment distribution, whereas lad showed selective enrichment of pTDP‐43 in CA2/3 and TDP‐N in the DG and SUB [12, 13, 14]. These findings align with prior observations that CA2/3 and subiculum are early sites of TDP‐43 involvement in PART and AD‐related pathology and suggest that fragment‐specific accumulation may reflect distinct biochemical pathways engaged in each disease process [1].

  Direct comparison between PART and lad revealed that TDP‐C burden was consistently higher in PART across CA2/3, DG and SUB. This enrichment of C‐terminal fragments—known to be aggregation‐prone and neurotoxic—may indicate a more prominent role for proteolytic processing in PART‐TDP pathogenesis in the hippocampus [4, 15]. Conversely, the prominence of TDP‐N in lAD, particularly in the amygdala‐BL and SUB, suggests that N‐terminal species may contribute more substantially to TDP‐43 pathology in the context of AD‐related neurodegeneration, speculatively trying to rescue the accumulation of TDP‐C and hyperphosphorylated TDP‐43 [6, 10].

  Together, these findings support the concept that PART‐TDP and lAD‐TDP are molecularly distinct entities despite overlapping anatomical and pathological similarities [14]. Fragment‐specific signatures may reflect differences in upstream triggers, proteolytic pathways or cellular environments that shape TDP‐43 processing in each condition [4]. Although limited by a small sample size, this work provides initial evidence that TDP‐43 fragment profiling may help differentiate PART‐TDP from lAD‐TDP in early disease stages and may offer a framework for refining diagnostic criteria or developing targeted biomarkers.


## Author Contributions
  G.U. performed fluorescence immunohistochemical studies, as well as quantitative and statistical analyses, collected and analysed the neuropathological and immunofluorescent data. G.U. and R.G.G. drafted the original manuscript and contributed significantly to the drafting of the final manuscript. N.H. contributed to the table and figures. R.R.R. provided neuropathological data samples. K.A.J. and J.W. provided clinical information and expertise in data interpretation. K.A.J. and J.W. also conceptualized, supervised and funded the study. All authors read and approved the last version of the manuscript.


## Funding
  This work was supported by the National Institutes of Health (NIH) under grants: NIH: R01‐AG37491.


## Ethics Statement
  All participants underwent standardized behavioural evaluation and neuropathological assessment, and informed consent was obtained under Mayo Clinic IRB approval which included the ethical standards of the Committee on Human Experimentation at Mayo Clinic by the Helsinki Declaration of 1975. All patients or proxies consented to the research study (their proxies provided consent for patients when needed).


## Conflicts of Interest
  The authors declare no conflicts of interest.


## Supporting information

## Data Availability Statement
  All aggregated data are available in the main text and figures or the Supporting Information. Primary data (e.g., images and spreadsheets) will be provided upon written request to the corresponding author. This paper does not report any original code. Any additional information can also be requested directly from the corresponding author.


## Acknowledgements
  We would like to thank all participating patients and families who have contributed to making this research study possible.