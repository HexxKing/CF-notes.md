# [Pandas in 10](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)
### Object Creation 
- A Series is a one-dimensional array of indexed data and can be creted by passing a list of values 
- the DataFrame can be thought of either as a generalization of a NumPy array, or as a specialization of a Python dictionary.
  - There can be multiple rows and columns in the data.
  - Each row represents a sample of data,
  - Each column contains a different variable that describes the samples (rows).
  - The data in every column is usually the same type of data – e.g. numbers, strings, dates.
  - Usually, unlike an excel data set, DataFrames avoid having missing values, and there are no gaps and empty values between rows or columns.
  - If a Series is an analog of a one-dimensional array with flexible indices, a DataFrame is an analog of a two-dimensional array with both flexible row indices and flexible column names. Just as you might think of a two-dimensional array as an ordered sequence of aligned one-dimensional columns, you can think of a DataFrame as a sequence of aligned Series objects. Here, by "aligned" we mean that they share the same index.
  - Like the Series object, the DataFrame has an index attribute that gives access to the index labels
  - Additionally, the DataFrame has a columns attribute, which is an Index object holding the column labels
  - Thus the DataFrame can be thought of as a generalization of a two-dimensional NumPy array, where both the rows and columns have a generalized index for accessing the data
  - A DataFrame is a collection of Series objects, and a single-column DataFrame can be constructed from a single Series
  - Any list of dictionaries can be made into a DataFrame.
  - Even if some keys in the dictionary are missing, Pandas will fill them in with NaN values
  - Given a two-dimensional array of data, we can create a DataFrame with any specified column and index names. If omitted, an integer index will be used for each

### [Loading CSV data into Pandas](https://www.shanelynn.ie/using-pandas-dataframe-creating-editing-viewing-data-in-python/)
- Creating DataFrames from CSV (comma-separated value) files is made extremely simple with the read_csv() function in Pandas, once you know the path to your file. A CSV file is a text file containing data in table form, where columns are separated using the ‘,’ comma character, and rows are on separate lines (see here).
- If your data is in some other form, such as an SQL database, or an Excel (XLS / XLSX) file, you can look at the other functions to read from these sources into DataFrames, namely read_xlsx, read_sql. However, for simplicity, sometimes extracting data directly to CSV and using that is preferable.

### Viewing Data
- `.head`, `.tail`, `.index`, and `.columns` will display the top, bottom, index and columns of the frame.
- NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column
- DataFrame.to_numpy() gives a NumPy representation of the underlying data. Note that this can be an expensive operation when your DataFrame has columns with different data types, which comes down to a fundamental difference between pandas and NumPy: NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column. When you call DataFrame.to_numpy(), pandas will find the NumPy dtype that can hold all of the dtypes in the DataFrame. This may end up being object, which requires casting every value to a Python object.
  - DataFrame.to_numpy() does not include the index or column labels in the output.
-  `.describe()` shows a quick statistic summary of your data:
- `.T` transposes your data
- `.sort_index(axis=n, ascending=T/F)` is sorting by an axis
- `.sort_values(by='value')` sorts by a value 

### Selections
- While standard Python / Numpy expressions for selecting and setting are intuitive and come in handy for interactive work, for production code, we recommend the optimized pandas data access methods, `.at`, `.iat`, `.loc` and `.iloc`.
- `df['X']` selects a single column, returns a series 
- `df[N:N]` selecting by slicing the rows 



## [Pandas - Getting Started](https://pandas.pydata.org/pandas-docs/stable/getting_started/intro_tutorials/index.html)
- The community agreed alias for pandas is `pd`, so loading pandas as `pd` is assumed standard practice for all of the pandas documentation.
  - `import pandas as pd`






# Other Resources
## [Real Python - Pandas Tutorials](https://realpython.com/learning-paths/pandas-data-science/)
## [What is Pandas - Video](https://www.youtube.com/watch?v=dcqPhpY7tWk&t=391s)
## [Master Pandas](https://towardsdatascience.com/be-a-more-efficient-data-scientist-today-master-pandas-with-this-guide-ea362d27386)




