
Project Overview
This project aims to predict the USD/JPY exchange rate using an LSTM (Long Short-Term Memory) model. The model is trained on a dataset that includes daily financial data, such as currency pairs (EUR/USD, GBP/USD), Treasury yields (10Y and 30Y), and various US economic indicators like interest rates, inflation rates, unemployment rates, and GDP growth rates.

Data Sources
The data used in this project is sourced from the following:

Yahoo Finance: For daily FX rates (EUR/USD, GBP/USD) and Treasury yields (10Y and 30Y).
FRED (Federal Reserve Economic Data): For US economic indicators, including:
US Interest Rate (Federal Funds Rate)
US Inflation Rate (Consumer Price Index)
US Unemployment Rate
US GDP Growth Rate
Data Preprocessing
1. Data Collection
Daily FX Rates and Treasury Yields: Data was fetched using the Yahoo Finance API.
Economic Indicators: Data was fetched from FRED, with different frequencies (monthly, quarterly) compared to the daily financial data.
2. Data Alignment and Filling
Economic indicators, which are reported monthly or quarterly, were forward-filled to align them with the daily frequency of FX rates and Treasury yields.
Missing values were filled using the forward fill (ffill) method to ensure continuity in the dataset.
3. Feature Engineering
Lagged Features: Lagged versions of all features (FX rates, Treasury yields, and economic indicators) were created to capture temporal dependencies.
Lag Period: A 5-day lag was used to generate lagged features.
Model Training
1. Model Selection
An LSTM model was chosen due to its ability to capture sequential dependencies in time-series data.
The model was designed with one or more LSTM layers, followed by dense layers to output the predicted USD/JPY exchange rate.
2. Hyperparameter Tuning
A grid search with time-series cross-validation was performed to optimize the following hyperparameters:
Number of LSTM units
Number of LSTM layers
Dropout rate
Optimizer (Adam, RMSprop)
Batch size and number of epochs
3. Training and Testing
The model was trained on data up to 2023.
The 2024 data (up to today) was used as the test set to evaluate the model's performance.
Evaluation and Results
Model Performance
The model's predictions were compared against the actual USD/JPY rates for 2024.
The inclusion of economic indicators aimed to improve the model’s ability to predict USD/JPY by providing additional macroeconomic context.
Observations
Visualizations were created to compare the predicted and actual USD/JPY exchange rates.
Economic indicators were plotted to analyze their trends and potential impacts on the USD/JPY exchange rate.
Future Work
Potential Improvements
Additional Features: Consider incorporating more global economic indicators, or other financial instruments like stock indices or commodity prices.
Model Complexity: Experiment with more complex models such as GRUs or Transformer models.
Alternative Lag Structures: Explore different lag periods or dynamic lagging based on market conditions.
Getting Started
Prerequisites
Python 3.x
Jupyter Notebook
Required libraries: numpy, pandas, matplotlib, yfinance, scikit-learn, tensorflow, pandas_datareader, scikeras
Running the Project
Clone the repository.
Install the required libraries.
Open the Jupyter Notebook and run the cells sequentially.
Directory Structure
.
├── data/                   # Directory to store downloaded data
├── notebooks/              # Jupyter notebooks for data processing and modeling
├── plots/                  # Directory to save generated plots
├── README.md               # Project description and instructions
└── requirements.txt        # Python libraries required to run the project
Example Usage
For data manipulation and analysis.

matplotlib: For plotting and visualizing data.
yfinance: To download financial data (FX rates, Treasury yields) from Yahoo Finance.
scikit-learn: For machine learning algorithms and tools (e.g., MinMaxScaler, GridSearchCV).
tensorflow: For building and training the LSTM model.
pandas_datareader: To download economic indicators from FRED.
scikeras: A wrapper to integrate TensorFlow's Keras models w
# Install required packages
pip install -r requirements.txt

# Start Jupyter Notebook
jupyter notebook
Run the notebook notebooks/AIMLCapstoneEDA.ipynb for USD/JPY prediction
License
Project Presentation
The project presentation can be found Capstone Presentation.

This project is licensed under the MIT License.

Acknowledgments
Yahoo Finance: For providing access to financial data.
FRED (Federal Reserve Economic Data): For providing access to economic indicators.
Scikit-learn and TensorFlow: For the machine learning libraries used in this project.
Thank You UC Berkeley Extension AIML Program!
This README.md provides a comprehensive overview of your project, including the data sources, preprocessing steps, modeling approach, and instructions for running the code. You can customize it further based on your specific needs or additional details. Let me know if you need any other adjustments!
