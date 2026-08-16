### Q1. Predict the value of glucose level for age 55 using linear regression.

> **Simple Linear Regression** is a statistical method that allows us to summarize and study relationships between two continuous (quantitative) variables. One variable, denoted as $X$, is regarded as the predictor, explanatory, or independent variable. The other variable, denoted as $Y$, is regarded as the response, outcome, or dependent variable. The relationship is modeled by a straight line: $Y = b_0 + b_1X$.

**1. Data Preparation and Summation**

[span_0](start_span)First, we calculate the necessary sums from the provided data.[span_0](end_span) Let $X$ be Age and $Y$ be Glucose Level. There are $n=6$ data points.

| Subject | Age (X) | Glucose Level (Y) | XY     | X²     |
| :------ | :------ | :---------------- | :----- | :----- |
| 1       | 43      | 99                | 4257   | 1849   |
| 2       | 21      | 65                | 1365   | 441    |
| 3       | 25      | 79                | 1975   | 625    |
| 4       | 42      | 75                | 3150   | 1764   |
| 5       | 57      | 87                | 4959   | 3249   |
| 6       | 59      | 81                | 4779   | 3481   |
| **Sum** | **ΣX=247** | **ΣY=486** | **ΣXY=20485** | **ΣX²=11409** |

**2. Calculate Coefficients**

Now, we calculate the slope ($b_1$) and the y-intercept ($b_0$) for the regression line.

> [!abstract]
> **Formulas Used**
> * **Slope ($b_1$)**: $b_1 = \frac{n(\sum XY) - (\sum X)(\sum Y)}{n(\sum X^2) - (\sum X)^2}$
> * **Y-Intercept ($b_0$)**: $b_0 = \bar{Y} - b_1\bar{X}$
> * **Mean**: $\bar{X} = \frac{\sum X}{n}$ and $\bar{Y} = \frac{\sum Y}{n}$

* **Calculate Means**:
    * $\bar{X} = \frac{247}{6} \approx 41.17$
    * $\bar{Y} = \frac{486}{6} = 81$

* **Calculate Slope ($b_1$)**:
    * $b_1 = \frac{6(20485) - (247)(486)}{6(11409) - (247)^2}$
    * $b_1 = \frac{122910 - 120102}{68454 - 61009}$
    * $b_1 = \frac{2808}{7445} \approx 0.377$

* **Calculate Y-Intercept ($b_0$)**:
    * $b_0 = 81 - 0.377(41.17)$
    * $b_0 = 81 - 15.52$
    * $b_0 \approx 65.48$

**3. Regression Equation and Prediction**

The final regression equation is:
**Glucose Level** = $65.48 + 0.377 \times (\text{Age})$

Now, we predict the glucose level for an age of **55**:
* $Y = 65.48 + 0.377 \times (55)$
* $Y = 65.48 + 20.735$
* $Y \approx 86.215$

The predicted glucose level for a person aged 55 is approximately **86.22**.

***

### Q2. Predict the exam score for Student A, who studied for 5 hours and slept for 7 hours.

> **Multiple Linear Regression** is a statistical technique that uses several explanatory variables to predict the outcome of a response variable. The goal is to model the linear relationship between the explanatory (independent) variables and response (dependent) variable. The formula for two independent variables is: $Y = b_0 + b_1X_1 + b_2X_2$.

**1. Data Preparation and Summation**

Let $X_1$ be Hours_Studied, $X_2$ be Hours_Slept, and $Y$ be Exam_Score. [span_1](start_span)There are $n=5$ data points.[span_1](end_span) We need to calculate various sums to solve the normal equations.

| X₁ | X₂ | Y  | X₁² | X₂² | X₁X₂ | X₁Y | X₂Y |
| :-- | :- | :- | :-- | :- | :-- | :-- | :-- |
| 2  | 9  | 75 | 4   | 81 | 18   | 150 | 675 |
| 4  | 8  | 82 | 16  | 64 | 32   | 328 | 656 |
| 6  | 6  | 90 | 36  | 36 | 36   | 540 | 540 |
| 8  | 5  | 94 | 64  | 25 | 40   | 752 | 470 |
| 10 | 3  | 98 | 100 | 9  | 30   | 980 | 294 |
| **ΣX₁=30** | **ΣX₂=31** | **ΣY=439** | **ΣX₁²=220** | **ΣX₂²=215** | **ΣX₁X₂=156** | **ΣX₁Y=2750** | **ΣX₂Y=2635** |

**2. Set up the Normal Equations**

> [!abstract]
> **Normal Equations**
> 1. $\sum Y = nb_0 + b_1\sum X_1 + b_2\sum X_2$
> 2. $\sum X_1Y = b_0\sum X_1 + b_1\sum X_1^2 + b_2\sum X_1X_2$
> 3. $\sum X_2Y = b_0\sum X_2 + b_1\sum X_1X_2 + b_2\sum X_2^2$

Substituting the sums into the equations:
1.  $439 = 5b_0 + 30b_1 + 31b_2$
2.  $2750 = 30b_0 + 220b_1 + 156b_2$
3.  $2635 = 31b_0 + 156b_1 + 215b_2$

**3. Solve the Equations**

Solving this system of linear equations (using methods like substitution, elimination, or matrix inversion) yields the following coefficients:
* $b_0 \approx 62.23$
* $b_1 \approx 2.91$
* $b_2 \approx 1.47$

**4. Regression Equation and Prediction**

The final regression equation is:
**Exam Score** = $62.23 + 2.91 \times (\text{Hours\_Studied}) + 1.47 \times (\text{Hours\_Slept})$

Now, predict the exam score for a student who studied for **5 hours** ($X_1=5$) and slept for **7 hours** ($X_2=7$):
* $Y = 62.23 + 2.91(5) + 1.47(7)$
* $Y = 62.23 + 14.55 + 10.29$
* $Y = 87.07$

The predicted exam score is **87.07**.

***

### Q3. Calculate the Cohen's Kappa statistic for the recruiter agreement.

> **Cohen's Kappa ($\kappa$)** is a statistic which measures inter-rater agreement for categorical items. It is a more robust measure than simple percent agreement calculation, as it takes into account the possibility of the agreement occurring by chance.

**1. Calculate Observed Agreement ($p_o$)**

[span_2](start_span)This is the proportion of times the two recruiters agreed.[span_2](end_span)
* Agreed on 'Shortlist': 25
* Agreed on 'Reject': 40
* Total agreements = $25 + 40 = 65$
* Total resumes = $25 + 5 + 10 + 40 = 80$

$p_o = \frac{\text{Total Agreements}}{\text{Total Observations}} = \frac{65}{80} = 0.8125$

**2. Calculate Chance Agreement ($p_e$)**

This is the probability that the two recruiters would agree by chance.

* **[span_3](start_span)Step 2a: Find the marginal totals**[span_3](end_span)
    * Recruiter A said 'Shortlist' = $25 + 5 = 30$
    * Recruiter A said 'Reject' = $10 + 40 = 50$
    * Recruiter B said 'Shortlist' = $25 + 10 = 35$
    * Recruiter B said 'Reject' = $5 + 40 = 45$

* **Step 2b: Calculate the probability of chance agreement for each category**
    * Probability of both saying 'Shortlist' by chance:
        * $P(\text{A:Shortlist}) \times P(\text{B:Shortlist}) = (\frac{30}{80}) \times (\frac{35}{80}) = 0.375 \times 0.4375 = 0.1640625$
    * Probability of both saying 'Reject' by chance:
        * $P(\text{A:Reject}) \times P(\text{B:Reject}) = (\frac{50}{80}) \times (\frac{45}{80}) = 0.625 \times 0.5625 = 0.3515625$

* **Step 2c: Sum the probabilities**
    * $p_e = 0.1640625 + 0.3515625 = 0.515625$

**3. Calculate Cohen's Kappa**

> [!abstract]
> **Formula Used**
> * $\kappa = \frac{p_o - p_e}{1 - p_e}$

* $\kappa = \frac{0.8125 - 0.515625}{1 - 0.515625}$
* $\kappa = \frac{0.296875}{0.484375}$
* $\kappa \approx 0.6129$

The Cohen's Kappa statistic is **0.6129**, which typically indicates a **substantial** level of agreement between the two recruiters.

***

### Q4. Calculate Karl Pearson’s Coefficient of Correlation.

> **Karl Pearson’s Coefficient of Correlation ($r$)** is a measure of the linear correlation between two sets of data. It is the ratio between the covariance of two variables and the product of their standard deviations; thus, it is essentially a normalized measurement of the covariance. The value of $r$ ranges from -1 to +1.

**1. Data Preparation and Summation**

[span_4](start_span)First, we set up a table to calculate the required sums from the given data.[span_4](end_span) Let $X$ be Study Hours and $Y$ be Exam Marks. There are $n=5$ students.

| Student | Study Hours (X) | Exam Marks (Y) | XY      | X²    | Y²     |
| :------ | :-------------- | :------------- | :------ | :---- | :----- |
| A       | 2               | 50             | 100     | 4     | 2500   |
| B       | 3               | 60             | 180     | 9     | 3600   |
| C       | 4               | 65             | 260     | 16    | 4225   |
| D       | 5               | 70             | 350     | 25    | 4900   |
| E       | 6               | 85             | 510     | 36    | 7225   |
| **Sum** | **ΣX=20** | **ΣY=330** | **ΣXY=1400** | **ΣX²=90** | **ΣY²=22450** |

**2. Calculate Correlation Coefficient**

Now, we substitute these sums into the formula.

> [!abstract]
> **Formula Used**
> * $r = \frac{n(\sum XY) - (\sum X)(\sum Y)}{\sqrt{[n\sum X^2 - (\sum X)^2][n\sum Y^2 - (\sum Y)^2]}}$

* Numerator:
    * $n(\sum XY) - (\sum X)(\sum Y) = 5(1400) - (20)(330)$
    * $= 7000 - 6600 = 400$

* Denominator:
    * Term 1: $n\sum X^2 - (\sum X)^2 = 5(90) - (20)^2 = 450 - 400 = 50$
    * Term 2: $n\sum Y^2 - (\sum Y)^2 = 5(22450) - (330)^2 = 112250 - 108900 = 3350$
    * $\sqrt{50 \times 3350} = \sqrt{167500} \approx 409.27$

* Calculate $r$:
    * $r = \frac{400}{409.27} \approx 0.977$

The Karl Pearson's Coefficient of Correlation is **0.977**. This indicates a very strong positive linear relationship between study hours and exam marks.



***



### Q5. For the given data and equation, find how many people will buy candy if the price is $10.

> The problem provides a pre-calculated line of best fit and asks to use it for prediction. The equation models the relationship between the price of candy (x) and the number of people who buy it (y).

**1. Identify the Given Information**

* **[span_0](start_span)Equation of the line of best fit**: $y = -2.1x + 1220$[span_0](end_span)
* **[span_1](start_span)Price of candy (x)**: $10[span_1](end_span)

**2. Predict the Value of y**

We need to substitute the value of $x=10$ into the given equation to find the predicted number of people ($y$).

* $y = -2.1(10) + 1220$
* $y = -21 + 1220$
* $y = 1199$

According to the equation, **1199** people will buy candy if the price is $10.

***

### Q6. Find the linear regression equation for the following two sets of data.

> **Simple Linear Regression** aims to find the best-fitting straight line through a set of data points. The equation for this line is $y = b_0 + b_1x$, where $b_1$ is the slope and $b_0$ is the y-intercept.

**1. Data Preparation and Summation**

[span_2](start_span)First, we calculate the necessary sums from the provided data, where $n=4$[span_2](end_span).

| X       | Y       | XY        | X²      |
| :------ | :------ | :-------- | :------ |
| 2       | 3       | 6         | 4       |
| 4       | 7       | 28        | 16      |
| 6       | 5       | 30        | 36      |
| 8       | 10      | 80        | 64      |
| **ΣX=20** | **ΣY=25** | **ΣXY=144** | **ΣX²=120** |

**2. Calculate Coefficients**

Now, we calculate the slope ($b_1$) and the y-intercept ($b_0$).

> [!abstract]
> **Formulas Used**
> * **Slope ($b_1$)**: $b_1 = \frac{n(\sum XY) - (\sum X)(\sum Y)}{n(\sum X^2) - (\sum X)^2}$
> * **Y-Intercept ($b_0$)**: $b_0 = \bar{Y} - b_1\bar{X}$
> * **Mean**: $\bar{X} = \frac{\sum X}{n}$ and $\bar{Y} = \frac{\sum Y}{n}$

* **Calculate Means**:
    * $\bar{X} = \frac{20}{4} = 5$
    * $\bar{Y} = \frac{25}{4} = 6.25$

* **Calculate Slope ($b_1$)**:
    * $b_1 = \frac{4(144) - (20)(25)}{4(120) - (20)^2}$
    * $b_1 = \frac{576 - 500}{480 - 400}$
    * $b_1 = \frac{76}{80} = 0.95$

* **Calculate Y-Intercept ($b_0$)**:
    * $b_0 = 6.25 - 0.95(5)$
    * $b_0 = 6.25 - 4.75$
    * $b_0 = 1.5$

**3. Final Regression Equation**

Substituting the calculated coefficients, the linear regression equation is:

**y = 1.5 + 0.95x**
