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

![Alt text](path/to/image.png)
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

## Pseudo Data Generation

Due to limited access to real patient data, we generated pseudo data to train and evaluate our model. Here's an overview of our data generation process:

1. **Tool Used:** Mockaroo for synthetic data generation
2. **Data Attributes:** Included health metrics like heart rate, blood pressure, BMI, active energy, and sleep quality
3. **Formulas and Correlations:** Established realistic correlations based on research and domain knowledge
4. **Key Features:** Selected six key features for the model based on relevance and impact on distress prediction



## Usage instructions
<!--
Give details on how to install fork and install your project. You can get all of the python dependencies for your project by typing `pip3 freeze requirements.txt` on the system that runs your project. Add the generated `requirements.txt` to this repo.
-->
1. Fork this repo
2. Change directories into your project
3. On the command line, type `pip3 install requirements.txt`
4. ....
