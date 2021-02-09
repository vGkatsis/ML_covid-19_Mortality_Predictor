# Prediction Of Deaths Caused By COVID-19

[TOC]

## Overview

This project is an attempt to predict the number of deaths caused by covid-19 in a  country, using simple Machine Learning models. The training data consist of facts about the country's  course throughout each month of the pandemic  (e.g. monthly cases and monthly deaths) as well as country specific data such as the number of hospital beds per thousand people, the percentage of smokers etc.                                                                                                     Models are trained with the above mentioned data from the period  01/01/2020 - 01/01/2021. Then for each target country the model is provided with the same data from the same period  and makes predictions about the number of deaths in January 2021.                                                                                            The problem described above is a quite complex one since it is a multi-factor problem. The data used in this implementation describe only a part of it. Normally factors such as epidemiological data, economic decisions, local culture and customs  would be taken under consideration. Therefor it is expected that the experimental results will not be precise. The ultimate goal of this project is to find out what level of accuracy we can achieve in our predictions using only simple machine learning tools.

## Running

All the code and experiments for this project are included in the **src.ipynb** file which is a jupyter notebook.                                                                                   This notebook contains graphs created using the plotly python library which (for the time being) cannot be rendered by git-hub.
So in order to view the whole code and examples the following **nbviewer** link is provided:
[src.ipynb](https://nbviewer.jupyter.org/github/vGkatsis/Prediction_Of_Number_Of_Deaths_Caused_By_COVID-19/blob/devel/src.ipynb?flush_cache=true)

## Regression Models

Experiments have been conducted using a variety of different regression algorithms in order to find the one that bests fits
our data. These are:

<ul>
<li> Linear Regression </li>
<li> Lasso Regression </li>
<li> Ridge Regression </li>
<li> Elastic Net </li>
<li> Suport Vector Machine </li>
</ul>

Each one has its own advantages and disadvantages and hence responds differently to the requirements of this project.

## Metrics

The metrics chosen for measuring each models performance are:

<ul>
<li>R<sup>2</sup></li>
<li>Mean Absolute Error</li>
<li>Mean Squared Error</li>
<li>Rooted Mean Squared Error</li>
</ul>
## Data
Data for this project are taken from Our World in Data:
> Hasell, J., Mathieu, E., Beltekian, D. _et al._ A cross-country database of COVID-19 testing. _Sci Data_ **7**, 345 (2020). [https://doi.org/10.1038/s41597-020-00688-8](https://doi.org/10.1038/s41597-020-00688-8)

All the pre-processing has been done using the data in **.csv** form. The database is updated in a daily bases. The version used for this project, is the one that was public until January the 31st 2021.

## Experiments

The experiments phase can be divided into four steps.

1. Feature extraction.
2. Feature selection.
3. Model tuning.
4. Model evaluation.

In step number one, data are processed so that they will come to the form needed by the problem. For example the number of cases and the number of deaths for each country and for each month must be aggregated.

In step number two the feature are visualized in contrast to the  total number of deaths, in order to decide which features will be those that will be used in the training phase.

Step number three is about finding the best parameter values so that the models can achieve best performance. This is achieved in an iterative manner. Starting from a base value for each parameter we create the model and evaluate its performance using a k-fold validation process as well as a validation dataset. While the mean absolute error(MAE) for the predictions for both the k-fold process and the validation dataset decreases the base value is augmented. So the final value is the one that minimizes the MAE in both cases.

Step number four is the evaluation of the models. For this process the metrics described in the above section are used. Each one of them gives different information about the models performance.

- R<sup>2</sup>  describes how well the selected features explain the depended variable.
- Mean Absolute Error (MAE) represents the positive/negative prediction error in problem related units(in this case monthly deaths).
- Mean Squared Error (MSE)  has the same meaning with MAE but it gives a higher penalty to bigger errors.
- Rooted Mean Squared Error (RMSE) gives an approximation of the MSE counted in problem units.

The table below show the experimental results for each algorithm in the testing dataset.

|               | Linear Regression | Lasso Regression | Ridge Regression | Elastic Net |    SVM    |
| :-----------: | :---------------: | :--------------: | :--------------: | :---------: | :-------: |
| R<sup>2</sup> |       0.76        |       0.76       |       0.82       |    0.75     |   -0.34   |
|      MAE      |      2756.4       |       2761       |      1463.2      |   2837.6    |  5508.6   |
|      MSE      |     20662752      |     20737069     |     26953354     |  21816409   | 117010907 |
|     RMSE      |      4545.63      |      4556.8      |       5191       |    4670     |   10817   |

It is clear now that none of this models consists a feasible solution to the problem. Ridge regression has given the best score in terms of both variable explanation and error approximation but still the high values of MSE and RMSE scores indicate that this model can give errors much larger than the others.