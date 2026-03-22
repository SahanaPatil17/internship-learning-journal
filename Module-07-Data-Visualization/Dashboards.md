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

# Visualising Network Data with Kumu

## Data Preparation
- Extract data from IMDB datasets.
- Filter:
  - Only movies (exclude TV shows)
  - Specific region (e.g., Indian movies)

## Entity Mapping
- Actors assigned unique IDs.
- Map IDs to actor names for interpretation.

## Matrix Construction
- Create Movie × Actor matrix:
  - 1 → Actor in movie
  - 0 → Actor not in movie

## Co-occurrence Matrix
- Multiply matrix with its transpose.
- Result:
  - Diagonal → total movies per actor
  - Off-diagonal → shared movies between actors

## Sparse Matrix Optimization
- Use Compressed Sparse Row (CSR) format.
- Stores only non-zero values.
- Improves performance and memory efficiency.

## Data Formatting for Kumu
- Convert matrix into edge list:
  - From (Actor A)
  - To (Actor B)
  - Weight (number of collaborations)

## Filtering
- Minimum number of movies per actor
- Minimum collaborations between actor pairs

## Visualization in Kumu
- Upload dataset to create network graph.
- Features:
  - Node highlighting
  - Zoom and filtering
  - Cluster exploration

## Dashboard Insights
- Identify highly connected actors.
- Detect communities and clusters.
- Analyze relationship paths between entities.

---

# Data Visualisation with Seaborn

## Setup
- Libraries:
  - numpy
  - pandas
  - matplotlib
  - seaborn

## Data Handling
- Load datasets using:
  - pandas (CSV, etc.)
  - seaborn built-in datasets

## Visualization Categories

### Distribution Analysis
- distplot → histogram + KDE
- kdeplot → smooth distribution
- jointplot → relationship between variables
- pairplot → multi-variable relationships

### Categorical Analysis
- barplot → aggregated statistics
- countplot → frequency
- boxplot → spread and outliers
- violinplot → density + distribution
- stripplot/swarmplot → individual data points

### Matrix Visualization
- heatmap → correlation/pattern detection
- pivot tables for structured data
- clustermap → hierarchical clustering

### Grid Systems
- PairGrid → custom multi-plot layout
- FacetGrid → split data across rows/columns

### Regression Analysis
- lmplot → regression relationships
- Supports grouping (hue, row, column)

## Styling & Customization
- set_style → grid/background styles
- set_context → scaling (paper, talk, poster)
- palettes → color themes
- despine → remove axes lines
- figure size adjustments

## Dashboard Insights
- Identify distributions and trends.
- Compare categories effectively.
- Detect correlations and clusters.
- Create visually appealing analytical dashboards.

---

# Google Charts

## Tools & Integration
- Google Charts (JavaScript library)
- googleVis (R interface to Google Charts)
- Supports:
  - R Markdown
  - Shiny apps
  - Web dashboards

## Data Workflow
- Data processing in R or backend
- Visualization using Google Charts API
- Integration into web applications

## Dashboard Features

### Interactivity
- Mouse hover tooltips
- Dynamic filtering
- Zoom and scale adjustments

### Chart Customization
- Multiple chart types for same data
- HTML-based tooltips
- Color and size encoding

### Dashboard Composition
- Combine multiple charts using merge functions
- Create full dashboards with multiple visualizations

### Motion Charts
- Time slider for dynamic data
- Adjustable axes and scales
- Bubble size and color encoding

### Sankey Diagrams
- Visualize flows between nodes
- Useful for journey or transition analysis

## Limitations
- Requires internet connection
- Not ideal for print-based reports
- Dependency on external APIs

## Dashboard Insights
- Enables real-time, interactive dashboards.
- Useful for storytelling and exploration.
- Helps users interact directly with data.

---

# Google Data Studio

## Data Setup
- Use Google Sheets or other connectors.
- Clean dataset requirements:
  - One row per record
  - No merged cells
  - Consistent data types
  - Headers in first row

## Core Concepts

### Dimensions vs Metrics
- Dimensions → categorical data (name, date, country)
- Metrics → numerical data (salary, count)

### Aggregation Functions
- SUM, AVG, MEDIAN, MIN, MAX, COUNT

## Dashboard Features

### Tables
- Custom columns and sorting
- Aggregation tables for statistics
- Heatmap tables for comparisons

### Filters
- Date range filter (global)
- Dropdown filters (country, recruiter)
- Table-level filters
- Page-level filters

### Interactivity
- Filters update all charts dynamically
- Drill-down options in charts
- Clickable elements for filtering

### Charts
- Bar charts → daily trends
- Line charts → overall trends
- Treemaps → category distribution
- Geo maps → geographic insights

### Scorecards
- Display KPIs
- Compare with previous periods
- Show percentage or absolute change

### Styling
- Themes and layouts
- Font and color customization
- Alignment and spacing
- Dashboard sections using shapes

## Dashboard Insights
- Enables real-time data exploration.
- Combines multiple data views in one place.
- Supports interactive and user-friendly reporting.

---

# Actor Network Visualization

- Show actor connections and shortest paths
- Highlight key nodes and bridges
- Allow exploration of collaboration networks

Useful for storytelling with graph data.

---

# RAWGraphs

- Import data directly from spreadsheets
- Choose chart type and map variables
- Customize visuals before exporting
- Can integrate with design tools

Best for exploratory visualization.

---

# Data Storytelling

- Combine charts, text, numbers, and visuals
- Use multiple formats for better understanding
- Focus on clarity and engagement

---

# Interactive Notebooks : Marimo

- Notebooks can be converted into interactive web apps
- Users can interact with sliders, filters, and charts
- Supports real-time updates without re-running cells manually
- Can be shared as read-only web applications

Bridges the gap between notebooks and dashboards.

---

# Narratives with Excel

- Pivot tables used as data sources
- Filters (e.g., country selection) update entire dashboard
- Reference tables created using formulas (VLOOKUP)
- Narratives update automatically based on selected data

Enables creation of interactive and auto-updating storytelling dashboards.

---

# Narratives with Comics 

- Google Sheets used as backend for dynamic storytelling
- Comicgen generates characters and speech bubbles
- IMAGE() function used to embed visuals dynamically
- IF conditions and mappings control text, emotions, and visuals
- Entire comic updates based on selected data (e.g., cluster)

Transforms dashboards into engaging, story-driven interfaces.
