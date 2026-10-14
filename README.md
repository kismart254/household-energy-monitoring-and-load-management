# \# Household Energy Monitoring and Automated Load Management Using KNN

# 

# \##  Project Overview

# 

# This project implements a machine learning-based system for household energy monitoring and automated load management using the \*\*K-Nearest Neighbors (KNN)\*\* algorithm.

# 

# The system analyses electrical measurements to classify household energy consumption and determine appropriate load-management actions when electricity usage becomes unusually high. It is designed to help improve energy management by identifying high-consumption conditions and simulating the disconnection of selected non-essential appliances while keeping essential loads operational.

# 

# The project is implemented in Python using a Jupyter Notebook and Scikit-learn.

# 

# \## Objectives

# 

# \- Monitor and analyse household electricity consumption.

# \- Classify energy consumption into different operating conditions using KNN.

# \- Determine suitable load-management actions based on predicted consumption conditions.

# \- Simulate automated load shedding for selected non-essential appliances.

# \- Apply machine learning techniques to a practical electrical engineering problem.

# 

# \##  How the System Works

# 

# The system uses two KNN classification models.

# 

# \### 1. Energy Consumption Classification

# 

# The first KNN model classifies household electricity consumption into three categories:

# 

# \- \*\*Normal:\*\* Electricity consumption is within the defined normal range.

# \- \*\*Unusual\_High:\*\* Electricity consumption is elevated and requires non-essential load management.

# \- \*\*Abnormal:\*\* Electricity consumption exceeds the defined high-consumption threshold.

# 

# \### 2. Load-Management Classification

# 

# The second KNN model predicts the appropriate load-management action:

# 

# \- `Keep\_All\_ON` — Keep the appliances in their current operating states.

# \- `Shed\_Non\_Essential` — Initiate non-essential load shedding.

# \- `Critical\_Shedding` — Initiate the critical load-shedding response.

# 

# \### 3. Automated Load-Shedding Simulation

# 

# The predicted action is passed to a control-logic section that simulates appliance switching.

# 

# In the current implementation:

# \- The refrigerator and lights are treated as essential loads.

# \- The air conditioner (AC) and electric vehicle (EV) charger are switched off when the applicable load-shedding action is triggered.

# \- Appliance states before and after load shedding are displayed for evaluation.

# 

# \*\*Note:\*\* This is a software simulation. The notebook does not currently connect to physical smart meters, relays, IoT devices, or household appliances.

# 

# \## Machine Learning Approach

# 

# The project uses the \*\*K-Nearest Neighbors (KNN)\*\* classification algorithm from Scikit-learn.

# 

# The models use the following electrical measurements as input features:

# 

# | Feature | Description |

# |---|---|

# | `total\_power\_watts` | Total household power consumption in watts |

# | `current\_a` | Electrical current in amperes |

# | `voltage\_v` | Supply voltage in volts |

# 

# The target variables are `consumption\_status` and `load\_action`.

# 

# Both models use the following training workflow:

# 

# 1\. Split the dataset into 80% training data and 20% testing data.

# 2\. Standardise the input features using `StandardScaler`.

# 3\. Train a KNN classifier with `n\_neighbors=3`.

# 4\. Evaluate predictions using accuracy and a confusion matrix.

# 5\. Save the trained model and scaler using Joblib for later use.

# 

# \##  Dataset

# 

# The notebook generates a \*\*synthetic dataset containing 500 household energy readings\*\* using NumPy.

# 

# The simulated household includes appliances such as:

# 

# \- Refrigerator

# \- Lights

# \- Entertainment system

# \- Air conditioner

# \- EV charger

# \- Washing machine

# \- Water heater

# \- Microwave

# 

# The dataset includes electrical measurements, appliance operating states, and labelled consumption and load-management categories.

# 

# The labels are generated using predefined power-consumption thresholds. Therefore, the dataset is intended for experimentation and demonstration rather than representing measurements collected from an actual household.

# 

# \## Model Evaluation

# 

# Both classifiers achieved approximately \*\*95% accuracy\*\* on the notebook's 20% test split.

# 

# The models are evaluated using:

# \- Accuracy score

# \- Confusion matrix

# \- Predictions on new sample readings

# \- A combined simulation of energy classification and load shedding

# 

# These results apply to the synthetic dataset and should not be interpreted as proof of equivalent performance on real household electricity data.

# 

# Because the two target variables are generated from the same power thresholds and map directly to one another, their similar performance is expected. Testing with real measurements and independently defined load-management decisions would provide a stronger evaluation.

# 

# \## Technologies Used

# 

# \- \*\*Python\*\* — Programming language

# \- \*\*NumPy\*\* — Synthetic data generation and numerical operations

# \- \*\*Pandas\*\* — Dataset creation and manipulation

# \- \*\*Scikit-learn\*\* — KNN classification, feature scaling, data splitting, and model evaluation

# \- \*\*Joblib\*\* — Saving and loading trained models and scalers

# \- \*\*Jupyter Notebook / Google Colab\*\* — Development and experimentation

# 

# \## Getting Started

# 

# \### Prerequisites

# 

# Install Python and the required libraries, or open the notebook in Google Colab.

# 

# Install the dependencies using:

# 

# ```bash

# pip install numpy pandas scikit-learn joblib jupyter

# ```

# 

# \### Running the Project

# 

# 1\. Clone this repository:

# 

# &#x20;  ```bash

# &#x20;  git clone <YOUR-REPOSITORY-URL>

# &#x20;  ```

# 

# 2\. Navigate to the project directory:

# 

# &#x20;  ```bash

# &#x20;  cd <YOUR-REPOSITORY-NAME>

# &#x20;  ```

# 

# 3\. Open the notebook in Jupyter:

# 

# &#x20;  ```bash

# &#x20;  jupyter notebook

# &#x20;  ```

# 

# 4\. Open `k\_n\_n\_model\_for\_energy\_monitoring\_and\_load\_management.ipynb`.

# 

# 5\. Run the notebook cells sequentially, starting with synthetic dataset generation.

# 

# 6\. Observe the model-training results, accuracy scores, confusion matrices, predictions, and simulated load-shedding actions.

# 

# \*\*Important:\*\* Run the dataset-generation cell before training the models. It creates the `smart\_home\_power.csv` file required by subsequent cells. The model and scaler files are also generated during execution.

# 

# \## 📂 Project Structure

# 

# ```text

# repository/

# │

# ├── k\_n\_n\_model\_for\_energy\_monitoring\_and\_load\_management.ipynb

# ├── README.md

# │

# └── Generated during execution:

# &#x20;   ├── smart\_home\_power.csv

# &#x20;   ├── consump model

# &#x20;   ├── consump\_scaler

# &#x20;   ├── load\_action model

# &#x20;   └── load\_action scaler

# ```

# 

# The generated files may not appear in the repository until the notebook has been executed and the files have been saved or uploaded.

# 

# \## 🔮 Future Improvements

# 

# Potential improvements to this project include:

# 

# \- Integrating a real energy meter to collect live electrical measurements.

# \- Connecting an ESP32 or another suitable microcontroller to acquire readings and control loads.

# \- Adding IoT-based remote monitoring through a web or mobile dashboard.

# \- Introducing GSM notifications for high-consumption events.

# \- Using real household electricity data to improve model training and evaluation.

# \- Developing appliance-priority rules that consider appliance states, operating schedules, and user preferences.

# \- Expanding the control logic to manage additional non-essential appliances.

# \- Evaluating alternative classification algorithms and comparing their performance.

# 

# \## 🎓 Learning Outcomes

# 

# This project demonstrates the application of machine learning to electrical engineering, particularly household energy monitoring and load management. It also provides practical experience in synthetic data generation, feature scaling, supervised learning, model evaluation, and translating classification outputs into simulated control actions.

# 

# 

