#  Machine Learning Viva Notes

---

### **1. What is Supervised Learning?**
Supervised learning is a type of machine learning where the model is trained using labeled data — meaning both input and output are known. The algorithm learns the relationship between them to make predictions on new data.  
**Example:** Predicting house prices using features like area, rooms, and location.

---

### **2. Support Vector Machine (SVM)**
SVM is a supervised learning algorithm used for classification and regression problems. It finds the best possible boundary (hyperplane) that separates different classes with the maximum margin.  
**Example:** Classifying emails as *spam* or *not spam*.

---

### **3. Decision Tree**
A decision tree is a model that splits data into branches based on feature conditions, leading to decisions at leaf nodes. It works well for both classification and regression tasks and is easy to interpret.  
**Example:** Predicting whether a person will buy a car based on income and age.

---

### **4. Difference between Decision Tree and Clustering**
Decision trees are **supervised** models that predict a specific output based on labeled data, while clustering is **unsupervised** and groups similar data without predefined labels.  
**Example:** Decision tree for predicting exam results; clustering for grouping students by learning patterns.

---

### **5. Hierarchical Clustering**
Hierarchical clustering builds a tree-like structure (dendrogram) of nested clusters. It can be **agglomerative (bottom-up)** or **divisive (top-down)**, depending on how clusters are formed.  
**Example:** Grouping customers based on spending behavior similarity.

---

### **6. Ensemble Learning**
Ensemble learning combines multiple machine learning models to get better accuracy and stability than a single model. It reduces overfitting and improves generalization by merging different predictions.  
**Example:** Combining decision trees in a random forest for stronger results.

---

### **7. Bagging (Bootstrap Aggregating)**
Bagging trains several models on random subsets of the data and combines their outputs to form a final prediction. It helps reduce variance and improves accuracy in unstable models like decision trees.  
**Example:** Random Forest uses bagging to build multiple trees.

---

### **8. Boosting**
Boosting trains models one after another, where each new model focuses on correcting the mistakes made by the previous ones. It aims to reduce bias and improve model performance over time.  
**Example:** AdaBoost or Gradient Boosting for improved classification accuracy.

---

### **9. Random Forest**
Random Forest is an ensemble algorithm that builds multiple decision trees using bagging and takes the majority vote (for classification) or average (for regression). It is accurate and reduces overfitting.  
**Example:** Predicting loan approval based on multiple user features.

---

### **10. Numpy**
NumPy is a Python library used for numerical and scientific computing. It supports operations on large, multi-dimensional arrays and provides mathematical functions for fast data processing.  
**Example:** Performing matrix operations or statistical calculations efficiently.

---

### **11. Pandas**
Pandas is a data analysis library that provides tools like DataFrame and Series to handle structured data. It is widely used for data cleaning, transformation, and analysis.  
**Example:** Reading and analyzing data from CSV files.

---

### **12. Matplotlib**
Matplotlib is a Python library used for creating visualizations such as line charts, bar graphs, histograms, and scatter plots. It helps in understanding patterns and trends in data visually.  
**Example:** Plotting sales growth over months using a line graph.

---

### **13. Scikit-learn (Sklearn)**
Scikit-learn is a machine learning library in Python that provides simple and efficient tools for data mining and data analysis. It includes ready-to-use implementations of ML algorithms like SVM, Decision Trees, and Random Forests.  
**Example:** Building a classification model to predict student grades.

---

### **14. Difference between K-Means and K-Medoids**
K-Means groups data using the average of cluster points (centroid), while K-Medoids uses an actual data point as the cluster center, making it more robust to outliers.  
**Example:** K-Means for customer segmentation; K-Medoids when outliers are present in data.

---

### **15. Subagging**
Subagging (Subset Aggregating) is similar to bagging but uses smaller random subsets of data without replacement. It is computationally faster and still reduces model variance.  
**Example:** Training multiple models on 70% subsets of data and combining their predictions.

---

### **16. Stacking**
Stacking combines predictions from multiple different models using another model (called a meta-learner) to make the final decision. It helps leverage the strengths of various algorithms together.  
**Example:** Combining Decision Tree, SVM, and Logistic Regression for higher accuracy.