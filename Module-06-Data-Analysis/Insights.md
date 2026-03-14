# Correlation with Excel

The regression model produced an Adjusted R Square value of approximately 0.816, indicating that around 81% of the variation in new deaths can be explained by the independent variables included in the model. The F-test significance value was below 0.05, suggesting that the regression model is statistically significant.

The coefficient values showed that increases in new cases and new tests are associated with increases in deaths. Specifically, for every 1000 new cases, deaths increase by approximately 7, and for every 1000 new tests, deaths increase by about 0.69.

New vaccinations showed a small negative coefficient, suggesting that higher vaccination numbers may slightly reduce deaths, although the effect was very small and cannot be considered conclusive. The stringency index had a positive coefficient but was statistically insignificant because its P-value was greater than 0.05, meaning it should not be included in the final model without further analysis.

---

# Regression with Excel

The regression model produced an Adjusted R Square value of approximately 0.816, indicating that around 81% of the variation in new deaths can be explained by the independent variables included in the model. The F-test significance value was below 0.05, suggesting that the regression model is statistically significant.

The coefficient values showed that increases in new cases and new tests are associated with increases in deaths. Specifically, for every 1000 new cases, deaths increase by approximately 7, and for every 1000 new tests, deaths increase by about 0.69.

New vaccinations showed a small negative coefficient, suggesting that higher vaccination numbers may slightly reduce deaths, although the effect was very small and cannot be considered conclusive. The stringency index had a positive coefficient but was statistically insignificant because its P-value was greater than 0.05, meaning it should not be included in the final model without further analysis.

---

# Forecasting with Excel

Using the FORECAST (or FORECAST.LINEAR) function, Excel applies linear regression to estimate unknown values based on existing relationships between variables. In the height and weight dataset, the model predicted weight values based on height and vice versa.

The TREND function was shown to be more efficient when predicting multiple values simultaneously because it calculates regression once and applies it across a range of inputs. This improves performance compared to repeating individual FORECAST calculations.

The tutorial also highlighted that linear forecasting is not always suitable for datasets with seasonal or cyclical patterns. In such cases, FORECAST.ETS performs better because it incorporates seasonality and patterns in the data. When applied to traffic data, the ETS model provided predictions that more closely followed real-world fluctuations compared to simple linear regression.

---

# Outlier detection with Excel

The analysis identified outliers by comparing each data value against calculated lower and upper bounds derived from the interquartile range. Any value greater than the upper bound or lower than the lower bound was marked as an outlier.

In the COVID-19 dataset, several values were found to be above the upper bound, indicating unusually high daily case counts. A negative value was also detected, which is unrealistic for daily case numbers and likely represents an error in the data.

The box-and-whisker plot helped visualize the distribution of the data and clearly highlighted extreme values outside the normal range. These outliers may either represent meaningful insights about sudden spikes in cases or errors that could distort statistical analysis, depending on the context of the data.

---

# Data analysis with Python

The regional dispute analysis showed that certain regions had different dispute patterns. Fraud-related disputes appeared lower in the Central Europe, Middle East, and Africa region compared to other regions, while the Asia-Pacific and US regions showed slightly higher dispute levels.

Correlation analysis between transaction amount and approval decisions revealed a very small negative correlation, indicating that higher-value transactions might be slightly more likely to be declined. However, statistical testing showed that this relationship was not significant, meaning a reliable conclusion could not be drawn.

A similar analysis comparing domestic and cross-border transactions also showed very weak correlations with approval decisions. Time-based analysis of approvals by hour and day of the week did not reveal any strong patterns, which was expected because the dataset was randomly generated. In real-world datasets, such analyses often reveal useful operational patterns for financial institutions.

---

# Data analysis with SQL 

Analysis of the posts table showed that user participation follows a typical distribution where a small portion of users contribute the majority of posts. The top 20% of users accounted for approximately 76% of the total posts, which closely follows the 80–20 rule commonly seen in online platforms.

Correlation analysis between user age and reputation showed an extremely small correlation coefficient, indicating that age does not significantly influence a user’s reputation score. However, analysis between views and reputation revealed a very strong positive correlation, suggesting that posts with more views tend to contribute significantly to higher reputation scores.

Regression analysis further indicated that reputation tends to increase as the number of views increases, highlighting the importance of visibility and engagement in online communities. The tutorial also demonstrated that performing aggregations directly in SQL can significantly reduce the amount of data transferred to Python, making analysis more efficient for large datasets.

---

# Data analysis with DuckDB

The comparison of file formats revealed that Parquet is significantly more efficient for analytical workloads. The Parquet file storing the flight dataset was approximately 25 MB, while the equivalent CSV file was over 150 MB and the JSON file exceeded 500 MB. Additionally, reading data from Parquet was several times faster than reading CSV or JSON files.

Performance comparisons between Pandas and DuckDB showed that DuckDB can process analytical queries much faster, especially for operations involving grouping, aggregation, and distinct counts. In the experiment, a grouping operation that took around 10 seconds in Pandas was completed in less than one second using DuckDB.

DuckDB also demonstrated advantages in memory efficiency and flexibility. It can directly query files without loading them entirely into memory and allows SQL queries to be executed on existing Python variables such as Pandas DataFrames. This hybrid approach allows analysts to combine the strengths of SQL and Python within the same workflow.

---

# Geospatial analysis with Excel

The geospatial analysis revealed that Starbucks has a significantly larger presence in Manhattan, with around 230 stores compared to approximately 16 McDonald's locations. As a result, about two-thirds of Manhattan's population lives closer to a Starbucks store.

However, despite having fewer locations, McDonald's stores tend to serve more customers per location. This indicates that McDonald's stores are positioned in high-density areas where a larger number of potential customers are located nearby.

The analysis also showed that relocating underperforming stores could improve profitability. Strategic repositioning of stores toward areas with higher population coverage could influence the competitive balance between Starbucks and McDonald's in Manhattan.

---

# Geospatial analysis with Python

The geospatial visualization revealed that Starbucks has a much higher number of stores compared to McDonald’s in New York, especially in the southern part of the city. McDonald’s stores were fewer and appeared more concentrated in specific areas.

Distance analysis showed that some stores are located very close to the Empire State Building, with the nearest Starbucks only a few meters away. In contrast, the farthest stores were located more than 13–14 kilometers away.

Such analysis helps businesses understand market saturation and identify optimal locations for opening new stores. By analyzing store density and customer accessibility, companies can make strategic decisions to reduce travel distance for customers and improve store profitability.

---

# Geospatial analysis with QGIS

Geographic shapefiles are essential for geospatial analysis because they store spatial boundaries along with descriptive attributes such as region names and demographic data. These files enable analysts to visualize geographic information and perform location-based analysis.

The tutorial demonstrated that when shapefiles are unavailable for certain regions, they can be created manually using QGIS digitizing tools. This ensures that missing geographic data does not prevent further analysis.

Exporting shapefiles into formats such as KML enables seamless integration with mapping tools like Google Earth, allowing the created geographic boundaries to be visualized and shared easily.

---

# Network analysis in Python

The network clustering revealed meaningful communities of actors based on the language and film industries they primarily worked in. For example, clusters naturally formed around Hollywood actors, Bollywood actors, Telugu actors, and other regional film industries.

The analysis also identified actors who frequently collaborated across clusters. These actors acted as connectors between different film communities because they worked with actors from multiple industries.

Such network analysis helps identify influential individuals within networks and understand how different groups are interconnected. These insights can be applied to many domains such as social networks, collaboration networks, and organizational structures.

---

# Visualizing Machine Learning

Machine learning models are often highly accurate but difficult to interpret, which can prevent organizations from adopting them. Visualization techniques help bridge this gap by translating complex model outputs into understandable patterns and insights.

By visualizing clustering results on maps and analyzing relationships between variables, analysts can interpret the characteristics that define each cluster and derive actionable strategies. For example, demographic clusters can guide marketing strategies, content targeting, or regional product planning.

Interactive visualizations that allow users to explore model behavior and adjust parameters help stakeholders better understand how models work, improving trust and adoption of machine learning solutions.

---
