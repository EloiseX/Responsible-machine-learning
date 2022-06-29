# Model Card

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


### Training data

Home Mortgage Disclosure Act data was downloaded from Github class repository for academical use. In order to fit the interpretable maching learning model, I splited this preprocessed and labeled dataset into 70% of train partition and 30% of test partition. In the training dataset, there are 112253 rows with numeric measurements and binary values. Validation dataset contains 48085 rows in total. Here is a berif describtion of Home Mortgage Disclosure Act dataset:  

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
  
The evaluation (or test) data of Home Mortgage Disclosur Act was derived from Github class repository for academical use. There are 19831 rows in the preprocessed and unlabeled test dataset. The information about columns and data type is shown below.  

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
          max_bins: [128, 256, 512],
          max_interaction_bins: [16, 32, 64],
          interactions: [5, 10, 15],
          outer_bags: [4, 8, 12], 
          inner_bags: [0, 4],
          learning_rate: [0.001, 0.01, 0.05],
          validation_size: [0.1, 0.25, 0.5],
          min_samples_leaf: [1, 2, 5, 10],
          max_leaves: [1, 3, 5]

          early_stopping_rounds = 100
          seed = 12345                          # set numpy random seed for better reproducibility
          NTHREAD = 4                           # set number of threads  
          '''  
          
### Quantitative analysis

1. Metrics  

     The best remediated EBM is a classificiation system to predict whether to approve an candidate's application of home mortgage or not, and was trained multiple times in a random grid search with a dictionary of hyperparameter list. It outperforms other two models concerning the [interpretion](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%201/Assignmnet_1.ipynb), [feature importance](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%202.ipynb), [discrimination](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%203.ipynb), [red-teaming](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%204.ipynb),  [model debugging](https://github.com/EloiseX/Responsible-machine-learning/blob/main/Assignment%205.ipynb).

### Ethical consideration
