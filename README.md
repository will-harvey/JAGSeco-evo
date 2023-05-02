# JAGSeco-evo
Bayesian models specified in JAGS that may be useful in ecology and evolutionary analysis


## Variable selection using BSSVS

Bayesian Stochastic Search Variable Selection (BSSVS) is a variable selection technique, which usually involves the use of indicator variables.
Binary indicator variables dictate whether a variable is included in the model or not, while the distribution for a parameter estimate associated with the variable is also estimated.
This means that variable selection and model-fitting are carried out simultaneously.
The mean of an indicator variable provides an estimate of the inclusion probability of that indicator.
These approaches are particularly useful when the number of possible predictors is high, including when this number is higher than the number of observations.
The folder 'jags_model/bssvs' contains subdirectories with models to perform the following methods of BSSVS
- Binary-mask variable selection
- Spike-and-slab regression
In addition, a null model to compare with these models is coded. The null model uses no variable selection and thus the model is fully saturated with all possible predictors provided included.

## Zero-one-inflated beta regression

Standard beta regression is used to model variation in a response variable expressed as proportions between 0 and 1.
Observations are assumed to follow a beta regression, parameterised with mean and precision.
The mean of the beta distribution is dependent on some combination of explanatory variables.
The precision can also be modelled independently for observations rather than being held constant; this is sometimes referred to as a variable dispersion beta regression.

When values of 0 and 1 are also present among the response variable, zero-one-inflated beta (ZOIB) regression may be used.
ZOIB regression involves modelling a mixture of three things:
1. A logistic regression model that predicts if an outcome is either discrete (0 or 1) or not (a proportion between 0 and 1)
2. A logistic regression model that predicts if discrete values are 0 or 1.
3. A beta regression model that predicts the value of an outcome that falls between 0 and 1. The parameters of a beta distribution are modelled.

Zero-inflated beta (ZIB) regression or one-inflated beta (OIB) regression are slightly simplified versions of ZIOB that involve modelling:
1. A logistic regression model that predicts if an outcome is either discrete (0 or 1 for ZIB or OIB regression, respectively) or not (a proportion between 0 and 1)
2. A beta regression model that predicts the value of an outcome that falls between 0 and 1. The parameters of a beta distribution are modelled.

JAGS-specified models are located in the directory 'jags_model/zoib'.
A script showing how to apply these models to proportional data mimicking what might be found in a analysis of lizard microhabitat is shown in 'analysis_habitat_zoib/run_zoib_lizard_example.Rmd'.