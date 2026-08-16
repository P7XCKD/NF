## code

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import classification_report, accuracy_score
import warnings

warnings.filterwarnings("ignore", category=UserWarning)

df = pd.read_csv('e.csv')

print("First 5 rows of the dataset:")
print(df.head())

df['price_category'] = pd.qcut(df['price'], q=3, labels=['low', 'medium', 'high'])

features = ['carat', 'cut', 'color']
target = 'price_category'

df_encoded = pd.get_dummies(df[features], columns=['cut', 'color'], drop_first=True)

X = df_encoded
y = df[target]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

dtree = DecisionTreeClassifier(random_state=42)
dtree.fit(X_train, y_train)

y_pred = dtree.predict(X_test)

print("\nPredicted classes for test data:")
print(y_pred)

print("\nAccuracy:", accuracy_score(y_test, y_pred))
print("\nClassification Report:\n", classification_report(y_test, y_pred))


```
***
## ouput
![image](.attachments/9ebeb29ccbee9d16c8291411507e132256a7706c.png) 
```python
PS C:\A5EV5C\app\templates> python ee.py
First 5 rows of the dataset:
   carat      cut color  price
0   0.23    Ideal     E    326
1   0.21  Premium     E    326
2   0.23     Good     E    327
3   0.29  Premium     I    334
4   0.31     Good     J    335

Predicted classes for test data:
['low' 'low']

Accuracy: 0.5

Classification Report:
               precision    recall  f1-score   support

        high       0.00      0.00      0.00         1
         low       0.50      1.00      0.67         1

    accuracy                           0.50         2
   macro avg       0.25      0.50      0.33         2
weighted avg       0.25      0.50      0.33         2

```