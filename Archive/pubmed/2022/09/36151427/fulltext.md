# Prediction of TTF-1 expression in non-small-cell lung cancer using machine learning-based radiomics


## Purpose
  To explore the feasibility and performance of machine learning-based radiomics models in predicting thyroid transcription factor-1 (TTF-1) expression in non-small cell lung cancer (NSCLC).


## Methods
  A total of 227 NSCLC patients were included in this retrospective study and divided into the training set and test set with a ratio of 8:2 randomly. Lung tumors on CT images were semi-automatic segmented utilizing 3D Slicer. Radiomic features quantifying tumor intensity, shape, texture, and transformed wavelet were extracted using a Python toolkit. Variance threshold (VT), principal component analysis (PCA), and least absolute shrinkage selection operator (LASSO) were used to reduce features; logistic regression (LR), random forest (RF), and support vector machine (SVM) were used to develop classifier, respectively. The performance of the models was evaluated by areas under the curves (AUC) of receiver operating characteristic (ROC) curves. Different models were compared by the Delong test to determine the optimal algorithms.


## Results
  Total 1968 radiomic features were extracted from the lung tumors images, and then 13, 15, and 13 stable features were selected by VT, PCA, and LASSO, respectively. Each classifier could discriminate against the TTF-1-positive groups with average AUC ranging from 0.601 to 0.784 in the training set. Among the models, three models constructed by the LASSO method showed satisfactory performance in the test set with AUC ranging from 0.715 to 0.787. The Delong test showed no significant difference between the LASSO models (P > 0.05).


## Conclusion
  Machine learning-based radiomics model could predict the expression of TTF-1 in NSCLC patients.


## Supplementary Information
  The online version contains supplementary material available at 10.1007/s00432-022-04357-8.