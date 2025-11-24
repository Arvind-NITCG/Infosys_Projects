# AI FOOTBALL ANALYTICS SUITE
Author: Arvind K N
Project: Infosys Springboard AI Internship

# PROJECT OVERVIEW
This repository contains the AI Football Analytics Suite, a comprehensive, dual-mode web application built with Streamlit. It is the culmination of a deep-dive engineering project that involved rigorous data preprocessing, advanced feature engineering, multi-model evaluation, and deployment.

The suite provides two distinct AI-powered tools for football analysis:

Match Winner Predictor: A true pre-match predictor that forecasts the outcome (Home Win, Draw, or Away Win) of a future Premier League match using deep historical data and live league standings.

Top Goal Scorer Estimator: A live, in-season estimator that projects a player's final goal tally for the season based on their performance statistics partway through the campaign.

The final application is live and accessible, demonstrating an end-to-end MLOps pipeline from data to production.

# THE ENGINEERING JOURNEY & KEY DECISIONS
This project was not a linear path but a journey of experimentation, analysis, and data-driven decision-making.

MATCH WINNER PREDICTOR: A "HARD PROBLEM"

Predicting football matches is a classic "hard problem" due to high randomness and hidden variables. The key to success was in advanced feature engineering:

Temporal League Rank: A system was built to reconstruct the exact league table before every single match in the historical dataset.

Temporal Team Strength (Elo): An Elo-style rating system was implemented to track the true, evolving power level of each team over time.

Multiple architectures were tested, including a complex XGBoost "divide and conquer" system. However, rigorous evaluation proved that a single, powerful CatBoost Classifier provided the best balance of accuracy and reliability on the held-out test set, making it the champion model.

#TOP GOAL SCORER ESTIMATOR: A TALE OF TWO PROBLEMS

The initial goal was a pre-season prediction, but this was proven to be statistically unreliable with the available data. Following the project requirements for a "live" model, the objective was pivoted to a more robust in-season estimation.

Feature Importance: Analysis revealed that in-season stats, particularly Goals_per_90, were overwhelmingly powerful predictors of a player's final goal tally.

Model Selection: While a simple Linear Regression failed to capture the complexity, a powerful, non-linear XGBoost Regressor proved highly effective, achieving an R² score of 0.92.

# FINAL ARCHITECTURE & TECH STACK
The final application is a multi-page Streamlit app that loads two distinct, trained models.

TECH STACK

Backend & Modeling: Python, Pandas, Scikit-learn, CatBoost, XGBoost

Frontend: Streamlit

Data Scraping: Requests, BeautifulSoup

PROJECT STRUCTURE

The repository is organized into a professional structure to separate concerns:

Frontend_files/: Contains the main app.py, all data files (.csv), model files (.pkl), and UI assets (assets/).

Backend_files/: Contains the Jupyter Notebooks and Python scripts used for all data preprocessing, feature engineering, and model training.

Presentation/: Contains the final project presentation.

4. HOW TO RUN THE PROJECT LOCALLY
To run the AI Football Analytics Suite on your local machine, please follow these steps.

PREREQUISITES

Python 3.9+

pip for package installation

STEPS

Clone the repository:

git clone <your-repository-url>
cd <your-repository-name>

Install the required dependencies:
The requirements.txt file is located inside the Frontend_files directory.

pip install -r Frontend_files/requirements.txt

Run the Streamlit application:
Navigate to the correct directory and run the app.py file.

streamlit run Frontend_files/app.py
