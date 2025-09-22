
## code
```py
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report, confusion_matrix, roc_auc_score

# 1. Load dataset
df = pd.read_csv('e.csv')

# 2. Check columns to confirm names
print("Columns in dataset:\n", df.columns.tolist())

# 3. Define features and target
X = df[['balance', 'income', 'age']]
y = df['default']

# 4. Split dataset into train and test
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)

# 5. Feature scaling
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# 6. Train logistic regression model
model = LogisticRegression(max_iter=1000)
model.fit(X_train_scaled, y_train)

# 7. Predictions
y_pred = model.predict(X_test_scaled)
y_prob = model.predict_proba(X_test_scaled)[:, 1]

# 8. Evaluation
print("Confusion Matrix:\n", confusion_matrix(y_test, y_pred))
print("\nClassification Report:\n", classification_report(y_test, y_pred))
print("ROC AUC Score:", roc_auc_score(y_test, y_prob))


```

## output
![image](.attachments/12f1908fc3503c092702d7752ac0cac92c695f3a.png) 
```bash
PS C:\A5EV5C\app\templates> py ee.py
Columns in dataset:
 ['balance', 'income', 'age', 'default']
Confusion Matrix:
 [[1 1]
 [0 2]]

Classification Report:
               precision    recall  f1-score   support

           0       1.00      0.50      0.67         2
           1       0.67      1.00      0.80         2

    accuracy                           0.75         4
   macro avg       0.83      0.75      0.73         4
weighted avg       0.83      0.75      0.73         4

ROC AUC Score: 0.75

```