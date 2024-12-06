# AI-Powered Safety Heatmap

This project provides a web application that enables users to input safety concerns and visualize interactive **heatmaps** of safe and unsafe areas. It also features a **voice-activated SOS system** that notifies nearby police stations in emergencies. Users can explore area-specific safety information based on real-time and historical data to plan their visits with better safety measures.

---

## Features
- **Interactive Safety Heatmap**: Generates heatmaps based on user input and historical data, highlighting safe and unsafe areas.
- **Voice-Activated SOS**: Activates the SOS system via voice commands and alerts nearby police stations in emergencies.
- **Area Safety Insights**: Enables users to explore and assess the safety of a location before visiting.
- **AI Prediction**: Predicts the crime rate till a year analyzing the record of previous data of that region.

---

## Table of Contents
1. [Installation](#installation)
2. [Usage](#usage)
3. [API Endpoints](#api-endpoints)
4. [Backend Architecture](#backend-architecture)

---

## Installation

### Prerequisites
Ensure you have the following installed:
- **Python 3.x** (preferably Python 3.7+)
- **pip** (Python package manager)

### Steps to Install

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/repository-name.git
   cd repository-name


## Installation

### Prerequisites
Make sure you have the following installed:
- **Python 3.x** (preferably Python 3.7+)
- **pip** (Python package manager)

### Steps to install

1. Clone this repository:

   ```bash
   git clone git@github.com:linkon63/team-hello-world-hackathon-backend.git
   cd repository-name

2.  manually install the dependencies:
    ```bash
    pip install flask scikit-learn numpy pandas
    
## Usage

### 1. Running the Flask App

- To start the Flask server and run the API, use the following command:
   ```bash
   python app.py

### 2. Testing the API with Postman
- You can use Postman to test the API by sending a POST request to the /predict endpoint.

- URL: http://127.0.0.1:5000/predict

- Method: POST

- Headers:

- Content-Type: application/json
- Request Body (JSON):
{
  "age": 17,
  "test_score": 89,
  "high_school_percentage": 77
}

- Example Response:
{
  "admission_status": "Admitted"
}
## API Endpoints
- /predict
- Method: POST
- Description: Predicts admission status based on the provided features.
- Request Body (JSON):

## Backend Architechture

- The model uses Age, Test Score, and High School Percentage to predict whether a student will be admitted. The model was trained on historical admission data.