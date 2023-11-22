# Stock-Trading-Bot
A stock trading bot to generate optimized returns on the S&amp;P 500.

# Results

# 1. Technical Indicators
**1.1 Trend Detection**
We will use the 200-day moving average for trend detection. 

If candles are trading above the curve of the moving average, we are in an uptrend. If below the SMA, we are in a downtrend. We determine this by testing if there are 5 consecutive candles trading above or below the curve.

**1.2 Price Envelope**
We will use Bollinger Bands for our price envelope. Bollinger Bands are upper and lower bands that are set above and below the moving average by a certain number of standard deviations of price, thus incorporating volatility.

The period for our Bollinger Band is 20 days, and our standard deviation is 2.5. The standard deviation for typical Bollinger Bands is 2, but this strategy is for safely increasing your capital in the S&P 500 Index, and therefore we want to cover 98% of price data.

![bellcurve](google.com)

Length=20, STD=2.5

If the stock price touches the lower curve of the Bollinger Band, we assume the stock is oversold and a buying opportunity is present. If the stock price touches the upper curve, we assume the stock is overbought and a selling opportunity is present.

**1.3 Momentum**
We use RSI to measure the speed and magnitude of the stock’s short-term price change. This can help us determine when to close our position, which will be discussed in the next portion: Strategy.

# 2. Strategy
**2.1 Buy/Sell Triggers**
If we have an uptrend and are looking for buying positions, we will wait for a candle closing below the lower Bollinger Band. When this happens, we will put in an order at the closing price of the trigger candle. Likewise, when we are looking for a selling position, we look for a candle closing above the high Bollinger Band. When this happens, we put in an order to sell at the closing price of the trigger candle.

**2.2 When to Close Position**
We will close the position when the 2-day RSI crosses 50% or after 10 days.

**2.3 Open Order Duration**
If the order is not traded the next day, we will keep the trade open for 2 days.

2.4 Multiple Orders
Only one trade should be allowed to be open at any given point in time. This is inherently a very selective trading model, and we want to avoid overlapping trades.

If we have consecutive signals to make a trade, we will only take the latest signal into account. The previous signal and target price will be erased. This will prevent over-trading on a single price swing.
