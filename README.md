# E-COMMERCE-CUSTOMER-SEGMENTATION-ANALYSIS
## INTRODUCTION
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This project aims to perform customer segmentation analysis for an e-commerce company using Python as the primary data analytics tool. By analyzing customer behavior and purchase patterns, the goal is to group customers into distinct segments to support targeted marketing strategies and improve customer satisfaction.  
The dataset provides a detailed view of customer transactions and interactions, offering insights into purchase frequency, spending habits, and engagement levels. This analysis will help businesses make data-driven decisions to enhance customer experience and optimize business strategies.

## PROBLEM STATEMENT
1. Descriptive Statistics
   - What is the average purchase value per customer?
   - What is the distribution of purchase frequency among customers?
   - What is the total revenue contribution of different customer groups?
2. Customer Segmentation
   - How can we group customers based on their purchasing behavior?
   - What are the optimal number of clusters for segmenting customers using K-means?
   - Are there outliers or unusual spending behaviors among customers?
3. Visualization & Insights
   - What do customer segments look like when visualized using scatter plots or bar charts?
   - How do average purchase value and frequency differ across segments?
   - Can we identify patterns or trends using heatmaps or distribution plots?
   - What visual insights can help in making data-driven marketing decisions?

## SKILLS AND CONCEPTS DEMONSTRATED
1. Data Handling & Preprocessing
2. Descriptive Analytics & Statistical Analysis
3. Customer Segmentation & Clustering
4. Data Visualization & Insights Communication
5. Business Application & Decision-Making
6. Python & Machine Learning Skills

## STAGES TO NAVIGATE IN THE E-COMMERCE CUSTOMER SEGMENTATION ANALYSIS PROJECT

The project comprises four critical stages essential for successful completion, which encompass:
1. Libraries and Data Importation
2. Data Assessment to Detect Data Quality Issues
3. Data Cleaning
4. Data Manipulation and Data Visualization

#### EXPLANATIONS
1. "Libraries and Data Importation":
   ---
   In a Jupyter Notebook, the first step is to import the necessary libraries, as they serve as the foundation for data analysis and visualization. The following libraries were used in this case:

- Pandas (pd) – for data importation and manipulation.
- NumPy (np) – for numerical computations.
- Datetime (dt) – for handling date-related operations.
- Matplotlib.pyplot (plt) and Seaborn (sns) – for data visualization.
- Warnings – to suppress unnecessary warnings during execution.
- Scipy.stats (pointbiserialr) – for statistical analysis.

  Once these libraries are imported, the next step is to load the sales dataset into the Jupyter Notebook environment as a DataFrame using the pd.read_csv() function. The 
  dataset is assigned to a variable named df, allowing easy reference throughout the analysis.
   
  Below is a snapshot of the code snippet used for importing libraries, loading the dataset, and displaying the DataFrame.

  LIBRARIES AND DATA IMPORTATION
  :-----------------------------:
  ![](Saless/library.png)

2. "Data Assessment to Detect Data Quality Issues":
   ---
Data assessment is a crucial step in evaluating imported data to ensure its suitability and cleanliness for analysis. In this case, a programmatic assessment was conducted using code, which is especially useful for large datasets with numerous rows and columns that cannot be manually inspected.

To assess the dataset, several Pandas functions and attributes were utilized:

- df.shape – Returns the dataset's dimensions (rows and columns). The dataset contains 350 rows and 11 columns.
- df.info() – Provides a summary of the DataFrame, including data types and memory usage. The output confirms that all columns have the correct data types.
- df.isnull().sum() – Counts missing values in each column. The result shows that the Satisfaction Level column has two missing values.
- df.duplicated().sum() – Identifies duplicate rows. The output confirms that no duplicate records are present.
- df['Satisfaction Level'].value_counts() – Examines the Satisfaction Level column to understand its unique categories and their frequencies. The results reveal three 
 distinct categories:
  - Satisfied: 125 occurrences
  - Unsatisfied: 116 occurrences
  - Neutral: 107 occurrences

Findings:  
Based on these assessments, the only detected data quality issue is the two missing values in the Satisfaction Level column..

These assessments and data quality issue detected are illustrated in the snapshots below. 
A    |B    
:---:|:---:
![](Saless/datass1.png)|![](Saless/datass2.png)

3. "Data Cleaning":
   ---
During the data assessment, it was discovered that the Satisfaction Level column contained two missing values. To address this, two possible approaches can be used:

a. Deleting the Rows – Since only two values are missing, removing them would have a negligible impact on the analysis.  
b. Filling the Missing Values – Instead of deletion, the missing values can be categorized appropriately. Typically, missing categorical values are assigned to the most frequent category. In this case, the Satisfied category appears most often. However, since there is also a Neutral category, it is more appropriate to classify the missing values as Neutral, as the customers could either be Satisfied or Unsatisfied.  
The df['Satisfaction Level'].value_counts() function was used to analyze the column and support this decision.

To implement this solution, the fillna() function from Pandas was applied:
```python
df['Satisfaction Level'].fillna('Neutral', inplace=True)
```
After executing this code, the missing values were successfully replaced with Neutral. To confirm the change, running df['Satisfaction Level'].value_counts() now shows that the Neutral category has 109 occurrences instead of 107, verifying that the update was effective.

The snapshots below illustrate the Satisfaction Level column before and after cleaning, highlighted in a yellow rectangular shape.
BEFORE CLEANING  |AFTER  CLEANING
:---------------:|:--------------:
![](before.png)|![](Saless/dataclean.png)

4. "Data Manipulation and Visualization (Analysis of the Problem Statement)":
   ---
### 1, Descriptive Statistics 
#### a. What is the average purchase value per customer?
   ---

   To calculate the average purchase value per customer, follow these steps:
   - Group purchases by customer ID using the groupby function and aggregate total purchase per customer using the sum() function, then store the result in a variable 
     called customer_purchases.
   - Compute the average purchase value by applying the mean() function to customer_purchases, storing the result in avg_purchase_value.
   - Print the result using formatted strings to display the final value, e.g., "Average Purchase Value per Customer: 845.38".  
   The code snippet used to achieve this is shown in the snapshot below.

   LIBRARIES AND DATA IMPORTATION  
   :-----------------------------:  
   ![](Saless/library.png)  
   
#### b. What is the distribution of purchase frequency among customers?
   ---
   To analyze the distribution of purchase frequency among customers, follow these steps:  
   - Count the occurrences of each unique Customer ID and store the result in a variable named purchase_frequency.
   - Generate summary statistics using the describe() function.
   - Print the results to understand the spread of purchase frequency.  
   The output reveals that every customer has made exactly one purchase, as indicated by the mean, standard deviation, and quartiles all equaling 1.  
   The snapshot below shows the code snippet used to achieve this:

   LIBRARIES AND DATA IMPORTATION  
   :-----------------------------:  
   ![](Saless/library.png) 

#### c. What is the total revenue contribution of different customer groups?
   ---
   To calculate the total revenue contribution of different customer groups, follow these steps:

   - Group customers by Customer ID and aggregate their total revenue using the sum() function, storing the result in customer_revenue.
   - Define spending categories based on quantiles (['Low', 'Medium', 'High', 'VIP']) and classify customers accordingly, storing the categorized data in 
     customer_revenue_groups.
   - Create a DataFrame to display the total revenue contribution of each customer group and store it in revenue_by_group.
   - Print revenue_by_group to analyze the distribution of revenue across different segments.
   The output is as follows:

   Customer Group  | Total Spend            
  :---------------:|:--------------:
  Low              |40,544.9
  Medium	          |55,181  
  High             |83,400.5
  VIP              |116,757.2

  The code snippet used to achieve this is shown in the snapshot below.
  
  LIBRARIES AND DATA IMPORTATION  
   :-----------------------------:  
   ![](Saless/library.png) 

### 1, Customer Segmentation
#### a. Group customers based on their purchasing behavior
   ---
   To group customers based on their purchasing behavior, you can use customer segmentation techniques. Here are some common methods:
   
  


 







