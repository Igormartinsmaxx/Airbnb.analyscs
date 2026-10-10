%pip install pandas
"""Airbnb Project"""

import os
import pandas as pd

# Define the correct path of the CSV file (replace with the correct file name if necessary)
file_path = r"C:\\Users\silva\\OneDrive\\Área de Trabalho\\Aula Python\\Exe_Igor.py\\testeprecificacao.csv"

# Check if the file exists
if os.path.exists(file_path):
    # Load data into pandas
    df = pd.read_csv(file_path)
    
    # Display the first 5 rows of the DataFrame
    display("First 5 rows of the dataset:")
    display(df.head())
    
    # Display general dataset information (data types and non-null values)
    display("\nGeneral dataset information:")
    display(df.info())
    
    # Display descriptive statistics of the dataset (numeric columns only)
    display("\nDescriptive statistics:")
    display(df.describe())
else:
    display("Error: File not found. Check the path.")

# 1. Perform Exploratory Data Analysis (EDA), demonstrating the main 
# characteristics between variables and presenting some related business hypotheses.

import matplotlib.pyplot as plt
import seaborn as sns

# Configure plot style
sns.set_style("whitegrid")

# Create the price distribution histogram
plt.figure(figsize=(10, 5))
sns.histplot(df['price'], bins=50, kde=True)

# Limit the x-axis for better visualization (optional)
plt.xlim(0, 500)

# Add titles and labels
plt.title("Property Price Distribution")
plt.xlabel("Price (USD)")
plt.ylabel("Frequency")

# Show plot
plt.show()

# Create the bar chart for accommodation types
plt.figure(figsize=(8, 4))
sns.countplot(data=df, x='room_type', palette="pastel", order=df['room_type'].value_counts().index)

# Add titles and labels
plt.title("Distribution of Accommodation Types")
plt.xlabel("Accommodation Type")
plt.ylabel("Number of Properties")

# Show plot
plt.show()

# Create the boxplot to visualize price distribution by neighborhood group
plt.figure(figsize=(10, 5))
sns.boxplot(data=df, x='bairro_group', y='price', showfliers=False, palette="pastel")

# Limit the y-axis for better visualization (optional)
plt.ylim(0, 500)

# Add titles and labels
plt.title("Property Price by Neighborhood Group")
plt.xlabel("Neighborhood Group")
plt.ylabel("Price (USD)")

# Show plot
plt.show()

# Select only numeric columns
numeric_df = df.select_dtypes(include=['number'])

# Calculate the correlation matrix
correlation_matrix = numeric_df.corr()

# Create the heatmap
plt.figure(figsize=(10, 6))
sns.heatmap(correlation_matrix, annot=True, fmt=".2f", cmap="coolwarm", linewidths=0.5)

# Display the plot
plt.title("Correlation Matrix")
plt.show()
