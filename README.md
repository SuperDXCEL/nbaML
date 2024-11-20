## Predicting Points and Other Stats Using Machine Learning Models

This section summarizes the exploration of different machine learning models to predict various basketball stats from the same game. The process involved testing multiple approaches, identifying issues like data leakage, and refining methods to achieve the best possible performance.

---

### Approaches and Observations

#### 1. **Initial Approach: Predicting Points from Other Stats (Data Leakage)**

- The first attempt involved predicting `PTS`, `REB`, and `AST` directly from game data (`player_id`, `game_date`, `matchup`), which led to **data leakage**.
- Performance of models:
  - **Multioutput Model**:
    - Mean Squared Error (MSE): `0.964`
    - Mean Absolute Error (MAE): `0.780`
  - **Decision Tree Model**:
    - MSE: `0.454`
    - MAE: `0.257`
  - **Random Forest Model**:
    - MSE: `0.448`
    - MAE: `0.469`

#### 2. **Predicting All Stats with Data Inversion**

- Predictions required reversing the transformation of features using `StandardScaler.inverse_transform`.
- This approach failed due to incorrect error measurement across models.
- Observations:
  - **Multioutput Model**: Average MAE = `140`
  - **Decision Tree**: Average MAE = `10`
  - **Random Forest**: Average MAE = `140`

#### 3. **Error in Measuring Across Models**

- MAE was mistakenly calculated for all models using predictions from a single tree model instead of their respective outputs.
- Tested advanced models like **MultiTaskLasso**, **MultiTaskElasticNet**, and `MultiOutputRegressor(ElasticNet(alpha=0.5), num_workers=5)`, which all performed similarly:
  - **Multioutput Model**: MAE = `4.6–5.1`
  - **Decision Tree**: MAE = `10.1–10.3`
  - **Random Forest**: MAE = `6.6–7.3`

---

### Final Approach and Results

#### Feature Selection
- The model was trained on `76 columns`, reduced to `39 features` with a feature importance threshold of `0.005`.

#### MultiOutputRegressor Performance
Corrected the error measurement by properly reversing transformations. Results (MAE per stat):

| **Stat**         | **MAE**                  |
|-------------------|--------------------------|
| MIN              | 25.286                  |
| FGM              | 4.513                   |
| FGA              | 9.618                   |
| FG_PCT           | 0.851                   |
| FG3M             | 1.478                   |
| FG3A             | 3.577                   |
| FG3_PCT          | 0.877                   |
| FTM              | 2.118                   |
| FTA              | 2.636                   |
| FT_PCT           | 0.948                   |
| OREB             | 1.276                   |
| DREB             | 3.534                   |
| REB              | 4.535                   |
| AST              | 2.689                   |
| STL              | 1.131                   |
| BLK              | 0.937                   |
| TOV              | 1.580                   |
| PF               | 1.981                   |
| PTS              | 12.359                  |
| PLUS_MINUS       | 1.639                   |

---

#### XGBRegressor Performance
Results showed improvements across most stats compared to ElasticNet, except for `PLUS_MINUS`:

| **Stat**         | **MAE**                  |
|-------------------|--------------------------|
| MIN              | 25.260                  |
| FGM              | 4.506                   |
| FGA              | 9.598                   |
| FG_PCT           | 0.840                   |
| FG3M             | 1.402                   |
| FG3A             | 3.560                   |
| FG3_PCT          | 0.851                   |
| FTM              | 2.073                   |
| FTA              | 2.621                   |
| FT_PCT           | 0.896                   |
| OREB             | 1.176                   |
| DREB             | 3.539                   |
| REB              | 4.550                   |
| AST              | 2.665                   |
| STL              | 1.085                   |
| BLK              | 0.878                   |
| TOV              | 1.519                   |
| PF               | 1.984                   |
| PTS              | 12.340                  |
| PLUS_MINUS       | 4.136                   |
