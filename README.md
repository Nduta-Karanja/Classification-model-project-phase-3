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

