# An Analysis of Kickstarter Campaigns
## Purpose of this Analysis
The purpose of this analysis is to give Louise the chance to compare the outcome of her own play *Fever* to other plays based on their launch dates and their funding goals. By analyzing the data we have already prepared for Louise before she started her fundraising campaign, we are able to create visualizations that make it easy for Louise to see the data and compare it to her own campaign.
## Analysis
Using the spreadsheets that we have already prepared for Louise, we need to put together charts and tables to show us the data of the campaign outcomes based on their launch dates and their fundraising goals.
### Outcomes Based on Launch Dates
I created a pivot chart using the data from the Kickstarter sheet and filtered it by the parent category "Theater." The rows consist of the date created by month, and the columns consist of the different outcomes "successful," "failed," and "canceled." The values also consist of the count of outcomes. 

<img src="images/pivot_table1.png" width="343" height="295"> <img scr="images/pivot_table2.png" width="462" height="250">

From this pivot table, I was able to create a line chart that shows the number of outcomes based on the month of the launch date.

![](resources/Theater_Outcomes_vs_Launch.png)
### Outcomes Based on Fundraising Goals
First, I created a column of ranges of different goal amounts, a column for the number of each different outcome based on the different goal amount ranges, a column of the total number of projects for each goal amount, and a column for the percentage of each different outcome. 

<img src="images/outcomes_goals_table.png">

Next, I put in formulas to calculate each of the columns I created. For the number of each campaign outcome, I used the COUNTIFS function that looked at the goal amount column, the outcome column, and the subcategory column from the main Kickstarter sheet. 
```
=COUNTIFS(Kickstarter!$D:$D, ">=1000", Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays")-COUNTIFS(Kickstarter!$D:$D, ">4999", Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays")
```
Therefore, the formula pulls the number of each outcome for each range of goals amounts only looking at those that were plays. 

Then, for the total number of projects, I used the SUM formula to add together the number of projects of each outcome for each range of the fundraising goals. 
```
=SUM(B2:D2)
```
Therefore, it adds the total number of projects of each row, each range of goal amounts, and populates it in the total projects column.

Next, for the percentage of each outcome columns, I divided the number of each outcome by the total number of projects. 
```
=B2/E2
```
I also formatted the columns so that the number would be presented as a percentage. 


After that, with the goal and percentage columns selected, I created a line chart that shows the percentage of each outcome across the different ranges of the fundraising goals.

![](resources/Outcomes_vs_Goals.png)
## Challenges
When trying to figure out the formula to pull the number of campaigns based on the different goal ranges, the first formula I created excluded the first number of the range and the last number of the range. Also, it pulled the number from all the campaigns, all outcomes and all subcategories in the Kickstarter sheet. Even when the sheet was filtered based on the outcomes and was filtered on the subcategory "plays," it still would pull the number from all the campaigns on the Kickstarter sheet. I researched on the internet how to use a COUNTIFS formula that is inclusive, and was able to improve on my formula that included both the first number and the last number of the range. I also researched how to use a COUNTIFS formula that looks at multiple criteria, and was able to improve my formula so that it looks at not only the goal amount column but also the outcome and the subcategory of the campaigns.
## Conclusions
### Theater Outcomes Based on Launch Dates
According to the Theater Outcomes Based on Launch Dates line chart, the highest number of successful campaigns were launched in May. Also, the difference between the number of failed campaigns and the number of successful campaigns is also the greatest in May. Therefore, it is more likely to have a successful campaign when it is launched in May. Also, according to the Theater Outcomes Based on Launch Dates line chart, the number of successful campaigns drops to the lowest when they are launched from November to December. And, the number of failed campaigns and the number of successful campaigns are the closest when they are launched in December. Therefore, it is the least likely to have a successful campaign when it is launched in December.
### Outcomes Based on Goals
According to the Outcomes Based on Goals line chart, the highest percentage of successful campaigns is when the goal is less than $1000. As the goal amount increases, the percentage of successful campaigns decreases. However, there is two more goal amount ranges, $35000 to $39999 and $40000 to $44999, where the percentage of successful campaigns is more than the percentage of failed campaigns. Therefore, according to the Outcomes Based on Goals line chart, the campaign is more likely to be successful when the goal amount is less than $5000. Also, the campaign is likely to be successful when the goal amount is between $30000 and $44999. 
### Limitations
When looking at the Outcomes Based on Goals line chart, it fails to show the number of campaigns as it only shows the percentage. The number of successful campaigns is significantly higher when the goal amount is less than $5000 compared to when the goal is between $30000 and $44999. The number of campaigns drops as the goal amount increases, which makes it difficult to get an accurate and reliable percentage. The line chart makes it look like the amount of successful campaigns with goals less than $5000 is the same as the amount of successful campaigns with goals between $35000 to $44999. However, this is not true.

