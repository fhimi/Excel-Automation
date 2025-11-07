<h1>📊 Automation Workflow: Date Difference & Trimester Calculation</h1>

This workflow reads a list of dates from a spreadsheet, calculates the number of days between each date and today, and determines which trimester of the year each date belongs to. The results are written into new columns within the same dataset.

<h1>✅ What This Workflow Does</h1>h1>

Reads a spreadsheet containing a column of dates.

Converts each value into a valid date format (supports Excel serial numbers).

Calculates the difference in days between the date and today.

Determines the trimester (Q1, Q2, Q3, or Q4) based on the month of the date.

Writes both results into new columns in the same row.

<h1>🏗️ Workflow Logic</h1>h1>
Step	Description
1	Read the input Excel/CSV file
2	Parse date column into proper date objects
3	Calculate day difference (today - date)
4	Detect trimester based on month
5	Output updated dataset

<h1>🧮 Trimester Rules</h1>h1>
Month Range	Trimester
January – March	Q1
April – June	Q2
July – September	Q3
October – December	Q4

<h1>🧾 Example (Before → After)</h1>
Original Date	Difference (Days)	Trimester
2024-01-15	297	Q1
2024-05-02	190	Q2
2024-08-11	89	Q3
2024-11-23	10	Q4

#🛠️ Tools Used

n8n for workflow automation

Excel / CSV for input/output data

JavaScript for processing logic

<h1>🎯 Use Cases</h1>

HR contract aging reports

Subscription / billing cycle tracking

Maintenance scheduling

Academic / administrative reporting

Sales and performance dashboards
