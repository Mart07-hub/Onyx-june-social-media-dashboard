##Dax Formulas
1)Avg. Engagement Rate = AVERAGE(Sheet1[Engagement_Rate])

2)BestDay = 
CALCULATE (
    MAX('Sheet1'[DayOfWeek]),
    TOPN(
        1,
        SUMMARIZE('Sheet1', 'Sheet1'[DayOfWeek], "Engagement", SUM('Sheet1'[Engagement])),
        [Engagement], DESC
    )
)

3)Top Content_Category = 
CALCULATE (
    MAX('Sheet1'[Content_Category]),
    TOPN(1, 
        SUMMARIZE('Sheet1', 'Sheet1'[Content_Category], "EngagementSum", 
            SUM('Sheet1'[Engagement])
        ),
        [EngagementSum], DESC
    )
)


4)TopPlatform by Engagement = 
CALCULATE (
    MAX('Sheet1'[Platform]),
    TOPN(1, SUMMARIZE('Sheet1', 'Sheet1'[Platform], "TotalEngagement", SUM('Sheet1'[Engagement])), [TotalEngagement])
)


5)Total Engagement = SUM(Sheet1[Engagement])
