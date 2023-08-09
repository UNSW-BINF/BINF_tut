# Week 8: Data Viz
### Download data 
First things first! Download these palmer penguins data into your working directory. 
Into a terminal, type in: 
```
pip -q install palmerpenguins
```

### Installing and importing libraries 
```
pip install numpy
pip install pandas
pip install seaborn
```
Then, run an interactive python session in a terminal. In your python session:
```
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```
- Pandas is a library for working with tabular data. Based on the R data.frame library.
- Seaborn is a visulization package. 

### Importing data 
```
from palmerpenguins import load_penguins
df = load_penguins()
print(type(df))
df
```
### Summary statistics and properties 
```
df.describe()
df.dtypes
df.columns
```
### Indexing/accessing data in a data frame 
```
df.values
df.loc[i] 
df.iloc[i,j]
df[['bill_length_mm','island']]
df.query("year > 2007")

```

### Plotting 
```
sns.histplot(df['bill_length_mm'],kde=True,bins=20)
plt.show() 
```

```
sns.jointplot(data=df, x="bill_length_mm", y="bill_depth_mm")
plt.show() 
```

```
sns.pairplot(df)
plt.show() 
```

```
g = sns.boxplot(x = 'island',
            y ='body_mass_g',
            hue = 'species',
            data = penguins,
            palette=['#FF8C00','#159090','#A034F0'],
            linewidth=0.3)
g.set_xlabel('Island')
g.set_ylabel('Body Mass')
plt.show() 
```


```
g = sns.lmplot(x="flipper_length_mm",
               y="body_mass_g",
               hue="species",
               height=7,
               data=penguins,
               palette=['#FF8C00','#159090','#A034F0'])
g.set_xlabels('Flipper Length')
g.set_ylabels('Body Mass')
plt.show() 
```


