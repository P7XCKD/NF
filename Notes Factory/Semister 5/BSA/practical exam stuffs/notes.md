- [ ] 1.  
## Data analytics in Excel – Lookup functions (H, V & Xlookup)  

### **HLOOKUP**

**Purpose:**  
Used to look up a value in the first row of a table and return a value from a specified row below it.

**Transposed Example Dataset**

| Product ID | P001 | P002 | P003 | P004 | P005 |
| --- | --- | --- | --- | --- | --- |
| Product Name | Laptop | Mouse | Keyboard | Monitor | Printer |
| Price | 60000 | 800 | 1500 | 12000 | 7000 |

**Formula Example:**

```excel
=HLOOKUP("P004", B1:F3, 3, FALSE)
```

**Explanation:**

-   `"P004"` → Lookup value.
    
-   `B1:F3` → Table range.
    
-   `3` → Row index (Price).
    
-   `FALSE` → Exact match.
    

**Before:** You have only the Product ID.  
**After:** The function returns **12000**, the price of Monitor.

### VLOOKUP function in Excel

The **VLOOKUP function** is one of the most popular functions in **Excel**. This page contains many easy to follow VLOOKUP examples.

#### Exact Match

Most of the time you are looking for an exact match when you use the VLOOKUP function in Excel. Let's take a look at the arguments of the VLOOKUP function.

1. The VLOOKUP function below looks up the value 53 (first argument) in the leftmost column of the red table (second argument).

![VLOOKUP arguments](https://www.excel-easy.com/examples/images/vlookup/vlookup-arguments.png "VLOOKUP arguments")

2. The value 4 (third argument) tells the VLOOKUP function to return the value in the same row from the fourth column of the red table.

![VLOOKUP result in Excel](https://www.excel-easy.com/examples/images/vlookup/vlookup-result.png "VLOOKUP result in Excel")

Note: the Boolean FALSE (fourth argument) tells the VLOOKUP function to return an exact match. If the VLOOKUP function cannot find the value 53 in the first column, it will return a [#N/A error](https://www.excel-easy.com/examples/vlookup.html#na-error).

3. Here's another example. Instead of returning the salary, the VLOOKUP function below returns the last name (third argument is set to 3) of ID 79.

![Exact Match](https://www.excel-easy.com/examples/images/vlookup/exact-match.png "Exact Match")

#### Approximate Match

Let's take a look at an example of the VLOOKUP function in approximate match mode (fourth argument set to TRUE).

1. The VLOOKUP function below looks up the value 85 (first argument) in the leftmost column of the red table (second argument). There's just one problem. There's no value 85 in the first column.

![VLOOKUP function in Approximate Match Mode](https://www.excel-easy.com/examples/images/vlookup/vlookup-function-approximate-match-mode.png "VLOOKUP function in Approximate Match Mode")

2. Fortunately, the Boolean TRUE (fourth argument) tells the VLOOKUP function to return an approximate match. If the VLOOKUP function cannot find the value 85 in the first column, it will return the largest value smaller than 85. In this example, this will be the value 80.

![Largest Value Smaller than Lookup Value](https://www.excel-easy.com/examples/images/vlookup/largest-value-smaller-than-lookup-value.png "Largest Value Smaller than Lookup Value")

3. The value 2 (third argument) tells the VLOOKUP function to return the value in the same row from the second column of the red table.

![Approximate Match in Excel](https://www.excel-easy.com/examples/images/vlookup/approximate-match.png "Approximate Match in Excel")

Note: always sort the leftmost column of the red table in ascending order if you use the VLOOKUP function in approximate match mode (fourth argument set to TRUE).
***

***
### XLOOKUP function in Excel

If you have Excel 365 or Excel 2021, use XLOOKUP instead of [VLOOKUP](https://www.excel-easy.com/examples/vlookup.html). The **XLOOKUP function** is easier to use and has some additional advantages.

#### Exact Match

By default, the XLOOKUP function in **Excel 365/2021** performs an exact match.

1. The XLOOKUP function below looks up the value 53 (first argument) in the range B3:B9 (second argument).

![XLOOKUP arguments](https://www.excel-easy.com/examples/images/xlookup/xlookup-arguments.png "XLOOKUP arguments")

2. Next, it simply returns the value in the same row from the range E3:E9 (third argument).

![XLOOKUP function in Excel](https://www.excel-easy.com/examples/images/xlookup/xlookup-function.png "XLOOKUP function in Excel")

3. Here's another example. Instead of returning the salary, the XLOOKUP function below returns the last name (replace E3:E9 with D3:D9) of ID 79.

![Exact Match](https://www.excel-easy.com/examples/images/xlookup/exact-match.png "Exact Match")

- [ ] 2.  
### Pivot tables in Excel, dashboard and slicer in Excel  

**Pivot tables** are one of **Excel**'s most powerful features. A pivot table allows you to extract the significance from a large, detailed data set.

Our data set consists of 213 records and 6 fields. Order ID, Product, Category, Amount, Date and Country.

![Pivot Table Data in Excel](https://www.excel-easy.com/data-analysis/images/pivot-tables/pivot-table-data.png "Pivot Table Data in Excel")

### Insert a Pivot Table

To insert a **pivot table**, execute the following steps.

1. Click any single cell inside the data set.

2. On the Insert tab, in the Tables group, click PivotTable.

![Insert Excel Pivot Table](https://www.excel-easy.com/data-analysis/images/pivot-tables/insert-pivot-table.png "Insert Excel Pivot Table")

The following dialog box appears. Excel automatically selects the data for you. The default location for a new pivot table is New Worksheet.

3. Click OK.

![Create PivotTable Dialog Box](https://www.excel-easy.com/data-analysis/images/pivot-tables/create-pivot-table-dialog-box.png "Create PivotTable Dialog Box")

### Drag fields

The **PivotTable Fields pane** appears. To get the total amount exported of each product, drag the following fields to the different areas.

1. Product field to the Rows area.

2. Amount field to the Values area.

3. Country field to the Filters area.

![Drag Fields to Areas](https://www.excel-easy.com/data-analysis/images/pivot-tables/drag-fields-areas.png "Drag Fields to Areas")

Below you can find the pivot table. Bananas are our main export product. That's how easy pivot tables can be!

![Pivot Table](https://www.excel-easy.com/data-analysis/images/pivot-tables/pivot-table.png "Pivot Table")

### Sort a Pivot Table

To get Banana at the top of the list, sort the pivot table.

1. Click any cell inside the Sum of Amount column.

2. Right click and click on Sort, Sort Largest to Smallest.

![Sort Largest to Smallest](https://www.excel-easy.com/data-analysis/images/pivot-tables/sort-largest-to-smallest.png "Sort Largest to Smallest")

Result:

![Sorted Pivot Table](https://www.excel-easy.com/data-analysis/images/pivot-tables/sorted-pivot-table.png "Sorted Pivot Table")

### Filter a Pivot Table

Because we added the Country field to the Filters area, we can filter this pivot table by Country. For example, which products do we export the most to France?

1. Click the filter drop-down and select France.

Result: Apples are our main export product to France.

![Filtered Pivot Table](https://www.excel-easy.com/data-analysis/images/pivot-tables/filtered-pivot-table.png "Filtered Pivot Table")

Note: you can use the standard filter (triangle next to Row Labels) to only show the amounts of specific products.

### Change Summary Calculation

By default, Excel summarizes your data by either summing or counting the items. To change the type of calculation that you want to use, execute the following steps.

1. Click any cell inside the Sum of Amount column.

2. Right click and click on Value Field Settings.

![Value Field Settings](https://www.excel-easy.com/data-analysis/images/pivot-tables/value-field-settings.png "Value Field Settings")

3. Choose the type of calculation you want to use. For example, click Count.

![Summarize Value Field By](https://www.excel-easy.com/data-analysis/images/pivot-tables/summarize-value-field-by.png "Summarize Value Field By")

4. Click OK.

Result: 16 out of the 28 orders to France were 'Apple' orders.

![Count](https://www.excel-easy.com/data-analysis/images/pivot-tables/count.png "Count")

### Two-dimensional Pivot Table

If you drag a field to the Rows area and Columns area, you can create a two-dimensional pivot table. First, [insert a pivot table](https://www.excel-easy.com/data-analysis/pivot-tables.html#insert-pivot-table). Next, to get the total amount exported to each country, of each product, drag the following fields to the different areas.

1. Country field to the Rows area.

2. Product field to the Columns area.

3. Amount field to the Values area.

4. Category field to the Filters area.

![Create Two-dimensional Pivot Table](https://www.excel-easy.com/data-analysis/images/pivot-tables/create-two-dimensional-pivot-table.png "Create Two-dimensional Pivot Table")

Below you can find the two-dimensional pivot table.

![Two-dimensional Pivot Table in Excel](https://www.excel-easy.com/data-analysis/images/pivot-tables/two-dimensional-pivot-table.png "Two-dimensional Pivot Table in Excel")



### Creating an Excel Dashboard – Step-by-Step Guide  

![image](.attachments/fff4353e7e51d97a8826c91c3dc052a4ca202001.png) 
data ^
![image](.attachments/66966288c05478cb75a59abef8369b1ad73bcd50.png) 
select pivot chart on right side of insert tab 
rest figure out urself
![image](.attachments/b476324c7d5a50c39fcf7a2fca2ab0d4ad25d07b.png) 
***

### slicer
Use **slicers in Excel** to quickly and easily filter pivot tables. Connect multiple slicers to multiple pivot tables to create awesome reports.

Below you can find a pivot table. Go back to [Pivot Tables](https://www.excel-easy.com/data-analysis/pivot-tables.html) to learn how to create this pivot table.

![Pivot Table](https://www.excel-easy.com/examples/images/slicers/pivot-table.png "Pivot Table")

To **insert a slicer**, execute the following steps.

1. Click any cell inside the pivot table.

2. On the PivotTable Analyze tab, in the Filter group, click Insert Slicer.

![Insert Slicer](https://www.excel-easy.com/examples/images/slicers/insert-slicer.png "Insert Slicer")

3. Check Country and click OK.

![Insert Slicers](https://www.excel-easy.com/examples/images/slicers/insert-slicers.png "Insert Slicers")

4. Click United States to find out which products we export the most to the United States.

![Excel Slicer](https://www.excel-easy.com/examples/images/slicers/slicer.png "Excel Slicer")

Conclusion: bananas are our main export product to the United States. The report filter (cell B1) changes to United States.

OK, that was pretty easy. Let's insert a second slicer.

5. Click any cell inside the pivot table.

6. On the PivotTable Analyze tab, in the Filter group, click Insert Slicer.

![Insert Slicer](https://www.excel-easy.com/examples/images/slicers/insert-slicer.png "Insert Slicer")

7. Check Product and click OK.

![Insert Another Slicer](https://www.excel-easy.com/examples/images/slicers/insert-another-slicer.png "Insert Another Slicer")

8. Select the slicer.

9. On the Slicer tab, in the Slicer Styles group, click a slicer style.

![Change Slicer Style](https://www.excel-easy.com/examples/images/slicers/change-slicer-style.png "Change Slicer Style")

10. Use the second slicer. Click the Multi-Select button to select multiple products.

![Multiple Slicers](https://www.excel-easy.com/examples/images/slicers/multiple-slicers.png "Multiple Slicers")

Note: instead of using the Multi-Select button, hold down CTRL to select multiple items.

To really impress your boss, execute the following steps.

11. Insert a second pivot table.

To connect both slicers to this pivot table, execute the following steps.

12. Select the first slicer.

13. On the Slicer tab, in the Slicer group, click Report Connections.

![Click Report Connections](https://www.excel-easy.com/examples/images/slicers/click-report-connections.png "Click Report Connections")

14. Select the second pivot table and click OK.

![Connect Slicer to Pivot Table](https://www.excel-easy.com/examples/images/slicers/connect-slicer-to-pivot-table.png "Connect Slicer to Pivot Table")

15. Repeat steps 12-14 for the second slicer.

16. Use both slicers.

![Multiple Slicers and Pivot Tables](https://www.excel-easy.com/examples/images/slicers/multiple-slicers-pivot-tables.png "Multiple Slicers and Pivot Tables")

Conclusion: the total amount of apples exported to Canada equals $24,867 (6 orders) and the total amount of oranges exported to Canada equals $19,929 (3 orders).

17. Click the icon in the upper-right corner of a slicer to clear the filter.

![Clear Filter](https://www.excel-easy.com/examples/images/slicers/clear-filter.png "Clear Filter")

Note: we didn't export any beans or carrots to Canada. Try it yourself, download the Excel file and use slicers to create awesome reports.
***

- [ ] 3.  
### What if analysis in MS Excel  

***

- [ ] 4.  
### Data structures in R – Vectors, Lists, Arrays, Matrices, Factors, Data Frames  

***

- [ ] 5.  
### To import, clean & transform raw data in R  

***

- [ ] 6.  
### To perform data manipulation using dplyr in R  

***

- [ ] 7.  
### To perform data visualization with ggplot2  

***

- [ ] 8.  
### Data transformation using Power Query Editor in Power BI  

***

- [ ] 9.  
### Creating various charts and map visualization in Power BI  

***

- [ ] 10.  
### Slicers and filters in Power BI  

***

- [ ] 11.  
### To generate and publish dashboards and reports in Power BI  

***


