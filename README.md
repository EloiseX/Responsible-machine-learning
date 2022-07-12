# Model Card

The best remediated EBM is selected by comparing with other two models(Elastic net logistic regression, Monotonic gradient boosting machines). Then, I improved the  best remediated EBM considering feature importance, discrimination, red-teaming and model debugging.

### Model developing person

Name:   Yiliang Xu   
Email:  yiliangxu@gwu.edu  

### License

Copyright 2022 Patrick Hall (jphall@gwu.edu) and Yiliang Xu (yiliangxu@gwu.edu)

Licensed under the Apacha License, Version 2.0 (the "License");you may not use the file except in compliance with the License. You may obtain a copy of the License at
     http://www.apache.org/licenses/LICENSE-2.0
     
Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

*DISCLAIMER*: This notebook is not legal or compilance advice.

## Model details

### Intended use

The best remediated EBM was trained to identify the eligibility of candidates to get home mortgage. Banks and other financial institutions could use this model to evaluate candidates' financial conditions. The main task of this proejct is to find whether a candiadte should be accepted to a home mortgage or not. As a classification model, the best remediated EBM was selected from hundreds of models and trained to avoid discrimation, internal/external attacking and model debugging.  

Generaly, this best remediated EBM performs well in classifing candidates in home mortgage. If the dataset changes to another type (eg.commodity data), this model could be not as good as it works on financial datasets. Additionally, the best remediated EBM is prorbably unsuitable for regression problems.

### Training data

Home Mortgage Disclosure Act data was downloaded from [Github class repository](https://github.com/jphall663/GWU_rml/tree/master/assignments/data) for academical use. In order to fit the interpretable maching learning model, I split this preprocessed and labeled dataset into 70% of train partition and 30% of test partition. In the training dataset, there are 112253 rows with numeric measurements and binary values. Validation dataset contains 48085 rows in total. Here is a berif describtion of Home Mortgage Disclosure Act dataset:  

     '''
     RangeIndex: 160338 entries, 0 to 160337
     Data columns (total 23 columns):
      #   Column                        Non-Null Count   Dtype  
     ---  ------                        --------------   -----  
      0   row_id                        160338 non-null  int64  
      1   black                         137790 non-null  float64
      2   asian                         137790 non-null  float64
      3   white                         137790 non-null  float64
      4   amind                         137790 non-null  float64
      5   hipac                         137790 non-null  float64
      6   hispanic                      137877 non-null  float64
      7   non_hispanic                  137877 non-null  float64
      8   male                          86537 non-null   float64
      9   female                        86537 non-null   float64
      10  agegte62                      81414 non-null   float64
      11  agelt62                       81414 non-null   float64
      12  term_360                      160338 non-null  int64  
      13  conforming                    160338 non-null  int64  
      14  debt_to_income_ratio_missing  160338 non-null  int64  
      15  loan_amount_std               160338 non-null  float64
      16  loan_to_value_ratio_std       160338 non-null  float64
      17  no_intro_rate_period_std      160338 non-null  float64
      18  intro_rate_period_std         160338 non-null  float64
      19  property_value_std            160338 non-null  float64
      20  income_std                    160338 non-null  float64
      21  debt_to_income_ratio_std      160338 non-null  float64
      22  high_priced                   160338 non-null  int64  
      '''      

**row_id**: an unique id for each candidate.  

**black**, **asian**, **white**, **amind**, **hipac**, **hispanic**, **non_hispanic**: Binary numeric input, whether a candidate belongs to this region (1) or not (0). 

**male**, **female**: Binary numeric input, gender of candidates.  

**agegte62**: Binary numeric input, whether the age of a candidate is greater than 62 (1) or not (0).   

**agelt62**: Binary numeric input, whether the age of a candidate is less than 62 (1) or not (0).  

**term_360**: Binary numeric input,  whether the morgage is a standard 360 month mortgage (1) or a different type of morgage(0).  

**conforming**: Binary numeric input, whether the morgage conforms to normal standards (1), or whether the load is differnet (0).  

**debt_to_incom_ratio_missing**: Binary numeric input, missing maker (1) for debt_incom_ratio_std.  

**loan_amount_std**: Numeric input, standardized mortgage amount for candidates.  

**loan_to_value_ratio_std**: Numeric input, ratio of the mortgage size to the value of property for morgage candidates.  

**no_intro_rate_period_std**: Binary numeric input, whether a morgage does not include an introductory rate period (1) or not (0).  

**intro_rate_period_std**: Numeric input, standardized introductory rate period for morgage candadites.  

**property_value_std**: Numeric input, value of the mortgaged property.  

**income_std**: Numeric input, standardized income for mortgage candidates. 

**debt_to_income_ratio_std**: Numeric input, standardized debt-to-income ratio for mortgage candidates. 

**high_priced**: Binary target, whether the annual percentage rate (APR) charged for a mortage is 1.5% or more above a survey-based estimate of similar mortgage (1) or not (0).   

### Evaluation data  
  
The evaluation (or test) data of Home Mortgage Disclosur Act was derived from [Github class repository](https://github.com/jphall663/GWU_rml/tree/master/assignments/data) for academical use. There are 19831 rows in the preprocessed and unlabeled test dataset. The information about columns and data type is shown below.  

     '''
     RangeIndex: 19831 entries, 0 to 19830
     Data columns (total 22 columns):
      #   Column                        Non-Null Count  Dtype  
     ---  ------                        --------------  -----  
      0   row_id                        19831 non-null  int64  
      1   black                         17018 non-null  float64
      2   asian                         17018 non-null  float64
      3   white                         17018 non-null  float64
      4   amind                         17018 non-null  float64
      5   hipac                         17018 non-null  float64
      6   hispanic                      17016 non-null  float64
      7   non_hispanic                  17016 non-null  float64
      8   male                          10730 non-null  float64
      9   female                        10730 non-null  float64
      10  agegte62                      10089 non-null  float64
      11  agelt62                       10089 non-null  float64
      12  term_360                      19831 non-null  int64  
      13  conforming                    19831 non-null  int64  
      14  debt_to_income_ratio_missing  19831 non-null  int64  
      15  loan_amount_std               19831 non-null  float64
      16  loan_to_value_ratio_std       19831 non-null  float64
      17  no_intro_rate_period_std      19831 non-null  float64
      18  intro_rate_period_std         19831 non-null  float64
      19  property_value_std            19831 non-null  float64
      20  income_std                    19831 non-null  float64
      21  debt_to_income_ratio_std      19831 non-null  float64
     '''  
Compared with training data, evaluation (or test) data containes 22 columns without column **high_priced**, the target feature. Therefore, I can compete the result where label for evaluation data is not given to avoid learning from evaluation data.  

### Model details  

1. Model inputs and target

     For the model part, I selected 10 columns as inputs (X variables) in the best remediated EBM model including **term_360**, **conforming**, **debt_to_incom_ratio_missing**, **loan_amount_std**, **loan_to_value_ratio_std**, **no_intro_rate_period_std**, **intro_rate_period_std**, **property_value_std**, **income_std**, and **debt_to_income_ratio_std**.

     **high_priced** is the target vaiable of the best remediated EBM model.  

2. Model Type

     In terms of the best remediated model, explainable boosting machine (EBM) outperformes other two models (Elastic net logistic regression, Monotonic gradient boosting machines) considering the AUC score. EBM is a gradient boosting generalized additive model with interaction term based on decision trees. Compared with Random Forest and other machine learning models, EBM is a glass-box model which is more explainable.  

3. Model version

     The best remediated model EBM was trained with Python in Jupyter Notebook. I applied several packages to train this EBM model including numpy, pandas, interpret, h2o, xgboost etc. Here is the applied packages and version.

          '''
          # Python 3.6.9  
          
          h2o==3.32.1.3
          interpret==0.2.4
          jupyter==1.0.0 
          matplotlib==3.3.4
          numpy==1.19.5
          pandas==1.1.5
          scikit-learn==0.24.2
          seaborn==0.11.1
          xgboost==1.4.2
          '''  
4. Model hyperparameters   

     The hyperparameters and settings for the EBM is shown below.

          '''
          max_bins: 512,
          max_interaction_bins: 16,
          interactions: 10,
          outer_bags: 4, 
          inner_bags: 0,
          learning_rate: 0.001,
          validation_size: 0.25,
          min_samples_leaf: 5, 
          max_leaves: 5
          early_stopping_rounds = 100
          seed = 12345                          # set numpy random seed for better reproducibility
          NTHREAD = 4                           # set number of threads  
          '''  
          
### Quantitative analysis

1. Metrics  

     The best remediated EBM is a classificiation system to predict whether to approve an candidate's application of home mortgage or not, and was trained multiple times in a random grid search with a dictionary of hyperparameter list. It outperforms other two models concerning the [interpretion](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%201/Assignmnet_1.ipynb), [feature importance](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%202.ipynb), [discrimination](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%203.ipynb), [red-teaming](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%204.ipynb),  [model debugging](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%205.ipynb).  
     
    The AUC score of the EBM from the Assignment 1 is shown below.
    
    
2. Visualization  

     This project includes 5 coding file which develops the EBM cosidering different aspects. The plots displayed below correspond to each topic.
     
     **Assignment 1 Model score**  
     
     ![image](https://user-images.githubusercontent.com/98284132/176549638-73662bf6-f0e3-4e0b-add7-c2b30a07aba2.png)
     
     **Assignment 2 Feature importance**
     
      - Global feature importance  
      
      ![image](https://user-images.githubusercontent.com/98284132/176549514-278d634f-5bc5-402f-8d1a-590758eb512c.png)
     
     - Local feature importance  
     
       ![image](https://user-images.githubusercontent.com/98284132/176539508-ae0cce44-e6f3-4351-9a4b-773a18c80481.png)
       
     - Partical depedence  

       ![image](https://user-images.githubusercontent.com/98284132/176583776-9f9658fd-6d94-4b68-914c-23b2f665a72c.png) ![image](https://user-images.githubusercontent.com/98284132/176585018-0631d24b-4b85-4916-bdb0-bcb148985ad9.png) ![image](https://user-images.githubusercontent.com/98284132/176584143-e9b99572-63fb-424b-bbe5-a8dfc03e5638.png) ![image](https://user-images.githubusercontent.com/98284132/176584192-6bd589ce-d944-42c2-bcf0-4ad3fe2a34b4.png) ![image](https://user-images.githubusercontent.com/98284132/176584241-ef18499a-a68d-45f3-8780-5c5baed36cc6.png) ![image](https://user-images.githubusercontent.com/98284132/176584376-a3494549-d954-4f91-ade9-91dc0be96483.png) ![image](https://user-images.githubusercontent.com/98284132/176584428-3794be84-01b8-400a-9d57-490defd5f45c.png) ![image](https://user-images.githubusercontent.com/98284132/176584616-b9d5a387-17f1-4f46-b0ae-2f443d8e6a36.png) ![image](https://user-images.githubusercontent.com/98284132/176584661-45c9a811-3d71-407d-8648-8cc4e4b45c48.png) ![image](https://user-images.githubusercontent.com/98284132/176584711-785d8a41-9747-4312-9313-48e66ba69e74.png) ![image](https://user-images.githubusercontent.com/98284132/176584764-1a06ab33-2aa9-4ffe-8858-65ac0b11aedc.png) ![image](https://user-images.githubusercontent.com/98284132/176584805-c81b1322-ac2b-4986-962a-ace5d25f204c.png)

     **Assignment 3 Discrimaination**
     
     - EBM grid search result  
     
       ![image](https://user-images.githubusercontent.com/98284132/176543392-9fc0a785-0bd4-4ffd-990a-cac3587987d0.png)

     - Retrained impact raio of differnet group of region
     
       ![image](https://user-images.githubusercontent.com/98284132/176544201-7300819d-4713-4538-89b8-5c83b0dba83c.png)  
       
     **Assignment 4 Model extraction attack**  
     
     ![image](https://user-images.githubusercontent.com/98284132/176550430-719b6bad-d025-4b05-8705-62d49b96b9be.png)

     **Assignment 5 Model debugging**
     
     - Residual analysis
     
      ![image](https://user-images.githubusercontent.com/98284132/176547818-a10ed360-907a-4165-bca6-43d59552b0df.png)  
      
     - Retained EBM AUC after the removal of outliers  
     
      ![image](https://user-images.githubusercontent.com/98284132/176547671-b8c9240a-094d-4858-b006-6eff28f4a233.png)

     Additionally, the Montonic XGBoost performed better than EBM in Assignment 3 concerning the AUC score. However, the Montonic XGBoost did not show a vaild plot in the residual analysis, the EBM is still the best remediated model.  
     
### Ethical consideration  

1. Potential negative impacts  

   The best remediated EBM has the limitation on the prediction without efficient data. The prediction of a feature without data may revert to its mean which is unreasonable for Home morgage dataset. However, montonic GBM solve this problem by applying a montonic constraints. It is important to use domain knowledge to make the model more reasonable and explainable.     

   In the real world, the discrimation may happens in the differnet race concerning the education, financial service and etc. The products or system of a company could be attacked by other individuals or organization in the midnight or Christmas Day. Therefore, we need to design a back-up plan and monitor the model frequently to avoid the discrimation, internal/external attack and some other risks.

2. Potential uncertainties  

   The best remediated EBM is interpretable compared with some other traditional machine learning models. In some case, the EBM may need to sacrifice a level of accuracy to maintain its interpretability. Therefore, this best remediated EBM may not performe well in the case with a high requirement of AUC. In the real world, the large dataset fitting into this best remediated EBM could dramatically increase the time to get results. It's also an unexpected case I met in Assignment 3 that finds the best model in grid search with 500 models. Finding the best remediated EBM costs 8-9 hours to train 500 models.  

   In couclusion, although this model was tested and remediated for bias, there is much more to bias than models and data, and this best remediated EBM should be monitored for bias issues moving forward.
