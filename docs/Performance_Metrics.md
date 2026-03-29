#### Performance Metrics

Final Portfolio Value <br>
- The last total value of the portfolio after simulation
- Calculation:
    - final_portfolio_value = df["Portfolio_Value"].iloc[-1]

Total Profit <br>
- The amount of money made by the portfolio
- Calculation:
    - total_profit = final_portfolio_value - df["Total_Invested"].iloc[-1]

CAGR <br>
- Compounded Annual Growth Rate
- the average rate of growth in terms of total portfolio value for the portfolio
- long term growth rate
- Calculation:
    - initial_value = df["Portfolio_Value"].iloc[0]
      final_value = df["Portfolio_Value"].iloc[-1]
      years = len(df) / 252

      cagr = (final_value / initial_value) ** (1 / years) - 1

Volatility <br>
- the standard deviation of all returns
- determines how much the portfolio has fluctuated
- higher the result, the greater the risk
- Calculation:
    - returns = df["Daily_Return"].dropna()
      volatility = returns.std() * (252 ** 0.5)

Sharpe Ratio <br>
- the risk adjusted return ratio, with the risk rate assumption of 0
    - if it wasn't 0, will be measuring excess return per risk
    - simplifies so its only for per every unit of risk only
- how much return per unit of risk
- the higher the better
- Calculation:
    - sharpe_ratio = (returns.mean() / returns.std()) * (252 ** 0.5)

Maximum Drawdown <br>
- the largest drop since the last peak in the porfolio
- helps shows how well a portfolio can recover from an economic decline
- also shows the worse that the investor can lose
- Calulation:
    - running_max = df["Portfolio_Value"].cummax()
      drawdown = df["Portfolio_Value"] / running_max - 1
      max_drawdown = drawdown.min()