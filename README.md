[NamSor](https://v2.namsor.com/NamSorAPIv2/apidoc.html) fairness backtest on COMPAS database using [Aequitas](https://github.com/dssg/aequitas), with their [example analysis of COMPAS](https://github.com/dssg/aequitas/blob/master/docs/source/examples/compas_demo.ipynb) as a reference. 

## 1 COMPAS Analysis
Can a fairness audit of another tool work even if protected attributes like gender and ethnicity are NOT provided but we infer them using NamSor? For this experiment I repeat Aequitas' COMPAS analysis using not the original values but the predictions made by NamSor. For the data preparation I format the [original COMPAS data from ProPublica](https://github.com/propublica/compas-analysis/blob/master/compas-scores-two-years.csv) with [a script from Aequitas](https://github.com/dssg/aequitas/blob/master/examples/compas_data_for_aequitas.py) which I modified so it keeps first and last names. I add predictions for name gender and origin made as made by NamSor API. For using the NamSor Python SDK to get predictions for the gender and origin of names I oriented on what I did in my [Bachelor Thesis](https://github.com/LiFaytheGoblin/Gender-Equality-in-CS-Publications/blob/master/01_DataGatheringAndCleaning/03_Gender.ipynb).

For a critical review of ProPublica's original analysis see [Anthony et. al 2016](https://www.researchgate.net/publication/306032039_False_Positives_False_Negatives_and_False_Analyses_A_Rejoinder_to_Machine_Bias_There's_Software_Used_Across_the_Country_to_Predict_Future_Criminals_And_it's_Biased_Against_Blacks).

## 2 Fairness Audit
How good are NamSor's predictions for gender and ethnicity? And are they equally good for all groups of people? How fair is NamSor? To answer these questions I first need to prepare two data sets (using a modified script from 1.) and then calculate Fairness Measures with the help of Aequitas. 

Details on theoretical background, the fairness audit technology, method, results and discussion are made available in my report [Algorithmic Fairness from Theory to Practical Application. A Fairness Audit of NamSor’s Gender and Ethnicity Classification Algorithms.](https://github.com/namsor/namsor-compass/blob/master/algorithmic-fairness-fernsel-linda-2020.pdf) which I included in this repository.

## How to run this analysis on your computer
I developed with the following environment
* Python 3.7.3 installed
* Anaconda 1.7.2 installed with Jupyter Notebook
* [Aequitas 38.1](https://github.com/dssg/aequitas) downloaded
* [NamSor 2.0.9 SDK for Python](https://github.com/namsor/namsor-python-sdk2) downloaded (To use, get an API key for NamSor and safe it in a key.txt file the root folder of this repository. The gitignore file is set to ignore the key.txt file.)
