## ES/CL algo trading SAMPLES
Algorithmic trading is a method of executing orders using automated pre-programmed trading instructions accounting for variables such as time, price, and volume.

## #1 Example:
Sample of strategy using simple conditions based on moving average with period 15 and initial balance range for buy-only trading ES futures. Chart with P&L (profit and loss - cumulative) and DD (drawdown - maximum cumulative) for better understanting potential Profit and Risk.
```python
df['con1'] = [1 if ibr > pibr else 0 for ibr, pibr in zip(df['IB_RNG'], df['pIB_RNG'])]
df['con2'] = [1 if c < sma else 0 for c, sma in zip(df['RTH_C'], df['SMA'])]
df['signal'] = [1 if c1+c2 == 2 else 0 for c1, c2 in zip(df['con1'], df['con2'])]
```
![Algo IRET](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_iret_SAMPLE.png)

## #2 Example:
Long term Buy&Hold timeing strategy using %change of price to indicate potentional long term buying opportunities in SPX (entries with markers for visual interpretation). 
![Buy Opp](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/buying%20opportunities.png)

## #3 Example:
Sample of strategy using simple conditions based on opening above SMA20 and specific previous days closes for buy-only trading ES futures. Chart with P&L (profit and loss - cumulative) and DD (drawdown - maximum cumulative) for better understanting potential Profit and Risk.
```python
df['con2'] = [1 if op >= sm else 0 for op, sm in zip(df['Open'], df['SMA'])]
df['con3'] = [1 if p == 'D' and pp == 'D' else 0 for p, pp in zip(df['p_UD'], df['pp_UD'])]
df['signal'] = [1 if c1+c2+c3 == 3 else 0 for c1, c2, c3 in zip(df['con1'], df['con2'], df['con3'])]
```
![Algo sma](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_sma20_pD_ppD_SAMPLE.png)

## #4 Example:
Sample of strategy similar to #3 using SMA20 and specific previous days closes for buy-only trading ES futures with an intraday holding time (no possitions are hold overnight). Chart with P&L (profit and loss - cumulative) and DD (drawdown - maximum cumulative) for better understanting potential Profit and Risk.

![Algo intra](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_intra_SAMPLE.png)

## #5 Example:
Strategy using candle patterns and OHLC values for buy-only trading ES futures with an intraday holding time (no possitions are hold overnight). Chart with P&L (profit and loss - cumulative) and DD (drawdown - maximum cumulative) for better understanting potential Profit and Risk.

![Algo rrtt](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_rrtt.png)

## #6 Example:
```python
df['IBS'] = (df['Close'] - df['Low']) / (df['High'] - df['Low'])
df['p_High'] = df['High'].shift(1)
df['Mid'] = (df['High'] + df['Low']) / 2
df['p_Mid'] = df['Mid'].shift(1)
```
Strategy using IBS strenght and OHLC values for buy-only trading ES futures with 15 minutes holding time on M15 chart (no possitions are hold overnight). Chart with P&L (profit and loss - cumulative) and DD (drawdown - maximum cumulative) for better understanting potential Profit and Risk. Results with 2 ticks slippage and $5 commisions on every trade, last 10 years / 8263 trades.

![Algo rrtt](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_IBS_M15.png)

## #7 Example:
```python
import investpy

data = investpy.economic_calendar(
    from_date='01/01/2010',
    to_date='31/12/2020',
    countries=['united states'],
    importances=['high', 'medium']
)

df['IBS'] = (df['Close'] - df['Low']) / (df['High'] - df['Low'])
```
Similar IBS strenght strategy trading ES futures on daily data with fundamental news taken into consideration (one day holding period). Chart with P&L (profit and loss - cumulative) and DD (drawdown - maximum cumulative) for better understanting potential Profit and Risk. Results with 2 ticks slippage and $5 commisions on every trade, last 10 years. Only 83 trades but invested in market for only 3.4% of the time this strategy produce great results.

![Algo rrtt](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_IBS_daily.png)

## #8 Example:
Intraday strategy trading for ES futures on M5 data with 3 if-then conditions and intraday holding period. Chart with P&L (profit and loss - cumulative) and DD (drawdown - maximum cumulative) for better understanting potential Profit and Risk. Results with 2 ticks slippage and $5 commisions on every trade, 2010-2019 years. Only 259 trades in 10 years. Barchart with profits for different months and heatmap for overall outlook on strategy during whole test period.

![Algo adee1](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_M5_buyside/ALGO_ADEE_m5_intraday(259).png)

![Algo adee2](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_M5_buyside/ALGO_ADEE_ruturn_months.png)

![Algo adee3](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_M5_buyside/ALGO_ADEE_YMheat.png)

## #9 Example:
Intraday breakout strategy trading ES futures with holding period of couple of minutes. Chart with P&L (profit and loss - cumulative) and DD (drawdown - maximum cumulative) for better understanting potential Profit and Risk. Results without slipp or commisions, 2010-2019. 

![Algo 8v88](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_8Av88A.png)

## #10 Example:
Intraday price action strategy trading CL futures with holding period of couple of minutes. Chart with P&L (profit and loss in R (risk/reward) - cumulative) and DD (drawdown in R - maximum cumulative) for better understanting potential Profit and Risk. Results without slipp or commisions, 2017-2021. Second chart with different entry conditions (filter for smaller trade frequency).

![Algo 8v18](https://github.com/vldmrmrv/ES-algorithmic-trading-strategy/blob/main/ALGO_CL_n21_1h.png)

![Algo 8a18](https://github.com/vldmrmrv/ES-CL-algorithmic-trading-strategy/blob/main/ALGO_CL_n21_12a4B.png)

## #11 Example:
Intraday ES IB breakout strategy with fixed RRR. Chart with P&L (profit and loss in R (risk/reward) - cumulative) and DD (drawdown in R - maximum cumulative) for better understanting potential Profit and Risk (markers on new equity highs). Results without slipp or commisions, 2017-2021.

![Algo 8EE78](https://github.com/vldmrmrv/ES-CL-algorithmic-trading-strategy/blob/main/ALGO_ES_IRB_a44.png)

## #12 Example:
Intraday ES - holding period from minutes to EOD. Charts of P&L in points, DD (drawdown: P&L - maximum cumulative) and trades distribution. Results with slipp/commisions - 3 ticks/trade, dataset 1.7.2020-29.6.2023.

![Algo R1](https://github.com/vldmrmrv/ES-CL-algo-ML-trading/blob/main/A_RL_F1.png)

![Algo R2](https://github.com/vldmrmrv/ES-CL-algo-ML-trading/blob/main/A_RL_F2.png)

![Algo R3](https://github.com/vldmrmrv/ES-CL-algo-ML-trading/blob/main/A_RL_F3.png)

## #13 Example:
Intraday Crude Oil futures - holding period from minutes to EOD. Charts of P&L in points, DD (drawdown: P&L - maximum cumulative) and trades distribution. Results with slipp/commisions - 3 and 6 ticks/trade, dataset 2.1.2014-28.9.2021.

![Algo CLR1](https://github.com/vldmrmrv/ES-CL-algo-trading/blob/main/Crude/A_L_2_3tk6tk.png)

![Algo CLR2](https://github.com/vldmrmrv/ES-CL-algo-trading/blob/main/Crude/A_L_2_DD3DD6.png)

![Algo CLR3](https://github.com/vldmrmrv/ES-CL-algo-trading/blob/main/Crude/A_L_2_3tk.png)

![Algo CLR3](https://github.com/vldmrmrv/ES-CL-algo-trading/blob/main/Crude/A_L_2_6tk.png)

## #14 ML decisiontree & randomforrest:

Simple decision tree (DT) and random forres (RF) algorithms used for a regression task in ES dataset (10 years of data - 2300 rows). Based on 13 variables/columns we tried to predict ES RTH range in points (RNG_RTH).

```python
X = df[features]

train_X, val_X, train_y, val_y = train_test_split(X, y, random_state=1)
rth_model = DecisionTreeRegressor(random_state=1)
rth_model.fit(train_X, train_y)

val_predictions = rth_model.predict(val_X)
val_mae = mean_absolute_error(val_predictions, val_y)
print("Validation MAE: {:,.0f}".format(val_mae))
```

Similar results for DT and RF with 5 nodes for DT and defaul settings in RF.


```python
for max_leaf_nodes in [5, 21, 144, 377, 1597]:
    my_mae = get_mae(max_leaf_nodes, train_X, val_X, train_y, val_y)
    print("Max leaf nodes: %d  \t\t\t Mean Absolute Error:  %d" %(max_leaf_nodes, my_mae))

forest_model = RandomForestRegressor(random_state=1)
forest_model.fit(train_X, train_y)
rthrng_preds = forest_model.predict(val_X)
print(mean_absolute_error(val_y, rthrng_preds))
```

Results: (RNG_RTH mean is 18.75 which makes these models w/ current settings pretty much useless)

```python
Validation MAE: 9
Max leaf nodes: 5  			     Mean Absolute Error:  6
Max leaf nodes: 21  			 Mean Absolute Error:  7
Max leaf nodes: 144  			 Mean Absolute Error:  7
Max leaf nodes: 377  			 Mean Absolute Error:  8
Max leaf nodes: 1597  			 Mean Absolute Error:  8
6.409842592592593
```
