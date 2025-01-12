# hybrid_11_seasons_avg_no_rival_4_lagged_no_norm
**Predicting 'WL' and 'PTS'**

***Features***

AVG_MIN	AVG_FGM	AVG_FGA	AVG_FG_PCT	AVG_FG3M	AVG_FG3A	AVG_FG3_PCT	AVG_FTM	AVG_FTA	AVG_FT_PCT	AVG_OREB	AVG_DREB	AVG_REB	AVG_AST	AVG_STL	AVG_BLK	AVG_TOV	AVG_PF	AVG_PTS	Team	Rival	Home	FGM_lag1	FGM_lag2	FGM_lag3	FGM_lag4	FGA_lag1	FGA_lag2	FGA_lag3	FGA_lag4	FG_PCT_lag1	FG_PCT_lag2	FG_PCT_lag3	FG_PCT_lag4	FG3M_lag1	FG3M_lag2	FG3M_lag3	FG3M_lag4	FG3A_lag1	FG3A_lag2	FG3A_lag3	FG3A_lag4	FG3_PCT_lag1	FG3_PCT_lag2	FG3_PCT_lag3	FG3_PCT_lag4	FT_PCT_lag1	FT_PCT_lag2	FT_PCT_lag3	FT_PCT_lag4	FTM_lag1	FTM_lag2	FTM_lag3	FTM_lag4	FTA_lag1	FTA_lag2	FTA_lag3	FTA_lag4	OREB_lag1	OREB_lag2	OREB_lag3	OREB_lag4	DREB_lag1	DREB_lag2	DREB_lag3	DREB_lag4	REB_lag1	REB_lag2	REB_lag3	REB_lag4	AST_lag1	AST_lag2	AST_lag3	AST_lag4	STL_lag1	STL_lag2	STL_lag3	STL_lag4	BLK_lag1	BLK_lag2	BLK_lag3	BLK_lag4	TOV_lag1	TOV_lag2	TOV_lag3	TOV_lag4	PF_lag1	PF_lag2	PF_lag3	PF_lag4	2P_PCT_lag1	2P_PCT_lag2	2P_PCT_lag3	2P_PCT_lag4	lagged_FGM	lagged_FGA	lagged_FG_PCT	lagged_FG3M	lagged_FG3A	lagged_FG3_PCT	lagged_FT_PCT	lagged_FTM	lagged_FTA	lagged_OREB	lagged_DREB	lagged_REB	lagged_AST	lagged_STL	lagged_BLK	lagged_TOV	lagged_PF	lagged_2P_PCT	Year	Month_Sin	Month_Cos	Day_Sin	Day_Cos

**xgboost.XGBClassifier:** 0.5737269862332062

**sklearn.DecisionTreeClassifier:** 0.5375684193066843

**sklearn.RandomForestClassifier:** 0.5954552993862996

**xgboost.XGBRegressor:** 0.09091293762859207

**sklearn.DecisionTreeRegressor:** 0.09781112649611859

**sklearn.RandomForestRegressor:** 0.08753635432312727
