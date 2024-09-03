This bot uses the following strategy:

1. It polls the Kraken order book for all currency pairs at the rate limit:

2. It polls the Uniswap Automated Money Market exchange rates at the maximum rate limit?:

3. It restructures this data into a normalized relational database:

4. It computes arbitrage opportunities on the data in real time. For Kraken and Uniswap, at each moment in time, per quantity purchased, it computes:

    a. The trading fee (including gas fees)

    b. The liquidity

    c. The slippage

It then scans that multi-dimensional space for any optimum points that maximize profit. This is essentially solving a linear equation, defined as:

1. Quantity greater than zero, less or equal to than trader's liquidity, leq than Uniswap's liquidity pool, leq than Kraken's liquidity

2. The Buy-Sell ratio minus the trading fees minus the expected slippage must be greater than 0 (indicating profit)

That's it (for now). It's a very simple model of arbitrage.
