# Housing Price Prediction USA

## 1. OBJECTIVE 
To analyze publicly available data on economic, demographic, and real estate indicators to build a predictive model that explains the impact of these factors on the S&P/Case-Shiller Home Price Index, a key indicator of U.S. home prices, over the last two decades.

## 2. INTRODUCTION
The S&P CoreLogic Case-Shiller Home Price Indices hold significant importance in tracking the fluctuations of single-family home prices throughout the United States. These indices serve as invaluable tools for comprehending the dynamics of the housing market, offering insights crucial for monitoring price trends. Central to this system is the S&P CoreLogic Case-Shiller U.S. National Home Price Index, providing a comprehensive overview of the collective worth of single-family homes nationwide. It achieves this by aggregating data from nine distinct regions, with updates issued monthly. Additionally, focusing on city indices allows for a detailed examination of price variations within specific geographic markets, covering 20 major metropolitan areas. These areas are further categorized into two composites, one comprising 10 metro areas, and the other encompassing all 20. Notably, these indices maintain a consistent level of quality, enabling accurate measurement of percentage changes in housing prices while mitigating variations stemming from factors like house types, sizes, or physical attributes.


## 3.DATA COLLECTION 
- Download the data as .csv from below links:- 
1. **gdp_per_capita**:- Real gross domestic product per capita: https://fred.stlouisfed.org/series/A939RX0Q048SBEA
   
2. **disposable_personal_income**:- Real Disposable Personal Income: https://fred.stlouisfed.org/series/DSPIC96

3. **unemployment level**:- Unemployment Level: https://fred.stlouisfed.org/series/UNEMPLOY

4. **population**:- Population, Total for United States : https://fred.stlouisfed.org/series/POPTOTUSA647NWDB

5. **cpi**:- Consumer Price Index: All Items: Total for United States: https://fred.stlouisfed.org/series/CPALTT01USM657N

6. **inflation**:- Inflation, consumer prices for the United States: https://fred.stlouisfed.org/series/FPCPITOTLZGUSA

7. **house_price_index**:- S&P CoreLogic Case-Shiller U.S. National Home Price Index: https://fred.stlouisfed.org/series/CSUSHPISA

8. **privately_owned_house**:- New Privately-Owned Housing Units Started: Total Units: https://fred.stlouisfed.org/series/HOUST

9. **interest_rate**:- Interest Rates, Discount Rate for United States: https://fred.stlouisfed.org/series/INTDSRUSM193N

10. **labour_force_rte**:- Infra-Annual Labor Statistics: Labor Force Total: 15 Years or over for United States: https://fred.stlouisfed.org/series/LFACTTTTUSM657S

11. **homeownerdhip_rate**:- Homeownership Rate in the United States: https://fred.stlouisfed.org/series/RSAHORUSQ156S

12. **residential_construction_spending**:- Total Construction Spending: Residential in the United States: https://fred.stlouisfed.org/series/TLRESCONS

13. **NASDAQCOM**:- NASDAQ Composite Index: https://fred.stlouisfed.org/series/NASDAQCOM

14. **median_sale_price**:- Median Sales Price for New Houses Sold in the United States: https://fred.stlouisfed.org/series/MSPNHSUS

15. **privately_owned_house**:- New Privately-Owned Housing Units Authorized in Permit-Issuing Places: Total Units: https://fred.stlouisfed.org/series/HSN1F

16. **house_sold**:- New One Family Houses Sold: United States: https://fred.stlouisfed.org/series/PERMIT

## 4. DATA PREPARATION
- Convert the **NASDAQ Composite Index (NASDAQCOM)** from daily to monthly frequency by taking the mean of the monthly data.
- Convert the **Real gross domestic product per capita (gdp_per_capita)** from quarterly to monthly frequency using forward filling.
- Convert the **Population, Total for United States (population)** from annually to monthly frequency using forward filling.
- Convert the **Inflation, consumer prices for the United States (inflation)** from annually to monthly frequency using forward filling.
- Convert the **Homeownership Rate in the United States (homeownership_rate)** from quarterly to monthly frequency using forward filling.
- Ensure that all other data has a monthly frequency.
- Merge all the datasets based on the DATE column.
- Filter out data from January 1st, 2000 onwards.

## 5. EXPLORATORY DATA ANALYSIS
#### Strong Positive Correlations with house_price_index:
- gdp_per_capita (0.94)
- median_sale_price (0.95)
- disposable_personal_income (0.86)
- NASDAQCOM (0.9) 
- population (0.79)
- residential_construction_spending (0.9)
- inflation (0.7)

#### Negative Correlations with house_price_index
- houseowneship_rate (-0.33)
- interest_rate (-0.33)
- unemployment_rate (-0.31)

#### Weak correlation with house_price_index
- PERMIT (0.2)
- cpi (0.19)
- privately_owned_house (0.15)
- house_sold (-0.047) 
- labour_force_rate (-0.042)
  

## 6. MODEL EVALUATION
Regression models including Linear, Lasso, Ridge, BayesianRidge, and Elastic Net were utilized to analyze the influence of the mentioned factors on the S&P/Case-Shiller Home Price Index. These models serve a dual purpose, aiding in feature selection and mitigating challenges like multicollinearity and overfitting. The top-performing model was then employed to predict the output for the test data. Evaluation of the model's performance was carried out using the R-squared metric (coefficient of determination), with a value approaching 1 indicating excellent model performance and a value close to 0 suggesting poor performance.

## 7. CONCLUSION
- R-squared (uncentered): 0.986 indicates a very strong relationship between the independent and dependent variables, suggesting that the model provides an excellent fit to the data and that the independent variables explain a large proportion of the variability in the dependent variable.

- F-statistic: 923.4 indicates that the regression model is statistically significant, suggesting that the included predictors collectively have an effect on the dependent variable. It provides valuable information about the overall fit and usefulness of the regression model in explaining the variability in the dependent variable.

- The p-value of variables **NASDAQCOM, gdp_per_capita, houseownership_rate and median_sale_price** is less than 0.05 or 5% significance level that means there is strong evidence to reject the null hypothesis that the coefficient is zero, suggesting that these variables has a significant effect on the dependent variable i,e house_price_index.


## How to run the project
### STEP 1: Download .csv files from the given links
### STEP 2: Run file "data_collection.ipynb"
### STEP 3: Run file "housing_price_prediction.ipynb"
