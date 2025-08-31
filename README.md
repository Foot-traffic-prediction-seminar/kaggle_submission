# Foot Traffic Prediction in Würzburg, Germany

## Overview
This project focuses on forecasting **hourly pedestrian foot traffic** for one week on three streets in Würzburg, Germany. Accurate predictions of pedestrian movement can help local retailers optimise resource management and assist city planners in designing better urban infrastructure.

The challenge, hosted on [Kaggle](https://www.kaggle.com/competitions/foot-traffic-wue), is beginner-friendly and a great entry point for newcomers to data science and machine learning.

We aim to predict three target variables:
1. **n_pedestrians** – total number of pedestrians  
2. **n_pedestrians_towards** – pedestrians moving towards the city centre  
3. **n_pedestrians_away** – pedestrians moving away from the city centre  

Understanding these flows allows stakeholders to model pedestrian traffic dynamics within the city.

---

## Dataset
The dataset contains **hourly pedestrian counts from 2019 to 2024** for three streets in Würzburg. Key challenges include:
- Variable data lengths across streets  
- Seasonal trends, public holidays, and special events  
- Impact of external factors such as the COVID-19 pandemic  

Additional context, such as event schedules or public holidays, can be incorporated as external features, as long as they were **available before the test period**.

Street counter locations are provided in a **JSON file**, and a map of the monitored areas is available on Würzburg’s open-data platform.

---

## Approach
We implemented multiple machine learning models using a **Scikit-learn pipeline** for consistent preprocessing, feature engineering, and hyperparameter tuning. The models included:

- **Linear Regression**  
- **Decision Tree**  
- **Random Forest**  
- **LightGBM**  
- **XGBoost**  

Key techniques and tools:
- **Randomised search** for hyperparameter optimisation  
- **GPU acceleration** for faster training  
- Handling temporal patterns such as seasonal trends and anomalies  
- Feature engineering including `holiday_with_weekends` and event-related variables  

This pipeline allowed for a streamlined evaluation of all models and facilitated adaptations depending on specific model requirements.

---

## Evaluation
Performance is measured using **Mean Squared Error (MSE)** across all three target variables and streets:

\[
\text{MSE}_{total} = \frac{1}{S \cdot T \cdot 3} \sum_{s=1}^{S} \sum_{t=1}^{T} \sum_{i=1}^{3} \left(y_{st}^{i} - \hat{y}_{st}^{i}\right)^2
\]

Where:
- \(S\) = total streets  
- \(T\) = total test time points  
- \(i\) = target variable index  
- \(y_{st}^{i}\) = actual pedestrian count  
- \(\hat{y}_{st}^{i}\) = predicted pedestrian count  

Lower MSE indicates better predictive performance. Fine-tuning and feature engineering are crucial to optimising forecasts.

---

## Findings
Our study revealed several insights regarding pedestrian traffic forecasting:

- Ensemble models (**Random Forest, LightGBM, XGBoost**) outperformed baseline models (Linear Regression and Decision Tree).  
- The **Random Forest Regressor** provided particularly accurate predictions, though long training times limited extensive hyperparameter tuning.  
- GPU acceleration improved training times for gradient boosting models, making them suitable for practical model testing.  
- Feature engineering, such as combining holidays with adjacent weekends and including event data, improved predictive accuracy.  
- Static features like store, hospital, or school presence were not included due to their constant nature, but could be valuable for urban planning in areas lacking pedestrian data.  

Overall, our pipeline demonstrated that machine learning can provide robust and adaptable forecasts of foot traffic, supporting informed decision-making for urban planning, business strategy, and public safety during large-scale events.

---

## Insights
Through this analysis, we aim to:
- Identify the most accurate forecasting model for pedestrian traffic  
- Understand pedestrian flow patterns over time  
- Provide actionable insights for local businesses and city planning