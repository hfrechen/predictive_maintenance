# Decision Trees and Random Forest in Predictive Maintenance Tasks

This repository shows the usage of Decision Trees and Random Forests in the prediction of a machine / process failures. The data preprocessing, EDA and modelling is done in multiple notebooks, which can be looked at here:

1. [Dataset preprocessing and EDA](https://nbviewer.org/github/hfrechen/predictive_maintenance/blob/main/notebooks/EDA.ipynb)
2. [Binary classification of machine failures - Decision Trees](https://nbviewer.org/github/hfrechen/predictive_maintenance/blob/main/notebooks/Modelling_Decision_Trees.ipynb)
3. [Binary classification of machine failures - Random Forest](https://nbviewer.org/github/hfrechen/predictive_maintenance/blob/main/notebooks/Modelling_Random_Forest.ipynb)

To run the notebooks install conda and create an environment:
> conda env create -f environment.yml
> 
> conda activate predictive_maintenance

## Data Set Description

Dataset is downloaded from the [UCI Machine Learning Repository](https://archive-beta.ics.uci.edu/ml/datasets/ai4i+2020+predictive+maintenance+dataset) and the following description is taken from the author's dataset description.

Since real predictive maintenance datasets are generally difficult to obtain and in particular difficult to publish, we present and provide a synthetic dataset that reflects real predictive maintenance encountered in industry to the best of our knowledge.

## Attribute Information

The dataset consists of 10 000 data points stored as rows with 14 features in columns

- UID: unique identifier ranging from 1 to 10000
- product ID: consisting of a letter L, M, or H for low (50% of all products), medium (30%) and high (20%) as product quality variants and a variant-specific serial number
- air temperature [K]: generated using a random walk process later normalized to a standard deviation of 2 K around 300 K
- process temperature [K]: generated using a random walk process normalized to a standard deviation of 1 K, added to the air temperature plus 10 K.
- rotational speed [rpm]: calculated from a power of 2860 W, overlaid with a normally distributed noise
- torque [Nm]: torque values are normally distributed around 40 Nm with a Ïƒ = 10 Nm and no negative values.
- tool wear [min]: The quality variants H/M/L add 5/3/2 minutes of tool wear to the used tool in the process.

In addition there are 'machine failure' labels that indicate, whether the machine has failed in this particular datapoint for any of the following failure modes are true. The machine failure consists of five independent failure modes

- tool wear failure (TWF): the tool will be replaced of fail at a randomly selected tool wear time between 200 and 240 mins (120 times in our dataset). At this point in time, the tool is replaced 69 times, and fails 51 times (randomly assigned).
- heat dissipation failure (HDF): heat dissipation causes a process failure, if the difference between air- and process temperature is below 8.6 K and the tool's rotational speed is below 1380 rpm. This is the case for 115 data points.
- power failure (PWF): the product of torque and rotational speed (in rad/s) equals the power required for the process. If this power is below 3500 W or above 9000 W, the process fails, which is the case 95 times in our dataset.
- overstrain failure (OSF): if the product of tool wear and torque exceeds 11,000 minNm for the L product variant (12,000 M, 13,000 H), the process fails due to overstrain. This is true for 98 datapoints.
- random failures (RNF): each process has a chance of 0.1 % to fail regardless of its process parameters. This is the case for only 5 datapoints, less than could be expected for 10,000 datapoints in our dataset.

If at least one of the above failure modes is true, the process fails and the 'machine failure' label is set to 1. It is therefore not transparent to the machine learning method, which of the failure modes has caused the process to fail

## Relevant Papers

[Stephan Matzka, 'Explainable Artificial Intelligence for Predictive Maintenance Applications', Third International Conference on Artificial Intelligence for Industries (AI4I 2020)](https://ieeexplore.ieee.org/document/9253083)

[https://doi.org/10.1109/AI4I49448.2020.00023](https://doi.org/10.1109/AI4I49448.2020.00023)
