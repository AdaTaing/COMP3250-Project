General Approach

Buy & Hold: Buying a shares and not selling them
    - Start with initial investment to buy shares according to the portfolio
    - With biweekly contributions, buy shares according to required portfolio distribution

Timing: Buying and selling shares when the moving average over the past 50 days reaches a threshold
    - Start with initial investment to buy shares according to the portfolio
    - For each day, calculate the moving average by calculating the rolling average of each etf prices for the past 50 days
    - If the moving average is less than the the current etf price:
        - indicate to buy the share
        - With biweekly contributions, buy shares according to required portfolio distribution
    - If the moving average is greater than the current etf price:
        - indicate to sell shares
        - sell all shares for that etf
        - move profits to cash


Simulation
    - Cases to explore/portfolio share distribution weights in both strategies:
        - Single ETF: SPY=100%, QQQ=0%, VTI=0%
        - Equal ETF Shares: SPY=33.3%, QQQ=33.3%, VTI=33.3%
        - Custom ETF Shares: SPY=50%, QQQ=30%, VTI=20%

    - Dataset used for all simulations:
        - Columns:
            - Date
            - SPY_Price
            - QQQ_Price
            - VTI_Price
            - SPY_MA50
            - QQQ_MA50
            - VTI_MA50
            - Position_SPY
            - Position_QQQ
            - Position_VTI
            - Shares_SPY
            - Shares_QQQ
            - Shares_VTI
            - Cash
            - Contribution
            - Total_Invested
            - Portfolio_Value
            - Earnings
            - Daily_Return
            - Strategy
            - Portfolio_Type

        - In the Buy & Hold Strategy
            - Columns not used/will remain blank:
                - Moving average columns (ie SPY_MA50, ....)
                - Cash
            - Position columns will always be 1
            - Shares never decrease

        - In the Timing Strategy
            - Moving Average changes daily as the it calculates based on the most recent 50 days
            - Position changes:
                - 1 when moving average is less than the current etf price
                - 0 when moving average is greater than the current etf price
            - Shares increase and decrease when:
                - Position is 1: buying shares
                - Position is 0: sell all shares
            - Cash
                - increases when shares are sold
                - will be used alongside contributions to buy more shares
        
        - Contributions every 10 days (every 2 weeks, 10 days since trading weeks are 5 days)
        
        - Share calculations are dependant on the portfolio distribution amounts
            - ie if its single etf, all contributions and investments go into 1 etf, while the rest remain blank for the entire simulation

        - Total invested is the initial invested plus all contributions

        - Portfolio value is the price of the all etf shares at the moment plus cash

        - Earnings is the difference between the portfolio value and total invested

        - daily return is the difference in portfolio value from the day before and the present