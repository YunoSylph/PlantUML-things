# 1. State and Transition Diagram for Kursach V8 2.5L Twin-Turbo GT3S

This document explains the **State and Transition Diagram** for the Kursach V8 2.5L Twin-Turbo GT3S project, including planned future functionality.

---

## Overview
The state diagram illustrates the various stages that the system goes through during its lifecycle. It includes:

- **Data Ingestion Process**
- **Model Training Process**
- **Inference Process**
- **Monitoring and Feedback Process**

This diagram emphasizes both the main workflow and the future functionality enhancements such as automated monitoring and retraining.

---

## State Descriptions

### **1. Data Ingestion**
This state handles the preparation and preprocessing of raw data before it is sent for model training.

- **`Data_Loading`** → Loads raw data from the source (e.g., CSV file).
- **`Data_Cleaning`** → Cleans the data by handling null values, anomalies, and formatting.
- **`Feature_Extraction`** → Extracts key features relevant to malware detection.
- **`Data_Stored`** → Saves the processed data for later use in training.

> **Transition:** The state moves to `Model_Training` once the processed data is saved.

---

### **2. Model Training**
This state manages the process of training the machine learning model.

- **`Data_Preparation`** → Prepares data by formatting it into model-ready input.
- **`Model_Training_In_Progress`** → The model is actively being trained with the prepared data.
- **`Model_Training_Completed`** → Marks the model as "Ready" for deployment once training is finished.

> **Transition:** The state moves to `Inference_Process` when the model is successfully trained.

---

### **3. Inference Process**
This state handles prediction requests from the User Interface / API.

- **`Awaiting_Requests`** → The system is waiting for incoming prediction requests.
- **`Prediction_In_Progress`** → The system processes data and generates predictions.
- **`Prediction_Completed`** → Sends the prediction results back to the UI/API.

> **Transition:** The system logs the prediction data and moves to `Monitoring_Feedback`.

---

### **4. Monitoring & Feedback**
This state ensures system reliability by tracking performance and triggering retraining when required.

- **`Monitoring_Active`** → Monitors system behavior, prediction accuracy, and overall performance.
- **`Performance_Alert`** → An alert is generated if model performance degrades or anomalies are detected.
- **`Feedback_Triggered`** → Initiates the feedback loop for model retraining.

> **Transition:** Retraining sends data back to `Model_Training`.

---

## System Transitions
### Key Transitions Between States
- **`Data_Ingestion → Model_Training`** → When processed data is saved, the model training process begins.
- **`Model_Training → Inference_Process`** → After successful training, the model is deployed for inference.
- **`Inference_Process → Monitoring_Feedback`** → Logs prediction details for monitoring and quality assurance.
- **`Monitoring_Feedback → Model_Training`** → If performance degrades or user feedback suggests issues, retraining is triggered.

![Component_Diagram](State_and_Transition.png)

## PlantUML Code:
@startuml
title State and Transition Diagram for Kursach V8 2.5L Twin-Turbo GT3S

[*] --> Data_Ingestion : System Initialized

' ----------------------
' Data Processing States
' ----------------------
state Data_Ingestion {
    [*] --> Data_Loading
    Data_Loading --> Data_Cleaning : Raw Data Loaded
    Data_Cleaning --> Feature_Extraction : Data Cleaned
    Feature_Extraction --> Data_Stored : Features Extracted
    Data_Stored --> [*] : Processed Data Saved
}

' ----------------------
' Model Training States
' ----------------------
state Model_Training {
    [*] --> Data_Preparation
    Data_Preparation --> Model_Training_In_Progress : Data Ready
    Model_Training_In_Progress --> Model_Training_Completed : Model Trained
    Model_Training_Completed --> [*] : Model Ready
}

' ----------------------
' Inference States
' ----------------------
state Inference_Process {
    [*] --> Awaiting_Requests
    Awaiting_Requests --> Prediction_In_Progress : Prediction Request Received
    Prediction_In_Progress --> Prediction_Completed : Prediction Made
    Prediction_Completed --> [*] : Results Sent to UI
}

' ----------------------
' Monitoring and Feedback Loop
' ----------------------
state Monitoring_Feedback {
    [*] --> Monitoring_Active
    Monitoring_Active --> Performance_Alert : Performance Degradation Detected
    Performance_Alert --> Feedback_Triggered : Feedback Triggered
    Feedback_Triggered --> Model_Training_In_Progress : Model Retraining
}

' ----------------------
' System Transitions
' ----------------------
Data_Ingestion --> Model_Training : Processed Data Ready
Model_Training --> Inference_Process : Model Deployed
Inference_Process --> Monitoring_Feedback : Log Data Captured
Monitoring_Feedback --> Model_Training : Retraining Triggered
Monitoring_Feedback --> [*] : System Stable

@enduml


---
The diagram integrates key future functionalities to improve system performance and scalability:
✅ **Automated Monitoring** to track prediction accuracy and detect performance degradation.  
✅ **Feedback Loop** for automatic model retraining based on performance metrics or user feedback.  
✅ **Data Flow Optimization** ensures data consistency throughout the pipeline.  
✅ **System Stability Focus** distinguishes stable states from those requiring intervention.

---
This state and transition diagram effectively illustrates the data flow, training pipeline, prediction process, and system monitoring of the **Kursach V8 2.5L Twin-Turbo GT3S** project. The inclusion of future functionality ensures the system remains adaptive and efficient over time.

For developers, this diagram provides a clear roadmap for integrating additional functionality while maintaining robust system behavior.


# 2. Activity Diagram for Kursach V8 2.5L Twin-Turbo GT3S (With Planned Functionality)

This document explains the **Activity Diagram** for the **Kursach V8 2.5L Twin-Turbo GT3S** project, including core functionalities and planned future enhancements. The diagram outlines the system’s workflow, from data processing to prediction, with an integrated monitoring and feedback loop for continuous improvement.

---

## Overview
The diagram captures the following key processes:
- **Data Ingestion Process**
- **Model Training Process**
- **Prediction Process**
- **Monitoring and Feedback Loop**
- **User Feedback Integration**

This structured approach ensures clarity in system behavior and enables efficient maintenance and scaling.

---

## Detailed Explanation of Each Process

### **1. Data Ingestion Process**
This phase involves preparing the raw malware data before sending it to model training.

- **Load Raw Data:**  
   Imports data from the `.csv` file or other data sources.
- **Clean Data:**  
   Cleans the data by handling missing values, removing noise, and normalizing data for consistency.
- **Extract Features:**  
   Identifies and extracts relevant features required for training the machine learning model.
- **Save Processed Data:**  
   Stores the processed data for future use in both training and prediction.

> **Decision Point:**  
If processed data is successfully prepared, it’s saved in the data storage system. Otherwise, the process stops.

---

### **2. Model Training Process**
This phase trains the malware detection model using processed data.

- **Prepare Data for Training:**  
   Organizes and structures data to align with model training requirements.
- **Train Model:**  
   Executes the machine learning model training process.
- **Save Trained Model:**  
   Stores the trained model for later use during inference.

> **Decision Point:**  
If the model is successfully trained, it is deployed for prediction. Otherwise, the process stops.

---

### **3. Prediction Process**
This stage handles the model's deployment for real-time prediction.

- **Wait for Prediction Request:**  
   The system remains idle until it receives a request from the UI/API.
- **Receive Prediction Request:**  
   Captures prediction requests sent by users or applications.
- **Load Trained Model:**  
   Loads the latest trained model to perform prediction.
- **Generate Prediction:**  
   Uses the loaded model to predict malware behavior or characteristics.
- **Send Prediction Result:**  
   Sends the generated result to the UI/API for user visibility.

> **Logging Predictions:**  
The system logs prediction data to support performance analysis and monitoring.

---

### **4. Monitoring and Feedback Loop**
The monitoring system ensures the model's performance remains stable and optimal.

- **Monitor System Performance:**  
   Tracks prediction accuracy, latency, and system stability.
- **Performance Degrades? (Decision Point):**  
   - If **YES**, an alert is triggered, prompting retraining.
   - If **NO**, the system continues monitoring without further action.
- **Generate Alert:**  
   Notifies the system that the model’s performance has degraded.
- **Trigger Feedback Loop:**  
   Initiates the retraining process to improve model performance.
- **Initiate Model Retraining:**  
   Launches the model retraining process using updated data.
- **Update Model with New Training:**  
   Replaces the previous model with the newly trained one.

---

### **5. User Feedback Integration**
User feedback plays a crucial role in improving model accuracy and reliability.

- **Receive User Feedback:**  
   Captures user feedback indicating incorrect or suspicious predictions.
- **Feedback Requires Retraining? (Decision Point):**  
   - If **YES**, the feedback triggers model retraining.
   - If **NO**, the feedback is logged for future analysis.

---

## Key Future Functionalities Integrated
✅ **Automated Performance Monitoring:** Ensures degraded performance is automatically detected.  
✅ **Feedback Loop for Model Improvement:** Ensures real-time adaptation to data changes.  
✅ **Data Storage Optimization:** Ensures processed data and logs are archived securely for auditing and retraining.  
✅ **Continuous System Tracking:** Maintains system reliability and prediction accuracy.  
✅ **User Feedback Handling:** Ensures system behavior evolves to improve accuracy based on user insights.

---

## Key Transition Points
- **Processed Data Ready?** — Ensures data meets quality standards before proceeding to model training.
- **Model Ready?** — Ensures only stable and optimized models are deployed for inference.
- **Performance Degrades?** — Automatically triggers model retraining when performance issues are detected.
- **Feedback Requires Retraining?** — Ensures the system adapts to changing data patterns or user insights.

---

![Component_Diagram](Activity_diagram.png)

## PlantUML Code:
@startuml
title Activity Diagram for Kursach V8 2.5L Twin-Turbo GT3S (With Planned Functionality)

start

' ---------------------------
' Data Ingestion Process
' ---------------------------
:Load Raw Data;
:Clean Data;
:Extract Features;
:Save Processed Data;

' Decision for Data Flow
if (Processed Data Ready?) then (Yes)
    :Store Data in Data Storage;
else (No)
    stop
endif

' ---------------------------
' Model Training Process
' ---------------------------
:Prepare Data for Training;
:Train Model;
:Save Trained Model;

' Decision for Model Readiness
if (Model Ready?) then (Yes)
    :Deploy Model for Prediction;
else (No)
    stop
endif

' ---------------------------
' Inference Process
' ---------------------------
:Wait for Prediction Request;
:Receive Prediction Request;
:Load Trained Model;
:Generate Prediction;
:Send Prediction Result;

' Logging Predictions for Monitoring
:Log Prediction Data;

' ---------------------------
' Monitoring and Feedback Loop
' ---------------------------
:Monitor System Performance;
if (Performance Degrades?) then (Yes)
    :Generate Alert;
    :Trigger Feedback Loop;
    :Initiate Model Retraining;
    :Update Model with New Training;
else (No)
    :Continue Monitoring;
endif

' ---------------------------
' User Feedback Integration
' ---------------------------
:Receive User Feedback;
if (Feedback Requires Retraining?) then (Yes)
    :Trigger Feedback Loop;
    :Initiate Model Retraining;
    :Update Model with New Training;
endif

stop

@enduml


This detailed **Activity Diagram** effectively visualizes the workflow of your **Kursach V8 2.5L Twin-Turbo GT3S** project. By combining data processing, training, prediction, and monitoring, this diagram reflects a robust and scalable system architecture.

With planned functionality like automated monitoring, feedback handling, and retraining, this system is designed to stay adaptive, efficient, and high-performing over time.

This design offers clear decision points, efficient data flow, and flexible enhancement paths for future development. 🚀
