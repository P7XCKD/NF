```python
import pandas as pd
import numpy as np

data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Eva', 'Frank'],
    'Age': [25, 30, 35, np.nan, 28, 40],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston', np.nan, 'Phoenix'],
    'Salary': [70000, 80000, 120000, 90000, 75000, 110000]
}

df = pd.DataFrame(data)
print("Original DataFrame:", df, "\n")
print("head\n", df.head(), "\n")
print("tail\n", df.tail(), "\n")
print("Select 'Age' column:\n", df['Age'], "\n")
print("Row at index 4:\n", df.iloc[4], "\n")
filtered_df = df[df['Age'] > 30]
print("Filtered rows where Age > 30:\n", filtered_df, "\n")

df['Experience'] = [2, 5, 7, 3, 4, 10]
print("After adding 'Experience' column:\n", df, "\n")

df['Salary'] *= 1.10
print("After increasing Salary by 10%:\n", df, "\n")

df = df.drop('City', axis=1)
print("After removing 'City' column:\n", df, "\n")
print("Missing values in each column:\n", df.isnull().sum(), "\n")

df['Age'] = df['Age'].fillna(30)
print("After filling missing Age values with 30:\n", df, "\n")

df.loc[1, 'Experience'] = np.nan
print("DataFrame before dropping rows with missing Experience:\n", df, "\n")

df_dropped = df.dropna()
print("After dropping rows with missing data:\n", df_dropped, "\n")

df['Experience'] = df['Experience'].fillna(df['Experience'].mean())
print("After filling missing Experience with mean:\n", df)

```
***

### output


```
Original DataFrame:
   Name     Age         City   Salary
0  Alice   25.0     New York   70000
1    Bob   30.0  Los Angeles   80000
2 Charlie   35.0      Chicago  120000
3  David    NaN      Houston   90000
4    Eva   28.0          NaN   75000
5  Frank   40.0      Phoenix  110000

Head:
   Name     Age         City  Salary
0  Alice   25.0     New York   70000
1    Bob   30.0  Los Angeles   80000
2 Charlie   35.0      Chicago 120000

Tail:
3  David    NaN      Houston   90000
4    Eva   28.0          NaN   75000
5  Frank   40.0      Phoenix  110000

Select 'Age' column:
[25.0, 30.0, 35.0, nan, 28.0, 40.0]

Row at index 4:
{'Name': 'Eva', 'Age': 28.0, 'City': nan, 'Salary': 75000}

Filtered rows where Age > 30:
   Name     Age     City   Salary
2 Charlie  35.0  Chicago  120000
5  Frank   40.0  Phoenix  110000

After adding 'Experience' column:
   Name  Experience
0  Alice           2
1    Bob           5
2 Charlie          7
3  David           3
4    Eva           4
5  Frank          10

After increasing Salary by 10%:
   Name   Salary
0  Alice   77000.0
1    Bob   88000.0
2 Charlie 132000.0
3  David   99000.0
4    Eva   82500.0
5  Frank  121000.0

After removing 'City' column:
   Name   Age   Salary  Experience
0  Alice  25.0  77000.0          2
1    Bob  30.0  88000.0          5
2 Charlie 35.0 132000.0          7
3  David  NaN   99000.0          3
4    Eva  28.0  82500.0          4
5  Frank  40.0 121000.0         10

Missing values per column:
Name: 0, Age: 1, Salary: 0, Experience: 0

After filling missing Age with 30:
   Name   Age   Salary  Experience
0  Alice  25.0  77000.0          2
1    Bob  30.0  88000.0          5
2 Charlie 35.0 132000.0          7
3  David  30.0  99000.0          3
4    Eva  28.0  82500.0          4
5  Frank  40.0 121000.0         10

Before dropping rows with missing Experience:
   Name   Age   Salary  Experience
0  Alice  25.0  77000.0        2.0
1    Bob  30.0  88000.0        NaN
2 Charlie 35.0 132000.0        7.0
3  David  30.0  99000.0        3.0
4    Eva  28.0  82500.0        4.0
5  Frank  40.0 121000.0       10.0

After dropping rows with missing data:
   Name   Age   Salary  Experience
0  Alice  25.0  77000.0        2.0
2 Charlie 35.0 132000.0        7.0
3  David  30.0  99000.0        3.0
4    Eva  28.0  82500.0        4.0
5  Frank  40.0 121000.0       10.0

After filling missing Experience with mean:
   Name   Age   Salary  Experience
0  Alice  25.0  77000.0        2.0
1    Bob  30.0  88000.0        5.2
2 Charlie 35.0 132000.0        7.0
3  David  30.0  99000.0        3.0
4    Eva  28.0  82500.0        4.0
5  Frank  40.0 121000.0       10.0
```