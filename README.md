# Predicting-Insurance-Costs
Health insurance costs are rising. As such, it can be a strain on a person's financial life. It is useful to know what can make insurance costs rise to see if the costs can be minimized. 
## Goal 
The goal is to create a linear regression model to train and test data. The model will then be used to 
predict what raises insurance costs. 

## Plan for the Project
1. Explore Dataset
2. Describe the Data 
3. Determine Useful Variables
4. Divide Data
5. Build Model
6. Interpret Model
7. Draw Conclusions
8. Write Findings

## 1. Explore Dataset 
The dataset used is from Kaggle.com. It is called [Medical Cost Personal Datasets](https://www.kaggle.com/datasets/mirichoi0218/insurance?resource=download). This dataset has already been cleaned and recoded to be properly formatted. 

Exploring the data set is useful since it will allow me to understand the data more and how everything relates to one another. I will explore using various methods and graphing some relationships I think could be useful for the linear regression model.

### Pros of the Data
* It is already cleaned.
* It has multiple variables to utilize for the linear regression model.
* It is well documented

 ### Cons of the Data
 * It has some variables that are categorical rather than numerical

## 2. Describing the Data

### Columns 
This dataset was gathered from Kaggle, a website that provides datasets for data science and other related areas. 
There are 7 columns that each describe an aspect of a person using insurance. 

1. Age: How old the primary beneficiary is 
2. Sex: What gender the primary beneficiary is
3. BMI: Body Mass Index, provides insights about weight versus height 
4. Children: The number of children the primary beneficiary has 
5. Smoker: Stats whether the primary beneficiary is a smoker or not 
6. Region: The region in the US in which the primary beneficiary has their residential area listed 
7. Charges: The medical costs charged by health insurance 

### Quantitative Data
Quantitative Data is data that can be counted or measured. For example, a TV that is 60 inches has quantitative data since 60 inches describes the size of the TV. 

In the insurance dataset, there are a few columns with quantitative data: 
1. Age
2. BMI
3. Children
4. Charges

### Qualitative Data
Qualitative data can describe characteristics or aspects of an object or person. For example, a red TV has qualitative data since the color 'red' is used to explain how the TV looks. 

In the insurance dataset, there are a few columns with qualitative data: 
1. Sex 
2. Smoker
3. Region

## 3. Determine Useful Variables 
Since we are looking for correlations in the data, it is useful to plot the data to determine, visually, if there could be any correlations. 

To reduce the skewness of the data, the data was log-transformed to have a more uniform distribution of data. The log-transformed data was then graphed. 

![Log data](/Screenshots/histogram.png)

Before graphing the data, I used insurance.corr to see if there was any strong relation of variables to insurance costs. From the results, it showed that age and smoker status had high correlations with the cost of insurance.

Here I have plotted: 
1. Smoker vs Insurance Cost
   
![LSmoker](/Screenshots/smoker.png)

In this boxplot, those who are smokers tend to have higher insurance costs since the mean and median are higher than those who do not smoke. 

3. Sex vs Insurance cost
  ![Gender](/Screenshots/gender.png)
Here, it is shown that females have slightly higher average insurance costs, but not as big of a difference as those who are smokers versus not smokers.


4. Children vs Insurance Costs
   
![Children](/Screenshots/children.png)

In this graph, the average insurance cost stays around the same regardless of how many children the primary beneficiary has.

5. Region vs Insurance Costs
   
![Region](/Screenshots/region.png)

The region does not seem to change the average insurance costs, according to this graph.

7. Age vs Insurance Costs
   
![Age](/Screenshots/age.png)

As the age increases, so do the insurance costs. The rate at which it does is almost logarithmic.

From the graphs, the ones that have a little more variety in the average health insurance costs are: 
1. Smoker vs Insurance Costs
2. Age vs Insurance Costs

## 4. Dividing the Data 
Now that I have chosen the proper variables, I can start dividing the data to use in the linear regression model. 
First, I'll have to convert the smoker data into numerical data. I opted to use .map() due to its simplicity and ability to quickly convert categorical data into numerical data. 
![Map](/Screenshots/mappng) 

Now, for the division of the data, I have set my X to contain the smoker_boolean and age columns. These are my dependent variables. My independent variable (the one changing as a result of the dependents) is the log_charges column. 

The test size is about 30% so I was able to train 70% of the data. With that much training, the results of the training will be more reliable. To keep the divided dataset consistent, I chose a random state of 42. 

## 5. Build the Model 
I had divided the dataset, so I created the model. Earlier I used the sci-kit learn module to import various libraries needed to make and use the linear regression model. 

![Import](/Screenshots/import.png)

I created the model and fit the data using the training sets. 

## 6. Interpret the Model 

### MSE and R^2 Scores for Training Data
The training mean squared error score was around 0.469. The relatively low score indicated that the model was a good fit. The R^2 value was around 0.73. This means that it can account for 73% of the variation in the data, which is good for having a reliable dataset to draw predictions. 

### The Model Coefficient 
Using model.coef_, the obtained coefficients were: 
1. Smoker: 2.24
  
3. Age: 0.05

### MSE and R^2 Scores for Test Data 
The test MSE was around 0.432 and the R^2 value was 0.75. The similarity to the training dataset means that the data was not overfitted and could be reliably used to make predictions. 

### Residuals
The residuals are the differences between the actual value and the predicted value from the model. The scatterplot below shows that although the expected residuals were going to lie somewhere around 0, the trend of the graph is that it is going down. This indicates that the prediction and the model should be taken with a grain of salt as it the differences in the actual values and the predicted values are greater than expected. 

![Residuals](/Screenshots/residuals.png)

## 7. Draw Conclusions 
The model produced some reliable predictions. 

As a person ages, the model predicts that insurance costs will go up. Additionally, being a smoker has more weight on insurance costs going up. 

To apply this to real life, although aging is inevitable, one way to reduce health insurance costs is to try to not be a smoker. 




