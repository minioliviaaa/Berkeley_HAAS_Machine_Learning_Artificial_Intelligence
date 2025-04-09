
# UsedCarPriceAnalysis
What drives the price of a car?

## OVERVIEW

In this application, you will explore a dataset from kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing. Your goal is to understand what factors make a car more or less expensive. As a result of your analysis, you should provide clear recommendations to your client -- a used car dealership -- as to what consumers value in a used car.

## CRISP-DM Framework

We have followed below CRISP-DM model for this assignment

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/e32b15cf-4097-4cc1-bede-40b37c16dc47)

## Business Understanding

From a business perspective, we are tasked with identifying key drivers for used car prices. In the CRISP-DM overview, we are asked to convert this business framing to a data problem definition. Using a few sentences, reframe the task as a data task with the appropriate technical vocabulary.



####  We want to find out all the features which affect the used car price.

####  Given is the vehicle dataset.

1. Understand the features and the data
2. Cleanup the data records and columns
3. Create the models which can predict the price of used car based on the features provided
4. Report the most influential features based on the models built.

## Data Understanding

After considering the business understanding, we want to get familiar with our data. Write down some steps that you would take to get to know the dataset and identify any quality issues within. Take time to get to know the dataset and explore what information it contains and how this could be used to inform your business understanding.

#### Steps for Data Understanding

1. Check the data by taking samples
2. Find out how many features and data rows are available
3. Check the data types for the features
4. Check the quality of data such as duplicates and null values
5. Find out how many unique values are present
6. Find out the outliers.
7. Understand the dataset quality. Find out which features have non-proportional data which can affect the outcome of the model.
8. Visualization wherever required


## Data Preparation

After our initial exploration and fine tuning of the business understanding, it is time to construct our final dataset prior to modeling. Here, we want to make sure to handle any integrity issues and cleaning, the engineering of new features, any transformations that we believe should happen (scaling, logarithms, normalization, etc.), and general preparation for modeling with sklearn


#### Data Cleanup

1. Id , VIN columns will not help in the model so deleting these columns from the dataset.
2. Also almost 72% values for Size are null so we will delete Size column as well.
3. Model column will not help as it has too much variance so deleting modelcolumn from the dataset
4. Records with price 0 will not help so deleting records with price 0.
5. As most of the data values are having vehicles after Year 2000, We will eliminate records having Year before 2000.
6. We are considering used cars so we will consider cars having odometer reading more than 100.
7. As most of the data is for "clean" title cars, we are considering considering cars with clean title only.
8. Looking at data, we have decided to not consider paint_color and transmission columns. 

   We are converting Cylinders field to numeric values :

   ![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/d0134990-462d-4194-82d2-52cb75c6f168)

   We are converting condition field to numeric values :

   ![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/5e209bfc-601f-40ed-8156-63d8a45c5495)


   Price Histogram :

   ![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/4456dc13-45a7-4e32-b5e6-bd1acdc63bb1)

   Year Histogram :

   ![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/eebcc582-090c-43f1-9877-c6266c57fe0b)

   Odometer Histogram :

   ![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/7844738f-01b6-47e9-8f9b-5fda2f2387fc)



## Modeling

With your (almost?) final dataset in hand, it is now time to build some models. Here, you should build a number of different regression models with the price as the target. In building your models, you should explore different parameters and be sure to cross-validate your findings.

#### Linear Regression : 

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/895b68e2-3c2d-4139-ae61-336fa4e0279c)

Training MSE:  209291431796789.9

Testing MSE:  280822271427.3136

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/f86fe7e2-0b90-4c21-a33c-5aeb6fd83650)


#### Ridge Regression with alpha = 100 : 

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/27daf343-2402-475c-a7d4-c9a3f533bef5)

Training MSE:  208799320901582.22

Testing MSE:  516907155768.854

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/236078f4-46bd-4a8e-b991-327c326709ce)

#### Lasso Regression with alpha = 1: 

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/d6f0b4c0-6f5c-4375-bcc7-5c25dee937db)

Training MSE:  208758480094704.44

Testing MSE:  775731739482.3242

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/0b3a99be-7da3-4ffe-b6a9-2b8544b7784c)


Above 3 models were used to predict the car price and to find out the most influential features for the used car price. Linear regression relatively performed better with the lowest MSE amongst the three models evaluated. The main observation is , although the three models have little bit difference in finding the most influential features, many of the fetures are overlapping amongst the three models.

## Observations & Findings

As per linear regression, the most influential fetures in driving the price of used car are :
1. Number of Cylinders
2. Manufacturer
3. Year
4. Trim Type
5. Condition
6. Fuel

For other models also manufacturer, cylinders, trim type are amongst first 5 influential features.

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/e25a291c-2355-4874-841e-2c7bc7565675)

Most cars have 4, 6 or 8 cylinders. Cars with 8 cylinders are most expensive while cars with 4 cylinders are cheapest

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/4c732177-13ed-493d-9054-48b41801b80a)

Trucks, Pickups and SUVs are generally more expensive than other vehicle types such as sendans

![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/f6bb688b-701e-4dd1-9d7b-09e7ec816485)


![image](https://github.com/aksagar85/UsedCarPriceAnalysis/assets/31389612/f7caae54-0638-4915-bc6a-15cc18d30230)

Cars are more expensive , if the are newer (manufactured in latest years)


## Recommendations 

1. Cars with recent manufacturing years are more popular so dealership should keep more invetory for these cars
2. Cars with 4 , 6, 8 cylinders are more popular but cars with 8 & 6 cylinders keep more value.
3. Delership should consider manufacturer as important factor when re-stocking the inventory
4. Other factors deleraship should consider while acquiring or re-stocking inventory are Trum Type, Condition of Vehicles and Fuel type
