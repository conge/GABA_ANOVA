ANOVA analysis on the connectivity values for GABA Project
========================================================

Qingyang Li | 2013/05/10 | Qingyang.Li@Childmind.org

Intro
-----  

ANOVA analysis on the connectivity values extracted from significant clusters from the [JAACAP paper](http://linkinghub.elsevier.com/retrieve/pii/S0890856713001937) using the following models:
1. Dx, GABAW, GLXW, GABAW*Dx, GLXW*Dx, Age, Sex, MeanFD, CSF, GM.
2. AnhBC_fMRI, Age, Sex, MeanFD, CSF, GM.

How to Read the resutls:
---------

The results are grouped into for categories based on the significant clusters. The order of clusters are listed at the begenning of the each section of the results. For each cluster, you will see the fomula of the linear regression model and then the beta estimates and the T and P values for each regressor. Then the anova report table will be there to show the ANOVA results.

Let me know if you have any questions.

MDD > CT
-----------

The results were show for the clusters below in following order:  

Seeds / region of the cluster 
* Right DC / dmPFC  
* Left DRP / dmPFC	
* Right DRP / Inferior Frontal Gyrus	
* Right VRP / dmPFC and paracingulate	
* Left NAc / dmPFC	
* Right NAC / dmPFC	
* Left VC / dmPFC	
* Right VC / dmPFC and ACC



```r
input = read.csv("/Users/qingyang.li/Projects/Vilma_Adolescent_MDD_2011/GABA_ANOVA/ANOVA_input_MDDgtCT.csv")
varlist = colnames(input)[3:10]
# models = lapply(varlist, function(x) {lm(substitute(i ~ Diagnosis +
# GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex
# +CSF_PCT+GM_PCT, list(i = as.name(x))), data = input) })

for (i in seq(1:length(varlist))) {
    
    Formula = paste(varlist[1], " ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT")
    model = lm(Formula, data = input)
    model.anova = anova(model)
    print("++++++++ Model +++++++++++++")
    print(Formula)
    print("+++++++ Model Summary ++++++")
    print(summary(model))
    print("+++++++ ANOVA results ++++++")
    print(model.anova)
    print("")
    
}
```

```
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...dmPFC  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.05645 -0.02125 -0.00578  0.01485  0.09254 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)   
## (Intercept)          0.66400    0.21000    3.16   0.0057 **
## DiagnosisMDD         0.10815    0.18310    0.59   0.5625   
## GABAW              -71.50223   42.05139   -1.70   0.1073   
## GLXW                -0.51127   27.90449   -0.02   0.9856   
## AgefMRI             -0.01649    0.00601   -2.74   0.0139 * 
## Sex                  0.02550    0.01912    1.33   0.2000   
## MeanFD               0.23758    0.12785    1.86   0.0805 . 
## CSF_PCT              0.00333    0.00358    0.93   0.3652   
## GM_PCT              -0.00475    0.00224   -2.12   0.0487 * 
## DiagnosisMDD:GLXW   25.55217   38.16016    0.67   0.5121   
## DiagnosisMDD:GABAW -23.83166   65.41413   -0.36   0.7201   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0433 on 17 degrees of freedom
## Multiple R-squared: 0.81,	Adjusted R-squared: 0.699 
## F-statistic: 7.26 on 10 and 17 DF,  p-value: 0.000208 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...dmPFC
##                 Df Sum Sq Mean Sq F value  Pr(>F)    
## Diagnosis        1 0.0946  0.0946   50.49 1.8e-06 ***
## GABAW            1 0.0029  0.0029    1.55  0.2301    
## GLXW             1 0.0015  0.0015    0.81  0.3794    
## AgefMRI          1 0.0172  0.0172    9.17  0.0076 ** 
## Sex              1 0.0011  0.0011    0.60  0.4509    
## MeanFD           1 0.0062  0.0062    3.33  0.0857 .  
## CSF_PCT          1 0.0029  0.0029    1.57  0.2275    
## GM_PCT           1 0.0084  0.0084    4.51  0.0487 *  
## Diagnosis:GLXW   1 0.0008  0.0008    0.43  0.5185    
## Diagnosis:GABAW  1 0.0002  0.0002    0.13  0.7201    
## Residuals       17 0.0318  0.0019                    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...dmPFC  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.05645 -0.02125 -0.00578  0.01485  0.09254 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)   
## (Intercept)          0.66400    0.21000    3.16   0.0057 **
## DiagnosisMDD         0.10815    0.18310    0.59   0.5625   
## GABAW              -71.50223   42.05139   -1.70   0.1073   
## GLXW                -0.51127   27.90449   -0.02   0.9856   
## AgefMRI             -0.01649    0.00601   -2.74   0.0139 * 
## Sex                  0.02550    0.01912    1.33   0.2000   
## MeanFD               0.23758    0.12785    1.86   0.0805 . 
## CSF_PCT              0.00333    0.00358    0.93   0.3652   
## GM_PCT              -0.00475    0.00224   -2.12   0.0487 * 
## DiagnosisMDD:GLXW   25.55217   38.16016    0.67   0.5121   
## DiagnosisMDD:GABAW -23.83166   65.41413   -0.36   0.7201   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0433 on 17 degrees of freedom
## Multiple R-squared: 0.81,	Adjusted R-squared: 0.699 
## F-statistic: 7.26 on 10 and 17 DF,  p-value: 0.000208 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...dmPFC
##                 Df Sum Sq Mean Sq F value  Pr(>F)    
## Diagnosis        1 0.0946  0.0946   50.49 1.8e-06 ***
## GABAW            1 0.0029  0.0029    1.55  0.2301    
## GLXW             1 0.0015  0.0015    0.81  0.3794    
## AgefMRI          1 0.0172  0.0172    9.17  0.0076 ** 
## Sex              1 0.0011  0.0011    0.60  0.4509    
## MeanFD           1 0.0062  0.0062    3.33  0.0857 .  
## CSF_PCT          1 0.0029  0.0029    1.57  0.2275    
## GM_PCT           1 0.0084  0.0084    4.51  0.0487 *  
## Diagnosis:GLXW   1 0.0008  0.0008    0.43  0.5185    
## Diagnosis:GABAW  1 0.0002  0.0002    0.13  0.7201    
## Residuals       17 0.0318  0.0019                    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...dmPFC  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.05645 -0.02125 -0.00578  0.01485  0.09254 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)   
## (Intercept)          0.66400    0.21000    3.16   0.0057 **
## DiagnosisMDD         0.10815    0.18310    0.59   0.5625   
## GABAW              -71.50223   42.05139   -1.70   0.1073   
## GLXW                -0.51127   27.90449   -0.02   0.9856   
## AgefMRI             -0.01649    0.00601   -2.74   0.0139 * 
## Sex                  0.02550    0.01912    1.33   0.2000   
## MeanFD               0.23758    0.12785    1.86   0.0805 . 
## CSF_PCT              0.00333    0.00358    0.93   0.3652   
## GM_PCT              -0.00475    0.00224   -2.12   0.0487 * 
## DiagnosisMDD:GLXW   25.55217   38.16016    0.67   0.5121   
## DiagnosisMDD:GABAW -23.83166   65.41413   -0.36   0.7201   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0433 on 17 degrees of freedom
## Multiple R-squared: 0.81,	Adjusted R-squared: 0.699 
## F-statistic: 7.26 on 10 and 17 DF,  p-value: 0.000208 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...dmPFC
##                 Df Sum Sq Mean Sq F value  Pr(>F)    
## Diagnosis        1 0.0946  0.0946   50.49 1.8e-06 ***
## GABAW            1 0.0029  0.0029    1.55  0.2301    
## GLXW             1 0.0015  0.0015    0.81  0.3794    
## AgefMRI          1 0.0172  0.0172    9.17  0.0076 ** 
## Sex              1 0.0011  0.0011    0.60  0.4509    
## MeanFD           1 0.0062  0.0062    3.33  0.0857 .  
## CSF_PCT          1 0.0029  0.0029    1.57  0.2275    
## GM_PCT           1 0.0084  0.0084    4.51  0.0487 *  
## Diagnosis:GLXW   1 0.0008  0.0008    0.43  0.5185    
## Diagnosis:GABAW  1 0.0002  0.0002    0.13  0.7201    
## Residuals       17 0.0318  0.0019                    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...dmPFC  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.05645 -0.02125 -0.00578  0.01485  0.09254 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)   
## (Intercept)          0.66400    0.21000    3.16   0.0057 **
## DiagnosisMDD         0.10815    0.18310    0.59   0.5625   
## GABAW              -71.50223   42.05139   -1.70   0.1073   
## GLXW                -0.51127   27.90449   -0.02   0.9856   
## AgefMRI             -0.01649    0.00601   -2.74   0.0139 * 
## Sex                  0.02550    0.01912    1.33   0.2000   
## MeanFD               0.23758    0.12785    1.86   0.0805 . 
## CSF_PCT              0.00333    0.00358    0.93   0.3652   
## GM_PCT              -0.00475    0.00224   -2.12   0.0487 * 
## DiagnosisMDD:GLXW   25.55217   38.16016    0.67   0.5121   
## DiagnosisMDD:GABAW -23.83166   65.41413   -0.36   0.7201   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0433 on 17 degrees of freedom
## Multiple R-squared: 0.81,	Adjusted R-squared: 0.699 
## F-statistic: 7.26 on 10 and 17 DF,  p-value: 0.000208 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...dmPFC
##                 Df Sum Sq Mean Sq F value  Pr(>F)    
## Diagnosis        1 0.0946  0.0946   50.49 1.8e-06 ***
## GABAW            1 0.0029  0.0029    1.55  0.2301    
## GLXW             1 0.0015  0.0015    0.81  0.3794    
## AgefMRI          1 0.0172  0.0172    9.17  0.0076 ** 
## Sex              1 0.0011  0.0011    0.60  0.4509    
## MeanFD           1 0.0062  0.0062    3.33  0.0857 .  
## CSF_PCT          1 0.0029  0.0029    1.57  0.2275    
## GM_PCT           1 0.0084  0.0084    4.51  0.0487 *  
## Diagnosis:GLXW   1 0.0008  0.0008    0.43  0.5185    
## Diagnosis:GABAW  1 0.0002  0.0002    0.13  0.7201    
## Residuals       17 0.0318  0.0019                    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...dmPFC  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.05645 -0.02125 -0.00578  0.01485  0.09254 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)   
## (Intercept)          0.66400    0.21000    3.16   0.0057 **
## DiagnosisMDD         0.10815    0.18310    0.59   0.5625   
## GABAW              -71.50223   42.05139   -1.70   0.1073   
## GLXW                -0.51127   27.90449   -0.02   0.9856   
## AgefMRI             -0.01649    0.00601   -2.74   0.0139 * 
## Sex                  0.02550    0.01912    1.33   0.2000   
## MeanFD               0.23758    0.12785    1.86   0.0805 . 
## CSF_PCT              0.00333    0.00358    0.93   0.3652   
## GM_PCT              -0.00475    0.00224   -2.12   0.0487 * 
## DiagnosisMDD:GLXW   25.55217   38.16016    0.67   0.5121   
## DiagnosisMDD:GABAW -23.83166   65.41413   -0.36   0.7201   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0433 on 17 degrees of freedom
## Multiple R-squared: 0.81,	Adjusted R-squared: 0.699 
## F-statistic: 7.26 on 10 and 17 DF,  p-value: 0.000208 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...dmPFC
##                 Df Sum Sq Mean Sq F value  Pr(>F)    
## Diagnosis        1 0.0946  0.0946   50.49 1.8e-06 ***
## GABAW            1 0.0029  0.0029    1.55  0.2301    
## GLXW             1 0.0015  0.0015    0.81  0.3794    
## AgefMRI          1 0.0172  0.0172    9.17  0.0076 ** 
## Sex              1 0.0011  0.0011    0.60  0.4509    
## MeanFD           1 0.0062  0.0062    3.33  0.0857 .  
## CSF_PCT          1 0.0029  0.0029    1.57  0.2275    
## GM_PCT           1 0.0084  0.0084    4.51  0.0487 *  
## Diagnosis:GLXW   1 0.0008  0.0008    0.43  0.5185    
## Diagnosis:GABAW  1 0.0002  0.0002    0.13  0.7201    
## Residuals       17 0.0318  0.0019                    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...dmPFC  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.05645 -0.02125 -0.00578  0.01485  0.09254 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)   
## (Intercept)          0.66400    0.21000    3.16   0.0057 **
## DiagnosisMDD         0.10815    0.18310    0.59   0.5625   
## GABAW              -71.50223   42.05139   -1.70   0.1073   
## GLXW                -0.51127   27.90449   -0.02   0.9856   
## AgefMRI             -0.01649    0.00601   -2.74   0.0139 * 
## Sex                  0.02550    0.01912    1.33   0.2000   
## MeanFD               0.23758    0.12785    1.86   0.0805 . 
## CSF_PCT              0.00333    0.00358    0.93   0.3652   
## GM_PCT              -0.00475    0.00224   -2.12   0.0487 * 
## DiagnosisMDD:GLXW   25.55217   38.16016    0.67   0.5121   
## DiagnosisMDD:GABAW -23.83166   65.41413   -0.36   0.7201   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0433 on 17 degrees of freedom
## Multiple R-squared: 0.81,	Adjusted R-squared: 0.699 
## F-statistic: 7.26 on 10 and 17 DF,  p-value: 0.000208 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...dmPFC
##                 Df Sum Sq Mean Sq F value  Pr(>F)    
## Diagnosis        1 0.0946  0.0946   50.49 1.8e-06 ***
## GABAW            1 0.0029  0.0029    1.55  0.2301    
## GLXW             1 0.0015  0.0015    0.81  0.3794    
## AgefMRI          1 0.0172  0.0172    9.17  0.0076 ** 
## Sex              1 0.0011  0.0011    0.60  0.4509    
## MeanFD           1 0.0062  0.0062    3.33  0.0857 .  
## CSF_PCT          1 0.0029  0.0029    1.57  0.2275    
## GM_PCT           1 0.0084  0.0084    4.51  0.0487 *  
## Diagnosis:GLXW   1 0.0008  0.0008    0.43  0.5185    
## Diagnosis:GABAW  1 0.0002  0.0002    0.13  0.7201    
## Residuals       17 0.0318  0.0019                    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...dmPFC  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.05645 -0.02125 -0.00578  0.01485  0.09254 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)   
## (Intercept)          0.66400    0.21000    3.16   0.0057 **
## DiagnosisMDD         0.10815    0.18310    0.59   0.5625   
## GABAW              -71.50223   42.05139   -1.70   0.1073   
## GLXW                -0.51127   27.90449   -0.02   0.9856   
## AgefMRI             -0.01649    0.00601   -2.74   0.0139 * 
## Sex                  0.02550    0.01912    1.33   0.2000   
## MeanFD               0.23758    0.12785    1.86   0.0805 . 
## CSF_PCT              0.00333    0.00358    0.93   0.3652   
## GM_PCT              -0.00475    0.00224   -2.12   0.0487 * 
## DiagnosisMDD:GLXW   25.55217   38.16016    0.67   0.5121   
## DiagnosisMDD:GABAW -23.83166   65.41413   -0.36   0.7201   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0433 on 17 degrees of freedom
## Multiple R-squared: 0.81,	Adjusted R-squared: 0.699 
## F-statistic: 7.26 on 10 and 17 DF,  p-value: 0.000208 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...dmPFC
##                 Df Sum Sq Mean Sq F value  Pr(>F)    
## Diagnosis        1 0.0946  0.0946   50.49 1.8e-06 ***
## GABAW            1 0.0029  0.0029    1.55  0.2301    
## GLXW             1 0.0015  0.0015    0.81  0.3794    
## AgefMRI          1 0.0172  0.0172    9.17  0.0076 ** 
## Sex              1 0.0011  0.0011    0.60  0.4509    
## MeanFD           1 0.0062  0.0062    3.33  0.0857 .  
## CSF_PCT          1 0.0029  0.0029    1.57  0.2275    
## GM_PCT           1 0.0084  0.0084    4.51  0.0487 *  
## Diagnosis:GLXW   1 0.0008  0.0008    0.43  0.5185    
## Diagnosis:GABAW  1 0.0002  0.0002    0.13  0.7201    
## Residuals       17 0.0318  0.0019                    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...dmPFC  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD + CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.05645 -0.02125 -0.00578  0.01485  0.09254 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)   
## (Intercept)          0.66400    0.21000    3.16   0.0057 **
## DiagnosisMDD         0.10815    0.18310    0.59   0.5625   
## GABAW              -71.50223   42.05139   -1.70   0.1073   
## GLXW                -0.51127   27.90449   -0.02   0.9856   
## AgefMRI             -0.01649    0.00601   -2.74   0.0139 * 
## Sex                  0.02550    0.01912    1.33   0.2000   
## MeanFD               0.23758    0.12785    1.86   0.0805 . 
## CSF_PCT              0.00333    0.00358    0.93   0.3652   
## GM_PCT              -0.00475    0.00224   -2.12   0.0487 * 
## DiagnosisMDD:GLXW   25.55217   38.16016    0.67   0.5121   
## DiagnosisMDD:GABAW -23.83166   65.41413   -0.36   0.7201   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0433 on 17 degrees of freedom
## Multiple R-squared: 0.81,	Adjusted R-squared: 0.699 
## F-statistic: 7.26 on 10 and 17 DF,  p-value: 0.000208 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...dmPFC
##                 Df Sum Sq Mean Sq F value  Pr(>F)    
## Diagnosis        1 0.0946  0.0946   50.49 1.8e-06 ***
## GABAW            1 0.0029  0.0029    1.55  0.2301    
## GLXW             1 0.0015  0.0015    0.81  0.3794    
## AgefMRI          1 0.0172  0.0172    9.17  0.0076 ** 
## Sex              1 0.0011  0.0011    0.60  0.4509    
## MeanFD           1 0.0062  0.0062    3.33  0.0857 .  
## CSF_PCT          1 0.0029  0.0029    1.57  0.2275    
## GM_PCT           1 0.0084  0.0084    4.51  0.0487 *  
## Diagnosis:GLXW   1 0.0008  0.0008    0.43  0.5185    
## Diagnosis:GABAW  1 0.0002  0.0002    0.13  0.7201    
## Residuals       17 0.0318  0.0019                    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
```


MDD < CT
----------

* Left DC / Superior Temporal  
* Left DC / Occipital Cuneal	
* Right DC / Occipital Cuneal	
* Right DC / Occipital Lingual	
* Right DC / Fusiform	
* Left DRP / Occipital Fusiform	
* Right DRP / Occipital Fusiform	
* Right DRP / Lateral Occipital	
* Right DRP / Lateral Occipital	
* Right VRP / Cuneal	
* Right VRP / Fusiform	
* Right NAc / Middle Temporal	
* Right NAc / Middle Occipital	
* Right NAc / Occipital Fusiform	
* Left VC / Postcentral	
* Right VC / Occipital Fusiform	
* Right VC / Occipital Cuneal	
* Right DCP / Lateral Occipital


```r
input = read.csv("/Users/qingyang.li/Projects/Vilma_Adolescent_MDD_2011/GABA_ANOVA/ANOVA_input_MDDltCT.csv")
varlist = colnames(input)[3:20]

for (i in seq(1:length(varlist))) {
    
    Formula = paste(varlist[1], " ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT")
    model = lm(Formula, data = input)
    model.anova = anova(model)
    print("++++++++ Model +++++++++++++")
    print(Formula)
    print("+++++++ Model Summary ++++++")
    print(summary(model))
    print("+++++++ ANOVA results ++++++")
    print(model.anova)
    print("")
    
}
```

```
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...Superior.Temporal  ~ Diagnosis + GABAW + GLXW + GLXW* Diagnosis+ GABAW * Diagnosis + AgefMRI +Sex + MeanFD +CSF_PCT+GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -0.1433 -0.0310  0.0160  0.0386  0.1201 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)  
## (Intercept)          0.31530    0.41167    0.77    0.454  
## DiagnosisMDD        -0.22335    0.35893   -0.62    0.542  
## GABAW              -37.59043   82.43407   -0.46    0.654  
## GLXW                46.04789   54.70166    0.84    0.412  
## AgefMRI              0.00276    0.01179    0.23    0.818  
## Sex                  0.06851    0.03748    1.83    0.085 .
## MeanFD              -0.00443    0.25063   -0.02    0.986  
## CSF_PCT             -0.00557    0.00701   -0.79    0.438  
## GM_PCT              -0.00665    0.00439   -1.52    0.148  
## DiagnosisMDD:GLXW   -2.08915   74.80604   -0.03    0.978  
## DiagnosisMDD:GABAW  46.54484  128.23248    0.36    0.721  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0848 on 17 degrees of freedom
## Multiple R-squared: 0.581,	Adjusted R-squared: 0.335 
## F-statistic: 2.36 on 10 and 17 DF,  p-value: 0.0574 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...Superior.Temporal
##                 Df Sum Sq Mean Sq F value Pr(>F)   
## Diagnosis        1 0.1018  0.1018   14.14 0.0016 **
## GABAW            1 0.0005  0.0005    0.07 0.7888   
## GLXW             1 0.0107  0.0107    1.48 0.2397   
## AgefMRI          1 0.0101  0.0101    1.41 0.2516   
## Sex              1 0.0181  0.0181    2.52 0.1308   
## MeanFD           1 0.0000  0.0000    0.01 0.9413   
## CSF_PCT          1 0.0031  0.0031    0.43 0.5231   
## GM_PCT           1 0.0244  0.0244    3.40 0.0829 . 
## Diagnosis:GLXW   1 0.0000  0.0000    0.00 0.9863   
## Diagnosis:GABAW  1 0.0009  0.0009    0.13 0.7211   
## Residuals       17 0.1224  0.0072                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
```


ANH > 0
--------

* Left DC / SMA  
* Right DC / Middle Frontal	
* Right DRP / Supramarginal	
* Left VC / SMA	* Left VC / Precuneus	
* Right VC / Supramarginal	
* Right VC / pgACC


```r
input = read.csv("/Users/qingyang.li/Projects/Vilma_Adolescent_MDD_2011/GABA_ANOVA/ANH_pos.csv")
varlist = colnames(input)[3:10]


for (i in seq(1:length(varlist))) {
    
    Formula = paste(varlist[1], " ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT")
    model = lm(Formula, data = input)
    model.anova = anova(model)
    print("++++++++ Model +++++++++++++")
    print(Formula)
    print("+++++++ Model Summary ++++++")
    print(summary(model))
    print("+++++++ ANOVA results ++++++")
    print(model.anova)
    print("")
    
}
```

```
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...SMA  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.09875 -0.02180 -0.00257  0.03855  0.07927 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)  
## (Intercept) -0.392834   0.266460   -1.47    0.184  
## AnhBC.fMRI   0.029508   0.011420    2.58    0.036 *
## AgefMRI     -0.001435   0.008696   -0.17    0.874  
## Sex         -0.035965   0.040650   -0.88    0.406  
## MeanFD       0.069788   0.298876    0.23    0.822  
## CSF_PCT      0.000633   0.005678    0.11    0.914  
## GM_PCT       0.003169   0.003483    0.91    0.393  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0667 on 7 degrees of freedom
## Multiple R-squared: 0.63,	Adjusted R-squared: 0.312 
## F-statistic: 1.98 on 6 and 7 DF,  p-value: 0.196 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...SMA
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0402  0.0402    9.04   0.02 *
## AgefMRI     1 0.0031  0.0031    0.70   0.43  
## Sex         1 0.0052  0.0052    1.18   0.31  
## MeanFD      1 0.0007  0.0007    0.16   0.70  
## CSF_PCT     1 0.0000  0.0000    0.00   1.00  
## GM_PCT      1 0.0037  0.0037    0.83   0.39  
## Residuals   7 0.0311  0.0044                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...SMA  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.09875 -0.02180 -0.00257  0.03855  0.07927 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)  
## (Intercept) -0.392834   0.266460   -1.47    0.184  
## AnhBC.fMRI   0.029508   0.011420    2.58    0.036 *
## AgefMRI     -0.001435   0.008696   -0.17    0.874  
## Sex         -0.035965   0.040650   -0.88    0.406  
## MeanFD       0.069788   0.298876    0.23    0.822  
## CSF_PCT      0.000633   0.005678    0.11    0.914  
## GM_PCT       0.003169   0.003483    0.91    0.393  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0667 on 7 degrees of freedom
## Multiple R-squared: 0.63,	Adjusted R-squared: 0.312 
## F-statistic: 1.98 on 6 and 7 DF,  p-value: 0.196 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...SMA
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0402  0.0402    9.04   0.02 *
## AgefMRI     1 0.0031  0.0031    0.70   0.43  
## Sex         1 0.0052  0.0052    1.18   0.31  
## MeanFD      1 0.0007  0.0007    0.16   0.70  
## CSF_PCT     1 0.0000  0.0000    0.00   1.00  
## GM_PCT      1 0.0037  0.0037    0.83   0.39  
## Residuals   7 0.0311  0.0044                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...SMA  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.09875 -0.02180 -0.00257  0.03855  0.07927 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)  
## (Intercept) -0.392834   0.266460   -1.47    0.184  
## AnhBC.fMRI   0.029508   0.011420    2.58    0.036 *
## AgefMRI     -0.001435   0.008696   -0.17    0.874  
## Sex         -0.035965   0.040650   -0.88    0.406  
## MeanFD       0.069788   0.298876    0.23    0.822  
## CSF_PCT      0.000633   0.005678    0.11    0.914  
## GM_PCT       0.003169   0.003483    0.91    0.393  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0667 on 7 degrees of freedom
## Multiple R-squared: 0.63,	Adjusted R-squared: 0.312 
## F-statistic: 1.98 on 6 and 7 DF,  p-value: 0.196 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...SMA
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0402  0.0402    9.04   0.02 *
## AgefMRI     1 0.0031  0.0031    0.70   0.43  
## Sex         1 0.0052  0.0052    1.18   0.31  
## MeanFD      1 0.0007  0.0007    0.16   0.70  
## CSF_PCT     1 0.0000  0.0000    0.00   1.00  
## GM_PCT      1 0.0037  0.0037    0.83   0.39  
## Residuals   7 0.0311  0.0044                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...SMA  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.09875 -0.02180 -0.00257  0.03855  0.07927 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)  
## (Intercept) -0.392834   0.266460   -1.47    0.184  
## AnhBC.fMRI   0.029508   0.011420    2.58    0.036 *
## AgefMRI     -0.001435   0.008696   -0.17    0.874  
## Sex         -0.035965   0.040650   -0.88    0.406  
## MeanFD       0.069788   0.298876    0.23    0.822  
## CSF_PCT      0.000633   0.005678    0.11    0.914  
## GM_PCT       0.003169   0.003483    0.91    0.393  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0667 on 7 degrees of freedom
## Multiple R-squared: 0.63,	Adjusted R-squared: 0.312 
## F-statistic: 1.98 on 6 and 7 DF,  p-value: 0.196 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...SMA
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0402  0.0402    9.04   0.02 *
## AgefMRI     1 0.0031  0.0031    0.70   0.43  
## Sex         1 0.0052  0.0052    1.18   0.31  
## MeanFD      1 0.0007  0.0007    0.16   0.70  
## CSF_PCT     1 0.0000  0.0000    0.00   1.00  
## GM_PCT      1 0.0037  0.0037    0.83   0.39  
## Residuals   7 0.0311  0.0044                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...SMA  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.09875 -0.02180 -0.00257  0.03855  0.07927 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)  
## (Intercept) -0.392834   0.266460   -1.47    0.184  
## AnhBC.fMRI   0.029508   0.011420    2.58    0.036 *
## AgefMRI     -0.001435   0.008696   -0.17    0.874  
## Sex         -0.035965   0.040650   -0.88    0.406  
## MeanFD       0.069788   0.298876    0.23    0.822  
## CSF_PCT      0.000633   0.005678    0.11    0.914  
## GM_PCT       0.003169   0.003483    0.91    0.393  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0667 on 7 degrees of freedom
## Multiple R-squared: 0.63,	Adjusted R-squared: 0.312 
## F-statistic: 1.98 on 6 and 7 DF,  p-value: 0.196 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...SMA
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0402  0.0402    9.04   0.02 *
## AgefMRI     1 0.0031  0.0031    0.70   0.43  
## Sex         1 0.0052  0.0052    1.18   0.31  
## MeanFD      1 0.0007  0.0007    0.16   0.70  
## CSF_PCT     1 0.0000  0.0000    0.00   1.00  
## GM_PCT      1 0.0037  0.0037    0.83   0.39  
## Residuals   7 0.0311  0.0044                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...SMA  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.09875 -0.02180 -0.00257  0.03855  0.07927 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)  
## (Intercept) -0.392834   0.266460   -1.47    0.184  
## AnhBC.fMRI   0.029508   0.011420    2.58    0.036 *
## AgefMRI     -0.001435   0.008696   -0.17    0.874  
## Sex         -0.035965   0.040650   -0.88    0.406  
## MeanFD       0.069788   0.298876    0.23    0.822  
## CSF_PCT      0.000633   0.005678    0.11    0.914  
## GM_PCT       0.003169   0.003483    0.91    0.393  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0667 on 7 degrees of freedom
## Multiple R-squared: 0.63,	Adjusted R-squared: 0.312 
## F-statistic: 1.98 on 6 and 7 DF,  p-value: 0.196 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...SMA
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0402  0.0402    9.04   0.02 *
## AgefMRI     1 0.0031  0.0031    0.70   0.43  
## Sex         1 0.0052  0.0052    1.18   0.31  
## MeanFD      1 0.0007  0.0007    0.16   0.70  
## CSF_PCT     1 0.0000  0.0000    0.00   1.00  
## GM_PCT      1 0.0037  0.0037    0.83   0.39  
## Residuals   7 0.0311  0.0044                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...SMA  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.09875 -0.02180 -0.00257  0.03855  0.07927 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)  
## (Intercept) -0.392834   0.266460   -1.47    0.184  
## AnhBC.fMRI   0.029508   0.011420    2.58    0.036 *
## AgefMRI     -0.001435   0.008696   -0.17    0.874  
## Sex         -0.035965   0.040650   -0.88    0.406  
## MeanFD       0.069788   0.298876    0.23    0.822  
## CSF_PCT      0.000633   0.005678    0.11    0.914  
## GM_PCT       0.003169   0.003483    0.91    0.393  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0667 on 7 degrees of freedom
## Multiple R-squared: 0.63,	Adjusted R-squared: 0.312 
## F-statistic: 1.98 on 6 and 7 DF,  p-value: 0.196 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...SMA
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0402  0.0402    9.04   0.02 *
## AgefMRI     1 0.0031  0.0031    0.70   0.43  
## Sex         1 0.0052  0.0052    1.18   0.31  
## MeanFD      1 0.0007  0.0007    0.16   0.70  
## CSF_PCT     1 0.0000  0.0000    0.00   1.00  
## GM_PCT      1 0.0037  0.0037    0.83   0.39  
## Residuals   7 0.0311  0.0044                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Left.DC...SMA  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.09875 -0.02180 -0.00257  0.03855  0.07927 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)  
## (Intercept) -0.392834   0.266460   -1.47    0.184  
## AnhBC.fMRI   0.029508   0.011420    2.58    0.036 *
## AgefMRI     -0.001435   0.008696   -0.17    0.874  
## Sex         -0.035965   0.040650   -0.88    0.406  
## MeanFD       0.069788   0.298876    0.23    0.822  
## CSF_PCT      0.000633   0.005678    0.11    0.914  
## GM_PCT       0.003169   0.003483    0.91    0.393  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0667 on 7 degrees of freedom
## Multiple R-squared: 0.63,	Adjusted R-squared: 0.312 
## F-statistic: 1.98 on 6 and 7 DF,  p-value: 0.196 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Left.DC...SMA
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0402  0.0402    9.04   0.02 *
## AgefMRI     1 0.0031  0.0031    0.70   0.43  
## Sex         1 0.0052  0.0052    1.18   0.31  
## MeanFD      1 0.0007  0.0007    0.16   0.70  
## CSF_PCT     1 0.0000  0.0000    0.00   1.00  
## GM_PCT      1 0.0037  0.0037    0.83   0.39  
## Residuals   7 0.0311  0.0044                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
```


ANH < 0
---------

* Right DC / Precuneus and PCC  
* Left NAC / sgACC and Caudate	
* Right NAc / Occipital Fusiform


```r
input = read.csv("/Users/qingyang.li/Projects/Vilma_Adolescent_MDD_2011/GABA_ANOVA/ANH_neg.csv")
varlist = colnames(input)[3:10]


for (i in seq(1:length(varlist))) {
    
    Formula = paste(varlist[1], " ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT")
    model = lm(Formula, data = input)
    model.anova = anova(model)
    print("++++++++ Model +++++++++++++")
    print(Formula)
    print("+++++++ Model Summary ++++++")
    print(summary(model))
    print("+++++++ ANOVA results ++++++")
    print(model.anova)
    print("")
    
}
```

```
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...Precuneus.and.PCC  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.13372 -0.02318  0.00292  0.03529  0.08123 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)  
## (Intercept)  0.32033    0.29472    1.09    0.313  
## AnhBC.fMRI  -0.02330    0.01263   -1.85    0.108  
## AgefMRI      0.01016    0.00962    1.06    0.326  
## Sex          0.01558    0.04496    0.35    0.739  
## MeanFD      -0.72597    0.33057   -2.20    0.064 .
## CSF_PCT     -0.00515    0.00628   -0.82    0.439  
## GM_PCT      -0.00538    0.00385   -1.40    0.205  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0737 on 7 degrees of freedom
## Multiple R-squared: 0.724,	Adjusted R-squared: 0.488 
## F-statistic: 3.07 on 6 and 7 DF,  p-value: 0.0842 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...Precuneus.and.PCC
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0114  0.0114    2.10  0.190  
## AgefMRI     1 0.0318  0.0318    5.85  0.046 *
## Sex         1 0.0095  0.0095    1.75  0.228  
## MeanFD      1 0.0344  0.0344    6.34  0.040 *
## CSF_PCT     1 0.0023  0.0023    0.42  0.538  
## GM_PCT      1 0.0106  0.0106    1.95  0.205  
## Residuals   7 0.0380  0.0054                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...Precuneus.and.PCC  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.13372 -0.02318  0.00292  0.03529  0.08123 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)  
## (Intercept)  0.32033    0.29472    1.09    0.313  
## AnhBC.fMRI  -0.02330    0.01263   -1.85    0.108  
## AgefMRI      0.01016    0.00962    1.06    0.326  
## Sex          0.01558    0.04496    0.35    0.739  
## MeanFD      -0.72597    0.33057   -2.20    0.064 .
## CSF_PCT     -0.00515    0.00628   -0.82    0.439  
## GM_PCT      -0.00538    0.00385   -1.40    0.205  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0737 on 7 degrees of freedom
## Multiple R-squared: 0.724,	Adjusted R-squared: 0.488 
## F-statistic: 3.07 on 6 and 7 DF,  p-value: 0.0842 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...Precuneus.and.PCC
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0114  0.0114    2.10  0.190  
## AgefMRI     1 0.0318  0.0318    5.85  0.046 *
## Sex         1 0.0095  0.0095    1.75  0.228  
## MeanFD      1 0.0344  0.0344    6.34  0.040 *
## CSF_PCT     1 0.0023  0.0023    0.42  0.538  
## GM_PCT      1 0.0106  0.0106    1.95  0.205  
## Residuals   7 0.0380  0.0054                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...Precuneus.and.PCC  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.13372 -0.02318  0.00292  0.03529  0.08123 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)  
## (Intercept)  0.32033    0.29472    1.09    0.313  
## AnhBC.fMRI  -0.02330    0.01263   -1.85    0.108  
## AgefMRI      0.01016    0.00962    1.06    0.326  
## Sex          0.01558    0.04496    0.35    0.739  
## MeanFD      -0.72597    0.33057   -2.20    0.064 .
## CSF_PCT     -0.00515    0.00628   -0.82    0.439  
## GM_PCT      -0.00538    0.00385   -1.40    0.205  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0737 on 7 degrees of freedom
## Multiple R-squared: 0.724,	Adjusted R-squared: 0.488 
## F-statistic: 3.07 on 6 and 7 DF,  p-value: 0.0842 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...Precuneus.and.PCC
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0114  0.0114    2.10  0.190  
## AgefMRI     1 0.0318  0.0318    5.85  0.046 *
## Sex         1 0.0095  0.0095    1.75  0.228  
## MeanFD      1 0.0344  0.0344    6.34  0.040 *
## CSF_PCT     1 0.0023  0.0023    0.42  0.538  
## GM_PCT      1 0.0106  0.0106    1.95  0.205  
## Residuals   7 0.0380  0.0054                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...Precuneus.and.PCC  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.13372 -0.02318  0.00292  0.03529  0.08123 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)  
## (Intercept)  0.32033    0.29472    1.09    0.313  
## AnhBC.fMRI  -0.02330    0.01263   -1.85    0.108  
## AgefMRI      0.01016    0.00962    1.06    0.326  
## Sex          0.01558    0.04496    0.35    0.739  
## MeanFD      -0.72597    0.33057   -2.20    0.064 .
## CSF_PCT     -0.00515    0.00628   -0.82    0.439  
## GM_PCT      -0.00538    0.00385   -1.40    0.205  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0737 on 7 degrees of freedom
## Multiple R-squared: 0.724,	Adjusted R-squared: 0.488 
## F-statistic: 3.07 on 6 and 7 DF,  p-value: 0.0842 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...Precuneus.and.PCC
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0114  0.0114    2.10  0.190  
## AgefMRI     1 0.0318  0.0318    5.85  0.046 *
## Sex         1 0.0095  0.0095    1.75  0.228  
## MeanFD      1 0.0344  0.0344    6.34  0.040 *
## CSF_PCT     1 0.0023  0.0023    0.42  0.538  
## GM_PCT      1 0.0106  0.0106    1.95  0.205  
## Residuals   7 0.0380  0.0054                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...Precuneus.and.PCC  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.13372 -0.02318  0.00292  0.03529  0.08123 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)  
## (Intercept)  0.32033    0.29472    1.09    0.313  
## AnhBC.fMRI  -0.02330    0.01263   -1.85    0.108  
## AgefMRI      0.01016    0.00962    1.06    0.326  
## Sex          0.01558    0.04496    0.35    0.739  
## MeanFD      -0.72597    0.33057   -2.20    0.064 .
## CSF_PCT     -0.00515    0.00628   -0.82    0.439  
## GM_PCT      -0.00538    0.00385   -1.40    0.205  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0737 on 7 degrees of freedom
## Multiple R-squared: 0.724,	Adjusted R-squared: 0.488 
## F-statistic: 3.07 on 6 and 7 DF,  p-value: 0.0842 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...Precuneus.and.PCC
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0114  0.0114    2.10  0.190  
## AgefMRI     1 0.0318  0.0318    5.85  0.046 *
## Sex         1 0.0095  0.0095    1.75  0.228  
## MeanFD      1 0.0344  0.0344    6.34  0.040 *
## CSF_PCT     1 0.0023  0.0023    0.42  0.538  
## GM_PCT      1 0.0106  0.0106    1.95  0.205  
## Residuals   7 0.0380  0.0054                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...Precuneus.and.PCC  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.13372 -0.02318  0.00292  0.03529  0.08123 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)  
## (Intercept)  0.32033    0.29472    1.09    0.313  
## AnhBC.fMRI  -0.02330    0.01263   -1.85    0.108  
## AgefMRI      0.01016    0.00962    1.06    0.326  
## Sex          0.01558    0.04496    0.35    0.739  
## MeanFD      -0.72597    0.33057   -2.20    0.064 .
## CSF_PCT     -0.00515    0.00628   -0.82    0.439  
## GM_PCT      -0.00538    0.00385   -1.40    0.205  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0737 on 7 degrees of freedom
## Multiple R-squared: 0.724,	Adjusted R-squared: 0.488 
## F-statistic: 3.07 on 6 and 7 DF,  p-value: 0.0842 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...Precuneus.and.PCC
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0114  0.0114    2.10  0.190  
## AgefMRI     1 0.0318  0.0318    5.85  0.046 *
## Sex         1 0.0095  0.0095    1.75  0.228  
## MeanFD      1 0.0344  0.0344    6.34  0.040 *
## CSF_PCT     1 0.0023  0.0023    0.42  0.538  
## GM_PCT      1 0.0106  0.0106    1.95  0.205  
## Residuals   7 0.0380  0.0054                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...Precuneus.and.PCC  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.13372 -0.02318  0.00292  0.03529  0.08123 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)  
## (Intercept)  0.32033    0.29472    1.09    0.313  
## AnhBC.fMRI  -0.02330    0.01263   -1.85    0.108  
## AgefMRI      0.01016    0.00962    1.06    0.326  
## Sex          0.01558    0.04496    0.35    0.739  
## MeanFD      -0.72597    0.33057   -2.20    0.064 .
## CSF_PCT     -0.00515    0.00628   -0.82    0.439  
## GM_PCT      -0.00538    0.00385   -1.40    0.205  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0737 on 7 degrees of freedom
## Multiple R-squared: 0.724,	Adjusted R-squared: 0.488 
## F-statistic: 3.07 on 6 and 7 DF,  p-value: 0.0842 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...Precuneus.and.PCC
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0114  0.0114    2.10  0.190  
## AgefMRI     1 0.0318  0.0318    5.85  0.046 *
## Sex         1 0.0095  0.0095    1.75  0.228  
## MeanFD      1 0.0344  0.0344    6.34  0.040 *
## CSF_PCT     1 0.0023  0.0023    0.42  0.538  
## GM_PCT      1 0.0106  0.0106    1.95  0.205  
## Residuals   7 0.0380  0.0054                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
## [1] "++++++++ Model +++++++++++++"
## [1] "Right.DC...Precuneus.and.PCC  ~  + AnhBC.fMRI + AgefMRI +Sex + MeanFD + CSF_PCT + GM_PCT"
## [1] "+++++++ Model Summary ++++++"
## 
## Call:
## lm(formula = Formula, data = input)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.13372 -0.02318  0.00292  0.03529  0.08123 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)  
## (Intercept)  0.32033    0.29472    1.09    0.313  
## AnhBC.fMRI  -0.02330    0.01263   -1.85    0.108  
## AgefMRI      0.01016    0.00962    1.06    0.326  
## Sex          0.01558    0.04496    0.35    0.739  
## MeanFD      -0.72597    0.33057   -2.20    0.064 .
## CSF_PCT     -0.00515    0.00628   -0.82    0.439  
## GM_PCT      -0.00538    0.00385   -1.40    0.205  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## 
## Residual standard error: 0.0737 on 7 degrees of freedom
## Multiple R-squared: 0.724,	Adjusted R-squared: 0.488 
## F-statistic: 3.07 on 6 and 7 DF,  p-value: 0.0842 
## 
## [1] "+++++++ ANOVA results ++++++"
## Analysis of Variance Table
## 
## Response: Right.DC...Precuneus.and.PCC
##            Df Sum Sq Mean Sq F value Pr(>F)  
## AnhBC.fMRI  1 0.0114  0.0114    2.10  0.190  
## AgefMRI     1 0.0318  0.0318    5.85  0.046 *
## Sex         1 0.0095  0.0095    1.75  0.228  
## MeanFD      1 0.0344  0.0344    6.34  0.040 *
## CSF_PCT     1 0.0023  0.0023    0.42  0.538  
## GM_PCT      1 0.0106  0.0106    1.95  0.205  
## Residuals   7 0.0380  0.0054                 
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 
## [1] ""
```

You can also embed plots, for example:


```r
plot(cars)
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5.png) 


