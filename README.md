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


