[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/ol4GAg0d)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=15423777)
<!--
Name of your team's final project
-->
# Final-project - Using ML to Predict Distress in Cancer Patients
##  Apple [National Action Council for Minorities in Engineering(NACME)](https://www.nacme.org) Artificial Intelligence - Machine Learning (AIML) Intensive Summer Bootcamp at the [University of Southern California](https://viterbischool.usc.edu) 

<!--
List all of the members who developed the project and
link to each members respective GitHub profile
-->
Developed by: 
- [Rabiat Sadiq](https://github.com/rabiats) - `Computer Engineer / CS` - `University of Texas at San Antonio`
- [Emiliano Gonzalez](https://github.com/egonzalez82077) - `Materials Science and Engineering` - `Georgia Institute of Technology` 
- [Emily Mojica](https://github.com/emimojica) - `Computer Science and Business Administration` - `University of Southern California` 


![Python](https://img.shields.io/badge/Code-Python-informational?style=flat&logo=python&logoColor=white&color=6aa6f8)
![Swift](https://img.shields.io/badge/Code-Swift-informational?style=flat&logo=swift&logoColor=white&color=6aa6f8)
![CoreML](https://img.shields.io/badge/Code-CoreML-informational?style=flat&logo=coreML&logoColor=white&color=6aa6f8)
![Xcode](https://img.shields.io/badge/Code-Xcode-informational?style=flat&logo=Xcode&logoColor=white&color=6aa6f8)
![CareKit](https://img.shields.io/badge/Code-CareKit-informational?style=flat&logo=CareKit&logoColor=white&color=6aa6f8)
![Healthkit](https://img.shields.io/badge/Code-HealthKit-informational?style=flat&logo=HealthKit&logoColor=white&color=6aa6f8)
![ResearchKit](https://img.shields.io/badge/Code-ResearchKit-informational?style=flat&logo=ResearchKit&logoColor=white&color=6aa6f8)


## Description
<!--
Give a short description on what your project accomplishes and what tools is uses. In addition, you can drop screenshots directly into your README file to add them to your README. Take these from your presentations.
-->
Distress is defined in the NCCN Guidelines for Distress Management as a
multifactorial, unpleasant experience of a psychologic (ie, cognitive, behavioral,
emotional), social, spiritual, and/or physical nature that may interfere with the ability to
cope effectively with cancer, its physical symptoms, and its treatment.” Early evaluation
and screening for distress leads to early and timely management of psychologic
distress, which in turn improves medical management 

[1]. Assuage is a HIPAA-compliant research platform that leverages Apple’s ResearchKit and CareKit
open-source frameworks. In addition, Assuage’s frontend leverages Apple’s HealthKit
to aggregate sensor-based health data when applicable. Assuage is a distributed
system where each patients’ device operates online/offline using synchronized vector
clocks, but currently lacks the ability to leverage ML 

[2]. The frontend app of Assuage is developed in Swift for iOS and watchOS.
The objective of this project is to use ML to understand patient objective and subjective
data in remote patient monitoring applications. Specifically to integrate ML into
Assuage’s frontend to detect/predict Distress via sensor data (objective data). The
project will leverage tools such as: Xcode, CoreML, CareKit, ResearchKit, HealthKit,
and PyTorch.

<img width="647" alt="image" src="https://github.com/user-attachments/assets/9ed68e14-1868-48ed-a445-f05e8340176a">

## Major Findings/Learning
* How to naviagte Xcode for app development
* How to code via Swift
* The correlation of psychological indicators and emotional distress

## Research
The Wearable Stress and Affect Detection (WESAD) Dataset contains physiological and motion data from 15 participants collected via wearable devices (chest and wrist) during activities inducing stress, amusement, and neutral states. 
Dataset includes Blood Volume Pulse (BVP), Electrocardiogram (ECG), Electromyogram (EMG), Electrodermal Activity (EDA), Respiration (RESP), body temperature, and acceleration data, useful for stress and emotion detection research.
For our project, we focused on BVP and RESP data, as these were most applicable and attainable using our data collection equipment (Apple Watch and Apple Health).

We identified 5 strong indicators of emotional distress:

Primary Indicators:
* Higher Heart Rate
* Lower Heart Rate Variability (HRV)
* Lower Respiration Rate
  
Activity Metrics:
* Lower Step Count
* Lower Active Energy (Calories Burned)


## Exploratory Data Anlysis (EDA)
This data validated the influence of emotional distress on Heart Rate and Heart Rate Variability via BVP

<img width="501" alt="image" src="https://github.com/user-attachments/assets/ee7e2f09-b6a7-409f-aa33-4f32ded82136">

This data validated the influence of emotional distress on Respiration Rate via RESP

<img width="501" alt="image" src="https://github.com/user-attachments/assets/ab13072b-fc18-432d-bfcc-4deb73c10f5b">

### Further Data Processing
Due to time constraints and the complexity of these calculations, we adopted a creative approach by using zero crossings to determine frequency and derive the necessary values.
BVP:

<img width="569" alt="image" src="https://github.com/user-attachments/assets/140ed49e-0c8d-4a2e-a1e7-58e1d2874bb6">

RESP:

<img width="571" alt="image" src="https://github.com/user-attachments/assets/12e94982-b1ea-4ec8-a1e2-ba2334656392">

Overall, we found a strong correlation between biometric signals (BVP and RESP) and Distress that we could derived values from that are automatically calculated by Apple Watch and Health Kit

## Features

- **ML Integration:** Incorporates a machine learning model to predict distress levels from sensor data.
- **Real-Time Alerts:** Provides notifications when distress levels exceed a predefined threshold.
- **Data Utilization:** Leverages sensor-based data for accurate distress prediction.
- **iOS Integration:** Seamlessly integrates with the existing Assuage iOS app.

## Technologies Used

- Xcode
- CoreML
- CareKit
- ResearchKit
- HealthKit
- PyTorch
- Swift (iOS and watchOS development)

  
<img width="96" alt="image" src="https://github.com/user-attachments/assets/282e2ab7-77f4-4fcd-b41f-c743e2e90143"> <img width="440" alt="image" src="https://github.com/user-attachments/assets/c6140151-ff89-4995-b260-5e4c8a047d59"> <img width="107" alt="image" src="https://github.com/user-attachments/assets/94040612-87fc-4dec-b381-f1e3121f1915">




## Methodology

* The methodology involved collecting biometric data through HealthKit and organizing it with CareKit.
* The data was analyzed using machine learning models integrated via Core ML.
* To present the data and predictions effectively, an intuitive app was developed using SwiftUI.

## Pseudo Data Generation

Due to limited access to real patient data, we generated pseudo data to train and evaluate our model. Here's an overview of our data generation process:

1. **Tool Used:** Mockaroo for synthetic data generation
2. **Data Attributes:** Included health metrics like heart rate, blood pressure, BMI, active energy, and sleep quality
3. **Formulas and Correlations:** Established realistic correlations based on research and domain knowledge
4. **Key Features:** Selected six key features for the model based on relevance and impact on distress prediction


## Formulas and Correlations:

To simulate realistic distress levels, we established correlations based on research and domain knowledge:
Heart Rate & Blood Pressure: For every 10 bpm increase in resting heart rate, systolic BP might increase by 3-5 mmHg.
* Body Fat Percent & BMI: Approximately 0.7 to 0.8 correlation coefficient.
* Active Energy & Steps: Correlation coefficient around 0.8 to 0.9.
* Sleep Habits & Sleep Quality: Correlation coefficient approximately 0.5 to 0.7.
* Cardio Fitness & Resting Heart Rate: Negative correlation around -0.6 to -0.7.
* Heart Rate Variability & Stress Level: Negative correlation approximately -0.4 to -0.6.

We refined the pseudo data to achieve meaningful correlations between variables. This helped in simulating real-life distress scenarios and improving model performance.

<img width="618" alt="image" src="https://github.com/user-attachments/assets/d559b900-7fe5-408a-85d9-5279b8b2c739">


## Example
https://github.com/user-attachments/assets/704a3645-613f-486c-8282-15453fe6bc13



<img width="810" alt="image" src="https://github.com/user-attachments/assets/b6a2621c-85c2-46d0-871f-176d7faa173a">

## Data Preprocessing

* Import data into Dataframe via Python Pandas Library
* Normalize data via MinMaxScalar transformation
* Translate data to PyTorch Dataset
* Translate dataset into PyTorch Dataloader

## Model Selection

Multiple model types were attractive to and provided high accuracies on the pseudo data:

* Linear Regression
* Logistic Regression
* KNN
* Random Forest
* Other models

We selected Logistic Regression due to its Binary Classification which yielded the highest accuracy of 90.5%.

Additionally we performed a GridSearchCV to find the best parameters for the selected model (tol, C, Solver, max_iter).

## Converted Model to Core ML for easy importation to Assuage App Software (Xcode)

We utlized Core ML to easily translate the model from PyTorch to Core ML which is easily readable in Xcode (Swift).
<img width="432" alt="image" src="https://github.com/user-attachments/assets/e8373066-8382-4cb2-b145-b1e836f908bb">


## Usage instructions
<!--
Give details on how to install fork and install your project. You can get all of the python dependencies for your project by typing `pip3 freeze requirements.txt` on the system that runs your project. Add the generated `requirements.txt` to this repo.
-->
1. Fork this repo
2. Change directories into your project
3. On the command line, type `pip3 install requirements.txt`


## Questions 
<!--
-->
Please feel free to contact
* Rabiat Sadiq  - Robbiahsadiq@gmail.com
* Emiliano Gonzalez - egonzalez92@gatech.edu
* Emily Mojica - melymojica@icloud.com
* Rodrigo Aguilar B - Aguilarb@usc.edu
