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

## Conclusion  

In 