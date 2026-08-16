```r
# Load required libraries
library(ggplot2)
library(treemapify)

# Built-in dataset
df <- mtcars

# Create a PDF file (all plots will go here)
pdf("All_Plots.pdf", width = 8, height = 6)

# 1. Column Chart (Bar Plot for categorical variable 'cyl')
ggplot(df, aes(x = factor(cyl))) +
  geom_bar(fill = "steelblue") +
  labs(title = "Count of Cars by Cylinders", x = "Cylinders", y = "Count")

# 2. Pie Chart (using dummy data)
pie_df <- data.frame(Category = c("A", "B", "C"),
                     Count = c(30, 45, 25))
ggplot(pie_df, aes(x = "", y = Count, fill = Category)) +
  geom_bar(stat = "identity", width = 1) +
  coord_polar("y") +
  labs(title = "Pie Chart Example") +
  theme_void()

# 3. Histogram (Distribution of 'mpg')
ggplot(df, aes(x = mpg)) +
  geom_histogram(binwidth = 5, fill = "orange", color = "black") +
  labs(title = "Histogram of MPG", x = "Miles per Gallon", y = "Frequency")

# 4. Scatter Plot (Weight vs MPG, colored by 'cyl')
ggplot(df, aes(x = wt, y = mpg, color = factor(cyl))) +
  geom_point(size = 3) +
  labs(title = "Scatter Plot: Weight vs MPG", x = "Weight", y = "MPG", color = "Cylinders")

# 5. Line Chart (using 'pressure' dataset)
ggplot(pressure, aes(x = temperature, y = pressure)) +
  geom_line(color = "red") +
  labs(title = "Pressure vs Temperature", x = "Temperature", y = "Pressure")

# 6. Box Plot (MPG grouped by Cylinders)
ggplot(df, aes(x = factor(cyl), y = mpg, fill = factor(cyl))) +
  geom_boxplot() +
  labs(title = "Box Plot: MPG by Cylinders", x = "Cylinders", y = "MPG")

# 7. Tree Map (Using treemapify)
tree_df <- data.frame(
  Category = c("A", "B", "C"),
  Value = c(20, 40, 60)
)
ggplot(tree_df, aes(area = Value, fill = Category, label = Category)) +
  geom_treemap() +
  geom_treemap_text(color = "white", place = "centre", size = 15) +
  labs(title = "Tree Map Example")

# 8. Faceting Example (Scatter plot split by 'cyl')
ggplot(df, aes(x = wt, y = mpg)) +
  geom_point() +
  facet_wrap(~ cyl) +
  labs(title = "Faceted Scatter Plot by Cylinders")

# Close the PDF device
dev.off()

cat("✅ All plots saved successfully in 'All_Plots.pdf'\n")


```

### output is in time remnant