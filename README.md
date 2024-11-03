# MercadoLibre Search Trends Forecasting with Prophet

This repository contains a comprehensive time series analysis and forecasting project that examines search trends for MercadoLibre using Facebook's Prophet library. The goal of this project is to investigate patterns in hourly search data, detect seasonal behaviors, and produce a forecast that provides insights into potential fluctuations in search interest over time. This analysis aims to help the marketing and business strategy teams at MercadoLibre optimize their efforts based on search trends.

## Project Overview

In this project, we dive into Google search trends data for MercadoLibre, covering several years at an hourly granularity. Our analysis involves the following key steps:

1. **Data Preparation**: Prepares and cleans the search trends data, ensuring it meets the requirements for analysis with Prophet.
2. **Time Series Modeling with Prophet**: Uses Prophet to build a forecasting model, leveraging seasonality components to capture daily, weekly, and yearly trends.
3. **Seasonality Component Analysis**: Analyzes seasonal components individually to uncover the times of day, days of the week, and times of year when MercadoLibre experiences peak search interest.
4. **Forecasting and Visualization**: Generates a forecast that projects search traffic into the future, providing a reliable view of expected interest trends. This includes confidence intervals that help gauge the variability of the forecast.

Each step in this workflow builds on the previous one, culminating in a clear picture of MercadoLibre's search traffic trends and insights into how they might evolve over time.

## Data

The dataset used in this project consists of hourly Google search trends data for MercadoLibre. This data includes:
- **`ds` (datetime)**: Timestamp for each observation, set in hourly intervals.
- **`y` (search trends)**: The normalized search volume for MercadoLibre at each timestamp.

The data spans multiple years, allowing for a thorough investigation into seasonal patterns and long-term trends. 

## Key Analytical Steps and Code Walkthrough

### 1. Data Preparation and Cleaning

The initial phase involves preparing the data so it’s compatible with Prophet's requirements. This includes:
- **Resetting the Index**: Converting the datetime column from an index to a standard column named `ds` so that Prophet can recognize it as the time variable.
- **Renaming Columns**: Ensuring that the search trend column is labeled `y`, as Prophet expects `ds` and `y` as standard column names for time and target variable, respectively.
- **Handling Missing Values**: Removing any rows with NaN values to maintain data integrity and avoid issues during model training.

This phase ensures that the data is in the right format and free from inconsistencies, setting the stage for accurate modeling.

### 2. Building the Forecast Model with Prophet

Prophet, a robust time series forecasting library designed to handle seasonality, is used to model the data. Key steps include:
- **Model Initialization**: Creating a Prophet model object, which allows us to specify daily, weekly, and yearly seasonality.
- **Fitting the Model**: Training the model on the historical search trends data.
- **Creating Future Data**: Generating a DataFrame with a future timeframe, extending the forecast to 2000 hours (approximately 80 days) beyond the historical data.
- **Forecasting**: Using Prophet’s built-in prediction capabilities, we produce a forecasted dataset that includes:
  - **`yhat`**: The predicted values, representing the expected search volume.
  - **`yhat_lower`** and **`yhat_upper`**: The lower and upper bounds of a 95% confidence interval, providing an estimate of the prediction's variability.

This model allows us to project future search interest for MercadoLibre, offering insights into near-term popularity trends and aiding in strategic decision-making.

### 3. Seasonality Component Analysis

Prophet’s `plot_components` function provides a breakdown of the individual seasonality patterns in the search trends data, allowing us to analyze three main components:

- **Daily Seasonality**: This component reveals the time of day when search interest peaks. The analysis shows that search traffic is highest around midnight, indicating late-night activity as a significant driver of search volume.
  
- **Weekly Seasonality**: This component illustrates the days of the week with the highest and lowest search volumes. Our analysis finds that Tuesday experiences the highest search traffic, while weekends (particularly Sunday) tend to see a decrease in search interest.

- **Yearly Seasonality**: This component highlights seasonal trends over the course of a year. The analysis shows that the lowest point for search traffic occurs in early September, possibly indicating a period of lower interest due to seasonal factors.

By examining these seasonal components individually, we can identify critical periods for marketing focus and gauge potential fluctuations in search traffic based on typical user behavior patterns.

### 4. Visualizing the Forecast

With the forecasted data in hand, we proceed to visualize the results:
- **Forecast Plot**: A comprehensive plot showing `yhat`, `yhat_lower`, and `yhat_upper` over the last 2000 hours of data, illustrating the predicted range of search interest with its confidence interval.
- **Component Plots**: Detailed visualizations of the daily, weekly, and yearly seasonal components, as discussed above.

These visualizations make it easier to interpret the forecast and identify actionable insights, such as optimal times for marketing campaigns, by leveraging the natural ebbs and flows in search trends.

## Results and Insights

### Seasonality Insights

- **Time of Day**: Search traffic peaks around midnight, suggesting that MercadoLibre might benefit from late-night marketing strategies to capture this audience.
- **Day of the Week**: Tuesday sees the highest search volume, while weekends experience a decline, particularly on Sunday. This insight can inform the timing of ad placements and other promotional activities.
- **Calendar Year**: The lowest point in search traffic is observed in early September, hinting at a potential seasonal dip. This information can be used to optimize resource allocation during slower periods.

### Forecast Interpretation

The forecast model indicates that search interest for MercadoLibre follows a consistent, cyclical pattern, with predictable peaks and troughs across daily and weekly cycles. The confidence intervals in the forecast provide an understanding of the potential variability in search volume, which is essential for planning marketing activities with a degree of uncertainty in mind.

These insights are valuable for MercadoLibre's strategic planning, offering guidance on when to ramp up marketing efforts and when to anticipate natural dips in user interest.

## Repository Structure

```plaintext
.
├── forecasting_net_prophet.ipynb   # Jupyter Notebook containing the full analysis and code
├── README.md                       # Project README with detailed description
└── data/                           # Directory for raw data files (if available)


## Requirements

To replicate the analysis, you will need the following Python libraries:

- `pandas` for data manipulation and cleaning
- `matplotlib` for plotting and visualization
- `fbprophet` (Prophet) for time series forecasting

You can install these packages using:

```bash
pip install pandas matplotlib prophet


## Usage

To run the analysis:

1. Clone the repository:
    ```bash
    git clone <repository-url>
    ```

2. Navigate to the project directory:
    ```bash
    cd <repository-directory>
    ```

3. Open and execute the Jupyter notebook:
    ```bash
    jupyter notebook forecasting_net_prophet.ipynb
    ```

4. Follow along with the code and review the output visualizations to understand the trends and forecasts.

## Conclusion

This project provides a comprehensive analysis of MercadoLibre's search trends using Prophet. By examining daily, weekly, and yearly seasonality components, it uncovers patterns that can help inform marketing and operational strategies. The forecast model projects future search interest, offering valuable insights for optimizing timing and resource allocation in marketing.

## License

This project is licensed under the [MIT License](LICENSE). For more details, please see the LICENSE file in the repository.

