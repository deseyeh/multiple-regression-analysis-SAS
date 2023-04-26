# multiple-regression-analysis-SAS

## Background

Investigating the administrative costs of pension funds, evaluating the size, schemes, administrative complexity of  the funds and Critically  provide recommendation metrics on how to enhance the administrative effectiveness of the pension plans.

![image](https://user-images.githubusercontent.com/100138272/234721488-a2726897-bb3d-4497-97f4-b99832d1eb30.png)

## EXPLORATORY ANALYSIS OF  VARIABLES Y, A1 AND PER2 TO PER 7

We begin with the exploratory analysis of the variables and investigating any missing values 

![image](https://user-images.githubusercontent.com/100138272/234721610-98e04e6f-40e9-40b4-b992-159a597bf156.png)

Table 1.1, shows the mean of the total cost per active member (response variable Y ) to be approximately 28 with a standard deviation of 13. This indicates that there is a relatively large variation in the total cost per active member across different pension funds.

Also, No missing value was identified for each variables.

Based on the histogram in figure 1.1, the distribution of Y appears to near normality with slightly positive skewness. The distribution is assumed unimodal.

![image](https://user-images.githubusercontent.com/100138272/234721780-8089e1c6-cabd-4024-afb6-41c2f748fbc3.png)

## FREQUENCY DISTRIBUTION OF FACTORS C1 TO C8

Then, we deep down to analyze each of the factors, to remove non-significant factor based on frequency 

![image](https://user-images.githubusercontent.com/100138272/234722011-b905743c-3982-4c9d-ad9f-c824cec35e74.png)

From the frequency distribution Table 1.2, there is very large variation in the variable C4 with almost all funds allowing members to pay AVC's, except for 1 fund that is not allowing members to pay AVC's.

As a result, this variable is unlikely to have a significant relationship with Y and may be more appropriate not to include it as an explanatory variable in any regression model for Y. It may not improve the accuracy of the predictions due to its low variability

## INVESTIGATING THE RELATIONSHIP BETWEEN TOTAL COST PER ACTIVE MEMBER AND MEASURES, TURN OVER AND SCHEMES.

To investigate the relationship between the target and the explanatory variables, we plot a scatterplot  and investigate the analysis of variance.
![image](https://user-images.githubusercontent.com/100138272/234722149-73547213-0cf1-4fe2-969c-cf863d22fd98.png)

In the scatterplot of Figure 2.1, the target variable Y generally increases with the explanatory variables. The data seems to be non-linear. They are scattered about the line in much the same way that individual observations are typically widely scattered about their mean.

![image](https://user-images.githubusercontent.com/100138272/234722192-8e745643-ca39-4ebc-9baf-1ed5e4913ad8.png)

In Table 2.1,  F-test is significant with p-value - P0 = 0.0189. Since P0 < 0.05, the obtained result is significant at the 5% level. Also, the R2 58% of the variation is being explained by the model. Hence, the multiple regression is “worthwhile”, and we can continue with the investigation and interpretation of the fitted regression model. 

## TENABILITY OF THE STATISTIC ASSUMPTION OF THE MODEL
![image](https://user-images.githubusercontent.com/100138272/234722379-2a095e62-b5e4-4380-9217-e00793919956.png)

To investigate the tenability, a studentized residuals plot (Figure 2.2) appears to be randomly scattered about a mean value of zero, with approximately constant range (hence variance) across the entire range of fitted values. The plot is therefore consistent with the adequacy of the systematic component of the multiple regression model, and with the assumption of constant variance. (Homoscedasticity)

![image](https://user-images.githubusercontent.com/100138272/234722415-b8c66191-77eb-4d87-a4f2-dc58207f5faf.png)
Figure 2.3, the histogram of studentized Residual which suggests that the residuals normally distributed and unimodal.

![image](https://user-images.githubusercontent.com/100138272/234722470-25a5c015-45b9-4425-bcec-de53fe083cbf.png)

Figure 2.4,  The studentised residuals conform nearly to an approximate straight line of unit slope passing near to the origin on this normal plot. However, there are some irregularities in the plot that can be further investigated. The assumption of the near-normality of the random errors is tenable. 

## In conclusion, to achieve a suitable model, it will be appropriate to further investigate or transform the data to resolve the issues of non-linearity and irregularities on plots. 

## TRANSFORMATION OF THE INITIAL MODEL, USING LOG 

LY = Log(Y), LA1 = Log(A1),  LPer2 = Log(LPer2),  … , LPer7 = Log(LPer7)

We proceed to transform the initial model to resolve the apparent non-linearity seen in the relationship between the target variable and the explanatory variable. 

However;
It is not necessary to transform the values of factors C1 to C3 and C5 to C8 in this regression model because these variables are categorical variables. 

Indicators or dummy variables are used to create a separate variable for each category and assigned a value of 1 or 0 to indicate the presence or absence of that category. 

These variables do not require transformation because they are not measured on a continuous scale and do not violate statistical assumptions.

Categorical variables are not subject to the same statistical assumptions as continuous variables, such as normality, linearity, and homoscedasticity, which may require transformations.

## FITTING THE TRANSFORMED MODEL

![image](https://user-images.githubusercontent.com/100138272/234722886-ac42e908-6cd2-487b-8235-d679cfca64b3.png)

The scattered plot of the transformed model can be seen on figure 3.1 which looks straighter than the previous model with data evenly scatter along the straight line.

![image](https://user-images.githubusercontent.com/100138272/234722940-2c85a647-1da5-4745-8981-4ab3b0029fb9.png)

In Table 3.1, Now the F tests are even more significant since the p-value are much smaller at p0 = < .0.001. R2 has shot up to 78%, which is very high indeed. 

This is sufficiently high to indicate that the multiple regression model may prove useful in estimating or predicting PFARG’s total cost per active member, LY with the transformed variables.

Hence, the multiple regression is “worthwhile”, and we can continue with the investigation and interpretation of the fitted regression model. 

## TENABILITY OF THE STATISTIC ASSUMPTION OF THE MODEL

![image](https://user-images.githubusercontent.com/100138272/234723054-3315c98d-275f-40d3-a9bf-aee6e08d79a6.png)

To investigate the tenability, a studentized residuals plot (Figure 3.2) appears to be randomly scattered about a mean value of zero, with approximately constant range (hence variance) across the entire range of fitted values. The plot is therefore consistent with the adequacy of the systematic component of the multiple regression model, and with the assumption of constant variance. (Homoscedasticity)

![image](https://user-images.githubusercontent.com/100138272/234723145-ef317592-670a-42e0-855b-cf954fafc873.png)

From Figure 3.3, the histogram suggests that the residuals is approximately bell-shaped, and we can assume the distribution is relatively symmetrical

![image](https://user-images.githubusercontent.com/100138272/234723250-4a8180c7-8179-47cf-b467-ea0668e813e0.png)

Figure 3.4,  The studentized residuals appear to be randomly scattered about a mean value of zero, with approximately constant range (hence variance) across the range of fitted values. The plot is therefore consistent with the adequacy of the systematic component of the multiple regression model, and this suggests that the linear regression model is appropriate for the data.

![image](https://user-images.githubusercontent.com/100138272/234723321-e0441229-c039-4d8c-ad0d-799aae46b92c.png)

From Table 3.2  We can conclude that there is  significant different between the initially fitted model and the model upon Transformed with Log. The Transformed model is a better fit compared to the initial model. However, to achieve a best model we will proceed to reduce the model to a parsimonious model . 

## MODEL SELECTION TO ACHIEVE BEST FIT ON TRANSFORMED MODEL

Approaches based on considering all possible models are impractical in removing unnecessary variables in this instance because there are many potential explanatory variables and the number of possible models will be 2k – 1, where k is the total number of potential variable. In this instance where K = 14 potential explanatory variable, this will generate over 16,000 possible models. This approach is only practicable with modest number of potential explanatory variables.

To achieve a best fit model for this investigation, we employ the backward elimination mode of selection. 

![image](https://user-images.githubusercontent.com/100138272/234723716-22dd6f8d-ed82-40a7-8a0d-47412a79e30e.png)

![image](https://user-images.githubusercontent.com/100138272/234723738-f6def90c-5ab0-4e49-8d00-63543c18326c.png)

Nine explanatory variables were removed in the following sequence LPer7, LPer6, C8, C7, LPer4, LPer5, C5, C6, C3 which all were non-significant at p-value > 0.05 (5%) at each model. It is important to note that when C3 was removed it had a very marginally non-significant p-value of 0.1075. 

From all ten models fitted, we note from the output the number of explanatory variable k (just the model degrees of freedom) and the corresponding error mean square S2. These were as follows:

![image](https://user-images.githubusercontent.com/100138272/234723778-bb2e9319-9ee1-4693-8a29-201816f5acc0.png)

The error mean square remains stable (at around 0.08) for all the models fitted. When the model is reduced to only k = 5 explanatory variable, S2 increases slightly, but there is no clear jump in values. The final model with k = 5 explanatory variables is not marked poorer than the preceding models, despite the exclusion of the marginally non-significant variable C3. Additionally, all the remaining variables in the final model had a p-value of less than 0.05, indicating that they are significantly related to the response variable. Also, k =5 remains the most parsimonious model to choose. 

## Final Model

The final model will describe and predict the Logged target variable LY (Total cost per active member with the Logged explanatory variables, LA1, C1, C2, LPer2 and LPer3.

E(Ly) = b0 + b1C11 + b1C12 + b1C13 + b2C2 + b3LA1 + b4LPer2 + b5LPer3

E(Ly) = 7.707 – 0.936C11– 0.471C12 - 0.349C13 - 0.368C2 – 0.467LA1 – 0.226LPer2 + 0.328LPer3

Where LY is the natural logarithm of the total cost per active member.

![image](https://user-images.githubusercontent.com/100138272/234724090-38c7cfa2-dcf4-495e-9576-2dead0cf7ba5.png)

## PARAMETER ESTIMATES 

![image](https://user-images.githubusercontent.com/100138272/234724352-17a3a9f7-3579-4d33-9db8-4a623dc97e9b.png)

E(Ly) = b0 + b1C11 + b1C12 + b1C13 + b2C2 + b3LA1 + b4LPer2 + b5LPer3
E(Ly) = 7.707 – 0.936C11– 0.471C12 - 0.349C13 - 0.368C2 – 0.467LA1 – 0.226LPer2 + 0.328LPer3

Where LY is the natural logarithm of the total cost per active member.

The Model's Parameter estimates suggest that :

The total cost per active member will decrease by 0.936 value of Fund type been staff only (C1_1)

For every change in Fund type as Combined scheme, same scales the total cost per active member will decrease by 0.471 (C1_2)

for every change in Fund type as separate scheme, the total cost per active member will decrease by 0.349 (C1_3)

For every change in Fund type as Combined scheme, different scales the total cost per active member will neither decrease nor increase (C1_4)

For every change in whether scheme is contracted out or not, the total cost per active member will decrease by 0.368 (C2)

For every change in the number of active member, the total cost per active member will decrease by 0.467 (LA1)

For every change in the number of deferred pensioners per active member the total cost per active member will decrease by 0.226 (LPer2)

The total cost per active member will increase by 0.328 value of the number of pensioners per active member (LPer3)

## FITTING THE FINAL MODEL 

![image](https://user-images.githubusercontent.com/100138272/234725133-99c1321e-6041-4877-8e6d-fd5081c661eb.png)

![image](https://user-images.githubusercontent.com/100138272/234725143-08adfad2-36e3-44d3-8829-f9fe0d3fe3d9.png)

We proceed to fit the transformed model and analyzing using appropriate plots and investigate the tenability of the assumption

The data remains randomly scattered around a straight line.

The F test remains significant since the p-value are much smaller at p0 = < .0001). The R2 also at 72% which is high and shows that the model is worthwhile. This indicates that the final model will be useful to estimate or predict PFARG’s total cost per active member, LY with the transformed variables.

We will also plot appropriate plots to investigate the fit of our final model.

## TENABILITY OF THE STATISTIC ASSUMPTION OF THE MODEL

![image](https://user-images.githubusercontent.com/100138272/234725202-9d01ca3d-cd0d-41fd-9023-3874f0b2a2f6.png)

The Studentized residuals appear to be randomly scattered about a mean value of zero, with approximately constant range (hence variance) across the entire range of fitted values. The plot is therefore consistent with the adequacy of the systematic component of the multiple regression model. Therefore, the plot suggests that the assumption of constant variance (homoscedasticity) is reasonable.

![image](https://user-images.githubusercontent.com/100138272/234725352-ea946a9b-b648-4fdd-b87b-2357b813d19f.png)

The studentized residual appears to be reasonably randomly scattered about a mean value of zero, with approximately constant range (hence variance) across the entire range of values of the transformed explanatory variable LA1. The plot is therefore consistent with the adequacy of the assumption of a linear association between the transformed response LY and LA1 (and with assumption of constant variance)

![image](https://user-images.githubusercontent.com/100138272/234725434-1a15b70b-cf31-4784-8024-12b83d6d576b.png)

The studentized residual appears to be reasonably randomly scattered about a mean value of zero, with approximately constant range (hence variance) across the entire range of values of the transformed explanatory variable LPer2. The plot is therefore consistent with the adequacy of the assumption of a linear association between the transformed response LY and LPer2 (and with assumption of constant variance)

![image](https://user-images.githubusercontent.com/100138272/234725499-5fa7c8e5-a63f-40d4-9348-9a49e8b91371.png)

The studentized residual appears to be reasonably randomly scattered about a mean value of zero, with approximately constant range (hence variance) across the entire range of values of the transformed explanatory variable LPer3. The plot is therefore consistent with the adequacy of the assumption of a linear association between the transformed response LY and LPer3 (and with assumption of constant variance).

![image](https://user-images.githubusercontent.com/100138272/234725533-8eaca814-f652-4585-9ed5-30e81ff27022.png)

Based on the Histogram, there is a suggestion that the residual is approximately bell-shaped, and we can assume the distribution appears to be relatively near symmetrical (Normally distributed) and unimodal

![image](https://user-images.githubusercontent.com/100138272/234725573-75ffbd37-7677-4c19-98b5-90891741ae47.png)

From the above plot, the studentized residuals indeed conform nearer to an approximate straight line of unit slope passing near to the origin on this normal. Also, plot shows that the residuals follow the line closely, suggesting that the normality assumption of the random errors  is tenable.

## OUTLIERS

From the previous studentized residual plot, normal probability plot, there is clearly no identified outlier. However, We investigate further for any potential outliers and potential influential by investigating the deleted residuals: an overlaid scatter diagram of the studentized and deleted residual against the fitted values (Figure 6.1 ) below

![image](https://user-images.githubusercontent.com/100138272/234725715-4f74865c-c9ff-41b0-a7da-226ff5ad76b9.png)

It is very clear from figure 6.1 that for most of the observations, the studentized and deleted residual coincide almost perfectly, so are almost perfectly superimposed on the plot. Only 1 shows a small degree of separation with the deleted residual a bit far than its studentized residual. To confirm further, we simply identify any observation with an extreme deleted residual (one with an absolute value in excess of 2).

![image](https://user-images.githubusercontent.com/100138272/234725743-a2e82490-220a-4a4f-a0d0-aedd4c8f22a1.png)

The two observations in Table 6.1, have extreme deleted residuals and barely exceeds 2 and below 3, so is only just large enough to be considered extreme and likely to have occurred by chance.

## To further investigate the potential outlier, we will investigate the potential influential point for the multiple regression:

We check the weight of the residual to identify any possibility of outlier with the DFFITS

n = 45 observations, with k = 7 explanatory variables (LA1, C1_1, C1_2, C1_3, C2, LPer2, Lper3) , 
Hence p = 7 + 1 = 8 parameters in our multiple regression model. 

![image](https://user-images.githubusercontent.com/100138272/234725856-e649712d-534c-43fd-9dba-2d051a225410.png)

An absolute DFFITS value of 2 or more would be convincing evidence of an influential point, but further consideration should also be given to observations with an absolute DFFITS value of 0.730 or more.

![image](https://user-images.githubusercontent.com/100138272/234725933-e58e837d-934b-40af-b6c2-3148e8e740be.png)

Figure 6.2 is a Pareto graph of the absolute DFFITS values that clearly shows only the two leftmost points on the graph stand out. However, the leftmost 6 points all have an absolute DFFITS value above the size-related cut-off, although no value exceeds the overall cut-off of 2. We have only marginal evidence that these 6 points may be influential. 
We further investigate all 6 of these observations in Table 6.2.

![image](https://user-images.githubusercontent.com/100138272/234725980-86e92550-47bc-47b3-be38-18d1d93fad11.png)

![image](https://user-images.githubusercontent.com/100138272/234726038-fac94449-2e52-4697-b99c-f5313fba0e03.png)

Figure 6.2 is a Pareto graph of the absolute DFFITS values that clearly shows only the two leftmost points on the graph stand out. However, the leftmost 6 points all have an absolute DFFITS value above the size-related cut-off, although no value exceeds the overall cut-off of 2. We have only marginal evidence that these 6 points may be influential. 

We further investigate all 6 of these observations in Table 6.2.
 
Table 6.2 reveals the identity of the 6 potential influential point. 

Looking at their data points location on scattered diagram FIGURE 5.1 of observed against predicted values will be, Neither of these points appears to be any great distance from the reference line. This again suggests that we have only marginal evidence that the points may, in fact, be influential.
![image](https://user-images.githubusercontent.com/100138272/234726103-f06b5fe3-83c0-45c7-b4b2-3299d9bbe364.png)

![image](https://user-images.githubusercontent.com/100138272/234726130-ce33cff3-ecd5-4478-b82e-d72d4b4e62eb.png)

Next, we also investigate the DFBETAS to detect parameter estimate that may be affected by the influential point.
The sample-size related cut-off for DFBETAS is:






