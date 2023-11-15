# Data-Preprocessing-Analysis-for-the-Used-Car-Market
The primary objective of this project is to conduct a comprehensive data preprocessing analysis to understand and explore the behavior of the used car market. This preparatory analysis is crucial for conducting an effective Exploratory Data Analysis (EDA) and gaining valuable insights that can be used to make informed decisions.

## Documentation of the Code UC.ipynb

### Description
This Python code corresponds to a data analysis of car price variations based on different attributes such as brand, mileage, etc. The analysis is conducted in three main steps: data import and consolidation, data exploration and cleaning, and univariate and bivariate variable analysis.

### Step 1: Data Import, Load, and Consolidation
#### 1.1 Library Import
The pandas library is imported for data handling and analysis.
#### 1.2 Data Load
Several datasets (DataFrames) are loaded from CSV files, corresponding to different car brands.
#### 1.3 Data Consolidation
It is verified whether the DataFrames have the same structure, and if so, they are concatenated vertically into a single DataFrame named `merged_df`.

### Step 2: Data Exploration and Cleaning
#### 2.1 Identification of Duplicates
Duplicate records in the consolidated DataFrame (`merged_df`) are identified and displayed.
#### 2.2 Duplicate Cleaning
Duplicate records are removed from the consolidated DataFrame, and null values in certain columns are imputed.
#### 2.3 Imputation of Null Values
Null values in the columns 'fuel type', 'engine size', and 'mileage' are filled using secondary columns. Then, the secondary columns are removed, and null values in other columns are imputed using mean or mode, depending on the data type.
#### 2.4 Column Deletion
The columns 'reference' and 'tax(£)' are removed from the DataFrame.

### Step 3: Univariate Variable Analysis
An exploratory analysis of DataFrame variables after cleaning and imputation is performed. Histograms and distribution charts are generated to visualize the variable distribution.
#### 3.1 Analysis of Numeric Variables
Bar charts and histograms are generated to analyze the numeric variables of the DataFrame.
#### 3.2 Analysis of Relationships Between Variables
Relationships between numeric variables are explored through scatter plots and heatmaps.
#### 3.3 Categorical-Categorical Analysis
Categorical variables are analyzed using bar charts and stacked bar charts. Additionally, a chi-square analysis is performed to evaluate the association between the categorical variables "transmission" and "fuelType".

### Stacked Bar Chart
A stacked bar chart is created using seaborn. This chart shows the distribution of fuel types by transmission type. The legend is placed in the upper right corner, and the axes are appropriately labeled.

### Scatter Plots and Boxplots
Scatter plots and boxplots are generated using seaborn and matplotlib. These plots explore relationships between numeric and categorical variables, such as year vs price, engine size vs price, transmission type vs price, and fuel type vs price. The `clean_df_imputado` DataFrame is used to visualize these graphs.

### Correlation Analysis
Correlations between numeric and categorical variables are analyzed. A correlation matrix is used, and a heatmap is displayed using seaborn. Key interpretations of the correlations are detailed in code comments. Categorical variables are also encoded using the factorize method.

### Additional Charts
Additional charts are created to explore relationships between year and price, transmission type and price, and engine size and price. These charts provide a more detailed visualization of the associations between variables.

### Pairplot (Optional)
An optional pairplot graph using seaborn is included. This graph shows the distribution of each variable and relationships between pairs of variables. It can be useful for identifying general patterns in the data.

These additional code snippets complement the original data analysis and provide more detailed visualizations of relationships between variables in the `clean_df_imputado` DataFrame.

## OUTLIER ANALYSIS IN CAR FEATURES

### Dataset Description
An exploratory analysis of outliers has been conducted on a dataset containing information about car features such as year, price, tax, fuel efficiency (mpg), and engine size.

### Descriptive Analysis Results
#### Year (year):
The year ranges from 1970 to 2060. The maximum value of 2060 appears to be a data input or storage error.
#### Price (price):
The maximum price is 159999, a value that could be considered an outlier depending on the overall distribution of prices.
#### Tax (tax):
The maximum tax is 580, another value that could be considered an outlier, especially if most values are around 145.
#### Fuel Efficiency (mpg):
The maximum fuel efficiency is 470.8, a significantly higher value than the third quartile (Q3), suggesting the possibility of being an outlier.
#### Engine Size (engineSize):
The minimum engine size is 0, which could be an error or an outlier depending on the context of the data.

### Visualization of Outliers
Boxplots have been created to visualize the distribution and possible outliers in each of the mentioned features.

### Outlier Removal
The interquartile range (IQR) has been calculated for the 'year' feature, and upper and lower limits have been identified for outlier detection. Rows where the value in the 'year' column is outside these limits have been removed.

### Calculation of the Rest
Descriptive statistics, IQR, and upper and lower limits have been calculated for the remaining features (price, tax, mpg, engineSize). These values can be used to identify and address outliers in these variables.

## Feature Selection

### Description
In this stage, feature selection is carried out to improve the model's efficiency and reduce the complexity of the dataset. For this purpose, the chi-square (chi2) method is employed along with the SelectKBest technique.

### Used Libraries
- `sklearn.feature_selection`: chi2, SelectKBest
- `sklearn.model_selection`: train_test_split
- `sklearn.preprocessing`: MinMaxScaler
- `pandas`

### Definition of Variables and Min-Max Scaling
Relevant numeric variables for the model, such as "year", "tax", "mpg", and "engineSize", are identified. Subsequently, min-max scaling of these variables is performed.

### Dataset Division
The dataset is split into training (train) and test sets using train_test_split.

### Feature Selection with chi2 and k='all'
The chi-square method is used to assess the dependence between predictor variables and the target variable. The SelectKBest technique is employed with the parameter k='all' to select all available features.

### Selected Datasets Saved in CSV Files
Selected datasets based on identified relevant features are created. These datasets, both for training and testing, are saved in CSV files ("clean_price_train.csv" and "clean_price_test.csv," respectively) for further use.

In this step, feature selection has been completed, allowing for the preparation of the dataset for model training.
