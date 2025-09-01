# Experiment No. 8  
**Title:** Data visualization with ggplot2  

**Aim:**  
To perform data visualization with ggplot2 in R.  

**Software Used:**  
R and RStudio  

---

## Theory  
**ggplot2** is an R package for data visualization based on the **Grammar of Graphics**. It builds plots by combining:  
- **geom_()** → plot type (bar, line, scatter, etc.)  
- **aes()** → mapping of variables (x, y, color, fill)  
- **facets** → split data into multiple panels  
- **labels & scales** → add titles, axes, legends, and adjust appearance  

---

## Practical – Steps  

1. Open RStudio and load the `ggplot2` library.  
2. Prepare or import a dataset (e.g., `mtcars`, `iris`, or a CSV file).  
3. Select variables:  
   - Categorical → for column, pie, tree, stacked bar.  
   - Numerical → for histogram, line, scatter, box.  
4. Choose appropriate geom function:  
   - `geom_bar()` → Column / Stacked Bar.  
   - `geom_bar() + coord_polar("y")` → Pie Chart.  
   - `geom_histogram()` → Histogram.  
   - `geom_point()` → Scatter Plot.  
   - `geom_line()` → Line Chart.  
   - `geom_boxplot()` → Box Plot.  
   - `geom_treemap()` (treemapify package) → Tree Map.  
   - `maps` / `ggmap` → Geomaps.  
5. Add aesthetics (`aes()`) to map variables like x, y, color, fill, group.  
6. Customize visualization using titles and labels (`labs()`, `xlab()`, `ylab()`) and modify scales (`scale_*()`).  
7. Apply grouping inside `aes()` to compare categories.  
8. Apply faceting with `facet_wrap()` or `facet_grid()` for multiple subplots.  
9. Render the chart and check the output in the plots pane.  
10. Save or export the visualization using `ggsave()`.  

---

```r
# Data Visualization with ggplot2
library(ggplot2)
library(treemapify)   # for treemap

# Sample data
df <- mtcars

# Column Chart
ggplot(df, aes(factor(cyl))) + geom_bar(fill="steelblue")

# Pie Chart
pie_df <- data.frame(Category=c("A","B","C"), Count=c(30,45,25))
ggplot(pie_df, aes(x="", y=Count, fill=Category)) +
  geom_bar(stat="identity") + coord_polar("y")

# Histogram
ggplot(df, aes(mpg)) + geom_histogram(binwidth=5, fill="orange")

# Scatter Plot
ggplot(df, aes(wt, mpg, color=factor(cyl))) + geom_point(size=3)

# Line Chart
ggplot(pressure, aes(temperature, pressure)) + geom_line(color="red")

# Box Plot
ggplot(df, aes(factor(cyl), mpg, fill=factor(cyl))) + geom_boxplot()

# Tree Map
tree_df <- data.frame(Category=c("A","B","C"), Value=c(20,40,60))
ggplot(tree_df, aes(area=Value, fill=Category)) + geom_treemap()

# Faceting Example
ggplot(df, aes(wt, mpg)) + geom_point() + facet_wrap(~cyl)

```
























## Conclusion  

In 