# Credit Line Increase Model Card

### Basic Information

* **Group member names and emails**: Victoria Abel, vrabel@gwu.edu
* **Model date**: August, 2021
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: [DNSC 6301 Project](https://github.com/vrabel1/GWU_DNSC_6301_Project/blob/main/DNSC%206301%20Project.ipynb)

### Intended Use
* **Primary intended uses**: This model is a probability of default classifier, with a use case for determining eligibility for a credit line increase.
* **Primary intended users**: Professor Hall
* **Out-of-scope use cases**: Any use beyond an project submission is out-of-scope.

### Training Data

* Data dictionary: 

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |

* **Source of training data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500

### Test Data
* **Source of test data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

### Model Details
* **Columns used as inputs in the final model**: 'LIMIT_BAL', 'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1', 'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6', 'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6'
* **Column(s) used as target(s) in the final model**: DELINQ_NEXT
* **Type of model**:Decision Tree
* **Software used to implement the model**: Python
* **Version of the modeling software**: 
* **Hyperparameters or other settings of your model**:

### Quantitative Analysis
* **Metrics used to evaluate your final model**: Training AUC, Validation AUC, Test AUC, and AIR
* **State the final values of the metrics for all data: training, validation, and test data**: 
    * Training AUC: 0.78
    * Validation AUC: 0.75
    * Test AUC: 0.74
    * Asian-to-White AIR: 1.00
    * Black-to-White AIR: 0.85
    * Female-to-Male AIR: 1.02
    * Hispanic-to-White AIR: 0.83
* **Provide any plots related to your data or final model -- be sure to label the plots!**: 
![image](https://user-images.githubusercontent.com/89735988/131259488-6a6efde6-3435-4ff1-bd52-2861fa467c09.png)
![image](https://user-images.githubusercontent.com/89735988/131259520-45a8e6b6-dbbb-4c03-b998-94c892f155bb.png)


### Ethical consideration
* **Describe potential negative impacts of using your model**:
  One potential negative impact of using this model is the extremely high importance for Pay_0. The high importance means a large amount of the decisions from the model are based on Pay_0. If there was an economic recession or another disaster that limits individuals funds, a large portion of the population would be predicted as delinquent on their next payment. This also ignores earlier payment history for individuals. Someone with excellent previous payment history that for any number of reasons couldn't pay their bill in the most recent month would be heavily penalized regardless of previous history.
* **Describe potential uncertainties relating to the impacts of using your model**:
  One uncertainty of this model would be its intended use. This model was only designed to predict delinquency on the next payment for applications of a credit line increase, therefore attemtpting to use it for another reason would be out of the scope for this model. A bank may try to use this for other uses such as: credit card applications and loan applications. It's uncertain how the model would perform on these tasks and could produce incorrect predicitions that could deny qualified individiuals or accept unqalified individiuals. This would be harmful both for the banks and the individuals applying to them.
* **Describe any unexpected or results**:
  The final model results were of interest as they 
