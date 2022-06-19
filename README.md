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

*Filters:* Parent category, Years

*Legend (Series):* outcomes

*Axis (Categories):* Date Created Conversion

*Values:* Count of outcomes

This table can then be filtered for "theater".

This pivot table was then used to generate the following chart:
![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/107309793/174297453-e081d658-5e1d-4b37-b545-2981d2aa85b5.png)

### Analysis of Outcomes Based on Goals

A table was created in a new worksheet on the Kickstarter file which was organized as such and contained the following information:
![Outcomes_vs_Goals Table](https://user-images.githubusercontent.com/107309793/174460531-68a11db5-e84b-4f2c-b40b-d1670ce82dbd.png)

The table organizes a count of all of the successful, failed, and canceled plays into categories of specific goal ranges. This is possible using the `=COUNTIFS()` function in B2:H13. This function references the goal data from the "Kickstarter" worksheet tab and uses criteria to filter the data and only return a count of the values that match said criteria. There were essentially 3 versions of this formula used to accurately determine a count for each goal range category:

For the "Less than 1000" range: `=COUNTIFS(Kickstarter!D:D,"<1000",Kickstarter!F:F,"successful",Kickstarter!R:R,"plays")`

For the middle ranges (using B3 as an example): `=COUNTIFS(Kickstarter!D:D,"<=4999",Kickstarter!D:D,">=1000",Kickstarter!F:F,"successful",Kickstarter!R:R,"plays")`

For the "50000 or more" range: `=COUNTIFS(Kickstarter!D:D,">=50000",Kickstarter!F:F,"successful",Kickstarter!R:R,"plays")`

These formulas call on the goal column (Kickstarter!D:D), the outcomes column (Kickstarter!F:F), and the subcategory column (Kickstarter!R:R). Note that "successful" was swapped for "failed" and "canceled" to fill out columns C and D as pictured above. Note that the values in the Sum row and the Total Projects column values were all  calculated for each outcome category using the `=SUM()` function. This value was double-checked for each outcome category using the `=COUNTIFS` function again as so (with B15 as an example): 

`=COUNTIFS(Kickstarter!D:D,">0",Kickstarter!F:F,"successful",Kickstarter!R:R,"plays")`

The percentages in columns 

### Challenges and Difficulties Encountered

Deliverable 1 Challenges

One difficulty with generating this deliverable was figuring out how to display the months in the row labels of the pivot table. When I initially dropped the "Date Created Conversion" field into the Axis (Categories) for the pivot chart it automatically places 3 fields: Date Created Conversion, Quarters, and Years2. When all of these are unmodified and left in the categories section, the row labels display the outcomes only by year. Both the Quarters and Years2 fields needed to be removed for the row labels to display the months. F-H were calculated from these summed values.

The following line chart was created by selecting the goal range categories vs. the percentage values:
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/107309793/174480990-cf6fe6af-10f5-4757-89a5-e2e03da1abff.png)

Deliverable 2 Challenges

I challenge I encountered with completing the table with the appropriate count values was attempting to copy and paste the `=COUNTIFS()` function into other cells. For example - once I completed the "Number Successful" column, I copied and pasted the formulas into column C and changed the criteria to reference "failed" but by default the column ranges referenced in the Kickstarter data change by one coloumn to the right (Kickstarter!D:D becomes Kickstarter!E:E and so forth).

My workaround for this was to select the cell I wanted the formula copied, click into the formula bar and copy the text, click into the cell I wanted the formula pasted, press Esc to prevent changes to the original cell selected, and the pasting the copied text. This copied the formula with the correct column references and allowed for me to simply change only the outcomes criteria rather than having to type this formula out one-by-one in each cell as was done for column B.

I still had to spend time copying and pasting each respective formula into each cell for both the "Number Failed" and "Number Canceled" columns, but I do feel time was saved using this method.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

Without filtering by "Years" and only filtering by the "theater" parent category, it's evident that the majority of theater productions that were successful were launched between May, June, and July with a total of 111, 100, and 87 successful plays respectively.

Looking at the 2 data points from "successful" and "failed" in the month of December, you can conclude that about the same number of both successful and failed theater productions occurred (37 and 35 respectively). This means that there's about a 50% chance that the production will fail if launched at this time. This is contrary to all other months of the year where there is a much greater difference between the number of successful productions to failed productions. Of note - the 3 months mentioned above have the greatest difference between successful and failed, meaning the chance of success is very likely.

- What can you conclude about the Outcomes based on Goals?

Looking at the "Percentage Successful" line, it's evident that projects within the smallest goal category (Less Than 1000) had the  largest percentage. This could indicate that productions with the smallest goals resulted in the most success.

Looking at both the "Percentage Successful" and "Percentage Failed" lines at the same time (and where they intersect) splits up the goal categories into useful ranges. The following conclusions can be made:

Plays with goals of <1000 and less and up to the 10000 to 14999 were more likely to be successful.

Plays with goals of 15000 to 19999 were equally as likely to be successful or to fail (50/50 chance).

Plays with goals of 20000 to 24999 up to 30000 to 34999 were more likely to fail.

Plays with goals of 35000 to 39999 up to 40000 to 44999 were more likely to be successful.

Plays with goals of 45000 to 49999 up to 50000 or more were more likely to fail.

Summarized in goal ranges:

More Successful than Failed plays: $0-$14,999 and $35,000-$44,999
More Failed than Successful plays: $20,000-$34,999 and $45,000-$50,000+
Equally Successful and Failed plays: $15,000-$19,999.

Based on this conclusion, it might be helpful to stick to goal ranges of $0-$14,999 or $35,000-$44,999 as these productions are more likely to be successful.

- What are some limitations of this dataset?

One limitation of this dataset is potentially subjectivity in the "outcomes" column. Each cell in this column has one of 4 categories; successful, live, failed, or canceled. None of these categories are mathematically determined from the data. How exactly is "successful" defined? Is it when pledges exceed/meet goals? Is it when pledges reach a certain value? Similar questions can be applied to the failed category. Without the objectivity of a calculation in the outcomes column, all of the conclusions made based off of this information may not be an accurate representation of success.



- What are some other possible tables and/or graphs that we could create?
