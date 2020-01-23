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

This opens a new blank worksheet, however, you can observe `PivotTable Fields` on the right side of the sheet. This box by default has two areas, first, you have `Field Section` and second, stacked `Areas Section`. The `Field Section` consists of all the column names and the `Areas Section` has four sub-sections, Filters, Columns, Rows and Values. You drag a column name from the `Field Section` and drop  it to any of the `Areas Section`.

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

### Creating a Recommended Table
When you click on the `Insert` tab in the Menu bar, you can observe `Recommended PivotTable` option adjacent to `PivotTable` option. Clicking on this option pops up a new dialog box which consists of most of the common PivotTables which can be built using the provided data. For instance, considering there is no missing value in the data, the recommended PivotTables are shown below:

![Imgur](https://i.imgur.com/EQzdtpA.png)

## Managing Data in PivotTables
So far, we have learn to create a PivotTable, now let us learn managing its items using the given table:

| Year | Quarter | Nikodale Furniture | Samuel Arts |
|------|---------|--------------------|-------------|
| 2019 |       1 |               4548 |        2500 |
| 2019 |       2 |               7548 |        3888 |
| 2019 |       3 |               2154 |        5699 |
| 2019 |       4 |               8875 |        8875 |
| 2018 |       1 |               6588 |        4578 |
| 2018 |       2 |               2233 |        4221 |
| 2018 |       3 |               6630 |        6584 |
| 2018 |       4 |               1855 |        1452 |

First, we built a PivotTable out of this table keeping the following Pivot structure:

- **Rows**: Year followed by Quarter
- **Values**: Sum of Nikodale Furniture followed by Sum of Samuel Arts

This leaves us to the given result:

| Row Labels  | Sum of Nikodale Furniture | Sum of Samuel Arts |
|-------------|---------------------------|--------------------|
| **2018**        |                           |                    |
| 1           |                      6588 |               4578 |
| 2           |                      2233 |               4221 |
| 3           |                      6630 |               6584 |
| 4           |                      1855 |               1452 |
| **2019**        |                           |                    |
| 1           |                      4548 |               2500 |
| 2           |                      7548 |               3888 |
| 3           |                      2154 |               5699 |
| 4           |                      8875 |               8875 |
| Grand Total |                     40431 |              37797 |

### SubTotal of Group
As you can observe, the PivotTable has two sub-sections (2018 and 2019) with a final Grand Total. To get the total of each section separately, we can follow the given steps: 

>> Menu bar > Design > Subtotal > Choose any option (here, Show all Subtotals at the Bottom of Group)

| Row Labels  | Sum of Nikodale Furniture | Sum of Samuel Arts |
|-------------|---------------------------|--------------------|
| **2018**        |                           |                    |
| 1           |                      6588 |               4578 |
| 2           |                      2233 |               4221 |
| 3           |                      6630 |               6584 |
| 4           |                      1855 |               1452 |
| **2018 Total**  |                     17306 |              16835 |
| **2019**        |                           |                    |
| 1           |                      4548 |               2500 |
| 2           |                      7548 |               3888 |
| 3           |                      2154 |               5699 |
| 4           |                      8875 |               8875 |
| **2019 Total**  |                     23125 |              20962 |
| Grand Total |                     40431 |              37797 |

You can also control the display of Grand Total from the same menu.

### Controlling Field Settings
You may have observed that when we drop a field in the `Values` section, if automatically calls the Sum function. However, we can control what function needs to be implemented on a particular value. Let us try to change the following:
- Nikodale Furniture: From Sum to Maximum value
- Samuel Arts: From Sum to Average value

To accomplish this change, click on `Sum of Nikodale Furniture` under the `Values` section and select `Value Field Settings...` option.

![Imgur](https://i.imgur.com/gXtdbh0.png)

Now, click on `Max` and press OK.

![Imgur](https://i.imgur.com/pHVSWjw.png)

Perform similar operation with Samuel Arts but this time select `Average`. Once you've done both the operations, you will receive the following PivotTable:

| Row Labels  | Max of Nikodale Furniture | Average of Samuel Arts |
|-------------|---------------------------|------------------------|
| **2018**        |                           |                        |
| 1           |                      6588 |                   4578 |
| 2           |                      2233 |                   4221 |
| 3           |                      6630 |                   6584 |
| 4           |                      1855 |                   1452 |
| **2018 Total**  |                      6630 |                4208.75 |
| **2019**        |                           |                        |
| 1           |                      4548 |                   2500 |
| 2           |                      7548 |                   3888 |
| 3           |                      2154 |                   5699 |
| 4           |                      8875 |                   8875 |
| **2019 Total**  |                      8875 |                 5240.5 |
| Grand Total |                      8875 |               4724.625 |

### Filtering
Just like we can apply filter on a usual table in Excel, we can also apply similar filter on a PivotTable. For instance, consider the table above, if you click on any year's quarter cell (1, 2, 3, or 4) and then click on the drop down button next to **Row Labels** column, you'll find an option to select all or specific quarters. Similarly, if you click on a cell with year value (2018 or 2019), the drop down values changes from quarter to year. The images given below represent the drop down box in each case:

![Imgur](https://i.imgur.com/rwDwaGo.png)

![Imgur](https://i.imgur.com/27Gzfwn.png)

Instead of clicking on a cell to select a field (Quarter or Year), you can also choose them right from the `Select Field` option available in the drop down box.

The PivotTable given below shows the data only for quarters 1 and 2 in 2018:

| Row Labels  | Max of Nikodale Furniture | Average of Samuel Arts |
|-------------|---------------------------|------------------------|
| 2018        |                           |                        |
| 1           |                      6588 |                   4578 |
| 2           |                      2233 |                   4221 |
| 2018 Total  |                      6588 |                 4399.5 |
| Grand Total |                      6588 |                 4399.5 |
