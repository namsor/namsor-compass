# namsor-compass
NamSor backtest on COMPAS database using [Aequitas](https://github.com/dssg/aequitas), with their [example analysis of COMPAS](https://github.com/dssg/aequitas/blob/master/docs/source/examples/compas_demo.ipynb) as a reference. 

## 1 Data Preparation
To Aequitas' [pre-prepared COMPAS data](https://github.com/dssg/aequitas/blob/master/examples/data/compas_for_aequitas.csv) we add predictions for name gender and origin made as made by NamSor API.

## 2 COMPAS Analysis
We repeat Aequitas' COMPAS analysis using not the original values but the predictions made by NamSor

## 3 Fairness Analysis
How good are NamSor's predictions? And are they equally good for all groups of people? How fair is NamSor? 

To answer these questions we calculate Fairness Measures with the help of Aequitas. Aequitas can calculate the following metrics for groups, where a group is a specific combination of vectors (eg. race, sex):

* True Positive Rate 'tpr'
* True Negative Rate 'tnr'
* False Omission Rate 'for'
* False Discovery Rate 'fdr'
* False Positive Rate 'fpr'
* False Negative Rate 'fnr'
* Negative Predictive Value 'npv'
* Precision 'precision'
* Predicted Positive Ratio 'ppr'
* Predicted Positive Ratio 'pprev'
* Group Prevalence 'prev'

Based on these metrics Aequitas can calculate the fairness between groups and a reference group. An example for a reference group could be: race=caucasian, sex=male. Or, one could have Aequitas automatically select the biggest or smallest group from the data set.

The following fairness conditions are available from Aequitas:
* True Positive Rate Parity 'TPR Parity'
* True Negative Rate Parity 'TNR Parity'
* False Omission Rate Parity 'FOR Parity'
* False Discovery Rate Parity 'FDR Parity'
* False Positive Rate Parity 'FPR Parity'
* False Negative Rate Parity	'FNR Parity'
* Negative Predictive Value Parity 'NPV Parity'
* Precision Parity	'Precision Parity'
* Predicted Positive Ratio Parity	'Statistical Parity'
* Predicted Positive Ratio Parity	'Impact Parity'
* Type I Parity: Fairness in both FDR Parity and FPR Parity
* Type II Parity: Fairness in both FOR Parity and FNR Parity
* Equalized Odds: Fairness in both FPR Parity and TPR Parity
* Unsupervised Fairness: Fairness in both Statistical Parity and Impact Parity
* Supervised Fairness: Fairness in both Type I and Type II Parity
* Overall Fairness: Fairness across all parities for all attributes

# 4 Visualization
...
