## Introduction
A PivotTable constructed in Excel becomes a powerful tool to calculate, summarize, and analyze data that lets you see comparisons, patterns, and trends in your data. For example, you have a huge amount of transaction data for a shop and you are asked to make a report along with a dashboard to show the transactions done every year for last twenty years. It would take days to complete the task when done manually, but with the help of PivotTable and pivot charts, it would hardly take few minutes as it is able to powerfully analyze large volumes of data in a few clicks and also reduces the chances of errors to the minimum.

In this guide we will cover the following features associated to Pivot tables:

- Creating a PivotTable
- Managing Data in PivotTable 
- Formulas on PivotTables
- Exploring Data with PivotChart

## Creating a PivotTable
Before we start learning about the creation of PivotTables, it is important to know the data format on which they are built. A PivotTable requires tablular data and it treats blank spaces separately. A complete blank row is treated as a `blank()` value, however, if there is at least one data field available in a row, then the rest of the row data field is considered blank and the row is treated just like other rows.

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

To create a PivotTable on this data, first arrange the data in the form of a table using the following hierarchy:

>> Menu bar > Home > Format as Table > Select a table format you like

![Imgur](https://i.imgur.com/PQ08q4c.png)

Once you get the data in a tablular form, now you can follow the given hierarchy to create a PivotTable in a new worksheet:

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

### Layout Transformation
In the above PivotTables, you may have observed that there is no separate boundary to distinguish a group from another (here, 2018 data from 2019 data). Plus, the year and quarter appears in a single column. PivotTables provide an option under the Design tab named as `Report Layout` and `Blank Rows` to tackle these issues. Let us learn them step by step:

#### Adding and Removing Blank Rows in a PivotTable
Consider a PivotTable with two groups as shown below:

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

You can notice that we can improve the visual of this table by adding a blank row below 2019 year row. To achieve this, follow the given steps:

>> Menu bar > Design > Blank Rows > Insert Blank Line After Each Item

This above operation results in the following PivotTable:

| Row Labels  | Sum of Nikodale Furniture | Sum of Samuel Arts |
|-------------|---------------------------|--------------------|
| **2018**        |                           |                    |
| 1           |                      6588 |               4578 |
| 2           |                      2233 |               4221 |
| 3           |                      6630 |               6584 |
| 4           |                      1855 |               1452 |
|  |  |  |
| **2019**        |                           |                    |
| 1           |                      4548 |               2500 |
| 2           |                      7548 |               3888 |
| 3           |                      2154 |               5699 |
| 4           |                      8875 |               8875 |
| Grand Total |                     40431 |              37797 |

To remove the blank row, follow the given steps:

>> Menu bar > Design > Blank Rows > Remove Blank Line After Each Item

#### Changing Table Layout
The `Report Layout` option under the Design tab has the following options:

![Imgur](https://i.imgur.com/7VegCEJ.png)

By default, the PivotTable comes with the first option `Show in Compact Form`. Let us use another format `Show in Outline Form` to separate Year from Quarter which results in the following PivotTable:

|    Year     | Quarter | Sum of Nikodale Furniture | Sum of Samuel Arts |
|-------------|---------|---------------------------|--------------------|
| 2018        |         |                     17306 |              16835 |
|             |       1 |                      6588 |               4578 |
|             |       2 |                      2233 |               4221 |
|             |       3 |                      6630 |               6584 |
|             |       4 |                      1855 |               1452 |
| 2019        |         |                     23125 |              20962 |
|             |       1 |                      4548 |               2500 |
|             |       2 |                      7548 |               3888 |
|             |       3 |                      2154 |               5699 |
|             |       4 |                      8875 |               8875 |
| Grand Total |         |                     40431 |              37797 |

Now, you can test rest of the options and observe the difference in the table.

## Formulas on PivotTables
In this section, we will learn about two formulas:
- GETPIVOTDATA
- Calculated Field

### GETPIVOTDATA
Sometimes you start with a PivotTable structure but a while ago the structure may change depending upon the requirements. Therefore, a function named `GETPIVOTDATA` is suggested to use in such scenario where you want to keep the information regardless of changes in the PivotTable structure.

For instance, consider the following PivotTable:

| Row Labels  | Max of Nikodale Furniture | Average of Samuel Arts |
|-------------|---------------------------|------------------------|
| 2018        |                           |                        |
| 1           |                      6588 |                   4578 |
| 3           |                      6630 |                   6584 |
| 2018 Total  |                      6588 |                 5581 |
| Grand Total |                      6588 |                 5581 |

Here, if you want to keep the maximum profit value ($6630) of Nikodale Furniture in Quarter 3 of year 2018 in a separate cell regardless of change in PivotTable structure then proceed with the following steps:
- Click on a new cell and write `=`.
- Next, click on cell with value 6630. This will result in the following formula in the new cell which you have selected `=GETPIVOTDATA("Max of Nikodale Furniture",$A$3,"Year",2018,"Quarter",3)`.
- Press Enter which leaves you with value 6630 in the cell with formula.

So far, we are able to retrieve the value using the formula, now let's change the structure of the table by adding Quarter 2 in the table which changes the location of cell with value 6630.

| Row Labels  | Max of Nikodale Furniture | Average of Samuel Arts |
|-------------|---------------------------|------------------------|
| 2018        |                           |                        |
| 1           |                      6588 |                   4578 |
| 2           |                      2233 |                   4221 |
| 3           |                      6630 |                   6584 |
| 2018 Total  |                      6588 |                 5127.67 |
| Grand Total |                      6588 |                 5127.67 |

As you can notice the value has remain unchanged!

### Calculated Field
Just as we can add a new column to an Excel table by connecting them with a formula, in a similar fashion we can add a new field in the PivotTable. Consider a PivotTable given below:

| Row Labels  | Max of Nikodale Furniture | Max of Samuel Arts |
|-------------|---------------------------|--------------------|
| 2018        |                           |                    |
| 1           |                      6588 |               4578 |
| 2           |                      2233 |               4221 |
| 3           |                      6630 |               6584 |
| 4           |                      1855 |               1452 |
| 2018 Total  |                      6630 |               6584 |
| 2019        |                           |                    |
| 1           |                      4548 |               2500 |
| 2           |                      7548 |               3888 |
| 3           |                      2154 |               5699 |
| 4           |                      8875 |               8875 |
| 2019 Total  |                      8875 |               8875 |
| Grand Total |                      8875 |               8875 |

So if we need to add a new column which represents the difference between columns `Max of Nikodale Furniture` and `Max of Samuel Arts` then use the following steps:
- Menu bar > Analyze > Fields, Items & Sets > Calculated Fields...
- In the Insert Calculated Field dialog box, provide a new column name and suitable formula as shown in the image below:

![Imgur](https://i.imgur.com/j0RPEBm.png)

This results in the following PivotTable:

| Row Labels  | Max of Nikodale Furniture | Max of Samuel Arts | Sum of NikToSam |
|-------------|---------------------------|--------------------|-----------------|
| 2018        |                           |                    |                 |
| 1           |                      6588 |               4578 |            2010 |
| 2           |                      2233 |               4221 |           -1988 |
| 3           |                      6630 |               6584 |              46 |
| 4           |                      1855 |               1452 |             403 |
| 2018 Total  |                      6630 |               6584 |             471 |
| 2019        |                           |                    |                 |
| 1           |                      4548 |               2500 |            2048 |
| 2           |                      7548 |               3888 |            3660 |
| 3           |                      2154 |               5699 |           -3545 |
| 4           |                      8875 |               8875 |               0 |
| 2019 Total  |                      8875 |               8875 |            2163 |
| Grand Total |                      8875 |               8875 |            2634 |

## Exploring Data with PivotChart
We can also visualize the data available in a PivotTable using PivotChart provided under the `Insert` menu. We build a stacked line chart with markers on the following PivotTable:

| Row Labels  | Max of Nikodale Furniture | Max of Samuel Arts |
|-------------|---------------------------|--------------------|
| 2018        |                           |                    |
| 1           |                      6588 |               4578 |
| 2           |                      2233 |               4221 |
| 3           |                      6630 |               6584 |
| 4           |                      1855 |               1452 |
| 2018 Total  |                      6630 |               6584 |
| 2019        |                           |                    |
| 1           |                      4548 |               2500 |
| 2           |                      7548 |               3888 |
| 3           |                      2154 |               5699 |
| 4           |                      8875 |               8875 |
| 2019 Total  |                      8875 |               8875 |
| Grand Total |                      8875 |               8875 |

![Imgur](https://i.imgur.com/0XqDjMV.png)

From the above chart, it is easy to infer that the profit of Samuel Arts is always higher than profit earned by Nikodale Furniture in all the quarters of 2018 and 2019.

## Conclusion
In this guide, you have learned about the basics of creating a PivotTable, managing the items within it, working with functions and charts. 

To get in-depth working knowledge on this subject, you can take [Exploring Data with PivotTables](https://www.pluralsight.com/courses/exploring-data-pivottables) course on PluralSight. 
