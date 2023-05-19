# Ex-09-Data-Visualization

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# DATA PREPROCESSING
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from google.colab import files
uploaded = files.upload()
df = pd.read_csv("tips.csv")
df
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/6bbf4a3f-930c-44d0-898d-60873a3e4faf)
```
df.isnull().sum()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/c376b840-1fb6-44a4-b986-9eafd07f386e)
# FINDING OUTLIERS
```
plt.figure(figsize=(8,8))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/c8c31aa2-9d51-471c-90ee-2a19f3132868)

# REMOVING OUTLIERS
```
plt.figure(figsize=(8,8))
cols = ['size','tip','total_bill']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
plt.title("Dataset after removing outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/32d36cde-c9c6-4909-b5ca-72d28ea0b086)

# 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x="day", y="total_bill", data=df)
plt.title("Total Bill Amount by Day of Week")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/89da3fd8-a8e8-4053-b77a-04eb68afe6fc)

# 2.What is the average tip amount given by smokers and non-smokers?
```
sns.boxplot(x="smoker", y="tip", data=df)
plt.title("Tip Amount by Smoking Status")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/effe6903-f2a6-49b2-9f47-99dec3c1bff7)

# 3.How does the tip percentage vary based on the size of the dining party?
```
df["tip_pct"] = df["tip"] / df["total_bill"]
sns.scatterplot(x="size", y="tip_pct", data=df)
plt.title("Tip Percentage by Dining Party Size")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/005642aa-f8c8-4647-a853-0ba71a760707)

# 4.Which gender tends to leave higher tips?
```
sns.boxplot(x="sex", y="tip", data=df)
plt.title("Tip Amount by Gender")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/4f1737c9-5027-422a-ae58-dc76b185518c)

# 5.Is there any relationship between the total bill amount and the day of the week?
```
sns.scatterplot(x="day", y="total_bill", data=df)
plt.title("Total Bill Amount by Day of Week")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/500c85a9-e354-452a-9557-d3879a341fef)

# 6.How does the distribution of total bill amounts vary across different time periods (lunch vs. dinner)?
```
sns.histplot(data=df, x="total_bill", hue="time", element="step", stat="density")
plt.title("Distribution of Total Bill Amounts by Time of Day")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/83f3217c-f607-49d5-bfa0-09dda67d5a0e)

# 7.Which dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x="size", y="total_bill", data=df)
plt.title("Average Total Bill Amount by Dining Party Size")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/06c8a388-765e-41b4-a440-7038362809de)

# 8.What is the distribution of tip amounts for each day of the week?
```
sns.boxplot(x="day", y="tip", data=df)
plt.title("Tip Amount by Day of Week")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/d7a8cc27-91cd-48e8-82ae-1245ae26a8a2)

# 9.How does the tip amount vary based on the type of service (lunch vs. dinner)?
```
sns.violinplot(x="time", y="tip", data=df)
plt.title("Tip Amount by Time of Day")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/febd7dab-168c-4937-aff2-70a6d5091830)

# 10.Is there any correlation between the total bill amount and the tip amount?
```
sns.scatterplot(x="total_bill", y="tip", data=df)
plt.title("Correlation between Tip Amount and Total Bill Amount")
plt.show()
```
![image](https://github.com/ManiKandan228/Ex-09-Data-Visualization/assets/119160414/6a6c4385-f9a3-47f9-ad4f-56357eedcf55)

# Result:
Thus, Data Visualization is performed on the given dataset and save the data to a file.
