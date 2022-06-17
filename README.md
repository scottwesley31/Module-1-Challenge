# Kickstarting with Excel

## Overview of Project
A playwright named Louise requested information in regards to plays she had prior involvement in fundraising. She specifically wants to know the outcomes of fundraising campaigns based on their launch date.

### Purpose
To determine trends in the Kickstarter dataset between fundraising goal vs launch date as well as fundraising goal vs outcomes.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
The original file (following modification as instructed in Module 1) did not include a "Years" column. The following formula was used to generate this column:

`=YEAR(S2)`
where S2 is a cell containing the date each event was created

A pivot table was created by placing the fields as follows:
Filters: Parent category, Years
Legend (Series): outcomes
Axis (Categories): Date Created Conversion
Values: Count of outcomes

This table can then be filtered for "theater".

This pivot table was then used to generate the following chart:
![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/107309793/174297453-e081d658-5e1d-4b37-b545-2981d2aa85b5.png)

### Analysis of Outcomes Based on Goals

### Challenges and Difficulties Encountered

Deliverable 1 Challenges

One difficulty with generating this deliverable was figuring out how to display the months in the row labels of the pivot table. When I initially dropped the "Date Created Conversion" field into the Axis (Categories) for the pivot chart it automatically places 3 fields: Date Created Conversion, Quarters, and Years2. When all of these are unmodified and left in the categories section, the row labels display the outcomes only by year. Both the Quarters and Years2 fields needed to be removed for the row labels to display the months.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
