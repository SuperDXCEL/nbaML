# Approaches

1. Predicting points from other stats in the same game (Awful approach-> Data Leakage).
2. Predicting PTS, REB, AST with different models from [player_id, game_date, matchup]:
    Multioutput Model    -   Mean Squared Error:   0.9642395896195829
    Multioutput Model    -   Mean Absolute Error:  0.7798865952362899
    Decision Tree Model  -   Mean Squared Error:   0.4544610300358123
    Decision Tree Model  -   Mean Absolute Error:  0.2565295187785709
    Random Forest Model  -   Mean Squared Error:   0.44835280896947866
    Random Forest Model  -   Mean Absolute Error:  0.4691160540835029
3. Predicting all stats with different models, the data here must be inverted back using -> StandardScaler.inverse_transform(predictions) <- and then get the MAE for each variable,
   so approach number 2 was useless.
   Multioutput Model average MAE = 140
   Decision Tree average MAE = 10
   Random Forest average MAE = 140
