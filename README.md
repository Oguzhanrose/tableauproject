`Python`, `Pandas`, `Tableau`, `Dashboard`, `Interactive`, `Big Data`, `Data Cleaning`, `Data Visualizations`, `Basic Statistics`, `Business Intelligence`

# About Children World - Dashboard
The project is based on a dataset of an American company that specializes in production sale of children's products to businesses 
provided by Technical University of Denmark. This is a knowledge based project to learn a Business Intelligence (BI) tool as Tableau.
<br>
<p align="center"> <img src="./git_image/geographical_to_convert.gif" alt="Drawing"/> </p>
<br>

<br>
<p align="center"> <img src="./git_image/manager_and_customer_overview.gif" alt="Drawing"/> </p>
<br>

<br>
<p align="center"> <img src="./git_image/focus_on_trades.gif" alt="Drawing"/> </p>
<br>

## Problems with the geographical values

6 different datatypes are supported in Tableau. These are:

- Text(String) values 
- Date values
- Date & Time values
- Numerical values
- Boolean values
- Geographical values

Although we have geographical values in our dataset (TerritoryName) that supports both abbrevations for Denmark `DK` and Norway `NO`, the tool won't accept the abbreviation `SE` for Sweden. The visual in my worksheet looks like this, when using the feature TerritoryName as it is: 

<br>
<p align="center"> <img src="./git_image/raw_country_name_problem.png" alt="Drawing"/> </p>
<br>

This lead me to do some basic data wrangling with Python using the Pandas library:

<br>

<details>
<summary>Click to see the libraries</summary>

```python
# Import relevant library
import pandas as pd

# Load the raw data
df = pd.read_excel('data.xlsx')

# Correcting from abbreviation to full country name. To make tableau understand it.
df.loc[df['TerritoryName'] == "SE", 'TerritoryName'] = "Sweden"
df.loc[df['TerritoryName'] == "DK", 'TerritoryName'] = "Denmark"
df.loc[df['TerritoryName'] == "NO", 'TerritoryName'] = "Norway"

# Outputing the corrected dataframe as excel file
df.to_excel("cleaned_data.xlsx")  
```

</details>

<br>

## Steps against interactive dashboards

When the data finally is prepared and fulfill all the accepted datatypes listed above, we are ready to go. We first create worksheets, which contains a single view. Some of them are too easy to create, as it is drag and drop. But to do some specific visuals `Calculated field` are essential, which basically is to create new data from already existing data. This allow us to create new dimensions or measures, which will help us to describe the data even better. 

An example on calculated field is for instance the following code, which is used in many visuals for this project. 
```
# Deviation_budget_percentage
[Budget Deviation]/[Budget Amount]
```

To have many information in a single worksheet, it sometimes requires additionally drag and drop operations. An example on an illustration where additional drag and drop operations are applied, is for instance the scatter plot (last image at the very bottom of this readme file). The mark bar looks like the following image for that scatter plot:

<br>
<p align="center"> <img src="./git_image/additional_drag_drop.png" alt="Drawing"/> </p>
<br>

By draging the `Territory Name` feature into color, which has the data type *Text(String)*, the circles turns into colorcode of their respective country. By this functionalty the colors (Red, Blue and Orange) remains the same throughout all the three dashboards, for respectively (Sweden, Denmark and Norway). Another feature which is dragged is SUM of the `Budget Amount` *Numerical values* into the size, which makes the sizes of the circles big with respect to the budget amount each sales manager has been allocated to.  



## Dashboards for the Children World dataset

The next three illustration shows the static form of our interactive dashboards. To see the intractive ones please scrool up at the very top. And to see the dasboards yourself in action, please download `final_workbook.twbx`.


### 1.) Geographical overview

<br>
<p align="center"> <img src="./git_image/geographical_overview.png" alt="Drawing"/> </p>
<br>

### 2.) An overview of salesmanagers and customers

<br>
<p align="center"> <img src="./git_image/manager_and_customer_overview.png" alt="Drawing"/> </p>
<br>


### 3.) Focus on the trades 

<br>
<p align="center"> <img src="./git_image/focus_on_trades.png" alt="Drawing"/> </p>
<br>










