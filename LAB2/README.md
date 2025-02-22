# Future Functionality Component Diagram for Kursach V8 2.5L Twin-Turbo GT3S

This document provides an overview of the system architecture as depicted in the component diagram. The diagram illustrates both the current components and planned future functionalities, focusing on data processing, machine learning model training, inference, and continuous improvement through monitoring and retraining.

## Diagram Overview

The diagram is generated using PlantUML and represents the following key components:

- **Obfuscated-MalMem2022.csv (Raw Data):**
  Represented as a database, this file contains the raw, obfuscated malware data that serves as the initial input to the system.

- **CourseWork_ver7.ipynb (Data Preprocessing):**  
  A component that preprocesses the raw data. It cleans and transforms the data, making it ready for model training.

- **malware_detection_model.h5 (ML Model):**  
  This component represents the machine learning model (stored as an H5 file) that is trained on the preprocessed data.

- **Inference Engine:**  
  Responsible for loading the trained model and providing real-time predictions based on new input data.

- **User Interface / API:**  
  Provides an interface through which users or external systems can send prediction requests and, optionally, feedback for further improvements.

- **Data Storage (Processed Data & Logs):**  
  A component that saves the processed data and logs generated during data preprocessing, useful for audits and further model training.

- **Feedback Loop (Model Retraining):**  
  Depicted as a database, this component handles retraining of the model when triggered by alerts or user feedback, ensuring the model stays up-to-date.

- **Monitoring & Logging:**  
  Represented as a process, this component logs the details of predictions and overall system performance, triggering retraining alerts when necessary.
![Components](Component_Diagram.png)
## Data Flow

The data flows between components are as follows:

1. **Raw Data Ingestion:**  
   - **Obfuscated-MalMem2022.csv** feeds raw data into the **CourseWork_ver7.ipynb** component.

2. **Data Preprocessing:**  
   - The **Notebook** component processes the raw data.
   - Processed data is saved in **Data Storage**.
   - Processed data is also used to train or update the **ML Model**.

3. **Model Training and Inference:**  
   - The **ML Model** is updated/trained using the processed data.
   - The trained model is loaded by the **Inference Engine** to serve predictions.

4. **User Interaction:**  
   - **User Interface / API** sends prediction requests to the **Inference Engine**.
   - Optionally, it also sends user feedback to the **Feedback Loop**.

5. **Monitoring and Feedback Loop:**  
   - The **Inference Engine** logs prediction details to **Monitoring & Logging**.
   - The **Monitoring & Logging** process triggers retraining alerts to the **Feedback Loop**.
   - The **Feedback Loop** updates the **ML Model** with new training based on these alerts and any provided user feedback.


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
