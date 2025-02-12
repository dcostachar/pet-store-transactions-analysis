# Pet Store Transactions Analysis: Uncovering Sales Insights with Python

Author: Charlene D'Costa <br />
Date: February 10, 2025 <br />
Coursework for the Meta Marketing Analytics Professional Certificate. <br />

[Pet Store Transactions Dataset](https://github.com/dcostachar/pet-store-transactions-analysis/blob/main/data/transactions.csv)

# Project Overview

<details>
  <summary>Defining the business problem.</summary>

<br />

For this project, I used Python to perform data cleaning and exploratory data analysis (EDA) on a fictitious pet store transactions dataset. I began by cleaning the data—handling missing values, removing data anomalies, and dropping columns with excessive nulls. Next, I conducted EDA to uncover product sales trends, analyze the quantity sold by category, and identify both the most popular and the highest-priced categories within different product lines. Finally, I created visualizations, including bar and box plots, to provide stakeholders with actionable insights on top-selling categories and price distributions, informing business decisions about which product lines drive the most revenue and where pricing adjustments might be considered.

</details>

# Data Cleaning

<details>
  <summary>Cleaning the data for analysis. </summary> 

<br />

In this section, I will import and clean the dataset to prepare it for analysis. I will use PyCharm as my integrated development environment (IDE) along with its Jupyter Notebook integration to perform the analysis. Additionally, I import the following libraries, which will be used throughout the project: pandas, matplotlib, and seaborn.


```python
# Importing libraries.
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Importing dataset.
df = pd.read_csv("./data/transactions.csv")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Order_Number</th>
      <th>Customer_ID</th>
      <th>Product_Name</th>
      <th>SKU</th>
      <th>Price</th>
      <th>Size</th>
      <th>Quantity</th>
      <th>Product_Category</th>
      <th>Product_Line</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Feline Fix Mix</td>
      <td>RKAPY3I1TP</td>
      <td>39.55</td>
      <td>NaN</td>
      <td>1</td>
      <td>treat</td>
      <td>cat</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Scratchy Post</td>
      <td>MPH6SCD7UT</td>
      <td>26.95</td>
      <td>NaN</td>
      <td>3</td>
      <td>toy</td>
      <td>cat</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Reddy Beddy</td>
      <td>DJWE1V9LZK</td>
      <td>23.07</td>
      <td>large</td>
      <td>3</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3/23/2020</td>
      <td>DG7-5410-5845-1340</td>
      <td>5929a0e9-95a7-4dbf-896e-c11d1988615e</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>NaN</td>
      <td>3</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3/23/2020</td>
      <td>DG7-5410-5845-1340</td>
      <td>5929a0e9-95a7-4dbf-896e-c11d1988615e</td>
      <td>Reddy Beddy</td>
      <td>KDTMPSBZKZ</td>
      <td>13.84</td>
      <td>small</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2898</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Cat Cave</td>
      <td>058G0P7V60</td>
      <td>29.66</td>
      <td>NaN</td>
      <td>1</td>
      <td>bedding</td>
      <td>cat</td>
    </tr>
    <tr>
      <th>2899</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Kitty Climber</td>
      <td>W86BRJ9SSG</td>
      <td>39.32</td>
      <td>NaN</td>
      <td>1</td>
      <td>toy</td>
      <td>cat</td>
    </tr>
    <tr>
      <th>2900</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Fetch Blaster</td>
      <td>M291KHJ4LW</td>
      <td>29.47</td>
      <td>NaN</td>
      <td>1</td>
      <td>toy</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>2901</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>NaN</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>2902</th>
      <td>12/10/2019</td>
      <td>6ZD-7972-0320-6653</td>
      <td>f2a090b3-ec77-4018-939e-1a18d2b4f4ef</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>NaN</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
  </tbody>
</table>
<p>2903 rows × 10 columns</p>
</div>




```python
# Using df.info() to display a concise summary of the DataFrame, including the index, column names, data types, non-null counts, and memory usage.
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Index: 2758 entries, 0 to 2902
    Data columns (total 10 columns):
     #   Column            Non-Null Count  Dtype  
    ---  ------            --------------  -----  
     0   Date              2758 non-null   object 
     1   Order_Number      2758 non-null   object 
     2   Customer_ID       2716 non-null   object 
     3   Product_Name      2758 non-null   object 
     4   SKU               2758 non-null   object 
     5   Price             2758 non-null   float64
     6   Size              626 non-null    object 
     7   Quantity          2758 non-null   int64  
     8   Product_Category  2758 non-null   object 
     9   Product_Line      2758 non-null   object 
    dtypes: float64(1), int64(1), object(8)
    memory usage: 237.0+ KB


### Question 1: Remove all rows that are missing either the `Product_Name` or the `Product_Category`.


```python
# Dropping rows where either the 'Product_Name' or the 'Product_Category' column has a missing value.
df = df.dropna(subset = ['Product_Name', 'Product_Category'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Order_Number</th>
      <th>Customer_ID</th>
      <th>Product_Name</th>
      <th>SKU</th>
      <th>Price</th>
      <th>Size</th>
      <th>Quantity</th>
      <th>Product_Category</th>
      <th>Product_Line</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Feline Fix Mix</td>
      <td>RKAPY3I1TP</td>
      <td>39.55</td>
      <td>NaN</td>
      <td>1</td>
      <td>treat</td>
      <td>cat</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Scratchy Post</td>
      <td>MPH6SCD7UT</td>
      <td>26.95</td>
      <td>NaN</td>
      <td>3</td>
      <td>toy</td>
      <td>cat</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Reddy Beddy</td>
      <td>DJWE1V9LZK</td>
      <td>23.07</td>
      <td>large</td>
      <td>3</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3/23/2020</td>
      <td>DG7-5410-5845-1340</td>
      <td>5929a0e9-95a7-4dbf-896e-c11d1988615e</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>NaN</td>
      <td>3</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3/23/2020</td>
      <td>DG7-5410-5845-1340</td>
      <td>5929a0e9-95a7-4dbf-896e-c11d1988615e</td>
      <td>Reddy Beddy</td>
      <td>KDTMPSBZKZ</td>
      <td>13.84</td>
      <td>small</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2898</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Cat Cave</td>
      <td>058G0P7V60</td>
      <td>29.66</td>
      <td>NaN</td>
      <td>1</td>
      <td>bedding</td>
      <td>cat</td>
    </tr>
    <tr>
      <th>2899</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Kitty Climber</td>
      <td>W86BRJ9SSG</td>
      <td>39.32</td>
      <td>NaN</td>
      <td>1</td>
      <td>toy</td>
      <td>cat</td>
    </tr>
    <tr>
      <th>2900</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Fetch Blaster</td>
      <td>M291KHJ4LW</td>
      <td>29.47</td>
      <td>NaN</td>
      <td>1</td>
      <td>toy</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>2901</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>NaN</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
    <tr>
      <th>2902</th>
      <td>12/10/2019</td>
      <td>6ZD-7972-0320-6653</td>
      <td>f2a090b3-ec77-4018-939e-1a18d2b4f4ef</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>NaN</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
    </tr>
  </tbody>
</table>
<p>2758 rows × 10 columns</p>
</div>



### Question 2: Find any clearly "incorrect" values in the `Price` column and clean the DataFrame to address those values.


```python
# Based on the earlier output from df.info(), we know that the 'Price' column is numeric (float64).
# Therefore, instead of checking for non-numeric data, we need to verify that the price values are valid.
# For example, negative prices are not acceptable.

# Check the minimum and maximum values of the 'Price' column.
# (A negative minimum indicates an invalid value.)
df.Price.min(), df.Price.max()

# Create a mask to retain only rows where 'Price' is greater than 0 and less than 15,000.
# This filters out any negative prices and any values that are unreasonably high.
valid_mask = (df.Price > 0) & (df.Price < 15000)

# Apply the mask to filter the DataFrame.
df = df[valid_mask]
```




    (np.float64(10.8), np.float64(39.55))



### Question 3: After you've done the cleaning above, remove any column that has more than 500 missing values.


```python
# From counting the number of missing values in each column, we see that the 'Size' column has over 500 missing values (2222 missing values).
df.isna().sum()

# Dropping the 'Size' column from the DataFrame.
df = df.drop(columns='Size')
```

### Question 4: Address the other missing values. You can replace the values or remove them, but whatever method you decide to clean the DataFrame, you should no longer have any missing values.


```python
# Using df.dropna() to remove any remaining rows that contain missing values.
df = df.dropna()

# Verifying that all missing values have been removed by counting the missing values in each column. Since there are none, we can move on.
df.isna().sum()
```




    Date                0
    Order_Number        0
    Customer_ID         0
    Product_Name        0
    SKU                 0
    Price               0
    Quantity            0
    Product_Category    0
    Product_Line        0
    dtype: int64


</details>

# Exploratory Data Analysis

<details>
  <summary>Uncovering patterns and analyzing relationships between variables. </summary>

### Question 5: Create a `Subtotal` column by multiplying the `Price` and `Quantity` values.


```python
# Creating 'Subtotal' column
df['Subtotal'] = df.Price * df.Quantity
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Order_Number</th>
      <th>Customer_ID</th>
      <th>Product_Name</th>
      <th>SKU</th>
      <th>Price</th>
      <th>Quantity</th>
      <th>Product_Category</th>
      <th>Product_Line</th>
      <th>Subtotal</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Feline Fix Mix</td>
      <td>RKAPY3I1TP</td>
      <td>39.55</td>
      <td>1</td>
      <td>treat</td>
      <td>cat</td>
      <td>39.55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Scratchy Post</td>
      <td>MPH6SCD7UT</td>
      <td>26.95</td>
      <td>3</td>
      <td>toy</td>
      <td>cat</td>
      <td>80.85</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5/22/2021</td>
      <td>SXF-7309-1727-1334</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c</td>
      <td>Reddy Beddy</td>
      <td>DJWE1V9LZK</td>
      <td>23.07</td>
      <td>3</td>
      <td>bedding</td>
      <td>dog</td>
      <td>69.21</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3/23/2020</td>
      <td>DG7-5410-5845-1340</td>
      <td>5929a0e9-95a7-4dbf-896e-c11d1988615e</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>3</td>
      <td>bedding</td>
      <td>dog</td>
      <td>84.12</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3/23/2020</td>
      <td>DG7-5410-5845-1340</td>
      <td>5929a0e9-95a7-4dbf-896e-c11d1988615e</td>
      <td>Reddy Beddy</td>
      <td>KDTMPSBZKZ</td>
      <td>13.84</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
      <td>13.84</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2898</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Cat Cave</td>
      <td>058G0P7V60</td>
      <td>29.66</td>
      <td>1</td>
      <td>bedding</td>
      <td>cat</td>
      <td>29.66</td>
    </tr>
    <tr>
      <th>2899</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Kitty Climber</td>
      <td>W86BRJ9SSG</td>
      <td>39.32</td>
      <td>1</td>
      <td>toy</td>
      <td>cat</td>
      <td>39.32</td>
    </tr>
    <tr>
      <th>2900</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Fetch Blaster</td>
      <td>M291KHJ4LW</td>
      <td>29.47</td>
      <td>1</td>
      <td>toy</td>
      <td>dog</td>
      <td>29.47</td>
    </tr>
    <tr>
      <th>2901</th>
      <td>10/16/2020</td>
      <td>P8K-8079-0264-6569</td>
      <td>468f40b3-59ca-47fd-9739-c7f19cf48f32</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
      <td>28.04</td>
    </tr>
    <tr>
      <th>2902</th>
      <td>12/10/2019</td>
      <td>6ZD-7972-0320-6653</td>
      <td>f2a090b3-ec77-4018-939e-1a18d2b4f4ef</td>
      <td>Snoozer Essentails</td>
      <td>GABWVMEL2R</td>
      <td>28.04</td>
      <td>1</td>
      <td>bedding</td>
      <td>dog</td>
      <td>28.04</td>
    </tr>
  </tbody>
</table>
<p>2714 rows × 10 columns</p>
</div>



### Question 6: Identify the most common `Product_Category` purchased for each `Product_Line`. Then, assign the name of that category (as a string) to the variables common_category_cat and common_category_dog.


```python
# Grouping the DataFrame by 'Product_Line' and 'Product_Category' and summing the numeric columns (e.g., Quantity) to identify the most purchased item for each Product Line (cat and dog).
df.groupby(['Product_Line', 'Product_Category']).sum()

# Based on the aggregated results, assigning the most common product category (i.e., the one with the highest total items sold) for each product line to the respective variables.
common_category_cat = 'treat'
common_category_dog = 'bedding'
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Date</th>
      <th>Order_Number</th>
      <th>Customer_ID</th>
      <th>Product_Name</th>
      <th>SKU</th>
      <th>Price</th>
      <th>Quantity</th>
      <th>Subtotal</th>
    </tr>
    <tr>
      <th>Product_Line</th>
      <th>Product_Category</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="4" valign="top">cat</th>
      <th>bedding</th>
      <td>9/21/20199/12/20209/14/20198/24/202111/6/20197...</td>
      <td>ENT-5271-0660-48509K8-5765-4461-7159G7Y-9331-8...</td>
      <td>d13c8860-67ae-44fb-8827-7afa9b4eec7a5c91c913-6...</td>
      <td>Cat CaveSnoozer HammockSnoozer HammockCat Cave...</td>
      <td>058G0P7V60V4B4RNS3ZPV4B4RNS3ZP058G0P7V60058G0P...</td>
      <td>8371.70</td>
      <td>526</td>
      <td>16733.96</td>
    </tr>
    <tr>
      <th>food</th>
      <td>6/30/20219/14/20191/27/202010/9/20198/24/20217...</td>
      <td>TCS-6223-7628-2720G7Y-9331-8313-29499FH-9267-0...</td>
      <td>aacbf226-43d2-4b06-987b-5c4224c11b9d5bc15bf9-0...</td>
      <td>Yum Fish-DishPurr MixYum Fish-DishPurr MixYum ...</td>
      <td>GZCJZ3ET04O5FYJLBE0HGZCJZ3ET04O5FYJLBE0HGZCJZ3...</td>
      <td>5957.41</td>
      <td>422</td>
      <td>11638.76</td>
    </tr>
    <tr>
      <th>toy</th>
      <td>5/22/20215/14/20209/12/20205/30/20219/14/20191...</td>
      <td>SXF-7309-1727-1334VQE-2656-9729-61949K8-5765-4...</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c041686b3-e...</td>
      <td>Scratchy PostFoozy MouseFoozy MouseFoozy Mouse...</td>
      <td>MPH6SCD7UT8PYSMLYINS8PYSMLYINS8PYSMLYINS8PYSML...</td>
      <td>10116.60</td>
      <td>851</td>
      <td>19651.79</td>
    </tr>
    <tr>
      <th>treat</th>
      <td>5/22/20211/5/20205/14/202011/2/202012/2/20191/...</td>
      <td>SXF-7309-1727-133414C-6286-0019-4676VQE-2656-9...</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821ce7b79f56-2...</td>
      <td>Feline Fix MixSnack-em FishFeline Fix MixPurrf...</td>
      <td>RKAPY3I1TPORGRBTIKZRRKAPY3I1TP28LQOI0LSKA8SU9C...</td>
      <td>11453.96</td>
      <td>1026</td>
      <td>22817.43</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">dog</th>
      <th>bedding</th>
      <td>5/22/20213/23/20203/23/20205/16/20215/14/20209...</td>
      <td>SXF-7309-1727-1334DG7-5410-5845-1340DG7-5410-5...</td>
      <td>476582ea-1bba-4289-8775-3fcd8074821c5929a0e9-9...</td>
      <td>Reddy BeddySnoozer EssentailsReddy BeddyReddy ...</td>
      <td>DJWE1V9LZKGABWVMEL2RKDTMPSBZKZDJWE1V9LZKI2GQUN...</td>
      <td>11906.83</td>
      <td>953</td>
      <td>24253.04</td>
    </tr>
    <tr>
      <th>food</th>
      <td>3/23/20205/14/20209/12/20205/30/20219/26/20203...</td>
      <td>DG7-5410-5845-1340VQE-2656-9729-61949K8-5765-4...</td>
      <td>5929a0e9-95a7-4dbf-896e-c11d1988615e041686b3-e...</td>
      <td>Whole Chemistry RecipeWhole Chemistry RecipeWh...</td>
      <td>6K4AUUS7306K4AUUS7306K4AUUS730NYW2F6CPBY6K4AUU...</td>
      <td>4593.70</td>
      <td>505</td>
      <td>9022.00</td>
    </tr>
    <tr>
      <th>toy</th>
      <td>1/5/20201/5/20206/30/20216/22/20217/25/20219/2...</td>
      <td>14C-6286-0019-467614C-6286-0019-4676TCS-6223-7...</td>
      <td>e7b79f56-2196-49a0-852a-3d329ad7cb57e7b79f56-2...</td>
      <td>Tug-a-BackChomp-a PlushFetch BlasterChomp-a Pl...</td>
      <td>IZBHF5KR793HDX5H4WTMM291KHJ4LW3HDX5H4WTMIZBHF5...</td>
      <td>9746.13</td>
      <td>662</td>
      <td>19605.11</td>
    </tr>
    <tr>
      <th>treat</th>
      <td>9/21/20199/14/20195/27/20217/7/20204/3/20195/2...</td>
      <td>ENT-5271-0660-4850G7Y-9331-8313-2949R3O-6541-4...</td>
      <td>d13c8860-67ae-44fb-8827-7afa9b4eec7a5bc15bf9-0...</td>
      <td>Chewie DentalChewie DentalAll Veggie YummiesAl...</td>
      <td>CG3531YP08CG3531YP08OWFPW3WZHGOWFPW3WZHGOWFPW3...</td>
      <td>7409.18</td>
      <td>453</td>
      <td>14207.34</td>
    </tr>
  </tbody>
</table>
</div>



### Question 7: Determine which categories (`Product_Category`) by `Product_Line` have the median highest `Price`. Assign the (string) name of these categories to their respective variables priciest_category_cat and priciest_category_dog.


```python
# Grouping the DataFrame by 'Product_Line' and 'Product_Category' and calculating the median 'Price' for each group to identify which product category has the highest median price within each Product Line (cat and dog).
df.groupby(['Product_Line','Product_Category'])['Price'].median()

# Based on the median prices calculated above, assigning the name of the product category with the highest median price for each product line to the respective variables.
priciest_category_cat = 'bedding'
priciest_category_dog = 'toy'
```




    Product_Line  Product_Category
    cat           bedding             29.66
                  food                24.53
                  toy                 16.71
                  treat               19.96
    dog           bedding             28.04
                  food                18.53
                  toy                 29.47
                  treat               25.48
    Name: Price, dtype: float64

</details>

# Data Visualization

<details>
  <summary>Using the matplotlib and seaborn libraries to create visualizations.</summary>

### Question 8: You want to emphasize to your stakeholders that the total number of product categories sold differ between the two `Product_Line` categories ('cat' & 'dog'). Create a horizontal bar plot that has `Product_Category` on the y-axis and the total number of that category sold (using the `Quantity`) by each `Product_Line` category. Also change the axis labels to something meaningful and add a title.


```python
# Creating a horizontal bar plot that meets the question requirements.
ax = sns.barplot(data=df, y='Product_Category', x='Quantity', estimator=sum, ci=None, hue='Product_Line')

# Setting a meaningful title and labels.
ax.set_ylabel('Product Category')
ax.set_xlabel ('Total Products Sold')
ax.set_title = ('Total Number of Products Sold')

```

    /var/folders/73/442cck753ndc4t4bclgcnbr80000gn/T/ipykernel_41509/1645217559.py:2: FutureWarning: 
    
    The `ci` parameter is deprecated. Use `errorbar=None` for the same effect.
    
      ax = sns.barplot(data=df, y='Product_Category', x='Quantity', estimator=sum, ci=None, hue='Product_Line')



    
![png](pet-store-transactions-analysis_files/pet-store-transactions-analysis_22_1.png)
    


### Question 9: Based on the plot from Question 8, what would you conclude for your stakeholders about what products they should sell? What would be the considerations and/or caveats you'd communicate to your stakeholders?


```python
answer_to_9 = '''
Based on the visualization, I would advise stakeholders to focus on treats for cats and bedding for dogs, as these appear to be the most popular products within their respective product lines, with toys also performing well. However, it's important to note that this analysis is based on a single dataset, which may not be the most up-to-date or account for seasonal trends.
'''
```

### Question 10: Create an explanatory visualization that gives business stakeholders deeper insights into product sales trends.


```python
# Creating a box plot
ax = df.Price.plot.box()

answer_to_10 = '''
I created a box plot to illustrate the distribution of product prices. The plot reveals that most product prices fall between approximately $17 and $35, with some notable outliers—prices as high as around $40 and as low as $11 or $12. This visualization not only highlights the central tendency and variability in pricing but also helps stakeholders understand the overall price range of the products. Such insights can inform pricing strategies, inventory decisions, and identify opportunities for adjustments to maximize revenue.
'''
```


    
![png](pet-store-transactions-analysis_files/pet-store-transactions-analysis_26_0.png)
    
</details>
