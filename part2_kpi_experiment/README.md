## Task 1: Understand the Business Problem
Business Problem
The company launched a new onboarding and activation campaign to improve user activation and subscription conversion.

The decision to be made is whether the new onboarding experience (Treatment) should be rolled out to all users or not.

This decision impacts:

->New users entering the product

->Product and Growth teams

->Revenue performance of the business

The primary outcome expected is an increase in paid conversion rate.

Before recommending rollout, the company must ensure that:

->Conversion improves significantly

->Revenue quality is maintained

->Refund rates do not increase materially

->Support burden does not increase excessively

->User engagement remains healthy

Evidence required:

->Statistically significant improvement in the primary success metric(paid conversion rate)

->Positive movement in supporting metrics

->No major deterioration in guardrail metrics

->Consistent performance across key user segments

## Task 2: Define the North Star Metric

North star metric chosen for this experiment is Paid Conversion Rate

The purpose of the onboarding and activation campaign is to move users toward becoming paid customers.
The campaign only creates business value if more users ultimately subscribe.

Other metrics are chosen as supporting metrics due to following reasons-
Landing Page Visit Rate- Early funnel indicator

Trial Start Rate- Intermediate funnel step

Onboarding Completion Rate- Activation indicator

Engagement Score- Quality signal

Revenue per User- Financial outcome

Days to Convert- Efficiency indicator

These above supporting metrics tell why conversion changed but do not directly represent business success.

Higher paid conversion contributes to business growth in the following ways-

->More subscribers

->More recurring revenue

->Higher lifetime value

Risk of Optimizing Blindly

Paid conversion could increase while:

->Refunds increase

->Support burden rises

->Low-quality customers convert

->Long-term retention decreases

## Task 4: Clean and Prepare Experiment Data
1.missing values found-

device type-18 (filled with Unknown)

traffic source-24 (filled with Unkown)

days_to_convert-1336 (ignored as most users did not convert)

engagement_score-14 (filled with median)

2.Group counts

before removing duplicated-

treatment-715

control-693

3.Found 8 duplicate user ids and duplicates were removed

4.Did not find any invalid binary values

# Outliers in revenue(after removing duplicate values)
quartile1=404.02

quartile 3=1178.665

IQR=774.645

upper_bound=2340.6325

lower_bound= -757.9475

found 4 outliers but didnot remove it as they represent legitimate customer purchases and are important for measuring business performance.
Segment distribution across groups

# Segment distribution across groups-after removing duplicates
distribution across region

Row Labels	|Control	|Treatment

East	    |157	    |170

North	    |201	    |180

South	    |184	    |183

West	    |148	    |177

fairly distributed 

ditribution across device type
Row Labels	    |Control	    |Treatment

Desktop	        |200	        |213

Mobile	        |426	        |432

Tablet	        |55	            |56

Unknown	        |9	            |9

distribution across traffic source

Row Labels	       |Control	    |Treatment

Email	           |73	        |56

Organic	           |246	        |237	  

Paid Search	       |155	        |176	

Referral	       |81	        |91	

Social	           |129	        |132	

Unknown	           |6	        |18	

distribution across plan type

Row Labels	   |Control	   |Treatment

Basic	       |221	       |232

Free	       |360	       |366

Premium	       |109	       |112

# Task 8: Evaluate Guardrail Metrics

Refund Rate for control is 0.0% and for treatment is 0.42% which is the slight increase which must be monitored.
support ticket rate increased from 14.8 in control to 24.8% in treatment and it is meaningful as more users will have queries on onboarding. Needs investigation
Days to convert decreased from 8.8 in control to 6.40 in treatment which is a good improvement.

## README requirements

# A/B Testing Analysis for Onboarding & Activation Campaign

## Business Context

A subscription-based digital product company introduced a new onboarding and activation campaign to improve user activation, engagement, and paid subscription conversion. New users were randomly assigned to one of two groups:

* Control Group: Existing onboarding experience
* Treatment Group: New onboarding and activation campaign

The objective of this experiment is to determine whether the new onboarding experience should be rolled out to all users based on statistical evidence and business impact.

The business decision depends on whether the treatment significantly improves user conversion while maintaining healthy customer experience and revenue quality.

# Dataset Description

The dataset contains user-level information collected during the A/B experiment.

Each row represents one user and includes attributes such as:

* User ID
* Experiment Group (Control/Treatment)
* Region
* Device Type
* Traffic Source
* Plan Type
* Landing Page Visit
* Trial Started
* Onboarding Completed
* Paid Conversion
* Revenue for 30 days
* Refund Requested
* Support Ticket
* Engagement Score
* Days to Convert

The dataset was cleaned before analysis by checking for:

* Missing values
* Duplicate user IDs
* Group balance
* Invalid binary values
* Revenue outliers
* Segment distribution across experiment groups

### Data Cleaning Summary

* Duplicate user IDs were removed.
* Missing values in categorical variables were labeled as "Unknown".
* Missing engagement scores were imputed using the median.
* Blank values in Days to Convert were retained for users who did not convert.
* Revenue outliers were identified using the IQR method after excluding zero revenue values. The identified outliers were retained because they represent legitimate customer purchases rather than data errors.

# North Star Metric

### Paid Conversion Rate
Paid Conversion Rate = Number of Paid Users ÷ Total Users

### Why it was selected

Paid conversion rate directly measures whether the onboarding campaign successfully converts free users into paying subscribers. Since the primary business objective is revenue growth through subscriptions, this metric best reflects the success of the experiment.

Supporting metrics such as landing page visits, trial starts, onboarding completion, engagement score, and revenue help explain user behavior but do not directly represent business growth.

Optimizing only paid conversion without monitoring customer quality could increase refunds or support costs; therefore guardrail metrics were also evaluated.


# KPI Tree Summary
Shared in the screenshot 

### Step 1: Data Preparation

* Checked missing values
* Removed duplicate users
* Validated binary variables
* Evaluated revenue outliers
* Verified experiment group balance
* Checked segment distribution

### Step 2: Experiment Summary

Calculated and compared the following metrics between Control and Treatment groups:

* User Count
* Landing Page Visit Rate
* Trial Start Rate
* Onboarding Completion Rate
* Paid Conversion Rate
* Average Revenue Per User
* Average Revenue Per Converted User
* Refund Rate
* Support Ticket Rate
* Average Engagement Score
* Average Days to Convert

Segment-level analysis was also performed for:

* Region
* Plan type
* Traffic Source

### Step 3: Statistical Testing

A one-tailed Two-Proportion Z-Test was performed on the Paid Conversion Rate.

Hypotheses:

H₀: Paid Conversion Rate (Treatment) ≤ Paid Conversion Rate (Control)

H₁: Paid Conversion Rate (Treatment) > Paid Conversion Rate (Control)

Significance Level:

α = 0.05

# Hypothesis Test Summary

| Metric               | Control | Treatment |
| -------------------- | ------- | --------- |
| Paid Conversion Rate | 3.19%   | 7.04%     |

### Statistical Results

* Z Statistic = 3.26
* P-value = 0.00055

### Decision

Since the p-value is less than 0.05, the null hypothesis was rejected.

### Interpretation

The new onboarding campaign produced a statistically significant improvement in paid conversion rate compared with the existing onboarding experience.

# Guardrail Metrics Considered

Although paid conversion improved significantly, additional business metrics were evaluated before making a recommendation.

### Refund Rate

* Control: 0.00%
* Treatment: 0.42%

A small increase was observed but remained relatively low.

### Support Ticket Rate

* Control: 14.8%
* Treatment: 24.8%

Support requests increased noticeably under the new onboarding experience, indicating potential usability issues that should be investigated.

### Average Engagement Score

* Control: 57.0
* Treatment: 62.9

User engagement improved under the treatment.

### Average Days to Convert

* Control: 8.86 days
* Treatment: 6.40 days

Treatment users converted more quickly than control users.

# Final Recommendation

The treatment significantly increased paid conversion rate while also improving engagement and reducing the average time required for users to convert.

However, the increase in support ticket rate indicates that some users experienced friction during onboarding.

Recommendation: Launch the new onboarding campaign for high-performing user segments while investigating the causes of increased support requests before a complete rollout.

Recommended rollout segments include:

* Mobile users
* Referral traffic users
* North and South regions

Following improvements to onboarding clarity and customer support, the experiment should be repeated before a full deployment.


# Assumptions and Limitations

## Assumptions

* Users were randomly assigned to experiment groups.
* User observations are independent.
* The experiment duration was sufficient to measure initial conversion behavior.
* Revenue values represent valid business transactions.

## Limitations

* Long-term retention and customer lifetime value were not available.
* Only early-stage conversion behavior was analyzed.
* Revenue outliers were retained because they represent genuine purchases.
* Support ticket reasons were unavailable for root-cause analysis.

