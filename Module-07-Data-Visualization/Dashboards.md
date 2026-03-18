# Visualising Forecasts with Excel

## Pivot Table Base
- Used to structure time series data.
- Organizes securities vs dates efficiently.

## Trend Column
- Created using Sparklines.
- Shows mini time-series trend for each security.

## Average Calculation
- Formula: =AVERAGE(range)
- Provides central tendency of values.

## Forecasting
- Formula: =GROWTH(known_y’s, known_x’s, new_x)
- Predicts next value in the series.

## Daily Growth %
- Formula: (Forecast - Last Value) / Last Value
- Shows expected percentage change.

## Variance (Volatility)
- Formula: =STDEV(range)/AVERAGE(range)
- Measures fluctuation relative to mean.

## Range (Optional)
- Formula: (MAX - MIN)/MIN
- Alternative measure of spread.

## Correlation Analysis
- Formula: =CORREL(array1, array2)
- Measures relationship strength between securities.

## Correlation Matrix
- Built using Data Analysis ToolPak or CORREL formula.
- Shows pairwise relationships across all securities.

## Dashboard Insights
- Identify highest growth forecasts.
- Detect most volatile securities.
- Find strongest and weakest correlations.

---
