# DATA-ANALYSIS-EDA-
EDA OF ''AI GENERATED GHIBLI - STYLE TRENDS(2025'')


# EDA-Project

The provided code segment represents an Exploratory Data Analysis (EDA) conducted on a dataset concerning Ghibli style. The analysis is performed using Python within a Jupyter Notebook environment. Here's a concise overview of the code:

1. **Data Import and Libraries:**
   import pandas as pd
import numpy as np 
import matplotlib.pyplot as plt

import seaborn as sns
2. **Data Loading and Preprocessing:**
   
df=pd.read_csv("C:\\Users\\jacks\\Downloads\\archive\\ai_ghibli_trend_dataset_v2.csv")
df

3. **Data Transformation:**
   df.shape
df.head(10)
df.sample(10)
df.info()
df.duplicated().sum()
df.columns
df.isnull().sum()
df.dropna()
4. **Descriptive Statistics:**
   df.describe()
df.describe().T
5. **Exploratory Data Analysis (EDA) Visualizations:**
   - A series of visualizations are generated to provide insights into the dataset's characteristics.

   1 Pie Chart: Displays the distribution of platform within the dataset.
smg = df['platform'].value_counts()
smg
plt.figure(figsize=(8, 8))
plt.pie(smg,autopct='%1.1f%%',colors=['lightblue','lightcoral'],labels=smg.index)
plt.title('Distribution of platforms')

plt.show()
plt.axis('equal')


   2 Histogram: Shows the distribution of user_id, including a kernel density estimate.

plt.figure(figsize=(10, 5))
sns.histplot(df['user_id'],kde=True,bins = 30)

plt.title('distribution of user_id')
plt.xlabel('users')
plt.ylabel('count')
plt.show()

   3 Countplot: Illustrates the distribution of shares.
shares = df['shares'].value_counts()
shares
plt.figure(figsize=(10, 5))
sns.countplot(shares,palette='pastel')

plt.title('DISTRIBUTION OF SHARES')
plt.xlabel('SHARES')
plt.ylabel('count')
plt.show()
plt.xticks(rotation=30)
   4 Countplot: Represents the distribution of various likes.

likes = df['likes']
likes
plt.figure(figsize=(10, 5))
sns.countplot(likes,palette='pastel',)

plt.title('DISTRIBUTION OF various likes')
plt.xlabel('likes')
plt.ylabel('count')
plt.grid(True,axis='y')
plt.show()
plt.xticks(rotation=80)

   5 Histogram: Depicts the distribution  of top_comment, including kernel density.


tc = df['top_comment']
tc
plt.figure(figsize=(10, 5))
sns.histplot(tc,bins=20,kde=True,color='yellow')

plt.title('DISTRIBUTION OF TOP_COMMENTS')
plt.xlabel('top comments')
plt.ylabel('frequency')
plt.xticks(rotation=180)

plt.show()

   6 Countplot: Presents the distribution of likes across different platforms.
plt.figure(figsize=(10, 5))
sns.countplot(data=df,x='platform',hue='likes')
             

plt.title('DISTRIBUTION OF likes accross platforms')
plt.xticks(rotation=45)
plt.show()

   



   8 Scatter Plot: Shows the relationship between comments and likes.

plt.figure(figsize=(8, 5))
sns.scatterplot(data=df, x='comments', y='likes')
plt.title('Comments vs Likes')


plt.show()


   9 Box Plot and Violin Plot: Depict the relationship between prompt and user_id.
#box plot
plt.figure(figsize=(10,6))
sns.boxplot(data = df,x='prompt',y='user_id')
plt.title('PROMPT VS USER_ID')
plt.xticks(rotation=45)
plt.show()


#violin plot
plt.figure(figsize=(10,6))
sns.violinplot(data = df,x='prompt',y='user_id')
plt.title('PROMPT VS USER_ID')
plt.xticks(rotation=45)
plt.show()



   10 Box Plot and Violin Plot: Illustrates the connection between user_id and comments.
#box plot
plt.figure(figsize=(10,6))
sns.boxplot(data = df,x='user_id',y='comments')
plt.title('user_id and comments')
plt.xticks(rotation=45)
plt.show()


#violin plot
plt.figure(figsize=(10,6))
sns.violinplot(data = df,x='user_id',y='comments')
plt.title('user_id and comments')
plt.xticks(rotation=45)
plt.show()



   11 Bar Plot: Displays the average shares for different image_id.

# calculate the avg shares
avg_shares=df.groupby('image_id')['shares'].mean().reset_index()
avg_shares=avg_shares.sort_values(by='shares',ascending=False)
avg_shares

# bar plot
plt.figure(figsize=(8,6))
sns.barplot(data=avg_shares,x='image_id',y='shares',color='green')
plt.title('AVG SHARES BY IMAGE_ID')
plt.xlabel('IMG ID')
plt.ylabel('SHARES')
plt.xticks(rotation=45)

plt.show()
   12 Scatter Plot: Represents the relationship between file_size_kb and resolution.
 plt.figure(figsize=(8,5))
sns.scatterplot(data=df,x='file_size_kb',y='resolution',color='teal')
 plt.title('relation between file_size_kb and resolution')
plt.tight_layout()
plt.show()
   13 Box Plot and 1Violin Plot: Depict the relationship between style_accuracy_score and is_hand_edited.
#box plot 
plt.figure(figsize=(8,6))
sns.boxplot(data=df,x='is_hand_edited',y='style_accuracy_score')
plt.title('relation btwn style_accuracy_score and is hand edited')
plt.show()

#violin plot 
plt.figure(figsize=(8,6))
sns.violinplot(data=df,x='is_hand_edited',y='style_accuracy_score')
plt.title('relation btwn style_accuracy_score and is hand edited')

plt.show()

   14 Box Plot and Violin Plot: Illustrates the relationship between generation_time and creation_date.
#box plot 
plt.figure(figsize=(8,6))
sns.boxplot(data=df,x='creation_date',y='generation_time')
plt.title('relation btwn style_accuracy_score and is hand edited')
plt.xticks(rotation=45)
plt.show()
#violin plot 
plt.figure(figsize=(8,6))
sns.violinplot(data=df,x='creation_date',y='generation_time')
plt.title('relation btwn style_accuracy_score and is hand edited')
plt.xticks(rotation=45)
plt.show()

   15 Heatmap: Displays the correlation matrix between numerical columns.

numeric_colns = df.select_dtypes(include=['float64','int64'])
numeric_colns
cor = numeric_colns.corr()

#plot
plt.figure(figsize=(10,6))
sns.heatmap(cor,annot=True,cmap='coolwarm',fmt='.2f')
plt.title('correlation matrix')
plt.tight_layout()
plt.xticks(rotation=45)
plt.show()

   16 Pair Plot: Shows scatter plots for pairwise numerical relationships.
numeric_colns = df.select_dtypes(include=['float64','int64'])
numeric_colns
cor = numeric_colns.corr()

#plot
plt.figure(figsize=(7,6))
sns.pairplot(cor)
plt.suptitle('Pair plot of numerical relationships',y=1.02)
plt.show()

In summary, the code showcases a comprehensive EDA process aimed at gaining insights into AI GHIBLI TREND 2025 based on demographic attributes. The visualizations provide a better understanding of distribution patterns, relationships, and potential trends within the dataset.
