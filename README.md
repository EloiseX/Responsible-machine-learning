# Model Card

### Model developing person

Name:   Yiliang Xu   
Email:  yiliangxu@gwu.edu  

### License

Copyright 2022 Patrick Hall (jphall@gwu.edu) and Yiliang Xu (yiliangxu@gwu.edu)

Licensed under the Apacha License, Version 2.0 (the "License");you may not use the file except in compliance with the License. You may obtain a copy of the License at
     http://www.apache.org/licenses/LICENSE-2.0
     
Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

*DISCLAIMER*: This notebook is nnot legal or compilance advice.

## Model details

### Intended use


### Training data

Home Mortgage Disclosure Act data was downloaded from Github class repository for academical use. In order to fit the interpretable maching learning model, I splited this preprocessed and labeled dataset into 70% of train partition and 30% of test partition. In the training dataset, there are 112253 rows with numeric measurements and binary values. Validation dataset contains 48085 rows in total. Here is a shortcut of Home Mortgage Disclosure Act data:  

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

**row_id** : an unique id for each candidate.  
*black*, *asian*, *white*, *amind*, *hipac*, *hispanic*, *non_hispanic*: Binary numeric input, whether a candidate belongs to this region (1) or not (0).  
*male*, *female*: Binary numeric input, gender of candidates.  
*agegte62*:  
*agelt62*:  
*term_360*: Binary numeric input,  whether the morgage is a standard 360 month mortgage (1) or a different type of morgage(0).  
*conforming*:  
*debt_to_incom_ratio_missing*:  
*loan_amount_std*:  
*loan_to_value_ratio_std*:  
*no_intro_rate_period_std*:  
*intro_rate_period_std*:  
*property_value_std*:  
*income_std*:  
*debt_to_income_ratio_std*:  
*high_priced*:  

### Evaluation data


### Model details


### Quantitative analysis


### Ethical consideration
