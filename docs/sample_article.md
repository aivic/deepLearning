## Introduction
A PivotTable constructed in Excel becomes a powerful tool to calculate, summarize, and analyze data that lets you see comparisons, patterns, and trends in your data. For example, you have a huge amount of transaction data for a shop and you are asked to make a report along with a dashboard to show the transactions done every year for last twenty years. It would take days to complete the task when done manually, but with the help of PivotTable and pivot charts, it would hardly take few minutes as it is able to powerfully analyze large volumes of data in a few clicks and also reduces the chances of errors to the minimum.

In this guide we will cover the following features associated to Pivot tables:

- sdf
- wer

## Creating a Pivot Table
Before we start learning about the creation of pivot tables, it is important to know the data format on which they are built. A pivot table requires tablular data and it treats blank spaces separately. A complete blank row is treated as a `blank()` value, however, if there is at least one data field available in a row, then the rest of the row data field is considered blank and the row is treated just like other rows.

To understand how blank spaces are treated in a pivot table, consider below three cases:

### Case 1: No Blank Values
Consider the following table where 24 data rows are available along with four columns.

| Month | Quarter |        Shop        | Profit in USD |
|-------|---------|--------------------|---------------|
| Jan   |       1 | Nikodale Furniture |          2500 |
| Feb   |       1 | Nikodale Furniture |          3888 |
| Mar   |       1 | Nikodale Furniture |          5699 |
| Apr   |       2 | Nikodale Furniture |          8875 |
| May   |       2 | Nikodale Furniture |          6588 |
| Jun   |       2 | Nikodale Furniture |          2233 |
| Jul   |       3 | Nikodale Furniture |          6630 |
| Aug   |       3 | Nikodale Furniture |          1855 |
| Sep   |       3 | Nikodale Furniture |          3555 |
| Oct   |       4 | Nikodale Furniture |          8795 |
| Nov   |       4 | Nikodale Furniture |          1211 |
| Dec   |       4 | Nikodale Furniture |          2222 |
| Jan   |       1 | Samuel Arts        |          6554 |
| Feb   |       1 | Samuel Arts        |          6899 |
| Mar   |       1 | Samuel Arts        |          7845 |
| Apr   |       2 | Samuel Arts        |          9555 |
| May   |       2 | Samuel Arts        |          7588 |
| Jun   |       2 | Samuel Arts        |          6558 |
| Jul   |       3 | Samuel Arts        |          5224 |
| Aug   |       3 | Samuel Arts        |          6554 |
| Sep   |       3 | Samuel Arts        |          7558 |
| Oct   |       4 | Samuel Arts        |          4555 |
| Nov   |       4 | Samuel Arts        |          3555 |
| Dec   |       4 | Samuel Arts        |          1555 |

To create a pivot table on this data, first arrange the data in the form of a table using the following hierarchy:

>> Menu bar > Home > Format as Table > Select a table format you like

![Imgur](https://i.imgur.com/PQ08q4c.png)

Once you get the data in a tablular form, now you can follow the given hierarchy to create a pivot table in a new worksheet:

>> Menu bar > Insert > PivotTable > Press OK

![Imgur](https://i.imgur.com/1xakDeD.png)

This opens a new blank worksheet, however, you can observe `PivotTable Fields` on the right side of the sheet. This box by default has two areas, first, you have `Field Section` and second stacked `Areas Section`. The `Field Section` consists of all the column names and the `Areas Section` has four sub-sections, Filters, Columns, Rows and Values. You drag a column name from the `Field Section` and drop  it to any of the `Areas Section`.

If you proceed with the following structure:

![Imgur](https://i.imgur.com/DnNwiIF.png)

You receive the following PivotTable:

| <p> Sum of Profit in USD Column Labels <br> Row Labels  </p>         | Nikodale Furniture | Samuel Arts | Grand Total |
|----------------------|--------------------|-------------|-------------|
| 1                    | 12087              | 21298       | 33385       |
| 2                    | 17696              | 23701       | 41397       |
| 3                    | 12040              | 19336       | 31376       |
| 4                    | 12228              | 9665        | 21893       |
| Grand Total          | 54051              | 74000       | 128051      |

As you can observe, there were no missing values in the original table, hence there is no blank values in the PivotTable.

### Case 2: Missing Row
Consider this time that the following row is missing from the table (replaced by blank values):

| Month | Quarter |        Shop        | Profit in USD |
|-------|---------|--------------------|---------------|
| Sep   |       3 | Nikodale Furniture |          3555 |

Now, if we try to build a PivotTable on the top of such table, we get the following result:

| <p> Sum of Profit in USD Column Labels <br> Row Labels </p>          | Nikodale Furniture | Samuel Arts | **(blank)** | Grand Total |
|----------------------|--------------------|-------------|---------|-------------|
| 1                    | 12087              | 21298       |         | 33385       |
| 2                    | 17696              | 23701       |         | 41397       |
| 3                    | 8485               | 19336       |         | 27821       |
| 4                    | 12228              | 9665        |         | 21893       |
| **(blank)**              |                    |             |         |             |
| Grand Total          | 50496              | 74000       |         | 124496      |

Here, `blank()` is considered both as a separate row and column. 

### Case 3: Missing value
What if only few values are missing rather than a complete record? To understand the PivotTable result in such case, let's remove the profit in the month of September from Nikodale Furniture:

| Month | Quarter |        Shop        | Profit in USD |
|-------|---------|--------------------|---------------|
| Sep   |       3 | Nikodale Furniture |           |

Building PivotTable on this data results in the following:

| <p> Sum of Profit in USD Column Labels <br> Row Labels  </p>         | Nikodale Furniture | Samuel Arts | Grand Total |
|----------------------|--------------------|-------------|-------------|
| 1                    | 12087              | 21298       | 33385       |
| 2                    | 17696              | 23701       | 41397       |
| 3                    | **8485**              | 19336       | 31376       |
| 4                    | 12228              | 9665        | 21893       |
| Grand Total          | 54051              | 74000       | 128051      |

This results in a similar table as case 1 with a difference in the value of Quarter 3 profit for Nikoldale Furniture.

These three cases signifies how missing row(s) or missing value(s) in the data can impact the corresponding PivotTable. 
