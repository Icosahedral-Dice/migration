# Heterogeneity - Commuting Openness
Last updated: Jun 2nd, 2021

## Description

1. Rerun the treatment effect case by case  
    (1) code: `src\analysis\heterogeneity_analysis_112220\hetero_case_by_case_new`  
    + 02_build_tract_year_partial_balanced_panel_with_pscore_dist_control.do
    + 02_build_zip_year_partial_balanced_panel_with_pscore_dist_control.do
    + 03_reg_tract_case_by_case.do
    + 03_reg_zipcode_case_by_case.do
    + 06_binscatter_multi_reg_case_by_case.do
    (2) output: `output\analysis\heterogeneity_analysis_112220\hetero_case_by_case_new\partial_balanced_panel`
    (3) Description:
    + first filtering tracts by balance criteria, and then carryforward
        + balance criteria: br10 with partial balanced panel: 
            + The treated year (tau = 0) is included in the post years. I always require the outcome to be non-missing in the baseline year of tau = -1.
            + pre years (-4-0) is equal to or more than 1 years; and first group of post years (0-5) is equal to or more than 1 years; second group of post years (6-10) is equal to or more than 1 years
            + outcome variables are carryforwarded only for the pre-treated years
        + carryforward: after filtering by br10, tracts/zipcodes which have lot of missing values will be dropped. Then only several tracts/zipcodes will be changed.
    + only keep the cases in which there are more than 5 inner tracts (or 3 inner zipcodes). Because the outer tracts (or zipcodes) are systemically more than inner tracts (or zipcodes), the totally number of different tracts (both treatment groups and control groups) will be enough. 
    + a robustness check, discarding unique IDs with < 50% coverage.
    
## Results
(1) **Openness (30 mins)**:  
[Number of residents whose home tract is in 30mins and work tract is 30mins+ away]  
÷  
[Number of residents living within 30mins]  
`output/analysis/heterogeneity_analysis_112220/hetero_case_by_case_new/partial_balanced_panel/final_graphs/multi_reg_060121/regression_outcomes_commuting6`

