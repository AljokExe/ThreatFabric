
# Threat Fabric MLOPS Challenge

This repository contains the solution to the Threat Fabric MLOPS Challenge, which involves building and deploying a machine learning model for user recognition based on keystroke data. The challenge is divided into two parts: Model Building (Part 1) and Model Deployment (Part 2).

## Part 1 - Model Building

### Dataset
- The provided dataset, `Train_keystroke.csv`, contains keystroke data from 110 users.
- Each user was asked to type a 13-character string eight times, and the dataset contains information on keypress time and key-release time for each key.

### Feature Extraction
- To build an effective model, four informative features were extracted from the raw data:
  - Hold Time (HT)
  - Press-Press Time (PPT)
  - Release-Release Time (RRT)
  - Release-Press Time (RPT)
- These features were generated for each pair of consecutive keys in the dataset.

### Feature Summary
- For each row in the dataset, the mean and standard deviation of the four features were calculated, resulting in eight features per row.

### Model Training
- Three machine learning models were trained using the extracted features and UserID as the class label:
  1. Support Vector Machine (SVM)
  2. Random Forest (RF)
  3. XGBoost (XGB)
- Default parameters were used for each classifier, and no feature selection or cross-validation was performed.

### Model Storage
- The trained models were stored on the local device.

## Part 2 - Model Deployment

### API Deployment
- The three trained models (SVM, RF, and XGB) were deployed as a single REST API for real-time predictions.

### Input Format
- The API accepts input data in JSON format with the following structure:
  ```json
  {
    "Model": "RF",
    "HT": {
      "Mean": 48.43,
      "STD": 23.34
    },
    "PPT": {
      "Mean": 120.43,
      "STD": 37.41
    },
    "RRT": {
      "Mean": 124.43,
      "STD": 45.34
    },
    "RPT": {
      "Mean": 132.56,
      "STD": 47.12
    }
  }
  ```

### Model Selection
- The API loads the relevant model based on the "Model" value in the input and predicts the UserID, returning the result.

## Platform for Deployment

Choose one of the following platforms for model deployment:

1. **AWS Platform**
   - Deploy the model on the AWS cloud.
   - Provide a complete solution using AWS services.

2. **Microsoft Azure Platform**
   - Deploy the model on the Microsoft Azure cloud.
   - Provide a complete solution using Azure services.

## Deliverables

1. A complete Jupyter notebook file with detailed descriptions for Part 1 (Model Building).
2. For Part 2 (Model Deployment) on your chosen platform (AWS or Azure):
   a. A comprehensive diagram showing various modules and services used with their internal relationships.
   b. A detailed step-by-step instruction guide on how to develop the deployment pipeline and serve the model API.
   c. Any required scripts with sufficient code comments in Python.

