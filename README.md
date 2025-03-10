Explanation of the Code
Inputs:
LotSize: Volume of the trade (e.g., 0.1 lots).
TargetPips: Fixed at 100 pips for profit target.
StopLossPips: Optional stop loss (set to 0 to disable; adjust as needed).
Logic:
UpdateCandleData(): Fetches the high and low of the last completed 4H candle (shift 1, not the current forming candle).
IsNewCandle(): Ensures candle data updates only when a new 4H candle forms.
OnTick(): Checks if the price crosses above lastHigh (buy) or below lastLow (sell), using the previous price (prevPrice) to confirm a crossover.
Trade Execution:
BuyTrade() and SellTrade(): Use the CTrade class to place orders with a 100-pip take profit. Stop loss is optional and disabled by default.
PipValue(): Adjusts pip size for 4/5-digit brokers (e.g., 0.0001 for EURUSD on 5-digit brokers).
Position Management: Limits to one open position at a time (PositionsTotal() > 0).
How to Use This EA
Open MetaEditor:
In MT5, press F4 to open MetaEditor.
File > New > Expert Advisor > Name it (e.g., "4H_Breakout").
Paste and Compile:
Replace the default code with the above script.
Click "Compile" (F7). Fix any errors if they appear.
Attach to Chart:
Open an MT5 chart (any timeframe, e.g., M15 or H1, since it uses H4 data).
Drag the EA from the Navigator onto the chart.
Adjust inputs (LotSize, StopLossPips) in the pop-up window.
Enable "Allow Algo Trading."
Enable Auto-Trading:
Click the "AutoTrading" button (green arrow) on the MT5 toolbar.
Test It:
Use the Strategy Tester (Ctrl+R) with "Every tick" mode to backtest on historical H4 data.
Monitor live performance on a demo account first.
Enhancements You Might Want
Stop Loss: Set StopLossPips to a value (e.g., 50) for risk management.
Time Filter: Add a check to trade only during specific hours (e.g., London session).
Trailing Stop: Modify the code to trail the stop loss as profit grows.
Multiple Positions: Remove the PositionsTotal() check to allow multiple trades.
