# Data Professional Survey Results Breakdown
### Dashboard :
<img width="587" height="332" alt="Image" src="https://github.com/user-attachments/assets/679b6f99-2641-44fa-a903-bf50b7c03708" />

## Problem Statement

This dashboard provides a breakdown of a survey carried  out by Alex the Analyst, in which 630 participants were questions regarding their careers in data, through a link on various social media platforms including linked in, twitter etc.  Questions were asked about yearly salary, precise industries, favourite programming language, happiness rating in career over a number of variables and general demographic questions. 
Since, number of neutrl/dissatisfied customers (almost 57 %) are more than satisfied customers (around 43 %), thus in all they must work on improving their services. 

Also since average delay in arrival & departure both is 15 minutes, thus they must try to reduce it.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor to transform data. 
- Step 3 : Data cleaning
    - removed columns, split columns by delimeter to create separate column of other comments to remove free text responses and create consistent 'other' option for a number of responses. 
    - calculated average of current yearly salary range by splitting column 'digit to non digit', removing '-', '+', 'k'.   
    - Used Power Query formula to create new column of average salary,  ((MinSalary + MaxSalary)/2), Changed data type from text to decimal. 
- Step 4 : Added visualisations
    - Card for number of participants
    - Card for Average Salary of participants
    - STacked bar chart for average salarys by Data Job Title (changed titles, axis lables and legend)
    - Added stacked column chart of favourite programming laguage by Job Title
    - Added pie chart describing demographic of participants (country) so can interact with data and understand how averages change by country. 
    - Donut chart of job entry difficulty.
    - Added gauage of hapiness levels of variables .  
- Step 5: Used DAX Function to find overall average happiness rating using the variables surveyed. 
- Step 6 : In the report view, under the view tab, theme was selected.
-

```dax       
AvgHappinessTrue = 
DIVIDE(
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Coworkers)]) +
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Learning New Things)]) +
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Management)]) +
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Upward Mobility)]) +
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Work/Life Balance)]),
    
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Coworkers)]) +
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Learning New Things)]) +
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Management)]) +
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Upward Mobility)]) +
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Work/Life Balance)])
) 
```

        
Step  7: Single Dashboard created in Power BI.
