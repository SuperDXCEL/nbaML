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
   
5. Final MultiOutputRegressor is the best performing model, still underwhelming, trained on around 76 columns of which only 39 are kept since they are over the 0.005 feature importance threshold. Turns out I was measuring the error wrong as I was not inversing the StandardScaler transformed columns properly, this are the actual numbers:

    MULTIOUTPUT_MAE for MIN: 25.286315750330605
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FGM: 4.512742201244077
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FGA: 9.618494639452209
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FG_PCT: 0.8510725795768563
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FG3M: 1.4777327702664869
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FG3A: 3.576580504907982
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FG3_PCT: 0.8771553291850931
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FTM: 2.117662117691145
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FTA: 2.6356895807756686
    -----------------------------------------------------
    MULTIOUTPUT_MAE for FT_PCT: 0.9476607652309528
    -----------------------------------------------------
    MULTIOUTPUT_MAE for OREB: 1.2757554817832744
    -----------------------------------------------------
    MULTIOUTPUT_MAE for DREB: 3.5336600636970052
    -----------------------------------------------------
    MULTIOUTPUT_MAE for REB: 4.534824725629052
    -----------------------------------------------------
    MULTIOUTPUT_MAE for AST: 2.689088584918284
    -----------------------------------------------------
    MULTIOUTPUT_MAE for STL: 1.1306312744235554
    -----------------------------------------------------
    MULTIOUTPUT_MAE for BLK: 0.9367025460997473
    -----------------------------------------------------
    MULTIOUTPUT_MAE for TOV: 1.580352709528453
    -----------------------------------------------------
    MULTIOUTPUT_MAE for PF: 1.9808467752566252
    -----------------------------------------------------
    MULTIOUTPUT_MAE for PTS: 12.359489590296455
    -----------------------------------------------------
    MULTIOUTPUT_MAE for PLUS_MINUS: 1.6394930815747515
    -----------------------------------------------------
