## code
```python
import warnings
from sklearn.exceptions import UndefinedMetricWarning
warnings.filterwarnings("ignore", category=UndefinedMetricWarning)

import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score, classification_report

df = pd.read_csv('e.csv')

print("First 5 rows:")
print(df.head())

df['price_category'] = pd.qcut(df['price'], q=3, labels=['low', 'medium', 'high'])

features = ['carat', 'cut', 'color']
target = 'price_category'

df_encoded = pd.get_dummies(df[features], columns=['cut', 'color'], drop_first=True)

X = df_encoded
y = df[target]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

gnb = GaussianNB()
gnb.fit(X_train, y_train)
y_pred = gnb.predict(X_test)

accuracy = accuracy_score(y_test, y_pred)
report = classification_report(y_test, y_pred)

print(f"\nAccuracy: {accuracy:.2f}")
print("Classification Report:")
print(report)


```
## output
![image](.attachments/9ebeb29ccbee9d16c8291411507e132256a7706c.png) 

```bash

PS C:\A5EV5C\app\templates> python ee.py
First 5 rows:
   carat      cut color  price
0   0.23    Ideal     E    326
1   0.21  Premium     E    326
2   0.23     Good     E    327
3   0.29  Premium     I    334
4   0.31     Good     J    335

Accuracy: 0.67
Classification Report:
              precision    recall  f1-score   support

        high       0.00      0.00      0.00         1
         low       0.50      1.00      0.67         1
      medium       1.00      1.00      1.00         1

    accuracy                           0.67         3
   macro avg       0.50      0.67      0.56         3
weighted avg       0.50      0.67      0.56         3


```