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

# Geospatial analysis with Excel

This tutorial demonstrated geospatial analysis using Excel along with supporting tools such as Python, GeoPandas, and GIS mapping tools. The case study analyzed coffee shop coverage in Manhattan to understand how Starbucks and McDonald's compete geographically for customers.

Coffee shop location data and population data were collected and combined with geographic boundary data. Python libraries such as GeoPandas were used to merge demographic data with map boundaries. Geographic coverage areas were then calculated to determine which coffee shop was closest to residents in different locations.

The processed data was visualized using Excel 3D maps and GIS tools to create coverage maps showing population distribution and coffee shop proximity. These visualizations helped illustrate how many people live closest to each coffee shop and where the highest potential customer densities exist.

---

# Geospatial analysis with Python

This tutorial demonstrated geospatial analysis using Python to support decision making for opening new stores or business branches. A dataset containing the geographic coordinates (latitude and longitude) of Starbucks and McDonald’s stores in New York was used for the analysis.

The first step involved preparing the dataset by combining latitude and longitude values into coordinate pairs. The Empire State Building was chosen as a reference point, and the distance of each store from this location was calculated using the geopy library. The computed distances were added as a new column to the dataset.

The store locations were then visualized on an interactive map using the Folium library. Different colored markers were used to represent Starbucks and McDonald’s locations. Further analysis included identifying stores within a given radius and calculating the closest and farthest stores relative to the Empire State Building.

---

# Geospatial analysis with QGIS

This tutorial demonstrated how to create and manage geographic data using QGIS, a free and open-source Geographic Information System (GIS). The main focus was on creating shapefiles and exporting them into formats such as KML for geospatial analysis.

Initially, existing shapefiles were downloaded from online spatial data repositories such as DIVA-GIS. These shapefiles represent geographic regions such as countries, states, districts, or cities using polygon boundaries. The shapefiles were loaded into QGIS and explored using attribute tables to understand geographic attributes like region names and administrative levels.

In cases where shapefiles were unavailable, QGIS was used to manually create new shapefiles. A polygon representing South Sudan was drawn using digitizing tools, and attributes such as ID and region name were added. The created shapefile was then exported in formats such as SHP and KML for use in geospatial analysis tools like Google Earth.

---

# Network analysis in Python

This tutorial demonstrated network analysis using the IMDB dataset of actors and movies. In this analysis, each actor was treated as a node in a network, and a connection (edge) was created between two actors if they appeared together in a movie.

The dataset contained movie identifiers, actor identifiers, and additional metadata such as movie language and actor names. The analysis first constructed a binary movie–actor matrix indicating which actors appeared in each movie. Matrix multiplication with the transpose of this matrix was used to efficiently compute how many times each pair of actors acted together.

Using the scikit-network library, this actor collaboration data was converted into a network representation. Community detection algorithms such as the Louvain method were then applied to identify clusters of actors who frequently worked together in the same movies.

---

# Visualizing Machine Learning

This session explored the importance of visualizing machine learning models to make them understandable and interpretable. Modern machine learning models such as neural networks, support vector machines, and random forests often act as black box models, meaning their internal decision processes are difficult for users to understand.

Through examples such as customer churn prediction and district clustering using census data, the tutorial demonstrated how machine learning outputs can be visualized using tools like maps, charts, and clustering visualizations. Techniques such as K-means clustering were applied to group similar districts based on demographic characteristics and then visualized geographically to reveal meaningful patterns.

The tutorial emphasized moving up and down the "ladder of abstraction", where raw data is summarized into visual patterns and then explored interactively to better interpret model behavior and relationships within data.

---
