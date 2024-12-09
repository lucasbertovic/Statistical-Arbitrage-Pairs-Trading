# Statistical Arbitrage: Pairs Trading Strategy Development

In this notebook, we will develop and backtest a pairs trading strategy using US stocks. The process will involve the following steps:

1. **Stock Selection**: We begin by identifying a population of the top 500 US stocks based on highest trading volume.
2. **Data Extraction**: Hourly price data for these stocks will be collected, starting from 2021.
3. **Industry Partitioning**: The selected stocks will be grouped by industry based on their SIC codes.
4. **Cointegration Testing**: For each industry group, we will test pairs of stocks for cointegration, accounting for multiple comparisons bias using the Benjamini-Hochberg process.
5. **Stationarity Testing**: For the identified cointegrated pairs, we will perform ordinary least squares (OLS) regression and use the Augmented Dickey-Fuller test to confirm stationarity, again controlling for multiple comparisons bias.
6. **Selection of Pairs**: From the pairs that pass the stationarity test, we will calculate rolling betas and z-scores, and visualize the price series and z-scores. We will then narrow down the pairs to the top 5 based on the shortest mean reversion half-life, determined using the Ornstein-Uhlenbeck process.
7. **Signal Generation**: Trading signals will be generated when the rolling z-score crosses the ±3 threshold. Positions will be closed when the z-score crosses zero, with an additional 20% stop loss rule in place.
8. **Position Sizing**: Each trade will allocate 20% of the portfolio’s value to the selected pair.
9. **Backtesting**: Finally, we will backtest the strategy using out-of-sample data, achieving a Sharpe ratio of 0.3 and a 6-month return of 120%. Over this period, 27 trades were executed, with 16 profitable trades.