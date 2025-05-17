## dsa210-termproject
This is my term project for the course, DSA210: Introduction to Data Science, in the 2024-25 Spring term.

---
# Contents
- [Motivation](#motivation)
- [Plan](#plan)
  - [Data to be Used](#data-to-be-used)
  - [Plans on Collecting Data](#plans-on-collecting-data)
- [Data Analysis](#data-analysis)
- [Findings](#findings)
  - [Distribution of Variables](#distributions-of-variables)
  - [Descriptive Statistics](#distributions-of-variables)
  - [Cartographic Visualizations](#distributions-of-variables)
  - [Comparing the Variables](#comparing-the-variables-with-house-prices)
  - [Correlation Analysis](#comparing-the-variables-with-house-prices)
  - [Hypothesis Testing](#hypothesis-testing-1)
  - [Machine Learning Techniques](#machine-learning-techniques)
- [Limitations and Future Work](#limitations-and-future-work)
  - [Limitations](#limitations)
  - [Future Work](#future-work)
---

# Project Report

In this project, I will be exploring some essential factors that affect life in a location and their relation to **housing prices**, which will serve as an analog for the general demand of living in a specific place. Among these factors are:

- **Air quality**, crucial in the future of someone's health and quality of life.
- **Unemployment rate**, which determines the chances of a person being able to make a livelihood where they live.
- **Environmental risk**, something increasingly vital in an uncertain future riddled with climate change.

## Motivation

My interest in this project started with reflections on my life at university, and thoughts about what my life might look like in the future. Sabancı University's campus in Tuzla, İstanbul is in close proximity to an **'Organized Industrial Zone'** (OSB), an area of land designated by public authorities for industrial facilities. While this type of zoning can help industry work effectively and efficiently, it also produces a significant amount of pollution as a side effect of waste.

Students at our university often complain about the quality of the air, unpleasant smells, and difficulty breathing as a result of living and studying so close to the pollution. This situation has made me think more carefully about the qualities of where I will want to live and work after I graduate, especially the quality of the air everyone has to breathe. As I looked deeper into this matter, I became interested in how employment opportunities, and environmental risks, such the risk of natural disasters might influence people's decisions. These two matters are particularly relevant in Turkey, as they are hot-button issues, and they will especially be so for graduating students looking for work, soon including myself.

In conclusion, I wanted to find out whether people have taken air quality, unemployment, and environmental risk into account when buying houses. This question led to the conception of this project.

## Plan

My plan is to analyze if and how the main variable of interest, **housing prices** is affected by key environmental and economic variables. These variables are: the **Air Quality Index (AQI)**, a metric developed by environmental and meteorological agencies to quantify the air pollution levels of an area, the **rate of unemployment**, and the **environmental risk levels** across small administrative units. The area of focus will be the United States, which was attractive to use in my project due to its wide availability of data including those from small locations.

### Data to be Used

Currently, I intend to use the following data in the United States of America over a **per-county basis** (counties are the next largest level of administrative unit after the states.):

- **Housing prices**
- **AQI** (an indicator developed by agencies specializing in the environment to make the pollution in the air easily understandable)
- **Unemployment rate**
- **Environmental risk** (presented by environmental and disaster management agencies)

I will combine the relevant data so that every county is an object with the above data assigned to each of them as distinct variables.

### Plans on Collecting Data

I plan to obtain this data through publicly available online datasets and websites created by companies and organizations specializing in the relevant areas. The organizations and services I intend on collecting this data from are as follows:

1. **Housing**

- **Zillow**: A real-estate marketplace company in the U.S. that shares its meticulous data in various forms, including adjusted housing prices for research. This can be used for housing data. [Datasets are available here.](https://www.zillow.com/research/data/)

- **Redfin**: A real-estate broker firm that also shares similar data. This can also be used for housing data. [Datasets are available here.](https://www.redfin.com/news/data-center/)
  
  Either one of these sources, or both, can be used for housing data.

2. **Air Quality**
- **United States Environmental Protection Agency (EPA)**: Shares AQI recordings on an annual basis for every county (the administrative division one level below the state). This can be used for air quality data. [Datasets are available here.](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual)
  
- **IQAir**: A private Swiss air quality technology company that records and shares AQI data globally. This can also be used for air quality data. Datasets are available here. [(1)](https://www.iqair.com/usa) and [(2)](https://www.iqair.com/world-most-polluted-cities?continent=59af928f3e70001c1bd78e4f&country=7KEznm2wS6Zk3chh2&state=&sort=-rank&page=1&perPage=50&cities=)

  Either one of these sources, or both, can be used for housing data.

3. **Unemployment Rate**

- **United States Bureau of Labor Statistics**: A government organization that collects and shares data on the proportions of employed and unemployed people. This can be used for unemployment rate data. [Datasets are available here.](https://www.bls.gov/lau/tables.htm)

4. **Environmental Risk**

- **United States Federal Emergency Management Agency (FEMA)**: Develops a measure of environmental risk, known as the **Environmental Risk Index**, which is available for each individual county. [Datasets are available here.](https://hazards.fema.gov/nri/data-resources#csvDownload)

## Data Analysis

### Data Sourcing
- Among the data sources mentioned above, the following ended up being used for this project: House prices data from [Zillow](https://www.zillow.com/research/data/), Air quality data from the [EPA](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual), employment data from the [Bureau of Labor Statistics](https://www.bls.gov/lau/tables.htm), environmental risk data from [FEMA](https://hazards.fema.gov/nri/data-resources#csvDownload) were used.

- To make the processing of this data easier, two auxiliary datasets were obtained. One is a dataset that contained a standardized FIPS (Federal Information Processing Standard) code for every county in the United States. All datasets except for the AQI data had these codes present, and they were vital for matching every attribute to the correct locations. Many copies of this kind of data are available online. I used one from the [United States Department of Transportation](https://data.transportation.gov/Railroads/State-County-and-City-FIPS-Reference-Table/eek5-pv8d/about_data). The other is a dataset that combined these FIPS codes to a GeoJSON dataset for each county in the United States, this makes it possible to visualize the data in the form of an interactive map. This dataset was obtained from a [public GitHub repository](https://github.com/plotly/datasets/blob/master/geojson-counties-fips.json).

### Processing and Combining Data
- Since the obtained data is from public sources they are often quite large and contain a plethora of different observations. Only some of them were necessary for this project so the datasets were "filtered", cleaned, and then combined into a single dataset for further analysis. The notebook files in the repository outline these processes as well.

### Exploratory Data Analysis and Further Transformations
- The distributions of house prices, AQI, unemployment rate, and the risk index were obtained and analyzed using different plotting techniques such as histograms and boxplots. The variables' relation to house prices were obtained and analyzed by use of scatter plotting.
- A log-transformation was applied to house prices due to its skewness for the rest of the data analysis, the reasons will be further explained in the findings.

### Correlation Analysis
- The relationships between the variables were examined by use of a correlation matrix and were visualized.

### Hypothesis Testing
- The significance of the correlations between the house prices and the rest of the variables were analyzed by use of permutation testing their respective Pearson correlation coefficients, distributions of these tests and the observed correlations were visualized as well.

## Findings

### Distributions of Variables

#### 1. Air Quality Index
The following histogram shows the distribution of the median AQI that was recorded in a single year. The x-axis is the AQI that was recorded, and the y-axis are the frequency of that particular AQI reading across all counties. The distribution appears mostly normal and has a low variance from a mean of about 40.

![AQI_Histogram](https://github.com/user-attachments/assets/b54b7f99-28eb-4ac3-9ab5-4063b6c2264b)

The following boxplot shows the distribution of the median AQI values. The points between Q1 and Q3 are in a small margin ranging from approximately 35 to 45. The whiskers are slightly far away from the median. Some, but not many outliers are present as well, ranging from near 0 to about 80.

![AQI_Boxplot](https://github.com/user-attachments/assets/1afb6030-a565-4f6c-99bf-2d8026e09563)


#### 2. Unemployment Rate
The following histogram shows the distribution of the unemployment rate percentages that were recorded in a single year. The x-axis is the unemployment rate that was recorded for that county and the y-axis is the frequency of that rate. The distribution appears normal but is right skewed and has a low variance from a mean of about 4%.

![Unemployment_Histogram](https://github.com/user-attachments/assets/c8f367dc-58de-4ac1-9a94-5c18ac53ec31)

The following boxplot shows the distribution of the unemployment rates. Most of the data points are near the mean as shown in the histogram. The range between Q1 and Q3 is also small, from 3% to 4.5%. All of the outliers are on the right side, meaning most of the counties have lower unemployment. The outliers range from 7% to beyond 20%.

![Unemployment_Boxplot](https://github.com/user-attachments/assets/55f9ecc9-d02a-4b25-a67b-8e373acd939c)

#### 3. National (Environmental) Risk Index
The following histogram shows the distribution of the National Risk Index values that were calculated for each county in a single year. The x-axis is their Risk Index values and the y-axis is the frequency of those values. As the index increases, the frequency of the specific index values increases with it, levelling off and following an almost uniform distribution. This is expected as the Risk Index data is calculated in a percentile form comparing each county with fellow counties with similar attributes other than the environmental risk. As a result, all the values range from 0 to 100.

![NRI_Histogram](https://github.com/user-attachments/assets/2ee23438-9103-4bab-8371-b7073150dc45)

The following boxplot shows the distribution of the National Risk Index values. As observed in the histogram, almost completely uniform, with a median value only slightly above 50 and there are no outliers.

![NRI_Boxplot](https://github.com/user-attachments/assets/7c4ca38f-356d-4a2b-8d64-c630304258d8)

#### 4. Average House Prices

The following histogram shows the distributions for the average house price for every county in a single year. The x-axis is the house price (in millions of US Dollars), and the y-axis is the frequency of the prices. The distribution is **heavily right-skewed** and most houses are priced around the mean of around $170,000. While the average house price can reach up to $1,700,000 for some counties.
![AvgHouse_Histogram](https://github.com/user-attachments/assets/9302802a-44b0-4fc0-be0a-ae8e4babd8b7)

The following boxplot shows the distribution of the average house prices, too. A similar observation can be made here as with the histogram, most prices are grouped on the left while there are some outliers close to the whiskers, and there are also a few outliers very far away from the median. Q1, Median, and Q3 points are also quite close to each other.

![AvgHouse_Boxplot](https://github.com/user-attachments/assets/bf73460b-ff7c-447c-824e-eb5ae9d02975)

#### 5. Log-Transformed House Prices

Since our house price data is **heavily right-skewed**, this raw form can negatively impact the rest of our visualizations, testing, and analysis. This skewness can affect any attempt at machine learning on the data as well. In order to mitigate these problems, I will apply a logarithm transformation (taking the base-10 logarithm of each average house price value in the dataset) that will reduce the skewness and stabilize the variance.

The histogram and the boxplot of these new transformed house price values are as follows:

![LogHouse_Histogram](https://github.com/user-attachments/assets/267c3503-57be-4c9a-9349-ea3a4503772b)

![LogHouse_Boxplot](https://github.com/user-attachments/assets/069530c8-57ed-4660-8fe2-cc8e13b26d7b)

As it can be seen, the data much more resembles a normal distribution, with the mean value much better centered than before. The number of outliers has also been reduced, making analysis easier. We will use this form of the house prices for the rest of our analyses and hypothesis testing.

### Descriptive Statistics
The following numerical descriptive statistics were acquired from the data, here they're given in table form:
|               | Average House Price | Log-transformed House Price | Unemployment Rate (%) | National (Environmental) Risk Index | Median AQI |
|---------------|---------------------|-----------------------------|-----------------------|-------------------------------------|------------|
| **Count**     | 3,004               | 3,004                       | 3,004                 | 3,004                               | 995        |
| **Mean**      | $171,594            | 5.17                        | 3.93                  | 51.66                               | 39.35      |
| **Median**    | $143,815            | 5.15                        | 3.70                  | 52.06                               | 40         |
| **Std. Dev.** | $113,751            | 0.21                        | 1.38                  | 28.29                               | 9.67       |
| **Min.**      | $25,423             | 4.40                        | 1.3                   | 0                                   | 2          |
| **Max.**      | $1,797,555          | 6.25                        | 20.7                  | 100                                 | 81         |

### Cartographic Visualizations

Since our data is location-based, we can draw geographic maps showing the relationship between the counties pertaining to our data. Following are pictures of a map for each variable in the data, interactive versions are available in the notebook files. Lower values are light yellow while higher values are dark red, gray means that there was no data for that county. A legend is provided in the top-right corner.

#### 1. Median AQI
![AQI_Map](https://github.com/user-attachments/assets/6d208538-cd8a-414f-9b94-7cb5feb7535e)

#### 2. Unemployment Rate
![Unemployment_Map](https://github.com/user-attachments/assets/3f4b46e8-c232-4257-a6cd-ad365f0c63f7)

#### 3. National (Environmental) Risk Index
![NRI_Map](https://github.com/user-attachments/assets/bf9f512d-eeb6-4b3b-9865-1990722bb6a6)

#### 4. Log-transformed House Prices
![LogHousePrice_Map](https://github.com/user-attachments/assets/44de3928-5e91-426f-936e-bb725108bb7b)

### Comparing the Variables with House Prices

#### 1. Median AQI

The following scatter plot compares the distribution of the counties in terms of the AQI and the house prices. The x-axis is the AQI value, and the y-axis is the log-transformed house price value. Darker spots indicate that there is more than one point in that spot. The distribution appears to be quite uniform around the center, and there doesn't appear to be any distinguishable patterns, implying low if any correlation.

![AQI_Scatter](https://github.com/user-attachments/assets/ff9a8aba-ef9e-40d9-b716-ee3fbd8ed7f8)

#### 2. Unemployment Rate
The following scatter plot compares the distribution of the counties in terms of the unemployment rate and the house prices. The x-axis is the unemployment rate percentage value, and the y-axis is the log-transformed house price value. Darker spots indicate that there is more than one point in that spot. The distribution is concentrated around the left side, however there is a slight decline in house price as unemployment rises. The counties with higher house prices are more on the left-side (lower unemployment) than those with lower house prices, implicating some correlation.

![Unemployment_Scatter](https://github.com/user-attachments/assets/ce1b488c-5332-4d98-8958-7ae834ae23b6)

#### 3. National (Environmental) Risk Index
The following scatter plot compares the distribution of the counties in terms of the National Risk Index and the house prices. The x-axis is the Risk Index value, and the y-axis is the log-transformed house price value. Darker spots indicate that there is more than one point in that spot. The distribution is quite uniform. As the Risk Index value increases the points get more spread out have a slight inclination in terms of house prices. This might be implying that places with more valuable houses are in more environmental risk.

![RiskIndex_Scatter](https://github.com/user-attachments/assets/b3a4634b-97a1-4e68-afd7-b8c14758b3ac)

### Correlation Analysis
The heatmap illustration below shows the correlation coefficient values between the following variables: Log-transformed House Price, Average House Price, Median AQI, Unemployment Rate (%), National (Environmental) Risk Index. Some key observations are:
- Correlation between the Log-transformed house price and the AQI: **0.04**
  - Positive but very small correlation.
- Correlation between the Log-transformed house price and the Unemployment Rate: **-0.25**
  - Negative and slight correlation
- Correlation between the Log-transformed house price and the National Risk Index: **0.36**
  - Positive and slight correlation

  ![Corr_Matrix](https://github.com/user-attachments/assets/559bebb1-ad6c-4be6-ad21-ce9b1ea8f475)

### Hypothesis Testing

We will test the correlation of each variable (AQI, Unemployment Rate, Environmental Risk Index) with the log-transformed house prices to see if their correlations were significant or not. In order to prevent any disproportionality and variability, I will apply a min-max normalization on all of the values in the dataset. After that, we apply a permutation test for each pair of variables. Along with the numerical results, a graph of the distribution resulting from the permutation test and the observed correlation coefficient will be obtained.

#### 1. Median AQI and House Prices

- **Null Hypothesis (H<sub>0</sub>)**: There is **no correlation** between the **Median AQI** and the house prices.
- **Alternative Hypothesis (H<sub>1</sub>)**: There is **a correlation** between the **Median AQI** and the house prices.

A permutation test of 10,000 iterations was performed with a significance level of 0.05.

- **Results**:
  - Observed Correlation: 0.0406
  - p-value: 0.2108
  - **Fail to reject** the null hypothesis. This means that the observed correlation between the **Median AQI** and the house price is **not statistically significant**.
  
![AQI_Hypothesis](https://github.com/user-attachments/assets/826c0005-7c8b-4bfe-875d-fbeed6323c0c)

#### 2. Unemployment Rate and House Prices

- **Null Hypothesis (H<sub>0</sub>)**: There is **no correlation** between the **Unemployment Rate** and the house prices.
- **Alternative Hypothesis (H<sub>1</sub>)**: There is **a correlation** between the **Unemployment Rate** and the house prices.

A permutation test of 10,000 iterations was performed with a significance level of 0.05.

- **Results**:
  - Observed Correlation: -0.2380
  - p-value: 0.0002
  - **Reject** the null hypothesis. This means that the observed correlation between the **Unemployment Rate** and the house price is **statistically significant**.

![Unemployment_Hypothesis](https://github.com/user-attachments/assets/f22b3ff6-0d21-4610-8b2f-ea093c0b3719)

#### 3. National (Environmental) Risk Index and House Prices

- **Null Hypothesis (H<sub>0</sub>)**: There is **no correlation** between the **National Risk Index** and the house prices.
- **Alternative Hypothesis (H<sub>1</sub>)**: There is **a correlation** between the **National Risk Index** and the house prices.

A permutation test of 10,000 iterations was performed with a significance level of 0.050.

- **Results**:
  - Observed Correlation: 0.3260
  - p-value: 0.0002
  - **Reject** the null hypothesis. This means that the observed correlation between the **National Risk Index** and the house price is **statistically significant**.

![NRI_Hypothesis](https://github.com/user-attachments/assets/b25c6db7-8906-49c8-9183-961429324a90)

#### Conclusions for Hypothesis Testing

- **Air Quality Index (AQI)**
  - The correlation found in our data turned out to be not statistically significant. This revealed that there is not an apparent relationship between the air quality of a location and the house prices of that location.
- **Unemployment Rate**
   - The correlation found in our data turned out to be statistically significant. This revealed a negative relationship between the unemployment in a location and the house prices of that location. The negative relationship means we've found out that the higher the employment, the higher the house prices are. Although, it should be noted that the correlation value was not high.
- **National (Environmental) Risk Index**
   - The correlation found in our data turned out to be statistically significant. This revealed a positive relationship between the environmental risk and house prices. In hindsight, this appears contrary to my expectations when starting this project, when I expected that the safer a place is, the more the houses would be in demand. Instead, the data suggests that higher-risk counties have higher house prices. Again, it should be noted that the correlation value was not high.

### Machine Learning Techniques

After analyzing the relationship between the features, we will apply machine learning techniques to see how well we can use these relationships to predict the average house price of an area by taking into account the Unemployment Rate, Environmental Risk, and Air Quality.

Since our variables are entirely continuous and numerical, training regression models on our dataset is most appropriate. We will also scale our data using standardization (subtracting the mean and dividing by the standard deviation) for each feature to improve the performance of our regression models.

#### Multicollinearity

Before training models on our data, it is advisable to check for multicollinearity, as it can cause instability, increase variance, and reduce the statistical significance of our features. Although our earlier analysis showed relatively low correlation between our features, it is still important to check for multicollinearity.

The Variance Inflation Factor (VIF) of the predicting features was found as follows:
| Feature                             | VIF      |
|-------------------------------------|----------|
| Unemployment Rate (%)               | 1.001443 |
| National (Environmental) Risk Index | 1.136174 |
| Median AQI                          | 1.134710 |

The VIF values are low, indicating that there is no multicollinearity between our features.

#### Models and Parameters

Given our dataset is not very large (approximately 1,000 rows with no missing values, and 4 variables), model training time is not a major concern. We will train several regression models with various hyperparameter configurations on multiple folds of training and testing data to achieve the best results. The following models were trained with the following hyperparameters:

- **Multiple Linear Regression**
- **K Nearest Neighbors**
  - Number of neighbors ranging from 1 to 20
- **Decision Tree**
  - Maximum depth: values from 3 to 30
  - Minimum samples per leaf: values from 2 to 10
- **Random Forest**
   - Maximum depth: valeus from 5 to 10
   - Number of estimators: values from 50 to 500
Cross-validation was used to find the optimal parameters for each machine learning model. Results were scored using R² values. 
 
#### Results of Machine Learning and Conclusions

The optimal parameters of each model, along with their scores were found as follows:

| Model Name        | R²    | RMSE  | Optimal Parameters                               |
|-------------------|-------|-------|--------------------------------------------------|
| Linear Regression | 0.149 | 0.201 | (Not applicable)                                 |
| KNN               | 0.243 | 0.190 | 20-21 Neighbors                                  |
| DecisionTree      | 0.195 | 0.196 | 5 Max Depth and 10 Minimum Samples for Each Leaf |
| RandomForest      | 0.277 | 0.185 | 5 Max Depth and 100 Estimators                   |

Furthermore, each model was refitted on the entire dataset, and scatter plots were generated to compare predicted and actual house prices for each county.

![Machine Learning Grid Plot](https://github.com/user-attachments/assets/0ac7e210-f1dd-4da4-80f6-3a97e0c7c882)

It can be seen that the RandomForest model with a maximum depth of 5 and 100 estimators performed the best among the models, with an R² value of 0.277 and a root mean square error (RMSE) of 0.185. It should be said that the R² and RMSE values of each model are considerably low, though this was expected after our correlation analysis. The Pearson correlation coefficients of our data points were also quite low, and this likely contributed to our models' low performance.

We can observe this on the graphs drawn as well. The dashed red diagonal line represents a perfect prediction on every point in our model. Most predictions are clustered around the middle, with some outliers around the cluster. Ideally the data points would be following the red line more closely. This implies our models are predicting the same house price for many regions with different prices and attributes.

#### Analysis of the Linear Regression Model
While the multiple linear regression model has no hyperparameters, it does have intercept and coefficient values. The optimal linear regression model's intercept and coefficient values were found and placed into equation form:

$$ \text{Log-transformed\ House\ Price}\ =\ 5.2962\ +\ (-0.0492)\cdot\text{Unemployment\ Rate}\ +\ (0.0753)\cdot\text{National\ Risk\ Index}\ +\ (-0.0177)\cdot\text{Median\ AQI} $$

The coefficients are in line with our correlation values. The coefficients of the Unemployment Rate and Median AQI are negative, meaning they're related to lower house prices. While the National Risk Index's coefficient is positive, meaning it is related to higher house prices. The size of the regression equation's coefficients aligns with the size of the correlation coefficients. They are both clearly low.

## Limitations and Future Work

### Limitations
 - **Diversity of data**: The data collected was exclusively from the United States, which is a diverse country by itself but in comparison to the rest of the world it's very rich and developed.
 - **Types of data obtained**: While the house price data was meant to serve as an analog to the demand to live in a certain place, buying houses are simply not the only way people get to live somewhere. Renting houses, building new ones, and short-to-medium term homestays (such as AirBnB) were not included in the project.
 - **Timeframe**: The data that was used for all variables were from 2019 exclusively, which can be considered a limited view, and we may have missed any emerging or long-term trends.
 - **Narrow variables**: The variables used, such as house prices and unemployment, may be too dependent on macro-level attributes like the economy. To better isolate relevant trends, we would need to obtain additional data to account for these broader economic influences.
 - **Data availability**: The AQI data was only available for around 1,000 counties out of a total 3,000, less diverse data can affect the confidence in our findings.

### Future Work
 - **Expanding the geographic breadth of the data**: Data from other countries can be collected alongside the United States to enhance and strengthen our findings.
 - **Diversifying target variables**: More types of data can be collected alongside house prices such as: rent prices, tourism, homestays, population changes, house constructions etc. We can get a clearer picture of the demand to live in a certain place this way. This will improve our insights.
 - **Expanding the timeframe**: More data can be collected simply by increasing the time range, most of the data collected have archives from previous years as well.
 - **More general variables**: In order to do a fairer comparison, we might want to look at how house prices move independent of the economy or the housing market and move in line with our other variables like air quality, unemployment, and disaster risk. For this we need to obtain more data from these areas to serve as a controlling factor.
 - **Increasing sources for data**: Obtaining more data from other sources may also help to diversify and increase the quantity of our data, leading to more confident analysis.
