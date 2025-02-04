
# Wind Turbine Power Output Prediction Using LSTM

<p align="center">
    <img width="1150" src="Images_Ref/Logo_06.png" alt="Logo_01">
</p>


<p align="justify">
This repository contains a project to predict the power output of wind turbines based on historical data. The project utilizes the Wind Turbine SCADA Dataset from Kaggle and employs Long Short-Term Memory (LSTM) networks to model and forecast power output using multivariate time series data.
</p>


## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
- [Model Architecture](#model-architecture)
- [Setup Instructions](#setup-instructions)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Overview
Wind turbines are a key source of renewable energy, but their power output depends on multiple variables, such as wind speed, temperature, and rotor speed. Predicting power output can improve efficiency, stability, and integration with the power grid.

This project leverages LSTM models to capture temporal patterns and relationships between variables to predict turbine power output with higher accuracy.

## Dataset
The dataset used in this project is the Wind Turbine SCADA Dataset available on Kaggle. It contains measurements recorded every 20 minutes, including:
- Wind Speed (m/s)
- Wind Direction (°)
- Ambient Temperature (°C)
- Turbine Power Output (kW)

### Preprocessing
- Handled missing rows using KNN Imputation.
- Reconstructed missing timestamps and scaled all features using Min-Max scaling.
- Created sequences for LSTM training with a time window of 24 steps (8 hours).

## Project Workflow
The project follows this structured workflow:

### Data Preprocessing
- Imputation of missing values using KNNImputer.
- Scaling features using MinMaxScaler.
- Sequence generation for LSTM input.

### Feature Engineering
- Added time-based features (e.g., hour of the day, day of the week).
- Generated rolling statistics (e.g., moving averages).

### Model Building
Built and trained an LSTM model with multiple layers:
- 128 units in the first layer
- 64 units in the second layer
- 32 units in the third layer
- Added Dropout and Batch Normalization for better generalization.

### Model Evaluation
- Used Mean Squared Error (MSE) to evaluate performance.
- Visualized predictions against actual values.

## Model Architecture
The LSTM model architecture is as follows:

| Layer         | Units | Activation |
|---------------|-------|------------|
| LSTM          | 128   | ReLU       |
| LSTM          | 64    | ReLU       |
| LSTM          | 32    | ReLU       |
| Dense         | 64    | ReLU       |
| Dense (Output)| 1     | Linear     |

## Setup Instructions

### Requirements
- Python 3.9+
- TensorFlow 2.5+
- NumPy
- pandas
- scikit-learn
- matplotlib

### Installation
Clone the repository:
```bash
git clone https://github.com/your-username/wind-turbine-power-prediction.git
cd wind-turbine-power-prediction
```

Install the required libraries:
```bash
pip install -r requirements.txt
```

Download the dataset:
- Download the Wind Turbine SCADA Dataset from Kaggle.
- Place the dataset file (`dataset.csv`) in the project directory.

Run the preprocessing script:
```bash
python preprocess.py
```

Train the model:
```bash
python train_model.py
```

## Results
- Train/Test Split: 80% training, 20% testing.
- Error Metrics:
    - Mean Squared Error (MSE): value
    - Mean Absolute Error (MAE): value

Below is a sample plot of Actual vs Predicted Power Output:

![Actual vs Predicted Power Output](path/to/plot.png)

## Future Improvements
- Incorporate Attention Mechanisms: To allow the model to focus on the most important time steps.
- Feature Selection: Explore advanced methods to select the most relevant features.
- Model Optimization: Use hyperparameter tuning (e.g., Keras Tuner) to improve model performance.
- Bidirectional LSTMs: Capture both past and future dependencies for better predictions.
- Deployment: Deploy the trained model as a REST API using Flask or FastAPI.

## License
This project is licensed under the MIT License.

## Acknowledgments
- Dataset: Wind Turbine SCADA Dataset from Kaggle.
- Tools: TensorFlow, scikit-learn, pandas, and matplotlib.

Feel free to reach out with feedback or questions. Contributions are welcome!

## Notes
- Replace `your-username` with your GitHub username in the clone link.
- Add any missing MSE/MAE values and a sample plot of results.
- Make sure you create the referenced scripts (`preprocess.py`, `train_model.py`) or provide a Jupyter notebook if that’s how you organized your project.



---
