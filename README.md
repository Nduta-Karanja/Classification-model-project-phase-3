# **VEHICLE EMISSIONS CLASSIFICATION FOR REGULATORY COMPLIANCE MODEL PROJECT- STAGE I**
**Author: Nduta Karanja**

## 1.INTRODUCTION

**1.1. Problem Statement**

* **Context:** Vehicle emissions have become a critical issue in addressing environmental sustainability and public health. In the UK, stringent regulations are in place to reduce vehicle emissions and combat air pollution. High levels of CO2 emissions from vehicles contribute significantly to climate change, deteriorate air quality, and pose health risks such as respiratory and cardiovascular diseases. Regulatory agencies face the challenge of monitoring and enforcing emission standards effectively.

* **Business Problem:** 
Regulatory agencies need an efficient method to categorize vehicles into emission levels to prioritize enforcement actions and promote cleaner alternatives. The current process of manual assessment and enforcement is both time-consuming and prone to errors. Moreover, consumers lack accessible tools to understand and compare vehicle emissions easily.

* **Objective:**  Develop a robust classification model to categorize vehicles into three emission levels: Low, Moderate, and High, based on CO2 emissions data to help achieve Automatic Classification of Vehicles,Prioritize Enforcement Actions and Support Cleaner Alternatives.
 
**1.2. Project Goals And Stakeholders**

*Primary Goal:*

 - **Create a Classification Model** by developing and potentially deploying a machine learning model that categorizes vehicles into emission levels based on their CO2 emissions. The model should be accurate and reliable to ensure effective regulatory compliance.

*Secondary Goals:*

  - **Facilitate development and implemention of policies**  by providing *policy makers* with data driven insights aimed at reducing vehicle emmission,improving environmental quality and tracking effectiveness of emission reduction measures.
  - **Facilitate Regulatory Actions**  by enabling *regulatory agencies* to quickly and accurately identify high-emission vehicles for targeted actions and compliance checks.
  - **Enhance Awareness** by facilitating *Environmrental Advocacy Groups* with data and tools to support emmission reduction drives and providing *consumers* with a user-friendly interface or tool that allows consumers to check and compare vehicle emissions, encouraging the adoption of cleaner vehicles.
  - **Support Data-Driven Decisions** by offering insights and reports that can guide policy-making and regulatory strategies for improving air quality and reducing environmental impact.
  - **Facilitate Emission Reduction Strategy Development** by providing *Automotive Manufacturers* with a framework and tools to develop effective emission reduction strategies that align with current and anticipated regulatory requirements. This goal aims to support manufacturers in designing and implementing changes in their production processes and vehicle designs to achieve lower emissions and comply with environmental standards.

**1.3. Scope and Limitations**

 *Scope:*

   - **Data Focus**-The project centers on analyzing and classifying vehicle emissions data. It leverages a dataset containing information on various vehicle attributes and CO2 emissions.
   - **Model Development**-The project involves developing machine learning models (Logistic Regression and Decision Tree) to classify vehicles into predefined emission categories.
   - **Regulatory Use Case**- The classification model will be used by regulatory agencies to enhance their monitoring and enforcement capabilities.

*Limitations:*

   - **Data Quality**- The effectiveness of the classification model depends on the quality and completeness of the dataset. Inaccurate or incomplete data may affect model performance.
   - **Feature Limitations**-The model relies on available features such as engine size and CO2 emissions. Additional factors like driving conditions and maintenance history are not considered, which might influence actual emissions.
   
   - **Generalizability** -The model's performance is based on the specific dataset and may vary when applied to different datasets or vehicle types. Continuous updates and validation are required to maintain accuracy.
   - 
   - # 2.DATA

**2.1. Data Understanding**

  - **Name:** Vehicle Emissions Data Set (uk_gov_data_dense_preproc.csv)
  - **Source:** Kaggle

**Description:** This dataset contains information on 6,756 vehicles, including various features related to vehicle specifications and emissions. It is designed to facilitate analysis and modeling for vehicle emissions, which can be used for classification, regulatory compliance, and environmental impact studies.The fields are:

1. `car_id`                : **Number** - A unique identifier for each vehicle.
2. `manufacturer`          : **Categorical String** - The name of the vehicle manufacturer (e.g., Ford, Toyota, BMW)
3. `model`                 : **Categorical String** - The specific model of the vehicle (e.g., Focus, Corolla, X5)
4. `description`           : **Categorical String** - Additional details about the vehicle, which may include information on design, features, or special attributes.
5. `transmission`          : **Categorical String** - Gearbox type, such as "Manual" or "Automatic." This feature may influence emissions based on the type of transmission used.
6. `transmission_type`     : **Categorical String** - "Manual", "Automatic", or "Electric - Not Applicable".
7. `engine_size_cm3`       : **Number** - The volume of the engine’s gas displacement in cubic centimeters (cm³).
8. `fuel`                  : **Categorical String** -The type of fuel used by the vehicle (e.g., Petrol, Diesel, Electric). Different fuels have different emission profiles.
9. `powertrain`            : **Categorical String** -Describes the powertrain configuration (e.g., Front-Wheel Drive, All-Wheel Drive). The powertrain can impact fuel efficiency and emissions.
10. `power_ps`             : **Number** - Power of vehicle in PferdStarke (metric measure of horsepower, equivalent to 98.6% of one HP) This feature is important for understanding the vehicle’s performance and potential emissions.
11. `co2_emissions_gPERkm~`: **Number** - The CO2 emissions of the vehicle measured in grams per kilometer (g/km) according to the Worldwide Harmonized Light Vehicles Test Procedure (WLTP). This is the target variable for classification into emission levels.

**2.2. Data Inspection And Analysis**

To get a general sense of the structure and contents,we examine our dataset for preparation to ensure that the data is clean, well-understood, and properly prepared for creating accurate and reliable models.This is by checking basic information like the shape and consistency,looking out for missing, duplicates and NaN values,checking for duplicates
![image](https://github.com/user-attachments/assets/3581fb24-2966-49a4-87bb-96e04d5b9926)
As observed above,we do not have missing or NaN values.

Next,we get a concise summary of the DataFrame to nderstand the type of data each column contains by use of `df.dtypes` function in Python .
This is to help us identify and create consistency in our data as we will use categorical and numerical datatypes during our modeling.

![image](https://github.com/user-attachments/assets/aaf69f7d-9760-4265-a203-1dd6225df437)

## Summary Statistics Insights
The bellow summary provides a high-level understanding of the data’s structure and distribution, which is crucial for feature engineering, modeling, and interpretation in your analysis or machine learning tasks.

![image](https://github.com/user-attachments/assets/bb4c6113-ab56-4274-b4a2-91754c18682c)



1.`engine_size_cm3`:

* The *mean* engine size is around **1793.3 cm³**, but there is considerable *variability* (standard deviation of 825.9 cm³).
* The *range* (0 to 6749 cm³) suggests a *wide diversity*V in engine sizes. 
* The *median* (1749 cm³) is slightly below the mean, indicating a *right-skewed distribution* where  ***more* vehicles have smaller engines compared to larger ones.**

2.`power_ps`

* The *mean* power is 184.3 PS, with significant variability (standard deviation of 109.8 PS).
* *The *wide range* (0 to 800 PS) and the *higher median* (150 PS) compared to the *25th percentile* suggest that **while most vehicles have moderate power, there are also some with very high power ratings**. The distribution is likely right-skewed.

3.`co2_emissions_gPERkm`

* The *mean* CO2 emissions are 154.8 g/km, with a *standard deviation* of 55.0 g/km **indicating considerable variability**.
* The *range* from 0 to 380 g/km **shows a broad spectrum of emission levels.**
*  The *median* (151 g/km) is *slightly below the mean*, indicating a right-skewed distribution. **Most vehicles have emissions around the median, but a significant number have higher emissions.**


From this summarry we can conclude:

* **Wide Range of Values:** All numerical features have a wide range, indicating variability in vehicle specifications.
* **Skewed Distributions:** Variables such as engine_size_cm3, power_ps, and co2_emissions_gPERkm show right-skewed distributions, with more data points clustering towards the lower end.
* **High Variability:** Features such as engine_size_cm3 and power_ps have high standard deviations relative to their means, suggesting significant variability in these characteristics among the vehicles.
* **Potential Outliers:** The wide range and high maximum values in engine_size_cm3 and power_ps might indicate the presence of outliers or extreme values in these columns.


## Visualization

For our **visualization analysis**, we look at different aspects of our data in relation to emission.
Emissions Outlliers will be treated as:higher side as high-level emission release and lower side as low-level emmission release.Our goal is to maintain the lowest levels of emissions as consumers get to enjoy their ultimate choice and taste in motor vehicles so we will pick up on arlarming levels of emissions

![image](https://github.com/user-attachments/assets/e54db786-52db-4de0-a924-77427f713b71)
![image](https://github.com/user-attachments/assets/64b954e0-87c3-4a80-9ec7-6f45b2489ce9)
![image](https://github.com/user-attachments/assets/825f77cb-f6a7-4fdc-8258-87e903380a33)
![image](https://github.com/user-attachments/assets/ca500511-98ba-471b-9dad-8cb35d6c69cd)
![image](https://github.com/user-attachments/assets/f42de434-fd89-4040-b8e3-80ae0876d5e3)
![image](https://github.com/user-attachments/assets/0a93b3cd-ce34-4c50-94d4-e96c2119c953)

## Visualization Summary

From the observation above,we get to see:
   * the distribution of CO2 Emission accross all manufacturers with most of the highest emission releasing cars being `sports cars`(Ferraris,masseratis),`
   *  As the `engine size` increases,emmission also increase  (as very high levels are observed in big engine cars like Rolls Royce and land Rovers)
   This is mainly observed in `internal combastion engine cars`
   * `Petrol` cars are also represented as the highest emitting car followed by `Diesel` units but by a significant gap indicating need for regulations
   * `Electric` cars have the lowest levels of emissions with pure electrics at level zero
   *  According to the known UK vehicle emission standards,our data shows `modarate emision levels` as the highest distribution (Statistical summary-Most vehicles have emissions around the median, but a significant number have higher emissions)

     **2.3. Data Preprocessing And Feature Engineering**

    ## Identify features and target
The target variable for classification into emission levels is the CO2 emissions of the vehicle measured in grams per kilometer (g/km) according to the Worldwide Harmonized Light Vehicles Test Procedure (WLTP),so we separate the data into `X` and `y` accordingly:

In the UK, CO2 emissions are typically categorized by levels, particularly in the context of vehicles and their emissions. Here’s a general breakdown according to UK standards:

* **Low Emissions**
For vehicles, "low emissions" usually refers to those that produce less than 100 grams of CO2 per kilometer. Electric vehicles (EVs) and hybrid vehicles often fall into this category.

* **Medium Emissions**
This category generally includes vehicles that emit between 100 and 200 grams of CO2 per kilometer. These vehicles are typically more fuel-efficient than higher-emission models but still produce a significant amount of CO2.

* **High Emissions**
Vehicles that emit more than 200 grams of CO2 per kilometer are considered to have high emissions. These are often larger, less fuel-efficient vehicles such as SUVs or performance cars.
These classifications help consumers understand the environmental impact of their vehicles and are used for purposes like road tax and congestion charging in various UK cities.

In essence, we’re taking a list of CO2 emissions, sorting each entry into one of three categories, and adding this information to our list to make it easier to understand and compare the environmental impact of different vehicles
## Data Splitting 
Next, we separate the data into a train set and a test set prior to performing any preprocessing steps:

![image](https://github.com/user-attachments/assets/7e6917b8-d553-46a7-bd4f-e5a035ed3ed0)

## Drop Irrelevant Columns If Any

For the purpose of this analysis, we'll only use the following columns, described by `relevant_columns`. You can find the full description of their values in the file `uk_gov_data_dense_preproc.csv` included in this repository.

In the cell below, we get to reassign `X_train` so that it only contains the columns in `relevant_columns`.The sabset should lso contain the same number of rows adst the previous `x_train` set
![image](https://github.com/user-attachments/assets/0c9db721-2c5d-45fe-adca-9e626a5f32f1)

Let's look at the full `x_train` set
**2.3.3. Convert Categorical Features into Numbers**

Anything that is already `float64` or `int64` will work with our model, but these features need to be converted:

* `manufacturer` (currently type `object`)
* `model` (currently type `object`)
* `description` (currently type `object`)
* `transmission` (currently type `object`)
* `transmission_type` (currently type `object`)
* `fuel` (currently type `object`)
* `powertrain` (currently type `object`)

There are two main approaches to converting these values, depending on whether there are 2 values (meaning the categorical variable can be converted into a single binary number) or more than 2 values (meaning we need to create extra columns to represent all categories).
In the cells below, we inspect the value counts of the specified features:
As observed,all our features have more than 2 categories and will need to be expanded into multiple columns.
## Handling multiple categorical data
Categorical encoding is crucial for preparing data for machine learning models, as most algorithms require numerical inputs.
 Unlike *Binary Category Data* ,the process for encoding *Multiple Category data*  numerically is a bit more complicated, because we will need to create multiple *"dummy"* columns that are each representing one category.

To do this,we will use a common encoding method: `label encoding` from `sklearn.preprocessing`that works under the following process:

1. Identify data to be transformed (typically not every column is passed to every transformer)
2. Instantiate the transformer object
3. Fit the transformer object (on training data only)
4. Transform data using the transformer object
5. Add the transformed data to the other data that was not transformed

For our encoding,we will build an iterative encoding function to work on all our features one by one without the the need for a cumbersome code

## Preprossesing our test data

For consistency sake during our modeling,it is important for out train and test data to match


 Everything is numeric now! We have completed the minimum necessary preprocessing to use these features in a scikit-learn model!


 



