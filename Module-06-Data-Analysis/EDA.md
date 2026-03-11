# Correlation of Excel

In this module, correlation analysis was performed on a COVID-19 dataset using Microsoft Excel. The analysis focused on three variables: new cases, new deaths, and new vaccinations. Before performing the analysis, the Excel Data Analysis ToolPak was enabled through the Add-ins settings.

Using the Data Analysis feature, a correlation matrix was generated to examine the relationships between the selected variables. The correlation values ranged between -1 and +1, indicating the strength and direction of the relationship between variables.

The analysis showed a strong positive correlation between new cases and new deaths, while the relationship between new vaccinations and new deaths showed a weak positive correlation. Scatter plots with trendlines were then created to visually analyze these relationships and better understand the patterns in the data.

---

# Regression of Excel 

In this tutorial, regression analysis was performed using Microsoft Excel on a cleaned COVID-19 dataset. The Excel Data Analysis ToolPak was used to run a multiple linear regression model. In this model, new deaths was treated as the dependent variable, while new cases, new tests, new vaccinations (per 1000), and stringency index were used as independent variables.

Before running the regression, some variables were scaled by dividing them by 1000 to simplify interpretation. The regression was performed by selecting the dependent variable as the Y range and the independent variables as the X range within the Data Analysis → Regression option.

The regression output provided statistical indicators such as Adjusted R Square, F-test significance, coefficients, and P-values, which were used to evaluate the model and interpret the relationship between the variables.

---

# Forecasting with Excel

This tutorial explored forecasting techniques in Excel using linear regression and time-series forecasting methods. A sample dataset containing heights and weights of individuals was used to demonstrate how Excel’s FORECAST or FORECAST.LINEAR function predicts values based on existing data.

The dataset was first converted from imperial units to metric units by converting height from inches to centimeters and weight from pounds to kilograms. A scatter plot was created to visualize the relationship between height and weight. Using the FORECAST function, Excel predicted unknown values such as the expected weight for a given height or the expected height for a given weight.

The tutorial also demonstrated the TREND function, which applies regression to a range of values and produces multiple forecasts at once. Additionally, a traffic dataset was used to illustrate time-series forecasting where FORECAST.ETS was applied to account for seasonal patterns in the data.

---

# Outlier detection with Excel

This tutorial demonstrated how to detect outliers in a dataset using Microsoft Excel. An outlier is a data point that differs significantly from the rest of the observations and may occur due to measurement variability or experimental error. Outliers can affect statistical analysis, so identifying them is an important step in data preprocessing.

Using a COVID-19 dataset, the new cases column was analyzed to identify unusual values. The process involved calculating the first quartile (Q1), third quartile (Q3), and the interquartile range (IQR). The lower and upper bounds were then computed using the formulas: Lower Bound = Q1 − 1.5 × IQR and Upper Bound = Q3 + 1.5 × IQR.

Excel functions such as QUARTILE.EXC were used to compute the quartiles, and logical formulas were applied to determine whether each value fell outside the defined bounds. The detected outliers were then visualized using a box-and-whisker plot, which provided a graphical representation of the distribution and highlighted extreme values.

---

# Data Analysis with Python

This tutorial introduced data analysis using Python, primarily with the Pandas library, which is widely used for programmatic data analysis. A credit card transaction dataset stored in Parquet format was analyzed. The dataset contained multiple fields such as transaction ID, transaction date, decision (approved or declined), amount, jurisdiction, dispute type, and regional information.

The dataset was loaded into Python using the pandas.read_parquet() function. Initial exploration included inspecting column names, understanding dataset structure, and identifying potential variables for analysis. Tools like df.columns were used to view all available columns in the dataset.

Various statistical analyses were then performed using Pandas, including pivot tables, grouping, correlations, and time-based aggregations. Pivot tables were created to analyze dispute types across regions, while correlations were used to study relationships between transaction amount and approval decisions. Time-based analysis was also conducted by combining transaction date and time fields to study approval rates across different hours and days of the week. Visualizations such as heatmaps were used to identify patterns in approval percentages over time.

---

# Data Analysis with SQL

This tutorial demonstrated how data analysis can be performed directly on databases using SQL along with Python and Pandas. Since most real-world data is stored in relational databases, SQL becomes an essential tool for querying and analyzing large datasets.

A dataset from the Relational Dataset Repository was used, specifically the Stats.StackExchange database. The database contained multiple related tables such as posts, users, votes, and post history. These tables were connected using identifiers such as user IDs, illustrating the concept of database normalization where information is stored efficiently without duplication.

Using Python, the database was accessed through Pandas using the pd.read_sql() function along with SQLAlchemy to create a connection engine. SQL queries were executed to retrieve and analyze data, such as counting the total number of posts, identifying the most active users, and extracting user attributes like age, views, and reputation.

Further analysis was performed by combining SQL queries with Pandas statistical operations. Correlation analysis was conducted between variables such as age and reputation, and views and reputation. Regression analysis was also performed to estimate how reputation changes with increasing views. Additionally, SQL was used to perform aggregation operations within the database itself to reduce data transfer and improve efficiency.

---

# Data Analysis with DuckDB

This tutorial introduced two important technologies for modern data analytics: the Parquet file format and DuckDB. Parquet is a columnar storage format optimized for analytical workloads. It is highly compressed, supports data typing, and provides significantly faster read and write performance compared to formats like CSV and JSON. In the demonstration, a flight dataset containing hundreds of thousands of rows was downloaded and stored in different formats to compare performance and storage size.

Experiments showed that Parquet files were significantly smaller and faster to load compared to CSV and JSON formats. The dataset was then analyzed using both Pandas and DuckDB. DuckDB is an analytical database designed for fast data processing and supports SQL queries directly on data files such as CSV, JSON, and Parquet without requiring explicit database loading.

A computationally intensive task was performed to group flights by departure delay and count unique routes. The same operation was executed using Pandas and DuckDB to compare performance. DuckDB executed the query much faster due to its columnar execution model, parallel processing capabilities, and efficient disk-based operations. The tutorial also demonstrated how DuckDB can work directly with Pandas DataFrames, allowing flexible integration between SQL-based and Python-based data analysis workflows.

---

