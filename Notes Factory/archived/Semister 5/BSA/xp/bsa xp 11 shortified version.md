
## Experiment: 11 bsa shortified version

### 1. Aim

To visualize a dataset using various chart types in power bi



### 2. Theory

#### 2.1 Introduction to Power BI

Power BI is Microsoft’s business intelligence and data analytics tool used to connect, clean, transform, and visualize data through interactive dashboards and reports. It enables analysts, organizations, and decision-makers to explore data, uncover insights, and make informed decisions efficiently.

#### 2.2 Importance of Data Visualization

Data visualization converts raw numerical information into graphical formats like charts and graphs. This helps to:  
• Identify trends and patterns.  
• Compare categories and time periods.  
• Detect outliers or unusual values.  
• Support data-driven decisions and improve communication.

#### 2.3 Chart Types Used

• **Bar / Column Chart:** Compares values across categories (e.g., sales by product).  
• **Line Chart:** Shows trends over time (e.g., monthly revenue growth).  
• **Pie / Donut Chart:** Represents parts of a whole, such as market share or percentage contribution.  
• **Histogram:** Displays frequency distribution of numeric data (e.g., customer ages).  
• **Crosstab (Matrix):** Compares two dimensions and summarizes measures like sales or profit.  
• **Box Plot:** Shows data spread using median, quartiles, and outliers.  
• **Bubble Chart:** Plots three variables using X, Y, and bubble size to represent relationships.

By combining these charts, a comprehensive and interactive dashboard can be created for effective data analysis.

***

### 3. Procedure

#### 3.1 Preparing the Dataset

1.  Choose or create a dataset (e.g., Sales Data — Date, Region, Product, Quantity, Revenue, Profit).
    
2.  Open **Power BI Desktop** → click **Home → Get Data** → import data from Excel/CSV/SQL.
    
3.  Verify data types (text, number, date, currency, etc.).
    
4.  Use **Transform Data** to clean and format data:
    
    -   Remove nulls or duplicates.
        
    -   Rename columns for clarity.
        
    -   Adjust number and date formats.
        

#### 3.2 Creating Visualizations

(a) **Bar Chart:** Insert _Clustered Column Chart_ → Axis: Product → Values: Revenue → Format and title.  
(b) **Line Chart:** Insert _Line Chart_ → X-axis: Date → Values: Sales → Set axis to Continuous.  
(c) **Pie Chart:** Insert _Pie Chart_ → Legend: Region → Values: Profit → Add percentage labels.  
(d) **Histogram:** Create numeric bins via _Modeling → New Group_ → Use Column Chart to display count by bin.  
(e) **Crosstab (Matrix):** Insert _Matrix_ → Rows: Region → Columns: Product → Values: Sales → Enable totals.  
(f) **Box Plot:** Add _Box and Whisker_ visual → Category: Region → Values: Profit.  
(g) **Bubble Chart:** Insert _Scatter Chart_ → X: Sales → Y: Profit → Size: Quantity → Legend: Region → Add Play Axis (Date) for time-based animation.

#### 3.3 Dashboard Formatting

• Use the _Format Pane_ to adjust colors, labels, and titles.  
• Add _Slicers_ for interactive filtering by category, region, or date.  
• Arrange visuals neatly for a clear, professional dashboard layout.  
• Save the Power BI file for sharing or future use.

***

### 4. Conclusion
