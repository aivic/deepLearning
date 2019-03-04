Consider a CSV file named `pandas_read.csv` having 11 columns and nearly 1000 rows along with a footer. The table below shows a glimpse of data from the CSV file.

To initiate the process, first import the pandas library and assign an alias name to it. The commonly referred alias to pandas library is pd.

`import pandas as pd`

Next, let us take a glimpse of the CSV file if we read it without specifying any explicit arguments. We are appending our reading operation with `.head(4)` method to retrieve first 4 rows.

`pd.read_csv('pandas_read.csv').head(4)`

|   | **ID1** | **Id2** | **Id2.1** | **ID3** | **Age** | **kg** | **kg.1** | **cm** | **DOB** | **Study** | **Grade** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? |
| 1 | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? |
| 2 | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? |
| 3 | 2748 | 1847 | 1847 | 2898 | 48 | 80 | 80 | 151 | 11/13/1990 | Ph.D. | A- |

Notice the problems which occur when we read the file directly –

1. There are two columns `Id2.1` and `kg.1` which are duplicates of `Id2` and `kg` columns. Hence, these two columns need to be dropped and only unique columns need to be read.
2. First three rows consist of garbage data and hence need to be removed.
3. As mentioned earlier, the last three rows hold a footer and hence need to be removed.
4. The Date of Birth `DOB` column needs to be parsed to the datetime datatype.

Let us begin by dropping the duplicate columns. The duplicate columns (`Id2.1` and `kg.1`) are placed on index 2 and 6 respectively. So, we need to utilize `usecols` argument and specify the column indexes which we need to retain.

`pd.read_csv('pandas_read.csv', usecols=[0, 1, 3, 4, 5, 7, 8, 9, 10]).head(4)`

|   | **ID1** | **Id2** | **ID3** | **Age** | **kg** | **cm** | **DOB** | **Study** | **Grade** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | ? | ? | ? | ? | ? | ? | ? | ? | ? |
| 1 | ? | ? | ? | ? | ? | ? | ? | ? | ? |
| 2 | ? | ? | ? | ? | ? | ? | ? | ? | ? |
| 3 | 2748 | 1847 | 2898 | 48 | 80 | 151 | 11/13/1990 | Ph.D. | A- |



Next, let us remove the first three garbage rows. This can be achieved by mentioning the row numbers in the `skiprows` argument. Do remember that index in `skiprows` starts with 1 not 0. So, here we will be skipping 1, 2, and 3 rows.

`pd.read_csv('pandas_read.csv', usecols=[0, 1, 3, 4, 5, 7, 8, 9, 10], skiprows=[1, 2, 3]).head(4)`

|   | **ID1** | **Id2** | **ID3** | **Age** | **kg** | **cm** | **DOB** | **Study** | **Grade** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 2748 | 1847 | 2898 | 48 | 80 | 151 | 11/13/1990 | Ph.D. | A- |
| 1 | 1171 | 2077 | 4124 | 51 | 57 | 165 | 8/4/1988 | Doctorate | F- |
| 2 | 1732 | 3784 | 1402 | 50 | 101 | 194 | 11/11/1989 | Doctorate | D- |
| 3 | 4394 | 4799 | 1141 | 45 | 90 | 171 | 12/26/1995 | Ph.D. | A+ |

We can observe that first three garbage rows with `?` have been removed without changing the row numbers.

Moving ahead, let us take a look on how the file looks at the bottom. We have used the `.tail(4)` method after reading the file to get the last 4 rows of the dataframe.

`pd.read_csv('pandas_read.csv', usecols=[0, 1, 3, 4, 5, 7, 8, 9, 10], skiprows=[1, 2, 3]).tail(4)`

|   | **ID1** | **Id2** | **ID3** | **Age** | **kg** | **cm** | **DOB** | **Study** | **Grade** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 996 | 4719 | 646 | 4414 | 43 | 103 | 150 | 12/3/1985 | Master | F+ |
| 997 | The data in the CSV file lists three IDs of 10... | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN |
| 998 | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN |
| 999 | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN |

As you may observe, only cell `ID1 997` holds the footer and rest of the cells in rows 997, 998 and 999 are empty which are represented as `NaN` (Not A Number) by Pandas automatically. So, let us drop the last 3 rows to remove the footer while reading the file. This can be achieved by using `skipfooter` argument and mentioning the number of rows to be skipped. Since the footer in our case comprises of 3 rows, hence we will assign 3 to `skipfooter` argument. Furthermore, the fastest engine used by Pandas library is `c`, whereas `skipfooter` is only compatible with `python` engine, therefore we also have to mention `python` engine explicitly.

`pd.read_csv('pandas_read.csv', usecols=[0, 1, 3, 4, 5, 7, 8, 9, 10], skiprows=[1, 2, 3], skipfooter=3, engine='python').tail(4)`

|   | **ID1** | **Id2** | **ID3** | **Age** | **kg** | **cm** | **DOB** | **Study** | **Grade** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 993 | 261 | 3653 | 3633 | 30 | 58 | 176 | 11/9/1995 | Bachelor | A+ |
| 994 | 4839 | 2027 | 3023 | 41 | 85 | 191 | 2/5/1991 | Doctorate | A+ |
| 995 | 3233 | 1947 | 4584 | 41 | 50 | 151 | 9/23/1996 | Doctorate | B+ |
| 996 | 4719 | 646 | 4414 | 43 | 103 | 150 | 12/3/1985 | Master | F+ |

As we can observe, rows 997-999 have been removed leaving the last row as 996.

Next, let us find the datatype for DOB column using Pandas `dtypes` attribute.

`pd.read_csv('pandas_read.csv', usecols=[0, 1, 3, 4, 5, 7, 8, 9, 10], skiprows=[1, 2, 3], skipfooter=3, engine='python').DOB.dtypes`

This results to `dtype('O')` which means `DOB` column has an object datatype in spite of a datetime datatype. To convert this column to a datetime column, we need to mention a datetime parser along with the format of date. The `DOB` column has a date format given as `MM/DD/YYYY`, therefore we need to parse each row data. This can be accomplished by mentioning the column inside `parse_dates` argument followed by date parser function. The function can be implemented using `lambda` and pandas `datetime.strptime` methods.

`dateparse = lambda x: pd.datetime.strptime(x, '%m/%d/%Y')`

`pd.read_csv('pandas_read.csv', usecols=[0, 1, 3, 4, 5, 7, 8, 9, 10], skiprows=[1, 2, 3], skipfooter=3, engine='python', parse_dates=['DOB'], date_parser=dateparse).DOB.dtypes`

This results into `dtype('<M8[ns]')` which is a Pandas datetime format.

By following these steps, we have overcome the before-mentioned problems and now we can write back these changes to a new CSV file named `pandas_write.csv`.

However, before we write the changes to a new file, let us transform all the column names to uppercase and change two column names (`kg` and `cm`) to (`WEIGHT` and `HEIGHT`). There are many ways to perform these changes, but we can also do it during writing phase by assigning new column names to `header` argument in the form of a list. Also, make sure to make `index` argument as `False` so that row numbers do not arrive as a new column.

`dateparse = lambda x: pd.datetime.strptime(x, '%m/%d/%Y')`

`# Using a variable named file to store the changes in CSV file and write it to the pandas_write.csv file`

`file = pd.read_csv('pandas_read.csv', usecols=[0, 1, 3, 4, 5, 7, 8, 9, 10], skiprows=[1, 2, 3], skipfooter=3, engine='python', parse_dates=['DOB'], date_parser=dateparse)`

`file.to_csv('pandas_write.csv', header=['ID1', 'ID2', 'ID3', 'AGE', 'WEIGHT', 'HEIGHT', 'DOB', 'STUDY', 'GRADE'], index=False)`
