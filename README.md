# Walmart Sales Forecasting & Study

## Overview
The primary goal of this project is to analyze weekly sales data from various retail outlets to derive meaningful insights through statistical analysis, exploratory data analysis (EDA), and predictive modeling. The project aims to answer key business questions related to sales trends, factors influencing sales, and to forecast future sales for each store.

## Dataset
The dataset Walmart_DataSet.csv contains 6435 rows and 8 columns, detailing weekly sales data for various Walmart stores. Each entry includes a store identifier (Store), the week of sales (Date), and the total sales for that week (Weekly_Sales). Additionally, the dataset records whether the week included a holiday (Holiday_Flag), the temperature on the sales day (Temperature), the regional fuel price (Fuel_Price), the Consumer Price Index (CPI), and the unemployment rate (Unemployment).

## EDA Key Steps
- The Date column, initially in object type (string), is converted to datetime format using pd.to_datetime() with the format specified as '%d-%m-%Y'.
- The dataset has zero missing values and duplicates.
- It is observed that the dataset includes values for 45 different Walmart stores at various locations.
- A histogram is created to visualize the distribution of Weekly_Sales across all stores using seaborn and matplotlib.
- Data was checked for outliers using the mean of sales data which is grouped on dates as this considers overall sales patterns and identifies sales data that deviates significantly from the overall mean. The outliers were ultimately not removed because this contained authentic data and was not an error in entry.
- Since the dataset contains information for 45 Walmart stores, each store's data is stored in separate dataframes within a dictionary (store), indexed by store number foe easier analysis of a particular store.

## Insights from Studiying Data
- Based on th study it was found that when Unemployment decreases, the Weekly Sales will increase.
- When considering overall weekly sales trends, there is an upward trend with yearly seasonality. However, on an individual store level, some stores exhibit downward trends.
- Sales increased significantly during periods of seasonality, specifically between holiday weeks, and the temperature was consistently lower during these times.
- On an individual store level, the Weekly Sales of 20 stores out of 45 are negatively correlated with CPI and 25 are positively correlated with CPI. Taken as a whole (Avg. Weekly sales based on each stores) Weekly Sales is slightly negatively correlated with CPI. So as the CPI increases the Weeky Sales will decrease.
- Stores 20, 4, 14, 13, 2 are the top five and stores 38, 36, 5, 44, 33 worst five performing stores. The weekly sales of Store 33 (the least performing) is 87.67% less than that of the top-performing store (Store 20).

## Sales Forecasting
- The Prophet library was utilized for sales forecasting across all stores.
- Holiday weeks, indicated by the Holiday_Flag column, were incorporated into the Prophet model to refine predictions by accounting for their impact on sales.
- Forecasts were generated with machine learning (45 different models for the forecasting of 45 different stores) for the next 12 weeks beyond the end date of the available data. The results, including forecast values and Prophet models, were stored in a dictionary for easy access when needed.
- The output from the trained model shows the forecasted values along with their upper and lower bounds, the trend, and various other additive and multiplicative components that contribute to the forecast.
- A forecast of the Collective Sales Trends of all the stores by grouping and taking the mean value of weekly sales based on each dates was also made.
