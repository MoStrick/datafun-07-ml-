# datafun-07-ml-
Introduction to Machine Learning: We'll employ a type of supervised learning, simple linear regression, to train a model using all available data and use the resulting model (a "best-fit" straight line) to make predictions. 
Project Title:


# Add files
Create README.md & .gitignore when creating respository
venv created when creating the virtual environemnt
Add file: requirements.txt


### Create Virtual Environment
# Navigate to the project directory
cd path/to/your/repository

# Create a virtual environment named 'venv'
python -m venv venv

# Activate the virtual environment
# macOS/Linux
source venv/bin/activate

# Install packages
pip install requests

# Deactivate the virtual environment when done
deactivate


### Install Dependencies
# Install any necessary packages
jupyterlab
numpy
pandas
pyarrow
matplotlib
seaborn
scipy
pymongo
pyspark
tensorflow
wordcloud

pip install jupyterlab numpy pandas pyarrow matplotlib seaborn scipy notebook pymongo pyspark tensorflow wordcloud

# Freeze the current state of installed packages
pip freeze > requirements.txt

# Deactivate the virtual environment when done
deactivate



### Saving Progress/ Commit Changes

# Check the status of your repository
git status

# Add all changes to the staging area
git add .

# Or add specific files to the staging area
git add filename

# Commit the changes with a descriptive message
git commit -m "Descriptive Message"

# Push the changes to the remote repository
git push origin main

# Or if your branch is named master
git push origin master




### Upload Files
Open Unit 10 in Finder
   Click and hold over folder in project open in VS Code
Open Unit 15 in Finder
   Click and hold over folder in project open in VS Code

# Part 1 & 2: Chapter 10
### CC 7.5 Chart a Straight Line (Ex 10.16 in textbook)
ipython --matplotlib
In [1]: c = lambda f: 5 / 9 * (f - 32)
In [2]: temps = [(f, c(f)) for f in range (0, 101,10)]
In [3]: import pandas as pd
In [4]: temps_df = pd.DataFrame(temps, columns=['Fahrenheit','Celsius'])
In [5]: axes = temps_df.plot(x='Fahrenheit',y='Celsius',style='.-')
In [6]: y_label = axes.set_ylabel('Celsius')
We obtained the January average high temperatures for New York City from 1895 through 2018 from NOAA’s “Climate at a Glance” time series at: https://www.ncdc.noaa.gov/cag
OR file in Unit 10: ave_hi_nyc_jan_1895-2018.csv
In [7]: nyc = pd.read_csv('ave_hi_nyc_jan_1895-2018.csv')
### Display beginning and end of table (first and last five rows)
In [8]: nyc.head()
In [9]: nyc.tail()
### Rename Column
In [10]: nyc.columns = ['Date','Temperature','Anomaly']
In [11]:nyc.head(3)
Remove 01 from the dates to create just columns
In [12]: nyc.Date.dtype
   Out[12]: dtype('int64'): floor division performs integer division on every element of the series
In [13]: nyc.Date = nyc.Date.floordiv(100)
In [14]: nyc.head(3)
### Calculating basic descriptive statistis for the data set
In[15]: pd.set_option('precision',2)
In [16]: nyc.Temperature.describe()
### Forecasting future values (SciPy)
In [17]: from scipy import stats
IN [18]: linear_regression=stats.linregress(x=nyc.Date,y=nyc.Temperature)
The opject returned by linregress contains the regression line's slope and y-intercept:
In [19]: linear_regression.slope
In [20]: linear_regression.intercept
To predict temperature in 2019 and 1890
In [21]: linear_regression.slope*2019+linear_regression.intercept
In [22]: linear_regression.slope*1890+linear_regression.intercept
### Create the scatterplot
Close the matplotlib window if you have not done so already, or it will use the existing window that already contains the graph
In[23]: import seaborn as sns
In [24]: sns.set_style('whitegrid')
In [25]: axes = sns.regplot(x=nyc.Date,y=nyc.Temperature)

In [26]: axes.set_ylim(10,70)


# Part 3 Ch 15
### Load data into dataframe
import matplotlib
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.model_selection import LinearRegression
import seaborn as sns
import numpy as np
import matplotlib.pylot as plt

nyc = pd.read_csv('ave_hi_nyc_jan_1895-2018.csv')

nyc.columns = ['Date','Temperature','Anomaly']

nyc.Date = nyc.Date.floordiv(100)

nyc.head(3)

### Splitting the Data for training and testing
X_train, X_test, y_train, y_test = train_test_split(nyc.Date.values.reshape(-1,1), nyc.Temperature.values,random_state=11)

X_train.shape

X_test.shape

### Training the Model
linear_regression = LinearRegression()
linear_regression.fit(X=X_train, y=y_train)

linear_regression.coef_

linear_regression.intercept_

### Testing the Model
predicted = linear_regression.predict(X_test)

expected = y_test

for p, e in zip(precidted[::5], expected[::5]): print(f'predicted: {p:.2f}, expected: {e:.2f}')

### Estimating Past and Predicting Future Temps
predict = (lambda x: inear_regression.coef_*x+linear_regression.intercept_)

predict (2019)

predict(1890)

### Visualizing the Data Set
axes = sns.scatterplot(data=nyc, x='Date', y='Temperature', hue='Temperature", palette='winter', legend=False)

^^The keyword arguments are:, which specifies the  () containing the data to display.  and , which specify the names of ’s columns that are the source of the data along the x- and y-axes, respectively. In this case,  is the  and  is the . The corresponding values from each column form x-y coordinate pairs used to plot the dots., which specifies which column’s data should be used to determine the dot colors. In this case, we use the  column. Color is not particularly important in this example, but we wanted to add some visual interest to the graph., which specifies a Matplotlib color map from which to choose the dots’ colors., which specifies that  should not show a legend for the graph—the default is , but we do not need a legend for this example

axes.set_ylim(10,70)

x = np.array([min(nyc.Date.values), max(nyc.Date.values)])

y = predict(x)

line = plt.plot(x,y)












