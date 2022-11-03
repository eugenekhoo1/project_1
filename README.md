# Project 1: Standardized Test Analysis

## Problem Statement:
What is the ideal state to study in and test to sit for? We will analyse test and admission scores to identify trends and suggestions to optimize for school admissions.

## Background

The SAT and ACT are standardized tests that many colleges and universities in the United States require for their admissions process. This score is used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a potential student will be accepted to the university.

The SAT has two sections of the test: Evidence-Based Reading and Writing and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). 

Standardized tests have long been a controversial topic for students, administrators, and legislators. Since the 1940's, an increasing number of colleges have been using scores from sudents' performances on tests like the SAT and the ACT as a measure for college readiness and aptitude ([*source*](https://www.minotdailynews.com/news/local-news/2017/04/a-brief-history-of-the-sat-and-act/)). Supporters of these tests argue that these scores can be used as an objective measure to determine college admittance. Opponents of these tests claim that these tests are not accurate measures of students potential or ability and serve as an inequitable barrier to entry. Lately, more and more schools are opting to drop the SAT/ACT requirement for their Fall 2021 applications ([*read more about this here*](https://www.cnn.com/2020/04/14/us/coronavirus-colleges-sat-act-test-trnd/index.html)).

Still, pre tertiary admission tests are a signal of a prospective student's intellectual capacity and are necessary given the scarcity of placements in top universities. Test scores (of all types including university grades) act as signals to employers as well.

## Datasets

For this analysis, we will be using SAT and ACT scores, as well as the ranges of accepted ACT/SAT student scores by colleges
* act_2017
* act_2018
* act_2019
* sat_2017
* sat_2018
* sat_2019
* sat_act_by_college

These datasets are then cleaned and merged to conduct cross-sectional and time series analysis. The resulting datasets used are:
* merged_scores_{} : {2017, 2018, 2019, all}
* sat_act_by_college

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|__state__|object|merged_scores_{}|State|
|__sat_ebrw__|int|merged_scores_{}|(SAT) Evidence-Based Reading and Writing|
|__sat_math__|int|merged_scores_{}|(SAT) Math|
|__sat_total__|int|merged_scores_{}|Total SAT Score|
|__sat_participation__|float|merged_scores_{}|SAT Participation Rate (by Seniors)|
|__act_composite__|float|merged_scores_{}|ACT Composite Scores|
|__act_participation__|float|merged_scores_{}|ACT Participation Rate (by Seniors)|
|__school__|object|sat_act_by_college|University name|
|__number_of_applicants__|float|sat_act_by_college|Number of applicants|
|__accept_rate__|float|sat_act_by_college|Acceptance rate|
|__sat_25th_percentile__|float|sat_act_by_college|SAT score at 25th percentile|
|__sat_75th_percentile__|float|sat_act_by_college|SAT score at 75th percentile|
|__act_25th_percentile__|float|sat_act_by_college|ACT score at 25th percentile|
|__act_75th_percentile__|float|sat_act_by_college|ACT score at 75th percentile|


## Analysis

At a high level, the average participation rates across all states has increased for SAT and decreased for ACT. 
Test scores on average have fallen over the 3 years.

<img src="https://github.com/eugenekhoo1/project_1/blob/90ce956c8e0e3f11a9d88ed181e37c45a76e7ee2/images/year_on_year_summary.png">

SAT and ACT test scores are negatively correlated. Taking both tests results in one underperforming

<img src="https://github.com/eugenekhoo1/project_1/blob/90ce956c8e0e3f11a9d88ed181e37c45a76e7ee2/images/test_score_correlation_matrix.png">

Both SAT and ACT scores and participation rates are negatively correlated. (2019 data)
Likely a case of high participation rates diluting quality of test scores.

<img src="https://github.com/eugenekhoo1/project_1/blob/90ce956c8e0e3f11a9d88ed181e37c45a76e7ee2/images/sat_scores_vs_participation.png">

<img src="https://github.com/eugenekhoo1/project_1/blob/90ce956c8e0e3f11a9d88ed181e37c45a76e7ee2/images/act_scores_vs_participation.png">

## Conclusions and Recommendations

Given that test scores on average have been falling and with SAT/ACT scores negatively correlated, it might be wise for prospective students to be selective with the state in which they plan to undergo pre-tertiary education. We interpret low test scores as a proxy for a poor education system, although more analysis should be conducted to identify other factors (e.g. household income per capita, parent's education level, crime rates, etc.)

Nevertheless, for this exercise, we assume that a prospective student will end up being an average one. A prospective student also has limited time and resources and should pick an admissions test to focus on (although both have similar topics). We present the optimal state and admissions test to consider.

<img src="https://github.com/eugenekhoo1/project_1/blob/bec43865fed0406c47d87c188a3d2c846bfe7e3b/images/school_qualification_count1.png">

The School Qualification Count measures the number of admission thresholds (at 25th percentile) that the average student is able to meet. For example, the average student taking the SAT in Wisconsin would have met the 25th percentile threshold of 332 schools. We also observe that for the top 10 states, the average students taking the SATs have a higher school qualification count than if they took the ACT. This could be a contributing factor to the increasing SAT participation rates and declining ACT participation rates.

The recommendation would be to study for the __SAT__ in one of the following states:
<br> __['Wisconsin', 'Minnesota', 'South Dakota', 'North Dakota', 'Nebraska', 'Iowa', 'Kansas', 'Missouri', 'Utah', 'Mississippi']__
