# 9-13-EMA-Crossover-Strategy

This GitHub repository contains a simple trading strategy script written in Pine Script, a domain-specific language used for creating custom indicators and strategies on TradingView. This script is designed to implement an Exponential Moving Average (EMA) crossover strategy, where buy and sell signals are generated based on the crossover and crossunder of two EMAs.

## Overview

The EMA Crossover Strategy involves two key Exponential Moving Averages:

- A 9-period EMA (Exponential Moving Average)
- A 13-period EMA

The strategy aims to capture potential trend changes by identifying crossovers and crossunders between these two EMAs.

## Pine Script Code

```pinescript
//@version=4
strategy("EMA Crossover Strategy", shorttitle="EMA Crossover", overlay=true)

// Define EMA lengths
ema9 = ema(close, 9)
ema13 = ema(close, 13)

// Plot EMAs
plot(ema9, color=color.blue, title="9 EMA")
plot(ema13, color=color.red, title="13 EMA")

// Define buy and sell conditions
buyCondition = crossover(ema9, ema13)
sellCondition = crossunder(ema9, ema13)

// Plot buy and sell signals
plotshape(series=buyCondition, title="Buy Signal", location=location.belowbar, color=color.green, style=shape.triangleup, size=size.small)
plotshape(series=sellCondition, title="Sell Signal", location=location.abovebar, color=color.red, style=shape.triangledown, size=size.small)

// Strategy entry conditions
strategy.entry("Buy", strategy.long, when=buyCondition)
strategy.entry("Sell", strategy.short, when=sellCondition)
```

## How It Works

1. The script defines two EMAs with lengths of 9 and 13 periods using the `ema` function.

2. The script plots these two EMAs on the chart with different colors for easy visualization.

3. Buy and sell conditions are defined based on the crossovers and crossunders of the two EMAs.

4. Buy signals are marked with green triangle shapes below the bars when the `buyCondition` is met.

5. Sell signals are marked with red triangle shapes above the bars when the `sellCondition` is met.

6. The strategy entry conditions are set to execute a long (buy) trade when the `buyCondition` is true and a short (sell) trade when the `sellCondition` is true.

## How to Use

1. Copy the Pine Script code above.

2. Open TradingView and create a new Pine Script indicator.

3. Paste the code into the Pine Script editor.

4. Save the script.

5. Apply the script to a chart.

6. The buy and sell signals will be displayed on the chart as green and red triangles, respectively.

7. You can customize the EMA lengths or other parameters to suit your trading preferences.

## Disclaimer

This script is provided for educational purposes only and should not be considered financial advice. Trading carries risks, and you should do your own research and consider seeking advice from a financial professional before making any trading decisions.
