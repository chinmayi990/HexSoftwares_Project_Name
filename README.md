import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd 

# Load Titanic dataset
titanic_df = pd.read_csv("Titanic Dataset.csv")
print(titanic_df.head())

# Drop rows with missing Age or Fare for relevant plots
titanic_df = titanic_df.dropna(subset=['Age', 'Fare'])
sns.set(style="whitegrid")

# 1. Age vs Survival 
plt.figure(figsize=(8, 5))
sns.boxplot(x='Survived', y='Age', data=titanic_df)
plt.title("Age vs Survival")
plt.xlabel("Survived (0 = No, 1 = Yes)")
plt.ylabel("Age")
plt.show()

# 2. Fare vs Survival 
plt.figure(figsize=(8, 5))
sns.boxplot(x='Survived', y='Fare', data=titanic_df)
plt.title("Fare vs Survival")
plt.xlabel("Survived (0 = No, 1 = Yes)")
plt.ylabel("Fare")
plt.ylim(0, 100)  
plt.show()

# 3. Age distribution by Survival 
plt.figure(figsize=(8, 5))
sns.histplot(data=titanic_df, x='Age', hue='Survived', bins=30, kde=True, element="step")
plt.title("Age Distribution by Survival")
plt.xlabel("Age")
plt.ylabel("Count")
plt.show()

# 4. Age vs Pclass by Survival 
plt.figure(figsize=(8, 6))

# Ensure 'Survived' is binary for split=True
if titanic_df['Survived'].nunique() == 2:
    sns.violinplot(x='Pclass', y='Age', hue='Survived', data=titanic_df, split=True)
else:
    sns.violinplot(x='Pclass', y='Age', hue='Survived', data=titanic_df)
plt.title("Age Distribution by Pclass and Survival")
plt.xlabel("Passenger Class")
plt.ylabel("Age")
plt.show()

# 5. Fare vs Pclass by Survival 
plt.figure(figsize=(8, 6))
sns.boxplot(x='Pclass', y='Fare', hue='Survived', data=titanic_df)
plt.title("Fare Distribution by Pclass and Survival")
plt.xlabel("Passenger Class")
plt.ylabel("Fare")
plt.ylim(0, 150)
plt.show()

[Proj 1.ipynb](https://github.com/user-attachments/files/22196813/Proj.1.ipynb)
[hexa Project1 report .pdf](https://github.com/user-attachments/files/22196815/hexa.Project1.report.pdf)


