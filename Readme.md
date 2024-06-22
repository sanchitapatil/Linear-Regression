# Bike Sharing Demand Prediction

## Project Overview

This project aims to predict the demand for bike sharing based on various factors such as weather conditions, seasonal effects, holidays, and more. The dataset used for this project contains daily records of bike-sharing counts and associated features.

## Dataset Characteristics

The dataset `day.csv` includes the following fields:

- **instant**: record index
- **dteday**: date
- **season**: season (1: spring, 2: summer, 3: fall, 4: winter)
- **yr**: year (0: 2018, 1: 2019)
- **mnth**: month (1 to 12)
- **holiday**: whether the day is a holiday or not
- **weekday**: day of the week
- **workingday**: if the day is neither weekend nor holiday (1), otherwise (0)
- **weathersit**: 
  - 1: Clear, Few clouds, Partly cloudy
  - 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds
  - 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds
  - 4: Heavy Rain + Ice Pellets + Thunderstorm + Mist, Snow + Fog
- **temp**: temperature in Celsius
- **atemp**: feeling temperature in Celsius
- **hum**: humidity
- **windspeed**: wind speed
- **casual**: count of casual users
- **registered**: count of registered users
- **cnt**: count of total rental bikes including both casual and registered

## Objective

To build a predictive model that accurately estimates the number of bike rentals based on the provided features.

## Methodology

### Data Preprocessing

1. **Initial Cleaning**: Handled missing values and ensured correct data types.
2. **Feature Engineering**: Created dummy variables for categorical features and dropped irrelevant columns (`casual` and `registered` to avoid multicollinearity).

### Feature Selection

1. **Avoiding Multicollinearity**: Used Variance Inflation Factor (VIF) to remove features with high collinearity.
2. **Manual Selection vs. Recursive Feature Elimination (RFE)**:
   - **RFE**: Selected features using automatic feature selection.
   - **Manual Selection**: Chose features based on domain knowledge and statistical significance.

### Model Building

1. **Linear Regression Model**: Used Ordinary Least Squares (OLS) method to build the model.
2. **Assumptions Validation**:
   - **Linearity**: Verified the linear relationship between variables.
   - **Independence**: Used Durbin-Watson test to check for residual independence.
   - **Homoscedasticity**: Checked constant variance of residuals.
   - **Normality**: Assessed residuals' normal distribution using Q-Q plots.

### Final Model

1. **Selected Features**:
   - `year`
   - `avg_temperature`
   - `windspeed`
   - `season_winter`
   - `holiday`
   - `weathersit_Light Rain/Snow`
   - `season_spring`
2. **Model Performance**:
   - R-squared (Training): 0.795
   - Adjusted R-squared: 0.792

### Conclusion

The manual approach was chosen for the final model due to a higher R-squared value and better interpretability. The top contributing features included `avg_temperature`, `year`, and `weathersit_Light Rain/Snow`. The model successfully captured significant factors affecting bike-sharing demand and can be used for future predictions and strategic planning.

## Results

- **R-squared (Training)**: 0.795
- **Adjusted R-squared**: 0.792
- **Top Contributing Features**:
  - `avg_temperature`
  - `year`
  - `weathersit_Light Rain/Snow`

## Tools and Libraries Used

- **Python**: Programming language used for analysis and modeling.
- **Pandas**: Data manipulation and preprocessing.
- **NumPy**: Numerical operations.
- **Scikit-learn**: Machine learning model building and feature selection.
- **Statsmodels**: Statistical modeling and validation.
- **Matplotlib/Seaborn**: Data visualization.

## License

Use of this dataset in publications must be cited to the following publication:

Fanaee-T, Hadi, and Gama, Joao, "Event labeling combining ensemble detectors and background knowledge", Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, doi:10.1007/s13748-013-0040-3.

## Citation

@article{year={2013}, issn={2192-6352}, journal={Progress in Artificial Intelligence}, doi={10.1007/s13748-013-0040-3}, title={Event labeling combining ensemble detectors and background knowledge}, url={http://dx.doi.org/10.1007/s13748-013-0040-3}, publisher={Springer Berlin Heidelberg}, keywords={Event labeling; Event detection; Ensemble learning; Background knowledge}, author={Fanaee-T, Hadi and Gama, Joao}, pages={1-15}}

## Contact

For further information about this dataset, please contact Hadi Fanaee-T (hadi.fanaee@fe.up.pt).
