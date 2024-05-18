# SuperTrend Indicator on MQL5
An indicator used to ascertain the market's direction is SuperTrend. It plots bends below for a bullish market and above for a negative market using the ATR and its multiplier on the candlesticks.

## Understanding the ATR (Average True Range)
This is not a directional indicator; rather, it is a lagging indicator used to determine market volatility.

We must be able to compute a True Range before we can compute the Average True Range.

### True Range (TR)
A true range is calculated using the following standard formula.
```
MAX = [{ High - Low}, {High - p.Close}, {p.Close - Low}]

High = Current High
Low = Current Low
p.Close = Previous Close

MAX = Maximum Values
```
### Average True Range (ATR)
I am not going to specifically calculate the True Range and the Average True Range since we have it built for us [MQL Docs](https://www.mql5.com/en/docs/indicators/iatr)
Since there are no strict guidelines for smoothing the TR, we can use any type of moving average to extract the ATR from the TR. As an example, we can use a Simple Moving Average to smooth the TR.

**After being able to obtain the ATR we need to start with execution in order to start executing consider the below cases**

## Understanding the implementation
In order to be able to start drawing the SuperTrend bands we need to be able to calculate the bands' positions below and above the candle sticks.

### Bands drawing
To calculate the position of the upper band and lower band the following calculations are needed.
```

Upperband = HLA + [Multiplier * ATR 10]
Lowerband = HLA - [Multiplier * ATR 10]

```
1. HLA - High Low Average is calculated as [(High + Low)/2]
2. Multiplier - Is usually 3. Not sure why however you can change it to what suit your needs.
3. ATR 10 - Is an Average True Range with a lookback period of 10

That's it after doing the above calculation with the bands it is then you can start coding your MQL5 indicator!
