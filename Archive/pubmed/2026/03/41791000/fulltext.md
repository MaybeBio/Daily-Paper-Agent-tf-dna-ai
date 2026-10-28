# Analysis of Large Language Model Decision Making in Hormone Receptor–Positive/Human Epidermal Growth Factor Receptor 2–Negative Early Breast Cancer


## PURPOSE
  To assess the ability of GPT-4o in adjuvant treatment decision making in hormone receptor–positive (HR+)/human epidermal growth factor receptor 2–negative (HER2−) early breast cancer by comparing its recommendations with those of clinicians including Oncotype DX data, and to explore its potential as a decision-support tool in routine clinical practice.


## METHODS
  We compared clinician and GPT-4o recommendations in patients tested with Oncotype DX in routine practice at the University of Naples Federico II (n = 607, cohort 1 [C1]) and within the prospective, multicenter PRO BONO study (n = 237, cohort 2 [C2]). Pre– and post–Oncotype DX treatment recommendations were categorized as chemotherapy (CT) + endocrine therapy (ET) or ET alone. Concordance between clinician and GPT-4o recommendations was assessed using agreement rates and Cohen's kappa. The accuracy of Oncotype DX results was evaluated using the AUC metric.


## RESULTS
  The agreement between clinicians and GPT-4o in pretest recommendations was 68% (kappa, 0.381 [95% CI, 0.31 to 0.45], P < .001) in C1 and 70% (0.401 [95% CI, 0.29 to 0.52], P < .001) in C2. Before Oncotype DX, clinicians recommended CT more frequently than GPT-4o for C1 (58% v 38%) and C2 (53% v 43%). Post-test agreement increased to 93% (0.814 [95% CI, 0.76 to 0.87], P < .001) in C1 and 90% (0.741 [95% CI, 0.64 to 0.84], P < .001) in C2. The agreement between pre– and post–Oncotype DX treatment recommendations for clinicians was 56% and 63% versus 68% and 60% for GPT-4o in C1 and C2, respectively. GPT-4o showed higher accuracy in predicting low than high genomic risk in postmenopausal patients (87% v 43% in C1; 85% v 45% in C2, P < .001) and low versus intermediate and high risk in premenopausal patients in both cohorts (P < .001).


## CONCLUSION
  The agreement between clinicians and GPT-4o in pretest recommendations was modest but improved post-test, highlighting the importance of multigene testing and the potential of large language models in clinical decision making.


## BACKGROUND
  Artificial intelligence (AI) is progressively transforming health care by corroborating and enhancing physicians' capabilities in complex clinical scenarios, particularly in screening, diagnosis, and treatment.1,2 Similarly to various medical specialties, AI is rapidly emerging as a pivotal tool in radiology,3-6 oncology,7 and pathology.8-13 Despite this, the integration of AI into treatment decision making remains challenging since this process is inherently multifactorial, necessitating the interplay among physician expertise, tumor biology, and patient characteristics and preferences.

  Among AI models, next-generation pretrained large language models (LLMs)14 represent a practical and user-friendly approach with the ability to generate human-like responses across multiple medical domains.15 LLMs could assist clinicians in summarizing data, answering clinical questions, and providing treatment recommendations supporting medical decision making.16

  However, their clinical integration presents greater challenges depending on the quality of available patients' and tumor-specific data, raising criticisms about their advantages, limitations, and feasibility in daily practice.

  To evaluate the clinical readiness of LLMs and their potential role in supporting medical decision making, we conducted a comparative analysis between LLM-assisted and physician-guided decisions in a commonly encountered clinical scenario: patients with hormone receptor–positive/human epidermal growth factor receptor 2–negative (HR+/HER2–) early breast cancer (eBC), eligible for adjuvant therapy, and undergoing multigene testing. Specifically, we assessed GPT-4o's recommendations regarding multigene testing indications, test selection, and treatment decisions both before and after testing. Additionally, we evaluated the concordance in treatment recommendations between clinicians and GPT-4o pretest, and the agreement between pre- and post-test recommendations provided by both clinicians and GPT-4o. Finally, we assessed GPT-4o's capacity to predict multigene test results.


## METHODS

### Study Objectives
  This study aimed to evaluate the performance of GPT-4o in formulating adjuvant treatment recommendations in patients with HR+/HER2– eBC. The analysis focused on three main areas:Indications for multigene testing and selection of test type by GPT-4o.Pre- and post-test therapy recommendations provided by GPT-4o compared with those proposed by clinicians.Prediction of multigene test results performed by GPT-4o.


### Population
  The study included 844 consecutive patients with HR+/HER2– eBC who underwent surgery and subsequent Oncotype DX testing recommended by their physicians at the University of Naples Federico II (cohort 1 [C1]) or within the PRO BONO study17 (cohort 2 [C2]). Pre- and post-test clinical decisions were prospectively collected for all patients by multidisciplinary oncology teams within multi-institutional health care networks (C1) and academic hospitals (C2). Data on clinicians' pre- and post-test decisions were collected for each patient, including indications for multigene testing, the specific test used, and treatment recommendations. Treatment recommendations were categorized as chemotherapy (CT) followed by endocrine therapy (CT-ET) or ET alone, with additional details on the type of CT and ET prescribed.


### Question Format for LLM Treatment Indications and Prediction Assessment
  To evaluate the predictive performance of the model, a series of structured, clinically oriented questions were developed. A zero-shot prompting strategy was used. In this approach, the model generated responses based solely on its preexisting knowledge and the information contained within each prompt.18 The questions were designed to assess the indications for adjuvant therapy as illustrated in Figure 1. This approach was chosen to evaluate how ChatGPT performs, when applied to routine clinical decision-making tasks.


### Statistical Analysis
  To evaluate the agreement between GPT-4o and clinicians, treatment recommendations were compared in terms of overall strategy (CT-ET v ET alone) and the specific types of CT and ET suggested.

  Interdecision reliability was assessed using agreement rates and Cohen's kappa coefficient. Separate analyses were performed for C1 and C2 to identify potential differences in the performance of clinical decisions compared with LLM-assisted recommendations within different frameworks.

  To further characterize the dynamics of agreement between clinicians and LLM, we evaluated two patterns where only one of the two decision-makers modified their recommendation between the pre- and post-test settings: cases where clinicians changed their recommendation while the LLM's recommendation remained stable (clinician-shift/stable LLM) and vice versa (LLM-shift/stable clinician).

  Furthermore, GPT-4o predictions of genomic test results were expressed as percentage probabilities for specific risk categories:Postmenopausal patients: High risk (recurrence score [RS] ≥26) versus low risk (RS ≤25).Premenopausal patients: High risk (RS ≥26), intermediate risk (RS 16-25), and low risk (RS ≤15).

  The accuracy of GPT-4o genomic prediction was evaluated using the AUC metric. The statistical association between the predicted and observed test results was analyzed using the chi-square test.

  All statistical analyses were performed with R software (version 4.4.1).


### Error Analysis
  A human-in-the-loop approach was used19,20 for error analysis to assess significant discrepancies produced by the LLM model, including hallucinations, inconsistencies, inappropriate results, and reported references. Further information and methods are detailed in the Data Supplement.


### Ethics Approval
  This study was conducted in accordance with the ethical standards outlined in the Declaration of Helsinki. Ethical approval was obtained from Comitato Etico Campania 3 (reference number, Prot. 331/2024). Written informed consent was obtained from participants before their inclusion in the study.


## RESULTS

### Baseline Characteristics and Indication for Multigene Testing
  A total of 844 patients with HR+/HER2– eBC were included. Among them, 607 (68.7%) patients were treated by local multidisciplinary oncology teams (C1), whereas the remaining 237 patients (31.3%) were enrolled in the PRO BONO study17 (C2). All patients underwent Oncotype DX testing as recommended by their treating physicians' recommendation. Patient characteristics, including age, menopausal status, nodal involvement, and multigene testing results, are summarized in Table 1.

  For all patients (n = 844), GPT-4o prospectively confirmed physicians' indication for genomic testing, with the Oncotype DX test being the only multigene assay selected among all the available assays.


### Pretest Treatment Recommendations
  In both cohorts, GPT-4o recommended ET alone more frequently than clinicians (Tables 2 and 3). In C1, GPT-4o recommended ET for 375 patients (62%), compared with 255 patients (42%) recommended by clinicians (Table 2). Similarly, in C2, GPT-4o recommended ET for 135 patients (57%), whereas academic clinicians recommended ET for 110 patients (46%; Table 3). Detailed data on specific ET regimens were only available for C1 (Table 2). GPT-4o most frequently selected aromatase inhibitors (ArI; 265 patients, 44%), followed by tamoxifen (TAM; 61 patients, 10%) and TAM plus luteinizing hormone–releasing hormone analog (LHRHa; 48 patients, 8%). In contrast, clinicians recommended ArI for 196 patients (32%), ArI plus LHRHa for 47 patients (8%), and TAM plus LHRHa for nine patients (2%). Conversely, CT-ET was more frequently recommended by clinicians. The most selected CT regimen in C1 was docetaxel plus cyclophosphamide (TC; 186 patients, 31%), followed by doxorubicin plus cyclophosphamide and paclitaxel (AC-T; 167 patients, 27%). In contrast, GPT-4o recommended TC for 42 patients (7%) and AC-T for 168 patients (28%).


### Post-Test Treatment Recommendations
  After multigene testing, both GPT-4o and clinicians consistently recommended ET in C1 (461 patients, 76%; 460 patients, 76%) and C2 (170 patients, 72%; 178 patients, 75%; Tables 2 and 3). Among the ET regimens (Table 2), ArI monotherapy remained the most frequently selected option, as recommended by both clinicians (332 patients, 55%) and GPT-4o (326 patients, 54%). ArI plus LHRHa was the second choice among clinicians (99 patients, 17%), whereas GPT-4o more frequently recommended TAM (65 patients, 11%) and TAM plus an LHRHa (56 patients, 9%). CT was less frequently recommended by clinicians in both C1 (146 patients, 24%) and C2 (67 patients, 28%; Tables 2 and 3). GPT-4o also had a lower CT recommendation rate, suggesting CT for 146 patients (24%) across both cohorts (Tables 2 and 3). Among CT regimens, epirubicin/doxorubicin plus cyclophosphamide/AC + T was the most frequently selected regimen, favored by both clinicians (82 patients, 13%) and GPT-4o (97 patients, 16%; Table 2).


### Concordance Between LLM and Clinicians' Treatment Recommendations
  The agreement between GPT-4o and clinicians' pretest treatment recommendations (CT-ET v ET) was 68% (kappa, 0.381 [95% CI, 0.31 to 0.45], P < .001) in C1 and 70% (kappa, 0.401 [95% CI, 0.29 to 0.52], P < .001) in C2 (Table 4). After multigene testing, concordance improved significantly to 93% (kappa, 0.814 [95% CI, 0.76 to 0.87], P < .001) in C1 and 90% (kappa, 0.741 [95% CI, 0.64 to 0.84], P < .001) in C2 (Table 4). In C1, the concordance between clinicians' pretest and post-test recommendations was 56% (kappa, 0.189 [95% CI, 0.13 to 0.25], P < .001), whereas GPT-4o showed slightly higher consistency, with a 68% agreement rate (kappa, 0.262 [95% CI, 0.19 to 0.34], P < .001; Table 4). In C2, clinicians exhibited 63% agreement (kappa, 0.284 [95% CI, 0.17 to 0.38], P < .001) between pre- and post-test recommendations, whereas GPT-4o demonstrated 60% agreement (kappa, 0.14 [95% CI, 0.01 to 0.25], P < .001; Table 4). Changes in treatment recommendations in both cohorts are detailed as alluvial plots in the Data Supplement.


### Agreement Between Pretest and Post-Test Decisions Provided by LLM
  In C1, GPT-4o agreement was higher in N0 patients compared with N+ patients (70% v 52%, P = .001). Although numerically higher in patients with RS ≤25 compared with those with RS ≥ 26 (60% v 60%, P = .08), the difference was not statistically significant. GPT-4o agreement was independent of age (P = .608). Similarly, in C2, GPT-4o demonstrated significantly higher agreement in treatment recommendations for patients with node-negative (N0) compared with those with node-positive (N+) tumors (69% v 40%, P = .001). Concordance did not differ between patients with an Oncotype DX RS <25 and those with RS ≥25 (P = .834). GPT-4o agreement was also higher in patients age ≤50 years compared with those age >50 years (67% v 59%, P = .001).


### Agreement Between Pretest and Post-Test Decisions Provided by Clinicians
  In C1, clinician agreement was higher for patients with N0 than for those with N+ tumors (56% v 41%, P = .002). In contrast to GPT-4o, clinician agreement was significantly higher for patients with RS ≥26 than for those with RS ≤25 (67% v 50%, P = .001) but remained independent of age (P = .741). In C2, clinician agreement was also significantly higher for patients with RS ≥26 than for those with RS ≤25 (75% v 60%, P = .04). However, in contrast to the data from C1, clinician agreement in C2 was independent of age and nodal status (P = .846).


### Determinants of Treatment Decisions
  In C1, the disagreement between GPT-4o and clinicians on pretest decisions was independent of nodal status (N0 v N+, P = .407) and RS (≥26 v ≤25, P = .658). A nonsignificant trend was observed for age (>50 v ≤50 years, 30% v 37.6%, P = .06). Conversely, in post-test decisions, disagreement remained independent of age (P = .348), nodal status (P = .351), and RS (P = .508). In C2, pretest disagreement was independent of age (P = .529), nodal status (P = .921), and RS (P = .174). However, for post-test decisions, a higher rate of disagreement was observed for N+ compared with N0 patients (18% v 8%, P = .03), whereas disagreement remained independent of age (P = .328) and RS (P = .223). Cases of clinician-shift/stable LLM were significantly more frequent among premenopausal patients in C1 (22.5%) and patients with an RS ≤25 in both cohorts (18% in C1 and 19.3% in C2); conversely, cases of LLM-shift/stable clinician were significantly more frequent among patients with high RS (≥26) in C1 (37.3%) and N+ in C2 (31.7%; Data Supplement, Tables S1 and S2).


### LLM Prediction of Oncotype DX Result
  GPT-4o prediction of RS result varied by menopausal status and risk category in both cohorts (Fig 2). In C1 (Fig 2A), GPT-4o achieved an AUC of 0.817 (95% CI, 0.790 to 0.846) in postmenopausal patients and 0.700 (95% CI, 0.695 to 0.740) in premenopausal patients, whereas in C2 (Fig 2B), the AUC was 0.803 (95% CI, 0.758 to 0.858) and 0.654 (95% CI, 0.567 to 0.759), respectively. Among postmenopausal patients, GPT-4o demonstrated higher accuracy in predicting low than high genomic risk (C1: 75% v 62%; C2: 85% v 45%; P < .001). In premenopausal patients, GPT-4o demonstrated higher accuracy in predicting low genomic risk compared with both intermediate and high genomic risk, in both C1 (61% v 50% v 42%, P < .001) and C2 (48% v 43% v 30%, P = .04; Fig 2).


### Error Analysis
  Hallucinations in the initial case summary were identified in 3% of the cases. No factual, logical, or linguistic hallucinations were detected at any of the three decision points. By contrast, at least one reference hallucination was observed in up to 28% of cases. Further information is supplied in the Data Supplement.


## DISCUSSION
  We conducted a comprehensive analysis of LLM-assisted decision making in HR+/HER2– eBC, both in routine clinical practice (C1) and within a clinical study17 (C2). Our findings underscore key insights into the potential role of LLMs in supporting oncology decision making while also highlighting the challenges that need to be addressed.

  Previous studies have investigated the use of ChatGPT in breast cancer management.21,22 ChatGPT showed to provide appropriate breast cancer screening recommendations23 and demonstrated substantial accuracy and reliability in answering questions raised by patients with breast cancer about surgical treatment.24 A recent trial suggested that GPT-4 assistance could effectively improve physician performance in patient care tasks.25 Finally, an independent analysis evaluating the concordance of treatment recommendations between the Multidisciplinary Tumor Board (MTB) and five publicly available LLMs in 20 complex breast cancer cases showed high agreement of GPT-4o and the MTB (82.4%).26

  To our knowledge, our study is the first to systematically evaluate the potential of ChatGPT to generate personalized treatment recommendations for a large cohort of patients with eBC.

  First, we evaluated the indication for multigene testing and the selection of the test provided by GPT-4o. In both C1 and C2, multigene testing was recommended in all patients. Oncotype DX was the test selected for 100% of patients, in agreement with highest level of evidence (IA), as reported by international guidelines.27 The rationale for the choice of Oncotype DX was its prognostic and predictive value, longer time of use also supported by extensive real-world evidence. This result seems to be in slight contrast to the findings of a recent study28 where ChatGPT was used to assess the need for both Oncotype DX in 100 patients with HR+/HER2– eBC at intermediate risk. In contrast to our findings, ChatGPT suggested Oncotype DX in most but not all patients (61%). This discrepancy may be due to methodological differences. In particular, comorbidities were not reported in our study, and this may have limited the capability of GPT-4o to identify patients not eligible to CT and thus to multigene testing.

  Before multigene testing, GPT-4o predominantly recommended ET alone as the most appropriate adjuvant therapy (62% of cases in C1 and 57% in C2). By contrast, clinicians recommended ET alone in 42% and 46% of patients in C1 and C2, respectively, more frequently favoring CT-ET than GPT-4o. This discrepancy may reflect the tendency of clinicians to adopt a more aggressive treatment approach, influenced by their clinical experience and the goal of minimizing the risk of undertreatment. Accordingly, the clinician-shift/stable LLM pattern was more frequent among premenopausal patients in C1, consistent with a clinician inclination toward CT to reduce the perceived risk of suboptimal therapy in younger patients. Conversely, GPT-4o may exhibit a more conservative approach in cases of uncertainty, at least in part due to intrinsic biases in its information-processing mechanisms or to decision heuristics inherent in its training approach.

  Regarding the selection of CT regimens, GPT-4o recommended only standard CT regimens, mostly matching those commonly used by clinicians (Table 3); only rarely (9% in the pretest and 4.7% in the post-test settings), GPT-4o chose less commonly employed regimens (eg, fluorouracil/epirubicin/cyclophosphamide-docetaxel), which, although standard, has become progressively less used.

  Despite the relatively low concordance in treatment recommendations observed between clinicians and GPT-4o before receiving Oncotype DX results, the agreement increased significantly after Oncotype DX testing, reaching 93% in the real-world cohort and 90% in the clinical study cohort. These findings highlight the critical role of genomic testing in refining treatment strategies and standardizing clinical decisions, by reducing variability among health care providers.29

  Although the overall results appear to be consistent between C1 and C2, the agreement between pre- and post-test clinician decisions was numerically higher in C2 than in C1. These imbalances likely stem from differences between real-world practice and clinical study conditions, not from patient factors. The structured, multidisciplinary design of the PRO BONO study, with expert oncologists from high-volume hospitals, likely promoted greater consistency between pre- and post-test decisions.

  The LLM predicted Oncotype DX RS values more accurately in postmenopausal than in premenopausal patients, likely due to different classification frameworks (ie, two risk categories for postmenopausal and three for premenopausal patients), making predictions more variable in the latter group. The increased granularity of classification in the premenopausal group may also have introduced greater complexity in accurately identifying the corresponding RS range, potentially contributing to the increased variability in prediction.

  Furthermore, GPT-4o demonstrated higher accuracy in predicting low versus high genomic risk both in pre- and postmenopausal patients.

  In the error analysis, hallucinations were uncommon in case summaries (3%) and were not observed at the decision points (Data Supplement). By contrast, citation issues were frequent (25%-28% across time points), predominantly topic-related yet context-inappropriate. These findings are consistent with previous evidence30 and underscore that citation generation and clinical recommendation generation are partially independent behaviors of LLMs. Consequently, references supplied by the model may not reliably substantiate otherwise reasonable recommendations and should be appraised separately in clinical validation workflows.

  Several limitations of our study should be acknowledged.

  First, our study did not involve any model training or fine-tuning process. Of note, our aim was not to develop a predictive model but rather was to investigate how ChatGPT performs when integrated into routine clinical practice.

  Moreover, the use of a single LLM model (GPT-4o) may limit the generalizability of our findings. Furthermore, clinician decisions for both C1 and C2 were collected prospectively, whereas LLM-generated decisions were obtained retrospectively.

  Finally, our analyses did not account for long-term patient outcomes, which are critical for validating the clinical utility of LLM-assisted decision making.

  Our findings suggest that LLMs, such as GPT-4o, can effectively integrate standardized clinicopathologic variables and genomic data to align with clinician-recommended treatment decisions, particularly following multigene testing. However, caution is warranted when relying solely on LLM for decision making, especially in cases requiring nuanced clinical judgment. Rather than replacing multidisciplinary expertise, LLMs should be viewed as a complementary tool that enhances oncologic decision making by fostering a more standardized and data-driven approach to patient care.


## DATA SHARING STATEMENT
  The datasets generated and/or analyzed during the current study are available from the corresponding author upon reasonable request.


## AUTHOR CONTRIBUTIONS
  Conception and design: Roberto Buonaiuto, Aldo Caltavituro, Grazia Arpino, Carmine De Angelis, Mario Giuliano

  Provision of study materials or patients: Luigi Leo, Massimiliano D’Aiuto, Roberto Bianco, Michelino De Laurentiis, Grazia Arpino, Mario Giuliano

  Collection and assembly of data: Roberto Buonaiuto, Aldo Caltavituro, Rossana Di Rienzo, Angela Grieco, Federica P. Mangiacotti, Alessandra Longobardi, Vincenza Cantile, Vittoria Molinaro, Martina Pagliuca, Giuseppe Buono, Pietro De Placido, Erica Pietroluongo, Valeria Forestieri, Claudia Martinelli, Vincenzo di Lauro, Luigi Leo, Massimiliano D'Aiuto, Michelino De Laurentiis

  Data analysis and interpretation: Roberto Buonaiuto, Aldo Caltavituro, Giampaolo Bianchini, Carmen Criscitiello, Roberto Bianco, Lucia Del Mastro, Michelino De Laurentiis, Grazia Arpino, Carmine De Angelis, Mario Giuliano

  Manuscript writing: All authors

  Final approval of manuscript: All authors

  Accountable for all aspects of the work: All authors


## AUTHORS' DISCLOSURES OF POTENTIAL CONFLICTS OF INTEREST
  The following represents disclosure information provided by authors of this manuscript. All relationships are considered compensated unless otherwise noted. Relationships are self-held unless noted. I = Immediate Family Member, Inst = My Institution. Relationships may not relate to the subject matter of this manuscript. For more information about ASCO's conflict of interest policy, please refer to www.asco.org/rwc or ascopubs.org/cci/author-center.

  Open Payments is a public database containing information reported by companies about payments made to US-licensed physicians (Open Payments).


## ACKNOWLEDGMENT
  We acknowledge Genny Paradiso for her support in managing the reporting of the tests, which provided an additional source to support the confirmation of our pre- and post-test decision data.

  We acknowledge Domenico Ciuonzo from the Department of Electrical Engineering and Information Technologies (DIETI) of the University of Naples Federico II for the support in conducting the error analysis.