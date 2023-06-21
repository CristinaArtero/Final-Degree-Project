# Final Degree Project
## Description
This repository contains scripts used for the project: Proteomic signatures associated with the body composition at baseline and after five years of follow-up in an adult population.  
The project aimed to characterize plasma proteomic profiles associated to baseline body composition and changes in body weight in two Swedish cohorts composed of adult men and women.  
To explore these associations, repeated double cross-validated models were performed coupled to random forest (rdCV-RF) and partial least squares (rdCV-PLS) algorithms. The package “MUVR” was used to perform these analyses. The MUVR function requires some specifications for arguments such as:
* the proteome dataset (`X`)
* a response vector corresponding to the exposure variable (`Y`). Depending on the type of model, the response vector was in a categorical scale (for RF) or in a continuous scale (PLS).
*	a vector of unique variable identifiers for samples/individuals (`ids`)
*	a logical one to scale the protein expression matrix (scale, for PLS)
*	the number of repetitions (`nRep`)
*	the number of outer cross-validation segments (`nOuter`)
*	the variable ratio (proportion of variables kept per iteration, `varRatio`)

All models incorporated the same values for parameters (except parameters `X`, `Y` and `ids`). As a clarification, all models incorporated `nRep = 10`, `nOuter = 8` and `varRatio = 0.7` (even permutation tests).

## Input files
* `Q2008.csv`: dataset containing data from a health questionnaire at 2008.
*	`Q2009.csv`: dataset containing data from lifestyle and dietary questionnaires at 2009.
*	`visitclin.csv`: dataset containing clinical examinations measurements of all participants, including the following anthropometric measures used in this study:  weight, height, hip, waist circumference, body fat composition.
*	`CVD2.csv`: dataset containing protein expression values of the Olink® panel “Cardiovascular II”.
*	`CVD3.csv`: dataset containing protein expression values of the Olink® panel “Cardiovascular III”.
*	`Metabolism.csv`: dataset containing protein expression values of the Olink® panel “Cardiometabolic”.
*	`delta.bwa.omics.rds` (Rdata file): This object includes the dataset containing anthropometrics measures in different scales for the population of interest (individuals having body weight data at baseline and follow-up as well as proteomics data at baseline). These measurements were used as variables of exposures for different tests.
*	`diseases.csv`: dataset containing all documented disease diagnoses of participants as well as the date of their visit to clinical examination.
*	`ICD10 _codes_10_selected.xlsx`: dataset containing a conversion of diseases names and their abbreviations in ICD10 format

## Scripts
*	`Descriptive_BMI.Rmd`: script exploring the baseline characteristics of participants according to three BMI categories. This script was employed to generate Table S1.
*	`rdcv.PLS.modeling.Rmd`: script including performance and validation of rdCV-PLS models assessing the association (in a continuous scale) of plasma proteome and baseline BMI, WC and %BF.
*	`rdcv.RF.modeling.Rmd`: script including performance and validation of rdCV-RF models assessing the association (in a categorical scale) of plasma proteome and baseline BMI, WC and %BF.
