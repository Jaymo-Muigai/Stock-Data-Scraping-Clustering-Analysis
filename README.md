#Stock Data Scraping & Clustering Analysis

## Objective
The primary goal of this project is to collect and analyze Kenyan stock market data over a 10-year period. We aim to group stocks based on their daily returns and volatility, visualizing clusters to highlight unique risk-return profiles for informed investment decision-making.

## Purpose
This project will create a robust dataset on Kenyan stocks for future analysis, useful to myself and other enthusiasts of local financial markets. By gathering around 250,000 data points, we can analyze differences in volatility and returns, supporting diversification strategies. Investors can minimize portfolio risk by choosing stocks from different clusters.

---

## Data Requirements
1. **Ticker Symbols**: Ticker symbols will serve as keys, with sectors as values, organized in a dictionary format.
2. **Price Data**: Closing and opening prices are necessary for calculating daily returns and applying logarithmic transformations.

---

## Data Collection Strategy
1. **Iterative Data Collection**:
   - A loop iterates through each day over the past decade, using approximately 3,653 days for a 10-year period.
   - We generate a dynamic URL in each iteration using an `f-string` and a date variable incremented by the time delta.

2. **Scraping & Data Aggregation**:
   - Use `pandas.read_html` to scrape daily stock data and append each DataFrame to a cumulative list outside the loop.
   - After the loop completes, concatenate all the DataFrames into one and save the compiled data as a CSV file. The final dataset should contain approximately 250,000 records.

---

## Data Preparation Process
1. **Data Loading & Filtering**:
   - Import the saved CSV file into a DataFrame, selecting only relevant columns.

2. **Data Cleaning**:
   - Remove non-numeric symbols (e.g., commas) and convert the price columns to a float type.

3. **Return Calculation**:
   - Create a new "Returns" feature by dividing the current price by the previous day's price, and then apply a logarithmic transformation.

4. **Grouping by Ticker**:
   - Calculate the mean and standard deviation of returns for each ticker symbol and store this in a new DataFrame.

---

## Modeling and Visualization
1. **Initial Scatterplot**:
   - Plot mean returns against standard deviation in a scatterplot, labeling each data point with the corresponding ticker symbol.

2. **Outlier Removal**:
   - Calculate z-scores to filter out extreme outliers (those with z-scores beyond -3 or 3), as outliers can impact clustering results.

3. **Optimal Cluster Count**:
   - Create an elbow curve to determine the best number of clusters. The optimal value for \(K\) will be found at the "elbow" point.

4. **Clustering with K-Means**:
   - Fit a K-Means model to the DataFrame containing the mean and standard deviation of returns.

5. **Cluster Visualization**:
   - Plot the clusters with ticker symbols labeled to easily identify which stocks belong to each group.

6. **Results Saving**:
   - Save the clustering results in a DataFrame that includes ticker symbols, sectors, and cluster assignments for reference and additional analysis.

---

## Future Work
- **Data Expansion**: Expand to include more features, such as trading volume, to improve clustering accuracy.
- **Enhanced Modeling**: Experiment with other clustering algorithms (e.g., DBSCAN) to compare performance.
- **Interactive Visualization**: Develop interactive visualizations for easier data exploration.

---

## License
This project is open-source and available under the MIT License.
