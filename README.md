# Diabetic Hospital Readmission Classification Model

author: Alison Park

![diabetes](images/diabetes.jpeg)

<sup>(source. https://www.google.com/url?sa=i&url=https%3A%2F%2Fnews.keckmedicine.org%2Fclinical-trial-investigating-innovative-way-to-control-type-2-diabetes%2F&psig=AOvVaw3guxc0dr4fM2r_Xn9TZ9lx&ust=1685658625681000&source=images&cd=vfe&ved=0CBIQjhxqFwoTCKDy6O7NoP8CFQAAAAAdAAAAABAJ)</sup>

## Overview
The objective was to develop a classification model to help hospitals improve 


## Business Understanding
Hospital readmission for diabetic patients is a significant business problem with potential implications for patient outcomes and healthcare costs. 

1. Impact on Patient Health: Hospital readmission for diabetes is associated with worse long-term outcomes for patients. Poorly controlled diabetes during the initial hospitalization can lead to complications and disease progression, including cardiovascular events, kidney problems, infections, and diabetic ketoacidosis. Inadequate management and fragmented care transitions contribute to gaps in follow-up care, medication adherence, and lifestyle management, further impacting patient health and well-being.

2. Healthcare Resource Utilization: Hospital readmissions for diabetes impose a substantial burden on the healthcare system. Repeated hospitalizations increase healthcare utilization and costs, straining healthcare resources. Additionally, fragmented care and lack of continuity disrupt the establishment of consistent and effective care plans, hindering disease management and potentially leading to avoidable readmissions.

3. Need for Comprehensive Solutions: Addressing hospital readmission for diabetic patients requires comprehensive solutions. Improving care coordination, patient education, medication management, discharge planning, and post-discharge follow-up are essential components. By focusing on these areas, healthcare providers can promote continuity of care, reduce readmission rates, improve patient outcomes, and mitigate the financial impact on the healthcare system.

In summary, hospital readmission for diabetic patients presents a significant business problem due to its impact on patient health outcomes and healthcare resource utilization. A comprehensive approach that addresses care coordination and continuity is crucial for reducing readmission rates, improving patient outcomes, and optimizing healthcare costs.

The classification model created in this project will be able to shed light on specific features included in the model that have the highest effect on readmission which hospitals can use to streamline their policies and methodologies in care coordination.


## Data Understanding

The data set represents 10 years (1999-2008) of clinical care at 130 US hospitals and integrated delivery networks. It includes over 50 features representing patient and hospital outcomes. Information was extracted from the database for encounters that satisfied the following criteria.

1. It is an inpatient encounter (a hospital admission).
2. It is a diabetic encounter, that is, one during which any kind of diabetes was entered to the system as a diagnosis.
3. The length of stay was at least 1 day and at most 14 days.
4. Laboratory tests were performed during the encounter.
5. Medications were administered during the encounter.

The target for this classification model was `readmission` and it originally started off as multiclass (no, >30, <30) but for this model, we focused on the binary problem.

There are information on the features in IDs_mapping.csv as well as the paper cited below. The IDs_mapping.csv is specifically used when binning the three features (admission_id, discharge_disposition_id, as well as admission_source).

(Beata Strack, Jonathan P. DeShazo, Chris Gennings, Juan L. Olmo, Sebastian Ventura, Krzysztof J. Cios, and John N. Clore, “Impact of HbA1c Measurement on Hospital Readmission Rates: Analysis of 70,000 Clinical Database Patient Records,” BioMed Research International, vol. 2014, Article ID 781670, 11 pages, 2014.)



## Methods

This project uses machine learning tools to make different types of models and gridsearch for hyperparameters to optimize the model.

The evaluation metric was the F1 score. The F1 score is a commonly used evaluation metric in classification tasks. It combines two important metrics: precision and recall.

Precision measures the model's ability to correctly identify positive cases (hospital readmissions) out of all instances predicted as positive. In the context of hospital readmission, precision represents the proportion of patients predicted as readmitted who are actually readmitted. A high precision indicates that when the model predicts a patient will be readmitted, it is likely to be correct.

Recall, on the other hand, measures the model's ability to correctly identify all positive cases (actual hospital readmissions) out of the total actual positive cases. In the context of hospital readmission, recall represents the proportion of actual readmissions that the model correctly identifies. A high recall indicates that the model is effective at capturing a significant portion of the readmissions.

The F1 score combines precision and recall into a single metric, providing a balanced measure of the model's performance. It considers both false positives and false negatives, which is important in healthcare applications where the consequences of misclassification can be significant. By optimizing for the F1 score, we aim to strike a balance between identifying as many true positives (correctly predicting readmissions) as possible while minimizing false positives and false negatives.

In summary, the F1 score is a useful evaluation metric in the context of hospital readmission prediction because it considers both precision and recall, providing a balanced assessment of the model's ability to identify readmissions while minimizing false predictions.


## Final Model

We decided to use the second grid search for the decision tree model as the final model. This model had a f1 score of 0.5603. 

![Dummy Model vs Final Model](images/dummy_vs_final.png)

This shows the dummy model, model that purely guesses the most frequent (no readmission), compared to the final model. As you can both the f1 score and ROC AUC scores increased with our final model which means that this model will be more precise when predicing which patients are likely to get readmitted.


## Interpretation of Model

![Top 10 key features](images/top_10_features.png)

This graph shows the top 10 key features that is important to predict which patients will get the seasonal flu vaccine. I will be highlighting doctor's recommendation and age group (graphs are up in EDA section).

![Number of Emergency](images/number_emergency.png)

For those who got a doctor's recommendation, 73.8% of the patients received a vaccine. This is a drastic difference to only 34.6% of patients receiving the vaccine when they did not get a doctor's recommendation. It seems to be that a doctor's recommendation is important in a patient's decision to receive the flu vaccine.

![Num meds](images/num_meds.png)

Age group 65+ have the highest vaccination rates. The bottom three age groups have more people that have not received the vaccine than those who did. This might be due to health policies already set in place for the elderly since they are at a higher-risk of getting sick. Since herd immunity is important, it is imperative to target the younger age groups as well to increase the overall effectivness of the vaccine.


## Conclusions



## Next Steps



To improve the robustness of our model, we recommend exploring alternative machine learning algorithms such as XGBoost or conducting further grid searches on the random forest model to identify the optimal categorical model. This would enable us to identify more accurate features to target for future hospital policies.

Overall, the results of our study suggest that additional research is necessary to further refine the model's precision and predictive ability, and to ensure that it can be effectively applied in real-world settings.

## For Inquiries, Business Proposals, or Additional Information...

Our process is available in this [Jupyter Notebook](./final_notebook.ipynb) or abbreviated in this 
[presentation](./DIABETES_Hospital Readmission_AlisonPark_ppt.pdf).

We can be contacted via email at [alisonsjpark@gmail.com \(Alison\)](mailto:alisonsjpark@gmail.com) 


## Repository structure

```
├── data
│   ├── submission_format.csv
│   ├── test_set_features.csv
│   ├── training_set_features.csv
│   └── training_set_label.csv
├── images
│   ├── age.png
│   ├── doctor_rec.png
│   ├── dummy_vs_final.png
│   ├── top_10_features.png
│   └── vaccine.jpeg
├── .gitignore
├── final_notebook.ipynb
├── LICENSE
├── DIABETES_Hospital Readmission_AlisonPark_ppt.pdf
├── README.md
└── 
```


