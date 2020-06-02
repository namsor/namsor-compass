# namsor-compass
[NamSor](https://v2.namsor.com/NamSorAPIv2/apidoc.html) backtest on COMPAS database using [Aequitas](https://github.com/dssg/aequitas), with their [example analysis of COMPAS](https://github.com/dssg/aequitas/blob/master/docs/source/examples/compas_demo.ipynb) as a reference. 

## 1 Data Preparation
I format ProPublica's [COMPAS data](https://github.com/propublica/compas-analysis/raw/master/compas-scores-two-years.csv) with [a script from Aequitas](https://github.com/dssg/aequitas/blob/master/examples/compas_data_for_aequitas.py) which I modified so it keeps first and last names. I add predictions for name gender and origin made as made by NamSor API. For using the NamSor Python SDK to get predictions for the gender and origin of names I oriented on what I did in my [Bachelor Thesis](https://github.com/LiFaytheGoblin/Gender-Equality-in-CS-Publications/blob/master/01_DataGatheringAndCleaning/03_Gender.ipynb).

## 2 COMPAS Analysis
I repeat Aequitas' COMPAS analysis using not the original values but the predictions made by NamSor

## 3 Fairness Analysis
How good are NamSor's predictions? And are they equally good for all groups of people? How fair is NamSor? 

To answer these questions I calculate Fairness Measures with the help of Aequitas. Aequitas can calculate the following metrics for groups, where a group is a specific combination of vectors (eg. race, sex):

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

## 4 Visualization
...


## How to run this analysis on your computer

I developed with the following environment
* Python 3.7.3 installed
* Anaconda 1.7.2 installed with Jupyter Notebook
* [Aequitas](https://github.com/dssg/aequitas) downloaded
* [NamSor 2.0.9 SDK for Python](https://github.com/namsor/namsor-python-sdk2) downloaded (To use, get an API key for NamSor and safe it in a key.txt file the root folder of this repository. The gitignore file is set to ignore the key.txt file.)