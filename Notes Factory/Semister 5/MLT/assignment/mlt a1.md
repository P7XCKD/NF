### Q1. Calculate the correlation coefficient from the following table and find out the relationship between variables.

> **Karl Pearson's correlation coefficient** is a measure of the linear relationship between two continuous variables. The formula is:
> $$r = \frac{n(\sum xy) - (\sum x)(\sum y)}{\sqrt{[n\sum x^2 - (\sum x)^2][n\sum y^2 - (\sum y)^2]}}$$
> Where:
> - **n** is the number of data points.
> - **$\sum xy$** is the sum of the product of paired scores.
> - **$\sum x$** is the sum of x scores.
> - **$\sum y$** is the sum of y scores.
> - **$\sum x^2$** is the sum of squared x scores.
> - **$\sum y^2$** is the sum of squared y scores.

**Step 1: Create a calculation table**
[span_0](start_span)Here is the data provided and the necessary calculations for the formula[span_0](end_span).

| Subject | Age (X) | Glucose Level (Y) | $x^2$ | $y^2$ | $xy$ |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 42 | 98 | 1764 | 9604 | 4116 |
| 2 | 23 | 68 | 529 | 4624 | 1564 |
| 3 | 22 | 73 | 484 | 5329 | 1606 |
| 4 | 47 | 79 | 2209 | 6241 | 3713 |
| 5 | 50 | 88 | 2500 | 7744 | 4400 |
| 6 | 60 | 82 | 3600 | 6724 | 4920 |
| **Sum** | **$\sum x = 244$** | **$\sum y = 488$** | **$\sum x^2 = 11086$** | **$\sum y^2 = 40266$** | **$\sum xy = 20319$** |

**Step 2: Substitute the summed values into the formula**
Given $n=6$:

* **Numerator:** $n(\sum xy) - (\sum x)(\sum y) = 6(20319) - (244)(488) = 121914 - 119072 = 2842$
* **Denominator (Part 1):** $n\sum x^2 - (\sum x)^2 = 6(11086) - (244)^2 = 66516 - 59536 = 6980$
* **Denominator (Part 2):** $n\sum y^2 - (\sum y)^2 = 6(40266) - (488)^2 = 241596 - 238144 = 3452$
* **Full Denominator:** $\sqrt{6980 \times 3452} = \sqrt{24094960} \approx 4908.66$

**Step 3: Calculate the correlation coefficient (r)**
$$r = \frac{2842}{4908.66} \approx 0.579$$

**Conclusion**
The correlation coefficient **r** is approximately **0.58**. This value indicates a **moderate positive linear relationship** between Age (X) and Glucose Level (Y). As age increases, the glucose level tends to increase as well.

***

### Q2. For the craft item data, find MAE, MSE, and RMSE.

> These are metrics used to evaluate the performance of a regression model.
> - **Mean Absolute Error (MAE):** The average of the absolute differences between the predicted and actual values. It gives an idea of the magnitude of the error but not the direction.
> - **Mean Squared Error (MSE):** The average of the squared differences between the predicted and actual values. It penalizes larger errors more than smaller ones.
> - **Root Mean Squared Error (RMSE):** The square root of the MSE. It is in the same units as the target variable, making it more interpretable.

**Step 1: Create a calculation table**
[span_1](start_span)Using the provided actual and predicted prices[span_1](end_span):

| Craft Item | Actual Price ($y_i$) | Predicted Price ($\hat{y}_i$) | Error ($e_i = y_i - \hat{y}_i$) | Absolute Error ($|e_i|$) | Squared Error ($e_i^2$) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Necklace | 25 | 28 | -3 | 3 | 9 |
| Bracelet | 15 | 14 | 1 | 1 | 1 |
| Earrings | 20 | 22 | -2 | 2 | 4 |
| Ring | 30 | 29 | 1 | 1 | 1 |
| Brooch | 40 | 38 | 2 | 2 | 4 |
| **Sum** | | | | **$\sum |e_i| = 9$** | **$\sum e_i^2 = 19$** |

**Step 2: Calculate the metrics**
Given the number of items $n=5$:

* **Mean Absolute Error (MAE)**
    $$MAE = \frac{1}{n} \sum |e_i| = \frac{9}{5} = 1.8$$

* **Mean Squared Error (MSE)**
    $$MSE = \frac{1}{n} \sum e_i^2 = \frac{19}{5} = 3.8$$

* **Root Mean Squared Error (RMSE)**
    $$RMSE = \sqrt{MSE} = \sqrt{3.8} \approx 1.949$$

> [!abstract]
> **Final Metrics**
> - **MAE:** $1.8$
> - **MSE:** $3.8$
> - **RMSE:** $1.949$

***

### Q3. Apply the linear regression technique to predict 7th and 12th-week sales.

> **Simple Linear Regression** is a statistical method that allows us to summarize and study relationships between two continuous variables. The goal is to find a line of best fit, represented by the equation $y = a + bx$.
>
> The coefficients are calculated as:
> - **Slope (b):** $b = \frac{n(\sum xy) - (\sum x)(\sum y)}{n(\sum x^2) - (\sum x)^2}$
> - **Intercept (a):** $a = \bar{y} - b\bar{x}$

**Step 1: Create a calculation table**
[span_2](start_span)Using the sales data provided[span_2](end_span):

| Week (x) | Sales in Thousands (y) | $x^2$ | $xy$ |
| :--- | :--- | :--- | :--- |
| 1 | 1.2 | 1 | 1.2 |
| 2 | 1.8 | 4 | 3.6 |
| 3 | 2.6 | 9 | 7.8 |
| 4 | 3.2 | 16 | 12.8 |
| 5 | 3.8 | 25 | 19.0 |
| **$\sum x=15$** | **$\sum y=12.6$** | **$\sum x^2=55$** | **$\sum xy=44.4$** |

**Step 2: Calculate the slope (b)**
Given $n=5$:
$$b = \frac{5(44.4) - (15)(12.6)}{5(55) - (15)^2} = \frac{222 - 189}{275 - 225} = \frac{33}{50} = 0.66$$

**Step 3: Calculate the intercept (a)**
First, find the means of x and y:
* $\bar{x} = \frac{\sum x}{n} = \frac{15}{5} = 3$
* $\bar{y} = \frac{\sum y}{n} = \frac{12.6}{5} = 2.52$

Now, calculate 'a':
$$a = 2.52 - (0.66)(3) = 2.52 - 1.98 = 0.54$$

**Step 4: Form the regression equation and make predictions**
The line of best fit is: **$y = 0.54 + 0.66x$**

* **Prediction for 7th week (x=7):**
    $y = 0.54 + 0.66(7) = 0.54 + 4.62 = 5.16$
    The predicted sales for the 7th week are **5.16 thousands**.

* **Prediction for 12th week (x=12):**
    $y = 0.54 + 0.66(12) = 0.54 + 7.92 = 8.46$
    The predicted sales for the 12th week are **8.46 thousands**.

***

### Q4. Using the equation y = -5.8x + 1320, find how many people will attend the concert if the ticket price is $25.

> [span_3](start_span)The problem requires substituting a given value of 'x' (ticket price) into the provided linear regression equation to find the corresponding 'y' value (number of people attending)[span_3](end_span).

**Step 1: Identify the equation and variables**
* **[span_4](start_span)Equation:** $y = -5.8x + 1320$[span_4](end_span)
* **[span_5](start_span)Variable x (Ticket Price):** $25[span_5](end_span)

**Step 2: Substitute the value of x into the equation**
$$y = -5.8(25) + 1320$$

**Step 3: Calculate the result**
$$y = -145 + 1320$$
$$y = 1175$$

**Conclusion**
If the ticket price is $25, **1175 people** are predicted to attend the concert.

***

### Q5. Using the equation y = -2.1x + 1220, find how many people will buy candy if the price is $10.

> [span_6](start_span)This problem requires substituting the given candy price ('x') into the provided equation to predict the number of people who will buy candy ('y')[span_6](end_span).

**Step 1: Identify the equation and variables**
* **[span_7](start_span)Equation:** $y = -2.1x + 1220$[span_7](end_span)
* **[span_8](start_span)Variable x (Candy Price):** $10[span_8](end_span)

**Step 2: Substitute the value of x into the equation**
$$y = -2.1(10) + 1220$$

**Step 3: Calculate the result**
$$y = -21 + 1220$$
$$y = 1199$$

**Conclusion**
If the price of candy is $10, **1199 people** are predicted to buy candy.

***

### Q6. Find the linear regression equation for the following two sets of data.

> To find the linear regression equation ($y = a + bx$), we need to calculate the slope (b) and the y-intercept (a) using the same formulas as in Question 3.

**Step 1: Create a calculation table**
[span_9](start_span)Using the data provided[span_9](end_span):

| x | y | $x^2$ | $xy$ |
| :--- | :--- | :--- | :--- |
| 2 | 3 | 4 | 6 |
| 4 | 7 | 16 | 28 |
| 6 | 5 | 36 | 30 |
| 8 | 10 | 64 | 80 |
| **$\sum x=20$** | **$\sum y=25$** | **$\sum x^2=120$** | **$\sum xy=144$** |

**Step 2: Calculate the slope (b)**
Given $n=4$:
$$b = \frac{n(\sum xy) - (\sum x)(\sum y)}{n(\sum x^2) - (\sum x)^2} = \frac{4(144) - (20)(25)}{4(120) - (20)^2} = \frac{576 - 500}{480 - 400} = \frac{76}{80} = 0.95$$

**Step 3: Calculate the intercept (a)**
First, find the means of x and y:
* $\bar{x} = \frac{\sum x}{n} = \frac{20}{4} = 5$
* $\bar{y} = \frac{\sum y}{n} = \frac{25}{4} = 6.25$

Now, calculate 'a':
$$a = \bar{y} - b\bar{x} = 6.25 - (0.95)(5) = 6.25 - 4.75 = 1.5$$

**Conclusion**
The linear regression equation for the given data is:
$$y = 1.5 + 0.95x$$
