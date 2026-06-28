
# Task 6: Frame Hypotheses
Metric-
Paid Conversion Rate

Null Hypothesis (H0)-
There is no difference in paid conversion rate between Control and Treatment group.
pTreatment = pControl

Alternative Hypothesis (Ha)-
Treatment has a higher paid conversion rate.
pTreatment > pControl

Test Type-
One-tailed Two-Proportion Z-Test 

Significance Level-
α = 0.05

Paid conversion directly measures business success.

If  p-value < 0.05 then reject null hypotheses

## Task 7: Perform Hypothesis or A/B Test Analysis

Test- One-tailed Two-Proportion Z-Test		
Item	                      Value	
Control paid Conversion-	0.0319(p1)	
Treatment paid Conversion-	0.0704(p2)	
        
Pooled Rate- (x1+x2)/(n1+n2)=0.051428571 (72/1400)
            
standard error- SQRT(pooled*(1-pooled)*(1/n1+1/n2))=0.011807217
        
z-statistics-(p2-p1)/SE= 3.260717553
        
p-value= 1-NORM.S.DIST(Z,TRUE)= 0.000555653
        
since 0.00055 < 0.05- Reject null hypothesis	
        
Interpretation- The treatment significantly improves paid conversion rate.	
