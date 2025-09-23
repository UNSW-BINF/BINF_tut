## Test yourself SOLUTIONS

1. In your jupyter notebook, create new chunk for this question. In this chunk, write some code to access and print out the properties of the first two columns from the df variable.
You should have it loaded from the previous section:
```
from palmerpenguins import load_penguins
df = load_penguins()
```
Then: 
```
print(df.columns)
print(df['species']) 
len(df['species'])
col_names = df.columns 
print(df[col_names[1]])
```

2. In your jupyter notebook, create new chunk for this question. In this chunk, write some code to create two variables m and n that are correlated to each other. You can do this by first creating values for m. If you remember from last week, we generated a single value with the random package. Here, we can use the numpy package to generate multiple numbers. e.g., m = np.random.normal(0,1,100), where 0 is the mean, 1 is the standard deviation, and 100 is the number of values to generate. To get correlated values n, we generate some "noise" (e.g, noise = np.random.normal(0,0.1,100)) and add that signal to m (assigning it to n). Then plot m versus n variables (don't forget the "o" variable!). Note how we decreased the standard deviation when generating the noise signal. See what happens when you play around with that value by increasing and decreasing it and plotting those two graphs again.

```
import numpy as np 
import matplotlib.pyplot as plt
import scipy.stats as sps

sd = 0.5
m = np.random.normal(0,1,100)
noise = np.random.normal(0,sd,100)
n = m + noise
plt.plot(m, n, "o")

z = sps.spearmanr(m, n)
print(z)
```

3. In your jupyter notebook, create new chunk for this question. In this chunk, we will try to repeat similar plots with the iris dataset. Using the describe function, look at the variables in the iris dataset, and make a distribution plot for one of them. HINT, this dataset is part of the seaborn package: `iris = sns.load_dataset("iris")`

```
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib as plt

iris = sns.load_dataset("iris")
```
Look at it and make a distribution plot for one of the variables.
```
display(iris)
print(iris.columns)
sns.histplot(iris['sepal_width'],kde=True,bins=20, color="purple")
```
Another plot 
```
sns.histplot(iris['sepal_length'],kde=True,bins=20 )
```
 
4. In your jupyter notebook, create new chunk for this question. In this chunk, we will try to repeat similar plots with the iris dataset. Plot a multiple plot figure, with any variable in the iris dataset, across the four different plot types.

```
import matplotlib.pyplot as pltt
fig ,ax = pltt.subplots(figsize=(15,12), ncols=2,nrows=2)
sns.swarmplot(data=iris,x='species',y='petal_width',ax=ax[0,0],hue='species')
sns.violinplot(data=iris,x='species',y='petal_width',ax=ax[0,1])
sns.boxplot(data=iris,x='species',y='petal_width',ax=ax[1,0])
sns.barplot(data=iris,x='species',y='petal_width',ax=ax[1,1])
pltt.show()
```
Do a pairplot between all variables for the iris dataset.
```
sns.pairplot(iris, palette="mako", hue="species")
```
Plot a variable in the iris dataset with the four different plot types as shown above but with different colors.
```
fig ,ax = pltt.subplots(figsize=(15,12), ncols=2,nrows=2)
sns.swarmplot(data=iris,x='species',y='petal_width',ax=ax[0,0],hue='species', palette="mako")
sns.violinplot(data=iris,x='species',y='petal_width',ax=ax[0,1],hue='species', palette="rocket")
sns.boxplot(data=iris,x='species',y='petal_width',ax=ax[1,0],hue='species', palette="flare")
sns.barplot(data=iris,x='species',y='petal_width',ax=ax[1,1],hue='species')
pltt.show()
```
