# Molecular dynamics simulations of a multicellular model with cell-cell interactions and Hippo signaling pathway


## Abstract
  The transcriptional coactivator Yes-associated protein (YAP)/transcriptional co-activator with PDZ binding motif (TAZ) induces cell proliferation through nuclear localization at low cell density. Conversely, at extremely high cell density, the Hippo pathway, which regulates YAP/TAZ, is activated. This activation leads to the translocation of YAP/TAZ into the cytoplasm, resulting in cell cycle arrest. Various cancer cells have several times more YAP/TAZ than normal cells. However, it is not entirely clear whether this several-fold increase in YAP/TAZ alone is sufficient to overcome proliferation inhibition (contact inhibition) under high-density conditions, thereby allowing continuous proliferation. In this study, we construct a three-dimensional (3D) mathematical model of cell proliferation incorporating the Hippo-YAP/TAZ pathway. Herein, a significant innovation in our approach is the introduction of a novel modeling component that inputs cell density, which reflects cell dynamics, into the Hippo pathway and enables the simulation of cell proliferation as the output response. We assume such 3D model with cell-cell interactions by solving reaction and molecular dynamics (MD) equations by applying adhesion and repulsive forces that act between cells and frictional forces acting on each cell. We assume Lennard-Jones (12-6) potential with a softcore character so that each cell secures its exclusive domain. We set cell cycles composed of mitotic and cell growth phases in which cells divide and grow under the influence of cell kinetics. We perform mathematical simulations at various YAP/TAZ levels to investigate the extent of YAP/TAZ increase required for sustained proliferation at high density. The results show that a twofold increase in YAP/TAZ levels of cancer cells was sufficient to evade cell cycle arrest compared to normal cells, enabling cells to continue proliferating even under high-density conditions. Finally, this mathematical model, which incorporates cell-cell interactions and the Hippo-YAP/TAZ pathway, may be applicable for evaluating cancer malignancy based on YAP/TAZ levels, developing drugs to suppress the abnormal proliferation of cancer cells, and determining appropriate drug dosages. The source codes are freely available.


## 1 Introduction
  The Hippo pathway has recently attracted attention as a molecular target for anticancer drugs and regenerative medicine [1]. This unique pathway senses cell contacts and mechanical stimulation, supports organ size control and cell differentiation, and acts as a potent tumor suppressor gene [1]. The Hippo pathway is an evolutionarily conserved signaling cascade that controls organ size and tumorigenesis [2–4]. In mammals, the Hippo pathway involves two kinases: MST1/2 and LATS1/2. Under low-density conditions, MST1/2 and LATS1/2 remain inactive, allowing co-activators Yes-associated protein (YAP) and transcriptional co-activator with PDZ binding motif (TAZ) to interact with transcription factors, such as TEAD1-4, in the nucleus, thereby inducing the transcription of genes involved in cell proliferation and survival. In contrast, MST1/2 is activated first under high-density conditions, leading to the phosphorylation of LATS1/2. Activated LATS1/2 phosphorylates YAP/TAZ leads to its sequestration in the cytoplasm by binding to 14-3-3 proteins. Consequently, the YAP/TAZ-induced expression of cell proliferation-related genes is inhibited [5–10].

  YAP and TAZ are major effectors of the Hippo pathway and are considered proto-oncoproteins involved in cancer tissue proliferation, stemness, metastasis, and drug resistance [11–13]. Indeed, in various cancers, increased YAP/TAZ levels have been observed because of mutations in MST1/2 and LATS1/2 as well as gene amplification of YAP1 and WWTR1, which encode YAP and TAZ [14–21]. However, the precise extent of YAP/TAZ protein upregulation in cancer tissues is several-fold higher than that in normal tissues [12, 22, 23], and measures to evade cell cycle arrest under high-density conditions and trigger sustained chronic proliferation [24] remains poorly understood.

  Some methods use cell elasticity and adhesion [25], and potential forces with arguments such as exponential functions [26, 27] to model cell-cell interactions. Previous studies on cells using MD methods includes cases without proliferations [28], reactions and diffusions [29], dynamics of two-species particle systems [30], mitotic cone formations [31], multiparticle collisions in aqueous solutions [32], and 3D models with cell growths and divisions in the context of tumor invasions [25]. However, these studies often did not directly address the intricate molecular signaling pathways that regulate cell proliferation and their interactions with mechanical forces at the multicellular level. Additionally, previous models did not incorporate the dynamic feedback mechanisms of the Hippo pathway on cell proliferation and survival, especially under high cell density conditions.

  This study investigated whether an increase in YAP/TAZ levels is sufficient to induce sustained chronic cancer proliferation. We conducted cell proliferation simulations using a 3D model that considered cell proliferation and cell-cell interactions to achieve such investigations based on reaction networks representing normal and cancerous tissues. We combined MD models with a reaction network model of the Hippo pathway, which controls cell proliferation by inhibiting YAP/TAZ.

  We mimicked normal and cancerous tissues using different initial concentrations of YAP/TAZ molecules. While previous studies used the Lennard-Jones (LJ) potential for modeling intermolecular forces in MD methods [33], we used the LJ potential for the adhesion and repulsion of multiple cells, which have softcore characteristics, avoiding sudden increase when the cells are close [34]. Our approach uniquely integrates the Hippo pathway signaling dynamics with cell-cell interactions, providing a more comprehensive understanding of the regulation of cell proliferation and tumorigenesis.

  In this study, we calculated 3D spatiotemporal patterns of normal and cancerous tissues, including cell survival or cell cycle arrest. We added external factors, such as adhesion, repulsion, and friction, based on kinetic equations to describe the motion of an agent representing each cell. Here, we calculated multicellular time evolutions by solving reaction equations coupled with the MD method, where we built models to incorporate the factors of cell growth and division. Herein, a significant innovation in our approach is the introduction of a novel modeling component that inputs cell density, which reflects cell dynamics, into the Hippo pathway and enables the simulation of cell proliferation as the output response. In addition to the standard MD model, we introduce the cell cycle as a factor to reflect the dynamics of life in this model. We also solved the equations of motion of cells that undergo repeated growth and division and obtained temporal evolutions of the positions of multicellular cells. By integrating the molecular signaling of the Hippo pathway with cell mechanics and cell cycle dynamics, our study offers new insights into the mechanisms driving cancer proliferation and presents a newly and more dynamic model compared to previous research.


## 2 Materials and methods
  We summarize the overall methodology for 3D multicellular simulations in Fig 1A. The green and orange boxes represent the simulations of cell dynamics and intra-cellular dynamics, respectively. The simulation of cell dynamics outputs the cell density (ρ), which is then transferred to the intra-cellular dynamics simulation. This simulation subsequently outputs the concentration of nuclear YAP/TAZ, which induces cell proliferation, back into the cell dynamics. In cancer tissues, YAP/TAZ concentrations are several times higher than in normal tissues, leading to chronic proliferation. We replicated these experimental findings using a three-dimensional (3D) molecular dynamics (MD) model and reaction equation analysis. In the 3D MD model, cell positions and velocities were numerically analyzed using the Verlet method [35], a numerical technique employed in MD to integrate Newton’s equations of motion, renowned for its accuracy and stability in long-term simulations, while assuming potential forces between the cells. Our novel approach within the model includes a sophisticated algorithm for cell division that is based on real-time changes in intracellular signaling pathways, particularly the Hippo-YAP/TAZ pathway. The reaction equations for the Hippo-YAP/TAZ pathway were numerically analyzed using the eigenvalue problem method. Further details of these five models are provided in Fig 1B and the following subsections.


### 2.1 Initializing cells
  Algorithm 1 Initializing cells and 3D multicellular simulation

  1: (1) Initializing cells:

  Input: cell cycle: TCC=20h, duration of mitosis phase: TM=1h, total simulation time tL=L × dt ≅ 10.4TCC = 208 h, dt = 3.75s, L=200000.

  Input:  γ=23−1 , ζ=2−αLJ(1−λ)26,

  Input: er=t(sin ϕ cos θ, sin ϕ sin θ, cos ϕ), θ=random [0, 2π), ϕ=random [0, π),

  Input:  σ0′=5μm , m0=2 ng, σ0=σ0′/ζ, dσ=(23−1)dtσ0/TCC,

  Input: X0=0.15 [μM]

  2: N0=2

  3: if the tissue is normal then

  4:  Xi0=t(0.05,0.2,0)[μM], i=1, 2

  5: else {the tissue is cancer}

  6:  Xi0=t(0.1,0.4,0)[μM], i=1, 2

  7: end if

  8: αi0 = 0, σi0 = σ0, ri0=∓γσ0′er, vi0=∓(1−γ)σ0′er/TM, i=1, 2,

  9: k ← 1

  10: while 1 ≤ k ≤ L do

  11:  t = kdt

  12:  (2) Discrimination of whether cell growth or cell cycle arrest

  13:   In: αik, σik, X2ik, Out: αik, σik, cik, i=1, ⋯, Nk−1.

  14:  (3) Discrimination of whether cells division or nondivision

  15:   In: Nk−1, σik, αik, rik, vik, Xlik, ρik, i=1, ⋯, Nk−1, l=1,2,3.

  16:   Out: Nk, σjk, αjk, rjk, vjk, Xljk, ρj, j=1, ⋯, Nk, l=1,2,3.

  17:  (4) Solving multicellular kinetic equations

  18:   In: rjk, vjk, Out: rjk, vjk, j=1, ⋯, Nk.

  19:  (5) Solving reaction equations of each cell

  20:   In: Xljk, rjk, Out: Xljk, ρjk, j=1, ⋯, Nk, l=1,2,3.

  21:  k ← k + 1

  22: end while 1 ≤ k ≤ L

  Output:  Xik , rik, σi′k, cik

  We assume that the two cells have initial positions r10 and r20 and velocities v10 and v20 with directions of the azimuthal angle in the xy-plane from the x-axis; θ, and the polar angle from the positive z-axis; ϕ according to the pseudocode of Algorithm 1. where rik and vik∈ℝ3 are center positions of i-th cells, i=1, ⋯, Nk, k is natural number representing the time step in time evolution, where k = 0, ⋯, L. L is the maximum number for k, and the time t is given by t = kdt. Nk is the total number of cells at time step k; the initial value N0 is set to 2 at time t=0, γ represents the dimensional ratio between the mother cell just before division and the daughter cells just after division, calculated by subtracting one from the cube root of two, such that the volume of one mother cell is equal to the sum of the volumes of the two daughter cells; γ=(23−1). This assumption is based on previous researches [36, 37] that determined cell division is regulated by whether the cell size exceeds a certain threshold or not.

  t(x, y, z) is a vector with components x, y, z in the Cartesian coordinate system, er is the radial unit vector in the polar coordinate system. θ and ϕ are uniform random numbers [0, 2π) and [0, π), respectively; the directions of cell division are random [38], and the upper-right subscripts represent the discrete values at time t=kdt. Algorithm 1 describes the calculations of the entire cell-cell interaction model of elements (1)–(5); details of (2)–(5) are described in the following sections.


#### 2.1.1 Modeling of cancer and normal tissues
  To investigate whether the increased levels of YAP/TAZ in cancer tissues led to sustained chronic proliferation, we used two models representing normal and cancerous tissues. In this simulation, we defined the variables X0 and initial values of X1,i–X3,i as presented in Table 1. The parameters are set as follows:


### 2.2 Discriminate between cell growth and cell cycle arrest
  Depending on whether the Nuclear YAP/TAZ of the i-th cell, X2ik, was larger or smaller than the concentration threshold Xth, we determined whether the cells experience growth or cell cycle arrest. We express these states using four cell colors defined by the cell color scheme in Fig 2; cell colors of orange and red correspond to the mitotic [M (αi < TM)] and cell growth [G1 (αi > TM)] phases of growing cells; where αi is the age of i-th cell, that is, the time immediately after division, and cell colors of cyan and blue correspond to the M and G1 phases of the cell cycle arrest, respectively. ci is color index of i-th cell, which assigned for the colors of cyan, orange, blue and red to 0, 1, 2, and 3, respectively. During the aging of i-th cell from 0 to TCC, the cells grow from σi=σ0 to σi=23σ0 if X2i > Xth where TCC ≡ TM + TG1 is the cell cycle, TM and TG1 are the periods of the M and G1 phases, respectively. The cell radius in the M phase is σ0′ immediately after cell division, and the sizes of the two daughter cells are within the range of one mother cell, as indicated by the red dashed circle. The green two-way arrows on the left and right sides of Fig 2 indicate that the red and orange cells in the growing state and the blue and cyan cells in the cell-cycle-arrest state alternate. The ith cell is discriminated as belonging to the growing state (down green arrow) or cell cycle arrest (up green arrow) if X2i becomes greater or less than Xth, respectively. In the M phase, the cells first divide into two daughter cells at a distance of ±γσ0′ from the central position of the mother cell. From age 0 to TM, the cells start growing at a growth rate dσ/dt=γσ0/TCC and the multicellular structures are rearranged due to the equilibrium of forces acting among the cells. At ages TM and above in the G1 phase, each cell grows and moves independently. With cell cycle arrest, αi remains constant, while in cell growth, the age of the i-th cell, αi, increases. When αi reaches time TCC, the cell divides. If the cell remains in a red or orange state over time TCC, it’s defined as one cycle.

  We define the cell growth processes for each dt progress at time t=kdt, k=1, ⋯, L, if σ0<σik<23σ0 and X2i > Xth as follows: αi←αi+dt,i=1,⋯,N, (1a) σi←σi+dσ,i=1,⋯,N. (1b)


### 2.3 Discriminate between cell division and nondivision
  We assume cell division if i-th cell becomes σik≥23σ0 at time t=kdt, k = 1, ⋯, L, which assumption is based on previous studies [36, 37] that have determined cell division is regulated by whether the cell size exceeds a certain threshold or not. The number, position, and velocity of cells are updated as follows: N←N+1, (2a) σi←σ0, (2b) σN←σ0, (2c) αi←0, (2d) αN←0, (2e) ri←ri-γσ0′er, (2f) rN←ri+γσ0′er, (2g) vi←-(1-γ)σ0′er/TM, (2h) vN←+(1-γ)σ0′er/TM, (2i) Xli←Xli, (2j) XlN←Xli, (2k) ci←1, (2l) cN←1. (2m)

  If σik<23σ0, Nk, αik, rik and vik, inherit the values at previous time t=(k−1)dt.


### 2.4 Solve multicellular kinetic equations using MD method
  By solving the kinetic differential equations using the Verlet method S2 Appendix, we calculated the time evolutions of the cell positions rik and velocities vik, i = 1, ⋯, Nk, k = 0, ⋯, L.


### 2.5 Solve reaction equations of each cell in the multicellular system
  In this section, we construct a model of reaction network of the Hippo-YAP/TAZ signaling pathway [40] in Fig 3 an example. The corresponding reaction equations are given by Eqs (3a), (3b) and (3c). X1i0, X2i0, and X3i0 are the concentrations of YAP/TAZ cytoplasm, YAP/TAZ nucleus, and P-YAP/TAZ cytoplasm, respectively. Translocation, phosphorylation, dephosphorylation, and phosphate are indicated by orange, green, and blue arrow lines and circled P marks, respectively, in Fig 3. Accordingly, the reaction equations for the molar concentrations Xli of l-th molecule in i-th cell are given as follows: dX1idt=-a1X1i+a2X2i+a3X3i-b1ρiX0X1i, (3a) dX2idt=+a1X1i-a2X2i, (3b) dX3idt=-a3X3i+b1ρiX0X1i, (3c)

  The reaction equation parameters are presented in Table 1 [5, 22, 39]. The derivation process of the model and the simulations are explained in S1 Appendix. We can also diagonalize the right-hand sides of Eqs (3a), (3b) and (3c), which we discuss later in Discussion and S3 Appendix using the eigenvalue problem method. We calculate the packing fraction ρi of the i-th cell, which is defined as the sum of exponential functions of the distance between the i-th cell and other multicellular distances formulated in S4 Appendix, where the cell position ri, i=1, ⋯, N obtained using MD calculations. We can solve these reaction equations in conjunction with the MD equations when calculating ρi in S4 Appendix.


## 3 Results
  This section calculates the time evolution of molar concentrations and 3D multicellular spatiotemporal properties. We set the initial cell radius to σ0′=5μm, with σ0= σ0′/ζ=4.53μm; The parameters are presented in Table B1 of S2 Appendix, where ζ is the ratio of cell radius to the σi of i-th cell; ζ=2−αLJ(1−λ)26, where αLJ is parameter of the LJ potential, λ is a coupling parameter. For normal and cancerous tissues, we set the initial molar concentrations to (X1i0, X2i0, X3i0)=(0.05, 0.2, 0) and (0.1, 0.4, 0)[μM], respectively, as listed in Table 1 [22]. We set cell growth to occur when the nuclear levels of YAP/TAZ (X2i) reach or exceed a specific threshold value Xth, where Xth was set to 0.012 μM experimentally.


### 3.1 Time evolutions of molecular concentrations
  We find solutions to the simultaneous first-order differential equations, Eqs (3a), (3b) and (3c), to calculate the time evolutions of the multicellular cells with the parameters in Table B1 of S2 Appendix using the eigen-value problem (EVP) formulations in S3 Appendix. The Time evolution of nuclear YAP/TAZ concentrations in normal and cancer tissues are shown in Fig 4A and 4B, respectively. The red, green, and blue solid lines represent maximum, mean, and minimum of X2i for i=1⋯N (total number of multicellular cells) defined as follows: Xlmean=1N∑i=1NXli, (4a) Xlmax=maxi=1,⋯,N(Xli), (4b) Xlmin=mini=1,⋯,N(Xli), (4c) where X2max, X2mean, and X2min are the mean, maximum, and minimum molecular concentrations Xli, l=1, 2, 3, respectively. The black dashed lines represent the threshold Xth. We discriminate between cell proliferation and growth arrest depending on whether X2i exceeds Xth. If X2min falls below Xth, the cells experience growth arrest. For normal tissues, we observe cell cycle arrests in addition to cell proliferation, especially 100 tens of hours later in the time evolution in Fig 4A, where X2min is lower than Xth. In contrast, for cancer tissues, X2min do not fall below Xth until around 200 h, as shown in the time evolution in Fig 4B.


### 3.2 Time evolutions of 3D real-images
  We calculated 3D real-images shown in Fig 5 of (A, B) normal and (C, D) cancer tissues by solving the multicellular equations of motions in S2 Appendix using the Verlet method using recursion formulas Eq. (1.5) in [41] and coupled with the reaction equations Eqs (3a), (3b) and (3c). Panels (A, C) and (B, D) show the perspective view and cross-section at x=0 of the multicells at t= 208 hours (10.4 cell cycles) immediately after a cell dividing, respectively. The scale of these images is in [μm]. Colors of the spherical cells are orange and red for cell growth in the M and G1 phases and cyan and blue for cell cycle arrest in the M and G1 phases, respectively. We show videos of 3D perspective views for normal and cancer tissues over 0–208 h immediately after cell division, as shown in the links S1 and S2 Videos, respectively, and cross-sections of 3D moving images for normal and cancer tissues, as shown in S3 and S4 Videos. The cross-sections show cuts at x=0 in the perspective views. To quantitatively evaluate the cell proliferation outcomes in normal and cancerous tissues, we calculated the time-dependent changes in the total number of multicellular structures, as shown in Fig 6 (0–208 hours). Exponential cell growth is suppressed in normal tissues, particularly in the center of tissues. However, in cancer tissues, despite having YAP/TAZ levels only twice as high as those in normal tissues, cancer tissues demonstrated exponential cell proliferation.


## 4 Discussion
  We explored the effects of increased YAP/TAZ levels on cell proliferation in cancer cells. YAP/TAZ play a role in the cell nucleus and are restrained by the activated Hippo pathway under high-density conditions, causing them to be retained in the cytoplasm and ultimately stopping cell growth. Many cancer cells have significantly higher YAP/TAZ expression compared to normal cells [12, 22, 23]. However, it remains uncertain whether this increase in YAP/TAZ expression can override the inhibitory effect of the Hippo pathway and maintain cell growth. We developed a computational model using MD simulations to investigate this type of chronic proliferation maintenance. This model mimics cell interactions driven by external factors such as adhesion, repulsion, and friction.

  This study focuses on a model that integrates cell dynamics, which affect cell density, and intra-cellular dynamics, which influence YAP/TAZ levels. Our goal was to understand how increased YAP/TAZ levels in cancer cells affect their proliferation under high-density conditions. Using this model, we monitored the changes in nuclear YAP levels (X2i) over time in normal tissues. After 100 h, the minimum X2i fell below the threshold (Xth) required for nuclear YAP levels to support proliferation.

  Additionally, in normal tissues, we observed exponential cell proliferation for 100 tens of hours, followed by cell cycle arrest in the central region of the cell population (Fig 5A and 5B), reducing exponential growth (Fig 6). In contrast, in cancer tissues, despite a twofold increase in YAP/TAZ expression compared to normal tissues, cell cycle arrest was rarely observed in the central region (high-density conditions) of the cell population (Fig 5C and 5D). Instead, exponential cell proliferation continued for up to 200 h (Fig 6). Fig 7 shows time evolutions of the total number of multi-cells of cancer and normal tissues with (X10,X20)=(0.1,0.4), (0.05, 0.2), and an exponential function with a time rounding-up parameter: exp⌈t/20h⌉. From this semi-log plot, it is quantitatively confirmed that the red curve for cancer cells almost matches the exponential function of the orange dashed curve up to 200 hours, indicating that exponential cell growth continues up to that point. The basis for choosing this time point to draw conclusions is the nature of cancer cells, specifically as a model demonstrating exponential cell growth.

  As shown in Fig 4B, in cancer tissues, X2i rarely fell below Xth even after 200 h. Thus, a two-fold increase in YAP/TAZ levels was sufficient to override the density-dependent growth inhibition effect and sustain exponential proliferation, thereby increasing cancer malignancy.

  This model, integrating cell dynamics and intra-cellular dynamics, provides a comprehensive understanding of the influence of both cell density and YAP/TAZ concentration on proliferation, contributing to our understanding of the proliferative characteristics of normal and cancer cells.

  From the comparison between Fig 5A–5C and 5D, the following computational and biological observations can be made despite only a twofold increase in YAP/TAZ levels:

  Moreover, Fig 6 quantitatively demonstrates that cells typically double with each division, leading to exponential growth if unchecked. In normal tissues, this exponential increase is significantly suppressed. Remarkably, cancer cells with merely a twofold increase in YAP/TAZ levels exhibit almost no growth inhibition and continue to increase exponentially. This suggests that cancer cells with elevated YAP/TAZ levels bypass typical proliferative checks, underscoring the pivotal role of YAP/TAZ in regulating cellular proliferation dynamics in oncogenic contexts. The ratio of X2 between cancer and normal cells (C/N_X2mean) exhibits a temporal evolution in Fig 8. Here, by setting the initial ratio of X2(cancer)/X2(normal) to 2, this ratio remains around 2 for up to 100 hours. Interestingly, after 100 hours, regions where the ratio approaches threefold emerge. This nonlinear region mediated by multicellularity, concerning nuclear YAP/TAZ concentration, can be seen as the reason why cancer cells continue to proliferate without showing cell cycle arrest.

  Reports have linked higher YAP protein levels to a poorer prognosis in patients with cancer [11, 13, 21]. Currently, clinical trials are underway to investigate drugs, such as VT3989, that inhibit the nuclear activity of YAP/TAZ. However, excessive doses of these drugs hinder the proliferation of normal tissues. Using the proposed 3D mathematical model, calculating the appropriate dose of VT3989 based on YAP/TAZ levels may become possible.

  To investigate the influence of the packing fraction ρi on concentrations, we define the solutions of the reaction equations, Eqs (3a), (3b) and (3c), for ρi=ρ0 as Xlρ=ρ0, where ρ0 is a certain density. On Fig 9A and 9C, for normal and cancer tissues, we plot time evolutions of X2mean, X2ρ=0.0, X2ρ=0.5, X2ρ=1.0, and X2ρ=1.5 as a green solid line and brown, orange, cyan, purple dashed lines, respectively. On Fig 9B and 9D, we also plot time evolutions of X3mean, X3ρ=0.0, X3ρ=0.5, X3ρ=1.0, and X3ρ=1.5 as a green solid line and brown, orange, cyan, purple dashed lines, respectively. The time evolution of YAP/TAZ concentrations X2 and X3 falls within the range of ρ=0 to 1.5 in both normal and cancer tissues.


## 5 Conclusion
  In this study, we performed 3D multicellular simulations combining MD methods with reaction network models of the Hippo pathway, which is known to regulate cell proliferation by inhibiting YAP/TAZ activity. Our approach effectively simulated cell division and growth, preventing cell overlap by assigning exclusive domains to each cell with LJ (12–6) potential with a softcore character, and integrating cell cycle dynamics, particularly the M and G1 phases. We introduced a novel modeling component that inputs cell density, reflecting cell dynamics, into the Hippo pathway simulation. This innovation allowed us to simulate cell proliferation as an output response, providing a more detailed and dynamic representation of how intracellular signaling modulates cell division decisions.

  To investigate whether the elevated levels of YAP/TAZ observed in cancer tissues are sufficient to sustain chronic proliferation, we developed models representing time evolutions of normal and cancerous tissues. Our 3D simulations revealed that while normal tissues exhibited cell cycle arrest and suppression of exponential growth, cancer tissues with YAP/TAZ levels twice as high demonstrated continuous exponential proliferation. These findings suggest that increased YAP/TAZ alone can bypass contact inhibition under high-density conditions, contributing to unchecked proliferation in cancer cells. Our model’s integration of cell dynamics and intra-cellular dynamics could position it as a tool for evaluating cancer malignancy, exploring therapeutic interventions targeting YAP/TAZ, and optimizing drug dosages.


## Supporting information