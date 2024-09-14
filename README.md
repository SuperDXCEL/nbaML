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
4. Approach number 3 was messed up since I was measuring all three model average MAE with the tree predictions, instead of using the actual predictions made by each model. Furthermore, I have tried MultiTaskLasso, MultiTaskElasticNet and MultiOutputRegressor(ElasticNet(alpha=0.5), num_workers=5).
They all perform similar, I will look into the actual architecture of all models. MAE for each:
   Multioutput Model average MAE = 4.6-5.1
   Decision Tree average MAE = 10.1-10.3
   Random Forest average MAE = 6.6-7.3
5. Final MultiOutputRegressor outperforms everyother model by large, trained on around 76 columns of which only 39 are kept since they are over the 0.005 threshold.
    MULTIOUTPUT_MAE for MIN: 2.8316601664582413
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FGM: 2.1459363165872394
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FGA: 2.3909446368666063
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FG_PCT: 1.0026251801030908
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FG3M: 1.5263608436381422
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FG3A: 1.7490310887872191
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FG3_PCT: 1.0422946913274391
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FTM: 2.0519862996558436
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FTA: 2.052502129182723
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FT_PCT: 1.4988057269775006
    -----------------------------------------------------
    MULTIOUTPUT_MAE for OREB: 0.9798991082557041
    -----------------------------------------------------
    MULTIOUTPUT_MAE for DREB: 1.8464688989707057
    -----------------------------------------------------
    MULTIOUTPUT_MAE for REB: 1.6722359017801676
    -----------------------------------------------------
    MULTIOUTPUT_MAE for AST: 1.8478217827121945
    -----------------------------------------------------
    MULTIOUTPUT_MAE for STL: 1.2480673940555553
    -----------------------------------------------------
    MULTIOUTPUT_MAE for BLK: 1.1203622508880162
    -----------------------------------------------------
    MULTIOUTPUT_MAE for TOV: 1.729208761912785
    -----------------------------------------------------
    MULTIOUTPUT_MAE for PF: 1.1477902914349933
    -----------------------------------------------------
    MULTIOUTPUT_MAE for PTS: 2.3638691130730938
    -----------------------------------------------------
    MULTIOUTPUT_MAE for PLUS_MINUS: 1.6394930815747515
    -----------------------------------------------------
