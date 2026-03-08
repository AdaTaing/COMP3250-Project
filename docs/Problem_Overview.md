Problem Statement
    - Is it better to use to time the market or invest for long term?
    - sub questions to help answer the problem:
        - Which strategy made the most money?
        - Which strategy holds the least risk?
        - which strategy is efficient when it comes to risk?
        - How bad can losses get?


ETFs: Exchange traded funds, a collection of stocks/bonds/other securities in a single fund that tracks a major stock exchange
Chosen ETFs:
    - SPY: tracks the large and mid caps stocks selected by the S&P committee
    - QQQ: tracks the best 100 stocks in the NASDAQ list of stocks
    - VTI: tracks the total market exposure of US stocks

Objective/Solution Approach
    - Explore 2 different strategies:
        - Market Timing:
            - Using the rolling average strategy
            - calculate the average price of shares in the past 50 days
            - buy or sell shares depending on that average
        - Buy & Hold: 
            - buying shares and then keeping them til the end
    - Using the 3 ETFs:
        - simulate each strategy with different portfolio types
        - Starting with an initial investment
            - start buying shares according to case type
            - new shares are bought using biweekly contributions
            - for the timing strategy, sell shares depending on the rolling average of stock prices in the past 50 days
            - for the buy & hold strategy, only need to buy shares
        - There will be 6 cases/portfolio types to explore:
            - Buy & Hold with only 1 ETF in the portfolio
            - Buy & Hold with 3 ETFs in the porfolio, divide contrbutions and initial investment equally to buy shares for each
            - Buy & Hold with 3 ETFs in the porfolio, custom division of  contrbutions and initial investment for each ETF and share (50%, 30%, 20%)
            - Timing with only 1 ETF in the portfolio
            - Timing with 3 ETFs in the porfolio, divide contrbutions and initial investment equally to buy shares for each
            - Timing with 3 ETFs in the porfolio, custom division of  contrbutions and initial investment for each ETF and share (50%, 30%, 20%)
        - Starting investing amount = 10000
        - Biweekly contribution = 500

        - Performance Evaluation:
            - 252 is the number of trading days
                - Years = the number of days traded / 252
                - the number of days traded are the number of dates retrieved

            - After simulations, calculate the performance of each case with these metrics
                - CAGR: The average growth rate of investments over a period of time
                    - ((Final Value/Initial Value) ^ (1/Years)) - 1

                - Volatility: the index return over time
                    - the higher the more risky
                    - standard deviation on the daily returns based on the number of trading days
                    - Volatility = std(daily returns) * sqrt(252)

                - Sharpe Ratio: To show whether the excess returns of the portfolio attribute to good investment decisions or its based on luck and risk
                    - Average Return / Volatility * sqrt(252)
                    - the higher the better return per unit of risk

                - Maximum Drawdown: measures the bigeest drop in value for an investment to highlight the downside risks and potential volatility
                    - lower indicates smaller historical losses
                    - Maximum drawdown = Min((protfolio value / the running max portfolio value) - 1)
                    - running max portfolio value = the highest portfolio value reached

                - Total Profit/Final Value: the amount of money earned by the end of the simulation, with total profit being the amount gained
                    - Total Profit = Final Value - Total Invested
                    - Final Value = the portfolio value at the end


