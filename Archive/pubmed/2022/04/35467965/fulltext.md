# Development of a Machine Learning Model Using Limited Features to Predict 6-Month Mortality at Treatment Decision Points for Patients With Advanced Solid Tumors


## METHODS
  We identified a cohort of adults with advanced solid tumors receiving care at a major cancer center from 2014 to 2020. We identified TDPs for new lines of therapy (LoTs) and confirmed mortality at 6 months after a TDP. Using extreme gradient boosting, ML models were developed, which used or derived features from a limited set of electronic health record data considering the literature, clinical relevance, variability, availability, and predictive importance using Shapley additive explanations scores. We predicted and observed 6-month mortality after a TDP and assessed a risk stratification strategy with different risk thresholds to support communication of chance of survival.


## RESULTS
  Four thousand one hundred ninety-two patients were included. Patients had 7,056 TDPs, for which the 6-month mortality increased from 17.9% to 46.7% after starting first to sixth LoT, respectively. On the basis of internal validation, models using both 111 (Full) or 45 (Limited-45) features accurately predicted 6-month mortality (area under the curve ≥ 0.80). Using a 0.3 risk threshold in the Limited-45 model, the observed 6-month survival was 34% (95% CI, 28 to 40) versus 81% (95% CI, 81 to 82) among those classified with low or higher chance of survival, respectively. The positive predictive value of the Limited-45 model was 0.66 (95% CI, 0.60 to 0.72).


## CONCLUSION
  We developed and validated a ML model using a limited set of 45 features readily derived from electronic health record data to predict 6-month prognosis in patients with advanced solid tumors. The model output may support shared decision making as patients consider the next LoT.


## INTRODUCTION
  Despite new therapeutic options, many patients with advanced cancer transition to a phase of terminal illness in which intensive treatments might have limited ability to extend life or restore health.1,2 This final 6 months preceding death is generally referred to as the end of life (EOL).3 At EOL, patients with advanced cancer should have access to high-value, compassionate, and evidence-based care consistent with their wishes.4,5 Despite the desire for a good death and eligibility for hospice when the life expectancy is less than 6 months,6 patients may receive intensive treatments at EOL.1,2,7-9 When clinicians accurately estimate prognosis, they refer patients earlier for palliative care and hospice care.10 Similarly, when patients have an accurate perception of prognosis, they are less likely to choose aggressive care at EOL11,12 and more likely to receive care consistent with their preferences.13

  Delivering high-value care for patients with advanced cancer requires that clinicians accurately communicate prognosis during treatment discussions, and patients express their values and goals of care.14 Despite the existence of prognostic tools,9,15 clinicians often overestimate survival,16 which may affect decision making about treatment options.5,17 In addition, prognostic tools developed before 2018 focused on patients who were hospitalized, receiving hospice care, or within a few weeks or months of death, potentially suboptimal time frames for treatment decision making.18-21

  Advances in computational capacity and electronic health records (EHRs) provide opportunities for machine learning (ML) to deliver data-driven mortality predictions linked to cancer care decisions. Recent publications describe accurate ML-based approaches for predicting 6-month mortality for patients with cancer.22-26 However, their relevance, scalability, and interpretability may be limited by inclusion of patients before diagnosis with advanced cancer, the hundreds of features used, or positive predictive values (PPVs) not reported or < 54%.22-26 One model has been implemented as a stand-alone application,27 but requires manual data entry and is based on pre-2015 data.22 These tools appear to be designed to influence clinician behavior and are not patient-facing. To optimize advance planning and palliative care, prognostic tools should be available during treatment discussions.

  At the Huntsman Cancer Institute (HCI), a team with expertise in oncology (A.B. and J.M.), informatics (C.S. and M.N.), and data science (G.C., M.N., and S.Y.) developed a Use Case to describe goals, stakeholders, data, and tasks for integrating a prognostic tool into the advanced cancer care workflow.28 From these discussions, the team sought to develop an automated, EHR-integrated tool using a limited feature set to accurately predict 6-month prognosis and support shared decision making as clinicians and patients with any advanced solid tumor consider a new line of therapy (LoT). Our objective was to (1) develop and validate a ML model that predicts 6-month mortality for patients with an advanced solid tumor considering a new LoT, using only EHR data available before starting therapy, and (2) risk stratify patients to support usability of the output for clinicians and patients.


## METHODS

### Data Source
  Data were obtained in February 2021 from the University of Utah Health (UHealth) enterprise data warehouse, which includes data from the (1) Epic EHR implemented in all inpatient or outpatient UHealth and HCI care settings, (2) HCI hospital–based cancer registry (HCI-CR),29 and (3) Utah Vital Records. To identify the study population, we used HCI-CR29 and EHR data. To assign a deceased outcome, we queried EHR or vital records data for a death date; if not available, we queried HCI-CR. To assign an alive outcome, we queried EHR data for patient measurements. All predictive features were based on EHR data, including International Classification of Diseases (ICD) codes used to assign metastases.


### Study Population and Treatment Decision Points
  Our study cohort concerned patients with advanced solid tumors who received care within UHealth enterprise. Advanced solid tumor was defined as malignant brain or nervous system cancer or any other solid tumor with metastases (Data Supplement). The index date was defined as the first date when an advanced solid tumor diagnosis was recorded in EHR data. Eligible patients had (1) no history of hematologic malignancy or bone marrow transplant; (2) two or more visits with a UHealth medical oncologist from 6 months before the index date or later; (3) age 18 years or older on the index date; and (4) an index date between June 1, 2014, and June 1, 2020.

  To determine the final study population with at least one LoT with a treatment decision point (TDP), additional preprocessing and inclusion criteria were applied. To identify a LoT and treatment start date, we extracted data from 12 months before the patient's index date through November 30, 2020, allowing for a minimum follow-up of 6 months. Any anticancer therapy (chemotherapy, biologics, targeted therapy, immunotherapy, and hormonal therapy) entered into EHR treatment plans was defined as an eligible LoT, consistent with a recently published framework.30 Injectable and selected oral hormonal therapies for prostate and breast cancer were not included. Finally, to define a TDP, we identified a visit within 30 days before the LoT start date with values for required features. A description of the preprocessing strategy and a flow diagram illustrating the study population are available (Data Supplement).


### Features
  Initially, the team reviewed tools and publications concerning cancer prognostication, enumerated potential prognostic features mentioned, and identified additional potentially clinically relevant features (Data Supplement). Next, clinical experts (A.B. and J.M.) selected a subset deemed clinically important and available in EHR data and described logic to operationalize features. To assess usefulness, we investigated feature availability and variability; then, evaluated feature logic and importance during iterative model development. On the basis of this analysis, we identified 111 features to be operationalized for each TDP (Table 1). Treated cancer type was determined using ICD codes reported in the EHR treatment plan data and classified into 15 categories (Data Supplement). The presence of metastasis (seven categories) was determined using ICD codes in encounter data. Most features were directly used, whereas others were derived using logic. For example, LoTs were counted after the index date and included as a counter variable. Time to next treatment (TTNT), the difference between current and previous treatment start dates, is a surrogate end point for real-world progression-free survival31 and only calculated for a second or later LoT. Features related to history of encounters (eg, emergency visits, inpatient visits, and inpatient length of stay), radiation therapy, and blood transfusions were summarized for defined months before TDP.23,32 Binary variables were used to create features for palliative care history (eg, flag if an order was recorded in the EHR ever before or within three months before the TDP). Order dates, encounter types, and logic were used to derive features concerning hospice and advance directives. Laboratory values, body mass index (BMI), and weight were augmented with their 3-month percent change if data within 2.5-3.5 months before the TDP were available.33 We arrived at 111 features to include in the full prediction model (Table 1). No imputation of missing data was performed. Data after the TDP and the primary outcome were not included.


### Outcome
  The primary outcome was 6-month mortality after a TDP. An outcome of deceased was assigned if a death date was documented within 6 months after a TDP. For patients with no recorded death date, an outcome status of alive was assigned if at least one of the following data points was available during a visit 6 months or longer after the TDP: BMI, diagnoses, laboratory measurement, patient performance score, or length of stay.


### Sample Size
  Patients might have had multiple TDPs, and each TDP was an independent observation. Use of multiple observations per patient is appropriate for prognostic model development.34,35 When performing analyses by cancer type and LoT, we required at least two observations for each outcome (deceased or alive) to ensure that the algorithm could be trained and evaluated for higher LoTs when data were scarce.


### Machine Learning Algorithm
  We used the extreme gradient boosting algorithm (xgb)36 for three reasons. First, a previous relevant publication compared six ML strategies and demonstrated highest performance using xgb, even with missing values.22 Second, xgb was used in four recent publications for a similar context.23-25,37 Third, the Shapley additive explanations (SHAP)38 can be used to identify the importance of features when aggregating individual predictions across the population, thus allowing for selection of features for a limited model to improve explainability for users of a future tool.

  We used repeated Monte Carlo record-wise cross-validation simulations34,35,39 to train and evaluate the classifier. TDPs were randomly split accounting for cancer type, LoT, and 6-month mortality: 70% of observations were used to train and 30% were used to evaluate the model. Optimized hyperparameters were determined as described in the Data Supplement.39


### Limited Models
  To develop a model with a limited set of features, we used an iterative strategy. While operationalizing features for the full model, we ranked features by SHAP score and requested clinical experts (A.B. and J.M.) to select 25-30 features on the basis of clinical importance, predictive impact, and expected availability across health care settings. Generally, features with scores above 0.1 were selected. Next, we created Limited models with and without features for cancer type and metastases (n = 45 v 23 features, respectively). Although these features were not highly ranked, they may be expected by users to be included.


### Assessment of Performance, Risk Thresholds, and Risk Stratification
  We used repeated Monte Carlo cross-validations to assess the mean and 95% CI for each performance measure.39,40 Since PPV, sensitivity, negative predictive value (NPV), and specificity depend on a risk threshold (ie, decision boundary) for assigning patients to either low or higher survival chance group at six months, we used clinical input and a data-driven approach to determine a clinically relevant risk threshold, rather than the default of 0.50. We calculated model performance and observed survival using incremental risk thresholds from 0.05 to 0.95.

  Using the Limited-45 model and defined risk threshold of 0.30, patients were classified by chance of survival (low or higher). We then calculated mean observed 6-month survival, overall and stratified by LoT, cancer type, predicted chance of survival, and quality metrics such as referrals for palliative care or hospice and rates of hospitalization.


### Statistical Analysis
  We used descriptive analyses to summarize population characteristics and quality metrics. Delong's method was used to compare area under the curve (AUC) of different prediction models.41 We adjusted P values using Bonferroni correction.

  This project was approved by the University of Utah and Hitachi Institutional Review Boards and followed Transparent Reporting of a Multivariable Prediction Model for Individual Prognosis or Diagnosis guidelines.42


## RESULTS
  Among the 7,690 potentially eligible patients identified in the EHR, 5,167 (67%) had treatment data and 4,192 (54.5%) met the inclusion criteria for the final study cohort (Data Supplement). These 4,192 patients had a total of 7,056 TDPs distributed across the first to sixth LoTs (Table 2). The most common cancer types were breast (13.1%), lung (11.4%), melanoma (11.2%), colon, rectum and small bowel (10.1%), and prostate (8.9%). The observed 6-month mortality after a TDP increased incrementally from 17.9% after the first line to 46% after the sixth LoT. Additional detailed patient characteristics and observed 6-month survival stratified by cancer type at each LoT are available (Data Supplement).

  Among the 111 features included in the full model, albumin was most predictive (SHAP score 0.81), followed by selected laboratory values, pain score, palliative care history, time since index date, TTNT, and age. Cancer type, metastasis, MEWS score, Charlson comorbidity index, encounter history, sex, and race had lower importance (Table 1).

  The subset of predictive and clinically relevant features selected by clinical experts resulted in two models: Limited-45 (with 45 features) and Limited-23 (with 23 features excluding types of cancers and metastases). The top 20 features for both models in descending order were as follows: albumin, lymphocyte %, pain score, hemoglobin, alkaline phosphatase, TTNT, time since index date, sodium, lactate dehydrogenase, BMI, age, 3-month % weight change, calcium, platelets, monocyte %, line of therapy (LoT), bilirubin, 3-month % platelets change, 3-month % hemoglobin change, white blood count (Data Supplement).


### Model Performance
  For predicting 6-month mortality at any TDP aggregating across LoTs using internal validation, the full model had an AUC of 0.81 (95% CI, 0.79 to 0.82), which was not significantly different from the Limited-45 model (AUC: 0.80 [95% CI, 0.78 to 0.81]; Table 3). The Limited-23 model was accurate (AUC: 0.78 [95% CI, 0.76 to 0.80]) despite using no cancer features, but the AUC differed significantly from the other two models (P < .05).

  To define a risk threshold, the Limited-45 model was used. PPV, sensitivity, NPV, and specificity varied across risk thresholds, as shown in Figure 1 and the Data Supplement. Similarly, the observed 6-month survival increased by 3% with each 10% change in risk threshold (eg, from 27% to 39% when the risk threshold was adjusted from < 0.10 to < 0.50; Fig 2A). Using a risk threshold of 0.30, only one in 3 (33%) patients who were classified as having low chance of survival had in fact survived 6 months, matching the mental model of clinical experts on the team. In addition, PPV was higher when using a threshold of 0.30 compared with the standard threshold of 0.50. Thus, given the priority for accurate prognosis over sensitivity, the risk threshold of 0.30 was used for all model performance evaluations.

  Using the selected risk threshold of 0.30, predictive performance metrics varied by LoTs and were similar for all models (Table 3). PPV and sensitivity were lowest when prognosticating for first LoT but increased with each subsequent line. NPV and specificity were high for all models and subgroups.


### Assessment of Risk Stratification Compared With Observed Outcomes
  Using the Limited-45 model (and 0.30 risk threshold), on aggregate, the observed 6-month survival among patients predicted with low chance of survival (33.6%) was less than half of that observed among patients predicted with higher chance of survival (81.1%; Fig 2B and Table 4). The proportion of patients classified with a low chance of survival increased with each successive LoT (from 5% for the first LoT to 10%, 16%, 19% to 25% for the fifth LoT); however, the observed 6-month survival was similar regardless of LoT (range: 26% to 37%; Table 4).

  Among 7,056 TDPs experienced by our patient population, an average of 8.5% were flagged with low chance of survival. Among those with low chance of survival, on average, 66% were deceased within 6 months (PPV = 66%). Of those patients predicted to have low chance of survival who died within 6 months of starting a new LoT, estimated quality metrics were suboptimal: an average of 15% were referred for hospice care, 51% were referred for palliative care, and 60% were hospitalized between the TDP and death.


## DISCUSSION
  The observed 6-month mortality rate for our cohort of patients with advanced solid tumors increased incrementally from 18% after starting the first LoT to 47% after starting the sixth line, demonstrating the need for improved prediction of mortality when considering new LoTs. We developed an accurate prognosis model that relied on a limited set of features from EHR data available at a patient's visit to discuss treatment options. Our unique approach for feature selection using SHAP resulted in a set of most influential features, including albumin, consistent with those identified by others.22-24 However, we identified additional predictive features that could be operationalized using EHR data, including treatment response time (using TTNT as a proxy), palliative care consultation, and pain scores over time. Most importantly, the predictive performance of the model was similar with or without cancer-related features and continued to have a PPV of 60% or higher regardless of the model or LoT. This suggests that patients with advanced solid tumors may converge to a common pathway at EOL regardless of the cancer type, at which point patient-specific factors unrelated to cancer are most important.

  We acknowledge that previously reported ML models have similar predictive capabilities; however, these models required hundreds of data points, potentially limiting scalability and interpretability.23,24 Our Limited-45 model achieved equivalent and accurate performance with only 45 readily derivable features. The 45 features may be implementable using the FHIR standard,43 maximizing portability, and displayed in a user interface to support interpretability. Transparent display of input values may allow users to manually update values to recalculate prognosis, if needed. These factors may improve presentation of objective data used by providers to discuss the difficult subject of prognosis with their patients.

  We selected a decision threshold consistent with how clinicians explain low or higher chance of survival. Regardless of LoT, observed 6-month survival approximated one third for every subset assigned to low chance of survival, illustrating model consistency discrimination. In addition, these patients had suboptimal EOL quality metrics.44 Automating identification of at-risk patients could improve care.

  Our risk stratification was designed to be patient- and provider-facing to support shared decision making. We are currently developing a user interface for clinicians and patients to visualize model inputs and observed survival among patients with similar risk. A clinical trial assessing the effect on shared decision making and EOL quality metrics is planned.

  Our study has limitations. The model was trained on patients who underwent therapy because TDPs were defined using treatment data. Therefore, the model can only make predictions on the basis of the assumption that anticancer therapy will be continued. The model was trained on data from one institution and may not reflect care patterns in other settings or for minority populations.45 Furthermore, LoTs were only calculated on the basis of treatment data available in the EHR. Our limited sample size, particularly at higher LoTs, rendered predictions with higher uncertainty, but reporting 95% CIs improved transparency. Our model was only validated internally; external validation will be necessary. Finally, although pain score was a highly predictive feature, these data are subjective and inconsistently recorded. Despite limitations, our approach is expected to be scalable, interpretable, and clinically relevant. A prospective evaluation and deployment at other health systems is needed to validate these assumptions.

  In conclusion, we developed and validated a ML model using a limited set of 45 features readily derived from EHR data to predict 6-month prognosis. Risk stratification using this model may be used to support shared decision making as patients with advanced cancer consider the next LoT.


## AUTHOR CONTRIBUTIONS
  Conception and design: George Chalkidis, Jordan McPherson, Anna Beck, Shuntaro Yui, Catherine Staes

  Collection and assembly of data: George Chalkidis, Jordan McPherson, Anna Beck, Michael Newman, Catherine Staes

  Data analysis and interpretation: George Chalkidis, Jordan McPherson, Anna Beck, Catherine Staes

  Manuscript writing: All authors

  Final approval of manuscript: All authors

  Accountable for all aspects of the work: All authors


## AUTHORS' DISCLOSURES OF POTENTIAL CONFLICTS OF INTEREST
  The following represents disclosure information provided by authors of this manuscript. All relationships are considered compensated unless otherwise noted. Relationships are self-held unless noted. I = Immediate Family Member, Inst = My Institution. Relationships may not relate to the subject matter of this manuscript. For more information about ASCO's conflict of interest policy, please refer to www.asco.org/rwc or ascopubs.org/cci/author-center.

  Open Payments is a public database containing information reported by companies about payments made to US-licensed physicians (Open Payments).


## ACKNOWLEDGMENT
  We acknowledge support for this work from Kensaku Kawamoto, MD, PhD, MHS, Associate Chief Medical Information Officer, University of Utah Health, and Andrew Post, MD, PhD, Research Informatics Director, Huntsman Cancer Institute.