# Explainable machine learning classification for rheumatoid arthritis using B cell receptor sequences

This is the MSc Bioinformatics dissertation repository that uses B cell receptor (BCR)
sequences to train classification models to distinguish between rheumatoid arthritis (RA)
patients and the general public. 

For this project, 2 machine learning models (Logistic regression and Multilayer perceptron) 
are trained and tested for their accuracy in distinguishing the patients primarily on BCR 
sequences. The raw Illumina BCR reads are cleaned and transformed into features that could 
be accessed by the machine learning model. One ‘shallow’ model (Logistic regression) and one 
‘deep’ model (Multilayer perceptron) were trained on the features to decide whether a complex 
model is needed to identify the patterns in the datasets. Then, SHapley Additive exPlanation 
(SHAP) was used to explain the decisions of the multilayer perceptron model that performs better 
with a higher F1-score (balance between Type I and Type II error). The explainability of the deep 
learning model allows the feature importance to be analysed and extracts biologically meaningful 
features that could be used for further research.


## Methods
### 1. reads_processing_pipeline
- PRESTO analysis of Illumina raw reads through quality control and primer masking
- IgBLAST analysis of quality-controled alligned reads to transform into features

The reads proccessing pipeline is created using presto (version 0.7.4) and igblast 
(version 1.21.0) with OGRDB database (version 9). These tools are organised into a pipeline using snakemake with docker image acccess containing required tools and database for reproducibility. 

### 2. exploratory_and_data_cleaning
- Data cleaning and filtering of reads with NAs after feature transformation
- Train test split using 80% training, 10% validation, and 10% testing

### 3. model_training
- MLP outperforms Logistic regression with higher accuracy, f1-score, and ROC-curve
- MLP model reaches f1-score of 0.677, and increase from 0.367 with logistic regression model
- 68% accuracy at individual reads level but 100% acccuracy at patient repertoire lvel with 
statistical tests indicating significant differences between repertoires classified as coming from RA and coontrol.

### 4. SHAP_analysis (SHapley Additive exPlanation )
- Analysis of feature importance in MLP model,highliting potential features that are 
related to the development of rheumatoid arthritis
- Explainability of deep models

## Notes
Airr reads dataset is collected from "In Human Autoimmunity, a Substantial Component of the B Cell Repertoire Consists of Polyclonal, Barely Mutated IgG+ve B Cells" by Graeme Cowan. \
doi: https://doi.org/10.3389/fimmu.2020.00395

