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

# Visualising Animated Data with PowerPoint

## Data Preparation
- Extract data (e.g., from Wikipedia).
- Clean using:
  - Paste Special (Values only)
  - Remove unnecessary formatting/images
- Restructure data into:
  - Year | Rank | Category | Value

## Data Transformation
- Transpose data for proper format.
- Normalize values (e.g., scaling for visualization).
- Clean inconsistent names (e.g., FRG → West Germany).

## Pivot Table Validation
- Used to verify correctness of structured data.
- Helps check rankings and values across years.

## PowerPoint Dashboard Design
- Use shapes to represent bars.
- Adjust width of shapes proportional to values.
- Add:
  - Country names
  - GDP values
  - Titles for each year

## Animation (Core Component)
- Use **Morph Transition** for smooth movement.
- Maintain consistent object names using Selection Pane.
- Naming format: !!CountryName

## Dynamic Effects
- Bars grow/shrink based on values.
- New entries appear from outside the slide.
- Exiting entries move out of frame.

## Optimization
- Adjust animation duration (e.g., 0.5–1 sec).
- Align bars for clean visuals.
- Ensure consistent scaling across slides.

## Dashboard Insights
- Visual storytelling of ranking changes.
- Easy identification of dominant and emerging entities.
- Highlights long-term trends and disruptions.

---

# Visualising Animated Data with Flourish

## Animation Principles
- Animation should:
  - Engage users
  - Inform clearly
- Avoid unnecessary or misleading animations.

## Object Constancy
- Same data points should remain visually consistent across transitions.
- Helps users track changes easily.

## Animation Controls

### Line Chart Race
- Animation Duration → speed between data points
- Mode Duration → transition between views

### Bar Chart Race
- Timeline Duration → total animation time
- Movement Speed → smoothness of bar transitions

### Line/Bar/Pie Template
- Animation Duration controls:
  - Chart drawing
  - Morphing in stories mode
- Option to disable animation for unrelated charts

### Scatter Plot
- Requires:
  - Name column (for tracking points)
- Settings:
  - Duration
  - Stagger (delayed movement for clarity)

### Time-based Controls
- Time slider controls pace between steps
- Separate from animation duration

## Advanced Features
- Animate series with same/different names
- Entry/exit animations for elements
- Stagger effects for better clarity

## Dashboard Insights
- Smooth animations improve readability.
- Proper settings prevent confusion.
- Animation enhances storytelling and comparisons.

---

