 # Viva Stuffs

---

## **1. Download and Installation of Power BI**

### **What is Power BI?**
Power BI is a data analytics and visualization tool by Microsoft that allows users to connect to various data sources, transform data, and create interactive reports and dashboards.  

**Example:** You can connect Excel sales data, clean it, and visualize monthly sales performance.

### **What are the advantages of Power BI?**
- Easy to use and learn.  
- Connects to multiple data sources (Excel, SQL, web, etc.).  
- Real-time data updates and automatic refresh.  
- Interactive dashboards and visualizations.  
- Cloud-based sharing and collaboration.  

**Example:** A company’s sales manager can check daily sales performance in real-time using a Power BI dashboard.

### **What are some disadvantages of Power BI?**
- Limited customization in visuals compared to coding tools.  
- Requires strong internet for Power BI Service.  
- Large datasets can slow down performance.  
- Limited free version features.  

**Example:** When using very large Excel files, Power BI may take longer to load visuals.

### **What is a common workflow in Power BI?**
1. **Import data** from various sources.  
2. **Clean and transform data** using Power Query Editor.  
3. **Model relationships** between tables.  
4. **Create visuals and reports.**  
5. **Publish dashboards** to Power BI Service.  

**Example:** Importing a sales Excel file → Cleaning region names → Building a sales report → Publishing it to share with your team.

### **What are the main business applications of Power BI?**
- Sales and marketing analysis.  
- Financial performance tracking.  
- HR and workforce analytics.  
- Supply chain management.  
- Customer insights and trend analysis.  

**Example:** Retail companies use Power BI to track daily sales and compare regional performance.

---

## **2. Simple Bar Chart and Line Chart**

### **Purpose of a Simple Bar Chart**
A **Bar Chart** is used to compare values across different categories, such as sales by region or department.  

**Example:** Comparing total sales across North, South, East, and West regions.

### **How to create a Simple Bar Chart in Power BI**
1. Import your dataset.  
2. Drag the **“Bar Chart”** visual from the Visualizations pane.  
3. Add a **category** (e.g., Region) to the Axis.  
4. Add a **numerical value** (e.g., Sales) to the Values field.  

**Example:** Drag “Region” to Axis and “Sales” to Values to display sales per region.

### **Main features of a Line Chart**
- Displays trends over time.  
- Shows continuous data changes.  
- Can include multiple lines for comparison.  

**Example:** Shows monthly revenue growth of two different product lines.

### **How to create a Line Chart in Power BI**
1. Select the **“Line Chart”** visual.  
2. Add a **date or time field** to the Axis.  
3. Add a **value field** (e.g., Sales) to the Values section.  
4. Optionally, add another field to the Legend to compare groups.  

**Example:** Plot “Month” on Axis and “Sales” on Values to track monthly performance.

### **Example scenario where a Line Chart is appropriate**
Tracking monthly revenue, stock price changes, or website visits over time.

---

## **3. Map Visualization**

### **Purpose of using map visualizations in Power BI**
Map visualizations show geographic data to identify regional trends, patterns, and performance differences.  

**Example:** Visualizing which regions generate the highest sales.

### **Types of map visualizations available in Power BI**
1. **Basic Map** – Displays data points on a map.  
2. **Filled Map (Choropleth Map)** – Shades regions based on values.  
3. **ArcGIS Map** – Advanced mapping with more layers and features.  
4. **Shape Map** – Uses custom shapes or boundaries.  

**Example:** A Filled Map can show sales intensity by color across different states.

### **What are the types of maps in Power BI**
- Map  
- Filled Map  
- ArcGIS Map  
- Shape Map  
- Azure Map  

### **Example scenario for map visualization**
Showing the number of customers or sales revenue per country.

### **Type of data best represented using maps**
Data with **geographic fields** like city, state, country, or latitude and longitude.  

**Example:** Showing store locations across India using city names.

### **Handling geographic data in Power BI**
1. Ensure data fields (e.g., City, Country) are properly categorized.  
2. Use “Data Category” in Power BI to assign geographic roles.  
3. Add the field to a map visual.  

**Example:** Assign “City” as a location field before plotting it on a map.

---

## **4. Basic Data Import and Cleaning**

### **Purpose of Power Query in Power BI**
Power Query helps you import, clean, and transform data before creating reports.  

**Example:** Removing duplicates or correcting misspelled city names.

### **What is Power Query and how is it used in Power BI?**
Power Query is a tool inside Power BI used to connect to data sources, clean messy data, and prepare it for analysis.  

**Example:** Load an Excel file, fix column names, and remove blank rows using Power Query.

### **Main features of Power Query**
- Connect to multiple data sources.  
- Remove duplicates and errors.  
- Combine or merge tables.  
- Change data types and rename columns.  
- Create custom calculated columns.  

**Example:** Merge customer and sales tables into one clean dataset.

### **How to import data using Power Query**
1. Click **Home → Get Data → Excel (or other source)**.  
2. Choose your file and table.  
3. Click **Transform Data** to open Power Query Editor.  
4. Apply cleaning steps and load data into Power BI.  

**Example:** Import “sales_data.xlsx” → Clean data → Load into report.

### **Common data transformation tasks**
- Removing duplicates or blank rows.  
- Filling missing values.  
- Changing column names.  
- Merging and appending tables.  
- Splitting columns.  

**Example:** Fill missing “Region” values and remove duplicate entries.

---

## **5. Implement Basic Data Filtering using Slicers**

### **What is a Slicer in Power BI?**
A **Slicer** is an interactive filter that lets users select values to filter visuals dynamically.  

**Example:** Selecting a specific year to view sales for that period only.

### **Purpose of using slicers**
Slicers help users focus on specific subsets of data (e.g., specific regions, dates, or categories).  

**Example:** Filtering data to view only “North Region” performance.

### **How slicers enhance interactivity**
They make dashboards more user-friendly by allowing instant filtering without editing the visuals.  

**Example:** A slicer allows a manager to instantly switch between different product categories.

---

## **6. Dashboard Creation**

### **What is a dashboard in Power BI?**
A dashboard is a single-page, interactive view combining multiple visualizations.  

**Example:** A dashboard showing sales, profit, and top products in one view.

### **Purpose of a dashboard**
To give decision-makers a quick summary of key performance indicators (KPIs) and insights.  

**Example:** Management can instantly check monthly revenue vs. target.

### **Difference between a dashboard and a report**
- **Report**: Multiple pages with detailed visuals.  
- **Dashboard**: One page with summarized visuals from different reports.  

**Example:** A detailed sales report can feed into a one-page executive dashboard.

### **How to create a dashboard in Power BI**
1. Create visuals in Power BI Desktop.  
2. Publish your report to Power BI Service.  
3. Pin visuals to a new or existing dashboard.  

**Example:** Pin sales chart, map, and KPIs from a report into one dashboard.

### **Example business scenario for a dashboard**
An **executive dashboard** showing total sales, profit margin, and regional performance in one view.  

**Example:** The CEO uses the dashboard to view company-wide KPIs.

### **How to interpret and analyze data on a dashboard**
- Identify trends and outliers.  
- Compare KPIs against targets.  
- Drill down for detailed insights.  

**Example:** Spot declining sales in one region and analyze the cause using other visuals.

---
