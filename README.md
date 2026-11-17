# California Housing – Model as a Service

**Machine Learning Model Deployment using Flask and Docker**

## 1. Project Overview

This project demonstrates the development and deployment of a Machine Learning model as a Model as a Service (MaaS) using Flask and Docker.

The system uses the California Housing dataset to train a Random Forest Regressor model for predicting median house values based on housing and demographic features.

Users can input housing information through a web interface and receive a predicted house value. The system also provides a REST API for accessing the prediction model.

## 2. Objectives

- Understand the concept of Model as a Service.
- Develop a Flask web application for Machine Learning predictions.
- Use Docker to create a consistent application environment.
- Deploy and publish the project on GitHub.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Python 3.11 | Main programming language |
| Flask | Web application and REST API |
| Scikit-learn | Machine Learning |
| Random Forest Regressor | Prediction model |
| California Housing | Training dataset |
| NumPy | Numerical computation |
| Joblib | Model serialization |
| Gunicorn | Production WSGI server |
| Docker | Application containerization |

## 4. Machine Learning Model

**Model:** Random Forest Regressor

**Dataset:** California Housing Dataset

The model is trained using eight input features:

| Feature | Description |
|---|---|
| MedInc | Median income |
| HouseAge | Average house age |
| AveRooms | Average rooms per household |
| AveBedrms | Average bedrooms per household |
| Population | Block group population |
| AveOccup | Average household occupancy |
| Latitude | Geographic latitude |
| Longitude | Geographic longitude |

The model predicts the median house value in units of $100,000.

## 5. Project Structure

```text
ml_service/
│
├── app.py
├── train_model.py
├── requirements.txt
├── Dockerfile
│
├── templates/
│   └── main.html
│
├── model/
│   └── model.pkl
│
└── screenshots/
    └── prediction-success.png
```

Note: The `model/` directory and trained model file are generated automatically when the model is trained.

## 6. Installation and Setup

### Prerequisites

- Python 3.11
- pip
- Docker Desktop
- Git

### Clone the Repository

```bash
git clone https://github.com/ARNAY9/394_ml_service
cd ml_service
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

## 7. Build and Run

### 7.1 Train the Machine Learning Model

Run the following command:

```bash
python train_model.py
```

The trained model will be saved to:

```text
model/model.pkl
```

### 7.2 Run Flask Application

```bash
python app.py
```

Open the browser:

http://127.0.0.1:5000/

### 7.3 Build Docker Image

Build the Docker image using:

```bash
docker build -t ds-ml-service .
```

### 7.4 Run Docker Container

```bash
docker run --rm -p 5000:5000 ds-ml-service
```

Open the web application:

http://127.0.0.1:5000/

The application will be available on port 5000.

## 8. API Endpoints

### Health Check

**Endpoint:** `GET /health`

Checks whether the application is running.

Example response:

```json
{
  "ok": true,
  "features": [
    "MedInc",
    "HouseAge",
    "AveRooms",
    "AveBedrms",
    "Population",
    "AveOccup",
    "Latitude",
    "Longitude"
  ]
}
```

### House Price Prediction

**Endpoint:** `POST /predict`

Accepts eight housing features in JSON format.

Example request:

```json
{
  "features": [8.3, 25.0, 6.0, 1.0, 1200, 3.0, 34.2, -118.3]
}
```

Example response:

```json
{
  "prediction": 4.03
}
```

The predicted value is approximately $403,000.

## 9. Prediction Result

The following screenshot demonstrates the successful prediction process through the Flask web application.

![Prediction Result](screenshots/prediction-success.png)

## 10. Docker Commands

Build the image:

```bash
docker build -t ds-ml-service .
```

Run the container:

```bash
docker run --rm -p 5000:5000 ds-ml-service
```

Stop the container:

Press `Ctrl + C` in the terminal.

## 11. Expected Results

- The Machine Learning model can be trained successfully.
- The Flask web application displays a housing prediction form.
- Users can enter housing features and receive prediction results.
- The `/health` endpoint returns application status.
- The `/predict` endpoint returns predicted house values.
- The application can be built and executed using Docker.

## 12. Author

Developed as part of the CPE312 course assignment.

**Project:** Model as a Service using Flask and Docker
