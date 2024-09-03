This bot uses the following strategy:

At every time t (the maximum rate according to the rate limit), for all currency pairs, and for all possible purchase quantities, it polls:

    a. the exchange rate

    a. the trading fee (including gas fees)

    b. the liquidity

    c. the estimated slippage

It normalizes this data in a relational database.

To be more precise, this is:

- The exchange rates of the intersection of the exchange pairs on Kraken and the exchange pairs on Uniswap

- The difference between the exchange rates at every time t

- The trading fee on Kraken and on Uniswap per quantity traded at time t

- The estimated slippage per quantity traded on Kraken and Uniswap at time t

Bound that data by the liquidity limits. Find the optimal points in that space. Once more:

For every exchange pair, calculate exchange rate per quantity (factoring in trading fees and slippage).

You end up with a distribution of profits relative to quantity traded. Then just select the quantity, within the liquidity bound, that is most profitable - literally just the MAX() of the profit values. One more time...
