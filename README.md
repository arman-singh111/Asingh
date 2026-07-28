Revenue Regression Analysis (AFM 244)

Predicting monthly revenue from operational and weather data using ordinary least squares (OLS) regression. Seven candidate models are fit on a training period and compared on a held-out testing period using Mean Absolute Percentage Error (MAPE).

Overview

The project uses linear regression to forecast a company's monthly revenue from three predictors:

production — units produced in the month
coolDD — cooling degree days (a measure of how hot the month was)
heatDD — heating degree days (a measure of how cold the month was)

Each model is trained on the dt4training rows and evaluated on the dt4testing rows. Model accuracy is measured with MAPE, so lower is better.

Data

The script expects a CSV named AICPA_regressionAnalysisData (1).csv in the same directory. It has one row per month with the following columns:

Column	Description
type	dt4training or dt4testing — splits the data into training and testing sets
date	Month-end date
revenue	Monthly revenue (the target variable)
production	Units produced
coolDD	Cooling degree days
heatDD	Heating degree days
Models
Model	Predictors
Model 1	production + coolDD
Model 2	production
Model 3	coolDD
Model 4	heatDD
Model 5	production + heatDD
Model 6	coolDD + heatDD
Model 7	production + coolDD + heatDD

For each model the script fits the regression on the training data, predicts revenue on the testing data, computes the absolute percentage error per row, and reports the average (MAPE). It also plots actual vs. predicted revenue over time.

Based on the notebook's results, Model 5 (production + heatDD) is the most accurate, with a test MAPE of about 8.7%.

Requirements
Python 3.9+
numpy
pandas
matplotlib
statsmodels

Install with:

bash
pip install numpy pandas matplotlib statsmodels
Usage
Place AICPA_regressionAnalysisData (1).csv in the project directory.
Run the notebook or script.

In Google Colab, upload the CSV first, then run all cells. To run locally, export the notebook to a .py file or run it in Jupyter:

bash
jupyter notebook "AFM 244 Week 10.ipynb"
Output

For each model the script prints the fitted coefficients and the test-set MAPE, for example:

Model 1 MAPE: 0.1337542277547468

It also produces revenue-forecast plots comparing actual revenue against each model's predictions.
