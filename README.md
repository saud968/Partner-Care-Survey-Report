# Partner-Care-Survey-Report

![Intro Image](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/405f626f-7684-4b81-ae51-0bf3e1fcbe59)

## Introduction:
This is a Power BI project on the “Partner Care Survey Report”. The
project is to analyze and derive insights into survey count, score, and participation percentage to make data-driven decisions.

## Problem statement:
1. What is the survey count in the current year and months?
2. What are the CSAT, CES, CSAT %, and CES% scores?
3. Which are the top products?

## Skills/concepts demonstrated:
The following Power BI features were incorporated:
-	Bookmarking, 
-	DAX, 
-	Measures, 
-	Page navigation, 
-	Filters, 
-	Toggle Button, 
-	Info Panel.

## Features:
1. The "i" icon opens the Info Panel and it closes as you click anywhere on the screen.
   ![I icon for Info Panel](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/6f7c28ca-0472-44e1-8789-67d12d0cf686)
2. Toggle button to switch between CSAT and CES Score and similar toggle button for CSAT & CSAT % Positive and CES and Net Easy.
   ![CSAT toggle button feature](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/4842856f-df67-4da1-b2b2-6c31a129f32d)

## Visualization:
The report is set on a single page as per the requirement:
1.	Info Panel -
2.	Slicers and New Card Visual. 
3.	Survey Count.
4.	CSAT and CES Score.
5.	Product Pie (Volume %) and Bar Chat (Volume Count). 
6.	CSAT & CSAT % Positive and CES and Net Easy. 
7.	Survey Participation.

## Analysis:

1. Info Panel.
![Info Panel from Report](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/4f39cc2a-5925-4451-b512-b9be3b40bbe1)

This is an image prepared in PowerPoint and added as an effect to the report to help users to know about each visual as per the call-out.

2. Slicers and New Card Visual.
![Slicers   New Card](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/5f6ac324-7b9f-4219-a2f0-52e555923d2d)

You can click on the dropdown of the Month filter in the Report in Power BI and use control to select multiple months. You can click on the dropdown of the week filter and use control to select 3 Weeks. In the end, you can clear all slicers.

In "New Card Visual" you will view the surveys sent to the partner after the case is closed. It has different statuses related to surveys sent out to help understand whether the survey is completed.

LOGIC: The survey is sent to the partner as soon as the Salesforce case is closed by the Partner Care Manager. The same data is then stored under different columns. This report utilizes the column name "RESPONSE_STATUS" as a base to calculate the count and survey participation.

a)	TOTAL CARE SURVEY COUNT: Survey count is calculated using the Count of all rows under "RESPONSE_STATUS. 

b)	COMPLETED: Completed is calculated based on rows under "RESPONSE_STATUS" with the status name "Completed".

c)	FORMULA: CompletedCount = COUNTROWS(FILTER('PARTNER CARE PARTICIPANT', 'PARTNER CARE PARTICIPANT'[RESPONSE_STATUS] = "Completed"))

d)	NOT STARTED: Not started is calculated based on rows under "RESPONSE_STATUS" with the status name "Not started".

e)	FORMULA: NotStartedCount = COUNTROWS(FILTER('PARTNER CARE PARTICIPANT', 'PARTNER CARE PARTICIPANT'[RESPONSE_STATUS] = "NotStarted"))

f)	STARTED: Started is calculated based on rows under "RESPONSE_STATUS" with the status "Started".

g)	FORMULA: StartedCount = COUNTROWS(FILTER('PARTNER CARE PARTICIPANT', 'PARTNER CARE PARTICIPANT'[RESPONSE_STATUS] = "Started"))

h)	PAUSED: Paused is calculated based on rows under "RESPONSE_STATUS" with the status name "Paused".

i)	FORMULA: PausedCount = COUNTROWS(FILTER('PARTNER CARE PARTICIPANT', 'PARTNER CARE PARTICIPANT'[RESPONSE_STATUS] = "Paused"))

j)	COMPLETED %: Completed % is calculated based on the completed count divided by the total response count.

k)	FORMULA: Survey Participate % = 'PARTNER CARE PARTICIPANT'[CompletedCount]/'PARTNER CARE PARTICIPANT'[TotalResponseCount]

l)	NOT STARTED %: Not started % is calculated based on the not started count divided by the total response count.

m)	FORMULA: Survey Participate % = 'PARTNER CARE PARTICIPANT'[NotStarted]/'PARTNER CARE PARTICIPANT'[TotalResponseCount]

n)	STARTED %: Started % is calculated based on the started count divided by the total response count.

o)	FORMULA: Survey Participate % = 'PARTNER CARE PARTICIPANT'[Started]/'PARTNER CARE PARTICIPANT'[TotalResponseCount]

p)	AVERAGE AGE: Age is based on the survey age filtering with the Response Status = "Completed".

q)	FORMULA: Average Age = CALCULATE(AVERAGE('SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP'[AGE] ), KEEPFILTERS( 'PARTNER CARE PARTICIPANT'[RESPONSE_STATUS]  = "Completed" ))


3. Survey Count.
![Survey Count](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/0f0abb5e-aa9d-40f6-8ed8-7063863a4f94)

The survey count is calculated using the Count of all CSAT & CES Case Numbers from the date of January 2023.

4. CSAT and CES Score.
![CSAT Score with Toggle Button](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/ca93bdd4-4b8f-4324-9eac-c3b63a090249)

The C-SAT score was determined using the average of the response value and the question name “How satisfied are you with the overall service you received today from the Team?" It was calculated by taking the average of the responses and filtering out the question.

FORMULA: CSAT Score = CALCULATE(AVERAGEX(SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP, SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP[NUMBER_VALUE]), SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP[QUESTION_NAME] = "How satisfied are you with the overall service you received today from the Team?")

The CES score was determined using the average of the response value and the question name "The Team made it easy for me to handle my issue/case". It was calculated by taking the average of the responses and filtering out the question.

FORMULA: CES Score = CALCULATE(AVERAGEX(SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP, SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP[NUMBER_VALUE]), SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP[QUESTION_NAME] = "The Team made it easy for me to handle my issue/case.")
   
5. Product Pie (Volume %) and Bar Chat (Volume Count).
![Product Chart](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/b3b79eed-b4ff-45a0-b0ec-ad6e24a083d6)

The Product Charts have details related to Major Products Pie Chart is about volume by percentage by each major product and the bar chart is about volume count by each major product.

6. CSAT & CSAT % Positive and CES and Net Easy.
![CSAT   CES % with Toggle Button](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/07fa7b44-d914-49aa-97d7-c3e27cee2bbf)

By dividing the CSAT RESPONSE value by the total response value, the C-SAT percent is determined.
Here, we used two variables—Total response count and Total CSAT response count—and used them to calculate the variable's percentage of the C-SAT score.
In order to arrive at the variable Total Response count, we counted the number values (1,2,3,4,5) while simultaneously maintaining the filter question, "How satisfied are you with the overall service you received today from the Team?" In order to calculate the variable Total CSAT Response count, we added the Number values (4,5) and kept the filter question, "How satisfied are you with the overall service you received today from the Team?" The Total CSAT Response Count was then divided by the Total Response Count.

FORMULA: {% CSAT Score =  VAR _TotalResponseCount = CALCULATE(COUNTROWS(FILTER(SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP, SUPPORT__CW_OPS_CES_CSAT_TEMP[NUMBER_VALUE] in {1, 2, 3, 4, 5})), SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP[QUESTION_NAME] = "How satisfied are you with the overall service you received today from the Team?") VAR _TotalCSATResponseCount = CALCULATE(COUNTROWS(FILTER(SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP, SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP[NUMBER_VALUE] in {4, 5})), SUPPORT__CW_OPS_CES_CSAT_PARTNER_CARE_TEMP[QUESTION_NAME] = "How satisfied are you with the overall service you received today from the Team?") RETURN DIVIDE(_TotalCSATResponseCount, _TotalResponseCount) }

   
7. Survey Participation.
![Survey Participation %](https://github.com/saud968/Partner-Care-Survey-Report/assets/48719613/742dd35d-63b4-4438-ae29-762df068719d)

PCM SURVEY PARTICIPATION %: This visual represents the count of surveys sent out as per the PCM and the percentage of the count of completed surveys by the partner. 
Survey Participate % = 'PARTNER CARE PARTICIPANT'[CompletedCount]/'PARTNER CARE PARTICIPANT'[TotalResponseCount].



