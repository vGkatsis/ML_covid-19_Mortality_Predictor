# Prediction Of Deaths Caused By COVID-19

## Regression Models

Experiments have been conducted using a variety of different regression algorithms in order to find the one that bests fits
our data. These are:

<ul>
<li> Linear Regression </li>
<li> Lasso Regression </li>
<li> Ridge Regression </li>
<li> Elastic Net </li>
<li> Decision Tree </li>
<li> Suport Vector Machine </li>
</ul>

Each one has its own advantages and disadvantages and hence responds defferently to the requirements of this project.
</br>The effectiveness of each algorithm is furthere discussed in the Experiments section.

## Metrics

The metrics choosen for measuring each models performane are:

<ul>
<li>R<sup>2</sup></li>
<li>Mean Absolute Error</li>
<li>Mean Squared Error</li>
<li>Rooted Mean Squared Error</li>
</ul>

## Running

All the code and experiments for this project are included in the **src.ipynb** file which is a jupyter notebook.
<br/>This notebook contains graphs created using the plotly python library which (for the time being) cannot be rendered by github.
So in order to view the whole code and examples the following **nbviewer** link is provided:
[src.ipynb](https://nbviewer.jupyter.org/github/vGkatsis/Prediction_Of_Number_Of_Deaths_Caused_By_COVID-19/blob/devel/src.ipynb?flush_cache=true)

## Data
Data for this project are taken from Our World in Data:
> Hasell, J., Mathieu, E., Beltekian, D. _et al._ A cross-country database of COVID-19 testing. _Sci Data_ **7**, 345 (2020). [https://doi.org/10.1038/s41597-020-00688-8](https://doi.org/10.1038/s41597-020-00688-8)

All the pre-processing has been done using the data in **.csv** form. The database is updated in a daily bases. The version used fot this project, is the one that was public until January the 31st 2021.