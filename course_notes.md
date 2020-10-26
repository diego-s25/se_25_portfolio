**<span style="text-decoration:underline;">Data manipulation with pandas</span>**

Basic dataframe knowledge:

- Print a dataframe:

  print(dataframe)

* Return first few rows of a dataframe:

  dataframe.head()

- Display dataframe’s names of columns and if they have any missing values:

  dataframe.info()

* Return dataframe number of rows and columns:

  dataframe.shape

* Return dataframe’s summary statistics:

  dataframe.describe()

- Return dataframe values in 2 dimensional numpy array:

  Dataframe.values

* Return column names and row names respectively:

  Dataframe.columns

  Dataframe.index

Sorting and subsetting:

- Sort a dataframe by a column value:

  dataframe.sort_values(“column_name”)

  \*Passing parameter ‘ascending=False’ reverses order

  \*You can sort by multiple columns by passing a list of values


    *You can set which order these multiple columns are ordered by you can pass a list to the ‘	‘ascending’ parameter

- Subsetting columns:

  Dataframe[“column_name”]

  \*You can subset multiple columns by passing a list of column names instead

* Subsetting rows:

  Dataframe[dataframe[“*column_name*”] > | = | &lt; _value_]


    *You can subset based on multiple conditions by first assigning individual conditions to variables and then passing the variables as parameters (e.g. ‘dataframe[is_x & is_y]’

- Subsetting using .isin()

  Is_black_or_brown = dogs[“color”].isin([“Black”, “Brown”])

  Dogs[is_black_or_brown]

New columns:

- Adding a new column:

  Dataframe[“new_columns_name”]

Explicit indexes:

- Setting a column as the index:

  New_dataframe = dataframe.set_index(“column_name”)

* Removing an index:

  dataframe.reset_index()

  \*Passing parameter ‘drop=True’ eliminates the previous index’s column completely

- Filter for rows based on their index value:

  Dataframe.loc[“value”]

* Multi-level indexes:

  Dataframe_new = dataframe.set_index([“column1”, “column2”])

- Sort by index values:

  dataframe.sort_index()

Slicing:

- Slicing a list:

  list[*first_value* : *second_value*] returns values between those 2 values (inclusively)

  \*You can also slice with index values (python index starts with 0)

  list[ : *value*] returns all values before value given

  List[ : ] returns the whole list

* Slicing a dataframe by index values:

  Dataframe.loc[“first_value” : “second_value”]

- Slicing a dataframe by columns:

  Dataframe.loc[ : , “column_name1” : “column_name2”

Pivot tables:

- Pivot_table = dataframe.pivot_table(“column_name_to_aggregate”, index=”column_name_to_index”, columns=”column_name_for_columns”)
- Calculating summary statistics across rows:

  dataframe.mean(axis=”index”)

* Calculate summary statistics by across columns:

  dataframe.mean(axis=””columns)

Visualizing your data:

- Import pyplot for plots:

  import matplotlib.pyplot as plt

* Create a histogram for a column:

  dataframe[“column_name”].hist()

  plt.show()

  \*You can pass parameter ‘bins=number’ to set the number of bars for the histogram

- Bar plots:

  dataframe.plot(kind=”bar”)

  plt.show()

* Line plots:

  dataframe.plot(x=”x_avis_column”, y=”y_axis_column”, kind=”line”)

  plt.show()

  *You can rotate x axis labels by passing parameter ‘rot=*degrees_number\*’

- Scatter plots:

  dataframe.plot(x=”x_avis_column”, y=”y_axis_column”, kind=”scatter”)

  plt.show()

* Layering histograms:

  dataframe[“column_name”].hist(alpha=0.7)

dataframe[“column_name”].hist(alpha=0.7)

    plt.legend([“first_histogram_name”, “second_histogram_name”])


    plt.show()

Missing values:

- Detect missing values:

  dataframe.isna()

- Return True or False if there is any missing values in each column:

  dataframe.isna().any()

- Counting missing values:

  dataframe.isna().sum()

* Removing missing values:

  dataframe.dropna()

- Replacing missing values:

  dataframe.fillna(0)

Creating dataframes:

- Converting a list of dictionaries into a dataframe:

  New_dataframe = pd.DataFrame(list_of_dictionaries)

Reading and writing CSVs:

- Converting CSV to dataframe:

  Import pandas as pd


    New_dataframe = pd.read_csv(“csv_name.csv”)

- Converting from DataFrame to CSV:

  dataframe.to_csv(“new_csv_name”)

**<span style="text-decoration:underline;">Cleaning data in Python</span>**

Data type constraints:

- Get data types of columns:

  Dataframe.dtypes

* Get dataframe info:

  dataframe.info

* Remove a symbol or character from a column:

  dataframe[‘column_name’].str.strip(‘character’)

* Change column data type:

  dataframe[‘column_name’].astype(‘int’)

* Assert statement to run tests:

  Assert 1+1 == 2 will pass


    Assert 1+2 == 2 will fail

Data range constraints:

- Drop values using filtering:

  Movies = movies[movies[‘avg_rating] &lt;= 5]

- Drop values using .drop()

  movies.drop(movies[movies[‘avg_rating] > 5].index, inplace = True)

- Convert date object to datetime:

  User_signups[‘subscription_date’] = pd.to_datetime(User_signups[‘subscription_date’])

- Return today’s date:

  dt.date.today()

Uniqueness constraints:

- Find duplicates in a dataframe:

  Duplicates = dataframe.duplicated()


    *You can get the duplicated rows with ‘dataframe[duplicates]’

    *You can pass the ‘subset’ argument as a list of column names to check for duplication


    *You can pass the ‘keep’ argument as either ‘first’, ‘last’, or ‘false’ to keep the first, last or all duplicate values respectively

- Drop complete duplicates:

  dataframe.drop_duplicates(inplace=True)

Membership constraints:

- It is of best practice to have a separate dataframe with each possible category of a categorical column in a dataframe
- Finding inconsistent categories:

  Inconsistent_categories = set(study_data[‘blood_type’]).difference(categories[‘blood_type’])

- Get rows with inconsistent categories:

  Inconsistent_rows = study_data[‘blood_type’].isin(inconsistent_categories)

- Drop inconsistent rows:

  Consistent_data = study_data[*TILDE*inconsistent_rows]

Categorical variables:

- Value consistency with capitalization:

  Dataframe[‘column_name’] = dataframe[‘column_name’].str.upper()

  Dataframe[‘column_name’] = dataframe[‘column_name’].str.lower()

* Value consistency with leading or trailing spaces:

  Dataframe = dataframe[‘column_name’].str.strip()

* Collapsing data into categories:

  Mapping = {‘Microsoft’: ‘DesktopOS’, ‘MacOS’:’DesktopOS’, ‘IOS’:’MobileOS’}


    Devices[‘operating_system’] = devices[‘operating_system’].replace(mapping)

Cleaning text data:

- Replacing values in strings:

  phones[“Phone number”] = phones[“Phone number”].str.replace(“+”, “00”)


    *First value of .replace() is the value you want to replace, second value is what you’re replacing the first one with

- Using regular expressions (e.g. replacing anything that is not a number with nothing)

  phones[‘Phone number’] = phones[“Phone numbers”].str.replace(r’\D+’, ‘’)

Cross field validation:

- Using multiple fields in a dataset to sanity check data integrity:

  Sum_classes = flights[[’economy’, ‘business’, ‘first’]].sum(axis=1)


    Passenger_equ = sum_classes == flights[‘total_passengers’]


    Inconsistent_pass = flights[*TILDE*passenger_equ]


    consistent_pass = flights[passenger_equ]

- When inconsistencies are caught, one can either:

  Drop data | Set to missing and impute | Apply rules from domain knowledge

Completeness:

- Visualize and understand missing dat ausing Missingno:

  Import missingno as msno


    Import matplotlib.pyplot as plt


    msno.matrix(dataframe)


    plt.show()

Comparing strings:

- Compare strings with Fuzzywuzzy:

  From fuzzywuzzy import fuzz

  fuzz.WRatio(‘Reeding’, ‘Reading’)

  \*Returns a score from 0 to 100 with 0 being not similar at all and 100 being an exact match

Linking dataframes:

- Full_census = census_A.append(census_B_new)

**<span style="text-decoration:underline;">Intermediate data visualization with Seaborn:</span>**

Using the distribution plot:

- Distplot function has multiple optional arguments
- E.g. a simple histogram is `sis.distplot(df[‘*DataFrame name*’], kde=False, bins =_# of bins_)
- Alternative data distributions are also possible via optional arguments; following is a kde curve and a rug plot combined:

  `sns.distplot(df[‘*DataFrame name’], hist=False, rug=True)`

* You can further customize a plot with their underlying functions’ arguments, e.g:

  `sns.distplot(df[‘DataFrame name’], hist=False, rug=True, kda_kws={‘shade’:True})`

Regression Plots in Seaborn:

- ‘regplot’ function generates a scatter plot with regression line
- Variables ‘data’, ‘x’, and ‘y’ must be defined
- ‘sns.regplot(x=“alcohol”, y=“pH”)’
- lmplot is like regplot but much more powerful and allows for more options through ‘faceting’. E.g. :

  sns.lmplot(x=“quality”, y=“alcohol”, data=df, hue=“type”)

  sns.lmplot(x=“quality”, y=“alcohol”, data=df, col=“type”)

Using Seaborn Styles:

- Setting styles:

  ‘sns.set()’

  ‘sns.set()

  df[‘Tuition’].plot.hist()’

* Theme examples include ‘white’, ‘dark’, ‘whitegrid’, ‘darkgrid’, ‘ticks’

  Style is then set with ‘sns.set_style(style)’

- Removing axes with ‘despine()’

  Eg: ‘sns.despine(left=True)’

Colors in Seaborn:

- Defining a color for a plot:

  ‘sns.set(color_codes=True)’

  ‘sns.distplot(df[‘Tuition’], color=‘g’)’

* Palettes:

  ‘for p in sns.palettes.SEABORN_PALETTES:

      sns.set_palette(p)

      sns.distplot(df[‘Tuition’])’

- Displaying palettes:

  ‘sns.palplot()’ - displays a palette

  ‘sns.color_palette()’ - returns the current palette

Customizing with matplotlib:

- Matplotlib axes:

  Axes can be passed to seaborn functions for more customisation:

  ‘

  fig, ax = plt.subplots()

  sns.distplot(df[‘Tuition], ax=ax)

  ax.set(xlabel=“Tuition 2013-14”)

  ’

Categorical Plot Types:

- Regression Plots:

  ‘sns.regplot(data=df, x=‘temp’, y=‘total_rentals’, marker=‘+’)’

* A Residual Plot is useful for evaluating the fit of a model:

  ‘sns.residplot(data=df, x=‘temp’, y=‘total_rentals’)’

- Polynomial regression uses the ‘order’ parameter

Matrix Plots:

- Seaborn’s ‘heatmap()’ function requires data to be in a grid format. This can be done with pandas’ ‘crosstab()’ function:

  ‘

  pd.crosstab(dt[“mnth”], df[“weekday”], values=df[“total_rentals”], aggfunc=‘mean’).round(0)

  ’

  ‘

  sns.heatmap(pd.crosstab(dt[“mnth”], df[“weekday”], values=df[“total_rentals”], aggfunc=‘mean’))

  ’

* Customise a heatmap with arguments such as:

  annot=True

  fmt=“d”

  cmap=“YlGnBu”

  cbar=False

  linewidths=.5

Using FacetGrid, factorplot and lmplot:

- Tidy Data: Seaborn’s grid plots require data in “tidy format”, which means one observation per row of data
- The ‘factorplot()’ function is a simpler way to use a FacetGrid for categorical data. It co,mnimes the faceting and mapping process into 1 function:

  ‘

  sns.factorplot(x=“Tuition”, data=df, col=“HIGHDEG”, kind=‘box’)

  ’

Using PairGrid and pairplot:

- PairGrid shows pairwise relationships between data elements:

  g = sns.PairGrid(df, vars=[“Fair_Markt_Rent”, “Median_Income”])

  g = g.map(pot.scatter)

* pairplot is a shortcut for the PairGrid:
  - Sns.pairplot(df, vars=[“Fair_Markt_rent”, “Median_Income”], kind=‘reg’, diag_kind=‘hist’)

Using JointGrid and jointplot:

- Basic JointGrid:

  g = sns.JointGrid(data=df, x=“Tuition”, y=“ADM_RATE_ALL”)

  g.plot(sns.regplot, sns.distplot)

* jointplot is easier to use but contains fewer capabilities:

  sns.jointplot(data=df, x=“Tuition”, y=“ADM_RATE_ALL”, kind=‘hex’)

Selecting Seaborn Plots:

- Univariate Distribution Analysis:

  distplot() is the best starting point

  rugplot() and kdeplot() can be useful alternatives

* Regression Analysis:

  lmplot() performs regression analysis and supports facetting

- Categorical Plots:

  e.g. boxplot() and violinplot() followed by point, bar, or countplot()

  IF you need to facet the data, use a factorplot()

* pairplot() and jointplot():

  Perform regression analysis with lmplot AND analyze distributions with distplot
