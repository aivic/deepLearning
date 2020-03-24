## Introduction
In today's world, numbers are present in every domain be it accounting, education, agriculture, etc. People working in domains which are related to computers are known to have been using sophisticated tools. However, for non-technical users, if they need to perform basic calculations or maintain records, Excel comes very handy.

In this guide, we will learn to search and manipulate the data in Excel. We cover topics such as:
- Changing the Text Case in Excel
- Sorting and Filtering Data in Excel
- Combining Data Using the Concatenate Function
- Filling and Pasting Data into Cells
- Filling Cells in Excel Using AutoFill
- Paste Options in Excel

## Changing the Text Case in Excel
You may get text in your spreadsheet in any format. To change the text case in Excel, let us first consider these records:

|                                                          Statements                                                           |
|-------------------------------------------------------------------------------------------------------------------------------|
| Microsoft Excel is a spreadsheet developed by Microsoft for Windows, macOS, Android and iOS.                                  |
| It features calculation, graphing tools, pivot tables, and a macro programming language called Visual Basic for Applications. |
| Microsoft Excel has the basic features of all spreadsheets.                                                                   |
| Excel forms part of the Microsoft Office suite of software.                                                                   |

As you can observe in the above table, all the statements begin with a capital letter (exception being Keywords like Windows, Android, etc.) and the rest of the words are in small case. Let us learn to perform changes to the text.

We start with the `**PROPER**` function which converts first letter of all the words into the upper case as shown:

`=PROPER(select_cells)`

**OUTPUT**

|                                                          Statements                                                           |
|-------------------------------------------------------------------------------------------------------------------------------|
| Microsoft Excel Is A Spreadsheet Developed By Microsoft For Windows, Macos, Android And Ios.                                  |
| It Features Calculation, Graphing Tools, Pivot Tables, And A Macro Programming Language Called Visual Basic For Applications. |
| Microsoft Excel Has The Basic Features Of All Spreadsheets.                                                                   |
| Excel Forms Part Of The Microsoft Office Suite Of Software.                                                                   |

Next, we have two other functions `**LOWER**` and `**UPPER**` respectively. The implementation along with their results has been shown below: 

`=LOWER(select_cells)`

**OUTPUT**

|                                                          Statements                                                           |
|-------------------------------------------------------------------------------------------------------------------------------|
| microsoft excel is a spreadsheet developed by microsoft for windows, macos, android and ios.                                  |
| it features calculation, graphing tools, pivot tables, and a macro programming language called visual basic for applications. |
| microsoft excel has the basic features of all spreadsheets.                                                                   |
| excel forms part of the microsoft office suite of software.                                                                   |

`=UPPER(select_cells)`

**OUTPUT**

|                                                          Statements                                                           |
|-------------------------------------------------------------------------------------------------------------------------------|
| MICROSOFT EXCEL IS A SPREADSHEET DEVELOPED BY MICROSOFT FOR WINDOWS, MACOS, ANDROID AND IOS.                                  |
| IT FEATURES CALCULATION, GRAPHING TOOLS, PIVOT TABLES, AND A MACRO PROGRAMMING LANGUAGE CALLED VISUAL BASIC FOR APPLICATIONS. |
| MICROSOFT EXCEL HAS THE BASIC FEATURES OF ALL SPREADSHEETS.                                                                   |
| EXCEL FORMS PART OF THE MICROSOFT OFFICE SUITE OF SOFTWARE.                                                                   |


## Sorting and Filtering Data in Excel
Consider a data from UCI Machine Learning Repository named Abalone. We take the first 10 rows of the data set to teach you how to perform sorting and filtering of data in Excel. 

| Gender | Length | Diam  | Height | Whole  | Shucked | Viscera | Shell | Rings |
|--------|--------|-------|--------|--------|---------|---------|-------|-------|
| M      |  0.455 | 0.365 |  0.095 |  0.514 |  0.2245 |   0.101 |  0.15 |    15 |
| M      |   0.35 | 0.265 |   0.09 | 0.2255 |  0.0995 |  0.0485 |  0.07 |     7 |
| F      |   0.53 |  0.42 |  0.135 |  0.677 |  0.2565 |  0.1415 |  0.21 |     9 |
| M      |   0.44 | 0.365 |  0.125 |  0.516 |  0.2155 |   0.114 | 0.155 |    10 |
| I      |   0.33 | 0.255 |   0.08 |  0.205 |  0.0895 |  0.0395 | 0.055 |     7 |
| I      |  0.425 |   0.3 |  0.095 | 0.3515 |   0.141 |  0.0775 |  0.12 |     8 |
| F      |   0.53 | 0.415 |   0.15 | 0.7775 |   0.237 |  0.1415 |  0.33 |    20 |
| F      |  0.545 | 0.425 |  0.125 |  0.768 |   0.294 |  0.1495 |  0.26 |    16 |
| M      |  0.475 |  0.37 |  0.125 | 0.5095 |  0.2165 |  0.1125 | 0.165 |     9 |
| F      |   0.55 |  0.44 |   0.15 | 0.8945 |  0.3145 |   0.151 |  0.32 |    19 |

The following image depicts how sorting and filtering icons look like in the Excel menu bar:

![Imgur](https://i.imgur.com/MJ9NBGy.png)

First step is to select the table and then click on the **Filter** icon. This will bring a drop down menu icon on each of the column headers. 

Let's say you want to sort these records based on the gender labels. Click on the drop-down arrow of Gender column and select **Sort A to Z**, this will result in the following table:

| Gender | Length | Diam  | Height | Whole  | Shucked | Viscera | Shell | Rings |
|--------|--------|-------|--------|--------|---------|---------|-------|-------|
| F      |   0.53 |  0.42 |  0.135 |  0.677 |  0.2565 |  0.1415 |  0.21 |     9 |
| F      |   0.53 | 0.415 |   0.15 | 0.7775 |   0.237 |  0.1415 |  0.33 |    20 |
| F      |  0.545 | 0.425 |  0.125 |  0.768 |   0.294 |  0.1495 |  0.26 |    16 |
| F      |   0.55 |  0.44 |   0.15 | 0.8945 |  0.3145 |   0.151 |  0.32 |    19 |
| I      |   0.33 | 0.255 |   0.08 |  0.205 |  0.0895 |  0.0395 | 0.055 |     7 |
| I      |  0.425 |   0.3 |  0.095 | 0.3515 |   0.141 |  0.0775 |  0.12 |     8 |
| M      |  0.455 | 0.365 |  0.095 |  0.514 |  0.2245 |   0.101 |  0.15 |    15 |
| M      |   0.35 | 0.265 |   0.09 | 0.2255 |  0.0995 |  0.0485 |  0.07 |     7 |
| M      |   0.44 | 0.365 |  0.125 |  0.516 |  0.2155 |   0.114 | 0.155 |    10 |
| M      |  0.475 |  0.37 |  0.125 | 0.5095 |  0.2165 |  0.1125 | 0.165 |     9 |

First, the records with label F (Female), followed by I (Infant) and lastly M (Male). In case, if you just want the records corresponding to Females, just select the label F (first unselect all) under the Gender drop-down menu. That should result in the following table:

| Gender | Length | Diam  | Height | Whole  | Shucked | Viscera | Shell | Rings |
|--------|--------|-------|--------|--------|---------|---------|-------|-------|
| F      |   0.53 |  0.42 |  0.135 |  0.677 |  0.2565 |  0.1415 |  0.21 |     9 |
| F      |   0.53 | 0.415 |   0.15 | 0.7775 |   0.237 |  0.1415 |  0.33 |    20 |
| F      |  0.545 | 0.425 |  0.125 |  0.768 |   0.294 |  0.1495 |  0.26 |    16 |
| F      |   0.55 |  0.44 |   0.15 | 0.8945 |  0.3145 |   0.151 |  0.32 |    19 |

## Combining Data Using the Concatenate Function







