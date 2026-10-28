# SAMPDI-3D: predicting the effects of protein and DNA mutations on protein–DNA interactions


## Motivation
  Mutations that alter protein–DNA interactions may be pathogenic and cause diseases. Therefore, it is extremely important to quantify the effect of mutations on protein–DNA binding free energy to reveal the molecular origin of diseases and to assist the development of treatments. Although several methods that predict the change of protein–DNA binding affinity upon mutations in the binding protein were developed, the effect of DNA mutations was not considered yet.


## Results
  Here, we report a new version of SAMPDI, the SAMPDI-3D, which is a gradient boosting decision tree machine learning method to predict the change of the protein–DNA binding free energy caused by mutations in both the binding protein and the bases of the corresponding DNA. The method is shown to achieve Pearson correlation coefficient of 0.76 and 0.80 in a benchmarking test against experimentally determined change of the binding free energy caused by mutations in the binding protein or DNA, respectively. Furthermore, three datasets collected from literature were used to do blind benchmark for SAMPDI-3D and it is shown that it outperforms all existing state-of-the-art methods. The method is very fast allowing for genome-scale investigations.


## Availabilityand implementation
  It is available as a web server and a stand-code at http://compbio.clemson.edu/SAMPDI-3D/.


## Supplementary information
  Supplementary data are available at Bioinformatics online.