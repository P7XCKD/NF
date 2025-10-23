- [ ] 1.  
### Data analytics in Excel – Lookup functions (H, V & Xlookup)  


**Dataset Example**

| Product ID | Product Name | Category | Price | Quantity | Region |
|-------------|---------------|-----------|--------|-----------|---------|
| P001 | Laptop | Electronics | 60000 | 10 | North |
| P002 | Mouse | Accessories | 800 | 50 | South |
| P003 | Keyboard | Accessories | 1500 | 40 | East |
| P004 | Monitor | Electronics | 12000 | 20 | West |
| P005 | Printer | Electronics | 7000 | 15 | North |

---

**1. VLOOKUP**

**Purpose:**  
Used to look up a value in the first column of a table and return a value in the same row from another column.

**Formula Example:**  
```excel
=VLOOKUP("P003", A2:F6, 2, FALSE)
````

**Explanation:**

-   `"P003"` → The lookup value.
    
-   `A2:F6` → The data table range.
    
-   `2` → Column index (Product Name).
    
-   `FALSE` → Exact match.
    

**Before:** You only know the Product ID.  
**After:** You can find that **P003 = Keyboard**.

**Another Example:**

```excel
=VLOOKUP("P005", A2:F6, 4, FALSE)
```

→ Returns **7000**, which is the price of Printer.

***

**2. HLOOKUP**

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

***

**3. XLOOKUP**

**Purpose:**  
A newer and more flexible lookup function replacing both VLOOKUP and HLOOKUP.  
It allows lookups both vertically and horizontally without needing column indexes.

**Formula Example:**

```excel
=XLOOKUP("P002", A2:A6, D2:D6)
```

**Explanation:**

-   `"P002"` → Lookup value.
    
-   `A2:A6` → Lookup array (Product IDs).
    
-   `D2:D6` → Return array (Prices).
    

**Before:** Only have the Product ID.  
**After:** Returns **800**, which is the price of Mouse.

**Advanced Example (with default return):**

```excel
=XLOOKUP("P010", A2:A6, D2:D6, "Not Found")
```

→ Returns **"Not Found"** since P010 doesn’t exist in the dataset.

***

**Summary of Differences**

| Function | Lookup Direction | Needs Column/Row Index | Works with Missing Data | Simplified Syntax |
| --- | --- | --- | --- | --- |
| VLOOKUP | Vertical | Yes | No  | No  |
| HLOOKUP | Horizontal | Yes | No  | No  |
| XLOOKUP | Both | No  | Yes | Yes |

***

**Practical Insight**

| Task | Formula | Result |
| --- | --- | --- |
| Find product name of P003 | `=VLOOKUP("P003", A2:F6, 2, FALSE)` | Keyboard |
| Find price of P004 | `=HLOOKUP("P004", B1:F3, 3, FALSE)` | 12000 |
| Find price of P002 using XLOOKUP | `=XLOOKUP("P002", A2:A6, D2:D6)` | 800 |

***

**Before & After Effect**

| Stage | Description |
| --- | --- |
| Before | You have a large dataset and manually search for values (time-consuming). |
| After | Lookup functions instantly fetch related data automatically, improving accuracy and speed. |
***

- [ ] 2.  
### Pivot tables in Excel, dashboard and slicer in Excel  


**How a PivotTable Works**

PivotTables summarize large datasets and allow dynamic data analysis. They have **four main components**:

1. **Columns**  
   - Columns are vertical tabular data.  
   - The column includes a unique header at the top, defining what data is listed downwards.  
   - Example: **D5 (Sum of Attack)** is the header.  
   - Data: `D6 (110), D7 (100), D8 (50), D9 (73)`, etc.  

   ![Pivot Table Column Highlighted](https://www.w3schools.com/excel/img_excel_pivot_table_column.png)  

2. **Rows**  
   - Rows are horizontal tabular data.  
   - Data in the same row are related.  
   - Example: **A8 (Alakazam)** is the Pokémon name.  
   - Stats: `B8 (500), C8 (55), D8 (50), E8 (45)` correspond to the column headers.  

   ![Pivot Table Row Highlighted](https://www.w3schools.com/excel/img_excel_table_pivot_row.png)  

3. **Filters**  
   - Filters allow selection of what data you see in the PivotTable.  
   - Example: Filters **Generation** and **Type 1** set to `Generation 1` and `Type Psychic`.  
   - Only Pokémon meeting these criteria are displayed.  

   ![Pivot Table Filter Highlighted](https://www.w3schools.com/excel/img_excel_table_pivot_filter.png)  
   ![Pivot Table Filter view](https://www.w3schools.com/excel/img_excel_table_pivot_filter_view.png)  

4. **Values**  
   - Values define how the data is presented.  
   - You can summarize values (Sum, Count, Average, etc.).  
   - Example: Range `B5:E5` is summarized using **Sum**, displayed in `B14:E14`.  

   ![Pivot Table Value Range Highlighted](https://www.w3schools.com/excel/img_excel_table_pivot_values.png)  
   ![Values settings view](https://www.w3schools.com/excel/img_excel_table_pivot_values_view.png)  

---

**Fields and Layout**

The PivotTable display is controlled via the **PivotTable Fields panel**. The panel has two main parts: **Fields** and **Layout**.

1. **Fields**  
   - Checkboxes select/unselect which data appears in the PivotTable.  
   - Example: Selecting **Speed** displays it in the table.  
   - Arrow next to the field allows changing how the data is summarized.  

   ![Fields in panel](https://www.w3schools.com/excel/img_excel_table_pivot_fields_panel.png)  
   ![Fields properties](https://www.w3schools.com/excel/img_excel_table_pivot_fields_panel_properties.png)  

2. **Layout**  
   - Drag and drop fields into **Filters, Rows, Columns, or Values** boxes to arrange the PivotTable.  
   - Example: Dragging **Sp. Def** to **Values** adds it to the table.  

   ![Drag and drop to display data](https://www.w3schools.com/excel/img_excel_table_pivot_fields_panel_drag_and_drop.png)  
   ![Added SP def to table](https://www.w3schools.com/excel/img_excel_table_pivot_fields_added_spdef.png)  
   ![Change settings layout fields](https://www.w3schools.com/excel/img_excel_table_pivot_settings_layout.png)  

---


**Practical Tips for Exams**

- **Columns and Rows:** Know which data goes where. Columns are vertical headers (e.g., Product Name, Sales), and Rows are horizontal entries (e.g., Region, Salesperson).  
- **Filters:** Use filters to view only a subset of data (e.g., specific regions, products, or time periods).  
- **Values:** Check how the data is summarized: Sum, Count, Average, Max, Min. Always confirm the correct aggregation.  
- **Fields Panel:** Drag-and-drop fields to Filters, Rows, Columns, or Values to restructure your PivotTable.  
- **Dynamic Analysis:** Any change in Filters, Rows, Columns, or Values instantly updates the PivotTable.  

---

**Example Practical Task – Sales Dataset**

| Region | Product | Salesperson | Sales | Profit |
|--------|---------|------------|-------|--------|
| North  | Laptop  | Ramesh     | 55000 | 5000  |
| South  | Mouse   | Priya      | 25000 | 4000  |
| East   | Keyboard| Anil       | 40000 | 3500  |
| West   | Monitor | Sita       | 70000 | 6000  |
| North  | Printer | John       | 30000 | 2500  |

---

**Step-by-Step Guide**

1. **Insert PivotTable**  
   - Select the dataset.  
   - Go to **Insert → PivotTable → New Worksheet**.  
   - A blank PivotTable appears with **PivotTable Fields Panel** on the right.  

2. **Assign Rows and Columns**  
   - Drag **Region** to **Rows** → Each region is listed vertically.  
   - Drag **Product** to **Columns** → Each product forms a column.  

3. **Add Values**  
   - Drag **Sales** to **Values** → Shows total sales for each region-product combination.  
   - Check the aggregation (default is **Sum**). Change if needed via field settings.  

4. **Apply Filters**  
   - Drag **Region** or **Salesperson** to **Filters**.  
   - Example: Filter **Region** to only show North and South → PivotTable now only shows these regions.  

5. **Add Additional Insight**  
   - Drag **Profit** into **Values** → Now the PivotTable shows both Sales and Profit per product per region.  

---

**Result Example Table**

| Region | Laptop | Mouse | Keyboard | Monitor | Printer | Grand Total |
|--------|--------|-------|---------|--------|---------|-------------|
| North  | 55000  |       |         |        | 30000  | 85000       |
| South  |        | 25000 |         |        |         | 25000       |
| Grand Total | 55000 | 25000 | 0 | 0 | 30000 | 110000 |

- Columns = Products  
- Rows = Regions  
- Values = Sales & Profit  
- Filters = Applied to limit data  

---

**If Something Goes Wrong**  

- **Blank or missing data:** Check the dataset for empty cells or spelling errors.  
- **PivotTable not updating:** Click **Refresh** under PivotTable Tools.  
- **Wrong aggregation:** Click the value → **Value Field Settings** → Change Sum/Count/Average as needed.  
- **Incorrect rows/columns:** Re-drag fields in the **Fields Panel** to correct position.  

This ensures your PivotTable is accurate and displays the desired insights clearly.

### click next 4 more info: [Introduction Excel PivotTable](https://www.w3schools.com/excel/excel_table_pivot_intro.php)

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


