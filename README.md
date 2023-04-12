<h1 align="center" style="color:MediumSeaGreen;"> <b> Loading-Multiple-Files-In-Python   </b></h1>

# Preface
At the beginning of every data science project, the primary goal is always to load datasets. However, when dealing with multiple files, it can often lead to the question of "how do I go about loading all this data?" based on my experience.
# Data 
In this small project, I will demonstrate a simple approach to loading 20 CSV [European cities](https://zenodo.org/record/4446043#.Y9Y9ENJBwUE) files using SSIS package, as opposed to an alternative method with Python.
# Loading Files 
## SSIS 
* One option available in SSIS is the for loop container, which can be used to load and combine multiple files. However, this approach requires a good understanding of the SSIS tool and SQL.

<img src="https://github.com/Piettro314/Loading-Multiple-Files-In-Python/blob/main/Content/SSIS%20Loading.gif" align="center">

Please refer to the complete project where the entire ETL package was used [AirBnB Project](https://github.com/Piettro314/Data-Visualization--AirBnB-Europe).

## Python 

<img src="https://github.com/Piettro314/Loading-Multiple-Files-In-Python/blob/main/Content/Python.png" align="center" width="100%">

---

When it comes to the question of how to load a large amount of data, Python makes it simple and straightforward using 'glob'.
```
import glob as glob
import pandas as pd
```
* glob is a module in Python's standard library that provides a way to retrieve files/pathnames that match a specified pattern.

```
# Location of the csv files needed to load
path = './data/*.csv'

# Load all the CSV files into a single dataframe
result = pd.concat([pd.read_csv(file) for file in glob.glob(path)], ignore_index=True)
```
* Once the path has been defined, a list comprehension with the pandas library is used to iterate through each CSV file retrieved by `glob.glob` from the specified path. For each file, `pd.read_csv` is used to read the data and `pd.concat` is used to concatenate it with the other files.

# Video Explanation


See video link here for explanation

# Recommended Uses
The technique of utilizing glob is highly beneficial for rapid analysis of multiple datasets due to its speed and the requirement of minimal code. This means that Exploratory Data Analysis can be performed prior to transitioning to a more robust tool like SSIS for handling all the data preparation tasks with components like for loop containers, data flow tasks, flat file sources, and more.

