# analyze
data analysis week 7
Task 1: Load and Explore the Dataset
Choose a dataset in CSV format (for example, you can use datasets like the Iris dataset, a sales dataset, or any dataset of your choice).
Load the dataset using pandas.
Display the first few rows of the dataset using .head() to inspect the data.
Explore the structure of the dataset by checking the data types and any missing values.
Clean the dataset by either filling or dropping any missing values.
Task 2: Basic Data Analysis
Compute the basic statistics of the numerical columns (e.g., mean, median, standard deviation) using .describe().
Perform groupings on a categorical column (for example, species, region, or department) and compute the mean of a numerical column for each group.
Identify any patterns or interesting findings from your analysis.
Task 3: Data Visualization
Create at least four different types of visualizations:
Line chart showing trends over time (for example, a time-series of sales data).
Bar chart showing the comparison of a numerical value across categories (e.g., average petal length per species).
Histogram of a numerical column to understand its distribution.
Scatter plot to visualize the relationship between two numerical columns (e.g., sepal length vs. petal length).
Customize your plots with titles, labels for axes, and legends where necessary.

**Task one**
import pandas as pd

# Load the dataset (replace 'your_dataset.csv' with the actual dataset file)
df = pd.read_csv("your_dataset.csv")

# Display the first few rows
print(df.head())

# Check data types and missing values
print(df.info())
print(df.isnull().sum())

# Clean dataset (fill missing values or drop them)
df = df.dropna()  # Alternatively, you can fill missing values using df.fillna(value)
print("Cleaned dataset:")
print(df.head())

**Task Two**
# Compute basic statistics of numerical columns
print(df.describe())

# Perform grouping on a categorical column (modify 'category_column' and 'numeric_column' as per dataset)
grouped_data = df.groupby("category_column")["numeric_column"].mean()
print(grouped_data)

# Identify patterns or interesting findings
correlation = df.corr()  # Finds relationships between numerical columns
print("Correlation Matrix:")
print(correlation)

**TASK THREE**
import matplotlib.pyplot as plt
import seaborn as sns

# Line chart (modify 'date_column' and 'value_column' as per dataset)
plt.figure(figsize=(10, 5))
df.plot(x="date_column", y="value_column", kind="line", title="Time-Series Trend")
plt.xlabel("Date")
plt.ylabel("Value")
plt.show()

# Bar chart
plt.figure(figsize=(10, 5))
sns.barplot(x="category_column", y="numeric_column", data=df)
plt.title("Comparison of Categories")
plt.xlabel("Category")
plt.ylabel("Average Value")
plt.show()

# Histogram
plt.figure(figsize=(10, 5))
sns.histplot(df["numeric_column"], bins=20, kde=True)
plt.title("Distribution of Numeric Values")
plt.xlabel("Value")
plt.ylabel("Frequency")
plt.show()

# Scatter plot
plt.figure(figsize=(10, 5))
sns.scatterplot(x="numeric_column1", y="numeric_column2", data=df)
plt.title("Scatter Plot of Two Numeric Features")
plt.xlabel("Feature 1")
plt.ylabel("Feature 2")
plt.show()

**IRIS**
from sklearn.datasets import load_iris
import pandas as pd

iris = load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
df["species"] = iris.target
print(df.head())

**ERROR HANDLING**
try:
    df = pd.read_csv("your_dataset.csv")
except FileNotFoundError:
    print("Error: Dataset file not found. Please check the filename or file path.")
except Exception as e:
    print(f"An error occurred: {e}")
    

