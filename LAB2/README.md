# Component Diagram for Kursach V8 2.5L Twin-Turbo GT3S

This document provides an overview of the component diagram for the Kursach V8 2.5L Twin-Turbo GT3S project. The diagram illustrates both the current system components and planned future enhancements aimed at improving scalability, maintainability, and continuous improvement.

## Component Diagram Overview

The diagram is divided into two groups of components:

1. **Existing Components:**
   - **Obfuscated-MalMem2022.csv (Raw Data):**  
     This file contains raw, obfuscated malware data used as the input for the system.
   - **CourseWork_ver7.ipynb (Data Preprocessing):**  
     A Jupyter Notebook responsible for cleaning, preparing, and transforming raw data into a format suitable for training.
   - **malware_detection_model.h5 (ML Model):**  
     The machine learning model trained on the processed data.
   - **Inference Engine:**  
     Loads the trained model to perform predictions on incoming data.
   - **User Interface / API:**  
     Provides an interface for users or external systems to send prediction requests and, optionally, provide feedback.
   - **Data Storage (Processed Data & Logs):**  
     Stores the processed data and logs generated during preprocessing, which can be used for audits or further training.
   - **Monitoring & Logging:**  
     Captures detailed logs of predictions and system performance, facilitating error tracking and performance monitoring.
   - **Feedback Loop (Model Retraining):**  
     Uses monitoring alerts and user feedback to trigger retraining of the model, ensuring that the system remains effective as new data becomes available.

# Detailed Component Descriptions

Obfuscated-MalMem2022.csv (Raw Data):
Serves as the entry point of data. It contains raw, obfuscated information that forms the basis of the analysis and training processes.

CourseWork_ver7.ipynb (Data Preprocessing):
A Jupyter Notebook that processes the raw data. It cleans, transforms, and extracts features necessary for effective model training. It also saves the processed data for record-keeping.

malware_detection_model.h5 (ML Model):
The machine learning model that is trained using the processed data. This model is updated over time to improve prediction accuracy.

Inference Engine:
Uses the trained ML model to make predictions on new data. It receives prediction requests from the User Interface / API.

User Interface / API:
Provides a user-facing endpoint for submitting data for prediction and optionally feeding back performance insights.

Data Storage (Processed Data & Logs):
Stores the outputs of the data preprocessing stage as well as logs generated during system operation. This is crucial for audits, debugging, and retraining.

Monitoring & Logging:
Collects detailed logs and monitors system performance. This component generates alerts when the system's performance degrades or anomalies are detected.

Feedback Loop (Model Retraining):
Uses alerts from the monitoring system and user feedback to trigger retraining of the ML model, ensuring that the model remains current and effective.

![Component_Diagram](Component_Diagram.png)
# Data Flow Overview

Raw Data Input:
The system starts with the Obfuscated-MalMem2022.csv component, which supplies raw malware data to the CourseWork_ver7.ipynb component.
Data Preprocessing:
The notebook processes the raw data, transforming it into a format suitable for model training. The processed data is also saved into the Data Storage component.
Model Training/Update:
The preprocessed data is used to train or update the machine learning model stored as malware_detection_model.h5.
Inference:
The trained model is loaded by the Inference Engine to perform predictions. Prediction requests are received via the User Interface / API.
Monitoring and Feedback:
The Inference Engine sends log data to the Monitoring & Logging component, which in turn triggers the Feedback Loop for retraining the model based on performance alerts and user feedback.


# Deployment Diagram for Kursach V8 2.5L Twin-Turbo GT3S (Future Functionality)

This document provides an overview of the deployment architecture for the Kursach V8 2.5L Twin-Turbo GT3S project. The diagram illustrates how various components are distributed across physical nodes (servers) and details the interactions between them. It includes both core components and additional modules planned for future functionality.

## Overview

The system is deployed across four main servers:

- **Data Processing Server:**  
  Hosts the raw data and data preprocessing artifacts.
  
- **Model & Inference Server:**  
  Contains the trained machine learning model, the inference engine, and the feedback loop for model retraining.
  
- **Data Storage & Monitoring Server:**  
  Manages storage for processed data and logs, and monitors system performance.
  
- **Web Server:**  
  Provides the user interface or API endpoints for external interactions.

## Components Description

### Data Processing Server
- **Obfuscated-MalMem2022.csv (Raw Data):**  
  Contains the raw, obfuscated malware data.
- **CourseWork_ver7.ipynb (Data Preprocessing):**  
  A Jupyter Notebook responsible for cleaning, transforming, and preparing raw data for model training.

### Model & Inference Server
- **malware_detection_model.h5 (ML Model):**  
  The trained machine learning model used for making predictions.
- **Inference Engine:**  
  Loads the ML model and handles real-time prediction requests.
- **Feedback Loop (Model Retraining):**  
  Triggers model retraining based on performance metrics and user feedback to ensure the model stays current.

### Data Storage & Monitoring Server
- **Data Storage (Processed Data & Logs):**  
  Archives processed data and logs for auditing purposes and to support future retraining.
- **Monitoring & Logging:**  
  Monitors prediction details and overall system performance, generating alerts as needed.

### Web Server
- **User Interface / API:**  
  Provides endpoints for users to submit prediction requests and optionally send feedback to enhance model performance.

## Data Flow and Interactions

1. **Raw Data Processing:**
   - The `Obfuscated-MalMem2022.csv` file feeds raw data into the `CourseWork_ver7.ipynb` for preprocessing.
   
2. **Data Archiving and Model Training:**
   - The preprocessed data and logs are saved to the `Data Storage` component.
   - Processed data is used to train or update the `malware_detection_model.h5`.

3. **Inference:**
   - The trained model is loaded by the `Inference Engine`, which provides real-time predictions.
   - User prediction requests are received via the `User Interface / API`.

4. **Monitoring and Feedback:**
   - The `Inference Engine` sends prediction details to the `Monitoring & Logging` component.
   - Alerts from monitoring trigger the `Feedback Loop`, which then initiates model retraining.
   - Additionally, user feedback can be sent from the UI to the feedback loop to further refine the model.

## Future Functionality Considerations

- **Continuous Monitoring:**  
  The system will continuously monitor performance and log detailed prediction data to facilitate proactive maintenance.
  
- **Automated Retraining:**  
  The feedback loop ensures the model is retrained automatically when performance issues or data drift are detected.
  
- **Data Archiving:**  
  Long-term storage of processed data and logs supports compliance, auditing, and iterative improvements to the model.

![Component_Diagram](Deployment_Diagram.png)
## Conclusion

This deployment diagram outlines the physical distribution and interactions of the components within the Kursach V8 2.5L Twin-Turbo GT3S project. It provides a clear view of how raw data is processed, how the model is trained and deployed, and how the system integrates future functionality such as monitoring and automated retraining, ensuring scalability and robustness in real-world operations.
