# JAGSeco-evo
Bayesian models specified in JAGS that may be useful in ecology and evolutionary analysis


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