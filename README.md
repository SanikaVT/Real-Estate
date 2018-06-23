# 1.Funding Successful Projects(CLassification Problem)
Funding successful project is a binary classification problem.
# 1. Business Problem
## 1.1 Problem Context

Our client is a large community of tech enthusiasts called Kickstarter.

- This community aids people in bringing out creative projects.
- Till now, more than 3 billion dollars have been contributed by the members in fuelling creative projects.
- It works on All or Nothing basis i.e if a project dosen't meet its goal, the project owner gets nothing.

## 1.2 Problem Statement

- Recently, Kickstarter released its public data repository to allow researchers and enthusiasts like us to help them solve a problem.
- The problem is regarding whether a project will get successfully funded or not.
- If we are able to build such a model that predicts whether a project will be funded as per its requirements, it can help the community to determine beforehand, its successful completion.

## 1.3 Business Objectives and Constraints

-  Deliverable: Trained model file.
-  Ouput Probabilities along with the prediction.
-  Model interprtability is very important
-  No latency constraints.

# 2. Machine Learning Problem

## 2.1 Data Overview
For this project:

1. The train dataset and the test datset has 108129 observations and 63465 obervations respectively.
2. The train data consists of sample projects from the May 2009 to May 2015. The test data consists of projects from June 2015 to March 2017.
3. Each observation in the train and test sets refers to a project's description and status.

**Target Variable**
- 'final_status' - whether the project got successfully funded (target variable – 1,0)

**Features of the data:**

Unique characteristics

* project_id - unique id of project
* name - name of the project
* desc - description of project
* goal - the goal (amount) required for the project
* keywords - keywords which describe project

General project specifications 

* disable communication - whether the project authors has disabled communication option with people donating to the project
* country - country of project author
* currency - currency in which goal (amount) is required
* deadline - till this date the goal must be achieved (in unix timeformat)
* backers_count - no. of people who backed the project

Project state information

* state_changed_at - at this time the project status changed. Status could be successful, failed, suspended, cancelled etc. (in unix timeformat)
* created_at - at this time the project was posted on the website(in unix timeformat)
* launched_at - at this time the project went live on the website(in unix timeformat)
* final_status - 	whether the project got successfully funded (target variable – 1,0)

## 2.2 Mapping business problem to ML problem

### 2.2.1 Type of Machine Learning Problem

It is a binary classification problem, where given the above set of features, we need to predict if a given project will be successfully funded or not.

### 2.2.2 Evaluation Metric (KPI)

Since this is binary classification problem, we use the following metrics:
* **Confusion matrix** - For getting a better clarity of the no of correct/incorrect predictions by the model
* **ROC-AUC** - It considers the rank of the output probabilities and intuitively measures the likelihood that model can distinguish between a positive point and a negative point. (**Note:** ROC-AUC is typically used for binary classification only). We will use AUC to select the best model.

# 3.Feature Engineering 

### 3.1.Features Created:
##### time_to_achieve:
* This features shows time required to complete the project.
* Feature is created using two other features: launched_at and created_at
* The difference between launched_at and created_at gives the time in terms of number of days required to complete the project.
##### completion_before_deadline:
* This features shows how early the project state is changed before the deadline.
* Feature is created using two other features: launched_at and deadline.
* The difference between deadline and launched_at gives how early the project is launched before the deadline.
##### time_to_change_the_status:
* One more feature is created which gives the number of days in which the status of the project changes after it is launched

### 3.2.Features Removed:
* Features such as project_id, description, name, keywords and other unused features are removed.

# 2.Real Estate(Regression Problem)

# 1. Business Problem
## 1.1 Problem Context

Our client is a large Real Estate Investment Trust (REIT).
* They invest in houses, apartments, and condos(complex of buildings) within a small county in New York state.
* As part of their business, they try to predict the fair transaction price of a property before it's sold.
* They do so to calibrate their internal pricing models and keep a pulse on the market.

## 1.2 Problem Statement
The REIT has hired us to find a data-driven approach to valuing properties.
* They currently have an untapped dataset of transaction prices for previous properties on the market.
* The data was collected in 2016.
* Our task is to build a real-estate pricing model using that dataset.
* If we can build a model to predict transaction prices with an average error of under US Dollars 70,000, then our client will be very satisfied with the our resultant model.

## 1.3 Business Objectives and Constraints
* Deliverable: Trained model file
* Win condition: Avg. prediction error < \$70,000
* Model Interpretability will be useful
* No latency requirement
# 2. Machine Learning Problem
## 2.1 Data Overview

For this project:
1. The dataset has 1883 observations in the county where the REIT operates.
2. Each observation is for the transaction of one property only.
3. Each transaction was between \$200,000 and \$800,000.

#### Target Variable
* 'tx_price' - Transaction price in USD

#### Features of the data:

Public records:
* 'tx_year' - Year the transaction took place
* 'property_tax' - Monthly property tax
* 'insurance' - Cost of monthly homeowner's insurance

Property characteristics:
* 'beds' - Number of bedrooms
* 'baths' - Number of bathrooms
* 'sqft' - Total floor area in squared feet
* 'lot_size' - Total outside area in squared feet
* 'year_built' - Year property was built
* 'active_life' - Number of gyms, yoga studios, and sports venues within 1 mile
* 'basement' - Does the property have a basement?
* 'exterior_walls' - The material used for constructing walls of the house
* 'roof' - The material used for constructing the roof

Location convenience scores:
* 'restaurants' - Number of restaurants within 1 mile
* 'groceries' - Number of grocery stores within 1 mile
* 'nightlife' - Number of nightlife venues within 1 mile
* 'cafes' - Number of cafes within 1 mile
* 'shopping' - Number of stores within 1 mile
* 'arts_entertainment' - Number of arts and entertainment venues within 1 mile
* 'beauty_spas' - Number of beauty and spa locations within 1 mile
* 'active_life' - Number of gyms, yoga studios, and sports venues within 1 mile

Neighborhood demographics:
* 'median_age' - Median age of the neighborhood
* 'married' - Percent of neighborhood who are married
* 'college_grad' - Percent of neighborhood who graduated college

Schools:
* 'num_schools' - Number of public schools within district
* 'median_school' - Median score of the public schools within district, on the range 1 - 10

## 2.2 Mapping business problem to ML problem
### 2.2.1 Type of Machine Learning Problem
It is a regression problem, where given the above set of features, we need to predict the transaction price of the house.

### 2.2.2 Performance Metric (KPI)
**Since it is a regression problem, we will use the following regression metrics:**
* Root Mean Squared Error (RMSE)
* R-squared
* Mean Absolute Error

# 3.Feature Engineering

### 3.1.Features Created:
##### two_and_two:
* An indicator variable to flag properties with 2 beds and 2 baths and name it 'two_and_two'.
##### old_properties:
* People might also not take much interest in old properties.
* so, this feature gives properties built before 1980.
##### tax_and _insurance:
* Both tax and insurance are monthly quantities property holder needs to pay monthly 
##### during_recession:
* A new feature called 'during_recession' is created to indicate if a transaction falls between 2010 and 2013.
##### propery_age:
* property_age' denotes the age of the property when it was sold and not how old it is today, since we want to predict the price at the time when the property is sold.
##### school_score:
* A school score feature is created as num_schools * median_school

##### One hot Encoding:
* Machine learning algorithms cannot directly handle categorical features. Specifically, they cannot handle text values.
* Therefore, we need to create dummy variables for our categorical features.
* *Dummy variables* are a set of binary (0 or 1) features that each represent a single class from a categorical feature.

### 3.2.Features Removed:
* Features such as property_tax, year_built, tx_year, insurance are removed.
